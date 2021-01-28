---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
ms.topic: how-to
keywords: Devtools debuggen Entwicklertools für mobile Chrome-Desktopclients
ms.openlocfilehash: 8f23a5d56faa00d40451d2bbeadde32f6a5d0f7f
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014579"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Entwicklertools für Microsoft Teams-Registerkarten

Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 (unter Windows) oder Command-Option-I (unter MacOS). Die DevTools bietet Ihnen Zugriff auf:

1. Anzeigen von Konsolenprotokollen.
1. Html-, CSS- und Netzwerkanforderungen während der Laufzeit anzeigen/ändern.
1. Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie ein interaktives Debuggen aus.

Das Feature ist nur in Desktop- und Android-Clients verfügbar, Developer Preview aktiviert wurde. Weitere [Informationen finden Sie unter "Developer Preview](~/resources/dev-preview/developer-preview-intro.md) aktivieren".

## <a name="accessing-devtools-in-the-desktop"></a>Zugreifen auf DevTools auf dem Desktop

Obwohl die Webversion von Teams und die Desktopversion von Teams fast identisch sind, gibt es einige Unterschiede, insbesondere im Hinblick auf die Authentifizierung. Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools. Hier erfahren Sie, wie Sie über den Teams-Desktopclient zu ihnen kommen. So verwenden Sie DevTools im Desktopclient:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)
1. Öffnen Sie eine Registerkarte, damit Sie etwas mit devTools überprüfen können.
1. Öffnen der DevTools
    * Unter Windows öffnen Sie DevTools über das Microsoft Teams-Symbol in der Taskleiste des Desktops:

  ![Klicken Sie mit der rechten Maustaste, um DevTools zu öffnen.](~/assets/images/dev-preview/devtools-right-click.png)

    * Klicken Sie unter MacOS im Dock auf das Microsoft Teams-Symbol.

So sieht eine Beispielregisterkarte aus, wenn devTools geöffnet und ein Element ausgewählt ist:

![Registerkarte und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a>Zugreifen auf DevTools über einen Android-Client

Sie können die DevTools auch über den Teams -Android-Client aktivieren. Gehen Sie hierzu folgendermaßen vor:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)
1. Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für remote [debuggen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. Öffnen Sie in Ihrem Browser Chrome `chrome://inspect/#devices` .
1. Klicken **Sie unterhalb** der Registerkarte, die Sie debuggen möchten, auf "Überprüfen", wie im folgenden Screenshot dargestellt.

![Android DevTools](~/assets/images/android-devtools.png)
