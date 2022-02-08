---
title: Erweitern einer Teams persönlichen Registerkarten-App über Microsoft 365
description: Erweitern einer Teams persönlichen Registerkarten-App über Microsoft 365
ms.date: 11/15/2021
ms.topic: tutorial
ms.custom: Microsoft 365 apps
ms.localizationpriority: medium
ms.openlocfilehash: 529dd82276f4e11dc6256d23b6e8eb622a1651a0
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435272"
---
# <a name="extend-a-teams-personal-tab-across-microsoft-365"></a>Erweitern einer Teams persönlichen Registerkarte über Microsoft 365

> [!NOTE]
> *Das Erweitern einer Teams persönlichen Registerkarte über Microsoft 365* ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar. Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Persönliche Registerkarten bieten eine hervorragende Möglichkeit, die Microsoft Teams Zu verbessern. Mit persönlichen Registerkarten können Sie einem Benutzer direkt innerhalb Teams Zugriff auf seine Anwendung gewähren, ohne dass der Benutzer die Benutzeroberfläche verlassen oder sich erneut anmelden muss. Mit dieser Vorschau können persönliche Registerkarten in anderen Microsoft 365-Anwendungen angezeigt werden. In diesem Lernprogramm wird gezeigt, wie Sie eine vorhandene Teams persönliche Registerkarte verwenden und aktualisieren, damit sie sowohl in Outlook Desktop- und Webumgebungen als auch Office im Web (office.com) ausgeführt wird.

Das Aktualisieren Ihrer persönlichen App für die Ausführung in Outlook und Office Home umfasst die folgenden Schritte:

> [!div class="checklist"]
> * Aktualisieren des App-Manifests
> * Aktualisieren Ihrer TeamsJS SDK-Referenzen 
> * Ändern der Kopfzeilen der Inhaltssicherheitsrichtlinie
> * Aktualisieren der Azure AD-App-Registrierung für einmaliges Anmelden (Single Sign On, SSO)

Zum Testen Ihrer App sind die folgenden Schritte erforderlich:

> [!div class="checklist"]
> * Registrieren Ihres Microsoft 365 Mandanten in *Office 365 gezielten Versionen*
> * Konfigurieren Ihres Kontos für den Zugriff auf Vorschauversionen von Outlook- und Office-Apps
> * Querladen Ihrer aktualisierten App in Teams

Nach diesen Schritten sollte Ihre App in den Vorschauversionen von Outlook- und Office-Apps angezeigt werden.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieses Lernprogramms benötigen Sie Folgendes:

* Ein Sandkastenmandant des Microsoft 365-Entwicklerprogramms
* Ihr Sandkastenmandant, der in *Office 365 Targeted Releases registriert ist*
* Ein Computer mit Office Apps, die über den Microsoft 365 Apps *Betakanal* installiert sind
* (Optional) [Teams Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Microsoft Visual Studio Code, um Ihren Code zu aktualisieren

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-personal-tab-for-the-upgrade"></a>Vorbereiten Ihrer persönlichen Registerkarte für das Upgrade

Wenn Sie über eine vorhandene persönliche Registerkarten-App verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Produktionsprojekts zum Testen, und aktualisieren Sie Ihre App-ID im App-Manifest, um einen neuen Bezeichner zu verwenden (der sich von der Produktions-App-ID unterscheidet).

Wenn Sie Beispielcode zum Abschließen dieses Lernprogramms verwenden möchten, führen Sie die Setupschritte im Beispiel für erste [Schritte mit Todo-Listen aus,](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend) um eine persönliche Registerkarten-App mithilfe der Teams Toolkit-Erweiterung für Visual Studio Code zu erstellen. Sie können auch mit dem gleichen [Todo-Listenbeispiel beginnen, das für TeamsJS SDK v2 Preview aktualisiert wurde](https://github.com/OfficeDev/TeamsFx-Samples/tree/main/todo-list-with-Azure-backend-M365), und mit [der Vorschau Ihrer persönlichen Registerkarte in anderen Microsoft 365 fortfahren](#preview-your-personal-tab-in-other-microsoft-365-experiences). Das aktualisierte Beispiel ist auch in Teams Toolkit-Erweiterung verfügbar: *DevelopmentView* >  **samplesTodo List (Funktioniert in Teams, Outlook und Office)**. > 

:::image type="content" source="images/toolkit-todo-sample.png" alt-text="Todo List-Beispiel (Funktioniert in Teams, Outlook und Office) in Teams Toolkit":::


## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen das [Teams Entwicklervorschau-Manifestschema](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) und die `Microsoft 365 DevPreview` Manifestversion verwenden, damit Ihre Teams persönliche Registerkarte in Office und Outlook ausgeführt werden kann.

Sie können entweder Teams Toolkit verwenden, um Ihr App-Manifest zu aktualisieren, oder die Änderungen manuell anwenden:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen Sie den Befehl aus `Teams: Upgrade Teams manifest to support Outlook and Office apps` , und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden vorgenommen.

# <a name="manual-steps"></a>[Manuelle Schritte](#tab/manifest-manual)

Öffnen Sie Ihr Teams-App-Manifest, und aktualisieren Sie das `$schema` und `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```
---

Wenn Sie Teams Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie sie auch verwenden, um die Änderungen an Ihrer Manifestdatei zu überprüfen und Fehler zu identifizieren. Öffnen Sie die Befehlspalette`Ctrl+Shift+P`, und suchen Sie **nach Teams: Überprüfen der Manifestdatei**, oder wählen Sie die Option im Bereitstellungsmenü des Teams Toolkits aus (suchen Sie auf der linken Seite von Visual Studio Code nach dem Symbol Teams).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Option &quot;Manifestdatei überprüfen&quot; des Teams Toolkits im Menü &quot;Bereitstellung&quot;":::

## <a name="update-sdk-references"></a>Aktualisieren von SDK-Verweisen

Um in Outlook und Office ausgeführt zu werden, muss Ihre App vom npm-Paket `@microsoft/teams-js@2.0.0-beta.1` (oder einer späteren *Betaversion*) abhängig sein. Während code with downlevel versions of `@microsoft/teams-js` is supported in Outlook and Office, deprecation warnings will be logged, and support for downlevel versions of `@microsoft/teams-js` in Outlook and Office will eventually ends.

Sie können Teams Toolkit verwenden, um einige der Codeänderungen zu automatisieren, um die nächste Version von `@microsoft/teams-js`zu übernehmen. Wenn Sie die Schritte jedoch manuell ausführen möchten, finden Sie weitere Informationen [unter Microsoft Teams JavaScript-Client-SDK-Vorschau](using-teams-client-sdk-preview.md).

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Ausführen des Befehls `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`

Nach Abschluss des Vorgangs hat das Hilfsprogramm Ihre `package.json` Datei mit der Abhängigkeit von TeamsJS SDK Preview (`@microsoft/teams-js@2.0.0-beta.1` oder höher) aktualisiert, und Ihre `*.js/.ts` Und-Dateien `*.jsx/.tsx` werden mit Folgendem aktualisiert:

> [!div class="checklist"]
> * `package.json` Verweise auf TeamsJS SDK Preview
> * Importanweisungen für TeamsJS SDK Preview
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](using-teams-client-sdk-preview.md#apis-organized-into-capabilities) von TeamsJS SDK Preview
> * `TODO` Kommentarerinnerungen zum Überprüfen von Bereichen, die möglicherweise von [Änderungen der Kontextschnittstelle](using-teams-client-sdk-preview.md#updates-to-the-context-interface) betroffen sind
> * `TODO` Kommentarerinnerungen, um sicherzustellen, dass die [Konvertierung in Zusagenfunktionen aus Rückrufstilfunktionen](using-teams-client-sdk-preview.md#callbacks-converted-to-promises) auf jeder Aufrufwebsite, die das Tool gefunden hat, gut funktioniert hat

> [!IMPORTANT]
> Code in *.html* Dateien wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

> [!NOTE]
> Wenn Sie Ihren Code manuell aktualisieren möchten, finden Sie [in Microsoft Teams JavaScript-Client-SDK Preview](using-teams-client-sdk-preview.md) Informationen zu den erforderlichen Änderungen.

## <a name="configure-content-security-policy-headers"></a>Konfigurieren von Kopfzeilen für Inhaltssicherheitsrichtlinien

[Wie in Microsoft Teams](/microsoftteams/platform/tabs/what-are-tabs) werden Registerkartenanwendungen in Office und Outlook Webclients gehostet ([iframe-Elemente](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)).

Wenn Ihre App CSP-Header ( [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) ) verwendet, stellen Sie sicher, dass Sie alle folgenden [Frame-Vorgänger](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) in Ihren CSP-Headern zulassen:

|Microsoft 365 Host| Frame-Vorgängerberechtigung|
|--|--|
| Teams | `teams.microsoft.com` |
| Office | `*.office.com` |
| Outlook | `outlook.office.com`, `outlook.office365.com` |

## <a name="update-azure-ad-app-registration-for-sso"></a>Aktualisieren Azure AD App-Registrierung für SSO

Azure Active Directory Einmaliges Anmelden (Single Sign On, SSO) für persönliche Registerkarten funktioniert in Office und Outlook auf die gleiche Weise [wie in Teams](/microsoftteams/platform/tabs/how-to/authentication/auth-aad-sso). Sie müssen jedoch der Azure AD App-Registrierung Ihrer Registerkarten-App im *App-Registrierungsportal* Ihres Mandanten mehrere Clientanwendungs-IDs hinzufügen.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei [Microsoft Azure Portal](https://portal.azure.com) an.
1. Öffnen Sie das Blatt " **App-Registrierungen** ".
1. Wählen Sie den Namen Ihrer persönlichen Registerkartenanwendung aus, um die App-Registrierung zu öffnen. 
1. Wählen Sie  **"API verfügbar machen** " (unter *"Verwalten*") aus.

:::image type="content" source="images/azure-app-registration-clients.png" alt-text="Autorisieren von Client-IDs aus dem Blatt &quot;*App-Registrierungen*&quot; im Microsoft Azure Portal":::

Stellen Sie im Abschnitt **"Autorisierte Clientanwendungen** " sicher, dass alle folgenden `Client Id` Werte hinzugefügt werden:

|Microsoft 365-Clientanwendung | Client-ID |
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

Der letzte Schritt besteht darin, ihre aktualisierte persönliche Registerkarte ([App-Paket](/microsoftteams/platform/concepts/build-and-test/apps-package)) in Microsoft Teams querzuladen. Nach Abschluss des Vorgangs kann Ihre App zusätzlich zu Teams in Office und Outlook ausgeführt werden.

1. Verpacken Sie Ihre Teams Anwendung (Manifest[- und App-Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mit der Option **zip Teams Metadatenpaket** im *Bereitstellungsmenü* von Teams Toolkit oder in der Befehlspalette `Ctrl+Shift+P` von Visual Studio Code tun:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option &quot;Zip-Teams-Metadatenpaket&quot; in Teams Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Teams an, und stellen Sie sicher, dass Sie sich in der Öffentlichen Entwicklervorschau befinden. Sie können überprüfen, ob Sie sich auf der Vorschau im Teams-Client befinden, indem Sie auf das Menü mit den Auslassungspunkten (**...**) ihres Benutzerprofils klicken und "**Info**" öffnen, um zu überprüfen, ob die *Option "Entwicklervorschau*" aktiviert ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie im Menü Teams Ellipsen &quot;Info&quot;, und überprüfen Sie, ob die Option &quot;Entwicklervorschau&quot; aktiviert ist.":::

1. Öffnen Sie den *Bereich "Apps*", und klicken Sie auf **Hochladen einer benutzerdefinierten App**, und **Hochladen Sie dann für mich oder meine Teams**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Schaltfläche &quot;Hochladen einer benutzerdefinierten App&quot; im Bereich Teams &quot;Apps&quot;":::

1. Wählen Sie Ihr App-Paket aus, und klicken Sie auf *"Öffnen*".

Nach dem Querladen über Teams ist Ihre persönliche Registerkarte in Outlook und Office verfügbar. Melden Sie sich unbedingt mit denselben Anmeldeinformationen an, die Sie zum Querladen Ihrer App in Teams verwendet haben.

Sie können die App für den Schnellzugriff anheften, oder Sie finden Ihre App im Ellipsen-Flyout (**...**) unter den zuletzt verwendeten Anwendungen in der Randleiste auf der linken Seite.

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
> Lesen Sie die neuesten Updates auf [Microsoft Teams – Microsoft 365 Entwicklerblog](https://devblogs.microsoft.com/microsoft365dev/), um zu überprüfen, ob Office.com-Unterstützung für Teams persönliche Apps für Ihren Testmandanten verfügbar ist.

Melden Sie sich bei office.com mit Testmandantenanmeldeinformationen an, um eine Vorschau Ihrer app ausgeführt in Office im Web ausgeführt. Klicken Sie auf die Auslassungspunkte (**...**) auf der Seitenleiste. Der Titel der quergeladenen App wird unter den installierten Apps angezeigt.

Klicken Sie auf das App-Symbol, um Ihre App in Office Startseite zu starten.

## <a name="next-steps"></a>Nächste Schritte

Outlook- und Office-aktivierte persönliche Registerkarten befinden sich in der Vorschau und werden für die Produktionsverwendung nicht unterstützt. Hier erfahren Sie, wie Sie Ihre persönliche Registerkarten-App zu Testzwecken in der Vorschau anzeigen.

### <a name="single-tenant-distribution"></a>Einzelmandantenverteilung

Outlook- und Office-aktivierte persönliche Registerkarten können auf eine der folgenden drei Arten an eine Vorschaugruppe über einen Testmandanten (oder Produktionsmandanten) verteilt werden:

#### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü *"Apps*" die Option *"Apps verwaltenSubmit* >  **einer App an Ihre Organisation**" aus. Dies erfordert die Genehmigung durch Ihren IT-Administrator.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation hochladen https://admin.teams.microsoft.com/und vorab installieren. Weitere Informationen finden Sie [unter Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

#### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket hochladen und vorab installieren.https://admin.microsoft.com/ Weitere Informationen finden Sie [unter Testen und Bereitstellen von Microsoft 365 Apps von Partnern im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

### <a name="multi-tenant-distribution"></a>Mehrinstanzenfähige Verteilung

Die Verteilung an Microsoft AppSource wird während dieser frühen Entwicklervorschau von Outlook- und Office-aktivierten Teams persönlichen Registerkarten nicht unterstützt.
