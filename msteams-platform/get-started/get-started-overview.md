---
title: Erste Schritte – Übersicht
description: Übersicht über die ersten Schritte für Microsoft Teams-Entwicklerdokumentation
ms.localizationpriority: medium
ms.topic: reference
keywords: Microsoft Teams Entwicklerbeispiele
ms.openlocfilehash: cb498d176b8893a2097e19ca76120a33a5f7221c
ms.sourcegitcommit: a2d7d2bdf4b056b35f29c6fdb315bc7dc28b6f6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2021
ms.locfileid: "61569497"
---
# <a name="get-started"></a>Erste Schritte

Willkommen bei den ersten Schritten für das Erstellen und Bereitstellen von angepassten Apps für Microsoft Teams!

Führen Sie die Schritte zum Erstellen einer einfachen, realen Teams-App durch. "Erste Schritte" führt Sie auch in allgemeine Tools, grundlegende Konzepte und erweiterte Features ein.

Hier ist eine Vorstellung davon, was Sie lernen werden:

- Beginnen Sie schnell mit dem Microsoft Teams Toolkit (einer Visual Studio Code-Erweiterung).
- Machen Sie sich mit dem Toolkit und SDKs vertraut.
- Konfigurieren und erstellen Sie verschiedene Arten von Teams-Apps.

Werfen wir einen kurzen Blick auf die Optionen der Buildumgebung, aus denen Sie wählen können, und die Roadmap zum Erstellen und Bereitstellen einer Teams App.

:::image type="content" source="../assets/images/get-started/gs-build-options.png" alt-text="Abbildung der grundlegenden Schritte zum Erstellen und Bereitstellen einer Teams App":::

## <a name="app-capabilities-and-development-tools"></a>App-Funktionen und Entwicklungstools

Wählen Sie je nach gewünschten Funktionen für Ihre App einen geeigneten Satz von Entwicklungstool aus.

| App-Funktionen | Benutzerinteraktionen | Empfohlene Tools | SDKs | Technologiestapel/Sprachen |
|--------|-------------|--------|--------|--------|
| Registerkarten | Eine eingebettete Weboberfläche im Vollbildmodus. | VS Code mit Teams Toolkit-Erweiterung oder [TeamsFx CLI,](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) wenn Sie CLI bevorzugen | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) für kernbibliotheken und [Teams-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) für UI-Funktionen | Webtechnologie im Allgemeinen HTML, CSS und JavaScript (incl. React). |
| Bots | Ein Chat-Bot, der sich mit Mitgliedern unterhält. | VS Code mit Teams Toolkit-Erweiterung oder [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) und [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C#, Java und Python. |
| Messaging-Erweiterungen | Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten. | VS Code mit Teams Toolkit-Erweiterung oder [TeamsFx CLI](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) | [TeamsFx SDK](/javascript/api/@microsoft/teamsfx/?view=msteams-client-js-latest&preserve-view=true) und [Bot Framework SDK](https://dev.botframework.com/) | Node.js, C#, Java und Python. |

*Sie sind nicht auf die Verwendung dieser speziellen Stapel beschränkt!*

Wenn Sie bereits mit dem Yeoman-Workflow vertraut sind, bevorzugen Sie möglicherweise die Verwendung von [YoTeams Yeoman Generator](https://github.com/pnp/generator-teams/blob/master/docs/docs/tutorials/build-your-first-microsoft-teams-app.md) zum Erstellen Ihrer Apps.

> [!NOTE]
> Wenn Sie App Studio verwendet haben, empfehlen wir, das Entwicklerportal zum Konfigurieren, Verteilen und Verwalten Ihrer Teams-Apps zu testen.


## <a name="build-your-first-teams-app"></a>Erstellen Ihrer ersten Teams-App

Nun erstellen wir Ihre erste Teams-App. Wählen Sie jedoch zunächst Ihre Sprache (oder Das Framework) aus, und bereiten Sie Ihre Entwicklungsumgebung vor.

> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit JavaScript mit React](../sbs-gs-javascript.yml)

> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit SPFx](../sbs-gs-spfx.yml)

> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit C# oder .NET](../sbs-gs-csharp.yml)

> [!div class="nextstepaction"]
> [Erstellen einer Teams-App mit Node.js](../sbs-gs-nodejs.yml)

## <a name="see-also"></a>Siehe auch

[Beispiele für Microsoft Teams](https://github.com/OfficeDev/Microsoft-Teams-Samples#microsoft-teams-samples)
