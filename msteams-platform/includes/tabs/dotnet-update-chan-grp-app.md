### <a name="_layoutcshtml"></a>_Layout.cshtml

Damit Die Registerkarte in Teams angezeigt werden kann, müssen Sie das **Microsoft Teams JavaScript-Client-SDK** und einen Aufruf nach `microsoftTeams.initialize()` dem Laden der Seite einschließen. So kommunizieren Ihre Registerkarte und der Teams-Client:

Wechseln Sie zum Ordner **"Freigegeben",** öffnen **Sie _Layout.cshtml,** und fügen Sie dem Tag Folgendes `<head>` hinzu:

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

>[!IMPORTANT]
> Kopieren Sie die URLs von dieser Seite nicht, und fügen Sie `<script src="...">` sie nicht ein, da sie möglicherweise nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API.](https://www.npmjs.com/package/@microsoft/teams-js)

### <a name="tabcshtml"></a>Tab.cshtml

**So aktualisieren Sie das eingebettete Skript**

1. Öffnen Sie in Visual Studio **Tab.cshtml,** um die eingebettete zu `<script>` aktualisieren.

1. Rufen Sie oben im Skript `microsoftTeams.initialize()` .

1. Aktualisieren Sie die `websiteUrl` Werte in jeder Funktion mit der `contentUrl` HTTPS-ngrok-URL auf Ihre Registerkarte.

    Ihr Code sollte nun wie folgt aussehen, wobei **y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:

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

1. Stellen Sie sicher, dass Sie das aktualisierte **Tab.cshtml**-Objekt speichern.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

Drücken Sie in Visual Studio **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus. Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.

> [!TIP]
> Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu **arbeiten, führen Sie ngrok aus.** Sie lauscht weiterhin und setzt das Weiterleiten der Anforderung Ihrer Anwendung fort, wenn sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

## <a name="upload-your-tab"></a>Hochladen Der Registerkarte

>[!Note]
> App Studio kann verwendet werden, um Ihre **manifest.jszu** bearbeiten und das fertige Paket in Teams hochzuladen. Sie können die **manifest.js** für die Datei auch manuell bearbeiten, wenn Sie möchten. Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die hochzuladende **tab.zipdatei** zu erstellen.

**So laden Sie Ihre Registerkarte hoch**

1. Wechseln Sie zu Microsoft Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.

1. Wechseln Sie zu **App Studio,** und wählen Sie die Registerkarte **"Manifest-Editor"** aus.

1. Wählen Sie im Manifest-Editor eine **vorhandene App importieren** aus, um mit dem Aktualisieren des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest. Der Name Ihres App-Pakets ist **tab.zip.** Sie ist hier verfügbar:

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. Hochladen app Studio **tab.zip.**

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren des App-Pakets mit dem Manifest-Editor

Nachdem Sie Das App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abschließen.

Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Auf der linken Seite des Manifest-Editors finden Sie eine Liste der Schritte und auf der rechten Seite eine Liste der Eigenschaften, die werte für jeden dieser Schritte aufweisen müssen. Ein Großteil der Informationen wurde von Ihrem **manifest.js** bereitgestellt, es gibt jedoch einige Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

Im Abschnitt **"App-Details":**

1. Wählen Sie unter **"Identifikation"** die Option **"Generieren"** aus, um die Platzhalter-ID durch die erforderliche GUID für Ihre Registerkarte zu ersetzen.

1. Aktualisieren Sie unter **"Entwicklerinformationen"** **die Website** mit Ihrer **ngrok** HTTPS-URL.

1. Aktualisieren Sie unter **App-URLs** die **Datenschutzerklärung** `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt **"Registerkarten":**

1. Wählen Sie **auf der Registerkarte "Team"** die Option **"Hinzufügen"** aus.

1. Aktualisieren Sie im Popupfenster der **Registerkarte "Team"** die **Konfigurations-URL** auf `https://<yourngrokurl>/tab` .

1. Stellen Sie sicher, dass die **Kontrollkästchen "Konfiguration aktualisieren können",** **"Team"** und **"Gruppenchat"** aktiviert sind, und wählen Sie **"Speichern"** aus.

#### <a name="finish-domains-and-permissions"></a>Fertig stellen: Domänen und Berechtigungen

Im Abschnitt **"Domänen und Berechtigungen"** müssen **Domänen von Ihren Registerkarten** Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io/` enthalten.

#### <a name="finish-test-and-distribute"></a>Fertig stellen: Testen und Verteilen

>[!IMPORTANT]
> Auf der rechten Seite wird in der **Beschreibung** die folgende Warnung angezeigt:
>
> &#9888; "**Das Array "validDomains" darf keine Tunnelwebsite enthalten...**"
>
> Diese Warnung kann beim Testen der Registerkarte ignoriert werden.

1. Wählen Sie im Abschnitt **"Testen und Verteilen"** die Option **"Installieren"** aus.

1. Wählen Sie im Popupdialogfeld **"Zu einem Team hinzufügen"** oder aus der Dropdownliste die Option **"Zu einem Chat hinzufügen"** aus.

1. Wählen Sie das Team oder den Chat aus, in dem die Registerkarte angezeigt werden soll, und wählen Sie **"Registerkarte einrichten"** aus.

1. Wählen Sie im nächsten Popupdialogfeld entweder **"Grau"** oder **"Rot"** aus, und wählen Sie **"Speichern"** aus.

1. Um Ihre Registerkarte anzuzeigen, wechseln Sie zu dem Team, in dem Sie die Registerkarte installiert haben, und wählen Sie sie in der Registerkartenleiste aus. Die Seite, die Sie während der Konfiguration ausgewählt haben, wird angezeigt.

    ![Kanalregisterkarte ASPNETMVC hochgeladen](../../assets/images/tab-images/channeltabaspnetmvcuploaded.png)

