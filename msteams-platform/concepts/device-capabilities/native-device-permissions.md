---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für die Funktionen von Teams-Apps
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features an fordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
ms.topic: how-to
ms.openlocfilehash: 0343754eacbb6088a3e44fa5df8ec90e3b10b076
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231610"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a><span data-ttu-id="73c1d-104">Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="73c1d-104">Request device permissions for your Microsoft Teams app</span></span>

<span data-ttu-id="73c1d-105">Sie können Ihre Teams-App um systemeigene Gerätefunktionen erweitern, z. B. Kamera, Mikrofon und Position.</span><span class="sxs-lookup"><span data-stu-id="73c1d-105">You can enrich your Teams app with native device capabilities, such as camera, microphone, and location.</span></span> <span data-ttu-id="73c1d-106">In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="73c1d-106">This document guides you on how to request user consent and access the native device permissions.</span></span>

> [!NOTE]
> <span data-ttu-id="73c1d-107">Informationen zum Integrieren von Medienfunktionen in Ihre mobile Microsoft Teams-App finden Sie [unter "Integrieren von Medienfunktionen".](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="73c1d-107">To integrate media capabilities within your Microsoft Teams mobile app, see [Integrate media capabilities](mobile-camera-image-permissions.md).</span></span>

## <a name="native-device-permissions"></a><span data-ttu-id="73c1d-108">Systemeigene Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="73c1d-108">Native device permissions</span></span>

<span data-ttu-id="73c1d-109">Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="73c1d-109">You must request the device permissions to access native device capabilities.</span></span> <span data-ttu-id="73c1d-110">Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen, ähnlich.</span><span class="sxs-lookup"><span data-stu-id="73c1d-110">The device permissions work similarly for all app constructs, such as tabs, task modules, or messaging extensions.</span></span> <span data-ttu-id="73c1d-111">Der Benutzer muss zur Berechtigungsseite in den Einstellungen von Teams wechseln, um Geräteberechtigungen zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="73c1d-111">The user must go to the permissions page in Teams settings to manage device permissions.</span></span>
<span data-ttu-id="73c1d-112">Durch den Zugriff auf die Gerätefunktionen können Sie vielfältigere Funktionen auf der Teams-Plattform erstellen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="73c1d-112">By accessing the device capabilities, you can build richer experiences on the Teams platform, such as:</span></span>
* <span data-ttu-id="73c1d-113">Erfassen und Anzeigen von Bildern.</span><span class="sxs-lookup"><span data-stu-id="73c1d-113">Capture and view images.</span></span>
* <span data-ttu-id="73c1d-114">Aufzeichnen und Freigeben kurzer Videos.</span><span class="sxs-lookup"><span data-stu-id="73c1d-114">Record and share short videos.</span></span>
* <span data-ttu-id="73c1d-115">Notieren Sie Audionotizen, und speichern Sie sie für die spätere Verwendung.</span><span class="sxs-lookup"><span data-stu-id="73c1d-115">Record audio memos and save them for later use.</span></span>
* <span data-ttu-id="73c1d-116">Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="73c1d-116">Use the location information of the user to display relevant information.</span></span>

## <a name="access-device-permissions"></a><span data-ttu-id="73c1d-117">Zugreifen auf Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="73c1d-117">Access device permissions</span></span>

<span data-ttu-id="73c1d-118">Das [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) von Microsoft Teams stellt die Tools bereit, die Für Ihre mobile Microsoft Teams-App erforderlich sind, um auf die Geräteberechtigungen des Benutzers zu zugreifen und eine reichhaltigere Benutzererfahrung zu schaffen. [](#manage-permissions)</span><span class="sxs-lookup"><span data-stu-id="73c1d-118">The [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) provides the tools necessary for your Teams mobile app to access the user’s [device permissions](#manage-permissions) and build a richer experience.</span></span>

<span data-ttu-id="73c1d-119">Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="73c1d-119">While access to these features is standard in modern web browsers, you must inform Teams about the features you use by updating your app manifest.</span></span> <span data-ttu-id="73c1d-120">Dieses Update ermöglicht es Ihnen, Berechtigungen zu fordern, während Ihre App auf dem Teams-Desktopclient ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="73c1d-120">This update allows you to ask for permissions while your app runs on the Teams desktop client.</span></span>

> [!NOTE] 
> <span data-ttu-id="73c1d-121">Derzeit ist die Unterstützung von Medienfunktionen von Microsoft Teams nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="73c1d-121">Currently, Microsoft Teams support for media capabilities is only available for mobile clients.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="73c1d-122">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="73c1d-122">Manage permissions</span></span>

<span data-ttu-id="73c1d-123">Ein Benutzer kann Geräteberechtigungen in den Einstellungen von Teams verwalten, indem er die Berechtigung **"Zulassen"** oder "Verweigern" **für** bestimmte Apps aus.</span><span class="sxs-lookup"><span data-stu-id="73c1d-123">A user can manage device permissions in Teams settings by selecting **Allow** or **Deny** permissions to specific apps.</span></span>
 
# <a name="desktop"></a>[<span data-ttu-id="73c1d-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="73c1d-124">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="73c1d-125">Öffnen Sie Ihre Teams-App.</span><span class="sxs-lookup"><span data-stu-id="73c1d-125">Open your Teams app.</span></span>
1. <span data-ttu-id="73c1d-126">Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.</span><span class="sxs-lookup"><span data-stu-id="73c1d-126">Select your profile icon in the upper right corner of the window.</span></span>
1. <span data-ttu-id="73c1d-127">Wählen **Sie im**  >   Dropdownmenü "Einstellungsberechtigungen" aus.</span><span class="sxs-lookup"><span data-stu-id="73c1d-127">Select **Settings** > **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="73c1d-128">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="73c1d-128">Select your desired settings.</span></span>

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="73c1d-130">Mobil</span><span class="sxs-lookup"><span data-stu-id="73c1d-130">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="73c1d-131">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="73c1d-131">Open Teams.</span></span>
1. <span data-ttu-id="73c1d-132">Wechseln Sie zu   >  **"Einstellungen-App-Berechtigungen".**</span><span class="sxs-lookup"><span data-stu-id="73c1d-132">Go to **Settings** > **App Permissions**.</span></span>
1. <span data-ttu-id="73c1d-133">Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="73c1d-133">Select the app for which you need to choose the settings.</span></span>
1. <span data-ttu-id="73c1d-134">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="73c1d-134">Select your desired settings.</span></span>

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a><span data-ttu-id="73c1d-136">Angeben von Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="73c1d-136">Specify permissions</span></span>

<span data-ttu-id="73c1d-137">Aktualisieren Sie die App, indem Sie die fünf Eigenschaften hinzufügen und angeben, die `manifest.json` Sie in Ihrer Anwendung `devicePermissions` verwenden:</span><span class="sxs-lookup"><span data-stu-id="73c1d-137">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties that you use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="73c1d-138">Mit jeder Eigenschaft können Sie den Benutzer bitten, seine Zustimmung einzuholen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-138">Each property allows you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="73c1d-139">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="73c1d-139">Property</span></span>      | <span data-ttu-id="73c1d-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="73c1d-140">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="73c1d-141">media</span><span class="sxs-lookup"><span data-stu-id="73c1d-141">media</span></span>         | <span data-ttu-id="73c1d-142">Berechtigung zur Verwendung der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf die Mediengalerie.</span><span class="sxs-lookup"><span data-stu-id="73c1d-142">Permission to use the camera, microphone, speakers, and access media gallery.</span></span> |
| <span data-ttu-id="73c1d-143">geolocation</span><span class="sxs-lookup"><span data-stu-id="73c1d-143">geolocation</span></span>   | <span data-ttu-id="73c1d-144">Berechtigung zum Zurückgeben des Standorts des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="73c1d-144">Permission to return the user's location.</span></span>      |
| <span data-ttu-id="73c1d-145">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="73c1d-145">notifications</span></span> | <span data-ttu-id="73c1d-146">Berechtigung zum Senden von Benutzerbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="73c1d-146">Permission to send the user notifications.</span></span>      |
| <span data-ttu-id="73c1d-147">midi</span><span class="sxs-lookup"><span data-stu-id="73c1d-147">midi</span></span>          | <span data-ttu-id="73c1d-148">Berechtigung zum Senden und Empfangen von Musik instrument digital Interface (MIDI)-Informationen von einem digitalen Musikgerät.</span><span class="sxs-lookup"><span data-stu-id="73c1d-148">Permission to send and receive  Musical Instrument Digital Interface (MIDI) information from a digital musical instrument.</span></span>   |
| <span data-ttu-id="73c1d-149">openExternal</span><span class="sxs-lookup"><span data-stu-id="73c1d-149">openExternal</span></span>  | <span data-ttu-id="73c1d-150">Berechtigung zum Öffnen von Links in externen Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="73c1d-150">Permission to open links in external applications.</span></span>  |

## <a name="check-permissions-from-your-app"></a><span data-ttu-id="73c1d-151">Überprüfen von Berechtigungen aus Ihrer App</span><span class="sxs-lookup"><span data-stu-id="73c1d-151">Check permissions from your app</span></span>

<span data-ttu-id="73c1d-152">Überprüfen Sie nach dem Hinzufügen zu Ihrem App-Manifest die Berechtigungen mithilfe der `devicePermissions` **HTML5-Berechtigungs-API,** ohne eine Eingabeaufforderung zu verursachen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-152">After adding `devicePermissions` to your app manifest, check permissions using the **HTML5 permissions API** without causing a prompt:</span></span>

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

## <a name="use-teams-apis-to-get-device-permissions"></a><span data-ttu-id="73c1d-153">Verwenden von Teams-APIs zum Erhalten von Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="73c1d-153">Use Teams APIs to get device permissions</span></span>

<span data-ttu-id="73c1d-154">Nutzen Sie entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen einzuholen.</span><span class="sxs-lookup"><span data-stu-id="73c1d-154">Leverage appropriate HTML5 or Teams API, to display a prompt for getting consent to access device permissions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="73c1d-155">Unterstützung für `camera` , und wird über `gallery` `microphone` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="73c1d-155">Support for `camera`, `gallery`, and `microphone` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="73c1d-156">Verwenden [**Sie die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.</span><span class="sxs-lookup"><span data-stu-id="73c1d-156">Use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) for a single image capture.</span></span>
> * <span data-ttu-id="73c1d-157">Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="73c1d-157">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="73c1d-158">Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf dem Teams-Desktopclient unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="73c1d-158">You must use this `getLocation API` for location, as HTML5 geolocation API is currently not fully supported on Teams desktop client.</span></span>

<span data-ttu-id="73c1d-159">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="73c1d-159">For example:</span></span>
 * <span data-ttu-id="73c1d-160">Um den Benutzer zum Zugriff auf seinen Standort aufforderen zu können, müssen Sie dies `getCurrentPosition()` aufrufen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-160">To prompt the user to access their location you must call `getCurrentPosition()`:</span></span>

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * <span data-ttu-id="73c1d-161">Um den Benutzer auf dem Desktop oder im Web zum Zugriff auf seine Kamera aufforderen zu können, müssen Sie dies `getUserMedia()` aufrufen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-161">To prompt the user to access their camera on desktop or web you must call `getUserMedia()`:</span></span>

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * <span data-ttu-id="73c1d-162">Um das Bild auf mobilen Geräten zu erfassen, fordert Teams Mobile beim Anruf die Berechtigung `captureImage()` an:</span><span class="sxs-lookup"><span data-stu-id="73c1d-162">To capture the image on mobile, Teams mobile asks for permission when you call `captureImage()`:</span></span>

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * <span data-ttu-id="73c1d-163">Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-163">Notifications will prompt the user when you call `requestPermission()`:</span></span>

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* <span data-ttu-id="73c1d-164">Um die Kamera oder den Zugriff auf die Fotogalerie zu verwenden, fordert Teams Mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-164">To use the camera or access photo gallery, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* <span data-ttu-id="73c1d-165">Um das Mikrofon zu verwenden, fordert Teams Mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-165">To use the microphone, Teams mobile asks permission when you call `selectMedia()`:</span></span>

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* <span data-ttu-id="73c1d-166">Um den Benutzer zur Freigabe des Standorts auf der Kartenoberfläche auffordern, fordert Teams Mobile die Berechtigung an, wenn Sie `getLocation()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="73c1d-166">To prompt the user to share location on the map interface, Teams mobile asks permission when you call `getLocation()`:</span></span>

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[<span data-ttu-id="73c1d-167">Desktop</span><span class="sxs-lookup"><span data-stu-id="73c1d-167">Desktop</span></span>](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräte](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="73c1d-169">Mobil</span><span class="sxs-lookup"><span data-stu-id="73c1d-169">Mobile</span></span>](#tab/mobile)

   ![Eingabeaufforderung für Registerkarten für Mobilgeräte](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="73c1d-171">Berechtigungsverhalten in allen Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="73c1d-171">Permission behavior across login sessions</span></span>

<span data-ttu-id="73c1d-172">Geräteberechtigungen werden für jede Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="73c1d-172">Device permissions are stored for every login session.</span></span> <span data-ttu-id="73c1d-173">Wenn Sie sich bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus Ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="73c1d-173">It means that if you sign in to another instance of Teams, for example, on another computer, your device permissions from your previous sessions are not available.</span></span> <span data-ttu-id="73c1d-174">Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen.</span><span class="sxs-lookup"><span data-stu-id="73c1d-174">Therefore, you must re-consent to device permissions for the new session.</span></span> <span data-ttu-id="73c1d-175">Das bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.</span><span class="sxs-lookup"><span data-stu-id="73c1d-175">It also means, if you sign out of Teams or switch tenants in Teams, your device permissions are deleted from the previous login session.</span></span>  

> [!NOTE]
> <span data-ttu-id="73c1d-176">Wenn Sie den systemeigenen Geräteberechtigungen zustimmen, ist sie nur für Ihre _aktuelle Anmeldesitzung_ gültig.</span><span class="sxs-lookup"><span data-stu-id="73c1d-176">When you consent to the native device permissions, it is valid only for your _current_ login session.</span></span>

## <a name="next-step"></a><span data-ttu-id="73c1d-177">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="73c1d-177">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73c1d-178">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="73c1d-178">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)
