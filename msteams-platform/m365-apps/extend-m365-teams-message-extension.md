---
title: Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365
description: Hier erfahren Sie, wie Sie Ihre suchbasierte Teams-Nachrichtenerweiterung für die Ausführung in Outlook aktualisieren.
ms.date: 02/11/2022
ms.topic: tutorial
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 7e3a0d772367952c1726648fce2f10e1d8b885b2
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111374"
---
# <a name="extend-a-teams-message-extension-across-microsoft-365"></a>Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365

> [!NOTE]
> Die Funktion zum *Erweitern einer Teams-Nachrichtenerweiterung in Microsoft 365* ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar. Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Suchbasierte [Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ermöglichen es Benutzern, ein externes System zu durchsuchen und die Ergebnisse über den Bereich des Microsoft Teams-Clients zum Verfassen von Nachrichten freizugeben. Durch das [Erweitern Ihrer Teams-Apps in Microsoft 365 (Vorschau)](overview.md) können Sie jetzt Ihre suchbasierten Teams-Nachrichtenerweiterungen auf Outlook für Desktop- und Weboberflächen unter Windows übertragen.

Der Prozess zum Aktualisieren Ihrer suchbasierten Teams-Nachrichtenerweiterung zum Ausführen in Outlook umfasst die folgenden Schritte:

> [!div class="checklist"]
>
> * Aktualisieren Ihres App-Manifests
> * Hinzufügen eines Outlook-Kanals für Ihren Bot
> * Querladen Ihrer aktualisierten App in Teams

Der Rest dieses Leitfadens führt Sie durch diese Schritte und zeigt Ihnen, wie Sie Ihre Nachrichtenerweiterung in Outlook sowohl für Desktop- als auch für Webumgebungen unter Windows in der Vorschau anzeigen können.

## <a name="prerequisites"></a>Voraussetzungen

Um dieses Lernprogramm abzuschließen, benötigen Sie Folgendes:

* Einen Sandkastenmandanten für Microsoft 365-Entwicklerprogramme
* Ihren Sandkastenmandanten, der in *gezielten Office 365-Releases* registriert ist
* Eine Testumgebung mit Office-Apps, die über den Microsoft 365 Apps-*Betakanal* installiert sind
* Microsoft Visual Studio Code mit der Erweiterung Teams Toolkit (Vorschau) (optional)

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-message-extension-for-the-upgrade"></a>Vorbereiten Ihrer Nachrichtenerweiterung für das Upgrade

Wenn Sie über eine vorhandene Nachrichtenerweiterung verfügen, erstellen Sie eine Kopie oder einen Zweig Ihres Produktionsprojekts zum Testen und Aktualisieren Ihrer App-ID im App-Manifest, um einen neuen Bezeichner (unterschiedlich von der Produktions-App-ID) zu verwenden.

Wenn Sie dieses Lernprogramm mithilfe von Beispielcode abschließen möchten, führen Sie die Setupschritte unter [Suchbeispiel für Teams-Nachrichtenerweiterungen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) aus, um schnell eine suchbasierte Microsoft Teams-Nachrichtenerweiterung zu erstellen. Oder Sie können mit demselben [für TeamsJS SDK v2 Preview aktualisierten Suchbeispiel für Teams-Nachrichtenerweiterungen](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/NPM-search-connector-M365) beginnen und mit [Anzeigen einer Vorschau Ihrer Nachrichtenerweiterung in Outlook](#preview-your-message-extension-in-outlook) fortfahren. Das aktualisierte Beispiel ist auch in der Teams Toolkit-Erweiterung verfügbar: *Entwicklung* >  *Beispiele anzeigen* >  **NPM-Suchconnector**.

:::image type="content" source="images/toolkit-search-sample.png" alt-text="NPM Search Connector-Beispiel in Teams Toolkit":::

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen das Schema für das [Teams-Entwicklervorschaumanifest](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) und die `m365DevPreview` Manifestversion verwenden, damit Ihre Teams-Nachrichtenerweiterung in Outlook ausgeführt werden kann.

Sie haben zwei Möglichkeiten zum Aktualisieren Ihres App-Manifests:

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen Sie den `Teams: Upgrade Teams manifest to support Outlook and Office apps` Befehl aus, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden direkt dort vorgenommen.

# <a name="manual-steps"></a>[Manuelle Schritte](#tab/manifest-manual)

Öffnen Sie Ihr Teams-App-Manifest, und aktualisieren Sie das `$schema` und die `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```

---

Wenn Sie Teams Toolkit zum Erstellen Ihrer Nachrichtenerweiterungs-App verwendet haben, können Sie damit die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette `Ctrl+Shift+P`, und suchen Sie **Teams: Manifestdatei validieren**, oder wählen Sie die Option im Menü „Bereitstellung“ von Teams Toolkit aus (suchen Sie nach dem Teams-Symbol auf der linken Seite von Visual Studio Code).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Teams Toolkit-Option „Manifestdatei validieren“ im Menü „Bereitstellung“":::

## <a name="add-an-outlook-channel-for-your-bot"></a>Hinzufügen eines Outlook-Kanals für Ihren Bot

In Microsoft Teams besteht eine Nachrichtenerweiterung aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, wo Ihr Webdienst gehostet wird. Der Webdienst nutzt das [Bot Framework SDK](/azure/bot-service/bot-service-overview)-Nachrichtenschema und das sichere Kommunikationsprotokoll über einen Teams-Kanal, der für Ihren Bot registriert ist.

Damit Benutzer von Outlook aus mit Ihrer Nachrichtenerweiterung interagieren können, müssen Sie Ihrem Bot einen Outlook-Kanal hinzufügen:

1. Navigieren Sie aus dem [Microsoft Azure-Portal](https://portal.azure.com) (oder [Bot Framework-Portal](https://dev.botframework.com), wenn Sie sich zuvor dort registriert haben) zu Ihrer Bot-Ressource.

1. Wählen Sie unter *Einstellungen* die Option **Kanäle**.

1. Klicken Sie auf **Outlook**, wählen Sie die Registerkarte **Nachrichtenerweiterungen** aus, und klicken Sie dann auf **Speichern**.

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Hinzufügen eines Outlook-Kanals „Nachrichtenerweiterungen“ für Ihren Bot aus dem Bereich „Azure Bot Channels“":::

1. Vergewissern Sie sich, dass Ihr Outlook-Kanal zusammen mit Microsoft Teams im Bereich **Kanäle** Ihres Bots aufgeführt ist:

    :::image type="content" source="images/azure-bot-channels.png" alt-text="Bereich „Azure Bot Channels“, in dem sowohl Microsoft Teams als auch Outlook-Kanäle aufgeführt sind":::

## <a name="update-microsoft-azure-active-directory-azure-ad-app-registration-for-sso"></a>Aktualisieren der Microsoft Azure Active Directory (Azure AD)-App-Registrierung für SSO

> [!NOTE]
> Sie können den Schritt überspringen, wenn Sie [Suchbeispiel für die Teams-Nachrichtenerweiterung](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) verwenden, da das Szenario keine Azure Active Directory (AAD) Single Sign-On-Authentifizierung umfasst.

Azure Active Directory Single Sign-On (SSO) für Nachrichtenerweiterungen funktioniert in Outlook genauso [wie in Teams](/microsoftteams/platform/bots/how-to/authentication/auth-aad-sso-bots). Sie müssen jedoch der Azure AD-App-Registrierung Ihres Bots im Portal *App-Registrierungen* Ihres Mandanten mehrere Clientanwendungsbezeichner hinzufügen.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto beim [Azure-Portal](https://portal.azure.com) an.
1. Öffnen Sie **App-Registrierungen**.
1. Wählen Sie den Namen Ihrer Anwendung aus, um die entsprechende App-Registrierung zu öffnen.
1. Wählen Sie die Option **Eine API verfügbar machen** aus (unter *Verwalten*).

Stellen Sie im Abschnitt **Autorisierte Clientanwendungen** sicher, dass alle folgenden `Client Id` Werte aufgeführt sind:

|Microsoft 365-Clientanwendung | Client-ID |
|--|--|
|Teams-Desktop und mobiles Gerät |1fec8e78-bce4-4aaf-ab1b-5451cc387264 |
|Teams-Web |5e3ce6c0-2b1f-4285-8d4b-75ee78787346 |
|Outlook Desktop | d3590ed6-52b3-4102-aeff-aad2292ab01c |
|Outlook Web Access | 00000002-0000-0ff1-ce00-000000000000 |
|Outlook Web Access | bc59ab01-8403-45c6-8796-ac3ef710b3e3 |

## <a name="sideload-your-updated-message-extension-in-teams"></a>Querladen Ihrer aktualisierten Nachrichtenerweiterung in Teams

Der letzte Schritt besteht darin, die aktualisierte Nachrichtenerweiterung ([App-Paket](/microsoftteams/platform/concepts/build-and-test/apps-package)) in Microsoft Teams querzuladen. Nach Abschluss wird Ihre Nachrichtenerweiterung in den installierten *Apps* aus dem Bereich zum Verfassen von Nachrichten angezeigt.

1. Verpacken Sie Ihre Teams-Anwendung (Manifest- und App-[Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mithilfe der Option **Teams-Metadatenpaket in einer ZIP-Datei verpacken** im Menü *Bereitstellung* von Teams Toolkit tun:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option „Teams-Metadatenpaket in einer ZIP-Datei verpacken“ in der Teams Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Teams an, und vergewissern Sie sich, dass Sie sich in der *öffentlichen Entwicklervorschau* befinden, indem Sie in Ihrem Benutzerprofil auf das Menü mit den Auslassungspunkten (**…**) klicken und **Info** öffnen, um zu überprüfen, ob die Option *Entwicklervorschau* aktiviert ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie über das Teams-Menü mit den Auslassungspunkten die Option „Info“, und stellen Sie sicher, dass die Option „Entwicklervorschau“ aktiviert ist.":::

1. Öffnen Sie den Bereich *Apps*, klicken Sie auf **Benutzerdefinierte App hochladen**, und klicken Sie dann auf **Für mich oder meine Teams hochladen**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Schaltfläche „Benutzerdefinierte App hochladen“ im Teams-Bereich „Apps“":::

1. Wählen Sie Ihr App-Paket aus, und klicken Sie auf *Öffnen*.

Nach dem Querladen über Teams ist Ihre Nachrichtenerweiterung in Outlook im Web verfügbar.

## <a name="preview-your-message-extension-in-outlook"></a>Anzeigen einer Vorschau ihrer Nachrichtenerweiterung in Outlook

Jetzt können Sie Ihre Nachrichtenerweiterung zur Ausführung in Outlook auf Desktop- und Weboberflächen unter Windows testen. Ihre aktualisierte Nachrichtenerweiterung wird zwar weiterhin in Teams mit vollständiger [Funktionsunterstützung für Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ausgeführt, es gibt jedoch Einschränkungen in dieser frühen Vorschau der Outlook-aktivierten Benutzeroberfläche, die Sie beachten müssen:

* Nachrichtenerweiterungen in Outlook sind auf den [*Kontext zum Verfassen*](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions) von E-Mails beschränkt. Auch wenn Ihre Teams-Nachrichtenerweiterung `commandBox` als *Kontext* in ihrem Manifest enthält, ist die aktuelle Vorschau auf die Option zum Verfassen von E-Mails (`compose`) beschränkt. Das Aufrufen einer Nachrichtenerweiterung aus dem globalen Outlook-Feld *Suchen* wird nicht unterstützt.
* [Aktionsbasierte Nachrichtenerweiterungsbefehle](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) werden in Outlook nicht unterstützt. Wenn Ihre App sowohl such- als auch aktionsbasierte Befehle enthält, wird sie in Outlook angezeigt, aber das Aktionsmenü ist nicht verfügbar.
* Das Einfügen von mehr als fünf [adaptiven Karten](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) in eine E-Mail wird nicht unterstützt. Adaptive Karten v1.4 und höher werden nicht unterstützt.
* [Kartenaktionen](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) vom Typ `messageBack`, `imBack`, `invoke`und `signin` werden für eingefügte Karten nicht unterstützt. Die Unterstützung ist beschränkt auf `openURL`: Beim Klicken wird der Benutzer zur angegebenen URL auf einer neuen Registerkarte weitergeleitet.

Beim Testen Ihrer Nachrichtenerweiterung können Sie die Quelle (aus Teams und nicht aus Outlook stammend) von Bot-Anforderungen anhand der Eigenschaft [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) des [Activity](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md)-Objekts identifizieren. Wenn ein Benutzer eine Abfrage ausführt, erhält Ihr Dienst ein standardmäßiges Bot Framework-`Activity`Objekt. Eine der Eigenschaften im Activity-Objekt ist `channelId`, die den Wert von `msteams` oder `outlook` hat, je nachdem, woher die Bot-Anforderung stammt. Weitere Informationen finden Sie im [SDK für suchbasierte Nachrichtenerweiterungen](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

### <a name="outlook-on-the-web"></a>Outlook im Web

So zeigen Sie eine Vorschau Ihrer App an, die in Outlook im Web ausgeführt wird:

1. Melden Sie sich mit den Anmeldeinformationen für Ihren Testmandanten bei [outlook.com](https://www.outlook.com) an.
1. Wählen Sie **Neue Nachricht** aus.
1. Öffnen Sie das Flyoutmenü **Weitere Apps** am unteren Rand des Kompositionsfensters.

:::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Klicken Sie unten im E-Mail-Kompositionsfenster auf das Menü „Weitere Apps“, um Ihre Nachrichtenerweiterung zu verwenden.":::

Ihre Nachrichtenerweiterung wird aufgelistet. Sie können sie von dort aus aufrufen und genauso verwenden, wie Sie es beim Verfassen einer Nachricht in Teams tun würden.

### <a name="outlook"></a>Outlook

> [!IMPORTANT]
> Lesen Sie die neuesten Updates in [Microsoft Teams – Microsoft 365-Entwicklerblog](https://devblogs.microsoft.com/microsoft365dev/), um zu überprüfen, ob persönliche Teams-Apps durch Outlook auf Windows-Desktop für Ihren Testmandanten unterstützt werden.

So zeigen Sie eine Vorschau Ihrer App an, die in Outlook auf Windows-Desktop ausgeführt wird:

1. Starten Sie Outlook mit den Anmeldeinformationen für Ihren Testmandanten. 1. Klicken Sie auf **Neue E-Mail**.
1. Öffnen Sie das Flyoutmenü **Weitere Apps** im oberen Menüband.

Ihre Nachrichtenerweiterung wird aufgelistet. Sie können sie von dort aus aufrufen und genauso verwenden, wie Sie es beim Verfassen einer Nachricht in Teams tun würden.

## <a name="next-steps"></a>Nächste Schritte

Outlook-aktivierte Teams-Nachrichtenerweiterungen befinden sich in der Vorschau und werden für die Produktionsverwendung nicht unterstützt. Hier erfahren Sie, wie Sie Ihre Outlook-aktivierte Nachrichtenerweiterung verteilen, um eine Vorschau von Benutzergruppen zu Testzwecken anzuzeigen.

### <a name="single-tenant-distribution"></a>Verteilung an einen einzelnen Mandanten

Outlook- und Office-fähige persönliche Registerkarten können auf eine von drei Arten über einen Testmandanten (oder Produktionsmandanten) an eine Vorschaubenutzergruppe verteilt werden:

#### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü *Apps* die Option *Ihre Apps verwalten* > **Eine App an Ihre Organisation übermitteln** aus. Dies erfordert die Genehmigung Ihres IT-Administrators.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation über den [Teams-Administrator](https://admin.teams.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden Sie unter [Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

#### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket über den [Microsoft-Administrator](https://admin.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden Sie unter [Testen und Bereitstellen von Microsoft 365 Apps durch Partner im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

### <a name="multitenant-distribution"></a>Verteilung an mehrere Mandanten

Die Verteilung an Microsoft AppSource wird während dieser frühen Entwicklervorschau von Outlook-aktivierten Teams-Nachrichtenerweiterungen noch nicht unterstützt.
