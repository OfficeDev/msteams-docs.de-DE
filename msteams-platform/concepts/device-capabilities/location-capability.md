---
title: Integration von Standortfunktionen
author: Rajeshwari-v
description: Erfahren Sie, wie Sie Teams JavaScript-Client-SDK verwenden, um Standortfunktionen mit Codeausschnitten und Beispielen zu nutzen.
keywords: Systemeigene Geräteberechtigungen für Standortzuordnungsfunktionen
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: a375d8f7c2692c9da8e220474c2c0ece97b623c2
ms.sourcegitcommit: a36760750ff4f510c374a4c956be57f7c1b4a0db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2022
ms.locfileid: "63675013"
---
# <a name="integrate-location-capabilities"></a>Integration von Standortfunktionen

Sie können die Standortfunktionen des nativen Geräts in Ihre Teams-App integrieren.  

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die tools bereitstellt, die Ihre App für den Zugriff auf die [systemeigenen Gerätefunktionen](native-device-permissions.md) des Benutzers benötigt. Verwenden Sie die Standort-APIs, z. B. [getLocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) und [showLocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) , um die Funktionen in Ihre App zu integrieren.

## <a name="advantages-of-integrating-location-capabilities"></a>Vorteile der Integration von Standortfunktionen

Der Hauptvorteil der Integration von Standortfunktionen in Ihre Teams-Apps besteht darin, dass Web-App-Entwickler auf Teams Plattform Standortfunktionen mit Microsoft Teams JavaScript-Client-SDK nutzen können.

Die folgenden Beispiele zeigen, wie die Integration von Standortfunktionen in verschiedenen Szenarien verwendet wird:

* In einer Fabrik kann der Vorgesetzte die Anwesenheit von Mitarbeitern nachverfolgen, indem er sie auffordert, sich in der Nähe der Fabrik zu befinden und sie über die angegebene App freizugeben. Die Standortdaten werden auch erfasst und zusammen mit dem Bild gesendet.
* Die Standortfunktionen ermöglichen es den Wartungsmitarbeitern eines Dienstanbieters, authentifizierte Gesundheitsdaten von Mobilfunkmasten mit der Geschäftsleitung zu teilen. Die Geschäftsleitung kann jeden Konflikt zwischen erfassten Standortinformationen und den von Wartungsmitarbeitern übermittelten Daten vergleichen.

Um Standortfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die APIs aufrufen. Für eine effektive Integration müssen Sie über ein gutes Verständnis von [Codeausschnitten](#code-snippets) für den Aufruf der Standort-APIs verfügen.
Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE]
> Derzeit ist Microsoft Teams Unterstützung für Standortfunktionen nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Aktualisieren des Manifests

Aktualisieren Sie ihre Teams App [manifest.json-Datei](../../resources/schema/manifest-schema.md#devicepermissions), indem Sie die `devicePermissions` Eigenschaft hinzufügen und angeben`geolocation`. Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der Standortfunktionen beginnen. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
> * Die Eingabeaufforderung **"Berechtigungen anfordern**" wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).
> * Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter ["Berechtigungen für Browsergeräte"](browser-device-permissions.md).

## <a name="location-apis"></a>Standort-APIs

Sie müssen die folgenden APIs verwenden, um die Standortfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
|[Getlocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) | Gibt den aktuellen Gerätestandort des Benutzers an oder öffnet die systemeigene Standortauswahl und gibt den vom Benutzer ausgewählten Standort zurück. |
|[showLocation](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#showLocation_Location___error__SdkError__status__boolean_____void_&preserve-view=true) | Zeigt die Position auf der Karte an. |

> [!NOTE]
> Die `getLocation()` API enthält die folgenden [Eingabekonfigurationen](/javascript/api/@microsoft/teams-js/locationprops?view=msteams-client-js-latest&preserve-view=true) und `allowChooseLocation` `showMap`. <br/> Wenn der Wert "`allowChooseLocation`*true"* ist, können die Benutzer einen beliebigen Speicherort auswählen.<br/>  Wenn der Wert *"false*" ist, können die Benutzer ihren aktuellen Standort nicht ändern.<br/> Wenn der Wert "`showMap`*false*" lautet, wird die aktuelle Position abgerufen, ohne die Karte anzuzeigen. `showMap` wird ignoriert, wenn `allowChooseLocation` sie auf *"true*" festgelegt ist.

Die folgende Abbildung zeigt die Web-App-Erfahrung mit Standortfunktionen:

![Web-App-Erfahrung für Standortfunktionen](../../assets/images/tabs/location-capability.png)

### <a name="code-snippets"></a>Codeausschnitte

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

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Beim Ausführen des erforderlichen Vorgangs ist ein interner Fehler aufgetreten.|
| **1000** | PERMISSION_DENIED |Der Benutzer hat standortbezogene Berechtigungen für die Teams-App oder die Web-App verweigert.|
| **4000** | INVALID_ARGUMENTS | Die API wird mit falschen oder nicht ausreichenden obligatorischen Argumenten aufgerufen.|
| **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000** | OLD_PLATFORM | Der Benutzer befindet sich auf einem alten Plattformbuild, in dem die Implementierung der API nicht vorhanden ist. Das Upgrade des Builds sollte das Problem beheben.|

### <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Aktueller App-Eincheckspeicherort | Benutzer können den aktuellen Speicherort einchecken und alle vorherigen Standort-Eincheckungen anzeigen.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-checkin-location/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-checkin-location/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
* [Integrieren von QR-Code oder Strichcodescanner-Funktion in Teams](qr-barcode-scanner-capability.md)
* [Integrieren der Personenauswahl in Teams](people-picker-capability.md)
