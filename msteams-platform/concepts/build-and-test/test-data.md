---
title: Hinzufügen von Test Daten zum Office 365 Testmandanten
description: Einrichten Ihres Office 365-Entwicklerprogramm Abonnements für erfolgreiche Tests von Microsoft Teams-apps
keywords: Testen von apps-Entwicklerprogramm Teams
ms.date: 11/01/2019
ms.openlocfilehash: 87e9dc280c192f013098c3e9f604f72238bfafdf
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867093"
---
# <a name="add-test-data-to-your-office-365-test-tenant"></a><span data-ttu-id="de730-104">Hinzufügen von Test Daten zum Office 365 Testmandanten</span><span class="sxs-lookup"><span data-stu-id="de730-104">Add test data to your Office 365 test tenant</span></span>

<span data-ttu-id="de730-105">Richten Sie Ihr O365-Entwicklerprogramm Abonnement (oder einen anderen Testmandanten) ein, damit Sie die von Ihnen erstellten Apps einfach testen können.</span><span class="sxs-lookup"><span data-stu-id="de730-105">Set up your O365 developer program subscription (or other test tenant) to make it easy for you to test the apps that you've built.</span></span>  <span data-ttu-id="de730-106">Es hilft Ihnen:</span><span class="sxs-lookup"><span data-stu-id="de730-106">It will help you:</span></span>

- <span data-ttu-id="de730-107">Erstellen neuer Teams und Kanäle in Ihrer Organisation</span><span class="sxs-lookup"><span data-stu-id="de730-107">Create new teams and channels in your organization</span></span>

- <span data-ttu-id="de730-108">Fügen Sie die Benutzer, die über das Benutzerinhalts Paket erstellt wurden, diesen Teams hinzu.</span><span class="sxs-lookup"><span data-stu-id="de730-108">Add the users that are created via the User content pack to those teams.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="de730-109">Vor der Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="de730-109">Before you start</span></span>

<span data-ttu-id="de730-110">Wenn Sie noch nicht über einen Testmandanten verfügen, müssen Sie am Office 365 Entwicklerprogramm teilnehmen und sich für ein Entwickler Abonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="de730-110">If you don't already have a test tenant, you will need to join the Office 365 developer program and sign up for a developer subscription.</span></span> <span data-ttu-id="de730-111">Außerdem müssen Sie die erforderlichen PowerShell-Module installieren.</span><span class="sxs-lookup"><span data-stu-id="de730-111">You'll also need to install the necessary PowerShell modules.</span></span> <span data-ttu-id="de730-112">Für jeden von Ihnen verwendeten Mandanten benötigen Sie globale Administratorberechtigungen, um die Skripts auszuführen.</span><span class="sxs-lookup"><span data-stu-id="de730-112">For whatever tenant you use you'll need to have global administrator permissions to run the scripts.</span></span>

1. [<span data-ttu-id="de730-113">Treten Sie dem Office 365 Entwickler Programm bei</span><span class="sxs-lookup"><span data-stu-id="de730-113">Join the Office 365 Developer Program</span></span>](/office/developer-program/office-365-developer-program)
2. [<span data-ttu-id="de730-114">Einrichten eines Microsoft 365-Entwickler Abonnements</span><span class="sxs-lookup"><span data-stu-id="de730-114">Set up a Microsoft 365 Developer Subscription</span></span>](/office/developer-program/office-365-developer-program-get-started)
3. [<span data-ttu-id="de730-115">Verwenden von Beispiel-Datenpaketen mit Ihrem Office 365 Entwickler-Abonnement zum Installieren des Inhaltspakets "Users"</span><span class="sxs-lookup"><span data-stu-id="de730-115">Use sample data packs with your Office 365 developer subscription to install the Users content pack</span></span>](/office/developer-program/install-sample-packs)
4. [<span data-ttu-id="de730-116">Installieren des PowerShell-Moduls für Teams</span><span class="sxs-lookup"><span data-stu-id="de730-116">Install the Teams PowerShell module</span></span>](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)
5. [<span data-ttu-id="de730-117">Installieren des Azure AD PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="de730-117">Install the Azure AD PowerShell module</span></span>](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module)

### <a name="optional-step-allow-upload-of-custom-apps"></a><span data-ttu-id="de730-118">Optionaler Schritt: Hochladen von benutzerdefinierten apps zulassen</span><span class="sxs-lookup"><span data-stu-id="de730-118">Optional step: allow upload of custom apps</span></span>

<span data-ttu-id="de730-119">Standardmäßig können nur globale Administratoren oder Teams-Dienstadministratoren benutzerdefinierte apps in den Mandanten-App-Katalog hochladen.</span><span class="sxs-lookup"><span data-stu-id="de730-119">By default, only global admins or teams service admins can upload custom apps into the tenant app catalog.</span></span>  <span data-ttu-id="de730-120">Sie können auch allen Benutzern die Möglichkeit geben, benutzerdefinierte Apps für Ihre eigene Verwendung oder für Tests in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="de730-120">You can also enable all users to upload custom apps for their own use or to teams for testing.</span></span>

