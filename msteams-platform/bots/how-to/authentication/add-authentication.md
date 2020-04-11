---
title: Hinzufügen von Authentifizierung zu ihren Teams-bot
author: clearab
description: Vorgehensweise Hinzufügen von OAuth-Authentifizierung zu einem bot in Microsoft Teams.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 4a573037e970be3f6c010a0a3c4b2e18be811d2f
ms.sourcegitcommit: a08f1c7eb9fca11f44842773ab669c69d4af40db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2020
ms.locfileid: "43225798"
---
# <a name="add-authentication-to-your-teams-bot"></a><span data-ttu-id="631e2-103">Hinzufügen von Authentifizierung zu ihren Teams-bot</span><span class="sxs-lookup"><span data-stu-id="631e2-103">Add authentication to your Teams bot</span></span>

<span data-ttu-id="631e2-104">Es gibt Situationen, in denen Sie möglicherweise Bots in Microsoft Teams erstellen müssen, die im Namen des Benutzers auf Ressourcen zugreifen können, beispielsweise einen e-Mail-Dienst.</span><span class="sxs-lookup"><span data-stu-id="631e2-104">There are times when you may need to create bots in Microsoft Teams that can access resources on behalf of the user, such as a mail service.</span></span>

<span data-ttu-id="631e2-105">In diesem Artikel wird die Verwendung der Azure bot Service V4 SDK-Authentifizierung basierend auf OAuth 2,0.</span><span class="sxs-lookup"><span data-stu-id="631e2-105">This article demonstrates how to use Azure Bot Service v4 SDK authentication, based on OAuth 2.0.</span></span> <span data-ttu-id="631e2-106">Dies erleichtert die Entwicklung eines bot, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="631e2-106">This makes it easier to develop a bot that can use authentication tokens based on the user's credentials.</span></span> <span data-ttu-id="631e2-107">Key in all dies ist die Verwendung von **Identitätsanbietern**, wie wir später sehen werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-107">Key in all this is the use of **identity providers**, as we will see later.</span></span>

<span data-ttu-id="631e2-108">OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-108">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="631e2-109">Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="631e2-109">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

