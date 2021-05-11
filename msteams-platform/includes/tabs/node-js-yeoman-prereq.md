## <a name="prerequisites"></a>Voraussetzungen

- Zum Abschließen dieses Schnellstarts benötigen Sie einen Office 365 Mandanten und ein Team, das mit aktivierter Aktivierung des *Hochladens benutzerdefinierter Apps konfiguriert* ist. Weitere Informationen finden Sie unter [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Wenn Sie derzeit kein Office 365 haben, können Sie sich über das Office 365 für ein kostenloses Abonnement registrieren. Das Abonnement bleibt aktiv, solange Sie es für die fortlaufende Entwicklung verwenden. Weitere [Informationen finden Sie unter Welcome to the Office 365 Developer Program](https://docs.microsoft.com/office/developer-program/microsoft-365-developer-program).

Darüber hinaus erfordert dieses Projekt, dass Sie folgendes in Ihrer Entwicklungsumgebung installiert haben:

- Beliebiger Texteditor oder IDE. Sie können die Visual Studio Code [kostenlos](https://code.visualstudio.com/download) installieren und verwenden.

- [Node.js/npm](https://nodejs.org/en/). Sie sollten die neueste LTS-Version verwenden. Der Knoten Paket-Manager (npm) wird mit der Installation von Node.js.

- Nachdem Sie die Node.js installiert haben, installieren Sie die [Pakete Yeoman](https://yeoman.io/) und [gulp-cli,](https://www.npmjs.com/package/gulp-cli) indem Sie folgendes in die Eingabeaufforderung eingeben:

```bash
npm install yo gulp-cli --global
```

- Installieren Sie den Microsoft Teams-Apps-Generator, indem Sie in der Eingabeaufforderung Folgendes eingeben:

```bash
npm install generator-teams --global
```

## <a name="generate-your-project"></a>Generieren Ihres Projekts

- Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.

- Navigieren Sie zum Starten des Generators zu Ihrem neuen Verzeichnis, und geben Sie den folgenden Befehl ein:

```bash
yo teams
```

- Als Nächstes stellen Sie eine Reihe von Werten zur Verfügung, die in der Datei ihrer Anwendungmanifest.js **werden:**

![Screenshot zum Öffnen des Generators](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

**Wie ist Ihr Lösungsname?**

Dies ist Ihr Projektname. Sie können den vorgeschlagenen Namen akzeptieren, indem Sie die EINGABETASTE drücken.

**Wohin möchten Sie die Daten verschieben?**

Sie befinden sich derzeit im Projektverzeichnis. Drücken Sie die EINGABETASTE.

**Titel Ihres Microsoft Teams-App-Projekts?**

Dies ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet.

**Ihr (Firmen)-Name? (max. 32 Zeichen)**

Ihr Firmenname wird im App-Manifest verwendet.

<br>**Welche Manifestversion möchten Sie verwenden?**

Wählen Sie das Standardschema aus.

**Schnelles Gerüst? (Y/n)**

Der Standardwert ist Ja. Geben **Sie n** ein, um Ihre Microsoft Partner-ID ein eingeben.

**Geben Sie Ihre Microsoft Partner-ID ein, wenn Sie über eine verfügen? (Leer lassen, um zu überspringen)**

Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network sind.](https://partner.microsoft.com)

**Was möchten Sie Ihrem Projekt hinzufügen?**

Wählen Sie ( &ast; ) Eine Registerkarte aus.

**Die URL, in der Sie diese Lösung hosten?**

Standardmäßig schlägt der Generator eine Azure-Website-URL vor. Sie testen Ihre App nur lokal, daher ist für diesen Schnellstart keine gültige URL erforderlich.

**Möchten Sie das Testframework und die ersten Tests enthalten? (y/N)**

Wählen **Sie aus,** kein Testframework für dieses Projekt zu enthalten. Der Standardwert ist Ja. Geben **Sie n** ein.

**Möchten Sie Azure Applications Insights für telemetrie verwenden? (y/N)**

Wählen **Sie aus,** dass [Azure Application Insights nicht enthalten ist.](/azure-docs/articles/azure-monitor/app/app-insights-overview.md) Der Standardwert ist nein. Geben **Sie n** ein.

**Standardregisterkartenname (max. 16 Zeichen)?**

Nennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei-/URL-Pfadkomponente verwendet.
