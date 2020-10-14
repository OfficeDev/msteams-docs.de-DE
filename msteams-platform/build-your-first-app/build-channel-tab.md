---
title: Erste Schritte – Erstellen einer Kanal-und Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine Microsoft Teams-Kanal-und-Gruppen-Registerkarte.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: f890754cdf4ca43f39c25e3ba24fcf47b08c5a9f
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452855"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a>Erstellen einer Kanal-und Gruppenregisterkarte für Microsoft Teams

In diesem Lernprogramm erstellen Sie eine einfache *Kanal Registerkarte* (auch als *Gruppe Registerkarte*bezeichnet), bei der es sich um eine voll Bild Seite für einen Teamkanal oder Chat handelt. Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Registerkarte konfigurieren (beispielsweise benennen Sie die Registerkarte so um, dass Sie für Ihren Kanal sinnvoll ist).

## <a name="your-assignment"></a>Ihre Zuordnung

Vor kurzem hat Ihre Organisation eine Registerkarte "Teams" mit Informationen zur Kontaktaufnahme mit wichtigen Funktionen (Help Desk, HR usw.) erstellt. Da die Registerkarte jedoch nur für den persönlichen Gebrauch verwendet wurde, muss jeder Benutzer die Registerkarte installieren, um ihn anzuzeigen, und die Annahme ist niedriger als erwartet. In anderen Worten: zu viele Arbeitskräfte wissen immer noch nicht, wie Sie zum Helpdesk gelangen.

Sie können diese Informationen leichter finden, indem Sie eine Kanal RegisterkarteErstellen, wodurch die Belastung der Installation einer APP durch alle Benutzer beseitigt wird. Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Nutzen einer ganzen Gruppe installieren.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts mithilfe des Microsoft Teams-Toolkits für Visual Studio Code
> * Identifizieren einiger der Eigenschaften des App-Manifests und der für Kanal-und Gruppenregisterkarten relevanten Gerüste
> * Lokal Hosten einer APP
> * Erstellen von Registerkarten Inhalten
> * Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte
> * Zulassen der Konfiguration und Installation einer Registerkarte
> * Angeben eines vorgeschlagenen Registerkarten namens

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Das Microsoft Teams-Toolkit hilft Ihnen beim Einrichten des App-Manifests und der für Kanal-und Gruppenregisterkarten relevanten Gerüste, einschließlich einer grundlegenden Konfigurationsseite und einer Inhaltsseite, auf der ein "Hello, World!" angezeigt wird. Nachricht.

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Register **Karte** dann **Gruppe oder Teams Kanal Registerkarte**.
1. Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.  

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren der relevanten App-Projektkomponenten

Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen. Lassen Sie uns die Hauptkomponenten zum Erstellen einer Kanal-und Gruppenregisterkarte betrachten.

### <a name="app-manifest"></a>App-Manifest

