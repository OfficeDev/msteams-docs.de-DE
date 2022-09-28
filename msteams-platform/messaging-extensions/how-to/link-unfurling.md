---
title: Verbreiten von Links
author: surbhigupta
description: Hinzufügen der Verbreitung von Links mit Messaging-Erweiterung in einer Microsoft Teams-App mit App-Manifest oder manuell. Hinzufügen der Verbreitung von Links mithilfe des Entwicklerportals. So aktualisieren Sie den Webdienstcode, um die Aufrufanforderung zu behandeln.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 57d3ed45bebfc221f376bf7e08aef73a5b4c40ae
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100630"
---
# <a name="add-link-unfurling"></a>Linkausweitung hinzufügen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

In diesem Dokument erfahren Sie, wie Sie Mithilfe des Entwicklerportals oder manuell links zu Ihrem App-Manifest hinzufügen. Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden. Enthält `invoke` die vollständige URL, die in den Nachrichtenbereich zum Verfassen eingefügt wurde. Sie können mit einer Karte antworten, die der Benutzer für zusätzliche Informationen oder Aktionen ausblenden kann. Dies funktioniert als Suchbefehl mit der URL als Suchbegriff.

> [!NOTE]
>
> * Derzeit wird das Aufheben der Verbreitung von Links auf mobilen Clients nicht unterstützt.
> * Das Ergebnis der Verbreitung von Links wird 30 Minuten lang zwischengespeichert.
> * Messaging-Erweiterungsbefehle sind für die Verbreitung von Links nicht erforderlich. Es muss jedoch mindestens ein Befehl im Manifest vorhanden sein, da es sich um eine obligatorische Eigenschaft in Messagingerweiterungen handelt. Weitere Informationen finden Sie [unter Verfassen von Erweiterungen](/microsoftteams/platform/resources/schema/manifest-schema)

Die Azure DevOps Nachrichtenerweiterung verwendet die Verbreitung von Links, um nach URLs zu suchen, die in den Bereich für das Verfassen von Nachrichten eingefügt werden, der auf ein Arbeitselement verweist. In der folgenden Abbildung hat ein Benutzer eine URL für ein Element in Azure DevOps eingefügt, das die Nachrichtenerweiterung in eine Karte aufgelöst hat:

:::image type="content" source="~/assets/images/compose-extensions/messagingextensions_linkunfurling.png" alt-text="Beispiel der Verbreitung von Links":::

Weitere Informationen zur Verbreitung von Links finden Sie im folgenden Video:
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OFZG]
<br>

## <a name="add-link-unfurling-to-your-app-manifest"></a>Hinzufügen einer Verbreitung von Links zum App-Manifest

Um Ihrem App-Manifest das Verbreiten von Links hinzuzufügen, fügen Sie dem `composeExtensions`-Abschnitt des JSON-Codes Ihres App-Manifests ein neues `messageHandlers`-Array hinzu. Sie können das Array mithilfe des Entwicklerportals oder manuell hinzufügen. Domain-Auflistungen können Platzhalter enthalten, zum Beispiel `*.example.com`. Dies entspricht genau einem Segment der Domäne; Wenn Sie übereinstimmen müssen, verwenden `a.b.example.com` Sie `*.*.example.com`.

> [!NOTE]
> Fügen Sie keine Domänen hinzu, die sich weder direkt noch über Platzhalter in Ihrem Steuerelement befinden. Beispielsweise ist `yourapp.onmicrosoft.com` gültig, `*.onmicrosoft.com` gilt jedoch nicht. Die Domänen der obersten Ebene sind verboten, `*.com`z. B. . `*.org`

### <a name="add-link-unfurling-using-developer-portal"></a>Hinzufügen der Verbreitung von Links mithilfe des Entwicklerportals

1. Öffnen Sie das **Entwicklerportal** über den Microsoft Teams-Client, und wählen Sie dann die Registerkarte **"Apps** " aus.
1. Laden Sie Ihr App-Manifest.
1. Wählen Sie auf der Seite " **Messaging-Erweiterung** " unter **"App-Features**" einen vorhandenen Bot aus, oder erstellen Sie einen neuen Bot.
1. Wählen Sie **Speichern** aus.
1. Wählen Sie im Abschnitt "**Vorschaulinks**" die Option **"Domäne hinzufügen**" aus, und geben Sie dann eine gültige Domäne ein.
1. Klicken Sie auf **Hinzufügen**. In der folgenden Abbildung wird der Prozess erläutert:

   :::image type="content" source="../../assets/images/tdp/add-domain-button.PNG" alt-text="Screenshot des Abschnitts &quot;Nachrichtenhandler&quot; im Entwicklerportal." lightbox="../../assets/images/tdp/add-domain.PNG":::

### <a name="add-link-unfurling-manually"></a>Verbreitung von Links manuell hinzufügen

> [!NOTE]
> Wenn die Authentifizierung über Azure AD hinzugefügt wird, [lösen Sie Links in Teams mithilfe des Bots](/microsoftteams/platform/sbs-botbuilder-linkunfurling?tabs=vs&tutorial-step=4) aus.

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
