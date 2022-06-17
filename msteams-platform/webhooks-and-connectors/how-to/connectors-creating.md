---
title: Erstellen von Office 365-Connectors
author: laujan
description: In diesem Modul erfahren Sie, wie Sie mit Office 365 Connectors beginnen und Teams App in Microsoft Teams
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 53f5f6d9f360c465175b18d8b1b5eab9020d3ccf
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143557"
---
# <a name="create-office-365-connectors"></a>Erstellen von Office 365-Connectors

Mit Microsoft Teams Apps können Sie Ihren bestehenden Office 365 Connector hinzufügen oder einen neuen in Teams erstellen. Weitere Informationen finden Sie unter [Erstellen Sie Ihren eigenen Connector](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).

## <a name="add-a-connector-to-teams-app"></a>Hinzufügen eines Connectors zur Teams-App

Sie können ein [Paket](~/concepts/build-and-test/apps-package.md) erstellen und den Connector als Teil Ihrer AppSource-Übermittlung [veröffentlichen](~/concepts/deploy-and-publish/apps-publish.md). Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Informationen zu Einstiegspunkten für die Teams-App finden Sie unter [Funktionen](~/concepts/extensibility-points.md). Sie können das Paket Benutzern auch direkt zum Hochladen in Teams bereitstellen.

