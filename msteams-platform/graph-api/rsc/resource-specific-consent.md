---
title: Ressourcenspezifische Einwilligung in Teams
description: Beschreibt die ressourcenspezifische Einwilligung in Teams und wie sie ausgenutzt werden kann.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: reference
keywords: Teams Autorisierung OAuth SSO AAD rsc Graph
ms.openlocfilehash: dabe0c33013fbb398eee7bf00ac2881cd86e6bc5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566130"
---
# <a name="resource-specific-consent-rsc"></a>Ressourcenspezifische Zustimmung (RSC)

Die ressourcenspezifische Zustimmung (Resource-Specific Consent, RSC) ist eine Microsoft Teams- und Microsoft-Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Teams innerhalb einer Organisation zu verwalten. Das rSC-Berechtigungsmodell (Resource-Specific Consent) ermöglicht es *Teambesitzern,* der Anwendung die Zustimmung zum Zugriff auf und/oder das Ändern der Daten eines Teams zu erteilen. Die granularen, Teams-spezifischen RSC-Berechtigungen definieren, was eine Anwendung innerhalb eines bestimmten Teams tun kann:

## <a name="resource-specific-permissions"></a>Ressourcenspezifische Berechtigungen

|Anwendungsberechtigung| Aktion |
| ----- | ----- |
|TeamSettings.Read.Group | Holen Sie sich die Einstellungen für dieses Team.|
|TeamSettings.ReadWrite.Group|Aktualisieren Sie die Einstellungen für dieses Team.|
|ChannelSettings.Read.Group|Holen Sie sich die Kanalnamen, Kanalbeschreibungen und Kanaleinstellungen für dieses Team ab.|
|ChannelSettings.ReadWrite.Group|Aktualisieren Sie die Kanalnamen, Kanalbeschreibungen und Kanaleinstellungen für dieses Team.|
|Channel.Create.Group|Erstellen von Kanälen in diesem Team.|
|Channel.Delete.Group|Löschen Sie Kanäle in diesem Team.|
|ChannelMessage.Read.Group |Holen Sie sich die Kanalnachrichten dieses Teams.|
|TeamsAppInstallation.Read.Group|Hier finden Sie eine Liste der installierten Apps dieses Teams.|
|TeamsTab.Read.Group|Hier finden Sie eine Liste der Registerkarten dieses Teams.|
|TeamsTab.Create.Group|Erstellen von Registerkarten in diesem Team.|
|TeamsTab.ReadWrite.Group|Aktualisieren Sie die Registerkarten dieses Teams.|
|TeamsTab.Delete.Group|Löschen der Registerkarten dieses Teams.|
|TeamMember.Read.Group|Holen Sie sich die Mitglieder dieses Teams.|

>[!NOTE]
>Ressourcenspezifische Berechtigungen sind nur für Teams Auf dem Teams-Client installierten Apps verfügbar und sind derzeit nicht Teil des Azure Active Directory-Portals.

## <a name="enable-resource-specific-consent-in-your-application"></a>Aktivieren der ressourcenspezifischen Zustimmung in Ihrer Anwendung

Die Schritte zum Aktivieren von RSC in Ihrer Anwendung sind wie folgt:

