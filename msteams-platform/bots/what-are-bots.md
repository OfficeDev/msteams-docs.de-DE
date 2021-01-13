---
title: Was sind Unterhaltungsbots?
author: clearab
description: Eine Übersicht über Unterhaltungsbots in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 0304ae436b54db0d111eaed507beb350f1ca4632
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797869"
---
# <a name="what-are-conversational-bots-in-microsoft-teams"></a>Was sind Unterhaltungsbots in Microsoft Teams?

Unterhaltungsbots ermöglichen Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren. Sie sind unglaublich flexibel– Unterhaltungsbots können auf die Verarbeitung von wenigen einfachen Befehlen oder komplexen virtuellen Assistenten für die Verarbeitung von künstlicher Intelligenz und natürlicher Sprache begrenzt werden. Sie können ein Aspekt einer größeren Anwendung oder vollständig eigenständige Sein.

Die folgende GIF zeigt einen Benutzer, der mit einem Bot in einem 1:1-Chat mit Text und interaktiven Karten konversiert. Die suche nach der richtigen Mischung aus Karten, Text und Aufgabenmodulen ist der Schlüssel zum Erstellen eines nützlichen Bots. Vergessen Sie nicht, Bots sind viel mehr als nur Text!

![HÄUFIG gestellte Fragen plus GIF](~/assets/images/FAQPlusEndUser.gif)

## <a name="build--a-bot-for-teams-with-the-microsoft-bot-framework"></a>Erstellen eines Bots für Teams mit dem Microsoft Bot Framework

