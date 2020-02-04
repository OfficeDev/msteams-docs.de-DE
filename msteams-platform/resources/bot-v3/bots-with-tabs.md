---
title: Kombinieren von Bots mit Registerkarten
description: Beschreibt, wie Registerkarten und Bots gemeinsam verwendet werden
keywords: Teams Bots-Tabs-Entwicklung
ms.date: 03/15/2018
ms.openlocfilehash: 59ae8bc01f82c70dd7ea6869cb870e26acae1293
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674376"
---
# <a name="combine-bots-with-tabs"></a>Kombinieren von Bots mit Registerkarten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots und Registerkarten funktionieren gut zusammen und werden häufig in einem einzigen Back-End-Dienst kombiniert. In diesem Abschnitt werden bewährte Methoden und allgemeine Muster für die Verwendung von Registerkarten und Bots zusammen beschrieben.

## <a name="associating-user-identities-across-bot-and-tab"></a>Zuordnen von Benutzeridentitäten über bot und Tab

Beispiel: angenommen, ihre Tab-Anwendung verwendet ein proprietäres ID-System, um den Inhalt zu sichern. Angenommen, Sie haben auch einen bot, der mit dem Benutzer interagieren kann. In der Regel sollten Sie Inhalte auf der Registerkarte anzeigen, die speziell für den Benutzer angezeigt wird. Die Herausforderung besteht darin, dass sich die Benutzer-ID in Ihrem System wahrscheinlich von der Benutzer-ID von Microsoft Teams unterscheidet. Wie ordnen Sie diese beiden Identitäten zu?
Im Allgemeinen besteht der empfohlene Ansatz darin, den Benutzer mit dem gleichen Identitätssystem, mit dem die Authentifizierung für die Registerkarteninhalte erfolgt, mit dem bot zu signieren. Sie können dies über die Anmeldeaktion implementieren, die sich in der Regel über einen OAuth-Fluss im Benutzer anmeldet.

Dieser Ablauf eignet sich am besten, wenn Ihr Identitätsanbieter das OAuth 2,0-Protokoll implementiert. Anschließend können Sie die Microsoft Teams-Benutzer-ID den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.

   ![Zuordnen von Identitäten](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Erstellen von Deep-Links zu Registerkarten in Nachrichten von Ihrem bot

Möglicherweise möchten Sie Registerkarten verwenden, um mehr Inhalte anzuzeigen, als in eine Karte passt, oder um komplexe Aufgaben zum Ausfüllen von Formularen mithilfe des Registerkartenbereichs abzuschließen. Beispielsweise sollten Sie den Benutzer zur Registerkarte navigieren, wenn er von Ihrem bot auf die Karte klickt. Damit dies geschieht, müssen Sie die Nachricht Ihres bot codieren, um eine [Deep Link](~/concepts/build-and-test/deep-links.md) -URL zu verwenden, entweder über Markup oder als Ziel der openUrl-Aktion.

Deep-Links basieren auf einer Entitäts-Nr, bei der es sich um einen nicht transparenten Wert handelt, der einer eindeutigen Entität in Ihrem System zugeordnet ist. Wenn die Registerkarte erstellt wird, speichern Sie im Idealfall einen einfachen Zustand (beispielsweise "Flag") im Back-End, der angibt, dass die Registerkarte im Kanal erstellt wurde. Wenn Ihr bot eine Nachricht erstellt, kann Sie auf die Entitäts-Nr, die dieser Registerkarte zugeordnet ist, abzielen.

**Hinweis:** in persönlichen Chats, da Registerkarten "statisch" sind und mit der APP installiert werden, können Sie immer ihre Existenz übernehmen und so tiefe Verknüpfungen entsprechend erstellen.

## <a name="sending-notifications-for-tab-updates"></a>Senden von Benachrichtigungen für Registerkarten Aktualisierungen

Häufig möchten Sie den Endbenutzer Benachrichtigen, wenn eine Aktualisierung oder eine Benutzeraktion auf einer Registerkarte erfolgt. Ein Beispielszenario ist das Zuweisen einer Aufgabe oder eines Tickets zu einem Teammitglied und das anschließende Benachrichtigen dieses Teammitglieds.

Es gibt zwei Möglichkeiten, dieses Szenario zu erreichen:

1. Wenn Sie einen ganzen Kanal benachrichtigen möchten, kann Ihr bot asynchron eine Nachricht an den Kanal senden. Es gibt keine Möglichkeit für einen bot, proaktiv die Registerkarten Unterhaltung zu erstellen, wenn er nicht mit der Registerkarte erstellt wurde.

2. Wenn Sie nur den Empfänger oder interessierte Parteien benachrichtigen möchten, die an der Aktion beteiligt sind, kann Ihr bot eine persönliche Chatnachricht an den Benutzer senden. Überprüfen Sie zunächst, ob eine persönliche Unterhaltung zwischen Ihrem bot und dem Benutzer vorhanden ist. Wenn dies nicht der Fall ist `CreateConversation` , können Sie zum Initiieren des persönlichen Chats aufrufen.

Verwenden Sie in beiden Fällen Ereignisbenachrichtigungen mit Bedacht und niemals Spam für den Benutzer mit unnötigen Updates.
