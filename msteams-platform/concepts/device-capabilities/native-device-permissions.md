---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für Teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzufordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 920ab47a60340fd9a14e4f5dfb2e39a8ad8f3a89
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994350"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="1d1df-104">Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="1d1df-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="1d1df-105">Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort erweitern.</span><span class="sxs-lookup"><span data-stu-id="1d1df-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="1d1df-106">In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="1d1df-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> * <span data-ttu-id="1d1df-107">Informationen zum Integrieren von Medienfunktionen in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren von Medienfunktionen.](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="1d1df-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>
> * <span data-ttu-id="1d1df-108">Informationen zum Integrieren der QR- oder Strichcodescannerfunktion in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren der QR- oder Strichcodescanner-Funktion in Teams.](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="1d1df-108">To integrate QR or barcode scanner capability within your Microsoft Teams mobile app, see [Integrate QR or barcode scanner capability in Teams](qr-barcode-scanner-capability.md).</span></span>
> * <span data-ttu-id="1d1df-109">Informationen zum Integrieren von Standortfunktionen in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren von Standortfunktionen.](location-capability.md)</span><span class="sxs-lookup"><span data-stu-id="1d1df-109">To integrate location capabilities within your Microsoft Teams mobile app, see [Integrate location capabilities](location-capability.md).</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="1d1df-110">Systemeigene Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="1d1df-110">Native device permissions</span></span>

<span data-ttu-id="1d1df-111">Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="1d1df-111">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="1d1df-112">Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messaging-Erweiterungen, ähnlich.</span><span class="sxs-lookup"><span data-stu-id="1d1df-112">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="1d1df-113">Der Benutzer muss zur Seite "Berechtigungen" in Teams Einstellungen wechseln, um Geräteberechtigungen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="1d1df-113">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="1d1df-114">Durch den Zugriff auf die Gerätefunktionen können Sie umfassendere Funktionen auf der Teams Plattform erstellen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="1d1df-114">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="1d1df-115">Erfassen und Anzeigen von Bildern.</span><span class="sxs-lookup"><span data-stu-id="1d1df-115">Capture and view images.</span></span>
* <span data-ttu-id="1d1df-116">Scannen Sie QR oder Barcode.</span><span class="sxs-lookup"><span data-stu-id="1d1df-116">Scan QR or barcode.</span></span>
* <span data-ttu-id="1d1df-117">Aufzeichnen und Freigeben kurzer Videos.</span><span class="sxs-lookup"><span data-stu-id="1d1df-117">Record and share short videos.</span></span>
* <span data-ttu-id="1d1df-118">Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="1d1df-118">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="1d1df-119">Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-119">Use the location information of the user to display relevant information.</span></span>

> [!NOTE]
> <span data-ttu-id="1d1df-120">Derzeit unterstützt Teams keine Geräteberechtigungen für Apps, Registerkarten und das Besprechungs-Sidepanel.</span><span class="sxs-lookup"><span data-stu-id="1d1df-120">Currently, Teams does not support device permissions for multi window apps, tabs, and the meeting sidepanel.</span></span> 

## <a name="access-device-permissions"></a><span data-ttu-id="1d1df-121">Zugreifen auf Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="1d1df-121">Access device permissions</span></span>

