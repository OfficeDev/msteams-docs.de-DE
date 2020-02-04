---
title: Hinzufügen von Authentifizierung zu ihren Teams-bot
author: clearab
description: Vorgehensweise Hinzufügen von OAuth-Authentifizierung zu einem bot in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 63d06100f69a5dc3777bdfb20b3231a85dce1f04
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674241"
---
# <a name="add-authentication-to-your-teams-bot"></a><span data-ttu-id="3bde1-103">Hinzufügen von Authentifizierung zu ihren Teams-bot</span><span class="sxs-lookup"><span data-stu-id="3bde1-103">Add authentication to your Teams bot</span></span>

<span data-ttu-id="3bde1-104">Es gibt Situationen, in denen Sie möglicherweise Bots in Microsoft Teams erstellen müssen, die im Namen des Benutzers auf Ressourcen zugreifen können, beispielsweise einen e-Mail-Dienst.</span><span class="sxs-lookup"><span data-stu-id="3bde1-104">There are times when you may need to create bots in Microsoft Teams that can access resources on behalf of the user, such as a mail service.</span></span>

<span data-ttu-id="3bde1-105">In diesem Artikel wird die Verwendung der Azure bot Service V4 SDK-Authentifizierung basierend auf OAuth 2,0.</span><span class="sxs-lookup"><span data-stu-id="3bde1-105">This article demonstrates how to use Azure Bot Service v4 SDK authentication, based on OAuth 2.0.</span></span> <span data-ttu-id="3bde1-106">Dies erleichtert die Entwicklung eines bot, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="3bde1-106">This makes it easier to develop a bot that can use authentication tokens based on the user's credentials.</span></span> <span data-ttu-id="3bde1-107">Key in all dies ist die Verwendung von **Identitätsanbietern**, wie wir später sehen werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-107">Key in all this is the use of **identity providers**, as we will see later.</span></span>

<span data-ttu-id="3bde1-108">OAuth 2,0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-108">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="3bde1-109">Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3bde1-109">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

