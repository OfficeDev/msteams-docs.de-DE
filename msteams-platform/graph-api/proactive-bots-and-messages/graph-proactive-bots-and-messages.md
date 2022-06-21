---
title: Verwenden von Microsoft Graph zum Autorisieren der proaktiven Bot-Installation und des proaktiven Bot-Messagings in Microsoft Teams
description: In diesem Artikel werden proaktive Nachrichten in Teams und deren Implementierung beschrieben. Erfahren Sie anhand eines Codebeispiels, wie Sie die proaktive App-Installation und das proaktive Messaging aktivieren.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: Overview
ms.openlocfilehash: 832dfe6ddce7710d506c480fc1195c426b8da0df
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189584"
---
# <a name="proactive-installation-of-apps-using-graph-api-to-send-messages"></a>Proaktive Installation von Apps über die Graph-API zum Senden von Nachrichten

## <a name="proactive-messaging-in-teams"></a>Proaktives Messaging in Microsoft Teams

Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit Benutzern zu beginnen. Sie dienen vielen Zwecken, darunter dem Senden von Begrüßungsnachrichten, dem Durchführen von Umfragen oder dem Senden organisationsweiter Benachrichtigungen. Proaktive Nachrichten in Microsoft Teams können als **Ad-hoc**- oder **dialogbasierte** Unterhaltungen gesendet werden:

|Nachrichtentyp | Beschreibung |
|----------------|-------------- |
|Proaktive Ad-hoc-Nachrichten| Der Bot schiebt eine Nachricht ein, ohne die Unterhaltung zu unterbrechen.|
|Dialogbasierte proaktive Nachrichten | Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, übermittelt die proaktive Nachricht, schließt und gibt die Steuerung an den vorherigen Dialogthread zurück.|

## <a name="proactive-app-installation-in-teams"></a>Proaktive App-Installation in Microsoft Teams

Bevor Ihr Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist. Manchmal müssen Sie Benutzern, die Ihre App nicht installiert oder zuvor interagiert haben, proaktiv eine Nachricht senden. Wenn Sie beispielsweise wichtige Informationen an alle Personen in Ihrer Organisation senden müssen, können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.

## <a name="permissions"></a>Berechtigungen

Microsoft Graph-Berechtigungen für den [teamsAppInstallation-Ressourcentyp](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) helfen Ihnen, den Installationslebenszyklus Ihrer App für alle Benutzerbereiche (persönlich) oder Teambereiche (Kanal) innerhalb der Microsoft Teams-Plattform zu verwalten:

|Anwendungsberechtigung | Beschreibung|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Ermöglicht es einer Microsoft-Teams-App, sich selbst für einen *Benutzer* ohne vorherige Anmeldung oder Nutzung zu lesen, installieren, aktualisieren und deinstallieren.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Ermöglicht es einer Microsoft-Teams-App, sich selbst für ein beliebiges *Team* ohne vorherige Anmeldung oder Nutzung zu lesen, installieren, aktualisieren und deinstallieren.|

Um diese Berechtigungen zu verwenden, müssen Sie ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:

* **id**: Ihre Azure Active Directory App-ID
* **resource**: Die Ressourcen-URL für die App

