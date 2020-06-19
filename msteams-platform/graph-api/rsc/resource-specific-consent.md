---
title: Ressourcenspezifische Zustimmung in Microsoft Teams
description: Beschreibt die ressourcenspezifische Zustimmung in Microsoft Teams und deren Vorteile.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Teams-Autorisierung OAuth SSO Aad RSC Graph
ms.openlocfilehash: eb6fe0e0da03b355a4fb16d8ca5b046080af0db8
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44801344"
---
# <a name="resource-specific-consent-rsc--developer-preview"></a><span data-ttu-id="f3221-104">Ressourcenspezifische Zustimmung (RSC) – Entwicklervorschau</span><span class="sxs-lookup"><span data-stu-id="f3221-104">Resource-specific consent (RSC) — Developer Preview</span></span>

>[!NOTE]
><span data-ttu-id="f3221-105">Die Berechtigungen für die ressourcenspezifische Zustimmung sind nur in Desktop-und Android-Clients verfügbar, nachdem die Entwicklervorschau aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="f3221-105">The resource-specific consent permissions are only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="f3221-106">Weitere Informationen finden Sie unter [How do I enable Developer Preview](../../resources/dev-preview/developer-preview-intro.md) .</span><span class="sxs-lookup"><span data-stu-id="f3221-106">See [How do I enable Developer Preview](../../resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

<span data-ttu-id="f3221-107">Die ressourcenspezifische Zustimmung (RSC) ist eine Microsoft Teams-und Graph-API-Integration, die es Ihrer APP ermöglicht, API-Endpunkte zum Verwalten bestimmter Teams in einer Organisation zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f3221-107">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="f3221-108">Mit dem Berechtigungsmodell für die ressourcenspezifische Zustimmung (RSC) können *Teambesitzer* einer Anwendung die Zustimmung erteilen, auf die Daten eines Teams zuzugreifen und/oder diese zu ändern.</span><span class="sxs-lookup"><span data-stu-id="f3221-108">The resource-specific consent (RSC) permissions model enables *team owners* to grant consent for an application to access and/or modify a team's data.</span></span> <span data-ttu-id="f3221-109">Die detaillierten, Teams-spezifischen RSC-Berechtigungen definieren, was eine Anwendung in einem bestimmten Team tun kann:</span><span class="sxs-lookup"><span data-stu-id="f3221-109">The granular, Teams-specific, RSC permissions define what an application can do within a specific team:</span></span>

## <a name="resource-specific-permissions"></a><span data-ttu-id="f3221-110">Ressourcenspezifische Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="f3221-110">Resource-specific permissions</span></span>

|<span data-ttu-id="f3221-111">Anwendungsberechtigung</span><span class="sxs-lookup"><span data-stu-id="f3221-111">Application permission</span></span>| <span data-ttu-id="f3221-112">Aktion</span><span class="sxs-lookup"><span data-stu-id="f3221-112">Action</span></span> |
| ----- | ----- |
|<span data-ttu-id="f3221-113">TeamSettings. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-113">TeamSettings.Read.Group</span></span> | <span data-ttu-id="f3221-114">Rufen Sie die Einstellungen für dieses Team ab.</span><span class="sxs-lookup"><span data-stu-id="f3221-114">Get the settings for this team.</span></span>|
|<span data-ttu-id="f3221-115">TeamSettings. Edit. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-115">TeamSettings.Edit.Group</span></span>|<span data-ttu-id="f3221-116">Aktualisieren Sie die Einstellungen für dieses Team.</span><span class="sxs-lookup"><span data-stu-id="f3221-116">Update the settings for this team.</span></span>|
|<span data-ttu-id="f3221-117">ChannelSettings. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-117">ChannelSettings.Read.Group</span></span>|<span data-ttu-id="f3221-118">Rufen Sie die Kanalnamen, Kanal Beschreibungen und Kanaleinstellungen für dieses Team ab.</span><span class="sxs-lookup"><span data-stu-id="f3221-118">Get the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="f3221-119">ChannelSettings. Edit. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-119">ChannelSettings.Edit.Group</span></span>|<span data-ttu-id="f3221-120">Aktualisieren Sie die Kanalnamen, Kanal Beschreibungen und Kanaleinstellungen für dieses Team.</span><span class="sxs-lookup"><span data-stu-id="f3221-120">Update the channel names, channel descriptions, and channel settings for this team.</span></span>|
|<span data-ttu-id="f3221-121">Channel. Create. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-121">Channel.Create.Group</span></span>|<span data-ttu-id="f3221-122">Erstellen Sie in diesem Team Kanäle.</span><span class="sxs-lookup"><span data-stu-id="f3221-122">Create channels in this team.</span></span>|
|<span data-ttu-id="f3221-123">Kanal. Delete. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-123">Channel.Delete.Group</span></span>|<span data-ttu-id="f3221-124">Löschen Sie Kanäle in diesem Team.</span><span class="sxs-lookup"><span data-stu-id="f3221-124">Delete channels in this team.</span></span>|
|<span data-ttu-id="f3221-125">ChannelMessage. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-125">ChannelMessage.Read.Group</span></span> |<span data-ttu-id="f3221-126">Rufen Sie die Kanal Nachrichten dieses Teams ab.</span><span class="sxs-lookup"><span data-stu-id="f3221-126">Get this team's channel messages.</span></span>|
|<span data-ttu-id="f3221-127">TeamsApp. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-127">TeamsApp.Read.Group</span></span>|<span data-ttu-id="f3221-128">Rufen Sie eine Liste der installierten apps dieses Teams ab.</span><span class="sxs-lookup"><span data-stu-id="f3221-128">Get a list of this team's installed apps.</span></span>|
|<span data-ttu-id="f3221-129">TeamsTab. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-129">TeamsTab.Read.Group</span></span>|<span data-ttu-id="f3221-130">Rufen Sie eine Liste der Registerkarten dieses Teams ab.</span><span class="sxs-lookup"><span data-stu-id="f3221-130">Get a list of this team's tabs.</span></span>|
|<span data-ttu-id="f3221-131">TeamsTab. Create. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-131">TeamsTab.Create.Group</span></span>|<span data-ttu-id="f3221-132">Erstellen von Registerkarten in diesem Team.</span><span class="sxs-lookup"><span data-stu-id="f3221-132">Create tabs in this team.</span></span>|
|<span data-ttu-id="f3221-133">TeamsTab. Edit. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-133">TeamsTab.Edit.Group</span></span>|<span data-ttu-id="f3221-134">Aktualisieren Sie die Registerkarten dieses Teams.</span><span class="sxs-lookup"><span data-stu-id="f3221-134">Update this team's tabs.</span></span>|
|<span data-ttu-id="f3221-135">TeamsTab. Delete. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-135">TeamsTab.Delete.Group</span></span>|<span data-ttu-id="f3221-136">Löschen Sie die Registerkarten dieses Teams.</span><span class="sxs-lookup"><span data-stu-id="f3221-136">Delete this team's tabs.</span></span>|
|<span data-ttu-id="f3221-137">Member. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-137">Member.Read.Group</span></span>|<span data-ttu-id="f3221-138">Die Mitglieder dieses Teams abrufen.</span><span class="sxs-lookup"><span data-stu-id="f3221-138">Get this team's members.</span></span>|
|<span data-ttu-id="f3221-139">Owner. Read. Group</span><span class="sxs-lookup"><span data-stu-id="f3221-139">Owner.Read.Group</span></span>|<span data-ttu-id="f3221-140">Die Besitzer dieses Teams abrufen.</span><span class="sxs-lookup"><span data-stu-id="f3221-140">Get this team's owners.</span></span>|

>[!NOTE]
><span data-ttu-id="f3221-141">Ressourcenspezifische Berechtigungen stehen nur für Teams-Apps zur Verfügung, die auf dem Microsoft Teams-Client installiert sind und derzeit nicht Teil des Azure Active Directory-Portals sind.</span><span class="sxs-lookup"><span data-stu-id="f3221-141">Resource-specific permissions are only available to Teams apps installed on the Teams client and are currently not part of the Azure Active Directory portal.</span></span>

## <a name="enabling-resource-specific-consent-in-your-application"></a><span data-ttu-id="f3221-142">Aktivieren der ressourcenspezifischen Zustimmung in Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="f3221-142">Enabling resource-specific consent in your application</span></span>

<span data-ttu-id="f3221-143">Die Schritte zum Aktivieren von RSC in Ihrer Anwendung lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f3221-143">The steps for enabling RSC in your application are as follows:</span></span>

1. <span data-ttu-id="f3221-144">[Konfigurieren Sie die Zustimmungs Einstellungen für den Gruppenbesitzer im Azure Active Directory-Portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="f3221-144">[Configure group owner consent settings in the Azure Active Directory portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).</span></span>
1. <span data-ttu-id="f3221-145">[Registrieren Sie Ihre APP mit der Microsoft Identity Platform über das Azure AD Portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="f3221-145">[Register your app with Microsoft identity platform via the Azure AD portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
1. [<span data-ttu-id="f3221-146">Überprüfen der Anwendungsberechtigungen im Azure AD Portal</span><span class="sxs-lookup"><span data-stu-id="f3221-146">Review your application permissions in the Azure AD portal</span></span>](#review-your-application-permissions-in-the-azure-ad-portal)
1. <span data-ttu-id="f3221-147">[Rufen Sie ein Zugriffstoken von der Microsoft Identity-Plattform ab](#obtain-an-access-token-from-the-microsoft-identity-platform).</span><span class="sxs-lookup"><span data-stu-id="f3221-147">[Obtain an access token from the Microsoft Identity platform](#obtain-an-access-token-from-the-microsoft-identity-platform).</span></span>
1. <span data-ttu-id="f3221-148">[Aktualisieren Sie Ihr Teams-App-Manifest](#update-your-teams-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="f3221-148">[Update your Teams app manifest](#update-your-teams-app-manifest).</span></span>
1. <span data-ttu-id="f3221-149">[Installieren Sie Ihre APP direkt in Microsoft Teams](#install-your-app-directly-in-teams).</span><span class="sxs-lookup"><span data-stu-id="f3221-149">[Install your app directly in Teams](#install-your-app-directly-in-teams).</span></span>
1. <span data-ttu-id="f3221-150">[Überprüfen Sie Ihre APP auf hinzugefügte RSC-Berechtigungen](#check-your-app-for-added-rsc-permissions).</span><span class="sxs-lookup"><span data-stu-id="f3221-150">[Check your app for added RSC permissions](#check-your-app-for-added-rsc-permissions).</span></span>

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a><span data-ttu-id="f3221-151">Konfigurieren von Zustimmungs Einstellungen für Gruppenbesitzer im Azure AD Portal</span><span class="sxs-lookup"><span data-stu-id="f3221-151">Configure group owner consent settings in the Azure AD portal</span></span>

<span data-ttu-id="f3221-152">Sie können die Zustimmung des [Gruppen Besitzers](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data) direkt im Azure-Portal aktivieren oder deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="f3221-152">You can enable or disable  [group owner consent](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data) directly within the Azure portal:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="f3221-153">Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator/Unternehmensadministrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)an.</span><span class="sxs-lookup"><span data-stu-id="f3221-153">Sign in to the [Azure portal](https://portal.azure.com) as a [Global Administrator/Company Administrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator).</span></span>  
 > - <span data-ttu-id="f3221-154">Wählen Sie **Azure Active Directory**  => Benutzereinstellungen für**Enterprise**  => **User settings**-Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="f3221-154">Select **Azure Active Directory** =>**Enterprise applications** =>**User settings**.</span></span>
> - <span data-ttu-id="f3221-155">Aktivieren, deaktivieren oder begrenzen der Benutzer Zustimmung mit dem Steuerelement mit der Bezeichnung **Benutzer können apps, die auf Unternehmensdaten zugreifen, für die Gruppen, die Sie besitzen, einwilligen** (diese Funktion ist standardmäßig aktiviert).</span><span class="sxs-lookup"><span data-stu-id="f3221-155">Enable, disable, or limit user consent with the control labeled **Users can consent to apps accessing company data for the groups they own** (This capability is enabled by default).</span></span>

![Azure RSC-Konfiguration](../../assets/images/azure-rsc-configuration.svg)

| <span data-ttu-id="f3221-157">Wert</span><span class="sxs-lookup"><span data-stu-id="f3221-157">Value</span></span> | <span data-ttu-id="f3221-158">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f3221-158">Description</span></span>|
|--- | --- |
|<span data-ttu-id="f3221-159">Ja</span><span class="sxs-lookup"><span data-stu-id="f3221-159">Yes</span></span> | <span data-ttu-id="f3221-160">Aktivieren Sie die gruppenspezifische Zustimmung für alle Gruppenbesitzer.</span><span class="sxs-lookup"><span data-stu-id="f3221-160">Enable group-specific consent for all group owners.</span></span>|
|<span data-ttu-id="f3221-161">Nein</span><span class="sxs-lookup"><span data-stu-id="f3221-161">No</span></span> |<span data-ttu-id="f3221-162">Deaktivieren Sie die gruppenspezifische Zustimmung für alle Benutzer.</span><span class="sxs-lookup"><span data-stu-id="f3221-162">Disable group-specific consent for all users.</span></span>| 
|<span data-ttu-id="f3221-163">Beschränkt</span><span class="sxs-lookup"><span data-stu-id="f3221-163">Limited</span></span> | <span data-ttu-id="f3221-164">Aktivieren Sie die gruppenspezifische Zustimmung für Mitglieder einer ausgewählten Gruppe.</span><span class="sxs-lookup"><span data-stu-id="f3221-164">Enable group-specific consent for members of a selected group.</span></span>|

<span data-ttu-id="f3221-165">Um die Zustimmung des Gruppen Besitzers innerhalb des Azure-Portals mithilfe von PowerShell zu aktivieren oder zu deaktivieren, führen Sie die unter [configure Group Owner Einwilligung using PowerShell](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-using-powershell)beschriebenen Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="f3221-165">To enable or disable group owner consent within the Azure portal using PowerShell, follow the steps outlined in [Configure group owner consent using PowerShell](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-using-powershell).</span></span>

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a><span data-ttu-id="f3221-166">Registrieren Ihrer APP mit der Microsoft Identity Platform über das Azure AD Portal</span><span class="sxs-lookup"><span data-stu-id="f3221-166">Register your app with Microsoft identity platform via the Azure AD portal</span></span>

<span data-ttu-id="f3221-167">Das Azure Active Directory-Portal stellt eine zentrale Plattform zum Registrieren und Konfigurieren Ihrer Apps bereit.</span><span class="sxs-lookup"><span data-stu-id="f3221-167">The Azure Active Directory portal provides a central platform for you to register and configure your apps.</span></span> <span data-ttu-id="f3221-168">Ihre APP muss im Azure AD-Portal registriert sein, damit Sie in die Microsoft Identity Platform und die Call Graph-APIs integriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="f3221-168">Your app must be registered in the Azure AD portal to integrate with the Microsoft identity platform and call Graph APIs.</span></span> <span data-ttu-id="f3221-169">*Weitere Informationen finden Sie unter* [Registrieren einer Anwendung mit der Microsoft Identity-Plattform](/graph/auth-register-app-v2).</span><span class="sxs-lookup"><span data-stu-id="f3221-169">*See* [Register an application with the Microsoft identity platform](/graph/auth-register-app-v2).</span></span>

>[!WARNING]
><span data-ttu-id="f3221-170">Registrieren Sie mehrere Teams-apps nicht für dieselbe Azure AD App-ID. Die APP-ID muss für jede APP eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="f3221-170">Do not register multiple Teams apps to the same Azure AD app id. The app id must be unique for each app.</span></span> <span data-ttu-id="f3221-171">Versuche, mehrere apps in derselben APP-ID zu installieren, können nicht ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f3221-171">Attempts to install multiple apps to the same app id will fail.</span></span>

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a><span data-ttu-id="f3221-172">Überprüfen der Anwendungsberechtigungen im Azure AD Portal</span><span class="sxs-lookup"><span data-stu-id="f3221-172">Review your application permissions in the Azure AD portal</span></span>

<span data-ttu-id="f3221-173">Navigieren Sie zur Seite **Home**  =>  **App Registrations** , und wählen Sie Ihre RSC-App aus.</span><span class="sxs-lookup"><span data-stu-id="f3221-173">Navigate to the **Home** => **App registrations** page and select your RSC app.</span></span> <span data-ttu-id="f3221-174">Wählen Sie in der linken Navigationsleiste **API-Berechtigungen** aus, und überprüfen Sie die Liste der konfigurierten Berechtigungen für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="f3221-174">Choose **API permissions** from the left nav bar and examine the list of configured permissions for your app.</span></span> <span data-ttu-id="f3221-175">Wenn Ihre APP nur RSC-Grafik Anrufe tätigen kann, löschen Sie alle Berechtigungen auf dieser Seite.</span><span class="sxs-lookup"><span data-stu-id="f3221-175">If your app will only make RSC Graph calls, delete all the permission on that page.</span></span> <span data-ttu-id="f3221-176">Wenn Ihre APP auch nicht-RSC-Anrufe tätigen kann, behalten Sie diese Berechtigungen bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="f3221-176">If your app will also make non-RSC calls, keep those permissions as needed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f3221-177">Das Azure AD Portal kann nicht verwendet werden, um RSC-Berechtigungen anzufordern.</span><span class="sxs-lookup"><span data-stu-id="f3221-177">The Azure AD portal cannot be used to request RSC permissions.</span></span> <span data-ttu-id="f3221-178">RSC-Berechtigungen sind derzeit ausschließlich für Microsoft Teams-Anwendungen, die im Microsoft Teams-Client installiert sind, und werden in der APP-Manifestdatei (JSON) deklariert.</span><span class="sxs-lookup"><span data-stu-id="f3221-178">RSC permissions are currently exclusive to Teams applications installed in the Teams client and are declared in the app manifest (JSON) file.</span></span>

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a><span data-ttu-id="f3221-179">Abrufen eines Zugriffstokens von der Microsoft Identity-Plattform</span><span class="sxs-lookup"><span data-stu-id="f3221-179">Obtain an access token from the Microsoft identity platform</span></span>

<span data-ttu-id="f3221-180">Um Graph-API-Aufrufe zu erstellen, müssen Sie ein Zugriffstoken für Ihre APP über die Identitäts Plattform abrufen.</span><span class="sxs-lookup"><span data-stu-id="f3221-180">To make Graph API calls, you must obtain an access token for your app from the identity platform.</span></span> <span data-ttu-id="f3221-181">Damit Ihre APP ein Token von der Microsoft Identity-Plattform erhalten kann, muss Sie im Azure AD Portal registriert sein.</span><span class="sxs-lookup"><span data-stu-id="f3221-181">Before your app can get a token from the Microsoft identity platform, it must be registered in the Azure AD portal.</span></span> <span data-ttu-id="f3221-182">Das Zugriffstoken enthält Informationen zu Ihrer App und die Berechtigungen, über die es für die Ressourcen und APIs verfügt, die über Microsoft Graph bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f3221-182">The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph.</span></span>

<span data-ttu-id="f3221-183">Sie benötigen die folgenden Werte aus dem Azure AD Registrierungsprozess, um ein Zugriffstoken von der Identitäts Plattform abzurufen:</span><span class="sxs-lookup"><span data-stu-id="f3221-183">You'll need to have the following values from the Azure AD registration process to retrieve an access token from the identity platform:</span></span>

- <span data-ttu-id="f3221-184">Die **Anwendungs-ID** , die vom APP-Registrierungs Portal zugewiesen wird.</span><span class="sxs-lookup"><span data-stu-id="f3221-184">The **Application ID** assigned by the app registration portal.</span></span> <span data-ttu-id="f3221-185">Wenn Ihre APP einmaliges Anmelden (Single Sign-on, SSO) unterstützt, sollten Sie die gleiche Anwendungs-ID für Ihre APP und SSO verwenden.</span><span class="sxs-lookup"><span data-stu-id="f3221-185">If your app supports single sign-on (SSO) you should use the same Application ID for your app and SSO.</span></span>
- <span data-ttu-id="f3221-186">Der **geheime Client Schlüssel/das Kennwort** oder ein öffentliches/privates Schlüsselpaar (**Certificate**).</span><span class="sxs-lookup"><span data-stu-id="f3221-186">The  **Client secret/password** or a public/private key pair (**Certificate**).</span></span> <span data-ttu-id="f3221-187">Dies ist für systemeigene Apps nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f3221-187">This is not required for native apps.</span></span>
- <span data-ttu-id="f3221-188">Eine **Umleitungs-URI** (oder Antwort-URL) für Ihre APP, um Antworten von Azure AD zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f3221-188">A **Redirect URI** (or reply URL) for your app to receive responses from Azure AD.</span></span>

 <span data-ttu-id="f3221-189">*Siehe* [Abrufen des Zugriffs im Namen eines Benutzers](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token) und [Abrufen des Zugriffs ohne Benutzer](/graph/auth-v2-service)</span><span class="sxs-lookup"><span data-stu-id="f3221-189">*See* [Get access on behalf of a user](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token) and [Get access without a user](/graph/auth-v2-service)</span></span>

## <a name="update-your-teams-app-manifest"></a><span data-ttu-id="f3221-190">Aktualisieren des Teams-App-Manifests</span><span class="sxs-lookup"><span data-stu-id="f3221-190">Update your Teams app manifest</span></span>

<span data-ttu-id="f3221-191">Die RSC-Berechtigungen werden in Ihrer APP-Manifestdatei (JSON-Datei) deklariert.</span><span class="sxs-lookup"><span data-stu-id="f3221-191">The RSC permissions are declared in you app manifest (JSON) file.</span></span>  <span data-ttu-id="f3221-192">Fügen Sie dem App-Manifest einen [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) -Schlüssel mit den folgenden Werten hinzu:</span><span class="sxs-lookup"><span data-stu-id="f3221-192">Add a [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) key to your app manifest with the following values:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f3221-193">**ID** – ihre Azure AD App-ID. *Weitere Informationen finden Sie unter* [Registrieren Ihrer APP im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="f3221-193">**id**  — your Azure AD app id. *See* [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="f3221-194">**Resource** – eine beliebige Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="f3221-194">**resource**  — any string.</span></span> <span data-ttu-id="f3221-195">Dieses Feld hat keine Operation im RSC, muss jedoch hinzugefügt werden und einen Wert haben, um eine Fehlerantwort zu vermeiden. eine Zeichenfolge wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="f3221-195">This field has no operation in RSC, but must be added and have a value to avoid an error response; any string will do.</span></span>
> - <span data-ttu-id="f3221-196">**Anwendungsberechtigungen** – RSC-Berechtigungen für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="f3221-196">**application permissions** — RSC permissions for  your app.</span></span> <span data-ttu-id="f3221-197">*Siehe* [ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="f3221-197">*See* [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

>
>[!IMPORTANT]
> <span data-ttu-id="f3221-198">Nicht-RSC-Berechtigungen werden im Azure-Portal gespeichert.</span><span class="sxs-lookup"><span data-stu-id="f3221-198">Non-RSC permissions are stored in the Azure portal.</span></span> <span data-ttu-id="f3221-199">Fügen Sie Sie nicht zum App-Manifest hinzu.</span><span class="sxs-lookup"><span data-stu-id="f3221-199">Do not add them to the app manifest.</span></span>
>

```json
"webApplicationInfo": {

        "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX", 

"resource": "https://RscBasedStoreApp",

        "applicationPermissions": [

    "TeamSettings.Read.Group",

   "ChannelMessage.Read.Group",

  "TeamSettings.Edit.Group",

  "ChannelSettings.Edit.Group",

  "Channel.Create.Group",

  "Channel.Delete.Group",

  "TeamsApp.Read.Group",

  "TeamsTab.Read.Group",

  "TeamsTab.Create.Group",

  "TeamsTab.Edit.Group",

  "TeamsTab.Delete.Group",

  "Member.Read.Group",

  "Owner.Read.Group"

        ]

    }
```

## <a name="install-your-app-directly-in-teams"></a><span data-ttu-id="f3221-200">Direkte Installation Ihrer APP in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f3221-200">Install your app directly in Teams</span></span>

<span data-ttu-id="f3221-201">Nachdem Sie Ihre APP erstellt haben, können Sie [Ihr App-Paket](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) direkt in ein bestimmtes Team hochladen.</span><span class="sxs-lookup"><span data-stu-id="f3221-201">Once you've created your app you can [upload your app package](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) directly to a specific team.</span></span>  <span data-ttu-id="f3221-202">Hierzu muss die Richtlinieneinstellung **benutzerdefinierte apps hochladen** als Teil der benutzerdefinierten Richtlinien für die APP-Einrichtung aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="f3221-202">To do so, the **Upload custom apps** policy setting must be enabled as part of the custom app setup policies.</span></span> <span data-ttu-id="f3221-203">*Siehe* [benutzerdefinierte App-Richtlinieneinstellungen](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).</span><span class="sxs-lookup"><span data-stu-id="f3221-203">*See* [Custom app policy settings](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).</span></span>

## <a name="check-your-app-for-added-rsc-permissions"></a><span data-ttu-id="f3221-204">Überprüfen Ihrer APP auf hinzugefügte RSC-Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="f3221-204">Check your app for added RSC permissions</span></span>

>[!IMPORTANT]
><span data-ttu-id="f3221-205">Die RSC-Berechtigungen werden keinem Benutzer zugeschrieben.</span><span class="sxs-lookup"><span data-stu-id="f3221-205">The RSC permissions are not attributed to a user.</span></span> <span data-ttu-id="f3221-206">Aufrufe werden mit App-Berechtigungen und nicht mit Benutzern Delegierten Berechtigungen durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="f3221-206">Calls are made with app permissions, not user delegated permissions.</span></span> <span data-ttu-id="f3221-207">Daher kann die APP möglicherweise Aktionen durchführen, die der Benutzer nicht ausführen kann, beispielsweise das Erstellen eines Kanals oder das Löschen einer Registerkarte. Sie sollten die Absicht des Team Besitzers für Ihren Anwendungsfall vor dem Erstellen von RSC-API-aufrufen überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f3221-207">Thus, the app may be allowed to perform actions that the user cannot, such as creating a channel or deleting a tab. You should review the team owner's intent for your use case prior to making RSC API calls.</span></span> <span data-ttu-id="f3221-208">*Weitere Informationen finden Sie unter* [Übersicht über die Microsoft Teams-API](/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="f3221-208">*See* [Microsoft Teams API overview](/graph/teams-concept-overview).</span></span>

<span data-ttu-id="f3221-209">Nachdem die app in einem Team installiert wurde, können Sie den [Graph-Explorer](https://developer.microsoft.com/graph/graph-explorer) verwenden, um die Berechtigungen anzuzeigen, die der app in einem Team erteilt wurden:</span><span class="sxs-lookup"><span data-stu-id="f3221-209">Once the app has been installed to a team, you can use [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)  to view the permissions that have been granted to the app in a team:</span></span>

> [!div class="checklist"]
>
>- <span data-ttu-id="f3221-210">Rufen Sie die **Gruppen** -Nr des Teams vom Microsoft Teams-Client ab.</span><span class="sxs-lookup"><span data-stu-id="f3221-210">Get the team's **groupId** from the Teams client.</span></span>
> - <span data-ttu-id="f3221-211">Wählen Sie im Microsoft Teams-Client die Option **Teams** von der ganz linken Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="f3221-211">In the Teams client, select **Teams** from the far left nav bar.</span></span>
> - <span data-ttu-id="f3221-212">Wählen Sie im Dropdownmenü das Team aus, in dem die APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="f3221-212">Select the team where the app is installed from the drop-down menu.</span></span>
> - <span data-ttu-id="f3221-213">Klicken Sie auf das Symbol **Weitere Optionen** (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="f3221-213">Select the **More options** icon (&#8943;).</span></span>
> - <span data-ttu-id="f3221-214">Wählen Sie **Get Link to Team**aus.</span><span class="sxs-lookup"><span data-stu-id="f3221-214">Select **Get link to team**.</span></span>
> - <span data-ttu-id="f3221-215">Kopieren Sie den Wert der **Gruppe** , und speichern Sie ihn aus der Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="f3221-215">Copy and save the **groupId** value from the string.</span></span>
> - <span data-ttu-id="f3221-216">Melden Sie sich beim **Graph-Explorer**an.</span><span class="sxs-lookup"><span data-stu-id="f3221-216">Log into **Graph Explorer**.</span></span>
> - <span data-ttu-id="f3221-217">Einen **Get** -Aufruf an den folgenden Endpunkt ausführen: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` .</span><span class="sxs-lookup"><span data-stu-id="f3221-217">Make a **GET** call to the following endpoint: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants`.</span></span> <span data-ttu-id="f3221-218">Das clientAppId-Feld in der Antwort wird der im Microsoft Teams-App-Manifest angegebenen Anwendungs-ID zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="f3221-218">The clientAppId field in the response will map to the appId specified in the Teams app manifest.</span></span>

 ![Graph-Explorer-Antwort zum Abrufen eines Anrufs.](../../assets/images/graph-permissions.png)

 > [!div class="nextstepaction"]
> [<span data-ttu-id="f3221-220">Testen von Berechtigungen für die ressourcenspezifische Zustimmung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f3221-220">Test resource-specific consent permissions in Teams</span></span>](test-resource-specific-consent.md)
