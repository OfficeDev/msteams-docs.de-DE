---
title: Tools und SDKs
author: surbhigupta
description: Übersicht über die Tools und SDKs zum Erstellen Microsoft Teams Bots.
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: e34d89b0ea8aaeb533899309cfb8fdf34d4ceb4994a6e87db398cc3dfc577abd
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57707099"
---
# <a name="bots-and-sdks"></a>Tools und SDKs

Sie können einen Bot erstellen, der in Microsoft Teams mit einem der folgenden Tools oder Funktionen funktioniert:

* [Microsoft Bot Framework Sdk](#bots-with-the-microsoft-bot-framework)
* [Power Virtual Agents](#bots-with-power-virtual-agents)
* [Virtual Assistant](~/samples/virtual-assistant.md)
* [Webhooks und Connectors](#bots-with-webhooks-and-connectors)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots mit der Microsoft Bot Framework

Ihr Teams Bot besteht aus Folgenden:

* Ein öffentlich zugänglicher Webdienst, der von Ihnen gehostet wird.
* Eine Bot Framework-Registrierung für Ihren Webdienst.
* Ihr Teams-App-Paket, das den Teams-Client mit Ihrem Webdienst verbindet.

> [!TIP]
> Verwenden Sie das Entwicklerportal, um Ihren Webdienst beim Bot Framework zu registrieren und Ihre App-Konfigurationen anzugeben. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Teams.](~/concepts/build-and-test/teams-developer-portal.md)

Das [Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK, das zum Erstellen von Bots mit C#, Java, Python und JavaScript verwendet wird. Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn einfach so ändern, dass er in Teams funktioniert. Verwenden Sie C# oder Node.js, um unsere SDKs zu [nutzen.](/microsoftteams/platform/#pivot=sdk-tools) Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs folgendermaßen:

* Verwenden Sie spezielle Kartentypen wie die Office 365-Connectorkarte.
* Legen Sie Teams-spezifischen Kanaldaten für Aktivitäten fest.
* Verarbeiten Sie Messaging-Erweiterungsanforderungen.

> [!IMPORTANT]
> Sie können Teams Apps in jeder Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen. Sie müssen jedoch in allen Fällen die Tokenverarbeitung durchführen.

## <a name="bots-with-power-virtual-agents"></a>Bots mit Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Chatbot-Dienst, der auf der Microsoft Power-Plattform und bot Framework basiert. Der Power Virtual Agent-Entwicklungsprozess verwendet einen geführten, codefreien und grafischen Schnittstellenansatz, der Es Ihren Teammitgliedern ermöglicht, einfach einen intelligenten virtuellen Agent zu erstellen und zu verwalten. Nachdem Sie Ihren Chatbot im [Power Virtual Agents Portal](https://powervirtualagents.microsoft.com)erstellt haben, können Sie ihn problemlos in [Teams integrieren.](how-to/add-power-virtual-agents-bot-to-teams.md) Weitere Informationen zu den ersten Schritten finden Sie [in Power Virtual Agents Dokumentation.](/power-virtual-agents)

## <a name="bots-with-webhooks-and-connectors"></a>Bots mit Webhooks und Connectors

Webhooks und Connectors verbinden Ihren Bot mit Ihren Webdiensten. Mithilfe von Webhooks und Connectors können Sie einen einfachen Bot für grundlegende Interaktionen erstellen, z. B. das Erstellen eines Workflows oder anderer einfacher Befehle. Sie sind nur in dem Team verfügbar, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie unter [Webhooks und Connectors.](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="advantages-of-bots"></a>Vorteile von Bots

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet einzigartige Möglichkeiten und Herausforderungen für Ihren Unterhaltungsbot.

| In einem Kanal | In einem Gruppenchat | In einem 1:1-Chat. |
| :-- | :-- | :-- |
| Massive Reichweite | Weniger Mitglieder | Traditionelle Methode |
| Präzise individuelle Interaktionen | @mention zum Bot  | F&A-Bots |
| @mention zum Bot | Ähnlich wie im Kanal | Bots, die Witze erzählen und Notizen machen |

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Threadunterhaltungen zwischen mehreren Personen, sogar bis zu 2.000. Dies ermöglicht Ihrem Bot möglicherweise eine enorme Reichweite, aber die einzelnen Interaktionen müssen präzise sein. Herkömmliche Multi-Turn-Interaktionen funktionieren nicht. Stattdessen müssen Sie interaktive Karten oder Aufgabenmodule verwenden oder die Unterhaltung in eine 1:1-Unterhaltung verschieben, um viele Informationen zu sammeln. Ihr Bot hat nur Zugriff auf Nachrichten, in denen er sich `@mentioned` befindet. Sie können zusätzliche Nachrichten aus der Unterhaltung mit microsoft Graph und Berechtigungen auf Organisationsebene abrufen.

Bots funktionieren in den folgenden Fällen besser in einem Kanal:

* Benachrichtigungen, in denen Sie eine interaktive Karte für Benutzer bereitstellen, um zusätzliche Informationen zu erhalten.
* Feedbackszenarien, z. B. Umfragen und Umfragen.
* Ein einzelner Anforderungs- oder Antwortzyklus löst Interaktionen auf, und die Ergebnisse sind für mehrere Mitglieder der Unterhaltung hilfreich.
* Soziale oder spaßige Bots, in denen Sie ein großartiges Katzenbild erhalten, wählen nach dem Zufallsprinzip einen Wahlgewinner aus usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threading zwischen drei oder mehr Personen. Sie weisen tendenziell weniger Mitglieder auf als ein Kanal und sind kurzlebiger. Ähnlich wie ein Kanal hat Ihr Bot nur Zugriff auf Nachrichten, in denen er `@mentioned` sich direkt befindet.

In den Fällen, in denen Bots in einem Kanal besser funktionieren, funktionieren sie auch besser in einem Gruppenchat.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat.

Ein 1:1-Chat ist eine herkömmliche Möglichkeit für einen Unterhaltungsbot, mit einem Benutzer zu interagieren. Ein paar Beispiele für 1:1-Unterhaltungs-Bots sind Q&A-Bots, Bots, die Workflows in anderen Systemen initiieren, Bots, die Blättern erzählen, und Bots, die Notizen machen. Bevor Sie 1:1-Chatbots erstellen, sollten Sie überlegen, ob eine unterhaltungsbasierte Schnittstelle die beste Möglichkeit ist, Ihre Funktionalität darzustellen.

## <a name="disadvantages-of-bots"></a>Nachteile von Bots

Ein umfangreiches Dialogfeld zwischen Ihrem Bot und dem Benutzer ist eine langsame und komplexe Möglichkeit, eine Aufgabe abzuschließen. Ein Bot, der exzessive Befehle unterstützt, insbesondere eine breite Palette von Befehlen, ist nicht erfolgreich oder wird von Benutzern positiv betrachtet.

### <a name="have-multi-turn-experiences-in-chat"></a>Multi-Turn-Erfahrungen im Chat

Für ein umfangreiches Dialogfeld muss der Entwickler den Status beibehalten. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Timeout oder **abbrechen** auswählen. Außerdem ist der Prozess mühsam. Sehen Sie sich beispielsweise das folgende Unterhaltungsszenario an:

BENUTZER: Plane eine Besprechung mit Marie.

BOT: Ich habe 200 Ergebnisse gefunden, bitte geben Sie einen Vor- und Nachnamen an.

BENUTZER: Plane eine Besprechung mit Marie Krause.

BOT: OK, Wann möchten Sie sich mit Marie Krause treffen?

BENUTZER: um 13:00 Uhr.

BOT: An welchem Tag?

### <a name="support-too-many-commands"></a>Zu viele Befehle unterstützen

Da es im aktuellen Botmenü nur sechs sichtbare Befehle gibt, ist es unwahrscheinlich, dass mehr mit beliebiger Häufigkeit verwendet wird. Bots, die tief in einen bestimmten Bereich gehen, anstatt eine umfassende Assistentin zu sein, arbeiten und besser arbeiten.

### <a name="maintain-a-large-knowledge-base"></a>Verwalten einer umfangreichen Wissensdatenbank

Einer der Nachteile von Bots besteht darin, dass es schwierig ist, eine große Abrufwissensbasis mit unrangigen Antworten aufrechtzuerhalten. Bots eignen sich am besten für kurze, schnelle Interaktionen und nicht für das Durchsuchen langer Listen, die nach einer Antwort suchen.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NETCore | Node.js |
|----------------|-----------------|--------------|----------------|
| Teams-Unterhaltungsbot | Behandlung von Nachrichten- und Unterhaltungsereignissen. |[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Aktivitätenhandler](~/bots/bot-basics.md)
