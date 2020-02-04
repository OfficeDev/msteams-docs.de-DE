### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="78840-101">Aktualisieren des App-Pakets mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="78840-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="78840-102">App Studio ist eine Teams-APP, die Sie im Microsoft Teams Store installieren können.</span><span class="sxs-lookup"><span data-stu-id="78840-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="78840-103">Es vereinfacht das Erstellen und Registrieren einer App.</span><span class="sxs-lookup"><span data-stu-id="78840-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="78840-104">Wenn Sie App Studio in Microsoft Teams installieren möchten, klicken Sie auf das App Store-Symbol unten in der linken Leiste, und suchen Sie nach App Studio.</span><span class="sxs-lookup"><span data-stu-id="78840-104">To install App Studio in Teams, click on the app store icon at the bottom of the left hand bar, and search for App Studio.</span></span>

<img  width="450px" title="Suchen von App Studio im Store" src="~/assets/images/get-started/app-studio-store.png"/>

<span data-ttu-id="78840-106">Wenn Sie die Kachel für App Studio gefunden haben, klicken Sie darauf, und wählen Sie im Dialogfeld *Installieren* aus, das eingeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="78840-106">Once you find the tile for App Studio, click on it and choose *install* in the dialog that pops up.</span></span>

<img  width="450px" title="Installieren von App Studio" src="~/assets/images/get-started/app-studio-install.png"/>

<span data-ttu-id="78840-108">Sobald App Studio installiert ist, klicken Sie auf die Registerkarte Manifest-Editor, um mit der Erstellung des App-Pakets für Ihre Teams-APP zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="78840-108">Once App Studio is installed click on the Manifest editor tab to begin creating the app package for your Teams app.</span></span>

<img  width="450px" title="App Studio" src="~/assets/images/get-started/app-studio.png"/>

<span data-ttu-id="78840-110">Das Beispiel enthält ein eigenes vordefiniertes Manifest und wurde entwickelt, um ein App-Paket zu erstellen, wenn das Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="78840-110">The sample comes with its own pre-made manifest, and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="78840-111">In .net erfolgt dies in Visual Studio und auf Node js erfolgt dies durch Eingabe `gulp` an der Befehlszeile im Stammverzeichnis des Projekts.</span><span class="sxs-lookup"><span data-stu-id="78840-111">On .NET this is done in Visual Studio, and on Node JS this is done by typing `gulp` at the command line in the root directory of the project.</span></span>

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

<span data-ttu-id="78840-112">Der Name des generierten App-Pakets lautet *helloworldapp. zip*.</span><span class="sxs-lookup"><span data-stu-id="78840-112">The name of the generated app package is *helloworldapp.zip*.</span></span> <span data-ttu-id="78840-113">Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="78840-113">You can search for this file if the location is not clear in the tool you are using.</span></span>

<span data-ttu-id="78840-114">Im nächsten Teil dieser exemplarischen Vorgehensweise ändern Sie dieses app-Paket, indem Sie die Kachel *Importieren einer vorhandenen APP* im Manifest-Editor auswählen.</span><span class="sxs-lookup"><span data-stu-id="78840-114">In the next part of this walkthrough you are going to modify this app package by selecting the *Import an existing app* tile in the Manifest Editor.</span></span>

<img  width="450px" title="Importieren einer APP" src="~/assets/images/get-started/app-studio-import.png"/>

<span data-ttu-id="78840-116">Wenn das App-Paket importiert wurde, sollte App Studio wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="78840-116">Once the app package has been imported App Studio should look like this:</span></span>

<img  width="450px" title="Importieren einer APP" src="~/assets/images/get-started/app-studio-imported-app.png"/>

<span data-ttu-id="78840-118">Klicken Sie auf die Kachel für Ihre neu importierte APP, *Hello World*.</span><span class="sxs-lookup"><span data-stu-id="78840-118">Click on the tile for your newly imported app, *Hello World*.</span></span>

<img  width="450px" title="Importieren einer APP" src="~/assets/images/get-started/app-studio-manifest-editor.png"/>

