---
title: 1-zu-1-Unterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario einer 1:1-Unterhaltung mit einem Bot in Microsoft Teams
keywords: teams scenarios 1on1 1to1 conversation bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 05/20/2019
ms.openlocfilehash: dff65e919485eff0443032995b934b7ae93c64eb
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566502"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Führen einer persönlichen (1:1) Unterhaltung mit einem Microsoft Teams Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht Benutzern, direkte Unterhaltungen mit Bots zu führen, die auf dem [Microsoft Bot Framework.](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true) Benutzer können Bots im Katalog "Apps entdecken" finden und sie Teams persönliche Unterhaltungen hinzufügen. Teambesitzer und Benutzer mit den entsprechenden Berechtigungen können auch Bots als Teammitglieder hinzufügen. Weitere Informationen finden Sie unter [Interagieren in](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)einem Teamkanal ), der sie nicht nur in den Kanälen dieses Teams zur Verfügung stellt, sondern auch für persönliche Chats für alle diese Benutzer.

Der persönliche Chat unterscheidet sich vom Chat in Kanälen, da der Benutzer den @mention muss. Wenn ein Bot in mehreren Kontexten wie persönlichen, groupChat oder Kanal verwendet wird, müssen Sie erkennen, ob sich der Bot in einem Gruppenchat oder Kanal befindet, und Nachrichten etwas anders verarbeiten. Weitere Informationen finden Sie unter [Interact in a team channel or group chat](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

## <a name="designing-a-great-personal-bot"></a>Entwerfen eines großartigen persönlichen Bots

Ein großartiger Bot in Microsoft Teams hilft Benutzern, die benötigten Informationen im Kontext der Teams erhalten. Persönliche Unterhaltungen mit einem Bot sind privater Austausch zwischen einem Bot und seinem Benutzer. Sie sind eine hervorragende Möglichkeit, um bestimmte und für diesen Benutzer relevante Informationen im persönlichen Kontext zur Verfügung zu stellen. Ein Bot im persönlichen Chat ist wirklich ein Dialogfeld zwischen Ihrem Dienst und der Person, in dem ein Bot in einem Gruppenchat oder Kanal alles an eine Gruppe von Personen sendet.

Je nachdem, wie sie erstellt werden möchten, muss der Bot möglicherweise in mehreren Bereiche verwendet werden : personal, groupchat und team. Die Arbeit zur Unterstützung von mehr als einem Bereich ist minimal. Es besteht keine erwartungsversprechend Teams, dass Ihr Bot in allen Bereiche funktioniert. Sie sollten jedoch sicherstellen, dass Ihr Bot sinnvoll ist und einen Benutzerwert in den von Ihnen unterstützten Umfangen bietet.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Bewährte Methode: Willkommensnachrichten in persönlichen Unterhaltungen

Ihr Bot sollte [proaktiv](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) eine Willkommensnachricht an einen persönlichen Chat senden, wenn ein Benutzer das erste Mal (und nur das erste Mal) einen persönlichen Chat mit Ihrem Bot initiiert. Diese Empfehlung gilt nicht für Erste-Mal-Kontakte in einem Kanal.
