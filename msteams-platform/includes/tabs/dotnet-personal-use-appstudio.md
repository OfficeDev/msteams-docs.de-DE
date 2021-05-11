## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="c3439-101">Hochladen Ihrer Registerkarte, um Teams App Studio zu verwenden</span><span class="sxs-lookup"><span data-stu-id="c3439-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="c3439-102">Wir verwenden App Studio, um Ihre **manifest.jsdatei zu** bearbeiten und das fertige Paket in das Teams.</span><span class="sxs-lookup"><span data-stu-id="c3439-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="c3439-103">Sie können die Einstellungen auch **manuellmanifest.jsbearbeiten,** wenn Sie dies bevorzugen.</span><span class="sxs-lookup"><span data-stu-id="c3439-103">You can also manually edit **manifest.json** if you prefer.</span></span> <span data-ttu-id="c3439-104">Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **Tab.zip** hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="c3439-104">If you do, be sure to build the solution again to create the **Tab.zip** file to upload.</span></span>

- <span data-ttu-id="c3439-105">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="c3439-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="c3439-106">Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="c3439-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="c3439-107">Öffnen Sie App studio, und wählen Sie die **Registerkarte Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-107">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="c3439-108">Wählen Sie **die Kachel Vorhandene App importieren** im Manifest-Editor aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode verfügt über ein eigenes teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="c3439-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="c3439-109">Der Name Ihres App-Pakets **isttab.zip.**</span><span class="sxs-lookup"><span data-stu-id="c3439-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="c3439-110">Sie sollte hier gefunden werden:</span><span class="sxs-lookup"><span data-stu-id="c3439-110">It should be found here:</span></span>

```bash
/bin/Debug/netcoreapp2.2/Tab.zip
```

- <span data-ttu-id="c3439-111">Hochladen **Tab.zip** App Studio.</span><span class="sxs-lookup"><span data-stu-id="c3439-111">Upload **Tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="c3439-112">Aktualisieren Des App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="c3439-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="c3439-113">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="c3439-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="c3439-114">Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Willkommensseite des Manifest-Editors aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="c3439-115">Es gibt eine Liste der Schritte auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste der Eigenschaften, die Werte für jeden dieser Schritte aufweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="c3439-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="c3439-116">Viele der Informationen wurden von Ihremmanifest.js *bereitgestellt,* aber es gibt einige Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="c3439-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="c3439-117">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="c3439-117">Details: App details</span></span>

<span data-ttu-id="c3439-118">Im Abschnitt *App-Details:*</span><span class="sxs-lookup"><span data-stu-id="c3439-118">In the *App details* section:</span></span>

- <span data-ttu-id="c3439-119">Wählen *Sie unter Identifikation* die Option **Generieren** aus, um eine neue App-ID für Ihre App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="c3439-119">Under *Identification* select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="c3439-120">Aktualisieren *Sie unter* Entwicklerinformationen die **Website-URL** mit Ihrer *ngrok-HTTPS-URL.*</span><span class="sxs-lookup"><span data-stu-id="c3439-120">Under *Developer information* update the **Website URL** with your *ngrok* HTTPS URL.</span></span>

- <span data-ttu-id="c3439-121">Aktualisieren *Sie unter App-URLs* **die Datenschutzerklärung** auf `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** für `https://<yourngrokurl>/tou`>.</span><span class="sxs-lookup"><span data-stu-id="c3439-121">Under *App URLs* update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="c3439-122">Funktionen: Registerkarten</span><span class="sxs-lookup"><span data-stu-id="c3439-122">Capabilities: Tabs</span></span>

<span data-ttu-id="c3439-123">Im Abschnitt *Registerkarten:*</span><span class="sxs-lookup"><span data-stu-id="c3439-123">In the *Tabs* section:</span></span>

