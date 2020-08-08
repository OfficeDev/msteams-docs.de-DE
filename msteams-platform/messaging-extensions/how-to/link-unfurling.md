---
title: Entfalten von Links
author: clearab
description: Vorgehensweise durchführen einer Link Entfaltung mit Messaging Erweiterung in einer Microsoft Teams-app.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 32d19fcd44f2475047539350706d2745aeec3691
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587804"
---
# <a name="link-unfurling"></a>Entfalten von Links

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> Derzeit wird das Aufrollen von Hyperlinks auf mobilen Clients nicht unterstützt.

Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden. Der `invoke` enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde, und Sie können mit einer Karte Antworten, die der Benutzer *entfalten*kann, indem zusätzliche Informationen oder Aktionen bereitgestellt werden. Dies funktioniert ähnlich wie ein [Suchbefehl](~/messaging-extensions/how-to/search-commands/define-search-command.md), wobei die URL als Suchbegriff dient.

Die Azure DevOps-Messaging Erweiterung verwendet Link-Entfaltung, um nach URLs zu suchen, die in den Nachrichtenbereich verfassen eingefügt werden, der auf ein Arbeitselement zeigt. Im folgenden Screenshot wurde ein Benutzer in eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die von der Messaging Erweiterung in eine Karte aufgelöst wurde.

![Beispiel für eine Link-Entfaltung](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen eines Links, der Ihrem App-Manifest entrollt

Dazu fügen Sie `messageHandlers` dem `composeExtensions` Abschnitt Ihres App-Manifests JSON ein neues Array hinzu. Sie können dies entweder mit Hilfe von App Studio oder manuell tun. Domänen Auflistungen können beispielsweise Platzhalterzeichen enthalten `*.example.com` . Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung benötigen, `a.b.example.com` verwenden Sie `*.*.example.com` .

### <a name="using-app-studio"></a>Verwenden von App Studio

1. Laden Sie in App Studio auf der Registerkarte Manifest-Editor Ihr App-Manifest.
1. Fügen Sie auf der Seite **Messaging Erweiterung** im Abschnitt **Nachrichtenhandler** die Domäne hinzu, nach der Sie suchen möchten (siehe Screenshot unten).

![Abschnitt "Nachrichtenhandler" in App Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a>Manuell

Damit Ihre Messaging Erweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array wie im folgenden Beispiel zu Ihrem App-Manifest hinzufügen. Dieses Beispiel ist nicht das vollständige Manifest, siehe [Manifest-Referenz](~/resources/schema/manifest-schema.md) für ein vollständiges Manifest-Beispiel.

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

## <a name="handle-the-composeextensionquerylink-invoke"></a>Behandeln des `composeExtension/queryLink` Aufrufs

Nachdem Sie die Domäne zum Überwachen des App-Manifests hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Invoke-Anforderung zu verarbeiten. Verwenden Sie die URL, die Sie erhalten, um Ihren Dienst zu durchsuchen und eine Karten Antwort zu erstellen. Wenn Sie mit mehr als einer Karte Antworten, wird nur der erste verwendet.

Wir unterstützen die folgenden Kartentypen:

* [Miniatur Ansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero Card](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Anschluss Karte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Eine Übersicht finden Sie unter [Was sind Karten](~/task-modules-and-cards/what-are-cards.md) .

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

Dies ist ein Beispiel für die `invoke` an Ihren bot gesendet.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Unten sehen Sie ein Beispiel für die Antwort.

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
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
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
