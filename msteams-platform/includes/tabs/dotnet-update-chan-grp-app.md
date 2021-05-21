### <a name="_layoutcshtml"></a><span data-ttu-id="7572f-101">_Layout.cshtml</span><span class="sxs-lookup"><span data-stu-id="7572f-101">_Layout.cshtml</span></span>

<span data-ttu-id="7572f-102">Damit Ihre Registerkarte in Teams angezeigt werden kann, müssen Sie das Microsoft Teams **JavaScript-Client-SDK** und einen Aufruf nach dem Laden der `microsoftTeams.initialize()` Seite hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7572f-102">For your tab to display in Teams, you must include the **Microsoft Teams JavaScript client SDK** and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="7572f-103">So kommunizieren Ihre Registerkarte und Teams Client:</span><span class="sxs-lookup"><span data-stu-id="7572f-103">This is how your tab and the Teams client communicate:</span></span>

- <span data-ttu-id="7572f-104">Navigieren Sie zum **Freigegebenen** Ordner, öffnen **Sie _Layout.cshtml**, und fügen Sie dem Tag Folgendes `<head>` hinzu:</span><span class="sxs-lookup"><span data-stu-id="7572f-104">Navigate to the **Shared** folder, open **_Layout.cshtml**, and add the following to the `<head>` tag:</span></span>

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

>[!IMPORTANT]
><span data-ttu-id="7572f-105">Kopieren/einfügen Sie die URLs nicht von dieser Seite, da `<script src="...">` sie möglicherweise nicht die neueste Version darstellen.</span><span class="sxs-lookup"><span data-stu-id="7572f-105">Don't copy/paste the `<script src="...">` URLs from this page, as they may not represent the latest version.</span></span> <span data-ttu-id="7572f-106">Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu: [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).</span><span class="sxs-lookup"><span data-stu-id="7572f-106">To get the latest version of the SDK, always go to: [Microsoft Teams JavaScript API](https://www.npmjs.com/package/@microsoft/teams-js).</span></span>

### <a name="tabcshtml"></a><span data-ttu-id="7572f-107">Tab.cshtml</span><span class="sxs-lookup"><span data-stu-id="7572f-107">Tab.cshtml</span></span>

<span data-ttu-id="7572f-108">Öffnen **Sie Tab.cshtml,** und aktualisieren Sie den `<script>` eingebetteten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7572f-108">Open **Tab.cshtml** and update the embedded `<script>` as follows:</span></span>

- <span data-ttu-id="7572f-109">Rufen Sie oben im Skript `microsoftTeams.initialize()` auf.</span><span class="sxs-lookup"><span data-stu-id="7572f-109">At the top of the script, call `microsoftTeams.initialize()`.</span></span>

- <span data-ttu-id="7572f-110">Aktualisieren Sie `websiteUrl` die Werte und in jeder Funktion mit der HTTPS `contentUrl` ngrok-URL auf Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="7572f-110">Update the `websiteUrl` and `contentUrl` values in each function with the HTTPS ngrok URL to your tab.</span></span>

<span data-ttu-id="7572f-111">Ihr Code sollte nun wie folgt aussehen, **wenn y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:</span><span class="sxs-lookup"><span data-stu-id="7572f-111">Your code should now look like the following with **y8rCgT2b** replaced with your ngrok URL:</span></span>

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

<span data-ttu-id="7572f-112">Stellen Sie sicher, dass Sie die aktualisierte **Tab.cshtml -Datei speichern.**</span><span class="sxs-lookup"><span data-stu-id="7572f-112">Make sure to save the updated **Tab.cshtml**.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="7572f-113">Erstellen und Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="7572f-113">Build and run your application</span></span>

- <span data-ttu-id="7572f-114">Drücken Visual Studio **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus.</span><span class="sxs-lookup"><span data-stu-id="7572f-114">In Visual Studio press **F5**, or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="7572f-115">Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="7572f-115">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="7572f-116">Sie müssen ihre Anwendung in Visual Studio und ngrok ausführen, um diesen Schnellstart ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7572f-116">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="7572f-117">Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio, damit sie funktioniert, **halten Sie ngrok am Laufen.**</span><span class="sxs-lookup"><span data-stu-id="7572f-117">If you need to stop running your application in Visual Studio to work on it **keep ngrok running**.</span></span> <span data-ttu-id="7572f-118">Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in einem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7572f-118">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="7572f-119">Wenn Sie den ngrok-Dienst neu starten müssen, gibt er eine neue URL zurück, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7572f-119">If you have to restart the ngrok service it will return a new URL and you'll have to update your application with the new URL.</span></span>

## <a name="upload-your-tab-to-teams"></a><span data-ttu-id="7572f-120">Hochladen Registerkarte zum Teams</span><span class="sxs-lookup"><span data-stu-id="7572f-120">Upload your tab to Teams</span></span>

