---
title: Grundlagen zu Unterhaltungen
description: Einführung in Unterhaltungen
ms.topic: overview
ms.author: anclear
keyword: conversations basics messages
ms.openlocfilehash: eff1c6fe18f7b2ba082b5075b6c1806f41b68a6b
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "51996037"
---
# <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams-Bot und einem oder mehreren Benutzern gesendet werden. Die folgende Tabelle enthält die drei Arten von Unterhaltungen, die auch als Bereiche in Teams bezeichnet werden:

| Unterhaltungstyp | Description |
| ------- | ----------- |
| `channel` | Dieser Unterhaltungstyp ist für alle Mitglieder des Kanals sichtbar. |
| `personal` | Dieser Unterhaltungstyp enthält Unterhaltungen zwischen Bots und einem einzelnen Benutzer. |
| `groupChat` | Dieser Unterhaltungstyp umfasst Chats zwischen einem Bot und zwei oder mehr Benutzern. Es aktiviert ihren Bot auch in Besprechungschats. |

Ein Bot verhält sich abhängig von der Unterhaltung, an der er beteiligt ist, unterschiedlich:

* Bots in Kanal- und Gruppenchatunterhaltungen erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufgerufen zu haben.
* Bots in einer 1:1-Unterhaltung erfordern keine @-Erwähnung. Alle nachrichten, die vom Benutzer gesendet werden, werden an Ihren Bot gesendet.

Damit der Bot in einer bestimmten Unterhaltung oder einem bestimmten Bereich funktioniert, fügen Sie diesem Bereich unterstützung im [App-Manifest hinzu.](~/resources/schema/manifest-schema.md)

Jede Nachricht in einer Bot-Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message` . Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot, und der Bot verarbeitet die Nachricht. Darüber hinaus können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen, um kerne Befehle zu definieren, auf die Ihr Bot antwortet. Bots in einer Gruppe oder einem Kanal empfangen nachrichten nur, wenn sie @botname. Teams sendet Benachrichtigungen an Ihren Bot für Unterhaltungsereignisse, die in Bereiche auftreten, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse in Ihrem Code erfassen und Aktionen für diese Ereignisse ergreifen. 

Ein Bot kann auch proaktive Nachrichten an Benutzer senden. Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht auf eine Anforderung eines Benutzers reagiert. Sie können Ihre Botnachrichten so formatieren, dass sie umfangreiche Karten enthalten, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video und so weiter enthalten. Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden. Nachrichten können auch mit der Bot Framework-Methode gelöscht `DeleteActivity` werden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Meldungen in Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-messages.md)
