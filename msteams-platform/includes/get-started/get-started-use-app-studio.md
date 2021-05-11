### <a name="use-app-studio-to-update-the-app-package"></a><span data-ttu-id="82641-101">Aktualisieren des App-Pakets mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="82641-101">Use App Studio to update the app package</span></span>

<span data-ttu-id="82641-102">App Studio ist eine Teams App, die Sie über den Teams installieren können.</span><span class="sxs-lookup"><span data-stu-id="82641-102">App Studio is a Teams app that you can install from the Teams store.</span></span> <span data-ttu-id="82641-103">Es vereinfacht die Erstellung und Registrierung einer App.</span><span class="sxs-lookup"><span data-stu-id="82641-103">It simplifies the creation and registration of an app.</span></span>

<span data-ttu-id="82641-104">Führen Sie die folgenden Schritte aus, um das App-Paket zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="82641-104">Complete the following steps to update the app package:</span></span>

1. <span data-ttu-id="82641-105">Wenn Sie App Studio in Teams installieren möchten, wählen Sie unten auf der linken Leiste das Symbol **Apps** aus, und suchen Sie nach **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="82641-105">To install App Studio in Teams, select the **Apps** icon at the bottom of the left-hand bar, and search for **App Studio**.</span></span>

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

2. <span data-ttu-id="82641-106">Wählen Sie die **Kachel App Studio** aus, und wählen Sie Installieren **aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-106">Select the **App Studio** tile and choose **Install**.</span></span> <span data-ttu-id="82641-107">Das App Studio ist installiert.</span><span class="sxs-lookup"><span data-stu-id="82641-107">The App Studio is installed.</span></span>

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

3. <span data-ttu-id="82641-108">Um das App-Paket für Ihre Teams zu erstellen, wählen Sie in App Studio die **Registerkarte Manifesteditor** **aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-108">To create the app package for your Teams app, select the **Manifest editor** tab in **App Studio**.</span></span>

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

<span data-ttu-id="82641-109">Das Beispiel enthält ein eigenes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="82641-109">The sample comes with its own manifest and is designed to build an app package when the project is built.</span></span> <span data-ttu-id="82641-110">In .NET erfolgt dies in Visual Studio und Node.js erfolgt dies durch Eingabe an der Befehlszeile `gulp` im Stammverzeichnis des Projekts.</span><span class="sxs-lookup"><span data-stu-id="82641-110">On .NET this is done in Visual Studio and on Node.js this is done by typing `gulp` at the command line in the root directory of the project.</span></span>

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

<span data-ttu-id="82641-111">Der Name des generierten App-Pakets **isthelloworldapp.zip.**</span><span class="sxs-lookup"><span data-stu-id="82641-111">The name of the generated app package is **helloworldapp.zip**.</span></span> <span data-ttu-id="82641-112">Sie können nach dieser Datei suchen, wenn der Speicherort im verwendeten Tool nicht eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="82641-112">You can search for this file if the location is not clear in the tool you are using.</span></span>

4. <span data-ttu-id="82641-113">Wählen Sie zum Ändern dieses App-Pakets **im Manifest-Editor** die Option Vorhandene **App importieren aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-113">Now to modify this app package, select **Import an existing app** in the **Manifest editor**.</span></span>

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

5. <span data-ttu-id="82641-114">Wählen Sie die **Kachel Hello World** für Ihre neu importierte App aus.</span><span class="sxs-lookup"><span data-stu-id="82641-114">Select the **Hello World** tile for your newly imported app.</span></span>

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

<span data-ttu-id="82641-115">Die folgende Abbildung zeigt das importierte App-Paket in App Studio:</span><span class="sxs-lookup"><span data-stu-id="82641-115">The following image shows the imported app package in App Studio:</span></span>

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

