### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="00fd1-101">Verwenden von App Studio zum Aktualisieren des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="00fd1-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="00fd1-102">App Studio ist eine Teams-App, die Sie aus dem Teams Store installieren können.</span><span class="sxs-lookup"><span data-stu-id="00fd1-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="00fd1-103">Dies vereinfacht das Erstellen und Registrieren einer App.</span><span class="sxs-lookup"><span data-stu-id="00fd1-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="00fd1-104">Führen Sie die folgenden Schritte aus, um das App-Paket zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="00fd1-104">Complete the following steps to update the app package:</span></span>

1. <span data-ttu-id="00fd1-105">Um App Studio in Teams zu installieren, wählen Sie unten auf der linken Leiste das Symbol **"Apps"** aus, und suchen Sie nach **App Studio:**</span><span class="sxs-lookup"><span data-stu-id="00fd1-105">To install App Studio in Teams, select the **Apps** icon at the bottom of the left-hand bar, and search for **App Studio**:</span></span>

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. <span data-ttu-id="00fd1-106">Wählen Sie die **Kachel "App Studio"** aus, und wählen Sie **"Installieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-106">Select the **App Studio** tile and choose **Install**.</span></span> <span data-ttu-id="00fd1-107">App Studio ist installiert:</span><span class="sxs-lookup"><span data-stu-id="00fd1-107">The App Studio is installed:</span></span>

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. <span data-ttu-id="00fd1-108">Um das App-Paket für Ihre Teams App zu erstellen, wählen Sie die Registerkarte **"Manifest-Editor"** in **App Studio** aus:</span><span class="sxs-lookup"><span data-stu-id="00fd1-108">To create the app package for your Teams app, select the **Manifest editor** tab in **App Studio**:</span></span>

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    <span data-ttu-id="00fd1-109">Das Beispiel enthält ein eigenes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="00fd1-109">The sample comes with its own manifest and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="00fd1-110">Sie können das App-Paket in .NET mit Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-110">You can build the app package on .NET with Visual Studio.</span></span> <span data-ttu-id="00fd1-111">In Visual Studio befindet sich die manifest.json-Datei unter **Manifest** in `Microsoft.Teams.Samples.HelloWorld.Web` .</span><span class="sxs-lookup"><span data-stu-id="00fd1-111">In Visual Studio, the manifest.json file is located in under **Manifest** in `Microsoft.Teams.Samples.HelloWorld.Web`.</span></span> <span data-ttu-id="00fd1-112">Dieser Schritt wird in der folgenden Abbildung beschrieben:</span><span class="sxs-lookup"><span data-stu-id="00fd1-112">This step is described by the following image:</span></span>  
    
    <img  width="450px" alt="Build the app package on .NET with Visual Studio" src="~/assets/images/get-started/app-package-on-.NET-with-Visual-Studio.png"/>
    
    <span data-ttu-id="00fd1-113">Sie können das App-Paket auf Node.js erstellen, indem Sie `gulp` an der Befehlszeile im Stammverzeichnis des Projekts eingeben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-113">You can build the app package on Node.js by typing `gulp` at the command line in the root directory of the project.</span></span>

    ```bash
    $ gulp
    [13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
    [13:39:27] Starting 'clean'...
    [13:39:27] Starting 'generate-manifest'...
    [13:39:27] Finished 'generate-manifest' after 11 ms
    [13:39:27] Finished 'clean' after 21 ms
    [13:39:27] Starting 'default'...
    Build completed. Output in manifest folder
    [13:39:27] Finished 'default' after 62 μs
    ```

    <span data-ttu-id="00fd1-114">Der Name des generierten App-Pakets ist **helloworldapp.zip.**</span><span class="sxs-lookup"><span data-stu-id="00fd1-114">The name of the generated app package is **helloworldapp.zip**.</span></span> <span data-ttu-id="00fd1-115">Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="00fd1-115">You can search for this file if the location is not clear in the tool you are using.</span></span>

