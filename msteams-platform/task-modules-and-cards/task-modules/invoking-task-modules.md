---
title: Aufrufen und Schließen von Aufgabenmodulen
description: Erfahren Sie mehr über das Aufrufen und Schließen von Aufgabenmodulen, Aufgabeninformationsobjekt, Aufgabenmodulgröße, Aufgabenmodul-Deep-Link-Syntax mithilfe von Codebeispielen
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 84cca74d6e81dce9bbcd7637b5d0b6537524d831
ms.sourcegitcommit: a36760750ff4f510c374a4c956be57f7c1b4a0db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2022
ms.locfileid: "63674726"
---
# <a name="invoke-and-dismiss-task-modules"></a>Aufrufen und Schließen von Aufgabenmodulen

Aufgabenmodule können über Registerkarten, Bots oder Deep-Links aufgerufen werden. Die Antwort kann entweder in HTML, JavaScript oder als adaptive Karte erfolgen. Es gibt eine große Flexibilität hinsichtlich der Art und Weise, wie Aufgabenmodule aufgerufen werden und wie sie mit der Reaktion der Benutzerinteraktion umzugehen sind. In der folgenden Tabelle wird die Funktionsweise zusammengefasst:

| Wird mithilfe von | Aufgabenmodul mit HTML oder JavaScript | Aufgabenmodul mit adaptiver Karte |
| --- | --- | --- |
| JavaScript auf einer Registerkarte | 1. Verwenden Sie die Teams Client-SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion. <br/><br/> 2. Rufen Sie im Aufgabenmodulcode, wenn der Benutzer die Aktionen ausgeführt hat, die Teams SDK-Funktion `tasks.submitTask()` mit einem `result` Objekt als Parameter auf. Wenn ein `submitHandler` Rückruf in `tasks.startTask()`angegeben wurde, ruft Teams ihn `result` als Parameter auf. Wenn beim Aufrufen `tasks.startTask()`ein Fehler aufgetreten ist, wird die `submitHandler` Funktion stattdessen mit einer `err` Zeichenfolge aufgerufen. <br/><br/> 3. Sie können auch eine `completionBotId` beim Aufrufen `teams.startTask()`angeben. Dann wird er `result` stattdessen an den Bot gesendet. | 1. Rufen Sie die Teams Client-SDK-Funktion `tasks.startTask()` mit einem [TaskInfo-Objekt](#the-taskinfo-object) auf und `TaskInfo.card` enthalten den JSON-Code für die adaptive Karte, die im Aufgabenmodul-Popup angezeigt werden soll. <br/><br/> 2. Wenn ein `submitHandler` Rückruf in `tasks.startTask()`angegeben wurde, ruft Teams ihn mit einer `err` Zeichenfolge auf, wenn beim Aufrufen `tasks.startTask()` ein Fehler aufgetreten ist oder wenn der Benutzer das Aufgabenmodul-Popup mit dem X oben rechts schließt. <br/><br/> 3. Wenn der Benutzer eine `Action.Submit` Schaltfläche drückt, wird sein `data` Objekt als Wert von `result`zurückgegeben. |
| Bot-Kartenschaltfläche | 1. Botkartenschaltflächen können, abhängig vom Typ der Schaltfläche, Aufgabenmodule auf zwei Arten aufrufen: eine Deep-Link-URL oder durch Senden einer `task/fetch` Nachricht. <br/><br/> 2. Wenn die Aktion `type` `task/fetch` der Schaltfläche den Schaltflächentyp für adaptive Karten darstellt `Action.Submit` , wird ein `task/fetch invoke` Ereignis, bei dem es sich um einen HTTP-POST handelt, an den Bot gesendet. Der Bot antwortet auf den POST mit HTTP 200 und den Antworttext, der einen Wrapper um das [TaskInfo-Objekt](#the-taskinfo-object) enthält. Weitere Informationen finden Sie unter [Aufrufen eines Aufgabenmoduls mithilfe von `task/fetch`](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch). Teams zeigt das Aufgabenmodul an. <br/><br/> 3. Nachdem der Benutzer die Aktionen ausgeführt hat, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem `result` Objekt als Parameter auf. Der Bot empfängt eine `task/submit invoke` Nachricht, die das `result` Objekt enthält. <br/><br/> 4. Sie haben drei verschiedene Möglichkeiten, auf die `task/submit` Nachricht zu reagieren, indem Sie nichts tun, was die Aufgabe erfolgreich abgeschlossen hat, indem Sie dem Benutzer eine Nachricht in einem Popupfenster anzeigen oder ein anderes Aufgabenmodulfenster aufrufen. Weitere Informationen finden Sie in [den ausführlichen Erläuterungen zu `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | <ul><li> Wie Schaltflächen auf Bot Framework-Karten unterstützen Schaltflächen auf adaptiven Karten zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen, Deep-Link-URLs mit `Action.openUrl` Schaltflächen und `task/fetch` zum Verwenden von `Action.Submit` Schaltflächen. </li></ul> <br/><br/> <ul><li> Aufgabenmodule mit adaptiven Karten funktionieren sehr ähnlich wie der HTML- oder JavaScript-Fall. Der Hauptunterschied besteht darin, dass es keine Möglichkeit gibt, adaptive Karten aufzurufen, da es kein JavaScript gibt, wenn Sie adaptive Karten verwenden `tasks.submitTask()`. Stattdessen übernimmt Teams das `data` Objekt und gibt es als Nutzlast des `task/submit` Ereignisses zurück`Action.Submit`. Weitere Informationen finden Sie unter [Flexibilität von `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). </li></ul> |
| Deep-Link-URL <br/>[URL-Syntax](#task-module-deep-link-syntax) | 1. Teams ruft das Aufgabenmodul auf, bei dem es sich um die URL handelt, die innerhalb des `<iframe>` angegebenen Parameters `url` des Deep-Links angezeigt wird. Es gibt keinen `submitHandler` Rückruf. <br/><br/> 2. Rufen `tasks.submitTask()` Sie innerhalb des JavaScript der Seite im Aufgabenmodul auf, es mit einem `result` Objekt als Parameter zu schließen, genauso wie beim Aufrufen von einer Registerkarte oder einer Bot-Kartenschaltfläche. Die Abschlusslogik unterscheidet sich jedoch geringfügig. Wenn sich die Abschlusslogik auf dem Client befindet, der sich befindet, wenn kein Bot vorhanden ist, gibt es keinen `submitHandler` Rückruf, daher muss sich jede Vervollständigungslogik im Code vor dem Aufruf von `tasks.submitTask()`befinden. Aufruffehler werden nur über die Konsole gemeldet. Wenn Sie über einen Bot verfügen, können Sie im Deep-Link einen `completionBotId` Parameter angeben, um das `result` Objekt über ein `task/submit` Ereignis zu senden. | 1. Teams ruft das Aufgabenmodul auf, bei dem es sich um den JSON-Kartentext der adaptiven Karte handelt, die als URL-codierter Wert des `card` Parameters des Deep-Links angegeben ist. <br/><br/> 2. Der Benutzer schließt das Aufgabenmodul, indem er das X oben rechts des Aufgabenmoduls auswählt oder eine `Action.Submit` Schaltfläche auf der Karte drückt. Da kein Aufruf erforderlich ist `submitHandler` , muss der Benutzer über einen Bot verfügen, um den Wert der Felder für adaptive Karten zu senden. Der Benutzer muss den `completionBotId` Parameter im Deep-Link verwenden, um den Bot anzugeben, an den die Daten mithilfe eines `task/submit invoke` Ereignisses gesendet werden sollen. |

Im nächsten Abschnitt wird das Objekt angegeben, das `TaskInfo` bestimmte Attribute für ein Aufgabenmodul definiert.

## <a name="the-taskinfo-object"></a>Das TaskInfo-Objekt

Das `TaskInfo` Objekt enthält die Metadaten für ein Aufgabenmodul. Definieren Sie den `url` für einen eingebetteten iFrame oder `card` für eine adaptive Karte. Die folgende Tabelle enthält die Objektdefinition:

| Attribut | Typ | Beschreibung |
| --- | --- | --- |
| `title` | string | Dieses Attribut wird unter dem App-Namen und rechts neben dem App-Symbol angezeigt. |
| `height` | Zahl oder Zeichenfolge | Dieses Attribut kann eine Zahl sein, die die Höhe des Aufgabenmoduls in Pixeln oder `small`, `medium`oder `large`darstellt. Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls](#task-module-sizing). |
| `width` | Zahl oder Zeichenfolge | Dieses Attribut kann eine Zahl sein, die die Breite des Aufgabenmoduls in Pixeln oder `small`, `medium`oder `large`darstellt. Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls](#task-module-sizing). |
| `url` | string | Dieses Attribut ist die URL der Seite, die als innerhalb des Aufgabenmoduls `<iframe>` geladen wurde. Die Domäne der URL muss sich im [ValidDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der App im Manifest Ihrer App befinden. |
| `card` | Anlage einer adaptiven Karte oder eines Adaptive Card-Bots | Dieses Attribut ist der JSON-Code für die adaptive Karte, die im Aufgabenmodul angezeigt wird. Wenn der Benutzer von einem Bot aufruft, verwenden Sie den JSON-Code für adaptive Karten in einem Bot Framework-Objekt `attachment` . Auf einer Registerkarte muss der Benutzer eine adaptive Karte verwenden. Weitere Informationen finden Sie unter ["Adaptive Karte" oder "Botkartenanlage für adaptive Karten"](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | string | Dieses Attribut öffnet die URL in einer Browserregisterkarte, wenn ein Client das Aufgabenmodulfeature nicht unterstützt. |
| `completionBotId` | string | Dieses Attribut gibt eine Bot-App-ID an, um das Ergebnis der Benutzerinteraktion mit dem Aufgabenmodul zu senden. Wenn angegeben, empfängt der Bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast. |

> [!NOTE]
> Das Aufgabenmodulfeature erfordert, dass die Domänen aller URLs, die Sie laden möchten, im `validDomains` Array im Manifest Ihrer App enthalten sind.

Im nächsten Abschnitt wird die Größe des Aufgabenmoduls angegeben, mit der der Benutzer die Höhe und Breite des Aufgabenmoduls festlegen kann.

## <a name="task-module-sizing"></a>Größe des Aufgabenmoduls

Die Verwendung ganzzahliger Zahlen für `TaskInfo.width` und `TaskInfo.height`legt die Höhe und Breite des Aufgabenmoduls in Pixel fest. Abhängig von der Größe des Fensters und der Bildschirmauflösung des Teams werden sie jedoch proportional reduziert, während das Seitenverhältnis, das breite oder höhe ist, beibehalten wird.

If `TaskInfo.width` and `TaskInfo.height` are `"small"`, `"medium"`or `"large"`, the size of the red rectangle in the following image is a proportion of the available space, 20%, 50% and 60% for `width` and 20%, 50% and 66% for `height`:

![Beispiel für ein Aufgabenmodul](~/assets/images/task-module/task-module-example.png)

Aufgabenmodule, die von einer Registerkarte aufgerufen werden, können dynamisch geändert werden. Nach dem Aufruf `tasks.startTask()` können Sie aufrufen `tasks.updateTask(newSize)` , wo die Höhen- und Breiteneigenschaften des newSize-Objekts der TaskInfo-Spezifikation entsprechen, z. B `{ height: 'medium', width: 'medium' }`. .

Der nächste Abschnitt enthält Beispiele für das Einbetten von Aufgabenmodulen in ein YouTube-Video und eine PowerApp.

## <a name="task-module-css-for-html-or-javascript-task-modules"></a>Aufgabenmodul-CSS für HTML- oder JavaScript-Aufgabenmodule

HTML- oder JavaScript-basierte Aufgabenmodule haben Zugriff auf den gesamten Bereich des Aufgabenmoduls unterhalb des Headers. Dies bietet zwar ein hohes Maß an Flexibilität, wenn Sie den Abstand an den Rändern an den Kopfzeilenelementen ausrichten möchten und unnötige Bildlaufleisten vermeiden möchten, muss der Benutzer das richtige CSS bereitstellen. Die nächsten Abschnitte enthalten einige Beispiele für einige Anwendungsfälle.

### <a name="example-1-youtube-video"></a>Beispiel 1: YouTube-Video

YouTube bietet die Möglichkeit, Videos auf Webseiten einzubetten. Videos können ganz einfach mithilfe einer einfachen Stub-Webseite in Webseiten in ein Aufgabenmodul eingebettet werden.

![YouTube-Video](~/assets/images/task-module/youtube-example.png)

Der folgende Code enthält ein Beispiel für den HTML-Code für die Webseite ohne CSS:

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

Der folgende Code enthält ein Beispiel für das CSS:

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

### <a name="example-2-powerapp"></a>Beispiel 2: PowerApp

Der Benutzer kann den gleichen Ansatz verwenden, um auch eine PowerApp einzubetten. Da die Höhe oder Breite einer einzelnen PowerApp angepasst werden kann, kann der Benutzer die Höhe und Breite anpassen, um die gewünschte Präsentation zu erzielen.

![Ressourcenverwaltung PowerApp](~/assets/images/task-module/powerapp-example.png)

Der folgende Code enthält ein Beispiel für den HTML-Code für PowerApp:

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

Der folgende Code enthält ein Beispiel für das CSS:

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

Der nächste Abschnitt enthält Details zum Aufrufen Ihrer Karte mithilfe einer adaptiven Karte oder einer Adaptive Card-Bot-Kartenanlage.

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Anlage einer adaptiven Karte oder eines Adaptive Card-Bots

Je nachdem, wie Sie Ihre `card`aufrufen, müssen Sie entweder eine adaptive Karte oder eine Adaptive Card-Bot-Kartenanlage verwenden, bei der es sich um eine adaptive Karte handelt, die in ein Anlagenobjekt eingeschlossen ist.

Wenn Sie von einer Registerkarte aufrufen, muss der Benutzer eine adaptive Karte verwenden.

Der folgende Code enthält ein Beispiel für eine adaptive Karte:

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

Der folgende Code enthält ein Beispiel für eine Adaptive Card-Bot-Kartenanlage, wenn Sie von einem Bot aufrufen:

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

Der nächste Abschnitt enthält Details zur Deep Link-Syntax des Aufgabenmoduls, einschließlich des `TaskInfo` Objekts und `APP_ID` .`BOT_APP_ID`

## <a name="task-module-deep-link-syntax"></a>Deep Link-Syntax des Aufgabenmoduls

Ein Deep-Link des Aufgabenmoduls ist eine Serialisierung des TaskInfo-Objekts mit den folgenden zwei weiteren Details und `APP_ID` optional dem `BOT_APP_ID`:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Die Datentypen und zulässigen Werte für `<TaskInfo.url>`, `<TaskInfo.card>`, `<TaskInfo.height>`und `<TaskInfo.width>``<TaskInfo.title>`, finden Sie unter [TaskInfo -Objekt](#the-taskinfo-object).

> [!TIP]
> Die URL codiert den Deep-Link, wenn der `card` Parameter verwendet wird, z. B. die [JavaScript-Funktion`encodeURI()`](https://www.w3schools.com/jsref/jsref_encodeURI.asp).

Die folgende Tabelle enthält Informationen zu `APP_ID` und `BOT_APP_ID`:

| Wert | Typ | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| `APP_ID` | string | Ja | Die [ID](~/resources/schema/manifest-schema.md#id) der App, die das Aufgabenmodul aufruft. Das [Array "validDomains](~/resources/schema/manifest-schema.md#validdomains) " im Manifest muss `APP_ID` die Domäne `url` für "if `url` " in der URL enthalten. Die App-ID ist bereits bekannt, wenn ein Aufgabenmodul von einer Registerkarte oder einem Bot aufgerufen wird, weshalb sie nicht in `TaskInfo`enthalten ist. |
| `BOT_APP_ID` | string | Nein | Wenn ein Wert für `completionBotId` angegeben wird, wird das `result` Objekt mithilfe einer `task/submit invoke` Nachricht an den angegebenen Bot gesendet. `BOT_APP_ID` muss im Manifest der App als Bot angegeben werden, d. h., Sie können ihn nicht an einen Bot senden. |

> [!NOTE]
> `APP_ID` und `BOT_APP_ID` kann in vielen Fällen identisch sein, wenn eine App über einen empfohlenen Bot verfügt, der als App-ID verwendet werden soll, falls vorhanden.

Der nächste Abschnitt enthält Details zur Verwendung einer Tastatur mit dem Aufgabenmodul Ihrer App.

## <a name="keyboard-and-accessibility-guidelines"></a>Richtlinien für Tastatur und Barrierefreiheit

Bei HTML- oder JavaScript-basierten Aufgabenmodulen müssen Sie sicherstellen, dass das Aufgabenmodul Ihrer App mit einer Tastatur verwendet werden kann. Sprachausgabeprogramme sind auch von der Möglichkeit abhängig, mit der Tastatur zu navigieren. Dazu gehören die folgenden beiden Dinge:

* Verwenden des [Tabindex-Attributs](https://developer.mozilla.org/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können. Verwenden Sie außerdem das tabindex-Attribut, um zu ermitteln, wo es an der sequenziellen Tastaturnavigation beteiligt ist, in der Regel mit den Tasten <kbd>Tab und</kbd> <kbd>UMSCHALTTASTE</kbd> .
* Behandeln des <kbd>Esc-Schlüssels</kbd> im JavaScript für Ihr Aufgabenmodul. Der folgende Code enthält ein Beispiel für die Behandlung des <kbd>Esc-Schlüssels</kbd> :

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

Microsoft Teams stellt sicher, dass die Tastaturnavigation vom Aufgabenmodulheader in Ihren HTML-Code ordnungsgemäß funktioniert und umgekehrt.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodul-Beispielbots-V4 | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|
|Aufgabenmodul-Beispielregisterkarten und Bots-V3 | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](~/concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren von QR- oder Strichcodescannern in Teams](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](~/concepts/device-capabilities/location-capability.md)
