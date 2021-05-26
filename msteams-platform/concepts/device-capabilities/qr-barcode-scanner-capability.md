---
title: QR- oder Barcode-Scannerfunktion integrieren
author: Rajeshwari-v
description: Verwenden des Teams JavaScript-Client-SDK zum Nutzen der QR- oder Barcodescannerfunktion
keywords: Kameramedien qr code qrcode Strichcode Barcodescanner Scanfunktionen systemeigene Geräteberechtigungen
localization_priority: Normal
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 9b85de05bea8c9f704f4d8138b041b90e159b10f
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646562"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a>QR- oder Barcode-Scannerfunktion integrieren 

In diesem Dokument erfahren Sie, wie Sie die QR- oder Strichcodescannerfunktion integrieren. 

Barcode ist eine Methode zum Darstellen von Daten in einem visuellen und maschinenlesbaren Format. Der Strichcode enthält Informationen zu einem Produkt, z. B. einen Typ, eine Größe, einen Hersteller und ein Ursprungsland in Form von Balken und Leerzeichen. Der Code wird mithilfe des optischen Scanners auf der nativen Gerätekamera gelesen. Für eine reichhaltigere Zusammenarbeit können Sie die QR- oder Strichcodescannerfunktion, die in der Teams-Plattform bereitgestellt wird, in Ihre Teams integrieren.   

Sie können das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die tools zur Verfügung stellt, die für Ihre App für den Zugriff auf die systemeigenen Gerätefunktionen des [Benutzers erforderlich sind.](native-device-permissions.md) Verwenden Sie die [scanBarCode-API,](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) um die Scannerfunktion in Ihre App zu integrieren. 

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a>Vorteile der Integration von QR- oder Barcodescannerfunktionen

Nachfolgend finden Sie die Vorteile der Integration von QR- oder Barcodescannerfunktionen: 

* Die Integration ermöglicht Web-App-Entwicklern auf Teams-Plattform die Verwendung von QR- oder Barcodescanfunktionen mit Teams JavaScript-Client-SDK.
* Bei diesem Feature muss der Benutzer nur einen QR- oder Strichcode in einem Frame in der Mitte der Scannerbenutzeroberfläche ausrichten, und der Code wird automatisch gescannt. Die gespeicherten Daten werden mit der aufrufenden Web-App wieder freigegeben. Dadurch werden Unannehmlichkeiten und menschliche Fehler vermieden, wenn Sie langwierige Produktcodes oder andere relevante Informationen manuell eingeben.

Zum Integrieren der QR- oder Barcodescannerfunktion müssen Sie die App-Manifestdatei aktualisieren und die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) aufrufen. Für eine effektive Integration müssen Sie [](#code-snippet) über ein gutes Verständnis des Codeausschnitts zum Aufrufen der [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) verfügen, mit der Sie systemeigene QR- oder Strichcodescannerfunktionen verwenden können. Die API gibt einen Fehler für einen nicht unterstützten Barcodestandard an.
Es ist wichtig, sich [](#error-handling) mit den API-Antwortfehlern vertraut zu machen, um die Fehler in Ihrer app Teams behandeln.

> [!NOTE] 
> Derzeit ist Microsoft Teams unterstützung für QR- oder Strichcodescanner nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Updatemanifest

Aktualisieren Sie Teams [Appmanifest.jsdatei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die `devicePermissions` Eigenschaft hinzufügen und `media` angeben. Sie ermöglicht Es Ihrer App, die erforderlichen Berechtigungen von Benutzern zu fordern, bevor sie mit der Verwendung der QR- oder Strichcodescannerfunktion beginnen.

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine Teams-API initiiert wird. Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).

## <a name="scanbarcode-api"></a>ScanBarCode-API

Die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) ruft ein Scannersteuerelement auf, mit dem der Benutzer verschiedene Barcodetypen scannen kann, und gibt das Ergebnis als Zeichenfolge zurück.

Zum Anpassen der Barcodescanerfahrung wird die optionale [Barcodekonfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.barcodeconfig?view=msteams-client-js-latest&preserve-view=true) als Eingabe an [die scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) übergeben. Sie können das Intervall für das Überprüfungs-Zeitintervall in Sekunden mithilfe von `timeOutIntervalInSec` angeben. Der Standardwert beträgt 30 Sekunden, der Höchstwert 60 Sekunden.

Die **scanBarCode()-API** unterstützt die folgenden Barcodetypen:

| Strichcodetyp | Unter Android unterstützt | Unter iOS unterstützt |
| ---------- | ---------- | ------------ |
| Codeleiste | Ja | Nein |
| Code 39 | Ja | Ja | 
| Code 93 | Ja | Ja |
| Code 128 | Ja | Ja |
| EAN-13 | Ja | Ja |
| EAN-8 | Ja | Ja |
| ITF | Nein | Ja |
| QR-Code | Ja | Ja |
| RSS-Erweitert | Ja | Nein |
| RSS-14 | Ja | Nein |
| UPC-A | Ja | Ja |
| UPC-E | Ja | Ja |

**Web-App-Erfahrung für `ScanBarCode` API für QR- oder Barcodescannerfunktionen** 
 ![ Web-App-Erfahrung für Qr- oder Strichcodescannerfunktionen](../../assets/images/tabs/qr-barcode-scanner-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer App Teams werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden: 

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | DIE API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Die Berechtigung wird vom Benutzer verweigert.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000** | INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
| **8000** | USER_ABORT |Der Benutzer bricht den Vorgang ab.|
| **8001** | OPERATION_TIMED_OUT | Der Strichcode konnte im angegebenen Zeitintervall nicht erkannt werden.|
| **9000** | OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|

## <a name="code-snippet"></a>Codeausschnitt

**Aufrufen `ScanBarCode()` API** zum Scannen von QR- oder Strichcode mithilfe der Kamera:

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

## <a name="see-also"></a>Siehe auch

* [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
* [Integrieren von Standortfunktionen in Teams](location-capability.md)
