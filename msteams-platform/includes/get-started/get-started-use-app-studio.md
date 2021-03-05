### <a name="use-app-studio-to-update-the-app-package"></a>Aktualisieren des App-Pakets mithilfe von App Studio

App Studio ist eine Teams-App, die Sie im Teams Store installieren können. Es vereinfacht die Erstellung und Registrierung einer App.

Führen Sie die folgenden Schritte aus, um das App-Paket zu aktualisieren:

1. Um App Studio in Teams zu installieren, wählen Sie das **Symbol Apps** unten auf der linken Leiste aus, und suchen Sie nach **App Studio**.

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

2. Wählen Sie die **Kachel App Studio** aus, und wählen Sie Installieren **aus.** Das App Studio ist installiert.

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

3. Wählen Sie zum Erstellen des App-Pakets für Ihre Teams-App die Registerkarte **Manifest-Editor** in **App Studio aus.**

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

Das Beispiel enthält ein eigenes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird. In .NET erfolgt dies in Visual Studio und Node.js erfolgt dies durch Eingabe an der Befehlszeile `gulp` im Stammverzeichnis des Projekts.

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

Der Name des generierten App-Pakets **isthelloworldapp.zip.** Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.

4. Wählen Sie zum Ändern dieses App-Pakets **im Manifest-Editor** die Option Vorhandene **App importieren aus.**

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

5. Wählen Sie die **Kachel Hello World** für Ihre neu importierte App aus.

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

Die folgende Abbildung zeigt das importierte App-Paket in App Studio:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Auf der linken Seite des Manifest-Editors befindet sich eine Liste der Schritte. Auf der rechten Seite befindet sich eine Liste der Eigenschaften, die für jeden Schritt ausgefüllt werden müssen. Wie Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits abgeschlossen. Mit den nächsten Schritten können Sie die Eigenschaften der Hello World-App aktualisieren.

#### <a name="app-details"></a>App-Details

Wählen **Sie App-Details** unter **Details aus.** Wählen Sie die **Schaltfläche Generieren** aus, um eine neue App-ID zu erstellen.

Ihre neue App-ID ähnelt `2322041b-72bf-459d-b107-f4f335bc35bd` .

Gehen Sie im rechten Bereich durch die App-Details, einschließlich **Entwicklerinformationen** und **Brandingdetails.** Diese Details sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.

#### <a name="tabs"></a>Registerkarten

Es ist einfach, einer Teams-App Registerkarten hinzuzufügen. Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können sie aktivieren.

##### <a name="team-tab"></a>Registerkarte "Team"

