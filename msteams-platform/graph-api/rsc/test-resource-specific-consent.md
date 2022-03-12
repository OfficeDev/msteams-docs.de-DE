---
title: Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams
description: Details zum Testen der ressourcenspezifischen Zustimmung in Teams Verwendung von Postman mit Codebeispielen
ms.localizationpriority: medium
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: Teams-Autorisierung OAuth SSO Microsoft Azure Active Directory (Azure AD) rsc Postman Graph
ms.openlocfilehash: ad99a06873ba3e5cff0ca6a957270a35ef668b8c
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453859"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams

> [!NOTE]
> Die ressourcenspezifische Zustimmung für den Chatbereich ist nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die ressourcenspezifische Zustimmung (RESOURCE-Specific Consent, RSC) ist eine Microsoft Teams- und Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Ressourcen innerhalb einer Organisation zu verwalten – entweder Teams oder Chats. Weitere Informationen finden Sie unter [Resource-specific consent (RSC) – Microsoft Teams Graph API](resource-specific-consent.md).

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie vor dem Testen die folgenden App-Manifeständerungen für die ressourcenspezifische Zustimmung überprüfen:

<br>

<details>

<summary><b>RSC-Berechtigungen für App-Manifestversion 1.12</b></summary>

Fügen Sie ihrem [App-Manifest einen webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzu:

|Name| Typ | Beschreibung|
|---|---|---|
|`id` |Zeichenfolge |Ihre Azure AD App-ID. Weitere Informationen finden Sie unter [Registrieren Ihrer App im Azure AD Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Zeichenfolge| Dieses Feld hat keinen Vorgang in RSC, muss jedoch hinzugefügt werden und einen Wert aufweisen, um eine Fehlerantwort zu vermeiden. Jede Zeichenfolge wird ausgeführt.|

Geben Sie die von der App benötigten Berechtigungen an.

|Name| Typ | Beschreibung|
|---|---|---|
|`authorization`|Object|Liste der Berechtigungen, welche die App benötigt, um zu funktionieren. Weitere Informationen finden Sie unter [Autorisierung](../../resources/schema/manifest-schema.md#authorization).|

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
> Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter `authorization`angegeben werden.

</details>

<br>

<details>

<summary><b>RSC-Berechtigungen für App-Manifestversion 1.11 oder frühere Versionen</b></summary>

Fügen Sie ihrem [App-Manifest einen webApplicationInfo-Schlüssel](../../resources/schema/manifest-schema.md#webapplicationinfo) mit den folgenden Werten hinzu:

|Name| Typ | Beschreibung|
|---|---|---|
|`id` |Zeichenfolge |Ihre Azure AD App-ID. Weitere Informationen finden Sie unter [Registrieren Ihrer App im Azure AD Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-azure-ad-portal).|
|`resource`|Zeichenfolge| Dieses Feld hat keinen Vorgang in RSC, muss jedoch hinzugefügt werden und einen Wert aufweisen, um eine Fehlerantwort zu vermeiden. Jede Zeichenfolge wird ausgeführt.|
|`applicationPermissions`|Array aus Zeichenfolgen|RSC-Berechtigungen für Ihre App. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).|

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

<br>

> [!NOTE]
> Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter `applicationPermissions`angegeben werden.

</details>

> [!IMPORTANT]
> Fügen Sie in Ihrem App-Manifest nur die RSC-Berechtigungen ein, über die Ihre App verfügen soll.

> [!NOTE]
> Wenn die App auf Anruf-/Medien-APIs zugreifen soll, sollte dies `webApplicationInfo.Id` die Azure AD App-ID eines [Azure Bot Service](/graph/cloud-communications-get-started#register-a-bot) sein.

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a>Testen hinzugefügter RSC-Berechtigungen zu einem Team mithilfe der Postman-App

Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC JSON-Testcode für das Team](test-team-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:

* `azureADAppId`: Die Azure AD App-ID Ihrer App.
* `azureADAppSecret`: Ihr Azure AD App-Kennwort.
* `token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen. legen Sie den Wert auf https://graph.microsoft.com/.default.
* `teamGroupId`: Sie können die Teamgruppen-ID wie folgt vom Teams-Client abrufen:

    1. Wählen Sie im Teams Client in der Navigationsleiste ganz links **Teams** aus.
    2. Wählen Sie im Dropdownmenü das Team aus, in dem die App installiert ist.
    3. Klicken Sie auf das Symbol **"Weitere Optionen** " (&#8943;).
    4. Wählen Sie **"Link zum Team abrufen" aus**.
    5. Kopieren und speichern Sie den **groupId-Wert** aus der Zeichenfolge.

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a>Testen hinzugefügter RSC-Berechtigungen zu einem Chat mithilfe der Postman-App

Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC JSON-Testcode für Chats](test-chat-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:

* `azureADAppId`: Die Azure AD App-ID Ihrer App.
* `azureADAppSecret`: Ihr Azure AD App-Kennwort.
* `token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen. legen Sie den Wert auf https://graph.microsoft.com/.default.
* `tenantId`: Der Name oder die Azure AD Objekt-ID Ihres Mandanten.
* `chatId`: Sie können die Chatthread-ID wie folgt vom *Teams-Webclient* abrufen:

    1. Wählen Sie im Teams Webclient in der linken Navigationsleiste ganz links "**Chat**" aus.
    2. Wählen Sie im Dropdownmenü den Chat aus, in dem die App installiert ist.
    3. Kopieren Sie die Web-URL, und speichern Sie die Chatthread-ID aus der Zeichenfolge.
![Chatthread-ID von Web-URL.](../../assets/images/chat-thread-id.png)

### <a name="use-postman"></a>Verwenden von Postman

1. Öffnen Sie die [Postman-App](https://www.postman.com) .
2. Wählen Sie **"****FileImportImport** >  > "-**Datei** aus, um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.  
3. Wählen Sie die Registerkarte **"Sammlungen" aus** .
4. Wählen Sie das Chevron **>** neben dem **Test RSC** aus, um die Detailansicht zu erweitern und die API-Anforderungen anzuzeigen.

Führen Sie die gesamte Berechtigungssammlung für jeden API-Aufruf aus. Die berechtigungen, die Sie in Ihrem App-Manifest angegeben haben, müssen erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen müssen. Überprüfen Sie alle Antwortstatuscodes, um zu überprüfen, ob das Verhalten der RSC-Berechtigungen in Ihrer App die Erwartungen erfüllt.

> [!NOTE]
> Um bestimmte DELETE- und READ-API-Aufrufe zu testen, fügen Sie diese Instanzszenarien zur JSON-Datei hinzu.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testen widerrufener RSC-Berechtigungen mit [Postman](https://www.postman.com/)

1. Deinstallieren Sie die App aus der jeweiligen Ressource.
2. Führen Sie die Schritte für Chat oder Team aus:
    1. [Test hat RSC-Berechtigungen zu einem Team mitHilfe von Postman hinzugefügt](#test-added-rsc-permissions-to-a-team-using-the-postman-app).
    2. [Test hat RSC-Berechtigungen zu einem Chat mit Postman hinzugefügt](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).
3. Überprüfen Sie alle Antwortstatuscodes, um zu überprüfen, ob die spezifischen **API-Aufrufe mit einem HTTP 403-Statuscode fehlgeschlagen sind**.

## <a name="see-also"></a>Siehe auch

* [Microsoft Graph-API und Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)
* [Ressourcenspezifische Zustimmung](~/graph-api/rsc/resource-specific-consent.md)
