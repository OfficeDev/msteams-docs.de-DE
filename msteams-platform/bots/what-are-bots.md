---
title: Was sind Unterhaltungs-Bots?
author: clearab
description: Überblick über Unterhaltungs-Bots in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 0304ae436b54db0d111eaed507beb350f1ca4632
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797869"
---
# <a name="what-are-conversational-bots-in-microsoft-teams"></a>Was sind Unterhaltungs-Bots in Microsoft Teams?

Unterhaltungs-Bots ermöglichen Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren. Unterhaltungs-Bots können darauf zugeschnitten werden, mit nur wenigen einfachen Befehlen oder komplexen, KI-gestützten und natürliche Sprache verarbeitenden virtuellen Assistenten zu arbeiten. Sie können ein Element einer umfassenderen Anwendung darstellen oder vollkommen eigenständig sein.

Das GIF unten zeigt einen Benutzer, der sich in einem 1:1-Chat mit einem Bot unterhält, wobei sowohl Text als auch interaktive Karten verwendet werden. Die richtige Mischung aus Karten, Text und Aufgabenmodulen zu finden, ist der Schlüssel zur Erstellung eines nützlichen Bots. Vergessen Sie nicht: Bots sind viel mehr als nur Text!

![FAQ Plus GIF](~/assets/images/FAQPlusEndUser.gif)

## <a name="build--a-bot-for-teams-with-the-microsoft-bot-framework"></a>Erstellen eines Bots für Teams mit Microsoft Bot Framework

