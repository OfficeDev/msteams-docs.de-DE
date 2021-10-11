---
title: Entwicklervorschau
description: Beschreibt die Features in der Public Developer Preview von Microsoft Teams
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams– Vorschau für Entwicklerfeatures
ms.openlocfilehash: 8cf3f4faf4387aba6ea6238b0469bae840aba87f
ms.sourcegitcommit: c04a1a792773a9d5c61169c5702d94a8c478ad1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2021
ms.locfileid: "60260623"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Öffentliche Entwicklervorschau für Microsoft Teams

>[!NOTE]
>Features, die in der Vorschau enthalten sind, sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der Veröffentlichung verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Developer Preview ist ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht freigegebene Features in Microsoft Teams bietet. Auf diese Weise können Sie bevorstehende Features erkunden und testen, um eine potenzielle Einbindung in Ihre Microsoft Teams-App zu ermöglichen. Wir freuen uns auch über [Feedback](~/feedback.md) zu allen Features in der Entwicklervorschau. Die Entwicklervorschau ist pro Microsoft Teams Client aktiviert, sodass Sie sich keine Gedanken über die Auswirkungen auf Ihre gesamte Organisation machen müssen.

## <a name="developer-preview-app-manifest"></a>Entwicklervorschau-App-Manifest

Viele in der Entwicklervorschau aktivierte Features erfordern Änderungen an Ihrer JSON-Datei des App-Manifests. Dazu müssen Sie das [Entwicklervorschau-Manifestschema](~/resources/schema/manifest-schema-dev-preview.md)verwenden. Wenn Sie dieses Schema verwenden, können Sie [app Studio](~/concepts/build-and-test/app-studio-overview.md) nicht verwenden, um diese Änderungen vorzunehmen, und Sie können es auch nicht verwenden, um Ihre App zu Testzwecken hochzuladen. Um Ihre App hochzuladen, müssen Sie auf das `More apps` Symbol auf der App-Leiste klicken und dann die Option `Upload a custom app link` auswählen. Mit dieser Methode können Sie nur eine gezippte Version Ihres App-Pakets hochladen.

Möglicherweise ist es hilfreich, App Studio zum Erstellen der Nicht-Entwicklervorschau-Teile Ihres App-Pakets zu verwenden, dieses Paket zu exportieren und die Datei manuell `manifest.json` zu bearbeiten, um die Entwicklervorschaufeatures hinzuzufügen, die Sie verwenden möchten. Nachdem Sie der Datei Entwicklervorschaufeatures hinzugefügt haben, `manifest.json` können Sie das Paket nicht erneut in App Studio importieren.

## <a name="enable-developer-preview"></a>Aktivieren der Entwicklervorschau

Die Entwicklervorschau ist pro Client aktiviert, die Option zum Aktivieren der Entwicklervorschau wird jedoch auf Organisationsebene gesteuert. Um die Option zum Aktivieren der Entwicklervorschau für eine Einzelperson zu aktivieren, müssen Sie sicherstellen, dass diese benutzerdefinierte Apps hochladen können. Weitere Informationen finden Sie unter ["Einrichten Ihres Mandanten".](~/concepts/build-and-test/prepare-your-o365-tenant.md)

Die Verwendung einer App, die Entwicklervorschaufeatures enthält, kann dazu führen, dass sich Clients, die die Entwicklervorschau nicht aktiviert haben, unerwartet verhalten. Wenn kein Eintrag für die Entwicklervorschau angezeigt wird, ist der wahrscheinlichste Grund, dass Ihre Organisation nicht für das Hochladen von Apps konfiguriert ist.

### <a name="on-a-desktop-or-web-client"></a>Auf einem Desktop- oder Webclient

Um die öffentliche Entwicklervorschau auf einem Desktop- oder Webclient zu aktivieren, müssen Sie folgendermaßen vorgehen:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie [hier](~/concepts/build-and-test/prepare-your-o365-tenant.md)beschrieben.
1. Klicken Sie auf Ihr Profil (entweder in der oberen rechten oder unteren linken Ecke der Teams Schnittstelle), um das Teams Menü anzuzeigen.
1. Wählen Sie "Info → Entwicklervorschau" aus.
1. Wählen Sie **"Zur Entwicklervorschau wechseln" aus.**

### <a name="on-a-mobile-client"></a>Auf einem mobilen Client

Um die öffentliche Entwicklervorschau auf einem mobilen Client zu aktivieren, müssen Sie folgendermaßen vorgehen:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie [hier](~/concepts/build-and-test/prepare-your-o365-tenant.md)beschrieben.
1. Öffnen Sie das Hamburger-Menü oben links, und wählen Sie dann **Einstellungen** aus.
1. Wählen Sie **"Info" aus.**
1. Klicken Sie auf den Entwicklervorschau-Umschalter.

## <a name="disable-developer-preview"></a>Deaktivieren der Entwicklervorschau

Verwenden Sie dasselbe Menüelement unter "Info → Entwicklervorschau", und klicken Sie darauf, um es zu deaktivieren.



