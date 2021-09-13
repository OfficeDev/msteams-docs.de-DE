---
title: Entwerfen Ihrer App – Grundlegendes zur App-Struktur
description: Verstehen Sie, was Sie in Microsoft Teams beim Entwerfen Ihrer App anpassen können und was nicht.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: 481ed07682767a303efed50ec06a22cbbb393408
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156800"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Grundlegendes zur Microsoft Teams App-Struktur

Beim Erstellen Ihrer App ist es wichtig zu wissen, was Sie in Microsoft Teams anpassen können und was nicht. Anhand dieser Informationen können Sie besser verstehen, welche Teile der App-Erfahrung Sie steuern.

Die folgenden Drahtframes zeigen Ihnen:

* Die Oberflächen, die Sie in jeder Teams App-Funktion anpassen können (in Rosa umrissen).
* Die Bereiche, die jede Funktion unterstützt.

> [!TIP]
> **Was bedeutet "Bereich"?** Ein Bereich ist ein Bereich in Teams in dem Benutzer Ihre App verwenden können. Apps können einen oder mehrere Bereiche haben, einschließlich persönlich, Kanäle, Chats und Besprechungen.

## <a name="personal-apps"></a>Persönliche Apps

Persönliche Apps bieten eine große Canvas, um Ihre App-Inhalte für einzelne Benutzer zu hosten.

***Unterstützte Bereiche:** Persönlich*

### <a name="mobile"></a>Mobilgeräte

Die Canvas ist eine Webansicht, sodass Sie die Oberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

Die Canvas ist ein iFrame, sodass Sie die Benutzeroberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf dem Desktop anpassen können." border="false":::

## <a name="tabs"></a>Registerkarten

Registerkarten bieten einen großen Canvas zum Hosten der App-Inhalte für eine Gruppe von Benutzern. Sie können Registerkarten in freigegebene Bereiche wie Kanäle, Chats und Besprechungseinladungen einschließen.

***Unterstützte Bereiche:** Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgeräte

Die Canvas ist eine Webansicht, sodass Sie die Oberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf Mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

Die Canvas ist ein iFrame, sodass Sie die Benutzeroberfläche vollständig anpassen können.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf Desktops anpassen können." border="false":::

## <a name="bots"></a>Bots

Bots sind Unterhaltungs-Apps, die mit Teams systemeigenen Messaging-Features integriert sind, sodass die Ui-Arbeit für Sie erledigt wird. Aus Entwurfssicht gibt es weiterhin Möglichkeiten, Persönlichkeit, benutzerdefinierte Funktionen und umfangreiche, umsetzbare Informationen mit unserer NLP-Unterstützung (Natural Language Processing) und der Plattform für adaptive Karten hinzuzufügen.

***Unterstützte Bereiche:** Persönlich, Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf desktop anpassen können." border="false":::

## <a name="messaging-extensions"></a>Messaging-Erweiterungen

Messagingerweiterungen sind Tastenkombinationen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne von der Konversation weg zu navigieren. Aktionsbasierte Messaging-Erweiterungen bieten Ihnen mehr Kontrolle über die Benutzeroberfläche, während Teams viel von dem verarbeitet, was für suchbasierte Messaging-Erweiterungen gerendert wird.

***Unterstützte Bereiche:** Persönlich, Kanäle, Chats, Besprechungen*

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Messaging-Erweiterungen auf mobilen Geräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Messaging-Erweiterungen auf dem Desktop anpassen können." border="false":::

## <a name="meeting-extensions"></a>Besprechungserweiterungen

Besprechungserweiterungen sind Apps zur Verbesserung von Livebesprechungen. Sie können Ihre App-Inhalte in verschiedenen Szenarien hosten, einschließlich vor, während und nach Besprechungen.

***Unterstützte Bereiche:** Besprechungen, Chats*

### <a name="mobile"></a>Mobilgeräte

Die Oberfläche ist eine Webansicht, mit der Sie die Benutzeroberfläche anpassen können. Bedenken Sie jedoch, dass diese Apps in Besprechungen dunkles Design verwenden.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf mobilgeräten anpassen können." border="false":::

### <a name="desktop"></a>Desktop

Die Oberfläche ist ein iFrame, mit dem Sie die Benutzeroberfläche anpassen können. Bedenken Sie jedoch, dass diese Apps während Besprechungen dunkles Design verwenden und schmal sind.

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf dem Desktop anpassen können." border="false":::