[Microsoft Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zur Erstellung von Bots mit C#, Java, Python und JavaScript. Wenn Sie bereits über einen Bot verfügen, der auf Bot Framework basiert, können Sie ihn problemlos für Microsoft Teams anpassen. Microsoft empfiehlt die Verwendung von C# oder Node.js, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools) nutzen zu können. Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs folgendermaßen:

* Verwenden Sie spezielle Kartentypen wie die Office 365-Connector-Karte.
* Sie können Teams-spezifische Kanaldaten zu Aktivitäten verarbeiten und festlegen.
* Verarbeiten Sie Messaging-Erweiterungsanforderungen.

Ihr Teams-Bot besteht aus drei Elementen:

* Einem öffentlich zugänglichen Webdienst, der von Ihnen betrieben wird.
* Ihrer Bot-Registrierung bei Bot Framework.
* Ihrem Teams-App-Paket mit Ihrem App-Manifest. Dies ist das Element, das von Ihren Benutzer installiert wird und das, geroutet durch den Bot-Dienst, die Verbindung Ihres Teams-Client mit Ihrem Webdienst herstellt.

> [!IMPORTANT]
> Sie können Teams-Apps in jeder beliebigen Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die gesamte Tokenverarbeitung selbst vornehmen.

> [!TIP]
> Teams App Studio* hilft Ihnen bei der Erstellung und Konfiguration Ihres App-Manifests und kann Ihren Webdienst als Bot bei Bot Framework registrieren. Es enthält auch eine React-Steuerungsbibliothek sowie einen Generator für interaktive Karten. *Siehe* [Erste Schritte mit Teams App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="create-a-chatbot-for-teams-with-microsoft-power-virtual-agents"></a>Erstellen eines Chatbots für Teams mit Microsoft Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Chatbot-Dienst, der auf der Microsoft Power-Plattform und Bot Framework aufbaut.  Der Power Virtual Agent-Entwicklungsprozess verwendet einen geführten, Ansatz ohne Code über eine grafische Schnittstelle, um jedes Mitglied Ihres Teams in die Lage zu versetzen, mühelos einen intelligenten virtuellen Agent zu erstellen und zu pflegen.  Sobald Sie Ihre Chatbot im [Power Virtual Agents-Portal](https://powervirtualagents.microsoft.com) erstellt haben, können Sie Ihren [Power Virtual Agents-Chatbot einfach in Teams integrieren](how-to/add-power-virtual-agents-bot-to-teams.md). Um mit der Erstellung Ihres Power Virtual Agents-Chatbots zu beginnen, *lesen* Sie die [Power Virtual Agents-Dokumentation](https://docs.microsoft.com/power-virtual-agents/).

## <a name="webhooks-and-connectors"></a>Webhooks und Connectors

Mit Webhooks und Connectors können Sie einen einfachen Bot für grundlegende Interaktionen erstellen, wie das Starten eines Workflows oder andere einfache Befehle. Diese sind nur in dem Team verfügbar, in dem Sie sie erstellen, und sind für einfache, auf den Workflow Ihres Unternehmens zugeschnittene Prozesse gedacht. *Unter* [Was sind Webhooks und Connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) finden Sie weitere Informationen.

## <a name="where-bots-work-best"></a>Wo Bots am besten funktionieren

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet für Ihren Unterhaltungs-Bot besondere Chancen und Herausforderungen.

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Unterhaltungsthreads zwischen mehreren Personen – potenziell einer großen Anzahl von Personen (derzeit bis zu 2.000). Dadurch erhält Ihr Bot potenziell eine enorme Reichweite, die einzelnen Interaktionen müssen aber präzise sein. Herkömmliche dialogartige Interaktionen mit vielen Fragen und Antworten funktionieren wahrscheinlich nicht gut. Versuchen Sie stattdessen, interaktive Karten oder Aufgabenmodule einzusetzen, oder lagern Sie die Unterhaltung in eine 1:1-Unterhaltung aus, wenn Sie viele Informationen sammeln müssen. Ihr Bot hat nur Zugriff auf die Nachrichten, in denen er direkt @erwähnt (`@mentioned`) wird. Sie können allerdings mithilfe von Microsoft Graph und erhöhten Berechtigungen auf Organisationsebene auch weitere Nachrichten aus der Unterhaltung abrufen.

Dies sind einige Szenarien, in denen Bots in einem Kanal glänzen können:

* **Benachrichtigungen**, insbesondere, wenn Sie eine interaktive Karte für die Benutzer bereitstellen, die weitere Informationen aufnimmt.
* **Feedbackszenarien** wie Abstimmungen und Umfragen.
* Interaktionen, die in einem **einzelnen Anfrage/Antwortzyklus** gelöst werden können, und deren Ergebnis für mehrere Mitglieder der Unterhaltung nützlich ist.
* **Soziale/Spaß-Bots** – Holen Sie sich ein tolles Katzenbild, wählen Sie zufällig einen Gewinner aus, usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threads zwischen drei oder mehr Personen. Sie weisen tendenziell weniger Mitglieder auf als ein Kanal und sind kurzlebiger. Ähnlich wie bei einem Kanal hat ihr Bot nur Zugriff auf Nachrichten, in denen er direkt @erwähnt (`@mentioned`) wird.

Szenarien, die in einem Kanal gut funktionieren, können in der Regel auch genau so gut in einem Gruppenchat verwendet werden.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat.

Dies ist das herkömmliche Interaktionsverfahren eines Unterhaltungs-Bots mit einem Benutzer. Bots eignen sich für unglaublich vielfältige Workloads. Q&A-Bots, Bots, die Arbeitsabläufe in anderen Systemen auslösen, Bots, die Witze erzählen, und Bots, die Notizen erfassen, sind nur ein paar Beispiele. Überprüfen Sie aber auch stets, ob eine unterhaltungsbasierte Oberfläche die beste Möglichkeit ist, Ihre Funktionalität darzustellen.

## <a name="bot-fails"></a>Bot schlägt fehl

### <a name="having-multi-turn-experiences-in-chat"></a>Komplexe Aufgaben im Chat

Ein umfangreicher Dialog zwischen Ihrem Bot und dem Benutzer ist ein langsamer und übermäßig komplexer Weg, um eine Aufgabe zu erledigen, und er erfordert außerdem, dass der Entwickler den Zustand aufrechterhält. Um den Zustand zu verlassen, muss ein Benutzer entweder ein Timeout überschreiten oder *Abbrechen* eingeben. Vor allem aber ist der Prozess unnötig langwierig:

BENUTZER: Plane eine Besprechung mit Marie.

BOT: Ich habe 200 Ergebnisse gefunden, bitte geben Sie einen Vor- und Nachnamen an.

BENUTZER: Plane eine Besprechung mit Marie Krause.

BOT: OK, Wann möchten Sie sich mit Marie Krause treffen?

BENUTZER: um 13:00 Uhr.

BOT: An welchem Tag?

### <a name="supporting-too-many-commands"></a>Unterstützung zu vieler Befehle

Ein Bot, der zu viele Befehle unterstützt, insbesondere eine zu große Anzahl von Befehlen, wird nicht erfolgreich sein oder von Benutzern nicht positiv gesehen werden. Da es im aktuellen Bot-Menü nur 6 sichtbare Befehle gibt, wird alles andere wahrscheinlich nicht häufig verwendet. Bots, die detailliert auf einen bestimmten Bereich eingehen, anstatt zu versuchen, ein allgemeiner Assistent zu sein, werden besser funktionieren und besser abschneiden.

### <a name="maintaining-a-large-retrieval-knowledge-base-with-unranked-responses"></a>Verwalten einer großen Retrieval-Knowledge Base mit Antworten ohne Rangfolge

Bots sind am besten für kurze, schnelle Interaktionen geeignet, nicht für das Durchsuchen langer Listen auf der Suche nach einer Antwort.

## <a name="get-started"></a>Erste Schritte

* [Teams-Unterhaltungs-Bot in C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [Teams-Unterhaltungs-Bot in JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a>Weitere Informationen

> [!div class="nextstepaction"]
> [Grundlagen von Bots in Teams](~/bots/bot-basics.md)

> [!div class="nextstepaction"]
> [Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)
