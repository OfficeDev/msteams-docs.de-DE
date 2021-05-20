---
title: Installieren von Moodle LMS
description: So installieren und konfigurieren Sie die Moodle-Integrations-App für Microsoft Teams
keywords: Teams Moodle App-Integrations-Plugins
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
# <a name="install-moodle-lms"></a><span data-ttu-id="0761e-104">Installieren von Moodle LMS</span><span class="sxs-lookup"><span data-stu-id="0761e-104">Install Moodle LMS</span></span>

<span data-ttu-id="0761e-105">In diesem Artikel erfahren Sie, wie Sie das Moodle LMS installieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-105">In this article you'll learn how to install the Moodle LMS.</span></span>

> [!NOTE]
> <span data-ttu-id="0761e-106">Um IT-Administratoren bei der einfachen Einrichtung von Moodle und Teams-Integration zu unterstützen, werden Open-Source-Microsoft 365 Moodle Plugins für Folgendes aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="0761e-106">To help IT admins to easily set-up Moodle and Teams integration, open-source Microsoft 365 Moodle Plugins is updated for the following:</span></span>
>
> * <span data-ttu-id="0761e-107">Automatische Registrierung Ihres Moodle-Servers mit [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span><span class="sxs-lookup"><span data-stu-id="0761e-107">Auto-registration of your Moodle server with [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).</span></span>
>
> * <span data-ttu-id="0761e-108">Ein-Klick-Bereitstellung Ihres Moodle Assistant-Bots in Azure.</span><span class="sxs-lookup"><span data-stu-id="0761e-108">One-click deployment of your Moodle Assistant bot to Azure.</span></span>
>
> * <span data-ttu-id="0761e-109">Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder ausgewählte Moodle-Kurse.</span><span class="sxs-lookup"><span data-stu-id="0761e-109">Auto-provisioning of teams and auto-synchronization of team enrollments for all or select Moodle courses.</span></span>
>
> * <span data-ttu-id="0761e-110">Automatische Installation der Moodle-Registerkarte und des Moodle-Assistenten-Bots in jedes synchronisierte Team.</span><span class="sxs-lookup"><span data-stu-id="0761e-110">Auto-installation of the Moodle tab and the Moodle assistant bot into each synchronized team.</span></span>
>
> <span data-ttu-id="0761e-111">Weitere Informationen zu den Funktionen dieser Integration finden Sie unter [Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).</span><span class="sxs-lookup"><span data-stu-id="0761e-111">To learn more about the functionality this integration provides, see [Microsoft Teams and Moodle](https://education.microsoft.com/resource/3dffb3a8).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0761e-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0761e-112">Prerequisites</span></span>

<span data-ttu-id="0761e-113">Im Folgenden sind die Voraussetzungen für die Installation von Moodle:</span><span class="sxs-lookup"><span data-stu-id="0761e-113">Following are the prerequisites to install Moodle:</span></span>

* <span data-ttu-id="0761e-114">Moodle-Administratoranmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="0761e-114">Moodle administrator credentials.</span></span>

* <span data-ttu-id="0761e-115">Azure AD-Administratoranmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="0761e-115">Azure AD administrator credentials.</span></span>

* <span data-ttu-id="0761e-116">Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="0761e-116">An Azure subscription where you can create new resources.</span></span>

## <a name="1-install-the-microsoft-365-moodle-plugins"></a><span data-ttu-id="0761e-117">1. Installieren Sie die Microsoft 365 Moodle Plugins</span><span class="sxs-lookup"><span data-stu-id="0761e-117">1. Install the Microsoft 365 Moodle Plugins</span></span>

<span data-ttu-id="0761e-118">Moodle Integration in Microsoft Teams wird durch die Open-Source-Microsoft 365 [Moodle Plugins gesetzt](https://github.com/Microsoft/o365-moodle)angetrieben.</span><span class="sxs-lookup"><span data-stu-id="0761e-118">Moodle integration in Microsoft Teams is powered by the open source [Microsoft 365 Moodle plugins set](https://github.com/Microsoft/o365-moodle).</span></span>

### <a name="requisite-applications-and-plugins"></a><span data-ttu-id="0761e-119">Erforderliche Anwendungen und Plugins</span><span class="sxs-lookup"><span data-stu-id="0761e-119">Requisite applications and plugins</span></span>

<span data-ttu-id="0761e-120">Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 Moodle-Plugins fortfahren:</span><span class="sxs-lookup"><span data-stu-id="0761e-120">Ensure to install and download the following before proceeding with the Microsoft 365 Moodle plugins installation:</span></span>

1. <span data-ttu-id="0761e-121">Stellen Sie sicher, dass Sie eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/)installieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-121">Ensure to install a [current stable version of Moodle](https://download.moodle.org/releases/latest/).</span></span>

1. <span data-ttu-id="0761e-122">Laden Sie die Moodle [OpenID Verbinden](https://moodle.org/plugins/auth_oidc) und die [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) Plugins auf Ihren lokalen Computer herunter und speichern Sie sie.</span><span class="sxs-lookup"><span data-stu-id="0761e-122">Download and save the Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) and the [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) plugins to your local computer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0761e-123">Für die Teams-Integration sind die Installation der OpenID-Verbinden und Microsoft 365 Integration-Plugins erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0761e-123">Installing the OpenID Connect and Microsoft 365 Integration plugins are required for the Teams integration.</span></span>
    >
    > <span data-ttu-id="0761e-124">Darüber hinaus ist die [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) Plugins sehr zu empfehlen.</span><span class="sxs-lookup"><span data-stu-id="0761e-124">In addition, the [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) plugins is highly recommended.</span></span>

### <a name="microsoft-365-moodle-plugins"></a><span data-ttu-id="0761e-125">Microsoft 365 Moodle Plugins</span><span class="sxs-lookup"><span data-stu-id="0761e-125">Microsoft 365 Moodle plugins</span></span>

1. <span data-ttu-id="0761e-126">Melden Sie sich bei Ihrem Moodle-Server als Administrator an, und wählen Sie **Siteadministration** aus dem [Einstellungen-Block](https://docs.moodle.org/22/en/Settings_block) im linken Navigationsbereich aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-126">Sign in to your Moodle server as an administrator and select **Site administration** from the [Settings block](https://docs.moodle.org/22/en/Settings_block) located in the left navigation panel.</span></span>

1. <span data-ttu-id="0761e-127">Wählen Sie die Registerkarte **Plugins** aus, und wählen Sie dann **Plugins installieren**.</span><span class="sxs-lookup"><span data-stu-id="0761e-127">Select the **Plugins** tab, and then select **Install plugins**.</span></span>

1. <span data-ttu-id="0761e-128">Wählen Sie im Abschnitt Installieren von **Plugins aus ZIP-Dateien** **eine Datei auswählen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-128">From the **Install plugins from ZIP file** section, select **Choose a file**.</span></span>

1. <span data-ttu-id="0761e-129">Wählen Sie **Hochladen Dateioption** aus dem linken Navigationsbereich aus, suchen Sie nach der heruntergeladenen Datei, und wählen Sie **Hochladen diese Datei** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-129">Select **Upload a file** option from the left navigation panel, browse for the file that you downloaded, and select **Upload this file**.</span></span>

1. <span data-ttu-id="0761e-130">Wählen Sie **Siteadministration** im linken Navigationsbereich aus, um zu Ihrem Admin-Dashboard zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="0761e-130">Select **Site administration** from the left navigation panel to return to your admin dashboard.</span></span> <span data-ttu-id="0761e-131">Scrollen Sie nach unten zu den **lokalen Plugins** und wählen Sie den **Link Microsoft 365 Integration** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-131">Scroll down to the **Local plugins** and select the **Microsoft 365 Integration** link.</span></span>

    > [!IMPORTANT]
    >
    > * <span data-ttu-id="0761e-132">Halten Sie Ihre Microsoft 365 Moodle Plugins Konfigurationsseite in einer separaten Browser-Registerkarte geöffnet, wie Sie zu diesem Satz von Seiten während des gesamten Prozesses zurückkehren müssen.</span><span class="sxs-lookup"><span data-stu-id="0761e-132">Keep your Microsoft 365 Moodle Plugins configuration page open in a separate browser tab as you need to return to this set of pages throughout the process.</span></span>  
    >
    > * <span data-ttu-id="0761e-133">Wenn Sie nicht über eine vorhandene Moodle-Site verfügen, wechseln Sie zum [Moodle on](https://github.com/azure/moodle) Azure-Repository, und stellen Sie schnell eine Moodle-Instanz bereit, und passen Sie sie an Ihre Anforderungen an.</span><span class="sxs-lookup"><span data-stu-id="0761e-133">If you do not have an existing Moodle site, go to the [Moodle on Azure](https://github.com/azure/moodle) repo, and quickly deploy a Moodle instance and customize it to your needs.</span></span>

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a><span data-ttu-id="0761e-134">2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plugins und Azure Active Directory (Azure AD)</span><span class="sxs-lookup"><span data-stu-id="0761e-134">2. Configure the connection between the Microsoft 365 plugins and Azure Active Directory (Azure AD)</span></span>

<span data-ttu-id="0761e-135">Sie müssen die Verbindung zwischen den Microsoft 365-Plugins und Azure AD konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-135">You must configure the connection between the Microsoft 365 plugins and Azure AD.</span></span>

### <a name="requisites"></a><span data-ttu-id="0761e-136">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0761e-136">Requisites</span></span>

<span data-ttu-id="0761e-137">Registrieren Sie Moodle mithilfe des PowerShell-Skripts als Anwendung in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0761e-137">Register Moodle as an application in your Azure AD, using the PowerShell script.</span></span> <span data-ttu-id="0761e-138">Das Powershell-Skript sieht Folgendes vor:</span><span class="sxs-lookup"><span data-stu-id="0761e-138">The Powershell script provisions the following:</span></span>

* <span data-ttu-id="0761e-139">Eine neue Azure AD-Anwendung für Ihren Microsoft 365-Mandanten, der von den Microsoft 365 Moodle-Plugins verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0761e-139">A new Azure AD application for your Microsoft 365 tenant, which is used by the Microsoft 365 Moodle Plugins.</span></span>
* <span data-ttu-id="0761e-140">Die App für Ihren Microsoft 365 Mandanten, richten Sie die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein, und gibt die `AppID` und `Key` zurück.</span><span class="sxs-lookup"><span data-stu-id="0761e-140">The app for your Microsoft 365 tenant, set up the required reply URLs and permissions for the provisioned app, and returns the `AppID` and `Key`.</span></span>

<span data-ttu-id="0761e-141">Verwenden Sie die generierte `AppID` und auf Ihrer Microsoft 365 `Key` Moodle Plugins-Setupseite, um Ihre Moodle-Serversite mit Azure AD zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-141">Use the generated `AppID` and `Key` in your Microsoft 365 Moodle Plugins setup page to configure your Moodle server site with Azure AD.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="0761e-142">Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert, daher müssen Sie die Konfiguration manuell nach den Schritten in den Releaseseiten Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) ausführen.</span><span class="sxs-lookup"><span data-stu-id="0761e-142">The PowerShell script is not updated with the latest configuration items, therefore, you must complete the configuration manually following the steps outlined in the Moodle [3.8.0.4 and 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) and [3.8.0.5 and 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) release pages.</span></span>
>
> * <span data-ttu-id="0761e-143">Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instance finden Sie unter [Registrieren Ihrer Moodle-Instance als Anwendung](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span><span class="sxs-lookup"><span data-stu-id="0761e-143">For more information on registering your Moodle instance manually, see [Register your Moodle instance as an application](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).</span></span>

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a><span data-ttu-id="0761e-144">Die Registerkarte Moodle für Microsoft Teams Informationsfluss</span><span class="sxs-lookup"><span data-stu-id="0761e-144">The Moodle tab for Microsoft Teams information flow</span></span>

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. <span data-ttu-id="0761e-145">Wählen Sie auf der Seite Microsoft 365 Integration-Plugins die Registerkarte **Setup** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-145">From the Microsoft 365 Integration plugins page, select the **Setup** tab.</span></span>

1. <span data-ttu-id="0761e-146">Wählen Sie die Schaltfläche **PowerShell-Skript herunterladen** aus, und speichern Sie sie als ZIP-Ordner auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="0761e-146">Select the **Download PowerShell Script** button and save it as a ZIP folder to your local computer.</span></span>

1. <span data-ttu-id="0761e-147">Bereiten Sie das PowerShell-Skript aus der ZIP-Datei wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="0761e-147">Prepare the PowerShell script from the ZIP file as follows:</span></span> 

    1. <span data-ttu-id="0761e-148">Laden Sie die Datei herunter und extrahieren Sie `Moodle-AzureAD-Powershell.zip` sie.</span><span class="sxs-lookup"><span data-stu-id="0761e-148">Download and extract the `Moodle-AzureAD-Powershell.zip` file.</span></span>
    1. <span data-ttu-id="0761e-149">Öffnen Sie den extrahierten Ordner.</span><span class="sxs-lookup"><span data-stu-id="0761e-149">Open the extracted folder.</span></span>
    1. <span data-ttu-id="0761e-150">Klicken Sie mit der rechten Maustaste auf die `Moodle-AzureAD-Script.ps1` Datei und wählen Sie **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-150">Right-click on the `Moodle-AzureAD-Script.ps1` file and select **Properties**.</span></span>
    1. <span data-ttu-id="0761e-151">Aktivieren Sie unter der Registerkarte **Allgemein** im Fenster Eigenschaften das `Unblock` Kontrollkästchen neben dem **Sicherheitsattribut** am unteren Rand des Fensters.</span><span class="sxs-lookup"><span data-stu-id="0761e-151">Under the **General** tab of the Properties window, select the `Unblock` checkbox next to the **Security** attribute located at the bottom of the window.</span></span>
    1. <span data-ttu-id="0761e-152">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="0761e-152">Select **OK**.</span></span>
    1. <span data-ttu-id="0761e-153">Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.</span><span class="sxs-lookup"><span data-stu-id="0761e-153">Copy the directory path to the extracted folder.</span></span>

1. <span data-ttu-id="0761e-154">Führen Sie PowerShell als Administrator aus:</span><span class="sxs-lookup"><span data-stu-id="0761e-154">Run PowerShell as an administrator:</span></span>

    1. <span data-ttu-id="0761e-155">Klicken Sie auf Starten.</span><span class="sxs-lookup"><span data-stu-id="0761e-155">Select Start.</span></span>
    1. <span data-ttu-id="0761e-156">Geben Sie PowerShell ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-156">Type PowerShell.</span></span>
    1. <span data-ttu-id="0761e-157">Rechtsklick auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0761e-157">Right-click on **Windows PowerShell**.</span></span>
    1. <span data-ttu-id="0761e-158">Wählen Sie **Ausführen als Administrator** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-158">Select **Run as Administrator**.</span></span>

1. <span data-ttu-id="0761e-159">Navigieren Sie zum entpackten Verzeichnis, indem Sie `cd .../.../Moodle-AzureAD-Powershell` eingeben, wo `.../...` sich der Pfad zum Verzeichnis befindet.</span><span class="sxs-lookup"><span data-stu-id="0761e-159">Navigate to the unzipped directory by typing `cd .../.../Moodle-AzureAD-Powershell` where `.../...` is the path to the directory.</span></span>

1. <span data-ttu-id="0761e-160">Führen Sie das PowerShell-Skript aus:</span><span class="sxs-lookup"><span data-stu-id="0761e-160">Execute the PowerShell script:</span></span>

    1. <span data-ttu-id="0761e-161">Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-161">Enter `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.</span></span>
    1. <span data-ttu-id="0761e-162">Geben Sie `./Moodle-AzureAD-Script.ps1` ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-162">Enter `./Moodle-AzureAD-Script.ps1`.</span></span>
    1. <span data-ttu-id="0761e-163">Melden Sie sich im Popup-Fenster bei Ihrem Microsoft 365-Administratorkonto an.</span><span class="sxs-lookup"><span data-stu-id="0761e-163">Sign in to your Microsoft 365 administrator account in the pop-up window.</span></span>
    1. <span data-ttu-id="0761e-164">Geben Sie den Namen der Azure AD-Anwendung ein, z. B. Moodle- oder Moodle-Plugins.</span><span class="sxs-lookup"><span data-stu-id="0761e-164">Enter the name of the Azure AD Application, for example, Moodle or Moodle plugins.</span></span>
    1. <span data-ttu-id="0761e-165">Geben Sie die URL für Ihren Moodle-Server ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-165">Enter the URL for your Moodle server.</span></span>
    1. <span data-ttu-id="0761e-166">Kopieren Sie die vom Skript generierte **Anwendungs-ID ( `AppID` )** und **den Anwendungsschlüssel ( `Key` ),** und speichern Sie sie.</span><span class="sxs-lookup"><span data-stu-id="0761e-166">Copy the **Application ID (`AppID`)** and **Application Key(`Key`)** generated by the script and save them.</span></span>

1. <span data-ttu-id="0761e-167">Als nächstes müssen Sie die `AppID` und `Key` zum Microsoft 365 Moodle Plugins hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0761e-167">Next you must add the `AppID` and `Key` to the Microsoft 365 Moodle Plugins.</span></span> <span data-ttu-id="0761e-168">Zurück zur Plugins-Verwaltungsseite, Website-Verwaltung > Plugins > Microsoft 365 Integration.</span><span class="sxs-lookup"><span data-stu-id="0761e-168">Return to the plugins administration page, Site administration > Plugins > Microsoft 365 Integration.</span></span>

1. <span data-ttu-id="0761e-169">Fügen Sie auf der Registerkarte **Setup** die `AppID` und sie zuvor kopiert `Key` hinzu, und wählen Sie dann Änderungen **speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-169">On the **Setup** tab add the `AppID` and `Key` you copied previously, and then select **Save changes**.</span></span> <span data-ttu-id="0761e-170">Nach der Seitenaktualisierung wird ein neuer Abschnitt **Verbindungsmethode auswählen** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0761e-170">After the page refreshes, you can see a new section **Choose connection method**.</span></span>

1. <span data-ttu-id="0761e-171">Aktivieren Sie in der **Verbindungsmethode "Verbindung auswählen"** das Kontrollkästchen **Standard**, und wählen Sie dann erneut **Änderungen speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-171">In the **Choose connection method**, select the checkbox labeled **Default**, and then select **Save changes** again.</span></span>

1. <span data-ttu-id="0761e-172">Nachdem die Seite aktualisiert wurde, können Sie einen weiteren neuen Abschnitt **Admin Zustimmung & zusätzlichen Informationen** sehen.</span><span class="sxs-lookup"><span data-stu-id="0761e-172">After the page refreshes you can see another new section **Admin consent & additional information**.</span></span>
    1. <span data-ttu-id="0761e-173">Wählen Sie Link **Admin Consent bereitstellen** aus, geben Sie Ihre Microsoft 365 Globalen Administratoranmeldeinformationen ein, und **akzeptieren** Sie dann, um die Berechtigungen zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="0761e-173">Select **Provide Admin Consent** link, enter your Microsoft 365 Global Administrator credentials, then **Accept** to grant the permissions.</span></span>
    1. <span data-ttu-id="0761e-174">Wählen Sie neben dem Feld **Azure AD Tenant** die Schaltfläche **Erkennen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-174">Next to the **Azure AD Tenant** field, select the **Detect** button.</span></span>
    1. <span data-ttu-id="0761e-175">Wählen Sie neben der **OneDrive for Business URL** die Schaltfläche **Erkennen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-175">Next to the **OneDrive for Business URL**, select the **Detect** button.</span></span>
    1. <span data-ttu-id="0761e-176">Nachdem die Felder aufgepopt wurden, wählen Sie die Schaltfläche **Änderungen speichern** erneut aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-176">After the fields populate, select the **Save changes** button again.</span></span>

1. <span data-ttu-id="0761e-177">Wählen Sie die Schaltfläche **Aktualisieren** aus, um die Installation zu überprüfen, und wählen Sie dann **Änderungen speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-177">Select the **Update** button to verify the installation, and then select **Save changes**.</span></span>

1. <span data-ttu-id="0761e-178">Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0761e-178">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="0761e-179">Erste Schritte:</span><span class="sxs-lookup"><span data-stu-id="0761e-179">To get started:</span></span>

    > [!NOTE]
    > <span data-ttu-id="0761e-180">Je nach Umgebung können Sie in dieser Phase verschiedene Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="0761e-180">Depending on your environment, you can select different options during this stage.</span></span>

1. <span data-ttu-id="0761e-181">Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0761e-181">Synchronize users between your Moodle server and Azure AD.</span></span> <span data-ttu-id="0761e-182">Je nach Umgebung können Sie in dieser Phase verschiedene Optionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="0761e-182">Depending on your environment, you can select different options during this stage.</span></span> <span data-ttu-id="0761e-183">Erste Schritte:</span><span class="sxs-lookup"><span data-stu-id="0761e-183">To get started:</span></span>
    1. <span data-ttu-id="0761e-184">Wechseln Sie zur **Registerkarte Synchronisieren Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="0761e-184">Switch to the **Sync Settings tab**.</span></span>

    1. <span data-ttu-id="0761e-185">Aktivieren Sie im Abschnitt **Benutzer mit Azure AD** synchronisieren die Kontrollkästchen, die für Ihre Umgebung gelten.</span><span class="sxs-lookup"><span data-stu-id="0761e-185">In the **Sync users with Azure AD** section, select the checkboxes that apply to your environment.</span></span> <span data-ttu-id="0761e-186">Sie müssen Folgendes auswählen:</span><span class="sxs-lookup"><span data-stu-id="0761e-186">You must select the following:</span></span>  

        <span data-ttu-id="0761e-187">✔ Erstellen von Konten in Moodle für Benutzer in Azure AD.</span><span class="sxs-lookup"><span data-stu-id="0761e-187">✔ Create accounts in Moodle for users in Azure AD.</span></span>

        <span data-ttu-id="0761e-188">✔ Alle Konten in Moodle für Benutzer in Azure AD aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-188">✔ Update all accounts in Moodle for users in Azure AD.</span></span>

    1. <span data-ttu-id="0761e-189">Im Abschnitt **Benutzererstellungseinschränkung** können Sie einen Filter einrichten, um die Azure AD-Benutzer einzuschränken, die mit Moodle synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="0761e-189">In the **User Creation Restriction** section, you can setup a filter to limit the Azure AD users that is synced to Moodle.</span></span>
    1. <span data-ttu-id="0761e-190">Im Abschnitt **Benutzerfeldzuordnung** können Sie die Feldzuordnung von Azure AD zu Moodle-Benutzerprofil anpassen.</span><span class="sxs-lookup"><span data-stu-id="0761e-190">The **User Field Mapping** section allows you to customize the Azure AD to Moodle User Profile field mapping.</span></span>
    1. <span data-ttu-id="0761e-191">Im Abschnitt **Teams Sync** können Sie auswählen, dass automatisch Gruppen erstellt werden sollen, z. B. Teams für einige oder alle vorhandenen Moodle-Kurse.</span><span class="sxs-lookup"><span data-stu-id="0761e-191">In the **Teams Sync** section, you can select to automatically create Groups, such as teams for some, or all, of your existing Moodle courses.</span></span>

13. <span data-ttu-id="0761e-192">Um [Cron-Aufträge](https://docs.moodle.org/310/en/Cron) zu überprüfen und manuell für die erste Ausführung auszuführen, wählen Sie im Abschnitt **Benutzer mit Azure AD** synchronisieren den Link zur Verwaltung **geplanter Aufgaben** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-192">To validate [cron](https://docs.moodle.org/310/en/Cron) jobs and run them manually for the first run, select the **Scheduled tasks management page** link in the **Sync users with Azure AD** section.</span></span> <span data-ttu-id="0761e-193">Dadurch gelangen Sie zur Seite **Geplante Aufgaben.**</span><span class="sxs-lookup"><span data-stu-id="0761e-193">This takes you to the **Scheduled Tasks** page.</span></span>

    1. <span data-ttu-id="0761e-194">Scrollen Sie nach unten, und suchen Sie den **Azure AD-Auftrag synchronisieren,** und wählen Sie **Jetzt ausführen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-194">Scroll down and find the **Sync users with Azure AD** job and select **Run now**.</span></span>
    1. <span data-ttu-id="0761e-195">Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch die **Benutzergruppen erstellen in Microsoft 365** ausführen.</span><span class="sxs-lookup"><span data-stu-id="0761e-195">If you select to create Groups based on existing courses, you can also run the **Create user groups in Microsoft 365** job.</span></span>

    > [!NOTE]
    >
    > <span data-ttu-id="0761e-196">Der Moodle [Cron](https://docs.moodle.org/310/en/Cron) läuft nach dem Aufgabenplan.</span><span class="sxs-lookup"><span data-stu-id="0761e-196">The Moodle [Cron](https://docs.moodle.org/310/en/Cron) runs according to the task schedule.</span></span> <span data-ttu-id="0761e-197">Der Standardzeitplan ist einmal täglich.</span><span class="sxs-lookup"><span data-stu-id="0761e-197">The default schedule is once a day.</span></span> <span data-ttu-id="0761e-198">Der Cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.</span><span class="sxs-lookup"><span data-stu-id="0761e-198">However, the cron must run more frequently to keep everything in sync.</span></span>

1. <span data-ttu-id="0761e-199">Kehren Sie zur Plugin-Verwaltungsseite, **zur Websiteverwaltung > Plugins > Microsoft 365 Integration** zurück, und wählen Sie die Seite **Teams Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-199">Return to the plugins administration page, **Site administration > Plugins > Microsoft 365 Integration**, and select the **Teams Settings** page.</span></span>

1. <span data-ttu-id="0761e-200">Konfigurieren Sie auf der **Seite Teams Einstellungen** die erforderlichen Einstellungen, um die Teams App-Integration zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-200">On the **Teams Settings** page, configure the required settings to enable the Teams app integration.</span></span>

    1. <span data-ttu-id="0761e-201">Um **OpenID Verbinden** zu aktivieren, wählen Sie den Link **Authentifizierung verwalten** aus, und wählen Sie das Augensymbol in der **OpenId-Verbinden-Zeile** aus, wenn es ausgegraut ist.</span><span class="sxs-lookup"><span data-stu-id="0761e-201">To enable **OpenID Connect**, select the **Manage Authentication** link, and select the eye icon on the **OpenId Connect** line if it is greyed out.</span></span>
    1. <span data-ttu-id="0761e-202">Um die Einbettung von Frames zu aktivieren, wählen Sie die **HTTP-Sicherheitsverknüpfung** aus, und aktivieren Sie dann das Kontrollkästchen neben **Frameeinbettung zulassen**.</span><span class="sxs-lookup"><span data-stu-id="0761e-202">To enable frame embedding, select the **HTTP Security** link, and then select the checkbox next to **Allow frame embedding**.</span></span>
    1. <span data-ttu-id="0761e-203">Um Webdienste zu aktivieren, die die Moodle-API-Funktionen aktivieren, wählen Sie den Link **Erweiterte Funktionen** aus, und stellen Sie dann sicher, dass das Kontrollkästchen neben **Webdienste aktivieren** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0761e-203">To enable web services, which enables the Moodle API features, select the **Advanced Features** link, and then ensure the checkbox next to **Enable web services** is selected.</span></span>
    1. <span data-ttu-id="0761e-204">Um die externen Dienste für Microsoft 365 zu aktivieren, wählen Sie die Verknüpfung **Externe Dienste** aus, und dann:</span><span class="sxs-lookup"><span data-stu-id="0761e-204">To enable the external services for Microsoft 365, select the **External services** link, and then:</span></span>  

        <span data-ttu-id="0761e-205">✔ Wählen Sie **Bearbeiten** in der **Zeile Moodle Microsoft 365 Webservices** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-205">✔ Select **Edit** on the **Moodle Microsoft 365 Webservices** row.</span></span>

        <span data-ttu-id="0761e-206">✔ Aktivieren Sie das Kontrollkästchen neben **Aktiviert**, und wählen Sie dann **Änderungen speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-206">✔ Select the checkbox next to **Enabled**, then select **Save Changes**</span></span>

    1. <span data-ttu-id="0761e-207">Bearbeiten Sie Ihre authentifizierten Benutzerberechtigungen, damit diese Webdiensttoken erstellen können.</span><span class="sxs-lookup"><span data-stu-id="0761e-207">Edit your authenticated user permissions to allow them to create web service tokens.</span></span>

        <span data-ttu-id="0761e-208">✔ Wählen Sie die **Bearbeitungsrolle Authentifizierter Benutzerlink** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-208">✔ Select the **Editing role Authenticated user** link.</span></span>

        <span data-ttu-id="0761e-209">✔ Scrollen Sie nach unten und suchen Sie die Funktion **Webdiensttoken erstellen,** und aktivieren Sie das Kontrollkästchen **Zulassen.**</span><span class="sxs-lookup"><span data-stu-id="0761e-209">✔ Scroll down and find the **Create a web service token** capability and select the **Allow** checkbox.</span></span>

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a><span data-ttu-id="0761e-210">3. Stellen Sie den Moodle Assistant Bot in Azure bereit</span><span class="sxs-lookup"><span data-stu-id="0761e-210">3. Deploy the Moodle Assistant Bot to Azure</span></span>

<span data-ttu-id="0761e-211">Der kostenlose Moodle-Assistents-Bot für Microsoft Teams hilft Lehrern und Schülern, Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="0761e-211">The free Moodle assistant bot for Microsoft Teams helps teachers and students answer questions about their courses, assignments, grades, and other information in Moodle.</span></span> <span data-ttu-id="0761e-212">Der Bot sendet auch Moodle-Benachrichtigungen an Schüler und Lehrer innerhalb Teams.</span><span class="sxs-lookup"><span data-stu-id="0761e-212">The bot also sends Moodle notifications to students and teachers within Teams.</span></span> <span data-ttu-id="0761e-213">Der Bot ist ein Open-Source-Projekt, das von Microsoft verwaltet wird und auf [GitHub](https://github.com/microsoft/Moodle-Teams-Bot)verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="0761e-213">The bot is an open-source project maintained by Microsoft, and is available on [GitHub](https://github.com/microsoft/Moodle-Teams-Bot).</span></span>

> [!NOTE]
>
> * <span data-ttu-id="0761e-214">Stellen Sie Ressourcen für Ihr Azure-Abonnement bereit.</span><span class="sxs-lookup"><span data-stu-id="0761e-214">Deploy resources to your Azure subscription.</span></span> <span data-ttu-id="0761e-215">Alle Ressourcen wurden mit dem **kostenlosen** Kontingent konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="0761e-215">All resources were configured using the **free** tier.</span></span> <span data-ttu-id="0761e-216">Abhängig von der Nutzung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-216">Depending on the usage of your bot, you may have to scale these resources.</span></span>
>
> * <span data-ttu-id="0761e-217">Um die Moodle-Registerkarte ohne den Bot zu verwenden, springen Sie zu [4](#4-deploy-your-microsoft-teams-app).</span><span class="sxs-lookup"><span data-stu-id="0761e-217">To use the Moodle tab without the bot, skip to [4](#4-deploy-your-microsoft-teams-app).</span></span>

### <a name="moodle-bot-information-flow"></a><span data-ttu-id="0761e-218">Moodle Bot-Informationsfluss</span><span class="sxs-lookup"><span data-stu-id="0761e-218">Moodle bot information flow</span></span>

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

<span data-ttu-id="0761e-219">Um den Bot zu installieren, müssen Sie ihn auf der [Microsoft Identity Platform](https://identity.microsoft.com/Landing)registrieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-219">To install the bot, you must register it on the [Microsoft Identity Platform](https://identity.microsoft.com/Landing).</span></span> <span data-ttu-id="0761e-220">Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-220">This allows your bot to authenticate against your Microsoft endpoints.</span></span> 

<span data-ttu-id="0761e-221">**So registrieren Sie Ihren Bot**</span><span class="sxs-lookup"><span data-stu-id="0761e-221">**To register your bot**</span></span>

1. <span data-ttu-id="0761e-222">Gehen Sie zur Plugins-Verwaltungsseite, und wählen Sie dann **Plugins** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-222">Go to the plugins administration page, and then select **Plugins**.</span></span> <span data-ttu-id="0761e-223">Wählen Sie unter **Microsoft 365 Integration** die Registerkarte **Teams Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-223">Under **Microsoft 365 Integration**, select the **Teams Settings** tab.</span></span>

1. <span data-ttu-id="0761e-224">Wählen Sie den Link **Microsoft Application Registration Portal** aus, und melden Sie sich mit Ihrer Microsoft ID an.</span><span class="sxs-lookup"><span data-stu-id="0761e-224">Select the **Microsoft Application Registration Portal** link and sign in with your Microsoft ID.</span></span>

1. <span data-ttu-id="0761e-225">Geben Sie einen Namen für Ihre App ein, z. B. MoodleBot, und wählen Sie die Schaltfläche **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-225">Enter a name for your app, such as MoodleBot and select the **Create** button.</span></span>

1. <span data-ttu-id="0761e-226">Kopieren Sie die **Anwendungs-ID,** und fügen Sie sie in das Feld **Bot-Anwendungs-ID** auf der **Seite Team Einstellungen** ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-226">Copy the **Application ID** and paste it into the **Bot Application ID** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="0761e-227">Wählen Sie die Schaltfläche **Neues Kennwort generieren** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-227">Select the **Generate New Password** button.</span></span> <span data-ttu-id="0761e-228">Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld **Bot-Anwendungskennwort** auf der **Seite Team Einstellungen** ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-228">Copy the generated password and and paste it into the **Bot Application Password** field on the **Team Settings** page.</span></span>

1. <span data-ttu-id="0761e-229">Scrollen Sie zum unteren Rand des Formulars, und wählen Sie **Änderungen speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-229">Scroll to the bottom of the form and select **Save Changes**.</span></span>

<span data-ttu-id="0761e-230">Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:</span><span class="sxs-lookup"><span data-stu-id="0761e-230">After generating your application ID and password, deploy your bot to Azure:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="0761e-231">Wählen Sie **Bereitstellen in Azure** aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. der Bot-Anwendungs-ID, dem Bot-Anwendungskennwort und dem Moodle Secret auf der **Teams Einstellungen-Seite.**</span><span class="sxs-lookup"><span data-stu-id="0761e-231">Select **Deploy to Azure** and complete the form with the necessary information, such as the Bot Application ID, Bot Application Password, and the Moodle Secret on the **Teams Settings** page.</span></span> <span data-ttu-id="0761e-232">Die Azure-Informationen befinden sich auf der **Seite Setup.**</span><span class="sxs-lookup"><span data-stu-id="0761e-232">The Azure information is on the **Setup** page.</span></span> 
> * <span data-ttu-id="0761e-233">Aktivieren Sie nach dem Ausfüllen des Formulars das Kontrollkästchen, um den Geschäftsbedingungen zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="0761e-233">After completing the form, select the checkbox to agree to the terms and conditions.</span></span>
> * <span data-ttu-id="0761e-234">Wählen Sie **Kauf**.</span><span class="sxs-lookup"><span data-stu-id="0761e-234">Select **Purchase**.</span></span> <span data-ttu-id="0761e-235">Alle Azure-Ressourcen werden im kostenlosen Kontingent bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="0761e-235">All Azure resources are deployed to the free tier.</span></span>

<span data-ttu-id="0761e-236">Nachdem die Bereitstellung der Ressourcen in Azure abgeschlossen wurde, müssen Sie die Microsoft 365 Moodle-Plugins mit einem Messagingendpunkt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-236">After the resources have completed deploying to Azure, you must configure the Microsoft 365 Moodle plugins with a messaging endpoint.</span></span> <span data-ttu-id="0761e-237">Sie müssen den Endpunkt von Ihrem Bot in Azure abrufen:</span><span class="sxs-lookup"><span data-stu-id="0761e-237">You must get the endpoint from your bot in Azure:</span></span>

1. <span data-ttu-id="0761e-238">Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.</span><span class="sxs-lookup"><span data-stu-id="0761e-238">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

1. <span data-ttu-id="0761e-239">Wählen Sie im linken Bereich **Ressourcengruppen** aus, und wählen Sie die Ressourcengruppe aus, die Sie verwendet oder erstellt haben, während Sie ihren Bot bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0761e-239">In the left pane, select **Resource groups** and select the resource group you used or created, while deploying your bot.</span></span>

1. <span data-ttu-id="0761e-240">Wählen Sie die **WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-240">Select the **WebApp Bot** resource from the list of resources in the group.</span></span>

1. <span data-ttu-id="0761e-241">Kopieren Sie den **Messaging-Endpunkt** aus dem Abschnitt **Übersicht.**</span><span class="sxs-lookup"><span data-stu-id="0761e-241">Copy the **Messaging Endpoint** from the **Overview** section.</span></span>

1. <span data-ttu-id="0761e-242">Öffnen Sie in Moodle die **Team-Einstellungen-Seite** Ihres Microsoft 365 Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="0761e-242">In Moodle, open the **Team Settings** page of your Microsoft 365 Moodle Plugins.</span></span>

1. <span data-ttu-id="0761e-243">Fügen Sie im Feld **Bot Endpoint** die URL ein, die Sie gerade kopiert haben, und ändern Sie das Wort *Nachrichten* in *webhook*.</span><span class="sxs-lookup"><span data-stu-id="0761e-243">In the **Bot Endpoint** field paste the URL you just copied and change the word *messages* to *webhook*.</span></span> <span data-ttu-id="0761e-244">Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`</span><span class="sxs-lookup"><span data-stu-id="0761e-244">The URL must appear as follows: `https://botname.azurewebsites.net/api/webhook`</span></span>

1. <span data-ttu-id="0761e-245">Wählen Sie **Änderungen speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-245">Select **Save Changes**.</span></span>

1. <span data-ttu-id="0761e-246">Nachdem Sie die Änderungen gespeichert haben, kehren Sie zur Registerkarte **Team Einstellungen** zurück, wählen Sie die Schaltfläche **Manifestdatei herunterladen** aus, und speichern Sie das App-Manifestpaket zur weiteren Verwendung auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="0761e-246">After saving the changes, go back to the **Team Settings** tab, select the **Download manifest file** button, and save the app manifest package to your computer for further use.</span></span>

## <a name="4-deploy-your-microsoft-teams-app"></a><span data-ttu-id="0761e-247">4. Stellen Sie Ihre Microsoft Teams-App bereit</span><span class="sxs-lookup"><span data-stu-id="0761e-247">4. Deploy your Microsoft Teams app</span></span>

<span data-ttu-id="0761e-248">Nachdem Ihr Bot in Azure bereitgestellt und für die Weiterbereitung mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams-App bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0761e-248">After your bot deployed to Azure and configured to talk to your Moodle server, you must deploy your Microsoft Teams app.</span></span> <span data-ttu-id="0761e-249">Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Seite Microsoft 365 Moodle Plugins Team Einstellungen heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="0761e-249">To do this you must load the app manifest file that you downloaded from the Microsoft 365 Moodle Plugins Team Settings page in the previous step.</span></span>

<span data-ttu-id="0761e-250">Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="0761e-250">Before you install the app you must ensure to enable external apps and uploading of apps.</span></span> <span data-ttu-id="0761e-251">Weitere Informationen finden Sie unter [Vorbereiten des Microsoft 365 Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md).</span><span class="sxs-lookup"><span data-stu-id="0761e-251">For more information, see [Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md).</span></span> 

<span data-ttu-id="0761e-252">**So stellen Sie Ihre App bereit**</span><span class="sxs-lookup"><span data-stu-id="0761e-252">**To deploy your app**</span></span> 

1. <span data-ttu-id="0761e-253">Öffnen **Sie Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="0761e-253">Open **Microsoft Teams**.</span></span> 

1. <span data-ttu-id="0761e-254">Wählen Sie das **App-Symbol** im unteren linken Bereich der Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-254">Select the **App** icon on the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="0761e-255">Wählen Sie die **Hochladen einen benutzerdefinierten App-Link** aus der Liste der Optionen aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-255">Select the **Upload a custom app** link from the list of options.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0761e-256">Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen, andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.</span><span class="sxs-lookup"><span data-stu-id="0761e-256">If you are logged in as a global administrator, you must have the option of uploading the app to your organization's app catalog, otherwise you can only load the app for a team in which you are a member.</span></span>

4. <span data-ttu-id="0761e-257">Wählen Sie das Paket aus, `manifest.zip` das Sie zuvor heruntergeladen haben, und wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-257">Select the `manifest.zip` package you downloaded previously and select **Save**.</span></span> <span data-ttu-id="0761e-258">Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie es von der Registerkarte **Team Einstellungen** der Plugins-Konfigurationsseite in Moodle herunterladen.</span><span class="sxs-lookup"><span data-stu-id="0761e-258">If you have not downloaded the app manifest package, you can download from the **Team Settings** tab of the plugins configuration page in Moodle.</span></span>

<span data-ttu-id="0761e-259">Nachdem Sie die App installiert haben, können Sie die Registerkarte jedem Kanal hinzufügen, auf den Sie Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="0761e-259">Now that you have the app installed, you can add the tab to any channel that you have access to.</span></span> <span data-ttu-id="0761e-260">Navigieren Sie dazu zum Kanal, wählen Sie das **Plussymbol** (➕) und wählen Sie Ihre App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-260">To do so, navigate to the channel, select the **plus** (➕) symbol and select your app from the list.</span></span> <span data-ttu-id="0761e-261">Folgen Sie den Anweisungen, um das Hinzufügen der Moodle-Kursregisterkarte zu einem Kanal abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="0761e-261">Follow the prompts to finish adding your Moodle course tab to a channel.</span></span>

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a><span data-ttu-id="0761e-262">5. Erlauben Sie die automatische Erstellung von Moodle-Tabs in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0761e-262">5. Allow automatic creation of Moodle tabs in Microsoft Teams</span></span>

<span data-ttu-id="0761e-263">Obwohl die Moodle-Registerkarten manuell in Microsoft Teams erstellt werden, können Sie sie automatisch erstellen, wenn Teams aus der Kurssynchronisierung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0761e-263">Although the Moodle tabs are created manually in Microsoft Teams, you can decide to create them automatically when teams are created from course synchronization.</span></span> <span data-ttu-id="0761e-264">Dazu müssen Sie die ID der hochgeladenen Microsoft Teams-App in Moodle konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0761e-264">To do this, you must configure the ID of the uploaded Microsoft Teams app in Moodle.</span></span>

<span data-ttu-id="0761e-265">**So ermöglichen Sie die automatische Erstellung von Moodle-Registerkarten**</span><span class="sxs-lookup"><span data-stu-id="0761e-265">**To allow automatic creation of Moodle tabs**</span></span>

1. <span data-ttu-id="0761e-266">Öffnen Sie Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0761e-266">Open Microsoft Teams.</span></span>

1. <span data-ttu-id="0761e-267">Wählen Sie das Apps-Symbol im unteren linken Bereich der Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="0761e-267">Select the Apps icon from the lower-left area of the navigation bar.</span></span>

1. <span data-ttu-id="0761e-268">Suchen Sie die hochgeladene **Moodle-App** > das **Optionssymbol** auswählen > **Den Link kopieren** auswählen.</span><span class="sxs-lookup"><span data-stu-id="0761e-268">Locate the uploaded **Moodle app** > select the **options** icon > select **copy link**.</span></span>

1. <span data-ttu-id="0761e-269">Fügen Sie in einem Texteditor den kopierten Inhalt ein.</span><span class="sxs-lookup"><span data-stu-id="0761e-269">In a text editor, paste the copied content.</span></span> <span data-ttu-id="0761e-270">Sie muss eine URL wie ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff enthalten.</span><span class="sxs-lookup"><span data-stu-id="0761e-270">It must contain a URL such as ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff.</span></span> <span data-ttu-id="0761e-271">Kopieren Sie den letzten Teil der URL, z. B. `00112233-4455-6677-8899-aabbccddeeff` , der die ID der Microsoft Teams-App ist.</span><span class="sxs-lookup"><span data-stu-id="0761e-271">Copy the last part of the URL, such as  `00112233-4455-6677-8899-aabbccddeeff`, which is the ID of the Microsoft Teams app.</span></span>

1. <span data-ttu-id="0761e-272">Öffnen Sie in Moodle die **Teams Moodle-App-Registerkarte** von Ihrer Konfigurationsseite Microsoft 365 Moodle Plugins.</span><span class="sxs-lookup"><span data-stu-id="0761e-272">In Moodle, open the **Teams Moodle app** tab from your Microsoft 365 Moodle Plugins configuration page.</span></span>

1. <span data-ttu-id="0761e-273">Fügen Sie die ID der Microsoft Teams-App in das Feld Moodle-App-ID ein, und speichern Sie Änderungen.</span><span class="sxs-lookup"><span data-stu-id="0761e-273">Paste the ID of the Microsoft Teams app into the Moodle app ID field, and save changes.</span></span>

<span data-ttu-id="0761e-274">Wenn ein Moodle-Kurs synchronisiert wird, installiert Microsoft Teams automatisch die Moodle-App im Team, erstellt eine Moodle-Registerkarte im allgemeinen Kanal von Teams und konfiguriert sie so, dass sie die Kursseite für den Moodle-Kurs enthält, von dem aus er synchronisiert wird.</span><span class="sxs-lookup"><span data-stu-id="0761e-274">When a Moodle course is synced, Microsoft Teams automatically installs the Moodle app in the team, creates a Moodle tab in the General channel of Teams, and configures it to contain the course page for the Moodle course from which it is synced.</span></span> <span data-ttu-id="0761e-275">Sie können jetzt direkt von Microsoft Teams aus mit der Arbeit mit Ihren Moodle-Kursen beginnen.</span><span class="sxs-lookup"><span data-stu-id="0761e-275">You can now start working with your Moodle courses directly from Microsoft Teams.</span></span>

> [!NOTE]
> <span data-ttu-id="0761e-276">Um Feature-Anfragen oder Feedback mit uns zu teilen, besuchen Sie unsere [User Voice-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).</span><span class="sxs-lookup"><span data-stu-id="0761e-276">To share any feature requests or feedback with us, visit our [User Voice page](https://microsoftteams.uservoice.com/forums/916759-moodle).</span></span>

## <a name="see-also"></a><span data-ttu-id="0761e-277">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0761e-277">See also</span></span>

- [<span data-ttu-id="0761e-278">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="0761e-278">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
- [<span data-ttu-id="0761e-279">Moodle</span><span class="sxs-lookup"><span data-stu-id="0761e-279">Moodle</span></span>](https://moodle.org/)
- <span data-ttu-id="0761e-280">[Moodle-Dokumentation](https://docs.moodle.org/34/en/Installing_plugins).</span><span class="sxs-lookup"><span data-stu-id="0761e-280">[Moodle documentation](https://docs.moodle.org/34/en/Installing_plugins).</span></span>

