---
title: Registrieren Ihrer Registerkartenapp bei Azure AD
description: Konfigurieren Sie single sign-on (SSO) mit Azure AD, indem Sie den App-ID-URI, den Zugriffstokenbereich und vertrauenswürdige Clients vorab autorisieren.
ms.topic: how-to
ms.localizationpriority: high
keywords: Teams Authentifizierung Registerkarten Microsoft Azure Active Directory (Azure AD) Zugriffstoken SSO Mandantenbereich
ms.openlocfilehash: 4cbe07c37a12ef3f2902c2a2760ed07ed99e4af6
ms.sourcegitcommit: 937ea793889fc1efa9ec6a52374d5098be1117e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2022
ms.locfileid: "67653199"
---
# <a name="register-your-tab-app-in-azure-ad"></a>Registrieren Ihrer Registerkarten-App in Azure AD

Azure AD ermöglicht den Zugriff auf Ihre Registerkartenapp basierend auf der Teams-Identität des App-Benutzers. Sie müssen Ihre Registerkartenapp bei Azure AD registrieren, damit der App-Benutzer, der sich bei Teams angemeldet hat, Zugriff auf Ihre Registerkartenapp erhalten kann.

## <a name="enabling-sso-on-azure-ad"></a>Aktivieren von SSO auf Azure AD

Um Ihre Registerkartenapp in Azure AD zu registrieren und für SSO zu aktivieren, müssen Sie App-Konfigurationen vornehmen, z. B. die App-ID generieren, den API-Bereich definieren und Client-IDs für vertrauenswürdige Anwendungen vorab autorisieren.

:::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-azure-ad.png" alt-text="Konfigurieren von Azure AD, um Zugriffstoken an die Teams-Client-App zu senden":::

Erstellen Sie eine neue App-Registrierung in Azure AD, und machen Sie ihre (Web-) API mithilfe von Bereichen (Berechtigungen) verfügbar. Konfigurieren Sie eine Vertrauensstellung zwischen der verfügbar gemachten API auf Azure AD und Ihrer App. Es ermöglicht dem Teams-Client, ein Zugriffstoken im Namen Ihrer Anwendung und des angemeldeten Benutzers abzurufen. Sie können Client-IDs für die vertrauenswürdigen mobilen, Desktop- und Webanwendungen hinzufügen, die Sie vorab autorisieren möchten.

Möglicherweise müssen Sie auch zusätzliche Details konfigurieren, z. B. die Authentifizierung von App-Benutzern auf der Plattform oder auf dem Gerät, auf das Sie Ihre Registerkartenapp ausrichten möchten.

Es werden Graph API-Berechtigungen auf Benutzerebene unterstützt, d. h. E-Mail, Profil, Offline_Access und OpenId. Wenn Sie Zugriff auf zusätzliche Graph-Bereiche benötigen, z. B. `User.Read` oder `Mail.Read`, finden Sie weitere Informationen unter [Abrufen eines Zugriffstokens mit Graph-Berechtigungen](tab-sso-graph-api.md).

Die Azure AD-Konfiguration aktiviert SSO für Ihre Registerkartenapp in Teams. Sie antwortet mit einem Zugriffstoken zum Überprüfen des App-Benutzers.

> [!NOTE]
> Das Microsoft Teams-Toolkit registriert die Azure AD-Anwendung in einem SSO-Projekt.

### <a name="before-you-register-with-azure-ad"></a>Bevor Sie sich mit Azure AD registrieren

Es ist hilfreich, wenn Sie sich zuerst über die Konfiguration für die Registrierung Ihrer App auf Azure AD informieren. Stellen Sie sicher, dass Sie sich darauf vorbereitet haben, die folgenden Details zu konfigurieren, bevor Sie Ihre App registrieren:

