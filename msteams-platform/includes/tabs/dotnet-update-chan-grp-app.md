### <a name="_layoutcshtml"></a><span data-ttu-id="a1c3b-101">_Layout. cshtml</span><span class="sxs-lookup"><span data-stu-id="a1c3b-101">_Layout.cshtml</span></span>

<span data-ttu-id="a1c3b-102">Damit Ihre Registerkarte in Teams angezeigt wird, müssen Sie das **Microsoft Teams-JavaScript-Client-SDK** einschließen und nach dem Laden einer Seite einen Anruf hinzufügen `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="a1c3b-102">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="a1c3b-103">So kommunizieren Ihr Tab und der Microsoft Teams-Client:</span><span class="sxs-lookup"><span data-stu-id="a1c3b-103">This is how your tab and the Teams client communicate:</span></span>

- <span data-ttu-id="a1c3b-104">Navigieren Sie zum **freigegebenen** Ordner, öffnen Sie **_Layout. cshtml**, und fügen Sie dem-Tag Folgendes hinzu `<head>` :</span><span class="sxs-lookup"><span data-stu-id="a1c3b-104">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

>[!IMPORTANT]
><span data-ttu-id="a1c3b-105">Kopieren/fügen Sie die `<script src="...">` URLs nicht von dieser Seite ein, da Sie möglicherweise nicht die neueste Version darstellen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-105">Don't copy/paste the `<script src="...">` URLs from this page, as they may not represent the latest version.</span></span> <span data-ttu-id="a1c3b-106">Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu: [Microsoft Teams-JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).</span><span class="sxs-lookup"><span data-stu-id="a1c3b-106">To get the latest version of the SDK, always go to: [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js).</span></span>

### <a name="tabcshtml"></a><span data-ttu-id="a1c3b-107">Tab. cshtml</span><span class="sxs-lookup"><span data-stu-id="a1c3b-107">Tab.cshtml</span></span>

<span data-ttu-id="a1c3b-108">Öffnen Sie **Tab. cshtml** , und aktualisieren Sie die Embedded `<script>` wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a1c3b-108">Open **Tab.cshtml** and update the embedded `<script>` as follows:</span></span>

- <span data-ttu-id="a1c3b-109">Rufen Sie am oberen Rand des Skripts auf `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="a1c3b-109">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

- <span data-ttu-id="a1c3b-110">Aktualisieren `websiteUrl` Sie die-und- `contentUrl` Werte in jeder Funktion mit der HTTPS-ngrok-URL zu ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-110">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

<span data-ttu-id="a1c3b-111">Ihr Code sollte jetzt wie folgt aussehen, wenn **y8rCgT2b** durch ihre ngrok-URL ersetzt wird:</span><span class="sxs-lookup"><span data-stu-id="a1c3b-111">Your code should now look like the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

```javascript
    microsoftTeams.initialize();

    let saveGray = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                entityId: "grayIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }

    let saveRed = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                entityId: "redIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }
```

<span data-ttu-id="a1c3b-112">Stellen Sie sicher, dass die aktualisierte **Registerkarte. cshtml** gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-112">Make sure to save the updated **Tab.cshtml**.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="a1c3b-113">Erstellen und Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="a1c3b-113">Build and run your application</span></span>

- <span data-ttu-id="a1c3b-114">Drücken Sie in Visual Studio **F5**, oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-114">In Visual Studio press **F5**, or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="a1c3b-115">Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und zu ihrer Inhaltsseite über die ngrok-HTTPS-URL wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-115">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="a1c3b-116">Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diesen Schnellstart abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-116">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="a1c3b-117">Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um damit zu arbeiten, **halten Sie ngrok** auf dem laufenden.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-117">If you need to stop running your application in Visual Studio to work on it **keep ngrok running**.</span></span> <span data-ttu-id="a1c3b-118">Sie wird weiterhin überwacht und setzt die Weiterleitung der Anforderung Ihrer Anwendung fort, wenn Sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-118">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="a1c3b-119">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-119">If you have to restart the ngrok service it will return a new URL and you'll have to update your application with the new URL.</span></span>

## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="a1c3b-120">Hochladen der Registerkarte in Microsoft Teams mit App Studio</span><span class="sxs-lookup"><span data-stu-id="a1c3b-120">Upload your tab to Teams with App Studio</span></span>

>[!Note]
> <span data-ttu-id="a1c3b-121">Wir verwenden App Studio, um Ihre **manifest.jsauf** Datei zu bearbeiten und das abgeschlossene Paket in Microsoft Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-121">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="a1c3b-122">Sie können diemanifest.jsauch manuell **in** der Datei bearbeiten, wenn Sie dies bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-122">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="a1c3b-123">Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die **tab.zip** Datei zu erstellen, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-123">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="a1c3b-124">Öffnen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-124">Open the Microsoft Teams client.</span></span> <span data-ttu-id="a1c3b-125">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-125">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="a1c3b-126">Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-126">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="a1c3b-127">Wählen Sie die Kachel **Importieren einer vorhandenen APP** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-127">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="a1c3b-128">Der Name des App-Pakets lautet **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-128">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="a1c3b-129">Es sollte hier gefunden werden:</span><span class="sxs-lookup"><span data-stu-id="a1c3b-129">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- <span data-ttu-id="a1c3b-130">Laden Sie **tab.zip** in das App-Studio hoch.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-130">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="a1c3b-131">Aktualisieren des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="a1c3b-131">Update your app package with Manifest editor</span></span>

