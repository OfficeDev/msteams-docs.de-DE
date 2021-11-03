---
title: Registerkarten für Unterhaltungen erstellen
author: surbhigupta
description: Erstellen eines Unterhaltungsunterunterhaltungschats für Ihre Kanalregisterkarten
keywords: Kanal "Teams-Registerkarten" konfigurierbar
ms.topic: conceptual
ms.author: lomeybur
ms.localizationpriority: none
ms.openlocfilehash: 7426ca8d994a9009b05e5a3eece05d4938f07f80
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720372"
---
# <a name="create-conversational-tabs"></a>Registerkarten für Unterhaltungen erstellen

Unterhaltungsunterentitäten bieten eine Möglichkeit, Benutzern zu ermöglichen, Unterhaltungen zu Untergeordneten Aufzählungen auf Ihrer Registerkarte zu führen. Wie z. B. bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu besprechen, die auch als Entität bezeichnet wird. Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht dem Benutzer eine Unterhaltung über eine Registerkarte, aber der Benutzer erfordert eine gezielte unterhaltung. Die Anforderung für eine fokussiertere Unterhaltung kann entweder auftreten, wenn zu viele Inhalte vorhanden sind, um eine zentrale Diskussion zu führen, oder weil sich der Inhalt im Laufe der Zeit geändert hat, wodurch die Unterhaltung für den angezeigten Inhalt irrelevant wird. Unterhaltungsunterteilungen bieten eine viel fokussiertere Unterhaltungserfahrung für dynamische Registerkarten.

Unterhaltungsunterteilungen werden nur in Kanälen unterstützt. Sie können von einer persönlichen oder statischen Registerkarte verwendet werden, um Unterhaltungen in Registerkarten zu erstellen oder fortzusetzen, die bereits an einen Kanal angeheftet sind. Die statische Registerkarte ist nützlich, wenn Sie einen Ort für einen Benutzer bereitstellen möchten, an dem Unterhaltungen über mehrere Kanäle hinweg angezeigt und darauf zugegriffen werden kann.

## <a name="prerequisites"></a>Voraussetzungen

Um Unterhaltungsunterhaltungen zu unterstützen, muss Ihre Registerkartenwebanwendung in der Lage sein, eine Zuordnung zwischen Untergeordneten ↔ Unterhaltungen in einer Back-End-Datenbank zu speichern. Die `conversationId` wird bereitgestellt, aber Sie müssen dies speichern `conversationId` und an Teams zurückgeben, damit Benutzer die Unterhaltung fortsetzen können.

## <a name="start-a-new-conversation"></a>Starten einer neuen Unterhaltung

Verwenden Sie die Funktion, um eine neue Unterhaltung zu `openConversation()` starten. Das Starten und Fortsetzen einer Unterhaltung wird von dieser Methode verarbeitet. Die Eingaben für die Funktion ändern sich je nachdem, welche Aktion Sie aus Sicht des Benutzers ausführen möchten. Dadurch wird der Unterhaltungsbereich rechts vom Bildschirm geöffnet, um eine Unterhaltung zu initiieren oder eine Unterhaltung fortzusetzen.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:

* **subEntityId:** Die ID Ihrer spezifischen Unterentität. Beispiel: Task-123.
* **entityId:** Die ID der Registerkarteninstanz, als sie erstellt wurde. Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zurück zu verweisen.
* **channelId:** Der Kanal, in dem sich die Registerkarteninstanz befindet.
   > [!NOTE]
   > Die **channelId** ist optional für Kanalregisterkarten. Es wird jedoch empfohlen, die Implementierung kanalübergreifend und auf statischen Registerkarten gleich zu halten.
* **title**: Der Titel, der dem Benutzer im Chatbereich angezeigt wird.

Die meisten dieser Werte können auch aus der API abgerufen `getContext` werden.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

Die folgende Abbildung zeigt den Unterhaltungsbereich:

![Unterhaltungsunterentitäten – Unterhaltung starten](~/assets/images/tabs/conversational-subentities/start-conversation.png)

Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die **conversationId** abzurufen und zu speichern:

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

Das `conversationResponse` Objekt enthält Informationen zu der unterhaltung, die gestartet wurde. Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Verwendung zu speichern.

## <a name="continue-a-conversation"></a>Unterhaltung fortsetzen

Nachdem eine Unterhaltung gestartet wurde, müssen nachfolgende Aufrufe `openConversation()` erforderlich sein, dass Sie auch die gleichen Eingaben wie beim [Starten einer neuen Unterhaltung](#start-a-new-conversation)angeben, aber auch die **conversationId** einschließen. Der Unterhaltungsbereich wird für die Benutzer geöffnet, für die die entsprechende Unterhaltung angezeigt wird. Benutzer können neue oder eingehende Nachrichten in Echtzeit sehen.

Die folgende Abbildung zeigt den Unterhaltungsbereich mit der entsprechenden Unterhaltung:

![Unterhaltungsunterentitäten – Unterhaltung fortsetzen](~/assets/images/tabs/conversational-subentities/continue-conversation.png)

## <a name="enhance-a-conversation"></a>Verbessern einer Unterhaltung

Es ist wichtig, dass Ihre Registerkarte [Deep-Links zu Ihrer Unterentität](~/concepts/build-and-test/deep-links.md)enthält. Der Benutzer wählt z. B. den Tabstopp-Deep-Link aus der Kanalunterhaltung aus. Das erwartete Verhalten besteht darin, den Deep-Link zu erhalten, diese Subentität zu öffnen und dann den Unterhaltungsbereich für diese Subentität zu öffnen.

Um unterhaltungsbezogene Subentitäten von Ihrer persönlichen oder statischen Registerkarte zu unterstützen, müssen Sie in Ihrer Implementierung nichts ändern. Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen über Kanalregisterkarten, die bereits angeheftet sind. Die Unterstützung statischer Registerkarten ermöglicht es Ihnen, ihren Benutzern einen einzelnen Speicherort für die Interaktion mit allen Ihren Unterteilungen bereitzustellen. Es ist wichtig, dass Sie die Registerkarte speichern `subEntityId` und wenn die Registerkarte ursprünglich in einem Kanal erstellt `entityId` `channelId` wurde, um die richtigen Eigenschaften zu haben, wenn Sie die Unterhaltungsansicht in einer statischen Registerkarte öffnen.

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

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Registerkarte "Unterhaltung erstellen"| Microsoft Teams Registerkarten-Beispiel-App zum Demonstrieren der Registerkarte "Unterhaltung erstellen". | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/csharp) |  [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/nodejs) |

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Änderungen am Registerkartenrand](~/resources/removing-tab-margins.md)
