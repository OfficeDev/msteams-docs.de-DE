---
title: Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365
description: In diesem Artikel erfahren Sie, wie Sie die suchbasierte Teams-Nachrichtenerweiterung für die Ausführung in Outlook aktualisieren, indem Sie das Anwendungsmanifest aktualisieren, einen Outlook-Kanal hinzufügen und die aktualisierte Anwendung per Sideloading installieren.
ms.date: 05/24/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 790c6324f012da8aabe7c4489a414d9887e03640
ms.sourcegitcommit: 4ba6392eced76ba6baeb6d6dd9ba426ebf4ab24f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2022
ms.locfileid: "66919732"
---
# <a name="extend-a-teams-message-extension-across-microsoft-365"></a>Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365

Suchbasierte [Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ermöglichen es Benutzern, ein externes System zu durchsuchen und die Ergebnisse über den Bereich des Microsoft Teams-Clients zum Verfassen von Nachrichten freizugeben. Durch das [Erweitern Ihrer Microsoft Teams-Apps in Microsoft 365 (Vorschau)](overview.md) können Sie jetzt Ihre suchbasierten Microsoft Teams-Nachrichtenerweiterungen in der Produktion in Outlook für Desktop und Web in der Vorschau einbinden.

Der Prozess zum Aktualisieren Ihrer suchbasierten Teams-Nachrichtenerweiterung zum Ausführen in Outlook umfasst die folgenden Schritte:

> [!div class="checklist"]
>
> * Aktualisieren Sie Ihr App-Manifest.
> * Fügen Sie einen Outlook-Kanal für Ihren Bot hinzu.
> * Laden Sie Ihre aktualisierte App in Teams quer.

Der Rest dieses Leitfadens führt Sie durch diese Schritte und zeigt Ihnen, wie Sie Ihre Nachrichtenerweiterung in Outlook für Windows Desktop und auf outlook.com in der Vorschau anzeigen können.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Lernprogramm benötigen Sie Folgendes:

* Einen Sandkastenmandanten für das Microsoft 365-Entwicklerprogramm.
* Registrierung in *Office 365 Targeted Releases* für Ihren Sandbox-Mandanten.
* Eine Testumgebung mit installierten Office-Anwendungen aus dem Microsoft 365 Apps-*Betakanal*.
* (Optional) Microsoft Visual Studio Code mit der Teams Toolkit-Erweiterung.

> [!div class="nextstepaction"]
> [Veröffentlichen von Microsoft Teams-Apps, die für Microsoft 365 erweitert wurden](publish.md)

## <a name="prepare-your-message-extension-for-the-upgrade"></a>Vorbereiten Ihrer Nachrichtenerweiterung für das Upgrade

Wenn Sie über eine vorhandene Nachrichtenerweiterung in der Produktion verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Projekts zum Testen, und aktualisieren Ihre App-ID im App-Manifest, um einen neuen Bezeichner (unterschiedlich von der Produktions-App-ID, für Testzwecke) zu verwenden.

Wenn Sie dieses Lernprogramm zum Aktualisieren einer vorhandenen Microsoft Teams-App mithilfe von Beispielcode absolvieren möchten, führen Sie die Setupschritte unter [Suchbeispiel für Microsoft Teams-Nachrichtenerweiterungen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) aus, um schnell eine suchbasierte Microsoft Teams-Nachrichtenerweiterung zu erstellen.

Alternativ können Sie die fertige Outlook-fähige App im folgenden Abschnitt verwenden und den Teil dieses Lernprogramms zum [*Aktualisieren des App-Manifests*](#update-the-app-manifest) überspringen.

### <a name="quickstart"></a>Schnellstart

Verwenden Sie die Microsoft Teams Toolkit-Erweiterung für Visual Studio Code, um mit einer [Beispielnachrichtenerweiterung](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/NPM-search-connector-M365) zu beginnen, die bereits für die Ausführung in Outlook aktiviert ist.

1. Öffnen Sie in Visual Studio Code die Befehlspalette (`Ctrl+Shift+P`), geben Sie `Teams: Create a new Teams app` ein.
1. Wählen Sie die Option **Neue Microsoft Teams-App erstellen** aus.
1. Wählen Sie **Suchbasierte Nachrichtenerweiterung** aus, um Beispielcode für eine Microsoft Teams Nachrichtenerweiterung mit dem neuesten Microsoft Teams-App-Manifest (Version`1.13`) herunterzuladen.

    :::image type="content" source="images/toolkit-palatte-search-sample.png" alt-text="VS Code Befehlspalette zur Eingabe von &quot;Neue Microsoft Teams-App erstellen&quot;, um Microsoft Teams-Beispieloptionen aufzulisten":::

    Das Beispiel ist auch als *NPM-Suchconnector* im Microsoft Teams Toolkit-Beispielkatalog verfügbar. Wählen Sie im Microsoft Teams Toolkit-Bereich die Option *Entwicklung* > *Beispiele anzeigen* >  **NPM-Suchconnector** aus.

    :::image type="content" source="images/toolkit-search-sample.png" alt-text="NPM-Suchconnector-Beispiel im Microsoft Teams Toolkit-Beispielkatalog":::

1. Wählen Sie einen Speicherort auf Ihrem lokalen Computer für den Arbeitsbereichsordner aus.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben Sie `Teams: Provision in the cloud` ein, um die erforderlichen App-Ressourcen (Azure App Service, App Service Plan, Azure Bot und verwaltete Identität) in Ihrem Azure-Konto zu erstellen.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben Sie `Teams: Deploy to the cloud` ein, um den Beispielcode für die bereitgestellten Ressourcen in Azure einzusetzen und die App zu starten.

Von hier aus können Sie mit dem [Hinzufügen eines Outlook Kanals für Ihren Bot](#add-an-outlook-channel-for-your-bot) fortfahren, um den letzten Schritt zur Aktivierung der Microsoft Teams-Nachrichtenerweiterung in Outlook auszuführen. (Das App-Manifest verweist bereits auf die richtige Version, daher sind keine Aktualisierungen erforderlich.)

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen die Schemaversion `1.13` des [Microsoft Teams-Entwicklermanifests](../resources/schema/manifest-schema.md) verwenden, damit Ihre Microsoft Teams-Nachrichtenerweiterung in Outlook ausgeführt werden kann.

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

Wenn Sie das Microsoft Teams Toolkit zum Erstellen Ihrer Nachrichtenerweiterungs-App verwendet haben, können Sie damit die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette `Ctrl+Shift+P` und suchen Sie **Teams: Manifestdatei validieren** (Teams: Validate manifest file).

## <a name="add-an-outlook-channel-for-your-bot"></a>Hinzufügen eines Outlook-Kanals für Ihren Bot

In Microsoft Teams besteht eine Nachrichtenerweiterung aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, wo Ihr Webdienst gehostet wird. Der Webdienst nutzt das [Bot Framework SDK](/azure/bot-service/bot-service-overview)-Nachrichtenschema und das sichere Kommunikationsprotokoll über einen Teams-Kanal, der für Ihren Bot registriert ist.

Damit Benutzer von Outlook aus mit Ihrer Nachrichtenerweiterung interagieren können, müssen Sie Ihrem Bot einen Outlook-Kanal hinzufügen:

1. Navigieren Sie aus dem [Microsoft Azure-Portal](https://portal.azure.com) (oder [Bot Framework-Portal](https://dev.botframework.com), wenn Sie sich zuvor dort registriert haben) zu Ihrer Bot-Ressource.

1. Wählen Sie unter *Einstellungen* die Option **Kanäle**.

1. Wählen Sie unter *Verfügbare Kanäle* die Option **Outlook** aus. Wählen Sie die Registerkarte **Nachrichtenerweiterungen** und dann **Anwenden** aus.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Hinzufügen eines Outlook-Kanals „Nachrichtenerweiterungen“ für Ihren Bot aus dem Bereich „Azure Bot Channels“":::

1. Vergewissern Sie sich, dass Ihr Outlook-Kanal zusammen mit Teams im Bereich **Kanäle** Ihres Bots aufgeführt ist.

    :::image type="content" source="images/azure-bot-channels.png" alt-text="Bereich „Azure Bot-Kanäle“, in dem sowohl Teams als auch Outlook-Kanäle aufgeführt sind":::

## <a name="update-microsoft-azure-active-directory-azure-ad-app-registration-for-sso"></a>Aktualisieren der Microsoft Azure Active Directory (Azure AD)-App-Registrierung für SSO

> [!NOTE]
> Sie können den Schritt überspringen, wenn Sie die in diesem Lernprogramm bereitgestellte [Beispiel-App](#quickstart) verwenden, da das Szenario keine Azure Active Directory (AAD) Single Sign-On-Authentifizierung umfasst.

Azure Active Directory (AD) Single Sign-On (SSO) für Nachrichtenerweiterungen funktioniert in Outlook genauso [wie in Microsoft Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots). Sie müssen jedoch der Azure AD-App-Registrierung Ihres Bots im *App-Registrierungsportal* Ihres Mandanten mehrere Clientanwendungsbezeichner hinzufügen.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto beim [Azure-Portal](https://portal.azure.com) an.
1. Öffnen Sie **App-Registrierungen**.
1. Wählen Sie den Namen Ihrer Anwendung aus, um die entsprechende App-Registrierung zu öffnen.
1. Wählen Sie die Option **Eine API verfügbar machen** aus (unter *Verwalten*).
1. Stellen Sie im Abschnitt **Autorisierte Clientanwendungen** sicher, dass alle folgenden `Client Id` Werte aufgeführt sind:

   |Microsoft 365-Clientanwendung | Client-ID |
   |--|--|
   |Teams-Desktop und mobiles Gerät |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
   |Teams-Web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
   |Outlook Desktop | d3590ed6-52b3-4102-aeff-aad2292ab01c |
   |Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
   |Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-updated-message-extension-in-teams"></a>Querladen Ihrer aktualisierten Nachrichtenerweiterung in Teams

Der letzte Schritt besteht darin, die aktualisierte Nachrichtenerweiterung ([App-Paket](/microsoftteams/platform/concepts/build-and-test/apps-package)) in Teams querzuladen. Nach Abschluss wird Ihre Nachrichtenerweiterung in den installierten *Apps* aus dem Bereich zum Verfassen von Nachrichten angezeigt.

1. Verpacken Sie Ihre Teams-Anwendung (Manifest- und App-[Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der Option **Teams-Metadatenpaket in einer ZIP-Datei verpacken** im Menü *Bereitstellung* von Teams Toolkit tun.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option „ Microsoft Teams-Metadatenpaket in einer ZIP-Datei verpacken“ in der Microsoft Teams-Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Microsoft Teams an, und wechseln Sie in den *Entwicklervorschaumodus*. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil Folgendes aus: **Info** > **Entwicklervorschau**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie über das Microsoft Teams-Menü mit den Auslassungspunkten die Option „Info“, und wählen Sie dann „Entwicklervorschau“ aus.":::

1. Wählen Sie **Apps** aus, um den Bereich **Apps verwalten** zu öffnen. Wählen Sie dann **App veröffentlichen** aus.

    :::image type="content" source="images/teams-manage-your-apps.png" alt-text="Öffnen Sie den Bereich &quot;Apps verwalten&quot;, und wählen Sie &quot;App veröffentlichen&quot; aus.":::

1. Wählen Sie die Option **Benutzerdefinierte App hochladen** und dann Ihr App-Paket aus, und installieren Sie es (*Hinzufügen*) auf Ihrem Microsoft Teams-Client.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Option &quot;Benutzerdefinierte App hochladen&quot; in Microsoft Teams":::

Nachdem sie in Microsoft Teams quergeladen wurde, ist Ihre Nachrichtenerweiterung in outlook.com und Outlook für Windows Desktop verfügbar.

## <a name="preview-your-message-extension-in-outlook"></a>Anzeigen einer Vorschau ihrer Nachrichtenerweiterung in Outlook

So können Sie Ihre Nachrichtenerweiterung zur Ausführung in Outlook auf Desktop- und Weboberflächen unter Windows testen.

### <a name="outlook-on-the-web"></a>Outlook im Web

So zeigen Sie eine Vorschau Ihrer App an, die in Outlook im Web ausgeführt wird:

1. Melden Sie sich mit den Anmeldeinformationen für Ihren Testmandanten bei [outlook.com](https://www.outlook.com) an.
1. Wählen Sie **Neue Nachricht** aus.
1. Öffnen Sie das Flyoutmenü **Weitere Apps** am unteren Rand des Kompositionsfensters.

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Klicken Sie unten im E-Mail-Kompositionsfenster auf das Menü „Weitere Apps“, um Ihre Nachrichtenerweiterung zu verwenden.":::

Ihre Nachrichtenerweiterung wird aufgelistet. Sie können sie von dort aus aufrufen und genauso verwenden, wie Sie es beim Verfassen einer Nachricht in Teams tun würden.

### <a name="outlook"></a>Outlook

So zeigen Sie eine Vorschau Ihrer App an, die in Outlook auf Windows-Desktop ausgeführt wird:

1. Starten Sie Outlook mit den Anmeldeinformationen für Ihren Testmandanten.
1. Wählen Sie **Neue E-Mail** aus.
1. Öffnen Sie das Flyoutmenü **Weitere Apps** im oberen Menüband.

    :::image type="content" source="images/outlook-desktop-compose-more-apps.png" alt-text="Klicken Sie im Menüband des Kompositionsfensters auf &quot;Weitere Apps&quot;, um Ihre Nachrichtenerweiterung zu verwenden.":::

Ihre Nachrichtenerweiterung wird aufgelistet. Sie öffnet einen angrenzenden Bereich, in dem Suchergebnisse angezeigt werden.

## <a name="troubleshooting"></a>Problembehandlung

 Ihre aktualisierte Nachrichtenerweiterung wird zwar weiterhin in Teams mit vollständiger [Funktionsunterstützung für Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ausgeführt, es gibt jedoch Einschränkungen in dieser frühen Vorschau der Outlook-aktivierten Benutzeroberfläche, die Sie beachten müssen:

* Nachrichtenerweiterungen in Outlook sind auf den [*Kontext zum Verfassen*](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions) von E-Mails beschränkt. Auch wenn Ihre Teams-Nachrichtenerweiterung `commandBox` als *Kontext* in ihrem Manifest enthält, ist die aktuelle Vorschau auf die Option zum Verfassen von E-Mails (`compose`) beschränkt. Das Aufrufen einer Nachrichtenerweiterung aus dem globalen Outlook-Feld *Suchen* wird nicht unterstützt.
* [Aktionsbasierte Nachrichtenerweiterungsbefehle](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) werden in Outlook nicht unterstützt. Wenn Ihre App sowohl such- als auch aktionsbasierte Befehle enthält, wird sie in Outlook angezeigt, aber das Aktionsmenü ist nicht verfügbar.
* Das Einfügen von mehr als fünf [adaptiven Karten](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) in eine E-Mail wird nicht unterstützt. Adaptive Karten v1.4 und höher werden nicht unterstützt.
* [Kartenaktionen](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) vom Typ `messageBack`, `imBack`, `invoke`und `signin` werden für eingefügte Karten nicht unterstützt. Die Unterstützung ist beschränkt auf `openURL`: Beim Klicken wird der Benutzer zur angegebenen URL auf einer neuen Registerkarte weitergeleitet.

Verwenden Sie die [Kanäle der Microsoft Teams-Entwicklercommunity](/microsoftteams/platform/feedback), um Probleme zu melden und Feedback zu geben.

### <a name="debugging"></a>Debugging

Beim Testen Ihrer Nachrichtenerweiterung können Sie die Quelle (aus Teams und nicht aus Outlook stammend) von Bot-Anforderungen anhand der Eigenschaft [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) des [Activity](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md)-Objekts identifizieren. Wenn ein Benutzer eine Abfrage ausführt, erhält Ihr Dienst ein standardmäßiges Bot Framework-`Activity`Objekt. Eine der Eigenschaften im Activity-Objekt ist `channelId`, die den Wert von `msteams` oder `outlook` hat, je nachdem, woher die Bot-Anforderung stammt. Weitere Informationen finden Sie im [SDK für suchbasierte Nachrichtenerweiterungen](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
| NPM-Suchconnector | Verwenden Sie Teams Toolkit, um eine Nachrichtenerweiterungs-App zu erstellen. Funktioniert in Teams, Outlook. |  [Anzeigen](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/NPM-search-connector-M365) |

## <a name="next-step"></a>Nächster Schritt

Veröffentlichen Sie Ihre App, damit sie in Teams, Outlook und Office auffindbar ist:

> [!div class="nextstepaction"]
> [Veröffentlichen von Teams-Apps für Outlook und Office](publish.md)
