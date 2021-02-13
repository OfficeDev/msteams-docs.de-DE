### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="1ac59-101">Verwenden von App Studio zum Aktualisieren des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="1ac59-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="1ac59-102">App Studio ist eine Teams-App, die Sie aus dem Teams Store installieren können.</span><span class="sxs-lookup"><span data-stu-id="1ac59-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="1ac59-103">Dies vereinfacht das Erstellen und Registrieren einer App.</span><span class="sxs-lookup"><span data-stu-id="1ac59-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="1ac59-104">Um App Studio in Teams zu installieren, wählen Sie das Symbol **"Apps"** am unteren Rand der linken Leiste aus, und suchen Sie nach **App Studio.**</span><span class="sxs-lookup"><span data-stu-id="1ac59-104">To install App Studio in Teams, select the **Apps** icon at the bottom of the left-hand bar, and search for **App Studio**.</span></span>

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

<span data-ttu-id="1ac59-105">Wählen Sie die **Kachel "App Studio"** und dann **"Installieren" aus.**</span><span class="sxs-lookup"><span data-stu-id="1ac59-105">Select the **App Studio** tile and choose **Install**.</span></span> <span data-ttu-id="1ac59-106">App Studio ist installiert.</span><span class="sxs-lookup"><span data-stu-id="1ac59-106">The App Studio is installed.</span></span>

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

<span data-ttu-id="1ac59-107">Wählen Sie die **Registerkarte "Manifest-Editor"** aus, um das App-Paket für Ihre Teams-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-107">Select the **Manifest editor** tab to create the app package for your Teams app.</span></span>

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

<span data-ttu-id="1ac59-108">Das Beispiel enthält ein eigenes vordefiniertes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="1ac59-108">The sample comes with its own pre-made manifest and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="1ac59-109">In .NET erfolgt dies in Visual Studio, und auf Knoten JS erfolgt dies durch Eingabe an der Befehlszeile im Stammverzeichnis `gulp` des Projekts.</span><span class="sxs-lookup"><span data-stu-id="1ac59-109">On .NET this is done in Visual Studio, and on Node JS this is done by typing `gulp` at the command line in the root directory of the project.</span></span>

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

<span data-ttu-id="1ac59-110">Der Name des generierten App-Pakets **isthelloworldapp.zip**.</span><span class="sxs-lookup"><span data-stu-id="1ac59-110">The name of the generated app package is **helloworldapp.zip**.</span></span> <span data-ttu-id="1ac59-111">Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="1ac59-111">You can search for this file if the location is not clear in the tool you are using.</span></span>

<span data-ttu-id="1ac59-112">Um nun dieses App-Paket zu ändern, wählen Sie die **Kachel "Vorhandene** App importieren" im **Manifest-Editor aus.**</span><span class="sxs-lookup"><span data-stu-id="1ac59-112">Now to modify this app package, select the **Import an existing app** tile in the **Manifest editor**.</span></span>

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

<span data-ttu-id="1ac59-113">Klicken Sie **auf die Kachel "Hello World"** für Ihre neu importierte App.</span><span class="sxs-lookup"><span data-stu-id="1ac59-113">Click the **Hello World** tile for your newly imported app.</span></span>

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

<span data-ttu-id="1ac59-114">Die folgende Abbildung zeigt das importierte App-Paket in App Studio:</span><span class="sxs-lookup"><span data-stu-id="1ac59-114">The following image shows the imported app package in App Studio:</span></span>

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

<span data-ttu-id="1ac59-115">Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die für jeden dieser Schritte ausgefüllt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-115">There is a list of steps on the left-hand side of the Manifest editor and on the right-hand side, a list of properties that need to be filled in for each of those steps.</span></span> <span data-ttu-id="1ac59-116">Seit Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits ausgefüllt. In den nächsten Schritten werden Sie durch das Ändern der Noch zu aktualisierenden Teile gehen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-116">Since you started with a sample app, much of the information is already filled out. The next steps will walk you through changing the parts that still need to be updated.</span></span>

#### <a name="app-details"></a><span data-ttu-id="1ac59-117">Details zur App</span><span class="sxs-lookup"><span data-stu-id="1ac59-117">App details</span></span>

<span data-ttu-id="1ac59-118">Klicken Sie unter *"Details" auf* den Eintrag *"App-Details".*</span><span class="sxs-lookup"><span data-stu-id="1ac59-118">Click on the *App details* entry under *Details*.</span></span> <span data-ttu-id="1ac59-119">Klicken *Sie* auf die Schaltfläche "Generieren", um eine neue App-ID zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-119">Click the *Generate* button to create a new app id.</span></span>

