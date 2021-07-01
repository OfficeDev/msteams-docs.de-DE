---
title: Integrieren von Medienfunktionen
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK, um Medienfunktionen zu aktivieren
keywords: Systemeigene Geräteberechtigungsmedien für Kamerabildmikrofonfunktionen
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 22d4a791e83cf36f18b75a3846865835b0ee024f
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211625"
---
# <a name="integrate-media-capabilities"></a><span data-ttu-id="c93d5-104">Integrieren von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="c93d5-104">Integrate media capabilities</span></span> 

<span data-ttu-id="c93d5-105">Sie können systemeigene Gerätefunktionen wie **Kamera** und **Mikrofon** in Ihre Teams-App integrieren.</span><span class="sxs-lookup"><span data-stu-id="c93d5-105">You can integrate native device capabilities, such as the **camera** and **microphone** with your Teams app.</span></span> <span data-ttu-id="c93d5-106">Zur Integration können Sie [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die Tools bereitstellt, die Ihre App für den Zugriff auf [die Geräteberechtigungen](native-device-permissions.md)eines Benutzers benötigt.</span><span class="sxs-lookup"><span data-stu-id="c93d5-106">For integration, you can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), that provides the tools necessary for your app to access a user’s [device permissions](native-device-permissions.md).</span></span> <span data-ttu-id="c93d5-107">Verwenden Sie geeignete Medienfunktions-APIs, um die Gerätefunktionen wie **Kamera** und **Mikrofon** in die Teams-Plattform in Ihre Microsoft Teams mobile App zu integrieren und eine umfassendere Umgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-107">Use suitable media capability APIs to integrate the device capabilities, such as **camera** and **microphone** with the Teams platform within your Microsoft Teams mobile app, and build a richer experience.</span></span> 

## <a name="advantage-of-integrating-media-capabilities"></a><span data-ttu-id="c93d5-108">Vorteile der Integration von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="c93d5-108">Advantage of integrating media capabilities</span></span>

<span data-ttu-id="c93d5-109">Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Teams-Apps besteht darin, dass systemeigene Teams-Steuerelemente genutzt werden, um Ihren Benutzern eine umfassende und immersive Erfahrung zu bieten.</span><span class="sxs-lookup"><span data-stu-id="c93d5-109">The main advantage of integrating device capabilities in your Teams apps is it leverages native Teams controls to provide a rich and immersive experience to your users.</span></span>
<span data-ttu-id="c93d5-110">Um Medienfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die Medienfunktions-APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-110">To integrate media capabilities you must update the app manifest file and call the media capability APIs.</span></span> 

