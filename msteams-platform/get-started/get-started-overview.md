---
title: Erste Schritte – Übersicht
description: Beginnen. Erstellen Sie Ihre erste Microsoft Teams-App basierend auf Sprache (Node.js,C#, Java, Python) und Entwicklungsumgebung, und verstehen Sie die App-Funktionen, SDKs.
ms.localizationpriority: high
ms.topic: reference
ms.openlocfilehash: 4ad64240c97ab11da6a999f87621fdff6d70ebe2
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100434"
---
# <a name="get-started"></a>Erste Schritte

Willkommen bei den ersten Schritten für das Erstellen und Bereitstellen von angepassten Apps für Microsoft Teams!

Führen Sie die Schritte zum Erstellen einer einfachen, realen Teams-App durch. "Erste Schritte" führt Sie auch in allgemeine Tools, grundlegende Konzepte und erweiterte Features ein.

Hier ist eine Vorstellung davon, was Sie lernen werden:

- Beginnen Sie schnell mit dem Microsoft Teams Toolkit (einer Visual Studio Code-Erweiterung).
- Machen Sie sich mit dem Toolkit und SDKs vertraut.
- Konfigurieren und erstellen Sie verschiedene Arten von Teams-Apps.

Werfen wir einen kurzen Blick auf die Optionen der Buildumgebung, aus denen Sie auswählen können, und die Roadmap zum Erstellen und Bereitstellen einer Teams-App.

:::image type="content" source="../assets/images/get-started/gs-build-options.png" alt-text="Abbildung der grundlegenden Schritte zum Erstellen und Bereitstellen einer Teams-App":::

## <a name="app-capabilities-and-development-tools"></a>App-Funktionen und Entwicklungstools

Wählen Sie je nach gewünschten Funktionen für Ihre App einen geeigneten Satz von Entwicklungstool aus.

| App-Funktionen | Benutzerinteraktionen | Empfohlene Tools | SDKs | Technologiestapel / Sprachen |
|--------|-------------|--------|--------|--------|
| Registerkarten | Eine eingebettete Weboberfläche im Vollbildmodus. | Microsoft Visual Studio Code mit Teams-Toolkit-Erweiterung oder [TeamsFx CLI,](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) wenn Sie es bevorzugen, CLI zu nutzen | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) für wichtige Libs und [Teams-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) für UI-Funktionen | Webtechnologie im Allgemeinen HTML, CSS und JavaScript (inkl. React). |
| Bots | Ein Chat-Bot, der sich mit Mitgliedern unterhält. | Visual Studio Code mit Teams-Toolkit-Erweiterung oder [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) und [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C#, Java und Python. |
| Nachrichtenerweiterungen | Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten. | Visual Studio Code mit Teams-Toolkit-Erweiterung oder [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) und [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C#, Java und Python. |

*Sie sind nicht auf die Verwendung dieser speziellen Stapel beschränkt!*

Wenn Sie bereits mit dem Yeoman-Workflow vertraut sind, bevorzugen Sie möglicherweise die Verwendung von [YoTeams Yeoman Generator](https://github.com/pnp/generator-teams/blob/master/docs/docs/tutorials/build-your-first-microsoft-teams-app.md) zum Erstellen Ihrer Apps.

## <a name="build-your-first-teams-app"></a>Erstellen Ihrer ersten Teams-App

Nun erstellen wir Ihre erste Teams-App. Wählen Sie jedoch zunächst Ihre Sprache (oder das Framework) aus, und bereiten Sie Ihre Entwicklungsumgebung vor.

> [!div class="nextstepaction"]
> [Erstellen einer Registerkarten-App in Teams mit JavaScript, mithilfe von React](../sbs-gs-javascript.yml)
> [!div class="nextstepaction"]
> [Erstellen einer Bot-App in Teams mit JavaScript](../sbs-gs-bot.yml)
> [!div class="nextstepaction"]
> [Erstellen einer Nachrichtenerweiterungs-App in Teams mit JavaScript, mithilfe von React](../sbs-gs-msgext.yml)
> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit Blazor](../sbs-gs-blazorupdate.yml)
> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit SPFx](../sbs-gs-spfx.yml)
> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit C# oder .NET](../sbs-gs-csharp.yml)
> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit Node.js](../sbs-gs-nodejs.yml)
> [!div class="nextstepaction"]
> [Erstellen eines Benachrichtigungsbots mit JavaScript](../sbs-gs-notificationbot.yml)
> [!div class="nextstepaction"]
> [Erstellen eines Befehlsbots mit JavaScript](../sbs-gs-commandbot.yml)
> [!div class="nextstepaction"]

## <a name="see-also"></a>Siehe auch

- [Beispiele für Microsoft Teams](https://github.com/OfficeDev/Microsoft-Teams-Samples#microsoft-teams-samples)
- [Git- und GitHub-Ressourcen](/contribute/additional-resources)