1. <span data-ttu-id="00fd1-116">Wählen Sie nun zum Ändern dieses App-Pakets im **Manifest-Editor** die Option **"Vorhandene App importieren"** aus:</span><span class="sxs-lookup"><span data-stu-id="00fd1-116">Now to modify this app package, select **Import an existing app** in the **Manifest editor**:</span></span>

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. <span data-ttu-id="00fd1-117">Wählen Sie die **Kachel "Hello World"** für Ihre neu importierte App aus:</span><span class="sxs-lookup"><span data-stu-id="00fd1-117">Select the **Hello World** tile for your newly imported app:</span></span>

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

<span data-ttu-id="00fd1-118">Die folgende Abbildung zeigt das importierte App-Paket in App Studio:</span><span class="sxs-lookup"><span data-stu-id="00fd1-118">The following image shows the imported app package in App Studio:</span></span>

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

<span data-ttu-id="00fd1-119">Auf der linken Seite des Manifest-Editors finden Sie eine Liste der Schritte.</span><span class="sxs-lookup"><span data-stu-id="00fd1-119">On the left-hand side of the Manifest editor there is a list of steps.</span></span> <span data-ttu-id="00fd1-120">Auf der rechten Seite gibt es eine Liste der Eigenschaften, die für jeden Schritt ausgefüllt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-120">On the right-hand side there is a list of properties that need to be filled in for each step.</span></span> <span data-ttu-id="00fd1-121">Als Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-121">As you started with a sample app, much of the information is already completed.</span></span> <span data-ttu-id="00fd1-122">Mit den nächsten Schritten können Sie die Eigenschaften der Hello World-App aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="00fd1-122">The next steps enable you to update the properties of the Hello World app.</span></span>

#### <a name="app-details"></a><span data-ttu-id="00fd1-123">App-Details</span><span class="sxs-lookup"><span data-stu-id="00fd1-123">App details</span></span>

<span data-ttu-id="00fd1-124">Wählen Sie **App-Details** unter **Details** aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-124">Select **App details** under **Details**.</span></span> <span data-ttu-id="00fd1-125">Wählen Sie die Schaltfläche **"Generieren"** aus, um eine neue App-ID zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-125">Select the **Generate** button to create a new App ID.</span></span>

<span data-ttu-id="00fd1-126">Ihre neue App-ID ähnelt `2322041b-72bf-459d-b107-f4f335bc35bd` .</span><span class="sxs-lookup"><span data-stu-id="00fd1-126">Your new App ID is similar to `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="00fd1-127">Gehen Sie die App-Details im rechten Bereich durch, einschließlich **Entwicklerinformationen** und **Brandingdetails.**</span><span class="sxs-lookup"><span data-stu-id="00fd1-127">Go through the app details in the right-hand pane including **Developer information** and **Branding** details.</span></span> <span data-ttu-id="00fd1-128">Diese Details sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-128">These details are important if you are writing a new app for distribution.</span></span>

#### <a name="tabs"></a><span data-ttu-id="00fd1-129">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="00fd1-129">Tabs</span></span>

<span data-ttu-id="00fd1-130">Es ist einfach, einer Teams App Registerkarten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-130">It is simple to add tabs to a Teams app.</span></span> <span data-ttu-id="00fd1-131">Die Beispiel-App unterstützt bereits mehrere Registerkarten, die Sie aktivieren können.</span><span class="sxs-lookup"><span data-stu-id="00fd1-131">The sample app already supports several tabs, and you can enable them.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="00fd1-132">Registerkarte "Team"</span><span class="sxs-lookup"><span data-stu-id="00fd1-132">Team tab</span></span>

<span data-ttu-id="00fd1-133">Ihre App kann nur eine Teamregisterkarte haben:</span><span class="sxs-lookup"><span data-stu-id="00fd1-133">Your app can only have one Team tab:</span></span>

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

<span data-ttu-id="00fd1-134">In diesem Beispiel wird die Konfigurationsseite auf der Registerkarte "Team" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="00fd1-134">In this sample, the Team tab is where your configuration page is displayed.</span></span> <span data-ttu-id="00fd1-135">Wählen Sie das **Symbol ...** der **Registerkartenkonfigurations-URL** aus, und wählen Sie im Dropdownmenü die Option **"Bearbeiten"** aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-135">Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu.</span></span> <span data-ttu-id="00fd1-136">Ändern Sie die URL so, dass sie `https://yourteamsapp.ngrok.io/configure` durch die URL ersetzt werden `yourteamsapp.ngrok.io` muss, die Sie beim [Hosten Ihrer App](#host-the-sample-app)verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-136">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` must be replaced with the URL that you used when [hosting your app](#host-the-sample-app).</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="00fd1-137">Persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="00fd1-137">Personal tabs</span></span>

