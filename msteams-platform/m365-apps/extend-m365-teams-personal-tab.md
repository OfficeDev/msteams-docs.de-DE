---
title: Ausweiten einer Microsoft Teams-App für persönliche Registerkarten auf Microsoft 365
description: Ausweiten einer Microsoft Teams-App für persönliche Registerkarten auf Microsoft 365
ms.date: 05/24/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: f0dc772043eca4fc624fbd04261ddbc921c91fc4
ms.sourcegitcommit: d9025e959dcdd011ed4feca820dae7c5d1251b27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65755951"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Ausweiten einer persönlichen Microsoft Teams-Registerkarte auf Microsoft 365

Persönliche Registerkarten bieten eine hervorragende Möglichkeit, das Benutzererlebnis in Microsoft Teams noch weiter zu verbessern. Mithilfe persönlicher Registerkarten können Sie einem Benutzer direkt innerhalb Microsoft Teams den Zugriff auf seine Anwendung ermöglichen, ohne dass er die Umgebung verlassen oder sich erneut anmelden muss. Mit dieser Vorschauversion können persönliche Registerkarten in anderen Microsoft 365-Anwendungen angezeigt werden. In diesem Lernprogramm wird veranschaulicht, wie eine vorhandene persönliche Microsoft Teams-Registerkarte so aktualisiert wird, dass sie sowohl in Outlook Desktop- und Webversionen als auch in Office im Web (office.com) funktioniert.

Das Aktualisieren Ihrer persönlichen App für die Ausführung in Outlook und Office umfasst die folgenden Schritte:

> [!div class="checklist"]
>
> * Aktualisieren des App-Manifests
> * Aktualisieren Ihrer TeamsJS SDK-Verweise
> * Ändern der Header Ihrer Inhaltssicherheitsrichtlinie
> * Aktualisieren Ihrer Microsoft Azure Active Directory (Azure AD) App-Registrierung für einmaliges Anmelden (Single Sign On, SSO)
> * Querladen Ihrer aktualisierten App in Teams

Der Rest dieses Leitfadens führt Sie durch diese Schritte und zeigt Ihnen, wie Sie eine Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365 Anwendungen anzeigen.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Lernprogramm benötigen Sie Folgendes:

* Einen Sandkastenmandanten für das Microsoft 365-Entwicklerprogramm
* Ihren Sandkastenmandanten, der in *gezielten Office 365-Releases* registriert ist
* Einen Computer mit Office-Apps, die über den Microsoft 365 Apps-*Betakanal* installiert sind
* (Optional) Die [Microsoft Teams-Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Microsoft Visual Studio Code zur Aktualisierung Ihres Codes

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Vorbereiten Ihrer persönlichen Registerkarte für das Upgrade

Wenn Sie über eine vorhandene persönliche Registerkarten-App verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Produktionsprojekts zum Testen und Aktualisieren Ihrer App-ID im App-Manifest, um einen neuen Bezeichner zu verwenden (der sich von der Produktions-App-ID unterscheidet, zum Testen).

Wenn Sie dieses Lernprogramm mithilfe von Beispielcode abschließen möchten, führen Sie die Setupschritte im [Todo-Listenbeispiel](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) aus, um eine persönliche Registerkarten-App mithilfe der Erweiterung Teams Toolkit für Visual Studio Code zu erstellen, und kehren Sie dann zu diesem Artikel zurück, um sie für Microsoft 365 zu aktualisieren.

Alternativ können Sie eine einfache Single Sign-On *Hello World-App* verwenden, die bereits Microsoft 365 im folgenden Schnellstartabschnitt aktiviert ist, und dann mit dem [Querladen Ihrer App in Teams](#sideload-your-app-in-teams) beginnen.

### <a name="quickstart"></a>Schnellstart

Um mit einer [persönlichen Registerkarte](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365) zu beginnen, die bereits für die Ausführung in Outlook und Office aktiviert ist, verwenden Sie Teams Toolkit-Erweiterung für Visual Studio Code.

1. Öffnen Sie in Visual Studio Code die Befehlspalette (`Ctrl+Shift+P`), geben Sie `Teams: Create a new Teams app` ein.
1. Wählen Sie die **SSO-aktivierte persönliche Registerkarte aus**.

    :::image type="content" source="images/toolkit-tab-sample.png" alt-text="Aufgabenlisten-Beispiel (funktioniert in Microsoft Teams, Outlook und Office) im Microsoft Teams-Toolkit":::

1. Wählen Sie einen Speicherort auf Ihrem lokalen Computer für den Arbeitsbereichsordner aus.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben `Teams: Provision in the cloud` Sie ein, um die erforderlichen App-Ressourcen (App Service Plan, Storage Konto, Funktions-App, verwaltete Identität) in Ihrem Azure-Konto zu erstellen.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben Sie `Teams: Deploy to the cloud` ein, um den Beispielcode für die bereitgestellten Ressourcen in Azure einzusetzen und die App zu starten.

Von hier aus können Sie die [App in Teams querladen](#sideload-your-app-in-teams) und eine Vorschau ihrer App in Outlook und Office anzeigen. (Die App-Manifest- und TeamsJS-API-Aufrufe wurden bereits für Microsoft 365 aktualisiert.)

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen die Schemaversion `1.13` des [Teams Entwicklermanifests](../resources/schema/manifest-schema.md) verwenden, damit Ihre Teams persönliche Registerkarte in Outlook und Office ausgeführt werden kann.

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

Wenn Sie das Microsoft Teams-Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie damit auch die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`), und suchen Sie **nach Teams: Überprüfen der Manifestdatei**.

## <a name="update-sdk-references"></a>Aktualisieren von SDK-Verweisen

Um in Outlook und Office ausgeführt werden zu können, muss Ihre App auf das npm-Paket `@microsoft/teams-js@2.0.0` (oder höher) verweisen. Während Code mit Versionen auf unterer Ebene in Outlook und Office unterstützt wird, werden Veraltete Warnungen protokolliert, und die Unterstützung für Versionen unterer Ebene von TeamsJS in Outlook und Office wird schließlich eingestellt.

Sie können Teams Toolkit verwenden, um die erforderlichen Codeänderungen für das Upgrade von 1.x TeamsJS-Versionen auf TeamsJS Version 2.0.0 zu identifizieren und zu automatisieren. Alternativ können Sie dieselben Schritte manuell ausführen. Weitere Informationen finden Sie [unter Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20).

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`.
1. Führen Sie den Befehl `Teams: Upgrade Teams JS SDK and code references` aus.

Nach Abschluss der Datei *"package.json* " wird auf die Datei "package.json" (oder höher) verwiesen `@microsoft/teams-js@2.0.0` , und Ihre `*.js/.ts` Dateien `*.jsx/.tsx` und Dateien werden aktualisiert mit:

> [!div class="checklist"]
> * Importieren von Anweisungen für teams-js@2.0.0
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20) für teams-js@2.0.0
> * `TODO` Kommentarerinnerungen, die Bereiche kennzeichnen, die von Änderungen der [Kontextschnittstelle](../tabs/how-to/using-teams-client-sdk.md#updates-to-the-context-interface) betroffen sein könnten
> * `TODO` Kommentarerinnerungen zum [Konvertieren von Rückruffunktionen in Zusagen](../tabs/how-to/using-teams-client-sdk.md#callbacks-converted-to-promises)

> [!IMPORTANT]
> Code in *.html* Dateien wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

## <a name="configure-content-security-policy-headers"></a>Konfigurieren der Header von Inhaltssicherheitsrichtlinien

Wie in Microsoft Teams werden Registerkartenanwendungen in [iframe-Elementen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) in Office- und Outlook-Webclients gehostet.

Wenn Ihre App CSP-Header ( [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) ) verwendet, stellen Sie sicher, dass Sie alle folgenden [Frame-Vorgänger](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) in Ihren CSP-Headern zulassen:

|Microsoft 365-Host| Frame-Vorgängerberechtigung|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Aktualisieren der Azure AD App-Registrierung für SSO

[Azure Active Directory (AD) Einmaliges Anmelden (Single Sign On, SSO)](../tabs/how-to/authentication/auth-aad-sso.md) für persönliche Registerkarten funktioniert in Office und Outlook genauso wie in Teams. Sie müssen jedoch mehrere Clientanwendungs-IDs zur Azure AD-App-Registrierung Ihrer Registerkarten-App im *App-Registrierungen* Portal Ihres Mandanten hinzufügen.

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
    |Office.com  |4765445b-32c6-49b0-83e6-1d93765276ca|
    |Office-Desktop  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
    |Outlook Desktop | d3590ed6-52b3-4102-aeff-aad2292ab01c |
    |Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
    |Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-app-in-teams"></a>Querladen der App in Microsoft Teams

Der letzte Schritt zum Ausführen Ihrer App in Office und Outlook besteht darin, das aktualisierte [App-Paket](..//concepts/build-and-test/apps-package.md) für persönliche Registerkarten in Microsoft Teams querzuladen.

1. Packen Sie Ihre Teams-Anwendung ([Manifest-](../resources/schema/manifest-schema.md) und [App-Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der Option **Teams-Metadatenpaket in einer ZIP-Datei verpacken** im Menü **Bereitstellung** von Teams Toolkit tun.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option „ Microsoft Teams-Metadatenpaket in einer ZIP-Datei verpacken“ in der Microsoft Teams-Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Microsoft Teams an, und wechseln Sie in den *Entwicklervorschaumodus*. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil Folgendes aus: **Info** > **Entwicklervorschau**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie über das Microsoft Teams-Menü mit den Auslassungspunkten die Option „Info“, und wählen Sie dann „Entwicklervorschau“ aus.":::

1. Wählen Sie **Apps** aus, um den Bereich **Apps verwalten** zu öffnen. Wählen Sie dann **App veröffentlichen** aus.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Öffnen Sie den Bereich &quot;Apps verwalten&quot;, und wählen Sie &quot;App veröffentlichen&quot; aus.":::

1. Wählen Sie **Hochladen eine benutzerdefinierte App-Option** aus, und wählen Sie Ihr App-Paket aus.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Option &quot;Benutzerdefinierte App hochladen&quot; in Microsoft Teams":::

Nachdem sie auf Teams quergeladen wurde, ist Ihre persönliche Registerkarte in Outlook und Office verfügbar. Melden Sie sich mit den gleichen Anmeldeinformationen an, die Sie zum Anmelden bei Teams zum Querladen Ihrer App verwendet haben.

Sie können die App für den schnellen Zugriff anheften, oder Sie finden Ihre App im Flyout mit den Auslassungszeichen (**...**) unter den zuletzt verwendeten Anwendungen in der Randleiste auf der linken Seite. Wenn Sie eine App in Teams anheften, heften Sie sie nicht als App in Office oder Outlook an.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Anzeigen einer Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Umgebungen

Hier erfahren Sie, wie Sie eine Vorschau Ihrer App anzeigen, die in Office- und Outlook-, Web- und Windows Desktopclients ausgeführt wird.

> [!NOTE]
> Wenn Sie Ihre App aus Teams deinstallieren, wird sie auch aus den Katalogen "**Weitere Apps**" in Outlook und Office entfernt. Wenn Sie die oben bereitgestellte Teams Toolkit-Beispiel-App verwenden.

### <a name="outlook-on-windows"></a>Outlook unter Windows

So zeigen Sie Ihre App an, die in Outlook auf Windows Desktop ausgeführt wird:

1. Starten Sie Outlook, und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Wählen Sie auf der Seitenleiste  **"Weitere Apps" aus**. Ihr quergeladener App-Titel wird unter den installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um die App in Outlook zu starten.

    :::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste in Outlook-Desktopclients auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="outlook-on-the-web"></a>Outlook im Web

So zeigen Sie Ihre App in Outlook im Web an:

1. Navigieren Sie zu [Outlook im Web](https://outlook.office.com), und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Wählen Sie die Auslassungszeichen (**...**) auf der Seitenleiste aus. Ihr quergeladener App-Titel wird unter den installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um die App zu starten und eine Vorschau anzuzeigen, die in Outlook im Web ausgeführt wird.

    :::image type="content" source="images/outlook-web-more-apps.png" alt-text="Klicken Sie auf outlook.com auf der Seitenleiste auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-on-windows"></a>Office unter Windows

So zeigen Sie Ihre App an, die in Office auf einem Windows-Desktop ausgeführt wird:

1. Starten Sie Office, und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Wählen Sie die Auslassungszeichen (**...**) auf der Seitenleiste aus. Ihr quergeladener App-Titel wird unter den installierten Apps angezeigt.
1. Wählen Sie ihr App-Symbol aus, um die App in Office zu starten.

    :::image type="content" source="images/office-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste in Office-Desktopclients auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-on-the-web"></a>Office im Web

So zeigen Sie eine Vorschau Ihrer App an, die in Office im Web ausgeführt wird:

1. Melden Sie sich bei **office.com** mit den Anmeldeinformationen des Testmandanten an.
1. Wählen Sie auf der Seitenleiste das **Symbol "Apps** " aus. Ihr quergeladener App-Titel wird unter den installierten Apps angezeigt.
1. Wählen Sie Ihr App-Symbol aus, um die App in Office im Web zu starten.

    :::image type="content" source="images/office-web-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste von office.com auf die Option &quot;Weitere Apps&quot;, um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

## <a name="troubleshooting"></a>Problembehandlung

Derzeit wird eine Teilmenge Teams Anwendungstypen und -funktionen in Outlook- und Office-Clients unterstützt. Diese Unterstützung wird im Laufe der Zeit erweitert.

Lesen Sie [Microsoft 365 Support](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook), um die Hostunterstützung für verschiedene TeamsJS-Funktionen zu überprüfen.

Eine allgemeine Zusammenfassung Microsoft 365 Host- und Plattformunterstützung für Teams-Apps finden [Sie unter Erweitern Teams apps über Microsoft 365 hinweg](overview.md).

Sie können die Hostunterstützung einer bestimmten Funktion zur Laufzeit überprüfen, indem Sie die Funktion für diese `isSupported()` Funktion (Namespace) aufrufen und das App-Verhalten entsprechend anpassen. Auf diese Weise kann Ihre App benutzeroberflächen und Funktionen in Hosts, die sie unterstützen, aufhellen und in Hosts, die dies nicht unterstützen, eine ansprechende Fallbackerfahrung bieten. Weitere Informationen finden Sie unter ["Unterscheiden der App-Erfahrung"](../tabs/how-to/using-teams-client-sdk.md#differentiate-your-app-experience).

Verwenden Sie die [Kanäle der Microsoft Teams-Entwicklercommunity](/microsoftteams/platform/feedback), um Probleme zu melden und Feedback zu geben.

### <a name="debugging"></a>Debugging

Über Teams Toolkit können Sie ihre Registerkartenanwendung, die in Office und Outlook ausgeführt wird, zusätzlich zu Teams debuggen`F5`.

:::image type="content" source="images/toolkit-debug-targets.png" alt-text="Wählen Sie aus Teams, Outlook und Office Debugzielen im Teams Toolkit aus.":::

Bei der ersten Ausführung des lokalen Debuggens zum Office oder Outlook werden Sie aufgefordert, sich bei Ihrem Microsoft 365 Mandantenkonto anzumelden und ein selbstsigniertes Testzertifikat zu installieren. Sie werden auch aufgefordert, Teams manuell zu installieren. Wählen Sie **"In Teams installieren**" aus, um ein Browserfenster zu öffnen und Ihre App manuell zu installieren. Klicken Sie dann auf **"Weiter**", um mit dem Debuggen Ihrer App in Office/Outlook fortzufahren.

:::image type="content" source="images/toolkit-dialog-teams-install.png" alt-text="Dialogfeld &quot;Toolkit&quot; Teams Installation":::

Geben Sie Feedback und melden Sie Alle Probleme mit dem Teams Toolkit-Debugging unter [Microsoft Teams Framework (TeamsFx)](https://github.com/OfficeDev/TeamsFx/issues).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
| Todoliste | Bearbeitbare Todoliste mit SSO, die mit React und Azure Functions erstellt wurde. Funktioniert nur in Teams (verwenden Sie diese Beispiel-App, um den in diesem Lernprogramm beschriebenen Upgradeprozess auszuprobieren). | [View](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend)  |
| Todoliste (Microsoft 365) | Bearbeitbare Todoliste mit SSO, die mit React und Azure Functions erstellt wurde. Funktioniert in Teams, Outlook Office. | [Anzeigen](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/todo-list-with-Azure-backend-M365)|
| Bild-Editor (Microsoft 365) | Erstellen, Bearbeiten, Öffnen und Speichern von Bildern mithilfe von Microsoft Graph-API. Funktioniert in Teams, Outlook Office. | [Anzeigen](https://github.com/OfficeDev/m365-extensibility-image-editor) |

## <a name="next-step"></a>Nächster Schritt

Veröffentlichen Sie Ihre App, damit sie in Teams, Outlook und Office auffindbar ist:

> [!div class="nextstepaction"]
> [Veröffentlichen von Teams-Apps für Outlook und Office](publish.md)
