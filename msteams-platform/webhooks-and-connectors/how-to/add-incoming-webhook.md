---
title: Veröffentlichen externer Anforderungen an Microsoft Teams mit eingehenden Webhooks
author: laujan
description: So fügen Sie der Teams-App eingehenden Webhook hinzu
keywords: Teams tabs outgoing webhook*
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a05f9ec448a722f3d662a8323a40ebe6b2de1e27
ms.sourcegitcommit: 23ceb25d07a76f03ffe92cf1ac578b7c50b0bafc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777917"
---
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Veröffentlichen externer Anforderungen an Teams mit eingehenden Webhooks

## <a name="what-are-incoming-webhooks-in-teams"></a>Was sind eingehende Webhooks in Teams?

Eingehende Webhooks sind ein spezieller Connectortyp in Teams, der einer externen App eine einfache Möglichkeit zum Freigeben von Inhalten in Teamkanälen bietet und häufig als Nachverfolgungs- und Benachrichtigungstools verwendet wird. Teams stellt eine eindeutige URL zur Verfügung, an die Sie eine JSON-Nutzlast mit der Nachricht senden, die Sie posten möchten, in der Regel in einem Kartenformat. Karten sind Benutzeroberflächencontainer, die Inhalte und Aktionen im Zusammenhang mit einem einzelnen Thema enthalten und eine Möglichkeit zur konsistenten Benutzeroberfläche sind. Teams verwendet Karten innerhalb von drei Funktionen:

* Bots
* Messaging-Erweiterungen
* Connectors

## <a name="incoming-webhook-key-features"></a>Wichtige Features des eingehenden Webhooks

| Feature | Beschreibung |
| ------- | ----------- |
|Bereichskonfiguration|Eingehende Webhooks werden auf Kanalebene begrenzt und konfiguriert (z. B. ausgehende Webhooks sind auf Teamebene begrenzt und konfiguriert).|
|Sichere Ressourcendefinitionen|Nachrichten sind als JSON-Nutzlasten formatiert. Diese deklarative Messagingstruktur verhindert das Einfeinen von bösartigem Code, da auf dem Client keine Codeausführung ausgeführt wird.|
|Unterstützung von Nachrichten mit Aktionen|Wenn Sie Nachrichten über Karten senden möchten, müssen Sie das **Nachrichtenkartenformat** mit Aktionen verwenden. Nachrichtenkarten mit Aktionen werden in allen Office 365-Gruppen einschließlich Teams unterstützt. Hier finden Sie Links zum Verweis auf [die Legacy-Nachrichtenkarte](/outlook/actionable-messages/message-card-reference) mit Aktionen und zum [Nachrichtenkarten-Playground.](https://messagecardplayground.azurewebsites.net)|
|Unabhängige UNTERSTÜTZUNG für HTTPS-Messaging| Karten sind eine hervorragende Möglichkeit, Informationen auf klare und konsistente Weise zu präsentieren. Jedes Tool oder Framework, das HTTPS -POST-Anforderungen senden kann, kann Nachrichten über einen eingehenden Webhook an Teams senden.|
|Unterstützung von Markdown|Alle Textfelder in Messagingkarten mit Aktionen unterstützen grundlegendes Markdown. **Verwenden Sie in Ihren Karten kein HTML-Markup.** HTML wird ignoriert und als reiner Text behandelt.|

> [!Note]
> Teams-Bots, Messaging-Erweiterungen, eingehende Webhooks und das Bot Framework unterstützen adaptive Karten, ein offenes kartenübergreifendes Plattformframework. [Teams Connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) unterstützen derzeit keine adaptiven Karten. Es ist jedoch möglich, [](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) einen Fluss zu erstellen, der adaptive Karten in einem Kanal von Teams veröffentlicht.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Hinzufügen eines eingehenden Webhooks zu einem Teams-Kanal

> [!Important]  
> Wenn die Berechtigungen "Mitgliedereinstellungen" Ihres Teams aktiviert sind, um Mitgliedern das Erstellen, Aktualisieren und Entfernen von Connectors zu ermöglichen, kann jedes Teammitglied einen Connector  =>    =>   hinzufügen, ändern oder löschen.

1. Navigieren Sie zu dem Kanal, dem Sie den Webhook  hinzufügen möchten, und wählen Sie (&#8226;&#8226;&#8226;) Weitere Optionen in der oberen Navigationsleiste aus.
1. Wählen **Sie im** Dropdownmenü "Connectors" aus, und suchen Sie nach **"Eingehender Webhook".**
1. Wählen Sie **die Schaltfläche** "Konfigurieren" aus, geben Sie einen Namen ein, und laden Sie optional einen Bild-Avatar für Ihren Webhook hoch.
1. Im Dialogfeld wird eine eindeutige URL angezeigt, die dem Kanal zuordnung wird. Stellen Sie sicher, dass **Sie die URL kopieren** und speichern – Sie müssen sie für den außen nen Dienst bereitstellen.
1. Klicken Sie auf die Schaltfläche **"Fertig".** Der Webhook ist im Teamkanal verfügbar.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Entfernen eines eingehenden Webhooks aus einem Teams-Kanal

1. Navigieren Sie zu dem Kanal, in dem der Webhook hinzugefügt wurde, und wählen Sie *(&#8226;&#8226;&#8226;)* Weitere Optionen in der oberen Navigationsleiste aus.
1. Wählen **Sie im** Dropdownmenü "Connectors" aus.
1. On the left, under **Manage**, choose **Configured**.
1. Wählen Sie *die Nummer "Konfiguriert"* aus, um eine Liste der aktuellen Connectors zu sehen.
1. Wählen **Sie "Verwalten"** neben dem Connector aus, den Sie löschen möchten.
1. Wählen Sie **die Schaltfläche** "Entfernen" aus, und es wird ein Dialogfeld *"Konfiguration entfernen"* angezeigt.
1. Füllen Sie optional die Dialogfeldfelder und Kontrollkästchen aus, bevor Sie die Schaltfläche **"Entfernen"** auswählen. Der Webhook wird aus dem Teamkanal gelöscht.

## <a name="distribution"></a>Verteilung

Sie haben drei Optionen für die Verteilung Ihres eingehenden Webhooks:

* Richten Sie einen eingehenden Webhook direkt für Ihr Team ein.
* Hinzufügen einer Konfigurationsseite und Umschließen des eingehenden Webhooks in einem [O365-Connector](~/webhooks-and-connectors/how-to/connectors-creating.md)
* Packen und veröffentlichen Sie den Connector als Teil Ihrer [AppSource-Übermittlung.](~/concepts/deploy-and-publish/office-store-guidance.md)

## <a name="learn-more"></a>Mehr erfahren

* [Senden von Nachrichten an Connectors und Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md)
