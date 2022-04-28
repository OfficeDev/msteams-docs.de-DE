---
title: Empfangen aller Kanalnachrichten mit RSC
author: surbhigupta12
description: Empfangen aller Kanalnachrichten mit RSC-Berechtigungen
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: a78910b083943e5296f3e0d50eae00a713f194aa
ms.sourcegitcommit: e40383d9081bf117030f7e6270140e6b94214e8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65102074"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Empfangen aller Kanalnachrichten mit RSC

Das ressourcenspezifische Zustimmungsmodell (RESOURCE-Specific Consent, RSC) wurde ursprünglich für Teams Graph-APIs entwickelt und wird auf Botszenarien erweitert.

Mit RSC können Sie jetzt Teambesitzer bitten, einem Bot zuzustimmen, um Benutzernachrichten über Standardkanäle in einem Team zu empfangen, ohne @mentioned zu sein. Diese Funktion wird aktiviert, indem die `ChannelMessage.Read.Group` Berechtigung im Manifest einer RSC-aktivierten Teams-App angegeben wird. Nach der Konfiguration können Teambesitzer während des App-Installationsvorgangs die Zustimmung erteilen.

Weitere Informationen zum Aktivieren von RSC für Ihre App finden Sie [unter ressourcenspezifische Zustimmung in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Aktivieren von Bots zum Empfangen aller Kanalnachrichten

Die `ChannelMessage.Read.Group` RSC-Berechtigung wird auf Bots erweitert. Mit Zustimmung des Benutzers ermöglicht diese Berechtigung Graph-Anwendungen, alle Nachrichten in einer Unterhaltung abzurufen, und Bots können alle Kanalnachrichten empfangen, ohne @mentioned zu werden.

> [!NOTE]
>
> * Dienste, die Zugriff auf alle Teams Nachrichtendaten benötigen, müssen die Graph-APIs verwenden, die auch Zugriff auf archivierte Daten in Kanälen und Chats bieten.
> * Bots müssen die `ChannelMessage.Read.Group` RSC-Berechtigung entsprechend verwenden, um ansprechende Benutzererfahrungen für Benutzer im Team zu erstellen und zu verbessern, oder sie werden die Store-Genehmigung nicht bestehen. Die App-Beschreibung muss enthalten, wie der Bot die gelesenen Daten verwendet.
> * Die `ChannelMessage.Read.Group` RSC-Berechtigung darf nicht von Bots verwendet werden, um große Mengen von Kundendaten zu extrahieren.

## <a name="update-app-manifest"></a>Aktualisieren des App-Manifests

Damit Ihr Bot alle Kanalnachrichten empfangen kann, muss RSC im Teams App-Manifest mit der `ChannelMessage.Read.Group` in der `webApplicationInfo` Eigenschaft angegebenen Berechtigung konfiguriert werden.

![Aktualisieren des App-Manifests](~/bots/how-to/conversations/Media/appmanifest.png)


Es folgt ein Beispiel für das `webApplicationInfo` Objekt:

* **id**: Ihre Microsoft Azure Active Directory(Azure AD)-App-ID. Dies kann mit Ihrer Bot-ID identisch sein.
* **resource**: Any string. Dieses Feld hat keinen Vorgang in RSC, muss aber hinzugefügt werden und einen Wert aufweisen, um eine Fehlerantwort zu vermeiden.
* **applicationPermissions**: RSC-Berechtigungen für Ihre App `ChannelMessage.Read.Group` müssen angegeben werden. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

Der folgende Code enthält ein Beispiel für das App-Manifest:

```json
"webApplicationInfo": {
"id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
"resource": "https://AnyString",
"applicationPermissions": [
"ChannelMessage.Read.Group"
    ]
  }
```

## <a name="sideload-in-a-team"></a>Querladen in einem Team

So laden Sie in einem Team quer, um zu testen, ob alle Kanalnachrichten in einem Team mit RSC empfangen werden, ohne @mentioned:

1. Wählen Sie ein Team aus, oder erstellen Sie es.
1. Wählen Sie die aus dem linken Bereich &#x25CF;&#x25CF;&#x25CF; Auslassungszeichen aus. Das Dropdownmenü wird angezeigt.
1. Wählen Sie im Dropdownmenü " **Team verwalten** " aus. Die Details werden angezeigt.

   ![Verwalten von Apps im Team](~/bots/how-to/conversations/Media/managingteam.png)

      :::image type="content" source="Media/managingteam.png" alt-text="Verwalten des Teams"border="true":::

1. Wählen Sie **Apps** aus. Mehrere Apps werden angezeigt.
1. Wählen Sie **Hochladen einer benutzerdefinierten App** in der unteren rechten Ecke aus.

      :::image type="content" source="Media/uploadingcustomapp.png" alt-text="Hochladen einer benutzerdefinierten App":::
  
1. Wählen Sie das App-Paket im Dialogfeld " **Öffnen** " aus.
1. Klicken Sie auf **Öffnen**.

      :::image type="content" source="Media/selectapppackage.png" alt-text="Auswählen des App-Pakets"lightbox="Media/selectapppackage.png"border="true":::

1. Wählen Sie im Popup "App-Details" die Option **"Hinzufügen** " aus, um den Bot zu Ihrem ausgewählten Team hinzuzufügen.

      :::image type="content" source="Media/addingbot.png" alt-text="Hinzufügen eines Bots"lightbox="Media/addingbot.png"border="true":::

1. Wählen Sie einen Kanal aus, und geben Sie eine Nachricht in den Kanal für Ihren Bot ein.

    Der Bot empfängt die Nachricht, ohne @mentioned zu sein.

      :::image type="content" source="Media/botreceivingmessage.png" alt-text="Bot empfängt Nachricht"lightbox="Media/botreceivingmessage.png"border="true":::

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für RSC-Berechtigungen:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text("Using RSC the bot can recieve messages across channels in team without being @mentioned."));
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

// Handle when a message is addressed to the bot. 
// When rsc is enabled the method will be called even when bot is addressed without being @mentioned
this.onMessage(async (context, next) => {
   await context.sendActivity(MessageFactory.text("Using RSC the bot can recieve messages across channles in team without being @mentioned."))
   await next();
});
```

---

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Kanalnachrichten mit RSC-Berechtigungen| Microsoft Teams Beispiel-App, die zeigt, wie ein Bot alle Kanalnachrichten mit RSC empfangen kann, ohne @mentioned zu sein.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Bot-Unterhaltungen](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Ressourcenspezifische Zustimmung](/microsoftteams/resource-specific-consent)
* [Ressourcenspezifische Zustimmung testen](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Hochladen benutzerdefinierte App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
