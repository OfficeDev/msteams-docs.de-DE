---
title: Ressourcenspezifische Zustimmung in Microsoft Teams
description: Beschreibt die ressourcenspezifische Zustimmung in Microsoft Teams und deren Vorteile.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Teams-Autorisierung OAuth SSO Aad RSC Graph
ms.openlocfilehash: 7d0927fc360d8c005326cdff6453796fb45bf113
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867139"
---
# <a name="resource-specific-consent-rsc--developer-preview"></a>Ressourcenspezifische Zustimmung (RSC) – Entwicklervorschau

>[!NOTE]
>Die Berechtigungen für die ressourcenspezifische Zustimmung sind nur in Desktop-und Android-Clients verfügbar, nachdem die Entwicklervorschau aktiviert wurde. Weitere Informationen finden Sie unter [How do I enable Developer Preview](../../resources/dev-preview/developer-preview-intro.md) .

Die ressourcenspezifische Zustimmung (RSC) ist eine Microsoft Teams-und Graph-API-Integration, die es Ihrer APP ermöglicht, API-Endpunkte zum Verwalten bestimmter Teams in einer Organisation zu verwenden. Mit dem Berechtigungsmodell für die ressourcenspezifische Zustimmung (RSC) können *Teambesitzer* einer Anwendung die Zustimmung erteilen, auf die Daten eines Teams zuzugreifen und/oder diese zu ändern. Die detaillierten, Teams-spezifischen RSC-Berechtigungen definieren, was eine Anwendung in einem bestimmten Team tun kann:

## <a name="resource-specific-permissions"></a>Ressourcenspezifische Berechtigungen

|Anwendungsberechtigung| Aktion |
| ----- | ----- |
|TeamSettings. Read. Group | Rufen Sie die Einstellungen für dieses Team ab.|
|TeamSettings. Edit. Group|Aktualisieren Sie die Einstellungen für dieses Team.|
|ChannelSettings. Read. Group|Rufen Sie die Kanalnamen, Kanal Beschreibungen und Kanaleinstellungen für dieses Team ab.|
|ChannelSettings. Edit. Group|Aktualisieren Sie die Kanalnamen, Kanal Beschreibungen und Kanaleinstellungen für dieses Team.|
|Channel. Create. Group|Erstellen Sie in diesem Team Kanäle.|
|Kanal. Delete. Group|Löschen Sie Kanäle in diesem Team.|
|ChannelMessage. Read. Group |Rufen Sie die Kanal Nachrichten dieses Teams ab.|
|TeamsApp. Read. Group|Rufen Sie eine Liste der installierten apps dieses Teams ab.|
|TeamsTab. Read. Group|Rufen Sie eine Liste der Registerkarten dieses Teams ab.|
|TeamsTab. Create. Group|Erstellen von Registerkarten in diesem Team.|
|TeamsTab. Edit. Group|Aktualisieren Sie die Registerkarten dieses Teams.|
|TeamsTab. Delete. Group|Löschen Sie die Registerkarten dieses Teams.|
|Member. Read. Group|Die Mitglieder dieses Teams abrufen.|
|Owner. Read. Group|Die Besitzer dieses Teams abrufen.|

>[!NOTE]
>Ressourcenspezifische Berechtigungen stehen nur für Teams-Apps zur Verfügung, die auf dem Microsoft Teams-Client installiert sind und derzeit nicht Teil des Azure Active Directory-Portals sind.

## <a name="enabling-resource-specific-consent-in-your-application"></a>Aktivieren der ressourcenspezifischen Zustimmung in Ihrer Anwendung

Die Schritte zum Aktivieren von RSC in Ihrer Anwendung lauten wie folgt:

