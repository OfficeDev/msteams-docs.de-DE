---
title: Was sind Aufgabenmodule?
author: clearab
description: Hinzufügen von modalen Popup-Erlebnissen zum Sammeln oder Anzeigen von Informationen für Benutzer aus Ihren Microsoft Teams-Apps
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 23157e30ce25c2dfa1c21e7f5c4ddd4f735b660f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566841"
---
# <a name="task-modules"></a>Aufgabenmodule

Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, ein `<iframe>` -basiertes Widget wie ein YouTube- oder Microsoft Stream-Video anzeigen oder eine [adaptive Karte](/adaptive-cards/)anzeigen. Sie eignen sich besonders für das Initiieren und Fertigstellen von Aufgaben oder das Anzeigen von Multimedia-Informationen wie Videos oder Power BI-Dashboards. Eine Popup-Oberfläche wirkt für Benutzer, die Aufgaben initiieren und fertigstellen, im Vergleich zu einer Registerkarte oder einer auf einer Unterhaltung basierenden Bot-Umgebung, häufig natürlicher.

Taskmodule bauen auf der Grundlage von Microsoft Teams Registerkarten auf. Sie sind im Wesentlichen eine Registerkarte in einem Popup-Fenster. Sie verwenden dasselbe SDK, wenn Sie also eine Registerkarte erstellt haben, sind Sie bereits 90 % der Möglichkeit, ein Aufgabenmodul erstellen zu können.

Aufgabenmodule können auf drei Arten aufgerufen werden:

* **Kanal- oder persönliche Registerkarten**: Mit dem Microsoft Teams Tabs SDK können Sie Task-Module über Schaltflächen, Links oder Menüs auf Ihrer Registerkarte [aufrufen.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots**: Buttons auf [Karten](~/task-modules-and-cards/cards/cards-reference.md) von Ihrem Bot gesendet. Dies ist besonders nützlich, wenn Sie nicht jeden in einem Kanal benötigen, um zu sehen, was Sie mit einem Bot tun. Wenn Benutzer beispielsweise auf eine Umfrage in einem Kanal antworten, ist es nicht unbedingt nötig, einen Datensatz der erstellten Umfrage anzuzeigen. [Dies wird hier ausführlich behandelt.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Außerhalb Teams über einen Deep Link:** Sie können auch URLs erstellen, um ein Aufgabenmodul von überall aus aufzurufen. [Dies wird hier ausführlich behandelt.](#task-module-deep-link-syntax)

## <a name="task-module-looks-like"></a>Aufgabenmodul sieht aus wie

So sieht ein Aufgabenmodul aus, wenn es von einem Bot aufgerufen wird (natürlich ohne die farbigen Rechtecke und nummerierten Kreise):

![Beispiel für das Aufgabenmodul](~/assets/images/task-module/task-module-example.png)

Lassen Sie uns durch sie gehen:

1. Das [ `color` Symbol](~/resources/schema/manifest-schema.md#icons)Ihrer App .
1. [ `short` Der Name](~/resources/schema/manifest-schema.md#name)Ihrer App .
1. Der Titel des Aufgabenmoduls, der in der `title` Eigenschaft des [TaskInfo-Objekts](#the-taskinfo-object)angegeben ist.
1. Die Nah-/Abbruch-Schaltfläche des Taskmoduls. Wenn der Benutzer dies drückt, erhält Ihre App ein `err` Ereignis, wie [hier](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)beschrieben.
    > [!Note]
    > Es ist derzeit nicht möglich, dieses Ereignis zu erkennen, wenn ein Taskmodul von einem Bot aufgerufen wird.
1. Das blaue Rechteck ist die Stelle, an der Ihre Webseite angezeigt wird, wenn Sie Eine eigene Webseite mit der `url` Eigenschaft des [TaskInfo-Objekts](#the-taskinfo-object)laden. Weitere Details finden Sie im Abschnitt Größenänderung des [Aufgabenmoduls](#task-module-sizing) unten.
1. Wenn Sie eine adaptive Karte über die `card` Eigenschaft des [TaskInfo-Objekts](#the-taskinfo-object) anzeigen, wird das Auffüllen für Sie hinzugefügt, andernfalls müssen Sie [dies selbst behandeln.](#task-module-css-for-htmljavascript-task-modules)
1. Adaptive Kartentasten werden hier gerendert. Wenn Sie Ihre eigene Seite verwenden, müssen Sie eigene Schaltflächen erstellen.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Überblick über das Aufrufen und Ablassen von Aufgabenmodulen

Aufgabenmodule können von Registerkarten, Bots oder Deep Links aufgerufen werden, und was in einem angezeigt wird, kann entweder HTML oder eine adaptive Karte sein, sodass es eine Menge Flexibilität in Bezug auf ihre Behebung und den Umgang mit dem Ergebnis der Interaktion eines Benutzers gibt. Die folgende Tabelle fasst zusammen, wie dies funktioniert:

| **Aufgerufen über...** | **Aufgabenmodul ist HTML/JavaScript** | **Aufgabenmodul ist Adaptive Karte** |
| --- | --- | --- |
| **JavaScript in einer Registerkarte** | 1. Verwenden Sie die Teams Client-SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion. <br/><br/> 2. Rufen Sie im Taskmodulcode, wenn der Benutzer fertig ist, die Teams SDK-Funktion `tasks.submitTask()` mit einem Objekt als Parameter `result` auf. Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn als Parameter `result` auf.<br/><br/> 3. Wenn beim Aufrufen ein Fehler aufgetreten `tasks.startTask()` ist, wird die `submitHandler` Funktion stattdessen mit einer Zeichenfolge `err` aufgerufen. <br/><br/> 4. Sie können auch eine `completionBotId` angeben, wenn Sie anrufen `teams.startTask()` - in diesem Fall wird stattdessen an den Bot `result` gesendet. | 1. Rufen Sie die Teams Client-SDK-Funktion `tasks.startTask()` mit einem [TaskInfo-Objekt](#the-taskinfo-object) auf und `TaskInfo.card` enthalten sie das JSON für die adaptive Karte, das im Taskmodul-Popup angezeigt werden soll. <br/><br/> 2. Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn mit einer `err` Zeichenfolge auf, wenn beim Aufrufen ein Fehler aufgetreten `tasks.startTask()` ist oder wenn der Benutzer das Taskmodul-Popup mit dem X oben rechts schließt. <br/><br/> 3. Wenn der Benutzer eine Action.Submit-Taste drückt, wird sein `data` Objekt als Wert von `result` zurückgegeben. |
| **Bot-Karte-Taste** | 1. Bot-Karten-Tasten, je nach Art der Schaltfläche, können Task-Module auf zwei Arten aufrufen: eine Deep-Link-URL oder durch Senden einer `task/fetch` Nachricht. Im Folgenden finden Sie die Funktionsweise von Deep Link-URLs. <br/><br/> 2. Wenn die Aktion der Schaltfläche `type` `task/fetch` `Action.Submit` (Schaltflächentyp für Adaptive-Karten) lautet, wird ein `task/fetch invoke` Ereignis (ein HTTP-POST unter den Abdeckungen) an den Bot gesendet, und der Bot antwortet auf den POST-Test mit HTTP 200 und dem Antworttext, der einen Wrapper um das [TaskInfo-Objekt](#the-taskinfo-object)enthält. Dies wird ausführlich beim [Aufrufen eines Taskmoduls über task/fetch](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-through-taskfetch)erläutert.<br/><br/> 3. Teams zeigt das Taskmodul an; Wenn der Benutzer fertig ist, rufen Sie die Teams `tasks.submitTask()` SDK-Funktion mit einem `result` Objekt als Parameter auf. <br/><br/> 4. Der Bot erhält eine `task/submit invoke` Nachricht, die das `result` Objekt enthält. Sie haben drei verschiedene Möglichkeiten, auf die Nachricht zu reagieren: indem Sie `task/submit` nichts tun (die Aufgabe erfolgreich abgeschlossen wurde), indem Sie dem Benutzer in einem Popupfenster eine Nachricht anzeigen oder ein anderes Aufgabenmodulfenster aufrufen (d. h. eine Assistenten-ähnliche Erfahrung erstellen). Diese drei Optionen werden [in der ausführlichen Diskussion über Aufgabe/Einreichung](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit)näher erläutert. | 1. Wie Schaltflächen auf Bot Framework-Karten unterstützen Schaltflächen auf Adaptive-Karten zwei Möglichkeiten, Aufgabenmodule aufzuberufen: Deep Link-URLs mit `Action.openUrl` Schaltflächen und über `task/fetch` die Verwendung von `Action.Submit` Schaltflächen. <br/><br/> 2. Task-Module mit adaptiven Karten funktionieren sehr ähnlich wie der Fall HTML/JavaScript (siehe links). Der Hauptunterschied besteht darin, dass es keine Möglichkeit gibt, aufzurufen, da es kein JavaScript gibt, wenn Sie Adaptive-Karten `tasks.submitTask()` verwenden. Stattdessen nimmt Teams das `data` Objekt aus und gibt es als `Action.Submit` Nutzlast von im `task/submit` Ereignis zurück, wie [hier](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit)beschrieben. |
| **Deep link URL** <br/>[URL-Syntax](#task-module-deep-link-syntax) | 1. Teams ruft das Taskmodul auf; die URL, die innerhalb der `<iframe>` im Parameter des Tiefenverknüpfungs angegebenen URL angezeigt `url` wird. Es gibt keinen `submitHandler` Rückruf. <br/><br/> 2. Rufen Sie innerhalb des JavaScript der Seite im Taskmodul an, `tasks.submitTask()` um es mit einem Objekt als Parameter zu `result` schließen, wie beim Aufrufen von einer Registerkarte oder einer Bot-Kartenschaltfläche. Die Abschlusslogik ist jedoch etwas anders. Wenn sich Ihre Abschlusslogik auf dem Client befindet (d. h. wenn kein Bot vorhanden ist), gibt es keinen `submitHandler` Rückruf, daher muss sich jede Abschlusslogik im Code befinden, der dem Aufruf von vorangeht. `tasks.submitTask()` Aufruffehler werden nur über die Konsole gemeldet. Wenn Sie einen Bot haben, können Sie einen `completionBotId` Parameter in der Deep-Link angeben, um das Objekt über ein Ereignis zu `result` `task/submit` senden. | 1. Teams ruft das Taskmodul auf; Der JSON-Kartenkörper der Adaptive-Karte wird als URL-codierter Wert des `card` Parameters des Deep-Links angegeben. <br/><br/> 2. Der Benutzer schließt das Taskmodul, indem er auf das X oben rechts im Taskmodul klickt oder eine `Action.Submit` Taste auf der Karte drückt. Da es keinen `submitHandler` Aufruf gibt, müssen Sie über einen Bot verfügen, an den der Wert der Adaptivecardfelder gesendet werden kann. Sie verwenden den `completionBotId` Parameter im Deep Link, um den Bot anzugeben, an den die Daten über ein Ereignis gesendet werden `task/submit invoke` sollen. |

## <a name="the-taskinfo-object"></a>Das TaskInfo-Objekt

Das `TaskInfo` Objekt enthält die Metadaten für ein Aufgabenmodul. Die Objektdefinition ist unten. Sie **müssen** entweder `url` für ein eingebettetes iFrame oder für eine adaptive Karte `card` definieren.

| Attribut | Typ | Beschreibung |
| --- | --- | --- |
| `title` | string | Wird unter dem App-Namen und rechts neben dem App-Symbol angezeigt. |
| `height` | Zahl oder Zeichenfolge | Dies kann eine Zahl sein, die die Höhe des Taskmoduls in Pixel oder `small` , `medium` oder `large` darstellt. [Siehe unten, wie Höhe und Breite behandelt werden.](#task-module-sizing) |
| `width` | Zahl oder Zeichenfolge | Dies kann eine Zahl sein, die die Breite des Taskmoduls in Pixel oder `small` , `medium` oder `large` darstellt. [Siehe unten, wie Höhe und Breite behandelt werden.](#task-module-sizing) |
| `url` | Zeichenfolge | Die URL der Seite, die als `<iframe>` innerhalb des Taskmoduls geladen wurde. Die Domäne der URL muss sich im [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der App im Manifest Ihrer App befinden. |
| `card` | Adaptive Karte oder ein adaptiver Kartenbotkartenaufsatz | Der JSON für die adaptive Karte, die im Taskmodul angezeigt wird. Wenn Sie von einem Bot aufrufen, müssen Sie die Adaptive-Karte JSON in einem Bot `attachment` Framework-Objekt verwenden. Von einer Registerkarte aus verwenden Sie nur eine Adaptive Card. [Hier ist ein Beispiel.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | Zeichenfolge | Wenn ein Client die Funktion des Aufgabenmoduls nicht unterstützt, wird diese URL in einer Browser-Registerkarte geöffnet. |
| `completionBotId` | Zeichenfolge | Gibt eine Bot-App-ID an, an die das Ergebnis der Interaktion des Benutzers mit dem Taskmodul gesendet werden soll. Wenn angegeben, empfängt der Bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast. |

> [!NOTE]
> Die Funktion des Aufgabenmoduls erfordert, dass die Domänen aller URLs, die Sie laden möchten, im Array im Manifest Ihrer App enthalten `validDomains` sind.

## <a name="task-module-sizing"></a>Größe des Aufgabenmoduls

Verwenden von ganzzahlen für `TaskInfo.width` und legen Sie die Höhe und Breite in `TaskInfo.height` Pixelfest fest. Abhängig von der Größe des Fensters des Teams und der Bildschirmauflösung werden sie jedoch proportional reduziert, während das Seitenverhältnis (Breite/Höhe) beibehalten wird.

Wenn `TaskInfo.width` und sind , oder die Größe des roten `TaskInfo.height` `"small"` `"medium"` `"large"` Rechtecks im Bild oben ist ein Anteil des verfügbaren Speicherplatzes: 20%, 50%, 60% für `width` und 20%, 50%, 66% für `height` .

Taskmodule, die von einer Registerkarte aufgerufen werden, können dynamisch in der Größe geändert werden. Nach dem Aufruf `tasks.startTask()` können Sie `tasks.updateTask(newSize)` aufrufen, wo Höhen- und Breiteneigenschaften für das newSize-Objekt der TaskInfo-Spezifikation entsprechen (z. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>Taskmodul CSS für HTML/JavaScript-Aufgabenmodule

HTML/JavaScript-basierte Task-Module haben Zugriff auf den gesamten Bereich des Task-Moduls unterhalb des Headers. Während dies eine große Flexibilität bietet, wenn Sie möchten, dass das Auffüllen um die Kanten an den Headerelementen ausgerichtet wird und unnötige Bildlaufleisten vermieden werden, müssen Sie das richtige CSS bereitstellen. Hier sind einige Beispiele für einige Anwendungsfälle.

### <a name="example-1---youtube-video"></a>Beispiel 1 - YouTube-Video

YouTube bietet die Möglichkeit, Videos auf Webseiten einzubetten. Mit einer einfachen Stub-Webseite ist es einfach, dies in einem Aufgabenmodul anzuzeigen:

![YouTube-Video](~/assets/images/task-module/youtube-example.png)

Hier ist der HTML-Code für diese Seite, ohne das CSS:

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

Das CSS sieht wie folgt aus:

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

### <a name="example-2---powerapp"></a>Beispiel 2 - PowerApp

Sie können den gleichen Ansatz verwenden, um eine PowerApp einzubetten. Da die Höhe/Breite jeder einzelnen PowerApp anpassbar ist, müssen Sie möglicherweise die Höhe und Breite anpassen, um Ihre gewünschte Präsentation zu erreichen.

![Asset Management PowerApp](~/assets/images/task-module/powerapp-example.png)

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

Und die CSS ist:

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Adaptive Karte oder Adaptive Karten-Bot-Karten-Anhang

Wie bereits erwähnt, müssen Sie, je nachdem, wie Sie Ihre Karte `card` aufrufen, entweder eine adaptive Karte oder einen Adaptive Card Bot Card-Anhang verwenden (das ist nur eine adaptive Karte, die in ein Befestigungsobjekt eingewickelt ist).

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

Wenn Sie von einem Bot aufrufen, müssen Sie einen adaptiven Karten-Bot-Kartenanhang verwenden, wie im folgenden Beispiel:

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

Sie müssen sich daran erinnern, ob Sie ein Aufgabenmodul aufrufen, das eine adaptive Karte von einem Bot oder einer Registerkarte enthält.

## <a name="task-module-deep-link-syntax"></a>Taskmodul Deep Link Syntax

Eine Deep-Link-Verbindung des Taskmoduls ist nur eine Serialisierung des [TaskInfo-Objekts](#the-taskinfo-object) mit zwei weiteren Informationen, `APP_ID` und optional `BOT_APP_ID` die:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Siehe [TaskInfo-Objekt](#the-taskinfo-object) für die Datentypen und zulässigen Werte für `<TaskInfo.url>` , , , und `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` .

> [!TIP]
> Achten Sie darauf, die DEEP-Link zu codieren, insbesondere bei Verwendung des Parameters (z. B. `card` JavaScript-Funktion ). [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)

Hier sind die Informationen zu `APP_ID` `BOT_APP_ID` und:

| Wert | Typ | Pflichtfeld? | Beschreibung |
| --- | --- | --- | --- |
| `APP_ID` | string | Ja | Die [ID](~/resources/schema/manifest-schema.md#id) der App, die das Aufgabenmodul aufruft. Das [validDomains-Array](~/resources/schema/manifest-schema.md#validdomains) im Manifest für `APP_ID` muss die Domäne für if in der URL `url` `url` enthalten. (Die App-ID ist bereits bekannt, wenn ein Taskmodul von einer Registerkarte oder einem Bot aufgerufen wird, weshalb es nicht in `TaskInfo` enthalten ist.) |
| `BOT_APP_ID` | Zeichenfolge | Nein | Wenn ein Wert für `completionBotId` angegeben ist, wird das `result` Objekt über eine Nachricht an den angegebenen Bot `task/submit invoke` gesendet. `BOT_APP_ID` muss als Bot im App-Manifest angegeben werden, d.h. Sie können ihn nicht einfach an einen Bot senden. |

Beachten Sie, dass es für und für das gleiche gültig `APP_ID` `BOT_APP_ID` ist, und in vielen Fällen wird sein, wenn eine App einen Bot hat, da es empfohlen wird, dies als ID einer App zu verwenden, wenn es eine gibt.

## <a name="keyboard-and-accessibility-guidelines"></a>Richtlinien für Tastatur und Barrierefreiheit

Bei HTML/JavaScript-basierten Aufgabenmodulen liegt es in Ihrer Verantwortung sicherzustellen, dass das Aufgabenmodul Ihrer App mit einer Tastatur verwendet werden kann. Screenreader-Programme hängen auch von der Fähigkeit ab, über die Tastatur zu navigieren. In der Praxis bedeutet dies zwei Dinge:

1. Verwenden des [tabindex-Attributs](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können und ob/wo es an der sequenziellen Tastaturnavigation beteiligt ist (in der Regel mit den <kbd>Tasten Tab</kbd> und <kbd>Shift-Tab).</kbd>
2. Behandeln des <kbd>Esc-Schlüssels</kbd> im JavaScript für Ihr Aufgabenmodul. Hier ist ein Codebeispiel, das zeigt, wie Sie dies tun:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

Microsoft Teams stellt sicher, dass die Tastaturnavigation vom Header des Taskmoduls in Ihren HTML-Code und umgekehrt ordnungsgemäß funktioniert.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Taskmodulbeispiel (Bots-V4) | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 
|Taskmodulbeispiel (Tabs + Bots-V3) | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](../concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren Sie QR- oder Barcode-Scanner-Funktionen in Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](../concepts/device-capabilities/location-capability.md)
