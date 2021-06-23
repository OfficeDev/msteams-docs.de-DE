---
title: Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams
description: Details zum Testen der ressourcenspezifischen Zustimmung in Teams mit Postman
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: tutorial
keywords: Teams-Autorisierung OAuth SSO AAD rsc Postman Graph
ms.openlocfilehash: 92c6d5d96c103fb5e0da6afd91357b5887b2ba10
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069084"
---
# <a name="test-resource-specific-consent-permissions-in-teams"></a><span data-ttu-id="0ac4f-104">Testen von ressourcenspezifischen Zustimmungsberechtigungen in Teams</span><span class="sxs-lookup"><span data-stu-id="0ac4f-104">Test resource-specific consent permissions in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="0ac4f-105">Die ressourcenspezifische Zustimmung für den Chatbereich ist nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-105">Resource-specific consent for chat scope is available in [public developer preview](../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="0ac4f-106">Die ressourcenspezifische Zustimmung (RESOURCE-Specific Consent, RSC) ist eine Microsoft Teams- und Graph-API-Integration, mit der Ihre App API-Endpunkte verwenden kann, um bestimmte Ressourcen innerhalb einer Organisation zu verwalten – entweder Teams oder Chats.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-106">Resource-specific consent (RSC) is a Microsoft Teams and Graph API integration that enables your app to use API endpoints to manage specific resources—either teams or chats—within an organization.</span></span> <span data-ttu-id="0ac4f-107">Weitere Informationen finden Sie unter [Resource-specific consent (RSC) – Microsoft Teams Graph API.](resource-specific-consent.md)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-107">For more information, see [Resource-specific consent (RSC) — Microsoft Teams Graph API](resource-specific-consent.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0ac4f-108">Zum Testen der RSC-Berechtigungen muss ihre Teams App-Manifestdatei einen **webApplicationInfo-Schlüssel** enthalten, der mit den folgenden Feldern gefüllt ist:</span><span class="sxs-lookup"><span data-stu-id="0ac4f-108">To test the RSC permissions, your Teams app manifest file must include a **webApplicationInfo** key populated with the following fields:</span></span>
>
> - <span data-ttu-id="0ac4f-109">**id:** Ihre Azure AD-App-ID, siehe [Registrieren Ihrer App im Azure AD-Portal.](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-109">**id**: Your Azure AD app ID, see [Register your app in the Azure AD portal](resource-specific-consent.md#register-your-app-with-microsoft-identity-platform-via-the-azure-ad-portal).</span></span>
> - <span data-ttu-id="0ac4f-110">**Ressource:** Eine beliebige Zeichenfolge finden Sie in der Notiz im [App-Manifest aktualisieren Teams.](resource-specific-consent.md#update-your-teams-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-110">**resource**: Any string, see the note in  [Update your Teams app manifest](resource-specific-consent.md#update-your-teams-app-manifest).</span></span>
> - <span data-ttu-id="0ac4f-111">**Anwendungsberechtigungen:** RSC-Berechtigungen für Ihre App finden Sie unter ["Ressourcenspezifische Berechtigungen".](resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-111">**application permissions**: RSC permissions for  your app, see [Resource-specific Permissions](resource-specific-consent.md#resource-specific-permissions).</span></span>

## <a name="example-for-a-team"></a><span data-ttu-id="0ac4f-112">Beispiel für ein Team</span><span class="sxs-lookup"><span data-stu-id="0ac4f-112">Example for a team</span></span>
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

## <a name="example-for-a-chat"></a><span data-ttu-id="0ac4f-113">Beispiel für einen Chat</span><span class="sxs-lookup"><span data-stu-id="0ac4f-113">Example for a chat</span></span>
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
          "OnlineMeeting.ReadBasic.Chat"
      ]
   }
```

> [!IMPORTANT]
> <span data-ttu-id="0ac4f-114">Fügen Sie in Ihrem App-Manifest nur die RSC-Berechtigungen ein, über die Ihre App verfügen soll.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-114">In your app manifest, only include the RSC permissions that you want your app to have.</span></span>

>[!NOTE]
><span data-ttu-id="0ac4f-115">Wenn die App die Installation sowohl im Team- als auch im Chatbereich unterstützen soll, können sowohl Team- als auch Chatberechtigungen im selben Manifest unter angegeben `applicationPermissions` werden.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-115">If the app is meant to support installation in both team and chat scopes, then both team and chat permissions can be specified in the same manifest under `applicationPermissions`.</span></span>

## <a name="test-added-rsc-permissions-to-a-team-using-the-postman-app"></a><span data-ttu-id="0ac4f-116">Testen hinzugefügter RSC-Berechtigungen zu einem Team mithilfe der Postman-App</span><span class="sxs-lookup"><span data-stu-id="0ac4f-116">Test added RSC permissions to a team using the Postman app</span></span>

<span data-ttu-id="0ac4f-117">Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC JSON-Testcode für das Team](test-team-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="0ac4f-117">To check whether the RSC permissions are being honored by the API request payload, you need to copy the [RSC JSON test code for team](test-team-rsc-json-file.md) into your local environment and update the following values:</span></span>

* <span data-ttu-id="0ac4f-118">`azureADAppId`: Die Azure AD-App-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-118">`azureADAppId`: Your app's Azure AD app ID.</span></span>
* <span data-ttu-id="0ac4f-119">`azureADAppSecret`: Ihr Azure AD-App-Kennwort.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-119">`azureADAppSecret`: Your Azure AD app password.</span></span>
* <span data-ttu-id="0ac4f-120">`token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-120">`token_scope`: The scope is required to get a token.</span></span> <span data-ttu-id="0ac4f-121">legen Sie den Wert auf https://graph.microsoft.com/.default .</span><span class="sxs-lookup"><span data-stu-id="0ac4f-121">set the value to https://graph.microsoft.com/.default.</span></span>
* <span data-ttu-id="0ac4f-122">`teamGroupId`: Sie können die Teamgruppen-ID wie folgt vom Teams-Client abrufen:</span><span class="sxs-lookup"><span data-stu-id="0ac4f-122">`teamGroupId`: You can get the team group id from the Teams client as follows:</span></span>

    1. <span data-ttu-id="0ac4f-123">Wählen Sie im Teams Client in der Navigationsleiste ganz links **Teams** aus.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-123">In the Teams client, select **Teams** from the far left navigation bar.</span></span>
    2. <span data-ttu-id="0ac4f-124">Wählen Sie im Dropdownmenü das Team aus, in dem die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-124">Select the team where the app is installed from the dropdown menu.</span></span>
    3. <span data-ttu-id="0ac4f-125">Wählen Sie das Symbol **"Weitere Optionen"** aus (&#8943;).</span><span class="sxs-lookup"><span data-stu-id="0ac4f-125">Select the **More options** icon (&#8943;).</span></span>
    4. <span data-ttu-id="0ac4f-126">Wählen Sie **"Link zum Team abrufen" aus.**</span><span class="sxs-lookup"><span data-stu-id="0ac4f-126">Select **Get link to team**.</span></span> 
    5. <span data-ttu-id="0ac4f-127">Kopieren und speichern Sie den **groupId-Wert** aus der Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-127">Copy and save the **groupId** value from the string.</span></span>

## <a name="test-added-rsc-permissions-to-a-chat-using-the-postman-app"></a><span data-ttu-id="0ac4f-128">Testen hinzugefügter RSC-Berechtigungen zu einem Chat mithilfe der Postman-App</span><span class="sxs-lookup"><span data-stu-id="0ac4f-128">Test added RSC permissions to a chat using the Postman app</span></span>

<span data-ttu-id="0ac4f-129">Um zu überprüfen, ob die RSC-Berechtigungen von der API-Anforderungsnutzlast berücksichtigt werden, müssen Sie den [RSC JSON-Testcode für Chats](test-chat-rsc-json-file.md) in Ihre lokale Umgebung kopieren und die folgenden Werte aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="0ac4f-129">To check whether the RSC permissions are being honored by the API request payload, you need to copy the [RSC JSON test code for chats](test-chat-rsc-json-file.md) into your local environment and update the following values:</span></span>

* <span data-ttu-id="0ac4f-130">`azureADAppId`: Die Azure AD-App-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-130">`azureADAppId`: Your app's Azure AD app ID.</span></span>
* <span data-ttu-id="0ac4f-131">`azureADAppSecret`: Ihr Azure AD-App-Kennwort.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-131">`azureADAppSecret`: Your Azure AD app password.</span></span>
* <span data-ttu-id="0ac4f-132">`token_scope`: Der Bereich ist erforderlich, um ein Token abzurufen.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-132">`token_scope`: The scope is required to get a token.</span></span> <span data-ttu-id="0ac4f-133">legen Sie den Wert auf https://graph.microsoft.com/.default .</span><span class="sxs-lookup"><span data-stu-id="0ac4f-133">set the value to https://graph.microsoft.com/.default.</span></span>
* <span data-ttu-id="0ac4f-134">`tenantId`: Der Name oder die AAD-Objekt-ID Ihres Mandanten.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-134">`tenantId`: The name or the AAD Object ID of your tenant.</span></span>
* <span data-ttu-id="0ac4f-135">`chatId`: Sie können die Chatthread-ID wie folgt vom *Teams-Webclient* abrufen:</span><span class="sxs-lookup"><span data-stu-id="0ac4f-135">`chatId`: You can get the chat thread id from the Teams *web* client as follows:</span></span>

    1. <span data-ttu-id="0ac4f-136">Wählen Sie im Teams Webclient in der Navigationsleiste ganz links die Option **"Chat"** aus.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-136">In the Teams web client, select **Chat** from the far left navigation bar.</span></span>
    2. <span data-ttu-id="0ac4f-137">Wählen Sie im Dropdownmenü den Chat aus, in dem die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-137">Select the chat where the app is installed from the dropdown menu.</span></span>
    3. <span data-ttu-id="0ac4f-138">Kopieren Sie die Web-URL, und speichern Sie die Chatthread-ID aus der Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-138">Copy the web URL and save the chat thread id from the string.</span></span>
<span data-ttu-id="0ac4f-139">![Chatthread-ID von Web-URL.](../../assets/images/chat-thread-id.png)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-139">![Chat thread id from web URL.](../../assets/images/chat-thread-id.png)</span></span>

### <a name="use-postman"></a><span data-ttu-id="0ac4f-140">Verwenden von Postman</span><span class="sxs-lookup"><span data-stu-id="0ac4f-140">Use Postman</span></span>

1. <span data-ttu-id="0ac4f-141">Öffnen Sie die [Postman-App.](https://www.postman.com)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-141">Open the [Postman](https://www.postman.com) app.</span></span>
2. <span data-ttu-id="0ac4f-142">Wählen Sie  >    >  **Dateiimport-Importdatei** aus, um die aktualisierte JSON-Datei aus Ihrer Umgebung hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-142">Select **File** > **Import** > **Import file** to upload the updated JSON file from your environment.</span></span>  
3. <span data-ttu-id="0ac4f-143">Wählen Sie die Registerkarte **"Sammlungen" aus.**</span><span class="sxs-lookup"><span data-stu-id="0ac4f-143">Select the **Collections** tab.</span></span> 
4. <span data-ttu-id="0ac4f-144">Wählen Sie das Chevron **>** neben dem **Test RSC** aus, um die Detailansicht zu erweitern und die API-Anforderungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-144">Select the chevron **>** next to the **Test RSC** to expand the details view and see the API requests.</span></span>

<span data-ttu-id="0ac4f-145">Führen Sie die gesamte Berechtigungssammlung für jeden API-Aufruf aus.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-145">Execute the entire permissions collection for each API call.</span></span> <span data-ttu-id="0ac4f-146">Die berechtigungen, die Sie in Ihrem App-Manifest angegeben haben, müssen erfolgreich sein, während die nicht angegebenen Berechtigungen mit einem HTTP 403-Statuscode fehlschlagen müssen.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-146">The permissions that you specified in your app manifest must succeed, while those not specified must fail with an HTTP 403 status code.</span></span> <span data-ttu-id="0ac4f-147">Überprüfen Sie alle Antwortstatuscodes, um zu überprüfen, ob das Verhalten der RSC-Berechtigungen in Ihrer App die Erwartungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-147">Check all of the response status codes to confirm that the behavior of the RSC permissions in your app meet expectations.</span></span>

> [!NOTE]
> <span data-ttu-id="0ac4f-148">Um bestimmte DELETE- und READ-API-Aufrufe zu testen, fügen Sie diese Instanzszenarien zur JSON-Datei hinzu.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-148">To test specific DELETE and READ API calls, add those instance scenarios to the JSON file.</span></span>

## <a name="test-revoked-rsc-permissions-using-postman"></a><span data-ttu-id="0ac4f-149">Testen widerrufener RSC-Berechtigungen mit [Postman](https://www.postman.com/)</span><span class="sxs-lookup"><span data-stu-id="0ac4f-149">Test revoked RSC permissions using [Postman](https://www.postman.com/)</span></span>

1. <span data-ttu-id="0ac4f-150">Deinstallieren Sie die App aus der jeweiligen Ressource.</span><span class="sxs-lookup"><span data-stu-id="0ac4f-150">Uninstall the app from the specific resource.</span></span>
2. <span data-ttu-id="0ac4f-151">Führen Sie die Schritte für Chat oder Team aus:</span><span class="sxs-lookup"><span data-stu-id="0ac4f-151">Follow the steps for either chat or team:</span></span> 
    1. <span data-ttu-id="0ac4f-152">[Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).</span><span class="sxs-lookup"><span data-stu-id="0ac4f-152">[Test added RSC permissions to a team using Postman](#test-added-rsc-permissions-to-a-team-using-the-postman-app).</span></span>
    2. <span data-ttu-id="0ac4f-153">[Test hinzugefügt RSC-Berechtigungen zu einem Chat mit Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).</span><span class="sxs-lookup"><span data-stu-id="0ac4f-153">[Test added RSC permissions to a chat using Postman](#test-added-rsc-permissions-to-a-chat-using-the-postman-app).</span></span>
3. <span data-ttu-id="0ac4f-154">Überprüfen Sie alle Antwortstatuscodes, um zu überprüfen, ob die spezifischen API-Aufrufe **mit einem HTTP 403-Statuscode fehlgeschlagen sind.**</span><span class="sxs-lookup"><span data-stu-id="0ac4f-154">Check all the response status codes to confirm that the specific API calls **have failed with an HTTP 403 status code**.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac4f-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0ac4f-155">See also</span></span>

[<span data-ttu-id="0ac4f-156">Microsoft Graph-API und Teams</span><span class="sxs-lookup"><span data-stu-id="0ac4f-156">Microsoft Graph API and Teams</span></span>](/graph/api/resources/teams-api-overview?view=graph-rest-1.0&preserve-view=true)

