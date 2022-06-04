---
title: Registrieren Ihrer Registerkarten-App bei Azure AD
description: Beschreibt das Registrieren Ihrer Registerkarten-App bei Azure AD
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams-Authentifizierungsregisterkarten Zugriffstoken-SSO-Mandantenbereich von Microsoft Azure Active Directory (Azure AD)
ms.openlocfilehash: e508e80f4e2c881e848f628a12392e6ced5e6f4b
ms.sourcegitcommit: e16b51a49756e0fe4eaf239898e28d3021f552da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2022
ms.locfileid: "65888046"
---
# <a name="register-your-app-in-azure-ad"></a>Registrieren Ihrer App in Azure AD

Azure AD bietet Zugriff auf Ihre Registerkarten-App basierend auf der Teams-Identität des App-Benutzers. Sie müssen Ihre Registerkarten-App bei Azure AD registrieren, damit der App-Benutzer, der sich bei Teams angemeldet hat, Zugriff auf Ihre Registerkarten-App erhalten kann.

## <a name="enabling-sso-on-azure-ad"></a>Aktivieren von SSO in Azure AD

Um Ihre Registerkarten-App in Azure AD zu registrieren und für SSO zu aktivieren, müssen Sie App-Konfigurationen erstellen, z. B. App-ID generieren, API-Bereich definieren und Client-IDs für vertrauenswürdige Anwendungen vorab autorisieren.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-azure-ad.png" alt-text="Konfigurieren von Azure AD zum Senden des Zugriffstokens an die Teams-Client-App" border="false":::

Erstellen Sie eine neue App-Registrierung in Azure AD, und machen Sie ihre (Web-)API mithilfe von Bereichen (Berechtigungen) verfügbar. Konfigurieren Sie eine Vertrauensstellung zwischen der verfügbar gemachten API in Azure AD und Ihrer App. Auf diese Weise kann der Teams-Client ein Zugriffstoken im Namen Ihrer Anwendung und des angemeldeten Benutzers abrufen. Sie können Client-IDs für die vertrauenswürdigen mobilen, Desktop- und Webanwendungen hinzufügen, die Sie vorab autorisieren möchten.

Möglicherweise müssen Sie auch zusätzliche Details konfigurieren, z. B. die Authentifizierung von App-Benutzern auf der Plattform oder auf dem Gerät, auf das Sie Ihre Registerkarten-App ausrichten möchten.

