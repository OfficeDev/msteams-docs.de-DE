---
title: Kontext für Ihre Registerkarte erhalten
description: Beschreibt, wie Sie Benutzerkontext zu Ihren Registerkarten abrufen
localization_priority: Normal
ms.topic: how-to
keywords: Teams Registerkarten Benutzerkontext
ms.openlocfilehash: 8c91cf5a65f13d9f58f6ae8aa2678266c37338c8
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179727"
---
# <a name="get-context-for-your-tab"></a><span data-ttu-id="ec28b-104">Kontext für Ihre Registerkarte erhalten</span><span class="sxs-lookup"><span data-stu-id="ec28b-104">Get context for your tab</span></span>

<span data-ttu-id="ec28b-105">Ihre Registerkarte erfordert Kontextinformationen, um relevante Inhalte anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="ec28b-105">Your tab requires contextual information to display relevant content:</span></span>

* <span data-ttu-id="ec28b-106">Grundlegende Informationen über den Benutzer, das Team oder das Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="ec28b-106">Basic information about the user, team, or company.</span></span>
* <span data-ttu-id="ec28b-107">Gebietsschema- und Designinformationen.</span><span class="sxs-lookup"><span data-stu-id="ec28b-107">Locale and theme information.</span></span>
* <span data-ttu-id="ec28b-108">Lesen Sie die `entityId` `subEntityId` Oder, die identifiziert, was sich auf dieser Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="ec28b-108">Read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="ec28b-109">Benutzerkontext</span><span class="sxs-lookup"><span data-stu-id="ec28b-109">User context</span></span>

<span data-ttu-id="ec28b-110">Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn:</span><span class="sxs-lookup"><span data-stu-id="ec28b-110">Context about the user, team, or company can be especially useful when:</span></span>

* <span data-ttu-id="ec28b-111">Sie erstellen ressourcen in Ihrer App oder ordnen sie dem angegebenen Benutzer oder Team zu.</span><span class="sxs-lookup"><span data-stu-id="ec28b-111">You create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="ec28b-112">Sie initiieren einen Authentifizierungsfluss von Azure Active Directory (AAD) oder einem anderen Identitätsanbieter, und Sie müssen den Benutzer nicht erneut eingeben.</span><span class="sxs-lookup"><span data-stu-id="ec28b-112">You initiate an authentication flow from Azure Active Directory (AAD) or other identity provider, and you do not require the user to enter their username again.</span></span> <span data-ttu-id="ec28b-113">Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers auf der Registerkarte Microsoft Teams.](~/concepts/authentication/authentication.md)</span><span class="sxs-lookup"><span data-stu-id="ec28b-113">For more information, see [authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec28b-114">Obwohl diese Benutzerinformationen zu einer reibungslosen Benutzererfahrung beitragen können, dürfen Sie sie nicht als Identitätsnachweis verwenden.</span><span class="sxs-lookup"><span data-stu-id="ec28b-114">Although this user information can help provide a smooth user experience, you must not use it as proof of identity.</span></span> <span data-ttu-id="ec28b-115">Beispielsweise kann ein Angreifer Ihre Seite in einem Browser laden und schädliche Informationen oder Anforderungen rendern.</span><span class="sxs-lookup"><span data-stu-id="ec28b-115">For example, an attacker can load your page in a browser and render harmful information or requests.</span></span>

## <a name="access-context-information"></a><span data-ttu-id="ec28b-116">Zugreifen auf Kontextinformationen</span><span class="sxs-lookup"><span data-stu-id="ec28b-116">Access context information</span></span>

<span data-ttu-id="ec28b-117">Sie können auf zwei Arten auf Kontextinformationen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="ec28b-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="ec28b-118">Fügen Sie URL-Platzhalterwerte ein.</span><span class="sxs-lookup"><span data-stu-id="ec28b-118">Insert URL placeholder values.</span></span>
* <span data-ttu-id="ec28b-119">Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK.](/javascript/api/overview/msteams-client)</span><span class="sxs-lookup"><span data-stu-id="ec28b-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client).</span></span>

### <a name="get-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="ec28b-120">Abrufen von Kontext durch Einfügen von URL-Platzhalterwerten</span><span class="sxs-lookup"><span data-stu-id="ec28b-120">Get context by inserting URL placeholder values</span></span>

