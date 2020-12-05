---
title: Was sind Aufgabenmodule?
author: clearab
description: Fügen Sie modale Popup-Erlebnisse hinzu, um Informationen für Ihre Benutzer aus Ihren Microsoft Teams-apps zu sammeln oder anzuzeigen.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 44d4e308614763b9da36c2abb7dd150778484c56
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576855"
---
# <a name="what-are-task-modules"></a>Was sind Aufgabenmodule?

Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, ein `<iframe>` -basiertes Widget wie ein YouTube-oder Microsoft Stream-Video anzeigen oder eine [Adaptive Karte](/adaptive-cards/)anzeigen. Sie eignen sich besonders für das Initiieren und Fertigstellen von Aufgaben oder das Anzeigen von Multimedia-Informationen wie Videos oder Power BI-Dashboards. Eine Popup-Oberfläche wirkt für Benutzer, die Aufgaben initiieren und fertigstellen, im Vergleich zu einer Registerkarte oder einer auf einer Unterhaltung basierenden Bot-Umgebung, häufig natürlicher.

Aufgaben Module werden auf der Grundlage von Microsoft Teams-Registerkarten erstellt. Es handelt sich im Wesentlichen um eine Registerkarte innerhalb eines Popupfensters. Sie verwenden das gleiche SDK, wenn Sie also eine Registerkarte erstellt haben, sind Sie bereits 90% der Art und Weise, ein Aufgabenmodul erstellen zu können.

Aufgabenmodule können auf drei Arten aufgerufen werden:

