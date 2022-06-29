---
title: Registerkarten für Unterhaltungen erstellen
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Unterhaltungsunterentitätschats für Ihre Kanalregisterkarten erstellen und Unterhaltungen mithilfe von Codebeispielen verwalten.
ms.topic: conceptual
ms.author: lomeybur
ms.localizationpriority: medium
ms.openlocfilehash: 56fa54f1a8aa9dce9ba049ae300099c0c67ae263
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485674"
---
# <a name="create-conversational-tabs"></a>Registerkarten für Unterhaltungen erstellen

Conversational subentities provide a way to allow users to have conversations about subentities in your tab. Wie z. B. bestimmte Aufgaben, Patienten und Verkaufschancen, anstatt die gesamte Registerkarte zu besprechen, auch als Entität bezeichnet. Ein herkömmlicher Kanal oder eine konfigurierbare Registerkarte ermöglicht es dem Benutzer, eine Unterhaltung über eine Registerkarte zu führen, der Benutzer benötigt jedoch eine fokussiertere Unterhaltung. Die Anforderung für eine fokussiertere Unterhaltung kann entweder entstehen, wenn zu viele Inhalte vorhanden sind, um eine zentrale Diskussion zu führen, oder weil sich der Inhalt im Laufe der Zeit geändert hat, wodurch die Unterhaltung für den angezeigten Inhalt irrelevant ist. Unterhaltungsunterentitäten bieten eine viel fokussiertere Unterhaltungserfahrung für dynamische Registerkarten.

Unterhaltungsunterentitäten werden nur in Kanälen unterstützt. Sie können von einer persönlichen oder statischen Registerkarte aus verwendet werden, um Unterhaltungen in Registerkarten zu erstellen oder fortzusetzen, die bereits an einen Kanal angeheftet sind. Die statische Registerkarte ist nützlich, wenn Sie einem Benutzer einen Ort zum Anzeigen und Zugreifen auf Unterhaltungen über mehrere Kanäle bereitstellen möchten.

## <a name="prerequisites"></a>Voraussetzungen

Um Unterhaltungsunterentitäten zu unterstützen, muss Ihre Registerkartenwebanwendung die Möglichkeit haben, eine Zuordnung zwischen Unterentitäten-Unterhaltungen ↔ in einer Back-End-Datenbank zu speichern. Das `conversationId` wird bereitgestellt, aber Sie müssen es `conversationId` speichern und an Teams zurückgeben, damit Benutzer die Unterhaltung fortsetzen können.

## <a name="start-a-new-conversation"></a>Starten einer neuen Unterhaltung

Verwenden Sie die `openConversation()` Funktion, um eine neue Unterhaltung zu beginnen. Das Starten und Fortsetzen einer Unterhaltung wird mit dieser Methode behandelt. Die Eingaben für die Funktion ändern sich, je nachdem, welche Aktion Sie aus Benutzersicht ausführen möchten. Dadurch wird der Unterhaltungsbereich rechts neben dem Bildschirm geöffnet, um entweder eine Unterhaltung zu initiieren oder eine Unterhaltung fortzusetzen.

``` javascript
microsoftTeams.conversations.openConversation(openConversationRequest);
```

**openConversation** verwendet die folgenden Eingaben, um eine Unterhaltung in einem Kanal zu starten:

* **subEntityId**: Die ID Ihrer spezifischen Unterentität. Beispiel: Task-123.
* **entityId**: Die ID der Registerkarteninstanz, als sie erstellt wurde. Die ID ist wichtig, um auf dieselbe Registerkarteninstanz zurück zu verweisen.
* **channelId**: Der Kanal, in dem sich die Registerkarteninstanz befindet.
   > [!NOTE]
   > Die **channelId** ist für Kanalregisterkarten optional. Es wird jedoch empfohlen, die Implementierung über Kanal- und statische Registerkarten hinweg beizubehalten.
