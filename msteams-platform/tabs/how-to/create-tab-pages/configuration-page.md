---
title: Erstellen einer Konfigurationsseite
author: laujan
description: ''
keywords: Teams-Registerkartengruppe Kanal konfigurierbar
ms.topic: conceptualF
ms.author: laujan
ms.openlocfilehash: c7b6b636a342c650667a1131e7899908744beedf
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674086"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Bei einer Konfigurationsseite handelt es sich um einen speziellen Inhaltstyp der [Inhaltsseite](content-page.md) , mit dem Ihre Benutzer einen Aspekt Ihrer Teams-App konfigurieren können. Diese werden normalerweise als Bestandteil von verwendet:

* Eine Kanal-oder Gruppenchat-Registerkarte – auf der Konfigurationsseite können Sie Informationen von Ihren Benutzern sammeln `contentUrl` und die anzuzeigende Inhaltsseite festlegen.
* Eine [Messaging Erweiterung](~/messaging-extensions/what-are-messaging-extensions.md)
* Ein [Office 365 Verbinder](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="configuring-a-channel-or-group-chat-tab"></a>Konfigurieren einer Kanal-oder Gruppenchat-Registerkarte

Auf einer Konfigurationsseite wird die Inhaltsseite darüber informiert, wie Sie gerendert werden soll. Ihre Anwendung muss auf das [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) verweisen und `microsoft.initialize()`den Anruf tätigen. Außerdem müssen Ihre URLs sichere HTTPS-Endpunkte und in der Cloud verfügbar sein. Unten sehen Sie ein Beispiel für eine Konfigurationsseite.

```html
<head>
<script src='https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
</head>
    <body>
        <button onclick="(document.getElementById('icon').src = '/images/iconGray.png'); colorClickGray()">Select Gray</button>
        <img id="icon" src="/images/teamsIcon.png" alt="icon" style="width:100px" />
        <button onclick="(document.getElementById('icon').src = '/images/iconRed.png'); colorClickRed()">Select Red</button>

        <script>
            microsoftTeams.initialize();
            let saveGray = () => {
                microsoftTeams.settings.registerOnSaveHandler((saveEvent) => {
                    microsoftTeams.settings.setSettings({
                        websiteUrl: "https://yourWebsite.com",
                        contentUrl: "https://yourWebsite.com/gray",
                        entityId: "grayIconTab",
                        suggestedDisplayName: "MyNewTab"
                    });
                    saveEvent.notifySuccess();
                });
            }
            let saveRed = () => {
                microsoftTeams.settings.registerOnSaveHandler((saveEvent) => {
                    microsoftTeams.settings.setSettings({
                        websiteUrl: "https://yourWebsite.com",
                        contentUrl: "https://yourWebsite.com/red",
                        entityId: "redIconTab",
                        suggestedDisplayName: "MyNewTab"
                    });
                    saveEvent.notifySuccess();
                });
            }

            let gr = document.getElementById("gray").style;
            let rd = document.getElementById("red").style;

            const colorClickGray = () => {
                gr.display = "block";
                rd.display = "none";
                microsoftTeams.settings.setValidityState(true);
                saveGray()
            }

            const colorClickRed = () => {
                rd.display = "block";
                gr.display = "none";
                microsoftTeams.settings.setValidityState(true);
                saveRed();
            }
        </script>
    </body>

...
```

Hier werden dem Benutzer zwei Optionsschaltflächen angezeigt, **Wählen Sie grau** aus, oder **Wählen Sie Rot aus** , um den Registerkarteninhalt mit einem roten oder grauen Symbol anzuzeigen. Die Auswahl der relativen Schalt `saveGray()` Fläche `saveRed()` wird ausgelöst oder ruft Folgendes auf:

1. Der `settings.setValidityState(true)` ist auf true festgelegt.
1. Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
1. Die Schaltfläche **Speichern** auf der Konfigurationsseite der APP, die in Teams hochgeladen wurde, ist aktiviert.

Mit diesem Code können Teams wissen, dass die Konfigurationsanforderungen erfüllt wurden und die Installation fortgesetzt werden kann. Bei **Save**werden die Parameter von `settings.setSettings()` festgelegt, wie durch die `Settings` Schnittstelle für die aktuelle Instanz definiert (siehe [Einstellungen-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest) ). Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Wenn ein Speicher Handler mit `microsoftTeams.settings.registerOnSaveHandler()`registriert wurde, muss der Rückruf aufrufen `saveEvent.notifySuccess()` oder `saveEvent.notifyFailure()` das Ergebnis der Konfiguration angeben.
>* Wenn kein Speicher Handler registriert wurde, wird `saveEvent.notifySuccess()` der Anruf automatisch sofort ausgeführt, sobald der Benutzer die Schaltfläche **Speichern** auswählt.

### <a name="get-context-data-for-your-tab-settings"></a>Abrufen von Kontextdaten für die Registerkarteneinstellungen

Für Ihre Registerkarte sind möglicherweise Kontextinformationen erforderlich, um relevante Inhalte anzuzeigen. Kontextinformationen können die Attraktivität Ihrer Registerkarte weiter verbessern, indem Sie eine Benutzerfreundlichkeit bieten, die Ihnen angepasst ist.

Die [Kontext Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) für Teams definiert die Eigenschaften, die für Ihre Registerkartenkonfiguration verwendet werden können. Sie können die Werte von Kontextdaten Variablen auf zwei Arten erfassen:

1. Fügen Sie Platzhalter für URL- `configurationURL`Abfragezeichenfolgen in das Manifest ein.

1. Verwenden Sie die [Teams-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) `microsoftTeams.getContext((context) =>{}` -Methode.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Einfügen von Platzhaltern im`configurationURL`

Platzhalter für die Kontext Schnittstelle können ihrer Basis `configurationUrl`hinzugefügt werden. Zum Beispiel:

##### <a name="base-url"></a>Basis-URL

```json
...
"configurationUrl": "https://yourWebsite/config",
...
```

#### <a name="base-url-with-query-strings"></a>Basis-URL mit Abfragezeichenfolgen

```json
...
"configurationUrl": "https://yourWebsite/config?team={teamId}&channel={channelId}&{locale}"
...
```

Nachdem die Seite hochgeladen wurde, werden die Platzhalter für die Abfragezeichenfolge von Microsoft Teams mit den entsprechenden Werten aktualisiert. Sie können Logik in Ihre Konfigurationsseite einbeziehen, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN-Webdocs. Nachfolgend finden Sie ein Beispiel zum Extrahieren eines Werts aus der obigen `configurationURL` Eigenschaft:

```html
<script>
   microsoftTeams.initialize();
   const getId = () => {
        let urlParams = new URLSearchParams(document.location.search.substring(1));
        let blueTeamId = urlParams.get('team');
        return blueTeamId
    }
//For testing, you can invoke the following to view the pertinent value:
document.write(getId());
</script>

```

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Verwenden der `getContext()` -Funktion zum Abrufen des Kontexts

Wenn die `microsoftTeams.getContext((context) => {})` Funktion aufgerufen wird, ruft Sie die [Kontext Schnittstelle](/javascript/api/@microsoft/teams-js//microsoftteams.context?view=msteams-client-js-latest)ab. Sie können diese Funktion zur Konfigurationsseite hinzufügen, um Kontext Werte abzurufen:

```html

    <!-- `userPrincipalName` will render in the span with the id "user". -->

    <span id="user"></span>
    ...
    <script>
        microsoftTeams.getContext((context) =>{
            let userId = document.getElementById('user');
            userId.innerHTML = context.userPrincipalName;
        });
    </script>
    ...
```

## <a name="context-and-authentication"></a>Kontext und Authentifizierung

Möglicherweise benötigen Sie eine Authentifizierung, bevor Sie einem Benutzer die Konfiguration Ihrer APP erlauben, oder Ihre Inhalte können Quellen enthalten, die über eigene Authentifizierungsprotokolle verfügen. Informationen zum Erstellen von Authentifizierungsanforderungen und Autorisierungs Seiten-URLs finden Sie unter [Authentifizieren eines Benutzers in einer Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-flow-tab.md) Kontextinformationen können verwendet werden.
Stellen Sie sicher, dass alle auf den Registerkartenseiten verwendeten Domänen im `manifest.json` `validDomains` Array aufgelistet sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder Entfernen einer Registerkarte

Unterstützte Entfernungsoptionen können die Benutzerfreundlichkeit weiter verfeinern. Sie können Benutzern das ändern, konfigurieren oder Umbenennen einer Gruppe/Kanal-Registerkarte ermöglichen, indem Sie die `canUpdateConfiguration` Eigenschaft des Manifests auf `true`festlegen.  Darüber hinaus können Sie festlegen, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit den Entfernungsoptionen in Ihrer APP `removeUrl` hinzufügen und `setSettings()` einen Wert für die Eigenschaft in der Konfiguration festlegen (siehe unten). Persönliche Registerkarten können nicht geändert, aber vom Benutzer deinstalliert werden. Weitere Informationen finden Sie unter [Erstellen einer Entfernungs Seite für die Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md).

## <a name="mobile-clients"></a>Mobile Clients

Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, muss `setSettings()` die Konfiguration über einen Wert für die `websiteUrl` Eigenschaft verfügen (siehe unten). Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze veröffentlicht. Zur Vorbereitung des Updates sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.

Microsoft Teams SetSettings ()-Konfiguration für die Entfernungs Seite und/oder Mobile Clients:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
