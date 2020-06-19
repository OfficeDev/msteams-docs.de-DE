---
title: Verwenden von Aufgaben Modulen in Microsoft Teams-Registerkarten
description: Erläutert das Aufrufen von Aufgaben Modulen aus Microsoft Teams-Registerkarten mithilfe des Microsoft Teams-Client-SDK.
keywords: Aufgaben Module-Registerkarten für Microsoft Teams-Client SDK
ms.openlocfilehash: e10958195713f338a9b5e0a0672d8b6a29da9264
ms.sourcegitcommit: 2a84a3c8b10771e37ce51bf603a967633947a3e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "44801198"
---
# <a name="using-task-modules-in-tabs"></a>Verwenden von Aufgaben Modulen in Registerkarten

Das Hinzufügen eines Aufgabenmoduls zur Registerkarte kann die Benutzerfreundlichkeit für Workflows erheblich vereinfachen, die Dateneingaben erfordern. Aufgaben Module ermöglichen es Ihnen, Ihre Eingaben in einem Teams-fähigen Popup-Fenster zu erfassen. Ein gutes Beispiel hierfür ist das Bearbeiten von Planner-Karten; Sie können Aufgaben Module verwenden, um eine ähnliche Erfahrung zu erstellen.

Zur Unterstützung der Funktion "Aufgabenmodul" wurden dem [Microsoft Teams-Client SDK](/javascript/api/overview/msteams-client)zwei neue Funktionen hinzugefügt:

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

Mal sehen, wie jeder von Ihnen funktioniert.

## <a name="invoking-a-task-module-from-a-tab"></a>Aufrufen eines Aufgabenmoduls über eine Registerkarte

Zum Aufrufen eines Aufgabenmoduls aus einer Registerkarte verwenden Sie `microsoftTeams.tasks.startTask()` das Übergeben eines [taskinfo-Objekts](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) und einer optionalen `submitHandler` Rückruffunktion. Wie zuvor beschrieben, gibt es zwei Fälle, die beachtet werden sollten:

