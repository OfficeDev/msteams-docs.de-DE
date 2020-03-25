---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: f0e19c0ed716147c097137c4ef0bf3454783b2eb
ms.sourcegitcommit: c4a7bc638e848a702cce92798cba84917fcecc35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "42928517"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="99693-104">Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="99693-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="99693-105">Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die den Zugriff auf systemeigene Gerätefunktionen erfordern, wie:</span><span class="sxs-lookup"><span data-stu-id="99693-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

* <span data-ttu-id="99693-106">Kamera</span><span class="sxs-lookup"><span data-stu-id="99693-106">Camera</span></span>
* <span data-ttu-id="99693-107">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="99693-107">Microphone</span></span>
* <span data-ttu-id="99693-108">Standort</span><span class="sxs-lookup"><span data-stu-id="99693-108">Location</span></span>
* <span data-ttu-id="99693-109">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="99693-109">Notifications</span></span>

![Bildschirm "Geräte Berechtigungseinstellungen"](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
> <span data-ttu-id="99693-111">Die systemeigene Gerätefunktionalität wird derzeit nicht für Registerkarten auf mobilen Clients unterstützt, aber die vollständige Unterstützung wird bald verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="99693-111">Native device functionality is currently not supported for tabs on mobile clients but full support is coming soon.</span></span> <span data-ttu-id="99693-112">Zur Vorbereitung auf diese Änderung sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.</span><span class="sxs-lookup"><span data-stu-id="99693-112">To prepare for this change you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="99693-113">Persönliche Apps (statische Registerkarten) sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="99693-113">Personal apps (static tabs) are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
>
> <span data-ttu-id="99693-114">Wenn die vollständige Unterstützung für Tabs freigegeben wird:</span><span class="sxs-lookup"><span data-stu-id="99693-114">When full support for tabs is released:</span></span>
>
> * <span data-ttu-id="99693-115">Alle Registerkarten sind auf mobilen Geräten immer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="99693-115">All tabs will always be available on mobile</span></span>
> * <span data-ttu-id="99693-116">Ihr `contentUrl` **wird in den Mobile Teams-Client geladen**.</span><span class="sxs-lookup"><span data-stu-id="99693-116">Your `contentUrl` **will be loaded in the mobile Teams client**.</span></span>
> * <span data-ttu-id="99693-117">Bei Kanälen/Gruppenregisterkarten können Benutzer ihre Registerkarte weiterhin in einem separaten Browser öffnen `websiteUrl`, jedoch werden Sie `contentUrl` zuerst geladen.</span><span class="sxs-lookup"><span data-stu-id="99693-117">For channel/group tabs, users can still open your tab in a separate browser via your `websiteUrl`, however your `contentUrl` will be loaded first.</span></span>  

## <a name="device-permissions"></a><span data-ttu-id="99693-118">Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="99693-118">Device permissions</span></span>

<span data-ttu-id="99693-119">Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="99693-119">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="99693-120">Aufzeichnen und Freigeben von kurzen Videos</span><span class="sxs-lookup"><span data-stu-id="99693-120">Record and share short videos</span></span>
* <span data-ttu-id="99693-121">Kurze audiomemos aufzeichnen und später speichern</span><span class="sxs-lookup"><span data-stu-id="99693-121">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="99693-122">Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen</span><span class="sxs-lookup"><span data-stu-id="99693-122">Use user location information to display relevant information</span></span>

<span data-ttu-id="99693-123">Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern standardmäßig ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="99693-123">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="99693-124">Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.</span><span class="sxs-lookup"><span data-stu-id="99693-124">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="properties"></a><span data-ttu-id="99693-125">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="99693-125">Properties</span></span>

<span data-ttu-id="99693-126">Aktualisieren Sie Ihre APP `manifest.json` , indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="99693-126">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="99693-127">Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen.</span><span class="sxs-lookup"><span data-stu-id="99693-127">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="99693-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="99693-128">Property</span></span>      | <span data-ttu-id="99693-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99693-129">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="99693-130">media</span><span class="sxs-lookup"><span data-stu-id="99693-130">media</span></span>         | <span data-ttu-id="99693-131">Berechtigung zur Verwendung der Kamera, des Mikrofons und der Lautsprecher</span><span class="sxs-lookup"><span data-stu-id="99693-131">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="99693-132">Geolocation</span><span class="sxs-lookup"><span data-stu-id="99693-132">geolocation</span></span>   | <span data-ttu-id="99693-133">Berechtigung zum Zurückgeben des Standorts des Benutzers</span><span class="sxs-lookup"><span data-stu-id="99693-133">permission to return the user's location</span></span>      |
| <span data-ttu-id="99693-134">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="99693-134">notifications</span></span> | <span data-ttu-id="99693-135">Berechtigung zum Senden der Benutzer Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="99693-135">permission to send the user notifications</span></span>      |
| <span data-ttu-id="99693-136">MIDI</span><span class="sxs-lookup"><span data-stu-id="99693-136">midi</span></span>          | <span data-ttu-id="99693-137">Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument</span><span class="sxs-lookup"><span data-stu-id="99693-137">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="99693-138">openextern</span><span class="sxs-lookup"><span data-stu-id="99693-138">openExternal</span></span>  | <span data-ttu-id="99693-139">Berechtigung zum Öffnen von Links in externen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="99693-139">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="99693-140">Überprüfen von Berechtigungen auf der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="99693-140">Checking permissions from your tab</span></span>

<span data-ttu-id="99693-141">Nachdem Sie Ihrem APP `devicePermissions` -Manifest hinzugefügt haben, können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="99693-141">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="99693-142">Auffordern des Benutzers</span><span class="sxs-lookup"><span data-stu-id="99693-142">Prompting the user</span></span>

<span data-ttu-id="99693-143">Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-API nutzen.</span><span class="sxs-lookup"><span data-stu-id="99693-143">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 API.</span></span> <span data-ttu-id="99693-144">Um den Benutzer zum Zugreifen auf seine Kamera aufzufordern, müssen Sie beispielsweise`getUserMedia`</span><span class="sxs-lookup"><span data-stu-id="99693-144">For example, in order to prompt the user to access their camera you need to call `getUserMedia`</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="99693-145">Geolocation zeigt eine Berechtigungs Aufforderung an, wenn Sie die`getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="99693-145">Geolocation will  show a permission prompt when you call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="99693-146">Benachrichtigungen werden vom Benutzer aufgefordert, wenn Sie anrufen`requestPermission`</span><span class="sxs-lookup"><span data-stu-id="99693-146">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Eingabeaufforderung für Tabs Device Permissions](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="99693-148">Berechtigungsverhalten für Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="99693-148">Permission behavior across login sessions</span></span>

<span data-ttu-id="99693-149">Berechtigungen für systemeigene Geräte werden pro Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="99693-149">Native device permissions are stored per login session.</span></span> <span data-ttu-id="99693-150">Wenn Sie sich also bei einer anderen Instanz von Teams anmelden (z.b. auf einem anderen Computer), sind Ihre Geräte Berechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="99693-150">This means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="99693-151">Stattdessen müssen Sie die Geräte Berechtigungen für den neuen Anmelde sessoin erneut einwilligen.</span><span class="sxs-lookup"><span data-stu-id="99693-151">Instead, you will need to re-consent to device permissions for the new login sessoin.</span></span> <span data-ttu-id="99693-152">Dies bedeutet auch, dass Ihre Geräte Berechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln).</span><span class="sxs-lookup"><span data-stu-id="99693-152">This also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="99693-153">Beachten Sie Folgendes, wenn Sie systemeigene Geräte Berechtigungen entwickeln: die systemeigenen Funktionen, die Sie einwilligen, gelten nur für Ihre _aktuelle_ Anmelde-sessoin.</span><span class="sxs-lookup"><span data-stu-id="99693-153">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login sessoin.</span></span>