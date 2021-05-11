---
title: Tools und SDKs
author: clearab
description: Bots und SDKs in Microsoft Teams.
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 2a77b629a645625398fccfd6a18eb1ed3f09844e
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020183"
---
# <a name="bots-and-sdks"></a>Tools und SDKs

Zum Erstellen eines Bots, der in Microsoft Teams funktioniert, können Sie einen der folgenden Optionen verwenden:
* Ein vorhandener Bot, der auf dem Microsoft Bot Framework SDK baut.
* Power Virtual Agents chatbot-Dienst.
* Webhooks und Connectors.

## <a name="bots-and-the-microsoft-bot-framework"></a>Bots und Microsoft Bot Framework

Ihr Teams besteht aus den folgenden drei Elementen:

* Einem öffentlich zugänglichen Webdienst, der von Ihnen betrieben wird.
* Ihrer Bot-Registrierung bei Bot Framework.
* Ihrem Teams-App-Paket mit Ihrem App-Manifest. Dies ist das, was Ihre Benutzer installieren und den Teams-Client mit Ihrem Webdienst verbinden, der über den Botdienst geroutet wird.

Das [Bot Framework ist](https://dev.botframework.com/) ein umfangreiches SDK, das zum Erstellen von Bots mithilfe von C#, Java, Python und JavaScript verwendet wird. Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn ganz einfach so ändern, dass er in der Microsoft Teams. Verwenden Sie C# oder Node.js, um unsere [SDKs zu nutzen.](/microsoftteams/platform/#pivot=sdk-tools) Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs folgendermaßen:

* Verwenden Sie spezielle Kartentypen wie Office 365 Connectorkarte.
* Legen Teams kanalspezifische Daten für Aktivitäten.
* Verarbeiten Sie Messaging-Erweiterungsanforderungen.

> [!IMPORTANT]
> Sie können Teams in jeder Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs direkt](/bot-framework/rest-api/bot-framework-rest-overview) aufrufen. Sie müssen jedoch in allen Fällen eine Tokenbehandlung durchführen.

> [!TIP]
> Teams App Studio hilft Ihnen beim Erstellen und Konfigurieren Ihres App-Manifests und beim Registrieren Ihres Webdiensts als Bot im Bot Framework. Es enthält auch eine React-Steuerungsbibliothek sowie einen Generator für interaktive Karten. Weitere Informationen finden Sie unter [Erste Schritte mit Teams App Studio](~/concepts/build-and-test/app-studio-overview.md).

## <a name="bots-and-the-microsoft-power-virtual-agents"></a>Bots und microsoft Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein chatbot-Dienst, der auf der Microsoft Power-Plattform und dem Bot Framework baut. Der Power Virtual Agent-Entwicklungsprozess verwendet einen geführten, code- und grafischen Benutzeroberflächenansatz, mit dem Ihre Teammitglieder einfach einen intelligenten virtuellen Agent erstellen und verwalten können. Nachdem Sie Ihren Chatbot im Power Virtual Agents [erstellt](https://powervirtualagents.microsoft.com)haben, können Sie ihn problemlos [in Teams.](how-to/add-power-virtual-agents-bot-to-teams.md) Weitere Informationen zu den ersten Schritte finden Sie [in Power Virtual Agents Dokumentation](https://docs.microsoft.com/power-virtual-agents/).

## <a name="bots-and-webhooks-and-connectors"></a>Bots und Webhooks und Connectors

