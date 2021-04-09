---
title: Hinzufügen von Testdaten zu Ihrem Microsoft 365-Test-Mandanten
description: Einrichten Ihres Office 365-Entwicklerprogrammabonnements für erfolgreiche Tests von Microsoft Teams Apps
ms.topic: how-to
keywords: Testen von Entwicklerprogrammteams für Apps
ms.date: 11/01/2019
ms.openlocfilehash: 9e23b9054f45ccff6c08b97c72f4d5375fef58ea
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634720"
---
# <a name="add-test-data-to-your-microsoft-365-test-tenant"></a>Hinzufügen von Testdaten zu Ihrem Microsoft 365-Test-Mandanten

Mit einem Microsoft 365-Entwicklerabonnement können Sie Ihre Microsoft Teams-App mit Testteams, Kanälen und Benutzern verwenden.

## <a name="prerequisites"></a>Voraussetzungen

1. [Nehmen Sie am Microsoft 365 Developer Program teil,](/office/developer-program/office-365-developer-program)wenn Sie keinen Test mandanten haben.
2. [Richten Sie ein Microsoft 365-Entwicklerabonnement ein.](/office/developer-program/office-365-developer-program-get-started)
3. [Verwenden Sie Beispieldatenpakete mit Ihrem Microsoft 365-Entwicklerabonnement, um das Users Content Pack zu installieren.](/office/developer-program/install-sample-packs)
4. [Installieren Sie das Teams PowerShell-Modul](https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.2).
5. [Installieren Sie das Azure AD PowerShell-Modul](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0#installing-the-azure-ad-module&preserve-view=true).

> [!NOTE]
> Für jeden mandanten, den Sie verwenden, müssen Sie die globalen Administratorberechtigungen zum Ausführen der Skripts erhalten.

## <a name="enable-custom-app-sideloading"></a>Aktivieren des Querladens von benutzerdefinierten Apps

Das Aktivieren der benutzerdefinierten App-Querladen ist optional. Standardmäßig können nur globale Administratoren oder Teams-Dienstadministratoren benutzerdefinierte Apps in den Mandanten-App-Katalog hochladen. Sie können Benutzern auch erlauben, benutzerdefinierte Apps in Teams hochzuladen. Weitere Informationen finden Sie unter [Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies).

## <a name="create-teams-and-channels"></a>Erstellen von Teams und Kanälen

1. Speichern Sie den folgenden Codeausschnitt als **XML-Datei,** und notieren Sie sich den Dateipfad. In dieser XML wird die Struktur des Teams und Kanals definiert, das zusammen mit seinen Mitgliedern erstellt wird:

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

2. Speichern Sie den folgenden Codeausschnitt als PowerShell-Skript (PS1), und notieren Sie sich, wo Sie ihn gespeichert haben. Dieses Skript führt die Schritte aus, um das Team und den Kanal zu erstellen und ihnen Mitglieder hinzuzufügen:

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

3. Öffnen Sie Windows PowerShell sitzung im Administratormodus, und führen Sie das Skript aus, das Sie gerade gespeichert haben.
4. Wenn Sie aufgefordert werden, die Anmeldeinformationen zur Verfügung zu stellen, geben Sie die Anmeldeinformationen des globalen Administrators ein, die Sie bei der ersten Anmeldung für Ihr Entwicklerabonnement erhalten haben.

    > [!Note]
    > Schließen Sie die PowerShell-Sitzung nicht, da die Ausführung des Skripts einige Minuten dauert. Wenn Sie die Benutzer in Ihrem Abonnement von dem geändert haben, was im Standardinhaltspaket erstellt wurde, werden einige Benutzer möglicherweise nicht zu Teams hinzugefügt. Während der Ausführung des Skripts werden erfolgreiche oder fehlgeschlagene Aktionen angezeigt.

5. Nachdem das Skript ausgeführt wurde, können Sie sich beim Teams-Client mit einem der Benutzerkonten anmelden und die neu erstellten Teams anzeigen.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Debuggen Ihrer Registerkarte](~/tabs/how-to/developer-tools.md)
 
> [!div class="nextstepaction"]
> [Debuggen Ihrer Bots](~/bots/how-to/debug/locally-with-an-ide.md)

> [!div class="nextstepaction"]
> [Testen von RSC-Berechtigungen](~/graph-api/rsc/test-resource-specific-consent.md)

