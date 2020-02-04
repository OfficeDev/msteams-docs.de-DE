## <a name="upload-your-tab-to-teams-with-app-studio"></a>Hochladen der Registerkarte in Microsoft Teams mit App Studio

>[!NOTE]
> Wir verwenden App Studio, um Ihre **Manifest. JSON** -Datei zu bearbeiten und das abgeschlossene Paket in Microsoft Teams hochzuladen. Sie können **Manifest. JSON** auch manuell bearbeiten, wenn Sie dies bevorzugen. Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die Datei **"Tab. zip"** zu erstellen, die hochgeladen werden soll.

- Öffnen Sie den Microsoft Teams-Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.

- Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.

- Wählen Sie die Kachel **Importieren einer vorhandenen APP** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest. Der Name Ihres App-Pakets lautet **Tab. zip**. Es sollte hier gefunden werden:

```bash
/bin/Debug/netcoreapp2.2/Tab.zip
```

- Upload **Tab. zip** in App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren des App-Pakets mit dem Manifest-Editor

Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration fertig stellen.

- Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Auf der linken Seite des Manifest-Editors finden Sie eine Liste mit Schritten und auf der rechten Seite eine Liste mit Eigenschaften, die für jeden dieser Schritte Werte enthalten müssen. Ein Großteil der Informationen wurde von Ihrem *Manifest. JSON* bereitgestellt, aber es gibt ein paar Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

Im Abschnitt *App-Details* :

- Wählen Sie unter *Identifikation* **generieren** aus, um eine neue APP-ID für Ihre APP zu generieren.

- Aktualisieren Sie unter *Entwickler Informationen* die **Website-URL** mit Ihrer *ngrok* -HTTPS-URL.

- Aktualisieren Sie unter *App* `https://<yourngrokurl>/privacy` -URLs die **Datenschutzbestimmungen** und **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt *Tabs* :

- Wählen Sie unter *persönliche Registerkarte hinzufügen die* Option ***Hinzufügen***aus. Ihnen wird ein Popup-Dialogfenster angezeigt.

- Füllen Sie das Feld *Name* aus.

- Schließen Sie das Feld *Entitäts-ID* ab.

- Aktualisieren Sie das Feld *Inhalts* -URL `https://<yourngrokurl>/personalTab`mit auf.

- Lassen Sie das Feld *Website-URL* leer.

- Klicken Sie auf ***Speichern***.

#### <a name="finish-domains-and-permissions"></a>Fertig stellen: Domänen und Berechtigungen

Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld Ihre ngrok- `<yourngrokurl>.ngrok.io/`URL ohne das Präfix "https" enthalten.

##### <a name="finish-test-and-distribute"></a>Fertig stellen: Testen und verteilen

>[!IMPORTANT]
>Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:
>
>&#9888; "**das Array" validDomains "kann keine Tunneling-Website enthalten...**"
>
>Diese Warnung kann beim Testen der Registerkarte ignoriert werden.

Im Abschnitt *Testen und verteilen* :

- **Installieren** auswählen.

- Stellen Sie im Popupfenster sicher, dass *Add for you* auf *Ja* festgelegt ist und *zu einem Team oder Chat hinzufügen* auf *Nein*festgelegt ist.

- **Installieren** auswählen.

- Wählen Sie im nächsten Popupfenster die Option **Öffnen** aus, und ihre Registerkarte wird angezeigt.

## <a name="view-your-personal-tab"></a>Anzeigen Ihrer persönlichen Registerkarte

- Wählen Sie in der Navigationsleiste, die sich in der Microsoft Teams-App ganz links `...` befindet, das Menü aus. Ihnen wird eine Liste mit persönlichen apps angezeigt.

- Wählen Sie die Registerkarte aus der Liste aus, die angezeigt werden soll.
