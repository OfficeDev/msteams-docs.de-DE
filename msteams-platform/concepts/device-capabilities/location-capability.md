---
title: Integration von Standortfunktionen
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK, um Standortfunktionen zu nutzen
keywords: Systemeigene Geräteberechtigungen für Standortzuordnungsfunktionen
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 3e6c4bda9a1a0024380cb295cd280db1d630f019
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211611"
---
# <a name="integrate-location-capabilities"></a><span data-ttu-id="4cd76-104">Integration von Standortfunktionen</span><span class="sxs-lookup"><span data-stu-id="4cd76-104">Integrate location capabilities</span></span> 

<span data-ttu-id="4cd76-105">Sie können die Standortfunktionen des nativen Geräts in Ihre Teams-App integrieren.</span><span class="sxs-lookup"><span data-stu-id="4cd76-105">You can integrate the location capabilities of native device with your Teams app.</span></span>  

<span data-ttu-id="4cd76-106">Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die Tools bereitstellt, die Ihre App für den Zugriff auf die [systemeigenen Gerätefunktionen](native-device-permissions.md)des Benutzers benötigt.</span><span class="sxs-lookup"><span data-stu-id="4cd76-106">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides the tools necessary for your app to access the user’s [native device capabilities](native-device-permissions.md).</span></span> <span data-ttu-id="4cd76-107">Verwenden Sie die Standort-APIs, z. B. [getLocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) und [showLocation,](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) um die Funktionen in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="4cd76-107">Use the location APIs, such as [getLocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) and [showLocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) to integrate the capabilities within your app.</span></span> 

## <a name="advantages-of-integrating-location-capabilities"></a><span data-ttu-id="4cd76-108">Vorteile der Integration von Standortfunktionen</span><span class="sxs-lookup"><span data-stu-id="4cd76-108">Advantages of integrating location capabilities</span></span>

<span data-ttu-id="4cd76-109">Der Hauptvorteil der Integration von Standortfunktionen in Ihre Teams-Apps besteht darin, dass Web-App-Entwickler auf Teams Plattform Standortfunktionen mit Microsoft Teams JavaScript-Client-SDK nutzen können.</span><span class="sxs-lookup"><span data-stu-id="4cd76-109">The main advantage of integrating location capabilities in your Teams apps is that it allows web app developers on Teams platform to leverage location functionality with Microsoft Teams JavaScript client SDK.</span></span> 

<span data-ttu-id="4cd76-110">Die folgenden Beispiele zeigen, wie die Integration von Standortfunktionen in verschiedenen Szenarien verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="4cd76-110">Following examples show how the integration of location capabilities is used in different scenarios:</span></span>
* <span data-ttu-id="4cd76-111">In einer Fabrik kann der Vorgesetzte die Anwesenheit von Mitarbeitern nachverfolgen, indem er sie auffordert, sich in der Nähe der Fabrik zu befinden und sie über die angegebene App freizugeben.</span><span class="sxs-lookup"><span data-stu-id="4cd76-111">In a factory, the supervisor can track the attendance of workers by asking them to take a selfie in the vicinity of the factory and share it through the specified app.</span></span> <span data-ttu-id="4cd76-112">Die Standortdaten werden auch erfasst und zusammen mit dem Bild gesendet.</span><span class="sxs-lookup"><span data-stu-id="4cd76-112">The location data also gets captured and sent along with the image.</span></span>
* <span data-ttu-id="4cd76-113">Die Standortfunktionen ermöglichen es den Wartungsmitarbeitern eines Dienstanbieters, authentifizierte Gesundheitsdaten von Mobilfunkmasten mit der Geschäftsleitung zu teilen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-113">The location capabilities enables the maintenance staff of a service provider to share authentic health data of cellular towers with the management.</span></span> <span data-ttu-id="4cd76-114">Die Geschäftsleitung kann jeden Konflikt zwischen erfassten Standortinformationen und den von Wartungsmitarbeitern übermittelten Daten vergleichen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-114">The management can compare any mismatch between captured location information and the data submitted by maintenance staff.</span></span>

<span data-ttu-id="4cd76-115">Um Standortfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-115">To integrate location capabilities, you must update the app manifest file and call the APIs.</span></span> <span data-ttu-id="4cd76-116">Für eine effektive Integration müssen Sie über ein gutes Verständnis von [Codeausschnitten](#code-snippets) für den Aufruf der Standort-APIs verfügen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-116">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the location APIs.</span></span> <span data-ttu-id="4cd76-117">Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="4cd76-117">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="4cd76-118">Derzeit ist Microsoft Teams Unterstützung für Standortfunktionen nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4cd76-118">Currently, Microsoft Teams support for location capabilities is available for mobile clients only.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="4cd76-119">Updatemanifest</span><span class="sxs-lookup"><span data-stu-id="4cd76-119">Update manifest</span></span>