<span data-ttu-id="78840-120">Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und rechts eine Liste von Eigenschaften, die für jeden dieser Schritte ausgefüllt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="78840-120">There is a list of steps in the left-hand side of the Manifest editor, and on the right a list of properties that need to be filled in for each of those steps.</span></span> <span data-ttu-id="78840-121">Da Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits ausgefüllt. Die nächsten Schritte führen Sie durch die Änderung der Teile, die noch aktualisiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="78840-121">Since you started with a sample app, much of the information is already filled out. The next steps will walk you through changing the parts that still need to be updated.</span></span>

#### <a name="app-details"></a><span data-ttu-id="78840-122">App-Details</span><span class="sxs-lookup"><span data-stu-id="78840-122">App details</span></span>

<span data-ttu-id="78840-123">Klicken Sie unter *Details*auf den Eintrag *App-Details* .</span><span class="sxs-lookup"><span data-stu-id="78840-123">Click on the *App details* entry under *Details*.</span></span> <span data-ttu-id="78840-124">Klicken Sie auf die Schaltfläche *generieren* , um eine neue APP-ID zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="78840-124">Click the *Generate* button to create a new app id.</span></span>

<span data-ttu-id="78840-125">Die neue APP-ID sollte etwa wie folgt `2322041b-72bf-459d-b107-f4f335bc35bd`aussehen:.</span><span class="sxs-lookup"><span data-stu-id="78840-125">Your new app id should look something like: `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="78840-126">Sehen Sie sich die restlichen App-Details im rechten Bereich an, und machen Sie sich mit einigen Einträgen wie *Entwickler Informationen* und *Branding*vertraut.</span><span class="sxs-lookup"><span data-stu-id="78840-126">Look through the rest of the App details in the right hand pane, and familiarize yourself with some of the entries such as *Developer information* and *Branding*.</span></span> <span data-ttu-id="78840-127">Diese Abschnitte sind wichtig, wenn Sie eine neue APP für die Verteilung schreiben.</span><span class="sxs-lookup"><span data-stu-id="78840-127">These sections are important if you are writing a new app for distribution.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="78840-128">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="78840-128">Capabilities: Tabs</span></span>

<span data-ttu-id="78840-129">Registerkarten gehören zu den einfachsten Elementen, die einer Teams-app hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="78840-129">Tabs are among the simplest elements to add to a Teams app.</span></span> <span data-ttu-id="78840-130">Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können Sie wie folgt aktivieren.</span><span class="sxs-lookup"><span data-stu-id="78840-130">The sample app already supports several tabs, and you can enable them as follows.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="78840-131">Registerkarte "Team"</span><span class="sxs-lookup"><span data-stu-id="78840-131">Team tab</span></span>

<span data-ttu-id="78840-132">Ihre APP kann nur eine Team Registerkarte haben.</span><span class="sxs-lookup"><span data-stu-id="78840-132">Your app can only have one Team tab.</span></span>

<img  width="450px" title="Hinzufügen einer Registerkarte "Teams"" src="~/assets/images/get-started/app-studio-manifest-editor-tabs.png"/>

<span data-ttu-id="78840-134">In diesem Beispiel wird auf der Registerkarte "Team" die Konfigurationsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78840-134">In this sample, the Team tab is where your configuration page goes.</span></span> <span data-ttu-id="78840-135">Klicken Sie am Ende des Eintrags auf das Symbol *...* , und wählen Sie im Dropdownmenü *Bearbeiten* aus.</span><span class="sxs-lookup"><span data-stu-id="78840-135">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="78840-136">Ändern Sie die URL `https://yourteamsapp.ngrok.io/configure` dahin `yourteamsapp.ngrok.io` , wo Sie durch die URL ersetzt werden soll, die Sie beim Hosten Ihrer APP oben verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="78840-136">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="78840-137">Persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="78840-137">Personal tabs</span></span>

<span data-ttu-id="78840-138">Ihre APP kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte Team.</span><span class="sxs-lookup"><span data-stu-id="78840-138">Your app can have up to 16 tabs, including the team tab.</span></span>

