---
title: Erstellen einer Konfigurationsseite
author: laujan
description: Erstellen einer Konfigurationsseite
keywords: Gruppenkanal für Registerkarten von Teams konfigurierbar
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2544454fd06348fa41269f3a8fd57cc71a07d140
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886737"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Eine Konfigurationsseite ist ein spezieller Typ von [Inhaltsseite.](content-page.md) Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration im Rahmen der folgenden Schritte:

* Registerkarte "Kanal" oder "Gruppenchat" – Sammeln von Informationen von den Benutzern und Festlegen der anzuzeigende `contentUrl` Inhaltsseite.
* Eine [Messagingerweiterung](~/messaging-extensions/what-are-messaging-extensions.md)
* Ein [Office 365-Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)

## <a name="configuring-a-channel-or-group-chat-tab"></a>Konfigurieren einer Kanal- oder Gruppenchatregisterkarte

Die Anwendung muss auf das [Microsoft Teams JavaScript-Client-SDK verweisen und](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoft.initialize()` aufrufen. Außerdem müssen die verwendeten URLs gesicherte HTTPS-Endpunkte sein und über die Cloud verfügbar sein. Der folgende Code ist ein Beispiel für eine Konfigurationsseite:

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

Wählen Sie **auf der Konfigurationsseite** die **Schaltfläche** "Grau auswählen" oder "Rot auswählen" aus, um den Registerkarteninhalt mit einem grauen oder roten Symbol anzuzeigen. Wenn Sie die relative Schaltfläche auswählen, wird entweder eine oder eine oder mehrere der `saveGray()` `saveRed()` folgenden Schaltflächen aufgerufen:

1. Der `settings.setValidityState(true)` Wert ist auf "true" festgelegt.
1. Der `microsoftTeams.settings.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
1. Die **Schaltfläche** "Speichern" auf der Konfigurationsseite der App, die in Teams hochgeladen wurde, ist aktiviert.

Der Konfigurationsseitencode informiert Teams darüber, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann. Wenn der Benutzer **"Speichern"** auswählt, werden die Parameter `settings.setSettings()` festgelegt, wie von der Benutzeroberfläche `Settings` definiert. Weitere Informationen finden Sie unter ["Einstellungsschnittstelle".](/javascript/api/@microsoft/teams-js/_settings?view=msteams-client-js-latest&preserve-view=true) Im letzten Schritt wird aufgerufen, um anzugeben, `saveEvent.notifySuccess()` dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Wenn Sie einen Speicherhandler mithilfe registrieren, muss der Rückruf das Ergebnis der Konfiguration aufrufen `microsoftTeams.settings.registerOnSaveHandler()` `saveEvent.notifySuccess()` oder `saveEvent.notifyFailure()` angeben.
>* Wenn Sie keinen Speicherhandler registrieren, wird der Aufruf automatisch ausgeführt, wenn `saveEvent.notifySuccess()` der Benutzer "Speichern" **auswählt.**

### <a name="get-context-data-for-your-tab-settings"></a>Kontextdaten für Ihre Registerkarteneinstellungen erhalten

Ihre Registerkarte erfordert möglicherweise kontextbezogene Informationen, um relevante Inhalte anzuzeigen. Kontextbezogene Informationen verbessern die Aufrufe Ihrer Registerkarte weiter, indem sie eine angepasste Benutzeroberfläche bereitstellen.

Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true). Sammeln Sie die Werte von Kontextdatenvariablen auf zwei Arten:

1. Einfügen von Platzhaltern für die URL-Abfragezeichenfolge im `configurationURL` Manifest.

1. Verwenden Sie die [Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `microsoftTeams.getContext((context) =>{})` SDK-Methode.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Einfügen von Platzhaltern in das `configurationUrl`

Fügen Sie Ihrer Basis Platzhalter für die Kontextschnittstelle `configurationUrl` hinzu. Zum Beispiel:

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

Nach dem Hochladen der Seite aktualisiert Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten. Schließen Sie logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter ["URLSearchParams"](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Im folgenden Beispiel wird die Methode zum Extrahieren eines Werts aus der Eigenschaft `configurationUrl` beschrieben:

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

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Verwenden der `getContext()` Funktion zum Abrufen von Kontext

Die `microsoftTeams.getContext((context) => {})` Funktion ruft die [Kontextschnittstelle ab,](/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) wenn sie aufgerufen wird. Fügen Sie diese Funktion zur Konfigurationsseite hinzu, um Kontextwerte abzurufen:

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

 Authentifizieren Sie sich, bevor Ein Benutzer Ihre App konfigurieren können. Andernfalls können Ihre Inhalte Quellen enthalten, die über ihre Authentifizierungsprotokolle verfügen. Weitere Informationen finden Sie unter [Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte.](~/tabs/how-to/authentication/auth-flow-tab.md) Verwenden Sie Kontextinformationen, um die URLs für Authentifizierungsanforderungen und Autorisierungsseiten zu erstellen.
Stellen Sie sicher, dass alle auf Ihren Registerkartenseiten verwendeten Domänen im `manifest.json` Und-Array aufgeführt `validDomains` sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder Entfernen einer Registerkarte

Unterstützte Entfernungsoptionen optimieren die Benutzeroberfläche weiter. Legen Sie die Eigenschaft Des Manifests auf , die es den Benutzern ermöglicht, eine Gruppe oder Kanalregisterkarte zu ändern, neu zu konfigurieren oder `canUpdateConfiguration` `true` umzubenennen. Geben Sie außerdem an, was mit dem Inhalt geschieht, wenn eine Registerkarte entfernt wird, indem Sie eine Seite mit Optionen zum Entfernen in die App hinzufügen und einen Wert für die Eigenschaft `removeUrl` in der Konfiguration  `setSettings()` festlegen. Weitere Informationen finden Sie unter [Mobile Clients](#mobile-clients). Der Benutzer kann die persönlichen Registerkarten deinstallieren, aber nicht ändern. Weitere Informationen finden Sie unter ["Erstellen einer Seite zum Entfernen" für Ihre Registerkarte.](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="mobile-clients"></a>Mobile Clients

Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf den mobilen Clients von Teams anzeigen möchten, muss die Konfiguration `setSettings()` einen Wert für die Eigenschaft `websiteUrl` haben. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen Geräten.](~/tabs/design/tabs-mobile.md)

Microsoft Teams setSettings()-Konfiguration zum Entfernen von Seiten oder mobilen Clients:

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add unique name here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "URL REQUIRED FOR MOBILE CLIENTS",
    removeUrl: "ADD REMOVAL PAGE URL HERE"
});
```
