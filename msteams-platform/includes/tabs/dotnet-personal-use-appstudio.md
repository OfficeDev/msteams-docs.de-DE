## <a name="upload-your-tab-to-teams-with-app-studio"></a>Hochladen Ihrer Registerkarte, um Teams App Studio zu verwenden

>[!NOTE]
> Wir verwenden App Studio, um Ihre **manifest.jsdatei zu** bearbeiten und das fertige Paket in das Teams. Sie können die Einstellungen auch **manuellmanifest.jsbearbeiten,** wenn Sie dies bevorzugen. Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **Tab.zip** hochzuladen.

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)

- Öffnen Sie App studio, und wählen Sie die **Registerkarte Manifest-Editor** aus.

- Wählen Sie **die Kachel Vorhandene App importieren** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode verfügt über ein eigenes teilweise vollständiges Manifest. Der Name Ihres App-Pakets **isttab.zip.** Sie sollte hier gefunden werden:

```bash
/bin/Debug/netcoreapp2.2/Tab.zip
```

- Hochladen **Tab.zip** App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren Des App-Pakets mit dem Manifest-Editor

Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abgeschlossen haben.

- Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die Werte für jeden dieser Schritte aufweisen müssen. Viele der Informationen wurden von Ihremmanifest.js *bereitgestellt,* aber es gibt einige Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

Im Abschnitt *App-Details:*

- Wählen *Sie unter Identifikation* die Option **Generieren** aus, um eine neue App-ID für Ihre App zu generieren.

- Aktualisieren *Sie unter* Entwicklerinformationen die **Website-URL** mit Ihrer *ngrok-HTTPS-URL.*

- Aktualisieren *Sie unter App-URLs* **die Datenschutzerklärung** auf `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt *Registerkarten:*

- Wählen *Sie unter Persönliche Registerkarte hinzufügen* die Option Hinzufügen ***aus.*** Ihnen wird ein Popupdialogfenster angezeigt.

- Füllen Sie das *Feld Name* aus.

- Füllen Sie das *Feld Entitäts-ID* aus.

- Aktualisieren Sie *das Feld Inhalts-URL* mit auf `https://<yourngrokurl>/personalTab` .

- Lassen Sie *das Feld Website-URL* leer.

- Wählen Sie ***Speichern*** aus.

#### <a name="finish-domains-and-permissions"></a>Finish: Domänen und Berechtigungen

Im Abschnitt *Domänen und Berechtigungen* sollte das Feld Domänen aus Ihrem *Registerkartenfeld* Ihre ngrok-URL ohne das HTTPS-Präfix - `<yourngrokurl>.ngrok.io/` enthalten.

##### <a name="finish-test-and-distribute"></a>Finish: Testen und Verteilen

>[!IMPORTANT]
>Im **Feld Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:
>
>&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"
>
>Diese Warnung kann beim Testen ihrer Registerkarte ignoriert werden.

Im Abschnitt *Test and distribute:*

- Wählen Sie **Installieren** aus.

- Stellen Sie im Popupfenster sicher, dass *Hinzufügen* für Sie auf *Ja* und *Hinzufügen* zu einem Team oder Chat auf Nein *festgelegt ist.*

- Wählen Sie **Installieren** aus.

- Wählen Sie im nächsten Popupfenster **Öffnen** aus, und Ihre Registerkarte wird angezeigt.

## <a name="view-your-personal-tab"></a>Anzeigen Ihrer persönlichen Registerkarte

- Wählen Sie in der Navigationsleiste ganz links neben der Teams das `...` Menü aus. Ihnen wird eine Liste der persönlichen Apps angezeigt.

- Wählen Sie ihre Registerkarte aus der Liste aus, die angezeigt werden soll.
