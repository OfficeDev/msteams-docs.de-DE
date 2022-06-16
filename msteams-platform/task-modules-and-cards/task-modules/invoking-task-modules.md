---
title: Aufrufen und Schließen von Aufgabenmodulen
description: Informationen zum Aufrufen und Schließen von Aufgabenmodulen, Aufgabeninformationsobjekt, Aufgabenmodulgröße, Taskmodul-Deep-Link-Syntax unter Verwendung von Codebeispielen
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 04e27e780c1d2686be2ee73909c2d28bfc19fd23
ms.sourcegitcommit: b4986bf529c74444db67b7ce522b3b0d2c2a8e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66130410"
---
# <a name="invoke-and-dismiss-task-modules"></a>Aufrufen und Schließen von Aufgabenmodulen

Aufgabenmodule können über Registerkarten, Bots oder Deep-Links aufgerufen werden. Die Antwort kann entweder in HTML, JavaScript oder als adaptive Karte erfolgen. Es gibt eine Vielzahl von Flexibilitäten in Bezug auf das Aufrufen von Aufgabenmodulen und den Umgang mit der Antwort der Benutzerinteraktion. In der folgenden Tabelle wird zusammengefasst, wie dies funktioniert:

| Wird mithilfe von | Aufgabenmodul mit HTML oder JavaScript | Aufgabenmodul mit adaptiver Karte |
| --- | --- | --- |
| JavaScript auf einer Registerkarte | 1. Verwenden Sie die Teams-Client-SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion. <br/><br/> 2. Wenn der Benutzer die Aktionen im Aufgabenmodulcode ausgeführt hat, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem `result` Objekt als Parameter auf. Wenn ein `submitHandler` Rückruf in `tasks.startTask()`angegeben wurde, ruft Teams ihn mit `result` als Parameter auf. Wenn beim Aufrufen `tasks.startTask()`ein Fehler aufgetreten ist, wird die `submitHandler` Funktion stattdessen mit einer `err` Zeichenfolge aufgerufen. <br/><br/> 3. Sie können beim Aufrufen `teams.startTask()`auch eine `completionBotId` angeben. Dann wird das `result` stattdessen an den Bot gesendet. | 1. Rufen Sie die Teams-Client-SDK-Funktion `tasks.startTask()` mit einem [TaskInfo-Objekt](#the-taskinfo-object) auf, das `TaskInfo.card` den JSON-Code für die adaptive Karte enthält, die im Aufgabenmodul-Popup angezeigt werden soll. <br/><br/> 2. Wenn ein `submitHandler` Rückruf in `tasks.startTask()`angegeben wurde, ruft Teams ihn mit einer `err` Zeichenfolge auf, wenn beim Aufrufen `tasks.startTask()` ein Fehler aufgetreten ist oder wenn der Benutzer das Aufgabenmodul-Popup mithilfe des X oben rechts schließt. <br/><br/> 3. Wenn der Benutzer eine `Action.Submit` Schaltfläche drückt, wird sein `data` Objekt als Wert von `result`zurückgegeben. |
| Bot-Kartenschaltfläche | 1. Bot-Kartenschaltflächen können, je nach Art der Schaltfläche, Aufgabenmodule auf zwei Arten aufrufen: eine Deep-Link-URL oder durch Senden einer `task/fetch` Nachricht. <br/><br/> 2. Wenn die Aktion `type` der Schaltfläche der Schaltflächentyp für adaptive Karten ist `task/fetch` `Action.Submit` , wird ein `task/fetch invoke` Ereignis, bei dem es sich um einen HTTP POST handelt, an den Bot gesendet. Der Bot antwortet auf den POST mit HTTP 200 und den Antworttext, der einen Wrapper um das [TaskInfo-Objekt](#the-taskinfo-object) enthält. Weitere Informationen finden Sie [unter Aufrufen eines Aufgabenmoduls mithilfe von `task/fetch`](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoke-a-task-module-using-taskfetch). Teams zeigt das Aufgabenmodul an. <br/><br/> 3. Nachdem der Benutzer die Aktionen ausgeführt hat, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem `result` Objekt als Parameter auf. Der Bot empfängt eine `task/submit invoke` Nachricht, die das `result` Objekt enthält. <br/><br/> 4. Sie haben drei verschiedene Möglichkeiten, auf die `task/submit` Nachricht zu reagieren, indem Sie nichts tun, was die Aufgabe erfolgreich abgeschlossen hat, indem Sie dem Benutzer eine Nachricht in einem Popupfenster anzeigen oder ein anderes Aufgabenmodulfenster aufrufen. Weitere Informationen finden Sie [in der ausführlichen Diskussion auf `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). | <ul><li> Wie Schaltflächen auf Bot Framework-Karten unterstützen Schaltflächen auf adaptiven Karten zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen, Deep-Link-URLs mit `Action.openUrl` Schaltflächen und `task/fetch` die Verwendung von `Action.Submit` Schaltflächen. </li></ul> <br/><br/> <ul><li> Aufgabenmodule mit adaptiven Karten funktionieren ähnlich wie der HTML- oder JavaScript-Fall. Der Hauptunterschied besteht darin, dass es keine Möglichkeit zum Aufrufen gibt, da es kein JavaScript gibt, wenn Sie adaptive Karten verwenden `tasks.submitTask()`. Stattdessen verwendet Teams das `data` Objekt `Action.Submit` und gibt es als Nutzlast des `task/submit` Ereignisses zurück. Weitere Informationen finden Sie [unter Flexibilität von `task/submit`](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit). </li></ul> |
| Deep-Link-URL <br/>[URL-Syntax](#task-module-deep-link-syntax) | 1. Teams ruft das Aufgabenmodul auf, bei dem es sich um die URL handelt, die innerhalb der `<iframe>` im `url` Parameter des Deep-Links angegebenen Url angezeigt wird. Es gibt keinen `submitHandler` Rückruf. <br/><br/> 2. Rufen Sie `tasks.submitTask()` im JavaScript der Seite im Aufgabenmodul auf, es mit einem `result` Objekt als Parameter zu schließen, wie beim Aufrufen von einer Registerkarte oder einer Bot-Kartenschaltfläche. Die Vervollständigungslogik unterscheidet sich jedoch geringfügig. Wenn sich Ihre Abschlusslogik auf dem Client befindet, d. h. wenn kein Bot vorhanden ist, gibt es keinen `submitHandler` Rückruf. Daher muss sich eine Abschlusslogik im Code befinden, der dem Aufruf `tasks.submitTask()`von vorausgeht. Aufruffehler werden nur über die Konsole gemeldet. Wenn Sie über einen Bot verfügen, können Sie einen `completionBotId` Parameter im Deep-Link angeben, um das `result` Objekt über ein `task/submit` Ereignis zu senden. | 1. Teams ruft das Aufgabenmodul auf, bei dem es sich um den JSON-Kartentext der adaptiven Karte handelt, der als URL-codierter Wert des `card` Parameters der Deep-Verknüpfung angegeben ist. <br/><br/> 2. Der Benutzer schließt das Aufgabenmodul, indem er das X oben rechts im Aufgabenmodul auswählt oder eine Schaltfläche auf der Karte drückt `Action.Submit` . Da es keinen `submitHandler` Aufruf gibt, muss der Benutzer über einen Bot verfügen, um den Wert der Felder für adaptive Karten zu senden. Der Benutzer muss den `completionBotId` Parameter im Deep-Link verwenden, um den Bot anzugeben, an den die Daten mithilfe eines `task/submit invoke` Ereignisses gesendet werden sollen. |

Im nächsten Abschnitt wird das `TaskInfo` Objekt angegeben, das bestimmte Attribute für ein Aufgabenmodul definiert.

## <a name="the-taskinfo-object"></a>Das TaskInfo-Objekt

Das `TaskInfo` Objekt enthält die Metadaten für ein Aufgabenmodul. Definieren Sie den `url` für einen eingebetteten iFrame oder `card` für eine adaptive Karte. Die folgende Tabelle enthält die Objektdefinition:

| Attribut | Typ | Beschreibung |
| --- | --- | --- |
| `title` | string | Dieses Attribut wird unterhalb des App-Namens und rechts neben dem App-Symbol angezeigt. |
| `height` | Zahl oder Zeichenfolge | Dieses Attribut kann eine Zahl sein, die die Höhe des Aufgabenmoduls in Pixeln darstellt, oder `small`, `medium`oder `large`. Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls](#task-module-sizing). |
| `width` | Zahl oder Zeichenfolge | Dieses Attribut kann eine Zahl sein, die die Breite des Aufgabenmoduls in Pixeln darstellt, oder `small`, `medium`oder `large`. Weitere Informationen finden Sie unter [Größe des Aufgabenmoduls](#task-module-sizing). |
| `url` | string | Dieses Attribut ist die URL der Seite, die als eine innerhalb des Aufgabenmoduls `<iframe>` geladen wird. Die Domäne der URL muss sich im [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der App im Manifest Ihrer App befinden. |
| `card` | Anlage für adaptive Karten oder Bot-Karten adaptiver Karten | Dieses Attribut ist der JSON-Code für die adaptive Karte, die im Aufgabenmodul angezeigt wird. Wenn der Benutzer einen Bot aufruft, verwenden Sie den JSON-Code für adaptive Karten in einem Bot Framework-Objekt `attachment` . Auf einer Registerkarte muss der Benutzer eine adaptive Karte verwenden. Weitere Informationen finden Sie unter ["Adaptive Karte" oder "Botkartenanlage für adaptive Karten"](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | string | Dieses Attribut öffnet die URL auf einer Browserregisterkarte, wenn ein Client das Aufgabenmodulfeature nicht unterstützt. |
| `completionBotId` | string | Dieses Attribut gibt eine Bot-App-ID an, um das Ergebnis der Benutzerinteraktion mit dem Aufgabenmodul zu senden. Wenn angegeben, empfängt der Bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast. |

> [!NOTE]
> Das Aufgabenmodulfeature erfordert, dass die Domänen aller URLs, die Sie laden möchten, im `validDomains` Array im Manifest Ihrer App enthalten sind.

Im nächsten Abschnitt wird die Größe des Aufgabenmoduls angegeben, mit der der Benutzer die Höhe und Breite des Aufgabenmoduls festlegen kann.

## <a name="task-module-sizing"></a>Größe des Aufgabenmoduls

Mithilfe von ganzzahligen Zahlen für `TaskInfo.width` und `TaskInfo.height`wird die Höhe und Breite des Aufgabenmoduls in Pixeln festgelegt. Je nach Größe des Teamfensters und der Bildschirmauflösung werden sie jedoch proportional reduziert, während das Seitenverhältnis, das breite oder höhe ist, beibehalten wird.

Wenn `TaskInfo.width` und `TaskInfo.height` sind `"small"`, `"medium"`oder `"large"`ist die Größe des roten Rechtecks in der folgenden Abbildung ein Anteil des verfügbaren Platzes, 20%, 50% und 60% für `width` und 20%, 50% und 66% für `height`:

:::image type="content" source="../../assets/images/task-module/task-module-example.png" alt-text="Beispiel für ein Aufgabenmodul":::

Aufgabenmodule, die über eine Registerkarte aufgerufen werden, können dynamisch in der Größe geändert werden. Nach dem Aufruf `tasks.startTask()` können Sie aufrufen `tasks.updateTask(newSize)` , wo die Höhen- und Breiteneigenschaften für das newSize -Objekt der TaskInfo-Spezifikation entsprechen, z. B `{ height: 'medium', width: 'medium' }`. .

Der nächste Abschnitt enthält Beispiele für das Einbetten von Aufgabenmodulen in ein YouTube-Video und eine PowerApp.

## <a name="task-module-css-for-html-or-javascript-task-modules"></a>Aufgabenmodul-CSS für HTML- oder JavaScript-Aufgabenmodule

HTML- oder JavaScript-basierte Aufgabenmodule haben Zugriff auf den gesamten Bereich des Aufgabenmoduls unterhalb der Kopfzeile. Dies bietet zwar eine große Flexibilität. Wenn Sie möchten, dass der Abstand an den Rändern an den Kopfzeilenelementen ausgerichtet wird und unnötige Bildlaufleisten vermieden werden, muss der Benutzer das richtige CSS bereitstellen. In den nächsten Abschnitten finden Sie einige Beispiele für einige Anwendungsfälle.

### <a name="example-1-youtube-video"></a>Beispiel 1: YouTube-Video

YouTube bietet die Möglichkeit, Videos auf Webseiten einzubetten. Das Einbetten von Videos auf Webseiten in ein Aufgabenmodul ist mithilfe einer einfachen Stub-Webseite ganz einfach.

:::image type="content" source="../../assets/images/task-module/youtube-example.png" alt-text="Youtube-Beispiel":::

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

Der folgende Code enthält ein Beispiel für css:

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

Der Benutzer kann den gleichen Ansatz auch zum Einbetten einer PowerApp verwenden. Da die Höhe oder Breite einer einzelnen PowerApp angepasst werden kann, kann der Benutzer die Höhe und Breite anpassen, um die gewünschte Präsentation zu erzielen.

:::image type="content" source="../../assets/images/task-module/powerapp-example.png" alt-text="powerapp":::

Der folgende Code enthält ein Beispiel für den HTML-Code für PowerApp:

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

Der folgende Code enthält ein Beispiel für css:

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

Der nächste Abschnitt enthält Details zum Aufrufen Ihrer Karte mithilfe der Anlage für adaptive Karten oder Botkarten adaptiver Karten.

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Anlage für adaptive Karten oder Bot-Karten adaptiver Karten

Je nachdem, wie Sie Die `card`App aufrufen, müssen Sie entweder eine adaptive Karte oder eine Botkartenanlage für adaptive Karten verwenden, bei der es sich um eine adaptive Karte handelt, die in ein Anlageobjekt eingeschlossen ist.

Wenn Sie eine Registerkarte aufrufen, muss der Benutzer eine adaptive Karte verwenden.

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

Der folgende Code enthält ein Beispiel für eine Botkartenanlage für adaptive Karten, wenn Sie einen Bot aufrufen:

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

Der nächste Abschnitt enthält Details zur Deep Link-Syntax des Aufgabenmoduls, einschließlich des Objekts `TaskInfo` und und `APP_ID` `BOT_APP_ID`.

## <a name="task-module-deep-link-syntax"></a>Deep Link-Syntax des Aufgabenmoduls

Ein Aufgabenmodul-Deep-Link ist eine Serialisierung des TaskInfo-Objekts mit den folgenden zwei weiteren Details und `APP_ID` optional der `BOT_APP_ID`:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Die Datentypen und zulässigen Werte für `<TaskInfo.url>`, `<TaskInfo.card>`, `<TaskInfo.height>`, `<TaskInfo.width>`und `<TaskInfo.title>`, siehe [TaskInfo -Objekt](#the-taskinfo-object).

> [!TIP]
> Die URL codiert den Deep-Link, wenn der `card` Parameter verwendet wird, z. B. die [JavaScript-Funktion`encodeURI()`](https://www.w3schools.com/jsref/jsref_encodeURI.asp).

Die folgende Tabelle enthält Informationen zu `APP_ID` und `BOT_APP_ID`:

| Wert | Typ | Erforderlich | Beschreibung |
| --- | --- | --- | --- |
| `APP_ID` | string | Ja | Die [ID](~/resources/schema/manifest-schema.md#id) der App, die das Aufgabenmodul aufruft. Das [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) im Manifest `APP_ID` muss die Domäne `url` enthalten, wenn `url` sich diese in der URL befindet. Die App-ID ist bereits bekannt, wenn ein Aufgabenmodul von einer Registerkarte oder einem Bot aufgerufen wird, weshalb es nicht in `TaskInfo`enthalten ist. |
| `BOT_APP_ID` | string | Nein | Wenn ein Wert für `completionBotId` angegeben wird, wird das `result` Objekt mithilfe einer `task/submit invoke` Nachricht an den angegebenen Bot gesendet. `BOT_APP_ID` muss im Manifest der App als Bot angegeben werden, d. h., Sie können ihn nicht an einen Bot senden. |

> [!NOTE]
> `APP_ID` und `BOT_APP_ID` kann in vielen Fällen identisch sein, wenn eine App über einen empfohlenen Bot verfügt, der als App-ID verwendet werden soll, falls vorhanden.

Der nächste Abschnitt enthält Details zur Verwendung einer Tastatur mit dem Aufgabenmodul Ihrer App.

## <a name="keyboard-and-accessibility-guidelines"></a>Richtlinien für Tastatur und Barrierefreiheit

Bei HTML- oder JavaScript-basierten Aufgabenmodulen müssen Sie sicherstellen, dass das Aufgabenmodul Ihrer App mit einer Tastatur verwendet werden kann. Sprachausgabeprogramme sind auch von der Möglichkeit abhängig, mithilfe der Tastatur zu navigieren. Dazu gehören die folgenden beiden Punkte:

* Verwenden des [Tabindex-Attributs](https://developer.mozilla.org/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können. Verwenden Sie auch das Tabindex-Attribut, um zu identifizieren, wo es an der sequenziellen Tastaturnavigation beteiligt ist, normalerweise mit der <kbd>TAB</kbd><kbd>- und UMSCHALT-TAB-TASTE</kbd>.
* Behandeln des <kbd>ESC-Schlüssels</kbd> im JavaScript für Ihr Aufgabenmodul. Der folgende Code enthält ein Beispiel für die Behandlung des <kbd>ESC-Schlüssels</kbd> :

    ```javascript
    // Handle the Esc key
    document.onkeyup = function(event) {
    if ((event.key === 27) || (event.key === "Escape")) {
      microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
      }
    }
    ```

Microsoft Teams stellt sicher, dass die Tastaturnavigation vom Aufgabenmodulkopf in Ihren HTML-Code ordnungsgemäß funktioniert und umgekehrt.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodul-Beispiel-Bots-V4 | Beispiele für das Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|
|Beispielregisterkarten und Bots des Aufgabenmoduls – V3 | Beispiele für das Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](~/concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](~/concepts/device-capabilities/media-capabilities.md)
* [Integrieren von QR-Code- oder Strichcodescanner-Funktionen in Microsoft Teams](~/concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Microsoft Teams](~/concepts/device-capabilities/location-capability.md)