<span data-ttu-id="1ac59-120">Ihre neue App-ID sollte in etwa so aussehen: `2322041b-72bf-459d-b107-f4f335bc35bd` .</span><span class="sxs-lookup"><span data-stu-id="1ac59-120">Your new app id should look something like: `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="1ac59-121">Sehen Sie sich die restlichen Details der App im rechten Bereich an,  und machen Sie sich mit einigen Einträgen wie Entwicklerinformationen und *Branding vertraut.*</span><span class="sxs-lookup"><span data-stu-id="1ac59-121">Look through the rest of the App details in the right-hand pane, and familiarize yourself with some of the entries such as *Developer information* and *Branding*.</span></span> <span data-ttu-id="1ac59-122">Diese Abschnitte sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-122">These sections are important if you are writing a new app for distribution.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="1ac59-123">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="1ac59-123">Capabilities: Tabs</span></span>

<span data-ttu-id="1ac59-124">Registerkarten gehören zu den einfachsten Elementen, die einer Teams-App hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="1ac59-124">Tabs are among the simplest elements to add to a Teams app.</span></span> <span data-ttu-id="1ac59-125">Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können sie wie folgt aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1ac59-125">The sample app already supports several tabs, and you can enable them as follows.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="1ac59-126">Registerkarte "Team"</span><span class="sxs-lookup"><span data-stu-id="1ac59-126">Team tab</span></span>

<span data-ttu-id="1ac59-127">Ihre App kann nur eine Teamregisterkarte haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-127">Your app can only have one Team tab.</span></span>

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

<span data-ttu-id="1ac59-128">In diesem Beispiel wird auf der Registerkarte "Team" die Konfigurationsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ac59-128">In this sample, the Team tab is where your configuration page goes.</span></span> <span data-ttu-id="1ac59-129">Klicken Sie am *Ende* des Eintrags auf das Symbol ..., und wählen Sie *in* der Dropdownliste "Bearbeiten" aus.</span><span class="sxs-lookup"><span data-stu-id="1ac59-129">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="1ac59-130">Ändern Sie die URL so, dass sie durch die URL ersetzt werden soll, die Sie oben beim `https://yourteamsapp.ngrok.io/configure` `yourteamsapp.ngrok.io` Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-130">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="1ac59-131">Persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="1ac59-131">Personal tabs</span></span>

<span data-ttu-id="1ac59-132">Ihre App kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte "Team".</span><span class="sxs-lookup"><span data-stu-id="1ac59-132">Your app can have up to 16 tabs, including the team tab.</span></span>

<span data-ttu-id="1ac59-133">Persönliche Registerkarten werden anders dargestellt als die Registerkarte "Team". Die Registerkarte *"Hello" sollte* bereits in der Liste der persönlichen Registerkarten aufgeführt sein.</span><span class="sxs-lookup"><span data-stu-id="1ac59-133">Personal tabs are represented differently from the team tab. You should see *Hello Tab* already listed in the personal tabs list.</span></span> <span data-ttu-id="1ac59-134">Zurzeit hat sie einen `com.contoso.helloworld.hellotab` Platzhalterwert.</span><span class="sxs-lookup"><span data-stu-id="1ac59-134">At the moment it has a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="1ac59-135">Klicken Sie am *Ende* des Eintrags auf das Symbol ..., und wählen Sie *in* der Dropdownliste "Bearbeiten" aus.</span><span class="sxs-lookup"><span data-stu-id="1ac59-135">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="1ac59-136">Das folgende Dialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ac59-136">The following dialog will appear.</span></span>

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

<span data-ttu-id="1ac59-137">Es gibt zwei Felder, die Sie mit Ihrer App-URL aktualisieren müssen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-137">There are two fields that you need to update with your app URL.</span></span>

- <span data-ttu-id="1ac59-138">Ändern der Inhalts-URL in `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="1ac59-138">Change Content URL to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="1ac59-139">Ändern der Website-URL in `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="1ac59-139">Change Website URL to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="1ac59-140">Wo `yourteamsapp.ngrok.io` sollte die URL ersetzt werden, die Sie oben beim Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-140">Where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="1ac59-141">Bots</span><span class="sxs-lookup"><span data-stu-id="1ac59-141">Bots</span></span>

