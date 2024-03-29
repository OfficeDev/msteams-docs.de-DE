---
title: Erstellen einer Konfigurationsseite
author: surbhigupta
description: Seite "Konfiguration erstellen", um Informationen vom Benutzer zu sammeln. Rufen Sie außerdem Kontextdaten für Microsoft Teams-Registerkarten ab, wissen Sie über die Authentifizierung, ändern oder entfernen Sie Registerkarten.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 6cd9ed8572b3df2db4a727225159774156008fa6
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820171"
---
# <a name="create-a-configuration-page"></a>Erstellen einer Konfigurationsseite

Eine Konfigurationsseite ist eine spezielle [Art von Inhaltsseite](content-page.md). Die Benutzer konfigurieren einige Aspekte der Microsoft Teams-App mithilfe der Konfigurationsseite und verwenden diese Konfiguration als Teil der folgenden Aktionen:

* Eine Kanal- oder Gruppenchat-Registerkarte: Sammeln Sie Informationen von den Benutzern und `contentUrl` legen Sie die Anzeige der Inhaltsseite fest.
* Eine [Nachrichtenerweiterung](~/messaging-extensions/what-are-messaging-extensions.md).
* [Office 365-Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="configure-a-channel-or-group-chat-tab"></a>Konfigurieren einer Kanal- oder Gruppenchatregisterkarte

Die Anwendung muss auf das JavaScript-Client-SDK von [Microsoft Teams](/javascript/api/overview/msteams-client) verweisen und aufrufen `app.initialize()`. Die verwendeten URLs müssen gesicherte HTTPS-Endpunkte sein und sind in der Cloud verfügbar.

### <a name="example"></a>Beispiel

Ein Beispiel für eine Konfigurationsseite ist in der folgenden Abbildung dargestellt:

:::image type="content" source="../../../assets/images/tab-images/configuration-page.png" alt-text="Screenshot: Konfigurationsseite":::

Der folgende Code ist ein Beispiel für entsprechenden Code für die Konfigurationsseite:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<head>
    <script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" 
      integrity="sha384yBjE++eHeBPzIg+IKl9OHFqMbSdrzY2S/LW3qeitc5vqXewEYRWegByWzBN/chRh" 
      crossorigin="anonymous" >
    </script>
<body>
    <button onclick="(document.getElementById('icon').src = '/images/iconGray.png'); colorClickGray()">Select Gray</button>
    <img id="icon" src="/images/teamsIcon.png" alt="icon" style="width:100px" />
    <button onclick="(document.getElementById('icon').src = '/images/iconRed.png'); colorClickRed()">Select Red</button>

    <script>
        await microsoftTeams.app.initialize();
        let saveGray = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                const configPromise = pages.config.setConfig({
                    websiteUrl: "https://yourWebsite.com",
                    contentUrl: "https://yourWebsite.com/gray",
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                configPromise.
                    then((result) => {saveEvent.notifySuccess()}).
                    catch((error) => {saveEvent.notifyFailure("failure message")});
            });
        }

        let saveRed = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                const configPromise = pages.config.setConfig({
                    websiteUrl: "https://yourWebsite.com",
                    contentUrl: "https://yourWebsite.com/red",
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                configPromise.
                    then((result) => {saveEvent.notifySuccess();}).
                    catch((error) => {saveEvent.notifyFailure("failure message")});
            });
        }

        let gr = document.getElementById("gray").style;
        let rd = document.getElementById("red").style;

        const colorClickGray = () => {
            gr.display = "block";
            rd.display = "none";
            microsoftTeams.pages.config.setValidityState(true);
            saveGray()
        }

        const colorClickRed = () => {
            rd.display = "block";
            gr.display = "none";
            microsoftTeams.pages.config.setValidityState(true);
            saveRed();
        }
    </script>
    ...
</body>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***
Wählen Sie auf der **Konfigurationsseite** entweder **die Schaltfläche Grau auswählen oder Rot** auswählen, um den Inhalt der Registerkarte mit einem grauen oder roten Symbol anzuzeigen.

Das folgende Bild zeigt den Inhalt der Registerkarte mit ausgewähltem **grauem** Symbol:

:::image type="content" source="../../../assets/images/tab-images/configure-tab-with-gray.png" alt-text="Screenshot: Registerkarte &quot;Konfigurieren&quot; mit grauer Option":::

Das folgende Bild zeigt den Inhalt der Registerkarte mit ausgewähltem **rotem** Symbol:

:::image type="content" source="../../../assets/images/tab-images/configure-tab-with-red.png" alt-text="Screenshot: Registerkarte &quot;Konfigurieren&quot; mit roter Option":::

Die Auswahl der entsprechenden Schaltfläche löst entweder `saveGray()` oder `saveRed()` aus und ruft Folgendes auf:

* Auf `pages.config.setValidityState(true)` wahr setzen.
* Der `pages.config.registerOnSaveHandler()` Ereignishandler wird ausgelöst.
* **Speichern** auf der Konfigurationsseite der App ist aktiviert.

Der Konfigurationsseitencode informiert Teams darüber, dass die Konfigurationsanforderungen erfüllt sind und die Installation fortgesetzt werden kann. Wenn der Benutzer **Speichern** auswählt, werden die `pages.config.setConfig()` Parameter von eingestellt, wie von der Schnittstelle `Config` definiert. Weitere Informationen finden Sie unter [Konfigurationsschnittstelle](/javascript/api/@microsoft/teams-js/pages.config?). `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

>[!NOTE]
>
>* Vor dem Timeout haben Sie 30 Sekunden Zeit, um den Speichervorgang (rückruf an `registerOnSaveHandler`) abzuschließen. Nach dem Timeout erscheint eine allgemeine Fehlermeldung.
>* Wenn Sie einen save-Handler mit registrieren `registerOnSaveHandler()`, muss der Callback `saveEvent.notifySuccess()` oder `saveEvent.notifyFailure()` aufrufen, um das Ergebnis der Konfiguration anzugeben.
>* Wenn Sie keinen Speicherhandler registrieren, erfolgt der `saveEvent.notifySuccess()` Aufruf automatisch, wenn der Benutzer **Speichern auswählt**.
>* Stellen Sie sicher, dass eindeutig `entityId`ist. Doppelte `entityId` Umleitungen zur ersten Instanz der Registerkarte.

### <a name="get-context-data-for-your-tab-settings"></a>Rufen Sie Kontextdaten für Ihre Registerkarteneinstellungen ab

Ihre Registerkarte benötigt Kontextinformationen, um relevante Inhalte anzuzeigen. Kontextinformationen erhöhen die Attraktivität Ihres Tabs weiter, indem sie eine individuellere Benutzererfahrung bieten.

Weitere Informationen zu den Eigenschaften, die für die Registerkartenkonfiguration verwendet werden, finden Sie unter [Kontextschnittstelle](/javascript/api/@microsoft/teams-js/app.context?view=msteams-client-js-latest&preserve-view=true). Sammeln Sie die Werte von Kontextdatenvariablen auf die folgenden zwei Arten:

* Platzhalter für URL-Abfragezeichenfolgen in die `configurationURL`.

* Verwenden Sie die [Teams SDK-Methode](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) `app.getContext()`.

#### <a name="insert-placeholders-in-the-configurationurl"></a>Platzhalter in die einfügen `configurationUrl`

Fügen Sie Platzhalter für Kontextschnittstellen zu Ihrer Basis hinzu `configurationUrl`. Beispiel:

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

Nachdem Ihre Seite hochgeladen wurde, aktualisiert Teams die Platzhalter der Abfragezeichenfolge mit relevanten Werten. Fügen Sie Logik in die Konfigurationsseite ein, um diese Werte abzurufen und zu verwenden. Weitere Informationen zum Arbeiten mit URL-Abfragezeichenfolgen finden Sie unter [URLSearchParams](https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams) in MDN Web Docs. Das folgende Codebeispiel bietet die Möglichkeit, einen Wert aus der Eigenschaft zu `configurationUrl` extrahieren:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<script>
   await microsoftTeams.app.initialize();
   const getId = () => {
        let urlParams = new URLSearchParams(document.location.search.substring(1));
        let blueTeamId = urlParams.get('team');
        return blueTeamId
    }
//For testing, you can invoke the following to view the pertinent value:
document.write(getId());
</script>
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***

### <a name="use-the-getcontext-function-to-retrieve-context"></a>Verwenden Sie die `getContext()` Funktion, um den Kontext abzurufen

Die `app.getContext()` Funktion gibt eine Zusage zurück, die mit dem [Kontextschnittstellenobjekt](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest&preserve-view=true) aufgelöst wird.

Der folgende Code ist ein Beispiel für das Hinzufügen dieser Funktion zur Konfigurationsseite, um Kontextwerte abzurufen:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```html
<!-- `userPrincipalName` will render in the span with the id "user". -->

