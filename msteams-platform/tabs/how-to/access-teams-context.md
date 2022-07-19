---
title: Kontext für Ihre Registerkarte erhalten
description: In diesem Modul erfahren Sie, wie Sie Benutzerkontext zu Ihren Registerkarten, Benutzerkontext und Access-Kontextinformationen abrufen.
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: 63bbc9c0e5f20e293f9230000597860e3f053274
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841722"
---
# <a name="get-context-for-your-tab"></a>Kontext für Ihre Registerkarte erhalten

Ihre Registerkarte erfordert Kontextinformationen, um relevante Inhalte anzuzeigen:

* Grundlegende Informationen über den Benutzer, das Team oder das Unternehmen.
* Gebietsschema- und Designinformationen.
* Das `page.id` und `page.subPageId` das identifizieren, was sich auf dieser Registerkarte befindet (bekannt als `entityId` und `subEntityId` vor TeamsJS v.2.0.0).

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="user-context"></a>Benutzerkontext

Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn:

* Sie erstellen oder ordnen Ressourcen in Ihrer App dem angegebenen Benutzer oder Team zu.
* Sie initiieren einen Authentifizierungsfluss von Microsoft Azure Active Directory (Azure AD) oder einem anderen Identitätsanbieter, und Sie müssen den Benutzer nicht erneut zum Eingeben seines Benutzernamens auffordern.

