---
title: Kontext für Ihre Registerkarte erhalten
description: Beschreibt, wie Sie Benutzerkontext zu Ihren Registerkarten abrufen
localization_priority: Normal
ms.topic: how-to
keywords: Teams Registerkarten Benutzerkontext
ms.openlocfilehash: 0d9224a941ae4f6a5ad125c93d5877ec49b6df28
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566866"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a><span data-ttu-id="a17c1-104">Abrufen von Kontext zu Ihrer Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="a17c1-104">Get context for your Microsoft Teams tab</span></span>

<span data-ttu-id="a17c1-105">Ihre Registerkarte muss Kontextinformationen benötigen, um relevante Inhalte anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="a17c1-105">Your tab must require contextual information to display relevant content:</span></span>

* <span data-ttu-id="a17c1-106">Grundlegende Informationen zum Benutzer, Team oder Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="a17c1-106">Basic information about the user, team, or company.</span></span>
* <span data-ttu-id="a17c1-107">Lokal- und Themeninformationen.</span><span class="sxs-lookup"><span data-stu-id="a17c1-107">Locale and theme information.</span></span>
* <span data-ttu-id="a17c1-108">Lesen Sie die `entityId` `subEntityId` oder, die identifiziert, was auf dieser Registerkarte ist.</span><span class="sxs-lookup"><span data-stu-id="a17c1-108">Read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="a17c1-109">Benutzerkontext</span><span class="sxs-lookup"><span data-stu-id="a17c1-109">User context</span></span>

<span data-ttu-id="a17c1-110">Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders nützlich sein, wenn:</span><span class="sxs-lookup"><span data-stu-id="a17c1-110">Context about the user, team or company can be especially useful when:</span></span>

* <span data-ttu-id="a17c1-111">Sie erstellen oder ordnen Ressourcen in Ihrer App dem angegebenen Benutzer oder Team zu.</span><span class="sxs-lookup"><span data-stu-id="a17c1-111">You create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="a17c1-112">Sie initiieren einen Authentifizierungsfluss für Azure Active Directory oder einen anderen Identitätsanbieter, und Sie möchten nicht, dass der Benutzer seinen Benutzernamen erneut eingibt.</span><span class="sxs-lookup"><span data-stu-id="a17c1-112">You initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again.</span></span> <span data-ttu-id="a17c1-113">Weitere Informationen zur Authentifizierung auf ihrer Registerkarte Microsoft Teams finden Sie unter [Authentifizieren eines Benutzers auf der Registerkarte Microsoft Teams](~/concepts/authentication/authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a17c1-113">For more information on authenticating within your Microsoft Teams tab, see [Authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a17c1-114">Diese Benutzerinformationen können zwar zu einer reibungslosen Benutzererfahrung beitragen, Sie sollten sie aber *nicht* als Identitätsnachweis verwenden.</span><span class="sxs-lookup"><span data-stu-id="a17c1-114">Although this user information can help provide a smooth user experience, you should *not* use it as proof of identity.</span></span> <span data-ttu-id="a17c1-115">Beispielsweise könnte ein Angreifer Ihre Seite in einem „Bad Browser“ laden und schädliche Informationen oder Anforderungen rendern.</span><span class="sxs-lookup"><span data-stu-id="a17c1-115">For example, an attacker could load your page in a "bad browser" and render harmful information or requests.</span></span>

## <a name="accessing-context"></a><span data-ttu-id="a17c1-116">Zugreifen auf den Kontext</span><span class="sxs-lookup"><span data-stu-id="a17c1-116">Accessing context</span></span>

<span data-ttu-id="a17c1-117">Sie können auf zwei Arten auf Kontextinformationen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="a17c1-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="a17c1-118">Fügen Sie URL-Platzhalterwerte ein.</span><span class="sxs-lookup"><span data-stu-id="a17c1-118">Insert URL placeholder values.</span></span>
* <span data-ttu-id="a17c1-119">Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client).</span><span class="sxs-lookup"><span data-stu-id="a17c1-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client).</span></span>

