---
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine Kanal Registerkarte für Ihre erste Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
title: Erstellen einer Microsoft Teams-Kanal Registerkarte
ms.openlocfilehash: d0846c3af23fd9df6013f989e9f455f711d05a5f
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210256"
---
# <a name="build-a-teams-channel-tab"></a>Erstellen einer Microsoft Teams-Kanal Registerkarte

In diesem Lernprogramm erstellen Sie eine einfache *Kanal Registerkarte*, eine Vollbildschirm-Inhaltsseite für einen Teamkanal oder Chat. Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte einer Kanal Registerkarte konfigurieren (beispielsweise benennen Sie die Registerkarte so um, dass Sie für Ihren Kanal sinnvoll ist).

## <a name="before-you-begin"></a>Bevor Sie beginnen

Sie benötigen eine grundlegende ausgeführte App für den Einstieg. Wenn Sie noch keinen haben, folgen Sie den [Anweisungen unter Build, und führen Sie Ihre Teams erste APP](../build-your-first-app/build-and-run.md)aus. Wenn Sie Ihr App-Projekt erstellen, wählen Sie nur die **Kanal Registerkarte "Gruppe" oder "Teams"** aus.

## <a name="your-assignment"></a>Ihre Zuordnung

Vor kurzem hat Ihre Organisation eine Registerkarte "Teams" mit Informationen zur Kontaktaufnahme mit wichtigen Funktionen (Help Desk, HR usw.) erstellt. Da die Registerkarte jedoch nur für den persönlichen Gebrauch verwendet wurde, muss jeder Benutzer die Registerkarte installieren, um ihn anzuzeigen, und die Annahme ist niedriger als erwartet. In anderen Worten: zu viele Arbeitskräfte wissen immer noch nicht, wie Sie zum Helpdesk gelangen.

Sie können diese Informationen leichter finden, indem Sie eine Kanal RegisterkarteErstellen, wodurch die Belastung der Installation einer APP durch alle Benutzer beseitigt wird. Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Nutzen einer ganzen Gruppe installieren.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Identifizieren einiger der Eigenschaften des App-Manifests und der für Kanal Registerkarten relevanten Gerüste
> * Erstellen von Registerkarten Inhalten
> * Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte
> * Zulassen der Konfiguration und Installation einer Registerkarte
> * Angeben eines vorgeschlagenen Registerkarten namens

## <a name="identify-relevant-app-project-components"></a>Identifizieren relevanter App-Projektkomponenten

Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen. Lassen Sie uns die Hauptkomponenten zum Erstellen einer Kanal Registerkarte betrachten.

### <a name="app-manifest"></a>App-Manifest

Der folgende Ausschnitt aus dem App-Manifest zeigt [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , der die Eigenschaften und Standardwerte enthält, die für Kanal Registerkarten relevant sind.

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

## <a name="create-your-tab-content"></a>Erstellen des Registerkarteninhalts

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

## <a name="create-your-tab-configuration-page"></a>Erstellen der Seite für die Registerkartenkonfiguration

Jede Kanal Registerkarte verfügt über eine Konfigurationsseite, eine modale mit mindestens einer Setup Option, die bei der Installation der App angezeigt wird. Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob Sie den Kanal oder den Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.

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

## <a name="allow-the-tab-to-be-configured-and-installed"></a>Konfigurieren und Installieren der Registerkarte zulassen

Damit Benutzer die Kanal Registerkarte erfolgreich konfigurieren und installieren können, müssen Sie die Host-URL hinzufügen, die Sie beim [Erstellen und durchführen ihrer ersten App](../build-your-first-app/build-and-run.md) für die Komponente "Konfigurationsseite" eingerichtet haben.

Wechseln Sie zu `TabConfig.js` und suchen Sie `microsoftTeams.settings.setSettings` . `"contentUrl"`Ersetzen Sie dabei den `localhost:3000` Teil der URL durch die Domäne, in der Sie den Registerkarteninhalt hosten (siehe Abbildung).

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

Stellen Sie außerdem sicher, dass `microsoftTeams.settings.setValidityState(true);` . Standardmäßig ist `false` die Schaltfläche **Speichern** auf der Konfigurationsseite jedoch deaktiviert, wenn Sie auf festgelegt ist.

## <a name="provide-a-suggested-tab-name"></a>Angeben eines vorgeschlagenen Registerkarten namens

Wenn Sie eine Registerkarte zur persönlichen Verwendung installieren, ist der Anzeigename die `name` Eigenschaft im `staticTabs` Teil des App-Manifests (beispielsweise " **meine Kontakte**"). Wenn Sie eine Kanal Registerkarte installieren, wird standardmäßig der App-Name angezeigt (beispielsweise **First-App**).

Dies ist möglicherweise in Ordnung, je nachdem, was Sie Ihre APP aufrufen, aber Sie möchten möglicherweise einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (beispielsweise **Team Kontakte**).

`TabConfig.js`Wechseln Sie in zu zurück zu `microsoftTeams.settings.setSettings` . Fügen `suggestedDisplayName` Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten (siehe Abbildung). Verwenden Sie den angegebenen Namen, oder erstellen Sie einen eigenen. Denken Sie daran, dass Sie in dem Manifest Benutzern erlauben, den Namen zu ändern, wenn Sie möchten.

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="view-the-channel-tab"></a>Anzeigen der Kanal Registerkarte

Um die Konfigurations-und Inhaltsseiten Ihrer Kanal Registerkarte anzuzeigen, müssen Sie Sie in einem Kanal oder Chat installieren.

1. Wählen Sie im Microsoft Teams-Client **apps**aus.
1. Wählen Sie **Upload a custom app** aus, und wählen Sie Ihre apps aus `Development.zip` .
1. Wählen Sie **zu einem Team hinzufügen** oder **zu einem Chat hinzufügen** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.
1. Wählen Sie **Einrichten einer Registerkarte**aus. Die Konfigurationsseite wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::
1. Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Der Inhalt wird angezeigt.<br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanal Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Teams-App mit einer Kanal Registerkarte, um nützliche Inhalte in Kanälen und Chats anzuzeigen.

## <a name="learn-more"></a>Weitere Informationen

* [Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.
* [Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.
* [Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.
* [Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.
* [Erstellen einer Registerkarte ohne Toolkit](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen. Möchten Sie versuchen, eine andere Art von Teams-APP zu erstellen?

> [!div class="nextstepaction"]
> [Erstellen eines bot](../build-your-first-app/build-bot.md)