<span data-ttu-id="a1c3b-132">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration fertig stellen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-132">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="a1c3b-133">Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-133">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="a1c3b-134">Auf der linken Seite des Manifest-Editors finden Sie eine Liste mit Schritten und auf der rechten Seite eine Liste mit Eigenschaften, die für jeden dieser Schritte Werte enthalten müssen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-134">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="a1c3b-135">Viele der Informationen wurden von Ihrem *manifest.js* bereitgestellt, aber es gibt ein paar Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="a1c3b-135">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="a1c3b-136">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="a1c3b-136">Details: App details</span></span>

- <span data-ttu-id="a1c3b-137">Wählen Sie unter *Identifikation* \***generieren** _ aus, um die Platzhalter-ID durch die erforderliche GUID für die Registerkarte zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-137">Under *Identification* select \***Generate** _ to replace the placeholder id with the required GUID for your tab.</span></span>

- <span data-ttu-id="a1c3b-138">Aktualisieren Sie unter _Developer Informationen das Feld **Website-URL** mit Ihrer *ngrok* -HTTPS-URL.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-138">Under _Developer information\* update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="a1c3b-139">Aktualisieren Sie unter *App-URLs* die **Datenschutzbestimmungen** und **Nutzungsbedingungen für** URL-Felder mit Ihrer *ngrok* -HTTPS-URL.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-139">Under *App URLs* update the **Privacy statement** and **Terms of use** URL fields with your *ngrok* HTTPS URL.</span></span> <span data-ttu-id="a1c3b-140">Denken Sie daran, die */Privacy* -und */tou* -Pfade am Ende der URLs einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-140">Remember to include the */privacy* and */tou* paths at the end of the URLs.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="a1c3b-141">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="a1c3b-141">Capabilities: Tabs</span></span>

<span data-ttu-id="a1c3b-142">Im Abschnitt *Tabs* :</span><span class="sxs-lookup"><span data-stu-id="a1c3b-142">In the *Tabs* section:</span></span>

- <span data-ttu-id="a1c3b-143">Wählen Sie unter *Team Tab* die Option **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-143">Under *Team Tab* select **Add**.</span></span>

- <span data-ttu-id="a1c3b-144">Aktualisieren Sie im Popupfenster der Registerkarte "Team" die *Konfigurations-URL* auf `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="a1c3b-144">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="a1c3b-145">Stellen Sie schließlich sicher, dass die *Konfiguration aktualisiert werden kann? Team*-und *Gruppenchat* Felder werden überprüft, und wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-145">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="a1c3b-146">Fertig stellen: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="a1c3b-146">Finish: Domains and permissions</span></span>

<span data-ttu-id="a1c3b-147">Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld Ihre ngrok-URL ohne das Präfix "https" enthalten `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="a1c3b-147">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="test-and-distribute-test-and-distribute"></a><span data-ttu-id="a1c3b-148">Testen und verteilen: Testen und verteilen</span><span class="sxs-lookup"><span data-stu-id="a1c3b-148">Test and distribute: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="a1c3b-149">Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a1c3b-149">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="a1c3b-150">&#9888; "**das Array" validDomains "kann keine Tunneling-Website enthalten...**"</span><span class="sxs-lookup"><span data-stu-id="a1c3b-150">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="a1c3b-151">Diese Warnung kann beim Testen der Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-151">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="a1c3b-152">Im Abschnitt *Testen und verteilen* :</span><span class="sxs-lookup"><span data-stu-id="a1c3b-152">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="a1c3b-153">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-153">Select **Install**.</span></span>

- <span data-ttu-id="a1c3b-154">Geben Sie in das Popupfenster *Hinzufügen zu einem Team oder Chat* Feld Ihr Team ein, und wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-154">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="a1c3b-155">Wählen Sie im nächsten Popupfenster den Team Kanal aus, in dem die Registerkarte angezeigt werden soll, und wählen Sie **Einrichten** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-155">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="a1c3b-156">Wählen Sie im letzten Popupfenster einen Wert für die Registerkartenseite aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-156">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="a1c3b-157">Navigieren Sie zum Anzeigen der Registerkarte zu dem Team, auf dem Sie es installiert haben, und wählen Sie es in der Registerkartenleiste aus.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-157">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="a1c3b-158">Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a1c3b-158">The page that you chose during configuration should be displayed.</span></span>
