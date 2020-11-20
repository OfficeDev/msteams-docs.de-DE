---
title: Kontext für die Registerkarte abrufen
description: Beschreibt, wie Benutzerkontext auf Ihre Registerkarten abgerufen wird.
keywords: Teams-Registerkarten Benutzerkontext
ms.openlocfilehash: 8c94c4fd895896186ddda20bfaafd1d6ccdc1e73
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346798"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a><span data-ttu-id="4d1e7-104">Kontext für Ihre Microsoft Teams-Registerkarte abrufen</span><span class="sxs-lookup"><span data-stu-id="4d1e7-104">Get context for your Microsoft Teams tab</span></span>

<span data-ttu-id="4d1e7-105">Für Ihre Registerkarte sind möglicherweise Kontextinformationen erforderlich, um relevante Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-105">Your tab might require contextual information to display relevant content.</span></span>

* <span data-ttu-id="4d1e7-106">Auf Ihrer Registerkarte sind möglicherweise grundlegende Informationen zum Benutzer, Team oder Unternehmen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-106">Your tab might need basic information about the user, team, or company.</span></span>
* <span data-ttu-id="4d1e7-107">Auf Ihrer Registerkarte sind möglicherweise Gebietsschema-und Designinformationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-107">Your tab might need locale and theme information.</span></span>
* <span data-ttu-id="4d1e7-108">Möglicherweise müssen Sie die Registerkarte Lesen `entityId` oder das `subEntityId` kennzeichnet, was auf dieser Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-108">Your tab might need to read the `entityId` or `subEntityId` that identifies what is in this tab.</span></span>

## <a name="user-context"></a><span data-ttu-id="4d1e7-109">Benutzerkontext</span><span class="sxs-lookup"><span data-stu-id="4d1e7-109">User context</span></span>

<span data-ttu-id="4d1e7-110">Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn</span><span class="sxs-lookup"><span data-stu-id="4d1e7-110">Context about the user, team or company can be especially useful when</span></span>

* <span data-ttu-id="4d1e7-111">Sie müssen Ressourcen in Ihrer APP mit dem angegebenen Benutzer oder Team erstellen oder zuordnen.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-111">You need to create or associate resources in your app with the specified user or team.</span></span>
* <span data-ttu-id="4d1e7-112">Sie möchten einen Authentifizierungs Fluss für Azure Active Directory oder einen anderen Identitätsanbieter initiieren, und Sie möchten nicht, dass der Benutzer seinen Benutzernamen erneut eingeben muss.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-112">You want to initiate an authentication flow against Azure Active Directory or other identity provider, and you don't want to require the user to enter their username again.</span></span> <span data-ttu-id="4d1e7-113">(Weitere Informationen zur Authentifizierung auf der Registerkarte Microsoft Teams finden Sie unter [Authentifizieren eines Benutzers auf Ihrer Microsoft Teams-Registerkarte](~/concepts/authentication/authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="4d1e7-113">(For more information on authenticating within your Microsoft Teams tab, see [Authenticate a user in your Microsoft Teams tab](~/concepts/authentication/authentication.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d1e7-114">Diese Benutzerinformationen können zwar eine reibungslose Benutzeroberfläche bieten, Sie sollten Sie jedoch *nicht* als Identitätsnachweis verwenden.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-114">Although this user information can help provide a smooth user experience, you should *not* use it as proof of identity.</span></span> <span data-ttu-id="4d1e7-115">Ein Angreifer kann beispielsweise die Seite in einen "schlechten Browser" Laden und ihm alle gewünschten Informationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-115">For example, an attacker could you load your page in a "bad browser" and provide it with any information they want.</span></span>

## <a name="accessing-context"></a><span data-ttu-id="4d1e7-116">Zugreifen auf Kontext</span><span class="sxs-lookup"><span data-stu-id="4d1e7-116">Accessing context</span></span>

<span data-ttu-id="4d1e7-117">Sie können auf zwei Arten auf Kontextinformationen zugreifen:</span><span class="sxs-lookup"><span data-stu-id="4d1e7-117">You can access context information in two ways:</span></span>

* <span data-ttu-id="4d1e7-118">Einfügen von URL-Platzhalterwerten</span><span class="sxs-lookup"><span data-stu-id="4d1e7-118">Insert URL placeholder values</span></span>
* <span data-ttu-id="4d1e7-119">Verwenden des [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client)</span><span class="sxs-lookup"><span data-stu-id="4d1e7-119">Use the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client)</span></span>

