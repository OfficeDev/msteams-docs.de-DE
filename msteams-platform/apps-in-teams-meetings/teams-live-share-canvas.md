---
title: Übersicht über die Live-Freigabe-Canvas
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Live Share-Canvas, eine Erweiterung, die Freihandeingaben, Laserpointer und Cursor für Besprechungs-Apps ermöglicht.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 10/04/2022
ms.openlocfilehash: 9d1a776432f728c1e56caa357089be6e47c17e4c
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560610"
---
# <a name="live-share-canvas-overview"></a>Übersicht über die Live-Freigabe-Canvas

:::image type="content" source="../assets/images/teams-live-share/live-share-canvas-docs-feature-1.png" alt-text="Screenshot zeigt ein Beispiel für einen Zeichenbereich, der mit anderen Besprechungsteilnehmern in einer Teams-Besprechung synchronisiert ist.":::

In Konferenzräumen und Klassenzimmern auf der ganzen Welt sind Whiteboards ein zentraler Bestandteil der Zusammenarbeit. In der Modernen Zeit reicht das Whiteboard jedoch nicht mehr aus. Da zahlreiche digitale Tools wie PowerPoint im Mittelpunkt der Zusammenarbeit in der Moderne stehen, ist es wichtig, dasselbe kreative Potenzial zu ermöglichen.

Um eine nahtlosere Zusammenarbeit zu ermöglichen, hat Microsoft PowerPoint Live erstellt, die entscheidend für die Arbeitsweise von Personen in Teams geworden ist. Referenten können Folien kommentieren, die jeder sehen kann, indem sie Stifte, Textmarker und Laserpointer verwenden, um die Aufmerksamkeit auf wichtige Konzepte zu lenken. Mithilfe der Live Share-Canvas kann Ihre App mit minimalem Aufwand die Leistungsfähigkeit PowerPoint Live Freihandtools nutzen.

## <a name="install"></a>Installieren

So fügen Sie ihrer Anwendung mithilfe von NPM die neueste Version des SDK hinzu:

```bash
npm install @microsoft/live-share@next --save
npm install @microsoft/live-share-canvas@next --save
```

ODER

