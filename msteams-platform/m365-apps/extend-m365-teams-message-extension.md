---
title: Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365
description: Erfahren Sie, wie Sie Ihre suchbasierte Nachrichtenerweiterung so aktualisieren, dass sie zusätzlich zu Microsoft Teams in Outlook ausgeführt wird.
ms.date: 10/10/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 9b153eaaaa4cf3eb59d1a7b34122b569ae0d0d1a
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789940"
---
# <a name="extend-a-teams-message-extension-across-microsoft-365"></a>Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365

Suchbasierte [Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ermöglichen es Benutzern, ein externes System zu durchsuchen und die Ergebnisse über den Bereich des Microsoft Teams-Clients zum Verfassen von Nachrichten freizugeben. Sie können jetzt suchbasierte Teams-Nachrichtenerweiterungen in der Produktion für Vorschaugruppen in Outlook für Windows Desktop und outlook.com nutzen, indem [Sie Ihre Teams-Apps auf Microsoft 365 erweitern](overview.md).

Der Prozess zum Aktualisieren Ihrer suchbasierten Teams-Nachrichtenerweiterung umfasst die folgenden Schritte:

> [!div class="checklist"]
>
> * Aktualisieren Sie Ihr App-Manifest.
> * Fügen Sie einen Outlook-Kanal für Ihren Bot hinzu.
> * Laden Sie Ihre aktualisierte App in Teams quer.

Der Rest dieses Leitfadens führt Sie durch diese Schritte und zeigt, wie Sie eine Vorschau Ihrer Nachrichtenerweiterung in Outlook für Windows Desktop und Web anzeigen.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial benötigen Sie Folgendes:

* Einen Sandkastenmandanten für das Microsoft 365-Entwicklerprogramm.
* Registrierung in *Office 365 Targeted Releases* für Ihren Sandbox-Mandanten.
* Eine Testumgebung mit installierten Office-Anwendungen aus dem Microsoft 365 Apps-*Betakanal*.
* (Optional) Microsoft Visual Studio Code mit der Teams Toolkit-Erweiterung.

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="link-unfurling"></a>Verbreiten von Links

Wenn Ihre suchbasierte Nachrichtenerweiterung [das Entpacken von Links](../messaging-extensions/how-to/link-unfurling.md) in Teams unterstützt, ermöglicht das Ausführen der Schritte in diesem Tutorial auch das Entpacken von Links in Outlook im Web- und Windows-Desktopumgebungen. Der Abschnitt [Codebeispiele](#code-sample) unten enthält eine einfache App zum Entpacken von Links zum Testen.

## <a name="prepare-your-message-extension-for-the-upgrade"></a>Vorbereiten Ihrer Nachrichtenerweiterung für das Upgrade

Wenn Sie über eine vorhandene Nachrichtenerweiterung in der Produktion verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Projekts zum Testen, und aktualisieren Ihre App-ID im App-Manifest, um einen neuen Bezeichner (unterschiedlich von der Produktions-App-ID, für Testzwecke) zu verwenden.

Wenn Sie dieses Lernprogramm zum Aktualisieren einer vorhandenen Microsoft Teams-App mithilfe von Beispielcode absolvieren möchten, führen Sie die Setupschritte unter [Suchbeispiel für Microsoft Teams-Nachrichtenerweiterungen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) aus, um schnell eine suchbasierte Microsoft Teams-Nachrichtenerweiterung zu erstellen.

Alternativ können Sie die fertige Outlook-fähige App im folgenden Abschnitt verwenden und den Teil dieses Lernprogramms zum [*Aktualisieren des App-Manifests*](#update-the-app-manifest) überspringen.

### <a name="quickstart"></a>Schnellstart

Verwenden Sie die Microsoft Teams Toolkit-Erweiterung für Visual Studio Code, um mit einer [Beispielnachrichtenerweiterung](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/NPM-search-connector-M365) zu beginnen, die bereits für die Ausführung in Outlook aktiviert ist.

1. Öffnen Sie in Visual Studio Code die Befehlspalette (`Ctrl+Shift+P`), geben Sie `Teams: Create a new Teams app` ein.
1. Wählen Sie die Option **Neue Microsoft Teams-App erstellen** aus.
1. Wählen Sie **Suchbasierte Nachrichtenerweiterung** aus, um Beispielcode für eine Microsoft Teams Nachrichtenerweiterung mit dem neuesten Microsoft Teams-App-Manifest (Version`1.13`) herunterzuladen.

    :::image type="content" source="images/toolkit-palatte-search-sample.png" alt-text="Der Screenshot zeigt die VS Code-Befehlspalette &quot;Neue Teams-App erstellen&quot; zum Auflisten von Teams-Beispieloptionen.":::

    Das Beispiel ist auch als *NPM-Suchconnector* im Microsoft Teams Toolkit-Beispielkatalog verfügbar. Wählen Sie im Microsoft Teams Toolkit-Bereich die Option *Entwicklung* > *Beispiele anzeigen* >  **NPM-Suchconnector** aus.

    :::image type="content" source="images/toolkit-search-sample.png" alt-text="Der Screenshot ist ein Beispiel, das das NPM-Suchconnector-Beispiel im Teams-Toolkit-Beispielkatalog zeigt.":::

1. Wählen Sie die bevorzugte Programmiersprache aus.
1. Wählen Sie einen Speicherort auf Ihrem lokalen Computer für den Arbeitsbereichsordner aus, und geben Sie ihren Anwendungsnamen ein.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben Sie `Teams: Provision in the cloud` ein, um die erforderlichen App-Ressourcen (Azure App Service, App Service Plan, Azure Bot und verwaltete Identität) in Ihrem Azure-Konto zu erstellen.
1. Wählen Sie ein Abonnement und eine Ressourcengruppe aus.
1. Wählen Sie **Bereitstellen** aus.
1. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`) und geben Sie `Teams: Deploy to the cloud` ein, um den Beispielcode für die bereitgestellten Ressourcen in Azure einzusetzen und die App zu starten.
1. Wählen Sie **Bereitstellen**.

Von hier aus können Sie mit dem [Hinzufügen eines Outlook Kanals für Ihren Bot](#add-an-outlook-channel-for-your-bot) fortfahren, um den letzten Schritt zur Aktivierung der Microsoft Teams-Nachrichtenerweiterung in Outlook auszuführen. (Das App-Manifest verweist bereits auf die richtige Version, sodass keine Updates erforderlich sind.)

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen die Schemaversion `1.13` des [Teams-Entwicklermanifests](../resources/schema/manifest-schema.md) verwenden, damit Ihre Teams-Nachrichtenerweiterung in Outlook ausgeführt werden kann.

Sie haben zwei Möglichkeiten zum Aktualisieren Ihres App-Manifests:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die Befehlspalette: `Ctrl+Shift+P`.
1. Führen Sie den `Teams: Upgrade Teams manifest`-Befehl aus, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden direkt dort vorgenommen.

# <a name="manual-steps"></a>[Manuelle Anwendung](#tab/manifest-manual)

Öffnen Sie Ihr Teams-App-Manifest, und aktualisieren Sie das `$schema` und die `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

Wenn Sie Teams Toolkit zum Erstellen Ihrer Nachrichtenerweiterungs-App verwendet haben, können Sie damit die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette (`Ctrl+Shift+P`), und suchen **Sie nach Teams: Manifestdatei überprüfen**.

## <a name="add-an-outlook-channel-for-your-bot"></a>Hinzufügen eines Outlook-Kanals für Ihren Bot

In Microsoft Teams besteht eine Nachrichtenerweiterung aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, wo Ihr Webdienst gehostet wird. Der Webdienst nutzt das [Bot Framework SDK](/azure/bot-service/bot-service-overview)-Nachrichtenschema und das sichere Kommunikationsprotokoll über einen Teams-Kanal, der für Ihren Bot registriert ist.

Damit Benutzer mit Ihrer Nachrichtenerweiterung aus Outlook interagieren können, müssen Sie Ihrem Bot einen Outlook-Kanal hinzufügen:

1. Navigieren Sie [von Microsoft Azure-Portal](https://portal.azure.com) (oder [Bot Framework-Portal](https://dev.botframework.com), wenn Sie sich zuvor dort registriert haben) zu Ihrer Botressource.

1. Wählen Sie unter *Einstellungen* die Option **Kanäle**.

1. Wählen Sie unter *Verfügbare Kanäle* die Option **Outlook** aus. Wählen Sie die Registerkarte **Nachrichtenerweiterungen** und dann **Anwenden** aus.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Der Screenshot ist ein Beispiel, das den Outlook-Kanal &quot;Nachrichtenerweiterungen&quot; für Ihren Bot aus dem Bereich &quot;Azure Bot Channels&quot; zeigt.":::

1. Vergewissern Sie sich, dass Ihr Outlook-Kanal zusammen mit Teams im Bereich **Kanäle** Ihres Bots aufgeführt ist.

    :::image type="content" source="images/azure-bot-channels.png" alt-text="Der Screenshot ist ein Beispiel, das den Bereich &quot;Azure Bot Channels&quot; zeigt, in dem sowohl Teams- als auch Outlook-Kanäle aufgelistet sind.":::

## <a name="update-microsoft-azure-active-directory-azure-ad-app-registration-for-sso"></a>Aktualisieren der Microsoft Azure Active Directory (Azure AD)-App-Registrierung für SSO

> [!NOTE]
> Sie können diesen Schritt überspringen, wenn Sie die in diesem Tutorial bereitgestellte [Beispiel-App](#quickstart) verwenden, da das Szenario keine Azure Active Directory-Authentifizierung (AAD) single Sign-On umfasst.

Azure Active Directory (AD) Single Sign-On (SSO) für Nachrichtenerweiterungen funktioniert in Outlook [genauso wie in Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots). Sie müssen der Azure AD-App-Registrierung Ihres Bots im *App-Registrierungen-Portal* Ihres Mandanten jedoch mehrere Clientanwendungs-IDs hinzufügen.

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

Der letzte Schritt besteht darin, Ihre aktualisierte Nachrichtenerweiterung ([App-Paket](/microsoftteams/platform/concepts/build-and-test/apps-package)) in Teams querzuladen. Nachdem Sie den Vorgang abgeschlossen haben, wird die Nachrichtenerweiterung in Ihren *installierten Apps* im Nachrichtenbereich zum Verfassen angezeigt.

1. Verpacken Sie Ihre Teams-Anwendung (Manifest- und App-[Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der Option **Teams-Metadatenpaket in einer ZIP-Datei verpacken** im Menü *Bereitstellung* von Teams Toolkit tun.

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Der Screenshot zeigt ein Beispiel mit der Option &quot;Zip Teams metadata package&quot; (Teams-Metadatenpaket zippen) in der Teams Toolkit-Erweiterung für Visual Studio Code.":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Microsoft Teams an, und wechseln Sie in den *Entwicklervorschaumodus*. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil Folgendes aus: **Info** > **Entwicklervorschau**.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Der Screenshot ist ein Beispiel, das die Option &quot;Entwicklervorschau&quot; zeigt.":::

1. Wählen Sie **Apps** aus, um den Bereich **Apps verwalten** zu öffnen. Wählen Sie dann **App hochladen** aus.

    :::image type="content" source="../assets/images/teams-manage-your-apps.png" alt-text="Der Screenshot ist ein Beispiel, das die Option &quot;App hochladen&quot; zeigt.":::

1. Wählen Sie **die Option Angepasste App hochladen** aus, wählen Sie Ihr App-Paket aus, und installieren Sie es auf Ihrem Teams-Client( *Hinzufügen*).

    :::image type="content" source="../assets/images/teams-upload-custom-app.png" alt-text="Der Screenshot ist ein Beispiel, das die Option &quot;Benutzerdefinierte App hochladen&quot; in Teams zeigt.":::

Nachdem sie über Teams quergeladen wurde, ist Ihre Nachrichtenerweiterung in Outlook für Windows Desktop und Web verfügbar.

## <a name="preview-your-message-extension-in-outlook"></a>Anzeigen einer Vorschau ihrer Nachrichtenerweiterung in Outlook

So können Sie Ihre Nachrichtenerweiterung zur Ausführung in Outlook auf Desktop- und Weboberflächen unter Windows testen.

### <a name="outlook-on-the-web"></a>Outlook im Web

So zeigen Sie eine Vorschau Ihrer App an, die in Outlook im Web ausgeführt wird:

1. Melden Sie sich mit Ihren Testmandantenanmeldeinformationen bei [outlook.com](https://www.outlook.com) an.
1. Wählen Sie **Neue Nachricht** aus.
1. Öffnen Sie das Flyoutmenü **Weitere Apps** am unteren Rand des Kompositionsfensters.

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Der Screenshot ist ein Beispiel, das das Menü &quot;Weitere Apps&quot; am unteren Rand des E-Mail-Kompositionsfensters zeigt, um Ihre Nachrichtenerweiterung zu verwenden.":::

Ihre Nachrichtenerweiterung wird aufgelistet. Sie können sie von dort aus aufrufen und genauso verwenden, wie Sie es beim Verfassen einer Nachricht in Teams tun würden.

### <a name="outlook"></a>Outlook

So zeigen Sie eine Vorschau Ihrer App an, die in Outlook auf Windows-Desktop ausgeführt wird:

1. Starten Sie Outlook, und melden Sie sich mit Ihren Testmandantenanmeldeinformationen an.
1. Wählen Sie **Neue E-Mail** aus.
1. Öffnen Sie das Flyoutmenü **Weitere Apps** im oberen Menüband.

    :::image type="content" source="images/outlook-desktop-compose-more-apps.png" alt-text="Der Screenshot ist ein Beispiel, das &quot;Weitere Apps&quot; im Menüband des Kompositionsfensters zeigt, um Ihre Nachrichtenerweiterung zu verwenden.":::

Ihre Nachrichtenerweiterung wird aufgelistet. Sie öffnet einen angrenzenden Bereich, in dem Suchergebnisse angezeigt werden.

## <a name="troubleshooting"></a>Problembehandlung

 Ihre aktualisierte Nachrichtenerweiterung wird zwar weiterhin in Teams mit vollständiger [Funktionsunterstützung für Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ausgeführt, es gibt jedoch Einschränkungen in dieser frühen Vorschau der Outlook-aktivierten Benutzeroberfläche, die Sie beachten müssen:

* Nachrichtenerweiterungen in Outlook sind auf den [*Kontext zum Verfassen*](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions) von E-Mails beschränkt. Auch wenn Ihre Teams-Nachrichtenerweiterung `commandBox` als *Kontext* in ihrem Manifest enthält, ist die aktuelle Vorschau auf die Option zum Verfassen von E-Mails (`compose`) beschränkt. Das Aufrufen einer Nachrichtenerweiterung aus dem globalen Outlook-Feld *Suchen* wird nicht unterstützt.
* [Aktionsbasierte Nachrichtenerweiterungsbefehle](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) werden in Outlook nicht unterstützt. Wenn Ihre App sowohl such- als auch aktionsbasierte Befehle enthält, wird sie in Outlook angezeigt, aber das Aktionsmenü ist nicht verfügbar.
* Das Einfügen von mehr als fünf [adaptiven Karten](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) in eine E-Mail wird nicht unterstützt. Adaptive Karten v1.4 und höher werden nicht unterstützt.
* [Kartenaktionen](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) vom Typ `messageBack`, `imBack`, `invoke`und `signin` werden für eingefügte Karten nicht unterstützt. Die Unterstützung ist auf `openURL`beschränkt: Wenn diese Option ausgewählt ist, wird der Benutzer auf einer neuen Registerkarte an die angegebene URL umgeleitet.

Verwenden Sie die [Kanäle der Microsoft Teams-Entwicklercommunity](/microsoftteams/platform/feedback), um Probleme zu melden und Feedback zu geben.

### <a name="debugging"></a>Debugging

Beim Testen Ihrer Nachrichtenerweiterung können Sie die Quelle (aus Teams und nicht aus Outlook stammend) von Bot-Anforderungen anhand der Eigenschaft [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) des [Activity](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md)-Objekts identifizieren. Wenn ein Benutzer eine Abfrage ausführt, erhält Ihr Dienst ein standardmäßiges Bot Framework-`Activity`Objekt. Eine der Eigenschaften im Activity-Objekt ist `channelId`, das den Wert von `msteams` oder `outlook`hat, je nachdem, wo die Botanforderung stammt. Weitere Informationen finden Sie unter [Suchbasiertes Nachrichtenerweiterungs-SDK](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Node.js** |
|---------------|--------------|--------|
| NPM-Suchconnector | Verwenden Sie Teams Toolkit, um eine Nachrichtenerweiterungs-App zu erstellen. Funktioniert in Teams, Outlook. |  [Anzeigen](https://github.com/OfficeDev/TeamsFx-Samples/tree/ga/NPM-search-connector-M365) |
| Teams Link Unfurling | Einfache Teams-App zur Veranschaulichung der Link-Entflechtung. Funktioniert in Teams, Outlook. | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/55.teams-link-unfurling)

## <a name="next-step"></a>Nächster Schritt

Veröffentlichen Sie Ihre App, damit sie in Teams, Outlook und Office auffindbar ist:

> [!div class="nextstepaction"]
> [Veröffentlichen von Teams-Apps für Outlook und Office](publish.md)
