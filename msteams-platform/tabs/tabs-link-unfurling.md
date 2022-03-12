---
title: Aufgeklappte Registerkartenverknüpfung und Phasenansicht
author: Rajeshwari-v
description: Erfahren Sie, wie Sie einen Link freigeben, die Phasenansicht öffnen und eine Registerkarte mit Microsoft Teams App anheften. Erfahren Sie mehr über die Phasenansicht und deren Aufruf mithilfe einer adaptiven Karte mithilfe von Codebeispielen und Beispielen.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: 1608f6e24ef4fbd3c979dcb7081c754d3b7cc30f
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453845"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Aufgeklappte Registerkartenverknüpfung und Phasenansicht

Die Phasenansicht ist eine neue Benutzeroberflächenkomponente, mit der Sie den Inhalt rendern können, der im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet wird.

## <a name="stage-view"></a>Phasenansicht

Die Phasenansicht ist eine Vollbild-UI-Komponente, die Sie aufrufen können, um Ihre Webinhalte anzuzeigen. Der vorhandene Link-Verbreitungsdienst wird so aktualisiert, dass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte umzuwandeln. Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird die URL auf eine adaptive Karte entrollt. Der Benutzer kann auf der Karte " **Anzeigen** " auswählen und den Inhalt direkt in der Phasenansicht als Registerkarte anheften.

## <a name="advantage-of-stage-view"></a>Vorteile der Phasenansicht

Die Phasenansicht bietet eine nahtlosere Erfahrung beim Anzeigen von Inhalten in Teams. Benutzer können die von Ihrer App bereitgestellten Inhalte öffnen und anzeigen, ohne den Kontext zu verlassen, und sie können die Inhalte an den Chat oder Kanal anheften, um später schnell auf Ihre App zugreifen zu können, was zu einer größeren Benutzerbindung führt.

## <a name="stage-view-vs-task-module"></a>Phasenansicht im Vergleich zum Aufgabenmodul