<span data-ttu-id="1ac59-142">Bots sind die am häufigsten verwendeten Möglichkeit, Ihrer App Funktionen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-142">Bots are the most common way to add functionality to your app.</span></span> <span data-ttu-id="1ac59-143">Das Beispiel "Hello World" hat bereits einen Bot als Teil des Beispiels, wurde aber noch nicht bei Microsoft registriert.</span><span class="sxs-lookup"><span data-stu-id="1ac59-143">The hello world sample already has a bot as part of the sample, but it has not been registered with Microsoft yet.</span></span>

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

<span data-ttu-id="1ac59-144">Dem Bot, der aus dem Beispiel importiert wurde, ist noch keine App-ID zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="1ac59-144">The bot that was imported from the sample does not have an App ID associated with it yet.</span></span> <span data-ttu-id="1ac59-145">Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="1ac59-145">You will have to create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span> <span data-ttu-id="1ac59-146">Beachten Sie, dass dies die App-ID für den Bot ist, die sich von der für die App erstellten App-ID abh?nt.</span><span class="sxs-lookup"><span data-stu-id="1ac59-146">Note that this is the App ID for the bot, which is different from the App ID created for the app.</span></span> <span data-ttu-id="1ac59-147">Jeder Bot in einer App benötigt eine eigene App-ID.</span><span class="sxs-lookup"><span data-stu-id="1ac59-147">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="1ac59-148">Klicken Sie *auf die Schaltfläche* "Löschen" neben dem *importierten Bot* in der Botliste.</span><span class="sxs-lookup"><span data-stu-id="1ac59-148">Click the *delete* button next to the *Imported bot* in the bot list.</span></span>

<span data-ttu-id="1ac59-149">Jetzt gibt es keine Bots mehr, die sie anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="1ac59-149">Now there are no bots left to show.</span></span> <span data-ttu-id="1ac59-150">Klicken Sie *auf Setup*.</span><span class="sxs-lookup"><span data-stu-id="1ac59-150">Click *Setup*.</span></span> <span data-ttu-id="1ac59-151">Dadurch wird das Dialogfeld *"Bot einrichten"* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ac59-151">This will display the *Set up a bot* dialog.</span></span>

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

<span data-ttu-id="1ac59-152">Fügen Sie einen Botnamen wie hinzu, und wählen Sie unter Bereich `Contoso bot` alle drei **Schaltflächen aus.**</span><span class="sxs-lookup"><span data-stu-id="1ac59-152">Add a bot name such as `Contoso bot`, and select all three buttons under **Scope**.</span></span>

<span data-ttu-id="1ac59-153">Choose *Create bot* to exit the dialog.</span><span class="sxs-lookup"><span data-stu-id="1ac59-153">Choose *Create bot* to exit the dialog.</span></span> <span data-ttu-id="1ac59-154">App Studio registriert Ihren Bot bei Microsoft und zeigt den neuen Bot in der Botliste an.</span><span class="sxs-lookup"><span data-stu-id="1ac59-154">App Studio registers your bot with Microsoft and displays your new bot in the bot list.</span></span> <span data-ttu-id="1ac59-155">Jetzt wäre es ein guter Zeitpunkt, eine Textdatei im Editor zu öffnen und Ihre neue Bot-ID zu kopieren und in sie zu einfügen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-155">Now would be a good time to open a text file in notepad and copy and paste your new bot id into it.</span></span> <span data-ttu-id="1ac59-156">Sie benötigen diese ID später.</span><span class="sxs-lookup"><span data-stu-id="1ac59-156">You will need this id later.</span></span>

<span data-ttu-id="1ac59-157">Klicken *Sie auf "Neues Kennwort generieren",* und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre Bot-App-ID notiert haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-157">Click *Generate New Password*, and make a note of the password in the same text file you noted your Bot app ID in.</span></span> <span data-ttu-id="1ac59-158">Dies ist das einzige Mal, dass Ihr Kennwort angezeigt wird. Stellen Sie daher sicher, dass Sie dies jetzt tun.</span><span class="sxs-lookup"><span data-stu-id="1ac59-158">This is the only time your password will be shown, so be sure to do this now.</span></span>

<span data-ttu-id="1ac59-159">Aktualisieren Sie die *Adresse des Bot-Endpunkts* auf , wo sie durch die URL ersetzt werden sollte, die Sie oben beim `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-159">Update the *Bot endpoint address* to `https://yourteamsapp.ngrok.io/api/messages`, where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

