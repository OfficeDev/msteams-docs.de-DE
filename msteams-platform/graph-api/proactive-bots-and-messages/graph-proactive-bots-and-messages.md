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
# <a name="proactive-installation-of-apps-using-graph-api-and-send-messages"></a><span data-ttu-id="48bf1-104">Proaktive Installation von Apps über die Graph-API und Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="48bf1-104">Proactive installation of apps using Graph API and send messages</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48bf1-105">Microsoft Graph und Microsoft Teams öffentlichen Vorschauen stehen für frühzeitigen Zugriff und Feedback zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="48bf1-105">Microsoft Graph and Microsoft Teams public previews are available for early access and feedback.</span></span> <span data-ttu-id="48bf1-106">Obwohl diese Version umfangreichen Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="48bf1-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="48bf1-107">Proaktives Messaging in Teams</span><span class="sxs-lookup"><span data-stu-id="48bf1-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="48bf1-108">Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu starten.</span><span class="sxs-lookup"><span data-stu-id="48bf1-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="48bf1-109">Sie dienen vielen Zwecken, z. B. dem Senden von Willkommensnachrichten, der Durchführung von Umfragen oder Umfragen und der Übertragung organisationsweiter Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="48bf1-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span> <span data-ttu-id="48bf1-110">Proaktive Nachrichten in Teams können entweder als **Ad-hoc-** oder **dialogbasierte Unterhaltungen zugestellt** werden:</span><span class="sxs-lookup"><span data-stu-id="48bf1-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="48bf1-111">Nachrichtentyp</span><span class="sxs-lookup"><span data-stu-id="48bf1-111">Message Type</span></span> | <span data-ttu-id="48bf1-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="48bf1-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="48bf1-113">Ad-hoc-proaktive Nachricht</span><span class="sxs-lookup"><span data-stu-id="48bf1-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="48bf1-114">Der Bot interjects a message without interrupting the conversation flow.</span><span class="sxs-lookup"><span data-stu-id="48bf1-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="48bf1-115">Dialogbasierte proaktive Nachricht</span><span class="sxs-lookup"><span data-stu-id="48bf1-115">Dialog-based proactive message</span></span> | <span data-ttu-id="48bf1-116">Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, liefert die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.</span><span class="sxs-lookup"><span data-stu-id="48bf1-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

