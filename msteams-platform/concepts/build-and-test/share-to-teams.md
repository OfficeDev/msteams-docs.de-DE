---
title: Erstellen einer Schaltfläche zum Teilen in Microsoft Teams
description: So fügen Sie die eingebettete Schaltfläche "Zu Teams freigeben" auf Ihrer Website hinzu
ms.topic: reference
keywords: Share Teams Share-to-Teams
ms.openlocfilehash: 46091c957137cc871095ca6a57c0d61fa79d9458
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014334"
---
# <a name="create-a-share-to-teams-button-for-your-website"></a>Erstellen einer Schaltfläche zum Teilen in Teams für Ihre Website

>[!NOTE]
> * Nur die Desktopversionen von Edge und Chrome werden unterstützt.
> * Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.

Drittanbieterwebsites können das Startskript verwenden, um Schaltflächen "In Teams freigeben" auf ihren Webseiten einzubetten, wodurch die Freigabe für Teams in einem Popupfenster gestartet wird, wenn darauf geklickt wird. Dadurch können Sie einen Link direkt für eine beliebige Person oder einen Microsoft Teams-Kanal freigeben, ohne den Kontext zu wechseln.

![Popup "Für Teams freigeben"](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a>So betten Sie eine Schaltfläche "In Teams freigeben" ein

Zunächst müssen Sie das Skript auf Ihrer `launcher.js` Webseite hinzufügen.

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

Fügen Sie als Nächstes ein HTML-Element auf Ihrer Webseite mit dem Klassenattribut und dem Link zum Freigeben `teams-share-button` im Attribut `data-href` hinzu.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

Dadurch wird das Microsoft Teams-Symbol zu Ihrer Website hinzugefügt.

![Symbol "Für Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

Wenn Sie für die Schaltfläche "In Teams freigeben" eine andere Symbolgröße wünschen, verwenden Sie optional das `data-icon-px-size` Attribut.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

Wenn Sie wissen, dass die URL-Vorschau von Ihrem Link, der freigegeben werden soll, in Teams nicht gut gerendert wird (z. B. wäre für den Link eine Benutzerauthentifizierung erforderlich), können Sie die URL-Vorschau deaktivieren, indem Sie das Attribut hinzufügen, das auf festgelegt `data-preview` `false` ist.

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

Wenn Ihre Seite Inhalte dynamisch rendert, können Sie die Methode verwenden, um zu erzwingen, dass die Schaltfläche "Freigeben" an der entsprechenden Stelle `shareToMicrosoftTeams.renderButtons()` in der Pipeline gerendert wird. 

## <a name="crafting-your-website-preview"></a>Erstellen der Websitevorschau

Wenn Ihre Website für Teams freigegeben ist, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website. Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website (der URL) die entsprechenden `data-href` Metadaten hinzugefügt werden. In der folgenden Tabelle sind die erforderlichen Tags aufgeführt. Sie können entweder die Html-Standardversionen oder die Open Graph-Version verwenden.

Damit die Vorschau angezeigt wird, müssen Sie:

* Schließen Sie entweder ein Miniaturbild oder einen Titel und eine Beschreibung ein (um optimale Ergebnisse zu erzielen, schließen Sie alle drei ein).
* Die freigegebene URL kann keine Authentifizierung erfordern. Wenn dies möglich ist, können Sie sie weiterhin freigeben, aber die Vorschau wird nicht erstellt.

|Wert|Metatag| Open Graph|
|----|----|----|
|Titel|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Beschreibung|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Miniaturansicht| n/v |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a>Freigeben für Teams für Bildungseinrichtungen

Für Lehrer, die die Schaltfläche "In Teams freigeben" verwenden, erhalten Sie eine zusätzliche Option für `Create an Assignment` . Auf diese Weise können Sie schnell eine Zuweisung im ausgewählten Team basierend auf dem freigegebenen Link erstellen.

![Popup "In Teams freigeben"](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Vollständige launcher.js Definition

| Eigenschaft | HTML-Attribut | Typ | Standard | Beschreibung |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | Zeichenfolge | n/v | Der Href des zu teilende Inhalts. |
| Vorschau | `data-preview` | boolean (als Zeichenfolge) | `true` | Gibt an, ob eine Vorschau des zu teilende Inhalts angezeigt werden soll. |
| iconPxSize | `data-icon-px-size` | Zahl (als Zeichenfolge) | `32` | Die Größe der zu rendernde Schaltfläche "Share-to-Teams" in Pixeln. |
| msgText | `data-msg-text` | Zeichenfolge | n/v | Standardtext, der vor dem Link in das Feld zum Verfassen von Nachrichten eingefügt werden soll (Grenzwert von 200 Zeichen) |
| assignInstr | `data-assign-instr` | Zeichenfolge | n/v | Standardtext, der in das Feld "Anweisungen" eingefügt werden soll (Grenzwert von 200 Zeichen) |
| assignTitle | `data-assign-title` | Zeichenfolge | n/v | Standardtext, der in das Zuordnungsfeld "Titel" eingefügt werden soll (Grenzwert von 50 Zeichen) |

### <a name="methods"></a>Methoden

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (optional): `{ elements?: HTMLElement[] }`

Rendert alle Freigabeschaltflächen, die sich derzeit auf der Seite befindet. Wenn ein optionales Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente `options` in Freigabeschaltflächen gerendert.

### <a name="setting-default-form-values"></a>Festlegen von Standardformularwerten

Optional können Sie standardwerte für die folgenden Felder im Formular "In Teams freigeben" festlegen:

* Etwas dazu sagen ( `msgText` )
* Zuweisungsanweisungen ( `assignInstr` )
* Zuweisungstitel ( `assignTitle` )

#### <a name="example-default-form-values"></a>Beispiel: Standardformularwerte

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
