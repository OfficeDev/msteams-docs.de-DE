---
title: Grundlagen zu Unterhaltungen
description: In diesem Modul erfahren Sie mehr über botunterhaltungstypen in einem Kanal, persönlichen Chat und Gruppenchatbereichen in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: ab27bc6000712cd046d92d9e020bfbe8fa65daa0
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791818"
---
# <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams-Bot und einem oder mehreren Benutzern gesendet werden. Die folgende Tabelle enthält die drei Arten von Unterhaltungen, die in Teams auch als Bereiche bezeichnet werden:

| Unterhaltungstyp | Beschreibung |
| ------- | ----------- |
| `channel` | Dieser Konversationstyp ist für alle Mitglieder des Kanals sichtbar. |
| `personal` | Dieser Konversationstyp umfasst Unterhaltungen zwischen Bots und einem einzelnen Benutzer. |
| `groupChat` | Dieser Konversationstyp umfasst den Chat zwischen einem Bot und zwei oder mehr Benutzern. Außerdem wird Ihr Bot in Besprechungschats aktiviert. |

Ein Bot verhält sich je nach Der Konversation, an der er beteiligt ist, unterschiedlich:

* Für Bots in Kanal- und Gruppenchatunterhaltungen muss der Benutzer den Bot @erwähnen, um ihn in einem Kanal aufzurufen.

* Für Bots in einer 1:1-Unterhaltung ist keine @Erwähnung erforderlich. Alle vom Benutzer gesendeten Nachrichten werden an Ihren Bot weitergeleitet.

> [!NOTE]
> Bots können aktiviert werden, um alle Kanalnachrichten in einem Team zu empfangen, ohne mit ressourcenspezifischen Zustimmungsberechtigungen (RSC) @mentioned zu werden. Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar. Weitere Informationen finden Sie unter [Empfangen aller Kanalnachrichten mit RSC](channel-messages-with-rsc.md).

Damit der Bot in einer bestimmten Konversation oder einem bestimmten Bereich funktioniert, fügen Sie diesem Bereich im [App-Manifest](~/resources/schema/manifest-schema.md) Unterstützung hinzu.

Jede Nachricht in einer Botunterhaltung ist ein `Activity` Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot, und der Bot verarbeitet die Nachricht. Darüber hinaus können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen, um kernige Befehle zu definieren, auf die Ihr Bot reagiert. Bots in einer Gruppe oder einem Kanal empfangen Nachrichten nur, wenn sie @botname erwähnt werden. Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Unterhaltungsereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse in Ihrem Code erfassen und entsprechende Maßnahmen ergreifen.

Ein Bot kann auch proaktive Nachrichten an Benutzer senden. Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht als Antwort auf eine Anforderung eines Benutzers gesendet wurde. Sie können Ihre Botnachrichten so formatieren, dass sie Rich-Karten enthalten, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video usw. enthalten. Der Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden. Nachrichten können auch mithilfe der Bot Framework-Methode `DeleteActivity` gelöscht werden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Meldungen in Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-messages.md)