<span data-ttu-id="78840-139">Persönliche Registerkarten werden auf der Registerkarte Team unterschiedlich dargestellt. Die *Registerkarte "Hello"* sollte bereits in der Liste "persönliche Registerkarten" angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="78840-139">Personal tabs are represented differently from the team tab. You should see *Hello Tab* already listed in the personal tabs list.</span></span> <span data-ttu-id="78840-140">Im Moment verfügt er über einen Platzhalter `com.contoso.helloworld.hellotab`Wert.</span><span class="sxs-lookup"><span data-stu-id="78840-140">At the moment it has a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="78840-141">Klicken Sie am Ende des Eintrags auf das Symbol *...* , und wählen Sie im Dropdownmenü *Bearbeiten* aus.</span><span class="sxs-lookup"><span data-stu-id="78840-141">Click on the *...* symbol at the end of the entry and choose *Edit* from the drop-down.</span></span> <span data-ttu-id="78840-142">Das folgende Dialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78840-142">The following dialog will appear.</span></span>

<img  width="450px" title="Hinzufügen eines persönlichen Registerkarten Dialogfelds" src="~/assets/images/get-started/app-studio-manifest-editor-p-tabs-dialog.png"/>

<span data-ttu-id="78840-144">Es gibt zwei Felder, die Sie mit ihrer App-URL aktualisieren müssen.</span><span class="sxs-lookup"><span data-stu-id="78840-144">There are two fields that you need to update with your app URL.</span></span>

- <span data-ttu-id="78840-145">Ändern der Inhalts-URL in`https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="78840-145">Change Content URL to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="78840-146">Website-URL ändern in`https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="78840-146">Change Website URL to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="78840-147">Wo `yourteamsapp.ngrok.io` sollte durch die URL ersetzt werden, die Sie beim Hosten Ihrer APP oben verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="78840-147">Where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="78840-148">Bots</span><span class="sxs-lookup"><span data-stu-id="78840-148">Bots</span></span>

<span data-ttu-id="78840-149">Bots sind die gängigste Methode zum Hinzufügen von Funktionen zu Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="78840-149">Bots are the most common way to add functionality to your app.</span></span> <span data-ttu-id="78840-150">Das Beispiel "Hello World" verfügt bereits über einen bot als Teil des Beispiels, wurde aber noch nicht bei Microsoft registriert.</span><span class="sxs-lookup"><span data-stu-id="78840-150">The hello world sample already has a bot as part of the sample, but it has not been registered with Microsoft yet.</span></span>

<img  width="450px" title="Hinzufügen eines bot" src="~/assets/images/get-started/app-studio-manifest-editor-bots.png"/>

<span data-ttu-id="78840-152">Dem bot, der aus dem Beispiel importiert wurde, ist noch keine APP-ID zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="78840-152">The bot that was imported from the sample does not have an App ID associated with it yet.</span></span> <span data-ttu-id="78840-153">Sie müssen einen neuen bot erstellen, damit App Studio eine neue APP-ID erstellen und bei Microsoft registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="78840-153">You will have to create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span> <span data-ttu-id="78840-154">Beachten Sie, dass dies die APP-ID für den Bot ist, die sich von der APP-ID unterscheidet, die wir in einem früheren Schritt für die App erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="78840-154">Note that this is the App ID for the bot, which is different from the App ID that we created for the app in a earlier step.</span></span> <span data-ttu-id="78840-155">Jeder bot in einer APP benötigt eine eigene APP-ID.</span><span class="sxs-lookup"><span data-stu-id="78840-155">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="78840-156">Klicken Sie in der Liste bot neben dem *importierten bot* auf die Schaltfläche *Löschen* .</span><span class="sxs-lookup"><span data-stu-id="78840-156">Click the *delete* button next to the *Imported bot* in the bot list.</span></span>

<span data-ttu-id="78840-157">Jetzt sind keine Bots mehr verfügbar, die angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="78840-157">Now there are no bots left to show.</span></span> <span data-ttu-id="78840-158">Klicken Sie auf *Setup*.</span><span class="sxs-lookup"><span data-stu-id="78840-158">Click *Setup*.</span></span> <span data-ttu-id="78840-159">Dadurch wird das Dialogfeld " *bot einrichten* " angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78840-159">This will display the *Set up a bot* dialog.</span></span>