<span data-ttu-id="3bde1-110">Ein grundlegendes Verständnis finden Sie in [OAuth 2 vereinfacht](https://aka.ms/oauth2-simplified) , und [OAuth 2,0](https://oauth.net/2/) für die vollständige Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="3bde1-110">See [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) for a basic understanding, and [OAuth 2.0](https://oauth.net/2/) for the complete specification.</span></span>

<span data-ttu-id="3bde1-111">Weitere Informationen darüber, wie der Azure bot-Dienst die Authentifizierung verarbeitet, finden Sie unter [User Authentication in a Conversation](https://aka.ms/azure-bot-authentication).</span><span class="sxs-lookup"><span data-stu-id="3bde1-111">For more information about how the Azure Bot Service handles authentication, see [User authentication within a conversation](https://aka.ms/azure-bot-authentication).</span></span>

<span data-ttu-id="3bde1-112">In diesem Artikel erhalten Sie Informationen zu folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="3bde1-112">In this article you'll learn:</span></span>

- <span data-ttu-id="3bde1-113">**Erstellen eines Authentifizierungs aktivierten bot**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-113">**How to create an authentication-enabled bot**.</span></span> <span data-ttu-id="3bde1-114">Sie verwenden [CS-auth-Sample][teams-auth-bot] zum Verarbeiten von Anmeldeinformationen für die Benutzeranmeldung und zum Generieren des Authentifizierungstokens.</span><span class="sxs-lookup"><span data-stu-id="3bde1-114">You'll use [cs-auth-sample][teams-auth-bot] to handle user sign-in credentials and the generating the authentication token.</span></span>
- <span data-ttu-id="3bde1-115">**Wie Sie den bot in Azure bereitstellen und einem Identitätsanbieter zuordnen**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-115">**How to deploy the bot to Azure and associate it with an identity provider**.</span></span> <span data-ttu-id="3bde1-116">Der Anbieter gibt ein Token basierend auf den Anmeldeinformationen für die Benutzeranmeldung aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-116">The provider issues a token based on user sign-in credentials.</span></span> <span data-ttu-id="3bde1-117">Der Bot kann mithilfe des Tokens auf Ressourcen zugreifen, beispielsweise auf einen e-Mail-Dienst, für den eine Authentifizierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="3bde1-117">The bot can use the token to access resources, such as a mail service, which require authentication.</span></span> <span data-ttu-id="3bde1-118">Weitere Informationen finden Sie unter [Microsoft Teams-Authentifizierungs Fluss für Bots](auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="3bde1-118">For more information see  [Microsoft Teams authentication flow for bots](auth-flow-bot.md).</span></span>
- <span data-ttu-id="3bde1-119">**Vorgehensweise zum Integrieren des bot in Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-119">**How to integrate the bot within Microsoft Teams**.</span></span> <span data-ttu-id="3bde1-120">Nachdem der bot integriert wurde, können Sie sich in einem Chat anmelden und Nachrichten damit austauschen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-120">Once the bot has been integrated, you can sign in and exchange messages with it in a chat.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3bde1-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="3bde1-121">Prerequisites</span></span>

- <span data-ttu-id="3bde1-122">Kenntnisse der [grundlegenden][concept-basics]Funktionen von bot, der [Verwaltung von Status][concept-state], der [Dialogfeld Bibliothek][concept-dialogs]und der [Implementierung eines sequenziellen Unterhaltungs Flusses][simple-dialog].</span><span class="sxs-lookup"><span data-stu-id="3bde1-122">Knowledge of [bot basics][concept-basics], [managing state][concept-state], the [dialogs library][concept-dialogs], and how to [implement sequential conversation flow][simple-dialog].</span></span>
- <span data-ttu-id="3bde1-123">Kenntnisse in Azure und OAuth 2,0-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="3bde1-123">Knowledge of Azure and OAuth 2.0 development.</span></span>
- <span data-ttu-id="3bde1-124">Visual Studio 2017 oder höher und git.</span><span class="sxs-lookup"><span data-stu-id="3bde1-124">Visual Studio 2017 or later and Git.</span></span>
- <span data-ttu-id="3bde1-125">Azure-Konto.</span><span class="sxs-lookup"><span data-stu-id="3bde1-125">Azure account.</span></span> <span data-ttu-id="3bde1-126">Bei Bedarf können Sie ein [Kostenloses Azure-Konto](https://azure.microsoft.com/free/)erstellen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-126">If needed, you can create an [Azure free account](https://azure.microsoft.com/free/).</span></span>
- <span data-ttu-id="3bde1-127">Im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="3bde1-127">The following sample.</span></span>

    | <span data-ttu-id="3bde1-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3bde1-128">Sample</span></span> | <span data-ttu-id="3bde1-129">BotBuilder-Version</span><span class="sxs-lookup"><span data-stu-id="3bde1-129">BotBuilder version</span></span> | <span data-ttu-id="3bde1-130">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="3bde1-130">Demonstrates</span></span> |
    |:---|:---:|:---|
    | <span data-ttu-id="3bde1-131">**Bot-Authentifizierung** in [CS-auth-Sample][teams-auth-bot]</span><span class="sxs-lookup"><span data-stu-id="3bde1-131">**Bot authentication** in [cs-auth-sample][teams-auth-bot]</span></span> | <span data-ttu-id="3bde1-132">v4</span><span class="sxs-lookup"><span data-stu-id="3bde1-132">v4</span></span> | <span data-ttu-id="3bde1-133">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="3bde1-133">OAuthCard support</span></span> |
    | <span data-ttu-id="3bde1-134">**Bot-Authentifizierung** in [python-auth-Sample][teams-auth-bot-py]</span><span class="sxs-lookup"><span data-stu-id="3bde1-134">**Bot authentication** in [python-auth-sample][teams-auth-bot-py]</span></span> | <span data-ttu-id="3bde1-135">v4</span><span class="sxs-lookup"><span data-stu-id="3bde1-135">v4</span></span> | <span data-ttu-id="3bde1-136">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="3bde1-136">OAuthCard support</span></span> |

## <a name="create-the-resource-group"></a><span data-ttu-id="3bde1-137">Erstellen der Ressourcengruppe</span><span class="sxs-lookup"><span data-stu-id="3bde1-137">Create the resource group</span></span>

<span data-ttu-id="3bde1-138">Die Ressourcengruppe und der Dienstplan sind nicht unbedingt erforderlich, Sie ermöglichen jedoch das bequeme Freigeben der von Ihnen erstellten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-138">The resource group and the service plan aren't strictly necessary, but they allow you to conveniently release the resources you create.</span></span> <span data-ttu-id="3bde1-139">Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.</span><span class="sxs-lookup"><span data-stu-id="3bde1-139">This is good practice for keeping your resources organized and manageable.</span></span>

<span data-ttu-id="3bde1-140">Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das bot-Framework zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-140">You use a resource group to create individual resources for the Bot Framework.</span></span> <span data-ttu-id="3bde1-141">Stellen Sie für die Leistung sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-141">For performance, ensure that these resources are located in the same Azure region.</span></span>

1. <span data-ttu-id="3bde1-142">Melden Sie sich in Ihrem Browser beim [**Azure-Portal**][azure-portal]an.</span><span class="sxs-lookup"><span data-stu-id="3bde1-142">In your browser, sign into the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="3bde1-143">Wählen Sie im linken Navigationsbereich **Ressourcengruppen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-143">In the left navigation panel, select **Resource groups**.</span></span>
1. <span data-ttu-id="3bde1-144">Wählen Sie in der oberen linken Ecke des angezeigten Fensters Tab **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-144">In the upper left of the displayed window, select **Add** tab to create a new resource group.</span></span> <span data-ttu-id="3bde1-145">Sie werden aufgefordert, Folgendes bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="3bde1-145">You'll be prompted to provide the following:</span></span>
    1. <span data-ttu-id="3bde1-146">**Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-146">**Subscription**.</span></span> <span data-ttu-id="3bde1-147">Verwenden Sie Ihr vorhandenes Abonnement.</span><span class="sxs-lookup"><span data-stu-id="3bde1-147">Use your existing subscription.</span></span>
    1. <span data-ttu-id="3bde1-148">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-148">**Resource group**.</span></span> <span data-ttu-id="3bde1-149">Geben Sie den Namen für die Ressourcengruppe ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-149">Enter the name for the resource group.</span></span> <span data-ttu-id="3bde1-150">Ein Beispiel könnte *TeamsResourceGroup*sein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-150">An example could be  *TeamsResourceGroup*.</span></span> <span data-ttu-id="3bde1-151">Beachten Sie, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="3bde1-151">Remember that the name must be unique.</span></span>
    1. <span data-ttu-id="3bde1-152">Wählen Sie im Dropdownmenü **Region** die Option *West US*oder eine Region, die sich in der Nähe ihrer Anwendungen befindet.</span><span class="sxs-lookup"><span data-stu-id="3bde1-152">From the **Region** drop-down menu, select *West US*, or a region close to your applications.</span></span>
    1. <span data-ttu-id="3bde1-153">Klicken Sie auf die Schaltfläche **überprüfen und erstellen** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-153">Select the **Review and create** button.</span></span> <span data-ttu-id="3bde1-154">Es sollte ein Banner angezeigt werden, das die *übergebene Validierung*liest.</span><span class="sxs-lookup"><span data-stu-id="3bde1-154">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="3bde1-155">Klicken Sie auf die Schaltfläche **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-155">Select the **Create** button.</span></span> <span data-ttu-id="3bde1-156">Es kann einige Minuten dauern, bis die Ressourcengruppe erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="3bde1-156">It may take a few minutes to create the resource group.</span></span>

> [!TIP]
> <span data-ttu-id="3bde1-157">Wie bei den Ressourcen, die Sie später in diesem Lernprogramm erstellen, empfiehlt es sich, diese Ressourcengruppe für einfachen Zugriff an das Dashboard zu anheften.</span><span class="sxs-lookup"><span data-stu-id="3bde1-157">As with the resources you'll create later in this tutorial, it's a good idea to pin this resource group to your dashboard for easy access.</span></span> <span data-ttu-id="3bde1-158">Wenn Sie dies möchten, wählen Sie das Pin-Symbol #a0 # 128204; in der oberen rechten Ecke des Dashboards.</span><span class="sxs-lookup"><span data-stu-id="3bde1-158">If you'd like to do so, select the pin icon &#128204; in the upper right of the dashboard.</span></span>

## <a name="create-the-service-plan"></a><span data-ttu-id="3bde1-159">Erstellen des Dienstplans</span><span class="sxs-lookup"><span data-stu-id="3bde1-159">Create the service plan</span></span>

1. <span data-ttu-id="3bde1-160">Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Ressource erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-160">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Create a resource**.</span></span>
1. <span data-ttu-id="3bde1-161">Geben Sie im Suchfeld den Text *App-Dienst Plan*ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-161">In the search box, type *App Service Plan*.</span></span> <span data-ttu-id="3bde1-162">Wählen Sie die **App-Service Plan** Karte in den Suchergebnissen aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-162">Select the **App Service Plan** card from the search results.</span></span>
1. <span data-ttu-id="3bde1-163">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-163">Select **Create**.</span></span>
1. <span data-ttu-id="3bde1-164">Sie werden aufgefordert, die folgenden Informationen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="3bde1-164">You'll be asked to provide the following information:</span></span>
    1. <span data-ttu-id="3bde1-165">**Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-165">**Subscription**.</span></span> <span data-ttu-id="3bde1-166">Sie können ein vorhandenes Abonnement verwenden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-166">You can use an existing subscription.</span></span>
    1. <span data-ttu-id="3bde1-167">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-167">**Resource Group**.</span></span> <span data-ttu-id="3bde1-168">Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-168">Select the group you created earlier.</span></span>
    1. <span data-ttu-id="3bde1-169">**Name**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-169">**Name**.</span></span> <span data-ttu-id="3bde1-170">Geben Sie den Namen für den Service Plan ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-170">Enter the name for the service plan.</span></span> <span data-ttu-id="3bde1-171">Ein Beispiel könnte *TeamsServicePlan*sein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-171">An example could be  *TeamsServicePlan*.</span></span> <span data-ttu-id="3bde1-172">Beachten Sie, dass der Name innerhalb der Gruppe eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="3bde1-172">Remember that the name must be unique, within the group.</span></span>
    1. <span data-ttu-id="3bde1-173">**Betriebs System**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-173">**Operating System**.</span></span> <span data-ttu-id="3bde1-174">Wählen Sie *Windows* oder Ihr entsprechendes Betriebssystem aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-174">Select *Windows* or your applicable OS.</span></span>
    1. <span data-ttu-id="3bde1-175">**Region**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-175">**Region**.</span></span> <span data-ttu-id="3bde1-176">Wählen Sie " *West US* " oder eine Region in der Nähe ihrer Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-176">Select *West US* or a region close to your applications.</span></span>
    1. <span data-ttu-id="3bde1-177">**Preisstufe**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-177">**Pricing Tier**.</span></span> <span data-ttu-id="3bde1-178">Stellen Sie sicher, dass *Standard S1* ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="3bde1-178">Make sure that *Standard S1* is selected.</span></span> <span data-ttu-id="3bde1-179">Dies sollte der Standardwert sein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-179">This should be the default value.</span></span>
    1. <span data-ttu-id="3bde1-180">Klicken Sie auf die Schaltfläche **überprüfen und erstellen** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-180">Select the **Review and create** button.</span></span> <span data-ttu-id="3bde1-181">Es sollte ein Banner angezeigt werden, das die *übergebene Validierung*liest.</span><span class="sxs-lookup"><span data-stu-id="3bde1-181">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="3bde1-182">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-182">Select **Create**.</span></span> <span data-ttu-id="3bde1-183">Es kann einige Minuten dauern, bis Sie den App-Dienstplan erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-183">It may take a few minutes to create the app service plan.</span></span> <span data-ttu-id="3bde1-184">Der Plan wird in der Ressourcengruppe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="3bde1-184">The plan will be listed in the resource group.</span></span>

## <a name="create-the-bot-channels-registration"></a><span data-ttu-id="3bde1-185">Erstellen der Registrierung für bot-Kanäle</span><span class="sxs-lookup"><span data-stu-id="3bde1-185">Create the bot channels registration</span></span>

<span data-ttu-id="3bde1-186">Die Registrierung von bot-Kanälen registriert Ihren Webdienst als bot mit dem bot-Framework, vorausgesetzt, Sie verfügen über eine Microsoft-App-ID und ein App-Kennwort (geheimer Client Schlüssel).</span><span class="sxs-lookup"><span data-stu-id="3bde1-186">The bot channels registration registers your web service as a bot with the Bot Framework, provided you have a Microsoft App Id and App password (client secret).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bde1-187">Sie müssen ihren bot nur registrieren, wenn er nicht in Azure gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-187">You only need to register your bot if it is not hosted in Azure.</span></span> <span data-ttu-id="3bde1-188">Wenn Sie [einen bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0) über das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert.</span><span class="sxs-lookup"><span data-stu-id="3bde1-188">If you [created a bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0) through the Azure portal then it is already registered with the service.</span></span> <span data-ttu-id="3bde1-189">Wenn Sie Ihren bot über das [bot-Framework](https://dev.botframework.com/bots/new) oder [AppStudio](~/concepts/build-and-test/app-studio-overview.md) erstellt haben, ist Ihr bot nicht in Azure registriert.</span><span class="sxs-lookup"><span data-stu-id="3bde1-189">If you created your bot through the [Bot Framework](https://dev.botframework.com/bots/new) or [AppStudio](~/concepts/build-and-test/app-studio-overview.md) your bot isn't registered in Azure.</span></span>

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

<span data-ttu-id="3bde1-190">Nachdem Azure die Registrierungs Ressource erstellt hat, wird es in die Liste Ressourcengruppe aufgenommen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-190">After Azure has created the registration resource it will be included in the resource group list.</span></span>  

![App Channels-Registrierungsgruppe für bot](../../../assets/images/authentication/auth-bot-channels-registration-group.PNG)

> [!NOTE]
> <span data-ttu-id="3bde1-192">Die Ressourcen zur Registrierung von bot-Kanälen zeigen die **globale** Region an, selbst wenn Sie West US ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-192">The Bot Channels Registration resource will show the **Global** region even if you selected West US.</span></span> <span data-ttu-id="3bde1-193">Dies wird erwartet.</span><span class="sxs-lookup"><span data-stu-id="3bde1-193">This is expected.</span></span>

<span data-ttu-id="3bde1-194">Weitere Informationen finden Sie unter [Erstellen eines bot für Teams](../create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="3bde1-194">For more information, see [Create a bot for Teams](../create-a-bot-for-teams.md).</span></span>

## <a name="create-the-identity-provider"></a><span data-ttu-id="3bde1-195">Erstellen des Identitätsanbieters</span><span class="sxs-lookup"><span data-stu-id="3bde1-195">Create the identity provider</span></span>

<span data-ttu-id="3bde1-196">Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3bde1-196">You need an identity provider that can be used for authentication.</span></span>
<span data-ttu-id="3bde1-197">In diesem Verfahren verwenden Sie einen Azure AD Anbieter; Außerdem können andere Azure Ad Unterstützte Identitätsanbieter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-197">In this procedure you'll use an Azure AD provider; other Azure AD supported identity providers can also be used.</span></span>

1. <span data-ttu-id="3bde1-198">Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Azure Active Directory**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-198">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Azure Active Directory**.</span></span>
    > [!TIP]
    > <span data-ttu-id="3bde1-199">Sie müssen diese Azure AD Ressource in einem Mandanten erstellen und registrieren, in dem Sie die Berechtigung zum Delegieren von von einer Anwendung angeforderten Berechtigungen erteilen können.</span><span class="sxs-lookup"><span data-stu-id="3bde1-199">You'll need to create and register this Azure AD resource in a tenant in which you can consent to delegate permissions requested by an application.</span></span>
    > <span data-ttu-id="3bde1-200">Anweisungen zum Erstellen eines Mandanten finden Sie unter [zugreifen auf das Portal und Erstellen eines Mandanten](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span><span class="sxs-lookup"><span data-stu-id="3bde1-200">For instruction on creating a tenant, see [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span></span>
1. <span data-ttu-id="3bde1-201">Wählen Sie im linken Bereich **App-Registrierungen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-201">In the left panel, select **App registrations**.</span></span>
1. <span data-ttu-id="3bde1-202">Wählen Sie im rechten Bereich die Registerkarte **neue Registrierung** in der oberen linken Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-202">In the right panel, select the **New registration** tab, in the upper left.</span></span>
1. <span data-ttu-id="3bde1-203">Sie werden aufgefordert, die folgenden Informationen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="3bde1-203">You'll be asked to provide the following information:</span></span>
   1. <span data-ttu-id="3bde1-204">**Name**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-204">**Name**.</span></span> <span data-ttu-id="3bde1-205">Geben Sie den Namen der Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-205">Enter the name for the application.</span></span> <span data-ttu-id="3bde1-206">Ein Beispiel könnte *BotTeamsIdentity*sein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-206">An example could be  *BotTeamsIdentity*.</span></span> <span data-ttu-id="3bde1-207">Beachten Sie, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="3bde1-207">Remember that the name must be unique.</span></span>
   1. <span data-ttu-id="3bde1-208">Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-208">Select the **Supported account types** for your application.</span></span> <span data-ttu-id="3bde1-209">Wählen Sie *Konten in einem beliebigen Organisations Verzeichnis (beliebige Azure AD Verzeichnis – Multimandanten) und persönliche Microsoft-Konten (beispielsweise Skype, Xbox)* aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-209">Select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
   1. <span data-ttu-id="3bde1-210">Für den **Umleitungs-URI**:</span><span class="sxs-lookup"><span data-stu-id="3bde1-210">For the **Redirect URI**:</span></span><br/>
       <span data-ttu-id="3bde1-211">&#x2713;wählen Sie das **Webpart**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-211">&#x2713;Select **Web**.</span></span> <br/>
       <span data-ttu-id="3bde1-212">&#x2713; legen Sie die URL `https://token.botframework.com/.auth/web/redirect`auf fest.</span><span class="sxs-lookup"><span data-stu-id="3bde1-212">&#x2713; Set the URL to `https://token.botframework.com/.auth/web/redirect`.</span></span>
   1. <span data-ttu-id="3bde1-213">Wählen Sie **registrieren**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-213">Select **Register**.</span></span>

1. <span data-ttu-id="3bde1-214">Nach der Erstellung zeigt Azure die Übersichts **Seite für die APP** an.</span><span class="sxs-lookup"><span data-stu-id="3bde1-214">Once it is created, Azure displays the **Overview** page for the app.</span></span> <span data-ttu-id="3bde1-215">Kopieren Sie die folgenden Informationen, und speichern Sie Sie in einer Datei:</span><span class="sxs-lookup"><span data-stu-id="3bde1-215">Copy and save the following information to a file:</span></span>

    1. <span data-ttu-id="3bde1-216">Der Wert der **Anwendungs-ID (Client)** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-216">The **Application (client) ID** value.</span></span> <span data-ttu-id="3bde1-217">Sie verwenden diesen Wert später als *Client-ID* , wenn Sie diese Azure-Identitäts Anwendung mit Ihrem bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-217">You'll use this value later as the *Client ID* when you register this Azure identity application with your bot.</span></span>
    1. <span data-ttu-id="3bde1-218">Der **Verzeichnis Wert (Mandant) ID** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-218">The **Directory (tenant) ID** value.</span></span> <span data-ttu-id="3bde1-219">Sie werden diesen Wert auch später als *Mandanten-ID* verwenden, um diese Azure-Identitäts Anwendung mit Ihrem bot zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-219">You'll also use this value later as the *Tenant ID* to register this Azure identity application with your bot.</span></span>

1. <span data-ttu-id="3bde1-220">Wählen Sie im linken Bereich **Zertifikate #a0 Secrets** aus, um einen geheimen Client Schlüssel für Ihre Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-220">In the left panel, select **Certificates & secrets** to create a client secret for your application.</span></span>

   1. <span data-ttu-id="3bde1-221">Wählen Sie unter **Client Secrets**#a0 **neuen geheimen Client Schlüssel**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-221">Under **Client secrets**, select &#x2795; **New client secret**.</span></span>
   1. <span data-ttu-id="3bde1-222">Fügen Sie eine Beschreibung hinzu, um dieses Geheimnis von anderen Personen zu identifizieren, die Sie für diese APP möglicherweise erstellen müssen, beispielsweise für die *app "bot Identity" in Microsoft Teams*.</span><span class="sxs-lookup"><span data-stu-id="3bde1-222">Add a description to identify this secret from others you might need to create for this app, such as *Bot identity app in Teams*.</span></span>
   1. <span data-ttu-id="3bde1-223">Festlegen **läuft** auf Ihre Auswahl ab.</span><span class="sxs-lookup"><span data-stu-id="3bde1-223">Set **Expires** to your selection.</span></span>
   1. <span data-ttu-id="3bde1-224">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-224">Select **Add**.</span></span>
   1. <span data-ttu-id="3bde1-225">**Notieren Sie den geheimen Schlüssel**, bevor Sie diese Seite verlassen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-225">Before leaving this page, **record the secret**.</span></span> <span data-ttu-id="3bde1-226">Diesen Wert verwenden Sie später als _geheimer Client Schlüssel_ , wenn Sie Ihre Azure AD Anwendung mit Ihrem bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-226">You'll use this value later as the _Client secret_ when you register your Azure AD application with your bot.</span></span>

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a><span data-ttu-id="3bde1-227">Konfigurieren Sie die Verbindung mit dem Identitätsanbieter, und registrieren Sie Sie mit dem bot.</span><span class="sxs-lookup"><span data-stu-id="3bde1-227">Configure the identity provider connection and register it with the bot</span></span>

1. <span data-ttu-id="3bde1-228">Wählen Sie im [**Azure-Portal**][azure-portal]ihre Ressourcengruppe aus dem Dashboard aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-228">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="3bde1-229">Wählen Sie Ihren bot-Kanal Registrierungslink aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-229">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="3bde1-230">Wählen Sie auf der Seite Ressource die Option **Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-230">On the resource page, select **Settings**.</span></span>
1. <span data-ttu-id="3bde1-231">Wählen Sie unter **OAuth-Verbindungseinstellungen** am unteren Rand der Seite die Option **Einstellung hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-231">Under **OAuth Connection Settings** near the bottom of the page, select **Add Setting**.</span></span>
1. <span data-ttu-id="3bde1-232">Füllen Sie das Formular wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3bde1-232">Complete the form as follows:</span></span>

    1. <span data-ttu-id="3bde1-233">**Name**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-233">**Name**.</span></span> <span data-ttu-id="3bde1-234">Geben Sie einen Namen für die Verbindung ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-234">Enter a name for the connection.</span></span> <span data-ttu-id="3bde1-235">Sie verwenden diesen Namen in Ihrem bot in der `appsettings.json` Datei.</span><span class="sxs-lookup"><span data-stu-id="3bde1-235">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="3bde1-236">Beispiel *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="3bde1-236">For example *BotTeamsAuthADv1*.</span></span>
    1. <span data-ttu-id="3bde1-237">**Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-237">**Service Provider**.</span></span> <span data-ttu-id="3bde1-238">Wählen Sie **Azure Active Directory** aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-238">Select **Azure Active Directory**.</span></span> <span data-ttu-id="3bde1-239">Nachdem Sie diese Option ausgewählt haben, werden die Azure AD spezifischen Felder angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3bde1-239">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="3bde1-240">**Client-ID**. Geben Sie die Anwendungs-ID (Client) ein, die Sie in den obigen Schritten für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-240">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="3bde1-241">**Geheimer Client Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-241">**Client secret**.</span></span> <span data-ttu-id="3bde1-242">Geben Sie den geheimen Schlüssel ein, den Sie in den obigen Schritten für Ihre Azure Identity-Anbieter-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-242">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="3bde1-243">**Grant-Typ**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-243">**Grant Type**.</span></span> <span data-ttu-id="3bde1-244">Geben `authorization_code`Sie ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-244">Enter `authorization_code`.</span></span>
    1. <span data-ttu-id="3bde1-245">**Anmelde-URL**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-245">**Login URL**.</span></span> <span data-ttu-id="3bde1-246">Geben `https://login.microsoftonline.com`Sie ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-246">Enter `https://login.microsoftonline.com`.</span></span>
    1. <span data-ttu-id="3bde1-247">**Mandanten-ID**: Geben Sie die **Verzeichnis (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure Identity-App aufgezeichnet haben, oder **verbreitet** , je nach dem unterstützten Kontotyp, der beim Erstellen der APP für den Identitätsanbieter ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="3bde1-247">**Tenant ID**, enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="3bde1-248">Um zu entscheiden, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="3bde1-248">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="3bde1-249">Wenn Sie entweder *Konten in diesem Organisations Verzeichnis (nur Microsoft – einzelner Mandant)* oder *Konten in einem Organisations Verzeichnis (Microsoft Aad Directory-Multi Mandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die Aad-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-249">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="3bde1-250">Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="3bde1-250">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="3bde1-251">Wenn Sie *Konten in einem beliebigen Organisations Verzeichnis (AAD Directory-Multi Mandanten und persönliche Microsoft-Konten wie Skype, Xbox, Outlook)* ausgewählt haben, geben Sie das Wort " **Common** " anstelle einer Mandanten-ID ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-251">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="3bde1-252">Andernfalls wird die Aad-App über den Mandanten überprüfen, dessen ID ausgewählt wurde, und persönliche Microsoft-Konten ausschließen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-252">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    <span data-ttu-id="3bde1-253">h.</span><span class="sxs-lookup"><span data-stu-id="3bde1-253">h.</span></span> <span data-ttu-id="3bde1-254">Geben Sie für **Ressourcen**- `https://graph.microsoft.com/`URL den Eintrag ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-254">For **Resource URL**, enter `https://graph.microsoft.com/`.</span></span> <span data-ttu-id="3bde1-255">Dies wird im aktuellen Codebeispiel nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="3bde1-255">This is not used in the current code sample.</span></span>  
    <span data-ttu-id="3bde1-256">Ich.</span><span class="sxs-lookup"><span data-stu-id="3bde1-256">i.</span></span> <span data-ttu-id="3bde1-257">Lassen Sie **Bereiche** leer.</span><span class="sxs-lookup"><span data-stu-id="3bde1-257">Leave **Scopes** blank.</span></span> <span data-ttu-id="3bde1-258">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-258">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. <span data-ttu-id="3bde1-260">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-260">Select **Save**.</span></span>

### <a name="test-the-connection"></a><span data-ttu-id="3bde1-261">Testen der Verbindung</span><span class="sxs-lookup"><span data-stu-id="3bde1-261">Test the connection</span></span>

1. <span data-ttu-id="3bde1-262">Wählen Sie den Eintrag Connection aus, um die soeben erstellte Verbindung zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-262">Select the connection entry to open the connection you just created.</span></span>
1. <span data-ttu-id="3bde1-263">Wählen Sie oben im Bereich **Service Provider Connection Setting** die Option **Test connection** aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-263">Select **Test Connection** at the top of the **Service Provider Connection Setting** panel.</span></span>
1. <span data-ttu-id="3bde1-264">Wenn Sie das erste Mal durchführen, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-264">The first time you do this will open a new browser window asking you to select an account.</span></span> <span data-ttu-id="3bde1-265">Wählen Sie diejenige aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3bde1-265">Select the one you want to use.</span></span>
1. <span data-ttu-id="3bde1-266">Als nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu gestatten.</span><span class="sxs-lookup"><span data-stu-id="3bde1-266">Next, you'll be asked to allow to the identity provider to use your data (credentials).</span></span> <span data-ttu-id="3bde1-267">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-267">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. <span data-ttu-id="3bde1-269">Wählen Sie **akzeptieren**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-269">Select **Accept**.</span></span>
1. <span data-ttu-id="3bde1-270">Anschließend sollten Sie zu einer **Test Verbindung zu \<Ihrer-Connection-Name> erfolgreich gefolgten** Seite umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-270">This should then redirect you to a **Test Connection to \<your-connection-name> Succeeded** page.</span></span> <span data-ttu-id="3bde1-271">Aktualisieren Sie die Seite, wenn Sie eine Fehlermeldung erhalten.</span><span class="sxs-lookup"><span data-stu-id="3bde1-271">Refresh the page if you get an error.</span></span> <span data-ttu-id="3bde1-272">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-272">The following image is an example:</span></span>

  ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

<span data-ttu-id="3bde1-274">Der Verbindungsname wird vom bot-Code zum Abrufen von Benutzerauthentifizierungstoken verwendet.</span><span class="sxs-lookup"><span data-stu-id="3bde1-274">The connection name is used by the bot code to retrieve user authentication tokens.</span></span>

## <a name="prepare-the-bot-sample-code"></a><span data-ttu-id="3bde1-275">Vorbereiten des bot-Beispielcodes</span><span class="sxs-lookup"><span data-stu-id="3bde1-275">Prepare the bot sample code</span></span>

<span data-ttu-id="3bde1-276">Nachdem die vorläufigen Einstellungen vorgenommen wurden, konzentrieren wir uns auf die Erstellung des bot, der in diesem Artikel verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3bde1-276">With the preliminary settings done, let's focus on the creation of the bot to use in this article.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="3bde1-277">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="3bde1-277">C#/.NET</span></span>](#tab/dotnet)

1. <span data-ttu-id="3bde1-278">Klon [CS-auth-Sample][teams-auth-bot].</span><span class="sxs-lookup"><span data-stu-id="3bde1-278">Clone [cs-auth-sample][teams-auth-bot].</span></span>
1. <span data-ttu-id="3bde1-279">Starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3bde1-279">Launch Visual Studio.</span></span>
1. <span data-ttu-id="3bde1-280">Wählen Sie in der Symbolleiste **Datei-#a0 Open-#a1 Projekt/Lösung** aus, und öffnen Sie das bot-Projekt.</span><span class="sxs-lookup"><span data-stu-id="3bde1-280">From the toolbar select **File -> Open -> Project/Solution** and open the bot project.</span></span>
1. <span data-ttu-id="3bde1-281">In C# Update **appSettings. JSON** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="3bde1-281">In C# Update **appsettings.json** as follows:</span></span>

    - <span data-ttu-id="3bde1-282">Legen `ConnectionName` Sie den Namen der Identitätsanbieter Verbindung fest, die Sie der bot-Kanal Registrierung hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-282">Set `ConnectionName` to the name of the identity provider connection you added to the bot channel registration.</span></span> <span data-ttu-id="3bde1-283">Der Name, den wir in diesem Beispiel verwendet haben, ist *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="3bde1-283">The name we used in this example is *BotTeamsAuthADv1*.</span></span>
    - <span data-ttu-id="3bde1-284">Legen `MicrosoftAppId` Sie die **bot-APP-ID** fest, die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-284">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="3bde1-285">Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-285">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="3bde1-286">Legen Sie `ConnectionName` den auf den Namen der Identitätsanbieter Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="3bde1-286">Set the `ConnectionName` to the name of the identity provider connection.</span></span> 

    <span data-ttu-id="3bde1-287">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-287">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="3bde1-288">Beispielsweise müssen alle kaufmännischen und-Zeichen (#a0) als `&amp;`codiert werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-288">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. <span data-ttu-id="3bde1-289">Navigieren Sie im Projektmappen-Explorer `TeamsAppManifest` zum Ordner öffnen `manifest.json` und festlegen `id` sowie `botId` zur **bot-APP-ID** , die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-289">In the Solution Explorer, navigate to the `TeamsAppManifest` folder, open `manifest.json` and set `id` and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="pythontabpython"></a>[<span data-ttu-id="3bde1-290">Python</span><span class="sxs-lookup"><span data-stu-id="3bde1-290">Python</span></span>](#tab/python)

1. <span data-ttu-id="3bde1-291">Klonen Sie die Beispiel- [Teams-bot-Authentifizierung][teams-auth-bot-py] aus dem GitHub-Repository.</span><span class="sxs-lookup"><span data-stu-id="3bde1-291">Clone the sample [Teams bot authentication][teams-auth-bot-py] from the github repository.</span></span>
1. <span data-ttu-id="3bde1-292">**Config.py**aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="3bde1-292">Update **config.py**:</span></span>

    - <span data-ttu-id="3bde1-293">Legen `ConnectionName` Sie den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem bot hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-293">Set `ConnectionName` to the name of the OAuth connection setting you added to your bot.</span></span>
    - <span data-ttu-id="3bde1-294">Legen Sie die APP-ID und den App-Schlüssel Ihres bot fest `MicrosoftAppId` `MicrosoftAppPassword`</span><span class="sxs-lookup"><span data-stu-id="3bde1-294">Set `MicrosoftAppId` and `MicrosoftAppPassword` to your bot's app ID and app secret.</span></span>

      <span data-ttu-id="3bde1-295">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-295">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="3bde1-296">Beispielsweise müssen alle kaufmännischen und-Zeichen (#a0) als `&amp;`codiert werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-296">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a><span data-ttu-id="3bde1-297">Bereitstellen des bot in Azure</span><span class="sxs-lookup"><span data-stu-id="3bde1-297">Deploy the bot to Azure</span></span>

<span data-ttu-id="3bde1-298">Um den bot bereitzustellen, befolgen Sie die Schritte unter How to [deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span><span class="sxs-lookup"><span data-stu-id="3bde1-298">To deploy the bot, follow the steps in the how to [Deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span></span>

<span data-ttu-id="3bde1-299">Alternativ können Sie in Visual Studio die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="3bde1-299">Alternatively, while in Visual Studio, you can follow these steps:</span></span>

1. <span data-ttu-id="3bde1-300">Wählen Sie im Visual Studio Projekt *Mappen-Explorer* den Projektnamen aus, und halten Sie ihn (oder klicken Sie mit der rechten Maustaste).</span><span class="sxs-lookup"><span data-stu-id="3bde1-300">In Visual Studio *Solution Explorer* select and hold (or right-click) the project name.</span></span>
1. <span data-ttu-id="3bde1-301">Wählen Sie im Dropdownmenü die Option **veröffentlichen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-301">In the drop-down menu, select **Publish**.</span></span>
1. <span data-ttu-id="3bde1-302">Wählen Sie im angezeigten Fenster den **neuen** Link aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-302">In the displayed window, select the **New** link.</span></span>
1. <span data-ttu-id="3bde1-303">Wählen Sie im Dialogfeld **App-Dienst** auf der linken Seite aus, und **Erstellen Sie neu** auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="3bde1-303">In the dialog window, select **App Service** on the left and **Create New** on the right.</span></span>
1. <span data-ttu-id="3bde1-304">Klicken Sie auf die Schaltfläche **veröffentlichen** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-304">Select the **Publish** button.</span></span>
1. <span data-ttu-id="3bde1-305">Geben Sie im nächsten Dialogfenster die erforderlichen Informationen ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-305">In the next dialog window, enter the required information.</span></span> <span data-ttu-id="3bde1-306">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-306">The following is an example:</span></span>

   ![auth-App-Service](../../../assets/images/authentication/auth-bot-app-service.png)

1. <span data-ttu-id="3bde1-308">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-308">Select **Create**.</span></span>
1. <span data-ttu-id="3bde1-309">Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte Sie in Visual Studio angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-309">If the deployment completes successfully, you should see it reflected in Visual Studio.</span></span> <span data-ttu-id="3bde1-310">Darüber hinaus wird in Ihrem Standardbrowser eine Seite angezeigt, die besagt, dass *Ihr bot Ready!*.</span><span class="sxs-lookup"><span data-stu-id="3bde1-310">Moreover, a page is displayed in your default browser saying *Your bot is ready!*.</span></span> <span data-ttu-id="3bde1-311">Die URL wird wie folgt aussehen: `https://botteamsauth.azurewebsites.net/`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-311">The URL will be similar to this: `https://botteamsauth.azurewebsites.net/`.</span></span> <span data-ttu-id="3bde1-312">Speichern Sie Sie in einer Datei.</span><span class="sxs-lookup"><span data-stu-id="3bde1-312">Save it to a file.</span></span>
1. <span data-ttu-id="3bde1-313">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="3bde1-313">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="3bde1-314">Überprüfen Sie Ihre Ressourcengruppe, der bot sollte zusammen mit den anderen Ressourcen aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-314">Check your resource group, the bot should be listed along with the other resources.</span></span> <span data-ttu-id="3bde1-315">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-315">The following image is an example:</span></span>

    ![Teams-bot-auth-App-Service-Gruppe](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. <span data-ttu-id="3bde1-317">Wählen Sie in der Gruppe Ressourcen den Namen des bot-Kanal Registrierungs namens (Link) aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-317">In the resource group, select the bot channel registration name (link).</span></span>
1. <span data-ttu-id="3bde1-318">Wählen Sie im linken Bereich **Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-318">In the left panel, select **Settings**.</span></span>
1. <span data-ttu-id="3bde1-319">Geben Sie im Feld **Messaging-Endpunkt** die oben abgerufene URL ein, `api/messages`gefolgt von.</span><span class="sxs-lookup"><span data-stu-id="3bde1-319">In the **Messaging endpoint** box, enter the URL obtained above followed by `api/messages`.</span></span> <span data-ttu-id="3bde1-320">Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-320">This is an example: `https://botteamsauth.azurewebsites.net/api/messages`.</span></span>
1. <span data-ttu-id="3bde1-321">Klicken Sie oben links auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-321">Select the **Save** button in the upper left.</span></span>

## <a name="test-the-bot-using-the-emulator"></a><span data-ttu-id="3bde1-322">Testen des bot mit dem Emulator</span><span class="sxs-lookup"><span data-stu-id="3bde1-322">Test the bot using the Emulator</span></span>

<span data-ttu-id="3bde1-323">Wenn Sie es nicht bereits getan haben, installieren Sie den [Microsoft bot Framework-Emulator](https://aka.ms/bot-framework-emulator-readme).</span><span class="sxs-lookup"><span data-stu-id="3bde1-323">If you haven't done it already, install the [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme).</span></span> <span data-ttu-id="3bde1-324">Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span><span class="sxs-lookup"><span data-stu-id="3bde1-324">See also [Debug with the Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span></span>

<span data-ttu-id="3bde1-325">Damit die bot-Beispiel Anmeldung funktioniert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-325">In order for the bot sample login to work you must configure the Emulator as shown below.</span></span>

### <a name="configure-the-emulator-for-authentication"></a><span data-ttu-id="3bde1-326">Konfigurieren des Emulators für die Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="3bde1-326">Configure the Emulator for authentication</span></span>

<span data-ttu-id="3bde1-327">Wenn ein bot eine Authentifizierung erfordert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-327">If a bot requires authentication, you must configure the Emulator as shown below.</span></span>

1. <span data-ttu-id="3bde1-328">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="3bde1-328">Start the Emulator.</span></span>
1. <span data-ttu-id="3bde1-329">Wählen Sie im Emulator das Zahnradsymbol #a0 unten links oder die Registerkarte **Emulatoreinstellungen** in der oberen rechten Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-329">In the Emulator, select the gear icon &#9881; in the bottom left, or the **Emulator Settings** tab in the upper right.</span></span>
1. <span data-ttu-id="3bde1-330">Aktivieren Sie das Kontrollkästchen mit der **Version 1,0-Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-330">Check the box by **Use version 1.0 authentication tokens**.</span></span>
1. <span data-ttu-id="3bde1-331">Geben Sie den lokalen Pfad zum **ngrok** -Tool ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-331">Enter the local path to the **ngrok** tool.</span></span> <span data-ttu-id="3bde1-332">*Siehe* bot Framework Emulator/ngrok Tunneling Integration [wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span><span class="sxs-lookup"><span data-stu-id="3bde1-332">*See* the Bot Framework Emulator / ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span></span> <span data-ttu-id="3bde1-333">Weitere Informationen zum Tool finden Sie unter [ngrok](https://ngrok.com/).</span><span class="sxs-lookup"><span data-stu-id="3bde1-333">For more tool information, see [ngrok](https://ngrok.com/).</span></span>
1. <span data-ttu-id="3bde1-334">Aktivieren Sie das Kontrollkästchen **ngrok ausführen, wenn der Emulator gestartet wird**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-334">Check the box by **Run ngrok when the Emulator starts up**.</span></span>
1. <span data-ttu-id="3bde1-335">Klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-335">Select the **Save** button.</span></span>

<span data-ttu-id="3bde1-336">Wenn der bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, die der Benutzer zum Anmelden mit dem Authentifizierungsanbieter verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="3bde1-336">When the bot displays a sign-in card and the user selects the sign-in button, the Emulator opens a page that the user can use to sign in with the authentication provider.</span></span>
<span data-ttu-id="3bde1-337">Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den bot.</span><span class="sxs-lookup"><span data-stu-id="3bde1-337">Once the user does so, the provider generates a user token and sends it to the bot.</span></span> <span data-ttu-id="3bde1-338">Danach kann der bot im Namen des Benutzers handeln.</span><span class="sxs-lookup"><span data-stu-id="3bde1-338">After that, the bot can act on behalf of the user.</span></span>

### <a name="test-the-bot-locally"></a><span data-ttu-id="3bde1-339">Testen des bot lokal</span><span class="sxs-lookup"><span data-stu-id="3bde1-339">Test the bot locally</span></span>

<span data-ttu-id="3bde1-340">Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die eigentlichen bot-Tests durchführen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-340">After you have configured the authentication mechanism, you can perform the actual bot testing.</span></span>  

1. <span data-ttu-id="3bde1-341">Führen Sie das bot-Beispiel lokal auf Ihrem Computer aus, beispielsweise über Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3bde1-341">Run the bot sample locally on your machine, via Visual Studio for example.</span></span>
1. <span data-ttu-id="3bde1-342">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="3bde1-342">Start the Emulator.</span></span>
1. <span data-ttu-id="3bde1-343">Klicken Sie auf die Schaltfläche **bot öffnen** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-343">Select the **Open bot** button.</span></span>
1. <span data-ttu-id="3bde1-344">Geben Sie in der **bot-URL**die lokale URL des bot ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-344">In the **Bot URL**, enter the bot's local URL.</span></span> <span data-ttu-id="3bde1-345">Normalerweise `http://localhost:3978/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-345">Usually, `http://localhost:3978/api/messages`.</span></span>
1. <span data-ttu-id="3bde1-346">Geben Sie in der **Microsoft App-ID** die APP-ID `appsettings.json`des bot von ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-346">In the **Microsoft App ID** enter the bot's app ID from `appsettings.json`.</span></span>
1. <span data-ttu-id="3bde1-347">Geben Sie im **Microsoft App-Kennwort** das App-Kennwort des bot `appsettings.json`aus dem ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-347">In the **Microsoft App password** enter the bot's app password from the `appsettings.json`.</span></span>
1. <span data-ttu-id="3bde1-348">Wählen Sie **verbinden**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-348">Select **Connect**.</span></span>
1. <span data-ttu-id="3bde1-349">Geben Sie nach dem Starten des bot einen beliebigen Text ein, um die Anmeldekarte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-349">After the bot is up and running, enter any text to display the sign-in card.</span></span>
1. <span data-ttu-id="3bde1-350">Klicken Sie **auf** die Schaltfläche anmelden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-350">Select the **Sign in** button.</span></span>
1. <span data-ttu-id="3bde1-351">Ein Popupdialogfeld wird angezeigt, um die **geöffnete URL zu bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-351">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="3bde1-352">Dadurch kann der Benutzer des bot (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-352">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="3bde1-353">Wählen Sie **bestätigen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-353">Select **Confirm**.</span></span>
1. <span data-ttu-id="3bde1-354">Wenn Sie dazu aufgefordert werden, wählen Sie das entsprechende Benutzerkonto aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-354">If asked, select the applicable user's account.</span></span>
1. <span data-ttu-id="3bde1-355">Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="3bde1-355">Depending which configuration you used for the Emulator, you get one of the following:</span></span>
    1. <span data-ttu-id="3bde1-356">**Verwenden des Anmelde Bestätigungscodes**</span><span class="sxs-lookup"><span data-stu-id="3bde1-356">**Using sign-in verification code**</span></span>  
      <span data-ttu-id="3bde1-357">&#x2713; ein Fenster wird geöffnet, in dem der Validierungscode angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-357">&#x2713; A window is opened displaying the validation code.</span></span>  
      <span data-ttu-id="3bde1-358">&#x2713; kopieren Sie den Validierungscode, und geben Sie ihn in das Feld Chat ein, um die Anmeldung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-358">&#x2713; Copy and enter the validation code into the chat box to complete the sign-in.</span></span>
    1. <span data-ttu-id="3bde1-359">**Verwenden von Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-359">**Using authentication tokens**.</span></span>  
      <span data-ttu-id="3bde1-360">&#x2713; Sie auf der Grundlage ihrer Anmeldeinformationen angemeldet sind.</span><span class="sxs-lookup"><span data-stu-id="3bde1-360">&#x2713; You're logged in based on your credentials.</span></span>

    <span data-ttu-id="3bde1-361">Die folgende Abbildung ist ein Beispiel für die bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="3bde1-361">The following image is an example of the bot UI after you've logged in:</span></span>

    ![Authentifizierungs-bot-Anmelde Emulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. <span data-ttu-id="3bde1-363">Wenn Sie " **Ja** " auswählen, wenn der bot *möchte, dass Ihr Token angezeigt*wird, erhalten Sie eine ähnliche Antwort wie die folgende:</span><span class="sxs-lookup"><span data-stu-id="3bde1-363">If you select **Yes** when the bot asks *Would you like to view your token?*, you'll get a response similar to the following:</span></span>

    ![Authentifizierungs-bot-Anmelde Emulator-Token](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. <span data-ttu-id="3bde1-365">Geben Sie **Logout** in das Feld Eingabe Chat ein, um sich abzumelden. Dadurch wird das Benutzertoken freigegeben, und der Bot kann nicht in Ihrem Namen handeln, bis Sie sich erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-365">Enter **logout** in the input chat box to sign out. This releases the user token, and the bot won't be able to act on your behalf until you sign in again.</span></span>

> [!NOTE]
> <span data-ttu-id="3bde1-366">Für die bot-Authentifizierung ist die Verwendung des **bot Connector-Diensts**erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3bde1-366">Bot authentication requires use of the **Bot Connector Service**.</span></span> <span data-ttu-id="3bde1-367">Der Dienst greift auf die Registrierungsinformationen für bot-Kanäle für Ihren bot zu.</span><span class="sxs-lookup"><span data-stu-id="3bde1-367">The service accesses the bot channels registration information for your bot.</span></span>

## <a name="test-the-deployed-bot"></a><span data-ttu-id="3bde1-368">Testen des bereitgestellten bot</span><span class="sxs-lookup"><span data-stu-id="3bde1-368">Test the deployed bot</span></span>

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. <span data-ttu-id="3bde1-369">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="3bde1-369">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="3bde1-370">Suchen Sie Ihre Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="3bde1-370">Find your resource group.</span></span>
1. <span data-ttu-id="3bde1-371">Wählen Sie den Link Ressource aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-371">Select the resource link.</span></span> <span data-ttu-id="3bde1-372">Die Seite Ressource wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3bde1-372">The resource page is displayed.</span></span>
1. <span data-ttu-id="3bde1-373">Wählen Sie auf der Seite Ressource die Option **Test im Webchat**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-373">In the resource page, select **Test in Web Chat**.</span></span> <span data-ttu-id="3bde1-374">Der bot startet und zeigt die vordefinierten Begrüßungen an.</span><span class="sxs-lookup"><span data-stu-id="3bde1-374">The bot starts and displays the predefined greetings.</span></span>
1. <span data-ttu-id="3bde1-375">Geben Sie im Feld Chat eine beliebige Eingabe ein.</span><span class="sxs-lookup"><span data-stu-id="3bde1-375">Type anything in the chat box.</span></span>
1. <span data-ttu-id="3bde1-376">Aktivieren Sie das Kontrollkästchen **Anmelden** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-376">Select the **Sign in** box.</span></span>
1. <span data-ttu-id="3bde1-377">Ein Popupdialogfeld wird angezeigt, um die **geöffnete URL zu bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-377">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="3bde1-378">Dadurch kann der Benutzer des bot (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-378">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="3bde1-379">Wählen Sie **bestätigen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-379">Select **Confirm**.</span></span>
1. <span data-ttu-id="3bde1-380">Wenn Sie dazu aufgefordert werden, wählen Sie das entsprechende Benutzerkonto aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-380">If asked, select the applicable user's account.</span></span>
    <span data-ttu-id="3bde1-381">Die folgende Abbildung ist ein Beispiel für die bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="3bde1-381">The following image is an example of the bot UI after you have logged in:</span></span>

    ![bereitgestellte Authentifizierungs-bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed.PNG)<span data-ttu-id="3bde1-383">.</span><span class="sxs-lookup"><span data-stu-id="3bde1-383">.</span></span>

1. <span data-ttu-id="3bde1-384">Wählen Sie die Schaltfläche **Ja** aus, um das Authentifizierungstoken anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-384">Select the **Yes** button to display your authentication token.</span></span> <span data-ttu-id="3bde1-385">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-385">The following image is an example:</span></span>

    ![bereitgestelltes Token für auth-bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG)<span data-ttu-id="3bde1-387">.</span><span class="sxs-lookup"><span data-stu-id="3bde1-387">.</span></span>

1. <span data-ttu-id="3bde1-388">Geben Sie Logout ein, um sich abzumelden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-388">Enter logout to sign out.</span></span>

    ![Authentifizierungs-bot bereitgestellt Logout](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> <span data-ttu-id="3bde1-390">Wenn Sie bei der Anmeldung Probleme haben, versuchen Sie, die Verbindung erneut zu testen, wie in den vorherigen Schritten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-390">If you're having problems signing in, try to test the connection again as described in the previous steps.</span></span> <span data-ttu-id="3bde1-391">Dadurch könnte das Authentifizierungstoken neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-391">This could recreate the authentication token.</span></span>
> <span data-ttu-id="3bde1-392">Mit dem bot-Framework-Webchat Client in Azure müssen Sie sich möglicherweise mehrere Male anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="3bde1-392">With the Bot Framework Web Chat client in Azure, you may need to sign in several times before the authentication is established correctly.</span></span>

## <a name="install-and-test-the-bot-in-teams"></a><span data-ttu-id="3bde1-393">Installieren und Testen des bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3bde1-393">Install and test the bot in Teams</span></span>

1. <span data-ttu-id="3bde1-394">Stellen Sie in Ihrem bot-Projekt sicher `TeamsAppManifest` , dass der `manifest.json` Ordner den zusammen `outline.png` mit `color.png` einem und Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="3bde1-394">In your bot project, ensure that the `TeamsAppManifest` folder contains the `manifest.json` along with an `outline.png` and `color.png` files.</span></span>
1. <span data-ttu-id="3bde1-395">Navigieren Sie im Projektmappen- `TeamsAppManifest` Explorer zum Ordner.</span><span class="sxs-lookup"><span data-stu-id="3bde1-395">In Solution Explorer, navigate to the `TeamsAppManifest` folder.</span></span> <span data-ttu-id="3bde1-396">Bearbeiten `manifest.json` , indem Sie die folgenden Werte zuweisen:</span><span class="sxs-lookup"><span data-stu-id="3bde1-396">Edit `manifest.json` by assigning the following values:</span></span>
    1. <span data-ttu-id="3bde1-397">Stellen Sie sicher, dass die **bot-APP-ID** , die Sie zum Zeitpunkt der bot- `id` Kanal `botId`Registrierung erhalten haben, und zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="3bde1-397">Ensure that the **bot App ID** you received at the time of the bot channel registration is assigned to `id` and `botId`.</span></span>
    1. <span data-ttu-id="3bde1-398">Weisen Sie diesen Wert `validDomains: [ "token.botframework.com" ]`zu:.</span><span class="sxs-lookup"><span data-stu-id="3bde1-398">Assign this value: `validDomains: [ "token.botframework.com" ]`.</span></span>
1. <span data-ttu-id="3bde1-399">Wählen Sie die `manifest.json` `color.png` Dateien aus `outline.png`, und **zippen** Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="3bde1-399">Select and **zip** the `manifest.json`, `outline.png`, and `color.png` files.</span></span>
1. <span data-ttu-id="3bde1-400">Öffnen Sie **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="3bde1-400">Open **Microsoft Teams**.</span></span>
1. <span data-ttu-id="3bde1-401">Wählen Sie im linken Bereich unten das **Symbol apps**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-401">In the left panel, at the bottom, select the **Apps icon**.</span></span>
1. <span data-ttu-id="3bde1-402">Wählen Sie im rechten Bereich unten die Option **benutzerdefinierte App hochladen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-402">In the right panel, at the bottom, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="3bde1-403">Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.</span><span class="sxs-lookup"><span data-stu-id="3bde1-403">Navigate to the `TeamsAppManifest` folder and upload the zipped manifest.</span></span>
<span data-ttu-id="3bde1-404">Der folgende Assistent wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3bde1-404">The following wizard is displayed:</span></span>

    ![Upload von auth-bot-Teams](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. <span data-ttu-id="3bde1-406">Klicken Sie auf die Schaltfläche **zu einem Team hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="3bde1-406">Select the **Add to a team** button.</span></span>
1. <span data-ttu-id="3bde1-407">Wählen Sie im nächsten Fenster das Team aus, in dem Sie den bot verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3bde1-407">In the next window, select the team where you want to use the bot.</span></span>
1. <span data-ttu-id="3bde1-408">Wählen Sie die Schaltfläche **Einrichten eines bot** aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-408">Select the **Set up a bot** button.</span></span>
1. <span data-ttu-id="3bde1-409">Wählen Sie im linken Bereich die drei Punkte (#a3) aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-409">Select the three dots (&#x25cf;&#x25cf;&#x25cf;) in the left panel.</span></span> <span data-ttu-id="3bde1-410">Wählen Sie dann das **App Studio** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-410">Then select the **App Studio** icon.</span></span>
1. <span data-ttu-id="3bde1-411">Wählen Sie die Registerkarte **Manifest-Editor** aus. Das Symbol für den von Ihnen hochgeladenen bot sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-411">Select the **Manifest editor** tab. You should see the icon for the bot you uploaded.</span></span>
1. <span data-ttu-id="3bde1-412">Außerdem sollten Sie in der Lage sein, den bot als Kontakt in der Chat Liste zu sehen, den Sie zum Austauschen von Nachrichten mit dem bot verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3bde1-412">Also, you should be able to see the bot listed as a contact in the chat list that you can use to exchange messages with the bot.</span></span>

### <a name="testing-the-bot-locally-in-teams"></a><span data-ttu-id="3bde1-413">Testen des bot lokal in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3bde1-413">Testing the bot locally in Teams</span></span>

<span data-ttu-id="3bde1-414">Microsoft Teams ist ein vollständig Cloud-basiertes Produkt, für das alle Dienste, auf die es zugreift, über die Cloud über HTTPS-Endpunkte verfügbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-414">Microsoft Teams is an entirely cloud-based product, it requires all services it accesses to be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="3bde1-415">Um den bot (unser Beispiel) für die Arbeit in Microsoft Teams zu aktivieren, müssen Sie daher entweder den Code in der Cloud Ihrer Wahl veröffentlichen oder eine lokal ausgeführten Instanz über ein **Tunneling** -Tool Extern zugänglich machen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-415">Therefore, to enable the bot (our sample) to work in Teams, you need to either publish the code to the cloud of your choice, or make a locally running instance externally accessible via a **tunneling** tool.</span></span> <span data-ttu-id="3bde1-416">Wir empfehlen [ngrok](https://ngrok.com/download), mit dem eine extern adressierbare URL für einen Port erstellt wird, den Sie lokal auf Ihrem Computer öffnen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-416">We recommend  [ngrok](https://ngrok.com/download), which creates an externally addressable URL for a port you open locally on your machine.</span></span>
<span data-ttu-id="3bde1-417">Führen Sie die folgenden Schritte aus, um ngrok als Vorbereitung für die lokale Ausführung Ihrer Microsoft Teams-App einzurichten:</span><span class="sxs-lookup"><span data-stu-id="3bde1-417">To set up ngrok in preparation for running your Microsoft Teams app locally, follow these steps:</span></span>

1. <span data-ttu-id="3bde1-418">Wechseln Sie in einem Terminalfenster zu dem Verzeichnis, in `ngrok.exe` dem Sie installiert haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-418">In a terminal window, go the directory where you have `ngrok.exe` installed.</span></span> <span data-ttu-id="3bde1-419">Es wird empfohlen, den Pfad der *Umgebungsvariable* so festzulegen, dass darauf verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-419">We suggest setting the *environment variable* path to point to it.</span></span>
1. <span data-ttu-id="3bde1-420">Ausführen, beispielsweise `ngrok http 3978 --host-header=localhost:3978`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-420">Run, for example, `ngrok http 3978 --host-header=localhost:3978`.</span></span> <span data-ttu-id="3bde1-421">Ersetzen Sie die Portnummer bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="3bde1-421">Replace the port number as needed.</span></span>
<span data-ttu-id="3bde1-422">Dadurch wird ngrok gestartet, um den angegebenen Port abzuhören.</span><span class="sxs-lookup"><span data-stu-id="3bde1-422">This launches ngrok to listen on the port you specify.</span></span> <span data-ttu-id="3bde1-423">Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-423">In return, it gives you an externally addressable URL, valid for as long as ngrok is running.</span></span> <span data-ttu-id="3bde1-424">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-424">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG)<span data-ttu-id="3bde1-426">.</span><span class="sxs-lookup"><span data-stu-id="3bde1-426">.</span></span>

1. <span data-ttu-id="3bde1-427">Kopieren Sie die Weiterleitungs-HTTPS-Adresse.</span><span class="sxs-lookup"><span data-stu-id="3bde1-427">Copy the forwarding HTTPS address.</span></span> <span data-ttu-id="3bde1-428">Es sollte wie folgt aussehen: `https://dea822bf.ngrok.io/`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-428">It should be similar to the following: `https://dea822bf.ngrok.io/`.</span></span>
1. <span data-ttu-id="3bde1-429">Append `/api/messages` zu erhalten `https://dea822bf.ngrok.io/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-429">Append `/api/messages` to obtain `https://dea822bf.ngrok.io/api/messages`.</span></span> <span data-ttu-id="3bde1-430">Dies ist der **Nachrichten Endpunkt** für den bot, der lokal auf Ihrem Computer läuft und über das Internet in einem Chat in Microsoft Teams erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="3bde1-430">This is the **messages endpoint** for the bot running locally on your machine and reachable over the web in a chat in Microsoft Teams.</span></span>
1. <span data-ttu-id="3bde1-431">Ein letzter Schritt besteht darin, den Nachrichten Endpunkt des bereitgestellten bot zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-431">One final step to perform is to update the messages endpoint of the deployed bot.</span></span> <span data-ttu-id="3bde1-432">In dem Beispiel haben wir den bot in Azure bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3bde1-432">In the example, we deployed the bot in Azure.</span></span> <span data-ttu-id="3bde1-433">So \* \* lassen Sie uns diese Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="3bde1-433">So \*\*let's perform these steps:</span></span>
    1. <span data-ttu-id="3bde1-434">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="3bde1-434">In your browser navigate to the [**Azure portal**][azure-portal].</span></span>
    1. <span data-ttu-id="3bde1-435">Wählen Sie Ihre **bot-Kanal Registrierung**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-435">Select your **Bot Channel Registration**.</span></span>
    1. <span data-ttu-id="3bde1-436">Wählen Sie im linken Bereich **Einstellungen**aus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-436">In the left panel, select **Settings**.</span></span>
    1. <span data-ttu-id="3bde1-437">Geben Sie im rechten Bereich im Feld **Messaging-Endpunkt** die ngrok-URL in unserem Beispiel ein `https://dea822bf.ngrok.io/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="3bde1-437">In the right panel, in the **Messaging endpoint** box, enter the ngrok URL, in our example, `https://dea822bf.ngrok.io/api/messages`.</span></span>
1. <span data-ttu-id="3bde1-438">Starten Sie Ihren bot lokal, beispielsweise in Visual Studio Debugmodus.</span><span class="sxs-lookup"><span data-stu-id="3bde1-438">Start your bot locally, for example in Visual Studio debug mode.</span></span>
1. <span data-ttu-id="3bde1-439">Testen Sie den bot, während er lokal mit dem **Test-Webchat**des bot-Framework-Portals läuft.</span><span class="sxs-lookup"><span data-stu-id="3bde1-439">Test the bot while running locally using the Bot Framework portal's **Test Web chat**.</span></span> <span data-ttu-id="3bde1-440">Wie der Emulator erlaubt Ihnen dieser Test nicht den Zugriff auf Teams-spezifische Funktionen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-440">Like the Emulator, this test doesn't allow you to access Teams-specific functionality.</span></span>
1. <span data-ttu-id="3bde1-441">Im Terminal-Fenster, `ngrok` in dem Sie sich befinden, können Sie den HTTP-Datenverkehr zwischen dem bot und dem Chat Client sehen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-441">In the terminal window where `ngrok` is running you can see HTTP traffic between the bot and the web chat client.</span></span> <span data-ttu-id="3bde1-442">Wenn Sie eine detailliertere Ansicht wünschen, geben `http://127.0.0.1:4040` Sie in einem Browserfenster die Daten ein, die Sie aus dem vorherigen Terminalfenster erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="3bde1-442">If you want a more detailed view, in a browser window enter `http://127.0.0.1:4040` you obtained from the previous terminal window.</span></span> <span data-ttu-id="3bde1-443">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3bde1-443">The following image is an example:</span></span>

    ![Authentifizierungs-bot-Teams ngrok Tests](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png)<span data-ttu-id="3bde1-445">.</span><span class="sxs-lookup"><span data-stu-id="3bde1-445">.</span></span>

> [!NOTE]
> <span data-ttu-id="3bde1-446">Wenn Sie ngrok beenden und neu starten, ändert sich die URL.</span><span class="sxs-lookup"><span data-stu-id="3bde1-446">If you stop and restart ngrok, the URL changes.</span></span> <span data-ttu-id="3bde1-447">Um ngrok in Ihrem Projekt zu verwenden, müssen Sie in Abhängigkeit von den von Ihnen verwendeten Funktionen alle URL-Verweise aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3bde1-447">To use ngrok in your project, and depending on the capabilities you're using, you must update all URL references.</span></span>

## <a name="additional-information"></a><span data-ttu-id="3bde1-448">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3bde1-448">Additional information</span></span>

### <a name="teamsappmanifestmanifestjson"></a><span data-ttu-id="3bde1-449">TeamsAppManifest/Manifest. JSON</span><span class="sxs-lookup"><span data-stu-id="3bde1-449">TeamsAppManifest/manifest.json</span></span>

<span data-ttu-id="3bde1-450">Dieses Manifest enthält Informationen, die Microsoft Teams benötigt, um eine Verbindung mit dem bot herzustellen.</span><span class="sxs-lookup"><span data-stu-id="3bde1-450">This manifest contains information needed by Microsoft Teams to connect with the bot.</span></span>  

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

<span data-ttu-id="3bde1-451">Bei der Authentifizierung verhält sich Microsoft Teams geringfügig anders als andere Kanäle, wie unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="3bde1-451">With authentication, Teams behaves slightly differently than other channels, as explained below.</span></span>

### <a name="handling-invoke-activity"></a><span data-ttu-id="3bde1-452">Behandeln von Invoke-Aktivität</span><span class="sxs-lookup"><span data-stu-id="3bde1-452">Handling Invoke Activity</span></span>

<span data-ttu-id="3bde1-453">Eine **Invoke-Aktivität** wird an den bot statt an die Ereignisaktivität gesendet, die von anderen Kanälen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-453">An **Invoke Activity** is sent to the bot rather than the Event Activity used by other channels.</span></span>
<span data-ttu-id="3bde1-454">Dies wird durch Unterklassen für das **ActivityHandler**getan.</span><span class="sxs-lookup"><span data-stu-id="3bde1-454">This is done by sub-classing the **ActivityHandler**.</span></span>

<span data-ttu-id="3bde1-455">**Bots/DialogBot. cs**</span><span class="sxs-lookup"><span data-stu-id="3bde1-455">**Bots/DialogBot.cs**</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="3bde1-456">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="3bde1-456">C#/.NET</span></span>](#tab/dotnet)

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

<span data-ttu-id="3bde1-457">**Bots/TeamsBot. cs**</span><span class="sxs-lookup"><span data-stu-id="3bde1-457">**Bots/TeamsBot.cs**</span></span>

<span data-ttu-id="3bde1-458">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-458">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a><span data-ttu-id="3bde1-459">TeamsActivityHandler.cs</span><span class="sxs-lookup"><span data-stu-id="3bde1-459">TeamsActivityHandler.cs</span></span>

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

# <a name="pythontabpython"></a>[<span data-ttu-id="3bde1-460">Python</span><span class="sxs-lookup"><span data-stu-id="3bde1-460">Python</span></span>](#tab/python)

<span data-ttu-id="3bde1-461">**Bots/dialog_bot. py**</span><span class="sxs-lookup"><span data-stu-id="3bde1-461">**bots/dialog_bot.py**</span></span>

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

<span data-ttu-id="3bde1-462">**Bots/teams_bot. py**</span><span class="sxs-lookup"><span data-stu-id="3bde1-462">**bots/teams_bot.py**</span></span>

<span data-ttu-id="3bde1-463">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-463">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)] 

<span data-ttu-id="3bde1-464">**Dialoge/main_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="3bde1-464">**dialogs/main_dialog.py**</span></span>

<span data-ttu-id="3bde1-465">Verwenden `begin_dialog` Sie in einem Dialogschritt zum Starten der OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-465">Within a dialog step, use `begin_dialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="3bde1-466">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Token-Antwortereignis, ohne dass der Benutzer aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="3bde1-466">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="3bde1-467">Andernfalls wird der Benutzer aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-467">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="3bde1-468">Der Azure bot-Dienst sendet das Token-Antwortereignis, nachdem der Benutzer versucht, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="3bde1-468">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

<span data-ttu-id="3bde1-469">Überprüfen Sie im folgenden Dialogschritt auf das vorhanden sein eines Tokens im Ergebnis des vorherigen Schritts.</span><span class="sxs-lookup"><span data-stu-id="3bde1-469">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="3bde1-470">Wenn es sich nicht um NULL handelt, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="3bde1-470">If it is not null, the user successfully signed in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=54-65)]

<span data-ttu-id="3bde1-471">**Dialoge/logout_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="3bde1-471">**dialogs/logout_dialog.py**</span></span>

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

## <a name="further-reading"></a><span data-ttu-id="3bde1-472">Weiterführende Literatur</span><span class="sxs-lookup"><span data-stu-id="3bde1-472">Further reading</span></span>

- [<span data-ttu-id="3bde1-473">Hinzufügen von Authentifizierung zu Ihrem bot über Azure bot-Dienst</span><span class="sxs-lookup"><span data-stu-id="3bde1-473">Add authentication to your bot via Azure Bot Service</span></span>](https://aka.ms/azure-bot-add-authentication)

<!-- Footnote-style links -->

[azure-portal]: https://ms.portal.azure.com

[concept-basics]: https://docs.microsoft.com/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0
[concept-state]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-state?view=azure-bot-service-4.0
[concept-dialogs]: https://docs.microsoft.com/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0
[simple-dialog]: https://docs.microsoft.com/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0

[teams-auth-bot]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/46.teams-auth

[teams-auth-bot-py]: https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/python/46.teams-auth

[azure-aad-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview
[aad-registration-blade]: https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredAppsPreview
