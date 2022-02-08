---
title: Microsoft Teams JavaScript-Client-SDK v2 Preview
description: Grundlegendes zu den Änderungen, die mit Microsoft Teams JavaScript-Client-SDK v2 Preview
ms.date: 11/15/2021
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: e70133fcd538e83a7822056074be27ac9dcb9bb0
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435174"
---
# <a name="microsoft-teams-javascript-client-sdk-v2-preview"></a>Microsoft Teams JavaScript-Client-SDK v2 Preview

Mit dem [Microsoft Teams JavaScript-Client-SDK v2 Preview](/javascript/api/overview/msteams-client?view=msteams-client-js-beta&preserve-view=true) wurde das vorhandene Teams SDK (`@microsoft/teams-js`oder einfach `TeamsJS`) umgestaltet, um Teams Entwicklern die Möglichkeit zu bieten, [Teams Apps für die Ausführung in Outlook und Office zu erweitern](overview.md). Aus funktionaler Sicht ist das TeamsJS SDK v2 Preview (`@microsoft/teams-js@next`) eine Obermenge des aktuellen TeamsJS SDK und unterstützt vorhandene Teams-App-Funktionen und bietet gleichzeitig die Möglichkeit, Teams Apps in Outlook und Office zu hosten.

Es gibt zwei wesentliche Änderungen im TeamsJS SDK v2 Preview, die Ihr Code berücksichtigen muss, um in anderen Microsoft 365 Anwendungen ausgeführt werden zu können:

