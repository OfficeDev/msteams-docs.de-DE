---
title: Erste Schritte – Erstellen Ihrer ersten Teams app mit Blazor
author: adrianhall
description: Erstellen Sie schnell Microsoft Teams App, die ein "Hello, World!" anzeigt. mit dem Microsoft Teams Toolkit und .NET Blazor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: 6a9c7e008e2fb6d77c3314286b09d006bd468c37
ms.sourcegitcommit: 25c02757fe207cdff916ba63aa215f88e24e1d6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2021
ms.locfileid: "52667454"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a>Erstellen und Ausführen der ersten Microsoft Teams app mit Blazor

In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-App in .NET/Blazor, die eine einfache persönliche App implementiert, um Informationen aus dem Microsoft-Graph. (Eine *persönliche App* enthält eine Reihe von Registerkarten, die für die individuelle Verwendung festgelegt sind.)  Im Lernprogramm erfahren Sie mehr über die Struktur einer Teams-App, das lokale Ausführen einer App und die Bereitstellung der App in Azure.

Die app, die erstellt wird, zeigt grundlegende Benutzerinformationen für den aktuellen Benutzer an.  Wenn die Berechtigung erteilt wird, stellt die App eine Verbindung mit dem Microsoft Graph als aktueller Benutzer, um das vollständige Profil zu erhalten.

## <a name="before-you-begin"></a>Bevor Sie loslegen

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten installieren.](prerequisites.md)

> [!div class="nextstepaction"]
> [Installieren der erforderlichen Komponenten](prerequisites.md)

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie das Teams Toolkit, um Ihr erstes Projekt zu erstellen:

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

1. Öffnen Visual Studio 2019.

1. Wählen **Sie Neues Projekt erstellen aus.**

1. Wählen **Microsoft Teams App** aus, und drücken Sie dann **weiter**.  Um die Vorlage zu finden, verwenden Sie den Projekttyp **Microsoft Teams**.

1. Geben Sie dem Projekt und der Projektmappe einen guten Namen, und drücken Sie dann **weiter**.

1. Geben Sie den Anwendungsnamen und den Firmennamen an, und drücken Sie dann **erstellen**.  Der Anwendungsname und der Firmenname werden ihren Endbenutzern angezeigt.

1. Ihre Teams-App wird innerhalb weniger Sekunden erstellt.  Nachdem das Projekt erstellt wurde, richten Sie einmaliges Anmelden mit M365 ein:

   - Wählen **Project**  >  **TeamsFx**  >  **Configure for SSO...** aus.
   - Wenn Sie dazu aufgefordert werden, melden Sie sich bei Ihrem M365-Administratorkonto an.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

1. Öffnen Sie ein Terminal, und wählen Sie das Verzeichnis aus, in dem Sie das Projekt erstellen möchten.

1. Führen `dotnet new -i` Sie aus, um die Vorlage von NuGet:

   ``` bash
   dotnet new --install Microsoft.TeamsFx.VisualStudio.ProjectTemplates::0.1.43-beta
   ```

   Sie müssen dies nur beim ersten Mal oder beim Aktualisieren der Vorlage tun. Überprüfen [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) die neueste Version dieses Pakets.

1. Erstellen eines Verzeichnisses:

   ``` bash
   mkdir helloworld
   ```

1. Führen `dotnet new` Sie aus, um ein neues Projekt zu erstellen:

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. Konfigurieren Sie nach dem Gerüst das Projekt für Teams Bereitstellung:

   ``` bash
   teamsfx init
   ```

Sie können die Lösung nun in einem Visual Studio Debuggen öffnen.

