---
title: Erstellen einer Schaltfläche zum Teilen in Microsoft Teams
description: So fügen Sie die Freigabe zu Teams eingebetteten Schaltfläche auf Ihrer Website hinzu
ms.topic: reference
localization_priority: Normal
keywords: Freigeben von Teams Share-to-Teams
ms.openlocfilehash: 4bbf29bb355726b519975bec5d6fad3419b81ce3
ms.sourcegitcommit: 09067fb9886323f144384254c41e93469c433382
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2021
ms.locfileid: "58358622"
---
# <a name="create-share-to-teams-button"></a>Erstellen einer Schaltfläche zum Teilen in Microsoft Teams

Websites von Drittanbietern können das Startprogrammskript verwenden, um Share-to-Teams-Schaltflächen auf ihren Webseiten einzubetten. Wenn Sie diese Option auswählen, wird die Share-to-Teams-Oberfläche in einem Popupfenster gestartet. Auf diese Weise können Sie einen Link direkt für jede Person oder Microsoft Teams Kanal freigeben, ohne den Kontext zu wechseln. In diesem Dokument erfahren Sie, wie Sie eine Schaltfläche für Teams freigeben für Ihre Website erstellen und einbetten, Eine Websitevorschau erstellen und share-to-Teams für Education erweitern.

> [!NOTE]
> * Nur die Desktopversionen von Edge und Chrome werden unterstützt.
> * Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.  

In der folgenden Abbildung wird die Popupoberfläche "Share-to-Teams" angezeigt:

![Share-to-Teams-Popup](~/assets/images/share-to-teams-popup.png)

## <a name="embed-a-share-to-teams-button"></a>Schaltfläche zum Einbetten einer Freigabe in Teams

1. Fügen Sie das `launcher.js` Skript auf Ihrer Webseite hinzu.

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. Fügen Sie ein HTML-Element auf Ihrer Webseite mit dem `teams-share-button` Klassenattribut und dem Link hinzu, der im Attribut freigegeben werden `data-href` soll.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    Nach Abschluss dieses Vorgangs wird das symbol Microsoft Teams ihrer Website hinzugefügt. Die folgende Abbildung zeigt das Symbol "Freigeben für Teams":

    ![Symbol "Für Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

1. Wenn Sie eine andere Symbolgröße für die Schaltfläche "Freigeben bis Teams" wünschen, verwenden Sie alternativ das `data-icon-px-size` Attribut.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```
1. Wenn der freigegebene Link eine Benutzerauthentifizierung erfordert und die URL-Vorschau ihres Links, der freigegeben werden soll, in Teams nicht gut gerendert wird, können Sie die URL-Vorschau deaktivieren, indem Sie das Attribut hinzufügen, `data-preview` das auf festgelegt `false` ist.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. Wenn Ihre Seite Inhalte dynamisch rendert, können Sie mit der `shareToMicrosoftTeams.renderButtons()` Methode erzwingen, dass **Share** an der entsprechenden Stelle in der Pipeline gerendert wird.

## <a name="craft-your-website-preview"></a>Erstellen der Websitevorschau

Wenn Ihre Website für Teams freigegeben wird, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website. Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website die entsprechenden Metadaten hinzugefügt werden, `data-href` z. B. die URL.  

**So zeigen Sie die Vorschau an**

* Sie müssen entweder ein **Miniaturbild** oder einen **Titel** und eine **Beschreibung** einschließen. Um optimale Ergebnisse zu erzielen, schließen Sie alle drei ein.
* Die freigegebene URL erfordert keine Authentifizierung. Wenn eine Authentifizierung erforderlich ist, können Sie sie freigeben, aber die Vorschau wird nicht erstellt.

In der folgenden Tabelle werden die erforderlichen Tags beschrieben:

|Wert|Metatag| Öffnen Graph|
|----|----|----|
|Titel|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Beschreibung|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Miniaturansicht| nichts. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Sie können entweder die HTML-Standardversionen oder die Open Graph-Version verwenden.

## <a name="share-to-teams-for-education"></a>Freigeben für Teams für Education

Für Lehrer, die die Schaltfläche "Freigeben" zum Teams verwenden, gibt es eine zusätzliche Option für `Create an Assignment` . Auf diese Weise können Sie basierend auf dem freigegebenen Link schnell eine Aufgabe im ausgewählten Team erstellen. Die folgende Abbildung zeigt Share-to-Teams für Bildungseinrichtungen: 

![Freigeben für Teams Popup-Bildungseinrichtungen](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a>Vollständige launcher.js Definition

| Eigenschaft | HTML-Attribut | Typ | Standard | Beschreibung |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/v | Das Href des freizugebenden Inhalts. |
| Vorschau | `data-preview` | Boolescher Wert (als Zeichenfolge) | `true` | Gibt an, ob eine Vorschau des freizugebenden Inhalts angezeigt werden soll. |
| iconPxSize | `data-icon-px-size` | Zahl (als Zeichenfolge) | `32` | Die Größe der zu rendernden Schaltfläche "Share-to-Teams" in Pixeln. |
| msgText | `data-msg-text` | string | n/v | Standardtext, der vor dem Link in das Feld zum Verfassen von Nachrichten eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200 Zeichen. |
| assignInstr | `data-assign-instr` | string | n/v | Standardtext, der in das Zuordnungsfeld Anweisungen eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200 Zeichen. |
| assignTitle | `data-assign-title` | string | n/v | Standardtext, der in das Zuordnungsfeld Titel eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 50 Zeichen. |

### <a name="methods"></a>Methoden

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (optional): `{ elements?: HTMLElement[] }`

Derzeit werden alle Freigabeschaltflächen auf der Seite gerendert. Wenn ein optionales `options` Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente in Freigabeschaltflächen gerendert.

### <a name="set-default-form-values"></a>Festlegen von Standardformularwerten

Sie können die Standardwerte für die folgenden Felder im Formular "Freigeben" auf Teams festlegen:

* Sagen Sie dazu etwas: `msgText`
* Zuweisungsanweisungen: `assignInstr`
* Zuweisungstitel: `assignTitle`

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
