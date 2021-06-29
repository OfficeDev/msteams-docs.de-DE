## <a name="upload-your-tab-with-app-studio"></a>Hochladen Ihrer Registerkarte mit App Studio

>[!NOTE]
> Wir verwenden **App Studio,** um Ihre **manifest.jszu** bearbeiten und das fertige Paket in Teams hochzuladen. Sie können auch manuell **manifest.jsbearbeiten.** Stellen Sie in diesem Fall sicher, dass Sie die Lösung erneut erstellen, um die hochzuladende **Tab.zipdatei** zu erstellen.

**So laden Sie Ihre Registerkarte mit App Studio hoch**

1. Wechseln Sie zu Microsoft Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.

1. Wechseln Sie zu **App Studio,** und wählen Sie die Registerkarte **"Manifest-Editor"** aus.

1. Wählen Sie im **Manifest-Editor** eine **vorhandene App importieren** aus, um mit dem Aktualisieren des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest. Der Name Ihres App-Pakets ist **tab.zip.** Es ist über den folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

1. Hochladen zu **App Studio** **tab.zip.**

### <a name="update-your-app-package-with-manifest-editor"></a>Aktualisieren des App-Pakets mit dem Manifest-Editor

Nachdem Sie Das App-Paket in App Studio hochgeladen haben, müssen Sie es konfigurieren.

Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.

Auf der linken Seite des Manifest-Editors finden Sie eine Liste der Schritte und auf der rechten Seite eine Liste der Eigenschaften, die werte für jeden dieser Schritte aufweisen müssen. Ein Großteil der Informationen wurde von Ihrem **manifest.js** bereitgestellt, es gibt jedoch Felder, die Sie aktualisieren müssen.

#### <a name="details-app-details"></a>Details: App-Details

Im Abschnitt **"App-Details":**

1. Wählen Sie unter **"Identifikation"** die Option **"Generieren"** aus, um eine neue App-ID für Ihre App zu generieren.

1. Aktualisieren Sie unter **"Entwicklerinformationen"** die **Website** mit Ihrer **ngrok** HTTPS-URL.

1. Aktualisieren Sie unter **App-URLs** die **Datenschutzerklärung** `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`>.

#### <a name="capabilities-tabs"></a>Funktionen: Registerkarten

Im Abschnitt **"Registerkarten":**

1. Wählen Sie unter **"Persönliche Registerkarte hinzufügen"** die Option **"Hinzufügen"** aus. Ein Popupdialogfeld wird angezeigt.

1. Geben Sie einen Namen für die persönliche Registerkarte in **Name** ein.

1. Geben Sie die **Entitäts-ID** ein.

1. Aktualisieren Sie **die Inhalts-URL** mit `https://<yourngrokurl>/personalTab` .

    Lassen Sie das **Feld "Website-URL"** leer.

1. Klicken Sie auf **Speichern**.

#### <a name="finish-domains-and-permissions"></a>Fertig stellen: Domänen und Berechtigungen

Im Abschnitt **"Domänen und Berechtigungen"** muss das Feld **"Domänen" im Registerkartenfeld** Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io/` enthalten.

##### <a name="finish-test-and-distribute"></a>Fertig stellen: Testen und Verteilen

>[!IMPORTANT]
> Auf der rechten Seite wird in der **Beschreibung** die folgende Warnung angezeigt:
>
> &#9888; Das **Array "validDomains" darf keine Tunnelwebsite enthalten...**
>
>Diese Warnung kann beim Testen der Registerkarte ignoriert werden.

1. Wählen Sie im Abschnitt **"Testen und Verteilen"** die Option **"Installieren"** aus.

1. Wählen Sie im Dialogfeld Hinzufügen die Option Hinzufügen aus, und ihre Registerkarte wird mit zwei Optionen angezeigt. 

1. Wählen Sie in den Optionen auf der Registerkarte entweder **Grau** oder **Rot aus.** Die Registerkarte wird entsprechend der ausgewählten Farbe angezeigt.
 
    ![Persönliche Registerkarte ASPNETMVC hochgeladen](../../assets/images/tab-images/personaltabaspnetmvcuploaded.png)

## <a name="view-your-personal-tab"></a>Anzeigen Ihrer persönlichen Registerkarte

1. Wählen Sie in der Navigationsleiste ganz links neben der Teams App die Ellipsen aus, &#x25CF;&#x25CF;&#x25CF;. Es wird eine Liste der persönlichen Apps angezeigt.

1. Wählen Sie ihre Registerkarte aus der Liste aus, um sie anzuzeigen.
