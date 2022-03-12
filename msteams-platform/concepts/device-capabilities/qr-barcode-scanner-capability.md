---
title: QR- oder Barcode-Scannerfunktion integrieren
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK, um die QR- oder Strichcodescanner-Funktion zu nutzen
keywords: Kameramedien qr code qrcode barcode barcode scanner scan capabilities native device permissions
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 799306024980a9bb4e7a44b5ca654865303dec24
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452956"
---
# <a name="integrate-qr-or-barcode-scanner-capability"></a>QR- oder Barcode-Scannerfunktion integrieren

Barcode ist eine Methode zum Darstellen von Daten in einem visuellen und maschinenlesbaren Formular. Der Barcode enthält Informationen zu einem Produkt, z. B. Typ, Größe, Hersteller und Ursprungsland in Form von Balken und Leerzeichen. Der Code wird mithilfe des optischen Scanners auf Ihrer nativen Gerätekamera gelesen. Für eine umfassendere Zusammenarbeit können Sie die QR- oder Strichcodescanner-Funktion, die in der Teams-Plattform bereitgestellt wird, in Ihre Teams-App integrieren.

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die tools bereitstellt, die Ihre App für den Zugriff auf die [systemeigenen Gerätefunktionen](native-device-permissions.md) des Benutzers benötigt. Verwenden Sie die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) , um die Scannerfunktion in Ihre App zu integrieren.

## <a name="advantage-of-integrating-qr-or-barcode-scanner-capability"></a>Vorteile der Integration von QR- oder Strichcodescannern

Nachfolgend sind die Vorteile der Integration von QR- oder Strichcodescanner-Funktionen aufgeführt:

* Die Integration ermöglicht Web-App-Entwicklern auf Teams Plattform die Nutzung von QR- oder Strichcodescanfunktionen mit Teams JavaScript-Client-SDK.
* Mit diesem Feature muss der Benutzer nur einen QR- oder Barcode innerhalb eines Frames in der Mitte der Scanner-UI ausrichten, und der Code wird automatisch gescannt. Die gespeicherten Daten werden wieder mit der aufrufenden Web-App geteilt. Dadurch werden die Unannehmlichkeiten und menschlichen Fehler vermieden, wenn lange Produktcodes oder andere relevante Informationen manuell eingegeben werden.

Um DIE QR- oder Strichcodescanner-Funktion zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) aufrufen. Für eine effektive Integration müssen Sie über ein gutes Verständnis des [Codeausschnitts](#code-snippet) für den Aufruf der [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) verfügen, mit dem Sie native QR- oder Strichcodescanner-Funktionen verwenden können. Die API gibt einen Fehler für einen nicht unterstützten Strichcodestandard aus.
Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE]
> Derzeit ist Microsoft Teams Unterstützung für QR- oder Strichcodescanner-Funktionen nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Updatemanifest

Aktualisieren Sie ihre Teams App [manifest.json-Datei](../../resources/schema/manifest-schema.md#devicepermissions), indem Sie die `devicePermissions` Eigenschaft hinzufügen und angeben`media`. Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der QR- oder Strichcodescanner-Funktion beginnen. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die Eingabeaufforderung **"Berechtigungen anfordern**" wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).

## <a name="scanbarcode-api"></a>ScanBarCode-API

Die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) ruft das Scannersteuerelement auf, mit dem der Benutzer verschiedene Barcodetypen scannen kann, und gibt das Ergebnis als Zeichenfolge zurück.

Um die Strichcodeüberprüfung anzupassen, wird die optionale [Strichcodekonfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.barcodeconfig?view=msteams-client-js-latest&preserve-view=true) als Eingabe an die [scanBarCode-API](/javascript/api/@microsoft/teams-js/microsoftteams.media?view=msteams-client-js-latest&preserve-view=true#scanBarCode__error__SdkError__decodedText__string_____void__BarCodeConfig_) übergeben. Sie können das Intervall für das Scantimeout in Sekunden angeben, indem `timeOutIntervalInSec`Sie . Der Standardwert ist 30 Sekunden und der Maximalwert beträgt 60 Sekunden.

Die **scanBarCode()** -API unterstützt die folgenden Strichcodetypen:

| Strichcodetyp | Unterstützt unter Android | Unterstützt unter iOS |
| ---------- | ---------- | ------------ |
| Codeleiste | Ja | Nein |
| Code 39 | Ja | Ja |
| Code 93 | Ja | Ja |
| Code 128 | Ja | Ja |
| EAN-13 | Ja | Ja |
| EAN-8 | Ja | Ja |
| ITF | Nein | Ja |
| QR-Code | Ja | Ja |
| RSS Expanded | Ja | Nein |
| RSS-14 | Ja | Nein |
| UPC-A | Ja | Ja |
| UPC-E | Ja | Ja |

Die folgende Abbildung zeigt die Web-App-Erfahrung der QR- oder Strichcodescanner-Funktion:

![Web-App-Erfahrung für qr- oder Strichcodescanner-Funktion](../../assets/images/tabs/qr-barcode-scanner-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Beim Ausführen des erforderlichen Vorgangs ist ein interner Fehler aufgetreten.|
| **1000** | PERMISSION_DENIED |Der Benutzer verweigert die Berechtigung.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000** | INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
| **8000** | USER_ABORT |Der Benutzer abgebrochen den Vorgang.|
| **8001** | OPERATION_TIMED_OUT | Der Barcode konnte im angegebenen Zeitintervall nicht erkannt werden.|
| **9000** | OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|

## <a name="code-snippet"></a>Codeausschnitt

**Aufrufen `ScanBarCode()` API** zum Scannen von QR oder Strichcode mithilfe der Kamera:

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
* [Integrieren der Personenauswahl in Teams](people-picker-capability.md)