* **Titel**: Der Titel, der dem Benutzer im Chatbereich angezeigt wird.

Die meisten dieser Werte können auch aus der `getContext` API abgerufen werden.

```javascript
microsoftTeams.conversations.openConversation({“subEntityId”:”task-1”, “entityId”: “tabInstanceId-1”, “channelId”: ”19:baa6e71f65b948d189bf5c892baa8e5a@thread.skype”, “title”: "Task Title”});
```

Die folgende Abbildung zeigt den Unterhaltungsbereich:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/start-conversation.png" alt-text="Unterhaltungen starten":::

Wenn der Benutzer eine Unterhaltung startet, ist es wichtig, auf den Rückruf dieses Ereignisses zu lauschen, um die **conversationId** abzurufen und zu speichern:

```javascript
microsoftTeams.conversations.onStartConversation = (conversationResponse) => {
    // console.log(conversationReponse.conversationId)
};
```

Das `conversationResponse` Objekt enthält Informationen im Zusammenhang mit der Unterhaltung, die gestartet wurde. Es wird empfohlen, alle Eigenschaften dieses Antwortobjekts zur späteren Verwendung zu speichern.

## <a name="continue-a-conversation"></a>Fortsetzen einer Unterhaltung

Nachdem eine Unterhaltung gestartet wurde, müssen nachfolgende Aufrufe `openConversation()` erforderlich sein, dass Sie auch dieselben Eingaben wie beim [Starten einer neuen Unterhaltung](#start-a-new-conversation) bereitstellen, aber auch die **conversationId** einschließen. Der Unterhaltungsbereich wird für die Benutzer mit der entsprechenden Unterhaltung geöffnet. Benutzer können neue oder eingehende Nachrichten in Echtzeit sehen.

Die folgende Abbildung zeigt den Unterhaltungsbereich mit der entsprechenden Unterhaltung:

:::image type="content" source="../../assets/images/tabs/conversational-subentities/continue-conversation.png" alt-text="Unterhaltungen fortsetzen":::

## <a name="enhance-a-conversation"></a>Verbessern einer Unterhaltung

Es ist wichtig, dass Ihre Registerkarte [Deep-Links zu Ihrer Unternubentität](~/concepts/build-and-test/deep-links.md) enthält. Beispielsweise wählt der Benutzer den Registerkarten-Chiclet-Deep-Link aus der Kanalunterhaltung aus. Das erwartete Verhalten besteht darin, den Deep-Link zu empfangen, diese Unterentität zu öffnen und dann den Unterhaltungsbereich für diese Unterentität zu öffnen.The expected behavior is to receive the deep link, open that subentity, and then open the conversation panel for that subentity.

Um Unterhaltungsunterentitäten von Ihrer persönlichen oder statischen Registerkarte zu unterstützen, müssen Sie in Ihrer Implementierung nichts ändern. Wir unterstützen nur das Starten oder Fortsetzen von Unterhaltungen über Kanalregisterkarten, die bereits angeheftet sind. Durch die Unterstützung statischer Registerkarten können Sie ihren Benutzern einen einzigen Speicherort für die Interaktion mit allen Ihren Unterentitäten bereitstellen. Es ist wichtig, dass Sie die `subEntityId``entityId`Registerkarte speichern und `channelId` wenn Ihre Registerkarte ursprünglich in einem Kanal erstellt wurde, um die richtigen Eigenschaften zu haben, wenn Sie die Unterhaltungsansicht auf einer statischen Registerkarte öffnen.

## <a name="close-a-conversation"></a>Schließen einer Unterhaltung

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
|Registerkarte "Unterhaltung erstellen"| Beispiel-App für die Microsoft Teams-Registerkarte zum Demonstrieren der Registerkarte "Unterhaltung erstellen". | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/csharp) |  [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-conversations/nodejs) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Änderungen am Registerkartenrand](~/resources/removing-tab-margins.md)

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
