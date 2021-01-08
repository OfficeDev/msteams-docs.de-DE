---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: 6be183d2610616f3bd3bdf32554976322193c132
ms.sourcegitcommit: d0e71ea63af2f67eba75ba283ec46cc7cdf87d75
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "49731979"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte

Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die Zugriff auf systemeigene Gerätefunktionen benötigen, wie:

> [!div class="checklist"]
>
> * Kamera
> * Mikrofon
> * Ort
> * Benachrichtigungen

[!Note] Um die Kamera-und Bildfunktionen in Ihre Microsoft Teams-Mobile App zu integrieren, referieren Sie die [Kamera-und Bildfunktionen in Microsoft Teams.](../../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!IMPORTANT]
>
> * Derzeit unterstützt Teams Mobile Clients nur den Zugriff auf `camera` , `gallery` , `mic` und `location` über Native Gerätefunktionen und steht in allen APP-Konstrukten einschließlich Registerkarten zur Verfügung. </br>
> * Unterstützung für `camera` , `gallery` und `mic` wird über die [**selectMedia-API**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)aktiviert. Für die Einzelbild Erfassung können Sie die [**captureImage-API**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true)verwenden.
> * Die Unterstützung für `location` ist über die [**getLocation-API**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true)aktiviert. Es wird empfohlen, diese API zu verwenden, da die [**Geolocation-API**](../../resources/schema/manifest-schema.md#devicepermissions) derzeit nicht vollständig auf allen Desktop-Clients unterstützt wird.

## <a name="device-permissions"></a>Geräteberechtigungen

Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:

* Aufzeichnen und Freigeben von kurzen Videos
* Kurze audiomemos aufzeichnen und später speichern
* Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen

Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern Standard ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren. Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Teams.
1. Wählen Sie in der oberen rechten Ecke des Fensters Ihr Profilsymbol aus.
1. Wählen Sie  ->  im Dropdownmenü Einstellungen **Berechtigungen** aus.
1. Wählen Sie die gewünschten Einstellungen aus.

![Bildschirm "Geräte Berechtigungen-Desktopeinstellungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobilgeräte](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu **Einstellungen**  ->  **App-Berechtigungen**.
1. Wählen Sie die APP aus, für die Sie Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

![Bildschirm mit den mobilen Einstellungen für Geräte Berechtigungen](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a>Eigenschaften

Aktualisieren Sie Ihre APP, `manifest.json` indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```
> [!Note]
>
> Medien werden auch für Kamera Berechtigungen auf mobilen Geräten verwendet.

Mit jeder Eigenschaft können Sie den Benutzer auffordern, nach seiner Zustimmung zu Fragen:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| Medien         | Berechtigung zum Verwenden der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs Medien Katalogs |
| Geolocation   | Berechtigung zum Zurückgeben des Standorts des Benutzers      |
| Benachrichtigungen | Berechtigung zum Senden der Benutzer Benachrichtigungen      |
| MIDI          | Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument   |
| openextern  | Berechtigung zum Öffnen von Links in externen Anwendungen  |

## <a name="checking-permissions-from-your-tab"></a>Überprüfen von Berechtigungen auf der Registerkarte

Nachdem Sie Ihrem App-Manifest hinzugefügt haben `devicePermissions` , können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.

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

## <a name="prompting-the-user"></a>Auffordern des Benutzers

Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-oder Teams-API nutzen. 

Um beispielsweise den Benutzer aufzufordern, auf seinen Standort zuzugreifen, müssen Sie `getCurrentPosition` Folgendes aufrufen:

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

Um die Kamera auf dem Desktop oder im Internet verwenden zu können, wird von Microsoft Teams eine Berechtigungs Aufforderung angezeigt, wenn Sie `getUserMedia` Folgendes aufrufen:

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

Um das Bild auf mobilen Geräten zu erfassen, fragt Microsoft Teams Mobile die Berechtigung ab, wenn Sie anrufen `captureImage()` :

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

Der Benutzer wird beim Aufruf von Benachrichtigungen aufgefordert `requestPermission` :

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

Um die Kamera oder den Zugriff auf die Fotogalerie zu verwenden, fragt Microsoft Teams Mobile beim Aufruf die Berechtigung ab `selectMedia()` :

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Um MIC zu verwenden, fragt Teams Mobile beim Aufruf die Berechtigung ab `selectMedia()` :

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Um den Benutzer aufzufordern, den Standort auf der Kartenoberfläche freizugeben, fragt Teams Mobile beim Aufruf die Berechtigung ab `getLocation()` :

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Eingabeaufforderung für Desktop Geräte Berechtigungen für Tabs](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobilgeräte](#tab/mobile)

![Eingabeaufforderung für mobile Geräte Berechtigungen für Tabs](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten für Anmeldesitzungen

Für jede Anmeldesitzung werden systemeigene Geräte Berechtigungen gespeichert. Wenn Sie sich bei einer anderen Instanz von Teams (beispielsweise auf einem anderen Computer) anmelden, sind Ihre Geräte Berechtigungen aus ihren vorherigen Sitzungen nicht verfügbar. Stattdessen müssen Sie die Geräte Berechtigungen für die neue Anmeldesitzung erneut genehmigen. Dies bedeutet auch, dass die Geräte Berechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln). Beachten Sie Folgendes, wenn Sie systemeigene Geräte Berechtigungen entwickeln: die systemeigenen Funktionen, die Sie einwilligen, gelten nur für Ihre _aktuelle_ Anmeldesitzung.
