---
title: Von Web-Apps für Teams freigeben
description: Erfahren Sie, wie Sie die Schaltfläche "Freigeben" zu Teams eingebetteten Schaltfläche auf Ihrer Website mit einer Websitevorschau hinzufügen, indem Sie Codebeispiele verwenden.
ms.topic: reference
ms.localizationpriority: medium
keywords: Freigeben Teams Freigeben für Teams
ms.openlocfilehash: b3efd268e2bded3955c2d9ab76d6dea755d06b5a
ms.sourcegitcommit: a3567e3e1a52b8e3cb2072b037f0e75bd0f12e58
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2022
ms.locfileid: "65439300"
---
# <a name="share-to-teams-from-web-apps"></a>Von Web-Apps für Teams freigeben

Websites von Drittanbietern können das Startprogrammskript verwenden, um "Freigeben" in Teams Schaltflächen auf ihren Webseiten einzubetten. Wenn Sie diese Option auswählen, wird die Freigabe gestartet, um Teams Oberfläche in einem Popupfenster anzuzeigen. Auf diese Weise können Sie einen Link direkt für eine beliebige Person oder Microsoft Teams Kanal freigeben, ohne den Kontext zu wechseln. In diesem Dokument erfahren Sie, wie Sie eine Schaltfläche "Freigeben" erstellen und in Teams für Ihre Website einbetten, ihre Websitevorschau erstellen und "Freigeben" auf Teams für Education erweitern.

> [!NOTE]
>
> * Nur die Desktopversionen von MicrosoftEdge&nbsp; und Google Chrome werden unterstützt.
> * Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.  

In der folgenden Abbildung wird die Popupoberfläche "Freigeben für Teams" angezeigt:

:::image type="content" source="../../assets/images/share-to-teams-popup.png" alt-text="Popupmenü &quot;Für Teams freigeben&quot;":::

## <a name="embed-a-share-to-teams-button"></a>Einbetten einer Freigabe in Teams Schaltfläche

1. Fügen Sie das `launcher.js` Skript auf Ihrer Webseite hinzu.

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. Fügen Sie auf Ihrer Webseite ein HTML-Element mit dem `teams-share-button` Klassenattribut und dem Link zum Freigeben im `data-href` Attribut hinzu.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    Nach Abschluss dieses Vorgangs wird das symbol für Microsoft Teams ihrer Website hinzugefügt. Die folgende Abbildung zeigt das Symbol "Für Teams freigeben":

    ![Symbol "Für Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

1. Wenn Sie für die Schaltfläche "Freigeben zu Teams" eine andere Symbolgröße wünschen, verwenden Sie das `data-icon-px-size` Attribut.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```

1. Wenn für den freigegebenen Link eine Benutzerauthentifizierung erforderlich ist und die URL-Vorschau ihres zu teilenden Links in Teams nicht gut gerendert wird, können Sie die URL-Vorschau deaktivieren, indem Sie das `data-preview` auf `false`festgelegte Attribut hinzufügen.

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. Um eine Nachricht Ihrer Wahl im Feld zum Verfassen anzuzeigen, können Sie Ihren Text im `data-msg-text` Attribut definieren.

     ```html
     <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-msg-text="<default-message-to-be-populated-in-compose-box>"
      data-preview="false">
      </div>
     ```

1. Wenn Ihre Seite Inhalte dynamisch rendert, können Sie mithilfe der `shareToMicrosoftTeams.renderButtons()` Methode erzwingen, dass **"Freigeben** " an der entsprechenden Stelle in der Pipeline gerendert wird.

## <a name="craft-your-website-preview"></a>Erstellen der Websitevorschau

Wenn Ihre Website für Teams freigegeben wird, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website. Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website die entsprechenden Metadaten hinzugefügt werden, z. B. die `data-href` URL.  

So zeigen Sie die Vorschau an:

* Sie müssen entweder ein **Miniaturbild** oder einen **Titel** und eine **Beschreibung** einschließen. Um optimale Ergebnisse zu erzielen, schließen Sie alle drei ein.
* Die freigegebene URL erfordert keine Authentifizierung. Wenn eine Authentifizierung erforderlich ist, können Sie sie freigeben, aber die Vorschau wird nicht erstellt.

In der folgenden Tabelle sind die erforderlichen Tags aufgeführt:

|Wert|Metatag| öffnen Graph|
|----|----|----|
|Titel|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Beschreibung|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Miniaturansicht| nichts. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Sie können entweder die HTML-Standardversionen oder die Open Graph-Version verwenden.

## <a name="share-to-teams-for-education"></a>Für Teams für Education freigeben

Für Lehrer, die die Schaltfläche "Freigeben zum Teams" verwenden, gibt es eine zusätzliche Option für `Create an Assignment`. Auf diese Weise können Sie schnell eine Aufgabe im ausgewählten Team basierend auf dem freigegebenen Link erstellen. In der folgenden Abbildung wird "Freigeben für Teams für Bildungseinrichtungen" angezeigt:

:::image type="content" source="../../assets/images/share-to-teams-popup-edu.png" alt-text="Für Teams Popupschulung freigeben":::

## <a name="full-launcherjs-definition"></a>Vollständige launcher.js Definition

| Eigenschaft | HTML-Attribut | Typ | Standard | Beschreibung |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/v | Der Href des freizugebenden Inhalts. |
| Vorschau | `data-preview` | Boolescher Wert (als Zeichenfolge) | `true` | Gibt an, ob eine Vorschau des freizugebenden Inhalts angezeigt werden soll. |
| iconPxSize | `data-icon-px-size` | Zahl (als Zeichenfolge) | `32` | Die Größe der zu Teams Schaltfläche "Freigeben" in Pixeln, die gerendert werden soll. |
| msgText | `data-msg-text` | string | n/v | Standardtext, der vor dem Link im Feld zum Verfassen von Nachrichten eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200 Zeichen. |
| assignInstr | `data-assign-instr` | string | n/v | Standardtext, der in das Feld "Anweisungen" eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200 Zeichen. |
| assignTitle | `data-assign-title` | string | n/v | Standardtext, der in das Feld "Titel" für Zuordnungen eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 50 Zeichen. |

### <a name="methods"></a>Methoden

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (optional): `{ elements?: HTMLElement[] }`

Derzeit werden alle Freigabeschaltflächen auf der Seite gerendert. Wenn ein optionales `options` Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente in Freigabeschaltflächen gerendert.

### <a name="set-default-form-values"></a>Festlegen von Standardformularwerten

Sie können festlegen, dass Standardwerte für die folgenden Felder im Formular "Freigeben" auf Teams festgelegt werden:

* Sagen Sie etwas dazu: `msgText`
* Aufgabenanweisungen: `assignInstr`
* Zuordnungstitel: `assignTitle`

#### <a name="example"></a>Beispiel

 Im folgenden Beispiel werden Standardformularwerte angegeben:

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

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Für Teams über persönliche App oder Registerkarte freigeben](share-to-teams-from-personal-app-or-tab.md)
