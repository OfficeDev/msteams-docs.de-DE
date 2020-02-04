---
title: Office 365-Connectors
description: Beschreibt die ersten Schritte mit Office 365-Konnektoren in Microsoft Teams
keywords: Teams o365 Connector
ms.date: 04/19/2019
ms.openlocfilehash: e26c264cc418d326e783ff0378089d2565ecbfef
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674072"
---
# <a name="creating-office-365-connectors-for-microsoft-teams"></a>Erstellen Office 365 Connectors für Microsoft Teams

>Mit Microsoft Teams-Apps können Sie Ihren vorhandenen Office 365-Connector hinzufügen oder einen neuen erstellen, der in Microsoft Teams enthalten sein soll. Weitere Informationen finden Sie unter [Erstellen eines eigenen Connectors](/outlook/actionable-messages/connectors-dev-dashboard#build-your-own-connector) .

## <a name="adding-a-connector-to-your-teams-app"></a>Hinzufügen eines Connectors zu Ihrer Teams-App

Sie können Ihren registrierten Connector als Teil Ihres Teams-App-Pakets verteilen. Ob als eigenständige Lösung oder eine von mehreren [Funktionen](~/concepts/extensibility-points.md) , die ihre Erfahrung in Microsoft Teams ermöglicht, Sie können den Connector als Teil ihrer AppSource-Übermittlung [Verpacken](~/concepts/build-and-test/apps-package.md) und [veröffentlichen](~/concepts/deploy-and-publish/apps-publish.md) , oder Sie können ihn direkt für das Hochladen in Microsoft Teams bereitstellen.

Um den Connector zu verteilen, müssen Sie sich über das [Entwickler Dashboard für Connectors](https://outlook.office.com/connectors/home/login/#/publish)registrieren. Wenn ein Connector registriert ist, wird standardmäßig angenommen, dass der Connector in allen Office 365 Produkten, die diese unterstützen, einschließlich Outlook und Microsoft Teams, funktioniert. Wenn dies _nicht_ der Fall ist und Sie einen Connector erstellen müssen, der nur in Microsoft Teams funktioniert, wenden Sie sich direkt an den [Support von Teams Store Submissions](mailto:TeamsSubSupport@microsoft.com).

> [!IMPORTANT]
> Nachdem Sie im Entwickler Dashboard für Konnektoren **Speichern** ausgewählt haben, ist Ihr Connector registriert. Wenn Sie den Connector in AppSource veröffentlichen möchten, befolgen Sie die Anweisungen unter [Veröffentlichen Ihrer Microsoft Teams-app in AppSource](~/concepts/deploy-and-publish/apps-publish.md). Wenn Sie Ihre APP nicht in AppSource veröffentlichen möchten und Sie nur direkt an Ihre Organisation verteilen möchten, können Sie dies tun, indem Sie Sie [in Ihrer Organisation veröffentlichen](#publish-connectors-for-your-organization). Wenn Sie nur in Ihrer Organisation veröffentlichen möchten, ist im Connector-Dashboard keine weitere Aktion erforderlich.

### <a name="integrating-the-configuration-experience"></a>Integrieren der Konfigurationsumgebung

Ihre Benutzer werden die gesamte Connector-Konfigurationsumgebung durchführen, ohne den Microsoft Teams-Client verlassen zu müssen. Um diese Erfahrung zu erzielen, werden die Konfigurationsseiten von Microsoft Teams direkt in einen iframe eingebettet. Die Reihenfolge der Vorgänge lautet wie folgt:

1. Der Benutzer klickt auf den Connector, um den Konfigurationsprozess zu starten.
2. Microsoft Teams lädt ihre Konfigurations Erfahrung in Einklang.
3. Der Benutzer interagiert mit ihrer Weboberfläche, um die Konfiguration abzuschließen.
4. Der Benutzer drückt "Speichern", wodurch ein Rückruf in Ihrem Code ausgelöst wird.
5. Ihr Code verarbeitet das Save-Ereignis, indem die webhook-Einstellungen abgerufen werden (unten dokumentiert). Der Code sollte dann den webhook speichern, um Ereignisse später zu veröffentlichen.

Sie können Ihre vorhandene Webkonfigurations Erfahrung wieder verwenden oder eine separate Version erstellen, die speziell in Microsoft Teams gehostet wird. Ihr Code sollte:

1. Schließen Sie das Microsoft Teams-JavaScript-SDK ein. Dadurch erhält der Codezugriff auf APIs, um allgemeine Vorgänge wie Abrufen des aktuellen Benutzers/Kanals/Team Kontexts und Initiieren von Authentifizierungs Flüssen auszuführen. Initialisieren Sie das SDK durch `microsoftTeams.initialize()`Aufrufen von.
2. Rufen `microsoftTeams.settings.setValidityState(true)` Sie an, wenn Sie die Schaltfläche speichern aktivieren möchten. Sie sollten dies als Antwort auf eine gültige Benutzereingabe wie eine Auswahl oder ein Feld Update tun.
3. Registrieren eines `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandlers, der aufgerufen wird, wenn der Benutzer auf Speichern klickt.
4. Aufrufen `microsoftTeams.settings.setSettings()` , um die Connectoreinstellungen zu speichern. Was hier gespeichert wird, ist auch, was im Konfigurationsdialogfeld angezeigt wird, wenn der Benutzer versucht, eine vorhandene Konfiguration für den Connector zu aktualisieren.
5. Aufruf `microsoftTeams.settings.getSettings()` zum Abrufen von webhook-Eigenschaften, einschließlich der URL selbst. Sie sollten dies zusätzlich zu während des Save-Ereignisses aufrufen, sollten Sie dies auch aufrufen, wenn die Seite beim ersten Mal im Fall einer Neukonfiguration geladen wird.
6. Optional Registrieren eines `microsoftTeams.settings.registerOnRemoveHandler()` Ereignishandlers, der aufgerufen wird, wenn der Benutzer den Connector entfernt. Dieses Ereignis gibt Ihrem Dienst die Möglichkeit, Bereinigungsaktionen auszuführen.

#### <a name="getsettings-response-properties"></a>`GetSettings()`Antworteigenschaften

>[!Note]
>Die Parameter, die durch `getSettings` den Aufruf hier zurückgegeben werden, unterscheiden sich, wenn Sie diese Methode auf einer Registerkarte aufrufen und von den [hier](/javascript/api/%40microsoft/teams-js/settings.settings?view=msteams-client-js-latest)dokumentierten abweichen.

| Parameter   | Details |
|-------------|---------|
| `entityId`       | Die Entitäts-ID, die vom Code beim Aufruf `setSettings()`festgelegt wird. |
| `configName`  | Der Konfigurationsname, wie vom Code beim Aufruf `setSettings()`festgelegt. |
| `contentUrl` | Die URL der Konfigurationsseite, die vom Code beim Aufruf festgelegt wird`setSettings()` |
| `webhookUrl` | Die webhook-URL, die für diesen Connector erstellt wurde. Speichern Sie die webhook-URL, und verwenden Sie Sie, um strukturiertes JSON zu veröffentlichen, um Karten an den Kanal zu senden. `webhookUrl` wird nur zurückgegeben, wenn Anwendung erfolgreich zurückgegeben wird. |
| `appType` | Die zurückgegebenen Werte werden können `mail`, `groups` bzw. `teams` entsprechend Office 365-Mail, Office 365-Gruppen oder Microsoft Teams sein. |
| `userObjectId` | Dies ist die eindeutige ID, die dem Office 365 Benutzer entspricht, der das Setup des Connectors initiiert hat. Sie sollte gesichert werden. Dieser Wert kann verwendet werden, um den Benutzer in Office 365 zuzuweisen, der die Konfiguration für den Benutzer in Ihrem Dienst eingerichtet hat. |

Wenn Sie den Benutzer als Teil des Ladens Ihrer Seite in Schritt 2 oben authentifizieren müssen, lesen Sie [diesen Link](~/tabs/how-to/authentication/auth-flow-tab.md) , um Details darüber zu erhalten, wie Sie die Anmeldung beim Einbetten Ihrer Seite integrieren können.

> [!NOTE]
> Aufgrund von clientseitigen Kompatibilitätsgründen muss Ihr Code vor dem Aufruf `microsoftTeams.authentication.registerAuthenticationHandlers()` `authenticate()`mit den URL-und Success/Failure-Rückrufmethoden aufgerufen werden.

#### <a name="handling-edits"></a>Behandeln von Bearbeitungen

Ihr Code sollte Benutzer behandeln, die zum Bearbeiten einer vorhandenen Connector-Konfiguration zurückkehren. Rufen `microsoftTeams.settings.setSettings()` Sie dazu während der anfänglichen Konfiguration mit den folgenden Parametern auf:

- `entityId`ist die benutzerdefinierte ID, die von Ihrem Dienst verstanden wird, und stellt dar, was der Benutzer konfiguriert hat.
- `configName`ist ein Anzeigename, den Ihr Konfigurationscode abrufen kann.
- `contentUrl`ist eine benutzerdefinierte URL, die geladen wird, wenn ein Benutzer eine vorhandene Connector-Konfiguration bearbeitet. Sie können diese URL verwenden, um den Code bei der Bearbeitung des Bearbeitungs Falls zu vereinfachen.

Normalerweise wird dieser Aufruf als Teil des Save-Ereignishandlers ausgeführt. Dann, wenn die `contentUrl` oben geladen wird, sollte Ihr Code aufrufen `getSettings()` , um alle Einstellungen oder Formulare in ihrer Konfigurationsbenutzeroberfläche aufzufüllen.

#### <a name="handling-removals"></a>Behandeln von Entfernungen

Sie können optional einen Ereignishandler ausführen, wenn der Benutzer eine vorhandene Connector-Konfiguration entfernt. Sie registrieren diesen Handler durch Aufrufen `microsoftTeams.settings.registerOnRemoveHandler()`von. Dieser Handler kann verwendet werden, um Bereinigungsvorgänge wie das Entfernen von Einträgen aus einer Datenbank durchzuführen.

### <a name="including-the-connector-in-your-manifest"></a>Einschließen des Konnektors in Ihr Manifest

Sie können das automatisch generierte Teams-App-Manifest aus dem Portal herunterladen. Bevor Sie es verwenden können, um Ihre APP zu testen oder zu veröffentlichen, müssen Sie jedoch folgende Schritte ausführen:

- Schließen Sie zwei Symbole ein, und befolgen Sie die Anweisungen unter [Icons](~/concepts/build-and-test/apps-package.md#icons).
- Ändern Sie `icons` den Teil des Manifests so, dass er auf die Dateinamen der Symbole anstelle von URLs verweist.

Die folgende Manifest. JSON-Datei enthält die grundlegenden Elemente, die zum Testen und übermitteln Ihrer APP erforderlich sind.

> [!NOTE]
> Ersetzen `id` Sie `connectorId` und im folgenden Beispiel durch die GUID Ihres Konnektors.

#### <a name="example-manifestjson-with-connector"></a>Beispiel Manifest. JSON mit Connector

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
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

Wenn Sie Ihren Connector testen möchten, laden Sie ihn wie bei jeder anderen app in ein Team hoch. Sie können ein ZIP-Paket mithilfe der Manifestdatei aus dem Connectors Developer Dashboard (geändert wie im vorherigen Abschnitt weitergeleitet) und den beiden Symboldateien erstellen.

Nachdem Sie die APP hochgeladen haben, öffnen Sie die Liste Konnektoren in einem beliebigen Kanal. Scrollen Sie nach unten, um Ihre APP im **hochgeladenen** Abschnitt anzuzeigen.

![Screenshot des Abschnitts "uploaded" im Dialogfeld "Connector"](~/assets/images/connectors/connector_dialog_uploaded.png)

Sie können nun die Konfigurationsumgebung starten. Beachten Sie, dass dieser Fluss vollständig innerhalb von Microsoft Teams als gehostete Erfahrung auftritt.

Um zu überprüfen `HttpPOST` , ob eine Aktion ordnungsgemäß funktioniert, [Senden Sie Nachrichten an den Connector](~/webhooks-and-connectors/how-to/connectors-using.md).

## <a name="publish-connectors-for-your-organization"></a>Veröffentlichen von Connectors für Ihre Organisation

In einigen Fällen möchten Sie die Connector-App möglicherweise nicht im öffentlichen AppSource/Store veröffentlichen, sondern nur den Benutzern in Ihrer Organisation zur Verfügung stehen. In diesen Fällen können Sie Ihre benutzerdefinierte Connector-app in den [App-Katalog Ihrer Organisation](~/concepts/deploy-and-publish/apps-publish.md)hochladen. Auf diese Weise ist ihre Connector-app nur für diese Organisation verfügbar, und Sie müssen den Connector nicht im öffentlichen Informationsspeicher veröffentlichen.

Nachdem Sie Ihr App-Paket hochgeladen haben, können Sie den Connector in einem Team konfigurieren und verwenden, indem Sie die folgenden Schritte ausführen, um aus dem App-Katalog der Organisation zu installieren:

1. Wählen Sie das Apps-Symbol in der vertikalen Navigationsleiste ganz links aus.
1. Wählen Sie im Fenster **apps** die Option **Connectors**aus.
1. Wählen Sie den Connector aus, den Sie hinzufügen möchten, und ein Popupdialogfeld wird angezeigt.
1. Wählen Sie die Leiste **zu einem Team hinzufügen** aus.
1. Geben Sie im nächsten Dialogfenster einen Team-oder Kanalnamen ein.
1. Wählen Sie in der unteren rechten Ecke des Dialogfensters die Option zum **Einrichten einer Verbindungs** Leiste aus.
1. Der Connector wird im Abschnitt &#9679;&#9679;&#9679; => *Weitere Optionen* => *Connectors* => *alle* => *Connectors für Ihr Team* für dieses Team verfügbar sein. Sie können navigieren, indem Sie zu diesem Abschnitt Scrollen oder nach der Connector-App suchen.
1. Um den Connector zu konfigurieren oder zu ändern, wählen Sie die Leiste **configure** aus.
