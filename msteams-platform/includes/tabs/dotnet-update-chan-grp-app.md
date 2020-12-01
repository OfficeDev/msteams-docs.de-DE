### <a name="_layoutcshtml"></a>_Layout. cshtml

Damit Ihre Registerkarte in Teams angezeigt wird, müssen Sie das **Microsoft Teams-JavaScript-Client-SDK** einschließen und nach dem Laden einer Seite einen Anruf hinzufügen `microsoftTeams.initialize()` . So kommunizieren Ihr Tab und der Microsoft Teams-Client:

- Navigieren Sie zum **freigegebenen** Ordner, öffnen Sie **_Layout. cshtml**, und fügen Sie dem-Tag Folgendes hinzu `<head>` :

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

>[!IMPORTANT]
>Kopieren/fügen Sie die `<script src="...">` URLs nicht von dieser Seite ein, da Sie möglicherweise nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu: [Microsoft Teams-JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).

### <a name="tabcshtml"></a>Tab. cshtml

Öffnen Sie **Tab. cshtml** , und aktualisieren Sie die Embedded `<script>` wie folgt:

- Rufen Sie am oberen Rand des Skripts auf `microsoftTeams.initialize()` .

- Aktualisieren `websiteUrl` Sie die-und- `contentUrl` Werte in jeder Funktion mit der HTTPS-ngrok-URL zu ihrer Registerkarte.

Ihr Code sollte jetzt wie folgt aussehen, wenn **y8rCgT2b** durch ihre ngrok-URL ersetzt wird:

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

Stellen Sie sicher, dass die aktualisierte **Registerkarte. cshtml** gespeichert ist.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

- Drücken Sie in Visual Studio **F5**, oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus. Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und zu ihrer Inhaltsseite über die ngrok-HTTPS-URL wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.

>[!TIP]
>Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diesen Schnellstart abzuschließen. Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um damit zu arbeiten, **halten Sie ngrok** auf dem laufenden. Sie wird weiterhin überwacht und setzt die Weiterleitung der Anforderung Ihrer Anwendung fort, wenn Sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

## <a name="upload-your-tab-to-teams-with-app-studio"></a>Hochladen der Registerkarte in Microsoft Teams mit App Studio

>[!Note]
> Wir verwenden App Studio, um Ihre **manifest.jsauf** Datei zu bearbeiten und das abgeschlossene Paket in Microsoft Teams hochzuladen. Sie können diemanifest.jsauch manuell **in** der Datei bearbeiten, wenn Sie dies bevorzugen. Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die **tab.zip** Datei zu erstellen, die hochgeladen werden soll.

- Öffnen Sie den Microsoft Teams-Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.

- Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.

- Wählen Sie die Kachel **Importieren einer vorhandenen APP** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest. Der Name des App-Pakets lautet **tab.zip**. Es sollte hier gefunden werden:

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- Laden Sie **tab.zip** in das App-Studio hoch.

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren des App-Pakets mit dem Manifest-Editor

Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration fertig stellen.

- Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Auf der linken Seite des Manifest-Editors finden Sie eine Liste mit Schritten und auf der rechten Seite eine Liste mit Eigenschaften, die für jeden dieser Schritte Werte enthalten müssen. Viele der Informationen wurden von Ihrem *manifest.js* bereitgestellt, aber es gibt ein paar Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

- Wählen Sie unter *Identifikation* ***generieren** _ aus, um die Platzhalter-ID durch die erforderliche GUID für die Registerkarte zu ersetzen.

- Aktualisieren Sie unter _Developer Informationen das Feld **Website-URL** mit Ihrer *ngrok* -HTTPS-URL.

- Aktualisieren Sie unter *App-URLs* die **Datenschutzbestimmungen** und **Nutzungsbedingungen für** URL-Felder mit Ihrer *ngrok* -HTTPS-URL. Denken Sie daran, die */Privacy* -und */tou* -Pfade am Ende der URLs einzubeziehen.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt *Tabs* :

- Wählen Sie unter *Team Tab* die Option **Hinzufügen** aus.

- Aktualisieren Sie im Popupfenster der Registerkarte "Team" die *Konfigurations-URL* auf `https://<yourngrokurl>/tab` .

- Stellen Sie schließlich sicher, dass die *Konfiguration aktualisiert werden kann? Team*-und *Gruppenchat* Felder werden überprüft, und wählen Sie **Speichern** aus.

#### <a name="finish-domains-and-permissions"></a>Fertig stellen: Domänen und Berechtigungen

Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld Ihre ngrok-URL ohne das Präfix "https" enthalten `<yourngrokurl>.ngrok.io/` .

#### <a name="test-and-distribute-test-and-distribute"></a>Testen und verteilen: Testen und verteilen

>[!IMPORTANT]
>Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:
>
>&#9888; "**das Array" validDomains "kann keine Tunneling-Website enthalten...**"
>
>Diese Warnung kann beim Testen der Registerkarte ignoriert werden.

Im Abschnitt *Testen und verteilen* :

- Wählen Sie **Installieren** aus.

- Geben Sie in das Popupfenster *Hinzufügen zu einem Team oder Chat* Feld Ihr Team ein, und wählen Sie **Installieren** aus.

- Wählen Sie im nächsten Popupfenster den Team Kanal aus, in dem die Registerkarte angezeigt werden soll, und wählen Sie **Einrichten** aus.

- Wählen Sie im letzten Popupfenster einen Wert für die Registerkartenseite aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern** aus.

Navigieren Sie zum Anzeigen der Registerkarte zu dem Team, auf dem Sie es installiert haben, und wählen Sie es in der Registerkartenleiste aus. Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.
