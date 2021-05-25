---
title: Tabs link unfurling and Stage View
author: Rajeshwari-v
description: So öffnen Sie einen Link, öffnen Sie die Stage View, und anheften Sie eine Registerkarte mit Microsoft Teams App.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 7dfabfa58c49237e776af37a1ee40d707783d0dc
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631279"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Tabs link unfurling and Stage View

> [!NOTE]
> Dieses Feature ist nur in [der öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die Stage View ist eine neue Benutzeroberflächenkomponente, mit der Sie inhalte rendern können, die im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet werden.
 
> [!NOTE]
> Derzeit unterstützen Teams mobile Clients keine Registerkartenlinks zum Entffurling und zur Stage View. Mobile Clients verwenden das vom Entwickler bereitgestellte Attribut, um die Seite im Webbrowser des `websiteUrl` Geräts zu öffnen.

## <a name="stage-view"></a>Stage View

Die Stage View ist eine Vollbild-UI-Komponente, die Sie aufrufen können, um Ihre Webinhalte anzuzeigen. Der vorhandene Link-Entf?ndungsdienst wird so aktualisiert, dass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte zu verwandeln. Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird die URL auf eine adaptive Karte entsperrt. Der Benutzer kann **auf** der Karte Ansicht auswählen und den Inhalt direkt aus der Stage View als Registerkarte anheften.

## <a name="advantage-of-stage-view"></a>Vorteile der Stage View

Die Stage View bietet eine nahtlose Darstellung von Inhalten in Teams. Benutzer können die von Ihrer App bereitgestellten Inhalte öffnen und anzeigen, ohne den Kontext zu verlassen, und sie können die Inhalte an den Chat oder Kanal anheften, um künftig schnell darauf zugreifen zu können. Dies führt zu einer höheren Benutzerbindung mit Ihrer App.

##  <a name="stage-view-vs-task-module"></a>Stage View vs. Task Module

|Stage View|Aufgabenmodul|
|:-----------|:-----------|
|Die Stage View ist hilfreich, wenn Sie den Benutzern einen reichhaltigen Inhalt anzeigen können, z. B. eine Seite, ein Dashboard, eine Datei und so weiter. Es bietet maximale Immobilie, die hilft, Ihre Inhalte im Vollbildbereich zu rendern.|[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzeigen zu können, die die Aufmerksamkeit des Benutzers erfordern, oder informationen zu sammeln, die zum Nächsten Schritt erforderlich sind.|
  
## <a name="invoke-the-stage-view"></a>Aufrufen der Stage View

Sie können die Stage View auf folgende Weise aufrufen: 

* [Aufrufen der Stage View von adaptiver Karte](#invoke-stage-view-from-adaptive-card)
* [Aufrufen der Stage View über einen tiefen Link](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Aufrufen der Stage View von adaptiver Karte

Wenn der Benutzer eine URL auf dem Teams-Desktopclient eingibt, wird der Bot aufgerufen und gibt eine [adaptive](../task-modules-and-cards/cards/cards-actions.md) Karte mit der Option zurück, die URL in einer Phase zu öffnen. Nachdem eine Phase gestartet und die übergeben wurde, können Sie die Möglichkeit hinzufügen, die Phase als `tabInfo` Registerkarte anheften.  

In den folgenden Bildern wird eine Phase angezeigt, die von einer adaptiven Karte geöffnet wurde:

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card1.png" alt="Open a stage from Adaptive Card" width="400"/>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card2.png" alt="Open a stage" width="400"/>

### <a name="example"></a>Beispiel 

Im Folgenden finden Sie den Code zum Öffnen einer Phase über eine adaptive Karte:

```json
{
    type: "Action.Submit",
    name: "View",
    data: {
          msteams: {
            type: "invoke",
            value: {
                type: "tab/tabInfoAction",
                tabInfo: {
                    contentUrl: contentUrl,
                    websiteUrl: websiteUrl,
                    name: "Tasks",
                    entityId: "entityId"
                 }
                }
            }
        }
} 
```

Der `invoke` Anforderungstyp muss `composeExtension/queryLink` sein. 

> [!NOTE]
> * `invoke` workflow ähnelt dem aktuellen `appLinking` Workflow. 
> * Um konsistenzkonsistent zu bleiben, wird empfohlen, die als `Action.Submit` zu `View` benennen.
> * `websiteUrl` ist eine erforderliche Eigenschaft, die im Objekt übergeben `TabInfo` werden muss.

**Prozess zum Aufrufen der Stage View**

1. Wenn der Benutzer Ansicht **auswählt,** empfängt der Bot eine `invoke` Anforderung. Der Anforderungstyp ist `composeExtension/queryLink` .
1. `invoke` Antwort vom Bot enthält eine adaptive Karte mit `tab/tabInfoAction` typ.
1. Der Bot antwortet mit einem `200` Code.

> [!NOTE]
> Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht. Wenn ein Benutzer **ansicht** auf einem mobilen Client auswählt, wird der Benutzer zum Browser des Geräts übernommen. Der Browser öffnet die im Parameter des `websiteUrl` Objekts angegebene `TabInfo` URL.

## <a name="invoke-stage-view-through-deep-link"></a>Aufrufen der Stage View über einen tiefen Link

Zum Aufrufen der Stage View über einen tiefen Link von Ihrer Registerkarte müssen Sie die Deep Link-URL in der `microsoftTeams.executeDeeplink(url)` API umschließen. Der Deeplink kann auch über eine Aktion `OpenURL` auf der Karte übergeben werden.

In der folgenden Abbildung wird eine Stage View angezeigt, die über einen tiefen Link aufgerufen wird:

<img src="~/assets/images/tab-images/invoke-stage-view-through-deep-link.png" alt="Invoke a Stage View through a deep link" width="400"/>

### <a name="syntax"></a>Syntax 

Im Folgenden finden Sie die Deeplinksyntax:  
 
https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"[contentUrl]","websiteUrl":"[websiteUrl]","name":"[name]"}

### <a name="examples"></a>Beispiele

Wenn ein Benutzer eine URL eintritt, wird sie in einer adaptiven Karte entsperrt.
Im Folgenden finden Sie die Deep Link-Beispiele zum Aufrufen der Stage View:

**Beispiel 1**

https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}

**Beispiel 2**

https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}

> [!NOTE]
> * Das `name` ist optional in deep link. Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt. 
> * Der Deep Link kann auch über eine Aktion übergeben `OpenURL` werden.
> * Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht. Wenn Benutzer einen tiefen Link zu einer Stage View auswählen, werden sie zum Webbrowser ihres Geräts übernommen. Der Webbrowser öffnet die im Parameter des Deep-Links angegebene `websiteUrl` URL.
> * Wenn Sie eine Phase aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert. Wenn Ihre Stage View beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App einen persönlichen Bereich hat.

## <a name="tab-information-property"></a>Tabinformationseigenschaft

| Eigenschaftenname | Typ | Anzahl der Zeichen | Beschreibung |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | String | 64 | Diese Eigenschaft ist ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird. Dies ist ein Pflichtfeld.|
| `name` | String | 128 | Diese Eigenschaft ist der Anzeigename der Registerkarte in der Kanalschnittstelle. Dieses Feld ist optional.|
| `contentUrl` | String | 2048 | Diese Eigenschaft ist die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll. Dies ist ein Pflichtfeld.|
| `websiteUrl?` | String | 2048 | Diese Eigenschaft ist die https:// URL, auf die verweisen soll, wenn ein Benutzer die Ansicht in einem Browser auswählt. Dies ist ein Pflichtfeld.|
| `removeUrl?` | String | 2048 | Diese Eigenschaft ist die https://-URL, die auf die Benutzeroberfläche verweist, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.|

## <a name="see-also"></a>Sehen Sie ebenfalls

[Verknüpfung mit Messagingerweiterungen wird entf?ndt](~/messaging-extensions/how-to/link-unfurling.md)