<span data-ttu-id="1ac59-160">Jetzt wäre es ein guter Zeitpunkt, Ihre Textdatei zu speichern, wenn Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-160">Now would be a good time to save your text file if you have not done so already.</span></span> <span data-ttu-id="1ac59-161">Sie fügen diese Informationen später in dieser exemplarischen Vorgehensweise zu Ihrer gehosteten App hinzu, was eine sichere Kommunikation mit Ihrem Bot ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1ac59-161">You will add this information to your hosted app later in this walkthrough, which will allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="1ac59-162">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="1ac59-162">Messaging extensions</span></span>

<span data-ttu-id="1ac59-163">Mit Messagingerweiterungen können Benutzer Informationen von Ihrem Dienst ein- und ausstellen und diese Informationen in Form von Karten direkt in der Kanal unterhaltung veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-163">Messaging extensions let users ask for information from your service and post that information, in the form of cards, right into the channel conversation.</span></span> <span data-ttu-id="1ac59-164">Messagingerweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ac59-164">Messaging extensions appear along the bottom of the compose box.</span></span>

<span data-ttu-id="1ac59-165">Wählen **Sie messaging extensions** under **Capabilities** in the left-hand column of App Studio to configure the messaging extension.</span><span class="sxs-lookup"><span data-stu-id="1ac59-165">Select **Messaging extensions** under **Capabilities** in the left-hand column of App Studio to configure the messaging extension.</span></span>

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

<span data-ttu-id="1ac59-166">Die Beispiel-Messaging-Erweiterung ist im rechten Bereich unter **"Messaging Extensions" aufgeführt.**</span><span class="sxs-lookup"><span data-stu-id="1ac59-166">The sample messaging extension is listed in the right-hand pane under **Messaging Extensions**.</span></span> <span data-ttu-id="1ac59-167">Wählen **Sie erneut** "Löschen" aus,  um diesen Eintrag zu entfernen, und klicken Sie dann auf die Schaltfläche "Einrichten", indem Sie die gleichen Schritte wie für Bots ausführen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-167">Select **Delete** again to remove this entry, and then click the *Set up* button following the same steps as you followed for bots.</span></span> <span data-ttu-id="1ac59-168">Dadurch wird das Dialogfeld *"Messagingerweiterung"* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1ac59-168">This will display the *Messaging Extension* dialog.</span></span>

<span data-ttu-id="1ac59-169">Wählen Sie *die Registerkarte "Vorhandenen Bot verwenden"* aus, und wählen Sie dann aus einem meiner *vorhandenen Bots aus.*</span><span class="sxs-lookup"><span data-stu-id="1ac59-169">Select the *Use existing bot* tab, then *Select from one of my existing bots*.</span></span> <span data-ttu-id="1ac59-170">Wählen Sie im Dropdownmenü den Bot aus, den Sie im abschnitt oben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="1ac59-170">In the drop-down menu, select the bot you created in the section above.</span></span> <span data-ttu-id="1ac59-171">Fügen Sie einen *Botnamen hinzu,* und klicken *Sie auf "Speichern",* um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-171">Add a *Bot name* and click *Save* to close the dialog.</span></span>

<span data-ttu-id="1ac59-172">Klicken Sie *im Befehlsabschnitt* auf *"Hinzufügen".*</span><span class="sxs-lookup"><span data-stu-id="1ac59-172">Under the *Command* section, click *Add*.</span></span> <span data-ttu-id="1ac59-173">We're adding a search-based command, so choose the *Allow users to query your service...* option.</span><span class="sxs-lookup"><span data-stu-id="1ac59-173">We're adding a search-based command, so choose the *Allow users to query your service...* option.</span></span>

<span data-ttu-id="1ac59-174">Geben Sie **im Dialogfeld "Neu"** die folgenden Werte ein.</span><span class="sxs-lookup"><span data-stu-id="1ac59-174">In the **New command** dialog, enter the following values.</span></span>

<span data-ttu-id="1ac59-175">Under *New command*:</span><span class="sxs-lookup"><span data-stu-id="1ac59-175">Under *New command*:</span></span>

- <span data-ttu-id="1ac59-176">*Befehls-ID*  = getRandomText</span><span class="sxs-lookup"><span data-stu-id="1ac59-176">*Command ID*  = getRandomText</span></span>
- <span data-ttu-id="1ac59-177">*Title*       = Get some random text for fun</span><span class="sxs-lookup"><span data-stu-id="1ac59-177">*Title*       = Get some random text for fun</span></span>
- <span data-ttu-id="1ac59-178">*Beschreibung* = Ruft zufälligen Text und Bilder ab</span><span class="sxs-lookup"><span data-stu-id="1ac59-178">*Description* = Gets some random text and images</span></span>

