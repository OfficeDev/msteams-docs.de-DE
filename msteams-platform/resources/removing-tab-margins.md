---
title: Änderungen am Registerkartenrand
author: surbhigupta
description: Erfahren Sie, wie Sie Ränder um Registerkarten in Microsoft Teams mit dem UI-Kit entfernen. Kennen Sie den zusätzlichen Abstandseffekt, die Randgröße für links, rechts, oben und unten.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 715c6b735323e442490de8634384054be565e7a8
ms.sourcegitcommit: 87bba925d005eb331d876a0b9b75154f8100e911
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450443"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams Ihre App-Erstellung verbessert. Dies ist eine Verbesserung, die 2021 in Teams eingeführt wurde.
Sie können Apps erstellen, die für Teams nativer aussehen, indem Sie die Ränder um alle Registerkarten entfernen. Registerkarten mit entfernten Seitenrändern entsprechen den [Ui Kit-Designs](~/tabs/design/tabs.md) von Microsoft Teams. Die meisten Apps bieten ein verbessertes Aussehen ohne Ränder.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp-Witz und ohne Ränder":::

> [!NOTE]
> Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder aufweisen.

## <a name="guidelines"></a>Anleitungen

Das Entfernen von Tabrändern wirkt sich auf Ihre Teams-Apps aus, die Registerkarten verwenden. In solchen Fällen können Sie Ränder um Ihre Registerkartendesigns herum hinzufügen, wo dies erforderlich ist. App-Designs in der Produktion haben einen zusätzlichen Abstandseffekt, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und verschwindet in einigen Wochen, sodass nur der von der App bereitgestellte Abstand übrig bleibt.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es für App-Chrome, z. B. Kopfzeile oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**

Ja, das ist in Ordnung und Teams fördert ein solches Design. Es hilft der App, sich nativ zu fühlen.

**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, die linken und rechten Ränder unserer Designs zu berühren?**

Nein, Sie müssen einen eigenen Abstand oder eigene Ränder links und rechts neben allen App-Inhalten bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden. Sie können bei Bedarf auch Ränder oben auf der Registerkarte hinzufügen.

**Wie groß sind die Registerkartenränder, die Zuvor von Teams angewendet wurden?**

* Links und rechts: 20 Pixel
* Oben: 16 Pixel
* Unten: 0 Pixel

> [!IMPORTANT]
>
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, Chatregisterkarten (Gruppen), Besprechungsregisterkarten und Kanalregisterkarten.
> * Die Änderung zum Entfernen des Tabstopprands gilt für alle Registerkarten. Es gibt keine Möglichkeit, sich an der Änderung zu beteiligen oder abzumelden.
> * Die Änderung von Registerkartenrändern kann sich auf Registerkarten auswirken, die darauf angewiesen sind, dass Microsoft Teams Ränder rund um die Benutzeroberfläche bereitstellt.

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
