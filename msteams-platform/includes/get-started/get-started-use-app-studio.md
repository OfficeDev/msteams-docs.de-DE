### <a name="use-app-studio-to-update-the-app-package"></a>Verwenden von App Studio zum Aktualisieren des App-Pakets

App Studio ist eine Teams-App, die Sie aus dem Teams Store installieren können. Dies vereinfacht das Erstellen und Registrieren einer App.

Um App Studio in Teams zu installieren, wählen Sie das Symbol **"Apps"** am unteren Rand der linken Leiste aus, und suchen Sie nach **App Studio.**

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

Wählen Sie die **Kachel "App Studio"** und dann **"Installieren" aus.** App Studio ist installiert.

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

Wählen Sie die **Registerkarte "Manifest-Editor"** aus, um das App-Paket für Ihre Teams-App zu erstellen.

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

Das Beispiel enthält ein eigenes vordefiniertes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird. In .NET erfolgt dies in Visual Studio, und auf Knoten JS erfolgt dies durch Eingabe an der Befehlszeile im Stammverzeichnis `gulp` des Projekts.

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

Der Name des generierten App-Pakets **isthelloworldapp.zip**. Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.

Um nun dieses App-Paket zu ändern, wählen Sie die **Kachel "Vorhandene** App importieren" im **Manifest-Editor aus.**

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

Klicken Sie **auf die Kachel "Hello World"** für Ihre neu importierte App.

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

Die folgende Abbildung zeigt das importierte App-Paket in App Studio:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die für jeden dieser Schritte ausgefüllt werden müssen. Seit Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits ausgefüllt. In den nächsten Schritten werden Sie durch das Ändern der Noch zu aktualisierenden Teile gehen.

#### <a name="app-details"></a>Details zur App

Klicken Sie unter *"Details" auf* den Eintrag *"App-Details".* Klicken *Sie* auf die Schaltfläche "Generieren", um eine neue App-ID zu erstellen.

Ihre neue App-ID sollte in etwa so aussehen: `2322041b-72bf-459d-b107-f4f335bc35bd` .

Sehen Sie sich die restlichen Details der App im rechten Bereich an,  und machen Sie sich mit einigen Einträgen wie Entwicklerinformationen und *Branding vertraut.* Diese Abschnitte sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Registerkarten gehören zu den einfachsten Elementen, die einer Teams-App hinzugefügt werden können. Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können sie wie folgt aktivieren.

##### <a name="team-tab"></a>Registerkarte "Team"

Ihre App kann nur eine Teamregisterkarte haben.

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In diesem Beispiel wird auf der Registerkarte "Team" die Konfigurationsseite angezeigt. Klicken Sie am *Ende* des Eintrags auf das Symbol ..., und wählen Sie *in* der Dropdownliste "Bearbeiten" aus. Ändern Sie die URL so, dass sie durch die URL ersetzt werden soll, die Sie oben beim `https://yourteamsapp.ngrok.io/configure` `yourteamsapp.ngrok.io` Hosten Ihrer App verwendet haben.

##### <a name="personal-tabs"></a>Persönliche Registerkarten

Ihre App kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte "Team".

Persönliche Registerkarten werden anders dargestellt als die Registerkarte "Team". Die Registerkarte *"Hello" sollte* bereits in der Liste der persönlichen Registerkarten aufgeführt sein. Zurzeit hat sie einen `com.contoso.helloworld.hellotab` Platzhalterwert. Klicken Sie am *Ende* des Eintrags auf das Symbol ..., und wählen Sie *in* der Dropdownliste "Bearbeiten" aus. Das folgende Dialogfeld wird angezeigt.

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Es gibt zwei Felder, die Sie mit Ihrer App-URL aktualisieren müssen.

- Ändern der Inhalts-URL in `https://yourteamsapp.ngrok.io/hello`
- Ändern der Website-URL in `https://yourteamsapp.ngrok.io/hello`

Wo `yourteamsapp.ngrok.io` sollte die URL ersetzt werden, die Sie oben beim Hosten Ihrer App verwendet haben.

#### <a name="bots"></a>Bots

Bots sind die am häufigsten verwendeten Möglichkeit, Ihrer App Funktionen hinzuzufügen. Das Beispiel "Hello World" hat bereits einen Bot als Teil des Beispiels, wurde aber noch nicht bei Microsoft registriert.

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

Dem Bot, der aus dem Beispiel importiert wurde, ist noch keine App-ID zugeordnet. Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann. Beachten Sie, dass dies die App-ID für den Bot ist, die sich von der für die App erstellten App-ID abh?nt. Jeder Bot in einer App benötigt eine eigene App-ID.

Klicken Sie *auf die Schaltfläche* "Löschen" neben dem *importierten Bot* in der Botliste.

Jetzt gibt es keine Bots mehr, die sie anzeigen können. Klicken Sie *auf Setup*. Dadurch wird das Dialogfeld *"Bot einrichten"* angezeigt.

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

