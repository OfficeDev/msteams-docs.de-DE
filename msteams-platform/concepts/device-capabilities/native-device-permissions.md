---
title: Anfordern von Geräteberechtigungen für Ihre Registerkarte
description: So aktualisieren Sie Ihr App-Manifest, um Zugriff auf systemeigene Features an fordern, für die in der Regel die Zustimmung des Benutzers erforderlich ist
ms.topic: how-to
keywords: Entwicklung von Teams-Registerkarten
ms.openlocfilehash: a2893fb2905584eac4b398287d431f406c23b12b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014530"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-Registerkarte

Sie können Ihre Registerkarte mit Features erweitern, die Zugriff auf systemeigene Gerätefunktionen erfordern, wie:

> [!div class="checklist"]
>
> * Kamera
> * Mikrofon
> * Ort
> * Benachrichtigungen

> [!NOTE]
> Informationen zum Integrieren von Kamera- und Bildfunktionen in Ihre mobile Microsoft Teams-App finden Sie unter ["Kamera- und Bildfunktionen in Teams".](../../concepts/device-capabilities/mobile-camera-image-permissions.md)

> [!IMPORTANT]
>
> * Derzeit unterstützt der mobile Client von Teams nur den Zugriff auf , und über systemeigene Gerätefunktionen und ist in allen `camera` `gallery` `mic` `location` App-Konstrukten einschließlich Registerkarten verfügbar. </br>
> * Unterstützung für `camera` , und wird über `gallery` `mic` [**selectMedia-API aktiviert.**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) Für eine einzelne Bildaufnahme können Sie [**die captureImage-API verwenden.**](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest#captureimage--error--sdkerror--files--file-------void-&preserve-view=true)
> * Die Unterstützung `location` für wird über die [**getLocation-API aktiviert.**](/javascript/api/@microsoft/teams-js/location?view=msteams-client-js-latest#getLocation_LocationProps___error__SdkError__location__Location_____void_&preserve-view=true) Es wird empfohlen, diese API zu verwenden, da [**die Geolocation-API**](../../resources/schema/manifest-schema.md#devicepermissions) derzeit nicht vollständig auf allen Desktopclients unterstützt wird.

## <a name="device-permissions"></a>Geräteberechtigungen

Wenn Sie auf die Geräteberechtigungen eines Benutzers zugreifen, können Sie viel reichhaltigere Benutzeroberflächen erstellen, z. B.:

* Aufzeichnen und Freigeben kurzer Videos
* Aufzeichnen kurzer Audionotizen und Speichern für später
* Verwenden von Benutzerstandortinformationen zum Anzeigen relevanter Informationen

Während der Zugriff auf diese Features in den meisten modernen Webbrowsern standard ist, müssen Sie Teams durch Aktualisieren Ihres App-Manifests wissen lassen, welche Features Sie verwenden möchten. Auf diese Weise können Sie berechtigungen wie in einem Browser ein verlangen, während Ihre App auf dem Desktopclient von Teams ausgeführt wird.

## <a name="manage-permissions"></a>
            Berechtigungen verwalten

# <a name="desktop"></a>[Desktop](#tab/desktop)

1. Öffnen Sie Teams.
1. Wählen Sie in der oberen rechten Ecke des Fensters Ihr Profilsymbol aus.
1. Wählen **Sie im**  ->   Dropdownmenü "Einstellungsberechtigungen" aus.
1. Wählen Sie die gewünschten Einstellungen aus.

![Bildschirm "Desktopeinstellungen für Geräteberechtigungen"](../../assets/images/tabs/device-permissions.png)

# <a name="mobile"></a>[Mobilgeräte](#tab/mobile)

1. Öffnen Sie Teams.
1. Wechseln Sie zu   ->  **"Einstellungen-App-Berechtigungen".**
1. Wählen Sie die App aus, für die Sie Einstellungen auswählen müssen.
1. Wählen Sie die gewünschten Einstellungen aus.

![Bildschirm "Mobile Einstellungen für Geräteberechtigungen"](../../assets/images/tabs/MobilePermissions.png)

---

## <a name="properties"></a>Eigenschaften

Aktualisieren Sie die App, indem Sie die fünf Eigenschaften hinzufügen und angeben, die Sie `manifest.json` in Ihrer Anwendung verwenden `devicePermissions` möchten:

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
> Medien werden auch für Kameraberechtigungen auf Mobilgeräten verwendet.

Jede Eigenschaft ermöglicht es Ihnen, den Benutzer auf, um seine Zustimmung zu bitten:

| Eigenschaft      | Beschreibung   |
| --- | --- |
| media         | Berechtigung zur Verwendung der Kamera, des Mikrofons, der Lautsprecher und des Zugriffs auf die Mediengalerie |
| geolocation   | Berechtigung zum Zurückgeben des Standorts des Benutzers      |
| Benachrichtigungen | Berechtigung zum Senden von Benutzerbenachrichtigungen      |
| midi          | Berechtigung zum Senden und Empfangen von Midiinformationen von einem digitalen Musikgerät   |
| openExternal  | Berechtigung zum Öffnen von Links in externen Anwendungen  |

## <a name="checking-permissions-from-your-tab"></a>Überprüfen von Berechtigungen auf Ihrer Registerkarte

Nachdem Sie Ihrem App-Manifest hinzugefügt haben, können Sie Berechtigungen mithilfe der HTML5-API "Berechtigungen" überprüfen, ohne eine `devicePermissions` Eingabeaufforderung zu verursachen.

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

## <a name="prompting-the-user"></a>Benutzeraufforderung

Um eine Aufforderung zum Einholen der Zustimmung zum Zugriff auf Geräteberechtigungen zu erhalten, müssen Sie die entsprechende HTML5- oder Teams-API nutzen. 

Um den Benutzer z. B. zum Zugreifen auf seinen Standort aufforderen, müssen Sie den folgenden Anruf `getCurrentPosition` aufrufen:

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

Um die Kamera auf Desktops oder im Web zu verwenden, zeigt Teams beim Aufrufen eine Berechtigungsaufforderung `getUserMedia` an:

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

Um das Bild auf mobilen Geräten zu erfassen, fordert Teams Mobile beim Anruf die Berechtigung `captureImage()` an:

```Javascript
microsoftTeams.media.captureImage((error: microsoftTeams.SdkError, files: microsoftTeams.media.File[]) => {
  /* ... */
});
```

Benachrichtigungen fordern den Benutzer auf, wenn Sie `requestPermission` anrufen:

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

Um kamera- oder zugriffsfotokataloge zu verwenden, fragt Teams Mobile die Berechtigung, wenn Sie `selectMedia()` anrufen:

```JavaScript
microsoftTeams.media.selectMedia({ maxMediaCount: 10, mediaType: microsoftTeams.media.MediaType.Image }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Zur Verwendung des Mikrofons fragt Teams Mobile beim Anruf die Berechtigung `selectMedia()` ab:

```JavaScript 
microsoftTeams.media.selectMedia({ maxMediaCount: 1, mediaType: microsoftTeams.media.MediaType.Audio }, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
  /* ... */
});
```

Um den Benutzer zum Freigeben des Standorts auf der Kartenoberfläche aufforderen, fordert Teams Mobile beim Anruf die Berechtigung `getLocation()` an:

```JavaScript 
microsoftTeams.location.getLocation({ allowChooseLocation: true, showMap: true }, (error: microsoftTeams.SdkError, location: microsoftTeams.location.Location) => {
  /* ... *
/});
```

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Eingabeaufforderung für Registerkarten für Desktopgeräte](~/assets/images/tabs/device-permissions-prompt.png)

# <a name="mobile"></a>[Mobilgeräte](#tab/mobile)

![Eingabeaufforderung für Registerkarten für Mobilgeräte](../../assets/images/tabs/MobileLocationPermission.png)


## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten in allen Anmeldesitzungen

Systemeigene Geräteberechtigungen werden für jede Anmeldesitzung gespeichert. Wenn Sie sich bei einer anderen Instanz von Teams (z. B. auf einem anderen Computer) anmelden, stehen Ihre Geräteberechtigungen aus Ihren vorherigen Sitzungen nicht zur Verfügung. Stattdessen müssen Sie den Geräteberechtigungen für die neue Anmeldesitzung erneut zustimmen. Dies bedeutet auch, dass Ihre Geräteberechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln). Beachten Sie dies beim Entwickeln systemeigener Geräteberechtigungen: Die systemeigenen Funktionen, denen Sie zustimmen, sind nur für Ihre _aktuelle Anmeldesitzung._
