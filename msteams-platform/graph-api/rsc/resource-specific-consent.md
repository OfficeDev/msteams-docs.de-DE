---
title: Aktivieren der ressourcenspezifischen Zustimmung in Teams
description: Beschreibt die ressourcenspezifische Zustimmung in Teams und wie sie genutzt werden kann.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: reference
keywords: Teams-Autorisierung OAuth SSO AAD rsc Graph
ms.openlocfilehash: abd56787c89fde44f7cc4c72f0f59e66b05af9aa
ms.sourcegitcommit: 37b1724bb0d2f1b087c356e0fd0ff80145671e22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2021
ms.locfileid: "60291632"
---
# <a name="resource-specific-consent"></a>Ressourcenspezifische Zustimmung

> [!NOTE]
> Die ressourcenspezifische Zustimmung für den Chatbereich ist nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Bei der ressourcenspezifischen Zustimmung (RSC) handelt es sich um eine Microsoft Teams- und Microsoft Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Ressourcen innerhalb einer Organisation zu verwalten, entweder Teams oder Chats. Das RSC-Berechtigungsmodell ermöglicht *Es Teambesitzern* und *Chatbesitzern,* einer Anwendung die Zustimmung zu erteilen, auf die Daten eines Teams und die Daten eines Chats zuzugreifen bzw. diese zu ändern. 

**Hinweis:** Wenn einem Chat eine Besprechung oder ein Anruf zugeordnet ist, gelten die entsprechenden RSC-Berechtigungen auch für diese Ressourcen.

## <a name="resource-specific-permissions"></a>Ressourcenspezifische Berechtigungen

Die granularen, Teams-spezifischen RSC-Berechtigungen definieren, was eine Anwendung innerhalb einer bestimmten Ressource tun kann.

### <a name="resource-specific-permissions-for-a-team"></a>Ressourcenspezifische Berechtigungen für ein Team

|Anwendungsberechtigung| Aktion |
| ----- | ----- |
|TeamSettings.Read.Group | Rufen Sie die Einstellungen dieses Teams ab.|
|TeamSettings.ReadWrite.Group|Aktualisieren Sie die Einstellungen dieses Teams.|
|ChannelSettings.Read.Group|Rufen Sie die Kanalnamen, Kanalbeschreibungen und Kanaleinstellungen dieses Teams ab.|
|ChannelSettings.ReadWrite.Group|Aktualisieren Sie die Kanalnamen, Kanalbeschreibungen und Kanaleinstellungen dieses Teams.|
|Channel.Create.Group|Erstellen von Kanälen in diesem Team. |
|Channel.Delete.Group|Löschen Sie Kanäle in diesem Team. |
|ChannelMessage.Read.Group |Rufen Sie die Kanalnachrichten dieses Teams ab. |
|TeamsAppInstallation.Read.Group|Rufen Sie eine Liste der installierten Apps dieses Teams ab.|
|TeamsTab.Read.Group|Rufen Sie eine Liste der Registerkarten dieses Teams ab.|
|TeamsTab.Create.Group|Erstellen von Registerkarten in diesem Team. |
|TeamsTab.ReadWrite.Group|Aktualisieren Sie die Registerkarten dieses Teams. |
|TeamsTab.Delete.Group|Löschen der Registerkarten dieses Teams. |
|TeamMember.Read.Group|Rufen Sie die Mitglieder dieses Teams ab. |
|TeamsActivity.Send.Group|Erstellen Sie neue Benachrichtigungen in den Aktivitätsfeeds der Benutzer in diesem Team. |

