---
title: Verwenden von Aufgabenmodulen in Microsoft Teams Registerkarten
description: Erläutert das Aufrufen von Aufgabenmodulen von Teams Registerkarten mithilfe des Microsoft Teams-Client-SDKs.
localization_priority: Normal
ms.topic: how-to
keywords: Teams-Registerkarten-Client-SDK für Aufgabenmodule
ms.openlocfilehash: 8afd2c93261f28aa7ced4c98d29be27dca35f8b1
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140552"
---
# <a name="use-task-modules-in-tabs"></a>Verwenden von Aufgabenmodulen in Registerkarten

Fügen Sie Ihrer Registerkarte ein Aufgabenmodul hinzu, um die Benutzererfahrung für workflows zu vereinfachen, die eine Dateneingabe erfordern. Mit Aufgabenmodulen können Sie ihre Eingaben in einem Microsoft Teams-Aware-Popup erfassen. Ein gutes Beispiel hierfür ist das Bearbeiten von Planner-Karten. Sie können Aufgabenmodule verwenden, um eine ähnliche Oberfläche zu erstellen.

Zur Unterstützung des Aufgabenmodulfeatures werden dem [Teams-Client-SDK](/javascript/api/overview/msteams-client)zwei neue Funktionen hinzugefügt. Der folgende Code zeigt ein Beispiel für diese beiden Funktionen:

```typescript
microsoftTeams.tasks.startTask(
    taskInfo: TaskInfo,
    submitHandler?: (err: string, result: string | any) => void
): void;

microsoftTeams.tasks.submitTask(
    result?: string | any,
    appIds?: string | string[]
): void;
```

Sie können sehen, wie das Aufrufen eines Aufgabenmoduls über eine Registerkarte und das Übermitteln des Ergebnisses eines Aufgabenmoduls funktioniert.

## <a name="invoke-a-task-module-from-a-tab"></a>Aufrufen eines Aufgabenmoduls über eine Registerkarte

Zum Aufrufen eines Aufgabenmoduls über eine Registerkarte übergeben Sie `microsoftTeams.tasks.startTask()` ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) und eine optionale `submitHandler` Rückruffunktion. Es gibt zwei Zu berücksichtigende Fälle:

