---
title: Microsoft Teams-Codebeispiele
description: Links und Beschreibungen von Beispielanwendungen für die Microsoft Teams-Entwicklerplattform
keywords: Microsoft Teams-Entwickler Beispiele
ms.openlocfilehash: eb7794e788f8eb39102ac874748e23d8621f281e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674066"
---
# <a name="code-samples-for-the-microsoft-teams-developer-platform"></a>Code Beispiele für die Microsoft Teams-Entwicklerplattform

Hier finden Sie eine Liste mit Codebeispielen, in denen verschiedene Funktionen der Microsoft Teams-Entwicklungsplattform veranschaulicht werden, und wie Sie Apps erstellen, um diese Funktionen zu nutzen.

## <a name="getting-samples"></a>Einholen von Beispielen

So laden Sie unsere Beispiele von GitHub herunter:

1. Wählen Sie eines der unten aufgeführten Projekte aus, und öffnen Sie das Projekt in GitHub.
2. Klicken Sie auf die Schaltfläche **Klonen oder herunterladen** und kopieren Sie die URL
3. Öffnen Sie eine Eingabeaufforderung im übergeordneten Verzeichnis, in dem Sie das Beispielprojekt installieren möchten.
4. Ausführen`git clone <pasted url>`

### <a name="for-netc-samples"></a>Für .NET/C#-Beispiele

Jedes unserer .net-Beispiele enthält eine Visual Studio Lösungsdatei, mit der die Lösung vollständig erstellt werden kann, einschließlich der Wiederherstellung der NuGet-Pakete.

### <a name="for-nodejs-samples"></a>Für node. js-Beispiele

Wir stellen eine Datei Packages. JSON bereit, die alle erforderlichen Pakete für ein Beispiel auflistet. Führen `npm install` Sie einfach von der Befehlszeile im Projektverzeichnis Node. js aus, um die erforderlichen Pakete zu installieren. Nun können Sie das Projekt in Visual Studio Code öffnen und mit dem Experimentieren beginnen.

### <a name="for-other-samples"></a>Für andere Beispiele

Wie immer sollte die Readme-Datei des Projekts weitere Informationen zu spezifischen Anforderungen für bestimmte Beispiele enthalten.

## <a name="get-started"></a>Erste Schritte

| Beispiel | Beschreibung|
|--------|-------------|
| [Hello World in Microsoft Teams mit Node. js](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) | Eine Beispiel-Microsoft Teams `Node.js` -APP, in der Sie die grundlegenden App-Funktionen vorgestellt haben.|
| [Hello World in Microsoft Teams mit C# .net](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) | Eine Beispiel-Microsoft Teams `C# .NET` -APP, in der Sie die grundlegenden App-Funktionen vorgestellt haben.|
| [Erste Schritte mit dem Landarbeits Generator für Microsoft Teams](~/tutorials/get-started-yeoman.md) | Erstellen Sie eine Teams-APP von Grund auf neu, indem Sie den Landarbeits Generator für Microsoft Teams verwenden. |

## <a name="bots-using-the-v4-sdk"></a>Bots (mit dem V4-SDK)

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="messaging-extensions-using-the-v4-sdk"></a>Messaging Erweiterungen (mithilfe des V4-SDK)

| Beispiel | Beschreibung | .NET Core | JavaScript |
|--------|------------- |---|---|
| Suchbefehl | Einfache Messaging Erweiterung mit einem Suchbefehl | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|
| Aktionsbefehl | Einfache Messaging Erweiterung mit einem Aktionsbefehl. Die Antwort wurde in den Bereich zum Verfassen von Nachrichten eingefügt. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)|
| Aktionsbefehl w/bot-Antwort | Messaging-Erweiterung mit einem Aktionsbefehl. Die Antwort wurde von dem bot in die Unterhaltung eingefügt. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/53.teams-messaging-extensions-action-preview)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/53.teams-messaging-extensions-action-preview)|
| Suchbefehl | Messaging-Erweiterung mit einem Suchbefehl und Authentifizierung und Konfiguration | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)|