1. [Konfigurieren Sie die Zustimmungs Einstellungen für den Gruppenbesitzer im Azure Active Directory-Portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).
1. [Registrieren Sie Ihre APP mit der Microsoft Identity Platform über das Azure AD Portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
1. [Überprüfen der Anwendungsberechtigungen im Azure AD Portal](#review-your-application-permissions-in-the-azure-ad-portal)
1. [Rufen Sie ein Zugriffstoken von der Microsoft Identity-Plattform ab](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Aktualisieren Sie Ihr Teams-App-Manifest](#update-your-teams-app-manifest).
1. [Installieren Sie Ihre APP direkt in Microsoft Teams](#install-your-app-directly-in-teams).
1. [Überprüfen Sie Ihre APP auf hinzugefügte RSC-Berechtigungen](#check-your-app-for-added-rsc-permissions).

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a>Konfigurieren von Zustimmungs Einstellungen für Gruppenbesitzer im Azure AD Portal

Sie können die Zustimmung des [Gruppen Besitzers](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-to-apps-accessing-group-data) direkt im Azure-Portal aktivieren oder deaktivieren:

> [!div class="checklist"]
>
>- Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator/Unternehmensadministrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)an.  
 > - Wählen Sie **Azure Active Directory**  => Benutzereinstellungen für**Enterprise**  => **User settings**-Anwendungen aus.
> - Aktivieren, deaktivieren oder begrenzen der Benutzer Zustimmung mit dem Steuerelement mit der Bezeichnung **Benutzer können apps, die auf Unternehmensdaten zugreifen, für die Gruppen, die Sie besitzen, einwilligen** (diese Funktion ist standardmäßig aktiviert).

![Azure RSC-Konfiguration](../../assets/images/azure-rsc-configuration.svg)

| Wert | Beschreibung|
|--- | --- |
|Ja | Aktivieren Sie die gruppenspezifische Zustimmung für alle Gruppenbesitzer.|
|Nein |Deaktivieren Sie die gruppenspezifische Zustimmung für alle Benutzer.| 
|Beschränkt | Aktivieren Sie die gruppenspezifische Zustimmung für Mitglieder einer ausgewählten Gruppe.|

Um die Zustimmung des Gruppen Besitzers innerhalb des Azure-Portals mithilfe von PowerShell zu aktivieren oder zu deaktivieren, führen Sie die unter [configure Group Owner Einwilligung using PowerShell](/azure/active-directory/manage-apps/configure-user-consent#configure-group-owner-consent-using-powershell)beschriebenen Schritte aus.

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a>Registrieren Ihrer APP mit der Microsoft Identity Platform über das Azure AD Portal

Das Azure Active Directory-Portal stellt eine zentrale Plattform zum Registrieren und Konfigurieren Ihrer Apps bereit. Ihre APP muss im Azure AD-Portal registriert sein, damit Sie in die Microsoft Identity Platform und die Call Graph-APIs integriert werden kann. *Weitere Informationen finden Sie unter* [Registrieren einer Anwendung mit der Microsoft Identity-Plattform](/graph/auth-register-app-v2).

>[!WARNING]
>Registrieren Sie mehrere Teams-apps nicht für dieselbe Azure AD App-ID. Die APP-ID muss für jede APP eindeutig sein. Versuche, mehrere apps in derselben APP-ID zu installieren, können nicht ausgeführt werden.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Überprüfen der Anwendungsberechtigungen im Azure AD Portal

Navigieren Sie zur Seite **Home**  =>  **App Registrations** , und wählen Sie Ihre RSC-App aus. Wählen Sie in der linken Navigationsleiste **API-Berechtigungen** aus, und überprüfen Sie die Liste der konfigurierten Berechtigungen für Ihre APP. Wenn Ihre APP nur RSC-Grafik Anrufe tätigen kann, löschen Sie alle Berechtigungen auf dieser Seite. Wenn Ihre APP auch nicht-RSC-Anrufe tätigen kann, behalten Sie diese Berechtigungen bei Bedarf.

>[!IMPORTANT]
>Das Azure AD Portal kann nicht verwendet werden, um RSC-Berechtigungen anzufordern. RSC-Berechtigungen sind derzeit ausschließlich für Microsoft Teams-Anwendungen, die im Microsoft Teams-Client installiert sind, und werden in der APP-Manifestdatei (JSON) deklariert.

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Abrufen eines Zugriffstokens von der Microsoft Identity-Plattform

Um Graph-API-Aufrufe zu erstellen, müssen Sie ein Zugriffstoken für Ihre APP über die Identitäts Plattform abrufen. Damit Ihre APP ein Token von der Microsoft Identity-Plattform erhalten kann, muss Sie im Azure AD Portal registriert sein. Das Zugriffstoken enthält Informationen zu Ihrer App und die Berechtigungen, über die es für die Ressourcen und APIs verfügt, die über Microsoft Graph bereitgestellt werden.

Sie benötigen die folgenden Werte aus dem Azure AD Registrierungsprozess, um ein Zugriffstoken von der Identitäts Plattform abzurufen:

- Die **Anwendungs-ID** , die vom APP-Registrierungs Portal zugewiesen wird. Wenn Ihre APP einmaliges Anmelden (Single Sign-on, SSO) unterstützt, sollten Sie die gleiche Anwendungs-ID für Ihre APP und SSO verwenden.
- Der **geheime Client Schlüssel/das Kennwort** oder ein öffentliches/privates Schlüsselpaar (**Certificate**). Dies ist für systemeigene Apps nicht erforderlich.
- Eine **Umleitungs-URI** (oder Antwort-URL) für Ihre APP, um Antworten von Azure AD zu erhalten.

 *Siehe* [Abrufen des Zugriffs im Namen eines Benutzers](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token) und [Abrufen des Zugriffs ohne Benutzer](/graph/auth-v2-service)

## <a name="update-your-teams-app-manifest"></a>Aktualisieren des Teams-App-Manifests

Die RSC-Berechtigungen werden in Ihrer APP-Manifestdatei (JSON-Datei) deklariert.  Fügen Sie dem App-Manifest einen [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo) -Schlüssel mit den folgenden Werten hinzu:

> [!div class="checklist"]
>
> - **ID** – ihre Azure AD App-ID. *Weitere Informationen finden Sie unter* [Registrieren Ihrer APP im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **Resource** – eine beliebige Zeichenfolge. Dieses Feld hat keine Operation im RSC, muss jedoch hinzugefügt werden und einen Wert haben, um eine Fehlerantwort zu vermeiden. eine Zeichenfolge wird verwendet.
> - **Anwendungsberechtigungen** – RSC-Berechtigungen für Ihre APP. *Siehe* [ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).

>
>[!IMPORTANT]
> Nicht-RSC-Berechtigungen werden im Azure-Portal gespeichert. Fügen Sie Sie nicht zum App-Manifest hinzu.
>

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelMessage.Read.Group",
      "TeamSettings.Edit.Group",
      "ChannelSettings.Edit.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.Edit.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group"
    ]
  }
```

## <a name="install-your-app-directly-in-teams"></a>Direkte Installation Ihrer APP in Microsoft Teams

Nachdem Sie Ihre APP erstellt haben, können Sie [Ihr App-Paket](../../concepts/deploy-and-publish/apps-upload.md#upload-your-package-into-a-team-using-the-apps-tab) direkt in ein bestimmtes Team hochladen.  Hierzu muss die Richtlinieneinstellung **benutzerdefinierte apps hochladen** als Teil der benutzerdefinierten Richtlinien für die APP-Einrichtung aktiviert werden. *Siehe* [benutzerdefinierte App-Richtlinieneinstellungen](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

## <a name="check-your-app-for-added-rsc-permissions"></a>Überprüfen Ihrer APP auf hinzugefügte RSC-Berechtigungen

>[!IMPORTANT]
>Die RSC-Berechtigungen werden keinem Benutzer zugeschrieben. Aufrufe werden mit App-Berechtigungen und nicht mit Benutzern Delegierten Berechtigungen durchgeführt. Daher kann die APP möglicherweise Aktionen durchführen, die der Benutzer nicht ausführen kann, beispielsweise das Erstellen eines Kanals oder das Löschen einer Registerkarte. Sie sollten die Absicht des Team Besitzers für Ihren Anwendungsfall vor dem Erstellen von RSC-API-aufrufen überprüfen. *Weitere Informationen finden Sie unter* [Übersicht über die Microsoft Teams-API](/graph/teams-concept-overview).

Nachdem die app in einem Team installiert wurde, können Sie den [Graph-Explorer](https://developer.microsoft.com/graph/graph-explorer) verwenden, um die Berechtigungen anzuzeigen, die der app in einem Team erteilt wurden:

> [!div class="checklist"]
>
>- Rufen Sie die **Gruppen** -Nr des Teams vom Microsoft Teams-Client ab.
> - Wählen Sie im Microsoft Teams-Client die Option **Teams** von der ganz linken Navigationsleiste aus.
> - Wählen Sie im Dropdownmenü das Team aus, in dem die APP installiert ist.
> - Klicken Sie auf das Symbol **Weitere Optionen** (&#8943;).
> - Wählen Sie **Get Link to Team**aus.
> - Kopieren Sie den Wert der **Gruppe** , und speichern Sie ihn aus der Zeichenfolge.
> - Melden Sie sich beim **Graph-Explorer**an.
> - Einen **Get** -Aufruf an den folgenden Endpunkt ausführen: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` . Das clientAppId-Feld in der Antwort wird der im Microsoft Teams-App-Manifest angegebenen Anwendungs-ID zugeordnet.

 ![Graph-Explorer-Antwort zum Abrufen eines Anrufs.](../../assets/images/graph-permissions.png)

 > [!div class="nextstepaction"]
> [Testen von Berechtigungen für die ressourcenspezifische Zustimmung in Microsoft Teams](test-resource-specific-consent.md)
