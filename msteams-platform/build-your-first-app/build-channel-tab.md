---
title: Erste Schritte – Erstellen eines Kanals und einer Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Kanal und eine Gruppenregisterkarte.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 0692d28653063c2f886db9a03e7136379edde9c3
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911877"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Erstellen eines Kanals und einer Gruppenregisterkarte für Microsoft Teams

In diesem Lernprogramm erstellen Sie eine einfache Kanalregisterkarte *(auch* als Gruppenregisterkarte *bezeichnet),* die eine Vollbildseite für einen Teamkanal oder Chat ist. Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Art von Registerkarte konfigurieren (benennen Sie die Registerkarte beispielsweise so um, dass sie für ihren Kanal von Bedeutung ist).

## <a name="your-assignment"></a>Ihre Zuordnung

Vor nicht langer Zeit hat Ihre Organisation eine Teams-App erstellt, die eine Registerkarte zum Anzeigen wichtiger Kontaktinformationen (Helpdesk, Personalabteilung usw.) verwendet. Da es sich jedoch um eine persönliche Registerkarte handelt, muss jeder Benutzer die Registerkarte installieren, um sie zu sehen, und die Akzeptanz ist geringer als erwartet. Mit anderen Worten: Zu viele Mitarbeiter wissen immer noch nicht, wie sie zum Helpdesk gelangen.

Sie können diese Informationen leichter finden, indem Sie eine Kanalregisterkarte erstellen. Dadurch entlasten Sie jeden, eine App zu installieren. Stattdessen kann ein Benutzer die Registerkarte in einem Kanal hinzufügen oder zum Vorteil einer ganzen Gruppe chatten.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts mithilfe des Microsoft Teams Toolkit for Visual Studio Code
> * Identifizieren einiger der für Kanalregisterkarten relevanten App-Konfigurationen und Gerüste
> * Erstellen von Registerkarteninhalten
> * Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte
> * Bereitstellen eines vorgeschlagenen Registerkartennamens
> * Erstellen und Lokales Ausführen Ihrer App
> * Querladen Ihrer App in Teams zu Testzwecken

## <a name="before-you-begin"></a>Vorabinformationen

Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die Entwicklung von Teams verstehen und [installieren.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Mit dem Microsoft Teams Toolkit können Sie Ihre App konfigurieren und ein Gerüst einrichten, das für Kanal- und Gruppenregisterkarten relevant ist, einschließlich einer einfachen Konfigurationsseite und einer Inhaltsseite mit dem Titel "Hello, World!" Nachricht.

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, in der Projekte ausführlicher erläutert werden.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** aus, und wählen :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: Sie **"Neue Teams-App erstellen" aus.**
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem Bildschirm** "Funktionen hinzufügen" die Option **"Tab"** und dann **"Weiter" aus.**
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.) Wählen Sie **die Registerkarte "Gruppen- oder Teams-Kanal" aus.**
1. Wählen **Sie "Fertig** stellen" am unteren Rand des Bildschirms aus, um das Projekt zu konfigurieren.  

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren relevanter Komponenten des App-Projekts

Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.

### <a name="app-configurations"></a>App-Konfigurationen

Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.

### <a name="app-scaffolding"></a>App-Gerüst

Das App-Gerüst stellt die Komponenten zum Rendern Ihrer Kanalregisterkarte in Teams zur Seite. Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:

* Zwei Dateien im Verzeichnis `src/components` Ihres Projekts:
  * `Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.
  * `TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.
* Microsoft Teams JavaScript-Client-SDK, das vorab in den Front-End-Komponenten Ihres Projekts geladen wird.

## <a name="3-customize-your-tab-content-page"></a>3. Anpassen der Registerkarteninhaltsseite

Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie den Code der Zeit nach belieben.

