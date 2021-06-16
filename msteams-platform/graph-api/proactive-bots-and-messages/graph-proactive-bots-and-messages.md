---
title: Verwenden von Microsoft Graph zum Autorisieren proaktiver Bot-Installation und Messaging in Teams
description: Beschreibt proaktives Messaging in Teams und Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Proaktive Chatinstallation von Teams Graph
ms.openlocfilehash: db36c64e557b90699bb09e77dc67ca4c9a8e5853
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949665"
---
# <a name="proactive-installation-of-apps-using-graph-api-to-send-messages"></a><span data-ttu-id="add2a-104">Proaktive Installation von Apps mit Graph-API zum Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="add2a-104">Proactive installation of apps using Graph API to send messages</span></span>

>[!IMPORTANT]
> <span data-ttu-id="add2a-105">Microsoft Graph und Microsoft Teams öffentliche Vorschauen stehen für frühzeitigen Zugriff und Feedback zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="add2a-105">Microsoft Graph and Microsoft Teams public previews are available for early access and feedback.</span></span> <span data-ttu-id="add2a-106">Obwohl diese Version umfangreichen Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="add2a-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="add2a-107">Proaktives Messaging in Teams</span><span class="sxs-lookup"><span data-stu-id="add2a-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="add2a-108">Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu starten.</span><span class="sxs-lookup"><span data-stu-id="add2a-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="add2a-109">Sie dienen vielen Zwecken, z. B. dem Senden von Willkommensnachrichten, der Durchführung von Umfragen oder Umfragen und dem Senden organisationsweiter Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="add2a-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span> <span data-ttu-id="add2a-110">Proaktive Nachrichten in Teams können als **Ad-hoc-** oder **dialogbasierte** Unterhaltungen übermittelt werden:</span><span class="sxs-lookup"><span data-stu-id="add2a-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="add2a-111">Nachrichtentyp</span><span class="sxs-lookup"><span data-stu-id="add2a-111">Message Type</span></span> | <span data-ttu-id="add2a-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="add2a-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="add2a-113">Proaktive Ad-hoc-Nachricht</span><span class="sxs-lookup"><span data-stu-id="add2a-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="add2a-114">Der Bot übergibt eine Nachricht, ohne den Unterhaltungsfluss zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="add2a-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="add2a-115">Dialogbasierte proaktive Nachricht</span><span class="sxs-lookup"><span data-stu-id="add2a-115">Dialog-based proactive message</span></span> | <span data-ttu-id="add2a-116">Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, übermittelt die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.</span><span class="sxs-lookup"><span data-stu-id="add2a-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="add2a-117">Proaktive App-Installation in Teams</span><span class="sxs-lookup"><span data-stu-id="add2a-117">Proactive app installation in Teams</span></span>

<span data-ttu-id="add2a-118">Bevor Ihr Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="add2a-118">Before your bot can proactively message a user, it must be installed either as a personal app or in a team where the user is a member.</span></span> <span data-ttu-id="add2a-119">Manchmal müssen Sie proaktive Nachrichten an Benutzer senden, die Ihre App nicht installiert oder zuvor mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="add2a-119">At times, you need to proactively message users that have not installed or previously interacted with your app.</span></span> <span data-ttu-id="add2a-120">Beispielsweise müssen wichtige Informationen an alle Personen in Ihrer Organisation ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="add2a-120">For example, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="add2a-121">Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.</span><span class="sxs-lookup"><span data-stu-id="add2a-121">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="add2a-122">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="add2a-122">Permissions</span></span>