<span data-ttu-id="00fd1-138">Ihre App kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte "Team".</span><span class="sxs-lookup"><span data-stu-id="00fd1-138">Your app can have up to 16 tabs, including the Team tab.</span></span>

<span data-ttu-id="00fd1-139">Persönliche Registerkarten unterscheiden sich von der Registerkarte "Team". **Hello Tab** ist bereits in der Liste der persönlichen Registerkarten mit einem Platzhalterwert `com.contoso.helloworld.hellotab` aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="00fd1-139">Personal tabs are different from the Team tab. **Hello Tab** is already listed in the personal tabs list with a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="00fd1-140">Wählen Sie das **Symbol ...** der **Registerkartenkonfigurations-URL** aus, und wählen Sie im Dropdownmenü die Option **"Bearbeiten"** aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-140">Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu.</span></span> <span data-ttu-id="00fd1-141">Das folgende Dialogfeld wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="00fd1-141">The following dialog box appears:</span></span>

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

<span data-ttu-id="00fd1-142">Aktualisieren Sie die folgenden Felder mit Ihrer App-URL:</span><span class="sxs-lookup"><span data-stu-id="00fd1-142">Update the following boxes with your app URL:</span></span>

- <span data-ttu-id="00fd1-143">Ändern des **Felds "Inhalts-URL"** in `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="00fd1-143">Change the **Content URL** box to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="00fd1-144">Ändern sie das **Feld "Website-URL"** in `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="00fd1-144">Change the **Website URL** box to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="00fd1-145">Ersetzen Sie `yourteamsapp.ngrok.io` diese durch die URL, die Sie beim Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-145">Replace `yourteamsapp.ngrok.io` by the URL that you used when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="00fd1-146">Bots</span><span class="sxs-lookup"><span data-stu-id="00fd1-146">Bots</span></span>

<span data-ttu-id="00fd1-147">Es ist einfach, ihrer App die Bots-Funktionalität hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-147">It is easy to add the bots functionality to your app.</span></span> <span data-ttu-id="00fd1-148">Die Hello World-Beispiel-App verfügt bereits über einen Bot als Teil des Beispiels, Sie müssen ihn jedoch bei Microsoft registrieren: </span><span class="sxs-lookup"><span data-stu-id="00fd1-148">The **Hello World** sample app already has a bot as part of the sample, but you must register it with Microsoft:</span></span>

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

<span data-ttu-id="00fd1-149">Dem Bot, der aus dem Beispiel importiert wurde, ist keine App-ID zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="00fd1-149">The bot that was imported from the sample does not have an associated App ID.</span></span> <span data-ttu-id="00fd1-150">Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="00fd1-150">You must create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="00fd1-151">Die app-ID, die von App Studio für den Bot erstellt wurde, unterscheidet sich von der App-ID, die für die App erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="00fd1-151">The App ID created by App Studio for the bot is different from the App ID created for the app.</span></span> <span data-ttu-id="00fd1-152">Jeder Bot in einer App benötigt eine eigene App-ID.</span><span class="sxs-lookup"><span data-stu-id="00fd1-152">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="00fd1-153">Führen Sie die folgenden Schritte aus, um Ihren Bot einzurichten:</span><span class="sxs-lookup"><span data-stu-id="00fd1-153">Complete the following steps to setup your bot:</span></span>

