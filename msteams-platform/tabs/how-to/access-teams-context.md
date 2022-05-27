---
title: Kontext für Ihre Registerkarte erhalten
description: Beschreibt, wie Sie Benutzerkontext zu Ihren Registerkarten abrufen
ms.localizationpriority: medium
ms.topic: how-to
keywords: Teams Registerkarten Benutzerkontext
ms.openlocfilehash: 04a0e751a8a532895b183690e00bc058c94d3346
ms.sourcegitcommit: d9025e959dcdd011ed4feca820dae7c5d1251b27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65755944"
---
# <a name="get-context-for-your-tab"></a>Kontext für Ihre Registerkarte erhalten

Ihre Registerkarte erfordert Kontextinformationen, um relevante Inhalte anzuzeigen:

* Grundlegende Informationen über den Benutzer, das Team oder das Unternehmen.
* Gebietsschema- und Designinformationen.
* Lesen Sie das `entityId` oder `subEntityId` das identifiziert, was sich auf dieser Registerkarte befindet.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="user-context"></a>Benutzerkontext

Kontext über den Benutzer, das Team oder das Unternehmen kann besonders hilfreich sein, wenn:

* Sie erstellen oder ordnen Ressourcen in Ihrer App dem angegebenen Benutzer oder Team zu.
* Sie initiieren einen Authentifizierungsfluss von Microsoft Azure Active Directory (Azure AD) oder einem anderen Identitätsanbieter, und Sie erfordern nicht, dass der Benutzer den Benutzernamen erneut eingibt.

Weitere Informationen finden Sie [unter Authentifizieren eines Benutzers in Ihrem Microsoft Teams](~/concepts/authentication/authentication.md).

> [!IMPORTANT]
> Obwohl diese Benutzerinformationen zu einer reibungslosen Benutzererfahrung beitragen können, dürfen Sie sie nicht als Identitätsnachweis verwenden.  Beispielsweise kann ein Angreifer Ihre Seite in einen Browser laden und schädliche Informationen oder Anforderungen rendern.

## <a name="access-context-information"></a>Zugreifen auf Kontextinformationen

Sie können auf zwei Arten auf Kontextinformationen zugreifen:

* Fügen Sie URL-Platzhalterwerte ein.
* Verwenden Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client).

### <a name="get-context-by-inserting-url-placeholder-values"></a>Abrufen des Kontexts durch Einfügen von URL-Platzhalterwerten

Verwenden Sie Platzhalter in Ihren Konfigurations-oder Inhalts-URLs. Microsoft Teams ersetzt die Platzhalter durch die relevanten Werte, wenn die tatsächliche Konfigurations- oder Inhalts-URL ermittelt wird. Die verfügbaren Platzhalter umfassen alle Felder des [Kontextobjekts](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-1.12.1&preserve-view=true) . Häufige Platzhalter sind folgende:

* {entityId}: Die ID, die Sie für das Element auf dieser Registerkarte beim ersten [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md) angegeben haben.
* {subEntityId}: Die ID, die Sie beim Generieren eines [Deep-Links](~/concepts/build-and-test/deep-links.md) für ein bestimmtes Element auf dieser Registerkarte angegeben haben. Dies muss verwendet werden, um einen bestimmten Zustand innerhalb einer Entität wiederherzustellen. Beispiel: Scrollen zu oder Aktivieren eines bestimmten Inhaltsabschnitts.
* {loginHint}: Ein Wert, der als Anmeldehinweis für Azure AD geeignet ist. Dies ist in der Regel der Anmeldename des aktuellen Benutzers in ihrem Private Tenant.
* {userPrincipalName}: Der Benutzerprinzipalname des aktuellen Benutzers im aktuellen Mandanten.
* {userObjectId}: Die Azure AD-Objekt-ID des aktuellen Benutzers im aktuellen Mandanten.
* {theme}: Das aktuelle Benutzeroberflächendesign wie `default`, `dark`oder `contrast`.
* {groupId}: Die ID der Office 365 Gruppe, in der sich die Registerkarte befindet.
* {tid}: Die Azure AD-Mandanten-ID des aktuellen Benutzers.
* {locale}: Das aktuelle Gebietsschema des Benutzers, das als languageId-countryId(en-us) formatiert ist.

> [!NOTE]
> Der bisherige Platzhalter `{upn}` ist nun veraltet. Aus Gründen der Abwärtskompatibilität ist es derzeit ein Synonym für `{loginHint}`.

Beispielsweise legen Sie in Ihrem Registerkartenmanifest das `configURL` Attribut auf `"https://www.contoso.com/config?name={loginHint}&tenant={tid}&group={groupId}&theme={theme}"`den angemeldeten Benutzer fest, der die folgenden Attribute aufweist:

* Der Benutzername ist **user@example.com**.
* Die Mandanten-ID ihres Unternehmens ist **e2653c-usw**.
* Sie sind Mitglied der gruppe Office 365 mit der ID **00209384-usw**.
* Der Benutzer hat sein Teams Design auf **dunkel** festgelegt.

Wenn sie die Registerkarte konfigurieren, ruft Teams die folgende URL auf:

`https://www.contoso.com/config?name=user@example.com&tenant=e2653c-etc&group=00209384-etc&theme=dark`

### <a name="get-context-by-using-the-microsoft-teams-javascript-library"></a>Abrufen des Kontexts mithilfe der Microsoft Teams JavaScript-Bibliothek

