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
# <a name="test-resource-specific-consent-permissions-in-teams"></a><span data-ttu-id="ebe70-104">Testen ressourcenspezifischer Zustimmungsberechtigungen in Teams</span><span class="sxs-lookup"><span data-stu-id="ebe70-104">Test resource-specific consent permissions in Teams</span></span>

<span data-ttu-id="ebe70-105">Resource-specific consent (RSC) ist eine Microsoft Teams- und Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Teams innerhalb einer Organisation zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="ebe70-105">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific teams within an organization.</span></span> <span data-ttu-id="ebe70-106">Weitere Informationen finden Sie unter [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span><span class="sxs-lookup"><span data-stu-id="ebe70-106">For more information, see [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ebe70-107">Zum Testen der RSC-Berechtigungen muss Ihre Teams-App-Manifestdatei einen **webApplicationInfo-Schlüssel** enthalten, der mit den folgenden Feldern gefüllt ist:</span><span class="sxs-lookup"><span data-stu-id="ebe70-107">To test the RSC permissions, your Teams app manifest file must include a **webApplicationInfo** key populated with the following fields:</span></span>
>
> - <span data-ttu-id="ebe70-108">**id**: Ihre Azure AD-App-ID finden Sie [unter Registrieren Ihrer App im Azure AD-Portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span><span class="sxs-lookup"><span data-stu-id="ebe70-108">**id**: Your Azure AD app ID, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="ebe70-109">**resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="ebe70-109">**resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest)</span></span>
> - <span data-ttu-id="ebe70-110">**Anwendungsberechtigungen**: RSC-Berechtigungen für Ihre App finden Sie unter [Ressourcenspezifische Berechtigungen](resource-specific-consent.md#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="ebe70-110">**application permissions**: RSC permissions for  your app, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

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
> <span data-ttu-id="ebe70-111">Fügen Sie in Ihr App-Manifest nur die RSC-Berechtigungen ein, die Ihre App besitzen soll.</span><span class="sxs-lookup"><span data-stu-id="ebe70-111">In your app manifest, only include the RSC permissions that you want your app to have.</span></span>

## <a name="test-added-rsc-permissions-using-the-postman-app"></a><span data-ttu-id="ebe70-112">Testen hinzugefügter RSC-Berechtigungen mithilfe der Postman-App</span><span class="sxs-lookup"><span data-stu-id="ebe70-112">Test added RSC permissions using the Postman app</span></span>

<span data-ttu-id="ebe70-113">Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC-JSON-Testcode](test-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="ebe70-113">To check whether the RSC permissions are being honored by the API request payload, you need to copy the [RSC JSON test code](test-rsc-json-file.md) into your local environment and update the following values:</span></span>

* <span data-ttu-id="ebe70-114">`azureADAppId`: Azure AD-App-ID Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ebe70-114">`azureADAppId`: Your app's Azure AD app ID</span></span>
* <span data-ttu-id="ebe70-115">`azureADAppSecret`: Ihr geheimer Azure AD-App-Schlüssel (Kennwort)</span><span class="sxs-lookup"><span data-stu-id="ebe70-115">`azureADAppSecret`: Your Azure AD app secret (password)</span></span>
* <span data-ttu-id="ebe70-116">`token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen – legen Sie den Wert auf https://graph.microsoft.com/.default</span><span class="sxs-lookup"><span data-stu-id="ebe70-116">`token_scope`: The scope is required to get a token - set the value to https://graph.microsoft.com/.default</span></span>
* <span data-ttu-id="ebe70-117">`teamGroupId`: Sie können die Teamgruppen-ID wie folgt vom Teams-Client erhalten:</span><span class="sxs-lookup"><span data-stu-id="ebe70-117">`teamGroupId`: You can get the team group id from the Teams client as follows:</span></span>

  > [!div class="checklist"]
  >
  > * <span data-ttu-id="ebe70-118">Wählen Sie im Teams-Client **in der Navigationsleiste** ganz links Teams aus.</span><span class="sxs-lookup"><span data-stu-id="ebe70-118">In the Teams client, select **Teams** from the far left navigation bar .</span></span>
  > * <span data-ttu-id="ebe70-119">Wählen Sie im Dropdownmenü das Team aus, in dem die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="ebe70-119">Select the team where the app is installed from the dropdown menu.</span></span>
  > * <span data-ttu-id="ebe70-120">Wählen Sie **das Symbol Weitere Optionen** aus (&#8943;)</span><span class="sxs-lookup"><span data-stu-id="ebe70-120">Select the **More options** icon (&#8943;)</span></span>
  > * <span data-ttu-id="ebe70-121">Wählen **Sie Link zum Team erhalten aus.**</span><span class="sxs-lookup"><span data-stu-id="ebe70-121">Select **Get link to team**</span></span> 
  > * <span data-ttu-id="ebe70-122">Kopieren Und speichern Sie den **groupId-Wert** aus der Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="ebe70-122">Copy and save the **groupId** value from the string.</span></span>

### <a name="use-postman"></a><span data-ttu-id="ebe70-123">Verwenden von Postman</span><span class="sxs-lookup"><span data-stu-id="ebe70-123">Use Postman</span></span>

1. <span data-ttu-id="ebe70-124">Öffnen Sie [die Postman-App.](https://www.postman.com)</span><span class="sxs-lookup"><span data-stu-id="ebe70-124">Open the [Postman](https://www.postman.com) app.</span></span>
2. <span data-ttu-id="ebe70-125">Wählen **Sie**  >  **Dateiimport**  >  **importieren aus,** um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="ebe70-125">Select **File** > **Import** > **Import file** to upload the updated JSON file from your environment.</span></span>  
3. <span data-ttu-id="ebe70-126">Wählen Sie die **Registerkarte Sammlungen** aus.</span><span class="sxs-lookup"><span data-stu-id="ebe70-126">Select the **Collections** tab.</span></span> 
4. <span data-ttu-id="ebe70-127">Wählen Sie den Chevron neben der RSC testen aus, um die Detailansicht zu **>** erweitern und die API-Anforderungen anzuzeigen. </span><span class="sxs-lookup"><span data-stu-id="ebe70-127">Select the chevron **>** next to the **Test RSC** to expand the details view and see the API requests.</span></span>

<span data-ttu-id="ebe70-128">Führen Sie die gesamte Berechtigungssammlung für jeden API-Aufruf aus.</span><span class="sxs-lookup"><span data-stu-id="ebe70-128">Execute the entire permissions collection for each API call.</span></span> <span data-ttu-id="ebe70-129">Die Berechtigungen, die Sie im App-Manifest angegeben haben, müssen erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen müssen.</span><span class="sxs-lookup"><span data-stu-id="ebe70-129">The permissions that you specified in your app manifest must succeed, while those not specified must fail with an HTTP 403 status code.</span></span> <span data-ttu-id="ebe70-130">Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass das Verhalten der RSC-Berechtigungen in Ihrer App den Erwartungen entspricht.</span><span class="sxs-lookup"><span data-stu-id="ebe70-130">Check all of the response status codes to confirm that the behavior of the RSC permissions in your app meet expectations.</span></span>

> [!NOTE]
> <span data-ttu-id="ebe70-131">Um bestimmte DELETE- und READ-API-Aufrufe zu testen, fügen Sie diese Instanzszenarien der JSON-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="ebe70-131">To test specific DELETE and READ API calls, add those instance scenarios to the JSON file.</span></span>

## <a name="test-revoked-rsc-permissions-using-postman"></a><span data-ttu-id="ebe70-132">Testen widerrufener RSC-Berechtigungen mithilfe [von Postman](https://www.postman.com/)</span><span class="sxs-lookup"><span data-stu-id="ebe70-132">Test revoked RSC permissions using [Postman](https://www.postman.com/)</span></span>

1. <span data-ttu-id="ebe70-133">Deinstallieren Sie die App aus dem jeweiligen Team.</span><span class="sxs-lookup"><span data-stu-id="ebe70-133">Uninstall the app from the specific team.</span></span>
2. <span data-ttu-id="ebe70-134">Führen Sie die Schritte für [Test added RSC permissions using Postman aus.](#test-added-rsc-permissions-using-the-postman-app)</span><span class="sxs-lookup"><span data-stu-id="ebe70-134">Follow the steps for [Test added RSC permissions using Postman](#test-added-rsc-permissions-using-the-postman-app).</span></span>
3. <span data-ttu-id="ebe70-135">Überprüfen Sie alle Antwortstatuscodes, um zu bestätigen, dass die spezifischen API-Aufrufe erfolgreich mit einem **HTTP 403-Statuscode fehlgeschlagen sind.**</span><span class="sxs-lookup"><span data-stu-id="ebe70-135">Check all the response status codes to confirm that the specific API calls, **succeeded, have failed with an HTTP 403 status code**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebe70-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ebe70-136">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ebe70-137">Microsoft Graph-API und Teams</span><span class="sxs-lookup"><span data-stu-id="ebe70-137">Microsoft Graph API and Teams</span></span>](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

