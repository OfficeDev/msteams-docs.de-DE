---
title: Anfordern von Geräteberechtigungen für Microsoft Teams App
keywords: Berechtigungen für teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzuholen, für die in der Regel die Zustimmung des Benutzers erforderlich ist
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 452840c5809da32a79c231f85cd1de9f8746367a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019853"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Anfordern von Geräteberechtigungen für Microsoft Teams App

Sie können Ihre Teams mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort bereichern. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.

> [!NOTE]
> * Informationen zur Integration von Medienfunktionen in Microsoft Teams Mobile App finden Sie [unter Integrieren von Medienfunktionen](mobile-camera-image-permissions.md).
> * Informationen zur Integration von QR- oder Barcodescannerfunktionen in Microsoft Teams Mobile App finden Sie unter Integrieren von QR- oder [Barcodescannerfunktionen in Teams](qr-barcode-scanner-capability.md)
> * Informationen zur Integration von Standortfunktionen in Microsoft Teams Mobile App finden Sie [unter Integrieren von Standortfunktionen](location-capability.md).

## <a name="native-device-permissions"></a>Berechtigungen für systemeigene Geräte

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zu zugreifen. Die Geräteberechtigungen funktionieren ähnlich für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen. Der Benutzer muss zur Seite Berechtigungen in den Teams wechseln, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie auf der plattform Teams, z. B.:
* Erfassen und Anzeigen von Bildern.
* Scannen Sie QR oder Barcode.
* Aufzeichnen und Freigeben von kurzen Videos.
* Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzeigen zu können.

## <a name="access-device-permissions"></a>Zugreifen auf Geräteberechtigungen

Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) bietet die Tools, die für Ihre Teams [](#manage-permissions) mobile App erforderlich sind, um auf die Geräteberechtigungen des Benutzers zu zugreifen und eine reichhaltigere Umgebung zu erstellen.

Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen bitten, während Ihre App auf dem Teams ausgeführt wird.

> [!NOTE] 
> Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Strichcodescanner nur für mobile Clients verfügbar.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in Teams  verwalten,  indem er Berechtigungen für bestimmte Apps zulassen oder verweigern aus.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie ihre Teams App.
1. Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen **Einstellungen**  >  **Berechtigungen** im Dropdownmenü aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

1. Öffnen Teams.
1. Wechseln Sie **zu Einstellungen**  >  **App Permissions**.
1. Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Angeben von Berechtigungen

Aktualisieren Sie Ihre App, indem Sie hinzufügen und angeben, welche der `manifest.json` `devicePermissions` fünf Eigenschaften, die Sie in Ihrer Anwendung verwenden:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Mit jeder Eigenschaft können Sie den Benutzer bitten, um seine Zustimmung zu bitten:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| media         | Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf den Medienkatalog. |
| geolocation   | Berechtigung zum Zurückgeben des Speicherorts des Benutzers.      |
| Benachrichtigungen | Berechtigung zum Senden von Benutzerbenachrichtigungen.      |
| midi          | Berechtigung zum Senden und Empfangen von Midi-Informationen (Musical Instrument Digital Interface) von einem digitalen Musikinstrument.   |
| openExternal  | Berechtigung zum Öffnen von Links in externen Anwendungen.  |

## <a name="check-permissions-from-your-app"></a>Überprüfen von Berechtigungen aus Ihrer App

Überprüfen Sie nach dem Hinzufügen zu Ihrem App-Manifest Berechtigungen mithilfe der `devicePermissions` **HTML5-Berechtigungs-API,** ohne eine Eingabeaufforderung zu verursachen:

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

## <a name="use-teams-apis-to-get-device-permissions"></a>Verwenden Teams-APIs zum Erhalten von Geräteberechtigungen

Verwenden Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen einzuholen.

> [!IMPORTANT]
> * Unterstützung für `camera` , und wird über die `gallery` `microphone` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) Verwenden [**Sie die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) Sie müssen dies für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf dem `getLocation API` Teams unterstützt wird.

Zum Beispiel:
 * Um den Benutzer zum Zugriff auf seinen Standort aufforderen zu können, müssen Sie `getCurrentPosition()` anrufen:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Um den Benutzer zum Zugriff auf seine Kamera auf dem Desktop oder Web aufforderen zu können, müssen Sie `getUserMedia()` anrufen:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Um das Bild auf mobilen Geräten zu erfassen, Teams Mobile beim Anruf um Erlaubnis `captureImage()` bitten:

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission()` anrufen:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Um die Kamera oder den Fotokatalog zu verwenden, Teams Mobile die Berechtigung, wenn Sie `selectMedia()` anrufen:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Um das Mikrofon zu verwenden, Teams Mobile beim Anruf die Berechtigung `selectMedia()` ein:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Um den Benutzer zum Freigeben des Speicherorts auf der Kartenschnittstelle auffordern, fordert Teams Mobile beim Anruf die Berechtigung `getLocation()` an:

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

   ![Eingabeaufforderung für Mobile Geräteberechtigungen für Registerkarten](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten in Anmeldesitzungen

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich bei einer anderen Instanz von Teams, z. B. auf einem anderen Computer, anmelden, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar. Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen. Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, Teams sie sich abmelden oder mandanten in Teams wechseln.  

> [!NOTE]
> Wenn Sie den berechtigungen für systemeigene Geräte zustimmen, ist sie nur für Ihre _aktuelle Anmeldesitzung_ gültig.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrieren von QR- oder Barcodescannerfunktionen in Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integrieren von Standortfunktionen in Teams](location-capability.md)
