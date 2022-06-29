---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features anzufordern, die eine Zustimmung des Benutzers erfordern, z. B. QR-, Barcode-, Bild-, Audio- und Videofunktionen scannen
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: a573855b6512cdbfcebb12c305973f8ad23113d6
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66484488"
---
# <a name="request-device-permissions-for-your-teams-app"></a>Anfordern von Geräteberechtigungen für Ihre Teams-App

Sie können Ihre Teams-App mit systemeigenen Gerätefunktionen wie Kamera, Mikrofon und Standort erweitern. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen können.

> [!NOTE]
>
> * Informationen zum Integrieren von Medienfunktionen in Ihren Microsoft Teams-Webclient, -Desktop und -Mobilgerät finden Sie unter [Integrieren von Medienfunktionen](media-capabilities.md).
> * Informationen zum Integrieren von QR- oder Strichcodescannerfunktionen in Ihre mobile Microsoft [Teams-App finden Sie unter Integrieren der QR- oder Strichcodescannerfunktion in Teams](qr-barcode-scanner-capability.md).
> * Informationen zum Integrieren von Standortfunktionen in Ihren Teams-Webclient, -Desktop und -Mobilgerät finden [Sie unter "Integrieren von Standortfunktionen"](location-capability.md).

## <a name="native-device-permissions"></a>Systemeigene Geräteberechtigungen

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können. Die Geräteberechtigungen funktionieren ähnlich für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messaging-Erweiterungen. Der Benutzer muss zur Berechtigungsseite in den Teams-Einstellungen wechseln, um Geräteberechtigungen zu verwalten. Sie können auf der Teams-Plattform mithilfe von Gerätefunktionen eine umfassendere Umgebung erstellen, z. B.: Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können. Die Geräteberechtigungen funktionieren ähnlich für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Nachrichtenerweiterungen. Der Benutzer muss zur Berechtigungsseite in den Teams-Einstellungen wechseln, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie eine umfassendere Umgebung auf der Teams-Plattform erstellen, z. B.:

* Erfassen und Anzeigen von Bildern
* Scannen Sie QR oder Barcode.
* Zeichnen Sie kurze Videos auf, und teilen Sie sie.
* Zeichnen Sie Audionotizen auf, und speichern Sie sie zur späteren Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzuzeigen.

> [!NOTE]
>
> * Derzeit unterstützt Teams keine Geräteberechtigungen für Apps mit mehreren Fenstern, Registerkarten und den Besprechungsbereich.
> * Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter [Browsergeräteberechtigungen](browser-device-permissions.md).
> * Derzeit ist Microsoft Teams nur für mobile Clients verfügbar.

## <a name="access-device-permissions"></a>Zugriff auf Geräteberechtigungen

