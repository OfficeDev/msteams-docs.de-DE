---
title: Verwenden Sie Microsoft Graph, um proaktive Bot-Installation und Messaging in Teams zu autorisieren
description: Beschreibt proaktives Messaging in Teams und die Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Teams proaktive Messaging-Chat-Installation Graph
ms.openlocfilehash: 06b50e5ab8594c257959430383bab5e355af4e06
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566152"
---
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a>Proaktive Installation von Apps über die Graph-API und Senden von Nachrichten

>[!IMPORTANT]
> Microsoft Graph und Microsoft Teams öffentliche Vorschauen für den frühen Zugriff und Feedback verfügbar sind. Obwohl diese Version umfangreichen Tests unterzogen wurde, ist sie nicht für den Einsatz in der Produktion bestimmt.

## <a name="proactive-messaging-in-teams"></a>Proaktives Messaging in Teams

Proaktive Nachrichten werden von Bots initiiert, um Gespräche mit einem Benutzer zu starten. Sie dienen vielen Zwecken, einschließlich des Versendens von Begrüßungsbotschaften, der Durchführung von Umfragen oder Umfragen und der Übertragung von unternehmensweiten Benachrichtigungen. Proaktive Nachrichten in Teams können entweder als **Ad-hoc-** oder **dialogbasierte** Unterhaltungen übermittelt werden:

|Nachrichtentyp | Beschreibung |
|----------------|-------------- |
|Proaktive Ad-hoc-Nachricht| Der Bot interjekt eine Nachricht, ohne den Konversationsfluss zu unterbrechen.|
|Dialogbasierte proaktive Nachricht | Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, übermittelt die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.|

## <a name="proactive-app-installation-in-teams"></a>Proaktive App-Installation in Teams

Bevor Ihr Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist. Manchmal müssen Sie Benutzer, die nicht installiert oder zuvor mit Ihrer App interagiert haben, proaktiv an uns senden. Beispielsweise muss wichtige Informationen an alle in Ihrer Organisation gesendet werden. Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.

## <a name="permissions"></a>Berechtigungen

Microsoft Graph [teamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) helfen Ihnen, den Installationslebenszyklus Ihrer App für alle Benutzerbereiche (persönlich) oder Teambereiche (Kanal) innerhalb der Microsoft Teams Plattform zu verwalten:

|Anwendungsberechtigung | Beschreibung|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|Ermöglicht einer Teams App das Lesen, Installieren, Aktualisieren und Deinstallieren von **benutzern,** ohne sich vorher anzumelden oder zu verwenden.|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|Ermöglicht einer Teams App das Lesen, Installieren, Aktualisieren und Deinstallieren in jedem **Team,** ohne sich vorher anzumelden oder zu verwenden.|

Um diese Berechtigungen zu verwenden, müssen Sie Ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:
> [!div class="checklist"]
> [!div class="checklist"]
>
> * **id** – Ihre Azure AD-App-ID.
> * **Ressource** – die Ressourcen-URL für die App.
>
>[!NOTE]
>
> * Ihr Bot erfordert Anwendungsberechtigungen und keine vom Benutzer delegierten Berechtigungen, da die Installation für andere bestimmt ist.
>
> * Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application) Nachdem einer Anwendung Berechtigungen erteilt wurden, erhalten alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.

## <a name="enable-proactive-app-installation-and-messaging"></a>Aktivieren der proaktiven App-Installation und -Messaging

> [!IMPORTANT]
>Microsoft Graph können nur Apps installieren, die im App Store Ihrer Organisation oder im Teams Store veröffentlicht wurden.

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a>✔ Erstellen und Veröffentlichen Ihres proaktiven Messaging-Bots für Teams

