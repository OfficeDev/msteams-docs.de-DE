## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="ec992-101">Hochladen der Registerkarte in Microsoft Teams mit App Studio</span><span class="sxs-lookup"><span data-stu-id="ec992-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="ec992-102">Wir verwenden App Studio, um Ihre **Manifest. JSON** -Datei zu bearbeiten und das abgeschlossene Paket in Microsoft Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="ec992-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="ec992-103">Sie können **Manifest. JSON** auch manuell bearbeiten, wenn Sie dies bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="ec992-103">You can also manually edit **manifest.json** if you prefer.</span></span> <span data-ttu-id="ec992-104">Wenn Sie dies tun, müssen Sie die Lösung erneut erstellen, um die Datei **"Tab. zip"** zu erstellen, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ec992-104">If you do, be sure to build the solution again to create the **Tab.zip** file to upload.</span></span>

- <span data-ttu-id="ec992-105">Öffnen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="ec992-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="ec992-106">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ec992-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="ec992-107">Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="ec992-107">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="ec992-108">Wählen Sie die Kachel **Importieren einer vorhandenen APP** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="ec992-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="ec992-109">Der Name Ihres App-Pakets lautet **Tab. zip**.</span><span class="sxs-lookup"><span data-stu-id="ec992-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="ec992-110">Es sollte hier gefunden werden:</span><span class="sxs-lookup"><span data-stu-id="ec992-110">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/Tab.zip
```

- <span data-ttu-id="ec992-111">Upload **Tab. zip** in App Studio.</span><span class="sxs-lookup"><span data-stu-id="ec992-111">Upload **Tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="ec992-112">Aktualisieren des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="ec992-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="ec992-113">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration fertig stellen.</span><span class="sxs-lookup"><span data-stu-id="ec992-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="ec992-114">Wählen Sie die Kachel für Ihre neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="ec992-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="ec992-115">Auf der linken Seite des Manifest-Editors finden Sie eine Liste mit Schritten und auf der rechten Seite eine Liste mit Eigenschaften, die für jeden dieser Schritte Werte enthalten müssen.</span><span class="sxs-lookup"><span data-stu-id="ec992-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="ec992-116">Ein Großteil der Informationen wurde von Ihrem *Manifest. JSON* bereitgestellt, aber es gibt ein paar Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="ec992-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="ec992-117">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="ec992-117">Details: App details</span></span>

<span data-ttu-id="ec992-118">Im Abschnitt *App-Details* :</span><span class="sxs-lookup"><span data-stu-id="ec992-118">In the *App details* section:</span></span>

- <span data-ttu-id="ec992-119">Wählen Sie unter *Identifikation* **generieren** aus, um eine neue APP-ID für Ihre APP zu generieren.</span><span class="sxs-lookup"><span data-stu-id="ec992-119">Under *Identification* select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="ec992-120">Aktualisieren Sie unter *Entwickler Informationen* die **Website-URL** mit Ihrer *ngrok* -HTTPS-URL.</span><span class="sxs-lookup"><span data-stu-id="ec992-120">Under *Developer information* update the **Website URL** with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="ec992-121">Aktualisieren Sie unter *App* `https://<yourngrokurl>/privacy` -URLs die **Datenschutzbestimmungen** und **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="ec992-121">Under *App URLs* update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="ec992-122">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="ec992-122">Capabilities: Tabs</span></span>

<span data-ttu-id="ec992-123">Im Abschnitt *Tabs* :</span><span class="sxs-lookup"><span data-stu-id="ec992-123">In the *Tabs* section:</span></span>

- <span data-ttu-id="ec992-124">Wählen Sie unter *persönliche Registerkarte hinzufügen die* Option ***Hinzufügen***aus.</span><span class="sxs-lookup"><span data-stu-id="ec992-124">Under *Add a personal tab* select ***Add***.</span></span> <span data-ttu-id="ec992-125">Ihnen wird ein Popup-Dialogfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec992-125">You will be presented with a pop-up dialogue window.</span></span>

