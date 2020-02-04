---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: 454466ff17ecf275f6ae6c7413df8e117335f3c8
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674083"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="c65f6-104">Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="c65f6-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="c65f6-105">Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die den Zugriff auf systemeigene Gerätefunktionen erfordern, wie:</span><span class="sxs-lookup"><span data-stu-id="c65f6-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

* <span data-ttu-id="c65f6-106">Kamera</span><span class="sxs-lookup"><span data-stu-id="c65f6-106">Camera</span></span>
* <span data-ttu-id="c65f6-107">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="c65f6-107">Microphone</span></span>
* <span data-ttu-id="c65f6-108">Ort</span><span class="sxs-lookup"><span data-stu-id="c65f6-108">Location</span></span>
* <span data-ttu-id="c65f6-109">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c65f6-109">Notifications</span></span>

![Bildschirm "Geräte Berechtigungseinstellungen"](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
> <span data-ttu-id="c65f6-111">Die systemeigene Gerätefunktionalität wird derzeit nicht für Registerkarten auf mobilen Clients unterstützt, aber die vollständige Unterstützung wird bald verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="c65f6-111">Native device functionality is currently not supported for tabs on mobile clients but full support is coming soon.</span></span> <span data-ttu-id="c65f6-112">Zur Vorbereitung auf diese Änderung sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.</span><span class="sxs-lookup"><span data-stu-id="c65f6-112">To prepare for this change you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="c65f6-113">Persönliche Apps (statische Registerkarten) sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c65f6-113">Personal apps (static tabs) are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
>
> <span data-ttu-id="c65f6-114">Wenn die vollständige Unterstützung für Tabs freigegeben wird:</span><span class="sxs-lookup"><span data-stu-id="c65f6-114">When full support for tabs is released:</span></span>
>
> * <span data-ttu-id="c65f6-115">Alle Registerkarten sind auf mobilen Geräten immer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c65f6-115">All tabs will always be available on mobile</span></span>
> * <span data-ttu-id="c65f6-116">Ihr `contentUrl` **wird in den Mobile Teams-Client geladen**.</span><span class="sxs-lookup"><span data-stu-id="c65f6-116">Your `contentUrl` **will be loaded in the mobile Teams client**.</span></span>
> * <span data-ttu-id="c65f6-117">Bei Kanälen/Gruppenregisterkarten können Benutzer ihre Registerkarte weiterhin in einem separaten Browser öffnen `websiteUrl`, jedoch werden Sie `contentUrl` zuerst geladen.</span><span class="sxs-lookup"><span data-stu-id="c65f6-117">For channel/group tabs, users can still open your tab in a separate browser via your `websiteUrl`, however your `contentUrl` will be loaded first.</span></span>  

## <a name="device-permissions"></a><span data-ttu-id="c65f6-118">Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="c65f6-118">Device permissions</span></span>

<span data-ttu-id="c65f6-119">Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="c65f6-119">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="c65f6-120">Aufzeichnen und Freigeben von kurzen Videos</span><span class="sxs-lookup"><span data-stu-id="c65f6-120">Record and share short videos</span></span>
* <span data-ttu-id="c65f6-121">Kurze audiomemos aufzeichnen und später speichern</span><span class="sxs-lookup"><span data-stu-id="c65f6-121">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="c65f6-122">Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen</span><span class="sxs-lookup"><span data-stu-id="c65f6-122">Use user location information to display relevant information</span></span>

<span data-ttu-id="c65f6-123">Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern standardmäßig ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c65f6-123">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="c65f6-124">Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.</span><span class="sxs-lookup"><span data-stu-id="c65f6-124">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="properties"></a><span data-ttu-id="c65f6-125">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="c65f6-125">Properties</span></span>

<span data-ttu-id="c65f6-126">Aktualisieren Sie Ihre APP `manifest.json` , indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="c65f6-126">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="c65f6-127">Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen.</span><span class="sxs-lookup"><span data-stu-id="c65f6-127">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="c65f6-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c65f6-128">Property</span></span>      | <span data-ttu-id="c65f6-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c65f6-129">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="c65f6-130">Medien</span><span class="sxs-lookup"><span data-stu-id="c65f6-130">media</span></span>         | <span data-ttu-id="c65f6-131">Berechtigung zur Verwendung der Kamera, des Mikrofons und der Lautsprecher</span><span class="sxs-lookup"><span data-stu-id="c65f6-131">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="c65f6-132">Geolocation</span><span class="sxs-lookup"><span data-stu-id="c65f6-132">geolocation</span></span>   | <span data-ttu-id="c65f6-133">Berechtigung zum Zurückgeben des Standorts des Benutzers</span><span class="sxs-lookup"><span data-stu-id="c65f6-133">permission to return the user's location</span></span>      |
| <span data-ttu-id="c65f6-134">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c65f6-134">notifications</span></span> | <span data-ttu-id="c65f6-135">Berechtigung zum Senden der Benutzer Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c65f6-135">permission to send the user notifications</span></span>      |
| <span data-ttu-id="c65f6-136">MIDI</span><span class="sxs-lookup"><span data-stu-id="c65f6-136">midi</span></span>          | <span data-ttu-id="c65f6-137">Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument</span><span class="sxs-lookup"><span data-stu-id="c65f6-137">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="c65f6-138">openextern</span><span class="sxs-lookup"><span data-stu-id="c65f6-138">openExternal</span></span>  | <span data-ttu-id="c65f6-139">Berechtigung zum Öffnen von Links in externen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c65f6-139">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="c65f6-140">Überprüfen von Berechtigungen auf der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="c65f6-140">Checking permissions from your tab</span></span>

<span data-ttu-id="c65f6-141">Nachdem Sie Ihrem APP `devicePermissions` -Manifest hinzugefügt haben, können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="c65f6-141">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="c65f6-142">Auffordern des Benutzers</span><span class="sxs-lookup"><span data-stu-id="c65f6-142">Prompting the user</span></span>

<span data-ttu-id="c65f6-143">Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-API nutzen.</span><span class="sxs-lookup"><span data-stu-id="c65f6-143">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 API.</span></span> <span data-ttu-id="c65f6-144">Um den Benutzer zum Zugreifen auf seine Kamera aufzufordern, müssen Sie beispielsweise`getUserMedia`</span><span class="sxs-lookup"><span data-stu-id="c65f6-144">For example, in order to prompt the user to access their camera you need to call `getUserMedia`</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="c65f6-145">Geolocation zeigt eine Berechtigungs Aufforderung an, wenn Sie die`getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="c65f6-145">Geolocation will  show a permission prompt when you call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="c65f6-146">Benachrichtigungen werden vom Benutzer aufgefordert, wenn Sie anrufen`requestPermission`</span><span class="sxs-lookup"><span data-stu-id="c65f6-146">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Eingabeaufforderung für Tabs Device Permissions](~/assets/images/tabs/device-permissions-prompt.png)