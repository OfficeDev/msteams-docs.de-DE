---
title: Verwenden von Microsoft Graph zum Aktivieren der proaktiven Botinstallation und -messaging in Teams
description: Beschreibt proaktives Messaging in Teams und die Implementierung.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Graph zur proaktiven Messaging-Chatinstallation für Teams
ms.openlocfilehash: 4f26b4d2f4e82fcf50b7a35c46bcd07e5afecf19
ms.sourcegitcommit: b99ed616db734371e4af4594b7e895c5b05737c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2021
ms.locfileid: "50162894"
---
# <a name="enable-proactive-bot-installation-and-proactive-messaging-in-teams-with-microsoft-graph-public-preview"></a><span data-ttu-id="9f044-104">Aktivieren einer proaktiven Botinstallation und proaktivem Messaging in Teams mit Microsoft Graph (Public Preview)</span><span class="sxs-lookup"><span data-stu-id="9f044-104">Enable proactive bot installation and proactive messaging in Teams with Microsoft Graph (Public Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="9f044-105">Microsoft Graph und Microsoft Teams public previews are available for early-access and feedback.</span><span class="sxs-lookup"><span data-stu-id="9f044-105">Microsoft Graph and Microsoft Teams public previews are available for early-access and feedback.</span></span> <span data-ttu-id="9f044-106">Obwohl diese Version umfassenden Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="9f044-106">Although this release has undergone extensive testing, it is not intended for use in production.</span></span>

## <a name="proactive-messaging-in-teams"></a><span data-ttu-id="9f044-107">Proaktives Messaging in Teams</span><span class="sxs-lookup"><span data-stu-id="9f044-107">Proactive messaging in Teams</span></span>

<span data-ttu-id="9f044-108">Proaktive Nachrichten werden von Bots initiiert, um Unterhaltungen mit einem Benutzer zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="9f044-108">Proactive messages are initiated by bots to start conversations with a user.</span></span> <span data-ttu-id="9f044-109">Sie dienen vielen Zwecken, z. B. dem Senden von Begrüßungsnachrichten, dem Durchführen von Umfragen oder Umfragen und der Übertragung organisationsweiter Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="9f044-109">They serve many purposes including sending welcome messages, conducting surveys or polls, and broadcasting organization-wide notifications.</span></span>  <span data-ttu-id="9f044-110">Proaktive Nachrichten in Teams können als **Ad-hoc-** oder **dialogbasierte Unterhaltungen übermittelt** werden:</span><span class="sxs-lookup"><span data-stu-id="9f044-110">Proactive messages in Teams can be delivered as either **ad-hoc** or **dialog-based** conversations:</span></span>

|<span data-ttu-id="9f044-111">Nachrichtentyp</span><span class="sxs-lookup"><span data-stu-id="9f044-111">Message Type</span></span> | <span data-ttu-id="9f044-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9f044-112">Description</span></span> |
|----------------|-------------- |
|<span data-ttu-id="9f044-113">Proaktive Ad-hoc-Nachricht</span><span class="sxs-lookup"><span data-stu-id="9f044-113">Ad-hoc proactive message</span></span>| <span data-ttu-id="9f044-114">Der Bot interjects a message without interrupting the conversation flow.</span><span class="sxs-lookup"><span data-stu-id="9f044-114">The bot interjects a message without interrupting the conversation flow.</span></span>|
|<span data-ttu-id="9f044-115">Dialogbasierte proaktive Nachricht</span><span class="sxs-lookup"><span data-stu-id="9f044-115">Dialog-based proactive message</span></span> | <span data-ttu-id="9f044-116">Der Bot erstellt einen neuen Dialogthread, übernimmt die Kontrolle über eine Unterhaltung, übermittelt die proaktive Nachricht, schließt und gibt die Steuerung an das vorherige Dialogfeld zurück.</span><span class="sxs-lookup"><span data-stu-id="9f044-116">The bot creates a new dialog thread, takes control of a conversation, delivers the proactive message, closes, and returns control to the previous dialog.</span></span>|

