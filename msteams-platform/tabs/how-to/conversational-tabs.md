---
title: Erstellen von Unterhaltungsregisterkarten
author: laujan
description: Erstellen von Unterhaltungsunterentitätschats für Ihre Kanalregisterkarten
keywords: Teams-Registerkartenkanal konfigurierbar
ms.topic: conceptual
ms.author: lomeybur
ms.openlocfilehash: 4171265a3ef4ad917661e258dd7305f82411c5ef
ms.sourcegitcommit: 118f7261d313feeac5b398fef56a44bd90104b2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2021
ms.locfileid: "52709646"
---
# <a name="create-conversational-tabs"></a>Erstellen von Unterhaltungsregisterkarten

Unterhaltungsunterentitäten bieten eine Möglichkeit, Benutzern zu ermöglichen, Unterhaltungen über Unterentitäten auf Ihrer Registerkarte zu führen, z. B. bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu besprechen, die auch als Entität bezeichnet wird. Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht es dem Benutzer, eine Unterhaltung über eine Registerkarte zu führen, aber der Benutzer möchte möglicherweise eine fokussierte Unterhaltung. Die Anforderung einer fokussierteren Unterhaltung kann entweder auftreten, wenn zu viel Inhalt für eine zentrale Diskussion vor sich geht oder der Inhalt im Laufe der Zeit geändert wird, was die Unterhaltung für den angezeigten Inhalt irrelevant macht. Unterhaltungsunterentitäten bieten eine viel fokussiertere Unterhaltungserfahrung für dynamische Registerkarten.

Unterhaltungsunterentitäten werden nur in Kanälen unterstützt. Sie können jedoch auf einer persönlichen oder statischen Registerkarte zum  Erstellen oder Fortsetzen von Unterhaltungen in Registerkarten verwendet werden, die bereits an einen Kanal angeheftet sind. Die statische Registerkarte ist hilfreich, wenn Sie einem Benutzer einen Ort zum Anzeigen und Zugreifen auf Unterhaltungen über mehrere Kanäle bereitstellen möchten.

## <a name="prerequisites"></a>Voraussetzungen

Um Unterhaltungsunterentitäten zu unterstützen, muss Ihre Registerkartenwebanwendung die Möglichkeit haben, eine Zuordnung zwischen Unterentitäten ↔ Unterhaltungen in einer Back-End-Datenbank zu speichern. Wir stellen Ihnen die zur Verfügung, aber es liegt in Ihrer Verantwortung, dies zu speichern und an Teams zurück, damit Benutzer `conversationId` `conversationId` die Unterhaltung fortsetzen können.

## <a name="start-a-new-conversation"></a>Starten einer neuen Unterhaltung

Verwenden Sie die Funktion, um eine neue Unterhaltung zu `openConversation()` starten. Das Starten und Fortsetzen einer Unterhaltung wird von dieser Methode behandelt, die Eingaben für die Funktion ändern sich jedoch je nach der Aktion, die Sie ergreifen möchten. Aus Benutzersicht wird dadurch der Unterhaltungsbereich rechts neben dem Bildschirm geöffnet, um eine Unterhaltung zu initiieren oder eine Unterhaltung weiter zu führen.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:

* **subEntityId**: Dies ist die ID Ihrer bestimmten Unterentität. Beispiel: task-123.
* **entityId**: Dies ist die ID der Registerkarteninstanz, als sie erstellt wurde. Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zurück verweisen.
* **channelId**: Dies ist der Kanal, in dem sich die Registerkarteninstanz befindet.
   > [!NOTE]
   > Die **channelId** ist optional für Kanalregisterkarten. Es wird jedoch empfohlen, die Implementierung kanal- und statisch gleich zu halten.
* **title**: Dies ist der Titel, der dem Benutzer im Chatbereich angezeigt wird.

Die meisten dieser Werte können auch aus der API abgerufen `getContext` werden.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

Dadurch wird der Unterhaltungsbereich geöffnet.

![Conversationl Sub Entities – Unterhaltung starten](~/assets/images/tabs/conversational-subentities/start-conversation.png)

Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die conversationId abzurufen und **zu speichern:**

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

Das `conversationReponse` Objekt enthält Informationen im Zusammenhang mit der Unterhaltung, die gerade gestartet wurde. Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Wiederverwendung zu speichern.

## <a name="continue-a-conversation"></a>Fortsetzen einer Unterhaltung

Nachdem eine Unterhaltung gestartet wurde, müssen Sie für nachfolgende Aufrufe auch die gleichen Eingaben wie unter Starten einer neuen Kanalregisterkarten-Unterhaltung bereitstellen, aber auch `openConversation()` **die conversationId enthalten.** [](#Starting a new channel tab conversation) Der Unterhaltungsbereich wird für den Benutzer geöffnet, in dem die entsprechende Unterhaltung angezeigt wird. Benutzer können neue oder eingehende Nachrichten in Echtzeit anzeigen.

![Conversationl Sub Entities – Unterhaltung fortsetzen](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a>Verbessern einer Unterhaltung

Schließlich ist es wichtig, dass Ihre Registerkarte [Deeplinks zu Ihrer Unterentität verwendet.](~/concepts/build-and-test/deep-links.md) Beispielsweise klickt der Benutzer in der Kanal-Unterhaltung auf die Registerkartenschickslet-Deeplink. Das erwartete Verhalten ist, dass Sie den Deeplink erhalten, diese Unterentität öffnen und dann den Unterhaltungsbereich für diese bestimmte Unterentität öffnen.

Um Unterhaltungsunterentitäten von Ihrer persönlichen oder statischen Registerkarte zu unterstützen, müssen Sie nichts an Ihrer Implementierung ändern. Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen auf Kanalregisterkarten, die bereits angeheftet sind. Durch die Unterstützung statischer Registerkarten können Sie ihren Benutzern einen einzigen Speicherort für die Interaktion mit allen Unterentitäten bereitstellen. Es ist jedoch wichtig, dass Sie die , speichern und wenn Ihre Registerkarte ursprünglich in einem Kanal erstellt wurde, damit Sie beim Öffnen der Unterhaltungsansicht auf einer statischen Registerkarte die richtigen Eigenschaften `subEntityId` `entityId` `channelId` haben.

## <a name="close-a-conversation"></a>Schließen einer Unterhaltung

Sie können die Unterhaltungsansicht manuell schließen, indem Sie die Funktion `closeConversation()` aufrufen.

```javascript
microsoftTeams.conversations.closeConversation();
```

Sie können auch auf ein Ereignis lauschen, wenn die Unterhaltungsansicht von einem Benutzer geschlossen wird.

```javascript
microsoftTeams.conversations.onCloseConversation = (conversationResponse) => {
    // console.log(conversationResponse)
};
```
