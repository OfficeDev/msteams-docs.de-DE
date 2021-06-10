---
title: Entfalten von Links
author: clearab
description: So führen Sie die Verbreitung von Links mit der Messaging-Erweiterung in einer Microsoft Teams-App durch.
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 726ba47d1290b4dc38bb2b90e5ce9fc8a3c5fb6b
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853550"
---
# <a name="link-unfurling"></a>Entfalten von Links

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Sie Ihrem App-Manifest mitHilfe von App Studio und manuell eine Verknüpfung hinzufügen. Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden. Die `invoke` enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde, und Sie können mit einer Karte antworten, die der Benutzer freigeben kann, und zusätzliche Informationen oder Aktionen bereitstellen. Dies funktioniert ähnlich wie ein Suchbefehl mit der URL, die als Suchbegriff dient.

> [!NOTE]
> * Derzeit wird die Verbreitung von Links auf mobilen Clients nicht unterstützt.
> * Das Ergebnis der Verknüpfungsentrollung wird 30 Minuten zwischengespeichert.

Die Azure DevOps Messaging-Erweiterung verwendet die Verbreitung von Links, um nach URLs zu suchen, die in den Bereich zum Verfassen von Nachrichten eingefügt sind, die auf eine Arbeitsaufgabe verweisen. In der folgenden Abbildung hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die die Messaging-Erweiterung in eine Karte aufgelöst hat:

![Beispiel für die Verbreitung von Links](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen der Verbreitung von Links zu Ihrem App-Manifest

Zum Hinzufügen der Verbreitung von Links zu Ihrem App-Manifest fügen Sie `messageHandlers` dem Abschnitt Ihres App-Manifest-JSON ein neues Array `composeExtensions` hinzu. Sie können das Array entweder mithilfe von App Studio oder manuell hinzufügen. Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. . Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` .

> [!NOTE]
> Fügen Sie keine Domänen hinzu, die sich nicht in Ihrem Steuerelement befinden, entweder direkt oder über Platzhalter. Ist z. `yourapp.onmicrosoft.com` B. gültig, aber `*.onmicrosoft.com` nicht gültig. Außerdem sind die Domänen auf oberster Ebene nicht zulässig. Beispiel: `*.com` , `*.org` .

### <a name="add-link-unfurling-using-app-studio"></a>Hinzufügen der Verbreitung von Links mit App Studio

1. Öffnen Sie **App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **"Manifest-Editor"** aus.
1. Laden Sie Das App-Manifest.
1. Fügen Sie auf der Seite **"Messaging-Erweiterung"** die Domäne hinzu, nach der Sie im Abschnitt **"Nachrichtenhandler"** suchen möchten. In der folgenden Abbildung wird der Prozess erläutert:

    ![Abschnitt "message handlers" in App Studio](~/assets/images/link-unfurling.png)
    
### <a name="add-link-unfurling-manually"></a>Manuelles Hinzufügen der Verknüpfungsweitergabe

Damit Ihre Messaging-Erweiterung mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array zu Ihrem App-Manifest hinzufügen. Im folgenden Beispiel wird erläutert, wie Sie die Verknüpfungsweitergabe manuell hinzufügen: 


```json
...
"composeExtensions": [
  {
    "botId": "abc123456-ab12-ab12-ab12-abcdef123456",
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.trackeddomain.com"
          ]
        }
      }
    ]
  }
],
...
```

Ein vollständiges Manifestbeispiel finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md)

## <a name="handle-the-composeextensionquerylink-invoke"></a>Behandeln des `composeExtension/queryLink` Aufrufs

Nachdem Sie die Domäne zum App-Manifest hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten. Verwenden Sie die empfangene URL, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen. Wenn Sie mit mehr als einer Karte antworten, wird nur die erste Kartenantwort verwendet.

Die folgenden Kartentypen werden unterstützt:

* [Miniaturansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

### <a name="example"></a>Beispiel

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsAppBasedLinkQueryAsync(ITurnContext<IInvokeActivity> turnContext, AppBasedLinkQuery query, CancellationToken cancellationToken)
{
    //You'll use the query.link value to search your service and create a card response
    var card = new HeroCard
    {
        Title = "Hero Card",
        Text = query.Url,
        Images = new List<CardImage> { new CardImage("https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png") },
    };

    var attachments = new MessagingExtensionAttachment(HeroCard.ContentType, null, card);
    var result = new MessagingExtensionResult(AttachmentLayoutTypes.List, "result", new[] { attachments }, null, "test unfurl");

    return new MessagingExtensionResponse(result);
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsLinkUnfurlingBot extends TeamsActivityHandler {
  handleTeamsAppBasedLinkQuery(context, query) {
    const attachment = CardFactory.thumbnailCard('Thumbnail Card',
      query.url,
      ['https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png']);

    const result = {
      attachmentLayout: 'list',
      type: 'result',
      attachments: [attachment]
    };

    const response = {
      composeExtension: result
    };
    return response;
  }
}
```

# <a name="json"></a>[Json](#tab/json)

Es folgt ein Beispiel für das `invoke` An Ihren Bot gesendete:

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Es folgt ein Beispiel für die Antwort:

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "attachments": [
      {
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

* * *

## <a name="see-also"></a>Siehe auch 

* [Karten](~/task-modules-and-cards/what-are-cards.md)
* [Aufgeklappte Registerkartenverknüpfung und Phasenansicht](~/tabs/tabs-link-unfurling.md)
