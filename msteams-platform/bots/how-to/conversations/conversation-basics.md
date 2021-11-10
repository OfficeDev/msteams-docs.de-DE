---
title: Grundlagen zu Unterhaltungen
description: Einführung in Bot-Unterhaltungen in einem Kanal, persönlichen Chat und einer Gruppenchatumgebung.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
keyword: conversations basics messages groupchap group channel
ms.openlocfilehash: ec8e5b2d632912aac6cc9e1e06e6db3a7f1ed948
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887441"
---
# <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams Bot und einem oder mehreren Benutzern gesendet werden. Die folgende Tabelle enthält die drei Arten von Unterhaltungen, die in Teams auch als Bereiche bezeichnet werden:

| Unterhaltungstyp | Beschreibung |
| ------- | ----------- |
| `channel` | Dieser Unterhaltungstyp ist für alle Mitglieder des Kanals sichtbar. |
| `personal` | Dieser Unterhaltungstyp umfasst Unterhaltungen zwischen Bots und einem einzelnen Benutzer. |
| `groupChat` | Dieser Unterhaltungstyp umfasst chatten zwischen einem Bot und zwei oder mehr Benutzern. Es aktiviert auch Ihren Bot in Besprechungschats. |

Ein Bot verhält sich abhängig von der Unterhaltung, an der er beteiligt ist, unterschiedlich:

* Für Bots in Kanal- und Gruppenchatunterhaltungen muss der Benutzer den Bot @erwähnen, um ihn in einem Kanal aufzurufen.

* Bots in einer 1:1-Unterhaltung erfordern keine @mention. Alle vom Benutzer gesendeten Nachrichten werden an Ihren Bot weitergeleitet.

> [!NOTE]
> Bots können aktiviert werden, um alle Kanalnachrichten in einem Team zu empfangen, ohne dass sie mithilfe ressourcenspezifischer Zustimmungsberechtigungen (RSC) @mentioned werden. Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar. Weitere Informationen finden Sie unter [Empfangen aller Kanalnachrichten mit RSC.](channel-messages-with-rsc.md)

Damit der Bot in einer bestimmten Unterhaltung oder einem bestimmten Bereich funktioniert, fügen Sie unterstützung zu diesem Bereich im [App-Manifest](~/resources/schema/manifest-schema.md)hinzu.

Jede Nachricht in einer Bot-Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message` . Wenn ein Benutzer eine Nachricht sendet, Teams die Nachricht an Ihren Bot sendet und der Bot die Nachricht verarbeitet. Darüber hinaus können Sie zum Definieren der Kernbefehle, auf die Ihr Bot reagiert, ein Befehlsmenü mit einer Dropdownliste von Befehlen für Ihren Bot hinzufügen. Bots in einer Gruppe oder einem Kanal empfangen Nachrichten nur, wenn sie @botname erwähnt werden. Teams sendet Benachrichtigungen an Ihren Bot für Unterhaltungsereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse in Ihrem Code erfassen und entsprechende Maßnahmen ergreifen.

Ein Bot kann auch proaktive Nachrichten an Benutzer senden. Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht als Antwort auf eine Anforderung eines Benutzers erfolgt. Sie können Ihre Bot-Nachrichten so formatieren, dass sie umfangreiche Karten enthalten, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video usw. enthalten. Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden. Nachrichten können auch mithilfe der Bot Framework-Methode gelöscht `DeleteActivity` werden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Meldungen in Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-messages.md)
