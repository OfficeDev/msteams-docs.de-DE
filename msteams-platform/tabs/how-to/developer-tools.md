---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: In diesem Modul erfahren Sie, wie Sie bei Verwendung des Microsoft Teams Desktopclients und debuggen zu den DevTools gelangen.
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: de502588d6c1d4e11d7f68e2fff1c7e591d2918d
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143011"
---
# <a name="devtools-for-microsoft-teams-tabs"></a>Entwicklertools für Microsoft Teams-Registerkarten

Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf die DevTools des Browsers zuzugreifen: F12 unter Windows oder Command-Option-I unter MacOS. Mit den DevTools haben Sie Zugriff auf:

1. Konsolenprotokolle anzeigen.
1. Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.
1. Fügen Sie Haltepunkte zu Ihrem JavaScript-Code hinzu und führen Sie ein interaktives Debugging durch.

> [!NOTE]
> Die Funktion ist nur für Desktop- und **Android-Clients verfügbar, nachdem die Entwicklervorschau** aktiviert wurde. Weitere Informationen finden Sie unter [Wie aktiviere ich die Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).

## <a name="access-devtools-on-the-desktop"></a>Greifen Sie auf dem Desktop auf DevTools zu

Während die Webversion und die Desktopversion von Teams fast identisch sind, gibt es einige Unterschiede in Bezug auf die Authentifizierung. Manchmal ist die Verwendung der DevTools die einzige Möglichkeit, herauszufinden, was vor sich geht. Um DevTools im Desktopclient zu verwenden, müssen Sie:

1. Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben](~/resources/dev-preview/developer-preview-intro.md).
1. Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools untersuchen können.
1. Öffnen Sie die DevTools auf eine der folgenden Arten:
    * Unter Windows öffnen Sie DevTools über das Microsoft Teams-Symbol in der Desktopleiste.

      :::image type="content" source="../../assets/images/dev-preview/devtools-right-click.png" alt-text="developer-tool-windows":::

    * Wählen Sie unter MacOS das Microsoft Teams-Symbol im Dock aus.

      :::image type="content" source="../../assets/images/dev-preview/mac-os-developer-tools.PNG" alt-text="mac-os-dev-tools":::

Das folgende Beispiel zeigt, wie DevTools geöffnet und ein Registerkartenkonfigurationsdialogfeld untersucht wird:

   [![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)](~/assets/images/dev-preview/tab-and-devtools.png#lightbox)

## <a name="access-devtools-from-an-android-device"></a>Greifen Sie von einem Android-Gerät aus auf DevTools zu

Sie können die DevTools auch über den Teams-Android-Client aktivieren. Um DevTools zu aktivieren, müssen Sie:

1. Aktivieren Sie die [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).
1. Verbinden Sie Ihr Gerät mit Ihrem Desktop-Computer und richten Sie Ihr Android-Gerät für [das Remote-Debugging ein](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).
1. Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices`.
1. Wählen **Sie unter der** Registerkarte, die Sie debuggen möchten, Inspizieren aus, wie in der folgenden Abbildung:

   ![Android DevTools](~/assets/images/android-devtools.png)