### <a name="getting-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="a17c1-120">Abrufen von Kontext durch Einfügen von URL-Platzhalterwerten</span><span class="sxs-lookup"><span data-stu-id="a17c1-120">Getting context by inserting URL placeholder values</span></span>

<span data-ttu-id="a17c1-121">Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs.</span><span class="sxs-lookup"><span data-stu-id="a17c1-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="a17c1-122">Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="a17c1-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL.</span></span> <span data-ttu-id="a17c1-123">Die verfügbaren Platzhalter umfassen alle Felder des [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="a17c1-123">The available placeholders include all fields on the [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) object.</span></span> <span data-ttu-id="a17c1-124">Häufige Platzhalter sind folgende:</span><span class="sxs-lookup"><span data-stu-id="a17c1-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="a17c1-125">{entityId}: Die ID, die Sie für das Element auf dieser Registerkarte beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md) angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="a17c1-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="a17c1-126">{subEntityId}: Die ID, die Sie beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element _innerhalb_ dieser Registerkarte angegeben haben. Diese sollte verwendet werden, um einen bestimmten Zustand innerhalb einer Entität wiederherzustellen, z: B., um zu einem bestimmten Inhalt zu blättern oder diesen zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a17c1-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item _within_ this tab. This should be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="a17c1-127">{loginHint}: Ein Wert, der sich als Anmeldehinweis für Azure AD eignet. Dies ist in der Regel der Anmeldename des aktuellen Benutzers in seinem Basismandanten.</span><span class="sxs-lookup"><span data-stu-id="a17c1-127">{loginHint}: A value suitable as a login hint for Azure AD.This is usually the login name of the current user, in their home tenant.</span></span>
* <span data-ttu-id="a17c1-128">{userPrincipalName}: Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="a17c1-128">{userPrincipalName}: The User Principal Name of the current user, in the current tenant.</span></span>
* <span data-ttu-id="a17c1-129">{userObjectId}: Die Azure AD-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="a17c1-129">{userObjectId}: The Azure AD object ID of the current user, in the current tenant.</span></span>
* <span data-ttu-id="a17c1-130">{theme}: Das aktuelle UI-Design, z. B. `default`, `dark` oder `contrast`.</span><span class="sxs-lookup"><span data-stu-id="a17c1-130">{theme}: The current UI theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="a17c1-131">{groupId}: Die ID der Office 365-Gruppe, in der sich die Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="a17c1-131">{groupId}: The ID of the Office 365 Group in which the tab resides.</span></span>
* <span data-ttu-id="a17c1-132">{tid}: Die Azure AD-Mandanten-ID des aktuellen Benutzers.</span><span class="sxs-lookup"><span data-stu-id="a17c1-132">{tid}: The Azure AD tenant ID of the current user.</span></span>
* <span data-ttu-id="a17c1-133">Gebietsschema: Das aktuelle Gebietsschema des Als languageId-countryId formatierten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="a17c1-133">{locale}: The current locale of the user formatted as languageId-countryId.</span></span> <span data-ttu-id="a17c1-134">Zum Beispiel en-us.</span><span class="sxs-lookup"><span data-stu-id="a17c1-134">For example, en-us.</span></span>

>[!NOTE]
><span data-ttu-id="a17c1-135">Der bisherige Platzhalter `{upn}` ist nun veraltet.</span><span class="sxs-lookup"><span data-stu-id="a17c1-135">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="a17c1-136">Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}`.</span><span class="sxs-lookup"><span data-stu-id="a17c1-136">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="a17c1-137">Angenommen, In Ihrem Registerkartenmanifest legen Sie das `configURL` Attribut auf , der `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"` angemeldete Benutzer hat die folgenden Attribute:</span><span class="sxs-lookup"><span data-stu-id="a17c1-137">For example, suppose in your tab manifest you set the `configURL` attribute to `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`, the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="a17c1-138">Ihr Benutzername lautet "user@example.com".</span><span class="sxs-lookup"><span data-stu-id="a17c1-138">Their username is 'user@example.com'.</span></span>
* <span data-ttu-id="a17c1-139">Ihre Firmenmieter-ID ist 'e2653c-etc'.</span><span class="sxs-lookup"><span data-stu-id="a17c1-139">Their company tenant ID is 'e2653c-etc'.</span></span>
* <span data-ttu-id="a17c1-140">Sie sind Mitglied der Office 365 Gruppe mit der Id '00209384-etc'.</span><span class="sxs-lookup"><span data-stu-id="a17c1-140">They are a member of the Office 365 group with id '00209384-etc'.</span></span>
* <span data-ttu-id="a17c1-141">Der Benutzer hat sein Teams Thema auf "dunkel" gesetzt.</span><span class="sxs-lookup"><span data-stu-id="a17c1-141">The user has set their Teams theme to 'dark'.</span></span>