### <a name="getting-context-by-inserting-url-placeholder-values"></a><span data-ttu-id="4d1e7-120">Kontext wird abgerufen, indem URL-Platzhalterwerte eingefügt werden</span><span class="sxs-lookup"><span data-stu-id="4d1e7-120">Getting context by inserting URL placeholder values</span></span>

<span data-ttu-id="4d1e7-121">Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-121">Use placeholders in your configuration or content URLs.</span></span> <span data-ttu-id="4d1e7-122">Microsoft Teams ersetzt die Platzhalter durch die entsprechenden Werte beim Bestimmen der tatsächlichen Konfigurations-oder Inhalts-URL, zu der navigiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-122">Microsoft Teams replaces the placeholders with the relevant values when determining the actual configuration or content URL to navigate to.</span></span> <span data-ttu-id="4d1e7-123">Die verfügbaren Platzhalter enthalten alle Felder im [Kontext](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) Objekt.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-123">The available placeholders include all fields on the [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) object.</span></span> <span data-ttu-id="4d1e7-124">Zu den allgemeinen Platzhaltern zählen folgende:</span><span class="sxs-lookup"><span data-stu-id="4d1e7-124">Common placeholders include the following:</span></span>

* <span data-ttu-id="4d1e7-125">{Entitäts Kennung}: die ID, die Sie beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)für das Element auf dieser Registerkarte angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-125">{entityId}: The ID you supplied for the item in this tab when first [configuring the tab](~/tabs/how-to/create-tab-pages/configuration-page.md).</span></span>
* <span data-ttu-id="4d1e7-126">{subentity-ID}: die ID, die Sie beim Generieren einer [tiefen Verknüpfung](~/concepts/build-and-test/deep-links.md) für ein _bestimmtes Element auf_ dieser Registerkarte angegeben haben. Dies sollte verwendet werden, um in einem bestimmten Zustand innerhalb einer Entität wiederherzustellen. beispielsweise scrollen zu einem bestimmten Inhaltselement oder Aktivieren dieses.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-126">{subEntityId}: The ID you supplied when generating a [deep link](~/concepts/build-and-test/deep-links.md) for a specific item _within_ this tab. This should be used to restore to a specific state within an entity; for example, scrolling to or activating a specific piece of content.</span></span>
* <span data-ttu-id="4d1e7-127">{loginHint}: ein Wert, der als Anmelde Hinweis für Azure AD geeignet ist. Dies ist normalerweise der Anmeldename des aktuellen Benutzers in seinem Home-Mandanten.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-127">{loginHint}: A value suitable as a login hint for Azure AD.This is usually the login name of the current user, in their home tenant.</span></span>
* <span data-ttu-id="4d1e7-128">{userPrincipalName}: der Benutzerprinzipal Name des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-128">{userPrincipalName}: The User Principal Name of the current user, in the current tenant.</span></span>
* <span data-ttu-id="4d1e7-129">{userObjectId}: die Azure AD Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-129">{userObjectId}: The Azure AD object ID of the current user, in the current tenant.</span></span>
* <span data-ttu-id="4d1e7-130">{Theme}: das aktuelle Benutzeroberflächendesign wie `default` , `dark` , oder `contrast` .</span><span class="sxs-lookup"><span data-stu-id="4d1e7-130">{theme}: The current UI theme such as `default`, `dark`, or `contrast`.</span></span>
* <span data-ttu-id="4d1e7-131">{Gruppenkennung}: die ID der Office 365 Gruppe, in der sich die Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-131">{groupId}: The ID of the Office 365 Group in which the tab resides.</span></span>
* <span data-ttu-id="4d1e7-132">{TID}: die Azure AD Mandanten-ID des aktuellen Benutzers.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-132">{tid}: The Azure AD tenant ID of the current user.</span></span>
* <span data-ttu-id="4d1e7-133">{locale}: das aktuelle Gebietsschema des Benutzers, der als sprach-Country-Format formatiert ist (beispielsweise "en-US").</span><span class="sxs-lookup"><span data-stu-id="4d1e7-133">{locale}: The current locale of the user formatted as languageId-countryId (for example, en-us).</span></span>
* <span data-ttu-id="4d1e7-134">{osLocaleInfo}: detailliertere Gebietsschemainformationen aus dem Betriebssystem des Benutzers, sofern verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-134">{osLocaleInfo}: More detailed locale info from the user's OS if available.</span></span> <span data-ttu-id="4d1e7-135">Kann zusammen mit folgendem verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="4d1e7-135">Can be used together with:</span></span>
    * <span data-ttu-id="4d1e7-136">das @Microsoft/Globe NPM-Paket, um sicherzustellen, dass Ihre APP das Betriebssystem Datum des Benutzers respektiert und</span><span class="sxs-lookup"><span data-stu-id="4d1e7-136">the @microsoft/globe NPM package to ensure your app respects the user's OS date and</span></span>
    * <span data-ttu-id="4d1e7-137">Zeitformat Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-137">time format configuration.</span></span>
