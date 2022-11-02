---
title: Registerkarten für Unterhaltungen erstellen
author: surbhigupta
description: Erfahren Sie, wie Sie Unterhaltungsregisterkarten in Microsoft Teams erstellen, um eine Unterhaltung zu starten, fortzusetzen, zu verbessern und zu schließen.
ms.topic: conceptual
ms.author: lomeybur
ms.localizationpriority: high
ms.openlocfilehash: fa54221a413b19704d80ec62feb1cf068e42d1a0
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820122"
---
# <a name="create-conversational-tabs"></a>Registerkarten für Unterhaltungen erstellen

Konversationsunterentitäten bieten eine Möglichkeit, Benutzern zu ermöglichen, Unterhaltungen über untergeordnete Entitäten auf Ihrer Registerkarte zu führen. Wie z. B. bestimmte Aufgabe, Patient und Verkaufschance, anstatt die gesamte Registerkarte zu diskutieren, auch als Entität bezeichnet. Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht es dem Benutzer, eine Unterhaltung über eine Registerkarte zu führen, aber der Benutzer benötigt eine fokussiertere Unterhaltung. Die Anforderung einer fokussierteren Unterhaltung kann entweder auftreten, wenn zu viel Inhalt vorhanden ist, um eine zentralisierte Diskussion zu führen, oder weil sich der Inhalt im Laufe der Zeit geändert hat, wodurch die Unterhaltung für den angezeigten Inhalt irrelevant wird. Untergeordnete Konversationen bieten eine viel fokussiertere Konversationserfahrung für dynamische Registerkarten.

Untergeordnete Konversationen werden nur in Kanälen unterstützt. Sie können auf einer persönlichen oder statischen Registerkarte verwendet werden, um Unterhaltungen in Registerkarten zu erstellen oder fortzusetzen, die bereits an einen Kanal angeheftet sind. Die statische Registerkarte ist nützlich, wenn Sie einen Speicherort für einen Benutzer zum Anzeigen und Zugreifen auf Unterhaltungen bereitstellen möchten, die über mehrere Kanäle hinweg stattfinden.

## <a name="prerequisites"></a>Voraussetzungen

Um untergeordnete Konversationen zu unterstützen, muss Ihre Tab-Webanwendung in der Lage sein, eine Zuordnung zwischen untergeordneten Konversationen ↔ in einer Back-End-Datenbank zu speichern. Wird `conversationId` bereitgestellt, aber Sie müssen diese `conversationId` speichern und an Teams zurückgeben, damit Benutzer die Unterhaltung fortsetzen können.

## <a name="start-a-new-conversation"></a>Starten einer neuen Unterhaltung

Verwenden Sie die `openConversation()` -Funktion, um eine neue Unterhaltung zu starten. Das Starten und Fortsetzen einer Konversation wird von dieser Methode verarbeitet. Die Eingaben für die Funktion ändern sich je nachdem, welche Aktion Sie ausführen möchten. Aus Sicht des Benutzers wird der Unterhaltungsbereich rechts vom Bildschirm geöffnet, um entweder eine Unterhaltung zu initiieren oder eine Unterhaltung fortzusetzen.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:

* **subEntityId**: Die ID Ihrer spezifischen untergeordneten Eigenschaft. Beispiel: Task-123.
* **entityId**: Die ID der Registerkarteninstanz, als sie erstellt wurde. Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zu verweisen.
* **channelId**: Der Kanal, in dem sich die Registerkarteninstanz befindet.
   > [!NOTE]
   > Die **channelId** ist für Kanalregisterkarten optional. Es wird jedoch empfohlen, wenn Sie Ihre Implementierung kanalübergreifend und statische Registerkarten unverändert lassen möchten.
* **title**: Der Titel, der dem Benutzer im Chatbereich angezeigt wird.

