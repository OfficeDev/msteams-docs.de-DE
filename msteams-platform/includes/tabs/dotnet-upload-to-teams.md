## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="965ed-101">Hochladen der Registerkarte in Microsoft Teams mit App Studio</span><span class="sxs-lookup"><span data-stu-id="965ed-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="965ed-102">Wir verwenden App Studio, um Ihre **Manifest. JSON** -Datei zu bearbeiten und das abgeschlossene Paket in Microsoft Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="965ed-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="965ed-103">Sie können die Datei " **Manifest. JSON** " auch manuell bearbeiten, wenn Sie dies bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="965ed-103">You can also manually edit the **manifest.json** file if you prefer.</span></span> <span data-ttu-id="965ed-104">Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die Datei **"Tab. zip"** zu erstellen, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="965ed-104">If you do, be sure to build the solution again to create the **tab.zip** file to upload.</span></span>

- <span data-ttu-id="965ed-105">Öffnen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="965ed-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="965ed-106">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="965ed-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="965ed-107">Öffnen Sie die APP Studio-app, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-107">Open the App Studio app and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="965ed-108">Wählen Sie die Kachel **Importieren einer vorhandenen APP** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="965ed-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="965ed-109">Der Name Ihres App-Pakets lautet **Tab. zip**.</span><span class="sxs-lookup"><span data-stu-id="965ed-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="965ed-110">Es sollte hier gefunden werden:</span><span class="sxs-lookup"><span data-stu-id="965ed-110">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- <span data-ttu-id="965ed-111">Upload **Tab. zip** in App Studio.</span><span class="sxs-lookup"><span data-stu-id="965ed-111">Upload **tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="965ed-112">Aktualisieren des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="965ed-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="965ed-113">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration fertig stellen.</span><span class="sxs-lookup"><span data-stu-id="965ed-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="965ed-114">Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="965ed-115">Auf der linken Seite des Manifest-Editors finden Sie eine Liste mit Schritten und auf der rechten Seite eine Liste mit Eigenschaften, die für jeden dieser Schritte Werte enthalten müssen.</span><span class="sxs-lookup"><span data-stu-id="965ed-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="965ed-116">Ein Großteil der Informationen wurde von Ihrem *Manifest. JSON* bereitgestellt, aber es gibt ein paar Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="965ed-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="965ed-117">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="965ed-117">Details: App details</span></span>

- <span data-ttu-id="965ed-118">Wählen Sie unter *Identifikation* **generieren** aus, um eine neue APP-ID für Ihre APP zu generieren.</span><span class="sxs-lookup"><span data-stu-id="965ed-118">Under *Identification* select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="965ed-119">Aktualisieren Sie unter *Entwickler Informationen* das Feld **Website-URL** mit Ihrer *ngrok* -HTTPS-URL.</span><span class="sxs-lookup"><span data-stu-id="965ed-119">Under *Developer information* update the **Website URL** field with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="965ed-120">Aktualisieren Sie unter *App* `https://<yourngrokurl>/privacy` -URLs die **Datenschutzbestimmungen** und **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="965ed-120">Under *App URLs* update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="965ed-121">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="965ed-121">Capabilities: Tabs</span></span>

<span data-ttu-id="965ed-122">Im Abschnitt *Tabs* :</span><span class="sxs-lookup"><span data-stu-id="965ed-122">In the *Tabs* section:</span></span>

- <span data-ttu-id="965ed-123">Wählen Sie unter *Team Tab* die Option **Hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-123">Under *Team Tab* select **Add**.</span></span>

- <span data-ttu-id="965ed-124">Aktualisieren Sie im Popupfenster der Registerkarte "Team" die Konfigurations `https://<yourngrokurl>/tab`- *URL* auf.</span><span class="sxs-lookup"><span data-stu-id="965ed-124">In the Team tab pop-up window update the *Configuration URL* to `https://<yourngrokurl>/tab`.</span></span>

- <span data-ttu-id="965ed-125">Stellen Sie schließlich sicher, dass die *Konfiguration aktualisiert werden kann? Team*-und *Gruppenchat* Felder werden überprüft, und wählen Sie **Speichern**aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-125">Finally, make sure the *can update configuration? Team*, and *Group chat* boxes are checked and select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="965ed-126">Fertig stellen: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="965ed-126">Finish: Domains and permissions</span></span>

<span data-ttu-id="965ed-127">Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld Ihre ngrok- `<yourngrokurl>.ngrok.io/`URL ohne das Präfix "https" enthalten.</span><span class="sxs-lookup"><span data-stu-id="965ed-127">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

#### <a name="finish-test-and-distribute"></a><span data-ttu-id="965ed-128">Fertig stellen: Testen und verteilen</span><span class="sxs-lookup"><span data-stu-id="965ed-128">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="965ed-129">Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="965ed-129">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="965ed-130">&#9888; "**das Array" validDomains "kann keine Tunneling-Website enthalten...**"</span><span class="sxs-lookup"><span data-stu-id="965ed-130">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="965ed-131">Diese Warnung kann beim Testen der Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="965ed-131">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="965ed-132">Im Abschnitt *Testen und verteilen* :</span><span class="sxs-lookup"><span data-stu-id="965ed-132">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="965ed-133">**Installieren** auswählen.</span><span class="sxs-lookup"><span data-stu-id="965ed-133">Select **Install**.</span></span>

- <span data-ttu-id="965ed-134">Geben Sie in das Popupfenster *Hinzufügen zu einem Team oder Chat* Feld Ihr Team ein, und wählen Sie **Installieren**aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-134">In the pop-up window's *Add to a team or chat* field enter your team and select **Install**.</span></span>

- <span data-ttu-id="965ed-135">Wählen Sie im nächsten Popupfenster den Team Kanal aus, in dem die Registerkarte angezeigt werden soll, und wählen Sie **Einrichten**aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-135">In the next pop-up window choose the team channel where you would like the tab displayed and select **Set up**.</span></span>

- <span data-ttu-id="965ed-136">Wählen Sie im letzten Popupfenster einen Wert für die Registerkartenseite aus (entweder ein rotes oder graues Symbol), und wählen Sie **Speichern**aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-136">In the final pop-up window select a value for the tab page (either a red or gray icon) and select **Save**.</span></span>

<span data-ttu-id="965ed-137">Navigieren Sie zum Anzeigen der Registerkarte zu dem Team, auf dem Sie es installiert haben, und wählen Sie es in der Registerkartenleiste aus.</span><span class="sxs-lookup"><span data-stu-id="965ed-137">To view your tab, navigate to the team you installed it on, and select it from the tab bar.</span></span> <span data-ttu-id="965ed-138">Die Seite, die Sie während der Konfiguration ausgewählt haben, sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="965ed-138">The page that you chose during configuration should be displayed.</span></span>
