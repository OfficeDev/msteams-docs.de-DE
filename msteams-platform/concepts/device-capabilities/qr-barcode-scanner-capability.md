---
title: QR- oder Barcode-Scannerfunktion integrieren
description: Verwenden des Teams JavaScript-Client-SDK zum Nutzen der QR- oder Barcodescannerfunktion
keywords: Kameramedien qr code qrcode Strichcode Barcodescanner Scanfunktionen systemeigene Geräteberechtigungen
ms.author: lajanuar
ms.openlocfilehash: 1a13de1a4d9e03f0f36f03af0fdd948cf74a0392
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449416"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a><span data-ttu-id="2d063-104">QR- oder Barcode-Scannerfunktion integrieren</span><span class="sxs-lookup"><span data-stu-id="2d063-104">Integrate QR or barcode scanner capability</span></span> 

<span data-ttu-id="2d063-105">In diesem Dokument erfahren Sie, wie Sie die QR- oder Strichcodescannerfunktion integrieren.</span><span class="sxs-lookup"><span data-stu-id="2d063-105">This document guides you on how to integrate the QR or barcode scanner capability.</span></span> 

<span data-ttu-id="2d063-106">Barcode ist eine Methode zum Darstellen von Daten in einem visuellen und maschinenlesbaren Format.</span><span class="sxs-lookup"><span data-stu-id="2d063-106">Barcode is a method of representing data in a visual and machine-readable form.</span></span> <span data-ttu-id="2d063-107">Der Strichcode enthält Informationen zu einem Produkt, z. B. einen Typ, eine Größe, einen Hersteller und ein Ursprungsland in Form von Balken und Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="2d063-107">The barcode contains information about a product, such as a type, size, manufacturer, and Country of origin in the form of bars and spaces.</span></span> <span data-ttu-id="2d063-108">Der Code wird mithilfe des optischen Scanners auf der nativen Gerätekamera gelesen.</span><span class="sxs-lookup"><span data-stu-id="2d063-108">The code is read using the optical scanner on your native device camera.</span></span> <span data-ttu-id="2d063-109">Für eine reichhaltigere Zusammenarbeit können Sie die QR- oder Strichcodescannerfunktion, die in der Teams-Plattform bereitgestellt wird, in Ihre Teams-App integrieren.</span><span class="sxs-lookup"><span data-stu-id="2d063-109">For a richer collaborative experience, you can integrate the QR or barcode scanner capability provided in the Teams platform with your Teams app.</span></span>   