<img  width="450px" title="Hinzufügen eines bot-Dialogfelds" src="~/assets/images/get-started/app-studio-manifest-editor-bots-setup-dialog.png"/>

<span data-ttu-id="78840-161">Fügen Sie einen bot-Namen `Contoso bot`wie ein, und klicken Sie auf die Schaltflächen unter *Bereich*.</span><span class="sxs-lookup"><span data-stu-id="78840-161">Add a bot name such as `Contoso bot`, and click both the buttons under *scope*.</span></span>

<span data-ttu-id="78840-162">Wählen Sie *Create bot* aus, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="78840-162">Choose *Create bot* to exit the dialog.</span></span> <span data-ttu-id="78840-163">App Studio wird einen Moment Zeit damit verbringen, ihren bot bei Microsoft zu registrieren, und sollte dann Ihren neuen bot in der bot-Liste anzeigen.</span><span class="sxs-lookup"><span data-stu-id="78840-163">App Studio will spend a moment registering your bot with Microsoft, and then should display your new bot in the bot list.</span></span> <span data-ttu-id="78840-164">Jetzt wäre ein guter Zeitpunkt, eine Textdatei im Editor zu öffnen und ihre neue bot-ID zu kopieren und in diese einzufügen.</span><span class="sxs-lookup"><span data-stu-id="78840-164">Now would be a good time to open a text file in notepad and copy and paste your new bot id into it.</span></span> <span data-ttu-id="78840-165">Sie benötigen die ID später.</span><span class="sxs-lookup"><span data-stu-id="78840-165">You will need this id later.</span></span>

<span data-ttu-id="78840-166">Klicken Sie auf *Neues Kennwort generieren*, und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre bot-APP-ID notiert haben.</span><span class="sxs-lookup"><span data-stu-id="78840-166">Click *Generate New Password*, and make a note of the password in the same text file you noted your Bot app ID in.</span></span> <span data-ttu-id="78840-167">Dies ist das einzige Mal, wenn Ihr Kennwort angezeigt wird, deshalb sollten Sie dies jetzt tun.</span><span class="sxs-lookup"><span data-stu-id="78840-167">This is the only time your password will be shown, so be sure to do this now.</span></span>

<span data-ttu-id="78840-168">Aktualisieren Sie die *bot-Endpunktadresse* auf `https://yourteamsapp.ngrok.io/api/messages`, wobei `yourteamsapp.ngrok.io` die URL ersetzt werden soll, die Sie beim Hosten Ihrer APP oben verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="78840-168">Update the *Bot endpoint address* to `https://yourteamsapp.ngrok.io/api/messages`, where `yourteamsapp.ngrok.io` should be replaced by the URL that you used above when hosting your app.</span></span>

<span data-ttu-id="78840-169">Jetzt wäre ein guter Zeitpunkt, um Ihre Textdatei zu speichern, wenn Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="78840-169">Now would be a good time to save your text file if you have not done so already.</span></span> <span data-ttu-id="78840-170">Sie werden diese Informationen später in dieser exemplarischen Vorgehensweise zu ihrer gehosteten app hinzufügen, um eine sichere Kommunikation mit Ihrem bot zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="78840-170">You will add this information to your hosted app later in this walkthrough, which will allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="78840-171">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="78840-171">Messaging extensions</span></span>

<span data-ttu-id="78840-172">Mithilfe von Messaging Erweiterungen können Benutzer nach Informationen von Ihrem Dienst Fragen und diese Informationen in Form von Karten direkt in die Kanal Unterhaltung Posten.</span><span class="sxs-lookup"><span data-stu-id="78840-172">Messaging extensions let users ask for information from your service and post that information, in the form of cards, right into the channel conversation.</span></span> <span data-ttu-id="78840-173">Messaging Erweiterungen werden am unteren Rand des Felds verfassen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78840-173">Messaging extensions appear along the bottom of the compose box.</span></span>

