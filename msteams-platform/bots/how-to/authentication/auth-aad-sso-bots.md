---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie sie ein Benutzertoken erhalten. Derzeit kann ein Botentwickler eine Anmeldekarte oder den Azure -Bot-Dienst mit der Unterstützung der OAuth-Karte verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots
ms.topic: conceptual
ms.openlocfilehash: 8669e00fcfcfb69844c4d63c9e7aa06b47567705
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014495"
---
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="af644-105">Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Bots</span><span class="sxs-lookup"><span data-stu-id="af644-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="af644-106">Die Authentifizierung mit einmaligem Anmelden in Azure Active Directory (AAD) minimiert die Anzahl der Benutzer, die ihre Anmeldeinformationen eingeben müssen, indem das Authentifizierungstoken automatisch aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="af644-106">Single sign-on authentication in Azure Active Directory (AAD) minimizes the number of times users need to enter their sign in credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="af644-107">Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie auf einem anderen Gerät keine weitere Zustimmung erteilen und können sich automatisch anmelden.</span><span class="sxs-lookup"><span data-stu-id="af644-107">If users agree to use your app, they need not provide consent again on another device and can sign in automatically.</span></span> <span data-ttu-id="af644-108">Der Ablauf ähnelt dem der Unterstützung von [Microsoft Teams-Registerkarten-SSO,](../../../tabs/how-to/authentication/auth-aad-sso.md)der Unterschied besteht jedoch im Protokoll dafür, wie ein Bot Token [anfordert](#request-a-bot-token) und Antworten [empfängt.](#receive-the-bot-token)</span><span class="sxs-lookup"><span data-stu-id="af644-108">The flow is similar to that of [Microsoft Teams tab SSO support](../../../tabs/how-to/authentication/auth-aad-sso.md), however, the difference is in the protocol for how a bot [requests tokens](#request-a-bot-token) and [receives responses](#receive-the-bot-token).</span></span>

>[!NOTE]
> <span data-ttu-id="af644-109">OAuth 2.0 ist ein offener Standard für die Authentifizierung und Autorisierung, der von AAD und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af644-109">OAuth 2.0 is an open standard for authentication and authorization used by AAD and many other identity providers.</span></span> <span data-ttu-id="af644-110">Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.</span><span class="sxs-lookup"><span data-stu-id="af644-110">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="af644-111">Bot-SSO zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="af644-111">Bot SSO at runtime</span></span>

![Bot-SSO zur Laufzeit (Diagramm)](../../../assets/images/bots/bots-sso-diagram.png)

<span data-ttu-id="af644-113">Führen Sie die folgenden Schritte aus, um Authentifizierungs- und Botanwendungstoken abzurufen:</span><span class="sxs-lookup"><span data-stu-id="af644-113">Complete the following steps to get authentication and bot application tokens:</span></span>

1. <span data-ttu-id="af644-114">Der Bot sendet eine Nachricht mit einer OAuthCard, die die Eigenschaft `tokenExchangeResource` enthält.</span><span class="sxs-lookup"><span data-stu-id="af644-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="af644-115">Er weist Teams an, ein Authentifizierungstoken für die Botanwendung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="af644-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="af644-116">Der Benutzer empfängt Nachrichten an allen aktiven Benutzerendpunkten.</span><span class="sxs-lookup"><span data-stu-id="af644-116">The user receives messages at all the active user endpoints.</span></span>

    > [!NOTE]
    >* <span data-ttu-id="af644-117">Ein Benutzer kann mehrere aktive Endpunkte gleichzeitig haben.</span><span class="sxs-lookup"><span data-stu-id="af644-117">A user can have more than one active endpoint at a time.</span></span>
    >* <span data-ttu-id="af644-118">Das Bottoken wird von jedem aktiven Benutzerendpunkt empfangen.</span><span class="sxs-lookup"><span data-stu-id="af644-118">The bot token is received from every active user endpoint.</span></span>
    >* <span data-ttu-id="af644-119">Die App muss im persönlichen Bereich für die Unterstützung von SSO installiert werden.</span><span class="sxs-lookup"><span data-stu-id="af644-119">The app must be installed in personal scope for SSO support.</span></span>