Um zu beginnen, benötigen Sie einen [Bot für Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [proaktiven Messagingfunktionen,](../../concepts/bots/bot-conversations/bots-conv-proactive.md) die sich im [App Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) Ihrer Organisation oder im [Teams-Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store)befinden.

>[!TIP]
> Die produktionsbereite Communicator-App-Vorlage des [**Unternehmens**](../..//samples/app-templates.md#company-communicator) ermöglicht Broadcast-Messaging und ist eine gute Grundlage für den Aufbau Ihrer proaktiven Bot-Anwendung.

### <a name="-get-the-teamsappid-for-your-app"></a>✔ Holen Sie sich die `teamsAppId` für Ihre App

**1.** Sie benötigen die `teamsAppId` für die nächsten Schritte.

Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:

**Microsoft Graph Seitenverweis:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

Die Anforderung muss ein `teamsApp` Objekt zurückgeben. Das zurückgegebene Objekt `id` ist die vom Katalog generierte App-ID der App und unterscheidet sich von der ID, die Sie in Ihrem Teams-App-Manifest angegeben haben:

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

**2.**  Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder nebeninstalliert wurde, können Sie `teamsAppId` Folgendes abrufen:

**Microsoft Graph Seitenverweis:** [Apps auflisten, die für Benutzer installiert wurden](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

**3.** Wenn Ihre App für einen Kanal im Teambereich hochgeladen oder seitlich geladen wurde, können Sie `teamsAppId` Folgendes abrufen:

**Microsoft Graph Seitenverweis:** [Apps im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> Um die Ergebnisliste einzugrenzen, können Sie nach einem der Felder von [**teamsApp-Objekten**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern.

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a>✔ Bestimmen Sie, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist

**Microsoft Graph Seitenverweis:** [Apps auflisten, die für Benutzer installiert wurden](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Diese Anforderung gibt ein leeres Array zurück, wenn die App nicht installiert ist, und ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) wenn die App installiert ist.

### <a name="-install-your-app"></a>✔ Installieren Sie Ihre App

**Microsoft Graph Seitenverweis:** [App für Benutzer installieren](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)

**HTTP** POST-Anforderung:

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

Wenn der Benutzer Microsoft Teams ausgeführt hat, wird die App-Installation sofort angezeigt. Möglicherweise ist ein Neustart erforderlich, um die installierte App anzuzeigen.

### <a name="-retrieve-the-conversation-chatid"></a>✔ Abrufen der **Konversations-Chat-Id**

Wenn Ihre App für den Benutzer installiert ist, erhält der Bot eine `conversationUpdate` [Ereignisbenachrichtigung,](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) die die erforderlichen Informationen zum Senden der proaktiven Nachricht enthält.

Die `chatId` kann auch wie folgt abgerufen werden:

**Microsoft Graph Seitenverweis:** [Chat abrufen](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)

**1.** Sie müssen die `{teamsAppInstallationId}` . Wenn Sie es nicht haben, verwenden Sie Folgendes:

**HTTP** GET-Anforderung:

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

Die **id-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .

**2.** Stellen Sie die folgende Anfrage, um die `chatId` :

**HTTP GET-Anforderung** (Berechtigung — `TeamsAppInstallation.ReadWriteSelfForUser.All` ):  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

Die **id-Eigenschaft** der Antwort ist die `chatId` .

Sie können die auch mit der folgenden Anforderung abrufen, `chatId` erfordert jedoch die umfassendere `Chat.Read.All` Berechtigung:

**HTTP GET-Anforderung** (Berechtigung — `Chat.Read.All` ):

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a>✔ Proaktive Nachrichten senden

Ihr Bot kann [proaktive Nachrichten senden,](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) nachdem der Bot für einen Benutzer oder ein Team hinzugefügt wurde und alle Benutzerinformationen erhalten hat.

## <a name="see-also"></a>Siehe auch

* [**Verwalten von Richtlinien für App-Setup in Teams**](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [Senden proaktiver Benachrichtigungen an Benutzer SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="view-additional-code-samples"></a>Anzeigen zusätzlicher Codebeispiele
>
> [!div class="nextstepaction"]
> [**Teams proaktive Messagingcodebeispiele**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)