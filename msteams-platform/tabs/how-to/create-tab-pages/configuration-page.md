---
title: Erstellen einer Konfigurationsseite
author: surbhigupta
description: So erstellen Sie eine Konfigurationsseite
keywords: Konfigurierbarer Gruppenkanal für Teams-Registerkarten
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 041ef78fcc6e3f5203842e808949e86e8dd3aae4
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069216"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Eine Konfigurationsseite ist ein spezieller [Inhaltsseitentyp.](content-page.md) Die Benutzer konfigurieren einige Aspekte der Microsoft Teams App mithilfe der Konfigurationsseite und verwenden diese Konfiguration als Teil der folgenden Komponenten:

* Registerkarte "Kanal- oder Gruppenchat": Sammeln sie Informationen von den Benutzern, und legen Sie `contentUrl` die anzuzeigende Inhaltsseite fest.
* Eine [Messaging-Erweiterung](~/messaging-extensions/what-are-messaging-extensions.md).
* Ein [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="configuring-a-channel-or-group-chat-tab"></a>Konfigurieren einer Kanal- oder Gruppenchatregisterkarte

Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verweisen und `microsoft.initialize()` aufrufen. Außerdem müssen die verwendeten URLs gesicherte HTTPS-Endpunkte sein und in der Cloud verfügbar sein. 

### <a name="example"></a>Beispiel

Ein Beispiel für eine Konfigurationsseite ist in der folgenden Abbildung dargestellt: 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

Der entsprechende Code für die Konfigurationsseite wird im folgenden Abschnitt angezeigt:

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

Wählen Sie auf der Konfigurationsseite entweder die Schaltfläche **"Grau"** oder **"Rot auswählen"** aus, um den Registerkarteninhalt mit einem grauen oder roten Symbol anzuzeigen. 

In der folgenden Abbildung wird der Registerkarteninhalt mit grauen Symbolen angezeigt:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

In der folgenden Abbildung wird der Registerkarteninhalt mit einem roten Symbol angezeigt:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Wenn Sie die relative Schaltfläche auswählen, wird entweder `saveGray()` oder `saveRed()` ausgelöst, und Folgendes wird aufgerufen:

1. Der `settings.setValidityState(true)` Wert ist auf "true" festgelegt.
1. Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
1. Die Schaltfläche **"Speichern"** auf der Konfigurationsseite der App, die in Teams hochgeladen wurde, ist aktiviert.

Der Code der Konfigurationsseite informiert die Teams, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann. Wenn der Benutzer **"Speichern"** auswählt, werden die Parameter `settings.setSettings()` festgelegt, wie von der `Settings` Benutzeroberfläche definiert. Weitere Informationen finden Sie unter [Einstellungen Schnittstelle.](/javascript/api/@microsoft/teams-js/microsoftteams.settings.settings?view=msteams-client-js-latest&preserve-view=true) Wird im letzten Schritt `saveEvent.notifySuccess()` aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Wenn Sie einen Speicherhandler mithilfe `microsoftTeams.settings.registerOnSaveHandler()` registrieren, muss der Rückruf aufgerufen `saveEvent.notifySuccess()` werden oder das Ergebnis der Konfiguration `saveEvent.notifyFailure()` angeben.
>* Wenn Sie keinen Speicherhandler registrieren, wird der `saveEvent.notifySuccess()` Aufruf automatisch ausgeführt, wenn der Benutzer **"Speichern"** auswählt.

### <a name="get-context-data-for-your-tab-settings"></a>Abrufen von Kontextdaten für Ihre Registerkarteneinstellungen

Auf der Registerkarte sind möglicherweise Kontextinformationen zum Anzeigen relevanter Inhalte erforderlich. Kontextbezogene Informationen verbessern die Darstellung Ihrer Registerkarte weiter, indem sie eine angepasstere Benutzeroberfläche bereitstellen.

Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter ["Kontextschnittstelle".](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) Erfassen Sie die Werte von Kontextdatenvariablen auf zwei Arten:

1. Fügen Sie PLATZHALTER FÜR URL-Abfragezeichenfolgen in das Manifest `configurationURL` ein.

1. Verwenden Sie die [Teams SDK-Methode.](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`

#### <a name="insert-placeholders-in-the-configurationurl"></a>Einfügen von Platzhaltern in die `configurationUrl`

Fügen Sie Ihrer Basis Platzhalter für die Kontextschnittstelle `configurationUrl` hinzu. Beispiel:

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

Nachdem die Seite hochgeladen wurde, aktualisiert das Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten. Schließen Sie Logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Im folgenden Beispiel wird die Methode zum Extrahieren eines Werts aus der `configurationUrl` Eigenschaft beschrieben:

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

Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) ab, wenn sie aufgerufen wird. Fügen Sie diese Funktion zur Konfigurationsseite hinzu, um Kontextwerte abzurufen:

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

 Authentifizieren Sie sich, bevor ein Benutzer Ihre App konfigurieren kann. Andernfalls können Ihre Inhalte Quellen mit ihren Authentifizierungsprotokollen enthalten. Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers auf einer registerkarte Microsoft Teams.](~/tabs/how-to/authentication/auth-flow-tab.md) Verwenden Sie Kontextinformationen, um die URLs für Authentifizierungsanforderungen und Autorisierungsseiten zu erstellen.
Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkartenseiten verwendet werden, im `manifest.json` `validDomains` Und-Array aufgeführt sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder Entfernen einer Registerkarte

Unterstützte Entfernungsoptionen verfeinern die Benutzeroberfläche weiter. Legen Sie die Eigenschaft Ihres Manifests `canUpdateConfiguration` auf , die es benutzern `true` ermöglicht, eine Gruppe oder Kanalregisterkarte zu ändern, neu zu konfigurieren oder umzubenennen. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit Den entfernten Optionen in die App einschließen und einen Wert für die `removeUrl` Eigenschaft in der Konfiguration  `setSettings()` festlegen. Der Benutzer kann die persönlichen Registerkarten deinstallieren, aber nicht ändern. Weitere Informationen finden Sie unter [Erstellen einer Seite zum Entfernen ihrer Registerkarte.](~/tabs/how-to/create-tab-pages/removal-page.md)

Microsoft Teams setSettings()-Konfiguration für die Entfernungsseite:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

## <a name="mobile-clients"></a>Mobile Clients

Wenn Ihre Kanal- oder Gruppenregisterkarte auf den Teams mobilen Clients angezeigt werden soll, muss die `setSettings()` Konfiguration einen Wert für `websiteUrl` aufweisen. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen Geräten.](~/tabs/design/tabs-mobile.md)