1. <span data-ttu-id="00fd1-154">Wählen Sie **"Löschen"** neben dem importierten Bot in der Botliste aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-154">Select **Delete** next to the imported bot in the bot list.</span></span> <span data-ttu-id="00fd1-155">Jetzt gibt es keine Bots mehr, die angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="00fd1-155">Now there are no bots left to show.</span></span> 
1. <span data-ttu-id="00fd1-156">Wählen Sie **"Setup"** aus, um das Dialogfeld **"Bot einrichten"** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-156">Select **Setup** to display the **Set up a bot** dialog box.</span></span>

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. <span data-ttu-id="00fd1-157">Fügen Sie einen Botnamen **"Contoso-Bot"** hinzu, und aktivieren Sie alle drei Kontrollkästchen unter **"Bereich".**</span><span class="sxs-lookup"><span data-stu-id="00fd1-157">Add a bot name **Contoso bot** and select all three check boxes under **Scope**.</span></span>
1. <span data-ttu-id="00fd1-158">Wählen Sie **"Speichern"** aus, um das Dialogfeld zu beenden.</span><span class="sxs-lookup"><span data-stu-id="00fd1-158">Choose **Save** to exit the dialog box.</span></span> <span data-ttu-id="00fd1-159">App Studio registriert Ihren Bot bei Microsoft und zeigt Ihren neuen Bot in der Botliste an.</span><span class="sxs-lookup"><span data-stu-id="00fd1-159">App Studio registers your bot with Microsoft and displays your new bot in the bot list.</span></span> 
1. <span data-ttu-id="00fd1-160">Öffnen Sie nun eine Textdatei im Editor, und kopieren Sie Ihre neue Bot-ID, und fügen Sie sie ein.</span><span class="sxs-lookup"><span data-stu-id="00fd1-160">Now open a text file in notepad and copy and paste your new bot ID into it.</span></span>
1. <span data-ttu-id="00fd1-161">Klicken Sie auf **"Neues Kennwort generieren",** und notieren Sie sich das Kennwort in derselben Textdatei, die Sie als Bot-App-ID angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-161">Click **Generate New Password**, and note the password in the same text file you noted your bot App ID.</span></span>
1. <span data-ttu-id="00fd1-162">Aktualisieren Sie die **Bot-Endpunktadresse** auf und ersetzen Sie sie `https://yourteamsapp.ngrok.io/api/messages` durch die `yourteamsapp.ngrok.io` URL, die Sie beim Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-162">Update the **Bot endpoint address** to `https://yourteamsapp.ngrok.io/api/messages`, and replace `yourteamsapp.ngrok.io` with the URL that you used when hosting your app.</span></span>
1. <span data-ttu-id="00fd1-163">Speichern Sie nun Ihre Textdatei, da Sie die Informationen aus der Datei zu Ihrer gehosteten App hinzufügen müssen, um eine sichere Kommunikation mit Ihrem Bot zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-163">Now save your text file as you must add the information from the file to your hosted app to allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="00fd1-164">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="00fd1-164">Messaging extensions</span></span>

<span data-ttu-id="00fd1-165">MitHilfe von Messaging-Erweiterungen können Benutzer Informationen von Ihrem Dienst anfordern und diese Informationen veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-165">Messaging extensions let users ask for information from your service and post that information.</span></span> <span data-ttu-id="00fd1-166">Die Informationen werden in Form von Karten in der Kanalunterhaltung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="00fd1-166">The information is posted in the form of cards into the channel conversation.</span></span> <span data-ttu-id="00fd1-167">Messaging-Erweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="00fd1-167">Messaging extensions appear at the bottom of the compose box.</span></span>

