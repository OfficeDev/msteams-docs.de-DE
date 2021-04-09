---
title: Testen ressourcenspezifischer Zustimmungsberechtigungen in Teams
description: Details zum Testen der ressourcenspezifischen Zustimmung in Teams mithilfe von Postman
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: tutorial
keywords: Teams-Autorisierung OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: 0d3d1c895c77bb417a9fdd84e319103485aa8944
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634708"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a>Testen ressourcenspezifischer Zustimmungsberechtigungen in Teams

Resource-specific consent (RSC) ist eine Microsoft Teams- und Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Teams innerhalb einer Organisation zu verwalten. Weitere Informationen finden Sie unter [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).

> [!NOTE]
> Zum Testen der RSC-Berechtigungen muss Ihre Teams-App-Manifestdatei einen **webApplicationInfo-Schlüssel** enthalten, der mit den folgenden Feldern gefüllt ist:
>
> - **id**: Ihre Azure AD-App-ID finden Sie [unter Registrieren Ihrer App im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest)
> - **Anwendungsberechtigungen**: RSC-Berechtigungen für Ihre App finden Sie unter [Ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).

```json
"webApplicationInfo":{
      "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
      "resource":"https://AnyString",
      "applicationPermissions":[
         "Channel.Create.Group",
         "Channel.Delete.Group",
         "ChannelMessage.Read.Group",
         "ChannelSettings.Read.Group",
         "ChannelSettings.Edit.Group",
         "Member.Read.Group",
         "Owner.Read.Group",
         "TeamsApp.Read.Group",
         "TeamsTab.Read.Group",
         "TeamsTab.Create.Group",
         "TeamsTab.Edit.Group",
         "TeamsTab.Delete.Group",
         "TeamSettings.Read.Group",
         "TeamSettings.Edit.Group"
      ]
   }
```

> [!IMPORTANT]
> Fügen Sie in Ihr App-Manifest nur die RSC-Berechtigungen ein, die Ihre App besitzen soll.

## <a name="test-added-rsc-permissions-using-the-postman-app"></a>Testen hinzugefügter RSC-Berechtigungen mithilfe der Postman-App

Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC-JSON-Testcode](test-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:

* `azureADAppId`: Azure AD-App-ID Ihrer App
* `azureADAppSecret`: Ihr geheimer Azure AD-App-Schlüssel (Kennwort)
* `token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen – legen Sie den Wert auf https://graph.microsoft.com/.default
* `teamGroupId`: Sie können die Teamgruppen-ID wie folgt vom Teams-Client erhalten:

  > [!div class="checklist"]
  >
  > * Wählen Sie im Teams-Client **in der Navigationsleiste** ganz links Teams aus.
  > * Wählen Sie im Dropdownmenü das Team aus, in dem die App installiert ist.
  > * Wählen Sie **das Symbol Weitere Optionen** aus (&#8943;)
  > * Wählen **Sie Link zum Team erhalten aus.** 
  > * Kopieren Und speichern Sie den **groupId-Wert** aus der Zeichenfolge.

### <a name="use-postman"></a>Verwenden von Postman

1. Öffnen Sie [die Postman-App.](https://www.postman.com)
2. Wählen **Sie**  >  **Dateiimport**  >  **importieren aus,** um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.  
3. Wählen Sie die **Registerkarte Sammlungen** aus. 
4. Wählen Sie den Chevron neben der RSC testen aus, um die Detailansicht zu **>** erweitern und die API-Anforderungen anzuzeigen. 

Führen Sie die gesamte Berechtigungssammlung für jeden API-Aufruf aus. Die Berechtigungen, die Sie im App-Manifest angegeben haben, müssen erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen müssen. Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass das Verhalten der RSC-Berechtigungen in Ihrer App den Erwartungen entspricht.

> [!NOTE]
> Um bestimmte DELETE- und READ-API-Aufrufe zu testen, fügen Sie diese Instanzszenarien der JSON-Datei hinzu.

## <a name="test-revoked-rsc-permissions-using-postman"></a>Testen widerrufener RSC-Berechtigungen mithilfe [von Postman](https://www.postman.com/)

1. Deinstallieren Sie die App aus dem jeweiligen Team.
2. Führen Sie die Schritte für [Test added RSC permissions using Postman aus.](#test-added-rsc-permissions-using-the-postman-app)
3. Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass die spezifischen API-Aufrufe erfolgreich mit einem **HTTP 403-Statuscode fehlgeschlagen sind.**

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Microsoft Graph-API und Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

