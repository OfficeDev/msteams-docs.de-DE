### <a name="use-app-studio-to-update-the-app-package"></a>Aktualisieren des App-Pakets mithilfe von App Studio

App Studio ist eine Teams-APP, die Sie im Microsoft Teams Store installieren können. Es vereinfacht das Erstellen und Registrieren einer App.

Wenn Sie App Studio in Microsoft Teams installieren möchten, klicken Sie auf das App Store-Symbol unten in der linken Leiste, und suchen Sie nach App Studio.

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

Wenn Sie die Kachel für App Studio gefunden haben, klicken Sie darauf, und wählen Sie im Dialogfeld *Installieren* aus, das eingeblendet wird.

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

Sobald App Studio installiert ist, klicken Sie auf die Registerkarte Manifest-Editor, um mit der Erstellung des App-Pakets für Ihre Teams-APP zu beginnen.

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

Das Beispiel enthält ein eigenes vordefiniertes Manifest und wurde entwickelt, um ein App-Paket zu erstellen, wenn das Projekt erstellt wird. In .net erfolgt dies in Visual Studio und auf Node js erfolgt dies durch Eingabe `gulp` an der Befehlszeile im Stammverzeichnis des Projekts.

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

Der Name des generierten App-Pakets lautet *helloworldapp.zip*. Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.

Im nächsten Teil dieser exemplarischen Vorgehensweise ändern Sie dieses app-Paket, indem Sie die Kachel *Importieren einer vorhandenen APP* im Manifest-Editor auswählen.

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

Wenn das App-Paket importiert wurde, sollte App Studio wie folgt aussehen:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Klicken Sie auf die Kachel für Ihre neu importierte APP, *Hello World*.

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und rechts eine Liste von Eigenschaften, die für jeden dieser Schritte ausgefüllt werden müssen. Da Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits ausgefüllt. Die nächsten Schritte führen Sie durch die Änderung der Teile, die noch aktualisiert werden müssen.

#### <a name="app-details"></a>App-Details

Klicken Sie unter *Details*auf den Eintrag *App-Details* . Klicken Sie auf die Schaltfläche *generieren* , um eine neue APP-ID zu erstellen.

Die neue APP-ID sollte etwa wie folgt aussehen: `2322041b-72bf-459d-b107-f4f335bc35bd` .

Sehen Sie sich die restlichen App-Details im rechten Bereich an, und machen Sie sich mit einigen Einträgen wie *Entwickler Informationen* und *Branding*vertraut. Diese Abschnitte sind wichtig, wenn Sie eine neue APP für die Verteilung schreiben.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Registerkarten gehören zu den einfachsten Elementen, die einer Teams-app hinzugefügt werden. Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können Sie wie folgt aktivieren.

##### <a name="team-tab"></a>Registerkarte "Team"

Ihre APP kann nur eine Team Registerkarte haben.

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In diesem Beispiel wird auf der Registerkarte "Team" die Konfigurationsseite angezeigt. Klicken Sie am Ende des Eintrags auf das Symbol *...* , und wählen Sie im Dropdownmenü *Bearbeiten* aus. Ändern Sie die URL `https://yourteamsapp.ngrok.io/configure` dahin, wo `yourteamsapp.ngrok.io` Sie durch die URL ersetzt werden soll, die Sie beim Hosten Ihrer APP oben verwendet haben.

##### <a name="personal-tabs"></a>Persönliche Registerkarten

Ihre APP kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte Team.

Persönliche Registerkarten werden auf der Registerkarte Team unterschiedlich dargestellt. Die *Registerkarte "Hello"* sollte bereits in der Liste "persönliche Registerkarten" angezeigt werden. Im Moment verfügt er über einen Platzhalterwert `com.contoso.helloworld.hellotab` . Klicken Sie am Ende des Eintrags auf das Symbol *...* , und wählen Sie im Dropdownmenü *Bearbeiten* aus. Das folgende Dialogfeld wird angezeigt.

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Es gibt zwei Felder, die Sie mit ihrer App-URL aktualisieren müssen.

- Ändern der Inhalts-URL in `https://yourteamsapp.ngrok.io/hello`
- Website-URL ändern in `https://yourteamsapp.ngrok.io/hello`

Wo `yourteamsapp.ngrok.io` sollte durch die URL ersetzt werden, die Sie beim Hosten Ihrer APP oben verwendet haben.

#### <a name="bots"></a>Bots

Bots sind die gängigste Methode zum Hinzufügen von Funktionen zu Ihrer APP. Das Beispiel "Hello World" verfügt bereits über einen bot als Teil des Beispiels, wurde aber noch nicht bei Microsoft registriert.

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

Dem bot, der aus dem Beispiel importiert wurde, ist noch keine APP-ID zugeordnet. Sie müssen einen neuen bot erstellen, damit App Studio eine neue APP-ID erstellen und bei Microsoft registrieren kann. Beachten Sie, dass dies die APP-ID für den Bot ist, die sich von der APP-ID unterscheidet, die wir in einem früheren Schritt für die App erstellt haben. Jeder bot in einer APP benötigt eine eigene APP-ID.

Klicken Sie in der Liste bot neben dem *importierten bot* auf die Schaltfläche *Löschen* .

Jetzt sind keine Bots mehr verfügbar, die angezeigt werden sollen. Klicken Sie auf *Setup*. Dadurch wird das Dialogfeld " *bot einrichten* " angezeigt.

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

