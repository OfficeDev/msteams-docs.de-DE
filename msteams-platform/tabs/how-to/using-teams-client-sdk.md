---
title: Erstellen von Registerkarten und anderen gehosteten Umgebungen mit dem Microsoft Teams JavaScript-Client-SDK
author: heath-hamilton
ms.author: surbhigupta
description: Lernen Sie in diesem Modul das JavaScript-Client-SDK von Microsoft Teams kennen, das Ihnen beim Erstellen von App-Erfahrungen helfen kann, die in <iframe> in Office und Outlook gehostet werden.
ms.localizationpriority: high
ms.topic: conceptual
ms.openlocfilehash: 1909df76b3cc61f0d93e4efe40e02b99dc3de730
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144215"
---
# <a name="building-tabs-and-other-hosted-experiences-with-the-microsoft-teams-javascript-client-sdk"></a>Erstellen von Registerkarten und anderen gehosteten Umgebungen mit dem Microsoft Teams JavaScript-Client-SDK

Mit dem Microsoft Teams JavaScript-Client-SDK können Sie gehostete Umgebungen in Teams, Office und Outlook erstellen, in denen Ihre App-Inhalte in einem [iframe](https://developer.mozilla.org/docs/Web/HTML/Element/iframe) gehostet werden. Das SDK ist hilfreich für die Entwicklung von Apps mit den folgenden Microsoft Teams-Funktionen:

* [Registerkarten](../../tabs/what-are-tabs.md)
* [Dialogfelder (Aufgabenmodule)](../../task-modules-and-cards/what-are-task-modules.md)

Ab Version `2.0.0` wurde das vorhandene Teams-Client-SDK (`@microsoft/teams-js` oder einfach `TeamsJS`) umgestaltet, damit [Teams-Apps nicht nur in Microsoft Teams, sondern auch in Outlook und Office ausgeführt werden können](/microsoftteams/platform/m365-apps/overview). Aus funktionaler Sicht unterstützt die neueste Version von TeamsJS alle vorhandenen Teams-App-Funktionen (v.1.x.x) und fügt gleichzeitig die optionale Möglichkeit zum Hosten von Teams-Apps in Outlook und Office hinzu.

Hier sehen Sie die aktuellen Anleitungen zu Versionsverwaltung für verschiedene App-Szenarien:

[!INCLUDE [pre-release-label](~/includes/teamjs-version-details.md)]

Der Rest dieses Artikels führt Sie durch die Struktur und die neuesten Updates für das Microsoft Teams JavaScript-Client-SDK.

### <a name="microsoft-365-support-running-teams-apps-in-office-and-outlook"></a>Microsoft 365-Unterstützung (Ausführen von Teams-Apps in Office und Outlook)

TeamsJS v.2.0 führt die Möglichkeit ein, bestimmte Arten von Teams-Apps über das gesamte Microsoft 365-Ökosystem hinweg auszuführen. Derzeit unterstützen andere Microsoft 365 Anwendungshosts für Teams-Apps (einschließlich Office und Outlook) eine Teilmenge der Anwendungstypen und Funktionen, die Sie für die Teams-Plattform erstellen können. Diese Unterstützung wird im Laufe der Zeit erweitert. Eine Zusammenfassung der Hostunterstützung für Teams-Apps finden Sie unter [Erweitern von Teams-Apps auf Microsoft 365](../../m365-apps/overview.md).

In der folgenden Tabelle sind Teams-Registerkarten und -Dialogfelder (Aufgabenmodule) sowie Funktionen (öffentliche Namespaces) mit erweiterter Unterstützung für die Ausführung auf anderen Microsoft 365-Hosts aufgeführt.

> [!TIP]
> Überprüfen Sie die Hostunterstützung einer bestimmten Funktion zur Laufzeit, indem Sie für diese Funktion (Namespace) die Funktion `isSupported()` aufrufen.

|Funktion | Hostunterstützung | Hinweise |
|-----------|--------------|-------|
| App | Teams, Outlook, Office | Namespace, der die App-Initialisierung und den Lebenszyklus darstellt. |
| appInitialization| | Veraltet. Durch Namespace `app` ersetzt. |
| appInstallDialog | Teams||
| Authentifizierung | Teams, Outlook, Office | |
| Kalender | Teams, Outlook ||
| call | Teams||
| Chat |Teams||
| Dialogfeld | Teams, Outlook, Office | Namespace, der Dialogfelder darstellt (vormals als *Aufgabenmodule* bezeichnet. Siehe Hinweise zu [Dialogfeldern](#dialogs). |
| Speicherort |Teams| Siehe Hinweise zu [App-Berechtigungen](#app-permissions).|
| mail | Outlook (nur Windows Desktop)||
| media |Teams| Siehe Hinweise zu [App-Berechtigungen](#app-permissions).|
| Seiten | Teams, Outlook, Office | Namespace, der die Seitennavigation darstellt. Siehe Hinweise zu [Deep Linking](#deep-linking). |
| Kontakte |Teams||
| settings || Veraltet. Ersetzt durch `pages.config`.|
| sharing | Teams||
| tasks | | Veraltet. Ersetzt durch die Funktion `dialog`. Siehe Hinweise zu [Dialogfeldern](#dialogs).|
| teamsCore | Teams | Namespace, der Teams-spezifische Funktionen enthält.|
| video | Teams||

#### <a name="app-permissions"></a>App-Berechtigungen

App-Funktionen, für die der Benutzer [Geräteberechtigungen](../../concepts/device-capabilities/device-capabilities-overview.md) (z. B. *Standort*) erteilen muss, werden für Apps, die außerhalb von Teams ausgeführt werden, noch nicht unterstützt. Es gibt derzeit keine Möglichkeit, App-Berechtigungen bei der Ausführung in Outlook oder Office unter „Einstellungen“ oder in Ihrem App-Header zu überprüfen. Wenn eine Teams-Anwendung, die in Office oder Outlook ausgeführt wird, eine TeamsJS (oder HTML5) API aufruft, die Geräteberechtigungen auslöst, generiert diese API einen Fehler und zeigt keinen Systemdialog an, der den Benutzer um seine Zustimmung bittet.

Der aktuelle Ansatz besteht derzeit darin, den Code so zu ändern, dass der Fehler abgefangen wird:

* Überprüfen Sie [isSupported()](#differentiate-your-app-experience) für eine Funktion, bevor Sie sie verwenden. `media`, `meeting` und `files` unterstützen sie noch keine *isSupported*-Anrufe und funktionieren noch nicht außerhalb von Microsoft Teams.
* Erfassen und Behandeln von Fehlern beim Aufrufen von TeamsJS- und HTML5-APIs.

Wenn eine API nicht unterstützt wird oder einen Fehler generiert, fügen Sie eine Logik hinzu, um einen Fehler zu vermeiden oder einen Workaround anzubieten. Beispiel:

* Leiten Sie den Benutzer auf die Website Ihrer App weiter.
* Weisen Sie den Benutzer an, die App in Microsoft Teams zu verwenden, um den Fluss abzuschließen.
* Benachrichtigen Sie den Benutzer darüber, dass die Funktionalität noch nicht verfügbar ist.

Darüber hinaus empfiehlt es sich, sicherzustellen, dass Ihr App-Manifest nur die Geräteberechtigungen angibt, die es verwendet.

#### <a name="deep-linking"></a>Deep Linking

Vor Version 2.0 von TeamsJS wurden alle Deep Linking-Szenarien mithilfe von `shareDeepLink` (zum Generieren eines Links *zu* einem bestimmten Teil Ihrer App) und `executeDeepLink` (zum Navigieren zu einem Deeplink *von* oder *innerhalb* Ihrer App) behandelt. Mit TeamsJS v.2.0 wird eine neue API eingeführt (`navigateToApp`), mit der Sie auf konsistente Weise zu Seiten (und Unterseiten) innerhalb einer App über App-Hosts hinweg (neben zu Teams auch Office und Outlook) navigieren können. Hier ist die aktualisierte Anleitung für Deep Linking-Szenarien:

##### <a name="deep-links-into-your-app"></a>Deep-Links zu Ihrer App

Verwenden Sie `pages.shareDeepLink` (vor TeamsJS v.2.0 als *shareDeepLink* bezeichnet), um einen kopierbaren Link zu generieren und anzuzeigen, den der Benutzer freigeben kann. Wird darauf geklickt, wird ein Benutzer aufgefordert, die App zu installieren, sofern sie nicht bereits für den (im Linkpfad angegebenen) Anwendungshost installiert ist.

##### <a name="navigation-within-your-app"></a>Navigation in Ihrer App

Verwenden Sie die neue `pages.navigateToApp`-API, um in Ihrer App innerhalb der Hostinganwendung zu navigieren.

Diese API bietet ein Äquivalent zum Navigieren zu einem Deep-Link (wofür bislang das jetzt veraltete *executeDeepLink* verwendet wurde), ohne dass Ihre App eine URL erstellen oder unterschiedliche Deep-Link-Formate für verschiedene Anwendungshosts verwalten muss.

##### <a name="deep-links-out-of-your-app"></a>Deep-Links aus Ihrer App

Verwenden Sie für Deep-Links von Ihrer App zu verschiedenen Bereichen des aktuellen Hosts die stark typisierten APIs, die vom TeamsJS-SDK bereitgestellt werden. Verwenden Sie beispielsweise die *Kalenderfunktion*, um ein Planungsdialogfeld oder ein Kalenderelement aus Ihrer App zu öffnen.

Verwenden Sie `pages.navigateToApp` für Deep-Links von Ihrer App zu anderen Apps, die auf demselben Host ausgeführt werden.

Für alle anderen externen Deep Linking-Szenarien können Sie `app.openLink` verwenden, das eine ähnliche Funktionalität wie die (seit TeamsJS v.2.0) veraltete *executeDeepLink*-API bereitstellt.

#### <a name="dialogs"></a>Dialoge

Ab Version 2.0 von TeamsJS wurde das Teams-Plattformkonzept des [Aufgabenmoduls](../../task-modules-and-cards/what-are-task-modules.md) in *Dialogfeld* umbenannt, um eine bessere Konsistenz mit vorhandenen Konzepten im Microsoft 365-Entwicklerökosystem zu erzielen. Dementsprechend wurde der Namespace `tasks` zugunsten des neuen Namespaces `dialog` eingestellt.

Diese neue Dialogfeldfunktion ist in eine Hauptfunktion (`dialog`) für die Unterstützung von HTML-basierten Dialogfeldern und eine Unterfunktion (`dialog.bot`) für die Bot-basierte Dialogfeldentwicklung unterteilt.

Die Dialogfeldfunktion unterstützt noch keine [Dialogfelder für adaptive Karten](../../task-modules-and-cards/task-modules/design-teams-task-modules.md). Auf adaptiven Karten basierende Dialogfelder müssen weiterhin mithilfe von `tasks.startTask()` aufgerufen werden.

Die Funktion `dialog.open` funktioniert derzeit nur zum Öffnen von HTMl-basierten Dialogfeldern und gibt eine Rückruffunktion (`PostMessageChannel`) zurück, die Sie zum Übergeben von Nachrichten (`ChildAppWindow.postMessage`) an das neu geöffnete Dialogfeld verwenden können.  `dialog.open` gibt einen Rückruf (anstelle einer Zusage) zurück, da die App-Ausführung nicht angehalten werden muss, bis das Dialogfelds wieder geschlossen wurde (was mehr Flexibilität für verschiedene Benutzerinteraktionsmuster bietet).

## <a name="whats-new-in-teamsjs-version-20"></a>Neuerungen in TeamsJS, Version 2.0

Es gibt zwei wesentliche Änderungen zwischen TeamsJS 1.x.x-Versionen und v.2.0.0 und höher:

* [**Rückruffunktionen geben jetzt Zusageobjekte zurück.**](#callbacks-converted-to-promises) Die meisten Funktionen mit Rückrufparametern in TeamsJS v.1.12 wurden so modernisiert, dass ein JavaScript [Zusageobjekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) zurückgegeben wird, um die Behandlung asynchroner Vorgänge und die Code-Lesbarkeit zu verbessern.

* [**APIs sind jetzt in *Funktionen* unterteilt.**](#apis-organized-into-capabilities) Stellen Sie sich Funktionen als logische Gruppierungen von APIs vor, die ähnliche Funktionen bereitstellen, z. B. `authentication`, `dialog`, `chat` und `calendar`. Jeder Namespace stellt eine separate Funktion dar.

> [!TIP]
> Sie können die [Teams-Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Microsoft Visual Studio Code verwenden, um den [TeamsJS v.2.0-Updateprozess](#updating-to-the-teams-client-sdk-v200) für eine vorhandene Teams-App zu vereinfachen.

### <a name="backwards-compatibility"></a>Abwärtskompatibilität

Sobald Sie beginnen, aus einer vorhandenen Teams-App auf `@microsoft/teams-js@2.0.0` (oder höher) zu verweisen, werden für alle geänderten Codeaufruf-APIs Warnungen wegen veralteter Funktionalität angezeigt.

Es wird eine API-Übersetzungsebene bereitgestellt (die v.1-SDK-Aufrufe zu v.2-SDK-API-Aufrufen zuordnet), damit vorhandene Teams-Apps weiterhin in Teams verwendet werden können, bis der Anwendungscode aktualisiert werden kann, um die TeamsJS v.2-API-Muster zu verwenden.

#### <a name="teams-only-apps"></a>Reine Teams-Apps

Selbst wenn Sie beabsichtigen, Ihre App nur in Teams auszuführen (und nicht in Office und Outlook), empfiehlt es sich, sobald wie möglich mit dem Verweisen auf die neuesten TeamsJS-Version (*v.2.0* oder höher) zu beginnen, um von den neuesten Verbesserungen, neuen Features und der Unterstützung zu profitieren (auch für reine Teams-Apps). TeamsJS v.1.12 wird weiterhin unterstützt, es werden jedoch keine neuen Features oder Verbesserungen hinzugefügt.

Sobald wie möglich besteht der nächste Schritt darin, [vorhandenen Anwendungscode mit den in diesem Artikel beschriebenen Änderungen zu aktualisieren](#2-update-sdk-references). In der Zwischenzeit bietet die Übersetzungsebene von der v.1- zur v.2-API Abwärtskompatibilität, sodass sichergestellt ist, dass Ihre vorhandene Microsoft Teams-App in TeamsJS, Version 2.0, weiterhin funktioniert.

#### <a name="teams-apps-running-across-microsoft-365"></a>Teams-Apps, die im gesamten Microsoft 365-Ölkosystem ausgeführt werden können

Damit eine vorhandene Teams-App in Outlook und Office ausgeführt werden kann, ist Folgendes erforderlich:

1. Abhängigkeit von TeamsJS Version 2.0 (`@microsoft/teams-js@2.0`) oder höher,

2. [Ändern des vorhandenen Anwendungscodes](#2-update-sdk-references) gemäß den in diesem Artikel beschriebenen erforderlichen Änderungen und

3. [Aktualisieren des App-Manifests](#3-update-the-manifest-optional) auf Version 1.13 oder höher.

Weitere Informationen finden Sie unter [Erweitern von Teams-Apps auf Microsoft 365](../../m365-apps/overview.md).

### <a name="callbacks-converted-to-promises"></a>In Zusagen konvertierte Rückrufe

Teams-APIs, die zuvor einen Rückrufparameter verwendeten, wurden aktualisiert, und geben nun ein JavaScript-[Zusageobjekt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) zurück. Dazu gehören die folgenden APIs:

```js
app.getContext, app.initialize, appInstallDialog.openAppInstallDialog, app.openLink, authentication.authenticate, authentication.getAuthToken, authentication.getUser, authentication.registerAuthenticationHandlers was removed to support using Promises, calendar.openCalendarItem, calendar.composeMeeting, call.startCall, chat.getChatMembers, conversations.openConversation, location.getLocation, location.showLocation, mail.openMailItem, mail.composeMail, pages.backStack.navigateBack, pages.navigateCrossDomain, pages.navigateToTab, pages.tabs.getMruTabInstances, pages.tabs.getTabInstances, pages.getConfig, pages.config.setConfig, pages.backStack.navigateBack, people.selectPeople, teams.fullTrust.getConfigSetting, teams.fullTrust.joinedTeams.getUserJoinedTeams
```

Sie müssen die Art und Weise aktualisieren, wie Ihr Code diese APIs aufruft, um Zusagen zu verwenden. Wenn Ihr Code z. B. eine Teams-API wie folgt aufruft:

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

... oder das entsprechende `async/await`-Muster:

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

... oder das entsprechende `async/await`-Muster:

```TypeScript
import { app, Context } from "@microsoft/teams-js";

async function example() {
  const context: Context = await app.getContext();
  /*...*/
}
```

---

> [!TIP]
> Wenn Sie das [Teams-Toolkit verwenden, um auf TeamsJS v.2.0 zu aktualisieren](#updating-to-the-teams-client-sdk-v200), werden die erforderlichen Updates für Sie mit `TODO`-Kommentaren in Ihrem Clientcode gekennzeichnet.

### <a name="apis-organized-into-capabilities"></a>In Funktionen unterteilte APIs

Eine *Funktion* ist eine logische Gruppierung (über Namespaces) von APIs, die ähnliche Funktionen bereitstellen. Sie können sich Microsoft Teams, Outlook und Office als Hosts für Ihre Registerkarten-App vorstellen. Ein Host unterstützt eine bestimmte Funktion, wenn er alle in dieser Funktion definierten APIs unterstützt. Ein Host kann eine Funktion nicht teilweise implementieren. Funktionen können feature- oder inhaltsbasiert sein, z. B. *authentication* (Authentifizierung) oder *dialog* (Dialogfeld). Es gibt auch Funktionen für Anwendungstypen wie *Seiten* und andere Gruppierungen.

Ab TeamsJS v.2.0 werden APIs als Funktionen in einem JavaScript-Namespace definiert, dessen Name der erforderlichen Funktion entspricht. Wenn eine App beispielsweise auf einem Host ausgeführt wird, der die *dialog*-Funktion (Dialogfeld) unterstützt, kann die App sicher APIs aufrufen, z. B. `dialog.open` (zusätzlich zu anderen dialogfeldbezogenen APIs, die im Namespace definiert sind). Wenn eine Anwendung versucht, eine API aufzurufen, die in diesem Host nicht unterstützt wird, erzeugt die API eine Ausnahme. Um zu überprüfen, ob der aktuelle Host, auf dem Ihre App ausgeführt wird, eine bestimmte Funktion unterstützt, rufen Sie die Funktion [isSupported()](#differentiate-your-app-experience) ihres Namespaces auf.

#### <a name="differentiate-your-app-experience"></a>Ableiten Ihrer App-Umgebung

Sie können die Hostunterstützung einer bestimmten Funktion zur Laufzeit überprüfen, indem Sie die Funktion `isSupported()` für diese Funktion (Namespace) aufrufen. `true` wird zurückgegeben, wenn die Funktion unterstützt wird und `false`, wenn nicht. Sie können das App-Verhalten entsprechend anpassen. Auf diese Weise kann Ihre App Benutzeroberflächen und Funktionen in Hosts nutzen, die diese unterstützen, kann aber weiterhin auch für Hosts ausgeführt werden, die diese nicht unterstützen.

Der Name des Hosts, auf dem Ihre App ausgeführt wird, wird als *hostName*-Eigenschaft auf der Context-Schnittstelle (`app.Context.app.host.name`) verfügbar gemacht und kann zur Laufzeit durch Aufrufen von `getContext` abgefragt werden. Er ist auch als `{hostName}` [URL-Platzhalterwert](./access-teams-context.md#get-context-by-inserting-url-placeholder-values) verfügbar. Eine bewährte Methode ist die sparsame Verwendung des *hostName*-Mechanismus:

* Gehen Sie **nicht** basierend auf dem *HostName*-Eigenschaftswert davon aus, dass bestimmte Funktionen auf einem Host verfügbar sind oder nicht verfügbar sind. Überprüfen Sie stattdessen die Unterstützung der Funktion (`isSupported`).
* Sie sollten *hostName* **nicht verwenden**, um API-Aufrufe Gates zuzuweisen. Überprüfen Sie stattdessen die Unterstützung der Funktion (`isSupported`).
* Sie sollten *hostName* **verwenden**, um das Design Ihrer Anwendung basierend auf dem Host, auf dem sie ausgeführt wird, zu unterscheiden. Sie können das Lila von Microsoft Teams beispielsweise als Hauptakzentfarbe verwenden, wenn die App in Teams ausgeführt wird, und das Blau von Outlook, wenn sie in Outlook ausgeführt wird.
* Sie sollten *hostName* **verwenden**, um Nachrichten, die dem Benutzer angezeigt werden, basierend auf dem Host, auf dem die App ausgeführt wird, zu unterscheiden. Zeigen Sie beispielsweise *Aufgaben in Office verwalten* an, wenn die App in Office im Web ausgeführt wird, und *Aufgaben in Teams verwalten*, wenn sie in Microsoft Teams ausgeführt wird.

#### <a name="namespaces"></a>Namespaces

Ab TeamsJS v.2.0 werden APIs mithilfe von Namespaces in *Funktionen* unterteilt. Einige neue Namespaces von besonderer Bedeutung sind *app*, *pages*, *dialog* und *teamsCore*.

##### <a name="app-namespace"></a>Namespace *app*(App)

Der Namespace `app` enthält APIs auf oberster Ebene, die für die allgemeine App-Nutzung über Microsoft Teams, Office und Outlook hinweg erforderlich sind. Alle APIs aus verschiedenen anderen TeamsJS-Namespaces wurden ab TeamsJS v.2.0 in den Namespace `app` verschoben:

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `app` |
| - | - |
| `executeDeepLink` | `app.openLink` (umbenannt) |
| `initialize` | `app.initialize` |
| `getContext` | `app.getContext` |
| `registerOnThemeChangeHandler` | `app.registerOnThemeChangeHandler` |

| Ursprünglicher Namespace `appInitialization` | Neuer Namespace `app` |
| - | - |
| `appInitialization.notifyAppLoaded` | `app.notifyAppLoaded` |
| `appInitialization.notifySuccess` | `app.notifySuccess` |
| `appInitialization.notifyFailure` | `app.notifyFailure` |
| `appInitialization.notifyExpectedFailure` | `app.notifyExpectedFailure` |
| `appInitialization.FailedReason`-Enumeration | `app.FailedReason` |
| `appInitialization.ExpectedFailureReason`-Enumeration | `app.ExpectedFailureReason` |
| `appInitialization.IFailedRequest`-Enumeration | `app.IFailedRequest` |
| `appInitialization.IExpectedFailureRequest`-Enumeration | `app.IExpectedFailureRequest` |

##### <a name="pages-namespace"></a>Namespace *pages* (Seiten)

Der Namespace `pages` enthält Funktionen zum Ausführen von und Navigieren in Webseiten innerhalb verschiedener Microsoft 365 Hosts, einschließlich Teams, Office und Outlook. Er enthält auch mehrere Unterfunktionen, die als Unternamespaces implementiert sind.

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `pages` |
| - | - |
| `setFrameContext` | `pages.setCurrentFrame` (umbenannt) |
| `initializeWithFrameContext` | `pages.initializeWithFrameContext` |
| `registerFocusEnterHandler` | `pages.registerFocusEnterHandler`
| `registerFullScreenHandler` | `pages.registerFullScreenHandler` |
| `navigateCrossDomain` | `pages.navigateCrossDomain` |
| `returnFocus` | `pages.returnFocus` |
| `shareDeepLink` | `pages.shareDeepLink` |

| Ursprünglicher Namespace `settings` | Neuer Namespace `pages`  |
| - | - |
| `settings.getSettings` | `pages.getConfig` (umbenannt)

###### <a name="pagestabs"></a>*pages.tabs*

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `pages.tabs` |
| - | - |
| `getTabInstances` |  `pages.tabs.getTabInstances` |
| `getMruTabInstances` | `pages.tabs.getMruTabInstances` |

| Ursprünglicher Namespace `navigation` | Neuer Namespace `pages.tabs` |
| - | - |
| `navigation.navigateToTab` | `pages.tabs.navigateToTab` |

###### <a name="pagesconfig"></a>*pages.config*

| Ursprünglicher Namespace `settings` | Neuer Namespace `pages.config`  |
| - | - |
| `settings.setSettings` | `pages.config.setConfig` (umbenannt)
| `settings.setValidityState`| `pages.config.setValidityState`
| `settings.initialize` | `pages.config.initialize`
| `settings.registerOnSaveHandler`| `pages.config.registerOnSaveHandler`
| `settings.registerOnRemoveHandler` | `pages.config.registerOnRemoveHandler`
| `settings.Settings`-Schnittstelle | `pages.config.Config` (umbenannt)
| `settings.SaveEvent`-Schnittstelle | `pages.config.SaveEvent` (umbenannt)
| `settings.RemoveEvent`-Schnittstelle | `pages.config.RemoveEvent` (umbenannt)
| `settings.SaveParameters`-Schnittstelle | `pages.config.SaveParameters` (umbenannt)
| `settings.SaveEventImpl`-Schnittstelle | `pages.config.SaveEventImpl` (umbenannt)

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `pages.config` |
| - | - |
| `registerChangeConfigHandler` | `pages.config.registerChangeConfigHandler` (umbenannt)

###### <a name="pagesbackstack"></a>*pages.backStack*

| Ursprünglicher Namespace `navigation` | Neuer Namespace `pages.backStack`  |
| - | - |
| `navigation.navigateBack` | `pages.backStack.navigateBack`

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `pages.backStack`  |
| - | - |
| `registerBackButtonHandler` | `pages.backStack.registerBackButtonHandler`

###### <a name="pagesappbutton"></a>*pages.appButton*

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `pages.appButton`  |
| - | - |
| `registerAppButtonClickHandler` | `pages.appButton.onClick` (umbenannt)
| `registerAppButtonHoverEnterHandler` | `pages.appButton.onHoverEnter` (umbenannt)
| `registerAppButtonHoverLeaveEnter` | `pages.appButton.onHoverLeave` (umbenannt)
| `FrameContext`-Schnittstelle | `pages.appButton.FrameInfo` (umbenannt) |

##### <a name="dialog-namespace"></a>Namespace *dialog* (Dialogfeld)

Der TeamsJS-Namespace *tasks* (Aufgaben) wurde in *dialog* (Dialogfeld) umbenannt, und die folgenden APIs wurden umbenannt:

| Ursprünglicher Namespace `tasks` | Neuer Namespace `dialog`  |
| - | - |
| `tasks.startTask` | `dialog.open` (umbenannt) |
| `tasks.submitTasks` | `dialog.submit` (umbenannt) |
| `tasks.updateTasks` | `dialog.update.resize` (umbenannt) |
| `tasks.TaskModuleDimension`-Enumeration | `dialog.DialogDimension` (umbenannt) |
| `tasks.TaskInfo`-Schnittstelle | `dialog.DialogInfo` (umbenannt) |

Außerdem wurde diese Funktion in eine Hauptfunktion (`dialog`) für die Unterstützung von HTML-basierten Dialogfeldern und eine Unterfunktion für die Bot-basierte Dialogfelder (`dialog.bot`) unterteilt.

##### <a name="teamscore-namespace"></a>Namespace *teamsCore*

Um das TeamsJS-SDK so zu generalisieren, dass andere Microsoft 365-Hosts wie Office und Outlook ausgeführt werden, wurde Teams-spezifische Funktionalität (ursprünglich im Namespace *global*) in einen *teamsCore*-Namespace verschoben:

| Ursprünglicher Namespace `global (window)` | Neuer Namespace `teamsCore`  |
| - | - |
| `enablePrintCapability` | `teamsCore.enablePrintCapability`
| `print` | `teamsCore.print`
| `registerOnLoadHandler` | `teamsCore.registerOnLoadHandler`
| `registerBeforeUnloadHandler` | `teamsCore.registerBeforeUnloadHandler`

#### <a name="updates-to-the-context-interface"></a>Aktualisierungen der *Context*-Schnittstelle

Die `Context`-Schnittstelle wurde in den Namespace `app` verschoben und aktualisiert, um ähnliche Eigenschaften für eine bessere Skalierbarkeit zu gruppieren, da sie neben Microsoft Teams auch in Outlook und Office ausgeführt werden kann.

Es wurde eine neue Eigenschaft `app.Context.app.host.name` hinzugefügt, mit der Registerkarten die Benutzeroberfläche je nach Hostanwendung unterscheiden können.

Sie können die Änderungen auch visualisieren, indem Sie die Funktion `transformLegacyContextToAppContext` in der [Microsoft TeamsJS v.2.0-Quelle](https://github.com/OfficeDev/microsoft-teams-library-js/blob/main/packages/teams-js/src/public/app.ts) (Datei *app.ts*) überprüfen.

| Ursprünglicher Name in der `Context`-Schnittstelle | Neuer Speicherort in `app.Context` |
| - | - |
| `appIconPosition` | `app.Context.app.iconPositionVertical` |
| `appLaunchId`| *NICHT IN TeamsJS v.2.0* |
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
|`userClickTime`| `app.Context.app.userClickTime`|
| `userFileOpenPreference` | `app.Context.app.userFileOpenPreference` |
| `userLicenseType`| `app.Context.user.licenseType` |
| `userObjectId` | `app.Context.user.id`|
| `userTeamRole` | `app.Context.team.userRole`|
| `userDisplayName` | `app.Context.user.displayName` |
| Nicht zutreffend | `app.Context.app.host.name`|

## <a name="updating-to-the-teams-client-sdk-v200"></a>Aktualisieren auf das Teams-Client-SDK v.2.0.0

Die einfachste Möglichkeit, Ihre Teams-App zur Verwendung von TeamsJS v.2.0 zu aktualisieren, ist die Verwendung der [Teams-Toolkit-Erweiterung](https://aka.ms/teams-toolkit) für Visual Studio Code. In diesem Abschnitt werden Sie durch die dazu erforderlichen Schritte geführt. Wenn Sie ihren Code lieber manuell aktualisieren möchten, finden Sie weitere Details zu erforderlichen API-Änderungen in den Abschnitten [In Zusagen konvertierte Rückrufe](#callbacks-converted-to-promises) und [APIs, die in Funktionen unterteilt sind](#apis-organized-into-capabilities).

### <a name="1-install-the-latest-teams-toolkit-visual-studio-code-extension"></a>1. Installieren der neuesten Teams Toolkit-Visual Studio-Codeerweiterung

Suchen Sie im *Marketplace für Visual Studio-Codeerweiterungen* nach **Teams-Toolkit**, und installieren Sie die Version `2.10.0` oder höher.

### <a name="2-update-sdk-references"></a>2. Aktualisieren der SDK-Verweise

Um in Outlook und Office ausgeführt werden zu können, muss Ihre App vom [npm-Paket](https://www.npmjs.com/package/@microsoft/teams-js/v/2.0.0) `@microsoft/teams-js@2.0.0` (oder höher) abhängig sein. Wenn Sie diese Schritte manuell ausführen möchten und weitere Informationen zu den API-Änderungen benötigen, lesen Sie die Abschnitte [In Zusagen konvertierte Rückrufe](#callbacks-converted-to-promises) und [APIs, die in Funktionen unterteilt sind](#apis-organized-into-capabilities).

1. Stellen Sie sicher, dass Sie über das [Teams-Toolkit](https://aka.ms/teams-toolkit) `v.2.10.0` oder höher verfügen
1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen Sie den Befehl `Teams: Upgrade Teams JS SDK references to support Outlook and Office apps` aus.

Nach Abschluss des Vorgangs hat das Hilfsprogramm Ihre `package.json`-Datei mit der Abhängigkeit von TeamsJS v.2.0 (`@microsoft/teams-js@2.0.0` oder höher), aktualisiert, und Ihre `*.js/.ts`- und `*.jsx/.tsx`-Dateien werden aktualisiert mit:

> [!div class="checklist"]
>
> * `package.json`-Verweise auf TeamsJS v.2.0
> * Importanweisungen für TeamsJS v.2.0
> * [Funktions-, Enumerations- und Schnittstellenaufrufe](#apis-organized-into-capabilities) an TeamsJS v.2.0
> * `TODO`-Kommentarerinnerungen zum Überprüfen von Bereichen, die von Änderungen an der [Kontextschnittstelle](#updates-to-the-context-interface) betroffen sein könnten
> * `TODO` Kommentarerinnerungen zum [Konvertieren von Rückruffunktionen in Zusagen](#callbacks-converted-to-promises)

> [!IMPORTANT]
> Code in HTML-Dateien wird von den Upgradetools nicht unterstützt und erfordert manuelle Änderungen.

### <a name="3-update-the-manifest-optional"></a>3. Aktualisieren des Manifests (optional)

Wenn Sie eine Teams-App so aktualisieren, dass sie in Office und Outlook ausgeführt werden kann, müssen Sie das App-Manifest auch auf Version 1.13 oder höher aktualisieren. Sie können dies ganz einfach mit dem Teams-Toolkit oder manuell erledigen.

# <a name="teams-toolkit"></a>[Teams Toolkit](#tab/manifest-teams-toolkit)

1. Öffnen Sie die *Befehlspalette*: `Ctrl+Shift+P`
1. Führen den Befehl **Teams: Upgrade des Teams-Manifests ausführen, um Outlook- und Office-Apps zu unterstützen**, und wählen Sie Ihre App-Manifestdatei aus. Änderungen werden direkt dort vorgenommen.

# <a name="manual-steps"></a>[Manuelle Anwendung](#tab/manifest-manual)

Öffnen Sie Ihr Microsoft Teams-App-Manifest, und aktualisieren Sie das `$schema` und die `manifestVersion` mit den folgenden Werten:

```json
{
    "$schema" : "https://developer.microsoft.com/json-schemas/teams/v1.13/MicrosoftTeams.schema.json",
    "manifestVersion" : "1.13"
}
```

---

Wenn Sie das Microsoft Teams-Toolkit zum Erstellen Ihrer persönlichen App verwendet haben, können Sie damit auch die Änderungen an der Manifestdatei validieren und Fehler identifizieren. Öffnen Sie die Befehlspalette `Ctrl+Shift+P`, und suchen Sie **Microsoft Teams: Manifestdatei validieren**, oder wählen Sie die Option im Menü „Bereitstellung“ des Microsoft Teams-Toolkits aus (suchen Sie nach dem Microsoft Teams-Symbol auf der linken Seite von Visual Studio Code).

:::image type="content" source="../../m365-apps/images/toolkit-validate-manifest-file.png" alt-text="Microsoft Teams-Toolkit-Option &quot;Manifestdatei validieren&quot; im Menü &quot;Bereitstellung&quot;":::

## <a name="next-steps"></a>Nächste Schritte

* Verwenden Sie die [TeamsJS-Referenz](/javascript/api/overview/msteams-client) für Ihre ersten Schritte mit dem Microsoft Teams JavaScript-Client-SDK.
* Im [Änderungsprotokoll](https://github.com/OfficeDev/microsoft-teams-library-js/blob/main/packages/teams-js/CHANGELOG.md) finden Sie die neuesten Updates für TeamsJS.
