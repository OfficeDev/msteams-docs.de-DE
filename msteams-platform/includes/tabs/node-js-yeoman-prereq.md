## <a name="prerequisites"></a><span data-ttu-id="b418c-101">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="b418c-101">Prerequisites</span></span>

- <span data-ttu-id="b418c-102">Um diese Schnellstartanleitung abzuschließen, benötigen Sie einen Office 365 Mandanten und ein Team, das mit *aktiviertem Hochladen benutzerdefinierter Apps* zulassen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="b418c-102">To complete this quickstart you will need an Office 365 tenant and a team configured with *Allow uploading custom apps* enabled.</span></span> <span data-ttu-id="b418c-103">Weitere Informationen finden Sie unter [Vorbereiten des Office 365 Mandanten](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="b418c-103">To learn more, see [Prepare your Office 365 tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

  - <span data-ttu-id="b418c-104">Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich über das Office 365 Developer Program für ein kostenloses Abonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="b418c-104">If you don't currently have an Office 365 account, you can sign up for a free subscription through the Office 365 Developer Program.</span></span> <span data-ttu-id="b418c-105">Das Abonnement bleibt aktiv, solange Sie es für die laufende Entwicklung verwenden.</span><span class="sxs-lookup"><span data-stu-id="b418c-105">The subscription will remain active as long as you're using it for ongoing development.</span></span> <span data-ttu-id="b418c-106">Siehe [Willkommen im Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="b418c-106">See [Welcome to the Office 365 Developer Program](/office/developer-program/microsoft-365-developer-program).</span></span>

<span data-ttu-id="b418c-107">Darüber hinaus erfordert dieses Projekt, dass Sie folgendes in Ihrer Entwicklungsumgebung installiert haben:</span><span class="sxs-lookup"><span data-stu-id="b418c-107">In addition, this project requires that you have the following installed in your development environment:</span></span>

- <span data-ttu-id="b418c-108">Jeder Texteditor oder IDE.</span><span class="sxs-lookup"><span data-stu-id="b418c-108">Any text editor or IDE.</span></span> <span data-ttu-id="b418c-109">Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="b418c-109">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

- <span data-ttu-id="b418c-110">[Node.js/npm](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="b418c-110">[Node.js/npm](https://nodejs.org/en/).</span></span> <span data-ttu-id="b418c-111">Sie sollten die neueste LTS-Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="b418c-111">You should use the latest LTS version.</span></span> <span data-ttu-id="b418c-112">Der Knoten Paket-Manager (npm) wird mit der Installation von Node.js in Ihr System installiert.</span><span class="sxs-lookup"><span data-stu-id="b418c-112">The Node Package Manager (npm) will install into your system with the installation of Node.js.</span></span>

- <span data-ttu-id="b418c-113">Nachdem Sie Node.js erfolgreich installiert haben, installieren Sie die [Pakete Yeoman](https://yeoman.io/) und [gulp-cli,](https://www.npmjs.com/package/gulp-cli) indem Sie in Ihrer Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="b418c-113">After you've successfully installed Node.js, install the [Yeoman](https://yeoman.io/) and [gulp-cli](https://www.npmjs.com/package/gulp-cli) packages by typing the following in your command prompt:</span></span>

    ```bash
    npm install yo gulp-cli --global
    ```

- <span data-ttu-id="b418c-114">Installieren Sie den Microsoft Teams Apps-Generator, indem Sie in der Eingabeaufforderung Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="b418c-114">Install the Microsoft Teams Apps generator by typing the following in your command prompt:</span></span>

    ```bash
    npm install generator-teams --global
    ```

## <a name="generate-your-project"></a><span data-ttu-id="b418c-115">Generieren Sie Ihr Projekt</span><span class="sxs-lookup"><span data-stu-id="b418c-115">Generate your project</span></span>

- <span data-ttu-id="b418c-116">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="b418c-116">Open a command prompt and create a new directory for your tab project.</span></span>

- <span data-ttu-id="b418c-117">Um den Generator zu starten, navigieren Sie zu Ihrem neuen Verzeichnis und geben Sie den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="b418c-117">To start the generator, navigate to your new directory and type the following command:</span></span>

    ```bash
    yo teams
    ```

- <span data-ttu-id="b418c-118">Als Nächstes stellen Sie eine Reihe von Werten bereit, die in der **manifest.js** Ihrer Anwendung verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="b418c-118">Next, you'll provide a series of values that will be used in your application's **manifest.json** file:</span></span>

    ![Generator-Eröffnungs-Screenshot](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <span data-ttu-id="b418c-120">**Wie lautet Ihr Lösungsname?**</span><span class="sxs-lookup"><span data-stu-id="b418c-120">**What is your solution name?**</span></span>

    <span data-ttu-id="b418c-121">Dies ist Ihr Projektname.</span><span class="sxs-lookup"><span data-stu-id="b418c-121">This is your project name.</span></span> <span data-ttu-id="b418c-122">Sie können den vorgeschlagenen Namen akzeptieren, indem Sie die Eingabetaste drücken.</span><span class="sxs-lookup"><span data-stu-id="b418c-122">You can accept the suggested name by pressing enter.</span></span>

    <span data-ttu-id="b418c-123">**Wohin möchten Sie die Daten verschieben?**</span><span class="sxs-lookup"><span data-stu-id="b418c-123">**Where do you want to place the files?**</span></span>

    <span data-ttu-id="b418c-124">Sie befinden sich derzeit in Ihrem Projektverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="b418c-124">You're currently in your project directory.</span></span> <span data-ttu-id="b418c-125">Drücken Sie die Eingabetaste.</span><span class="sxs-lookup"><span data-stu-id="b418c-125">Press enter.</span></span>

    <span data-ttu-id="b418c-126">**Titel Ihres Microsoft Teams App-Projekts?**</span><span class="sxs-lookup"><span data-stu-id="b418c-126">**Title of your Microsoft Teams app project?**</span></span>

    <span data-ttu-id="b418c-127">Dies ist Ihr App-Paketname und wird im App-Manifest und in der Beschreibung verwendet.</span><span class="sxs-lookup"><span data-stu-id="b418c-127">This is your app package name and will be used in the app manifest and description.</span></span>

    <span data-ttu-id="b418c-128">**Ihr (Firmen-)Name? (max. 32 Zeichen)**</span><span class="sxs-lookup"><span data-stu-id="b418c-128">**Your (company) name? (max 32 characters)**</span></span>

    <span data-ttu-id="b418c-129">Ihr Firmenname wird im App-Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="b418c-129">Your company name will be used in the app manifest.</span></span>

    <span data-ttu-id="b418c-130">**Welche Manifestversion möchten Sie verwenden?**</span><span class="sxs-lookup"><span data-stu-id="b418c-130">**Which manifest version would you like to use?**</span></span>

    <span data-ttu-id="b418c-131">Wählen Sie das Standardschema aus.</span><span class="sxs-lookup"><span data-stu-id="b418c-131">Select the default schema.</span></span>

    <span data-ttu-id="b418c-132">**Schnelles Gerüst? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="b418c-132">**Quick scaffolding? (Y/n)**</span></span>

    <span data-ttu-id="b418c-133">Der Standardwert ist yes; Geben Sie **n** ein, um Ihre Microsoft-Partner-ID einzugeben.</span><span class="sxs-lookup"><span data-stu-id="b418c-133">The default is yes; enter **n** to enter your Microsoft Partner Id.</span></span>

    <span data-ttu-id="b418c-134">**Geben Sie Ihre Microsoft-Partner-ID ein, wenn Sie eine haben? (Leer lassen, um zu überspringen)**</span><span class="sxs-lookup"><span data-stu-id="b418c-134">**Enter your Microsoft Partner Id, if you have one? (Leave blank to skip)**</span></span>

    <span data-ttu-id="b418c-135">Dieses Feld ist nicht erforderlich und sollte nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network](https://partner.microsoft.com)sind.</span><span class="sxs-lookup"><span data-stu-id="b418c-135">This field isn't required and should only be used if you're already part of the [Microsoft Partner Network](https://partner.microsoft.com).</span></span>

    <span data-ttu-id="b418c-136">**Was möchten Sie Ihrem Projekt hinzufügen?**</span><span class="sxs-lookup"><span data-stu-id="b418c-136">**What do you want to add to your project?**</span></span>

    <span data-ttu-id="b418c-137">Wählen Sie ( &ast; ) Eine Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="b418c-137">Select ( &ast; ) A Tab.</span></span>

    <span data-ttu-id="b418c-138">**Die URL, unter der Sie diese Lösung hosten werden?**</span><span class="sxs-lookup"><span data-stu-id="b418c-138">**The URL where you will host this solution?**</span></span>

    <span data-ttu-id="b418c-139">Standardmäßig schlägt der Generator eine Azure-Website-URL vor.</span><span class="sxs-lookup"><span data-stu-id="b418c-139">By default the generator suggests an Azure Web Sites URL.</span></span> <span data-ttu-id="b418c-140">Sie testen Ihre App nur lokal, daher ist keine gültige URL erforderlich, um diese Schnellstartanleitung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b418c-140">You'll only be testing your app locally, therefore, a valid URL is not necessary to complete this quickstart.</span></span>

    <span data-ttu-id="b418c-141">**Möchten Sie Testframework und erste Tests einschließen? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="b418c-141">**Would you like to include Test framework and initial tests? (y/N)**</span></span>

    <span data-ttu-id="b418c-142">Wählen Sie **aus,** dass kein Testframework für dieses Projekt enthalten sein soll.</span><span class="sxs-lookup"><span data-stu-id="b418c-142">Choose **not** to include a test framework for this project.</span></span> <span data-ttu-id="b418c-143">Der Standardwert ist yes; geben Sie **n** ein.</span><span class="sxs-lookup"><span data-stu-id="b418c-143">The default is yes; enter **n**.</span></span>

    <span data-ttu-id="b418c-144">**Möchten Sie Azure Applications Insights für Telemetriedaten verwenden? (y/N)**</span><span class="sxs-lookup"><span data-stu-id="b418c-144">**Would you like to use Azure Applications Insights for telemetry? (y/N)**</span></span>

    <span data-ttu-id="b418c-145">Wählen Sie **aus,** [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md)nicht einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b418c-145">Choose **not** to include [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md).</span></span> <span data-ttu-id="b418c-146">Der Standardwert ist nein; geben Sie **n** ein.</span><span class="sxs-lookup"><span data-stu-id="b418c-146">The default is no; enter **n**.</span></span>

    <span data-ttu-id="b418c-147">**Standard-Tabname (max. 16 Zeichen)?**</span><span class="sxs-lookup"><span data-stu-id="b418c-147">**Default Tab Name (max 16 characters)?**</span></span>

    <span data-ttu-id="b418c-148">Benennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei-/URL-Pfadkomponente verwendet.</span><span class="sxs-lookup"><span data-stu-id="b418c-148">Name your tab. This tab name will be used throughout your project as a file/URL path component.</span></span>