* [**Rückruffunktionen geben jetzt Promise-Objekte zurück.**](#callbacks-converted-to-promises) Alle vorhandenen Funktionen mit einem Rückrufparameter wurden modernisiert, um ein JavaScript [Promise-Objekt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) zurückzugeben, um die Behandlung asynchroner Vorgänge und die Lesbarkeit von Code zu verbessern.

 - [**APIs sind jetzt in *Funktionen* unterteilt.**](#apis-organized-into-capabilities) Sie können sich Funktionen als logische Gruppierungen von APIs vorstellen, die ähnliche Funktionen bereitstellen, z`authentication`. B. , `calendar`, `mail`, `monetization``meeting`und `sharing`.

 Sie können die [Teams Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Microsoft Visual Studio Code verwenden, um den Aktualisierungsprozess für Ihre Teams-App zu vereinfachen, wie im folgenden Abschnitt beschrieben.

> [!NOTE]
> Die Aktivierung einer vorhandenen Teams-App in Outlook und Office erfordert beides:
> 1. Abhängigkeit von der oder höher `@microsoft/teams-js@2.0.0-beta.1` und
> 2. Ändern des vorhandenen Anwendungscodes gemäß den in diesem Dokument beschriebenen erforderlichen Änderungen.
>
>  Wenn Sie aus einer vorhandenen Teams-App (oder höher) verweisen `@microsoft/teams-js@2.0.0-beta.1` , werden Veraltete Warnungen angezeigt, wenn Ihr Code geänderte APIs aufruft. Eine API-Übersetzungsebene (Zuordnung des aktuellen SDK zur Vorschau von SDK-API-Aufrufen) wird bereitgestellt, damit vorhandene Teams-Apps weiterhin in Teams arbeiten können, bis sie Code aktualisieren können, um mit dem TeamsJS SDK v2 Preview zu arbeiten. Nachdem Sie Den Code mit den in diesem Artikel beschriebenen Änderungen aktualisiert haben, wird Ihre persönliche Registerkarte auch in Outlook und Office ausgeführt.

## <a name="updating-to-the-teams-client-sdk-v2-preview"></a>Aktualisieren auf das Teams Client SDK v2 Preview

Die einfachste Möglichkeit, Ihre Teams-App für die Verwendung des TeamsJS SDK v2 Preview zu aktualisieren, ist die Verwendung der [Teams Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Visual Studio Code. In diesem Abschnitt werden Sie durch die erforderlichen Schritte geführt. Wenn Sie es vorziehen, Ihren Code manuell zu aktualisieren, finden Sie in den in [Zusagen konvertierten Rückrufen](#callbacks-converted-to-promises) und [APIs, die in Funktionen](#apis-organized-into-capabilities) unterteilt sind, weitere Informationen zu erforderlichen API-Änderungen.

### <a name="1-install-the-latest-teams-toolkit-visual-studio-code-extension"></a>1. Installieren Sie die neueste Teams Toolkit-Visual Studio Code-Erweiterung

Suchen *Sie im Visual Studio Code Extensions Marketplace* nach **Teams Toolkit**, und installieren Sie die Version `2.10.0` oder höher. Das Toolkit bietet zwei Befehle zur Unterstützung des Prozesses:

1. Ein Befehl zum Aktualisieren des Manifestschemas
1. Ein Befehl zum Aktualisieren ihrer SDK-Verweise und Aufrufen von Websites

Es folgen die beiden wichtigsten Updates, die Sie zum Ausführen einer Teams persönlichen Registerkarten-App in anderen Microsoft 365-Anwendungen benötigen: ''

### <a name="2-updating-the-manifest"></a>2. Aktualisieren des Manifests

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen Sie **Teams aus: Aktualisieren Sie Teams Manifest, um den Befehl Outlook und Office Apps zu unterstützen**, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden vorgenommen.

# <a name="manual-steps"></a>[Manuelle Schritte](#tab/manifest-manual)

Öffnen Sie Ihr Teams-App-Manifest, und aktualisieren Sie das `$schema` und `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion" : "m365DevPreview"
}
```
---

Wenn Sie Teams Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie sie auch verwenden, um die Änderungen an Ihrer Manifestdatei zu überprüfen und Fehler zu identifizieren. Öffnen Sie die Befehlspalette`Ctrl+Shift+P`, und suchen Sie **nach Teams: Überprüfen der Manifestdatei**, oder wählen Sie die Option im Bereitstellungsmenü des Teams Toolkits aus (suchen Sie auf der linken Seite von Visual Studio Code nach dem Symbol Teams).

:::image type="content" source="images/toolkit-validate-manifest-file.png" alt-text="Option &quot;Manifestdatei überprüfen&quot; im Teams Toolkit im Menü &quot;Bereitstellung&quot;":::

### <a name="2-update-sdk-references"></a>2. Aktualisieren von SDK-Verweisen

Um in Outlook und Office ausgeführt zu werden, muss Ihre App vom [npm-Paket](https://www.npmjs.com/package/@microsoft/teams-js/v/2.0.0-beta.1) `@microsoft/teams-js@2.0.0-beta.1` (oder einer späteren *Betaversion*) abhängig sein. Wenn Sie diese Schritte manuell ausführen möchten, und weitere Informationen zu den API-Änderungen finden Sie in den folgenden Abschnitten zu [Rückrufen, die in Zusagen](#callbacks-converted-to-promises) und APIs umgewandelt wurden, die [in Funktionen unterteilt sind](#apis-organized-into-capabilities).

1. Stellen Sie sicher[, dass Sie über Teams Toolkit](https://aka.ms/teams-toolkit) `v2.10.0` oder höher verfügen.
1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Ausführen des Befehls `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps`

Nach Abschluss des Vorgangs hat das Hilfsprogramm Ihre `package.json` Datei mit der Abhängigkeit von TeamsJS SDK v2 Preview (`@microsoft/teams-js@2.0.0-beta.1`oder höher) aktualisiert, und Ihre und `*.jsx/.tsx` Ihre `*.js/.ts` Dateien werden mit Folgendem aktualisiert:

> [!div class="checklist"]
> * `package.json` Verweise auf TeamsJS SDK v2 Preview
> * Importanweisungen für TeamsJS SDK v2 Preview
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](#apis-organized-into-capabilities) an TeamsJS SDK v2 Preview
> * `TODO` Kommentarerinnerungen zum Überprüfen von Bereichen, die möglicherweise von [Änderungen der Kontextschnittstelle](#updates-to-the-context-interface) betroffen sind
> * `TODO` Kommentarerinnerungen, um sicherzustellen, dass die [Konvertierung in Zusagenfunktionen aus Rückrufstilfunktionen](#callbacks-converted-to-promises) auf jeder Aufrufwebsite, die das Tool gefunden hat, gut funktioniert hat

> [!IMPORTANT]
> Code in HTML-Dateien wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

## <a name="callbacks-converted-to-promises"></a>In Zusagen konvertierte Rückrufe

Teams APIs, die zuvor einen Rückrufparameter verwendet haben, wurden aktualisiert, um ein JavaScript [Promise-Objekt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) zurückzugeben. Dazu gehören die folgenden APIs:

```js
app.getContext, app.initialize, appInstallDialog.openAppInstallDialog, authentication.authenticate, authentication.getAuthToken, authentication.getUser, authentication.registerAuthenticationHandlers was removed to support using Promises, calendar.openCalendarItem, calendar.composeMeeting, call.startCall, core.executeDeepLink, location.getLocation, location.showLocation, mail.openMailItem, mail.composeMail, media.captureImage, media.getMedia, media.selectMedia, media.viewImages, media.scanBarCode, meeting.getAppContentStageSharingCapabilities, meeting.getAuthenticationTokenForAnonymousUser, meeting.getIncomingClientAudioState, meeting.getLiveStreamState, meeting.getMeetingDetails, meeting.requestStartLiveStreaming, meeting.requestStopLiveStreaming, meeting.shareAppContentToStage, meeting.stopSharingAppContentToStage, meeting.toggleIncomingClientAudio, meeting.getAppContentStageSharingState, pages.backStack.navigateBack, pages.navigateCrossDomain, pages.navigateToTab, pages.tabs.getMruTabInstances, pages.tabs.getTabInstances, pages.config.setConfig, pages.config.getConfig, people.selectPeople, ChildAppWindow.postMessage, ParentAppWindow.postMessage
```

Sie müssen aktualisieren, wie Ihr Code eine dieser APIs aufruft, um Zusagen zu verwenden. Beispiel: Wenn Ihr Code eine Teams-API wie folgt aufruft:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Dieser Code:

```js
import microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context) => { /* ... */ });
```

Muss aktualisiert werden auf:

```js
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context) => {
    /*...*/
});
```

... oder das entsprechende `async/await` Muster:

```js
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context = await app.getContext();
  /*...*/
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Dieser Code:

```TypeScript
import * as microsoftTeams from "@microsoft/teams-js";

microsoftTeams.getContext((context: microsoftTeams.Context) => {
  /* ... */
});
```

Muss aktualisiert werden auf:

```TypeScript
import { app, Context } from "@microsoft/teams-js";

app.getContext().then((context: Context) => {
    /*...*/
});
```

... oder das entsprechende `async/await` Muster:

```TypeScript
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context: Context = await app.getContext();
  /*...*/
}
```

---

> [!TIP]
> Wenn Sie Ihren Code für das TeamsJS SDK v2 Preview mit [Teams Toolkit](#updating-to-the-teams-client-sdk-v2-preview) aktualisieren, werden die erforderlichen Updates für Sie mit `TODO` Kommentaren in Ihrem Clientcode gekennzeichnet.

## <a name="apis-organized-into-capabilities"></a>In Funktionen unterteilte APIs

Eine *Funktion* ist eine logische Gruppierung von APIs, die ähnliche Funktionen bereitstellen. Sie können sich Microsoft Teams, Outlook und Office als Hosts vorstellen. Ein Host unterstützt eine bestimmte Funktion, wenn er alle in dieser Funktion definierten APIs unterstützt. Ein Host kann eine Funktion nicht teilweise implementieren.  Funktionen können feature- oder inhaltsbasiert sein, z. B. *Dialog* oder *Authentifizierung*. Es gibt auch Funktionen für Anwendungstypen, z. B *. Registerkarten/Seiten* oder *Bots* und andere Gruppierungen.

Im TeamsJS SDK v2 Preview werden APIs als Funktionen in einem JavaScript-Namespace definiert, deren Name ihrer erforderlichen Funktion entspricht. Wenn eine App auf einem Host ausgeführt wird, der die Dialogfunktion unterstützt, kann die App sicher APIs aufrufen, z `dialog.open` . B. (zusätzlich zu anderen dialogbezogenen APIs, die im Namespace definiert sind). Wenn eine App versucht, eine API aufzurufen, die in diesem Host nicht unterstützt wird, löst die API in der Zwischenzeit eine Ausnahme aus.

### <a name="differentiate-your-app-experience"></a>Unterscheiden Der App-Erfahrung

Sie können die Hostunterstützung einer bestimmten Funktion zur Laufzeit überprüfen, indem Sie die `isSupported()` Funktion für diese Funktion (Namespace) aufrufen. Es wird zurückgegeben `true` , wenn es unterstützt wird und `false` wenn nicht, und Sie können das App-Verhalten entsprechend anpassen. Dadurch kann Ihre App die Benutzeroberfläche und Die Funktionalität in Hosts, die sie unterstützen, aufhellen, während sie weiterhin für Hosts ausgeführt wird, die dies nicht tun.

Der Name des Hosts, in dem Ihre App ausgeführt wird, wird als *hostName-Eigenschaft* auf der Kontextschnittstelle (`app.Context.app.host.name`) verfügbar gemacht, die zur Laufzeit durch Aufrufen `getContext`abgefragt werden kann. Es ist auch als [URL-Platzhalterwert](../tabs/how-to/access-teams-context.md#get-context-by-inserting-url-placeholder-values)`{hostName}` verfügbar. Bewährte Methode ist die sparsame Verwendung des *hostName-Mechanismus* :

* **Gehen Sie nicht** davon aus, dass bestimmte Funktionen basierend auf dem *HostName-Eigenschaftswert* in einem Host verfügbar sind oder nicht verfügbar sind. Suchen Sie stattdessen nach Funktionsunterstützung (`isSupported`).
* Verwenden Sie *"hostName*" **nicht**, um API-Aufrufe zu tätigen. Suchen Sie stattdessen nach Funktionsunterstützung (`isSupported`).
* Verwenden **Sie** *hostName*, um das Design Ihrer Anwendung basierend auf dem Host zu unterscheiden, in dem sie ausgeführt wird. Sie können beispielsweise Microsoft Teams Lila als Hauptakzentfarbe verwenden, wenn sie in Teams ausgeführt wird, und Outlook Blau, wenn Sie in Outlook ausgeführt werden.
* Verwenden **Sie** *"hostName"*, um dem Benutzer angezeigte Nachrichten basierend auf dem Host zu unterscheiden, auf dem er ausgeführt wird. Zeigen *Sie beispielsweise Die Aufgaben in Office* verwalten an, wenn sie in Office im Web ausgeführt werden, und *verwalten Sie Ihre Aufgaben in Teams*, wenn sie in Microsoft Teams ausgeführt werden.

### <a name="namespaces"></a>Namespaces

Das TeamsJS SDK v2 Preview organisiert APIs anhand von Namespaces in *Funktionen* . Einige neue Namespaces von besonderer Bedeutung sind *App*, *Seiten*, *Dialog* und *teamsCore*.

#### <a name="app-namespace"></a>*App-Namespace*

Der `app` Namespace enthält APIs der obersten Ebene, die für die allgemeine App-Nutzung über Microsoft Teams, Office und Outlook erforderlich sind. Alle APIs aus verschiedenen anderen TeamsJS-Namespaces wurden in den `app` Namespace im TeamsJS SDK v2 Preview verschoben:

| Originalnamespace `global (window)` | Neuer Namespace `app` |
| - | - |
| `initialize` | `app.initialize` |
| `getContext` | `app.getContext` |
| `registerOnThemeChangeHandler` | `app.registerOnThemeChangeHandler` |

| Originalnamespace `appInitialization` | Neuer Namespace `app` |
| - | - |
| `appInitialization.notifyAppLoaded` | `app.notifyAppLoaded` |
| `appInitialization.notifySuccess` | `app.notifySuccess` |
| `appInitialization.notifyFailure` | `app.notifyFailure` |
| `appInitialization.notifyExpectedFailure` | `app.notifyExpectedFailure` |
| `appInitialization.FailedReason` Enum | `app.FailedReason` |
| `appInitialization.ExpectedFailureReason` Enum | `app.ExpectedFailureReason` |
| `appInitialization.IFailedRequest` Enum | `app.IFailedRequest` |
| `appInitialization.IExpectedFailureRequest` Enum | `app.IExpectedFailureRequest` |

#### <a name="core-namespace"></a>*Kernnamespace*

Der `core` Namespace enthält Funktionen für Deep-Links.

| Originalnamespace `publicAPIs` | Neuer Namespace `core` |
| - | - |
| `shareDeepLink` | `core.shareDeepLink` |
| `executeDeepLink` | `core.executeDeepLink` |

#### <a name="pages-namespace"></a>*Seitennamespace*

Der `pages` Namespace enthält Funktionen zum Ausführen und Navigieren von Webseiten innerhalb verschiedener Microsoft 365 Clients, einschließlich Teams, Office und Outlook. Es enthält auch mehrere Unterfunktionen, die als Unternamespaces implementiert werden.

| Originalnamespace `global (window)` | Neuer Namespace `pages` |
| - | - |
| `setFrameContext` | `pages.setCurrentFrame` (umbenannt) |
| `initializeWithFrameContext` | `pages.initializeWithFrameContext` |
| `registerFullScreenHandler` | `pages.registerFullScreenHandler` |
| `navigateCrossDomain` | `pages.navigateCrossDomain` |
| `returnFocus` | `pages.returnFocus` |

##### <a name="pagestabs"></a>*pages.tabs*

| Originalnamespace `global (window)` | Neuer Namespace `pages.tabs` |
| - | - |
| `getTabInstances` |  `pages.tabs.getTabInstances` |
| `getMruTabInstances` | `pages.tabs.getMruTabInstances` |
| ` navigateToTab` | `pages.tabs.navigateToTab` |

| Originalnamespace `navigation` | Neuer Namespace `pages.tabs` |
| - | - |
| `navigation.navigateToTab` | `pages.tabs.navigateToTab` |

##### <a name="pagesconfig"></a>*pages.config*

| Originalnamespace `settings` | Neuer Namespace `pages.config`  |
| - | - |
| `settings.setSettings` | `pages.config.setConfig` (umbenannt)
| `settings.getSettings` | `pages.config.getConfig` (umbenannt)
| `settings.setValidityState`| `pages.config.setValidityState`
| `settings.initialize` | `pages.config.initialize`
| `settings.registerOnSaveHandler`| `pages.config.registerOnSaveHandler`
| `settings.registerOnRemoveHandler` | `pages.config.registerOnRemoveHandler`
| `settings.Settings` Schnittstelle | `pages.config.Config` (umbenannt)
| `settings.SaveEvent` Schnittstelle | `pages.config.SaveEvent` (umbenannt)
| `settings.RemoveEvent` Schnittstelle | `pages.config.RemoveEvent` (umbenannt)
| `settings.SaveParameters` Schnittstelle | `pages.config.SaveParameters` (umbenannt)
| `settings.SaveEventImpl` Schnittstelle | `pages.config.SaveEventImpl` (umbenannt)

| Originalnamespace `global (window)` | Neuer Namespace `pages.config` |
| - | - |
| `registerEnterSettingsHandler` | `pages.config.registerChangeConfigHandler` (umbenannt)

##### <a name="pagesbackstack"></a>*pages.backStack*

| Originalnamespace `navigation` | Neuer Namespace `pages.backStack`  |
| - | - |
| `navigation.navigateBack` | `pages.backStack.navigateBack`

| Originalnamespace `global (window)` | Neuer Namespace `pages.backStack`  |
| - | - |
| `registerBackButtonHandler` | `pages.backStack.registerBackButtonHandler`

##### <a name="pagesappbutton"></a>*pages.appButton*

| Originalnamespace `global (window)` | Neuer Namespace `pages.appButton`  |
| - | - |
| `registerAppButtonClickHandler` | `pages.appButton.onClick` (umbenannt)
| `registerAppButtonHoverEnterHandler` | `pages.appButton.onHoverEnter` (umbenannt)
| `registerAppButtonHoverLeaveEnter` | `pages.appButton.onHoverLeave` (umbenannt)
| `FrameContext` Schnittstelle | `pages.appButton.FrameInfo` (umbenannt)) |

#### <a name="dialog-namespace"></a>*Dialognamespace*

Der *TeamsJS-Aufgabennamespace* wurde in *Dialog* umbenannt, und die folgenden APIs wurden umbenannt:

| Originalnamespace `tasks` | Neuer Namespace `dialog`  |
| - | - |
| `tasks.startTask` | `dialog.open` (umbenannt) |
| `tasks.submitTasks` | `dialog.submit` (umbenannt) |
| `tasks.updateTasks` | `dialog.resize` (umbenannt) |
| `tasks.TaskModuleDimension` Enum | `dialog.DialogDimension` (umbenannt) |
| `tasks.TaskInfo` Schnittstelle | `dialog.DialogInfo` (umbenannt) |

#### <a name="teamscore-namespace"></a>*teamsCore-Namespace*

Um das TeamsJS SDK so zu generalisieren, dass andere Microsoft 365 Hosts wie Office und Outlook ausgeführt werden, wurde Teams-spezifische Funktionalität (ursprünglich im *globalen* Namespace) in einen *teamsCore-Namespace* verschoben:

| Originalnamespace `global (window)` | Neuer Namespace `teamsCore`  |
| - | - |
| `enablePrintCapability` | `teamsCore.enablePrintCapability`
| `print` | `teamsCore.print`
| `registerOnLoadHandler` | `teamsCore.registerOnLoadHandler`
| `registerBeforeUnloadHandler` | `teamsCore.registerBeforeUnloadHandler`
| `registerFocusEnterHandler` | `teamsCore.registerFocusEnterHandler`

### <a name="updates-to-the-context-interface"></a>Aktualisierungen der *Kontextschnittstelle*

Die `Context` Schnittstelle wurde in den `app` Namespace verschoben und aktualisiert, um ähnliche Eigenschaften zu gruppieren, um eine bessere Skalierbarkeit zu erhalten, da sie in Outlook und Office ausgeführt wird, zusätzlich zu Teams.

Eine neue Eigenschaft `app.Context.app.host.name` wurde hinzugefügt, um persönliche Registerkarten zu ermöglichen, um die Benutzererfahrung je nach Hostanwendung zu unterscheiden.

Sie können die Änderungen auch visualisieren, indem Sie die  [`transformLegacyContextToAppContext`](https://github.com/OfficeDev/microsoft-teams-library-js/blob/2.0-preview/packages/teams-js/src/public/app.ts) Funktion in der Microsoft TeamsJS SDK v2 Preview-Quelle überprüfen.

| Originalname in `Context` Schnittstelle | Neuer Standort in `app.Context` |
| - | - |
| `appIconPosition` | `app.Context.app.iconPositionVertical` |
| `appLaunchId`| *NICHT IN Teams Client SDK v2 Preview* |
| `appSessionId` | `app.Context.app.sessionId`|
| `channelId`| `app.Context.channel.id` |
| `channelName`| `app.Context.channel.displayName`|
| `channelRelativeUrl` | `app.Context.channel.relativeUrl`|
| `channelType`| `app.Context.channel.membershipType` |
| `chatId` | `app.Context.chat.id`|
| `defaultOneNoteSectionId`| `app.Context.channel.defaultOneNoteSectionId`|
| `entityId` | `app.Context.page.id`|
| `frameContext` | `app.Context.page.frameContext`|
| `groupId`| `app.Context.team.groupId` |
| `hostClientType` | `app.Context.app.host.clientType`|
| `hostTeamGroupId`| `app.Context.channel.ownerGroupId` |
| `hostTeamTenantId` | `app.Context.channel.ownerTenantId`|
| `isCallingAllowed` | `app.Context.user.isCallingAllowed`|
| `isFullScreen` | `app.Context.page.isFullScreen`|
| `isMultiWindow`| `app.Context.page.isMultiWindow` |
| `isPSTNCallingAllowed` | `app.Context.user.isPSTNCallingAllowed`|
| `isTeamArchived` | `app.Context.team.isArchived`|
| `locale` | `app.Context.app.locale` |
| `loginHint`| `app.Context.user.loginHint` |
| `meetingId`| `app.Context.meeting.id` |
| `osLocaleInfo` | `app.Context.app.osLocaleInfo` |
| `parentMessageId`| `app.Context.app.parentMessageId`|
| `ringId` | `app.Context.app.host.ringId`|
| `sessionId`| `app.Context.app.host.sessionId` |
| `sourceOrigin` | `app.Context.page.sourceOrigin`|
| `subEntityId`| `app.Context.page.subPageId` |
| `teamId` | `app.Context.team.internalId`|
| `teamSiteDomain` | `app.Context.sharepointSite.domain`|
| `teamSitePath` | `app.Context.sharepointSite.path`|
| `teamSiteUrl`| `app.Context.sharepointSite.url` |
| `teamTemplateId` | `app.Context.team.templateId`|
| `teamType` | `app.Context.team.type`|
| `tenantSKU`| `app.Context.user.tenant.teamsSku` |
| `tid`| `app.Context.user.tenant.id` |
| `upn` | `app.Context.user.userPrincipalName` |
|` userClickTime`| `app.Context.app.userClickTime`|
| `userFileOpenPreference` | `app.Context.app.userFileOpenPreference` |
| `userLicenseType`| `app.Context.user.licenseType` |
| `userObjectId` | `app.Context.user.id`|
| ` userTeamRole` | `app.Context.team.userRole`|
| `userDisplayName` | `app.Context.user.displayName` |
| N/V | `app.Context.app.host.name`|

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu grundlegenden Änderungen finden Sie auch im [Changelog des TeamsJS SDK v2 Preview](https://github.com/OfficeDev/microsoft-teams-library-js/blob/2.0-preview/CHANGELOG.md) und in der [Api-Referenz für das TeamsJS SDK v2 Preview](/javascript/api/overview/msteams-client?view=msteams-client-js-beta&preserve-view=true).

Wenn Sie bereit sind, Ihre Teams Apps zu testen, die in Outlook und Office ausgeführt werden, lesen Sie Folgendes:

> [!div class="nextstepaction"]
> [Erweitern Ihrer Teams-App über Microsoft 365](overview.md)