* <span data-ttu-id="4d1e7-138">{SessionID}: eindeutige ID für die aktuelle Teams-Sitzung zur Verwendung in korrelierenden Telemetrie-Daten.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-138">{sessionId}: Unique ID for the current Teams session for use in correlating telemetry data.</span></span>
* <span data-ttu-id="4d1e7-139">{Kanalkennung}: die Microsoft Teams-ID für den Kanal, dem der Inhalt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-139">{channelId}: The Microsoft Teams ID for the channel with which the content is associated.</span></span>
* <span data-ttu-id="4d1e7-140">{ChannelName}: der Name des Kanals, dem der Inhalt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-140">{channelName}: The name for the channel with which the content is associated.</span></span>
* <span data-ttu-id="4d1e7-141">{Chat Kennung}: die Microsoft Teams-ID für den Chat, dem der Inhalt zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-141">{chatId}: The Microsoft Teams ID for the chat with which the content is associated.</span></span>
* <span data-ttu-id="4d1e7-142">{URL}: Inhalts-URL dieser Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-142">{url}: Content URL of this tab.</span></span>
* <span data-ttu-id="4d1e7-143">{websiteUrl}: Website-URL dieser Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-143">{websiteUrl}: Website URL of this tab.</span></span>
* <span data-ttu-id="4d1e7-144">{favoriteChannelsOnly}: Flag, das nur bevorzugte Kanäle auswählen lässt.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-144">{favoriteChannelsOnly}: Flag allowing to select favorite channels only.</span></span>
* <span data-ttu-id="4d1e7-145">{favoriteTeamsOnly}: Flag, das nur bevorzugte Teams auswählen lässt.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-145">{favoriteTeamsOnly}: Flag allowing to select favorite teams only.</span></span>
* <span data-ttu-id="4d1e7-146">{userTeamRole}: Rolle des aktuellen Benutzers im Team.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-146">{userTeamRole}: Role of current user in the team.</span></span>
* <span data-ttu-id="4d1e7-147">{Team Type}: der Typ des Teams.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-147">{teamType}: The type of the team.</span></span>
* <span data-ttu-id="4d1e7-148">{isTeamLocked}: der gesperrte Status des Teams.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-148">{isTeamLocked}: The locked status of the team.</span></span>
* <span data-ttu-id="4d1e7-149">{isTeamArchived}: der archivierte Status des Teams.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-149">{isTeamArchived}: The archived status of the team.</span></span>
* <span data-ttu-id="4d1e7-150">{IsFullScreen}: Angabe, ob die Registerkarte sich im Vollbildmodus befindet.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-150">{isFullScreen}: Indication whether the tab is in full-screen mode.</span></span>
* <span data-ttu-id="4d1e7-151">{teamSiteUrl}: die SharePoint-Stammwebsite, die dem Team zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-151">{teamSiteUrl}: The root SharePoint site associated with the team.</span></span>
* <span data-ttu-id="4d1e7-152">{teamSiteDomain}: die Domäne der SharePoint-Stammwebsite, die dem Team zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-152">{teamSiteDomain}: The domain of the root SharePoint site associated with the team.</span></span>
* <span data-ttu-id="4d1e7-153">{teamSitePath}: der relative Pfad zu der SharePoint-Website, die dem Team zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-153">{teamSitePath}: The relative path to the SharePoint site associated with the team.</span></span>
* <span data-ttu-id="4d1e7-154">{channelRelativeUrl}: der relative Pfad zum SharePoint-Ordner, der dem Kanal zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-154">{channelRelativeUrl}: The relative path to the SharePoint folder associated with the channel.</span></span>
* <span data-ttu-id="4d1e7-155">{tenantSKU}: der Typ der Lizenz für den aktuellen Benutzer Mandanten.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-155">{tenantSKU}: The type of license for the current users tenant.</span></span>
* <span data-ttu-id="4d1e7-156">{Klingelton}: aktuelle Ring-ID.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-156">{ringId}: Current ring ID.</span></span>
* <span data-ttu-id="4d1e7-157">{appSessionId}: eindeutige ID für die aktuelle Sitzung zur Verwendung in korrelierenden Telemetrie-Daten.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-157">{appSessionId}: Unique ID for the current session for use in correlating telemetry data.</span></span>
* <span data-ttu-id="4d1e7-158">{completionBotId}: gibt eine bot-ID an, um das Ergebnis der Interaktion des Benutzers mit dem Aufgabenmodul zu senden.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-158">{completionBotId}: Specifies a bot ID to send the result of the user's interaction with the task module.</span></span>
* <span data-ttu-id="4d1e7-159">{Konversations Kennung}: die ID der Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-159">{conversationId}: The Id of the conversation.</span></span>
* <span data-ttu-id="4d1e7-160">{hostClientType}: Typ des Host Clients. (Mögliche Werte sind: Android, Ios, Internet, Desktop und Rigel.)</span><span class="sxs-lookup"><span data-stu-id="4d1e7-160">{hostClientType}: Type of the host client.(Possible values are: android, ios, web, desktop, and rigel.)</span></span>
* <span data-ttu-id="4d1e7-161">{framecontext}: der Kontext, in dem die Registerkarten-URL geladen wird (Inhalt, Aufgabe, Einstellung, entfernen, sidePanel).</span><span class="sxs-lookup"><span data-stu-id="4d1e7-161">{frameContext}: The context where the tab url is loaded (content, task, setting, remove, sidePanel).</span></span>
* <span data-ttu-id="4d1e7-162">{SharePoint}: Dies ist nur verfügbar, wenn es in SharePoint gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-162">{sharepoint}: This is only available when hosted in SharePoint.</span></span>
* <span data-ttu-id="4d1e7-163">{Besprechungs-Nr}: Sie wird von der Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-163">{meetingId}: It is used by tab when running in meeting context.</span></span>
* <span data-ttu-id="4d1e7-164">{userLicenseType} Der Lizenztyp für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-164">{userLicenseType} The license type for the current user.</span></span>

