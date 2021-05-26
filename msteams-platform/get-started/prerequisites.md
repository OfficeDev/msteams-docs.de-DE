---
title: Erste Schritte – Voraussetzungen
author: adrianhall
description: Erfahren Sie, wie Sie mit der Entwicklung Microsoft Teams App beginnen und Ihre Umgebung einrichten.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.openlocfilehash: 73d99f2bbbc69bf13242110a56e13e662655283c
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646771"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a>Voraussetzungen: Erste Schritte mit Microsoft Teams App-Entwicklung

Bevor Sie Ihre erste Teams erstellen, müssen Sie einige Tools installieren und Ihre Entwicklungsumgebung einrichten.

## <a name="install-required-tools"></a>Installieren erforderlicher Tools

Einige der benötigten Tools hängen davon ab, wie Sie Ihre App Teams möchten:

- [Node.js](https://nodejs.org/en/download/) (verwenden Sie die neueste Version von v14 LTS) 
- Ein Browser mit Entwicklertools – [z. B. Microsoft Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/)
- Wenn Sie mit JavaScript, TypeScript oder dem SharePoint-Framework (SPFx) entwickeln, installieren Sie [Visual Studio Code](https://code.visualstudio.com/download), Version 1.55 oder höher.  
- Wenn Sie mit .NET entwickeln, installieren Sie [Visual Studio 2019](https://visualstudio.com/download).  Stellen Sie sicher, **dass ASP.NET und Webentwicklung** oder **.NET Core plattformübergreifende Entwicklungsarbeitsauslastung installieren.**

> [!WARNING]
> Es gibt bekannte Probleme mit `npm@7` , verpackt mit Knoten v15 und höher. Wenn Probleme beim Ausführen auftreten, stellen Sie sicher, dass Sie `npm install` Knoten v14 (LTS) verwenden.

## <a name="install-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Teams Toolkit vereinfacht den Entwicklungsprozess mit Tools zum Bereitstellen und Bereitstellen von Cloudressourcen für Ihre App, zum Veröffentlichen im Teams Store und mehr. Sie können das Toolkit mit Visual Studio Code, Visual Studio oder als CLI `teamsfx` (genannt) verwenden.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie die Ansicht Erweiterungen (**STRG+Umschalt+X**  /  **.⇧-X** oder **Ansicht > Erweiterungen ).**
1. Geben Sie im Suchfeld Teams _Toolkit ein._
1. Wählen Sie auf der grünen Installationsschaltfläche neben dem Teams Toolkit aus.

Sie finden auch das Teams Toolkit im [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

Die folgenden Tools werden von der erweiterung Visual Studio Code installiert, wenn sie benötigt werden.  Wenn sie bereits installiert ist, wird stattdessen die installierte Version verwendet.  Wenn Sie Linux (einschließlich WSL) verwenden, müssen Sie diese Tools vor der Verwendung installieren:

- [Azure Functions Core Tools](/azure/azure-functions/functions-run-local)

    Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debug ausgeführt, einschließlich der Authentifizierungshilfen, die beim Ausführen Ihrer Dienste in Azure erforderlich sind.  Es wird im Projektverzeichnis installiert (mit npm `devDependencies` ).

- [.NET SDK](/dotnet/core/install/)

    Das .NET SDK wird verwendet, um angepasste Bindungen für lokale Debugging- und Azure Functions-App-Bereitstellungen zu installieren.  Wenn Sie das .NET 3.1 (oder höher) SDK nicht global installiert haben, wird die portable Version installiert.

- [ngrok](https://ngrok.com/download)

    Einige Teams (Unterhaltungsbots, Messagingerweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen.  Sie müssen Ihr Entwicklungssystem für die Teams Tunnel verfügbar machen.  Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich.  Dieses Paket wird im Projektverzeichnis installiert (mithilfe von npm `devDependencies` ).

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Sie können Visual Studio 2019 verwenden, um Teams mit Blazor Server in .NET zu entwickeln.  Wenn Sie nicht beabsichtigen, Teams in .NET zu entwickeln, installieren Sie die Visual Studio Code version von Teams Toolkit.

So installieren Sie Teams Toolkit-Erweiterung:

1. Öffnen Visual Studio 2019.
1. Wählen **Sie Erweiterungen** Erweiterungen verwalten  >  **aus.**
1. Geben Sie im Suchfeld Teams _Toolkit ein._
1. Wählen Sie die Teams Toolkiterweiterung aus, und wählen Sie **Herunterladen aus.**

Die Erweiterung wird heruntergeladen.  Schließen Visual Studio 2019, um die Erweiterung zu installieren.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie den Paket-Manager, um die TeamsFx CLI `npm` zu installieren:

``` bash
npm install -g @microsoft/teamsfx-cli
```

Je nach Konfiguration müssen Sie möglicherweise verwenden, um `sudo` die CLI zu installieren:

``` bash
sudo npm install -g --unsafe-perm @microsoft/teamsfx-cli
```

Dies ist auf Linux- und macOS-Systemen häufiger.

Stellen Sie sicher, dass Sie den globalen npm-Cache zu Path hinzufügen.  Dies geschieht normalerweise im Rahmen des Node.js Installationsprogramms.  

Sie können die CLI mit dem Befehl `teamsfx` verwenden.  Stellen Sie sicher, dass der Befehl funktioniert, indem Sie `teamsfx -h` ausführen.

> [!CAUTION]
> Bevor Sie TeamsFx in PowerShell-Terminalen ausführen können, müssen Sie die Ausführungsrichtlinie "Remote signiert" für PowerShell aktivieren.  Weitere Informationen finden Sie in der [PowerShell-Dokumentation](/powershell/module/microsoft.powershell.core/about/about_signing).

---

## <a name="install-optional-tools"></a>Installieren optionaler Tools

Installieren Sie Browsertools für die App-Entwicklung. Wenn Ihre App z. B. mit React geschrieben wird, können Sie React Verwenden:

- [React Entwicklertools für Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

Wenn Sie auf in Azure gespeicherte Daten zugreifen oder ein cloudbasiertes Back-End für Ihre Teams in Azure bereitstellen möchten, installieren Sie die folgenden Tools:

- [Azure Tools for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [Azure CLI](/cli/azure/install-azure-cli)

Wenn Sie mit Microsoft Graph arbeiten, sollten Sie mehr über den Microsoft Graph explorer erfahren und ein Lesezeichen setzen. Mit diesem browserbasierten Tool können Sie Microsoft Graph außerhalb einer App abfragen.

- [Microsoft Graph-Tester](https://developer.microsoft.com/graph/graph-explorer)

Mit dem Entwicklerportal für Teams können Sie Ihre Teams-App konfigurieren, verwalten und verteilen (einschließlich an Ihre Organisation oder den Teams Store).

- [Entwicklerportal für Teams](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a>Aktivieren des Querladens

Während der Entwicklung müssen Sie Ihre App innerhalb von Teams laden, ohne sie zu verteilen.  Dies wird als "Querladen" bezeichnet.

1. Wenn Sie über ein Teams verfügen, überprüfen Sie, ob Sie Apps in einem Teams:

    1. Wählen Sie im Teams Die Option **Apps aus.**
    1. Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Abbildung, in der Teams sie eine benutzerdefinierte App hochladen können.":::

> [!NOTE]
> Wenn Sie Apps weiterhin nicht querladen können, wenden Sie sich an Ihren Teams Administrator. Weitere Informationen finden Sie unter Aktivieren Teams benutzerdefinierter Apps und [Aktivieren des Hochladens benutzerdefinierter](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Apps.

## <a name="get-a-free-teams-developer-tenant-optional"></a>Get a free Teams developer tenant (optional)

Wenn die Querladenoption nicht angezeigt wird oder Sie nicht über ein Teams-Konto verfügen, können Sie ein kostenloses Teams-Entwicklerkonto erhalten, indem Sie am M365-Entwicklerprogramm teilnehmen.  Der Registrierungsprozess dauert ca. zwei Minuten.

1. Wechseln Sie zum [Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
1. Wählen **Sie Jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wenn Sie zum Willkommensbildschirm kommen, wählen Sie **E5-Abonnement einrichten aus.**
1. Richten Sie Ihr Administratorkonto ein. Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was Sie nach der Anmeldung für das Microsoft 365 sehen.":::

1. Melden Sie sich mit Teams Administratorkonto an, das Sie gerade eingerichtet haben.
1. Überprüfen Sie, ob Sie **jetzt über Hochladen benutzerdefinierte App-Option** verfügen.

## <a name="get-a-free-azure-account"></a>Kostenloses Azure-Konto erhalten

Wenn Sie Ihre App hosten oder auf Ressourcen in Azure zugreifen möchten, benötigen Sie ein Azure-Abonnement.  Sie können [ein kostenloses Konto erstellen,](https://azure.microsoft.com/free/) bevor Sie beginnen.

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a>Melden Sie sich bei Ihren Microsoft 365- und Azure-Konten an

Sie benötigen Zugriff auf zwei Konten:

- Ihre Microsoft 365 Kontoanmeldeinformationen. Dies ist das Konto, das Sie zum Anmelden bei Teams. Wenn Sie einen mandanten Microsoft 365 verwenden, ist dies das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.
- - Ihre Azure-Anmeldeinformationen. Dies ist das Konto, das Sie für den Zugriff auf das Azure-Portal und für die Bereitstellung neuer Cloudressourcen zur Unterstützung Ihrer App verwenden.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Visual Studio Code
1. Wählen Sie Teams Symbol in der Seitenleiste aus:

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Teams Symbol in der Visual Studio Code Seitenleiste.":::

1. Wählen **Sie Anmelden bei M365 aus.**

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Speicherort des Abschnitts Konten, der für die Anmeldung verwendet wird.":::

1. Der Anmeldevorgang beginnt mit dem normalen Webbrowser.  Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab.  Sie werden aufgefordert, den Browser zu schließen und zu Visual Studio Code.
1. Kehren Sie zum Teams Toolkit innerhalb Visual Studio Code.
1. Wählen **Sie Anmelden bei Azure aus.**

    > [!TIP]
    > Wenn Sie die Azure Account-Erweiterung installiert haben und dasselbe Konto verwenden, können Sie diesen Schritt überspringen.  Sie verwenden automatisch dasselbe Konto wie in anderen Erweiterungen.

1. Der Anmeldevorgang beginnt mit dem normalen Webbrowser.  Führen Sie den Anmeldevorgang für Ihr Azure-Konto aus.  Sie werden aufgefordert, den Browser zu schließen und zu Visual Studio Code.

Nach Abschluss des Vorgangs zeigt der Abschnitt **ACCOUNTS** der Seitenleiste die beiden Konten zusammen mit der Anzahl der verwendbaren Azure-Abonnements an, die Ihnen zur Verfügung stehen.  Stellen Sie sicher, dass mindestens ein verwendbares Azure-Abonnement verfügbar ist.  Wenn nicht, melden Sie sich ab, und verwenden Sie ein anderes Konto.

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Visual Studio 2019 werden Sie aufgefordert, sich bei jedem Dienst bei Bedarf zu melden.  Sie müssen sich nicht vorab bei Ihren M365- und Azure-Konten anmelden.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

1. Melden Sie sich bei Microsoft 365 mit der TeamsFx CLI an:

    ``` bash
    teamsfx account login m365
    ```

    Der Anmeldevorgang beginnt mit dem normalen Webbrowser.  Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab.  Sie werden aufgefordert, den Browser zu schließen.

2. Melden Sie sich mit der TeamsFx CLI bei Azure an:

    ``` bash
    teamsfx account login azure
    ```

    Der Anmeldevorgang beginnt mit dem normalen Webbrowser.  Führen Sie den Anmeldevorgang für Ihr Azure-Konto aus.  Sie werden aufgefordert, den Browser zu schließen.

Die Kontoanmeldungen werden von Visual Studio Code und der TeamsFx CLI freigegeben.

---

## <a name="next-steps"></a>Nächste Schritte

Nachdem Ihre Entwicklungsumgebung konfiguriert ist, können Sie Ihre erste App erstellen, erstellen und Teams bereitstellen.

- [Erstellen Sie Ihre erste Teams-App mithilfe React](first-app-react.md)
- [Erstellen Ihrer ersten Teams-App mit Blazor](first-app-blazor.md)
- [Erstellen Ihrer ersten Teams-App mithilfe SharePoint-Framework (SPFx)](first-app-spfx.md)
- [Erstellen einer Unterhaltungsbot-App](first-app-bot.md)
- [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
