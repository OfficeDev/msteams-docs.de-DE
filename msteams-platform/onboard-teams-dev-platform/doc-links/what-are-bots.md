---
title: Was sind Bots?
author: clearab
description: Eine Übersicht über Bots in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 1e07d56769cbb303f9af98f84c8ae6064325c1a7
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652002"
---
# <a name="what-are-bots"></a>Was sind Bots?

Bots ermöglichen Benutzern die Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgaben Module. Sie sind unglaublich flexibel – Sie können Bots mit einigen einfachen Befehlen oder virtuellen Assistenten umgehen, die von künstlicher Intelligenz und natürlicher Sprachverarbeitung betrieben werden. Sie können ein Aspekt einer größeren Anwendung oder vollständig eigenständig sein.

Die Suche nach der richtigen Mischung aus Karten, Text und Aufgaben Modulen ist der Schlüssel zum Erstellen eines nützlichen bot. Vergessen Sie nicht, Bots sind viel mehr als nur Text!

![FAQ Plus GIF](~/assets/images/FAQPlusEndUser.gif)

## <a name="user-scenarios"></a>Benutzerszenarien

Bots in Microsoft Teams können Teil eines Kanals, Gruppenchats oder eins-zu-eins-Chats sein. Jeder Bereich stellt einzigartige Möglichkeiten und Herausforderungen für Ihren Unterhaltungs bot bereit.

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten threadbezogene Unterhaltungen zwischen mehreren Personen – potenziell viele Personen (derzeit bis zu 2000). Dadurch erhält Ihr Bot potenziell eine enorme Reichweite, die einzelnen Interaktionen müssen aber präzise sein. Herkömmliche dialogartige Interaktionen mit vielen Fragen und Antworten funktionieren wahrscheinlich nicht gut. Versuchen Sie stattdessen, interaktive Karten oder Aufgabenmodule einzusetzen, oder lagern Sie die Unterhaltung in eine 1:1-Unterhaltung aus, wenn Sie viele Informationen sammeln müssen. Ihr bot hat auch nur Zugriff auf Nachrichten, in denen er `@mentioned` direkt ist, obwohl Sie zusätzliche Nachrichten aus der Unterhaltung mithilfe von Microsoft Graph und erweiterte Berechtigungen auf Organisationsebene abrufen können.

Dies sind einige Szenarien, in denen Bots in einem Kanal glänzen können:

* **Benachrichtigungen**, insbesondere, wenn Sie eine interaktive Karte für die Benutzer bereitstellen, die weitere Informationen aufnimmt.
* **Feedback Szenarien** wie Umfragen und Umfragen.
* Interaktionen, die in einem **einzelnen Anfrage/Antwortzyklus** gelöst werden können, und deren Ergebnis für mehrere Mitglieder der Unterhaltung nützlich ist.
* **Soziale/lustige Bots** – holen Sie sich ein fantastisches Cat-Bild, wählen Sie zufällig einen Gewinner aus usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threading zwischen drei oder mehr Personen. Sie neigen dazu, weniger Mitglieder als ein Kanal und sind mehr flüchtig. Ähnlich wie bei einem Kanal hat ihr bot nur dann Zugriff auf Nachrichten, wenn er `@mentioned` direkt ist.

Szenarien, die in einem Kanal gut funktionieren, werden in der Regel in einem Gruppenchat genauso gut funktionieren.

### <a name="in-a-one-on-one-chat"></a>In einem Einzelchat

Dies ist das herkömmliche Interaktionsverfahren eines Unterhaltungs-Bots mit einem Benutzer. Sie können unglaublich vielfältige Arbeitslasten ermöglichen. Q&A-Bots, Bots, die Arbeitsabläufe in anderen Systemen auslösen, Bots, die Witze erzählen, und Bots, die Notizen erfassen, sind nur ein paar Beispiele. Denken Sie daran, zu prüfen, ob eine Gesprächs basierte Oberfläche die beste Möglichkeit zum präsentieren ihrer Funktionalität ist.

## <a name="building-a-teams-bot-with-the-microsoft-bot-framework"></a>Erstellen eines Teams mit dem bot-Framework von Microsoft