Weitere Informationen finden Sie [unter Authentifizieren eines Benutzers in Ihren Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Obwohl diese Benutzerinformationen zu einer reibungslosen Benutzererfahrung beitragen können, dürfen Sie sie nicht als Identitätsnachweis verwenden.  Beispielsweise kann ein Angreifer Ihre Seite in einen Browser laden und schädliche Informationen oder Anforderungen rendern.

## <a name="access-context-information"></a>Zugreifen auf Kontextinformationen

Sie können auf zwei Arten auf Kontextinformationen zugreifen:

* Verwenden von [URL-Platzhalterwerten](#get-context-by-inserting-url-placeholder-values).
* Aus dem JavaScript-Client-SDK-Kontextobjekt von Microsoft Teams.[](/javascript/api/@microsoft/teams-js/app.context)

### <a name="get-context-by-inserting-url-placeholder-values"></a>Abrufen des Kontexts durch Einfügen von URL-Platzhalterwerten

Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs. Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird. Die verfügbaren Platzhalter umfassen alle Felder des [Kontextobjekts](/javascript/api/@microsoft/teams-js/app.context) . Zu den allgemeinen Platzhaltern gehören die folgenden Listen:

* [{page.id}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-id): Die vom Entwickler definierte eindeutige ID für die Seite, die beim ersten [Konfigurieren der Seite](~/tabs/how-to/create-tab-pages/configuration-page.md) definiert wurde. (Bekannt als `{entityId}` vor TeamsJS v.2.0.0).
* [{page.subPageId}](/javascript/api/@microsoft/teams-js/app.pageinfo#@microsoft-teams-js-app-pageinfo-subpageid): Die vom Entwickler definierte eindeutige ID für die Unterseite, auf die dieser Inhalt verweist, der beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element auf der Seite definiert wird. (Bekannt als `{subEntityId}` vor TeamsJS v.2.0.0).
* [{user.loginHint}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-loginhint): Ein Wert, der als Anmeldehinweis für Azure AD geeignet ist. Dies ist in der Regel der Anmeldename des aktuellen Benutzers in ihrem Private Tenant. (Bekannt als `{loginHint}` vor TeamsJS v.2.0.0).
* [{user.userPrincipalName}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-userprincipalname): Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten. (Bekannt als `{userPrincipalName}` vor TeamsJS v.2.0.0).
* [{user.id}](/javascript/api/@microsoft/teams-js/app.userinfo#@microsoft-teams-js-app-userinfo-id): Die Azure AD-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten. (Bekannt als `{userObjectId}` vor TeamsJS v.2.0.0).
* [{app.theme}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-theme): Das aktuelle Benutzeroberflächendesign wie `default`, `dark`oder `contrast`. (Bekannt als `{theme}` vor TeamsJS v.2.0.0).
* [{team.groupId}](/javascript/api/@microsoft/teams-js/app.teaminfo#@microsoft-teams-js-app-teaminfo-groupid): Die ID der Office 365 Gruppe, in der sich die Registerkarte befindet. (Bekannt als `{groupId}` vor TeamsJS v.2.0.0)
* [{user.tenant.id}](/javascript/api/@microsoft/teams-js/app.tenantinfo#@microsoft-teams-js-app-tenantinfo-id): Die Azure AD-Mandanten-ID des aktuellen Benutzers. (Bekannt als `{tid}` vor TeamsJS v.2.0.0).
* [{app.locale}](/javascript/api/@microsoft/teams-js/app.appinfo#@microsoft-teams-js-app-appinfo-locale): Das aktuelle Gebietsschema des Benutzers, das z`en-us`. B. als *languageId-countryId* formatiert ist. (Bekannt als `{locale}` vor TeamsJS v.2.0.0).

> [!NOTE]
> Der bisherige Platzhalter `{upn}` ist nun veraltet. Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{user.loginHint}`.

Wenn Sie z. B. in Ihrem App-Manifest das Attribut "*configurationUrl*`"https://www.contoso.com/config?name={user.loginHint}&tenant={user.tenant.id}&group={team.groupId}&theme={app.theme}"`" für die Registerkarte festlegen und der angemeldete Benutzer die folgenden Attribute aufweist:

* Der Benutzername ist **user@example.com**.
* Die Mandanten-ID ihres Unternehmens ist **e2653c-usw**.
* Sie sind Mitglied der Office 365 Gruppe mit der ID **00209384 usw**.
* Der Benutzer hat sein Teams-Design auf **dunkel** festgelegt.

. . . dann ruft Teams beim Konfigurieren der Registerkarte die folgende URL auf:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Abrufen des Kontexts mithilfe der JavaScript-Bibliothek von Microsoft Teams

Sie können die zuvor aufgeführten Informationen auch mithilfe des [JavaScript-Client-SDKs von Microsoft Teams](/javascript/api/overview/msteams-client) abrufen, indem Sie `microsoftTeams.getContext(function(context) { /* ... */ })` aufrufen.

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

| TeamsJS v2-Name | Name von TeamsJS v1 | Beschreibung |
|-----------------|-----------------|-------------|
| team.internalId | teamId | Die Microsoft Teams-ID für das Team, dem der Inhalt zugeordnet ist. |
| team.displayName | teamName | Der Name für das Team, dem der Inhalt zugeordnet ist. |
| channel.id | channelId | Die Microsoft Teams-ID für den Kanal, dem der Inhalt zugeordnet ist. |
| channel.displayName | Channelname | Der Name für den Kanal, dem der Inhalt zugeordnet ist. |
| chat.id | chatId | Die Microsoft Teams-ID für den Chat, mit dem der Inhalt verknüpft ist. |
| app.locale | Gebietsschema | Das aktuelle Gebietsschema, das der Benutzer für die App konfiguriert hat, die als "languageId-countryId" (z. B. "en-us") formatiert ist. |
| page.id | entityId | Die vom Entwickler definierte eindeutige ID für die Seite, auf die dieser Inhalt verweist. |
| page.subPageId | subEntityId | Die vom Entwickler definierte eindeutige ID für die Unterseite, auf die dieser Inhalt verweist. Dieses Feld sollte verwendet werden, um einen bestimmten Zustand innerhalb einer Seite wiederherzustellen, z. B. zum Scrollen oder Aktivieren eines bestimmten Inhaltselements. |
| user.loginHint | loginHint | Ein Wert, der für die Verwendung als login_hint bei der Authentifizierung mit Azure AD geeignet ist. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführen kann, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| user.userPrincipalName | Upn | Der UPN des aktuellen Benutzers. Hierbei kann es sich um einen extern authentifizierten UPN (z. B. Gastbenutzer) handelt. Da ein Böswilliger Ihre Inhalte in einem Browser ausführt, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| user.id | userObjectId | Die Azure AD-Objekt-ID des aktuellen Benutzers. Da ein Böswilliger Ihre Inhalte in einem Browser ausführt, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| user.tenant.id | Tid | Die Azure AD-Mandanten-ID des aktuellen Benutzers. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführen kann, sollte dieser Wert nur als Hinweis darauf verwendet werden, wer der Benutzer ist und niemals als Identitätsnachweis. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| team.groupId | groupId | Die Office 365 Gruppen-ID für das Team, dem der Inhalt zugeordnet ist. Dieses Feld ist nur verfügbar, wenn die Identitätsberechtigung im Manifest angefordert wird. |
| app.theme  | theme | Das aktuelle Benutzeroberflächendesign: Standard, dunkel, Kontrast |
| page.isFullScreen | isFullScreen | Gibt an, ob sich die Seite im Vollbildmodus befindet. |
| team.type | teamType | Der Typ des Teams. |
| sharepointSite.teamSiteUrl | teamSiteUrl | Die SharePoint-Stammwebsite, die dem Team zugeordnet ist. |
| sharepointSite.teamSiteDomain | teamSiteDomain | Die Domäne der SharePoint-Stammwebsite, die dem Team zugeordnet ist. |
| sharepointSite.teamSitePath | teamSitePath | Der relative Pfad zur SharePoint-Website, die dem Team zugeordnet ist. |
| channel.relativeUrl | channelRelativeUrl | Der relative Pfad zum SharePoint-Ordner, der dem Kanal zugeordnet ist. |
| app.host.sessionId | Sessionid | Eindeutige ID für die aktuelle Hostsitzung zur Verwendung beim Korrelieren von Telemetriedaten. |
| team.userRole | userTeamRole | Die Rolle des Benutzers im Team. Da eine böswillige Partei Ihre Inhalte in einem Browser ausführen kann, sollte dieser Wert nur als Hinweis auf die Rolle des Benutzers und nie als Beweis für ihre Rolle verwendet werden. |
| team.isArchived | isTeamArchived | Gibt an, ob das Team archiviert ist. Apps sollten dies als Signal verwenden, um Änderungen an Inhalten zu verhindern, die archivierten Teams zugeordnet sind. |
| app.host.clientType | hostClientType | Der Typ des Hostclients. Mögliche Werte sind: android, ios, web, desktop, rigel |
| page.frameContext | frameContext | Der Kontext, in den die Seiten-URL geladen wird (Inhalt, Aufgabe, Einstellung, Entfernen, SidePanel) |
| sharepoint | sharepoint | SharePoint-Kontext. Dies ist nur verfügbar, wenn es in SharePoint gehostet wird. |
| user.tenant.teamsSku | tenantSKU | Der Lizenztyp für den aktuellen Benutzermandanten. Mögliche Werte sind Enterprise, free, edu, unknown |
| user.licenseType | userLicenseType | Der Lizenztyp für den aktuellen Benutzer. Mögliche Werte sind E1-, E3- und E5-Enterprise-Pläne. |
| app.parentMessageId | parentMessageId | Die ID der übergeordneten Nachricht, von der aus dieses Aufgabenmodul gestartet wurde. Dies ist nur in Aufgabenmodulen verfügbar, die von Botkarten gestartet werden. |
| app.host.ringId | ringId | Aktuelle Ring-ID. |
| app.sessionId | appSessionId | Eindeutige ID für die aktuelle Hostsitzung zur Verwendung beim Korrelieren von Telemetriedaten. |
| user.isCallingAllowed | isCallingAllowed | Gibt an, ob der Aufruf für den aktuellen angemeldeten Benutzer zulässig ist. |
| user.isPSTNCallingAllowed | isPSTNCallingAllowed | Gibt an, ob PSTN-Anrufe für den aktuellen Benutzer zulässig sind. |
| meeting.id | meetingId | Die Besprechungs-ID, die von der Registerkarte verwendet wird, wenn sie im Besprechungskontext ausgeführt wird. |
| channel.defaultOneNoteSectionId | defaultOneNoteSectionId | Die OneNote-Abschnitts-ID, die mit dem Kanal verknüpft ist. |
| page.isMultiWindow | isMultiWindow | Die Angabe, ob sich die Registerkarte in einem Popupfenster befindet. |

Weitere Informationen finden Sie [unter Aktualisierungen zur *Kontextschnittstelle*](using-teams-client-sdk.md#updates-to-the-context-interface) und zur Kontextschnittstellen-API-Referenz.[](/javascript/api/@microsoft/teams-js/app.context)

## <a name="retrieve-context-in-private-channels"></a>Abrufen des Kontexts in privaten Kanälen

Wenn Ihre Inhaltsseite in einen privaten Kanal geladen wird, werden die Daten, die `getContext` Sie vom Anruf erhalten, verschleiert, um die Privatsphäre des Kanals zu schützen.

Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem privaten Kanal befindet:

* `team.groupId`: Nicht definiert für private Kanäle
* `team.internalId`: Auf die threadId des privaten Kanals festgelegt
* `team.displayName`: Auf den Namen des privaten Kanals festgelegt
* `sharepointSite.url`: Festlegen auf die URL einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal
* `sharepointSite.path`: Auf den Pfad einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal festgelegt
* `sharepointSite.domain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint-Websitedomäne für den privaten Kanal festgelegt

Wenn Ihre Seite einen dieser Werte verwendet, muss der Wert des Felds `channel.membershipType` sein `Private` , um zu bestimmen, ob ihre Seite in einem privaten Kanal geladen ist und entsprechend reagieren kann.

## <a name="retrieve-context-in-microsoft-teams-connect-shared-channels"></a>Abrufen des Kontexts in Microsoft Teams Connect freigegebenen Kanälen

> [!NOTE]
> Derzeit befinden sich Microsoft Teams Connect freigegebenen Kanäle nur in der [Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md).

Wenn Ihre Inhaltsseite in einen Microsoft Teams Connect freigegebenen Kanal geladen wird, werden die Daten, die `getContext` Sie vom Anruf erhalten, aufgrund der eindeutigen Liste der Benutzer in freigegebenen Kanälen geändert.

Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem freigegebenen Kanal befindet:

* `team.groupId`: Nicht definiert für freigegebene Kanäle.
* `team.internalId`: Auf das `threadId` Team festgelegt, wird der Kanal für den aktuellen Benutzer freigegeben. Wenn der Benutzer Zugriff auf mehrere Teams hat, wird dies auf das Team festgelegt, das den freigegebenen Kanal hostet (erstellt).
* `team.displayName`: Auf den Namen des Teams festgelegt, wird der Kanal für den aktuellen Benutzer freigegeben. Wenn der Benutzer Zugriff auf mehrere Teams hat, wird dies auf das Team festgelegt, das den freigegebenen Kanal hostet (erstellt).
* `sharepointSite.url`: Legen Sie die URL einer eindeutigen, eindeutigen SharePoint-Website für den freigegebenen Kanal fest.
* `sharepointSite.path`: Legen Sie den Pfad einer eindeutigen, eindeutigen SharePoint-Website für den freigegebenen Kanal fest.
* `sharepointSite.domain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint-Websitedomäne für den freigegebenen Kanal festgelegt.

Zusätzlich zu diesen Feldänderungen stehen zwei neue Felder für freigegebene Kanäle zur Verfügung:

* `hostTeamGroupId`: Legen Sie den Wert fest, der `team.groupId` dem Hostingteam oder dem Team zugeordnet ist, das den freigegebenen Kanal erstellt hat. Mit der Eigenschaft kann Microsoft Graph-API Aufrufe die Mitgliedschaft im freigegebenen Kanal abrufen.
* `hostTeamTenantId`: Legen Sie den Wert fest, der `channel.ownerTenantId` dem Hostingteam oder dem Team zugeordnet ist, das den freigegebenen Kanal erstellt hat. Auf die Eigenschaft kann mit der Mandanten-ID des aktuellen Benutzers im `user.tenant.id` Feld des *Kontextobjekts* verwiesen werden, um festzustellen, ob der Benutzer intern oder extern zum Mandanten des Hostingteams gehört.

Wenn Ihre Seite einen dieser Werte verwendet, muss der Wert des Felds `channel.membershipType` sein `Shared` , um zu bestimmen, ob Ihre Seite in einem freigegebenen Kanal geladen ist und entsprechend reagieren kann.

> [!NOTE]
> Jedes Mal, wenn ein Benutzer den Teams-Desktop- oder Webclient neu startet oder neu lädt, wird eine neue SessionID erstellt, die von der Teams-Sitzung nachverfolgt wird. Wenn ein Benutzer die Teams-Apps verlässt und in der Teams-Plattform neu lädt, wird eine neue App-SessionID erstellt, die von der App-Sitzung nachverfolgt wird.

## <a name="handle-theme-change"></a>Behandeln von Designänderungen

Sie können Ihre App registrieren, um informiert zu werden, wenn sich das Design ändert, indem Sie aufrufen `microsoftTeams.app.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

Das `theme` Argument in der Funktion ist eine Zeichenfolge mit dem Wert `default`, `dark`oder `contrast`.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Weitere Artikel

* [Richtlinien für den Registerkartenentwurf](../../tabs/design/tabs.md)
* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