>[!NOTE]
><span data-ttu-id="4d1e7-165">Der vorherige `{upn}` Platzhalter ist jetzt veraltet.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-165">The previous `{upn}` placeholder is now deprecated.</span></span> <span data-ttu-id="4d1e7-166">Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}` .</span><span class="sxs-lookup"><span data-stu-id="4d1e7-166">For backward compatibility, it is currently a synonym for `{loginHint}`.</span></span>

<span data-ttu-id="4d1e7-167">Angenommen, in Ihrem Tab-Manifest legen Sie das- `configURL` Attribut auf</span><span class="sxs-lookup"><span data-stu-id="4d1e7-167">For example, suppose in your tab manifest you set the `configURL` attribute to</span></span>

`"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`

<span data-ttu-id="4d1e7-168">Und der angemeldete Benutzer verfügt über die folgenden Attribute:</span><span class="sxs-lookup"><span data-stu-id="4d1e7-168">And the signed-in user has the following attributes:</span></span>

* <span data-ttu-id="4d1e7-169">Ihr Benutzername ist "user@example.com"</span><span class="sxs-lookup"><span data-stu-id="4d1e7-169">Their username is 'user@example.com'</span></span>
* <span data-ttu-id="4d1e7-170">Die Mandanten-ID des Unternehmens lautet "e2653c-etc".</span><span class="sxs-lookup"><span data-stu-id="4d1e7-170">Their company tenant ID is 'e2653c-etc'</span></span>
* <span data-ttu-id="4d1e7-171">Sie sind Mitglied der Office 365 Gruppe mit der ID "00209384-etc".</span><span class="sxs-lookup"><span data-stu-id="4d1e7-171">They are a member of the Office 365 group with id '00209384-etc'</span></span>
* <span data-ttu-id="4d1e7-172">Der Benutzer hat sein Microsoft Teams-Design auf "dunkel" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-172">The user has set their Teams theme to 'dark'</span></span>

<span data-ttu-id="4d1e7-173">Bei der Konfiguration Ihrer Registerkarte ruft Microsoft Teams diese URL auf:</span><span class="sxs-lookup"><span data-stu-id="4d1e7-173">When they configure your tab, Teams calls this URL:</span></span>

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a><span data-ttu-id="4d1e7-174">Kontext wird mithilfe der JavaScript-Bibliothek von Microsoft Teams abgerufen.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-174">Getting context by using the Microsoft Teams JavaScript library</span></span>

