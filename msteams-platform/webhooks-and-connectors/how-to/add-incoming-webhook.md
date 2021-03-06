---
title: Senden externer Anfragen an Microsoft Teams mit eingehenden Webhooks
author: laujan
description: Hinzufügen eines eingehenden Webhooks zur Teams-App
keywords: Teams-Registerkarte „Ausgehender Webhook“*
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a05f9ec448a722f3d662a8323a40ebe6b2de1e27
ms.sourcegitcommit: 23ceb25d07a76f03ffe92cf1ac578b7c50b0bafc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777917"
---
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Senden externer Anfragen an Microsoft Teams mit eingehenden Webhooks

## <a name="what-are-incoming-webhooks-in-teams"></a>Was sind eingehende Webhooks in Teams?

Bei eingehenden Webhooks handelt es sich um eine spezielle Art von Connectors in Microsoft Teams, die eine einfache Möglichkeit für externe Apps zum Freigeben von Inhalten in Teamkanälen bieten und häufig als Nachverfolgungs- und Benachrichtigungstools verwendet werden. Teams stellt eine eindeutige URL bereit, an die Sie eine JSON-Nutzlast mit der Nachricht senden, die Sie etwas senden (POST) möchten, typischerweise in einem Kartenformat. Karten sind Benutzeroberflächencontainer, die Inhalte und Aktionen zu einem bestimmten Thema enthalten und eine Möglichkeit darstellen, Nachrichtendaten auf einheitliche Weise zu präsentieren. Teams verwendet Karten in von drei Funktionen:

* Bots
* Messaging-Erweiterungen
* Connectors

## <a name="incoming-webhook-key-features"></a>Wichtige Features eingehender Webhooks

| Feature | Beschreibung |
| ------- | ----------- |
|Konfigurationsbereich|Eingehende Webhooks werden auf Kanalebene festgelegt und konfiguriert (im Gegensatz zu ausgehenden Webhooks, die auf Teamebene festgelegt und konfiguriert werden).|
|Sichere Ressourcendefinitionen|Nachrichten werden als JSON-Nutzlast formatiert. Diese deklarative Nachrichtenstruktur verhindert die Einschleusung von bösartigem Code, da auf dem Client keine Codeausführung stattfindet.|
|Unterstützung für Aktion erfordernde Nachrichten|Wenn Sie festlegen, dass Nachrichten als Karten gesendet werden sollen, müssen Sie das Format für **Aktion erfordernde Nachrichtenkarten** verwenden. Aktion erfordernde Nachrichtenkarten werden in allen Office 365-Gruppen einschließlich Microsoft Teams unterstützt. Hier sind Links zur [Referenz zu Legacy-Nachrichtenkarten mit Aktionen](/outlook/actionable-messages/message-card-reference)und zum [Nachrichtenkarten-Playground](https://messagecardplayground.azurewebsites.net).|
|Unabhängige HTTPS-Messaging-Unterstützung| Karten sind eine großartige Möglichkeit, Informationen in einer übersichtlichen und einheitlichen Weise darzustellen. Jedes Tool oder Framework, das HTTPS-POST-Anforderungen senden kann, kann über einen eingehenden Webhook Nachrichten an Microsoft Teams senden.|
|Markdown-Unterstützung|Alle Textfelder in Aktion erfordernden Nachrichtenkarten unterstützen grundlegendes Markdown. **Verwenden Sie in Ihren Karten kein HTML-Markup.** HTML wird ignoriert und als reiner Text behandelt.|

> [!Note]
> Teams-Bots, Messaging-Erweiterungen, eingehende Webhooks und das Bot-Framework unterstützen adaptive Karten, ein offenes, plattformübergreifendes Framework. [Teams-Connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) unterstützen derzeit keine adaptiven Karten. Es ist jedoch möglich, einen [Fluss](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) zu erstellen, der adaptive Karten an einen Teams-Kanal sendet.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Hinzufügen eines eingehenden Webhooks zu einem Teams-Kanal

> [!Important]  
> Wenn in Ihrem Team unter **Einstellungen** => **Mitgliederberechtigungen** => **Mitgliedern das Erstellen, Aktualisieren und Entfernen von Connectors erlauben** ausgewählt ist, kann jedes Teammitglied einen Connector hinzufügen, ändern oder löschen.

1. Navigieren Sie zu dem Kanal, dem Sie den Webhook hinzufügen möchten, und wählen Sie (&#8226;&#8226;&#8226;) *Weitere Optionen* in der oberen Navigationsleiste aus.
1. Suchen Sie im Dropdownmenü **Connectors** nach **Eingehender Webhook**.
1. Wählen Sie die Schaltfläche **Konfigurieren** aus, geben Sie einen Namen ein, und laden Sie optional einen Avatar für Ihren Webhook hoch.
1. Im Dialogfeld wird eine eindeutige URL angezeigt, die dem Kanal zugeordnet ist. Stellen Sie sicher, dass Sie die **URL kopieren und speichern**, da Sie diese dem externen Dienst zur Verfügung stellen müssen.
1. Klicken Sie auf die Schaltfläche **Fertig**. Der Webhook ist nun im Teamkanal verfügbar.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Entfernen eines eingehenden Webhooks aus einem Teams-Kanal

1. Navigieren Sie zu dem Kanal, dem der Webhook hinzugefügt wurde, und wählen Sie (&#8226;&#8226;&#8226;) *Weitere Optionen* in der oberen Navigationsleiste aus.
1. Wählen Sie im Dropdownmenü die Option **Connectors** aus.
1. Wählen Sie auf der linken Seite unter **Verwalten** die Option **Konfiguriert** aus.
1. Wählen Sie *Zahl konfiguriert* aus, um eine Liste Ihrer aktuellen Connectors zu sehen.
1. Wählen Sie **Verwalten** neben dem Connector aus, den Sie löschen möchten.
1. Wählen Sie die Schaltfläche **Entfernen** aus, und ein Dialogfeld *Konfiguration entfernen* wird angezeigt.
1. Füllen Sie optional die Felder und Kontrollkästchen des Dialogfelds aus, bevor Sie die Schaltfläche **Entfernen** auswählen. Der Webhook wird aus dem Teamkanal gelöscht.

## <a name="distribution"></a>Verteilung

Sie haben drei Möglichkeiten, Ihren eingehenden Webhook zu verteilen:

* Richten Sie einen eingehenden Webhook direkt für Ihr Team ein.
* Fügen Sie eine Konfigurationsseite hinzu, und verpacken Sie Ihren eingehenden Webhook in einen [O365 Connector](~/webhooks-and-connectors/how-to/connectors-creating.md).
* Verpacken und veröffentlichen Sie Ihren Connector als Teil Ihrer [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md)-Übermittlung.

## <a name="learn-more"></a>Weitere Informationen

* [Senden von Nachrichten an Connectors und Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md)