<span data-ttu-id="c93d5-111">Für eine effektive Integration müssen Sie über ein gutes Verständnis von [Codeausschnitten](#code-snippets) für den Aufruf der entsprechenden APIs verfügen, mit denen Sie systemeigene Medienfunktionen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c93d5-111">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the respective APIs, which allow you to use native media capabilities.</span></span>

<span data-ttu-id="c93d5-112">Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="c93d5-112">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> * <span data-ttu-id="c93d5-113">Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c93d5-113">Currently, Microsoft Teams support for media capabilities is available for mobile clients only.</span></span>   
> * <span data-ttu-id="c93d5-114">Derzeit unterstützt Teams keine Geräteberechtigungen für Apps mit mehreren Fenstern, Registerkarten und das Besprechungs-Sidepanel.</span><span class="sxs-lookup"><span data-stu-id="c93d5-114">Currently, Teams does not support device permissions for multi window apps, tabs, and the meeting sidepanel.</span></span>    

## <a name="update-manifest"></a><span data-ttu-id="c93d5-115">Updatemanifest</span><span class="sxs-lookup"><span data-stu-id="c93d5-115">Update manifest</span></span>

<span data-ttu-id="c93d5-116">Aktualisieren Sie die Teams [App-manifest.jsauf](../../resources/schema/manifest-schema.md#devicepermissions) der Datei, indem Sie die Eigenschaft hinzufügen `devicePermissions` und `media` angeben.</span><span class="sxs-lookup"><span data-stu-id="c93d5-116">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `media`.</span></span> <span data-ttu-id="c93d5-117">Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Aufnahme des Bilds mit der **Kamera** beginnen, den Katalog öffnen, um ein Bild auszuwählen, das als Anlage übermittelt werden soll, oder das **Mikrofon** verwenden, um die Unterhaltung aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-117">It allows your app to ask for requisite permissions from users before they start using  the **camera** to capture the image, open the gallery to select an image to submit as an attachment, or use the **microphone** to record the conversation.</span></span> <span data-ttu-id="c93d5-118">Das Update für das App-Manifest lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c93d5-118">The update for app manifest is as follows:</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="c93d5-119">Die Eingabeaufforderung **"Berechtigungen anfordern"** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="c93d5-119">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="c93d5-120">Weitere Informationen finden Sie unter Anfordern von [Geräteberechtigungen.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="c93d5-120">For more information, see [Request device permissions](native-device-permissions.md).</span></span>

## <a name="media-capability-apis"></a><span data-ttu-id="c93d5-121">APIs für Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="c93d5-121">Media capability APIs</span></span>

<span data-ttu-id="c93d5-122">Mit den [APIs selectMedia,](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)und [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) können Sie systemeigene Medienfunktionen wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="c93d5-122">The [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true), and [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) APIs enable you to use native media capabilities as follows:</span></span>

* <span data-ttu-id="c93d5-123">Verwenden Sie das systemeigene **Mikrofon,** um Benutzern das Aufzeichnen von **Audiodaten** (Aufzeichnung von 10 Minuten Unterhaltung) vom Gerät aus zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-123">Use the native **microphone** to allow users to **record audio** (record 10 minutes of conversation) from the device.</span></span>
* <span data-ttu-id="c93d5-124">Verwenden Sie das systemeigene **Kamerasteuerelement,** damit Benutzer **unterwegs Bilder erfassen und anfügen** können.</span><span class="sxs-lookup"><span data-stu-id="c93d5-124">Use native **camera control** to allow users to **capture and attach images** on the go.</span></span>
* <span data-ttu-id="c93d5-125">Verwenden Sie die **native Katalogunterstützung,** damit Benutzer **Gerätebilder** als Anlagen auswählen können.</span><span class="sxs-lookup"><span data-stu-id="c93d5-125">Use native **gallery support** to allow users to **select device images** as attachments.</span></span>
* <span data-ttu-id="c93d5-126">Verwenden Sie das systemeigene **Bildanzeige-Steuerelement,** um **mehrere Bilder** gleichzeitig in der Vorschau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-126">Use native **image viewer control** to **preview multiple images** at one time.</span></span>
* <span data-ttu-id="c93d5-127">Unterstützt **große Bildübertragung** (von 1 MB bis 50 MB) über die SDK-Brücke.</span><span class="sxs-lookup"><span data-stu-id="c93d5-127">Support **large image transfer** (from 1 MB to 50 MB) through the SDK bridge.</span></span>
* <span data-ttu-id="c93d5-128">Unterstützung **erweiterter Bildfunktionen,** mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:</span><span class="sxs-lookup"><span data-stu-id="c93d5-128">Support **advanced image capabilities** allowing users to preview and edit images:</span></span>
  * <span data-ttu-id="c93d5-129">Scannen Sie Dokumente, Whiteboards und Visitenkarten über die Kamera.</span><span class="sxs-lookup"><span data-stu-id="c93d5-129">Scan document, whiteboard, and business cards  through the camera.</span></span>
  
> [!IMPORTANT]
> * <span data-ttu-id="c93d5-130">Die `selectMedia` , `getMedia` und `viewImages` APIs können von mehreren Teams Oberflächen aufgerufen werden, z. B. Aufgabenmodule, Registerkarten und persönliche Apps.</span><span class="sxs-lookup"><span data-stu-id="c93d5-130">The `selectMedia`, `getMedia`, and `viewImages` APIs can be invoked from multiple Teams surfaces, such as task modules, tabs, and personal apps.</span></span> <span data-ttu-id="c93d5-131">Weitere Informationen finden Sie unter [Einstiegspunkte für Teams Apps.](../extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="c93d5-131">For more details, see [Entry points for Teams apps](../extensibility-points.md).</span></span>
> * <span data-ttu-id="c93d5-132">`selectMedia` Die API wurde erweitert, um Mikrofon- und Audioeigenschaften zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-132">`selectMedia` API has been extended to support microphone and audio properties.</span></span>

<span data-ttu-id="c93d5-133">Sie müssen die folgenden APIs verwenden, um die Medienfunktionen Ihres Geräts zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="c93d5-133">You must use the following set of APIs to enable your device's media capabilities:</span></span>

| <span data-ttu-id="c93d5-134">API</span><span class="sxs-lookup"><span data-stu-id="c93d5-134">API</span></span>      | <span data-ttu-id="c93d5-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c93d5-135">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="c93d5-136">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Kamera)**</span><span class="sxs-lookup"><span data-stu-id="c93d5-136">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Camera)**</span></span>| <span data-ttu-id="c93d5-137">Mit dieser API können Benutzer **Medien aus der Gerätekamera erfassen oder auswählen** und an die Web-App zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c93d5-137">This API allows users to **capture or select media from the device camera** and return it to the web-app.</span></span> <span data-ttu-id="c93d5-138">Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder zeichnen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-138">The users can edit, crop, rotate, annotate, or draw over images before submission.</span></span> <span data-ttu-id="c93d5-139">Als Reaktion darauf `selectMedia` empfängt die Web-App die Medien-IDs ausgewählter Bilder und eine Miniaturansicht der ausgewählten Medien.</span><span class="sxs-lookup"><span data-stu-id="c93d5-139">In response to `selectMedia`, the web-app receives the media IDs of selected images and a thumbnail of the selected media.</span></span> <span data-ttu-id="c93d5-140">Diese API kann über die [ImageProps-Konfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) weiter konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="c93d5-140">This API can be further configured through the [ImageProps](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) configuration.</span></span> |
| <span data-ttu-id="c93d5-141">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Mikrofon**)</span><span class="sxs-lookup"><span data-stu-id="c93d5-141">[**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Microphone**)</span></span>| <span data-ttu-id="c93d5-142">Legen Sie ["mediaType"](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) `4` auf "in `selectMedia` API" fest, um auf die Mikrofonfunktion zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-142">Set the [mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) to `4` in `selectMedia` API for accessing microphone  capability.</span></span> <span data-ttu-id="c93d5-143">Diese API ermöglicht es Benutzern auch, Audiodaten vom Gerätemikrofon aufzuzeichnen und aufgezeichnete Clips an die Web-App zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="c93d5-143">This API also allows users to record audio from the device microphone and return recorded clips to the web-app.</span></span> <span data-ttu-id="c93d5-144">Die Benutzer können vor der Übermittlung anhalten, erneut aufzeichnen und die Aufzeichnungsvorschau wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="c93d5-144">The users can pause, re-record, and play recording preview before submission.</span></span> <span data-ttu-id="c93d5-145">Als Reaktion auf **selectMedia** empfängt die Web-App Medien-IDs der ausgewählten Audioaufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="c93d5-145">In response to **selectMedia**, the web-app receives media IDs of the selected audio recording.</span></span> <br/> <span data-ttu-id="c93d5-146">Verwenden Sie `maxDuration` dies, wenn Sie eine Dauer in Minuten für die Aufzeichnung der Unterhaltung konfigurieren müssen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-146">Use `maxDuration`, if you require to configure a duration in minutes for recording the conversation.</span></span> <span data-ttu-id="c93d5-147">Die aktuelle Aufzeichnungsdauer beträgt 10 Minuten, danach wird die Aufzeichnung beendet.</span><span class="sxs-lookup"><span data-stu-id="c93d5-147">The current duration for recording is 10 minutes, after which the recording terminates.</span></span>  |
| [<span data-ttu-id="c93d5-148">**getMedia**</span><span class="sxs-lookup"><span data-stu-id="c93d5-148">**getMedia**</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| <span data-ttu-id="c93d5-149">Diese API ruft die von der API erfassten Medien `selectMedia` in Blöcken ab, unabhängig von der Mediengröße.</span><span class="sxs-lookup"><span data-stu-id="c93d5-149">This API retrieves the media captured by `selectMedia` API in chunks, irrespective of the media size.</span></span> <span data-ttu-id="c93d5-150">Diese Blöcke werden zusammengestellt und als Datei oder Blob an die Web-App zurückgesendet.</span><span class="sxs-lookup"><span data-stu-id="c93d5-150">These chunks are assembled and sent back to the web app as a file or blob.</span></span> <span data-ttu-id="c93d5-151">Das Unterteilen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien.</span><span class="sxs-lookup"><span data-stu-id="c93d5-151">Breaking of media into smaller chunks facilitates large file transfer.</span></span> |
| [<span data-ttu-id="c93d5-152">**viewImages**</span><span class="sxs-lookup"><span data-stu-id="c93d5-152">**viewImages**</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| <span data-ttu-id="c93d5-153">Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c93d5-153">This API enables the user to view images in  full-screen mode as a scrollable list.</span></span>|

<span data-ttu-id="c93d5-154">Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für bildfunktion:</span><span class="sxs-lookup"><span data-stu-id="c93d5-154">The following image depicts web app experience of `selectMedia` API for image capability:</span></span>

![Kamera- und Bilderfahrung des Geräts in Teams](../../assets/images/tabs/image-capability.png)

<span data-ttu-id="c93d5-156">Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für Mikrofonfunktion:</span><span class="sxs-lookup"><span data-stu-id="c93d5-156">The following image depicts web app experience of `selectMedia` API for microphone capability:</span></span>

![Web-App-Erfahrung für Mikrofonfunktion](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a><span data-ttu-id="c93d5-158">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="c93d5-158">Error handling</span></span>

<span data-ttu-id="c93d5-159">Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams App ordnungsgemäß behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="c93d5-159">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="c93d5-160">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="c93d5-160">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="c93d5-161">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="c93d5-161">Error code</span></span> |  <span data-ttu-id="c93d5-162">Fehlername</span><span class="sxs-lookup"><span data-stu-id="c93d5-162">Error name</span></span>     | <span data-ttu-id="c93d5-163">Bedingung</span><span class="sxs-lookup"><span data-stu-id="c93d5-163">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="c93d5-164">**100**</span><span class="sxs-lookup"><span data-stu-id="c93d5-164">**100**</span></span> | <span data-ttu-id="c93d5-165">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="c93d5-165">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="c93d5-166">Die API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c93d5-166">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="c93d5-167">**404**</span><span class="sxs-lookup"><span data-stu-id="c93d5-167">**404**</span></span> | <span data-ttu-id="c93d5-168">FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="c93d5-168">FILE_NOT_FOUND</span></span> | <span data-ttu-id="c93d5-169">Die angegebene Datei wurde am angegebenen Speicherort nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="c93d5-169">File specified is not found in the given location.</span></span>|
| <span data-ttu-id="c93d5-170">**500**</span><span class="sxs-lookup"><span data-stu-id="c93d5-170">**500**</span></span> | <span data-ttu-id="c93d5-171">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="c93d5-171">INTERNAL_ERROR</span></span> | <span data-ttu-id="c93d5-172">Beim Ausführen des erforderlichen Vorgangs ist ein interner Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="c93d5-172">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="c93d5-173">**1000**</span><span class="sxs-lookup"><span data-stu-id="c93d5-173">**1000**</span></span> | <span data-ttu-id="c93d5-174">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="c93d5-174">PERMISSION_DENIED</span></span> |<span data-ttu-id="c93d5-175">Der Benutzer verweigert die Berechtigung.</span><span class="sxs-lookup"><span data-stu-id="c93d5-175">Permission is denied by the user.</span></span>|
| <span data-ttu-id="c93d5-176">**3000**</span><span class="sxs-lookup"><span data-stu-id="c93d5-176">**3000**</span></span> | <span data-ttu-id="c93d5-177">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="c93d5-177">NO_HW_SUPPORT</span></span> | <span data-ttu-id="c93d5-178">Die zugrunde liegende Hardware unterstützt die Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="c93d5-178">Underlying hardware does not support the capability.</span></span>|
| <span data-ttu-id="c93d5-179">**4000**</span><span class="sxs-lookup"><span data-stu-id="c93d5-179">**4000**</span></span>| <span data-ttu-id="c93d5-180">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="c93d5-180">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="c93d5-181">Mindestens ein Argument ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="c93d5-181">One or more arguments are invalid.</span></span>|
|  <span data-ttu-id="c93d5-182">**8000**</span><span class="sxs-lookup"><span data-stu-id="c93d5-182">**8000**</span></span> | <span data-ttu-id="c93d5-183">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="c93d5-183">USER_ABORT</span></span> |<span data-ttu-id="c93d5-184">Der Benutzer abgebrochen den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="c93d5-184">User aborts the operation.</span></span>|
| <span data-ttu-id="c93d5-185">**9000**</span><span class="sxs-lookup"><span data-stu-id="c93d5-185">**9000**</span></span>| <span data-ttu-id="c93d5-186">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="c93d5-186">OLD_PLATFORM</span></span> | <span data-ttu-id="c93d5-187">Plattformcode ist veraltet und implementiert diese API nicht.</span><span class="sxs-lookup"><span data-stu-id="c93d5-187">Platform code is outdated and does not implement this API.</span></span>|
| <span data-ttu-id="c93d5-188">**10000**</span><span class="sxs-lookup"><span data-stu-id="c93d5-188">**10000**</span></span>| <span data-ttu-id="c93d5-189">SIZE_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="c93d5-189">SIZE_EXCEEDED</span></span> |  <span data-ttu-id="c93d5-190">Der Rückgabewert ist zu groß und hat die Grenzen der Plattformgröße überschritten.</span><span class="sxs-lookup"><span data-stu-id="c93d5-190">Return value is too big and has exceeded the platform size boundaries.</span></span>|

## <a name="code-snippets"></a><span data-ttu-id="c93d5-191">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="c93d5-191">Code snippets</span></span>

<span data-ttu-id="c93d5-192">**Anrufe `selectMedia` API** zum Aufnehmen von Bildern mithilfe der Kamera:</span><span class="sxs-lookup"><span data-stu-id="c93d5-192">**Calling `selectMedia` API** for capturing images using camera:</span></span>

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

<span data-ttu-id="c93d5-193">**Anrufe `getMedia` API** zum Abrufen großer Medien in Blöcken:</span><span class="sxs-lookup"><span data-stu-id="c93d5-193">**Calling `getMedia` API** to retrieve large media in chunks:</span></span>

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

<span data-ttu-id="c93d5-194">**Anrufe `viewImages` API nach ID, die von `selectMedia` der API zurückgegeben wird:**</span><span class="sxs-lookup"><span data-stu-id="c93d5-194">**Calling `viewImages` API by ID returned by `selectMedia` API**:</span></span>

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

<span data-ttu-id="c93d5-195">**Anrufe `viewImages` API nach URL:**</span><span class="sxs-lookup"><span data-stu-id="c93d5-195">**Calling `viewImages` API by URL**:</span></span>

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

<span data-ttu-id="c93d5-196">**Anrufe `selectMedia` und `getMedia` APIs zum Aufzeichnen von Audio über das Mikrofon:**</span><span class="sxs-lookup"><span data-stu-id="c93d5-196">**Calling `selectMedia` and `getMedia` APIs for recording audio through microphone**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c93d5-197">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c93d5-197">See also</span></span>

* [<span data-ttu-id="c93d5-198">Integrieren von QR- oder Strichcodescannern in Teams</span><span class="sxs-lookup"><span data-stu-id="c93d5-198">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
* [<span data-ttu-id="c93d5-199">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="c93d5-199">Integrate location capabilities in Teams</span></span>](location-capability.md)
* [<span data-ttu-id="c93d5-200">Integrieren der Personenauswahlfunktion in Teams</span><span class="sxs-lookup"><span data-stu-id="c93d5-200">Integrate People Picker capability in Teams</span></span>](people-picker-capability.md)

