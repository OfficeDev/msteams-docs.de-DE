---
title: Integrieren von Standortfunktionen
description: Verwenden des Teams JavaScript-Client-SDK zum Nutzen von Standortfunktionen
keywords: Standortzuordnungsfunktionen Systemeigene Geräteberechtigungen
ms.author: lajanuar
ms.openlocfilehash: fccf39c37c785be716bfff26907f9184c0d9beec
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449619"
---
# <a name="integrate-location-capabilities"></a>Integrieren von Standortfunktionen 

In diesem Dokument erfahren Sie, wie Sie die Standortfunktionen des systemeigenen Geräts in Ihre Teams-App integrieren.  

Sie können [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die tools zur Verfügung stellt, die Für Ihre App erforderlich sind, um auf die systemeigenen Gerätefunktionen des Benutzers zu [zugreifen.](native-device-permissions.md) Verwenden Sie die Standort-APIs, z. B. [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_) und [showLocation,](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_) um die Funktionen in Ihre App zu integrieren. 

## <a name="advantages-of-integrating-location-capabilities"></a>Vorteile der Integration von Standortfunktionen

Der Hauptvorteil der Integration von Standortfunktionen in Ihre Teams-Apps besteht in der Möglichkeit, dass Web-App-Entwickler auf der Microsoft Teams-Plattform Standortfunktionen mit Dem JavaScript-Client-SDK von Microsoft Teams nutzen können. 

In den folgenden Beispielen wird gezeigt, wie die Integration von Standortfunktionen in verschiedenen Szenarien verwendet wird:
* In einer Fabrik kann der Vorgesetzte die Anwesenheit von Mitarbeitern nachverfolgen, indem er sie bittet, ein Selfie in der Nähe der Fabrik zu machen und es über die angegebene App zu teilen. Die Standortdaten werden auch zusammen mit dem Bild erfasst und gesendet.
* Die Standortfunktionen ermöglichen es den Wartungsmitarbeitern eines Dienstanbieters, die echten Integritätsdaten von Mobilfunkmasten mit der Verwaltung zu teilen. Die Verwaltung kann jeglichen Konflikt zwischen erfassten Standortinformationen und den vom Wartungspersonal übermittelten Daten vergleichen.

Zum Integrieren von Standortfunktionen müssen Sie die App-Manifestdatei aktualisieren und die APIs aufrufen. Für eine effektive Integration müssen Sie [](#code-snippets) über ein gutes Verständnis von Codeausschnitten zum Aufrufen der Speicherort-APIs verfügen. Es ist wichtig, sich mit den API-Antwortfehlern vertraut zu [machen,](#error-handling) um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE] 
> Derzeit ist Die Unterstützung von Standortfunktionen von Microsoft Teams nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Updatemanifest

Aktualisieren Sie Ihre [ Teamsmanifest.js-App-Datei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die `devicePermissions` -Eigenschaft hinzufügen und `geolocation` angeben. Sie ermöglicht Es Ihrer App, die erforderlichen Berechtigungen von Benutzern zu fordern, bevor sie mit der Verwendung der Standortfunktionen beginnen.

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).

## <a name="location-apis"></a>Speicherort-APIs

Sie müssen die folgenden APIs verwenden, um die Standortfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
|[getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_) | Gibt den aktuellen Gerätespeicherort des Benutzers an oder öffnet die systemeigene Standortauswahl und gibt den vom Benutzer ausgewählten Speicherort zurück. |
|[showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation) | Zeigt den Standort auf der Karte an |

> [!NOTE]

> Die `getLocation()` API enthält die folgenden [Eingabekonfigurationen](https://docs.microsoft.com/en-us/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest)und `allowChooseLocation` `showMap` . <br/> Wenn der Wert von true ist, können die Benutzer `allowChooseLocation` einen beliebigen Speicherort ihrer Wahl auswählen. <br/>  Wenn der Wert *false ist,* können die Benutzer ihren aktuellen Speicherort nicht ändern.<br/> Wenn der Wert `showMap` von *false ist,* wird der aktuelle Speicherort abgerufen, ohne die Karte anzuzeigen. `showMap`wird ignoriert, `allowChooseLocation` wenn auf true festgelegt *ist.* 

**Web-App-Erfahrung für Standortfunktionen** 
 ![ Web-App-Erfahrung für Standortfunktionen](../../assets/images/tabs/location-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App angemessen umgangen werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden: 

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | DIE API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Benutzer verweigerte Standortberechtigungen für die Teams-App oder die Web-App.|
| **4000** | INVALID_ARGUMENTS | DIE API wird mit falschen oder unzureichenden obligatorischen Argumenten aufgerufen.|
| **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000** | OLD_PLATFORM | Der Benutzer befindet sich im alten Plattform build, in dem die Implementierung der API nicht vorhanden ist. Beim Upgrade des Build sollte das Problem behoben werden.|

## <a name="code-snippets"></a>Codeausschnitte

**Aufrufen `getLocation` der API zum Abrufen des Speicherorts:**

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

**Aufrufen `showLocation` der API zum Anzeigen des Speicherorts:**

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

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrieren von QR- oder Barcodescannerfunktionen in Teams](qr-barcode-scanner-capability.md)