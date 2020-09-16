---
title: Bereitstellen externer Anforderungen an Microsoft Teams mit eingehenden webhooks
author: laujan
description: Vorgehensweise Hinzufügen von eingehender webhook zu Teams-App
keywords: Teams-Registerkarten für ausgehende webhooks *
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 3aa795170af9695fc375043c94e794f814b38646
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47819067"
---
# <a name="post-external-requests-to-teams-with-incoming-webhooks"></a>Bereitstellen externer Anforderungen an Teams mit eingehenden webhooks

## <a name="what-are-incoming-webhooks-in-teams"></a>Was sind eingehende webhooks in Microsoft Teams?

Bei eingehenden webhooks handelt es sich um einen speziellen Connectortyp in Microsoft Teams, der eine einfache Möglichkeit für eine externe App zum Freigeben von Inhalten in Team Kanälen bietet und häufig als Überwachungs-und Benachrichtigungs Tools verwendet wird. Teams stellt eine eindeutige URL bereit, an die Sie eine JSON-Nutzlast mit der Nachricht senden, die Sie bereitstellen möchten, normalerweise in einem Kartenformat. Karten sind Benutzeroberflächencontainer, die Inhalte und Aktionen im Zusammenhang mit einem einzelnen Thema enthalten und eine Möglichkeit zum konsistenten präsentieren von Nachrichtendaten darstellen. Microsoft Teams verwendet Karten in drei Funktionen:

* Bots
* Messaging-Erweiterungen
* Connectors

## <a name="incoming-webhook-key-features"></a>Wichtige Features für eingehende webhooks

| Feature | Beschreibung |
| ------- | ----------- |
|Bereichsbezogene Konfiguration|Eingehende webhooks werden auf Kanalebene ausgelegt und konfiguriert (beispielsweise werden ausgehende webhooks auf Teamebene konfiguriert und konfiguriert).|
|Sichere Ressourcendefinitionen|Nachrichten werden als JSON-Nutzlast formatiert. Diese deklarative Messaging Struktur verhindert, dass schädlicher Code injiziert wird, da auf dem Client keine Codeausführung ausgeführt wird.|
|Unterstützung für Nachrichten mit Aktionen|Wenn Sie sich für das Senden von Nachrichten über Karten entscheiden, müssen Sie das **Nachrichten Karten** Format mit Aktionen verwenden. Umsetzbare Nachrichten Karten werden in allen Office 365 Gruppen einschließlich Teams unterstützt. Hier finden Sie Links zu der [Legacy-Nachrichten Karten Referenz für Aktionen](/outlook/actionable-messages/message-card-reference) und zum [Nachrichten Karten-Spielplatz](https://messagecardplayground.azurewebsites.net).|
|Unterstützung für unabhängige HTTPS-Messaging| Karten sind eine hervorragende Möglichkeit, um Informationen auf klare und konsistente Weise darzustellen. Jedes Tool oder Framework, das HTTPS-POST-Anforderungen senden kann, kann Nachrichten über einen eingehenden webhook an Microsoft Teams senden.|
|Unterstützung für den Abschlag|Alle Textfelder in umsetzbaren Messaging Karten unterstützen das grundlegende Abschlag. **Verwenden Sie kein HTML-Markup auf ihren Karten**. HTML wird ignoriert und als reiner Text behandelt.|

> [!Note]  
> Teams-Bots, Messaging-Erweiterungen und das bot-Framework unterstützen Adaptive Karten, ein offenes plattformübergreifendes Plattform-Framework. Microsoft Teams-Connectors unterstützen derzeit keine adaptiven Karten. Es ist jedoch möglich, einen [Flow](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) zu erstellen, der Adaptive Karten für einen Teams-Kanal bereitstellt.

## <a name="add-an-incoming-webhook-to-a-teams-channel"></a>Hinzufügen eines eingehenden webhooks zu einem Teams-Kanal

> [!Important]  
> Wenn die **Einstellungen**des Team  =>  **Mitgliedsberechtigungen**  =>  **Mitgliedern das Erstellen, aktualisieren und Entfernen von Connectors gestatten** , können alle Teammitglieder einen Connector hinzufügen, ändern oder löschen.

1. Navigieren Sie zu dem Kanal, dem Sie den webhook hinzufügen möchten, und wählen Sie (&#8226;&#8226;&#8226;) *Weitere Optionen* in der oberen Navigationsleiste aus.
1. Wählen Sie im Dropdownmenü **Konnektoren** aus, und suchen Sie nach **eingehenden webhooks**.
1. Wählen Sie die Schaltfläche **configure** aus, geben Sie einen Namen an, und laden Sie optional einen Bild-Avatar für Ihren webhook hoch.
1. Das Dialogfenster stellt eine eindeutige URL dar, die dem Kanal zugeordnet wird. Stellen Sie sicher, dass Sie **die URL kopieren und speichern**– Sie müssen Sie dem externen Dienst zur Verfügung stellen.
1. Klicken Sie auf die Schaltfläche **Fertig** . Der webhook wird im Team Kanal zur Verfügung stehen.

## <a name="remove-an-incoming-webhook-from-a-teams-channel"></a>Entfernen eines eingehenden webhooks aus einem Teams-Kanal

1. Navigieren Sie zu dem Kanal, in dem der webhook hinzugefügt wurde, und wählen Sie in der oberen Navigationsleiste (&#8226;&#8226;&#8226;) *Weitere Optionen* aus.
1. Wählen Sie im Dropdownmenü **Verbinder** aus.
1. Wählen Sie auf der linken Seite unter **Verwalten**die Option **konfiguriert**aus.
1. Wählen Sie die Nummer aus, die so *konfiguriert* ist, dass eine Liste Ihrer aktuellen Connectors angezeigt wird.
1. Wählen Sie neben dem Connector, den Sie löschen möchten, die Option **Verwalten** aus.
1. Klicken Sie auf die Schaltfläche **Entfernen** , und es wird ein Dialogfeld *Konfiguration entfernen* angezeigt.
1. Schließen Sie optional die Felder und Kontrollkästchen des Dialogfelds ab, bevor **Sie** die Schaltfläche Entfernen auswählen. Der webhook wird aus dem Team Kanal gelöscht.

## <a name="distribution"></a>Verteiler

Sie haben drei Möglichkeiten, Ihren eingehenden webhook zu verteilen:

* Richten Sie einen eingehenden webhook direkt für Ihr Team ein.
* Hinzufügen einer Konfigurationsseite und Umbrechen des eingehenden webhooks in einen [O365-Connector](~/webhooks-and-connectors/how-to/connectors-creating.md)
* Verpacken und veröffentlichen Sie den Connector als Teil ihrer [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md) -Übermittlung.

## <a name="learn-more"></a>Weitere Informationen

* [Senden von Nachrichten an Connectors und webhooks](~/webhooks-and-connectors/how-to/connectors-using.md)