<span data-ttu-id="a17c1-142">Wenn sie Ihre Registerkarte konfigurieren, ruft Teams die folgende URL auf:</span><span class="sxs-lookup"><span data-stu-id="a17c1-142">When they configure your tab, Teams calls the following URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="a17c1-143">Abrufen von Kontext durch Verwendung der JavaScript-Bibliothek von Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a17c1-143">Getting context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="a17c1-144">Sie können die zuvor aufgeführten Informationen auch mithilfe des [JavaScript-Client-SDKs von Microsoft Teams](/javascript/api/overview/msteams-client) abrufen, indem Sie `microsoftTeams.getContext(function(context) { /* ... */ })` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a17c1-144">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="a17c1-145">Die Kontextvariable sieht wie im folgenden Beispiel aus:</span><span class="sxs-lookup"><span data-stu-id="a17c1-145">The context variable looks like the following example:</span></span>

```json
{
    "teamId": "The Microsoft Teams ID in the format 19:[id]@thread.skype",
    "teamName": "The name of the current team",
    "channelId": "The channel ID in the format 19:[id]@thread.skype",
    "channelName": "The name of the current channel",
    "chatId": "The chat ID in the format 19:[id]@thread.skype",
    "locale": "The current locale of the user formatted as languageId-countryId (for example, en-us)",
    "entityId": "The developer-defined unique ID for the entity this content points to",
    "subEntityId": "The developer-defined unique ID for the sub-entity this content points to",
    "loginHint": "A value suitable as a login hint for Azure AD. This is usually the login name of the current user, in their home tenant",
    "userPrincipalName": "The principal name of the current user, in the current tenant",
    "userObjectId": "The Azure AD object id of the current user, in the current tenant",
    "tid": "The Azure AD tenant ID of the current user",
    "groupId": "Guid identifying the current O365 Group ID",
    "theme": "The current UI theme: default | dark | contrast",
    "isFullScreen": "Indicates if the tab is in full-screen",
    "teamType": "The type of team",
    "teamSiteUrl": "The root SharePoint site associated with the team",
    "teamSiteDomain": "The domain of the root SharePoint site associated with the team",
    "teamSitePath": "The relative path to the SharePoint site associated with the team",
    "channelRelativeUrl": "The relative path to the SharePoint folder associated with the channel",
    "sessionId": "The unique ID for the current Teams session for use in correlating telemetry data",
    "userTeamRole": "The user's role in the team",
    "isTeamArchived": "Indicates if team is archived",
    "hostClientType": "The type of host client. Possible values are android, ios, web, desktop, rigel",
    "frameContext": "The context where tab URL is loaded (for example, content, task, setting, remove, sidePanel)",
    "sharepoint": "The SharePoint context is available only when hosted in SharePoint",
    "tenantSKU": "The license type for the current user tenant. Possible values are enterprise, free, edu, unknown",
    "userLicenseType": "The license type for the current user",
    "parentMessageId": "The parent message ID from which this task module is launched",
    "ringId": "The current ring ID",
    "appSessionId": "The unique ID for the current session used for correlating telemetry data",
    "isCallingAllowed": "Indicates if calling is allowed for the current logged in user",
    "isPSTNCallingAllowed": "Indicates if PSTN calling is allowed for the current logged in user",
    "meetingId": "The meeting ID used by tab when running in meeting context",
    "defaultOneNoteSectionId": "The OneNote section ID that is linked to the channel"
}
```

