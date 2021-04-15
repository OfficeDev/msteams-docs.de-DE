---
title: Hinzufügen von Testdaten zu Ihrem Microsoft 365-Test-Mandanten
description: Einrichten Ihres Office 365-Entwicklerprogrammabonnements für erfolgreiche Tests von Microsoft Teams Apps
ms.topic: how-to
keywords: Testen von Entwicklerprogrammteams für Apps
ms.date: 11/01/2019
ms.openlocfilehash: c702921b1c55570ca8e2869b95c00ae6ae4ebdf4
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696864"
---
# <a name="add-test-data-to-your-microsoft-365-test-tenant"></a><span data-ttu-id="78bf1-104">Hinzufügen von Testdaten zu Ihrem Microsoft 365-Test-Mandanten</span><span class="sxs-lookup"><span data-stu-id="78bf1-104">Add test data to your Microsoft 365 test tenant</span></span>

<span data-ttu-id="78bf1-105">Mit einem Microsoft 365-Entwicklerabonnement können Sie Ihre Microsoft Teams-App mit Testteams, Kanälen und Benutzern verwenden.</span><span class="sxs-lookup"><span data-stu-id="78bf1-105">With a Microsoft 365 developer subscription, you can use your Microsoft Teams app with test teams, channels, and users.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78bf1-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="78bf1-106">Prerequisites</span></span>