<span data-ttu-id="2d063-110">Sie können [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die tools zur Verfügung stellt, die Für Ihre App erforderlich sind, um auf die systemeigenen Gerätefunktionen des Benutzers zu [zugreifen.](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="2d063-110">You can use [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), which provides the tools necessary for your app to access the user’s [native device capabilities](native-device-permissions.md).</span></span> <span data-ttu-id="2d063-111">Verwenden Sie die `scanBarCode` API, um die Scannerfunktion in Ihre App zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="2d063-111">Use the `scanBarCode` API to integrate the scanner capability within your app.</span></span> 

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a><span data-ttu-id="2d063-112">Vorteile der Integration von QR- oder Barcodescannerfunktionen</span><span class="sxs-lookup"><span data-stu-id="2d063-112">Advantage of integrating QR or barcode scanner capability</span></span>

<span data-ttu-id="2d063-113">Nachfolgend finden Sie die Vorteile der Integration von QR- oder Barcodescannerfunktionen:</span><span class="sxs-lookup"><span data-stu-id="2d063-113">Following are the advantages of integration of QR or barcode scanner capabilities:</span></span> 

* <span data-ttu-id="2d063-114">Die Integration ermöglicht Es Web-App-Entwicklern auf der Teams-Plattform, QR- oder Barcodescanfunktionen mit dem Teams JavaScript-Client-SDK zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="2d063-114">The integration allows web app developers on Teams platform to leverage QR or barcode scanning functionality with Teams JavaScript client SDK.</span></span>
* <span data-ttu-id="2d063-115">Bei diesem Feature muss der Benutzer nur einen QR- oder Strichcode in einem Frame in der Mitte der Scannerbenutzeroberfläche ausrichten, und der Code wird automatisch gescannt.</span><span class="sxs-lookup"><span data-stu-id="2d063-115">With this feature, the user only needs to align a QR or barcode within a frame at the center of the scanner UI and the code gets scanned automatically.</span></span> <span data-ttu-id="2d063-116">Die gespeicherten Daten werden mit der aufrufenden Web-App wieder freigegeben.</span><span class="sxs-lookup"><span data-stu-id="2d063-116">The stored data is shared back with the calling web app.</span></span> <span data-ttu-id="2d063-117">Dadurch werden Unannehmlichkeiten und menschliche Fehler vermieden, wenn Sie langwierige Produktcodes oder andere relevante Informationen manuell eingeben.</span><span class="sxs-lookup"><span data-stu-id="2d063-117">This avoids the inconvenience and human-errors of entering lengthy product codes or other relevant information manually.</span></span>

<span data-ttu-id="2d063-118">Um die QR- oder Strichcodescannerfunktion zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die `scanBarCode` API aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2d063-118">To integrate QR or barcode scanner capability, you must update the app manifest file and call the `scanBarCode` API.</span></span> <span data-ttu-id="2d063-119">Für eine effektive Integration müssen Sie [](#code-snippet) über ein gutes Verständnis des Codeausschnitts für den Aufruf der API verfügen, mit dem Sie systemeigene QR- oder Strichcodescannerfunktionen `scanBarCode` verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2d063-119">For effective integration, you must have a good understanding of [code snippet](#code-snippet) for calling the `scanBarCode` API, which allows you to use native QR or barcode scanner capability.</span></span> <span data-ttu-id="2d063-120">Die API gibt einen Fehler für einen nicht unterstützten Barcodestandard an.</span><span class="sxs-lookup"><span data-stu-id="2d063-120">The API gives an error for an unsupported barcode standard.</span></span>
<span data-ttu-id="2d063-121">Es ist wichtig, sich mit den API-Antwortfehlern vertraut zu [machen,](#error-handling) um die Fehler in Ihrer Teams-App zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="2d063-121">It is important to familiarize yourself with the [API response errors](#error-handling) to handle the errors in your Teams app.</span></span>

> [!NOTE] 
> <span data-ttu-id="2d063-122">Derzeit ist die Unterstützung von Microsoft Teams für QR- oder Strichcodescanner nur für mobile Clients verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2d063-122">Currently, Microsoft Teams support for QR or barcode scanner capability is only available for mobile clients.</span></span>

## <a name="update-manifest"></a><span data-ttu-id="2d063-123">Updatemanifest</span><span class="sxs-lookup"><span data-stu-id="2d063-123">Update manifest</span></span>

<span data-ttu-id="2d063-124">Aktualisieren Sie Ihre [ Teamsmanifest.js-App-Datei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die `devicePermissions` -Eigenschaft hinzufügen und `media` angeben.</span><span class="sxs-lookup"><span data-stu-id="2d063-124">Update your Teams app [manifest.json](../../resources/schema/manifest-schema.md#devicepermissions) file by adding the `devicePermissions` property and specifying `media`.</span></span> <span data-ttu-id="2d063-125">Sie ermöglicht Es Ihrer App, die erforderlichen Berechtigungen von Benutzern zu fordern, bevor sie mit der Verwendung der QR- oder Strichcodescannerfunktion beginnen.</span><span class="sxs-lookup"><span data-stu-id="2d063-125">It allows your app to ask for requisite permissions from users before they start using  the QR or barcode scanner capability.</span></span>

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> <span data-ttu-id="2d063-126">Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird.</span><span class="sxs-lookup"><span data-stu-id="2d063-126">The **Request Permissions** prompt is automatically displayed when a relevant Teams API is initiated.</span></span> <span data-ttu-id="2d063-127">Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).</span><span class="sxs-lookup"><span data-stu-id="2d063-127">For more information, see [Request device permissions](native-device-permissions.md).</span></span>

## <a name="scanbarcode-api"></a><span data-ttu-id="2d063-128">ScanBarCode-API</span><span class="sxs-lookup"><span data-stu-id="2d063-128">ScanBarCode API</span></span>

<span data-ttu-id="2d063-129">Die API ruft das Scannersteuerelement auf, mit dem der Benutzer verschiedene Barcodetypen überprüfen kann, und gibt das `ScanBarCode` Ergebnis als Zeichenfolge zurück.</span><span class="sxs-lookup"><span data-stu-id="2d063-129">The `ScanBarCode` API invokes scanner control that enables the user to scan different types of barcode, and returns the result as a string.</span></span>

<span data-ttu-id="2d063-130">Zum Anpassen der Barcodescanerfahrung wird die optionale Barcodekonfiguration als Eingabe an die `ScanBarCode` API übergeben.</span><span class="sxs-lookup"><span data-stu-id="2d063-130">To customize the barcode scanning experience, optional barcode configuration is passed as input to `ScanBarCode` API.</span></span> <span data-ttu-id="2d063-131">Sie können das Intervall für das Überprüfungs-Zeitintervall in Sekunden mithilfe von `timeOutIntervalInSec` angeben.</span><span class="sxs-lookup"><span data-stu-id="2d063-131">You can specify the scan time-out interval in seconds using `timeOutIntervalInSec`.</span></span> <span data-ttu-id="2d063-132">Der Standardwert beträgt 30 Sekunden, der Höchstwert 60 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="2d063-132">Its default value is 30 seconds and the maximum value is 60 seconds.</span></span>

<span data-ttu-id="2d063-133">Die **scanBarCode()-API** unterstützt die folgenden Barcodetypen:</span><span class="sxs-lookup"><span data-stu-id="2d063-133">The **scanBarCode()** API supports the following barcode types:</span></span>

| <span data-ttu-id="2d063-134">Strichcodetyp</span><span class="sxs-lookup"><span data-stu-id="2d063-134">Barcode Type</span></span> | <span data-ttu-id="2d063-135">Unter Android unterstützt</span><span class="sxs-lookup"><span data-stu-id="2d063-135">Supported on Android</span></span> | <span data-ttu-id="2d063-136">Unter iOS unterstützt</span><span class="sxs-lookup"><span data-stu-id="2d063-136">Supported on iOS</span></span> |
| ---------- | ---------- | ------------ |
| <span data-ttu-id="2d063-137">Codeleiste</span><span class="sxs-lookup"><span data-stu-id="2d063-137">Codebar</span></span> | <span data-ttu-id="2d063-138">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-138">Yes</span></span> | <span data-ttu-id="2d063-139">Nein</span><span class="sxs-lookup"><span data-stu-id="2d063-139">No</span></span> |
| <span data-ttu-id="2d063-140">Code 39</span><span class="sxs-lookup"><span data-stu-id="2d063-140">Code 39</span></span> | <span data-ttu-id="2d063-141">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-141">Yes</span></span> | <span data-ttu-id="2d063-142">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-142">Yes</span></span> | 
| <span data-ttu-id="2d063-143">Code 93</span><span class="sxs-lookup"><span data-stu-id="2d063-143">Code 93</span></span> | <span data-ttu-id="2d063-144">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-144">Yes</span></span> | <span data-ttu-id="2d063-145">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-145">Yes</span></span> |
| <span data-ttu-id="2d063-146">Code 128</span><span class="sxs-lookup"><span data-stu-id="2d063-146">Code 128</span></span> | <span data-ttu-id="2d063-147">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-147">Yes</span></span> | <span data-ttu-id="2d063-148">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-148">Yes</span></span> |
| <span data-ttu-id="2d063-149">EAN-13</span><span class="sxs-lookup"><span data-stu-id="2d063-149">EAN-13</span></span> | <span data-ttu-id="2d063-150">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-150">Yes</span></span> | <span data-ttu-id="2d063-151">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-151">Yes</span></span> |
| <span data-ttu-id="2d063-152">EAN-8</span><span class="sxs-lookup"><span data-stu-id="2d063-152">EAN-8</span></span> | <span data-ttu-id="2d063-153">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-153">Yes</span></span> | <span data-ttu-id="2d063-154">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-154">Yes</span></span> |
| <span data-ttu-id="2d063-155">ITF</span><span class="sxs-lookup"><span data-stu-id="2d063-155">ITF</span></span> | <span data-ttu-id="2d063-156">Nein</span><span class="sxs-lookup"><span data-stu-id="2d063-156">No</span></span> | <span data-ttu-id="2d063-157">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-157">Yes</span></span> |
| <span data-ttu-id="2d063-158">QR-Code</span><span class="sxs-lookup"><span data-stu-id="2d063-158">QR Code</span></span> | <span data-ttu-id="2d063-159">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-159">Yes</span></span> | <span data-ttu-id="2d063-160">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-160">Yes</span></span> |
| <span data-ttu-id="2d063-161">RSS-Erweitert</span><span class="sxs-lookup"><span data-stu-id="2d063-161">RSS Expanded</span></span> | <span data-ttu-id="2d063-162">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-162">Yes</span></span> | <span data-ttu-id="2d063-163">Nein</span><span class="sxs-lookup"><span data-stu-id="2d063-163">No</span></span> |
| <span data-ttu-id="2d063-164">RSS-14</span><span class="sxs-lookup"><span data-stu-id="2d063-164">RSS-14</span></span> | <span data-ttu-id="2d063-165">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-165">Yes</span></span> | <span data-ttu-id="2d063-166">Nein</span><span class="sxs-lookup"><span data-stu-id="2d063-166">No</span></span> |
| <span data-ttu-id="2d063-167">UPC-A</span><span class="sxs-lookup"><span data-stu-id="2d063-167">UPC-A</span></span> | <span data-ttu-id="2d063-168">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-168">Yes</span></span> | <span data-ttu-id="2d063-169">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-169">Yes</span></span> |
| <span data-ttu-id="2d063-170">UPC-E</span><span class="sxs-lookup"><span data-stu-id="2d063-170">UPC-E</span></span> | <span data-ttu-id="2d063-171">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-171">Yes</span></span> | <span data-ttu-id="2d063-172">Ja</span><span class="sxs-lookup"><span data-stu-id="2d063-172">Yes</span></span> |

<span data-ttu-id="2d063-173">**Web-App-Erfahrung für `ScanBarCode` API für QR- oder Barcodescannerfunktionen** 
 ![ Web-App-Erfahrung für Qr- oder Strichcodescannerfunktionen](../../assets/images/tabs/qr-barcode-scanner-capability.png)</span><span class="sxs-lookup"><span data-stu-id="2d063-173">**Web app experience for `ScanBarCode` API for QR or barcode scanner capability**
![web app experience for qr or barcode scanner capability](../../assets/images/tabs/qr-barcode-scanner-capability.png)</span></span>

## <a name="error-handling"></a><span data-ttu-id="2d063-174">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="2d063-174">Error handling</span></span>

<span data-ttu-id="2d063-175">Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App angemessen umgangen werden.</span><span class="sxs-lookup"><span data-stu-id="2d063-175">You must ensure to handle these errors appropriately in your Teams app.</span></span> <span data-ttu-id="2d063-176">In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:</span><span class="sxs-lookup"><span data-stu-id="2d063-176">The following table lists the error codes and the conditions under which the errors are generated:</span></span> 

|<span data-ttu-id="2d063-177">Fehlercode</span><span class="sxs-lookup"><span data-stu-id="2d063-177">Error code</span></span> |  <span data-ttu-id="2d063-178">Fehlername</span><span class="sxs-lookup"><span data-stu-id="2d063-178">Error name</span></span>     | <span data-ttu-id="2d063-179">Bedingung</span><span class="sxs-lookup"><span data-stu-id="2d063-179">Condition</span></span>|
| --------- | --------------- | -------- |
| <span data-ttu-id="2d063-180">**100**</span><span class="sxs-lookup"><span data-stu-id="2d063-180">**100**</span></span> | <span data-ttu-id="2d063-181">NOT_SUPPORTED_ON_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="2d063-181">NOT_SUPPORTED_ON_PLATFORM</span></span> | <span data-ttu-id="2d063-182">DIE API wird auf der aktuellen Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2d063-182">API is not supported on the current platform.</span></span>|
| <span data-ttu-id="2d063-183">**500**</span><span class="sxs-lookup"><span data-stu-id="2d063-183">**500**</span></span> | <span data-ttu-id="2d063-184">INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="2d063-184">INTERNAL_ERROR</span></span> | <span data-ttu-id="2d063-185">Interner Fehler beim Ausführen des erforderlichen Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="2d063-185">Internal error is encountered while performing the required operation.</span></span>|
| <span data-ttu-id="2d063-186">**1000**</span><span class="sxs-lookup"><span data-stu-id="2d063-186">**1000**</span></span> | <span data-ttu-id="2d063-187">PERMISSION_DENIED</span><span class="sxs-lookup"><span data-stu-id="2d063-187">PERMISSION_DENIED</span></span> |<span data-ttu-id="2d063-188">Die Berechtigung wird vom Benutzer verweigert.</span><span class="sxs-lookup"><span data-stu-id="2d063-188">Permission is denied by the user.</span></span>|
| <span data-ttu-id="2d063-189">**3000**</span><span class="sxs-lookup"><span data-stu-id="2d063-189">**3000**</span></span> | <span data-ttu-id="2d063-190">NO_HW_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="2d063-190">NO_HW_SUPPORT</span></span> | <span data-ttu-id="2d063-191">Die zugrunde liegende Hardware unterstützt die Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="2d063-191">Underlying hardware does not support the capability.</span></span>|
| <span data-ttu-id="2d063-192">**4000**</span><span class="sxs-lookup"><span data-stu-id="2d063-192">**4000**</span></span> | <span data-ttu-id="2d063-193">INVALID_ARGUMENTS</span><span class="sxs-lookup"><span data-stu-id="2d063-193">INVALID_ARGUMENTS</span></span> | <span data-ttu-id="2d063-194">Mindestens ein Argument ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="2d063-194">One or more arguments are invalid.</span></span>|
| <span data-ttu-id="2d063-195">**8000**</span><span class="sxs-lookup"><span data-stu-id="2d063-195">**8000**</span></span> | <span data-ttu-id="2d063-196">USER_ABORT</span><span class="sxs-lookup"><span data-stu-id="2d063-196">USER_ABORT</span></span> |<span data-ttu-id="2d063-197">Der Benutzer bricht den Vorgang ab.</span><span class="sxs-lookup"><span data-stu-id="2d063-197">User aborts the operation.</span></span>|
| <span data-ttu-id="2d063-198">**8001**</span><span class="sxs-lookup"><span data-stu-id="2d063-198">**8001**</span></span> | <span data-ttu-id="2d063-199">OPERATION_TIMED_OUT</span><span class="sxs-lookup"><span data-stu-id="2d063-199">OPERATION_TIMED_OUT</span></span> | <span data-ttu-id="2d063-200">Der Strichcode konnte im angegebenen Zeitintervall nicht erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="2d063-200">Could not detect the barcode in the given time interval.</span></span>|
| <span data-ttu-id="2d063-201">**9000**</span><span class="sxs-lookup"><span data-stu-id="2d063-201">**9000**</span></span> | <span data-ttu-id="2d063-202">OLD_PLATFORM</span><span class="sxs-lookup"><span data-stu-id="2d063-202">OLD_PLATFORM</span></span> | <span data-ttu-id="2d063-203">Plattformcode ist veraltet und implementiert diese API nicht.</span><span class="sxs-lookup"><span data-stu-id="2d063-203">Platform code is outdated and does not implement this API.</span></span>|

## <a name="code-snippet"></a><span data-ttu-id="2d063-204">Codeausschnitt</span><span class="sxs-lookup"><span data-stu-id="2d063-204">Code snippet</span></span>

<span data-ttu-id="2d063-205">**Aufrufen `ScanBarCode()` API** zum Scannen von QR- oder Strichcode mithilfe der Kamera:</span><span class="sxs-lookup"><span data-stu-id="2d063-205">**Calling `ScanBarCode()` API** for scanning QR or barcode using camera:</span></span>

```javascript
const config: microsoftTeams.media.BarCodeConfig = {
  timeOutIntervalInSec: 30};
microsoftTeams.media.scanBarCode((error: microsoftTeams.SdkError, decodedText: string) => {
  if (error) {
    if (error.message) {
      output(" ErrorCode: " + error.errorCode + error.message);
    } else {
      output(" ErrorCode: " + error.errorCode);
    }
  } else if (decodedText) {
    output(decodedText);
  }
}, config);
```

## <a name="see-also"></a><span data-ttu-id="2d063-206">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2d063-206">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d063-207">Integrieren von Medienfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="2d063-207">Integrate media capabilities in Teams</span></span>](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d063-208">Integrieren von Standortfunktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="2d063-208">Integrate location capabilities in Teams</span></span>](location-capability.md)