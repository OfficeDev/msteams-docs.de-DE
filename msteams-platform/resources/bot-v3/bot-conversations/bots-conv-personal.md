---
title: 1:1-Unterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario einer 1:1-Unterhaltung mit einem Bot in Microsoft Teams
keywords: Teams-Szenarien 1on1 1to1 Unterhaltungs-Bot
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 05/20/2019
ms.openlocfilehash: 2fd76b8bc5fa4cd260b70e15b92bef2dec2de683
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156111"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Persönliche (1:1)-Unterhaltung mit einem Microsoft Teams Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht Benutzern die Teilnahme an direkten Unterhaltungen mit Bots, die auf dem [Microsoft Bot Framework](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true)basieren. Benutzer finden Bots im Katalog "Apps entdecken" und fügen sie ihrer Teams Für persönliche Unterhaltungen hinzu. Teambesitzer und Benutzer mit den entsprechenden Berechtigungen können auch Bots als Teammitglieder hinzufügen. Weitere Informationen finden Sie unter ["Interagieren in einem Teamkanal",](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)der sie nicht nur in den Kanälen dieses Teams verfügbar macht, sondern auch für persönliche Chats für alle diese Benutzer.

Der persönliche Chat unterscheidet sich von Chats in Kanälen dadurch, dass der Benutzer den Bot nicht @mention muss. Wenn ein Bot in mehreren Kontexten verwendet wird, z. B. persönlich, GroupChat oder Kanal, müssen Sie erkennen, ob sich der Bot in einem Gruppenchat oder Kanal befindet, und Nachrichten etwas anders verarbeiten. Weitere Informationen finden Sie unter [Interagieren in einem Teamkanal oder Gruppenchat.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)

## <a name="designing-a-great-personal-bot"></a>Entwerfen eines großartigen persönlichen Bots

Ein hervorragender Bot in Microsoft Teams hilft Benutzern, die benötigten Informationen im Kontext der Teams zu erhalten. Persönliche Unterhaltungen mit einem Bot sind privater Austausch zwischen einem Bot und seinem Benutzer; Sie sind eine hervorragende Möglichkeit, informationen bereitzustellen, die für diesen Benutzer im persönlichen Kontext spezifisch und relevant sind. Ein Bot im persönlichen Chat ist wirklich ein Dialog zwischen Ihrem Dienst und der Person, in dem ein Bot in einem Gruppenchat oder Kanal alles an eine Gruppe von Personen überträgt.

Abhängig von der Oberfläche, die Sie erstellen möchten, muss der Bot möglicherweise in mehreren Bereichen arbeiten – persönlich, Gruppenchat und Team. Die Unterstützung mehrerer Bereiche ist minimal. Es wird nicht erwartet, dass Teams, dass Ihr Bot in allen Bereichen funktioniert. Sie sollten jedoch sicherstellen, dass Ihr Bot sinnvoll ist und einen Benutzerwert in allen Bereichen bereitstellt, die Sie unterstützen möchten.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Bewährte Methode: Willkommensnachrichten in persönlichen Unterhaltungen

Ihr Bot sollte proaktiv eine Willkommensnachricht an einen persönlichen Chat [senden,](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) wenn ein Benutzer zum ersten Mal (und nur beim ersten Mal) einen persönlichen Chat mit Ihrem Bot initiiert. Diese Empfehlung gilt nicht für Erstmalige Kontakte in einem Kanal.