<span data-ttu-id="78840-174">Klicken Sie unter *Funktionen* in der linken Spalte von App Studio auf *Messaging Erweiterungen* , um mit der Konfiguration der Messaging Erweiterung zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="78840-174">Click on *Messaging extensions* under *Capabilities* in the left hand column of App Studio to begin configuring the messaging extension.</span></span>

<img  width="450px" title="Hinzufügen einer Messaging Erweiterung" src="~/assets/images/get-started/app-studio-manifest-editor-mess-ext.png"/>

<span data-ttu-id="78840-176">Die Beispiel-Messaging-Erweiterung wird im rechten Bereich unter *Messaging Extensions*aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="78840-176">The sample messaging extension is listed in the right hand pane under *Messaging Extensions*.</span></span> <span data-ttu-id="78840-177">Klicken Sie erneut auf *Löschen* , um diesen Eintrag zu entfernen, und klicken Sie dann auf die Schaltfläche *Einrichten* , indem Sie die gleichen Schritte ausführen, die Sie für Bots befolgt haben.</span><span class="sxs-lookup"><span data-stu-id="78840-177">Click *Delete* again to remove this entry, and then click the *Set up* button following the same steps as you followed for bots.</span></span> <span data-ttu-id="78840-178">Dadurch wird das Dialogfeld *Messaging Erweiterung* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78840-178">This will display the *Messaging Extension* dialog.</span></span>

<span data-ttu-id="78840-179">Wählen Sie die Registerkarte *vorhandenen bot verwenden* aus, und *Wählen Sie dann eines meiner vorhandenen Bots aus*.</span><span class="sxs-lookup"><span data-stu-id="78840-179">Select the *Use existing bot* tab, then *Select from one of my existing bots*.</span></span> <span data-ttu-id="78840-180">Wählen Sie im Dropdownmenü den bot aus, den Sie im obigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="78840-180">In the drop-down menu, select the bot you created in the section above.</span></span> <span data-ttu-id="78840-181">Fügen Sie einen *bot-Namen* hinzu, und klicken Sie auf *Speichern* , um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="78840-181">Add a *Bot name* and click *Save* to close the dialog.</span></span>

<span data-ttu-id="78840-182">Klicken Sie im Abschnitt *Command* auf *Hinzufügen*.</span><span class="sxs-lookup"><span data-stu-id="78840-182">Under the *Command* section, click *Add*.</span></span> <span data-ttu-id="78840-183">Wir fügen einen suchbasierten Befehl hinzu, wählen Sie also die Option *Benutzer können Ihren Dienst Abfragen* ... aus.</span><span class="sxs-lookup"><span data-stu-id="78840-183">We're adding a search-based command, so choose the *Allow users to query your service...* option.</span></span>

<span data-ttu-id="78840-184">Geben Sie im Dialogfeld *neuer Befehl* die folgenden Werte ein.</span><span class="sxs-lookup"><span data-stu-id="78840-184">In the *New command* dialog enter the following values.</span></span>

<span data-ttu-id="78840-185">Unter *neuer Befehl*:</span><span class="sxs-lookup"><span data-stu-id="78840-185">Under *New command*:</span></span>

- <span data-ttu-id="78840-186">*Befehls-ID* = getRandomText</span><span class="sxs-lookup"><span data-stu-id="78840-186">*Command ID*  = getRandomText</span></span>
- <span data-ttu-id="78840-187">*Title* = Abrufen von zufälligen Texten zum Spaß</span><span class="sxs-lookup"><span data-stu-id="78840-187">*Title*       = Get some random text for fun</span></span>
- <span data-ttu-id="78840-188">*Description* = ruft einige zufällige Text und Bilder</span><span class="sxs-lookup"><span data-stu-id="78840-188">*Description* = Gets some random text and images</span></span>

<span data-ttu-id="78840-189">Unter *Parameter*:</span><span class="sxs-lookup"><span data-stu-id="78840-189">Under *Parameter*:</span></span>

- <span data-ttu-id="78840-190">*Name* = cardTitle</span><span class="sxs-lookup"><span data-stu-id="78840-190">*Name*        = cardTitle</span></span>
- <span data-ttu-id="78840-191">*Title* = Kartentitel</span><span class="sxs-lookup"><span data-stu-id="78840-191">*Title*       = Card title</span></span>
- <span data-ttu-id="78840-192">*Description* = zu verwendender Kartentitel</span><span class="sxs-lookup"><span data-stu-id="78840-192">*Description* = Card title to use</span></span>