- <span data-ttu-id="ec992-126">Füllen Sie das Feld *Name* aus.</span><span class="sxs-lookup"><span data-stu-id="ec992-126">Complete the *Name* field.</span></span>

- <span data-ttu-id="ec992-127">Schließen Sie das Feld *Entitäts-ID* ab.</span><span class="sxs-lookup"><span data-stu-id="ec992-127">Complete the *Entity Id* field.</span></span>

- <span data-ttu-id="ec992-128">Aktualisieren Sie das Feld *Inhalts* -URL `https://<yourngrokurl>/personalTab`mit auf.</span><span class="sxs-lookup"><span data-stu-id="ec992-128">Update the *Content URL* field with to `https://<yourngrokurl>/personalTab`.</span></span>

- <span data-ttu-id="ec992-129">Lassen Sie das Feld *Website-URL* leer.</span><span class="sxs-lookup"><span data-stu-id="ec992-129">Leave the *Website URL* field blank.</span></span>

- <span data-ttu-id="ec992-130">Klicken Sie auf ***Speichern***.</span><span class="sxs-lookup"><span data-stu-id="ec992-130">Select ***Save***.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="ec992-131">Fertig stellen: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="ec992-131">Finish: Domains and permissions</span></span>

<span data-ttu-id="ec992-132">Im Abschnitt *Domains and Permissions* sollte die *Domäne aus Ihrem Registerkarten* Feld Ihre ngrok- `<yourngrokurl>.ngrok.io/`URL ohne das Präfix "https" enthalten.</span><span class="sxs-lookup"><span data-stu-id="ec992-132">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="ec992-133">Fertig stellen: Testen und verteilen</span><span class="sxs-lookup"><span data-stu-id="ec992-133">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="ec992-134">Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ec992-134">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="ec992-135">&#9888; "**das Array" validDomains "kann keine Tunneling-Website enthalten...**"</span><span class="sxs-lookup"><span data-stu-id="ec992-135">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="ec992-136">Diese Warnung kann beim Testen der Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="ec992-136">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="ec992-137">Im Abschnitt *Testen und verteilen* :</span><span class="sxs-lookup"><span data-stu-id="ec992-137">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="ec992-138">**Installieren** auswählen.</span><span class="sxs-lookup"><span data-stu-id="ec992-138">Select **Install**.</span></span>

- <span data-ttu-id="ec992-139">Stellen Sie im Popupfenster sicher, dass *Add for you* auf *Ja* festgelegt ist und *zu einem Team oder Chat hinzufügen* auf *Nein*festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="ec992-139">In the pop-up window make sure that *Add for you* is set to *Yes* and *Add to a team or chat* is set to *No*.</span></span>

- <span data-ttu-id="ec992-140">**Installieren** auswählen.</span><span class="sxs-lookup"><span data-stu-id="ec992-140">Select **Install**.</span></span>

- <span data-ttu-id="ec992-141">Wählen Sie im nächsten Popupfenster die Option **Öffnen** aus, und ihre Registerkarte wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec992-141">In the next pop-up window select **Open** and your tab will be displayed.</span></span>

## <a name="view-your-personal-tab"></a><span data-ttu-id="ec992-142">Anzeigen Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ec992-142">View your personal tab</span></span>

- <span data-ttu-id="ec992-143">Wählen Sie in der Navigationsleiste, die sich in der Microsoft Teams-App ganz links `...` befindet, das Menü aus.</span><span class="sxs-lookup"><span data-stu-id="ec992-143">In the navigation bar located at the far-left of the Teams App, select the `...` menu.</span></span> <span data-ttu-id="ec992-144">Ihnen wird eine Liste mit persönlichen apps angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ec992-144">You'll be presented with a list of personal apps.</span></span>

- <span data-ttu-id="ec992-145">Wählen Sie die Registerkarte aus der Liste aus, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ec992-145">Select your tab from the list to view.</span></span>
