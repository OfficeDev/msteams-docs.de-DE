---
title: Was sind Aufgabenmodule?
author: surbhigupta
description: Hinzufügen modaler Popup-Oberflächen zum Sammeln oder Anzeigen von Informationen für Ihre Benutzer aus Ihren Microsoft Teams-Apps
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e4937fc4909535506c61b4ac353283322d5f3631
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068607"
---
# <a name="task-modules"></a>Aufgabenmodule

Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML-/JavaScript-Code ausführen, ein `<iframe>` -basiertes Widget wie ein YouTube- oder Microsoft Stream-Video anzeigen oder eine [adaptive Karte](/adaptive-cards/)anzeigen. Sie eignen sich besonders für das Initiieren und Fertigstellen von Aufgaben oder das Anzeigen von Multimedia-Informationen wie Videos oder Power BI-Dashboards. Eine Popup-Oberfläche wirkt für Benutzer, die Aufgaben initiieren und fertigstellen, im Vergleich zu einer Registerkarte oder einer auf einer Unterhaltung basierenden Bot-Umgebung, häufig natürlicher.

Aufgabenmodule basieren auf der Grundlage Microsoft Teams Registerkarten; Sie sind im Wesentlichen eine Registerkarte in einem Popupfenster. Sie verwenden das gleiche SDK, wenn Sie also eine Registerkarte erstellt haben, sind Sie bereits zu 90 % der Möglichkeit, ein Aufgabenmodul zu erstellen.

Aufgabenmodule können auf drei Arten aufgerufen werden:

* **Kanal- oder persönliche Registerkarten:** Mit dem Microsoft Teams Tabs SDK können Sie Aufgabenmodule über Schaltflächen, Links oder Menüs auf Ihrer Registerkarte aufrufen. [Dies wird hier ausführlich behandelt.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
* **Bots:** Schaltflächen auf [Karten,](~/task-modules-and-cards/cards/cards-reference.md) die von Ihrem Bot gesendet werden. Dies ist besonders nützlich, wenn Sie nicht jeden in einem Kanal benötigen, um zu sehen, was Sie mit einem Bot tun. Wenn Benutzer beispielsweise auf eine Umfrage in einem Kanal antworten, ist es nicht unbedingt nötig, einen Datensatz der erstellten Umfrage anzuzeigen. [Dies wird hier ausführlich behandelt.](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* **Außerhalb von Teams von einem Deep-Link:** Sie können auch URLs erstellen, um ein Aufgabenmodul von überall aus aufzurufen. [Dies wird hier ausführlich behandelt.](#task-module-deep-link-syntax)

## <a name="task-module-looks-like"></a>Aufgabenmodul sieht aus wie

So sieht ein Aufgabenmodul aus, wenn es von einem Bot aufgerufen wird (natürlich ohne farbige Rechtecke und nummerierte Kreise):

![Beispiel für das Aufgabenmodul](~/assets/images/task-module/task-module-example.png)

Lassen Sie uns durchgehen:

1. [ `color` Das Symbol](~/resources/schema/manifest-schema.md#icons)Ihrer App.
1. Der [ `short` Name](~/resources/schema/manifest-schema.md#name)Ihrer App.
1. Der Titel des Aufgabenmoduls, der in der `title` Eigenschaft des [TaskInfo -Objekts](#the-taskinfo-object)angegeben ist.
1. Die Schaltfläche zum Schließen/Abbrechen des Aufgabenmoduls. Wenn der Benutzer dies drückt, empfängt Ihre App ein `err` Ereignis, wie [hier](~/task-modules-and-cards/task-modules/task-modules-tabs.md#example-submitting-the-result-of-a-task-module)beschrieben.
    > [!Note]
    > Es ist derzeit nicht möglich, dieses Ereignis zu erkennen, wenn ein Aufgabenmodul von einem Bot aufgerufen wird.
1. Das blaue Rechteck ist die Stelle, an der Ihre Webseite angezeigt wird, wenn Sie Ihre eigene Webseite mithilfe der `url` Eigenschaft des [TaskInfo -Objekts](#the-taskinfo-object)laden. Weitere Details finden Sie unten im Abschnitt zur Dimensionierung des [Aufgabenmoduls.](#task-module-sizing)
1. Wenn Sie eine adaptive Karte über die `card` Eigenschaft des [TaskInfo -Objekts](#the-taskinfo-object) anzeigen, wird der Abstand für Sie hinzugefügt, andernfalls müssen Sie [dies selbst behandeln.](#task-module-css-for-htmljavascript-task-modules)
1. Adaptive Kartenschaltflächen werden hier gerendert. Wenn Sie Ihre eigene Seite verwenden, müssen Sie Eigene Schaltflächen erstellen.

## <a name="overview-of-invoking-and-dismissing-task-modules"></a>Übersicht über das Aufrufen und Schließen von Aufgabenmodulen

Aufgabenmodule können von Registerkarten, Bots oder Deep-Links aufgerufen werden, und was in einem angezeigt wird, kann entweder HTML oder eine adaptive Karte sein, sodass es eine große Flexibilität hinsichtlich ihrer Aufrufe und des Umgangs mit dem Ergebnis der Interaktion eines Benutzers gibt. In der folgenden Tabelle wird die Funktionsweise zusammengefasst:

| **Aufgerufen über...** | **Aufgabenmodul ist HTML/JavaScript** | **Aufgabenmodul ist adaptive Karte** |
| --- | --- | --- |
| **JavaScript auf einer Registerkarte** | 1. Verwenden Sie die Teams Client SDK-Funktion `tasks.startTask()` mit einer optionalen `submitHandler(err, result)` Rückruffunktion. <br/><br/> 2. Rufen Sie im Aufgabenmodulcode, wenn der Benutzer fertig ist, die Teams SDK-Funktion `tasks.submitTask()` mit einem Objekt als Parameter `result` auf. Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn als Parameter `result` auf.<br/><br/> 3. Wenn beim Aufrufen ein Fehler aufgetreten `tasks.startTask()` ist, wird die `submitHandler` Funktion stattdessen mit einer `err` Zeichenfolge aufgerufen. <br/><br/> 4. Sie können auch eine beim Aufruf angeben `completionBotId` – in diesem Fall wird `teams.startTask()` `result` stattdessen an den Bot gesendet. | 1. Rufen Sie die Teams Client-SDK-Funktion `tasks.startTask()` mit einem [TaskInfo-Objekt](#the-taskinfo-object) auf und `TaskInfo.card` enthalten den JSON-Code für die adaptive Karte, die im Popup des Aufgabenmoduls angezeigt wird. <br/><br/> 2. Wenn ein `submitHandler` Rückruf in angegeben `tasks.startTask()` wurde, ruft Teams ihn mit einer `err` Zeichenfolge auf, wenn beim Aufrufen ein Fehler aufgetreten ist `tasks.startTask()` oder wenn der Benutzer das Aufgabenmodul-Popup mit dem X oben rechts schließt. <br/><br/> 3. Wenn der Benutzer eine Action.Submit-Schaltfläche drückt, wird sein `data` Objekt als Wert von `result` zurückgegeben. |
| **Bot-Kartenschaltfläche** | 1. Botkartenschaltflächen können, je nach Schaltflächentyp, Aufgabenmodule auf zwei Arten aufrufen: eine Deep-Link-URL oder durch Senden einer `task/fetch` Nachricht. Die Funktionsweise von Deep-Link-URLs finden Sie weiter unten. <br/><br/> 2. Wenn die Aktion der Schaltfläche `type` `task/fetch` ( `Action.Submit` Schaltflächentyp für adaptive Karten) ist, wird ein `task/fetch invoke` Ereignis (ein HTTP POST unter den Deckeln) an den Bot gesendet, und der Bot antwortet auf den POST mit HTTP 200 und den Antworttext, der einen Wrapper um das [TaskInfo -Objekt](#the-taskinfo-object)enthält. Dies wird beim [Aufrufen eines Aufgabenmoduls über "task/fetch"](~/task-modules-and-cards/task-modules/task-modules-bots.md#invoking-a-task-module-through-taskfetch)ausführlich erläutert.<br/><br/> 3. Teams zeigt das Aufgabenmodul an. Wenn der Benutzer fertig ist, rufen Sie die Teams SDK-Funktion `tasks.submitTask()` mit einem Objekt als Parameter `result` auf. <br/><br/> 4. Der Bot empfängt eine `task/submit invoke` Nachricht, die das `result` Objekt enthält. Sie haben drei verschiedene Möglichkeiten, auf die Nachricht zu reagieren: indem Sie `task/submit` nichts tun (die Aufgabe wurde erfolgreich abgeschlossen), indem Sie dem Benutzer eine Nachricht in einem Popupfenster anzeigen oder ein anderes Aufgabenmodulfenster aufrufen (d. h. eine assistentenähnliche Oberfläche erstellen). Diese drei Optionen werden [in der ausführlichen Erläuterung zu Aufgabe/Übermittlung](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit)ausführlicher erläutert. | 1. Wie Schaltflächen auf Bot Framework-Karten unterstützen Schaltflächen auf adaptiven Karten zwei Möglichkeiten zum Aufrufen von Aufgabenmodulen: Deep-Link-URLs mit `Action.openUrl` Schaltflächen und `task/fetch` die Verwendung von `Action.Submit` Schaltflächen. <br/><br/> 2. Aufgabenmodule mit adaptiven Karten funktionieren sehr ähnlich wie der HTML-/JavaScript-Fall (siehe links). Der Hauptunterschied besteht darin, dass es keine Möglichkeit zum Aufrufen gibt, da es kein JavaScript gibt, wenn Sie adaptive Karten `tasks.submitTask()` verwenden. Stattdessen übernimmt Teams das `data` Objekt und gibt es als Nutzlast des `Action.Submit` `task/submit` Ereignisses zurück, wie [hier](~/task-modules-and-cards/task-modules/task-modules-bots.md#the-flexibility-of-tasksubmit)beschrieben. |
| **Deep-Link-URL** <br/>[URL-Syntax](#task-module-deep-link-syntax) | 1. Teams das Aufgabenmodul aufruft; die URL, die innerhalb der `<iframe>` angegebenen im `url` Parameter des Deep-Links angezeigt wird. Es gibt keinen `submitHandler` Rückruf. <br/><br/> 2. Rufen Sie innerhalb des JavaScript der Seite im Aufgabenmodul auf, `tasks.submitTask()` es mit einem Objekt als Parameter zu schließen, genauso wie beim Aufrufen von einer Registerkarte oder einer `result` Bot-Kartenschaltfläche. Die Abschlusslogik unterscheidet sich jedoch geringfügig. Wenn sich die Abschlusslogik auf dem Client befindet (d. h. wenn kein Bot vorhanden ist), gibt es keinen `submitHandler` Rückruf, daher muss sich jede Abschlusslogik im Code vor dem Aufruf `tasks.submitTask()` befinden. Aufruffehler werden nur über die Konsole gemeldet. Wenn Sie über einen Bot verfügen, können Sie im `completionBotId` Deep-Link einen Parameter angeben, um das Objekt über ein Ereignis zu `result` `task/submit` senden. | 1. Teams das Aufgabenmodul aufruft; Der JSON-Kartentext der adaptiven Karte wird als URL-codierter Wert des `card` Parameters des Deep-Links angegeben. <br/><br/> 2. Der Benutzer schließt das Aufgabenmodul, indem er oben rechts im Aufgabenmodul auf das X klickt oder `Action.Submit` eine Schaltfläche auf der Karte drückt. Da kein `submitHandler` Aufruf erforderlich ist, müssen Sie über einen Bot verfügen, an den der Wert der Felder der adaptiven Karte gesendet werden kann. Sie verwenden den `completionBotId` Parameter im Deep-Link, um den Bot anzugeben, an den die Daten über ein Ereignis gesendet werden `task/submit invoke` sollen. |

## <a name="the-taskinfo-object"></a>Das TaskInfo-Objekt

Das `TaskInfo` Objekt enthält die Metadaten für ein Aufgabenmodul. Die Objektdefinition ist unten aufgeführt. Sie **müssen** entweder `url` für einen eingebetteten iFrame oder `card` eine adaptive Karte definieren.

| Attribut | Typ | Beschreibung |
| --- | --- | --- |
| `title` | string | Wird unter dem App-Namen und rechts neben dem App-Symbol angezeigt. |
| `height` | Zahl oder Zeichenfolge | Dies kann eine Zahl sein, die die Höhe des Aufgabenmoduls in Pixel oder `small` `medium` , oder `large` darstellt. [Siehe unten, wie Höhe und Breite behandelt werden.](#task-module-sizing) |
| `width` | Zahl oder Zeichenfolge | Dies kann eine Zahl sein, die die Breite des Aufgabenmoduls in Pixel oder `small` `medium` , oder `large` darstellt. [Siehe unten, wie Höhe und Breite behandelt werden.](#task-module-sizing) |
| `url` | Zeichenfolge | Die URL der Seite, die als `<iframe>` innerhalb des Aufgabenmoduls geladen wurde. Die Domäne der URL muss sich im [ValidDomains-Array](~/resources/schema/manifest-schema.md#validdomains) der App im Manifest Ihrer App befinden. |
| `card` | Adaptive Karte oder eine Adaptive Karten-Bot-Kartenanlage | Der JSON-Code für die adaptive Karte, der im Aufgabenmodul angezeigt werden soll. Wenn Sie von einem Bot aufrufen, müssen Sie die JSON der adaptiven Karte in einem Bot `attachment` Framework-Objekt verwenden. Auf einer Registerkarte verwenden Sie nur eine adaptive Karte. [Hier ist ein Beispiel.](#adaptive-card-or-adaptive-card-bot-card-attachment) |
| `fallbackUrl` | Zeichenfolge | Wenn ein Client das Aufgabenmodulfeature nicht unterstützt, wird diese URL auf einer Browserregisterkarte geöffnet. |
| `completionBotId` | Zeichenfolge | Gibt eine Bot-App-ID an, an die das Ergebnis der Benutzerinteraktion mit dem Aufgabenmodul gesendet werden soll. Wenn angegeben, empfängt der Bot ein `task/submit invoke` Ereignis mit einem JSON-Objekt in der Ereignisnutzlast. |

> [!NOTE]
> Das Aufgabenmodulfeature erfordert, dass die Domänen aller URLs, die Sie laden möchten, im Array im Manifest Ihrer App enthalten `validDomains` sind.

## <a name="task-module-sizing"></a>Größe des Aufgabenmoduls

Die Verwendung ganzer Zahlen für `TaskInfo.width` und legt die Höhe und Breite in Pixel `TaskInfo.height` fest. Abhängig von der Größe des Fensters und der Bildschirmauflösung des Teams werden sie jedoch proportional reduziert, während das Seitenverhältnis (Breite/Höhe) beibehalten wird.

If `TaskInfo.width` and are , or the size of the red rectangle in the picture above is `TaskInfo.height` a proportion of the available `"small"` `"medium"` `"large"` space: 20%, 50%, 60% for `width` and 20%, 50%, 66% for `height` .

Aufgabenmodule, die von einer Registerkarte aufgerufen werden, können dynamisch geändert werden. Nach dem Aufruf `tasks.startTask()` können Sie `tasks.updateTask(newSize)` aufrufen, wo die Höhen- und Breiteneigenschaften des newSize-Objekts der TaskInfo-Spezifikation entsprechen (z. B. `{ height: 'medium', width: 'medium' }`).

## <a name="task-module-css-for-htmljavascript-task-modules"></a>Aufgabenmodul-CSS für HTML/JavaScript-Aufgabenmodule

HTML/JavaScript-basierte Aufgabenmodule haben Zugriff auf den gesamten Bereich des Aufgabenmoduls unterhalb des Headers. Dies bietet zwar ein hohes Maß an Flexibilität, wenn Sie den Abstand an den Rändern an den Kopfzeilenelementen ausrichten möchten und unnötige Bildlaufleisten vermeiden möchten, müssen Sie das richtige CSS bereitstellen. Hier sind einige Beispiele für einige Anwendungsfälle.

### <a name="example-1---youtube-video"></a>Beispiel 1 – YouTube-Video

YouTube bietet die Möglichkeit, Videos auf Webseiten einzubetten. Mithilfe einer einfachen Stubwebseite ist es einfach, dies in einem Aufgabenmodul anzuzeigen:

![YouTube-Video](~/assets/images/task-module/youtube-example.png)

Hier sehen Sie den HTML-Code für diese Seite ohne CSS:

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

### <a name="example-2---powerapp"></a>Beispiel 2 – PowerApp

Sie können den gleichen Ansatz auch verwenden, um eine PowerApp einzubetten. Da die Höhe/Breite einer einzelnen PowerApp anpassbar ist, müssen Sie möglicherweise die Höhe und Breite anpassen, um die gewünschte Präsentation zu erzielen.

![Ressourcenverwaltungs-PowerApp](~/assets/images/task-module/powerapp-example.png)

```html
<iframe width="720" height="520" src="https://web.powerapps.com/webplayer/iframeapp?source=iframe&screenColor=rgba(104,101,171,1)&appId=/providers/Microsoft.PowerApps/apps/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></iframe>
```

Und das CSS lautet:

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

## <a name="adaptive-card-or-adaptive-card-bot-card-attachment"></a>Adaptive Karte oder Adaptive Karten-Bot-Kartenanlage

Wie bereits erwähnt, müssen Sie je nachdem, wie Sie Ihre Karte aufrufen, `card` entweder eine adaptive Karte oder eine Adaptive Karten-Bot-Kartenanlage (bei der es sich nur um eine adaptive Karte handelt, die in ein Anlagenobjekt eingeschlossen ist) verwenden.

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

Wenn Sie von einem Bot aufrufen, müssen Sie eine Adaptive Karten-Bot-Kartenanlage verwenden, wie im folgenden Beispiel gezeigt:

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

## <a name="task-module-deep-link-syntax"></a>Deep Link-Syntax des Aufgabenmoduls

Ein Aufgabenmodul-Deep-Link ist nur eine Serialisierung des [TaskInfo-Objekts](#the-taskinfo-object) mit zwei weiteren `APP_ID` Informationen, und `BOT_APP_ID` optional:

`https://teams.microsoft.com/l/task/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

`https://teams.microsoft.com/l/task/APP_ID?card=<TaskInfo.card>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID`

Unter [TaskInfo-Objekt](#the-taskinfo-object) finden Sie die Datentypen und zulässigen Werte für `<TaskInfo.url>` , , , und `<TaskInfo.card>` `<TaskInfo.height>` `<TaskInfo.width>` `<TaskInfo.title>` .

> [!TIP]
> Achten Sie darauf, den Deep-Link urlcodieren, insbesondere bei Verwendung des Parameters (z. B. `card` JavaScript-Funktion). [ `encodeURI()` ](https://www.w3schools.com/jsref/jsref_encodeURI.asp)

Hier sind die Informationen `APP_ID` zu `BOT_APP_ID` und:

| Wert | Typ | Pflichtfeld? | Beschreibung |
| --- | --- | --- | --- |
| `APP_ID` | string | Ja | Die [ID](~/resources/schema/manifest-schema.md#id) der App, die das Aufgabenmodul aufruft. Das [Array "validDomains"](~/resources/schema/manifest-schema.md#validdomains) im Manifest `APP_ID` muss die Domäne für `url` `url` "if" in der URL enthalten. (Die App-ID ist bereits bekannt, wenn ein Aufgabenmodul von einer Registerkarte oder einem Bot aufgerufen wird, weshalb sie nicht in enthalten `TaskInfo` ist.) |
| `BOT_APP_ID` | Zeichenfolge | Nein | Wenn ein Wert für `completionBotId` angegeben wird, wird das `result` Objekt über eine Nachricht an den `task/submit invoke` angegebenen Bot gesendet. `BOT_APP_ID` muss als Bot im Manifest der App angegeben werden, d. h. Sie können ihn nicht einfach an einen bot senden. |

Beachten Sie, dass sie gültig ist und gleich ist. In vielen Fällen ist dies der Fall, wenn eine App über einen Bot verfügt, `APP_ID` `BOT_APP_ID` da empfohlen wird, diese als App-ID zu verwenden, falls vorhanden.

## <a name="keyboard-and-accessibility-guidelines"></a>Richtlinien für Tastatur und Barrierefreiheit

Bei HTML/JavaScript-basierten Aufgabenmodulen liegt es in Ihrer Verantwortung, sicherzustellen, dass das Aufgabenmodul Ihrer App mit einer Tastatur verwendet werden kann. Sprachausgabeprogramme sind auch von der Möglichkeit abhängig, mit der Tastatur zu navigieren. Praktisch bedeutet dies zwei Dinge:

1. Verwenden des [Tabindex-Attributs](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) in Ihren HTML-Tags, um zu steuern, welche Elemente fokussiert werden können und ob/wo es an der sequenziellen Tastaturnavigation beteiligt ist (in der Regel mit den Tasten <kbd>"Tab"</kbd> und <kbd>"Shift-Tab").</kbd>
2. Behandeln des <kbd>Esc-Schlüssels</kbd> im JavaScript für Ihr Aufgabenmodul. Hier ist ein Codebeispiel, in dem gezeigt wird, wie dies funktioniert:

  ```javascript
  // Handle the Esc key
  document.onkeyup = function(event) {
  if ((event.key === 27) || (event.key === "Escape")) {
    microsoftTeams.submitTask(null); // this will return an err object to the completionHandler()
    }
  }
  ```

Microsoft Teams stellen sicher, dass die Tastaturnavigation vom Aufgabenmodulheader in Ihren HTML-Code ordnungsgemäß funktioniert und umgekehrt.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Aufgabenmodulbeispiel (Bots-V4) | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-task-module/nodejs)| 
|Aufgabenmodulbeispiel (Registerkarten + Bots-V3) | Beispiele zum Erstellen von Aufgabenmodulen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/54.teams-task-module)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/54.teams-task-module)|

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen anfordern](../concepts/device-capabilities/native-device-permissions.md)
* [Integrieren von Medienfunktionen](../concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Integrieren von QR- oder Strichcodescannern in Teams](../concepts/device-capabilities/qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](../concepts/device-capabilities/location-capability.md)