## <a name="retrieving-context-in-private-channels"></a><span data-ttu-id="a17c1-146">Abrufen von Kontext in privaten Kanälen</span><span class="sxs-lookup"><span data-stu-id="a17c1-146">Retrieving context in private channels</span></span>

> [!Note]
> <span data-ttu-id="a17c1-147">Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.</span><span class="sxs-lookup"><span data-stu-id="a17c1-147">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="a17c1-148">Wenn Ihre Inhaltsseite in einem privaten Kanal geladen wird, werden die Daten, die Sie vom `getContext`-Aufruf erhalten, verschleiert, um den Datenschutz des Kanals zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="a17c1-148">When your content page is loaded in a private channel, the data you receive from the `getContext` call will be obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="a17c1-149">Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem privaten Kanal befindet.</span><span class="sxs-lookup"><span data-stu-id="a17c1-149">The following fields are changed when your content page is in a private channel.</span></span> <span data-ttu-id="a17c1-150">Wenn Ihre Seite einen der unten aufgeführten Werte verwendet, müssen Sie das Feld `channelType` überprüfen, um festzustellen, ob Ihre Seite in einem privaten Kanal geladen wird, und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="a17c1-150">If your page makes use of any of the values below, you'll need to check the `channelType` field to determine if your page is loaded in a private channel, and respond appropriately.</span></span>

* <span data-ttu-id="a17c1-151">`groupId`: Nicht definiert für private Kanäle</span><span class="sxs-lookup"><span data-stu-id="a17c1-151">`groupId`: Undefined for private channels</span></span>
* <span data-ttu-id="a17c1-152">`teamId`: Auf threadId des privaten Kanals eingestellt</span><span class="sxs-lookup"><span data-stu-id="a17c1-152">`teamId`: Set to the threadId of the private channel</span></span>
* <span data-ttu-id="a17c1-153">`teamName`: Auf den Namen des privaten Kanals gesetzt</span><span class="sxs-lookup"><span data-stu-id="a17c1-153">`teamName`: Set to the name of the private channel</span></span>
* <span data-ttu-id="a17c1-154">`teamSiteUrl`: Wird auf die URL einer eindeutigen, eindeutigen SharePoint Website für den privaten Kanal festgelegt</span><span class="sxs-lookup"><span data-stu-id="a17c1-154">`teamSiteUrl`: Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="a17c1-155">`teamSitePath`: Stellen Sie den Pfad einer eindeutigen, eindeutigen SharePoint Website für den privaten Kanal ein</span><span class="sxs-lookup"><span data-stu-id="a17c1-155">`teamSitePath`: Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="a17c1-156">`teamSiteDomain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint Standortdomäne für den privaten Kanal festgelegt</span><span class="sxs-lookup"><span data-stu-id="a17c1-156">`teamSiteDomain`: Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

> [!Note]
>  <span data-ttu-id="a17c1-157">„teamSiteUrl“ funktioniert auch für Standardkanäle gut.</span><span class="sxs-lookup"><span data-stu-id="a17c1-157">teamSiteUrl works well for standard channels also.</span></span>

## <a name="theme-change-handling"></a><span data-ttu-id="a17c1-158">Verarbeitung von Designänderungen</span><span class="sxs-lookup"><span data-stu-id="a17c1-158">Theme change handling</span></span>

<span data-ttu-id="a17c1-159">Sie können Ihre App für eine Benachrichtigung, wenn sich das Design ändert, registrieren, indem Sie `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a17c1-159">You can register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="a17c1-160">Das Argument `theme` in der Funktion ist eine Zeichenfolge mit einem Wert von `default`, `dark` oder `contrast`.</span><span class="sxs-lookup"><span data-stu-id="a17c1-160">The `theme` argument in the function will be a string with a value of `default`, `dark`, or `contrast`.</span></span>
