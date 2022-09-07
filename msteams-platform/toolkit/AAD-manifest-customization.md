---
title: Bearbeiten des Azure Active Directory-Manifests im Teams-Toolkit
author: zyxiaoyuer
description: Beschreibt das Verwalten der Azure Active Directory-Anwendung im Teams-Toolkit
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/20/2022
ms.openlocfilehash: 2091649581686b376d2486a874118d36fd6a984b
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616653"
---
# <a name="edit-azure-ad-manifest"></a>Bearbeiten des Azure AD-Manifests

Das [Azure Active Directory (Azure AD)-Manifest](/azure/active-directory/develop/reference-app-manifest) enthält Definitionen aller Attribute eines Azure AD-Anwendungsobjekts in der Microsoft Identity Platform.

Das Teams-Toolkit verwaltet jetzt die Azure AD-Anwendung mit der Manifestdatei als Quelle der Wahrheit während des Entwicklungslebenszyklus Ihrer Teams-Anwendung.

In diesem Abschnitt werden folgende Themen behandelt:

* [Anpassen der Azure AD-Manifestvorlage](#customize-azure-ad-manifest-template)
* [Platzhalter für Azure AD-Manifestvorlagen](#azure-ad-manifest-template-placeholders)
* [Erstellen und Anzeigen einer Vorschau des Azure AD-Manifests mit Codeobjektiv](#author-and-preview-azure-ad-manifest-with-code-lens)
* [Bereitstellen von Azure AD-Anwendungsänderungen für die lokale Umgebung](#deploy-azure-ad-application-changes-for-local-environment)
* [Bereitstellen von Azure AD-Anwendungsänderungen für die Remoteumgebung](#deploy-azure-ad-application-changes-for-remote-environment)
* [Anzeigen der Azure AD-Anwendung auf dem Azure-Portal](#view-azure-ad-application-on-the-azure-portal)
* [Verwenden einer vorhandenen Azure AD-Anwendung](#use-an-existing-azure-ad-application)
* [Azure AD-Anwendung im Entwicklungslebenszyklus von Teams-Anwendungen](#azure-ad-application-in-teams-application-development-lifecycle)

## <a name="customize-azure-ad-manifest-template"></a>Anpassen der Azure AD-Manifestvorlage

Sie können die Azure AD-Manifestvorlage anpassen, um die Azure AD-Anwendung zu aktualisieren.

1. Öffnen Sie `aad.template.json` in Ihrem Projekt.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add template.png" alt-text="template":::

2. Aktualisieren Sie die Vorlage direkt, oder [verweisen Sie auf Werte aus einer anderen Datei](https://github.com/OfficeDev/TeamsFx/wiki/Manage-AAD-application-in-Teams-Toolkit#Placeholders-in-AAD-manifest-template). Hier finden Sie mehrere Anpassungsszenarien:
  
   * [Hinzufügen einer Anwendungsberechtigung](#add-an-application-permission)
   * [Vorautorisieren einer Clientanwendung](#preauthorize-a-client-application)
   * [Aktualisieren der Umleitungs-URL für die Authentifizierungsantwort](#update-redirect-url-for-authentication-response)

3. [Stellen Sie Azure AD-Anwendungsänderungen für die lokale Umgebung bereit](#deploy-azure-ad-application-changes-for-local-environment).
  
4. [Stellen Sie Azure AD-Anwendungsänderungen für die Remoteumgebung bereit](#deploy-azure-ad-application-changes-for-remote-environment).

### <a name="add-an-application-permission"></a>Hinzufügen einer Anwendungsberechtigung

Wenn die Teams-Anwendung mehr Berechtigungen zum Aufrufen der API mit zusätzlichen Berechtigungen benötigt, müssen Sie die Eigenschaft in der Azure AD-Manifestvorlage aktualisieren `requiredResourceAccess` . Sie können das folgende Beispiel für diese Eigenschaft sehen:

```JSON

   "requiredResourceAccess": [
    {
        "resourceAppId": "Microsoft Graph",
        "resourceAccess": [
            {
                "id": "User.Read", // For Microsoft Graph API, you can also use uuid for permission id
                "type": "Scope" // Scope is for delegated permission
            },
            {
                "id": "User.Export.All",
                "type": "Role" // Role is for application permission
            }
        ]
    },
    {
        "resourceAppId": "Office 365 SharePoint Online",
        "resourceAccess": [
            {
                "id": "AllSites.Read",
                "type": "Scope"
            }
        ]
    }
]
```

* `resourceAppId` -Eigenschaft wird für verschiedene APIs verwendet. `Microsoft Graph` Geben Sie den Namen direkt anstelle von UUID ein, und `Office 365` `SharePoint Online`verwenden Sie für andere APIs UUID.

* `resourceAccess.id` wird für unterschiedliche Berechtigungen verwendet. `Microsoft Graph` Geben Sie den Berechtigungsnamen direkt anstelle von UUID ein, und `Office 365 SharePoint Online`verwenden Sie für andere APIs UUID.

* `resourceAccess.type` -Eigenschaft wird für delegierte Berechtigungen oder Anwendungsberechtigungen verwendet. `Scope` bedeutet delegierte Berechtigung und `Role` bedeutet Anwendungsberechtigung.

### <a name="preauthorize-a-client-application"></a>Vorautorisieren einer Clientanwendung

Mithilfe der `preAuthorizedApplications` Eigenschaft können Sie eine Clientanwendung autorisieren, um anzugeben, dass die API der Anwendung vertraut. Benutzer stimmen nicht zu, wenn der Client die verfügbar gemachte API aufruft. Sie können das folgende Beispiel für diese Eigenschaft sehen:

```JSON

    "preAuthorizedApplications": [
        {
            "appId": "1fec8e78-bce4-4aaf-ab1b-5451cc387264",
            "permissionIds": [
                "{{state.fx-resource-aad-app-for-teams.oauth2PermissionScopeId}}"
            ]
        }
        ...
    ]
```

`preAuthorizedApplications.appId` wird für die Anwendung verwendet, die Sie autorisieren möchten. Wenn Sie die Anwendungs-ID nicht kennen und nur den Anwendungsnamen kennen, führen Sie die folgenden Schritte aus, um die Anwendungs-ID zu durchsuchen:

1. Wechseln Sie zu [Azure-Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), und öffnen **Sie Anwendungsregistrierungen**.

1. Wählen Sie **"Alle Anwendungen** " aus, und suchen Sie nach dem Namen der Anwendung.

1. Wählen Sie den Anwendungsnamen aus, und rufen Sie die Anwendungs-ID von der Übersichtsseite ab.

### <a name="update-redirect-url-for-authentication-response"></a>Aktualisieren der Umleitungs-URL für die Authentifizierungsantwort

  Umleitungs-URLs werden beim Zurückgeben von Authentifizierungsantworten wie Token nach erfolgreicher Authentifizierung verwendet. Sie können Umleitungs-URLs mithilfe der Eigenschaft `replyUrlsWithType`anpassen. Wenn Sie beispielsweise eine Umleitungs-URL hinzufügen `https://www.examples.com/auth-end.html` möchten, können Sie sie im folgenden Beispiel hinzufügen:

``` JSON
"replyUrlsWithType": [
    ...
    {
        "url": "https://www.examples.com/auth-end.html",
        "type": "Spa"
    }
]
```

## <a name="azure-ad-manifest-template-placeholders"></a>Platzhalter für Azure AD-Manifestvorlagen

Die Azure AD-Manifestdatei enthält Platzhalterargumente mit {{...}} wird während des Builds für unterschiedliche Umgebungen ersetzt. Mit den Platzhalterargumenten können Sie Verweise auf Konfigurationsdatei-, Zustandsdatei- und Umgebungsvariablen erstellen.

### <a name="reference-state-file-values-in-azure-ad-manifest-template"></a>Referenzstatusdateiwerte in der Azure AD-Manifestvorlage

Die Statusdatei befindet sich in `.fx\states\state.xxx.json` (xxx stellt eine andere Umgebung dar). Das folgende Beispiel zeigt eine typische Statusdatei:

``` JSON
{
    "solution": {
        "teamsAppTenantId": "uuid",
        ...
    },
    "fx-resource-aad-app-for-teams": {
        "applicationIdUris": "api://xxx.com/uuid",
        ...
    }
    ...
}
```

Sie können dieses Platzhalterargument im Azure AD-Manifest verwenden, `{{state.fx-resource-aad-app-for-teams.applicationIdUris}}` um auf den Wert in der `fx-resource-aad-app-for-teams` Eigenschaft hinzuweisen`applicationIdUris`.

### <a name="reference-config-file-values-in-azure-ad-manifest-template"></a>Referenzkonfigurationsdateiwerte in der Azure AD-Manifestvorlage

Die Konfigurationsdatei befindet sich in `.fx\configs\config.xxx.json` (xxx stellt eine andere Umgebung dar). Das folgende Beispiel zeigt die Konfigurationsdatei:

``` JSON
{
  "$schema": "https://aka.ms/teamsfx-env-config-schema",
  "description": "description.",
  "manifest": {
    "appName": {
      "short": "app",
      "full": "Full name for app"
    }
  }
}
```

Sie können das Platzhalterargument im Azure AD-Manifest verwenden: `{{config.manifest.appName.short}}` um auf den Wert zu verweisen `short` .

### <a name="reference-environment-variable-in-azure-ad-manifest-template"></a>Referenzumgebungsvariable in der Azure AD-Manifestvorlage

Manchmal möchten Sie die Werte in der Azure AD-Manifestvorlage nicht hartcodieren. Wenn der Wert beispielsweise ein geheimer Schlüssel ist. Die Azure AD-Manifestvorlagendatei unterstützt Werte für Referenzumgebungsvariablen. Sie können die Syntax `{{env.YOUR_ENV_VARIABLE_NAME}}` in Parameterwerten verwenden, um das Tool anzuweisen, den Wert der aktuellen Umgebungsvariablen aufzulösen.

## <a name="author-and-preview-azure-ad-manifest-with-code-lens"></a>Erstellen und Anzeigen einer Vorschau des Azure AD-Manifests mit Codeobjektiv

Die Azure AD-Manifestvorlagendatei verfügt über ein Codeobjektiv zum Überprüfen und Bearbeiten.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/preview view.png" alt-text="Vorschauansicht":::

### <a name="azure-ad-manifest-template-file"></a>Azure AD-Manifestvorlagendatei

Am Anfang der Azure AD-Manifestvorlagendatei befindet sich ein Vorschaucodeobjektiv. Wählen Sie das Codeobjektiv aus, um ein Azure AD-Manifest basierend auf Ihrer ausgewählten Umgebung zu generieren.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add codelens.png" alt-text="addcodelens":::

### <a name="placeholder-argument-code-lens"></a>Codeobjektiv für Platzhalterargumente

Das Platzhalterargument-Codeobjektiv hilft Ihnen, die Werte für die lokale Debug- und Entwicklungsumgebung schnell zu ermitteln. Wenn Sie mit der Maus auf das Platzhalterargument zeigen, wird ein QuickInfo-Feld für die Werte der gesamten Umgebung angezeigt.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add arguments.png" alt-text="addarguments":::

### <a name="required-resource-access-code-lens"></a>Codeobjektiv für den erforderlichen Ressourcenzugriff

Es unterscheidet sich vom offiziellen [Azure AD-Manifestschema](/azure/active-directory/develop/reference-app-manifest) , dass `resourceAppId` und `resourceAccess` die ID in der `requiredResourceAccess` Eigenschaft nur UUID unterstützt. Die Azure AD-Manifestvorlage im Teams-Toolkit unterstützt auch benutzerlesbare Zeichenfolgen für `Microsoft Graph` und `Office 365 SharePoint Online` Berechtigungen. Wenn Sie UUID eingeben, zeigt die Codelinse lesbare Zeichenfolgen an, andernfalls wird UUID angezeigt.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/add resource.png" alt-text="addresource":::

### <a name="pre-authorized-applications-code-lens"></a>Codeobjektiv für vorab autorisierte Anwendungen

Die Codelinse zeigt den Anwendungsnamen für die vor autorisierte Anwendungs-ID für die `preAuthorizedApplications` Eigenschaft an.

## <a name="deploy-azure-ad-application-changes-for-local-environment"></a>Bereitstellen von Azure AD-Anwendungsänderungen für die lokale Umgebung

1. Wählen Sie `Preview` das Codeobjektiv in `aad.template.json`aus.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy1.png" alt-text="deploy1":::

2. Wählen Sie **die lokale** Umgebung aus.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy2.png" alt-text="deploy2":::

3. Wählen Sie `Deploy Azure AD Manifest` das Codeobjektiv in `aad.local.json`aus.

     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy3.png" alt-text="deploy3":::

4. Die Änderungen für die Azure AD-Anwendung, die in der lokalen Umgebung verwendet wird, werden bereitgestellt.
  
## <a name="deploy-azure-ad-application-changes-for-remote-environment"></a>Bereitstellen von Azure AD-Anwendungsänderungen für die Remoteumgebung

1. Öffnen Sie die Befehlspalette, und wählen Sie Folgendes aus: `Teams: Deploy Azure Active Directory application manifest`.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy4.png" alt-text="deploy4":::

2. Sie können auch mit der rechten Maustaste auf das `aad.template.json` Kontextmenü klicken und aus dem Kontextmenü auswählen `Deploy Azure Active Directory application manifest` .
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add deploy5.png" alt-text="deploy5":::

## <a name="view-azure-ad-application-on-the-azure-portal"></a>Anzeigen der Azure AD-Anwendung auf dem Azure-Portal

1. Kopieren Sie die Azure AD-Anwendungsclient-ID aus der `state.xxx.json` ()Datei in der `fx-resource-aad-app-for-teams` Eigenschaft.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view1.png" alt-text="Ansicht 1":::

   > [!NOTE]
   > xxx in der Client-ID gibt den Namen der Umgebung an, in der Sie die Azure AD-Anwendung bereitgestellt haben.

2. Wechseln Sie zu [Azure-Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), und melden Sie sich beim Microsoft 365-Konto an.
  
   > [!NOTE]
   > Stellen Sie sicher, dass die Anmeldeinformationen der Teams-Anwendung und des M365-Kontos identisch sind.

3. Öffnen Sie [die Seite "App-Registrierungen"](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), und durchsuchen Sie die Azure AD-Anwendung mithilfe der Client-ID, die Sie zuvor kopiert haben.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view2.png" alt-text="Ansicht 2":::

4. Wählen Sie die Azure AD-Anwendung aus dem Suchergebnis aus, um die Detailinformationen anzuzeigen.
  
5. Wählen Sie auf der Informationsseite der Azure AD-App das Menü aus, um das `Manifest` Manifest dieser Anwendung anzuzeigen. Das Schema des Manifests ist mit dem Schema in `aad.template.json` der Datei identisch. Weitere Informationen zum Manifest finden Sie unter [Azure Active Directory-Anwendungsmanifest](/azure/active-directory/develop/reference-app-manifest).
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add view3.png" alt-text="Ansicht 3":::

6. Sie können " **Anderes Menü** " auswählen, um die Azure AD-Anwendung über das Portal anzuzeigen oder zu konfigurieren.
  
## <a name="use-an-existing-azure-ad-application"></a>Verwenden einer vorhandenen Azure AD-Anwendung

Sie können die vorhandene Azure AD-Anwendung für das Teams-Projekt verwenden. Weitere Informationen finden [Sie unter Verwenden einer vorhandenen Azure AD-Anwendung für Ihre Teams-Anwendung](https://github.com/OfficeDev/TeamsFx/wiki/Customize-provision-behaviors#use-an-existing-aad-app-for-your-teams-app).

## <a name="azure-ad-application-in-teams-application-development-lifecycle"></a>Azure AD-Anwendung im Entwicklungslebenszyklus von Teams-Anwendungen

Sie müssen während verschiedener Phasen des Entwicklungslebenszyklus Ihrer Teams-Anwendung mit der Azure AD-Anwendung interagieren.

1. **So erstellen Sie Project**

      Sie können ein Projekt mit dem Teams-Toolkit erstellen, das standardmäßig SSO-Unterstützung bietet, z `SSO-enabled tab`. B. . Weitere Informationen zum Erstellen einer neuen App finden Sie unter [Erstellen einer neuen Teams-Anwendung mithilfe des Teams-Toolkits](create-new-project.md). Eine Azure AD-Manifestdatei wird automatisch für Sie `templates\appPackage\aad.template.json`in erstellt. Das Teams-Toolkit erstellt oder aktualisiert die Azure AD-Anwendung während der lokalen Entwicklung oder beim Verschieben der Anwendung in die Cloud.

2. **So fügen Sie SSO zu Ihrem Bot oder Ihrer Registerkarte hinzu**

      Nachdem Sie eine Teams-Anwendung ohne integriertes SSO erstellt haben, hilft Ihnen das Teams-Toolkit inkrementell, SSO für das Projekt hinzuzufügen. Daher wird automatisch eine Azure AD-Manifestdatei in `templates\appPackage\aad.template.json`erstellt.

      Das Teams-Toolkit erstellt oder aktualisiert die Azure AD-Anwendung während der nächsten lokalen Debugsitzung oder beim Verschieben der Anwendung in die Cloud.

3. **So erstellen Sie lokal**

    Das Teams-Toolkit führt die folgenden Funktionen während der lokalen Entwicklung aus, oder es wird als F5 bezeichnet:

    * Lesen Sie die `state.local.json` Datei, um eine vorhandene Azure AD-Anwendung zu finden. Wenn bereits eine Azure AD-Anwendung vorhanden ist, verwendet das Teams-Toolkit die vorhandene Azure AD-Anwendung wieder. Andernfalls müssen Sie eine neue Anwendung mithilfe der `aad.template.json` Datei erstellen.

    * Zunächst werden einige Eigenschaften in der Manifestdatei ignoriert, die mehr Kontext erfordern (z. B. replyUrls-Eigenschaft, die einen lokalen Debugendpunkt erfordert) während der Erstellung einer neuen Azure AD-Anwendung mit der Manifestdatei.

    * Nach dem erfolgreichen Start der lokalen Entwicklungsumgebung werden die IdentifierUris, replyUrls und anderen Eigenschaften der Azure AD-Anwendung, die während der Erstellungsphase nicht verfügbar sind, entsprechend aktualisiert.

    * Die Änderungen, die Sie an Ihrer Azure AD-Anwendung vorgenommen haben, werden während der nächsten lokalen Debugsitzung geladen. Sie können [Änderungen der Azure AD-Anwendung](https://github.com/OfficeDev/TeamsFx/wiki/) anzeigen, um Änderungen manuell an der Azure AD-Anwendung anzuwenden.

4. **So stellen Sie Cloudressourcen bereit**

      Sie müssen Cloudressourcen bereitstellen und Ihre Anwendung bereitstellen, während Sie Ihre Anwendung in die Cloud verschieben. In den Phasen wie der lokalen Entwicklung wird das Teams-Toolkit Folgendes ausführen:

      * Lesen Sie die `state.{env}.json` Datei, um eine vorhandene Azure AD-Anwendung zu finden. Wenn bereits eine Azure AD-Anwendung vorhanden ist, verwendet das Teams-Toolkit die vorhandene Azure AD-Anwendung erneut. Andernfalls müssen Sie eine neue Anwendung mithilfe der `aad.template.json` Datei erstellen.

      * Zunächst werden einige Eigenschaften in der Manifestdatei ignoriert, die mehr Kontext erfordern (z. B. replyUrls-Eigenschaft erfordert Frontend oder Bot-Endpunkt) während der Erstellung einer neuen Azure AD-Anwendung mit der Manifestdatei.

      * Nach Abschluss der Bereitstellung anderer Ressourcen werden die IdentifierUris und replyUrls der Azure AD-Anwendung entsprechend auf die richtigen Endpunkte aktualisiert.

5. **So erstellen Sie eine Anwendung**

    * Mit dem Befehl "In der Cloud bereitstellen" wird Ihre Anwendung für die bereitgestellten Ressourcen bereitgestellt. Dies schließt nicht die Bereitstellung von Änderungen der Azure AD-Anwendung ein, die Sie vorgenommen haben.

    * Sie können sehen, [Bereitstellen von Azure AD-Anwendungsänderungen für die Remoteumgebung](#deploy-azure-ad-application-changes-for-remote-environment) , um Azure AD-Anwendungsänderungen für die Remoteumgebung bereitzustellen.

    * Das Teams-Toolkit aktualisiert die Azure AD-Anwendung gemäß der Azure AD-Manifestvorlagendatei.

## <a name="limitations"></a>Einschränkungen

1. Die Erweiterung des Teams-Toolkits unterstützt nicht alle Eigenschaften, die im Azure AD-Manifestschema aufgeführt sind.
  
      In der folgenden Tabelle sind die Eigenschaften aufgeführt, die in der Erweiterung des Teams-Toolkits nicht unterstützt werden:

      |**Nicht unterstützte Eigenschaften**|**Grund**|
      |-----------|----------|
      |passwordCredentials|Im Manifest nicht zulässig|
      |createdDateTime|Schreibgeschützt und kann nicht geändert werden|
      |logoUrl|Schreibgeschützt und kann nicht geändert werden|
      |publisherDomain|Schreibgeschützt und kann nicht geändert werden|
      |oauth2RequirePostResponse|In Graph-API nicht vorhanden|
      |oauth2AllowUrlPathMatching|In Graph-API nicht vorhanden|
      |samlMetadataUrl|In Graph-API nicht vorhanden|
      |orgRestrictions|In Graph-API nicht vorhanden|
      |Zertifizierung|In Graph-API nicht vorhanden|

2. Derzeit `requiredResourceAccess` kann die Eigenschaft nur für benutzerlesbare Ressourcenanwendungsnamen oder Berechtigungsnamenzeichenfolgen und `Office 365 SharePoint Online` APIs `Microsoft Graph` verwendet werden. Für andere APIs müssen Sie stattdessen UUID verwenden. Sie können die folgenden Schritte ausführen, um IDs aus Azure-Portal abzurufen:

    * Registrieren Sie eine neue Azure AD-Anwendung auf [Azure-Portal](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
    * Wählen Sie `API permissions` auf der Azure AD-Anwendungsseite aus.
    * Wählen Sie diese Option aus `add a permission` , um die gewünschte Berechtigung hinzuzufügen.
    * Wählen Sie `Manifest`aus der Eigenschaft die `requiredResourceAccess` IDs der API und Berechtigungen aus.

## <a name="see-also"></a>Siehe auch

* [Vorschau und Anpassen des App-Manifests im Toolkit](TeamsFx-preview-and-customize-app-manifest.md)
