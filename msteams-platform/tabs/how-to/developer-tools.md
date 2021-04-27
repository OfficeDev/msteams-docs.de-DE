---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
localization_priority: Normal
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 663368c96f4c75953dde2ce1160314eca0917e2a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020373"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Entwicklertools für Microsoft Teams-Registerkarten

Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 unter Windows oder Command-Option-I unter MacOS. Die DevTools bietet Ihnen Zugriff auf:

1. Anzeigen von Konsolenprotokollen.
1. Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.
1. Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.

> [!NOTE]
> Das Feature ist nur für Desktop- und **Android-Clients** verfügbar, nachdem Developer Preview aktiviert wurde. Weitere Informationen finden Sie unter [Aktivieren der Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).

## <a name="access-devtools-in-the-desktop"></a>Zugreifen auf DevTools im Desktop

Obwohl die Webversion und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede in Bezug auf die Authentifizierung. Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools. Um DevTools im Desktopclient zu verwenden, müssen Sie:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)
1. Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.
1. Öffnen Sie devTools auf eine der folgenden Arten:
    * **Windows**: Wählen Sie das Symbol Teams im Desktoptablett aus.
    * **macOS**: Wählen Sie das Symbol Teams im Dock aus.
 
   Die folgende Abbildung zeigt DevTools, die ein Element in einem Registerkartenkonfigurationsdialogfeld überprüfen:

   ![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-client"></a>Zugreifen auf DevTools über einen Android-Client

Sie können devTools auch über den Teams Android-Client aktivieren. Um DevTools zu aktivieren, müssen Sie:

1. Aktivieren Sie [die Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).
1. Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für das [Remotedebugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)
1. Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .
1. Wählen **Sie überprüfen** unter der Registerkarte aus, die Sie debuggen möchten, wie in der folgenden Abbildung:

   ![Android DevTools](~/assets/images/android-devtools.png)
