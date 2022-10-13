---
title: Erstellen von Office 365-Connectors
author: laujan
description: Erste Schritte mit Office 365 Connectors. Fügen Sie der Teams-App in Microsoft Teams einen Connector hinzu. Beispiel(.NET, Node.js) Office 365 Connector, der Benachrichtigungen an den Teams-Kanal generiert.
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 8e9b1d831858bcf9aefeedbafcb098744470e1d7
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560743"
---
# <a name="create-office-365-connectors"></a>Erstellen von Office 365-Connectors

With Microsoft Teams apps, you can add your existing Office 365 Connector or build a new one within Teams. For more information, see [build your own connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).

Im folgenden Video erfahren Sie, wie Sie eine Office 365 Connectors erstellen:
<br>

> [!VIDEO <https://www.microsoft.com/en-us/videoplayer/embed/RE4OIzv>]
<br>

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="add-a-connector-to-teams-app"></a>Hinzufügen eines Connectors zur Teams-App

Sie können ein [Paket](~/concepts/build-and-test/apps-package.md) erstellen und den Connector als Teil Ihrer AppSource-Übermittlung [veröffentlichen](~/concepts/deploy-and-publish/apps-publish.md). Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Informationen zu Einstiegspunkten für die Teams-App finden Sie unter [Funktionen](~/concepts/extensibility-points.md). Sie können das Paket Benutzern auch direkt zum Hochladen in Teams bereitstellen.

Um Ihren Connector zu verteilen, registrieren Sie ihn im [Connectors-Entwicklerdashboard](https://aka.ms/connectorsdashboard).

Damit ein Connector nur in Teams funktioniert, befolgen Sie die Anweisungen zum Übermitteln des Connectors beim [Veröffentlichen Ihrer App im Microsoft Teams Store-Artikel](~/concepts/deploy-and-publish/appsource/publish.md) . Ansonsten funktioniert ein registrierter Connector in allen Office 365-Produkten, die Anwendungen unterstützen, einschließlich Outlook und Teams.

> [!IMPORTANT]
> Ihr Connector wird registriert, nachdem Sie im Connectors-Entwicklerdashboard auf **Speichern** klicken. Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, folgen Sie den Anweisungen zum [Veröffentlichen Ihrer Microsoft Teams-App in AppSource](~/concepts/deploy-and-publish/apps-publish.md). Wenn Sie Ihre App nicht in AppSource veröffentlichen möchten, verteilen Sie sie direkt an die Organisation. Nach dem Veröffentlichen von Connectors für Ihre Organisation ist keine weitere Aktion im Connectordashboard erforderlich.

### <a name="integrate-the-configuration-experience"></a>Integrieren der Konfigurationserfahrung

Benutzer können die gesamte Connectorkonfiguration abschließen, ohne den Teams-Client verlassen zu müssen. Um die Erfahrung zu erhalten, kann Teams Ihre Konfigurationsseite direkt in einen iFrame einbetten. Die Abfolge der Vorgänge lautet wie folgt:

1. Der Benutzer wählt den Connector aus, um den Konfigurationsvorgang zu starten.
1. Der Benutzer interagiert mit der Weboberfläche, um die Konfiguration abzuschließen.
1. Der Benutzer wählt **Speichern** aus, wodurch ein Rückruf im Code ausgelöst wird.

    > [!NOTE]
    >
    > * Der Code kann das Speicherereignis verarbeiten, indem er die Webhookeinstellungen abruft. Ihr Code speichert den Webhook, um später Ereignisse zu posten.
    > * Die Konfigurationserfahrung wird inline in Teams geladen.

Sie können Ihre vorhandene Webkonfigurationserfahrung wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet wird. Ihr Code muss das Teams JavaScript SDK enthalten. Dadurch erhält Ihr Code Zugriff auf APIs, um allgemeine Vorgänge auszuführen, z. B. das Abrufen des aktuellen Benutzer-, Kanal- oder Teamkontexts und das Initiieren von Authentifizierungsabläufen.

So integrieren Sie die Konfigurationserfahrung:

> [!NOTE]
> Ab Teams JavaScript Client SDK (TeamsJS) v.2.0.0 sind APIs im *Einstellungsnamespace* zugunsten gleichwertiger APIs im *Seitennamespace* veraltet, einschließlich `pages.getConfig()` und anderer APIs im `pages.config` Unternamespace. Weitere Informationen finden Sie [unter Neuigkeiten in TeamsJS Version 2.0](../../tabs/how-to/using-teams-client-sdk.md#whats-new-in-teamsjs-version-20)

1. Initialisieren Sie das SDK durch Aufrufen von `app.initialize()`.
1. Rufen Sie `pages.config.setValidityState(true)` auf, um **Speichern** zu aktivieren.

    > [!NOTE]
    > Sie müssen `microsoftTeams.pages.config.setValidityState(true)` als Antwort auf die Benutzerauswahl oder Feldaktualisierung aufrufen.

1. Registrieren Sie den `microsoftTeams.pages.config.registerOnSaveHandler()`-Ereignishandler, der aufgerufen wird, wenn der Benutzer auf **Speichern** klickt.
1. Call `microsoftTeams.pages.config.setConfig()` to save the connector settings. The saved settings are also shown in the configuration dialog if the user tries to update an existing configuration for your connector.
1. Rufen Sie `microsoftTeams.pages.getConfig()` auf, um Webhookeigenschaften abzurufen, einschließlich der URL.

    > [!NOTE]
    > Im Falle einer Neukonfiguration müssen Sie `microsoftTeams.pages.getConfig()` aufrufen, wenn Ihre Seite zum ersten Mal geladen wird.

1. Registrieren Sie den `microsoftTeams.pages.config.registerOnRemoveHandler()`-Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt.

Dieses Ereignis gibt Ihrem Dienst die Möglichkeit, alle Bereinigungsaktionen auszuführen.

Der folgende Code stellt ein Beispiel-HTML bereit, um eine Connector-Konfigurationsseite ohne Kundendienst und Support zu erstellen:

```html
<h2>Send notifications when tasks are:</h2>
<div class="col-md-8">
    <section id="configSection">
        <form id="configForm">
            <input type="radio" name="notificationType" value="Create" onclick="onClick()"> Created
            <br>
            <br>
            <input type="radio" name="notificationType" value="Update" onclick="onClick()"> Updated
        </form>
    </section>
</div>

<script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" integrity="sha384-Q2Z9S56exI6Oz/ThvYaV0SUn8j4HwS8BveGPmuwLXe4CvCUEGlL80qSzHMnvGqee" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script>
        function onClick() {
            pages.config.setValidityState(true);
        }

        await microsoftTeams.app.initialize();
        pages.config.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            await pages.config.setConfig({
                entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                configName: eventType
                });

            pages.getConfig().then(async (config) {
                // We get the Webhook URL from config.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        pages.config.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

Wenn Sie die Anmeldung in Ihre eingebettete Seite integrieren möchten, um den Benutzer beim Laden der Seite zu authentifizieren, finden Sie weitere Informationen unter [Authentifizierungsablauf für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md).

> [!NOTE]
> Vor TeamsJS v.2.0.0 muss Ihr Code aus clientübergreifenden Kompatibilitätsgründen mit der URL und erfolg- oder fehlerbasierten Rückrufmethoden `authenticate()` aufrufen`microsoftTeams.authentication.registerAuthenticationHandlers()`. Ab TeamsJS v.2.0.0 wurde *registerAuthenticationHandlers zugunsten des direkten Aufrufens* von [authenticate()](/javascript/api/@microsoft/teams-js/authentication#@microsoft-teams-js-authentication-authenticate) mit den erforderlichen Authentifizierungsparametern veraltet.

#### <a name="getconfig-response-properties"></a>Eigenschaften der `getConfig`-Antwort

>[!NOTE]
>Die vom `getConfig` Aufruf zurückgegebenen Parameter unterscheiden sich, wenn Sie diese Methode von einer Registerkarte aus aufrufen, und unterscheiden sich von den in der [Referenz](/javascript/api/@microsoft/teams-js/pages#@microsoft-teams-js-pages-getconfig) dokumentierten Parametern.

Die folgende Tabelle enthält die Parameter und die Details zu `getConfig`-Antworteigenschaften:

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, wie durch Ihren Code beim Aufrufen von `setConfig()` festgelegt. |
| `configName`  | Der Konfigurationsname, wie durch Ihren Code beim Aufrufen von `setConfig()` festgelegt. |
| `contentUrl` | Die URL der Konfigurationsseite, wie durch Ihren Code beim Aufruf von `setConfig()` festgelegt. |
| `webhookUrl` | The webhook URL created for the connector. Use the webhook URL to POST structured JSON to send cards to the channel. The `webhookUrl` is returned only when the application returns data successfully. |
| `appType` | Die zurückgegebenen Werte können dem `mail``groups``teams` Office 365 Mail, Office 365 Groups oder Teams entsprechen. |
| `userObjectId` | Die eindeutige ID, die dem Office 365 Benutzer entspricht, der die Einrichtung des Connectors initiiert hat. Es muss gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuordnen, der die Konfiguration in Ihrem Dienst eingerichtet hat. |

#### <a name="handle-edits"></a>Behandeln von Bearbeitungen

Ihr Code muss Benutzer verarbeiten, die zurückkehren, um eine vorhandene Connectorkonfiguration zu bearbeiten. Rufen Sie `microsoftTeams.pages.config.setConfig()` dazu bei der Erstkonfiguration mit folgenden Parametern auf:

* `entityId` ist die benutzerdefinierte ID, die angibt, was der Benutzer konfiguriert hat und wird von Ihrem Dienst verstanden.
* `configName` ist ein Name, den der Konfigurationscode abrufen kann.
* `contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration bearbeitet.

Dieser Aufruf wird im Rahmen des Speicherereignishandlers ausgeführt. Wenn die `contentUrl` geladen wird, muss Ihr Code `getConfig()` aufrufen, um Einstellungen oder Formulare in der Benutzeroberfläche der Konfiguration vorab auszufüllen.

#### <a name="handle-removals"></a>Behandeln von Entfernungen

Sie können einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Konnektorkonfiguration entfernt. Sie registrieren diesen Handler, indem Sie `microsoftTeams.pages.config.registerOnRemoveHandler()` aufrufen. Dieser Handler wird zum Ausführen von Bereinigungsvorgängen verwendet, z. B. zum Entfernen von Einträgen aus einer Datenbank.

### <a name="include-the-connector-in-your-manifest"></a>Einschließen des Connectors in Ihr Manifest

Laden Sie das automatisch generierte *Manifest der Teams-App* aus dem Entwicklerportal herunter (<https://dev.teams.microsoft.com>). Führen Sie die folgenden Schritte aus, bevor Sie die App testen oder veröffentlichen:

1. [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
1. Ändern Sie den `icons`-Teil des Manifests so, dass er die Dateinamen der Symbole anstelle von URLs enthält.

Die folgende Datei *manifest.json* enthält die Elemente, die zum Testen und Übermitteln der App erforderlich sind:

> [!NOTE]
> Ersetzen Sie `id` und `connectorId` im folgenden Beispiel durch die GUID des Connectors.

#### <a name="example-of-manifestjson-with-connector"></a>Beispiel für manifest.json mit Connector

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="test-your-connector"></a>Testen des Connectors

To test your connector, upload it to a team with any other app. You can create a .zip package using the manifest file from the two icon files and connectors Developer Dashboard, modified as directed in [Include the connector in your Manifest](#include-the-connector-in-your-manifest).

Nachdem Sie die App hochgeladen haben, öffnen Sie die Connectorliste von einem beliebigen Kanal aus. Scrollen Sie nach unten, um Ihre App im Abschnitt **Hochgeladen** anzuzeigen:

![Screenshot des Abschnitts „Hochgeladen“ im Connectordialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> Der Ablauf erfolgt vollständig innerhalb von Teams als gehostete Erfahrung.

Um zu überprüfen, ob die `HttpPOST`-Aktion ordnungsgemäß funktioniert, [senden Sie Nachrichten an Ihren Connector](~/webhooks-and-connectors/how-to/connectors-using.md).

Befolgen Sie die [schrittweise Anleitung](../../sbs-teams-connectors.yml) zum Erstellen und Testen der Connectors in Ihren Teams.

## <a name="distribute-webhook-and-connector"></a>Verteilen von Webhook und Connector

1. [Richten Sie einen eingehenden Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md#create-an-incoming-webhook) direkt für Ihr Team ein.

1. Fügen Sie eine [Konfigurationsseite](~/webhooks-and-connectors/how-to/connectors-creating.md?#integrate-the-configuration-experience) hinzu, und veröffentlichen Sie Ihren eingehenden Webhook in einem Office 365 Connector.

1. Verpacken und veröffentlichen Sie Ihren Connector als Teil Ihrer [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md)-Übermittlung.

## <a name="code-sample"></a>Codebeispiel

Die folgende Tabelle enthält den Beispielnamen und die Beschreibung:

|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Connectors | Beispiel für einen Office 365-Connector, der Benachrichtigungen an einen Teams-Kanal generiert.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Beispiel für generische Connectors |Beispielcode für einen generischen Connector, der einfach an jedes System angepasst werden kann, das Webhooks unterstützt.| | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../sbs-teams-connectors.yml) zum Erstellen und Testen von Connectors in Teams.

## <a name="see-also"></a>Siehe auch

* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [So können Administratoren Connectors aktivieren oder deaktivieren](/MicrosoftTeams/office-365-custom-connectors#enable-or-disable-connectors-in-teams)
* [So können Administratoren benutzerdefinierte Connectors innerhalb ihrer Organisation veröffentlichen](/MicrosoftTeams/office-365-custom-connectors)
* [Erstellen eines Benachrichtigungsbots mit JavaScript](../../sbs-gs-notificationbot.yml)
* [Erstellen Ihrer ersten Bot-App mit JavaScript](../../sbs-gs-bot.yml)