- **Einzel- oder Mehrinstanzenoptionen**: Wird Ihre Anwendung nur im Microsoft 365-Mandanten verwendet, in dem sie registriert ist, oder wird sie von vielen Microsoft 365-Mandanten verwendet? Anwendungen, die für ein Unternehmen geschrieben wurden, sind in der Regel ein mandant. Anwendungen, die von einem unabhängigen Softwareanbieter geschrieben und von vielen Kunden verwendet werden, müssen mehrere Mandanten sein, damit der Mandant jedes Kunden auf die Anwendung zugreifen kann.
- **Anwendungs-ID-URI**: Es handelt sich um einen global eindeutigen URI, der die Web-API identifiziert, die Sie für den Zugriff Ihrer App über Bereiche verfügbar machen. Er wird auch als Bezeichner-URI bezeichnet. Der Anwendungs-ID-URI enthält die App-ID und die tertiäre Domäne, in der Ihre App gehostet wird. Der Domänenname Ihrer Anwendung und der Domänenname, den Sie für Ihre Azure AD-Anwendung registrieren, sollten identisch sein. Derzeit werden mehrere Domänen pro App nicht unterstützt.
- **Bereich**: Dies ist die Berechtigung, die einem autorisierten App-Benutzer oder Ihrer App für den Zugriff auf eine Ressource erteilt werden kann, die von der API verfügbar gemacht wird.

> [!NOTE]
>
> - **LOB-Anwendungen**: Ihre Organisation kann Branchenanwendungen über den Microsoft Store verfügbar machen. Diese Apps sind für Ihre Organisation angepasst. Sie sind intern oder spezifisch innerhalb Ihrer Organisation oder Ihres Geschäfts.
> - **Kundeneigene Apps**: SSO wird auch für kundeneigene Apps innerhalb der Azure AD B2C-Mandanten unterstützt.

So erstellen und konfigurieren Sie Ihre App in Azure AD zum Aktivieren von SSO:

