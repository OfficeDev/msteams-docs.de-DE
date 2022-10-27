---
title: Ausweiten einer Microsoft Teams-App für persönliche Registerkarten auf Microsoft 365
description: Erfahren Sie, wie Sie Ihre persönliche Registerkarten-App so aktualisieren, dass sie zusätzlich zu Microsoft Teams in Outlook und Office ausgeführt wird.
ms.date: 10/10/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 2e16b27b0854e9dc4f92e1c7ce4dc35c2af1f5c4
ms.sourcegitcommit: 6926cf5eee55d5047c11ca13afc7f6f23e270396
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2022
ms.locfileid: "68739925"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Ausweiten einer persönlichen Microsoft Teams-Registerkarte auf Microsoft 365

Persönliche Registerkarten bieten eine hervorragende Möglichkeit, das Benutzererlebnis in Microsoft Teams noch weiter zu verbessern. Mithilfe persönlicher Registerkarten können Sie einem Benutzer direkt innerhalb Microsoft Teams den Zugriff auf seine Anwendung ermöglichen, ohne dass er die Umgebung verlassen oder sich erneut anmelden muss. Mit dieser Vorschauversion können persönliche Registerkarten in anderen Microsoft 365-Anwendungen angezeigt werden. In diesem Tutorial wird veranschaulicht, wie Sie eine vorhandene persönliche Registerkarte von Teams verwenden und aktualisieren, um sie sowohl in Outlook- als auch in Office-Desktop- und Webumgebungen sowie in der Office-App für Android auszuführen.

Das Aktualisieren Ihrer persönlichen App für die Ausführung in Outlook und Office umfasst die folgenden Schritte:

> [!div class="checklist"]
>
> * Aktualisieren Sie Ihr App-Manifest.
> * Aktualisieren Sie Ihre TeamsJS SDK-Verweise.
> * Ändern Sie die Header ihrer Inhaltssicherheitsrichtlinie.
> * Aktualisieren Sie Ihre Microsoft Azure Active Directory -App-Registrierung (Azure AD) für einmaliges Anmelden (Single Sign On, SSO).
> * Laden Sie Ihre aktualisierte App in Teams quer.

Der Rest dieses Leitfadens führt Sie durch diese Schritte und zeigt Ihnen, wie Sie eine Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Anwendungen anzeigen.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Lernprogramm benötigen Sie Folgendes:

* Einen Sandkastenmandanten für das Microsoft 365-Entwicklerprogramm
* Ihren Sandkastenmandanten, der in *gezielten Office 365-Releases* registriert ist
* Einen Computer mit Office-Apps, die über den Microsoft 365 Apps-*Betakanal* installiert sind
* (Optional) Ein Android-Gerät oder -Emulator, auf dem die Office-App für Android installiert und im *Betaprogramm* registriert ist
* (Optional) Die [Microsoft Teams-Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Microsoft Visual Studio Code zur Aktualisierung Ihres Codes

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Vorbereiten Ihrer persönlichen Registerkarte für das Upgrade

Wenn Sie über eine vorhandene persönliche Registerkarten-App verfügen, erstellen Sie eine Kopie oder einen Branch Ihres Produktionsprojekts zum Testen, und aktualisieren Sie Ihre App-ID im App-Manifest, um einen neuen Bezeichner (anders als die Produktions-App-ID zum Testen) zu verwenden.

Wenn Sie für dieses Tutorial Beispielcode verwenden möchten, führen Sie die Setupschritte im [Todo-Listenbeispiel](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) aus, um eine persönliche Registerkarten-App mit der Teams Toolkit-Erweiterung für Visual Studio Code zu erstellen. Kehren Sie dann zu diesem Artikel zurück, um sie für Microsoft 365 zu aktualisieren.

Alternativ können Sie eine einfache *Hello World-App* für einmaliges Anmelden verwenden, die Microsoft 365 bereits im folgenden [Schnellstartabschnitt](#quickstart) aktiviert hat, und dann mit [Querladen Ihrer App in Teams](#sideload-your-app-in-teams) fortfahren.

### <a name="quickstart"></a>Schnellstart

Um mit einer [persönlichen Registerkarte](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365) zu beginnen, die bereits für die Ausführung in Outlook und Office aktiviert ist, verwenden Sie die Teams-Toolkit-Erweiterung für Visual Studio Code.

1. Öffnen Sie in Visual Studio Code die Befehlspalette (`Ctrl+Shift+P`), geben Sie `Teams: Create a new Teams app` ein.
1. Wählen Sie **die persönliche Registerkarte "SSO-fähiges Anmelden" aus**.

    :::image type="content" source="images/toolkit-tab-sample.png" alt-text="Aufgabenlisten-Beispiel (funktioniert in Microsoft Teams, Outlook und Office) im Microsoft Teams-Toolkit":::

1. Wählen Sie einen Speicherort auf Ihrem lokalen Computer für den Arbeitsbereichsordner aus.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`), und geben Sie ein`Teams: Provision in the cloud`, um die erforderlichen App-Ressourcen (App Service Plan, Speicherkonto, Funktions-App, verwaltete Identität) in Ihrem Azure-Konto zu erstellen.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben Sie `Teams: Deploy to the cloud` ein, um den Beispielcode für die bereitgestellten Ressourcen in Azure einzusetzen und die App zu starten.

Von hier aus können Sie zum [Querladen Ihrer App in Teams](#sideload-your-app-in-teams) und zur Vorschau Ihrer App in Outlook und Office springen. (Das App-Manifest und die TeamsJS-API-Aufrufe wurden bereits für Microsoft 365 aktualisiert.)

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen die Schemaversion `1.13` des [Teams-Entwicklermanifests](../resources/schema/manifest-schema.md) verwenden, damit Ihre persönliche Teams-Registerkarte in Outlook und Office ausgeführt werden kann.

Sie haben zwei Möglichkeiten zum Aktualisieren Ihres App-Manifests:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die Befehlspalette: `Ctrl+Shift+P`.
1. Führen Sie den `Teams: Upgrade Teams manifest`-Befehl aus, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden direkt dort vorgenommen.

# <a name="manual-steps"></a>[Manuelle Anwendung](#tab/manifest-manual)

Öffnen Sie Ihr Microsoft Teams-App-Manifest, und aktualisieren Sie das `$schema` und die `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

Wenn Sie das Microsoft Teams-Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie damit auch die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`), und suchen **Sie nach Teams: Manifestdatei überprüfen**.

## <a name="update-sdk-references"></a>Aktualisieren von SDK-Verweisen

Für die Ausführung in Outlook und Office muss Ihre App auf das npm-Paket `@microsoft/teams-js@2.0.0` (oder höher) verweisen. Während Code mit Downlevel-Versionen in Outlook und Office unterstützt wird, werden Veraltetkeitswarnungen protokolliert, und die Unterstützung für downlevel-Versionen von TeamsJS in Outlook und Office wird schließlich eingestellt.

Sie können das Teams Toolkit verwenden, um die erforderlichen Codeänderungen zu identifizieren und zu automatisieren, um ein Upgrade von 1.x TeamsJS-Versionen auf TeamsJS-Version 2.x.x durchzuführen. Alternativ können Sie die gleichen Schritte manuell ausführen. Weitere Informationen finden Sie unter [Microsoft Teams JavaScript Client SDK](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) .

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`.
1. Führen Sie den Befehl `Teams: Upgrade Teams JS SDK and code references` aus.

Nach Abschluss des Vorgangs verweist Ihre *Datei "package.json* " auf `@microsoft/teams-js@2.0.0` (oder höher), und Ihre `*.js/.ts` Dateien und `*.jsx/.tsx` werden aktualisiert mit:

> [!div class="checklist"]
>
> * Importieren von Anweisungen für teams-js@2.x.x.x
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) für teams-js@2.x.x
> * `TODO` Kommentarerinnerungen kennzeichnen Bereiche, die möglicherweise von Änderungen an [der Kontextschnittstelle](../tabs/how-to/using-teams-client-sdk.md#updates-to-the-context-interface) betroffen sind
> * `TODO` Kommentarerinnerungen zum [Konvertieren von Rückruffunktionen in Zusagen](../tabs/how-to/using-teams-client-sdk.md#callbacks-converted-to-promises)

> [!IMPORTANT]
> Code in *.html-Dateien* wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

## <a name="configure-content-security-policy-headers"></a>Konfigurieren der Header von Inhaltssicherheitsrichtlinien

Wie in Microsoft Teams werden Registerkartenanwendungen in [iframe-Elementen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) in Office- und Outlook-Webclients gehostet.

Wenn Ihre App CSP-Header ( [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) ) verwendet, stellen Sie sicher, dass Sie alle folgenden [Frame-Vorgänger](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) in Ihren CSP-Headern zulassen:

|Microsoft 365-Host| Frame-Vorgängerberechtigung|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.microsoft365.com`, `*.office.com` |
| Outlook | `outlook.live.com`, `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Aktualisieren der Azure AD App-Registrierung für SSO

[Das einmalige Anmelden (Single Sign On, SSO) von Azure Active Directory (AD)](../tabs/how-to/authentication/tab-sso-overview.md) für persönliche Registerkarten funktioniert in Office und Outlook genauso wie in Teams. Sie müssen der Azure AD-App-Registrierung Ihrer Registerkarten-App im *App-Registrierungen-Portal* Ihres Mandanten jedoch mehrere Clientanwendungs-IDs hinzufügen.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto beim [Microsoft Azure-Portal](https://portal.azure.com) an.
1. Öffnen Sie das Blatt **App-Registrierungen**.
1. Wählen Sie den Namen Ihrer persönlichen Registerkartenanwendung aus, um die entsprechende App-Registrierung zu öffnen.
1. Wählen Sie die Option **Eine API verfügbar machen** aus (unter *Verwalten*).

    :::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorisieren von Client-IDs vom Blatt *App-Registrierungen* im Azure-Portal":::

1. Stellen Sie im Abschnitt **Autorisierte Clientanwendungen** sicher, dass alle folgenden `Client Id`-Werte hinzugefügt wurden:

    |Microsoft 365-Clientanwendung | Client-ID |
    |--|--|
    |Teams-Desktop, Mobil |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
    |Teams-Web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
    |Office Web  |4765445b-32c6-49b0-83e6-1d93765276ca|
    |Office-Desktop  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
    |Office Mobile  | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Outlook-Desktop, Mobil | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Outlook Web | bc59ab01-8403-45c6-8796-ac3ef710b3e3|

    > [!NOTE]
    > Einige Microsoft 365-Clientanwendungen teilen Client-IDs.

## <a name="sideload-your-app-in-teams"></a>Querladen der App in Microsoft Teams

Der letzte Schritt zum Ausführen Ihrer App in Office und Outlook besteht darin, Ihr aktualisiertes [App-Paket](..//concepts/build-and-test/apps-package.md) für persönliche Registerkarten in Microsoft Teams querzuladen.

1. Packen Sie Ihre Teams-Anwendung ([Manifest](../resources/schema/manifest-schema.md) - und [App-Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der Option **Teams-Metadatenpaket in einer ZIP-Datei verpacken** im Menü **Bereitstellung** von Teams Toolkit tun.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option „ Microsoft Teams-Metadatenpaket in einer ZIP-Datei verpacken“ in der Microsoft Teams-Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Microsoft Teams an, und wechseln Sie in den *Entwicklervorschaumodus*. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil Folgendes aus: **Info** > **Entwicklervorschau**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie über das Microsoft Teams-Menü mit den Auslassungspunkten die Option „Info“, und wählen Sie dann „Entwicklervorschau“ aus.":::

1. Wählen Sie **Apps** aus, um den Bereich **Apps verwalten** zu öffnen. Wählen Sie dann **App veröffentlichen** aus.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Öffnen Sie den Bereich &quot;Apps verwalten&quot;, und wählen Sie &quot;App veröffentlichen&quot; aus.":::

1. Wählen Sie **die Option Benutzerdefinierte App hochladen** aus, und wählen Sie Ihr App-Paket aus.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Option &quot;Benutzerdefinierte App hochladen&quot; in Microsoft Teams":::

Nachdem sie in Teams quergeladen wurde, ist Ihre persönliche Registerkarte in Outlook und Office verfügbar. Sie müssen sich mit den gleichen Anmeldeinformationen anmelden, die Sie zum Querladen Ihrer App in Teams verwendet haben. Wenn Sie die Office-App für Android ausführen, müssen Sie die App neu starten, um Ihre persönliche Registerkarten-App aus der Office-App zu verwenden.

Sie können die App für den schnellen Zugriff anheften, oder Sie finden Ihre App im Flyout mit den Auslassungszeichen (**...**) unter den zuletzt verwendeten Anwendungen in der Randleiste auf der linken Seite. Wenn Sie eine App in Teams anheften, wird sie nicht als App in Office oder Outlook angeheftt.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Anzeigen einer Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Umgebungen

Hier erfahren Sie, wie Sie eine Vorschau Ihrer App anzeigen, die in Office- und Outlook-, Web- und Windows-Desktopclients ausgeführt wird.

> [!NOTE]
> Wenn Sie Ihre App aus Teams deinstallieren, wird sie auch aus den **Katalogen weitere Apps** in Outlook und Office entfernt. Wenn Sie die oben bereitgestellte Teams Toolkit-Beispiel-App verwenden.

### <a name="outlook-on-windows"></a>Outlook unter Windows

So zeigen Sie Ihre App an, die in Outlook auf Windows Desktop ausgeführt wird:

1. Starten Sie Outlook, und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Wählen Sie auf der Seitenleiste  **Weitere Apps** aus. Ihr quergeladener App-Titel wird unter Ihren installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um Ihre App in Outlook zu starten.

    :::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste in Outlook-Desktopclients auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="outlook-on-the-web"></a>Outlook im Web

So zeigen Sie Ihre App in Outlook im Web an:

1. Wechseln [Sie zu Outlook im Web](https://outlook.office.com), und melden Sie sich mit Ihrem Entwicklermandantenkonto an.
1. Wählen Sie auf der Seitenleiste  **Weitere Apps** aus. Ihr quergeladener App-Titel wird unter Ihren installierten Apps angezeigt.
1. Wählen Sie ihr App-Symbol aus, um Ihre App zu starten und eine Vorschau anzuzeigen, die in Outlook im Web ausgeführt wird.

    :::image type="content" source="images/outlook-web-more-apps.png" alt-text="Klicken Sie auf outlook.com auf der Seitenleiste auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-on-windows"></a>Office unter Windows

So zeigen Sie Ihre App an, die in Office auf einem Windows-Desktop ausgeführt wird:

1. Starten Sie Office, und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Wählen Sie auf der Seitenleiste das **Symbol Apps** aus. Ihr quergeladener App-Titel wird unter Ihren installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um Ihre App in Office zu starten.

    :::image type="content" source="images/office-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste in Office-Desktopclients auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-on-the-web"></a>Office im Web

So zeigen Sie eine Vorschau Ihrer App an, die in Office im Web ausgeführt wird:

1. Melden Sie sich mit den Anmeldeinformationen des Testmandanten bei **office.com** an.
1. Wählen Sie auf der Seitenleiste das **Symbol Apps** aus. Ihr quergeladener App-Titel wird unter Ihren installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um Ihre App in Office im Web zu starten.

    :::image type="content" source="images/office-web-more-apps.png" alt-text="Klicken Sie auf die Option &quot;Weitere Apps&quot; in der Seitenleiste von office.com, um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-app-for-android"></a>Office-App für Android

> [!NOTE]
> Führen Sie vor der Installation der App [die Schritte aus, um den neuesten Betabuild der Office-App zu installieren](prerequisites.md#mobile) und Teil des Betaprogramms zu sein.

So zeigen Sie ihre App an, die in der Office-App für Android ausgeführt wird:

1. Starten Sie die Office-App, und melden Sie sich mit Ihrem Entwicklermandantenkonto an. Wenn die Office-App für Android bereits vor dem Querladen Ihrer App in Teams ausgeführt wurde, müssen Sie sie neu starten, um sie unter Ihren installierten Apps anzuzeigen.
1. Wählen Sie das **Symbol Apps** aus. Ihre quergeladene App wird unter den installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um Ihre App in der Office-App für Android zu starten.

:::image type="content" source="images/office-mobile-apps.png" alt-text="Tippen Sie auf die Option &quot;Apps&quot; in der Seitenleiste der Office-App, um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

## <a name="troubleshooting"></a>Problembehandlung

Derzeit wird eine Teilmenge der Teams-Anwendungstypen und -Funktionen in Outlook- und Office-Clients unterstützt. Diese Unterstützung wird im Laufe der Zeit erweitert.

Informationen zum Hostsupport für verschiedene TeamsJS-Funktionen finden Sie unter [Microsoft 365-Support](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook) .

Eine allgemeine Zusammenfassung der Microsoft 365-Host- und Plattformunterstützung für Teams-Apps finden Sie unter [Erweitern von Teams-Apps auf Microsoft 365](overview.md).

Sie können die Hostunterstützung einer bestimmten Funktion zur Laufzeit überprüfen, indem Sie die `isSupported()` Funktion für diese Funktion (Namespace) aufrufen und das App-Verhalten entsprechend anpassen. Dadurch kann Ihre App die Benutzeroberfläche und Funktionalität auf Hosts, die sie unterstützen, aufleuchten und eine ordnungsgemäße Fallbackerfahrung auf Hosts bereitstellen, die dies nicht unterstützen. Weitere Informationen finden Sie unter [Differenzieren ihrer App-Erfahrung](../tabs/how-to/using-teams-client-sdk.md#differentiate-your-app-experience).

Verwenden Sie die [Kanäle der Microsoft Teams-Entwicklercommunity](/microsoftteams/platform/feedback), um Probleme zu melden und Feedback zu geben.

### <a name="debugging"></a>Debugging

Im Teams Toolkit können Sie Ihre Registerkartenanwendung debuggen (`F5`), die in Office und Outlook ausgeführt wird, zusätzlich zu Teams.

:::image type="content" source="images/toolkit-debug-targets.png" alt-text="Auswählen von Teams-, Outlook- und Office-Debugzielen im Teams-Toolkit":::

Beim ersten Ausführen des lokalen Debuggens in Office oder Outlook werden Sie aufgefordert, sich bei Ihrem Microsoft 365-Mandantenkonto anzumelden und ein selbstsigniertes Testzertifikat zu installieren. Sie werden auch aufgefordert, Teams manuell zu installieren. Wählen Sie **In Teams installieren** aus, um ein Browserfenster zu öffnen und Ihre App manuell zu installieren. Wählen Sie dann **Weiter** aus, um mit dem Debuggen Ihrer App in Office/Outlook fortzufahren.

:::image type="content" source="images/toolkit-dialog-teams-install.png" alt-text="Toolkitdialogfeld teams install":::

Geben Sie Feedback, und melden Sie alle Probleme mit der Debugerfahrung des Teams-Toolkits unter [Microsoft Teams Framework (TeamsFx).](https://github.com/OfficeDev/TeamsFx/issues)

#### <a name="mobile-debugging"></a>Mobiles Debuggen

Das Debuggen des Teams-Toolkits (`F5`) wird mit der Office-App für Android noch nicht unterstützt. Hier erfahren Sie, wie Sie Ihre App, die in der Office-App für Android ausgeführt wird, remote debuggen:

1. Wenn Sie mit einem physischen Android-Gerät debuggen, verbinden Sie es mit Ihrem Entwicklungscomputer, und aktivieren Sie die Option für [das USB-Debuggen](https://developer.android.com/studio/debug/dev-options). Dies ist standardmäßig mit dem Android-Emulator aktiviert.
1. Starten Sie die Office-App von Ihrem Android-Gerät aus.
1. Öffnen Sie Ihr Profil **Ich > Einstellungen > Debuggen zulassen**, und aktivieren Sie die Option **Remotedebuggen aktivieren**.

    :::image type="content" source="images/office-android-enable-remote-debugging.png" alt-text="Screenshot: Aktivieren des Remotedebuggens":::

1. **Ausgangseinstellungen**.
1. Beenden Sie den Profilbildschirm.
1. Wählen Sie **Apps** aus, und starten Sie Ihre quergeladene App, um sie in der Office-App auszuführen.
1. Stellen Sie sicher, dass Ihr Android-Gerät mit Ihrem Entwicklungscomputer verbunden ist. Öffnen Sie auf Ihrem Entwicklungscomputer Ihren Browser, um die zugehörige DevTools-Inspektionsseite zu öffnen. Wechseln Sie beispielsweise in Microsoft Edge zu `edge://inspect/#devices` , um eine Liste der debugfähigen Android WebViews anzuzeigen.
1. Suchen Sie die `Microsoft Teams Tab` mit Ihrer Registerkarten-URL, und wählen Sie **Überprüfen** aus, um mit dem Debuggen Ihrer App mit DevTools zu beginnen.

    :::image type="content" source="images/office-android-debug.png" alt-text="Screenshot: Liste der Webviews in devtool":::

1. Debuggen Sie Ihre Registerkarten-App in der Android WebView. Auf die gleiche Weise debuggen Sie eine reguläre Website [auf einem Android-Gerät remote](/microsoft-edge/devtools-guide-chromium/remote-debugging) .

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
| Aufgabenliste | Bearbeitbare Aufgabenliste mit SSO, die mit React und Azure Functions erstellt wurde. Funktioniert nur in Teams (verwenden Sie diese Beispiel-App, um den in diesem Tutorial beschriebenen Upgradeprozess auszuprobieren). | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend)  |
| Aufgabenliste (Microsoft 365) | Bearbeitbare Aufgabenliste mit SSO, die mit React und Azure Functions erstellt wurde. Funktioniert in Teams, Outlook, Office. | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365)|
| Bildbearbeitung (Microsoft 365) | Erstellen, Bearbeiten, Öffnen und Speichern von Bildern mithilfe von Microsoft Graph-API. Funktioniert in Teams, Outlook, Office. | [View](https://github.com/OfficeDev/m365-extensibility-image-editor) |
| Beispielstartseite (Microsoft 365) | Veranschaulicht SSO-Authentifizierung und TeamsJS SDK-Funktionen, die auf verschiedenen Hosts verfügbar sind. Funktioniert in Teams, Outlook, Office. | [Anzeigen](https://github.com/OfficeDev/microsoft-teams-library-js/tree/main/apps/sample-app) |
| Northwind Orders-App | Veranschaulicht, wie Sie microsoft TeamsJS SDK V2 verwenden, um die Teams-Anwendung auf andere M365-Host-Apps zu erweitern. Funktioniert in Teams, Outlook, Office. Optimiert für Mobilgeräte.| [Anzeigen](https://github.com/microsoft/app-camp/tree/main/experimental/ExtendTeamsforM365) |

## <a name="next-step"></a>Nächster Schritt

Veröffentlichen Sie Ihre App, damit sie in Teams, Outlook und Office auffindbar ist:

> [!div class="nextstepaction"]
> [Veröffentlichen von Teams-Apps für Outlook und Office](publish.md)
