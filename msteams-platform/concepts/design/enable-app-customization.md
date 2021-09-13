---
title: Aktivieren der Anpassung Ihrer App
author: heath-hamilton
description: Erfahren Sie, wie Teams Administratoren Ihre App für ihre Organisation anpassen können.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 193b4baeee16badb1dcb26139831d3e298de9a5c
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156208"
---
# <a name="enable-your-microsoft-teams-app-to-be-customized"></a>Aktivieren der anpassungsfähigen Microsoft Teams-App

Sie können Es Kunden ermöglichen, einige Aspekte Ihrer Microsoft Teams-App im Teams Admin Center anzupassen. Dieses Feature wird nur für Apps unterstützt, die im Teams Store veröffentlicht wurden. Quergeladene Apps und Apps, die für eine Organisation veröffentlicht wurden, können nicht angepasst werden.

Einige mögliche Beispiele für dieses Feature sind:

* Ändern der Akzentfarbe der App entsprechend der Marke einer Organisation.
* Aktualisieren des App-Namens von *Contoso* auf *Contoso-Agent*, bei dem es sich um den Namen handelt, der Benutzern in der Organisation angezeigt wird. (Hinweis: Benutzern, die einen Connector zu einem Chat oder Kanal hinzufügen, wird weiterhin der ursprüngliche App-Name *Contoso* angezeigt.)

Sie können dieses Feature im [Entwicklerportal für Teams](https://dev.teams.microsoft.com/home)aktivieren. Dadurch `configurableProperties` wird konfiguriert, was in Versionen vor 1.10 des Teams-App-Manifests nicht verfügbar ist.

## <a name="test-your-app"></a>Testen eigener Apps

Sie können dieses Feature während der Entwicklung nicht testen. Die App-Anpassung wird beim Querladen oder Veröffentlichen im App-Katalog einer Organisation nicht unterstützt.

## <a name="user-considerations"></a>Überlegungen zu Benutzern

Bereitstellen von Richtlinien für Kunden (insbesondere Teams Administratoren), die Ihre App anpassen möchten. Weitere Informationen finden Sie unter [Anpassen von Apps in Teams.](/MicrosoftTeams/customize-apps)

## <a name="see-also"></a>Siehe auch

* [Anpassen von Apps im Teams Admin Center](/MicrosoftTeams/customize-apps)
