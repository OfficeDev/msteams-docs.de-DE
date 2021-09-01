---
title: App-Codebeispiele
description: Links und Beschreibungen von Beispielanwendungen für die Microsoft Teams-Entwicklerplattform
localization_priority: Normal
ms.topic: reference
keywords: Microsoft Teams Entwicklerbeispiele
ms.openlocfilehash: c261aebc327d09265db8831c2b7a8549f30a34fe
ms.sourcegitcommit: 68f5411f5989ac706b6a4a7b2884296e145fe7c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2021
ms.locfileid: "58849426"
---
# <a name="overview"></a>Übersicht

In diesem Lernprogramm erfahren Sie, wie Sie eine App mit React, SPFx, C# oder .NET, Node.js und Yeoman Generator erstellen. Außerdem erfahren Sie, wie Sie Ihren ersten Bot und Ihre erste Messaging-Erweiterung erstellen. Dieses Lernprogramm führt Sie durch mehrere Codebeispiele für Registerkarten, Bots, Messaging-Erweiterungen, Webhooks und Connectors und Graph-APIs, mit denen Sie Ihre Apps anpassen und konfigurieren können. Darüber hinaus können Sie sich auch in den Microsoft Learn-Abschnitten informieren, in denen Sie die Funktionen der Teams Entwicklerplattform erweitern können, indem Sie benutzerdefinierte Apps erstellen.  

## <a name="getting-started-with-microsoft-learn"></a>Erste Schritte mit Microsoft Learn

| **Funktionalität**| **Lernmodul**|
|--------|-------------|
| Registerkarten – eingebettete Weboberflächen  |  [Erstellen einer eingebetteten Weboberfläche mit Registerkarten für Microsoft Teams](/learn/modules/embedded-web-experiences/) |
| Webhooks und Connectors  |  [Verbinden von Webdiensten mit Microsoft Teams mit Webhooks und Office 365-Connectors](/learn/modules/msteams-webhooks-connectors/) |
|Messaging-Erweiterungen  | [Aufgabenorientierte Interaktionen in Microsoft Teams mit Messaging-Erweiterungen](/learn/modules/msteams-messaging-extensions/)  |
| Aufgabenmodule |  [Sammeln von Eingaben in Microsoft Teams mit Aufgabenmodulen](/learn/modules/msteams-task-modules/) |
| Unterhaltungs-Bots  | [Erstellen von interaktiven Unterhaltungsbots für Microsoft Teams](/learn/modules/msteams-conversation-bots/)  |

## <a name="build-your-first-microsoft-teams-app-overview"></a>Erstellen Ihrer ersten Microsoft Teams App-Übersicht

In den **ersten** Lektionen erfahren Sie, wie Sie grundlegende Teams-Apps erstellen. Jedes Lernprogramm führt Sie durch die Erstellung einer einfachen, realen Teams-App und führt Sie mit allgemeinen Tools, grundlegenden Konzepten und erweiterten Features ein.

### <a name="teams-app-fundamentals"></a>Grundlagen Teams App

Mit [der Teams Entwicklerplattform](../overview.md) können Sie benutzerdefinierte Apps erstellen. Einige häufige Szenarios, im Rahmen derer eine benutzerdefinierte Microsoft Teams-App hilfreich sein kann, lauten wie folgt:

* Betten Sie Ihre Website oder Web App direkt in den Teams-Client ein.
* Helfen Sie Benutzern, Schnellinformationen in einem anderen System nachzuschlagen und die Ergebnisse einer Unterhaltung in Teams hinzuzufügen.
* Initiieren Sie Workflows und Prozesse basierend auf einer Unterhaltung in Microsoft Teams, und behalten Sie dabei den Kontext der Unterhaltung bei.

Bevor Sie mit den Lernprogrammen beginnen, sollten Sie Folgendes über das Erstellen von Apps für Teams wissen.

### <a name="app-capabilities"></a>App-Funktionen

Eine Teams App besteht aus einer oder mehreren [Plattformfunktionen](../concepts/capabilities-overview.md) und [Benutzerinteraktionspunkten.](../concepts/extensibility-points.md)

Je nachdem, welche Funktionen Sie für Ihre App benötigen, benötigen Sie ein entsprechendes Entwicklungstoolset.

| App-Funktionen | Benutzerinteraktionen | Empfohlene Tools | SDKs | Technologiestapel |
|--------|-------------|--------|--------|--------|
| Registerkarten | Eine eingebettete Weboberfläche im Vollbildmodus. | VS Code mit Teams Toolkit-Erweiterung oder YoTeams (Yeoman Generator) | [Teams-Client-SDK](/javascript/api/overview/msteams-client) | Webtechnologie im Allgemeinen, HTML, CSS und JavaScript |
| Bots | Ein Chat-Bot, der sich mit Mitgliedern unterhält. | VS Code mit Teams Toolkit-Erweiterung oder YoTeams (Yeoman Generator) | [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C# oder Python |
| Messaging-Erweiterungen | Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten. | VS Code mit Teams Toolkit-Erweiterung oder YoTeams (Yeoman Generator) | [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C# oder Python |

Der Abschnitt "Erste Schritte" führt Sie durch empfohlene Toolsätze und häufig verwendete Technologien, z. B. Visual Studio Code mit Teams Erweiterung, React.js für Registerkarten und Node.js für Bots und Messaging-Erweiterungen, obwohl *Sie nicht auf die Verwendung dieser bestimmten Stapel beschränkt sind.*

Wenn Sie lieber eine Befehlszeilenschnittstelle (CLI) verwenden möchten, lesen Sie die Informationen zum [Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Yeoman-Generators.](../get-started/get-started-yeoman.md)

### <a name="teams-does-not-host-your-app"></a>Teams hosten Ihre App nicht

Sie installieren nur ein App-Paket mit einer Konfigurationsdatei, die als Manifest- und App-Symbole bezeichnet wird, auf Teams Client. Die restlichen App-Logiken und der Datenspeicherung werden an anderer Stelle gehostet, z. B. azure-Webdienste. Ihre App in der Cloud oder localhost während der Entwicklung greift über HTTPS auf Teams zu.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Abbildung der App auf Teams zeigt auf Ihre App-Logik auf dem Cloudserver.":::

## <a name="see-also"></a>Siehe auch

* [Erstellen einer App mit React](first-app-react.md)
* [Erstellen einer App mitHilfe von Blatter](first-app-blazor.md)
* [Erstellen einer App mit SPFx](first-app-spfx.md)
* [Erstellen einer App mithilfe von C# oder .NET](get-started-dotnet-app-studio.md)
* [Erstellen einer App mithilfe von Node.js](get-started-nodejs-app-studio.md)
* [Erstellen einer App mithilfe des Yeoman-Generators](get-started-yeoman.md)
* [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
* [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)
