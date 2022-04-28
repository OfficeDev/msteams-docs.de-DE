---
title: Verbreiten von Links
author: surbhigupta
description: Erfahren Sie, wie Sie die Verbreitung von Links mit nachrichtenerweiterung in einer Microsoft Teams-App mit App-Manifest oder manuell mitHilfe von Codebeispielen und Beispielen hinzufügen.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 2dee02545a522b202e9cc695f7099848269e8944
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104406"
---
# <a name="link-unfurling"></a>Verbreiten von Links

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Sie Ihrem App-Manifest mit App Studio und manuell die Verbreitung von Links hinzufügen. Mit der Verbreitung von Links kann Sich Ihre App registrieren, um eine `invoke` Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Nachrichtenbereich zum Verfassen eingefügt werden. Die `invoke` enthält die vollständige URL, die in den Nachrichtenbereich zum Verfassen eingefügt wurde, und Sie können mit einer Karte antworten, die der Benutzer ausblenden kann, wodurch zusätzliche Informationen oder Aktionen bereitgestellt werden. Dies funktioniert ähnlich wie ein Suchbefehl, bei dem die URL als Suchbegriff dient.

> [!NOTE]
>
> * Derzeit wird die Verbreitung von Links auf mobilen Clients nicht unterstützt.
> * Das Ergebnis der Entknüpfung der Verknüpfung wird 30 Minuten lang zwischengespeichert.

Die Azure DevOps Nachrichtenerweiterung verwendet die Verbreitung von Links, um nach URLs zu suchen, die in den Nachrichtenbereich zum Verfassen eingefügt wurden, die auf ein Arbeitselement verweisen. In der folgenden Abbildung hat ein Benutzer eine URL für ein Arbeitselement in Azure DevOps eingefügt, die die Nachrichtenerweiterung in eine Karte aufgelöst hat:

![Beispiel für die Verbreitung von Links](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen der Verbreitung von Links zum App-Manifest

Um dem App-Manifest die Verbreitung von Links hinzuzufügen, fügen Sie dem `composeExtensions` Abschnitt ihres App-Manifest-JSON ein neues `messageHandlers` Array hinzu. Sie können das Array entweder mithilfe von App Studio oder manuell hinzufügen. Domäneneinträge können beispielsweise `*.example.com`Platzhalter enthalten. Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com`dann .

> [!NOTE]
> Fügen Sie keine Domänen hinzu, die sich weder direkt noch über Platzhalter in Ihrem Steuerelement befinden. Ist z. B. `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` ungültig. Außerdem sind domänen auf oberster Ebene unzulässig. Beispiel: `*.com`. `*.org`

### <a name="add-link-unfurling-using-app-studio"></a>Hinzufügen der Verbreitung von Links mitHilfe von App Studio

1. Öffnen Sie **App Studio** über den Microsoft Teams-Client, und wählen Sie die Registerkarte "**Manifest-Editor**" aus.
1. Laden Sie Ihr App-Manifest.
1. Fügen Sie auf der Seite " **Nachrichtenerweiterung** " die Domäne hinzu, nach der Sie im Abschnitt " **Nachrichtenhandler** " suchen möchten. In der folgenden Abbildung wird der Vorgang erläutert:

    ![Abschnitt "Nachrichtenhandler" in App Studio](~/assets/images/link-unfurling.png)

### <a name="add-link-unfurling-manually"></a>Hinzufügen der manuellen Verbreitung von Links

Damit Ihre Nachrichtenerweiterung mit Links interagiert, müssen Sie zuerst das `messageHandlers` Array zu Ihrem App-Manifest hinzufügen. Im folgenden Beispiel wird erläutert, wie Sie die Bereitstellung von Links manuell hinzufügen:

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

## <a name="handle-the-composeextensionquerylink-invoke"></a>Behandeln des Aufrufs `composeExtension/queryLink`

Nachdem Sie die Domäne zum App-Manifest hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten. Verwenden Sie die empfangene URL, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen. Wenn Sie mit mehr als einer Karte antworten, wird nur die erste Kartenantwort verwendet.

Die folgenden Kartentypen werden unterstützt:

* [Miniaturbildkarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Weitere Informationen finden Sie unter [Aufrufen des Aktionstyps](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).

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

Es folgt ein Beispiel für das `invoke` An Ihren Bot gesendete Beispiel:

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

Befolgen Sie die [schrittweise Anleitung](../../sbs-botbuilder-linkunfurling.yml), um Links in Teams mithilfe von Bot zu entfernen.

## <a name="see-also"></a>Siehe auch

* [Karten](~/task-modules-and-cards/what-are-cards.md)
* [Registerkartenverknüpfung und Phasenansicht](~/tabs/tabs-link-unfurling.md)