---
title: Erstellen von Office 365-Connectors
author: laujan
description: Beschreibt die Verwendung von Office 365-Connectors in Microsoft Teams
keywords: Teams-Office365-Connector
ms.localizationpriority: high
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 9381fb9a55b6a48126e8c157040745d56708e9f8
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111612"
---
# <a name="create-office-365-connectors"></a>Erstellen von Office 365-Connectors

Mit Microsoft Teams Apps können Sie Ihren vorhandenen Office 365 Connector hinzufügen oder innerhalb Teams einen neuen erstellen. Weitere Informationen finden Sie unter [Erstellen eines eigenen Connectors](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector).

## <a name="add-a-connector-to-teams-app"></a>Fügen Sie der Teams-App einen Connector hinzu

Sie können ein [Paket](~/concepts/build-and-test/apps-package.md) erstellen und Den Connector als Teil Ihrer AppSource-Übermittlung [veröffentlichen](~/concepts/deploy-and-publish/apps-publish.md). Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Informationen zu Einstiegspunkten für die Teams-App finden Sie unter [Funktionen](~/concepts/extensibility-points.md). Sie können das Paket Benutzern auch direkt zum Hochladen in Teams bereitstellen.

Um Ihren Connector zu verteilen, registrieren Sie ihn im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).

Damit ein Konnektor nur in Microsoft Teams funktioniert, befolgen Sie die Anweisungen zum Einreichen des Konnektors im [Artikel zum Veröffentlichen Ihrer App im Microsoft Teams](~/concepts/deploy-and-publish/appsource/publish.md) Store. Ansonsten funktioniert ein registrierter Connector in allen Office 365-Produkten, die Anwendungen unterstützen, einschließlich Outlook und Teams.

