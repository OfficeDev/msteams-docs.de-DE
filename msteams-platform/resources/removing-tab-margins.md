---
title: Entfernen von Registerkartenrändern in Microsoft Teams
author: laujan
description: Beschreibt, wie das Entfernen von Registerkartenrändern die Erfahrung von Entwicklern verbessert.
keywords: Tabulatoren entfernen Ränderabstand
ms.topic: reference
ms.author: lomeybur
ms.openlocfilehash: f26701b2c432ba35ce6f069eabd3b401aae8e369
ms.sourcegitcommit: 1ce74ed167bb81bf09f7f6f8d518093efafb549e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "50827928"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die Erfahrung des Entwicklers beim Erstellen von Apps verbessert. Dies ist eine Verbesserung, die in Microsoft Teams in 2021 eingeführt wurde.
Wenn Sie die Ränder um alle Registerkarten entfernen, können Entwickler Apps erstellen, die für Teams systemeigener aussehen. Dies entspricht auch unseren [Ui Kit-Designs.](~/tabs/design/tabs.md) Die meisten Apps sehen ohne die Ränder, die ihre Erfahrungen umgeben, bereits besser aus. Einige Registerkarten sind jedoch visuell von dieser Änderung betroffen, und Entwickler müssen die erforderlichen Änderungen vornehmen.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp-Witz und ohne Ränder" border="false":::

## <a name="timelines"></a>Zeitpläne

* 5. März 2021 – Ränder in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).
* 15. Juni 2021 – Ränder werden in der Produktion entfernt.

## <a name="guidelines"></a>Anleitungen

Microsoft Teams-Apps, die Registerkarten verwenden, sind von dieser Änderung betroffen. Entwickler müssen zu [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) wechseln, um zu bestimmen, wie ihre Registerkarten betroffen sind, und die erforderlichen Änderungen vornehmen.

Registerkartenentwickler dürfen sich nicht darauf verlassen, dass Teams Ränder für ihre Registerkarten zur Verfügung stellt. Entwickler werden ermutigt, Ränder um ihre Registerkartendesigns hinzuzufügen, wo dies erforderlich ist. App-Designs in der Produktion können wie zusätzliche Abstände aussehen, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und wird in ein paar Wochen weg sein, und nur der von der App bereitgestellte Abstand bleibt erhalten.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es für App Chrome, z. B. Kopf- oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**

Ja, dies ist in Ordnung und wird ermutigt. Dies hilft der App, sich systemeigener zu fühlen.

**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, den linken und rechten Rand unserer Designs zu berühren?**

Nein, Sie müssen links und rechts von allen App-Inhalten einen eigenen Abstand oder Ränder bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden. Sie können bei Bedarf auch Ränder oben auf Ihrer Registerkarte hinzufügen.

**Wie groß sind die Ränder, die Teams zuvor angewendet hat?**

* Links und rechts: 20px
* Top: 16px
* Unten: 0px

> [!IMPORTANT]
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, (Gruppen-) Chatregisterkarten, Besprechungsregisterkarten und Kanalregisterkarten.
> * Es gibt keine Möglichkeit, sich für diese Änderung zu entscheiden oder abmelden. Sie gilt für alle Registerkarten.
> * Diese Änderung kann sich auf Registerkarten auswirken, die auf Microsoft Teams angewiesen sind, um Ränder für die Benutzeroberfläche zur Verfügung zu stellen.
