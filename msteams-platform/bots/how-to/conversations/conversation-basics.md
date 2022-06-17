---
title: Grundlagen zu Unterhaltungen
description: In diesem Modul lernen Sie Bot-Unterhaltungen in einem Kanal, persönlichen Chat und einer Gruppenchatumgebung in Teams kennen.
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 682555cadaeca5f50a942de98b2dcdd85ce0f6b2
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142920"
---
# <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams Bot und einem oder mehreren Benutzern gesendet werden. Die folgende Tabelle enthält die drei Arten von Unterhaltungen, die in Teams auch als Bereiche bezeichnet werden:

| Unterhaltungstyp | Beschreibung |
| ------- | ----------- |
| `channel` | Dieser Unterhaltungstyp ist für alle Mitglieder des Kanals sichtbar. |
| `personal` | Dieser Unterhaltungstyp umfasst Unterhaltungen zwischen Bots und einem einzelnen Benutzer. |
| `groupChat` | Dieser Unterhaltungstyp umfasst chatten zwischen einem Bot und zwei oder mehr Benutzern. Es ermöglicht Ihrem Bot auch in Besprechungschats. |

Ein Bot verhält sich je nach Unterhaltung, an der er beteiligt ist, unterschiedlich:

* Für Bots in Kanal- und Gruppenchatunterhaltungen muss der Benutzer den Bot @erwähnen, um ihn in einem Kanal aufzurufen.

* Bots in einer 1:1-Unterhaltung benötigen keine @mention. Alle vom Benutzer gesendeten Nachrichten werden an Ihren Bot weitergeleitet.

> [!NOTE]
> Bots können aktiviert werden, um alle Kanalnachrichten in einem Team zu empfangen, ohne mithilfe von RSC-Berechtigungen (Resource-Specific Consent) @mentioned zu werden. Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar. Weitere Informationen finden Sie unter ["Empfangen aller Kanalnachrichten mit RSC"](channel-messages-with-rsc.md).

Damit der Bot in einer bestimmten Unterhaltung oder einem bestimmten Bereich funktioniert, fügen Sie diesem Bereich im [App-Manifest](~/resources/schema/manifest-schema.md) Unterstützung hinzu.

Jede Nachricht in einer Bot-Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot, und der Bot verarbeitet die Nachricht. Um die wichtigsten Befehle zu definieren, auf die Ihr Bot reagiert, können Sie außerdem ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen. Bots in einer Gruppe oder einem Kanal empfangen Nachrichten nur, wenn sie @botname erwähnt werden. Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Unterhaltungsereignisse, die in Bereichen stattfinden, in denen Ihr Bot aktiv ist. Sie können diese Ereignisse in Ihrem Code erfassen und entsprechende Maßnahmen ergreifen.

Ein Bot kann auch proaktive Nachrichten an Benutzer senden. Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird und nicht auf eine Anforderung eines Benutzers reagiert. Sie können Ihre Bot-Nachrichten so formatieren, dass sie umfangreiche Karten enthalten, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video usw. enthalten. Der Bot kann Nachrichten nach dem Senden dynamisch aktualisieren, anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden. Nachrichten können auch mithilfe der Bot Framework-Methode `DeleteActivity` gelöscht werden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Meldungen in Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-messages.md)