> [!IMPORTANT]
> Ihr Konnektor wird registriert, nachdem Sie im Konnektor-Entwickler-Dashboard **Speichern** ausgewählt haben. Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, befolgen Sie die Anweisungen unter [Veröffentlichen Ihrer Microsoft Teams-App in AppSource](~/concepts/deploy-and-publish/apps-publish.md). Wenn Sie Ihre App nicht in AppSource veröffentlichen möchten, verteilen Sie sie direkt an die Organisation. Nach dem [Veröffentlichen von Connectors für Ihre Organisation](#publish-connectors-for-the-organization) ist keine weitere Aktion im Connector-Dashboard erforderlich.

### <a name="integrate-the-configuration-experience"></a>Integrieren Sie die Konfigurationserfahrung

Benutzer können die gesamte Konnektorkonfiguration abschließen, ohne den Teams-Client verlassen zu müssen. Um die Erfahrung zu erhalten, kann Teams Ihre Konfigurationsseite direkt in einen Iframe einbetten. Die Reihenfolge der Operationen ist wie folgt:

1. Der Benutzer wählt den Konnektor aus, um mit dem Konfigurationsprozess zu beginnen.
1. Der Benutzer interagiert mit dem Weberlebnis, um die Konfiguration abzuschließen.
1. Der Benutzer wählt **Speichern aus**, wodurch ein Rückruf im Code ausgelöst wird.

    > [!NOTE]
    >
    > * Der Code kann das Speicherereignis verarbeiten, indem er die Webhook-Einstellungen abruft. Ihr Code speichert den Webhook, um später Ereignisse zu posten.
    > * Die Konfigurationserfahrung wird inline in Teams geladen.

Sie können Ihre vorhandene Webkonfigurationserfahrung wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet wird. Ihr Code muss das Microsoft Teams JavaScript SDK enthalten. Dadurch erhält Ihr Code Zugriff auf APIs, um allgemeine Vorgänge auszuführen, z. B. das Abrufen des aktuellen Benutzer-, Kanal- oder Teamkontexts und das Initiieren von Authentifizierungsabläufen.

So integrieren Sie die Konfigurationserfahrung:

1. Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.
1. Rufen `microsoftTeams.settings.setValidityState(true)` Sie auf, um **Save zu aktivieren**.

    > [!NOTE]
    > Sie müssen als `microsoftTeams.settings.setValidityState(true)` Antwort auf die Benutzerauswahl oder Feldaktualisierung aufrufen.

1. Registrieren  `microsoftTeams.settings.registerOnSaveHandler()` Sie den Ereignishandler, der aufgerufen wird, wenn der Benutzer **Speichern auswählt**.
1. Rufen `microsoftTeams.settings.setSettings()` Sie auf, um die Connector-Einstellungen zu speichern. Die gespeicherten Einstellungen werden auch im Konfigurationsdialog angezeigt, wenn der Benutzer versucht, eine vorhandene Konfiguration für Ihren Connector zu aktualisieren.
1. Aufruf `microsoftTeams.settings.getSettings()` zum Abrufen von Webhook-Eigenschaften, einschließlich der URL.

    > [!NOTE]
    > Im Falle einer `microsoftTeams.settings.getSettings()` Neukonfiguration müssen Sie anrufen, wenn Ihre Seite zum ersten Mal geladen wird.

1. Ereignishandler `microsoftTeams.settings.registerOnRemoveHandler()` registrieren, der aufgerufen wird, wenn der Benutzer den Connector entfernt.

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

Informationen zum Authentifizieren des Benutzers beim Laden Ihrer Seite finden Sie unter [Authentifizierungsablauf](~/tabs/how-to/authentication/auth-flow-tab.md) für Registerkarten zum Integrieren der Anmeldung, wenn Ihre Seite eingebettet ist.

> [!NOTE]
> Aus Gründen der clientübergreifenden Kompatibilität `microsoftTeams.authentication.registerAuthenticationHandlers()` muss Ihr Code mit der URL und den Callback-Methoden für Erfolg oder Fehler vor dem Aufruf von aufrufen `authenticate()`.

#### <a name="getsettings-response-properties"></a>`GetSettings` antworteigenschaften

>[!NOTE]
>Die vom `getSettings` Aufruf zurückgegebenen Parameter unterscheiden sich, wenn Sie diese Methode von einer Registerkarte aus aufrufen, und unterscheiden sich von denen, die in [js settings dokumentiert sind.](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true)

Die folgende Tabelle enthält die Parameter und die Details der `GetSetting` Antworteigenschaften:

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, wie durch Ihren Code beim Aufrufen festgelegt `setSettings()`. |
| `configName`  | Der Konfigurationsname, wie durch Ihren Code beim Aufrufen festgelegt `setSettings()`. |
| `contentUrl` | Die URL der Konfigurationsseite, wie sie durch Ihren Code beim Aufruf von festgelegt wird `setSettings()`. |
| `webhookUrl` | Die für den Connector erstellte Webhook-URL. Verwenden Sie die Webhook-URL, um strukturiertes JSON zu POST, um Karten an den Kanal zu senden. Der `webhookUrl` wird nur zurückgegeben, wenn die Anwendung erfolgreich Daten zurückgibt. |
| `appType` | Die zurückgegebenen Werte können `mail`, `groups`, oder `teams` entsprechend Office 365 Mail, Office 365 Groups bzw. Microsoft Teams sein. |
| `userObjectId` | Die eindeutige ID, die dem Office 365-Benutzer entspricht, der die Einrichtung des Connectors initiiert hat. Es muss gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuordnen, der die Konfiguration in Ihrem Dienst eingerichtet hat. |

#### <a name="handle-edits"></a>Bearbeiten bearbeiten

Ihr Code muss Benutzer verarbeiten, die zurückkehren, um eine vorhandene Connector-Konfiguration zu bearbeiten. Rufen Sie dazu `microsoftTeams.settings.setSettings()` bei der Erstkonfiguration mit folgenden Parametern auf:

* `entityId` ist die benutzerdefinierte ID, die darstellt, was der Benutzer konfiguriert und von Ihrem Dienst verstanden hat.
* `configName` ist ein Name, den der Konfigurationscode abrufen kann.
* `contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connector-Konfiguration bearbeitet.

Dieser Aufruf erfolgt als Teil Ihres save-Event-Handlers. Wenn dann `contentUrl` geladen wird, muss Ihr Code aufrufen, um alle Einstellungen `getSettings()` oder Formulare in Ihrer Konfigurationsbenutzeroberfläche vorab auszufüllen.

#### <a name="handle-removals"></a>Umzüge bearbeiten

Sie können einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Konnektorkonfiguration entfernt. Sie registrieren diesen Handler, indem Sie aufrufen `microsoftTeams.settings.registerOnRemoveHandler()`. Dieser Handler wird zum Ausführen von Bereinigungsvorgängen verwendet, z. B. zum Entfernen von Einträgen aus einer Datenbank.

### <a name="include-the-connector-in-your-manifest"></a>Fügen Sie den Connector in Ihr Manifest ein

Laden Sie die automatisch generierte `Teams app manifest` vom Portal herunter. Führen Sie die folgenden Schritte aus, bevor Sie die App testen oder veröffentlichen:

1. [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
1. Ändern Sie den Teil des `icons` Manifests so, dass er die Dateinamen der Symbole anstelle von URLs enthält.

Die folgende manifest.json-Datei enthält die Elemente, die zum Testen und Einreichen der App erforderlich sind:

> [!NOTE]
> Ersetzen Sie `id` und `connectorId` im folgenden Beispiel durch die GUID des Connectors.

#### <a name="example-of-manifestjson-with-connector"></a>Beispiel für manifest.json mit Konnektor

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

## <a name="enable-or-disable-connectors-in-teams"></a>Aktivieren oder deaktivieren Sie Konnektoren in Teams

Das Exchange Online PowerShell V2-Modul verwendet moderne Authentifizierung und arbeitet mit Multi-Factor-Authentifizierung, MFA genannt, für die Verbindung mit allen Exchange-bezogenen PowerShell-Umgebungen in Microsoft 365. Administratoren können Exchange Online PowerShell verwenden, um Connectors für einen gesamten Mandanten oder ein bestimmtes Gruppenpostfach zu deaktivieren, was sich auf alle Benutzer in diesem Mandanten oder Postfach auswirkt. Es ist nicht möglich, für einige und andere nicht zu deaktivieren. Außerdem sind Konnektoren für die Government Community Cloud, sogenannte GCC-Mandanten, standardmäßig deaktiviert.

Die Einstellung auf Mandantenebene überschreibt die Einstellung auf Gruppenebene. Wenn ein Administrator beispielsweise Konnektoren für die Gruppe aktiviert und sie auf dem Mandanten deaktiviert, werden Konnektoren für die Gruppe deaktiviert. Um einen Connector in Teams zu aktivieren, [stellen Sie mithilfe der modernen Authentifizierung mit oder ohne MFA eine Verbindung mit Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) her.

### <a name="commands-to-enable-or-disable-connectors"></a>Befehle zum Aktivieren oder Deaktivieren von Connectors

Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:

* So deaktivieren Sie Konnektoren für den Mandanten: `Set-OrganizationConfig -ConnectorsEnabled:$false`.
* Umsetzbare Nachrichten für den Mandanten zu deaktivieren: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.
* Führen Sie die folgenden Befehle aus, um Konnektoren für Teams zu aktivieren:
  * `Set-OrganizationConfig -ConnectorsEnabled:$true`
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

Weitere Informationen zum Austausch von PowerShell-Modulen finden Sie unter [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true). Um Outlook-Connectors zu aktivieren oder zu deaktivieren, [verbinden Sie Apps mit Ihren Gruppen in Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab).

## <a name="test-your-connector"></a>Testen Sie Ihren Konnektor

Um Ihren Konnektor zu testen, laden Sie ihn mit einer beliebigen anderen App in ein Team hoch. Sie können ein ZIP-Paket erstellen, indem Sie die Manifestdatei aus den beiden Symboldateien und Konnektoren im Entwickler-Dashboard verwenden, die wie unter [Einbeziehen des Konnektors in Ihr Manifest beschrieben geändert werden](#include-the-connector-in-your-manifest).

Nachdem Sie die App hochgeladen haben, öffnen Sie die Connector-Liste von einem beliebigen Kanal aus. Scrollen Sie nach unten, um Ihre App im Abschnitt **Hochgeladen** anzuzeigen:

![Screenshot eines hochgeladenen Abschnitts im Connector-Dialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> Der Flow erfolgt vollständig innerhalb von Microsoft Teams als gehostete Erfahrung.

Um zu überprüfen, ob die `HttpPOST` Aktion ordnungsgemäß funktioniert, [senden Sie Nachrichten an Ihren Connector](~/webhooks-and-connectors/how-to/connectors-using.md).

Folgen Sie der [Schritt-für-Schritt-Anleitung](../../sbs-teams-connectors.yml), um die Konnektoren in Ihren Microsoft Teams zu erstellen und zu testen.

## <a name="publish-connectors-for-the-organization"></a>Veröffentlichen Sie Konnektoren für die Organisation

Wenn Sie möchten, dass der Connector nur für die Benutzer in Ihrer Organisation verfügbar ist, können Sie Ihre benutzerdefinierte Connector-App in den App-Katalog Ihrer [Organisation hochladen](~/concepts/deploy-and-publish/apps-publish.md).

Nachdem Sie das App-Paket hochgeladen haben, um den Connector in einem Team zu konfigurieren und zu verwenden, installieren Sie den Connector aus dem App-Katalog der Organisation.

So richten Sie einen Konnektor ein:

1. Wählen Sie in der linken Navigationsleiste **Apps** aus.
1. Wählen Sie im Abschnitt **Apps** die Option **Konnektoren aus**.
1. Wählen Sie den Connector aus, den Sie hinzufügen möchten. Ein Popup-Dialogfenster wird angezeigt.
1. Wählen Sie im **Dropdown-Menü Zu einem Team hinzufügen aus**.
1. Geben Sie im Suchfeld einen Team- oder Kanalnamen ein.
1. Wählen **Sie Konnektor** einrichten aus dem Dropdown-Menü in der unteren rechten Ecke des Dialogfensters.

> [!IMPORTANT]
> Derzeit sind benutzerdefinierte Konnektoren in der Government Community Cloud (GCC), GCC-High und dem Verteidigungsministerium (DOD) nicht verfügbar.

Der Konnektor ist im Abschnitt &#9679;&#9679;&#9679; > **Weitere Optionen** > **Konnektoren** > **Alle** > **Konnektoren für Ihr Team für dieses** Team. Sie können navigieren, indem Sie zu diesem Abschnitt scrollen oder nach der Connector-App suchen. Um den Connector zu konfigurieren oder zu ändern, wählen Sie **Konfigurieren**.

## <a name="distribute-webhook-and-connector"></a>Webhook und Konnektor verteilen

1. [Richten Sie einen eingehenden Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md#create-an-incoming-webhook) direkt für Ihr Team ein.
1. Fügen Sie eine [Konfigurationsseite](~/webhooks-and-connectors/how-to/connectors-creating.md?#integrate-the-configuration-experience) hinzu, und [veröffentlichen Sie Ihren eingehenden Webhook](~/webhooks-and-connectors/how-to/connectors-creating.md#publish-connectors-for-the-organization) in einem Office 365 Connector.
1. Verpacken und veröffentlichen Sie Ihren Connector als Teil Ihrer [AppSource](~/concepts/deploy-and-publish/office-store-guidance.md)-Übermittlung.

## <a name="code-sample"></a>Codebeispiel

Die folgende Tabelle enthält den Beispielnamen und die Beschreibung:

|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Connectors | Beispiel für Office 365 Connector, der Benachrichtigungen an Teams Kanal generiert.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Beispiel für generische Konnektoren |Beispielcode für einen generischen Konnektor, der einfach an jedes System angepasst werden kann, das Webhooks unterstützt.| | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../sbs-teams-connectors.yml) zum Erstellen und Testen von Connectors in Teams.

## <a name="see-also"></a>Siehe auch

* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
