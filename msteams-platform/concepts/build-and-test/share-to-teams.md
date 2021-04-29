---
title: Erstellen einer Schaltfläche zum Teilen in Microsoft Teams
description: Hinzufügen der eingebetteten Schaltfläche "Zu Teams freigeben" auf Ihrer Website
ms.topic: reference
localization_priority: Normal
keywords: Freigeben von Teams-Share-to-Teams
ms.openlocfilehash: d3e23c50cbaa38a53fa02c19cec69061478d9a57
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075647"
---
# <a name="create-share-to-teams-button"></a>Erstellen einer Schaltfläche zum Teilen in Microsoft Teams

Websites von Drittanbietern können das Startstartskript verwenden, um Share-to-Teams-Schaltflächen auf ihren Webseiten einzubetten. Wenn Sie diese Option auswählen, wird die Share-to-Teams-Erfahrung in einem Popupfenster gestartet. Auf diese Weise können Sie einen Link direkt mit jeder Person oder einem Microsoft Teams-Kanal teilen, ohne den Kontext zu wechseln. In diesem Dokument erfahren Sie, wie Sie eine Share-to-Teams-Schaltfläche für Ihre Website erstellen und einbetten, ihre Websitevorschau erstellen und Share-to-Teams for Education erweitern.

> [!NOTE]
> * Nur die Desktopversionen von Edge und Chrome werden unterstützt.
> * Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.  

In der folgenden Abbildung wird die Popuperfahrung "Share-to-Teams" angezeigt:

![Share-to-Teams-Popup](~/assets/images/share-to-teams-popup.png)

## <a name="embed-a-share-to-teams-button"></a>Einbetten einer Schaltfläche Für Teams freigeben

1. Fügen Sie `launcher.js` das Skript auf Ihrer Webseite hinzu.

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. Fügen Sie ein HTML-Element auf Ihrer Webseite mit dem Klassenattribut und dem Link hinzu, `teams-share-button` der im Attribut gemeinsam verwendet werden `data-href` soll.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    Nachdem Sie dies abgeschlossen haben, wird das Microsoft Teams-Symbol zu Ihrer Website hinzugefügt. Die folgende Abbildung zeigt das Share-to-Teams-Symbol:

    ![Symbol "Für Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

1. Wenn Sie eine andere Symbolgröße für die Schaltfläche Für Teams freigeben möchten, verwenden Sie alternativ das `data-icon-px-size` Attribut.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```
1. Wenn für den freigegebenen Link die Benutzerauthentifizierung erforderlich ist und die URL-Vorschau ihres links, der freigegeben werden soll, in Teams nicht gut gerendert wird, können Sie die URL-Vorschau deaktivieren, indem Sie das Attribut hinzufügen, das auf `data-preview` festgelegt `false` ist.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. Wenn Ihre Seite Inhalte dynamisch rendert, können Sie mit der -Methode erzwingen, dass die Schaltfläche Freigeben an der entsprechenden Stelle `shareToMicrosoftTeams.renderButtons()` in der Pipeline gerendert wird. 

## <a name="craft-your-website-preview"></a>Erstellen der Websitevorschau

Wenn Ihre Website für Teams freigegeben wird, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website. Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website die entsprechenden Metadaten hinzugefügt werden, z. B. die `data-href` URL.  

**So zeigen Sie die Vorschau an**

* Sie müssen entweder ein **Miniaturansichtsbild** oder einen **Titel und** eine **Beschreibung enthalten.** Um die besten Ergebnisse zu erzielen, schließen Sie alle drei ein.
* Die freigegebene URL erfordert keine Authentifizierung. Wenn die Authentifizierung erforderlich ist, können Sie sie freigeben, aber die Vorschau wird nicht erstellt.

In der folgenden Tabelle sind die erforderlichen Tags aufgeführt:

|Wert|Metatag| Öffnen von Graph|
|----|----|----|
|Titel|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Beschreibung|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Miniaturansicht| none. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Sie können entweder die Html-Standardversionen oder die Open Graph-Version verwenden.

## <a name="share-to-teams-for-education"></a>Freigeben für Teams for Education

Für Lehrkräfte, die die Schaltfläche Für Teams freigeben verwenden, gibt es eine zusätzliche Option zu `Create an Assignment` . Auf diese Weise können Sie schnell eine Zuordnung im ausgewählten Team basierend auf dem freigegebenen Link erstellen. Die folgende Abbildung zeigt Share-to-Teams für Bildungseinrichtungen: 

![Freigeben für Teams-Popup-Bildungseinrichtungen](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Vollständige launcher.js Definition

| Eigenschaft | HTML-Attribut | Typ | Standard | Beschreibung |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/v | Der Href des inhalts, der gemeinsam verwendet werden soll. |
| Vorschau | `data-preview` | boolean (als Zeichenfolge) | `true` | Gibt an, ob eine Vorschau des zu teilende Inhalts angezeigt werden soll. |
| iconPxSize | `data-icon-px-size` | Zahl (als Zeichenfolge) | `32` | Die Größe der zu rendernde Schaltfläche "Share-to-Teams" in Pixeln. |
| msgText | `data-msg-text` | string | n/v | Standardtext, der vor dem Link im Feld Zum Verfassen von Nachrichten eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200. |
| assignInstr | `data-assign-instr` | string | n/v | Standardtext, der in das Feld "Anweisungen" eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200. |
| assignTitle | `data-assign-title` | string | n/v | Standardtext, der in das Feld Zuordnungen "Titel" eingefügt werden soll. Die maximale Anzahl von Zeichen ist 50. |

### <a name="methods"></a>Methoden

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (optional): `{ elements?: HTMLElement[] }`

Derzeit werden alle Freigabeschaltflächen auf der Seite gerendert. Wenn ein optionales Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente `options` in Freigabeschaltflächen gerendert.

### <a name="set-default-form-values"></a>Festlegen von Standardformularwerten

Sie können die Standardwerte für die folgenden Felder im Formular Für Teams freigeben festlegen:

* Sagen Sie dazu etwas: `msgText`
* Zuweisungsanweisungen: `assignInstr`
* Zuordnungstitel: `assignTitle`

#### <a name="example"></a>Beispiel

 Standardformularwerte werden im folgenden Beispiel angegeben:

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```

## <a name="see-also"></a>Siehe auch

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
