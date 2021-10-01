---
title: Aufgeklappte Registerkartenverknüpfung und Phasenansicht
author: Rajeshwari-v
description: Wie Sie einen Link öffnen, die Phasenansicht öffnen und eine Registerkarte mit Microsoft Teams App anheften.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: cc77667a8782f2f519d6dc3e6af74949a9dcbed2
ms.sourcegitcommit: 329447310013a2672216793dab79145b24ef2cd2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2021
ms.locfileid: "60017303"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Aufgeklappte Registerkartenverknüpfung und Phasenansicht

> [!NOTE]
> Dieses Feature ist nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die Phasenansicht ist eine neue Benutzeroberflächenkomponente, mit der Sie den Inhalt rendern können, der im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet ist.
 
> [!NOTE]
> Derzeit unterstützen Teams mobile Clients das Aufheben von Registerkartenlinks und die Phasenansicht nicht. Mobile Clients verwenden das `websiteUrl` vom Entwickler bereitgestellte Attribut, um die Seite im Webbrowser des Geräts zu öffnen.

## <a name="stage-view"></a>Phasenansicht

Die Phasenansicht ist eine Vollbild-UI-Komponente, die Sie aufrufen können, um Ihre Webinhalte anzuzeigen. Der vorhandene Link-Verbreitungsdienst wird so aktualisiert, dass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte umzuwandeln. Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird die URL auf eine adaptive Karte entrollt. Der Benutzer kann auf der Karte **"Anzeigen"** auswählen und den Inhalt direkt in der Phasenansicht als Registerkarte anheften.

## <a name="advantage-of-stage-view"></a>Vorteile der Phasenansicht

Die Phasenansicht bietet eine nahtlosere Erfahrung beim Anzeigen von Inhalten in Teams. Benutzer können die von Ihrer App bereitgestellten Inhalte öffnen und anzeigen, ohne den Kontext zu verlassen, und sie können den Inhalt für zukünftigen Schnellzugriff an den Chat oder Kanal anheften. Dies führt zu einer höheren Benutzerbindung für Ihre App.

## <a name="stage-view-vs-task-module"></a>Phasenansicht im Vergleich zum Aufgabenmodul

