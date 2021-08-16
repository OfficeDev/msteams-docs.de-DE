---
title: Änderungen am Registerkartenrand
author: surbhigupta
description: Beschreibt, wie das Entfernen von Registerkartenrändern die App-Erstellung verbessert.
keywords: Registerkarte zum Entfernen des Abstands von Rändern
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 2dc024bea28dbd8f98c658ccfa4a7494e77e19d9
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345600"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die App-Erstellung verbessert. Dies ist eine Erweiterung, die in Microsoft Teams 2021 eingeführt wurde.
Sie können Apps erstellen, die systemeigener für Teams aussehen, indem Sie die Ränder um alle Registerkarten entfernen. Registerkarten mit entfernten Rändern entsprechen Microsoft Teams [UI-Kit-Designs.](~/tabs/design/tabs.md) Die meisten Apps verfügen über ein verbessertes Aussehen ohne Ränder.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp und ohne Ränder" border="false":::

> [!NOTE]
> Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder aufweisen. 

## <a name="guidelines"></a>Anleitungen

Das Entfernen von Registerkartenrändern wirkt sich auf Ihre Teams Apps aus, die Registerkarten verwenden. In solchen Fällen können Sie Ränder um Ihre Registerkartendesigns herum hinzufügen, wo dies erforderlich ist. App-Designs in der Produktion haben einen zusätzlichen Abstandseffekt, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen entfernt, sodass nur der von der App bereitgestellte Abstand übrig bleibt.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es für App-Chrom, z. B. Kopfzeile oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**

Ja, dies ist in Ordnung, und Teams fördert ein solches Design. Es hilft der App, sich systemintern anfühlen zu können.

**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, die linken und rechten Ränder unserer Designs zu berühren?**

Nein, Sie müssen Ihren eigenen Abstand oder Ränder links und rechts von allen App-Inhalten bereitstellen, um sicherzustellen, dass die Ränder Ihrer Benutzeroberfläche nicht berührt werden. Sie können bei Bedarf auch Ränder oben auf der Registerkarte hinzufügen.

**Wie groß sind die Registerkartenränder, die zuvor angewendet Teams?**

* Links und rechts: 20 Pixel
* Top: 16px
* Unten: 0px

> [!IMPORTANT]
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-)Chat-Registerkarten, Besprechungsregisterkarten und Kanalregisterkarten.
> * Die Änderung des Registerkartenrands gilt für alle Registerkarten. Es gibt keine Möglichkeit, die Änderung abzumelden oder abzuwählen. 
> * Die Änderung von Registerkartenrändern kann sich auf Registerkarten auswirken, die auf Microsoft Teams angewiesen sind, um Ränder zu ihrer Benutzeroberfläche bereitzustellen.

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
