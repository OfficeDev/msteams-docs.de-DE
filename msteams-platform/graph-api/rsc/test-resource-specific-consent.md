---
title: Testen der ressourcenspezifischen Zustimmung in Microsoft Teams
description: Details Testen der ressourcenspezifischen Zustimmung in Teams mithilfe von Postman
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: How-to
keywords: Teams Authorization OAuth SSO Aad RSC Postman Graph
ms.openlocfilehash: c1c02c2ba0051193aa459d0df26fadfc9fa55550
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867102"
---
# <a name="test-resource-specific-consent-permissions--in-teams"></a><span data-ttu-id="9e623-104">Testen von Berechtigungen für die ressourcenspezifische Zustimmung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9e623-104">Test resource-specific consent permissions  in Teams</span></span>

<span data-ttu-id="9e623-105">Die ressourcenspezifische Zustimmung (RSC) ist eine Microsoft Teams-und Graph-API-Integration, die es Ihrer APP ermöglicht, API-Endpunkte zum Verwalten bestimmter Teams in einer Organisation zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9e623-105">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="9e623-106">*Weitere Informationen finden Sie unter*[ressourcenspezifische Zustimmung (RSC) – Microsoft Teams Graph-API](resource-specific-consent.md).  </span><span class="sxs-lookup"><span data-stu-id="9e623-106">Please *see*  [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span></span>