<span data-ttu-id="82641-116">Auf der linken Seite des Manifest-Editors befindet sich eine Liste der Schritte.</span><span class="sxs-lookup"><span data-stu-id="82641-116">On the left-hand side of the Manifest editor there is a list of steps.</span></span> <span data-ttu-id="82641-117">Auf der rechten Seite befindet sich eine Liste der Eigenschaften, die für jeden Schritt ausgefüllt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="82641-117">On the right-hand side there is a list of properties that need to be filled in for each step.</span></span> <span data-ttu-id="82641-118">Wie Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="82641-118">As you started with a sample app, much of the information is already completed.</span></span> <span data-ttu-id="82641-119">Mit den nächsten Schritten können Sie die Eigenschaften der Hello World-App aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="82641-119">The next steps enable you to update the properties of the Hello World app.</span></span>

#### <a name="app-details"></a><span data-ttu-id="82641-120">App-Details</span><span class="sxs-lookup"><span data-stu-id="82641-120">App details</span></span>

<span data-ttu-id="82641-121">Wählen **Sie App-Details** unter **Details aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-121">Select **App details** under **Details**.</span></span> <span data-ttu-id="82641-122">Wählen Sie die **Schaltfläche Generieren** aus, um eine neue App-ID zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82641-122">Select the **Generate** button to create a new App ID.</span></span>

<span data-ttu-id="82641-123">Ihre neue App-ID ähnelt `2322041b-72bf-459d-b107-f4f335bc35bd` .</span><span class="sxs-lookup"><span data-stu-id="82641-123">Your new App ID is similar to `2322041b-72bf-459d-b107-f4f335bc35bd`.</span></span>

<span data-ttu-id="82641-124">Gehen Sie im rechten Bereich durch die App-Details, einschließlich **Entwicklerinformationen** und **Brandingdetails.**</span><span class="sxs-lookup"><span data-stu-id="82641-124">Go through the app details in the right-hand pane including **Developer information** and **Branding** details.</span></span> <span data-ttu-id="82641-125">Diese Details sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.</span><span class="sxs-lookup"><span data-stu-id="82641-125">These details are important if you are writing a new app for distribution.</span></span>

#### <a name="tabs"></a><span data-ttu-id="82641-126">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="82641-126">Tabs</span></span>

<span data-ttu-id="82641-127">Das Hinzufügen von Registerkarten zu einer Teams ist einfach.</span><span class="sxs-lookup"><span data-stu-id="82641-127">It is simple to add tabs to a Teams app.</span></span> <span data-ttu-id="82641-128">Die Beispiel-App unterstützt bereits mehrere Registerkarten, und Sie können sie aktivieren.</span><span class="sxs-lookup"><span data-stu-id="82641-128">The sample app already supports several tabs, and you can enable them.</span></span>

##### <a name="team-tab"></a><span data-ttu-id="82641-129">Registerkarte "Team"</span><span class="sxs-lookup"><span data-stu-id="82641-129">Team tab</span></span>

<span data-ttu-id="82641-130">Ihre App kann nur über eine Teamregisterkarte verfügen.</span><span class="sxs-lookup"><span data-stu-id="82641-130">Your app can only have one Team tab.</span></span>

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

<span data-ttu-id="82641-131">In diesem Beispiel wird auf der Registerkarte Team die Konfigurationsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82641-131">In this sample, the Team tab is where your configuration page is displayed.</span></span> <span data-ttu-id="82641-132">Wählen Sie **das Symbol ...** der **Tab-Konfigurations-URL aus,** und wählen Sie **im** Dropdownmenü Bearbeiten aus.</span><span class="sxs-lookup"><span data-stu-id="82641-132">Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu.</span></span> <span data-ttu-id="82641-133">Ändern Sie die URL so, dass sie durch die URL ersetzt werden muss, die Sie `https://yourteamsapp.ngrok.io/configure` `yourteamsapp.ngrok.io` beim [Hosten Ihrer App verwendet haben.](#host-the-sample-app)</span><span class="sxs-lookup"><span data-stu-id="82641-133">Change the URL to `https://yourteamsapp.ngrok.io/configure` where `yourteamsapp.ngrok.io` must be replaced with the URL that you used when [hosting your app](#host-the-sample-app).</span></span>

