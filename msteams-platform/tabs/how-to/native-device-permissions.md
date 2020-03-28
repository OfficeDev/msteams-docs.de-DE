---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: e9dc6c6f177e3a87e2846bcb836cc38601c9a50e
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034036"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a><span data-ttu-id="c26c5-104">Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="c26c5-104">Request device permissions for your Microsoft Teams tab</span></span>

<span data-ttu-id="c26c5-105">Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die den Zugriff auf systemeigene Gerätefunktionen erfordern, wie:</span><span class="sxs-lookup"><span data-stu-id="c26c5-105">You might want to enrich your tab with features that require access native device functionality like:</span></span>

* <span data-ttu-id="c26c5-106">Kamera</span><span class="sxs-lookup"><span data-stu-id="c26c5-106">Camera</span></span>
* <span data-ttu-id="c26c5-107">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="c26c5-107">Microphone</span></span>
* <span data-ttu-id="c26c5-108">Standort</span><span class="sxs-lookup"><span data-stu-id="c26c5-108">Location</span></span>
* <span data-ttu-id="c26c5-109">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c26c5-109">Notifications</span></span>

![Bildschirm "Geräte Berechtigungseinstellungen"](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
>
> <span data-ttu-id="c26c5-111">Die systemeigene Gerätefunktionalität wird derzeit für Registerkarten auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c26c5-111">Native device functionality is currently not supported for tabs on mobile clients.</span></span>
>
> <span data-ttu-id="c26c5-112">Die Geolocation-API wird derzeit nicht vollständig auf allen Desktop-Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c26c5-112">The geolocation API is currently not fully supported on all desktop clients.</span></span>

## <a name="device-permissions"></a><span data-ttu-id="c26c5-113">Geräteberechtigungen</span><span class="sxs-lookup"><span data-stu-id="c26c5-113">Device permissions</span></span>

<span data-ttu-id="c26c5-114">Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="c26c5-114">Accessing a user’s device permissions allows you to build much richer experiences, for example:</span></span>

* <span data-ttu-id="c26c5-115">Aufzeichnen und Freigeben von kurzen Videos</span><span class="sxs-lookup"><span data-stu-id="c26c5-115">Record and share short videos</span></span>
* <span data-ttu-id="c26c5-116">Kurze audiomemos aufzeichnen und später speichern</span><span class="sxs-lookup"><span data-stu-id="c26c5-116">Record short audio memos and save them for later</span></span>
* <span data-ttu-id="c26c5-117">Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen</span><span class="sxs-lookup"><span data-stu-id="c26c5-117">Use user location information to display relevant information</span></span>

<span data-ttu-id="c26c5-118">Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern standardmäßig ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c26c5-118">While access to these features are standard in most modern web browsers, you need to let Teams know which features you’d like to use by updating your app manifest.</span></span> <span data-ttu-id="c26c5-119">Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.</span><span class="sxs-lookup"><span data-stu-id="c26c5-119">This will allow you to ask for permissions, the same way you would in a browser, while your app is running on the Teams desktop client.</span></span>

## <a name="properties"></a><span data-ttu-id="c26c5-120">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="c26c5-120">Properties</span></span>

<span data-ttu-id="c26c5-121">Aktualisieren Sie Ihre APP `manifest.json` , indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="c26c5-121">Update your app's `manifest.json` by adding `devicePermissions` and specifying which of the five properties you’d like to use in your application:</span></span>

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

<span data-ttu-id="c26c5-122">Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen.</span><span class="sxs-lookup"><span data-stu-id="c26c5-122">Each property will allow you to prompt the user to ask for their consent</span></span>

| <span data-ttu-id="c26c5-123">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="c26c5-123">Property</span></span>      | <span data-ttu-id="c26c5-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c26c5-124">Description</span></span>   |
| --- | --- |
| <span data-ttu-id="c26c5-125">media</span><span class="sxs-lookup"><span data-stu-id="c26c5-125">media</span></span>         | <span data-ttu-id="c26c5-126">Berechtigung zur Verwendung der Kamera, des Mikrofons und der Lautsprecher</span><span class="sxs-lookup"><span data-stu-id="c26c5-126">permission to use the camera, microphone and speakers</span></span> |
| <span data-ttu-id="c26c5-127">Geolocation</span><span class="sxs-lookup"><span data-stu-id="c26c5-127">geolocation</span></span>   | <span data-ttu-id="c26c5-128">Berechtigung zum Zurückgeben des Standorts des Benutzers</span><span class="sxs-lookup"><span data-stu-id="c26c5-128">permission to return the user's location</span></span>      |
| <span data-ttu-id="c26c5-129">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c26c5-129">notifications</span></span> | <span data-ttu-id="c26c5-130">Berechtigung zum Senden der Benutzer Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="c26c5-130">permission to send the user notifications</span></span>      |
| <span data-ttu-id="c26c5-131">MIDI</span><span class="sxs-lookup"><span data-stu-id="c26c5-131">midi</span></span>          | <span data-ttu-id="c26c5-132">Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument</span><span class="sxs-lookup"><span data-stu-id="c26c5-132">permission to send and receive midi information from a digital musical instrument</span></span>   |
| <span data-ttu-id="c26c5-133">openextern</span><span class="sxs-lookup"><span data-stu-id="c26c5-133">openExternal</span></span>  | <span data-ttu-id="c26c5-134">Berechtigung zum Öffnen von Links in externen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c26c5-134">permission to open links in external applications</span></span>  |

## <a name="checking-permissions-from-your-tab"></a><span data-ttu-id="c26c5-135">Überprüfen von Berechtigungen auf der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="c26c5-135">Checking permissions from your tab</span></span>

<span data-ttu-id="c26c5-136">Nachdem Sie Ihrem APP `devicePermissions` -Manifest hinzugefügt haben, können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="c26c5-136">Once you’ve added `devicePermissions` to your app manifest, you can check permissions using the HTML5 “permissions” API without causing a prompt.</span></span>

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

## <a name="prompting-the-user"></a><span data-ttu-id="c26c5-137">Auffordern des Benutzers</span><span class="sxs-lookup"><span data-stu-id="c26c5-137">Prompting the user</span></span>

<span data-ttu-id="c26c5-138">Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-API nutzen.</span><span class="sxs-lookup"><span data-stu-id="c26c5-138">In order to show a prompt to get consent to access device permissions you need to leverage the appropriate HTML5 API.</span></span> <span data-ttu-id="c26c5-139">Um den Benutzer zum Zugreifen auf seine Kamera aufzufordern, müssen Sie beispielsweise`getUserMedia`</span><span class="sxs-lookup"><span data-stu-id="c26c5-139">For example, in order to prompt the user to access their camera you need to call `getUserMedia`</span></span>

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

<span data-ttu-id="c26c5-140">Geolocation zeigt eine Berechtigungs Aufforderung an, wenn Sie die`getCurrentPosition`</span><span class="sxs-lookup"><span data-stu-id="c26c5-140">Geolocation will  show a permission prompt when you call `getCurrentPosition`</span></span>

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

<span data-ttu-id="c26c5-141">Benachrichtigungen werden vom Benutzer aufgefordert, wenn Sie anrufen`requestPermission`</span><span class="sxs-lookup"><span data-stu-id="c26c5-141">Notifications will prompt the user when you call `requestPermission`</span></span>

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Eingabeaufforderung für Tabs Device Permissions](~/assets/images/tabs/device-permissions-prompt.png)

