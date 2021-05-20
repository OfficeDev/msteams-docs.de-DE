---
title: Erste Schritte - Erstellen Sie Ihre erste App-Übersicht und -Voraussetzungen
author: girliemac
description: Erfahren Sie, wie Sie mit Microsoft Teams App-Entwicklung beginnen und Ihre Umgebung einrichten.
ms.author: timura
ms.date: 03/18/2021
ms.topic: quickstart
ms.openlocfilehash: dae942be9383ef1e0a931d238e6148651f334ef5
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565879"
---
# <a name="get-started-with-microsoft-teams-app-development"></a>Erste Schritte mit Microsoft Teams App-Entwicklung

Erstellen Sie eine einfache App, um die Grundlagen der Teams App-Entwicklung zu erlernen. Sobald Sie "Hello, World!" sehen, versuchen Sie einen der anderen ersten Artikel für weitere Informationen über allgemeine Tools, grundlegende Konzepte und erweiterte Funktionen.



## <a name="what-youll-learn"></a>Was Sie lernen werden

* Mit dem Teams Toolkit, einer Visual Studio Code-Erweiterung, können Sie schnell losfahren. 
* Konfigurieren Sie Ihre App mit App Studio.
* Machen Sie sich mit Teams Entwicklertools und SDKs vertraut.
* Berücksichtigen Sie wichtige Teams App-Konzepten, z. B. Authentifizierung und Best Practices für das Design.

Sie können eine Teams-App mit jeder Technologie Ihrer Wahl erstellen, z. B. Befehlszeilenschnittstelle (CLI). Diese Artikel helfen Ihnen jedoch bei den ersten Schritte mit den folgenden empfohlenen Tools und Technologien:

* Teams Toolkit, eine Visual Studio Code Erweiterung
* React.js für Tabs
* Node.js für Bots und Messaging-Erweiterungen


## <a name="teams-app-fundamentals"></a>Teams-App-Grundlagen

Sie können benutzerdefinierte Teams Apps für sich selbst, Personen in Ihrer Organisation oder Personen auf der ganzen Welt erstellen. Bevor Sie beginnen, sollten Sie die folgenden grundlegenden Konzepte zur Teams App-Entwicklung verstehen:

### <a name="common-app-use-cases"></a>Häufige Anwendungsfälle für Apps

Einige typische Szenarien, bei denen eine benutzerdefinierte Teams App helfen kann, sind:

* Einbetten webbasierter Inhalte, z. B. einer Web-App oder eines Teils einer Website, in den Teams Client.
* Suchen Sie Informationen schnell in einem anderen System und fügen Sie sie einer Teams Unterhaltung hinzu.
* Lösen Sie Workflows und Prozesse direkt aus dem, was in einer Unterhaltung gesagt wird.

### <a name="app-capabilities-and-tools"></a>App-Funktionen und -Tools

Eine App besteht aus einer oder mehreren Teams Funktionen und Benutzerinteraktionspunkten. Ihr Entwicklungstoolset hängt von den gewünschten Funktionen ab.

| **App-Funktionen**| **Interaktionspunkte** | **Empfohlene Werkzeuge** | **SDKs** | **Technologie-Stacks** |
|--------|--------|--------|--------|--------|
| Registerkarten | Räume, in denen Benutzer mit eingebetteten Webinhalten in persönlichen und freigegebenen Kontexten interagieren können. | VS Code mit Teams Toolkit-Erweiterung oder Yeoman Generator | Microsoft Teams JavaScript-Client-SDK | Allgemeine Webtechnologien (HTML, CSS und JavaScript) oder React.js |
| Bots | Chatbots, die mit Benutzern in persönlichen und gemeinsam genutzten Kontexten interagieren. | VS Code mit Teams Toolkit-Erweiterung oder Yeoman Generator | Bot Framework SDK | Node.js, C-Code oder Python | 
| Messaging-Erweiterungen | Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln auf einer Nachricht, ohne von der Unterhaltung weg zu navigieren. | VS Code mit Teams Toolkit-Erweiterung oder Yeoman Generator | Bot Framework SDK | Node.js, C-Code oder Python |

### <a name="teams-doesnt-host-your-app"></a>Teams hostt Ihre App nicht

Wenn ein Benutzer Ihre App in Teams installiert, installiert er nur ein App-Paket, das eine Konfigurationsdatei (auch als App-Manifest bezeichnet) und die Symbole Ihrer App enthält. Die Logik und der Datenspeicher Ihrer App werden an anderer Stelle gehostet, z. B. Azure Web Services oder localhost während der Entwicklung. Teams greift über HTTPS auf diese Ressourcen zu.

:::image type="content" source="../assets/images/build-your-first-app/app-in-cloud.png" alt-text="Abbildungen, die Ihre App auf Teams zeigen, verweisen auf Ihre App-Logik im Cloudserver.":::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen und Ausführen Ihrer ersten Teams-App](../build-your-first-app/build-and-run.md)