<span data-ttu-id="631e2-110">Ein grundlegendes Verständnis finden Sie in [OAuth 2 vereinfacht](https://aka.ms/oauth2-simplified) , und [OAuth 2,0](https://oauth.net/2/) für die vollständige Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="631e2-110">See [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) for a basic understanding, and [OAuth 2.0](https://oauth.net/2/) for the complete specification.</span></span>

<span data-ttu-id="631e2-111">Weitere Informationen darüber, wie der Azure bot-Dienst die Authentifizierung verarbeitet, finden Sie unter [User Authentication in a Conversation](https://aka.ms/azure-bot-authentication).</span><span class="sxs-lookup"><span data-stu-id="631e2-111">For more information about how the Azure Bot Service handles authentication, see [User authentication within a conversation](https://aka.ms/azure-bot-authentication).</span></span>

<span data-ttu-id="631e2-112">In diesem Artikel erhalten Sie Informationen zu folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="631e2-112">In this article you'll learn:</span></span>

- <span data-ttu-id="631e2-113">**Erstellen eines Authentifizierungs aktivierten bot**.</span><span class="sxs-lookup"><span data-stu-id="631e2-113">**How to create an authentication-enabled bot**.</span></span> <span data-ttu-id="631e2-114">Sie verwenden [CS-auth-Sample][teams-auth-bot-cs] zum Verarbeiten von Anmeldeinformationen für die Benutzeranmeldung und zum Generieren des Authentifizierungstokens.</span><span class="sxs-lookup"><span data-stu-id="631e2-114">You'll use [cs-auth-sample][teams-auth-bot-cs] to handle user sign-in credentials and the generating the authentication token.</span></span>
- <span data-ttu-id="631e2-115">**Wie Sie den bot in Azure bereitstellen und einem Identitätsanbieter zuordnen**.</span><span class="sxs-lookup"><span data-stu-id="631e2-115">**How to deploy the bot to Azure and associate it with an identity provider**.</span></span> <span data-ttu-id="631e2-116">Der Anbieter gibt ein Token basierend auf den Anmeldeinformationen für die Benutzeranmeldung aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-116">The provider issues a token based on user sign-in credentials.</span></span> <span data-ttu-id="631e2-117">Der Bot kann mithilfe des Tokens auf Ressourcen zugreifen, beispielsweise auf einen e-Mail-Dienst, für den eine Authentifizierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="631e2-117">The bot can use the token to access resources, such as a mail service, which require authentication.</span></span> <span data-ttu-id="631e2-118">Weitere Informationen finden Sie unter [Microsoft Teams-Authentifizierungs Fluss für Bots](auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="631e2-118">For more information see  [Microsoft Teams authentication flow for bots](auth-flow-bot.md).</span></span>
- <span data-ttu-id="631e2-119">**Vorgehensweise zum Integrieren des bot in Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="631e2-119">**How to integrate the bot within Microsoft Teams**.</span></span> <span data-ttu-id="631e2-120">Nachdem der bot integriert wurde, können Sie sich in einem Chat anmelden und Nachrichten damit austauschen.</span><span class="sxs-lookup"><span data-stu-id="631e2-120">Once the bot has been integrated, you can sign in and exchange messages with it in a chat.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="631e2-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="631e2-121">Prerequisites</span></span>

- <span data-ttu-id="631e2-122">Kenntnisse der [grundlegenden][concept-basics]Funktionen von bot, der [Verwaltung von Status][concept-state], der [Dialogfeld Bibliothek][concept-dialogs]und der [Implementierung eines sequenziellen Unterhaltungs Flusses][simple-dialog].</span><span class="sxs-lookup"><span data-stu-id="631e2-122">Knowledge of [bot basics][concept-basics], [managing state][concept-state], the [dialogs library][concept-dialogs], and how to [implement sequential conversation flow][simple-dialog].</span></span>
- <span data-ttu-id="631e2-123">Kenntnisse in Azure und OAuth 2,0-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="631e2-123">Knowledge of Azure and OAuth 2.0 development.</span></span>
- <span data-ttu-id="631e2-124">Visual Studio 2017 oder höher und git.</span><span class="sxs-lookup"><span data-stu-id="631e2-124">Visual Studio 2017 or later and Git.</span></span>
- <span data-ttu-id="631e2-125">Azure-Konto.</span><span class="sxs-lookup"><span data-stu-id="631e2-125">Azure account.</span></span> <span data-ttu-id="631e2-126">Bei Bedarf können Sie ein [Kostenloses Azure-Konto](https://azure.microsoft.com/free/)erstellen.</span><span class="sxs-lookup"><span data-stu-id="631e2-126">If needed, you can create an [Azure free account](https://azure.microsoft.com/free/).</span></span>
- <span data-ttu-id="631e2-127">Im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="631e2-127">The following sample.</span></span>

    | <span data-ttu-id="631e2-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="631e2-128">Sample</span></span> | <span data-ttu-id="631e2-129">BotBuilder-Version</span><span class="sxs-lookup"><span data-stu-id="631e2-129">BotBuilder version</span></span> | <span data-ttu-id="631e2-130">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="631e2-130">Demonstrates</span></span> |
    |:---|:---:|:---|
    | <span data-ttu-id="631e2-131">**Bot-Authentifizierung** in [CS-auth-Sample][teams-auth-bot-cs]</span><span class="sxs-lookup"><span data-stu-id="631e2-131">**Bot authentication** in [cs-auth-sample][teams-auth-bot-cs]</span></span> | <span data-ttu-id="631e2-132">v4</span><span class="sxs-lookup"><span data-stu-id="631e2-132">v4</span></span> | <span data-ttu-id="631e2-133">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="631e2-133">OAuthCard support</span></span> |
    | <span data-ttu-id="631e2-134">**Bot-Authentifizierung** in [js-auth-Sample][teams-auth-bot-js]</span><span class="sxs-lookup"><span data-stu-id="631e2-134">**Bot authentication** in [js-auth-sample][teams-auth-bot-js]</span></span> | <span data-ttu-id="631e2-135">v4</span><span class="sxs-lookup"><span data-stu-id="631e2-135">v4</span></span>| <span data-ttu-id="631e2-136">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="631e2-136">OAuthCard support</span></span>  |
    | <span data-ttu-id="631e2-137">**Bot-Authentifizierung** in [py-auth-Sample][teams-auth-bot-py]</span><span class="sxs-lookup"><span data-stu-id="631e2-137">**Bot authentication** in [py-auth-sample][teams-auth-bot-py]</span></span> | <span data-ttu-id="631e2-138">v4</span><span class="sxs-lookup"><span data-stu-id="631e2-138">v4</span></span> | <span data-ttu-id="631e2-139">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="631e2-139">OAuthCard support</span></span> |

## <a name="create-the-resource-group"></a><span data-ttu-id="631e2-140">Erstellen der Ressourcengruppe</span><span class="sxs-lookup"><span data-stu-id="631e2-140">Create the resource group</span></span>

<span data-ttu-id="631e2-141">Die Ressourcengruppe und der Dienstplan sind nicht unbedingt erforderlich, Sie ermöglichen jedoch das bequeme Freigeben der von Ihnen erstellten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="631e2-141">The resource group and the service plan aren't strictly necessary, but they allow you to conveniently release the resources you create.</span></span> <span data-ttu-id="631e2-142">Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.</span><span class="sxs-lookup"><span data-stu-id="631e2-142">This is good practice for keeping your resources organized and manageable.</span></span>

<span data-ttu-id="631e2-143">Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das bot-Framework zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="631e2-143">You use a resource group to create individual resources for the Bot Framework.</span></span> <span data-ttu-id="631e2-144">Stellen Sie für die Leistung sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.</span><span class="sxs-lookup"><span data-stu-id="631e2-144">For performance, ensure that these resources are located in the same Azure region.</span></span>

1. <span data-ttu-id="631e2-145">Melden Sie sich in Ihrem Browser beim [**Azure-Portal**][azure-portal]an.</span><span class="sxs-lookup"><span data-stu-id="631e2-145">In your browser, sign into the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="631e2-146">Wählen Sie im linken Navigationsbereich **Ressourcengruppen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-146">In the left navigation panel, select **Resource groups**.</span></span>
1. <span data-ttu-id="631e2-147">Wählen Sie in der oberen linken Ecke des angezeigten Fensters Tab **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="631e2-147">In the upper left of the displayed window, select **Add** tab to create a new resource group.</span></span> <span data-ttu-id="631e2-148">Sie werden aufgefordert, Folgendes bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="631e2-148">You'll be prompted to provide the following:</span></span>
    1. <span data-ttu-id="631e2-149">**Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="631e2-149">**Subscription**.</span></span> <span data-ttu-id="631e2-150">Verwenden Sie Ihr vorhandenes Abonnement.</span><span class="sxs-lookup"><span data-stu-id="631e2-150">Use your existing subscription.</span></span>
    1. <span data-ttu-id="631e2-151">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="631e2-151">**Resource group**.</span></span> <span data-ttu-id="631e2-152">Geben Sie den Namen für die Ressourcengruppe ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-152">Enter the name for the resource group.</span></span> <span data-ttu-id="631e2-153">Ein Beispiel könnte *TeamsResourceGroup*sein.</span><span class="sxs-lookup"><span data-stu-id="631e2-153">An example could be  *TeamsResourceGroup*.</span></span> <span data-ttu-id="631e2-154">Beachten Sie, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="631e2-154">Remember that the name must be unique.</span></span>
    1. <span data-ttu-id="631e2-155">Wählen Sie im Dropdownmenü **Region** die Option *West US*oder eine Region, die sich in der Nähe ihrer Anwendungen befindet.</span><span class="sxs-lookup"><span data-stu-id="631e2-155">From the **Region** drop-down menu, select *West US*, or a region close to your applications.</span></span>
    1. <span data-ttu-id="631e2-156">Klicken Sie auf die Schaltfläche **überprüfen und erstellen** .</span><span class="sxs-lookup"><span data-stu-id="631e2-156">Select the **Review and create** button.</span></span> <span data-ttu-id="631e2-157">Es sollte ein Banner angezeigt werden, das die *übergebene Validierung*liest.</span><span class="sxs-lookup"><span data-stu-id="631e2-157">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="631e2-158">Klicken Sie auf die Schaltfläche **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="631e2-158">Select the **Create** button.</span></span> <span data-ttu-id="631e2-159">Es kann einige Minuten dauern, bis die Ressourcengruppe erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="631e2-159">It may take a few minutes to create the resource group.</span></span>

> [!TIP]
> <span data-ttu-id="631e2-160">Wie bei den Ressourcen, die Sie später in diesem Lernprogramm erstellen, empfiehlt es sich, diese Ressourcengruppe für einfachen Zugriff an das Dashboard zu anheften.</span><span class="sxs-lookup"><span data-stu-id="631e2-160">As with the resources you'll create later in this tutorial, it's a good idea to pin this resource group to your dashboard for easy access.</span></span> <span data-ttu-id="631e2-161">Wenn Sie dies möchten, wählen Sie das Pin-Symbol & # 128204; in der oberen rechten Ecke des Dashboards.</span><span class="sxs-lookup"><span data-stu-id="631e2-161">If you'd like to do so, select the pin icon &#128204; in the upper right of the dashboard.</span></span>

## <a name="create-the-service-plan"></a><span data-ttu-id="631e2-162">Erstellen des Dienstplans</span><span class="sxs-lookup"><span data-stu-id="631e2-162">Create the service plan</span></span>

1. <span data-ttu-id="631e2-163">Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Ressource erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-163">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Create a resource**.</span></span>
1. <span data-ttu-id="631e2-164">Geben Sie im Suchfeld den Text *App-Dienst Plan*ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-164">In the search box, type *App Service Plan*.</span></span> <span data-ttu-id="631e2-165">Wählen Sie die **App-Service Plan** Karte in den Suchergebnissen aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-165">Select the **App Service Plan** card from the search results.</span></span>
1. <span data-ttu-id="631e2-166">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-166">Select **Create**.</span></span>
1. <span data-ttu-id="631e2-167">Sie werden aufgefordert, die folgenden Informationen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="631e2-167">You'll be asked to provide the following information:</span></span>
    1. <span data-ttu-id="631e2-168">**Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="631e2-168">**Subscription**.</span></span> <span data-ttu-id="631e2-169">Sie können ein vorhandenes Abonnement verwenden.</span><span class="sxs-lookup"><span data-stu-id="631e2-169">You can use an existing subscription.</span></span>
    1. <span data-ttu-id="631e2-170">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="631e2-170">**Resource Group**.</span></span> <span data-ttu-id="631e2-171">Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-171">Select the group you created earlier.</span></span>
    1. <span data-ttu-id="631e2-172">**Name**.</span><span class="sxs-lookup"><span data-stu-id="631e2-172">**Name**.</span></span> <span data-ttu-id="631e2-173">Geben Sie den Namen für den Service Plan ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-173">Enter the name for the service plan.</span></span> <span data-ttu-id="631e2-174">Ein Beispiel könnte *TeamsServicePlan*sein.</span><span class="sxs-lookup"><span data-stu-id="631e2-174">An example could be  *TeamsServicePlan*.</span></span> <span data-ttu-id="631e2-175">Beachten Sie, dass der Name innerhalb der Gruppe eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="631e2-175">Remember that the name must be unique, within the group.</span></span>
    1. <span data-ttu-id="631e2-176">**Betriebs System**.</span><span class="sxs-lookup"><span data-stu-id="631e2-176">**Operating System**.</span></span> <span data-ttu-id="631e2-177">Wählen Sie *Windows* oder Ihr entsprechendes Betriebssystem aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-177">Select *Windows* or your applicable OS.</span></span>
    1. <span data-ttu-id="631e2-178">**Region**.</span><span class="sxs-lookup"><span data-stu-id="631e2-178">**Region**.</span></span> <span data-ttu-id="631e2-179">Wählen Sie " *West US* " oder eine Region in der Nähe ihrer Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-179">Select *West US* or a region close to your applications.</span></span>
    1. <span data-ttu-id="631e2-180">**Preisstufe**.</span><span class="sxs-lookup"><span data-stu-id="631e2-180">**Pricing Tier**.</span></span> <span data-ttu-id="631e2-181">Stellen Sie sicher, dass *Standard S1* ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="631e2-181">Make sure that *Standard S1* is selected.</span></span> <span data-ttu-id="631e2-182">Dies sollte der Standardwert sein.</span><span class="sxs-lookup"><span data-stu-id="631e2-182">This should be the default value.</span></span>
    1. <span data-ttu-id="631e2-183">Klicken Sie auf die Schaltfläche **überprüfen und erstellen** .</span><span class="sxs-lookup"><span data-stu-id="631e2-183">Select the **Review and create** button.</span></span> <span data-ttu-id="631e2-184">Es sollte ein Banner angezeigt werden, das die *übergebene Validierung*liest.</span><span class="sxs-lookup"><span data-stu-id="631e2-184">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="631e2-185">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-185">Select **Create**.</span></span> <span data-ttu-id="631e2-186">Es kann einige Minuten dauern, bis Sie den App-Dienstplan erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-186">It may take a few minutes to create the app service plan.</span></span> <span data-ttu-id="631e2-187">Der Plan wird in der Ressourcengruppe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="631e2-187">The plan will be listed in the resource group.</span></span>

## <a name="create-the-bot-channels-registration"></a><span data-ttu-id="631e2-188">Erstellen der Registrierung für bot-Kanäle</span><span class="sxs-lookup"><span data-stu-id="631e2-188">Create the bot channels registration</span></span>

<span data-ttu-id="631e2-189">Die Registrierung von bot-Kanälen registriert Ihren Webdienst als bot mit dem bot-Framework, vorausgesetzt, Sie verfügen über eine Microsoft-App-ID und ein App-Kennwort (geheimer Client Schlüssel).</span><span class="sxs-lookup"><span data-stu-id="631e2-189">The bot channels registration registers your web service as a bot with the Bot Framework, provided you have a Microsoft App Id and App password (client secret).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="631e2-190">Sie müssen ihren bot nur registrieren, wenn er nicht in Azure gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-190">You only need to register your bot if it is not hosted in Azure.</span></span> <span data-ttu-id="631e2-191">Wenn Sie [einen bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0) über das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert.</span><span class="sxs-lookup"><span data-stu-id="631e2-191">If you [created a bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0) through the Azure portal then it is already registered with the service.</span></span> <span data-ttu-id="631e2-192">Wenn Sie Ihren bot über das [bot-Framework](https://dev.botframework.com/bots/new) oder [AppStudio](~/concepts/build-and-test/app-studio-overview.md) erstellt haben, ist Ihr bot nicht in Azure registriert.</span><span class="sxs-lookup"><span data-stu-id="631e2-192">If you created your bot through the [Bot Framework](https://dev.botframework.com/bots/new) or [AppStudio](~/concepts/build-and-test/app-studio-overview.md) your bot isn't registered in Azure.</span></span>

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

<span data-ttu-id="631e2-193">Nachdem Azure die Registrierungs Ressource erstellt hat, wird es in die Liste Ressourcengruppe aufgenommen.</span><span class="sxs-lookup"><span data-stu-id="631e2-193">After Azure has created the registration resource it will be included in the resource group list.</span></span>  

![App Channels-Registrierungsgruppe für bot](../../../assets/images/authentication/auth-bot-channels-registration-group.PNG)

> [!NOTE]
> <span data-ttu-id="631e2-195">Die Ressourcen zur Registrierung von bot-Kanälen zeigen die **globale** Region an, selbst wenn Sie West US ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-195">The Bot Channels Registration resource will show the **Global** region even if you selected West US.</span></span> <span data-ttu-id="631e2-196">Dies entspricht dem erwarteten Verhalten.</span><span class="sxs-lookup"><span data-stu-id="631e2-196">This is expected.</span></span>

<span data-ttu-id="631e2-197">Weitere Informationen finden Sie unter [Erstellen eines bot für Teams](../create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="631e2-197">For more information, see [Create a bot for Teams](../create-a-bot-for-teams.md).</span></span>

## <a name="create-the-identity-provider"></a><span data-ttu-id="631e2-198">Erstellen des Identitätsanbieters</span><span class="sxs-lookup"><span data-stu-id="631e2-198">Create the identity provider</span></span>

<span data-ttu-id="631e2-199">Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="631e2-199">You need an identity provider that can be used for authentication.</span></span>
<span data-ttu-id="631e2-200">In diesem Verfahren verwenden Sie einen Azure AD Anbieter; Außerdem können andere Azure Ad Unterstützte Identitätsanbieter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-200">In this procedure you'll use an Azure AD provider; other Azure AD supported identity providers can also be used.</span></span>

1. <span data-ttu-id="631e2-201">Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Azure Active Directory**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-201">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Azure Active Directory**.</span></span>
    > [!TIP]
    > <span data-ttu-id="631e2-202">Sie müssen diese Azure AD Ressource in einem Mandanten erstellen und registrieren, in dem Sie die Berechtigung zum Delegieren von von einer Anwendung angeforderten Berechtigungen erteilen können.</span><span class="sxs-lookup"><span data-stu-id="631e2-202">You'll need to create and register this Azure AD resource in a tenant in which you can consent to delegate permissions requested by an application.</span></span>
    > <span data-ttu-id="631e2-203">Anweisungen zum Erstellen eines Mandanten finden Sie unter [zugreifen auf das Portal und Erstellen eines Mandanten](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span><span class="sxs-lookup"><span data-stu-id="631e2-203">For instruction on creating a tenant, see [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span></span>
1. <span data-ttu-id="631e2-204">Wählen Sie im linken Bereich **App-Registrierungen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-204">In the left panel, select **App registrations**.</span></span>
1. <span data-ttu-id="631e2-205">Wählen Sie im rechten Bereich die Registerkarte **neue Registrierung** in der oberen linken Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-205">In the right panel, select the **New registration** tab, in the upper left.</span></span>
1. <span data-ttu-id="631e2-206">Sie werden aufgefordert, die folgenden Informationen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="631e2-206">You'll be asked to provide the following information:</span></span>
   1. <span data-ttu-id="631e2-207">**Name**.</span><span class="sxs-lookup"><span data-stu-id="631e2-207">**Name**.</span></span> <span data-ttu-id="631e2-208">Geben Sie den Namen der Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-208">Enter the name for the application.</span></span> <span data-ttu-id="631e2-209">Ein Beispiel könnte *BotTeamsIdentity*sein.</span><span class="sxs-lookup"><span data-stu-id="631e2-209">An example could be  *BotTeamsIdentity*.</span></span> <span data-ttu-id="631e2-210">Beachten Sie, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="631e2-210">Remember that the name must be unique.</span></span>
   1. <span data-ttu-id="631e2-211">Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-211">Select the **Supported account types** for your application.</span></span> <span data-ttu-id="631e2-212">Wählen Sie *Konten in einem beliebigen Organisations Verzeichnis (beliebige Azure AD Verzeichnis – Multimandanten) und persönliche Microsoft-Konten (beispielsweise Skype, Xbox)* aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-212">Select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
   1. <span data-ttu-id="631e2-213">Für den **Umleitungs-URI**:</span><span class="sxs-lookup"><span data-stu-id="631e2-213">For the **Redirect URI**:</span></span><br/>
       <span data-ttu-id="631e2-214">&#x2713;wählen Sie das **Webpart**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-214">&#x2713;Select **Web**.</span></span> <br/>
       <span data-ttu-id="631e2-215">&#x2713; legen Sie die URL `https://token.botframework.com/.auth/web/redirect`auf fest.</span><span class="sxs-lookup"><span data-stu-id="631e2-215">&#x2713; Set the URL to `https://token.botframework.com/.auth/web/redirect`.</span></span>
   1. <span data-ttu-id="631e2-216">Wählen Sie **Registrieren** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-216">Select **Register**.</span></span>

1. <span data-ttu-id="631e2-217">Nach der Erstellung zeigt Azure die Übersichts **Seite für die APP** an.</span><span class="sxs-lookup"><span data-stu-id="631e2-217">Once it is created, Azure displays the **Overview** page for the app.</span></span> <span data-ttu-id="631e2-218">Kopieren Sie die folgenden Informationen, und speichern Sie Sie in einer Datei:</span><span class="sxs-lookup"><span data-stu-id="631e2-218">Copy and save the following information to a file:</span></span>

    1. <span data-ttu-id="631e2-219">Der Wert der **Anwendungs-ID (Client)** .</span><span class="sxs-lookup"><span data-stu-id="631e2-219">The **Application (client) ID** value.</span></span> <span data-ttu-id="631e2-220">Sie verwenden diesen Wert später als *Client-ID* , wenn Sie diese Azure-Identitäts Anwendung mit Ihrem bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-220">You'll use this value later as the *Client ID* when you register this Azure identity application with your bot.</span></span>
    1. <span data-ttu-id="631e2-221">Der **Verzeichnis Wert (Mandant) ID** .</span><span class="sxs-lookup"><span data-stu-id="631e2-221">The **Directory (tenant) ID** value.</span></span> <span data-ttu-id="631e2-222">Sie werden diesen Wert auch später als *Mandanten-ID* verwenden, um diese Azure-Identitäts Anwendung mit Ihrem bot zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-222">You'll also use this value later as the *Tenant ID* to register this Azure identity application with your bot.</span></span>

1. <span data-ttu-id="631e2-223">Wählen Sie im linken Bereich **Zertifikate & Secrets** aus, um einen geheimen Client Schlüssel für Ihre Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="631e2-223">In the left panel, select **Certificates & secrets** to create a client secret for your application.</span></span>

   1. <span data-ttu-id="631e2-224">Wählen Sie unter **Client Secrets**&#x2795; **neuen geheimen Client Schlüssel**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-224">Under **Client secrets**, select &#x2795; **New client secret**.</span></span>
   1. <span data-ttu-id="631e2-225">Fügen Sie eine Beschreibung hinzu, um dieses Geheimnis von anderen Personen zu identifizieren, die Sie für diese APP möglicherweise erstellen müssen, beispielsweise für die *app "bot Identity" in Microsoft Teams*.</span><span class="sxs-lookup"><span data-stu-id="631e2-225">Add a description to identify this secret from others you might need to create for this app, such as *Bot identity app in Teams*.</span></span>
   1. <span data-ttu-id="631e2-226">Festlegen **läuft** auf Ihre Auswahl ab.</span><span class="sxs-lookup"><span data-stu-id="631e2-226">Set **Expires** to your selection.</span></span>
   1. <span data-ttu-id="631e2-227">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="631e2-227">Select **Add**.</span></span>
   1. <span data-ttu-id="631e2-228">**Notieren Sie den geheimen Schlüssel**, bevor Sie diese Seite verlassen.</span><span class="sxs-lookup"><span data-stu-id="631e2-228">Before leaving this page, **record the secret**.</span></span> <span data-ttu-id="631e2-229">Diesen Wert verwenden Sie später als _geheimer Client Schlüssel_ , wenn Sie Ihre Azure AD Anwendung mit Ihrem bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-229">You'll use this value later as the _Client secret_ when you register your Azure AD application with your bot.</span></span>

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a><span data-ttu-id="631e2-230">Konfigurieren Sie die Verbindung mit dem Identitätsanbieter, und registrieren Sie Sie mit dem bot.</span><span class="sxs-lookup"><span data-stu-id="631e2-230">Configure the identity provider connection and register it with the bot</span></span>

1. <span data-ttu-id="631e2-231">Wählen Sie im [**Azure-Portal**][azure-portal]ihre Ressourcengruppe aus dem Dashboard aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-231">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="631e2-232">Wählen Sie Ihren bot-Kanal Registrierungslink aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-232">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="631e2-233">Wählen Sie auf der Seite Ressource die Option **Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-233">On the resource page, select **Settings**.</span></span>
1. <span data-ttu-id="631e2-234">Wählen Sie unter **OAuth-Verbindungseinstellungen** am unteren Rand der Seite die Option **Einstellung hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-234">Under **OAuth Connection Settings** near the bottom of the page, select **Add Setting**.</span></span>
1. <span data-ttu-id="631e2-235">Füllen Sie das Formular wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="631e2-235">Complete the form as follows:</span></span>

    1. <span data-ttu-id="631e2-236">**Name**.</span><span class="sxs-lookup"><span data-stu-id="631e2-236">**Name**.</span></span> <span data-ttu-id="631e2-237">Geben Sie einen Namen für die Verbindung ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-237">Enter a name for the connection.</span></span> <span data-ttu-id="631e2-238">Sie verwenden diesen Namen in Ihrem bot in der `appsettings.json` Datei.</span><span class="sxs-lookup"><span data-stu-id="631e2-238">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="631e2-239">Beispiel *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="631e2-239">For example *BotTeamsAuthADv1*.</span></span>
    1. <span data-ttu-id="631e2-240">**Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="631e2-240">**Service Provider**.</span></span> <span data-ttu-id="631e2-241">Wählen Sie **Azure Active Directory** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-241">Select **Azure Active Directory**.</span></span> <span data-ttu-id="631e2-242">Nachdem Sie diese Option ausgewählt haben, werden die Azure AD spezifischen Felder angezeigt.</span><span class="sxs-lookup"><span data-stu-id="631e2-242">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="631e2-243">**Client-ID**. Geben Sie die Anwendungs-ID (Client) ein, die Sie in den obigen Schritten für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-243">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="631e2-244">**Geheimer Client Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="631e2-244">**Client secret**.</span></span> <span data-ttu-id="631e2-245">Geben Sie den geheimen Schlüssel ein, den Sie in den obigen Schritten für Ihre Azure Identity-Anbieter-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-245">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="631e2-246">**Grant-Typ**.</span><span class="sxs-lookup"><span data-stu-id="631e2-246">**Grant Type**.</span></span> <span data-ttu-id="631e2-247">Geben `authorization_code`Sie ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-247">Enter `authorization_code`.</span></span>
    1. <span data-ttu-id="631e2-248">**Anmelde-URL**.</span><span class="sxs-lookup"><span data-stu-id="631e2-248">**Login URL**.</span></span> <span data-ttu-id="631e2-249">Geben `https://login.microsoftonline.com`Sie ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-249">Enter `https://login.microsoftonline.com`.</span></span>
    1. <span data-ttu-id="631e2-250">**Mandanten-ID**: Geben Sie die **Verzeichnis (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure Identity-App aufgezeichnet haben, oder **verbreitet** , je nach dem unterstützten Kontotyp, der beim Erstellen der APP für den Identitätsanbieter ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="631e2-250">**Tenant ID**, enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="631e2-251">Um zu entscheiden, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="631e2-251">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="631e2-252">Wenn Sie entweder *Konten in diesem Organisations Verzeichnis (nur Microsoft – einzelner Mandant)* oder *Konten in einem Organisations Verzeichnis (Microsoft Aad Directory-Multi Mandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die Aad-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-252">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="631e2-253">Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="631e2-253">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="631e2-254">Wenn Sie *Konten in einem beliebigen Organisations Verzeichnis (AAD Directory-Multi Mandanten und persönliche Microsoft-Konten wie Skype, Xbox, Outlook)* ausgewählt haben, geben Sie das Wort " **Common** " anstelle einer Mandanten-ID ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-254">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="631e2-255">Andernfalls wird die Aad-App über den Mandanten überprüfen, dessen ID ausgewählt wurde, und persönliche Microsoft-Konten ausschließen.</span><span class="sxs-lookup"><span data-stu-id="631e2-255">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    <span data-ttu-id="631e2-256">h.</span><span class="sxs-lookup"><span data-stu-id="631e2-256">h.</span></span> <span data-ttu-id="631e2-257">Geben Sie für **Ressourcen**- `https://graph.microsoft.com/`URL den Eintrag ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-257">For **Resource URL**, enter `https://graph.microsoft.com/`.</span></span> <span data-ttu-id="631e2-258">Dies wird im aktuellen Codebeispiel nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="631e2-258">This is not used in the current code sample.</span></span>  
    <span data-ttu-id="631e2-259">Ich.</span><span class="sxs-lookup"><span data-stu-id="631e2-259">i.</span></span> <span data-ttu-id="631e2-260">Lassen Sie **Bereiche** leer.</span><span class="sxs-lookup"><span data-stu-id="631e2-260">Leave **Scopes** blank.</span></span> <span data-ttu-id="631e2-261">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-261">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. <span data-ttu-id="631e2-263">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="631e2-263">Select **Save**.</span></span>

### <a name="test-the-connection"></a><span data-ttu-id="631e2-264">Testen der Verbindung</span><span class="sxs-lookup"><span data-stu-id="631e2-264">Test the connection</span></span>

1. <span data-ttu-id="631e2-265">Wählen Sie den Eintrag Connection aus, um die soeben erstellte Verbindung zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="631e2-265">Select the connection entry to open the connection you just created.</span></span>
1. <span data-ttu-id="631e2-266">Wählen Sie oben im Bereich **Service Provider Connection Setting** die Option **Test connection** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-266">Select **Test Connection** at the top of the **Service Provider Connection Setting** panel.</span></span>
1. <span data-ttu-id="631e2-267">Wenn Sie das erste Mal durchführen, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="631e2-267">The first time you do this will open a new browser window asking you to select an account.</span></span> <span data-ttu-id="631e2-268">Wählen Sie diejenige aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="631e2-268">Select the one you want to use.</span></span>
1. <span data-ttu-id="631e2-269">Als nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu gestatten.</span><span class="sxs-lookup"><span data-stu-id="631e2-269">Next, you'll be asked to allow to the identity provider to use your data (credentials).</span></span> <span data-ttu-id="631e2-270">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-270">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. <span data-ttu-id="631e2-272">Wählen Sie **Annehmen** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-272">Select **Accept**.</span></span>
1. <span data-ttu-id="631e2-273">Anschließend sollten Sie zu einer **Test Verbindung zu \<Ihrer-Connection-Name> erfolgreich gefolgten** Seite umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-273">This should then redirect you to a **Test Connection to \<your-connection-name> Succeeded** page.</span></span> <span data-ttu-id="631e2-274">Aktualisieren Sie die Seite, wenn Sie eine Fehlermeldung erhalten.</span><span class="sxs-lookup"><span data-stu-id="631e2-274">Refresh the page if you get an error.</span></span> <span data-ttu-id="631e2-275">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-275">The following image is an example:</span></span>

  ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

<span data-ttu-id="631e2-277">Der Verbindungsname wird vom bot-Code zum Abrufen von Benutzerauthentifizierungstoken verwendet.</span><span class="sxs-lookup"><span data-stu-id="631e2-277">The connection name is used by the bot code to retrieve user authentication tokens.</span></span>

## <a name="prepare-the-bot-sample-code"></a><span data-ttu-id="631e2-278">Vorbereiten des bot-Beispielcodes</span><span class="sxs-lookup"><span data-stu-id="631e2-278">Prepare the bot sample code</span></span>

<span data-ttu-id="631e2-279">Nachdem die vorläufigen Einstellungen vorgenommen wurden, konzentrieren wir uns auf die Erstellung des bot, der in diesem Artikel verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="631e2-279">With the preliminary settings done, let's focus on the creation of the bot to use in this article.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="631e2-280">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="631e2-280">C#/.NET</span></span>](#tab/dotnet)

1. <span data-ttu-id="631e2-281">Klon [CS-auth-Sample][teams-auth-bot-cs].</span><span class="sxs-lookup"><span data-stu-id="631e2-281">Clone [cs-auth-sample][teams-auth-bot-cs].</span></span>
1. <span data-ttu-id="631e2-282">Starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="631e2-282">Launch Visual Studio.</span></span>
1. <span data-ttu-id="631e2-283">Wählen Sie in der Symbolleiste **Datei-> Open-> Projekt/Lösung** aus, und öffnen Sie das bot-Projekt.</span><span class="sxs-lookup"><span data-stu-id="631e2-283">From the toolbar select **File -> Open -> Project/Solution** and open the bot project.</span></span>
1. <span data-ttu-id="631e2-284">In C# Update **appSettings. JSON** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="631e2-284">In C# Update **appsettings.json** as follows:</span></span>

    - <span data-ttu-id="631e2-285">Legen `ConnectionName` Sie den Namen der Identitätsanbieter Verbindung fest, die Sie der bot-Kanal Registrierung hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-285">Set `ConnectionName` to the name of the identity provider connection you added to the bot channel registration.</span></span> <span data-ttu-id="631e2-286">Der Name, den wir in diesem Beispiel verwendet haben, ist *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="631e2-286">The name we used in this example is *BotTeamsAuthADv1*.</span></span>
    - <span data-ttu-id="631e2-287">Legen `MicrosoftAppId` Sie die **bot-APP-ID** fest, die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-287">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="631e2-288">Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-288">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="631e2-289">Legen Sie `ConnectionName` den auf den Namen der Identitätsanbieter Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="631e2-289">Set the `ConnectionName` to the name of the identity provider connection.</span></span>

    <span data-ttu-id="631e2-290">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="631e2-290">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="631e2-291">Beispielsweise müssen alle kaufmännischen und-Zeichen (&) als `&amp;`codiert werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-291">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. <span data-ttu-id="631e2-292">Navigieren Sie im Projektmappen-Explorer `TeamsAppManifest` zum Ordner öffnen `manifest.json` und festlegen `id` sowie `botId` zur **bot-APP-ID** , die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-292">In the Solution Explorer, navigate to the `TeamsAppManifest` folder, open `manifest.json` and set `id` and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="javascript"></a>[<span data-ttu-id="631e2-293">JavaScript</span><span class="sxs-lookup"><span data-stu-id="631e2-293">JavaScript</span></span>](#tab/node-js)

1. <span data-ttu-id="631e2-294">Clone [Node-auth-Sample][teams-auth-bot-js].</span><span class="sxs-lookup"><span data-stu-id="631e2-294">Clone [node-auth-sample][teams-auth-bot-js].</span></span>
1. <span data-ttu-id="631e2-295">Navigieren Sie in einer Konsole zum Projekt:</span><span class="sxs-lookup"><span data-stu-id="631e2-295">In a console, navigate to the project:</span></span> </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. <span data-ttu-id="631e2-296">Installieren von Modulen</span><span class="sxs-lookup"><span data-stu-id="631e2-296">Install modules</span></span></br></br>
`npm install`
1. <span data-ttu-id="631e2-297">Aktualisieren Sie die **. env-** Konfiguration wie folgt:</span><span class="sxs-lookup"><span data-stu-id="631e2-297">Update the **.env** configuration as follows:</span></span>

    - <span data-ttu-id="631e2-298">Legen `MicrosoftAppId` Sie die **bot-APP-ID** fest, die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-298">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="631e2-299">Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-299">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="631e2-300">Legen Sie `connectionName` den auf den Namen der Identitätsanbieter Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="631e2-300">Set the `connectionName` to the name of the identity provider connection.</span></span>

    <span data-ttu-id="631e2-301">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="631e2-301">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="631e2-302">Beispielsweise müssen alle kaufmännischen und-Zeichen (&) als `&amp;`codiert werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-302">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. <span data-ttu-id="631e2-303">Öffnen `teamsAppManifest` `manifest.json` Sie in dem Ordner Ihre Microsoft `id` - **App-ID** und `botId` die **bot-APP-ID** , die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben, und legen Sie diese fest.</span><span class="sxs-lookup"><span data-stu-id="631e2-303">In the `teamsAppManifest` folder, open `manifest.json` and set `id`  to your **Microsoft App ID** and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="python"></a>[<span data-ttu-id="631e2-304">Python</span><span class="sxs-lookup"><span data-stu-id="631e2-304">Python</span></span>](#tab/python)

1. <span data-ttu-id="631e2-305">Clone [py-auth-Sample][teams-auth-bot-py] aus dem GitHub-Repository.</span><span class="sxs-lookup"><span data-stu-id="631e2-305">Clone [py-auth-sample][teams-auth-bot-py] from the github repository.</span></span>
1. <span data-ttu-id="631e2-306">**Config.py**aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="631e2-306">Update **config.py**:</span></span>

    - <span data-ttu-id="631e2-307">Legen `ConnectionName` Sie den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem bot hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-307">Set `ConnectionName` to the name of the OAuth connection setting you added to your bot.</span></span>
    - <span data-ttu-id="631e2-308">Legen Sie die APP-ID und den App-Schlüssel Ihres bot fest `MicrosoftAppId` `MicrosoftAppPassword`</span><span class="sxs-lookup"><span data-stu-id="631e2-308">Set `MicrosoftAppId` and `MicrosoftAppPassword` to your bot's app ID and app secret.</span></span>

      <span data-ttu-id="631e2-309">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="631e2-309">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="631e2-310">Beispielsweise müssen alle kaufmännischen und-Zeichen (&) als `&amp;`codiert werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-310">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a><span data-ttu-id="631e2-311">Bereitstellen des bot in Azure</span><span class="sxs-lookup"><span data-stu-id="631e2-311">Deploy the bot to Azure</span></span>

<span data-ttu-id="631e2-312">Um den bot bereitzustellen, befolgen Sie die Schritte unter How to [deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span><span class="sxs-lookup"><span data-stu-id="631e2-312">To deploy the bot, follow the steps in the how to [Deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span></span>

<span data-ttu-id="631e2-313">Alternativ können Sie in Visual Studio die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="631e2-313">Alternatively, while in Visual Studio, you can follow these steps:</span></span>

1. <span data-ttu-id="631e2-314">Wählen Sie im Visual Studio Projekt *Mappen-Explorer* den Projektnamen aus, und halten Sie ihn (oder klicken Sie mit der rechten Maustaste).</span><span class="sxs-lookup"><span data-stu-id="631e2-314">In Visual Studio *Solution Explorer* select and hold (or right-click) the project name.</span></span>
1. <span data-ttu-id="631e2-315">Wählen Sie im Dropdownmenü die Option **veröffentlichen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-315">In the drop-down menu, select **Publish**.</span></span>
1. <span data-ttu-id="631e2-316">Wählen Sie im angezeigten Fenster den **neuen** Link aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-316">In the displayed window, select the **New** link.</span></span>
1. <span data-ttu-id="631e2-317">Wählen Sie im Dialogfeld **App-Dienst** auf der linken Seite aus, und **Erstellen Sie neu** auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="631e2-317">In the dialog window, select **App Service** on the left and **Create New** on the right.</span></span>
1. <span data-ttu-id="631e2-318">Klicken Sie auf die Schaltfläche **veröffentlichen** .</span><span class="sxs-lookup"><span data-stu-id="631e2-318">Select the **Publish** button.</span></span>
1. <span data-ttu-id="631e2-319">Geben Sie im nächsten Dialogfenster die erforderlichen Informationen ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-319">In the next dialog window, enter the required information.</span></span> <span data-ttu-id="631e2-320">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-320">The following is an example:</span></span>

   ![auth-App-Service](../../../assets/images/authentication/auth-bot-app-service.png)

1. <span data-ttu-id="631e2-322">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-322">Select **Create**.</span></span>
1. <span data-ttu-id="631e2-323">Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte Sie in Visual Studio angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-323">If the deployment completes successfully, you should see it reflected in Visual Studio.</span></span> <span data-ttu-id="631e2-324">Darüber hinaus wird in Ihrem Standardbrowser eine Seite angezeigt, die besagt, dass *Ihr bot Ready!*.</span><span class="sxs-lookup"><span data-stu-id="631e2-324">Moreover, a page is displayed in your default browser saying *Your bot is ready!*.</span></span> <span data-ttu-id="631e2-325">Die URL wird wie folgt aussehen: `https://botteamsauth.azurewebsites.net/`.</span><span class="sxs-lookup"><span data-stu-id="631e2-325">The URL will be similar to this: `https://botteamsauth.azurewebsites.net/`.</span></span> <span data-ttu-id="631e2-326">Speichern Sie Sie in einer Datei.</span><span class="sxs-lookup"><span data-stu-id="631e2-326">Save it to a file.</span></span>
1. <span data-ttu-id="631e2-327">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="631e2-327">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="631e2-328">Überprüfen Sie Ihre Ressourcengruppe, der bot sollte zusammen mit den anderen Ressourcen aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-328">Check your resource group, the bot should be listed along with the other resources.</span></span> <span data-ttu-id="631e2-329">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-329">The following image is an example:</span></span>

    ![Teams-bot-auth-App-Service-Gruppe](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. <span data-ttu-id="631e2-331">Wählen Sie in der Gruppe Ressourcen den Namen des bot-Kanal Registrierungs namens (Link) aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-331">In the resource group, select the bot channel registration name (link).</span></span>
1. <span data-ttu-id="631e2-332">Wählen Sie im linken Bereich **Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-332">In the left panel, select **Settings**.</span></span>
1. <span data-ttu-id="631e2-333">Geben Sie im Feld **Messaging-Endpunkt** die oben abgerufene URL ein, `api/messages`gefolgt von.</span><span class="sxs-lookup"><span data-stu-id="631e2-333">In the **Messaging endpoint** box, enter the URL obtained above followed by `api/messages`.</span></span> <span data-ttu-id="631e2-334">Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="631e2-334">This is an example: `https://botteamsauth.azurewebsites.net/api/messages`.</span></span>
1. <span data-ttu-id="631e2-335">Klicken Sie oben links auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="631e2-335">Select the **Save** button in the upper left.</span></span>

## <a name="test-the-bot-using-the-emulator"></a><span data-ttu-id="631e2-336">Testen des bot mit dem Emulator</span><span class="sxs-lookup"><span data-stu-id="631e2-336">Test the bot using the Emulator</span></span>

<span data-ttu-id="631e2-337">Wenn Sie es nicht bereits getan haben, installieren Sie den [Microsoft bot Framework-Emulator](https://aka.ms/bot-framework-emulator-readme).</span><span class="sxs-lookup"><span data-stu-id="631e2-337">If you haven't done it already, install the [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme).</span></span> <span data-ttu-id="631e2-338">Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span><span class="sxs-lookup"><span data-stu-id="631e2-338">See also [Debug with the Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span></span>

<span data-ttu-id="631e2-339">Damit die bot-Beispiel Anmeldung funktioniert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-339">In order for the bot sample login to work you must configure the Emulator as shown below.</span></span>

### <a name="configure-the-emulator-for-authentication"></a><span data-ttu-id="631e2-340">Konfigurieren des Emulators für die Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="631e2-340">Configure the Emulator for authentication</span></span>

<span data-ttu-id="631e2-341">Wenn ein bot eine Authentifizierung erfordert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-341">If a bot requires authentication, you must configure the Emulator as shown below.</span></span>

1. <span data-ttu-id="631e2-342">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="631e2-342">Start the Emulator.</span></span>
1. <span data-ttu-id="631e2-343">Wählen Sie im Emulator das Zahnradsymbol &#9881; unten links oder die Registerkarte **Emulatoreinstellungen** in der oberen rechten Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-343">In the Emulator, select the gear icon &#9881; in the bottom left, or the **Emulator Settings** tab in the upper right.</span></span>
1. <span data-ttu-id="631e2-344">Aktivieren Sie das Kontrollkästchen mit der **Version 1,0-Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="631e2-344">Check the box by **Use version 1.0 authentication tokens**.</span></span>
1. <span data-ttu-id="631e2-345">Geben Sie den lokalen Pfad zum **ngrok** -Tool ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-345">Enter the local path to the **ngrok** tool.</span></span> <span data-ttu-id="631e2-346">*Siehe* bot Framework Emulator/ngrok Tunneling Integration [wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span><span class="sxs-lookup"><span data-stu-id="631e2-346">*See* the Bot Framework Emulator / ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span></span> <span data-ttu-id="631e2-347">Weitere Informationen zum Tool finden Sie unter [ngrok](https://ngrok.com/).</span><span class="sxs-lookup"><span data-stu-id="631e2-347">For more tool information, see [ngrok](https://ngrok.com/).</span></span>
1. <span data-ttu-id="631e2-348">Aktivieren Sie das Kontrollkästchen **ngrok ausführen, wenn der Emulator gestartet wird**.</span><span class="sxs-lookup"><span data-stu-id="631e2-348">Check the box by **Run ngrok when the Emulator starts up**.</span></span>
1. <span data-ttu-id="631e2-349">Klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="631e2-349">Select the **Save** button.</span></span>

<span data-ttu-id="631e2-350">Wenn der bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, die der Benutzer zum Anmelden mit dem Authentifizierungsanbieter verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="631e2-350">When the bot displays a sign-in card and the user selects the sign-in button, the Emulator opens a page that the user can use to sign in with the authentication provider.</span></span>
<span data-ttu-id="631e2-351">Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den bot.</span><span class="sxs-lookup"><span data-stu-id="631e2-351">Once the user does so, the provider generates a user token and sends it to the bot.</span></span> <span data-ttu-id="631e2-352">Danach kann der bot im Namen des Benutzers handeln.</span><span class="sxs-lookup"><span data-stu-id="631e2-352">After that, the bot can act on behalf of the user.</span></span>

### <a name="test-the-bot-locally"></a><span data-ttu-id="631e2-353">Testen des bot lokal</span><span class="sxs-lookup"><span data-stu-id="631e2-353">Test the bot locally</span></span>

<span data-ttu-id="631e2-354">Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die eigentlichen bot-Tests durchführen.</span><span class="sxs-lookup"><span data-stu-id="631e2-354">After you have configured the authentication mechanism, you can perform the actual bot testing.</span></span>  

1. <span data-ttu-id="631e2-355">Führen Sie das bot-Beispiel lokal auf Ihrem Computer aus, beispielsweise über Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="631e2-355">Run the bot sample locally on your machine, via Visual Studio for example.</span></span>
1. <span data-ttu-id="631e2-356">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="631e2-356">Start the Emulator.</span></span>
1. <span data-ttu-id="631e2-357">Klicken Sie auf die Schaltfläche **bot öffnen** .</span><span class="sxs-lookup"><span data-stu-id="631e2-357">Select the **Open bot** button.</span></span>
1. <span data-ttu-id="631e2-358">Geben Sie in der **bot-URL**die lokale URL des bot ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-358">In the **Bot URL**, enter the bot's local URL.</span></span> <span data-ttu-id="631e2-359">Normalerweise `http://localhost:3978/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="631e2-359">Usually, `http://localhost:3978/api/messages`.</span></span>
1. <span data-ttu-id="631e2-360">Geben Sie in der **Microsoft App-ID** die APP-ID `appsettings.json`des bot von ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-360">In the **Microsoft App ID** enter the bot's app ID from `appsettings.json`.</span></span>
1. <span data-ttu-id="631e2-361">Geben Sie im **Microsoft App-Kennwort** das App-Kennwort des bot `appsettings.json`aus dem ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-361">In the **Microsoft App password** enter the bot's app password from the `appsettings.json`.</span></span>
1. <span data-ttu-id="631e2-362">Wählen Sie **verbinden**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-362">Select **Connect**.</span></span>
1. <span data-ttu-id="631e2-363">Geben Sie nach dem Starten des bot einen beliebigen Text ein, um die Anmeldekarte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="631e2-363">After the bot is up and running, enter any text to display the sign-in card.</span></span>
1. <span data-ttu-id="631e2-364">Wählen Sie die Schaltfläche **Anmelden** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-364">Select the **Sign in** button.</span></span>
1. <span data-ttu-id="631e2-365">Ein Popupdialogfeld wird angezeigt, um die **geöffnete URL zu bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="631e2-365">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="631e2-366">Dadurch kann der Benutzer des bot (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-366">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="631e2-367">Wählen Sie **bestätigen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-367">Select **Confirm**.</span></span>
1. <span data-ttu-id="631e2-368">Wenn Sie dazu aufgefordert werden, wählen Sie das entsprechende Benutzerkonto aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-368">If asked, select the applicable user's account.</span></span>
1. <span data-ttu-id="631e2-369">Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="631e2-369">Depending which configuration you used for the Emulator, you get one of the following:</span></span>
    1. <span data-ttu-id="631e2-370">**Verwenden des Anmelde Bestätigungscodes**</span><span class="sxs-lookup"><span data-stu-id="631e2-370">**Using sign-in verification code**</span></span>  
      <span data-ttu-id="631e2-371">&#x2713; ein Fenster wird geöffnet, in dem der Validierungscode angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-371">&#x2713; A window is opened displaying the validation code.</span></span>  
      <span data-ttu-id="631e2-372">&#x2713; kopieren Sie den Validierungscode, und geben Sie ihn in das Feld Chat ein, um die Anmeldung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="631e2-372">&#x2713; Copy and enter the validation code into the chat box to complete the sign-in.</span></span>
    1. <span data-ttu-id="631e2-373">**Verwenden von Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="631e2-373">**Using authentication tokens**.</span></span>  
      <span data-ttu-id="631e2-374">&#x2713; Sie auf der Grundlage ihrer Anmeldeinformationen angemeldet sind.</span><span class="sxs-lookup"><span data-stu-id="631e2-374">&#x2713; You're logged in based on your credentials.</span></span>

    <span data-ttu-id="631e2-375">Die folgende Abbildung ist ein Beispiel für die bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="631e2-375">The following image is an example of the bot UI after you've logged in:</span></span>

    ![Authentifizierungs-bot-Anmelde Emulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. <span data-ttu-id="631e2-377">Wenn Sie " **Ja** " auswählen, wenn der bot *möchte, dass Ihr Token angezeigt*wird, erhalten Sie eine ähnliche Antwort wie die folgende:</span><span class="sxs-lookup"><span data-stu-id="631e2-377">If you select **Yes** when the bot asks *Would you like to view your token?*, you'll get a response similar to the following:</span></span>

    ![Authentifizierungs-bot-Anmelde Emulator-Token](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. <span data-ttu-id="631e2-379">Geben Sie **Logout** in das Feld Eingabe Chat ein, um sich abzumelden. Dadurch wird das Benutzertoken freigegeben, und der Bot kann nicht in Ihrem Namen handeln, bis Sie sich erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-379">Enter **logout** in the input chat box to sign out. This releases the user token, and the bot won't be able to act on your behalf until you sign in again.</span></span>

> [!NOTE]
> <span data-ttu-id="631e2-380">Für die bot-Authentifizierung ist die Verwendung des **bot Connector-Diensts**erforderlich.</span><span class="sxs-lookup"><span data-stu-id="631e2-380">Bot authentication requires use of the **Bot Connector Service**.</span></span> <span data-ttu-id="631e2-381">Der Dienst greift auf die Registrierungsinformationen für bot-Kanäle für Ihren bot zu.</span><span class="sxs-lookup"><span data-stu-id="631e2-381">The service accesses the bot channels registration information for your bot.</span></span>

## <a name="test-the-deployed-bot"></a><span data-ttu-id="631e2-382">Testen des bereitgestellten bot</span><span class="sxs-lookup"><span data-stu-id="631e2-382">Test the deployed bot</span></span>

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. <span data-ttu-id="631e2-383">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="631e2-383">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="631e2-384">Suchen Sie Ihre Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="631e2-384">Find your resource group.</span></span>
1. <span data-ttu-id="631e2-385">Wählen Sie den Link Ressource aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-385">Select the resource link.</span></span> <span data-ttu-id="631e2-386">Die Seite Ressource wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="631e2-386">The resource page is displayed.</span></span>
1. <span data-ttu-id="631e2-387">Wählen Sie auf der Seite Ressource die Option **Test im Webchat**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-387">In the resource page, select **Test in Web Chat**.</span></span> <span data-ttu-id="631e2-388">Der bot startet und zeigt die vordefinierten Begrüßungen an.</span><span class="sxs-lookup"><span data-stu-id="631e2-388">The bot starts and displays the predefined greetings.</span></span>
1. <span data-ttu-id="631e2-389">Geben Sie im Feld Chat eine beliebige Eingabe ein.</span><span class="sxs-lookup"><span data-stu-id="631e2-389">Type anything in the chat box.</span></span>
1. <span data-ttu-id="631e2-390">Aktivieren Sie das Kontrollkästchen **Anmelden** .</span><span class="sxs-lookup"><span data-stu-id="631e2-390">Select the **Sign in** box.</span></span>
1. <span data-ttu-id="631e2-391">Ein Popupdialogfeld wird angezeigt, um die **geöffnete URL zu bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="631e2-391">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="631e2-392">Dadurch kann der Benutzer des bot (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-392">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="631e2-393">Wählen Sie **bestätigen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-393">Select **Confirm**.</span></span>
1. <span data-ttu-id="631e2-394">Wenn Sie dazu aufgefordert werden, wählen Sie das entsprechende Benutzerkonto aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-394">If asked, select the applicable user's account.</span></span>
    <span data-ttu-id="631e2-395">Die folgende Abbildung ist ein Beispiel für die bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="631e2-395">The following image is an example of the bot UI after you have logged in:</span></span>

    ![bereitgestellte Authentifizierungs-bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed.PNG)<span data-ttu-id="631e2-397">.</span><span class="sxs-lookup"><span data-stu-id="631e2-397">.</span></span>

1. <span data-ttu-id="631e2-398">Wählen Sie die Schaltfläche **Ja** aus, um das Authentifizierungstoken anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="631e2-398">Select the **Yes** button to display your authentication token.</span></span> <span data-ttu-id="631e2-399">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-399">The following image is an example:</span></span>

    ![bereitgestelltes Token für auth-bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG)<span data-ttu-id="631e2-401">.</span><span class="sxs-lookup"><span data-stu-id="631e2-401">.</span></span>

1. <span data-ttu-id="631e2-402">Geben Sie Logout ein, um sich abzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-402">Enter logout to sign out.</span></span>

    ![Authentifizierungs-bot bereitgestellt Logout](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> <span data-ttu-id="631e2-404">Wenn Sie bei der Anmeldung Probleme haben, versuchen Sie, die Verbindung erneut zu testen, wie in den vorherigen Schritten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="631e2-404">If you're having problems signing in, try to test the connection again as described in the previous steps.</span></span> <span data-ttu-id="631e2-405">Dadurch könnte das Authentifizierungstoken neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-405">This could recreate the authentication token.</span></span>
> <span data-ttu-id="631e2-406">Mit dem bot-Framework-Webchat Client in Azure müssen Sie sich möglicherweise mehrere Male anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="631e2-406">With the Bot Framework Web Chat client in Azure, you may need to sign in several times before the authentication is established correctly.</span></span>

## <a name="install-and-test-the-bot-in-teams"></a><span data-ttu-id="631e2-407">Installieren und Testen des bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="631e2-407">Install and test the bot in Teams</span></span>

1. <span data-ttu-id="631e2-408">Stellen Sie in Ihrem bot-Projekt sicher `TeamsAppManifest` , dass der `manifest.json` Ordner den zusammen `outline.png` mit `color.png` einem und Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="631e2-408">In your bot project, ensure that the `TeamsAppManifest` folder contains the `manifest.json` along with an `outline.png` and `color.png` files.</span></span>
1. <span data-ttu-id="631e2-409">Navigieren Sie im Projektmappen- `TeamsAppManifest` Explorer zum Ordner.</span><span class="sxs-lookup"><span data-stu-id="631e2-409">In Solution Explorer, navigate to the `TeamsAppManifest` folder.</span></span> <span data-ttu-id="631e2-410">Bearbeiten `manifest.json` , indem Sie die folgenden Werte zuweisen:</span><span class="sxs-lookup"><span data-stu-id="631e2-410">Edit `manifest.json` by assigning the following values:</span></span>
    1. <span data-ttu-id="631e2-411">Stellen Sie sicher, dass die **bot-APP-ID** , die Sie zum Zeitpunkt der bot- `id` Kanal `botId`Registrierung erhalten haben, und zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="631e2-411">Ensure that the **bot App ID** you received at the time of the bot channel registration is assigned to `id` and `botId`.</span></span>
    1. <span data-ttu-id="631e2-412">Weisen Sie diesen Wert `validDomains: [ "token.botframework.com" ]`zu:.</span><span class="sxs-lookup"><span data-stu-id="631e2-412">Assign this value: `validDomains: [ "token.botframework.com" ]`.</span></span>
1. <span data-ttu-id="631e2-413">Wählen Sie die `manifest.json` `color.png` Dateien aus `outline.png`, und **zippen** Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="631e2-413">Select and **zip** the `manifest.json`, `outline.png`, and `color.png` files.</span></span>
1. <span data-ttu-id="631e2-414">Öffnen Sie **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="631e2-414">Open **Microsoft Teams**.</span></span>
1. <span data-ttu-id="631e2-415">Wählen Sie im linken Bereich unten das **Symbol apps**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-415">In the left panel, at the bottom, select the **Apps icon**.</span></span>
1. <span data-ttu-id="631e2-416">Wählen Sie im rechten Bereich unten die Option **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-416">In the right panel, at the bottom, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="631e2-417">Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.</span><span class="sxs-lookup"><span data-stu-id="631e2-417">Navigate to the `TeamsAppManifest` folder and upload the zipped manifest.</span></span>
<span data-ttu-id="631e2-418">Der folgende Assistent wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="631e2-418">The following wizard is displayed:</span></span>

    ![Upload von auth-bot-Teams](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. <span data-ttu-id="631e2-420">Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="631e2-420">Select the **Add to a team** button.</span></span>
1. <span data-ttu-id="631e2-421">Wählen Sie im nächsten Fenster das Team aus, in dem Sie den bot verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="631e2-421">In the next window, select the team where you want to use the bot.</span></span>
1. <span data-ttu-id="631e2-422">Wählen Sie die Schaltfläche **Einrichten eines bot** aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-422">Select the **Set up a bot** button.</span></span>
1. <span data-ttu-id="631e2-423">Wählen Sie im linken Bereich die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-423">Select the three dots (&#x25cf;&#x25cf;&#x25cf;) in the left panel.</span></span> <span data-ttu-id="631e2-424">Wählen Sie dann das **App Studio** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-424">Then select the **App Studio** icon.</span></span>
1. <span data-ttu-id="631e2-425">Wählen Sie die Registerkarte **Manifest-Editor** aus. Das Symbol für den von Ihnen hochgeladenen bot sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="631e2-425">Select the **Manifest editor** tab. You should see the icon for the bot you uploaded.</span></span>
1. <span data-ttu-id="631e2-426">Außerdem sollten Sie in der Lage sein, den bot als Kontakt in der Chat Liste zu sehen, den Sie zum Austauschen von Nachrichten mit dem bot verwenden können.</span><span class="sxs-lookup"><span data-stu-id="631e2-426">Also, you should be able to see the bot listed as a contact in the chat list that you can use to exchange messages with the bot.</span></span>

### <a name="testing-the-bot-locally-in-teams"></a><span data-ttu-id="631e2-427">Testen des bot lokal in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="631e2-427">Testing the bot locally in Teams</span></span>

<span data-ttu-id="631e2-428">Microsoft Teams ist ein vollständig Cloud-basiertes Produkt, für das alle Dienste, auf die es zugreift, über die Cloud über HTTPS-Endpunkte verfügbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="631e2-428">Microsoft Teams is an entirely cloud-based product, it requires all services it accesses to be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="631e2-429">Um den bot (unser Beispiel) für die Arbeit in Microsoft Teams zu aktivieren, müssen Sie daher entweder den Code in der Cloud Ihrer Wahl veröffentlichen oder eine lokal ausgeführten Instanz über ein **Tunneling** -Tool Extern zugänglich machen.</span><span class="sxs-lookup"><span data-stu-id="631e2-429">Therefore, to enable the bot (our sample) to work in Teams, you need to either publish the code to the cloud of your choice, or make a locally running instance externally accessible via a **tunneling** tool.</span></span> <span data-ttu-id="631e2-430">Wir empfehlen [ngrok](https://ngrok.com/download), mit dem eine extern adressierbare URL für einen Port erstellt wird, den Sie lokal auf Ihrem Computer öffnen.</span><span class="sxs-lookup"><span data-stu-id="631e2-430">We recommend  [ngrok](https://ngrok.com/download), which creates an externally addressable URL for a port you open locally on your machine.</span></span>
<span data-ttu-id="631e2-431">Führen Sie die folgenden Schritte aus, um ngrok als Vorbereitung für die lokale Ausführung Ihrer Microsoft Teams-App einzurichten:</span><span class="sxs-lookup"><span data-stu-id="631e2-431">To set up ngrok in preparation for running your Microsoft Teams app locally, follow these steps:</span></span>

1. <span data-ttu-id="631e2-432">Wechseln Sie in einem Terminalfenster zu dem Verzeichnis, in `ngrok.exe` dem Sie installiert haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-432">In a terminal window, go the directory where you have `ngrok.exe` installed.</span></span> <span data-ttu-id="631e2-433">Es wird empfohlen, den Pfad der *Umgebungsvariable* so festzulegen, dass darauf verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-433">We suggest setting the *environment variable* path to point to it.</span></span>
1. <span data-ttu-id="631e2-434">Ausführen, beispielsweise `ngrok http 3978 --host-header=localhost:3978`.</span><span class="sxs-lookup"><span data-stu-id="631e2-434">Run, for example, `ngrok http 3978 --host-header=localhost:3978`.</span></span> <span data-ttu-id="631e2-435">Ersetzen Sie die Portnummer bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="631e2-435">Replace the port number as needed.</span></span>
<span data-ttu-id="631e2-436">Dadurch wird ngrok gestartet, um den angegebenen Port abzuhören.</span><span class="sxs-lookup"><span data-stu-id="631e2-436">This launches ngrok to listen on the port you specify.</span></span> <span data-ttu-id="631e2-437">Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-437">In return, it gives you an externally addressable URL, valid for as long as ngrok is running.</span></span> <span data-ttu-id="631e2-438">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-438">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG)<span data-ttu-id="631e2-440">.</span><span class="sxs-lookup"><span data-stu-id="631e2-440">.</span></span>

1. <span data-ttu-id="631e2-441">Kopieren Sie die Weiterleitungs-HTTPS-Adresse.</span><span class="sxs-lookup"><span data-stu-id="631e2-441">Copy the forwarding HTTPS address.</span></span> <span data-ttu-id="631e2-442">Es sollte wie folgt aussehen: `https://dea822bf.ngrok.io/`.</span><span class="sxs-lookup"><span data-stu-id="631e2-442">It should be similar to the following: `https://dea822bf.ngrok.io/`.</span></span>
1. <span data-ttu-id="631e2-443">Append `/api/messages` zu erhalten `https://dea822bf.ngrok.io/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="631e2-443">Append `/api/messages` to obtain `https://dea822bf.ngrok.io/api/messages`.</span></span> <span data-ttu-id="631e2-444">Dies ist der **Nachrichten Endpunkt** für den bot, der lokal auf Ihrem Computer läuft und über das Internet in einem Chat in Microsoft Teams erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="631e2-444">This is the **messages endpoint** for the bot running locally on your machine and reachable over the web in a chat in Microsoft Teams.</span></span>
1. <span data-ttu-id="631e2-445">Ein letzter Schritt besteht darin, den Nachrichten Endpunkt des bereitgestellten bot zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-445">One final step to perform is to update the messages endpoint of the deployed bot.</span></span> <span data-ttu-id="631e2-446">In dem Beispiel haben wir den bot in Azure bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="631e2-446">In the example, we deployed the bot in Azure.</span></span> <span data-ttu-id="631e2-447">So \* \* lassen Sie uns diese Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="631e2-447">So \*\*let's perform these steps:</span></span>
    1. <span data-ttu-id="631e2-448">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="631e2-448">In your browser navigate to the [**Azure portal**][azure-portal].</span></span>
    1. <span data-ttu-id="631e2-449">Wählen Sie Ihre **bot-Kanal Registrierung**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-449">Select your **Bot Channel Registration**.</span></span>
    1. <span data-ttu-id="631e2-450">Wählen Sie im linken Bereich **Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="631e2-450">In the left panel, select **Settings**.</span></span>
    1. <span data-ttu-id="631e2-451">Geben Sie im rechten Bereich im Feld **Messaging-Endpunkt** die ngrok-URL in unserem Beispiel ein `https://dea822bf.ngrok.io/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="631e2-451">In the right panel, in the **Messaging endpoint** box, enter the ngrok URL, in our example, `https://dea822bf.ngrok.io/api/messages`.</span></span>
1. <span data-ttu-id="631e2-452">Starten Sie Ihren bot lokal, beispielsweise in Visual Studio Debugmodus.</span><span class="sxs-lookup"><span data-stu-id="631e2-452">Start your bot locally, for example in Visual Studio debug mode.</span></span>
1. <span data-ttu-id="631e2-453">Testen Sie den bot, während er lokal mit dem **Test-Webchat**des bot-Framework-Portals läuft.</span><span class="sxs-lookup"><span data-stu-id="631e2-453">Test the bot while running locally using the Bot Framework portal's **Test Web chat**.</span></span> <span data-ttu-id="631e2-454">Wie der Emulator erlaubt Ihnen dieser Test nicht den Zugriff auf Teams-spezifische Funktionen.</span><span class="sxs-lookup"><span data-stu-id="631e2-454">Like the Emulator, this test doesn't allow you to access Teams-specific functionality.</span></span>
1. <span data-ttu-id="631e2-455">Im Terminal-Fenster, `ngrok` in dem Sie sich befinden, können Sie den HTTP-Datenverkehr zwischen dem bot und dem Chat Client sehen.</span><span class="sxs-lookup"><span data-stu-id="631e2-455">In the terminal window where `ngrok` is running you can see HTTP traffic between the bot and the web chat client.</span></span> <span data-ttu-id="631e2-456">Wenn Sie eine detailliertere Ansicht wünschen, geben `http://127.0.0.1:4040` Sie in einem Browserfenster die Daten ein, die Sie aus dem vorherigen Terminalfenster erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="631e2-456">If you want a more detailed view, in a browser window enter `http://127.0.0.1:4040` you obtained from the previous terminal window.</span></span> <span data-ttu-id="631e2-457">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="631e2-457">The following image is an example:</span></span>

    ![Authentifizierungs-bot-Teams ngrok Tests](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png)<span data-ttu-id="631e2-459">.</span><span class="sxs-lookup"><span data-stu-id="631e2-459">.</span></span>

> [!NOTE]
> <span data-ttu-id="631e2-460">Wenn Sie ngrok beenden und neu starten, ändert sich die URL.</span><span class="sxs-lookup"><span data-stu-id="631e2-460">If you stop and restart ngrok, the URL changes.</span></span> <span data-ttu-id="631e2-461">Um ngrok in Ihrem Projekt zu verwenden, müssen Sie in Abhängigkeit von den von Ihnen verwendeten Funktionen alle URL-Verweise aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="631e2-461">To use ngrok in your project, and depending on the capabilities you're using, you must update all URL references.</span></span>

## <a name="additional-information"></a><span data-ttu-id="631e2-462">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="631e2-462">Additional information</span></span>

### <a name="teamsappmanifestmanifestjson"></a><span data-ttu-id="631e2-463">TeamsAppManifest/Manifest. JSON</span><span class="sxs-lookup"><span data-stu-id="631e2-463">TeamsAppManifest/manifest.json</span></span>

<span data-ttu-id="631e2-464">Dieses Manifest enthält Informationen, die Microsoft Teams benötigt, um eine Verbindung mit dem bot herzustellen.</span><span class="sxs-lookup"><span data-stu-id="631e2-464">This manifest contains information needed by Microsoft Teams to connect with the bot.</span></span>  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0.0",
  "id": "",
  "packageName": "com.teams.auth.bot",
  "developer": {
    "name": "TeamsBotAuth",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.teams.com/privacy",
    "termsOfUseUrl": "https://www.teams.com/termsofuse"
  },
  "icons": {
    "color": "color.png",
    "outline": "outline.png"
  },
  "name": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "description": {
    "short": "TeamsBotAuth",
    "full": "Teams Bot Authentication"
  },
  "accentColor": "#FFFFFF",
  "bots": [
    {
      "botId": "",
      "scopes": [
        "groupchat",
        "team"
      ],
      "supportsFiles": false,
      "isNotificationOnly": false
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [ "token.botframework.com" ]
}
```

<span data-ttu-id="631e2-465">Bei der Authentifizierung verhält sich Microsoft Teams geringfügig anders als andere Kanäle, wie unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="631e2-465">With authentication, Teams behaves slightly differently than other channels, as explained below.</span></span>

### <a name="handling-invoke-activity"></a><span data-ttu-id="631e2-466">Behandeln von Invoke-Aktivität</span><span class="sxs-lookup"><span data-stu-id="631e2-466">Handling Invoke Activity</span></span>

<span data-ttu-id="631e2-467">Eine **Invoke-Aktivität** wird an den bot statt an die Ereignisaktivität gesendet, die von anderen Kanälen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-467">An **Invoke Activity** is sent to the bot rather than the Event Activity used by other channels.</span></span>
<span data-ttu-id="631e2-468">Dies wird durch Unterklassen für das **ActivityHandler**getan.</span><span class="sxs-lookup"><span data-stu-id="631e2-468">This is done by sub-classing the **ActivityHandler**.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="631e2-469">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="631e2-469">C#/.NET</span></span>](#tab/dotnet-sample)

<span data-ttu-id="631e2-470">**Bots/DialogBot. cs**</span><span class="sxs-lookup"><span data-stu-id="631e2-470">**Bots/DialogBot.cs**</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

<span data-ttu-id="631e2-471">**Bots/TeamsBot. cs**</span><span class="sxs-lookup"><span data-stu-id="631e2-471">**Bots/TeamsBot.cs**</span></span>

<span data-ttu-id="631e2-472">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-472">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a><span data-ttu-id="631e2-473">TeamsActivityHandler.cs</span><span class="sxs-lookup"><span data-stu-id="631e2-473">TeamsActivityHandler.cs</span></span>

```csharp

protected virtual Task OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    switch (turnContext.Activity.Name)
    {
        case "signin/verifyState":
            return OnSigninVerifyStateAsync(turnContext, cancellationToken);

        default:
            return Task.CompletedTask;
    }
}

protected virtual Task OnSigninVerifyStateAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    return Task.CompletedTask;
}
```

# <a name="javascript"></a>[<span data-ttu-id="631e2-474">JavaScript</span><span class="sxs-lookup"><span data-stu-id="631e2-474">JavaScript</span></span>](#tab/node-js-dialog-sample)

<span data-ttu-id="631e2-475">**Bots/dialogBot. js**</span><span class="sxs-lookup"><span data-stu-id="631e2-475">**bots/dialogBot.js**</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

<span data-ttu-id="631e2-476">**Bots/teamsBot. js**</span><span class="sxs-lookup"><span data-stu-id="631e2-476">**bots/teamsBot.js**</span></span>

<span data-ttu-id="631e2-477">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-477">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

<span data-ttu-id="631e2-478">**Dialogfelder/mainDialog. js**</span><span class="sxs-lookup"><span data-stu-id="631e2-478">**dialogs/mainDialog.js**</span></span>

<span data-ttu-id="631e2-479">Verwenden `beginDialog` Sie in einem Dialogschritt zum Starten der OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-479">Within a dialog step, use `beginDialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="631e2-480">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Token-Antwortereignis, ohne dass der Benutzer aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-480">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="631e2-481">Andernfalls wird der Benutzer aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-481">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="631e2-482">Der Azure bot-Dienst sendet das Token-Antwortereignis, nachdem der Benutzer versucht, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-482">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

<span data-ttu-id="631e2-483">Überprüfen Sie im folgenden Dialogschritt auf das vorhanden sein eines Tokens im Ergebnis des vorherigen Schritts.</span><span class="sxs-lookup"><span data-stu-id="631e2-483">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="631e2-484">Wenn es sich nicht um NULL handelt, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="631e2-484">If it is not null, the user successfully signed in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

<span data-ttu-id="631e2-485">**Bots/logoutDialog. js**</span><span class="sxs-lookup"><span data-stu-id="631e2-485">**bots/logoutDialog.js**</span></span>

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[<span data-ttu-id="631e2-486">Python</span><span class="sxs-lookup"><span data-stu-id="631e2-486">Python</span></span>](#tab/python-sample)

<span data-ttu-id="631e2-487">**Bots/dialog_bot. py**</span><span class="sxs-lookup"><span data-stu-id="631e2-487">**bots/dialog_bot.py**</span></span>

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

<span data-ttu-id="631e2-488">**Bots/teams_bot. py**</span><span class="sxs-lookup"><span data-stu-id="631e2-488">**bots/teams_bot.py**</span></span>

<span data-ttu-id="631e2-489">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-489">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

<span data-ttu-id="631e2-490">**Dialoge/main_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="631e2-490">**dialogs/main_dialog.py**</span></span>

<span data-ttu-id="631e2-491">Verwenden `begin_dialog` Sie in einem Dialogschritt zum Starten der OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-491">Within a dialog step, use `begin_dialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="631e2-492">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Token-Antwortereignis, ohne dass der Benutzer aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="631e2-492">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="631e2-493">Andernfalls wird der Benutzer aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-493">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="631e2-494">Der Azure bot-Dienst sendet das Token-Antwortereignis, nachdem der Benutzer versucht, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="631e2-494">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

<span data-ttu-id="631e2-495">Überprüfen Sie im folgenden Dialogschritt auf das vorhanden sein eines Tokens im Ergebnis des vorherigen Schritts.</span><span class="sxs-lookup"><span data-stu-id="631e2-495">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="631e2-496">Wenn es sich nicht um NULL handelt, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="631e2-496">If it is not null, the user successfully signed in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

<span data-ttu-id="631e2-497">**Dialoge/logout_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="631e2-497">**dialogs/logout_dialog.py**</span></span>

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

> [!div class="nextstepaction"]
> [<span data-ttu-id="631e2-498">Informationen zum Hinzufügen von Authentifizierung über Azure bot-Dienst</span><span class="sxs-lookup"><span data-stu-id="631e2-498">Learn about adding adding authentication via Azure Bot Service</span></span>](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: https://docs.microsoft.com/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0
[concept-state]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0
[concept-dialogs]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0
[simple-dialog]: https://docs.microsoft.com/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
