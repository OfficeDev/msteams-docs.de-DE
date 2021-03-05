---
title: Office 365-Connectors
description: Beschreibt, wie Sie mit Office 365 Connectors in Microsoft Teams beginnen
keywords: Teams O365-Connector
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 8f9fcc40ca0634ead0a6c5d7d0653ad4ab993860
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449255"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a>Erstellen von Office 365 Connectors für Microsoft Teams

>Mit Microsoft Teams-Apps können Sie Ihren vorhandenen Office 365 Connector hinzufügen oder einen neuen erstellen, der in Microsoft Teams enthalten ist. Weitere [Informationen finden Sie unter Build your own Connector.](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector)

## <a name="adding-a-connector-to-your-teams-app"></a>Hinzufügen eines Connectors zu Ihrer Teams-App

Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Ob als eigenständige Lösung oder [](~/concepts/extensibility-points.md) als eine von mehreren Funktionen, [](~/concepts/deploy-and-publish/apps-publish.md) die Ihre Erfahrung in Teams ermöglicht: Sie können Ihren Connector als Teil Ihrer AppSource-Übermittlung packen und veröffentlichen, oder Sie können ihn Benutzern direkt zum Hochladen in Teams bereitstellen. [](~/concepts/build-and-test/apps-package.md)

Zum Verteilen ihres Connectors müssen Sie sich über das [Connectors Developer Dashboard registrieren.](https://outlook.office.com/connectors/home/login/#/publish) Sobald ein Connector registriert wurde, wird standardmäßig davon ausgegangen, dass Ihr Connector in allen Office 365-Produkten funktioniert, die sie unterstützen, einschließlich Outlook und Teams. Wenn dies _nicht_ der Fall ist und Sie einen Connector erstellen müssen, der nur in Microsoft Teams funktioniert, kontaktieren Sie uns direkt unter [Microsoft Teams App Submissions](mailto:teamsubm@microsoft.com).

> [!IMPORTANT]
> Nachdem Sie **im Connectors** Developer Dashboard speichern auswählen, wird Ihr Connector registriert. Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, befolgen Sie die Anweisungen unter [Publish your Microsoft Teams app to AppSource](~/concepts/deploy-and-publish/apps-publish.md). Wenn Sie Ihre App nicht in AppSource veröffentlichen und stattdessen einfach nur direkt an Ihre Organisation verteilen möchten, können Sie dies tun, indem Sie sie in [Ihrer Organisation veröffentlichen.](#publish-connectors-for-your-organization) Wenn Sie nur in Ihrer Organisation veröffentlichen möchten, sind keine weiteren Aktionen im Connectordashboard erforderlich.

### <a name="integrating-the-configuration-experience"></a>Integrieren der Konfigurationserfahrung

Ihre Benutzer führen die gesamte Connectorkonfiguration aus, ohne den Teams-Client verlassen zu müssen. Um diese Erfahrung zu erzielen, betten Teams Ihre Konfigurationsseite direkt in einen iframe ein. Die Reihenfolge der Vorgänge lautet wie folgt:

1. Der Benutzer klickt auf den Connector, um mit dem Konfigurationsprozess zu beginnen.
2. Teams wird Ihre Konfigurationserfahrung in der Zeile laden.
3. Der Benutzer interagiert mit Ihrer Weberfahrung, um die Konfiguration zu vervollständigen.
4. Der Benutzer drückt auf "Speichern", wodurch ein Rückruf in Ihrem Code ausgelöst wird.
5. Ihr Code wird das Speicherereignis verarbeiten, indem die Webhookeinstellungen abgerufen werden (siehe unten). Ihr Code sollte dann den Webhook speichern, um Ereignisse später zu veröffentlichen.

Sie können Ihre vorhandene Webkonfigurationserfahrung wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet werden soll. Ihr Code sollte:

1. Schließen Sie das Microsoft Teams JavaScript SDK ein. Dadurch erhalten Sie Zugriff auf APIs, um allgemeine Vorgänge wie das Abrufen des aktuellen Benutzer-/Kanal-/Teamkontexts und das Initiieren von Authentifizierungsflüssen durchzuführen. Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.
2. Rufen `microsoftTeams.settings.setValidityState(true)` Sie auf, wenn Sie die Schaltfläche Speichern aktivieren möchten. Sie sollten dies als Antwort auf gültige Benutzereingaben, z. B. eine Auswahl oder Feldaktualisierung, tun.
3. Registrieren Sie `microsoftTeams.settings.registerOnSaveHandler()` einen Ereignishandler, der aufgerufen wird, wenn der Benutzer auf Speichern klickt.
4. Rufen `microsoftTeams.settings.setSettings()` Sie zum Speichern der Connectoreinstellungen auf. Was hier gespeichert wird, ist auch das, was im Konfigurationsdialogfeld angezeigt wird, wenn der Benutzer versucht, eine vorhandene Konfiguration für Ihren Connector zu aktualisieren.
5. Aufruf `microsoftTeams.settings.getSettings()` zum Abrufen von Webhookeigenschaften, einschließlich der URL selbst. Sie sollten dies auch während des Save-Ereignisses aufrufen, wenn Ihre Seite im Falle einer Neukonfiguration zum ersten Mal geladen wird.
6. (Optional) Registrieren Sie `microsoftTeams.settings.registerOnRemoveHandler()` einen Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt. Dieses Ereignis bietet Ihrem Dienst die Möglichkeit, bereinigende Aktionen durchzuführen.

Hier ist ein Beispiel-HTML zum Erstellen einer Connectorkonfigurationsseite ohne CSS:

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
            var removeCalled = true;
            alert("Removed" + JSON.stringify(removeEvent));
        });

