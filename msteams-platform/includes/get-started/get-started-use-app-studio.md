### <a name="use-app-studio-to-update-the-app-package"></a>Verwenden von App Studio zum Aktualisieren des App-Pakets

App Studio ist eine Teams-App, die Sie aus dem Teams Store installieren können. Es vereinfacht die Erstellung und Registrierung einer App.

Führen Sie die folgenden Schritte aus, um das App-Paket zu aktualisieren:

1. Um App Studio in Teams zu installieren, wählen Sie das **Symbol Apps** unten in der linken Leiste aus, und suchen Sie nach **App Studio:**

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Wählen Sie die **Kachel App Studio** aus, und wählen Sie **Installieren** aus. Das App Studio ist installiert:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Um das App-Paket für Ihre Teams-App zu erstellen, wählen Sie in **App Studio** die Registerkarte **Manifest-Editor** aus:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    Das Beispiel enthält ein eigenes Manifest und wurde entwickelt, um ein App-Paket zu erstellen, wenn das Projekt erstellt wird. Auf .NET erfolgt dies in Visual Studio und auf Node.js erfolgt dies durch Eingabe `gulp` der Befehlszeile im Stammverzeichnis des Projekts.

    ```bash
    $ gulp
    [13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
    [13:39:27] Starting 'clean'...
    [13:39:27] Starting 'generate-manifest'...
    [13:39:27] Finished 'generate-manifest' after 11 ms
    [13:39:27] Finished 'clean' after 21 ms
    [13:39:27] Starting 'default'...
    Build completed. Output in manifest folder
    [13:39:27] Finished 'default' after 62 μs
    ```

    Der Name des generierten App-Pakets lautet **helloworldapp.zip**. Sie können nach dieser Datei suchen, wenn der Speicherort in dem von Ihnen verwendeten Tool nicht klar ist.

1. Um dieses App-Paket zu ändern, wählen Sie Im **Manifest-Editor** **eine vorhandene App** importieren aus:

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Wählen Sie die **Kachel Hello World** für Ihre neu importierte App aus:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

Das folgende Bild zeigt das importierte App-Paket in App Studio:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Auf der linken Seite des Manifest-Editors befindet sich eine Liste der Schritte. Auf der rechten Seite befindet sich eine Liste der Eigenschaften, die für jeden Schritt ausgefüllt werden müssen. Wenn Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits abgeschlossen. Mit den nächsten Schritten können Sie die Eigenschaften der Hello World-App aktualisieren.

#### <a name="app-details"></a>App-Details

Wählen Sie **App-Details** unter **Details** aus. Wählen Sie die Schaltfläche **Generieren** aus, um eine neue App-ID zu erstellen.

Ihre neue App-ID ähnelt `2322041b-72bf-459d-b107-f4f335bc35bd` .

Gehen Sie die App-Details im rechten Bereich mit **Entwicklerinformationen** und **Brandingdetails** durch. Diese Details sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.

#### <a name="tabs"></a>Registerkarten

Es ist einfach, Registerkarten zu einer Teams App hinzuzufügen. Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können sie aktivieren.

##### <a name="team-tab"></a>Team-Registerkarte