<span data-ttu-id="ec28b-121">Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs.</span><span class="sxs-lookup"><span data-stu-id="ec28b-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="ec28b-122">Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="ec28b-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL.</span></span> <span data-ttu-id="ec28b-123">Die verfügbaren Platzhalter enthalten alle Felder im [Kontextobjekt.](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ec28b-123">The available placeholders include all fields on the [context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) object.</span></span> <span data-ttu-id="ec28b-124">Häufige Platzhalter sind folgende:</span><span class="sxs-lookup"><span data-stu-id="ec28b-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="ec28b-125">{entityId}: Die ID, die Sie für das Element auf dieser Registerkarte beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md) angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="ec28b-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="ec28b-126">{subEntityId}: Die ID, die Sie beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element auf dieser Registerkarte angegeben haben. Dies muss verwendet werden, um einen bestimmten Zustand innerhalb einer Entität wiederherzustellen. Beispiel: Scrollen zu oder Aktivieren eines bestimmten Inhaltselements.</span><span class="sxs-lookup"><span data-stu-id="ec28b-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item within this tab. This must be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="ec28b-127">{loginHint}: Ein Wert, der als Anmeldehinweis für AAD geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="ec28b-127">{loginHint}: A value suitable as a login hint for AAD.</span></span> <span data-ttu-id="ec28b-128">Dies ist in der Regel der Anmeldename des aktuellen Benutzers in seiner Startseitenmandanten.</span><span class="sxs-lookup"><span data-stu-id="ec28b-128">This is usually the login name of the current user in their home tenant.</span></span>
* <span data-ttu-id="ec28b-129">{userPrincipalName}: Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="ec28b-129">{userPrincipalName}: The User Principal Name of the current user in the current tenant.</span></span>
* <span data-ttu-id="ec28b-130">{userObjectId}: Die AAD-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="ec28b-130">{userObjectId}: The AAD object ID of the current user in the current tenant.</span></span>
* <span data-ttu-id="ec28b-131">{theme}: Das aktuelle Benutzeroberflächendesign wie `default` , `dark` oder `contrast` .</span><span class="sxs-lookup"><span data-stu-id="ec28b-131">{theme}: The current user interface (UI) theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="ec28b-132">{groupId}: Die ID der Office 365 Gruppe, in der sich die Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="ec28b-132">{groupId}: The ID of the Office 365 group in which the tab resides.</span></span>
* <span data-ttu-id="ec28b-133">{tid}: Die AAD-Mandanten-ID des aktuellen Benutzers.</span><span class="sxs-lookup"><span data-stu-id="ec28b-133">{tid}: The AAD tenant ID of the current user.</span></span>
* <span data-ttu-id="ec28b-134">{locale}: Das aktuelle Gebietsschema des Benutzers, das als languageId-countryId formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="ec28b-134">{locale}: The current locale of the user formatted as languageId-countryId.</span></span> <span data-ttu-id="ec28b-135">Beispiel: en-us.</span><span class="sxs-lookup"><span data-stu-id="ec28b-135">For example, en-us.</span></span>

> [!NOTE]
> <span data-ttu-id="ec28b-136">Der bisherige Platzhalter `{upn}` ist nun veraltet.</span><span class="sxs-lookup"><span data-stu-id="ec28b-136">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="ec28b-137">Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}`.</span><span class="sxs-lookup"><span data-stu-id="ec28b-137">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="ec28b-138">In Ihrem Registerkartenmanifest legen Sie das Attribut beispielsweise `configURL` auf `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"` fest, dass der angemeldete Benutzer die folgenden Attribute hat:</span><span class="sxs-lookup"><span data-stu-id="ec28b-138">For example, in your tab manifest you set the `configURL` attribute to `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`, the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="ec28b-139">Ihr Benutzername ist **user@example.com.**</span><span class="sxs-lookup"><span data-stu-id="ec28b-139">Their username is **user@example.com**.</span></span>
* <span data-ttu-id="ec28b-140">Die Mandanten-ID des Unternehmens lautet **e2653c usw.**</span><span class="sxs-lookup"><span data-stu-id="ec28b-140">Their company tenant ID is **e2653c-etc**.</span></span>
* <span data-ttu-id="ec28b-141">Sie sind Mitglied der Office 365-Gruppe mit id **00209384-usw.**</span><span class="sxs-lookup"><span data-stu-id="ec28b-141">They are a member of the Office 365 group with id **00209384-etc**.</span></span>
* <span data-ttu-id="ec28b-142">Der Benutzer hat sein Teams Design auf **dunkel** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ec28b-142">The user has set their Teams theme to **dark**.</span></span>

<span data-ttu-id="ec28b-143">Wenn sie die Registerkarte konfigurieren, ruft Teams die folgende URL auf:</span><span class="sxs-lookup"><span data-stu-id="ec28b-143">When they configure the tab, Teams calls the following URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="ec28b-144">Abrufen von Kontext mithilfe der Microsoft Teams JavaScript-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="ec28b-144">Get context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="ec28b-145">Sie können die zuvor aufgeführten Informationen auch mithilfe des [JavaScript-Client-SDKs von Microsoft Teams](/javascript/api/overview/msteams-client) abrufen, indem Sie `microsoftTeams.getContext(function(context) { /* ... */ })` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ec28b-145">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="ec28b-146">Der folgende Code enthält ein Beispiel für eine Kontextvariable:</span><span class="sxs-lookup"><span data-stu-id="ec28b-146">The following code provides an example of context variable:</span></span>

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

