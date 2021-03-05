---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzuholen, für die in der Regel die Zustimmung des Benutzers erforderlich ist
ms.topic: how-to
ms.openlocfilehash: e7c5f7ff477bc193924cdf11700c77ae620cd1c0
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449436"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App

Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort bereichern. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.

> [!NOTE]
> * Informationen zur Integration von Medienfunktionen in Ihre mobile Microsoft Teams-App finden Sie [unter Integrieren von Medienfunktionen](mobile-camera-image-permissions.md).
> * Informationen zur Integration von QR- oder Strichcodescannerfunktionen in Ihre mobile Microsoft Teams-App finden Sie unter Integrieren der QR- oder [Barcodescannerfunktion in Teams.](qr-barcode-scanner-capability.md)
> * Informationen zur Integration von Standortfunktionen in Ihre mobile Microsoft Teams-App finden Sie [unter Integrieren von Standortfunktionen](location-capability.md).

## <a name="native-device-permissions"></a>Berechtigungen für systemeigene Geräte

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zu zugreifen. Die Geräteberechtigungen funktionieren ähnlich für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen. Der Benutzer muss zur Seite Berechtigungen in den Teams-Einstellungen wechseln, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie auf der Teams-Plattform vielfältigere Erfahrungen erstellen, z. B.:
* Erfassen und Anzeigen von Bildern.
* Scannen Sie QR oder Barcode.
* Aufzeichnen und Freigeben von kurzen Videos.
* Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzeigen zu können.

## <a name="access-device-permissions"></a>Zugreifen auf Geräteberechtigungen

Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) bietet die Tools, die [](#manage-permissions) Für Ihre mobile Teams-App erforderlich sind, um auf die Geräteberechtigungen des Benutzers zu zugreifen und eine reichhaltigere Umgebung zu schaffen.

Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie durch Aktualisieren Ihres App-Manifests verwenden. Dieses Update ermöglicht es Ihnen, Berechtigungen zu fordern, während Ihre App auf dem Teams-Desktopclient ausgeführt wird.

> [!NOTE] 
> Derzeit ist Microsoft Teams nur für mobile Clients verfügbar, die Medienfunktionen und QR-Strichcodescanner unterstützen.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in  den Teams-Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps zulassen **oder** verweigern aus.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Ihre Teams-App.
1. Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen **Sie**  >  **im** Dropdownmenü Einstellungen Berechtigungen aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobilgeräte](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu **Einstellungen**  >  **App-Berechtigungen**.
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

## <a name="use-teams-apis-to-get-device-permissions"></a>Verwenden von Teams-APIs zum Erhalten von Geräteberechtigungen

Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen einzuholen.

> [!IMPORTANT]
> * Unterstützung für `camera` , und wird über die `gallery` `microphone` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) Verwenden [**Sie die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf dem Teams-Desktopclient unterstützt wird.

Beispiel:
 * Um den Benutzer zum Zugriff auf seinen Standort aufforderen zu können, müssen Sie `getCurrentPosition()` anrufen:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Um den Benutzer zum Zugriff auf seine Kamera auf dem Desktop oder Web aufforderen zu können, müssen Sie `getUserMedia()` anrufen:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Um das Bild auf mobilen Geräten zu erfassen, bittet Teams mobile um Erlaubnis, wenn Sie `captureImage()` anrufen:

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission()` anrufen:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Zum Verwenden der Kamera oder des Zugriffsfotokatalogs fragt Teams mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Um das Mikrofon zu verwenden, fordert Teams mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Um den Benutzer zum Freigeben des Speicherorts auf der Kartenschnittstelle auffordern zu können, fordert Teams mobile die Berechtigung auf, wenn Sie `getLocation()` anrufen:

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobilgeräte](#tab/mobile)

   ![Eingabeaufforderung für Mobile Geräteberechtigungen für Registerkarten](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten in Anmeldesitzungen

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar. Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen. Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich bei Teams abmelden oder Mandanten in Teams wechseln.  

> [!NOTE]
> Wenn Sie den berechtigungen für systemeigene Geräte zustimmen, ist sie nur für Ihre _aktuelle Anmeldesitzung_ gültig.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrieren von QR- oder Barcodescannerfunktionen in Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integrieren von Standortfunktionen in Teams](location-capability.md)