<span data-ttu-id="1ac59-179">Under *Parameter*:</span><span class="sxs-lookup"><span data-stu-id="1ac59-179">Under *Parameter*:</span></span>

- <span data-ttu-id="1ac59-180">*Name*        = cardTitle</span><span class="sxs-lookup"><span data-stu-id="1ac59-180">*Name*        = cardTitle</span></span>
- <span data-ttu-id="1ac59-181">*Titel*       = Kartentitel</span><span class="sxs-lookup"><span data-stu-id="1ac59-181">*Title*       = Card title</span></span>
- <span data-ttu-id="1ac59-182">*Beschreibung* = Zu verwendende Kartentitel</span><span class="sxs-lookup"><span data-stu-id="1ac59-182">*Description* = Card title to use</span></span>

<span data-ttu-id="1ac59-183">Nachdem Sie die Informationen eingegeben haben, klicken Sie auf *"Speichern",* um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-183">Once you're entered the information, click *Save* to close the dialog.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="1ac59-184">Registrieren Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="1ac59-184">Register your app in Teams</span></span>

<span data-ttu-id="1ac59-185">Sie haben nun die Eingabe der Details Ihrer App abgeschlossen, aber die folgenden beiden Schritte bleiben bestehen:</span><span class="sxs-lookup"><span data-stu-id="1ac59-185">You have now completed entering the details of your app, but the following two steps remain:</span></span>
1. <span data-ttu-id="1ac59-186">Verwenden Sie den Abschnitt "Testen und Verteilen" von App Studio, um Ihre App in Teams zu installieren.</span><span class="sxs-lookup"><span data-stu-id="1ac59-186">Use the Test and Distribute section of App Studio to install your app in Teams.</span></span>
1. <span data-ttu-id="1ac59-187">Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="1ac59-187">Update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="1ac59-188">Denken Sie daran, dass im Beispiel davon ausging, die gleiche App-ID und dasselbe Kennwort sowohl für den Bot als auch für die Messagingerweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1ac59-188">Remember that the sample expects to use the same App ID and password for both the bot and the messaging extension.</span></span>

<span data-ttu-id="1ac59-189">Wählen Sie das Element  **"Testen" und "Verteilen"** unter "Fertig stellen" in der linken Spalte von App Studio aus.</span><span class="sxs-lookup"><span data-stu-id="1ac59-189">Select the **Test and distribute** item under **Finish** in the left-hand column of App Studio.</span></span>

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

<span data-ttu-id="1ac59-190">Um Ihre App in Teams hochzuladen, klicken Sie unter "Testen" und "Verteilen" auf *die Schaltfläche "Installieren".* </span><span class="sxs-lookup"><span data-stu-id="1ac59-190">In order to upload your app to Teams, click the *Install* button under *Test and Distribute*.</span></span>

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

<span data-ttu-id="1ac59-191">Wählen Sie **im Abschnitt "Zu** einem Team hinzufügen" das Suchfeld **aus,** und wählen Sie ein Team aus, dem die Beispiel-App hinzugefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="1ac59-191">Select the **Search** box in the **Add to a team** section and select a team to add the sample app to.</span></span> <span data-ttu-id="1ac59-192">In der Regel können Sie ein spezielles Team für Tests einrichten.</span><span class="sxs-lookup"><span data-stu-id="1ac59-192">Usually, you can set up a special team for testing.</span></span>

<span data-ttu-id="1ac59-193">Klicken Sie **unten** im Dialogfeld auf die Schaltfläche "Installieren".</span><span class="sxs-lookup"><span data-stu-id="1ac59-193">Select the **Install** button at the bottom of the dialog.</span></span>

<span data-ttu-id="1ac59-194">Damit wird der App Studio-Teil dieser exemplarischen Vorgehensweise abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="1ac59-194">This finishes the App Studio portion of this walkthrough.</span></span> <span data-ttu-id="1ac59-195">Nun sollte Ihre App in Teams ausgeführt werden, der Bot und die Messagingerweiterung funktionieren jedoch erst, wenn Sie die Umgebung für gehostete Anwendungen aktualisieren, um zu erfahren, was die App-IDs und Kennwörter sind.</span><span class="sxs-lookup"><span data-stu-id="1ac59-195">You should now see your app running in Teams, however, the bot and the messaging extension will not work until you update the hosted applications environment to know what the App IDs and passwords are.</span></span>

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
