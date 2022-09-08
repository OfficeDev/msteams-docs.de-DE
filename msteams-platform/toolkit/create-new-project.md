---
title: Erstellen einer neuen Teams-App
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie eine neue Teams-App mithilfe des Teams-Toolkits erstellen.
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: 8500f5ba1f54b28f68f9b56c0a42aedfff108e64
ms.sourcegitcommit: c806c5ffe277c740d0d7b8f62e72ade562029194
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617796"
---
# <a name="create-a-new-teams-project"></a>Erstellen eines neuen Teams-Projekts

Sie können ein neues Teams-Projekt erstellen, indem Sie im **Teams-Toolkit die Option "Neue Teams-App erstellen"** auswählen. Sie können folgende Arten von Apps im Teams-Toolkit erstellen:

| App-Typ | Definition |
| --- | --- |
| Einfache Teams-App | Grundlegende Teams-Apps sind Registerkarten-, Bot- oder Nachrichtenerweiterungs-Apps, die Sie basierend auf Ihren Anforderungen erstellen und anpassen können. |
| Szenariobasierte Teams-App | Szenariobasierte Teams-Apps sind Benachrichtigungs-Bot, Befehls-Bot, SSO-aktivierte Registerkarte oder SPFx-Registerkarten-App und für ein bestimmtes Szenario geeignet. Beispielsweise eignet sich der Benachrichtigungs-Bot nur zum Senden von Benachrichtigungen und nicht zum Chat. |

## <a name="create-a-new-teams-app"></a>Erstellen einer neuen Teams-App

Die Schritte zum Erstellen einer neuen Teams-App sind für alle App-Typen mit Ausnahme von SPFx und Benachrichtigungs-Bot ähnlich. Die folgenden Schritte helfen Ihnen beim Erstellen einer neuen Registerkarten-App:

**So erstellen Sie eine App**

1. Öffnen Sie Visual Studio Code.

1. Wählen Sie in der linken Navigationsleiste das Symbol für das Teams-Toolkit :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png"::: aus.

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. Stellen Sie sicher, dass **die Registerkarte** als App-Funktion ausgewählt ist.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-capabilities-tabapp.png" alt-text="App-Funktion auswählen":::

1. Wählen Sie **JavaScript** als Programmiersprache aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-language-tab.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie **"Standardordner** " aus, um den Projektstammordner am Standardspeicherort zu speichern.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-default-location.png" alt-text="Standardspeicherort auswählen":::

   Die folgenden Schritte führen Sie zum Ändern des Standardspeicherorts:

      1. Wählen Sie **"Durchsuchen"** aus.

          :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/select-browse.png" alt-text="Wählen Sie &quot;Nach Speicher suchen&quot; aus.":::

      1. Wählen Sie den Speicherort für den Projektarbeitsbereich aus.

      1. Wählen Sie den **Ordner auswählen** aus.

          :::image type="content" source="../assets/images/teams-toolkit-v2/select-folder.png" alt-text="select-folder for storage":::

1. Geben Sie `helloworld` als Anwendungsnamen ein. Stellen Sie sicher, dass Sie nur alphanumerische Zeichen verwenden. Drücken Sie die **EINGABETASTE**.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/enter-name-tab1.png" alt-text="Screenshot, der zeigt, wo der App-Name eingegeben werden soll.":::

1. Standardmäßig wird das Projekt innerhalb von 10 Sekunden in einem neuen Fenster geöffnet. Wenn Sie das Fenster im aktuellen Fenster öffnen möchten, wählen Sie **"Im aktuellen Fenster öffnen**" aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/new-window-notification.png" alt-text="Benachrichtigung über das neue Fenster":::

   Die Teams-Registerkarten-App wird in wenigen Sekunden erstellt.

    :::image type="content" source="../assets/images/teams-toolkit-v2/first-tab/tap-app-created1.png" alt-text="Screenshot der erstellten App.":::


### <a name="directory-structure-for-different-app-types"></a>Verzeichnisstruktur für verschiedene App-Typen

Das Teams-Toolkit stellt alle Komponenten zum Erstellen einer App bereit. Nachdem Sie das Projekt erstellt haben, können Sie die Projektordner und Dateien unter **Explorer** anzeigen.

<br>
<details>
<summary><b>Verzeichnisstruktur für die grundlegende Teams-App</b></summary>

Sie haben drei verschiedene Arten von grundlegenden Teams-Apps, und die Verzeichnisstruktur sieht für alle Arten von Apps ähnlich aus. Das folgende Beispiel zeigt eine grundlegende Verzeichnisstruktur der Teams-Registerkarten-App:

| Ordnername | Inhalt |
| --- | --- |
| `.fx/configs` | Konfigurationsdateien, die Benutzer für die Teams-App anpassen können. |
| - `.fx/configs/config.<envName>.json` | Konfigurationsdatei für jede Umgebung. |
| - `.fx/configs/azure.parameters.<envName>.json` | Parameterdatei für die Azure BICEP-Bereitstellung für jede Umgebung. |
| - `.fx/configs/projectSettings.json` | Globale Projekteinstellungen, die für alle Umgebungen gelten. |
| `tabs` | Code für die zur Laufzeit erforderliche Registerkartenfunktion, z. B. datenschutzhinweis, Nutzungsbedingungen und Konfigurationsregisterkarten. |
| - `tabs/src/index.jsx` | Einstiegspunkt für die Front-End-App, in der die Hauptkomponente der App gerendert wird `ReactDOM.render()` |
| - `tabs/src/components/App.jsx` | Code für die Behandlung von URL-Routing in der App. Es ruft das [Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) auf, um die Kommunikation zwischen Ihrer App und Microsoft Teams herzustellen. |
| - `tabs/src/components/Tab.jsx` | Code zum Implementieren der Benutzeroberfläche Ihrer App. |
| - `tabs/src/components/TabConfig.jsx` | Code zum Implementieren der Benutzeroberfläche, die Ihre App konfiguriert. |
| `templates/appPackage` | App-Manifestvorlagendateien und die App-Symbole: color.png und outline.png. |
| - `templates/appPackage/manifest.template.json` | App-Manifest zum Ausführen der App in einer lokalen oder Remoteumgebung.  |
| `templates/azure` | BICEP-Vorlagendateien |

