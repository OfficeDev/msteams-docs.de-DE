---
title: Aktivieren Sie die ressourcenspezifische Zustimmung in Teams
description: Lernen Sie in diesem Modul die ressourcenspezifische Zustimmung in Microsoft Teams kennen und wie Sie sie nutzen können.
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: f311723aa6bdb9fc95207169b7ab55434d246509
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144355"
---
# <a name="resource-specific-consent"></a>Ressourcenspezifische Zustimmung

> [!NOTE]
> Die ressourcenspezifische Zustimmung für den Chatbereich ist nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die ressourcenspezifische Zustimmung (RSC) ist eine Microsoft Teams- und Microsoft Graph-API-Integration, die es Ihrer App ermöglicht, API-Endpunkte zu verwenden, um bestimmte Ressourcen, entweder Teams oder Chats, innerhalb einer Organisation zu verwalten. Das RSC-Berechtigungsmodell ermöglicht es *Teambesitzern* und *Chatbesitzern*, einer Anwendung zuzustimmen, auf die Daten eines Teams bzw. auf die Daten eines Chats zuzugreifen und diese zu ändern.

**Hinweis:** Wenn einem Chat ein Meeting oder ein Anruf zugeordnet ist, gelten die entsprechenden RSC-Berechtigungen auch für diese Ressourcen.

## <a name="resource-specific-permissions"></a>Ressourcenspezifische Berechtigungen

Die granularen, Teams-spezifischen RSC-Berechtigungen definieren, was eine Anwendung innerhalb einer bestimmten Ressource tun kann.

### <a name="resource-specific-permissions-for-a-team"></a>Ressourcenspezifische Berechtigungen für ein Team

|Anwendungsberechtigung| Aktion |
| ----- | ----- |
|TeamSettings.Read.Group | Rufen Sie die Einstellungen dieses Teams ab.|
|TeamSettings.ReadWrite.Group|Aktualisieren Sie die Einstellungen dieses Teams.|
|ChannelSettings.Read.Group|Rufen Sie die Kanalnamen, Kanalbeschreibungen und Kanaleinstellungen dieses Teams ab.|
|ChannelSettings.ReadWrite.Group|Aktualisiere die Kanalnamen, Kanalbeschreibungen und Kanaleinstellungen dieses Teams.|
|Channel.Create.Group|Erstellen von Kanälen in diesem Team. |
|Channel.Delete.Group|Kanäle in diesem Team löschen. |
|ChannelMessage.Read.Group |Rufen Sie die Kanalnachrichten dieses Teams ab. |
|TeamsAppInstallation.Read.Group|Rufen Sie eine Liste der installierten Apps dieses Teams ab.|
|TeamsTab.Read.Group|Rufen Sie eine Liste der Registerkarten dieses Teams ab.|
|TeamsTab.Create.Group|Erstellen von Registerkarten in diesem Team. |
|TeamsTab.ReadWrite.Group|Aktualisieren Sie die Registerkarten dieses Teams. |
|TeamsTab.Delete.Group|Löschen der Registerkarten dieses Teams. |
|TeamMember.Read.Group|Rufen Sie die Mitglieder dieses Teams ab. |
|TeamsActivity.Send.Group|Erstellen Sie neue Benachrichtigungen in den Aktivitätsfeeds der Benutzer in diesem Team. |