<span id="user"></span>
...
<script type="module">
    import {app} from 'https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js';
    const contextPromise = app.getContext();
    contextPromise.
        then((context) => {
            let userId = document.getElementById('user');
            userId.innerHTML = context.user.userPrincipalName;
        }).
        catch((error) => {/*Unsuccessful operation*/});
</script>
...
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

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

***

## <a name="context-and-authentication"></a>Kontext und Authentifizierung

Authentifizieren Sie sich, bevor Sie einem Benutzer erlauben, Ihre App zu konfigurieren. Andernfalls könnten Ihre Inhalte Quellen enthalten, die ihre eigenen Authentifizierungsprotokolle haben. Weitere Informationen finden [Sie unter Authentifizieren eines Benutzers auf einer Microsoft Teams-Registerkarte](~/tabs/how-to/authentication/auth-flow-tab.md). Verwenden Sie Kontextinformationen, um die Authentifizierungsanforderungen und Autorisierungsseiten-URLs zu erstellen. Stellen Sie sicher, dass alle Domänen, die auf Ihren Registerkarten verwendet werden, im Array `manifest.json` und aufgeführt `validDomains` sind.

## <a name="modify-or-remove-a-tab"></a>Ändern oder entfernen Sie eine Registerkarte

Legen Sie die -Eigenschaft Ihres Manifests `canUpdateConfiguration` auf fest `true`. Es ermöglicht den Benutzern, einen Kanal oder eine Gruppenregisterkarte zu ändern oder neu zu konfigurieren. Sie können Ihre Registerkarte nur über die Teams-Benutzeroberfläche umbenennen. Informieren Sie den Benutzer über die Auswirkungen auf den Inhalt, wenn eine Registerkarte entfernt wird. Fügen Sie dazu eine Seite mit Den Entfernungsoptionen in die App ein, und legen Sie einen Wert für die `removeUrl` Eigenschaft in der `setConfig()` (früheren `setSettings()`) Konfiguration fest. Der Benutzer kann persönliche Registerkarten deinstallieren, aber nicht ändern. Weitere Informationen finden [Sie unter Erstellen einer Entfernungsseite für Ihren Tab](~/tabs/how-to/create-tab-pages/removal-page.md).

Microsoft Teams `setConfig()` -Konfiguration (früher `setSettings()`) für die Entfernungsseite:

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
import { pages } from "@microsoft/teams-js";
const configPromise = pages.config.setConfig({
    contentUrl: "add content page URL here",
    entityId: "add a unique identifier here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
configPromise.
    then((result) => {/*Successful operation*/).
    catch((error) => {/*Unsuccessful operation*/});
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
microsoftTeams.settings.setSettings({
    contentUrl: "add content page URL here",
    entityId: "add a unique identifier here",
    suggestedDisplayName: "add name to display on tab here",
    websiteUrl: "add website URL here //Required field for configurable tabs on Mobile Clients",
    removeUrl: "add removal page URL here"
});
```

***

## <a name="mobile-clients"></a>Mobile Clients

Wenn Sie festlegen, dass Ihre Kanal- oder Gruppenregisterkarte auf den mobilen Teams-Clients angezeigt wird, muss die `setConfig()`Konfiguration einen Wert für haben `websiteUrl`. Weitere Informationen finden Sie in der [Anleitung für Tabs auf Mobilgeräten](~/tabs/design/tabs-mobile.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Sie eine Entfernungsseite für Ihren Tab](~/tabs/how-to/create-tab-pages/removal-page.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../../what-are-tabs.md)
* [Aktualisieren von App-Manifest für SSO und App-Vorschau](../authentication/tab-sso-manifest.md)
* [Konfigurieren der OAuth-IdP-Authentifizierung von Drittanbietern](../authentication/auth-tab-aad.md)
* [Erstellen von Office 365-Connectors](../../../webhooks-and-connectors/how-to/connectors-creating.md)
* [Kontext für Ihre Registerkarte erhalten](../access-teams-context.md)
* [Registerkarten auf mobilen Geräten](../../design/tabs-mobile.md)
