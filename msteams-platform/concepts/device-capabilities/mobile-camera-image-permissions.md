---
title: Integrieren von Medienfunktionen
author: Rajeshwari-v
description: Verwenden des Teams JavaScript-Client-SDK zum Aktivieren von Medienfunktionen
keywords: Kamerabildmikrofonfunktionen Systemeigene Geräteberechtigungen Medien
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 48566c6301141d8c7755482a1f5f5daec33449f3
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630565"
---
# <a name="integrate-media-capabilities"></a><span data-ttu-id="bc61b-104">Integrieren von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="bc61b-104">Integrate media capabilities</span></span> 

<span data-ttu-id="bc61b-105">In diesem Dokument erfahren Sie, wie Sie Medienfunktionen integrieren.</span><span class="sxs-lookup"><span data-stu-id="bc61b-105">This document guides you on how to integrate media capabilities.</span></span> <span data-ttu-id="bc61b-106">Bei dieser Integration werden die systemeigenen  Gerätefunktionen wie Kamera und Mikrofon mit der Teams kombiniert. </span><span class="sxs-lookup"><span data-stu-id="bc61b-106">This integration combines the native device capabilities, such as the **camera** and **microphone** with the Teams platform.</span></span>  

<span data-ttu-id="bc61b-107">Sie können das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die tools zur Verfügung stellt, die für Ihre App für den Zugriff auf die [Geräteberechtigungen](native-device-permissions.md)eines Benutzers erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="bc61b-107">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), that provides the tools necessary for your app to access a user’s [device permissions](native-device-permissions.md).</span></span> <span data-ttu-id="bc61b-108">Verwenden Sie geeignete Medienfunktions-APIs, um  die  systemeigenen Gerätefunktionen wie Kamera und Mikrofon in die Teams-Plattform in Ihrer Microsoft Teams mobilen App zu integrieren und eine reichhaltigere Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-108">Use suitable  media capability APIs to integrate the native device capabilities, such as the **camera** and **microphone** with the Teams platform within your Microsoft Teams mobile app, and build a richer experience.</span></span> 

## <a name="advantage-of-integrating-media-capabilities"></a><span data-ttu-id="bc61b-109">Vorteile der Integration von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="bc61b-109">Advantage of integrating media capabilities</span></span>

<span data-ttu-id="bc61b-110">Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Teams-Apps ist, dass sie systemeigene Teams verwendet, um Ihren Benutzern eine umfassende und immersive Benutzererfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="bc61b-110">The main advantage of integrating device capabilities in your Teams apps is it leverages native Teams controls to provide a rich and immersive experience to your users.</span></span>
<span data-ttu-id="bc61b-111">Zum Integrieren von Medienfunktionen müssen Sie die App-Manifestdatei aktualisieren und die APIs für Medienfunktionen aufrufen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-111">To integrate media capabilities you must update the app manifest file and call the media capability APIs.</span></span> 