Weitere Einzelheiten finden Sie unter [teamressourcenspezifische Einwilligungsberechtigungen](/graph/permissions-reference#teams-resource-specific-consent-permissions).

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
| TeamsAppInstallation.Read.Chat | Finden Sie heraus, welche Apps in diesem Chat installiert sind.                   |
| OnlineMeeting.ReadBasic.Chat   | Lesen Sie grundlegende Eigenschaften wie Name, Zeitplan, Organisator, Beitrittslink und Start-/Endbenachrichtigungen eines mit diesem Chat verknüpften Meetings. |
| Calls.AccessMedia.Chat         | Zugreifen auf Mediendatenströme in Anrufen, die mit diesem Chat oder dieser Besprechung verbunden sind.                                    |
| Calls.JoinGroupCall.Chat         | Nehmen Sie an Anrufen teil, die mit diesem Chat oder dieser Besprechung verbunden sind.                                    |
| TeamsActivity.Send.Chat         | Erstellen Sie neue Benachrichtigungen in den Aktivitätsfeeds der Benutzer in diesem Chat. |

Weitere Einzelheiten finden Sie unter [Zustimmungsberechtigungen für Chat-Ressourcen](/graph/permissions-reference#chat-resource-specific-consent-permissions).

> [!NOTE]
> Ressourcenspezifische Berechtigungen sind nur für Teams-Apps verfügbar, die auf dem Teams-Client installiert sind, und sind derzeit nicht Teil des Azure Active Directory (AAD)-Portals.

## <a name="enable-rsc-in-your-application"></a>Aktivieren von RSC in Ihrer Anwendung

1. [Konfigurieren Sie die Zustimmungseinstellungen im Azure AD Portal](#configure-consent-settings-in-the-azure-ad-portal).
    1. [Konfigurieren Sie die Zustimmungseinstellungen des Gruppenbesitzers für RSC in einem Team](#configure-group-owner-consent-settings-for-rsc-in-a-team).
    1. [Konfigurieren Sie die Benutzereinwilligungseinstellungen für RSC in einem Chat](#configure-user-consent-settings-for-rsc-in-a-chat).
1. [Registrieren Sie Ihre App über das Azure AD-Portal bei Microsoft Identity Platform](#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).
1. [Überprüfen Sie Ihre Anwendungsberechtigungen im Azure AD Portal](#review-your-application-permissions-in-the-azure-ad-portal).
1. [Rufen Sie ein Zugriffstoken von der Identitätsplattform ab](#obtain-an-access-token-from-the-microsoft-identity-platform).
1. [Aktualisieren Sie Ihr Teams-App-Manifest](#update-your-teams-app-manifest).
1. [Installieren Sie Ihre App direkt in Teams](#sideload-your-app-in-teams).
1. [Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen](#check-your-app-for-added-rsc-permissions).
    1. [Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen in einem Team](#check-your-app-for-added-rsc-permissions-in-a-team).
    1. [Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen in einem Chat](#check-your-app-for-added-rsc-permissions-in-a-chat).

## <a name="configure-consent-settings-in-the-azure-ad-portal"></a>Konfigurieren von Zustimmungseinstellungen im Azure AD-Portal

### <a name="configure-group-owner-consent-settings-for-rsc-in-a-team"></a>Konfigurieren Sie die Zustimmungseinstellungen des Gruppenbesitzers für RSC in einem Team

Sie können die Zustimmung des [Gruppenbesitzers](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-portal) direkt im Microsoft Azure-Portal aktivieren oder deaktivieren:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator oder Unternehmensadministrator an](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).
1. Wählen Sie **Azure Active Directory** > **Enterprise-Anwendungen** > **Zustimmung und Berechtigungen** > [**Benutzereinwilligungseinstellungen aus**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings).
1. Aktivieren, deaktivieren oder beschränken Sie die Benutzereinwilligung mit dem Steuerelement mit der Bezeichnung **Gruppeneigentümereinwilligung für Apps, die auf Daten zugreifen**. Die Standardeinstellung ist **Zustimmung des Gruppeneigentümers für alle Gruppeneigentümer zulassen**. .Damit ein Teambesitzer eine App mit RSC installieren kann, muss die Zustimmung des Gruppenbesitzers für diesen Benutzer aktiviert werden.

    ![Azure RSC-Teamkonfiguration](../../assets/images/azure-rsc-team-configuration.png)

Darüber hinaus können Sie die Zustimmung des Gruppenbesitzers mithilfe von PowerShell aktivieren oder deaktivieren, indem Sie die Schritte unter [Konfigurieren der Zustimmung des Gruppenbesitzers mithilfe von PowerShell ausführen](/azure/active-directory/manage-apps/configure-user-consent-groups?tabs=azure-powershell).

### <a name="configure-user-consent-settings-for-rsc-in-a-chat"></a>Konfigurieren Sie die Benutzereinwilligungseinstellungen für RSC in einem Chat

Sie können die [Benutzereinwilligung](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal) direkt im Azure-Portal aktivieren oder deaktivieren:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) als [globaler Administrator oder Unternehmensadministrator an](/azure/active-directory/roles/permissions-reference#global-administrator&preserve-view=true).
1. Wählen Sie **Azure Active Directory** > **Enterprise-Anwendungen** > **Zustimmung und Berechtigungen** > [**Benutzereinwilligungseinstellungen aus**](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/UserSettings).
1. Aktivieren, deaktivieren oder beschränken Sie die Benutzereinwilligung mit dem Steuerelement mit der Bezeichnung **Benutzereinwilligung für Anwendungen**. Die Standardeinstellung ist **Benutzereinwilligung für Apps zulassen**. Damit ein Chat-Mitglied eine App mit RSC installieren kann, muss die Benutzerzustimmung für diesen Benutzer aktiviert werden.

    ![Azure RSC-Chatkonfiguration](../../assets/images/azure-rsc-chat-configuration.png)

Darüber hinaus können Sie die Benutzereinwilligung mithilfe von PowerShell aktivieren oder deaktivieren, indem Sie die unter Benutzereinwilligung mithilfe von PowerShell [konfigurieren beschriebenen Sc](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-powershell)hritte ausführen.

## <a name="register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal"></a>Registrieren Ihrer App bei Microsoft Identity Platform über das Azure AD-Portal

Das Azure AD-Portal bietet ihnen eine zentrale Plattform zum Registrieren und Konfigurieren Ihrer Apps. Ihre App muss im Azure AD Portal registriert sein, um sie in die Identitätsplattform integrieren und Microsoft Graph-APIs aufrufen zu können. Weitere Informationen finden Sie unter [Registrieren einer Anwendung bei der Identitätsplattform](/graph/auth-register-app-v2).

> [!WARNING]
> Eine Azure AD App-ID darf nicht für mehrere Teams Apps freigegeben werden. Es muss eine 1:1 Zuordnung zwischen einer Teams-App und einer Azure AD-App vorhanden sein. Versuche, mehrere Teams Apps zu installieren, die derselben Azure AD App-ID zugeordnet sind, führen zu Installations- oder Laufzeitfehlern.

## <a name="review-your-application-permissions-in-the-azure-ad-portal"></a>Überprüfen Der Anwendungsberechtigungen im Azure AD-Portal

1. Gehen Sie zur Registrierungsseite der **Home** > **App und wählen** Sie Ihre RSC-App aus.
1. Wählen Sie im linken Bereich **API-Berechtigungen** aus und gehen Sie die Liste der **konfigurierten Berechtigungen** für Ihre App durch. Wenn Ihre App nur RSC Graph-API-Aufrufe durchführt, löschen Sie alle Berechtigungen auf dieser Seite. Wenn Ihre App auch Nicht-RSC-Aufrufe tätigt, behalten Sie diese Berechtigungen nach Bedarf bei.

> [!IMPORTANT]
> Das Azure AD-Portal kann nicht zum Anfordern von RSC-Berechtigungen verwendet werden. RSC-Berechtigungen gelten derzeit ausschließlich für Teams-Anwendungen, die im Teams-Client installiert sind, und werden in der Teams-App-Manifestdatei (JSON) deklariert.

## <a name="obtain-an-access-token-from-the-microsoft-identity-platform"></a>Rufen Sie ein Zugriffstoken von der Microsoft Identity Platform ab

Um Graph-API-Aufrufe durchzuführen, müssen Sie ein Zugriffstoken für Ihre App von der Identitätsplattform erhalten. Bevor Ihre App ein Token von der Identitätsplattform erhalten kann, muss sie im Azure AD-Portal registriert werden. Das Zugriffstoken enthält Informationen zu Ihrer App und die Berechtigungen, über die es für die Ressourcen und APIs verfügt, die über Microsoft Graph bereitgestellt werden.

Sie benötigen die folgenden Werte aus dem Azure AD-Registrierungsprozess, um ein Zugriffstoken von der Identitätsplattform abzurufen:

* Die vom **App-Registrierungsportal** zugewiesene Anwendungs-ID. Wenn Ihre App einmaliges Anmelden (SSO) unterstützt, müssen Sie dieselbe Anwendungs-ID für Ihre App und SSO verwenden.
* Der geheime Schlüssel/das Kennwort des **Clients** oder ein öffentliches oder privates Schlüsselpaar, nämlich **Certificate**. Dies ist für systemeigene Apps nicht erforderlich.
* Ein **Umleitungs-URI** oder eine Antwort-URL für Ihre App, um Antworten von Azure AD zu erhalten.

Weitere Informationen finden Sie unter [Zugriff im Auftrag eines Benutzers erhalten](/graph/auth-v2-user?view=graph-rest-1.0#3-get-a-token&preserve-view=true) und [Zugriff ohne Benutzer erhalten](/graph/auth-v2-service).

## <a name="update-your-teams-app-manifest"></a>Aktualisieren Sie Ihr Teams-App-Manifest

Die RSC-Berechtigungen werden in der JSON-Datei Ihres App-Manifests deklariert.

> [!IMPORTANT]
> Nicht-RSC-Berechtigungen werden im Azure-Portal gespeichert. Fügen Sie sie nicht zum App-Manifest hinzu.

### <a name="manifest-changes-for-resource-specific-consent"></a>Manifeständerungen für die ressourcenspezifische Zustimmung

<br>

<details>

<summary><b>RSC-Berechtigungen für App-Manifestversion 1.12</b></summary>

Fügen Sie Ihrem App-Manifest einen [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo)Schlüssel mit den folgenden Werten hinzu:

|Name| Typ | Beschreibung|
|---|---|---|
|`id` |Zeichenfolge |Ihre Azure AD App-ID. Weitere Informationen finden Sie [unter App im Azure AD-Portal registrieren](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Zeichenfolge| Dieses Feld hat in RSC keine Operation, muss aber hinzugefügt werden und einen Wert haben, um eine Fehlerantwort zu vermeiden; jede Zeichenfolge wird tun.|

Geben Sie die von der App benötigten Berechtigungen an.

|Name| Typ | Beschreibung|
|---|---|---|
|`authorization`|Object|Liste der Berechtigungen, welche die App benötigt, um zu funktionieren. Weitere Informationen finden Sie unter [Platzhalter für Link-Autorisierung im Manifest]

Beispiel für RSC in einem Team

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp"
    },
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "TeamSettings.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamSettings.ReadWrite.Group",
                "type": "Application"
            },
            {
                "name": "ChannelSettings.Read.Group",
                "type": "Application"
            },
            {
                "name": "ChannelSettings.ReadWrite.Group",
                "type": "Application"
            },
            {
                "name": "Channel.Create.Group",
                "type": "Application"
            },
            {
                "name": "Channel.Delete.Group",
                "type": "Application"
            },
            {
                "name": "ChannelMessage.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsAppInstallation.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Create.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.ReadWrite.Group",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Delete.Group",
                "type": "Application"
            },
            {
                "name": "TeamMember.Read.Group",
                "type": "Application"
            },
            {
                "name": "TeamsActivity.Send.Group",
                "type": "Application"
            }
        ]    
    }
}
```

Beispiel für RSC in einem Chat

```json
"webApplicationInfo": {
    "id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource": "https://RscBasedStoreApp"
    },
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "ChatSettings.Read.Chat",
                "type": "Application"
            },
            {
                "name": "ChatSettings.ReadWrite.Chat",
                "type": "Application"
            },
            {
                "name": "ChatMessage.Read.Chat",
                "type": "Application"
            },
            {
                "name": "ChatMember.Read.Chat",
                "type": "Application"
            },
            {
                "name": "Chat.Manage.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Read.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Create.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.Delete.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsTab.ReadWrite.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsAppInstallation.Read.Chat",
                "type": "Application"
            },
            {
                "name": "OnlineMeeting.ReadBasic.Chat",
                "type": "Application"
            },
            {
                "name": "Calls.AccessMedia.Chat",
                "type": "Application"
            },
            {
                "name": "Calls.JoinGroupCalls.Chat",
                "type": "Application"
            },
            {
                "name": "TeamsActivity.Send.Chat",
                "type": "Application"
            }
        ]    
    }
}
```

> [!NOTE]
> Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter angegeben werden `authorization`.

<br>

</details>

<br>

<details>

<summary><b>RSC-Berechtigungen für App-Manifest Version 1.11 oder früher</b></summary>

Fügen Sie Ihrem App-Manifest einen [webApplicationInfo](../../resources/schema/manifest-schema.md#webapplicationinfo)Schlüssel mit den folgenden Werten hinzu:

|Name| Typ | Beschreibung|
|---|---|---|
|`id` |Zeichenfolge |Ihre Azure AD App-ID. Weitere Informationen finden Sie [unter App im Azure AD-Portal registrieren](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Zeichenfolge| Dieses Feld hat in RSC keine Operation, muss aber hinzugefügt werden und einen Wert haben, um eine Fehlerantwort zu vermeiden; jede Zeichenfolge wird tun.|
|`applicationPermissions`|Array aus Zeichenfolgen|Legen Sie die Berechtigungen für  Ihre app. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).|

Beispiel für RSC in einem Team

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

Beispiel für RSC in einem Chat

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
> Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter angegeben werden `applicationPermissions`.

<br>

</details>

## <a name="sideload-your-app-in-teams"></a>Querladen der App in Microsoft Teams

Wenn Ihr Teams-Administrator benutzerdefinierte App-Uploads zulässt, können Sie Ihre [App direkt in ein bestimmtes Team](~/concepts/deploy-and-publish/apps-upload.md) oder einen bestimmten Chat querladen.

## <a name="check-your-app-for-added-rsc-permissions"></a>Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen

> [!IMPORTANT]
> Die RSC-Berechtigungen werden keinem Benutzer zugewiesen. Anrufe werden mit App-Berechtigungen getätigt, nicht mit vom Benutzer delegierten Berechtigungen. Der App kann gestattet werden, Aktionen auszuführen, die der Benutzer nicht ausführen kann, z. B. das Löschen einer Registerkarte. Sie müssen die Absicht des Teambesitzers oder Chatbesitzers für Ihre Verwendung überprüfen, bevor Sie RSC-API-Aufrufe tätigen. Weitere Informationen finden Sie unter Übersicht über die [Microsoft Teams-API](/graph/teams-concept-overview).

Nachdem die App in einer Ressource installiert wurde, können Sie den [Graph-Explorer](https://developer.microsoft.com/graph/graph-explorer) verwenden, um die Berechtigungen anzuzeigen, die der App in der Ressource gewährt wurden.

### <a name="check-your-app-for-added-rsc-permissions-in-a-team"></a>Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen in einem Team

1. Rufen Sie die **Gruppen-ID des Teams** von Teams ab.
1. Wählen Sie in **Teams** im Bereich ganz links Teams aus.
1. Wählen Sie das Team aus, in dem die App installiert werden soll.
1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; für dieses Team.
1. Wählen Sie **Link zum Team** abrufen aus dem Team-Dropdown-Menü aus.
1. Kopieren und speichern Sie den **groupId** Wert aus dem **Popup-Dialogfeld Link zum Team** abrufen.
1. Melden Sie sich bei **Graph Explorer an**.
1. Führen Sie einen **GET** Aufruf an diesen Endpunkt durch: `https://graph.microsoft.com/beta/teams/{teamGroupId}/permissionGrants`. Das `clientAppId` Feld in der Antwort wird dem im Manifest der Teams-App `webApplicationInfo.id` angegebenen Feld zugeordnet.

    ![Graph-Explorer-Antwort auf GET-Aufruf für Team-RSC-Berechtigungen](../../assets/images/team-graph-permissions.png)

Weitere Informationen zum Abrufen von Details zu den in einem bestimmten Team installierten Apps [finden Sie unter Abrufen der Namen und anderer Details von Apps, die in einem bestimmten Team installiert sind](/graph/api/team-list-installedapps#example-2-get-the-names-and-other-details-of-installed-apps).

### <a name="check-your-app-for-added-rsc-permissions-in-a-chat"></a>Überprüfen Sie Ihre App auf hinzugefügte RSC-Berechtigungen in einem Chat

1. Rufen Sie die Chat-Thread-ID vom *Teams-Webclient* ab.
1. Wählen Sie im Teams-Webclient im linken Bereich **Chat** aus.
1. Wählen Sie aus dem Dropdown-Menü den Chat aus, in dem die App installiert ist.
1. Kopieren Sie die Web-URL und speichern Sie die Chat-Thread-ID aus der Zeichenfolge.

    ![Chatthread-ID von Web-URL](../../assets/images/chat-thread-id.png)

1. Melden Sie sich bei **Graph Explorer an**.
1. Führen Sie einen **GET-Aufruf** an den folgenden Endpunkt durch: `https://graph.microsoft.com/beta/chats/{chatId}/permissionGrants`. Das `clientAppId` Feld in der Antwort wird dem im Manifest der Teams-App `webApplicationInfo.id` angegebenen Feld zugeordnet.

    ![Antwort des Graph-Explorers auf den GET-Aufruf für Chat-RSC-Berechtigungen](../../assets/images/chat-graph-permissions.png)

Weitere Informationen zum Abrufen von Details zu Apps, die in einem bestimmten Chat installiert sind, [finden Sie unter Abrufen der Namen und anderer Details von Apps, die in einem bestimmten Chat installiert sind](/graph/api/chat-list-installedapps#example-2-get-the-names-and-other-details-of-apps-installed-in-the-specified-chat).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **.NET** |**Node.js** |
|-----------------|-----------------|----------------|----------------|
| Resource-Specific Zustimmung (RSC) | Verwenden Sie RSC, um Graph-APIs aufzurufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-rsc/nodeJs)|

## <a name="see-also"></a>Siehe auch

* [Testen ressourcenspezifischer Zustimmungsberechtigungen in Teams](test-resource-specific-consent.md)
* [Ressourcenspezifische Zustimmung in Microsoft Teams für Administratoren](/MicrosoftTeams/resource-specific-consent)