Ihre App kann nur über eine Teamregisterkarte verfügen.

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In diesem Beispiel wird auf der Registerkarte Team die Konfigurationsseite angezeigt. Wählen Sie **das Symbol ...** der **Tab-Konfigurations-URL aus,** und wählen Sie **im** Dropdownmenü Bearbeiten aus. Ändern Sie die URL so, dass sie durch die URL ersetzt werden muss, die Sie `https://yourteamsapp.ngrok.io/configure` `yourteamsapp.ngrok.io` beim [Hosten Ihrer App verwendet haben.](#host-the-sample-app)

##### <a name="personal-tabs"></a>Persönliche Registerkarten

Ihre App kann über bis zu 16 Registerkarten verfügen, einschließlich der Registerkarte Team.

Persönliche Registerkarten unterscheiden sich von der Registerkarte Team. **Hello Tab** ist bereits in der Liste der persönlichen Registerkarten mit einem Platzhalterwert `com.contoso.helloworld.hellotab` aufgeführt. Wählen Sie **das Symbol ...** der **Tab-Konfigurations-URL aus,** und wählen Sie **im** Dropdownmenü Bearbeiten aus. Das folgende Dialogfeld wird angezeigt:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Aktualisieren Sie die folgenden Felder mit Ihrer App-URL:

- Ändern des **Felds Inhalts-URL** in `https://yourteamsapp.ngrok.io/hello`
- Ändern des **Felds Website-URL** in `https://yourteamsapp.ngrok.io/hello`

Ersetzen `yourteamsapp.ngrok.io` Sie durch die URL, die Sie beim Hosten Ihrer App verwendet haben.

#### <a name="bots"></a>Bots

Es ist einfach, die Bots-Funktionalität zu Ihrer App hinzuzufügen. Die Hello World-Beispiel-App verfügt bereits über einen Bot als Teil des Beispiels, Sie müssen ihn jedoch bei Microsoft registrieren. 

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

Der bot, der aus dem Beispiel importiert wurde, verfügt nicht über eine zugeordnete App-ID. Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.

> [!NOTE]
> Die von App Studio für den Bot erstellte App-ID ist anders als die app-ID, die für die App erstellt wurde. Jeder Bot in einer App benötigt eine eigene App-ID.

Führen Sie die folgenden Schritte aus, um Ihren Bot zu installieren:

1. Wählen **Sie neben** dem importierten Bot in der Botliste löschen aus. Jetzt sind keine Bots mehr zu sehen. 
2. Wählen **Sie Setup** aus, um das Dialogfeld Bot **einrichten** anzuzeigen.

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

3. Fügen Sie einen Botnamen **Contoso-Bot hinzu,** und aktivieren Sie alle drei Kontrollkästchen unter **Bereich**.
4. Wählen **Sie Speichern** aus, um das Dialogfeld zu beenden. App Studio registriert Ihren Bot bei Microsoft und zeigt Den neuen Bot in der Botliste an. 
5. Öffnen Sie nun eine Textdatei im Editor, und kopieren Und fügen Sie Ihre neue Bot-ID ein.
6. Klicken **Sie auf Neues Kennwort generieren,** und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre Bot-App-ID notiert haben.
7. Aktualisieren Sie die **Bot-Endpunktadresse** auf , und ersetzen Sie durch die URL, die Sie beim `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` Hosten Ihrer App verwendet haben.
8. Speichern Sie nun Ihre Textdatei, da Sie die Informationen aus der Datei zu Ihrer gehosteten App hinzufügen müssen, um eine sichere Kommunikation mit Ihrem Bot zu ermöglichen.

#### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Mit Messagingerweiterungen können Benutzer nach Informationen von Ihrem Dienst fragen und diese Informationen veröffentlichen. Die Informationen werden in Form von Karten in der Kanal unterhaltung bereitgestellt. Messagingerweiterungen werden am unteren Rand des Verfassenfelds angezeigt.

Führen Sie die folgenden Schritte aus, um Ihre Messagingerweiterung zu installieren:

1. Wählen **Sie Messagingerweiterungen** **unter Funktionen** im linken Bereich von App Studio aus, um die Messagingerweiterung zu konfigurieren.

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

Die Beispiel-Messagingerweiterung ist im Bereich **Messagingerweiterungen** aufgeführt.

2. Wählen **Sie Löschen** aus, um die Messagingerweiterung zu entfernen, wählen Sie **Einrichten** aus, und führen Sie die gleichen Schritte aus, die für [Bots verwendet werden.](#bots) Das **Dialogfeld Messagingerweiterung** wird angezeigt.
3. Wählen Sie die **Registerkarte Vorhandenen Bot verwenden** aus, und wählen Sie aus einem meiner **vorhandenen Bots aus.**
4. Wählen Sie den von Ihnen erstellten Bot im Dropdownmenü aus. Fügen Sie einen **Botnamen hinzu,** und wählen **Sie Speichern aus,** um das Dialogfeld zu schließen.
5. Wählen Sie **im Abschnitt Befehl** die Option Hinzufügen **aus.** Wenn Sie einen suchbasierten Befehl hinzufügen möchten, wählen Sie die Option Benutzern erlauben, Ihren Dienst nach Informationen zu fragen, und fügen Sie diesen **in eine Nachricht** ein.
6. Geben Sie im Dialogfeld **Neuer Befehl** die folgenden Werte ein:

Unter **Neuer Befehl**:

- **Befehls-ID**: Geben Sie zufälligen Text ein.
- **Titel**: Geben Sie zufälligen Titel ein.
- **Beschreibung**: Geben Sie eine zufällige Beschreibung ein.

Unter **Parameter**:

- **Name**: Geben Sie den Parameternamen ein.
- **Titel**: Geben Sie den Kartentitel ein.
- **Beschreibung**: Geben Sie die Kartenbeschreibung ein.

7. Nachdem Sie die Informationen eingeben, wählen **Sie Speichern** aus, um das Dialogfeld zu schließen.

#### <a name="register-your-app-in-teams"></a>Registrieren Ihrer App in Teams

Führen Sie nach der Eingabe der Details Ihrer App die folgenden Schritte aus, um Ihre App in Teams zu registrieren:

1. Verwenden **Sie Testen und Verteilen von** App Studio, um Ihre App in Teams zu installieren. 
2. Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot. Verwenden Sie für die Beispiel-App die gleiche App-ID und dasselbe Kennwort für Bot- und Messagingerweiterung. 
3. Wählen **Sie Testen und Verteilen**  unter **Fertig** stellen im linken Bereich von App Studio aus.

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

4. Um Ihre App in Teams hochzuladen, wählen Sie unter **Testen** und Verteilen die Schaltfläche **Installieren aus.**

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

5. Wählen Sie **im Abschnitt** **Zu** einem Team hinzufügen das Feld Suchen aus, und wählen Sie ein Team aus, um die Beispiel-App hinzuzufügen. Sie können ein spezielles Team für Tests einrichten.
6. Wählen Sie **unten** im Dialogfeld die Schaltfläche Installieren aus.

Ihre App ist jetzt in Teams verfügbar. Der Bot und die Messagingerweiterung funktionieren jedoch erst, wenn Sie die gehostete Anwendungsumgebung mit den App-IDs und Kennwörtern aktualisieren.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