## <a name="permission-behavior-across-login-sessions"></a><span data-ttu-id="c26c5-143">Berechtigungsverhalten für Anmeldesitzungen</span><span class="sxs-lookup"><span data-stu-id="c26c5-143">Permission behavior across login sessions</span></span>

<span data-ttu-id="c26c5-144">Berechtigungen für systemeigene Geräte werden pro Anmeldesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="c26c5-144">Native device permissions are stored per login session.</span></span> <span data-ttu-id="c26c5-145">Wenn Sie sich also bei einer anderen Instanz von Teams anmelden (z.b. auf einem anderen Computer), sind Ihre Geräte Berechtigungen aus ihren vorherigen Sitzungen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c26c5-145">This means that if you log into another instance of Teams (ex: on another computer), your device permissions from your previous sessions will not be available.</span></span> <span data-ttu-id="c26c5-146">Stattdessen müssen Sie die Geräte Berechtigungen für die neue Anmeldesitzung erneut genehmigen.</span><span class="sxs-lookup"><span data-stu-id="c26c5-146">Instead, you will need to re-consent to device permissions for the new login session.</span></span> <span data-ttu-id="c26c5-147">Dies bedeutet auch, dass Ihre Geräte Berechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln).</span><span class="sxs-lookup"><span data-stu-id="c26c5-147">This also means, if you log out of Teams (or switch tenants inside of Teams), your device permissions will be deleted for that previous login session.</span></span> <span data-ttu-id="c26c5-148">Beachten Sie Folgendes, wenn Sie systemeigene Geräte Berechtigungen entwickeln: die systemeigenen Funktionen, die Sie einwilligen, gelten nur für Ihre _aktuelle_ Anmeldesitzung.</span><span class="sxs-lookup"><span data-stu-id="c26c5-148">Please keep this in mind when developing native device permissions: the native capabilities you consent to are only for your _current_ login session.</span></span>