Das [Microsoft Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zum Erstellen von Bots mit C#, Java, Python und JavaScript. Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn problemlos an die Arbeit in Microsoft Teams anpassen. Es wird empfohlen, entweder C# oder Node.js zu verwenden, um unsere [SDKs zu nutzen.](/microsoftteams/platform/#pivot=sdk-tools) Diese Pakete erweitern die grundlegenden Bot Builder -SDK-Klassen und -Methoden wie folgt:

* Verwenden Sie spezielle Kartentypen wie die Office 365 Connector-Karte.
* Nutzen und Festlegen von Teams-spezifischen Kanaldaten zu Aktivitäten.
* Verarbeiten von Messagingerweiterungsanforderungen.

Ihr Teams Bot besteht aus drei Elementen:

* Einem öffentlich zugänglichen Webdienst, der von Ihnen betrieben wird.
* Ihre Botregistrierung beim Bot Framework.
* Ihr Teams-App-Paket mit Ihrem App-Manifest. Dies wird von Ihren Benutzern installiert und mit Ihrem Webdienst verbunden, der über den Botdienst geroutet wird.

> [!IMPORTANT]
> Sie können Teams-Apps in jeder Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen, aber Sie müssen die tokenverarbeitung selbst durchführen.

> [!TIP]
> Teams App Studio* hilft Ihnen beim Erstellen und Konfigurieren Ihres App-Manifests und kann Ihren Webdienst als Bot im Bot Framework registrieren. Es enthält auch eine React-Steuerelementbibliothek und einen interaktiven Karten-Generator. *Weitere Informationen* [finden Sie unter "Erste Schritte mit Teams App Studio".](~/concepts/build-and-test/app-studio-overview.md)

## <a name="create-a-chatbot-for-teams-with-microsoft-power-virtual-agents"></a>Erstellen eines Chatbots für Teams mit Microsoft Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Chatbot-Dienst, der auf der Microsoft Power Platform und dem Bot Framework aufgebaut ist.  Der Entwicklungsprozess von Power Virtual Agent verwendet einen geführten, codegesteuerten, grafischen Schnittstellenansatz, mit dem jedes Mitglied Ihres Teams problemlos einen intelligenten virtuellen Agent erstellen und verwalten kann.  Sobald Sie die Erstellung ihres Chatbots im [Power Virtual](https://powervirtualagents.microsoft.com)Agents-Portal abgeschlossen haben, können Sie Ihren Power [Virtual Agents-Chatbot](how-to/add-power-virtual-agents-bot-to-teams.md)ganz einfach in Teams integrieren. Informationen zu den ersten Schritte beim Erstellen Ihres Power Virtual Agents-Chatbots finden Sie *in* der [Dokumentation zu Power Virtual Agents.](https://docs.microsoft.com/power-virtual-agents/)

## <a name="webhooks-and-connectors"></a>Webhooks und Connectors

Mit Webhooks und Connectors können Sie einen einfachen Bot für grundlegende Interaktionen erstellen, z. B. einen Workflow oder andere einfache Befehle starten. Sie befinden sich nur in dem Team, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. *Weitere Informationen* [finden Sie unter Was sind Webhooks und Connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="where-bots-work-best"></a>Wo Bots am besten funktionieren

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet einzigartige Möglichkeiten und Herausforderungen für Ihren Unterhaltungsbot.

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Threadunterhaltungen zwischen mehreren Personen – potenziell viele Personen (derzeit bis zu 2.000). Dadurch erhält Ihr Bot potenziell eine enorme Reichweite, die einzelnen Interaktionen müssen aber präzise sein. Herkömmliche dialogartige Interaktionen mit vielen Fragen und Antworten funktionieren wahrscheinlich nicht gut. Versuchen Sie stattdessen, interaktive Karten oder Aufgabenmodule einzusetzen, oder lagern Sie die Unterhaltung in eine 1:1-Unterhaltung aus, wenn Sie viele Informationen sammeln müssen. Ihr Bot hat auch nur Zugriff auf Nachrichten, in denen er direkt ist, obwohl Sie zusätzliche Nachrichten aus der Unterhaltung mit Microsoft Graph und erhöhten Berechtigungen auf `@mentioned` Organisationsebene abrufen können.

Dies sind einige Szenarien, in denen Bots in einem Kanal glänzen können:

* **Benachrichtigungen**, insbesondere, wenn Sie eine interaktive Karte für die Benutzer bereitstellen, die weitere Informationen aufnimmt.
* **Feedbackszenarien** wie Umfragen und Umfragen.
* Interaktionen, die in einem **einzelnen Anfrage/Antwortzyklus** gelöst werden können, und deren Ergebnis für mehrere Mitglieder der Unterhaltung nützlich ist.
* **Social/Fun-Bots** – Erhalten Sie ein großartiges Cat-Bild, wählen Sie nach dem Zufallsprinzip einen Gewinn aus usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threading zwischen drei oder mehr Personen. Sie haben in der Regel weniger Mitglieder als ein Kanal und sind vorübergehender. Ähnlich wie bei einem Kanal hat Ihr Bot nur Zugriff auf Nachrichten, in denen er direkt `@mentioned` enthalten ist.

Szenarien, die in einem Kanal gut funktionieren, funktionieren in der Regel genauso gut in einem Gruppenchat.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat

Dies ist das herkömmliche Interaktionsverfahren eines Unterhaltungs-Bots mit einem Benutzer. Sie können unglaublich unterschiedliche Workloads ermöglichen. Q&A-Bots, Bots, die Arbeitsabläufe in anderen Systemen auslösen, Bots, die Witze erzählen, und Bots, die Notizen erfassen, sind nur ein paar Beispiele. Denken Sie daran, zu überlegen, ob eine unterhaltungsbasierte Schnittstelle die beste Möglichkeit ist, Ihre Funktionalität zu präsentieren.

## <a name="bot-fails"></a>Bot schlägt fehl

### <a name="having-multi-turn-experiences-in-chat"></a>Multi-Turn-Erfahrungen im Chat

Ein umfangreiches Dialogfeld zwischen Ihrem Bot und dem Benutzer ist eine langsame und zu komplexe Methode, um eine Aufgabe fertig zu machen. Außerdem muss der Entwickler den Zustand beibehalten. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Zeit-Out verwenden oder *"Abbrechen"* eingeben. Vor allem ist der Prozess unnötig mühsam:

USER: Planen Sie eine Besprechung mit Megan.

BOT: Ich habe 200 Ergebnisse gefunden, geben Sie bitte einen Vor- und Nachnamen an.

USER: Planen Sie eine Besprechung mit Megan Bowen.

BOT: OK, wie lange möchten Sie sich mit Megan Bowen treffen?

BENUTZER: 13:00 Uhr.

BOT: An welchem Tag?

### <a name="supporting-too-many-commands"></a>Unterstützen zu vieler Befehle

Ein Bot, der übermäßig viele Befehle unterstützt, insbesondere eine breite Palette von Befehlen, wird von Benutzern nicht erfolgreich oder positiv gesehen. Da nur sechs sichtbare Befehle im aktuellen Botmenü enthalten sind, ist es unwahrscheinlich, dass etwas mehr mit beliebiger Häufigkeit verwendet wird. Bots, die tief in einen bestimmten Bereich gehen, anstatt zu versuchen, ein breiter Assistent zu sein, funktionieren und gehen besser.

### <a name="maintaining-a-large-retrieval-knowledge-base-with-unranked-responses"></a>Verwalten einer großen Wissensdatenbank mit nicht getrunkenen Antworten

Bots eignen sich am besten für kurze, schnelle Interaktionen, ohne lange Listen zu durchsuchen, die nach einer Antwort suchen.

## <a name="get-started"></a>Erste Schritte

* [#A0 in C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)
* [Teams-Unterhaltungsbot in JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)

## <a name="learn-more"></a>Weitere Informationen

> [!div class="nextstepaction"]
> [Grundlagen von Bots in Teams](~/bots/bot-basics.md)

> [!div class="nextstepaction"]
> [Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)
