---
title: Entfernen von Registerkartenrändern in Microsoft Teams
author: surbhigupta
description: Beschreibt, wie das Entfernen von Registerkartenrändern die Erfahrung von Entwicklern verbessert.
keywords: Registerkarte zum Entfernen des Abstands von Rändern
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 5fab0e0145288718adb7eb96f8f103f75527ec58
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179741"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die Erfahrung des Entwicklers beim Erstellen von Apps verbessert. Dies ist eine Erweiterung, die in Microsoft Teams 2021 eingeführt wurde.
Wenn Sie die Ränder um alle Registerkarten entfernen, können Entwickler Apps erstellen, die systemeigener für Teams aussehen. Dies entspricht auch unseren [Ui-Kit-Designs.](~/tabs/design/tabs.md) Die meisten Apps sehen bereits besser aus, ohne dass die Ränder ihrer Umgebungen vorhanden sind. Einige Registerkarten sind jedoch visuell von dieser Änderung betroffen, und Entwickler müssen die erforderlichen Änderungen vornehmen.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp und ohne Ränder" border="false":::

> [!NOTE]
> Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder aufweisen. 

## <a name="timelines"></a>Zeitpläne

* 5. März 2021 – In [public Developer Preview](~/resources/dev-preview/developer-preview-intro.md)entfernte Ränder.
* 15. Juni 2021 – Ränder werden in der Produktion entfernt.

## <a name="guidelines"></a>Richtlinien

Microsoft Teams Apps, die Registerkarten verwenden, sind von dieser Änderung betroffen. Entwickler müssen zur [Öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) wechseln, um zu bestimmen, wie ihre Registerkarten betroffen sind, und die erforderlichen Änderungen vornehmen.

Registerkartenentwickler dürfen sich nicht auf Teams verlassen, um Ränder um ihre Registerkarten herum bereitzustellen. Entwickler sollten Ränder um ihre Registerkartendesigns herum hinzufügen, wo dies erforderlich ist. App-Designs in der Produktion können so aussehen, als ob zusätzliche Abstände vorhanden sind, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen entfernt, sodass nur der von der App bereitgestellte Abstand übrig bleibt.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es für App-Chrome, z. B. Kopfzeile oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**

Ja, dies ist in Ordnung und wird unterstützt. Dies hilft der App, sich systemintern anfühlen zu können.

**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, die linken und rechten Ränder unserer Designs zu berühren?**

Nein, Sie müssen ihren eigenen Abstand oder Ränder links und rechts von allen App-Inhalten bereitstellen, um sicherzustellen, dass sie nicht die Ränder Der Benutzeroberfläche berühren. Sie können bei Bedarf auch Ränder oben auf der Registerkarte hinzufügen.

**Wie groß sind die Ränder, die zuvor angewendet Teams?**

* Links und rechts: 20 Pixel
* Top: 16px
* Unten: 0px

> [!IMPORTANT]
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-)Chat-Registerkarten, Besprechungsregisterkarten und Kanalregisterkarten.
> * Es gibt keine Möglichkeit, diese Änderung abzumelden oder abzuwählen. Sie gilt für alle Registerkarten.
> * Diese Änderung kann sich auf Registerkarten auswirken, die auf Microsoft Teams angewiesen sind, um Ränder zu ihrer Benutzeroberfläche bereitzustellen.

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
