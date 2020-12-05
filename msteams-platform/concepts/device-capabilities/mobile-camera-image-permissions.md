---
title: Kamera-und Bildfunktionen in Microsoft Teams
description: Verwenden von Microsoft Teams-JavaScript-Client-SDK zur Aktivierung systemeigener Kamera-und Bildfunktionen
keywords: Kamerabild Funktionen systemeigene Geräte Berechtigungen
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d0ca4dc9c289ec525aa99ea0e156a9f91f5b5d4a
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576885"
---
# <a name="camera-and-image-capabilities-in-teams"></a><span data-ttu-id="05db5-104">Kamera-und Bildfunktionen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="05db5-104">Camera and image capabilities in Teams</span></span>

>[!IMPORTANT]
>
> * <span data-ttu-id="05db5-105">Derzeit ist die Microsoft Teams-Unterstützung für Kamera-und Bildfunktionen nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="05db5-105">At present, Teams support for camera and image capabilities is only available for mobile clients.</span></span>
>* <span data-ttu-id="05db5-106">Die `selectMedia` `getMedia` `viewImages` APIs können von mehreren Teams-Oberflächen wie Aufgaben Module, Registerkarten und persönliche apps aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="05db5-106">The `selectMedia`, `getMedia`, and `viewImages` APIs can be invoked from multiple Teams surfaces such as task modules, tabs, and personal apps.</span></span> <span data-ttu-id="05db5-107">Weitere Informationen _finden Sie unter_ [Einstiegspunkte für Microsoft Teams-apps](../extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="05db5-107">For more details, _see_ [Entry points for Teams apps](../extensibility-points.md)</span></span>

<span data-ttu-id="05db5-108">Sie können das  [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, um die Kamera-und Bildfunktionen in Ihren Microsoft Teams-Mobile App problemlos zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="05db5-108">You can use the  [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), to easily integrate camera and image capabilities within your Microsoft Teams mobile app.</span></span> <span data-ttu-id="05db5-109">Das SDK stellt die Tools bereit, die für Ihre APP erforderlich sind, um auf die [Geräte Berechtigungen](native-device-permissions.md?tabs=desktop#device-permissions) eines Benutzers zuzugreifen und eine umfassendere Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="05db5-109">The SDK provides the tools necessary for your app to access a user’s [device permissions](native-device-permissions.md?tabs=desktop#device-permissions) and build a richer experience.</span></span>

<span data-ttu-id="05db5-110">Die [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)-, [getmedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)-und [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) -APIs ermöglichen die Verwendung systemeigener Kamera/Bild-Funktionen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="05db5-110">The [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true), [getMedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true), and [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) APIs enable you to use native camera/image capabilities as follows:</span></span>

* <span data-ttu-id="05db5-111">Verwenden Sie systemeigene **Kamerasteuerung** , damit Benutzer **Bilder unterwegs erfassen und Anfügen** können.</span><span class="sxs-lookup"><span data-stu-id="05db5-111">Use native **camera control** to allow users to **capture and attach images** on the go.</span></span>
* <span data-ttu-id="05db5-112">Verwenden Sie Native **Gallery-Unterstützung** , um Benutzern das **Auswählen von Geräte Abbildern** als Anlagen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="05db5-112">Use native **gallery support** to allow users to **select device images** as attachments.</span></span>
* <span data-ttu-id="05db5-113">Verwenden Sie das systemeigene **Image Viewer-Steuerelement** , um mehrere Bilder gleichzeitig in einer **Vorschau anzuzeigen** .</span><span class="sxs-lookup"><span data-stu-id="05db5-113">Use native **image viewer control** to **preview multiple images** at one time.</span></span>
* <span data-ttu-id="05db5-114">Unterstützung der **großen Bildübertragung** (bis zu 50 MB) über die SDK-Brücke</span><span class="sxs-lookup"><span data-stu-id="05db5-114">Support **large image transfer** (up to 50 MB) via the SDK bridge</span></span>
* <span data-ttu-id="05db5-115">Unterstützung **Erweiterter Bildfunktionen** , mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:</span><span class="sxs-lookup"><span data-stu-id="05db5-115">Support **advanced image capabilities** allowing users to preview and edit images:</span></span>
  * <span data-ttu-id="05db5-116">Überprüfen Sie Dokument, Whiteboard, Visitenkarten usw. über die Kamera.</span><span class="sxs-lookup"><span data-stu-id="05db5-116">Scan document, whiteboard, business cards, etc., through the camera.</span></span>
  * <span data-ttu-id="05db5-117">Zuschneiden und Drehen der Bilder.</span><span class="sxs-lookup"><span data-stu-id="05db5-117">Crop and rotate the images.</span></span>
  * <span data-ttu-id="05db5-118">Fügen Sie dem Bild Text, Freihand oder Freihand-Anmerkungen hinzu.</span><span class="sxs-lookup"><span data-stu-id="05db5-118">Add text, ink, or freehand annotation to the image.</span></span>

## <a name="get-started"></a><span data-ttu-id="05db5-119">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="05db5-119">Get started</span></span>

<span data-ttu-id="05db5-120">Aktualisieren Sie Ihre Teams-APP- [manifest.jsauf](../../resources/schema/manifest-schema.md#devicepermissions) Datei, indem Sie die `devicePermissions`  -Eigenschaft hinzufügen und angeben `media` .</span><span class="sxs-lookup"><span data-stu-id="05db5-120">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions`  property and specifying `media`.</span></span> <span data-ttu-id="05db5-121">Dadurch kann Ihre APP die erforderlichen Berechtigungen von Endbenutzern anfordern, bevor Sie die Kamera zum Erfassen des Bilds verwenden oder den Katalog öffnen, um ein Bild auszuwählen, das als Anlage gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="05db5-121">This allows your app to ask for requisite permissions from end-users before they use the camera to capture the image or open the gallery to select an image to submit as an attachment.</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="05db5-122">Die _Anforderungs Berechtigungs_ Eingabeaufforderung wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="05db5-122">The _Request Permissions_ prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="05db5-123">Weitere Informationen *finden Sie unter* [anfordern von Geräte Berechtigungen](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="05db5-123">For more details, *see* [Request device permissions](native-device-permissions.md).</span></span>

## <a name="using-camera-and-image-capability-apis"></a><span data-ttu-id="05db5-124">Verwenden von Kamera-und Bild Funktions-APIs</span><span class="sxs-lookup"><span data-stu-id="05db5-124">Using camera and image capability APIs</span></span>

<span data-ttu-id="05db5-125">Sie können die folgenden APIs verwenden, um die Kamera-und Bildgeräte Funktionen zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="05db5-125">You can use the following set of APIs to enable camera and image device capabilities:</span></span>

| <span data-ttu-id="05db5-126">API</span><span class="sxs-lookup"><span data-stu-id="05db5-126">API</span></span>      | <span data-ttu-id="05db5-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="05db5-127">Description</span></span>   |
| --- | --- |
| [<span data-ttu-id="05db5-128">**selectMedia**</span><span class="sxs-lookup"><span data-stu-id="05db5-128">**selectMedia**</span></span>](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest&branch=master#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)| <span data-ttu-id="05db5-129">Mit dieser API können Benutzer **Medien von einem systemeigenen Gerät erfassen oder auswählen** und zur Webanwendung zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="05db5-129">This API allows users to **capture or select media from a native device** and return to the web-app.</span></span> <span data-ttu-id="05db5-130">Benutzer können vor der Übermittlung auswählen, ob Sie Bilder bearbeiten, Zuschneiden, drehen, kommentieren oder darüber zeichnen möchten.</span><span class="sxs-lookup"><span data-stu-id="05db5-130">Users may choose to edit, crop, rotate, annotate, or draw over images before submission.</span></span> <span data-ttu-id="05db5-131">Als Reaktion auf **selectMedia** empfängt die Webanwendung Medien-IDs ausgewählter Bilder und erhält möglicherweise eine Miniaturansicht des ausgewählten Mediums.</span><span class="sxs-lookup"><span data-stu-id="05db5-131">In response to **selectMedia**, the web-app will receive media ids of selected images and may receive a thumbnail of the selected media.</span></span> |
| [<span data-ttu-id="05db5-132">**getmedia**</span><span class="sxs-lookup"><span data-stu-id="05db5-132">**getMedia**</span></span>](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest&branch=master#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| <span data-ttu-id="05db5-133">Diese API ruft die Medien unabhängig von ihrer Größe in Chunks ab.</span><span class="sxs-lookup"><span data-stu-id="05db5-133">This API retrieves the media in chunks irrespective of size.</span></span> <span data-ttu-id="05db5-134">Diese Chunks werden zusammengestellt und als Datei/BLOB an die Webanwendung zurückgesendet.</span><span class="sxs-lookup"><span data-stu-id="05db5-134">These chunks are assembled and sent back to the web app as a file/blob.</span></span> <span data-ttu-id="05db5-135">Mit dieser API wird ein Bild in kleinere Abschnitte unterteilt, um eine große Bildübertragung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="05db5-135">With this API an image is broken into smaller chunks to facilitate large image transfer.</span></span> |
| [<span data-ttu-id="05db5-136">**viewImages**</span><span class="sxs-lookup"><span data-stu-id="05db5-136">**viewImages**</span></span>](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| <span data-ttu-id="05db5-137">Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="05db5-137">This API enables the user to view images full-screen mode as a scrollable list.</span></span>|

<span data-ttu-id="05db5-138">**Webanwendungs Oberfläche für die selectMedia-API** 
 ![ Gerätekamera-und Bilderfahrung in Microsoft Teams](../../assets/images/tabs/image-capability-screenshot.jpg)</span><span class="sxs-lookup"><span data-stu-id="05db5-138">**Web app experience for selectMedia API**
![device camera and image experience in Teams](../../assets/images/tabs/image-capability-screenshot.jpg)</span></span>

## <a name="error-handling"></a><span data-ttu-id="05db5-139">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="05db5-139">Error handling</span></span>

<span data-ttu-id="05db5-140">Sie sollten die API-Antwortfehler Codes verstehen und Sie entsprechend behandeln.</span><span class="sxs-lookup"><span data-stu-id="05db5-140">You should understand the API response error codes and handle them appropriately.</span></span> <span data-ttu-id="05db5-141">Nachfolgend finden Sie eine Liste der Fehlercodes, die von der Plattform zurückgegeben werden können:</span><span class="sxs-lookup"><span data-stu-id="05db5-141">Below is a list of error codes that may be returned by the platform:</span></span>

|<span data-ttu-id="05db5-142">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="05db5-142">Error code</span></span> |  <span data-ttu-id="05db5-143">Fehler Name</span><span class="sxs-lookup"><span data-stu-id="05db5-143">Error Name</span></span>     | <span data-ttu-id="05db5-144">Bedingung</span><span class="sxs-lookup"><span data-stu-id="05db5-144">Condition</span></span>|
| --- | --- | --- |
| <span data-ttu-id="05db5-145">**100**</span><span class="sxs-lookup"><span data-stu-id="05db5-145">**100**</span></span> | <span data-ttu-id="05db5-146">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="05db5-146">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="05db5-147">API wird in der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="05db5-147">API not supported in the current platform.</span></span>|
| <span data-ttu-id="05db5-148">**404**</span><span class="sxs-lookup"><span data-stu-id="05db5-148">**404**</span></span> | <span data-ttu-id="05db5-149">FILE_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="05db5-149">FILE_NOT_FOUND</span></span> | <span data-ttu-id="05db5-150">Die angegebene Datei wurde an der angegebenen Position nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="05db5-150">The file specified was not found on the given location.</span></span>|
| <span data-ttu-id="05db5-151">**500**</span><span class="sxs-lookup"><span data-stu-id="05db5-151">**500**</span></span> | <span data-ttu-id="05db5-152">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="05db5-152">INTERNAL_ERROR</span></span> | <span data-ttu-id="05db5-153">Interner Fehler, der beim Ausführen des erforderlichen Vorgangs aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="05db5-153">Internal error encountered while performing the required operation.</span></span>|
| <span data-ttu-id="05db5-154">**1000**</span><span class="sxs-lookup"><span data-stu-id="05db5-154">**1000**</span></span> | <span data-ttu-id="05db5-155">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="05db5-155">PERMISSION_DENIED</span></span> |<span data-ttu-id="05db5-156">Vom Benutzer verweigerte Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="05db5-156">Permissions denied by the user.</span></span>|
| <span data-ttu-id="05db5-157">**2000**</span><span class="sxs-lookup"><span data-stu-id="05db5-157">**2000**</span></span> |<span data-ttu-id="05db5-158">NETWORK_ERROR</span><span class="sxs-lookup"><span data-stu-id="05db5-158">NETWORK_ERROR</span></span> | <span data-ttu-id="05db5-159">Netzwerkproblem.</span><span class="sxs-lookup"><span data-stu-id="05db5-159">Network issue.</span></span>|
| <span data-ttu-id="05db5-160">**3000**</span><span class="sxs-lookup"><span data-stu-id="05db5-160">**3000**</span></span> | <span data-ttu-id="05db5-161">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="05db5-161">NO_HW_SUPPORT</span></span> | <span data-ttu-id="05db5-162">Die zugrunde liegende Hardware unterstützt die Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="05db5-162">Underlying hardware doesn't support the capability.</span></span>|
| <span data-ttu-id="05db5-163">**4000**</span><span class="sxs-lookup"><span data-stu-id="05db5-163">**4000**</span></span>| <span data-ttu-id="05db5-164">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="05db5-164">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="05db5-165">Mindestens ein Argument ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="05db5-165">One or more arguments is invalid.</span></span>|
| <span data-ttu-id="05db5-166">**5000**</span><span class="sxs-lookup"><span data-stu-id="05db5-166">**5000**</span></span> | <span data-ttu-id="05db5-167">UNAUTHORIZED_USER_OPERATION</span><span class="sxs-lookup"><span data-stu-id="05db5-167">UNAUTHORIZED_USER_OPERATION</span></span> | <span data-ttu-id="05db5-168">Der Benutzer ist nicht berechtigt, diesen Vorgang abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="05db5-168">User is not authorized to complete this operation.</span></span>|
| <span data-ttu-id="05db5-169">**6000**</span><span class="sxs-lookup"><span data-stu-id="05db5-169">**6000**</span></span> |<span data-ttu-id="05db5-170">INSUFFICIENT_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="05db5-170">INSUFFICIENT_RESOURCES</span></span> | <span data-ttu-id="05db5-171">Der Vorgang konnte aufgrund unzureichender Ressourcen nicht abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="05db5-171">The operation couldn't be completed due to insufficient resources.</span></span>|
|<span data-ttu-id="05db5-172">**7000**</span><span class="sxs-lookup"><span data-stu-id="05db5-172">**7000**</span></span> | <span data-ttu-id="05db5-173">THROTTLE</span><span class="sxs-lookup"><span data-stu-id="05db5-173">THROTTLE</span></span> | <span data-ttu-id="05db5-174">Die Plattform hat die Anforderung gedrosselt, da die API zu häufig aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="05db5-174">The platform throttled the request because the API was invoked too frequently.</span></span>|
|  <span data-ttu-id="05db5-175">**8000**</span><span class="sxs-lookup"><span data-stu-id="05db5-175">**8000**</span></span> | <span data-ttu-id="05db5-176">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="05db5-176">USER_ABORT</span></span> |<span data-ttu-id="05db5-177">Der Benutzer hat den Vorgang abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="05db5-177">User aborted the operation.</span></span>|
| <span data-ttu-id="05db5-178">**9000**</span><span class="sxs-lookup"><span data-stu-id="05db5-178">**9000**</span></span>| <span data-ttu-id="05db5-179">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="05db5-179">OLD_PLATFORM</span></span> | <span data-ttu-id="05db5-180">Der Plattformcode ist veraltet und implementiert diese API nicht.</span><span class="sxs-lookup"><span data-stu-id="05db5-180">The platform code is outdated and doesn't implement this API.</span></span>|
| <span data-ttu-id="05db5-181">**10000**</span><span class="sxs-lookup"><span data-stu-id="05db5-181">**10000**</span></span>| <span data-ttu-id="05db5-182">SIZE_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="05db5-182">SIZE_EXCEEDED</span></span> |  <span data-ttu-id="05db5-183">Der Rückgabewert ist zu groß und hat die Begrenzungen der Plattformgröße überschritten.</span><span class="sxs-lookup"><span data-stu-id="05db5-183">The return value is too big and has exceeded the platform size boundaries.</span></span>|

## <a name="sample-code-snippets"></a><span data-ttu-id="05db5-184">Beispielcodeausschnitte</span><span class="sxs-lookup"><span data-stu-id="05db5-184">Sample code snippets</span></span>

<span data-ttu-id="05db5-185">**Aufrufende `selectMedia` API**</span><span class="sxs-lookup"><span data-stu-id="05db5-185">**Calling `selectMedia` API**</span></span>

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

<span data-ttu-id="05db5-186">**Aufrufende `getMedia` API**</span><span class="sxs-lookup"><span data-stu-id="05db5-186">**Calling `getMedia` API**</span></span>

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

<span data-ttu-id="05db5-187">**Aufrufen `viewImages`  der API nach ID**</span><span class="sxs-lookup"><span data-stu-id="05db5-187">**Calling `viewImages`  API by ID**</span></span>

```javascript
view images by id:
    assumption: attachmentArray = select Media API Outputlet uriList = [];
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

<span data-ttu-id="05db5-188">**Aufrufen der viewImages-API nach URL**</span><span class="sxs-lookup"><span data-stu-id="05db5-188">**Calling viewImages API by URL**</span></span>

```javascript
View Images by URL:
    // Assumption 2 urls, url1 and url2let uriList = [];
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
}
```
