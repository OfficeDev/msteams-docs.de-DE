---
title: Anfordern von Geräteberechtigungen für Microsoft Teams App
keywords: Berechtigungen für teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzuholen, für die in der Regel die Zustimmung des Benutzers erforderlich ist
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: dd317da0b2c8e214f7a44d13ef69bf9fea2aad93
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630537"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="30ee7-104">Anfordern von Geräteberechtigungen für Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="30ee7-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="30ee7-105">Sie können Ihre Teams mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort bereichern.</span><span class="sxs-lookup"><span data-stu-id="30ee7-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="30ee7-106">In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="30ee7-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> * <span data-ttu-id="30ee7-107">Informationen zur Integration von Medienfunktionen in Microsoft Teams Mobile App finden Sie [unter Integrieren von Medienfunktionen](mobile-camera-image-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="30ee7-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>
> * <span data-ttu-id="30ee7-108">Informationen zur Integration von QR- oder Barcodescannerfunktionen in Microsoft Teams Mobile App finden Sie unter Integrieren der [QR-](qr-barcode-scanner-capability.md)oder Barcodescannerfunktion in Teams .</span><span class="sxs-lookup"><span data-stu-id="30ee7-108">To integrate QR or barcode scanner capability within your Microsoft Teams mobile app, see [Integrate QR or barcode scanner capability in Teams](qr-barcode-scanner-capability.md).</span></span>
> * <span data-ttu-id="30ee7-109">Informationen zur Integration von Standortfunktionen in Microsoft Teams Mobile App finden Sie [unter Integrieren von Standortfunktionen](location-capability.md).</span><span class="sxs-lookup"><span data-stu-id="30ee7-109">To integrate location capabilities within your Microsoft Teams mobile app, see [Integrate location capabilities](location-capability.md).</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="30ee7-110">Berechtigungen für systemeigene Geräte</span><span class="sxs-lookup"><span data-stu-id="30ee7-110">Native device permissions</span></span>

<span data-ttu-id="30ee7-111">Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-111">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="30ee7-112">Die Geräteberechtigungen funktionieren ähnlich für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-112">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="30ee7-113">Der Benutzer muss zur Seite Berechtigungen in den Teams wechseln, um Geräteberechtigungen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="30ee7-113">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="30ee7-114">Durch den Zugriff auf die Gerätefunktionen können Sie auf der plattform Teams, z. B.:</span><span class="sxs-lookup"><span data-stu-id="30ee7-114">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="30ee7-115">Erfassen und Anzeigen von Bildern.</span><span class="sxs-lookup"><span data-stu-id="30ee7-115">Capture and view images.</span></span>
* <span data-ttu-id="30ee7-116">Scannen Sie QR oder Barcode.</span><span class="sxs-lookup"><span data-stu-id="30ee7-116">Scan QR or barcode.</span></span>
* <span data-ttu-id="30ee7-117">Aufzeichnen und Freigeben von kurzen Videos.</span><span class="sxs-lookup"><span data-stu-id="30ee7-117">Record and share short videos.</span></span>
* <span data-ttu-id="30ee7-118">Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="30ee7-118">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="30ee7-119">Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="30ee7-119">Use the location information of the user to display relevant information.</span></span>

## <a name="access-device-permissions"></a><span data-ttu-id="30ee7-120">Zugreifen auf Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="30ee7-120">Access device permissions</span></span>

<span data-ttu-id="30ee7-121">Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) bietet die Tools, die für Ihre Teams [](#manage-permissions) mobile App erforderlich sind, um auf die Geräteberechtigungen des Benutzers zu zugreifen und eine reichhaltigere Umgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-121">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="30ee7-122">Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="30ee7-122">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="30ee7-123">Mit diesem Update können Sie Berechtigungen bitten, während Ihre App auf dem Teams ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="30ee7-123">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="30ee7-124">Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Strichcodescanner nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="30ee7-124">Currently, Microsoft Teams support for media capabilities and QR barcode scanner capability is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="30ee7-125">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="30ee7-125">Manage permissions</span></span>

<span data-ttu-id="30ee7-126">Ein Benutzer kann Geräteberechtigungen in Teams  verwalten,  indem er Berechtigungen für bestimmte Apps zulassen oder verweigern aus.</span><span class="sxs-lookup"><span data-stu-id="30ee7-126">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="30ee7-127">Desktop</span><span class="sxs-lookup"><span data-stu-id="30ee7-127">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="30ee7-128">Öffnen Sie ihre Teams App.</span><span class="sxs-lookup"><span data-stu-id="30ee7-128">Open your Teams app.</span></span>
1. <span data-ttu-id="30ee7-129">Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.</span><span class="sxs-lookup"><span data-stu-id="30ee7-129">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="30ee7-130">Wählen **Einstellungen**  >  **Berechtigungen** im Dropdownmenü aus.</span><span class="sxs-lookup"><span data-stu-id="30ee7-130">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="30ee7-131">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="30ee7-131">Select your desired settings.</span></span>

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="30ee7-133">Mobil</span><span class="sxs-lookup"><span data-stu-id="30ee7-133">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="30ee7-134">Öffnen Teams.</span><span class="sxs-lookup"><span data-stu-id="30ee7-134">Open Teams.</span></span>
1. <span data-ttu-id="30ee7-135">Wechseln Sie **zu Einstellungen**  >  **App Permissions**.</span><span class="sxs-lookup"><span data-stu-id="30ee7-135">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="30ee7-136">Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-136">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="30ee7-137">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="30ee7-137">Select your desired settings.</span></span>

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="30ee7-139">Angeben von Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="30ee7-139">Specify permissions</span></span>

<span data-ttu-id="30ee7-140">Aktualisieren Sie Ihre App, indem Sie hinzufügen und angeben, welche der `manifest.json` `devicePermissions` fünf Eigenschaften, die Sie in Ihrer Anwendung verwenden:</span><span class="sxs-lookup"><span data-stu-id="30ee7-140">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="30ee7-141">Mit jeder Eigenschaft können Sie den Benutzer bitten, um seine Zustimmung zu bitten:</span><span class="sxs-lookup"><span data-stu-id="30ee7-141">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="30ee7-142">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="30ee7-142">Property</span></span>      | <span data-ttu-id="30ee7-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="30ee7-143">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="30ee7-144">media</span><span class="sxs-lookup"><span data-stu-id="30ee7-144">media</span></span>         | <span data-ttu-id="30ee7-145">Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf den Medienkatalog.</span><span class="sxs-lookup"><span data-stu-id="30ee7-145">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="30ee7-146">geolocation</span><span class="sxs-lookup"><span data-stu-id="30ee7-146">geolocation</span></span>   | <span data-ttu-id="30ee7-147">Berechtigung zum Zurückgeben des Speicherorts des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="30ee7-147">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="30ee7-148">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="30ee7-148">notifications</span></span> | <span data-ttu-id="30ee7-149">Berechtigung zum Senden von Benutzerbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-149">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="30ee7-150">midi</span><span class="sxs-lookup"><span data-stu-id="30ee7-150">midi</span></span>          | <span data-ttu-id="30ee7-151">Berechtigung zum Senden und Empfangen von Midi-Informationen (Musical Instrument Digital Interface) von einem digitalen Musikinstrument.</span><span class="sxs-lookup"><span data-stu-id="30ee7-151">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="30ee7-152">openExternal</span><span class="sxs-lookup"><span data-stu-id="30ee7-152">openExternal</span></span>  | <span data-ttu-id="30ee7-153">Berechtigung zum Öffnen von Links in externen Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-153">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="30ee7-154">Überprüfen von Berechtigungen aus Ihrer App</span><span class="sxs-lookup"><span data-stu-id="30ee7-154">Check permissions from your app</span></span>

<span data-ttu-id="30ee7-155">Überprüfen Sie nach dem Hinzufügen zu Ihrem App-Manifest Berechtigungen mithilfe der `devicePermissions` **HTML5-Berechtigungs-API,** ohne eine Eingabeaufforderung zu verursachen:</span><span class="sxs-lookup"><span data-stu-id="30ee7-155">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="30ee7-156">Verwenden Teams-APIs zum Erhalten von Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="30ee7-156">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="30ee7-157">Verwenden Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen einzuholen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-157">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="30ee7-158">Unterstützung für `camera` , und wird über die `gallery` `microphone` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="30ee7-158">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="30ee7-159">Verwenden [**Sie die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.</span><span class="sxs-lookup"><span data-stu-id="30ee7-159">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="30ee7-160">Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="30ee7-160">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="30ee7-161">Sie müssen dies für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf dem `getLocation API` Teams unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="30ee7-161">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="30ee7-162">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="30ee7-162">For example:</span></span>
 * <span data-ttu-id="30ee7-163">Um den Benutzer zum Zugriff auf seinen Standort aufforderen zu können, müssen Sie `getCurrentPosition()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="30ee7-163">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="30ee7-164">Um den Benutzer zum Zugriff auf seine Kamera auf dem Desktop oder Web aufforderen zu können, müssen Sie `getUserMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="30ee7-164">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="30ee7-165">Um das Bild auf mobilen Geräten zu erfassen, Teams Mobile beim Anruf um Erlaubnis `captureImage()` bitten:</span><span class="sxs-lookup"><span data-stu-id="30ee7-165">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="30ee7-166">Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="30ee7-166">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="30ee7-167">Um die Kamera oder den Fotokatalog zu verwenden, Teams Mobile die Berechtigung, wenn Sie `selectMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="30ee7-167">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="30ee7-168">Um das Mikrofon zu verwenden, Teams Mobile beim Anruf die Berechtigung `selectMedia()` ein:</span><span class="sxs-lookup"><span data-stu-id="30ee7-168">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="30ee7-169">Um den Benutzer zum Freigeben des Speicherorts auf der Kartenschnittstelle auffordern, fordert Teams Mobile beim Anruf die Berechtigung `getLocation()` an:</span><span class="sxs-lookup"><span data-stu-id="30ee7-169">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="30ee7-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="30ee7-170">Desktop</span></span>](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="30ee7-172">Mobil</span><span class="sxs-lookup"><span data-stu-id="30ee7-172">Mobile</span></span>](#tab/mobile)

   ![Eingabeaufforderung für Mobile Geräteberechtigungen für Registerkarten](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="30ee7-174">Berechtigungsverhalten in Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="30ee7-174">Permission behavior across login sessions</span></span>

<span data-ttu-id="30ee7-175">Geräteberechtigungen werden für jede Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="30ee7-175">Device permissions are stored for every login session.</span></span> <span data-ttu-id="30ee7-176">Wenn Sie sich bei einer anderen Instanz von Teams, z. B. auf einem anderen Computer, anmelden, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="30ee7-176">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="30ee7-177">Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen.</span><span class="sxs-lookup"><span data-stu-id="30ee7-177">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="30ee7-178">Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, Teams sie sich abmelden oder mandanten in Teams wechseln.</span><span class="sxs-lookup"><span data-stu-id="30ee7-178">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="30ee7-179">Wenn Sie den berechtigungen für systemeigene Geräte zustimmen, ist sie nur für Ihre _aktuelle Anmeldesitzung_ gültig.</span><span class="sxs-lookup"><span data-stu-id="30ee7-179">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-steps"></a><span data-ttu-id="30ee7-180">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="30ee7-180">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30ee7-181">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="30ee7-181">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="30ee7-182">Integrieren von QR- oder Barcodescannerfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="30ee7-182">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="30ee7-183">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="30ee7-183">Integrate location capabilities in Teams</span></span>](location-capability.md)