- <span data-ttu-id="c3439-124">Wählen *Sie unter Persönliche Registerkarte hinzufügen* die Option Hinzufügen ***aus.***</span><span class="sxs-lookup"><span data-stu-id="c3439-124">Under *Add a personal tab* select ***Add***.</span></span> <span data-ttu-id="c3439-125">Ihnen wird ein Popupdialogfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c3439-125">You will be presented with a pop-up dialogue window.</span></span>

- <span data-ttu-id="c3439-126">Füllen Sie das *Feld Name* aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-126">Complete the *Name* field.</span></span>

- <span data-ttu-id="c3439-127">Füllen Sie das *Feld Entitäts-ID* aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-127">Complete the *Entity Id* field.</span></span>

- <span data-ttu-id="c3439-128">Aktualisieren Sie *das Feld Inhalts-URL* mit auf `https://<yourngrokurl>/personalTab` .</span><span class="sxs-lookup"><span data-stu-id="c3439-128">Update the *Content URL* field with to `https://<yourngrokurl>/personalTab`.</span></span>

- <span data-ttu-id="c3439-129">Lassen Sie *das Feld Website-URL* leer.</span><span class="sxs-lookup"><span data-stu-id="c3439-129">Leave the *Website URL* field blank.</span></span>

- <span data-ttu-id="c3439-130">Wählen Sie ***Speichern*** aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-130">Select ***Save***.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="c3439-131">Finish: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="c3439-131">Finish: Domains and permissions</span></span>

<span data-ttu-id="c3439-132">Im Abschnitt *Domänen und Berechtigungen* sollte das Feld Domänen aus Ihrem *Registerkartenfeld* Ihre ngrok-URL ohne das HTTPS-Präfix - `<yourngrokurl>.ngrok.io/` enthalten.</span><span class="sxs-lookup"><span data-stu-id="c3439-132">In the *Domains and permissions* section, the *Domains from your tabs* field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="c3439-133">Finish: Testen und Verteilen</span><span class="sxs-lookup"><span data-stu-id="c3439-133">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="c3439-134">Im **Feld Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c3439-134">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="c3439-135">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span><span class="sxs-lookup"><span data-stu-id="c3439-135">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="c3439-136">Diese Warnung kann beim Testen ihrer Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="c3439-136">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="c3439-137">Im Abschnitt *Test and distribute:*</span><span class="sxs-lookup"><span data-stu-id="c3439-137">In the *Test and distribute* section:</span></span>

- <span data-ttu-id="c3439-138">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-138">Select **Install**.</span></span>

- <span data-ttu-id="c3439-139">Stellen Sie im Popupfenster sicher, dass *Hinzufügen* für Sie auf *Ja* und *Hinzufügen* zu einem Team oder Chat auf Nein *festgelegt ist.*</span><span class="sxs-lookup"><span data-stu-id="c3439-139">In the pop-up window make sure that *Add for you* is set to *Yes* and *Add to a team or chat* is set to *No*.</span></span>

- <span data-ttu-id="c3439-140">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-140">Select **Install**.</span></span>

- <span data-ttu-id="c3439-141">Wählen Sie im nächsten Popupfenster **Öffnen** aus, und Ihre Registerkarte wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c3439-141">In the next pop-up window select **Open** and your tab will be displayed.</span></span>

## <a name="view-your-personal-tab"></a><span data-ttu-id="c3439-142">Anzeigen Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="c3439-142">View your personal tab</span></span>

- <span data-ttu-id="c3439-143">Wählen Sie in der Navigationsleiste ganz links neben der Teams das `...` Menü aus.</span><span class="sxs-lookup"><span data-stu-id="c3439-143">In the navigation bar located at the far-left of the Teams App, select the `...` menu.</span></span> <span data-ttu-id="c3439-144">Ihnen wird eine Liste der persönlichen Apps angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c3439-144">You'll be presented with a list of personal apps.</span></span>

- <span data-ttu-id="c3439-145">Wählen Sie ihre Registerkarte aus der Liste aus, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c3439-145">Select your tab from the list to view.</span></span>
