---
title: Verbreiten von Links
author: surbhigupta
description: Erfahren Sie, wie Sie in einer Microsoft Teams-App mit App-Manifest oder manuell mithilfe von Codebeispielen und Beispielen Links verbreiten, die sich mit der Messagingerweiterung erweitern.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 09b8447e68a07e98293409e6c371a301da3017d0
ms.sourcegitcommit: 430bf416bb8d1b74f926c8b5d5ffd3dbb0782286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2022
ms.locfileid: "65297184"
---
# <a name="link-unfurling"></a>Verbreiten von Links

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Sie Ihrem App-Manifest das Verbreiten von Links mithilfe von App Studio und manuell hinzufügen können. Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden. Die `invoke`-Aktivität enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde, und Sie können mit einer Karte antworten, die der Benutzer öffnen kann, die zusätzliche Informationen oder Aktionen bereitstellt. Dies funktioniert ähnlich wie ein Suchbefehl, wobei die URL als Suchbegriff dient.

> [!NOTE]
>
> * Derzeit wird das Aufheben der Verbreitung von Links auf mobilen Clients nicht unterstützt.
> * Das Ergebnis der Verbreitung von Links wird 30 Minuten lang zwischengespeichert.

Die Azure DevOps Nachrichtenerweiterung verwendet die Verbreitung von Links, um nach URLs zu suchen, die in den Bereich für das Verfassen von Nachrichten eingefügt werden, der auf ein Arbeitselement verweist. In der folgenden Abbildung hat ein Benutzer eine URL für ein Arbeitselement in Azure DevOps eingefügt, die die Nachrichtenerweiterung in eine Karte aufgelöst hat:

:::image type="content" source="~/assets/images/compose-extensions/messagingextensions_linkunfurling.png" alt-text="Beispiel der Verbreitung von Links":::

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen einer Verbreitung von Links zum App-Manifest

Um Ihrem App-Manifest das Verbreiten von Links hinzuzufügen, fügen Sie dem `composeExtensions`-Abschnitt des JSON-Codes Ihres App-Manifests ein neues `messageHandlers`-Array hinzu. Sie können das Array entweder mithilfe von App Studio oder manuell hinzufügen. Domain-Auflistungen können Platzhalter enthalten, zum Beispiel `*.example.com`. Dies entspricht genau einem Segment der Domäne; Wenn Sie übereinstimmen müssen, verwenden `a.b.example.com` Sie `*.*.example.com`.

> [!NOTE]
> Fügen Sie keine Domänen hinzu, die nicht Ihrer Kontrolle liegen, weder direkt noch über Platzhalter. Beispielsweise ist `yourapp.onmicrosoft.com` gültig, `*.onmicrosoft.com` gilt jedoch nicht. Außerdem sind die Domänen der obersten Ebene nicht zulässig. Beispielsweise `*.com`, `*.org`.

### <a name="add-link-unfurling-using-app-studio"></a>Hinzufügen des Verbreitens von Links mit App Studio

1. Öffnen Sie **App Studio** über den Microsoft Teams-Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.
1. Laden Sie Ihr App-Manifest.
1. Fügen Sie auf der Seite **Nachrichtenerweiterung** die Domäne hinzu, nach der Sie im Abschnitt **Nachrichtenhandler** suchen möchten. Das folgende Bild erläutert den Prozess:

    :::image type="content" source="~/assets/images/link-unfurling.png" alt-text="Abschnitt „Nachrichtenhandler“ in App Studio":::

### <a name="add-link-unfurling-manually"></a>Verbreitung von Links manuell hinzufügen

Damit Ihre Nachrichtenerweiterung mit Links interagieren kann, müssen Sie zuerst das `messageHandlers`-Array zu Ihrem App-Manifest hinzufügen. Im folgenden Beispiel wird erläutert, wie Sie das Verbreiten von Links manuell hinzufügen:

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

## <a name="handle-the-composeextensionquerylink-invoke"></a>Behandeln des `composeExtension/queryLink`-Aufrufs

Nachdem Sie die Domäne zum App-Manifest hinzugefügt haben, müssen Sie Ihren Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten. Verwenden Sie die empfangene URL, um Ihren Dienst durchzusuchen und eine Kartenantwort zu erstellen. Wenn Sie mit mehr als einer Karte antworten, wird nur die erste Kartenantwort verwendet.

Die folgenden Kartentypen werden unterstützt:

* [Miniaturbildkarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Weitere Informationen finden Sie unter [Aktionstypaufruf](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).

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

# <a name="json"></a>[JSON](#tab/json)

Es folgt ein Beispiel für `invoke`, die an Ihren Bot gesendet werden:

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

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../sbs-botbuilder-linkunfurling.yml), um Links in Teams mithilfe des Bots zu verbreiten.

## <a name="see-also"></a>Siehe auch

* [Karten](~/task-modules-and-cards/what-are-cards.md)
* [Registerkartenlink entfalten und Bühnenansicht](~/tabs/tabs-link-unfurling.md)