---
title: Was sind Unterhaltungs Bots?
author: clearab
description: Eine Übersicht über Unterhaltungs Bots in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e10275cba97f835cd59e572b48d2db7cb902d096
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "42635305"
---
# <a name="what-are-conversational-bots"></a>Was sind Unterhaltungs Bots?

Mit Unterhaltungs Bots können Benutzer über Text, interaktive Karten und Aufgaben Module mit Ihrem Webdienst interagieren. Sie sind unglaublich flexibel – Unterhaltungs Bots können mit einigen einfachen Befehlen oder komplexen, mit künstlicher Intelligenz versehenen und natürlichen sprachverarbeitenden virtuellen Assistenten behandelt werden. Sie können ein Aspekt einer größeren Anwendung oder völlig eigenständig sein.

Die folgende GIF-Datei zeigt einen Benutzer, der sich mit einem bot in einem 1:1-Chat unter Verwendung von Text und interaktiven Karten unterhält. Die Suche nach der richtigen Mischung aus Karten, Text und Aufgaben Modulen ist der Schlüssel zum Erstellen eines nützlichen bot. Vergessen Sie nicht, Bots sind viel mehr als nur Text!

![FAQ Plus GIF](~/assets/images/FAQPlusEndUser.gif)

## <a name="how-bots-work"></a>Funktionsweise von Bots

Ihr Teams-bot besteht aus drei Elementen:

* Ein öffentlich zugänglicher Webdienst, den Sie hosten.
* Ihre bot-Registrierung mit dem bot-Framework.
* Ihr Teams-App-Paket mit Ihrem App-Manifest. Dies wird von den Benutzern installiert, und der Microsoft Teams-Client wird mit Ihrem Webdienst verbunden, der über den bot-Dienst weitergeleitet wird.

