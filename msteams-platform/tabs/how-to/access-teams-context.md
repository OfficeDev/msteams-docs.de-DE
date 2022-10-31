---
title: Kontext für Ihre Registerkarte erhalten
description: Erfahren Sie, wie Sie einen Kontext für Ihre Registerkarte, ihren Benutzer-, Team- oder Unternehmenskontext erstellen, auf Informationen zugreifen, Kontext in privaten oder freigegebenen Kanälen abrufen und Designänderungen behandeln.
ms.localizationpriority: high
ms.topic: how-to
ms.openlocfilehash: f0a54dc749d1132918e3ec47ac614aff3ce8aab8
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791545"
---
# <a name="get-context-for-your-tab"></a>Kontext für Ihre Registerkarte erhalten

Ihre Registerkarte erfordert Kontextinformationen, um relevante Inhalte anzuzeigen:

* Grundlegende Informationen zum Benutzer, Team oder Unternehmen.
* Gebietsschema- und Designinformationen.
* Und `page.id` `page.subPageId` , die identifizieren, was sich auf dieser Registerkarte befindet (bekannt als `entityId` und `subEntityId` vor TeamsJS v.2.0.0).

## <a name="user-context"></a>Benutzerkontext

Kontext zum Benutzer, Team oder Unternehmen kann besonders nützlich sein, wenn:

* Sie erstellen oder ordnen Ressourcen in Ihrer App dem angegebenen Benutzer oder Team zu.
* Sie initiieren einen Authentifizierungsflow von Microsoft Azure Active Directory (Azure AD) oder einem anderen Identitätsanbieter, und Sie erfordern nicht, dass der Benutzer seinen Benutzernamen erneut eingibt.

Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers in Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Obwohl diese Benutzerinformationen zu einer reibungslosen Benutzererfahrung beitragen können, dürfen Sie sie nicht als Identitätsnachweis verwenden.  Beispielsweise kann ein Angreifer Ihre Seite in einem Browser laden und schädliche Informationen oder Anforderungen rendern.

## <a name="access-context-information"></a>Zugreifen auf Kontextinformationen

Sie können auf zwei Arten auf Kontextinformationen zugreifen:

* Verwenden von [URL-Platzhalterwerten](#get-context-by-inserting-url-placeholder-values).
* Aus dem [Microsoft](/javascript/api/@microsoft/teams-js/app.context) Teams JavaScript-Client-SDK-Kontextobjekt.

### <a name="get-context-by-inserting-url-placeholder-values"></a>Abrufen des Kontexts durch Einfügen von URL-Platzhalterwerten

Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs. Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird. Die verfügbaren Platzhalter enthalten alle Felder im [Kontextobjekt](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) . Allgemeine Platzhalter umfassen die folgenden Eigenschaften:

* [{page.id}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-id): Die vom Entwickler definierte eindeutige ID für die Seite, die beim ersten [Konfigurieren der Seite](~/tabs/how-to/create-tab-pages/configuration-page.md) definiert wurde. (Bekannt als `{entityId}` vor TeamsJS v.2.0.0).
* [{page.subPageId}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-subpageid): Die vom Entwickler definierte eindeutige ID für die Unterseite, auf die dieser Inhalt verweist, der beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element innerhalb der Seite definiert wurde. (Bekannt als `{subEntityId}` vor TeamsJS v.2.0.0).
* [{user.loginHint}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-loginhint): Ein Wert, der als Anmeldehinweis für Azure AD geeignet ist. Dies ist in der Regel der Anmeldename des aktuellen Benutzers in ihrem Basismandanten. (Bekannt als `{loginHint}` vor TeamsJS v.2.0.0).
* [{user.userPrincipalName}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-userprincipalname): Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten. (Bekannt als `{userPrincipalName}` vor TeamsJS v.2.0.0).
* [{user.id}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-id): Die Azure AD-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten. (Bekannt als `{userObjectId}` vor TeamsJS v.2.0.0).
* [{app.theme}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-theme): Das aktuelle Design der Benutzeroberfläche wie `default`, `dark`oder `contrast`. (Bekannt als `{theme}` vor TeamsJS v.2.0.0).
* [{team.groupId}](/javascript/api/@microsoft/teams-js/app.teaminfo#@microsoft-teams-js-app-teaminfo-groupid): Die ID der Office 365 Gruppe, in der sich die Registerkarte befindet. (Bekannt als `{groupId}` vor TeamsJS v.2.0.0)
* [{user.tenant.id}](/javascript/api/@microsoft/teams-js/app.tenantinfo#@microsoft-teams-js-app-tenantinfo-id): Die Azure AD-Mandanten-ID des aktuellen Benutzers. (Bekannt als `{tid}` vor TeamsJS v.2.0.0).
* [{app.locale}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-locale): Das aktuelle Gebietsschema des Benutzers, das als *languageId-countryId formatiert ist*, z. B `en-us`. . (Bekannt als `{locale}` vor TeamsJS v.2.0.0).

> [!NOTE]
> Der bisherige Platzhalter `{upn}` ist nun veraltet. Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{user.loginHint}`.

Wenn Sie beispielsweise in Ihrem App-Manifest ihr tab *configurationUrl-Attribut* auf `"https://www.contoso.com/config?name={user.loginHint}&tenant={user.tenant.id}&group={team.groupId}&theme={app.theme}"` festlegen und der angemeldete Benutzer über die folgenden Attribute verfügt:

* Ihr Benutzername ist **user@example.com**.
* Ihre Firmenmandanten-ID lautet **e2653c-etc**.
* Sie sind Mitglied der Office 365-Gruppe mit der ID **00209384-etc**.
* Der Benutzer hat sein Teams-Design auf **dunkel** festgelegt.

. . . Dann ruft Teams beim Konfigurieren der Registerkarte die folgende URL auf:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Abrufen von Kontext mithilfe der JavaScript-Bibliothek von Microsoft Teams

Sie können die zuvor aufgeführten Informationen auch mithilfe des [JavaScript-Client-SDKs von Microsoft Teams](/javascript/api/overview/msteams-client) abrufen, indem Sie `microsoftTeams.getContext(function(context) { /* ... */ })` aufrufen.

Der folgende Code enthält ein Beispiel für eine Kontextvariable:

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
    "groupId": "Guid identifying the current Office 365 Group ID",
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
    "hostClientType": "The type of host client. Possible values are android, ios, web, desktop, surfaceHub, teamsRoomsAndroid, teamsPhones, teamsDisplays rigel (deprecated, use teamsRoomsWindows instead)",
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
    "defaultOneNoteSectionId": "The OneNote section ID that is linked to the channel",
    "isMultiWindow": "The indication whether the tab is in a pop out window"
}
```

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

## <a name="typescript"></a>TypeScript

```TypeScript
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context: Context) => {
    /*...*/
});
```

Entsprechendes `async/await` Muster:

```TypeScript
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context: Context = await app.getContext();
  /*...*/
}
```

## <a name="javascript"></a>JavaScript

```js
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context) => {
    /*...*/
});
```

Entsprechendes `async/await` Muster:

```js
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context = await app.getContext();
  /*...*/
}
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

## <a name="typescript"></a>TypeScript

```TypeScript
import * as microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context: microsoftTeams.Context) => {
  /* ... */
});
```

## <a name="javascript"></a>JavaScript

```js
import microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context) => {
  /* ... */ 
});
```

---

In der folgenden Tabelle sind häufig verwendete Kontexteigenschaften des *Kontextobjekts* aufgeführt:

| TeamsJS v2-Name | TeamsJS v1-Name | Beschreibung |
|-----------------|-----------------|-------------|
| team.internalId | teamId | Die Microsoft Teams-ID für das Team, dem der Inhalt zugeordnet ist. |
| team.displayName | teamName | Der Name des Teams, dem der Inhalt zugeordnet ist. |
| channel.id | channelId | Die Microsoft Teams-ID für den Kanal, dem der Inhalt zugeordnet ist. |
| channel.displayName | Channelname | Der Name für den Kanal, dem der Inhalt zugeordnet ist. |
| chat.id | chatId | Die Microsoft Teams-ID für den Chat, dem der Inhalt zugeordnet ist. |
| app.locale | Gebietsschema | Das aktuelle Gebietsschema, das der Benutzer für die Als languageId-countryId formatierte App konfiguriert hat (z. B. en-us). |
| page.id | entityId | Die vom Entwickler definierte eindeutige ID für die Seite, auf die dieser Inhalt verweist. |
| page.subPageId | subEntityId | Die vom Entwickler definierte eindeutige ID für die Unterseite, auf die dieser Inhalt verweist. Dieses Feld sollte verwendet werden, um einen bestimmten Zustand innerhalb einer Seite wiederherzustellen, z. B. zum Scrollen zu oder Aktivieren eines bestimmten Inhaltsabschnitts. |
| user.loginHint | loginHint | Ein Wert, der für die Verwendung als login_hint bei der Authentifizierung mit Azure AD geeignet ist. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführen kann, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist, und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| user.userPrincipalName | Upn | Der UPN des aktuellen Benutzers. Dies kann ein extern authentifizierter UPN sein (z. B. Gastbenutzer). Da eine böswillige Partei Ihre Inhalte in einem Browser ausführt, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist, und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| user.id | userObjectId | Die Azure AD-Objekt-ID des aktuellen Benutzers. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführt, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist, und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| user.tenant.id | Tid | Die Azure AD-Mandanten-ID des aktuellen Benutzers. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführen kann, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist, und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| team.groupId | groupId | Die Office 365 Gruppen-ID für das Team, dem der Inhalt zugeordnet ist. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| app.theme  | theme | Das aktuelle UI-Design: Standard, Dunkel, Kontrast |
| page.isFullScreen | isFullScreen | Gibt an, ob sich die Seite im Vollbildmodus befindet. |
| team.type | teamType | Der Typ des Teams. |
| sharepointSite.teamSiteUrl | teamSiteUrl | Die SharePoint-Stammwebsite, die dem Team zugeordnet ist. |
| sharepointSite.teamSiteDomain | teamSiteDomain | Die Domäne der SharePoint-Stammwebsite, die dem Team zugeordnet ist. |
| sharepointSite.teamSitePath | teamSitePath | Der relative Pfad zur SharePoint-Website, die dem Team zugeordnet ist. |
| channel.relativeUrl | channelRelativeUrl | Der relative Pfad zum SharePoint-Ordner, der dem Kanal zugeordnet ist. |
| app.host.sessionId | Sessionid | Eindeutige ID für die aktuelle Hostsitzung zum Korrelieren von Telemetriedaten. |
| team.userRole | userTeamRole | Die Rolle des Benutzers im Team. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführen kann, sollte dieser Wert nur als Hinweis auf die Rolle des Benutzers und niemals als Nachweis ihrer Rolle verwendet werden. |
| team.isArchived | isTeamArchived | Gibt an, ob das Team archiviert wird. Apps sollten dies als Signal verwenden, um Änderungen an Inhalten zu verhindern, die mit archivierten Teams verknüpft sind. |
| app.host.clientType | hostClientType | Der Typ des Hostclients. Mögliche Werte sind: android, ios, web, desktop, rigel |
| page.frameContext | frameContext | Der Kontext, in dem die Seiten-URL geladen wird (Inhalt, Aufgabe, Einstellung, Entfernen, sidePanel) |
| sharepoint | sharepoint | SharePoint-Kontext. Dies ist nur verfügbar, wenn sie in SharePoint gehostet wird. |
| user.tenant.teamsSku | tenantSKU | Der Lizenztyp für den aktuellen Benutzermandanten. Mögliche Werte sind enterprise, free, edu, unknown |
| user.licenseType | userLicenseType | Der Lizenztyp für den aktuellen Benutzer. Mögliche Werte sind E1-, E3- und E5-Enterprise-Pläne. |
| app.parentMessageId | parentMessageId | Die ID der übergeordneten Nachricht, aus der dieses Aufgabenmodul gestartet wurde. Dies ist nur in Aufgabenmodulen verfügbar, die über Botkarten gestartet werden. |
| app.host.ringId | ringId | Aktuelle Ring-ID. |
| app.sessionId | appSessionId | Eindeutige ID für die aktuelle Hostsitzung zum Korrelieren von Telemetriedaten. |
| user.isCallingAllowed | isCallingAllowed | Gibt an, ob der Aufruf für den aktuell angemeldeten Benutzer zulässig ist. |
| user.isPSTNCallingAllowed | isPSTNCallingAllowed | Gibt an, ob PSTN-Anrufe für den aktuellen Benutzer zulässig sind. |
| meeting.id | meetingId | Die Besprechungs-ID, die von der Registerkarte verwendet wird, wenn sie im Besprechungskontext ausgeführt wird. |
| channel.defaultOneNoteSectionId | defaultOneNoteSectionId | Die Mit dem Kanal verknüpfte OneNote-Abschnitts-ID. |
| page.isMultiWindow | isMultiWindow | Die Angabe, ob sich die Registerkarte in einem Popupfenster befindet. |

Weitere Informationen finden Sie unter [Aktualisierungen zur *Kontextschnittstelle*](using-teams-client-sdk.md#updates-to-the-context-interface) und in der [Referenz zur Kontextschnittstellen-API](/javascript/api/@microsoft/teams-js/app.context).

## <a name="retrieve-context-in-private-channels"></a>Abrufen des Kontexts in privaten Kanälen

> [!NOTE]
> Private Kanäle befinden sich derzeit nur in der privaten Entwicklervorschau.

Wenn Ihre Inhaltsseite in einem privaten Kanal geladen wird, werden die Daten, die `getContext` Sie vom Anruf erhalten, verschleiert, um die Privatsphäre des Kanals zu schützen.

Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem privaten Kanal befindet:

* `team.groupId`: Für private Kanäle nicht definiert
* `team.internalId`: Auf die ThreadId des privaten Kanals festgelegt
* `team.displayName`: Auf den Namen des privaten Kanals festgelegt
* `sharepointSite.url`: Auf die URL einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal festgelegt
* `sharepointSite.path`: Auf den Pfad einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal festgelegt
* `sharepointSite.domain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint-Websitedomäne für den privaten Kanal festgelegt

