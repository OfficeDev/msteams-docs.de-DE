---
title: Kombinieren von Bots mit Registerkarten
description: Beschreibt die gemeinsame Verwendung von Tabs und Bots
keywords: Teams Bots Tabs Entwicklung
ms.topic: conceptual
localization_priority: Normal
ms.date: 03/15/2018
ms.openlocfilehash: 3273369ad1122355b792dc3d429c3a4eff7e1d47
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566453"
---
# <a name="combine-bots-with-tabs"></a>Kombinieren von Bots mit Registerkarten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Bots und Tabs funktionieren gut zusammen und werden oft zu einem einzigen Back-End-Service kombiniert. In diesem Abschnitt werden bewährte Methoden und allgemeine Muster für die gemeinsame Verwendung von Registerkarten und Bots beschrieben.

## <a name="associating-user-identities-across-bot-and-tab"></a>Zuordnen von Benutzeridentitäten zwischen Bot und Registerkarte

Beispiel: Angenommen, Ihre Tab-Anwendung verwendet ein proprietäres ID-System, um ihren Inhalt zu sichern. Angenommen, Sie haben auch einen Bot, der mit dem Benutzer interagieren kann. In der Regel sollten Sie Inhalte auf der Registerkarte anzeigen, die für den anzeigenden Benutzer spezifisch sind. Die Herausforderung besteht darin, dass sich die Benutzer-ID in Ihrem System wahrscheinlich von der Microsoft Teams-Benutzer-ID unterscheidet. Wie verbinden Sie diese beiden Identitäten?
Im Allgemeinen wird empfohlen, den Benutzer mit dem Bot mit demselben Identitätssystem zu signieren, das zum Bereitstellen der Authentifizierung für den Tabstoppinhalt verwendet wird. Sie können dies über die Anmeldeaktion implementieren, die sich in der Regel über einen OAuth-Fluss beim Benutzer anmeldet.

Dieser Flow funktioniert am besten, wenn Ihr Identitätsanbieter das OAuth 2.0-Protokoll implementiert. Anschließend können Sie die Teams Benutzer-ID den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.

   ![Zuordnen von Identitäten](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a>Erstellen von tiefen Links zu Registerkarten in Nachrichten aus Ihrem Bot

Sie können Registerkarten verwenden, um mehr Inhalt anzuzeigen, als in eine Karte passen, oder eine Möglichkeit bieten, komplexe Formularfüllaufgaben mithilfe des Registerkartenbereichs abzuschließen. Erwägen Sie beispielsweise, den Benutzer auf die Registerkarte zu navigieren, wenn er auf die Karte ihres Bots klickt. Damit dies geschieht, müssen Sie die Nachricht Ihres Bots codieren, um eine [Deep-Link-URL](~/concepts/build-and-test/deep-links.md) einzuschließen, entweder durch Markup oder als Ziel der openUrl-Aktion.

Tiefe Verknüpfungen basieren auf einer entityId, einem undurchsichtigen Wert, der einer eindeutigen Entität in Ihrem System zugeordnet ist. Wenn die Registerkarte erstellt wird, speichern Sie idealerweise einen einfachen Zustand, z. B. ein Flag auf Ihrem Backend, das angibt, dass die Registerkarte im Kanal erstellt wurde. Wenn Ihr Bot eine Nachricht erstellt, kann er auf die entityId abzielen, die dieser Registerkarte zugeordnet ist.

> [!NOTE]
> In persönlichen Chats, da Tabs "statisch" sind und mit der App installiert sind, können Sie immer ihre Existenz annehmen und so tiefe Links entsprechend konstruieren.

## <a name="sending-notifications-for-tab-updates"></a>Senden von Benachrichtigungen für Tabstoppaktualisierungen

Häufig möchten Sie den Endbenutzer benachrichtigen, wenn ein Update oder eine Benutzeraktion auf einer Registerkarte stattfindet. Ein Beispielszenario besteht darin, einem anderen Teammitglied eine Aufgabe oder ein Ticket zuzuweisen und dieses Teammitglied dann zu benachrichtigen.

Es gibt zwei Möglichkeiten, dieses Szenario zu erreichen:

1. Wenn Sie einen gesamten Kanal benachrichtigen möchten, kann Ihr Bot asynchron eine Nachricht an den Kanal senden. Es gibt keine Möglichkeit für einen Bot, proaktiv die Tabstoppunterhaltung zu erstellen, wenn sie nicht mit der Registerkarte erstellt wurde.

2. Wenn Sie nur den Empfänger oder interessierte Parteien, die an der Aktion beteiligt sind, benachrichtigen möchten, kann Ihr Bot eine persönliche Chat-Nachricht an den Benutzer senden. Sie sollten zuerst überprüfen, ob eine persönliche Unterhaltung zwischen Ihrem Bot und dem Benutzer vorhanden ist. Wenn nicht, können Sie `CreateConversation` anrufen, um den persönlichen Chat zu initiieren.

Verwenden Sie in beiden Fällen Ereignisbenachrichtigungen mit Bedacht und spamtherieren Sie den Benutzer niemals mit unnötigen Updates.
