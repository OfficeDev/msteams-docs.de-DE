---
title: Verwenden von Aufgabenmodulen auf Microsoft Teams Registerkarten
description: Erläutert, wie Sie Aufgabenmodule von Teams Registerkarten aufrufen und das Ergebnis mithilfe des Microsoft Teams-Client-SDK übermitteln. Es enthält Codebeispiele.
ms.localizationpriority: medium
ms.topic: how-to
keywords: Teams-Registerkarten-Client-SDK für Aufgabenmodule
ms.openlocfilehash: 63ac1df5b9cdbbba46ba204103a9a5c989b3a323
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073757"
---
# <a name="use-task-modules-in-tabs"></a>Verwenden von Aufgabenmodulen in Registerkarten

Fügen Sie Ihrer Registerkarte ein Aufgabenmodul hinzu, um die Benutzererfahrung für workflows zu vereinfachen, die Dateneingaben erfordern. Aufgabenmodule ermöglichen es Ihnen, ihre Eingaben in einem Microsoft Teams-Aware-Popup zu erfassen. Ein gutes Beispiel hierfür ist das Bearbeiten von Planner-Karten. Sie können Aufgabenmodule verwenden, um eine ähnliche Oberfläche zu erstellen.

Zur Unterstützung des Aufgabenmodulfeatures werden dem [Teams-Client-SDK](/javascript/api/overview/msteams-client) zwei neue Funktionen hinzugefügt. Der folgende Code zeigt ein Beispiel für diese beiden Funktionen:

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

Sie können sehen, wie das Aufrufen eines Aufgabenmoduls von einer Registerkarte und das Übermitteln des Ergebnisses eines Aufgabenmoduls funktioniert.

## <a name="invoke-a-task-module-from-a-tab"></a>Aufrufen eines Aufgabenmoduls über eine Registerkarte

Um ein Aufgabenmodul über eine Registerkarte aufzurufen, übergeben Sie `microsoftTeams.tasks.startTask()` ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) und eine optionale `submitHandler` Rückruffunktion. Es gibt zwei Fälle zu berücksichtigen:

* Der Wert von `TaskInfo.url` wird auf eine URL festgelegt. Das Aufgabenmodulfenster wird angezeigt und `TaskModule.url` als inneres `<iframe>` Fenster geladen. JavaScript auf dieser Seite ruft auf `microsoftTeams.initialize()`. Wenn auf der Seite eine `submitHandler` Funktion vorhanden ist und beim Aufrufen `microsoftTeams.tasks.startTask()`ein Fehler auftritt, `submitHandler` wird dies aufgerufen `err` , wobei auf die Fehlerzeichenfolge festgelegt ist, die dasselbe angibt. Weitere Informationen finden Sie [unter Fehler beim Aufrufen von Aufgabenmodulen](#task-module-invocation-errors).
* Der Wert ist `taskInfo.card` der [JSON-Code für eine adaptive Karte](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). Es gibt keine JavaScript-Funktion `submitHandler` , die aufgerufen werden kann, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt. Die einzige Möglichkeit, das vom Benutzer eingegebene Ergebnis zu erhalten, besteht darin, das Ergebnis an einen Bot zu übergeben. Um ein Aufgabenmodul für adaptive Karten von einer Registerkarte aus verwenden zu können, muss Ihre App einen Bot enthalten, um eine Antwort des Benutzers zu erhalten.

Der nächste Abschnitt enthält ein Beispiel für das Aufrufen eines Aufgabenmoduls.

## <a name="example-of-invoking-a-task-module"></a>Beispiel für das Aufrufen eines Aufgabenmoduls

In der folgenden Abbildung wird das Aufgabenmodul angezeigt:

:::image type="content" source="../../assets/images/task-module/task-module-custom-form.png" alt-text="Benutzerdefiniertes Aufgabenmodulformular":::

Der folgende Code wird aus [dem Beispiel des Aufgabenmoduls](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample) angepasst:

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

Dies `submitHandler` ist sehr einfach und spiegelt den Wert von `err` oder `result` auf die Konsole wider.

## <a name="submit-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Die `submitHandler` Funktion befindet sich auf der `TaskInfo.url` Webseite und wird mit `TaskInfo.url`verwendet. Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt, wird Ihre `submitHandler` Funktion sofort mit einer `err` Zeichenfolge aufgerufen, die angibt, welcher [Fehler aufgetreten](#task-module-invocation-errors) ist. Die `submitHandler` Funktion wird auch mit einer `err` Zeichenfolge aufgerufen, wenn der Benutzer oben rechts im Aufgabenmodul X auswählt, um sie zu schließen.

Wenn kein Aufruffehler vorliegt und der Benutzer X nicht auswählt, um es zu schließen, wählt der Benutzer nach Abschluss eine Schaltfläche aus. Je nachdem, ob es sich um eine URL oder eine adaptive Karte im Aufgabenmodul handelt, enthalten die nächsten Abschnitte Details zu den Ereignissen.

### <a name="html-or-javascript-taskinfourl"></a>HTML oder JavaScript `TaskInfo.url`

Nachdem Sie die Eingaben des Benutzers überprüft haben, rufen Sie die SDK-Funktion auf, die `microsoftTeams.tasks.submitTask()` als `submitTask()`. Rufen Sie `submitTask()` ohne Parameter auf, wenn Sie nur Teams möchten, um das Aufgabenmodul zu schließen. Sie können ein Objekt oder eine Zeichenfolge an Ihre `submitHandler`übergeben.

Übergeben Sie das Ergebnis als ersten Parameter. Teams ruft auf, wo `err` sich das Objekt oder die Zeichenfolge befindet `null` `result`, das bzw. die Sie übergeben haben`submitTask()`.`submitHandler` Wenn Sie einen Aufruf mit einem Parameter ausführen`submitTask()`, müssen Sie ein `appId` oder ein Array von Zeichenfolgen `appId` `result` übergeben. Auf diese Weise kann Teams überprüfen, ob die App, die das Ergebnis sendet, mit dem aufgerufenen Aufgabenmodul übereinstimmt.

### <a name="adaptive-card-taskinfocard"></a>Adaptive Karte `TaskInfo.card`

Wenn Sie das Aufgabenmodul mit einem `submitHandler` aufrufen und der Benutzer eine `Action.Submit` Schaltfläche auswählt, werden die Werte auf der Karte als Wert von `result`zurückgegeben. Wenn der Benutzer die ESC-Taste oder X oben rechts auswählt, `err` wird stattdessen zurückgegeben. Wenn Ihre App zusätzlich zu einer Registerkarte einen Bot enthält, können Sie einfach den `appId` Bot als Wert `completionBotId` in das `TaskInfo` Objekt einschließen. Der vom Benutzer ausgefüllte Textkörper der adaptiven Karte wird mithilfe einer `task/submit invoke` Nachricht an den Bot gesendet, wenn der Benutzer eine `Action.Submit` Schaltfläche auswählt. Das Schema für das Objekt, das Sie empfangen, ist [dem Schema, das Sie für Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten erhalten](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages), sehr ähnlich. Der einzige Unterschied besteht darin, dass das Schema des JSON-Objekts ein Adaptive Card-Objekt ist, im Gegensatz zu einem Objekt, das ein Adaptive Card-Objekt enthält, wie [wenn adaptive Karten mit Bots verwendet werden](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

Der nächste Abschnitt enthält ein Beispiel für das Übermitteln des Ergebnisses eines Aufgabenmoduls.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Beispiel für das Übermitteln des Ergebnisses eines Aufgabenmoduls

Weitere Informationen finden Sie [im HTML-Formular im Aufgabenmodul](#example-of-invoking-a-task-module). Der folgende Code zeigt ein Beispiel für die Definition des Formulars:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Dieses Formular enthält fünf Felder, für dieses Beispiel sind jedoch nur drei Werte erforderlich: `name`, `email`und `favoriteBook`.

Der folgende Code zeigt ein Beispiel für die Funktion, die `validateForm()` Aufrufe `submitTask()`:

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

Im nächsten Abschnitt werden Aufgabenmodulaufrufprobleme und deren Fehlermeldungen bereitgestellt.

## <a name="task-module-invocation-errors"></a>Fehler beim Aufrufen des Aufgabenmoduls

Die folgende Tabelle enthält die möglichen Werte, die `err` von Ihrem `submitHandler`empfangen werden können:

| Problem | Fehlermeldung, die den Wert von `err` |
| ------- | ------------------------------ |
| Werte für beide `TaskInfo.url` Und `TaskInfo.card` wurden angegeben. | Es wurden Werte für Karte und URL angegeben. Der eine oder andere, aber nicht beides, ist zulässig. |
| Weder `TaskInfo.url` angegeben noch `TaskInfo.card` angegeben. | Sie müssen einen Wert für karte oder URL angeben. |
| Ungültig `appId`. | Ungültige App-ID. |
| Der Benutzer hat die Schaltfläche "X" ausgewählt und sie geschlossen. | Der Benutzer hat das Aufgabenmodul abgebrochen oder geschlossen. |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Beispielregisterkarten und Bots des Aufgabenmoduls-V3 | Beispiele für das Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)

## <a name="see-also"></a>Siehe auch

[Aufrufen und Schließen von Aufgabenmodulen](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
