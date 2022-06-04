---
title: Aktualisieren des Manifests zum Aktivieren von SSO für Registerkarten
description: Beschreibt das Aktualisieren des Manifests zum Aktivieren von SSO für Registerkarten
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Microsoft Azure Active Directory (Azure AD) Graph-API
ms.openlocfilehash: 0bc50b61d5beac45ae11ec1264cd6fc4861e0738
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65888105"
---
# <a name="update-app-manifest-for-sso-and-preview-app"></a>Aktualisieren des App-Manifests für SSO und Vorschau-App

Stellen Sie vor dem Aktualisieren des Teams-App-Manifests sicher, dass Sie Code zum Aktivieren von SSO in Ihrer Registerkarten-App konfiguriert haben.

> [!div class="nextstepaction"]
> [Konfigurieren von Code](tab-sso-code.md)

Sie haben Ihre Registerkarten-App in Azure AD registriert und eine App-ID abgerufen. Sie haben ihren Code auch so konfiguriert, dass er das Zugriffstoken aufruft `getAuthToken()` und verarbeitet. Jetzt müssen Sie das Teams-App-Manifest aktualisieren, um SSO für Ihre Registerkarten-App zu aktivieren. Das Teams-App-Manifest beschreibt, wie eine App in Teams integriert wird.

## <a name="webapplicationinfo-property"></a>webApplicationInfo-Eigenschaft

Konfigurieren Sie die `webApplicationInfo` Eigenschaft in der Manifestdatei der Teams-App. Diese Eigenschaft ermöglicht SSO für Ihre App, damit App-Benutzer nahtlos auf Ihre Registerkarten-App zugreifen können.

&nbsp;&nbsp;:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-manifest.png" alt-text="Konfiguration des Teams-App-Manifests" border="false":::

`webApplicationInfo` verfügt über zwei Elemente und `id` `resource`.

| Element | Beschreibung |
| --- | --- |
| id | Geben Sie die App-ID (GUID) ein, die Sie in Azure AD erstellt haben. |
| resource | Geben Sie den Unterdomänen-URI Ihrer App und den Anwendungs-ID-URI ein, den Sie beim Erstellen des Bereichs in Azure AD erstellt haben. Sie können es aus dem **Abschnitt "Azure AD** > **Expose an API** " kopieren. |

> [!NOTE]
> Verwenden Sie die Manifestversion 1.5 oder höher, um die `webApplicationInfo` Eigenschaft zu implementieren.

Der Anwendungs-ID-URI, den Sie in Azure AD registriert haben, wird mit dem Umfang der API konfiguriert, die Sie verfügbar gemacht haben. Konfigurieren Sie den Unterdomänen-URI `resource` Ihrer App, um sicherzustellen, dass die Authentifizierungsanforderung, die verwendet `getAuthToken()` wird, von der Domäne stammt, die im Teams-App-Manifest angegeben ist.