2. <span data-ttu-id="af644-120">Wenn der aktuelle Benutzer Ihre Botanwendung zum ersten Mal verwendet, wird eine Anforderungsaufforderung angezeigt, in der der Benutzer aufgefordert wird, eine der folgenden Schritte zu tun:</span><span class="sxs-lookup"><span data-stu-id="af644-120">If the current user is using your bot application for the first time, a request prompt appears requesting the user to do one of the following:</span></span>
    * <span data-ttu-id="af644-121">Geben Sie ihre Zustimmung, falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af644-121">Provide consent, if required.</span></span>
    * <span data-ttu-id="af644-122">Behandeln Sie die Step-Up-Authentifizierung, z. B. die zweistufige Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="af644-122">Handle step-up authentication, such as two-factor authentication.</span></span>

3. <span data-ttu-id="af644-123">Teams fordert das Botanwendungstoken vom AAD-Endpunkt für den aktuellen Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="af644-123">Teams requests the bot application token from the AAD endpoint for the current user.</span></span>

4. <span data-ttu-id="af644-124">AAD sendet das Botanwendungstoken an die Teams-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="af644-124">AAD sends the bot application token to the Teams application.</span></span>

5. <span data-ttu-id="af644-125">Teams sendet das Token als Teil des Wertobjekts, das von der Aufrufaktivität mit dem Namen **"sign-in/tokenExchange" zurückgegeben wird, an den Bot.**</span><span class="sxs-lookup"><span data-stu-id="af644-125">Teams sends the token to the bot as part of the value object returned by the invoke activity with the name **sign-in/tokenExchange**.</span></span>
  
6. <span data-ttu-id="af644-126">Das analysierte Token in der Botanwendung stellt die erforderlichen Informationen zur Verfügung, z. B. die E-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="af644-126">The parsed token in the bot application provides the required information, such as the user's email address.</span></span>
  
## <a name="develop-an-sso-teams-bot"></a><span data-ttu-id="af644-127">Entwickeln eines SSO -Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="af644-127">Develop an SSO Teams bot</span></span>
  
<span data-ttu-id="af644-128">Führen Sie die folgenden Schritte aus, um einen SSO -Teams-Bot zu entwickeln:</span><span class="sxs-lookup"><span data-stu-id="af644-128">Complete the following steps to develop an SSO Teams bot:</span></span>

