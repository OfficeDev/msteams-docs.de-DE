### <a name="_layoutcshtml"></a>_Layout.cshtml

Damit Ihre Registerkarte in Teams angezeigt werden kann, müssen Sie das Microsoft Teams **JavaScript-Client-SDK** und einen Aufruf nach dem Laden der `microsoftTeams.initialize()` Seite hinzufügen. So kommunizieren Ihre Registerkarte und Teams Client:

- Navigieren Sie zum **Freigegebenen** Ordner, öffnen **Sie _Layout.cshtml**, und fügen Sie dem Tag Folgendes `<head>` hinzu:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

>[!IMPORTANT]
>Kopieren/einfügen Sie die URLs nicht von dieser Seite, da `<script src="...">` sie möglicherweise nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu: [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).

### <a name="tabcshtml"></a>Tab.cshtml

Öffnen **Sie Tab.cshtml,** und aktualisieren Sie den `<script>` eingebetteten wie folgt:

- Rufen Sie oben im Skript `microsoftTeams.initialize()` auf.

- Aktualisieren Sie `websiteUrl` die Werte und in jeder Funktion mit der HTTPS `contentUrl` ngrok-URL auf Ihrer Registerkarte.

Ihr Code sollte nun wie folgt aussehen, **wenn y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:

```javascript
    microsoftTeams.initialize();

    let saveGray = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                entityId: "grayIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }

    let saveRed = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                entityId: "redIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }
```

Stellen Sie sicher, dass Sie die aktualisierte **Tab.cshtml -Datei speichern.**

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

- Drücken Visual Studio **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus. Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.

>[!TIP]
>Sie müssen ihre Anwendung in Visual Studio und ngrok ausführen, um diesen Schnellstart ausführen zu können. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio, damit sie funktioniert, **halten Sie ngrok am Laufen.** Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in einem Visual Studio. Wenn Sie den ngrok-Dienst neu starten müssen, gibt er eine neue URL zurück, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

## <a name="upload-your-tab-to-teams"></a>Hochladen Registerkarte zum Teams

>[!Note]
> Wir verwenden App Studio, um Ihre **manifest.jsdatei zu** bearbeiten und das fertige Paket in das Teams. Sie können die Datei auch manuellmanifest.js **on-Datei** bearbeiten, wenn Sie es vorziehen. Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **tab.zip** hochzuladen.

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)

- Öffnen Sie App studio, und wählen Sie die **Registerkarte Manifest-Editor** aus.

- Wählen Sie **die Kachel Vorhandene App importieren** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode verfügt über ein eigenes teilweise vollständiges Manifest. Der Name Ihres App-Pakets **isttab.zip.** Sie sollte hier gefunden werden:

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

- Hochladen **tab.zip** App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren Des App-Pakets mit dem Manifest-Editor

Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abgeschlossen haben.

- Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die Werte für jeden dieser Schritte aufweisen müssen. Viele der Informationen wurden von Ihremmanifest.js *bereitgestellt,* aber es gibt einige Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

Im Abschnitt *App-Details:*

- *Identifikation:* Wählen Sie **Generieren** aus, um die Platzhalter-ID durch die erforderliche GUID für Ihre Registerkarte zu ersetzen.

- *Entwicklerinformationen:* Aktualisieren Sie das **Feld Website-URL** mit Ihrer *ngrok-HTTPS-URL.*

- *App-URLs*: Aktualisieren Sie **die Datenschutzbestimmungen** `https://<yourngrokurl>/privacy` auf und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt *Registerkarten:*

- *Registerkarte Team*: wählen Sie **Hinzufügen aus.**

- Aktualisieren Sie im Popupfenster team tab die *Konfigurations-URL auf* `https://<yourngrokurl>/tab` .

- Stellen Sie schließlich sicher, dass *die Konfiguration aktualisiert werden kann? Die Chatfelder Team* und *Gruppe* werden aktiviert, und wählen Sie **Speichern aus.**

#### <a name="finish-domains-and-permissions"></a>Finish: Domänen und Berechtigungen

Im Abschnitt *Domänen und Berechtigungen:*

- The *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/` .

#### <a name="finish-test-and-distribute"></a>Finish: Testen und Verteilen

>[!IMPORTANT]
>Im **Feld Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:
>
>&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"
>
>Diese Warnung kann beim Testen ihrer Registerkarte ignoriert werden.

Im Abschnitt *Test and distribute:*

- Wählen Sie **Installieren** aus.

- Geben Sie im Popupfenster Hinzufügen zu einem Team oder *Chatfeld* Ihr Team ein, und wählen Sie **Installieren aus.**

- Wählen Sie im nächsten Popupfenster den Teamkanal aus, in dem die Registerkarte angezeigt werden soll, und wählen **Sie Einrichten aus.**

- Wählen Sie im letzten Popupfenster einen Wert für die Registerkarte aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern aus.**

Navigieren Sie zum Anzeigen Ihrer Registerkarte zu dem Team, in dem Sie sie installiert haben, und wählen Sie sie in der Registerkartenleiste aus. Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.