* **Kanal oder persönliche Registerkarten.** Mithilfe des Microsoft Teams Tabs SDK können Sie Aufgaben Module über Schaltflächen, Links oder Menüs auf der Registerkarte aufrufen. [Dies wird hier ausführlich behandelt.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots.** Schaltflächen auf [Karten](~/task-modules-and-cards/cards/cards-reference.md) , die von Ihrem bot gesendet wurden. Dies ist besonders nützlich, wenn Sie nicht alle Benutzer in einem Kanal benötigen, um zu sehen, was Sie mit einem bot machen. Wenn Benutzer beispielsweise auf eine Umfrage in einem Kanal antworten, ist es nicht unbedingt nötig, einen Datensatz der erstellten Umfrage anzuzeigen. [Dies wird hier ausführlich erläutert.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Außerhalb von Teams von einem Deep Link.** Sie können auch URLs erstellen, um ein Aufgabenmodul von einem beliebigen Ort aus aufzurufen. [Dies wird hier ausführlich erläutert.](#task-module-deep-link-syntax)

## <a name="what-a-task-module-looks-like"></a>Wie ein Aufgabenmodul aussieht

So sieht ein Aufgabenmodul aus, wenn es von einem bot aufgerufen wird (natürlich ohne die farbigen Rechtecke und nummerierten Kreise):

![Aufgabenmodul Beispiel](~/assets/images/task-module/task-module-example.png)

Lassen Sie uns das durchgehen:

1. [ `color` Symbol](~/resources/schema/manifest-schema.md#icons)Ihrer APP.
2. [ `short` Name](~/resources/schema/manifest-schema.md#name)Ihrer APP.
3. Der in der `title` -Eigenschaft des [taskinfo-Objekts](#the-taskinfo-object)angegebene Titel des Vorgangs Moduls.
4. Die Schaltfläche close/Cancel des Aufgabenmoduls. Wenn der Benutzer Dies drückt, erhält Ihre APP `err` wie [hier](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)beschrieben ein Ereignis. (**Hinweis:** es ist derzeit nicht möglich, dieses Ereignis zu erkennen, wenn ein Aufgabenmodul von einem bot aufgerufen wird.)
5. Das blaue Rechteck ist das, wo Ihre Webseite angezeigt wird, wenn Sie eine eigene Webseite mit der `url` -Eigenschaft des [taskinfo-Objekts](#the-taskinfo-object)laden. Weitere Details finden Sie im Abschnitt zur [Größenanpassung für Aufgaben Module](#task-module-sizing) weiter unten.
6. Wenn Sie eine Adaptive Karte über die `card` -Eigenschaft des [taskinfo-Objekts](#the-taskinfo-object) anzeigen, wird der Textabstand für Sie hinzugefügt, andernfalls müssen Sie [diese selbst behandeln](#task-module-css-for-htmljavascript-task-modules).
7. Hier werden Adaptive Kartenschaltflächen gerendert. Wenn Sie eine eigene Seite verwenden, müssen Sie Ihre eigenen Schaltflächen erstellen.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Übersicht über das Aufrufen und entfehlen von Aufgaben Modulen

Aufgaben Module können von Tabs, Bots oder Deep Links aufgerufen werden und was in einem HTML-oder adaptiven-Kartenformat angezeigt wird, es gibt also viel Flexibilität hinsichtlich der Art und Weise, wie diese aufgerufen werden und wie das Ergebnis der Interaktion eines Benutzers behandelt werden kann. In der folgenden Tabelle ist die Funktionsweise zusammengefasst:

| **Aufgerufen über...** | **Aufgabenmodul ist HTML/JavaScript** | **Aufgabenmodul ist Adaptive Karte** |
| --- | --- | --- |
| **JavaScript auf einer Registerkarte** | 1. Verwenden der Teams-Client-SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion <br/><br/> 2. Rufen Sie im Code des Aufgabenmoduls, wenn der Benutzer fertig ist, die Microsoft Teams SDK-Funktion `tasks.submitTask()` mit einem `result` Objekt als Parameter auf. Wenn ein `submitHandler` Rückruf in angegeben wurde `tasks.startTask()` , wird er von Teams `result` als Parameter aufgerufen.<br/><br/> 3. Wenn beim Aufrufen eines Fehlers ein Fehler aufgetreten `tasks.startTask()` `submitHandler` ist, wird die Funktion `err` stattdessen mit einer Zeichenfolge aufgerufen. <br/><br/> 4. Sie können auch einen angeben `completionBotId` , wenn ein Aufruf `teams.startTask()` in diesem Fall `result` stattdessen an den bot gesendet wird. | 1. Rufen Sie die Microsoft Teams `tasks.startTask()` -Client-SDK-Funktion mit einem taskinfo- [Objekt](#the-taskinfo-object) auf und `TaskInfo.card` enthält die JSON für die Adaptive Karte, die im Popup des Aufgabenmoduls angezeigt werden soll. <br/><br/> 2. Wenn ein `submitHandler` Rückruf in angegeben wurde `tasks.startTask()` , wird er von Teams mit einer `err` Zeichenfolge aufgerufen, wenn beim Aufrufen ein Fehler aufgetreten ist `tasks.startTask()` oder wenn der Benutzer das Popup des Aufgabenmoduls mit dem X oben rechts schließt. <br/><br/> 3. wenn der Benutzer eine Aktion. Submit-Schaltfläche drückt, `data` wird sein Objekt als Wert von zurückgegeben `result` . |
| **Schaltfläche "bot Card"** | 1. bot-Kartenschaltflächen, je nach Art der Schaltfläche, können Aufgaben Module auf zwei Arten aufrufen: eine Deep Link-URL oder das Senden einer `task/fetch` Nachricht. Siehe unten für die Funktionsweise von Deep Link-URLs. <br/><br/> 2. wenn die Aktion der Schalt `type` Fläche `task/fetch` ( `Action.Submit` Schaltflächentyp für Adaptive Karten) ist, `task/fetch invoke` wird ein Ereignis (ein HTTP-Beitrag unter dem Deckblatt) an den bot gesendet, und der bot antwortet auf den Beitrag mit HTTP 200 und dem Antworttext, der einen Wrapper um das [taskinfo-Objekt](#the-taskinfo-object)enthält. Dies wird ausführlich unter [Aufrufen eines Aufgabenmoduls über Task/FETCH](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-via-taskfetch)erläutert.<br/><br/> 3. Teams zeigt den Aufgabenmodul an; Wenn der Benutzer fertig ist, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem `result` Objekt als Parameter auf. <br/><br/> 4. der bot erhält eine `task/submit invoke` Nachricht, die das `result` Objekt enthält. Sie haben drei verschiedene Möglichkeiten, auf die Nachricht zu Antworten `task/submit` : durch nichts tun (die Aufgabe wurde erfolgreich abgeschlossen), durch Anzeigen einer Nachricht an den Benutzer in einem Popupfenster oder durch Aufrufen eines anderen Vorgangs Modul Fensters (d. h. Erstellen einer Assistenten artigen Umgebung). Diese drei Optionen werden [in der detaillierten Diskussion über Aufgabe/Submit](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit)näher erläutert. | 1. wie Schaltflächen auf bot-Framework-Karten unterstützen Schaltflächen auf adaptiven Karten zwei Möglichkeiten zum Aufrufen von Aufgaben Modulen: Deep Link-URLs mit `Action.openUrl` Schaltflächen und über die `task/fetch` Verwendung von `Action.Submit` Schaltflächen. <br/><br/> 2. Aufgaben Module mit adaptiven Karten funktionieren ähnlich wie beim HTML/JavaScript-Fall (siehe Links). Der Hauptunterschied besteht darin, dass es keine Möglichkeit gibt, sich anzumelden, da es kein JavaScript gibt, wenn Sie Adaptive Karten verwenden `tasks.submitTask()` . Stattdessen übernimmt Teams das `data` Objekt aus `Action.Submit` und gibt es als Nutzlast von im `task/submit` Ereignis zurück, wie [hier](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit)beschrieben. |
| **Deep Link-URL** <br/>[URL-Syntax](#task-module-deep-link-syntax) | 1. Teams Ruft das Aufgabenmodul auf; die URL, die innerhalb des `<iframe>` im `url` -Parameter des Deep-Links angegebenen angezeigt wird. Es ist kein `submitHandler` Rückruf vorhanden. <br/><br/> 2. Rufen Sie im JavaScript der Seite im Aufgabenmodul `tasks.submitTask()` an, es mit einem `result` Objekt als Parameter zu schließen, genauso wie beim Aufrufen von einem Tab oder einer bot-kartenschaltfläche. Die Abschlusslogik unterscheidet sich jedoch geringfügig. Wenn sich Ihre Abschlusslogik auf dem Client befindet (d. h., wenn kein bot vorhanden ist), gibt es keinen `submitHandler` Rückruf, daher muss sich eine Abschlusslogik im Code befinden, der dem Aufruf vorausgeht `tasks.submitTask()` . Aufruffehler werden nur über die Konsole gemeldet. Wenn Sie einen bot haben, können Sie `completionBotId` im Deep-Link einen Parameter angeben, um das `result` Objekt über ein Ereignis zu senden `task/submit` . | 1. Teams Ruft das Aufgabenmodul auf; der JSON-Kartentext der adaptiven Karte wird als URL-codierter Wert des- `card` Parameters des Deep-Links angegeben. <br/><br/> 2. der Benutzer schließt das Aufgabenmodul, indem er auf das X-Symbol oben rechts im Aufgabenmodul klickt oder eine `Action.Submit` Taste auf der Karte drückt. Da kein Aufruf vorhanden ist `submitHandler` , müssen Sie einen bot haben, um den Wert der Felder für Adaptive Karten an zu senden. Verwenden Sie den `completionBotId` -Parameter im Deep-Link, um den bot anzugeben, an den die Daten über ein Ereignis gesendet werden sollen `task/submit invoke` . |

> [!NOTE]
> Das Aufrufen eines Aufgabenmoduls aus JavaScript wird auf mobilen Geräten nicht unterstützt.

## <a name="the-taskinfo-object"></a>Das taskinfo-Objekt

Das `TaskInfo` Objekt enthält die Metadaten für einen Aufgabenmodul. Die Objektdefinition ist unten. Sie **müssen** entweder `url` (für ein eingebettetes IFRAME) oder `card` (für eine Adaptive Karte) definieren.

| Attribut | Typ | Beschreibung |
| --- | --- | --- |
| `title` | string | Wird unterhalb des App-namens und rechts neben dem App-Symbol angezeigt. |
| `height` | Zahl oder Zeichenfolge | Hierbei kann es sich um eine Zahl handeln, die die Höhe des Aufgabenmoduls in Pixeln darstellt, oder `small` , oder `medium` `large` . [Unten sehen Sie, wie die Höhe und Breite gehandhabt werden](#task-module-sizing). |
| `width` | Zahl oder Zeichenfolge | Hierbei kann es sich um eine Zahl handeln, die die Breite des Aufgabenmoduls in Pixeln darstellt, oder `small` , oder `medium` `large` . [Unten sehen Sie, wie die Höhe und Breite gehandhabt werden](#task-module-sizing). |
| `url` | string | Die URL der Seite, die als `<iframe>` innerhalb des Aufgabenmoduls geladen wurde. Die Domäne der URL muss sich im [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der APP im App-Manifest befinden. |
| `card` | Adaptive Karte oder eine Adaptive Card-bot-Karten Anlage | Die JSON für die Adaptive Karte, die im Aufgabenmodul angezeigt werden soll. Wenn Sie von einem bot aus aufrufen, müssen Sie die Adaptive Card JSON in einem bot-Framework- `attachment` Objekt verwenden. Auf einer Registerkarte verwenden Sie nur eine Adaptive Karte. [Hier ist ein Beispiel.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | string | Wenn ein Client das Feature "Aufgabenmodul" nicht unterstützt, wird diese URL in einer Browserregister Karte geöffnet. |
| `completionBotId` | string | Gibt eine bot-APP-ID an, an die das Ergebnis der Interaktion des Benutzers mit dem Aufgabenmodul gesendet werden soll. Wenn angegeben, erhält der bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast. |

> [!NOTE]
> Das Feature "Aufgabenmodul" erfordert, dass die Domänen aller URLs, die Sie laden möchten, im Manifest der APP im Array enthalten sind `validDomains` .

## <a name="task-module-sizing"></a>Größe des Aufgabenmoduls

Mit ganzen Zahlen für `TaskInfo.width` und `TaskInfo.height` wird die Höhe und Breite in Pixeln festgelegt. Je nach Größe des Team Fensters und Bildschirmauflösung werden diese jedoch proportional reduziert, wobei das Seitenverhältnis (Breite/Höhe) beibehalten wird.

If `TaskInfo.width` und `TaskInfo.height` are `"small"` , `"medium"` oder `"large"` die Größe des roten Rechtecks im obigen Bild ist ein Anteil des verfügbaren Speicherplatzes: 20%, 50%, 60% für `width` und 20%, 50%, 66% für `height` .

Aufgaben Module, die von einer Registerkarte aufgerufen werden, können dynamisch angepasst werden. Nach dem Aufruf `tasks.startTask()` können Sie aufrufen, `tasks.updateTask(newSize)` wo die Eigenschaften Height und Width für das taskinfo-Objekt der Spezifikation (ex) entsprechen. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>Aufgabenmodul CSS für HTML/JavaScript-Aufgaben Module

HTML/JavaScript-basierte Aufgaben Module haben Zugriff auf den gesamten Bereich des Aufgabenmoduls unterhalb der Kopfzeile. Das bietet zwar viel Flexibilität, wenn Sie die Ränder an den Kopfzeilen Elementen ausrichten und unnötige Bildlaufleisten vermeiden möchten, müssen Sie das richtige CSS bereitstellen. Hier sind einige Beispiele für einige Anwendungsfälle.

### <a name="example-1---youtube-video"></a>Beispiel 1 – YouTube-Video

YouTube bietet die Möglichkeit zum Einbetten von Videos auf Webseiten. Wenn Sie eine einfache Stub-Webseite verwenden, können Sie dies in einem Aufgabenmodul einfach anzeigen:

![YouTube-Video](~/assets/images/task-module/youtube-example.png)

Hier ist der HTML-Code für diese Seite ohne CSS:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  ⋮
</head>
<body>
  <div id="embed-container">
    <iframe width="1000" height="700" src="https://www.youtube.com/embed/rd0Rd8w3FZ0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen=""></iframe>
  </div>
</body>
</html>
```

Die CSS sieht wie folgt aus:

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 95%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

### <a name="example-2---powerapp"></a>Beispiel 2-PowerApp

Sie können den gleichen Ansatz verwenden, um auch ein PowerApp einzubetten. Da die Höhe/Breite jedes einzelnen PowerApp anpassbar ist, müssen Sie möglicherweise die Höhe und Breite anpassen, um die gewünschte Präsentation zu erzielen.

![Asset Management PowerApp](~/assets/images/task-module/powerapp-example.png)

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

Und die CSS lautet wie folgt:

```css
#embed-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 94%;
    height: 95%;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-style: none;
}
```

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Adaptive Card oder Adaptive Card bot Card-Anlage

Wie bereits erwähnt, müssen Sie, je nachdem, wie Sie Ihren Anruf durch `card` führen, entweder eine Adaptive Karte oder einen Adaptive Card-bot-Karten Anhang verwenden (Dies ist nur eine Adaptive Karte, die in ein Attachment-Objekt eingeschlossen ist).

Wenn Sie auf einer Registerkarte aufrufen, müssen Sie eine Adaptive Karte verwenden. Hier ist ein sehr einfaches Beispiel:

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat:"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png",
            "size": "Medium"
        }
    ],
    "version": "1.0"
}
```

Wenn Sie von einem bot aus aufrufen, müssen Sie eine Adaptive Card-bot-Karten Anlage wie im folgenden Beispiel verwenden:

```json
{
    "contentType": "application/vnd.microsoft.card.adaptive",
    "content": {
        "type": "AdaptiveCard",
        "body": [
            {
                "type": "TextBlock",
                "text": "Here is a ninja cat:"
            },
            {
                "type": "Image",
                "url": "http://adaptivecards.io/content/cats/1.png",
                "size": "Medium"
            }
        ],
        "version": "1.0"
    }
}
```

Sie müssen sich daran erinnern, ob Sie ein Aufgabenmodul aufrufen, das eine Adaptive Karte von einem bot oder einer Registerkarte enthält.

## <a name="task-module-deep-link-syntax"></a>Syntax des Aufgabenmoduls Deep Link

Ein Aufgabenmodul-Deep Link ist nur eine Serialisierung des [taskinfo-Objekts](#the-taskinfo-object) mit zwei weiteren Informationen `APP_ID` und optional `BOT_APP_ID` Folgendes:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Weitere Informationen finden Sie unter [taskinfo-Objekt](#the-taskinfo-object) für die Datentypen und zulässigen Werte für,,,, `<TaskInfo.url>` `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` und `<TaskInfo.title>` .

> [!TIP]
> Achten Sie darauf, die Deep Link-URL zu codieren, insbesondere bei Verwendung des `card` Parameters (beispielsweise JavaScript- [ `encodeURI()` Funktion](https://www.w3schools.com/jsref/jsref_encodeURI.asp)).

Hier finden Sie die folgenden `APP_ID` Informationen `BOT_APP_ID` :

| Wert | Typ | Pflichtfeld? | Beschreibung |
| --- | --- | --- | --- |
| `APP_ID` | string | Ja | Die [ID](~/resources/schema/manifest-schema.md#id) der APP, die den Aufgabenmodul aufruft. Das [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) im Manifest für `APP_ID` muss die Domäne für `url` if `url` in der URL enthalten. (Die APP-ID ist bereits bekannt, wenn ein Aufgabenmodul von einer Registerkarte oder einem bot aufgerufen wird, weshalb Sie nicht in enthalten ist `TaskInfo` .) |
| `BOT_APP_ID` | string | Nein | Wenn ein Wert für `completionBotId` angegeben ist, `result` wird das Objekt über eine a- `task/submit invoke` Nachricht an den angegebenen bot gesendet. `BOT_APP_ID` muss im Manifest der App als bot angegeben werden, d. h., Sie können Sie nicht einfach an einen bot senden. |

Beachten Sie, dass es gültig für `APP_ID` und `BOT_APP_ID` identisch ist und in vielen Fällen sein wird, wenn eine APP einen Bot hat, da es empfehlenswert ist, dies als APP-ID zu verwenden, wenn eine vorhanden ist.

## <a name="keyboard-and-accessibility-guidelines"></a>Richtlinien für Tastatur und Barrierefreiheit

Mit HTML/JavaScript-basierten Aufgaben Modulen ist es Ihre Aufgabe, sicherzustellen, dass das Aufgabenmodul Ihrer APP mit einer Tastatur verwendet werden kann. Bildschirmsprachausgabe Programme hängen auch von der Fähigkeit ab, mit der Tastatur zu navigieren. Als praktische Angelegenheit bedeutet dies zwei Dinge:

1. Verwenden des [TabIndex-Attributs](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können und ob/wo Sie an der sequenziellen Tastaturnavigation teilnimmt (in der Regel mit den <kbd>Tab</kbd> <kbd>-und UMSCHALT</kbd> Tastern).
2. Behandeln der <kbd>ESC</kbd> -Taste im JavaScript für Ihr Aufgabenmodul. Im folgenden finden Sie ein Codebeispiel, in dem gezeigt wird, wie Sie vorgehen:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

Microsoft Teams stellt sicher, dass die Tastaturnavigation ordnungsgemäß in der Kopfzeile des Aufgabenmoduls in Ihrem HTML-Code und umgekehrt funktioniert.

## <a name="task-module-samples"></a>Aufgabenmodul Beispiele

* [Node.js/TypeScript-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-nodejs)
* [C#-/.NET-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-task-module-csharp)

> [!div class="nextstepaction"]
> [Weitere Informationen: Anfordern von Geräte Berechtigungen](/concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
>[Weitere Informationen: Berechtigungen für Kamera und Bildergalerie](/concepts/device-capabilities/mobile-camera-image-permissions.md)