Wenn Ihre Seite einen dieser Werte verwendet, muss der Wert des `channel.membershipType` Felds lauten `Private` , um zu bestimmen, ob Ihre Seite in einem privaten Kanal geladen ist und entsprechend reagieren kann.

> [!NOTE]
>`teamSiteUrl` eignet sich auch gut für Standardkanäle. Wenn Ihre Seite einen dieser Werte verwendet, muss der Wert des `channelType` Felds lauten `Shared` , um zu bestimmen, ob Ihre Seite in einem freigegebenen Kanal geladen ist und entsprechend reagieren kann.

## <a name="get-context-in-shared-channels"></a>Abrufen von Kontext in freigegebenen Kanälen

Wenn die Inhalts-UX in einem freigegebenen Kanal geladen wird, verwenden Sie die vom Aufruf empfangenen Daten für Änderungen am `getContext` freigegebenen Kanal. Wenn tab einen der folgenden Werte verwendet, müssen Sie das `channelType` Feld auffüllen, um festzustellen, ob die Registerkarte in einem freigegebenen Kanal geladen ist, und entsprechend reagieren.
Bei freigegebenen Kanälen ist `null`der `groupId` Wert , da die groupId des Hostteams die tatsächliche Mitgliedschaft des freigegebenen Kanals nicht genau widerspiegelt. Um dies zu beheben, werden die `hostTeamGroupID` Eigenschaften und `hostTenantID` neu hinzugefügt und sind nützlich, um Microsoft Graph-API Aufrufe zum Abrufen der Mitgliedschaft auszuführen. `hostTeam` verweist auf das Team, das den freigegebenen Kanal erstellt hat. `currentTeam` verweist auf team, von dem der aktuelle Benutzer auf den freigegebenen Kanal zugreift.

