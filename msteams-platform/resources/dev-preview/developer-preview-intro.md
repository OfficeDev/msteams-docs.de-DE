---
title: Developer Preview
description: Beschreibt die Features in der Öffentlichen Entwicklervorschau für Microsoft Teams
ms.topic: conceptual
ms.localizationpriority: high
keywords: Features der Entwicklervorschau für Teams
ms.openlocfilehash: ee367daaf1570e75a5da7518cc2b0e27704741c4
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059793"
---
# <a name="public-developer-preview-for-microsoft-teams"></a>Öffentliche Entwicklervorschau für Microsoft Teams

>[!NOTE]
>Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Developer Preview ist ein öffentliches Programm für Entwickler, das frühzeitigen Zugriff auf nicht veröffentlichte Features in Microsoft Teams bietet. Auf diese Weise können Sie anstehende Features untersuchen und testen, um sie in Ihre Microsoft Teams-App einzubeziehen. Wir freuen uns auch über [Feedback](~/feedback.md) zu allen Features in der Entwicklervorschau. Die Entwicklervorschau ist pro Microsoft Teams-Client aktiviert, sodass Sie sich keine Gedanken über Auswirkungen auf Ihre gesamte Organisation machen müssen.

## <a name="developer-preview-app-manifest"></a>Entwicklervorschau-App-Manifest

Viele in der Entwicklervorschau aktivierte Features erfordern Änderungen an der JSON-Datei Ihres App-Manifests. Dazu müssen Sie das [Manifestschema der Entwicklervorschau](~/resources/schema/manifest-schema-dev-preview.md) verwenden. Wenn Sie dieses Schema verwenden, können Sie weder [App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden, um diese Änderungen vorzunehmen, noch können Sie es verwenden, um Ihre App zu Testzwecken hochzuladen. Um Ihre App hochzuladen, klicken Sie auf das `More apps` Symbol in der App-Leiste und wählen Sie dann die `Upload a custom app link` aus. Mit dieser Methode können Sie nur eine gezippte Version Ihres App-Pakets hochladen.

Möglicherweise ist es hilfreich, App Studio zum Erstellen der Nicht-Entwicklervorschauteile Ihres App-Pakets zu verwenden, dieses Paket dann zu exportieren und die `manifest.json`-Datei manuell zu bearbeiten, um die Entwicklervorschaufeatures hinzuzufügen, die Sie verwenden möchten. Nachdem Sie die Entwicklervorschaufeatures der `manifest.json`-Datei hinzugefügt haben, können Sie das Paket nicht erneut in App Studio importieren.

## <a name="enable-developer-preview"></a>Entwicklervorschau aktivieren

Die Entwicklervorschau ist pro Client aktiviert, aber die Option zum Aktivieren der Entwicklervorschau wird auf Organisationsebene gesteuert. Um die Option zum Aktivieren der Entwicklervorschau für eine Einzelperson zu aktivieren, müssen Sie sicherstellen, dass diese benutzerdefinierte Apps hochladen kann. Weitere Informationen finden Sie unter [Einrichten Ihres Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).

Die Verwendung einer App, die Entwicklervorschaufeatures enthält, kann dazu führen, dass Clients, die die Entwicklervorschau nicht aktiviert haben, sich unerwartet verhalten. Wenn kein Eintrag für die Entwicklervorschau angezeigt wird, liegt der wahrscheinlichste Grund darin, dass Ihre Organisation nicht für das Hochladen von Apps konfiguriert ist.

### <a name="on-a-desktop-or-web-client"></a>Auf einem Desktop- oder Webclient

Um die öffentliche Entwicklervorschau auf einem Desktop- oder Webclient zu aktivieren, müssen Sie folgendermaßen vorgehen:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie [hier](~/concepts/build-and-test/prepare-your-o365-tenant.md) beschrieben.
1. Klicken Sie auf Ihr Profil (entweder in der oberen rechten oder unteren linken Ecke der Teams-Benutzeroberfläche), um das Teams-Menü anzuzeigen.
1. Wählen Sie Info → Entwicklervorschau aus.
1. Wählen Sie **Zur Entwicklervorschau wechseln** aus.

### <a name="on-a-mobile-client"></a>Auf einem mobilen Client

Um die öffentliche Entwicklervorschau auf einem mobilen Client zu aktivieren, müssen Sie folgende Schritte ausführen:

1. Aktivieren des Hochladens von Apps in der Verwaltungskonsole Ihres Mandanten, wie [hier](~/concepts/build-and-test/prepare-your-o365-tenant.md) beschrieben.
1. Öffnen Sie das Hamburger-Menü oben links, und wählen Sie dann **Einstellungen** aus.
1. Wählen Sie **Informationen** aus.
1. Klicken Sie auf die Entwicklervorschau-Umschaltfläche.

## <a name="disable-developer-preview"></a>Entwicklervorschau deaktivieren

Verwenden Sie das gleiche Menüelement unter Info → Entwicklervorschau, und klicken Sie darauf, um sie zu deaktivieren.

## <a name="see-also"></a>Siehe auch

[Testen und debuggen Sie Ihre Microsoft Teams-App](~/concepts/build-and-test/debug.md)