---

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen.](#run-your-app-locally)

Sobald Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams. Die Projektverzeichnissen und -dateien werden im Bereich Projektmappen-Explorer von Visual Studio 2019 angezeigt.

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Screenshot mit App-Projektdateien für eine persönliche App in Visual Studio 2019.":::

- Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.
- Das App-Manifest für die Veröffentlichung über das Entwicklerportal für Teams wird in `Properties/manifest.json` gespeichert.
- Zur Unterstützung der Authentifizierung wird ein `Controllers/BackendController.cs` Back-End-Controller bereitgestellt.

Da Sie während des Setups eine Tab-App erstellt haben, erstellt das Teams Toolkit einen Gerüst für den erforderlichen Code für eine einfache Registerkarte als [Blazor Server](/aspnet/core/blazor).

- `Pages/Tab.razor` ist der Einstiegspunkt der Front-End-Anwendung.
- `TeamsFx.cs`und `JS/src/index.js` wird zum Initialisieren der Kommunikation mit dem Teams verwendet.

Sie können Back-End-Funktionen hinzufügen, indem Sie ASP.NET Core Ihrer Anwendung hinzufügen.

## <a name="run-your-app-locally"></a>Lokales Ausführen der App

Teams Mit toolkit können Sie Ihre App lokal ausführen.  Dies besteht aus mehreren Teilen, die erforderlich sind, um die richtige Infrastruktur zur Verfügung zu stellen, die Teams erwartet:

- Eine Anwendung wird mit Azure Active Directory.  Diese Anwendung verfügt über Berechtigungen, die dem Speicherort zugeordnet sind, von dem die App geladen wird, und allen Back-End-Ressourcen, auf die sie zu zugegriffen hat.
- Eine Web-API wird (über IIS Express) gehostet, um Authentifizierungsaufgaben zu unterstützen und als Proxy zwischen der App und Azure Active Directory.  
- Ein App-Manifest wird generiert und ist im Entwicklerportal für Teams.  Teams verwendet das App-Manifest, um verbundene Clients zu informieren, von wo aus die App geladen werden soll.

Sobald dies geschehen ist, kann die App innerhalb des Teams geladen werden.  Wir verwenden den Teams-Webclient, damit der HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung angezeigt wird.

So erstellen und führen Sie Ihre App lokal aus:

1. Drücken Visual Studio Code **F5,** um die Anwendung im Debugmodus ausführen zu können.

1. Installieren Sie auf Wunsch das selbst signierte SSL-Zertifikat für das lokale Debuggen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot, der zeigt, wie die Aufforderung zum Installieren eines SSL-Zertifikats angezeigt wird, Teams die Anwendung von localhost laden zu können.":::

1. Teams werden in einem Webbrowser geladen, und Sie werden zur Anmeldung aufgefordert. Wenn Sie aufgefordert werden, Microsoft Teams öffnen, wählen Sie Abbrechen aus, um im Browser zu verbleiben. Melden Sie sich mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App auf Teams, drücken Sie **hinzufügen**.

Ihre App wird nun angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Screenshot der abgeschlossenen App":::

Sie können normale Debugaktivitäten so tun, als wäre dies eine andere Webanwendung (z. B. festlegen von Haltepunkten). Die App unterstützt das Laden von Hot Reloads.  Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite erneut geladen.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</summary>

Wenn Sie F5 gedrückt haben, Teams Toolkit:

1. Registriert Ihre Anwendung bei Azure Active Directory.
1. Registriert Ihre Anwendung für das "Seitenladen" in Microsoft Teams.
1. Das Anwendungs-Back-End wurde lokal ausgeführt.
1. Das Front-End der Anwendung wurde lokal gestartet.
1. Die Microsoft Teams in einem Webbrowser mit einem Befehl gestartet, um Teams anweisen, die Anwendung seitlich zu laden (die URL wird im Anwendungsmanifest registriert).

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, wie Sie häufige Probleme beim lokalen Ausführen Ihrer App beheben.</summary>

Um Ihre App erfolgreich in Teams ausführen zu können, müssen Sie über ein Microsoft 365-Entwicklungskonto verfügen, das das appseitige Laden zulässt. Weitere Informationen zum Öffnen von Konten finden Sie unter [Voraussetzungen](prerequisites.md#enable-sideloading).

</details>

## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten.  Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.

> **Vorschau**
>
> Die Unterstützung für Blazor-Apps ist neu in Teams Toolkit.  Bereitstellung und Bereitstellung erfolgt mit einer Kombination aus Visual Studio 2019 und dem Entwicklerportal für Teams.

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a>Bereitstellen und Bereitstellen Ihrer App im Azure App Service

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen** aus (oder verwenden Sie das **Menüelement Veröffentlichen**  >   erstellen).

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Auswählen des Veröffentlichungsvorgangs für das Projekt":::

1. Wählen Sie **im Fenster** Veröffentlichen die Option **Azure aus.**  Drücken Sie **weiter**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Auswählen von Azure als Veröffentlichungsziel":::

1. Wählen **Sie Azure App Service (Windows) aus.**  Drücken Sie **weiter**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Auswählen von Azure App Service als Veröffentlichungsziel":::

1. Wählen **+** Sie diese Option aus, um eine neue App -Dienstinstanz zu erstellen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Erstellen Sie eine neue Instanz.":::

1. Im Dialogfeld **App-Dienst erstellen (Windows)** werden die Eingabefelder **Name,** **Abonnementname,** **Ressourcengruppe** und **Hostingplan** aufgefüllt. Wenn Sie bereits einen App-Dienst ausgeführt haben, werden vorhandene Einstellungen ausgewählt.  Sie können eine neue Ressourcengruppe und einen neuen Hostingplan erstellen (empfohlen).  Wenn Sie bereit sind, wählen Sie **Erstellen aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Auswählen von Hostingplan und Abonnement":::

1. Im Dialogfeld **Veröffentlichen** wurde die neu erstellte Instanz automatisch ausgewählt.  Wenn Sie bereit sind, wählen Sie **Fertig stellen aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Wählen Sie die neue Instanz aus.":::

1. Drücken Sie **das Symbol Bearbeiten** (Bleistift) neben Bereitstellungsmodus, und wählen Sie dann **Eigenständiges aus.** 

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Wählen Sie den eigenständigen Bereitstellungsmodus aus.":::

1. Wählen Sie **Veröffentlichen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Veröffentlichen Ihrer App im App-Dienst":::

Visual Studio stellt die App in Ihrem Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen.  Fügen `/tab` Sie am Ende der URL hinzu, um Ihre Seite zu sehen.

Der Bereich **"Projekteigenschaften veröffentlichen"** zeigt die Website-URL und andere Details an. Notieren Sie sich die Website-URL.

## <a name="create-an-environment-for-your-app"></a>Erstellen einer Umgebung für Ihre App

Das Entwicklerportal für Teams verwaltet, wo die Registerkarten für Ihre App mit einer Umgebung geladen **werden.**  So erstellen Sie eine Umgebung:

1. Öffnen Sie [das Entwicklerportal für Teams](https://dev.teams.microsoft.com).  Melden Sie sich mit Ihrem M365-Administratorkonto an.

1. Wählen Sie in der Seitenleiste **Apps aus.**

1. Wenn Sie nur über eine App verfügen, wird sie automatisch ausgewählt.  Wenn nicht, wählen Sie Ihre App aus der Liste aus.

1. Wählen Sie **Umgebungen aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Auswählen von Umgebungen":::

1. Wählen **Sie Erstellen Ihrer ersten Umgebung aus.**

1. Geben Sie einen Namen für Ihre Umgebung ein, und drücken Sie dann **hinzufügen**; z. B. _Production_.

1. Drücken Sie bei Auswahl der neu erstellten Umgebung die **Erste Umgebungsvariable erstellen.**

1. Geben `azure_app_url` Sie für den Namen **ein.**  Geben Sie Ihre Azure-Website-URL (ohne `https://` ) als **Wert ein.**

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Erstellen einer Umgebungsvariablen":::

   Drücken Sie **Hinzufügen**.

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Das App-Manifest lädt die Registerkarte über eine `localhost` URL.  In diesem Abschnitt passen Sie das App-Manifest an, um die Registerkarte aus der URL zu laden, die in der Umgebung aufgeführt ist, die Sie gerade erstellt haben.

1. Wählen Sie auf der Seitenleiste **Grundlegende Informationen aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Auswählen grundlegender Informationen":::

1. Es gibt mehrere Orte im Manifest, die eine `locahost:XXXXX` als Teil einer URL auflisten.  Ersetzen Sie alle Vorkommen durch `{{azure_app_url}}` (einschließlich der geschweiften Klammern).

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Anpassen grundlegender Informationen für die Umgebung":::

1. Drücken Sie nach Abschluss des Vorgangs **speichern**.

1. Wählen Sie auf der Seitenleiste Funktionen **aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Auswählen von Funktionen":::

1. Wählen **Sie Persönliche Registerkarte aus.**
1. Wählen Sie neben **der Registerkarte Personal** die dreifachen Punkte aus, und wählen Sie dann Bearbeiten **aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Bearbeiten persönlicher Registerkarteneinstellungen":::

1. Ersetzen Sie die URL durch die Umgebungsvariable in den Feldern **Inhalts-URL** und **Website-URL.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Bearbeiten von URLs für persönliche Registerkarten":::

1. Drücken **Sie Update**.

1. Klicken Sie auf **Speichern**.

1. Wählen Sie auf der Seitenleiste **einmaliges Anmelden aus.**

1. Ersetzen Sie `localhost` den innerhalb des **Anwendungs-ID-URI** durch `{{azure_app_url}}` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Bearbeiten des Anwendungs-ID-URI für einmaliges Anmelden":::

1. Klicken Sie auf **Speichern**.

1. Drücken Sie an der Seitenleiste **domänen**.

1. Drücken **Sie die Taste Domäne hinzufügen.**

1. Wenn sie nicht als gültige Domäne aufgeführt ist, fügen Sie sie als gültige Domäne hinzu, und drücken `{{azure_app_url}}` Sie dann die Taste **Hinzufügen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Hinzufügen einer Domäne":::

Sie können nun die Schaltfläche **Vorschau im Teams** oben auf der Seite verwenden, um Ihre App innerhalb eines Teams.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über andere Methoden zum Erstellen Teams Apps:

- [Erstellen einer Teams App mit React](first-app-react.md)
- [Erstellen einer Teams-App](first-app-spfx.md) als SharePoint Web part (Azure nicht erforderlich)
- [Erstellen einer Unterhaltungsbot-App](first-app-bot.md)
- [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