> [!NOTE]
> Wenn Sie über eine Bot- oder Nachrichtenerweiterungs-App verfügen, werden der Verzeichnisstruktur relevante Ordner hinzugefügt.

Weitere Informationen zur Verzeichnisstruktur verschiedener Typen von grundlegenden Teams-Apps finden Sie in der folgenden Tabelle:

| App-Typ | Links |
| --- | --- |
| Für Registerkarten-App | [Erstellen Ihrer ersten Registerkarten-App mit JavaScript](../sbs-gs-javascript.yml) |
| Für Bot-App | [Erstellen Ihrer ersten Bot-App mit JavaScript](../sbs-gs-bot.yml) |
| Für Nachrichtenerweiterungs-App | [Erstellen Ihrer ersten Nachrichtenerweiterungs-App mit JavaScript](../sbs-gs-msgext.yml) |

</details>
<br>
<details>
<summary><b>Verzeichnisstruktur für szenariobasierte Teams-App</b></summary>

Sie haben vier verschiedene Arten von szenariobasierten Teams-Apps, und die Verzeichnisstruktur sieht für alle Arten von Apps ähnlich aus. Das folgende Beispiel zeigt eine szenariobasierte Benachrichtigungs-Bot-Teams-App-Verzeichnisstruktur:

Der neue Projektordner enthält folgende Inhalte:

| Ordnername | Inhalt |
| --- | --- |
| `.fx` | Einstellungen, Konfiguration und Umgebungsinformationen auf Projektebene |
| `.vscode` | VS-Codedateien für das lokale Debuggen |
| `bot` | Der Bot-Quellcode |
| `templates` | Vorlagen für teams-App-Manifest und entsprechende Azure-Ressourcen |

Die Kern-Benachrichtigungsimplementierung im **Bot-Ordner** und enthält:

| Dateiname | Inhalt |
| --- | --- |
| `src/adaptiveCards/` | Vorlagen für adaptive Karten  |
| `src/internal/` | Generierter Initialisierungscode für Benachrichtigungsfunktionen |
| `src/index.*s` | Der Einstiegspunkt zum Behandeln von Bot-Nachrichten und Senden von Benachrichtigungen |
| `.gitignore` | Datei zum Ausschließen lokaler Dateien aus dem Botprojekt |
| `package.json` | Die npm-Paketdatei für das Bot-Projekt |

> [!NOTE]
> Wenn Sie über einen Befehls-Bot, eine SSO-aktivierte Registerkarte oder eine SPFx-Registerkarten-App verfügen, werden der Verzeichnisstruktur relevante Ordner hinzugefügt.

Weitere Informationen zur Verzeichnisstruktur verschiedener Szenario-basierter Teams-App-Typen finden Sie in der folgenden Tabelle:

| App-Typ | Links |
| --- | --- |
| Für Benachrichtigungs-Bot-App | [Benachrichtigung an Teams senden](../sbs-gs-notificationbot.yml) |
| Für Befehls-Bot-App | [Befehlsbot erstellen](../sbs-gs-commandbot.yml) |
| Für die SPFx-Registerkarten-App | [Erstellen einer Teams-App mit SPFx](../sbs-gs-spfx.yml) |

</details>
<br>
<details>
<summary><b>Verzeichnisstruktur für App mit mehreren Funktionen</b></summary>

Sie können Ihrer vorhandenen Teams-App weitere Features hinzufügen, indem Sie Features hinzufügen. Wenn Sie beispielsweise der vorhandenen Registerkarten-App eine Bot-App hinzufügen, fügt das Teams-Toolkit den Bot-Ordner mit relevanten Dateien und Code hinzu.

Die folgende Abbildung zeigt die Verzeichnisstruktur der Registerkarten-App:

   :::image type="content" source="../assets/images/teams-toolkit-v2/tabapp-directory.png" alt-text="Verzeichnisstruktur der Registerkarten-App":::

Die folgende Abbildung zeigt die Verzeichnisstruktur der Registerkarten-App mit Bot-Feature:

   :::image type="content" source="../assets/images/teams-toolkit-v2/tab-app-with-bot-app.png" alt-text="Registerkarten-App mit Bot-App-Verzeichnisstruktur":::

</details>

## <a name="see-also"></a>Siehe auch

* [Erstellen einer Teams-App mit Blazor](../sbs-gs-blazorupdate.yml)
* [Erstellen einer Teams-App mit C# oder .NET](../sbs-gs-csharp.yml)
* [Voraussetzungen für alle Arten von Umgebungen und Erstellen Ihrer Teams-App](tools-prerequisites.md)
* [Vorbereiten des Erstellens von Apps mit dem Microsoft Teams-Toolkit](build-environments.md)
