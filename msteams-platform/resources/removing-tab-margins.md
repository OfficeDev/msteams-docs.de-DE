---
title: Entfernen von Registerkartenrändern in Microsoft Teams
author: laujan
description: Beschreibt, wie das Entfernen von Registerkartenrändern die Erfahrung von Entwicklern verbessert.
keywords: Tabulatoren entfernen Ränderabstand
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 78d97dca73e7fce2bf4b911f5ea4588525667378
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019713"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die Erfahrung des Entwicklers beim Erstellen von Apps verbessert. Dies ist eine Verbesserung, die in Microsoft Teams 2021 eingeführt wurde.
Wenn Sie die Ränder um alle Registerkarten entfernen, können Entwickler Apps erstellen, die nativ für Teams. Dies entspricht auch unseren [Ui Kit-Designs.](~/tabs/design/tabs.md) Die meisten Apps sehen ohne die Ränder, die ihre Erfahrungen umgeben, bereits besser aus. Einige Registerkarten sind jedoch visuell von dieser Änderung betroffen, und Entwickler müssen die erforderlichen Änderungen vornehmen.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp-Witz und ohne Ränder" border="false":::

> [!NOTE]
> Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder haben. 

## <a name="timelines"></a>Zeitpläne

* 5. März 2021 – Ränder in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).
* 15. Juni 2021 – Ränder werden in der Produktion entfernt.

## <a name="guidelines"></a>Richtlinien

Microsoft Teams Apps, die Registerkarten verwenden, sind von dieser Änderung betroffen. Entwickler müssen zu [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) wechseln, um zu bestimmen, wie ihre Registerkarten betroffen sind, und die erforderlichen Änderungen vornehmen.

Registerkartenentwickler dürfen sich nicht auf Teams verlassen, um Ränder für ihre Registerkarten zur Verfügung zu stellen. Entwickler werden ermutigt, Ränder um ihre Registerkartendesigns hinzuzufügen, wo dies erforderlich ist. App-Designs in der Produktion können so aussehen, als ob zusätzliche Abstände vorhanden sind, d. h. Ränder, die von Teams und Rändern bereitgestellt werden, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen weg sein, und nur der von der App bereitgestellte Abstand bleibt erhalten.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es für App Chrome, z. B. Kopf- oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**

Ja, dies ist in Ordnung und wird ermutigt. Dies hilft der App, sich systemeigener zu fühlen.

**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, den linken und rechten Rand unserer Designs zu berühren?**

Nein, Sie müssen links und rechts von allen App-Inhalten einen eigenen Abstand oder Ränder bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden. Sie können bei Bedarf auch Ränder oben auf Ihrer Registerkarte hinzufügen.

**Wie groß sind die Ränder, die Teams angewendet wurden?**

* Links und rechts: 20px
* Top: 16px
* Unten: 0px

> [!IMPORTANT]
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-) Chatregisterkarten, Besprechungsregisterkarten und Kanalregisterkarten.
> * Es gibt keine Möglichkeit, sich für diese Änderung zu entscheiden oder abmelden. Sie gilt für alle Registerkarten.
> * Diese Änderung kann sich auf Registerkarten auswirken, die Microsoft Teams, um Ränder für ihre Benutzeroberfläche zur Verfügung zu stellen.
