---
title: Erste Schritte – Erstellen einer Kanal- und Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Kanal und eine Gruppenregisterkarte.
ms.author: lajanuar
localization_priority: Normal
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: aadab4b6826b026eadd5ed564b6e5de5c29b4b1d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020877"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Erstellen einer Kanal- und Gruppenregisterkarte für Microsoft Teams

In diesem Lernprogramm erstellen Sie eine einfache Kanalregisterkarte *(auch* als Gruppenregisterkarte *bezeichnet),* die eine Vollbildseite für einen Teamkanal oder Chat ist. Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Art von Registerkarte konfigurieren (z. B. die Registerkarte umbenennen, sodass sie für ihren Kanal sinnvoll ist).

## <a name="your-assignment"></a>Ihre Zuordnung

Vor nicht langer Zeit hat Ihre Organisation eine Teams-App erstellt, die eine Registerkarte zum Anzeigen wichtiger Kontaktinformationen (Helpdesk, Personalwesen usw.) verwendet. Da es sich jedoch um eine persönliche Registerkarte handelt, muss jeder Benutzer die Registerkarte installieren, um sie zu sehen, und die Akzeptanz ist niedriger als erwartet. Anders ausgedrückt: Zu viele Mitarbeiter wissen noch nicht, wie sie den Helpdesk erreichen.

Sie können diese Informationen leichter finden, indem Sie eine Kanalregisterkarte erstellen. Dadurch wird der Aufwand für die Installation einer App durch alle Benutzer beseitigt. Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Vorteil einer gesamten Gruppe hinzufügen.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts mithilfe des Microsoft Teams Toolkits für Visual Studio Code
> * Identifizieren einiger der für Kanalregisterkarten relevanten App-Konfigurationen und Gerüste
> * Erstellen von Registerkarteninhalten
> * Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte
> * Bereitstellen eines vorgeschlagenen Registerkartennamens
> * Erstellen und Ausführen Ihrer App lokal
> * Querladen Ihrer App in Teams zu Testzwecken

## <a name="before-you-begin"></a>Bevor Sie beginnen

Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die [Teams-Entwicklung verstehen und installieren.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Mit dem Microsoft Teams Toolkit können Sie Ihre App konfigurieren und ein Gerüst einrichten, das für Kanal- und Gruppenregisterkarten relevant ist, einschließlich einer grundlegenden Konfigurationsseite und einer Inhaltsseite, auf der "Hello, World!" angezeigt wird. Nachricht.

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, die Projekte ausführlicher erläutern.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem** Bildschirm Funktionen hinzufügen die Option **Tab** und dann **Weiter aus.**
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.) Wählen **Sie Die Registerkarte Gruppen- oder Teams-Kanal aus.**
1. Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, um Ihr Projekt zu konfigurieren.  

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren relevanter App-Projektkomponenten

Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.

### <a name="app-configurations"></a>App-Konfigurationen

Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.

### <a name="app-scaffolding"></a>App-Gerüst

Das App-Gerüst stellt die Komponenten zum Rendern Ihrer Kanalregisterkarte in Teams zur Seite. Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:

* Zwei Dateien im `src/components` Verzeichnis Ihres Projekts:
  * `Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.
  * `TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.
* Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

## <a name="3-customize-your-tab-content-page"></a>3. Anpassen der Registerkarteninhaltsseite

Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie den Code aus Zeitgründen wie folgt.

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

Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` . Suchen Sie die `render()` Funktion, und fügen Sie Den Inhalt ein `return()` (wie dargestellt).

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

Fügen Sie die folgende Regel zu hinzu (ebenfalls in ), damit die E-Mail-Links unabhängig vom verwendeten `App.css` Design leichter zu lesen `src/components` sind.

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a>4. Anpassen der Registerkartenkonfigurationsseite

Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale Mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen. Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob sie den Kanal oder Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.

Fügen Sie ihrer Konfigurationsseite benutzerdefinierte Inhalte hinzu. Wechseln Sie zum Verzeichnis Ihres Projekts, öffnen Sie , und aktualisieren Sie den Platzhalterinhalt `src/components` `TabConfig.js` darin `return()` (wie im folgenden Beispiel gezeigt).

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
> Geben Sie zumindest einige kurze Informationen zu Ihrer App auf dieser Seite an, da dies das erste Mal sein kann, dass Benutzer davon lernen. Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)hinzufügen, der auf Registerkartenkonfigurationsseiten üblich ist.

## <a name="5-provide-a-suggested-tab-name"></a>5. Geben Sie einen vorgeschlagenen Registerkartennamen an.

Wenn Sie eine Kanalregisterkarte hinzufügen, wird standardmäßig der App-Name angezeigt (z. B. **First-App**).

Dies kann in Abhängigkeit von dem, was Sie Ihre App aufrufen, in Ordnung sein, aber Sie möchten möglicherweise einen Namen bereitstellen, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (z. B. **Teamkontakte**).

1. Wechseln `TabConfig.js` Sie in zu `microsoftTeams.settings.setSettings` .
2. Fügen Sie `suggestedDisplayName` die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten. 
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

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

Sobald sie abgeschlossen sind, wird ein **Kompiliert erfolgreich erstellt!** -Nachricht im Terminal. Ihre App wird auf `https://localhost:3000` ausgeführt.

## <a name="7-sideload-your-app-in-teams"></a>7. Querladen Ihrer App in Teams

Ihre App kann in Teams testen. Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps zulässt. (Wenn Sie nicht sicher sind, dass Sie dies haben, erfahren Sie mehr über das Abrufen eines [Teams-Entwicklungskontos.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)

1. Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.
1. Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, wo Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:
   1. Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (Standardmäßig Google Chrome), das nach dem Drücken von **F5 geöffnet wurde.**
   1. Wechseln Sie `https://localhost:3000/tab` zu und fahren Sie mit der Seite fort.
1. Wechseln Sie zurück zu Teams. Wählen Sie im modalen Modus **Hinzufügen zu einem** Team oder **Zu** einem Chat hinzufügen aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.
1. Wählen **Sie Tab einrichten aus.** Die Konfigurationsseite wird modal angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanalregisterkartenkonfigurationsseite.":::
1. Wählen **Sie Speichern** aus, um die Registerkarte zu konfigurieren. Die Inhaltsseite wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a>Gut gemacht

Glückwunsch! Sie verfügen über eine Teams-App mit einer Registerkarte zum Anzeigen nützlicher Inhalte in Kanälen und Chats.

## <a name="learn-more"></a>Weitere Informationen

* Befolgen Sie [unsere Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.
* Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.
* [Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)
* Verwenden von Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).
* [Erstellen einer Registerkarte ohne toolkit](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen. Möchten Sie versuchen, eine andere Art von Teams-App zu erstellen?

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