<span data-ttu-id="add2a-123">Microsoft Graph [TeamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) helfen Ihnen, den Installationslebenszyklus Ihrer App für alle Benutzer- (persönlichen) oder Teambereiche (Kanal) innerhalb der Microsoft Teams Plattform zu verwalten:</span><span class="sxs-lookup"><span data-stu-id="add2a-123">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions helps you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="add2a-124">Anwendungsberechtigung</span><span class="sxs-lookup"><span data-stu-id="add2a-124">Application permission</span></span> | <span data-ttu-id="add2a-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="add2a-125">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="add2a-126">Ermöglicht es einer Teams App, sich selbst für jeden **Benutzer** zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anzumelden oder zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="add2a-126">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="add2a-127">Ermöglicht es einer Teams App, sich selbst in einem **Beliebigen Team** zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anzumelden oder zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="add2a-127">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="add2a-128">Um diese Berechtigungen zu verwenden, müssen Sie Ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="add2a-128">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="add2a-129">**id** – Ihre Azure AD-App-ID.</span><span class="sxs-lookup"><span data-stu-id="add2a-129">**id** — your Azure AD app ID.</span></span>
> * <span data-ttu-id="add2a-130">**ressource** – die Ressourcen-URL für die App.</span><span class="sxs-lookup"><span data-stu-id="add2a-130">**resource** — the resource URL for the app.</span></span>
>
>[!NOTE]
>
> * <span data-ttu-id="add2a-131">Ihr Bot erfordert Eine Anwendung und keine delegierten Benutzerberechtigungen, da die Installation für andere benutzerdelegiert ist.</span><span class="sxs-lookup"><span data-stu-id="add2a-131">Your bot requires application and not user delegated permissions because the installation is for others.</span></span>
>
> * <span data-ttu-id="add2a-132">Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application)</span><span class="sxs-lookup"><span data-stu-id="add2a-132">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="add2a-133">Nachdem einer Anwendung Berechtigungen erteilt wurden, erhalten alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="add2a-133">After an application is granted permissions, all members of the Azure AD tenant gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="add2a-134">Proaktive App-Installation und Messaging aktivieren</span><span class="sxs-lookup"><span data-stu-id="add2a-134">Enable proactive app installation and messaging</span></span>

