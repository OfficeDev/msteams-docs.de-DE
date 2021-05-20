## <a name="prerequisites"></a>Voraussetzungen

- Um diese Schnellstartanleitung abzuschließen, benötigen Sie einen Office 365 Mandanten und ein Team, das mit *aktiviertem Hochladen benutzerdefinierter Apps* zulassen konfiguriert ist. Weitere Informationen finden Sie unter [Vorbereiten des Office 365 Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich über das Office 365 Developer Program für ein kostenloses Abonnement anmelden. Das Abonnement bleibt aktiv, solange Sie es für die laufende Entwicklung verwenden. Siehe [Willkommen im Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).

Darüber hinaus erfordert dieses Projekt, dass Sie folgendes in Ihrer Entwicklungsumgebung installiert haben:

- Jeder Texteditor oder IDE. Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.

- [Node.js/npm](https://nodejs.org/en/). Sie sollten die neueste LTS-Version verwenden. Der Knoten Paket-Manager (npm) wird mit der Installation von Node.js in Ihr System installiert.

- Nachdem Sie Node.js erfolgreich installiert haben, installieren Sie die [Pakete Yeoman](https://yeoman.io/) und [gulp-cli,](https://www.npmjs.com/package/gulp-cli) indem Sie in Ihrer Eingabeaufforderung Folgendes eingeben:

    ```bash
    npm install yo gulp-cli --global
    ```

- Installieren Sie den Microsoft Teams Apps-Generator, indem Sie in der Eingabeaufforderung Folgendes eingeben:

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a>Generieren Sie Ihr Projekt

- Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.

- Um den Generator zu starten, navigieren Sie zu Ihrem neuen Verzeichnis und geben Sie den folgenden Befehl ein:

    ```bash
    yo teams
    ```

- Als Nächstes stellen Sie eine Reihe von Werten bereit, die in der **manifest.js** Ihrer Anwendung verwendet werden:

    ![Generator-Eröffnungs-Screenshot](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    **Wie lautet Ihr Lösungsname?**

    Dies ist Ihr Projektname. Sie können den vorgeschlagenen Namen akzeptieren, indem Sie die Eingabetaste drücken.

    **Wohin möchten Sie die Daten verschieben?**

    Sie befinden sich derzeit in Ihrem Projektverzeichnis. Drücken Sie die Eingabetaste.

    **Titel Ihres Microsoft Teams App-Projekts?**

    Dies ist Ihr App-Paketname und wird im App-Manifest und in der Beschreibung verwendet.

    **Ihr (Firmen-)Name? (max. 32 Zeichen)**

    Ihr Firmenname wird im App-Manifest verwendet.

    **Welche Manifestversion möchten Sie verwenden?**

    Wählen Sie das Standardschema aus.

    **Schnelles Gerüst? (Y/n)**

    Der Standardwert ist yes; Geben Sie **n** ein, um Ihre Microsoft-Partner-ID einzugeben.

    **Geben Sie Ihre Microsoft-Partner-ID ein, wenn Sie eine haben? (Leer lassen, um zu überspringen)**

    Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network](https://partner.microsoft.com)sind.

    **Was möchten Sie Ihrem Projekt hinzufügen?**

    Wählen Sie ( &ast; ) Eine Registerkarte aus.

    **Die URL, unter der Sie diese Lösung hosten werden?**

    Standardmäßig schlägt der Generator eine Azure-Website-URL vor. Sie testen Ihre App nur lokal, daher ist keine gültige URL erforderlich, um diese Schnellstartanleitung abzuschließen.

    **Möchten Sie Testframework und erste Tests einschließen? (y/N)**

    Wählen Sie **aus,** dass kein Testframework für dieses Projekt enthalten sein soll. Der Standardwert ist yes; geben Sie **n** ein.

    **Möchten Sie Azure Applications Insights für Telemetriedaten verwenden? (y/N)**

    Wählen Sie **aus,** [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md)nicht einzuschließen. Der Standardwert ist nein; geben Sie **n** ein.

    **Standard-Tabname (max. 16 Zeichen)?**

    Benennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei-/URL-Pfadkomponente verwendet.
