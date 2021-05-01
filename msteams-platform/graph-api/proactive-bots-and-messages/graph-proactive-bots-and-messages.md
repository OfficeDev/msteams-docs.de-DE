---
title: Verwenden von Microsoft Graph zum Autorisieren der proaktiven Botinstallation und -messaging in Teams
description: Beschreibt proaktives Messaging in Teams und Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: proaktive Messagingchatinstallation für teams Graph
ms.openlocfilehash: 62974f6f3b26e53558658f0b6cfda815dee1de8a
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101800"
---
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a>Proaktive Installation von Apps über die Graph-API und Senden von Nachrichten

>[!IMPORTANT]
> Microsoft Graph und Microsoft Teams öffentlichen Vorschauen stehen für frühzeitigen Zugriff und Feedback zur Verfügung. Obwohl diese Version umfangreichen Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.

## <a name="proactive-messaging-in-teams"></a>Proaktives Messaging in Teams

Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu starten. Sie dienen vielen Zwecken, z. B. dem Senden von Willkommensnachrichten, der Durchführung von Umfragen oder Umfragen und der Übertragung organisationsweiter Benachrichtigungen. Proaktive Nachrichten in Teams können entweder als **Ad-hoc-** oder **dialogbasierte Unterhaltungen zugestellt** werden:

|Nachrichtentyp | Beschreibung |
|----------------|-------------- |
|Ad-hoc-proaktive Nachricht| Der Bot interjects a message without interrupting the conversation flow.|
|Dialogbasierte proaktive Nachricht | Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, liefert die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.|

Siehe Senden [proaktiver Benachrichtigungen an Benutzer SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).

## <a name="proactive-app-installation-in-teams"></a>Proaktive App-Installation in Teams

Bevor Der Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist. Manchmal müssen Sie benutzer proaktiv nachrichten, die nicht installiert oder zuvor mit Ihrer App interagiert haben. Beispielsweise die Notwendigkeit, wichtige Informationen an alle in Ihrer Organisation zu senden. In solchen Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.

## <a name="permissions"></a>Berechtigungen

Microsoft Graph [teamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) hilft Ihnen, den Installationslebenszyklus Ihrer App für alle Benutzerbereiche (persönlich) oder Teambereiche (Kanal) innerhalb der Microsoft Teams verwalten:

|Anwendungsberechtigung | Beschreibung|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Ermöglicht es Teams App, sich selbst für jeden Benutzer zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anmelden oder verwenden zu müssen.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Ermöglicht einer Teams, sich selbst in einem Team zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anmelden oder verwenden zu müssen.|

Um diese Berechtigungen verwenden zu können, müssen Sie ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **id** – Ihre Azure AD-App-ID.
> * **Resource** – die Ressourcen-URL für die App.
>
>[!NOTE]
>
> * Ihr Bot erfordert anwendungs- und nicht benutzerdelegierte Berechtigungen, da die Installation für andere Personen gilt.
>
> * Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application) Nachdem einer Anwendung Berechtigungen erteilt wurden, erhalten alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.

## <a name="enable-proactive-app-installation-and-messaging"></a>Aktivieren einer proaktiven App-Installation und -Messaging

> [!IMPORTANT]
>Microsoft Graph kann nur Apps installieren, die im App Store Ihrer Organisation oder im Teams werden.

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ Erstellen und Veröffentlichen Ihres proaktiven Messagingbots für Teams

Für die ersten Schritte [](../../bots/how-to/create-a-bot-for-teams.md) benötigen Sie einen [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) Bot für Teams mit proaktiven Messagingfunktionen, die sich im App [Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) Ihrer Organisation oder im [Teams finden.](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store)

>[!TIP]
> Die produktionsbereite Communicator-App-Vorlage ermöglicht Übertragungsnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven Botanwendung. [](../..//samples/app-templates.md#company-communicator)

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Get the `teamsAppId` for your app

**1.** Sie benötigen die `teamsAppId` für die nächsten Schritte.

Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:

**Microsoft Graph:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

Die Anforderung muss ein Objekt `teamsApp` zurückgeben. Das zurückgegebene Objekt ist die von der App im Katalog generierte App-ID und ist von der ID, die Sie im Manifest ihrer app `id` Teams angegeben haben:

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

**2.**  Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder seitengeladen wurde, können Sie folgendes `teamsAppId` abrufen:

**Microsoft Graph: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** Wenn Ihre App für einen Kanal im Teambereich hochgeladen oder seitengeladen wurde, können Sie folgendes `teamsAppId` abrufen:

**Microsoft Graph:Apps** [im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Zum Einen der Ergebnisliste können Sie nach allen Feldern des [**teamsApp-Objekts**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern.

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist

**Microsoft Graph: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Diese Anforderung gibt ein leeres Array zurück, wenn die App nicht installiert ist, und ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) wenn die App installiert ist.

### <a name="-install-your-app"></a>✔ Installieren Ihrer App

**Microsoft Graph:App** [für Benutzer installieren](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** POST-Anforderung:

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Wenn der Benutzer Microsoft Teams ausgeführt wird, wird die App-Installation sofort angezeigt. Möglicherweise ist ein Neustart erforderlich, um die installierte App anzeigen zu können.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Abrufen der **Chat-Id für Unterhaltungen**

Wenn Ihre App für den Benutzer installiert ist, empfängt der Bot eine Ereignisbenachrichtigung, die die erforderlichen Informationen zum Senden der `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) proaktiven Nachricht enthält.

Der `chatId` kann auch wie folgt abgerufen werden:

**Microsoft Graph: Chat** [herunterladen](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

**1.** Sie müssen die . `{teamsAppInstallationId}` Wenn Sie nicht über diese Verfügen, verwenden Sie Folgendes:

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Die **id-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .

**2. Stellen** Sie die folgende Anforderung zum Abrufen der `chatId` :

**HTTP GET-Anforderung** (Berechtigung — `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

Die **id-Eigenschaft** der Antwort ist die `chatId` .

Sie können auch die mit `chatId` der folgenden Anforderung abrufen, erfordert jedoch die umfassendere `Chat.Read.All` Berechtigung:

**HTTP GET-Anforderung** (Berechtigung — `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Proaktive Nachrichten senden

Ihr Bot kann [proaktive Nachrichten senden,](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) nachdem der Bot für einen Benutzer oder ein Team hinzugefügt wurde und alle Benutzerinformationen erhalten hat.

## <a name="related-topic-for-teams-administrators"></a>Verwandtes Thema für Teams Administratoren
>
> [!div class="nextstepaction"]
> [**Verwalten von Richtlinien für App-Setup in Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a>Anzeigen zusätzlicher Codebeispiele
>
> [!div class="nextstepaction"]
> [**Teams proaktiver Messagingcodebeispiele**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