##### <a name="personal-tabs"></a><span data-ttu-id="82641-134">Persönliche Registerkarten</span><span class="sxs-lookup"><span data-stu-id="82641-134">Personal tabs</span></span>

<span data-ttu-id="82641-135">Ihre App kann über bis zu 16 Registerkarten verfügen, einschließlich der Registerkarte Team.</span><span class="sxs-lookup"><span data-stu-id="82641-135">Your app can have up to 16 tabs, including the Team tab.</span></span>

<span data-ttu-id="82641-136">Persönliche Registerkarten unterscheiden sich von der Registerkarte Team. **Hello Tab** ist bereits in der Liste der persönlichen Registerkarten mit einem Platzhalterwert `com.contoso.helloworld.hellotab` aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="82641-136">Personal tabs are different from the Team tab. **Hello Tab** is already listed in the personal tabs list with a placeholder value `com.contoso.helloworld.hellotab`.</span></span> <span data-ttu-id="82641-137">Wählen Sie **das Symbol ...** der **Tab-Konfigurations-URL aus,** und wählen Sie **im** Dropdownmenü Bearbeiten aus.</span><span class="sxs-lookup"><span data-stu-id="82641-137">Select the **...** symbol of the **Tab configuration url** and choose **Edit** from the drop-down menu.</span></span> <span data-ttu-id="82641-138">Das folgende Dialogfeld wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="82641-138">The following dialog box appears:</span></span>

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

<span data-ttu-id="82641-139">Aktualisieren Sie die folgenden Felder mit Ihrer App-URL:</span><span class="sxs-lookup"><span data-stu-id="82641-139">Update the following boxes with your app URL:</span></span>

- <span data-ttu-id="82641-140">Ändern des **Felds Inhalts-URL** in `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="82641-140">Change the **Content URL** box to `https://yourteamsapp.ngrok.io/hello`</span></span>
- <span data-ttu-id="82641-141">Ändern des **Felds Website-URL** in `https://yourteamsapp.ngrok.io/hello`</span><span class="sxs-lookup"><span data-stu-id="82641-141">Change the **Website URL** box to `https://yourteamsapp.ngrok.io/hello`</span></span>

<span data-ttu-id="82641-142">Ersetzen `yourteamsapp.ngrok.io` Sie durch die URL, die Sie beim Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="82641-142">Replace `yourteamsapp.ngrok.io` by the URL that you used when hosting your app.</span></span>

#### <a name="bots"></a><span data-ttu-id="82641-143">Bots</span><span class="sxs-lookup"><span data-stu-id="82641-143">Bots</span></span>

<span data-ttu-id="82641-144">Es ist einfach, die Bots-Funktionalität zu Ihrer App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82641-144">It is easy to add the bots functionality to your app.</span></span> <span data-ttu-id="82641-145">Die Hello World-Beispiel-App verfügt bereits über einen Bot als Teil des Beispiels, Sie müssen ihn jedoch bei Microsoft registrieren. </span><span class="sxs-lookup"><span data-stu-id="82641-145">The **Hello World** sample app already has a bot as part of the sample, but you must register it with Microsoft.</span></span>

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

<span data-ttu-id="82641-146">Der bot, der aus dem Beispiel importiert wurde, verfügt nicht über eine zugeordnete App-ID.</span><span class="sxs-lookup"><span data-stu-id="82641-146">The bot that was imported from the sample does not have an associated App ID.</span></span> <span data-ttu-id="82641-147">Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="82641-147">You must create a new bot so that App Studio can create a new App ID and register it with Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="82641-148">Die von App Studio für den Bot erstellte App-ID ist anders als die app-ID, die für die App erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="82641-148">The App ID created by App Studio for the bot is different from the App ID created for the app.</span></span> <span data-ttu-id="82641-149">Jeder Bot in einer App benötigt eine eigene App-ID.</span><span class="sxs-lookup"><span data-stu-id="82641-149">Each bot in an app requires its own App ID.</span></span>

