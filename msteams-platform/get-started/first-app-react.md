---
title: Erste Schritte – Erstellen Ihrer ersten Microsoft Teams-App mit React
author: adrianhall
description: Erstellen Sie mithilfe von Microsoft Teams-Toolkit und React schnell eine Microsoft Teams-App, die die Meldung "Hallo, Welt!" anzeigt.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: 8c6a957dc01cfaac0f8463166a6647d6b18babed
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721836"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a>Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit React

In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-Anwendung in React, die eine einfache persönliche App implementiert, um Informationen aus Microsoft Graph abzurufen. (Eine *persönliche App* enthält eine Reihe von Registerkarten für die individuelle Verwendung.) Im Rahmen des Lernprogramms erfahren Sie Näheres zur Struktur einer Microsoft Teams-App, das lokale Ausführen einer App und die Bereitstellung der App in Azure.

In der erstellten App werden grundlegende Benutzerinformationen für den aktuellen Benutzer angezeigt.  Wenn die Berechtigung dazu erteilt wurde, stellt die App eine Verbindung mit Microsoft Graph als aktueller Benutzer her, um das vollständige Profil zu erhalten.

## <a name="before-you-begin"></a>Bevor Sie beginnen

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten](prerequisites.md) installieren.

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Klicken Sie auf **Neues Projekt erstellen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. Im Schritt **Funktionen auswählen** ist die Funktion **Registerkarten** bereits ausgewählt.  Drücken Sie **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. Wählen Sie im Schritt **Frontend-Hostingtyp** die Option **Azure** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. Drücken Sie im Schritt **Cloudressourcen** auf **OK**.  Für dieses Lernprogramm werden keine zusätzlichen Cloudressourcen benötigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Screenshot, der zeigt, wie Cloudressourcen für Ihre neue App hinzugefügt werden.":::

1. Wählen Sie im Schritt **Programmiersprache** die Option **JavaScript** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie einen Arbeitsbereichsordner aus.  Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.  Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.

``` bash
teamsfx new
```

Die CLI führt durch einige Fragen zum Erstellen des Projekts.  Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).  Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.
1. Wählen Sie die Funktion **Registerkarte** aus.
1. Wählen Sie **Azure**-Frontend-Hosting aus.
1. Wählen Sie keine Cloudressourcen aus.
1. Wählen Sie **JavaScript** als Programmiersprache aus.
1. Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.
1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.

Sobald alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.

---

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).

Nachdem das Microsoft Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Microsoft Teams. Die Projektverzeichnisse und -dateien werden im Explorer-Bereich von Visual Studio Code angezeigt.

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio Code":::

Das Toolkit erstellt im Projektverzeichnis automatisch Ordner basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben. Das Microsoft Teams Toolkit behält seinen Status für Ihre App im `.fx`-Verzeichnis bei.  Weitere Elemente in diesem Verzeichnis:

- Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.
- Das App-Manifest für die Veröffentlichung im Entwicklerportal für Microsoft Teams wird in `manifest.source.json` gespeichert.
- Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `settings.json` gespeichert.

Da Sie während des Setups die Registerkartenfunktion ausgewählt haben, erstellt das Microsoft Teams-Toolkit den erforderlichen Code für eine einfache Registerkarte im `tabs`-Verzeichnis. In diesem Verzeichnis befinden sich mehrere wichtige Dateien:

- `tabs/src/index.jsx` ist der Einstiegspunkt der Front-End-App, an dem die `App`-Hauptkomponente mit `ReactDOM.render()` gerendert wird.
- `tabs/src/components/App.jsx` übernimmt das URL-Routing in Ihrer App. Es ruft das [Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) auf, um die Kommunikation zwischen Ihrer App und Microsoft Teams herzustellen.
- `tabs/src/components/Tab.jsx` enthält den Code zum Implementieren der Benutzeroberfläche Ihrer App.
- `tabs/src/components/TabConfig.jsx` enthält den Code zum Implementieren der Benutzeroberfläche, die Ihre App konfiguriert.

Für die Microsoft Teams-Laufzeit sind mehrere Registerkarten erforderlich, darunter für Datenschutzhinweis, Nutzungsbedingungen und Konfiguration.  Der Code für den Datenschutzhinweis und die Nutzungsbedingungen befindet sich in demselben Verzeichnis.