So fügen Sie die neueste Version des SDK mit [Yarn](https://yarnpkg.com/) zu Ihrer Anwendung hinzu:

```bash
yarn add @microsoft/live-share@next
yarn add @microsoft/live-share-canvas@next
```

## <a name="setting-up-the-package"></a>Einrichten des Pakets

Die Live-Freigabe-Canvas verfügt über zwei primäre Klassen, die die Zusammenarbeit mit Schlüsseln ermöglichen: `InkingManager` und `LiveCanvas`. `InkingManager` ist für das Anfügen eines Elements mit vollem Funktionsumfang `<canvas>` an Ihre App verantwortlich, während `LiveCanvas` die Remotesynchronisierung mit anderen Besprechungsteilnehmern verwaltet wird. Zusammen verwendet, kann Ihre App in nur wenigen Codezeilen über eine vollständige Whiteboard-ähnliche Funktionalität verfügen.

| Klassen                                                                     | Beschreibung                                                                                                                                                                                                                                      |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [InkingManager](/javascript/api/@microsoft/live-share-canvas/inkingmanager) | Klasse, die einem bestimmten `<div>` Element ein `<canvas>` Element hinzufügt, um Stift- oder Textmarkerstriche, Laserpointer, Linien und Pfeile sowie Radierer automatisch zu verwalten. Macht eine Reihe von APIs (um zu steuern, welches Tool aktiv ist) und grundlegende Konfigurationseinstellungen verfügbar. |
| [LiveCanvas](/javascript/api/@microsoft/live-share-canvas/livecanvas)      | Eine `SharedObject` Klasse, die Striche und Cursorpositionen für `InkingManager` jeden in einer Live Share-Sitzung synchronisiert.                                                                                                                   |

Beispiel:

```html
<body>
  <div id="canvas-host"></div>
</body>
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient } from "@microsoft/live-share";
import { InkingManager, LiveCanvas } from "@microsoft/live-share-canvas";

// Setup the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { liveCanvas: LiveCanvas },
};
const { container } = await liveShare.joinContainer(schema);
const { liveCanvas } = container.initialObjects;

// Get the canvas host element
const canvasHostElement = document.getElementById("canvas-host");
const inkingManager = new InkingManager(canvasHostElement);

// Begin synchronization for LiveCanvas
await liveCanvas.initialize(inkingManager);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient } from "@microsoft/live-share";
import { InkingManager, LiveCanvas } from "@microsoft/live-share-canvas";
import { ContainerSchema } from "fluid-framework";

// Setup the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { liveCanvas: LiveCanvas },
};
const { container } = await liveShare.joinContainer(schema);
const liveCanvas = container.initialObjects.liveCanvas as LiveCanvas;

// Get the canvas host element
const canvasHostElement = document.getElementById("canvas-host");
const inkingManager = new InkingManager(canvasHostElement);

// Begin synchronization for LiveCanvas
await liveCanvas.initialize(inkingManager);
```

---

## <a name="canvas-tools-and-cursors"></a>Canvas-Tools und Cursor

Nachdem die Live-Freigabe-Canvas eingerichtet und synchronisiert wurde, können Sie den Zeichenbereich für Benutzerinteraktionen konfigurieren, z. B. Schaltflächen zum Auswählen eines Stifttools. In diesem Abschnitt wird erläutert, welche Tools verfügbar sind und wie sie verwendet werden können.

### <a name="inking-tools"></a>Freihandtools

Jedes Freihandtool in der Live Share-Canvas rendert Striche, während Benutzer zeichnen. Bei Verwendung eines Touchscreens oder Eingabestifts unterstützen die Tools auch die Druckdynamik, was sich auf die Strichbreite auswirkt. Zu den Konfigurationseinstellungen gehören Pinselfarbe, Stärke, Form und ein optionaler Endpfeil.

#### <a name="pen-tool"></a>Stifttool

:::image type="content" source="../assets/images/teams-live-share/canvas-pen-tool.gif" alt-text="GIF zeigt ein Beispiel für Zeichenstriche auf dem Zeichenbereich mithilfe des Stifttools.":::

Das Stifttool zeichnet einfarbige Striche, die im Zeichenbereich gespeichert sind. Die Standard-Spitzenform ist ein Kreis.

```html
<div>
  <button id="pen">Enable Pen</button>
  <label for="pen-color">Select a color:</label>
  <input type="color" id="color" name="color" value="#000000" />
  <button id="pen-tip-size">Increase pen size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to pen
document.getElementById("pen").onclick = () => {
  inkingManager.tool = InkingTool.pen;
};
// Change the selected color for pen
document.getElementById("pen-color").onchange = () => {
  const colorPicker = document.getElementById("color");
  inkingManager.penBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for pen
document.getElementById("pen-tip-size").onclick = () => {
  inkingManager.penBrush.tipSize = inkingManager.penBrush.tipSize + 1;
};
```

#### <a name="highlighter-tool"></a>Textmarkertool

:::image type="content" source="../assets/images/teams-live-share/canvas-highlighter-tool.gif" alt-text="GIF zeigt ein Beispiel für das Zeichnen transluzenter Striche auf dem Zeichenbereich mithilfe des Textmarkertools.":::

Das Textmarkertool zeichnet durchscheinende Striche, die in der Canvas gespeichert sind. Die Standardspitze ist ein Quadrat.

```html
<div>
  <button id="highlighter">Enable Highlighter</button><br />
  <label for="highlighter-color">Select a color:</label>
  <input type="color" id="highlighter-color" name="highlighter-color" value="#FFFC00" />
  <button id="highlighter-tip-size">Increase tip size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to highlighter
document.getElementById("highlighter").onclick = () => {
  inkingManager.tool = InkingTool.highlighter;
};
// Change the selected color for highlighter
document.getElementById("highlighter-color").onchange = () => {
  const colorPicker = document.getElementById("highlighter-color");
  inkingManager.highlighterBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for highlighter
document.getElementById("highlighter-tip-size").onclick = () => {
  inkingManager.highlighterBrush.tipSize = inkingManager.penBrush.tipSize + 1;
};
```

#### <a name="eraser-tool"></a>Radierertool

:::image type="content" source="../assets/images/teams-live-share/canvas-eraser-tool.gif" alt-text="GIF zeigt ein Beispiel für das Löschen von Strichen auf der Canvas mithilfe des Radierertools.":::

Das Radierertool löscht ganze Striche, die seinen Pfad kreuzen.

```html
<div>
  <button id="eraser">Enable Eraser</button><br />
  <button id="eraser-size">Increase eraser size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to eraser
document.getElementById("eraser").onclick = () => {
  inkingManager.tool = InkingTool.eraser;
};
// Increase the tip size for eraser
document.getElementById("eraser-size").onclick = () => {
  inkingManager.eraserSize = inkingManager.eraserSize + 1;
};
```

#### <a name="point-eraser-tool"></a>Punktradierertool

:::image type="content" source="../assets/images/teams-live-share/canvas-point-eraser-tool.gif" alt-text="GIF zeigt ein Beispiel für das Entfernen einzelner Punkte innerhalb von Strichen auf der Canvas mithilfe des Punktradierertools.":::

Das Punktradierertool löscht einzelne Punkte innerhalb von Strichen, die seinen Pfad kreuzen, indem vorhandene Striche in zwei Hälften geteilt werden. Dieses Tool ist rechenintensiv und kann zu langsameren Bildfrequenzen für Ihre Benutzer führen.

> [!NOTE]
> Der Punktradierer hat dieselbe Radiererpunktgröße wie das normale Radierertool.

```html
<div>
  <button id="point-eraser">Enable Point Eraser</button><br />
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to eraser
document.getElementById("point-eraser").onclick = () => {
  inkingManager.tool = InkingTool.pointEraser;
};
```

#### <a name="laser-pointer"></a>Laserpointer

:::image type="content" source="../assets/images/teams-live-share/canvas-laser-tool.gif" alt-text="GIF zeigt ein Beispiel für Zeichenstriche auf der Canvas mithilfe des Laserpointertools.":::

Der Laserpointer ist einzigartig, da die Spitze des Lasers eine nachgestellte Wirkung hat, während Sie die Maus bewegen. Wenn Sie Striche zeichnen, wird der nachfolgende Effekt für einen kurzen Zeitraum gerendert, bevor er vollständig ausgeblendet wird. Dieses Tool ist perfekt, um während einer Besprechung auf Informationen auf dem Bildschirm hinzuweisen, da der Referent nicht zwischen Tools wechseln muss, um Striche zu löschen.

```html
<div>
  <button id="laser">Enable Laser Pointer</button><br />
  <label for="laser-color">Select a color:</label>
  <input type="color" id="laser-color" name="laser-color" value="#000000" />
  <button id="laser-tip-size">Increase tip size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to laser pointer
document.getElementById("laser").onclick = () => {
  inkingManager.tool = InkingTool.highlighter;
};
// Change the selected color for laser pointer
document.getElementById("laser-color").onchange = () => {
  const colorPicker = document.getElementById("laser-color");
  inkingManager.laserPointerBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for laser pointer
document.getElementById("laser-tip-size").onclick = () => {
  inkingManager.laserPointerBrush.tipSize = inkingManager.laserPointerBrush.tipSize + 1;
};
```

#### <a name="line-and-arrow-tools"></a>Linien- und Pfeiltools

:::image type="content" source="../assets/images/teams-live-share/canvas-line-tool.gif" alt-text="GIF zeigt ein Beispiel für das Zeichnen gerader Linien auf einem Zeichenbereich mithilfe des Linien- und Pfeiltools.":::

Mit dem Linientool können Benutzer gerade Linien von einem Punkt zum anderen zeichnen, mit einem optionalen Pfeil, der am Ende angewendet werden kann.

```html
<div>
  <button id="line">Enable Line</button><br />
  <button id="line-arrow">Enable Arrow</button><br />
  <input type="color" id="line-color" name="line-color" value="#000000" />
  <button id="line-tip-size">Increase tip size</button>
</div>
```

```javascript
import {
  InkingManager,
  InkingTool,
  fromCssColor,
} from "@microsoft/live-share-canvas";
// ...

// Change the selected tool to line
document.getElementById("line").onclick = () => {
  inkingManager.tool = InkingTool.line;
  inkingManager.lineBrush.endArrow = "none";
};
// Change the selected tool to line
document.getElementById("line-arrow").onclick = () => {
  inkingManager.tool = InkingTool.line;
  inkingManager.lineBrush.endArrow = "open";
};
// Change the selected color for lineBrush
document.getElementById("line-color").onchange = () => {
  const colorPicker = document.getElementById("line-color");
  inkingManager.lineBrush.color = fromCssColor(colorPicker.value);
};
// Increase the tip size for lineBrush
document.getElementById("line-tip-size").onclick = () => {
  inkingManager.lineBrush.tipSize = inkingManager.lineBrush.tipSize + 1;
};
```

#### <a name="clear-all-strokes"></a>Alle Striche löschen

Sie können alle Striche im Zeichenbereich löschen, indem Sie aufrufen `inkingManager.clear()`. Dadurch werden alle Striche aus der Canvas gelöscht.

### <a name="cursors"></a>Cursor

:::image type="content" source="../assets/images/teams-live-share/canvas-cursors.gif" alt-text="GIF zeigt ein Beispiel für Benutzer, die einen Cursor auf einer Canvas freigeben.":::

Sie können Livecursor in Ihrer Anwendung aktivieren, damit Benutzer die Cursorpositionen des anderen auf der Canvas nachverfolgen können. Im Gegensatz zu den Freihandtools werden Cursor vollständig durch die `LiveCanvas` Klasse bewegt. Sie können optional einen Namen und ein Bild angeben, um jeden Benutzer zu identifizieren. Sie können Cursor separat oder mit den Freihandtools aktivieren.

```javascript
// Optional. Set user display info
liveCanvas.onGetLocalUserInfo = () => {
  return {
    displayName: "YOUR USER NAME",
    pictureUri: "YOUR USER PICTURE URI",
  };
};
// Toggle Live Canvas cursor enabled state
liveCanvas.isCursorShared = !isCursorShared;
```

## <a name="optimizing-across-devices"></a>Geräteübergreifende Optimierung

Bei den meisten Anwendungen im Web werden Inhalte je nach Bildschirmgröße oder variierendem Anwendungszustand unterschiedlich gerendert. Wenn `InkingManager` die App nicht ordnungsgemäß optimiert ist, kann dies dazu führen, dass Striche und Cursor für jeden Benutzer unterschiedlich angezeigt werden. Die Live Share-Canvas unterstützt einen einfachen Satz von APIs, mit dem die `<canvas>` Strichpositionen korrekt an Ihren Inhalt angepasst werden können.

Standardmäßig funktioniert die Live Share-Canvas wie eine Whiteboard-App, wobei der Inhalt mit einem 1x-Zoomfaktor zentriert am Viewport ausgerichtet wird. Nur ein Teil des Inhalts wird innerhalb der sichtbaren Grenzen des `<canvas>`gerendert. Vom Konzept her ist es so, als würde man ein Video aus der Vogelperspektive aufnehmen. Während der Viewport der Kamera einen Teil der Welt darunter aufzeichnet, dehnt sich die reale Welt nahezu unendlich in jede Richtung aus.

Hier ist ein einfaches Diagramm, um dieses Konzept zu visualisieren:

:::image type="content" source="../assets/images/teams-live-share/live-share-canvas-capabilities-docs-diagram-1.png" alt-text="Screenshot zeigt das Vollbild-Canvas-Layout für Desktop- und mobile Benutzer zusammen.":::

Sie können dieses Verhalten auf folgende Weise anpassen:

- Ändern des Startbezugspunkts in die obere linke Ecke des Zeichenbereichs.
- Ändern Sie die x- und y-Pixelpositionen des Viewports.
- Ändern Sie die Skalierungsebene des Viewports.

> [!NOTE]
> Referenzpunkte, Offsets und Skalierungsebenen sind lokal für den Client und werden nicht über Besprechungsteilnehmer hinweg synchronisiert.

Beispiel:

```html
<body>
  <button id="pan-left">Pan left</button>
  <button id="pan-up">Pan up</button>
  <button id="pan-right">Pan right</button>
  <button id="pan-down">Pan down</button>
  <button id="zoom-out">Zoom out</button>
  <button id="zoom-in">Zoom in</button>
  <button id="change-reference">Change reference</button>
</body>
```

```javascript
// ...

// Pan left
document.getElementById("pan-left").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x - 10,
    y: inkingManager.offset.y,
  };
};
// Pan up
document.getElementById("pan-up").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x,
    y: inkingManager.offset.y - 10,
  };
};
// Pan right
document.getElementById("pan-right").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x + 10,
    y: inkingManager.offset.y,
  };
};
// Pan down
document.getElementById("pan-down").onclick = () => {
  inkingManager.offset = {
    x: inkingManager.offset.x,
    y: inkingManager.offset.y + 10,
  };
};
// Zoom out
document.getElementById("zoom-out").onclick = () => {
  if (inkingManager.scale > 0.1) {
    inkingManager.scale -= 0.1;
  }
};
// Zoom in
document.getElementById("zoom-in").onclick = () => {
  inkingManager.scale += 0.1;
};
// Change reference
document.getElementById("change-reference").onclick = () => {
  if (inkingManager.referencePoint === "center") {
    inkingManager.referencePoint = "topLeft";
  } else {
    inkingManager.referencePoint = "center";
  }
};
```

## <a name="ideal-scenarios"></a>Ideale Szenarien

Da Webseiten in allen Formen und Größen verfügbar sind, ist es nicht möglich, die Live Share-Canvas so zu gestalten, dass sie jedes Szenario unterstützt. Das Paket eignet sich ideal für Szenarien, in denen alle Benutzer denselben Inhalt gleichzeitig betrachten. Obwohl nicht alle Inhalte auf dem Bildschirm sichtbar sein müssen, muss es sich um Inhalte handeln, die geräteübergreifend linear skaliert werden.

Hier sind einige Beispiele für Szenarien, in denen die Live Share-Canvas eine großartige Option für Ihre Anwendung ist:

- Überlagern Sie Bilder und Videos, die mit demselben Seitenverhältnis auf allen Clients gerendert werden.
- Anzeigen einer Karte, eines 3D-Modells oder eines Whiteboards aus demselben Drehwinkel.

Beide Szenarien funktionieren gut, da der Inhalt auf allen Geräten gleich angezeigt werden kann, auch wenn die Benutzer ihn mit unterschiedlichen Zoomstufen und Offsets betrachten. Wenn sich das Layout oder der Inhalt Ihrer App abhängig von der Bildschirmgröße ändert und es nicht möglich ist, eine gemeinsame Ansicht für alle Teilnehmer zu generieren, eignet sich die Livefreigabe-Canvas möglicherweise nicht gut für Ihr Szenario.

## <a name="code-samples"></a>Codebeispiele

| Beispielname          | Beschreibung                            | JavaScript                                                                                |
| -------------------- | -------------------------------------- | ----------------------------------------------------------------------------------------- |
| Live Canvas-Demo     | Einfache Whiteboard-Anwendung.         | [View](https://github.com/microsoft/live-share-sdk/tree/main/samples/03.live-canvas-demo) |
| React-Medienvorlage | Zeichnen Sie über einem synchronisierten Videoplayer. | [View](https://aka.ms/liveshare-mediatemplate)                                            |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Agiles Poker-Tutorial](../sbs-teams-live-share.yml)

## <a name="see-also"></a>Siehe auch

- [Live Share SDK – FAQ](teams-live-share-faq.md)
- [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
- [Referenzdokumente zum Live Share Canvas SDK](/javascript/api/@microsoft/live-share-canvas/)
- [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
