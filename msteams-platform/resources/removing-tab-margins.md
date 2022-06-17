---
title: Änderungen am Registerkartenrand
author: surbhigupta
description: In diesem Modul erfahren Sie, wie das Entfernen von Registerkartenrändern die App-Erstellung verbessert.
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 178c8616a00bc64f10a39815db16d11dcea6eb40
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143319"
---
# <a name="tab-margin-changes"></a>Änderungen am Registerkartenrand

In diesem Dokument wird beschrieben, wie das Entfernen von Rändern um alle Registerkarten in Microsoft Teams die App-Erstellung verbessert. Dies ist eine Verbesserung, die 2021 in Microsoft Teams eingeführt wurde.
Sie können Apps erstellen, die für Teams nativer aussehen, indem Sie die Ränder um alle Registerkarten entfernen. Registerkarten mit entfernten Rändern werden an Microsoft Teams [UI Kit-Designs](~/tabs/design/tabs.md) ausgerichtet. Die meisten Apps bieten ein verbessertes Aussehen ohne Ränder.

:::image type="content" source="../assets/images/tabs/remove-margins-tabs.png" alt-text="Tabstopp-Witz und ohne Ränder" border="false":::

> [!NOTE]
> Dieses Feature gilt nicht für mobile Clients, da die in den mobilen Clients angezeigten Registerkarten keine Ränder aufweisen.

## <a name="guidelines"></a>Anleitungen

Das Entfernen von Tabrändern wirkt sich auf Ihre Teams Apps aus, die Registerkarten verwenden. In solchen Fällen können Sie Ränder um Ihre Registerkartendesigns herum hinzufügen, wo dies erforderlich ist. App-Designs in der Produktion haben einen zusätzlichen Abstandseffekt, d. h. Ränder, die von Teams bereitgestellt werden, und Ränder, die von der Registerkarte bereitgestellt werden. Der zusätzliche Abstand ist jedoch nur temporär und verschwindet in einigen Wochen, sodass nur der von der App bereitgestellte Abstand übrig bleibt.

## <a name="faq"></a>Häufig gestellte Fragen

**Ist es für App-Chrome, z. B. Kopfzeile oder Taskleiste, in Ordnung, die Ränder unserer Designs zu berühren?**

Ja, das ist in Ordnung und Teams fördert ein solches Design. Es hilft der App, sich nativ zu fühlen.

**Ist es für App-Inhalte wie Text, Logos und Bilder in Ordnung, die linken und rechten Ränder unserer Designs zu berühren?**

Nein, Sie müssen einen eigenen Abstand oder eigene Ränder links und rechts neben allen App-Inhalten bereitstellen, um sicherzustellen, dass die Ränder der Benutzeroberfläche nicht berührt werden. Sie können bei Bedarf auch Ränder oben auf der Registerkarte hinzufügen.

**Wie groß sind die Registerkartenränder, die zuvor angewendet Teams?**

* Links und rechts: 20 px
* Oben: 16 px
* Unten: 0 px

> [!IMPORTANT]
>
> * Alle Registerkarten haben ihre Ränder entfernt: persönliche Registerkarten, Chatregisterkarten (Gruppen), Besprechungsregisterkarten und Kanalregisterkarten.
> * Die Änderung zum Entfernen des Tabstopprands gilt für alle Registerkarten. Es gibt keine Möglichkeit, sich an der Änderung zu beteiligen oder abzumelden.
> * Die Änderung von Registerkartenrändern kann sich auf Registerkarten auswirken, die darauf angewiesen sind, Microsoft Teams Ränder zur Verfügung zu stellen, die ihre Benutzeroberfläche umgeben.

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
