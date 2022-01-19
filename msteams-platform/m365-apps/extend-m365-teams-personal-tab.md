---
title: Erweitern einer Teams persönlichen Registerkarten-App über Microsoft 365
description: Erweitern einer Teams persönlichen Registerkarten-App über Microsoft 365
ms.date: 11/15/2021
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 27d690ca72ffe41fdcdfe39fcd5d7c203c9b3e7c
ms.sourcegitcommit: c65a868744e4108b5d786de2350981e3f1f05718
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2022
ms.locfileid: "62081076"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Erweitern einer Teams persönlichen Registerkarte über Microsoft 365

> [!NOTE]
> *Das Erweitern einer Teams persönlichen Registerkarte über Microsoft 365* ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md)verfügbar. Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Persönliche Registerkarten bieten eine hervorragende Möglichkeit, um die Microsoft Teams Erfahrung zu verbessern. Mit persönlichen Registerkarten können Sie einem Benutzer direkt innerhalb Teams Zugriff auf seine Anwendung gewähren, ohne dass der Benutzer die Benutzeroberfläche verlassen oder sich erneut anmelden muss. Mit dieser Vorschau können persönliche Registerkarten in anderen Microsoft 365-Anwendungen angezeigt werden. In diesem Lernprogramm wird gezeigt, wie Sie eine vorhandene Teams persönliche Registerkarte verwenden und aktualisieren, damit sie sowohl in Outlook Desktop- und Webumgebungen als auch Office im Web (office.com) ausgeführt wird.

Das Aktualisieren Ihrer persönlichen App für die Ausführung in Outlook und Office Home umfasst die folgenden Schritte:

> [!div class="checklist"]
> * Aktualisieren des App-Manifests
> * Aktualisieren Ihrer TeamsJS SDK-Referenzen 
> * Ändern der Kopfzeilen der Inhaltssicherheitsrichtlinie
> * Aktualisieren der AAD-App-Registrierung für einmaliges Anmelden (Single Sign On, SSO)

Zum Testen Ihrer App sind die folgenden Schritte erforderlich:

> [!div class="checklist"]
> * Registrieren Ihres M365-Mandanten in *Office 365 gezielten Versionen*
> * Konfigurieren Ihres Kontos für den Zugriff auf Vorschauversionen von Outlook- und Office-Apps
> * Querladen Der aktualisierten App in Teams

Nach diesen Schritten sollte Ihre App in den Vorschauversionen von Outlook und Office-Apps angezeigt werden.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieses Lernprogramms benötigen Sie Folgendes:

* Ein Sandkastenmandant des Microsoft 365-Entwicklerprogramms
* Ihr Sandkastenmandant, der in *Office 365 Targeted Releases* registriert ist
* Ein Computer mit Office Apps, die über den Microsoft 365 Apps *Betakanal* installiert sind
* (Optional) [Teams Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Visual Studio Code zur Aktualisierung des Codes

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Vorbereiten Ihrer persönlichen Registerkarte für das Upgrade

Wenn Sie über eine vorhandene persönliche Registerkarten-App verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Produktionsprojekts zum Testen, und aktualisieren Sie Ihre App-ID im App-Manifest, um einen neuen Bezeichner zu verwenden (der sich von der Produktions-App-ID unterscheidet).

Wenn Sie beispielcode verwenden möchten, um dieses Lernprogramm abzuschließen, führen Sie die Setupschritte in ["Erste Schritte mit Todo-Listenbeispiel" aus,](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) um eine persönliche Registerkarten-App mithilfe der Teams Toolkit-Erweiterung für Visual Studio Code zu erstellen. Sie können auch mit dem gleichen [Todo-Listenbeispiel](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend-M365) beginnen, das für TeamsJS SDK v2 Preview aktualisiert wurde, und mit [der Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Umgebungen](#preview-your-personal-tab-in-other-microsoft-365-experiences)fortfahren. Das aktualisierte Beispiel ist auch in Teams Toolkit-Erweiterung verfügbar:  >  Todo-Liste mit *Entwicklungsansichtsbeispielen*  >  **(funktioniert in Teams, Outlook und Office).**

:::image type="content" source="images/toolkit-todo-sample.png" alt-text="Todo List-Beispiel (Funktioniert in Teams, Outlook und Office) in Teams Toolkit":::


## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen das [Teams Entwicklervorschau-Manifestschema](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) und die `m365DevPreview` Manifestversion verwenden, damit Ihre Teams persönliche Registerkarte in Office und Outlook ausgeführt werden kann.

Sie können entweder Teams Toolkit verwenden, um Ihr App-Manifest zu aktualisieren, oder die Änderungen manuell anwenden:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die *Befehlspalette:*`Ctrl+Shift+P`
1. Führen Sie den `Teams: Upgrade Teams manifest to support Outlook and Office apps` Befehl aus, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden vorgenommen.

# <a name="manual-steps"></a>[Manuelle Schritte](#tab/manifest-manual)

Öffnen Sie Ihr Teams-App-Manifest, und aktualisieren Sie das `$schema` und mit den folgenden `manifestVersion` Werten:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```
---

Wenn Sie Teams Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie sie auch verwenden, um die Änderungen an Ihrer Manifestdatei zu überprüfen und Fehler zu identifizieren. Öffnen Sie die Befehlspalette, und suchen Sie nach Teams: Überprüfen sie `Ctrl+Shift+P` die **Manifestdatei,** oder wählen Sie die Option im Bereitstellungsmenü des Teams Toolkits aus (suchen Sie auf der linken Seite von Visual Studio Code nach dem Symbol Teams).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Option &quot;Manifestdatei überprüfen&quot; im Teams Toolkit im Menü &quot;Bereitstellung&quot;":::

## <a name="update-sdk-references"></a>Aktualisieren von SDK-Verweisen

Um in Outlook und Office ausgeführt zu werden, muss Ihre App vom npm-Paket `@microsoft/teams-js@2.0.0-beta.1` (oder einer späteren *Betaversion)* abhängig sein. Während Code mit Vorgängerversionen von `@microsoft/teams-js` in Outlook und Office unterstützt wird, werden veraltete Warnungen protokolliert, und die Unterstützung für Vorgängerversionen von in Outlook und Office wird schließlich `@microsoft/teams-js` eingestellt.

Sie können Teams Toolkit verwenden, um einige der Codeänderungen zu automatisieren, um die nächste Version von zu `@microsoft/teams-js` übernehmen. Wenn Sie die Schritte jedoch manuell ausführen möchten, finden Sie weitere Informationen [in Microsoft Teams JavaScript-Client-SDK-Vorschau.](using-teams-client-sdk-preview.md)

1. Öffnen Sie die *Befehlspalette:*`Ctrl+Shift+P`
1. Ausführen des Befehls `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`

Nach Abschluss des Vorgangs hat das Hilfsprogramm Ihre `package.json` Datei mit der Abhängigkeit von TeamsJS SDK Preview `@microsoft/teams-js@2.0.0-beta.1` (oder höher) aktualisiert, und Ihre `*.js/.ts` `*.jsx/.tsx` Und-Dateien werden mit Folgendem aktualisiert:

> [!div class="checklist"]
> * `package.json` Verweise auf TeamsJS SDK Preview
> * Importanweisungen für TeamsJS SDK Preview
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](using-teams-client-sdk-preview.md#apis-organized-into-capabilities) von TeamsJS SDK Preview
> * `TODO` Kommentarerinnerungen zum Überprüfen von Bereichen, die möglicherweise von Änderungen der [Kontextschnittstelle](using-teams-client-sdk-preview.md#updates-to-the-context-interface) betroffen sind
> * `TODO` Kommentarerinnerungen, um sicherzustellen, dass die [Konvertierung in Zusagenfunktionen aus Rückrufstilfunktionen](using-teams-client-sdk-preview.md#callbacks-converted-to-promises) auf jeder Aufrufwebsite, die das Tool gefunden hat, gut funktioniert hat

> [!IMPORTANT]
> Code in *.html* Dateien wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

> [!NOTE]
> Wenn Sie Ihren Code manuell aktualisieren möchten, lesen Sie [Microsoft Teams JavaScript-Client-SDK-Vorschau,](using-teams-client-sdk-preview.md) um mehr über die erforderlichen Änderungen zu erfahren.

## <a name="configure-content-security-policy-headers"></a>Konfigurieren von Kopfzeilen für Inhaltssicherheitsrichtlinien

[Wie in Microsoft Teams](/microsoftteams/platform/tabs/what-are-tabs)werden Registerkartenanwendungen in ([iframe-Elementen](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)) in Office und Outlook Webclients gehostet.

Wenn Ihre App [CSP-Header (Content Security Policy)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) verwendet, stellen Sie sicher, dass Sie alle folgenden [Frame-Vorgänger](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) in Ihren CSP-Headern zulassen:

|Microsoft 365 Host| Frame-Vorgängerberechtigung|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com` |

## <a name="update-aad-app-registration-for-sso"></a>Aktualisieren AAD App-Registrierung für SSO

Azure Active Directory Einmaliges Anmelden (Single Sign On, SSO) für persönliche Registerkarten funktioniert in Office und Outlook auf die gleiche Weise [wie in Teams.](/microsoftteams/platform/tabs/how-to/authentication/auth-aad-sso)Sie müssen jedoch der AAD App-Registrierung Ihrer Registerkarten-App im *App-Registrierungsportal* Ihres Mandanten mehrere Clientanwendungs-IDs hinzufügen.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto beim [Azure-Portal](https://portal.azure.com) an.
1. Öffnen Sie das Blatt **"App-Registrierungen".**
1. Wählen Sie den Namen Ihrer persönlichen Registerkartenanwendung aus, um die App-Registrierung zu öffnen. 
1. Wählen Sie  **"API verfügbar machen"** (unter *"Verwalten")* aus.

:::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorisieren von Client-IDs über das Blatt &quot;*App-Registrierungen*&quot; im Azure-Portal":::

Stellen Sie im Abschnitt **"Autorisierte Clientanwendungen"** sicher, dass alle folgenden `Client Id` Werte hinzugefügt werden:

|Microsoft 365 Clientanwendung | Client-ID |
|--|--|
|Teams Desktop, Mobil |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Teams Web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Office.com  |4345a7b9-9a63-4910-a426-35363201d503|
|Office.com  |4765445b-32c6-49b0-83e6-1d93765276ca|
|Office Desktop  | 0ec893e0-5785-4de6-99da-4ed124e5296c |
|Outlook Desktop | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-app-in-teams"></a>Querladen der App in Microsoft Teams

Der letzte Schritt besteht darin, ihre aktualisierte persönliche Registerkarte[(App-Paket)](/microsoftteams/platform/concepts/build-and-test/apps-package)in Microsoft Teams querzuladen. Nach Abschluss des Vorgangs kann Ihre App zusätzlich zu Teams auch in Office und Outlook ausgeführt werden.

1. Verpacken Sie Ihre Teams Anwendung (Manifest- und [App-Symbole)](/microsoftteams/platform/resources/schema/manifest-schema#icons)in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der **Option zip Teams Metadatenpaket** im *Bereitstellungsmenü* von Teams Toolkit oder in der Befehlspalette `Ctrl+Shift+P` von Visual Studio Code tun:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option &quot;Zip Teams Metadata Package&quot; in Teams Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Teams an, und stellen Sie sicher, dass Sie sich in der Public Developer Preview befinden. Sie können überprüfen, ob Sie sich auf der Vorschau im Teams-Client befinden, indem Sie auf das Menü mit den Auslassungspunkten (**...**) ihres Benutzerprofils klicken und **"Info"** öffnen, um zu überprüfen, ob die Option *"Entwicklervorschau"* aktiviert ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie im Menü Teams Ellipsen &quot;Info&quot;, und überprüfen Sie, ob die Option &quot;Entwicklervorschau&quot; aktiviert ist.":::

1. Öffnen Sie den *Bereich "Apps",* und klicken Sie auf **Hochladen einer benutzerdefinierten App,** und **Hochladen Sie dann für mich oder meine Teams.**

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Schaltfläche &quot;Hochladen einer benutzerdefinierten App&quot; im Bereich Teams &quot;Apps&quot;":::

1. Wählen Sie Ihr App-Paket aus, und klicken Sie auf *"Öffnen".*

Nach dem Querladen über Teams ist Ihre persönliche Registerkarte in Outlook und Office verfügbar. Melden Sie sich unbedingt mit denselben Anmeldeinformationen an, die Sie zum Querladen Ihrer App in Teams verwendet haben.

Sie können die App für den Schnellzugriff anheften, oder Sie finden Ihre App in den Ellipsen (**...**) flyout zwischen den zuletzt verwendeten Anwendungen in der Randleiste auf der linken Seite.

> [!NOTE]
> Wenn Sie eine App in Teams anheften, wird sie nicht als App in Office.com oder Outlook angeheftet.

## <a name="preview-your-personal-tab-in-other-microsoft-365-experiences"></a>Anzeigen einer Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365-Umgebungen

Wenn Sie Ihre Teams persönliche Registerkarte aktualisieren und in Teams querladen, wird sie auch in Outlook Desktop- und Webclients und Office im Web (office.com) ausgeführt. Hier erfahren Sie, wie Sie eine Vorschau dieser Microsoft 365-Umgebungen anzeigen.

### <a name="outlook"></a>Outlook

Um Ihre App anzuzeigen, die in Outlook auf Windows Desktop ausgeführt wird, starten Sie Outlook und melden Sie sich mit Ihrem Dev-Mandantenkonto an. Klicken Sie auf die Auslassungspunkte (**...**) auf der Seitenleiste. Der Titel der quergeladenen App wird unter den installierten Apps angezeigt.

:::image type="content" source="images/outlook-desktop-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste Office Desktopclients auf die Option &quot;Weitere Apps&quot;, um die installierten persönlichen Registerkarten anzuzeigen.":::

Klicken Sie auf das App-Symbol, um Ihre App in Outlook zu starten.

### <a name="outlook-on-the-web"></a>Outlook im Web

Um Ihre App in Outlook im Web anzuzeigen, besuchen https://outlook.office.com Sie Ihr Dev-Mandantenkonto, und melden Sie sich an. Klicken Sie auf die Auslassungspunkte (**...**) auf der Seitenleiste. Der Titel der quergeladenen App wird unter den installierten Apps angezeigt.

:::image type="content" source="images/outlook-web-more-apps.png" alt-text="Klicken Sie auf der Seitenleiste von outlook.com auf die Option &quot;Weitere Apps&quot;, um die installierten persönlichen Registerkarten anzuzeigen.":::

Klicken Sie auf das App-Symbol, um die App in Outlook im Web zu starten und eine Vorschau anzuzeigen.

### <a name="office-on-the-web"></a>Office im Web

> [!IMPORTANT]
> Lesen Sie die neuesten Updates auf [Microsoft Teams – Microsoft 365 Entwicklerblog,](https://devblogs.microsoft.com/microsoft365dev/) um zu überprüfen, ob Office.com-Unterstützung für Teams persönliche Apps für Ihren Testmandanten verfügbar ist.

Melden Sie sich mit testmandantenanmeldeinformationen bei office.com an, um eine Vorschau Ihrer app ausgeführt in Office im Web ausgeführt. Klicken Sie auf die Auslassungspunkte (**...**) auf der Seitenleiste. Der Titel der quergeladenen App wird unter den installierten Apps angezeigt.

Klicken Sie auf das App-Symbol, um Ihre App in Office Start zu starten.

## <a name="next-steps"></a>Nächste Schritte

Outlook- und Office-aktivierte persönliche Registerkarten befinden sich in der Vorschau und werden für die Produktionsverwendung nicht unterstützt. Hier erfahren Sie, wie Sie Ihre persönliche Registerkarten-App zu Testzwecken in der Vorschau anzeigen.

### <a name="single-tenant-distribution"></a>Einzelmandantenverteilung

Outlook- und Office-aktivierte persönliche Registerkarten können auf drei Arten an eine Vorschaugruppe über einen Testmandanten (oder Produktionsmandanten) verteilt werden:

#### <a name="teams-client"></a>Teams Client

Wählen Sie im Menü *"Apps"* die Option *"Apps verwalten"* aus,  >  **um eine App an Ihre Organisation zu übermitteln.** Dies erfordert die Genehmigung durch Ihren IT-Administrator.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation hochladen und vorab https://admin.teams.microsoft.com/ installieren. Weitere Informationen finden Sie [unter Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center.](/MicrosoftTeams/upload-custom-apps)

#### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket hochladen und vorab https://admin.microsoft.com/ installieren. Weitere Informationen finden Sie unter Testen und Bereitstellen von Microsoft 365 Apps von Partnern im Portal für [integrierte Apps.](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps)

### <a name="multi-tenant-distribution"></a>Mehrinstanzenfähige Verteilung

Die Verteilung an Microsoft AppSource wird während dieser frühen Entwicklervorschau von Outlook- und Office-aktivierten Teams persönlichen Registerkarten nicht unterstützt.
