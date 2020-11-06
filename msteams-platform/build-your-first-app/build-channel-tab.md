---
title: Erste Schritte – Erstellen einer Kanal-und Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine Microsoft Teams-Kanal-und-Gruppen-Registerkarte.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 46b5410a1ae7c866f8998362765dfe5462df94cb
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931764"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Erstellen einer Kanal-und Gruppenregisterkarte für Microsoft Teams

In diesem Lernprogramm erstellen Sie eine einfache *Kanal Registerkarte* (auch als *Gruppe Registerkarte* bezeichnet), bei der es sich um eine voll Bild Seite für einen Teamkanal oder Chat handelt. Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Registerkarte konfigurieren (beispielsweise benennen Sie die Registerkarte so um, dass Sie für Ihren Kanal sinnvoll ist).

## <a name="your-assignment"></a>Ihre Zuordnung

Vor kurzem hat Ihre Organisation eine Teams-App erstellt, die eine Registerkarte zum Anzeigen wichtiger Kontaktinformationen (Helpdesk, HR usw.) verwendet. Da es sich jedoch um eine persönliche Registerkarte handelt, muss jeder Benutzer die Registerkarte installieren, um es anzuzeigen, und die Annahme ist niedriger als erwartet. In anderen Worten: zu viele Arbeitskräfte wissen immer noch nicht, wie Sie zum Helpdesk gelangen.

Sie können diese Informationen leichter finden, indem Sie eine Kanal RegisterkarteErstellen, wodurch die Belastung der Installation einer APP durch alle Benutzer beseitigt wird. Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Nutzen einer ganzen Gruppe hinzufügen.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts mithilfe des Microsoft Teams-Toolkits für Visual Studio Code
> * Identifizieren einiger der für Kanal-und Gruppenregisterkarten relevanten App-Konfigurationen und Gerüste
> * Erstellen von Registerkarten Inhalten
> * Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte
> * Angeben eines vorgeschlagenen Registerkarten namens
> * Lokales erstellen und Ausführen der APP
> * Querladen ihrer app in Teams zum Testen

## <a name="before-you-begin"></a>Bevor Sie beginnen

Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Das Microsoft Teams-Toolkit unterstützt die Konfiguration Ihrer APP und das Einrichten von für Kanal-und Gruppenregisterkarten relevanten Gerüsten, einschließlich einer grundlegenden Konfigurationsseite und einer Inhaltsseite, auf der ein "Hello, World!" angezeigt wird. Nachricht.

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter** aus.
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Überprüfen Sie die Optionen auf der Registerkarte **persönliche** und **Gruppen-oder Teams-Kanäle** . (In Kürze erfahren Sie, warum Sie beide Arten von Registerkarten benötigen.)
1. Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.  

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren der relevanten App-Projektkomponenten

Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen. Lassen Sie uns die Hauptkomponenten zum Erstellen einer Kanal-und Gruppenregisterkarte betrachten.

### <a name="app-configurations"></a>App-Konfigurationen

Sie können Ihre APP-Konfigurationen mithilfe von App Studio anzeigen und aktualisieren, die im Toolkit enthalten ist.

Während des Setups hat das Toolkit zunächst zwei wesentliche Komponenten von Kanal-und Gruppenregisterkarten konfiguriert:

* **Konfigurationsseite** : das Dialogfeld zum Hinzufügen einer Registerkarte zu einem Kanal oder Chat. (In App Studio können Sie diese Seite finden, indem Sie auf **Tabs > Registerkarte "Team"** wechseln.)
* **Inhaltsseite** : dort, wo Sie Ihren primären Inhalt anzeigen. (In App Studio können Sie diese Seite finden, indem Sie zu **Registerkarten wechseln > eine persönliche Registerkarte hinzufügen**.)

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst stellt die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Microsoft Teams bereit. Es gibt eine Menge, mit der Sie arbeiten können, aber im Moment müssen Sie sich nur auf Folgendes konzentrieren:

