---
title: Microsoft Teams-Codebeispiele
description: Links und Beschreibungen von Beispielanwendungen für die Microsoft Teams-Entwicklerplattform
keywords: Microsoft Teams-Entwickler Beispiele
ms.openlocfilehash: 955588608fde694b163104d0a9e9e94289719003
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "44801303"
---
# <a name="tutorials-and-code-samples-for-the-microsoft-teams-developer-platform"></a>Lernprogramme und Codebeispiele für die Microsoft Teams-Entwicklerplattform

Hier finden Sie eine Liste der Lernprogramme und Codebeispiele, die veranschaulichen, wie Sie die Teams-Entwicklerplattform-Funktionen erweitern können, indem Sie benutzerdefinierte Apps erstellen.

## <a name="getting-started-with-microsoft-learn"></a>Erste Schritte mit Microsoft Learn

| Funktion| Lern Modul|
|--------|-------------|
| Registerkarten – eingebettete Webanwendungen  |  [Erstellen einer eingebetteten Weboberfläche mit Registerkarten für Microsoft Teams](https://docs.microsoft.com/learn/modules/embedded-web-experiences/) |
| Webhooks und Connectors  |  [Verbinden von Webdiensten mit Microsoft Teams mit Webhooks und Office 365-Connectors](https://docs.microsoft.com/learn/modules/msteams-webhooks-connectors/) |
|Messaging-Erweiterungen  | [Aufgabenorientierte Interaktionen in Microsoft Teams mit Messaging-Erweiterungen](https://docs.microsoft.com/learn/modules/msteams-messaging-extensions/)  |
| Aufgabenmodule |  [Sammeln von Eingaben in Microsoft Teams mit Aufgaben Modulen](https://docs.microsoft.com/learn/modules/msteams-task-modules/) |
| Unterhaltungs Bots  | [Erstellen von interaktiven Unterhaltungsbots für Microsoft Teams](https://docs.microsoft.com/learn/modules/msteams-conversation-bots/)  |

## <a name="getting-started-with-code-samples"></a>Erste Schritte mit Codebeispielen

So laden Sie unsere Beispiele von GitHub herunter:

1. Wählen Sie eines der unten aufgeführten Projekte aus, und öffnen Sie das Projekt in GitHub.
2. Klicken Sie auf die Schaltfläche **Klonen oder herunterladen** und kopieren Sie die URL
3. Öffnen Sie eine Eingabeaufforderung im übergeordneten Verzeichnis, in dem Sie das Beispielprojekt installieren möchten.
4. Ausführen`git clone <pasted url>`

### <a name="for-netc-samples"></a>Für .NET/C#-Beispiele

Jedes unserer .net-Beispiele enthält eine Visual Studio Lösungsdatei, mit der die Lösung vollständig erstellt werden kann, einschließlich der Wiederherstellung der NuGet-Pakete.

### <a name="for-nodejs-samples"></a>Node.js Beispiele

Wir stellen eine Datei packages.jsbereit, in der alle erforderlichen Pakete für ein Beispiel aufgelistet sind. Führen Sie einfach `npm install` von der Befehlszeile in Ihrem Node.js Projektverzeichnis aus, um die erforderlichen Pakete zu installieren. Nun können Sie das Projekt in Visual Studio Code öffnen und mit dem Experimentieren beginnen.

### <a name="for-other-samples"></a>Für andere Beispiele

Wie immer sollte die Readme-Datei des Projekts weitere Informationen zu spezifischen Anforderungen für bestimmte Beispiele enthalten.

## <a name="bots-using-the-v4-sdk"></a>Bots (mit dem V4-SDK)

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

>[!TIP]
>Besuchen Sie das [bot-Framework Samples Repository](https://github.com/Microsoft/BotBuilder-Samples) , um Microsoft bot Framework V4 SDK aufgabenorientierte Beispiele für C#, JavaScript, Schreibweise und python anzuzeigen.

## <a name="messaging-extensions-using-the-v4-sdk"></a>Messaging Erweiterungen (mithilfe des V4-SDK)

| Beispiel | Beschreibung | .NET Core | JavaScript | Python|
|--------|------------- |---|---|----|
| Suchbefehl | Einfache Messaging Erweiterung mit einem Suchbefehl | [Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)| [Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|[Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/50.teams-messaging-extension-search)|
| Aktionsbefehl | Einfache Messaging Erweiterung mit einem Aktionsbefehl. Die Antwort wurde in den Bereich zum Verfassen von Nachrichten eingefügt. | [Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)|[Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/51.teams-messaging-extensions-action)|
| Aktionsbefehl w/bot-Antwort | Messaging-Erweiterung mit einem Aktionsbefehl. Die Antwort wurde von dem bot in die Unterhaltung eingefügt. | [Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/53.teams-messaging-extensions-action-preview)|[Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/53.teams-messaging-extensions-action-preview)|[Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/53.teams-messaging-extensions-action-preview)|
| Suchbefehl | Messaging-Erweiterung mit einem Suchbefehl und Authentifizierung und Konfiguration | [Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)| [Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)|[Ansicht](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/52.teams-messaging-extensions-search-auth-config)|

## <a name="outgoing-webhooks"></a>Ausgehende webhooks

| Beispiel | Beschreibung
|--------|-------------
| [Ausgehende webhook für C#-/.net](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook) | Veranschaulicht das Erstellen eines **ausgehenden webhooks** für Microsoft Teams in C#/.net.
| [Ausgehende webhook für Node.js](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs) | Zeigt, wie Sie einen einfachen **ausgehenden webhook** für Microsoft Teams in ~ 50 Zeilen Node.js Code erstellen.

## <a name="connectors"></a>Connectors

| Beispiel | Beschreibung
|--------|-------------
| [Beispiel-Konnektor für Node.js](https://github.com/OfficeDev/microsoft-teams-sample-connector-nodejs) | In diesem Beispiel, das in Node.js geschrieben wurde, wird gezeigt, wie Sie einen Connector für Microsoft Teams mit GitHub als Beispiel zum Generieren von Connector-Benachrichtigungen erstellen.
| [Beispiel für Connector für C#-/.net](https://github.com/OfficeDev/microsoft-teams-sample-connector-csharp) | In diesem in C# geschriebenen Beispiel wird gezeigt, wie Sie einen Connector für Microsoft Teams mithilfe einer Beispiel-Aufgabenlisten-App als Beispiel zum Generieren von Connector-Benachrichtigungen erstellen.

## <a name="graph-api"></a>Graph-API

| Beispiel | Beschreibung
|--------|-------------
| [Microsoft Graph-API-Beispiele](https://github.com/OfficeDev/microsoft-teams-sample-graph) | In diesen Beispielen wird veranschaulicht, wie Sie mithilfe von Microsoft Graph-API-aufrufen Aufgaben wie das Abfragen von Teams und Kanälen von einem Webdienst ausführen, der außerhalb von Microsoft Teams ausgeführt wird.

### <a name="bot-framework-sdk-v3-samples"></a>Beispiele für bot Framework SDK v3

| Beispiel | Beschreibung |
|--------|------------- |
| [Beispiel bot für C#-/.net](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/CSharp/Samples/Microsoft.Bot.Connector.Teams.SampleBot) | Beispiele für bot Framework V3|
| [Beispiel bot für Node.js](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/Node/samples) | Beispiele für bot Framework V3 |
