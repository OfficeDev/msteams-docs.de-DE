---
title: Verwenden von Aufgabenmodulen in Microsoft Teams-Registerkarten
description: Erläutert, wie Aufgabenmodule auf Registerkarten von Teams mithilfe des Microsoft Teams-Client-SDK aufgerufen werden.
keywords: task modules teams tabs client sdk
ms.openlocfilehash: 3f1da4d5eec31638d69adc01a45831534d015f41
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449556"
---
# <a name="using-task-modules-in-tabs"></a>Verwenden von Aufgabenmodulen in Registerkarten

Das Hinzufügen eines Aufgabenmoduls zu Ihrer Registerkarte kann die Benutzererfahrung für Workflows, für die Dateneingaben erforderlich sind, erheblich vereinfachen. Mit Aufgabenmodulen können Sie ihre Eingaben in einem Teams-bewussten Popup erfassen. Ein gutes Beispiel hierin ist die Bearbeitung von Planner-Karten. Sie können Aufgabenmodule verwenden, um eine ähnliche Erfahrung zu erstellen.

Zur Unterstützung des Aufgabenmodulfeatures wurden dem [Microsoft Teams-Client-SDK](/javascript/api/overview/msteams-client)zwei neue Funktionen hinzugefügt:

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

Sehen wir uns an, wie jeder von ihnen funktioniert.

## <a name="invoking-a-task-module-from-a-tab"></a>Aufrufen eines Aufgabenmoduls über eine Registerkarte

Verwenden Sie zum Aufrufen eines Aufgabenmoduls von einer Registerkarte aus das Übergeben `microsoftTeams.tasks.startTask()` eines [TaskInfo-Objekts](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object) und einer optionalen `submitHandler` Rückruffunktion. Wie bereits beschrieben, sind zwei Fälle zu berücksichtigen:

1. Der Wert von `TaskInfo.url` ist auf eine URL festgelegt. Das Aufgabenmodulfenster wird angezeigt und `TaskModule.url` als innen `<iframe>` geladen. JavaScript auf dieser Seite sollte `microsoftTeams.initialize()` aufrufen. Wenn auf der Seite eine Funktion enthalten ist und beim Aufrufen ein Fehler auftritt, wird mit set auf die Fehlerzeichenfolge aufgerufen, die den Fehler angibt, wie `submitHandler` `microsoftTeams.tasks.startTask()` unten `submitHandler` `err` [beschrieben.](#task-module-invocation-errors)
1. Der Wert von `taskInfo.card` ist der [JSON für eine adaptive Karte](~/task-modules-and-cards/what-are-task-modules.md#adaptive-card-or-adaptive-card-bot-card-attachment). In diesem Fall gibt es offensichtlich keine JavaScript-Funktion zum Aufrufen, wenn der Benutzer eine Schaltfläche auf der adaptiven Karte schließt oder drückt. Die einzige Möglichkeit, das eingegebene Ergebnis zu erhalten, besteht in der Übergabe des Ergebnisses an einen `submitHandler` Bot. Um ein Aufgabenmodul für adaptive Karten auf einer Registerkarte verwenden zu können, muss Ihre App einen Bot enthalten, um Informationen vom Benutzer zurück zu erhalten. Dies wird unten erläutert.

## <a name="example-invoking-a-task-module"></a>Beispiel: Aufrufen eines Aufgabenmoduls

Der folgende Code wird aus dem [Aufgabenmodulbeispiel angepasst.](~/task-modules-and-cards/what-are-task-modules.md#code-sample) So sieht das Aufgabenmodul aus:

![Aufgabenmodul – Benutzerdefiniertes Formular](~/assets/images/task-module/task-module-custom-form.png)

Das `submitHandler` ist sehr einfach; es echot einfach den Wert von oder an die `err` `result` Konsole:

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

Die `submitHandler` Funktion wird mit `TaskInfo.url` verwendet. Die `submitHandler` Funktion befindet sich auf der `TaskInfo.url` Webseite. Wenn beim Aufrufen des Aufgabenmoduls ein Fehler auftritt, wird Ihre Funktion sofort mit einer Zeichenfolge aufgerufen, die angibt, `submitHandler` `err` welcher Fehler aufgetreten [ist.](#task-module-invocation-errors) Die Funktion wird auch mit einer Zeichenfolge aufgerufen, wenn der Benutzer das X oben `submitHandler` `err` rechts im Aufgabenmodul drückt.

Wenn kein Aufruffehler auftritt und der Benutzer X nicht drückt, um ihn zu schließen, drückt der Benutzer nach Abschluss eine Schaltfläche. Je nachdem, ob es sich um eine URL oder eine adaptive Karte im Aufgabenmodul geht, geschieht dies:

### <a name="htmljavascript-taskinfourl"></a>HTML/JavaScript ( `TaskInfo.url` )

Nachdem Sie überprüft haben, was der Benutzer eingegeben hat, rufen Sie die SDK-Funktion auf (im Folgenden als zu `microsoftTeams.tasks.submitTask()` `submitTask()` Lesbarkeitszwecken bezeichnet). Sie können ohne Parameter aufrufen, wenn Sie nur möchten, dass Teams das Aufgabenmodul schließt, aber meistens möchten Sie ein Objekt oder eine Zeichenfolge an `submitTask()` Ihre `submitHandler` übergeben.

Übergeben Sie Ihr Ergebnis als ersten Parameter. Teams ruft das Objekt/die Zeichenfolge auf, das Sie `submitHandler` `err` an übergeben `null` `result` `submitTask()` haben. Wenn Sie einen Parameter aufrufen, müssen Sie ein oder ein Array von Zeichenfolgen übergeben: Auf diese Weise kann Teams überprüfen, ob die App, die das Ergebnis sendet, dieselbe ist, die das Aufgabenmodul aufgerufen `submitTask()` `result`  `appId` `appId` hat.

### <a name="adaptive-card-taskinfocard"></a>Adaptive Karte ( `TaskInfo.card` )

Wenn Sie das Aufgabenmodul mit einem aufgerufen haben, werden die Werte auf der Karte als Wert von zurückgegeben, wenn der Benutzer eine Schaltfläche `submitHandler` `Action.Submit` `result` drückt. Wenn der Benutzer die Esc-Taste drückt oder das X drückt, `err` wird stattdessen zurückgegeben. Wenn Ihre App zusätzlich zu einer Registerkarte einen Bot enthält, können Sie auch einfach den des Bots als `appId` Wert in das Objekt `completionBotId` `TaskInfo` hinzufügen. Der adaptive Kartentext (wie vom Benutzer ausgefüllt) wird über eine Nachricht an den Bot gesendet, wenn der Benutzer `task/submit invoke` eine Schaltfläche `Action.Submit` drückt. Das Schema für das empfangene Objekt ähnelt dem Schema, das Sie für [Aufgaben-/Abruf- und Aufgaben-/Absenden von Nachrichten erhalten.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages) Der einzige Unterschied ist, dass das Schema des JSON-Objekts ein  adaptives Kartenobjekt ist, im Gegensatz zu einem Objekt, das ein adaptives Kartenobjekt enthält, als wenn adaptive Karten mit [Bots verwendet werden.](~/task-modules-and-cards/task-modules/task-modules-bots.md#payload-of-taskfetch-and-tasksubmit-messages)

## <a name="example-submitting-the-result-of-a-task-module"></a>Beispiel: Übermitteln des Ergebnisses eines Aufgabenmoduls

Rufen Sie [das Formular im obigen Aufgabenmodul mit](#example-invoking-a-task-module) einem HTML-Formular auf. Hier ist das Formular definiert:

```html
<form method="POST" id="customerForm" action="/register" onSubmit="return validateForm()">
```

Es gibt fünf Felder in diesem Formular, aber wir interessieren uns nur für die Werte von drei von ihnen für dieses Beispiel: `name` `email` , , und `favoriteBook` .

Hier ist die `validateForm()` Funktion, die `submitTask()` aufruft:

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

Hier sind die möglichen `err` Werte, die von Ihrem empfangen werden `submitHandler` können:

| Problem | Fehlermeldung (Wert von `err` ) |
| ------- | ------------------------------ |
| Werte für beide `TaskInfo.url` und `TaskInfo.card` wurden angegeben. | "Werte für Karte und URL wurden angegeben. Das eine oder andere, aber nicht beides, ist zulässig." |
| Weder `TaskInfo.url` angegeben noch `TaskInfo.card` angegeben. | "Sie müssen einen Wert für eine Karte oder url angeben." |
| `appId`Ungültig. | "Ungültige appId." |
| Der Benutzer hat die X-Taste gedrückt und sie geschlossen. | "Der Benutzer hat das Aufgabenmodul abgebrochen/geschlossen." |
