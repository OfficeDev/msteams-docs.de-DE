---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie zu devTools gelangen, wenn Sie den Microsoft Teams-Desktopclient und das Debuggen verwenden
ms.localizationpriority: medium
ms.topic: how-to
keywords: Entwicklertools debuggen die Entwicklertools für mobile Chrome-Desktopclients
ms.openlocfilehash: 6844648df311bd9ae326e74919cc64e871e54b05
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887420"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Entwicklertools für Microsoft Teams-Registerkarten

Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf die DevTools: F12 des Browsers unter Windows oder Command-Option-I unter MacOS zuzugreifen. DevTools bietet Ihnen Zugriff auf:

1. Anzeigen von Konsolenprotokollen.
1. Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.
1. Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie das interaktive Debuggen durch.

> [!NOTE]
> Das Feature ist nur für Desktop- und Android-Clients verfügbar, nachdem die **Entwicklervorschau** aktiviert wurde. Weitere Informationen finden Sie unter ["Aktivieren der Entwicklervorschau".](~/resources/dev-preview/developer-preview-intro.md)

## <a name="access-devtools-on-the-desktop"></a>Zugreifen auf DevTools auf dem Desktop

Während die Webversion und die Desktopversion von Teams fast identisch sind, gibt es einige Unterschiede bei der Authentifizierung. Manchmal ist die einzige Möglichkeit, herauszufinden, was passiert, die Verwendung der DevTools. Um DevTools im Desktopclient zu verwenden, müssen Sie:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)aktiviert haben.
1. Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.
1. Öffnen Sie devTools auf eine der folgenden Arten:
    * On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:<br>
  ![Klicken Sie mit der rechten Maustaste, um DevTools zu öffnen.](~/assets/images/dev-preview/devtools-right-click.png)
    * Klicken Sie unter MacOS auf das Symbol Microsoft Teams auf Dock.

Das folgende Beispiel zeigt, wie DevTools ein Dialogfeld für die Registerkartenkonfiguration öffnen und überprüfen:

   ![Registerkarte und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-device"></a>Zugreifen auf DevTools über ein Android-Gerät

Sie können die DevTools auch über den Teams Android-Client aktivieren. Um DevTools zu aktivieren, müssen Sie:

1. Aktivieren Sie die [Entwicklervorschau.](~/resources/dev-preview/developer-preview-intro.md)
1. Verbinden Sie Ihr Gerät auf Ihren Desktopcomputer, und richten Sie Ihr Android-Gerät für [das Remotedebugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)ein.
1. Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .
1. Wählen Sie **"Überprüfen"** auf der Registerkarte aus, die Sie debuggen möchten, wie in der folgenden Abbildung dargestellt:

   ![Android DevTools](~/assets/images/android-devtools.png)
