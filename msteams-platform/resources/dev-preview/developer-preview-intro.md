---
title: Entwicklervorschau
description: Beschreibt die Features in der öffentlichen Entwicklervorschau von Microsoft Teams
keywords: Entwicklerfeatures in Microsoft Teams Preview
ms.openlocfilehash: a09e715e4e2d4aba72726cc96c4d248c550a3ab1
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674374"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Public Developer Preview für Microsoft Teams

>[!NOTE]
>In der Vorschau enthaltene Features sind möglicherweise nicht vollständig und können Änderungen unterzogen werden, bevor Sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test-und Explorations Zwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Developer Preview ist ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht veröffentlichte Features in Microsoft Teams ermöglicht. Auf diese Weise können Sie bevorstehende Features für mögliche Inklusion in Ihre Microsoft Teams-App erkunden und testen. Wir begrüßen auch [Feedback](~/feedback.md) zu jedem Feature in der Entwicklervorschau. Die Entwicklervorschau ist pro Microsoft Teams-Client aktiviert, daher müssen Sie sich keine Gedanken über die Auswirkungen auf die gesamte Organisation machen.

## <a name="developer-preview-app-manifest"></a>Entwicklervorschau-App-Manifest

Für viele in der Entwicklervorschau aktivierte Features sind Änderungen an der JSON-Datei des App-Manifests erforderlich. Um dies zu tun, müssen Sie das [Entwickler-Vorschau-Manifest-Schema](~/resources/schema/manifest-schema-dev-preview.md) verwenden, wenn Sie dieses Schema verwenden, können Sie [App Studio](~/concepts/build-and-test/app-studio-overview.md) nicht verwenden, um diese Änderungen vorzunehmen, und Sie können es auch nicht verwenden, um Ihre APP zu Testzwecken hochzuladen. Um Ihre APP hochzuladen, müssen Sie auf der `More apps` App-Leiste auf das Symbol klicken und dann `Upload a custom app link`auf die. Mit dieser Methode können Sie nur eine gezippte Version des App-Pakets hochladen.

Möglicherweise ist es hilfreich, App Studio zum Erstellen der Vorschau Teile eines App-Pakets ohne Entwickler zu verwenden, dann dieses Paket zu exportieren und die `manifest.json` Datei manuell zu bearbeiten, um die gewünschten Entwicklervorschau-Features hinzuzufügen. Nachdem Sie der `manifest.json` Datei Entwicklervorschau-Features hinzugefügt haben, können Sie das Paket nicht erneut in App Studio importieren.

## <a name="enable-developer-preview"></a>Entwicklervorschau aktivieren

Die Entwicklervorschau wird auf Clientbasis aktiviert, aber die Option zum Aktivieren der Entwicklervorschau wird auf Organisationsebene gesteuert. Damit die Option Entwicklervorschau für eine einzelne Person aktiviert werden kann, müssen Sie sicherstellen, dass benutzerdefinierte apps hochgeladen werden können. Weitere Informationen finden Sie unter [Einrichten Ihres Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md) .

Die Verwendung einer APP, die Entwicklervorschau-Features enthält, kann dazu führen, dass Clients, die die Entwicklervorschau nicht aktiviert haben, unerwartet verhalten haben. Wenn Sie keinen Eintrag für Entwicklervorschau sehen, ist Ihre Organisation nicht für das Hochladen von apps konfiguriert.

### <a name="on-a-desktop-or-web-client"></a>Auf einem Desktop-oder WebClient

Um die öffentliche Entwicklervorschau auf einem Desktop-oder WebClient zu aktivieren, müssen Sie folgende Schritte ausführen:

1. Aktivieren des Hochladens von apps in der Admin-Konsole Ihres Mandanten wie [hier](~/concepts/build-and-test/prepare-your-o365-tenant.md)beschrieben.
1. Klicken Sie auf Ihr Profil (entweder in der oberen rechten oder linken Ecke der Benutzeroberfläche von Teams), um das Menü "Teams" anzuzeigen.
1. Wählen Sie about → Developer Preview aus.
1. Wählen Sie **zur Entwicklervorschau wechseln**aus.

### <a name="on-a-mobile-client"></a>Auf einem mobilen Client

Um die öffentliche Entwicklervorschau auf einem mobilen Client zu aktivieren, müssen Sie folgende Schritte ausführen:

1. Aktivieren des Hochladens von apps in der Admin-Konsole Ihres Mandanten wie [hier](~/concepts/build-and-test/prepare-your-o365-tenant.md)beschrieben.
1. Öffnen Sie das Menü Hamburger oben links, und wählen Sie dann **Einstellungen**aus.
1. Wählen Sie **about**aus.
1. Klicken Sie auf die Schaltfläche Entwicklervorschau.

## <a name="disable-developer-preview"></a>Entwicklervorschau deaktivieren

Verwenden Sie dasselbe Menüelement unter info → Entwicklervorschau, und klicken Sie darauf, um es zu deaktivieren.

## <a name="features-available-in-developer-preview"></a>In der Entwicklervorschau verfügbare Features

Eine vollständige Liste der Features, die derzeit in der Entwicklervorschau aktiviert sind, finden Sie unter: [Features in der Public Developer Preview](../../resources/dev-preview/developer-preview-features.md).
