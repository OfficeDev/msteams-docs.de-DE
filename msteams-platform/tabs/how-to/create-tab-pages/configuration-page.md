---
title: Erstellen einer Konfigurationsseite
author: surbhigupta
description: Erfahren Sie, wie Sie eine Konfigurationsseite zum Konfigurieren eines Kanal- oder Gruppenchats für Einstellungen erstellen, z. B. abrufen von Kontextdaten, Einfügen von Platzhaltern und Authentifizierung mithilfe von Codebeispielen.
keywords: Gruppenkanal für Teams-Registerkarten konfigurierbar
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: dc1c5c7c8852d13ab490ae0782be0a01eef3fbea
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103418"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Eine Konfigurationsseite ist ein spezieller Typ von [Inhaltsseite](content-page.md). Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration als Teil der folgenden:

* Eine Kanal- oder Gruppenchatregisterkarte: Sammeln Sie Informationen von den Benutzern, und legen Sie die `contentUrl` Anzeige der Inhaltsseite fest.
* Eine [Nachrichtenerweiterung](~/messaging-extensions/what-are-messaging-extensions.md).
* Ein [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="configure-a-channel-or-group-chat-tab"></a>Konfigurieren einer Kanal- oder Gruppenchatregisterkarte

Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verweisen und aufrufen`microsoft.initialize()`. Die verwendeten URLs müssen gesicherte HTTPS-Endpunkte sein und in der Cloud verfügbar sein.

### <a name="example"></a>Beispiel

Ein Beispiel für eine Konfigurationsseite ist in der folgenden Abbildung dargestellt:

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

Der folgende Code ist ein Beispiel für den entsprechenden Code für die Konfigurationsseite:

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
    ...
</body>
```

Wählen Sie auf der Konfigurationsseite entweder die Schaltfläche " **Grau auswählen** " oder " **Rot auswählen** " aus, um den Registerkarteninhalt mit einem grauen oder roten Symbol anzuzeigen.

In der folgenden Abbildung wird der Registerkarteninhalt mit ausgewähltem **Grausymbol** angezeigt:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

Die folgende Abbildung zeigt den Registerkarteninhalt mit ausgewähltem **roten** Symbol:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Wenn Sie die entsprechende Schaltfläche auswählen, wird entweder `saveGray()` oder `saveRed()`ausgelöst und Folgendes aufgerufen:

* Auf "true" festgelegt `settings.setValidityState(true)` .
* Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
* **Auf** der Konfigurationsseite der App speichern, ist aktiviert.

Der Code der Konfigurationsseite informiert Teams, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann. Wenn der Benutzer " **Speichern"** auswählt, werden die Parameter `settings.setSettings()` festgelegt, wie von der `Settings` Schnittstelle definiert. Weitere Informationen finden Sie unter ["Einstellungsschnittstelle"](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true). `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Sie haben 30 Sekunden Zeit, um den Speichervorgang (den Rückruf von registerOnSaveHandler) vor dem Timeout abzuschließen. Nach dem Timeout wird eine allgemeine Fehlermeldung angezeigt.
>* Wenn Sie einen Speicherhandler registrieren, `microsoftTeams.settings.registerOnSaveHandler()`muss der Rückruf das Ergebnis der Konfiguration aufrufen `saveEvent.notifySuccess()` oder `saveEvent.notifyFailure()` angeben.
>* Wenn Sie keinen Speicherhandler registrieren, wird der `saveEvent.notifySuccess()` Aufruf automatisch ausgeführt, wenn der Benutzer " **Speichern"** auswählt.

### <a name="get-context-data-for-your-tab-settings"></a>Abrufen von Kontextdaten für Ihre Registerkarteneinstellungen

Ihre Registerkarte erfordert kontextbezogene Informationen, um relevante Inhalte anzuzeigen. Kontextbezogene Informationen verbessern die Attraktivität Ihrer Registerkarte durch eine angepasste Benutzererfahrung.

Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter ["Kontextschnittstelle"](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true). Sammeln Sie die Werte von Kontextdatenvariablen auf zwei Arten:

* Fügen Sie Platzhalter für URL-Abfragezeichenfolgen in das Manifest ein `configurationURL`.

* Verwenden Sie die [Teams SDK-Methode](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)`microsoftTeams.getContext((context) =>{})`.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Einfügen von Platzhaltern in die `configurationUrl`

Fügen Sie Ihrer Basis `configurationUrl`Platzhalter für die Kontextschnittstelle hinzu. Beispiel:

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

Nachdem die Seite hochgeladen wurde, aktualisiert Teams die Abfragezeichenfolgenplatzhalter mit relevanten Werten. Fügen Sie Logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden [Sie unter URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Das folgende Codebeispiel bietet die Möglichkeit, einen Wert aus der `configurationUrl` Eigenschaft zu extrahieren:

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Verwenden der `getContext()` Funktion zum Abrufen des Kontexts

Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) ab, wenn sie aufgerufen wird.

Der folgende Code enthält ein Beispiel für das Hinzufügen dieser Funktion zur Konfigurationsseite zum Abrufen von Kontextwerten:

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

Authentifizieren Sie sich, bevor ein Benutzer Ihre App konfigurieren kann. Andernfalls können Ihre Inhalte Quellen enthalten, die über ihre Authentifizierungsprotokolle verfügen. Weitere Informationen finden Sie [unter Authentifizieren eines Benutzers auf einer Microsoft Teams Registerkarte](~/tabs/how-to/authentication/auth-flow-tab.md). Verwenden Sie Kontextinformationen, um die Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen. Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, in der `manifest.json` Und-Matrix `validDomains` aufgeführt sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder Entfernen einer Registerkarte

Legen Sie die Eigenschaft Ihres Manifests `canUpdateConfiguration` auf `true`die Eigenschaft fest, mit der benutzer eine Kanal- oder Gruppenregisterkarte ändern, neu konfigurieren oder umbenennen können. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit Denkoptionen in die App einschließen und einen Wert für die `removeUrl` Eigenschaft in der  `setSettings()` Konfiguration festlegen. Der Benutzer kann persönliche Registerkarten deinstallieren, aber nicht ändern. Weitere Informationen finden Sie unter [Erstellen einer Seite zum Entfernen ihrer Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md).

`setSettings()` Microsoft Teams Konfiguration für die Entfernungsseite:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add a unique identifier here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a>Mobile Clients

Wenn Ihre Kanal- oder Gruppenregisterkarte auf den Teams mobilen Clients angezeigt werden soll, muss die `setSettings()` Konfiguration einen Wert für `websiteUrl`aufweisen. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf Mobilgeräten](~/tabs/design/tabs-mobile.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Seite zum Entfernen ihrer Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="see-also"></a>Siehe auch

* [Teams Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Erstellen einer Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
