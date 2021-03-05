---
title: Was sind Aufgabenmodule?
author: clearab
description: Fügen Sie modale Popuperfahrungen hinzu, um Informationen zu Ihren Benutzern aus Ihren Microsoft Teams-Apps zu sammeln oder ihren Benutzern zu zeigen.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 3920d3ae71857dcc7673c4c27449b71009c7f07e
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449549"
---
# <a name="what-are-task-modules"></a>Was sind Aufgabenmodule?

Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Erlebnissen in Ihrer Teams-Anwendung. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, ein -basiertes Widget wie ein YouTube- oder Microsoft Stream-Video anzeigen oder eine `<iframe>` [adaptive Karte anzeigen.](/adaptive-cards/) Sie eignen sich besonders für das Initiieren und Fertigstellen von Aufgaben oder das Anzeigen von Multimedia-Informationen wie Videos oder Power BI-Dashboards. Eine Popup-Oberfläche wirkt für Benutzer, die Aufgaben initiieren und fertigstellen, im Vergleich zu einer Registerkarte oder einer auf einer Unterhaltung basierenden Bot-Umgebung, häufig natürlicher.

Aufgabenmodule, die auf den Registerkarten von Microsoft Teams aufbauen; Sie sind im Wesentlichen eine Registerkarte innerhalb eines Popupfensters. Sie verwenden dasselbe SDK. Wenn Sie also eine Registerkarte erstellt haben, sind Sie bereits zu 90 % in der Lage, ein Aufgabenmodul zu erstellen.

Aufgabenmodule können auf drei Arten aufgerufen werden:

