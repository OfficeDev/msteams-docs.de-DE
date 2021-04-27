---
title: Developer Preview
description: Beschreibt die Features im öffentlichen Developer Preview von Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: f19268afd81fe9fa7ae2116740e7b9d4ff8225cb
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019720"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Öffentliche Entwicklervorschau für Microsoft Teams

>[!NOTE]
>Features, die in der Vorschau enthalten sind, sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Explorationszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Developer Preview ist ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht freigegebene Features in Microsoft Teams bietet. Auf diese Weise können Sie anstehende Features für die mögliche Integration in Ihre Microsoft Teams-App erkunden und testen. Wir freuen uns auch [über Feedback](~/feedback.md) zu allen Features in der Entwicklervorschau. Die Entwicklervorschau ist pro Microsoft Teams-Client aktiviert, sodass Sie sich keine Gedanken über die Auswirkungen auf Ihre gesamte Organisation machen müssen.

## <a name="developer-preview-app-manifest"></a>Entwicklervorschau-App-Manifest

Viele features enabled in developer preview will require alterations to your app manifest JSON file. Hierzu müssen Sie das Entwicklervorschaumanifestschema verwenden [Wenn](~/resources/schema/manifest-schema-dev-preview.md) Sie dieses Schema verwenden, können Sie [App Studio](~/concepts/build-and-test/app-studio-overview.md) nicht verwenden, um diese Änderungen vorzunehmen, und Sie können es auch nicht verwenden, um Ihre App zu Testzwecken hochzuladen. Um Ihre App hochzuladen, müssen Sie auf das Symbol in der App-Leiste klicken, und wählen `More apps` Sie dann die `Upload a custom app link` aus. Mit dieser Methode können Sie nur eine gezippte Version Ihres App-Pakets hochladen.

Möglicherweise ist es hilfreich, App Studio zu verwenden, um die Vorschauteile ihres App-Pakets zu erstellen, das Paket zu exportieren und die Datei manuell zu bearbeiten, um die entwicklervorschaufeatures hinzuzufügen, die Sie verwenden `manifest.json` möchten. Nachdem Sie der Datei Entwicklervorschaufeatures hinzugefügt haben, können Sie das Paket nicht erneut in `manifest.json` App Studio importieren.

## <a name="enable-developer-preview"></a>Aktivieren der Entwicklervorschau

Die Entwicklervorschau ist pro Client aktiviert, die Option zum Aktivieren der Entwicklervorschau wird jedoch auf Organisationsebene gesteuert. Um die Option zum Aktivieren der Entwicklervorschau für eine Person zu aktivieren, müssen Sie sicherstellen, dass sie benutzerdefinierte Apps hochladen können. Weitere Informationen finden Sie unter Einrichten [Ihres Mandanten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

Die Verwendung einer App, die Entwicklervorschaufeatures enthält, kann dazu führen, dass Sich Clients, die die Entwicklervorschau nicht aktiviert haben, unerwartet verhalten. Wenn kein Eintrag für die Entwicklervorschau angezeigt wird, liegt der wahrscheinlichste Grund dafür, dass Ihre Organisation nicht für das Hochladen von Apps konfiguriert ist.

### <a name="on-a-desktop-or-web-client"></a>Auf einem Desktop- oder Webclient

Zum Aktivieren der öffentlichen Entwicklervorschau auf einem Desktop- oder Webclient müssen Sie die folgenden Schritte tun:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie hier [beschrieben.](~/concepts/build-and-test/prepare-your-o365-tenant.md)
1. Klicken Sie auf Ihr Profil (entweder oben rechts oder unten links auf der Teams-Schnittstelle), um das Menü Teams anzuzeigen.
1. Wählen Sie Informationen → Entwicklervorschau aus.
1. Wählen **Sie Switch to Developer preview aus.**

### <a name="on-a-mobile-client"></a>Auf einem mobilen Client

Gehen Sie wie folgt vor, um die Öffentliche Entwicklervorschau auf einem mobilen Client zu aktivieren:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie hier [beschrieben.](~/concepts/build-and-test/prepare-your-o365-tenant.md)
1. Öffnen Sie das Menü Hamburger oben links, und wählen Sie dann **Einstellungen aus.**
1. Wählen Sie **Informationen aus.**
1. Klicken Sie auf den Umschalter Entwicklervorschau.

## <a name="disable-developer-preview"></a>Deaktivieren der Entwicklervorschau

Verwenden Sie dasselbe Menüelement unter Informationen → Entwicklervorschau, und klicken Sie darauf, um es zu deaktivieren.

## <a name="features-available-in-developer-preview"></a>In der Entwicklervorschau verfügbare Features

Eine vollständige Liste der features, die derzeit in der Entwicklervorschau aktiviert sind, finden Sie unter Features [in der öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-features.md).
