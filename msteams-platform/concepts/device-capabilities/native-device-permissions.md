---
title: Anfordern von Geräteberechtigungen für Ihre Registerkarte
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features an fordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
ms.topic: how-to
keywords: Entwicklung von Teams-Registerkarten
ms.openlocfilehash: a2893fb2905584eac4b398287d431f406c23b12b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014530"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="98c5f-104">Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="98c5f-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="98c5f-105">Sie können Ihre Registerkarte mit Features erweitern, die Zugriff auf systemeigene Gerätefunktionen erfordern, wie:</span><span class="sxs-lookup"><span data-stu-id="98c5f-105">You might want to enrich your tab with features that require access to native device functionality like:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="98c5f-106">Kamera</span><span class="sxs-lookup"><span data-stu-id="98c5f-106">Camera</span></span>
> * <span data-ttu-id="98c5f-107">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="98c5f-107">Microphone</span></span>
> * <span data-ttu-id="98c5f-108">Ort</span><span class="sxs-lookup"><span data-stu-id="98c5f-108">Location</span></span>
> * <span data-ttu-id="98c5f-109">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="98c5f-109">Notifications</span></span>

> [!NOTE]
> <span data-ttu-id="98c5f-110">Informationen zum Integrieren von Kamera- und Bildfunktionen in Ihre mobile Microsoft Teams-App finden Sie unter ["Kamera- und Bildfunktionen in Teams".](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="98c5f-110">To integrate camera and image capabilities within your Microsoft Teams mobile app, see [Camera and image capabilities in Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="98c5f-111">Derzeit unterstützt der mobile Client von Teams nur den Zugriff auf , und über systemeigene Gerätefunktionen und ist in allen `camera` `gallery` `mic` `location` App-Konstrukten einschließlich Registerkarten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="98c5f-111">At present, Teams mobile client only supports access to `camera`, `gallery`, `mic`, and `location` through native device capabilities and is available on all app constructs including tabs.</span></span> </br>
> * <span data-ttu-id="98c5f-112">Unterstützung für `camera` , und wird über `gallery` `mic` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="98c5f-112">Support for `camera`, `gallery`, and `mic` is enabled through [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true).</span></span> <span data-ttu-id="98c5f-113">Für eine einzelne Bildaufnahme können Sie [**die captureImage-API verwenden.**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="98c5f-113">For single image capture you may use [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span></span>
> * <span data-ttu-id="98c5f-114">Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="98c5f-114">Support for `location` is enabled through [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true).</span></span> <span data-ttu-id="98c5f-115">Es wird empfohlen, diese API zu verwenden, da [**die Geolocation-API**](../../resources/schema/manifest-schema.md#devicepermissions) derzeit nicht vollständig auf allen Desktopclients unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="98c5f-115">It's recommended you use this API as [**geolocation API**](../../resources/schema/manifest-schema.md#devicepermissions) is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="98c5f-116">Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="98c5f-116">Device permissions</span></span>

<span data-ttu-id="98c5f-117">Wenn Sie auf die Geräteberechtigungen eines Benutzers zugreifen, können Sie viel reichhaltigere Benutzeroberflächen erstellen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="98c5f-117">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="98c5f-118">Aufzeichnen und Freigeben kurzer Videos</span><span class="sxs-lookup"><span data-stu-id="98c5f-118">Record and share short videos</span></span>
* <span data-ttu-id="98c5f-119">Aufzeichnen kurzer Audionotizen und Speichern für später</span><span class="sxs-lookup"><span data-stu-id="98c5f-119">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="98c5f-120">Verwenden von Benutzerstandortinformationen zum Anzeigen relevanter Informationen</span><span class="sxs-lookup"><span data-stu-id="98c5f-120">Use user location information to display relevant information</span></span>

<span data-ttu-id="98c5f-121">Während der Zugriff auf diese Features in den meisten modernen Webbrowsern standard ist, müssen Sie Teams durch Aktualisieren Ihres App-Manifests wissen lassen, welche Features Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="98c5f-121">While access to these features is standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="98c5f-122">Auf diese Weise können Sie berechtigungen wie in einem Browser ein verlangen, während Ihre App auf dem Desktopclient von Teams ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="98c5f-122">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="98c5f-123">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="98c5f-123">Manage permissions</span></span>

# <a name="desktop"></a>[<span data-ttu-id="98c5f-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="98c5f-124">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="98c5f-125">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="98c5f-125">Open Teams.</span></span>
1. <span data-ttu-id="98c5f-126">Wählen Sie in der oberen rechten Ecke des Fensters Ihr Profilsymbol aus.</span><span class="sxs-lookup"><span data-stu-id="98c5f-126">In the upper right corner of the window, select your profile icon.</span></span>
1. <span data-ttu-id="98c5f-127">Wählen **Sie im**  ->   Dropdownmenü "Einstellungsberechtigungen" aus.</span><span class="sxs-lookup"><span data-stu-id="98c5f-127">Select **Settings** -> **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="98c5f-128">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="98c5f-128">Choose your desired settings.</span></span>

![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="98c5f-130">Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="98c5f-130">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="98c5f-131">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="98c5f-131">Open Teams.</span></span>
1. <span data-ttu-id="98c5f-132">Wechseln Sie zu   ->  **"Einstellungen-App-Berechtigungen".**</span><span class="sxs-lookup"><span data-stu-id="98c5f-132">Go to **Settings** -> **App Permissions**.</span></span>
1. <span data-ttu-id="98c5f-133">Wählen Sie die App aus, für die Sie Einstellungen auswählen müssen.</span><span class="sxs-lookup"><span data-stu-id="98c5f-133">Select the app you need to choose settings for.</span></span>
1. <span data-ttu-id="98c5f-134">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="98c5f-134">Choose your desired settings.</span></span>

![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a><span data-ttu-id="98c5f-136">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="98c5f-136">Properties</span></span>

<span data-ttu-id="98c5f-137">Aktualisieren Sie die App, indem Sie die fünf Eigenschaften hinzufügen und angeben, die Sie `manifest.json` in Ihrer Anwendung verwenden `devicePermissions` möchten:</span><span class="sxs-lookup"><span data-stu-id="98c5f-137">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

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
> <span data-ttu-id="98c5f-138">Medien werden auch für Kameraberechtigungen auf Mobilgeräten verwendet.</span><span class="sxs-lookup"><span data-stu-id="98c5f-138">Media is also used for camera permissions on mobile.</span></span>

<span data-ttu-id="98c5f-139">Jede Eigenschaft ermöglicht es Ihnen, den Benutzer auf, um seine Zustimmung zu bitten:</span><span class="sxs-lookup"><span data-stu-id="98c5f-139">Each property will allow you to prompt the user to ask for their consent:</span></span>

| <span data-ttu-id="98c5f-140">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="98c5f-140">Property</span></span>      | <span data-ttu-id="98c5f-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="98c5f-141">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="98c5f-142">media</span><span class="sxs-lookup"><span data-stu-id="98c5f-142">media</span></span>         | <span data-ttu-id="98c5f-143">Berechtigung zur Verwendung der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf die Mediengalerie</span><span class="sxs-lookup"><span data-stu-id="98c5f-143">permission to use the camera, microphone, speakers, and access media gallery</span></span> |
| <span data-ttu-id="98c5f-144">geolocation</span><span class="sxs-lookup"><span data-stu-id="98c5f-144">geolocation</span></span>   | <span data-ttu-id="98c5f-145">Berechtigung zum Zurückgeben des Standorts des Benutzers</span><span class="sxs-lookup"><span data-stu-id="98c5f-145">permission to return the user's location</span></span>      |
| <span data-ttu-id="98c5f-146">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="98c5f-146">notifications</span></span> | <span data-ttu-id="98c5f-147">Berechtigung zum Senden von Benutzerbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="98c5f-147">permission to send the user notifications</span></span>      |
| <span data-ttu-id="98c5f-148">midi</span><span class="sxs-lookup"><span data-stu-id="98c5f-148">midi</span></span>          | <span data-ttu-id="98c5f-149">Berechtigung zum Senden und Empfangen von Midiinformationen von einem digitalen Musikgerät</span><span class="sxs-lookup"><span data-stu-id="98c5f-149">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="98c5f-150">openExternal</span><span class="sxs-lookup"><span data-stu-id="98c5f-150">openExternal</span></span>  | <span data-ttu-id="98c5f-151">Berechtigung zum Öffnen von Links in externen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="98c5f-151">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="98c5f-152">Überprüfen von Berechtigungen auf Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="98c5f-152">Checking permissions from your tab</span></span>

<span data-ttu-id="98c5f-153">Nachdem Sie Ihrem App-Manifest hinzugefügt haben, können Sie Berechtigungen mithilfe der HTML5-API "Berechtigungen" überprüfen, ohne eine `devicePermissions` Eingabeaufforderung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="98c5f-153">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="98c5f-154">Benutzeraufforderung</span><span class="sxs-lookup"><span data-stu-id="98c5f-154">Prompting the user</span></span>

<span data-ttu-id="98c5f-155">Um eine Aufforderung zum Einholen der Zustimmung zum Zugriff auf Geräteberechtigungen zu erhalten, müssen Sie die entsprechende HTML5- oder Teams-API nutzen.</span><span class="sxs-lookup"><span data-stu-id="98c5f-155">To show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 or Teams API.</span></span> 

<span data-ttu-id="98c5f-156">Um den Benutzer z. B. zum Zugreifen auf seinen Standort aufforderen, müssen Sie den folgenden Anruf `getCurrentPosition` aufrufen:</span><span class="sxs-lookup"><span data-stu-id="98c5f-156">For example, to prompt the user to access their location you need to call `getCurrentPosition`:</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="98c5f-157">Um die Kamera auf Desktops oder im Web zu verwenden, zeigt Teams beim Aufrufen eine Berechtigungsaufforderung `getUserMedia` an:</span><span class="sxs-lookup"><span data-stu-id="98c5f-157">To use the camera on desktop or web, Teams will show a permission prompt when you call `getUserMedia`:</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="98c5f-158">Um das Bild auf mobilen Geräten zu erfassen, fordert Teams Mobile beim Anruf die Berechtigung `captureImage()` an:</span><span class="sxs-lookup"><span data-stu-id="98c5f-158">To capture the image on mobile, Teams mobile will ask for permission when you call `captureImage()`:</span></span>

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

<span data-ttu-id="98c5f-159">Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission` anrufen:</span><span class="sxs-lookup"><span data-stu-id="98c5f-159">Notifications will prompt the user when you call `requestPermission`:</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

<span data-ttu-id="98c5f-160">Um kamera- oder zugriffsfotokataloge zu verwenden, fragt Teams Mobile die Berechtigung, wenn Sie `selectMedia()` anrufen:</span><span class="sxs-lookup"><span data-stu-id="98c5f-160">To use camera or access photo gallery, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="98c5f-161">Zur Verwendung des Mikrofons fragt Teams Mobile beim Anruf die Berechtigung `selectMedia()` ab:</span><span class="sxs-lookup"><span data-stu-id="98c5f-161">To use mic, Teams mobile will ask permission when you call `selectMedia()`:</span></span>

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

<span data-ttu-id="98c5f-162">Um den Benutzer zum Freigeben des Standorts auf der Kartenoberfläche aufforderen, fordert Teams Mobile beim Anruf die Berechtigung `getLocation()` an:</span><span class="sxs-lookup"><span data-stu-id="98c5f-162">To prompt user to share location on map interface, Teams mobile will ask permission when you call `getLocation()`:</span></span>

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[<span data-ttu-id="98c5f-163">Desktop</span><span class="sxs-lookup"><span data-stu-id="98c5f-163">Desktop</span></span>](#tab/desktop)

![Eingabeaufforderung für Registerkarten für Desktopgeräte](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[<span data-ttu-id="98c5f-165">Mobilgeräte</span><span class="sxs-lookup"><span data-stu-id="98c5f-165">Mobile</span></span>](#tab/mobile)

![Eingabeaufforderung für Registerkarten für Mobilgeräte](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="98c5f-167">Berechtigungsverhalten in allen Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="98c5f-167">Permission behavior across login sessions</span></span>

<span data-ttu-id="98c5f-168">Systemeigene Geräteberechtigungen werden für jede Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="98c5f-168">Native device permissions are stored for every login session.</span></span> <span data-ttu-id="98c5f-169">Wenn Sie sich bei einer anderen Instanz von Teams (z. B. auf einem anderen Computer) anmelden, stehen Ihre Geräteberechtigungen aus Ihren vorherigen Sitzungen nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="98c5f-169">It means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="98c5f-170">Stattdessen müssen Sie den Geräteberechtigungen für die neue Anmeldesitzung erneut zustimmen.</span><span class="sxs-lookup"><span data-stu-id="98c5f-170">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="98c5f-171">Dies bedeutet auch, dass Ihre Geräteberechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln).</span><span class="sxs-lookup"><span data-stu-id="98c5f-171">It also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="98c5f-172">Beachten Sie dies beim Entwickeln systemeigener Geräteberechtigungen: Die systemeigenen Funktionen, denen Sie zustimmen, sind nur für Ihre _aktuelle Anmeldesitzung._</span><span class="sxs-lookup"><span data-stu-id="98c5f-172">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
