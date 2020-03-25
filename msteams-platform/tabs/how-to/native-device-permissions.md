---
title: Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte
description: Aktualisieren des App-Manifests, um Zugriff auf systemeigene Features anzufordern, in denen normalerweise Benutzer Zustimmung erforderlich ist
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: f0e19c0ed716147c097137c4ef0bf3454783b2eb
ms.sourcegitcommit: c4a7bc638e848a702cce92798cba84917fcecc35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "42928517"
---
# <a name="request-device-permissions-for-your-microsoft-teams-tab"></a>Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte

Möglicherweise möchten Sie die Registerkarte mit Features erweitern, die den Zugriff auf systemeigene Gerätefunktionen erfordern, wie:

* Kamera
* Mikrofon
* Standort
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
| media         | Berechtigung zur Verwendung der Kamera, des Mikrofons und der Lautsprecher |
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

## <a name="permission-behavior-across-login-sessions"></a>Berechtigungsverhalten für Anmeldesitzungen

Berechtigungen für systemeigene Geräte werden pro Anmeldesitzung gespeichert. Wenn Sie sich also bei einer anderen Instanz von Teams anmelden (z.b. auf einem anderen Computer), sind Ihre Geräte Berechtigungen aus ihren vorherigen Sitzungen nicht verfügbar. Stattdessen müssen Sie die Geräte Berechtigungen für den neuen Anmelde sessoin erneut einwilligen. Dies bedeutet auch, dass Ihre Geräte Berechtigungen für diese vorherige Anmeldesitzung gelöscht werden, wenn Sie sich von Teams abmelden (oder Mandanten innerhalb von Teams wechseln). Beachten Sie Folgendes, wenn Sie systemeigene Geräte Berechtigungen entwickeln: die systemeigenen Funktionen, die Sie einwilligen, gelten nur für Ihre _aktuelle_ Anmelde-sessoin.