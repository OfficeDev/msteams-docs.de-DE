---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für Teams-Apps-Funktionen
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzufordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
localization_priority: Normal
ms.topic: how-to
ms.openlocfilehash: 420b874770a4ad506dbedd575600f333a51ad5c0
ms.sourcegitcommit: ec79bbbc3a8daa1ad96de809fc6d17367e8f0c6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2021
ms.locfileid: "53726950"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App

Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort erweitern. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.

> [!NOTE]
> * Informationen zum Integrieren von Medienfunktionen in Ihre Microsoft Teams mobile App finden Sie unter [Integrieren von Medienfunktionen.](mobile-camera-image-permissions.md)
> * Informationen zum Integrieren der QR- oder Strichcodescanner-Funktion in Ihre Microsoft Teams mobile App finden Sie unter [Integrieren der QR- oder Strichcodescanner-Funktion in Teams.](qr-barcode-scanner-capability.md)
> * Informationen zum Integrieren von Standortfunktionen in Ihre Microsoft Teams mobile App finden Sie unter [Integrieren von Standortfunktionen.](location-capability.md)
> * Informationen zum Integrieren der Personenauswahlfunktion in Ihre mobile Microsoft Teams-App finden Sie unter Integrieren der [Personenauswahlfunktion in Teams.](people-picker-capability.md)

## <a name="native-device-permissions"></a>Systemeigene Geräteberechtigungen

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können. Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messaging-Erweiterungen, ähnlich. Der Benutzer muss zur Seite "Berechtigungen" in Teams Einstellungen wechseln, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie umfassendere Funktionen auf der Teams Plattform erstellen, z. B.:
* Erfassen und Anzeigen von Bildern.
* Scannen Sie QR oder Barcode.
* Aufzeichnen und Freigeben kurzer Videos.
* Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzuzeigen.

> [!NOTE]
> Derzeit unterstützt Teams keine Geräteberechtigungen für Apps, Registerkarten und das Besprechungs-Sidepanel. 

## <a name="access-device-permissions"></a>Zugreifen auf Geräteberechtigungen

Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) stellt die Tools bereit, die Ihre Teams mobile App benötigt, um auf die [Geräteberechtigungen](#manage-permissions) des Benutzers zuzugreifen und eine umfassendere Oberfläche zu erstellen.

Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf dem Teams Desktopclient ausgeführt wird.

> [!NOTE] 
> Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Strichcodescanner nur für mobile Clients verfügbar.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in Teams Einstellungen verwalten, indem **er** Berechtigungen für bestimmte Apps zulassen oder verweigern auswählt. 
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Ihre Teams-App.
1. Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen Sie im Dropdownmenü **Einstellungen**  >  **Berechtigungen** aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu **Einstellungen**  >  **App-Berechtigungen.**
1. Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Angeben von Berechtigungen

Aktualisieren Sie Ihre App, `manifest.json` indem Sie die folgenden fünf Eigenschaften hinzufügen und `devicePermissions` angeben, die Sie in Ihrer Anwendung verwenden:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| Medien         | Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf den Medienkatalog. |
| Geolocation   | Berechtigung zum Zurückgeben des Standorts des Benutzers.      |
| Benachrichtigungen | Berechtigung zum Senden von Benutzerbenachrichtigungen.      |
| Midi          | Berechtigung zum Senden und Empfangen von Midi-Informationen (Music Instrument Digital Interface) von einem digitalen Musik instrument.   |
| openExternal  | Berechtigung zum Öffnen von Links in externen Anwendungen.  |

## <a name="check-permissions-from-your-app"></a>Überprüfen von Berechtigungen aus Ihrer App

Überprüfen Sie nach dem Hinzufügen `devicePermissions` zum App-Manifest die Berechtigungen mithilfe der **HTML5-Berechtigungs-API,** ohne eine Aufforderung zu verursachen:

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

## <a name="use-teams-apis-to-get-device-permissions"></a>Verwenden von Teams-APIs zum Abrufen von Geräteberechtigungen

Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen anzuzeigen.

> [!IMPORTANT]
> * Unterstützung für `camera` , und ist über `gallery` `microphone` [**selectMedia-API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true)aktiviert. Verwenden Sie [**die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung für `location` ist über [**die getLocation-API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)aktiviert. Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API auf Teams Desktopclient derzeit nicht vollständig unterstützt wird.

Zum Beispiel:
 * Um den Benutzer aufzufordern, auf seine Position zuzugreifen, müssen Sie Folgendes `getCurrentPosition()` aufrufen:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Um den Benutzer aufzufordern, auf seine Kamera auf dem Desktop oder im Web zuzugreifen, müssen Sie `getUserMedia()` Folgendes aufrufen:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Um das Bild auf mobilgeräten zu erfassen, fordert Teams Mobile beim Anruf die Berechtigung `captureImage()` an:

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * Benachrichtigungen fordern den Benutzer beim Aufrufen `requestPermission()` an:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Um die Kamera zu verwenden oder auf die Fotogalerie zuzugreifen, fragt Teams Mobiltelefon beim Anruf nach der `selectMedia()` Berechtigung:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Um das Mikrofon zu verwenden, fordert Teams Mobiltelefon beim Anruf die Berechtigung `selectMedia()` an:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Um den Benutzer aufzufordern, den Standort auf der Kartenoberfläche freizugeben, fordert Teams Mobile beim Aufrufen die Berechtigung `getLocation()` an:

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

   ![Registerkarten - Eingabeaufforderung für Berechtigungen für mobile Geräte](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten über Anmeldesitzungen hinweg

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich also bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar. Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen. Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.  

> [!NOTE]
> Wenn Sie den systemeigenen Geräteberechtigungen zustimmen, ist sie nur für Ihre _aktuelle_ Anmeldesitzung gültig.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
|Geräteberechtigungen | Verwenden Microsoft Teams Registerkarten-Beispiel-App zum Demonstrieren von Geräteberechtigungen |  [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)

> [!div class="nextstepaction"]
> [Integrieren von QR- oder Strichcodescannern in Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integrieren von Standortfunktionen in Teams](location-capability.md)

> [!div class="nextstepaction"]
> [Integrieren der Personenauswahlfunktion in Teams](people-picker-capability.md)
