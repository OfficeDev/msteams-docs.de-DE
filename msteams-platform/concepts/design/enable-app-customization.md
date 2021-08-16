---
title: Aktivieren der Anpassung Ihrer App
author: heath-hamilton
description: Erfahren Sie, wie Teams Administratoren Ihre App für ihre Organisation anpassen können.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 0af96eebb50aeb650cdd5a1b3bd6a93439fb57b8
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345565"
---
# <a name="enable-your-microsoft-teams-app-to-be-customized"></a>Aktivieren der anpassungsfähigen Microsoft Teams-App

Sie können es Kunden ermöglichen, einige Aspekte Ihrer Microsoft Teams-App im Teams Admin Center anzupassen. Dieses Feature wird nur für Apps unterstützt, die im Teams Store veröffentlicht wurden. Quergeladene Apps und Apps, die für eine Organisation veröffentlicht wurden, können nicht angepasst werden.

> [!IMPORTANT]
> Sideloading-Apps sind derzeit in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und das Verteidigungsministerium (Department of Defense, DOD).

Einige mögliche Beispiele für dieses Feature sind:

* Ändern der Akzentfarbe der App entsprechend der Marke einer Organisation.
* Aktualisieren des App-Namens von *Contoso* auf *Contoso-Agent*, bei dem es sich um den Namen handelt, der Benutzern in der Organisation angezeigt wird. (Hinweis: Benutzern, die einen Connector zu einem Chat oder Kanal hinzufügen, wird weiterhin der ursprüngliche App-Name *Contoso* angezeigt.)

Sie können dieses Feature im [Entwicklerportal für Teams](https://dev.teams.microsoft.com/home)aktivieren. Dadurch `configurableProperties` wird konfiguriert, welche in Versionen vor Version 1.10 des Teams-App-Manifests nicht verfügbar sind.

## <a name="test-your-app"></a>Testen eigener Apps

Sie können dieses Feature während der Entwicklung nicht testen. Die App-Anpassung wird beim Querladen oder Veröffentlichen im App-Katalog einer Organisation nicht unterstützt.

## <a name="user-considerations"></a>Überlegungen zu Benutzern

Stellen Sie als App-Herausgeber die folgenden Informationen für Kunden in Teams Administratoren bereit:
* Fügen Sie einen Hinweis ein, der empfiehlt, Anpassungsänderungen in einem Teams Testmandanten zu testen, bevor Sie Änderungen in der Produktionsumgebung vornehmen. 
* Stellen Sie bewährte Methoden zum Anpassen Ihrer App bereit.

## <a name="see-also"></a>Siehe auch

* [Anpassen von Apps im Teams Admin Center](/MicrosoftTeams/customize-apps)