Das [Microsoft bot-Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zum Erstellen von Bots mithilfe von C#, Java, Python oder JavaScript. Wenn Sie bereits einen bot haben, der auf dem bot-Framework basiert, können Sie ihn ganz einfach an die Arbeit in Microsoft Teams anpassen. Es wird empfohlen, dass Sie entweder C# oder Node.js verwenden, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools)zu nutzen. Diese Pakete erweitern die Klassen und Methoden des Basic bot Builder-SDK wie folgt:

* Verwenden Sie spezielle Kartentypen wie die Office 365-Anschluss Karte.
* Verwenden und Festlegen von Team spezifischen Kanaldaten zu Aktivitäten
* Verarbeiten von Messaging Erweiterungsanforderungen.

> [!IMPORTANT]
> Sie können Microsoft Teams-apps in jeder beliebigen webprogrammier Technologie entwickeln und die [bot-Framework-Rest-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die gesamte tokenbehandlung selbst durchführen.

Ihr Teams-bot besteht aus drei Elementen:

* Einem öffentlich zugänglichen Webdienst, der von Ihnen betrieben wird.
* Ihre bot-Registrierung mit dem bot-Framework.
* Ihr Teams-App-Paket mit Ihrem App-Manifest. Dies wird von den Benutzern installiert, und der Microsoft Teams-Client wird mit Ihrem Webdienst verbunden, der über den bot-Dienst weitergeleitet wird.

> [!TIP]
> Teams App Studio * unterstützt Sie bei der Erstellung und Konfiguration Ihres App-Manifests und kann Ihren Webdienst als bot im bot-Framework registrieren. Es enthält auch eine Reaktions Steuerungs Bibliothek und einen interaktiven Kartengenerator. *Weitere Informationen finden Sie unter* [Erste Schritte mit Microsoft Teams App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="building-a-teams-bot-with-microsoft-power-virtual-agents"></a>Erstellen eines Teams, das mit Microsoft Power Virtual Agents bot

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Dienst, der auf der Microsoft Power Platform und dem bot-Framework basiert. Der Entwicklungsprozess von Power Virtual Agent verwendet einen geführten, No-Code-grafischen Schnittstellen Ansatz, um jedes Mitglied Ihres Teams zu ermächtigen, einen intelligenten virtuellen Agent einfach zu erstellen und zu verwalten. Nachdem Sie die Erstellung Ihrer Chatbot im [Portal Power Virtual Agents](https://powervirtualagents.microsoft.com)abgeschlossen haben, können Sie [Ihre Power Virtual Agents Chatbot problemlos in Teams integrieren](../../bots/how-to/add-power-virtual-agents-bot-to-teams.md). Um mit dem Erstellen Ihrer Power Virtual Agents Chatbot zu beginnen, *Lesen Sie* die [Dokumentation zu Power Virtual Agents](https://docs.microsoft.com/power-virtual-agents/).

## <a name="connectors-and-bots"></a>Connectors und Bots

Konnektoren ermöglichen Ihnen, einen einfachen bot für die grundlegende Interaktion zu erstellen, wie das Starten eines Workflows oder andere einfache Befehle. Sie leben nur in dem Team, in dem Sie Sie erstellen, und sind für einfache Prozesse bestimmt, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen *finden Sie unter* [Was sind webhooks und Connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) .

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

Bots eignen sich am besten für kurze, schnelle Interaktionen und nicht Durchsichten langer Listen, die nach einer Antwort suchen.

## <a name="get-started"></a>Erste Schritte

* [Teams Conversation bot in C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [Teams-Unterhaltungsbot in JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a>Weitere Informationen

* [Grundlagen von Bots in Microsoft Teams](~/bots/bot-basics.md)
* [Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)
* [Planen Ihrer APP](../../concepts/extensibility-points.md)
* [Entwerfen ihrer app].. /(.. /designing-your-app/designing-overview.md)
* [Erstellen Ihrer APP](../../concepts/building-an-app.md)
* [Veröffentlichen Ihrer APP](../../concepts/deploy-and-publish/overview.md)
