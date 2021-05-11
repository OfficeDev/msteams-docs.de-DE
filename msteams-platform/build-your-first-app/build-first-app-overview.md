---
title: Erste Schritte – Erstellen Der ersten App-Übersicht und der voraussetzungen
author: girliemac
description: Erfahren Sie, wie Sie mit Microsoft Teams app-Entwicklung beginnen und Ihre Umgebung einrichten.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: 3bc99c535ea659f046b65dc26d9a60de0dd49cab
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068573"
---
# <a name="get-started-with-microsoft-teams-app-development"></a>Erste Schritte mit Microsoft Teams App-Entwicklung

Erstellen Sie eine einfache App, um die Grundlagen der Teams zu erlernen. Sobald Sie "Hello, World!" sehen, testen Sie einen der anderen Artikel für erste Schritte, um weitere Informationen zu allgemeinen Tools, grundlegenden Konzepten und erweiterten Features zu erhalten.



## <a name="what-youll-learn"></a>Was Sie lernen werden

* Schnelles Ausführen mit dem Teams Toolkit, einer Visual Studio Code Erweiterung 
* Konfigurieren Ihrer App mit App Studio 
* Machen Sie sich mit Teams Und SDKs vertraut
* Berücksichtigen wichtiger Teams-App-Konzepte, z. B. Authentifizierungs- und Entwurfs best practices

Sie können eine Teams mit einer beliebigen Technologie erstellen, z. B. der Befehlszeilenschnittstelle (CLI). Diese Artikel helfen Ihnen jedoch, mit den folgenden empfohlenen Tools und Technologien zu beginnen:

* Teams Toolkit, eine Visual Studio Code Erweiterung
* React.js für Registerkarten
* Node.js für Bots und Messagingerweiterungen


## <a name="teams-app-fundamentals"></a>Teams der App

Sie können benutzerdefinierte Teams für sich selbst, Personen in Ihrer Organisation oder Personen auf der ganzen Welt erstellen. Bevor Sie beginnen, sollten Sie die folgenden grundlegenden Konzepte zur Entwicklung Teams verstehen:

### <a name="common-app-use-cases"></a>Häufige Anwendungsfälle für Apps

Einige typische Szenarien, bei denen eine benutzerdefinierte Teams-App hilfreich sein kann, sind:

* Einbetten webbasierter Inhalte, z. B. einer Web-App oder eines Teils einer Website, in den Teams Client
* Schnelles Suchen von Informationen in einem anderen System und Hinzufügen zu einer Teams Unterhaltung 
* Auslösen von Workflows und Prozessen direkt aus dem, was in einer Unterhaltung gesagt wird 

### <a name="app-capabilities-and-tools"></a>App-Funktionen und -Tools

Eine App besteht aus einem oder mehreren Teams und Benutzerinteraktionspunkten. Ihr Entwicklungstoolset variiert je nach den von Ihnen verwendeten Funktionen.

| **App-Funktionen**| **Interaktionspunkte** | **Empfohlene Tools** | **SDKs** | **Technologiestapel** |
|--------|--------|--------|--------|--------|
| Registerkarten | Räume, in denen Benutzer mit eingebetteten Webinhalten in persönlichen und freigegebenen Kontexten interagieren können | VS Code mit Teams Toolkit-Erweiterung oder Yeoman-Generator | Microsoft Teams JavaScript-Client-SDK | Allgemeine Webtechnologien (HTML, CSS und JavaScript) oder React.js |
| Bots | Chatbots, die mit Benutzern in persönlichen und freigegebenen Kontexten interagieren | VS Code mit Teams Toolkit-Erweiterung oder Yeoman-Generator | Bot Franework SDK | Node.js, C# oder Python | 
| Messaging-Erweiterungen | Verknüpfungen zum Einfügen von App-Inhalten oder Zum Handeln in einer Nachricht, ohne aus der Unterhaltung zu navigieren | VS Code mit Teams Toolkit-Erweiterung oder Yeoman-Generator | Bot Framework SDK | Node.js, C# oder Python |

### <a name="teams-doesnt-host-your-app"></a>Teams hosten Ihre App nicht

Wenn ein Benutzer Ihre App in Teams installiert, installiert er nur ein App-Paket, das eine Konfigurationsdatei (auch als App-Manifest bezeichnet) und die Symbole Ihrer App enthält. Die Logik und datenspeicherung Ihrer App werden an anderer Stelle gehostet, z. B. Azure Web Services oder localhost während der Entwicklung. Teams über HTTPS auf diese Ressourcen zu.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Abbildung, die Ihre App auf Teams zeigt, zeigt auf Ihre App-Logik auf dem Cloudserver.":::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen und Ausführen der ersten Teams App](../build-your-first-app/build-and-run.md)
