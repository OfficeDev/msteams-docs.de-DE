---
title: Aufgabenmodule in Microsoft Teams-Registerkarten verwenden
description: Erfahren Sie, wie Sie Aufgabenmodule über Teams Registerkarten aufrufen und das Ergebnis mit dem Microsoft Teams Client SDK übermitteln. Es enthält Codebeispiele.
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: a55ea89e67bf70254d52791d1ed5f0a1c573e89e
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142066"
---
# <a name="use-task-modules-in-tabs"></a>Verwenden von Aufgabenmodulen in Registerkarten

Fügen Sie Ihrer Registerkarte ein Aufgabenmodul hinzu, um die Erfahrung Ihrer Benutzer mit Workflows zu vereinfachen, die Dateneingaben erfordern. Mit Aufgabenmodulen können Sie ihre Eingaben in einem Microsoft Teams-fähigen Popup erfassen. Ein gutes Beispiel hierfür ist das Bearbeiten von Planner-Karten. Sie können Aufgabenmodule verwenden, um eine ähnliche Erfahrung zu erstellen.

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

Sie können sehen, wie das Aufrufen eines Aufgabenmoduls über eine Registerkarte und das Übermitteln des Ergebnisses eines Aufgabenmoduls funktioniert.

## <a name="invoke-a-task-module-from-a-tab"></a>Aufrufen eines Aufgabenmoduls über eine Registerkarte

