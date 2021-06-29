---
title: Erstellen von Office 365-Connectors
author: laujan
description: Beschreibt die ersten Schritte mit Office 365 Connectors in Microsoft Teams
keywords: Teams O365-Connector
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/16/2021
ms.openlocfilehash: 28a2b35e868baf34e35a11a00e10b30b0f09c236
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179755"
---
# <a name="create-office-365-connectors"></a>Erstellen von Office 365-Connectors

Mit Microsoft Teams Apps können Sie Ihren vorhandenen Office 365 Connector hinzufügen oder einen neuen connector in Teams erstellen. Weitere Informationen finden Sie unter [Erstellen Eines eigenen Connectors.](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector)

## <a name="add-a-connector-to-teams-app"></a>Hinzufügen eines Connectors zu Teams App

Sie können Ihren Connector im Rahmen Ihrer AppSource-Übermittlung [verpacken](~/concepts/build-and-test/apps-package.md) und [veröffentlichen.](~/concepts/deploy-and-publish/apps-publish.md) Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Informationen zu Einstiegspunkten für Teams App finden Sie unter ["Funktionen".](~/concepts/extensibility-points.md) Sie können das Paket benutzern auch direkt zum Hochladen in Teams bereitstellen.

Um Den Connector zu verteilen, müssen Sie sich über [das Connectors Developer Dashboard](https://outlook.office.com/connectors/home/login/#/publish)registrieren. Wenn ein Connector registriert ist, wird davon ausgegangen, dass er in allen Office 365 Produkten funktioniert, die Anwendungen unterstützen, einschließlich Outlook und Teams. Wenn dies nicht der Fall ist und Sie einen Connector erstellen müssen, der nur in Microsoft Teams funktioniert, wenden Sie sich an: [Microsoft Teams E-Mail-Adresse für App-Übermittlungen.](mailto:teamsubm@microsoft.com)

> [!IMPORTANT]
> Ihr Connector wird registriert, nachdem Sie im Connectors Developer Dashboard die Option **"Speichern"** ausgewählt haben. Wenn Sie Ihren Connector in AppSource veröffentlichen möchten, folgen Sie den Anweisungen in der [Veröffentlichung Ihrer Microsoft Teams-App in AppSource.](~/concepts/deploy-and-publish/apps-publish.md) Wenn Sie Ihre App nicht in AppSource veröffentlichen möchten, verteilen Sie sie direkt an die Organisation. Nach der [Veröffentlichung von Connectors für Ihre Organisation](#publish-connectors-for-the-organization)sind keine weiteren Aktionen im Connector-Dashboard erforderlich.

### <a name="integrate-the-configuration-experience"></a>Integrieren der Konfigurationsumgebung

Benutzer können die gesamte Connectorkonfiguration abschließen, ohne den Teams-Client verlassen zu müssen. Um die Erfahrung zu erhalten, können Teams Ihre Konfigurationsseite direkt in einen iframe einbetten. Die Reihenfolge der Vorgänge lautet wie folgt:

1. Der Benutzer wählt den Connector aus, um mit dem Konfigurationsprozess zu beginnen.
1. Der Benutzer interagiert mit der Weboberfläche, um die Konfiguration abzuschließen.
1. Der Benutzer wählt **Speichern** aus, wodurch ein Rückruf im Code ausgelöst wird.

    > [!NOTE]
    > * Der Code kann das Speicherereignis verarbeiten, indem die Webhook-Einstellungen abgerufen werden. Ihr Code speichert den Webhook, um Ereignisse später zu posten.
    > * Die Konfigurationsoberfläche wird inline in Teams geladen.

Sie können Ihre vorhandene Webkonfigurationsoberfläche wiederverwenden oder eine separate Version erstellen, die speziell in Teams gehostet werden soll. Ihr Code muss das Microsoft Teams JavaScript SDK enthalten. Dadurch erhält Ihr Code Zugriff auf APIs, um allgemeine Vorgänge auszuführen, z. B. den aktuellen Benutzer-, Kanal- oder Teamkontext abzurufen und Authentifizierungsflüsse zu initiieren.

**So integrieren Sie die Konfigurationsumgebung**

1. Initialisieren Sie das SDK durch Aufrufen von `microsoftTeams.initialize()`.
1. Aufruf `microsoftTeams.settings.setValidityState(true)` zum Aktivieren von **Save**.

    > [!NOTE]
    > Sie müssen `microsoftTeams.settings.setValidityState(true)` als Antwort auf eine Aktualisierung der Benutzerauswahl oder des Felds aufrufen.

1. Registrieren Sie  `microsoftTeams.settings.registerOnSaveHandler()` den Ereignishandler, der aufgerufen wird, wenn der Benutzer **"Speichern"** auswählt.
1. Aufruf `microsoftTeams.settings.setSettings()` zum Speichern der Connectoreinstellungen. Die gespeicherten Einstellungen werden auch im Konfigurationsdialogfeld angezeigt, wenn der Benutzer versucht, eine vorhandene Konfiguration für Ihren Connector zu aktualisieren.
1. Aufrufen zum Abrufen von `microsoftTeams.settings.getSettings()` Webhook-Eigenschaften, einschließlich der URL.

    > [!NOTE]
    > Sie müssen bei `microsoftTeams.settings.getSettings()` der Neukonfiguration aufrufen, wann die Seite zum ersten Mal geladen wird.

1. Registrieren Sie `microsoftTeams.settings.registerOnRemoveHandler()` den Ereignishandler, der aufgerufen wird, wenn der Benutzer den Connector entfernt.

Dieses Ereignis bietet Ihrem Dienst die Möglichkeit, alle Bereinigungsaktionen auszuführen.

Der folgende Code enthält ein HTML-Beispiel zum Erstellen einer Connectorkonfigurationsseite ohne den Kundendienst und Support:

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

Informationen zum Authentifizieren des Benutzers als Teil des Ladens ihrer Seite finden Sie im [Authentifizierungsfluss für Registerkarten,](~/tabs/how-to/authentication/auth-flow-tab.md) um die Anmeldung zu integrieren, wenn Ihre Seite eingebettet ist.

> [!NOTE]
> Aus Gründen der clientübergreifenden Kompatibilität muss Ihr Code `microsoftTeams.authentication.registerAuthenticationHandlers()` vor dem Aufrufen mit der URL und den Rückrufmethoden für Erfolg oder Fehler `authenticate()` aufrufen.

#### <a name="getsettings-response-properties"></a>`GetSettings` Antworteigenschaften

>[!NOTE]
>Die vom Aufruf zurückgegebenen Parameter `getSettings` unterscheiden sich, wenn Sie diese Methode über eine Registerkarte aufrufen, und unterscheiden sich von den parametern, die in den [JS-Einstellungen](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest&preserve-view=true)dokumentiert sind.

Die folgende Tabelle enthält die Parameter und die Details der `GetSetting` Antworteigenschaften:

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, die vom Code beim Aufrufen festgelegt `setSettings()` wird. |
| `configName`  | Der Konfigurationsname, wie er vom Code beim Aufrufen festgelegt `setSettings()` wird. |
| `contentUrl` | Die URL der Konfigurationsseite, die vom Code beim Aufrufen festgelegt `setSettings()` wird. |
| `webhookUrl` | Die für den Connector erstellte Webhook-URL. Verwenden Sie die Webhook-URL, um strukturierten JSON-Code zu POSTEN, um Karten an den Kanal zu senden. Wird `webhookUrl` nur zurückgegeben, wenn die Anwendung Daten erfolgreich zurückgibt. |
| `appType` | Die zurückgegebenen Werte können den `mail` `groups` Office 365 `teams` E-Mail-, Office 365- oder Microsoft Teams entsprechen. |
| `userObjectId` | Die eindeutige ID, die dem Office 365 Benutzer entspricht, der die Einrichtung des Connectors initiiert hat. Sie muss gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuordnen, der die Konfiguration in Ihrem Dienst eingerichtet hat. |

#### <a name="handle-edits"></a>Bearbeiten behandeln

Ihr Code muss Benutzer verarbeiten, die zurückkehren, um eine vorhandene Connectorkonfiguration zu bearbeiten. Rufen Sie dazu `microsoftTeams.settings.setSettings()` während der Anfänglichen Konfiguration die folgenden Parameter auf:

- `entityId` ist die benutzerdefinierte ID, die darstellt, was der Benutzer von Ihrem Dienst konfiguriert und verstanden hat.
- `configName` ist ein Name, den Konfigurationscode abrufen kann.
- `contentUrl` ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connectorkonfiguration bearbeitet.

Dieser Aufruf erfolgt als Teil des Speicherereignishandlers. Wenn der Code geladen wird, muss er dann `contentUrl` aufgerufen werden, um alle Einstellungen oder Formulare `getSettings()` in der Konfigurationsbenutzeroberfläche vorab auszufüllen.

#### <a name="handle-removals"></a>Behandeln von Entfernungen

Sie können einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Connectorkonfiguration entfernt. Sie registrieren diesen Handler durch Aufrufen `microsoftTeams.settings.registerOnRemoveHandler()` von . Dieser Handler wird zum Ausführen von Bereinigungsvorgängen verwendet, z. B. zum Entfernen von Einträgen aus einer Datenbank.

### <a name="include-the-connector-in-your-manifest"></a>Einschließen des Connectors in Das Manifest

Laden Sie das automatisch generierte `Teams app manifest` Aus dem Portal herunter. Führen Sie die folgenden Schritte aus, bevor Sie die App testen oder veröffentlichen:

1. [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
1. Ändern Sie den `icons` Teil des Manifests so, dass er die Dateinamen der Symbole anstelle von URLs enthält.

Die folgende manifest.jszur Datei enthält die Elemente, die zum Testen und Übermitteln der App erforderlich sind:

> [!NOTE]
> Ersetzen Sie `id` im folgenden Beispiel die `connectorId` GUID des Connectors.

#### <a name="example-of-manifestjson-with-connector"></a>Beispiel für manifest.jsmit Connector

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

## <a name="enable-or-disable-connectors-in-teams"></a>Aktivieren oder Deaktivieren von Connectors in Teams

Das Exchange Online PowerShell V2-Modul verwendet moderne Authentifizierung und arbeitet mit mehrstufiger Authentifizierung, die als MFA bezeichnet wird, um eine Verbindung mit allen Exchange zugehörigen PowerShell-Umgebungen in Microsoft 365 herzustellen. Administratoren können Exchange Online PowerShell verwenden, um Connectors für einen ganzen Mandanten oder ein bestimmtes Gruppenpostfach zu deaktivieren, was sich auf alle Benutzer in diesem Mandanten oder Postfach auswirkt. Es ist nicht möglich, für einige und nicht für andere zu deaktivieren. Außerdem sind Connectors standardmäßig für Government Community Cloud deaktiviert, die als GCC Mandanten bezeichnet werden.

Die Einstellung auf Mandantenebene setzt die Einstellung auf Gruppenebene außer Kraft. Wenn ein Administrator beispielsweise Connectors für die Gruppe aktiviert und auf dem Mandanten deaktiviert, sind Connectors für die Gruppe deaktiviert. Um einen Connector in Teams zu aktivieren, stellen Sie mithilfe der modernen Authentifizierung mit oder ohne MFA eine Verbindung mit [Exchange Online PowerShell her.](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true)

### <a name="commands-to-enable-or-disable-connectors"></a>Befehle zum Aktivieren oder Deaktivieren von Connectors

Führen Sie die folgenden Befehle in Exchange Online PowerShell aus:

* So deaktivieren Sie Connectors für den Mandanten: `Set-OrganizationConfig -ConnectorsEnabled:$false` .
* So deaktivieren Sie Nachrichten mit Aktionen für den Mandanten: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false` .
* Führen Sie die folgenden Befehle aus, um Connectors für Teams zu aktivieren:
  * `Set-OrganizationConfig -ConnectorsEnabled:$true `
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

Weitere Informationen zum Austausch von PowerShell-Modulen finden Sie unter ["Set-OrganizationConfig".](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true) Um Outlook Connectors zu aktivieren oder zu deaktivieren, [verbinden Sie Apps mit Ihren Gruppen in Outlook.](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab?ui=en-us&rs=en-us&ad=us)

## <a name="test-your-connector"></a>Testen des Connectors

Laden Sie den Connector mit einer anderen App in ein Team hoch, um den Connector zu testen. Sie können ein .zip-Paket mithilfe der Manifestdatei aus den beiden Symboldateien und Connectors Erstellen Entwicklerdashboard, geändert wie unter ["Einschließen des Connectors in Ihr Manifest"](#include-the-connector-in-your-manifest)angegeben.

Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors aus einem beliebigen Kanal. Scrollen Sie nach unten, um Ihre App im Abschnitt **"Hochgeladen"** anzuzeigen:

![Screenshot eines hochgeladenen Abschnitts im Dialogfeld "Connector"](~/assets/images/connectors/connector_dialog_uploaded.png)

> [!NOTE]
> Der Fluss erfolgt vollständig innerhalb Microsoft Teams als gehostete Oberfläche.

Um zu überprüfen, ob die `HttpPOST` Aktion ordnungsgemäß funktioniert, [senden Sie Nachrichten an den Connector.](~/webhooks-and-connectors/how-to/connectors-using.md)

## <a name="publish-connectors-for-the-organization"></a>Veröffentlichen von Connectors für die Organisation

Wenn der Connector nur für die Benutzer in Ihrer Organisation verfügbar sein soll, können Sie Ihre benutzerdefinierte Connector-App in den [App-Katalog](~/concepts/deploy-and-publish/apps-publish.md)Ihrer Organisation hochladen.

Nachdem Sie das App-Paket hochgeladen haben, um den Connector in einem Team zu konfigurieren und zu verwenden, installieren Sie den Connector aus dem App-Katalog der Organisation.

**So richten Sie einen Connector ein**

1. Wählen Sie in der linken Navigationsleiste **Apps** aus.
1. Wählen Sie im Abschnitt **"Apps"** **Connectors** aus.
1. Wählen Sie den Connector aus, den Sie hinzufügen möchten. Ein Popup-Dialogfeld wird angezeigt.
1. Wählen Sie im Dropdownmenü die Option **"Zu einem Team hinzufügen"** aus.
1. Geben Sie im Suchfeld einen Team- oder Kanalnamen ein.
1. Wählen Sie im Dropdownmenü in der unteren rechten Ecke des Dialogfelds die Option **"Connector einrichten"** aus.

Der Connector ist im Abschnitt &#9679;&#9679;&#9679; > **Weitere Optionen** Connectors  >    >  **alle** Connectors für Ihr  >  **Team** für dieses Team verfügbar. Sie können navigieren, indem Sie zu diesem Abschnitt scrollen oder nach der Connector-App suchen. Um den Connector zu konfigurieren oder zu ändern, wählen Sie **Konfigurieren** aus.

## <a name="distribute-webhook-and-connector"></a>Verteilen von Webhook und Connector

1. [Richten Sie einen eingehenden Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md?branch=pr-en-us-3076#create-incoming-webhook) direkt für Ihr Team ein.
1. Fügen Sie eine [Konfigurationsseite](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#integrate-the-configuration-experience) hinzu, und [veröffentlichen Sie Ihren eingehenden Webhook](~/webhooks-and-connectors/how-to/connectors-creating.md?branch=pr-en-us-3076#publish-connectors-for-the-organization) in einem O365-Connector.
1. Verpacken und veröffentlichen Sie Ihren Connector als Teil Ihrer [AppSource-Übermittlung.](~/concepts/deploy-and-publish/office-store-guidance.md)

## <a name="code-sample"></a>Codebeispiel

Die folgende Tabelle enthält den Beispielnamen und dessen Beschreibung:

|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Connectors    | Beispiel Office 365 Connector, der Benachrichtigungen an Teams Kanal generiert.|   [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-todo-notification/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-github-notification/nodejs)|
| Beispiel für generische Connectors |Beispielcode für einen generischen Connector, der für jedes System, das Webhooks unterstützt, einfach angepasst werden kann.|  | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/connector-generic/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
