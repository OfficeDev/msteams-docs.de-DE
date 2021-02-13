---
title: Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App
keywords: Berechtigungen für die Funktionen von Teams-Apps
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features an fordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
ms.topic: how-to
ms.openlocfilehash: 0343754eacbb6088a3e44fa5df8ec90e3b10b076
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231610"
---
# <a name="request-device-permissions-for-your-microsoft-teams-app"></a>Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-App

Sie können Ihre Teams-App um systemeigene Gerätefunktionen erweitern, z. B. Kamera, Mikrofon und Position. In diesem Dokument erfahren Sie, wie Sie die Zustimmung des Benutzers anfordern und auf die systemeigenen Geräteberechtigungen zugreifen.

> [!NOTE]
> Informationen zum Integrieren von Medienfunktionen in Ihre mobile Microsoft Teams-App finden Sie [unter "Integrieren von Medienfunktionen".](mobile-camera-image-permissions.md)

## <a name="native-device-permissions"></a>Systemeigene Geräteberechtigungen

Sie müssen die Geräteberechtigungen anfordern, um auf systemeigene Gerätefunktionen zugreifen zu können. Die Geräteberechtigungen funktionieren für alle App-Konstrukte, z. B. Registerkarten, Aufgabenmodule oder Messagingerweiterungen, ähnlich. Der Benutzer muss zur Berechtigungsseite in den Einstellungen von Teams wechseln, um Geräteberechtigungen zu verwalten.
Durch den Zugriff auf die Gerätefunktionen können Sie vielfältigere Funktionen auf der Teams-Plattform erstellen, z. B.:
* Erfassen und Anzeigen von Bildern.
* Aufzeichnen und Freigeben kurzer Videos.
* Notieren Sie Audionotizen, und speichern Sie sie für die spätere Verwendung.
* Verwenden Sie die Standortinformationen des Benutzers, um relevante Informationen anzeigen zu können.

## <a name="access-device-permissions"></a>Zugreifen auf Geräteberechtigungen

Das [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) von Microsoft Teams stellt die Tools bereit, die Für Ihre mobile Microsoft Teams-App erforderlich sind, um auf die Geräteberechtigungen des Benutzers zu zugreifen und eine reichhaltigere Benutzererfahrung zu schaffen. [](#manage-permissions)

Während der Zugriff auf diese Features in modernen Webbrowsern standard ist, müssen Sie Teams über die Features informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Dieses Update ermöglicht es Ihnen, Berechtigungen zu fordern, während Ihre App auf dem Teams-Desktopclient ausgeführt wird.

> [!NOTE] 
> Derzeit ist die Unterstützung von Medienfunktionen von Microsoft Teams nur für mobile Clients verfügbar.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

Ein Benutzer kann Geräteberechtigungen in den Einstellungen von Teams verwalten, indem er die Berechtigung **"Zulassen"** oder "Verweigern" **für** bestimmte Apps aus.
 
# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Ihre Teams-App.
1. Wählen Sie ihr Profilsymbol in der oberen rechten Ecke des Fensters aus.
1. Wählen **Sie im**  >   Dropdownmenü "Einstellungsberechtigungen" aus.
1. Wählen Sie die gewünschten Einstellungen aus.

   ![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu   >  **"Einstellungen-App-Berechtigungen".**
1. Wählen Sie die App aus, für die Sie die Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

    ![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="specify-permissions"></a>Angeben von Berechtigungen

Aktualisieren Sie die App, indem Sie die fünf Eigenschaften hinzufügen und angeben, die `manifest.json` Sie in Ihrer Anwendung `devicePermissions` verwenden:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Mit jeder Eigenschaft können Sie den Benutzer bitten, seine Zustimmung einzuholen:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| media         | Berechtigung zur Verwendung der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf die Mediengalerie. |
| geolocation   | Berechtigung zum Zurückgeben des Standorts des Benutzers.      |
| Benachrichtigungen | Berechtigung zum Senden von Benutzerbenachrichtigungen.      |
| midi          | Berechtigung zum Senden und Empfangen von Musik instrument digital Interface (MIDI)-Informationen von einem digitalen Musikgerät.   |
| openExternal  | Berechtigung zum Öffnen von Links in externen Anwendungen.  |

## <a name="check-permissions-from-your-app"></a>Überprüfen von Berechtigungen aus Ihrer App

Überprüfen Sie nach dem Hinzufügen zu Ihrem App-Manifest die Berechtigungen mithilfe der `devicePermissions` **HTML5-Berechtigungs-API,** ohne eine Eingabeaufforderung zu verursachen:

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

Nutzen Sie entsprechende HTML5- oder Teams-API, um eine Eingabeaufforderung für den Zugriff auf Geräteberechtigungen einzuholen.

> [!IMPORTANT]
> * Unterstützung für `camera` , und wird über `gallery` `microphone` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) Verwenden [**Sie die captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true) für eine einzelne Bildaufnahme.
> * Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) Sie müssen dies `getLocation API` für den Standort verwenden, da die HTML5-Geolocation-API derzeit nicht vollständig auf dem Teams-Desktopclient unterstützt wird.

Beispiel:
 * Um den Benutzer zum Zugriff auf seinen Standort aufforderen zu können, müssen Sie dies `getCurrentPosition()` aufrufen:

    ```Javascript
    navigator.geolocation.getCurrentPosition    (function (position) { /*... */ });
    ```

 * Um den Benutzer auf dem Desktop oder im Web zum Zugriff auf seine Kamera aufforderen zu können, müssen Sie dies `getUserMedia()` aufrufen:

    ```Javascript
    navigator.mediaDevices.getUserMedia({ audio: true, video: true });
    ```

 * Um das Bild auf mobilen Geräten zu erfassen, fordert Teams Mobile beim Anruf die Berechtigung `captureImage()` an:

    ```Javascript
    microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
      /* ... */
    });
    ```

 * Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission()` anrufen:

    ```Javascript
    Notification.requestPermission(function(result) { /* ... */ });
    ```




* Um die Kamera oder den Zugriff auf die Fotogalerie zu verwenden, fordert Teams Mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:

    ```JavaScript
    microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    );
    ```

* Um das Mikrofon zu verwenden, fordert Teams Mobile die Berechtigung an, wenn Sie `selectMedia()` anrufen:

    ```JavaScript 
    microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
      /* ... */
    });
    ```

* Um den Benutzer zur Freigabe des Standorts auf der Kartenoberfläche auffordern, fordert Teams Mobile die Berechtigung an, wenn Sie `getLocation()` anrufen:

    ```JavaScript 
    microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
      /* ... *
    /});
    ```
# <a name="desktop"></a>[Desktop](#tab/desktop)

   ![Eingabeaufforderung für Registerkarten für Desktopgeräte](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

   ![Eingabeaufforderung für Registerkarten für Mobilgeräte](../../assets/images/tabs/MobileLocationPermission.png)

* * * 

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten in allen Anmeldesitzungen

Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich bei einer anderen Instanz von Teams anmelden, z. B. auf einem anderen Computer, sind Ihre Geräteberechtigungen aus Ihren vorherigen Sitzungen nicht verfügbar. Daher müssen Sie den Geräteberechtigungen für die neue Sitzung erneut zustimmen. Das bedeutet auch, dass Ihre Geräteberechtigungen aus der vorherigen Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden oder Mandanten in Teams wechseln.  

> [!NOTE]
> Wenn Sie den systemeigenen Geräteberechtigungen zustimmen, ist sie nur für Ihre _aktuelle Anmeldesitzung_ gültig.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Integrieren von Medienfunktionen in Teams](mobile-camera-image-permissions.md)