Wenn Sie Cloudfunktionen hinzufügen, werden dem Projekt zusätzliche Verzeichnisse hinzugefügt.  Besonders wichtig: Das `api`-Verzeichnis enthält den Code für alle von Ihnen geschriebenen Azure-Funktionen.

## <a name="run-your-app-locally"></a>Lokales Ausführen Ihrer App

Das Microsoft Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal auszuführen.  Dies besteht aus mehreren Teilen, die für die Bereitstellung der richtigen, von Microsoft Teams erwarteten Infrastruktur erforderlich sind:

- Es wird eine Anwendung bei Azure Active Directory registriert.  Diese Anwendung verfügt über Berechtigungen, die mit dem Speicherort, von dem die App geladen wird, und allen Back-End-Ressourcen verknüpft sind, auf die sie zugreift.
- Es wird eine Web-API zur Unterstützung von Authentifizierungsaufgaben gehostet, die als Proxy zwischen der App und Azure Active Directory agiert.  Dies wird über die Azure Functions Core Tools ausgeführt.  Der Zugriff darauf ist über die URL-Adresse `https://localhost:5000` möglich.
- Die HTML-, CSS- und JavaScript-Ressourcen, aus denen das Front-End der App besteht, werden in einem lokalen Dienst gehostet. Der Zugriff darauf ist über `https://localhost:3000` möglich.
- Es wird ein App-Manifest generiert und im Entwicklerportal für Microsoft Teams verfügbar gemacht.  Microsoft Teams verwendet das App-Manifest, um die verbundenen Clients darüber zu informieren, von wo die App geladen werden soll.

Sobald dies erfolgt ist, kann die App im Microsoft Teams-Client geladen werden.  Wir verwenden den Microsoft Teams-Webclient, um den HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung anzuzeigen.

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a>Erstellen und lokales Ausführen der App in Visual Studio Code

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.

   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.  Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.  Dies kann 3 bis 5 Minuten dauern.

   Sie werden vom Toolkit aufgefordert, bei Bedarf ein lokales Zertifikat zu installieren. Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden. Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. Ihr Webbrowser startet mit der Ausführung der App. Wenn Sie aufgefordert werden, Teams desktop zu öffnen, wählen **Sie Abbrechen** aus, um im Browser zu verbleiben. Sie werden möglicherweise auch aufgefordert, zu anderen Teams zu wechseln. wählen Sie Teams Web-App aus, wenn dies geschieht.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. Möglicherweise werden Sie aufgefordert, sich anzumelden.  Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.

Ihre App wird nun angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Screenshot der fertiggestellten App":::

Sie können normale Debugaktivitäten wie bei jeder anderen Webanwendung ausführen (z. B. Haltepunkte festlegen). Die App unterstützt Hot Reloading.  Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite neu geladen.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</summary>

Wenn Sie F5 gedrückt haben, hat das Microsoft Teams-Toolkit Folgendes getan:

1. Ihre Anwendung bei Azure Active Directory registriert
1. Ihre Anwendung in Microsoft Teams *quergeladen*
1. Ihr Anwendungs-Back-End mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start) lokal gestartet
1. Das lokal gehostete Anwendungs-Front-End gestartet
1. Microsoft Teams in einem Webbrowser mit der Anweisung gestartet, die App von `https://localhost:3000/tab` (die im Anwendungsmanifest registrierte URL) querzuladen.

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</summary>

Um Ihre App in Microsoft Teams erfolgreich auszuführen, müssen Sie über ein Microsoft Teams-Konto verfügen, das das Querladen von Apps zulässt. Weitere Informationen zum Öffnen eines Kontos finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</summary>

Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:

1. Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.
1. Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.

Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure.

1. Das Back-End (sofern konfiguriert) nutzt eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Storage.
1. Die Front-End-Anwendung wird in einem Azure Storage-Konto bereitgestellt, das für statisches Webhosting konfiguriert ist.

</details>

## <a name="next-steps"></a>Nächste Schritte

Informationen zu anderen Methoden zum Erstellen von Microsoft Teams-Apps finden Sie unter:

- [Erstellen einer Microsoft Teams-App mit Blazor](first-app-blazor.md)
- [Erstellen einer Microsoft Teams-App als SharePoint-Webpart](first-app-spfx.md) (Azure nicht erforderlich)
- [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
- [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
