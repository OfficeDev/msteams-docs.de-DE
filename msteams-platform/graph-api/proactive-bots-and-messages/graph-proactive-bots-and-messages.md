---
title: Verwenden von Microsoft Graph zur Aktivierung der proaktiven bot-Installation und-Nachrichten in Teams
description: Beschreibt proaktives Messaging in Microsoft Teams und die Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Microsoft Teams Proactive Messaging Chat-Installations Diagramm
ms.openlocfilehash: f1d2c51957eefbc548918210b843e408eb1107c8
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587741"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a><span data-ttu-id="e39ee-104">Aktivieren der proaktiven bot-Installation und proaktiver Nachrichten in Microsoft Graph-Teams (öffentliche Vorschau)</span><span class="sxs-lookup"><span data-stu-id="e39ee-104">Enable proactive bot installation and proactive messaging in Teams with Microsoft Graph (Public Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="e39ee-105">Öffentliche Vorschaubilder von Microsoft Graph sind für den frühzeitigen Zugriff und Feedback verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e39ee-105">Microsoft Graph public previews are available for early-access and feedback.</span></span> <span data-ttu-id="e39ee-106">Obwohl diese Version umfangreiche Tests unterzogen wurde, ist Sie nicht für die Verwendung in der Produktion vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="e39ee-107">Proaktives Messaging in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e39ee-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="e39ee-108">Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu starten.</span><span class="sxs-lookup"><span data-stu-id="e39ee-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="e39ee-109">Sie dienen zahlreichen Zwecken, beispielsweise beim Senden von Begrüßungsnachrichten, durchführen von Umfragen oder Umfragen sowie bei der Ausstrahlung organisationsweiter Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span>  <span data-ttu-id="e39ee-110">Proaktive Nachrichten in Microsoft Teams können entweder als **Ad-hoc** -oder **dialogbasierte** Unterhaltungen bereitgestellt werden:</span><span class="sxs-lookup"><span data-stu-id="e39ee-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="e39ee-111">Nachrichtentyp</span><span class="sxs-lookup"><span data-stu-id="e39ee-111">Message Type</span></span> | <span data-ttu-id="e39ee-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e39ee-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="e39ee-113">Ad-hoc-proaktive Nachricht</span><span class="sxs-lookup"><span data-stu-id="e39ee-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="e39ee-114">Der bot interject eine Nachricht, ohne den Unterhaltungs Fluss zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="e39ee-115">Dialog basierte proaktive Nachricht</span><span class="sxs-lookup"><span data-stu-id="e39ee-115">Dialog-based proactive message</span></span> | <span data-ttu-id="e39ee-116">Der bot erstellt einen neuen Dialog-Thread, übernimmt die Steuerung einer Unterhaltung, liefert die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.</span><span class="sxs-lookup"><span data-stu-id="e39ee-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

<span data-ttu-id="e39ee-117">*Siehe*, [senden proaktiver Benachrichtigungen an Benutzer SDK V4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)</span><span class="sxs-lookup"><span data-stu-id="e39ee-117">*See*, [Send proactive notifications to users SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)</span></span>

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="e39ee-118">Proaktive App-Installation in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e39ee-118">Proactive app installation in Teams</span></span>

<span data-ttu-id="e39ee-119">Bevor Ihr bot einen Benutzer proaktiv Nachrichten kann, muss er entweder als persönliche APP oder in einem Team installiert sein, in dem der Benutzer Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="e39ee-119">Before your bot can proactively message a user, it needs to be installed either as a personal app, or in a team where the user is a member.</span></span> <span data-ttu-id="e39ee-120">Gelegentlich müssen Sie Benutzer proaktiv Nachrichten, die noch _nicht_ mit Ihrer APP installiert oder zuvor interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="e39ee-120">At times,  you may need to proactively message users that have _not_ installed or previously interacted with your app.</span></span> <span data-ttu-id="e39ee-121">Zum Beispiel die Notwendigkeit, wichtige Informationen an alle Benutzer in Ihrer Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="e39ee-121">For instance, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="e39ee-122">Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren bot proaktiv für Ihre Benutzer zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e39ee-122">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="e39ee-123">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="e39ee-123">Permissions</span></span>