1. <span data-ttu-id="af644-129">[Registrieren Sie Ihre App über das AAD-Portal.](#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="af644-129">[Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span>
2. <span data-ttu-id="af644-130">[Aktualisieren Sie Ihr Teams-Anwendungsmanifest für Ihren Bot.](#update-your-teams-application-manifest-for-your-bot)</span><span class="sxs-lookup"><span data-stu-id="af644-130">[Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span>
3. <span data-ttu-id="af644-131">[Fügen Sie den Code zum Anfordern und Empfangen eines Bottokens hinzu.](#add-the-code-to-request-and-receive-a-bot-token)</span><span class="sxs-lookup"><span data-stu-id="af644-131">[Add the code to request and receive a bot token](#add-the-code-to-request-and-receive-a-bot-token).</span></span>

### <a name="register-your-app-through-the-aad-portal"></a><span data-ttu-id="af644-132">Registrieren Ihrer App über das AAD-Portal</span><span class="sxs-lookup"><span data-stu-id="af644-132">Register your app through the AAD portal</span></span>

<span data-ttu-id="af644-133">Die Schritte zum Registrieren Ihrer App über das AAD-Portal ähneln dem [Registerkarten-SSO-Fluss.](../../../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="af644-133">The steps to register your app through the AAD portal are similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="af644-134">Führen Sie die folgenden Schritte aus, um Ihre App zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="af644-134">Complete the following steps to register your app:</span></span>

1. <span data-ttu-id="af644-135">Registrieren Sie eine neue Anwendung im [Azure Active Directory – App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)</span><span class="sxs-lookup"><span data-stu-id="af644-135">Register a new application in the [Azure Active Directory – App Registrations](https://go.microsoft.com/fwlink/?linkid=2083908) portal.</span></span>
2. <span data-ttu-id="af644-136">Wählen Sie **"Neue Registrierung" aus.**</span><span class="sxs-lookup"><span data-stu-id="af644-136">Select **New Registration**.</span></span> <span data-ttu-id="af644-137">Die **Seite "Anwendung registrieren"** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af644-137">The **Register an application** page appears.</span></span>
3. <span data-ttu-id="af644-138">Geben Sie **auf der Seite "Anwendung registrieren"** die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="af644-138">In the **Register an application** page, enter the following values:</span></span>
    1. <span data-ttu-id="af644-139">Geben Sie **einen Namen** für Ihre App ein.</span><span class="sxs-lookup"><span data-stu-id="af644-139">Enter a **Name** for your app.</span></span>
    2. <span data-ttu-id="af644-140">Wählen Sie die **unterstützten Kontotypen** aus, wählen Sie den Kontotyp für einen einzelnen Mandanten oder mehrere Mandanten aus.</span><span class="sxs-lookup"><span data-stu-id="af644-140">Choose the **Supported account types**, select single tenant or multitenant account type.</span></span>

        > [!NOTE]
        >
        > <span data-ttu-id="af644-141">Die Benutzer werden nicht um Zustimmung gebeten und erhalten sofort Zugriffstoken, wenn die AAD-App im selben Mandanten registriert ist, in dem sie eine Authentifizierungsanforderung in Teams stellen.</span><span class="sxs-lookup"><span data-stu-id="af644-141">The users are not asked for consent and are granted access tokens right away, if the AAD app is registered in the same tenant where they are making an authentication request in Teams.</span></span> <span data-ttu-id="af644-142">Die Benutzer müssen jedoch den Berechtigungen zustimmen, wenn die AAD-App in einem anderen Mandanten registriert ist.</span><span class="sxs-lookup"><span data-stu-id="af644-142">However, the users must provide consent to the permissions, if the AAD app is registered in a different tenant.</span></span>

    3. <span data-ttu-id="af644-143">Wählen Sie **Registrieren** aus.</span><span class="sxs-lookup"><span data-stu-id="af644-143">Choose **Register**.</span></span>
4. <span data-ttu-id="af644-144">Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).**</span><span class="sxs-lookup"><span data-stu-id="af644-144">On the overview page, copy and save the **Application (client) ID**.</span></span> <span data-ttu-id="af644-145">Sie benötigen sie später beim Aktualisieren Ihres Teams-Anwendungsmanifests.</span><span class="sxs-lookup"><span data-stu-id="af644-145">You need it later when updating your Teams application manifest.</span></span>
5. <span data-ttu-id="af644-146">Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus.</span><span class="sxs-lookup"><span data-stu-id="af644-146">Under **Manage**, select **Expose an API**.</span></span> 

   > [!IMPORTANT]
    > * <span data-ttu-id="af644-147">Wenn Sie einen eigenständigen Bot erstellen, geben Sie den Anwendungs-ID-URI als `api://botid-{YourBotId}` ein.</span><span class="sxs-lookup"><span data-stu-id="af644-147">If you are building a standalone bot, enter the Application ID URI as `api://botid-{YourBotId}`.</span></span> <span data-ttu-id="af644-148">Hier **ist YourBotId** Ihre AAD-Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="af644-148">Here **YourBotId** is your AAD application ID.</span></span>
    > * <span data-ttu-id="af644-149">Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` ein.</span><span class="sxs-lookup"><span data-stu-id="af644-149">If you are building an app with a bot and a tab, enter the Application ID URI as `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

5. <span data-ttu-id="af644-150">Wählen Sie die Berechtigungen aus, die Ihre Anwendung für den AAD-Endpunkt und optional für Microsoft Graph benötigt.</span><span class="sxs-lookup"><span data-stu-id="af644-150">Select the permissions that your application needs for the AAD endpoint and, optionally, for Microsoft Graph.</span></span>
6. <span data-ttu-id="af644-151">[Erteilen von Berechtigungen](/azure/active-directory/develop/v2-permissions-and-consent) für Desktop-, Web- und mobile Anwendungen von Teams.</span><span class="sxs-lookup"><span data-stu-id="af644-151">[Grant permissions](/azure/active-directory/develop/v2-permissions-and-consent) for Teams desktop, web, and mobile applications.</span></span>
7. <span data-ttu-id="af644-152">Wählen Sie **Bereich hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="af644-152">Select **Add a scope**.</span></span>
8. <span data-ttu-id="af644-153">Fügen Sie in dem Bereich, der geöffnet wird, eine Client-App hinzu, indem Sie `access_as_user` den **Bereichsnamen eingeben.**</span><span class="sxs-lookup"><span data-stu-id="af644-153">In the panel that opens, add a client app by entering `access_as_user` as the **Scope name**.</span></span>

    >[!NOTE]
    > <span data-ttu-id="af644-154">Der bereich "access_as_user" zum Hinzufügen einer Client-App ist für "Administratoren und Benutzer".</span><span class="sxs-lookup"><span data-stu-id="af644-154">The "access_as_user" scope used to add a client app is for "Administrators and users".</span></span>
    >
    > <span data-ttu-id="af644-155">Beachten Sie die folgenden wichtigen Einschränkungen:</span><span class="sxs-lookup"><span data-stu-id="af644-155">You must be aware of the following important restrictions:</span></span>
    >
    > * <span data-ttu-id="af644-156">Es werden nur Microsoft Graph-API-Berechtigungen auf Benutzerebene unterstützt, z. B. E-Mail, Profil, offline_access und OpenId.</span><span class="sxs-lookup"><span data-stu-id="af644-156">Only user-level Microsoft Graph API permissions, such as email, profile, offline_access, and OpenId are supported.</span></span> <span data-ttu-id="af644-157">Wenn Sie Zugriff auf andere Microsoft Graph-Bereiche benötigen, z. B. oder , finden Sie weitere Informationen zur `User.Read` `Mail.Read` [empfohlenen Problemumgehung.](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-microsoft-graph-scopes)</span><span class="sxs-lookup"><span data-stu-id="af644-157">If you need access to other Microsoft Graph scopes, such as `User.Read` or `Mail.Read`, see [recommended workaround](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-microsoft-graph-scopes).</span></span>
    > * <span data-ttu-id="af644-158">Der Domänenname Ihrer Anwendung muss mit dem Domänennamen identisch sein, den Sie für Ihre AAD-Anwendung registriert haben.</span><span class="sxs-lookup"><span data-stu-id="af644-158">Your application's domain name must be same as the domain name that you have registered for your AAD application.</span></span>
    > * <span data-ttu-id="af644-159">Mehrere Domänen pro App werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="af644-159">Multiple domains per app are currently not supported.</span></span>
    > * <span data-ttu-id="af644-160">Anwendungen, die die Domäne verwenden, werden nicht unterstützt, da sie häufig verwendet werden `azurewebsites.net` und ein Sicherheitsrisiko darstellen können.</span><span class="sxs-lookup"><span data-stu-id="af644-160">Applications that use the `azurewebsites.net` domain are not supported because it is common and may be a security risk.</span></span>

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="af644-161">Aktualisieren des Azure-Portals mit der OAuth-Verbindung</span><span class="sxs-lookup"><span data-stu-id="af644-161">Update the Azure portal with the OAuth connection</span></span>

<span data-ttu-id="af644-162">Führen Sie die folgenden Schritte aus, um das Azure-Portal mit der OAuth-Verbindung zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="af644-162">Complete the following steps to update the Azure portal with the OAuth connection:</span></span>

1. <span data-ttu-id="af644-163">Navigieren Sie im Azure Portal zu **App-Registrierungen.**</span><span class="sxs-lookup"><span data-stu-id="af644-163">In the Azure Portal, navigate to **App registrations**.</span></span>

2. <span data-ttu-id="af644-164">Wechseln Sie zu **"API-Berechtigungen".**</span><span class="sxs-lookup"><span data-stu-id="af644-164">Go to **API Permissions**.</span></span> <span data-ttu-id="af644-165">Wählen **Sie "Delegierte Berechtigungen für** Microsoft Graph hinzufügen" aus, und fügen Sie dann die folgenden Berechtigungen aus der Microsoft  >    >  Graph-API hinzu:</span><span class="sxs-lookup"><span data-stu-id="af644-165">Select **Add a permission** > **Microsoft Graph** > **Delegated permissions**, then add the following permissions from Microsoft Graph API:</span></span>
    * <span data-ttu-id="af644-166">User.Read (standardmäßig aktiviert)</span><span class="sxs-lookup"><span data-stu-id="af644-166">User.Read (enabled by default)</span></span>
    * <span data-ttu-id="af644-167">email</span><span class="sxs-lookup"><span data-stu-id="af644-167">email</span></span>
    * <span data-ttu-id="af644-168">offline_access</span><span class="sxs-lookup"><span data-stu-id="af644-168">offline_access</span></span>
    * <span data-ttu-id="af644-169">OpenId</span><span class="sxs-lookup"><span data-stu-id="af644-169">OpenId</span></span>
    * <span data-ttu-id="af644-170">Profil</span><span class="sxs-lookup"><span data-stu-id="af644-170">profile</span></span>

3. <span data-ttu-id="af644-171">Navigieren Sie im Azure Portal zu **"Bot Channels Registration".**</span><span class="sxs-lookup"><span data-stu-id="af644-171">In the Azure Portal, navigate to **Bot Channels Registration**.</span></span>

4. <span data-ttu-id="af644-172">Wählen **Sie im** linken Bereich "Einstellungen" und dann "Einstellung hinzufügen" im Abschnitt  **"OAuth-Verbindungseinstellungen"** aus.</span><span class="sxs-lookup"><span data-stu-id="af644-172">Select **Settings** on the left pane and choose **Add Setting** under the **OAuth Connection Settings** section.</span></span>

    ![Ansicht SSOBotHandle2](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

5. <span data-ttu-id="af644-174">Führen Sie die folgenden Schritte aus, um das Formular für neue **Verbindungseinstellungen** auszufüllen:</span><span class="sxs-lookup"><span data-stu-id="af644-174">Perform the following steps to complete the **New Connection Setting** form:</span></span>

    >[!NOTE]
    > <span data-ttu-id="af644-175">**In der** AAD-Anwendung ist möglicherweise eine implizite Gewährung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af644-175">**Implicit grant** may be required in the AAD application.</span></span>

    1. <span data-ttu-id="af644-176">Geben Sie **auf der Seite "Neue** **Verbindungseinstellung" einen Namen** ein.</span><span class="sxs-lookup"><span data-stu-id="af644-176">Enter a **Name** in the **New Connection Setting** page.</span></span> <span data-ttu-id="af644-177">Dies ist der Name, auf den in den Einstellungen Ihres Botdienstcodes in Schritt *5* von Bot SSO zur [Laufzeit verwiesen wird.](#bot-sso-at-runtime)</span><span class="sxs-lookup"><span data-stu-id="af644-177">This is the name that is referred to inside the settings of your bot service code in *step 5* of [Bot SSO at runtime](#bot-sso-at-runtime).</span></span>
    2. <span data-ttu-id="af644-178">Wählen Sie **in der** Dropdownliste "Dienstanbieter" Azure Active **Directory v2 aus.**</span><span class="sxs-lookup"><span data-stu-id="af644-178">From the **Service Provider** drop-down, select **Azure Active Directory v2**.</span></span>
    3. <span data-ttu-id="af644-179">Geben Sie die Clientanmeldeinformationen ein, z. **B. Client-ID** und **geheimer Client für** die AAD-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="af644-179">Enter the client credentials, such as **Client id** and **Client secret** for the AAD application.</span></span>
    4. <span data-ttu-id="af644-180">Verwenden Sie **für die Token-Exchange-URL** den Bereichswert, der in [Update your Teams application manifest for your bot definiert ist.](#update-your-teams-application-manifest-for-your-bot)</span><span class="sxs-lookup"><span data-stu-id="af644-180">For the **Token Exchange URL**, use the scope value defined in [Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span> <span data-ttu-id="af644-181">Die Token-Exchange-URL gibt dem SDK an, dass diese AAD-Anwendung für SSO konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="af644-181">The Token Exchange URL indicates to the SDK that this AAD application is configured for SSO.</span></span>
    5. <span data-ttu-id="af644-182">Geben Sie **im Feld "Mandanten-ID"** eine *gemeinsame ein.*</span><span class="sxs-lookup"><span data-stu-id="af644-182">In the **Tenant ID** box, enter *common*.</span></span>
    6. <span data-ttu-id="af644-183">Fügen Sie alle **Bereiche hinzu,** die beim Angeben von Berechtigungen für downstream-APIs für Ihre AAD-Anwendung konfiguriert wurden.</span><span class="sxs-lookup"><span data-stu-id="af644-183">Add all the **Scopes** configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="af644-184">Wenn die Client-ID und der geheime Clientgeheimnis angegeben sind, tauscht der Tokenspeicher das Token gegen ein Diagrammtoken mit definierten Berechtigungen aus.</span><span class="sxs-lookup"><span data-stu-id="af644-184">With the Client id and Client secret provided, the token store exchanges the token for a graph token with defined permissions.</span></span>
    7. <span data-ttu-id="af644-185">Wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="af644-185">Select **Save**.</span></span>

    ![Einstellungsansicht für VuSSOBotConnection](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a><span data-ttu-id="af644-187">Aktualisieren Ihres Teams-Anwendungsmanifests für Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="af644-187">Update your Teams application manifest for your bot</span></span>

<span data-ttu-id="af644-188">Wenn die Anwendung einen eigenständigen Bot enthält, verwenden Sie den folgenden Code, um dem Anwendungsmanifest von Teams neue Eigenschaften hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="af644-188">If the application contains a standalone bot, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
<span data-ttu-id="af644-189">Wenn die Anwendung einen Bot und eine Registerkarte enthält, verwenden Sie den folgenden Code, um dem Anwendungsmanifest von Teams neue Eigenschaften hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="af644-189">If the application contains a bot and a tab, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

<span data-ttu-id="af644-190">**webApplicationInfo** ist das übergeordnete Element der folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="af644-190">**webApplicationInfo** is the parent of the following elements:</span></span>

* <span data-ttu-id="af644-191">**id** – Die Client-ID der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="af644-191">**id** - The client ID of the application.</span></span> <span data-ttu-id="af644-192">Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung bei AAD erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="af644-192">This is the application ID that you obtained as part of registering the application with AAD.</span></span>
* <span data-ttu-id="af644-193">**resource** – Die Domäne und Unterdomäne Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="af644-193">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="af644-194">Dies ist der gleiche URI, einschließlich des Protokolls, das Sie beim Erstellen Ihrer App über das `api://` AAD-Portal registriert `scope` [haben.](#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="af644-194">This is the same URI, including the `api://` protocol that you registered when creating your `scope` in [Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span> <span data-ttu-id="af644-195">Sie dürfen den Pfad `access_as_user` nicht in ihre Ressource verwenden.</span><span class="sxs-lookup"><span data-stu-id="af644-195">You must not include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="af644-196">Der Domänenteil dieses URI muss mit der Domäne und den Unterdomänen übereinstimmen, die in den URLs Ihres Anwendungsmanifests von Teams verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="af644-196">The domain part of this URI must match the domain and subdomains used in the URLs of your Teams application manifest.</span></span>

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a><span data-ttu-id="af644-197">Hinzufügen des Codes zum Anfordern und Empfangen eines Bottokens</span><span class="sxs-lookup"><span data-stu-id="af644-197">Add the code to request and receive a bot token</span></span>

#### <a name="request-a-bot-token"></a><span data-ttu-id="af644-198">Anfordern eines Bottokens</span><span class="sxs-lookup"><span data-stu-id="af644-198">Request a bot token</span></span>

<span data-ttu-id="af644-199">Die Anforderung zum Anfordern des Tokens ist eine normale POST-Nachrichtenanforderung, die das vorhandene Nachrichtenschema verwendet.</span><span class="sxs-lookup"><span data-stu-id="af644-199">The request to get the token is a normal POST message request using the existing message schema.</span></span> <span data-ttu-id="af644-200">Sie ist in den Anlagen einer OAuthCard enthalten.</span><span class="sxs-lookup"><span data-stu-id="af644-200">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="af644-201">Das Schema für die "OAuthCard"-Klasse ist in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="af644-201">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is similar to a sign-in card.</span></span> <span data-ttu-id="af644-202">Teams behandelt diese Anforderung als automatischen Tokenerwerb, wenn die Eigenschaft `TokenExchangeResource` auf der Karte aufgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="af644-202">Teams treats this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="af644-203">Für den Kanal "Teams" wird nur die Eigenschaft berücksichtigt, die eine `Id` Tokenanforderung eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="af644-203">For the Teams channel, only the `Id` property, which uniquely identifies a token request, is honored.</span></span>

>[!NOTE]
> <span data-ttu-id="af644-204">Das Microsoft Bot Framework `OAuthPrompt` oder das wird für die `MultiProviderAuthDialog` SSO-Authentifizierung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="af644-204">The Microsoft Bot Framework `OAuthPrompt` or the `MultiProviderAuthDialog` is supported for SSO authentication.</span></span>

<span data-ttu-id="af644-205">Wenn der Benutzer die Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird im folgenden Dialogfeld die Zustimmungserfahrung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="af644-205">If the user is using the application for the first time and user consent is required, the following dialog box appears to continue with the consent experience:</span></span>

![Dialogfeld "Zustimmung"](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="af644-207">Wenn der Benutzer **"Weiter"** auswählt, treten die folgenden Ereignisse auf:</span><span class="sxs-lookup"><span data-stu-id="af644-207">When the user selects **Continue**, the following events occur:</span></span>

* <span data-ttu-id="af644-208">Wenn der Bot eine Anmeldeschaltfläche definiert, wird der Anmeldefluss für Bots ähnlich wie der Anmeldefluss von einer Schaltfläche für eine OAuth-Karte in einem Nachrichtendatenstrom ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="af644-208">If the bot defines a sign-in button, the sign in flow for bots is triggered similar to the sign in flow from an OAuth card button in a message stream.</span></span> <span data-ttu-id="af644-209">Der Entwickler muss entscheiden, welche Berechtigungen die Zustimmung des Benutzers erfordern.</span><span class="sxs-lookup"><span data-stu-id="af644-209">The developer must decide which permissions require user's consent.</span></span> <span data-ttu-id="af644-210">Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen benötigen, die über `openId` diesen hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="af644-210">This approach is recommended if you require a token with permissions beyond `openId`.</span></span> <span data-ttu-id="af644-211">Beispielsweise, wenn Sie das Token gegen Graphressourcen austauschen möchten.</span><span class="sxs-lookup"><span data-stu-id="af644-211">For example, if you want to exchange the token for graph resources.</span></span>

* <span data-ttu-id="af644-212">Wenn der Bot keine Anmeldeschaltfläche auf der OAuth-Karte zur Verfügung stellt, ist die Zustimmung des Benutzers für einen minimalen Satz von Berechtigungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af644-212">If the bot is not providing a sign-in button on the OAuth card, user consent is required for a minimal set of permissions.</span></span> <span data-ttu-id="af644-213">Dieses Token ist nützlich für die Standardauthentifizierung und zum Erhalten der E-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="af644-213">This token is useful for basic authentication and to get the user's email address.</span></span>

##### <a name="c-token-request-without-a-sign-in-button"></a><span data-ttu-id="af644-214">C#-Tokenanforderung ohne Anmeldeschaltfläche</span><span class="sxs-lookup"><span data-stu-id="af644-214">C# token request without a sign-in button</span></span>

```csharp
    var attachment = new Attachment
            {
                Content = new OAuthCard
                {
                    TokenExchangeResource = new TokenExchangeResource
                    {
                        Id = requestId
                    }
                },
                ContentType = OAuthCard.ContentType,
            };
            var activity = MessageFactory.Attachment(attachment);

            // NOTE: This activity needs to be sent in the 1:1 conversation between the bot and the user. 
            // If the bot supports group and channel scope, this code should be updated to send the request to the 1:1 chat. 

       await turnContext.SendActivityAsync(activity, cancellationToken);
```

#### <a name="receive-the-bot-token"></a><span data-ttu-id="af644-215">Empfangen des Bottokens</span><span class="sxs-lookup"><span data-stu-id="af644-215">Receive the bot token</span></span>

<span data-ttu-id="af644-216">Die Antwort mit dem Token wird über eine Aufrufaktivität mit demselben Schema wie andere Aufrufaktivitäten gesendet, die die Bots heute erhalten.</span><span class="sxs-lookup"><span data-stu-id="af644-216">The response with the token is sent through an invoke activity with the same schema as other invoke activities that the bots receive today.</span></span> <span data-ttu-id="af644-217">Der einzige Unterschied besteht im Aufrufnamen, **der Anmeldung/tokenExchange** und dem **Wertfeld.**</span><span class="sxs-lookup"><span data-stu-id="af644-217">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field.</span></span> <span data-ttu-id="af644-218">Das **Wertfeld** enthält die **ID**, eine Zeichenfolge der  ursprünglichen Anforderung, um das Token und das Tokenfeld abzurufen, einen Zeichenfolgenwert einschließlich des Tokens.</span><span class="sxs-lookup"><span data-stu-id="af644-218">The **value** field contains the **Id**, a string of the initial request to get the token and the **token** field, a string value including the token.</span></span>

>[!NOTE]
> <span data-ttu-id="af644-219">Sie erhalten möglicherweise mehrere Antworten für eine bestimmte Anforderung, wenn der Benutzer über mehrere aktive Endpunkte verfügt.</span><span class="sxs-lookup"><span data-stu-id="af644-219">You might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="af644-220">Sie müssen die Antworten mit dem Token deduplizieren.</span><span class="sxs-lookup"><span data-stu-id="af644-220">You must deduplicate the responses with the token.</span></span>

##### <a name="c-code-to-handle-the-invoke-activity"></a><span data-ttu-id="af644-221">C#-Code zum Behandeln der Aufrufaktivität</span><span class="sxs-lookup"><span data-stu-id="af644-221">C# code to handle the invoke activity</span></span>

```csharp
    protected override async Task<InvokeResponse> OnInvokeActivityAsync
    (ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
            {
                try
                {
                    if (turnContext.Activity.Name == SignInConstants.TokenExchangeOperationName && turnContext.Activity.ChannelId == Channels.Msteams)
                    {
                        await OnTokenResponseEventAsync(turnContext, cancellationToken);
                        return new InvokeResponse() { Status = 200 };
                    }
                    else
                    {
                        return await base.OnInvokeActivityAsync(turnContext, cancellationToken);
                    }
                }
                catch (InvokeResponseException e)
                {
                    return e.CreateInvokeResponse();
                }
            }
```

<span data-ttu-id="af644-222">Der `turnContext.activity.value` ist vom Typ [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) und enthält das Token, das von Ihrem Bot weiter verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="af644-222">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="af644-223">Sie müssen die Token aus Leistungsgründen speichern und aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="af644-223">You must store the tokens for performance reasons and refresh them.</span></span>

### <a name="update-the-auth-sample"></a><span data-ttu-id="af644-224">Aktualisieren des Authentifizierungsbeispiels</span><span class="sxs-lookup"><span data-stu-id="af644-224">Update the auth sample</span></span>

<span data-ttu-id="af644-225">Öffnen [Sie das Beispiel für die](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) Teams-Authentifizierung, und führen Sie dann die folgenden Schritte aus, um es zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="af644-225">Open [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) and then complete the following steps to update it:</span></span>

1. <span data-ttu-id="af644-226">Aktualisieren Sie den TeamsBot, um die Deduplikung der eingehenden Anforderung zu verarbeiten, indem Sie den folgenden Code verwenden:</span><span class="sxs-lookup"><span data-stu-id="af644-226">Update the TeamsBot to handle the deduping of the incoming request by including the following code:</span></span>

    ```csharp
        protected override async Task OnSignInInvokeAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
            {
                await Dialog.RunAsync(turnContext, ConversationState.CreateProperty<DialogState>(nameof(DialogState)), cancellationToken);
            }
        protected override async Task OnTokenResponseEventAsync(ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
            {
                await Dialog.RunAsync(turnContext, ConversationState.CreateProperty<DialogState>(nameof(DialogState)), cancellationToken);
            }
    ```
  
2. <span data-ttu-id="af644-227">Aktualisieren Sie das Update, um das , Kennwort und den verbindungsnamen, die `appsettings.json` `botId` in Aktualisieren des [Azure-Portals mit der OAuth-Verbindung definiert sind.](#update-the-azure-portal-with-the-oauth-connection)</span><span class="sxs-lookup"><span data-stu-id="af644-227">Update `appsettings.json` to include the `botId`, password, and the connection name defined in [Update the Azure portal with the OAuth connection](#update-the-azure-portal-with-the-oauth-connection).</span></span>
3. <span data-ttu-id="af644-228">Aktualisieren Sie das Manifest, und stellen `token.botframework.com` Sie sicher, dass es sich in der Liste der gültigen Domänen befindet.</span><span class="sxs-lookup"><span data-stu-id="af644-228">Update the manifest and ensure that `token.botframework.com` is in the valid domains list.</span></span> <span data-ttu-id="af644-229">Weitere Informationen finden Sie im [Beispiel zur Teams-Authentifizierung.](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth)</span><span class="sxs-lookup"><span data-stu-id="af644-229">For more information, see [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>
4. <span data-ttu-id="af644-230">Zippern Sie das Manifest mit den Profilabbildern, und installieren Sie es in Teams.</span><span class="sxs-lookup"><span data-stu-id="af644-230">Zip the manifest with the profile images and install it in Teams.</span></span>

#### <a name="additional-code-samples"></a><span data-ttu-id="af644-231">Zusätzliche Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="af644-231">Additional code samples</span></span>

* <span data-ttu-id="af644-232">[C#-Beispiel mit dem Bot Framework SDK](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore).</span><span class="sxs-lookup"><span data-stu-id="af644-232">[C# sample using the Bot Framework SDK](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore).</span></span>
