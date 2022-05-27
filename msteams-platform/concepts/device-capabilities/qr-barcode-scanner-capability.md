---
title: QR- oder Barcode-Scannerfunktion integrieren
author: Rajeshwari-v
description: Verwenden Teams JavaScript-Client-SDK zur Nutzung der QR- oder Strichcodescannerfunktion
keywords: Kamera Medien QR-Code qrcode Barcode Strichcode Scanner Scan-Funktionen native Geräteberechtigungen
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 1a8b89754ddf4f04fb2cc6f5890d8ce4c3f25dab
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757717"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a>QR- oder Barcode-Scannerfunktion integrieren

Barcode ist eine Methode zum Darstellen von Daten in einer visuellen und maschinenlesbaren Form. Der Barcode enthält Informationen zu einem Produkt, z. B. Typ, Größe, Hersteller und Ursprungsland in Form von Balken und Leerzeichen. Der Code wird mithilfe des optischen Scanners auf Ihrer systemeigenen Gerätekamera gelesen. Für eine umfassendere Zusammenarbeit können Sie die QR- oder Strichcodescanner-Funktion der Teams-Plattform in Ihre Teams-App integrieren.

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die Tools bereitstellt, die Ihre App für den Zugriff auf die [nativen Gerätefunktionen](native-device-permissions.md) des Benutzers benötigt. Verwenden Sie die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) , um die Scannerfunktion in Ihre App zu integrieren.

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a>Vorteile der Integration von QR- oder Strichcodescannerfunktionen

Im Folgenden sind die Vorteile der Integration von QR- oder Strichcodescanner-Funktionen aufgeführt:

* Die Integration ermöglicht Es Web-App-Entwicklern auf Teams Plattform, QR- oder Barcode-Scanfunktionen mit Teams JavaScript-Client-SDK zu nutzen.
* Bei diesem Feature muss der Benutzer nur einen QR- oder Barcode innerhalb eines Rahmens in der Mitte der Scanner-UI ausrichten, und der Code wird automatisch gescannt. Die gespeicherten Daten werden wieder für die aufrufende Web-App freigegeben. Dadurch werden die Unannehmlichkeiten und menschlichen Fehler bei der manuellen Eingabe langwierigen Produktcodes oder anderer relevanter Informationen vermieden.

Um QR- oder Strichcodescannerfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) aufrufen. Für eine effektive Integration müssen Sie über ein gutes Verständnis des [Codeausschnitts](#code-snippet) zum Aufrufen der [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) verfügen, mit dem Sie systemeigene QR- oder Strichcodescannerfunktionen verwenden können. Die API gibt einen Fehler für einen nicht unterstützten Barcodestandard zurück.
Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE]
> Derzeit ist Microsoft Teams Unterstützung für QR- oder Strichcodescanner-Funktionen nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Aktualisieren des Manifests

Aktualisieren Sie Ihre Microsoft Teams-App-Datei[manifest.json](../../resources/schema/manifest-schema.md#devicepermissions), indem Sie die `devicePermissions`-Eigenschaft hinzufügen und `media` angeben. Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der QR- oder Strichcodescannerfunktion beginnen. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die Eingabeaufforderung **Berechtigungen anfordern** wird automatisch angezeigt, wenn eine relevante Microsoft Teams-API initiiert wird. Weitere Informationen finden Sie unter [Geräteberechtigungen anfordern](native-device-permissions.md).

## <a name="scanbarcode-api"></a>ScanBarCode-API

Die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) ruft das Scannersteuerelement auf, das es dem Benutzer ermöglicht, verschiedene Barcodetypen zu scannen, und gibt das Ergebnis als Zeichenfolge zurück.

Um die Strichcodeüberprüfung anzupassen, wird die optionale [Barcodekonfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.barcodeconfig?view=msteams-client-js-latest&preserve-view=true) als Eingabe an die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) übergeben. Sie können das Scantimeoutintervall in Sekunden mithilfe `timeOutIntervalInSec`von angeben. Der Standardwert beträgt 30 Sekunden und der Maximalwert 60 Sekunden.

Die **scanBarCode()** -API unterstützt die folgenden Barcodetypen:

| Barcodetyp | Unterstützt auf Android | Unterstützt auf iOS |
| ---------- | ---------- | ------------ |
| Codeleiste | Ja | Nein |
| Code 39 | Ja | Ja |
| Code 93 | Ja | Ja |
| Code 128 | Ja | Ja |
| EAN-13 | Ja | Ja |
| EAN-8 | Ja | Ja |
| ITF | Nein | Ja |
| QR-Code | Ja | Ja |
| RSS erweitert | Ja | Nein |
| RSS-14 | Ja | Nein |
| UPC-A | Ja | Ja |
| UPC-E | Ja | Ja |

Die folgende Abbildung zeigt die Web-App-Erfahrung der QR- oder Strichcodescanner-Funktion:

![Web-App-Erfahrung für QR- oder Strichcodescanner-Funktionen](../../assets/images/tabs/qr-barcode-scanner-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Microsoft Teams-App angemessen behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | DIE API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Die Berechtigung wird vom Benutzer verweigert.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000** | INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
| **8000** | USER_ABORT |Der Benutzer bricht den Vorgang ab.|
| **8001** | OPERATION_TIMED_OUT | Der Barcode konnte im angegebenen Zeitintervall nicht erkannt werden.|
| **9000** | OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|

## <a name="code-snippet"></a>Codeausschnitt

**Aufrufen `ScanBarCode()` API** zum Scannen von QR oder Barcode mithilfe der Kamera:

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

* [Integrieren von Medienfunktionen in Microsoft Teams](mobile-camera-image-permissions.md)
* [Integrieren von Standortfunktionen in Microsoft Teams](location-capability.md)
* [Integrieren der Personenauswahl in Microsoft Teams](people-picker-capability.md)