<span data-ttu-id="82641-150">Führen Sie die folgenden Schritte aus, um Ihren Bot zu installieren:</span><span class="sxs-lookup"><span data-stu-id="82641-150">Complete the following steps to setup your bot:</span></span>

1. <span data-ttu-id="82641-151">Wählen **Sie neben** dem importierten Bot in der Botliste löschen aus.</span><span class="sxs-lookup"><span data-stu-id="82641-151">Select **Delete** next to the imported bot in the bot list.</span></span> <span data-ttu-id="82641-152">Jetzt sind keine Bots mehr zu sehen.</span><span class="sxs-lookup"><span data-stu-id="82641-152">Now there are no bots left to show.</span></span> 
2. <span data-ttu-id="82641-153">Wählen **Sie Setup** aus, um das Dialogfeld Bot **einrichten** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82641-153">Select **Setup** to display the **Set up a bot** dialog box.</span></span>

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

3. <span data-ttu-id="82641-154">Fügen Sie einen Botnamen **Contoso-Bot hinzu,** und aktivieren Sie alle drei Kontrollkästchen unter **Bereich**.</span><span class="sxs-lookup"><span data-stu-id="82641-154">Add a bot name **Contoso bot** and select all three check boxes under **Scope**.</span></span>
4. <span data-ttu-id="82641-155">Wählen **Sie Speichern** aus, um das Dialogfeld zu beenden.</span><span class="sxs-lookup"><span data-stu-id="82641-155">Choose **Save** to exit the dialog box.</span></span> <span data-ttu-id="82641-156">App Studio registriert Ihren Bot bei Microsoft und zeigt Den neuen Bot in der Botliste an.</span><span class="sxs-lookup"><span data-stu-id="82641-156">App Studio registers your bot with Microsoft and displays your new bot in the bot list.</span></span> 
5. <span data-ttu-id="82641-157">Öffnen Sie nun eine Textdatei im Editor, und kopieren Und fügen Sie Ihre neue Bot-ID ein.</span><span class="sxs-lookup"><span data-stu-id="82641-157">Now open a text file in notepad and copy and paste your new bot ID into it.</span></span>
6. <span data-ttu-id="82641-158">Klicken **Sie auf Neues Kennwort generieren,** und notieren Sie sich das Kennwort in derselben Textdatei, in der Sie Ihre Bot-App-ID notiert haben.</span><span class="sxs-lookup"><span data-stu-id="82641-158">Click **Generate New Password**, and note the password in the same text file you noted your bot App ID.</span></span>
7. <span data-ttu-id="82641-159">Aktualisieren Sie die **Bot-Endpunktadresse** auf , und ersetzen Sie durch die URL, die Sie beim `https://yourteamsapp.ngrok.io/api/messages` `yourteamsapp.ngrok.io` Hosten Ihrer App verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="82641-159">Update the **Bot endpoint address** to `https://yourteamsapp.ngrok.io/api/messages`, and replace `yourteamsapp.ngrok.io` with the URL that you used when hosting your app.</span></span>
8. <span data-ttu-id="82641-160">Speichern Sie nun Ihre Textdatei, da Sie die Informationen aus der Datei zu Ihrer gehosteten App hinzufügen müssen, um eine sichere Kommunikation mit Ihrem Bot zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="82641-160">Now save your text file as you must add the information from the file to your hosted app to allow secure communication with your bot.</span></span>

#### <a name="messaging-extensions"></a><span data-ttu-id="82641-161">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="82641-161">Messaging extensions</span></span>

<span data-ttu-id="82641-162">Mit Messagingerweiterungen können Benutzer nach Informationen von Ihrem Dienst fragen und diese Informationen veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="82641-162">Messaging extensions let users ask for information from your service and post that information.</span></span> <span data-ttu-id="82641-163">Die Informationen werden in Form von Karten in der Kanal unterhaltung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="82641-163">The information is posted in the form of cards into the channel conversation.</span></span> <span data-ttu-id="82641-164">Messagingerweiterungen werden am unteren Rand des Verfassenfelds angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82641-164">Messaging extensions appear at the bottom of the compose box.</span></span>