Sie können die oben aufgeführten Informationen auch mithilfe des [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) abrufen, indem Sie die `app.getContext()` Funktion aufrufen. Weitere Informationen finden Sie in den Eigenschaften der [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/app.context?view=msteams-client-js-latest&preserve-view=true).

## <a name="retrieve-context-in-private-channels"></a>Abrufen des Kontexts in privaten Kanälen

Wenn Ihre Inhaltsseite in einen privaten Kanal geladen wird, werden die Daten, die `getContext` Sie vom Anruf erhalten, verschleiert, um die Privatsphäre des Kanals zu schützen.

Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem privaten Kanal befindet:

* `groupId`: Nicht definiert für private Kanäle
* `teamId`: Auf die threadId des privaten Kanals festgelegt
* `teamName`: Auf den Namen des privaten Kanals festgelegt
* `teamSiteUrl`: Festlegen auf die URL einer eindeutigen, eindeutigen SharePoint-Website für den privaten Kanal
* `teamSitePath`: Auf den Pfad einer eindeutigen, eindeutigen SharePoint Website für den privaten Kanal festgelegt
* `teamSiteDomain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint Websitedomäne für den privaten Kanal festgelegt

Wenn Ihre Seite einen dieser Werte verwendet, muss der Wert des Felds `channelType` sein `Private` , um zu bestimmen, ob ihre Seite in einem privaten Kanal geladen ist und entsprechend reagieren kann.

## <a name="retrieve-context-in-microsoft-teams-connect-shared-channels"></a>Abrufen des Kontexts in Microsoft Teams Connect freigegebenen Kanälen

> [!NOTE]
> Derzeit befinden sich Microsoft Teams Connect freigegebenen Kanäle nur in der [Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md).

Wenn Ihre Inhaltsseite in einen Microsoft Teams Connect freigegebenen Kanal geladen wird, werden die Daten, die `getContext` Sie vom Anruf erhalten, aufgrund der eindeutigen Liste der Benutzer in freigegebenen Kanälen geändert.

Die folgenden Felder werden geändert, wenn sich Ihre Inhaltsseite in einem freigegebenen Kanal befindet:

* `groupId`: Nicht definiert für freigegebene Kanäle.
* `teamId`: Auf das `threadId` Team festgelegt, wird der Kanal für den aktuellen Benutzer freigegeben. Wenn der Benutzer Zugriff auf mehrere Teams hat, wird er auf das `teamId` Team festgelegt, das den freigegebenen Kanal hostet (erstellt).
* `teamName`: Auf den Namen des Teams festgelegt, wird der Kanal für den aktuellen Benutzer freigegeben. Wenn der Benutzer Zugriff auf mehrere Teams hat, wird er auf das `teamName` Team festgelegt, das den freigegebenen Kanal hostet (erstellt).
* `teamSiteUrl`: Legen Sie die URL einer eindeutigen, eindeutigen SharePoint Website für den freigegebenen Kanal fest.
* `teamSitePath`: Legen Sie den Pfad einer eindeutigen, eindeutigen SharePoint Website für den freigegebenen Kanal fest.
* `teamSiteDomain`: Auf die Domäne einer eindeutigen, eindeutigen SharePoint Websitedomäne für den freigegebenen Kanal festgelegt.

Zusätzlich zu diesen Feldänderungen stehen zwei neue Felder für freigegebene Kanäle zur Verfügung:

* `hostTeamGroupId`: Legen Sie den Wert fest, der `groupId` dem Hostingteam oder dem Team zugeordnet ist, das den freigegebenen Kanal erstellt hat. Mit der Eigenschaft kann Microsoft Graph-API Aufrufe die Mitgliedschaft im freigegebenen Kanal abrufen.
* `hostTeamTenantId`: Legen Sie den Wert fest, der `tenantId` dem Hostingteam oder dem Team zugeordnet ist, das den freigegebenen Kanal erstellt hat. Auf die Eigenschaft kann mit der Mandanten-ID des aktuellen Benutzers im `tid` Feld `getContext` verwiesen werden, um zu ermitteln, ob der Benutzer intern oder extern zum Mandanten des Hostingteams gehört.

Wenn Ihre Seite einen dieser Werte verwendet, muss der Wert des Felds `channelType` sein `Shared` , um zu bestimmen, ob Ihre Seite in einem freigegebenen Kanal geladen ist und entsprechend reagieren kann.

> [!NOTE]
> Jedes Mal, wenn ein Benutzer den Teams Desktop- oder Webclient neu startet oder neu lädt, wird eine neue SessionID erstellt, die von Teams Sitzung nachverfolgt wird. Wenn ein Benutzer die Teams-Apps beendet und in Teams Plattform neu lädt, wird eine neue App-SessionID erstellt, die von der App-Sitzung nachverfolgt wird.

## <a name="handle-theme-change"></a>Behandeln von Designänderungen

Sie können Ihre App registrieren, um informiert zu werden, wenn sich das Design ändert, indem Sie aufrufen `app.registerOnThemeChangeHandler(function(theme) { /* ... */ })`.

Das `theme` Argument in der Funktion ist eine Zeichenfolge mit dem Wert `default`, `dark`oder `contrast`.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Richtlinien für den Registerkartenentwurf](../../tabs/design/tabs.md)
* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Verwenden von Aufgabenmodulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md)
