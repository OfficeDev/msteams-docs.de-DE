---
title: Erweitern einer Teams Messaging-Erweiterung über Microsoft 365
description: Hier erfahren Sie, wie Sie Ihre suchbasierte Teams Messaging-Erweiterung so aktualisieren, dass sie in Outlook
ms.date: 11/15/2021
ms.topic: tutorial
ms.custom: m365apps
ms.openlocfilehash: f019f82c4e617e3cf6aa7caa499e125dc448b1c3
ms.sourcegitcommit: abe5ccd61ba3e8eddc1bec01752fd949a7ba0cc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2022
ms.locfileid: "62281742"
---
# <a name="extend-a-teams-messaging-extension-across-microsoft-365"></a>Erweitern einer Teams Messaging-Erweiterung über Microsoft 365

> [!NOTE]
> *Das Erweitern einer Teams Messaging-Erweiterung über Microsoft 365* ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar. Die in der Vorschau enthaltenen Features sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie in der öffentlichen Version verfügbar werden. Sie werden nur zu Test- und Untersuchungszwecken bereitgestellt. Sie sollten nicht in Produktionsanwendungen verwendet werden.

Suchbasierte [Messaging-Erweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ermöglichen Es Benutzern, ein externes System zu durchsuchen und Ergebnisse über den Nachrichtenbereich zum Verfassen des Microsoft Teams-Clients freizugeben. Indem [Sie Ihre Teams-Apps auf Microsoft 365 (Vorschau) erweitern](overview.md), können Sie ihre suchbasierten Teams Messaging-Erweiterungen jetzt Outlook für Windows Desktop- und Webumgebungen bereitstellen.

Der Prozess zum Aktualisieren Ihrer suchbasierten Teams Messaging-Erweiterung zur Ausführung Outlook umfasst die folgenden Schritte:

> [!div class="checklist"]
> * Aktualisieren des App-Manifests
> * Hinzufügen eines Outlook Kanals für Ihren Bot
> * Querladen der aktualisierten App in Teams

Der Rest dieses Leitfadens führt Sie durch diese Schritte und zeigt Ihnen, wie Sie ihre Messaging-Erweiterung in Outlook für Windows Desktop und Web in der Vorschau anzeigen.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieses Lernprogramms benötigen Sie Folgendes:

 - Ein Sandkastenmandant des Microsoft 365-Entwicklerprogramms
 - Ihr Sandkastenmandant, der in *Office 365 Targeted Releases registriert ist*
 - Eine Testumgebung mit Office über den Microsoft 365 Apps *Betakanal* installierten Apps
 - Visual Studio Code mit der Erweiterung Teams Toolkit (Vorschau) (Optional)

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="prepare-your-messaging-extension-for-the-upgrade"></a>Vorbereiten der Messaging-Erweiterung für das Upgrade

Wenn Sie über eine vorhandene Messaging-Erweiterung verfügen, erstellen Sie zum Testen eine Kopie oder einen Zweig Ihres Produktionsprojekts, und aktualisieren Sie Ihre App-ID im App-Manifest so, dass sie einen neuen Bezeichner verwendet (der sich von der Produktions-App-ID unterscheidet).

Wenn Sie Beispielcode zum Abschließen dieses Lernprogramms verwenden möchten, führen Sie die Setupschritte in [Teams Suchbeispiel für Messaging-Erweiterungen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/50.teams-messaging-extensions-search) aus, um schnell eine Microsoft Teams suchbasierte Messaging-Erweiterung zu erstellen. Sie können auch mit demselben [Teams Suchbeispiel für Messaging-Erweiterungen beginnen, das für TeamsJS SDK v2 Preview aktualisiert wurde](https://github.com/OfficeDev/TeamsFx-Samples/tree/v2/NPM-search-connector-M365), und mit [der Vorschau Ihrer Messaging-Erweiterung in Outlook](#preview-your-messaging-extension-in-outlook) fortfahren. Das aktualisierte Beispiel ist auch in Teams Toolkit-Erweiterung verfügbar: *DevelopmentView* >  *samplesNPM* >  **Search Connector**.

:::image type="content" source="images/toolkit-search-sample.png" alt-text="NPM-Suchconnectorbeispiel in Teams Toolkit":::

## <a name="update-the-app-manifest"></a>Aktualisieren des App-Manifests

Sie müssen das [Teams Entwicklervorschau-Manifestschema](/microsoftteams/platform/resources/schema/manifest-schema-dev-preview) und die `m365DevPreview` Manifestversion verwenden, damit Ihre Teams Messaging-Erweiterung in Outlook ausgeführt werden kann.

Sie haben zwei Optionen zum Aktualisieren Des App-Manifests:

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

Wenn Sie Teams Toolkit zum Erstellen Ihrer Messaging-Erweiterungs-App verwendet haben, können Sie sie verwenden, um die Änderungen an Ihrer Manifestdatei zu überprüfen und Fehler zu identifizieren. Öffnen Sie die Befehlspalette`Ctrl+Shift+P`, und suchen Sie **nach Teams: Überprüfen der Manifestdatei**, oder wählen Sie die Option im Bereitstellungsmenü des Teams Toolkits aus (suchen Sie auf der linken Seite von Visual Studio Code nach dem Symbol Teams).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Option &quot;Manifestdatei überprüfen&quot; im Teams Toolkit im Menü &quot;Bereitstellung&quot;":::

## <a name="add-an-outlook-channel-for-your-bot"></a>Hinzufügen eines Outlook Kanals für Ihren Bot

In Microsoft Teams besteht eine Messaging-Erweiterung aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, wo Ihr Webdienst gehostet wird. Der Webdienst nutzt das [Bot Framework SDK-Messagingschema](/azure/bot-service/bot-service-overview) und das sichere Kommunikationsprotokoll über einen Teams Kanal, der für Ihren Bot registriert ist.

Damit Benutzer über Outlook mit Ihrer Messaging-Erweiterung interagieren können, müssen Sie Ihrem Bot einen Outlook Kanal hinzufügen:

1. Navigieren Sie über [das Azure-Portal](https://portal.azure.com) (oder [das Bot Framework-Portal](https://dev.botframework.com) , wenn Sie sich zuvor dort registriert haben) zu Ihrer Bot-Ressource.

1. Wählen Sie *in Einstellungen* **"Kanäle"** aus.

1. Klicken Sie auf **Outlook**, wählen Sie die Registerkarte **"Nachrichtenerweiterungen" aus**, und klicken Sie dann auf **"Speichern**".

    :::image type="content" source="images/azure-bot-channel-message-extensions.png" alt-text="Hinzufügen eines Outlook Kanals &quot;Nachrichtenerweiterungen&quot; für Ihren Bot aus dem Bereich &quot;Azure Bot-Kanäle&quot;":::

1. Vergewissern Sie sich, dass Ihr Outlook Kanal zusammen mit Microsoft Teams **im Kanalbereich** Ihres Bots aufgeführt ist:

    :::image type="content" source="images/azure-bot-channels.png" alt-text="Bereich &quot;Azure Bot-Kanäle&quot; mit Microsoft Teams und Outlook Kanälen":::

## <a name="sideload-your-updated-messaging-extension-in-teams"></a>Querladen der aktualisierten Messaging-Erweiterung in Teams

Der letzte Schritt besteht darin, Die aktualisierte Messaging-Erweiterung ([App-Paket](/microsoftteams/platform/concepts/build-and-test/apps-package)) in Microsoft Teams querzuladen. Nach Abschluss des Vorgangs wird Ihre Messaging-Erweiterung in den installierten *Apps* aus dem Bereich zum Verfassen von Nachrichten angezeigt.

1. Verpacken Sie Ihre Teams Anwendung (Manifest[- und App-Symbole](/microsoftteams/platform/resources/schema/manifest-schema#icons)) in einer ZIP-Datei. Wenn Sie Teams Toolkit zum Erstellen Ihrer App verwendet haben, können Sie dies ganz einfach mit der Option **zip Teams Metadatenpaket** im *Bereitstellungsmenü* von Teams Toolkit tun:

    :::image type="content" source="images/toolkit-zip-teams-metadata-package.png" alt-text="Option &quot;Zip-Teams-Metadatenpaket&quot; in Teams Toolkit-Erweiterung für Visual Studio Code":::

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Teams an, und überprüfen Sie, ob Sie sich in der *Öffentlichen Entwicklervorschau* befinden, indem Sie auf das Menü mit den Auslassungspunkten (**...**) ihres Benutzerprofils klicken und "**Info**" öffnen, um zu überprüfen, ob die Option "*Entwicklervorschau*" aktiviert ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie im Menü Teams Ellipsen &quot;Info&quot;, und überprüfen Sie, ob die Option &quot;Entwicklervorschau&quot; aktiviert ist.":::

1. Öffnen Sie den *Bereich "Apps*", und klicken Sie auf **Hochladen einer benutzerdefinierten App**, und **Hochladen Sie dann für mich oder meine Teams**.

    :::image type="content" source="images/teams-upload-custom-app.png" alt-text="Schaltfläche &quot;Hochladen einer benutzerdefinierten App&quot; im Bereich Teams &quot;Apps&quot;":::

1. Wählen Sie Ihr App-Paket aus, und klicken Sie auf *"Öffnen*".

Nach dem Querladen über Teams ist Ihre Messaging-Erweiterung in Outlook im Web verfügbar.

## <a name="preview-your-messaging-extension-in-outlook"></a>Anzeigen einer Vorschau ihrer Messaging-Erweiterung in Outlook

Jetzt können Sie Ihre Messaging-Erweiterung testen, die in Outlook auf Windows Desktop und im Web ausgeführt wird. Während Ihre aktualisierte Messaging-Erweiterung weiterhin in Teams mit vollständiger [Featureunterstützung für Messaging-Erweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) ausgeführt wird, gibt es in dieser frühen Vorschau der Outlook-aktivierten Erfahrung Einschränkungen, die Sie beachten sollten:

* Messaging-Erweiterungen in Outlook sind auf den [*E-Mail-Verfassenkontext*](/microsoftteams/platform/resources/schema/manifest-schema#composeextensions) beschränkt. Auch wenn Ihre Teams Messaging-Erweiterung als *Kontext* im Manifest enthalten `commandBox` ist, ist die aktuelle Vorschau auf die E-Mail-Kompositionsoption (`compose`) beschränkt. Das Aufrufen einer Messaging-Erweiterung aus dem globalen Outlook *Suchfeld* wird nicht unterstützt.
* [Aktionsbasierte Messaging-Erweiterungsbefehle](/microsoftteams/platform/messaging-extensions/how-to/action-commands/define-action-command?tabs=AS) werden in Outlook nicht unterstützt. Wenn Ihre App sowohl such- als auch aktionsbasierte Befehle hat, wird sie in Outlook angezeigt, aber das Aktionsmenü ist nicht verfügbar.
* Das Einfügen von mehr als fünf [adaptiven Karten](/microsoftteams/platform/task-modules-and-cards/cards/design-effective-cards?tabs=design) in eine E-Mail wird nicht unterstützt. Adaptive Karten v1.4 und höher werden nicht unterstützt.
* [Kartenaktionen](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json) vom Typ `messageBack`, `imBack`, `invoke`und `signin` werden für eingefügte Karten nicht unterstützt. Die Unterstützung ist auf Folgendes `openURL`beschränkt: Wenn Sie klicken, wird der Benutzer auf einer neuen Registerkarte an die angegebene URL umgeleitet.

Beim Testen Der Messaging-Erweiterung können Sie die Quelle (von Teams im Vergleich zu Outlook) von Bot-Anforderungen durch die [channelId](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md#channel-id) des [Activity -](https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md)Objekts identifizieren. Wenn ein Benutzer eine Abfrage durchführt, empfängt Ihr Dienst ein standardmäßiges Bot Framework-Objekt `Activity` . Eine der Eigenschaften im Activity -Objekt ist `channelId`, die den Wert oder `msteams` `outlook`, je nachdem, wo die Bot-Anforderung stammt. Weitere Informationen finden Sie unter  [Search Based Messaging Extensions SDK](/microsoftteams/platform/resources/messaging-extension-v3/search-extensions).

### <a name="outlook"></a>Outlook

Um eine Vorschau Ihrer App anzuzeigen, die in Outlook auf Windows Desktop ausgeführt wird, öffnen Sie Outlook mit Anmeldeinformationen für Ihren Testmandanten angemeldet. Klicken Sie auf **"Neue E-Mail"**. Öffnen Sie das Flyoutmenü **"Weitere Apps** " im oberen Menüband. Ihre Messaging-Erweiterung wird aufgelistet. Sie können es von dort aus aufrufen und wie beim Verfassen einer Nachricht in Teams verwenden.

### <a name="outlook-on-the-web"></a>Outlook im Web

Melden Sie sich bei outlook.com unter Verwendung von Anmeldeinformationen für Ihren Testmandanten an, um eine Vorschau Der App anzuzeigen, die in [Outlook im Web](https://www.outlook.com) ausgeführt wird. Klicken Sie auf **"Neue Nachricht"**. Öffnen Sie das Flyoutmenü **"Weitere Apps** " am unteren Rand des Kompositionsfensters. Ihre Messaging-Erweiterung wird aufgelistet. Sie können es von dort aus aufrufen und wie beim Verfassen einer Nachricht in Teams verwenden.

## <a name="next-steps"></a>Nächste Schritte

Outlook aktivierte Teams Messaging-Erweiterungen befinden sich in der Vorschau und werden für die Produktionsverwendung nicht unterstützt. Hier erfahren Sie, wie Sie Ihre Outlook-aktivierte Messaging-Erweiterung zu Testzwecken an Benutzer in der Vorschau anzeigen.

### <a name="single-tenant-distribution"></a>Einzelmandantenverteilung

Outlook- und Office-aktivierte persönliche Registerkarten können auf drei Arten an eine Vorschaugruppe über einen Testmandanten (oder Produktionsmandanten) verteilt werden:

#### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü *"Apps*" die Option *"Apps verwaltenSubmit* >  **einer App an Ihre Organisation**" aus. Dies erfordert die Genehmigung durch Ihren IT-Administrator.

#### <a name="microsoft-teams-admin-center"></a>Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation hochladen https://admin.teams.microsoft.com/und vorab installieren. Weitere Informationen finden Sie [unter Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

#### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket hochladen und vorab installieren.https://admin.microsoft.com/ Weitere Informationen finden Sie [unter Testen und Bereitstellen von Microsoft 365 Apps von Partnern im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

### <a name="multi-tenant-distribution"></a>Mehrinstanzenfähige Verteilung

Die Verteilung an Microsoft AppSource wird während dieser frühen Entwicklervorschau von Outlook-aktivierten Teams Messaging-Erweiterungen noch nicht unterstützt.