<span data-ttu-id="4cd76-120">Aktualisieren Sie die Teams [App-manifest.jsauf](../../resources/schema/manifest-schema.md#devicepermissions) der Datei, indem Sie die Eigenschaft hinzufügen `devicePermissions` und `geolocation` angeben.</span><span class="sxs-lookup"><span data-stu-id="4cd76-120">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `geolocation`.</span></span> <span data-ttu-id="4cd76-121">Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der Standortfunktionen beginnen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-121">It allows your app to ask for requisite permissions from users before they start using the location capabilities.</span></span> <span data-ttu-id="4cd76-122">Das Update für das App-Manifest lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4cd76-122">The update for app manifest is as follows:</span></span>

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> <span data-ttu-id="4cd76-123">Die Eingabeaufforderung **"Berechtigungen anfordern"** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="4cd76-123">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="4cd76-124">Weitere Informationen finden Sie unter Anfordern von [Geräteberechtigungen.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="4cd76-124">For more information, see [request device permissions](native-device-permissions.md).</span></span>

## <a name="location-apis"></a><span data-ttu-id="4cd76-125">Standort-APIs</span><span class="sxs-lookup"><span data-stu-id="4cd76-125">Location APIs</span></span>

<span data-ttu-id="4cd76-126">Sie müssen die folgenden APIs verwenden, um die Standortfunktionen Ihres Geräts zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="4cd76-126">You must use the following set of APIs to enable your device's location capabilities:</span></span>

| <span data-ttu-id="4cd76-127">API</span><span class="sxs-lookup"><span data-stu-id="4cd76-127">API</span></span>      | <span data-ttu-id="4cd76-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4cd76-128">Description</span></span>   |
| --- | --- |
|[<span data-ttu-id="4cd76-129">Getlocation</span><span class="sxs-lookup"><span data-stu-id="4cd76-129">getLocation</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) | <span data-ttu-id="4cd76-130">Gibt den aktuellen Gerätestandort des Benutzers an oder öffnet die systemeigene Standortauswahl und gibt den vom Benutzer ausgewählten Standort zurück.</span><span class="sxs-lookup"><span data-stu-id="4cd76-130">Gives user’s current device location or opens native location picker and returns the location chosen by the user.</span></span> |
|[<span data-ttu-id="4cd76-131">showLocation</span><span class="sxs-lookup"><span data-stu-id="4cd76-131">showLocation</span></span>](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) | <span data-ttu-id="4cd76-132">Zeigt die Position auf der Karte an.</span><span class="sxs-lookup"><span data-stu-id="4cd76-132">Shows location on map.</span></span> |

> [!NOTE]
> <span data-ttu-id="4cd76-133">Die `getLocation()` API enthält die folgenden [Eingabekonfigurationen](/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true) `allowChooseLocation` und `showMap` .</span><span class="sxs-lookup"><span data-stu-id="4cd76-133">The `getLocation()` API comes along with following [input configurations](/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true), `allowChooseLocation` and `showMap`.</span></span> <br/> <span data-ttu-id="4cd76-134">Wenn der Wert `allowChooseLocation` *"true"* lautet, können die Benutzer einen beliebigen Speicherort auswählen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-134">If the value of `allowChooseLocation` is *true*, then the users can choose any location of their choice.</span></span><br/>  <span data-ttu-id="4cd76-135">Wenn der Wert *"false"* ist, können die Benutzer ihren aktuellen Standort nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="4cd76-135">If the value is *false*, then the users cannot change their current location.</span></span><br/> <span data-ttu-id="4cd76-136">Wenn der Wert `showMap` *"false"* lautet, wird der aktuelle Speicherort abgerufen, ohne die Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-136">If the value of `showMap` is *false*, the current location is fetched without displaying the map.</span></span> <span data-ttu-id="4cd76-137">`showMap` wird ignoriert, wenn `allowChooseLocation` sie auf *"true"* festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="4cd76-137">`showMap` is ignored if `allowChooseLocation` is set to *true*.</span></span>

<span data-ttu-id="4cd76-138">Die folgende Abbildung zeigt die Web-App-Erfahrung mit Standortfunktionen:</span><span class="sxs-lookup"><span data-stu-id="4cd76-138">The following image depicts web app experience of location capabilities:</span></span>

![Web-App-Erfahrung für Standortfunktionen](../../assets/images/tabs/location-capability.png)

### <a name="code-snippets"></a><span data-ttu-id="4cd76-140">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="4cd76-140">Code snippets</span></span>

<span data-ttu-id="4cd76-141">**Aufrufen `getLocation` der API zum Abrufen des Speicherorts:**</span><span class="sxs-lookup"><span data-stu-id="4cd76-141">**Calling `getLocation` API to retrieve the location:**</span></span>

```javascript
let locationProps = {"allowChooseLocation":true,"showMap":true};
microsoftTeams.location.getLocation(locationProps, (err: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
          if (err) {
            output(err);
            return;
          }
          output(JSON.stringify(location));
});
```

<span data-ttu-id="4cd76-142">**Aufrufen `showLocation` der API zum Anzeigen des Speicherorts:**</span><span class="sxs-lookup"><span data-stu-id="4cd76-142">**Calling `showLocation` API to display the location:**</span></span>

```javascript
let location = {"latitude":17,"longitude":17};
microsoftTeams.location.showLocation(location, (err: microsoftTeams.SdkError, result: boolean) => {
          if (err) {
            output(err);
            return;
          }
     output(result);
});
```

## <a name="error-handling"></a><span data-ttu-id="4cd76-143">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="4cd76-143">Error handling</span></span>

<span data-ttu-id="4cd76-144">Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams App ordnungsgemäß behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="4cd76-144">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="4cd76-145">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="4cd76-145">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="4cd76-146">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="4cd76-146">Error code</span></span> |  <span data-ttu-id="4cd76-147">Fehlername</span><span class="sxs-lookup"><span data-stu-id="4cd76-147">Error name</span></span>     | <span data-ttu-id="4cd76-148">Bedingung</span><span class="sxs-lookup"><span data-stu-id="4cd76-148">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="4cd76-149">**100**</span><span class="sxs-lookup"><span data-stu-id="4cd76-149">**100**</span></span> | <span data-ttu-id="4cd76-150">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="4cd76-150">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="4cd76-151">Die API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4cd76-151">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="4cd76-152">**500**</span><span class="sxs-lookup"><span data-stu-id="4cd76-152">**500**</span></span> | <span data-ttu-id="4cd76-153">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="4cd76-153">INTERNAL_ERROR</span></span> | <span data-ttu-id="4cd76-154">Beim Ausführen des erforderlichen Vorgangs ist ein interner Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="4cd76-154">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="4cd76-155">**1000**</span><span class="sxs-lookup"><span data-stu-id="4cd76-155">**1000**</span></span> | <span data-ttu-id="4cd76-156">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="4cd76-156">PERMISSION_DENIED</span></span> |<span data-ttu-id="4cd76-157">Der Benutzer verweigerte Standortberechtigungen für die Teams-App oder die Web-App.</span><span class="sxs-lookup"><span data-stu-id="4cd76-157">User denied location permissions to the Teams App or the web-app .</span></span>|
| <span data-ttu-id="4cd76-158">**4000**</span><span class="sxs-lookup"><span data-stu-id="4cd76-158">**4000**</span></span> | <span data-ttu-id="4cd76-159">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="4cd76-159">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="4cd76-160">Die API wird mit falschen oder nicht ausreichenden obligatorischen Argumenten aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-160">API is invoked with wrong or insufficient mandatory arguments.</span></span>|
| <span data-ttu-id="4cd76-161">**8000**</span><span class="sxs-lookup"><span data-stu-id="4cd76-161">**8000**</span></span> | <span data-ttu-id="4cd76-162">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="4cd76-162">USER_ABORT</span></span> |<span data-ttu-id="4cd76-163">Der Benutzer hat den Vorgang abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="4cd76-163">User cancelled the operation.</span></span>|
| <span data-ttu-id="4cd76-164">**9000**</span><span class="sxs-lookup"><span data-stu-id="4cd76-164">**9000**</span></span> | <span data-ttu-id="4cd76-165">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="4cd76-165">OLD_PLATFORM</span></span> | <span data-ttu-id="4cd76-166">Der Benutzer befindet sich auf einem alten Plattformbuild, in dem die Implementierung der API nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="4cd76-166">User is on old platform build where implementation of the API is not present.</span></span> <span data-ttu-id="4cd76-167">Das Upgrade des Builds sollte das Problem beheben.</span><span class="sxs-lookup"><span data-stu-id="4cd76-167">Upgrading the build should resolve the issue.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4cd76-168">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4cd76-168">See also</span></span>

* [<span data-ttu-id="4cd76-169">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="4cd76-169">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)
* [<span data-ttu-id="4cd76-170">Integrieren von QR-Code oder Strichcodescanner-Funktion in Teams</span><span class="sxs-lookup"><span data-stu-id="4cd76-170">Integrate QR code or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
* [<span data-ttu-id="4cd76-171">Integrieren der Personenauswahlfunktion in Teams</span><span class="sxs-lookup"><span data-stu-id="4cd76-171">Integrate People Picker capability in Teams</span></span>](people-picker-capability.md)
