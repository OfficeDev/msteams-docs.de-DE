---
title: Entwerfen Der App – Grundlegendes zur App-Struktur
description: Verstehen Sie, was Sie beim Entwerfen Ihrer App in Microsoft Teams anpassen können und was nicht.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
keywords: Drahtmodellkanal-Chat-Besprechungsnachrichtenerweiterungen mobiler Desktop
ms.openlocfilehash: 8353fa74dce12642e5ca96c85c34dc06fc0da203
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103285"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Grundlegendes zur Struktur von Microsoft Teams-Apps

Beim Erstellen Ihrer App ist es wichtig zu wissen, was Sie in Microsoft Teams anpassen können und was nicht. Anhand dieser Informationen können Sie besser verstehen, welche Teile der App-Oberfläche Sie steuern.

Die folgenden Drahtmodelle zeigen Ihnen:

* Die Oberflächen, die Sie in den einzelnen Teams App-Funktionen anpassen können (rosa dargestellt).
* Die Bereiche, die von den einzelnen Funktionen unterstützt werden.

> [!TIP]
> **Was bedeutet Bereich?** Ein Bereich ist ein Bereich in Teams, in dem Benutzer Ihre App verwenden können. Apps können einen oder mehrere Bereiche haben, darunter Privat, Kanäle, Chats und Besprechungen.

## <a name="personal-apps"></a>Persönliche Apps

Persönliche Apps bieten einen großen Zeichenbereich, um Ihre App-Inhalte für einzelne Benutzer zu hosten.

***Unterstützte Bereiche**: Personal*

### <a name="mobile"></a>Mobilgeräte

Die Canvas ist eine Webansicht, sodass Sie die Oberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

Die Canvas ist ein iFrame, sodass Sie die Benutzeroberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf dem Desktop anpassen können." border="false":::

## <a name="tabs"></a>Registerkarten

Registerkarten bieten einen großen Zeichenbereich, um Ihre App-Inhalte für eine Gruppe von Benutzern zu hosten. Sie können Registerkarten in freigegebene Räume wie Kanäle, Chats und Besprechungseinladungen einschließen.

***Unterstützte Bereiche**: Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgeräte

Die Canvas ist eine Webansicht, sodass Sie die Oberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

Die Canvas ist ein iFrame, sodass Sie die Benutzeroberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf dem Desktop anpassen können." border="false":::

## <a name="bots"></a>Bots

Bots sind Unterhaltungs-Apps, die in Teams native Messaging-Features integriert sind, sodass die Ui-Arbeit für Sie erledigt wird. Aus Designsicht gibt es weiterhin Möglichkeiten, Persönlichkeit, benutzerdefinierte Funktionen und umfangreiche, umsetzbare Informationen mit unserer Unterstützung für die Verarbeitung natürlicher Sprache (NLP) und der Plattform für adaptive Karten hinzuzufügen.

***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf dem Desktop anpassen können." border="false":::

## <a name="message-extensions"></a>Nachrichtenerweiterungen

Nachrichtenerweiterungen sind Tastenkombinationen zum Einfügen von App-Inhalten oder zum Ausführen einer Nachricht, ohne die Unterhaltung zu beenden. Aktionsbasierte Nachrichtenerweiterungen bieten Ihnen mehr Kontrolle über die Benutzeroberfläche, während Teams vieles von dem verarbeitet, was für suchbasierte Nachrichtenerweiterungen gerendert wird.

***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Nachrichtenerweiterungen auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Nachrichtenerweiterungen auf dem Desktop anpassen können." border="false":::

## <a name="meeting-extensions"></a>Besprechungserweiterungen

Besprechungserweiterungen sind Apps zur Verbesserung von Livebesprechungen. Sie können Ihre App-Inhalte in mehreren Szenarien hosten, einschließlich vor, während und nach Besprechungen.

***Unterstützte Bereiche**: Besprechungen, Chats*

### <a name="mobile"></a>Mobilgeräte

Die Oberfläche ist eine Webansicht, mit der Sie die Benutzeroberfläche anpassen können, aber denken Sie daran, dass diese Apps während Besprechungen ein dunkles Design verwenden.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

Die Oberfläche ist ein iFrame, mit dem Sie die Benutzeroberfläche anpassen können, aber denken Sie daran, dass diese Apps während Besprechungen ein dunkles Design verwenden und schmal sind.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf dem Desktop anpassen können." border="false":::
