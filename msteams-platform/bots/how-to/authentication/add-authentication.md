---
title: Hinzufügen der Authentifizierung zu Teams Bot
author: clearab
description: Hinzufügen der OAuth-Authentifizierung zu einem Bot in Microsoft Teams.
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 7f171a791a9ee557e4af2e7d1e1b053046bd9db5
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101488"
---
# <a name="add-authentication-to-your-teams-bot"></a><span data-ttu-id="91c55-103">Hinzufügen der Authentifizierung zu Teams Bot</span><span class="sxs-lookup"><span data-stu-id="91c55-103">Add authentication to your Teams bot</span></span>

<span data-ttu-id="91c55-104">Es gibt Zeiten, in denen Sie möglicherweise Bots in Microsoft Teams, die im Namen des Benutzers auf Ressourcen zugreifen können, z. B. einen E-Mail-Dienst.</span><span class="sxs-lookup"><span data-stu-id="91c55-104">There are times when you may need to create bots in Microsoft Teams that can access resources on behalf of the user, such as a mail service.</span></span>

<span data-ttu-id="91c55-105">In diesem Artikel wird die Verwendung der Azure Bot Service v4 SDK-Authentifizierung basierend auf OAuth 2.0 veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="91c55-105">This article demonstrates how to use Azure Bot Service v4 SDK authentication, based on OAuth 2.0.</span></span> <span data-ttu-id="91c55-106">Dies erleichtert die Entwicklung eines Bots, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="91c55-106">This makes it easier to develop a bot that can use authentication tokens based on the user's credentials.</span></span> <span data-ttu-id="91c55-107">Entscheidend dabei ist die Verwendung von **Identitätsanbietern,** wie später zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="91c55-107">Key in all this is the use of **identity providers**, as we will see later.</span></span>

<span data-ttu-id="91c55-108">OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-108">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="91c55-109">Ein grundlegendes Verständnis von OAuth 2.0 ist eine Voraussetzung für die Arbeit mit der Authentifizierung in Teams.</span><span class="sxs-lookup"><span data-stu-id="91c55-109">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

