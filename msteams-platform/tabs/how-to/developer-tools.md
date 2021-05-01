---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie zu den DevTools bei Verwendung des Microsoft Teams Desktopclients
localization_priority: Normal
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 70c9a2bab94ceb97e8dcd5cf5cdb98261d037f74
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101828"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Entwicklertools für Microsoft Teams-Registerkarten

Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools: F12 des Browsers unter Windows oder Command-Option-I unter MacOS zu zugreifen. Die DevTools bietet Ihnen Zugriff auf:

1. Anzeigen von Konsolenprotokollen.
1. Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.
1. Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.

> [!NOTE]
> Das Feature ist nur für Desktop- und **Android-Clients** verfügbar, nachdem Developer Preview aktiviert wurde. Weitere Informationen finden Sie unter [Aktivieren der Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).

## <a name="access-devtools-on-the-desktop"></a>Zugreifen auf DevTools auf dem Desktop

Obwohl die Webversion und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede in Bezug auf die Authentifizierung. Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools. Um DevTools im Desktopclient zu verwenden, müssen Sie:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)
1. Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.
1. Öffnen Sie devTools auf eine der folgenden Arten:
    * Auf Windows öffnen Sie DevTools über das Microsoft Teams im Desktoptablett:<br>
  ![Klicken Sie mit der rechten Maustaste, um DevTools zu öffnen](~/assets/images/dev-preview/devtools-right-click.png)
    * Klicken Sie auf MacOS auf das Microsoft Teams im Dock.

Im folgenden Beispiel wird gezeigt, wie DevTools ein Dialogfeld zur Registerkartenkonfiguration öffnet und überprüft:

   ![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-device"></a>Zugreifen auf DevTools von einem Android-Gerät

Sie können die DevTools auch über den Teams aktivieren. Um DevTools zu aktivieren, müssen Sie:

1. Aktivieren Sie [die Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).
1. Verbinden Sie Ihr Gerät auf Ihrem Desktopcomputer an, und richten Sie Ihr Android-Gerät für das [Remotedebubugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .
1. Wählen **Sie überprüfen** unter der Registerkarte aus, die Sie debuggen möchten, wie in der folgenden Abbildung:

   ![Android DevTools](~/assets/images/android-devtools.png)
