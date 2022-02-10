---
title: Kontext für Ihre Registerkarte erhalten
description: Beschreibt, wie Sie Benutzerkontext zu Ihren Registerkarten abrufen
ms.localizationpriority: medium
ms.topic: how-to
keywords: Teams Registerkarten Benutzerkontext
ms.openlocfilehash: ca77ba61a880bb12067f884e8c294700938cc6be
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518128"
---
# <a name="get-context-for-your-tab"></a>Kontext für Ihre Registerkarte erhalten

Ihre Registerkarte erfordert Kontextinformationen, um relevante Inhalte anzuzeigen:

* Grundlegende Informationen über den Benutzer, das Team oder das Unternehmen.
* Gebietsschema- und Designinformationen.
* Lesen Sie die Oder`subEntityId`, die `entityId` identifiziert, was sich auf dieser Registerkarte befindet.

## <a name="user-context"></a>Benutzerkontext

Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn:

* Sie erstellen ressourcen in Ihrer App oder ordnen sie dem angegebenen Benutzer oder Team zu.
* Sie initiieren einen Authentifizierungsfluss von Microsoft Azure Active Directory (Azure AD) oder einem anderen Identitätsanbieter, und Sie müssen den Benutzer nicht erneut eingeben. 

Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers in Ihrem Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Obwohl diese Benutzerinformationen zu einer reibungslosen Benutzererfahrung beitragen können, dürfen Sie sie nicht als Identitätsnachweis verwenden.  Beispielsweise kann ein Angreifer Ihre Seite in einem Browser laden und schädliche Informationen oder Anforderungen rendern.

## <a name="access-context-information"></a>Zugreifen auf Kontextinformationen

Sie können auf zwei Arten auf Kontextinformationen zugreifen:

* Fügen Sie URL-Platzhalterwerte ein.
* Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client).

### <a name="get-context-by-inserting-url-placeholder-values"></a>Abrufen von Kontext durch Einfügen von URL-Platzhalterwerten

Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs. Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird. Die verfügbaren Platzhalter enthalten alle Felder im [Kontextobjekt](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) . Häufige Platzhalter sind folgende:

* {entityId}: Die ID, die Sie für das Element auf dieser Registerkarte beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md) angegeben haben.
* {subEntityId}: Die ID, die Sie beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element auf dieser Registerkarte angegeben haben. Dies muss verwendet werden, um einen bestimmten Zustand innerhalb einer Entität wiederherzustellen. Beispiel: Scrollen zu oder Aktivieren eines bestimmten Inhaltselements.
* {loginHint}: Ein Wert, der als Anmeldehinweis für Microsoft Azure Active Directory (Azure AD) geeignet ist. Dies ist in der Regel der Anmeldename des aktuellen Benutzers in dessen Home-Mandant.
* {userPrincipalName}: Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten.
* {userObjectId}: Die Microsoft Azure Active Directory (Azure AD)-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.
* {theme}: Das aktuelle Benutzeroberflächendesign wie `default`, `dark`oder `contrast`.
* {groupId}: Die ID der Office 365 Gruppe, in der sich die Registerkarte befindet.
* {tid}: Die Microsoft Azure Active Directory (Azure AD)-Mandanten-ID des aktuellen Benutzers.
* {locale}: Das aktuelle Gebietsschema des Benutzers, das als languageId-countryId(en-us) formatiert ist.

> [!NOTE]
> Der bisherige Platzhalter `{upn}` ist nun veraltet. Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}`.

In Ihrem Registerkartenmanifest legen `configURL` Sie das Attribut beispielsweise auf `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`fest, dass der angemeldete Benutzer die folgenden Attribute hat:

* Der Benutzername ist **user@example.com**.
* Die Mandanten-ID des Unternehmens lautet **e2653c usw**.
* Sie sind Mitglied der Office 365-Gruppe mit id **00209384-usw**.
* Der Benutzer hat sein Teams Design auf **dunkel** festgelegt.

Wenn sie die Registerkarte konfigurieren, ruft Teams die folgende URL auf:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Abrufen von Kontext mithilfe der Microsoft Teams JavaScript-Bibliothek

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
    "loginHint": "A value suitable as a login hint for Microsoft Azure Active Directory (Azure AD). This is usually the login name of the current user, in their home tenant",
    "userPrincipalName": "The principal name of the current user, in the current tenant",
    "userObjectId": "The Microsoft Azure Active Directory (Azure AD) object id of the current user, in the current tenant",
    "tid": "The Microsoft Azure Active Directory (Azure AD) tenant ID of the current user",
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
    "defaultOneNoteSectionId": "The OneNote section ID that is linked to the channel",
    "isMultiWindow": "The indication whether the tab is in a pop out window"
}
```

## <a name="retrieve-context-in-private-channels"></a>Abrufen von Kontext in privaten Kanälen

> [!Note]
> Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.

Wenn Ihre Inhaltsseite in einem privaten Kanal geladen wird, werden die Daten, die `getContext` Sie vom Anruf erhalten, verborgen, um den Datenschutz des Kanals zu schützen. 

Die folgenden Felder werden geändert, wenn sich Die Inhaltsseite in einem privaten Kanal befindet:

* `groupId`: Nicht definiert für private Kanäle
* `teamId`: Auf die threadId des privaten Kanals festgelegt
* `teamName`: Auf den Namen des privaten Kanals festgelegt
* `teamSiteUrl`: Legen Sie die URL einer eindeutigen SharePoint-Website für den privaten Kanal fest.
* `teamSitePath`: Legen Sie den Pfad einer bestimmten, eindeutigen SharePoint-Website für den privaten Kanal fest.
* `teamSiteDomain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint-Websitedomäne für den privaten Kanal festgelegt

Wenn Ihre Seite einen dieser Werte verwendet, müssen Sie das `channelType` Feld überprüfen, um festzustellen, ob Die Seite in einem privaten Kanal geladen ist, und entsprechend reagieren.

> [!Note]
> `teamSiteUrl` funktioniert auch gut für Standardkanäle.

## <a name="handle-theme-change"></a>Behandeln von Designänderungen

Sie können Ihre App registrieren, um informiert zu werden, wenn sich das Design ändert, indem Sie aufrufen `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

Das `theme` Argument in der Funktion ist eine Zeichenfolge mit dem Wert `default`, `dark`oder `contrast`.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Weitere Artikel

* [Richtlinien für den Registerkartenentwurf](../../tabs/design/tabs.md)
* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md)