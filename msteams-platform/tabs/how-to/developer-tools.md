---
title: DevTools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktop Clients zum devtools gelangen
keywords: DevTools Debugging Mobile Chrome Desktop Client Developer Tools
ms.openlocfilehash: 6c8ac15caf64c979b23155be847e8791988486e6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674330"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>DevTools für Microsoft Teams-Registerkarten

Wenn Microsoft Teams in einem Browser läuft, können Sie ganz einfach auf die devtools des Browsers zugreifen: F12 (unter Windows) oder Command-Option-I (unter MacOS). Die devtools ermöglicht den Zugriff auf:

1. Anzeigen von Konsolen Protokollen
1. Anzeigen/Ändern von HTML-, CSS-und Netzwerkanforderungen während der Laufzeit.
1. Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie ein interaktives Debugging aus.

Das Feature steht nur in Desktop-und Android-Clients zur Verfügung, nachdem die Entwicklervorschau aktiviert wurde. Weitere Informationen finden Sie unter [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) .

## <a name="accessing-devtools-in-the-desktop"></a>Zugreifen auf devtools auf dem Desktop

Während die Webversion von Teams und die Desktop Version von Microsoft Teams nahezu identisch sind, gibt es einige Unterschiede, insbesondere im Hinblick auf die Authentifizierung. Manchmal ist die Verwendung der devtools die einzige Möglichkeit, um herauszufinden, was vor sich geht. Hier erfahren Sie, wie Sie vom Microsoft Teams-Desktop Client aus dorthin gelangen. So verwenden Sie devtools im Desktop Client:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) aktiviert haben
1. Öffnen Sie eine Registerkarte, damit Sie mit dem devtools etwas zu inspizieren haben.
1. Öffnen des devtools
    * Unter Windows öffnen Sie devtools über das Microsoft Teams-Symbol in der Desktop Ablage:

  ![Klicken Sie mit der rechten Maustaste, um devtools zu öffnen](~/assets/images/dev-preview/devtools-right-click.png)

    * Klicken Sie unter MacOS auf das Microsoft Teams-Symbol im Dock.

Hier sehen Sie, wie eine Beispielregisterkarte aussieht, wenn das devtools geöffnet und ein Element ausgewählt ist:

![Tab-und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a>Zugriff auf devtools von einem Android-Client aus

Sie können die devtools auch über den Android-Client von Teams aktivieren. Gehen Sie hierzu folgendermaßen vor:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) aktiviert haben
1. Verbinden des Geräts mit dem Desktopcomputer und Einrichten des Android-Geräts für das [Remote Debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. Öffnen `chrome://inspect/#devices`Sie in Ihrem Chrome-Browser.
1. Klicken Sie auf über **prüfen** unter der Registerkarte, die Sie debuggen möchten, wie im Screenshot unten beschrieben.

![Android-devtools](~/assets/images/android-devtools.png)