<span data-ttu-id="00fd1-168">Führen Sie die folgenden Schritte aus, um Ihre Messaging-Erweiterung einzurichten:</span><span class="sxs-lookup"><span data-stu-id="00fd1-168">Complete the following steps to setup your messaging extension:</span></span>

1. <span data-ttu-id="00fd1-169">Wählen Sie **Messaging-Erweiterungen** unter **"Funktionen"** im linken Bereich von App Studio aus, um die Messaging-Erweiterung zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="00fd1-169">Select **Messaging extensions** under **Capabilities** in the left-hand pane of App Studio to configure the messaging extension:</span></span>

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    <span data-ttu-id="00fd1-170">Die Beispiel-Messaging-Erweiterung ist im Bereich **"Messaging-Erweiterungen"** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="00fd1-170">The sample messaging extension is listed in the **Messaging Extensions** pane.</span></span>

1. <span data-ttu-id="00fd1-171">Wählen Sie **"Löschen"** aus, um die Messaging-Erweiterung zu entfernen, wählen Sie **"Einrichten"** aus, und führen Sie die gleichen Schritte aus, die für [Bots](#bots)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="00fd1-171">Select **Delete** to remove the messaging extension, select **Set up**, and follow the same steps used for [bots](#bots).</span></span> <span data-ttu-id="00fd1-172">Das Dialogfeld **Messaging-Erweiterung** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="00fd1-172">The **Messaging Extension** dialog box is displayed.</span></span>
1. <span data-ttu-id="00fd1-173">Wählen Sie die Registerkarte **"Vorhandenen Bot verwenden"** und **"Aus einem meiner vorhandenen Bots auswählen" aus.**</span><span class="sxs-lookup"><span data-stu-id="00fd1-173">Select the **Use existing bot** tab and **Select from one of my existing bots**.</span></span>
1. <span data-ttu-id="00fd1-174">Wählen Sie den Bot aus, den Sie im Dropdownmenü erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="00fd1-174">Select the bot you created from the drop-down menu.</span></span> <span data-ttu-id="00fd1-175">Fügen Sie einen **Bot-Namen** hinzu, und wählen Sie **"Speichern"** aus, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-175">Add a **Bot name** and select **Save** to close the dialog box.</span></span>
1. <span data-ttu-id="00fd1-176">Wählen Sie im Abschnitt **"Befehl"** die Option **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-176">Under the **Command** section, select **Add**.</span></span> <span data-ttu-id="00fd1-177">Um einen suchbasierten Befehl hinzuzufügen, wählen Sie den Befehl **"Benutzer dürfen Ihren Dienst nach Informationen abfragen" aus, und fügen Sie diesen in eine Nachrichtenoption ein.**</span><span class="sxs-lookup"><span data-stu-id="00fd1-177">To add a search-based command, select the **Allow users to query your service for information and insert that into a message** option.</span></span>
1. <span data-ttu-id="00fd1-178">Geben Sie im Dialogfeld **"Neu"** die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="00fd1-178">In the **New command** dialog box, enter the following values:</span></span>

    <span data-ttu-id="00fd1-179">Under **New command**:</span><span class="sxs-lookup"><span data-stu-id="00fd1-179">Under **New command**:</span></span>

    - <span data-ttu-id="00fd1-180">**Befehls-ID:** Eingeben von zufälligen Text</span><span class="sxs-lookup"><span data-stu-id="00fd1-180">**Command ID**: Enter random text</span></span>
    - <span data-ttu-id="00fd1-181">**Title**: Enter random title</span><span class="sxs-lookup"><span data-stu-id="00fd1-181">**Title**: Enter random title</span></span>
    - <span data-ttu-id="00fd1-182">**Beschreibung:** Geben Sie eine zufällige Beschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="00fd1-182">**Description**: Enter random description</span></span>

    <span data-ttu-id="00fd1-183">Under **Parameter**:</span><span class="sxs-lookup"><span data-stu-id="00fd1-183">Under **Parameter**:</span></span>

    - <span data-ttu-id="00fd1-184">**Name:** Geben Sie den Parameternamen ein.</span><span class="sxs-lookup"><span data-stu-id="00fd1-184">**Name**: Enter the parameter name</span></span>
    - <span data-ttu-id="00fd1-185">**Titel:** Geben Sie den Kartentitel ein</span><span class="sxs-lookup"><span data-stu-id="00fd1-185">**Title**: Enter the card title</span></span>
    - <span data-ttu-id="00fd1-186">**Beschreibung:** Eingeben einer Kartenbeschreibung</span><span class="sxs-lookup"><span data-stu-id="00fd1-186">**Description**: Enter card description</span></span>

1. <span data-ttu-id="00fd1-187">Nachdem Sie die Informationen eingegeben haben, wählen Sie **Speichern** aus, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-187">After you enter the information, select **Save** to close the dialog box.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="00fd1-188">Registrieren Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="00fd1-188">Register your app in Teams</span></span>

<span data-ttu-id="00fd1-189">Führen Sie nach der Eingabe der Details Ihrer App die folgenden Schritte aus, um Ihre App in Teams zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="00fd1-189">After entering the details of your app, complete the following steps to register your app in Teams:</span></span>

1. <span data-ttu-id="00fd1-190">Verwenden Sie **"Testen" und verteilen** Sie App Studio, um Ihre App in Teams zu installieren.</span><span class="sxs-lookup"><span data-stu-id="00fd1-190">Use **Test and distribute** of App Studio to install your app in Teams.</span></span> 
1. <span data-ttu-id="00fd1-191">Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="00fd1-191">Update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="00fd1-192">Verwenden Sie für die Beispiel-App die gleiche App-ID und dasselbe Kennwort für Bot- und Messaging-Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-192">For the sample app, use the same App ID and password for both bot and messaging extension.</span></span> 
1. <span data-ttu-id="00fd1-193">Wählen Sie **"Testen" und "Verteilen"**  im linken Bereich von App Studio unter **"Fertig stellen"** aus:</span><span class="sxs-lookup"><span data-stu-id="00fd1-193">Select **Test and distribute**  under **Finish** in the left-hand pane of App Studio:</span></span>

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. <span data-ttu-id="00fd1-194">Um Ihre App in Teams hochzuladen, wählen Sie die Schaltfläche **"Installieren"** unter **"Testen und Verteilen"** aus:</span><span class="sxs-lookup"><span data-stu-id="00fd1-194">To upload your app to Teams, select the **Install** button under **Test and Distribute**:</span></span>

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

1. <span data-ttu-id="00fd1-195">Wählen Sie im Abschnitt **"Zu einem Team hinzufügen"** das **Suchfeld** aus, und wählen Sie ein Team aus, um die Beispiel-App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="00fd1-195">Select the **Search** box in the **Add to a team** section and select a team to add the sample app.</span></span> <span data-ttu-id="00fd1-196">Sie können ein spezielles Team für Tests einrichten.</span><span class="sxs-lookup"><span data-stu-id="00fd1-196">You can set up a special team for testing.</span></span>
1. <span data-ttu-id="00fd1-197">Wählen Sie unten im Dialogfeld die Schaltfläche **"Installieren"** aus.</span><span class="sxs-lookup"><span data-stu-id="00fd1-197">Select the **Install** button at the bottom of the dialog box.</span></span>

<span data-ttu-id="00fd1-198">Ihre App ist jetzt in Teams verfügbar.</span><span class="sxs-lookup"><span data-stu-id="00fd1-198">Your app is now available in Teams.</span></span> <span data-ttu-id="00fd1-199">Der Bot und die Messaging-Erweiterung funktionieren jedoch erst, wenn Sie die Gehostete Anwendungsumgebung mit den App-IDs und Kennwörtern aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="00fd1-199">However, the bot and the messaging extension will not work until you update the hosted applications environment with the App IDs and passwords.</span></span>

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
