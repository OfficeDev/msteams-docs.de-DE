---
title: Verwenden von Microsoft Graph zum Autorisieren proaktiver Bot-Installation und Messaging in Teams
description: Beschreibt proaktives Messaging in Teams und seine Implementierung. Erfahren Sie, wie Sie proaktive App-Installation und Messaging mithilfe von Codebeispielen aktivieren.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Proaktive Messaging-Chatinstallation von Teams Graph
ms.openlocfilehash: a3b7ffd24f7601c8247f1f11c6fe1a562d9cd847
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60888006"
---
# <a name="proactive-installation-of-apps-using-graph-api-to-send-messages"></a>Proaktive Installation von Apps über die Graph-API zum Senden von Nachrichten

>[!IMPORTANT]
> Microsoft Graph und Microsoft Teams öffentliche Vorschauen stehen für frühzeitigen Zugriff und Feedback zur Verfügung. Obwohl diese Version umfangreichen Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.

## <a name="proactive-messaging-in-teams"></a>Proaktives Messaging in Teams

Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu starten. Sie dienen vielen Zwecken, darunter das Senden von Willkommensnachrichten, das Durchführen von Umfragen oder Umfragen und das Senden organisationsweiter Benachrichtigungen. Proaktive Nachrichten in Teams können als **Ad-hoc-** oder **dialogbasierte** Unterhaltungen übermittelt werden:

|Nachrichtentyp | Beschreibung |
|----------------|-------------- |
|Proaktive Ad-hoc-Nachricht| Der Bot übergibt eine Nachricht, ohne den Unterhaltungsfluss zu unterbrechen.|
|Dialogbasierte proaktive Nachricht | Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, übermittelt die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.|

## <a name="proactive-app-installation-in-teams"></a>Proaktive App-Installation in Teams

Bevor Ihr Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist. Manchmal müssen Sie proaktive Nachrichten an Benutzer senden, die Ihre App nicht installiert oder zuvor mit ihrer App interagiert haben. Beispielsweise müssen wichtige Informationen an alle Personen in Ihrer Organisation ausgegeben werden. Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.

## <a name="permissions"></a>Berechtigungen

Microsoft Graph [TeamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) helfen Ihnen, den Installationslebenszyklus Ihrer App für alle Benutzer- (persönlichen) oder Teambereiche (Kanal) innerhalb der Microsoft Teams Plattform zu verwalten:

|Anwendungsberechtigung | Beschreibung|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Ermöglicht es einer Teams App, sich selbst ohne vorherige Anmeldung oder Verwendung für jeden *Benutzer* zu lesen, zu installieren, zu aktualisieren und zu deinstallieren.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Ermöglicht es einer Teams App, sich selbst in einem *Beliebigen Team* zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anzumelden oder zu verwenden.|

Um diese Berechtigungen zu verwenden, müssen Sie Ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:

* **id:** Ihre Azure Active Directory (AAD)-App-ID.
* **ressource:** Die Ressourcen-URL für die App.

> [!NOTE]
>
> * Ihr Bot erfordert Eine Anwendung und keine delegierten Benutzerberechtigungen, da die Installation für andere benutzerdelegiert ist.
>
> * Ein AAD Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application) Nachdem der Anwendung Berechtigungen erteilt wurden, erhalten alle Mitglieder des AAD Mandanten die erteilten Berechtigungen.

## <a name="enable-proactive-app-installation-and-messaging"></a>Proaktive App-Installation und Messaging aktivieren

> [!IMPORTANT]
> Microsoft Graph können nur Apps installieren, die im App Store Ihrer Organisation oder im Teams Store veröffentlicht wurden.

### <a name="create-and-publish-your-proactive-messaging-bot-for-teams"></a>Erstellen und Veröffentlichen Ihres proaktiven Messaging-Bots für Teams

