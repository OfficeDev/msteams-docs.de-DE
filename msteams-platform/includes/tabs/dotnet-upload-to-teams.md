## <a name="upload-your-tab-to-teams-with-app-studio"></a>Hochladen der Registerkarte in Microsoft Teams mit App Studio

>[!NOTE]
> Wir verwenden App Studio, um Ihre **Manifest. JSON** -Datei zu bearbeiten und das abgeschlossene Paket in Microsoft Teams hochzuladen. Sie können die Datei " **Manifest. JSON** " auch manuell bearbeiten, wenn Sie dies bevorzugen. Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die Datei **"Tab. zip"** zu erstellen, die hochgeladen werden soll.

- Öffnen Sie den Microsoft Teams-Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.

- Öffnen Sie die APP Studio-app, und wählen Sie die Registerkarte **Manifest-Editor** aus.

- Wählen Sie die Kachel **Importieren einer vorhandenen APP** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest. Der Name Ihres App-Pakets lautet **Tab. zip**. Es sollte hier gefunden werden:

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- Upload **Tab. zip** in App Studio.

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren des App-Pakets mit dem Manifest-Editor

Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration fertig stellen.

- Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Auf der linken Seite des Manifest-Editors finden Sie eine Liste mit Schritten und auf der rechten Seite eine Liste mit Eigenschaften, die für jeden dieser Schritte Werte enthalten müssen. Ein Großteil der Informationen wurde von Ihrem *Manifest. JSON* bereitgestellt, aber es gibt ein paar Felder, die Sie aktualisieren müssen:

#### <a name="details-app-details"></a>Details: App-Details

- Wählen Sie unter *Identifikation* **generieren** aus, um eine neue APP-ID für Ihre APP zu generieren.

- Aktualisieren Sie unter *Entwickler Informationen* das Feld **Website-URL** mit Ihrer *ngrok* -HTTPS-URL.

- Aktualisieren Sie unter *App* `https://<yourngrokurl>/privacy` -URLs die **Datenschutzbestimmungen** und **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt *Tabs* :

- Wählen Sie unter *Team Tab* die Option **Hinzufügen**aus.

- Aktualisieren Sie im Popupfenster der Registerkarte "Team" die Konfigurations `https://<yourngrokurl>/tab`- *URL* auf.

- Stellen Sie schließlich sicher, dass die *Konfiguration aktualisiert werden kann? Team*-und *Gruppenchat* Felder werden überprüft, und wählen Sie **Speichern**aus.

#### <a name="finish-domains-and-permissions"></a>Fertig stellen: Domänen und Berechtigungen

Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld Ihre ngrok- `<yourngrokurl>.ngrok.io/`URL ohne das Präfix "https" enthalten.

#### <a name="finish-test-and-distribute"></a>Fertig stellen: Testen und verteilen

>[!IMPORTANT]
>Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:
>
>&#9888; "**das Array" validDomains "kann keine Tunneling-Website enthalten...**"
>
>Diese Warnung kann beim Testen der Registerkarte ignoriert werden.

Im Abschnitt *Testen und verteilen* :

- **Installieren** auswählen.

- Geben Sie in das Popupfenster *Hinzufügen zu einem Team oder Chat* Feld Ihr Team ein, und wählen Sie **Installieren**aus.

- Wählen Sie im nächsten Popupfenster den Team Kanal aus, in dem die Registerkarte angezeigt werden soll, und wählen Sie **Einrichten**aus.

- Wählen Sie im letzten Popupfenster einen Wert für die Registerkartenseite aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern**aus.

Navigieren Sie zum Anzeigen der Registerkarte zu dem Team, auf dem Sie es installiert haben, und wählen Sie es in der Registerkartenleiste aus. Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.