<span data-ttu-id="9f044-117">*Siehe*, [proaktive Benachrichtigungen an Benutzer SDK v4 senden](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-117">*See*, [Send proactive notifications to users SDK v4](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)</span></span>

## <a name="proactive-app-installation-in-teams"></a><span data-ttu-id="9f044-118">Proaktive App-Installation in Teams</span><span class="sxs-lookup"><span data-stu-id="9f044-118">Proactive app installation in Teams</span></span>

<span data-ttu-id="9f044-119">Bevor Ihr Bot proaktiv eine Nachricht an einen Benutzer senden kann, muss er entweder als persönliche App oder in einem Team installiert werden, in dem der Benutzer Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="9f044-119">Before your bot can proactively message a user, it needs to be installed either as a personal app, or in a team where the user is a member.</span></span> <span data-ttu-id="9f044-120">Manchmal müssen Sie benutzer, die nicht  installiert oder zuvor mit Ihrer App interagiert haben, proaktiv nachrichten.</span><span class="sxs-lookup"><span data-stu-id="9f044-120">At times,  you may need to proactively message users that have _not_ installed or previously interacted with your app.</span></span> <span data-ttu-id="9f044-121">Beispielsweise müssen wichtige Informationen an alle In ihrer Organisation gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9f044-121">For instance, the need to message vital information to everyone in your organization.</span></span> <span data-ttu-id="9f044-122">Für solche Szenarien können Sie die Microsoft Graph-API verwenden, um Ihren Bot proaktiv für Ihre Benutzer zu installieren.</span><span class="sxs-lookup"><span data-stu-id="9f044-122">For such scenarios, you can use the Microsoft Graph API to proactively install your bot for your users.</span></span>

## <a name="permissions"></a><span data-ttu-id="9f044-123">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="9f044-123">Permissions</span></span>

<span data-ttu-id="9f044-124">Mit Microsoft Graph [teamsAppInstallation-Ressourcentypberechtigungen](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) können Sie den Installationslebenszyklus Ihrer App für alle Benutzer- oder Teambereiche (Kanal) innerhalb der Microsoft Teams-Plattform verwalten:</span><span class="sxs-lookup"><span data-stu-id="9f044-124">Microsoft Graph [teamsAppInstallation resource type](/graph/api/resources/teamsappinstallation?view=graph-rest-1.0&preserve-view=true) permissions allow you to manage your app's installation lifecycle for all user (personal) or team (channel) scopes within the Microsoft Teams platform:</span></span>

|<span data-ttu-id="9f044-125">Anwendungsberechtigung</span><span class="sxs-lookup"><span data-stu-id="9f044-125">Application permission</span></span> | <span data-ttu-id="9f044-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9f044-126">Description</span></span>|
|------------------|---------------------|
|`TeamsAppInstallation.ReadWriteSelfForUser.All`|<span data-ttu-id="9f044-127">Ermöglicht einer Teams-App, sich selbst für jeden Benutzer ohne vorherige Anmeldung oder Verwendung zu lesen, zu installieren, zu aktualisieren und zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="9f044-127">Allows a Teams app to read, install, upgrade, and uninstall itself for any **user**, without prior sign in or use.</span></span>|
|`TeamsAppInstallation.ReadWriteSelfForTeam.All`|<span data-ttu-id="9f044-128">Ermöglicht einer Teams-App, sich selbst in einem beliebigen Team zu lesen, zu installieren, zu aktualisieren und zu deinstallieren, ohne sich vorher anmelden oder verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="9f044-128">Allows a Teams app to read, install, upgrade, and uninstall itself in any **team**, without prior sign in or use.</span></span>|

<span data-ttu-id="9f044-129">Um diese Berechtigungen zu verwenden, müssen Sie ihrem [App-Manifest einen webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="9f044-129">To use these permissions, you must add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>
> [!div class="checklist"]
> [!div class="checklist"]
>
> * <span data-ttu-id="9f044-130">**id**  – Ihre Azure AD-App-ID.</span><span class="sxs-lookup"><span data-stu-id="9f044-130">**id**  — your Azure AD app id.</span></span>
> * <span data-ttu-id="9f044-131">**-Ressource** – die Ressourcen-URL für die App.</span><span class="sxs-lookup"><span data-stu-id="9f044-131">**resource** — the resource URL for the app.</span></span>
>

>[!NOTE]
>
> * <span data-ttu-id="9f044-132">Ihr Bot erfordert _keine delegierten_ Berechtigungen _der_ Anwendung, da die Installation nicht für sie selbst, sondern für andere personen ist.</span><span class="sxs-lookup"><span data-stu-id="9f044-132">Your bot requires _application_ not _user delegated_ permissions because the installation is not for yourself but for others.</span></span>
>
> * <span data-ttu-id="9f044-133">Ein Azure AD-Mandantenadministrator muss [einer Anwendung explizit Berechtigungen erteilen.](/graph/security-authorization#grant-permissions-to-an-application)</span><span class="sxs-lookup"><span data-stu-id="9f044-133">An Azure AD tenant administrator must [explicitly grant permissions to an application](/graph/security-authorization#grant-permissions-to-an-application).</span></span> <span data-ttu-id="9f044-134">Nachdem einer Anwendung Berechtigungen erteilt wurden, _erhalten_ alle Mitglieder des Azure AD-Mandanten die erteilten Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="9f044-134">After an application is granted permissions, _all_ members of the Azure AD tenant will gain the granted permissions.</span></span>

## <a name="enable-proactive-app-installation-and-messaging"></a><span data-ttu-id="9f044-135">Aktivieren der proaktiven Installation und Messaging von Apps</span><span class="sxs-lookup"><span data-stu-id="9f044-135">Enable proactive app installation and messaging</span></span>

 > [!IMPORTANT]
><span data-ttu-id="9f044-136">Microsoft Graph installiert nur Apps, die [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) im App-Katalog Ihrer Organisation oder in [AppSource veröffentlicht wurden.](https://appsource.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="9f044-136">Microsoft Graph will only install apps published within your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

### <a name="-create-and-publish-your-proactive-messaging-bot-for-teams"></a><span data-ttu-id="9f044-137">✔ Erstellen und Veröffentlichen Ihres proaktiven Messaging-Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="9f044-137">✔ Create and publish your proactive messaging bot for Teams</span></span>

<span data-ttu-id="9f044-138">Für die ersten Schritte benötigen Sie [](../../concepts/bots/bot-conversations/bots-conv-proactive.md) einen Bot [](../../concepts/deploy-and-publish/overview.md) für [Teams](../../bots/how-to/create-a-bot-for-teams.md) mit [](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) proaktiven Messagingfunktionen, der im App-Katalog Ihrer Organisation oder in [AppSource veröffentlicht wird.](https://appsource.microsoft.com/)</span><span class="sxs-lookup"><span data-stu-id="9f044-138">To get started, you will need a [bot for Teams](../../bots/how-to/create-a-bot-for-teams.md) with [proactive messaging](../../concepts/bots/bot-conversations/bots-conv-proactive.md) capabilities and  [published](../../concepts/deploy-and-publish/overview.md) in your organization's [app catalog](../../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or in [AppSource](https://appsource.microsoft.com/).</span></span>

>[!TIP]
> <span data-ttu-id="9f044-139">Die produktionsbereite [**Unternehmens-Communicator-App-Vorlage**](../..//samples/app-templates.md#company-communicator) ermöglicht Übertragungsnachrichten und ist eine gute Grundlage für die Erstellung Ihrer proaktiven Botanwendung.</span><span class="sxs-lookup"><span data-stu-id="9f044-139">The production-ready [**Company Communicator**](../..//samples/app-templates.md#company-communicator) app template enables broadcast messaging and is a good foundation for building your proactive bot application.</span></span>

### <a name="-get-the-teamsappid-for-your-app"></a><span data-ttu-id="9f044-140">✔ Für Ihre `teamsAppId` App erhalten</span><span class="sxs-lookup"><span data-stu-id="9f044-140">✔ Get the `teamsAppId` for your app</span></span>

<span data-ttu-id="9f044-141">**1.** Sie benötigen den `teamsAppId`  für die nächsten Schritte.</span><span class="sxs-lookup"><span data-stu-id="9f044-141">**1.** You will need the `teamsAppId`  for the next steps.</span></span>

<span data-ttu-id="9f044-142">Der `teamsAppId` kann aus dem App-Katalog Ihrer Organisation abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="9f044-142">The `teamsAppId` can be retrieved from your organization's app catalog:</span></span>

<span data-ttu-id="9f044-143">**Microsoft Graph-Seitenreferenz:** [teamsApp-Ressourcentyp](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-143">**Microsoft Graph page reference:** [teamsApp resource type](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true)</span></span>

<span data-ttu-id="9f044-144">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="9f044-144">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/appCatalogs/teamsApps?$filter=externalId eq '{IdFromManifest}'
```

<span data-ttu-id="9f044-145">Die Anforderung gibt ein Objekt `teamsApp`  zurück.</span><span class="sxs-lookup"><span data-stu-id="9f044-145">The request will return a `teamsApp`  object.</span></span> <span data-ttu-id="9f044-146">Die zurückgegebenen Objekte sind die vom App-Katalog generierte App-ID und unterscheiden sich von der "ID:", die Sie in Ihrem `id`  Teams-App-Manifest angegeben haben:</span><span class="sxs-lookup"><span data-stu-id="9f044-146">The returned object's `id`  is the app's catalog generated app id and is different from the "id:" that you provided in your Teams app manifest:</span></span>

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

<span data-ttu-id="9f044-147">**2.**  Wenn Ihre App bereits für einen Benutzer im persönlichen Bereich hochgeladen oder sideloaded wurde, können Sie folgendes `teamsAppId` abrufen:</span><span class="sxs-lookup"><span data-stu-id="9f044-147">**2.**  If your app has already been uploaded or sideloaded for a user in the personal scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="9f044-148">**Microsoft Graph-Seitenreferenz: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-148">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="9f044-149">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="9f044-149">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

<span data-ttu-id="9f044-150">**3.** Wenn Ihre App bereits für einen Kanal im Teambereich hochgeladen/sideloaded wurde, können Sie folgendes `teamsAppId` abrufen:</span><span class="sxs-lookup"><span data-stu-id="9f044-150">**3.** If your app has already been uploaded/sideloaded for a channel in the team scope, you can retrieve the `teamsAppId` as follows:</span></span>

<span data-ttu-id="9f044-151">**Microsoft Graph-Seitenreferenz: Apps** [im Team auflisten](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-151">**Microsoft Graph page reference:** [List apps in team](/graph/api/team-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="9f044-152">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="9f044-152">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/teams/{team-id}/installedApps?$expand=teamsApp&$filter=teamsApp/externalId eq '{IdFromManifest}'
```

>[!TIP]
> <span data-ttu-id="9f044-153">Sie können nach den Feldern des [**teamsApp-Objekts**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) filtern, um die Liste der Ergebnisse zu einengt.</span><span class="sxs-lookup"><span data-stu-id="9f044-153">You can filter on any of the fields of the [**teamsApp**](/graph/api/resources/teamsapp?view=graph-rest-1.0&preserve-view=true) object to narrow the list of results.</span></span>

### <a name="-determine-whether-your-bot-is-currently-installed-for-a-message-recipient"></a><span data-ttu-id="9f044-154">✔ Bestimmen, ob Ihr Bot derzeit für einen Nachrichtenempfänger installiert ist</span><span class="sxs-lookup"><span data-stu-id="9f044-154">✔ Determine whether your bot is currently installed for a message recipient</span></span>

<span data-ttu-id="9f044-155">**Microsoft Graph-Seitenreferenz: Für** [Benutzer installierte Apps auflisten](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-155">**Microsoft Graph page reference:** [List apps installed for user](/graph/api/userteamwork-list-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="9f044-156">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="9f044-156">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="9f044-157">Diese Anforderung gibt ein leeres Array zurück, wenn die App nicht installiert ist, oder ein Array mit einem einzelnen [teamsAppInstallation-Objekt,](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) falls es installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="9f044-157">This request will return an empty array if the app is not installed, or an array with a single [teamsAppInstallation](/graph/api/resources/teamsappinstallation?view=graph-rest-v1.0&preserve-view=true) object if it has been installed.</span></span>

### <a name="-install-your-app"></a><span data-ttu-id="9f044-158">✔ Installieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="9f044-158">✔ Install your app</span></span>

<span data-ttu-id="9f044-159">**Microsoft Graph-Seitenreferenz: Installieren** [der App für den Benutzer](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-159">**Microsoft Graph page reference:** [Install app for user](/graph/api/userteamwork-post-installedapps?view=graph-rest-v1.0&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="9f044-160">**HTTP POST-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="9f044-160">**HTTP POST** request:</span></span>

```http
POST https://graph.microsoft.com/v1.0/users/{user-id}/teamwork/installedApps
{
   "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
}
```

<span data-ttu-id="9f044-161">Wenn der Benutzer Microsoft Teams ausgeführt hat, wird die App möglicherweise sofort installiert.</span><span class="sxs-lookup"><span data-stu-id="9f044-161">If the user has Microsoft Teams running, they may see the app install immediately.</span></span> <span data-ttu-id="9f044-162">Alternativ kann ein Neustart erforderlich sein, um die installierte App zu sehen.</span><span class="sxs-lookup"><span data-stu-id="9f044-162">Alternatively, a restart may be necessary to see the installed app.</span></span>

### <a name="-retrieve-the-conversation-chatid"></a><span data-ttu-id="9f044-163">✔ Abrufen der **Chat-ID** der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="9f044-163">✔ Retrieve the conversation **chatId**</span></span>

<span data-ttu-id="9f044-164">Wenn Ihre App für den Benutzer installiert ist, erhält der Bot eine Ereignisbenachrichtigung, die die erforderlichen Informationen zum Senden der `conversationUpdate` [](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) proaktiven Nachricht enthält.</span><span class="sxs-lookup"><span data-stu-id="9f044-164">When your app is installed for the user, the bot will receive a `conversationUpdate` [event notification](../../resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) that will contain the necessary information to send the proactive message.</span></span>

<span data-ttu-id="9f044-165">Der `chatId` kann auch wie folgt abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="9f044-165">The `chatId` can also be retrieved as follows:</span></span>

<span data-ttu-id="9f044-166">**Microsoft Graph-Seitenreferenz: Chat** [erhalten](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-166">**Microsoft Graph page reference:** [Get chat](/graph/api/chat-get?view=graph-rest-beta&tabs=http&preserve-view=true)</span></span>

<span data-ttu-id="9f044-167">**1.** Sie benötigen die . `{teamsAppInstallationId}`</span><span class="sxs-lookup"><span data-stu-id="9f044-167">**1.** You will need your app's `{teamsAppInstallationId}`.</span></span> <span data-ttu-id="9f044-168">Verwenden Sie Folgendes, wenn Sie es nicht haben:</span><span class="sxs-lookup"><span data-stu-id="9f044-168">If you don't have it, use the following:</span></span>

<span data-ttu-id="9f044-169">**HTTP GET-Anforderung:**</span><span class="sxs-lookup"><span data-stu-id="9f044-169">**HTTP GET** request:</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps?$expand=teamsApp&$filter=teamsApp/id eq '{teamsAppId}'
```

<span data-ttu-id="9f044-170">Die **id-Eigenschaft** der Antwort ist die `teamsAppInstallationId` .</span><span class="sxs-lookup"><span data-stu-id="9f044-170">The **id** property of the response is the `teamsAppInstallationId`.</span></span>

<span data-ttu-id="9f044-171">**2. Stellen Sie** die folgende Anforderung, um folgendes zu `chatId` erhalten:</span><span class="sxs-lookup"><span data-stu-id="9f044-171">**2.** Make the following request to fetch the `chatId`:</span></span>

<span data-ttu-id="9f044-172">**HTTP -GET-Anforderung** (Berechtigung - `TeamsAppInstallation.ReadWriteSelfForUser.All` ):</span><span class="sxs-lookup"><span data-stu-id="9f044-172">**HTTP GET** request (permission — `TeamsAppInstallation.ReadWriteSelfForUser.All`):</span></span>  

```http
 GET https://graph.microsoft.com/beta/users/{user-id}/teamwork/installedApps/{teamsAppInstallationId}/chat
```

<span data-ttu-id="9f044-173">Die **id-Eigenschaft** der Antwort ist die `chatId` .</span><span class="sxs-lookup"><span data-stu-id="9f044-173">The **id** property of the response is the `chatId`.</span></span>

<span data-ttu-id="9f044-174">Alternativ können Sie die mit der unten aufgeführten Anforderung abrufen, benötigen `chatId`  jedoch die umfassendere `Chat.Read.All` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="9f044-174">Alternately, you can retrieve the `chatId`  with the request below, but it will require the broader `Chat.Read.All` permission:</span></span>

<span data-ttu-id="9f044-175">**HTTP -GET-Anforderung** (Berechtigung - `Chat.Read.All` ):</span><span class="sxs-lookup"><span data-stu-id="9f044-175">**HTTP GET** request (permission — `Chat.Read.All`):</span></span>

```http
GET https://graph.microsoft.com/beta/users/{user-id}/chats?$filter=installedApps/any(a:a/teamsApp/id eq '{teamsAppId}')
```

### <a name="-send-proactive-messages"></a><span data-ttu-id="9f044-176">✔ Proaktive Nachrichten senden</span><span class="sxs-lookup"><span data-stu-id="9f044-176">✔ Send proactive messages</span></span>

<span data-ttu-id="9f044-177">Nachdem Ihr Bot für einen Benutzer oder ein Team hinzugefügt wurde und die erforderlichen Benutzerinformationen erhalten hat, kann er mit dem Senden proaktiver [Nachrichten beginnen.](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9f044-177">Once your bot has been added for a user or team and has acquired the necessary user  information, it can begin to [send proactive messages](/azure/bot-service/bot-builder-howto-proactive-message?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

# <a name="c--net"></a>[<span data-ttu-id="9f044-178">C# / .NET</span><span class="sxs-lookup"><span data-stu-id="9f044-178">C# / .NET</span></span>](#tab/csharp)

<span data-ttu-id="9f044-179">Der folgende Codeausschnitt ist aus den [Microsoft Bot #A0 für C# enthalten.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span><span class="sxs-lookup"><span data-stu-id="9f044-179">The following code snippet is from the [Microsoft Bot Framework Samples for C#.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/16.proactive-messages)</span></span>

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

# <a name="javascript"></a>[<span data-ttu-id="9f044-180">JavaScript</span><span class="sxs-lookup"><span data-stu-id="9f044-180">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="9f044-181">Der folgende Codeausschnitt ist aus den [Microsoft Bot -Framework-Beispielen für JavaScript .](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages)</span><span class="sxs-lookup"><span data-stu-id="9f044-181">The following code snippet is from the [Microsoft Bot Framework Samples for JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/16.proactive-messages).</span></span>

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

## <a name="related-topic-for-teams-administrators"></a><span data-ttu-id="9f044-182">Verwandtes Thema für Teams-Administratoren</span><span class="sxs-lookup"><span data-stu-id="9f044-182">Related topic for Teams administrators</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9f044-183">**Verwalten von Richtlinien für App-Setup in Teams**</span><span class="sxs-lookup"><span data-stu-id="9f044-183">**Manage app setup policies in Microsoft Teams**</span></span>](/MicrosoftTeams/teams-app-setup-policies#create-a-custom-app-setup-policy)

## <a name="view-additional-code-samples"></a><span data-ttu-id="9f044-184">Anzeigen zusätzlicher Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="9f044-184">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9f044-185">**Proaktive Codebeispiele für Messaging in Teams**</span><span class="sxs-lookup"><span data-stu-id="9f044-185">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
