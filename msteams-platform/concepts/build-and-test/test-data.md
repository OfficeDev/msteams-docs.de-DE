---
title: Hinzufügen von Testdaten zu Ihrem Microsoft 365-Test-Mandanten
description: Einrichten Ihres Office 365-Entwicklerprogrammabonnements für erfolgreiche Tests von Microsoft Teams Apps
ms.topic: how-to
keywords: Testen von Entwicklerprogrammteams für Apps
ms.date: 11/01/2019
ms.openlocfilehash: 863f1d9843bb3ebe968ca180ee70a5b6bfa6cd7a
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596189"
---
# <a name="add-test-data-to-your-microsoft-365-test-tenant"></a><span data-ttu-id="7841d-104">Hinzufügen von Testdaten zu Ihrem Microsoft 365-Test-Mandanten</span><span class="sxs-lookup"><span data-stu-id="7841d-104">Add test data to your Microsoft 365 test tenant</span></span>

<span data-ttu-id="7841d-105">Mit einem Microsoft 365-Entwicklerabonnement können Sie Ihre Microsoft Teams-App mit Testteams, Kanälen und Benutzern verwenden.</span><span class="sxs-lookup"><span data-stu-id="7841d-105">With a Microsoft 365 developer subscription, you can use your Microsoft Teams app with test teams, channels, and users.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7841d-106">Vor dem Start</span><span class="sxs-lookup"><span data-stu-id="7841d-106">Before you start</span></span>

<span data-ttu-id="7841d-107">Wenn Sie noch keinen Test-Mandanten haben, müssen Sie am Office 365-Entwicklerprogramm teilnehmen und sich für ein Entwicklerabonnement registrieren.</span><span class="sxs-lookup"><span data-stu-id="7841d-107">If you don't already have a test tenant, you will need to join the Office 365 developer program and sign up for a developer subscription.</span></span> <span data-ttu-id="7841d-108">Sie müssen auch die erforderlichen PowerShell-Module installieren.</span><span class="sxs-lookup"><span data-stu-id="7841d-108">You'll also need to install the necessary PowerShell modules.</span></span> <span data-ttu-id="7841d-109">Für jeden Mandanten, den Sie verwenden, benötigen Sie globale Administratorberechtigungen, um die Skripts ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="7841d-109">For whatever tenant you use you'll need to have global administrator permissions to run the scripts.</span></span>

1. [<span data-ttu-id="7841d-110">Teilnehmen am Microsoft 365-Entwicklerprogramm</span><span class="sxs-lookup"><span data-stu-id="7841d-110">Join the Microsoft 365 Developer Program</span></span>](/office/developer-program/office-365-developer-program)
2. [<span data-ttu-id="7841d-111">Einrichten eines Microsoft 365-Entwicklerabonnements</span><span class="sxs-lookup"><span data-stu-id="7841d-111">Set up a Microsoft 365 Developer Subscription</span></span>](/office/developer-program/office-365-developer-program-get-started)
3. [<span data-ttu-id="7841d-112">Verwenden von Beispieldatenpaketen mit Ihrem Microsoft 365-Entwicklerabonnement zum Installieren des Inhaltspakets "Benutzer"</span><span class="sxs-lookup"><span data-stu-id="7841d-112">Use sample data packs with your Microsoft 365 developer subscription to install the Users content pack</span></span>](/office/developer-program/install-sample-packs)
4. [<span data-ttu-id="7841d-113">Installieren des Teams PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="7841d-113">Install the Teams PowerShell module</span></span>](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)
5. [<span data-ttu-id="7841d-114">Installieren des Azure AD PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="7841d-114">Install the Azure AD PowerShell module</span></span>](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module&preserve-view=true)

## <a name="optional-enable-custom-app-sideloading"></a><span data-ttu-id="7841d-115">(Optional) Aktivieren des Querladens von benutzerdefinierten Apps</span><span class="sxs-lookup"><span data-stu-id="7841d-115">(Optional) Enable custom app sideloading</span></span>

