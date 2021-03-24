---
title: Erstellen einer Konfigurationsseite
author: laujan
description: Erstellen einer Konfigurationsseite
keywords: Gruppenkanal für Teams-Registerkarten konfigurierbar
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b6da8437b6988f863288d77aedc1acb786c12d4b
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034678"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Eine Konfigurationsseite ist ein spezieller Typ von [Inhaltsseite](content-page.md). Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration im Rahmen der folgenden Schritte:

* Registerkarte "Kanal" oder "Gruppenchat" – Sammeln Sie Informationen von den Benutzern, und legen Sie die Anzuzeigende der `contentUrl` Inhaltsseite festgelegt.
* Eine [Messagingerweiterung](~/messaging-extensions/what-are-messaging-extensions.md)
* Ein [Office 365 Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="configuring-a-channel-or-group-chat-tab"></a>Konfigurieren einer Registerkarte "Kanal" oder "Gruppenchat"

Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK verweisen und](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoft.initialize()` aufrufen. Außerdem müssen die verwendeten URLs gesicherte HTTPS-Endpunkte sein und in der Cloud verfügbar sein. Der folgende Code ist ein Beispiel für eine Konfigurationsseite:

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

Wählen Sie **auf der** Konfigurationsseite die Schaltfläche **Grau** auswählen oder Rot auswählen aus, um den Registerkarteninhalt mit einem grauen oder roten Symbol anzuzeigen. Wenn Sie die relative Schaltfläche auswählen, wird entweder `saveGray()` oder `saveRed()` und folgendes aufgerufen:

1. Die `settings.setValidityState(true)` ist auf true festgelegt.
1. Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
1. Die **Schaltfläche** Speichern auf der Konfigurationsseite der App, die in Teams hochgeladen wurde, ist aktiviert.

Der Konfigurationsseitencode informiert Teams darüber, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann. Wenn der Benutzer Speichern **auswählt,** werden die Parameter von `settings.setSettings()` festgelegt, wie von der Schnittstelle `Settings` definiert. Weitere Informationen finden Sie unter [Einstellungsschnittstelle](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true). Im letzten Schritt wird `saveEvent.notifySuccess()` aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Wenn Sie einen Speicherhandler mithilfe registrieren, muss der Rückruf das Ergebnis der Konfiguration aufrufen oder `microsoftTeams.settings.registerOnSaveHandler()` `saveEvent.notifySuccess()` `saveEvent.notifyFailure()` angeben.
>* Wenn Sie keinen Speicherhandler registrieren, wird der Aufruf automatisch ausgeführt, wenn der `saveEvent.notifySuccess()` Benutzer Speichern **auswählt.**

### <a name="get-context-data-for-your-tab-settings"></a>Get context data for your tab settings

Ihre Registerkarte erfordert möglicherweise Kontextinformationen, um relevante Inhalte anzuzeigen. Kontextbezogene Informationen verbessern die Ansinnen Ihrer Registerkarte weiter, indem sie eine angepasste Benutzeroberfläche bereitstellen.

Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [Context interface](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true). Sammeln Sie die Werte von Kontextdatenvariablen auf die folgenden zwei Arten:

1. Einfügen von Platzhaltern für die URL-Abfragezeichenfolge in der `configurationURL` .

1. Verwenden Sie die [Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` SDK-Methode.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Einfügen von Platzhaltern in das `configurationUrl`

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

Nach dem Hochladen Der Seitenuploads aktualisiert Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten. Schließen Sie die Logik auf der Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Im folgenden Beispiel wird die Methode zum Extrahieren eines Werts aus der Eigenschaft `configurationUrl` beschrieben:

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

Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Kontextschnittstelle ab, wenn](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) sie aufgerufen wird. Fügen Sie diese Funktion der Konfigurationsseite hinzu, um Kontextwerte abzurufen:

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

 Authentifizieren Sie sich, bevor ein Benutzer Ihre App konfigurieren kann. Andernfalls können Ihre Inhalte Quellen enthalten, die über ihre Authentifizierungsprotokolle verfügen. Weitere Informationen finden Sie unter [Authenticate a user in a Microsoft Teams tab](~/tabs/how-to/authentication/auth-flow-tab.md). Verwenden Sie Kontextinformationen, um die URLs für Authentifizierungsanforderungen und Autorisierungsseiten zu erstellen.
Stellen Sie sicher, dass alle auf Ihren Registerkartenseiten verwendeten Domänen im `manifest.json` `validDomains` Und-Array aufgeführt sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder Entfernen einer Registerkarte

Unterstützte Entfernungsoptionen verfeinern die Benutzeroberfläche weiter. Legen Sie die Eigenschaft Ihres Manifests auf fest, mit der benutzer eine Gruppe oder Kanalregisterkarte ändern, neu konfigurieren oder umbenennen `canUpdateConfiguration` `true` können. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit Entfernungsoptionen in die App hinzufügen und einen Wert für die Eigenschaft `removeUrl` in der Konfiguration  `setSettings()` festlegen. Der Benutzer kann die Registerkarten "Persönlich" deinstallieren, aber nicht ändern. Weitere Informationen finden Sie unter [Create a removal page for your tab](~/tabs/how-to/create-tab-pages/removal-page.md).

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

Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf den mobilen Teams-Clients anzeigen möchten, muss die Konfiguration `setSettings()` einen Wert für die Eigenschaft `websiteUrl` haben. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen Geräten.](~/tabs/design/tabs-mobile.md)