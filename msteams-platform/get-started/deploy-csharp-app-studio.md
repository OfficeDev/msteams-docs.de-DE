---
title: Bereitstellen Ihrer ersten App mit C# in App Studio
description: Erfahren Sie, wie Sie Microsoft Teams-Apps mit C# oder .NET bereitstellen. in App Studio
keywords: Erste Schritte .net c# csharp app studio
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.localizationpriority: medium
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 08afc6a5d83d49f1fa6c2543f8a0ee4e001a3dc4
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60721453"
---
# <a name="update-c-app-package-in-app-studio"></a>Aktualisieren des C#-App-Pakets in App Studio

> [!TIP]
> **Testen Sie das Entwicklerportal:** App Studio hat sich weiterentwickelt. Konfigurieren, verteilen und verwalten Sie Ihre Teams-Apps mit dem neuen [Entwicklerportal.](https://dev.teams.microsoft.com/)

App Studio ist eine Teams-App, die Sie aus dem Teams Store installieren können. Dies vereinfacht das Erstellen und Registrieren einer App.

Führen Sie die folgenden Schritte aus, um das App-Paket zu aktualisieren:

1. Um App Studio in Teams zu installieren, wählen Sie unten auf der linken Leiste das Symbol **"Apps"** aus, und suchen Sie nach **App Studio:**

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Wählen Sie die **Kachel "App Studio"** aus, und wählen Sie **"Installieren"** aus. App Studio ist installiert:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Um das App-Paket für Ihre Teams App zu erstellen, wählen Sie die Registerkarte **"Manifest-Editor"** in **App Studio** aus:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>


    Das Beispiel enthält ein eigenes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird. Die Datei "manifest.json" befindet sich in Visual Studio im Manifest unter ```Microsoft.Teams.Samples.HelloWorld.Web``` .

     In Visual Studio befindet sich die Datei manifest.json unter **Manifest** in `Microsoft.Teams.Samples.HelloWorld.Web` . Dieser Schritt wird in der folgenden Abbildung beschrieben:  
    
    <img  width="450px" alt="Build the app package on .NET with Visual Studio" src="~/assets/images/get-started/app-package-on-.NET-with-Visual-Studio.png"/>

1. Wählen Sie nun zum Ändern dieses App-Pakets im **Manifest-Editor** die Option **"Vorhandene App importieren"** aus:

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Wählen Sie die **Kachel "Hello World"** für Ihre neu importierte App aus:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

    Die folgende Abbildung zeigt das importierte App-Paket in App Studio:

    <img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

    Auf der linken Seite des Manifest-Editors finden Sie eine Liste der Schritte. Auf der rechten Seite gibt es eine Liste der Eigenschaften, die für jeden Schritt ausgefüllt werden müssen. Als Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits abgeschlossen. Mit den nächsten Schritten können Sie die Eigenschaften der Hello World-App aktualisieren.

#### <a name="app-details"></a>App-Details

Wählen Sie **App-Details** unter **Details** aus. Wählen Sie die Schaltfläche **"Generieren"** aus, um eine neue App-ID zu erstellen.

Ihre neue App-ID ähnelt `2322041b-72bf-459d-b107-f4f335bc35bd` .

Gehen Sie die App-Details im rechten Bereich durch, einschließlich **Entwicklerinformationen** und **Brandingdetails.** Diese Details sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.

#### <a name="tabs"></a>Registerkarten

Es ist einfach, einer Teams App Registerkarten hinzuzufügen. Die Beispiel-App unterstützt bereits mehrere Registerkarten, die Sie aktivieren können.

##### <a name="team-tab"></a>Registerkarte "Team"

Ihre App kann nur eine Teamregisterkarte haben:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In diesem Beispiel wird die Konfigurationsseite auf der Registerkarte "Team" angezeigt. Wählen Sie das **Symbol ...** der **Registerkartenkonfigurations-URL** aus, und wählen Sie im Dropdownmenü die Option **"Bearbeiten"** aus. Ändern Sie die URL in den Ort, an dem sie `https://yourteamsapp.ngrok.io/configure` durch die URL ersetzt werden `yourteamsapp.ngrok.io` muss, die Sie beim Hosten Ihrer App verwendet haben.

##### <a name="personal-tabs"></a>Persönliche Registerkarten

Ihre App kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte "Team".

Persönliche Registerkarten unterscheiden sich von der Registerkarte "Team". **Hello Tab** ist bereits in der Liste der persönlichen Registerkarten mit einem Platzhalterwert `com.contoso.helloworld.hellotab` aufgeführt. Wählen Sie das **Symbol ...** der **Registerkartenkonfigurations-URL** aus, und wählen Sie im Dropdownmenü die Option **"Bearbeiten"** aus. Das folgende Dialogfeld wird angezeigt:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Aktualisieren Sie die folgenden Felder mit Ihrer App-URL:

- Ändern des **Felds "Inhalts-URL"** in `https://yourteamsapp.ngrok.io/hello`
- Ändern sie das **Feld "Website-URL"** in `https://yourteamsapp.ngrok.io/hello`

Ersetzen Sie `yourteamsapp.ngrok.io` diese durch die URL, die Sie beim Hosten Ihrer App verwendet haben.

#### <a name="bots"></a>Bots

Es ist einfach, ihrer App die Bots-Funktionalität hinzuzufügen. Die Hello World-Beispiel-App verfügt bereits über einen Bot als Teil des Beispiels, Sie müssen ihn jedoch bei Microsoft registrieren: 

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

Dem Bot, der aus dem Beispiel importiert wurde, ist keine App-ID zugeordnet. Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.

> [!NOTE]
> Die app-ID, die von App Studio für den Bot erstellt wurde, unterscheidet sich von der App-ID, die für die App erstellt wurde. Jeder Bot in einer App benötigt eine eigene App-ID.

Führen Sie die folgenden Schritte aus, um Ihren Bot einzurichten:

1. Wählen Sie **"Löschen"** neben dem importierten Bot in der Botliste aus. Jetzt gibt es keine Bots mehr, die angezeigt werden können. 
1. Wählen Sie **"Setup"** aus, um das Dialogfeld **"Bot einrichten"** anzuzeigen.

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Fügen Sie einen Botnamen **"Contoso-Bot"** hinzu, und aktivieren Sie alle drei Kontrollkästchen unter **"Bereich".**
1. Wählen Sie **"Speichern"** aus, um das Dialogfeld zu beenden. App Studio registriert Ihren Bot bei Microsoft und zeigt Ihren neuen Bot in der Botliste an. 
1. Öffnen Sie nun eine Textdatei im Editor, und kopieren Sie Ihre neue Bot-ID, und fügen Sie sie ein.
1. Klicken Sie auf **"Neues Kennwort generieren",** und notieren Sie sich das Kennwort in derselben Textdatei, die Sie als Bot-App-ID angegeben haben.
1. Aktualisieren Sie die **Bot-Endpunktadresse** auf und ersetzen Sie sie `https://yourteamsapp.ngrok.io/api/messages` durch die `yourteamsapp.ngrok.io` URL, die Sie beim Hosten Ihrer App verwendet haben.
1. Speichern Sie nun Ihre Textdatei, da Sie die Informationen aus der Datei zu Ihrer gehosteten App hinzufügen müssen, um eine sichere Kommunikation mit Ihrem Bot zu ermöglichen.

#### <a name="messaging-extensions"></a>Messaging-Erweiterungen

MitHilfe von Messaging-Erweiterungen können Benutzer Informationen von Ihrem Dienst anfordern und diese Informationen veröffentlichen. Die Informationen werden in Form von Karten in der Kanalunterhaltung bereitgestellt. Messaging-Erweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt.

Führen Sie die folgenden Schritte aus, um Ihre Messaging-Erweiterung einzurichten:

1. Wählen Sie **Messaging-Erweiterungen** unter **"Funktionen"** im linken Bereich von App Studio aus, um die Messaging-Erweiterung zu konfigurieren:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    Die Beispiel-Messaging-Erweiterung ist im Bereich **"Messaging-Erweiterungen"** aufgeführt.

1. Wählen Sie **"Löschen"** aus, um die Messaging-Erweiterung zu entfernen, wählen Sie **"Einrichten"** aus, und führen Sie die gleichen Schritte aus, die für [Bots](#bots)verwendet werden. Das Dialogfeld **Messaging-Erweiterung** wird angezeigt.
1. Wählen Sie die Registerkarte **"Vorhandenen Bot verwenden"** und **"Aus einem meiner vorhandenen Bots auswählen" aus.**
1. Wählen Sie den Bot aus, den Sie im Dropdownmenü erstellt haben. Fügen Sie einen **Bot-Namen** hinzu, und wählen Sie **"Speichern"** aus, um das Dialogfeld zu schließen.
1. Wählen Sie im Abschnitt **"Befehl"** die Option **"Hinzufügen"** aus. Um einen suchbasierten Befehl hinzuzufügen, wählen Sie den Befehl **"Benutzer dürfen Ihren Dienst nach Informationen abfragen" aus, und fügen Sie diesen in eine Nachrichtenoption ein.**
1. Geben Sie im Dialogfeld **"Neu"** die folgenden Werte ein:

    Under **New command**:

    - **Befehls-ID:** Eingeben von zufälligen Text
    - **Title**: Enter random title
    - **Beschreibung:** Geben Sie eine zufällige Beschreibung ein.

    Under **Parameter**:

    - **Name:** Geben Sie den Parameternamen ein.
    - **Titel:** Geben Sie den Kartentitel ein
    - **Beschreibung:** Eingeben einer Kartenbeschreibung

1. Nachdem Sie die Informationen eingegeben haben, wählen Sie **Speichern** aus, um das Dialogfeld zu schließen.

#### <a name="register-your-app-in-teams"></a>Registrieren Ihrer App in Teams

Führen Sie nach der Eingabe der Details Ihrer App die folgenden Schritte aus, um Ihre App in Teams zu registrieren:

1. Verwenden Sie **"Testen" und verteilen** Sie App Studio, um Ihre App in Teams zu installieren.
1. Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot. Verwenden Sie für die Beispiel-App die gleiche App-ID und dasselbe Kennwort für Bot- und Messaging-Erweiterungen. 
1. Wählen Sie **"Testen" und "Verteilen"**  im linken Bereich von App Studio unter **"Fertig stellen"** aus:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Um Ihre App in Teams hochzuladen, wählen Sie die Schaltfläche **"Installieren"** unter **"Testen und Verteilen"** aus:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>
    
    > [!NOTE]
    > Wenn Sie die App nicht querladen können, überprüfen Sie, ob Sie das [hochladen von benutzerdefinierten Apps aktiviert](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option)haben.

1. Wählen Sie im Abschnitt **"Zu einem Team hinzufügen"** das **Suchfeld** aus, und wählen Sie ein Team aus, um die Beispiel-App hinzuzufügen. Sie können ein spezielles Team für Tests einrichten.
1. Wählen Sie unten im Dialogfeld die Schaltfläche **"Installieren"** aus.

    Ihre App ist jetzt in Teams verfügbar. Der Bot und die Messaging-Erweiterung funktionieren jedoch erst, wenn Sie die Gehostete Anwendungsumgebung mit den App-IDs und Kennwörtern aktualisieren.

    <img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>

## <a name="register-your-app-in-teams"></a>Registrieren Ihrer App in Teams

Führen Sie nach der Eingabe der Details Ihrer App die folgenden Schritte aus, um Ihre App in Teams zu registrieren:

1. Verwenden Sie die **Vorschau** des Entwicklerportals, um Ihre App in Teams zu installieren.

    :::image type="content" source="../assets/images/teams-toolkit-v2/preview-in-teams.png" alt-text="Abbildung der Schaltfläche &quot;Vorschau&quot;" border="false":::

1. Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot. Verwenden Sie für die Beispiel-App die gleiche App-ID und dasselbe Kennwort für Bot- und Messaging-Erweiterungen.

1. Wählen Sie **"Veröffentlichen zum Speichern"** **im** linken Bereich des Entwicklerportals aus:

    :::image type="content" source="../assets/images/teams-toolkit-v2/devp-publish-left-pane.png" alt-text="Abbildung der Option &quot;Veröffentlichen&quot; im linken Bereich" border="false":::

    > [!NOTE]
    > Wenn Sie die App nicht querladen können, überprüfen Sie, ob Sie das [hochladen von benutzerdefinierten Apps aktiviert](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option)haben.

1. Wählen Sie **"Hinzufügen"** aus, um die App auf Teams zu installieren.

    Ihre App ist jetzt in Teams verfügbar. Der Bot und die Messaging-Erweiterung funktionieren jedoch erst, wenn Sie die Gehostete Anwendungsumgebung mit den App-IDs und Kennwörtern aktualisieren.

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Die Beispiel-App erfordert, dass die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der Textdatei gespeichert haben.

1. Öffnen Sie den Projektmappen-Explorer.

    :::image type="content" source="../assets/images/get-started/csharp-repo-cloned.png" alt-text="Beispiel-Repository für c#-Teams-App" border="false":::

1. die Datei `appsettings.json` öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-v2/csharp-appsetting-json.png" alt-text="Abbildung der Datei &quot;appsettings.json&quot;" border="false":::

1. Aktualisieren Sie den **MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben.
1. Aktualisieren Sie das **MicrosoftAppPassword** mit dem Bot-Kennwort, das Sie gespeichert haben.

    :::image type="content" source="../assets/images/get-started/get-started-net-azure-add-keys.png" alt-text="Abbildung des Hinzufügens von Azure-Schlüsseln" border="false":::

    Nachdem Sie diese Änderungen vorgenommen haben, erstellen Sie die App neu. Wenn Sie ngrok verwenden, können Sie die App lokal ausführen und die App erneut bereitstellen, wenn Sie sie in Azure gehostet haben.

## <a name="test-the-app-capabilities-in-teams"></a>Testen der App-Funktionen in Teams

### <a name="test-your-tab"></a>Testen Der Registerkarte

Nachdem Sie die App in Teams installiert haben, konfigurieren Sie sie so, dass die Registerkarte angezeigt wird, die die App laden soll.

**So konfigurieren Sie die Registerkarte "App"**

1. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+"** aus, um eine neue Registerkarte hinzuzufügen.
1. Wählen Sie **"Hello World"** aus der **Registerkartenliste hinzufügen** aus. Es wird ein Konfigurationsdialogfeld angezeigt, in dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll.
1. Wählen Sie **Speichern** aus. Die `Hello World` Registerkarte wird mit der Registerkarte geladen.

    <img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testen Ihres Bots in Teams

Sie können den Bot jetzt in Teams testen.

**So testen Sie Ihren Bot**

- Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` diesen ein. Dieser Nachrichtentyp wird als **\@ Erwähnung** bezeichnet. Der Bot antwortet auf eine beliebige Nachricht, die Sie senden.

    <img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen Der Messaging-Erweiterung

**So testen Sie Ihre Messaging-Erweiterung**

1. Wählen Sie **...** unterhalb des Eingabefelds in der Unterhaltungsansicht aus. Ein Menü mit der **App "Hello World"** wird angezeigt.
1. Wählen Sie das Menü aus, es wird eine Reihe zufälliger Texte angezeigt. Sie können einen der zufälligen Texte auswählen, der in Ihre Unterhaltung eingefügt wird.

    <img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Wählen Sie einen der zufälligen Texte aus. Eine Karte, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist, wird angezeigt.

    <img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

| &nbsp; | &nbsp; |
|:--- | ---:|
|[Back](get-started-overview.md) | &nbsp; |
|