1. <span data-ttu-id="78bf1-107">[Nehmen Sie am Microsoft 365 Developer Program teil,](/office/developer-program/office-365-developer-program)wenn Sie keinen Test mandanten haben.</span><span class="sxs-lookup"><span data-stu-id="78bf1-107">[Join the Microsoft 365 Developer Program](/office/developer-program/office-365-developer-program), if you do not have a test tenant.</span></span>
2. <span data-ttu-id="78bf1-108">[Richten Sie ein Microsoft 365-Entwicklerabonnement ein.](/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="78bf1-108">[Set up a Microsoft 365 Developer Subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>
3. <span data-ttu-id="78bf1-109">[Verwenden Sie Beispieldatenpakete mit Ihrem Microsoft 365-Entwicklerabonnement, um das Users Content Pack zu installieren.](/office/developer-program/install-sample-packs)</span><span class="sxs-lookup"><span data-stu-id="78bf1-109">[Use sample data packs with your Microsoft 365 developer subscription to install the Users content pack](/office/developer-program/install-sample-packs).</span></span>
4. <span data-ttu-id="78bf1-110">[Installieren Sie das Teams PowerShell-Modul](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2).</span><span class="sxs-lookup"><span data-stu-id="78bf1-110">[Install the Teams PowerShell module](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2).</span></span>
5. <span data-ttu-id="78bf1-111">[Installieren Sie das Azure AD PowerShell-Modul](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="78bf1-111">[Install the Azure AD PowerShell module](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module&preserve-view=true).</span></span>

> [!NOTE]
> <span data-ttu-id="78bf1-112">Für jeden mandanten, den Sie verwenden, müssen Sie die globalen Administratorberechtigungen zum Ausführen der Skripts erhalten.</span><span class="sxs-lookup"><span data-stu-id="78bf1-112">For any tenant that you use, you must get the global administrator permissions to run the scripts.</span></span>

### <a name="optional-step-to-allow-upload-of-custom-apps"></a><span data-ttu-id="78bf1-113">Optionaler Schritt zum Hochladen benutzerdefinierter Apps</span><span class="sxs-lookup"><span data-stu-id="78bf1-113">Optional step to allow upload of custom apps</span></span>

<span data-ttu-id="78bf1-114">Standardmäßig können nur globale Administratoren oder Teamdienstadministratoren benutzerdefinierte Apps in den Mandanten-App-Katalog hochladen.</span><span class="sxs-lookup"><span data-stu-id="78bf1-114">By default, only global admins or teams service admins can upload custom apps into the tenant app catalog.</span></span> <span data-ttu-id="78bf1-115">Sie können auch allen Benutzern das Hochladen benutzerdefinierter Apps für ihre eigene Verwendung oder für Teams zu Testzwecken ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="78bf1-115">You can also enable all users to upload custom apps for their own use or to teams for testing.</span></span>

<span data-ttu-id="78bf1-116">Um diese Einstellung zu aktivieren, müssen Sie die globale App-Setuprichtlinie in Ihrem Teams Admin Portal aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="78bf1-116">To enable this setting, you'll need to update the global App Setup Policy in your Teams Admin Portal.</span></span>

<img width="430px" src="~/assets/images/microsoft-teams-admin-center-screenshot.png" alt="Screenshot of App Setup Policy"/>

## <a name="optional-step-to-enable-custom-app-sideloading"></a><span data-ttu-id="78bf1-117">Optionaler Schritt zum Aktivieren des Querladens benutzerdefinierter Apps</span><span class="sxs-lookup"><span data-stu-id="78bf1-117">Optional step to enable custom app sideloading</span></span>

<span data-ttu-id="78bf1-118">Das Aktivieren der benutzerdefinierten App-Querladen ist optional.</span><span class="sxs-lookup"><span data-stu-id="78bf1-118">Enabling custom app sideloading is optional.</span></span> <span data-ttu-id="78bf1-119">Standardmäßig können nur globale Administratoren oder Teams-Dienstadministratoren benutzerdefinierte Apps in den Mandanten-App-Katalog hochladen.</span><span class="sxs-lookup"><span data-stu-id="78bf1-119">By default, only global admins or Teams service admins can upload custom apps into the tenant app catalog.</span></span> <span data-ttu-id="78bf1-120">Sie können Benutzern auch erlauben, benutzerdefinierte Apps in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="78bf1-120">You can also allow users to upload custom apps to Teams.</span></span> <span data-ttu-id="78bf1-121">Weitere Informationen finden Sie unter [Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="78bf1-121">For more information, see [manage app setup policies in Teams](/microsoftteams/teams-app-setup-policies).</span></span>

## <a name="create-teams-and-channels"></a><span data-ttu-id="78bf1-122">Erstellen von Teams und Kanälen</span><span class="sxs-lookup"><span data-stu-id="78bf1-122">Create teams and channels</span></span>

1. <span data-ttu-id="78bf1-123">Speichern Sie den folgenden Codeausschnitt als **XML-Datei,** und notieren Sie sich den Dateipfad.</span><span class="sxs-lookup"><span data-stu-id="78bf1-123">Save the following snippet as a **.xml** file and note the file path.</span></span> <span data-ttu-id="78bf1-124">In dieser XML wird die Struktur des Teams und Kanals definiert, das zusammen mit seinen Mitgliedern erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="78bf1-124">This XML defines the structure of the team and channel that is created along with its members:</span></span>

    ```xml
    <?xml version="1.0"?>
    <Teams>
      <Team Name="Store Portal" ID="storeportal" Description="" Type="Private" Creator="admin">
        <Members>
          <Member UserName="AlexW" IsOwner="false"/>
          <Member UserName="PattiF" IsOwner="false"/>
          <Member UserName="PradeepG" IsOwner="false"/>
          <Member UserName="JoniS" IsOwner="false"/>
          <Member UserName="JohannaL" IsOwner="false"/>
          <Member UserName="NestorW" IsOwner="false"/>
          <Member UserName="IsaiahL" IsOwner="false"/>
          <Member UserName="AdeleV" IsOwner="false"/>
          <Member UserName="LeeG" IsOwner="false"/>
          <Member UserName="MeganB" IsOwner="true"/>
          <Member UserName="LynneR" IsOwner="false"/>
          <Member UserName="GradyA" IsOwner="false"/>
          <Member UserName="LidiaH" IsOwner="false"/>
          <Member UserName="DiegoS" IsOwner="false"/>
          <Member UserName="MiriamG" IsOwner="true"/>
        </Members>
        <Channels>
          <Channel Name="Sales" ID="sales" Description="" Creator="Admin" />
          <Channel Name="Inventory" ID="inventory" Description="" Creator="Admin" />
          <Channel Name="Los Angeles Store 239" ID="losangelesstore239" Description="" Creator="Admin" />
          <Channel Name="Seattle Store 121" ID="seattlestore121" Description="" Creator="Admin" />
          <Channel Name="Online" ID="online" Description="" Creator="Admin" />
          <Channel Name="Store Layout" ID="storelayout" Description="" Creator="Admin" />
          <Channel Name="Promotions" ID="promotions" Description="" Creator="Admin" />
        </Channels>
      </Team>
      <Team Name="Mark 8 Project Team" ID="Mark8ProjectTeam" Description="Welcome to the team that we've assembled to create the Mark 8." Type="Private" Creator="admin">
        <Members>
          <Member UserName="meganb" IsOwner="true" />
          <Member UserName="alexw" IsOwner="false" />
          <Member UserName="lynner" IsOwner="false" />
          <Member UserName="isaiahl" IsOwner="false" />
          <Member UserName="leeg" IsOwner="false" />
          <Member UserName="pradeepg" IsOwner="false" />
          <Member UserName="lidiah" IsOwner="false" />
          <Member UserName="diegos" IsOwner="false" />
          <Member UserName="johannal" IsOwner="false" />
          <Member UserName="miriamg" IsOwner="false" />
          <Member UserName="adelev" IsOwner="false" />
          <Member UserName="jonis" IsOwner="false" />
          <Member UserName="nestorw" IsOwner="false" />
          <Member UserName="gradya" IsOwner="false" />
          <Member UserName="pattif" IsOwner="false" />
        </Members>
        <Channels>
          <Channel Name="Research and Development" ID="researchanddevelopment" Description="Channel for Research and Development!" Creator="meganb" />
          <Channel Name="Design" ID="design" Description="Discuss design projects." Creator="meganb" />
          <Channel Name="Digital Assets Web" ID="digitalassetsweb" Description="Discuss digital assets." Creator="meganb" />
          <Channel Name="Go to Market Plan" ID="gotomarketplan" Description="Our go-to-market plan!" Creator="meganb" />
        </Channels>
      </Team>
      <Team Name="District 9 Road Safety Audit" ID="district9roadsafetyaudit" Description="" Type="Private" Creator="admin">
        <Members>
          <Member UserName="meganb" IsOwner="true" />
          <Member UserName="alexw" IsOwner="false" />
          <Member UserName="lynner" IsOwner="false" />
          <Member UserName="isaiahl" IsOwner="false" />
          <Member UserName="leeg" IsOwner="false" />
          <Member UserName="pradeepg" IsOwner="false" />
          <Member UserName="lidiah" IsOwner="false" />
          <Member UserName="diegos" IsOwner="false" />
          <Member UserName="johannal" IsOwner="false" />
          <Member UserName="miriamg" IsOwner="false" />
          <Member UserName="adelev" IsOwner="false" />
          <Member UserName="jonis" IsOwner="false" />
          <Member UserName="nestorw" IsOwner="false" />
          <Member UserName="gradya" IsOwner="false" />
          <Member UserName="pattif" IsOwner="false" />
        </Members>
        <Channels>
          <Channel Name="Audit Planning" ID="auditplanning" Description="" Creator="Admin" />
          <Channel Name="Delivery" ID="delivery" Description="" Creator="Admin" />
          <Channel Name="Findings" ID="findings" Description="" Creator="Admin" />
          <Channel Name="Recommended Actions" ID="recommendedactions" Description="" Creator="Admin" />
          <Channel Name="Survey" ID="survey" Description="" Creator="Admin" />
        </Channels>
      </Team>
      <Team Name="ACC-1000 Product Team" ID="acc1000productteam" Description="" Type="Private" Creator="admin" >
        <Members>
          <Member UserName="meganb" IsOwner="true" />
          <Member UserName="alexw" IsOwner="false" />
          <Member UserName="lynner" IsOwner="false" />
          <Member UserName="isaiahl" IsOwner="false" />
          <Member UserName="leeg" IsOwner="false" />
          <Member UserName="pradeepg" IsOwner="false" />
          <Member UserName="lidiah" IsOwner="false" />
          <Member UserName="diegos" IsOwner="false" />
          <Member UserName="johannal" IsOwner="false" />
          <Member UserName="miriamg" IsOwner="false" />
          <Member UserName="adelev" IsOwner="false" />
          <Member UserName="jonis" IsOwner="false" />
          <Member UserName="nestorw" IsOwner="false" />
          <Member UserName="gradya" IsOwner="false" />
          <Member UserName="pattif" IsOwner="false" />
        </Members>
        <Channels>
          <Channel Name="Corporate Communication" ID="corporatecommunication" Description="" Creator="Admin" />
          <Channel Name="Lean Process Improvement" ID="corporatecommunication" Description="" Creator="Admin" />
          <Channel Name="Training and Certification" ID="trainingandcertification" Description="" Creator="Admin" />
          <Channel Name="Production" ID="production" Description="" Creator="Admin" />
          <Channel Name="Research and Development" ID="researchanddevelopment" Description="" Creator="Admin" />
          <Channel Name="Supplier Collaboration" ID="suppliercollaboration" Description="" Creator="Admin" />
        </Channels>
      </Team>
    </Teams>
    ```

2. <span data-ttu-id="78bf1-125">Speichern Sie den folgenden Codeausschnitt als PowerShell-Skript (PS1), und notieren Sie sich, wo Sie ihn gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="78bf1-125">Save the following snippet as a PowerShell script (.ps1) and note where you have saved it.</span></span> <span data-ttu-id="78bf1-126">Dieses Skript führt die Schritte aus, um das Team und den Kanal zu erstellen und ihnen Mitglieder hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="78bf1-126">This script executes the steps to create the team and channel, and add members to them:</span></span>

    ```powershell
    Param(
        [Parameter(Mandatory = $true)]

        # This specifies the location of your configuration XML.

        [string] $teamsFilePath 
    )

    [xml]$XmlDocument = Get-Content -Path $teamsFilePath.ToString()

    if ($XmlDocument.Teams.Team.Count -gt 0) {

        try {

            # 1. Login with the global administrator account for your O365 Developer Program tenant. This script uses these credentials to connect to the powershell modules for Azure Active Directory and Microsoft Teams

            $creds = Get-Credential

            # Connecting to AAD PowerShell
            Connect-AzureAD -Credential $creds | Out-Null

            # Connect to Microsoft Teams PowerShell
            Connect-MicrosoftTeams -Credential $creds | Out-Null

            Write-Host "Connected to Microsoft 365 and configuring your organization with test teams and channels"

            # 2. Create the teams as specified in the XML.

            foreach ($team in $XmlDocument.Teams.Team ) {
                try {
                    $group = New-Team -DisplayName $team.Name -Description $teams.description -visibility public 
                    Write-Host "Successfully created team: " $group.DisplayName
                }
                catch {
                    Write-Host "Unable to create team: $_"
                }

                # 3. Add users to the newly created teams.
                foreach ($user in $team.Members.Member) {
                    try {
                        $newUserPrincipalName = (Get-AzureADUser -SearchString $user.UserName).UserPrincipalName

                        if($user.IsOwner -eq $true){
                            Add-TeamUser -GroupId $group.GroupId -User $newUserPrincipalName -Role Owner | Out-Null
                        }else{
                            Add-TeamUser -GroupId $group.GroupId -User $newUserPrincipalName | Out-Null
                        }

                        Write-Host "Successfully added user : " $user.UserName
                    }
                    catch {
                        Write-Host "Unable to add team user: $_"
                    }

                }

                # 4. Add a set of channels to each newly created team
                foreach ($channel in $team.Channels.Channel) {
                    try {
                        # Adding each team channel
                        New-TeamChannel -GroupId $group.GroupId -DisplayName $channel.Name -Description $channel.Description | Out-Null
                        Write-Host "Successfully created channel: " $channel.Name
                    }
                    catch {
                        Write-Host "Unable to add new Team Channel: $_"
                    }   
                }

                Clear-Variable -Name group
            }

            Clear-Variable -Name creds

            # 5. Disconnect from all PowerShell sessions

            Write-Host "Completed execution and disconnecting from Microsoft 365 PowerShell sessions."
            Disconnect-MicrosoftTeams
            Disconnect-AzureAD
        }
        catch {
            Write-Host "Unable to complete the operation: $_"
        }
    }
    else {
        Write-Host "Content file has invalid data."
    }
    ```

3. <span data-ttu-id="78bf1-127">Öffnen Sie Windows PowerShell sitzung im Administratormodus, und führen Sie das Skript aus, das Sie gerade gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="78bf1-127">Open a Windows PowerShell session in Administrator mode, and run the script that you just saved.</span></span>
4. <span data-ttu-id="78bf1-128">Wenn Sie aufgefordert werden, die Anmeldeinformationen zur Verfügung zu stellen, geben Sie die Anmeldeinformationen des globalen Administrators ein, die Sie bei der ersten Anmeldung für Ihr Entwicklerabonnement erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="78bf1-128">When you are prompted to provide the credentials, enter the Global Administrator credentials you received when you first signed up for your developer subscription.</span></span>

    > [!Note]
    > <span data-ttu-id="78bf1-129">Schließen Sie die PowerShell-Sitzung nicht, da die Ausführung des Skripts einige Minuten dauert.</span><span class="sxs-lookup"><span data-stu-id="78bf1-129">Do not close your PowerShell session as the script takes several minutes to execute.</span></span> <span data-ttu-id="78bf1-130">Wenn Sie die Benutzer in Ihrem Abonnement von dem geändert haben, was im Standardinhaltspaket erstellt wurde, werden einige Benutzer möglicherweise nicht zu Teams hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="78bf1-130">If you have modified the users in your subscription from what is created in the default content pack, some users may not be added to Teams.</span></span> <span data-ttu-id="78bf1-131">Während der Ausführung des Skripts werden erfolgreiche oder fehlgeschlagene Aktionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78bf1-131">As the script executes it displays successful or failed actions.</span></span>

5. <span data-ttu-id="78bf1-132">Nachdem das Skript ausgeführt wurde, können Sie sich beim Teams-Client mit einem der Benutzerkonten anmelden und die neu erstellten Teams anzeigen.</span><span class="sxs-lookup"><span data-stu-id="78bf1-132">After the script has finished execution, you can sign in to the Teams client with one of the user accounts and view the newly created teams.</span></span>

## <a name="see-also"></a><span data-ttu-id="78bf1-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="78bf1-133">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78bf1-134">Debuggen Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="78bf1-134">Debug your tab</span></span>](~/tabs/how-to/developer-tools.md)
 
> [!div class="nextstepaction"]
> [<span data-ttu-id="78bf1-135">Debuggen Ihrer Bots</span><span class="sxs-lookup"><span data-stu-id="78bf1-135">Debug your bots</span></span>](~/bots/how-to/debug/locally-with-an-ide.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="78bf1-136">Testen von RSC-Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="78bf1-136">Test RSC permissions</span></span>](~/graph-api/rsc/test-resource-specific-consent.md)

