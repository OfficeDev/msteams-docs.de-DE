## <a name="prerequisites"></a><span data-ttu-id="1bae5-101">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1bae5-101">Prerequisites</span></span>

- <span data-ttu-id="1bae5-102">Zum Abschließen dieses Schnellstarts benötigen Sie einen Office 365 Mandanten und ein Team, das mit aktivierter Aktivierung des *Hochladens benutzerdefinierter Apps konfiguriert* ist.</span><span class="sxs-lookup"><span data-stu-id="1bae5-102">To complete this quickstart you will need an Office 365 tenant and a team configured with *Allow uploading custom apps* enabled.</span></span> <span data-ttu-id="1bae5-103">Weitere Informationen finden Sie unter [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="1bae5-103">To learn more, see [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

  - <span data-ttu-id="1bae5-104">Wenn Sie derzeit kein Office 365 haben, können Sie sich über das Office 365 für ein kostenloses Abonnement registrieren.</span><span class="sxs-lookup"><span data-stu-id="1bae5-104">If you don't currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="1bae5-105">Das Abonnement bleibt aktiv, solange Sie es für die fortlaufende Entwicklung verwenden.</span><span class="sxs-lookup"><span data-stu-id="1bae5-105">The subscription will remain active as long as you're using it for ongoing development.</span></span> <span data-ttu-id="1bae5-106">Weitere [Informationen finden Sie unter Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="1bae5-106">See [Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="1bae5-107">Darüber hinaus erfordert dieses Projekt, dass Sie folgendes in Ihrer Entwicklungsumgebung installiert haben:</span><span class="sxs-lookup"><span data-stu-id="1bae5-107">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="1bae5-108">Beliebiger Texteditor oder IDE.</span><span class="sxs-lookup"><span data-stu-id="1bae5-108">Any text editor or IDE.</span></span> <span data-ttu-id="1bae5-109">Sie können die Visual Studio Code [kostenlos](https://code.visualstudio.com/download) installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="1bae5-109">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="1bae5-110">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="1bae5-110">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="1bae5-111">Sie sollten die neueste LTS-Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="1bae5-111">You should use the latest LTS version.</span></span> <span data-ttu-id="1bae5-112">Der Knoten Paket-Manager (npm) wird mit der Installation von Node.js.</span><span class="sxs-lookup"><span data-stu-id="1bae5-112">The Node Package Manager (npm) will install into your system with the installation of Node.js.</span></span>

- <span data-ttu-id="1bae5-113">Nachdem Sie die Node.js installiert haben, installieren Sie die [Pakete Yeoman](https://yeoman.io/) und [gulp-cli,](https://www.npmjs.com/package/gulp-cli) indem Sie folgendes in die Eingabeaufforderung eingeben:</span><span class="sxs-lookup"><span data-stu-id="1bae5-113">After you've successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by typing the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="1bae5-114">Installieren Sie den Microsoft Teams-Apps-Generator, indem Sie in der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="1bae5-114">Install the Microsoft Teams Apps generator by typing the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a><span data-ttu-id="1bae5-115">Generieren Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="1bae5-115">Generate your project</span></span>

- <span data-ttu-id="1bae5-116">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="1bae5-116">Open a command prompt and create a new directory for your tab project.</span></span>

- <span data-ttu-id="1bae5-117">Navigieren Sie zum Starten des Generators zu Ihrem neuen Verzeichnis, und geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="1bae5-117">To start the generator, navigate to your new directory and type the following command:</span></span>

    ```bash
    yo teams
    ```

- <span data-ttu-id="1bae5-118">Als Nächstes stellen Sie eine Reihe von Werten zur Verfügung, die in der Datei ihrer Anwendungmanifest.js **werden:**</span><span class="sxs-lookup"><span data-stu-id="1bae5-118">Next, you'll provide a series of values that will be used in your application's **manifest.json** file:</span></span>

    ![Screenshot zum Öffnen des Generators](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="1bae5-120">**Wie ist Ihr Lösungsname?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-120">**What is your solution name?**</span></span>

    <span data-ttu-id="1bae5-121">Dies ist Ihr Projektname.</span><span class="sxs-lookup"><span data-stu-id="1bae5-121">This is your project name.</span></span> <span data-ttu-id="1bae5-122">Sie können den vorgeschlagenen Namen akzeptieren, indem Sie die EINGABETASTE drücken.</span><span class="sxs-lookup"><span data-stu-id="1bae5-122">You can accept the suggested name by pressing enter.</span></span>

    <span data-ttu-id="1bae5-123">**Wohin möchten Sie die Daten verschieben?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-123">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="1bae5-124">Sie befinden sich derzeit im Projektverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="1bae5-124">You're currently in your project directory.</span></span> <span data-ttu-id="1bae5-125">Drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="1bae5-125">Press enter.</span></span>

    <span data-ttu-id="1bae5-126">**Titel Ihres Microsoft Teams-App-Projekts?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-126">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="1bae5-127">Dies ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bae5-127">This is your app package name and will be used in the app manifest and description.</span></span>

    <span data-ttu-id="1bae5-128">**Ihr (Firmen)-Name? (max. 32 Zeichen)**</span><span class="sxs-lookup"><span data-stu-id="1bae5-128">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="1bae5-129">Ihr Firmenname wird im App-Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bae5-129">Your company name will be used in the app manifest.</span></span>

    <span data-ttu-id="1bae5-130">**Welche Manifestversion möchten Sie verwenden?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-130">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="1bae5-131">Wählen Sie das Standardschema aus.</span><span class="sxs-lookup"><span data-stu-id="1bae5-131">Select the default schema.</span></span>

    <span data-ttu-id="1bae5-132">**Schnelles Gerüst? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="1bae5-132">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="1bae5-133">Der Standardwert ist Ja. Geben **Sie n** ein, um Ihre Microsoft Partner-ID ein eingeben.</span><span class="sxs-lookup"><span data-stu-id="1bae5-133">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="1bae5-134">**Geben Sie Ihre Microsoft Partner-ID ein, wenn Sie über eine verfügen? (Leer lassen, um zu überspringen)**</span><span class="sxs-lookup"><span data-stu-id="1bae5-134">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="1bae5-135">Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network sind.](https://partner.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="1bae5-135">This field isn't required and should only be used if you're already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="1bae5-136">**Was möchten Sie Ihrem Projekt hinzufügen?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-136">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="1bae5-137">Wählen Sie ( &ast; ) Eine Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="1bae5-137">Select ( &ast; ) A Tab.</span></span>

    <span data-ttu-id="1bae5-138">**Die URL, in der Sie diese Lösung hosten?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-138">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="1bae5-139">Standardmäßig schlägt der Generator eine Azure-Website-URL vor.</span><span class="sxs-lookup"><span data-stu-id="1bae5-139">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="1bae5-140">Sie testen Ihre App nur lokal, daher ist für diesen Schnellstart keine gültige URL erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1bae5-140">You'll only be testing your app locally, therefore, a valid URL is not necessary to complete this quickstart.</span></span>

    <span data-ttu-id="1bae5-141">**Möchten Sie das Testframework und die ersten Tests enthalten? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="1bae5-141">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="1bae5-142">Wählen **Sie aus,** kein Testframework für dieses Projekt zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="1bae5-142">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="1bae5-143">Der Standardwert ist Ja. Geben **Sie n** ein.</span><span class="sxs-lookup"><span data-stu-id="1bae5-143">The default is yes; enter **n**.</span></span>

    <span data-ttu-id="1bae5-144">**Möchten Sie Azure Applications Insights für telemetrie verwenden? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="1bae5-144">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="1bae5-145">Wählen **Sie aus,** dass [Azure Application Insights nicht enthalten ist.](/azure/azure-monitor/app/app-insights-overview)</span><span class="sxs-lookup"><span data-stu-id="1bae5-145">Choose **not** to include [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview).</span></span> <span data-ttu-id="1bae5-146">Der Standardwert ist nein. Geben **Sie n** ein.</span><span class="sxs-lookup"><span data-stu-id="1bae5-146">The default is no; enter **n**.</span></span>

    <span data-ttu-id="1bae5-147">**Standardregisterkartenname (max. 16 Zeichen)?**</span><span class="sxs-lookup"><span data-stu-id="1bae5-147">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="1bae5-148">Nennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei-/URL-Pfadkomponente verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bae5-148">Name your tab. This tab name will be used throughout your project as a file/URL path component.</span></span>
