---
title: Kontext für die Registerkarte abrufen
description: Beschreibt, wie Benutzerkontext auf Ihre Registerkarten abgerufen wird.
keywords: Teams-Registerkarten Benutzerkontext
ms.openlocfilehash: 01919999e38d6b659f014b0f05b76d3f332db9ab
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674091"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a><span data-ttu-id="35a5a-104">Kontext für Ihre Microsoft Teams-Registerkarte abrufen</span><span class="sxs-lookup"><span data-stu-id="35a5a-104">Get context for your Microsoft Teams tab</span></span>

<span data-ttu-id="35a5a-105">Für Ihre Registerkarte sind möglicherweise Kontextinformationen erforderlich, um relevante Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-105">Your tab might require contextual information to display relevant content.</span></span>

* <span data-ttu-id="35a5a-106">Auf Ihrer Registerkarte sind möglicherweise grundlegende Informationen zum Benutzer, Team oder Unternehmen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="35a5a-106">Your tab might need basic information about the user, team, or company.</span></span>
* <span data-ttu-id="35a5a-107">Auf Ihrer Registerkarte sind möglicherweise Gebietsschema-und Designinformationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="35a5a-107">Your tab might need locale and theme information.</span></span>
* <span data-ttu-id="35a5a-108">Möglicherweise müssen Sie die Register `entityId` Karte `subEntityId` lesen oder das kennzeichnet, was auf dieser Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="35a5a-108">Your tab might need to read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="35a5a-109">Benutzerkontext</span><span class="sxs-lookup"><span data-stu-id="35a5a-109">User context</span></span>

<span data-ttu-id="35a5a-110">Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn</span><span class="sxs-lookup"><span data-stu-id="35a5a-110">Context about the user, team or company can be especially useful when</span></span>

* <span data-ttu-id="35a5a-111">Sie müssen Ressourcen in Ihrer APP mit dem angegebenen Benutzer oder Team erstellen oder zuordnen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-111">You need to create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="35a5a-112">Sie möchten einen Authentifizierungs Fluss für Azure Active Directory oder einen anderen Identitätsanbieter initiieren, und Sie möchten nicht, dass der Benutzer seinen Benutzernamen erneut eingeben muss.</span><span class="sxs-lookup"><span data-stu-id="35a5a-112">You want to initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again.</span></span> <span data-ttu-id="35a5a-113">(Weitere Informationen zur Authentifizierung auf der Registerkarte Microsoft Teams finden Sie unter [Authentifizieren eines Benutzers auf Ihrer Microsoft Teams-Registerkarte](~/concepts/authentication/authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="35a5a-113">(For more information on authenticating within your Microsoft Teams tab, see [Authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35a5a-114">Diese Benutzerinformationen können zwar eine reibungslose Benutzeroberfläche bieten, Sie sollten Sie jedoch *nicht* als Identitätsnachweis verwenden.</span><span class="sxs-lookup"><span data-stu-id="35a5a-114">Although this user information can help provide a smooth user experience, you should *not* use it as proof of identity.</span></span> <span data-ttu-id="35a5a-115">Ein Angreifer kann beispielsweise die Seite in einen "schlechten Browser" Laden und ihm alle gewünschten Informationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-115">For example, an attacker could you load your page in a "bad browser" and provide it with any information they want.</span></span>

## <a name="accessing-context"></a><span data-ttu-id="35a5a-116">Zugreifen auf Kontext</span><span class="sxs-lookup"><span data-stu-id="35a5a-116">Accessing context</span></span>

<span data-ttu-id="35a5a-117">Sie können auf zwei Arten auf Kontextinformationen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="35a5a-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="35a5a-118">Einfügen von URL-Platzhalterwerten</span><span class="sxs-lookup"><span data-stu-id="35a5a-118">Insert URL placeholder values</span></span>
* <span data-ttu-id="35a5a-119">Verwenden des [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client)</span><span class="sxs-lookup"><span data-stu-id="35a5a-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client)</span></span>

### <a name="getting-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="35a5a-120">Kontext wird abgerufen, indem URL-Platzhalterwerte eingefügt werden</span><span class="sxs-lookup"><span data-stu-id="35a5a-120">Getting context by inserting URL placeholder values</span></span>

