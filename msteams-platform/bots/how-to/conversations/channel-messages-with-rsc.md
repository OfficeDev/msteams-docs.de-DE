---
title: Empfangen aller Kanalnachrichten mit RSC
author: surbhigupta12
description: Aktivieren Sie Bots, alle Kanalnachrichten zu empfangen, ohne mit RSC-Berechtigungen @mentioned zu werden. Lesen Sie im WebApplicationInfo- oder Autorisierungsabschnitt im Manifest.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: bd740c999139d9b5f98c10800646501dd55e87f5
ms.sourcegitcommit: 217025a61ed9c3b76b507fe95563142abc6d0318
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2022
ms.locfileid: "67363466"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Empfangen aller Kanalnachrichten mit RSC

Das Modell für RSC-Berechtigungen (Resource-Specific Consent, ressourcenspezifische Zustimmung), das ursprünglich für Teams Graph-APIs entwickelt wurde, wird auf Bot-Szenarien erweitert.

Mit RSC können Sie jetzt Teambesitzer bitten, einem Bot zuzustimmen, damit er Benutzernachrichten über Standardkanäle in einem Team empfangen kann, ohne @erwähnt zu werden. Diese Funktion wird aktiviert, indem die Berechtigung `ChannelMessage.Read.Group` im Manifest einer RSC-fähigen Teams-App angegeben wird. Nach der Konfiguration können Teambesitzer während der App-Installation ihre Zustimmung erteilen.

Weitere Informationen zum Aktivieren von RSC für Ihre App finden Sie unter [Ressourcenspezifische Zustimmung in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).

## <a name="enable-bots-to-receive-all-channel-messages"></a>Ermöglichen des Empfangs aller Kanalnachrichten für Bots

Die RSC-Berechtigung `ChannelMessage.Read.Group` wird auf Bots erweitert. Mit Zustimmung des Benutzers ermöglicht es diese Berechtigung, dass Graph-Anwendungen alle Nachrichten in einer Unterhaltung abrufen und Bots alle Kanalnachrichten empfangen, ohne @erwähnt zu werden.

> [!NOTE]
>
> * Dienste, die Zugriff auf alle Teams-Nachrichtendaten benötigen, müssen die Graph-APIs verwenden, die auch Zugriff auf archivierte Daten in Kanälen und Chats bieten.
> * Bots müssen die RSC-Berechtigung `ChannelMessage.Read.Group` angemessen verwenden, um für Benutzer im Team ansprechende Erfahrungen zu erstellen und zu verbessern. Andernfalls erhalten sie die Store-Genehmigung nicht. Die App-Beschreibung muss enthalten, wie der Bot die gelesenen Daten verwendet.
> * Die RSC-Berechtigung `ChannelMessage.Read.Group` kann von Bots nicht als Möglichkeit verwendet werden, große Mengen von Kundendaten zu extrahieren.

## <a name="update-app-manifest"></a>Aktualisieren des App-Manifests

Damit Ihr Bot alle Kanalnachrichten empfangen kann, muss RSC im Teams-App-Manifest mit der Berechtigung `ChannelMessage.Read.Group`, die in der Eigenschaft `webApplicationInfo` angegeben ist, konfiguriert werden.

:::image type="content" source="~/bots/how-to/conversations/Media/appmanifest.png" alt-text="Screenshot des App-Manifestupdates.":::

Im Folgenden sehen Sie ein Beispiel für das Objekt `webApplicationInfo`:

* **id**: Ihre Microsoft Azure Active Directory-App-ID (Azure AD). Diese kann mit Ihrer Bot-ID identisch sein.
* **resource**: Eine beliebige Zeichenfolge. Dieses Feld hat keine Funktion in RSC, muss jedoch hinzugefügt werden und einen Wert aufweisen, um Fehlerantworten zu vermeiden.
* **applicationPermissions**: RSC-Berechtigungen für Ihre App mit `ChannelMessage.Read.Group` müssen angegeben werden. Weitere Informationen finden Sie unter [Ressourcenspezifische Berechtigungen](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

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

So laden Sie in einem Team quer, um zu testen, ob alle Kanalnachrichten in einem Team mit RSC empfangen werden, ohne @erwähnt zu werden

1. Wählen Sie ein Team aus, oder erstellen Sie es.
1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; im linken Bereich aus. Das Dropdownmenü wird angezeigt.
1. Wählen Sie im Dropdownmenü **Team verwalten** aus. Die Details werden angezeigt.

   :::image type="content" source="Media/managingteam.png" alt-text="Screenshot der Option &quot;Team verwalten&quot; in der Teams-Anwendung.":::

1. Wählen Sie **Apps** aus. Es werden mehrere Apps angezeigt.

1. Wählen Sie in der unteren rechten Ecke **Benutzerdefinierte App hochladen** aus.

      :::image type="content" source="Media/uploadingcustomapp.png" alt-text="Screenshot des Hochladens einer benutzerdefinierten App-Option.":::
  
1. Wählen Sie das App-Paket im Dialogfeld **Öffnen** aus.

1. Klicken Sie auf **Öffnen**.

      :::image type="content" source="Media/selectapppackage.png" alt-text="Screenshot des Dialogfelds &quot;Öffnen&quot;, um das App-Paket auszuwählen." lightbox="Media/selectapppackage.png":::

1. Wählen Sie im Popupfenster der App-Details **Hinzufügen** aus, um den Bot Ihrem ausgewählten Team hinzuzufügen.

      :::image type="content" source="Media/addingbot.png" alt-text="Screenshot der Schaltfläche &quot;Hinzufügen&quot;, um einem Team einen Bot hinzuzufügen." lightbox="Media/addingbot.png":::

1. Wählen Sie einen Kanal aus, und geben Sie im Kanal eine Nachricht für Ihren Bot ein.

    Der Bot empfängt die Nachricht, ohne @erwähnt zu werden.

      :::image type="content" source="Media/botreceivingmessage.png" alt-text="Screenshot eines Bots, der eine Nachricht in einem Kanal empfängt." lightbox="Media/botreceivingmessage.png":::

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
|Kanalnachrichten mit RSC-Berechtigungen| Die Microsoft Teams-Beispiel-App veranschaulicht, wie ein Bot alle Kanalnachrichten mit RSC empfangen kann, ohne @erwähnt zu werden.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Bot-Unterhaltungen](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Ressourcenspezifische Zustimmung](/microsoftteams/resource-specific-consent)
* [Testen der ressourcenspezifischen Zustimmung](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Hochladen einer benutzerdefinierten App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
* [Antworten auf Nachrichten in einem Kanal auflisten](/graph/api/chatmessage-list-replies?view=graph-rest-1.0&tabs=http&preserve-view=true)