Das [JavaScript-Client-SDK für Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) stellt die Tools bereit, die Für Ihre Teams-App erforderlich sind, um auf die [Geräteberechtigungen](#manage-permissions) des Benutzers zuzugreifen und eine umfassendere Erfahrung zu schaffen.

Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie berechtigungen anfordern, während Ihre App auf dem Teams-Desktop ausgeführt wird.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in den Teams-Einstellungen verwalten, indem er Berechtigungen für bestimmte Apps **zulassen** oder **verweigern** wählt.

# <a name="mobile"></a>[Mobil](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu **Einstellungen-App-Berechtigungen** > .
1. Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

    <!-- ![Device permissions mobile settings screen](../../assets/images/tabs/MobilePermissions.png) -->

    :::image type="content" source="~/assets/images/tabs/MobilePermissions.png" alt-text="Mobile Berechtigungen." border="true":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Ihre Teams-App.
1. Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen Sie im Dropdownmenü **"Einstellungsberechtigungen** > " aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   <!-- ![Device permissions desktop settings screen](~/assets/images/tabs/device-permissions.png) -->

   :::image type="content" source="~/assets/images/tabs/device-permissions.png" alt-text="Geräteberechtigung." border="true":::

---

## <a name="specify-permissions"></a>Berechtigungen angeben

Aktualisieren Sie Ihre App, `manifest.json` indem Sie hinzufügen `devicePermissions` und angeben, welche der folgenden fünf Eigenschaften Sie in Ihrer Anwendung verwenden:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Mit jeder Eigenschaft können Sie die Benutzer auffordern, um ihre Zustimmung zu bitten:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| media         | Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf die Mediengalerie. |
| Geolocation   | Berechtigung zum Zurückgeben des Standorts des Benutzers.      |
| Benachrichtigungen | Berechtigung zum Senden der Benutzerbenachrichtigungen.      |
| Midi          | Berechtigung zum Senden und Empfangen von Midi-Informationen (Musical Instrument Digital Interface) von einem digitalen Musikinstrument.   |
| openExternal  | Berechtigung zum Öffnen von Links in externen Anwendungen.  |

## <a name="check-permissions-from-your-app"></a>Überprüfen von Berechtigungen aus Ihrer App

Überprüfen Sie nach dem Hinzufügen `devicePermissions` zum App-Manifest die Berechtigungen mithilfe der **HTML5-Berechtigungs-API** , ohne eine Eingabeaufforderung zu verursachen:

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

Nutzen Sie die entsprechende HTML5- oder Teams-API, um eine Aufforderung zur Zustimmung zum Zugriff auf Geräteberechtigungen anzuzeigen.

> [!IMPORTANT]
>
> * Unterstützung für `camera`, `gallery`und `microphone` wird über [**die selectMedia-API**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) aktiviert. Verwenden Sie [**die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung für `location` wird über [**die getLocation-API**](/javascript/api/@microsoft/teams-js/microsoftteams.location?.view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) aktiviert. Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API auf dem Teams-Desktop derzeit nicht vollständig unterstützt wird.

Beispiel:

* Um den Benutzer auf seine Position zuzugreifen, müssen Sie Folgendes aufrufen `getCurrentPosition()`:

    ```JavaScript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

* Um den Benutzer aufzufordern, auf seine Kamera auf dem Desktop oder im Web zuzugreifen, müssen Sie Folgendes aufrufen `getUserMedia()`:

    ```JavaScript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

* Um die Bilder auf mobilen Geräten zu erfassen, fordert Teams Mobile beim Anrufen `captureImage()`folgende Berechtigung an:

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

* Benachrichtigungen fordern den Benutzer auf, wenn Sie folgendes aufrufen `requestPermission()`:

    ```JavaScript
    Notification.requestPermission(function(result) { /* ... */ });
    ```

* Um die Kamera zu verwenden oder auf die Fotogalerie zuzugreifen, fordert die Teams-App die Berechtigung an, wenn Sie folgendes aufrufen `selectMedia()`:

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

* Um das Mikrofon zu verwenden, fragt Teams Mobile die Berechtigung, wenn Sie anrufen `selectMedia()`:

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

* Um den Benutzer auf der Kartenoberfläche zum Freigeben des Standorts aufzufordern, fordert die Teams-App beim Aufrufen `getLocation()`folgende Berechtigung an:

    ```JavaScript
     function getLocation() {
     microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
         let currentLocation = JSON.stringify(location);
     });
     } 
    ```

# <a name="mobile"></a>[Mobil](#tab/mobile)

   <!-- ![Tabs mobile device permissions prompt](../../assets/images/tabs/MobileLocationPermission.png) -->

   :::image type="content" source="~/assets/images/tabs/MobileLocationPermission.png" alt-text="Mobile Standortberechtigung." border="true":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

   <!-- ![Tabs desktop device permissions prompt](~/assets/images/tabs/device-permissions-prompt.png) -->

   :::image type="content" source="~/assets/images/tabs/device-permissions-prompt.png" alt-text="Geräteberechtigung auf dem Desktop." border="true":::

---

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten in allen Anmeldesitzungen

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Dies bedeutet, dass, wenn Sie sich bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, Ihre Geräteberechtigungen aus Ihren vorherigen Sitzungen nicht verfügbar sind. Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen. Dies bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.  

> [!NOTE]
> Wenn Sie den berechtigungen des nativen Geräts zustimmen, ist sie nur für Ihre _aktuelle_ Anmeldesitzung gültig.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
|Geräteberechtigungen | Verwenden der Beispiel-App für die Microsoft Teams-Registerkarte zum Veranschaulichen von Geräteberechtigungen |  [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Geräteberechtigungen für den Browser](browser-device-permissions.md)
* [Integrieren von Medienfunktionen](media-capabilities.md)
* [Integrieren von QR-Code- oder Strichcodescanner-Funktionen in Microsoft Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Microsoft Teams](location-capability.md)