Weitere Informationen finden Sie unter [teamressourcenspezifische Zustimmungsberechtigungen.](/graph/permissions-reference#teams-resource-specific-consent-permissions)

### <a name="resource-specific-permissions-for-a-chat"></a>Ressourcenspezifische Berechtigungen für einen Chat

Die folgende Tabelle enthält ressourcenspezifische Berechtigungen für einen Chat:

|Anwendungsberechtigung| Aktion |
| ----- | ----- |
| ChatSettings.Read.Chat         | Rufen Sie die Einstellungen dieses Chats ab.                                    |
| ChatSettings.ReadWrite.Chat    | Aktualisieren Sie die Einstellungen dieses Chats.                          |
| ChatMessage.Read.Chat          | Rufen Sie die Nachrichten dieses Chats ab.                                    |
| ChatMember.Read.Chat           | Rufen Sie die Mitglieder dieses Chats ab.                                     |
| Chat.Manage.Chat               | Verwalten dieses Chats.                                             |
| TeamsTab.Read.Chat             | Rufen Sie die Registerkarten dieses Chats ab.                                        |
| TeamsTab.Create.Chat           | Erstellen von Registerkarten in diesem Chat.                                     |
| TeamsTab.Delete.Chat           | Löschen der Registerkarten dieses Chats.                                      |
| TeamsTab.ReadWrite.Chat        | Verwalten der Registerkarten dieses Chats.                                      |
| TeamsAppInstallation.Read.Chat | Rufen Sie ab, welche Apps in diesem Chat installiert sind.                   |
| OnlineMeeting.ReadBasic.Chat   | Lesen Sie grundlegende Eigenschaften wie Name, Zeitplan, Organisator, Verknüpfung und Start-/End-Benachrichtigungen einer Besprechung, die diesem Chat zugeordnet ist. |
| Calls.AccessMedia.Chat         | Zugreifen auf Mediendatenströme in Anrufen, die mit diesem Chat oder dieser Besprechung verbunden sind.                                    |
| Calls.JoinGroupCall.Chat         | Nehmen Sie an Anrufen teil, die mit diesem Chat oder dieser Besprechung verbunden sind.                                    |
| TeamsActivity.Send.Chat         | Erstellen Sie neue Benachrichtigungen in den Aktivitätsfeeds der Benutzer in diesem Chat. |

Weitere Informationen finden Sie unter ["Ressourcenspezifische Zustimmungsberechtigungen für Chats".](/graph/permissions-reference#chat-resource-specific-consent-permissions)

> [!NOTE]
> Ressourcenspezifische Berechtigungen sind nur für Teams Apps verfügbar, die auf dem Teams-Client installiert sind, und sind derzeit nicht Teil des Azure Active Directory-Portals (AAD).

## <a name="enable-rsc-in-your-application"></a>Aktivieren von RSC in Ihrer Anwendung

1. [Konfigurieren Sie die Zustimmungseinstellungen im AAD Portal.](#configure-consent-settings-in-the-aad-portal)
    1. Konfigurieren Sie die Einstellungen für die Zustimmung des [Gruppenbesitzers für RSC in einem Team.](#configure-group-owner-consent-settings-for-rsc-in-a-team)
    1. [Konfigurieren von Benutzer-Zustimmungseinstellungen für RSC in einem Chat.](#configure-user-consent-settings-for-rsc-in-a-chat)
1. [Registrieren Sie Ihre App mit Microsoft Identity Platform über das AAD-Portal.](#register-your-app-with-microsoft-identity-platform-using-the-aad-portal)
1. [Überprüfen Sie Ihre Anwendungsberechtigungen im AAD Portal.](#review-your-application-permissions-in-the-aad-portal)
1. [Rufen Sie ein Zugriffstoken von der Identitätsplattform ab.](#obtain-an-access-token-from-the-microsoft-identity-platform)
1. [Aktualisieren Sie das Teams-App-Manifest.](#update-your-teams-app-manifest)
1. [Installieren Sie Ihre App direkt in Teams.](#sideload-your-app-in-teams)
1. [Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen.](#check-your-app-for-added-rsc-permissions)
    1. [Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen in einem Team.](#check-your-app-for-added-rsc-permissions-in-a-team)
    1. [Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen in einem Chat.](#check-your-app-for-added-rsc-permissions-in-a-chat)

## <a name="configure-consent-settings-in-the-aad-portal"></a>Konfigurieren von Zustimmungseinstellungen im AAD-Portal

### <a name="configure-group-owner-consent-settings-for-rsc-in-a-team"></a>Konfigurieren der Einstellungen für die Zustimmung des Gruppenbesitzers für RSC in einem Team

Sie können die Zustimmung des [Gruppenbesitzers](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) direkt im Azure-Portal aktivieren oder deaktivieren:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator oder Unternehmensadministrator](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)an.
1. Wählen Sie **Azure Active Directory**  >  **Enterprise Anwendungen**  >  **Zustimmungs- und Berechtigungseinstellungen** für  >  [**Benutzergenehmigungen**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings)aus.
1. Aktivieren, deaktivieren oder beschränken Sie die Zustimmung des Benutzers mit der Zustimmung des Steuerelements **"Gruppenbesitzer" für Apps, die auf Daten zugreifen.** Der Standardwert ist **Die Zustimmung des Gruppenbesitzers für alle Gruppenbesitzer zulassen.** Damit ein Teambesitzer eine App mit RSC installieren kann, muss die Zustimmung des Gruppenbesitzers für diesen Benutzer aktiviert sein.

    ![Azure RSC-Teamkonfiguration](../../assets/images/azure-rsc-team-configuration.png)

Darüber hinaus können Sie die Zustimmung des Gruppenbesitzers mithilfe von PowerShell aktivieren oder deaktivieren. Führen Sie die unter Konfigurieren der [Gruppenbesitzerzustimmung mithilfe von PowerShell](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell)beschriebenen Schritte aus.

### <a name="configure-user-consent-settings-for-rsc-in-a-chat"></a>Konfigurieren von Benutzer-Zustimmungseinstellungen für RSC in einem Chat

Sie können die Zustimmung des [Benutzers](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) direkt im Azure-Portal aktivieren oder deaktivieren:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator oder Unternehmensadministrator](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true)an.
1. Wählen Sie **Azure Active Directory**  >  **Enterprise Anwendungen** Zustimmung und  >  **Berechtigungen**  >  [**Benutzer zustimmungseinstellungen**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings)aus.
1. Aktivieren, deaktivieren oder einschränken Sie die Zustimmung des Benutzers mit dem Steuerelement mit der Bezeichnung **"Benutzer-Zustimmung für Anwendungen".** Die Standardeinstellung ist **"Zustimmung des Benutzers für Apps zulassen".** Damit ein Chatmitglied eine App mit RSC installieren kann, muss die Benutzerzustimmung für diesen Benutzer aktiviert sein.

    ![Azure RSC-Chatkonfiguration](../../assets/images/azure-rsc-chat-configuration.png)

Darüber hinaus können Sie die Benutzerzustimmung mithilfe von PowerShell aktivieren oder deaktivieren. Führen Sie die schritte aus, die unter Konfigurieren der [Benutzerzustimmung mithilfe von PowerShell](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell)beschrieben sind.

## <a name="register-your-app-with-microsoft-identity-platform-using-the-aad-portal"></a>Registrieren Ihrer App bei Microsoft Identity Platform über das AAD Portal

Das AAD-Portal bietet Ihnen eine zentrale Plattform zum Registrieren und Konfigurieren Ihrer Apps. Ihre App muss im AAD Portal registriert sein, um sie in die Identitätsplattform zu integrieren und Microsoft Graph-APIs aufzurufen. Weitere Informationen finden Sie unter [Registrieren einer Anwendung bei der Identitätsplattform.](/graph/auth-register-app-v2)

> [!WARNING]
> Eine AAD App-ID darf nicht für mehrere Teams Apps freigegeben werden. Es muss eine 1:1-Zuordnung zwischen einer Teams-App und einer AAD-App vorhanden sein. Versuche, mehrere Teams Apps zu installieren, die derselben AAD App-ID zugeordnet sind, führen zu Installations- oder Laufzeitfehlern.

## <a name="review-your-application-permissions-in-the-aad-portal"></a>Überprüfen Der Anwendungsberechtigungen im AAD Portal

1. Wechseln Sie zur Registrierungsseite der **Start-App,**  >   und wählen Sie Ihre RSC-App aus.
1. Wählen Sie im linken Bereich **API-Berechtigungen** aus, und durchlaufen Sie die Liste der **konfigurierten Berechtigungen** für Ihre App. Wenn Ihre App nur RSC-Graph API-Aufrufe vornimmt, löschen Sie alle Berechtigungen auf dieser Seite. Wenn Ihre App auch Nicht-RSC-Aufrufe vornimmt, behalten Sie diese Berechtigungen bei Bedarf bei.

> [!IMPORTANT]
> Das AAD-Portal kann nicht zum Anfordern von RSC-Berechtigungen verwendet werden. RSC-Berechtigungen gelten derzeit ausschließlich für Teams Anwendungen, die im Teams-Client installiert sind, und werden in der JSON-Datei (Teams App Manifest) deklariert.

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Abrufen eines Zugriffstokens vom Microsoft Identity Platform

Um Graph API-Aufrufe auszuführen, müssen Sie ein Zugriffstoken für Ihre App von der Identitätsplattform abrufen. Bevor Ihre App ein Token von der Identitätsplattform abrufen kann, muss sie im AAD Portal registriert werden. Das Zugriffstoken enthält Informationen zu Ihrer App und die Berechtigungen, über die es für die Ressourcen und APIs verfügt, die über Microsoft Graph bereitgestellt werden.

Sie benötigen die folgenden Werte aus dem AAD Registrierungsprozess, um ein Zugriffstoken von der Identitätsplattform abzurufen:

- Die vom App-Registrierungsportal zugewiesene **Anwendungs-ID.** Wenn Ihre App einmaliges Anmelden (Single Sign-On, SSO) unterstützt, müssen Sie dieselbe Anwendungs-ID für Ihre App und SSO verwenden.
- Der **geheime Clientschlüssel/das Kennwort** oder ein öffentliches oder privates Schlüsselpaar, bei dem es sich um **ein Zertifikat** handelt. Dies ist für systemeigene Apps nicht erforderlich.
- Ein **Umleitungs-URI** oder eine Antwort-URL, damit Ihre App Antworten von AAD empfängt.

Weitere Informationen finden Sie unter ["Zugriff im Namen eines Benutzers erhalten](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) und Zugriff ohne Benutzer [erhalten".](/graph/auth-v2-service)

## <a name="update-your-teams-app-manifest"></a>Aktualisieren des Teams-App-Manifests

Die RSC-Berechtigungen werden in Ihrer JSON-Datei des App-Manifests deklariert. Fügen Sie ihrem [App-Manifest einen webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzu:

|Name| Typ | Beschreibung|
|---|---|---|
|`id` |Zeichenfolge |Ihre AAD-App-ID. Weitere Informationen finden Sie unter [Registrieren Ihrer App im AAD Portal.](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-aad-portal)|
|`resource`|Zeichenfolge| Dieses Feld hat keinen Vorgang in RSC, muss jedoch hinzugefügt werden und einen Wert aufweisen, um eine Fehlerantwort zu vermeiden. Jede Zeichenfolge wird ausgeführt.|
|`applicationPermissions`|Array aus Zeichenfolgen|RSC-Berechtigungen für Ihre App. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen.](resource-specific-consent.md#resource-specific-permissions)|

>
> [!IMPORTANT]
> Nicht-RSC-Berechtigungen werden im Azure-Portal gespeichert. Fügen Sie sie nicht dem App-Manifest hinzu.
>

### <a name="example-for-rsc-in-a-team"></a>Beispiel für RSC in einem Team

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
        "TeamSettings.Read.Group",
        "TeamSettings.ReadWrite.Group",
        "ChannelSettings.Read.Group",
        "ChannelSettings.ReadWrite.Group",
        "Channel.Create.Group",
        "Channel.Delete.Group",
        "ChannelMessage.Read.Group",
        "TeamsAppInstallation.Read.Group",
        "TeamsTab.Read.Group",
        "TeamsTab.Create.Group",
        "TeamsTab.ReadWrite.Group",
        "TeamsTab.Delete.Group",
        "TeamMember.Read.Group",
        "TeamsActivity.Send.Group"
    ]
  }
```

### <a name="example-for-rsc-in-a-chat"></a>Beispiel für RSC in einem Chat

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp",
    "applicationPermissions": [
        "ChatSettings.Read.Chat",
        "ChatSettings.ReadWrite.Chat",
        "ChatMessage.Read.Chat",
        "ChatMember.Read.Chat",
        "Chat.Manage.Chat",
        "TeamsTab.Read.Chat",
        "TeamsTab.Create.Chat",
        "TeamsTab.Delete.Chat",
        "TeamsTab.ReadWrite.Chat",
        "TeamsAppInstallation.Read.Chat",
        "OnlineMeeting.ReadBasic.Chat",
        "Calls.AccessMedia.Chat",
        "Calls.JoinGroupCalls.Chat",
        "TeamsActivity.Send.Chat"
    ]
  }
```

> [!NOTE]
> Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter angegeben `applicationPermissions` werden.

## <a name="sideload-your-app-in-teams"></a>Querladen Ihrer App in Teams

Wenn Ihr Teams-Administrator benutzerdefinierte App-Uploads zulässt, können Sie Ihre App direkt in ein bestimmtes Team oder einen bestimmten Chat [laden.](~/concepts/deploy-and-publish/apps-upload.md)

## <a name="check-your-app-for-added-rsc-permissions"></a>Überprüfen Ihrer App auf hinzugefügte RSC-Berechtigungen

> [!IMPORTANT]
> Die RSC-Berechtigungen werden keinem Benutzer zugeordnet. Aufrufe erfolgen mit App-Berechtigungen, nicht mit delegierten Berechtigungen des Benutzers. Die App kann Aktionen ausführen, die der Benutzer nicht ausführen kann, z. B. das Löschen einer Registerkarte. Sie müssen die Absicht des Teambesitzers oder Chatbesitzers für Ihre Verwendung überprüfen, bevor Sie RSC-API-Aufrufe tätigen. Weitere Informationen finden Sie unter [Microsoft Teams API-Übersicht.](/graph/teams-concept-overview)

Nachdem die App in einer Ressource installiert wurde, können Sie [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) verwenden, um die Berechtigungen anzuzeigen, die der App in der Ressource gewährt wurden.

### <a name="check-your-app-for-added-rsc-permissions-in-a-team"></a>Überprüfen Ihrer App auf hinzugefügte RSC-Berechtigungen in einem Team

1. Rufen Sie die **groupId** des Teams aus Teams ab.
1. Wählen Sie in Teams ganz links **Teams** aus.
1. Wählen Sie das Team aus, in dem die App installiert werden soll.
1. Wählen Sie die Ellipsen aus, &#x25CF;&#x25CF;&#x25CF; für dieses Team.
1. Wählen Sie im Teamdropdownmenü **den Link zum Team abrufen** aus.
1. Kopieren und speichern Sie den **groupId-Wert** aus dem Dialogfeld **"Link zum Team-Popup** abrufen".
1. Melden Sie sich bei **Graph Explorer** an.
1. Führen Sie einen **GET-Aufruf** an diesen Endpunkt aus: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants` . Das `clientAppId` Feld in der Antwort wird dem im Teams `webApplicationInfo.id` App-Manifest angegebenen zugeordnet.

    ![Graph Explorer-Antwort auf get call for team RSC permissions](../../assets/images/team-graph-permissions.png)

Weitere Informationen zum Abrufen von Details zu den in einem bestimmten Team installierten Apps finden Sie unter [Abrufen der Namen und anderer Details von Apps, die im angegebenen Team installiert sind.](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps)

### <a name="check-your-app-for-added-rsc-permissions-in-a-chat"></a>Überprüfen Ihrer App auf hinzugefügte RSC-Berechtigungen in einem Chat

1. Rufen Sie die Chatthread-ID vom *Teams-Webclient* ab.
1. Wählen Sie im Teams Webclient im bereich ganz links die Option **"Chat"** aus.
1. Wählen Sie im Dropdownmenü den Chat aus, in dem die App installiert ist.
1. Kopieren Sie die Web-URL, und speichern Sie die Chatthread-ID aus der Zeichenfolge.

    ![Chatthread-ID von Web-URL](../../assets/images/chat-thread-id.png)

1. Melden Sie sich bei **Graph Explorer** an.
1. Führen Sie einen **GET-Aufruf** an den folgenden Endpunkt aus: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants` . Das `clientAppId` Feld in der Antwort wird dem im Teams `webApplicationInfo.id` App-Manifest angegebenen zugeordnet.

    ![Graph Explorer-Antwort auf GET call for chat RSC permissions](../../assets/images/chat-graph-permissions.png)

Weitere Informationen zum Abrufen von Details zu in einem bestimmten Chat installierten Apps finden Sie unter [Abrufen der Namen und anderer Details von Apps, die im angegebenen Chat installiert sind.](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat)

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| Resource-Specific Zustimmung (RSC) | Verwenden Sie RSC, um Graph APIs aufzurufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|

## <a name="see-also"></a>Siehe auch
 
* [Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams](test-resource-specific-consent.md)
* [Ressourcenspezifische Zustimmung in Microsoft Teams für Administratoren](/MicrosoftTeams/resource-specific-consent)
