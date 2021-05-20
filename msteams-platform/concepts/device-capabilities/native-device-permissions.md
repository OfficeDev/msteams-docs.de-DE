---
title: Geräteberechtigungen für Ihre Microsoft Teams-App anfordern
keywords: Berechtigungen für Teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Funktionen anzufordern, für die normalerweise die Zustimmung des Benutzers erforderlich ist
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 34f84285dc883cc474cf1720c42b1699f76c6653
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566180"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Geräteberechtigungen für Ihre Microsoft Teams-App anfordern

Sie können Ihre Teams-App mit nativen Gerätefunktionen wie Kamera, Mikrofon und Standort anreichern. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die Berechtigungen für native Geräte zugreifen können.

> [!NOTE]
> * Informationen zum Integrieren von Medienfunktionen in Ihre Microsoft Teams mobile App finden Sie unter Integrieren von [Medienfunktionen](mobile-camera-image-permissions.md).
> * Informationen zur Integration der QR- oder Barcode-Scanner-Fähigkeit in Ihre Microsoft Teams mobile App finden Sie unter Integrieren der [QR- oder Barcode-Scanner-Funktion in Teams](qr-barcode-scanner-capability.md).
> * Informationen zum Integrieren von Standortfunktionen in Ihre Microsoft Teams mobile App finden Sie unter Integrieren von [Standortfunktionen](location-capability.md).

## <a name="native-device-permissions"></a>Native Geräteberechtigungen

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können. Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen, ähnlich. Der Benutzer muss die Berechtigungsseite in Teams Einstellungen aufrufen, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie umfangreichere Erlebnisse auf der Teams Plattform erstellen, z. B.:
* Erfassen und Anzeigen von Bildern.
* Scannen Sie QR oder Barcode.
* Nehmen Sie kurze Videos auf und teilen Sie sie.
* Nehmen Sie Audio-Memos auf und speichern Sie sie für die spätere Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzuzeigen.

## <a name="access-device-permissions"></a>Zugriff auf Geräteberechtigungen

Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) stellt die Tools bereit, die Für Ihre Teams mobile App erforderlich sind, um auf die [Geräteberechtigungen](#manage-permissions) des Benutzers zuzugreifen und eine umfangreichere Benutzererfahrung zu erstellen.

Obwohl der Zugriff auf diese Funktionen in modernen Webbrowsern Standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf dem Teams Desktopclient ausgeführt wird.

> [!NOTE] 
> Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Barcode-Scanner-Funktionen nur für mobile Clients verfügbar.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in Teams Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps **zulassen** oder **verweigern** auswählt.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Ihre Teams-App.
1. Wählen Sie Ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen Sie **Einstellungen**  >  **Berechtigungen** aus dem Dropdown-Menü aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   ![Bildschirm für Geräteberechtigungen desktop-einstellungen](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu **Einstellungen**  >  **App-Berechtigungen**.
1. Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

    ![Bildschirm für Geräteberechtigungen für mobile Einstellungen](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Angeben von Berechtigungen

Aktualisieren Sie die Ihrer App, `manifest.json` indem Sie die fünf Eigenschaften hinzufügen und `devicePermissions` angeben, die Sie in Ihrer Anwendung verwenden:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Jede Eigenschaft ermöglicht es Ihnen, den Benutzer aufzufordern, um seine Zustimmung zu bitten:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| media         | Berechtigung zur Verwendung der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf die Mediengalerie. |
| Geolocation   | Berechtigung zum Zurückgeben des Speicherorts des Benutzers.      |
| Benachrichtigungen | Berechtigung zum Senden der Benutzerbenachrichtigungen.      |
| Midi          | Berechtigung zum Senden und Empfangen von Musikinstrumenten Digital Interface (MIDI)-Informationen von einem digitalen Musikinstrument.   |
| openExtern  | Berechtigung zum Öffnen von Links in externen Anwendungen.  |

## <a name="check-permissions-from-your-app"></a>Überprüfen der Berechtigungen aus Ihrer App

Überprüfen Sie nach dem Hinzufügen `devicePermissions` zu Ihrem App-Manifest die Berechtigungen mithilfe der **HTML5-Berechtigungs-API,** ohne eine Eingabeaufforderung zu verursachen:

``` Javascript
// Different query options:
navigator.permissions.query({ name: 'camera' });
navigator.permissions.query({ name: 'microphone' });
navigator.permissions.query({ name: 'geolocation' });
navigator.permissions.query({ name: 'notifications' });
navigator.permissions.query({ name: 'midi', sysex: true });

// Example:
navigator.permissions.query({name:'geolocation'}).then(function(result) {
  if (result.state == 'granted') {
    // Access granted
  } else if (result.state == 'prompt') {
    // Access has not been granted
  }
});
```

## <a name="use-teams-apis-to-get-device-permissions"></a>Verwenden Teams-APIs zum Abrufen von Geräteberechtigungen

Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für die Zustimmung zum Zugriff auf Geräteberechtigungen anzuzeigen.

> [!IMPORTANT]
> * Unterstützung für `camera` , und wird über `gallery` `microphone` [**selectMedia API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)aktiviert. Verwenden Sie [**die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung `location` für ist über die [**getLocation API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)aktiviert. Sie müssen dies für den Standort verwenden, da die `getLocation API` HTML5-Geolocation-API derzeit auf Teams Desktopclient nicht vollständig unterstützt wird.

Zum Beispiel:
 * Um den Benutzer zum Zugriff auf seinen Standort aufzufordern, müssen Sie `getCurrentPosition()` Folgendes aufrufen:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Um den Benutzer zum Zugriff auf seine Kamera auf dem Desktop oder im Web aufzufordern, müssen Sie `getUserMedia()` Folgendes aufrufen:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Um das Bild auf Mobilgeräten zu erfassen, fragt Teams Mobile beim Anruf um `captureImage()` Erlaubnis:

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * Benachrichtigungen werden den Benutzer beim Aufruf `requestPermission()` aufgefordert:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Um die Kamera zu verwenden oder auf die Fotogalerie zuzugreifen, fragt Teams mobile beim Anruf `selectMedia()` um:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Um das Mikrofon zu verwenden, fragt Teams mobile beim Anruf `selectMedia()` um:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Um den Benutzer aufzufordern, den Standort auf der Kartenschnittstelle freizugeben, fragt Teams mobile beim Aufruf die `getLocation()` Berechtigung:

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Registerkarten Desktop-Geräteberechtigung Eingabeaufforderung](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

   ![Registerkarten für Berechtigungen für mobile Geräte](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten über Anmeldesitzungen hinweg

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich z. B. auf einem anderen Computer bei einer anderen Instanz Teams anmelden, sind Ihre Geräteberechtigungen aus den vorherigen Sitzungen nicht verfügbar. Daher müssen Sie die Geräteberechtigungen für die neue Sitzung erneut zustimmen. Wenn Sie sich bei Teams abmelden oder Mandanten in Teams wechseln, werden Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht.  

> [!NOTE]
> Wenn Sie den Berechtigungen für ein natives Gerät zustimmen, ist sie nur für Ihre _aktuelle_ Anmeldesitzung gültig.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrieren Sie QR- oder Barcode-Scanner-Funktionen in Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integrieren von Standortfunktionen in Teams](location-capability.md)
