---
title: Erstellen eines eingehenden Webhooks
author: laujan
description: In diesem Modul erfahren Sie, wie Sie der Teams-App einen eingehenden Webhook hinzufügen und alle externen Anforderungen mit diesem Webhook an Teams senden.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4b93e7118cbd9b22ef7022f19b9538fe156b59f6
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503494"
---
# <a name="create-incoming-webhooks"></a>Erstellen eingehender Webhooks

Mit einem eingehenden Webhook können externe Anwendungen Inhalte in Microsoft Teams-Kanälen freigeben. Die Webhooks werden als Tools zum Nachverfolgen und Benachrichtigen verwendet. Die Webhooks stellen eine eindeutige URL zum Senden einer JSON-Nutzlast mit einer Nachricht im Kartenformat bereit. Karten sind Benutzeroberflächencontainer, welche Inhalte und Aktionen enthalten, die sich auf ein einzelnes Thema beziehen. Sie können Karten innerhalb der folgenden Funktionen verwenden:

* Bots
* Nachrichtenerweiterungen
* Connectors

Im folgenden Video erfahren Sie, wie Sie eingehende Webhooks erstellen:
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4ODcY]

## <a name="key-features-of-an-incoming-webhook"></a>Wichtige Features des eingehenden Webhooks

Die folgende Tabelle enthält die Features und die Beschreibung eines eingehenden Webhooks:

| Features | Beschreibung |
| -------- | ----------- |
|Adaptiven Karten, die einen eingehenden Webhook verwenden | Adaptive Karten können über eingehende Webhooks gesendet werden. Weitere Informationen finden Sie unter [Senden von adaptiven Karten mit eingehenden Webhooks](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).|
|Unterstützung für Aktion erfordernde Nachrichten|Aktion erfordernde Nachrichtenkarten werden in allen Office 365-Gruppen einschließlich Microsoft Teams unterstützt. Wenn Sie Nachrichten über Karten senden, müssen Sie das Format für die eine Aktion erfordernde Nachrichtenkarte verwenden. Weitere Informationen finden Sie unter [Legacy-Referenz für eine Aktion erfordernde Nachrichtenkarte](/outlook/actionable-messages/message-card-reference) und [Nachrichten-Testwebsite für Karten](https://messagecardplayground.azurewebsites.net).|
|Unabhängige HTTPS-Messaging-Unterstützung|Karten stellen Informationen klar und konsistent bereit. Jedes Tool oder Framework, das HTTPS-POST-Anforderungen senden kann, kann über einen eingehenden Webhook Nachrichten an Teams senden.|
|Markdown-Unterstützung|Alle Textfelder in Aktion erfordernden Nachrichtenkarten unterstützen grundlegendes Markdown. Verwenden Sie in Ihren Karten kein HTML-Markup. HTML wird ignoriert und als reiner Text behandelt.|
|Konfigurationsbereich|Der eingehender Webhook ist auf Kanalebene begrenzt und konfiguriert.|
|Sichere Ressourcendefinitionen|Nachrichten werden als JSON-Nutzlast formatiert. Diese deklarative Nachrichtenstruktur verhindert das Einfügen von bösartigem Code.|

<!--- TBD: A note should be short and eye-catching. No need to put a list item inside a Note or any admonition for that matter. Re-write the below list item.
--->

> [!NOTE]
>
> * Teams-Bots, Nachrichtenerweiterungen, der eingehende Webhook und das Bot-Framework unterstützen adaptive Karten. Adaptive Karten sind ein offenes, plattformübergreifendes Kartenframework, das auf allen Plattformen wie Windows, Android, iOS usw. verwendet wird. Derzeit werden adaptive Karten von [Teams-Connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) nicht unterstützt. Es ist jedoch möglich, einen [Fluss](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) zu erstellen, der adaptive Karten an einen Teams-Kanal sendet.
> * Weitere Informationen zu Karten und Webhooks finden Sie unter [Adaptive Karten und eingehende Webhooks](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks).

## <a name="create-an-incoming-webhook"></a>Erstellen eines eingehenden Webhooks

Führen Sie die folgenden Schritte aus, um einem Teams-Kanal einen eingehenden Webhook hinzuzufügen:

1. Öffnen Sie den Kanal, dem Sie den Webhook hinzufügen möchten, und wählen Sie &#8226;&#8226;&#8226; **Weitere Optionen** in der oberen Navigationsleiste aus.
1. Wählen Sie **Connectors** aus dem Dropdownmenü aus:

    ![Connector auswählen](~/assets/images/connectors.png)

1. Suchen Sie nach **Eingehender Webhook** und wählen Sie **Hinzufügen** aus.
1. Wählen Sie **Konfigurieren** aus, geben Sie einen Namen an, und laden Sie bei Bedarf ein Bild für Ihren Webhook hoch:

    ![Schaltfläche „Konfigurieren“](~/assets/images/configure.png)

1. Kopieren und speichern Sie die eindeutige Webhook-URL, die im Dialogfeld vorhanden ist. Die URL ist dem Kanal zugeordnet, und Sie können sie verwenden, um Informationen an Teams zu senden. Wählen Sie **Fertig** aus.

    ![Eindeutige URL](~/assets/images/url.png)

Der Webhook ist im Teams-Kanal verfügbar.

Sie können Aktionen erfordernde Nachrichten über einen eingehenden Webhook oder Office 365-Connector erstellen und senden. Weitere Informationen finden Sie unter [Erstellen und Senden von Nachrichten](~/webhooks-and-connectors/how-to/connectors-using.md).

> [!NOTE]
> Wählen Sie in Teams **Einstellungen** > **Mitgliederberechtigungen** > **Mitgliedern das Erstellen, Aktualisieren und Entfernen von Connectors erlauben** aus, damit jedes Teammitglied einen Connector hinzufügen, ändern oder löschen kann.

## <a name="remove-an-incoming-webhook"></a>Entfernen eines eingehenden Webhooks

Führen Sie die folgenden Schritte aus, um einen eingehenden Webhook aus einem Teams-Kanal zu entfernen:

1. Öffnen Sie den Kanal, und wählen Sie &#8226;&#8226;&#8226; **Weitere Optionen** aus der oberen Navigationsleiste aus.
1. Wählen Sie im Dropdownmenü **Connectors** aus.
1. Wählen Sie **Konfiguriert** unter **Verwalten** aus.
1. Wählen Sie die Option **<*1*> Konfiguriert** aus, um eine Liste Ihrer aktuellen Connectors anzuzeigen:

    ![Konfigurierter Webhook](~/assets/images/configured.png)

1. Wählen Sie **Verwalten** für den Verbinder aus, den Sie entfernen möchten:

    ![Webhook verwalten](~/assets/images/manage.png)

1. Wählen Sie **Entfernen** aus, um das Dialogfeld **Konfiguration entfernen** anzuzeigen.

    ![Konfiguration entfernen](~/assets/images/removeconfiguration.png)

1. Füllen Sie die Felder des Dialogfelds und die Kontrollkästchen aus, und wählen Sie **Entfernen** aus.

    ![Endgültiges Entfernen](~/assets/images/finalremove.png)

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | C#    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Eingehender Webhook|Dieser Beispielcode veranschaulicht das Senden einer Karte mithilfe des eingehenden Webhooks. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/incoming-webhook/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/incoming-webhook/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Von Web-Apps für Teams freigeben](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