<span data-ttu-id="78840-193">Nachdem Sie die Informationen eingegeben haben, klicken Sie auf *Speichern* , um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="78840-193">Once you're entered the information, click *Save* to close the dialog.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="78840-194">Registrieren Ihrer APP in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="78840-194">Register your app in Teams</span></span>

<span data-ttu-id="78840-195">Sie haben nun die Eingabe der Details Ihrer APP abgeschlossen, jedoch bleiben zwei Schritte.</span><span class="sxs-lookup"><span data-stu-id="78840-195">You have now completed entering the details of your app, but two steps remain.</span></span> <span data-ttu-id="78840-196">Zunächst müssen Sie den Abschnitt Test and Distribute von App Studio verwenden, um Ihre APP in Microsoft Teams zu installieren, und zweitens müssen Sie die gehostete Anwendung mit der APP-ID und dem Kennwort für Ihren bot aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="78840-196">First you must use the Test and Distribute section of App Studio to install your app in Teams, and second you must update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="78840-197">Beachten Sie, dass im Beispiel die gleiche APP-ID und das gleiche Kennwort für die bot-und die Messaging-Erweiterung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="78840-197">Remember that the sample expects to use the same App ID and password for both the bot and the messaging extension.</span></span>

<span data-ttu-id="78840-198">Klicken Sie in der linken Spalte von App Studio auf das Element *Testen und verteilen* unter *Fertig stellen* .</span><span class="sxs-lookup"><span data-stu-id="78840-198">Click on the *Test and distribute* item under *Finish* in the left hand column of App Studio.</span></span>

<img  width="450px" title="Testen der APP" src="~/assets/images/get-started/app-studio-manifest-editor-test.png"/>

<span data-ttu-id="78840-200">Um Ihre APP in Teams hochzuladen, klicken Sie unter *Test and Distribute*auf die Schaltfläche *Installieren* .</span><span class="sxs-lookup"><span data-stu-id="78840-200">In order to upload your app to Teams, click the *Install* button under *Test and Distribute*.</span></span>

<img  width="450px" title="Hinzufügen eines Dialogfelds für die Nachrichten Erweiterung" src="~/assets/images/get-started/app-studio-manifest-editor-test-dialog.png"/>

<span data-ttu-id="78840-202">Klicken Sie im Abschnitt *zu einem Team hinzufügen* auf das *Suchfeld* , und wählen Sie ein Team aus, dem Sie die Beispiel-app hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="78840-202">Click on the *Search* box in the *Add to a team* section and select a team to add the sample app to.</span></span> <span data-ttu-id="78840-203">Normalerweise möchten Sie ein spezielles Team für Tests einrichten.</span><span class="sxs-lookup"><span data-stu-id="78840-203">Usually you will want to set up a special team for testing.</span></span>

<span data-ttu-id="78840-204">Klicken Sie unten im Dialogfeld auf die Schaltfläche *Installieren* .</span><span class="sxs-lookup"><span data-stu-id="78840-204">Click the *Install* button at the bottom of the dialog.</span></span>

<span data-ttu-id="78840-205">Dadurch wird der APP Studio-Teil dieser exemplarischen Vorgehensweise abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="78840-205">This finishes the App Studio portion of this walkthrough.</span></span> <span data-ttu-id="78840-206">Ihre APP sollte jetzt in Microsoft Teams ausgeführt werden, die bot-und die Messaging-Erweiterung funktionieren jedoch erst, wenn Sie die Umgebung für gehostete Anwendungen so aktualisieren, dass Sie wissen, was die APP-IDs und Kennwörter sind.</span><span class="sxs-lookup"><span data-stu-id="78840-206">You should now see your app running in Teams, however the bot and the messaging extension will not work until you update the hosted applications environment to know what the App IDs and passwords are.</span></span>

<img  width="450px" title="Die fertige App" src="~/assets/images/get-started/app-studio-finished-app.png"/>