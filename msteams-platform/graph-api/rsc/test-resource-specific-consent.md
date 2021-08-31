---
title: Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams
description: Details zum Testen der ressourcenspezifischen Zustimmung in Teams mit Postman
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: Teams-Autorisierung OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: 629d798e600a3a9a9ba1cbd7fd75bdc8de13a507
ms.sourcegitcommit: 95e0c767ca0f2a51c4a7ca87700ce50b7b154b7c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2021
ms.locfileid: "58528943"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams

> [!NOTE]
> Die ressourcenspezifische Zustimmung für den Chatbereich ist nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die ressourcenspezifische Zustimmung (RSC) ist eine Microsoft Teams- und Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Ressourcen innerhalb einer Organisation zu verwalten – entweder Teams oder Chats. Weitere Informationen finden Sie unter [Resource-specific consent (RSC) – Microsoft Teams Graph API.](resource-specific-consent.md)

> [!NOTE]
> Zum Testen der RSC-Berechtigungen muss ihre Teams App-Manifestdatei einen **webApplicationInfo-Schlüssel** enthalten, der mit den folgenden Feldern gefüllt ist:
>
> - **id:** Ihre Azure AD-App-ID, siehe [Registrieren Ihrer App im Azure AD-Portal.](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-using-the-aad-portal)
> - **Ressource:** Eine beliebige Zeichenfolge finden Sie in der Notiz im [App-Manifest aktualisieren Teams.](resource-specific-consent.md#update-your-teams-app-manifest)
> - **Anwendungsberechtigungen:** RSC-Berechtigungen für Ihre App finden Sie unter ["Ressourcenspezifische Berechtigungen".](resource-specific-consent.md#resource-specific-permissions)

## <a name="example-for-a-team"></a>Beispiel für ein Team
```json
"webApplicationInfo":{
    "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource":"https://AnyString",
    "applicationPermissions":[
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
        "TeamMember.Read.Group"
    ]
   }
```

## <a name="example-for-a-chat"></a>Beispiel für einen Chat
```json
"webApplicationInfo":{
    "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
    "resource":"https://AnyString",
    "applicationPermissions":[
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
        "Calls.JoinGroupCalls.Chat"
    ]
   }
```

> [!IMPORTANT]
> Fügen Sie in Ihrem App-Manifest nur die RSC-Berechtigungen ein, über die Ihre App verfügen soll.

>[!NOTE]
>Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter angegeben `applicationPermissions` werden.

>Wenn die App auf Anruf-/Medien-APIs zugreifen soll, sollte die `webApplicationInfo.Id` AAD-App-ID eines [Azure Bot Service](/graph/cloud-communications-get-started#register-a-bot)sein.

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a>Testen hinzugefügter RSC-Berechtigungen zu einem Team mithilfe der Postman-App

Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC JSON-Testcode für das Team](test-team-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:

* `azureADAppId`: Die Azure AD-App-ID Ihrer App.
* `azureADAppSecret`: Ihr Azure AD-App-Kennwort.
* `token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen. legen Sie den Wert auf https://graph.microsoft.com/.default .
* `teamGroupId`: Sie können die Teamgruppen-ID wie folgt vom Teams-Client abrufen:

    1. Wählen Sie im Teams Client in der Navigationsleiste ganz links **Teams** aus.
    2. Wählen Sie im Dropdownmenü das Team aus, in dem die App installiert ist.
    3. Wählen Sie das Symbol **"Weitere Optionen"** aus (&#8943;).
    4. Wählen Sie **"Link zum Team abrufen" aus.** 
    5. Kopieren und speichern Sie den **groupId-Wert** aus der Zeichenfolge.

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a>Testen hinzugefügter RSC-Berechtigungen zu einem Chat mithilfe der Postman-App

Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC JSON-Testcode für Chats](test-chat-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:

* `azureADAppId`: Die Azure AD-App-ID Ihrer App.
* `azureADAppSecret`: Ihr Azure AD-App-Kennwort.
* `token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen. legen Sie den Wert auf https://graph.microsoft.com/.default .
* `tenantId`: Der Name oder die AAD-Objekt-ID Ihres Mandanten.
* `chatId`: Sie können die Chatthread-ID wie folgt vom *Teams-Webclient* abrufen:

    1. Wählen Sie im Teams Webclient in der linken Navigationsleiste **"Chat"** aus.
    2. Wählen Sie im Dropdownmenü den Chat aus, in dem die App installiert ist.
    3. Kopieren Sie die Web-URL, und speichern Sie die Chatthread-ID aus der Zeichenfolge.
![Chatthread-ID von Web-URL.](../../assets/images/chat-thread-id.png)

### <a name="use-postman"></a>Verwenden von Postman

1. Öffnen Sie die [Postman-App.](https://www.postman.com)
2. Wählen Sie  >    >  **Dateiimport-Importdatei** aus, um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.  
3. Wählen Sie die Registerkarte **"Sammlungen" aus.** 
4. Wählen Sie das Chevron **>** neben dem **Test RSC** aus, um die Detailansicht zu erweitern und die API-Anforderungen anzuzeigen.

Führen Sie die gesamte Berechtigungssammlung für jeden API-Aufruf aus. Die berechtigungen, die Sie in Ihrem App-Manifest angegeben haben, müssen erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen müssen. Überprüfen Sie alle Antwortstatuscodes, um zu überprüfen, ob das Verhalten der RSC-Berechtigungen in Ihrer App die Erwartungen erfüllt.

> [!NOTE]
> Um bestimmte DELETE- und READ-API-Aufrufe zu testen, fügen Sie diese Instanzszenarien zur JSON-Datei hinzu.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testen widerrufener RSC-Berechtigungen mit [Postman](https://www.postman.com/)

1. Deinstallieren Sie die App aus der jeweiligen Ressource.
2. Führen Sie die Schritte für Chat oder Team aus: 
    1. [Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).
    2. [Test hinzugefügt RSC-Berechtigungen zu einem Chat mit Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).
3. Überprüfen Sie alle Antwortstatuscodes, um zu überprüfen, ob die spezifischen API-Aufrufe **mit einem HTTP 403-Statuscode fehlgeschlagen sind.**

## <a name="see-also"></a>Siehe auch

[Microsoft Graph-API und Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

