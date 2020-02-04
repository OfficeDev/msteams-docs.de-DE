## <a name="prerequisites"></a><span data-ttu-id="096f3-101">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="096f3-101">Prerequisites</span></span>

- <span data-ttu-id="096f3-102">Um diesen Schnellstart abzuschließen, benötigen Sie einen Office 365 Mandanten und ein Team, das mit aktiviertem *Hochladen benutzerdefinierter apps zulassen* konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="096f3-102">To complete this quickstart you will need an Office 365 tenant and a team configured with *Allow uploading custom apps* enabled.</span></span> <span data-ttu-id="096f3-103">Weitere Informationen finden Sie unter [Vorbereiten des Office 365 Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="096f3-103">To learn more, see [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

  - <span data-ttu-id="096f3-104">Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich über das Office 365-Entwicklerprogramm für ein kostenloses Abonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="096f3-104">If you don't currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="096f3-105">Das Abonnement bleibt aktiv, solange Sie es für die laufende Entwicklung verwenden.</span><span class="sxs-lookup"><span data-stu-id="096f3-105">The subscription will remain active as long as you're using it for ongoing development.</span></span> <span data-ttu-id="096f3-106">Weitere Informationen finden Sie unter [Willkommen beim Office 365 Entwicklerprogramms](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).</span><span class="sxs-lookup"><span data-stu-id="096f3-106">See [Welcome to the Office 365 Developer Program](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).</span></span>

<span data-ttu-id="096f3-107">Dieses Projekt erfordert außerdem, dass in Ihrer Entwicklungsumgebung Folgendes installiert ist:</span><span class="sxs-lookup"><span data-stu-id="096f3-107">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="096f3-108">Jeder Text-Editor oder jede IDE.</span><span class="sxs-lookup"><span data-stu-id="096f3-108">Any text editor or IDE.</span></span> <span data-ttu-id="096f3-109">Sie können [Visual Studio-Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="096f3-109">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="096f3-110">[Node. js/NPM](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="096f3-110">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="096f3-111">Sie sollten die neueste LTS-Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="096f3-111">You should use the latest LTS version.</span></span> <span data-ttu-id="096f3-112">Der Knoten Paket-Manager (NPM) wird mit der Installation von Node. js auf Ihrem System installiert.</span><span class="sxs-lookup"><span data-stu-id="096f3-112">The Node Package Manager (npm) will install into your system with the installation of Node.js.</span></span>

- <span data-ttu-id="096f3-113">Nachdem Sie Node. js erfolgreich installiert haben, installieren Sie die [Pakete "Autobauer" und "](https://yeoman.io/) [Schluck-CLI](https://www.npmjs.com/package/gulp-cli) ", indem Sie an der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="096f3-113">After you've successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by typing the following in your command prompt:</span></span>

```bash
npm install yo gulp-cli --global
```

- <span data-ttu-id="096f3-114">Installieren Sie den Microsoft Teams apps-Generator, indem Sie an der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="096f3-114">Install the Microsoft Teams Apps generator by typing the following in your command prompt:</span></span>

```bash
npm install generator-teams --global
```

## <a name="generate-your-project"></a><span data-ttu-id="096f3-115">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="096f3-115">Generate your project</span></span>

- <span data-ttu-id="096f3-116">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt.</span><span class="sxs-lookup"><span data-stu-id="096f3-116">Open a command prompt and create a new directory for your tab project.</span></span>

- <span data-ttu-id="096f3-117">Navigieren Sie zum Starten des Generators zu Ihrem neuen Verzeichnis, und geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="096f3-117">To start the generator, navigate to your new directory and type the following command:</span></span>

```bash
yo teams
```

- <span data-ttu-id="096f3-118">Als nächstes geben Sie eine Reihe von Werten an, die in der **Manifest. JSON** -Datei Ihrer Anwendung verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="096f3-118">Next, you'll provide a series of values that will be used in your application's **manifest.json** file:</span></span>

![Screenshot des Generators wird geöffnet](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

<span data-ttu-id="096f3-120">**Wie lautet Ihr Lösungsname?**</span><span class="sxs-lookup"><span data-stu-id="096f3-120">**What is your solution name?**</span></span>

<span data-ttu-id="096f3-121">Dies ist Ihr Projektname.</span><span class="sxs-lookup"><span data-stu-id="096f3-121">This is your project name.</span></span> <span data-ttu-id="096f3-122">Sie können den vorgeschlagenen Namen übernehmen, indem Sie die EINGABETASTE drücken.</span><span class="sxs-lookup"><span data-stu-id="096f3-122">You can accept the suggested name by pressing enter.</span></span>

<span data-ttu-id="096f3-123">**Wohin möchten Sie die Daten verschieben?**</span><span class="sxs-lookup"><span data-stu-id="096f3-123">**Where do you want to place the files?**</span></span>

<span data-ttu-id="096f3-124">Sie befinden sich derzeit im Projektverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="096f3-124">You're currently in your project directory.</span></span> <span data-ttu-id="096f3-125">Drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="096f3-125">Press enter.</span></span>

<span data-ttu-id="096f3-126">**Titel Ihres Microsoft Teams-App-Projekts?**</span><span class="sxs-lookup"><span data-stu-id="096f3-126">**Title of your Microsoft Teams app project?**</span></span>

<span data-ttu-id="096f3-127">Dies ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet.</span><span class="sxs-lookup"><span data-stu-id="096f3-127">This is your app package name and will be used in the app manifest and description.</span></span>

<span data-ttu-id="096f3-128">**Ihren Namen (Firma)? (Max 32 Zeichen)**</span><span class="sxs-lookup"><span data-stu-id="096f3-128">**Your (company) name? (max 32 characters)**</span></span>

<span data-ttu-id="096f3-129">Der Name Ihres Unternehmens wird im App-Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="096f3-129">Your company name will be used in the app manifest.</span></span>

<br><span data-ttu-id="096f3-130">**Welche manifestVersion möchten Sie verwenden?**</span><span class="sxs-lookup"><span data-stu-id="096f3-130">**Which manifest version would you like to use?**</span></span>

<span data-ttu-id="096f3-131">Wählen Sie das Standardschema aus.</span><span class="sxs-lookup"><span data-stu-id="096f3-131">Select the default schema.</span></span>

<span data-ttu-id="096f3-132">**Geben Sie Ihre Microsoft Partner-ID ein (sofern vorhanden). (Leer lassen, um zu überspringen)**</span><span class="sxs-lookup"><span data-stu-id="096f3-132">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

<span data-ttu-id="096f3-133">Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner-Netzwerks](https://partner.microsoft.com)sind.</span><span class="sxs-lookup"><span data-stu-id="096f3-133">This field isn't required and should only be used if you're already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

<span data-ttu-id="096f3-134">**Was möchten Sie Ihrem Projekt hinzufügen?**</span><span class="sxs-lookup"><span data-stu-id="096f3-134">**What do you want to add to your project?**</span></span>

<span data-ttu-id="096f3-135">&ast; Wählen Sie eine Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="096f3-135">Select ( &ast; ) A Tab.</span></span>

<span data-ttu-id="096f3-136">**Die URL, unter der Sie diese Lösung hosten werden?**</span><span class="sxs-lookup"><span data-stu-id="096f3-136">**The URL where you will host this solution?**</span></span>

<span data-ttu-id="096f3-137">Standardmäßig schlägt der Generator eine Azure-Websites-URL vor.</span><span class="sxs-lookup"><span data-stu-id="096f3-137">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="096f3-138">Sie testen ihre app nur lokal, daher ist für die Ausführung dieses Schnellstarts keine gültige URL erforderlich.</span><span class="sxs-lookup"><span data-stu-id="096f3-138">You'll only be testing your app locally, therefore, a valid URL is not necessary to complete this quickstart.</span></span>

<span data-ttu-id="096f3-139">**Möchten Sie Test Framework und erste Tests einschließen? (j/N)**</span><span class="sxs-lookup"><span data-stu-id="096f3-139">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

<span data-ttu-id="096f3-140">Wählen Sie **kein** Test Framework für dieses Projekt einschließen aus.</span><span class="sxs-lookup"><span data-stu-id="096f3-140">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="096f3-141">Der Standardwert ist yes; Geben Sie **n**ein.</span><span class="sxs-lookup"><span data-stu-id="096f3-141">The default is yes; enter **n**.</span></span>

<span data-ttu-id="096f3-142">**Möchten Sie Azure Applications-Einblicke für Telemetrie verwenden? (j/N)**</span><span class="sxs-lookup"><span data-stu-id="096f3-142">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

<span data-ttu-id="096f3-143">Wählen Sie **nicht** aus, um [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md)einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="096f3-143">Choose **not** to include [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md).</span></span> <span data-ttu-id="096f3-144">Der Standardwert ist Nein; Geben Sie **n**ein.</span><span class="sxs-lookup"><span data-stu-id="096f3-144">The default is no; enter **n**.</span></span>

<span data-ttu-id="096f3-145">**Standardregisterkarten Name (maximal 16 Zeichen)?**</span><span class="sxs-lookup"><span data-stu-id="096f3-145">**Default Tab Name (max 16 characters)?**</span></span>

<span data-ttu-id="096f3-146">Nennen Sie die Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei-URL-Pfadkomponente verwendet.</span><span class="sxs-lookup"><span data-stu-id="096f3-146">Name your tab. This tab name will be used throughout your project as a file/URL path component.</span></span>