Um zu beginnen, benötigen Sie einen [Bot für Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [proaktiven Messagingfunktionen,](../../concepts/bots/bot-conversations/bots-conv-proactive.md) die sich im [App Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) Ihrer Organisation oder im Teams [Store befinden.](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store)

> [!TIP]
> Die produktionsbereite [*Unternehmens-Communicator-App-Vorlage*](../..//samples/app-templates.md#company-communicator) ermöglicht Broadcast-Messaging und ist ein guter Start für die Erstellung Ihrer proaktiven Bot-Anwendung.

### <a name="get-the-teamsappid-for-your-app"></a>Abrufen der `teamsAppId` Für Ihre App

Sie können die `teamsAppId` folgenden Methoden abrufen:

* Aus dem App-Katalog Ihrer Organisation:

    **Microsoft Graph-Seitenreferenz:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

    **HTTP GET-Anforderung:**

    ```http
    GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
    ```

    Die Anforderung muss ein Objekt zurückgeben, bei dem es sich um `teamsApp` die vom `id` App-Katalog generierte App-ID handelt. Dies unterscheidet sich von der ID, die Sie in Ihrem Teams App-Manifest angegeben haben:

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

    **Microsoft Graph-Seitenverweis:** [Apps auflisten, die für Benutzer installiert sind](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    **HTTP GET-Anforderung:**

    ```http
    GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

* Wenn Ihre App bereits für einen Kanal im Teambereich hochgeladen oder quergeladen wurde:

    **Microsoft Graph-Seitenverweis:** [Apps im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

    **HTTP GET-Anforderung:**

    ```http
    GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
    ```

    > [!TIP]
    > Um die Liste der Ergebnisse einzugrenzen, können Sie alle Felder des [**teamsApp-Objekts**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern.

### <a name="determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>Ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist

Sie können wie folgt ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist:

**Microsoft Graph-Seitenverweis:** [Apps auflisten, die für Benutzer installiert sind](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP GET-Anforderung:**

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Die Anforderung gibt Folgendes zurück:

* Ein leeres Array, wenn die App nicht installiert ist.
* Ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) wenn die App installiert ist.

### <a name="install-your-app"></a>Installieren Ihrer App

Sie können Ihre App wie folgt installieren:

**Microsoft Graph-Seitenverweis:** [Installieren der App für den Benutzer](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP POST-Anforderung:**

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Wenn der Benutzer Microsoft Teams ausgeführt hat, erfolgt die App-Installation sofort. Möglicherweise ist ein Neustart erforderlich, um die installierte App anzuzeigen.

### <a name="retrieve-the-conversation-chatid"></a>Abrufen der Unterhaltung `chatId`

Wenn Ihre App für den Benutzer installiert ist, erhält der Bot eine `conversationUpdate` [Ereignisbenachrichtigung,](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) die die erforderlichen Informationen zum Senden der proaktiven Nachricht enthält.

**Microsoft Graph-Seitenverweis:** [Chat abrufen](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

1. Sie müssen über die `{teamsAppInstallationId}` App verfügen. Wenn sie nicht vorhanden ist, verwenden Sie Folgendes:

    **HTTP GET-Anforderung:**

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
    ```

    Die **ID-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .

1. Stellen Sie die folgende Anforderung, um die folgende Anforderung `chatId` abzurufen:

    **HTTP GET-Anforderung** (Berechtigung — `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
    ```

    Die **ID-Eigenschaft** der Antwort ist die `chatId` .

    Sie können dies auch `chatId` mit der folgenden Anforderung abrufen, erfordert jedoch die umfassendere `Chat.Read.All` Berechtigung:

    **HTTP GET-Anforderung** (Berechtigung — `Chat.Read.All` ):

    ```http
    GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
    ```

### <a name="send-proactive-messages"></a>Senden proaktiver Nachrichten

Ihr Bot kann [proaktive Nachrichten senden,](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) nachdem der Bot für einen Benutzer oder ein Team hinzugefügt wurde und alle Benutzerinformationen erhalten hat.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|---------------|--------------|--------|-------------|
| Proaktive Installation der App und Senden proaktiver Benachrichtigungen | Dieses Beispiel zeigt, wie Sie die proaktive Installation von Apps für Benutzer verwenden und proaktive Benachrichtigungen senden können, indem Sie Microsoft Graph APIs aufrufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) |

## <a name="additional-code-samples"></a>Zusätzliche Codebeispiele
>
> [!div class="nextstepaction"]
> [**Codebeispiele für proaktives Messaging Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)

## <a name="see-also"></a>Siehe auch

* [**Verwalten von App-Setuprichtlinien in Microsoft Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [Senden proaktiver Benachrichtigungen an Benutzer SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)