Ihre App kann nur über eine Team-Registerkarte verfügen:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In diesem Beispiel wird auf der Registerkarte Team die Konfigurationsseite angezeigt. Wählen Sie das **Symbol ...** der **Tab-Konfigurations-URL** und wählen Sie **Bearbeiten** aus dem Dropdown-Menü aus. Ändern Sie die URL in die `https://yourteamsapp.ngrok.io/configure` Stelle, an der `yourteamsapp.ngrok.io` Sie durch die URL ersetzt werden müssen, die Sie beim [Hosten Ihrer App](#host-the-sample-app)verwendet haben.

##### <a name="personal-tabs"></a>Persönliche Registerkarten

Ihre App kann über bis zu 16 Registerkarten verfügen, einschließlich der Registerkarte Team.

Persönliche Registerkarten unterscheiden sich von der Registerkarte Team. **Hello Tab** ist bereits in der Liste der persönlichen Registerkarten mit einem Platzhalterwert `com.contoso.helloworld.hellotab` aufgeführt. Wählen Sie das **Symbol ...** der **Tab-Konfigurations-URL** und wählen Sie **Bearbeiten** aus dem Dropdown-Menü aus. Das folgende Dialogfeld wird angezeigt:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Aktualisieren Sie die folgenden Felder mit Ihrer App-URL:

- Ändern des Felds **Inhalts-URL** in `https://yourteamsapp.ngrok.io/hello`
- Ändern des Felds **Website-URL** in `https://yourteamsapp.ngrok.io/hello`

Ersetzen Sie die `yourteamsapp.ngrok.io` URL, die Sie beim Hosten Ihrer App verwendet haben.

#### <a name="bots"></a>Bots

Es ist einfach, die Bots-Funktionalität zu Ihrer App hinzuzufügen. Die Hello World-Beispiel-App hat bereits einen Bot als Teil des Beispiels, aber Sie müssen ihn bei Microsoft registrieren: 

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

Der Bot, der aus dem Beispiel importiert wurde, verfügt nicht über eine zugeordnete App-ID. Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.

> [!NOTE]
> Die von App Studio für den Bot erstellte App-ID unterscheidet sich von der app-ID, die für die App erstellt wurde. Jeder Bot in einer App benötigt eine eigene App-ID.

Führen Sie die folgenden Schritte aus, um Ihren Bot einzurichten:

1. Wählen Sie **Löschen** neben dem importierten Bot in der Bot-Liste aus. Jetzt gibt es keine Bots mehr zu zeigen. 
1. Wählen Sie **Setup** aus, um das Dialogfeld **Bot** einrichten anzuzeigen.

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Fügen Sie einen Bot-Namen **Contoso-Bot** hinzu, und aktivieren Sie alle drei Kontrollkästchen unter **Bereich**.
1. Wählen Sie **Speichern** aus, um das Dialogfeld zu beenden. App Studio registriert Ihren Bot bei Microsoft und zeigt Ihren neuen Bot in der Bot-Liste an. 
1. Öffnen Sie nun eine Textdatei im Notizblock und kopieren Sie Ihre neue Bot-ID und fügen Sie sie ein.
1. Klicken Sie auf **Neues Kennwort generieren**, und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre Bot-App-ID notiert haben.
1. Aktualisieren Sie die **Bot-Endpunktadresse** auf , und ersetzen Sie sie `https://yourteamsapp.ngrok.io/api/messages` durch die `yourteamsapp.ngrok.io` URL, die Sie beim Hosten Ihrer App verwendet haben.
1. Speichern Sie nun Ihre Textdatei, da Sie die Informationen aus der Datei zu Ihrer gehosteten App hinzufügen müssen, um eine sichere Kommunikation mit Ihrem Bot zu ermöglichen.

#### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Mit Messagingerweiterungen können Benutzer Informationen von Ihrem Dienst anfordern und diese Informationen veröffentlichen. Die Informationen werden in Form von Karten in die Kanalunterhaltung gepostet. Messagingerweiterungen werden am unteren Rand des Verfassenfeldes angezeigt.

Führen Sie die folgenden Schritte aus, um Ihre Messagingerweiterung einzurichten:

1. Wählen Sie **Messagingerweiterungen** unter **Funktionen** im linken Bereich von App Studio aus, um die Messagingerweiterung zu konfigurieren:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    Die Beispielnachrichtenerweiterung wird im Bereich **Messagingerweiterungen** aufgeführt.

1. Wählen Sie **Löschen** aus, um die Messagingerweiterung zu entfernen, wählen **Sie Einrichten** aus, und führen Sie dieselben Schritte aus, die für [Bots](#bots)verwendet werden. Das Dialogfeld **Messagingerweiterung** wird angezeigt.
1. Wählen Sie die Registerkarte **Vorhandene Bot verwenden** und wählen Sie aus einem meiner vorhandenen **Bots**.
1. Wählen Sie den Bot, den Sie erstellt haben, aus dem Dropdown-Menü aus. Fügen Sie einen **Bot-Namen** hinzu, und wählen Sie **Speichern** aus, um das Dialogfeld zu schließen.
1. Wählen Sie im Abschnitt **Befehl** die Option **Hinzufügen** aus. Um einen suchbasierten Befehl hinzuzufügen, wählen Sie die Option Benutzer zulassen aus, **um Ihren Dienst nach Informationen abzufragen, und fügen Sie diese in eine Nachrichtenoption ein.**
1. Geben Sie im Dialogfeld **Neuer Befehl** die folgenden Werte ein:

    Unter **neuem Befehl**:

    - **Befehls-ID**: Geben Sie zufälligen Text ein
    - **Titel**: Geben Sie den zufälligen Titel ein
    - **Beschreibung**: Geben Sie eine Zufällige Beschreibung ein

    Unter **Parameter**:

    - **Name**: Geben Sie den Parameternamen ein
    - **Titel**: Geben Sie den Kartentitel ein
    - **Beschreibung**: Geben Sie die Kartenbeschreibung ein

1. Nachdem Sie die Informationen eingegeben haben, wählen Sie **Speichern** aus, um das Dialogfeld zu schließen.

#### <a name="register-your-app-in-teams"></a>Registrieren Ihrer App in Teams

Führen Sie nach Eingabe der Details Ihrer App die folgenden Schritte aus, um Ihre App in Teams zu registrieren:

1. Verwenden Sie **Testen und Verteilen** von App Studio, um Ihre App in Teams zu installieren. 
1. Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot. Verwenden Sie für die Beispiel-App dieselbe App-ID und dasselbe Kennwort für die Bot- und Messaging-Erweiterung. 
1. Wählen Sie **Testen und Verteilen**  unter Fertig **stellen** im linken Bereich von App Studio aus:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Um Ihre App in Teams hochzuladen, wählen Sie unter **Testen und Verteilen** die Schaltfläche **Installieren** aus:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

1. Wählen Sie das Feld **Suchen** im Abschnitt **Hinzufügen zu einem Team** aus, und wählen Sie ein Team aus, um die Beispiel-App hinzuzufügen. Sie können ein spezielles Team zum Testen einrichten.
1. Wählen Sie die Schaltfläche **Installieren** am unteren Rand des Dialogfelds aus.

Ihre App ist jetzt in Teams verfügbar. Der Bot und die Messagingerweiterung funktionieren jedoch erst, wenn Sie die gehostete Anwendungsumgebung mit den App-IDs und Kennwörtern aktualisieren.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
