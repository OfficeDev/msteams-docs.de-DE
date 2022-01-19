---
title: Erstellen eines eingehenden Webhooks
author: laujan
description: beschreibt, wie ein eingehender Webhook zur Teams-App hinzugefügt und externe Anforderungen mit eingehenden Webhooks zu Teams gepostet werden.
keywords: Teams-Registerkarte „Ausgehender Webhook“
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 308eaf9f08e946f468f02d897ad556681d1cc832
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059763"
---
# <a name="create-incoming-webhook"></a>Eingehenden Webhook erstellen

Ein eingehender Webhook ermöglicht es externen Apps, Inhalte in Teams-Kanälen freizugeben. Diese Webhooks werden als Nachverfolgungs- und Benachrichtigungstools verwendet. Sie stellen eine eindeutige URL bereit, an die Sie JSON-Nutzdaten mit einer Nachricht im Kartenformat senden. Karten sind Benutzeroberflächencontainer, welche Inhalte und Aktionen enthalten, die sich auf ein einzelnes Thema beziehen. Teams verwendet Karten innerhalb der folgenden Funktionen:

* Bots
* Messaging-Erweiterungen
* Connectors

## <a name="key-features-of-incoming-webhook"></a>Wichtige Features des eingehenden Webhooks

Die folgende Tabelle enthält die Features und die Beschreibung eines eingehenden Webhooks:

| Features | Beschreibung |
| ------- | ----------- |
|Adaptiven Karten, die einen eingehenden Webhook verwenden|Adaptive Karten können über eingehende Webhooks gesendet werden. Weitere Informationen finden Sie unter [Senden von adaptiven Karten mit eingehenden Webhooks](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).|
|Unterstützung für Aktion erfordernde Nachrichten|Aktion erfordernde Nachrichtenkarten werden in allen Office 365-Gruppen einschließlich Microsoft Teams unterstützt. Wenn Sie Nachrichten über Karten senden, müssen Sie das Format für die eine Aktion erfordernde Nachrichtenkarte verwenden. Weitere Informationen finden Sie unter [Legacy-Referenz für eine Aktion erfordernde Nachrichtenkarte](/outlook/actionable-messages/message-card-reference) und [Nachrichten-Testwebsite für Karten](https://messagecardplayground.azurewebsites.net).|
|Unabhängige HTTPS-Messaging-Unterstützung|Karten stellen Informationen klar und konsistent bereit. Jedes Tool oder Framework, das HTTPS-POST-Anforderungen senden kann, kann über einen eingehenden Webhook Nachrichten an Teams senden.|
|Markdown-Unterstützung|Alle Textfelder in Aktion erfordernden Nachrichtenkarten unterstützen grundlegendes Markdown. Verwenden Sie in Ihren Karten kein HTML-Markup. HTML wird ignoriert und als reiner Text behandelt.|
|Konfigurationsbereich|Der eingehender Webhook ist auf Kanalebene begrenzt und konfiguriert.|
|Sichere Ressourcendefinitionen|Nachrichten werden als JSON-Nutzlast formatiert. Diese deklarative Nachrichtenstruktur verhindert das Einfügen von bösartigem Code.|

> [!NOTE]
> * Teams-Bots, Messaging-Erweiterungen, der eingehende Webhook und das Bot-Framework unterstützen adaptive Karten. Adaptive Karten sind ein offenes, plattformübergreifendes Kartenframework, das auf allen Plattformen wie Windows, Android, iOS usw. verwendet werden kann. Derzeit werden adaptive Karten von [Teams-Connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) nicht unterstützt. Es ist jedoch möglich, einen [Fluss](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) zu erstellen, der adaptive Karten an einen Teams-Kanal sendet.
> * Weitere Informationen zu Karten und Webhooks finden Sie unter [Adaptive Karten und eingehende Webhooks](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks).

## <a name="create-incoming-webhook"></a>Eingehenden Webhook erstellen

**So fügen Sie einen eingehenden Webhook zu einem Teams-Kanal hinzu**

1. Wechseln Sie zu dem Kanal, dem Sie den Webhook hinzufügen möchten, und wählen Sie &#8226;&#8226;&#8226; **Weitere Optionen** in der oberen Navigationsleiste aus.
1. Wählen Sie **Connectors** aus dem Dropdownmenü aus:

    ![Connector auswählen](~/assets/images/connectors.png)

1. Suchen Sie nach **Eingehender Webhook** und wählen Sie **Hinzufügen** aus.
1. Wählen Sie **Konfigurieren** aus, geben Sie einen Namen an, und laden Sie bei Bedarf ein Bild für Ihren Webhook hoch:

    ![Schaltfläche „Konfigurieren“](~/assets/images/configure.png)

1. Das Dialogfeld zeigt eine eindeutige URL an, die dem Kanal zugeordnet ist. Kopieren und speichern Sie die Webhook-URL, um Informationen an Microsoft Teams zu senden, und wählen Sie **Fertig** aus:

    ![Eindeutige URL](~/assets/images/url.png)

Der Webhook ist im Teams-Kanal verfügbar.

Sie können Aktionen erfordernde Nachrichten über einen eingehenden Webhook oder Office 365-Connector erstellen und senden. Weitere Informationen finden Sie unter [Erstellen und Senden von Nachrichten](~/webhooks-and-connectors/how-to/connectors-using.md).

> [!NOTE]
> Wählen Sie in Teams **Einstellungen** > **Mitgliederberechtigungen** > **Mitgliedern das Erstellen, Aktualisieren und Entfernen von Connectors erlauben** aus, damit jedes Teammitglied einen Connector hinzufügen, ändern oder löschen kann.

## <a name="remove-incoming-webhook"></a>Eingehenden Webhook entfernen

**So entfernen Sie einen eingehenden Webhook aus einem Teams-Kanal**

1. Wechseln Sie zum Kanal.
1. Wählen Sie &#8226;&#8226;&#8226; **Weitere Optionen** in der oberen Navigationsleiste aus.
1. Wählen Sie im Dropdownmenü **Connectors** aus.
1. Wählen Sie auf der linken Seite unter **Verwalten** die Option **Konfiguriert** aus.
1. Wählen Sie die Option **<*1*> Konfiguriert** aus, um eine Liste Ihrer aktuellen Connectors anzuzeigen:

    ![Konfigurierter Webhook](~/assets/images/configured.png)

1. Wählen Sie **Verwalten** neben dem Connector aus, den Sie löschen möchten:

    ![Webhook verwalten](~/assets/images/manage.png)

1. Wählen Sie **Entfernen** aus:

    ![Webhook entfernen](~/assets/images/remove.png)

    Das Dialogfeld **Konfiguration entfernen** wird angezeigt:

    ![Konfiguration entfernen](~/assets/images/removeconfiguration.png)

1. Füllen Sie die Felder des Dialogfelds und die Kontrollkästchen aus, und wählen Sie **Entfernen** aus:

    ![Endgültiges Entfernen](~/assets/images/finalremove.png)

    Der Webhook wird aus dem Teams-Kanal entfernt.

## <a name="see-also"></a>Siehe auch

* [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Erstellen einer Schaltfläche zum Teilen in Microsoft Teams](../../concepts/build-and-test/share-to-teams.md#create-share-to-teams-button)
* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