## <a name="retrieve-context-in-private-channels"></a><span data-ttu-id="ec28b-147">Abrufen von Kontext in privaten Kanälen</span><span class="sxs-lookup"><span data-stu-id="ec28b-147">Retrieve context in private channels</span></span>

> [!Note]
> <span data-ttu-id="ec28b-148">Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.</span><span class="sxs-lookup"><span data-stu-id="ec28b-148">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="ec28b-149">Wenn Ihre Inhaltsseite in einem privaten Kanal geladen wird, werden die Daten, die Sie vom Anruf erhalten, `getContext` verborgen, um den Datenschutz des Kanals zu schützen.</span><span class="sxs-lookup"><span data-stu-id="ec28b-149">When your content page is loaded in a private channel, the data you receive from the `getContext` call is obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="ec28b-150">Die folgenden Felder werden geändert, wenn sich Die Inhaltsseite in einem privaten Kanal befindet:</span><span class="sxs-lookup"><span data-stu-id="ec28b-150">The following fields are changed when your content page is in a private channel:</span></span>

* <span data-ttu-id="ec28b-151">`groupId`: Nicht definiert für private Kanäle</span><span class="sxs-lookup"><span data-stu-id="ec28b-151">`groupId`: Undefined for private channels</span></span>
* <span data-ttu-id="ec28b-152">`teamId`: Auf die threadId des privaten Kanals festgelegt</span><span class="sxs-lookup"><span data-stu-id="ec28b-152">`teamId`: Set to the threadId of the private channel</span></span>
* <span data-ttu-id="ec28b-153">`teamName`: Auf den Namen des privaten Kanals festgelegt</span><span class="sxs-lookup"><span data-stu-id="ec28b-153">`teamName`: Set to the name of the private channel</span></span>
* <span data-ttu-id="ec28b-154">`teamSiteUrl`: Legen Sie die URL einer eindeutigen SharePoint-Website für den privaten Kanal fest.</span><span class="sxs-lookup"><span data-stu-id="ec28b-154">`teamSiteUrl`: Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="ec28b-155">`teamSitePath`: Legen Sie den Pfad einer bestimmten, eindeutigen SharePoint-Website für den privaten Kanal fest.</span><span class="sxs-lookup"><span data-stu-id="ec28b-155">`teamSitePath`: Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="ec28b-156">`teamSiteDomain`: Festlegen auf die Domäne einer eindeutigen SharePoint-Websitedomäne für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="ec28b-156">`teamSiteDomain`: Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

<span data-ttu-id="ec28b-157">Wenn Ihre Seite einen dieser Werte verwendet, müssen Sie das Feld überprüfen, `channelType` um festzustellen, ob Die Seite in einem privaten Kanal geladen ist, und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="ec28b-157">If your page makes use of any of these values, you must check the `channelType` field to determine if your page is loaded in a private channel and respond appropriately.</span></span>

> [!Note]
> <span data-ttu-id="ec28b-158">`teamSiteUrl` funktioniert auch gut für Standardkanäle.</span><span class="sxs-lookup"><span data-stu-id="ec28b-158">`teamSiteUrl` also works well for standard channels.</span></span>

## <a name="handle-theme-change"></a><span data-ttu-id="ec28b-159">Behandeln von Designänderungen</span><span class="sxs-lookup"><span data-stu-id="ec28b-159">Handle theme change</span></span>

<span data-ttu-id="ec28b-160">Sie können Ihre App registrieren, um informiert zu werden, wenn sich das Design ändert, indem Sie `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ec28b-160">You can register your app to be informed if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="ec28b-161">Das `theme` Argument in der Funktion ist eine Zeichenfolge mit dem Wert , oder `default` `dark` `contrast` .</span><span class="sxs-lookup"><span data-stu-id="ec28b-161">The `theme` argument in the function is a string with a value of `default`, `dark`, or `contrast`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec28b-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ec28b-162">See also</span></span>

* [<span data-ttu-id="ec28b-163">Richtlinien für den Registerkartenentwurf</span><span class="sxs-lookup"><span data-stu-id="ec28b-163">Tab design guidelines</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="ec28b-164">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="ec28b-164">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="ec28b-165">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ec28b-165">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="ec28b-166">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="ec28b-166">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a><span data-ttu-id="ec28b-167">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ec28b-167">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec28b-168">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="ec28b-168">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)