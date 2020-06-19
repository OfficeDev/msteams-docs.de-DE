---
title: 1-zu-1-Unterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario mit einer 1-zu-1-Unterhaltung mit einem bot in Microsoft Teams.
keywords: Teams-Szenarien 1on1 1to1 Conversation bot
ms.date: 05/20/2019
ms.openlocfilehash: e23bb98160125d7fdbb4521467e2f522d6b6ce40
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801242"
---
# <a name="have-a-personal-one-on-one-conversation-with-a-microsoft-teams-bot"></a>Haben Sie eine persönliche (eins-zu-eins)-Unterhaltung mit einem Microsoft Teams-bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams ermöglicht Benutzern das direkte Gespräch mit Bots, die auf dem [Microsoft bot Framework](/azure/bot-service/?view=azure-bot-service-3.0)basieren. Benutzer können Bots im Discover apps Gallery finden und diese Ihrer Teams-Umgebung für persönliche Unterhaltungen hinzufügen. Teambesitzer und Benutzer mit den entsprechenden Berechtigungen können Bots auch als Teammitglieder hinzufügen (siehe [Interact in einem Team Kanal](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)), was Sie nicht nur in den Kanälen dieses Teams verfügbar machen, sondern auch für den persönlichen Chat für alle diese Benutzer.

Persönlicher Chat unterscheidet sich von Chat in Kanälen dadurch, dass der Benutzer den bot nicht @mention muss. Wenn ein bot in mehreren Kontexten (Personal, groupChat oder Kanal) verwendet wird, müssen Sie erkennen, ob sich der bot in einem Gruppenchat oder-Kanal befindet und Nachrichten etwas anders verarbeiten. Weitere Informationen finden Sie unter [Interact in einem Team Kanal oder Gruppenchat](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .

## <a name="designing-a-great-personal-bot"></a>Entwerfen eines großen persönlichen bot

Ein großer bot in Microsoft Teams hilft Benutzern, die benötigten Informationen zu erhalten, und zwar im Kontext der Teams-Erfahrung. Bei persönlichen Gesprächen mit einem bot handelt es sich um einen privaten Austausch zwischen einem bot und seinem Benutzer. Sie sind eine hervorragende Möglichkeit, Informationen für diesen Benutzer im persönlichen Kontext bereitzustellen. Ein bot im persönlichen Chat ist wirklich ein Dialog zwischen Ihrem Dienst und dem einzelnen, bei dem ein bot in einem Gruppenchat oder Kanal alles an eine Gruppe von Personen sendet.

Je nachdem, welche Erfahrung Sie erstellen möchten, muss der bot möglicherweise in mehreren Bereichen-Personal, groupChat und/oder Team-arbeiten. Die Arbeit zur Unterstützung von mehr als einem Bereich ist minimal. Es gibt keine Erwartung in Microsoft Teams, dass Ihre bot-Funktion in allen Bereichen, aber Sie sollten sicherstellen, dass Ihr bot sinnvoll ist und den Benutzerwert in welchem Bereich (n), die Sie auswählen, zu unterstützen.

## <a name="best-practice-welcome-messages-in-personal-conversations"></a>Bewährte Methode: Willkommensnachrichten in persönlichen Unterhaltungen

Ihr bot sollte [proaktiv](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) eine Willkommensnachricht an einen persönlichen Chat senden (und nur zum ersten Mal), dass ein Benutzer einen persönlichen Chat mit Ihrem bot initiiert. (Diese Empfehlung gilt nicht für erstmalige Kontakte in einem Kanal.)
