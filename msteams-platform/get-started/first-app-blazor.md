---
title: Erste Schritte – Erstellen Ihrer ersten Teams-App mit Doppelklick
author: adrianhall
description: Erstellen Sie mithilfe von Microsoft Teams-Toolkit und React schnell eine Microsoft Teams-App, mithilfe des Microsoft Teams-Toolkits und von .NET Mofzor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: c336c97d477e7038cc41a5e593d71b0e98dc4643
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994392"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a>Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit Demerz

In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-App in .NET/Mofzor, die eine einfache persönliche App zum Abrufen von Informationen aus Microsoft Graph implementiert. (Eine *persönliche App* enthält eine Reihe von Registerkarten, die für die individuelle Verwendung vorgesehen sind.)  Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie eine App lokal ausführen und wie Sie die App in Azure bereitstellen.

In der erstellten App werden grundlegende Benutzerinformationen für den aktuellen Benutzer angezeigt.  Wenn die Berechtigung dazu erteilt wurde, stellt die App eine Verbindung mit Microsoft Graph als aktueller Benutzer her, um das vollständige Profil zu erhalten.

## <a name="before-you-begin"></a>Bevor Sie beginnen

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten](prerequisites.md) installieren.

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie **"Neues Projekt erstellen"** aus.

1. Wählen Sie **Microsoft Teams-App** aus, und drücken Sie dann **"Weiter".**  Verwenden Sie den Projekttyp Microsoft **Teams,** um Ihnen bei der Suche nach der Vorlage zu helfen.

1. Geben Sie dem Projekt und der Projektmappe einen guten Namen, und drücken Sie dann **"Weiter".**

1. Geben Sie den Anwendungsnamen und den Firmennamen ein, und drücken Sie dann die Schaltfläche **"Erstellen".**  Der Anwendungsname und der Firmenname werden Ihren Endbenutzern angezeigt.

1. Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.  Nachdem das Projekt erstellt wurde, richten Sie einmaliges Anmelden mit M365 ein:

   - Wählen Sie **Project**  >  **TeamsFx**  >  **Configure for SSO...** aus.
   - Melden Sie sich bei Ihrem M365-Administratorkonto an, wenn Sie dazu aufgefordert werden.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

1. Öffnen Sie ein Terminal, und wählen Sie das Verzeichnis aus, in dem Sie das Projekt erstellen möchten.

1. Ausführen, `dotnet new -i` um die Vorlage aus NuGet zu installieren:

   ``` bash
   dotnet new --install Microsoft.TeamsFx.VisualStudio.ProjectTemplates::0.1.43-beta
   ```

   Dies ist nur beim ersten Mal oder beim Aktualisieren der Vorlage erforderlich. Überprüfen Sie [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) auf die neueste Version dieses Pakets.

1. Erstellen eines Verzeichnisses:

   ``` bash
   mkdir helloworld
   ```

1. Ausführen, `dotnet new` um ein neues Projekt zu erstellen:

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. Nachdem Sie ein Gerüst erstellt haben, konfigurieren Sie das Projekt für die Teams-Bereitstellung:

   ``` bash
   teamsfx init
   ```

Sie können die Projektmappe jetzt in Visual Studio zum Debuggen öffnen.

---

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).

Nachdem das Microsoft Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Microsoft Teams. Die Im Projektmappen-Explorer-Bereich von Visual Studio 2019 angezeigten Projektverzeichnisse und Dateien.

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio 2019.":::

- Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.
- Das App-Manifest für die Veröffentlichung über das Entwicklerportal für Teams wird in `Properties/manifest.json` gespeichert.
- Zur Unterstützung der Authentifizierung wird ein Back-End-Controller `Controllers/BackendController.cs` bereitgestellt.

Da Sie während des Setups eine Registerkarten-App erstellt haben, erstellt das Teams-Toolkit das Gerüst für den gesamten erforderlichen Code für eine einfache Registerkarte als [Einenzockserver.](/aspnet/core/blazor)

- `Pages/Tab.razor` ist der Einstiegspunkt der Front-End-Anwendung.
- `TeamsFx.cs``JS/src/index.js`und wird für die Initialisierung der Kommunikation mit dem Teams-Host verwendet.

Sie können Back-End-Funktionen hinzufügen, indem Sie Ihrer Anwendung zusätzliche ASP.NET Core-Controller hinzufügen.

## <a name="run-your-app-locally"></a>Lokales Ausführen Ihrer App

Das Microsoft Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal auszuführen.  Dies besteht aus mehreren Teilen, die für die Bereitstellung der richtigen, von Microsoft Teams erwarteten Infrastruktur erforderlich sind:

- Es wird eine Anwendung bei Azure Active Directory registriert.  Diese Anwendung verfügt über Berechtigungen, die mit dem Speicherort, von dem die App geladen wird, und allen Back-End-Ressourcen verknüpft sind, auf die sie zugreift.
- Eine Web-API wird (über IIS Express) gehostet, um Authentifizierungsaufgaben zu unterstützen, die als Proxy zwischen der App und Azure Active Directory fungieren.  
- Es wird ein App-Manifest generiert und im Entwicklerportal für Microsoft Teams verfügbar gemacht.  Microsoft Teams verwendet das App-Manifest, um die verbundenen Clients darüber zu informieren, von wo die App geladen werden soll.

Sobald dies erfolgt ist, kann die App im Microsoft Teams-Client geladen werden.  Wir verwenden den Microsoft Teams-Webclient, um den HTML-, CSS- und JavaScript-Code in einer standardmäßigen Webentwicklungsumgebung anzuzeigen.

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.

1. Installieren Sie auf Anforderung das selbstsignierungsbasierte SSL-Zertifikat für das lokale Debuggen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. Teams wird in einem Webbrowser geladen, und Sie werden dazu aufgefordert, sich anzumelden. Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben. Melden Sie sich mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.

Ihre App wird nun angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Screenshot der fertiggestellten App":::

Sie können normale Debugaktivitäten wie bei jeder anderen Webanwendung ausführen (z. B. Haltepunkte festlegen). Die App unterstützt Hot Reloading.  Wenn Sie eine Datei innerhalb des Projekts ändern, wird die Seite neu geladen.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</summary>

Wenn Sie F5 gedrückt haben, hat das Microsoft Teams-Toolkit Folgendes getan:

1. Ihre Anwendung bei Azure Active Directory registriert.
1. Ihre Anwendung bei Microsoft Teams für das „Querladen“ registriert.
1. Das Anwendungs-Back-End wurde lokal ausgeführt.
1. Das lokal gehostete Anwendungs-Front-End gestartet
1. Microsoft Teams wurde in einem Webbrowser mit einem Befehl gestartet, um Teams anzuweisen, die Anwendung querzuladen (die URL ist im Anwendungsmanifest registriert).

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</summary>

Um Ihre App in Teams erfolgreich ausführen zu können, benötigen Sie ein Microsoft 365-Entwicklungskonto, das das Laden der App-Seite ermöglicht. Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).

</details>

## <a name="deploy-your-app-to-azure"></a>Bereitstellen Ihrer App in Azure

Die Bereitstellung besteht aus zwei Schritten.  Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.

> **Vorschau**
>
> Die Unterstützung für Mofzor-Apps ist neu im Teams-Toolkit.  Bereitstellung und Bereitstellung erfolgen mit einer Kombination aus Visual Studio 2019 und dem Entwicklerportal für Teams.

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a>Bereitstellen und Bereitstellen Ihrer App im Azure App Service

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie **"Veröffentlichen"** aus (oder verwenden Sie das Menüelement   >  **"Veröffentlichen** erstellen").

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Auswählen des Veröffentlichungsvorgangs für das Projekt":::

1. Wählen Sie im **Veröffentlichungsfenster** **Azure** aus.  Klicken Sie **auf "Weiter".**

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Auswählen von Azure als Veröffentlichungsziel":::

1. Wählen Sie **Azure App Service (Windows)** aus.  Klicken Sie **auf "Weiter".**

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Auswählen von Azure App Service als Veröffentlichungsziel":::

1. Wählen Sie **+** diese Option aus, um eine neue App Service-Instanz zu erstellen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Erstellen Sie eine neue Instanz.":::

1. Im Dialogfeld **"App-Dienst erstellen (Windows)** werden die Eintragsfelder **"Name",** **"Abonnementname",** **"Ressourcengruppe"** und **"Hostingplan"** ausgefüllt. Wenn Sie bereits einen App-Dienst ausgeführt haben, werden vorhandene Einstellungen ausgewählt.  Sie können eine neue Ressourcengruppe und einen Hostingplan erstellen (empfohlen).  Wenn Sie fertig sind, wählen Sie **Erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Auswählen von Hostingplan und Abonnement":::

1. Im Dialogfeld **"Veröffentlichen"** wurde die neu erstellte Instanz automatisch ausgewählt.  Wenn Sie fertig sind, wählen Sie **Fertig stellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Wählen Sie die neue Instanz aus.":::