1. Der Wert von `TaskInfo.url` ist auf eine URL festgelegt. Das Fenster Aufgabenmodul wird angezeigt, und `TaskModule.url` es wird als `<iframe>` darin geladen. JavaScript auf dieser Seite sollte aufgerufen werden `microsoftTeams.initialize()` . Wenn `submitHandler` auf der Seite eine Funktion vorhanden ist und beim Aufrufen ein Fehler auftritt `microsoftTeams.tasks.startTask()` , `submitHandler` wird mit `err` festgelegt, dass die Fehlerzeichenfolge den Fehler wie [unten](#task-module-invocation-errors)beschrieben angibt.
1. Der Wert von `taskInfo.card` ist [JSON für eine Adaptive Karte](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). In diesem Fall gibt es natürlich keine JavaScript- `submitHandler` Funktion, die aufgerufen wird, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt; die einzige Möglichkeit, die Eingabe des Benutzers zu erhalten, besteht darin, das Ergebnis an einen bot zu übergeben. Um einen Adaptive Card-Aufgabenmodul aus einer Registerkarte zu verwenden, muss Ihre APP einen bot enthalten, um alle Informationen vom Benutzer zurück zu erhalten. Dies wird im folgenden erläutert.

## <a name="example-invoking-a-task-module"></a>Beispiel: Aufrufen eines Aufgabenmoduls

Der folgende Code wird aus [dem Aufgabenmodul Beispiel](~/task-modules-and-cards/what-are-task-modules.md#task-module-samples)angepasst. Hier sehen Sie, wie das Aufgabenmodul aussieht:

![Aufgabenmodul – benutzerdefiniertes Formular](~/assets/images/task-module/task-module-custom-form.png)

Das `submitHandler` ist sehr einfach; er gibt nur den Wert von `err` oder `result` in der Konsole wieder:

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

## <a name="submitting-the-result-of-a-task-module"></a>Übermitteln des Ergebnisses eines Aufgabenmoduls

Die `submitHandler` -Funktion wird mit verwendet `TaskInfo.url` . Die `submitHandler` Funktion befindet sich auf der `TaskInfo.url` Webseite. Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt `submitHandler` , wird die Funktion sofort mit einer `err` Zeichenfolge aufgerufen, die angibt, welcher [Fehler aufgetreten](#task-module-invocation-errors)ist. Die `submitHandler` Funktion wird auch mit einer `err` Zeichenfolge aufgerufen, wenn der Benutzer das X in der oberen rechten Ecke des Aufgabenmoduls drückt.

Wenn kein Aufruffehler vorliegt und der Benutzer nicht X drückt, um ihn zu schließen, drückt der Benutzer nach Abschluss eine Schaltfläche. In Abhängigkeit davon, ob es sich um eine URL oder eine Adaptive Karte im Aufgabenmodul handelt, gehen Sie folgendermaßen vor:

### <a name="htmljavascript-taskinfourl"></a>HTML/JavaScript ( `TaskInfo.url` )

Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die `microsoftTeams.tasks.submitTask()` SDK-Funktion auf (wird im folgenden als `submitTask()` Zweck der Lesbarkeit bezeichnet). Sie können `submitTask()` ohne Parameter aufrufen, wenn Sie lediglich möchten, dass Teams den Aufgabenmodul schließen, aber in den meisten Fällen möchten Sie ein Objekt oder eine Zeichenfolge an Ihren übergeben `submitHandler` .

Übergeben Sie das Ergebnis als ersten Parameter. Teams rufen an, `submitHandler` wo `err` `null` `result` das Objekt/die Zeichenfolge, an das Sie übergeben werden, sein wird und wird `submitTask()` . Wenn Sie `submitTask()` einen `result` Parameter aufrufen, **müssen** Sie ein `appId` oder ein Array von `appId` Zeichenfolgen übergeben: Dadurch können Teams überprüfen, ob die APP, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen hat.

### <a name="adaptive-card-taskinfocard"></a>Adaptive Karte ( `TaskInfo.card` )

Wenn Sie den Aufgabenmodul mit einem aufgerufen `submitHandler` haben und der Benutzer eine Schaltfläche drückt, werden `Action.Submit` die Werte in der Karte als Wert von zurückgegeben `result` . Wenn der Benutzer die ESC-Taste drückt oder das X drückt, `err` wird stattdessen zurückgegeben. Alternativ können Sie, wenn Ihre APP zusätzlich zu einer Registerkarte einen bot enthält, den `appId` des bot einfach als Wert `completionBotId` in das `TaskInfo` Objekt einschließen. Der Adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den bot gesendet, `task/submit invoke` Wenn der Benutzer eine `Action.Submit` Schaltfläche drückt. Das Schema für das empfangene Objekt ähnelt [dem Schema, das Sie für Aufgaben/FETCH-und Task-/Submit-Nachrichten erhalten](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages). der einzige Unterschied besteht darin, dass das Schema des JSON-Objekts ein adaptives Kartenobjekt im Gegensatz zu einem Objekt ist, das ein adaptives Kartenobjekt *enthält* , als [Wenn Adaptive Karten mit Bots verwendet werden](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages).

## <a name="example-submitting-the-result-of-a-task-module"></a>Beispiel: übermitteln des Ergebnisses eines Aufgabenmoduls

Rufen Sie das [Formular im obigen Aufgabenmodul](#example-invoking-a-task-module) mit einem HTML-Formular auf. Hier wird das Formular definiert:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Es gibt fünf Felder in diesem Formular, aber wir sind nur an den Werten von drei für dieses Beispiel interessiert: `name` , `email` und `favoriteBook` .

Hier ist die `validateForm()` Funktion, die `submitTask()` Folgendes aufruft:

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

## <a name="task-module-invocation-errors"></a>Fehler beim Aufrufen des Aufgabenmoduls

Hier sind die möglichen Werte `err` , die von Ihrem empfangen werden können `submitHandler` :

| Problem | Fehlermeldung (Wert von `err` ) |
| ------- | ------------------------------ |
| Werte für beide `TaskInfo.url` und `TaskInfo.card` wurden angegeben. | "Die Werte für Karte und URL wurden angegeben. Die eine oder die andere, aber nicht beides, sind zulässig. " |
| Weder `TaskInfo.url` noch `TaskInfo.card` angegeben. | "Sie müssen einen Wert für die Karten-oder URL-Adresse angeben." |
| Ungültig `appId` . | "Ungültige Typkennung". |
| Der Benutzer hat die X-Schaltfläche gedrückt und geschlossen. | "Benutzer hat den Aufgabenmodul storniert/geschlossen." |