>[!Note]
> <span data-ttu-id="7572f-121">Wir verwenden App Studio, um Ihre **manifest.jsdatei zu** bearbeiten und das fertige Paket in das Teams.</span><span class="sxs-lookup"><span data-stu-id="7572f-121">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="7572f-122">Sie können die Datei auch manuellmanifest.js **on-Datei** bearbeiten, wenn Sie es vorziehen.</span><span class="sxs-lookup"><span data-stu-id="7572f-122">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="7572f-123">Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **tab.zip** hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="7572f-123">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="7572f-124">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="7572f-124">Open the Microsoft Teams client.</span></span> <span data-ttu-id="7572f-125">Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="7572f-125">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="7572f-126">Öffnen Sie App studio, und wählen Sie die **Registerkarte Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="7572f-126">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="7572f-127">Wählen Sie **die Kachel Vorhandene App importieren** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode verfügt über ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="7572f-127">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="7572f-128">Der Name Ihres App-Pakets **isttab.zip.**</span><span class="sxs-lookup"><span data-stu-id="7572f-128">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="7572f-129">Sie sollte hier gefunden werden:</span><span class="sxs-lookup"><span data-stu-id="7572f-129">It should be found here:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/tab.zip
    ```

- <span data-ttu-id="7572f-130">Hochladen **tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="7572f-130">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="7572f-131">Aktualisieren Des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="7572f-131">Update your app package with Manifest editor</span></span>

<span data-ttu-id="7572f-132">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="7572f-132">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="7572f-133">Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="7572f-133">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="7572f-134">Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die Werte für jeden dieser Schritte aufweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="7572f-134">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="7572f-135">Viele der Informationen wurden von Ihremmanifest.js *bereitgestellt,* aber es gibt einige Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="7572f-135">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="7572f-136">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="7572f-136">Details: App details</span></span>

<span data-ttu-id="7572f-137">Im Abschnitt *App-Details:*</span><span class="sxs-lookup"><span data-stu-id="7572f-137">In the *App details* section:</span></span>

- <span data-ttu-id="7572f-138">*Identifikation:* Wählen Sie **Generieren** aus, um die Platzhalter-ID durch die erforderliche GUID für Ihre Registerkarte zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="7572f-138">*Identification*: select **Generate** to replace the placeholder id with the required GUID for your tab.</span></span>

- <span data-ttu-id="7572f-139">*Entwicklerinformationen:* Aktualisieren Sie das **Feld Website-URL** mit Ihrer *ngrok-HTTPS-URL.*</span><span class="sxs-lookup"><span data-stu-id="7572f-139">*Developer information*: update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="7572f-140">*App-URLs*: Aktualisieren Sie **die Datenschutzbestimmungen** `https://<yourngrokurl>/privacy` auf und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="7572f-140">*App URLs*: update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="7572f-141">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="7572f-141">Capabilities: Tabs</span></span>

<span data-ttu-id="7572f-142">Im Abschnitt *Registerkarten:*</span><span class="sxs-lookup"><span data-stu-id="7572f-142">In the *Tabs* section:</span></span>

- <span data-ttu-id="7572f-143">*Registerkarte Team*: wählen Sie **Hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="7572f-143">*Team Tab*: select **Add**.</span></span>

- <span data-ttu-id="7572f-144">Aktualisieren Sie im Popupfenster team tab die *Konfigurations-URL auf* `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="7572f-144">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="7572f-145">Stellen Sie schließlich sicher, dass *die Konfiguration aktualisiert werden kann? Die Chatfelder Team* und *Gruppe* werden aktiviert, und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="7572f-145">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="7572f-146">Finish: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="7572f-146">Finish: Domains and permissions</span></span>

<span data-ttu-id="7572f-147">Im Abschnitt *Domänen und Berechtigungen:*</span><span class="sxs-lookup"><span data-stu-id="7572f-147">In the *Domains and permissions* section:</span></span>

- <span data-ttu-id="7572f-148">The *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="7572f-148">The *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="finish-test-and-distribute"></a><span data-ttu-id="7572f-149">Finish: Testen und Verteilen</span><span class="sxs-lookup"><span data-stu-id="7572f-149">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="7572f-150">Im **Feld Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="7572f-150">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="7572f-151">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span><span class="sxs-lookup"><span data-stu-id="7572f-151">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="7572f-152">Diese Warnung kann beim Testen ihrer Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="7572f-152">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="7572f-153">Im Abschnitt *Test and distribute:*</span><span class="sxs-lookup"><span data-stu-id="7572f-153">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="7572f-154">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="7572f-154">Select **Install**.</span></span>

- <span data-ttu-id="7572f-155">Geben Sie im Popupfenster Hinzufügen zu einem Team oder *Chatfeld* Ihr Team ein, und wählen Sie **Installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="7572f-155">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="7572f-156">Wählen Sie im nächsten Popupfenster den Teamkanal aus, in dem die Registerkarte angezeigt werden soll, und wählen **Sie Einrichten aus.**</span><span class="sxs-lookup"><span data-stu-id="7572f-156">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="7572f-157">Wählen Sie im letzten Popupfenster einen Wert für die Registerkarte aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="7572f-157">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="7572f-158">Navigieren Sie zum Anzeigen Ihrer Registerkarte zu dem Team, in dem Sie sie installiert haben, und wählen Sie sie in der Registerkartenleiste aus.</span><span class="sxs-lookup"><span data-stu-id="7572f-158">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="7572f-159">Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7572f-159">The page that you chose during configuration should be displayed.</span></span>
