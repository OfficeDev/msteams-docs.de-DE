---
title: Developer Preview
description: Beschreibt die Features in der öffentlichen Developer Preview von Microsoft Teams
ms.topic: conceptual
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: b8e8847d71ec3a571d434f952c79f3dd6a8f5bf1
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014075"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Öffentliche Entwicklervorschau für Microsoft Teams

>[!NOTE]
>Features, die in der Vorschau enthalten sind, sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Developer Preview ist ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht freigegebene Features in Microsoft Teams bietet. Auf diese Weise können Sie anstehende Features erkunden und testen, um potenzielle Inklusion in Ihre Microsoft Teams-App zu erhalten. Wir freuen uns auch [über Feedback](~/feedback.md) zu allen Features in der Entwicklervorschau. Die Entwicklervorschau ist pro Microsoft Teams-Client aktiviert, sodass Sie sich keine Gedanken über die Auswirkungen auf Ihre gesamte Organisation machen müssen.

## <a name="developer-preview-app-manifest"></a>Entwicklervorschau-App-Manifest

Viele Features, die in der Entwicklervorschau aktiviert sind, erfordern Änderungen an Ihrer App-Manifest-JSON-Datei. Dazu müssen Sie das Entwicklervorschaumanifestschema verwenden. Wenn Sie dieses Schema verwenden, können Sie [App Studio](~/concepts/build-and-test/app-studio-overview.md) nicht verwenden, um diese Änderungen vorzunehmen, und Sie können es auch nicht verwenden, um Ihre App zu Testzwecken hochzuladen. [](~/resources/schema/manifest-schema-dev-preview.md) Um Ihre App hochzuladen, müssen Sie auf das Symbol auf der App-Leiste klicken und dann `More apps` das `Upload a custom app link` auswählen. Mit dieser Methode können Sie nur eine gezippte Version Ihres App-Pakets hochladen.

Möglicherweise ist es hilfreich, App Studio zum Erstellen der Vorschauabschnitte ihres App-Pakets zu verwenden, die nicht für Entwickler vorgesehen sind, dann das Paket zu exportieren und die Datei manuell zu bearbeiten, um die Entwicklervorschaufeatures hinzuzufügen, die Sie verwenden `manifest.json` möchten. Nachdem Sie der Datei Entwicklervorschaufeatures hinzugefügt haben, können Sie das Paket nicht erneut in `manifest.json` App Studio importieren.

## <a name="enable-developer-preview"></a>Aktivieren der Entwicklervorschau

Die Entwicklervorschau ist pro Client aktiviert, aber die Option zum Aktivieren der Entwicklervorschau wird auf Organisationsebene gesteuert. Um die Option zum Aktivieren der Entwicklervorschau für eine Einzelperson zu aktivieren, müssen Sie sicherstellen, dass sie benutzerdefinierte Apps hochladen können. Weitere [Informationen finden Sie unter Einrichten Ihres](~/concepts/build-and-test/prepare-your-o365-tenant.md) Mandanten.

Die Verwendung einer App, die Vorschaufeatures für Entwickler enthält, kann dazu führen, dass sich Clients, die die Entwicklervorschau nicht aktiviert haben, unerwartet verhalten. Wenn kein Eintrag für die Entwicklervorschau angezeigt wird, ist der wahrscheinlichste Grund, dass Ihre Organisation nicht für das Hochladen von Apps konfiguriert ist.

### <a name="on-a-desktop-or-web-client"></a>Auf einem Desktop- oder Webclient

Gehen Sie wie folgt vor, um die öffentliche Entwicklervorschau auf einem Desktop- oder Webclient zu aktivieren:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie hier [beschrieben.](~/concepts/build-and-test/prepare-your-o365-tenant.md)
1. Klicken Sie auf Ihr Profil (entweder oben rechts oder unten links auf der Teams-Schnittstelle), um das Menü "Teams" anzuzeigen.
1. Select About → Developer preview.
1. Wählen **Sie "Zur Entwicklervorschau wechseln" aus.**

### <a name="on-a-mobile-client"></a>Auf einem mobilen Client

Gehen Sie wie folgt vor, um die öffentliche Entwicklervorschau auf einem mobilen Client zu aktivieren:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie hier [beschrieben.](~/concepts/build-and-test/prepare-your-o365-tenant.md)
1. Öffnen Sie das Hamburgermenü oben links, und wählen Sie dann **"Einstellungen" aus.**
1. Select **About**.
1. Klicken Sie auf den Umschalter "Entwicklervorschau".

## <a name="disable-developer-preview"></a>Deaktivieren der Entwicklervorschau

Verwenden Sie das gleiche Menüelement unter → Entwicklervorschau, und klicken Sie darauf, um es zu deaktivieren.

## <a name="features-available-in-developer-preview"></a>In der Entwicklervorschau verfügbare Features

Eine vollständige Liste der Features, die derzeit in der Entwicklervorschau aktiviert sind, finden Sie unter: [Features in der öffentlichen Entwicklervorschau.](../../resources/dev-preview/developer-preview-features.md)