</script>
```

#### <a name="getsettings-response-properties"></a>`GetSettings()` Antworteigenschaften

>[!Note]
>Die vom Aufruf hier zurückgegebenen Parameter unterscheiden sich von denen, wenn Sie diese Methode über eine Registerkarte aufrufen würden, und unterscheiden sich von denen, die `getSettings` hier [dokumentiert sind.](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true)

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, die vom Code beim Aufruf festgelegt `setSettings()` wird. |
| `configName`  | Der Konfigurationsname, der vom Code beim Aufrufen festgelegt `setSettings()` wird. |
| `contentUrl` | Die URL der Konfigurationsseite, die vom Code beim Aufrufen festgelegt wird `setSettings()` |
| `webhookUrl` | Die webhook-URL, die für diesen Connector erstellt wurde. Persist the webhook URL and use it to POST structured JSON to send cards to the channel. `webhookUrl` wird nur zurückgegeben, wenn Anwendung erfolgreich zurückgegeben wird. |
| `appType` | Die zurückgegebenen Werte werden können `mail`, `groups` bzw. `teams` entsprechend Office 365-Mail, Office 365-Gruppen oder Microsoft Teams sein. |
| `userObjectId` | Dies ist die eindeutige ID, die dem Office 365-Benutzer entspricht, der das Setup des Connectors initiiert hat. Sie sollte gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuweisen, der die Konfiguration für den Benutzer in Ihrem Dienst eingerichtet hat. |

Wenn Sie den Benutzer im Rahmen des Ladens Ihrer Seite [](~/tabs/how-to/authentication/auth-flow-tab.md) in Schritt 2 oben authentifizieren müssen, finden Sie unter diesem Link Weitere Informationen dazu, wie Sie die Anmeldung integrieren können, wenn Ihre Seite eingebettet ist.

> [!NOTE]
> Aus clientübergreifenden Kompatibilitätsgründen muss Ihr Code vor dem Aufrufen die URL und `microsoftTeams.authentication.registerAuthenticationHandlers()` die Methoden zum Erfolgreich-/Fehlerrückruf `authenticate()` aufrufen.

#### <a name="handling-edits"></a>Behandeln von Bearbeitungen

Der Code sollte wiederkehrenden Benutzern ermöglichen, eine vorhandene Connector-Konfiguration zu bearbeiten. Rufen Sie dazu während `microsoftTeams.settings.setSettings()` der Erstkonfiguration mit den folgenden Parametern auf:

- `entityId` ist die benutzerdefinierte ID, die von Ihrem Dienst verstanden wird und das darstellt, was der Benutzer konfiguriert hat.
- `configName` ist ein Anzeigename, den Der Konfigurationscode abrufen kann
- `contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration bearbeitet. Sie können diese URL verwenden, um es Ihrem Code zu erleichtern, den Bearbeitungsfall zu behandeln.

In der Regel wird dieser Aufruf als Teil des Speicherereignishandlers vorgenommen. Wenn das oben beschriebene Element geladen wird, sollte ihr Code dann aufrufen, um alle Einstellungen oder Formulare in der Konfigurationsbenutzeroberfläche `contentUrl` `getSettings()` vorab aufgefüllt zu haben.

#### <a name="handling-removals"></a>Behandeln von Entfernungen

