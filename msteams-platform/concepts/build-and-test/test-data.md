---
title: Hinzufügen von Test Daten zum Office 365 Testmandanten
description: Einrichten Ihres Office 365-Entwicklerprogramm Abonnements für erfolgreiche Tests von Microsoft Teams-apps
keywords: Testen von apps-Entwicklerprogramm Teams
ms.date: 11/01/2019
ms.openlocfilehash: 2d32b0bf4243d540eeb5e2cc89ea2518d737ae17
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674196"
---
# <a name="add-test-data-to-your-office-365-test-tenant"></a>Hinzufügen von Test Daten zum Office 365 Testmandanten

Richten Sie Ihr O365-Entwicklerprogramm Abonnement (oder einen anderen Testmandanten) ein, damit Sie die von Ihnen erstellten Apps einfach testen können.  Es hilft Ihnen:

- Erstellen neuer Teams und Kanäle in Ihrer Organisation

- Fügen Sie die Benutzer, die über das Benutzerinhalts Paket erstellt wurden, diesen Teams hinzu.

## <a name="before-you-start"></a>Vor der Bereitstellung

Wenn Sie noch nicht über einen Testmandanten verfügen, müssen Sie am Office 365 Entwicklerprogramm teilnehmen und sich für ein Entwickler Abonnement anmelden. Außerdem müssen Sie die erforderlichen PowerShell-Module installieren. Für jeden von Ihnen verwendeten Mandanten benötigen Sie globale Administratorberechtigungen, um die Skripts auszuführen.

1. [Treten Sie dem Office 365-Entwicklerprogramm bei](/office/developer-program/office-365-developer-program)
2. [Einrichten eines Microsoft 365-Entwickler Abonnements](/office/developer-program/office-365-developer-program-get-started)
3. [Verwenden von Beispiel-Datenpaketen mit Ihrem Office 365 Entwickler-Abonnement zum Installieren des Inhaltspakets "Users"](/office/developer-program/install-sample-packs)
4. [Installieren des PowerShell-Moduls für Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2)
5. [Installieren des Azure AD PowerShell-Moduls](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module)

### <a name="optional-step-allow-upload-of-custom-apps"></a>Optionaler Schritt: Hochladen von benutzerdefinierten apps zulassen

Standardmäßig können nur globale Administratoren oder Teams-Dienstadministratoren benutzerdefinierte apps in den Mandanten-App-Katalog hochladen.  Sie können auch allen Benutzern die Möglichkeit geben, benutzerdefinierte Apps für Ihre eigene Verwendung oder für Tests in Teams hochzuladen.

Um diese Einstellung zu aktivieren, müssen Sie die globale App-Setup Richtlinie im Team-Verwaltungs Portal aktualisieren.

<img width="430px" src="~/assets/images/microsoft-teams-admin-center-screenshot.png" title="Screenshot der APP-Setup Richtlinie" />

Weitere Informationen finden Sie unter:

 - [Verwalten von App-Setup Richtlinien in Microsoft Teams](/microsoftteams/teams-app-setup-policies)

## <a name="create-teams-and-channels"></a>Erstellen von Teams und Kanälen

Speichern Sie den folgenden Codeausschnitt als XML (. Xml), und notieren Sie, wo Sie es gespeichert haben.  Dieser XML-Code definiert die Struktur der Teams und Kanäle, die erstellt werden-zusammen mit seinen Mitgliedern.

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

Speichern Sie den folgenden Codeausschnitt als PowerShell-Skript (. ps1), und notieren Sie, wo Sie es gespeichert haben.  Dieses Skript führt die Schritte zum Erstellen der Teams und Kanäle und zum Hinzufügen von Mitgliedern zu diesen aus.

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

Öffnen Sie eine Windows PowerShell Sitzung im Administrator Modus.  Führen Sie das soeben gespeicherte Skript aus.  Sie werden aufgefordert, die Anmeldeinformationen anzugeben – verwenden Sie die Anmeldeinformationen des globalen Administrators, die Sie beim ersten Anmelden für Ihr Entwickler Abonnement erhalten haben.

> [!Note]
> Das Skript dauert einige Minuten, bis die PowerShell-Sitzung geschlossen wird.  Wenn Sie die Benutzer in Ihrem Abonnement von dem, was im Standardinhalts Paket erstellt wurde, geändert haben, werden einige Benutzer möglicherweise nicht zu Microsoft Teams hinzugefügt.  Während das Skript ausgeführt wird, werden erfolgreiche oder fehlgeschlagene Aktionen ausgegeben.

Nachdem die Ausführung des Skripts abgeschlossen ist, können Sie sich mit einem der Benutzerkonten beim Microsoft Teams-Client anmelden und die neu erstellten Teams anzeigen.