Verwenden Sie zum Aufrufen eines Aufgabenmoduls über eine Registerkarte `microsoftTeams.tasks.startTask()`, und übergeben Sie ein [TaskInfo-Objekt](~/task-modules-and-cards/task-modules/invoking-task-modules.md#the-taskinfo-object) und eine optionale `submitHandler`-Rückruffunktion. Es müssen zwei Fälle berücksichtigt werden:

* Der Wert von `TaskInfo.url` ist auf eine URL festgelegt. Das Aufgabenmodulfenster wird angezeigt, und `TaskModule.url` wird als ein `<iframe>` darin geladen. JavaScript auf dieser Seite ruft `microsoftTeams.initialize()` auf. `submitHandler` Wenn eine Funktion auf der Seite vorhanden ist und beim Aufrufen `microsoftTeams.tasks.startTask()`ein Fehler auftritt, wird diese `submitHandler` aufgerufen, wobei `err` der Wert auf die Fehlerzeichenfolge festgelegt ist, die dasselbe angibt. Weitere Informationen finden Sie unter [Aufgabenmodul-Aufruffehler](#task-module-invocation-errors).
* Der Wert von `taskInfo.card` ist der [JSON für eine adaptive Karte](~/task-modules-and-cards/task-modules/invoking-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). Es gibt keine JavaScript-Funktion `submitHandler` , die aufgerufen werden kann, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt. Die einzige Möglichkeit, den vom Benutzer eingegebenen Inhalt zu erhalten, besteht darin, das Ergebnis an einen Bot zu übergeben. Um ein Aufgabenmodul für eine adaptive Karte über eine Registerkarte zu verwenden, muss Ihre App einen Bot enthalten, um eine Antwort vom Benutzer zu erhalten.

Der nächste Abschnitt enthält ein Beispiel für das Aufrufen eines Aufgabenmoduls.

## <a name="example-of-invoking-a-task-module"></a>Beispiel für das Aufrufen eines Aufgabenmoduls

In der folgenden Abbildung wird das Aufgabenmodul angezeigt:

:::image type="content" source="../../assets/images/task-module/task-module-custom-form.png" alt-text="Benutzerdefinierte Maske für das Aufgabenmodul":::

Der folgende Code ist dem [Beispiel des Aufgabenmoduls](~/task-modules-and-cards/task-modules/invoking-task-modules.md#code-sample) entnommen:

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

Dies `submitHandler` ist einfach und spiegelt den Wert von `err` oder `result` an die Konsole wider.

## <a name="submit-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Die `submitHandler`-Funktion befindet sich auf der `TaskInfo.url`-Webseite und wird mit `TaskInfo.url` verwendet. Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt, wird Ihre `submitHandler` Funktion sofort mit einer `err` Zeichenfolge aufgerufen, die angibt, welcher [Fehler aufgetreten](#task-module-invocation-errors) ist. Die `submitHandler`-Funktion wird auch mit einer `err`-Zeichenfolge aufgerufen, wenn der Benutzer oben rechts im Aufgabenmodul „X“ auswählt, um es zu schließen.

Wenn kein Aufruffehler vorliegt und der Benutzer X nicht auswählt, um es zu schließen, wählt der Benutzer nach Abschluss eine Schaltfläche aus. Je nachdem, ob es sich um eine URL oder eine adaptive Karte im Aufgabenmodul handelt, enthalten die nächsten Abschnitte Details zu den Ereignissen.

### <a name="html-or-javascript-taskinfourl"></a>HTML- oder JavaScript-`TaskInfo.url`

Rufen Sie nach dem Überprüfen der Eingaben des Benutzers die SDK-Funktion `microsoftTeams.tasks.submitTask()` auf, die als `submitTask()` bezeichnet wird. Rufen Sie `submitTask()` ohne Parameter auf, wenn Teams nur das Aufgabenmodul schließen soll. Sie können ein Objekt oder eine Zeichenfolge an Ihren `submitHandler` übergeben.

Übergeben Sie Ihr Ergebnis als ersten Parameter. Teams ruft `submitHandler` auf, wobei `err` gleich `null` ist und `result` das Objekt oder die Zeichenfolge, das/die Sie an `submitTask()` übergeben haben. Wenn Sie `submitTask()` mit einem `result`-Parameter aufrufen, müssen Sie ein `appId` oder ein Array von `appId`-Zeichenfolgen übergeben. Dies erlaubt Teams zu validieren, ob die App, die das Ergebnis sendet, mit dem aufgerufenen Aufgabenmodul übereinstimmt.

### <a name="adaptive-card-taskinfocard"></a>Adaptive Karte `TaskInfo.card`

Wenn Sie das Aufgabenmodul mit einer `submitHandler` aufrufen und der Benutzer eine `Action.Submit`-Schaltfläche auswählt, werden die Werte auf der Karte als Wert von `result` zurückgegeben. Wenn der Benutzer oben rechts die ESC-Taste oder „X“ auswählt, wird stattdessen `err` zurückgegeben. Wenn Ihre App zusätzlich zu einer Registerkarte einen Bot enthält, können Sie den `appId` Bot als Wert `completionBotId` in das `TaskInfo` Objekt einschließen. Der vom Benutzer ausgefüllte Text der adaptiven Karte wird mithilfe einer `task/submit invoke`-Nachricht an den Bot gesendet, wenn der Benutzer eine `Action.Submit`-Schaltfläche auswählt. Das Schema für das empfangene Objekt ähnelt [dem Schema, das Sie für Aufgaben-/Abruf- und Aufgaben-/Sendenachrichten erhalten](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages). Der einzige Unterschied besteht darin, dass das Schema des JSON-Objekts ein adaptives Kartenobjekt ist, im Gegensatz zu einem Objekt, das ein adaptives Kartenobjekt enthält wie bei der [Verwendung von adaptiven Karten mit Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

Der nächste Abschnitt enthält ein Beispiel für die Übermittlung des Ergebnisses eines Aufgabenmoduls.

## <a name="example-of-submitting-the-result-of-a-task-module"></a>Beispiel für die Übermittlung des Ergebnisses eines Aufgabenmoduls

Weitere Informationen finden Sie im [HTML-Formular im Aufgabenmodul](#example-of-invoking-a-task-module). Der folgende Code enthält ein Beispiel dafür, wo das Formular definiert ist:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Dieses Formular enthält fünf Felder, aber für dieses Beispiel sind nur drei Werte erforderlich: `name`, `email` und `favoriteBook`.

Der folgende Code enthält ein Beispiel für die `validateForm()`-Funktion, die `submitTask()` aufruft:

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

Die folgende Tabelle enthält die möglichen Werte von `err`, die von Ihrem `submitHandler` empfangen werden können:

| Problem | Fehlermeldung mit dem Wert `err` |
| ------- | ------------------------------ |
| Es wurden Werte für `TaskInfo.url` und `TaskInfo.card` angegeben. | Sowohl für die Karte als auch für die URL wurden Werte angegeben. Der eine oder der andere Wert ist zulässig, aber nicht beide. |
| Weder `TaskInfo.url` noch `TaskInfo.card` wurden angegeben. | Sie müssen einen Wert entweder für die Karte oder die URL angeben. |
| Ungültige `appId`. | Ungültige App-ID. |
| Der Benutzer hat die Schaltfläche „X“ ausgewählt und es geschlossen. | Der Benutzer hat das Aufgabenmodul abgebrochen oder geschlossen. |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Beispielregisterkarten und Bots des Aufgabenmoduls – V3 | Beispiele für das Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)

## <a name="see-also"></a>Siehe auch

[Aufrufen und Schließen von Aufgabenmodulen](~/task-modules-and-cards/task-modules/invoking-task-modules.md)
