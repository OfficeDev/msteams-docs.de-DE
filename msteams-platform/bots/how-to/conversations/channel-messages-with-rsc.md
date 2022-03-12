---
title: Empfangen aller Kanalnachrichten mit RSC
author: surbhigupta12
description: Empfangen aller Kanalnachrichten mit RSC-Berechtigungen
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: b18b4f64d34abc1dec71c526c1f604978dc77cdf
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453453"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Empfangen aller Kanalnachrichten mit RSC

Das ressourcenspezifische Zustimmungsmodell (RSC), das ursprünglich für Teams Graph-APIs entwickelt wurde, wird auf Bot-Szenarien erweitert.

Mithilfe von RSC können Sie jetzt Teambesitzer bitten, einem Bot zuzustimmen, Benutzernachrichten über Standardkanäle in einem Team zu empfangen, ohne @mentioned zu werden. Diese Funktion wird aktiviert, indem die `ChannelMessage.Read.Group` Berechtigung im Manifest einer RSC-aktivierten Teams-App angegeben wird. Nach der Konfiguration können Teambesitzer während des App-Installationsvorgangs ihre Zustimmung erteilen.

Weitere Informationen zum Aktivieren von RSC für Ihre App finden Sie unter ["Ressourcenspezifische Zustimmung" in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Bots den Empfang aller Kanalnachrichten ermöglichen

Die `ChannelMessage.Read.Group` RSC-Berechtigung wird auf Bots erweitert. Mit der Zustimmung des Benutzers ermöglicht diese Berechtigung Graph-Anwendungen, alle Nachrichten in einer Unterhaltung abzurufen und Bots alle Kanalnachrichten zu empfangen, ohne @mentioned zu werden.

> [!NOTE]
>
> * Dienste, die Zugriff auf alle Teams Nachrichtendaten benötigen, müssen die Graph-APIs verwenden, die auch Zugriff auf archivierte Daten in Kanälen und Chats bieten.
> * Bots müssen die `ChannelMessage.Read.Group` RSC-Berechtigung entsprechend verwenden, um ansprechende Erfahrungen für Benutzer im Team zu erstellen und zu verbessern, oder sie bestehen die Store-Genehmigung nicht. Die App-Beschreibung muss enthalten, wie der Bot die gelesenen Daten verwendet.
> * Die `ChannelMessage.Read.Group` RSC-Berechtigung darf von Bots nicht als Möglichkeit verwendet werden, große Mengen von Kundendaten zu extrahieren.

## <a name="update-app-manifest"></a>Aktualisieren des App-Manifests

Damit Ihr Bot alle Kanalnachrichten empfangen kann, muss RSC im Teams App-Manifest mit der `ChannelMessage.Read.Group` in der `webApplicationInfo` Eigenschaft angegebenen Berechtigung konfiguriert sein.
![Aktualisieren des App-Manifests](~/bots/how-to/conversations/Media/appmanifest.png)

Es folgt ein Beispiel für das `webApplicationInfo` Objekt:

* **id**: Ihre Microsoft Azure Active Directory -App-ID (Azure AD). Dies kann mit Ihrer Bot-ID identisch sein.
* **ressource**: Eine beliebige Zeichenfolge. Dieses Feld verfügt über keinen Vorgang in RSC, muss jedoch hinzugefügt werden und einen Wert aufweisen, um eine Fehlerantwort zu vermeiden.
* **applicationPermissions**: RSC-Berechtigungen für Ihre App mit `ChannelMessage.Read.Group` müssen angegeben werden. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

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

Wenn Sie in einem Team querladen möchten, um zu testen, ob alle Kanalnachrichten in einem Team mit RSC empfangen werden, ohne @mentioned:

1. Wählen Sie ein Team aus, oder erstellen Sie es.
1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; im linken Bereich aus. Das Dropdownmenü wird angezeigt.
1. Wählen Sie im Dropdownmenü die Option **"Team verwalten** " aus. Die Details werden angezeigt.

   ![Verwalten von Apps im Team](~/bots/how-to/conversations/Media/managingteam.png)

1. Wählen Sie **Apps** aus. Es werden mehrere Apps angezeigt.
1. Wählen Sie in der unteren rechten Ecke **Hochladen einer benutzerdefinierten App** aus.

    ![Hochladen einer benutzerdefinierten App](~/bots/how-to/conversations/Media/uploadingcustomapp.png)

1. Wählen Sie im Dialogfeld **"Öffnen** " das App-Paket aus.
1. Klicken Sie auf **Öffnen**.

    ![Auswählen des App-Pakets](~/bots/how-to/conversations/Media/selectapppackage.png)

1. Wählen Sie im Popup "App-Details" die Option " **Hinzufügen** " aus, um den Bot ihrem ausgewählten Team hinzuzufügen.

    ![Hinzufügen des Bots](~/bots/how-to/conversations/Media/addingbot.png)

1. Wählen Sie einen Kanal aus, und geben Sie eine Nachricht im Kanal für Ihren Bot ein.

    Der Bot empfängt die Nachricht, ohne @mentioned zu werden.

    ![Bot empfängt Nachricht](~/bots/how-to/conversations/Media/botreceivingmessage.png)

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
|Kanalnachrichten mit RSC-Berechtigungen| Microsoft Teams Beispiel-App veranschaulicht, wie ein Bot alle Kanalnachrichten mit RSC empfangen kann, ohne @mentioned zu werden.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Bot-Unterhaltungen](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Ressourcenspezifische Zustimmung](/microsoftteams/resource-specific-consent)
* [Testen der ressourcenspezifischen Zustimmung](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Hochladen benutzerdefinierte App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