Weitere Informationen finden Sie [unter webApplicationInfo](../../../resources/schema/manifest-schema.md#webapplicationinfo).

## <a name="to-configure-teams-app-manifest"></a>So konfigurieren Sie das Microsoft Teams-App-Manifest

1. Öffnen Sie das Registerkarten-App-Projekt.
2. Öffnen Sie den Manifestordner.

  > [!NOTE]
  >
  > - Der Manifestordner sollte sich im Stammverzeichnis des Projekts befinden. Weitere Informationen finden Sie unter [Erstellen eines Microsoft Teams-App-Pakets](../../../concepts/build-and-test/apps-package.md).
  > - Weitere Informationen zum Erstellen einer manifest.json finden Sie unter [Referenz: Manifestschema für Microsoft Teams](../../../resources/schema/manifest-schema.md).

1. Öffnen der Datei "manifest.json"
1. Fügen Sie den folgenden Codeausschnitt an die Manifestdatei an, um die neue Eigenschaft hinzuzufügen:

    ```json
    "webApplicationInfo": {
    "id": "{Azure AD AppId}",
    "resource": "api://{Subdomain}.example.com/{Azure AD AppId}"
    }
    ```

    Wo
    - {Azure AD AppId} ist die App-ID, die Sie erstellt haben, als Sie Ihre App in Azure AD registriert haben. Es ist die GUID.
    - {{Subdomain}.app ID URI} ist der Anwendungs-ID-URI, den Sie beim Erstellen des Bereichs in Azure AD registriert haben.

4. Aktualisieren Sie die App-ID aus Azure AD in der **ID-Eigenschaft** .
5. Aktualisieren Sie die Unterdomänen-URL in den folgenden Eigenschaften:
   1. `contentUrl`
   2. `configurationUrl`
   3. `validDomains`
6. Speichern Sie die Manifestdatei der Teams-App.

<br>
<details>
<summary>Hier ist ein Beispiel für ein App-Manifest, nachdem es aktualisiert wurde.</summary>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
  "manifestVersion": "1.11",
  "version": "1.0.0",
  "id": "bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c",
  "packageName": "com.contoso.teamsauthsso",
  "developer": {
    "name": "Microsoft",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com/privacy",
    "termsOfUseUrl": "https://www.microsoft.com/termsofuse"
  },
  "name": {
    "short": "Teams Auth SSO",
    "full": "Teams Auth SSO"
  },
  "description": {
    "short": "Teams Auth SSO app",
    "full": "The Teams Auth SSO app"
  },
  "icons": {
    "outline": "outline.png",
    "color": "color.png"
  },
  "accentColor": "#60A18E",
  "staticTabs": [
    {
      "entityId": "auth",
      "name": "Auth",
      "contentUrl": "https://contoso.com/Home/Index",
      "scopes": [ "personal" ]
    }
  ],
  "configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/Home/Configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team"
      ]
    }
  ],
  "permissions": [ "identity", "messageTeamMembers" ],
  "validDomains": [
    "contoso.com"
  ],
  "webApplicationInfo": {
    "id": "bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c",
    "resource": "api://contoso.com/bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c"
  }
}
```

</details>

> [!NOTE]
> Während des Debuggens können Sie ngrok verwenden, um Ihre App in Azure AD zu testen. In diesem Fall müssen Sie die Unterdomäne in `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` durch die ngrok-URL ersetzen. Sie müssen die URL aktualisieren, wenn sich Ihre ngrok-Unterdomäne ändert, z. B. api://23c3-103-50-148-128.ngrok.io/bccfbe67-e08b-4ec1-a7fd-e0aaf41a097c.

## <a name="sideload-and-preview-in-teams"></a>Querladen und Vorschau in Teams

Sie haben die Registerkarten-App so konfiguriert, dass SSO in Azure AD, im App-Code und in der Teams-Manifestdatei aktiviert wird. Sie können jetzt Ihre Registerkarten-App in Teams querladen und in der Teams-Umgebung in der Vorschau anzeigen.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sso-flow.png" alt-text="SSO-App" border="false":::

So zeigen Sie eine Vorschau Ihrer Registerkarten-App in Teams an:

1. Erstellen Sie ein App-Paket.

   Das App-Paket ist eine ZIP-Datei, die die App-Manifestdatei und App-Symbole enthält.

1. Öffnen Sie Teams.

1. Wählen Sie **"Apps** > **verwalten" aus, um** > **eine App hochzuladen**.

    Die Optionen zum Hochladen einer App werden angezeigt.

1. Wählen Sie **"Benutzerdefinierte App hochladen** " aus, um die Registerkarten-App in Teams querzuladen.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/sideload-tab-app.png" alt-text="Querladen der Registerkarten-App in Teams":::

1. Wählen Sie Ihre ZIP-Datei des App-Pakets und dann **"Hinzufügen"** aus.

    Die Registerkarten-App wird quergeladen, und das Dialogfeld wird angezeigt, um Sie über die zusätzlichen Berechtigungen zu informieren, die möglicherweise erforderlich sind.

1. Wählen Sie **Weiter**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/teams-sso-consent.png" alt-text="Dialogfeld &quot;Teams&quot;, in dem über zusätzliche Berechtigungen informiert wird" border="true":::

    Das Azure AD-Zustimmungsdialogfeld wird angezeigt.

1. Wählen Sie **"Annehmen** " aus, um die Zustimmung für Open-ID-Bereiche zu erteilen.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/aad-sso-consent.png" alt-text="Azure AD-Zustimmungsdialogfeld" border="true":::

    Teams öffnet die Registerkarten-App, und Sie können sie verwenden.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/teams-sso-app.png" alt-text="Beispiel für die Teams-Registerkarten-App mit aktiviertem SSO" border="false":::

    Herzlichen Glückwunsch! Sie haben SSO für Ihre Registerkarten-App aktiviert.

## <a name="see-also"></a>Siehe auch

- [Manifestschema für Microsoft Teams](../../../resources/schema/manifest-schema.md)
- [Manifestschemaformat](https://developer.microsoft.com/json-schemas/teams/v1.12/MicrosoftTeams.schema.json)
- [Erstellen eines Microsoft Teams-App-Pakets](../../../concepts/build-and-test/apps-package.md)
