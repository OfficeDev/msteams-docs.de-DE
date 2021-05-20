## <a name="upload-your-tab-to-teams-with-app-studio"></a>Hochladen Sie Ihren Tab, um mit App Studio zu Teams

>[!NOTE]
> Wir verwenden App Studio, um Ihre **manifest.jsin** der Datei zu bearbeiten und das fertige Paket in Teams hochzuladen. Sie können **manifest.js** auch manuell bearbeiten, wenn Sie dies vorziehen. Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **Tab.zip** Datei zu erstellen, die hochgeladen werden soll.

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mit den [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.

- Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.

- Wählen Sie im Manifest-Editor die Kachel **"Importieren einer vorhandenen App"** aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes, teilweise vollständiges Manifest. Der Name Ihres App-Pakets lautet **tab.zip**. Sie sollte hier zu finden sein:

    ```bash
    /bin/Debug/netcoreapp2.2/Tab.zip
    ```

- Hochladen **Tab.zip** zu App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren Ihres App-Pakets mit dem Manifest-Editor

Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abschließen.

- Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Manifest-Editor-Willkommensseite aus.

Es gibt eine Liste von Schritten auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste von Eigenschaften, die Werte für jeden dieser Schritte haben müssen. Viele der Informationen wurden von Ihrem *manifest.jsbereitgestellt,* aber es gibt ein paar Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

Im Abschnitt **App-Details:**

- Wählen Sie unter **Kennung** **generieren** aus, um eine neue App-ID für Ihre App zu generieren.

- Aktualisieren Sie unter **Entwicklerinformationen** die **Website-URL** mit Ihrer **ngrok** HTTPS-URL.

- Unter **App-URLs** wird die **Datenschutzerklärung** `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`> aktualisiert.

#### <a name="capabilities-tabs"></a>Funktionen: Tabs

Im Abschnitt *Tabs:*

- Wählen Sie unter **Persönliche Registerkarte Hinzufügen** aus.  Sie erhalten ein Pop-up-Dialogfenster.

- Füllen Sie das Feld **Name** aus.

- Füllen Sie das Feld **Entitäts-ID** aus.

- Aktualisieren Sie das Feld **Inhalts-URL** mit `https://<yourngrokurl>/personalTab` .

- Lassen Sie das **Feld Website-URL** leer.

- Klicken Sie auf **Speichern**.

#### <a name="finish-domains-and-permissions"></a>Beenden: Domänen und Berechtigungen

Im Abschnitt **Domänen und Berechtigungen** sollte das Feld Domänen aus Ihrem **TabsFeld** Ihre ngrok-URL ohne das HTTPS-Präfix - `<yourngrokurl>.ngrok.io/` enthalten.

##### <a name="finish-test-and-distribute"></a>Finish: Testen und verteilen

>[!IMPORTANT]
>Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:
>
>&#9888; "**Das Array 'validDomains' darf keine Tunneling-Site enthalten...**"
>
>Diese Warnung kann beim Testen der Registerkarte ignoriert werden.

Im Abschnitt **Testen und Verteilen:**

- Wählen Sie **Installieren** aus.

- Stellen Sie im Popupfenster sicher, dass **Add for you** auf **Ja** und Hinzufügen zu einem Team **oder Chat** auf **Nein** gesetzt ist.

- Wählen Sie **Installieren** aus.

- Wählen Sie im nächsten Popup-Fenster **Öffnen** aus, und Ihre Registerkarte wird angezeigt.

## <a name="view-your-personal-tab"></a>Anzeigen Ihrer persönlichen Registerkarte

- Wählen Sie in der Navigationsleiste ganz links der Teams App das `...` Menü aus. Ihnen wird eine Liste persönlicher Apps angezeigt.

- Wählen Sie Ihre Registerkarte aus der anzuzeigenden Liste aus.