<span data-ttu-id="91c55-110">Grundlegende Informationen finden Sie unter [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) und [OAuth 2.0](https://oauth.net/2/) für die vollständige Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="91c55-110">See [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) for a basic understanding, and [OAuth 2.0](https://oauth.net/2/) for the complete specification.</span></span>

<span data-ttu-id="91c55-111">Weitere Informationen dazu, wie der Azure Bot Service die Authentifizierung verarbeitet, finden Sie unter [Benutzerauthentifizierung innerhalb einer Unterhaltung](https://aka.ms/azure-bot-authentication).</span><span class="sxs-lookup"><span data-stu-id="91c55-111">For more information about how the Azure Bot Service handles authentication, see [User authentication within a conversation](https://aka.ms/azure-bot-authentication).</span></span>

<span data-ttu-id="91c55-112">In diesem Artikel erhalten Sie Informationen zu folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="91c55-112">In this article you'll learn:</span></span>

- <span data-ttu-id="91c55-113">**Erstellen eines Authentifizierungs-aktivierten Bots**.</span><span class="sxs-lookup"><span data-stu-id="91c55-113">**How to create an authentication-enabled bot**.</span></span> <span data-ttu-id="91c55-114">Sie verwenden [cs-auth-sample,][teams-auth-bot-cs] um Anmeldeinformationen des Benutzers und das Generieren des Authentifizierungstokens zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="91c55-114">You'll use [cs-auth-sample][teams-auth-bot-cs] to handle user sign-in credentials and the generating the authentication token.</span></span>
- <span data-ttu-id="91c55-115">**So stellen Sie den Bot in Azure bereit und ordnen ihn einem Identitätsanbieter zu.**</span><span class="sxs-lookup"><span data-stu-id="91c55-115">**How to deploy the bot to Azure and associate it with an identity provider**.</span></span> <span data-ttu-id="91c55-116">Der Anbieter gibt ein Token basierend auf anmeldeinformationen des Benutzers aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-116">The provider issues a token based on user sign-in credentials.</span></span> <span data-ttu-id="91c55-117">Der Bot kann das Token für den Zugriff auf Ressourcen verwenden, z. B. einen E-Mail-Dienst, für die eine Authentifizierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="91c55-117">The bot can use the token to access resources, such as a mail service, which require authentication.</span></span> <span data-ttu-id="91c55-118">Weitere Informationen finden Sie [Microsoft Teams Authentifizierungsfluss für Bots](auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="91c55-118">For more information see  [Microsoft Teams authentication flow for bots](auth-flow-bot.md).</span></span>
- <span data-ttu-id="91c55-119">**Integrieren des Bots in Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="91c55-119">**How to integrate the bot within Microsoft Teams**.</span></span> <span data-ttu-id="91c55-120">Nachdem der Bot integriert wurde, können Sie sich in einem Chat anmelden und Nachrichten damit austauschen.</span><span class="sxs-lookup"><span data-stu-id="91c55-120">Once the bot has been integrated, you can sign in and exchange messages with it in a chat.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91c55-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="91c55-121">Prerequisites</span></span>

- <span data-ttu-id="91c55-122">Kenntnisse der [Botgrundkenntnisse,][concept-basics] [des Verwaltungsstatus,][concept-state]der [Dialogbibliothek][concept-dialogs]und der Implementierung des sequenziellen [Unterhaltungsflusses.][simple-dialog]</span><span class="sxs-lookup"><span data-stu-id="91c55-122">Knowledge of [bot basics][concept-basics], [managing state][concept-state], the [dialogs library][concept-dialogs], and how to [implement sequential conversation flow][simple-dialog].</span></span>
- <span data-ttu-id="91c55-123">Kenntnisse der Azure- und OAuth 2.0-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="91c55-123">Knowledge of Azure and OAuth 2.0 development.</span></span>
- <span data-ttu-id="91c55-124">Die aktuellen Versionen von Visual Studio und Git.</span><span class="sxs-lookup"><span data-stu-id="91c55-124">The current versions of Visual Studio and Git.</span></span>
- <span data-ttu-id="91c55-125">Azure-Konto.</span><span class="sxs-lookup"><span data-stu-id="91c55-125">Azure account.</span></span> <span data-ttu-id="91c55-126">Bei Bedarf können Sie ein [kostenloses Azure-Konto erstellen.](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="91c55-126">If needed, you can create an [Azure free account](https://azure.microsoft.com/free/).</span></span>
- <span data-ttu-id="91c55-127">Das folgende Beispiel.</span><span class="sxs-lookup"><span data-stu-id="91c55-127">The following sample.</span></span>

    | <span data-ttu-id="91c55-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="91c55-128">Sample</span></span> | <span data-ttu-id="91c55-129">BotBuilder-Version</span><span class="sxs-lookup"><span data-stu-id="91c55-129">BotBuilder version</span></span> | <span data-ttu-id="91c55-130">Demonstrates</span><span class="sxs-lookup"><span data-stu-id="91c55-130">Demonstrates</span></span> |
    |:---|:---:|:---|
    | <span data-ttu-id="91c55-131">**Bot-Authentifizierung** in [cs-auth-sample][teams-auth-bot-cs]</span><span class="sxs-lookup"><span data-stu-id="91c55-131">**Bot authentication** in [cs-auth-sample][teams-auth-bot-cs]</span></span> | <span data-ttu-id="91c55-132">v4</span><span class="sxs-lookup"><span data-stu-id="91c55-132">v4</span></span> | <span data-ttu-id="91c55-133">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="91c55-133">OAuthCard support</span></span> |
    | <span data-ttu-id="91c55-134">**Bot-Authentifizierung** in [js-auth-sample][teams-auth-bot-js]</span><span class="sxs-lookup"><span data-stu-id="91c55-134">**Bot authentication** in [js-auth-sample][teams-auth-bot-js]</span></span> | <span data-ttu-id="91c55-135">v4</span><span class="sxs-lookup"><span data-stu-id="91c55-135">v4</span></span>| <span data-ttu-id="91c55-136">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="91c55-136">OAuthCard support</span></span>  |
    | <span data-ttu-id="91c55-137">**Bot-Authentifizierung** in [py-auth-sample][teams-auth-bot-py]</span><span class="sxs-lookup"><span data-stu-id="91c55-137">**Bot authentication** in [py-auth-sample][teams-auth-bot-py]</span></span> | <span data-ttu-id="91c55-138">v4</span><span class="sxs-lookup"><span data-stu-id="91c55-138">v4</span></span> | <span data-ttu-id="91c55-139">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="91c55-139">OAuthCard support</span></span> |

## <a name="create-the-resource-group"></a><span data-ttu-id="91c55-140">Erstellen der Ressourcengruppe</span><span class="sxs-lookup"><span data-stu-id="91c55-140">Create the resource group</span></span>

<span data-ttu-id="91c55-141">Die Ressourcengruppe und der Dienstplan sind nicht unbedingt erforderlich, sie ermöglichen es Ihnen jedoch, die von Ihnen erstellten Ressourcen bequem frei zu lassen.</span><span class="sxs-lookup"><span data-stu-id="91c55-141">The resource group and the service plan aren't strictly necessary, but they allow you to conveniently release the resources you create.</span></span> <span data-ttu-id="91c55-142">Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.</span><span class="sxs-lookup"><span data-stu-id="91c55-142">This is good practice for keeping your resources organized and manageable.</span></span>

<span data-ttu-id="91c55-143">Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das Bot Framework zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="91c55-143">You use a resource group to create individual resources for the Bot Framework.</span></span> <span data-ttu-id="91c55-144">Stellen Sie für die Leistung sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.</span><span class="sxs-lookup"><span data-stu-id="91c55-144">For performance, ensure that these resources are located in the same Azure region.</span></span>

1. <span data-ttu-id="91c55-145">Melden Sie sich in Ihrem Browser beim [**Azure-Portal an.**][azure-portal]</span><span class="sxs-lookup"><span data-stu-id="91c55-145">In your browser, sign into the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="91c55-146">Wählen Sie im linken Navigationsbereich **Ressourcengruppen aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-146">In the left navigation panel, select **Resource groups**.</span></span>
1. <span data-ttu-id="91c55-147">Wählen Sie oben links im angezeigten Fenster die Registerkarte **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="91c55-147">In the upper left of the displayed window, select **Add** tab to create a new resource group.</span></span> <span data-ttu-id="91c55-148">Sie werden aufgefordert, Folgendes zur Verfügung zu stellen:</span><span class="sxs-lookup"><span data-stu-id="91c55-148">You'll be prompted to provide the following:</span></span>
    1. <span data-ttu-id="91c55-149">**Abonnement**:</span><span class="sxs-lookup"><span data-stu-id="91c55-149">**Subscription**.</span></span> <span data-ttu-id="91c55-150">Verwenden Sie Ihr vorhandenes Abonnement.</span><span class="sxs-lookup"><span data-stu-id="91c55-150">Use your existing subscription.</span></span>
    1. <span data-ttu-id="91c55-151">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="91c55-151">**Resource group**.</span></span> <span data-ttu-id="91c55-152">Geben Sie den Namen für die Ressourcengruppe ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-152">Enter the name for the resource group.</span></span> <span data-ttu-id="91c55-153">Ein Beispiel könnte *TeamsResourceGroup sein.*</span><span class="sxs-lookup"><span data-stu-id="91c55-153">An example could be  *TeamsResourceGroup*.</span></span> <span data-ttu-id="91c55-154">Denken Sie daran, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="91c55-154">Remember that the name must be unique.</span></span>
    1. <span data-ttu-id="91c55-155">Wählen Sie **im Dropdownmenü** Region die Option *West US* oder eine Region in der Nähe Ihrer Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-155">From the **Region** drop-down menu, select *West US*, or a region close to your applications.</span></span>
    1. <span data-ttu-id="91c55-156">Wählen Sie die **Schaltfläche Überprüfen und Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-156">Select the **Review and create** button.</span></span> <span data-ttu-id="91c55-157">Es sollte ein Banner mit dem Lesecode *Validation passed angezeigt werden.*</span><span class="sxs-lookup"><span data-stu-id="91c55-157">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="91c55-158">Wählen Sie die **Schaltfläche Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-158">Select the **Create** button.</span></span> <span data-ttu-id="91c55-159">Das Erstellen der Ressourcengruppe kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="91c55-159">It may take a few minutes to create the resource group.</span></span>

> [!TIP]
> <span data-ttu-id="91c55-160">Wie bei den Ressourcen, die Sie später in diesem Lernprogramm erstellen, sollten Sie diese Ressourcengruppe für den einfachen Zugriff an Ihr Dashboard anheften.</span><span class="sxs-lookup"><span data-stu-id="91c55-160">As with the resources you'll create later in this tutorial, it's a good idea to pin this resource group to your dashboard for easy access.</span></span> <span data-ttu-id="91c55-161">Wenn Sie dies tun möchten, wählen Sie das Pinsymbol aus, &#128204; in der oberen rechten Ecke des Dashboards.</span><span class="sxs-lookup"><span data-stu-id="91c55-161">If you'd like to do so, select the pin icon &#128204; in the upper right of the dashboard.</span></span>

## <a name="create-the-service-plan"></a><span data-ttu-id="91c55-162">Erstellen des Dienstplans</span><span class="sxs-lookup"><span data-stu-id="91c55-162">Create the service plan</span></span>

1. <span data-ttu-id="91c55-163">Wählen Sie [**im Azure-Portal**][azure-portal]im linken Navigationsbereich Die Option **Ressource erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-163">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Create a resource**.</span></span>
1. <span data-ttu-id="91c55-164">Geben Sie im Suchfeld *App Service Plan ein.*</span><span class="sxs-lookup"><span data-stu-id="91c55-164">In the search box, type *App Service Plan*.</span></span> <span data-ttu-id="91c55-165">Wählen Sie in den Suchergebnissen die Karte App **Service Plan** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-165">Select the **App Service Plan** card from the search results.</span></span>
1. <span data-ttu-id="91c55-166">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-166">Select **Create**.</span></span>
1. <span data-ttu-id="91c55-167">Sie werden aufgefordert, die folgenden Informationen zur Verfügung zu stellen:</span><span class="sxs-lookup"><span data-stu-id="91c55-167">You'll be asked to provide the following information:</span></span>
    1. <span data-ttu-id="91c55-168">**Abonnement**:</span><span class="sxs-lookup"><span data-stu-id="91c55-168">**Subscription**.</span></span> <span data-ttu-id="91c55-169">Sie können ein vorhandenes Abonnement verwenden.</span><span class="sxs-lookup"><span data-stu-id="91c55-169">You can use an existing subscription.</span></span>
    1. <span data-ttu-id="91c55-170">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="91c55-170">**Resource Group**.</span></span> <span data-ttu-id="91c55-171">Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-171">Select the group you created earlier.</span></span>
    1. <span data-ttu-id="91c55-172">**Name**.</span><span class="sxs-lookup"><span data-stu-id="91c55-172">**Name**.</span></span> <span data-ttu-id="91c55-173">Geben Sie den Namen für den Dienstplan ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-173">Enter the name for the service plan.</span></span> <span data-ttu-id="91c55-174">Ein Beispiel könnte *TeamsServicePlan sein.*</span><span class="sxs-lookup"><span data-stu-id="91c55-174">An example could be  *TeamsServicePlan*.</span></span> <span data-ttu-id="91c55-175">Denken Sie daran, dass der Name innerhalb der Gruppe eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="91c55-175">Remember that the name must be unique, within the group.</span></span>
    1. <span data-ttu-id="91c55-176">**Betriebssystem**.</span><span class="sxs-lookup"><span data-stu-id="91c55-176">**Operating System**.</span></span> <span data-ttu-id="91c55-177">Wählen *Windows* oder Ihr entsprechendes Betriebssystem aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-177">Select *Windows* or your applicable OS.</span></span>
    1. <span data-ttu-id="91c55-178">**Region**.</span><span class="sxs-lookup"><span data-stu-id="91c55-178">**Region**.</span></span> <span data-ttu-id="91c55-179">Wählen *Sie West US* oder eine Region in der Nähe Ihrer Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-179">Select *West US* or a region close to your applications.</span></span>
    1. <span data-ttu-id="91c55-180">**Preisebene**.</span><span class="sxs-lookup"><span data-stu-id="91c55-180">**Pricing Tier**.</span></span> <span data-ttu-id="91c55-181">Stellen Sie sicher, *dass Standard S1* ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="91c55-181">Make sure that *Standard S1* is selected.</span></span> <span data-ttu-id="91c55-182">Dies sollte der Standardwert sein.</span><span class="sxs-lookup"><span data-stu-id="91c55-182">This should be the default value.</span></span>
    1. <span data-ttu-id="91c55-183">Wählen Sie die **Schaltfläche Überprüfen und Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-183">Select the **Review and create** button.</span></span> <span data-ttu-id="91c55-184">Es sollte ein Banner mit dem Lesecode *Validation passed angezeigt werden.*</span><span class="sxs-lookup"><span data-stu-id="91c55-184">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="91c55-185">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-185">Select **Create**.</span></span> <span data-ttu-id="91c55-186">Das Erstellen des App-Dienstplans kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="91c55-186">It may take a few minutes to create the app service plan.</span></span> <span data-ttu-id="91c55-187">Der Plan wird in der Ressourcengruppe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="91c55-187">The plan will be listed in the resource group.</span></span>

## <a name="create-the-bot-channels-registration"></a><span data-ttu-id="91c55-188">Erstellen der Registrierung von Botkanälen</span><span class="sxs-lookup"><span data-stu-id="91c55-188">Create the bot channels registration</span></span>

<span data-ttu-id="91c55-189">Die Registrierung von Botkanälen registriert Ihren Webdienst als Bot beim Bot Framework, vorausgesetzt, Sie verfügen über eine Microsoft App-ID und ein App-Kennwort (geheimer Client).</span><span class="sxs-lookup"><span data-stu-id="91c55-189">The bot channels registration registers your web service as a bot with the Bot Framework, provided you have a Microsoft App Id and App password (client secret).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="91c55-190">Sie müssen Ihren Bot nur registrieren, wenn er nicht in Azure gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-190">You only need to register your bot if it is not hosted in Azure.</span></span> <span data-ttu-id="91c55-191">Wenn Sie [einen Bot über](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert.</span><span class="sxs-lookup"><span data-stu-id="91c55-191">If you [created a bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) through the Azure portal then it is already registered with the service.</span></span> <span data-ttu-id="91c55-192">Wenn Sie Ihren Bot über das [Bot Framework](https://dev.botframework.com/bots/new) oder [AppStudio](~/concepts/build-and-test/app-studio-overview.md) erstellt haben, ist Ihr Bot nicht in Azure registriert.</span><span class="sxs-lookup"><span data-stu-id="91c55-192">If you created your bot through the [Bot Framework](https://dev.botframework.com/bots/new) or [AppStudio](~/concepts/build-and-test/app-studio-overview.md) your bot isn't registered in Azure.</span></span>

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> <span data-ttu-id="91c55-193">Die Ressource Bot Channels Registration zeigt die **globale** Region an, auch wenn Sie "USA, Westen" ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-193">The Bot Channels Registration resource will show the **Global** region even if you selected West US.</span></span> <span data-ttu-id="91c55-194">Dies entspricht dem erwarteten Verhalten.</span><span class="sxs-lookup"><span data-stu-id="91c55-194">This is expected.</span></span>

<span data-ttu-id="91c55-195">Weitere Informationen finden Sie unter [Create a bot for Teams](../create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="91c55-195">For more information, see [Create a bot for Teams](../create-a-bot-for-teams.md).</span></span>

## <a name="create-the-identity-provider"></a><span data-ttu-id="91c55-196">Erstellen des Identitätsanbieters</span><span class="sxs-lookup"><span data-stu-id="91c55-196">Create the identity provider</span></span>

<span data-ttu-id="91c55-197">Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="91c55-197">You need an identity provider that can be used for authentication.</span></span>
<span data-ttu-id="91c55-198">In diesem Verfahren verwenden Sie einen Azure #A0 andere von Azure AD unterstützte Identitätsanbieter können ebenfalls verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-198">In this procedure you'll use an Azure AD provider; other Azure AD supported identity providers can also be used.</span></span>

1. <span data-ttu-id="91c55-199">Wählen Sie [**im Azure-Portal**][azure-portal]im linken Navigationsbereich die **Option Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="91c55-199">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Azure Active Directory**.</span></span>
    > [!TIP]
    > <span data-ttu-id="91c55-200">Sie müssen diese Azure AD-Ressource in einem Mandanten erstellen und registrieren, in dem Sie zustimmen können, von einer Anwendung angeforderte Berechtigungen zu delegieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-200">You'll need to create and register this Azure AD resource in a tenant in which you can consent to delegate permissions requested by an application.</span></span>
    > <span data-ttu-id="91c55-201">Anweisungen zum Erstellen eines Mandanten finden Sie unter [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span><span class="sxs-lookup"><span data-stu-id="91c55-201">For instruction on creating a tenant, see [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span></span>
1. <span data-ttu-id="91c55-202">Wählen Sie im linken Bereich **App-Registrierungen aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-202">In the left panel, select **App registrations**.</span></span>
1. <span data-ttu-id="91c55-203">Wählen Sie im rechten Bereich die Registerkarte **Neue Registrierung** oben links aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-203">In the right panel, select the **New registration** tab, in the upper left.</span></span>
1. <span data-ttu-id="91c55-204">Sie werden aufgefordert, die folgenden Informationen zur Verfügung zu stellen:</span><span class="sxs-lookup"><span data-stu-id="91c55-204">You'll be asked to provide the following information:</span></span>
   1. <span data-ttu-id="91c55-205">**Name**.</span><span class="sxs-lookup"><span data-stu-id="91c55-205">**Name**.</span></span> <span data-ttu-id="91c55-206">Geben Sie den Namen für die Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-206">Enter the name for the application.</span></span> <span data-ttu-id="91c55-207">Ein Beispiel könnte *BotTeamsIdentity sein.*</span><span class="sxs-lookup"><span data-stu-id="91c55-207">An example could be  *BotTeamsIdentity*.</span></span> <span data-ttu-id="91c55-208">Denken Sie daran, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="91c55-208">Remember that the name must be unique.</span></span>
   1. <span data-ttu-id="91c55-209">Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-209">Select the **Supported account types** for your application.</span></span> <span data-ttu-id="91c55-210">Wählen Sie Konten in einem beliebigen Organisationsverzeichnis *(Beliebiges Azure AD-Verzeichnis - Multitenant) und persönliche Microsoft-Konten (z. B. Skype, Xbox) aus.*</span><span class="sxs-lookup"><span data-stu-id="91c55-210">Select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
   1. <span data-ttu-id="91c55-211">Für den **Umleitungs-URI:**</span><span class="sxs-lookup"><span data-stu-id="91c55-211">For the **Redirect URI**:</span></span><br/>
       <span data-ttu-id="91c55-212">&#x2713;Wählen Sie **Web aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-212">&#x2713;Select **Web**.</span></span> <br/>
       <span data-ttu-id="91c55-213">&#x2713; Legen Sie die URL auf `https://token.botframework.com/.auth/web/redirect` .</span><span class="sxs-lookup"><span data-stu-id="91c55-213">&#x2713; Set the URL to `https://token.botframework.com/.auth/web/redirect`.</span></span>
   1. <span data-ttu-id="91c55-214">Wählen Sie **Registrieren** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-214">Select **Register**.</span></span>

1. <span data-ttu-id="91c55-215">Nachdem es erstellt wurde, zeigt Azure die **Seite Übersicht** für die App an.</span><span class="sxs-lookup"><span data-stu-id="91c55-215">Once it is created, Azure displays the **Overview** page for the app.</span></span> <span data-ttu-id="91c55-216">Kopieren Und speichern Sie die folgenden Informationen in einer Datei:</span><span class="sxs-lookup"><span data-stu-id="91c55-216">Copy and save the following information to a file:</span></span>

    1. <span data-ttu-id="91c55-217">Der **Wert der Anwendungs-ID (Client).**</span><span class="sxs-lookup"><span data-stu-id="91c55-217">The **Application (client) ID** value.</span></span> <span data-ttu-id="91c55-218">Sie verwenden diesen Wert später als *Client-ID,* wenn Sie diese Azure-Identitätsanwendung bei Ihrem Bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-218">You'll use this value later as the *Client ID* when you register this Azure identity application with your bot.</span></span>
    1. <span data-ttu-id="91c55-219">Der **Wert der Verzeichnis-ID (Mandant).**</span><span class="sxs-lookup"><span data-stu-id="91c55-219">The **Directory (tenant) ID** value.</span></span> <span data-ttu-id="91c55-220">Sie verwenden diesen Wert später auch als *Mandanten-ID,* um diese Azure-Identitätsanwendung bei Ihrem Bot zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-220">You'll also use this value later as the *Tenant ID* to register this Azure identity application with your bot.</span></span>

1. <span data-ttu-id="91c55-221">Wählen Sie im linken Bereich Zertifikate **& aus,** um einen geheimen Clientgeheimnisse für Ihre Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="91c55-221">In the left panel, select **Certificates & secrets** to create a client secret for your application.</span></span>

   1. <span data-ttu-id="91c55-222">Wählen **Sie unter Geheime** Clientgeheimnisse &#x2795; **Neuen Geheimen Client aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-222">Under **Client secrets**, select &#x2795; **New client secret**.</span></span>
   1. <span data-ttu-id="91c55-223">Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen Personen zu identifizieren, die Sie möglicherweise für diese App erstellen müssen, z. B. *bot identity app in Teams*.</span><span class="sxs-lookup"><span data-stu-id="91c55-223">Add a description to identify this secret from others you might need to create for this app, such as *Bot identity app in Teams*.</span></span>
   1. <span data-ttu-id="91c55-224">Set **Expires** to your selection.</span><span class="sxs-lookup"><span data-stu-id="91c55-224">Set **Expires** to your selection.</span></span>
   1. <span data-ttu-id="91c55-225">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="91c55-225">Select **Add**.</span></span>
   1. <span data-ttu-id="91c55-226">Bevor Sie diese Seite verlassen, **müssen Sie den geheimen Eintrag aufzeichnen.**</span><span class="sxs-lookup"><span data-stu-id="91c55-226">Before leaving this page, **record the secret**.</span></span> <span data-ttu-id="91c55-227">Dieser Wert wird später als  geheimer Clientgeheimnis verwendet, wenn Sie Ihre Azure AD-Anwendung bei Ihrem Bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-227">You'll use this value later as the _Client secret_ when you register your Azure AD application with your bot.</span></span>

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a><span data-ttu-id="91c55-228">Konfigurieren sie die Verbindung des Identitätsanbieters, und registrieren Sie sie beim Bot.</span><span class="sxs-lookup"><span data-stu-id="91c55-228">Configure the identity provider connection and register it with the bot</span></span>

<span data-ttu-id="91c55-229">Hinweis: Es gibt zwei Optionen für Dienstanbieter hier- Azure AD V1 und Azure AD V2.</span><span class="sxs-lookup"><span data-stu-id="91c55-229">Note-there are two options for Service Providers here-Azure AD V1 and Azure AD V2.</span></span>  <span data-ttu-id="91c55-230">Die Unterschiede zwischen den beiden Anbietern sind hier [zusammengefasst,](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison)aber im Allgemeinen bietet V2 mehr Flexibilität bei der Änderung von Botberechtigungen.</span><span class="sxs-lookup"><span data-stu-id="91c55-230">The differences between the two providers are summarized [here](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison), but in general, V2 provides more flexibility with respect to changing bot permissions.</span></span>  <span data-ttu-id="91c55-231">Graph API-Berechtigungen sind im Feld Bereiche aufgeführt, und wenn neue hinzugefügt werden, können Bots Benutzern bei der nächsten Anmeldung die Zustimmung zu den neuen Berechtigungen erteilen.</span><span class="sxs-lookup"><span data-stu-id="91c55-231">Graph API permissions are listed in the scopes field, and as new ones are added, bots will allow users to consent to the new permissions on the next sign in.</span></span>  <span data-ttu-id="91c55-232">Für V1 muss die Bot-Zustimmung vom Benutzer gelöscht werden, damit neue Berechtigungen im OAuth-Dialogfeld aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-232">For V1, the bot consent must be deleted by the user for new permissions to be prompted in the OAuth dialog.</span></span> 

#### <a name="azure-ad-v1"></a><span data-ttu-id="91c55-233">Azure AD V1</span><span class="sxs-lookup"><span data-stu-id="91c55-233">Azure AD V1</span></span>

1. <span data-ttu-id="91c55-234">Wählen Sie [**im Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-234">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="91c55-235">Wählen Sie den Link zur Botkanalregistrierung aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-235">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="91c55-236">Öffnen Sie die Ressourcenseite, und wählen **Sie Konfiguration** unter **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="91c55-236">Open the resource page and select **Configuration** under **Settings**.</span></span> 
1. <span data-ttu-id="91c55-237">Wählen **Sie OAuth Connection Einstellungen hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-237">Select **Add OAuth Connection Settings**.</span></span>    
<span data-ttu-id="91c55-238">In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:</span><span class="sxs-lookup"><span data-stu-id="91c55-238">The following image displays the corresponding selection in the resource page:</span></span>  
<span data-ttu-id="91c55-239">![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)</span><span class="sxs-lookup"><span data-stu-id="91c55-239">![SampleAppDemoBot configuration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)</span></span>
1. <span data-ttu-id="91c55-240">Füllen Sie das Formular wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="91c55-240">Complete the form as follows:</span></span>

    1. <span data-ttu-id="91c55-241">**Name**.</span><span class="sxs-lookup"><span data-stu-id="91c55-241">**Name**.</span></span> <span data-ttu-id="91c55-242">Geben Sie einen Namen für die Verbindung ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-242">Enter a name for the connection.</span></span> <span data-ttu-id="91c55-243">Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei.</span><span class="sxs-lookup"><span data-stu-id="91c55-243">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="91c55-244">Beispiel: *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="91c55-244">For example *BotTeamsAuthADv1*.</span></span>
    1. <span data-ttu-id="91c55-245">**Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="91c55-245">**Service Provider**.</span></span> <span data-ttu-id="91c55-246">Wählen Sie **Azure Active Directory** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-246">Select **Azure Active Directory**.</span></span> <span data-ttu-id="91c55-247">Nachdem Sie diese Option ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91c55-247">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="91c55-248">**Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-248">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="91c55-249">**Geheimer Clientgeheimnis**.</span><span class="sxs-lookup"><span data-stu-id="91c55-249">**Client secret**.</span></span> <span data-ttu-id="91c55-250">Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-250">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="91c55-251">**Grant Type**.</span><span class="sxs-lookup"><span data-stu-id="91c55-251">**Grant Type**.</span></span> <span data-ttu-id="91c55-252">Geben Sie `authorization_code` ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-252">Enter `authorization_code`.</span></span>
    1. <span data-ttu-id="91c55-253">**Anmelde-URL**.</span><span class="sxs-lookup"><span data-stu-id="91c55-253">**Login URL**.</span></span> <span data-ttu-id="91c55-254">Geben Sie `https://login.microsoftonline.com` ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-254">Enter `https://login.microsoftonline.com`.</span></span>
    1. <span data-ttu-id="91c55-255">**Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandant) ein,** die Sie zuvor für Ihre Azure-Identitäts-App aufgezeichnet haben oder je nach dem unterstützten Kontotyp, der beim Erstellen der Identitätsanbieter-App ausgewählt wurde. </span><span class="sxs-lookup"><span data-stu-id="91c55-255">**Tenant ID**, enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="91c55-256">So entscheiden Sie, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="91c55-256">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="91c55-257">Wenn Sie nur Konten in diesem Organisationsverzeichnis *(nur Microsoft - Einzelner* Mandant) oder Konten in einem beliebigen Organisationsverzeichnis *(Microsoft AAD-Verzeichnis - Mehr* mandant) ausgewählt haben, geben Sie die Mandanten-ID ein, die Sie zuvor für die AAD-App aufgezeichnet haben. </span><span class="sxs-lookup"><span data-stu-id="91c55-257">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="91c55-258">Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="91c55-258">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="91c55-259">Wenn Sie Konten in einem beliebigen Organisationsverzeichnis ausgewählt haben (Beliebiges AAD-Verzeichnis – Mehr mandanten- und persönliche  Microsoft-Konten, *z. B. Skype, Xbox, Outlook),* geben Sie das Wort common anstelle einer Mandanten-ID ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-259">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="91c55-260">Andernfalls überprüft die AAD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-260">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    <span data-ttu-id="91c55-261">h.</span><span class="sxs-lookup"><span data-stu-id="91c55-261">h.</span></span> <span data-ttu-id="91c55-262">Geben **Sie für Ressourcen-URL** `https://graph.microsoft.com/` ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-262">For **Resource URL**, enter `https://graph.microsoft.com/`.</span></span> <span data-ttu-id="91c55-263">Dies wird im aktuellen Codebeispiel nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="91c55-263">This is not used in the current code sample.</span></span>  
    <span data-ttu-id="91c55-264">i.</span><span class="sxs-lookup"><span data-stu-id="91c55-264">i.</span></span> <span data-ttu-id="91c55-265">Lassen **Sie Bereiche** leer.</span><span class="sxs-lookup"><span data-stu-id="91c55-265">Leave **Scopes** blank.</span></span> <span data-ttu-id="91c55-266">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-266">The following image is an example:</span></span>

    ![teams bots app auth connection string adv1 view](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. <span data-ttu-id="91c55-268">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="91c55-268">Select **Save**.</span></span>

#### <a name="azure-ad-v2"></a><span data-ttu-id="91c55-269">Azure AD V2</span><span class="sxs-lookup"><span data-stu-id="91c55-269">Azure AD V2</span></span>

1. <span data-ttu-id="91c55-270">Wählen Sie [**im Azure-Portal**][azure-portal]Ihre Ressourcengruppe aus dem Dashboard aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-270">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="91c55-271">Wählen Sie den Link zur Botkanalregistrierung aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-271">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="91c55-272">Öffnen Sie die Ressourcenseite, und wählen **Sie Konfiguration** unter **Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="91c55-272">Open the resource page and select **Configuration** under **Settings**.</span></span> 
1. <span data-ttu-id="91c55-273">Wählen **Sie OAuth Connection Einstellungen hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-273">Select **Add OAuth Connection Settings**.</span></span>  
<span data-ttu-id="91c55-274">In der folgenden Abbildung wird die entsprechende Auswahl auf der Ressourcenseite angezeigt:</span><span class="sxs-lookup"><span data-stu-id="91c55-274">The following image displays the corresponding selection in the resource page:</span></span>        
<span data-ttu-id="91c55-275">![SampleAppDemoBot-Konfiguration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)</span><span class="sxs-lookup"><span data-stu-id="91c55-275">![SampleAppDemoBot Configuration](~/assets/images/authentication/sample-app-demo-bot-configuration.png)</span></span> 

1. <span data-ttu-id="91c55-276">Füllen Sie das Formular wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="91c55-276">Complete the form as follows:</span></span>

    1. <span data-ttu-id="91c55-277">**Name**.</span><span class="sxs-lookup"><span data-stu-id="91c55-277">**Name**.</span></span> <span data-ttu-id="91c55-278">Geben Sie einen Namen für die Verbindung ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-278">Enter a name for the connection.</span></span> <span data-ttu-id="91c55-279">Sie verwenden diesen Namen in Ihrem Bot in der `appsettings.json` Datei.</span><span class="sxs-lookup"><span data-stu-id="91c55-279">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="91c55-280">Beispiel: *BotTeamsAuthADv2*.</span><span class="sxs-lookup"><span data-stu-id="91c55-280">For example *BotTeamsAuthADv2*.</span></span>
    1. <span data-ttu-id="91c55-281">**Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="91c55-281">**Service Provider**.</span></span> <span data-ttu-id="91c55-282">Wählen **Azure Active Directory v2 aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-282">Select **Azure Active Directory v2**.</span></span> <span data-ttu-id="91c55-283">Nachdem Sie diese Option ausgewählt haben, werden die Azure AD-spezifischen Felder angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91c55-283">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="91c55-284">**Client-ID**. Geben Sie in den obigen Schritten die Anwendungs-ID (Client-ID) ein, die Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-284">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="91c55-285">**Geheimer Clientgeheimnis**.</span><span class="sxs-lookup"><span data-stu-id="91c55-285">**Client secret**.</span></span> <span data-ttu-id="91c55-286">Geben Sie in den obigen Schritten den geheimen Schlüssel ein, den Sie für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-286">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="91c55-287">**Token Exchange URL**.</span><span class="sxs-lookup"><span data-stu-id="91c55-287">**Token Exchange URL**.</span></span> <span data-ttu-id="91c55-288">Lassen Sie dieses Feld leer.</span><span class="sxs-lookup"><span data-stu-id="91c55-288">Leave this blank.</span></span>
    1. <span data-ttu-id="91c55-289">**Mandanten-ID**, geben Sie die **Verzeichnis-ID (Mandant) ein,** die Sie zuvor für Ihre Azure-Identitäts-App aufgezeichnet haben oder je nach dem unterstützten Kontotyp, der beim Erstellen der Identitätsanbieter-App ausgewählt wurde. </span><span class="sxs-lookup"><span data-stu-id="91c55-289">**Tenant ID**, enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="91c55-290">So entscheiden Sie, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="91c55-290">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="91c55-291">Wenn Sie nur Konten in diesem Organisationsverzeichnis *(nur Microsoft - Einzelner* Mandant) oder Konten in einem beliebigen Organisationsverzeichnis *(Microsoft AAD-Verzeichnis - Mehr* mandant) ausgewählt haben, geben Sie die Mandanten-ID ein, die Sie zuvor für die AAD-App aufgezeichnet haben. </span><span class="sxs-lookup"><span data-stu-id="91c55-291">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="91c55-292">Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="91c55-292">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="91c55-293">Wenn Sie Konten in einem beliebigen Organisationsverzeichnis ausgewählt haben (Beliebiges AAD-Verzeichnis – Mehr mandanten- und persönliche  Microsoft-Konten, *z. B. Skype, Xbox, Outlook),* geben Sie das Wort common anstelle einer Mandanten-ID ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-293">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="91c55-294">Andernfalls überprüft die AAD-App den Mandanten, dessen ID ausgewählt wurde, und schließt persönliche Microsoft-Konten aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-294">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    1. <span data-ttu-id="91c55-295">Geben **Sie für** Bereiche eine durch Leerzeichen getrennte Liste von Graphberechtigungen ein, die für diese Anwendung erforderlich sind, z. B.: User.Read User.ReadBasic.All Mail.Read</span><span class="sxs-lookup"><span data-stu-id="91c55-295">For **Scopes**, enter a space-delimited list of graph permissions this application requires e.g.: User.Read User.ReadBasic.All Mail.Read</span></span> 

1. <span data-ttu-id="91c55-296">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="91c55-296">Select **Save**.</span></span>

### <a name="test-the-connection"></a><span data-ttu-id="91c55-297">Testen der Verbindung</span><span class="sxs-lookup"><span data-stu-id="91c55-297">Test the connection</span></span>

1. <span data-ttu-id="91c55-298">Wählen Sie den Verbindungseintrag aus, um die gerade erstellte Verbindung zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="91c55-298">Select the connection entry to open the connection you just created.</span></span>
1. <span data-ttu-id="91c55-299">Wählen **Sie oben im** Bereich Dienstanbieterverbindungseinstellung die Option Verbindung testen aus. </span><span class="sxs-lookup"><span data-stu-id="91c55-299">Select **Test Connection** at the top of the **Service Provider Connection Setting** panel.</span></span>
1. <span data-ttu-id="91c55-300">Wenn Sie dies zum ersten Mal tun, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="91c55-300">The first time you do this will open a new browser window asking you to select an account.</span></span> <span data-ttu-id="91c55-301">Wählen Sie das zu verwendende Aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-301">Select the one you want to use.</span></span>
1. <span data-ttu-id="91c55-302">Als Nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="91c55-302">Next, you'll be asked to allow to the identity provider to use your data (credentials).</span></span> <span data-ttu-id="91c55-303">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-303">The following image is an example:</span></span>

    ![teams bot auth connection string adv1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. <span data-ttu-id="91c55-305">Wählen Sie **Annehmen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-305">Select **Accept**.</span></span>
1. <span data-ttu-id="91c55-306">Dies sollte Sie dann auf eine Seite **"Testverbindung zu \<your-connection-name> Erfolgreich"** umleiten.</span><span class="sxs-lookup"><span data-stu-id="91c55-306">This should then redirect you to a **Test Connection to \<your-connection-name> Succeeded** page.</span></span> <span data-ttu-id="91c55-307">Aktualisieren Sie die Seite, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="91c55-307">Refresh the page if you get an error.</span></span> <span data-ttu-id="91c55-308">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-308">The following image is an example:</span></span>

  ![teams bots app auth connection str adv1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

<span data-ttu-id="91c55-310">Der Verbindungsname wird vom Botcode zum Abrufen von Benutzerauthentifizierungstoken verwendet.</span><span class="sxs-lookup"><span data-stu-id="91c55-310">The connection name is used by the bot code to retrieve user authentication tokens.</span></span>

## <a name="prepare-the-bot-sample-code"></a><span data-ttu-id="91c55-311">Vorbereiten des Bot-Beispielcodes</span><span class="sxs-lookup"><span data-stu-id="91c55-311">Prepare the bot sample code</span></span>

<span data-ttu-id="91c55-312">Wenn die vorläufigen Einstellungen fertig sind, konzentrieren wir uns auf die Erstellung des Bots, der in diesem Artikel verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="91c55-312">With the preliminary settings done, let's focus on the creation of the bot to use in this article.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="91c55-313">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="91c55-313">C#/.NET</span></span>](#tab/dotnet)

1. <span data-ttu-id="91c55-314">[Klonen Sie cs-auth-sample][teams-auth-bot-cs].</span><span class="sxs-lookup"><span data-stu-id="91c55-314">Clone [cs-auth-sample][teams-auth-bot-cs].</span></span>
1. <span data-ttu-id="91c55-315">Starten Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91c55-315">Launch Visual Studio.</span></span>
1. <span data-ttu-id="91c55-316">Wählen Sie auf **der Symbolleiste Datei -> Öffnen -> Project/Lösung** aus, und öffnen Sie das Bot-Projekt.</span><span class="sxs-lookup"><span data-stu-id="91c55-316">From the toolbar select **File -> Open -> Project/Solution** and open the bot project.</span></span>
1. <span data-ttu-id="91c55-317">In C# Update **appsettings.jswie** folgt:</span><span class="sxs-lookup"><span data-stu-id="91c55-317">In C# Update **appsettings.json** as follows:</span></span>

    - <span data-ttu-id="91c55-318">Legen `ConnectionName` Sie den Namen der Identitätsanbieterverbindung, die Sie der Botkanalregistrierung hinzugefügt haben, festgelegt.</span><span class="sxs-lookup"><span data-stu-id="91c55-318">Set `ConnectionName` to the name of the identity provider connection you added to the bot channel registration.</span></span> <span data-ttu-id="91c55-319">Der in diesem Beispiel verwendete Name ist *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="91c55-319">The name we used in this example is *BotTeamsAuthADv1*.</span></span>
    - <span data-ttu-id="91c55-320">Legen `MicrosoftAppId` Sie die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben, auf.</span><span class="sxs-lookup"><span data-stu-id="91c55-320">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="91c55-321">Legen `MicrosoftAppPassword` Sie den **Kundengeheimnis,** den Sie zum Zeitpunkt der Botkanalregistrierung gespeichert haben, auf.</span><span class="sxs-lookup"><span data-stu-id="91c55-321">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>

    <span data-ttu-id="91c55-322">Abhängig von den Zeichen in Ihrem Geheimen Bot müssen Sie möglicherweise das Kennwort als XML-Escapezeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="91c55-322">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="91c55-323">Beispielsweise müssen ampersands (&) als codiert `&amp;` werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-323">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. <span data-ttu-id="91c55-324">Navigieren Sie im Projektmappen-Explorer zu dem Ordner, öffnen und legen Sie diese und die `TeamsAppManifest` `manifest.json` `id` `botId` **Bot-App-ID,** die Sie zum Zeitpunkt der Botkanalregistrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-324">In the Solution Explorer, navigate to the `TeamsAppManifest` folder, open `manifest.json` and set `id` and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="javascript"></a>[<span data-ttu-id="91c55-325">JavaScript</span><span class="sxs-lookup"><span data-stu-id="91c55-325">JavaScript</span></span>](#tab/node-js)

1. <span data-ttu-id="91c55-326">Clone [node-auth-sample][teams-auth-bot-js].</span><span class="sxs-lookup"><span data-stu-id="91c55-326">Clone [node-auth-sample][teams-auth-bot-js].</span></span>
1. <span data-ttu-id="91c55-327">Navigieren Sie in einer Konsole zu dem Projekt:</span><span class="sxs-lookup"><span data-stu-id="91c55-327">In a console, navigate to the project:</span></span> </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. <span data-ttu-id="91c55-328">Installieren von Modulen</span><span class="sxs-lookup"><span data-stu-id="91c55-328">Install modules</span></span></br></br>
`npm install`
1. <span data-ttu-id="91c55-329">Aktualisieren Sie **die env-Konfiguration** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="91c55-329">Update the **.env** configuration as follows:</span></span>

    - <span data-ttu-id="91c55-330">Legen `MicrosoftAppId` Sie die **Bot-App-ID,** die Sie zum Zeitpunkt der Registrierung des Botkanals gespeichert haben, auf.</span><span class="sxs-lookup"><span data-stu-id="91c55-330">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="91c55-331">Legen `MicrosoftAppPassword` Sie den **Kundengeheimnis,** den Sie zum Zeitpunkt der Botkanalregistrierung gespeichert haben, auf.</span><span class="sxs-lookup"><span data-stu-id="91c55-331">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="91c55-332">Legen Sie `connectionName` den auf den Namen der Verbindung des Identitätsanbieters.</span><span class="sxs-lookup"><span data-stu-id="91c55-332">Set the `connectionName` to the name of the identity provider connection.</span></span>
    <span data-ttu-id="91c55-333">Abhängig von den Zeichen in Ihrem Geheimen Bot müssen Sie möglicherweise das Kennwort als XML-Escapezeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="91c55-333">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="91c55-334">Beispielsweise müssen ampersands (&) als codiert `&amp;` werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-334">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. <span data-ttu-id="91c55-335">Öffnen Sie im Ordner Ihre Microsoft App-ID und die `teamsAppManifest` Bot-App-ID, die Sie zum Zeitpunkt der Registrierung des `manifest.json` `id`  `botId` Botkanals gespeichert haben. </span><span class="sxs-lookup"><span data-stu-id="91c55-335">In the `teamsAppManifest` folder, open `manifest.json` and set `id`  to your **Microsoft App ID** and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="python"></a>[<span data-ttu-id="91c55-336">Python</span><span class="sxs-lookup"><span data-stu-id="91c55-336">Python</span></span>](#tab/python)

1. <span data-ttu-id="91c55-337">[Klonen Sie py-auth-sample][teams-auth-bot-py] aus dem github-Repository.</span><span class="sxs-lookup"><span data-stu-id="91c55-337">Clone [py-auth-sample][teams-auth-bot-py] from the github repository.</span></span>
1. <span data-ttu-id="91c55-338">Update **config.py**:</span><span class="sxs-lookup"><span data-stu-id="91c55-338">Update **config.py**:</span></span>

    - <span data-ttu-id="91c55-339">Legen `ConnectionName` Sie auf den Namen der OAuth-Verbindungseinstellung, die Sie Ihrem Bot hinzugefügt haben, festgelegt.</span><span class="sxs-lookup"><span data-stu-id="91c55-339">Set `ConnectionName` to the name of the OAuth connection setting you added to your bot.</span></span>
    - <span data-ttu-id="91c55-340">Legen Sie und die App-ID und den geheimen `MicrosoftAppId` App-Schlüssel Ihres `MicrosoftAppPassword` Bots.</span><span class="sxs-lookup"><span data-stu-id="91c55-340">Set `MicrosoftAppId` and `MicrosoftAppPassword` to your bot's app ID and app secret.</span></span>

      <span data-ttu-id="91c55-341">Abhängig von den Zeichen in Ihrem Geheimen Bot müssen Sie möglicherweise das Kennwort als XML-Escapezeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="91c55-341">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="91c55-342">Beispielsweise müssen ampersands (&) als codiert `&amp;` werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-342">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a><span data-ttu-id="91c55-343">Bereitstellen des Bots in Azure</span><span class="sxs-lookup"><span data-stu-id="91c55-343">Deploy the bot to Azure</span></span>

<span data-ttu-id="91c55-344">Führen Sie zum Bereitstellen des Bots die Schritte in der Bereitstellung [Ihres Bots in Azure aus.](https://aka.ms/azure-bot-deployment-cli)</span><span class="sxs-lookup"><span data-stu-id="91c55-344">To deploy the bot, follow the steps in the how to [Deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span></span>

<span data-ttu-id="91c55-345">Alternativ können Sie im Visual Studio die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="91c55-345">Alternatively, while in Visual Studio, you can follow these steps:</span></span>

1. <span data-ttu-id="91c55-346">Wählen Visual Studio *Projektmappen-Explorer* den Projektnamen aus, und halten Sie ihn fest (oder klicken Sie mit der rechten Maustaste).</span><span class="sxs-lookup"><span data-stu-id="91c55-346">In Visual Studio *Solution Explorer* select and hold (or right-click) the project name.</span></span>
1. <span data-ttu-id="91c55-347">Wählen Sie im Dropdownmenü Veröffentlichen **aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-347">In the drop-down menu, select **Publish**.</span></span>
1. <span data-ttu-id="91c55-348">Wählen Sie im angezeigten Fenster den Link **Neu** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-348">In the displayed window, select the **New** link.</span></span>
1. <span data-ttu-id="91c55-349">Wählen Sie im Dialogfeld auf der linken Seite **App-Dienst** und **rechts Neu** erstellen aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-349">In the dialog window, select **App Service** on the left and **Create New** on the right.</span></span>
1. <span data-ttu-id="91c55-350">Wählen Sie die **Schaltfläche Veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-350">Select the **Publish** button.</span></span>
1. <span data-ttu-id="91c55-351">Geben Sie im nächsten Dialogfeld die erforderlichen Informationen ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-351">In the next dialog window, enter the required information.</span></span> <span data-ttu-id="91c55-352">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-352">The following is an example:</span></span>

   ![auth-app-service](../../../assets/images/authentication/auth-bot-app-service.png)

1. <span data-ttu-id="91c55-354">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-354">Select **Create**.</span></span>
1. <span data-ttu-id="91c55-355">Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte sie in der Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91c55-355">If the deployment completes successfully, you should see it reflected in Visual Studio.</span></span> <span data-ttu-id="91c55-356">Darüber hinaus wird in Ihrem Standardbrowser eine Seite mit der Meldung *angezeigt, dass Ihr Bot bereit ist!*.</span><span class="sxs-lookup"><span data-stu-id="91c55-356">Moreover, a page is displayed in your default browser saying *Your bot is ready!*.</span></span> <span data-ttu-id="91c55-357">Die URL ähnelt der folgende: `https://botteamsauth.azurewebsites.net/` .</span><span class="sxs-lookup"><span data-stu-id="91c55-357">The URL will be similar to this: `https://botteamsauth.azurewebsites.net/`.</span></span> <span data-ttu-id="91c55-358">Speichern Sie es in einer Datei.</span><span class="sxs-lookup"><span data-stu-id="91c55-358">Save it to a file.</span></span>
1. <span data-ttu-id="91c55-359">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="91c55-359">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="91c55-360">Überprüfen Sie Ihre Ressourcengruppe, der Bot sollte zusammen mit den anderen Ressourcen aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-360">Check your resource group, the bot should be listed along with the other resources.</span></span> <span data-ttu-id="91c55-361">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-361">The following image is an example:</span></span>

    ![teams-bot-auth-app-service-group](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. <span data-ttu-id="91c55-363">Wählen Sie in der Ressourcengruppe den Namen der Botkanalregistrierung (Link) aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-363">In the resource group, select the bot channel registration name (link).</span></span>
1. <span data-ttu-id="91c55-364">Wählen Sie im linken Bereich die **Option Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-364">In the left panel, select **Settings**.</span></span>
1. <span data-ttu-id="91c55-365">Geben Sie **im Feld** Messagingendpunkt die oben erhaltene URL ein, gefolgt von `api/messages` .</span><span class="sxs-lookup"><span data-stu-id="91c55-365">In the **Messaging endpoint** box, enter the URL obtained above followed by `api/messages`.</span></span> <span data-ttu-id="91c55-366">Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="91c55-366">This is an example: `https://botteamsauth.azurewebsites.net/api/messages`.</span></span>
1. <span data-ttu-id="91c55-367">Wählen Sie **oben** links die Schaltfläche Speichern aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-367">Select the **Save** button in the upper left.</span></span>

## <a name="test-the-bot-using-the-emulator"></a><span data-ttu-id="91c55-368">Testen des Bots mithilfe des Emulators</span><span class="sxs-lookup"><span data-stu-id="91c55-368">Test the bot using the Emulator</span></span>

<span data-ttu-id="91c55-369">Wenn Sie dies noch nicht getan haben, installieren Sie [die Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme).</span><span class="sxs-lookup"><span data-stu-id="91c55-369">If you haven't done it already, install the [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme).</span></span> <span data-ttu-id="91c55-370">Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span><span class="sxs-lookup"><span data-stu-id="91c55-370">See also [Debug with the Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span></span>

<span data-ttu-id="91c55-371">Damit die Botbeispielanmeldung funktioniert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-371">In order for the bot sample login to work you must configure the Emulator as shown below.</span></span>

### <a name="configure-the-emulator-for-authentication"></a><span data-ttu-id="91c55-372">Konfigurieren des Emulators für die Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="91c55-372">Configure the Emulator for authentication</span></span>

<span data-ttu-id="91c55-373">Wenn für einen Bot die Authentifizierung erforderlich ist, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-373">If a bot requires authentication, you must configure the Emulator as shown below.</span></span>

1. <span data-ttu-id="91c55-374">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="91c55-374">Start the Emulator.</span></span>
1. <span data-ttu-id="91c55-375">Wählen Sie im Emulator das Zahnradsymbol &#9881; links unten oder die Registerkarte **Emulator Einstellungen** oben rechts aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-375">In the Emulator, select the gear icon &#9881; in the bottom left, or the **Emulator Settings** tab in the upper right.</span></span>
1. <span data-ttu-id="91c55-376">Aktivieren Sie das Kontrollkästchen Verwenden von Authentifizierungstoken der Version **1.0**.</span><span class="sxs-lookup"><span data-stu-id="91c55-376">Check the box by **Use version 1.0 authentication tokens**.</span></span>
1. <span data-ttu-id="91c55-377">Geben Sie den lokalen Pfad zum **ngrok-Tool** ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-377">Enter the local path to the **ngrok** tool.</span></span> <span data-ttu-id="91c55-378">*Weitere* Informationen finden Bot Framework Emulator /ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span><span class="sxs-lookup"><span data-stu-id="91c55-378">*See* the Bot Framework Emulator / ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span></span> <span data-ttu-id="91c55-379">Weitere Toolinformationen finden Sie unter [ngrok](https://ngrok.com/).</span><span class="sxs-lookup"><span data-stu-id="91c55-379">For more tool information, see [ngrok](https://ngrok.com/).</span></span>
1. <span data-ttu-id="91c55-380">Aktivieren Sie das Kontrollkästchen **durch Ausführen von ngrok, wenn der Emulator gestartet wird.**</span><span class="sxs-lookup"><span data-stu-id="91c55-380">Check the box by **Run ngrok when the Emulator starts up**.</span></span>
1. <span data-ttu-id="91c55-381">Wählen Sie die **Schaltfläche Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-381">Select the **Save** button.</span></span>

<span data-ttu-id="91c55-382">Wenn der Bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, die der Benutzer zum Anmelden beim Authentifizierungsanbieter verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="91c55-382">When the bot displays a sign-in card and the user selects the sign-in button, the Emulator opens a page that the user can use to sign in with the authentication provider.</span></span>
<span data-ttu-id="91c55-383">Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den Bot.</span><span class="sxs-lookup"><span data-stu-id="91c55-383">Once the user does so, the provider generates a user token and sends it to the bot.</span></span> <span data-ttu-id="91c55-384">Danach kann der Bot im Namen des Benutzers handeln.</span><span class="sxs-lookup"><span data-stu-id="91c55-384">After that, the bot can act on behalf of the user.</span></span>

### <a name="test-the-bot-locally"></a><span data-ttu-id="91c55-385">Lokal testen des Bots</span><span class="sxs-lookup"><span data-stu-id="91c55-385">Test the bot locally</span></span>

<span data-ttu-id="91c55-386">Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die eigentlichen Bottests durchführen.</span><span class="sxs-lookup"><span data-stu-id="91c55-386">After you have configured the authentication mechanism, you can perform the actual bot testing.</span></span>  

1. <span data-ttu-id="91c55-387">Führen Sie das Botbeispiel lokal auf Ihrem Computer aus, z. B. Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91c55-387">Run the bot sample locally on your machine, via Visual Studio for example.</span></span>
1. <span data-ttu-id="91c55-388">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="91c55-388">Start the Emulator.</span></span>
1. <span data-ttu-id="91c55-389">Wählen Sie die **Schaltfläche Bot öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-389">Select the **Open bot** button.</span></span>
1. <span data-ttu-id="91c55-390">Geben Sie **in der Bot-URL** die lokale URL des Bots ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-390">In the **Bot URL**, enter the bot's local URL.</span></span> <span data-ttu-id="91c55-391">In der Regel `http://localhost:3978/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="91c55-391">Usually, `http://localhost:3978/api/messages`.</span></span>
1. <span data-ttu-id="91c55-392">Geben Sie **in der Microsoft App-ID** die App-ID des Bots von `appsettings.json` ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-392">In the **Microsoft App ID** enter the bot's app ID from `appsettings.json`.</span></span>
1. <span data-ttu-id="91c55-393">Geben Sie **im Microsoft App-Kennwort** das App-Kennwort des Bots aus der `appsettings.json` ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-393">In the **Microsoft App password** enter the bot's app password from the `appsettings.json`.</span></span>
1. <span data-ttu-id="91c55-394">Wählen **Sie Verbinden** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-394">Select **Connect**.</span></span>
1. <span data-ttu-id="91c55-395">Nachdem der Bot ausgeführt wurde, geben Sie einen beliebigen Text ein, um die Anmeldekarte anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="91c55-395">After the bot is up and running, enter any text to display the sign-in card.</span></span>
1. <span data-ttu-id="91c55-396">Wählen Sie die Schaltfläche **Anmelden** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-396">Select the **Sign in** button.</span></span>
1. <span data-ttu-id="91c55-397">Ein Popupdialogfeld wird angezeigt, um open **URL zu bestätigen.**</span><span class="sxs-lookup"><span data-stu-id="91c55-397">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="91c55-398">Dadurch kann der Benutzer des Bots (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-398">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="91c55-399">Wählen Sie **Bestätigen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-399">Select **Confirm**.</span></span>
1. <span data-ttu-id="91c55-400">Wenn Sie gefragt werden, wählen Sie das Konto des entsprechenden Benutzers aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-400">If asked, select the applicable user's account.</span></span>
1. <span data-ttu-id="91c55-401">Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="91c55-401">Depending which configuration you used for the Emulator, you get one of the following:</span></span>
    1. <span data-ttu-id="91c55-402">**Verwenden des Anmeldeüberprüfungscodes**</span><span class="sxs-lookup"><span data-stu-id="91c55-402">**Using sign-in verification code**</span></span>  
      <span data-ttu-id="91c55-403">&#x2713; Ein Fenster wird geöffnet, in dem der Überprüfungscode angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-403">&#x2713; A window is opened displaying the validation code.</span></span>  
      <span data-ttu-id="91c55-404">&#x2713; Sie den Validierungscode kopieren und in das Chatfeld eingeben, um die Anmeldung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="91c55-404">&#x2713; Copy and enter the validation code into the chat box to complete the sign-in.</span></span>
    1. <span data-ttu-id="91c55-405">**Verwenden von Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="91c55-405">**Using authentication tokens**.</span></span>  
      <span data-ttu-id="91c55-406">&#x2713; Sie sind basierend auf Ihren Anmeldeinformationen angemeldet.</span><span class="sxs-lookup"><span data-stu-id="91c55-406">&#x2713; You're logged in based on your credentials.</span></span>

    <span data-ttu-id="91c55-407">Die folgende Abbildung ist ein Beispiel für die Bot-UI, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="91c55-407">The following image is an example of the bot UI after you've logged in:</span></span>

    ![Authentifizierungsbot-Anmeldeemulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. <span data-ttu-id="91c55-409">Wenn Sie **Ja auswählen,** wenn der Bot fragt, ob Sie Ihr Token anzeigen *möchten?*, erhalten Sie eine Antwort wie die folgende:</span><span class="sxs-lookup"><span data-stu-id="91c55-409">If you select **Yes** when the bot asks *Would you like to view your token?*, you'll get a response similar to the following:</span></span>

    ![Authentifizierungsbot-Anmeldeemulatortoken](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. <span data-ttu-id="91c55-411">Geben **Sie abmelden** in das Eingabechatfeld ein, um sich abmelden zu können. Dadurch wird das Benutzertoken veröffentlicht, und der Bot kann erst dann in Ihrem Namen handeln, wenn Sie sich erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="91c55-411">Enter **logout** in the input chat box to sign out. This releases the user token, and the bot won't be able to act on your behalf until you sign in again.</span></span>

> [!NOTE]
> <span data-ttu-id="91c55-412">Die Botauthentifizierung erfordert die Verwendung des **Bot Connector Service**.</span><span class="sxs-lookup"><span data-stu-id="91c55-412">Bot authentication requires use of the **Bot Connector Service**.</span></span> <span data-ttu-id="91c55-413">Der Dienst zugrifft auf die Registrierungsinformationen für den Bot.</span><span class="sxs-lookup"><span data-stu-id="91c55-413">The service accesses the bot channels registration information for your bot.</span></span>

## <a name="test-the-deployed-bot"></a><span data-ttu-id="91c55-414">Testen des bereitgestellten Bots</span><span class="sxs-lookup"><span data-stu-id="91c55-414">Test the deployed bot</span></span>

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. <span data-ttu-id="91c55-415">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="91c55-415">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="91c55-416">Suchen Sie nach Ihrer Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="91c55-416">Find your resource group.</span></span>
1. <span data-ttu-id="91c55-417">Wählen Sie den Ressourcenlink aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-417">Select the resource link.</span></span> <span data-ttu-id="91c55-418">Die Ressourcenseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91c55-418">The resource page is displayed.</span></span>
1. <span data-ttu-id="91c55-419">Wählen Sie auf der Ressourcenseite **Test in Web Chat aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-419">In the resource page, select **Test in Web Chat**.</span></span> <span data-ttu-id="91c55-420">Der Bot startet und zeigt die vordefinierten Begrüßungen an.</span><span class="sxs-lookup"><span data-stu-id="91c55-420">The bot starts and displays the predefined greetings.</span></span>
1. <span data-ttu-id="91c55-421">Geben Sie im Chatfeld alles ein.</span><span class="sxs-lookup"><span data-stu-id="91c55-421">Type anything in the chat box.</span></span>
1. <span data-ttu-id="91c55-422">Aktivieren Sie **das Feld Anmelden.**</span><span class="sxs-lookup"><span data-stu-id="91c55-422">Select the **Sign in** box.</span></span>
1. <span data-ttu-id="91c55-423">Ein Popupdialogfeld wird angezeigt, um open **URL zu bestätigen.**</span><span class="sxs-lookup"><span data-stu-id="91c55-423">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="91c55-424">Dadurch kann der Benutzer des Bots (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-424">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="91c55-425">Wählen Sie **Bestätigen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-425">Select **Confirm**.</span></span>
1. <span data-ttu-id="91c55-426">Wenn Sie gefragt werden, wählen Sie das Konto des entsprechenden Benutzers aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-426">If asked, select the applicable user's account.</span></span>
    <span data-ttu-id="91c55-427">Die folgende Abbildung ist ein Beispiel für die Bot-UI, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="91c55-427">The following image is an example of the bot UI after you have logged in:</span></span>

    ![Bereitgestellte Authentifizierungsbotanmeldung](../../../assets/images/authentication/auth-bot-login-deployed.PNG)<span data-ttu-id="91c55-429">.</span><span class="sxs-lookup"><span data-stu-id="91c55-429">.</span></span>

1. <span data-ttu-id="91c55-430">Wählen Sie die **Schaltfläche Ja** aus, um Ihr Authentifizierungstoken anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="91c55-430">Select the **Yes** button to display your authentication token.</span></span> <span data-ttu-id="91c55-431">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-431">The following image is an example:</span></span>

    ![Bereitgestelltes Token für die Authentifizierungsbotanmeldung](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG)<span data-ttu-id="91c55-433">.</span><span class="sxs-lookup"><span data-stu-id="91c55-433">.</span></span>

1. <span data-ttu-id="91c55-434">Geben Sie abmelden ein, um sich abmelden zu können.</span><span class="sxs-lookup"><span data-stu-id="91c55-434">Enter logout to sign out.</span></span>

    ![Authentifizierungsbot bereitgestellte Anmeldung](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> <span data-ttu-id="91c55-436">Wenn Bei der Anmeldung Probleme auftreten, versuchen Sie, die Verbindung wie in den vorherigen Schritten beschrieben erneut zu testen.</span><span class="sxs-lookup"><span data-stu-id="91c55-436">If you're having problems signing in, try to test the connection again as described in the previous steps.</span></span> <span data-ttu-id="91c55-437">Dadurch könnte das Authentifizierungstoken neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-437">This could recreate the authentication token.</span></span>
> <span data-ttu-id="91c55-438">Mit dem Bot Framework Web Chat-Client in Azure müssen Sie sich möglicherweise mehrmals anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="91c55-438">With the Bot Framework Web Chat client in Azure, you may need to sign in several times before the authentication is established correctly.</span></span>

## <a name="install-and-test-the-bot-in-teams"></a><span data-ttu-id="91c55-439">Installieren und Testen des Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="91c55-439">Install and test the bot in Teams</span></span>

1. <span data-ttu-id="91c55-440">Stellen Sie in Ihrem Bot-Projekt sicher, dass `TeamsAppManifest` der Ordner zusammen mit einer und `manifest.json` `outline.png` -Dateien `color.png` enthält.</span><span class="sxs-lookup"><span data-stu-id="91c55-440">In your bot project, ensure that the `TeamsAppManifest` folder contains the `manifest.json` along with an `outline.png` and `color.png` files.</span></span>
1. <span data-ttu-id="91c55-441">Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner.</span><span class="sxs-lookup"><span data-stu-id="91c55-441">In Solution Explorer, navigate to the `TeamsAppManifest` folder.</span></span> <span data-ttu-id="91c55-442">Bearbeiten `manifest.json` Sie, indem Sie die folgenden Werte zuweisen:</span><span class="sxs-lookup"><span data-stu-id="91c55-442">Edit `manifest.json` by assigning the following values:</span></span>
    1. <span data-ttu-id="91c55-443">Stellen Sie sicher, dass die **Bot-App-ID,** die Sie zum Zeitpunkt der Botkanalregistrierung erhalten haben, und zugewiesen `id` `botId` ist.</span><span class="sxs-lookup"><span data-stu-id="91c55-443">Ensure that the **bot App ID** you received at the time of the bot channel registration is assigned to `id` and `botId`.</span></span>
    1. <span data-ttu-id="91c55-444">Weisen Sie diesen Wert zu: `validDomains: [ "token.botframework.com" ]` .</span><span class="sxs-lookup"><span data-stu-id="91c55-444">Assign this value: `validDomains: [ "token.botframework.com" ]`.</span></span>
1. <span data-ttu-id="91c55-445">Wählen **Sie** die `manifest.json` , und `outline.png` -Dateien aus, und `color.png` zipen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="91c55-445">Select and **zip** the `manifest.json`, `outline.png`, and `color.png` files.</span></span>
1. <span data-ttu-id="91c55-446">Öffnen **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="91c55-446">Open **Microsoft Teams**.</span></span>
1. <span data-ttu-id="91c55-447">Wählen Sie im linken Bereich unten das **Symbol Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-447">In the left panel, at the bottom, select the **Apps icon**.</span></span>
1. <span data-ttu-id="91c55-448">Wählen Sie unten im rechten Bereich die Option **Hochladen benutzerdefinierte App aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-448">In the right panel, at the bottom, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="91c55-449">Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.</span><span class="sxs-lookup"><span data-stu-id="91c55-449">Navigate to the `TeamsAppManifest` folder and upload the zipped manifest.</span></span>
<span data-ttu-id="91c55-450">Der folgende Assistent wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="91c55-450">The following wizard is displayed:</span></span>

    ![Hochladen von Authentifizierungsbotteams](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. <span data-ttu-id="91c55-452">Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="91c55-452">Select the **Add to a team** button.</span></span>
1. <span data-ttu-id="91c55-453">Wählen Sie im nächsten Fenster das Team aus, in dem Sie den Bot verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="91c55-453">In the next window, select the team where you want to use the bot.</span></span>
1. <span data-ttu-id="91c55-454">Wählen Sie die **Schaltfläche Bot einrichten** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-454">Select the **Set up a bot** button.</span></span>
1. <span data-ttu-id="91c55-455">Wählen Sie die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) im linken Bereich aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-455">Select the three dots (&#x25cf;&#x25cf;&#x25cf;) in the left panel.</span></span> <span data-ttu-id="91c55-456">Wählen Sie dann das **Symbol App Studio** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-456">Then select the **App Studio** icon.</span></span>
1. <span data-ttu-id="91c55-457">Wählen Sie die **Registerkarte Manifest-Editor** aus. Das Symbol für den hochgeladenen Bot sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-457">Select the **Manifest editor** tab. You should see the icon for the bot you uploaded.</span></span>
1. <span data-ttu-id="91c55-458">Außerdem sollten Sie in der Lage sein, den Bot als Kontakt in der Chatliste aufgeführt zu sehen, die Sie zum Austauschen von Nachrichten mit dem Bot verwenden können.</span><span class="sxs-lookup"><span data-stu-id="91c55-458">Also, you should be able to see the bot listed as a contact in the chat list that you can use to exchange messages with the bot.</span></span>

### <a name="testing-the-bot-locally-in-teams"></a><span data-ttu-id="91c55-459">Testen des Bots lokal in Teams</span><span class="sxs-lookup"><span data-stu-id="91c55-459">Testing the bot locally in Teams</span></span>

<span data-ttu-id="91c55-460">Microsoft Teams ein vollständig cloudbasiertes Produkt ist, müssen alle Dienste, auf die zugegriffen wird, über HTTPS-Endpunkte in der Cloud verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="91c55-460">Microsoft Teams is an entirely cloud-based product, it requires all services it accesses to be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="91c55-461">Damit der Bot (unser Beispiel) in Teams funktioniert, müssen Sie den Code entweder in der Cloud Ihrer Wahl veröffentlichen oder  über ein Tunneltool extern auf eine lokal ausgeführte Instanz zugriffen.</span><span class="sxs-lookup"><span data-stu-id="91c55-461">Therefore, to enable the bot (our sample) to work in Teams, you need to either publish the code to the cloud of your choice, or make a locally running instance externally accessible via a **tunneling** tool.</span></span> <span data-ttu-id="91c55-462">Wir empfehlen  [ngrok](https://ngrok.com/download), das eine extern adressierbare URL für einen Port erstellt, den Sie lokal auf Ihrem Computer öffnen.</span><span class="sxs-lookup"><span data-stu-id="91c55-462">We recommend  [ngrok](https://ngrok.com/download), which creates an externally addressable URL for a port you open locally on your machine.</span></span>
<span data-ttu-id="91c55-463">Führen Sie die folgenden Schritte aus, um ngrok in Vorbereitung auf die lokale Ausführung Microsoft Teams App zu einrichten:</span><span class="sxs-lookup"><span data-stu-id="91c55-463">To set up ngrok in preparation for running your Microsoft Teams app locally, follow these steps:</span></span>

1. <span data-ttu-id="91c55-464">Wechseln Sie in einem Terminalfenster zu dem Verzeichnis, in dem Sie installiert `ngrok.exe` haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-464">In a terminal window, go the directory where you have `ngrok.exe` installed.</span></span> <span data-ttu-id="91c55-465">Wir empfehlen, den Pfad der *Umgebungsvariablen* so zu legen, dass er darauf verweisen kann.</span><span class="sxs-lookup"><span data-stu-id="91c55-465">We suggest setting the *environment variable* path to point to it.</span></span>
1. <span data-ttu-id="91c55-466">Führen Sie z. `ngrok http 3978 --host-header=localhost:3978` B. aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-466">Run, for example, `ngrok http 3978 --host-header=localhost:3978`.</span></span> <span data-ttu-id="91c55-467">Ersetzen Sie die Portnummer nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="91c55-467">Replace the port number as needed.</span></span>
<span data-ttu-id="91c55-468">Dadurch wird ngrok gestartet, um den von Ihnen angegebenen Port abzuhören.</span><span class="sxs-lookup"><span data-stu-id="91c55-468">This launches ngrok to listen on the port you specify.</span></span> <span data-ttu-id="91c55-469">Im Gegenzug erhalten Sie eine extern adressierbare URL, die so lange gültig ist, wie ngrok ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-469">In return, it gives you an externally addressable URL, valid for as long as ngrok is running.</span></span> <span data-ttu-id="91c55-470">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-470">The following image is an example:</span></span>

    ![teams bot app auth connection string adv1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG)<span data-ttu-id="91c55-472">.</span><span class="sxs-lookup"><span data-stu-id="91c55-472">.</span></span>

1. <span data-ttu-id="91c55-473">Kopieren Sie die Weiterleitungs-HTTPS-Adresse.</span><span class="sxs-lookup"><span data-stu-id="91c55-473">Copy the forwarding HTTPS address.</span></span> <span data-ttu-id="91c55-474">Sie sollte wie folgt sein: `https://dea822bf.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="91c55-474">It should be similar to the following: `https://dea822bf.ngrok.io/`.</span></span>
1. <span data-ttu-id="91c55-475">Append, `/api/messages` um zu erhalten `https://dea822bf.ngrok.io/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="91c55-475">Append `/api/messages` to obtain `https://dea822bf.ngrok.io/api/messages`.</span></span> <span data-ttu-id="91c55-476">Dies ist der **Nachrichtenendpunkt** für den Bot, der lokal auf Ihrem Computer ausgeführt wird und über das Web in einem Chat in einem Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="91c55-476">This is the **messages endpoint** for the bot running locally on your machine and reachable over the web in a chat in Microsoft Teams.</span></span>
1. <span data-ttu-id="91c55-477">Ein letzter Schritt besteht im Aktualisieren des Nachrichtenendpunkts des bereitgestellten Bots.</span><span class="sxs-lookup"><span data-stu-id="91c55-477">One final step to perform is to update the messages endpoint of the deployed bot.</span></span> <span data-ttu-id="91c55-478">Im Beispiel haben wir den Bot in Azure bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="91c55-478">In the example, we deployed the bot in Azure.</span></span> <span data-ttu-id="91c55-479">Führen wir also die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="91c55-479">So \*\*let's perform these steps:</span></span>
    1. <span data-ttu-id="91c55-480">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="91c55-480">In your browser navigate to the [**Azure portal**][azure-portal].</span></span>
    1. <span data-ttu-id="91c55-481">Wählen Sie Ihre **Bot-Kanal-Registrierung aus.**</span><span class="sxs-lookup"><span data-stu-id="91c55-481">Select your **Bot Channel Registration**.</span></span>
    1. <span data-ttu-id="91c55-482">Wählen Sie im linken Bereich die **Option Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="91c55-482">In the left panel, select **Settings**.</span></span>
    1. <span data-ttu-id="91c55-483">Geben Sie im rechten  Bereich im Feld Messagingendpunkt die ngrok-URL ein, in unserem Beispiel `https://dea822bf.ngrok.io/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="91c55-483">In the right panel, in the **Messaging endpoint** box, enter the ngrok URL, in our example, `https://dea822bf.ngrok.io/api/messages`.</span></span>
1. <span data-ttu-id="91c55-484">Starten Sie Ihren Bot lokal, z. B. im Visual Studio Debugmodus.</span><span class="sxs-lookup"><span data-stu-id="91c55-484">Start your bot locally, for example in Visual Studio debug mode.</span></span>
1. <span data-ttu-id="91c55-485">Testen Sie den Bot während der lokalen Ausführung mithilfe des TestWebchats des **Bot Framework-Portals.**</span><span class="sxs-lookup"><span data-stu-id="91c55-485">Test the bot while running locally using the Bot Framework portal's **Test Web chat**.</span></span> <span data-ttu-id="91c55-486">Wie beim Emulator können Sie bei diesem Test nicht auf Teams funktionen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="91c55-486">Like the Emulator, this test doesn't allow you to access Teams-specific functionality.</span></span>
1. <span data-ttu-id="91c55-487">Im Terminalfenster, `ngrok` in dem ausgeführt wird, wird der HTTP-Datenverkehr zwischen dem Bot und dem Webchatclient angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91c55-487">In the terminal window where `ngrok` is running you can see HTTP traffic between the bot and the web chat client.</span></span> <span data-ttu-id="91c55-488">Wenn Sie eine detailliertere Ansicht wünschen, geben Sie in ein Browserfenster ein, das Sie aus `http://127.0.0.1:4040` dem vorherigen Terminalfenster erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="91c55-488">If you want a more detailed view, in a browser window enter `http://127.0.0.1:4040` you obtained from the previous terminal window.</span></span> <span data-ttu-id="91c55-489">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="91c55-489">The following image is an example:</span></span>

    ![auth bot teams ngrok testing](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png)<span data-ttu-id="91c55-491">.</span><span class="sxs-lookup"><span data-stu-id="91c55-491">.</span></span>

> [!NOTE]
> <span data-ttu-id="91c55-492">Wenn Sie ngrok beenden und neu starten, ändert sich die URL.</span><span class="sxs-lookup"><span data-stu-id="91c55-492">If you stop and restart ngrok, the URL changes.</span></span> <span data-ttu-id="91c55-493">Um ngrok in Ihrem Projekt zu verwenden und je nach den von Ihnen verwendeten Funktionen, müssen Sie alle URL-Verweise aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="91c55-493">To use ngrok in your project, and depending on the capabilities you're using, you must update all URL references.</span></span>
 

## <a name="additional-information"></a><span data-ttu-id="91c55-494">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="91c55-494">Additional information</span></span>

### <a name="teamsappmanifestmanifestjson"></a><span data-ttu-id="91c55-495">TeamsAppManifest/manifest.json</span><span class="sxs-lookup"><span data-stu-id="91c55-495">TeamsAppManifest/manifest.json</span></span>

<span data-ttu-id="91c55-496">Dieses Manifest enthält Informationen, die von Microsoft Teams zum Herstellen einer Verbindung mit dem Bot benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="91c55-496">This manifest contains information needed by Microsoft Teams to connect with the bot.</span></span>  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
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

<span data-ttu-id="91c55-497">Bei der Authentifizierung verhält Teams sich etwas anders als andere Kanäle, wie unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="91c55-497">With authentication, Teams behaves slightly differently than other channels, as explained below.</span></span>

### <a name="handling-invoke-activity"></a><span data-ttu-id="91c55-498">Behandeln von Aufrufen von Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="91c55-498">Handling Invoke Activity</span></span>

<span data-ttu-id="91c55-499">Eine **Invoke-Aktivität** wird an den Bot gesendet und nicht an die Ereignisaktivität, die von anderen Kanälen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-499">An **Invoke Activity** is sent to the bot rather than the Event Activity used by other channels.</span></span>
<span data-ttu-id="91c55-500">Dazu wird der **ActivityHandler unterklassigiert.**</span><span class="sxs-lookup"><span data-stu-id="91c55-500">This is done by sub-classing the **ActivityHandler**.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="91c55-501">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="91c55-501">C#/.NET</span></span>](#tab/dotnet-sample)

<span data-ttu-id="91c55-502">**Bots/DialogBot.cs**</span><span class="sxs-lookup"><span data-stu-id="91c55-502">**Bots/DialogBot.cs**</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

<span data-ttu-id="91c55-503">**Bots/TeamsBot.cs**</span><span class="sxs-lookup"><span data-stu-id="91c55-503">**Bots/TeamsBot.cs**</span></span>

<span data-ttu-id="91c55-504">Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-504">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a><span data-ttu-id="91c55-505">TeamsActivityHandler.cs</span><span class="sxs-lookup"><span data-stu-id="91c55-505">TeamsActivityHandler.cs</span></span>

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

# <a name="javascript"></a>[<span data-ttu-id="91c55-506">JavaScript</span><span class="sxs-lookup"><span data-stu-id="91c55-506">JavaScript</span></span>](#tab/node-js-dialog-sample)

<span data-ttu-id="91c55-507">**bots/dialogBot.js**</span><span class="sxs-lookup"><span data-stu-id="91c55-507">**bots/dialogBot.js**</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

<span data-ttu-id="91c55-508">**bots/teamsBot.js**</span><span class="sxs-lookup"><span data-stu-id="91c55-508">**bots/teamsBot.js**</span></span>

<span data-ttu-id="91c55-509">Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-509">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

<span data-ttu-id="91c55-510">**dialogs/mainDialog.js**</span><span class="sxs-lookup"><span data-stu-id="91c55-510">**dialogs/mainDialog.js**</span></span>

<span data-ttu-id="91c55-511">Starten Sie in einem Dialogfeldschritt die OAuth-Eingabeaufforderung, in der der Benutzer zur `beginDialog` Anmeldung aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-511">Within a dialog step, use `beginDialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="91c55-512">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Tokenantwortereignis, ohne dass der Benutzer dazu aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-512">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="91c55-513">Andernfalls wird der Benutzer zur Anmeldung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="91c55-513">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="91c55-514">Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht, sich zu anmelden.</span><span class="sxs-lookup"><span data-stu-id="91c55-514">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

<span data-ttu-id="91c55-515">Überprüfen Sie im folgenden Dialogfeldschritt, ob ein Token im Ergebnis des vorherigen Schritts enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="91c55-515">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="91c55-516">Wenn der Wert nicht null ist, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="91c55-516">If it is not null, the user successfully signed in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

<span data-ttu-id="91c55-517">**bots/logoutDialog.js**</span><span class="sxs-lookup"><span data-stu-id="91c55-517">**bots/logoutDialog.js**</span></span>

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[<span data-ttu-id="91c55-518">Python</span><span class="sxs-lookup"><span data-stu-id="91c55-518">Python</span></span>](#tab/python-sample)

<span data-ttu-id="91c55-519">**bots/dialog_bot.py**</span><span class="sxs-lookup"><span data-stu-id="91c55-519">**bots/dialog_bot.py**</span></span>

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

<span data-ttu-id="91c55-520">**bots/teams_bot.py**</span><span class="sxs-lookup"><span data-stu-id="91c55-520">**bots/teams_bot.py**</span></span>

<span data-ttu-id="91c55-521">Die *Aufrufaktivität* muss an das Dialogfeld weitergeleitet werden, wenn **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-521">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

<span data-ttu-id="91c55-522">**dialogs/main_dialog.py**</span><span class="sxs-lookup"><span data-stu-id="91c55-522">**dialogs/main_dialog.py**</span></span>

<span data-ttu-id="91c55-523">Starten Sie in einem Dialogfeldschritt die OAuth-Eingabeaufforderung, in der der Benutzer zur `begin_dialog` Anmeldung aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-523">Within a dialog step, use `begin_dialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="91c55-524">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Tokenantwortereignis, ohne dass der Benutzer dazu aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="91c55-524">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="91c55-525">Andernfalls wird der Benutzer zur Anmeldung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="91c55-525">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="91c55-526">Der Azure Bot Service sendet das Tokenantwortereignis, nachdem der Benutzer versucht, sich zu anmelden.</span><span class="sxs-lookup"><span data-stu-id="91c55-526">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

<span data-ttu-id="91c55-527">Überprüfen Sie im folgenden Dialogfeldschritt, ob ein Token im Ergebnis des vorherigen Schritts enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="91c55-527">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="91c55-528">Wenn der Wert nicht null ist, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="91c55-528">If it is not null, the user successfully signed in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

<span data-ttu-id="91c55-529">**dialogs/logout_dialog.py**</span><span class="sxs-lookup"><span data-stu-id="91c55-529">**dialogs/logout_dialog.py**</span></span>

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

> [!div class="nextstepaction"]
> [<span data-ttu-id="91c55-530">Informationen zum Hinzufügen der Authentifizierung über Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="91c55-530">Learn about adding authentication via Azure Bot Service</span></span>](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: https://docs.microsoft.com/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true
[concept-state]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0&preserve-view=true
[concept-dialogs]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0&preserve-view=true
[simple-dialog]: https://docs.microsoft.com/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0&preserve-view=true

[teams-auth-bot-cs]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[teams-auth-bot-js]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
