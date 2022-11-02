---
title: Änderungen am Registerkartenrand
author: surbhigupta
description: Erfahren Sie, wie Sie Ränder um Registerkarten in Microsoft Teams mit dem UI-Kit entfernen. Kennen Sie zusätzlichen Auffüllungseffekt, Randgröße für links, rechts, oben und unten.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: ba203cd89904acde77e1d9971175afc19c47d24d
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820073"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams Ihre App-Erstellungserfahrung verbessert. Dies ist eine Erweiterung, die 2021 in Teams eingeführt wurde.
Sie können Apps erstellen, die in Teams nativer aussehen, indem Sie die Ränder um alle Registerkarten entfernen. Registerkarten mit entfernten Rändern entsprechen den Designs des [Microsoft Teams-Ui-Kits](~/tabs/design/tabs.md). Die meisten Apps bieten ein verbessertes Aussehen ohne Ränder.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp mit und ohne Ränder":::

> [!NOTE]
> Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Seitenränder aufweisen.

## <a name="guidelines"></a>Anleitungen

Das Entfernen von Tabstopprändern wirkt sich auf Ihre Teams-Apps aus, die Registerkarten verwenden. In solchen Fällen können Sie Ränder um Ihre Registerkartendesigns hinzufügen, wo dies erforderlich ist. App-Designs in der Produktion haben einen zusätzlichen Auffüllungseffekt, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Die zusätzliche Auffüllung ist jedoch nur vorübergehend und wird in einigen Wochen entfernt, sodass nur der von der App bereitgestellte Abstand bleibt.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es in Ordnung, wenn App-Chrom wie Kopfzeile oder Taskleiste die Ränder unserer Designs berührt?**

Ja, das ist in Ordnung, und Teams fördert ein solches Design. Es hilft der App, sich nativ zu fühlen.

**Ist es in Ordnung, dass App-Inhalte wie Text, Logos und Bilder den linken und rechten Rand unserer Designs berühren?**

Nein, Sie müssen links und rechts neben allen App-Inhalten eigene Abstände oder Ränder bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden. Sie können bei Bedarf auch Ränder oben auf der Registerkarte hinzufügen.

**Wie groß ist die Größe der Registerkartenränder, die Teams zuvor angewendet hat?**

* Links und rechts: 20 Pixel
* Oben: 16 Pixel
* Unten: 0 Pixel

> [!IMPORTANT]
>
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-)Chatregisterkarten, Besprechungsregisterkarten und Kanalregister.
> * Die Änderung zum Entfernen des Tabstopprands gilt für alle Registerkarten. Es gibt keine Möglichkeit, die Änderung zu aktivieren oder zu deaktivieren.
> * Die Änderung von Registerkartenrändern kann sich auf Registerkarten auswirken, die microsoft Teams verwenden, um Ränder rund um die Benutzeroberfläche bereitzustellen.

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](../tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanalregisterkarte oder Gruppenregisterkarte](../tabs/how-to/create-channel-group-tab.md)
