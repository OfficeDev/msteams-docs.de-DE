---
title: Office 365-Connectors
description: Beschreibt den Einstieg in Office 365 Connectors in Microsoft Teams
keywords: Teams O365-Connector
localization_priority: Normal
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 9eaaedf88d907dd7a7422068ab5d20450345f0e7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566810"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a>Erstellen Office 365 Connectors für Microsoft Teams

>Mit Microsoft Teams Apps können Sie Ihren vorhandenen Office 365 Connector hinzufügen oder einen neuen Connector erstellen, der in Microsoft Teams aufgenommen werden soll. Weitere Informationen finden Sie unter [Erstellen eines eigenen Connectors.](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector)

## <a name="adding-a-connector-to-your-teams-app"></a>Hinzufügen eines Connectors zu Ihrer Teams-App

Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Ob als eigenständige Lösung oder als eine von mehreren [Funktionen,](~/concepts/extensibility-points.md) die Ihre Erfahrung in Teams ermöglicht, Sie können Ihren Connector als Teil Ihrer AppSource-Übermittlung [verpacken](~/concepts/build-and-test/apps-package.md) und [veröffentlichen,](~/concepts/deploy-and-publish/apps-publish.md) oder Sie können ihn Benutzern direkt zum Hochladen innerhalb Teams zur Verfügung stellen.

Um Ihren Connector zu verteilen, müssen Sie sich über das [Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish)registrieren. Wenn ein Connector registriert ist, wird standardmäßig davon ausgegangen, dass Ihr Connector in allen Office 365 Produkten funktioniert, die ihn unterstützen, einschließlich Outlook und Teams. Wenn dies _nicht_ der Fall ist und Sie einen Connector erstellen müssen, der nur in Microsoft Teams funktioniert, kontaktieren Sie uns direkt unter [Microsoft Teams App-Einreichungen](mailto:teamsubm@microsoft.com).