- [Registrieren und Konfigurieren Sie die Azure AD-App.](#create-an-app-registration-in-azure-ad)
- [Konfigurieren Sie den Bereich für das Zugriffstoken.](#configure-scope-for-access-token)
- [Konfigurieren Sie die Version des Zugriffstokens.](#configure-access-token-version)

## <a name="create-an-app-registration-in-azure-ad"></a>Erstellen einer App-Registrierung in Azure AD

Registrieren Sie eine neue App in Azure AD, und konfigurieren Sie die Plattform für den Mandanten und die App. Sie werden eine neue App-ID generieren, die später in Ihrer Teams-App-Manifestdatei aktualisiert wird.

### <a name="to-register-a-new-app-in-azure-ad"></a>So registrieren Sie eine neue App in Azure AD

1. Öffnen Sie das [Azure-Portal](https://ms.portal.azure.com/) in Ihrem Webbrowser.
   Die Seite „Microsoft Azure AD-Portal“ wird geöffnet.

2. Wählen Sie das Symbol **App-Registrierungen** aus.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal.png" alt-text="Seite „Azure AD-Portal“.":::

   Die Seite **App-Registrierungen** wird angezeigt.

3. Wählen Sie das Symbol **+ Neue Registrierung** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-registrations.png" alt-text="Seite „Neue Registrierung“ im Azure AD Portal.":::

    Die Seite **Anwendung registrieren** wird angezeigt.

4. Geben Sie den Namen Ihrer App ein, die dem App-Benutzer angezeigt werden soll. Sie können diesen Namen zu einem späteren Zeitpunkt ändern, wenn Sie möchten.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/register-app.png" alt-text="Seite „App-Registrierung“ im Azure AD Portal.":::

5. Wählen Sie den Typ des Benutzerkontos aus, das auf Ihre App zugreifen kann. Sie können zwischen Einzel- oder Mehrmandanten-Optionen oder einem privatem Microsoft-Konto auswählen.

    <details>
    <summary><b>Options für unterstützte Kontotypen</b></summary>

    | Option | Wählen Sie dies aus, um... |
    | --- | --- |
    | Nur Konten in diesem Organisationsverzeichnis (Nur Microsoft – Einzelmandant) | Erstellen Sie eine Anwendung, die nur von Benutzern (oder Gästen) in Ihrem Mandanten verwendet werden kann. <br> Diese App wird häufig als Branchenanwendung (Line Of Business, LOB) bezeichnet und ist eine Einzelmandantenanwendung auf der Microsoft Identity-Plattform. |
    | Konten in einem beliebigen Organisationsverzeichnis (beliebiges Azure AD-Verzeichnis – mehrmandantenfähig) | Ermöglichen Sie Benutzern in einem beliebigen Azure AD-Mandanten die Verwendung Ihrer Anwendung. Diese Option ist geeignet, wenn Sie z. B. eine SaaS-Anwendung erstellen und sie mehreren Organisationen zur Verfügung stellen möchten. <br> Dieser App-Typ wird in der Microsoft Identity-Plattform als mehrmandantenfähige Anwendung bezeichnet.|
    | Konten in allen Organisationsverzeichnissen (beliebiges Azure AD-Verzeichnis – mehrmandantenfähig) und persönliche Microsoft-Konten | Sprechen Sie die breiteste Kundengruppe an. <br> Wenn Sie diese Option auswählen, registrieren Sie eine mehrmandantenfähige Anwendung, die App-Benutzer unterstützen kann, die auch über persönliche Microsoft-Konten verfügen. |
    | Nur persönliche Microsoft-Konten | Erstellen Sie eine Anwendung nur für Benutzer, die über persönliche Microsoft-Konten verfügen. |

    </details>

    > [!NOTE]
    > Sie müssen keine **Umleitungs-URI** eingeben, um SSO für eine Registerkartenapp zu aktivieren.

7. Wählen Sie **Registrieren** aus.
    Im Browser wird eine Nachricht angezeigt, die besagt, dass die App erstellt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-created-msg.png" alt-text="Registrieren Sie die App im Azure AD-Portal.":::

    Die Seite mit der App-ID und anderen Konfigurationen wird angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/tab-app-created.png" alt-text="Die App-Registrierung ist erfolgreich.":::

8. Notieren und speichern Sie die App-ID von **Anwendungs-ID (Client)**. Sie benötigen diesen später zum Aktualisieren des Teams-App-Manifests.

    Ihre App ist in Azure AD registriert. Sie sollten nun über eine App-ID für Ihre Registerkartenapp verfügen.

## <a name="configure-scope-for-access-token"></a>Konfigurieren des Bereichs für das Zugriffstoken

Nachdem Sie eine neue App-Registrierung erstellt haben, konfigurieren Sie Bereichsoptionen (Berechtigungen) zum Senden von Zugriffstoken an den Teams-Client und zum Autorisieren vertrauenswürdiger Clientanwendungen, um SSO zu aktivieren.

Um den Bereich zu konfigurieren und vertrauenswürdige Clientanwendungen zu autorisieren, benötigen Sie Folgendes:

- [Um eine API verfügbar zu machen](#to-expose-an-api): Konfigurieren Sie Bereichsoptionen (Berechtigungen) für Ihre App. Sie machen eine Web-API verfügbar und konfigurieren den Anwendungs-ID-URI.
- [Um den API-Bereich zu konfigurieren](#to-configure-api-scope): Definieren Sie den Bereich für die API und die Benutzer, die einem Bereich zustimmen können. Sie können festlegen, dass nur Admins die Zustimmung für höher privilegierte Berechtigungen erteilen.
- [Um autorisierte Clientanwendung zu konfigurieren](#to-configure-authorized-client-application): Erstellen Sie autorisierte Client-IDs für Anwendungen, die Sie vorab autorisieren möchten. Dadurch kann der App-Benutzer auf die von Ihnen konfigurierten App-Bereiche (Berechtigungen) zugreifen, ohne dass eine weitere Zustimmung erforderlich ist. Autorisieren Sie nur diejenigen Clientanwendungen, denen Sie vertrauen, da Ihre App-Benutzer nicht die Möglichkeit haben, die Zustimmung abzulehnen.

### <a name="to-expose-an-api"></a>Verfügbar machen einer API

1. Wählen Sie im linken Bereich **Verwalten** > **Eine API verfügbar machen** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-api-menu.png" alt-text="Menüoption „API verfügbar machen“.":::

    Die Seite **API verfügbar machen** wird angezeigt.

1. Wählen Sie **Festlegen** aus, um den Anwendungs-ID-URI in Form von `api://{AppID}` zu generieren.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/expose-an-api.png" alt-text="App-ID-URI festlegen":::

    Der Abschnitt zum Festlegen des Anwendungs-ID-URI wird angezeigt.

1. Geben Sie den Anwendungs-ID-URI in dem hier erläuterten Format ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/set-app-id-uri.png" alt-text="Anwendungs-ID-URI":::

    - Der **Anwendungs-ID-URI** wird mit der App-ID (GUID) im Format `api://{AppID}` vorausgefüllt.
    - Das Format des Anwendungs-ID-URI sollte wie folgt lauten: `api://fully-qualified-domain-name.com/{AppID}`.
    - Fügen Sie die `fully-qualified-domain-name.com` zwischen `api://` und `{AppID}` (d. h. der GUID) ein. Beispiel: api://example.com/{AppID}.

    Dabei gilt Folgendes:
    - `fully-qualified-domain-name.com` ist der lesbare Domänenname, über den Ihre Registerkartenapp bereitgestellt wird. Der Domänenname Ihrer Anwendung und der Domänenname, den Sie für Ihre Azure AD-Anwendung registrieren, sollten identisch sein.

      Wenn Sie einen Tunneldienst wie ngrok verwenden, müssen Sie diesen Wert aktualisieren, wenn sich Ihre tertiäre ngrok-Domäne ändert.
    - `AppID` ist die App-ID (GUID), die generiert wurde, als Sie Ihre App registriert haben. Sie können sie im Abschnitt **Übersicht** anzeigen.

    > [!IMPORTANT]
    >
    > - **Anwendungs-ID-URI für eine App mit mehreren Funktionen**: Wenn Sie eine App mit einem Bot, einer Messaging-Erweiterung und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/BotId-{YourClientId}` ein, wobei die BotID Ihre Bot-App-ID ist.
    >
    > - **Format für Domänennamen**: Verwenden Sie Kleinbuchstaben als Domänennamen. Verwenden Sie keine Großbuchstaben.
    >
    >   Um beispielsweise einen App-Dienst oder eine Web-App mit dem Ressourcennamen „demoapplication“ zu erstellen:
    >
    >   | Wenn der verwendete Basisressourcenname wie folgt lautet | Die URL wird folgende sein... | Format wird unterstützt auf... |
    >   | --- | --- | --- |
    >   | *demoapplication* | **<https://demoapplication.example.net>** | Alle Plattformen.|
    >   | *DemoApplication* | **<https://DemoApplication.example.net>** | Nur Desktop, Web und iOS. Sie wird auf Android nicht unterstützt. |
    >
    >    Verwenden Sie die Kleinbuchstabenoption *demoapplication* als Basisressourcennamen.

1. Wählen Sie **Speichern**.

    Im Browser wird eine Meldung angezeigt, die besagt, dass der Anwendungs-ID-URI aktualisiert wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-msg.png" alt-text="Anwendungs-ID-URI-Meldung":::

    Der Anwendungs-ID-URI wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/app-id-uri-added.png" alt-text="Anwendungs-ID-URI aktualisiert":::

1. Notieren und speichern Sie den Anwendungs-ID-URI. Sie benötigen diesen später zum Aktualisieren des Teams-App-Manifests.

### <a name="to-configure-api-scope"></a>So konfigurieren Sie den API-Bereich

1. Wählen Sie **+ Bereich hinzufügen** im Abschnitt **Bereiche, die von dieser API definiert werden** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/select-scope.png" alt-text="Bereich auswählen":::

    Die Seite **Einen Bereich hinzufügen** wird angezeigt.

1. Geben Sie die Details zum Konfigurieren des Bereichs ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-scope.png" alt-text="Bereichsdetails hinzufügen":::

    1. Geben Sie den Bereichsnamen ein. Dieses Feld ist erforderlich.
    2. Wählen Sie den Benutzer aus, der die Zustimmung für diesen Bereich erteilen kann. Die Standardoption ist **Nur Administratoren**.
    3. Geben Sie den **Anzeigename der Administratoreinwilligung** ein. Dieses Feld ist erforderlich.
    4. Geben Sie die Beschreibung für die Administratoreinwilligung ein. Dieses Feld ist erforderlich.
    5. Geben Sie den **Anzeigename der Benutzereinwilligung** ein.
    6. Geben Sie die Beschreibung für die Benutzereinwilligung ein.
    7. Wählen Sie die Option **Aktiviert** für den Status aus.
    8. Klicken Sie auf **Bereich hinzufügen**.

    Im Browser wird eine Meldung angezeigt, die besagt, dass der Bereich hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added-msg.png" alt-text="Nachricht „Bereich hinzugefügt“":::

    Der von Ihnen definierte neue Bereich wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/scope-added.png" alt-text="Bereich hinzugefügt und angezeigt":::

### <a name="to-configure-authorized-client-application"></a>Konfigurieren einer autorisierten Clientanwendung

1. Navigieren Sie durch die Seite **API verfügbar machen** zum Abschnitt **Autorisierte Clientanwendung**, und wählen Sie **+ Clientanwendung hinzufügen** aus.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/auth-client-apps.png" alt-text="Autorisierte Clientanwendungen":::

    Die Seite **Ein Clientanwendung hinzufügen** wird angezeigt.

1. Geben Sie die entsprechende Microsoft 365-Client-ID für den Teams-Client für die Anwendungen ein, die Sie für die Webanwendung Ihrer App autorisieren möchten.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/add-client-app.png" alt-text="Hinzufügen einer Clientanwendung":::

    > [!NOTE]
    >
    > - Die Microsoft 365-Client-IDs für mobile, Desktop- und Webanwendungen für Teams, Office und Outlook sind die eigentlichen IDs, die Sie hinzufügen sollten.
    > - Für eine Teams-Registerkartenapp benötigen Sie entweder Web oder SPA, da Sie keine mobile oder Desktop-Clientanwendung in Teams haben können.

    1. Wählen Sie eine der folgenden Client-IDs aus:

       | Client-ID verwenden | Zum Autorisieren... |
       | --- | --- |
       | 1fec8e78-bce4-4aaf-ab1b-5451cc387264 | mobile Teams- oder Desktopanwendung |
       | 5e3ce6c0-2b1f-4285-8d4b-75ee78787346 | Teams-Webanwendung |
       | 4765445b-32c6-49b0-83e6-1d93765276ca | Office-Webanwendung |
       | 0ec893e0-5785-4de6-99da-4ed124e5296c | Office-Desktopanwendung |
       | d3590ed6-52b3-4102-aeff-aad2292ab01c | Outlook-Desktop, mobile Anwendung |
       | bc59ab01-8403-45c6-8796-ac3ef710b3e3 | Outlook-Webanwendung |

    1. Wählen Sie den Anwendungs-ID-URI aus, den Sie für Ihre App in **Autorisierte Bereiche** erstellt haben, um den Bereich der Web-API hinzuzufügen, die Sie verfügbar gemacht haben.

    1. Wählen Sie **Anwendung hinzufügen** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass die autorisierte Client-App hinzugefügt wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-app-auth-msg.png" alt-text="Nachricht „Clientanwendung hinzugefügt“":::

    Die Client-ID wird auf der Seite angezeigt.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/client-app-added.png" alt-text="Client-App hinzugefügt und angezeigt":::

> [!NOTE]
> Sie können mehr als eine Clientanwendung autorisieren. Wiederholen Sie die Schritte dieses Verfahrens zum Konfigurieren einer anderen autorisierten Clientanwendung.

## <a name="configure-access-token-version"></a>Konfigurieren der Zugriffstokenversion

Sie müssen die Zugriffstokenversion definieren, die für Ihre App akzeptabel ist. Diese Konfiguration erfolgt im Azure AD-Anwendungsmanifest.

### <a name="to-define-the-access-token-version"></a>Definieren der Zugriffstokenversion

1. Wählen Sie im linken Bereich **Verwalten** > **Manifest** aus.

   :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-portal-manifest.png" alt-text="Azure AD-Portal – Manifest":::

    Das Azure AD-Anwendungsmanifest wird angezeigt.

1. Geben Sie **2** als Wert für die Eigenschaft `accessTokenAcceptedVersion` ein.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/azure-manifest-value.png" alt-text="Wert für akzeptierte Zugriffstokenversion":::

1. Wählen Sie **Speichern** aus.

    Im Browser wird eine Meldung angezeigt, die besagt, dass das Manifest erfolgreich aktualisiert wurde.

    :::image type="content" source="../../../assets/images/authentication/teams-sso-tabs/update-aad-manifest-msg.png" alt-text="Nachricht „Manifest aktualisiert“":::

Herzlichen Glückwunsch! Sie haben die App-Konfiguration in Azure AD abgeschlossen, die erforderlich ist, um SSO für Ihre Registerkartenapp zu aktivieren.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurationscode zum Aktivieren von SSO](tab-sso-code.md)

## <a name="see-also"></a>Siehe auch

- [Mandanten im Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps)
- [Erweitern der Registerkartenapp mit Microsoft Graph-Berechtigungen und -Bereich](tab-sso-graph-api.md)
- [Schnellstart – Registrieren einer Anwendung bei der Microsoft Identity-Plattform](/azure/active-directory/develop/quickstart-register-app)
- [Schnellstart: Konfigurieren einer Anwendung, um eine Web-API verfügbar zu machen](/azure/active-directory/develop/quickstart-configure-app-expose-web-apis)
- [OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow)
