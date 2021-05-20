---
title: Integration von Standortfunktionen
author: Rajeshwari-v
description: Verwenden Teams JavaScript Client SDK zur Nutzung von Standortfunktionen
keywords: Standortkartenfunktionen systemeigene Geräteberechtigungen
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: b85f19e74d0a8121dd290fc395c1018178437b3a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566187"
---
# <a name="integrate-location-capabilities"></a>Integration von Standortfunktionen 

In diesem Dokument erfahren Sie, wie Sie die Standortfunktionen des nativen Geräts in Ihre Teams-App integrieren können.  

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die Tools bereitstellt, die Für Ihre App erforderlich sind, um auf die [systemeigenen Gerätefunktionen](native-device-permissions.md)des Benutzers zuzugreifen. Verwenden Sie die Standort-APIs, z. B. [getLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) und [showLocation,](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) um die Funktionen in Ihre App zu integrieren. 

## <a name="advantages-of-integrating-location-capabilities"></a>Vorteile der Integration von Standortfunktionen

Der Hauptvorteil der Integration von Standortfunktionen in Ihre Teams-Apps besteht darin, dass Web-App-Entwickler auf Teams Plattform die Standortfunktionalität mit Microsoft Teams JavaScript-Client-SDK nutzen können. 

Die folgenden Beispiele zeigen, wie die Integration von Standortfunktionen in verschiedenen Szenarien verwendet wird:
* In einer Fabrik kann der Vorgesetzte die Anwesenheit von Arbeitern verfolgen, indem er sie bittet, ein Selfie in der Nähe der Fabrik zu machen und es über die angegebene App zu teilen. Die Standortdaten werden ebenfalls erfasst und zusammen mit dem Bild gesendet.
* Die Standortfunktionen ermöglichen es dem Wartungspersonal eines Dienstleisters, authentische Gesundheitsdaten von Mobilfunkmasten mit dem Management zu teilen. Das Management kann jede Diskrepanz zwischen erfassten Standortinformationen und den von Wartungspersonal übermittelten Daten vergleichen.

Um Standortfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die APIs aufrufen. Für eine effektive Integration müssen Sie über ein gutes Verständnis von [Codeausschnitten](#code-snippets) zum Aufrufen der Standort-APIs verfügen. Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE] 
> Derzeit ist Microsoft Teams Unterstützung für Standortfunktionen nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Update-Manifest

Aktualisieren Sie Ihre Teams-App [manifest.jsin](../../resources/schema/manifest-schema.md#devicepermissions) der Datei, indem Sie die Eigenschaft hinzufügen `devicePermissions` und `geolocation` angeben. Es ermöglicht Ihrer App, die erforderlichen Berechtigungen von Benutzern anzufordern, bevor sie mit der Verwendung der Standortfunktionen beginnen.

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> Die Eingabeaufforderung **"Anforderungsberechtigungen"** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter Anfordern von [Geräteberechtigungen](native-device-permissions.md).

## <a name="location-apis"></a>Standort-APIs

Sie müssen den folgenden Satz von APIs verwenden, um die Standortfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
|[Getlocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) | Gibt den aktuellen Gerätestandort des Benutzers an oder öffnet die systemeigene Standortauswahl und gibt den vom Benutzer ausgewählten Speicherort zurück. |
|[showLocation](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#showLocation&preserve-view=true) | Zeigt den Standort auf der Karte an. |

> [!NOTE]

> Die `getLocation()` API enthält folgende [Eingabekonfigurationen](/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true) `allowChooseLocation` und `showMap` . <br/> Wenn der Wert von `allowChooseLocation` *true* ist, können die Benutzer einen beliebigen Speicherort ihrer Wahl auswählen.<br/>  Wenn der Wert *false* ist, können die Benutzer ihren aktuellen Speicherort nicht ändern.<br/> Wenn der Wert von `showMap` *false* ist, wird die aktuelle Position abgerufen, ohne die Karte anzuzeigen. `showMap` wird ignoriert, wenn `allowChooseLocation` auf *true* festgelegt ist.

**Web-App-Erfahrung für Standortfunktionen** 
 ![ Web-App-Erfahrung für Standortfunktionen](../../assets/images/tabs/location-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden: 

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Beim Ausführen des erforderlichen Vorgangs tritt ein interner Fehler auf.|
| **1000** | PERMISSION_DENIED |Dem Benutzer wurden standortbezogene Berechtigungen für die Teams App oder die Web-App verweigert.|
| **4000** | INVALID_ARGUMENTS | API wird mit falschen oder unzureichenden obligatorischen Argumenten aufgerufen.|
| **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000** | OLD_PLATFORM | Der Benutzer befindet sich auf einem alten Plattformbuild, bei dem die Implementierung der API nicht vorhanden ist. Durch das Aktualisieren des Builds sollte das Problem behoben werden.|

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

* [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
* [Integrieren Sie QR-Code- oder Barcode-Scanner-Funktionen in Teams](qr-barcode-scanner-capability.md)