<span data-ttu-id="1d1df-122">Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) stellt die Tools bereit, die Für Ihre Teams mobile App erforderlich sind, um auf die [Geräteberechtigungen](#manage-permissions) des Benutzers zuzugreifen und eine umfassendere Oberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-122">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="1d1df-123">Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1d1df-123">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="1d1df-124">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf dem Teams Desktopclient ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1d1df-124">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="1d1df-125">Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Strichcodescanner nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1d1df-125">Currently, Microsoft Teams support for media capabilities and QR barcode scanner capability is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="1d1df-126">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="1d1df-126">Manage permissions</span></span>

<span data-ttu-id="1d1df-127">Ein Benutzer kann Geräteberechtigungen in Teams Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps **zulassen** oder verweigern auswählt. </span><span class="sxs-lookup"><span data-stu-id="1d1df-127">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="1d1df-128">Desktop</span><span class="sxs-lookup"><span data-stu-id="1d1df-128">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="1d1df-129">Öffnen Sie Ihre Teams-App.</span><span class="sxs-lookup"><span data-stu-id="1d1df-129">Open your Teams app.</span></span>
1. <span data-ttu-id="1d1df-130">Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.</span><span class="sxs-lookup"><span data-stu-id="1d1df-130">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="1d1df-131">Wählen Sie im Dropdownmenü **Einstellungen**  >  **Berechtigungen** aus.</span><span class="sxs-lookup"><span data-stu-id="1d1df-131">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="1d1df-132">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="1d1df-132">Select your desired settings.</span></span>

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="1d1df-134">Mobil</span><span class="sxs-lookup"><span data-stu-id="1d1df-134">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="1d1df-135">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="1d1df-135">Open Teams.</span></span>
1. <span data-ttu-id="1d1df-136">Wechseln Sie zu **Einstellungen**  >  **App-Berechtigungen.**</span><span class="sxs-lookup"><span data-stu-id="1d1df-136">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="1d1df-137">Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-137">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="1d1df-138">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="1d1df-138">Select your desired settings.</span></span>

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="1d1df-140">Angeben von Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="1d1df-140">Specify permissions</span></span>

<span data-ttu-id="1d1df-141">Aktualisieren Sie Ihre App, `manifest.json` indem Sie die fünf Eigenschaften hinzufügen und `devicePermissions` angeben, die Sie in Ihrer Anwendung verwenden:</span><span class="sxs-lookup"><span data-stu-id="1d1df-141">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="1d1df-142">Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen:</span><span class="sxs-lookup"><span data-stu-id="1d1df-142">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="1d1df-143">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1d1df-143">Property</span></span>      | <span data-ttu-id="1d1df-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1d1df-144">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="1d1df-145">Medien</span><span class="sxs-lookup"><span data-stu-id="1d1df-145">media</span></span>         | <span data-ttu-id="1d1df-146">Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf den Medienkatalog.</span><span class="sxs-lookup"><span data-stu-id="1d1df-146">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="1d1df-147">Geolocation</span><span class="sxs-lookup"><span data-stu-id="1d1df-147">geolocation</span></span>   | <span data-ttu-id="1d1df-148">Berechtigung zum Zurückgeben des Standorts des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="1d1df-148">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="1d1df-149">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="1d1df-149">notifications</span></span> | <span data-ttu-id="1d1df-150">Berechtigung zum Senden von Benutzerbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-150">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="1d1df-151">Midi</span><span class="sxs-lookup"><span data-stu-id="1d1df-151">midi</span></span>          | <span data-ttu-id="1d1df-152">Berechtigung zum Senden und Empfangen von Midi-Informationen (Music Instrument Digital Interface) von einem digitalen Musik instrument.</span><span class="sxs-lookup"><span data-stu-id="1d1df-152">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="1d1df-153">openExternal</span><span class="sxs-lookup"><span data-stu-id="1d1df-153">openExternal</span></span>  | <span data-ttu-id="1d1df-154">Berechtigung zum Öffnen von Links in externen Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-154">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="1d1df-155">Überprüfen von Berechtigungen aus Ihrer App</span><span class="sxs-lookup"><span data-stu-id="1d1df-155">Check permissions from your app</span></span>

<span data-ttu-id="1d1df-156">Überprüfen Sie nach dem Hinzufügen `devicePermissions` zum App-Manifest die Berechtigungen mithilfe der **HTML5-Berechtigungs-API,** ohne eine Aufforderung zu verursachen:</span><span class="sxs-lookup"><span data-stu-id="1d1df-156">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="1d1df-157">Verwenden von Teams-APIs zum Abrufen von Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="1d1df-157">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="1d1df-158">Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-158">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="1d1df-159">Unterstützung für `camera` , und ist über `gallery` `microphone` [**selectMedia-API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="1d1df-159">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="1d1df-160">Verwenden Sie [**die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.</span><span class="sxs-lookup"><span data-stu-id="1d1df-160">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="1d1df-161">Die Unterstützung für `location` ist über [**die getLocation-API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="1d1df-161">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="1d1df-162">Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API auf Teams Desktopclient derzeit nicht vollständig unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="1d1df-162">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="1d1df-163">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1d1df-163">For example:</span></span>
 * <span data-ttu-id="1d1df-164">Um den Benutzer aufzufordern, auf seine Position zuzugreifen, müssen Sie Folgendes `getCurrentPosition()` aufrufen:</span><span class="sxs-lookup"><span data-stu-id="1d1df-164">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="1d1df-165">Um den Benutzer aufzufordern, auf seine Kamera auf dem Desktop oder im Web zuzugreifen, müssen Sie `getUserMedia()` Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="1d1df-165">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="1d1df-166">Um das Bild auf mobilen Geräten zu erfassen, fragt Teams Mobiltelefon beim Anruf nach der `captureImage()` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="1d1df-166">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="1d1df-167">Benachrichtigungen fordern den Benutzer beim Aufrufen `requestPermission()` an:</span><span class="sxs-lookup"><span data-stu-id="1d1df-167">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="1d1df-168">Um die Kamera zu verwenden oder auf die Fotogalerie zuzugreifen, fordert Teams Mobiltelefon beim Anruf die Berechtigung `selectMedia()` an:</span><span class="sxs-lookup"><span data-stu-id="1d1df-168">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="1d1df-169">Um das Mikrofon zu verwenden, fordert Teams Mobiltelefon beim Anruf die Berechtigung `selectMedia()` an:</span><span class="sxs-lookup"><span data-stu-id="1d1df-169">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="1d1df-170">Um den Benutzer aufzufordern, den Standort auf der Kartenoberfläche freizugeben, fragt Teams Mobile beim Aufrufen die `getLocation()` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="1d1df-170">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="1d1df-171">Desktop</span><span class="sxs-lookup"><span data-stu-id="1d1df-171">Desktop</span></span>](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="1d1df-173">Mobil</span><span class="sxs-lookup"><span data-stu-id="1d1df-173">Mobile</span></span>](#tab/mobile)

   ![Registerkarten - Eingabeaufforderung für Berechtigungen für mobile Geräte](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="1d1df-175">Berechtigungsverhalten über Anmeldesitzungen hinweg</span><span class="sxs-lookup"><span data-stu-id="1d1df-175">Permission behavior across login sessions</span></span>

<span data-ttu-id="1d1df-176">Geräteberechtigungen werden für jede Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1d1df-176">Device permissions are stored for every login session.</span></span> <span data-ttu-id="1d1df-177">Wenn Sie sich also bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus Ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1d1df-177">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="1d1df-178">Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen.</span><span class="sxs-lookup"><span data-stu-id="1d1df-178">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="1d1df-179">Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.</span><span class="sxs-lookup"><span data-stu-id="1d1df-179">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="1d1df-180">Wenn Sie den systemeigenen Geräteberechtigungen zustimmen, ist sie nur für Ihre _aktuelle_ Anmeldesitzung gültig.</span><span class="sxs-lookup"><span data-stu-id="1d1df-180">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1d1df-181">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="1d1df-181">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d1df-182">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="1d1df-182">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d1df-183">Integrieren von QR- oder Strichcodescannern in Teams</span><span class="sxs-lookup"><span data-stu-id="1d1df-183">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d1df-184">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="1d1df-184">Integrate location capabilities in Teams</span></span>](location-capability.md)