<span data-ttu-id="bc61b-112">Für eine effektive Integration benötigen Sie [](#code-snippets) ein gutes Verständnis von Codeausschnitten zum Aufrufen der entsprechenden APIs, mit denen Sie systemeigene Medienfunktionen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bc61b-112">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the respective APIs, which allow you to use native media capabilities.</span></span>

<span data-ttu-id="bc61b-113">Es ist wichtig, sich [](#error-handling) mit den API-Antwortfehlern vertraut zu machen, um die Fehler in Ihrer app Teams behandeln.</span><span class="sxs-lookup"><span data-stu-id="bc61b-113">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="bc61b-114">Derzeit ist Microsoft Teams Medienfunktionen nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bc61b-114">Currently, Microsoft Teams support for media capabilities is only available for mobile clients.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="bc61b-115">Updatemanifest</span><span class="sxs-lookup"><span data-stu-id="bc61b-115">Update manifest</span></span>

<span data-ttu-id="bc61b-116">Aktualisieren Sie Teams [Appmanifest.jsdatei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die `devicePermissions` Eigenschaft hinzufügen und `media` angeben.</span><span class="sxs-lookup"><span data-stu-id="bc61b-116">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `media`.</span></span> <span data-ttu-id="bc61b-117">Sie ermöglicht es Ihrer App, die erforderlichen Berechtigungen  von Benutzern zu fordern, bevor sie mit der Kamera beginnen,  das Bild zu erfassen, den Katalog öffnen, um ein Bild auszuwählen, das als Anlage gesendet werden soll, oder das Mikrofon zum Aufzeichnen der Unterhaltung verwenden.</span><span class="sxs-lookup"><span data-stu-id="bc61b-117">It allows your app to ask for requisite permissions from users before they start using  the **camera** to capture the image, open the gallery to select an image to submit as an attachment, or use the **microphone** to record the conversation.</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="bc61b-118">Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="bc61b-118">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="bc61b-119">Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="bc61b-119">For more information, see [Request device permissions](native-device-permissions.md).</span></span>

## <a name="media-capability-apis"></a><span data-ttu-id="bc61b-120">APIs für Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="bc61b-120">Media capability APIs</span></span>

<span data-ttu-id="bc61b-121">Mit [den selectMedia-,](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) [getMedia-](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)und [viewImages-APIs](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) können Sie systemeigene Medienfunktionen wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="bc61b-121">The [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true), and [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) APIs enable you to use native media capabilities as follows:</span></span>

* <span data-ttu-id="bc61b-122">Verwenden Sie **das** systemeigene Mikrofon, um Benutzern das Aufzeichnen von **Audiodaten** (10 Minuten Unterhaltung) vom Gerät zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-122">Use the native **microphone** to allow users to **record audio** (record 10 minutes of conversation) from the device.</span></span>
* <span data-ttu-id="bc61b-123">Verwenden Sie das **systemeigene Kamerasteuerelement,** um Benutzern das **Erfassen und Anfügen von** Bildern unterwegs zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-123">Use native **camera control** to allow users to **capture and attach images** on the go.</span></span>
* <span data-ttu-id="bc61b-124">Verwenden Sie systemeigene **Katalogunterstützung,** um Benutzern die Auswahl von **Gerätebildern als** Anlagen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-124">Use native **gallery support** to allow users to **select device images** as attachments.</span></span>
* <span data-ttu-id="bc61b-125">Verwenden Sie **systemeigenes Bildanzeigesteuerelement,** um **eine Vorschau mehrerer Bilder** gleichzeitig anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-125">Use native **image viewer control** to **preview multiple images** at one time.</span></span>
* <span data-ttu-id="bc61b-126">Unterstützt **eine große Bildübertragung** (von 1 MB auf 50 MB) über die SDK-Brücke.</span><span class="sxs-lookup"><span data-stu-id="bc61b-126">Support **large image transfer** (from 1 MB to 50 MB) through the SDK bridge.</span></span>
* <span data-ttu-id="bc61b-127">Unterstützung **erweiterter Bildfunktionen,** mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:</span><span class="sxs-lookup"><span data-stu-id="bc61b-127">Support **advanced image capabilities** allowing users to preview and edit images:</span></span>
  * <span data-ttu-id="bc61b-128">Scannen Sie Dokument-, Whiteboard- und Visitenkarten über die Kamera.</span><span class="sxs-lookup"><span data-stu-id="bc61b-128">Scan document, whiteboard, and business cards  through the camera.</span></span>
  
> [!IMPORTANT]
> * <span data-ttu-id="bc61b-129">Die APIs , und können von mehreren Teams aufgerufen werden, z. B. Aufgabenmodule, Registerkarten `selectMedia` `getMedia` und persönliche `viewImages` Apps.</span><span class="sxs-lookup"><span data-stu-id="bc61b-129">The `selectMedia`, `getMedia`, and `viewImages` APIs can be invoked from multiple Teams surfaces, such as task modules, tabs, and personal apps.</span></span> <span data-ttu-id="bc61b-130">Weitere Informationen finden Sie unter [Einstiegspunkte für Teams Apps](../extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="bc61b-130">For more details, see [Entry points for Teams apps](../extensibility-points.md).</span></span>
> * <span data-ttu-id="bc61b-131">`selectMedia` Die API wurde erweitert, um Mikrofon- und Audioeigenschaften zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-131">`selectMedia` API has been extended to support microphone and audio properties.</span></span>

<span data-ttu-id="bc61b-132">Sie müssen die folgenden APIs verwenden, um die Medienfunktionen Ihres Geräts zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="bc61b-132">You must use the following set of APIs to enable your device's media capabilities:</span></span>

| <span data-ttu-id="bc61b-133">API</span><span class="sxs-lookup"><span data-stu-id="bc61b-133">API</span></span>      | <span data-ttu-id="bc61b-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bc61b-134">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="bc61b-135">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Camera)**</span><span class="sxs-lookup"><span data-stu-id="bc61b-135">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Camera)**</span></span>| <span data-ttu-id="bc61b-136">Mit dieser API können Benutzer **Medien** von der Gerätekamera erfassen oder auswählen und an die Web-App zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="bc61b-136">This API allows users to **capture or select media from the device camera** and return it to the web-app.</span></span> <span data-ttu-id="bc61b-137">Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder zeichnen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-137">The users can edit, crop, rotate, annotate, or draw over images before submission.</span></span> <span data-ttu-id="bc61b-138">Als Antwort auf `selectMedia` empfängt die Web-App die Medien-IDs ausgewählter Bilder und eine Miniaturansicht der ausgewählten Medien.</span><span class="sxs-lookup"><span data-stu-id="bc61b-138">In response to `selectMedia`, the web-app receives the media IDs of selected images and a thumbnail of the selected media.</span></span> <span data-ttu-id="bc61b-139">Diese API kann über die [ImageProps-Konfiguration weiter konfiguriert](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) werden.</span><span class="sxs-lookup"><span data-stu-id="bc61b-139">This API can be further configured through the [ImageProps](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) configuration.</span></span> |
| <span data-ttu-id="bc61b-140">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microphone**)</span><span class="sxs-lookup"><span data-stu-id="bc61b-140">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microphone**)</span></span>| <span data-ttu-id="bc61b-141">Legen Sie [mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) `4` in der API auf für den Zugriff auf `selectMedia` mikrofonfunktion.</span><span class="sxs-lookup"><span data-stu-id="bc61b-141">Set the [mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) to `4` in `selectMedia` API for accessing microphone  capability.</span></span> <span data-ttu-id="bc61b-142">Mit dieser API können Benutzer auch Audiodaten aus dem Gerätemikrofon aufzeichnen und aufgezeichnete Clips an die Web-App zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="bc61b-142">This API also allows users to record audio from the device microphone and return recorded clips to the web-app.</span></span> <span data-ttu-id="bc61b-143">Die Benutzer können die Aufzeichnungsvorschau vor der Übermittlung anhalten, erneut aufzeichnen und wiederverspielen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-143">The users can pause, re-record, and play recording preview before submission.</span></span> <span data-ttu-id="bc61b-144">Als Antwort auf **selectMedia** empfängt die Web-App Medien-IDs der ausgewählten Audioaufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="bc61b-144">In response to **selectMedia**, the web-app receives media IDs of the selected audio recording.</span></span> <br/> <span data-ttu-id="bc61b-145">Verwenden Sie , wenn Sie eine Dauer in Minuten für die `maxDuration` Aufzeichnung der Unterhaltung konfigurieren müssen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-145">Use `maxDuration`, if you require to configure a duration in minutes for recording the conversation.</span></span> <span data-ttu-id="bc61b-146">Die aktuelle Aufzeichnungsdauer beträgt 10 Minuten, nach der die Aufzeichnung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="bc61b-146">The current duration for recording is 10 minutes, after which the recording terminates.</span></span>  |
| [<span data-ttu-id="bc61b-147">**getMedia**</span><span class="sxs-lookup"><span data-stu-id="bc61b-147">**getMedia**</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| <span data-ttu-id="bc61b-148">Diese API ruft die von der API erfassten Medien unabhängig von der Mediengröße `selectMedia` in Blöcken ab.</span><span class="sxs-lookup"><span data-stu-id="bc61b-148">This API retrieves the media captured by `selectMedia` API in chunks, irrespective of the media size.</span></span> <span data-ttu-id="bc61b-149">Diese Blöcke werden zusammengesetzt und als Datei oder Blob an die Web-App gesendet.</span><span class="sxs-lookup"><span data-stu-id="bc61b-149">These chunks are assembled and sent back to the web app as a file or blob.</span></span> <span data-ttu-id="bc61b-150">Das Aufbrechen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien.</span><span class="sxs-lookup"><span data-stu-id="bc61b-150">Breaking of media into smaller chunks facilitates large file transfer.</span></span> |
| [<span data-ttu-id="bc61b-151">**viewImages**</span><span class="sxs-lookup"><span data-stu-id="bc61b-151">**viewImages**</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| <span data-ttu-id="bc61b-152">Mit dieser API kann der Benutzer Bilder im Vollbildmodus als bildlauffähige Liste anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bc61b-152">This API enables the user to view images in  full-screen mode as a scrollable list.</span></span>|


<span data-ttu-id="bc61b-153">**Web-App-Erfahrung für selectMedia-API für Bildfunktionen** 
 ![ Gerätekamera und Bilderfahrung in Teams](../../assets/images/tabs/image-capability.png)</span><span class="sxs-lookup"><span data-stu-id="bc61b-153">**Web app experience for selectMedia API for image capability**
![device camera and image experience in Teams](../../assets/images/tabs/image-capability.png)</span></span>

<span data-ttu-id="bc61b-154">**Web-App-Erfahrung für selectMedia-API für Mikrofonfunktion** 
 ![ Web-App-Erfahrung für Mikrofonfunktionen](../../assets/images/tabs/microphone-capability.png)</span><span class="sxs-lookup"><span data-stu-id="bc61b-154">**Web app experience for selectMedia API for microphone capability**
![web app experience for microphone capability](../../assets/images/tabs/microphone-capability.png)</span></span>

## <a name="error-handling"></a><span data-ttu-id="bc61b-155">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="bc61b-155">Error handling</span></span>

<span data-ttu-id="bc61b-156">Sie müssen sicherstellen, dass diese Fehler in Ihrer App Teams werden.</span><span class="sxs-lookup"><span data-stu-id="bc61b-156">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="bc61b-157">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="bc61b-157">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 


|<span data-ttu-id="bc61b-158">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="bc61b-158">Error code</span></span> |  <span data-ttu-id="bc61b-159">Fehlername</span><span class="sxs-lookup"><span data-stu-id="bc61b-159">Error name</span></span>     | <span data-ttu-id="bc61b-160">Bedingung</span><span class="sxs-lookup"><span data-stu-id="bc61b-160">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="bc61b-161">**100**</span><span class="sxs-lookup"><span data-stu-id="bc61b-161">**100**</span></span> | <span data-ttu-id="bc61b-162">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="bc61b-162">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="bc61b-163">DIE API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bc61b-163">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="bc61b-164">**404**</span><span class="sxs-lookup"><span data-stu-id="bc61b-164">**404**</span></span> | <span data-ttu-id="bc61b-165">FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="bc61b-165">FILE_NOT_FOUND</span></span> | <span data-ttu-id="bc61b-166">Die angegebene Datei wird am angegebenen Speicherort nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="bc61b-166">File specified is not found in the given location.</span></span>|
| <span data-ttu-id="bc61b-167">**500**</span><span class="sxs-lookup"><span data-stu-id="bc61b-167">**500**</span></span> | <span data-ttu-id="bc61b-168">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="bc61b-168">INTERNAL_ERROR</span></span> | <span data-ttu-id="bc61b-169">Interner Fehler beim Ausführen des erforderlichen Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="bc61b-169">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="bc61b-170">**1000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-170">**1000**</span></span> | <span data-ttu-id="bc61b-171">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="bc61b-171">PERMISSION_DENIED</span></span> |<span data-ttu-id="bc61b-172">Die Berechtigung wird vom Benutzer verweigert.</span><span class="sxs-lookup"><span data-stu-id="bc61b-172">Permission is denied by the user.</span></span>|
| <span data-ttu-id="bc61b-173">**2000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-173">**2000**</span></span> |<span data-ttu-id="bc61b-174">NETWORK_ERROR</span><span class="sxs-lookup"><span data-stu-id="bc61b-174">NETWORK_ERROR</span></span> | <span data-ttu-id="bc61b-175">Netzwerkproblem.</span><span class="sxs-lookup"><span data-stu-id="bc61b-175">Network issue.</span></span>|
| <span data-ttu-id="bc61b-176">**3000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-176">**3000**</span></span> | <span data-ttu-id="bc61b-177">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="bc61b-177">NO_HW_SUPPORT</span></span> | <span data-ttu-id="bc61b-178">Die zugrunde liegende Hardware unterstützt die Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="bc61b-178">Underlying hardware does not support the capability.</span></span>|
| <span data-ttu-id="bc61b-179">**4000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-179">**4000**</span></span>| <span data-ttu-id="bc61b-180">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="bc61b-180">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="bc61b-181">Mindestens ein Argument ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="bc61b-181">One or more arguments are invalid.</span></span>|
| <span data-ttu-id="bc61b-182">**5000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-182">**5000**</span></span> | <span data-ttu-id="bc61b-183">UNAUTHORIZED_USER_OPERATION</span><span class="sxs-lookup"><span data-stu-id="bc61b-183">UNAUTHORIZED_USER_OPERATION</span></span> | <span data-ttu-id="bc61b-184">Der Benutzer ist nicht zum Abschließen dieses Vorgangs autorisiert.</span><span class="sxs-lookup"><span data-stu-id="bc61b-184">User is not authorized to complete this operation.</span></span>|
| <span data-ttu-id="bc61b-185">**6000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-185">**6000**</span></span> |<span data-ttu-id="bc61b-186">INSUFFICIENT_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="bc61b-186">INSUFFICIENT_RESOURCES</span></span> | <span data-ttu-id="bc61b-187">Der Vorgang konnte aufgrund unzureichender Ressourcen nicht abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="bc61b-187">Operation could not be completed due to insufficient resources.</span></span>|
|<span data-ttu-id="bc61b-188">**7000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-188">**7000**</span></span> | <span data-ttu-id="bc61b-189">THROTTLE</span><span class="sxs-lookup"><span data-stu-id="bc61b-189">THROTTLE</span></span> | <span data-ttu-id="bc61b-190">Die Plattform hat die Anforderung gedrosselt, da die API häufig aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="bc61b-190">Platform throttled the request as the API was invoked frequently.</span></span>|
|  <span data-ttu-id="bc61b-191">**8000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-191">**8000**</span></span> | <span data-ttu-id="bc61b-192">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="bc61b-192">USER_ABORT</span></span> |<span data-ttu-id="bc61b-193">Der Benutzer bricht den Vorgang ab.</span><span class="sxs-lookup"><span data-stu-id="bc61b-193">User aborts the operation.</span></span>|
| <span data-ttu-id="bc61b-194">**9000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-194">**9000**</span></span>| <span data-ttu-id="bc61b-195">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="bc61b-195">OLD_PLATFORM</span></span> | <span data-ttu-id="bc61b-196">Plattformcode ist veraltet und implementiert diese API nicht.</span><span class="sxs-lookup"><span data-stu-id="bc61b-196">Platform code is outdated and does not implement this API.</span></span>|
| <span data-ttu-id="bc61b-197">**10000**</span><span class="sxs-lookup"><span data-stu-id="bc61b-197">**10000**</span></span>| <span data-ttu-id="bc61b-198">SIZE_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="bc61b-198">SIZE_EXCEEDED</span></span> |  <span data-ttu-id="bc61b-199">Der Rückgabewert ist zu groß und hat die Grenzen der Plattformgröße überschritten.</span><span class="sxs-lookup"><span data-stu-id="bc61b-199">Return value is too big and has exceeded the platform size boundaries.</span></span>|

## <a name="code-snippets"></a><span data-ttu-id="bc61b-200">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="bc61b-200">Code snippets</span></span>

<span data-ttu-id="bc61b-201">**Aufrufen `selectMedia` API** zum Aufzeichnen von Bildern mit der Kamera:</span><span class="sxs-lookup"><span data-stu-id="bc61b-201">**Calling `selectMedia` API** for capturing images using camera:</span></span>

```javascript
let imageProp: microsoftTeams.media.ImageProps = {
    sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
    startMode: microsoftTeams.media.CameraStartMode.Photo,
    ink: false,
    cameraSwitcher: false,
    textSticker: false,
    enableFilter: true,
};
let mediaInput: microsoftTeams.media.MediaInputs = {
    mediaType: microsoftTeams.media.MediaType.Image,
    maxMediaCount: 10,
    imageProps: imageProp
};
microsoftTeams.media.selectMedia(mediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
    if (attachments) {
        let y = attachments[0];
        img.src = ("data:" + y.mimeType + ";base64," + y.preview);
    }
});
```

<span data-ttu-id="bc61b-202">**Aufrufen `getMedia` API** zum Abrufen großer Medien in Blöcken:</span><span class="sxs-lookup"><span data-stu-id="bc61b-202">**Calling `getMedia` API** to retrieve large media in chunks:</span></span>

```javascript
let media: microsoftTeams.media.Media = attachments[0]
media.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
    if (blob) {
        if (blob.type.includes("image")) {
            img.src = (URL.createObjectURL(blob));
        }
    }
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
});
```

<span data-ttu-id="bc61b-203">**Aufrufen `viewImages` API nach ID, die von der `selectMedia` API zurückgegeben wird:**</span><span class="sxs-lookup"><span data-stu-id="bc61b-203">**Calling `viewImages` API by ID returned by `selectMedia` API**:</span></span>

```javascript
// View images by id:
// Assumption: attachmentArray = select Media API Output
let uriList = [];
if (attachmentArray && attachmentArray.length > 0) {
    for (let i = 0; i < attachmentArray.length; i++) {
        let file = attachmentArray[i];
        if (file.mimeType.includes("image")) {
            let imageUri = {
                value: file.content,
                type: 1,
            }
            uriList.push(imageUri);
        } else {
            alert("File type is not image");
        }
    }
}
if (uriList.length > 0) {
    microsoftTeams.media.viewImages(uriList, (error: microsoftTeams.SdkError) => {
        if (error) {
            if (error.message) {
                output(" ErrorCode: " + error.errorCode + error.message);
            } else {
                output(" ErrorCode: " + error.errorCode);
            }
        }
    });
} else {
    output("Url list is empty");
}
```

<span data-ttu-id="bc61b-204">**Aufrufen `viewImages` API nach URL**:</span><span class="sxs-lookup"><span data-stu-id="bc61b-204">**Calling `viewImages` API by URL**:</span></span>

```javascript
// View Images by URL:
// Assumption 2 urls, url1 and url2
let uriList = [];
if (URL1 != null && URL1.length > 0) {
    let imageUri = {
        value: URL1,
        type: 2,
    }
    uriList.push(imageUri);
}
if (URL2 != null && URL2.length > 0) {
    let imageUri = {
        value: URL2,
        type: 2,
    }
    uriList.push(imageUri);
}
if (uriList.length > 0) {
    microsoftTeams.media.viewImages(uriList, (error: microsoftTeams.SdkError) => {
        if (error) {
            if (error.message) {
                output(" ErrorCode: " + error.errorCode + error.message);
            } else {
                output(" ErrorCode: " + error.errorCode);
            }
        }
    });
} else {
    output("Url list is empty");
}
```

<span data-ttu-id="bc61b-205">**Anrufe `selectMedia` und `getMedia` APIs zum Aufzeichnen von Audio über Mikrofon**:</span><span class="sxs-lookup"><span data-stu-id="bc61b-205">**Calling `selectMedia` and `getMedia` APIs for recording audio through microphone**:</span></span>

```javascript
let mediaInput: microsoftTeams.media.MediaInputs = {
    mediaType: microsoftTeams.media.MediaType.Audio,
    maxMediaCount: 1,
};
microsoftTeams.media.selectMedia(mediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
    // If you want to directly use the audio file (for smaller file sizes (~4MB))    if (attachments) {
    let audioResult = attachments[0];
    var videoElement = document.createElement("video");
    videoElement.setAttribute("src", ("data:" + y.mimeType + ";base64," + y.preview));
    //To use the audio file via get Media API for bigger audio file sizes greater than 4MB        audioResult.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
    if (blob) {
        if (blob.type.includes("video")) {
            videoElement.setAttribute("src", URL.createObjectURL(blob));
        }
    }
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
});
```

## <a name="see-also"></a><span data-ttu-id="bc61b-206">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="bc61b-206">See also</span></span>

* [<span data-ttu-id="bc61b-207">Integrieren von QR- oder Barcodescannerfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="bc61b-207">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
* [<span data-ttu-id="bc61b-208">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="bc61b-208">Integrate location capabilities in Teams</span></span>](location-capability.md)
