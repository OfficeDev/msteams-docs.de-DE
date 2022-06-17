---
title: 1:1-Unterhaltungen mit Bots
description: In diesem Modul lernen Sie das End-to-End-Szenario einer Einzelunterhaltung mit einem Bot in Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 05/20/2019
ms.openlocfilehash: e973e335558a54187a11d5146b52c5774d3cf758
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144327"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Führen Sie eine persönliche (1:1) Unterhaltung mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Mit Microsoft Teams können Benutzer direkte Unterhaltungen mit Bots führen, die auf dem [Microsoft Bot Framework](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) basieren. Benutzer können Bots im Katalog "Apps entdecken" finden und sie zu ihrer Teams-Erfahrung für persönliche Unterhaltungen hinzufügen. Teambesitzer und -benutzer mit den entsprechenden Berechtigungen können Bots auch als Teammitglieder hinzufügen. Weitere Informationen finden Sie unter [Interagieren in einem Teamkanal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md), der sie nicht nur in den Kanälen dieses Teams verfügbar macht, sondern auch für Benutzer des persönlichen Chats.

Der persönliche Chat unterscheidet sich vom Chat in Kanälen darin, dass der Benutzer den Bot nicht @erwähnen muss. Wenn ein Bot in mehreren Kontexten verwendet wird, z. B. in den folgenden Bereichen:
* Privat
* Gruppen-Chat
* Kanal

Sie müssen erkennen, ob sich der Bot in einem Gruppenchat oder -kanal befindet, und Nachrichten ein wenig anders verarbeiten. Weitere Informationen finden Sie unter [Interagieren in einem Teamkanal oder Gruppenchat](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

## <a name="designing-a-great-personal-bot"></a>Entwerfen eines hervorragenden persönlichen Bots

Ein hervorragender Bot in Microsoft Teams hilft Benutzern, die benötigten Informationen im Kontext der Teams-Erfahrung zu erhalten. Persönliche Unterhaltungen mit einem Bot sind ein privater Austausch zwischen einem Bot und seinem Benutzer. Sie sind eine hervorragende Möglichkeit, für den Benutzer spezifische und relevante Informationen im persönlichen Kontext bereitzustellen. Ein Bot im persönlichen Chat ist ein Dialog zwischen Ihrem Dienst und der Person, in dem ein Bot in einem Gruppenchat oder Kanal alles an eine Gruppe von Personen überträgt.

Abhängig von der Erfahrung, die Sie erstellen möchten, muss der Bot möglicherweise in mehreren Bereichen arbeiten – persönlich, Gruppenchat und Team. Die Arbeit zur Unterstützung mehrerer Bereiche ist minimal. In Teams wird nicht erwartet, dass Ihr Bot in allen Bereichen funktioniert, aber Sie sollten sicherstellen, dass Ihr Bot sinnvoll ist und einen Benutzerwert in allen Bereichen bereitstellt, die Sie unterstützen möchten.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Bewährte Methode: Willkommensnachrichten in persönlichen Unterhaltungen

Ihr Bot sollte eine Begrüßungsnachricht in einem persönlichen Chat [proaktiv senden](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), wenn ein Benutzer zum ersten Mal (und nur beim ersten Mal) einen persönlichen Chat mit Ihrem Bot initiiert. Diese Empfehlung gilt nicht für erstmalige Kontakte in einem Kanal.
