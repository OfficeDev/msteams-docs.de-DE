## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="aff48-101">Bereitstellen Ihrer App in Azure</span><span class="sxs-lookup"><span data-stu-id="aff48-101">Deploy your app to Azure</span></span>

<span data-ttu-id="aff48-102">Die Bereitstellung besteht aus zwei Schritten.</span><span class="sxs-lookup"><span data-stu-id="aff48-102">Deployment consists of two steps.</span></span>  <span data-ttu-id="aff48-103">Zuerst werden erforderliche Cloudressourcen erstellt (auch als Bereitstellung bezeichnet), dann wird der Code, aus dem Ihre App besteht, in die erstellten Cloudressourcen kopiert.</span><span class="sxs-lookup"><span data-stu-id="aff48-103">First, necessary cloud resources are created (also known as provisioning), then the code that makes up your app is copied into the created cloud resources.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="aff48-104">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="aff48-104">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="aff48-105">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="aff48-105">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="aff48-106">Wählen Sie Teams Toolkit aus der Seitenleiste aus, indem Sie das Symbol Teams auswählen.</span><span class="sxs-lookup"><span data-stu-id="aff48-106">Select the Teams Toolkit from the sidebar by selecting the Teams icon.</span></span>
1. <span data-ttu-id="aff48-107">Wählen **Sie Bereitstellung in der Cloud aus.**</span><span class="sxs-lookup"><span data-stu-id="aff48-107">Select **Provision in the Cloud**.</span></span>

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

1. <span data-ttu-id="aff48-109">Wählen Sie bei Bedarf ein Abonnement aus, das für die Azure-Ressourcen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="aff48-109">If required, select a subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="aff48-110">Es gibt immer einige Azure-Ressourcen, die für das Hosten Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aff48-110">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="aff48-111">In einem Dialogfeld werden Sie gewarnt, dass beim Ausführen von Ressourcen in Azure Kosten entstehen können.</span><span class="sxs-lookup"><span data-stu-id="aff48-111">A dialog warns you that costs may be incurred when running resources in Azure.</span></span>  <span data-ttu-id="aff48-112">Drücken Sie **die Bereitstellung**.</span><span class="sxs-lookup"><span data-stu-id="aff48-112">Press **Provision**.</span></span>

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-warning.png" alt-text="Screenshot des Bereitstellungsdialogfelds.":::

   <span data-ttu-id="aff48-114">Der Bereitstellungsprozess erstellt Ressourcen in der Azure-Cloud.</span><span class="sxs-lookup"><span data-stu-id="aff48-114">The provisioning process will create resources in the Azure cloud.</span></span>  <span data-ttu-id="aff48-115">Dies dauert einige Zeit.</span><span class="sxs-lookup"><span data-stu-id="aff48-115">This will take some time.</span></span>  <span data-ttu-id="aff48-116">Sie können den Fortschritt überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen.</span><span class="sxs-lookup"><span data-stu-id="aff48-116">You can monitor the progress by watching the dialogs in the bottom right corner.</span></span>  <span data-ttu-id="aff48-117">Nach ein paar Minuten sehen Sie den folgenden Hinweis:</span><span class="sxs-lookup"><span data-stu-id="aff48-117">After a few minutes, you will see the following notice:</span></span>

   :::image type="content" source="~/assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. <span data-ttu-id="aff48-119">Nachdem die Bereitstellung abgeschlossen ist, wählen **Sie Bereitstellen in der Cloud aus.**</span><span class="sxs-lookup"><span data-stu-id="aff48-119">Once provisioning is complete, select **Deploy to the Cloud**.</span></span>  <span data-ttu-id="aff48-120">Wie bei der Bereitstellung dauert dieser Prozess einige Zeit.</span><span class="sxs-lookup"><span data-stu-id="aff48-120">As with provisioning, this process takes some time.</span></span>  <span data-ttu-id="aff48-121">Sie können den Prozess überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen.</span><span class="sxs-lookup"><span data-stu-id="aff48-121">You can monitor the process by watching the dialogs in the bottom right corner.</span></span> <span data-ttu-id="aff48-122">Nach ein paar Minuten wird eine Abschlussbenachrichtigung zu sehen sein.</span><span class="sxs-lookup"><span data-stu-id="aff48-122">After a few minutes, you will see a completion notice.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="aff48-123">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="aff48-123">Command Line</span></span>](#tab/cli)

