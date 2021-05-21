---
title: Installieren von Moodle LMS
description: Installieren und Konfigurieren der Moodle-Integrations-App für Microsoft Teams
keywords: Teams Integrations-Plug-Ins für die Moodle-App
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: d7fddad80ca08fd4ca8dee352cdcbc46e8e97dcd
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566719"
---
# <a name="install-moodle-lms"></a><span data-ttu-id="ea9bf-104">Installieren von Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="ea9bf-104">Install Moodle LMS</span></span>

<span data-ttu-id="ea9bf-105">In diesem Artikel erfahren Sie, wie Sie das Moodle LMS installieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-105">In this article you'll learn how to install the Moodle LMS.</span></span>

> [!NOTE]
> <span data-ttu-id="ea9bf-106">Um IT-Administratoren bei der einfachen Einrichtung von Moodle und Teams zu helfen, werden Open-Source-Microsoft 365 Von Moodle-Plug-Ins für folgendes aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-106">To help IT admins to easily set-up Moodle and Teams integration, open-source Microsoft 365 Moodle Plugins is updated for the following:</span></span>
>
> * <span data-ttu-id="ea9bf-107">Automatische Registrierung Ihres Moodle-Servers [mit Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="ea9bf-107">Auto-registration of your Moodle server with [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span></span>
>
> * <span data-ttu-id="ea9bf-108">Bereitstellung Ihres Moodle-Assistenten-Bots mit einem Klick in Azure.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-108">One-click deployment of your Moodle Assistant bot to Azure.</span></span>
>
> * <span data-ttu-id="ea9bf-109">Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder Auswählen von Moodle-Kursen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-109">Auto-provisioning of teams and auto-synchronization of team enrollments for all or select Moodle courses.</span></span>
>
> * <span data-ttu-id="ea9bf-110">Automatische Installation der Registerkarte "Moodle" und des "Moodle-Assistenten"-Bots in jedem synchronisierten Team.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-110">Auto-installation of the Moodle tab and the Moodle assistant bot into each synchronized team.</span></span>
>
> <span data-ttu-id="ea9bf-111">Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie [unter Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).</span><span class="sxs-lookup"><span data-stu-id="ea9bf-111">To learn more about the functionality this integration provides, see [Microsoft Teams and Moodle](https://education.microsoft.com/resource/3dffb3a8).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea9bf-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ea9bf-112">Prerequisites</span></span>

<span data-ttu-id="ea9bf-113">Es folgen die Voraussetzungen für die Installation von Moodle:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-113">Following are the prerequisites to install Moodle:</span></span>

* <span data-ttu-id="ea9bf-114">Anmeldeinformationen für den Administrator von "Moodle".</span><span class="sxs-lookup"><span data-stu-id="ea9bf-114">Moodle administrator credentials.</span></span>

* <span data-ttu-id="ea9bf-115">Azure AD-Administratoranmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-115">Azure AD administrator credentials.</span></span>

* <span data-ttu-id="ea9bf-116">Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-116">An Azure subscription where you can create new resources.</span></span>

## <a name="1-install-the-microsoft-365-moodle-plugins"></a><span data-ttu-id="ea9bf-117">1. Installieren der Microsoft 365 Von Moodle-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="ea9bf-117">1. Install the Microsoft 365 Moodle Plugins</span></span>

<span data-ttu-id="ea9bf-118">Die Integration von Moodle in Microsoft Teams wird durch die Open [Source-Microsoft 365 von Moodle-Plug-Ins unterstützt.](https://github.com/Microsoft/o365-moodle)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-118">Moodle integration in Microsoft Teams is powered by the open source [Microsoft 365 Moodle plugins set](https://github.com/Microsoft/o365-moodle).</span></span>

### <a name="requisite-applications-and-plugins"></a><span data-ttu-id="ea9bf-119">Erforderliche Anwendungen und Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="ea9bf-119">Requisite applications and plugins</span></span>

<span data-ttu-id="ea9bf-120">Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 von Moodle-Plug-Ins fortfahren:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-120">Ensure to install and download the following before proceeding with the Microsoft 365 Moodle plugins installation:</span></span>

1. <span data-ttu-id="ea9bf-121">Stellen Sie sicher, [dass Sie eine aktuelle stabile Version von Moodle installieren.](https://download.moodle.org/releases/latest/)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-121">Ensure to install a [current stable version of Moodle](https://download.moodle.org/releases/latest/).</span></span>

1. <span data-ttu-id="ea9bf-122">Laden Sie die Moodle [OpenID-Verbinden](https://moodle.org/plugins/auth_oidc) und die Microsoft 365 Integrations-Plug-Ins auf Ihrem lokalen Computer herunter, und speichern Sie sie. [](https://moodle.org/plugins/local_o365)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-122">Download and save the Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) and the [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) plugins to your local computer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea9bf-123">Die Installation der OpenID-Verbinden und Microsoft 365 Integrations-Plug-Ins sind für die Integration Teams erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-123">Installing the OpenID Connect and Microsoft 365 Integration plugins are required for the Teams integration.</span></span>
    >
    > <span data-ttu-id="ea9bf-124">Darüber hinaus werden die [Microsoft 365 Teams Design-Plug-Ins](https://moodle.org/plugins/theme_boost_o365teams) dringend empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-124">In addition, the [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) plugins is highly recommended.</span></span>

### <a name="microsoft-365-moodle-plugins"></a><span data-ttu-id="ea9bf-125">Microsoft 365 Moodle-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="ea9bf-125">Microsoft 365 Moodle plugins</span></span>

1. <span data-ttu-id="ea9bf-126">Melden Sie sich als Administrator bei  Ihrem Moodle-Server an, und wählen Sie im Einstellungen im linken Navigationsbereich die Option Websiteverwaltung aus. [](https://docs.moodle.org/22/en/Settings_block)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-126">Sign in to your Moodle server as an administrator and select **Site administration** from the [Settings block](https://docs.moodle.org/22/en/Settings_block) located in the left navigation panel.</span></span>

1. <span data-ttu-id="ea9bf-127">Wählen Sie die **Registerkarte Plug-Ins** aus, und wählen Sie dann **Plug-Ins installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-127">Select the **Plugins** tab, and then select **Install plugins**.</span></span>

1. <span data-ttu-id="ea9bf-128">Wählen Sie **im Abschnitt Plug-Ins aus ZIP-Datei** installieren die Option Datei auswählen **aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-128">From the **Install plugins from ZIP file** section, select **Choose a file**.</span></span>

1. <span data-ttu-id="ea9bf-129">Wählen **Hochladen im** linken Navigationsbereich eine Dateioption aus, suchen Sie nach der heruntergeladenen Datei, und wählen Sie Hochladen datei **aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-129">Select **Upload a file** option from the left navigation panel, browse for the file that you downloaded, and select **Upload this file**.</span></span>

1. <span data-ttu-id="ea9bf-130">Wählen **Sie websiteverwaltung** im linken Navigationsbereich aus, um zum Administratordashboard zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-130">Select **Site administration** from the left navigation panel to return to your admin dashboard.</span></span> <span data-ttu-id="ea9bf-131">Scrollen Sie nach unten zu **den lokalen Plug-Ins,** und wählen **Sie den Link Microsoft 365 Integration** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-131">Scroll down to the **Local plugins** and select the **Microsoft 365 Integration** link.</span></span>

    > [!IMPORTANT]
    >
    > * <span data-ttu-id="ea9bf-132">Lassen Sie Microsoft 365 Die Konfigurationsseite von Moodle-Plug-Ins auf einer separaten Browserregisterkarte geöffnet, da Sie während des gesamten Prozesses zu diesem Seitensatz zurückkehren müssen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-132">Keep your Microsoft 365 Moodle Plugins configuration page open in a separate browser tab as you need to return to this set of pages throughout the process.</span></span>  
    >
    > * <span data-ttu-id="ea9bf-133">Wenn Sie über keine vorhandene Moodle-Website verfügen, wechseln Sie zum [Repository "Moodle on Azure",](https://github.com/azure/moodle) stellen Sie schnell eine Moodle-Instanz bereit, und passen Sie sie an Ihre Anforderungen an.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-133">If you do not have an existing Moodle site, go to the [Moodle on Azure](https://github.com/azure/moodle) repo, and quickly deploy a Moodle instance and customize it to your needs.</span></span>

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a><span data-ttu-id="ea9bf-134">2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plug-Ins und Azure Active Directory (Azure AD)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-134">2. Configure the connection between the Microsoft 365 plugins and Azure Active Directory (Azure AD)</span></span>

<span data-ttu-id="ea9bf-135">Sie müssen die Verbindung zwischen den Microsoft 365 und Azure AD konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-135">You must configure the connection between the Microsoft 365 plugins and Azure AD.</span></span>

### <a name="requisites"></a><span data-ttu-id="ea9bf-136">Requisiten</span><span class="sxs-lookup"><span data-stu-id="ea9bf-136">Requisites</span></span>

<span data-ttu-id="ea9bf-137">Registrieren Sie Moodle als Anwendung in Azure AD mithilfe des PowerShell-Skripts.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-137">Register Moodle as an application in your Azure AD, using the PowerShell script.</span></span> <span data-ttu-id="ea9bf-138">Das Powershell-Skript enthält Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-138">The Powershell script provisions the following:</span></span>

* <span data-ttu-id="ea9bf-139">Eine neue Azure AD-Anwendung für Microsoft 365 Mandanten, die von den Microsoft 365 Verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-139">A new Azure AD application for your Microsoft 365 tenant, which is used by the Microsoft 365 Moodle Plugins.</span></span>
* <span data-ttu-id="ea9bf-140">Die App für Microsoft 365 Mandanten, richten Sie die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein, und gibt `AppID` die und `Key` zurück.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-140">The app for your Microsoft 365 tenant, set up the required reply URLs and permissions for the provisioned app, and returns the `AppID` and `Key`.</span></span>

<span data-ttu-id="ea9bf-141">Verwenden Sie die `AppID` generierte und in Microsoft 365 Setupseite von Moodle-Plug-Ins, um Ihre `Key` Moodle-Serverwebsite mit Azure AD zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-141">Use the generated `AppID` and `Key` in your Microsoft 365 Moodle Plugins setup page to configure your Moodle server site with Azure AD.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="ea9bf-142">Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert. Daher müssen Sie die Konfiguration manuell nach den Schritten ausführen, die auf den Releaseseiten von Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-142">The PowerShell script is not updated with the latest configuration items, therefore, you must complete the configuration manually following the steps outlined in the Moodle [3.8.0.4 and 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) and [3.8.0.5 and 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) release pages.</span></span>
>
> * <span data-ttu-id="ea9bf-143">Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instanz finden Sie unter [Registrieren Ihrer Moodle-Instanz als Anwendung.](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-143">For more information on registering your Moodle instance manually, see [Register your Moodle instance as an application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span></span>

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a><span data-ttu-id="ea9bf-144">Registerkarte "Moodle" für Microsoft Teams Informationsfluss</span><span class="sxs-lookup"><span data-stu-id="ea9bf-144">The Moodle tab for Microsoft Teams information flow</span></span>

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. <span data-ttu-id="ea9bf-145">Wählen Sie auf Microsoft 365 Seite Integrations-Plug-Ins die **Registerkarte Setup** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-145">From the Microsoft 365 Integration plugins page, select the **Setup** tab.</span></span>

1. <span data-ttu-id="ea9bf-146">Wählen Sie **die Schaltfläche PowerShell-Skript herunterladen** aus, und speichern Sie sie als ZIP-Ordner auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-146">Select the **Download PowerShell Script** button and save it as a ZIP folder to your local computer.</span></span>

1. <span data-ttu-id="ea9bf-147">Bereiten Sie das PowerShell-Skript aus der ZIP-Datei wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-147">Prepare the PowerShell script from the ZIP file as follows:</span></span> 

    1. <span data-ttu-id="ea9bf-148">Laden Sie die Datei herunter, und `Moodle-AzureAD-Powershell.zip` extrahieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-148">Download and extract the `Moodle-AzureAD-Powershell.zip` file.</span></span>
    1. <span data-ttu-id="ea9bf-149">Öffnen Sie den extrahierten Ordner.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-149">Open the extracted folder.</span></span>
    1. <span data-ttu-id="ea9bf-150">Klicken Sie mit der rechten Maustaste `Moodle-AzureAD-Script.ps1` auf die Datei, und wählen Sie **Eigenschaften aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-150">Right-click on the `Moodle-AzureAD-Script.ps1` file and select **Properties**.</span></span>
    1. <span data-ttu-id="ea9bf-151">Aktivieren Sie **unter der Registerkarte** Allgemein des Fensters Eigenschaften das Kontrollkästchen neben dem `Unblock` **Security-Attribut** am unteren Rand des Fensters.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-151">Under the **General** tab of the Properties window, select the `Unblock` checkbox next to the **Security** attribute located at the bottom of the window.</span></span>
    1. <span data-ttu-id="ea9bf-152">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-152">Select **OK**.</span></span>
    1. <span data-ttu-id="ea9bf-153">Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-153">Copy the directory path to the extracted folder.</span></span>

1. <span data-ttu-id="ea9bf-154">Führen Sie PowerShell als Administrator aus:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-154">Run PowerShell as an administrator:</span></span>

    1. <span data-ttu-id="ea9bf-155">Klicken Sie auf Starten.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-155">Select Start.</span></span>
    1. <span data-ttu-id="ea9bf-156">Geben Sie PowerShell ein.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-156">Type PowerShell.</span></span>
    1. <span data-ttu-id="ea9bf-157">Klicken Sie mit der rechten Maustaste **auf Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-157">Right-click on **Windows PowerShell**.</span></span>
    1. <span data-ttu-id="ea9bf-158">Wählen **Sie Als Administrator ausführen aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-158">Select **Run as Administrator**.</span></span>

1. <span data-ttu-id="ea9bf-159">Navigieren Sie zum entzippten Verzeichnis, indem Sie `cd .../.../Moodle-AzureAD-Powershell` eingeben, `.../...` wo sich der Pfad zum Verzeichnis befindet.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-159">Navigate to the unzipped directory by typing `cd .../.../Moodle-AzureAD-Powershell` where `.../...` is the path to the directory.</span></span>

1. <span data-ttu-id="ea9bf-160">Führen Sie das PowerShell-Skript aus:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-160">Execute the PowerShell script:</span></span>

    1. <span data-ttu-id="ea9bf-161">Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` ein.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-161">Enter `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.</span></span>
    1. <span data-ttu-id="ea9bf-162">Geben Sie `./Moodle-AzureAD-Script.ps1` ein.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-162">Enter `./Moodle-AzureAD-Script.ps1`.</span></span>
    1. <span data-ttu-id="ea9bf-163">Melden Sie sich bei Microsoft 365 Administratorkonto im Popupfenster an.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-163">Sign in to your Microsoft 365 administrator account in the pop-up window.</span></span>
    1. <span data-ttu-id="ea9bf-164">Geben Sie den Namen der Azure AD-Anwendung ein, z. B. "Moodle" oder "Moodle"-Plug-Ins.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-164">Enter the name of the Azure AD Application, for example, Moodle or Moodle plugins.</span></span>
    1. <span data-ttu-id="ea9bf-165">Geben Sie die URL für Ihren Moodle-Server ein.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-165">Enter the URL for your Moodle server.</span></span>
    1. <span data-ttu-id="ea9bf-166">Kopieren Sie die vom Skript generierte **Anwendungs-ID ( `AppID` )** und den **Anwendungsschlüssel( `Key` ),** und speichern Sie sie.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-166">Copy the **Application ID (`AppID`)** and **Application Key(`Key`)** generated by the script and save them.</span></span>

1. <span data-ttu-id="ea9bf-167">Als Nächstes müssen Sie das `AppID` und zum Microsoft 365 Hinzufügen von `Key` Moodle-Plug-Ins hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-167">Next you must add the `AppID` and `Key` to the Microsoft 365 Moodle Plugins.</span></span> <span data-ttu-id="ea9bf-168">Kehren Sie zur Seite "Plug-Ins-Verwaltung", Websiteverwaltung > Plugins > Microsoft 365 Integration zurück.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-168">Return to the plugins administration page, Site administration > Plugins > Microsoft 365 Integration.</span></span>

1. <span data-ttu-id="ea9bf-169">Fügen Sie **auf der Registerkarte** Setup das -Element hinzu, das Sie zuvor kopiert `AppID` `Key` haben, und wählen Sie dann Änderungen **speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-169">On the **Setup** tab add the `AppID` and `Key` you copied previously, and then select **Save changes**.</span></span> <span data-ttu-id="ea9bf-170">Nach dem Aktualisieren der Seite wird ein neuer Abschnitt Verbindungsmethode **auswählen angezeigt.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-170">After the page refreshes, you can see a new section **Choose connection method**.</span></span>

1. <span data-ttu-id="ea9bf-171">Aktivieren Sie **in der Methode Verbindung auswählen** das Kontrollkästchen Default , und wählen Sie dann Änderungen **erneut** speichern aus. </span><span class="sxs-lookup"><span data-stu-id="ea9bf-171">In the **Choose connection method**, select the checkbox labeled **Default**, and then select **Save changes** again.</span></span>

1. <span data-ttu-id="ea9bf-172">Nach der Aktualisierung der Seite sehen Sie einen weiteren neuen Abschnitt **Administrator-Zustimmung & zusätzliche Informationen**.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-172">After the page refreshes you can see another new section **Admin consent & additional information**.</span></span>
    1. <span data-ttu-id="ea9bf-173">Wählen **Sie Link Administratorzuwilligung** bereitstellen aus, geben Microsoft 365 Anmeldeinformationen des globalen Administrators ein, und akzeptieren Sie **dann,** um die Berechtigungen zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-173">Select **Provide Admin Consent** link, enter your Microsoft 365 Global Administrator credentials, then **Accept** to grant the permissions.</span></span>
    1. <span data-ttu-id="ea9bf-174">Wählen Sie neben dem **Feld Azure AD Tenant** die Schaltfläche **Erkennen** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-174">Next to the **Azure AD Tenant** field, select the **Detect** button.</span></span>
    1. <span data-ttu-id="ea9bf-175">Wählen Sie neben **OneDrive for Business URL** die Schaltfläche **Erkennen** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-175">Next to the **OneDrive for Business URL**, select the **Detect** button.</span></span>
    1. <span data-ttu-id="ea9bf-176">Nachdem die Felder auffüllt sind, wählen Sie erneut die Schaltfläche **Änderungen** speichern aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-176">After the fields populate, select the **Save changes** button again.</span></span>

1. <span data-ttu-id="ea9bf-177">Wählen Sie die **Schaltfläche Aktualisieren** aus, um die Installation zu überprüfen, und wählen Sie dann Änderungen **speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-177">Select the **Update** button to verify the installation, and then select **Save changes**.</span></span>

1. <span data-ttu-id="ea9bf-178">Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-178">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="ea9bf-179">Erste Schritte:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-179">To get started:</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea9bf-180">Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-180">Depending on your environment, you can select different options during this stage.</span></span>

1. <span data-ttu-id="ea9bf-181">Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-181">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="ea9bf-182">Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-182">Depending on your environment, you can select different options during this stage.</span></span> <span data-ttu-id="ea9bf-183">Erste Schritte:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-183">To get started:</span></span>
    1. <span data-ttu-id="ea9bf-184">Wechseln Sie zur **Registerkarte Einstellungen Synchronisieren.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-184">Switch to the **Sync Settings tab**.</span></span>

    1. <span data-ttu-id="ea9bf-185">Aktivieren Sie **im Abschnitt Benutzer mit Azure AD** synchronisieren die Kontrollkästchen, die für Ihre Umgebung gelten.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-185">In the **Sync users with Azure AD** section, select the checkboxes that apply to your environment.</span></span> <span data-ttu-id="ea9bf-186">Sie müssen Folgendes auswählen:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-186">You must select the following:</span></span>  

        <span data-ttu-id="ea9bf-187">✔ Erstellen von Konten in Moodle für Benutzer in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-187">✔ Create accounts in Moodle for users in Azure AD.</span></span>

        <span data-ttu-id="ea9bf-188">✔ Aktualisieren aller Konten in Moodle für Benutzer in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-188">✔ Update all accounts in Moodle for users in Azure AD.</span></span>

    1. <span data-ttu-id="ea9bf-189">Im Abschnitt **Einschränkung der** Benutzererstellung können Sie einen Filter einrichten, um die Azure AD-Benutzer zu beschränken, die mit Moodle synchronisiert sind.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-189">In the **User Creation Restriction** section, you can setup a filter to limit the Azure AD users that is synced to Moodle.</span></span>
    1. <span data-ttu-id="ea9bf-190">Im **Abschnitt Benutzerfeldzuordnung** können Sie die Azure AD an die Zuordnung von Moodle-Benutzerprofilen anpassen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-190">The **User Field Mapping** section allows you to customize the Azure AD to Moodle User Profile field mapping.</span></span>
    1. <span data-ttu-id="ea9bf-191">Im Abschnitt **Teams Synchronisierung** können Sie auswählen, dass automatisch Gruppen erstellt werden, z. B. Teams für einige oder alle Ihrer vorhandenen Moodle-Kurse.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-191">In the **Teams Sync** section, you can select to automatically create Groups, such as teams for some, or all, of your existing Moodle courses.</span></span>

13. <span data-ttu-id="ea9bf-192">Wählen Sie zum Überprüfen [von Aufträgen](https://docs.moodle.org/310/en/Cron) und zum  manuellen Ausführen dieser Aufträge für die erste Ausführung den Link Verwaltung geplanter Aufgaben im Abschnitt Synchronisieren von Benutzern **mit Azure AD** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-192">To validate [cron](https://docs.moodle.org/310/en/Cron) jobs and run them manually for the first run, select the **Scheduled tasks management page** link in the **Sync users with Azure AD** section.</span></span> <span data-ttu-id="ea9bf-193">Dadurch gelangen Sie zur **Seite Geplante Vorgänge.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-193">This takes you to the **Scheduled Tasks** page.</span></span>

    1. <span data-ttu-id="ea9bf-194">Scrollen Sie nach unten, und suchen Sie den **Auftrag Benutzer mit Azure AD** synchronisieren, und wählen Sie Jetzt ausführen **aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-194">Scroll down and find the **Sync users with Azure AD** job and select **Run now**.</span></span>
    1. <span data-ttu-id="ea9bf-195">Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch das Erstellen von Benutzergruppen **in einem Microsoft 365** ausführen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-195">If you select to create Groups based on existing courses, you can also run the **Create user groups in Microsoft 365** job.</span></span>

    > [!NOTE]
    >
    > <span data-ttu-id="ea9bf-196">Der [Moodle-Cron wird](https://docs.moodle.org/310/en/Cron) gemäß dem Vorgangszeitplan ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-196">The Moodle [Cron](https://docs.moodle.org/310/en/Cron) runs according to the task schedule.</span></span> <span data-ttu-id="ea9bf-197">Der Standardzeitplan ist einmal pro Tag.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-197">The default schedule is once a day.</span></span> <span data-ttu-id="ea9bf-198">Der cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-198">However, the cron must run more frequently to keep everything in sync.</span></span>

1. <span data-ttu-id="ea9bf-199">Kehren Sie zur Seite "Plug-Ins"-Verwaltung, **Websiteverwaltung > Plugins > Microsoft 365 Integration** zurück, und wählen Sie die Seite **Teams Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-199">Return to the plugins administration page, **Site administration > Plugins > Microsoft 365 Integration**, and select the **Teams Settings** page.</span></span>

1. <span data-ttu-id="ea9bf-200">Konfigurieren Sie **auf Teams Einstellungen** Seite die erforderlichen Einstellungen, um die Integration der Teams zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-200">On the **Teams Settings** page, configure the required settings to enable the Teams app integration.</span></span>

    1. <span data-ttu-id="ea9bf-201">Um **OpenID Verbinden** zu aktivieren,  wählen Sie den Link Authentifizierung verwalten aus, und wählen Sie das Augensymbol in der **Zeile OpenId Verbinden** aus, wenn es ausgegraut ist.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-201">To enable **OpenID Connect**, select the **Manage Authentication** link, and select the eye icon on the **OpenId Connect** line if it is greyed out.</span></span>
    1. <span data-ttu-id="ea9bf-202">Um die Frameeinbettung zu aktivieren, wählen Sie den **Link HTTP-Sicherheit** aus, und aktivieren Sie dann das Kontrollkästchen neben **Frameeinbettung zulassen.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-202">To enable frame embedding, select the **HTTP Security** link, and then select the checkbox next to **Allow frame embedding**.</span></span>
    1. <span data-ttu-id="ea9bf-203">Um Webdienste zu aktivieren, die die Funktionen der Moodle-API aktivieren, wählen Sie den Link **Erweiterte Features** aus, und stellen Sie dann sicher, dass das Kontrollkästchen neben Webdienste **aktivieren** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-203">To enable web services, which enables the Moodle API features, select the **Advanced Features** link, and then ensure the checkbox next to **Enable web services** is selected.</span></span>
    1. <span data-ttu-id="ea9bf-204">Um die externen Dienste für Microsoft 365 zu aktivieren, wählen Sie den Link **Externe** Dienste aus, und wählen Sie dann:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-204">To enable the external services for Microsoft 365, select the **External services** link, and then:</span></span>  

        <span data-ttu-id="ea9bf-205">✔ Wählen Sie **bearbeiten** in der Zeile **"Moodle Microsoft 365 Webservices"** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-205">✔ Select **Edit** on the **Moodle Microsoft 365 Webservices** row.</span></span>

        <span data-ttu-id="ea9bf-206">✔ Aktivieren Sie das Kontrollkästchen neben **Aktiviert,** und wählen Sie **dann Änderungen speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-206">✔ Select the checkbox next to **Enabled**, then select **Save Changes**</span></span>

    1. <span data-ttu-id="ea9bf-207">Bearbeiten Sie ihre authentifizierten Benutzerberechtigungen, damit sie Webdiensttoken erstellen können.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-207">Edit your authenticated user permissions to allow them to create web service tokens.</span></span>

        <span data-ttu-id="ea9bf-208">✔ Wählen Sie den **Link Bearbeitungsrolle Authentifizierter Benutzer** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-208">✔ Select the **Editing role Authenticated user** link.</span></span>

        <span data-ttu-id="ea9bf-209">✔ Scrollen Sie nach unten, und suchen Sie die Funktion **Webdiensttoken** erstellen, und aktivieren Sie das **Kontrollkästchen Zulassen.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-209">✔ Scroll down and find the **Create a web service token** capability and select the **Allow** checkbox.</span></span>

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a><span data-ttu-id="ea9bf-210">3. Bereitstellen des "Moodle Assistant Bot" in Azure</span><span class="sxs-lookup"><span data-stu-id="ea9bf-210">3. Deploy the Moodle Assistant Bot to Azure</span></span>

<span data-ttu-id="ea9bf-211">Der kostenlose Moodle-Assistent-Bot für Microsoft Teams hilft Lehrern und Schülern, Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-211">The free Moodle assistant bot for Microsoft Teams helps teachers and students answer questions about their courses, assignments, grades, and other information in Moodle.</span></span> <span data-ttu-id="ea9bf-212">Der Bot sendet auch Moodle-Benachrichtigungen an Schüler und Lehrer innerhalb Teams.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-212">The bot also sends Moodle notifications to students and teachers within Teams.</span></span> <span data-ttu-id="ea9bf-213">Der Bot ist ein von Microsoft verwaltetes Open-Source-Projekt, das unter [GitHub.](https://github.com/microsoft/Moodle-Teams-Bot)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-213">The bot is an open-source project maintained by Microsoft, and is available on [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).</span></span>

> [!NOTE]
>
> * <span data-ttu-id="ea9bf-214">Stellen Sie Ressourcen für Ihr Azure-Abonnement bereit.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-214">Deploy resources to your Azure subscription.</span></span> <span data-ttu-id="ea9bf-215">Alle Ressourcen wurden mithilfe der kostenlosen **Ebene** konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-215">All resources were configured using the **free** tier.</span></span> <span data-ttu-id="ea9bf-216">Je nach Verwendung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-216">Depending on the usage of your bot, you may have to scale these resources.</span></span>
>
> * <span data-ttu-id="ea9bf-217">Um die Registerkarte "Moodle" ohne den Bot zu verwenden, fahren Sie mit [4 aus.](#4-deploy-your-microsoft-teams-app)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-217">To use the Moodle tab without the bot, skip to [4](#4-deploy-your-microsoft-teams-app).</span></span>

### <a name="moodle-bot-information-flow"></a><span data-ttu-id="ea9bf-218">Informationen zum Moodle-Bot</span><span class="sxs-lookup"><span data-stu-id="ea9bf-218">Moodle bot information flow</span></span>

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

<span data-ttu-id="ea9bf-219">Zum Installieren des Bots müssen Sie ihn auf der [Microsoft Identity Platform registrieren.](https://identity.microsoft.com/Landing)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-219">To install the bot, you must register it on the [Microsoft Identity Platform](https://identity.microsoft.com/Landing).</span></span> <span data-ttu-id="ea9bf-220">Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-220">This allows your bot to authenticate against your Microsoft endpoints.</span></span> 

<span data-ttu-id="ea9bf-221">**So registrieren Sie Ihren Bot**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-221">**To register your bot**</span></span>

1. <span data-ttu-id="ea9bf-222">Wechseln Sie zur Verwaltungsseite der Plugins, und wählen Sie dann **Plug-Ins aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-222">Go to the plugins administration page, and then select **Plugins**.</span></span> <span data-ttu-id="ea9bf-223">Wählen **Microsoft 365 Integration** die Registerkarte **Teams Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-223">Under **Microsoft 365 Integration**, select the **Teams Settings** tab.</span></span>

1. <span data-ttu-id="ea9bf-224">Wählen Sie den **Link Microsoft Application Registration Portal** aus, und melden Sie sich mit Ihrer Microsoft-ID an.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-224">Select the **Microsoft Application Registration Portal** link and sign in with your Microsoft ID.</span></span>

1. <span data-ttu-id="ea9bf-225">Geben Sie einen Namen für Ihre App ein, z. B. "MoodleBot", und wählen Sie die **Schaltfläche Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-225">Enter a name for your app, such as MoodleBot and select the **Create** button.</span></span>

1. <span data-ttu-id="ea9bf-226">Kopieren Sie **die Anwendungs-ID,** und fügen Sie sie auf der Seite **Teamanwendungs-ID Einstellungen** ein. </span><span class="sxs-lookup"><span data-stu-id="ea9bf-226">Copy the **Application ID** and paste it into the **Bot Application ID** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="ea9bf-227">Wählen Sie die **Schaltfläche Neues Kennwort generieren** aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-227">Select the **Generate New Password** button.</span></span> <span data-ttu-id="ea9bf-228">Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld **Botanwendungskennwort** auf der **Einstellungen** ein.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-228">Copy the generated password and and paste it into the **Bot Application Password** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="ea9bf-229">Scrollen Sie zum unteren Rand des Formulars, und wählen **Sie Änderungen speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-229">Scroll to the bottom of the form and select **Save Changes**.</span></span>

<span data-ttu-id="ea9bf-230">Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-230">After generating your application ID and password, deploy your bot to Azure:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ea9bf-231">Wählen **Sie Bereitstellen in Azure** aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. der Botanwendungs-ID, dem Botanwendungskennwort und dem geheimen "Moodle"-Teams Einstellungen Seite. </span><span class="sxs-lookup"><span data-stu-id="ea9bf-231">Select **Deploy to Azure** and complete the form with the necessary information, such as the Bot Application ID, Bot Application Password, and the Moodle Secret on the **Teams Settings** page.</span></span> <span data-ttu-id="ea9bf-232">Die Azure-Informationen finden Sie auf der **Seite Setup.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-232">The Azure information is on the **Setup** page.</span></span> 
> * <span data-ttu-id="ea9bf-233">Aktivieren Sie nach Dem Ausfüllen des Formulars das Kontrollkästchen, um den Allgemeinen Geschäftsbedingungen zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-233">After completing the form, select the checkbox to agree to the terms and conditions.</span></span>
> * <span data-ttu-id="ea9bf-234">Wählen Sie **Kaufen aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-234">Select **Purchase**.</span></span> <span data-ttu-id="ea9bf-235">Alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-235">All Azure resources are deployed to the free tier.</span></span>

<span data-ttu-id="ea9bf-236">Nachdem die Bereitstellung der Ressourcen in Azure abgeschlossen ist, müssen Sie die Microsoft 365 von Moodle mit einem Messagingendpunkt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-236">After the resources have completed deploying to Azure, you must configure the Microsoft 365 Moodle plugins with a messaging endpoint.</span></span> <span data-ttu-id="ea9bf-237">Sie müssen den Endpunkt von Ihrem Bot in Azure erhalten:</span><span class="sxs-lookup"><span data-stu-id="ea9bf-237">You must get the endpoint from your bot in Azure:</span></span>

1. <span data-ttu-id="ea9bf-238">Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-238">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

1. <span data-ttu-id="ea9bf-239">Wählen Sie im linken Bereich **Ressourcengruppen aus,** und wählen Sie die Ressourcengruppe aus, die Sie beim Bereitstellen des Bots verwendet oder erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-239">In the left pane, select **Resource groups** and select the resource group you used or created, while deploying your bot.</span></span>

1. <span data-ttu-id="ea9bf-240">Wählen Sie **die WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-240">Select the **WebApp Bot** resource from the list of resources in the group.</span></span>

1. <span data-ttu-id="ea9bf-241">Kopieren Sie **den Messagingendpunkt** aus dem **Abschnitt** Übersicht.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-241">Copy the **Messaging Endpoint** from the **Overview** section.</span></span>

1. <span data-ttu-id="ea9bf-242">Öffnen Sie in Moodle die **Seite Team Einstellungen** Ihrer Microsoft 365-Plug-Ins.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-242">In Moodle, open the **Team Settings** page of your Microsoft 365 Moodle Plugins.</span></span>

1. <span data-ttu-id="ea9bf-243">Fügen Sie **im Feld BotEndpunkt** die URL ein, die Sie gerade kopiert haben, und ändern Sie das Wort *Nachrichten* in *Webhook*.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-243">In the **Bot Endpoint** field paste the URL you just copied and change the word *messages* to *webhook*.</span></span> <span data-ttu-id="ea9bf-244">Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`</span><span class="sxs-lookup"><span data-stu-id="ea9bf-244">The URL must appear as follows: `https://botname.azurewebsites.net/api/webhook`</span></span>

1. <span data-ttu-id="ea9bf-245">Wählen **Sie Änderungen speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-245">Select **Save Changes**.</span></span>

1. <span data-ttu-id="ea9bf-246">Wechseln Sie nach dem Speichern der Änderungen zur Registerkarte  Team Einstellungen, wählen Sie die Schaltfläche Manifestdatei herunterladen aus, und speichern Sie das **App-Manifestpaket** zur weiteren Verwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-246">After saving the changes, go back to the **Team Settings** tab, select the **Download manifest file** button, and save the app manifest package to your computer for further use.</span></span>

## <a name="4-deploy-your-microsoft-teams-app"></a><span data-ttu-id="ea9bf-247">4. Bereitstellen ihrer Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="ea9bf-247">4. Deploy your Microsoft Teams app</span></span>

<span data-ttu-id="ea9bf-248">Nachdem Ihr Bot in Azure bereitgestellt und für das Sprechen mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-248">After your bot deployed to Azure and configured to talk to your Moodle server, you must deploy your Microsoft Teams app.</span></span> <span data-ttu-id="ea9bf-249">Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Microsoft 365 -Seite des Moodle-Plug-Ins-Einstellungen heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-249">To do this you must load the app manifest file that you downloaded from the Microsoft 365 Moodle Plugins Team Settings page in the previous step.</span></span>

<span data-ttu-id="ea9bf-250">Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-250">Before you install the app you must ensure to enable external apps and uploading of apps.</span></span> <span data-ttu-id="ea9bf-251">Weitere Informationen finden Sie unter [Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="ea9bf-251">For more information, see [Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span> 

<span data-ttu-id="ea9bf-252">**So stellen Sie Ihre App zur Bereitstellung**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-252">**To deploy your app**</span></span> 

1. <span data-ttu-id="ea9bf-253">Öffnen **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-253">Open **Microsoft Teams**.</span></span> 

1. <span data-ttu-id="ea9bf-254">Wählen Sie **im** unteren linken Bereich der Navigationsleiste das Symbol App aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-254">Select the **App** icon on the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="ea9bf-255">Wählen Sie **Hochladen einen benutzerdefinierten App-Link** aus der Liste der Optionen aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-255">Select the **Upload a custom app** link from the list of options.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ea9bf-256">Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen, andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-256">If you are logged in as a global administrator, you must have the option of uploading the app to your organization's app catalog, otherwise you can only load the app for a team in which you are a member.</span></span>

4. <span data-ttu-id="ea9bf-257">Wählen Sie das `manifest.zip` paket aus, das Sie zuvor heruntergeladen haben, und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-257">Select the `manifest.zip` package you downloaded previously and select **Save**.</span></span> <span data-ttu-id="ea9bf-258">Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie auf der Registerkarte **Team Einstellungen** der Konfigurationsseite für Plug-Ins in Moodle herunterladen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-258">If you have not downloaded the app manifest package, you can download from the **Team Settings** tab of the plugins configuration page in Moodle.</span></span>

<span data-ttu-id="ea9bf-259">Nachdem Sie die App installiert haben, können Sie die Registerkarte zu jedem Kanal hinzufügen, auf den Sie Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-259">Now that you have the app installed, you can add the tab to any channel that you have access to.</span></span> <span data-ttu-id="ea9bf-260">Navigieren Sie dazu zum Kanal, wählen Sie das **Plussymbol** (➕) aus, und wählen Sie Ihre App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-260">To do so, navigate to the channel, select the **plus** (➕) symbol and select your app from the list.</span></span> <span data-ttu-id="ea9bf-261">Folgen Sie den Eingabeaufforderungen, um das Hinzufügen Ihrer Registerkarte "Moodle-Kurs" zu einem Kanal zu beenden.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-261">Follow the prompts to finish adding your Moodle course tab to a channel.</span></span>

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a><span data-ttu-id="ea9bf-262">5. Automatisches Erstellen von Registerkarten von "Moodle" in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ea9bf-262">5. Allow automatic creation of Moodle tabs in Microsoft Teams</span></span>

<span data-ttu-id="ea9bf-263">Obwohl die Registerkarten "Moodle" manuell in Microsoft Teams erstellt werden, können Sie sie automatisch erstellen, wenn Teams aus der Kurssynchronisierung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-263">Although the Moodle tabs are created manually in Microsoft Teams, you can decide to create them automatically when teams are created from course synchronization.</span></span> <span data-ttu-id="ea9bf-264">Dazu müssen Sie die ID der hochgeladenen app Microsoft Teams in Moodle konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-264">To do this, you must configure the ID of the uploaded Microsoft Teams app in Moodle.</span></span>

<span data-ttu-id="ea9bf-265">**So ermöglichen Sie die automatische Erstellung von Registerkarten für "Moodle"**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-265">**To allow automatic creation of Moodle tabs**</span></span>

1. <span data-ttu-id="ea9bf-266">Öffnen Sie Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-266">Open Microsoft Teams.</span></span>

1. <span data-ttu-id="ea9bf-267">Wählen Sie im unteren linken Bereich der Navigationsleiste das Symbol Apps aus.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-267">Select the Apps icon from the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="ea9bf-268">Suchen Sie die hochgeladene **Moodle->** wählen **Sie** das Optionssymbol aus, > Link **kopieren auswählen.**</span><span class="sxs-lookup"><span data-stu-id="ea9bf-268">Locate the uploaded **Moodle app** > select the **options** icon > select **copy link**.</span></span>

1. <span data-ttu-id="ea9bf-269">Fügen Sie in einem Texteditor den kopierten Inhalt ein.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-269">In a text editor, paste the copied content.</span></span> <span data-ttu-id="ea9bf-270">Sie muss eine URL wie ht-&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-270">It must contain a URL such as ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span></span> <span data-ttu-id="ea9bf-271">Kopieren Sie den letzten Teil der URL, z. B. , der die `00112233-4455-6677-8899-aabbccddeeff` ID der Microsoft Teams ist.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-271">Copy the last part of the URL, such as  `00112233-4455-6677-8899-aabbccddeeff`, which is the ID of the Microsoft Teams app.</span></span>

1. <span data-ttu-id="ea9bf-272">Öffnen Sie in Moodle die **Registerkarte Teams Der App-Microsoft 365** von Moodle-Plug-Ins.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-272">In Moodle, open the **Teams Moodle app** tab from your Microsoft 365 Moodle Plugins configuration page.</span></span>

1. <span data-ttu-id="ea9bf-273">Fügen Sie die ID der Microsoft Teams in das Feld App-ID von Moodle ein, und speichern Sie Änderungen.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-273">Paste the ID of the Microsoft Teams app into the Moodle app ID field, and save changes.</span></span>

<span data-ttu-id="ea9bf-274">Wenn ein Moodle-Kurs synchronisiert wird, installiert Microsoft Teams automatisch die Moodle-App im Team, erstellt eine Registerkarte "Moodle" im Kanal Allgemein von Teams und konfiguriert sie so, dass sie die Kursseite für den Kurs "Moodle" enthält, von dem aus er synchronisiert wird.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-274">When a Moodle course is synced, Microsoft Teams automatically installs the Moodle app in the team, creates a Moodle tab in the General channel of Teams, and configures it to contain the course page for the Moodle course from which it is synced.</span></span> <span data-ttu-id="ea9bf-275">Sie können jetzt direkt von der Website aus mit Ihren Moodle-Kursen Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ea9bf-275">You can now start working with your Moodle courses directly from Microsoft Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="ea9bf-276">Wenn Sie Featureanforderungen oder Feedback an uns senden möchten, besuchen Sie unsere [User Voice-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).</span><span class="sxs-lookup"><span data-stu-id="ea9bf-276">To share any feature requests or feedback with us, visit our [User Voice page](https://microsoftteams.uservoice.com/forums/916759-moodle).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea9bf-277">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ea9bf-277">See also</span></span>

- [<span data-ttu-id="ea9bf-278">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="ea9bf-278">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
- [<span data-ttu-id="ea9bf-279">Moodle</span><span class="sxs-lookup"><span data-stu-id="ea9bf-279">Moodle</span></span>](https://moodle.org/)
- <span data-ttu-id="ea9bf-280">[Dokumentation zu "Moodle".](https://docs.moodle.org/34/en/Installing_plugins)</span><span class="sxs-lookup"><span data-stu-id="ea9bf-280">[Moodle documentation](https://docs.moodle.org/34/en/Installing_plugins).</span></span>