Webhooks und Connectors verbinden Ihren Bot mit Ihren Webdiensten. Mithilfe von Webhooks und Connectors können Sie einen einfachen Bot für grundlegende Interaktionen erstellen, z. B. das Erstellen eines Workflows oder anderer einfacher Befehle. Sie sind nur im Team verfügbar, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie unter [Was sind Webhooks und Connectors](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="advantages-of-bots"></a>Vorteile von Bots

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet einzigartige Möglichkeiten und Herausforderungen für Ihren Unterhaltungsbot.

| In einem Kanal | In einem Gruppenchat | In einem 1:1-Chat. |
| :-- | :-- | :-- |
| Massive Reichweite | Weniger Mitglieder | Herkömmliche Methode |
| Präzise individuelle Interaktionen | @mention zum Bot  | Frage&Bots |
| @mention zum Bot | Ähnlich wie kanal | Bots, die Witze erzählen und Notizen machen |

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Threadunterhaltungen zwischen mehreren Personen sogar bis zu zweitausend. Dies bietet Ihrem Bot potenziell enorme Reichweite, einzelne Interaktionen müssen jedoch präzise sein. Herkömmliche Multi-Turn-Interaktionen funktionieren nicht. Stattdessen müssen Sie nach interaktiven Karten oder Aufgabenmodulen suchen oder die Unterhaltung in eine 1:1-Unterhaltung verschieben, um viele Informationen zu sammeln. Ihr Bot hat nur Zugriff auf Nachrichten, in denen er sich `@mentioned` befindet. Sie können zusätzliche Nachrichten aus der Unterhaltung mithilfe von Microsoft Graph Berechtigungen auf Organisationsebene abrufen.

Bots funktionieren in den folgenden Fällen besser in einem Kanal:

* Benachrichtigungen, bei denen Sie eine interaktive Karte für Benutzer bereitstellen, um zusätzliche Informationen zu erhalten.
* Feedbackszenarien, z. B. Umfragen und Umfragen.
* Einzelne Anfragen oder Reaktionszyklen lösen Interaktionen auf, und die Ergebnisse sind für mehrere Mitglieder der Unterhaltung nützlich.
* Social- oder Fun-Bots, in denen Sie ein großartiges Katzenbild erhalten, zufällig einen Gewinner auswählen und so weiter.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threads zwischen drei oder mehr Personen. Sie weisen tendenziell weniger Mitglieder auf als ein Kanal und sind kurzlebiger. Ähnlich wie bei einem Kanal hat Ihr Bot nur Zugriff auf Nachrichten, in denen er sich direkt `@mentioned` befindet.

In den Fällen, in denen Bots in einem Kanal besser funktionieren, funktionieren sie auch in einem Gruppenchat besser.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat.

Eins-zu-Eins-Chat ist eine herkömmliche Möglichkeit für einen Unterhaltungsbot, mit einem Benutzer zu interagieren. Einige Beispiele für 1:1-Unterhaltungsbots sind Q&A bots, Bots, die Workflows in anderen Systemen initiieren, Bots, die Witze erzählen, und Bots, die Notizen machen. Überlegen Sie vor dem Erstellen von 1:1-Chatbots, ob eine unterhaltungsbasierte Schnittstelle die beste Möglichkeit ist, Ihre Funktionalität zu präsentieren.

## <a name="disadvantages-of-bots"></a>Nachteile von Bots

Ein umfassendes Dialogfeld zwischen Ihrem Bot und dem Benutzer ist eine langsame und komplexe Methode, um eine Aufgabe fertig zu machen. Ein Bot, der exzessive Befehle unterstützt, insbesondere eine breite Palette von Befehlen, ist nicht erfolgreich oder wird von Benutzern positiv angezeigt.

### <a name="have-multi-turn-experiences-in-chat"></a>Multi-Turn-Erfahrungen im Chat

Für ein umfassendes Dialogfeld muss der Entwickler den Status beibehalten. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Zeit-Out oder Abbrechen **auswählen.** Außerdem ist der Prozess mühsam. Sehen Sie sich beispielsweise das folgende Unterhaltungsszenario an:

BENUTZER: Plane eine Besprechung mit Marie.

BOT: Ich habe 200 Ergebnisse gefunden, bitte geben Sie einen Vor- und Nachnamen an.

BENUTZER: Plane eine Besprechung mit Marie Krause.

BOT: OK, Wann möchten Sie sich mit Marie Krause treffen?

BENUTZER: um 13:00 Uhr.

BOT: An welchem Tag?

### <a name="support-too-many-commands"></a>Zu viele Befehle unterstützen

Da im aktuellen Botmenü nur sechs sichtbare Befehle enthalten sind, ist es unwahrscheinlich, dass weitere Befehle mit beliebiger Häufigkeit verwendet werden. Bots, die sich tief in einen bestimmten Bereich einarbeiten, anstatt zu versuchen, ein breiter Assistent zu sein und sich besser zu verbessern.

### <a name="maintain-a-large-knowledge-base"></a>Verwalten einer großen Wissensdatenbank

Einer der Nachteile von Bots ist, dass es schwierig ist, eine große Wissensdatenbank für Abrufe mit nicht getrunkenen Antworten zu unterhalten. Bots eignen sich am besten für kurze, schnelle Interaktionen und nicht für lange Listen, die nach einer Antwort suchen.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | . NETCore | Node.js |
|----------------|-----------------|--------------|----------------|
| Teams-Unterhaltungsbot | Nachrichten- und Unterhaltungsereignisbehandlung. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Aktivitätenhandler](~/bots/bot-basics.md)
