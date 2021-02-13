---
title: Integrieren von Medienfunktionen
description: Verwenden des JavaScript-Client-SDK für Teams zum Aktivieren von Medienfunktionen
keywords: Kamerabildmikrofonfunktionen systemeigene Geräteberechtigungsmedien
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4126551858116343689e08c4b4f385eb0bbc7ed1
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231595"
---
# <a name="integrate-media-capabilities"></a><span data-ttu-id="eabab-104">Integrieren von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="eabab-104">Integrate media capabilities</span></span> 

<span data-ttu-id="eabab-105">In diesem Dokument erfahren Sie, wie Sie Medienfunktionen integrieren.</span><span class="sxs-lookup"><span data-stu-id="eabab-105">This document guides you on how to integrate media capabilities.</span></span> <span data-ttu-id="eabab-106">Diese Integration kombiniert die systemeigenen Gerätefunktionen, z. B. die **Kamera** und **das Mikrofon,** mit der Teams-Plattform.</span><span class="sxs-lookup"><span data-stu-id="eabab-106">This integration combines the native device capabilities, such as the **camera** and **microphone** with the Teams platform.</span></span>  

<span data-ttu-id="eabab-107">Sie können das [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)von Microsoft Teams verwenden, das die Tools zur Verfügung stellt, die Für Ihre App für den Zugriff auf die Geräteberechtigungen eines [Benutzers erforderlich sind.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="eabab-107">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), that provides the tools necessary for your app to access a user’s [device permissions](native-device-permissions.md).</span></span> <span data-ttu-id="eabab-108">Verwenden Sie geeignete **APIs** für Medienfunktionen, um  die  systemeigenen Gerätefunktionen wie Kamera und Mikrofon in die Microsoft Teams-Plattform in Ihre mobile Microsoft Teams-App zu integrieren und eine reichhaltigere Erfahrung zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="eabab-108">Use suitable  **media capability APIs** to integrate the native device capabilities, such as the **camera** and **microphone** with the Teams platform within your Microsoft Teams mobile app, and build a richer experience.</span></span> 

## <a name="advantage-of-integrating-media-capabilities"></a><span data-ttu-id="eabab-109">Vorteile der Integration von Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="eabab-109">Advantage of integrating media capabilities</span></span>

<span data-ttu-id="eabab-110">Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Teams-Apps besteht in der Nutzung systemeigener Teams-Steuerelemente, um Ihren Benutzern ein umfassendes und immersives Erlebnis zu bieten.</span><span class="sxs-lookup"><span data-stu-id="eabab-110">The main advantage of integrating device capabilities in your Teams apps is it leverages native Teams controls to provide a rich and immersive experience to your users.</span></span>
<span data-ttu-id="eabab-111">Um Medienfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die APIs für die Medienfunktion aufrufen.</span><span class="sxs-lookup"><span data-stu-id="eabab-111">To integrate media capabilities you must update the app manifest file and call the media capability APIs.</span></span> 