> [!IMPORTANT]
><span data-ttu-id="add2a-135">Microsoft Graph können nur Apps installieren, die im App Store Ihrer Organisation oder im Teams Store veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="add2a-135">Microsoft Graph can only install apps published to your organization's app store or the Teams store.</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="add2a-136">✔ Erstellen und Veröffentlichen Ihres proaktiven Messaging-Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="add2a-136">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="add2a-137">Um zu beginnen, benötigen Sie einen [Bot für Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [proaktiven Messagingfunktionen,](../../concepts/bots/bot-conversations/bots-conv-proactive.md) die sich im [App Store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) Ihrer Organisation oder im Teams [Store befinden.](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store)</span><span class="sxs-lookup"><span data-stu-id="add2a-137">To get started, you need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities that's in your [organization's app store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-your-org) or the [Teams store](../../concepts/deploy-and-publish/apps-publish-overview.md#publish-your-app-to-the-teams-store).</span></span>

>[!TIP]
> <span data-ttu-id="add2a-138">Die produktionsbereite [**Unternehmens-Communicator-App-Vorlage**](../..//samples/app-templates.md#company-communicator) ermöglicht Übertragungsnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven Bot-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="add2a-138">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template permits broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="add2a-139">✔ Abrufen der `teamsAppId` App</span><span class="sxs-lookup"><span data-stu-id="add2a-139">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="add2a-140">**1.** Sie benötigen die `teamsAppId` für die nächsten Schritte.</span><span class="sxs-lookup"><span data-stu-id="add2a-140">**1.** You need the `teamsAppId` for the next steps.</span></span>

<span data-ttu-id="add2a-141">Dies `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="add2a-141">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="add2a-142">**Microsoft Graph-Seitenreferenz:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="add2a-142">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="add2a-143">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="add2a-143">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="add2a-144">Die Anforderung muss ein `teamsApp` Objekt zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="add2a-144">The request must return a `teamsApp` object.</span></span> <span data-ttu-id="add2a-145">Das zurückgegebene Objekt `id` ist die vom App-Katalog generierte App-ID und unterscheidet sich von der ID, die Sie in Ihrem Teams App-Manifest angegeben haben:</span><span class="sxs-lookup"><span data-stu-id="add2a-145">The returned object `id` is the app's catalog generated app ID and is different from the ID that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="add2a-146">**2.**  Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder quergeladen wurde, können Sie Folgendes `teamsAppId` abrufen:</span><span class="sxs-lookup"><span data-stu-id="add2a-146">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="add2a-147">**Microsoft Graph-Seitenverweis:** [Apps auflisten, die für den Benutzer installiert sind](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="add2a-147">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="add2a-148">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="add2a-148">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="add2a-149">**3.** Wenn Ihre App für einen Kanal im Teambereich hochgeladen oder quergeladen wurde, können Sie Folgendes `teamsAppId` abrufen:</span><span class="sxs-lookup"><span data-stu-id="add2a-149">**3.** If your app has been uploaded or sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="add2a-150">**Microsoft Graph-Seitenverweis:** [Apps im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="add2a-150">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="add2a-151">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="add2a-151">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="add2a-152">Um die Liste der Ergebnisse einzugrenzen, können Sie nach einem beliebigen Feld des [**teamsApp-Objekts**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern.</span><span class="sxs-lookup"><span data-stu-id="add2a-152">To narrow the list of results, you can filter on any of the fields of [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="add2a-153">✔ Ermitteln, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist</span><span class="sxs-lookup"><span data-stu-id="add2a-153">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="add2a-154">**Microsoft Graph-Seitenverweis:** [Apps auflisten, die für den Benutzer installiert sind](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="add2a-154">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="add2a-155">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="add2a-155">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="add2a-156">Diese Anforderung gibt ein leeres Array zurück, wenn die App nicht installiert ist, und ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) wenn die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="add2a-156">This request returns an empty array if the app is not installed and an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if the app is installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="add2a-157">✔ Installieren Der App</span><span class="sxs-lookup"><span data-stu-id="add2a-157">✔ Install your app</span></span>

<span data-ttu-id="add2a-158">**Microsoft Graph-Seitenverweis:** [Installieren der App für den Benutzer](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="add2a-158">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="add2a-159">**HTTP POST-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="add2a-159">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
Content-Type: application/json

{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="add2a-160">Wenn der Benutzer Microsoft Teams ausgeführt hat, wird die App-Installation sofort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="add2a-160">If the user has Microsoft Teams running, app installation is seen immediately.</span></span> <span data-ttu-id="add2a-161">Möglicherweise ist ein Neustart erforderlich, um die installierte App anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="add2a-161">A restart may be required to view the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="add2a-162">✔ Abrufen der **Chat-ID** für Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="add2a-162">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="add2a-163">Wenn Ihre App für den Benutzer installiert ist, erhält der Bot eine `conversationUpdate` [Ereignisbenachrichtigung,](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) die die erforderlichen Informationen zum Senden der proaktiven Nachricht enthält.</span><span class="sxs-lookup"><span data-stu-id="add2a-163">When your app is installed for the user, the bot receives a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that contains the necessary information to send the proactive message.</span></span>

<span data-ttu-id="add2a-164">Dies `chatId` kann auch wie folgt abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="add2a-164">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="add2a-165">**Microsoft Graph-Seitenverweis:** [Chat abrufen](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="add2a-165">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="add2a-166">**1.** Sie müssen die App `{teamsAppInstallationId}` benötigen.</span><span class="sxs-lookup"><span data-stu-id="add2a-166">**1.** You must need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="add2a-167">Wenn Sie es nicht haben, verwenden Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="add2a-167">If you don't have it, use the following:</span></span>

<span data-ttu-id="add2a-168">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="add2a-168">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="add2a-169">Die **ID-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="add2a-169">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="add2a-170">**2.** Stellen Sie die folgende Anforderung, um Folgendes `chatId` abzurufen:</span><span class="sxs-lookup"><span data-stu-id="add2a-170">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="add2a-171">**HTTP GET-Anforderung** (Berechtigung — `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="add2a-171">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="add2a-172">Die **ID-Eigenschaft** der Antwort ist die `chatId` .</span><span class="sxs-lookup"><span data-stu-id="add2a-172">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="add2a-173">Sie können dies auch `chatId` mit der folgenden Anforderung abrufen, aber sie erfordert die umfassendere `Chat.Read.All` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="add2a-173">You can also retrieve the `chatId` with the following request but it requires the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="add2a-174">**HTTP GET-Anforderung** (Berechtigung — `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="add2a-174">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="add2a-175">✔ Proaktive Nachrichten senden</span><span class="sxs-lookup"><span data-stu-id="add2a-175">✔ Send proactive messages</span></span>

<span data-ttu-id="add2a-176">Ihr Bot kann [proaktive Nachrichten senden,](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) nachdem der Bot für einen Benutzer oder ein Team hinzugefügt wurde und alle Benutzerinformationen erhalten hat.</span><span class="sxs-lookup"><span data-stu-id="add2a-176">Your bot can [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) after the bot has been added for a user or a team and has received all the user information.</span></span>

## <a name="see-also"></a><span data-ttu-id="add2a-177">Weitere Artikel</span><span class="sxs-lookup"><span data-stu-id="add2a-177">See also</span></span>

* [<span data-ttu-id="add2a-178">**Verwalten von App-Setuprichtlinien in Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="add2a-178">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)
* [<span data-ttu-id="add2a-179">Senden proaktiver Benachrichtigungen an Benutzer SDK v4</span><span class="sxs-lookup"><span data-stu-id="add2a-179">Send proactive notifications to users SDK v4</span></span>](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)

## <a name="view-additional-code-samples"></a><span data-ttu-id="add2a-180">Anzeigen zusätzlicher Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="add2a-180">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="add2a-181">**Codebeispiele für proaktives Messaging Teams**</span><span class="sxs-lookup"><span data-stu-id="add2a-181">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