Sie können optional einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Connectorkonfiguration entfernt. Sie registrieren diesen Handler durch Aufrufen `microsoftTeams.settings.registerOnRemoveHandler()` von . Dieser Handler kann zum Ausführen von Bereinigungsvorgängen verwendet werden, z. B. zum Entfernen von Einträgen aus einer Datenbank.

### <a name="including-the-connector-in-your-manifest"></a>Einschließlich des Connectors in Ihr Manifest

Sie können das automatisch generierte Teams-App-Manifest aus dem Portal herunterladen. Bevor Sie sie jedoch zum Testen oder Veröffentlichen Ihrer App verwenden können, müssen Sie folgendes tun:

- [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
- Ändern Sie den `icons`-Teil des Manifests so, dass er auf die Dateinamen der Symbole anstelle von URLs verweist.

Die folgende manifest.JSON-Datei enthält die grundlegenden Elemente, die zum Testen und Übermitteln Ihrer APP erforderlich sind.

> [!NOTE]
> Ersetzen Sie im folgenden Beispiel `id` und `connectorId` mit der GUID des Connectors.

#### <a name="example-manifestjson-with-connector"></a>Beispiel-manifest.JSON mit Connector

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
    "full": "This is a sample manifest for an app with a connector with an inline configuration experience.",
    "short": "This is a sample manifest for an app with a connector."
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "configurationUrl": "https://teamstodoappconnectorwithinlineconfig.azurewebsites.net/Connector/Setup",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App Long Name"
  },
  "accentColor": "#FFFFFF"
}
```

## <a name="testing-your-connector"></a>Testen des Connectors

Um den Connector zu testen, laden Sie ihn wie jede andere App in ein Team hoch. Sie können ein ZIP-Paket erstellen und dafür die (wie im vorherigen Abschnitt beschrieben modifizierte) Manifestdatei aus dem Entwicklerdashboard für Connectors sowie die beiden Symboldateien verwenden.

Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors von einem beliebigen Kanal aus. Scrollen Sie ganz nach unten bis zu Ihrer App im Abschnitt **Hochgeladenen**.

![Screenshot des Abschnitts "Hochgeladen" im Connector-Dialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

Sie können nun die Konfigurationsfunktion starten. Beachten Sie, dass dieser Fluss vollständig in Microsoft Teams als gehostete Benutzererfahrung erfolgt.

Um zu überprüfen, `HttpPOST` ob eine Aktion ordnungsgemäß funktioniert, senden Sie Nachrichten an Den [Connector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-your-organization"></a>Veröffentlichen von Connectors für Ihre Organisation

Manchmal möchten Sie Ihre Connector-App möglicherweise nicht im öffentlichen AppSource/Store veröffentlichen, sondern möchten, dass sie nur für die Benutzer in Ihrer Organisation verfügbar ist. In solchen Fällen können Sie Ihre benutzerdefinierte Connector-App in [den App-Katalog Ihrer Organisation hochladen.](~/concepts/deploy-and-publish/apps-publish.md) Auf diese Weise ist Ihre Connector-App nur für diese Organisation verfügbar, und Sie müssen Den Connector nicht im öffentlichen Store veröffentlichen.

Nachdem Sie Ihr App-Paket hochgeladen haben, kann der Connector zum Konfigurieren und Verwenden des Connectors in einem Team aus dem App-Katalog der Organisation installiert werden, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie das Apps-Symbol in der vertikalen Navigationsleiste ganz links aus.
1. Wählen Sie **im Fenster Apps** Connectors **aus.**
1. Wählen Sie den Connector aus, den Sie hinzufügen möchten, und ein Popupdialogfenster wird angezeigt.
1. Wählen Sie **die Leiste Zu einer Teamleiste hinzufügen** aus.
1. Geben Sie im nächsten Dialogfeld einen Team- oder Kanalnamen ein.
1. Wählen Sie **in der unteren rechten** Ecke des Dialogfelds die Option Connectorleiste einrichten aus.
1. Der Connector steht im Abschnitt &#9679;&#9679;&#9679; => Weitere *Optionen* Connectors Alle Connectors für Ihr Team  =>    =>    =>   für dieses Team zur Verfügung. Sie können navigieren, indem Sie zu diesem Abschnitt scrollen oder nach der Connector-App suchen.
1. Wählen Sie zum Konfigurieren oder Ändern des Connectors die **Leiste Konfigurieren** aus.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Connectors    | Beispiel für Office 365 Connector, der Benachrichtigungen an den Teams-Kanal generiert.|   [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Beispiel für generische Connectors |Beispielcode für einen generischen Connector, der einfach für jedes System angepasst werden kann, das Webhooks unterstützt.|  | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