* **Kanal- oder persönliche Registerkarten.** Mithilfe des Microsoft Teams Tabs SDK können Sie Aufgabenmodule über Schaltflächen, Links oder Menüs auf Ihrer Registerkarte aufrufen. Dies wird hier ausführlich [behandelt.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots.** Schaltflächen [auf Karten,](~/task-modules-and-cards/cards/cards-reference.md) die von Ihrem Bot gesendet werden. Dies ist besonders hilfreich, wenn Sie nicht alle in einem Kanal benötigen, um zu sehen, was Sie mit einem Bot tun. Wenn Benutzer beispielsweise auf eine Umfrage in einem Kanal antworten, ist es nicht unbedingt nötig, einen Datensatz der erstellten Umfrage anzuzeigen. [Dies wird hier ausführlich behandelt.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Außerhalb von Teams über einen tiefen Link.** Sie können auch URLs zum Aufrufen eines Aufgabenmoduls von überall aus erstellen. [Dies wird hier ausführlich behandelt.](#task-module-deep-link-syntax)

## <a name="what-a-task-module-looks-like"></a>So sieht ein Aufgabenmodul aus

So sieht ein Aufgabenmodul aus, wenn es von einem Bot aufgerufen wird (natürlich ohne die farbigen Rechtecke und nummerierten Kreise):

![Beispiel für das Aufgabenmodul](~/assets/images/task-module/task-module-example.png)

Gehen wir nun durch:

1. Das Symbol Ihrer [ `color` App](~/resources/schema/manifest-schema.md#icons).
2. Der Name Ihrer [ `short` App](~/resources/schema/manifest-schema.md#name).
3. Der Titel des Aufgabenmoduls, der in der `title` Eigenschaft des [TaskInfo-Objekts angegeben ist.](#the-taskinfo-object)
4. Die Schaltfläche "Schließen/Abbrechen" des Aufgabenmoduls. Wenn der Benutzer dies drückt, erhält Ihre App ein `err` Ereignis wie hier [beschrieben.](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module) (**Hinweis:** Es ist derzeit nicht möglich, dieses Ereignis zu erkennen, wenn ein Aufgabenmodul von einem Bot aufgerufen wird.)
5. Das blaue Rechteck ist die Stelle, an der Ihre Webseite angezeigt wird, wenn Sie eine eigene Webseite mit der Eigenschaft des `url` [TaskInfo-Objekts laden.](#the-taskinfo-object) Weitere Details finden Sie im Abschnitt [zur Größenanpassung des](#task-module-sizing) Aufgabenmoduls weiter unten.
6. Wenn Sie eine adaptive Karte über die Eigenschaft des TaskInfo-Objekts anzeigen, wird der Abstand für Sie hinzugefügt, andernfalls müssen Sie dies `card` [selbst behandeln.](#task-module-css-for-htmljavascript-task-modules) [](#the-taskinfo-object)
7. Schaltflächen für adaptive Karten werden hier gerendert. Wenn Sie Eine eigene Seite verwenden, müssen Sie eigene Schaltflächen erstellen.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Übersicht über das Aufrufen und Schließen von Aufgabenmodulen

Aufgabenmodule können von Registerkarten, Bots oder Tiefenlinks aufgerufen werden, und was in einer angezeigt wird, kann entweder HTML oder eine adaptive Karte sein. Daher gibt es viel Flexibilität hinsichtlich der Art und Weise, wie sie aufgerufen werden und wie sie mit dem Ergebnis der Benutzerinteraktion umgehen. In der folgenden Tabelle wird zusammengefasst, wie dies funktioniert:

| **Aufgerufen über...** | **Aufgabenmodul ist HTML/JavaScript** | **Aufgabenmodul ist adaptive Karte** |
| --- | --- | --- |
| **JavaScript auf einer Registerkarte** | 1. Verwenden der Teams-Client-SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion <br/><br/> 2. Rufen Sie im Aufgabenmodulcode nach Abschluss des Benutzers die Teams SDK-Funktion mit einem `tasks.submitTask()` `result` Objekt als Parameter auf. Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn mit als `result` Parameter auf.<br/><br/> 3. Wenn beim Aufrufen ein Fehler aufgetreten ist, wird die Funktion stattdessen `tasks.startTask()` `submitHandler` mit einer Zeichenfolge `err` aufgerufen. <br/><br/> 4. Sie können auch beim Aufrufen einen angeben – in diesem `completionBotId` Fall wird stattdessen an den Bot `teams.startTask()` `result` gesendet. | 1. Rufen Sie die Teams-Client-SDK-Funktion mit einem TaskInfo-Objekt auf und enthält das JSON für die adaptive Karte, die im Popup des `tasks.startTask()` [](#the-taskinfo-object) `TaskInfo.card` Aufgabenmoduls angezeigt werden soll. <br/><br/> 2. Wenn ein Rückruf in angegeben wurde, ruft Teams ihn mit einer Zeichenfolge auf, wenn beim Aufrufen ein Fehler aufgetreten ist oder wenn der Benutzer das Popup des Aufgabenmoduls mit dem X oben rechts `submitHandler` `tasks.startTask()` `err` `tasks.startTask()` schließt. <br/><br/> 3. Wenn der Benutzer eine Action.Submit-Schaltfläche drückt, wird sein Objekt als `data` Wert von `result` zurückgegeben. |
| **Botkartenschaltfläche** | 1. Bot-Kartenschaltflächen können je nach Schaltflächentyp aufgabenmodule auf zwei Arten aufrufen: eine Deep Link-URL oder durch Senden einer `task/fetch` Nachricht. Wie deep link URLs funktionieren, erfahren Sie unten. <br/><br/> 2. Wenn die Aktion der Schaltfläche ist ( Schaltflächentyp für adaptive Karten), wird ein Ereignis (http POST unter den Deckeln) an den Bot gesendet, und der Bot antwortet auf den POST mit `type` `task/fetch` HTTP 200 und den Antworttext, der einen Wrapper um das `Action.Submit` `task/fetch invoke` [TaskInfo-Objekt](#the-taskinfo-object)enthält. Dies wird im Aufrufen eines Aufgabenmoduls über [task/fetch ausführlich erläutert.](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-via-taskfetch)<br/><br/> 3. Teams zeigt das Aufgabenmodul an. Wenn der Benutzer fertig ist, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem Objekt als Parameter `result` auf. <br/><br/> 4. Der Bot empfängt eine `task/submit invoke` Nachricht, die das Objekt `result` enthält. Sie haben drei verschiedene Möglichkeiten, auf die Nachricht zu reagieren: indem Sie nichts tun (die Aufgabe wurde erfolgreich abgeschlossen), indem Sie dem Benutzer eine Nachricht in einem Popupfenster anzeigen oder ein anderes Aufgabenmodulfenster aufrufen (d. h. eine Assistentenerfahrung `task/submit` erstellen). Diese drei Optionen werden in der ausführlichen Diskussion zu [Aufgabe/Absenden ausführlicher behandelt.](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit) | 1. Wie Schaltflächen auf Bot Framework-Karten unterstützen Schaltflächen auf adaptiven Karten zwei Methoden zum Aufrufen von Aufgabenmodulen: Deep Link-URLs mit Schaltflächen und über die Verwendung von `Action.openUrl` `task/fetch` `Action.Submit` Schaltflächen. <br/><br/> 2. Aufgabenmodule mit adaptiven Karten funktionieren sehr ähnlich wie der HTML/JavaScript-Fall (siehe links). Der Hauptunterschied besteht in dem, dass es keine Möglichkeit zum Aufrufen gibt, da es kein JavaScript gibt, wenn Sie adaptive Karten `tasks.submitTask()` verwenden. Stattdessen übernimmt Teams das Objekt und gibt es als Nutzlast `data` `Action.Submit` des Ereignisses `task/submit` zurück, wie hier [beschrieben.](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit) |
| **URL für tiefe Verknüpfungen** <br/>[#A0](#task-module-deep-link-syntax) | 1. Teams ruft das Aufgabenmodul auf. die URL, die im angegebenen Parameter des Deep-Links `<iframe>` `url` angezeigt wird. Es gibt keinen `submitHandler` Rückruf. <br/><br/> 2. Rufen Sie im JavaScript der Seite im Aufgabenmodul auf, um es mit einem Objekt als Parameter zu schließen, genauso wie beim Aufrufen von einer Registerkarte oder einer Botkartenschaltfläche. `tasks.submitTask()` `result` Die Fertigstellungslogik ist jedoch etwas anders. Wenn sich Ihre Fertigstellungslogik auf dem Client befindet (d. h. wenn kein Bot enthalten ist), gibt es keinen Rückruf, daher muss sich jede Abschlusslogik im Code vor dem Aufruf von `submitHandler` `tasks.submitTask()` befinden. Aufruffehler werden nur über die Konsole gemeldet. Wenn Sie über einen Bot verfügen, können Sie einen Parameter in der Tiefenverknüpfung angeben, um das Objekt über `completionBotId` `result` ein Ereignis zu `task/submit` senden. | 1. Teams ruft das Aufgabenmodul auf. Der Textkörper der JSON-Karte der adaptiven Karte wird als URL-codierter Wert des Parameters des `card` Deep-Links angegeben. <br/><br/> 2. Der Benutzer schließt das Aufgabenmodul, indem er oben rechts im Aufgabenmodul auf das X klickt oder eine Schaltfläche `Action.Submit` auf der Karte drückt. Da kein Anruf besteht, müssen Sie über einen Bot verfügen, um den Wert der Felder für `submitHandler` adaptive Karten an zu senden. Verwenden Sie den Parameter im deep-Link, um den Bot anzugeben, an den `completionBotId` die Daten über ein Ereignis gesendet `task/submit invoke` werden. |

> [!NOTE]
> Das Aufrufen eines Aufgabenmoduls aus JavaScript wird auf Mobilgeräten nicht unterstützt.

## <a name="the-taskinfo-object"></a>Das TaskInfo-Objekt

Das `TaskInfo` Objekt enthält die Metadaten für ein Aufgabenmodul. Die Objektdefinition ist unten. Sie **müssen** entweder `url` (für einen eingebetteten iFrame) oder `card` (für eine adaptive Karte) definieren.

| Attribut | Typ | Beschreibung |
| --- | --- | --- |
| `title` | string | Wird unterhalb des App-Namens und rechts neben dem App-Symbol angezeigt. |
| `height` | Zahl oder Zeichenfolge | Dies kann eine Zahl sein, die die Höhe des Aufgabenmoduls in Pixel oder `small` , `medium` oder `large` darstellt. [Siehe unten, wie Höhe und Breite behandelt werden.](#task-module-sizing) |
| `width` | Zahl oder Zeichenfolge | Dies kann eine Zahl sein, die die Breite des Aufgabenmoduls in Pixel oder `small` , `medium` oder `large` darstellt. [Siehe unten, wie Höhe und Breite behandelt werden.](#task-module-sizing) |
| `url` | string | Die URL der Seite, die als innerhalb des `<iframe>` Aufgabenmoduls geladen wurde. Die Domäne der URL muss sich im [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der App im Manifest Ihrer App befinden. |
| `card` | Adaptive Karte oder adaptive Karten-Bot-Kartenanlage | Die JSON für die adaptive Karte, die im Aufgabenmodul angezeigt werden soll. Wenn Sie von einem Bot aufrufen, müssen Sie die adaptive Karten-JSON in einem Bot Framework-Objekt `attachment` verwenden. Auf einer Registerkarte verwenden Sie nur eine adaptive Karte. [Hier ist ein Beispiel.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | string | Wenn ein Client das Aufgabenmodulfeature nicht unterstützt, wird diese URL auf einer Browserregisterkarte geöffnet. |
| `completionBotId` | string | Gibt eine Bot-App-ID an, an die das Ergebnis der Benutzerinteraktion mit dem Aufgabenmodul gesendet werden soll. Wenn angegeben, erhält der Bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast. |

> [!NOTE]
> Das Aufgabenmodulfeature erfordert, dass die Domänen aller URLs, die Sie laden möchten, im Array im Manifest Ihrer `validDomains` App enthalten sind.

## <a name="task-module-sizing"></a>Größe des Aufgabenmoduls

Mit ganzzahligen Zahlen `TaskInfo.width` für und wird die Höhe und Breite in Pixel `TaskInfo.height` festgelegt. Je nach Größe des Fensters und der Bildschirmauflösung des Teams werden sie jedoch proportional reduziert, während das Seitenverhältnis (Breite/Höhe) beibehalten wird.

Wenn und sind , oder die Größe des roten Rechtecks in der obigen Abbildung ist ein Anteil des verfügbaren `TaskInfo.width` `TaskInfo.height` `"small"` `"medium"` Platzes: `"large"` 20 %, 50 %, 60 % für und `width` 20 %, 50 %, 66 % für `height` .

Aufgabenmodule, die von einer Registerkarte aufgerufen werden, können dynamisch geändert werden. Nach dem Aufruf können Sie aufrufen, wo die Höhen- und Breiteneigenschaften des `tasks.startTask()` `tasks.updateTask(newSize)` newSize-Objekts der TaskInfo-Spezifikation entsprechen (z. B. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>Aufgabenmodul-CSS für HTML-/JavaScript-Aufgabenmodule

HTML/JavaScript-basierte Aufgabenmodule haben Zugriff auf den gesamten Bereich des Aufgabenmoduls unterhalb der Kopfzeile. Dies bietet zwar sehr viel Flexibilität, aber wenn Sie möchten, dass der Abstand an den Rändern an den Kopfzeilenelementen ausgerichtet wird und unnötige Bildlaufleisten vermieden werden, müssen Sie die richtige CSS bereitstellen. Im Folgenden finden Sie einige Beispiele für einige Anwendungsfälle.

### <a name="example-1---youtube-video"></a>Beispiel 1 – YouTube-Video

YouTube bietet die Möglichkeit, Videos auf Webseiten einzubetten. Mithilfe einer einfachen Stubwebseite können Sie dies ganz einfach in einem Aufgabenmodul anzeigen:

![YouTube-Video](~/assets/images/task-module/youtube-example.png)

Hier ist der HTML-Code für diese Seite, ohne die CSS:

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

Die CSS sieht wie dies aus:

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

### <a name="example-2---powerapp"></a>Beispiel 2 – PowerApp

Sie können denselben Ansatz auch verwenden, um eine PowerApp einzubetten. Da die Höhe/Breite einer einzelnen PowerApp anpassbar ist, müssen Sie möglicherweise die Höhe und Breite anpassen, um die gewünschte Präsentation zu erreichen.

![Asset Management PowerApp](~/assets/images/task-module/powerapp-example.png)

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

Die CSS ist:

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Adaptive Karte oder adaptive Karten-Bot-Kartenanlage

Wie bereits erwähnt, müssen Sie je nachdem, wie Sie Ihre karte aufrufen, entweder eine adaptive Karte oder eine adaptive Karten-Bot-Kartenanlage verwenden (die nur eine adaptive Karte ist, die in ein Anlageobjekt verpackt `card` ist).

Wenn Sie von einer Registerkarte aufrufen, müssen Sie eine adaptive Karte verwenden. Hier ist ein sehr einfaches Beispiel:

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

Wenn Sie von einem Bot aufrufen, müssen Sie eine adaptive Karten-Bot-Kartenanlage wie im folgenden Beispiel verwenden:

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

Sie müssen sich merken, ob Sie ein Aufgabenmodul aufrufen, das eine adaptive Karte von einem Bot oder einer Registerkarte enthält.

## <a name="task-module-deep-link-syntax"></a>Syntax für tiefe Verknüpfungen des Aufgabenmoduls

Ein Tiefenlink des Aufgabenmoduls ist nur eine Serialisierung des [TaskInfo-Objekts](#the-taskinfo-object) mit zwei weiteren Informationen, `APP_ID` und optional die `BOT_APP_ID` :

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Unter [TaskInfo-Objekt](#the-taskinfo-object) finden Sie die Datentypen und zulässigen Werte für `<TaskInfo.url>` , , , und `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` .

> [!TIP]
> Achten Sie darauf, den Tiefenlink url zu codieren, insbesondere bei Verwendung des Parameters (z. B. `card` JavaScript-Funktion ). [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)

Hier sind die Informationen zu `APP_ID` und `BOT_APP_ID` :

| Wert | Typ | Pflichtfeld? | Beschreibung |
| --- | --- | --- | --- |
| `APP_ID` | string | Ja | Die [ID](~/resources/schema/manifest-schema.md#id) der App, die das Aufgabenmodul aufrufen. Das [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) im Manifest für muss die Domäne für `APP_ID` if in der URL `url` `url` enthalten. (Die App-ID ist bereits bekannt, wenn ein Aufgabenmodul von einer Registerkarte oder einem Bot aufgerufen wird, weshalb sie nicht in `TaskInfo` enthalten ist.) |
| `BOT_APP_ID` | string | Nein | Wenn ein Wert für angegeben wird, wird das Objekt über eine `completionBotId` `result` Nachricht an den `task/submit invoke` angegebenen Bot gesendet. `BOT_APP_ID` muss im Manifest der App als Bot angegeben werden, d. h. Sie können ihn nicht einfach an einen bot senden. |

Beachten Sie, dass es gültig für und gleich ist, und in vielen Fällen ist, wenn eine App über einen Bot verfügt, da es empfohlen wird, dies als ID einer App zu verwenden, wenn es einen `APP_ID` `BOT_APP_ID` gibt.

## <a name="keyboard-and-accessibility-guidelines"></a>Richtlinien für Tastatur und Barrierefreiheit

Bei HTML/JavaScript-basierten Aufgabenmodulen liegt es in Ihrer Verantwortung, sicherzustellen, dass das Aufgabenmodul Ihrer App mit einer Tastatur verwendet werden kann. Sprachausgabeprogramme hängen auch von der Möglichkeit ab, über die Tastatur zu navigieren. Praktisch bedeutet dies zwei Dinge:

1. Verwenden Sie [das tabindex-Attribut](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können und ob/wo es an der sequenziellen Tastaturnavigation (in der Regel mit den <kbd>Tab-</kbd> und Umschalttasten) beteiligt ist. <kbd></kbd>
2. Behandeln des <kbd>Esc-Schlüssels</kbd> im JavaScript für Ihr Aufgabenmodul. Im Folgenden finden Sie ein Codebeispiel, das dies zeigt:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

Microsoft Teams stellt sicher, dass die Tastaturnavigation vom Aufgabenmodulheader in Ihren HTML ordnungsgemäß funktioniert und umgekehrt.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodulbeispiel (Bots-V4) | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 
|Aufgabenmodulbeispiel (Tabs + Bots-V3) | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|



> [!div class="nextstepaction"]
> [Weitere Informationen: Anfordern von Geräteberechtigungen](../concepts/device-capabilities/native-device-permissions.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von QR- oder Barcodescannerfunktionen in Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Weitere Informationen: Integrieren von Standortfunktionen in Teams](../concepts/device-capabilities/location-capability.md)