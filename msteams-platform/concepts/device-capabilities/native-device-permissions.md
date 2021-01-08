---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: 6be183d2610616f3bd3bdf32554976322193c132
ms.sourcegitcommit: d0e71ea63af2f67eba75ba283ec46cc7cdf87d75
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "49731979"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="8be11-104">Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8be11-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="8be11-105">Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die Zugriff auf systemeigene Gerätefunktionen benötigen, wie:</span><span class="sxs-lookup"><span data-stu-id="8be11-105">You might want to enrich your tab with features that require access to native device functionality like:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="8be11-106">Kamera</span><span class="sxs-lookup"><span data-stu-id="8be11-106">Camera</span></span>
> * <span data-ttu-id="8be11-107">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="8be11-107">Microphone</span></span>
> * <span data-ttu-id="8be11-108">Ort</span><span class="sxs-lookup"><span data-stu-id="8be11-108">Location</span></span>
> * <span data-ttu-id="8be11-109">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8be11-109">Notifications</span></span>

[!Note] <span data-ttu-id="8be11-110">Um die Kamera-und Bildfunktionen in Ihre Microsoft Teams-Mobile App zu integrieren, referieren Sie die [Kamera-und Bildfunktionen in Microsoft Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="8be11-110">To integrate camera and image capabilities within your Microsoft Teams mobile app, refer [Camera and image capabilities in Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="8be11-111">Derzeit unterstützt Teams Mobile Clients nur den Zugriff auf `camera` , `gallery` , `mic` und `location` über Native Gerätefunktionen und steht in allen APP-Konstrukten einschließlich Registerkarten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8be11-111">At present, Teams mobile client only supports access to `camera`, `gallery`, `mic`, and `location` through native device capabilities and is available on all app constructs including tabs.</span></span> </br>
> * <span data-ttu-id="8be11-112">Unterstützung für `camera` , `gallery` und `mic` wird über die [**selectMedia-API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="8be11-112">Support for `camera`, `gallery`, and `mic` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="8be11-113">Für die Einzelbild Erfassung können Sie die [**captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true)verwenden.</span><span class="sxs-lookup"><span data-stu-id="8be11-113">For single image capture you may use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span></span>
> * <span data-ttu-id="8be11-114">Die Unterstützung für `location` ist über die [**getLocation-API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="8be11-114">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="8be11-115">Es wird empfohlen, diese API zu verwenden, da die [**Geolocation-API**](../../resources/schema/manifest-schema.md#devicepermissions) derzeit nicht vollständig auf allen Desktop-Clients unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="8be11-115">It's recommended you use this API as [**geolocation API**](../../resources/schema/manifest-schema.md#devicepermissions) is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="8be11-116">Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="8be11-116">Device permissions</span></span>

<span data-ttu-id="8be11-117">Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="8be11-117">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="8be11-118">Aufzeichnen und Freigeben von kurzen Videos</span><span class="sxs-lookup"><span data-stu-id="8be11-118">Record and share short videos</span></span>
* <span data-ttu-id="8be11-119">Kurze audiomemos aufzeichnen und später speichern</span><span class="sxs-lookup"><span data-stu-id="8be11-119">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="8be11-120">Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen</span><span class="sxs-lookup"><span data-stu-id="8be11-120">Use user location information to display relevant information</span></span>

<span data-ttu-id="8be11-121">Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern Standard ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8be11-121">While access to these features is standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="8be11-122">Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.</span><span class="sxs-lookup"><span data-stu-id="8be11-122">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="8be11-123">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="8be11-123">Manage permissions</span></span>

# <a name="desktop"></a>[<span data-ttu-id="8be11-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="8be11-124">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="8be11-125">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="8be11-125">Open Teams.</span></span>
1. <span data-ttu-id="8be11-126">Wählen Sie in der oberen rechten Ecke des Fensters Ihr Profilsymbol aus.</span><span class="sxs-lookup"><span data-stu-id="8be11-126">In the upper right corner of the window, select your profile icon.</span></span>
1. <span data-ttu-id="8be11-127">Wählen Sie  ->  im Dropdownmenü Einstellungen **Berechtigungen** aus.</span><span class="sxs-lookup"><span data-stu-id="8be11-127">Select **Settings** -> **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="8be11-128">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="8be11-128">Choose your desired settings.</span></span>

![Bildschirm "Geräte Berechtigungen-Desktopeinstellungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="8be11-130">Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="8be11-130">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="8be11-131">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="8be11-131">Open Teams.</span></span>
1. <span data-ttu-id="8be11-132">Wechseln Sie zu **Einstellungen**  ->  **App-Berechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="8be11-132">Go to **Settings** -> **App Permissions**.</span></span>
1. <span data-ttu-id="8be11-133">Wählen Sie die APP aus, für die Sie Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="8be11-133">Select the app you need to choose settings for.</span></span>
1. <span data-ttu-id="8be11-134">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="8be11-134">Choose your desired settings.</span></span>

![Bildschirm mit den mobilen Einstellungen für Geräte Berechtigungen](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a><span data-ttu-id="8be11-136">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8be11-136">Properties</span></span>

<span data-ttu-id="8be11-137">Aktualisieren Sie Ihre APP, `manifest.json` indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="8be11-137">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```
> [!Note]
>
> <span data-ttu-id="8be11-138">Medien werden auch für Kamera Berechtigungen auf mobilen Geräten verwendet.</span><span class="sxs-lookup"><span data-stu-id="8be11-138">Media is also used for camera permissions on mobile.</span></span>

<span data-ttu-id="8be11-139">Mit jeder Eigenschaft können Sie den Benutzer auffordern, nach seiner Zustimmung zu Fragen:</span><span class="sxs-lookup"><span data-stu-id="8be11-139">Each property will allow you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="8be11-140">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8be11-140">Property</span></span>      | <span data-ttu-id="8be11-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8be11-141">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="8be11-142">Medien</span><span class="sxs-lookup"><span data-stu-id="8be11-142">media</span></span>         | <span data-ttu-id="8be11-143">Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs Medien Katalogs</span><span class="sxs-lookup"><span data-stu-id="8be11-143">permission to use the camera, microphone, speakers, and access media gallery</span></span> |
| <span data-ttu-id="8be11-144">Geolocation</span><span class="sxs-lookup"><span data-stu-id="8be11-144">geolocation</span></span>   | <span data-ttu-id="8be11-145">Berechtigung zum Zurückgeben des Standorts des Benutzers</span><span class="sxs-lookup"><span data-stu-id="8be11-145">permission to return the user's location</span></span>      |
| <span data-ttu-id="8be11-146">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8be11-146">notifications</span></span> | <span data-ttu-id="8be11-147">Berechtigung zum Senden der Benutzer Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8be11-147">permission to send the user notifications</span></span>      |
| <span data-ttu-id="8be11-148">MIDI</span><span class="sxs-lookup"><span data-stu-id="8be11-148">midi</span></span>          | <span data-ttu-id="8be11-149">Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument</span><span class="sxs-lookup"><span data-stu-id="8be11-149">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="8be11-150">openextern</span><span class="sxs-lookup"><span data-stu-id="8be11-150">openExternal</span></span>  | <span data-ttu-id="8be11-151">Berechtigung zum Öffnen von Links in externen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="8be11-151">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="8be11-152">Überprüfen von Berechtigungen auf der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="8be11-152">Checking permissions from your tab</span></span>

<span data-ttu-id="8be11-153">Nachdem Sie Ihrem App-Manifest hinzugefügt haben `devicePermissions` , können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="8be11-153">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="8be11-154">Auffordern des Benutzers</span><span class="sxs-lookup"><span data-stu-id="8be11-154">Prompting the user</span></span>

<span data-ttu-id="8be11-155">Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-oder Teams-API nutzen.</span><span class="sxs-lookup"><span data-stu-id="8be11-155">To show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 or Teams API.</span></span> 

<span data-ttu-id="8be11-156">Um beispielsweise den Benutzer aufzufordern, auf seinen Standort zuzugreifen, müssen Sie `getCurrentPosition` Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="8be11-156">For example, to prompt the user to access their location you need to call `getCurrentPosition`:</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="8be11-157">Um die Kamera auf dem Desktop oder im Internet verwenden zu können, wird von Microsoft Teams eine Berechtigungs Aufforderung angezeigt, wenn Sie `getUserMedia` Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="8be11-157">To use the camera on desktop or web, Teams will show a permission prompt when you call `getUserMedia`:</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="8be11-158">Um das Bild auf mobilen Geräten zu erfassen, fragt Microsoft Teams Mobile die Berechtigung ab, wenn Sie anrufen `captureImage()` :</span><span class="sxs-lookup"><span data-stu-id="8be11-158">To capture the image on mobile, Teams mobile will ask for permission when you call `captureImage()`:</span></span>

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

<span data-ttu-id="8be11-159">Der Benutzer wird beim Aufruf von Benachrichtigungen aufgefordert `requestPermission` :</span><span class="sxs-lookup"><span data-stu-id="8be11-159">Notifications will prompt the user when you call `requestPermission`:</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

<span data-ttu-id="8be11-160">Um die Kamera oder den Zugriff auf die Fotogalerie zu verwenden, fragt Microsoft Teams Mobile beim Aufruf die Berechtigung ab `selectMedia()` :</span><span class="sxs-lookup"><span data-stu-id="8be11-160">To use camera or access photo gallery, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="8be11-161">Um MIC zu verwenden, fragt Teams Mobile beim Aufruf die Berechtigung ab `selectMedia()` :</span><span class="sxs-lookup"><span data-stu-id="8be11-161">To use mic, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="8be11-162">Um den Benutzer aufzufordern, den Standort auf der Kartenoberfläche freizugeben, fragt Teams Mobile beim Aufruf die Berechtigung ab `getLocation()` :</span><span class="sxs-lookup"><span data-stu-id="8be11-162">To prompt user to share location on map interface, Teams mobile will ask permission when you call `getLocation()`:</span></span>

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[<span data-ttu-id="8be11-163">Desktop</span><span class="sxs-lookup"><span data-stu-id="8be11-163">Desktop</span></span>](#tab/desktop)

![Eingabeaufforderung für Desktop Geräte Berechtigungen für Tabs](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="8be11-165">Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="8be11-165">Mobile</span></span>](#tab/mobile)

![Eingabeaufforderung für mobile Geräte Berechtigungen für Tabs](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="8be11-167">Berechtigungsverhalten für Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="8be11-167">Permission behavior across login sessions</span></span>

<span data-ttu-id="8be11-168">Für jede Anmeldesitzung werden systemeigene Geräte Berechtigungen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8be11-168">Native device permissions are stored for every login session.</span></span> <span data-ttu-id="8be11-169">Wenn Sie sich bei einer anderen Instanz von Teams (beispielsweise auf einem anderen Computer) anmelden, sind Ihre Geräte Berechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8be11-169">It means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="8be11-170">Stattdessen müssen Sie die Geräte Berechtigungen für die neue Anmeldesitzung erneut genehmigen.</span><span class="sxs-lookup"><span data-stu-id="8be11-170">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="8be11-171">Dies bedeutet auch, dass die Geräte Berechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln).</span><span class="sxs-lookup"><span data-stu-id="8be11-171">It also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="8be11-172">Beachten Sie Folgendes, wenn Sie systemeigene Geräte Berechtigungen entwickeln: die systemeigenen Funktionen, die Sie einwilligen, gelten nur für Ihre _aktuelle_ Anmeldesitzung.</span><span class="sxs-lookup"><span data-stu-id="8be11-172">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
