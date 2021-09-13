---
title: Kombinieren von Bots mit Registerkarten
description: Beschreibt, wie Registerkarten und Bots zusammen verwendet werden
keywords: Teams-Bots – Registerkartenentwicklung
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 03/15/2018
ms.openlocfilehash: 3053dbca3b1e91683564eb902d8b142fd4a30ddb
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156704"
---
# <a name="combine-bots-with-tabs"></a>Kombinieren von Bots mit Registerkarten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots und Registerkarten funktionieren gut zusammen und werden häufig zu einem einzigen Back-End-Dienst kombiniert. In diesem Abschnitt werden bewährte Methoden und allgemeine Muster für die gemeinsame Verwendung von Registerkarten und Bots beschrieben.

## <a name="associating-user-identities-across-bot-and-tab"></a>Zuordnen von Benutzeridentitäten über Bots und Registerkarten hinweg

Beispiel: Angenommen, Ihre Registerkartenanwendung verwendet ein proprietäres ID-System, um den Inhalt zu sichern. Angenommen, Sie haben auch einen Bot, der mit dem Benutzer interagieren kann. In der Regel möchten Sie Inhalte auf der Registerkarte anzeigen, die für den anzeigenden Benutzer spezifisch sind. Die Herausforderung besteht darin, dass sich die Benutzer-ID in Ihrem System wahrscheinlich von der Microsoft Teams Benutzer-ID unterscheidet. Wie ordnen Sie diese beiden Identitäten zu?
Im Allgemeinen wird empfohlen, den Benutzer mit dem Bot mit demselben Identitätssystem zu signieren, das für die Authentifizierung des Registerkarteninhalts verwendet wird. Sie können dies über die Anmeldeaktion implementieren, die sich in der Regel über einen OAuth-Fluss beim Benutzer anmeldet.

Dieser Ablauf funktioniert am besten, wenn Ihr Identitätsanbieter das OAuth 2.0-Protokoll implementiert. Anschließend können Sie die Teams Benutzer-ID den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.

   ![Zuordnen von Identitäten](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Erstellen von Deep-Links zu Registerkarten in Nachrichten von Ihrem Bot

Sie können Registerkarten verwenden, um mehr Inhalte anzuzeigen, als in eine Karte passen, oder eine Möglichkeit zum Ausführen komplexer Aufgaben zum Ausfüllen von Formularen mithilfe des Registerkartenbereichs bereitstellen. Ziehen Sie beispielsweise in Betracht, den Benutzer zur Registerkarte zu navigieren, wenn er von Ihrem Bot auf die Karte klickt. Um dies zu erreichen, müssen Sie die Nachricht Ihres Bots codieren, um eine [Deep-Link-URL](~/concepts/build-and-test/deep-links.md) entweder über Markup oder als Ziel der openUrl-Aktion einzuschließen.

Deep-Links basieren auf einer entityId, bei der es sich um einen undurchsichtigen Wert handelt, der einer eindeutigen Entität in Ihrem System zugeordnet ist. Wenn die Registerkarte erstellt wird, speichern Sie im Idealfall einen einfachen Zustand, z. B. ein Flag in Ihrem Back-End, das angibt, dass die Registerkarte im Kanal erstellt wurde. Wenn Ihr Bot eine Nachricht erstellt, kann er auf die entityId abzielen, die dieser Registerkarte zugeordnet ist.

> [!NOTE]
> da Registerkarten in persönlichen Chats "statisch" sind und mit der App installiert werden, können Sie immer davon ausgehen, dass sie vorhanden sind, und daher Deep-Links entsprechend erstellen.

## <a name="sending-notifications-for-tab-updates"></a>Senden von Benachrichtigungen für Registerkartenupdates

Häufig sollten Sie den Endbenutzer benachrichtigen, wenn auf einer Registerkarte ein Update oder eine Benutzeraktion ausgeführt wird. Ein Beispielszenario besteht darin, einem Mitteammitglied eine Aufgabe oder ein Ticket zuzuweisen und dann dieses Teammitglied zu benachrichtigen.

Es gibt zwei Möglichkeiten, dieses Szenario zu erreichen:

1. Wenn Sie einen gesamten Kanal benachrichtigen möchten, kann Ihr Bot asynchron eine Nachricht an den Kanal senden. Es gibt keine Möglichkeit für einen Bot, die Registerkartenunterhaltung proaktiv zu erstellen, wenn sie nicht mit der Registerkarte erstellt wurde.

2. Wenn Sie nur den Empfänger oder interessierte Parteien benachrichtigen möchten, die an der Aktion beteiligt sind, kann Ihr Bot eine persönliche Chatnachricht an den Benutzer senden. Überprüfen Sie zunächst, ob eine persönliche Unterhaltung zwischen Ihrem Bot und dem Benutzer vorhanden ist. Wenn nicht, können Sie `CreateConversation` anrufen, um den persönlichen Chat zu initiieren.

Verwenden Sie ereignisbenachrichtigungen in beiden Fällen weise und spammen Sie den Benutzer niemals mit unnötigen Updates.