<span data-ttu-id="4d1e7-175">Sie können die oben aufgeführten Informationen auch mithilfe des [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client) durch Aufrufen abrufen `microsoftTeams.getContext(function(context) { /* ... */ })` .</span><span class="sxs-lookup"><span data-stu-id="4d1e7-175">You can also retrieve the information listed above using the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) by calling `microsoftTeams.getContext(function(context) { /* ... */ })`.</span></span>

<span data-ttu-id="4d1e7-176">Die Kontextvariable wird wie im folgenden Beispiel aussehen.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-176">The context variable will look like the following example.</span></span>

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

## <a name="retrieving-context-in-private-channels"></a><span data-ttu-id="4d1e7-177">Abrufen von Kontext in privaten Kanälen</span><span class="sxs-lookup"><span data-stu-id="4d1e7-177">Retrieving context in private channels</span></span>

> [!Note]
> <span data-ttu-id="4d1e7-178">Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-178">Private channels are currently in private developer preview.</span></span>

<span data-ttu-id="4d1e7-179">Wenn Ihre Inhaltsseite in einen privaten Kanal geladen wird, werden die Daten, die Sie aus dem Aufruf erhalten, `getContext` verschleiert, um die Datenschutzfunktion des Kanals zu schützen.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-179">When your content page is loaded in a private channel, the data you receive from the `getContext` call will be obfuscated to protect the privacy of the channel.</span></span> <span data-ttu-id="4d1e7-180">Die folgenden Felder werden geändert, wenn sich die Inhaltsseite in einem privaten Kanal befindet.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-180">The following fields are changed when your content page is in a private channel.</span></span> <span data-ttu-id="4d1e7-181">Wenn Ihre Seite einen der unten aufgeführten Werte verwendet, müssen Sie das Feld überprüfen, `channelType` um festzustellen, ob Ihre Seite in einen privaten Kanal geladen wird, und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="4d1e7-181">If your page makes use of any of the values below, you'll need to check the `channelType` field to determine if your page is loaded in a private channel, and respond appropriately.</span></span>

* <span data-ttu-id="4d1e7-182">`groupId` -Undefined für private Kanäle</span><span class="sxs-lookup"><span data-stu-id="4d1e7-182">`groupId` - Undefined for private channels</span></span>
* <span data-ttu-id="4d1e7-183">`teamId` -Auf die Thread-Nr des privaten Kanals festlegen</span><span class="sxs-lookup"><span data-stu-id="4d1e7-183">`teamId` - Set to the threadId of the private channel</span></span>
* <span data-ttu-id="4d1e7-184">`teamName` -Auf den Namen des privaten Kanals festlegen</span><span class="sxs-lookup"><span data-stu-id="4d1e7-184">`teamName` - Set to the name of the private channel</span></span>
* <span data-ttu-id="4d1e7-185">`teamSiteUrl` -Festlegen der URL einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="4d1e7-185">`teamSiteUrl` - Set to the URL of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="4d1e7-186">`teamSitePath` -Festlegen des Pfads einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="4d1e7-186">`teamSitePath` - Set to the path of a distinct, unique SharePoint site for the private channel</span></span>
* <span data-ttu-id="4d1e7-187">`teamSiteDomain` -Festlegung auf die Domäne einer eindeutigen, eindeutigen SharePoint-Website Domäne für den privaten Kanal</span><span class="sxs-lookup"><span data-stu-id="4d1e7-187">`teamSiteDomain` - Set to the domain of a distinct, unique SharePoint site domain for the private channel</span></span>

## <a name="theme-change-handling"></a><span data-ttu-id="4d1e7-188">Behandlung von Designänderungen</span><span class="sxs-lookup"><span data-stu-id="4d1e7-188">Theme change handling</span></span>

<span data-ttu-id="4d1e7-189">Sie können Ihre APP so registrieren, dass Sie mitgeteilt wird, wenn sich das Design durch Aufrufen ändert `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` .</span><span class="sxs-lookup"><span data-stu-id="4d1e7-189">You can register your app to be told if the theme changes by calling `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.</span></span>

<span data-ttu-id="4d1e7-190">Das `theme` Argument in der-Funktion ist eine Zeichenfolge mit dem Wert `default` , `dark` oder `contrast` .</span><span class="sxs-lookup"><span data-stu-id="4d1e7-190">The `theme` argument in the function will be a string with a value of `default`, `dark`, or `contrast`.</span></span>
