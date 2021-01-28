---
title: App-Codebeispiele
description: Links und Beschreibungen von Beispielanwendungen für die Microsoft Teams-Entwicklerplattform
ms.topic: reference
keywords: Microsoft Teams – Entwicklerbeispiele
ms.openlocfilehash: f51ffb22a5e6b3b757d1971422adf955d95fb223
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014110"
---
# <a name="tutorials-and-code-samples-for-the-microsoft-teams-developer-platform"></a>Lernprogramme und Codebeispiele für die Microsoft Teams-Entwicklerplattform

Hier finden Sie eine Liste von Lernprogrammen und Codebeispielen, die veranschaulichen, wie Sie die Entwicklerplattformfunktionen von Teams durch Erstellen benutzerdefinierter Apps erweitern können.

## <a name="getting-started-with-microsoft-learn"></a>Erste Schritte mit Microsoft Learn

| Funktion| Lernmodul|
|--------|-------------|
| Registerkarten – eingebettete Weberfahrungen  |  [Erstellen einer eingebetteten Weboberfläche mit Registerkarten für Microsoft Teams](https://docs.microsoft.com/learn/modules/embedded-web-experiences/) |
| Webhooks und Connectors  |  [Verbinden von Webdiensten mit Microsoft Teams mit Webhooks und Office 365-Connectors](https://docs.microsoft.com/learn/modules/msteams-webhooks-connectors/) |
|Messaging-Erweiterungen  | [Aufgabenorientierte Interaktionen in Microsoft Teams mit Messaging-Erweiterungen](https://docs.microsoft.com/learn/modules/msteams-messaging-extensions/)  |
| Aufgabenmodule |  [Sammeln von Eingaben in Microsoft Teams mit Aufgabenmodulen](https://docs.microsoft.com/learn/modules/msteams-task-modules/) |
| Unterhaltungsbots  | [Erstellen von interaktiven Unterhaltungsbots für Microsoft Teams](https://docs.microsoft.com/learn/modules/msteams-conversation-bots/)  |

## <a name="getting-started-with-code-samples"></a>Erste Schritte mit Codebeispielen

So laden Sie unsere Beispiele von GitHub herunter:

1. Wählen Sie eines der unten aufgeführten Projekte aus, und öffnen Sie das Projekt in GitHub.
2. Klicken Sie auf die **Schaltfläche "Klonen"** oder "Herunterladen", und kopieren Sie die URL.
3. Öffnen Sie eine Eingabeaufforderung im übergeordneten Verzeichnis, in dem Sie das Beispielprojekt installieren möchten.
4. Ausführen `git clone <pasted url>`

### <a name="for-netc-samples"></a>Für .NET/C#-Beispiele

Jedes unserer .NET-Beispiele enthält eine Visual Studio Lösungsdatei, die die Lösung vollständig erstellen kann, einschließlich der Wiederherstellung der NuGet-Pakete.

### <a name="for-nodejs-samples"></a>For Node.js samples

Wir bieten eine packages.jsdatei, die alle erforderlichen Pakete für ein Beispiel auflistet. Führen Sie einfach die Befehlszeile in Ihrem Node.js aus, um `npm install` die erforderlichen Pakete zu installieren. Jetzt können Sie das Projekt in Visual Studio Code öffnen und mit dem Experimentieren beginnen.

### <a name="for-other-samples"></a>Für andere Beispiele

Wie immer sollte die README-Datei des Projekts über weitere Informationen zu bestimmten Anforderungen für bestimmte Beispiele verfügen.

## <a name="bots-using-the-v4-sdk"></a>Bots (mit dem v4 SDK)

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

>[!TIP]
>Besuchen Sie [das Bot Framework-Beispielrepository,](https://github.com/Microsoft/BotBuilder-Samples) um aufgabenorientierte Microsoft Bot Framework v4 SDK-Beispiele für C#, JavaScript, TypeScript und Python zu sehen.

## <a name="messaging-extensions-using-the-v4-sdk"></a>Messagingerweiterungen (mit dem v4 SDK)

| Beispiel | Beschreibung | .NET Core | JavaScript | Python|
|--------|------------- |---|---|----|
| Messagingerweiterungen – Suche | Messaging-Erweiterung, die Suchanforderungen akzeptiert und Ergebnisse zurückgibt. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
| Messagingerweiterungen – Aktion | Messaging-Erweiterung, die Parameter akzeptiert und eine Karte zurückgibt. Außerdem erfahren Sie, wie Sie eine weitergeleitete Nachricht als Parameter in einer Nachrichtenerweiterung empfangen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Messagingerweiterungen – Authentifizierung und Konfiguration | Messaging-Erweiterung, die über eine Konfigurationsseite verfügt, Suchanforderungen akzeptiert und Ergebnisse zurückgibt, nachdem sich der Benutzer angemeldet hat. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) |
| Messagingerweiterungen – Aktionsvorschau | Veranschaulicht das Erstellen eines Vorschau- und Bearbeitungsflusses für eine Messagingerweiterung. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/53.teams-messaging-extensions-action-preview) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/53.teams-messaging-extensions-action-preview) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/53.teams-messaging-extensions-action-preview) |
| Entfalten von Links | Messaging-Erweiterung, die das Auffing von Links durchführt. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/55.teams-link-unfurling) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/55.teams-link-unfurling) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/55.teams-link-unfurling) |


## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

| Beispiel | Beschreibung
|--------|-------------
| [Ausgehender Webhook für C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook) | Veranschaulicht das Erstellen eines **ausgehenden Webhooks** für Microsoft Teams in C#/.NET.
| [Ausgehender Webhook für Node.js](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs) | Veranschaulicht, wie sie einen einfachen ausgehenden **Webhook** für Microsoft Teams in ca. 50 Zeilen Node.js erstellen.

## <a name="connectors"></a>Connectors

| Beispiel | Beschreibung
|--------|-------------
| [Beispielconnector für Node.js](https://github.com/OfficeDev/microsoft-teams-sample-connector-nodejs) | In diesem beispiel, das in Node.js geschrieben wurde, wird gezeigt, wie Sie einen Connector für Microsoft Teams erstellen, indem Sie GitHub als Beispiel zum Generieren von Connectorbenachrichtigungen verwenden.
| [Beispielconnector für C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-connector-csharp) | In diesem in C# geschriebenen Beispiel wird gezeigt, wie Ein Connector für Microsoft Teams mithilfe einer Beispiel-Aufgabenlisten-App als Beispiel zum Generieren von Connectorbenachrichtigungen erstellt wird. In diesem Beispiel wird auch gezeigt, wie die Anmeldefunktionalität auf der Connectorkonfigurationsseite implementiert wird. 

## <a name="graph-api"></a>Graph-API

| Beispiel | Beschreibung
|--------|-------------
| [Microsoft Graph-API-Beispiele](https://github.com/OfficeDev/microsoft-teams-sample-graph) | Diese Beispiele veranschaulichen die Verwendung von Microsoft Graph-API-Aufrufen, um Aufgaben auszuführen, z. B. das Abfragen von Teams und Kanälen von einem Webdienst, der außerhalb von Microsoft Teams ausgeführt wird.

### <a name="bot-framework-sdk-v3-samples"></a>Bot Framework SDK v3-Beispiele

| Beispiel | Beschreibung |
|--------|------------- |
| [Beispielbot für C#/.NET](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/CSharp/Samples/Microsoft.Bot.Connector.Teams.SampleBot) | Bot Framework v3-Beispiele|
| [Beispielbot für Node.js](https://github.com/OfficeDev/BotBuilder-MicrosoftTeams/tree/master/Node/samples) | Bot Framework v3-Beispiele |