> [!NOTE]
>
> * Ihr Bot benötigt Anwendungsberechtigungen und keine delegierten Benutzerberechtigungen, da die Installation für andere vorgesehen ist.
>
> * Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen](/graph/security-authorization#grant-permissions-to-an-application). Nachdem der Anwendung Berechtigungen erteilt wurden, erhalten alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.

## <a name="enable-proactive-app-installation-and-messaging"></a>Aktivieren der proaktiven Bot-Installation und des proaktiven Bot-Messagings

> [!IMPORTANT]
> Über Microsoft Graph können nur Apps installiert werden, die im App Store Ihrer Organisation oder im Microsoft Teams Store veröffentlicht wurden.

### <a name="create-and-publish-your-proactive-messaging-bot-for-teams"></a>Erstellen und Veröffentlichen eines proaktiven Messaging-Bots für Microsoft Teams

Für den Einstieg benötigen Sie einen [Bot für Microsoft Teams](../../bots/how-to/create-a-bot-for-teams.md) mit Funktionen für [proaktives Messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md), der im [App Store Ihrer Organisation](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) oder im [Teams Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store) verfügbar ist.

> [!TIP]
> Die produktionsbereite [*Company Communicator*](../..//samples/app-templates.md#company-communicator)-App-Vorlage ermöglicht Messaging und ist ein guter Ausgangspunkt zum Erstellen Ihrer proaktiven Bot-Anwendung.

### <a name="get-the-teamsappid-for-your-app"></a>Abrufen der `teamsAppId` für Ihre App

Sie können die `teamsAppId` wie folgt abrufen:

* Aus dem App-Katalog Ihrer Organisation:

    **Microsoft Graph-Seitenreferenz:** [Der teamsApp -Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

    **HTTP GET**-Anforderung:

    ```http
    GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
    ```

    Die Anforderung muss ein `teamsApp`-Objekt `id` zurückgeben, bei dem es sich um die vom App-Katalog generierte App-ID handelt. Diese unterscheidet sich von der ID, die Sie in Ihrem Microsoft Teams-App-Manifest angegeben haben:

    ```json
    {
      "value": [
        {
          "id": "b1c5353a-7aca-41b3-830f-27d5218fe0e5",
          "externalId": "f31b1263-ba99-435a-a679-911d24850d7c",
          "name": "Test App",
          "version": "1.0.1",
          "distributionMethod": "Organization"
        }
      ]
    }
    ```

* Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder quergeladen wurde:

    **Microsoft Graph-Seitenreferenz:** [Auflisten der für den Benutzer installierten Apps](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    **HTTP GET**-Anforderung:

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

* Wenn Ihre App bereits für einen Kanal im Teambereich hochgeladen oder quergeladen wurde:

    **Microsoft Graph-Seitenreferenz:** [Auflisten von Apps im Team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    **HTTP GET**-Anforderung:

    ```http
    GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

    > [!TIP]
    > Um die Ergebnisliste einzugrenzen, können Sie jedes der Felder des [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)-Objekts filtern.

### <a name="determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>Ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist

Sie können wie folgt ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist:

**Microsoft Graph-Seitenreferenz:** [Auflisten der für den Benutzer installierten Apps](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP GET**-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Die Anforderung gibt Folgendes zurück:

* Ein leeres Array, wenn die App nicht installiert ist.
* Ein Array mit einem einzelnen [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true)-Objekt, wenn die App installiert ist.

### <a name="install-your-app"></a>Installieren Ihrer App

Sie können Ihre App wie folgt installieren:

**Microsoft Graph Seitenreferenz:** [Apps für Benutzer installieren](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP POST**-Anforderung:

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Wenn Microsoft Teams bei dem Benutzer gerade aktiv ist, erfolgt die App-Installation sofort. Möglicherweise ist ein Neustart erforderlich, damit die installierte App angezeigt wird.

### <a name="retrieve-the-conversation-chatid"></a>Abrufen der `chatId` einer Unterhaltung

Wenn Ihre App für den Benutzer installiert ist, empfängt der Bot eine `conversationUpdate` [Ereignisbenachrichtigung](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition), die die erforderlichen Informationen zum Senden der proaktiven Nachricht enthält.

**Microsoft Graph-Seitenreferenz:** [Chat abrufen](/graph/api/chat-get?view=graph-rest-v1.0&tabs=http&preserve-view=true)

1. Sie müssen über die `{teamsAppInstallationId}` Ihrer App verfügen. Wenn sie nicht vorhanden ist, verwenden Sie Folgendes:

    **HTTP GET**-Anforderung:

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
    ```

    Die **id**-Eigenschaft der Antwort ist die `teamsAppInstallationId`.

1. Führen Sie die folgende Anforderung aus, um die `chatId` abzurufen:

    **HTTP GET-Anforderung** (Berechtigung:`TeamsAppInstallation.ReadWriteSelfForUser.All`):  

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
    ```

    Die **id**-Eigenschaft der Antwort ist die `chatId`.

    Sie können die `chatId` auch mit der folgenden Anforderung abrufen, sie erfordert jedoch die umfassendere `Chat.Read.All`-Berechtigung:

    **HTTP GET-Anforderung** (Berechtigung:`Chat.Read.All`):

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
    ```

### <a name="send-proactive-messages"></a>Senden proaktiver Nachrichten

Ihr Bot kann [proaktive Nachrichten senden](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true), nachdem er für einen Benutzer oder ein Team hinzugefügt wurde und alle Benutzerinformationen erhalten hat.

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code stellt ein Beispiel für das Senden proaktiver Nachrichten dar:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
public async Task<int> SendNotificationToAllUsersAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
   int msgSentCount = 0;

   // Send notification to all the members
   foreach (var conversationReference in _conversationReferences.Values)
   {
       await turnContext.Adapter.ContinueConversationAsync(_configuration["MicrosoftAppId"], conversationReference, BotCallback, cancellationToken);
       msgSentCount++;
   }

   return msgSentCount;
}

private async Task BotCallback(ITurnContext turnContext, CancellationToken cancellationToken)
{
   await turnContext.SendActivityAsync("Proactive hello.");
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
server.get('/api/notify', async (req, res) => {
    for (const conversationReference of Object.values(conversationReferences)) {
        await adapter.continueConversationAsync(process.env.MicrosoftAppId, conversationReference, async context => {
            await context.sendActivity('proactive hello');
        });
    }

    res.setHeader('Content-Type', 'text/html');
    res.writeHead(200);
    res.write('<html><body><h1>Proactive messages have been sent.</h1></body></html>');
    res.end();
});
```

---

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|---------------|--------------|--------|-------------|
| Proaktive Installation der App und Senden proaktiver Benachrichtigungen | Dieses Beispiel zeigt, wie Sie die proaktive Installation der App für Benutzer verwenden und proaktive Benachrichtigungen senden können, indem Sie Microsoft Graph APIs aufrufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) |

## <a name="additional-code-samples"></a>Zusätzliche Codebeispiele
>
> [!div class="nextstepaction"]
> [**Codebeispiele für proaktives Messaging in Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)

## <a name="see-also"></a>Siehe auch

* [Verwalten von Richtlinien für App-Setup in Teams](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [Proaktive Benachrichtigungen an Benutzer senden – SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)
