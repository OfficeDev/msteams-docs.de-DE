## <a name="upload-your-tab-to-teams-with-app-studio"></a><span data-ttu-id="0b356-101">Hochladen Sie Ihren Tab, um mit App Studio zu Teams</span><span class="sxs-lookup"><span data-stu-id="0b356-101">Upload your tab to Teams with App Studio</span></span>

>[!NOTE]
> <span data-ttu-id="0b356-102">Wir verwenden App Studio, um Ihre **manifest.jsin** der Datei zu bearbeiten und das fertige Paket in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="0b356-102">We use App Studio to edit your **manifest.json** file and upload the completed package to Teams.</span></span> <span data-ttu-id="0b356-103">Sie können **manifest.js** auch manuell bearbeiten, wenn Sie dies vorziehen.</span><span class="sxs-lookup"><span data-stu-id="0b356-103">You can also manually edit **manifest.json** if you prefer.</span></span> <span data-ttu-id="0b356-104">Wenn Sie dies tun, stellen Sie sicher, dass Sie die Lösung erneut erstellen, um die **Tab.zip** Datei zu erstellen, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="0b356-104">If you do, be sure to build the solution again to create the **Tab.zip** file to upload.</span></span>

- <span data-ttu-id="0b356-105">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="0b356-105">Open the Microsoft Teams client.</span></span> <span data-ttu-id="0b356-106">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mit den [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0b356-106">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>

- <span data-ttu-id="0b356-107">Öffnen Sie App Studio, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-107">Open App studio and select the **Manifest editor** tab.</span></span>

- <span data-ttu-id="0b356-108">Wählen Sie im Manifest-Editor die Kachel **"Importieren einer vorhandenen App"** aus, um mit der Aktualisierung des App-Pakets für Ihre Registerkarte zu beginnen. Der Quellcode enthält ein eigenes, teilweise vollständiges Manifest.</span><span class="sxs-lookup"><span data-stu-id="0b356-108">Select the **Import an existing app** tile in the Manifest editor to begin updating the app package for your tab. The source code comes with its own partially complete manifest.</span></span> <span data-ttu-id="0b356-109">Der Name Ihres App-Pakets lautet **tab.zip**.</span><span class="sxs-lookup"><span data-stu-id="0b356-109">The name of your app package is **tab.zip**.</span></span> <span data-ttu-id="0b356-110">Sie sollte hier zu finden sein:</span><span class="sxs-lookup"><span data-stu-id="0b356-110">It should be found here:</span></span>

    ```bash
    /bin/Debug/netcoreapp2.2/Tab.zip
    ```

- <span data-ttu-id="0b356-111">Hochladen **Tab.zip** zu App Studio.</span><span class="sxs-lookup"><span data-stu-id="0b356-111">Upload **Tab.zip** to App Studio.</span></span>

### <a name="update-your-app-package-with-manifest-editor"></a><span data-ttu-id="0b356-112">Aktualisieren Ihres App-Pakets mit dem Manifest-Editor</span><span class="sxs-lookup"><span data-stu-id="0b356-112">Update your app package with Manifest editor</span></span>

<span data-ttu-id="0b356-113">Nachdem Sie Ihr App-Paket in App Studio hochgeladen haben, müssen Sie die Konfiguration abschließen.</span><span class="sxs-lookup"><span data-stu-id="0b356-113">Once you've uploaded your app package into App Studio, you'll need to finish configuring it.</span></span>

- <span data-ttu-id="0b356-114">Wählen Sie die Kachel für die neu importierte Registerkarte im rechten Bereich der Manifest-Editor-Willkommensseite aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-114">Select the tile for your newly imported tab in the right panel of the Manifest editor welcome page.</span></span>

<span data-ttu-id="0b356-115">Es gibt eine Liste von Schritten auf der linken Seite des Manifest-Editors und auf der rechten Seite eine Liste von Eigenschaften, die Werte für jeden dieser Schritte haben müssen.</span><span class="sxs-lookup"><span data-stu-id="0b356-115">There's a list of steps in the left-hand side of the Manifest editor, and on the right, a list of properties that need to have values for each of those steps.</span></span> <span data-ttu-id="0b356-116">Viele der Informationen wurden von Ihrem *manifest.jsbereitgestellt,* aber es gibt ein paar Felder, die Sie aktualisieren müssen:</span><span class="sxs-lookup"><span data-stu-id="0b356-116">Much of the information has been provided by your *manifest.json* but there are a few fields that you'll need to update:</span></span>

#### <a name="details-app-details"></a><span data-ttu-id="0b356-117">Details: App-Details</span><span class="sxs-lookup"><span data-stu-id="0b356-117">Details: App details</span></span>

<span data-ttu-id="0b356-118">Im Abschnitt **App-Details:**</span><span class="sxs-lookup"><span data-stu-id="0b356-118">In the **App details** section:</span></span>

- <span data-ttu-id="0b356-119">Wählen Sie unter **Kennung** **generieren** aus, um eine neue App-ID für Ihre App zu generieren.</span><span class="sxs-lookup"><span data-stu-id="0b356-119">Under **Identification** select **Generate** to generate a new App Id for your app.</span></span>

- <span data-ttu-id="0b356-120">Aktualisieren Sie unter **Entwicklerinformationen** die **Website-URL** mit Ihrer **ngrok** HTTPS-URL.</span><span class="sxs-lookup"><span data-stu-id="0b356-120">Under **Developer information** update the **Website URL** with your **ngrok** HTTPS URL.</span></span>

- <span data-ttu-id="0b356-121">Unter **App-URLs** wird die **Datenschutzerklärung** `https://<yourngrokurl>/privacy` und die **Nutzungsbedingungen** auf `https://<yourngrokurl>/tou`> aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="0b356-121">Under **App URLs** update the **Privacy statement** to `https://<yourngrokurl>/privacy` and **Terms of use** to `https://<yourngrokurl>/tou`>.</span></span>

#### <a name="capabilities-tabs"></a><span data-ttu-id="0b356-122">Funktionen: Tabs</span><span class="sxs-lookup"><span data-stu-id="0b356-122">Capabilities: Tabs</span></span>

<span data-ttu-id="0b356-123">Im Abschnitt *Tabs:*</span><span class="sxs-lookup"><span data-stu-id="0b356-123">In the *Tabs* section:</span></span>

- <span data-ttu-id="0b356-124">Wählen Sie unter **Persönliche Registerkarte Hinzufügen** aus. </span><span class="sxs-lookup"><span data-stu-id="0b356-124">Under **Add a personal tab** select **Add**.</span></span> <span data-ttu-id="0b356-125">Sie erhalten ein Pop-up-Dialogfenster.</span><span class="sxs-lookup"><span data-stu-id="0b356-125">You will be presented with a pop-up dialogue window.</span></span>

- <span data-ttu-id="0b356-126">Füllen Sie das Feld **Name** aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-126">Complete the **Name** field.</span></span>

- <span data-ttu-id="0b356-127">Füllen Sie das Feld **Entitäts-ID** aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-127">Complete the **Entity Id** field.</span></span>

- <span data-ttu-id="0b356-128">Aktualisieren Sie das Feld **Inhalts-URL** mit `https://<yourngrokurl>/personalTab` .</span><span class="sxs-lookup"><span data-stu-id="0b356-128">Update the **Content URL** field with to `https://<yourngrokurl>/personalTab`.</span></span>

- <span data-ttu-id="0b356-129">Lassen Sie das **Feld Website-URL** leer.</span><span class="sxs-lookup"><span data-stu-id="0b356-129">Leave the **Website URL** field blank.</span></span>

- <span data-ttu-id="0b356-130">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="0b356-130">Select **Save**.</span></span>

#### <a name="finish-domains-and-permissions"></a><span data-ttu-id="0b356-131">Beenden: Domänen und Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="0b356-131">Finish: Domains and permissions</span></span>

<span data-ttu-id="0b356-132">Im Abschnitt **Domänen und Berechtigungen** sollte das Feld Domänen aus Ihrem **TabsFeld** Ihre ngrok-URL ohne das HTTPS-Präfix - `<yourngrokurl>.ngrok.io/` enthalten.</span><span class="sxs-lookup"><span data-stu-id="0b356-132">In the **Domains and permissions** section, the **Domains from your tabs** field should contain your ngrok URL without the HTTPS prefix - `<yourngrokurl>.ngrok.io/`.</span></span>

##### <a name="finish-test-and-distribute"></a><span data-ttu-id="0b356-133">Finish: Testen und verteilen</span><span class="sxs-lookup"><span data-stu-id="0b356-133">Finish: Test and distribute</span></span>

>[!IMPORTANT]
><span data-ttu-id="0b356-134">Im Feld **Beschreibung** auf der rechten Seite wird die folgende Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="0b356-134">In the **Description** field on the right you'll see the following warning:</span></span>
>
><span data-ttu-id="0b356-135">&#9888; "**Das Array 'validDomains' darf keine Tunneling-Site enthalten...**"</span><span class="sxs-lookup"><span data-stu-id="0b356-135">&#9888; "**The 'validDomains' array cannot contain a tunneling site...**"</span></span>
>
><span data-ttu-id="0b356-136">Diese Warnung kann beim Testen der Registerkarte ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="0b356-136">This warning can be ignored while testing your tab.</span></span>

<span data-ttu-id="0b356-137">Im Abschnitt **Testen und Verteilen:**</span><span class="sxs-lookup"><span data-stu-id="0b356-137">In the **Test and distribute** section:</span></span>

- <span data-ttu-id="0b356-138">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-138">Select **Install**.</span></span>

- <span data-ttu-id="0b356-139">Stellen Sie im Popupfenster sicher, dass **Add for you** auf **Ja** und Hinzufügen zu einem Team **oder Chat** auf **Nein** gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="0b356-139">In the pop-up window make sure that **Add for you** is set to **Yes** and **Add to a team or chat** is set to **No**.</span></span>

- <span data-ttu-id="0b356-140">Wählen Sie **Installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-140">Select **Install**.</span></span>

- <span data-ttu-id="0b356-141">Wählen Sie im nächsten Popup-Fenster **Öffnen** aus, und Ihre Registerkarte wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0b356-141">In the next pop-up window select **Open** and your tab will be displayed.</span></span>

## <a name="view-your-personal-tab"></a><span data-ttu-id="0b356-142">Anzeigen Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="0b356-142">View your personal tab</span></span>

- <span data-ttu-id="0b356-143">Wählen Sie in der Navigationsleiste ganz links der Teams App das `...` Menü aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-143">In the navigation bar located at the far-left of the Teams App, select the `...` menu.</span></span> <span data-ttu-id="0b356-144">Ihnen wird eine Liste persönlicher Apps angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0b356-144">You'll be presented with a list of personal apps.</span></span>

- <span data-ttu-id="0b356-145">Wählen Sie Ihre Registerkarte aus der anzuzeigenden Liste aus.</span><span class="sxs-lookup"><span data-stu-id="0b356-145">Select your tab from the list to view.</span></span>
