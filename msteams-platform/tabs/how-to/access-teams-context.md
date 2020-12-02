---
title: Kontext für die Registerkarte abrufen
description: Beschreibt, wie Benutzerkontext auf Ihre Registerkarten abgerufen wird.
keywords: Teams-Registerkarten Benutzerkontext
ms.openlocfilehash: 5c52e6eea21f0c059f3cd650770e1076f903fb8e
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552437"
---
# <a name="get-context-for-your-microsoft-teams-tab"></a>Kontext für Ihre Microsoft Teams-Registerkarte abrufen

Für Ihre Registerkarte sind möglicherweise Kontextinformationen erforderlich, um relevante Inhalte anzuzeigen.

* Auf Ihrer Registerkarte sind möglicherweise grundlegende Informationen zum Benutzer, Team oder Unternehmen erforderlich.
* Auf Ihrer Registerkarte sind möglicherweise Gebietsschema-und Designinformationen erforderlich.
* Möglicherweise müssen Sie die Registerkarte Lesen `entityId` oder das `subEntityId` kennzeichnet, was auf dieser Registerkarte angezeigt wird.

## <a name="user-context"></a>Benutzerkontext

Der Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn

* Sie müssen Ressourcen in Ihrer APP mit dem angegebenen Benutzer oder Team erstellen oder zuordnen.
* Sie möchten einen Authentifizierungs Fluss für Azure Active Directory oder einen anderen Identitätsanbieter initiieren, und Sie möchten nicht, dass der Benutzer seinen Benutzernamen erneut eingeben muss. (Weitere Informationen zur Authentifizierung auf der Registerkarte Microsoft Teams finden Sie unter [Authentifizieren eines Benutzers auf Ihrer Microsoft Teams-Registerkarte](~/concepts/authentication/authentication.md).)

> [!IMPORTANT]
> Diese Benutzerinformationen können zwar eine reibungslose Benutzeroberfläche bieten, Sie sollten Sie jedoch *nicht* als Identitätsnachweis verwenden. Beispielsweise könnte ein Angreifer die Seite in einen "schlechten Browser" Laden und schädliche Informationen oder Anforderungen rendern.

## <a name="accessing-context"></a>Zugreifen auf Kontext

Sie können auf zwei Arten auf Kontextinformationen zugreifen:

* Einfügen von URL-Platzhalterwerten
* Verwenden des [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client)

### <a name="getting-context-by-inserting-url-placeholder-values"></a>Kontext wird abgerufen, indem URL-Platzhalterwerte eingefügt werden

Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs. Microsoft Teams ersetzt die Platzhalter durch die entsprechenden Werte, wenn die tatsächliche Konfigurations-oder Inhalts-URL ermittelt wird. Die verfügbaren Platzhalter enthalten alle Felder im [Kontext](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) Objekt. Zu den allgemeinen Platzhaltern zählen folgende:

* {Entitäts Kennung}: die ID, die Sie beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)für das Element auf dieser Registerkarte angegeben haben.
* {subentity-ID}: die ID, die Sie beim Generieren einer [tiefen Verknüpfung](~/concepts/build-and-test/deep-links.md) für ein _bestimmtes Element auf_ dieser Registerkarte angegeben haben. Dies sollte verwendet werden, um in einem bestimmten Zustand innerhalb einer Entität wiederherzustellen. beispielsweise scrollen zu einem bestimmten Inhaltselement oder Aktivieren dieses.
* {loginHint}: ein Wert, der als Anmelde Hinweis für Azure AD geeignet ist. Dies ist normalerweise der Anmeldename des aktuellen Benutzers in seinem Home-Mandanten.
* {userPrincipalName}: der Benutzerprinzipal Name des aktuellen Benutzers im aktuellen Mandanten.
* {userObjectId}: die Azure AD Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.
* {Theme}: das aktuelle Benutzeroberflächendesign wie `default` , `dark` , oder `contrast` .
* {Gruppenkennung}: die ID der Office 365 Gruppe, in der sich die Registerkarte befindet.
* {TID}: die Azure AD Mandanten-ID des aktuellen Benutzers.
* {locale}: das aktuelle Gebietsschema des Benutzers, der als sprach-Country-Format formatiert ist (beispielsweise "en-US").

>[!NOTE]
>Der vorherige `{upn}` Platzhalter ist jetzt veraltet. Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}` .

Angenommen, in Ihrem Tab-Manifest legen Sie das- `configURL` Attribut auf

`"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`

Und der angemeldete Benutzer verfügt über die folgenden Attribute:

* Ihr Benutzername ist "user@example.com"
* Die Mandanten-ID des Unternehmens lautet "e2653c-etc".
* Sie sind Mitglied der Office 365 Gruppe mit der ID "00209384-etc".
* Der Benutzer hat sein Microsoft Teams-Design auf "dunkel" festgelegt.

Bei der Konfiguration Ihrer Registerkarte ruft Microsoft Teams diese URL auf:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="getting-context-by-using-the-microsoft-teams-javascript-library"></a>Kontext wird mithilfe der JavaScript-Bibliothek von Microsoft Teams abgerufen.

Sie können die oben aufgeführten Informationen auch mithilfe des [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client) durch Aufrufen abrufen `microsoftTeams.getContext(function(context) { /* ... */ })` .

Die Kontextvariable wird wie im folgenden Beispiel aussehen.

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

## <a name="retrieving-context-in-private-channels"></a>Abrufen von Kontext in privaten Kanälen

> [!Note]
> Private Kanäle befinden sich derzeit in der privaten Entwicklervorschau.

Wenn Ihre Inhaltsseite in einen privaten Kanal geladen wird, werden die Daten, die Sie aus dem Aufruf erhalten, `getContext` verschleiert, um die Datenschutzfunktion des Kanals zu schützen. Die folgenden Felder werden geändert, wenn sich die Inhaltsseite in einem privaten Kanal befindet. Wenn Ihre Seite einen der unten aufgeführten Werte verwendet, müssen Sie das Feld überprüfen, `channelType` um festzustellen, ob Ihre Seite in einen privaten Kanal geladen wird, und entsprechend reagieren.

* `groupId` -Undefined für private Kanäle
* `teamId` -Auf die Thread-Nr des privaten Kanals festlegen
* `teamName` -Auf den Namen des privaten Kanals festlegen
* `teamSiteUrl` -Festlegen der URL einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal
* `teamSitePath` -Festlegen des Pfads einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal
* `teamSiteDomain` -Festlegung auf die Domäne einer eindeutigen, eindeutigen SharePoint-Website Domäne für den privaten Kanal

> [!Note]
>  teamSiteUrl funktioniert auch für Standardkanäle.

## <a name="theme-change-handling"></a>Behandlung von Designänderungen

Sie können Ihre APP so registrieren, dass Sie mitgeteilt wird, wenn sich das Design durch Aufrufen ändert `microsoftTeams.registerOnThemeChangeHandler(function(theme) { /* ... */ })` .

Das `theme` Argument in der-Funktion ist eine Zeichenfolge mit dem Wert `default` , `dark` oder `contrast` .
