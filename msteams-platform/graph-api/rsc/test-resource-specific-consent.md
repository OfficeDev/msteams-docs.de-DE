---
title: Testen der ressourcenspezifischen Zustimmung in Microsoft Teams
description: Details Testen der ressourcenspezifischen Zustimmung in Teams mithilfe von Postman
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: tutorial
keywords: Teams Authorization OAuth SSO Aad RSC Postman Graph
ms.openlocfilehash: f50f61e7eb62e3bcc6af2dafc1c7c781ff2145de
ms.sourcegitcommit: 43e1be9d9e3651ce73a8d2139e44d75550a0ca60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "49366854"
---
# <a name="test-resource-specific-consent-permissions--in-teams"></a>Testen von Berechtigungen für die ressourcenspezifische Zustimmung in Microsoft Teams

Die ressourcenspezifische Zustimmung (RSC) ist eine Microsoft Teams-und Graph-API-Integration, die es Ihrer APP ermöglicht, API-Endpunkte zum Verwalten bestimmter Teams in einer Organisation zu verwenden. *Weitere Informationen finden Sie unter*[ressourcenspezifische Zustimmung (RSC) – Microsoft Teams Graph-API](resource-specific-consent.md).  

> [!NOTE]
>Um die RSC-Berechtigungen zu testen, muss ihre Teams-App-Manifestdatei einen **webApplicationInfo** -Schlüssel enthalten, der mit den folgenden Feldern aufgefüllt ist:
>
> - **ID**  – ihre Azure AD App-ID *finden Sie unter* [Registrieren Ihrer APP im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).
> - **Resource** – eine beliebige Zeichenfolge *finden Sie* im Hinweis zum [Aktualisieren Ihres Teams-App-Manifests](resource-specific-consent.md#update-your-teams-app-manifest) .
> - **Anwendungsberechtigungen** – RSC-Berechtigungen für Ihre APP *finden Sie unter* [ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).

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

>[!IMPORTANT]
>Fügen Sie in Ihrem App-Manifest nur die RSC-Berechtigungen ein, die Ihre APP haben soll.

## <a name="test-added-rsc-permissions-using-the-postman-app"></a>Testen der hinzugefügten RSC-Berechtigungen mithilfe der Postman-App

Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC-JSON-Testcode](test-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:

1. `azureADAppId`  – die Azure AD App-ID Ihrer APP.
1. `azureADAppSecret`  – Ihr geheimer Azure AD-App-Schlüssel (Kennwort)
1. `token_scope`  – der Bereich ist erforderlich, um ein Token zu erhalten – legen Sie den Wert auf https://graph.microsoft.com/.default
1. `teamGroupId` – Sie können die Team Gruppen-ID wie folgt aus dem Microsoft Teams-Client abrufen:

> [!div class="checklist"]
>
> * Wählen Sie im Microsoft Teams-Client die Option **Teams** von der ganz linken Navigationsleiste aus.
> * Wählen Sie im Dropdownmenü das Team aus, in dem die APP installiert ist.
> * Klicken Sie auf das Symbol **Weitere Optionen** (&#8943;)
> * Wählen Sie **Get Link to Team** aus. 
> * Kopieren Sie den Wert der **Gruppe** , und speichern Sie ihn aus der Zeichenfolge.

### <a name="using-postman"></a>Verwenden von Postman

> [!div class="checklist"]
>
> * Öffnen Sie die [Postman](https://www.postman.com) -app.
> * Wählen Sie **Datei**  =>  **Import**  =>  **Importdatei** aus, um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.  
> * Wählen Sie die Registerkarte **Sammlungen** aus. 
> * Wählen Sie das Chevron (>) neben dem **Test-RSC** aus, um die Detailansicht zu erweitern und die API-Anforderungen anzuzeigen.

Führen Sie die gesamte Permissions-Auflistung für jeden API-Aufruf aus. Die Berechtigungen, die Sie in Ihrem App-Manifest angegeben haben, sollten erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen sollten. Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass das Verhalten der RSC-Berechtigungen in Ihrer APP die Erwartungen erfüllt.

>[!NOTE]
>Um bestimmte DELETE-und Read-API-Aufrufe zu testen, fügen Sie diese Instanzen Szenarien der JSON-Datei hinzu.

## <a name="test--revoked-rsc-permissions-using-postman"></a>Testen der aufgehobenen RSC-Berechtigungen mithilfe von [Postman](https://www.postman.com/)

> [!div class="checklist"]
>
> * Deinstallieren Sie die APP aus dem jeweiligen Team.
> * Führen Sie die obigen Schritte aus, um die [RSC-Berechtigungen mit Postman zu testen](#test-added-rsc-permissions-using-the-postman-app).
> * Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass die spezifischen API-Aufrufe, die erfolgreich waren, mit einem HTTP 403-Statuscode fehlgeschlagen sind.

> [!div class="nextstepaction"]
>
> [Weitere Informationen: Microsoft Graph-API und Teams](/graph/api/resources/teams-api-overview?view=graph-rest-1.0)