1. Klicken Sie auf das Symbol **"Bearbeiten"** (Bleistift) neben dem **Bereitstellungsmodus,** und wählen Sie dann **"Eigenständig"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Wählen Sie den eigenständigen Bereitstellungsmodus aus.":::

1. Wählen Sie **Veröffentlichen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Veröffentlichen Ihrer App im App-Dienst":::

Visual Studio stellt die App in Ihrem Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen.  Fügen Sie `/tab` am Ende der URL hinzu, um Ihre Seite anzuzeigen.

Im Bereich **"Veröffentlichen"** der Projekteigenschaften werden die Website-URL und andere Details angezeigt. Notieren Sie sich die Website-URL.

## <a name="create-an-environment-for-your-app"></a>Erstellen einer Umgebung für Ihre App

Das Entwicklerportal für Teams verwaltet, wo die Registerkarten für Ihre App mit einer **Umgebung** geladen werden.  So erstellen Sie eine Umgebung:

1. Öffnen Sie das [Entwicklerportal für Teams](https://dev.teams.microsoft.com).  Melden Sie sich mit Ihrem M365-Administratorkonto an.

1. Wählen Sie in der Seitenleiste **Apps** aus.

1. Wenn Sie nur eine App haben, wird sie automatisch ausgewählt.  Wenn nicht, wählen Sie Ihre App aus der Liste aus.

1. Wählen Sie **Umgebungen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Auswählen von Umgebungen":::

1. Wählen Sie **Ihre erste Umgebung erstellen** aus.

1. Geben Sie einen Namen für Ihre Umgebung ein, und drücken Sie dann **"Hinzufügen".** z. _B. Production_.

1. Wenn die neu erstellte Umgebung ausgewählt ist, drücken **Sie Die erste Umgebungsvariable** erstellen.

1. Geben Sie `azure_app_url` den **Namen** ein.  Geben Sie Ihre Azure-Website-URL (ohne die `https://` ) als **Wert** ein.

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Erstellen einer Umgebungsvariablen":::

   Klicken **Sie auf "Hinzufügen".**

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Das App-Manifest lädt die Registerkarte von einer `localhost` URL.  In diesem Abschnitt passen Sie das App-Manifest so an, dass die Registerkarte von der URL geladen wird, die in der soeben erstellten Umgebung aufgeführt ist.

1. Wählen Sie in der Seitenleiste die Option **"Grundlegende Informationen"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Auswählen grundlegender Informationen":::

1. Es gibt mehrere Stellen innerhalb des Manifests, an denen ein Element als Teil einer URL aufgeführt `locahost:XXXXX` wird.  Ersetzen Sie alle Vorkommen `{{azure_app_url}}` durch (einschließlich der geschweiften Klammern).

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Anpassen der grundlegenden Informationen für die Umgebung":::

1. Wenn Sie fertig sind, klicken Sie auf **"Speichern".**

1. Wählen Sie in der Seitenleiste **"Funktionen"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Auswählen von Funktionen":::

1. Wählen Sie **"Persönliche Registerkarte" aus.**
1. Wählen Sie neben der **Registerkarte "Persönlich"** die drei Punkte aus, und wählen Sie dann **"Bearbeiten"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Bearbeiten persönlicher Registerkarteneinstellungen":::

1. Ersetzen Sie die URL durch die Umgebungsvariable in den Feldern **"Inhalts-URL"** und **"Website-URL".**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Bearbeiten von URLs für persönliche Registerkarten":::

1. Drücken Sie **Update**.

1. Klicken Sie auf **Speichern**.

1. Wählen Sie in der Seitenleiste **single Sign-On** aus.

1. Ersetzen Sie den `localhost` innerhalb des **Anwendungs-ID-URI** durch `{{azure_app_url}}` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Bearbeiten des Anwendungs-ID-URI für einmaliges Anmelden":::

1. Klicken Sie auf **Speichern**.

1. Drücken Sie in der Seitenleiste **Domänen**.

1. Drücken **Sie "Domäne hinzufügen".**

1. Wenn `{{azure_app_url}}` sie nicht als gültige Domäne aufgeführt ist, fügen Sie sie als gültige Domäne hinzu, und klicken Sie dann auf **"Hinzufügen".**

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Hinzufügen einer Domäne":::

Sie können jetzt die Schaltfläche **"Vorschau in Teams"** oben auf der Seite verwenden, um Ihre App in Teams zu starten.

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Teams-App mit React](first-app-react.md)
- [Erstellen einer Teams-App als SharePoint-Webpart](first-app-spfx.md)
- [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
- [Erstellen einer Messaging-Erweiterung](first-message-extension.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Teams-App als SharePoint-Webpart](first-app-spfx.md)
