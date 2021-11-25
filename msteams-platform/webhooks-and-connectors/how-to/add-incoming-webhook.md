---
title: Erstellen eines eingehenden Webhooks
author: laujan
description: beschreibt, wie eingehende Webhooks zu Teams App hinzugefügt und externe Anforderungen an Teams mit eingehenden Webhooks gesendet werden.
keywords: Teams-Registerkarten für ausgehenden Webhook
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 7ce63a8456eaa0b15bd03999dd06c202ee689113
ms.sourcegitcommit: ba911ce3de7d096514f876faf00e4174444e2285
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2021
ms.locfileid: "61178300"
---
# <a name="create-incoming-webhook"></a>Erstellen eines eingehenden Webhooks

Mit eingehendem Webhook können externe Apps Inhalte in Teams Kanälen freigeben. Diese Webhooks werden als Tracking- und Benachrichtigungstools verwendet. Sie stellen eine eindeutige URL bereit, an die Sie eine JSON-Nutzlast mit einer Nachricht im Kartenformat senden. Karten sind Benutzeroberflächencontainer, die Inhalte und Aktionen im Zusammenhang mit einem einzelnen Thema enthalten. Teams Karten in den folgenden Funktionen verwenden:

* Bots
* Messaging-Erweiterungen
* Connectors

## <a name="key-features-of-incoming-webhook"></a>Wichtige Features des eingehenden Webhooks

Die folgende Tabelle enthält die Features und die Beschreibung des eingehenden Webhooks:

| Features | Beschreibung |
| ------- | ----------- |
|Adaptive Karten mit einem eingehenden Webhook|Adaptive Karten können über eingehende Webhooks gesendet werden. Weitere Informationen finden Sie unter [Senden adaptiver Karten mit eingehenden Webhooks.](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook)|
|Unterstützung für Aktion erfordernde Nachrichten|Aktion erfordernde Nachrichtenkarten werden in allen Office 365-Gruppen einschließlich Microsoft Teams unterstützt. Wenn Sie Nachrichten über Karten senden, müssen Sie das Kartenformat für Aktionen erfordernde Nachrichten verwenden. Weitere Informationen finden Sie unter [Legacy-Referenz für Nachrichtenkarten](/outlook/actionable-messages/message-card-reference) mit Aktionen und [Nachrichtenkarten-Playground.](https://messagecardplayground.azurewebsites.net)|
|Unabhängige HTTPS-Messaging-Unterstützung|Karten stellen Informationen klar und konsistent bereit. Jedes Tool oder Framework, das HTTPS POST-Anforderungen senden kann, kann Nachrichten über einen eingehenden Webhook an Teams senden.|
|Markdown-Unterstützung|Alle Textfelder in Aktion erfordernden Nachrichtenkarten unterstützen grundlegendes Markdown. Verwenden Sie kein HTML-Markup in Ihren Karten. HTML wird ignoriert und als reiner Text behandelt.|
|Bereichskonfiguration|Eingehender Webhook ist auf Kanalebene beschränkt und konfiguriert.|
|Sichere Ressourcendefinitionen|Nachrichten werden als JSON-Nutzlast formatiert. Diese deklarative Messagingstruktur verhindert das Einfügen von schädlichem Code.|

> [!NOTE]
> * Teams Bots, Messaging-Erweiterungen, eingehender Webhook und bot Framework unterstützen adaptive Karten. Adaptive Karten sind ein offenes kartenübergreifendes Plattformframework, das auf allen Plattformen wie Windows, Android, iOS usw. verwendet werden kann. Derzeit unterstützen [Teams Connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) keine adaptiven Karten. Es ist jedoch möglich, einen [Fluss](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) zu erstellen, der adaptive Karten an einen Teams-Kanal sendet.
> * Weitere Informationen zu Karten und Webhooks finden Sie unter [Adaptive Karten und eingehende Webhooks.](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks)

## <a name="create-incoming-webhook"></a>Erstellen eines eingehenden Webhooks

**So fügen Sie einem Teams Kanal einen eingehenden Webhook hinzu**

1. Wechseln Sie zu dem Kanal, in dem Sie den Webhook hinzufügen möchten, und wählen Sie &#8226;&#8226;&#8226; **Weitere Optionen** in der oberen Navigationsleiste aus.
1. Wählen Sie **connectors** aus dem Dropdownmenü aus:

    ![Connector auswählen](~/assets/images/connectors.png)

1. Suchen Sie nach **eingehendem Webhook,** und wählen Sie **"Hinzufügen"** aus.
1. Wählen Sie **"Konfigurieren",** geben Sie einen Namen an, und laden Sie bei Bedarf ein Bild für Ihren Webhook hoch:

    ![Schaltfläche "Konfigurieren"](~/assets/images/configure.png)

1. Im Dialogfeld wird eine eindeutige URL angezeigt, die dem Kanal zugeordnet ist. Kopieren und speichern Sie die Webhook-URL, um Informationen an Microsoft Teams zu senden und **"Fertig"** auszuwählen:

    ![Eindeutige URL](~/assets/images/url.png)

Der Webhook ist im Teams Kanal verfügbar.

> [!NOTE]
> Wählen Sie in Teams **Einstellungen**  >  **Mitgliedsberechtigungen** aus, damit Mitglieder Connectors  >  **erstellen, aktualisieren und entfernen können,** damit jedes Teammitglied einen Connector hinzufügen, ändern oder löschen kann.

## <a name="remove-incoming-webhook"></a>Entfernen des eingehenden Webhooks

**So entfernen Sie einen eingehenden Webhook aus einem Teams Kanal**

1. Wechseln Sie zum Kanal.
1. Wählen Sie in der oberen Navigationsleiste &#8226;&#8226;&#8226; **Weitere Optionen** aus.
1. Wählen Sie im Dropdownmenü **Connectors** aus.
1. Wählen Sie auf der linken Seite unter **Verwalten** die Option **"Konfiguriert"** aus.
1. Wählen Sie die **< *1*> Konfiguriert aus,** um eine Liste Ihrer aktuellen Connectors anzuzeigen:

    ![Konfigurierter Webhook](~/assets/images/configured.png)

1. Wählen Sie neben dem Connector, den Sie entfernen möchten, die Option **"Verwalten"** aus:

    ![Verwalten von Webhook](~/assets/images/manage.png)

1. Wählen Sie **"Entfernen" aus:**

    ![Entfernen von Webhook](~/assets/images/remove.png)

    Das Dialogfeld Konfiguration **entfernen** wird angezeigt:

    ![Entfernen der Konfiguration](~/assets/images/removeconfiguration.png)

1. Füllen Sie die Felder und Kontrollkästchen des Dialogfelds aus, und wählen Sie **"Entfernen" aus:**

    ![Endgültiges Entfernen](~/assets/images/finalremove.png)

    Der Webhook wird aus dem Teams-Kanal entfernt.

## <a name="see-also"></a>Weitere Informationen

* [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Erstellen einer Schaltfläche zum Teilen in Microsoft Teams](../../concepts/build-and-test/share-to-teams.md#create-share-to-teams-button)
* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