|Phasenansicht|Aufgabenmodul|
|:-----------|:-----------|
|Die Phasenansicht ist hilfreich, wenn Sie benutzern umfangreiche Inhalte anzeigen können, z. B. eine Seite, ein Dashboard, eine Datei usw. Es bietet umfangreiche Features, mit denen Sie Ihre Inhalte im Vollbildbereich rendern können.|[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzuzeigen, die Die Aufmerksamkeit des Benutzers erfordern, oder um Informationen zu sammeln, die zum Nächsten Schritt erforderlich sind.|
  
## <a name="invoke-stage-view"></a>Aufrufen der Phasenansicht

Sie können die Phasenansicht auf folgende Weise aufrufen:

* [Aufrufen der Phasenansicht von einer adaptiven Karte](#invoke-stage-view-from-adaptive-card)
* [Aufrufen der Phasenansicht über deep-Link](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Aufrufen der Phasenansicht von einer adaptiven Karte

Wenn der Benutzer eine URL auf dem Teams Desktopclient eingibt, wird der Bot aufgerufen und gibt eine [adaptive Karte](../task-modules-and-cards/cards/cards-actions.md) mit der Option zum Öffnen der URL in einer Phase zurück. Nachdem eine Phase gestartet und bereitgestellt `tabInfo` wurde, können Sie die Phase als Registerkarte anheften.  

Die folgenden Bilder zeigen eine Phase, die von einer adaptiven Karte geöffnet wurde:

[![Öffnen einer Phase über eine adaptive Karte](~/assets/images/tab-images/open-stage-from-adaptive-card1.png)](~/assets/images/tab-images/open-stage-from-adaptive-card1.png#lightbox)

[![Öffnen einer Phase](~/assets/images/tab-images/open-stage-from-adaptive-card2.png)](~/assets/images/tab-images/open-stage-from-adaptive-card2.png#lightbox)

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

Der Anforderungstyp `invoke` muss .`composeExtension/queryLink`

> [!NOTE]
>
> * `invoke` workflow is similar to the current `appLinking` workflow.
> * Um die Konsistenz zu gewährleisten, wird empfohlen, den Namen `Action.Submit` " `View`.
> * `websiteUrl` ist eine erforderliche Eigenschaft, die `TabInfo` im Objekt übergeben werden muss.

Nachfolgend sehen Sie den Prozess zum Aufrufen der Phasenansicht:

* Wenn der Benutzer **"Anzeigen**" auswählt, erhält der Bot eine `invoke` Anforderung. Der Anforderungstyp lautet `composeExtension/queryLink`.
* `invoke` antwort von Bot enthält eine adaptive Karte mit Typ `tab/tabInfoAction` darin.
* Der Bot antwortet mit einem `200` Code.

> [!NOTE]
> Auf Teams mobilen Clients öffnet das Aufrufen der Phasenansicht für Apps, die über den [Teams Store](/platform/concepts/deploy-and-publish/apps-publish-overview.md) verteilt werden und keine mobliesoptimierte Oberfläche haben, den Standardwebbrowser des Geräts. Der Browser öffnet die im `websiteUrl` Parameter des `TabInfo` Objekts angegebene URL.

## <a name="invoke-stage-view-through-deep-link"></a>Aufrufen der Phasenansicht über deep-Link

Um die Phasenansicht über den Deep-Link von Ihrer Registerkarte aus aufzurufen, müssen Sie die DEEP-Link-URL in der `microsoftTeams.executeDeeplink(url)` API umschließen. Der Deep-Link kann auch über eine `OpenURL` Aktion auf der Karte übergeben werden.

### <a name="syntax"></a>Syntax

Es folgt die Deeplinksyntax:

https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"contentUrl","websiteUrl":"websiteUrl","name":"Contoso"}
 
### <a name="examples"></a>Beispiele

Wenn ein Benutzer eine URL eingibt, wird diese in eine adaptive Karte entrollt.

Nachfolgend sind die Deep-Linkbeispiele zum Aufrufen der Phasenansicht aufgeführt:

**Beispiel 1: URL mit threadId**

Nicht codierte URL:

https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context={"contentUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191,"websiteUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true,"title":"Quotes:Miscellaneous","threadId":"19:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2"}

Codierte URL:

https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%2C%22threadId%22%3A%2219:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2%22%7D

**Beispiel 2: URL ohne threadId**

Nicht codierte URL:

https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context={"contentUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191,"websiteUrl":""https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true,"title":"Quotes:Miscellaneous"}

Codiert

https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%7D

> [!NOTE]
> Alle Deeplinks müssen vor dem Einfügen der URL codiert werden. Nicht codierte URLs werden nicht unterstützt.
>
> * Dies `name` ist optional im Deep-Link. Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt.
> * Der Deep-Link kann auch über eine `OpenURL` Aktion übergeben werden.
> * Wenn Sie eine Phase aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert. Wenn Ihre Phasenansicht beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App einen persönlichen Bereich aufweist.

## <a name="tab-information-property"></a>Tabinformationseigenschaft

| Eigenschaftenname | Typ | Anzahl der Zeichen | Beschreibung |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | Zeichenfolge | 64 | Diese Eigenschaft ist ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird. Dies ist ein Pflichtfeld.|
| `name` | Zeichenfolge | 128 | Diese Eigenschaft ist der Anzeigename der Registerkarte in der Kanalschnittstelle. Dieses Feld ist optional.|
| `contentUrl` | Zeichenfolge | 2048 | Diese Eigenschaft ist die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams Canvas angezeigt werden soll. Dies ist ein Pflichtfeld.|
| `websiteUrl?` | Zeichenfolge | 2048 | Diese Eigenschaft ist die https:// URL, auf die sie zeigen soll, wenn ein Benutzer die Anzeige in einem Browser auswählt. Dies ist ein Pflichtfeld.|
| `removeUrl?` | Zeichenfolge | 2048 | Diese Eigenschaft ist die https://-URL, die auf die Benutzeroberfläche zeigt, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.|

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Registerkarte in der Phasenansicht |Microsoft Teams Registerkartenbeispiel-App zum Demonstrieren der Registerkarte in der Phasenansicht.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Verbreitung von Messaging-Erweiterungen](~/messaging-extensions/how-to/link-unfurling.md)
* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
