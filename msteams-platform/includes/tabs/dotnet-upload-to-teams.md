## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="906d3-101">Hochladen Ihrer Registerkarte, um Teams App Studio zu verwenden</span><span class="sxs-lookup"><span data-stu-id="906d3-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="906d3-102">Wir verwenden App Studio, um Ihre **manifest.jsdatei zu** bearbeiten und das fertige Paket in das Teams.</span><span class="sxs-lookup"><span data-stu-id="906d3-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="906d3-103">Sie können die Datei auch manuellmanifest.js **on-Datei** bearbeiten, wenn Sie es vorziehen.</span><span class="sxs-lookup"><span data-stu-id="906d3-103">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="906d3-104">Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **tab.zip** hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="906d3-104">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="906d3-105">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="906d3-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="906d3-106">Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="906d3-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="906d3-107">Öffnen Sie die App Studio-App, und wählen Sie die **Registerkarte Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="906d3-107">Open the App Studio app and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="906d3-108">Wählen Sie **die Kachel Vorhandene App importieren** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode verfügt über ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="906d3-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="906d3-109">Der Name Ihres App-Pakets **isttab.zip.**</span><span class="sxs-lookup"><span data-stu-id="906d3-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="906d3-110">Sie sollte hier gefunden werden:</span><span class="sxs-lookup"><span data-stu-id="906d3-110">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- <span data-ttu-id="906d3-111">Hochladen **tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="906d3-111">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="906d3-112">Aktualisieren Des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="906d3-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="906d3-113">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="906d3-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="906d3-114">Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="906d3-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="906d3-115">Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die Werte für jeden dieser Schritte aufweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="906d3-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="906d3-116">Viele der Informationen wurden von Ihremmanifest.js *bereitgestellt,* aber es gibt einige Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="906d3-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="906d3-117">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="906d3-117">Details: App details</span></span>

- <span data-ttu-id="906d3-118">Wählen *Sie unter Identifikation* die Option **Generieren** aus, um eine neue App-ID für Ihre App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="906d3-118">Under *Identification* select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="906d3-119">Aktualisieren *Sie unter Entwicklerinformationen* das **Feld Website-URL** mit Ihrer *ngrok-HTTPS-URL.*</span><span class="sxs-lookup"><span data-stu-id="906d3-119">Under *Developer information* update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="906d3-120">Aktualisieren *Sie unter App-URLs* **die Datenschutzerklärung** auf `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="906d3-120">Under *App URLs* update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="906d3-121">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="906d3-121">Capabilities: Tabs</span></span>

<span data-ttu-id="906d3-122">Im Abschnitt *Registerkarten:*</span><span class="sxs-lookup"><span data-stu-id="906d3-122">In the *Tabs* section:</span></span>

- <span data-ttu-id="906d3-123">Wählen *Sie unter Registerkarte Team* die Option Hinzufügen **aus.**</span><span class="sxs-lookup"><span data-stu-id="906d3-123">Under *Team Tab* select **Add**.</span></span>

- <span data-ttu-id="906d3-124">Aktualisieren Sie im Popupfenster team tab die *Konfigurations-URL auf* `https://<yourngrokurl>/tab` .</span><span class="sxs-lookup"><span data-stu-id="906d3-124">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="906d3-125">Stellen Sie schließlich sicher, dass *die Konfiguration aktualisiert werden kann? Die Chatfelder Team* und *Gruppe* werden aktiviert, und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="906d3-125">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="906d3-126">Finish: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="906d3-126">Finish: Domains and permissions</span></span>

<span data-ttu-id="906d3-127">Im Abschnitt *Domänen und Berechtigungen* sollte das Feld Domänen aus Ihrem *Registerkartenfeld* Ihre ngrok-URL ohne das HTTPS-Präfix - `<yourngrokurl>.ngrok.io/` enthalten.</span><span class="sxs-lookup"><span data-stu-id="906d3-127">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="finish-test-and-distribute"></a><span data-ttu-id="906d3-128">Finish: Testen und Verteilen</span><span class="sxs-lookup"><span data-stu-id="906d3-128">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="906d3-129">Im **Feld Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="906d3-129">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="906d3-130">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span><span class="sxs-lookup"><span data-stu-id="906d3-130">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="906d3-131">Diese Warnung kann beim Testen ihrer Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="906d3-131">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="906d3-132">Im Abschnitt *Test and distribute:*</span><span class="sxs-lookup"><span data-stu-id="906d3-132">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="906d3-133">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="906d3-133">Select **Install**.</span></span>

- <span data-ttu-id="906d3-134">Geben Sie im Popupfenster Hinzufügen zu einem Team oder *Chatfeld* Ihr Team ein, und wählen Sie **Installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="906d3-134">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="906d3-135">Wählen Sie im nächsten Popupfenster den Teamkanal aus, in dem die Registerkarte angezeigt werden soll, und wählen **Sie Einrichten aus.**</span><span class="sxs-lookup"><span data-stu-id="906d3-135">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="906d3-136">Wählen Sie im letzten Popupfenster einen Wert für die Registerkarte aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="906d3-136">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="906d3-137">Navigieren Sie zum Anzeigen Ihrer Registerkarte zu dem Team, in dem Sie sie installiert haben, und wählen Sie sie in der Registerkartenleiste aus.</span><span class="sxs-lookup"><span data-stu-id="906d3-137">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="906d3-138">Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="906d3-138">The page that you chose during configuration should be displayed.</span></span>
