## <a name="prerequisites"></a>Voraussetzungen

- Um diesen Schnellstart abzuschließen, benötigen Sie einen Office 365 Mandanten und ein Team, das mit aktiviertem *Hochladen benutzerdefinierter apps zulassen* konfiguriert ist. Weitere Informationen finden Sie unter [Vorbereiten des Office 365 Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich über das Office 365-Entwicklerprogramm für ein kostenloses Abonnement anmelden. Das Abonnement bleibt aktiv, solange Sie es für die laufende Entwicklung verwenden. Weitere Informationen finden Sie unter [Willkommen beim Office 365 Entwicklerprogramms](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).

Dieses Projekt erfordert außerdem, dass in Ihrer Entwicklungsumgebung Folgendes installiert ist:

- Jeder Text-Editor oder jede IDE. Sie können [Visual Studio-Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.

- [Node. js/NPM](https://nodejs.org/en/). Sie sollten die neueste LTS-Version verwenden. Der Knoten Paket-Manager (NPM) wird mit der Installation von Node. js auf Ihrem System installiert.

- Nachdem Sie Node. js erfolgreich installiert haben, installieren Sie die [Pakete "Autobauer" und "](https://yeoman.io/) [Schluck-CLI](https://www.npmjs.com/package/gulp-cli) ", indem Sie an der Eingabeaufforderung Folgendes eingeben:

```bash
npm install yo gulp-cli --global
```

- Installieren Sie den Microsoft Teams apps-Generator, indem Sie an der Eingabeaufforderung Folgendes eingeben:

```bash
npm install generator-teams --global
```

## <a name="generate-your-project"></a>Erstellen des Projekts

- Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt.

- Navigieren Sie zum Starten des Generators zu Ihrem neuen Verzeichnis, und geben Sie den folgenden Befehl ein:

```bash
yo teams
```

- Als nächstes geben Sie eine Reihe von Werten an, die in der **Manifest. JSON** -Datei Ihrer Anwendung verwendet werden:

![Screenshot des Generators wird geöffnet](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

**Wie lautet Ihr Lösungsname?**

Dies ist Ihr Projektname. Sie können den vorgeschlagenen Namen übernehmen, indem Sie die EINGABETASTE drücken.

**Wohin möchten Sie die Daten verschieben?**

Sie befinden sich derzeit im Projektverzeichnis. Drücken Sie die EINGABETASTE.

**Titel Ihres Microsoft Teams-App-Projekts?**

Dies ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet.

**Ihren Namen (Firma)? (Max 32 Zeichen)**

Der Name Ihres Unternehmens wird im App-Manifest verwendet.

<br>**Welche manifestVersion möchten Sie verwenden?**

Wählen Sie das Standardschema aus.

**Geben Sie Ihre Microsoft Partner-ID ein (sofern vorhanden). (Leer lassen, um zu überspringen)**

Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner-Netzwerks](https://partner.microsoft.com)sind.

**Was möchten Sie Ihrem Projekt hinzufügen?**

&ast; Wählen Sie eine Registerkarte aus.

**Die URL, unter der Sie diese Lösung hosten werden?**

Standardmäßig schlägt der Generator eine Azure-Websites-URL vor. Sie testen ihre app nur lokal, daher ist für die Ausführung dieses Schnellstarts keine gültige URL erforderlich.

**Möchten Sie Test Framework und erste Tests einschließen? (j/N)**

Wählen Sie **kein** Test Framework für dieses Projekt einschließen aus. Der Standardwert ist yes; Geben Sie **n**ein.

**Möchten Sie Azure Applications-Einblicke für Telemetrie verwenden? (j/N)**

Wählen Sie **nicht** aus, um [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md)einzubeziehen. Der Standardwert ist Nein; Geben Sie **n**ein.

**Standardregisterkarten Name (maximal 16 Zeichen)?**

Nennen Sie die Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei-URL-Pfadkomponente verwendet.
