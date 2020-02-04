---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: 454466ff17ecf275f6ae6c7413df8e117335f3c8
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674083"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte

Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die den Zugriff auf systemeigene Gerätefunktionen erfordern, wie:

* Kamera
* Mikrofon
* Ort
* Benachrichtigungen

![Bildschirm "Geräte Berechtigungseinstellungen"](~/assets/images/tabs/device-permissions.png)

> [!IMPORTANT]
> Die systemeigene Gerätefunktionalität wird derzeit nicht für Registerkarten auf mobilen Clients unterstützt, aber die vollständige Unterstützung wird bald verfügbar sein. Zur Vorbereitung auf diese Änderung sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten. Persönliche Apps (statische Registerkarten) sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar.
>
> Wenn die vollständige Unterstützung für Tabs freigegeben wird:
>
> * Alle Registerkarten sind auf mobilen Geräten immer verfügbar.
> * Ihr `contentUrl` **wird in den Mobile Teams-Client geladen**.
> * Bei Kanälen/Gruppenregisterkarten können Benutzer ihre Registerkarte weiterhin in einem separaten Browser öffnen `websiteUrl`, jedoch werden Sie `contentUrl` zuerst geladen.  

## <a name="device-permissions"></a>Geräteberechtigungen

Wenn Sie auf die Geräte Berechtigungen eines Benutzers zugreifen, können Sie viel umfassendere Erfahrungen sammeln, beispielsweise:

* Aufzeichnen und Freigeben von kurzen Videos
* Kurze audiomemos aufzeichnen und später speichern
* Verwenden von Benutzerstandort Informationen zum Anzeigen relevanter Informationen

Während der Zugriff auf diese Funktionen in den meisten modernen Webbrowsern standardmäßig ist, müssen Sie Microsoft Teams mitteilen, welche Funktionen Sie verwenden möchten, indem Sie Ihr App-Manifest aktualisieren. Auf diese Weise können Sie Berechtigungen wie in einem Browser anfordern, während Ihre APP auf dem Desktop-Client von Teams läuft.

## <a name="properties"></a>Eigenschaften

Aktualisieren Sie Ihre APP `manifest.json` , indem `devicePermissions` Sie die fünf Eigenschaften hinzufügen und angeben, die Sie in Ihrer Anwendung verwenden möchten:

``` json
"devicePermissions": [
    "media",
    "geolocation",
    "notifications",
    "midi",
    "openExternal"
],
```

Mit jeder Eigenschaft können Sie den Benutzer auffordern, seine Zustimmung einzuholen.

| Eigenschaft      | Beschreibung   |
| --- | --- |
| Medien         | Berechtigung zur Verwendung der Kamera, des Mikrofons und der Lautsprecher |
| Geolocation   | Berechtigung zum Zurückgeben des Standorts des Benutzers      |
| Benachrichtigungen | Berechtigung zum Senden der Benutzer Benachrichtigungen      |
| MIDI          | Berechtigung zum Senden und empfangen von MIDI-Informationen von einem digitalen Musikinstrument   |
| openextern  | Berechtigung zum Öffnen von Links in externen Anwendungen  |

## <a name="checking-permissions-from-your-tab"></a>Überprüfen von Berechtigungen auf der Registerkarte

Nachdem Sie Ihrem APP `devicePermissions` -Manifest hinzugefügt haben, können Sie Berechtigungen mit der HTML5-API "Permissions" überprüfen, ohne eine Eingabeaufforderung zu verursachen.

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

Um eine Eingabeaufforderung anzuzeigen, um die Zustimmung zum Zugriff auf Geräte Berechtigungen zu erhalten, müssen Sie die entsprechende HTML5-API nutzen. Um den Benutzer zum Zugreifen auf seine Kamera aufzufordern, müssen Sie beispielsweise`getUserMedia`

```Javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true });
```

Geolocation zeigt eine Berechtigungs Aufforderung an, wenn Sie die`getCurrentPosition`

```Javascript
navigator.geolocation.getCurrentPosition(function (position) { /*... */ });
```

Benachrichtigungen werden vom Benutzer aufgefordert, wenn Sie anrufen`requestPermission`

```Javascript
Notification.requestPermission(function(result) { /* ... */ });
```

![Eingabeaufforderung für Tabs Device Permissions](~/assets/images/tabs/device-permissions-prompt.png)