Weitere Informationen zu diesen Konzepten finden Sie unter [Freigegebene Kanäle](~/concepts/build-and-test/shared-channels.md).

Verwenden Sie die folgenden `getContext` Eigenschaften in freigegebenen Kanälen:

| Eigenschaft | Beschreibung |
|----------|--------------|
|`channelId`| Die -Eigenschaft ist auf die Thread-ID für freigegebene Kanäle festgelegt.|
|`channelType`| Die -Eigenschaft ist für freigegebene Kanäle auf `sharedChannel` festgelegt.|
|`groupId`|Die -Eigenschaft gilt `null` für freigegebene Kanäle.|
|`hostTenantId`| Die -Eigenschaft wird neu hinzugefügt und beschreibt die Mandanten-ID des Hosts, die für den Vergleich mit der Mandanten-ID-Eigenschaft des `tid` aktuellen Benutzers nützlich ist. |
|`hostTeamGroupId`| Die -Eigenschaft wurde neu hinzugefügt und beschreibt die Azure AD-Gruppen-ID des Hostteams, die nützlich ist, um Microsoft Graph-API Aufrufe zum Abrufen der Mitgliedschaft im freigegebenen Kanal auszuführen. |
|`teamId`|Die -Eigenschaft wird neu hinzugefügt und auf die Thread-ID des aktuellen freigegebenen Teams festgelegt. |
|`teamName`|Die -Eigenschaft ist auf die des aktuellen freigegebenen `teamName`Teams festgelegt. |
|`teamType`|Die -Eigenschaft ist auf die des aktuellen freigegebenen `teamType`Teams festgelegt.|
|`teamSiteUrl`|Die -Eigenschaft beschreibt die des freigegebenen Kanals `channelSiteUrl`.|
|`teamSitePath`| Die -Eigenschaft beschreibt die des freigegebenen Kanals `channelSitePath`.|
|`teamSiteDomain`| Die -Eigenschaft beschreibt die des freigegebenen Kanals `channelSiteDomain`.|
|`tenantSKU`| Die -Eigenschaft beschreibt die des Hostteams `tenantSKU`.|
|`tid`|  Die -Eigenschaft beschreibt die Mandanten-ID des aktuellen Benutzers.|
|`userObjectId`|  Die -Eigenschaft beschreibt die ID des aktuellen Benutzers.|
|`userPrincipalName`| Die -Eigenschaft beschreibt den UPN des aktuellen Benutzers.|

Weitere Informationen zu freigegebenen Kanälen finden Sie unter [Freigegebene Kanäle](~/concepts/build-and-test/shared-channels.md).

## <a name="handle-theme-change"></a>Behandeln von Designänderungen

Sie können Ihre App registrieren, um informiert zu werden, wenn sich das Design ändert, indem Sie aufrufen `microsoftTeams.app.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

Das `theme` Argument in der Funktion ist eine Zeichenfolge mit dem Wert `default`, `dark`oder `contrast`.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Richtlinien zum Entwerfen von Registerkarten](../../tabs/design/tabs.md)
* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