Graph-API-Berechtigungen auf Benutzerebene werden unterstützt, d. h. E-Mail, Profil, offline_access und OpenId. Wenn Sie Zugriff auf zusätzliche Graph-Bereiche benötigen, z `User.Read` . B. oder `Mail.Read`, lesen [Sie "Abrufen eines Zugriffstokens mit Graph-Berechtigungen](tab-sso-graph-api.md)".

Die Azure AD-Konfiguration ermöglicht SSO für Ihre Registerkarten-App in Teams. Sie antwortet mit einem Zugriffstoken zum Überprüfen des App-Benutzers.

> [!NOTE]
> Das Microsoft Teams-Toolkit registriert die Azure AD-Anwendung in einem SSO-Projekt.

### <a name="before-you-register-with-azure-ad"></a>Vor der Registrierung bei Azure AD

Es ist hilfreich, wenn Sie sich vorab über die Konfiguration für die Registrierung Ihrer App in Azure AD informieren. Stellen Sie sicher, dass Sie die folgenden Details vor der Registrierung Ihrer App konfiguriert haben:

- **Optionen für einen oder mehrere Mandanten**: Wird Ihre Anwendung nur im Microsoft 365-Mandanten verwendet, in dem sie registriert ist, oder wird sie von vielen Microsoft 365-Mandanten verwendet? Anwendungen, die für ein Unternehmen geschrieben wurden, sind in der Regel ein mandant. Anwendungen, die von einem unabhängigen Softwareanbieter geschrieben und von vielen Kunden verwendet werden, müssen mehrere Mandanten sein, damit der Mandant jedes Kunden auf die Anwendung zugreifen kann.
- **Anwendungs-ID-URI**: Es ist ein global eindeutiger URI, der die Web-API identifiziert, die Sie für den Zugriff Ihrer App über Bereiche verfügbar machen. Er wird auch als Bezeichner-URI bezeichnet. Der Anwendungs-ID-URI enthält die App-ID und die Unterdomäne, in der Ihre App gehostet wird. Der Domänenname Ihrer Anwendung und der Domänenname, den Sie für Ihre Azure AD-Anwendung registrieren, sollten identisch sein. Derzeit werden mehrere Domänen pro App nicht unterstützt.
- **Bereich**: Es ist die Berechtigung, die einem autorisierten App-Benutzer oder Ihrer App für den Zugriff auf eine ressource gewährt werden kann, die von der API verfügbar gemacht wird.

> [!NOTE]
>
> - **BRANCHENANWENDUNGEN**: Ihre Organisation kann Branchenanwendungen über den Microsoft Store verfügbar machen. Diese Apps sind für Ihre Organisation benutzerdefiniert. Sie sind intern oder spezifisch innerhalb Ihrer Organisation oder Ihres Unternehmens.
> - **Kundeneigene Apps**: SSO wird auch für kundeneigene Apps innerhalb der Azure AD B2C-Mandanten unterstützt.

So erstellen und konfigurieren Sie Ihre App in Azure AD zum Aktivieren von SSO:

- [Registrieren und Konfigurieren der Azure AD-App.](#create-an-app-registration-in-azure-ad)
- [Konfigurieren Des Gültigkeitsbereichs für Zugriffstoken.](#configure-scope-for-access-token)
- [Konfigurieren der Zugriffstokenversion.](#configure-access-token-version)

## <a name="create-an-app-registration-in-azure-ad"></a>Erstellen einer App-Registrierung in Azure AD

Registrieren Sie eine neue App in Azure AD, und konfigurieren Sie den Mandanten und die App-Plattform. Sie generieren eine neue App-ID, die später in Ihrer Teams-App-Manifestdatei aktualisiert wird.

### <a name="to-register-a-new-app-in-azure-ad"></a>So registrieren Sie eine neue App in Azure AD

1. Öffnen Sie das [Azure-Portal](https://ms.portal.azure.com/) in Ihrem Webbrowser.
   Die Seite "Microsoft Azure AD-Portal" wird geöffnet.

2. Wählen Sie das Symbol " **App-Registrierungen** " aus.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal.png" alt-text="Azure AD-Portalseite." border="true":::

   Die Seite **"App-Registrierungen** " wird angezeigt.

3. Wählen Sie **+Symbol "Neue Registrierung** " aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-registrations.png" alt-text="Neue Registrierungsseite im Azure AD-Portal." border="true":::

    Die Seite **Anwendung registrieren** wird angezeigt.

4. Geben Sie den Namen Ihrer App ein, die dem App-Benutzer angezeigt werden soll. Sie können diesen Namen zu einem späteren Zeitpunkt ändern, wenn Sie möchten.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-app.png" alt-text="Seite &quot;App-Registrierung&quot; im Azure AD-Portal." border="true":::

5. Wählen Sie den Typ des Benutzerkontos aus, das auf Ihre App zugreifen kann. Sie können zwischen einzel- oder mehrinstanzenfähigen Optionen oder einem privaten Microsoft-Konto wählen.

    <details>
    <summary><b>Optionen für unterstützte Kontotypen</b></summary>

    | Option | Wählen Sie diese Option aus, um... |
    | --- | --- |
    | Nur Konten in diesem Organisationsverzeichnis (nur Microsoft – einzelner Mandant) | Erstellen Sie eine Anwendung, die nur von Benutzern (oder Gästen) in Ihrem Mandanten verwendet werden kann. <br> Diese App wird häufig als Branchenanwendung bezeichnet und ist eine Einzelmandantenanwendung auf der Microsoft Identity Platform. |
    | Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD-Verzeichnis – Mehrere Mandanten) | Ermöglichen Sie Benutzern in jedem Azure AD-Mandanten die Verwendung Ihrer Anwendung. Diese Option ist geeignet, wenn Sie z. B. eine SaaS-Anwendung erstellen und sie mehreren Organisationen zur Verfügung stellen möchten. <br> Dieser App-Typ wird in der Microsoft Identity Platform als mehrinstanzenfähige Anwendung bezeichnet.|
    | Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD-Verzeichnis – mehrere Mandanten) und persönliche Microsoft-Konten | Richten Sie sich an die breiteste Gruppe von Kunden. <br> Wenn Sie diese Option auswählen, registrieren Sie eine mehrinstanzenfähige Anwendung, die Auch App-Benutzer unterstützen kann, die über persönliche Microsoft-Konten verfügen. |
    | Nur persönliche Microsoft-Konten | Erstellen Sie eine Anwendung nur für Benutzer, die über persönliche Microsoft-Konten verfügen. |

    </details>

    > [!NOTE]
    > Sie müssen keinen **Umleitungs-URI** eingeben, um SSO für eine Registerkarten-App zu aktivieren.

7. Wählen Sie **Registrieren** aus.
    Im Browser wird eine Meldung angezeigt, die besagt, dass die App erstellt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-created-msg.png" alt-text="Registrieren Sie die App im Azure AD-Portal." border="true":::

    Die Seite mit App-ID und anderen Konfigurationen wird angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/tab-app-created.png" alt-text="Die App-Registrierung ist erfolgreich." border="true":::

8. Notieren und speichern Sie die App-ID aus der **Anwendungs-ID (Client-ID**). Sie benötigen es später zum Aktualisieren des Teams-App-Manifests.

    Ihre App ist in Azure AD registriert. Sie sollten jetzt über die App-ID für Ihre Registerkarten-App verfügen.

## <a name="configure-scope-for-access-token"></a>Konfigurieren des Bereichs für Zugriffstoken

Nachdem Sie eine neue App-Registrierung erstellt haben, konfigurieren Sie Bereichsoptionen (Berechtigung) für das Senden von Zugriffstoken an den Teams-Client und autorisieren vertrauenswürdige Clientanwendungen, um SSO zu aktivieren.

Um den Bereich zu konfigurieren und vertrauenswürdige Clientanwendungen zu autorisieren, benötigen Sie Folgendes:

- [So machen Sie eine API verfügbar](#to-expose-an-api): Konfigurieren von Bereichsoptionen (Berechtigungsoptionen) für Ihre App. Sie machen eine Web-API verfügbar und konfigurieren den Anwendungs-ID-URI.
- [So konfigurieren Sie den API-Bereich](#to-configure-api-scope): Definieren des Bereichs für die API und der Benutzer, die für einen Bereich zustimmen können. Sie können nur Administratoren die Zustimmung für Berechtigungen mit höheren Rechten erteilen lassen.
- [So konfigurieren Sie eine autorisierte Clientanwendung](#to-configure-authorized-client-application): Erstellen Sie autorisierte Client-IDs für Anwendungen, die Sie vorab autorisieren möchten. Dadurch kann der App-Benutzer auf die von Ihnen konfigurierten App-Bereiche (Berechtigungen) zugreifen, ohne dass eine weitere Zustimmung erforderlich ist. Autorisieren Sie nur die Clientanwendungen, denen Sie vertrauen, da Ihre App-Benutzer nicht die Möglichkeit haben, die Zustimmung abzulehnen.

### <a name="to-expose-an-api"></a>So machen Sie eine API verfügbar

1. Wählen Sie im linken Bereich "**API** **verwalten** > " aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-api-menu.png" alt-text="Verfügbarmachen einer API-Menüoption." border="true":::

    Die Seite **"API verfügbar machen** " wird angezeigt.

1. Wählen Sie **"Festlegen"** aus, um den Anwendungs-ID-URI in Form von `api://{AppID}`zu generieren.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-an-api.png" alt-text="App-ID-URI festlegen" border="true":::

    Der Abschnitt zum Festlegen des Anwendungs-ID-URI wird angezeigt.

1. Geben Sie den Anwendungs-ID-URI in dem hier erläuterten Format ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/set-app-id-uri.png" alt-text="Anwendungs-ID-URI" border="true":::

    - Der **Anwendungs-ID-URI** ist im Format mit app-ID (GUID) vorgefüllt `api://{AppID}`.
    - Das URI-Format der Anwendungs-ID sollte folgendes sein: `api://fully-qualified-domain-name.com/{AppID}`.
    - Fügen Sie die `fully-qualified-domain-name.com` Zwischen- `api://` und `{AppID}` (GUID) ein. Beispiel: api://example.com/{AppID}.

    Wo
    - `fully-qualified-domain-name.com` ist der lesbare Domänenname, aus dem Ihre Registerkarten-App bedient wird. Der Domänenname Ihrer Anwendung und der Domänenname, den Sie für Ihre Azure AD-Anwendung registrieren, sollten identisch sein.

      Wenn Sie einen Tunneldienst wie ngrok verwenden, müssen Sie diesen Wert aktualisieren, sobald sich Ihre ngrok-Unterdomäne ändert.
    - `AppID` ist die App-ID (GUID), die bei der Registrierung der App generiert wurde. Sie können es im Abschnitt **"Übersicht** " anzeigen.

    > [!IMPORTANT]
    >
    > - **Anwendungs-ID-URI für Apps mit mehreren Funktionen**: Wenn Sie eine App mit einem Bot, einer Messaging-Erweiterung und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/BotId-{YourClientId}`"BotID" als Bot-App-ID ein.
    >
    > - **Format für Domänennamen**: Verwenden Sie Kleinbuchstaben für Domänennamen. Verwenden Sie keine Großbuchstaben.
    >
    >   So erstellen Sie beispielsweise einen App-Dienst oder eine Web-App mit dem Ressourcennamen "demoapplication":
    >
    >   | Wenn der verwendete Basisressourcenname | DIE URL wird... | Format wird unterstützt am... |
    >   | --- | --- | --- |
    >   | *Demoapplication* | **<https://demoapplication.example.net>** | Alle Plattformen.|
    >   | *Demoapplication* | **<https://DemoApplication.example.net>** | Nur Desktop, Web und iOS. Es wird in Android nicht unterstützt. |
    >
    >    Verwenden Sie die *Demoanwendung* der Kleinbuchstabenoption als Basisressourcennamen.

1. Wählen Sie **Speichern** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass der Anwendungs-ID-URI aktualisiert wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-msg.png" alt-text="Anwendungs-ID-URI-Nachricht" border="true":::

    Der Anwendungs-ID-URI wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-added.png" alt-text="Anwendungs-ID-URI aktualisiert" border="true":::

1. Notieren und speichern Sie den Anwendungs-ID-URI. Sie benötigen es später zum Aktualisieren des Teams-App-Manifests.

### <a name="to-configure-api-scope"></a>So konfigurieren Sie den API-Bereich

1. Wählen Sie in den **in diesem API-Abschnitt definierten Bereichen** den **Bereich aus, und fügen Sie einen Bereich hinzu**.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-scope.png" alt-text="Bereich auswählen" border="true":::

    Die Seite **"Bereich hinzufügen** " wird angezeigt.

1. Geben Sie die Details zum Konfigurieren des Bereichs ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-scope.png" alt-text="Hinzufügen von Bereichsdetails" border="true":::

    1. Geben Sie den Bereichsnamen ein. Dieses Feld ist erforderlich.
    2. Wählen Sie den Benutzer aus, der die Zustimmung für diesen Bereich erteilen kann. Die Standardoption ist **nur "Administratoren**".
    3. Geben Sie den **Anzeigenamen der Administratorzustimmung ein**. Dieses Feld ist erforderlich.
    4. Geben Sie die Beschreibung für die Administratorzustimmung ein. Dieses Feld ist erforderlich.
    5. Geben Sie den **Anzeigenamen der Benutzerzustimmung ein**.
    6. Geben Sie die Beschreibung für die Beschreibung der Benutzer-Zustimmung ein.
    7. Wählen Sie die Option **"Aktiviert** " für den Status aus.
    8. Klicken Sie auf **Bereich hinzufügen**.

    Im Browser wird eine Meldung angezeigt, die besagt, dass der Bereich hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added-msg.png" alt-text="Bereich hinzugefügte Nachricht" border="true":::

    Der von Ihnen definierte neue Bereich wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added.png" alt-text="Bereich hinzugefügt und angezeigt" border="true":::

### <a name="to-configure-authorized-client-application"></a>So konfigurieren Sie eine autorisierte Clientanwendung

1. Navigieren Sie durch die Seite **"API verfügbar machen** " zum Abschnitt **"Autorisierte Clientanwendung** ", und wählen Sie **"+Clientanwendung hinzufügen"** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/auth-client-apps.png" alt-text="Autorisierte Clientanwendung" border="true":::

    Die Seite **"Clientanwendung hinzufügen** " wird angezeigt.

1. Geben Sie die entsprechende Client-ID für den Teams-Client für die Anwendungen ein, die Sie für die Webanwendung Ihrer App autorisieren möchten.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-app.png" alt-text="Hinzufügen einer Clientanwendung" border="true":::

    > [!NOTE]
    >
    > - Die Client-IDs für mobile Teams-, Desktop- und Webanwendungen sind die eigentlichen IDs, die Sie hinzufügen sollten.
    > - Für eine Teams-Registerkarten-App benötigen Sie entweder Web oder SPA, da Sie keine Mobile- oder Desktopclientanwendung in Teams haben können.

    1. Wählen Sie eine der folgenden Client-IDs aus:

       | Client-ID verwenden | Zur Autorisierung... |
       | --- | --- |
       | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 | Mobile Teams- oder Desktopanwendung |
       | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 | Teams-Webanwendung |

    1. Wählen Sie den Anwendungs-ID-URI aus, den Sie für Ihre App in **autorisierten Bereichen** erstellt haben, um den Bereich der von Ihnen verfügbar gemachten Web-API hinzuzufügen.

    1. Wählen Sie **Anwendung hinzufügen** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass die autorisierte Client-App hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Nachricht mit hinzugefügter Clientanwendung" border="true":::

    Die Client-ID wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-app-added.png" alt-text="Hinzugefügte und angezeigte Client-App" border="true":::

> [!NOTE]
> Sie können mehrere Clientanwendungen autorisieren. Wiederholen Sie die Schritte dieses Verfahrens zum Konfigurieren einer anderen autorisierten Clientanwendung.

## <a name="configure-access-token-version"></a>Konfigurieren der Zugriffstokenversion

Sie müssen die Zugriffstokenversion definieren, die für Ihre App akzeptabel ist. Diese Konfiguration erfolgt im Azure AD-Anwendungsmanifest.

### <a name="to-define-the-access-token-version"></a>So definieren Sie die Zugriffstokenversion

1. Wählen Sie im linken Bereich "**Manifest** **verwalten** > " aus.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-manifest.png" alt-text="Azure AD-Portalmanifest" border="true":::

    Das Azure AD-Anwendungsmanifest wird angezeigt.

1. Geben Sie **2** als Wert für die `accessTokenAcceptedVersion` Eigenschaft ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-manifest-value.png" alt-text="Wert für die Version des akzeptierten Zugriffstokens" border="true":::

1. Wählen Sie **Speichern** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass das Manifest erfolgreich aktualisiert wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-aad-manifest-msg.png" alt-text="Manifest aktualisierte Nachricht":::

Herzlichen Glückwunsch! Sie haben die App-Konfiguration in Azure AD abgeschlossen, die erforderlich ist, um SSO für Ihre Registerkarten-App zu aktivieren.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurieren von Code zum Aktivieren von SSO](tab-sso-code.md)

## <a name="see-also"></a>Siehe auch

- [Mandant in Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps)
- [Erweitern der Registerkarten-App mit Microsoft Graph-Berechtigungen und -Bereich](tab-sso-graph-api.md)
- [Schnellstart – Registrieren einer Anwendung bei der Microsoft Identity Platform](/azure/active-directory/develop/quickstart-register-app)
- [Schnellstart: Konfigurieren einer Anwendung zum Verfügbarmachen einer Web-API](/azure/active-directory/develop/quickstart-configure-app-expose-web-apis)
- [OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow)