```JSX
<div>
  <h1>Important Contacts</h1>
    <ul>
      <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
      <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
      <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
    </ul>
</div>
```

Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` . Suchen Sie die `render()` Funktion, und fügen Sie Ihren Inhalt `return()` ein (wie dargestellt).

```JavaScript
render() {

    let userName = Object.keys(this.state.context).length > 0 ? this.state.context['upn'] : "";

    return (
    <div>
      <h1>Important Contacts</h1>
        <ul>
          <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
          <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
          <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
        </ul>
    </div>
    );
}
```

Fügen Sie die folgende Regel zu (auch in ) hinzu, damit die E-Mail-Links unabhängig vom verwendeten `App.css` Design leichter zu lesen `src/components` sind.

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a>4. Anpassen der Registerkartenkonfigurationsseite

Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale Mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen. Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob sie den Kanal oder chatten möchten, wenn die Registerkarte installiert ist.

Fügen Sie Ihrer Konfigurationsseite benutzerdefinierte Inhalte hinzu. Wechseln Sie zum Verzeichnis Ihres Projekts, öffnen Sie das Verzeichnis, und aktualisieren Sie den Platzhalterinhalt (wie im `src/components` `TabConfig.js` folgenden Beispiel `return()` gezeigt).

```JavaScript
return (
    <div>
      <h1>Add My Contoso Contacts</h1>
      <div>
        Select <b>Save</b> to add our organization's important contacts to this workspace.
      </div>
    </div>
);
```
 
> [!TIP]
> Stellen Sie auf dieser Seite mindestens einige kurze Informationen zu Ihrer App zur Verfügung, da dies das erste Mal sein kann, dass Benutzer mehr darüber wissen. Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)verwenden, der auf Registerkartenkonfigurationsseiten häufig verwendet wird.

## <a name="5-provide-a-suggested-tab-name"></a>5. Geben Sie einen vorgeschlagenen Registerkartennamen an.

Wenn Sie eine Kanalregisterkarte hinzufügen, wird standardmäßig der Name der App angezeigt (z. B. **First-App).**

Dies kann in Abhängigkeit von dem, was Sie Ihre App aufrufen, in Ordnung sein, Aber Sie möchten möglicherweise einen Namen bereitstellen, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (z. B. **Teamkontakte).**

1. Wechseln `TabConfig.js` Sie in zu `microsoftTeams.settings.setSettings` .
2. Fügen Sie `suggestedDisplayName` die Eigenschaft mit dem Registerkartennamen hinzu, der standardmäßig angezeigt werden soll. 
3. Verwenden Sie den im folgenden Beispiel angegebenen Namen, oder geben Sie Ihren Namen ein. (Standardmäßig können Benutzer den Namen ändern.)

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a>6. Erstellen und Ausführen Ihrer App

Im Interesse der Zeit erstellen und führen Sie Ihre App lokal aus.

(Diese Informationen sind auch im Toolkit `README` verfügbar.)

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.
1. Führen Sie `npm start` .

Nach Abschluss des Vorgangs wird erfolgreich **kompiliert!** im Terminal zu senden. Ihre App wird unter `https://localhost:3000` ausgeführt.

## <a name="7-sideload-your-app-in-teams"></a>7. Querladen Ihrer App in Teams

Ihre App kann in Teams testen. Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps ermöglicht. (Wenn Sie nicht sicher sind, ob Sie dies haben, erfahren Sie mehr über das Abrufen eines [Teams-Entwicklungskontos.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)

1. Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.
1. Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, dass der Ort, an dem Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:
   1. Öffnen Sie eine neue Registerkarte im selben Browserfenster (standardmäßig Google Chrome), das nach drücken von **F5 geöffnet wurde.**
   1. Wechseln Sie `https://localhost:3000/tab` zu der Seite, und fahren Sie mit der Seite fort.
1. Wechseln Sie zurück zu Teams. Wählen Sie im modalen Modus "Zu einem Team **hinzufügen"** oder "Zu einem Chat **hinzufügen"** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zu Testzwecken verwenden können.
1. Wählen **Sie "Registerkarte einrichten" aus.** Die Konfigurationsseite wird modal angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Konfigurationsseite für Kanalregisterkarten.":::
1. Wählen **Sie "Speichern"** aus, um die Registerkarte zu konfigurieren. Die Inhaltsseite wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Teams-App mit einer Registerkarte zum Anzeigen nützlicher Inhalte in Kanälen und Chats.

## <a name="learn-more"></a>Weitere Informationen

* Folgen Sie [unseren Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.
* Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.
* [Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)
* Nutzen von Microsoft Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).
* [Erstellen einer Registerkarte ohne toolkit](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen. Möchten Sie versuchen, eine andere Art von Teams-App zu erstellen?

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