Fügen Sie einen bot-Namen wie ein `Contoso bot` , und wählen Sie alle drei Schaltflächen unter *Bereich*.

Wählen Sie *Create bot* aus, um das Dialogfeld zu schließen. App Studio wird einen Moment Zeit damit verbringen, ihren bot bei Microsoft zu registrieren, und sollte dann Ihren neuen bot in der bot-Liste anzeigen. Jetzt wäre ein guter Zeitpunkt, eine Textdatei im Editor zu öffnen und ihre neue bot-ID zu kopieren und in diese einzufügen. Sie benötigen die ID später.

Klicken Sie auf *Neues Kennwort generieren*, und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre bot-APP-ID notiert haben. Dies ist das einzige Mal, wenn Ihr Kennwort angezeigt wird, deshalb sollten Sie dies jetzt tun.

Aktualisieren Sie die *bot-Endpunktadresse* auf `https://yourteamsapp.ngrok.io/api/messages` , wobei `yourteamsapp.ngrok.io` die URL ersetzt werden soll, die Sie beim Hosten Ihrer APP oben verwendet haben.

Jetzt wäre ein guter Zeitpunkt, um Ihre Textdatei zu speichern, wenn Sie dies noch nicht getan haben. Sie werden diese Informationen später in dieser exemplarischen Vorgehensweise zu ihrer gehosteten app hinzufügen, um eine sichere Kommunikation mit Ihrem bot zu ermöglichen.

#### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Mithilfe von Messaging Erweiterungen können Benutzer nach Informationen von Ihrem Dienst Fragen und diese Informationen in Form von Karten direkt in die Kanal Unterhaltung Posten. Messaging Erweiterungen werden am unteren Rand des Felds verfassen angezeigt.

Klicken Sie unter *Funktionen* in der linken Spalte von App Studio auf *Messaging Erweiterungen* , um mit der Konfiguration der Messaging Erweiterung zu beginnen.

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

Die Beispiel-Messaging-Erweiterung wird im rechten Bereich unter *Messaging Extensions*aufgeführt. Klicken Sie erneut auf *Löschen* , um diesen Eintrag zu entfernen, und klicken Sie dann auf die Schaltfläche *Einrichten* , indem Sie die gleichen Schritte ausführen, die Sie für Bots befolgt haben. Dadurch wird das Dialogfeld *Messaging Erweiterung* angezeigt.

Wählen Sie die Registerkarte *vorhandenen bot verwenden* aus, und *Wählen Sie dann eines meiner vorhandenen Bots aus*. Wählen Sie im Dropdownmenü den bot aus, den Sie im obigen Abschnitt erstellt haben. Fügen Sie einen *bot-Namen* hinzu, und klicken Sie auf *Speichern* , um das Dialogfeld zu schließen.

Klicken Sie im Abschnitt *Command* auf *Hinzufügen*. Wir fügen einen suchbasierten Befehl hinzu, wählen Sie also die Option *Benutzer können Ihren Dienst Abfragen* ... aus.

Geben Sie im Dialogfeld *neuer Befehl* die folgenden Werte ein.

Unter *neuer Befehl*:

- *Befehls-ID*  = getRandomText
- *Title*       = Abrufen von zufälligen Texten zum Spaß
- *Description* = ruft einige zufällige Text und Bilder

Unter *Parameter*:

- *Name*        = cardTitle
- *Title*       = Kartentitel
- *Description* = zu verwendender Kartentitel

Nachdem Sie die Informationen eingegeben haben, klicken Sie auf *Speichern* , um das Dialogfeld zu schließen.

#### <a name="register-your-app-in-teams"></a>Registrieren Ihrer APP in Microsoft Teams

Sie haben nun die Eingabe der Details Ihrer APP abgeschlossen, jedoch bleiben zwei Schritte. Zunächst müssen Sie den Abschnitt Test and Distribute von App Studio verwenden, um Ihre APP in Microsoft Teams zu installieren, und zweitens müssen Sie die gehostete Anwendung mit der APP-ID und dem Kennwort für Ihren bot aktualisieren. Beachten Sie, dass im Beispiel die gleiche APP-ID und das gleiche Kennwort für die bot-und die Messaging-Erweiterung verwendet werden.

Klicken Sie in der linken Spalte von App Studio auf das Element *Testen und verteilen* unter *Fertig stellen* .

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

Um Ihre APP in Teams hochzuladen, klicken Sie unter *Test and Distribute*auf die Schaltfläche *Installieren* .

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

Klicken Sie im Abschnitt *zu einem Team hinzufügen* auf das *Suchfeld* , und wählen Sie ein Team aus, dem Sie die Beispiel-app hinzufügen möchten. Normalerweise möchten Sie ein spezielles Team für Tests einrichten.

Klicken Sie unten im Dialogfeld auf die Schaltfläche *Installieren* .

Dadurch wird der APP Studio-Teil dieser exemplarischen Vorgehensweise abgeschlossen. Ihre APP sollte jetzt in Microsoft Teams ausgeführt werden, die bot-und die Messaging-Erweiterung funktionieren jedoch erst, wenn Sie die Umgebung für gehostete Anwendungen so aktualisieren, dass Sie wissen, was die APP-IDs und Kennwörter sind.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