Bots für Microsoft Teams sind auf dem [Microsoft-bot-Framework](https://dev.botframework.com/)aufgebaut. Wenn Sie bereits einen bot haben, der auf dem bot-Framework basiert, können Sie ihn ganz einfach an die Arbeit in Microsoft Teams anpassen. Es wird empfohlen, dass Sie entweder C# oder Node. js verwenden, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools)nutzen zu können. Diese Pakete erweitern die Klassen und Methoden des Basic bot Builder-SDK wie folgt:

* Verwenden Sie spezielle Kartentypen wie die Office 365-Anschluss Karte.
* Verwenden und Festlegen von Team spezifischen Kanaldaten zu Aktivitäten
* Verarbeiten von Messaging Erweiterungsanforderungen.

> [!IMPORTANT]
> Sie können Microsoft Teams-apps in jeder beliebigen webprogrammier Technologie entwickeln und die [bot-Framework-Rest-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die gesamte tokenbehandlung selbst durchführen.

> [!TIP]
> Teams App Studio * unterstützt Sie bei der Erstellung und Konfiguration Ihres App-Manifests und kann Ihren Webdienst als bot im bot-Framework registrieren. Es enthält auch eine Reaktions Steuerungs Bibliothek und einen interaktiven Kartengenerator. *Weitere Informationen finden Sie unter* [Erste Schritte mit Microsoft Teams App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="webhooks-and-connectors"></a>Webhooks und Connectors

Webhooks und Konnektoren ermöglichen Ihnen, einen einfachen bot für die grundlegende Interaktion zu erstellen, wie das Starten eines Workflows oder andere einfache Befehle. Sie leben nur in dem Team, in dem Sie Sie erstellen, und sind für einfache Prozesse bestimmt, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen *finden Sie unter* [Was sind webhooks und Connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) .

## <a name="where-bots-work-best"></a>Wo Bots am besten funktionieren

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich stellt einzigartige Möglichkeiten und Herausforderungen für Ihren Unterhaltungs bot bereit.

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten threadbezogene Unterhaltungen zwischen mehreren Personen – potenziell viele Personen (derzeit bis zu 2000). Dadurch kann Ihr bot möglicherweise massiv erreicht werden, aber einzelne Interaktionen müssen prägnant sein. Herkömmliche Multi-Turn-Interaktionen funktionieren wahrscheinlich nicht gut. Suchen Sie stattdessen interaktive Karten oder Aufgaben Module oder führen Sie die Unterhaltung möglicherweise in eine 1:1-Unterhaltung ein, wenn Sie viele Informationen sammeln müssen. Ihr bot hat auch nur Zugriff auf Nachrichten, in denen `@mentioned` er direkt ist, Sie können keine weiteren Nachrichten aus der Unterhaltung mit Microsoft Graph und erweiterte Berechtigungen auf Organisationsebene abrufen.

Einige Szenarien, in denen Bots in einem Kanal Excel enthalten, umfassen Folgendes:

* **Benachrichtigungen**, insbesondere wenn Sie eine interaktive Karte für Benutzer zur Verfügung stellen, um zusätzliche Informationen zu nehmen.
* **Feedback Szenarien** wie Umfragen und Umfragen.
* Interaktionen, die in einem **einzelnen Anforderungs-Antwort-Zyklus**aufgelöst werden können, wobei die Ergebnisse für mehrere Mitglieder der Unterhaltung nützlich sind.
* **Soziale/lustige Bots** – holen Sie sich ein fantastisches Cat-Bild, wählen Sie zufällig einen Gewinner aus usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind nicht threadbezogene Unterhaltungen zwischen drei oder mehr Personen. Sie neigen dazu, weniger Mitglieder als ein Kanal und sind mehr flüchtig. Ähnlich wie bei einem Kanal hat ihr bot nur dann Zugriff auf Nachrichten, wenn `@mentioned` er direkt ist.

Szenarien, die in einem Kanal gut funktionieren, werden in der Regel in einem Gruppenchat genauso gut funktionieren.

### <a name="in-a-one-to-one-chat"></a>In einem eins-zu-eins-Chat

Dies ist die herkömmliche Möglichkeit für einen Unterhaltungs-bot, mit einem Benutzer zu interagieren. Sie können unglaublich vielfältige Arbeitslasten ermöglichen. Q&Bots, Bots, die Workflows in anderen Systemen initiieren, Bots, die Witze erzählen, und Bots, die Notizen machen, sind nur einige Beispiele. Denken Sie daran, zu prüfen, ob eine Gesprächs basierte Oberfläche die beste Möglichkeit zum präsentieren ihrer Funktionalität ist.

## <a name="bot-fails"></a>Bot schlägt fehl

### <a name="having-multi-turn-experiences-in-chat"></a>Multi-Turn-Erlebnisse im Chat

Ein umfassender Dialog zwischen Ihrem bot und dem Benutzer ist eine langsame und übermäßig komplexe Möglichkeit, eine Aufgabe abzuschließen, und Sie erfordert auch, dass der Entwickler den Status aufrecht erhält. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Timeout oder einen "*Cancel*" eingeben. Vor allem ist der Prozess unnötig langweilig:

Benutzer: Planen einer Besprechung mit Megan.

BOT: Ich habe 200 Ergebnisse gefunden, fügen Sie bitte einen vor-und Nachnamen ein.

Benutzer: Planen einer Besprechung mit Megan Bowen.

BOT: OK, Wann möchten Sie mit Megan Bowen Zusammentreffen?

Benutzer: 1:00 Uhr.

BOT: an welchem Tag?

### <a name="supporting-too-many-commands"></a>Unterstützung zu vieler Befehle

Ein bot, der übermäßige Befehle unterstützt, insbesondere eine Vielzahl von Befehlen, wird von den Benutzern nicht erfolgreich oder positiv betrachtet. Da es nur 6 sichtbare Befehle im aktuellen bot-Menü gibt, ist es unwahrscheinlich, dass mehr mit einer beliebigen Frequenz verwendet wird. Bots, die tief in einen bestimmten Bereich gehen, anstatt zu versuchen, ein breiter Assistent zu sein, funktionieren und sind besser.

### <a name="maintaining-a-large-retrieval-knowledge-base-with-unranked-responses"></a>Aufrecht erhalten einer großen Retrieval-Wissensdatenbank mit unbewerteten Antworten

Bots eignen sich am besten für kurze, schnelle Interaktionen, nicht aber lange Listen, die nach einer Antwort suchen.

## <a name="get-started"></a>Erste Schritte

* [Teams Conversation bot in C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [Teams Conversation bot in JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a>Weitere Informationen

> [!div class="nextstepaction"]
> [Grundlagen von Bots in Microsoft Teams](~/bots/bot-basics.md)

> [!div class="nextstepaction"]
> [Erstellen eines bot für Teams](~/bots/how-to/create-a-bot-for-teams.md)
