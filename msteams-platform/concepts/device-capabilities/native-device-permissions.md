---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: d6c66525ab0e81f0632df5e2c323926279e38a8e
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576880"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="12f5e-104">Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="12f5e-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="12f5e-105">Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die den Zugriff auf systemeigene Gerätefunktionen erfordern, wie:</span><span class="sxs-lookup"><span data-stu-id="12f5e-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="12f5e-106">Kamera</span><span class="sxs-lookup"><span data-stu-id="12f5e-106">Camera</span></span>
> * <span data-ttu-id="12f5e-107">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="12f5e-107">Microphone</span></span>
> * <span data-ttu-id="12f5e-108">Speicherort</span><span class="sxs-lookup"><span data-stu-id="12f5e-108">Location</span></span>
> * <span data-ttu-id="12f5e-109">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="12f5e-109">Notifications</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="12f5e-110">Derzeit unterstützt der Mobile Microsoft Teams `camera` -Client nur und `location`  über systemeigene Gerätefunktionen und steht in allen APP-Konstrukten einschließlich Registerkarten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="12f5e-110">Currently, Teams mobile client only supports `camera` and `location`  through native device capabilities and is available on all app constructs including tabs.</span></span> </br>
> * <span data-ttu-id="12f5e-111">Die Unterstützung für `camera` die Bildaufnahme wird von der [**captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true)aktiviert.</span><span class="sxs-lookup"><span data-stu-id="12f5e-111">Support for `camera` image capture is enabled by the [**captureImage API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true).</span></span>
> * <span data-ttu-id="12f5e-112">Die [**Geolocation-API**](../../resources/schema/manifest-schema.md#devicepermissions) wird derzeit nicht vollständig auf allen Desktop-Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="12f5e-112">The [**geolocation API**](../../resources/schema/manifest-schema.md#devicepermissions) is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="12f5e-113">Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="12f5e-113">Device permissions</span></span>

<span data-ttu-id="12f5e-114">Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="12f5e-114">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="12f5e-115">Aufzeichnen und Freigeben von kurzen Videos</span><span class="sxs-lookup"><span data-stu-id="12f5e-115">Record and share short videos</span></span>
* <span data-ttu-id="12f5e-116">Kurze audiomemos aufzeichnen und später speichern</span><span class="sxs-lookup"><span data-stu-id="12f5e-116">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="12f5e-117">Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen</span><span class="sxs-lookup"><span data-stu-id="12f5e-117">Use user location information to display relevant information</span></span>

<span data-ttu-id="12f5e-118">Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern standardmäßig ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="12f5e-118">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="12f5e-119">Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.</span><span class="sxs-lookup"><span data-stu-id="12f5e-119">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="manage-permissions"></a><span data-ttu-id="12f5e-120">
            Berechtigungen verwalten</span><span class="sxs-lookup"><span data-stu-id="12f5e-120">Manage permissions</span></span>

# <a name="desktop"></a>[<span data-ttu-id="12f5e-121">Desktop</span><span class="sxs-lookup"><span data-stu-id="12f5e-121">Desktop</span></span>](#tab/desktop)

1. <span data-ttu-id="12f5e-122">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="12f5e-122">Open Teams.</span></span>
1. <span data-ttu-id="12f5e-123">Wählen Sie in der oberen rechten Ecke des Fensters Ihr Profilsymbol aus.</span><span class="sxs-lookup"><span data-stu-id="12f5e-123">In the upper right corner of the window, select your profile icon.</span></span>
1. <span data-ttu-id="12f5e-124">Wählen **Settings** Sie  ->  im Dropdownmenü Einstellungen **Berechtigungen** aus.</span><span class="sxs-lookup"><span data-stu-id="12f5e-124">Select **Settings** -> **Permissions** from the drop-down menu.</span></span>
1. <span data-ttu-id="12f5e-125">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="12f5e-125">Choose your desired settings.</span></span>

![Bildschirm "Geräte Berechtigungen-Desktopeinstellungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[<span data-ttu-id="12f5e-127">Mobile</span><span class="sxs-lookup"><span data-stu-id="12f5e-127">Mobile</span></span>](#tab/mobile)

1. <span data-ttu-id="12f5e-128">Öffnen Sie Teams.</span><span class="sxs-lookup"><span data-stu-id="12f5e-128">Open Teams.</span></span>
1. <span data-ttu-id="12f5e-129">Wählen Sie in der oberen linken Ecke des Bildschirms das &#9776; Menüsymbol aus.</span><span class="sxs-lookup"><span data-stu-id="12f5e-129">In the upper left corner of the screen, select the &#9776; menu icon.</span></span>
1. <span data-ttu-id="12f5e-130">Wählen Sie **Einstellungen**  ->  **Geräte** aus.</span><span class="sxs-lookup"><span data-stu-id="12f5e-130">Select **Settings** -> **Devices**.</span></span>
1. <span data-ttu-id="12f5e-131">Wählen Sie die gewünschten Einstellungen aus.</span><span class="sxs-lookup"><span data-stu-id="12f5e-131">Choose your desired settings.</span></span>

![Bildschirm mit den mobilen Einstellungen für Geräte Berechtigungen](../../assets/images/tabs/mobile-device-permissions-screen.png)

---

## <a name="properties"></a><span data-ttu-id="12f5e-133">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="12f5e-133">Properties</span></span>

<span data-ttu-id="12f5e-134">Aktualisieren Sie Ihre APP, `manifest.json` indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="12f5e-134">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

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
> <span data-ttu-id="12f5e-135">Medien werden auch für Kamera Berechtigungen in Mobile verwendet.</span><span class="sxs-lookup"><span data-stu-id="12f5e-135">Media is also used for camera permissions in mobile.</span></span>

<span data-ttu-id="12f5e-136">Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen.</span><span class="sxs-lookup"><span data-stu-id="12f5e-136">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="12f5e-137">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="12f5e-137">Property</span></span>      | <span data-ttu-id="12f5e-138">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="12f5e-138">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="12f5e-139">Medien</span><span class="sxs-lookup"><span data-stu-id="12f5e-139">media</span></span>         | <span data-ttu-id="12f5e-140">Berechtigung zur Verwendung der Kamera, des Mikrofons und der Lautsprecher</span><span class="sxs-lookup"><span data-stu-id="12f5e-140">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="12f5e-141">Geolocation</span><span class="sxs-lookup"><span data-stu-id="12f5e-141">geolocation</span></span>   | <span data-ttu-id="12f5e-142">Berechtigung zum Zurückgeben des Standorts des Benutzers</span><span class="sxs-lookup"><span data-stu-id="12f5e-142">permission to return the user's location</span></span>      |
| <span data-ttu-id="12f5e-143">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="12f5e-143">notifications</span></span> | <span data-ttu-id="12f5e-144">Berechtigung zum Senden der Benutzer Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="12f5e-144">permission to send the user notifications</span></span>      |
| <span data-ttu-id="12f5e-145">MIDI</span><span class="sxs-lookup"><span data-stu-id="12f5e-145">midi</span></span>          | <span data-ttu-id="12f5e-146">Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument</span><span class="sxs-lookup"><span data-stu-id="12f5e-146">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="12f5e-147">openextern</span><span class="sxs-lookup"><span data-stu-id="12f5e-147">openExternal</span></span>  | <span data-ttu-id="12f5e-148">Berechtigung zum Öffnen von Links in externen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="12f5e-148">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="12f5e-149">Überprüfen von Berechtigungen auf der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="12f5e-149">Checking permissions from your tab</span></span>

<span data-ttu-id="12f5e-150">Nachdem Sie Ihrem App-Manifest hinzugefügt haben `devicePermissions` , können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="12f5e-150">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="12f5e-151">Auffordern des Benutzers</span><span class="sxs-lookup"><span data-stu-id="12f5e-151">Prompting the user</span></span>

<span data-ttu-id="12f5e-152">Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-oder Teams-API nutzen.</span><span class="sxs-lookup"><span data-stu-id="12f5e-152">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 or Teams API.</span></span> <span data-ttu-id="12f5e-153">Um den Benutzer zum Zugreifen auf seine Kamera aufzufordern, müssen Sie beispielsweise `getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="12f5e-153">For example, in order to prompt the user to access their camera you need to call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="12f5e-154">Um die Kamera auf dem Desktop oder im Internet verwenden zu können, wird von Microsoft Teams eine Berechtigungs Aufforderung angezeigt, wenn Sie getUserMedia aufrufen.</span><span class="sxs-lookup"><span data-stu-id="12f5e-154">To use camera on desktop or web, Teams will show a permission prompt when you call getUserMedia</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="12f5e-155">Um Bilder auf mobilen Geräten zu erfassen, fragt Microsoft Teams Mobile um Erlaubnis, wenn Sie captureImage genannt wird ().</span><span class="sxs-lookup"><span data-stu-id="12f5e-155">To capture image on mobile, Teams mobile will ask for permission when called captureImage()</span></span>

```Typescript
function captureImage(callback: (error: SdkError, files: File[]) => void)
```

<span data-ttu-id="12f5e-156">Benachrichtigungen werden vom Benutzer aufgefordert, wenn Sie anrufen `requestPermission`</span><span class="sxs-lookup"><span data-stu-id="12f5e-156">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Eingabeaufforderung für Tabs Device Permissions](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="12f5e-158">Berechtigungsverhalten für Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="12f5e-158">Permission behavior across login sessions</span></span>

<span data-ttu-id="12f5e-159">Berechtigungen für systemeigene Geräte werden pro Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="12f5e-159">Native device permissions are stored per login session.</span></span> <span data-ttu-id="12f5e-160">Wenn Sie sich also bei einer anderen Instanz von Teams anmelden (z.b. auf einem anderen Computer), sind Ihre Geräte Berechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="12f5e-160">This means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="12f5e-161">Stattdessen müssen Sie die Geräte Berechtigungen für die neue Anmeldesitzung erneut genehmigen.</span><span class="sxs-lookup"><span data-stu-id="12f5e-161">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="12f5e-162">Dies bedeutet auch, dass Ihre Geräte Berechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln).</span><span class="sxs-lookup"><span data-stu-id="12f5e-162">This also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="12f5e-163">Beachten Sie Folgendes, wenn Sie systemeigene Geräte Berechtigungen entwickeln: die systemeigenen Funktionen, die Sie einwilligen, gelten nur für Ihre _aktuelle_ Anmeldesitzung.</span><span class="sxs-lookup"><span data-stu-id="12f5e-163">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
