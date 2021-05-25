---
title: Entwerfen Ihrer App – Verstehen der App-Struktur
description: Verstehen Sie, was Sie beim Entwerfen Ihrer App in Microsoft Teams anpassen können und nicht.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: bf84ad1d52cf46e9242bf4122dc5e900461ab806
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631310"
---
# <a name="understand-the-microsoft-teams-app-structure"></a>Verstehen der Microsoft Teams-App-Struktur

Beim Erstellen Ihrer App ist es wichtig zu wissen, was Sie in der App Microsoft Teams. Diese Informationen helfen Ihnen, besser zu verstehen, welche Teile der App Sie steuern.

Die folgenden Wireframes zeigen Folgendes:

* Die Oberflächen, die Sie in den einzelnen apps Teams anpassen können (in Blau umrissen).
* Die Bereiche, die jede Funktion unterstützt.

> [!NOTE]
> **Was bedeutet Bereich?** Ein Bereich ist ein Bereich in Teams, in dem Benutzer Ihre App verwenden können. Apps können einen oder mehrere Bereiche haben, einschließlich persönlicher, Kanäle, Chats und Besprechungen.

## <a name="personal-apps"></a>Persönliche Apps

Persönliche Apps bieten eine große Canvas, um Ihre App-Inhalte für einzelne Benutzer zu hosten. Der Zeichenbereich ist ein iframe, damit Sie die Benutzererfahrung vollständig anpassen können.

***Unterstützte Bereiche**: Persönlich*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für persönliche Apps anpassen können." border="false":::

## <a name="tabs"></a>Registerkarten

Registerkarten bieten eine große Canvas zum Hosten von App-Inhalten für eine Gruppe von Benutzern. Sie können Registerkarten in freigegebene Bereiche wie Kanäle, Chats und Besprechungs einladen. Der Zeichenbereich ist ein iframe, damit Sie die Benutzererfahrung vollständig anpassen können.

***Unterstützte Bereiche**: Kanäle, Chats, Besprechungen*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Registerkarten anpassen können." border="false":::

## <a name="bots"></a>Bots

Bots sind Unterhaltungs-Apps, die Teams systemeigenen Messagingfeatures integrieren, sodass die Benutzeroberflächenarbeit für Sie erledigt wird. Aus entwurfsspezifischer Sicht gibt es weiterhin Möglichkeiten, persönlichkeitsspezifische, benutzerdefinierte Funktionen und umfangreiche, umsetzbare Informationen mit unserer Unterstützung für die Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP) und der Adaptive Cards-Plattform hinzuzufügen.

***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Bots anpassen können." border="false":::

## <a name="messaging-extensions"></a>Messaging-Erweiterungen

Messagingerweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln in einer Nachricht, ohne aus der Unterhaltung zu navigieren. Aktionsbasierte Messagingerweiterungen bieten Ihnen mehr Kontrolle über die Besensung, während Teams vieles von dem verarbeitet, was für suchbasierte Messagingerweiterungen gerendert wird.

***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Messagingerweiterungen anpassen können." border="false":::

## <a name="meeting-extensions"></a>Besprechungserweiterungen

Besprechungserweiterungen sind Apps zur Verbesserung von Livebesprechungen. Sie können Ihre App-Inhalte in verschiedenen Szenarien hosten, z. B. vor, während und nach Besprechungen. Die Oberfläche ist ein iframe, mit dem Sie die Oberfläche anpassen können, beachten Sie jedoch, dass diese Apps dunkel und schmal in Besprechungen sind.

***Unterstützte Bereiche**: Besprechungen, Chats*

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Besprechungserweiterungen anpassen können." border="false":::