Fügen Sie einen Botnamen wie hinzu, und wählen Sie unter Bereich `Contoso bot` alle drei **Schaltflächen aus.**

Choose *Create bot* to exit the dialog. App Studio registriert Ihren Bot bei Microsoft und zeigt den neuen Bot in der Botliste an. Jetzt wäre es ein guter Zeitpunkt, eine Textdatei im Editor zu öffnen und Ihre neue Bot-ID zu kopieren und in sie zu einfügen. Sie benötigen diese ID später.

Klicken *Sie auf "Neues Kennwort generieren",* und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre Bot-App-ID notiert haben. Dies ist das einzige Mal, dass Ihr Kennwort angezeigt wird. Stellen Sie daher sicher, dass Sie dies jetzt tun.

Aktualisieren Sie die *Adresse des Bot-Endpunkts* auf , wo sie durch die URL ersetzt werden sollte, die Sie oben beim `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` Hosten Ihrer App verwendet haben.

Jetzt wäre es ein guter Zeitpunkt, Ihre Textdatei zu speichern, wenn Sie dies noch nicht getan haben. Sie fügen diese Informationen später in dieser exemplarischen Vorgehensweise zu Ihrer gehosteten App hinzu, was eine sichere Kommunikation mit Ihrem Bot ermöglicht.

#### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Mit Messagingerweiterungen können Benutzer Informationen von Ihrem Dienst ein- und ausstellen und diese Informationen in Form von Karten direkt in der Kanal unterhaltung veröffentlichen. Messagingerweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt.

Wählen **Sie messaging extensions** under **Capabilities** in the left-hand column of App Studio to configure the messaging extension.

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

Die Beispiel-Messaging-Erweiterung ist im rechten Bereich unter **"Messaging Extensions" aufgeführt.** Wählen **Sie erneut** "Löschen" aus,  um diesen Eintrag zu entfernen, und klicken Sie dann auf die Schaltfläche "Einrichten", indem Sie die gleichen Schritte wie für Bots ausführen. Dadurch wird das Dialogfeld *"Messagingerweiterung"* angezeigt.

Wählen Sie *die Registerkarte "Vorhandenen Bot verwenden"* aus, und wählen Sie dann aus einem meiner *vorhandenen Bots aus.* Wählen Sie im Dropdownmenü den Bot aus, den Sie im abschnitt oben erstellt haben. Fügen Sie einen *Botnamen hinzu,* und klicken *Sie auf "Speichern",* um das Dialogfeld zu schließen.

Klicken Sie *im Befehlsabschnitt* auf *"Hinzufügen".* We're adding a search-based command, so choose the *Allow users to query your service...* option.

Geben Sie **im Dialogfeld "Neu"** die folgenden Werte ein.

Under *New command*:

- *Befehls-ID*  = getRandomText
- *Title*       = Get some random text for fun
- *Beschreibung* = Ruft zufälligen Text und Bilder ab

Under *Parameter*:

- *Name*        = cardTitle
- *Titel*       = Kartentitel
- *Beschreibung* = Zu verwendende Kartentitel

Nachdem Sie die Informationen eingegeben haben, klicken Sie auf *"Speichern",* um das Dialogfeld zu schließen.

#### <a name="register-your-app-in-teams"></a>Registrieren Ihrer App in Teams

Sie haben nun die Eingabe der Details Ihrer App abgeschlossen, aber die folgenden beiden Schritte bleiben bestehen:
1. Verwenden Sie den Abschnitt "Testen und Verteilen" von App Studio, um Ihre App in Teams zu installieren.
1. Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot. Denken Sie daran, dass im Beispiel davon ausging, die gleiche App-ID und dasselbe Kennwort sowohl für den Bot als auch für die Messagingerweiterung zu verwenden.

Wählen Sie das Element  **"Testen" und "Verteilen"** unter "Fertig stellen" in der linken Spalte von App Studio aus.

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

Um Ihre App in Teams hochzuladen, klicken Sie unter "Testen" und "Verteilen" auf *die Schaltfläche "Installieren".* 

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

Wählen Sie **im Abschnitt "Zu** einem Team hinzufügen" das Suchfeld **aus,** und wählen Sie ein Team aus, dem die Beispiel-App hinzugefügt werden soll. In der Regel können Sie ein spezielles Team für Tests einrichten.

Klicken Sie **unten** im Dialogfeld auf die Schaltfläche "Installieren".

Damit wird der App Studio-Teil dieser exemplarischen Vorgehensweise abgeschlossen. Nun sollte Ihre App in Teams ausgeführt werden, der Bot und die Messagingerweiterung funktionieren jedoch erst, wenn Sie die Umgebung für gehostete Anwendungen aktualisieren, um zu erfahren, was die App-IDs und Kennwörter sind.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
