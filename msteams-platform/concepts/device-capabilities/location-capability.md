---
title: Integration von Standortfunktionen
author: Rajeshwari-v
description: Erfahren Sie, wie Sie das Teams JavaScript-Client-SDK verwenden, um Standortfunktionen mithilfe von Codeausschnitten und Beispielen zu nutzen.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: 00fdfe470dcc5028afb233f9fbe0c6a6f7ff1b2c
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189865"
---
# <a name="integrate-location-capabilities"></a>Integration von Standortfunktionen

Sie können die Standortfunktionen nativer Geräte in Ihre Teams-App integrieren.  

Sie können [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die Tools bereitstellt, die Ihre App für den Zugriff auf die [nativen Gerätefunktionen](native-device-permissions.md) des Benutzers benötigt. Verwenden Sie die Standort-APIs, z. B. [getLocation](/javascript/api/@microsoft/teams-js/location.locationprops) und [showLocation](/javascript/api/@microsoft/teams-js/location.locationprops?), um die Funktionen in Ihre App zu integrieren.

## <a name="advantages-of-integrating-location-capabilities"></a>Vorteile der Integration von Standortfunktionen

Der Hauptvorteil der Integration von Standortfunktionen in Ihre Teams-Apps besteht darin, dass Web-App-Entwickler auf der Teams-Plattform Standortfunktionen mit Microsoft Teams JavaScript-Client-SDK nutzen können.

Die folgenden Beispiele zeigen, wie die Integration von Standortfunktionen in verschiedenen Szenarien verwendet wird:

* In einer Fabrik kann der Vorgesetzte die Anwesenheit von Mitarbeitern nachverfolgen, indem er sie auffordert, ein Selfie in der Nähe der Fabrik zu nehmen und es über die angegebene App freizugeben. Die Standortdaten werden auch erfasst und zusammen mit dem Bild gesendet.
* Die Standortfunktionen ermöglichen es den Wartungsmitarbeitern eines Dienstanbieters, authentische Integritätsdaten von Mobilfunkmasten mit der Verwaltung zu teilen. Die Verwaltung kann jede Übereinstimmung zwischen erfassten Standortinformationen und den von Wartungsmitarbeitern übermittelten Daten vergleichen.

Um Standortfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die APIs aufrufen. Für eine effektive Integration benötigen Sie ein gutes Verständnis von [Codeausschnitten](#code-snippets) zum Aufrufen der Standort-APIs.
Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE]
> Derzeit ist Microsoft Teams-Support für Standortfunktionen nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Aktualisieren des Manifests

Aktualisieren Sie Ihre Teams-App-Datei[manifest.json](../../resources/schema/manifest-schema.md#devicepermissions), indem Sie die `devicePermissions`-Eigenschaft hinzufügen und `geolocation` angeben. Dadurch kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der Standortfunktionen beginnen. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "geolocation",
],
```

> [!NOTE]
>
> * Die Eingabeaufforderung **Berechtigungen anfordern** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter [Geräteberechtigungen anfordern](native-device-permissions.md).
> * Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter [Browsergeräteberechtigungen](browser-device-permissions.md).

## <a name="location-apis"></a>Standort-APIs

Sie müssen die folgenden APIs verwenden, um die Standortfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
|[getLocation](/javascript/api/@microsoft/teams-js/location.locationprops) | Gibt den aktuellen Gerätespeicherort des Benutzers an oder öffnet die native Standortauswahl und gibt den vom Benutzer ausgewählten Speicherort zurück. |
|[showLocation](/javascript/api/@microsoft/teams-js/location.locationprops?) | Zeigt den Standort auf der Karte an. |

> [!NOTE]
> Die `getLocation()`-API enthält die folgenden [Eingabekonfigurationen](/javascript/api/@microsoft/teams-js/microsoftteams.location.locationprops), `allowChooseLocation` und `showMap`.<br/> Wenn der Wert von "`allowChooseLocation`" *true* lautet, können die Benutzer einen beliebigen Standort ihrer Wahl auswählen.<br/>  Wenn der Wert *false* lautet, können die Benutzer ihren aktuellen Speicherort nicht ändern.<br/> Wenn der Wert von "`showMap`" *false* lautet, wird der aktuelle Speicherort abgerufen, ohne die Karte anzuzeigen. "`showMap`" wird ignoriert, wenn "`allowChooseLocation`" auf *true* festgelegt ist.

Die folgende Abbildung zeigt die Web-App-Erfahrung der Standortfunktionen:

![Web-App-Erfahrung für Standortfunktionen](../../assets/images/tabs/location-capability.png)

### <a name="code-snippets"></a>Codeausschnitte

**Aufrufen der `getLocation`-API zum Abrufen des Speicherorts:**

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

**Aufrufen der `showLocation`-API zum Anzeigen des Speicherorts:**

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

Sie müssen sicherstellen, dass diese Fehler in Ihrer Microsoft Teams-App angemessen behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Der Benutzer hat die Standortberechtigungen für die Teams-App oder die Web-App verweigert.|
| **4000** | INVALID_ARGUMENTS | Die API wird mit falschen oder nicht ausreichenden obligatorischen Argumenten aufgerufen.|
| **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000** | OLD_PLATFORM | Der Benutzer befindet sich in einem alten Plattformbuild, in dem die Implementierung der API nicht vorhanden ist. Durch ein Upgrade des Builds sollte das Problem behoben werden.|

### <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| App-Check-In des aktuellen Standorts | Benutzer können den aktuellen Standort einchecken und alle vorherigen Standort-Check-Ins anzeigen.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-checkin-location/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-checkin-location/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Integrieren von Medienfunktionen](media-capabilities.md)
* [Integrieren von QR-Code- oder Strichcodescanner-Funktionen in Microsoft Teams](qr-barcode-scanner-capability.md)
* [Integrieren der Personenauswahl in Teams](people-picker-capability.md)
