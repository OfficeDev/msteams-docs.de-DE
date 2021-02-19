---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzuholen, für die in der Regel die Zustimmung des Benutzers erforderlich ist
ms.topic: how-to
ms.openlocfilehash: 60c28e1170e8bbdf664145bde7f7de585bd55a45
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294747"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="ea117-104">Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="ea117-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="ea117-105">Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort bereichern.</span><span class="sxs-lookup"><span data-stu-id="ea117-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="ea117-106">In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="ea117-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> * <span data-ttu-id="ea117-107">Informationen zur Integration von Medienfunktionen in Ihre mobile Microsoft Teams-App finden Sie [unter Integrieren von Medienfunktionen](mobile-camera-image-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="ea117-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>
> * <span data-ttu-id="ea117-108">Informationen zur Integration von QR- oder Barcodescannerfunktionen in Ihre mobile Microsoft Teams-App finden Sie unter Integrieren der QR- oder [Barcodescannerfunktion in Teams.](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="ea117-108">To integrate QR or barcode scanner capability within your Microsoft Teams mobile app, see [Integrate QR or barcode scanner capability in Teams](qr-barcode-scanner-capability.md)</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="ea117-109">Berechtigungen für systemeigene Geräte</span><span class="sxs-lookup"><span data-stu-id="ea117-109">Native device permissions</span></span>

<span data-ttu-id="ea117-110">Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ea117-110">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="ea117-111">Die Geräteberechtigungen funktionieren ähnlich für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="ea117-111">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="ea117-112">Der Benutzer muss zur Seite Berechtigungen in den Teams-Einstellungen wechseln, um Geräteberechtigungen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="ea117-112">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="ea117-113">Durch den Zugriff auf die Gerätefunktionen können Sie auf der Teams-Plattform vielfältigere Erfahrungen erstellen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="ea117-113">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="ea117-114">Erfassen und Anzeigen von Bildern.</span><span class="sxs-lookup"><span data-stu-id="ea117-114">Capture and view images.</span></span>
* <span data-ttu-id="ea117-115">Scannen Sie QR oder Barcode.</span><span class="sxs-lookup"><span data-stu-id="ea117-115">Scan QR or barcode.</span></span>
* <span data-ttu-id="ea117-116">Aufzeichnen und Freigeben von kurzen Videos.</span><span class="sxs-lookup"><span data-stu-id="ea117-116">Record and share short videos.</span></span>
* <span data-ttu-id="ea117-117">Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="ea117-117">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="ea117-118">Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="ea117-118">Use the location information of the user to display relevant information.</span></span>

## <a name="access-device-permissions"></a><span data-ttu-id="ea117-119">Zugreifen auf Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="ea117-119">Access device permissions</span></span>

<span data-ttu-id="ea117-120">Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) bietet die Tools, die [](#manage-permissions) Für Ihre mobile Teams-App erforderlich sind, um auf die Geräteberechtigungen des Benutzers zu zugreifen und eine reichhaltigere Umgebung zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="ea117-120">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="ea117-121">Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie durch Aktualisieren Ihres App-Manifests verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea117-121">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="ea117-122">Dieses Update ermöglicht es Ihnen, Berechtigungen zu fordern, während Ihre App auf dem Teams-Desktopclient ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ea117-122">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="ea117-123">Derzeit ist Microsoft Teams nur für mobile Clients verfügbar, die Medienfunktionen und QR-Strichcodescanner unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ea117-123">Currently, Microsoft Teams support for media capabilities and QR barcode scanner capability is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="ea117-124">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="ea117-124">Manage permissions</span></span>

<span data-ttu-id="ea117-125">Ein Benutzer kann Geräteberechtigungen in  den Teams-Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps zulassen **oder** verweigern aus.</span><span class="sxs-lookup"><span data-stu-id="ea117-125">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="ea117-126">Desktop</span><span class="sxs-lookup"><span data-stu-id="ea117-126">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="ea117-127">Öffnen Sie Ihre Teams-App.</span><span class="sxs-lookup"><span data-stu-id="ea117-127">Open your Teams app.</span></span>
1. <span data-ttu-id="ea117-128">Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.</span><span class="sxs-lookup"><span data-stu-id="ea117-128">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="ea117-129">Wählen **Sie**  >  **im** Dropdownmenü Einstellungen Berechtigungen aus.</span><span class="sxs-lookup"><span data-stu-id="ea117-129">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="ea117-130">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="ea117-130">Select your desired settings.</span></span>

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="ea117-132">Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="ea117-132">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="ea117-133">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="ea117-133">Open Teams.</span></span>
1. <span data-ttu-id="ea117-134">Wechseln Sie zu **Einstellungen**  >  **App-Berechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="ea117-134">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="ea117-135">Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="ea117-135">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="ea117-136">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="ea117-136">Select your desired settings.</span></span>

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="ea117-138">Angeben von Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="ea117-138">Specify permissions</span></span>

<span data-ttu-id="ea117-139">Aktualisieren Sie Ihre App, indem Sie hinzufügen und angeben, welche der `manifest.json` `devicePermissions` fünf Eigenschaften, die Sie in Ihrer Anwendung verwenden:</span><span class="sxs-lookup"><span data-stu-id="ea117-139">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="ea117-140">Mit jeder Eigenschaft können Sie den Benutzer bitten, um seine Zustimmung zu bitten:</span><span class="sxs-lookup"><span data-stu-id="ea117-140">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="ea117-141">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ea117-141">Property</span></span>      | <span data-ttu-id="ea117-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ea117-142">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="ea117-143">media</span><span class="sxs-lookup"><span data-stu-id="ea117-143">media</span></span>         | <span data-ttu-id="ea117-144">Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf den Medienkatalog.</span><span class="sxs-lookup"><span data-stu-id="ea117-144">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="ea117-145">geolocation</span><span class="sxs-lookup"><span data-stu-id="ea117-145">geolocation</span></span>   | <span data-ttu-id="ea117-146">Berechtigung zum Zurückgeben des Speicherorts des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="ea117-146">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="ea117-147">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="ea117-147">notifications</span></span> | <span data-ttu-id="ea117-148">Berechtigung zum Senden von Benutzerbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="ea117-148">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="ea117-149">midi</span><span class="sxs-lookup"><span data-stu-id="ea117-149">midi</span></span>          | <span data-ttu-id="ea117-150">Berechtigung zum Senden und Empfangen von Midi-Informationen (Musical Instrument Digital Interface) von einem digitalen Musikinstrument.</span><span class="sxs-lookup"><span data-stu-id="ea117-150">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="ea117-151">openExternal</span><span class="sxs-lookup"><span data-stu-id="ea117-151">openExternal</span></span>  | <span data-ttu-id="ea117-152">Berechtigung zum Öffnen von Links in externen Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="ea117-152">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="ea117-153">Überprüfen von Berechtigungen aus Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ea117-153">Check permissions from your app</span></span>

<span data-ttu-id="ea117-154">Überprüfen Sie nach dem Hinzufügen zu Ihrem App-Manifest Berechtigungen mithilfe der `devicePermissions` **HTML5-Berechtigungs-API,** ohne eine Eingabeaufforderung zu verursachen:</span><span class="sxs-lookup"><span data-stu-id="ea117-154">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

``` Javascript
// Different query options:
navigator.permissions.query({ name: 'camera' });
navigator.permissions.query({ name: 'microphone' });
navigator.permissions.query({ name: 'geolocation' });
navigator.permissions.query({ name: 'notifications' });
navigator.permissions.query({ name: 'midi', sysex: true });

// Example:
navigator.permissions.query({name:'geolocation'}).then(function(result) {
  if (result.state == 'granted') {
    // Access granted
  } else if (result.state == 'prompt') {
    // Access has not been granted
  }
});
```

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="ea117-155">Verwenden von Teams-APIs zum Erhalten von Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="ea117-155">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="ea117-156">Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen einzuholen.</span><span class="sxs-lookup"><span data-stu-id="ea117-156">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="ea117-157">Unterstützung für `camera` , und wird über die `gallery` `microphone` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ea117-157">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="ea117-158">Verwenden [**Sie die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.</span><span class="sxs-lookup"><span data-stu-id="ea117-158">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="ea117-159">Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ea117-159">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="ea117-160">Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf dem Teams-Desktopclient unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="ea117-160">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="ea117-161">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ea117-161">For example:</span></span>
 * <span data-ttu-id="ea117-162">Um den Benutzer zum Zugriff auf seinen Standort aufforderen zu können, müssen Sie `getCurrentPosition()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-162">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="ea117-163">Um den Benutzer zum Zugriff auf seine Kamera auf dem Desktop oder Web aufforderen zu können, müssen Sie `getUserMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-163">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="ea117-164">Um das Bild auf mobilen Geräten zu erfassen, bittet Teams mobile um Erlaubnis, wenn Sie `captureImage()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-164">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="ea117-165">Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-165">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="ea117-166">Zum Verwenden der Kamera oder des Zugriffsfotokatalogs fragt Teams mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-166">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="ea117-167">Um das Mikrofon zu verwenden, fordert Teams mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-167">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="ea117-168">Um den Benutzer zum Freigeben des Speicherorts auf der Kartenschnittstelle auffordern zu können, fordert Teams mobile die Berechtigung auf, wenn Sie `getLocation()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="ea117-168">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="ea117-169">Desktop</span><span class="sxs-lookup"><span data-stu-id="ea117-169">Desktop</span></span>](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="ea117-171">Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="ea117-171">Mobile</span></span>](#tab/mobile)

   ![Eingabeaufforderung für Mobile Geräteberechtigungen für Registerkarten](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="ea117-173">Berechtigungsverhalten in Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="ea117-173">Permission behavior across login sessions</span></span>

<span data-ttu-id="ea117-174">Geräteberechtigungen werden für jede Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ea117-174">Device permissions are stored for every login session.</span></span> <span data-ttu-id="ea117-175">Wenn Sie sich bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ea117-175">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="ea117-176">Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen.</span><span class="sxs-lookup"><span data-stu-id="ea117-176">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="ea117-177">Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich bei Teams abmelden oder Mandanten in Teams wechseln.</span><span class="sxs-lookup"><span data-stu-id="ea117-177">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="ea117-178">Wenn Sie den berechtigungen für systemeigene Geräte zustimmen, ist sie nur für Ihre _aktuelle Anmeldesitzung_ gültig.</span><span class="sxs-lookup"><span data-stu-id="ea117-178">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea117-179">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="ea117-179">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea117-180">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="ea117-180">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea117-181">Integrieren von QR- oder Barcodescannerfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="ea117-181">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
