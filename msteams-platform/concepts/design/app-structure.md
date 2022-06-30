---
title: Entwerfen Der App – Grundlegendes zur App-Struktur
description: In diesem Modul erfahren Sie, was Sie in Microsoft Teams beim Entwerfen Ihrer App-Struktur anpassen können und was nicht.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: 6a409accc5f55aa0a9c245aa061efde5b67d81f3
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558758"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Grundlegendes zur Struktur von Microsoft Teams-Apps

Beim Erstellen Ihrer App ist es wichtig zu wissen, was Sie in Microsoft Teams anpassen können und was nicht. Anhand dieser Informationen können Sie besser verstehen, welche Teile der App-Oberfläche Sie steuern.

Die folgenden Drahtmodelle zeigen Ihnen:

* Die Oberflächen, die Sie in den einzelnen Teams-App-Funktionen anpassen können (rosa dargestellt).
* Die Bereiche, die von den einzelnen Funktionen unterstützt werden.

> [!TIP]
> **Was bedeutet Bereich?** Ein Bereich ist ein Bereich in Teams, in dem Benutzer Ihre App verwenden können. Apps können einen oder mehrere Bereiche haben, darunter Privat, Kanäle, Chats und Besprechungen.

## <a name="personal-apps"></a>Persönliche Apps

Persönliche Apps bieten einen großen Zeichenbereich, um Ihre App-Inhalte für einzelne Benutzer zu hosten.

***Unterstützte Bereiche**: Personal*

### <a name="mobile"></a>Mobilgerät

Die Canvas ist eine Webansicht, sodass Sie die Oberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf mobilgeräten anpassen können.":::

### <a name="desktop"></a>Desktop

Die Canvas ist ein iFrame, sodass Sie die Benutzeroberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf dem Desktop anpassen können.":::

## <a name="tabs"></a>Registerkarten

Registerkarten bieten einen großen Zeichenbereich, um Ihre App-Inhalte für eine Gruppe von Benutzern zu hosten. Sie können Registerkarten in freigegebene Räume wie Kanäle, Chats und Besprechungseinladungen einschließen.

***Unterstützte Bereiche**: Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgerät

Die Canvas ist eine Webansicht, sodass Sie die Oberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf Mobilgeräten anpassen können.":::

### <a name="desktop"></a>Desktop

Die Canvas ist ein iFrame, sodass Sie die Benutzeroberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf dem Desktop anpassen können.":::

## <a name="bots"></a>Bots

Bots sind Unterhaltungs-Apps, die in systemeigene Messaging-Features von Teams integriert sind, sodass die Ui-Arbeit für Sie erledigt wird. Aus Designsicht gibt es weiterhin Möglichkeiten, Persönlichkeit, benutzerdefinierte Funktionen und umfangreiche, umsetzbare Informationen mit unserer Unterstützung für die Verarbeitung natürlicher Sprache (NLP) und der Plattform für adaptive Karten hinzuzufügen.

***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf mobilgeräten anpassen können.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf dem Desktop anpassen können.":::

## <a name="message-extensions"></a>Nachrichtenerweiterungen

Nachrichtenerweiterungen sind Abkürzungen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne die Konversation verlassen zu müssen. Aktionsbasierte Nachrichtenerweiterungen geben Ihnen mehr Kontrolle über die Erfahrung, während Teams einen Großteil der Rendervorgänge für suchbasierte Nachrichtenerweiterungen übernimmt.

***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Nachrichtenerweiterungen auf mobilgeräten anpassen können.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Nachrichtenerweiterungen auf dem Desktop anpassen können.":::

## <a name="meeting-extensions"></a>Besprechungserweiterungen

Besprechungserweiterungen sind Apps zur Verbesserung von Livebesprechungen. Sie können Ihre App-Inhalte in mehreren Szenarien hosten, einschließlich vor, während und nach Besprechungen.

***Unterstützte Bereiche**: Besprechungen, Chats*

### <a name="mobile"></a>Mobilgerät

Die Oberfläche ist eine Webansicht, mit der Sie die Benutzeroberfläche anpassen können, aber denken Sie daran, dass diese Apps während Besprechungen ein dunkles Design verwenden.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf mobilgeräten anpassen können.":::

### <a name="desktop"></a>Desktop

Die Oberfläche ist ein iFrame, mit dem Sie die Benutzeroberfläche anpassen können, aber denken Sie daran, dass diese Apps während Besprechungen ein dunkles Design verwenden und schmal sind.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf dem Desktop anpassen können.":::
