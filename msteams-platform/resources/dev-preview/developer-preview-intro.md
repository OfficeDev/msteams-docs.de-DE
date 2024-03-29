---
title: Öffentliche Entwicklervorschau für Microsoft Teams
description: Eine Entwicklervorschau (Beta) ist ein öffentliches Programm zum Erkunden und Testen anstehender Features für eine mögliche Aufnahme in Ihre Microsoft Teams-App.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: dd0583f453e93a0127bf4cbcc29a6a56dec6655a
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100287"
---
# <a name="public-developer-preview-for-teams"></a>Öffentliche Entwicklervorschau für Teams

>[!NOTE]
>Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Developer Preview ist ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht veröffentlichte Features in Microsoft Teams bietet. Auf diese Weise können Sie neue Funktionen erkunden und testen, um sie möglicherweise in Ihre Teams-App aufzunehmen. Wir freuen uns auch über [Feedback](~/feedback.md) zu allen Features in der Entwicklervorschau. Die Entwicklervorschau ist pro Microsoft Teams-Client aktiviert, sodass Sie sich keine Gedanken über Auswirkungen auf Ihre gesamte Organisation machen müssen.

## <a name="developer-preview-app-manifest"></a>Entwicklervorschau-App-Manifest

Viele in der Entwicklervorschau aktivierte Features erfordern Änderungen an der JSON-Datei Ihres App-Manifests. Dazu müssen Sie das [Manifestschema der Entwicklervorschau](~/resources/schema/manifest-schema-dev-preview.md) verwenden. Wenn Sie dieses Schema verwenden, können Sie weder das [Entwicklerportal für Teams](~/concepts/build-and-test/teams-developer-portal.md) verwenden, um diese Änderungen vorzunehmen, noch können Sie es verwenden, um Ihre App zu Testzwecken hochzuladen. Um Ihre App hochzuladen, wählen Sie das `More apps`-Symbol in der App-Leiste aus und wählen Sie dann die `Upload a custom app link` aus. Mit dieser Methode können Sie nur eine gezippte Version Ihres App-Pakets hochladen.

Möglicherweise ist es hilfreich, das Entwicklerportal zum Erstellen der Nicht-Entwicklervorschauteile Ihres App-Pakets zu verwenden, dieses Paket dann zu exportieren und die `manifest.json`-Datei manuell zu bearbeiten, um die Entwicklervorschaufeatures hinzuzufügen, die Sie verwenden möchten. Sobald Sie der `manifest.json`-Datei Funktionen für die Entwicklervorschau hinzugefügt haben, können Sie das Paket nicht mehr ins Entwicklerportal für Teams importieren.

## <a name="enable-developer-preview"></a>Entwicklervorschau aktivieren

Die Entwicklervorschau ist pro Client aktiviert, aber die Option zum Aktivieren der Entwicklervorschau wird auf Organisationsebene gesteuert. Um die Option zum Aktivieren der Entwicklervorschau für eine Einzelperson zu aktivieren, müssen Sie sicherstellen, dass diese benutzerdefinierte Apps hochladen kann. Weitere Informationen finden Sie unter [Einrichten Ihres Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).

Die Verwendung einer Anwendung, die Funktionen der Entwicklervorschau enthält, kann bei Clients, die die Entwicklervorschau nicht aktiviert haben, zu unerwartetem Verhalten führen. Wenn kein Eintrag für die Entwicklervorschau angezeigt wird, ist der wahrscheinlichste Grund, dass Ihre Organisation nicht für das Hochladen von Apps konfiguriert ist.

### <a name="on-a-desktop-or-web-client"></a>Auf einem Desktop- oder Webclient

So aktivieren Sie die öffentliche Entwicklervorschau auf einem Desktop- oder Webclient:

1. Aktivieren Sie das Hochladen oder Querladen benutzerdefinierter Apps für Ihren Entwicklermandanten. Weitere Informationen finden Sie unter [Aktivieren von benutzerdefinierten Teams-Apps](../../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading).
1. Wählen Sie das Menü mit den Auslassungspunkten (...) neben Ihrem Benutzerprofil aus, um das Teams-Menü anzuzeigen.
1. Wählen Sie **Über** > **Entwicklervorschau** aus.
1. Wählen Sie **Zur Entwicklervorschau wechseln** aus.

### <a name="on-a-mobile-client"></a>Auf einem mobilen Client

So aktivieren Sie die öffentliche Entwicklervorschau auf einem mobilen Client:

1. Aktivieren Sie das Hochladen oder Querladen von Apps für Ihren Entwicklermandanten. Weitere Informationen finden Sie unter [Aktivieren von benutzerdefinierten Teams-Apps](../../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading).
1. Öffnen Sie das Hamburger-Menü oben links, und wählen Sie dann **Einstellungen** aus.
1. Wählen Sie **Informationen** aus.
1. Aktivieren Sie den Schalter für die **Entwickler-Vorschau**.

## <a name="disable-developer-preview"></a>Entwicklervorschau deaktivieren

Verwenden Sie das gleiche Menüelement unter Info → Entwicklervorschau, und wählen Sie es aus, um sie zu deaktivieren.

## <a name="see-also"></a>Siehe auch

[Testen und debuggen Sie Ihre Microsoft Teams-App](~/concepts/build-and-test/debug.md)
