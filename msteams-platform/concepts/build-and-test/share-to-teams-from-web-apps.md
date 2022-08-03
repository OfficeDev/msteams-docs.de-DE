---
title: Von Web-Apps für Teams freigeben
description: Informationen zum Hinzufügen der eingebetteten Schaltfläche "Zu Teams teilen" auf Ihrer Website mit einer Websitevorschau unter Verwendung von Codebeispielen
ms.topic: reference
ms.localizationpriority: medium
ms.openlocfilehash: 1d7b9b6ae80b224e67f24a589fae5e6af7e7f839
ms.sourcegitcommit: 990a36fb774e614146444d4adaa2c9bcdb835998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2022
ms.locfileid: "67232337"
---
# <a name="share-to-teams-from-web-apps"></a>Von Web-Apps für Teams freigeben

Websites von Drittanbietern können das Launcher-Skript verwenden, um Schaltflächen für die Weitergabe an Teams in ihre Webseiten einzubetten. Wenn Sie die Schaltfläche "In Teams teilen" auswählen, wird die Oberfläche "Für Teams freigeben" in einem Popupfenster gestartet. Auf diese Weise können Sie einen Link direkt mit einer beliebigen Person oder einem Microsoft Teams-Kanal teilen, ohne den Kontext zu wechseln.

In der folgenden Abbildung wird das Popupfenster für die Vorschauoberfläche "Für Teams freigeben" angezeigt:

:::image type="content" source="~/assets/images/share-to-teams-popup.png" alt-text="Share-to-Teams-Popup":::

> [!NOTE]
>
> * Nur die Desktopversionen von Microsoft&nbsp;Edge und Google Chrome werden unterstützt.
> * Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.

Sie können auch die Verbreitung von Links für die Links hinzufügen, die über die Schaltfläche "Für Teams freigeben" freigegeben wurden, die in der Web-App, persönlichen App oder Registerkarte gehostet werden. Weitere Informationen finden Sie unter ["Verbreitung von Links"](~/messaging-extensions/how-to/link-unfurling.md).

In der folgenden Abbildung wird die Oberfläche für die Verbreitung von Links über die Schaltfläche "Für Teams freigeben" angezeigt:

:::image type="content" source="~/assets/images/share-to-teams-link-unfurling.png" alt-text="Verbreitung von Share-to-Teams-Links":::

In diesem Artikel erfahren Sie, wie Sie eine Schaltfläche "In Teams teilen" für Ihre Website erstellen und einbetten, ihre Websitevorschau erstellen und auf Teams für Education erweitern.

Im folgenden Video erfahren Sie, wie Sie die Schaltfläche "In Teams teilen" einbetten:
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4vhWH]
<br>

## <a name="embed-a-share-to-teams-button"></a>Einbetten einer Schaltfläche "In Teams teilen"

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

    Nach Abschluss dieses Vorgangs wird das Teams-Symbol zu Ihrer Website hinzugefügt. Die folgende Abbildung zeigt das Symbol "Für Teams freigeben":

    :::image type="content" source="~/assets/icons/share-to-teams-icon.png" alt-text="Symbol &quot;Für Teams freigeben&quot;":::

1. Wenn Sie eine andere Symbolgröße für die Schaltfläche "Für Teams freigeben" wünschen, verwenden Sie alternativ das `data-icon-px-size` Attribut.

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

|Wert|Metatag| Open Graph|
|----|----|----|
|Titel|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|Beschreibung|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|Miniaturansicht| nichts. |`<meta property="og:image" content="http://example.com/image.jpg">`|

Sie können entweder die HTML-Standardversionen oder die Open Graph-Version verwenden.

## <a name="share-to-teams-for-education"></a>Für Teams für Education freigeben

Für Lehrer, die die Schaltfläche "In Teams teilen" verwenden, gibt es eine zusätzliche Option `Create an Assignment` , mit der Sie schnell eine Aufgabe im ausgewählten Team basierend auf dem freigegebenen Link erstellen können. Die folgende Abbildung zeigt "In Teams für Bildungseinrichtungen freigeben":

:::image type="content" source="../../assets/images/share-to-teams-popup-edu.png" alt-text="Freigeben für Teams-Popupschulungen":::

## <a name="full-launcherjs-definition"></a>Vollständige launcher.js Definition

| Eigenschaft | HTML-Attribut | Typ | Standard | Beschreibung |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| href | `data-href` | string | n/v | Der Href des freizugebenden Inhalts. |
| Vorschau | `data-preview` | Boolescher Wert (als Zeichenfolge) | `true` | Gibt an, ob eine Vorschau des freizugebenden Inhalts angezeigt werden soll. |
| iconPxSize | `data-icon-px-size` | Zahl (als Zeichenfolge) | `32` | Die Größe in Pixeln der Schaltfläche "In Teams teilen", die gerendert werden soll. |
| msgText | `data-msg-text` | string | n/v | Standardtext, der vor dem Link im Feld zum Verfassen von Nachrichten eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200 Zeichen. |
| assignInstr | `data-assign-instr` | string | n/v | Standardtext, der in das Feld "Anweisungen" eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 200 Zeichen. |
| assignTitle | `data-assign-title` | string | n/v | Standardtext, der in das Feld "Titel" für Zuordnungen eingefügt werden soll. Die maximale Anzahl von Zeichen beträgt 50 Zeichen. |

### <a name="methods"></a>Methoden

**`shareToMicrosoftTeams.renderButtons(options)`**

`options` (optional): `{ elements?: HTMLElement[] }`

Derzeit werden alle Freigabeschaltflächen auf der Seite gerendert. Wenn ein optionales `options` Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente in Freigabeschaltflächen gerendert.

### <a name="set-default-form-values"></a>Festlegen von Standardformularwerten

Sie können die Standardwerte für die folgenden Felder im Formular "Für Teams freigeben" festlegen:

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