* Zwei Dateien, die sich im `src/components` Verzeichnis des Projekts befinden:
  * `Tab.js` zum Rendern der Inhaltsseite der Registerkarte.
  * `TabConfig.js` zum Rendern der Konfigurationsseite der Registerkarte.
* Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

## <a name="3-customize-your-tab-content-page"></a>3. Anpassen der Inhaltsseite der Registerkarte

Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.

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

Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` . Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).

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

Fügen Sie die folgende Regel zu hinzu `App.css` (befindet sich auch in `src/components` ), sodass die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a>4. Anpassen Ihrer Registerkarten-Konfigurationsseite

Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, ein Dialogfeld mit mindestens einer Setup Option, die angezeigt wird, wenn Benutzer Ihre APP hinzufügen. Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob Sie den Kanal oder den Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.

Fügen Sie der Konfigurationsseite einige benutzerdefinierte Inhalte hinzu. Wechseln Sie zum Verzeichnis des Projekts `src/components` , öffnen Sie `TabConfig.js` , und aktualisieren Sie den Platzhalterinhalt in `return()` (wie im folgenden Beispiel dargestellt).

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
> Geben Sie mindestens einige kurze Informationen zu Ihrer APP auf dieser Seite, da dies das erste Mal sein kann, dass Benutzer davon erfahren. Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungs Workflow](../tabs/how-to/authentication/auth-aad-sso.md)einschließen, was bei Registerkarten-Konfigurationsseiten üblich ist.

## <a name="5-provide-a-suggested-tab-name"></a>5. Angeben eines vorgeschlagenen Registerkarten namens

Wenn Sie eine Kanal-oder Gruppenregisterkarte hinzufügen, wird standardmäßig der App-Name angezeigt (beispielsweise **First-App** ).

Dies ist möglicherweise in Ordnung, je nachdem, was Sie Ihre APP aufrufen, aber Sie möchten möglicherweise einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (beispielsweise **Team Kontakte** ).

`TabConfig.js`Wechseln Sie in zu `microsoftTeams.settings.setSettings` . Fügen `suggestedDisplayName` Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten (siehe Abbildung). Verwenden Sie den angegebenen Namen, oder erstellen Sie einen eigenen. (Standardmäßig können Benutzer den Namen ändern, falls gewünscht.)

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a>6. erstellen und Ausführen der APP

Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.

(Diese Informationen sind auch im Toolkit verfügbar `README` .)

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!** Nachricht im Terminal. Ihre APP wird gestartet `https://localhost:3000` .

## <a name="7-sideload-your-app-in-teams"></a>7. querladen ihrer app in Microsoft Teams

Ihre APP ist zum Testen in Microsoft Teams verfügbar. Hierzu benötigen Sie ein Konto, das App-Sideloading zulässt. (Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)

1. Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.
1. Um Ihre APP-Inhalte in Microsoft Teams anzuzeigen, geben Sie an, wo Ihre APP aktiv ist ( `localhost` ) vertrauenswürdig ist:
   1. Öffnen Sie eine neue Registerkarte in demselben Browserfenster (standardmäßig Google Chrome), die nach Drücken von **F5** geöffnet wurde.
   1. Wechseln Sie zu `https://localhost:3000/tab` der Seite, und fahren Sie fort.
1. Wechseln Sie zurück zu Microsoft Teams. Wählen Sie im Dialogfeld **zu einem Team hinzufügen** oder **zu einem Chat hinzufügen** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.
1. Wählen Sie **Einrichten einer Registerkarte** aus. Die Konfigurationsseite wird in einem Dialogfeld angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::
1. Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Die Inhaltsseite wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanal Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Teams-App mit einer Registerkarte, in der Sie nützliche Inhalte in Kanälen und Chats anzeigen können.

## <a name="learn-more"></a>Mehr erfahren

* [Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.
* [Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.
* [Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.
* [Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.
* [Verwenden von Teams-Daten mit der Microsoft Graph-API](https://docs.microsoft.com/graph/teams-concept-overview)
* [Erstellen einer Registerkarte ohne Toolkit](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen. Möchten Sie versuchen, eine andere Art von Teams-APP zu erstellen?

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