> [!NOTE]
><span data-ttu-id="9e623-107">Um die RSC-Berechtigungen zu testen, muss ihre Teams-App-Manifestdatei einen **webApplicationInfo** -Schlüssel enthalten, der mit den folgenden Feldern aufgefüllt ist:</span><span class="sxs-lookup"><span data-stu-id="9e623-107">To test the RSC permissions, your Teams app manifest file must include a **webApplicationInfo** key populated with the following fields:</span></span>
>
> - <span data-ttu-id="9e623-108">**ID** – ihre Azure AD App-ID *finden Sie unter* [Registrieren Ihrer APP im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="9e623-108">**id**  — your Azure AD app id, *see* [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="9e623-109">**Resource** – eine beliebige Zeichenfolge *finden Sie* im Hinweis zum [Aktualisieren Ihres Teams-App-Manifests](resource-specific-consent.md#update-your-teams-app-manifest) .</span><span class="sxs-lookup"><span data-stu-id="9e623-109">**resource**  — any string, *see* the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest)</span></span>
> - <span data-ttu-id="9e623-110">**Anwendungsberechtigungen** – RSC-Berechtigungen für Ihre APP *finden Sie unter* [ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="9e623-110">**application permissions** — RSC permissions for  your app, *see* [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

```json
"webApplicationInfo":{
      "id":"XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
      "resource":"https://AnyString",
      "applicationPermissions":[
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

>[!IMPORTANT]
><span data-ttu-id="9e623-111">Fügen Sie in Ihrem App-Manifest nur die RSC-Berechtigungen ein, die Ihre APP haben soll.</span><span class="sxs-lookup"><span data-stu-id="9e623-111">In your app manifest, only include the RSC permissions that you want your app to have.</span></span>

## <a name="test-added-rsc-permissions-using-the-postman-app"></a><span data-ttu-id="9e623-112">Testen der hinzugefügten RSC-Berechtigungen mithilfe der Postman-App</span><span class="sxs-lookup"><span data-stu-id="9e623-112">Test added RSC permissions using the Postman app</span></span>

<span data-ttu-id="9e623-113">Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC-JSON-Testcode](test-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="9e623-113">To check whether the RSC permissions are being honored by the API request payload, you'll need to copy the [RSC JSON test code](test-rsc-json-file.md) into your local environment and update the following values:</span></span>

1. <span data-ttu-id="9e623-114">`azureADAppId`– die Azure AD App-ID Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="9e623-114">`azureADAppId`  — your app's Azure AD app id.</span></span>
1. <span data-ttu-id="9e623-115">`azureADAppSecret`– Ihr geheimer Azure AD-App-Schlüssel (Kennwort)</span><span class="sxs-lookup"><span data-stu-id="9e623-115">`azureADAppSecret`  — your Azure AD app secret (password)</span></span>
1. <span data-ttu-id="9e623-116">`teamGroupId`– Sie können die Team Gruppen-ID wie folgt aus dem Microsoft Teams-Client abrufen:</span><span class="sxs-lookup"><span data-stu-id="9e623-116">`teamGroupId` — you can get the team group id from the Teams client as follows:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9e623-117">Wählen Sie im Microsoft Teams-Client die Option **Teams** von der ganz linken Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="9e623-117">In the Teams client, select **Teams** from the far left nav bar .</span></span>
> * <span data-ttu-id="9e623-118">Wählen Sie im Dropdownmenü das Team aus, in dem die APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="9e623-118">Select the team where the app is installed from the dropdown menu.</span></span>
> * <span data-ttu-id="9e623-119">Klicken Sie auf das Symbol **Weitere Optionen** (&#8943;)</span><span class="sxs-lookup"><span data-stu-id="9e623-119">Select the **More options** icon (&#8943;)</span></span>
> * <span data-ttu-id="9e623-120">Wählen Sie **Get Link to Team** aus.</span><span class="sxs-lookup"><span data-stu-id="9e623-120">Select **Get link to team**</span></span> 
> * <span data-ttu-id="9e623-121">Kopieren Sie den Wert der **Gruppe** , und speichern Sie ihn aus der Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="9e623-121">Copy and save the **groupId** value from the string.</span></span>

### <a name="using-postman"></a><span data-ttu-id="9e623-122">Verwenden von Postman</span><span class="sxs-lookup"><span data-stu-id="9e623-122">Using Postman</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9e623-123">Öffnen Sie die [Postman](https://www.postman.com) -app.</span><span class="sxs-lookup"><span data-stu-id="9e623-123">Open the [Postman](https://www.postman.com) app.</span></span>
> * <span data-ttu-id="9e623-124">Wählen Sie **Datei**  =>  **Import**  =>  **Importdatei** aus, um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="9e623-124">Select **File** => **Import** => **Import file** to upload the updated JSON file from your environment.</span></span>  
> * <span data-ttu-id="9e623-125">Wählen Sie die Registerkarte **Sammlungen** aus.</span><span class="sxs-lookup"><span data-stu-id="9e623-125">Select the **Collections** tab.</span></span> 
> * <span data-ttu-id="9e623-126">Wählen Sie das Chevron (>) neben dem **Test-RSC** aus, um die Detailansicht zu erweitern und die API-Anforderungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9e623-126">Select the chevron (>) next to the **Test RSC** to expand the details view and see the API requests.</span></span>

<span data-ttu-id="9e623-127">Führen Sie die gesamte Permissions-Auflistung für jeden API-Aufruf aus.</span><span class="sxs-lookup"><span data-stu-id="9e623-127">Execute the entire permissions collection for each API call.</span></span> <span data-ttu-id="9e623-128">Die Berechtigungen, die Sie in Ihrem App-Manifest angegeben haben, sollten erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen sollten.</span><span class="sxs-lookup"><span data-stu-id="9e623-128">The permissions that you specified in your app manifest should succeed, while those not specified should fail with an HTTP 403 status code.</span></span> <span data-ttu-id="9e623-129">Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass das Verhalten der RSC-Berechtigungen in Ihrer APP die Erwartungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="9e623-129">Check all of the response status codes to confirm that the behavior of the RSC permissions in your app meet expectations.</span></span>

>[!NOTE]
><span data-ttu-id="9e623-130">Um bestimmte DELETE-und Read-API-Aufrufe zu testen, fügen Sie diese Instanzen Szenarien der JSON-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="9e623-130">To test specific DELETE and READ API calls, please add those instance scenarios to the JSON file.</span></span>

## <a name="test--revoked-rsc-permissions-using-postman"></a><span data-ttu-id="9e623-131">Testen der aufgehobenen RSC-Berechtigungen mithilfe von [Postman](https://www.postman.com/)</span><span class="sxs-lookup"><span data-stu-id="9e623-131">Test  revoked RSC permissions using [Postman](https://www.postman.com/)</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9e623-132">Deinstallieren Sie die APP aus dem jeweiligen Team.</span><span class="sxs-lookup"><span data-stu-id="9e623-132">Uninstall the app from the specific team.</span></span>
> * <span data-ttu-id="9e623-133">Führen Sie die obigen Schritte aus, um die [RSC-Berechtigungen mit Postman zu testen](#test-added-rsc-permissions-using-the-postman-app).</span><span class="sxs-lookup"><span data-stu-id="9e623-133">Follow the steps above for [Test added RSC permissions using Postman](#test-added-rsc-permissions-using-the-postman-app).</span></span>
> * <span data-ttu-id="9e623-134">Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass die spezifischen API-Aufrufe, die erfolgreich waren, mit einem HTTP 403-Statuscode fehlgeschlagen sind.</span><span class="sxs-lookup"><span data-stu-id="9e623-134">Check all of the response status codes to confirm that the specific API calls that succeeded have failed with an HTTP 403 status code.</span></span>

> [!div class="nextstepaction"]
>
> [<span data-ttu-id="9e623-135">Weitere Informationen zur Graph-API und zu Teams</span><span class="sxs-lookup"><span data-stu-id="9e623-135">Learn more about the Graph API and Teams</span></span>](/graph/api/resources/teams-api-overview?view=graph-rest-1.0)
