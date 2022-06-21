---
title: Kombinieren von Bots mit Registerkarten
description: In diesem Artikel erfahren Sie, wie Sie Registerkarten und Bots zusammen verwenden und Deep-Links zu Registerkarten in Nachrichten von Ihrem Bot und der Entwicklung von Teams-Bots-Registerkarten erstellen.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 03/15/2018
ms.openlocfilehash: 47a8ba3081fa629c650dfdf588e4b0c60600561e
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189736"
---
# <a name="combine-bots-with-tabs"></a>Kombinieren von Bots mit Registerkarten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots und Registerkarten arbeiten zusammen und werden häufig zu einem einzigen Back-End-Dienst kombiniert. In diesem Abschnitt werden bewährte Methoden und allgemeine Muster für die gemeinsame Verwendung von Registerkarten und Bots beschrieben.

## <a name="associating-user-identities-across-bot-and-tab"></a>Zuordnen von Benutzeridentitäten zu Bots und Registerkarten

Beispiel: Angenommen, Ihre Registerkartenanwendung verwendet ein proprietäres ID-System, um dessen Inhalt zu sichern. Angenommen, Sie haben auch einen Bot, der mit dem Benutzer interagieren kann. In der Regel möchten Sie Inhalte auf der Registerkarte anzeigen, die für den Anzeigebenutzer spezifisch ist. Die Herausforderung besteht darin, dass sich die Benutzer-ID in Ihrem System wahrscheinlich von der Microsoft Teams Benutzer-ID unterscheidet. Wie ordnen Sie diese beiden Identitäten zu?
Im Allgemeinen besteht der empfohlene Ansatz darin, den Benutzer mit dem Bot mit demselben Identitätssystem anzumelden, das zum Bereitstellen der Authentifizierung für den Registerkarteninhalt verwendet wird. Sie können dies über die Anmeldeaktion implementieren, die in der Regel den Benutzer über einen OAuth-Fluss anmeldet.

Dieser Fluss funktioniert am besten, wenn Ihr Identitätsanbieter das OAuth 2.0-Protokoll implementiert. Anschließend können Sie die Teams Benutzer-ID den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.

   ![Zuordnen von Identitäten](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Erstellen von Deep-Links zu Registerkarten in Nachrichten von Ihrem Bot

Sie möchten Registerkarten verwenden, um mehr Inhalte anzuzeigen, die in eine Karte passen, oder eine Möglichkeit zum Ausführen komplexer Aufgaben zum Ausfüllen von Formularen mithilfe des Registerkartenzeichenbereichs bieten. Erwägen Sie beispielsweise, den Benutzer zur Registerkarte zu navigieren, wenn der Benutzer die Karte in Ihrem Bot auswählt. Dazu müssen Sie die Nachricht Ihres Bots codieren, um eine [Deep-Link-URL](~/concepts/build-and-test/deep-links.md) einzuschließen, entweder über Markup oder als Ziel der openUrl-Aktion.

Deep-Links basieren auf einer entityId, einem undurchsichtigen Wert, der einer eindeutigen Entität in Ihrem System zugeordnet ist. Wenn die Registerkarte erstellt wird, speichern Sie einen einfachen Zustand. Kennzeichnen Sie z. B. auf Ihrem Back-End, dass die Registerkarte im Kanal erstellt wurde. Wenn Ihr Bot eine Nachricht erstellt, kann er auf die entitäts-ID abzielen, die dieser Registerkarte zugeordnet ist.

> [!NOTE]
> da Registerkarten in persönlichen Chats "statisch" sind und mit der App installiert sind, können Sie immer deren Existenz annehmen und so Deep-Links entsprechend erstellen.

## <a name="sending-notifications-for-tab-updates"></a>Senden von Benachrichtigungen für Registerkartenaktualisierungen

Häufig möchten Sie den Endbenutzer benachrichtigen, wenn ein Update oder eine Benutzeraktion auf einer Registerkarte auftritt. Ein Beispielszenario ist das Zuweisen einer Aufgabe oder eines Tickets zu einem anderen Teammitglied und anschließendes Benachrichtigen dieses Teammitglieds.

Es gibt zwei Möglichkeiten, dieses Szenario zu erreichen:

1. Wenn Sie einen gesamten Kanal benachrichtigen möchten, kann Ihr Bot asynchron eine Nachricht an den Kanal senden. Es gibt keine Möglichkeit für einen Bot, die Registerkartenunterhaltung proaktiv zu erstellen, wenn sie nicht mit der Registerkarte erstellt wurde.

2. Wenn Sie nur den Empfänger oder die an der Aktion beteiligten Interessenten benachrichtigen möchten, kann Ihr Bot eine persönliche Chatnachricht an den Benutzer senden. Sie sollten zuerst überprüfen, ob eine persönliche Unterhaltung zwischen Ihrem Bot und dem Benutzer vorhanden ist. Andernfalls können Sie anrufen `CreateConversation` , um den persönlichen Chat zu initiieren.

Verwenden Sie in beiden Fällen Ereignisbenachrichtigungen mit Bedacht, und spammen Sie den Benutzer niemals mit unnötigen Updates.
