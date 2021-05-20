---
title: Erstellen einer Konfigurationsseite
author: laujan
description: Erstellen einer Konfigurationsseite
keywords: Teams Tabs Gruppenkanal konfigurierbar
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: aeab1cf96d1e875db79d9143fefd0e46348f585a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566684"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Eine Konfigurationsseite ist ein spezieller [Inhaltstyp](content-page.md). Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration als Teil der folgenden:

* Eine Registerkarte für Kanal- oder Gruppenchats: Sammeln Sie Informationen von den Benutzern, und legen Sie fest, dass die `contentUrl` Inhaltsseite angezeigt wird.
* Eine [Messagingerweiterung](~/messaging-extensions/what-are-messaging-extensions.md).
* Ein [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="configuring-a-channel-or-group-chat-tab"></a>Konfigurieren einer Kanal- oder Gruppenchat-Registerkarte

Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verweisen und `microsoft.initialize()` aufrufen. Außerdem müssen die verwendeten URLs https-Endpunkte gesichert und in der Cloud verfügbar sein. 

### <a name="example"></a>Beispiel

Ein Beispiel für eine Konfigurationsseite wird in der folgenden Abbildung gezeigt: 

<img src="~/assets/images/tab-images/configuration-page.png" alt="Configuration page" width="400"/>

Der entsprechende Code für die Konfigurationsseite wird im folgenden Abschnitt gezeigt:

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

Wählen Sie entweder **Grau auswählen** **oder** Rote Schaltfläche auf der Konfigurationsseite, um den Tab-Inhalt mit einem grauen oder roten Symbol anzuzeigen. 

In der folgenden Abbildung wird der Tabstoppinhalt mit einem grauen Symbol angezeigt:

<img src="~/assets/images/tab-images/configure-tab-with-gray.png" alt="Configure tab with select gray" width="400"/>

In der folgenden Abbildung wird der Tabstoppinhalt mit einem roten Symbol angezeigt:

<img src="~/assets/images/tab-images/configure-tab-with-red.png" alt="Configure tab with select red" width="400"/>

Die Auswahl der relativen Schaltfläche löst entweder `saveGray()` oder aus und ruft Folgendes `saveRed()` auf:

1. Der `settings.setValidityState(true)` ist auf wahr eingestellt.
1. Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
1. Die Schaltfläche **Speichern** auf der Konfigurationsseite der App, die in Teams hochgeladen wurde, ist aktiviert.

Der Konfigurationsseitencode informiert die Teams, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann. Wenn der Benutzer **Speichern** auswählt, werden die Parameter von `settings.setSettings()` festgelegt, wie durch die Schnittstelle `Settings` definiert. Weitere Informationen finden Sie [unter Einstellungen Schnittstelle](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true). Im letzten Schritt `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Wenn Sie einen Speicherhandler mithilfe von `microsoftTeams.settings.registerOnSaveHandler()` registrieren, muss der Rückruf `saveEvent.notifySuccess()` aufgerufen werden oder das Ergebnis der Konfiguration `saveEvent.notifyFailure()` angeben.
>* Wenn Sie keinen Speicherhandler registrieren, wird der `saveEvent.notifySuccess()` Aufruf automatisch durchgeführt, wenn der Benutzer **Speichern** auswählt.

### <a name="get-context-data-for-your-tab-settings"></a>Abrufen von Kontextdaten für Ihre Registerkarteneinstellungen

Auf der Registerkarte sind möglicherweise Kontextinformationen zum Anzeigen relevanter Inhalte erforderlich. Kontextbezogene Informationen erhöhen die Attraktivität Ihres Tabs weiter, indem sie eine individuellere Benutzererfahrung bieten.

Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true). Sammeln Sie die Werte von Kontextdatenvariablen auf zwei Arten:

1. Fügen Sie URL-Abfragezeichenfolgenplatzhalter in die `configurationURL` .

1. Verwenden Sie die [Teams SDK-Methode.](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})`

#### <a name="insert-placeholders-in-the-configurationurl"></a>Platzhalter in die `configurationUrl`

Fügen Sie Ihrer Basis Kontextschnittstellenplatzhalter `configurationUrl` hinzu. Zum Beispiel:

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

Nach dem Hochladen der Seite aktualisiert die Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten. Schließen Sie Logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Im folgenden Beispiel wird beschrieben, wie ein Wert aus der Eigenschaft extrahiert werden `configurationUrl` kann:

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

Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Context-Schnittstelle](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) ab, wenn sie aufgerufen wird. Fügen Sie diese Funktion der Konfigurationsseite hinzu, um Kontextwerte abzurufen:

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

 Authentifizieren, bevor sie einem Benutzer erlauben, Ihre App zu konfigurieren. Andernfalls können Ihre Inhalte Quellen enthalten, die über ihre Authentifizierungsprotokolle verfügen. Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers auf einer Registerkarte Microsoft Teams](~/tabs/how-to/authentication/auth-flow-tab.md). Verwenden Sie Kontextinformationen, um die Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen.
Stellen Sie sicher, dass alle Domänen, die auf den Registerkarten verwendet werden, im und im Array aufgeführt `manifest.json` `validDomains` sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder Entfernen einer Registerkarte

Unterstützte Entfernungsoptionen verfeinern die Benutzerfreundlichkeit weiter. Legen Sie die Eigenschaft des Manifests `canUpdateConfiguration` auf , die es den Benutzern `true` ermöglicht, eine Gruppen- oder Kanalregisterkarte zu ändern, neu zu konfigurieren oder umzubenennen. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit den Entfernungsoptionen in die App einschließen und einen Wert für die `removeUrl` Eigenschaft in der Konfiguration  `setSettings()` festlegen. Der Benutzer kann die Registerkarten "Personal" deinstallieren, sie jedoch nicht ändern. Weitere Informationen finden Sie unter [Erstellen einer Entfernungsseite für Ihre Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md).

Microsoft Teams setSettings()-Konfiguration zum Entfernen:

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

Wenn Sie den Kanal oder die Gruppenregisterkarte auf der Teams mobilen Clients anzeigen möchten, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` haben. Weitere Informationen finden Sie unter [Anleitung zu Registerkarten auf mobilen](~/tabs/design/tabs-mobile.md).
