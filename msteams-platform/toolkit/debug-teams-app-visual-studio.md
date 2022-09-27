---
author: surbhigupta
title: Debuggen Ihrer Teams-App für Visual Studio
description: In diesem Modul erfahren Sie, wie Sie Ihre Teams-App lokal in Visual Studio mithilfe des Teams-Toolkits debuggen.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
ms.openlocfilehash: cff0b3e18f63bc7943a7fc16875294f41257a37c
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027446"
---
# <a name="debug-your-teams-app-locally-using-visual-studio"></a>Lokales Debuggen Ihrer Teams-App mit Visual Studio

Mit dem Teams-Toolkit können Sie Ihre Microsoft Teams-App lokal debuggen und eine Vorschau anzeigen. Debuggen ist ein Prozess zum Erstellen, Überprüfen, Erkennen und Beheben von Problemen oder Fehlern in Ihrer App. Debuggen stellt sicher, dass das Programm erfolgreich ausgeführt wird. Visual Studio ermöglicht ihnen das Debuggen von Registerkarten, Bots und Nachrichtenerweiterungen. Das Teams-Toolkit unterstützt die folgenden Debugfeatures:

* Vorbereiten von Teams-App-Abhängigkeiten
* Debugging starten
* Umschalthaltepunkte
* Hot Reload
* Debuggen beenden

Während des Debugprozesses startet das Teams-Toolkit automatisch App-Dienste, initiiert das Debuggen und lädt die Teams-App quer. Nach dem Debuggen können Sie eine Vorschau der Teams-App im Teams-Webclient anzeigen. Sie können auch Debugeinstellungen anpassen, um Ihre Bot-Endpunkte oder Umgebungsvariablen zum Laden Ihrer konfigurierten App zu verwenden.

## <a name="prerequisites"></a>Voraussetzungen

