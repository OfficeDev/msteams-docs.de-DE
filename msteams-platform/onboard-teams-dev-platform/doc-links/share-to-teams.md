---
title: Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website
description: Vorgehensweise hinzufügen der Schaltfläche "Share to Teams Embedded" auf Ihrer Website
keywords: Freigeben von Teams in Microsoft Teams
ms.openlocfilehash: 0ebd47af068bf523f27c19241b85d2137af3ada6
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652016"
---
# <a name="adding-a-share-to-teams-button-to-your-website"></a>Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website

>[!NOTE]
> * Nur die Desktop Versionen von Edge und Chrome werden unterstützt.
> * Die Verwendung von Freemium-oder Gastkonten wird nicht unterstützt.

Drittanbieterwebsites können das Startprogramm Skript verwenden, um Share to Teams-Schaltflächen auf Ihren Webseiten einzubetten, wodurch die Benutzeroberfläche für Teams in einem Popupfenster gestartet wird, wenn darauf geklickt wird. Auf diese Weise können Sie einen Link direkt für einen beliebigen Benutzer oder Microsoft Teams-Kanal freigeben, ohne Kontext zu wechseln.

![Popup "an Teams freigeben"](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a>Vorgehensweise Einbetten einer Share to Teams-Schaltfläche

Zunächst müssen Sie das `launcher.js` Skript auf Ihrer Webseite hinzufügen.

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

Fügen Sie als nächstes ein HTML-Element auf Ihrer Webseite mit dem `teams-share-button` Class-Attribut und dem Link hinzu, der in dem Attribut freigegeben werden soll `data-href` .

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

Dadurch wird das Microsoft Teams-Symbol zu Ihrer Website hinzugefügt.

![Symbol "an Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

Wenn Sie eine andere Symbolgröße für die Schaltfläche Freigeben für Teams verwenden möchten, verwenden Sie optional das- `data-icon-px-size` Attribut.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

Wenn Sie wissen, dass die URL-Vorschau von Ihrem Link freigegeben wird, in Microsoft Teams nicht gut gerendert wird (beispielsweise würde die Verknüpfung Benutzerauthentifizierung erfordern), können Sie die URL-Vorschau deaktivieren, indem Sie das `data-preview` auf festgelegte Attribut hinzufügen `false` .

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

Wenn die Seite Inhalt dynamisch rendert, können Sie die `shareToMicrosoftTeams.renderButtons()` -Methode verwenden, um zu erzwingen, dass die Schaltfläche **Freigeben** an der entsprechenden Stelle in der Pipeline gerendert wird.

## <a name="crafting-your-website-preview"></a>Fertigen Ihrer Website Vorschau

Wenn Ihre Website für Teams freigegeben wird, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website. Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website (der URL) die entsprechenden Metadaten hinzugefügt werden `data-href` . In der folgenden Tabelle werden die erforderlichen Tags dargestellt. Sie können entweder die HTML-Standardversionen oder die Open Graph-Version verwenden.

Damit die Vorschau angezeigt wird, müssen Sie Folgendes tun:

* Fügen Sie entweder ein Miniaturbild oder sowohl einen Titel als auch eine Beschreibung ein (um optimale Ergebnisse zu erzielen, schließen Sie alle drei ein).
* Für die freigegebene URL kann keine Authentifizierung erforderlich sein. Wenn dies der Fall ist, können Sie ihn trotzdem freigeben, die Vorschau wird jedoch nicht erstellt.

|Wert|Metatag| Diagramm öffnen|
|----|----|----|
|Title|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Beschreibung|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Miniaturbild| keine |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a>Freigeben für Teams für Bildungseinrichtungen

Für Lehrer, die die Schaltfläche "für Teams freigeben" verwenden, erhalten Sie eine zusätzliche Option für `Create an Assignment` . Auf diese Weise können Sie schnell eine Zuordnung im ausgewählten Team basierend auf dem freigegebenen Link erstellen.

![Popup "an Teams freigeben"](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Vollständige launcher.js Definition

| Eigenschaft | HTML-Attribut | Typ | Standard | Beschreibung |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/v | Die href des freizugebenden Inhalts. |
| Vorschau | `data-preview` | Boolean (als Zeichenfolge) | `true` | Gibt an, ob eine Vorschau des freizugebenden Inhalts angezeigt werden soll. |
| iconPxSize | `data-icon-px-size` | Zahl (als Zeichenfolge) | `32` | Die Größe der zu rendernden Schaltfläche "Share-to-Teams" in Pixel. |
| msgText | `data-msg-text` | string | n/v | Standard Text, der vor dem Link im Feld Nachricht erstellen eingefügt werden soll (Grenzwert für 200 Zeichen) |
| assignInstr | `data-assign-instr` | string | n/v | Standard Text, der in das Feldzuweisungen "Instructions" eingefügt werden soll (Grenzwert für 200 Zeichen) |
| assignTitle | `data-assign-title` | string | n/v | Standard Text, der in das Feldzuweisungen "Title" eingefügt werden soll (Grenzwert für 50 Zeichen) |

### <a name="methods"></a>Methoden

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (optional): `{ elements?: HTMLElement[] }`

Rendert alle derzeit auf der Seite befindlichen Freigabe Schaltflächen. Wenn ein optionales `options` Objekt mit einer Liste von Elementen angegeben wird, werden diese Elemente in Freigabe Schaltflächen gerendert.

### <a name="setting-default-form-values"></a>Festlegen von Standardformular Werten

Optional können Sie die Standardwerte für die folgenden Felder im Formular "freigeben für Teams" festlegen:

* Sagen Sie etwas zu diesem ( `msgText` )
* Zuordnungsanweisungen ( `assignInstr` )
* Zuordnungs Titel ( `assignTitle` )

#### <a name="example-default-form-values"></a>Beispiel: Standardformular Werte

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
