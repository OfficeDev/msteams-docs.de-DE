---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 1bf7d246136a24316309ae144ac9552c5fd4f57d
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596273"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Entwicklertools für Microsoft Teams-Registerkarten

Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 (unter Windows) oder Command-Option-I (unter MacOS). Die DevTools bietet Ihnen Zugriff auf:

1. Anzeigen von Konsolenprotokollen.
1. Anzeigen/Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.
1. Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.

Das Feature ist nur auf Desktop- und Android-Clients verfügbar, nachdem Developer Preview aktiviert wurde. Weitere Informationen finden Sie unter [How do I enable Developer Preview.](~/resources/dev-preview/developer-preview-intro.md)

## <a name="accessing-devtools-in-the-desktop"></a>Zugreifen auf DevTools im Desktop

Obwohl die Webversion von Teams und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede, insbesondere im Hinblick auf die Authentifizierung. Manchmal ist die einzige Möglichkeit, herauszufinden, was passiert, die Verwendung der DevTools. Hier erfahren Sie, wie Sie über den Teams-Desktopclient zu ihnen kommen. So verwenden Sie DevTools im Desktopclient:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben](~/resources/dev-preview/developer-preview-intro.md)
1. Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.
1. Öffnen Sie devTools auf eine der folgenden Arten:
    * **Windows**: Wählen Sie das Symbol Teams im Desktoptablett aus.
    * **macOS**: Wählen Sie das Symbol Teams im Dock aus.

Der folgende Screenshot zeigt DevTools, das ein Element in einem Registerkartenkonfigurationsdialogfeld überprüft:

![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a>Zugreifen auf DevTools von einem Android-Client

Sie können devTools auch über den Teams Android-Client aktivieren.

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben](~/resources/dev-preview/developer-preview-intro.md)
1. Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für das [Remotedebugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .
1. Klicken **Sie auf Überprüfen** unter der Registerkarte, die Sie debuggen möchten, wie im screenshot unten.

![Android DevTools](~/assets/images/android-devtools.png)
