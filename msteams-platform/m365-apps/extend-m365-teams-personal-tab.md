---
title: Ausweiten einer Microsoft Teams-App für persönliche Registerkarten auf Microsoft 365
description: Ausweiten einer Microsoft Teams-App für persönliche Registerkarten auf Microsoft 365
ms.date: 02/11/2022
ms.topic: tutorial
ms.custom: Microsoft 365 apps
ms.localizationpriority: high
ms.openlocfilehash: 873a6fa6207d122581e18cef0ae922ffca87762f
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111521"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Ausweiten einer persönlichen Microsoft Teams-Registerkarte auf Microsoft 365

> [!NOTE]
> Das *Ausweiten einer persönlichen Microsoft Teams-Registerkarte auf Microsoft 365* ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar. Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Persönliche Registerkarten bieten eine hervorragende Möglichkeit, das Benutzererlebnis in Microsoft Teams noch weiter zu verbessern. Mithilfe persönlicher Registerkarten können Sie einem Benutzer direkt innerhalb Microsoft Teams den Zugriff auf seine Anwendung ermöglichen, ohne dass er die Umgebung verlassen oder sich erneut anmelden muss. Mit dieser Vorschauversion können persönliche Registerkarten in anderen Microsoft 365-Anwendungen angezeigt werden. In diesem Lernprogramm wird veranschaulicht, wie eine vorhandene persönliche Microsoft Teams-Registerkarte so aktualisiert wird, dass sie sowohl in Outlook Desktop- und Webversionen als auch in Office im Web (office.com) funktioniert.

Das Aktualisieren Ihrer persönlichen App für Outlook und Office Home umfasst die folgenden Schritte:

> [!div class="checklist"]
>
> * Aktualisieren des App-Manifests
> * Aktualisieren Ihrer TeamsJS SDK-Verweise
> * Ändern der Header Ihrer Inhaltssicherheitsrichtlinie
> * Aktualisieren Ihrer Microsoft Azure Active Directory (Azure AD) App-Registrierung für einmaliges Anmelden (Single Sign On, SSO)

Zum Testen Ihrer App sind die folgenden Schritte erforderlich:

> [!div class="checklist"]
>
> * Registrieren Ihres Microsoft 365-Mandanten in *gezielten Versionen von Office 365*
> * Konfigurieren Ihres Kontos für den Zugriff auf Vorschauversionen von Outlook- und Office-Apps
> * Querladen der aktualisierten App in Microsoft Teams

Nach diesen Schritten sollte Ihre App in den Vorschauversionen von Outlook- und Office-Apps angezeigt werden.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Lernprogramm benötigen Sie Folgendes:

* Einen Sandkastenmandanten für das Microsoft 365-Entwicklerprogramm
* Ihren Sandkastenmandanten, der in *gezielten Office 365-Releases* registriert ist
* Einen Computer mit Office-Apps, die über den Microsoft 365 Apps-*Betakanal* installiert sind
* (Optional) Die [Microsoft Teams-Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Microsoft Visual Studio Code zur Aktualisierung Ihres Codes

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Vorbereiten Ihrer persönlichen Registerkarte für das Upgrade

Wenn Sie über eine vorhandene persönliche Registerkarte verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Produktionsprojekts zum Testen, und aktualisieren Sie Ihre App-ID im App-Manifest, um einen neuen Bezeichner (unterschiedlich von der Produktions-App-ID) zu verwenden.

Wenn Sie zum Durchführen dieses Lernprogramms Beispielcode verwenden möchten, führen Sie die Setupschritte unter [Erste Schritte mit dem Aufgabenlisten-Beispiel](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) aus, um eine persönliche Registerkarten-App mithilfe der Microsoft Teams-Toolkit-Erweiterung für Visual Studio Code zu erstellen. Oder Sie können mit demselben [für TeamsJS SDK v2 Preview aktualisierten Aufgabenlisten-Beispiel](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend-M365) starten und mit dem [Anzeigen einer Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Lösungen](#preview-your-personal-tab-in-other-microsoft-365-experiences) fortfahren. Das aktualisierte Beispiel ist auch in der Microsoft Teams-Toolkit-Erweiterung verfügbar: *Entwicklung* > *Beispiele anzeigen* > **Aufgabenliste (funktioniert in Microsoft Teams, Outlook und Office)**.

:::image type="content" source="images/toolkit-todo-sample.png" alt-text="Aufgabenlisten-Beispiel (funktioniert in Microsoft Teams, Outlook und Office) im Microsoft Teams-Toolkit":::

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen das Schema für das [Microsoft Teams-Entwicklervorschaumanifest](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) und die `Microsoft 365 DevPreview`-Manifestversion verwenden, damit Ihre persönliche Microsoft Teams-Registerkarte in Outlook angezeigt werden kann.

Sie können entweder das Microsoft Teams-Toolkit verwenden, um Ihr App-Manifest zu aktualisieren, oder die Änderungen manuell anwenden:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen Sie den `Teams: Upgrade Teams manifest to support Outlook and Office apps`-Befehl aus, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden direkt dort vorgenommen.

# <a name="manual-steps"></a>[Manuelle Anwendung](#tab/manifest-manual)

Öffnen Sie Ihr Microsoft Teams-App-Manifest, und aktualisieren Sie das `$schema` und die `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Wenn Sie das Microsoft Teams-Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie damit auch die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette `Ctrl+Shift+P`, und suchen Sie **Microsoft Teams: Manifestdatei validieren**, oder wählen Sie die Option im Menü „Bereitstellung“ des Microsoft Teams-Toolkits aus (suchen Sie nach dem Microsoft Teams-Symbol auf der linken Seite von Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Microsoft Teams-Toolkit-Option &quot;Manifestdatei validieren&quot; im Menü &quot;Bereitstellung&quot;":::

## <a name="update-sdk-references"></a>Aktualisieren von SDK-Verweisen

Um in Outlook und Office ausgeführt werden zu können, muss Ihre App vom npm-Paket `@microsoft/teams-js@2.0.0-beta.1` (oder einer höheren *Betaversion*) abhängig sein. Code mit früheren Versionen von `@microsoft/teams-js` wird in Outlook und Office zwar unterstützt, aber es werden Warnungen zu diesen veralteten Versionen protokolliert, und die Unterstützung für frühere Versionen von `@microsoft/teams-js` in Outlook und Office wird irgendwann eingestellt.

Sie können das Microsoft Teams-Toolkit verwenden, um einige der Codeänderungen für die Übernahme der nächsten Version von `@microsoft/teams-js` zu automatisieren. Wenn Sie die Schritte jedoch manuell ausführen möchten, finden Sie unter [Microsoft Teams JavaScript-Client-SDK – Vorschau](using-teams-client-sdk-preview.md) entsprechende Informationen.

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen Sie den Befehl `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps` aus.

Nach Abschluss des Vorgangs hat das Hilfsprogramm Ihre `package.json`-Datei mit der Abhängigkeit von TeamsJS SDK (Vorschau), `@microsoft/teams-js@2.0.0-beta.1` oder höher, aktualisiert, und Ihre `*.js/.ts`- und `*.jsx/.tsx`-Dateien werden aktualisiert mit:

> [!div class="checklist"]
>
> * `package.json`-Verweisen auf TeamsJS SDK (Vorschau)
> * Importanweisungen für TeamsJS SDK (Vorschau)
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](using-teams-client-sdk-preview.md#apis-organized-into-capabilities) an TeamsJS SDK (Vorschau)
> * `TODO`-Kommentarerinnerungen zum Überprüfen von Bereichen, die von Änderungen an der [Kontextschnittstelle](using-teams-client-sdk-preview.md#updates-to-the-context-interface) betroffen sein könnten
> * `TODO`-Kommentarerinnerungen, um sicherzustellen, dass die [ Konvertierung in Zusagenfunktionen aus Rückruffunktionen](using-teams-client-sdk-preview.md#callbacks-converted-to-promises) bei jeder Aufrufsite, die das Tool gefunden hat, gut funktioniert hat

> [!IMPORTANT]
> Code in *.html*-Dateien wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

> [!NOTE]
> Wenn Sie Ihren Code manuell aktualisieren möchten, lesen Sie [Microsoft Teams JavaScript-Client-SDK – Vorschau](using-teams-client-sdk-preview.md), um mehr über die erforderlichen Änderungen zu erfahren.

## <a name="configure-content-security-policy-headers"></a>Konfigurieren der Header von Inhaltssicherheitsrichtlinien

[Wie in Microsoft Teams](/microsoftteams/platform/tabs/what-are-tabs) werden Registerkartenanwendungen in Office- und Outlook-Webclients (in [iframe-Elementen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)) gehostet.

Wenn Ihre App CSP-Header ([Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy)) verwendet, stellen Sie sicher, dass Sie alle folgenden [Frame-Vorgänger](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) in Ihren CSP-Headern zulassen:

|Microsoft 365-Host| Frame-Vorgängerberechtigung|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com`, `outlook-sdf.office.com`, `outlook-sdf.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Aktualisieren der Azure AD App-Registrierung für SSO

Azure Active Directory-SSO (Single Sign On, einmaliges Anmelden) für persönliche Registerkarten funktioniert in Office und Outlook genauso [wie in Microsoft Teams](/microsoftteams/platform/tabs/how-to/authentication/auth-aad-sso). Sie müssen jedoch der Azure AD App-Registrierung Ihrer Registerkarten-App im *App-Registrierungsportal* Ihres Mandanten mehrere Clientanwendungsbezeichner hinzufügen.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto beim [Microsoft Azure-Portal](https://portal.azure.com) an.
1. Öffnen Sie das Blatt **App-Registrierungen**.
1. Wählen Sie den Namen Ihrer persönlichen Registerkartenanwendung aus, um die entsprechende App-Registrierung zu öffnen.
1. Wählen Sie die Option **Eine API verfügbar machen** aus (unter *Verwalten*).

:::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorisieren von Client-IDs vom Blatt *App-Registrierungen* im Azure-Portal":::

Stellen Sie im Abschnitt **Autorisierte Clientanwendungen** sicher, dass alle folgenden `Client Id`-Werte hinzugefügt wurden:

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

Der letzte Schritt besteht darin, die aktualisierte persönliche Registerkarte ([App-Paket](/microsoftteams/platform/concepts/build-and-test/apps-package)) in Microsoft Teams querzuladen. Nach Abschluss des Vorgangs kann Ihre App zusätzlich zu Microsoft Teams auch in Office und Outlook ausgeführt werden.

1. Verpacken Sie Ihre Microsoft Teams-Anwendung (Manifest- und App-[Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie das Microsoft Teams-Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der Option **Microsoft Teams-Metadatenpaket in einer ZIP-Datei verpacken** im Menü *Bereitstellung* des Microsoft Teams-Toolkits oder in der Befehlspalette `Ctrl+Shift+P` von Visual Studio Code tun:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option „ Microsoft Teams-Metadatenpaket in einer ZIP-Datei verpacken“ in der Microsoft Teams-Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Microsoft Teams an, und vergewissern Sie sich, dass Sie sich in der öffentlichen Entwicklervorschau befinden. Sie können überprüfen, ob Sie sich in der Vorschau im Microsoft Teams-Client befinden, indem Sie in Ihrem Benutzerprofil auf das Menü mit den Auslassungspunkten (**...**) klicken, "**Info**" öffnen und nachsehen, ob die Option *Entwicklervorschau* aktiviert ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie über das Microsoft Teams-Menü mit den Auslassungspunkten die Option „Info“, und stellen Sie sicher, dass die Option „Entwicklervorschau“ aktiviert ist.":::

1. Öffnen Sie den Bereich *Apps*, klicken Sie auf **Benutzerdefinierte App hochladen** und dann auf **Für mich oder meine Teams hochladen**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Schaltfläche „Benutzerdefinierte App hochladen“ im Microsoft Teams-Bereich „Apps“":::

1. Wählen Sie Ihr App-Paket aus, und klicken Sie auf *Öffnen*.

Nach dem Querladen über Microsoft Teams ist Ihre persönliche Registerkarte in Outlook und Office verfügbar. Melden Sie sich mit denselben Anmeldeinformationen an, die Sie zum Querladen Ihrer App in Microsoft Teams verwendet haben.

Sie können die App für den schnellen Zugriff anheften, oder Sie finden Ihre App im Flyout mit den Auslassungszeichen (**...**) unter den zuletzt verwendeten Anwendungen in der Randleiste auf der linken Seite.

> [!NOTE]
> Durch das Anheften einer App in Microsoft Teams wird sie nicht als App in Office.com oder Outlook angeheftet.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Anzeigen einer Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Umgebungen

Wenn Sie ihre persönliche Microsoft Teams-Registerkarte aktualisieren und in Microsoft Teams querladen, kann sie in Outlook unter Windows, im Web, Office unter Windows und im Web (office.com) angezeigt werden. Nachfolgend wird beschrieben, wie Sie eine Vorschau davon in diesen Microsoft 365-Umgebungen anzeigen.

### <a name="outlook-on-windows"></a>Outlook unter Windows

So zeigen Sie Ihre App an, die in Outlook auf Windows Desktop ausgeführt wird:

1. Starten Sie Outlook, und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Klicken Sie auf die Auslassungszeichen (**...**) auf der Seitenleiste. Der Titel Ihrer quergeladenen App wird unter den installierten Apps angezeigt.
1. Klicken Sie auf das App-Symbol, um die App in Outlook zu starten.

:::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste in Outlook-Desktopclients auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="outlook-on-the-web"></a>Outlook im Web

So zeigen Sie Ihre App in Outlook im Web an:

1. Navigieren Sie zu [Outlook im Web](https://outlook.office.com), und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Klicken Sie auf die Auslassungszeichen (**...**) auf der Seitenleiste. Der Titel Ihrer quergeladenen App wird unter den installierten Apps angezeigt.
1. Klicken Sie auf das App-Symbol, um die App zu starten und eine Vorschau davon anzuzeigen, wie sie in Outlook im Web ausgeführt wird.

:::image type="content" source="images/outlook-web-more-apps.png" alt-text="Klicken Sie auf outlook.com auf der Seitenleiste auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-on-windows"></a>Office unter Windows

So zeigen Sie Ihre App an, die in Office auf einem Windows-Desktop ausgeführt wird:

1. Starten Sie Office, und melden Sie sich mit Ihrem Entwickler-Mandantenkonto an.
1. Klicken Sie auf die Auslassungszeichen (**...**) auf der Seitenleiste. Der Titel Ihrer quergeladenen App wird unter den installierten Apps angezeigt.
1. Klicken Sie auf das App-Symbol, um die App in Office zu starten.

:::image type="content" source="images/office-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste in Office-Desktopclients auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

### <a name="office-on-the-web"></a>Office im Web

So zeigen Sie eine Vorschau Ihrer App an, die in Office im Web ausgeführt wird:

1. Melden Sie sich bei office.com mit Testmandantenanmeldeinformationen an.
1. Klicken Sie auf die Auslassungszeichen (**...**) auf der Seitenleiste. Der Titel Ihrer quergeladenen App wird unter den installierten Apps angezeigt.
1. Klicken Sie auf das App-Symbol, um die App in Office im Web zu starten.

:::image type="content" source="images/office-web-more-apps.png" alt-text="Klicken Sie auf office.com auf der Seitenleiste auf die Option &quot;Weitere Apps&quot; (Auslassungspunkte), um Ihre installierten persönlichen Registerkarten anzuzeigen.":::

## <a name="next-steps"></a>Nächste Schritte

Outlook- und Office-fähige persönliche Registerkarten befinden sich in der Vorschau und werden für die Verwendung in der Produktion nicht unterstützt. Hier erfahren Sie, wie Sie Ihre App für persönliche Registerkarten an Vorschau-Benutzergruppen zu Testzwecken verteilen.

### <a name="single-tenant-distribution"></a>Verteilung an einen einzelnen Mandanten

Outlook- und Office-fähige persönliche Registerkarten können auf eine von drei Arten über einen Testmandanten (oder Produktionsmandanten) an eine Vorschau-Benutzergruppe verteilt werden:

#### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü *Apps* die Option *Ihre Apps verwalten* > **Eine App an Ihre Organisation übermitteln** aus. Dies erfordert die Genehmigung Ihres IT-Administrators.

#### <a name="microsoft-teams-admin-center"></a>‎Microsoft Teams Admin Center

Als Microsoft Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation über den [Microsoft Teams-Administrator](https://admin.teams.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden Sie unter [Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

#### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket über den [Microsoft-Administrator](https://admin.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden Sie unter [Testen und Bereitstellen von Microsoft 365 Apps durch Partner im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

### <a name="multitenant-distribution"></a>Verteilung an mehrere Mandanten

Die Verteilung an Microsoft AppSource wird während dieser frühen Entwicklervorschauversion von Outlook- und Office-fähigen persönlichen Microsoft Teams-Registerkarten nicht unterstützt.
