---
title: Erste Schritte – Voraussetzungen
author: adrianhall
description: Erfahren Sie, wie Sie mit der Microsoft Teams App-Entwicklung beginnen und Ihre Umgebung einrichten.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.localizationpriority: none
ms.openlocfilehash: de9b351761f45999ce8cb0438c5d83041727f7f5
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156526"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a>Voraussetzungen: Erste Schritte mit Microsoft Teams App-Entwicklung

Bevor Sie mit dem Erstellen Ihrer ersten Teams-App beginnen, müssen Sie einige Tools installieren und Ihre Entwicklungsumgebung einrichten.

## <a name="install-required-tools"></a>Installieren erforderlicher Tools

Einige der benötigten Tools hängen davon ab, wie Sie Ihre Teams-App erstellen möchten:

- [Node.js](https://nodejs.org/en/download/) (verwenden Sie die neueste Version von v14 LTS)
- Ein Browser mit Entwicklertools, z. [B. Microsoft Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/)
- Wenn Sie mit JavaScript, TypeScript oder dem SharePoint-Framework (SPFx) entwickeln, installieren Sie [Visual Studio Code](https://code.visualstudio.com/download)Version 1.55 oder höher.  
- Wenn Sie mit .NET entwickeln, installieren Sie [Visual Studio 2019](https://visualstudio.com/download). Stellen Sie sicher, dass Sie die **ASP.NET- und Webentwicklung** oder **die plattformübergreifende .NET Core-Entwicklungsworkload** installieren.

> [!WARNING]
> Es gibt bekannte Probleme mit `npm@7` , die mit Node v15 und höher gepackt sind. Wenn Beim Ausführen Probleme `npm install` auftreten, stellen Sie sicher, dass Sie Node v14 (LTS) verwenden.

## <a name="install-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Teams Toolkit vereinfacht den Entwicklungsprozess mit Tools zum Bereitstellen und Bereitstellen von Cloudressourcen für Ihre App, zum Veröffentlichen im Teams Store und vieles mehr. Sie können das Toolkit mit Visual Studio Code, Visual Studio oder als CLI `teamsfx` (called) verwenden. Weitere Informationen finden Sie unter [Teams Toolkit für Visual Studio Code,](../toolkit/visual-studio-code-overview.md) [Teams Toolkit für Visual Studio](../toolkit/visual-studio-overview.md) und [Teamsfx CLI Tool.](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli)

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie die **Erweiterungsansicht** (**STRG+UMSCHALT+X**  /  **⌘⇧-X** oder **Ansicht > Erweiterungen) aus.**
1. Geben Sie in das Suchfeld **Teams Toolkit** ein.
1. Wählen  Sie neben dem Teams Toolkit installieren aus.

Sie finden auch das Teams Toolkit auf dem [Visual Studio Code Marketplace.](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)

Die folgenden Tools können von der Visual Studio Code-Erweiterung installiert werden, wenn sie benötigt werden. Wenn sie bereits installiert ist, kann stattdessen die installierte Version verwendet werden. Wenn Sie Linux einschließlich WSL verwenden, müssen Sie diese Tools vor der Verwendung installieren:

- [Azure Functions Core Tools](/azure/azure-functions/functions-run-local)

    Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debugausführung lokal auszuführen, einschließlich der Authentifizierungshilfsprogramme, die beim Ausführen Ihrer Dienste in Azure erforderlich sind. Sie wird im Projektverzeichnis installiert (mithilfe des `devDependencies` npm).

- [.NET SDK](/dotnet/core/install/)

    Das .NET SDK wird verwendet, um angepasste Bindungen für lokales Debuggen und Azure Functions-App-Bereitstellungen zu installieren. Wenn Sie das .NET 3.1 SDK (oder höher) nicht global installiert haben, kann die portierbare Version installiert werden.

- [ngrok](https://ngrok.com/download)

    Einige Teams App-Features (Unterhaltungs-Bots, Messaging-Erweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen. Sie müssen Ihr Entwicklungssystem für Teams über einen Tunnel verfügbar machen. Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich. Dieses Paket wird im Projektverzeichnis installiert (mit `devDependencies` npm).

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Sie können Visual Studio 2019 verwenden, um Teams-Apps mit Demzversenserver in .NET zu entwickeln. Wenn Sie nicht beabsichtigen, Teams Apps in .NET zu entwickeln, installieren Sie die Visual Studio Code Version von Teams Toolkit.

So installieren Sie die Teams Toolkit-Erweiterung:

1. Öffnen Sie Visual Studio 2019.
1. Wählen Sie **Erweiterungen**  >  **aus, um Erweiterungen zu verwalten.**
1. Geben Sie in das Suchfeld **Teams Toolkit** ein.
1. Wählen Sie die Teams Toolkit-Erweiterung aus, und wählen Sie **"Herunterladen"** aus. Die Erweiterung wird heruntergeladen.
1. Schließen Sie Visual Studio 2019, um die Erweiterung zu installieren.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Um die TeamsFx CLI zu installieren, verwenden Sie den `npm` Paket-Manager:

``` bash
npm install -g @microsoft/teamsfx-cli
```

Je nach Konfiguration müssen Sie die CLI möglicherweise `sudo` verwenden:

``` bash
sudo npm install -g --unsafe-perm @microsoft/teamsfx-cli
```

Dies ist auf Linux- und macOS-Systemen häufiger.

Stellen Sie sicher, dass Sie dem PFAD den globalen npm-Cache hinzufügen. Dies geschieht normalerweise als Teil des Node.js-Installationsprogramms.  

Sie können die CLI mit dem `teamsfx` Befehl verwenden. Stellen Sie sicher, dass der Befehl funktioniert, indem Sie `teamsfx -h` .

> [!CAUTION]
> Bevor Sie TeamsFx in PowerShell-Terminalen ausführen können, müssen Sie die Ausführungsrichtlinie "Remotesignierung" für PowerShell aktivieren. Weitere Informationen finden Sie in der [PowerShell-Dokumentation.](/powershell/module/microsoft.powershell.core/about/about_signing)

---

## <a name="install-optional-tools"></a>Installieren optionaler Tools

Installieren Sie Browsertools für die App-Entwicklung. Wenn Ihre App beispielsweise mit React geschrieben wurde, können Sie React Developer Tools verwenden:

- [React Entwicklertools für Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)
- [React Entwicklertools für Edge](https://microsoftedge.microsoft.com/addons/detail/react-developer-tools/gpphkfbcpidddadnkolkpfckpihlkkil)

Wenn Sie auf in Azure gespeicherte Daten zugreifen oder ein cloudbasiertes Back-End für Ihre Teams-App in Azure bereitstellen möchten, installieren Sie diese Tools:

- [Azure-Tools für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [Azure CLI](/cli/azure/install-azure-cli)

Wenn Sie mit Microsoft Graph-Daten arbeiten, sollten Sie den Microsoft Graph-Explorer mit einem Lesezeichen versehen. Mit diesem browserbasierten Tool können Sie Microsoft Graph außerhalb einer App abfragen.

- [Microsoft Graph-Tester](https://developer.microsoft.com/graph/graph-explorer)

Mit dem Entwicklerportal für Teams können Sie Ihre Teams App konfigurieren, verwalten und an Ihre Organisation oder den Teams Store verteilen.

- [Entwicklerportal für Teams](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a>Aktivieren des Querladens

Während der Entwicklung müssen Sie Ihre App innerhalb Teams laden, ohne sie zu verteilen. Dies wird als Querladen bezeichnet.

Wenn Sie über ein Teams Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:

1. Wählen Sie im Teams Client **Apps** aus.
1. Wählen Sie **Hochladen einer benutzerdefinierten App** aus.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Abbildung, die zeigt, wo in Teams Sie eine benutzerdefinierte App hochladen können.":::

> [!NOTE]
> Wenn Sie Apps immer noch nicht querladen können, wenden Sie sich an Ihren Teams-Administrator. Weitere Informationen finden Sie unter [Aktivieren von benutzerdefinierten Teams-Apps und Aktivieren des hochladens benutzerdefinierter Apps.](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

## <a name="get-a-free-teams-developer-tenant-optional"></a>Abrufen eines kostenlosen Teams Entwicklermandanten (optional)

Wenn die Option zum Querladen nicht angezeigt wird oder Sie nicht über ein Teams Konto verfügen, können Sie ein kostenloses Teams Entwicklerkonto erhalten, indem Sie am M365-Entwicklerprogramm teilnehmen.  Der Registrierungsvorgang dauert ungefähr zwei Minuten.

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm.](https://developer.microsoft.com/microsoft-365/dev-program)
1. Wählen Sie **"Jetzt beitreten"** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wählen Sie auf der Willkommensseite **"E5-Abonnement einrichten"** aus.
1. Richten Sie Ihr Administratorkonto ein. Nach Abschluss des Vorgangs sollte ein Bildschirm wie dieser angezeigt werden.

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was nach der Registrierung für das Microsoft 365-Entwicklerprogramm angezeigt wird.":::

1. Melden Sie sich mit dem soeben eingerichteten Administratorkonto bei Teams an. Stellen Sie sicher, dass Sie über die **Hochladen einer benutzerdefinierten App-Option** verfügen.

## <a name="get-a-free-azure-account"></a>Abrufen eines kostenlosen Azure-Kontos

Wenn Sie Ihre App hosten oder auf Ressourcen in Azure zugreifen möchten, benötigen Sie ein Azure-Abonnement.  Sie können [ein kostenloses Konto erstellen,](https://azure.microsoft.com/free/) bevor Sie beginnen.

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a>Melden Sie sich bei Ihren Microsoft 365- und Azure-Konten an.

Sie müssen Zugriff auf zwei Konten haben:

- Ihre Microsoft 365 Kontoanmeldeinformationen. Dies ist das Konto, mit dem Sie sich bei Teams anmelden. Wenn Sie einen Mandanten für Microsoft 365 Entwicklerprogramm verwenden, ist dies das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.
- Ihre Azure-Anmeldeinformationen. Dies ist das Konto, das Sie für den Zugriff auf das Azure-Portal und für die Bereitstellung neuer Cloudressourcen zur Unterstützung Ihrer App verwenden.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Visual Studio Code
1. Wählen Sie das Symbol Teams in der Seitenleiste aus:

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Wählen Sie **"Bei M365 anmelden"** aus.

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Speicherort des Abschnitts &quot;Konten&quot;, der für die Anmeldung verwendet wird.":::

    Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser. Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab. Wenn Sie dazu aufgefordert werden, können Sie den Browser schließen und zu Visual Studio Code zurückkehren.
1. Kehren Sie zum Teams Toolkit in Visual Studio Code zurück.
1. Wählen Sie **"Bei Azure anmelden"** aus.

    > [!TIP]
    > Wenn Sie die Azure-Kontoerweiterung installiert haben und dasselbe Konto verwenden, können Sie diesen Schritt überspringen. Verwenden Sie das gleiche Konto wie in anderen Erweiterungen.

1. Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser.  Schließen Sie den Anmeldevorgang für Ihr Azure-Konto ab. Wenn Sie dazu aufgefordert werden, können Sie den Browser schließen und zu Visual Studio Code zurückkehren.

    Nach Abschluss des Vorgangs werden im Abschnitt **"KONTEN"** der Randleiste die beiden Konten separat zusammen mit der Anzahl der verwendbaren Azure-Abonnements angezeigt, die Ihnen zur Verfügung stehen. Stellen Sie sicher, dass mindestens ein verwendbares Azure-Abonnement verfügbar ist. Wenn nicht, melden Sie sich ab, und verwenden Sie ein anderes Konto.

# <a name="visual-studio-2019"></a>[Visual Studio 2019](#tab/vs)

Visual Studio 2019 werden Sie aufgefordert, sich bei jedem Dienst bei Bedarf anzumelden. Sie müssen sich nicht vorab bei Ihren M365- und Azure-Konten anmelden.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

1. Melden Sie sich bei Microsoft 365 mit der TeamsFx CLI an:

    ``` bash
    teamsfx account login m365
    ```

    Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser. Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab. Sie werden aufgefordert, den Browser zu schließen.

2. Melden Sie sich bei Azure mit der TeamsFx CLI an:

    ``` bash
    teamsfx account login azure
    ```

    Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser. Schließen Sie den Anmeldevorgang für Ihr Azure-Konto ab. Sie werden aufgefordert, den Browser zu schließen.

    Die Kontoanmeldungen werden zwischen Visual Studio Code und der TeamsFx CLI geteilt.



    Nachdem Ihre Entwicklungsumgebung konfiguriert ist, können Sie Ihre erste Teams App erstellen, erstellen und bereitstellen.

## <a name="see-also"></a>Siehe auch

* [Übersicht über Lernprogramme](code-samples.md) 
* [Erstellen einer App mit React](first-app-react.md)
* [Erstellen einer App mitHilfe von Blatter](first-app-blazor.md)
* [Erstellen einer App mit SPFx](first-app-spfx.md)
* [Erstellen einer App mithilfe von C# oder .NET](get-started-dotnet-app-studio.md)
* [Erstellen einer App mithilfe von Node.js](get-started-nodejs-app-studio.md)
* [Erstellen einer App mithilfe des Yeoman-Generators](get-started-yeoman.md)
* [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
* [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)