<span data-ttu-id="e39ee-124">Mit den [Ressourcentypen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) Berechtigungen von Microsoft Graph teamsAppInstallation können Sie den Installationslebenszyklus Ihrer APP für alle Benutzer (persönlichen) oder Team (Kanal) Bereiche innerhalb der Microsoft Teams-Plattform verwalten:</span><span class="sxs-lookup"><span data-stu-id="e39ee-124">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) permissions allow you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="e39ee-125">Anwendungsberechtigung</span><span class="sxs-lookup"><span data-stu-id="e39ee-125">Application permission</span></span> | <span data-ttu-id="e39ee-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e39ee-126">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="e39ee-127">Ermöglicht einer Teams-APP, sich selbst für einen beliebigen **Benutzer**ohne vorherige Anmeldung oder Verwendung zu lesen, zu installieren, zu aktualisieren und zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="e39ee-127">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="e39ee-128">Ermöglicht einer Teams-APP, sich selbst in jedem **Team**zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne vorherige Anmeldung oder Verwendung.</span><span class="sxs-lookup"><span data-stu-id="e39ee-128">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="e39ee-129">Um diese Berechtigungen zu verwenden, müssen Sie Ihrem App-Manifest einen [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) -Schlüssel mit den folgenden Werten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="e39ee-129">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="e39ee-130">**ID** – ihre Azure AD App-ID.</span><span class="sxs-lookup"><span data-stu-id="e39ee-130">**id**  — your Azure AD app id.</span></span>
> * <span data-ttu-id="e39ee-131">**Resource** – die Ressourcen-URL für die app.</span><span class="sxs-lookup"><span data-stu-id="e39ee-131">**resource** — the resource URL for the app.</span></span>
>

