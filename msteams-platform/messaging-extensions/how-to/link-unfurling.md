---
title: Entfalten von Links
author: clearab
description: So führen Sie in einer Microsoft Teams-App das Aufblinken von Links mit der Messagingerweiterung aus.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 0d488638e63b8ec78bfa5bed8cf6f4f037883fb1
ms.sourcegitcommit: bf61ae5ad2afa4efdb0311158184d0cbb9c40174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "49845637"
---
# <a name="link-unfurling"></a>Entfalten von Links

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> Derzeit wird das Entf?nden von Links auf mobilen Clients nicht unterstützt.

Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden. Die enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingegeben wurde, und Sie können mit einer Karte antworten, die der Benutzer ausf?nnen kann, um zusätzliche Informationen oder `invoke` Aktionen zur Verfügung zu stellen.  Dies funktioniert ähnlich wie bei einem [Suchbefehl,](~/messaging-extensions/how-to/search-commands/define-search-command.md)bei dem die URL als Suchbegriff dient.

Die Azure DevOps-Messaging-Erweiterung verwendet das Wiederverteilen von Links, um nach URLs zu suchen, die in den Bereich zum Verfassen von Nachrichten, die auf eine Arbeitsaufgabe zeigen, eingef?ndert sind. Im folgenden Screenshot hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingegeben, die die Messagingerweiterung in eine Karte aufgelöst hat.

![Beispiel für die Verknüpfungsentbündelung](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen der Linkentleierung zu Ihrem App-Manifest

 Fügen Sie zum Hinzufügen von Links zum Entfingen ihres App-Manifests dem Abschnitt ihres `messageHandlers` `composeExtensions` App-Manifest-JSON ein neues Array hinzu. Sie können das Array mithilfe von App Studio oder manuell hinzufügen. Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` . Dies entspricht genau einem Segment der Domäne. Wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .

> [!NOTE]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter. Beispielsweise ist yourapp.onmicrosoft.com gültig, *.onmicrosoft.com ist jedoch ungültig. Außerdem sind Domänen auf oberster Ebene unzulässig. Beispiel: *.com, *.org.

### <a name="using-app-studio"></a>Verwenden von App Studio

1. Laden Sie in App Studio auf der Registerkarte "Manifest-Editor" Ihr App-Manifest.
1. Fügen Sie **auf der Seite "Messagingerweiterung"** die Domäne hinzu, nach der Sie suchen möchten, im Abschnitt **"Nachrichtenhandler",** wie im folgenden Screenshot dargestellt.

![Abschnitt "Message Handlers" in App Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a>Manuell

Damit Ihre Messagingerweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das Array zu Ihrem App-Manifest hinzufügen, wie im folgenden `messageHandlers` Beispiel gezeigt. Dieses Beispiel ist nicht das vollständige Manifest, siehe [Manifestreferenz](~/resources/schema/manifest-schema.md) für ein vollständiges Manifestbeispiel.

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

Nachdem Sie die Domäne zum Abhören des App-Manifests hinzugefügt haben, müssen Sie Ihren Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten. Verwenden Sie die URL, die Sie erhalten, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen. Wenn Sie mit mehr als einer Karte antworten, wird nur die erste Karte verwendet.

Wir unterstützen die folgenden Kartentypen:

* [Miniaturansichtkarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Herokarte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Eine [Übersicht finden Sie unter "Was sind](~/task-modules-and-cards/what-are-cards.md) Karten".

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

Dies ist ein Beispiel für das an `invoke` Ihren Bot gesendete.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Ein Beispiel für die Antwort ist unten dargestellt.

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