Um Ihren Connector zu verteilen, registrieren Sie ihn im [Connectors-Entwicklerdashboard](https://aka.ms/connectorsdashboard).

Damit ein Connector nur in Microsoft Teams funktioniert, befolgen Sie die Anweisungen zum Einreichen des Connectors im Artikel zum [Veröffentlichen Ihrer App im Microsoft Teams-Store](~/concepts/deploy-and-publish/appsource/publish.md). Ansonsten funktioniert ein registrierter Connector in allen Office 365-Produkten, die Anwendungen unterstützen, einschließlich Outlook und Teams.

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

Sie können Ihre vorhandene Webkonfigurationserfahrung wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet wird. Ihr Code muss das Microsoft Teams JavaScript SDK enthalten. Dadurch erhält Ihr Code Zugriff auf APIs, um allgemeine Vorgänge auszuführen, z. B. das Abrufen des aktuellen Benutzer-, Kanal- oder Teamkontexts und das Initiieren von Authentifizierungsabläufen.

So integrieren Sie die Konfigurationserfahrung:

1. Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.
1. Rufen Sie `microsoftTeams.settings.setValidityState(true)` auf, um **Speichern** zu aktivieren.

    > [!NOTE]
    > Sie müssen `microsoftTeams.settings.setValidityState(true)` als Antwort auf die Benutzerauswahl oder Feldaktualisierung aufrufen.

1. Registrieren Sie den `microsoftTeams.settings.registerOnSaveHandler()`-Ereignishandler, der aufgerufen wird, wenn der Benutzer auf **Speichern** klickt.
1. Aufruf`microsoftTeams.settings.setSettings()`, um die Einstellungen des Connectors zu speichern. Die gespeicherten Einstellungen werden auch im Konfigurationsdialog angezeigt, wenn der Benutzer versucht, eine bestehende Konfiguration für Ihren Connector zu aktualisieren.
1. Rufen Sie `microsoftTeams.settings.getSettings()` auf, um Webhookeigenschaften abzurufen, einschließlich der URL.

    > [!NOTE]
    > Im Falle einer Neukonfiguration müssen Sie `microsoftTeams.settings.getSettings()` aufrufen, wenn Ihre Seite zum ersten Mal geladen wird.

1. Registrieren Sie den `microsoftTeams.settings.registerOnRemoveHandler()`-Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt.

Dieses Ereignis gibt Ihrem Dienst die Möglichkeit, Bereinigungsaktionen durchzuführen.

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

<script src="https://statics.teams.microsoft.com/sdk/v1.5.2/js/MicrosoftTeams.min.js" crossorigin="anonymous"></script>
<script src="/Scripts/jquery-1.10.2.js"></script>

<script type="text/javascript">

        function onClick() {
            microsoftTeams.settings.setValidityState(true);
        }

        microsoftTeams.initialize();
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            var radios = document.getElementsByName('notificationType');

            var eventType = '';
            if (radios[0].checked) {
                eventType = radios[0].value;
            } else {
                eventType = radios[1].value;
            }

            microsoftTeams.settings.setSettings({
                 entityId: eventType,
                contentUrl: "https://YourSite/Connector/Setup",
                removeUrl:"https://YourSite/Connector/Setup",
                 configName: eventType
                });

            microsoftTeams.settings.getSettings(function (settings) {
                // We get the Webhook URL in settings.webhookUrl which needs to be saved. 
                // This can be used later to send notification.
            });

            saveEvent.notifySuccess();
        });

        microsoftTeams.settings.registerOnRemoveHandler(function (removeEvent) {
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

Wenn Sie die Anmeldung in Ihre eingebettete Seite integrieren möchten, um den Benutzer beim Laden der Seite zu authentifizieren, finden Sie weitere Informationen unter [Authentifizierungsablauf für Registerkarten](~/tabs/how-to/authentication/auth-flow-tab.md).

> [!NOTE]
> Aus Gründen der clientübergreifenden Kompatibilität muss Ihr Code `microsoftTeams.authentication.registerAuthenticationHandlers()` mit der URL aufrufen und den Rückrufmethoden für Erfolg oder Fehler aufrufen, bevor `authenticate()` aufgerufen wird.

#### <a name="getsettings-response-properties"></a>Eigenschaften der `GetSettings`-Antwort

>[!NOTE]
>Die vom `getSettings`-Aufruf zurückgegebenen Parameter unterscheiden sich, wenn Sie diese Methode von einer Registerkarte aus aufrufen, von den in den [js-Einstellungen](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings) dokumentierten Parametern.

Die folgende Tabelle enthält die Parameter und die Details zu `GetSetting`-Antworteigenschaften:

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, wie durch Ihren Code beim Aufrufen von `setSettings()` festgelegt. |
| `configName`  | Der Konfigurationsname, wie durch Ihren Code beim Aufrufen von `setSettings()` festgelegt. |
| `contentUrl` | Die URL der Konfigurationsseite, wie durch Ihren Code beim Aufruf von `setSettings()` festgelegt. |
| `webhookUrl` | Die für den Connector erstellte Webhook-URL. Verwenden Sie die Webhook-URL zum POSTEN von strukturiertem JSON, um Karten an den Kanal zu senden. Die `webhookUrl` wird nur zurückgegeben, wenn die Anwendung erfolgreich Daten zurückgibt. |
| `appType` | Die zurückgegebenen Werte können `mail`, `groups`, oder `teams` sein und entsprechen Office 365 Mail, Office 365-Gruppen bzw. Microsoft Teams. |
| `userObjectId` | Die eindeutige ID, die dem Office 365-Benutzer entspricht, der die Einrichtung des Connectors initiiert hat. Sie sollte gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuordnen, der die Konfiguration in Ihrem Dienst eingerichtet hat. |

#### <a name="handle-edits"></a>Behandeln von Bearbeitungen

Ihr Code muss Benutzer verarbeiten, die zurückkehren, um eine vorhandene Connectorkonfiguration zu bearbeiten. Rufen Sie `microsoftTeams.settings.setSettings()` dazu bei der Erstkonfiguration mit folgenden Parametern auf:

* `entityId` ist die benutzerdefinierte ID, die angibt, was der Benutzer konfiguriert hat und wird von Ihrem Dienst verstanden.
* `configName` ist ein Name, den der Konfigurationscode abrufen kann.
* `contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration bearbeitet.

Dieser Aufruf wird im Rahmen des Speicherereignishandlers ausgeführt. Wenn die `contentUrl` geladen wird, muss Ihr Code `getSettings()` aufrufen, um Einstellungen oder Formulare in der Benutzeroberfläche der Konfiguration vorab auszufüllen.

#### <a name="handle-removals"></a>Behandeln von Entfernungen

Sie können einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Konnektorkonfiguration entfernt. Sie registrieren diesen Handler, indem Sie `microsoftTeams.settings.registerOnRemoveHandler()` aufrufen. Dieser Handler wird zum Ausführen von Bereinigungsvorgängen verwendet, z. B. zum Entfernen von Einträgen aus einer Datenbank.

### <a name="include-the-connector-in-your-manifest"></a>Einschließen des Connectors in Ihr Manifest

Laden Sie das automatisch generierte `Teams app manifest` vom Portal herunter. Führen Sie die folgenden Schritte aus, bevor Sie die App testen oder veröffentlichen:

1. [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
1. Ändern Sie den `icons`-Teil des Manifests so, dass er die Dateinamen der Symbole anstelle von URLs enthält.

Die folgende manifest.json-Datei enthält die Elemente, die zum Testen und Einreichen der App erforderlich sind:

> [!NOTE]
> Ersetzen Sie `id` und `connectorId` im folgenden Beispiel durch die GUID des Connectors.

#### <a name="example-of-manifestjson-with-connector"></a>Beispiel für manifest.json mit Connector

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
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

Um Ihren Connector zu testen, laden Sie ihn zusammen mit einer beliebigen anderen App in ein Team hoch. Sie können ein .zip-Paket erstellen, indem Sie die Manifestdatei aus den beiden Symboldateien und dem Konnektor Developer Dashboard verwenden und diese gemäß den Anweisungen unter [Einbindung des Konnektors in Ihr Manifest](#include-the-connector-in-your-manifest)ändern.

Nachdem Sie die App hochgeladen haben, öffnen Sie die Connectorliste von einem beliebigen Kanal aus. Scrollen Sie nach unten, um Ihre App im Abschnitt **Hochgeladen** anzuzeigen:

![Screenshot des Abschnitts „Hochgeladen“ im Connectordialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> Der Fluss erfolgt vollständig innerhalb Microsoft Teams als gehostete Erfahrung.

Um zu überprüfen, ob die `HttpPOST`-Aktion ordnungsgemäß funktioniert, [senden Sie Nachrichten an Ihren Connector](~/webhooks-and-connectors/how-to/connectors-using.md).

Folgen Sie der [Schritt-für-Schritt-Anleitung](../../sbs-teams-connectors.yml), um die Connectors in Microsoft Teams zu erstellen und zu testen.

## <a name="distribute-webhook-and-connector"></a>Verteilen von Webhook und Connector

1. [Richten Sie einen eingehenden Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md#create-an-incoming-webhook) direkt für Ihr Team ein.

1. Fügen Sie eine [Konfigurationsseite](~/webhooks-and-connectors/how-to/connectors-creating.md?#integrate-the-configuration-experience) hinzu, und veröffentlichen Sie Ihren eingehenden Webhook in einem Office 365-Connector.

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