<span data-ttu-id="82641-165">Führen Sie die folgenden Schritte aus, um Ihre Messagingerweiterung zu installieren:</span><span class="sxs-lookup"><span data-stu-id="82641-165">Complete the following steps to setup your messaging extension:</span></span>

1. <span data-ttu-id="82641-166">Wählen **Sie Messagingerweiterungen** **unter Funktionen** im linken Bereich von App Studio aus, um die Messagingerweiterung zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="82641-166">Select **Messaging extensions** under **Capabilities** in the left-hand pane of App Studio to configure the messaging extension.</span></span>

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

<span data-ttu-id="82641-167">Die Beispiel-Messagingerweiterung ist im Bereich **Messagingerweiterungen** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="82641-167">The sample messaging extension is listed in the **Messaging Extensions** pane.</span></span>

2. <span data-ttu-id="82641-168">Wählen **Sie Löschen** aus, um die Messagingerweiterung zu entfernen, wählen Sie **Einrichten** aus, und führen Sie die gleichen Schritte aus, die für [Bots verwendet werden.](#bots)</span><span class="sxs-lookup"><span data-stu-id="82641-168">Select **Delete** to remove the messaging extension, select **Set up**, and follow the same steps used for [bots](#bots).</span></span> <span data-ttu-id="82641-169">Das **Dialogfeld Messagingerweiterung** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82641-169">The **Messaging Extension** dialog box is displayed.</span></span>
3. <span data-ttu-id="82641-170">Wählen Sie die **Registerkarte Vorhandenen Bot verwenden** aus, und wählen Sie aus einem meiner **vorhandenen Bots aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-170">Select the **Use existing bot** tab and **Select from one of my existing bots**.</span></span>
4. <span data-ttu-id="82641-171">Wählen Sie den von Ihnen erstellten Bot im Dropdownmenü aus.</span><span class="sxs-lookup"><span data-stu-id="82641-171">Select the bot you created from the drop-down menu.</span></span> <span data-ttu-id="82641-172">Fügen Sie einen **Botnamen hinzu,** und wählen **Sie Speichern aus,** um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="82641-172">Add a **Bot name** and select **Save** to close the dialog box.</span></span>
5. <span data-ttu-id="82641-173">Wählen Sie **im Abschnitt Befehl** die Option Hinzufügen **aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-173">Under the **Command** section, select **Add**.</span></span> <span data-ttu-id="82641-174">Wenn Sie einen suchbasierten Befehl hinzufügen möchten, wählen Sie die Option Benutzern erlauben, Ihren Dienst nach Informationen zu fragen, und fügen Sie diesen **in eine Nachricht** ein.</span><span class="sxs-lookup"><span data-stu-id="82641-174">To add a search-based command, select the **Allow users to query your service for information and insert that into a message** option.</span></span>
6. <span data-ttu-id="82641-175">Geben Sie im Dialogfeld **Neuer Befehl** die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="82641-175">In the **New command** dialog box, enter the following values:</span></span>

<span data-ttu-id="82641-176">Unter **Neuer Befehl**:</span><span class="sxs-lookup"><span data-stu-id="82641-176">Under **New command**:</span></span>

- <span data-ttu-id="82641-177">**Befehls-ID**: Geben Sie zufälligen Text ein.</span><span class="sxs-lookup"><span data-stu-id="82641-177">**Command ID**: Enter random text</span></span>
- <span data-ttu-id="82641-178">**Titel**: Geben Sie zufälligen Titel ein.</span><span class="sxs-lookup"><span data-stu-id="82641-178">**Title**: Enter random title</span></span>
- <span data-ttu-id="82641-179">**Beschreibung**: Geben Sie eine zufällige Beschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="82641-179">**Description**: Enter random description</span></span>

<span data-ttu-id="82641-180">Unter **Parameter**:</span><span class="sxs-lookup"><span data-stu-id="82641-180">Under **Parameter**:</span></span>

- <span data-ttu-id="82641-181">**Name**: Geben Sie den Parameternamen ein.</span><span class="sxs-lookup"><span data-stu-id="82641-181">**Name**: Enter the parameter name</span></span>
- <span data-ttu-id="82641-182">**Titel**: Geben Sie den Kartentitel ein.</span><span class="sxs-lookup"><span data-stu-id="82641-182">**Title**: Enter the card title</span></span>
- <span data-ttu-id="82641-183">**Beschreibung**: Geben Sie die Kartenbeschreibung ein.</span><span class="sxs-lookup"><span data-stu-id="82641-183">**Description**: Enter card description</span></span>

7. <span data-ttu-id="82641-184">Nachdem Sie die Informationen eingeben, wählen **Sie Speichern** aus, um das Dialogfeld zu schließen.</span><span class="sxs-lookup"><span data-stu-id="82641-184">After you enter the information, select **Save** to close the dialog box.</span></span>

#### <a name="register-your-app-in-teams"></a><span data-ttu-id="82641-185">Registrieren Sie Ihre App in Teams</span><span class="sxs-lookup"><span data-stu-id="82641-185">Register your app in Teams</span></span>

<span data-ttu-id="82641-186">Führen Sie nach der Eingabe der Details Ihrer App die folgenden Schritte aus, um Ihre App in Teams:</span><span class="sxs-lookup"><span data-stu-id="82641-186">After entering the details of your app, complete the following steps to register your app in Teams:</span></span>

1. <span data-ttu-id="82641-187">Verwenden **Sie Testen und Verteilen** von App Studio, um Ihre App in einem Teams.</span><span class="sxs-lookup"><span data-stu-id="82641-187">Use **Test and distribute** of App Studio to install your app in Teams.</span></span> 
2. <span data-ttu-id="82641-188">Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="82641-188">Update your hosted application with the App ID and password for your bot.</span></span> <span data-ttu-id="82641-189">Verwenden Sie für die Beispiel-App die gleiche App-ID und dasselbe Kennwort für Bot- und Messagingerweiterung.</span><span class="sxs-lookup"><span data-stu-id="82641-189">For the sample app, use the same App ID and password for both bot and messaging extension.</span></span> 
3. <span data-ttu-id="82641-190">Wählen **Sie Testen und Verteilen**  unter **Fertig** stellen im linken Bereich von App Studio aus.</span><span class="sxs-lookup"><span data-stu-id="82641-190">Select **Test and distribute**  under **Finish** in the left-hand pane of App Studio.</span></span>

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

4. <span data-ttu-id="82641-191">Um Ihre App in Teams hochzuladen, wählen Sie unter Testen und Verteilen **die** Schaltfläche **Installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="82641-191">To upload your app to Teams, select the **Install** button under **Test and Distribute**.</span></span>

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

5. <span data-ttu-id="82641-192">Wählen Sie **im Abschnitt** **Zu** einem Team hinzufügen das Feld Suchen aus, und wählen Sie ein Team aus, um die Beispiel-App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="82641-192">Select the **Search** box in the **Add to a team** section and select a team to add the sample app.</span></span> <span data-ttu-id="82641-193">Sie können ein spezielles Team für Tests einrichten.</span><span class="sxs-lookup"><span data-stu-id="82641-193">You can set up a special team for testing.</span></span>
6. <span data-ttu-id="82641-194">Wählen Sie **unten** im Dialogfeld die Schaltfläche Installieren aus.</span><span class="sxs-lookup"><span data-stu-id="82641-194">Select the **Install** button at the bottom of the dialog box.</span></span>

<span data-ttu-id="82641-195">Ihre App ist jetzt in Teams.</span><span class="sxs-lookup"><span data-stu-id="82641-195">Your app is now available in Teams.</span></span> <span data-ttu-id="82641-196">Der Bot und die Messagingerweiterung funktionieren jedoch erst, wenn Sie die gehostete Anwendungsumgebung mit den App-IDs und Kennwörtern aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="82641-196">However, the bot and the messaging extension will not work until you update the hosted applications environment with the App IDs and passwords.</span></span>

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