<span data-ttu-id="48bf1-117">Siehe Senden [proaktiver Benachrichtigungen an Benutzer SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="48bf1-117">See, [Send proactive notifications to users SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="48bf1-118">Proaktive App-Installation in Teams</span><span class="sxs-lookup"><span data-stu-id="48bf1-118">Proactive app installation in Teams</span></span>

<span data-ttu-id="48bf1-119">Bevor Der Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="48bf1-119">Before your bot can proactively message a user, it must be installed either as a personal app or in a team where the user is a member.</span></span> <span data-ttu-id="48bf1-120">Manchmal müssen Sie benutzer proaktiv nachrichten, die nicht installiert oder zuvor mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="48bf1-120">At times, you need to proactively message users that have not installed or previously interacted with your app.</span></span> <span data-ttu-id="48bf1-121">Beispielsweise die Notwendigkeit, wichtige Informationen an alle in Ihrer Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="48bf1-121">For example, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="48bf1-122">In solchen Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.</span><span class="sxs-lookup"><span data-stu-id="48bf1-122">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="48bf1-123">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="48bf1-123">Permissions</span></span>

<span data-ttu-id="48bf1-124">Microsoft Graph [teamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) hilft Ihnen, den Installationslebenszyklus Ihrer App für alle Benutzerbereiche (persönlich) oder Teambereiche (Kanal) innerhalb der Microsoft Teams verwalten:</span><span class="sxs-lookup"><span data-stu-id="48bf1-124">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="48bf1-125">Anwendungsberechtigung</span><span class="sxs-lookup"><span data-stu-id="48bf1-125">Application permission</span></span> | <span data-ttu-id="48bf1-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="48bf1-126">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="48bf1-127">Ermöglicht es Teams App, sich selbst für jeden Benutzer zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anmelden oder verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="48bf1-127">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="48bf1-128">Ermöglicht einer Teams, sich selbst in einem Team zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anmelden oder verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="48bf1-128">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="48bf1-129">Um diese Berechtigungen verwenden zu können, müssen Sie ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="48bf1-129">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="48bf1-130">**id** – Ihre Azure AD-App-ID.</span><span class="sxs-lookup"><span data-stu-id="48bf1-130">**id** — your Azure AD app ID.</span></span>
> * <span data-ttu-id="48bf1-131">**Resource** – die Ressourcen-URL für die App.</span><span class="sxs-lookup"><span data-stu-id="48bf1-131">**resource** — the resource URL for the app.</span></span>
>
>[!NOTE]
>
> * <span data-ttu-id="48bf1-132">Ihr Bot erfordert anwendungs- und nicht benutzerdelegierte Berechtigungen, da die Installation für andere Personen gilt.</span><span class="sxs-lookup"><span data-stu-id="48bf1-132">Your bot requires application and not user delegated permissions because the installation is for others.</span></span>
>
> * <span data-ttu-id="48bf1-133">Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application)</span><span class="sxs-lookup"><span data-stu-id="48bf1-133">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="48bf1-134">Nachdem einer Anwendung Berechtigungen erteilt wurden, erhalten alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="48bf1-134">After an application is granted permissions, all members of the Azure AD tenant gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="48bf1-135">Aktivieren einer proaktiven App-Installation und -Messaging</span><span class="sxs-lookup"><span data-stu-id="48bf1-135">Enable proactive app installation and messaging</span></span>

> [!IMPORTANT]
><span data-ttu-id="48bf1-136">Microsoft Graph kann nur Apps installieren, die im App Store Ihrer Organisation oder im Teams werden.</span><span class="sxs-lookup"><span data-stu-id="48bf1-136">Microsoft Graph can only install apps published to your organization's app store or the Teams store.</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="48bf1-137">✔ Erstellen und Veröffentlichen Ihres proaktiven Messagingbots für Teams</span><span class="sxs-lookup"><span data-stu-id="48bf1-137">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="48bf1-138">Für die ersten Schritte [](../../bots/how-to/create-a-bot-for-teams.md) benötigen Sie einen [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) Bot für Teams mit proaktiven Messagingfunktionen, die sich im App [Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) Ihrer Organisation oder im [Teams finden.](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store)</span><span class="sxs-lookup"><span data-stu-id="48bf1-138">To get started, you need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities that's in your [organization's app store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) or the [Teams store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).</span></span>

>[!TIP]
> <span data-ttu-id="48bf1-139">Die produktionsbereite Communicator-App-Vorlage ermöglicht Übertragungsnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven Botanwendung. [](../..//samples/app-templates.md#company-communicator)</span><span class="sxs-lookup"><span data-stu-id="48bf1-139">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template permits broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="48bf1-140">✔ Get the `teamsAppId` for your app</span><span class="sxs-lookup"><span data-stu-id="48bf1-140">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="48bf1-141">**1.** Sie benötigen die `teamsAppId` für die nächsten Schritte.</span><span class="sxs-lookup"><span data-stu-id="48bf1-141">**1.** You need the `teamsAppId` for the next steps.</span></span>

<span data-ttu-id="48bf1-142">Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="48bf1-142">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="48bf1-143">**Microsoft Graph:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="48bf1-143">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="48bf1-144">**HTTP** GET-Anforderung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-144">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="48bf1-145">Die Anforderung muss ein Objekt `teamsApp` zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="48bf1-145">The request must return a `teamsApp` object.</span></span> <span data-ttu-id="48bf1-146">Das zurückgegebene Objekt ist die von der App im Katalog generierte App-ID und ist von der ID, die Sie im Manifest ihrer app `id` Teams angegeben haben:</span><span class="sxs-lookup"><span data-stu-id="48bf1-146">The returned object `id` is the app's catalog generated app ID and is different from the ID that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="48bf1-147">**2.**  Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder seitengeladen wurde, können Sie folgendes `teamsAppId` abrufen:</span><span class="sxs-lookup"><span data-stu-id="48bf1-147">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="48bf1-148">**Microsoft Graph: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="48bf1-148">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="48bf1-149">**HTTP** GET-Anforderung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-149">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="48bf1-150">**3.** Wenn Ihre App für einen Kanal im Teambereich hochgeladen oder seitengeladen wurde, können Sie folgendes `teamsAppId` abrufen:</span><span class="sxs-lookup"><span data-stu-id="48bf1-150">**3.** If your app has been uploaded or sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="48bf1-151">**Microsoft Graph:Apps** [im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="48bf1-151">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="48bf1-152">**HTTP** GET-Anforderung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-152">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="48bf1-153">Zum Einen der Ergebnisliste können Sie nach allen Feldern des [**teamsApp-Objekts**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern.</span><span class="sxs-lookup"><span data-stu-id="48bf1-153">To narrow the list of results, you can filter on any of the fields of [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="48bf1-154">✔ Ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist</span><span class="sxs-lookup"><span data-stu-id="48bf1-154">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="48bf1-155">**Microsoft Graph: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="48bf1-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="48bf1-156">**HTTP** GET-Anforderung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="48bf1-157">Diese Anforderung gibt ein leeres Array zurück, wenn die App nicht installiert ist, und ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) wenn die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="48bf1-157">This request returns an empty array if the app is not installed and an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if the app is installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="48bf1-158">✔ Installieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="48bf1-158">✔ Install your app</span></span>

<span data-ttu-id="48bf1-159">**Microsoft Graph:App** [für Benutzer installieren](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="48bf1-159">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="48bf1-160">**HTTP** POST-Anforderung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-160">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="48bf1-161">Wenn der Benutzer Microsoft Teams ausgeführt wird, wird die App-Installation sofort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="48bf1-161">If the user has Microsoft Teams running, app installation is seen immediately.</span></span> <span data-ttu-id="48bf1-162">Möglicherweise ist ein Neustart erforderlich, um die installierte App anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="48bf1-162">A restart may be required to view the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="48bf1-163">✔ Abrufen der **Chat-Id für Unterhaltungen**</span><span class="sxs-lookup"><span data-stu-id="48bf1-163">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="48bf1-164">Wenn Ihre App für den Benutzer installiert ist, empfängt der Bot eine Ereignisbenachrichtigung, die die erforderlichen Informationen zum Senden der `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) proaktiven Nachricht enthält.</span><span class="sxs-lookup"><span data-stu-id="48bf1-164">When your app is installed for the user, the bot receives a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that contains the necessary information to send the proactive message.</span></span>

<span data-ttu-id="48bf1-165">Der `chatId` kann auch wie folgt abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="48bf1-165">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="48bf1-166">**Microsoft Graph: Chat** [herunterladen](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="48bf1-166">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="48bf1-167">**1.** Sie müssen die . `{teamsAppInstallationId}`</span><span class="sxs-lookup"><span data-stu-id="48bf1-167">**1.** You must need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="48bf1-168">Wenn Sie nicht über diese Verfügen, verwenden Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="48bf1-168">If you don't have it, use the following:</span></span>

<span data-ttu-id="48bf1-169">**HTTP** GET-Anforderung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-169">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="48bf1-170">Die **id-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="48bf1-170">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="48bf1-171">**2. Stellen** Sie die folgende Anforderung zum Abrufen der `chatId` :</span><span class="sxs-lookup"><span data-stu-id="48bf1-171">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="48bf1-172">**HTTP GET-Anforderung** (Berechtigung — `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="48bf1-172">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="48bf1-173">Die **id-Eigenschaft** der Antwort ist die `chatId` .</span><span class="sxs-lookup"><span data-stu-id="48bf1-173">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="48bf1-174">Sie können auch die mit `chatId` der folgenden Anforderung abrufen, erfordert jedoch die umfassendere `Chat.Read.All` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="48bf1-174">You can also retrieve the `chatId` with the following request but it requires the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="48bf1-175">**HTTP GET-Anforderung** (Berechtigung — `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="48bf1-175">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="48bf1-176">✔ Proaktive Nachrichten senden</span><span class="sxs-lookup"><span data-stu-id="48bf1-176">✔ Send proactive messages</span></span>

<span data-ttu-id="48bf1-177">Ihr Bot kann [proaktive Nachrichten senden,](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) nachdem der Bot für einen Benutzer oder ein Team hinzugefügt wurde und alle Benutzerinformationen erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="48bf1-177">Your bot can [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) after the bot has been added for a user or a team and has received all the user information.</span></span>

## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="48bf1-178">Verwandtes Thema für Teams Administratoren</span><span class="sxs-lookup"><span data-stu-id="48bf1-178">Related topic for Teams administrators</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="48bf1-179">**Verwalten von Richtlinien für App-Setup in Teams**</span><span class="sxs-lookup"><span data-stu-id="48bf1-179">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a><span data-ttu-id="48bf1-180">Anzeigen zusätzlicher Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="48bf1-180">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="48bf1-181">**Teams proaktiver Messagingcodebeispiele**</span><span class="sxs-lookup"><span data-stu-id="48bf1-181">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
