---
title: Entfalten von Links
author: clearab
description: So führen Sie die Verknüpfungsentschnappung mit der Messagingerweiterung in einer Microsoft Teams-App aus.
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 2037e1e9a903cfe90d0dd8866722b0d10fa156b2
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019818"
---
# <a name="link-unfurling"></a>Entfalten von Links

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Sie ihrem App-Manifest mithilfe von App Studio und manuell link unfurling hinzufügen. Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden. Der enthält die vollständige URL, die in den Bereich "Verfassen von Nachrichten" eingegeben wurde, und Sie können mit einer Karte antworten, die der Benutzer entfurlen kann, und zusätzliche Informationen oder `invoke` Aktionen bereitstellen. Dies funktioniert ähnlich wie bei einem Suchbefehl, bei dem die URL als Suchbegriff dient.

> [!NOTE]
> Derzeit wird die Verknüpfungsentfurling auf mobilen Clients nicht unterstützt.

Die Azure DevOps-Messagingerweiterung verwendet die Verknüpfungsentwennung, um nach URLs zu suchen, die in den Bereich verfassen von Nachrichten, die auf eine Arbeitsaufgabe zeigen, eingefügt wurden. In der folgenden Abbildung hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingegeben, die die Messagingerweiterung in eine Karte aufgelöst hat:

![Beispiel für die Verknüpfungsentfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen der Verknüpfungsentfurling zu Ihrem App-Manifest

Fügen Sie dem Abschnitt Ihres App-Manifests JSON ein neues Array hinzu, um dem App-Manifest ein neues Array `messageHandlers` `composeExtensions` hinzuzufügen. Sie können das Array entweder mithilfe von App Studio oder manuell hinzufügen. Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` . Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .

> [!NOTE]
> Fügen Sie keine Domänen hinzu, die sich weder direkt noch über Platzhalter in Ihrem Steuerelement befinden. Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig. Außerdem sind Domänen auf oberster Ebene verboten. Beispiel: `*.com` , `*.org` .

### <a name="add-link-unfurling-using-app-studio"></a>Hinzufügen der Verknüpfungsentfurling mithilfe von App Studio

1. Öffnen **Sie App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.
1. Laden Sie Ihr App-Manifest.
1. Fügen Sie **auf der** Seite Messagingerweiterung die Domäne hinzu, nach der Sie suchen möchten, im Abschnitt **Nachrichtenhandler.** In der folgenden Abbildung wird der Vorgang erläutert:

    ![Abschnitt "message handlers" in App Studio](~/assets/images/link-unfurling.png)
    
### <a name="add-link-unfurling-manually"></a>Manuelles Hinzufügen der Verknüpfungsentfurling

Damit Ihre Messagingerweiterung mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array zu Ihrem App-Manifest hinzufügen. Im folgenden Beispiel wird erläutert, wie Sie die Verknüpfung manuell entfernen: 


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

Ein vollständiges Manifestbeispiel finden Sie unter [Manifestreferenz](~/resources/schema/manifest-schema.md).

## <a name="handle-the-composeextensionquerylink-invoke"></a>Behandeln des `composeExtension/queryLink` Aufrufs

Nachdem Sie die Domäne zum App-Manifest hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten. Verwenden Sie die empfangene URL, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen. Wenn Sie mit mehreren Karten antworten, wird nur die erste Kartenantwort verwendet.

Die folgenden Kartentypen werden unterstützt:

* [Miniaturansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Heldenkarte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Connector-Karte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
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

Im Folgenden finden Sie ein Beispiel für die an `invoke` Ihren Bot gesendeten:

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Im Folgenden finden Sie ein Beispiel für die Antwort:

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

> [!div class="nextstepaction"]
> [Was sind Karten?](~/task-modules-and-cards/what-are-cards.md)
