---
title: Kombinieren von Bots mit Registerkarten
description: Beschreibt, wie Registerkarten und Bots zusammen verwendet werden
keywords: Entwicklung von Teams-Bots-Registerkarten
ms.topic: conceptual
ms.date: 03/15/2018
ms.openlocfilehash: d8ef669f55d5edbb9795fa2d34277bd2e2dccc7c
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696598"
---
# <a name="combine-bots-with-tabs"></a>Kombinieren von Bots mit Registerkarten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots und Registerkarten funktionieren gut und werden häufig in einem einzigen Back-End-Dienst kombiniert. In diesem Abschnitt werden bewährte Methoden und allgemeine Muster für die gemeinsame Verwendung von Registerkarten und Bots beschrieben.

## <a name="associating-user-identities-across-bot-and-tab"></a>Zuordnen von Benutzeridentitäten über Bot und Registerkarte

Beispiel: Angenommen, Ihre Registerkartenanwendung verwendet ein proprietäres ID-System, um den Inhalt zu sichern. Angenommen, Sie haben auch einen Bot, der mit dem Benutzer interagieren kann. In der Regel möchten Sie Inhalte auf der Registerkarte anzeigen, die für den Anzeigebenutzer spezifisch sind. Die Herausforderung besteht darin, dass die Benutzer-ID in Ihrem System wahrscheinlich von der Microsoft Teams-Benutzer-ID abhing. Wie ordnen Sie diese beiden Identitäten zu?
Im Allgemeinen wird empfohlen, den Benutzer mit dem Bot mit demselben Identitätssystem zu signieren, das zum Bereitstellen der Authentifizierung für die Registerkarteninhalte verwendet wird. Sie können dies über die Anmeldeaktion implementieren, die sich in der Regel über einen OAuth-Fluss beim Benutzer anmeldet.

Dieser Fluss funktioniert am besten, wenn Ihr Identitätsanbieter das OAuth 2.0-Protokoll implementiert. Anschließend können Sie die Benutzer-ID von Teams den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.

   ![Zuordnen von Identitäten](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Erstellen von tiefen Links zu Registerkarten in Nachrichten von Ihrem Bot

Sie können Registerkarten verwenden, um mehr Inhalt anzuzeigen, als in eine Karte passen kann, oder eine Möglichkeit bieten, komplexe Aufgaben zum Ausfüllen von Formularen mithilfe des Registerkartenbereichs auszuführen. Erwägen Sie beispielsweise, den Benutzer auf die Registerkarte zu navigieren, wenn er auf die Karte von Ihrem Bot klickt. Damit dies geschieht, müssen Sie die Nachricht Ihres Bots codieren, um eine Deep [Link-URL](~/concepts/build-and-test/deep-links.md) entweder über Markup oder als Ziel der openUrl-Aktion zu verwenden.

Deep links rely on an entityId, which is an opaque value that maps to a unique entity in your system. Wenn die Registerkarte erstellt wird, speichern Sie im Idealfall einen einfachen Zustand (z. B. Flag) im Back-End, der angibt, dass die Registerkarte im Kanal erstellt wurde. Wenn ihr Bot eine Nachricht erstellt, kann er auf die entityId zielen, die dieser Registerkarte zugeordnet ist.

**Hinweis:** Da Registerkarten in persönlichen Chats "statisch" sind und mit der App installiert sind, können Sie immer davon ausgehen, dass sie existieren und daher tiefe Links entsprechend erstellen.

## <a name="sending-notifications-for-tab-updates"></a>Senden von Benachrichtigungen für Registerkartenupdates

Häufig möchten Sie den Endbenutzer benachrichtigen, wenn ein Update oder eine Benutzeraktion auf einer Registerkarte auftritt. Ein Beispielszenario ist das Zuweisen einer Aufgabe oder eines Tickets zu einem kollegen Teammitglied und dann das Benachrichtigen dieses Teammitglieds.

Es gibt zwei Möglichkeiten, um dieses Szenario zu erreichen:

1. Wenn Sie einen gesamten Kanal benachrichtigen möchten, kann Ihr Bot asynchron eine Nachricht an den Kanal posten. Es gibt keine Möglichkeit für einen Bot, die Tab-Unterhaltung proaktiv zu erstellen, wenn sie nicht mit der Registerkarte erstellt wurde.

2. Wenn Sie nur den Empfänger oder die interessierten Parteien benachrichtigen möchten, die an der Aktion beteiligt sind, kann Ihr Bot eine persönliche Chatnachricht an den Benutzer senden. Sie sollten zuerst überprüfen, ob eine persönliche Unterhaltung zwischen Ihrem Bot und dem Benutzer vorhanden ist. Wenn nicht, können Sie anrufen, `CreateConversation` um den persönlichen Chat zu initiieren.

Verwenden Sie in beiden Fällen Ereignisbenachrichtigungen mit Bedacht, und spamen Sie den Benutzer niemals mit unnötigen Updates.
