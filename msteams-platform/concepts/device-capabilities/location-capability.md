---
title: Integration von Standortfunktionen
author: Rajeshwari-v
description: Verwenden des Teams JavaScript-Client-SDK zum Nutzen von Standortfunktionen
keywords: Standortzuordnungsfunktionen Systemeigene Geräteberechtigungen
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: d10f2df48ee5b75252508fbc51e5a31df9ea083f
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058369"
---
# <a name="integrate-location-capabilities"></a><span data-ttu-id="3285f-104">Integration von Standortfunktionen</span><span class="sxs-lookup"><span data-stu-id="3285f-104">Integrate location capabilities</span></span> 

<span data-ttu-id="3285f-105">In diesem Dokument erfahren Sie, wie Sie die Standortfunktionen des systemeigenen Geräts in Ihre Teams-App integrieren.</span><span class="sxs-lookup"><span data-stu-id="3285f-105">This document guides you on how to integrate the location capabilities of native device with your Teams app.</span></span>  

<span data-ttu-id="3285f-106">Sie können [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die tools zur Verfügung stellt, die Für Ihre App erforderlich sind, um auf die systemeigenen Gerätefunktionen des Benutzers zu [zugreifen.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="3285f-106">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides the tools necessary for your app to access the user’s [native device capabilities](native-device-permissions.md).</span></span> <span data-ttu-id="3285f-107">Verwenden Sie die Standort-APIs, z. B. [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) und [showLocation,](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) um die Funktionen in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="3285f-107">Use the location APIs, such as [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) and [showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) to integrate the capabilities within your app.</span></span> 

## <a name="advantages-of-integrating-location-capabilities"></a><span data-ttu-id="3285f-108">Vorteile der Integration von Standortfunktionen</span><span class="sxs-lookup"><span data-stu-id="3285f-108">Advantages of integrating location capabilities</span></span>

<span data-ttu-id="3285f-109">Der Hauptvorteil der Integration von Standortfunktionen in Ihre Teams-Apps besteht in der Möglichkeit, dass Web-App-Entwickler auf der Microsoft Teams-Plattform Standortfunktionen mit Dem JavaScript-Client-SDK von Microsoft Teams nutzen können.</span><span class="sxs-lookup"><span data-stu-id="3285f-109">The main advantage of integrating location capabilities in your Teams apps is that it allows web app developers on Teams platform to leverage location functionality with Microsoft Teams JavaScript client SDK.</span></span> 

<span data-ttu-id="3285f-110">In den folgenden Beispielen wird gezeigt, wie die Integration von Standortfunktionen in verschiedenen Szenarien verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="3285f-110">Following examples show how the integration of location capabilities is used in different scenarios:</span></span>
* <span data-ttu-id="3285f-111">In einer Fabrik kann der Vorgesetzte die Anwesenheit von Mitarbeitern nachverfolgen, indem er sie bittet, ein Selfie in der Nähe der Fabrik zu machen und es über die angegebene App zu teilen.</span><span class="sxs-lookup"><span data-stu-id="3285f-111">In a factory, the supervisor can track the attendance of workers by asking them to take a selfie in the vicinity of the factory and share it through the specified app.</span></span> <span data-ttu-id="3285f-112">Die Standortdaten werden auch zusammen mit dem Bild erfasst und gesendet.</span><span class="sxs-lookup"><span data-stu-id="3285f-112">The location data also gets captured and sent along with the image.</span></span>
* <span data-ttu-id="3285f-113">Die Standortfunktionen ermöglichen es den Wartungsmitarbeitern eines Dienstanbieters, die echten Integritätsdaten von Mobilfunkmasten mit der Verwaltung zu teilen.</span><span class="sxs-lookup"><span data-stu-id="3285f-113">The location capabilities enables the maintenance staff of a service provider to share authentic health data of cellular towers with the management.</span></span> <span data-ttu-id="3285f-114">Die Verwaltung kann jeglichen Konflikt zwischen erfassten Standortinformationen und den vom Wartungspersonal übermittelten Daten vergleichen.</span><span class="sxs-lookup"><span data-stu-id="3285f-114">The management can compare any mismatch between captured location information and the data submitted by maintenance staff.</span></span>

<span data-ttu-id="3285f-115">Zum Integrieren von Standortfunktionen müssen Sie die App-Manifestdatei aktualisieren und die APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="3285f-115">To integrate location capabilities, you must update the app manifest file and call the APIs.</span></span> <span data-ttu-id="3285f-116">Für eine effektive Integration müssen Sie [](#code-snippets) über ein gutes Verständnis von Codeausschnitten zum Aufrufen der Speicherort-APIs verfügen.</span><span class="sxs-lookup"><span data-stu-id="3285f-116">For effective integration, you must have a good understanding of [code snippets](#code-snippets) for calling the location APIs.</span></span> <span data-ttu-id="3285f-117">Es ist wichtig, sich mit den API-Antwortfehlern vertraut zu [machen,](#error-handling) um die Fehler in Ihrer Teams-App zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="3285f-117">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="3285f-118">Derzeit ist Die Unterstützung von Standortfunktionen von Microsoft Teams nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3285f-118">Currently, Microsoft Teams support for location capabilities is only available for mobile clients.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="3285f-119">Updatemanifest</span><span class="sxs-lookup"><span data-stu-id="3285f-119">Update manifest</span></span>

<span data-ttu-id="3285f-120">Aktualisieren Sie Ihre [ Teamsmanifest.js-App-Datei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die `devicePermissions` -Eigenschaft hinzufügen und `geolocation` angeben.</span><span class="sxs-lookup"><span data-stu-id="3285f-120">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `geolocation`.</span></span> <span data-ttu-id="3285f-121">Sie ermöglicht Es Ihrer App, die erforderlichen Berechtigungen von Benutzern zu fordern, bevor sie mit der Verwendung der Standortfunktionen beginnen.</span><span class="sxs-lookup"><span data-stu-id="3285f-121">It allows your app to ask for requisite permissions from users before they start using the location capabilities.</span></span>

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> <span data-ttu-id="3285f-122">Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="3285f-122">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="3285f-123">Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="3285f-123">For more information, see [request device permissions](native-device-permissions.md).</span></span>

## <a name="location-apis"></a><span data-ttu-id="3285f-124">Speicherort-APIs</span><span class="sxs-lookup"><span data-stu-id="3285f-124">Location APIs</span></span>

<span data-ttu-id="3285f-125">Sie müssen die folgenden APIs verwenden, um die Standortfunktionen Ihres Geräts zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="3285f-125">You must use the following set of APIs to enable your device's location capabilities:</span></span>

| <span data-ttu-id="3285f-126">API</span><span class="sxs-lookup"><span data-stu-id="3285f-126">API</span></span>      | <span data-ttu-id="3285f-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3285f-127">Description</span></span>   |
| --- | --- |
|[<span data-ttu-id="3285f-128">getLocation</span><span class="sxs-lookup"><span data-stu-id="3285f-128">getLocation</span></span>](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) | <span data-ttu-id="3285f-129">Gibt den aktuellen Gerätespeicherort des Benutzers an oder öffnet die systemeigene Standortauswahl und gibt den vom Benutzer ausgewählten Speicherort zurück.</span><span class="sxs-lookup"><span data-stu-id="3285f-129">Gives user’s current device location or opens native location picker and returns the location chosen by the user.</span></span> |
|[<span data-ttu-id="3285f-130">showLocation</span><span class="sxs-lookup"><span data-stu-id="3285f-130">showLocation</span></span>](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation&preserve-view=true) | <span data-ttu-id="3285f-131">Zeigt den Standort auf der Karte an</span><span class="sxs-lookup"><span data-stu-id="3285f-131">Shows location on map</span></span> |

> [!NOTE]

> <span data-ttu-id="3285f-132">Die `getLocation()` API enthält die folgenden [Eingabekonfigurationen](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true)und `allowChooseLocation` `showMap` .</span><span class="sxs-lookup"><span data-stu-id="3285f-132">The `getLocation()` API comes along with following [input configurations](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true), `allowChooseLocation` and `showMap`.</span></span> <br/> <span data-ttu-id="3285f-133">Wenn der Wert von true ist, können die Benutzer `allowChooseLocation` einen beliebigen Speicherort ihrer Wahl auswählen. </span><span class="sxs-lookup"><span data-stu-id="3285f-133">If the value of `allowChooseLocation` is *true*, then the users can choose any location of their choice.</span></span><br/>  <span data-ttu-id="3285f-134">Wenn der Wert *false ist,* können die Benutzer ihren aktuellen Speicherort nicht ändern.</span><span class="sxs-lookup"><span data-stu-id="3285f-134">If the value is *false*, then the users cannot change their current location.</span></span><br/> <span data-ttu-id="3285f-135">Wenn der Wert `showMap` von *false ist,* wird der aktuelle Speicherort abgerufen, ohne die Karte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3285f-135">If the value of `showMap` is *false*, the current location is fetched without displaying the map.</span></span> <span data-ttu-id="3285f-136">`showMap`wird ignoriert, `allowChooseLocation` wenn auf true festgelegt *ist.*</span><span class="sxs-lookup"><span data-stu-id="3285f-136">`showMap` is ignored if `allowChooseLocation` is set to *true*.</span></span> 


<span data-ttu-id="3285f-137">**Web-App-Erfahrung für Standortfunktionen** 
 ![ Web-App-Erfahrung für Standortfunktionen](../../assets/images/tabs/location-capability.png)</span><span class="sxs-lookup"><span data-stu-id="3285f-137">**Web app experience for location capabilities**
![web app experience for location capabilities](../../assets/images/tabs/location-capability.png)</span></span>

## <a name="error-handling"></a><span data-ttu-id="3285f-138">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="3285f-138">Error handling</span></span>

<span data-ttu-id="3285f-139">Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App angemessen umgangen werden.</span><span class="sxs-lookup"><span data-stu-id="3285f-139">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="3285f-140">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="3285f-140">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="3285f-141">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="3285f-141">Error code</span></span> |  <span data-ttu-id="3285f-142">Fehlername</span><span class="sxs-lookup"><span data-stu-id="3285f-142">Error name</span></span>     | <span data-ttu-id="3285f-143">Bedingung</span><span class="sxs-lookup"><span data-stu-id="3285f-143">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="3285f-144">**100**</span><span class="sxs-lookup"><span data-stu-id="3285f-144">**100**</span></span> | <span data-ttu-id="3285f-145">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="3285f-145">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="3285f-146">DIE API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3285f-146">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="3285f-147">**500**</span><span class="sxs-lookup"><span data-stu-id="3285f-147">**500**</span></span> | <span data-ttu-id="3285f-148">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="3285f-148">INTERNAL_ERROR</span></span> | <span data-ttu-id="3285f-149">Interner Fehler beim Ausführen des erforderlichen Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="3285f-149">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="3285f-150">**1000**</span><span class="sxs-lookup"><span data-stu-id="3285f-150">**1000**</span></span> | <span data-ttu-id="3285f-151">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="3285f-151">PERMISSION_DENIED</span></span> |<span data-ttu-id="3285f-152">Benutzer verweigerte Standortberechtigungen für die Teams-App oder die Web-App.</span><span class="sxs-lookup"><span data-stu-id="3285f-152">User denied location permissions to the Teams App or the web-app .</span></span>|
| <span data-ttu-id="3285f-153">**4000**</span><span class="sxs-lookup"><span data-stu-id="3285f-153">**4000**</span></span> | <span data-ttu-id="3285f-154">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="3285f-154">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="3285f-155">DIE API wird mit falschen oder unzureichenden obligatorischen Argumenten aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="3285f-155">API is invoked with wrong or insufficient mandatory arguments.</span></span>|
| <span data-ttu-id="3285f-156">**8000**</span><span class="sxs-lookup"><span data-stu-id="3285f-156">**8000**</span></span> | <span data-ttu-id="3285f-157">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="3285f-157">USER_ABORT</span></span> |<span data-ttu-id="3285f-158">Der Benutzer hat den Vorgang abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="3285f-158">User cancelled the operation.</span></span>|
| <span data-ttu-id="3285f-159">**9000**</span><span class="sxs-lookup"><span data-stu-id="3285f-159">**9000**</span></span> | <span data-ttu-id="3285f-160">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="3285f-160">OLD_PLATFORM</span></span> | <span data-ttu-id="3285f-161">Der Benutzer befindet sich im alten Plattform build, in dem die Implementierung der API nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3285f-161">User is on old platform build where implementation of the API is not present.</span></span> <span data-ttu-id="3285f-162">Beim Upgrade des Build sollte das Problem behoben werden.</span><span class="sxs-lookup"><span data-stu-id="3285f-162">Upgrading the build should resolve the issue.</span></span>|

## <a name="code-snippets"></a><span data-ttu-id="3285f-163">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="3285f-163">Code snippets</span></span>

<span data-ttu-id="3285f-164">**Aufrufen `getLocation` der API zum Abrufen des Speicherorts:**</span><span class="sxs-lookup"><span data-stu-id="3285f-164">**Calling `getLocation` API to retrieve the location:**</span></span>

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

<span data-ttu-id="3285f-165">**Aufrufen `showLocation` der API zum Anzeigen des Speicherorts:**</span><span class="sxs-lookup"><span data-stu-id="3285f-165">**Calling `showLocation` API to display the location:**</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3285f-166">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3285f-166">See also</span></span>

- [<span data-ttu-id="3285f-167">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="3285f-167">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

- [<span data-ttu-id="3285f-168">Integrieren von QR- oder Barcodescannerfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="3285f-168">Integrate QR or barcode scanner capability in Teams</span></span>](qr-barcode-scanner-capability.md)
