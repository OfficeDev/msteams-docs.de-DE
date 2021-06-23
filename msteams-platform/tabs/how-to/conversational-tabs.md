---
title: Registerkarten für Unterhaltungen erstellen
author: surbhigupta
description: Erstellen eines Unterhaltungsunterentitätschats für Ihre Kanalregisterkarten
keywords: Kanal "Teams-Registerkarten" konfigurierbar
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: 343cbe26ded2792489640ae3d86ec94c7c6db72b
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069230"
---
# <a name="create-conversational-tabs"></a>Registerkarten für Unterhaltungen erstellen

Unterhaltungsunterentitäten bieten eine Möglichkeit, Benutzern zu ermöglichen, Unterhaltungen über Unterentitäten auf Ihrer Registerkarte zu führen, z. B. bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu besprechen, die auch als Entität bezeichnet wird. Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht es dem Benutzer, eine Unterhaltung über eine Registerkarte zu führen, aber der Benutzer möchte möglicherweise eine fokussiertere Unterhaltung. Die Anforderung für eine fokussiertere Unterhaltung kann entweder auftreten, wenn zu viele Inhalte vorhanden sind, um eine zentrale Diskussion zu führen, oder wenn sich der Inhalt im Laufe der Zeit ändert, wodurch die Unterhaltung für die angezeigten Inhalte irrelevant wird. Unterhaltungsunterentitäten bieten eine viel fokussiertere Unterhaltungserfahrung für dynamische Registerkarten.

Unterhaltungsunterentitäten werden nur in Kanälen unterstützt. Sie können jedoch von einer persönlichen oder statischen Registerkarte verwendet werden, um Unterhaltungen in Registerkarten zu erstellen oder fortzusetzen, die *bereits* an einen Kanal angeheftet sind. Die statische Registerkarte ist nützlich, wenn Sie einen Ort für einen Benutzer bereitstellen möchten, um Unterhaltungen über mehrere Kanäle anzuzeigen und darauf zuzugreifen.

## <a name="prerequisites"></a>Voraussetzungen

Um Unterhaltungsunterentitäten zu unterstützen, muss Ihre Registerkartenwebanwendung in der Lage sein, eine Zuordnung zwischen Unterentitäten ↔ Unterhaltungen in einer Back-End-Datenbank zu speichern. Wir stellen Ihnen dies zur `conversationId` Verfügung, aber es ist In Ihrer Verantwortung, diese zu speichern `conversationId` und an Teams zurückzugeben, damit Benutzer die Unterhaltung fortsetzen können.

## <a name="start-a-new-conversation"></a>Starten einer neuen Unterhaltung

Zum Starten einer neuen Unterhaltung verwenden Sie die `openConversation()` Funktion. Das Starten und Fortsetzen einer Unterhaltung wird von dieser Methode verarbeitet. Die Eingaben für die Funktion ändern sich jedoch je nachdem, welche Aktion Sie ausführen möchten. Aus Sicht der Benutzer wird dadurch der Unterhaltungsbereich rechts vom Bildschirm geöffnet, um entweder eine Unterhaltung zu initiieren oder eine Unterhaltung fortzusetzen.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:

* **subEntityId:** Dies ist die ID Ihrer spezifischen Unterentität. Beispiel: Task-123.
* **entityId:** Dies ist die ID der Registerkarteninstanz, als sie erstellt wurde. Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zurück zu verweisen.
* **channelId:** Dies ist der Kanal, in dem sich die Registerkarteninstanz befindet.
   > [!NOTE]
   > Die **channelId** ist optional für Kanalregisterkarten. Es wird jedoch empfohlen, die Implementierung kanalübergreifend und auf statischen Registerkarten gleich zu halten.
* **title:** Dies ist der Titel, der dem Benutzer im Chatbereich angezeigt wird.

Die meisten dieser Werte können auch aus der API abgerufen `getContext` werden.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

Dadurch wird der Unterhaltungsbereich geöffnet.

![Conversationl-Unterentitäten – Unterhaltung starten](~/assets/images/tabs/conversational-subentities/start-conversation.png)

Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die **conversationId** abzurufen und zu speichern:

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

Das `conversationReponse` Objekt enthält Informationen zu der Gerade gestarteten Unterhaltung. Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Wiederverwendung zu speichern.

## <a name="continue-a-conversation"></a>Unterhaltung fortsetzen

Nachdem eine Unterhaltung gestartet wurde, müssen Sie bei nachfolgenden Aufrufen `openConversation()` auch die gleichen Eingaben wie beim Starten einer [neuen Kanalregisterkartenunterhaltung](#Starting a new channel tab conversation)angeben, aber auch die **conversationId** einschließen. Der Unterhaltungsbereich wird für den Benutzer geöffnet, in dem die entsprechende Unterhaltung angezeigt wird. Benutzer können neue oder eingehende Nachrichten in Echtzeit sehen.

![Conversationl-Unterentitäten – Unterhaltung fortsetzen](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a>Verbessern einer Unterhaltung

Schließlich ist es wichtig, dass Ihre Registerkarte [Deeplinks zu Ihrer Unterentität](~/concepts/build-and-test/deep-links.md)verwendet. Der Benutzer klickt z. B. in der Kanalunterhaltung auf den Deeplink des Registerkarten-Tabstopps. Das erwartete Verhalten ist, dass Sie den Deeplink erhalten, diese Unterentität öffnen und dann den Unterhaltungsbereich für diese bestimmte Unterentität öffnen.

Um Unterhaltungsunterentitäten von Ihrer persönlichen oder statischen Registerkarte zu unterstützen, müssen Sie nichts an Ihrer Implementierung ändern. Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen über Kanalregisterkarten, die bereits angeheftet sind. Die Unterstützung statischer Registerkarten ermöglicht es Ihnen, einen einzelnen Speicherort für Ihre Benutzer bereitzustellen, um mit allen Ihren Unterentitäten zu interagieren. Es ist jedoch wichtig, dass Sie die Registerkarte speichern `subEntityId` und wann die Registerkarte ursprünglich in einem Kanal erstellt `entityId` `channelId` wurde, damit Sie die richtigen Eigenschaften haben, wenn Sie die Unterhaltungsansicht auf einer statischen Registerkarte öffnen.

## <a name="close-a-conversation"></a>Beenden einer Unterhaltung

Sie können die Unterhaltungsansicht manuell schließen, indem Sie die `closeConversation()` Funktion aufrufen.

```javascript
microsoftTeams.conversations.closeConversation();
```

Sie können auch auf ein Ereignis lauschen, wenn die Unterhaltungsansicht von einem Benutzer geschlossen wird.

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```
