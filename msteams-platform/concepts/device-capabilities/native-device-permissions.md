---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für Teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzufordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 37312912b4901cd31feeb9b0ee9bc76a3e03826a
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211618"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="345f5-104">Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="345f5-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="345f5-105">Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort erweitern.</span><span class="sxs-lookup"><span data-stu-id="345f5-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="345f5-106">In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="345f5-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> * <span data-ttu-id="345f5-107">Informationen zum Integrieren von Medienfunktionen in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren von Medienfunktionen.](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="345f5-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>
> * <span data-ttu-id="345f5-108">Informationen zum Integrieren der QR- oder Strichcodescannerfunktion in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren der QR- oder Strichcodescanner-Funktion in Teams.](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="345f5-108">To integrate QR or barcode scanner capability within your Microsoft Teams mobile app, see [Integrate QR or barcode scanner capability in Teams](qr-barcode-scanner-capability.md).</span></span>
> * <span data-ttu-id="345f5-109">Informationen zum Integrieren von Standortfunktionen in Ihre Microsoft Teams mobile App finden Sie unter [Integrieren von Standortfunktionen.](location-capability.md)</span><span class="sxs-lookup"><span data-stu-id="345f5-109">To integrate location capabilities within your Microsoft Teams mobile app, see [Integrate location capabilities](location-capability.md).</span></span>
> * <span data-ttu-id="345f5-110">Informationen zum Integrieren der Personenauswahlfunktion in Ihre Microsoft Teams mobilen App finden Sie unter Integrieren der [Personenauswahlfunktion in Teams.](people-picker-capability.md)</span><span class="sxs-lookup"><span data-stu-id="345f5-110">To integrate People Picker capability within your Microsoft Teams mobile app, see [Integrate People Picker capability in Teams](people-picker-capability.md).</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="345f5-111">Systemeigene Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="345f5-111">Native device permissions</span></span>

<span data-ttu-id="345f5-112">Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="345f5-112">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="345f5-113">Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messaging-Erweiterungen, ähnlich.</span><span class="sxs-lookup"><span data-stu-id="345f5-113">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="345f5-114">Der Benutzer muss zur Seite "Berechtigungen" in Teams Einstellungen wechseln, um Geräteberechtigungen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="345f5-114">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="345f5-115">Durch den Zugriff auf die Gerätefunktionen können Sie umfassendere Funktionen auf der Teams Plattform erstellen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="345f5-115">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="345f5-116">Erfassen und Anzeigen von Bildern.</span><span class="sxs-lookup"><span data-stu-id="345f5-116">Capture and view images.</span></span>
* <span data-ttu-id="345f5-117">Scannen Sie QR oder Barcode.</span><span class="sxs-lookup"><span data-stu-id="345f5-117">Scan QR or barcode.</span></span>
* <span data-ttu-id="345f5-118">Aufzeichnen und Freigeben kurzer Videos.</span><span class="sxs-lookup"><span data-stu-id="345f5-118">Record and share short videos.</span></span>
* <span data-ttu-id="345f5-119">Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="345f5-119">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="345f5-120">Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="345f5-120">Use the location information of the user to display relevant information.</span></span>

> [!NOTE]
> <span data-ttu-id="345f5-121">Derzeit unterstützt Teams keine Geräteberechtigungen für Apps mit mehreren Fenstern, Registerkarten und das Besprechungs-Sidepanel.</span><span class="sxs-lookup"><span data-stu-id="345f5-121">Currently, Teams does not support device permissions for multi window apps, tabs, and the meeting sidepanel.</span></span> 

## <a name="access-device-permissions"></a><span data-ttu-id="345f5-122">Zugreifen auf Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="345f5-122">Access device permissions</span></span>

<span data-ttu-id="345f5-123">Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) stellt die Tools bereit, die Ihre Teams mobile App benötigt, um auf die [Geräteberechtigungen](#manage-permissions) des Benutzers zuzugreifen und eine umfassendere Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="345f5-123">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="345f5-124">Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="345f5-124">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="345f5-125">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf dem Teams Desktopclient ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="345f5-125">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="345f5-126">Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Strichcodescanner nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="345f5-126">Currently, Microsoft Teams support for media capabilities and QR barcode scanner capability is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="345f5-127">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="345f5-127">Manage permissions</span></span>

<span data-ttu-id="345f5-128">Ein Benutzer kann Geräteberechtigungen in Teams Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps zulassen **oder** verweigern auswählt. </span><span class="sxs-lookup"><span data-stu-id="345f5-128">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="345f5-129">Desktop</span><span class="sxs-lookup"><span data-stu-id="345f5-129">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="345f5-130">Öffnen Sie Ihre Teams-App.</span><span class="sxs-lookup"><span data-stu-id="345f5-130">Open your Teams app.</span></span>
1. <span data-ttu-id="345f5-131">Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.</span><span class="sxs-lookup"><span data-stu-id="345f5-131">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="345f5-132">Wählen Sie im Dropdownmenü **Einstellungen**  >  **Berechtigungen** aus.</span><span class="sxs-lookup"><span data-stu-id="345f5-132">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="345f5-133">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="345f5-133">Select your desired settings.</span></span>

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="345f5-135">Mobil</span><span class="sxs-lookup"><span data-stu-id="345f5-135">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="345f5-136">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="345f5-136">Open Teams.</span></span>
1. <span data-ttu-id="345f5-137">Wechseln Sie zu **Einstellungen**  >  **App-Berechtigungen.**</span><span class="sxs-lookup"><span data-stu-id="345f5-137">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="345f5-138">Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="345f5-138">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="345f5-139">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="345f5-139">Select your desired settings.</span></span>

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="345f5-141">Angeben von Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="345f5-141">Specify permissions</span></span>

<span data-ttu-id="345f5-142">Aktualisieren Sie Ihre App, `manifest.json` indem Sie die folgenden fünf Eigenschaften hinzufügen und `devicePermissions` angeben, die Sie in Ihrer Anwendung verwenden:</span><span class="sxs-lookup"><span data-stu-id="345f5-142">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the following five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="345f5-143">Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen:</span><span class="sxs-lookup"><span data-stu-id="345f5-143">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="345f5-144">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="345f5-144">Property</span></span>      | <span data-ttu-id="345f5-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="345f5-145">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="345f5-146">Medien</span><span class="sxs-lookup"><span data-stu-id="345f5-146">media</span></span>         | <span data-ttu-id="345f5-147">Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf den Medienkatalog.</span><span class="sxs-lookup"><span data-stu-id="345f5-147">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="345f5-148">Geolocation</span><span class="sxs-lookup"><span data-stu-id="345f5-148">geolocation</span></span>   | <span data-ttu-id="345f5-149">Berechtigung zum Zurückgeben des Standorts des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="345f5-149">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="345f5-150">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="345f5-150">notifications</span></span> | <span data-ttu-id="345f5-151">Berechtigung zum Senden von Benutzerbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="345f5-151">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="345f5-152">Midi</span><span class="sxs-lookup"><span data-stu-id="345f5-152">midi</span></span>          | <span data-ttu-id="345f5-153">Berechtigung zum Senden und Empfangen von Midi-Informationen (Music Instrument Digital Interface) von einem digitalen Musik instrument.</span><span class="sxs-lookup"><span data-stu-id="345f5-153">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="345f5-154">openExternal</span><span class="sxs-lookup"><span data-stu-id="345f5-154">openExternal</span></span>  | <span data-ttu-id="345f5-155">Berechtigung zum Öffnen von Links in externen Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="345f5-155">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="345f5-156">Überprüfen von Berechtigungen aus Ihrer App</span><span class="sxs-lookup"><span data-stu-id="345f5-156">Check permissions from your app</span></span>

<span data-ttu-id="345f5-157">Überprüfen Sie nach dem Hinzufügen `devicePermissions` zum App-Manifest die Berechtigungen mithilfe der **HTML5-Berechtigungs-API,** ohne eine Aufforderung zu verursachen:</span><span class="sxs-lookup"><span data-stu-id="345f5-157">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="345f5-158">Verwenden von Teams-APIs zum Abrufen von Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="345f5-158">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="345f5-159">Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="345f5-159">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="345f5-160">Unterstützung für `camera` , und ist über `gallery` `microphone` [**selectMedia-API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="345f5-160">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true).</span></span> <span data-ttu-id="345f5-161">Verwenden Sie [**die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.</span><span class="sxs-lookup"><span data-stu-id="345f5-161">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="345f5-162">Die Unterstützung für `location` ist über [**die getLocation-API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="345f5-162">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="345f5-163">Sie müssen dies für den Standort verwenden, da die `getLocation API` HTML5-Geolocation-API derzeit nicht vollständig auf Teams Desktopclient unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="345f5-163">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="345f5-164">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="345f5-164">For example:</span></span>
 * <span data-ttu-id="345f5-165">Um den Benutzer aufzufordern, auf seine Position zuzugreifen, müssen Sie Folgendes `getCurrentPosition()` aufrufen:</span><span class="sxs-lookup"><span data-stu-id="345f5-165">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="345f5-166">Um den Benutzer aufzufordern, auf seine Kamera auf dem Desktop oder im Web zuzugreifen, müssen Sie `getUserMedia()` Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="345f5-166">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="345f5-167">Um das Bild auf mobilgeräten zu erfassen, fordert Teams Mobile beim Anruf die Berechtigung `captureImage()` an:</span><span class="sxs-lookup"><span data-stu-id="345f5-167">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="345f5-168">Benachrichtigungen fordern den Benutzer beim Aufrufen `requestPermission()` an:</span><span class="sxs-lookup"><span data-stu-id="345f5-168">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="345f5-169">Um die Kamera zu verwenden oder auf die Fotogalerie zuzugreifen, fragt Teams Mobiltelefon beim Anruf nach der `selectMedia()` Berechtigung:</span><span class="sxs-lookup"><span data-stu-id="345f5-169">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="345f5-170">Um das Mikrofon zu verwenden, fordert Teams Mobiltelefon beim Anruf die Berechtigung `selectMedia()` an:</span><span class="sxs-lookup"><span data-stu-id="345f5-170">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="345f5-171">Um den Benutzer aufzufordern, den Standort auf der Kartenoberfläche freizugeben, fordert Teams Mobile beim Aufrufen die Berechtigung `getLocation()` an:</span><span class="sxs-lookup"><span data-stu-id="345f5-171">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="345f5-172">Desktop</span><span class="sxs-lookup"><span data-stu-id="345f5-172">Desktop</span></span>](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="345f5-174">Mobil</span><span class="sxs-lookup"><span data-stu-id="345f5-174">Mobile</span></span>](#tab/mobile)

   ![Registerkarten - Eingabeaufforderung für Berechtigungen für mobile Geräte](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="345f5-176">Berechtigungsverhalten über Anmeldesitzungen hinweg</span><span class="sxs-lookup"><span data-stu-id="345f5-176">Permission behavior across login sessions</span></span>

<span data-ttu-id="345f5-177">Geräteberechtigungen werden für jede Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="345f5-177">Device permissions are stored for every login session.</span></span> <span data-ttu-id="345f5-178">Wenn Sie sich also bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="345f5-178">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="345f5-179">Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen.</span><span class="sxs-lookup"><span data-stu-id="345f5-179">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="345f5-180">Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.</span><span class="sxs-lookup"><span data-stu-id="345f5-180">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="345f5-181">Wenn Sie den systemeigenen Geräteberechtigungen zustimmen, ist sie nur für Ihre _aktuelle_ Anmeldesitzung gültig.</span><span class="sxs-lookup"><span data-stu-id="345f5-181">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-steps"></a><span data-ttu-id="345f5-182">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="345f5-182">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="345f5-183">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="345f5-183">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="345f5-184">Integrieren von QR- oder Strichcodescannern in Teams</span><span class="sxs-lookup"><span data-stu-id="345f5-184">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="345f5-185">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="345f5-185">Integrate location capabilities in Teams</span></span>](location-capability.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="345f5-186">Integrieren der Personenauswahlfunktion in Teams</span><span class="sxs-lookup"><span data-stu-id="345f5-186">Integrate People Picker capability in Teams</span></span>](people-picker-capability.md)