<span data-ttu-id="de730-121">Um diese Einstellung zu aktivieren, müssen Sie die globale App-Setup Richtlinie im Team-Verwaltungs Portal aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="de730-121">To enable this setting, you'll need to update the global App Setup Policy in your Teams Admin Portal.</span></span>

<img width="430px" src="~/assets/images/microsoft-teams-admin-center-screenshot.png" title="Screenshot der APP-Setup Richtlinie" />

<span data-ttu-id="de730-123">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="de730-123">For more information see:</span></span>

 - [<span data-ttu-id="de730-124">Verwalten von App-Setup Richtlinien in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="de730-124">Manage app setup policies in Microsoft Teams</span></span>](/microsoftteams/teams-app-setup-policies)

## <a name="create-teams-and-channels"></a><span data-ttu-id="de730-125">Erstellen von Teams und Kanälen</span><span class="sxs-lookup"><span data-stu-id="de730-125">Create teams and channels</span></span>

<span data-ttu-id="de730-126">Speichern Sie den folgenden Codeausschnitt als XML (. Xml), und notieren Sie, wo Sie es gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="de730-126">Save the following snippet as an XML (.xml) and note where you've saved it.</span></span>  <span data-ttu-id="de730-127">Dieser XML-Code definiert die Struktur der Teams und Kanäle, die erstellt werden-zusammen mit seinen Mitgliedern.</span><span class="sxs-lookup"><span data-stu-id="de730-127">This XML defines the structure of the teams and channels that will be created - along with its members.</span></span>

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

<span data-ttu-id="de730-128">Speichern Sie den folgenden Codeausschnitt als PowerShell-Skript (. ps1), und notieren Sie, wo Sie es gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="de730-128">Save the following snippet as a PowerShell script (.ps1) and note where you've saved it.</span></span>  <span data-ttu-id="de730-129">Dieses Skript führt die Schritte zum Erstellen der Teams und Kanäle und zum Hinzufügen von Mitgliedern zu diesen aus.</span><span class="sxs-lookup"><span data-stu-id="de730-129">This script executes the steps to create the teams and channels and add members to them.</span></span>

```powershell
Param(
    [Parameter(Mandatory = $true)]
    
    # This specifies the location of your configuration XML.
    
    [string] $teamsFilePath 
)
    
[xml]$XmlDocument = Get-Content -Path $teamsFilePath.ToString()

if ($XmlDocument.Teams.Team.Count -gt 0) {

    try {
        
        # 1. Login with the global administrator account for your O365 Developer Program tenant.  This script will then use these credentials to connect to the powershell modules for Azure Active Directory and Microsoft Teams
        
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

<span data-ttu-id="de730-130">Öffnen Sie eine Windows PowerShell Sitzung im Administrator Modus.</span><span class="sxs-lookup"><span data-stu-id="de730-130">Open a Windows PowerShell session in Administrator mode.</span></span>  <span data-ttu-id="de730-131">Führen Sie das soeben gespeicherte Skript aus.</span><span class="sxs-lookup"><span data-stu-id="de730-131">Run the script that you just saved.</span></span>  <span data-ttu-id="de730-132">Sie werden aufgefordert, die Anmeldeinformationen anzugeben – verwenden Sie die Anmeldeinformationen des globalen Administrators, die Sie beim ersten Anmelden für Ihr Entwickler Abonnement erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="de730-132">You'll be prompted to provide the credentials - use the Global Administrator credentials you received when you first signed up for your developer subscription.</span></span>

> [!Note]
> <span data-ttu-id="de730-133">Das Skript dauert einige Minuten, bis die PowerShell-Sitzung geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="de730-133">The script will take several minutes to execute - do not close your PowerShell session.</span></span>  <span data-ttu-id="de730-134">Wenn Sie die Benutzer in Ihrem Abonnement von dem, was im Standardinhalts Paket erstellt wurde, geändert haben, werden einige Benutzer möglicherweise nicht zu Microsoft Teams hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="de730-134">If you've modified the users in your subscription from what is created in the default content pack, some users may not be added to teams.</span></span>  <span data-ttu-id="de730-135">Während das Skript ausgeführt wird, werden erfolgreiche oder fehlgeschlagene Aktionen ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="de730-135">As the script executes it will output successful or failed actions.</span></span>

<span data-ttu-id="de730-136">Nachdem die Ausführung des Skripts abgeschlossen ist, können Sie sich mit einem der Benutzerkonten beim Microsoft Teams-Client anmelden und die neu erstellten Teams anzeigen.</span><span class="sxs-lookup"><span data-stu-id="de730-136">Once the script has finished execution, you can login to the Teams client with one of the user accounts and view the newly created teams.</span></span>