<span data-ttu-id="eabab-112">Für eine effektive Integration benötigen Sie [](#code-snippets) ein gutes Verständnis der Codeausschnitte für den Aufruf der entsprechenden APIs, mit denen Sie systemeigene Medienfunktionen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="eabab-112">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the respective APIs, which allow you to use native media capabilities.</span></span>

<span data-ttu-id="eabab-113">Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="eabab-113">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="eabab-114">Derzeit ist die Unterstützung von Medienfunktionen von Microsoft Teams nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="eabab-114">Currently, Microsoft Teams support for media capabilities is only available for mobile clients.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="eabab-115">Manifest aktualisieren</span><span class="sxs-lookup"><span data-stu-id="eabab-115">Update manifest</span></span>

<span data-ttu-id="eabab-116">Aktualisieren Sie Ihre [ Teams-manifest.jsdatei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die Eigenschaft hinzufügen `devicePermissions` und `media` angeben.</span><span class="sxs-lookup"><span data-stu-id="eabab-116">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `media`.</span></span> <span data-ttu-id="eabab-117">Damit kann Ihre App die erforderlichen Berechtigungen von  Benutzern einsenden, bevor sie mit der Kamera zum Aufnehmen des  Bilds beginnen, den Katalog öffnen, um ein Bild auszuwählen, das als Anlage gesendet werden soll, oder das Mikrofon zum Aufzeichnen der Unterhaltung verwenden.</span><span class="sxs-lookup"><span data-stu-id="eabab-117">It allows your app to ask for requisite permissions from users before they start using  the **camera** to capture the image, open the gallery to select an image to submit as an attachment, or use the **microphone** to record the conversation.</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="eabab-118">Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="eabab-118">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="eabab-119">Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="eabab-119">For more information, see [Request device permissions](native-device-permissions.md).</span></span>

## <a name="media-capability-apis"></a><span data-ttu-id="eabab-120">APIs für Medienfunktionen</span><span class="sxs-lookup"><span data-stu-id="eabab-120">Media capability APIs</span></span>

<span data-ttu-id="eabab-121">Mit [den SELECTMedia-,](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) [getMedia-](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)und [viewImages-APIs](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) können Sie systemeigene Medienfunktionen wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="eabab-121">The [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true), and [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) APIs enable you to use native media capabilities as follows:</span></span>

* <span data-ttu-id="eabab-122">Verwenden Sie das systemeigene **Mikrofon,** um Benutzern das Aufzeichnen von Audio  (10 Minuten Unterhaltung) vom Gerät zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="eabab-122">Use the native **microphone** to allow users to **record audio** (record 10 minutes of conversation) from the device.</span></span>
* <span data-ttu-id="eabab-123">Verwenden Sie ein **systemeigenes Kamerasteuerelement,** damit Benutzer unterwegs Bilder erfassen und anfügen können. </span><span class="sxs-lookup"><span data-stu-id="eabab-123">Use native **camera control** to allow users to **capture and attach images** on the go.</span></span>
* <span data-ttu-id="eabab-124">Verwenden Sie die **systemeigene Katalogunterstützung,** um Benutzern die **Auswahl von Gerätebildern als** Anlagen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="eabab-124">Use native **gallery support** to allow users to **select device images** as attachments.</span></span>
* <span data-ttu-id="eabab-125">Verwenden Sie ein **systemeigenes Steuerelement für** die **Bildanzeige,** um mehrere Bilder gleichzeitig in der Vorschau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="eabab-125">Use native **image viewer control** to **preview multiple images** at one time.</span></span>
* <span data-ttu-id="eabab-126">Unterstützung **einer großen Bildübertragung** (von 1 MB auf 50 MB) über die SDK-Brücke.</span><span class="sxs-lookup"><span data-stu-id="eabab-126">Support **large image transfer** (from 1 MB to 50 MB) through the SDK bridge.</span></span>
* <span data-ttu-id="eabab-127">Unterstützung **erweiterter Bildfunktionen,** mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:</span><span class="sxs-lookup"><span data-stu-id="eabab-127">Support **advanced image capabilities** allowing users to preview and edit images:</span></span>
  * <span data-ttu-id="eabab-128">Scannen Sie Dokumente, Whiteboards und Visitenkarten über die Kamera.</span><span class="sxs-lookup"><span data-stu-id="eabab-128">Scan document, whiteboard, and business cards  through the camera.</span></span>
  
> [!IMPORTANT]
>*   <span data-ttu-id="eabab-129">Die , und APIs können von mehreren Teams-Oberflächen wie Aufgabenmodulen, Registerkarten und `selectMedia` `getMedia` `viewImages` persönlichen Apps aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="eabab-129">The `selectMedia`, `getMedia`, and `viewImages` APIs can be invoked from multiple Teams surfaces such as task modules, tabs, and personal apps.</span></span> <span data-ttu-id="eabab-130">Weitere Informationen finden Sie unter [Einstiegspunkte für Teams-Apps.](../extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="eabab-130">For more details, see [Entry points for Teams apps](../extensibility-points.md).</span></span>
>* <span data-ttu-id="eabab-131">`selectMedia` Die API wurde erweitert, um Mikrofon- und Audioeigenschaften zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="eabab-131">`selectMedia` API has been extended to support mic and audio properties.</span></span>

<span data-ttu-id="eabab-132">Sie müssen die folgenden APIs verwenden, um die Medienfunktionen Ihres Geräts zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="eabab-132">You must use the following set of APIs to enable your device's media capabilities:</span></span>

| <span data-ttu-id="eabab-133">API</span><span class="sxs-lookup"><span data-stu-id="eabab-133">API</span></span>      | <span data-ttu-id="eabab-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eabab-134">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="eabab-135">[**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Kamera)**</span><span class="sxs-lookup"><span data-stu-id="eabab-135">[**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Camera)**</span></span>| <span data-ttu-id="eabab-136">Mit dieser API können Benutzer **Medien** von der Gerätekamera erfassen oder auswählen und an die Web-App zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="eabab-136">This API allows users to **capture or select media from the device camera** and return it to the web-app.</span></span> <span data-ttu-id="eabab-137">Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder zeichnen.</span><span class="sxs-lookup"><span data-stu-id="eabab-137">The users can edit, crop, rotate, annotate, or draw over images before submission.</span></span> <span data-ttu-id="eabab-138">Als Reaktion auf **selectMedia** empfängt die Web-App die Medien-IDs ausgewählter Bilder und eine Miniaturansicht des ausgewählten Mediums.</span><span class="sxs-lookup"><span data-stu-id="eabab-138">In response to **selectMedia**, the web-app receives the media IDs of selected images and a thumbnail of the selected media.</span></span> <span data-ttu-id="eabab-139">Diese API kann über die [ImageProps-Konfiguration weiter konfiguriert](/javascript/api/@microsoft/teams-js/imageprops?view=msteams-client-js-latest&preserve-view=true) werden.</span><span class="sxs-lookup"><span data-stu-id="eabab-139">This API can be further configured through the [ImageProps](/javascript/api/@microsoft/teams-js/imageprops?view=msteams-client-js-latest&preserve-view=true) configuration.</span></span> |
| <span data-ttu-id="eabab-140">[**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Mikrofon**)</span><span class="sxs-lookup"><span data-stu-id="eabab-140">[**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Microphone**)</span></span>| <span data-ttu-id="eabab-141">Legen Sie [mediaType](/javascript/api/@microsoft/teams-js/mediatype?view=msteams-client-js-latest&preserve-view=true) in der `4` **selectMedia-API** für den Zugriff auf die Mikrofonfunktion auf "mediaType" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="eabab-141">Set the [mediaType](/javascript/api/@microsoft/teams-js/mediatype?view=msteams-client-js-latest&preserve-view=true) to `4` in **selectMedia** API for accessing microphone  capability.</span></span> <span data-ttu-id="eabab-142">Mit dieser API können Benutzer auch Audiodaten aus dem Gerätemikrofon aufzeichnen und aufgezeichnete Clips an die Web-App zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="eabab-142">This API also allows users to record audio from the device microphone and return recorded clips to the web-app.</span></span> <span data-ttu-id="eabab-143">Die Benutzer können die Aufzeichnungsvorschau vor der Übermittlung anhalten, erneut aufzeichnen und wiederverspielen.</span><span class="sxs-lookup"><span data-stu-id="eabab-143">The users can pause, re-record, and play recording preview before submission.</span></span> <span data-ttu-id="eabab-144">Als Reaktion auf **selectMedia** empfängt die Web-App Medien-IDs der ausgewählten Audioaufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="eabab-144">In response to **selectMedia**, the web-app receives media IDs of the selected audio recording.</span></span> <br/> <span data-ttu-id="eabab-145">Verwenden Sie , wenn Sie eine Dauer in Minuten für die `maxDuration` Aufzeichnung der Unterhaltung konfigurieren müssen.</span><span class="sxs-lookup"><span data-stu-id="eabab-145">Use `maxDuration`, if you require to configure a duration in minutes for recording the conversation.</span></span> <span data-ttu-id="eabab-146">Die aktuelle Dauer für die Aufzeichnung beträgt 10 Minuten, danach wird die Aufzeichnung beendet.</span><span class="sxs-lookup"><span data-stu-id="eabab-146">The current duration for recording is 10 minutes, after which the recording terminates.</span></span>  |
| [<span data-ttu-id="eabab-147">**getMedia**</span><span class="sxs-lookup"><span data-stu-id="eabab-147">**getMedia**</span></span>](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| <span data-ttu-id="eabab-148">Diese API ruft die von der **selectMedia-API** erfassten Medien unabhängig von der Mediengröße in Blöcken ab.</span><span class="sxs-lookup"><span data-stu-id="eabab-148">This API retrieves the media captured by **selectMedia** API in chunks, irrespective of the media size.</span></span> <span data-ttu-id="eabab-149">Diese Blöcke werden zusammengestellt und als Datei oder BLOB an die Web App gesendet.</span><span class="sxs-lookup"><span data-stu-id="eabab-149">These chunks are assembled and sent back to the web app as a file or blob.</span></span> <span data-ttu-id="eabab-150">Das Aufbrechen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien.</span><span class="sxs-lookup"><span data-stu-id="eabab-150">Breaking of media into smaller chunks facilitates large file transfer.</span></span> |
| [<span data-ttu-id="eabab-151">**viewImages**</span><span class="sxs-lookup"><span data-stu-id="eabab-151">**viewImages**</span></span>](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| <span data-ttu-id="eabab-152">Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="eabab-152">This API enables the user to view images in  full-screen mode as a scrollable list.</span></span>|


<span data-ttu-id="eabab-153">**Web-App-Erfahrung für selectMedia-API für Bildfunktionen** 
 ![ Gerätekamera und Bilderfahrung in Teams](../../assets/images/tabs/image-capability.png)</span><span class="sxs-lookup"><span data-stu-id="eabab-153">**Web app experience for selectMedia API for image capability**
![device camera and image experience in Teams](../../assets/images/tabs/image-capability.png)</span></span>

<span data-ttu-id="eabab-154">**Web-App-Erfahrung für selectMedia-API für Mikrofonfunktionen** 
 ![ Web-App-Erfahrung für Mikrofonfunktionen](../../assets/images/tabs/microphone-capability.png)</span><span class="sxs-lookup"><span data-stu-id="eabab-154">**Web app experience for selectMedia API for microphone capability**
![web app experience for microphone capability](../../assets/images/tabs/microphone-capability.png)</span></span>

## <a name="error-handling"></a><span data-ttu-id="eabab-155">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="eabab-155">Error handling</span></span>

<span data-ttu-id="eabab-156">Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App entsprechend umgangen werden.</span><span class="sxs-lookup"><span data-stu-id="eabab-156">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="eabab-157">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="eabab-157">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 


|<span data-ttu-id="eabab-158">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="eabab-158">Error code</span></span> |  <span data-ttu-id="eabab-159">Fehlername</span><span class="sxs-lookup"><span data-stu-id="eabab-159">Error name</span></span>     | <span data-ttu-id="eabab-160">Bedingung</span><span class="sxs-lookup"><span data-stu-id="eabab-160">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="eabab-161">**100**</span><span class="sxs-lookup"><span data-stu-id="eabab-161">**100**</span></span> | <span data-ttu-id="eabab-162">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="eabab-162">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="eabab-163">Die API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eabab-163">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="eabab-164">**404**</span><span class="sxs-lookup"><span data-stu-id="eabab-164">**404**</span></span> | <span data-ttu-id="eabab-165">FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="eabab-165">FILE_NOT_FOUND</span></span> | <span data-ttu-id="eabab-166">Die angegebene Datei wurde am angegebenen Speicherort nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="eabab-166">File specified is not found in the given location.</span></span>|
| <span data-ttu-id="eabab-167">**500**</span><span class="sxs-lookup"><span data-stu-id="eabab-167">**500**</span></span> | <span data-ttu-id="eabab-168">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="eabab-168">INTERNAL_ERROR</span></span> | <span data-ttu-id="eabab-169">Interner Fehler beim Ausführen des erforderlichen Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="eabab-169">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="eabab-170">**1000**</span><span class="sxs-lookup"><span data-stu-id="eabab-170">**1000**</span></span> | <span data-ttu-id="eabab-171">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="eabab-171">PERMISSION_DENIED</span></span> |<span data-ttu-id="eabab-172">Die Berechtigung wird vom Benutzer verweigert.</span><span class="sxs-lookup"><span data-stu-id="eabab-172">Permission is denied by the user.</span></span>|
| <span data-ttu-id="eabab-173">**2000**</span><span class="sxs-lookup"><span data-stu-id="eabab-173">**2000**</span></span> |<span data-ttu-id="eabab-174">NETWORK_ERROR</span><span class="sxs-lookup"><span data-stu-id="eabab-174">NETWORK_ERROR</span></span> | <span data-ttu-id="eabab-175">Netzwerkproblem.</span><span class="sxs-lookup"><span data-stu-id="eabab-175">Network issue.</span></span>|
| <span data-ttu-id="eabab-176">**3000**</span><span class="sxs-lookup"><span data-stu-id="eabab-176">**3000**</span></span> | <span data-ttu-id="eabab-177">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="eabab-177">NO_HW_SUPPORT</span></span> | <span data-ttu-id="eabab-178">Die zugrunde liegende Hardware unterstützt die Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="eabab-178">Underlying hardware does not support the capability.</span></span>|
| <span data-ttu-id="eabab-179">**4000**</span><span class="sxs-lookup"><span data-stu-id="eabab-179">**4000**</span></span>| <span data-ttu-id="eabab-180">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="eabab-180">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="eabab-181">Mindestens ein Argument ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="eabab-181">One or more arguments are invalid.</span></span>|
| <span data-ttu-id="eabab-182">**5000**</span><span class="sxs-lookup"><span data-stu-id="eabab-182">**5000**</span></span> | <span data-ttu-id="eabab-183">UNAUTHORIZED_USER_OPERATION</span><span class="sxs-lookup"><span data-stu-id="eabab-183">UNAUTHORIZED_USER_OPERATION</span></span> | <span data-ttu-id="eabab-184">Der Benutzer ist nicht zum Abschließen dieses Vorgangs autorisiert.</span><span class="sxs-lookup"><span data-stu-id="eabab-184">User is not authorized to complete this operation.</span></span>|
| <span data-ttu-id="eabab-185">**6000**</span><span class="sxs-lookup"><span data-stu-id="eabab-185">**6000**</span></span> |<span data-ttu-id="eabab-186">INSUFFICIENT_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="eabab-186">INSUFFICIENT_RESOURCES</span></span> | <span data-ttu-id="eabab-187">Der Vorgang konnte aufgrund unzureichender Ressourcen nicht abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="eabab-187">Operation could not be completed due to insufficient resources.</span></span>|
|<span data-ttu-id="eabab-188">**7000**</span><span class="sxs-lookup"><span data-stu-id="eabab-188">**7000**</span></span> | <span data-ttu-id="eabab-189">THROTTLE</span><span class="sxs-lookup"><span data-stu-id="eabab-189">THROTTLE</span></span> | <span data-ttu-id="eabab-190">Die Plattform hat die Anforderung gedrosselt, da die API häufig aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="eabab-190">Platform throttled the request as the API was invoked frequently.</span></span>|
|  <span data-ttu-id="eabab-191">**8000**</span><span class="sxs-lookup"><span data-stu-id="eabab-191">**8000**</span></span> | <span data-ttu-id="eabab-192">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="eabab-192">USER_ABORT</span></span> |<span data-ttu-id="eabab-193">Der Benutzer bricht den Vorgang ab.</span><span class="sxs-lookup"><span data-stu-id="eabab-193">User aborts the operation.</span></span>|
| <span data-ttu-id="eabab-194">**9000**</span><span class="sxs-lookup"><span data-stu-id="eabab-194">**9000**</span></span>| <span data-ttu-id="eabab-195">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="eabab-195">OLD_PLATFORM</span></span> | <span data-ttu-id="eabab-196">Plattformcode ist veraltet und implementiert diese API nicht.</span><span class="sxs-lookup"><span data-stu-id="eabab-196">Platform code is outdated and does not implement this API.</span></span>|
| <span data-ttu-id="eabab-197">**10000**</span><span class="sxs-lookup"><span data-stu-id="eabab-197">**10000**</span></span>| <span data-ttu-id="eabab-198">SIZE_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="eabab-198">SIZE_EXCEEDED</span></span> |  <span data-ttu-id="eabab-199">Der Rückgabewert ist zu groß und hat die Plattformgrößengrenzen überschritten.</span><span class="sxs-lookup"><span data-stu-id="eabab-199">Return value is too big and has exceeded the platform size boundaries.</span></span>|

## <a name="code-snippets"></a><span data-ttu-id="eabab-200">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="eabab-200">Code snippets</span></span>

<span data-ttu-id="eabab-201">**Anrufe `selectMedia` API** zum Aufnehmen von Bildern mit der Kamera:</span><span class="sxs-lookup"><span data-stu-id="eabab-201">**Calling `selectMedia` API** for capturing images using camera:</span></span>

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

<span data-ttu-id="eabab-202">**Anrufe `getMedia` API** zum Abrufen großer Medien in Blöcken:</span><span class="sxs-lookup"><span data-stu-id="eabab-202">**Calling `getMedia` API** to retrieve large media in chunks:</span></span>

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

<span data-ttu-id="eabab-203">**Anrufe `viewImages` API nach ID, die von der `selectMedia` API zurückgegeben wird:**</span><span class="sxs-lookup"><span data-stu-id="eabab-203">**Calling `viewImages` API by ID returned by `selectMedia` API**:</span></span>

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

<span data-ttu-id="eabab-204">**Anrufe `viewImages` API nach URL:**</span><span class="sxs-lookup"><span data-stu-id="eabab-204">**Calling `viewImages` API by URL**:</span></span>

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

<span data-ttu-id="eabab-205">**Anrufe `selectMedia` und `getMedia` APIs zum Aufzeichnen von Audio über Mikrofon:**</span><span class="sxs-lookup"><span data-stu-id="eabab-205">**Calling `selectMedia` and `getMedia` APIs for recording audio through microphone**:</span></span>

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