<span data-ttu-id="7841d-116">Standardmäßig können nur globale Administratoren oder Teams-Dienstadministratoren benutzerdefinierte Apps in den Mandanten-App-Katalog hochladen.</span><span class="sxs-lookup"><span data-stu-id="7841d-116">By default, only global admins or Teams service admins can upload custom apps into the tenant app catalog.</span></span> <span data-ttu-id="7841d-117">Sie können Benutzern auch erlauben, benutzerdefinierte Apps in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="7841d-117">You can also allow users to upload custom apps to Teams.</span></span> <span data-ttu-id="7841d-118">Weitere Informationen finden Sie [unter Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="7841d-118">For more information, [manage app setup policies in Teams](/microsoftteams/teams-app-setup-policies).</span></span>

## <a name="create-teams-and-channels"></a><span data-ttu-id="7841d-119">Erstellen von Teams und Kanälen</span><span class="sxs-lookup"><span data-stu-id="7841d-119">Create teams and channels</span></span>

<span data-ttu-id="7841d-120">Speichern Sie den folgenden Codeausschnitt als XML (XML), und notieren Sie sich, wo Sie ihn gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="7841d-120">Save the following snippet as an XML (.xml) and note where you've saved it.</span></span>  <span data-ttu-id="7841d-121">Diese XML definiert die Struktur der Teams und Kanäle, die erstellt werden , zusammen mit ihren Mitgliedern.</span><span class="sxs-lookup"><span data-stu-id="7841d-121">This XML defines the structure of the teams and channels that will be created - along with its members.</span></span>

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

<span data-ttu-id="7841d-122">Speichern Sie den folgenden Codeausschnitt als PowerShell-Skript (PS1), und notieren Sie sich, wo Sie ihn gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="7841d-122">Save the following snippet as a PowerShell script (.ps1) and note where you've saved it.</span></span>  <span data-ttu-id="7841d-123">Dieses Skript führt die Schritte aus, um die Teams und Kanäle zu erstellen und ihnen Mitglieder hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7841d-123">This script executes the steps to create the teams and channels and add members to them.</span></span>

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

<span data-ttu-id="7841d-124">Öffnen Sie eine Windows PowerShell im Administratormodus.</span><span class="sxs-lookup"><span data-stu-id="7841d-124">Open a Windows PowerShell session in Administrator mode.</span></span>  <span data-ttu-id="7841d-125">Führen Sie das Skript aus, das Sie gerade gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="7841d-125">Run the script that you just saved.</span></span>  <span data-ttu-id="7841d-126">Sie werden aufgefordert, die Anmeldeinformationen zur Verfügung zu stellen – verwenden Sie die Anmeldeinformationen des globalen Administrators, die Sie bei der ersten Anmeldung für Ihr Entwicklerabonnement erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="7841d-126">You'll be prompted to provide the credentials - use the Global Administrator credentials you received when you first signed up for your developer subscription.</span></span>

> [!Note]
> <span data-ttu-id="7841d-127">Die Ausführung des Skripts dauert einige Minuten – schließen Sie ihre PowerShell-Sitzung nicht.</span><span class="sxs-lookup"><span data-stu-id="7841d-127">The script will take several minutes to execute - do not close your PowerShell session.</span></span>  <span data-ttu-id="7841d-128">Wenn Sie die Benutzer in Ihrem Abonnement von dem geändert haben, was im Standardinhaltspaket erstellt wurde, werden einige Benutzer möglicherweise nicht zu Teams hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7841d-128">If you've modified the users in your subscription from what is created in the default content pack, some users may not be added to teams.</span></span>  <span data-ttu-id="7841d-129">Wenn das Skript ausgeführt wird, werden erfolgreiche oder fehlgeschlagene Aktionen ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="7841d-129">As the script executes it will output successful or failed actions.</span></span>

<span data-ttu-id="7841d-130">Nachdem das Skript ausgeführt wurde, können Sie sich mit einem der Benutzerkonten beim Teams-Client anmelden und die neu erstellten Teams anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7841d-130">Once the script has finished execution, you can login to the Teams client with one of the user accounts and view the newly created teams.</span></span>
