---
title: Unterstützung für einmaliges Anmelden für Bots
description: Beschreibt, wie Sie ein Benutzertoken erhalten. Derzeit kann ein Botentwickler eine Anmeldekarte oder den azure bot-Dienst mit der OAuth-Kartenunterstützung verwenden.
keywords: Token, Benutzertoken, SSO-Unterstützung für Bots
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 8da2591c3685b5bd3dffd272abd77babe94ab04c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020049"
---
# <a name="single-sign-on-sso-support-for-bots"></a><span data-ttu-id="45592-105">Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Bots</span><span class="sxs-lookup"><span data-stu-id="45592-105">Single sign-on (SSO) support for bots</span></span>

<span data-ttu-id="45592-106">Die einmalige Anmeldeauthentifizierung in Azure Active Directory (AAD) minimiert die Anzahl der Benutzer, die ihre Anmeldeinformationen eingeben müssen, indem das Authentifizierungstoken automatisch aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="45592-106">Single sign-on authentication in Azure Active Directory (AAD) minimizes the number of times users need to enter their sign in credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="45592-107">Wenn Benutzer der Verwendung Ihrer App zustimmen, müssen sie auf einem anderen Gerät keine erneute Zustimmung erteilen und können sich automatisch anmelden.</span><span class="sxs-lookup"><span data-stu-id="45592-107">If users agree to use your app, they need not provide consent again on another device and can sign in automatically.</span></span> <span data-ttu-id="45592-108">Der Ablauf ähnelt dem der Microsoft Teams-SSO-Unterstützung, der Unterschied besteht jedoch im Protokoll, wie ein Bot Token [anfordert](#request-a-bot-token) und Antworten [empfängt.](#receive-the-bot-token) [](../../../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="45592-108">The flow is similar to that of [Microsoft Teams tab SSO support](../../../tabs/how-to/authentication/auth-aad-sso.md), however, the difference is in the protocol for how a bot [requests tokens](#request-a-bot-token) and [receives responses](#receive-the-bot-token).</span></span>

>[!NOTE]
> <span data-ttu-id="45592-109">OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von AAD und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="45592-109">OAuth 2.0 is an open standard for authentication and authorization used by AAD and many other identity providers.</span></span> <span data-ttu-id="45592-110">Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.</span><span class="sxs-lookup"><span data-stu-id="45592-110">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

## <a name="bot-sso-at-runtime"></a><span data-ttu-id="45592-111">Bot-SSO zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="45592-111">Bot SSO at runtime</span></span>

![Bot-SSO zur Laufzeitdiagramm](../../../assets/images/bots/bots-sso-diagram.png)

<span data-ttu-id="45592-113">Führen Sie die folgenden Schritte aus, um Authentifizierungs- und Botanwendungstoken abzurufen:</span><span class="sxs-lookup"><span data-stu-id="45592-113">Complete the following steps to get authentication and bot application tokens:</span></span>

1. <span data-ttu-id="45592-114">Der Bot sendet eine Nachricht mit einer OAuthCard, welche die `tokenExchangeResource`-Eigenschaft enthält.</span><span class="sxs-lookup"><span data-stu-id="45592-114">The bot sends a message with an OAuthCard that contains the `tokenExchangeResource` property.</span></span> <span data-ttu-id="45592-115">Er weist Teams an, ein Authentifizierungstoken für die Botanwendung abzurufen.</span><span class="sxs-lookup"><span data-stu-id="45592-115">It tells Teams to obtain an authentication token for the bot application.</span></span> <span data-ttu-id="45592-116">Der Benutzer erhält auf allen aktiven Benutzerendpunkten Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="45592-116">The user receives messages at all the active user endpoints.</span></span>

    > [!NOTE]
    >* <span data-ttu-id="45592-117">Ein Benutzer kann mehrere aktive Endpunkte gleichzeitig haben.</span><span class="sxs-lookup"><span data-stu-id="45592-117">A user can have more than one active endpoint at a time.</span></span>
    >* <span data-ttu-id="45592-118">Der Bot-Token wird von jedem aktiven Benutzerendpunkt erhalten.</span><span class="sxs-lookup"><span data-stu-id="45592-118">The bot token is received from every active user endpoint.</span></span>
    >* <span data-ttu-id="45592-119">Die App muss für SSO-Support im persönlichen Bereich installiert sein.</span><span class="sxs-lookup"><span data-stu-id="45592-119">The app must be installed in personal scope for SSO support.</span></span>

2. <span data-ttu-id="45592-120">Wenn der aktuelle Benutzer Ihre Botanwendung zum ersten Mal verwendet, wird eine Anforderungsaufforderung angezeigt, in der der Benutzer aufgefordert wird, eine der folgenden Schritte zu tun:</span><span class="sxs-lookup"><span data-stu-id="45592-120">If the current user is using your bot application for the first time, a request prompt appears requesting the user to do one of the following:</span></span>
    * <span data-ttu-id="45592-121">Geben Sie bei Bedarf ihre Zustimmung ein.</span><span class="sxs-lookup"><span data-stu-id="45592-121">Provide consent, if required.</span></span>
    * <span data-ttu-id="45592-122">Erhöhte Authentifizierung durchführen, z. B. die zweistufige Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="45592-122">Handle step-up authentication, such as two-factor authentication.</span></span>

3. <span data-ttu-id="45592-123">Teams das Botanwendungstoken vom AAD-Endpunkt für den aktuellen Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="45592-123">Teams requests the bot application token from the AAD endpoint for the current user.</span></span>

4. <span data-ttu-id="45592-124">AAD sendet das Botanwendungstoken an die Teams Anwendung.</span><span class="sxs-lookup"><span data-stu-id="45592-124">AAD sends the bot application token to the Teams application.</span></span>

5. <span data-ttu-id="45592-125">Teams sendet das Token an den Bot als Teil des Wertobjekts, das von der Aufrufaktivität mit dem Namen **sign-in/tokenExchange zurückgegeben wird.**</span><span class="sxs-lookup"><span data-stu-id="45592-125">Teams sends the token to the bot as part of the value object returned by the invoke activity with the name **sign-in/tokenExchange**.</span></span>
  
6. <span data-ttu-id="45592-126">Das analysierte Token in der Bot-Anwendung stellt die erforderlichen Informationen zur Verfügung, wie z. B. die E-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="45592-126">The parsed token in the bot application provides the required information, such as the user's email address.</span></span>
  
## <a name="develop-an-sso-teams-bot"></a><span data-ttu-id="45592-127">Entwickeln eines SSO-Teams Bots</span><span class="sxs-lookup"><span data-stu-id="45592-127">Develop an SSO Teams bot</span></span>
  
<span data-ttu-id="45592-128">Führen Sie die folgenden Schritte aus, um einen SSO-Teams zu entwickeln:</span><span class="sxs-lookup"><span data-stu-id="45592-128">Complete the following steps to develop an SSO Teams bot:</span></span>

1. <span data-ttu-id="45592-129">[Registrieren Sie Ihre App über das AAD-Portal.](#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="45592-129">[Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span>
2. <span data-ttu-id="45592-130">[Aktualisieren Sie Teams Anwendungsmanifest für Ihren Bot](#update-your-teams-application-manifest-for-your-bot).</span><span class="sxs-lookup"><span data-stu-id="45592-130">[Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span>
3. <span data-ttu-id="45592-131">[Fügen Sie den Code zum Anfordern und Empfangen eines Bottokens hinzu.](#add-the-code-to-request-and-receive-a-bot-token)</span><span class="sxs-lookup"><span data-stu-id="45592-131">[Add the code to request and receive a bot token](#add-the-code-to-request-and-receive-a-bot-token).</span></span>

### <a name="register-your-app-through-the-aad-portal"></a><span data-ttu-id="45592-132">Registrieren Ihrer App über das AAD-Portal</span><span class="sxs-lookup"><span data-stu-id="45592-132">Register your app through the AAD portal</span></span>

<span data-ttu-id="45592-133">Die Schritte zum Registrieren Ihrer App über das AAD-Portal ähneln dem [Registerkarten-SSO-Fluss](../../../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="45592-133">The steps to register your app through the AAD portal are similar to the [tab SSO flow](../../../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="45592-134">Führen Sie die folgenden Schritte aus, um Ihre App zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="45592-134">Complete the following steps to register your app:</span></span>

1. <span data-ttu-id="45592-135">Registrieren Sie eine neue Anwendung im [Azure Active Directory – App-Registrierungsportal.](https://go.microsoft.com/fwlink/?linkid=2083908)</span><span class="sxs-lookup"><span data-stu-id="45592-135">Register a new application in the [Azure Active Directory – App Registrations](https://go.microsoft.com/fwlink/?linkid=2083908) portal.</span></span>
2. <span data-ttu-id="45592-136">Wählen **Sie Neue Registrierung aus.**</span><span class="sxs-lookup"><span data-stu-id="45592-136">Select **New Registration**.</span></span> <span data-ttu-id="45592-137">Die **Seite Anwendung registrieren** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="45592-137">The **Register an application** page appears.</span></span>
3. <span data-ttu-id="45592-138">Geben Sie **auf der Seite** Anwendung registrieren die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="45592-138">In the **Register an application** page, enter the following values:</span></span>
    1. <span data-ttu-id="45592-139">Geben Sie einen **Namen** für Ihre App ein.</span><span class="sxs-lookup"><span data-stu-id="45592-139">Enter a **Name** for your app.</span></span>
    2. <span data-ttu-id="45592-140">Wählen Sie **die Unterstützten Kontotypen** aus, wählen Sie einzelnen Mandanten- oder mehrstufigen Kontotyp aus.</span><span class="sxs-lookup"><span data-stu-id="45592-140">Choose the **Supported account types**, select single tenant or multitenant account type.</span></span>

        > [!NOTE]
        >
        > <span data-ttu-id="45592-141">Die Benutzer werden nicht um Zustimmung gebeten und erhalten sofort Zugriffstoken, wenn die AAD-App im selben Mandanten registriert ist, in dem sie eine Authentifizierungsanforderung in Teams.</span><span class="sxs-lookup"><span data-stu-id="45592-141">The users are not asked for consent and are granted access tokens right away, if the AAD app is registered in the same tenant where they are making an authentication request in Teams.</span></span> <span data-ttu-id="45592-142">Die Benutzer müssen jedoch den Berechtigungen zustimmen, wenn die AAD-App in einem anderen Mandanten registriert ist.</span><span class="sxs-lookup"><span data-stu-id="45592-142">However, the users must provide consent to the permissions, if the AAD app is registered in a different tenant.</span></span>

    3. <span data-ttu-id="45592-143">Wählen Sie **Registrieren** aus.</span><span class="sxs-lookup"><span data-stu-id="45592-143">Choose **Register**.</span></span>
4. <span data-ttu-id="45592-144">Kopieren und speichern Sie auf der Übersichtsseite die **Anwendungs-ID (Client-ID).**</span><span class="sxs-lookup"><span data-stu-id="45592-144">On the overview page, copy and save the **Application (client) ID**.</span></span> <span data-ttu-id="45592-145">Sie benötigen sie später beim Aktualisieren Teams Anwendungsmanifests.</span><span class="sxs-lookup"><span data-stu-id="45592-145">You need it later when updating your Teams application manifest.</span></span>
5. <span data-ttu-id="45592-146">Wählen Sie unter **Verwalten** die Option **Eine API verfügbar machen** aus.</span><span class="sxs-lookup"><span data-stu-id="45592-146">Under **Manage**, select **Expose an API**.</span></span> 

   > [!IMPORTANT]
    > * <span data-ttu-id="45592-147">Wenn Sie einen eigenständigen Bot erstellen, geben Sie den Anwendungs-ID-URI als `api://botid-{YourBotId}` ein.</span><span class="sxs-lookup"><span data-stu-id="45592-147">If you are building a standalone bot, enter the Application ID URI as `api://botid-{YourBotId}`.</span></span> <span data-ttu-id="45592-148">Hier **ist YourBotId** Ihre AAD-Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="45592-148">Here **YourBotId** is your AAD application ID.</span></span>
    > * <span data-ttu-id="45592-149">Wenn Sie eine App mit einem Bot und einer Registerkarte erstellen, geben Sie den Anwendungs-ID-URI als `api://fully-qualified-domain-name.com/botid-{YourBotId}` ein.</span><span class="sxs-lookup"><span data-stu-id="45592-149">If you are building an app with a bot and a tab, enter the Application ID URI as `api://fully-qualified-domain-name.com/botid-{YourBotId}`.</span></span>

5. <span data-ttu-id="45592-150">Wählen Sie die Berechtigungen aus, die Ihre Anwendung für den AAD-Endpunkt und optional für Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="45592-150">Select the permissions that your application needs for the AAD endpoint and, optionally, for Microsoft Graph.</span></span>
6. <span data-ttu-id="45592-151">[Erteilen von](/azure/active-directory/develop/v2-permissions-and-consent) Berechtigungen Teams Desktop-, Web- und mobilen Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="45592-151">[Grant permissions](/azure/active-directory/develop/v2-permissions-and-consent) for Teams desktop, web, and mobile applications.</span></span>
7. <span data-ttu-id="45592-152">Wählen Sie **Bereich hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="45592-152">Select **Add a scope**.</span></span>
8. <span data-ttu-id="45592-153">Fügen Sie in dem geöffneten Bereich eine Client-App hinzu, indem Sie `access_as_user` als **Bereichsname eingeben.**</span><span class="sxs-lookup"><span data-stu-id="45592-153">In the panel that opens, add a client app by entering `access_as_user` as the **Scope name**.</span></span>

    >[!NOTE]
    > <span data-ttu-id="45592-154">Der bereich "access_as_user", der zum Hinzufügen einer Client-App verwendet wird, ist für "Administratoren und Benutzer".</span><span class="sxs-lookup"><span data-stu-id="45592-154">The "access_as_user" scope used to add a client app is for "Administrators and users".</span></span>
    >
    > <span data-ttu-id="45592-155">Beachten Sie die folgenden wichtigen Einschränkungen:</span><span class="sxs-lookup"><span data-stu-id="45592-155">You must be aware of the following important restrictions:</span></span>
    >
    > * <span data-ttu-id="45592-156">Es werden nur Microsoft Graph-API-Berechtigungen auf Benutzerebene unterstützt, z. B. E-Mail, Profil, offline_access und OpenId.</span><span class="sxs-lookup"><span data-stu-id="45592-156">Only user-level Microsoft Graph API permissions, such as email, profile, offline_access, and OpenId are supported.</span></span> <span data-ttu-id="45592-157">Wenn Sie Zugriff auf andere Microsoft-Graph, z. B. oder benötigen, lesen Sie `User.Read` `Mail.Read` empfohlene [Problemumgehung](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-graph-scopes).</span><span class="sxs-lookup"><span data-stu-id="45592-157">If you need access to other Microsoft Graph scopes, such as `User.Read` or `Mail.Read`, see [recommended workaround](../../../tabs/how-to/authentication/auth-aad-sso.md#apps-that-require-additional-graph-scopes).</span></span>
    > * <span data-ttu-id="45592-158">Der Domänenname Ihrer Anwendung muss mit dem Domänennamen identisch sein, den Sie für Ihre AAD-Anwendung registriert haben.</span><span class="sxs-lookup"><span data-stu-id="45592-158">Your application's domain name must be same as the domain name that you have registered for your AAD application.</span></span>
    > * <span data-ttu-id="45592-159">Mehrere Domänen pro App werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="45592-159">Multiple domains per app are currently not supported.</span></span>
    > * <span data-ttu-id="45592-160">Anwendungen, die die Domäne verwenden, werden `azurewebsites.net` nicht unterstützt, da sie häufig verwendet werden und möglicherweise ein Sicherheitsrisiko darstellen.</span><span class="sxs-lookup"><span data-stu-id="45592-160">Applications that use the `azurewebsites.net` domain are not supported because it is common and may be a security risk.</span></span>

#### <a name="update-the-azure-portal-with-the-oauth-connection"></a><span data-ttu-id="45592-161">Aktualisieren des Azure-Portals mit der OAuth-Verbindung</span><span class="sxs-lookup"><span data-stu-id="45592-161">Update the Azure portal with the OAuth connection</span></span>

<span data-ttu-id="45592-162">Führen Sie die folgenden Schritte aus, um das Azure-Portal mit der OAuth-Verbindung zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="45592-162">Complete the following steps to update the Azure portal with the OAuth connection:</span></span>

1. <span data-ttu-id="45592-163">Navigieren Sie im Azure-Portal zu **App-Registrierungen**.</span><span class="sxs-lookup"><span data-stu-id="45592-163">In the Azure Portal, navigate to **App registrations**.</span></span>

2. <span data-ttu-id="45592-164">Wechseln Sie zu **API-Berechtigungen**.</span><span class="sxs-lookup"><span data-stu-id="45592-164">Go to **API Permissions**.</span></span> <span data-ttu-id="45592-165">Wählen **Sie Microsoft Graph** Delegierte Berechtigungen hinzufügen aus, und fügen Sie dann die folgenden Berechtigungen aus der Microsoft  >    >  Graph-API hinzu:</span><span class="sxs-lookup"><span data-stu-id="45592-165">Select **Add a permission** > **Microsoft Graph** > **Delegated permissions**, then add the following permissions from Microsoft Graph API:</span></span>
    * <span data-ttu-id="45592-166">User.Read (standardmäßig aktiviert)</span><span class="sxs-lookup"><span data-stu-id="45592-166">User.Read (enabled by default)</span></span>
    * <span data-ttu-id="45592-167">email</span><span class="sxs-lookup"><span data-stu-id="45592-167">email</span></span>
    * <span data-ttu-id="45592-168">offline_access</span><span class="sxs-lookup"><span data-stu-id="45592-168">offline_access</span></span>
    * <span data-ttu-id="45592-169">OpenId</span><span class="sxs-lookup"><span data-stu-id="45592-169">OpenId</span></span>
    * <span data-ttu-id="45592-170">Profil</span><span class="sxs-lookup"><span data-stu-id="45592-170">profile</span></span>

3. <span data-ttu-id="45592-171">Navigieren Sie im Azure-Portal zu **Bot Channels Registration**.</span><span class="sxs-lookup"><span data-stu-id="45592-171">In the Azure Portal, navigate to **Bot Channels Registration**.</span></span>

4. <span data-ttu-id="45592-172">Wählen **Einstellungen** linken Bereich aus, und wählen Sie **im** Abschnitt **OAuth Connection Einstellungen** Einstellung hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="45592-172">Select **Settings** on the left pane and choose **Add Setting** under the **OAuth Connection Settings** section.</span></span>

    ![SSOBotHandle2-Ansicht](../../../assets/images/bots/bots-vuSSOBotHandle2-settings.png)

5. <span data-ttu-id="45592-174">Führen Sie die folgenden Schritte aus, um das **Formular Neue Verbindungseinstellung auszufüllen:**</span><span class="sxs-lookup"><span data-stu-id="45592-174">Perform the following steps to complete the **New Connection Setting** form:</span></span>

    >[!NOTE]
    > <span data-ttu-id="45592-175">**Möglicherweise ist in** der AAD-Anwendung eine implizite Erteilung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45592-175">**Implicit grant** may be required in the AAD application.</span></span>

    1. <span data-ttu-id="45592-176">Geben Sie **auf der** Seite **Neue Verbindungseinstellung einen Namen** ein.</span><span class="sxs-lookup"><span data-stu-id="45592-176">Enter a **Name** in the **New Connection Setting** page.</span></span> <span data-ttu-id="45592-177">Dies ist der Name, auf den in den Einstellungen Ihres Botdienstcodes in *Schritt 5* von Bot SSO zur Laufzeit [verwiesen wird.](#bot-sso-at-runtime)</span><span class="sxs-lookup"><span data-stu-id="45592-177">This is the name that is referred to inside the settings of your bot service code in *step 5* of [Bot SSO at runtime](#bot-sso-at-runtime).</span></span>
    2. <span data-ttu-id="45592-178">Wählen Sie **in der** Dropdownliste Dienstanbieter die Option **Azure Active Directory v2 aus.**</span><span class="sxs-lookup"><span data-stu-id="45592-178">From the **Service Provider** drop-down, select **Azure Active Directory v2**.</span></span>
    3. <span data-ttu-id="45592-179">Geben Sie die Clientanmeldeinformationen ein, z. B. **Client-ID** und **geheimer Client für** die AAD-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="45592-179">Enter the client credentials, such as **Client id** and **Client secret** for the AAD application.</span></span>
    4. <span data-ttu-id="45592-180">Verwenden Sie **für die Token-Exchange-URL** den unter [Update your Teams application manifest for your bot definierten Bereichswert.](#update-your-teams-application-manifest-for-your-bot)</span><span class="sxs-lookup"><span data-stu-id="45592-180">For the **Token Exchange URL**, use the scope value defined in [Update your Teams application manifest for your bot](#update-your-teams-application-manifest-for-your-bot).</span></span> <span data-ttu-id="45592-181">Die Token Exchange-URL gibt dem SDK an, dass diese AAD-Anwendung für SSO konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="45592-181">The Token Exchange URL indicates to the SDK that this AAD application is configured for SSO.</span></span>
    5. <span data-ttu-id="45592-182">Geben Sie **im Feld Mandanten-ID** gemeinsame *ein.*</span><span class="sxs-lookup"><span data-stu-id="45592-182">In the **Tenant ID** box, enter *common*.</span></span>
    6. <span data-ttu-id="45592-183">Fügen Sie alle **Bereiche hinzu,** die beim Angeben von Berechtigungen für downstream-APIs für Ihre AAD-Anwendung konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="45592-183">Add all the **Scopes** configured when specifying permissions to downstream APIs for your AAD application.</span></span> <span data-ttu-id="45592-184">Wenn die Client-ID und der geheime Clientgeheimnis angegeben sind, tauscht der Tokenspeicher das Token durch ein Diagrammtoken mit definierten Berechtigungen aus.</span><span class="sxs-lookup"><span data-stu-id="45592-184">With the Client id and Client secret provided, the token store exchanges the token for a graph token with defined permissions.</span></span>
    7. <span data-ttu-id="45592-185">Wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="45592-185">Select **Save**.</span></span>

    ![VuSSOBotConnection-Einstellungsansicht](../../../assets/images/bots/bots-vuSSOBotConnection-settings.png)

### <a name="update-your-teams-application-manifest-for-your-bot"></a><span data-ttu-id="45592-187">Aktualisieren des Teams Anwendungsmanifests für Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="45592-187">Update your Teams application manifest for your bot</span></span>

<span data-ttu-id="45592-188">Wenn die Anwendung einen eigenständigen Bot enthält, verwenden Sie den folgenden Code, um dem Anwendungsmanifest Teams hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="45592-188">If the application contains a standalone bot, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://botid-00000000-0000-0000-0000-000000000000"
        }
```
<span data-ttu-id="45592-189">Wenn die Anwendung einen Bot und eine Registerkarte enthält, verwenden Sie den folgenden Code, um dem Anwendungsmanifest Teams hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="45592-189">If the application contains a bot and a tab, then use the following code to add new properties to the Teams application manifest:</span></span>

```json
    "webApplicationInfo": 
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "resource": "api://subdomain.example.com/botid-00000000-0000-0000-0000-000000000000"
        }
```

<span data-ttu-id="45592-190">**webApplicationInfo** ist das übergeordnete Element der folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="45592-190">**webApplicationInfo** is the parent of the following elements:</span></span>

* <span data-ttu-id="45592-191">**id** – Die Client-ID der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="45592-191">**id** - The client ID of the application.</span></span> <span data-ttu-id="45592-192">Dies ist die Anwendungs-ID, die Sie im Rahmen der Registrierung der Anwendung bei AAD erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="45592-192">This is the application ID that you obtained as part of registering the application with AAD.</span></span>
* <span data-ttu-id="45592-193">**resource** – Die Domäne und Unterdomäne Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="45592-193">**resource** - The domain and subdomain of your application.</span></span> <span data-ttu-id="45592-194">Dies ist derselbe URI, einschließlich des Protokolls, das Sie beim Erstellen Ihrer in Registrieren Ihrer App `api://` `scope` über das [AAD-Portal registriert haben.](#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="45592-194">This is the same URI, including the `api://` protocol that you registered when creating your `scope` in [Register your app through the AAD portal](#register-your-app-through-the-aad-portal).</span></span> <span data-ttu-id="45592-195">Sie dürfen den Pfad `access_as_user` nicht in Ihre Ressource verwenden.</span><span class="sxs-lookup"><span data-stu-id="45592-195">You must not include the `access_as_user` path in your resource.</span></span> <span data-ttu-id="45592-196">Der Domänenteil dieses URI muss mit der Domäne und den Unterdomänen übereinstimmen, die in den URLs ihres Teams werden.</span><span class="sxs-lookup"><span data-stu-id="45592-196">The domain part of this URI must match the domain and subdomains used in the URLs of your Teams application manifest.</span></span>

### <a name="add-the-code-to-request-and-receive-a-bot-token"></a><span data-ttu-id="45592-197">Hinzufügen des Codes zum Anfordern und Empfangen eines Bottokens</span><span class="sxs-lookup"><span data-stu-id="45592-197">Add the code to request and receive a bot token</span></span>

#### <a name="request-a-bot-token"></a><span data-ttu-id="45592-198">Anfordern eines Bottokens</span><span class="sxs-lookup"><span data-stu-id="45592-198">Request a bot token</span></span>

<span data-ttu-id="45592-199">Die Anforderung, das Token abzurufen, ist eine normale POST-Nachrichtenanforderung unter Verwendung des vorhandenen Nachrichtenschemas.</span><span class="sxs-lookup"><span data-stu-id="45592-199">The request to get the token is a normal POST message request using the existing message schema.</span></span> <span data-ttu-id="45592-200">Sie ist in den Anlagen einer OAuthCard enthalten.</span><span class="sxs-lookup"><span data-stu-id="45592-200">It is included in the attachments of an OAuthCard.</span></span> <span data-ttu-id="45592-201">Das Schema für die OAuthCard-Klasse ist in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) definiert und ähnelt einer Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="45592-201">The schema for the OAuthCard class is defined in [Microsoft Bot Schema 4.0](/dotnet/api/microsoft.bot.schema.oauthcard?view=botbuilder-dotnet-stable&preserve-view=true) and it is similar to a sign-in card.</span></span> <span data-ttu-id="45592-202">Teams wird diese Anforderung als automatischer Tokenerwerb behandelt, wenn die `TokenExchangeResource` Eigenschaft auf der Karte aufgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="45592-202">Teams treats this request as a silent token acquisition if the `TokenExchangeResource` property is populated on the card.</span></span> <span data-ttu-id="45592-203">Für den Teams wird nur die Eigenschaft berücksichtigt, die eine Tokenanforderung `Id` eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="45592-203">For the Teams channel, only the `Id` property, which uniquely identifies a token request, is honored.</span></span>

>[!NOTE]
> <span data-ttu-id="45592-204">Die Microsoft Bot Framework `OAuthPrompt` oder die wird für die `MultiProviderAuthDialog` SSO-Authentifizierung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="45592-204">The Microsoft Bot Framework `OAuthPrompt` or the `MultiProviderAuthDialog` is supported for SSO authentication.</span></span>

<span data-ttu-id="45592-205">Wenn der Benutzer die Anwendung zum ersten Mal verwendet und die Zustimmung des Benutzers erforderlich ist, wird das folgende Dialogfeld mit der Zustimmung fortgesetzt:</span><span class="sxs-lookup"><span data-stu-id="45592-205">If the user is using the application for the first time and user consent is required, the following dialog box appears to continue with the consent experience:</span></span>

![Dialogfeld "Zustimmung"](../../../assets/images/bots/bots-consent-dialogbox.png)

<span data-ttu-id="45592-207">Wenn der Benutzer **Weiter** auswählt, treten die folgenden Ereignisse auf:</span><span class="sxs-lookup"><span data-stu-id="45592-207">When the user selects **Continue**, the following events occur:</span></span>

* <span data-ttu-id="45592-208">Wenn der Bot eine Anmeldeschaltfläche definiert, wird der Anmeldefluss für Bots ähnlich wie der Anmeldefluss von einer OAuth-Kartenschaltfläche in einem Nachrichtenstrom ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="45592-208">If the bot defines a sign-in button, the sign in flow for bots is triggered similar to the sign in flow from an OAuth card button in a message stream.</span></span> <span data-ttu-id="45592-209">Der Entwickler muss entscheiden, welche Berechtigungen die Zustimmung des Benutzers erfordern.</span><span class="sxs-lookup"><span data-stu-id="45592-209">The developer must decide which permissions require user's consent.</span></span> <span data-ttu-id="45592-210">Dieser Ansatz wird empfohlen, wenn Sie ein Token mit Berechtigungen benötigen, die über `openId` hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="45592-210">This approach is recommended if you require a token with permissions beyond `openId`.</span></span> <span data-ttu-id="45592-211">Wenn Sie beispielsweise das Token gegen Graphressourcen austauschen möchten.</span><span class="sxs-lookup"><span data-stu-id="45592-211">For example, if you want to exchange the token for graph resources.</span></span>

* <span data-ttu-id="45592-212">Wenn der Bot keine Anmeldeschaltfläche auf der OAuth-Karte zur Verfügung stellt, ist die Zustimmung des Benutzers für einen minimalen Satz von Berechtigungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="45592-212">If the bot is not providing a sign-in button on the OAuth card, user consent is required for a minimal set of permissions.</span></span> <span data-ttu-id="45592-213">Dieses Token ist nützlich für die Standardauthentifizierung und zum Erhalten der E-Mail-Adresse des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="45592-213">This token is useful for basic authentication and to get the user's email address.</span></span>

##### <a name="c-token-request-without-a-sign-in-button"></a><span data-ttu-id="45592-214">C# Tokenanforderung ohne Anmeldeschaltfläche</span><span class="sxs-lookup"><span data-stu-id="45592-214">C# token request without a sign-in button</span></span>

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

#### <a name="receive-the-bot-token"></a><span data-ttu-id="45592-215">Empfangen des Bottokens</span><span class="sxs-lookup"><span data-stu-id="45592-215">Receive the bot token</span></span>

<span data-ttu-id="45592-216">Die Antwort mit dem Token wird über eine Aufrufaktivität mit demselben Schema wie andere Aufrufaktivitäten gesendet, die bots heute erhalten.</span><span class="sxs-lookup"><span data-stu-id="45592-216">The response with the token is sent through an invoke activity with the same schema as other invoke activities that the bots receive today.</span></span> <span data-ttu-id="45592-217">Der einzige Unterschied ist der Aufrufname, **die Anmeldung/tokenExchange** und das **Wertfeld.**</span><span class="sxs-lookup"><span data-stu-id="45592-217">The only difference is the invoke name, **sign-in/tokenExchange** and the **value** field.</span></span> <span data-ttu-id="45592-218">Das **Wertfeld** enthält die **ID**, eine Zeichenfolge der  ursprünglichen Anforderung zum Abzurufen des Tokens und des Tokenfelds, einen Zeichenfolgenwert einschließlich des Tokens.</span><span class="sxs-lookup"><span data-stu-id="45592-218">The **value** field contains the **Id**, a string of the initial request to get the token and the **token** field, a string value including the token.</span></span>

>[!NOTE]
> <span data-ttu-id="45592-219">Möglicherweise erhalten Sie mehrere Antworten für eine bestimmte Anforderung, wenn der Benutzer über mehrere aktive Endpunkte verfügt.</span><span class="sxs-lookup"><span data-stu-id="45592-219">You might receive multiple responses for a given request if the user has multiple active endpoints.</span></span> <span data-ttu-id="45592-220">Sie müssen die Antworten mit dem Token deduplizieren.</span><span class="sxs-lookup"><span data-stu-id="45592-220">You must deduplicate the responses with the token.</span></span>

##### <a name="c-code-to-handle-the-invoke-activity"></a><span data-ttu-id="45592-221">C# zum Behandeln der Aufrufaktivität</span><span class="sxs-lookup"><span data-stu-id="45592-221">C# code to handle the invoke activity</span></span>

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

<span data-ttu-id="45592-222">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span><span class="sxs-lookup"><span data-stu-id="45592-222">The `turnContext.activity.value` is of type [TokenExchangeInvokeRequest](/dotnet/api/microsoft.bot.schema.tokenexchangeinvokerequest?view=botbuilder-dotnet-stable&preserve-view=true) and contains the token that can be further used by your bot.</span></span> <span data-ttu-id="45592-223">Sie müssen die Token aus Leistungsgründen speichern und aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="45592-223">You must store the tokens for performance reasons and refresh them.</span></span>

### <a name="token-exchange-failure"></a><span data-ttu-id="45592-224">Tokenaustauschfehler</span><span class="sxs-lookup"><span data-stu-id="45592-224">Token exchange failure</span></span>

<span data-ttu-id="45592-225">Verwenden Sie im Falle eines Tokenaustauschfehlers den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="45592-225">In case of token exchange failure, use the following code:</span></span>

```json
{ 
    "status": "<response code>", 
    "body": 
    { 
        "id":"<unique Id>", 
        "connectionName": "<connection Name on the bot (from the OAuth card)>", 
        "failureDetail": "<failure reason if status code is not 200, null otherwise>" 
    } 
}
```

<span data-ttu-id="45592-226">Informationen zu den Aktionen des Bots, wenn der Tokenaustausch keine Zustimmungsaufforderung auslöst, finden Sie in den folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="45592-226">To understand what the bot does when the token exchange fails to trigger a consent prompt, see the following steps:</span></span>

>[!NOTE]
> <span data-ttu-id="45592-227">Es ist keine Benutzeraktion erforderlich, wenn der Bot die Aktionen ergreift, wenn der Tokenaustausch fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="45592-227">No user action is required to be taken as the bot takes the actions when the token exchange fails.</span></span>

1. <span data-ttu-id="45592-228">Der Client startet eine Unterhaltung mit dem Bot, der ein OAuth-Szenario auslöst.</span><span class="sxs-lookup"><span data-stu-id="45592-228">The client starts a conversation with the bot triggering an OAuth scenario.</span></span>
2. <span data-ttu-id="45592-229">Der Bot sendet eine OAuth-Karte an den Client zurück.</span><span class="sxs-lookup"><span data-stu-id="45592-229">The bot sends back an OAuth card to the client.</span></span>
3. <span data-ttu-id="45592-230">Der Client fängt die OAuth-Karte ab, bevor sie dem Benutzer angezeigt wird, und überprüft, ob sie eine Eigenschaft `TokenExchangeResource` enthält.</span><span class="sxs-lookup"><span data-stu-id="45592-230">The client intercepts the OAuth card before displaying it to the user and checks if it contains a `TokenExchangeResource` property.</span></span>
4. <span data-ttu-id="45592-231">Wenn die Eigenschaft vorhanden ist, sendet der Client eine `TokenExchangeInvokeRequest` an den Bot.</span><span class="sxs-lookup"><span data-stu-id="45592-231">If the property exists, the client sends a `TokenExchangeInvokeRequest` to the bot.</span></span> <span data-ttu-id="45592-232">Der Client muss über ein auswechselbares Token für den Benutzer verfügen, das ein Azure AD v2-Token sein muss und dessen Benutzergruppe mit der Eigenschaft identisch sein `TokenExchangeResource.Uri` muss.</span><span class="sxs-lookup"><span data-stu-id="45592-232">The client must have an exchangeable token for the user, which must be an Azure AD v2 token and whose audience must be the same as `TokenExchangeResource.Uri` property.</span></span> <span data-ttu-id="45592-233">Der Client sendet eine Aufrufaktivität mit dem folgenden Code an den Bot:</span><span class="sxs-lookup"><span data-stu-id="45592-233">The client sends an invoke activity to the bot with the following code:</span></span>

    ```json
    {
        "type": "Invoke",
        "name": "signin/tokenExchange",
        "value": 
        {
            "id": "<any unique Id>",
            "connectionName": "<connection Name on the skill bot (from the OAuth card)>",
            "token": "<exchangeable token>"
        }
    }
    ```

5. <span data-ttu-id="45592-234">Der Bot verarbeitet das `TokenExchangeInvokeRequest` und gibt einen Zurück an den Client `TokenExchangeInvokeResponse` zurück.</span><span class="sxs-lookup"><span data-stu-id="45592-234">The bot processes the `TokenExchangeInvokeRequest` and returns a `TokenExchangeInvokeResponse` back to the client.</span></span> <span data-ttu-id="45592-235">Der Client muss warten, bis er den `TokenExchangeInvokeResponse` empfängt.</span><span class="sxs-lookup"><span data-stu-id="45592-235">The client must wait till it receives the `TokenExchangeInvokeResponse`.</span></span>

    ```json
    {
        "status": "<response code>",
        "body": 
        {
            "id":"<unique Id>",
            "connectionName": "<connection Name on the skill bot (from the OAuth card)>",
            "failureDetail": "<failure reason if status code is not 200, null otherwise>"
        }
    }
    ```

6. <span data-ttu-id="45592-236">Wenn der über einen von verfügt, zeigt der `TokenExchangeInvokeResponse` `status` Client die `200` OAuth-Karte nicht an.</span><span class="sxs-lookup"><span data-stu-id="45592-236">If the `TokenExchangeInvokeResponse` has a `status` of `200`, then the client does not show the OAuth card.</span></span> <span data-ttu-id="45592-237">Siehe das [normale Flussbild](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="45592-237">See the [normal flow image](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span></span> <span data-ttu-id="45592-238">Für andere Benutzer oder wenn die nicht empfangen wird, zeigt der Client dem Benutzer die `status` `TokenExchangeInvokeResponse` OAuth-Karte an.</span><span class="sxs-lookup"><span data-stu-id="45592-238">For any other `status` or if the `TokenExchangeInvokeResponse` is not received, then the client shows the OAuth card to the user.</span></span> <span data-ttu-id="45592-239">Weitere Informationen [finden Sie im Fallbackflussbild](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="45592-239">See the [fallback flow image](/azure/bot-service/bot-builder-concept-sso?view=azure-bot-service-4.0#sso-components-interaction&preserve-view=true).</span></span> <span data-ttu-id="45592-240">Dadurch wird sichergestellt, dass der SSO-Fluss bei Fehlern oder nicht errungenen Abhängigkeiten wie der Zustimmung des Benutzers auf den normalen OAuthCard-Fluss zurückfällt.</span><span class="sxs-lookup"><span data-stu-id="45592-240">This ensures that the SSO flow falls back to normal OAuthCard flow in case of any errors or unmet dependencies like user consent.</span></span>


### <a name="update-the-auth-sample"></a><span data-ttu-id="45592-241">Aktualisieren des Authentifizierungsbeispiels</span><span class="sxs-lookup"><span data-stu-id="45592-241">Update the auth sample</span></span>

<span data-ttu-id="45592-242">Öffnen [Teams Authentifizierungsbeispiel,](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) und führen Sie dann die folgenden Schritte aus, um es zu aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="45592-242">Open [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth) and then complete the following steps to update it:</span></span>

1. <span data-ttu-id="45592-243">Aktualisieren Sie den TeamsBot, um die Deduping der eingehenden Anforderung zu verarbeiten, indem Sie den folgenden Code verwenden:</span><span class="sxs-lookup"><span data-stu-id="45592-243">Update the TeamsBot to handle the deduping of the incoming request by including the following code:</span></span>

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
  
2. <span data-ttu-id="45592-244">Aktualisieren Sie, um das , Kennwort und den unter Aktualisieren des Azure-Portals mit der OAuth-Verbindung definierten `appsettings.json` `botId` [Verbindungsnamen zu verwenden.](#update-the-azure-portal-with-the-oauth-connection)</span><span class="sxs-lookup"><span data-stu-id="45592-244">Update `appsettings.json` to include the `botId`, password, and the connection name defined in [Update the Azure portal with the OAuth connection](#update-the-azure-portal-with-the-oauth-connection).</span></span>
3. <span data-ttu-id="45592-245">Aktualisieren Sie das Manifest, und `token.botframework.com` stellen Sie sicher, dass es sich in der Liste der gültigen Domänen befindet.</span><span class="sxs-lookup"><span data-stu-id="45592-245">Update the manifest and ensure that `token.botframework.com` is in the valid domains list.</span></span> <span data-ttu-id="45592-246">Weitere Informationen finden Sie unter [Teams Authentifizierungsbeispiel](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span><span class="sxs-lookup"><span data-stu-id="45592-246">For more information, see [Teams auth sample](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth).</span></span>
4. <span data-ttu-id="45592-247">Zip the manifest with the profile images and install it in Teams.</span><span class="sxs-lookup"><span data-stu-id="45592-247">Zip the manifest with the profile images and install it in Teams.</span></span>

## <a name="code-sample"></a><span data-ttu-id="45592-248">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="45592-248">Code sample</span></span>
|<span data-ttu-id="45592-249">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="45592-249">**Sample name**</span></span> | <span data-ttu-id="45592-250">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="45592-250">**Description**</span></span> |<span data-ttu-id="45592-251">**.NET**</span><span class="sxs-lookup"><span data-stu-id="45592-251">**.NET**</span></span> | 
|----------------|-----------------|--------------|
|<span data-ttu-id="45592-252">Bot framework SDK</span><span class="sxs-lookup"><span data-stu-id="45592-252">Bot framework SDK</span></span> | <span data-ttu-id="45592-253">Beispiel für die Verwendung des Bot-Framework-SDK.</span><span class="sxs-lookup"><span data-stu-id="45592-253">Sample for using the bot framework SDK.</span></span> |[<span data-ttu-id="45592-254">View</span><span class="sxs-lookup"><span data-stu-id="45592-254">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/experimental/teams-sso/csharp_dotnetcore)|
