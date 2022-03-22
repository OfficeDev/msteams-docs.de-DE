---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Teams-App-Funktionen – Geräte-natives Scan-Qr-Barcode-Bild-Audiovideo
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzufordern, die in der Regel eine Zustimmung des Benutzers erfordern, z. B. Scan-QR, Barcode, Bild, Audio, Videofunktionen
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: 3cb15e82101be7df9f90c94928fa91ae570c14d5
ms.sourcegitcommit: a36760750ff4f510c374a4c956be57f7c1b4a0db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2022
ms.locfileid: "63674964"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App

Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort erweitern. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.

> [!NOTE]
>
> * Informationen zum Integrieren von Medienfunktionen in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren von Medienfunktionen](mobile-camera-image-permissions.md).
> * Informationen zum Integrieren der QR- oder Strichcodescannerfunktion in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren der QR- oder Strichcodescanner-Funktion in Teams](qr-barcode-scanner-capability.md).
> * Informationen zum Integrieren von Standortfunktionen in Ihre Microsoft Teams mobilen App finden Sie unter [Integrieren von Standortfunktionen](location-capability.md).

## <a name="native-device-permissions"></a>Systemeigene Geräteberechtigungen

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können. Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messaging-Erweiterungen, ähnlich. Der Benutzer muss zur Seite "Berechtigungen" in Teams Einstellungen wechseln, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie umfassendere Funktionen auf der Teams Plattform erstellen, z. B.:

* Erfassen und Anzeigen von Bildern.
* Scannen Sie QR oder Barcode.
* Aufzeichnen und Freigeben kurzer Videos.
* Notieren Sie Audionotizen, und speichern Sie sie zur späteren Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzuzeigen.

> [!NOTE]
> * Derzeit unterstützt Teams keine Geräteberechtigungen für Apps mit mehreren Fenstern, Registerkarten und den Besprechungsbereich.
> * Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter ["Berechtigungen für Browsergeräte"](browser-device-permissions.md).

## <a name="access-device-permissions"></a>Zugreifen auf Geräteberechtigungen

Das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) stellt die Tools bereit, die Ihre Teams mobile App benötigt, um auf die [Geräteberechtigungen](#manage-permissions) des Benutzers zuzugreifen und eine umfassendere Oberfläche zu erstellen.

Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf dem Teams Desktopclient ausgeführt wird.

> [!NOTE]
> Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen und QR-Strichcodescanner nur für mobile Clients verfügbar.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in Teams Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps **zulassen oder** verweigern auswählt.

# <a name="mobile"></a>[Mobil](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu **Einstellungen** >  **App-Berechtigungen**.
1. Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Ihre Teams-App.
1. Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen Sie im Dropdownmenü **Einstellungen** >  **Permissions** aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](~/assets/images/tabs/device-permissions.png)

---

## <a name="specify-permissions"></a>Angeben von Berechtigungen

Aktualisieren Sie Ihre App, `manifest.json` indem Sie die folgenden fünf Eigenschaften hinzufügen `devicePermissions` und angeben, die Sie in Ihrer Anwendung verwenden:

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

Überprüfen Sie nach dem Hinzufügen `devicePermissions` zum App-Manifest die Berechtigungen mithilfe der **HTML5-Berechtigungs-API** , ohne eine Aufforderung zu verursachen:

``` JavaScript
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
>
> * Unterstützung für `camera`, `gallery`und `microphone` ist über [**die selectMedia-API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) aktiviert. Verwenden Sie [**die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung für `location` wird über [**die getLocation-API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) aktiviert. Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf Teams Desktopclient unterstützt wird.

Beispiel:

* Um den Benutzer aufzufordern, auf seine Position zuzugreifen, müssen Sie Folgendes aufrufen `getCurrentPosition()`:

    ```JavaScript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

* Um den Benutzer aufzufordern, auf seine Kamera auf dem Desktop oder im Web zuzugreifen, müssen Sie Folgendes aufrufen `getUserMedia()`:

    ```JavaScript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

* Um das Bild auf mobilgeräten zu erfassen, fordert Teams Mobile beim Anruf `captureImage()`die Berechtigung an:

    ```JavaScript
            function captureImage() {
            microsoftTeams.media.captureImage((error, files) => {
                // If there's any error, an alert shows the error message/code
                if (error) {
                    if (error.message) {
                        alert(" ErrorCode: " + error.errorCode + error.message);
                    } else {
                        alert(" ErrorCode: " + error.errorCode);
                    }
                } else if (files) {
                    image = files[0].content;
                    // Adding this image string in src attr of image tag will display the image on web page.
                    let imageString = "data:" + item.mimeType + ";base64," + image;
                }
            });
        } 
    ```

* Benachrichtigungen fordern den Benutzer beim Aufrufen `requestPermission()`an:

    ```JavaScript
    Notification.requestPermission(function(result) { /* ... */ });
    ```

* Um die Kamera zu verwenden oder auf die Fotogalerie zuzugreifen, fragt Teams Mobiltelefon beim Anruf `selectMedia()`nach der Berechtigung:

    ```JavaScript
     function selectMedia() {
     microsoftTeams.media.selectMedia(mediaInput, (error, attachments) => {
         // If there's any error, an alert shows the error message/code
         if (error) {
             if (error.message) {
                 alert(" ErrorCode: " + error.errorCode + error.message);
             } else {
                 alert(" ErrorCode: " + error.errorCode);
             }
         } else if (attachments) {
             // creating image array which contains image string for all attached images. 
             const imageArray = attachments.map((item, index) => {
                 return ("data:" + item.mimeType + ";base64," + item.preview)
             })
         }
     });
    } 
  ```

* Um das Mikrofon zu verwenden, fordert Teams Mobiltelefon beim Anruf `selectMedia()`die Berechtigung an:

    ```JavaScript
     function selectMedia() {
     microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
         // If there's any error, an alert shows the error message/code
         if (error) {
             if (error.message) {
                 alert(" ErrorCode: " + error.errorCode + error.message);
             } else {
                 alert(" ErrorCode: " + error.errorCode);
             }
         }

         if (attachments) {
             // taking the first attachment  
             let audioResult = attachments[0];

             // setting audio string which can be used in Video tag
             let audioData = "data:" + audioResult.mimeType + ";base64," + audioResult.preview
         }
     });
     }
    ```

* Um den Benutzer aufzufordern, den Standort auf der Kartenoberfläche freizugeben, fragt Teams Mobile beim Aufrufen `getLocation()`nach der Berechtigung:

    ```JavaScript
     function getLocation() {
     microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
         let currentLocation = JSON.stringify(location);
     });
     } 
    ```

# <a name="mobile"></a>[Mobil](#tab/mobile)

   ![Registerkarten - Eingabeaufforderung für Berechtigungen für mobile Geräte](../../assets/images/tabs/MobileLocationPermission.png)

# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräteberechtigungen](~/assets/images/tabs/device-permissions-prompt.png)

---

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten über Anmeldesitzungen hinweg

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich also bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus ihren vorherigen Sitzungen nicht verfügbar. Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen. Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.  

> [!NOTE]
> Wenn Sie den systemeigenen Geräteberechtigungen zustimmen, ist sie nur für Ihre _aktuelle_ Anmeldesitzung gültig.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
|Geräteberechtigungen | Verwenden Microsoft Teams Registerkarten-Beispiel-App zum Veranschaulichen von Geräteberechtigungen |  [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen für den Browser](browser-device-permissions.md)
* [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
* [Integrieren von QR- oder Strichcodescannern in Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](location-capability.md)