<span data-ttu-id="35a5a-121">Verwenden Sie Platzhalter in ihren Konfigurations-oder Inhalts-URLs.</span><span class="sxs-lookup"><span data-stu-id="35a5a-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="35a5a-122">Microsoft Teams ersetzt die Platzhalter durch die entsprechenden Werte beim Bestimmen der tatsächlichen Konfigurations-oder Inhalts-URL, zu der navigiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="35a5a-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to.</span></span> <span data-ttu-id="35a5a-123">Die verfügbaren Platzhalter enthalten alle Felder im [Kontext](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) Objekt.</span><span class="sxs-lookup"><span data-stu-id="35a5a-123">The available placeholders include all fields on the [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) object.</span></span> <span data-ttu-id="35a5a-124">Zu den allgemeinen Platzhaltern zählen folgende:</span><span class="sxs-lookup"><span data-stu-id="35a5a-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="35a5a-125">{Entitäts Kennung}: die ID, die Sie beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)für das Element auf dieser Registerkarte angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="35a5a-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="35a5a-126">{subentity-ID}: die ID, die Sie beim Generieren einer [tiefen Verknüpfung](~/concepts/build-and-test/deep-links.md) für ein _bestimmtes Element auf_ dieser Registerkarte angegeben haben. Dies sollte verwendet werden, um in einem bestimmten Zustand innerhalb einer Entität wiederherzustellen. beispielsweise scrollen zu einem bestimmten Inhaltselement oder Aktivieren dieses.</span><span class="sxs-lookup"><span data-stu-id="35a5a-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item _within_ this tab. This should be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="35a5a-127">{loginHint}: ein Wert, der als Anmelde Hinweis für Azure AD geeignet ist. Dies ist normalerweise der Anmeldename des aktuellen Benutzers in seinem Home-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="35a5a-127">{loginHint}: A value suitable as a login hint for Azure AD.This is usually the login name of the current user, in their home tenant.</span></span>
* <span data-ttu-id="35a5a-128">{userPrincipalName}: der Benutzerprinzipal Name des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="35a5a-128">{userPrincipalName}: The User Principal Name of the current user, in the current tenant.</span></span>
* <span data-ttu-id="35a5a-129">{userObjectId}: die Azure AD Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="35a5a-129">{userObjectId}: The Azure AD object ID of the current user, in the current tenant.</span></span>
* <span data-ttu-id="35a5a-130">{Theme}: das aktuelle Benutzeroberflächendesign wie `default`, `dark`, oder `contrast`.</span><span class="sxs-lookup"><span data-stu-id="35a5a-130">{theme}: The current UI theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="35a5a-131">{Gruppenkennung}: die ID der Office 365 Gruppe, in der sich die Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="35a5a-131">{groupId}: The ID of the Office 365 Group in which the tab resides.</span></span>
* <span data-ttu-id="35a5a-132">{TID}: die Azure AD Mandanten-ID des aktuellen Benutzers.</span><span class="sxs-lookup"><span data-stu-id="35a5a-132">{tid}: The Azure AD tenant ID of the current user.</span></span>
* <span data-ttu-id="35a5a-133">{locale}: das aktuelle Gebietsschema des Benutzers, der als sprach-Country-Format formatiert ist (beispielsweise "en-US").</span><span class="sxs-lookup"><span data-stu-id="35a5a-133">{locale}: The current locale of the user formatted as languageId-countryId (for example, en-us).</span></span>

>[!NOTE]
><span data-ttu-id="35a5a-134">Der vorherige `{upn}` Platzhalter ist jetzt veraltet.</span><span class="sxs-lookup"><span data-stu-id="35a5a-134">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="35a5a-135">Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym `{loginHint}`für.</span><span class="sxs-lookup"><span data-stu-id="35a5a-135">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="35a5a-136">Angenommen, in Ihrem Tab-Manifest legen Sie das `configURL` -Attribut auf</span><span class="sxs-lookup"><span data-stu-id="35a5a-136">For example, suppose in your tab manifest you set the `configURL` attribute to</span></span>

`"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`

<span data-ttu-id="35a5a-137">Und der angemeldete Benutzer verfügt über die folgenden Attribute:</span><span class="sxs-lookup"><span data-stu-id="35a5a-137">And the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="35a5a-138">Ihr Benutzername ist "user@example.com"</span><span class="sxs-lookup"><span data-stu-id="35a5a-138">Their username is 'user@example.com'</span></span>
* <span data-ttu-id="35a5a-139">Die Mandanten-ID des Unternehmens lautet "e2653c-etc".</span><span class="sxs-lookup"><span data-stu-id="35a5a-139">Their company tenant ID is 'e2653c-etc'</span></span>
* <span data-ttu-id="35a5a-140">Sie sind Mitglied der Office 365 Gruppe mit der ID "00209384-etc".</span><span class="sxs-lookup"><span data-stu-id="35a5a-140">They are a member of the Office 365 group with id '00209384-etc'</span></span>
* <span data-ttu-id="35a5a-141">Der Benutzer hat sein Microsoft Teams-Design auf "dunkel" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="35a5a-141">The user has set their Teams theme to 'dark'</span></span>

<span data-ttu-id="35a5a-142">Bei der Konfiguration Ihrer Registerkarte ruft Microsoft Teams diese URL auf:</span><span class="sxs-lookup"><span data-stu-id="35a5a-142">When they configure your tab, Teams calls this URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="35a5a-143">Kontext wird mithilfe der JavaScript-Bibliothek von Microsoft Teams abgerufen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-143">Getting context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="35a5a-144">Sie können die oben aufgeführten Informationen auch mithilfe des [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client) durch Aufrufen `microsoftTeams.getContext(function(context) { /* ... */ })`abrufen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-144">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="35a5a-145">Die Kontextvariable wird wie im folgenden Beispiel aussehen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-145">The context variable will look like the following example.</span></span>