* Der Wert von `TaskInfo.url` ist auf eine URL festgelegt. Das Aufgabenmodulfenster wird angezeigt und `TaskModule.url` als `<iframe>` darin geladen. JavaScript auf dieser Seite ruft `microsoftTeams.initialize()` . Wenn eine Funktion auf der Seite vorhanden `submitHandler` ist und beim Aufrufen ein Fehler `microsoftTeams.tasks.startTask()` auftritt, wird dieser `submitHandler` aufgerufen, wobei die `err` Fehlerzeichenfolge auf dieselbe festgelegt ist. Weitere Informationen finden Sie unter [Fehler beim Aufrufen des Aufgabenmoduls.](#task-module-invocation-errors)
* Der Wert von `taskInfo.card` ist der [JSON-Code für eine adaptive Karte.](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment) Es gibt keine JavaScript-Funktion, die aufgerufen werden `submitHandler` kann, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt. Die einzige Möglichkeit, die vom Benutzer eingegebenen Informationen zu erhalten, besteht darin, das Ergebnis an einen Bot zu übergeben. Um ein Aufgabenmodul für adaptive Karten auf einer Registerkarte zu verwenden, muss Ihre App einen Bot enthalten, um eine Antwort des Benutzers zu erhalten.

Der nächste Abschnitt enthält ein Beispiel für das Aufrufen eines Aufgabenmoduls.

## <a name="example-of-invoking-a-task-module"></a>Beispiel für das Aufrufen eines Aufgabenmoduls

In der folgenden Abbildung wird das Aufgabenmodul angezeigt:

![Aufgabenmodul – benutzerdefiniertes Formular](~/assets/images/task-module/task-module-custom-form.png)

Der folgende Code basiert auf [dem Aufgabenmodulbeispiel:](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample)

```javascript
let taskInfo = {
    title: null,
    height: null,
    width: null,
    url: null,
    card: null,
    fallbackUrl: null,
    completionBotId: null,
};

taskInfo.url = "https://contoso.com/teamsapp/customform";
taskInfo.title = "Custom Form";
taskInfo.height = 510;
taskInfo.width = 430;
submitHandler = (err, result) => {
    console.log(`Submit handler - err: ${err}`);
    console.log(`Submit handler - result\rName: ${result.name}\rEmail: ${result.email}\rFavorite book: ${result.favoriteBook}`);
};
microsoftTeams.tasks.startTask(taskInfo, submitHandler);
```

Dies `submitHandler` ist sehr einfach und entspricht dem Wert der Konsole oder der `err` `result` Konsole.

## <a name="submit-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Die `submitHandler` Funktion befindet sich auf der Webseite und wird mit `TaskInfo.url` `TaskInfo.url` verwendet. Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt, wird Ihre `submitHandler` Funktion sofort mit einer Zeichenfolge `err` aufgerufen, die angibt, welcher [Fehler aufgetreten ist.](#task-module-invocation-errors) Die `submitHandler` Funktion wird auch mit einer Zeichenfolge `err` aufgerufen, wenn der Benutzer X oben rechts im Aufgabenmodul auswählt, um sie zu schließen.

Wenn kein Aufruffehler auftritt und der Benutzer X nicht auswählt, um es zu schließen, wählt der Benutzer nach Abschluss eine Schaltfläche aus. Je nachdem, ob es sich um eine URL oder eine adaptive Karte im Aufgabenmodul handelt, enthalten die nächsten Abschnitte Details dazu, was passiert.

### <a name="html-or-javascript-taskinfourl"></a>HTML oder JavaScript `TaskInfo.url`

Rufen Sie nach dem Überprüfen der Eingaben des Benutzers die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf, die als `submitTask()` bezeichnet wird. Rufen `submitTask()` Sie ohne Parameter auf, wenn Sie nur möchten, dass Teams das Aufgabenmodul schließt. Sie können ein Objekt oder eine Zeichenfolge an Ihre `submitHandler` übergeben.

Übergeben Sie Ihr Ergebnis als ersten Parameter. Teams ruft auf, wo sich das Objekt oder die Zeichenfolge befindet `submitHandler` `err` und `null` `result` ist, an die Sie übergeben `submitTask()` haben. Wenn Sie `submitTask()` mit einem Parameter `result` aufrufen, müssen Sie ein oder ein Array von `appId` `appId` Zeichenfolgen übergeben. Dadurch können Teams überprüfen, ob die App, die das Ergebnis sendet, mit dem aufgerufenen Aufgabenmodul übereinstimmt.

### <a name="adaptive-card-taskinfocard"></a>Adaptive Karte `TaskInfo.card`

Wenn Sie das Aufgabenmodul mit einer aufrufen `submitHandler` und der Benutzer eine Schaltfläche auswählt, werden die Werte auf der Karte als Wert von `Action.Submit` `result` zurückgegeben. Wenn der Benutzer die Esc-Taste oder X oben rechts auswählt, `err` wird stattdessen zurückgegeben. Wenn Ihre App zusätzlich zu einer Registerkarte einen Bot enthält, können Sie einfach den `appId` Bot als Wert in das Objekt `completionBotId` `TaskInfo` einschließen. Der vom Benutzer ausgefüllte Textkörper der adaptiven Karte wird mithilfe einer Nachricht an den Bot `task/submit invoke` gesendet, wenn der Benutzer eine Schaltfläche auswählt. `Action.Submit` Das Schema für das empfangene Objekt ähnelt dem [Schema, das Sie für Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten erhalten.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) Der einzige Unterschied besteht darin, dass das Schema des JSON-Objekts ein Adaptive Card-Objekt im Gegensatz zu einem Objekt ist, das ein Adaptive Card-Objekt enthält, als [wenn adaptive Karten mit Bots verwendet werden.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages)

Der nächste Abschnitt enthält ein Beispiel für das Übermitteln des Ergebnisses eines Aufgabenmoduls.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Beispiel für das Übermitteln des Ergebnisses eines Aufgabenmoduls

Weitere Informationen finden Sie [im HTML-Formular im Aufgabenmodul.](#example-of-invoking-a-task-module) Der folgende Code enthält ein Beispiel dafür, wo das Formular definiert ist:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Es gibt fünf Felder in diesem Formular, aber für dieses Beispiel sind nur drei Werte erforderlich, `name` und `email` `favoriteBook` .

Der folgende Code enthält ein Beispiel für die `validateForm()` Funktion, die `submitTask()` aufruft:

```javascript
function validateForm() {
    var customerInfo = {
        name: document.forms["customerForm"]["name"].value,
        email: document.forms["customerForm"]["email"].value,
        favoriteBook: document.forms["customerForm"]["favoriteBook"].value
    }
    microsoftTeams.tasks.submitTask(customerInfo, "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx");
    return true;
}
```

Der nächste Abschnitt enthält Aufrufprobleme des Aufgabenmoduls und deren Fehlermeldungen.

## <a name="task-module-invocation-errors"></a>Fehler beim Aufrufen des Aufgabenmoduls

Die folgende Tabelle enthält die möglichen `err` Werte, die von Ihnen empfangen werden `submitHandler` können:

| Problem | Fehlermeldung, die den Wert von `err` |
| ------- | ------------------------------ |
| Werte für beide `TaskInfo.url` werte und `TaskInfo.card` wurden angegeben. | Werte für Karte und URL wurden angegeben. Der eine oder andere, aber nicht beide, sind zulässig. |
| `TaskInfo.url`Weder `TaskInfo.card` angegeben noch angegeben. | Sie müssen einen Wert für karte oder URL angeben. |
| `appId`Ungültig. | Ungültige App-ID. |
| Der Benutzer hat die X-Schaltfläche ausgewählt und sie geschlossen. | Der Benutzer hat das Aufgabenmodul abgebrochen oder geschlossen. |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodul-Beispielregisterkarten und Bots-V3 | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 

## <a name="see-also"></a>Siehe auch

[Aufrufen und Schließen von Aufgabenmodulen](~/task-modules-and-cards/task-modules/invoking-task-modules.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden von Aufgabenmodulen von Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