> [!IMPORTANT]
> Nachdem Sie im Connectors Developer Dashboard die Option **Speichern** gewählt haben, wird Ihr Connector registriert. Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, befolgen Sie die Anweisungen unter [Veröffentlichen Ihrer Microsoft Teams-App in AppSource](~/concepts/deploy-and-publish/apps-publish.md). Wenn Sie Ihre App nicht in AppSource veröffentlichen und sondern nur direkt an Ihre Organisation verteilen möchten, können Sie dies tun, indem Sie [in Ihrer Organisation veröffentlichen.](#publish-connectors-for-your-organization) Wenn Sie nur in Ihrer Organisation veröffentlichen möchten, sind keine weiteren Aktionen im Connector-Dashboard erforderlich.

### <a name="integrating-the-configuration-experience"></a>Integration der Konfigurationserfahrung

Ihre Benutzer schließen die gesamte Connector-Konfigurationserfahrung ab, ohne den Teams Client verlassen zu müssen. Um diese Erfahrung zu erzielen, werden Teams Ihre Konfigurationsseite direkt in einen iframe einbetten. Die Reihenfolge der Operationen ist wie folgt:

1. Der Benutzer klickt auf Ihren Connector, um den Konfigurationsprozess zu starten.
2. Teams lädt Ihre Konfigurationserfahrung in einer Zeile.
3. Der Benutzer interagiert mit Ihrer Weberfahrung, um die Konfiguration abzuschließen.
4. Der Benutzer drückt auf "Speichern", was einen Rückruf in Ihrem Code auslöst.
5. Ihr Code verarbeitet das Speicherereignis, indem er die Webhook-Einstellungen abruft (unten dokumentiert). Ihr Code sollte dann den Webhook speichern, um Ereignisse später zu veröffentlichen.

Sie können Ihre vorhandene Webkonfigurationsumgebung wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet werden soll. Ihr Code sollte:

1. Schließen Sie das Microsoft Teams JavaScript SDK ein. Dadurch erhalten Sie Codezugriff auf APIs, um allgemeine Vorgänge wie das Abrufen des aktuellen Benutzer-/Kanal-/Teamkontexts und das Initiieren von Authentifizierungsflüssen auszuführen. Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.
2. Rufen `microsoftTeams.settings.setValidityState(true)` Sie an, wenn Sie die Schaltfläche Speichern aktivieren möchten. Sie sollten dies als Antwort auf gültige Benutzereingaben, z. B. eine Auswahl oder eine Feldaktualisierung, tun.
3. Registrieren Sie einen `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler, der aufgerufen wird, wenn der Benutzer auf Speichern klickt.
4. Rufen Sie `microsoftTeams.settings.setSettings()` an, um die Connectoreinstellungen zu speichern. Hier wird auch gespeichert, was im Konfigurationsdialog angezeigt wird, wenn der Benutzer versucht, eine vorhandene Konfiguration für Ihren Connector zu aktualisieren.
5. Rufen Sie `microsoftTeams.settings.getSettings()` den Aufruf zum Abrufen von Webhook-Eigenschaften, einschließlich der URL selbst, auf. Sie sollten dies aufrufen Zusätzlich zu während des Speicherereignisses, sollten Sie dies auch aufrufen, wenn Ihre Seite im Falle einer Neukonfiguration zum ersten Mal geladen wird.
6. (Optional) Registrieren Sie einen `microsoftTeams.settings.registerOnRemoveHandler()` Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt. Dieses Ereignis gibt Ihrem Dienst die Möglichkeit, Bereinigungsaktionen auszuführen.

Hier ist ein Beispiel-HTML zum Erstellen einer Connector-Konfigurationsseite ohne das CSS:

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

#### <a name="getsettings-response-properties"></a>`GetSettings()` Antworteigenschaften

>[!Note]
>Die Parameter, die vom Aufruf hier zurückgegeben `getSettings` werden, unterscheiden sich von der, wenn Sie diese Methode von einer Registerkarte aufrufen würden, und unterscheiden sich von den [hier](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true)dokumentierten .

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, die vom Code beim Aufrufen festgelegt `setSettings()` wird. |
| `configName`  | Der Konfigurationsname, der vom Code beim Aufruf festgelegt `setSettings()` wurde. |
| `contentUrl` | Die URL der Konfigurationsseite, die vom Code beim Aufruf festgelegt `setSettings()` wurde. |
| `webhookUrl` | Die webhook-URL, die für diesen Connector erstellt wurde. Belassen Sie die Webhook-URL und verwenden Sie sie, um strukturierte JSON-POST-Karten an den Kanal zu senden. `webhookUrl` wird nur zurückgegeben, wenn Anwendung erfolgreich zurückgegeben wird. |
| `appType` | Die zurückgegebenen Werte werden können `mail`, `groups` bzw. `teams` entsprechend Office 365-Mail, Office 365-Gruppen oder Microsoft Teams sein. |
| `userObjectId` | Dies ist die eindeutige ID, die dem Office 365 Benutzer entspricht, der die Einrichtung des Connectors initiiert hat. Sie sollte gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuweisen, der die Konfiguration für den Benutzer in Ihrem Dienst eingerichtet hat. |

Wenn Sie den Benutzer als Teil des Ladens Ihrer Seite in Schritt 2 oben authentifizieren müssen, finden Sie in [diesem Link](~/tabs/how-to/authentication/auth-flow-tab.md) Weitere Informationen dazu, wie Sie die Anmeldung integrieren können, wenn Ihre Seite eingebettet ist.

> [!NOTE]
> Aus clientübergreifenden Kompatibilitätsgründen muss Ihr Code `microsoftTeams.authentication.registerAuthenticationHandlers()` vor dem Aufruf mit der URL und den Erfolgs-/Fehlerrückrufmethoden aufgerufen `authenticate()` werden.

#### <a name="handling-edits"></a>Umgang mit Bearbeitungen

Der Code sollte wiederkehrenden Benutzern ermöglichen, eine vorhandene Connector-Konfiguration zu bearbeiten. Rufen Sie dazu `microsoftTeams.settings.setSettings()` während der Erstkonfiguration die folgenden Parameter auf:

- `entityId` ist die benutzerdefinierte ID, die von Ihrem Dienst verstanden wird und das darstellt, was der Benutzer konfiguriert hat.
- `configName` ist ein Anzeigename, den Ihr Konfigurationscode abrufen kann
- `contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration benimmt. Sie können diese URL verwenden, um es Ihrem Code zu erleichtern, den Bearbeitungsfall zu behandeln.

In der Regel wird dieser Aufruf als Teil des Save-Ereignishandlers durchgeführt. Wenn die `contentUrl` oben genannten Schritte ausgeführt werden, sollte der Code dann alle `getSettings()` Einstellungen oder Formulare in der Konfigurationsbenutzeroberfläche vorab auffüllen.

#### <a name="handling-removals"></a>Umgang mit Umzügen

Sie können optional einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Connectorkonfiguration entfernt. Sie registrieren diesen Handler, indem Sie `microsoftTeams.settings.registerOnRemoveHandler()` aufrufen. Dieser Handler kann verwendet werden, um Bereinigungsvorgänge auszuführen, z. B. das Entfernen von Einträgen aus einer Datenbank.

### <a name="including-the-connector-in-your-manifest"></a>Einschließen des Connectors in Ihr Manifest

Sie können das automatisch generierte Teams App-Manifest aus dem Portal herunterladen. Bevor Sie sie jedoch zum Testen oder Veröffentlichen Ihrer App verwenden können, müssen Sie Folgendes tun:

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

Sie können nun die Konfigurationsfunktion starten. Beachten Sie, dass dieser Fluss vollständig innerhalb Microsoft Teams als gehostetes Erlebnis auftritt.

Um zu überprüfen, ob eine `HttpPOST` Aktion ordnungsgemäß funktioniert, [senden Sie Nachrichten an Ihren Connector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-your-organization"></a>Veröffentlichen von Connectors für Ihre Organisation

Manchmal möchten Sie Ihre Connector-App möglicherweise nicht in der öffentlichen AppSource/Store veröffentlichen, möchten jedoch, dass sie nur für die Benutzer in Ihrer Organisation verfügbar ist. In solchen Fällen können Sie Ihre benutzerdefinierte Connector-App in [den App-Katalog](~/concepts/deploy-and-publish/apps-publish.md)Ihrer Organisation hochladen. Auf diese Weise ist Ihre Connector-App nur für diese Organisation verfügbar, und Sie müssen den Connector nicht im öffentlichen Speicher veröffentlichen.

Nachdem Sie Ihr App-Paket hochgeladen haben, können Sie den Connector aus dem App-Katalog der Organisation installieren, um den Connector in einem Team zu konfigurieren und zu verwenden, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie das Apps-Symbol in der linken vertikalen Navigationsleiste aus.
1. Wählen Sie im Fenster **Apps** **Connectors** aus.
1. Wählen Sie den Connector aus, den Sie hinzufügen möchten, und ein Popup-Dialogfenster wird angezeigt.
1. Wählen Sie die **Option Zu einer Teamleiste hinzufügen** aus.
1. Geben Sie im nächsten Dialogfenster einen Team- oder Kanalnamen ein.
1. Wählen Sie die **Verbindungsleiste** in der unteren rechten Ecke des Dialogfensters aus.
1. Der Connector ist im Abschnitt &#9679;&#9679;&#9679; => *Weitere Optionen*  =>  *Connectors*  =>  *All*  =>  *Connectors for You Team* für dieses Team verfügbar. Sie können navigieren, indem Sie zu diesem Abschnitt scrollen oder nach der Connector-App suchen.
1. Um den Connector zu konfigurieren oder zu ändern, wählen Sie die **Leiste Konfigurieren aus.**

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Connectors    | Beispiel Office 365 Connector, der Benachrichtigungen an den Teamskanal generiert.|   [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Generika-Connectors-Beispiel |Beispielcode für einen generischen Connector, der für jedes System, das Webhooks unterstützt, einfach angepasst werden kann.|  | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|
