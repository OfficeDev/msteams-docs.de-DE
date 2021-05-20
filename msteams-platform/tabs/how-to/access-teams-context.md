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
# <a name="get-context-for-your-microsoft-teams-tab"></a>Abrufen von Kontext zu Ihrer Microsoft Teams-Registerkarte

Ihre Registerkarte muss Kontextinformationen benötigen, um relevante Inhalte anzuzeigen:

* Grundlegende Informationen zum Benutzer, Team oder Unternehmen.
* Lokal- und Themeninformationen.
* Lesen Sie die `entityId` `subEntityId` oder, die identifiziert, was auf dieser Registerkarte ist.

## <a name="user-context"></a>Benutzerkontext

Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders nützlich sein, wenn:

* Sie erstellen oder ordnen Ressourcen in Ihrer App dem angegebenen Benutzer oder Team zu.
* Sie initiieren einen Authentifizierungsfluss für Azure Active Directory oder einen anderen Identitätsanbieter, und Sie möchten nicht, dass der Benutzer seinen Benutzernamen erneut eingibt. Weitere Informationen zur Authentifizierung auf ihrer Registerkarte Microsoft Teams finden Sie unter [Authentifizieren eines Benutzers auf der Registerkarte Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Diese Benutzerinformationen können zwar zu einer reibungslosen Benutzererfahrung beitragen, Sie sollten sie aber *nicht* als Identitätsnachweis verwenden. Beispielsweise könnte ein Angreifer Ihre Seite in einem „Bad Browser“ laden und schädliche Informationen oder Anforderungen rendern.

## <a name="accessing-context"></a>Zugreifen auf den Kontext

Sie können auf zwei Arten auf Kontextinformationen zugreifen:

* Fügen Sie URL-Platzhalterwerte ein.
* Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client).

### <a name="getting-context-by-inserting-url-placeholder-values"></a>Abrufen von Kontext durch Einfügen von URL-Platzhalterwerten

Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs. Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird. Die verfügbaren Platzhalter umfassen alle Felder des [Context](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true)-Objekts. Häufige Platzhalter sind folgende:

* {entityId}: Die ID, die Sie für das Element auf dieser Registerkarte beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md) angegeben haben.
* {subEntityId}: Die ID, die Sie beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element _innerhalb_ dieser Registerkarte angegeben haben. Diese sollte verwendet werden, um einen bestimmten Zustand innerhalb einer Entität wiederherzustellen, z: B., um zu einem bestimmten Inhalt zu blättern oder diesen zu aktivieren.
* {loginHint}: Ein Wert, der sich als Anmeldehinweis für Azure AD eignet. Dies ist in der Regel der Anmeldename des aktuellen Benutzers in seinem Basismandanten.
* {userPrincipalName}: Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten.
* {userObjectId}: Die Azure AD-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.
* {theme}: Das aktuelle UI-Design, z. B. `default`, `dark` oder `contrast`.
* {groupId}: Die ID der Office 365-Gruppe, in der sich die Registerkarte befindet.
* {tid}: Die Azure AD-Mandanten-ID des aktuellen Benutzers.
* Gebietsschema: Das aktuelle Gebietsschema des Als languageId-countryId formatierten Benutzers. Zum Beispiel en-us.

>[!NOTE]
>Der bisherige Platzhalter `{upn}` ist nun veraltet. Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}`.

Angenommen, In Ihrem Registerkartenmanifest legen Sie das `configURL` Attribut auf , der `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"` angemeldete Benutzer hat die folgenden Attribute:

* Ihr Benutzername lautet "user@example.com".
* Ihre Firmenmieter-ID ist 'e2653c-etc'.
* Sie sind Mitglied der Office 365 Gruppe mit der Id '00209384-etc'.
* Der Benutzer hat sein Teams Thema auf "dunkel" gesetzt.

Wenn sie Ihre Registerkarte konfigurieren, ruft Teams die folgende URL auf:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a>Abrufen von Kontext durch Verwendung der JavaScript-Bibliothek von Microsoft Teams

Sie können die zuvor aufgeführten Informationen auch mithilfe des [JavaScript-Client-SDKs von Microsoft Teams](/javascript/api/overview/msteams-client) abrufen, indem Sie `microsoftTeams.getContext(function(context) { /* ... */ })` aufrufen.

Die Kontextvariable sieht wie im folgenden Beispiel aus:

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

## <a name="retrieving-context-in-private-channels"></a>Abrufen von Kontext in privaten Kanälen

> [!Note]
> Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.

Wenn Ihre Inhaltsseite in einem privaten Kanal geladen wird, werden die Daten, die Sie vom `getContext`-Aufruf erhalten, verschleiert, um den Datenschutz des Kanals zu gewährleisten. Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem privaten Kanal befindet. Wenn Ihre Seite einen der unten aufgeführten Werte verwendet, müssen Sie das Feld `channelType` überprüfen, um festzustellen, ob Ihre Seite in einem privaten Kanal geladen wird, und entsprechend reagieren.

* `groupId`: Nicht definiert für private Kanäle
* `teamId`: Auf threadId des privaten Kanals eingestellt
* `teamName`: Auf den Namen des privaten Kanals gesetzt
* `teamSiteUrl`: Wird auf die URL einer eindeutigen, eindeutigen SharePoint Website für den privaten Kanal festgelegt
* `teamSitePath`: Stellen Sie den Pfad einer eindeutigen, eindeutigen SharePoint Website für den privaten Kanal ein
* `teamSiteDomain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint Standortdomäne für den privaten Kanal festgelegt

> [!Note]
>  „teamSiteUrl“ funktioniert auch für Standardkanäle gut.

## <a name="theme-change-handling"></a>Verarbeitung von Designänderungen

Sie können Ihre App für eine Benachrichtigung, wenn sich das Design ändert, registrieren, indem Sie `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` aufrufen.

Das Argument `theme` in der Funktion ist eine Zeichenfolge mit einem Wert von `default`, `dark` oder `contrast`.
