---
title: 1-on-1-Gespräche mit Bots
description: Beschreibt das End-to-End-Szenario eines 1-gegen-1-Gesprächs mit einem Bot in Microsoft Teams
keywords: Teams Szenarien 1on1 1to1 Konversationsbot
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
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Führen Sie ein persönliches (Einzel-)Gespräch mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht es Benutzern, direkte Gespräche mit Bots zu führen, die auf dem [Microsoft Bot Framework](/azure/bot-service/?view=azure-bot-service-3.0&preserve-view=true). Benutzer können Bots in der Discover Apps-Galerie finden und sie zu ihrem Teams-Erlebnis für persönliche Unterhaltungen hinzufügen. Teambesitzer und Benutzer mit den entsprechenden Berechtigungen können auch Bots als Teammitglieder hinzufügen. Weitere Informationen finden Sie unter [Interagieren in einem Teamkanal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)), der sie nicht nur in den Kanälen dieses Teams verfügbar macht, sondern auch für den persönlichen Chat für alle diese Benutzer.

Persönlicher Chat unterscheidet sich vom Chat in Kanälen dadurch, dass der Benutzer den Bot nicht @mention muss. Wenn ein Bot in mehreren Kontexten wie Personal, groupChat oder Channel verwendet wird, müssen Sie erkennen, ob sich der Bot in einem Gruppenchat oder -kanal befindet, und Nachrichten etwas anders verarbeiten. Weitere Informationen finden Sie unter [Interagieren in einem Teamkanal oder Gruppenchat](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).

## <a name="designing-a-great-personal-bot"></a>Entwerfen eines großartigen persönlichen Bots

Ein großartiger Bot in Microsoft Teams hilft Benutzern, die Informationen zu erhalten, die sie benötigen, und das alles im Kontext der Teams Erfahrung. Persönliche Gespräche mit einem Bot sind private Austausch zwischen einem Bot und seinem Benutzer; Sie sind eine großartige Möglichkeit, Informationen zu liefern, die für diesen Benutzer im persönlichen Kontext spezifisch und relevant sind. Ein Bot im persönlichen Chat ist wirklich ein Dialog zwischen Ihrem Dienst und der Person, wo ein Bot in einem Gruppenchat oder -kanal alles an eine Gruppe von Personen sendet.

Je nach der Erfahrung, die Sie erstellen möchten, muss der Bot möglicherweise in mehreren Bereichen arbeiten - persönlich, groupchat und Team. Die Arbeit zur Unterstützung von mehr als einem Bereich ist minimal. Es gibt keine Erwartung in Teams, dass Ihr Bot in allen Bereichen funktioniert, aber Sie sollten sicherstellen, dass Ihr Bot sinnvoll ist und Benutzerwert in den Bereichen bietet, die Sie unterstützen möchten.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Bewährte Verfahren: Willkommensbotschaften in persönlichen Gesprächen

Ihr Bot sollte proaktiv eine Willkommensnachricht an einen persönlichen Chat [senden,](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) wenn er zum ersten Mal (und nur zum ersten Mal) ein Benutzer einen persönlichen Chat mit Ihrem Bot initiiert. Diese Empfehlung gilt nicht für Erstkontakte in einem Kanal.