<span data-ttu-id="aff48-124">Im Terminalfenster:</span><span class="sxs-lookup"><span data-stu-id="aff48-124">In your terminal window:</span></span>

1. <span data-ttu-id="aff48-125">Führen Sie `teamsfx provision` aus.</span><span class="sxs-lookup"><span data-stu-id="aff48-125">Run `teamsfx provision`.</span></span>

   ``` bash
   teamsfx provision
   ```

   <span data-ttu-id="aff48-126">Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement zu melden.</span><span class="sxs-lookup"><span data-stu-id="aff48-126">You may be prompted to log in to your Azure subscription.</span></span>  <span data-ttu-id="aff48-127">Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="aff48-127">If required, you will be prompted to select an Azure subscription to use for the Azure resources.</span></span>

   > [!NOTE]
   > <span data-ttu-id="aff48-128">Es gibt immer einige Azure-Ressourcen, die für das Hosten Ihrer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aff48-128">There are always some Azure resources used for hosting your app.</span></span>

1. <span data-ttu-id="aff48-129">Führen Sie `teamsfx deploy` aus.</span><span class="sxs-lookup"><span data-stu-id="aff48-129">Run `teamsfx deploy`.</span></span>

   ``` bash
   teamsfx deploy
   ```

---

> [!NOTE]
> <span data-ttu-id="aff48-130">**Was ist der Unterschied zwischen Bereitstellung und Bereitstellen?**</span><span class="sxs-lookup"><span data-stu-id="aff48-130">**What's the difference between Provision and Deploy?**</span></span>
>
> <span data-ttu-id="aff48-131">Der **Schritt Bereitstellung** erstellt Ressourcen in Azure und M365 für Ihre App, aber kein Code (HTML, CSS, JavaScript usw.) wird in die Ressourcen kopiert.</span><span class="sxs-lookup"><span data-stu-id="aff48-131">The **Provision** step will create resources in Azure and M365 for your app, but no code (HTML, CSS, JavaScript, etc.) is copied to the resources.</span></span>  <span data-ttu-id="aff48-132">Der **Schritt Bereitstellen** kopiert den Code für Ihre App in die Ressourcen, die Sie während des Bereitstellungsschritts erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="aff48-132">The **Deploy** step will copy the code for your app to the resources you created during the provision step.</span></span>  <span data-ttu-id="aff48-133">Es ist üblich, dass sie mehrmals bereitgestellt werden, ohne neue Ressourcen bereitstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="aff48-133">It is common to deploy multiple times without provisioning new resources.</span></span> <span data-ttu-id="aff48-134">Da der Bereitstellungsschritt einige Zeit in Sich nehmen kann, ist er vom Bereitstellungsschritt getrennt.</span><span class="sxs-lookup"><span data-stu-id="aff48-134">Since the provision step can take some time to complete, it is separate from the deployment step.</span></span>

<span data-ttu-id="aff48-135">Sobald die Bereitstellungs- und Bereitstellungsschritte abgeschlossen sind:</span><span class="sxs-lookup"><span data-stu-id="aff48-135">Once the provisioning and deployment steps are finished:</span></span>

1. <span data-ttu-id="aff48-136">Öffnen Visual Studio Code sie den Debugbereich (**STRG+Umschalt+D**  /  **bzw. ⇧-D** oder Ansicht **> Ausführen**)</span><span class="sxs-lookup"><span data-stu-id="aff48-136">From Visual Studio Code, open the debug panel (**Ctrl+Shift+D** / **⌘⇧-D** or **View > Run**)</span></span>
1. <span data-ttu-id="aff48-137">Wählen Sie in der Dropdownliste Startkonfiguration die Option **Remote starten (Edge)** aus.</span><span class="sxs-lookup"><span data-stu-id="aff48-137">Select **Launch Remote (Edge)** from the launch configuration drop-down.</span></span>
1. <span data-ttu-id="aff48-138">Drücken Sie die Schaltfläche Wiedergabe, um Ihre App zu starten – wird jetzt remote von Azure ausgeführt!</span><span class="sxs-lookup"><span data-stu-id="aff48-138">Press the Play button to launch your app - now running remotely from Azure!</span></span>