## <a name="outgoing-webhooks"></a>Ausgehende webhooks

| Beispiel | Beschreibung
|--------|-------------
| [Ausgehende webhook für C#-/.net](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook) | Veranschaulicht das Erstellen eines **ausgehenden webhooks** für Microsoft Teams in C#/.net.
| [Ausgehendes webhook für Node. js](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs) | Zeigt, wie Sie einen einfachen **ausgehenden webhook** für Microsoft Teams in ~ 50 Zeilen mit dem Code Node. js erstellen.

## <a name="connectors"></a>Connectors

| Beispiel | Beschreibung
|--------|-------------
| [Beispiel-Konnektor für Node. js](https://github.com/OfficeDev/microsoft-teams-sample-connector-nodejs) | In diesem Beispiel, das in Node. js geschrieben ist, wird gezeigt, wie Sie einen Connector für Microsoft Teams mit GitHub als Beispiel zum Generieren von Connector-Benachrichtigungen erstellen.
| [Beispiel für Connector für C#-/.net](https://github.com/OfficeDev/microsoft-teams-sample-connector-csharp) | In diesem in C# geschriebenen Beispiel wird gezeigt, wie Sie einen Connector für Microsoft Teams mithilfe einer Beispiel-Aufgabenlisten-App als Beispiel zum Generieren von Connector-Benachrichtigungen erstellen.

## <a name="graph-api"></a>Graph-API

| Beispiel | Beschreibung
|--------|-------------
| [Microsoft Graph-API-Beispiele](https://github.com/OfficeDev/microsoft-teams-sample-graph) | In diesen Beispielen wird veranschaulicht, wie Sie mithilfe von Microsoft Graph-API-aufrufen Aufgaben wie das Abfragen von Teams und Kanälen von einem Webdienst ausführen, der außerhalb von Microsoft Teams ausgeführt wird.

## <a name="others"></a>Sonstige

| Code | Beschreibung |
|------|------------- |
| [Vollständiges Beispiel in Node. js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node) | In diesem Beispiel wird gezeigt, wie Sie alle Features der Microsoft Teams-Plattform verwenden. Hinweis: in diesem Beispiel wird das bot Framework V3 SDK verwendet.|
| [Vollständiges Beispiel in C#/.net](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp) | In diesem Beispiel wird gezeigt, wie Sie alle Features der Microsoft Teams-Plattform verwenden. Hinweis: in diesem Beispiel wird das bot Framework V3 SDK verwendet. |
| [Branchen-apps in C#/.net](https://github.com/OfficeDev/msteams-sample-line-of-business-apps-csharp) | Dieses Repository enthält mehrere Beispiel-Branchen-apps, die entweder als Inspiration oder als Vorlage zum Erstellen von oben verwendet werden können. Hinweis: in diesen Beispielen wird das bot Framework V3 SDK verwendet.|
| ["Aufgaben"-Registerkarten-Beispiel-App](https://github.com/OfficeDev/microsoft-teams-sample-todo) | Dieses node. js-Beispiel zeigt, wie einfach eine vorhandene Webanwendung in eine Registerkarte konvertiert werden kann. |
| [Orky](https://github.com/OfficeDev/Orky) | Sie können Orky verwenden, um Ihren eigenen lokalen bot in Microsoft Teams zu registrieren und Skripts von überall aus auszuführen. |
| [Build 2017 Wetter](https://github.com/OfficeDev/microsoft-teams-build2017-weather) | Veraltete. Quellcode für die unter//Build 2017-Sitzung zum Hinzufügen einer Wetter Registerkarte zur Skelett-APP, die zuvor in der Sitzung generiert wurde. |

### <a name="bot-framework-sdk-v3-samples"></a>Beispiele für bot Framework SDK v3

| Beispiel | Beschreibung |
|--------|------------- |
| [Beispiel bot für C#-/.net](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/CSharp/Samples/Microsoft.Bot.Connector.Teams.SampleBot) | Beispiele für bot Framework V3|
| [Beispiel-bot für Node. js](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/Node/samples) | Beispiele für bot Framework V3 |