| &nbsp; | Installieren | Zum Benutzen... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022, Version 17.3 | Sie können die Enterprise-Edition von Visual Studio und die "ASP.NET" Workload und Microsoft Teams-Entwicklungstools installieren. |
| &nbsp; | Teams Toolkit | Eine Visual Studio-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie die neueste Version. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort. |
| &nbsp; | [Vorbereiten Ihres Microsoft 365-Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md) | Zugriff auf das Teams-Konto mit den entsprechenden Berechtigungen zum Installieren einer App. |
| &nbsp; | [Microsoft 365-Entwicklerkonto](/../concepts/build-and-test/prepare-your-o365-tenant) | Zugriff auf das Teams-Konto mit den entsprechenden Berechtigungen zum Installieren einer App. |
| &nbsp; | Azure-Tools und [Microsoft Azure CLI](/cli/azure/install-azure-cli) | Azure-Tools für den Zugriff auf gespeicherte Daten oder die Bereitstellung eines cloudbasierten Back-End für Ihre Teams-App in Azure. |
|&nbsp;  | **Optional** | &nbsp; |
|&nbsp; |[Ngrok](https://ngrok.com/) | Ngrok wird verwendet, um externe Nachrichten von Azure Bot Framework an Ihren lokalen Computer weiterzuleiten.|

## <a name="debug-your-app-locally"></a>Lokales Debuggen Ihrer App

Sie können Ihre App lokal in Visual Studio mithilfe des Teams-Toolkits debuggen, indem Sie Folgendes ausführen:

### <a name="set-up-ngrok-only-for-bot-and-message-extension-app"></a>Einrichten von ngrok (nur für Bot- und Nachrichtenerweiterungs-App)

Verwenden Sie eine Eingabeaufforderung, um diesen Befehl auszuführen:

```
ngrok http 5130
```

### <a name="set-up-your-teams-toolkit"></a>Einrichten des Teams-Toolkits

Führen Sie die folgenden Schritte mithilfe des Teams-Toolkits aus, um Ihre App nach dem Erstellen eines Projekts zu debuggen:

1. Klicken Sie mit der rechten Maustaste auf Ihr **Projekt**.
1. Wählen Sie **das Teams-Toolkit** aus.
1. Wählen Sie **"Teams-App-Abhängigkeiten vorbereiten" aus**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png" alt-text="Abhängigkeiten von Teams-Apps für das lokale Debuggen":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname "MyTeamsApp1"

   Ihr Microsoft 365-Konto muss über die Berechtigung zum Querladen verfügen, bevor Sie sich anmelden.  Stellen Sie sicher, dass Ihre Teams-App in den Mandanten hochgeladen werden kann, andernfalls kann Ihre Teams-App im Teams-Client nicht ausgeführt werden.

1. Melden Sie sich bei Ihrem **Microsoft 365-Konto an**.
1. Wählen Sie ":::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-signin-m365.png" alt-text="Anmelden bei Microsoft 365-Konto"::: **fortsetzen**
   " aus.

   > [!Note]
   > Weitere Informationen zum Querladen von Berechtigungen finden Sie unter <https://aka.ms/teamsfx-sideloading-option>.

1. Wählen Sie **"Debuggen**" aus.
1. Wählen Sie **"Debuggen starten**" oder direkt **F5** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Startdebug.png" alt-text="Debuggen starten":::

   Visual Studio startet die Teams-App innerhalb des Microsoft Teams-Clients in Ihrem Browser.

   > [!Note]
   > Weitere Informationen finden Sie unter <https://aka.ms/teamsfx-vs-debug>.

1. Nachdem Microsoft Teams geladen wurde, wählen Sie **"Hinzufügen"** aus, um Ihre App in Teams zu installieren.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-add-loadapp.png" alt-text="Wählen Sie &quot;App hinzufügen&quot; aus, um die App zu laden.":::

   > [!TIP]
   > Sie können die Hot Reload-Funktion von Visual Studio auch während des Debuggens verwenden. Weitere Informationen finden Sie unter <https://aka.ms/teamsfx-vs-hotreload>.

   > [!NOTE]
   > Stellen Sie sicher, dass Sie beim Debuggen der Benachrichtigungs-Bot-App eine HTTP-Anforderung an "<http://localhost:5130/api/notification>" posten, um eine Benachrichtigung auszulösen. Wenn Sie beim Erstellen des Projekts den HTTP-Trigger ausgewählt haben, können Sie alle API-Tools wie curl (Windows-Eingabeaufforderung), Postman usw. verwenden.

   > [!TIP]
   > Wenn Sie Änderungen an der Teams-App-Manifestdatei (/templates/appPackage/manifest.template.json) vornehmen, stellen Sie sicher, dass Sie den Befehl "Teams-App-Abhängigkeiten vorbereiten" ausführen. Bevor Sie versuchen, die Teams-App erneut lokal auszuführen.

## <a name="key-features-of-teams-toolkit"></a>Wichtige Features des Teams-Toolkits

Sie können die folgenden wichtigen Features des Teams-Toolkits sehen, die den lokalen Debugprozess Ihrer Teams-App automatisieren:

### <a name="prepare-teams-app-dependencies"></a>Vorbereiten von Teams-App-Abhängigkeiten

Das Teams-Toolkit bereitet lokale Debugabhängigkeiten vor und registriert Ihre Teams-App im Mandanten in Ihrem Konto. Für Bot- und Nachrichtenerweiterungs-Apps registriert und konfiguriert das Teams-Toolkit den Bot.

### <a name="start-debugging"></a>Debugging starten

Sie können das Debuggen mit einem einzigen Vorgang ausführen und **F5** drücken, um das Debuggen zu starten. Das Teams-Toolkit erstellt Code, startet Dienste und startet die App in Ihrem Browser.

### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Sie können Haltepunkte in den Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure-Funktionen umschalten. Die Haltepunkte werden ausgeführt, wenn Sie mit der Teams-App in Ihrem Webbrowser interagieren.
Die folgende Abbildung zeigt die Umschalthaltepunkte:

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-toggle-breakpoint.png" alt-text="Lokale Debug-Umschaltfläche":::

### <a name="hot-reload"></a>Hot Reload

Wählen Sie **Hot Reload** aus, um Ihre Änderungen in Ihrer Teams-App anzuwenden, wenn Sie die Quellcodes während des Debuggens gleichzeitig aktualisieren und speichern möchten.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload.png" alt-text="Symbol &quot;Hot Reload&quot; auswählen":::

Wählen Sie in der Dropdownliste die Option **Hot Reload dateispeichern** aus, um das automatische Hot Reload zu aktivieren.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload-filesave.png" alt-text="Beim Speichern der Datei &quot;Hot Reload&quot; auswählen":::
  
   > [!Tip]
   > Weitere Informationen zu Hot Reload Funktion von Visual Studio während des Debuggens finden <https://aka.ms/teamsfx-vs-hotreload>Sie unter .

### <a name="stop-debugging"></a>Debuggen beenden

Wählen Sie **"Debuggen beenden** " aus, wenn das lokale Debuggen abgeschlossen ist.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Stopdebug.png" alt-text="Symbol &quot;Debug beenden&quot; auswählen":::

## <a name="customize-debug-settings"></a>Anpassen von Debugeinstellungen

Sie können die Debugeinstellung für Ihre Teams-App anpassen, um Ihre Bot-Endpunkte zu verwenden und Umgebungsvariablen hinzuzufügen:

### <a name="use-your-bot-endpoint"></a>Verwenden Ihres Bot-Endpunkts

Sie können die siteEndpoint-Konfiguration in **.fx/configs/config.local.json** auf Ihren Endpunkt festlegen.

```
"bot": {
    "siteEndpoint": "https://baidu.com"
}
```

### <a name="add-environment-variables"></a>Umgebungsvariablen hinzufügen

Sie können **"environmentVariables** " zur Datei **"launchSettings.json** " hinzufügen.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-environment-variables.png" alt-text="Hinzufügen benutzerdefinierter Umgebungsvariablen":::

### <a name="launch-teams-app-as-a-web-app"></a>Starten der Teams-App als Web-App

Sie können die Teams-App als Web-App starten, anstatt sie im Teams-Client auszuführen.

1. Wählen Sie **eigenschaften** > **launchSettings.json** in Projektmappen-Explorer Panel unter Ihrem Projekt aus.
1. Entfernen Sie " **launchUrl"** aus der Datei.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-launch-teamsapp-webapp.png" alt-text="Starten von Teams als Web-App durch Entfernen von launchurl":::

1. Klicken Sie mit der rechten Maustaste auf **"Lösung"**.
1. Wählen Sie **Eigenschaften** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-solution-properties.png" alt-text="Klicken Sie mit der rechten Maustaste auf die Lösung, und wählen Sie Eigenschaften aus.":::

1. Wählen Sie im Dialog **"Konfigurationseigenschaftenkonfiguration** > " aus.
1. Deaktivieren Sie das Kontrollkästchen "Prozess **bereitstellen** ".
1. Wählen Sie **OK** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-disable-deploy.png" alt-text="Deaktivieren der Bereitstellung in Konfigurationseigenschaften ":::

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
* [Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