Die meisten dieser Werte können auch aus der [`app.getContext()`](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-getcontext&preserve-view=true) API abgerufen werden (`microsoftTeams.getContext()` in TeamsJS v1). Weitere Informationen finden Sie unter [PageInfo-Schnittstelle](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-pageinfo&preserve-view=true).

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

Die folgende Abbildung zeigt den Unterhaltungsbereich:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/start-conversation.png" alt-text="Unterhaltungen starten":::

Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die **conversationId** abzurufen und zu speichern:

```javascript
⁠microsoftTeams.conversations.openConversation({
    ...,
    onStartConversation: (conversationResponse) => {
        ⁠// console.log(conversationResponse)
    },
});
```

Das `conversationResponse` -Objekt enthält Informationen im Zusammenhang mit der konversation, die gestartet wurde. Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Verwendung zu speichern.

## <a name="continue-a-conversation"></a>Fortsetzen einer Unterhaltung

Nachdem eine Unterhaltung gestartet wurde, müssen Nachfolgende Aufrufe erfordern `openConversation()` , dass Sie auch die gleichen Eingaben wie beim [Starten einer neuen Unterhaltung](#start-a-new-conversation) bereitstellen, aber auch die **conversationId** einschließen. Der Unterhaltungsbereich wird für die Benutzer mit der entsprechenden Unterhaltung geöffnet. Benutzer können neue oder eingehende Nachrichten in Echtzeit anzeigen.

Die folgende Abbildung zeigt den Unterhaltungsbereich mit der entsprechenden Unterhaltung:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/continue-conversation.png" alt-text="Unterhaltungen fortsetzen":::

## <a name="enhance-a-conversation"></a>Verbessern einer Unterhaltung

Es ist wichtig, dass Ihre Registerkarte [Deep-Links zu Ihrer untergeordneten Instanz](~/concepts/build-and-test/deep-links.md) enthält. Ein Benutzer, der beispielsweise den Deep-Link "Chiclet" aus der Kanalunterhaltung auswählt. Das erwartete Verhalten besteht darin, den Deep-Link zu erhalten, diese untergeordnete Entität zu öffnen und dann den Konversationsbereich für diese Untergeordneten zu öffnen.

Um konversationsunterstützte Entitäten von Ihrer persönlichen oder statischen Registerkarte zu unterstützen, müssen Sie nichts an Ihrer Implementierung ändern. Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen von Kanalregisterkarten, die bereits angeheftet sind. Durch die Unterstützung statischer Registerkarten können Sie einen einzelnen Speicherort für Ihre Benutzer für die Interaktion mit allen untergeordneten Entitäten bereitstellen. Es ist wichtig, dass Sie , `subEntityId``entityId`und `channelId` speichern, wenn Ihre Registerkarte ursprünglich in einem Kanal erstellt wurde, um die richtigen Eigenschaften beim Öffnen der Unterhaltungsansicht auf einer statischen Registerkarte zu erhalten.

## <a name="close-a-conversation"></a>Schließen einer Unterhaltung

Sie können die Unterhaltungsansicht manuell schließen, indem Sie die `closeConversation()` -Funktion aufrufen.

```javascript
microsoftTeams.conversations.closeConversation();
```

Sie können auch auf ein Ereignis lauschen, wenn die Benutzer in der Unterhaltungsansicht **Schließen (X)** auswählen.

```javascript
⁠microsoftTeams.conversations.openConversation({
    ...,
    onCloseConversation: (conversationResponse) => {
        ⁠// console.log(conversationResponse)
    },
});
```

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Registerkarte "Unterhaltung erstellen"| Microsoft Teams-Registerkarten-Beispiel-App zur Veranschaulichung der Registerkarte "Unterhaltung erstellen". | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/nodejs) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Änderungen am Registerkartenrand](~/resources/removing-tab-margins.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](create-personal-tab.md)
* [Erstellen einer Kanalregisterkarte oder Gruppenregisterkarte](create-channel-group-tab.md)
* [Erstellen von Registerkarten mit adaptiven Karten](build-adaptive-card-tabs.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