>[!NOTE]
>
> * <span data-ttu-id="e39ee-132">Ihr bot erfordert keine _Benutzer Delegierten_ Berechtigungen für die _Anwendung_ , da die Installation nicht für sich selbst, sondern für andere ist.</span><span class="sxs-lookup"><span data-stu-id="e39ee-132">Your bot requires _application_ not _user delegated_ permissions because the installation is not for yourself but for others.</span></span>
>
> * <span data-ttu-id="e39ee-133">Ein Azure AD mandantenadministrator muss [explizit Berechtigungen für eine Anwendung erteilen](/graph/security-authorization#grant-permissions-to-an-application).</span><span class="sxs-lookup"><span data-stu-id="e39ee-133">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="e39ee-134">Nachdem einer Anwendung Berechtigungen erteilt wurden, erhalten _alle_ Mitglieder des Azure AD Mandanten die gewährten Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-134">After an application is granted permissions, _all_ members of the Azure AD tenant will gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="e39ee-135">Aktivieren der proaktiven App-Installation und des Messaging</span><span class="sxs-lookup"><span data-stu-id="e39ee-135">Enable proactive app installation and messaging</span></span>

 > [!IMPORTANT]
><span data-ttu-id="e39ee-136">In Microsoft Graph werden nur apps installiert, die im [App-Katalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) Ihres Unternehmens oder in [AppSource](https://appsource.microsoft.com/)veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="e39ee-136">Microsoft Graph will only install apps published within your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="e39ee-137">✔ Erstellen und Veröffentlichen Ihres proaktiven Messaging-bot für Teams</span><span class="sxs-lookup"><span data-stu-id="e39ee-137">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="e39ee-138">Für die ersten Schritte benötigen Sie einen [bot für Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [proaktiven Messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) Funktionen, die im [App-Katalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) Ihres Unternehmens oder in [AppSource](https://appsource.microsoft.com/) [veröffentlicht](../../concepts/deploy-and-publish/overview.md) werden.</span><span class="sxs-lookup"><span data-stu-id="e39ee-138">To get started, you will need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities and  [published](../../concepts/deploy-and-publish/overview.md) in your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

>[!TIP]
> <span data-ttu-id="e39ee-139">Die produktionsfertige [**Unternehmens-Communicator**](../..//samples/app-templates.md#company-communicator) -App-Vorlage aktiviert Broadcastnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven bot-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="e39ee-139">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template enables broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="e39ee-140">✔ Abrufen der `teamsAppId` für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="e39ee-140">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="e39ee-141">**1.** Sie benötigen die `teamsAppId` für die nächsten Schritte.</span><span class="sxs-lookup"><span data-stu-id="e39ee-141">**1.** You will need the `teamsAppId`  for the next steps.</span></span>

<span data-ttu-id="e39ee-142">Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="e39ee-142">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="e39ee-143">**Microsoft Graph-Seitenreferenz:** [teamsApp Resource Type](/graph/api/resources/teamsapp?view=graph-rest-1.0)</span><span class="sxs-lookup"><span data-stu-id="e39ee-143">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0)</span></span>

<span data-ttu-id="e39ee-144">**HTTP Get** -Anforderung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-144">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="e39ee-145">Die Anforderung gibt ein `teamsApp` -Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="e39ee-145">The request will return a `teamsApp`  object.</span></span> <span data-ttu-id="e39ee-146">Das zurückgegebene Objekt ist `id` die vom Katalog generierte APP-ID der APP und unterscheidet sich von der ID:, die Sie in Ihrem Teams-App-Manifest angegeben haben:</span><span class="sxs-lookup"><span data-stu-id="e39ee-146">The returned object's `id`  is the app's catalog generated app id and is different from the "id:" that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="e39ee-147">**2.** Wenn Ihre APP bereits für einen Benutzer im persönlichen Bereich hochgeladen/quer geladene wurde, können Sie die `teamsAppId` wie folgt abrufen:</span><span class="sxs-lookup"><span data-stu-id="e39ee-147">**2.**  If your app has already been uploaded/sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="e39ee-148">**Microsoft Graph-Seitenreferenz:** [Auflisten von apps, die für den Benutzer installiert](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http) sind</span><span class="sxs-lookup"><span data-stu-id="e39ee-148">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="e39ee-149">**HTTP Get** -Anforderung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-149">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="e39ee-150">**3.** Wenn Ihre APP bereits für einen Kanal im Teambereich hochgeladen/quer geladene wurde, können Sie die `teamsAppId` wie folgt abrufen:</span><span class="sxs-lookup"><span data-stu-id="e39ee-150">**3.** If your app has already been uploaded/sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="e39ee-151">**Microsoft Graph-Seitenreferenz:** [Auflisten von apps im Team](/graph/api/teamsappinstallation-list?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="e39ee-151">**Microsoft Graph page reference:** [List apps in team](/graph/api/teamsappinstallation-list?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="e39ee-152">**HTTP Get** -Anforderung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-152">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{manifestId}'
```

>[!TIP]
> <span data-ttu-id="e39ee-153">Sie können nach einem der Felder des [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0) -Objekts filtern, um die Ergebnisliste einzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-153">You can filter on any of the fields of the [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0) object to narrow the list of results.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="e39ee-154">✔ Bestimmen, ob Ihr bot derzeit für einen Nachrichtenempfänger installiert ist</span><span class="sxs-lookup"><span data-stu-id="e39ee-154">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="e39ee-155">**Microsoft Graph-Seitenreferenz:** [Auflisten von apps, die für den Benutzer installiert](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http) sind</span><span class="sxs-lookup"><span data-stu-id="e39ee-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/user-list-teamsappinstallation?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="e39ee-156">**HTTP Get** -Anforderung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="e39ee-157">Diese Anforderung gibt ein leeres Array zurück, wenn die APP nicht installiert ist, oder ein Array mit einem einzelnen [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-beta) -Objekt, wenn es installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="e39ee-157">This request will return an empty array if the app is not installed, or an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-beta) object if it has been installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="e39ee-158">✔ Installieren Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="e39ee-158">✔ Install your app</span></span>

<span data-ttu-id="e39ee-159">**Microsoft Graph-Referenz:** [Installieren der APP für den Benutzer](/graph/api/user-add-teamsappinstallation?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="e39ee-159">**Microsoft Graph reference:** [Install app for user](/graph/api/user-add-teamsappinstallation?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="e39ee-160">**Http Post** -Anforderung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-160">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/beta/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="e39ee-161">Wenn der Benutzer Microsoft Teams ausführt, wird möglicherweise sofort die APP-Installation angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e39ee-161">If the user has Microsoft Teams running, they may see the app install immediately.</span></span> <span data-ttu-id="e39ee-162">Alternativ kann ein Neustart erforderlich sein, um die installierte App anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-162">Alternatively,  a  restart may be necessary to see the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="e39ee-163">✔ Abrufen der Unterhaltungs- **Chat** -Funktion</span><span class="sxs-lookup"><span data-stu-id="e39ee-163">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="e39ee-164">Wenn Ihre APP für den Benutzer installiert ist, erhält der bot eine `conversationUpdate` [Ereignisbenachrichtigung](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) , die die erforderlichen Informationen zum Senden der proaktiven Nachricht enthalten wird.</span><span class="sxs-lookup"><span data-stu-id="e39ee-164">When your app is installed for the user, the bot will receive a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that will contain the necessary information to send the proactive message.</span></span>

<span data-ttu-id="e39ee-165">Die `chatId` kann auch wie folgt abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="e39ee-165">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="e39ee-166">**Microsoft Graph-Referenz:** [Chat abrufen](/graph/api/chat-get?view=graph-rest-beta&tabs=http)</span><span class="sxs-lookup"><span data-stu-id="e39ee-166">**Microsoft Graph reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http)</span></span>

<span data-ttu-id="e39ee-167">**1.** Sie benötigen Ihre apps `{teamsAppInstallationId}` .</span><span class="sxs-lookup"><span data-stu-id="e39ee-167">**1.** You will need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="e39ee-168">Wenn Sie diesen nicht haben, verwenden Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e39ee-168">If you don't have it, use the following:</span></span>

<span data-ttu-id="e39ee-169">**HTTP Get** -Anforderung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-169">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="e39ee-170">Die **ID** -Eigenschaft der Antwort ist die `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="e39ee-170">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="e39ee-171">**2.** führen Sie die folgende Anforderung aus, um Folgendes abzurufen `chatId` :</span><span class="sxs-lookup"><span data-stu-id="e39ee-171">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="e39ee-172">**HTTP Get** -Anforderung (Berechtigung `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="e39ee-172">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="e39ee-173">Die **ID** -Eigenschaft der Antwort ist die `chatId` .</span><span class="sxs-lookup"><span data-stu-id="e39ee-173">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="e39ee-174">Alternativ können Sie die `chatId` mit der folgenden Anforderung abrufen, aber Sie erfordert die breitere `Chat.Read.All` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="e39ee-174">Alternately, you can retrieve the `chatId`  with the request below, but it will require the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="e39ee-175">**HTTP Get** -Anforderung (Berechtigung `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="e39ee-175">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="e39ee-176">✔ Senden von proaktiven Nachrichten</span><span class="sxs-lookup"><span data-stu-id="e39ee-176">✔ Send proactive messages</span></span>

<span data-ttu-id="e39ee-177">Sobald Ihr bot für einen Benutzer oder ein Team hinzugefügt wurde und die erforderlichen Benutzerinformationen erworben hat, kann er mit dem [senden proaktiver Nachrichten](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp)beginnen.</span><span class="sxs-lookup"><span data-stu-id="e39ee-177">Once your bot has been added for a user or team and has acquired the necessary user  information, it can begin to [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp).</span></span>

# <a name="c--net"></a>[<span data-ttu-id="e39ee-178">C#/.net</span><span class="sxs-lookup"><span data-stu-id="e39ee-178">C# / .NET</span></span>](#tab/csharp)

<span data-ttu-id="e39ee-179">Der folgende Codeausschnitt stammt aus den [Microsoft bot Framework-Beispielen für C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span><span class="sxs-lookup"><span data-stu-id="e39ee-179">The following code snippet is from the [Microsoft Bot Framework Samples for C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span></span>

```csharp
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.Bot.Builder;
using Microsoft.Bot.Schema;

namespace Microsoft.BotBuilderSamples
{
    public class ProactiveBot : ActivityHandler
    {
        // Message to send to users when the bot receives a Conversation Update event
        private const string WelcomeMessage = "Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.";

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

        public ProactiveBot(ConcurrentDictionary<string, ConversationReference> conversationReferences)
        {
            _conversationReferences = conversationReferences;
        }

        private void AddConversationReference(Activity activity)
        {
            var conversationReference = activity.GetConversationReference();
            _conversationReferences.AddOrUpdate(conversationReference.User.Id, conversationReference, (key, newValue) => conversationReference);
        }

        protected override Task OnConversationUpdateActivityAsync(ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            return base.OnConversationUpdateActivityAsync(turnContext, cancellationToken);
        }

        protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            foreach (var member in membersAdded)
            {
                // Greet anyone that was not the target (recipient) of this message.
                if (member.Id != turnContext.Activity.Recipient.Id)
                {
                    await turnContext.SendActivityAsync(MessageFactory.Text(WelcomeMessage), cancellationToken);
                }
            }
        }

        protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
        {
            AddConversationReference(turnContext.Activity as Activity);

            // Echo back what the user said
            await turnContext.SendActivityAsync(MessageFactory.Text($"You sent '{turnContext.Activity.Text}'"), cancellationToken);
        }
    }
}
```

# <a name="javascript"></a>[<span data-ttu-id="e39ee-180">JavaScript</span><span class="sxs-lookup"><span data-stu-id="e39ee-180">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="e39ee-181">Der folgende Codeausschnitt stammt aus den [Microsoft bot Framework-Beispielen für JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span><span class="sxs-lookup"><span data-stu-id="e39ee-181">The following code snippet is from the [Microsoft Bot Framework Samples for JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span></span>

```javascript
const { ActivityHandler, TurnContext } = require('botbuilder');

class ProactiveBot extends ActivityHandler {
    constructor(conversationReferences) {
        super();

        // Dependency injected dictionary for storing ConversationReference objects used in NotifyController to proactively message users
        this.conversationReferences = conversationReferences;

        this.onConversationUpdate(async (context, next) => {
            this.addConversationReference(context.activity);

            await next();
        });

        this.onMembersAdded(async (context, next) => {
            const membersAdded = context.activity.membersAdded;
            for (let cnt = 0; cnt < membersAdded.length; cnt++) {
                if (membersAdded[cnt].id !== context.activity.recipient.id) {
                    const welcomeMessage = 'Welcome to the Proactive Bot sample.  Navigate to http://localhost:3978/api/notify to proactively message everyone who has previously messaged this bot.';
                    await context.sendActivity(welcomeMessage);
                }
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });

        this.onMessage(async (context, next) => {
            this.addConversationReference(context.activity);

            // Echo back what the user said
            await context.sendActivity(`You sent '${ context.activity.text }'`);
            await next();
        });
    }

    addConversationReference(activity) {
        const conversationReference = TurnContext.getConversationReference(activity);
        this.conversationReferences[conversationReference.conversation.id] = conversationReference;
    }
}

module.exports.ProactiveBot = ProactiveBot;

```
---

## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="e39ee-182">Verwandtes Thema für Microsoft Teams-Administratoren</span><span class="sxs-lookup"><span data-stu-id="e39ee-182">Related topic for Teams administrators</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e39ee-183">**Verwalten von App-Setup Richtlinien in Microsoft Teams**</span><span class="sxs-lookup"><span data-stu-id="e39ee-183">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a><span data-ttu-id="e39ee-184">Anzeigen zusätzlicher Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="e39ee-184">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e39ee-185">**Proaktive Messaging-Codebeispiele für Teams**</span><span class="sxs-lookup"><span data-stu-id="e39ee-185">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
