---
title: Kombinieren von Bots mit Registerkarten
description: In diesem Artikel erfahren Sie, wie Sie Registerkarten und Bots zusammen verwenden und Deep-Links zu Registerkarten in Nachrichten ihres Bots und Teams-Bots erstellen.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 03/15/2018
ms.openlocfilehash: f993f3d8deb8b8a781c96627bf63c2eed350e6c8
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833023"
---
# <a name="combine-bots-with-tabs"></a>Kombinieren von Bots mit Registerkarten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots und Registerkarten arbeiten zusammen und werden häufig zu einem einzigen Back-End-Dienst kombiniert. In diesem Abschnitt werden bewährte Methoden und gängige Muster für die gemeinsame Verwendung von Registerkarten und Bots beschrieben.

## <a name="associating-user-identities-across-bot-and-tab"></a>Zuordnen von Benutzeridentitäten über Bot und Registerkarte

Beispiel: Angenommen, Ihre Registerkartenanwendung verwendet ein proprietäres ID-System, um den Inhalt zu schützen. Angenommen, Sie verfügen auch über einen Bot, der mit dem Benutzer interagieren kann. In der Regel möchten Sie Inhalte auf der Registerkarte anzeigen, die für den anzeigenden Benutzer spezifisch sind. Die Herausforderung besteht darin, dass sich die Benutzer-ID in Ihrem System wahrscheinlich von der Microsoft Teams-Benutzer-ID unterscheidet. Wie ordnen Sie diese beiden Identitäten zu?
Im Allgemeinen wird empfohlen, den Benutzer mit dem Bot mit demselben Identitätssystem anzumelden, das für die Authentifizierung des Registerkarteninhalts verwendet wurde. Sie können die Implementierung über die Anmeldeaktion durchführen, die den Benutzer in der Regel über einen OAuth-Flow anmeldet.

Dieser Flow funktioniert am besten, wenn Ihr Identitätsanbieter das OAuth 2.0-Protokoll implementiert. Anschließend können Sie die Teams-Benutzer-ID den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.

   :::image type="content" source="../../assets/images/bots/associating_contexts.png" alt-text="Screenshot: Zuordnen von Identitäten":::

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Erstellen von Deep-Links zu Registerkarten in Nachrichten von Ihrem Bot

Sie möchten Registerkarten verwenden, um mehr Inhalte anzuzeigen, die in eine Karte passen können, oder eine Möglichkeit zum Ausführen komplexer Aufgaben zum Ausfüllen von Formularen mithilfe des Registerkartenzeichenbereichs bieten. Erwägen Sie beispielsweise, den Benutzer zur Registerkarte zu navigieren, wenn der Benutzer die Karte aus Ihrem Bot auswählt. Dazu müssen Sie die Nachricht Ihres Bots codieren, um eine [Deep Link-URL](~/concepts/build-and-test/deep-links.md) einzuschließen, entweder über Markup oder als Ziel der openUrl-Aktion.

DeepLinks basieren auf einer entityId, bei der es sich um einen nicht transparenten Wert handelt, der einer eindeutigen Entität in Ihrem System zugeordnet ist. Wenn die Registerkarte erstellt wird, speichern Sie einen einfachen Zustand. Beispiel: Flag auf Ihrem Back-End, das angibt, dass die Registerkarte im Kanal erstellt wurde. Wenn Ihr Bot eine Nachricht erstellt, kann er auf die entityId abzielen, die dieser Registerkarte zugeordnet ist.

> [!NOTE]
> Da Registerkarten in persönlichen Chats *statisch* sind und mit der App installiert sind, können Sie immer davon ausgehen, dass sie vorhanden sind und daher deep links entsprechend erstellen.

## <a name="sending-notifications-for-tab-updates"></a>Senden von Benachrichtigungen für Registerkartenupdates

Häufig möchten Sie den Endbenutzer benachrichtigen, wenn ein Update oder eine Benutzeraktion auf einer Registerkarte erfolgt. Ein Beispielszenario ist das Zuweisen einer Aufgabe oder eines Tickets zu einem Anderen Teammitglied und das anschließende Benachrichtigen dieses Teammitglieds.

Es gibt zwei Möglichkeiten, dieses Szenario zu erreichen:

1. Wenn Sie einen gesamten Kanal benachrichtigen möchten, kann Ihr Bot eine Nachricht asynchron an den Kanal senden. Es gibt keine Möglichkeit für einen Bot, die Registerkartenunterhaltung proaktiv zu erstellen, wenn sie nicht mit der Registerkarte erstellt wurde.

2. Wenn Sie nur den Empfänger oder die interessierten Parteien benachrichtigen möchten, die an der Aktion beteiligt sind, kann Ihr Bot eine persönliche Chatnachricht an den Benutzer senden. Sie sollten zunächst überprüfen, ob eine persönliche Konversation zwischen Ihrem Bot und dem Benutzer besteht. Andernfalls können Sie anrufen `CreateConversation` , um den persönlichen Chat zu initiieren.

Verwenden Sie in beiden Fällen Ereignisbenachrichtigungen mit Bedacht, und spamen Sie den Benutzer niemals mit unnötigen Updates.