Der folgende Ausschnitt aus dem App-Manifest zeigt [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , der die Eigenschaften und Standardwerte für Kanal-und Gruppenregisterkarten enthält.

```JSON
"configurableTabs": [
    {
        "configurationUrl": "{baseUrl0}/config",
        "canUpdateConfiguration": true,
        "scopes": [
            "team",
            "groupchat"
        ]
    }
],
```

* `configurationUrl`: Die Host-URL für Ihre Registerkarten-Konfigurationsseite (muss https sein).
* `canUpdateConfiguration`: Wenn Sie auf festgelegt `true` ist, können Benutzer die Registerkarteneinstellungen ändern, die Registerkarte umbenennen oder aus einem Kanal oder Chat entfernen.
* `scopes`: Gibt an, ob Benutzer die app in Kanälen ( `team` ) und Chats installieren können ( `groupchat` ). Mindestens ein Wert ist erforderlich.

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst stellt eine `TabConfig.js` Datei bereit, die sich im `src/components` Verzeichnis des Projekts befindet, um die Konfigurationsseite der Registerkarte zu rendern (Weitere Informationen dazu in Kürze).

## <a name="3-run-your-app"></a>3. führen Sie Ihre APP aus.

Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!** Nachricht im Terminal.

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a>4. Einrichten eines sicheren Tunnels für Ihre APP

Für Testzwecke hosten wir die Registerkarte auf einem lokalen Webserver (Port 3000).

1. Führen Sie in einem Terminal aus `ngrok http 3000` .
1. Kopieren Sie die HTTPS-URL, die Sie bereitgestellt haben.
1. Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .
1. Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL. (Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

Ihr App-Manifest zeigt auf die Stelle, an der Sie die Registerkarte hosten.

## <a name="5-customize-your-tab-content-page"></a>5. Anpassen der Inhaltsseite für Registerkarten

Öffnen Sie das App-Manifest ( `manifest.json` ) im `.publish` Verzeichnis, und legen Sie die folgenden Eigenschaften in fest [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , die die Inhaltsseite ihrer Registerkarte definiert.

```JSON
"staticTabs": [
    {
        "entityId": "index",
        "name": "My Contacts",
        "contentUrl": "{baseUrl0}/tab",
        "scopes": [ "personal" ]
    }
],
```

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

Fügen Sie die folgende Regel hinzu, `App.css` damit die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.

```CSS
a {
  color: inherit;
}
```

## <a name="6-create-your-tab-configuration-page"></a>6. Erstellen Ihrer Registerkarten-Konfigurationsseite

Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale mit mindestens einer Setup Option, die angezeigt wird, wenn Benutzer ihre App installieren. Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob Sie den Kanal oder den Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.

Fügen Sie der Konfigurationsseite einige Inhalte hinzu. Wechseln Sie zum Verzeichnis Ihres Projekts `src/components` , öffnen Sie `TabConfig.js` und fügen Sie einige Inhalte in ein `return()` (siehe Abbildung).

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

## <a name="7-allow-the-tab-to-be-configured-and-installed"></a>7. zulassen, dass die Registerkarte konfiguriert und installiert wird

Damit Benutzer die Registerkarte erfolgreich konfigurieren und installieren können, müssen Sie die [sichere Host-URL](#4-set-up-a-secure-tunnel-to-your-app) hinzufügen, die Sie der Konfigurationsseiten Komponente eingerichtet haben.

Wechseln Sie zu `TabConfig.js` und suchen Sie `microsoftTeams.settings.setSettings` . `"contentUrl"`Ersetzen Sie dabei den `localhost:3000` Teil der URL durch die Domäne, in der Sie den Registerkarteninhalt hosten (siehe Abbildung).

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

Stellen Sie außerdem sicher, dass `microsoftTeams.settings.setValidityState(true);` . Standardmäßig ist `false` die Schaltfläche **Speichern** auf der Konfigurationsseite jedoch deaktiviert, wenn Sie auf festgelegt ist.

## <a name="8-provide-a-suggested-tab-name"></a>8. Angeben eines vorgeschlagenen Registerkarten namens

Wenn Sie eine Registerkarte zur persönlichen Verwendung installieren, ist der Anzeigename die `name` Eigenschaft im `staticTabs` Teil des App-Manifests (beispielsweise " **meine Kontakte**"). Wenn Sie eine Kanal Registerkarte installieren, wird standardmäßig der App-Name angezeigt (beispielsweise **First-App**).

Dies ist möglicherweise in Ordnung, je nachdem, was Sie Ihre APP aufrufen, aber Sie möchten möglicherweise einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (beispielsweise **Team Kontakte**).

`TabConfig.js`Wechseln Sie in zu zurück zu `microsoftTeams.settings.setSettings` . Fügen `suggestedDisplayName` Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten (siehe Abbildung). Verwenden Sie den angegebenen Namen, oder erstellen Sie einen eigenen. Denken Sie daran, dass Sie in dem Manifest Benutzern erlauben, den Namen zu ändern, wenn Sie möchten.

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="9-view-the-tab"></a>9. Anzeigen der Registerkarte

Um die Konfigurations-und Inhaltsseiten ihrer Registerkarte anzuzeigen, müssen Sie Sie in einem Kanal oder Chat installieren.

1. Wählen Sie im Microsoft Teams-Client **apps**aus.
1. Wählen Sie **Upload a custom app** aus, und wählen Sie Ihre apps aus `Development.zip` .
1. Wählen Sie **zu einem Team hinzufügen** oder **zu einem Chat hinzufügen** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.
1. Wählen Sie **Einrichten einer Registerkarte**aus. Die Konfigurationsseite wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::
1. Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Der Inhalt wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Teams-App mit einer Registerkarte, in der Sie nützliche Inhalte in Kanälen und Chats anzeigen können.

## <a name="learn-more"></a>Weitere Informationen

* [Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.
* [Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.
* [Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.
* [Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.
* [Erstellen einer Registerkarte ohne Toolkit](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen. Möchten Sie versuchen, eine andere Art von Teams-APP zu erstellen?

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