|Phasenansicht|Aufgabenmodul|
|:-----------|:-----------|
|Die Phasenansicht ist hilfreich, wenn Sie benutzern umfangreiche Inhalte anzeigen können, z. B. eine Seite, ein Dashboard, eine Datei usw. Es bietet umfangreiche Features, mit denen Sie Ihre Inhalte im Vollbildbereich rendern können.|[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzuzeigen, die Die Aufmerksamkeit des Benutzers erfordern, oder um Informationen zu sammeln, die zum Nächsten Schritt erforderlich sind.|
  
## <a name="invoke-stage-view"></a>Aufrufen der Phasenansicht

Sie können die Phasenansicht auf folgende Weise aufrufen:

* [Aufrufen der Phasenansicht von einer adaptiven Karte](#invoke-stage-view-from-adaptive-card)
* [Aufrufen der Phasenansicht über deep-Link](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Aufrufen der Phasenansicht von einer adaptiven Karte

Wenn der Benutzer eine URL auf dem Teams Desktopclient eingibt, wird der Bot aufgerufen und gibt eine [adaptive Karte](../task-modules-and-cards/cards/cards-actions.md) mit der Option zum Öffnen der URL in einer Phase zurück. Nachdem eine Phase gestartet und `tabInfo` bereitgestellt wurde, können Sie die Phase als Registerkarte anheften.  

Die folgenden Bilder zeigen eine Phase, die von einer adaptiven Karte geöffnet wurde:

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card1.png" alt="Open a stage from Adaptive Card" width="700"/>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card2.png" alt="Open a stage" width="700"/>

### <a name="example"></a>Beispiel

Es folgt der Code zum Öffnen einer Phase von einer adaptiven Karte aus:

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

Der `invoke` Anforderungstyp muss `composeExtension/queryLink` .

> [!NOTE]
> * `invoke` workflow is similar to the current `appLinking` workflow. 
> * Um die Konsistenz zu gewährleisten, wird empfohlen, den Namen `Action.Submit` `View` ".
> * `websiteUrl` ist eine erforderliche Eigenschaft, die im Objekt übergeben werden `TabInfo` muss.

Nachfolgend sehen Sie den Prozess zum Aufrufen der Phasenansicht:

* Wenn der Benutzer **"Anzeigen"** auswählt, erhält der Bot eine `invoke` Anforderung. Der Anforderungstyp lautet `composeExtension/queryLink` .
* `invoke` antwort von Bot enthält eine adaptive Karte mit Typ `tab/tabInfoAction` darin.
* Der Bot antwortet mit einem `200` Code.

> [!NOTE]
> Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht. Wenn ein Benutzer auf einem mobilen Client **"Anzeigen"** auswählt, wird der Benutzer zum Browser des Geräts weitergeleitet. Der Browser öffnet die im Parameter des Objekts angegebene `websiteUrl` `TabInfo` URL.

## <a name="invoke-stage-view-through-deep-link"></a>Aufrufen der Phasenansicht über deep-Link

Um die Phasenansicht über den Deep-Link von Ihrer Registerkarte aus aufzurufen, müssen Sie die DEEP-Link-URL in der `microsoftTeams.executeDeeplink(url)` API umschließen. Der Deep-Link kann auch über eine Aktion auf der Karte übergeben `OpenURL` werden.

In der folgenden Abbildung wird eine Phasenansicht angezeigt, die über einen Deep-Link aufgerufen wird:

<img src="~/assets/images/tab-images/invoke-stage-view-through-deep-link.png" alt="Invoke a Stage View through a deep link" width="400"/>

### <a name="syntax"></a>Syntax

Es folgt die Deeplinksyntax: 

https://teams.microsoft.com/l/stage/{appId}/0?context={\"contentUrl \" : \" "[contentUrl]" \" , \" websiteUrl \" : \" "[websiteUrl]" \" , name : Contoso \" \" \" \" }
 
### <a name="examples"></a>Beispiele

Wenn ein Benutzer eine URL eingibt, wird diese in eine adaptive Karte entrollt.

Nachfolgend sind die Deep-Linkbeispiele zum Aufrufen der Phasenansicht aufgeführt:

**Beispiel 1**

https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}

**Beispiel 2**

https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}

> [!NOTE]
> * Dies `name` ist optional im Deep-Link. Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt.
> * Der Deep-Link kann auch über eine Aktion übergeben `OpenURL` werden.
> * Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht. Wenn Benutzer einen Deep-Link zu einer Phasenansicht auswählen, werden sie zum Webbrowser ihres Geräts geleitet. Der Webbrowser öffnet die URL, die im `websiteUrl` Parameter des Deep-Links angegeben ist.
> * Wenn Sie eine Phase aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert. Wenn Ihre Phasenansicht beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App einen persönlichen Bereich aufweist.

## <a name="tab-information-property"></a>Tabinformationseigenschaft

| Eigenschaftenname | Typ | Anzahl der Zeichen | Beschreibung |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | String | 64 | Diese Eigenschaft ist ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird. Dies ist ein Pflichtfeld.|
| `name` | String | 128 | Diese Eigenschaft ist der Anzeigename der Registerkarte in der Kanalschnittstelle. Dieses Feld ist optional.|
| `contentUrl` | String | 2048 | Diese Eigenschaft ist die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams Canvas angezeigt werden soll. Dies ist ein Pflichtfeld.|
| `websiteUrl?` | String | 2048 | Diese Eigenschaft ist die https:// URL, auf die sie zeigen soll, wenn ein Benutzer die Anzeige in einem Browser auswählt. Dies ist ein Pflichtfeld.|
| `removeUrl?` | String | 2048 | Diese Eigenschaft ist die https:// URL, die auf die Benutzeroberfläche zeigt, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.|

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Registerkarte in der Phasenansicht |Microsoft Teams Registerkartenbeispiel-App zum Demonstrieren der Registerkarte in der Phasenansicht.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|
    

## <a name="see-also"></a>Siehe auch

* [Verbreitung von Messaging-Erweiterungen](~/messaging-extensions/how-to/link-unfurling.md)
* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)