```json
{
    "teamId": "The Microsoft Teams ID in the format 19:[id]@thread.skype",
    "teamName": "The name of the current team",
    "channelId": "The channel ID in the format 19:[id]@thread.skype",
    "channelName": "The name of the current channel",
    "chatId": "The chat ID in the in the format 19:[id]@thread.skype",
    "locale": "The current locale of the user formatted as languageId-countryId (for example, en-us)",
    "entityId": "The developer-defined unique ID for the entity this content points to",
    "subEntityId": "The developer-defined unique ID for the sub-entity this content points to",
    "loginHint": "A value suitable as a login hint for Azure AD. This is usually the login name of the current user, in their home tenant",
    "userPrincipalName": "The User Principal Name of the current user, in the current tenant",
    "userObjectId": "The Azure AD object id of the current user, in the current tenant",
    "tid": "The Azure AD tenant ID of the current user",
    "groupId": "Guid identifying the current O365 Group ID",
    "theme": "The current UI theme: default | dark | contrast",
    "isFullScreen": "Indicates whether the tab is in full-screen mode",
    "userLicenseType": "Indicates the user licence type in the given SKU (for example, student or teacher)",
    "tenantSKU": "Indicates the SKU category of the tenant (for example, EDU)",
    "channelType": "microsoftTeams.ChannelType.Private | microsoftTeams.ChannelType.Regular"
}
```

## <a name="retrieving-context-in-private-channels"></a><span data-ttu-id="35a5a-146">Abrufen von Kontext in privaten Kanälen</span><span class="sxs-lookup"><span data-stu-id="35a5a-146">Retrieving context in private channels</span></span>

> [!Note]
> <span data-ttu-id="35a5a-147">Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.</span><span class="sxs-lookup"><span data-stu-id="35a5a-147">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="35a5a-148">Wenn Ihre Inhaltsseite in einen privaten Kanal geladen wird, werden die Daten, die Sie `getContext` aus dem Aufruf erhalten, verschleiert, um die Datenschutzfunktion des Kanals zu schützen.</span><span class="sxs-lookup"><span data-stu-id="35a5a-148">When your content page is loaded in a private channel, the data you receive from the `getContext` call will be obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="35a5a-149">Die folgenden Felder werden geändert, wenn sich die Inhaltsseite in einem privaten Kanal befindet.</span><span class="sxs-lookup"><span data-stu-id="35a5a-149">The following fields are changed when your content page is in a private channel.</span></span> <span data-ttu-id="35a5a-150">Wenn Ihre Seite einen der unten aufgeführten Werte verwendet, müssen Sie das `channelType` Feld überprüfen, um festzustellen, ob Ihre Seite in einen privaten Kanal geladen wird, und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="35a5a-150">If your page makes use of any of the values below, you'll need to check the `channelType` field to determine if your page is loaded in a private channel, and respond appropriately.</span></span>

* <span data-ttu-id="35a5a-151">`groupId`-Undefined für private Kanäle</span><span class="sxs-lookup"><span data-stu-id="35a5a-151">`groupId` - Undefined for private channels</span></span>
* <span data-ttu-id="35a5a-152">`teamId`-Auf die Thread-Nr des privaten Kanals festlegen</span><span class="sxs-lookup"><span data-stu-id="35a5a-152">`teamId` - Set to the threadId of the private channel</span></span>
* <span data-ttu-id="35a5a-153">`teamName`-Auf den Namen des privaten Kanals festlegen</span><span class="sxs-lookup"><span data-stu-id="35a5a-153">`teamName` - Set to the name of the private channel</span></span>
* <span data-ttu-id="35a5a-154">`teamSiteUrl`-Festlegen der URL einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="35a5a-154">`teamSiteUrl` - Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="35a5a-155">`teamSitePath`-Festlegen des Pfads einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="35a5a-155">`teamSitePath` - Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="35a5a-156">`teamSiteDomain`-Festlegung auf die Domäne einer eindeutigen, eindeutigen SharePoint-Website Domäne für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="35a5a-156">`teamSiteDomain` - Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

## <a name="theme-change-handling"></a><span data-ttu-id="35a5a-157">Behandlung von Designänderungen</span><span class="sxs-lookup"><span data-stu-id="35a5a-157">Theme change handling</span></span>

<span data-ttu-id="35a5a-158">Sie können Ihre APP so registrieren, dass Sie mitgeteilt wird, wenn sich `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`das Design durch Aufrufen ändert.</span><span class="sxs-lookup"><span data-stu-id="35a5a-158">You can register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="35a5a-159">Das `theme` Argument in der-Funktion ist eine Zeichenfolge mit dem Wert `default`, `dark`oder `contrast`.</span><span class="sxs-lookup"><span data-stu-id="35a5a-159">The `theme` argument in the function will be a string with a value of `default`, `dark`, or `contrast`.</span></span>