1. [Konfigurieren Sie die Zustimmungseinstellungen für Gruppenbesitzer im Azure Active Directory Portal](#configure-group-owner-consent-settings-in-the-azure-ad-portal).
1. [Registrieren Sie Ihre App mit Microsoft Identity Platform über das Azure AD-Portal](#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
1. [Überprüfen Sie Ihre Anwendungsberechtigungen im Azure AD-Portal](#review-your-application-permissions-in-the-azure-ad-portal).
1. [Abrufen eines Zugriffstokens von der Microsoft Identity-Plattform](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Aktualisieren Sie Ihr Teams App-Manifest](#update-your-teams-app-manifest).
1. [Installieren Sie Ihre App direkt in Teams](#sideload-your-app-in-teams).
1. [Überprüfen Sie Ihre App auf zusätzliche RSC-Berechtigungen](#check-your-app-for-added-rsc-permissions).

## <a name="configure-group-owner-consent-settings-in-the-azure-ad-portal"></a>Konfigurieren der Zustimmungseinstellungen für Gruppenbesitzer im Azure AD-Portal

Sie können die Zustimmung des [Gruppenbesitzers](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) direkt im Azure-Portal aktivieren oder deaktivieren:

> [!div class="checklist"]
>
>- Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator/Unternehmensadministrator](/azure/active-directory/users-groups-roles/directory-assign-admin-roles.md#global-administrator--company-administrator)an.  
 > - [Wählen Sie](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings) **Azure Active Directory**  =>  **Enterprise Anwendungen** Zustimmung und  =>  **Berechtigungen**  =>  **Benutzerzustimmungseinstellungen**.
> - Aktivieren, deaktivieren oder beschränken Sie die Zustimmung des Benutzers mit der Zustimmung des Benutzers **für Apps,** die auf Daten zugreifen (Standard ist die Zustimmung zum **Gruppenbesitzer für alle Gruppenbesitzer** zulassen). Damit ein Teambesitzer eine App mit RSC installieren kann, muss die Zustimmung des Gruppenbesitzers für diesen Benutzer aktiviert sein.

![azure-rsc-Konfiguration](../../assets/images/azure-rsc-configuration.png)

Um die Zustimmung des Gruppenbesitzers mithilfe von PowerShell zu aktivieren oder zu deaktivieren, führen Sie die unter [Zustimmung zum Gruppenbesitzer konfigurieren mit PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell)beschriebenen Schritte aus.

## <a name="register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal"></a>Registrieren Ihrer App mit Microsoft Identity Platform über das Azure AD-Portal

Das Azure Active Directory-Portal bietet Ihnen eine zentrale Plattform, um Ihre Apps zu registrieren und zu konfigurieren. Ihre App muss im Azure AD-Portal registriert sein, um sie in die Microsoft Identity Platform zu integrieren und Microsoft Graph APIs aufzurufen. Weitere Informationen finden Sie unter [Registrieren einer Anwendung bei der Microsoft Identity Platform](/graph/auth-register-app-v2).

>[!WARNING]
>Registrieren Sie nicht mehrere Teams-Apps in derselben Azure AD-App-ID. Die App-ID muss für jede App eindeutig sein. Versuche, mehrere Apps auf derselben App-ID zu installieren, schlagen fehl.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Überprüfen der Anwendungsberechtigungen im Azure AD-Portal

Navigieren Sie zur Seite **Home**  =>  **App-Registrierungen,** und wählen Sie Ihre RSC-App aus. Wählen Sie **API-Berechtigungen** in der linken Navigationsleiste aus, und überprüfen Sie die Liste der konfigurierten Berechtigungen für Ihre App. Wenn Ihre App nur RSC-Graph-API-Aufrufe ausführt, löschen Sie alle Berechtigungen auf dieser Seite. Wenn Ihre App auch Nicht-RSC-Aufrufe abgibt, behalten Sie diese Berechtigungen bei Bedarf bei.

>[!IMPORTANT]
>Das Azure AD-Portal kann nicht zum Anfordern von RSC-Berechtigungen verwendet werden. RSC-Berechtigungen sind derzeit exklusiv für Teams Anwendungen, die im Teams-Client installiert sind, und werden in der JsON-Datei (App Manifest) deklariert.

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Abrufen eines Zugriffstokens aus dem Microsoft Identity Platform

Um Graph-API-Aufrufe ausführen zu können, müssen Sie ein Zugriffstoken für Ihre App von der Identitätsplattform abrufen. Bevor Ihre App ein Token von der Microsoft Identity Platform abrufen kann, muss sie im Azure AD-Portal registriert sein. Das Zugriffstoken enthält Informationen zu Ihrer App und die Berechtigungen, über die es für die Ressourcen und APIs verfügt, die über Microsoft Graph bereitgestellt werden.

Sie benötigen die folgenden Werte aus dem Azure AD-Registrierungsprozess, um ein Zugriffstoken von der Identitätsplattform abzurufen:

- Die vom App-Registrierungsportal zugewiesene **Anwendungs-ID.** Wenn Ihre App Single Sign-On (SSO) unterstützt, sollten Sie dieselbe Anwendungs-ID für Ihre App und SSO verwenden.
- Der  **geheime Clientschlüssel/das Kennwort** oder ein öffentliches/privates Schlüsselpaar (**Zertifikat**). Dies ist für systemeigene Apps nicht erforderlich.
- Ein **Umleitungs-URI** (oder eine Antwort-URL) für Ihre App, um Antworten von Azure AD zu erhalten.

 *Weitere Informationen* finden Sie unter [Zugriff im Namen eines Benutzers](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) und Abrufen von [Zugriff ohne Benutzer](/graph/auth-v2-service)

## <a name="update-your-teams-app-manifest"></a>Aktualisieren Ihres Teams-App-Manifests

Die RSC-Berechtigungen werden in Ihrer App-Manifestdatei (JSON) deklariert.  Fügen Sie Ihrem App-Manifest einen [webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzu:

> [!div class="checklist"]
>
> - **id**  — Ihre Azure AD-App-ID. Weitere Informationen finden Sie unter [Registrieren Ihrer App im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **Ressource**  – jede Zeichenfolge. Dieses Feld hat keine Operation in RSC, sondern muss hinzugefügt werden und einen Wert haben, um eine Fehlerreaktion zu vermeiden. eine beliebige Zeichenfolge.
> - **Anwendungsberechtigungen** – RSC-Berechtigungen für Ihre App. Weitere Informationen finden Sie unter [Ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).

>
>[!IMPORTANT]
> Nicht-RSC-Berechtigungen werden im Azure-Portal gespeichert. Fügen Sie sie nicht zum App-Manifest hinzu.
>

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelMessage.Read.Group",
      "TeamSettings.Edit.Group",
      "ChannelSettings.ReadWrite.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.ReadWrite.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group"
    ]
  }
```

## <a name="sideload-your-app-in-teams"></a>Sideload Ihre App in Teams

Wenn Ihr Teams Administrator benutzerdefinierte App-Uploads zulässt, können Sie Ihre App direkt an ein bestimmtes Team [laden.](~/concepts/deploy-and-publish/apps-upload.md)

## <a name="check-your-app-for-added-rsc-permissions"></a>Überprüfen Sie Ihre App auf zusätzliche RSC-Berechtigungen

>[!IMPORTANT]
>Die RSC-Berechtigungen werden keinem Benutzer zugeordnet. Aufrufe werden mit App-Berechtigungen und nicht mit vom Benutzer delegierten Berechtigungen ausgeführt. Daher kann die App Aktionen ausführen, die der Benutzer nicht ausführen kann, z. B. das Erstellen eines Kanals oder das Löschen einer Registerkarte. Sie sollten die Absicht des Teambesitzers für Ihren Anwendungsfall überprüfen, bevor Sie RSC-API-Aufrufe tätigen. Weitere Informationen finden Sie [unter Microsoft Teams API-Übersicht](/graph/teams-concept-overview).

Nachdem die App in einem Team installiert wurde, können Sie [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) verwenden, um die Berechtigungen anzuzeigen, die der App in einem Team erteilt wurden:

> [!div class="checklist"]
>
>- Holen Sie die **groupId** des Teams vom Teams-Client ab.
> - Wählen Sie im Teams Client **Teams** aus der linksextremen Navigationsleiste aus.
> - Wählen Sie das Team aus, in dem die App installiert ist, aus dem Dropdown-Menü aus.
> - Wählen Sie das Symbol **Weitere Optionen** (&#8943;).
> - Wählen Sie **Link zum Team abrufen** aus.
> - Kopieren und speichern Sie den **groupId-Wert** aus der Zeichenfolge.
> - Melden Sie sich **bei Graph Explorer** an.
> - Machen Sie einen **GET-Aufruf** an den folgenden Endpunkt: `https://graph.microsoft.com/beta/groups/{teamGroupId}/permissionGrants` . Das ClientAppId-Feld in der Antwort wird der appId zugeordnet, die im Teams App-Manifest angegeben ist.
  ![Graph Explorer-Antwort auf den GET-Aufruf.](../../assets/images/graph-permissions.png)

## <a name="code-sample"></a>Codebeispiel
| **Beispielname** | **Beschreibung** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| Ressourcenspezifische Zustimmung (RSC) | Verwenden Sie RSC, um Graph APIs aufzurufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|



## <a name="see-also"></a>Siehe auch
 
* [Testen ressourcenspezifischer Zustimmungsberechtigungen in Teams](test-resource-specific-consent.md)
* [Ressourcenspezifische Zustimmung in Microsoft Teams für Administratoren](/MicrosoftTeams/resource-specific-consent)


