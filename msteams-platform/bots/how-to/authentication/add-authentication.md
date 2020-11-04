---
title: Hinzufügen von Authentifizierung zu ihren Teams-bot
author: clearab
description: Vorgehensweise Hinzufügen von OAuth-Authentifizierung zu einem bot in Microsoft Teams.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 8e396842cb514eb3d3df6b71cafe9e79d9c2957a
ms.sourcegitcommit: df9448681d2a81f1029aad5a5e1989cd438d1ae0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877092"
---
# <a name="add-authentication-to-your-teams-bot"></a><span data-ttu-id="d1bf5-103">Hinzufügen von Authentifizierung zu ihren Teams-bot</span><span class="sxs-lookup"><span data-stu-id="d1bf5-103">Add authentication to your Teams bot</span></span>

<span data-ttu-id="d1bf5-104">Es gibt Situationen, in denen Sie möglicherweise Bots in Microsoft Teams erstellen müssen, die im Namen des Benutzers auf Ressourcen zugreifen können, beispielsweise einen e-Mail-Dienst.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-104">There are times when you may need to create bots in Microsoft Teams that can access resources on behalf of the user, such as a mail service.</span></span>

<span data-ttu-id="d1bf5-105">In diesem Artikel wird die Verwendung der Azure bot Service V4 SDK-Authentifizierung basierend auf OAuth 2,0.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-105">This article demonstrates how to use Azure Bot Service v4 SDK authentication, based on OAuth 2.0.</span></span> <span data-ttu-id="d1bf5-106">Dies erleichtert die Entwicklung eines bot, der Authentifizierungstoken basierend auf den Anmeldeinformationen des Benutzers verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-106">This makes it easier to develop a bot that can use authentication tokens based on the user's credentials.</span></span> <span data-ttu-id="d1bf5-107">Key in all dies ist die Verwendung von **Identitätsanbietern** , wie wir später sehen werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-107">Key in all this is the use of **identity providers** , as we will see later.</span></span>

<span data-ttu-id="d1bf5-108">OAuth 2.0 ist ein offener Standard für Authentifizierung und Autorisierung, der von Azure Active Directory (Azure AD) und vielen anderen Identitätsanbietern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-108">OAuth 2.0 is an open standard for authentication and authorization used by Azure Active Directory (Azure AD) and many other identity providers.</span></span> <span data-ttu-id="d1bf5-109">Ein grundlegendes Verständnis von OAuth 2,0 ist eine Voraussetzung für die Verwendung von Authentifizierung in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-109">A basic understanding of OAuth 2.0 is a prerequisite for working with authentication in Teams.</span></span>

<span data-ttu-id="d1bf5-110">Ein grundlegendes Verständnis finden Sie in [OAuth 2 vereinfacht](https://aka.ms/oauth2-simplified) , und [OAuth 2,0](https://oauth.net/2/) für die vollständige Spezifikation.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-110">See [OAuth 2 Simplified](https://aka.ms/oauth2-simplified) for a basic understanding, and [OAuth 2.0](https://oauth.net/2/) for the complete specification.</span></span>

<span data-ttu-id="d1bf5-111">Weitere Informationen darüber, wie der Azure bot-Dienst die Authentifizierung verarbeitet, finden Sie unter [User Authentication in a Conversation](https://aka.ms/azure-bot-authentication).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-111">For more information about how the Azure Bot Service handles authentication, see [User authentication within a conversation](https://aka.ms/azure-bot-authentication).</span></span>

<span data-ttu-id="d1bf5-112">In diesem Artikel erhalten Sie Informationen zu folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-112">In this article you'll learn:</span></span>

- <span data-ttu-id="d1bf5-113">**Erstellen eines Authentifizierungs aktivierten bot**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-113">**How to create an authentication-enabled bot**.</span></span> <span data-ttu-id="d1bf5-114">Sie verwenden [CS-auth-Sample][teams-auth-bot-cs] zum Verarbeiten von Anmeldeinformationen für die Benutzeranmeldung und zum Generieren des Authentifizierungstokens.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-114">You'll use [cs-auth-sample][teams-auth-bot-cs] to handle user sign-in credentials and the generating the authentication token.</span></span>
- <span data-ttu-id="d1bf5-115">**Wie Sie den bot in Azure bereitstellen und einem Identitätsanbieter zuordnen**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-115">**How to deploy the bot to Azure and associate it with an identity provider**.</span></span> <span data-ttu-id="d1bf5-116">Der Anbieter gibt ein Token basierend auf den Anmeldeinformationen für die Benutzeranmeldung aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-116">The provider issues a token based on user sign-in credentials.</span></span> <span data-ttu-id="d1bf5-117">Der Bot kann mithilfe des Tokens auf Ressourcen zugreifen, beispielsweise auf einen e-Mail-Dienst, für den eine Authentifizierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-117">The bot can use the token to access resources, such as a mail service, which require authentication.</span></span> <span data-ttu-id="d1bf5-118">Weitere Informationen finden Sie unter  [Microsoft Teams-Authentifizierungs Fluss für Bots](auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-118">For more information see  [Microsoft Teams authentication flow for bots](auth-flow-bot.md).</span></span>
- <span data-ttu-id="d1bf5-119">**Vorgehensweise zum Integrieren des bot in Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-119">**How to integrate the bot within Microsoft Teams**.</span></span> <span data-ttu-id="d1bf5-120">Nachdem der bot integriert wurde, können Sie sich in einem Chat anmelden und Nachrichten damit austauschen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-120">Once the bot has been integrated, you can sign in and exchange messages with it in a chat.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1bf5-121">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d1bf5-121">Prerequisites</span></span>

- <span data-ttu-id="d1bf5-122">Kenntnisse der [grundlegenden][concept-basics]Funktionen von bot, der [Verwaltung von Status][concept-state], der [Dialogfeld Bibliothek][concept-dialogs]und der [Implementierung eines sequenziellen Unterhaltungs Flusses][simple-dialog].</span><span class="sxs-lookup"><span data-stu-id="d1bf5-122">Knowledge of [bot basics][concept-basics], [managing state][concept-state], the [dialogs library][concept-dialogs], and how to [implement sequential conversation flow][simple-dialog].</span></span>
- <span data-ttu-id="d1bf5-123">Kenntnisse in Azure und OAuth 2,0-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-123">Knowledge of Azure and OAuth 2.0 development.</span></span>
- <span data-ttu-id="d1bf5-124">Die aktuellen Versionen von Visual Studio und git.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-124">The current versions of Visual Studio and Git.</span></span>
- <span data-ttu-id="d1bf5-125">Azure-Konto.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-125">Azure account.</span></span> <span data-ttu-id="d1bf5-126">Bei Bedarf können Sie ein [Kostenloses Azure-Konto](https://azure.microsoft.com/free/)erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-126">If needed, you can create an [Azure free account](https://azure.microsoft.com/free/).</span></span>
- <span data-ttu-id="d1bf5-127">Im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-127">The following sample.</span></span>

    | <span data-ttu-id="d1bf5-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d1bf5-128">Sample</span></span> | <span data-ttu-id="d1bf5-129">BotBuilder-Version</span><span class="sxs-lookup"><span data-stu-id="d1bf5-129">BotBuilder version</span></span> | <span data-ttu-id="d1bf5-130">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="d1bf5-130">Demonstrates</span></span> |
    |:---|:---:|:---|
    | <span data-ttu-id="d1bf5-131">**Bot-Authentifizierung** in [CS-auth-Sample][teams-auth-bot-cs]</span><span class="sxs-lookup"><span data-stu-id="d1bf5-131">**Bot authentication** in [cs-auth-sample][teams-auth-bot-cs]</span></span> | <span data-ttu-id="d1bf5-132">v4</span><span class="sxs-lookup"><span data-stu-id="d1bf5-132">v4</span></span> | <span data-ttu-id="d1bf5-133">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="d1bf5-133">OAuthCard support</span></span> |
    | <span data-ttu-id="d1bf5-134">**Bot-Authentifizierung** in [js-auth-Sample][teams-auth-bot-js]</span><span class="sxs-lookup"><span data-stu-id="d1bf5-134">**Bot authentication** in [js-auth-sample][teams-auth-bot-js]</span></span> | <span data-ttu-id="d1bf5-135">v4</span><span class="sxs-lookup"><span data-stu-id="d1bf5-135">v4</span></span>| <span data-ttu-id="d1bf5-136">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="d1bf5-136">OAuthCard support</span></span>  |
    | <span data-ttu-id="d1bf5-137">**Bot-Authentifizierung** in [py-auth-Sample][teams-auth-bot-py]</span><span class="sxs-lookup"><span data-stu-id="d1bf5-137">**Bot authentication** in [py-auth-sample][teams-auth-bot-py]</span></span> | <span data-ttu-id="d1bf5-138">v4</span><span class="sxs-lookup"><span data-stu-id="d1bf5-138">v4</span></span> | <span data-ttu-id="d1bf5-139">OAuthCard-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="d1bf5-139">OAuthCard support</span></span> |

## <a name="create-the-resource-group"></a><span data-ttu-id="d1bf5-140">Erstellen der Ressourcengruppe</span><span class="sxs-lookup"><span data-stu-id="d1bf5-140">Create the resource group</span></span>

<span data-ttu-id="d1bf5-141">Die Ressourcengruppe und der Dienstplan sind nicht unbedingt erforderlich, Sie ermöglichen jedoch das bequeme Freigeben der von Ihnen erstellten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-141">The resource group and the service plan aren't strictly necessary, but they allow you to conveniently release the resources you create.</span></span> <span data-ttu-id="d1bf5-142">Dies ist eine bewährte Methode, um Ihre Ressourcen organisiert und verwaltbar zu halten.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-142">This is good practice for keeping your resources organized and manageable.</span></span>

<span data-ttu-id="d1bf5-143">Sie verwenden eine Ressourcengruppe, um einzelne Ressourcen für das bot-Framework zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-143">You use a resource group to create individual resources for the Bot Framework.</span></span> <span data-ttu-id="d1bf5-144">Stellen Sie für die Leistung sicher, dass sich diese Ressourcen in derselben Azure-Region befinden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-144">For performance, ensure that these resources are located in the same Azure region.</span></span>

1. <span data-ttu-id="d1bf5-145">Melden Sie sich in Ihrem Browser beim [**Azure-Portal**][azure-portal]an.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-145">In your browser, sign into the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="d1bf5-146">Wählen Sie im linken Navigationsbereich **Ressourcengruppen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-146">In the left navigation panel, select **Resource groups**.</span></span>
1. <span data-ttu-id="d1bf5-147">Wählen Sie in der oberen linken Ecke des angezeigten Fensters Tab **Hinzufügen** aus, um eine neue Ressourcengruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-147">In the upper left of the displayed window, select **Add** tab to create a new resource group.</span></span> <span data-ttu-id="d1bf5-148">Sie werden aufgefordert, Folgendes bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-148">You'll be prompted to provide the following:</span></span>
    1. <span data-ttu-id="d1bf5-149">**Abonnement** :</span><span class="sxs-lookup"><span data-stu-id="d1bf5-149">**Subscription**.</span></span> <span data-ttu-id="d1bf5-150">Verwenden Sie Ihr vorhandenes Abonnement.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-150">Use your existing subscription.</span></span>
    1. <span data-ttu-id="d1bf5-151">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-151">**Resource group**.</span></span> <span data-ttu-id="d1bf5-152">Geben Sie den Namen für die Ressourcengruppe ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-152">Enter the name for the resource group.</span></span> <span data-ttu-id="d1bf5-153">Ein Beispiel könnte  *TeamsResourceGroup* sein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-153">An example could be  *TeamsResourceGroup*.</span></span> <span data-ttu-id="d1bf5-154">Beachten Sie, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-154">Remember that the name must be unique.</span></span>
    1. <span data-ttu-id="d1bf5-155">Wählen Sie im Dropdownmenü **Region** die Option *West US* oder eine Region, die sich in der Nähe ihrer Anwendungen befindet.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-155">From the **Region** drop-down menu, select *West US* , or a region close to your applications.</span></span>
    1. <span data-ttu-id="d1bf5-156">Klicken Sie auf die Schaltfläche **überprüfen und erstellen** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-156">Select the **Review and create** button.</span></span> <span data-ttu-id="d1bf5-157">Es sollte ein Banner angezeigt werden, das die *übergebene Validierung* liest.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-157">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="d1bf5-158">Klicken Sie auf die Schaltfläche **Erstellen** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-158">Select the **Create** button.</span></span> <span data-ttu-id="d1bf5-159">Es kann einige Minuten dauern, bis die Ressourcengruppe erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-159">It may take a few minutes to create the resource group.</span></span>

> [!TIP]
> <span data-ttu-id="d1bf5-160">Wie bei den Ressourcen, die Sie später in diesem Lernprogramm erstellen, empfiehlt es sich, diese Ressourcengruppe für einfachen Zugriff an das Dashboard zu anheften.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-160">As with the resources you'll create later in this tutorial, it's a good idea to pin this resource group to your dashboard for easy access.</span></span> <span data-ttu-id="d1bf5-161">Wenn Sie dies möchten, wählen Sie das Pin-Symbol & # 128204; in der oberen rechten Ecke des Dashboards.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-161">If you'd like to do so, select the pin icon &#128204; in the upper right of the dashboard.</span></span>

## <a name="create-the-service-plan"></a><span data-ttu-id="d1bf5-162">Erstellen des Dienstplans</span><span class="sxs-lookup"><span data-stu-id="d1bf5-162">Create the service plan</span></span>

1. <span data-ttu-id="d1bf5-163">Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Ressource erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-163">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Create a resource**.</span></span>
1. <span data-ttu-id="d1bf5-164">Geben Sie im Suchfeld den Text *App-Dienst Plan* ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-164">In the search box, type *App Service Plan*.</span></span> <span data-ttu-id="d1bf5-165">Wählen Sie die **App-Service Plan** Karte in den Suchergebnissen aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-165">Select the **App Service Plan** card from the search results.</span></span>
1. <span data-ttu-id="d1bf5-166">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-166">Select **Create**.</span></span>
1. <span data-ttu-id="d1bf5-167">Sie werden aufgefordert, die folgenden Informationen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-167">You'll be asked to provide the following information:</span></span>
    1. <span data-ttu-id="d1bf5-168">**Abonnement** :</span><span class="sxs-lookup"><span data-stu-id="d1bf5-168">**Subscription**.</span></span> <span data-ttu-id="d1bf5-169">Sie können ein vorhandenes Abonnement verwenden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-169">You can use an existing subscription.</span></span>
    1. <span data-ttu-id="d1bf5-170">**Ressourcengruppe**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-170">**Resource Group**.</span></span> <span data-ttu-id="d1bf5-171">Wählen Sie die Gruppe aus, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-171">Select the group you created earlier.</span></span>
    1. <span data-ttu-id="d1bf5-172">**Name**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-172">**Name**.</span></span> <span data-ttu-id="d1bf5-173">Geben Sie den Namen für den Service Plan ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-173">Enter the name for the service plan.</span></span> <span data-ttu-id="d1bf5-174">Ein Beispiel könnte  *TeamsServicePlan* sein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-174">An example could be  *TeamsServicePlan*.</span></span> <span data-ttu-id="d1bf5-175">Beachten Sie, dass der Name innerhalb der Gruppe eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-175">Remember that the name must be unique, within the group.</span></span>
    1. <span data-ttu-id="d1bf5-176">**Betriebs System**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-176">**Operating System**.</span></span> <span data-ttu-id="d1bf5-177">Wählen Sie *Windows* oder Ihr entsprechendes Betriebssystem aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-177">Select *Windows* or your applicable OS.</span></span>
    1. <span data-ttu-id="d1bf5-178">**Region**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-178">**Region**.</span></span> <span data-ttu-id="d1bf5-179">Wählen Sie " *West US* " oder eine Region in der Nähe ihrer Anwendungen aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-179">Select *West US* or a region close to your applications.</span></span>
    1. <span data-ttu-id="d1bf5-180">**Preisstufe**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-180">**Pricing Tier**.</span></span> <span data-ttu-id="d1bf5-181">Stellen Sie sicher, dass *Standard S1* ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-181">Make sure that *Standard S1* is selected.</span></span> <span data-ttu-id="d1bf5-182">Dies sollte der Standardwert sein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-182">This should be the default value.</span></span>
    1. <span data-ttu-id="d1bf5-183">Klicken Sie auf die Schaltfläche **überprüfen und erstellen** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-183">Select the **Review and create** button.</span></span> <span data-ttu-id="d1bf5-184">Es sollte ein Banner angezeigt werden, das die *übergebene Validierung* liest.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-184">You should see a banner that reads *Validation passed*.</span></span>
    1. <span data-ttu-id="d1bf5-185">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-185">Select **Create**.</span></span> <span data-ttu-id="d1bf5-186">Es kann einige Minuten dauern, bis Sie den App-Dienstplan erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-186">It may take a few minutes to create the app service plan.</span></span> <span data-ttu-id="d1bf5-187">Der Plan wird in der Ressourcengruppe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-187">The plan will be listed in the resource group.</span></span>

## <a name="create-the-bot-channels-registration"></a><span data-ttu-id="d1bf5-188">Erstellen der Registrierung für bot-Kanäle</span><span class="sxs-lookup"><span data-stu-id="d1bf5-188">Create the bot channels registration</span></span>

<span data-ttu-id="d1bf5-189">Die Registrierung von bot-Kanälen registriert Ihren Webdienst als bot mit dem bot-Framework, vorausgesetzt, Sie verfügen über eine Microsoft-App-ID und ein App-Kennwort (geheimer Client Schlüssel).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-189">The bot channels registration registers your web service as a bot with the Bot Framework, provided you have a Microsoft App Id and App password (client secret).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1bf5-190">Sie müssen ihren bot nur registrieren, wenn er nicht in Azure gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-190">You only need to register your bot if it is not hosted in Azure.</span></span> <span data-ttu-id="d1bf5-191">Wenn Sie [einen bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) über das Azure-Portal erstellt haben, ist er bereits beim Dienst registriert.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-191">If you [created a bot](/azure/bot-service/abs-quickstart?view=azure-bot-service-4.0&viewFallbackFrom=azure-bot-service-3.0&preserve-view=true) through the Azure portal then it is already registered with the service.</span></span> <span data-ttu-id="d1bf5-192">Wenn Sie Ihren bot über das [bot-Framework](https://dev.botframework.com/bots/new) oder [AppStudio](~/concepts/build-and-test/app-studio-overview.md) erstellt haben, ist Ihr bot nicht in Azure registriert.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-192">If you created your bot through the [Bot Framework](https://dev.botframework.com/bots/new) or [AppStudio](~/concepts/build-and-test/app-studio-overview.md) your bot isn't registered in Azure.</span></span>

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

> [!NOTE]
> <span data-ttu-id="d1bf5-193">Die Ressourcen zur Registrierung von bot-Kanälen zeigen die **globale** Region an, selbst wenn Sie West US ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-193">The Bot Channels Registration resource will show the **Global** region even if you selected West US.</span></span> <span data-ttu-id="d1bf5-194">Dies entspricht dem erwarteten Verhalten.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-194">This is expected.</span></span>

<span data-ttu-id="d1bf5-195">Weitere Informationen finden Sie unter [Erstellen eines bot für Teams](../create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-195">For more information, see [Create a bot for Teams](../create-a-bot-for-teams.md).</span></span>

## <a name="create-the-identity-provider"></a><span data-ttu-id="d1bf5-196">Erstellen des Identitätsanbieters</span><span class="sxs-lookup"><span data-stu-id="d1bf5-196">Create the identity provider</span></span>

<span data-ttu-id="d1bf5-197">Sie benötigen einen Identitätsanbieter, der für die Authentifizierung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-197">You need an identity provider that can be used for authentication.</span></span>
<span data-ttu-id="d1bf5-198">In diesem Verfahren verwenden Sie einen Azure AD Anbieter; Außerdem können andere Azure Ad Unterstützte Identitätsanbieter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-198">In this procedure you'll use an Azure AD provider; other Azure AD supported identity providers can also be used.</span></span>

1. <span data-ttu-id="d1bf5-199">Wählen Sie im [**Azure-Portal**][azure-portal]im linken Navigationsbereich die Option **Azure Active Directory** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-199">In the [**Azure portal**][azure-portal], on the left navigation panel, select **Azure Active Directory**.</span></span>
    > [!TIP]
    > <span data-ttu-id="d1bf5-200">Sie müssen diese Azure AD Ressource in einem Mandanten erstellen und registrieren, in dem Sie die Berechtigung zum Delegieren von von einer Anwendung angeforderten Berechtigungen erteilen können.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-200">You'll need to create and register this Azure AD resource in a tenant in which you can consent to delegate permissions requested by an application.</span></span>
    > <span data-ttu-id="d1bf5-201">Anweisungen zum Erstellen eines Mandanten finden Sie unter [zugreifen auf das Portal und Erstellen eines Mandanten](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-201">For instruction on creating a tenant, see [Access the portal and create a tenant](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant).</span></span>
1. <span data-ttu-id="d1bf5-202">Wählen Sie im linken Bereich **App-Registrierungen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-202">In the left panel, select **App registrations**.</span></span>
1. <span data-ttu-id="d1bf5-203">Wählen Sie im rechten Bereich die Registerkarte **neue Registrierung** in der oberen linken Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-203">In the right panel, select the **New registration** tab, in the upper left.</span></span>
1. <span data-ttu-id="d1bf5-204">Sie werden aufgefordert, die folgenden Informationen anzugeben:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-204">You'll be asked to provide the following information:</span></span>
   1. <span data-ttu-id="d1bf5-205">**Name**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-205">**Name**.</span></span> <span data-ttu-id="d1bf5-206">Geben Sie den Namen der Anwendung ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-206">Enter the name for the application.</span></span> <span data-ttu-id="d1bf5-207">Ein Beispiel könnte  *BotTeamsIdentity* sein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-207">An example could be  *BotTeamsIdentity*.</span></span> <span data-ttu-id="d1bf5-208">Beachten Sie, dass der Name eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-208">Remember that the name must be unique.</span></span>
   1. <span data-ttu-id="d1bf5-209">Wählen Sie die **unterstützten Kontotypen** für Ihre Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-209">Select the **Supported account types** for your application.</span></span> <span data-ttu-id="d1bf5-210">Wählen Sie *Konten in einem beliebigen Organisations Verzeichnis (beliebige Azure AD Verzeichnis – Multimandanten) und persönliche Microsoft-Konten (beispielsweise Skype, Xbox)* aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-210">Select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
   1. <span data-ttu-id="d1bf5-211">Für den **Umleitungs-URI** :</span><span class="sxs-lookup"><span data-stu-id="d1bf5-211">For the **Redirect URI** :</span></span><br/>
       <span data-ttu-id="d1bf5-212">&#x2713;wählen Sie das **Webpart** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-212">&#x2713;Select **Web**.</span></span> <br/>
       <span data-ttu-id="d1bf5-213">&#x2713; legen Sie die URL auf fest `https://token.botframework.com/.auth/web/redirect` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-213">&#x2713; Set the URL to `https://token.botframework.com/.auth/web/redirect`.</span></span>
   1. <span data-ttu-id="d1bf5-214">Wählen Sie **Registrieren** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-214">Select **Register**.</span></span>

1. <span data-ttu-id="d1bf5-215">Nach der Erstellung zeigt Azure die Übersichts **Seite für die APP** an.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-215">Once it is created, Azure displays the **Overview** page for the app.</span></span> <span data-ttu-id="d1bf5-216">Kopieren Sie die folgenden Informationen, und speichern Sie Sie in einer Datei:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-216">Copy and save the following information to a file:</span></span>

    1. <span data-ttu-id="d1bf5-217">Der Wert der **Anwendungs-ID (Client)** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-217">The **Application (client) ID** value.</span></span> <span data-ttu-id="d1bf5-218">Sie verwenden diesen Wert später als *Client-ID* , wenn Sie diese Azure-Identitäts Anwendung mit Ihrem bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-218">You'll use this value later as the *Client ID* when you register this Azure identity application with your bot.</span></span>
    1. <span data-ttu-id="d1bf5-219">Der **Verzeichnis Wert (Mandant) ID** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-219">The **Directory (tenant) ID** value.</span></span> <span data-ttu-id="d1bf5-220">Sie werden diesen Wert auch später als *Mandanten-ID* verwenden, um diese Azure-Identitäts Anwendung mit Ihrem bot zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-220">You'll also use this value later as the *Tenant ID* to register this Azure identity application with your bot.</span></span>

1. <span data-ttu-id="d1bf5-221">Wählen Sie im linken Bereich **Zertifikate & Secrets** aus, um einen geheimen Client Schlüssel für Ihre Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-221">In the left panel, select **Certificates & secrets** to create a client secret for your application.</span></span>

   1. <span data-ttu-id="d1bf5-222">Wählen Sie unter **Client Secrets** &#x2795; **neuen geheimen Client Schlüssel** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-222">Under **Client secrets** , select &#x2795; **New client secret**.</span></span>
   1. <span data-ttu-id="d1bf5-223">Fügen Sie eine Beschreibung hinzu, um dieses Geheimnis von anderen Personen zu identifizieren, die Sie für diese APP möglicherweise erstellen müssen, beispielsweise für die *app "bot Identity" in Microsoft Teams*.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-223">Add a description to identify this secret from others you might need to create for this app, such as *Bot identity app in Teams*.</span></span>
   1. <span data-ttu-id="d1bf5-224">Festlegen **läuft** auf Ihre Auswahl ab.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-224">Set **Expires** to your selection.</span></span>
   1. <span data-ttu-id="d1bf5-225">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-225">Select **Add**.</span></span>
   1. <span data-ttu-id="d1bf5-226">**Notieren Sie den geheimen Schlüssel** , bevor Sie diese Seite verlassen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-226">Before leaving this page, **record the secret**.</span></span> <span data-ttu-id="d1bf5-227">Diesen Wert verwenden Sie später als _geheimer Client Schlüssel_ , wenn Sie Ihre Azure AD Anwendung mit Ihrem bot registrieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-227">You'll use this value later as the _Client secret_ when you register your Azure AD application with your bot.</span></span>

### <a name="configure-the-identity-provider-connection-and-register-it-with-the-bot"></a><span data-ttu-id="d1bf5-228">Konfigurieren Sie die Verbindung mit dem Identitätsanbieter, und registrieren Sie Sie mit dem bot.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-228">Configure the identity provider connection and register it with the bot</span></span>

<span data-ttu-id="d1bf5-229">Hinweis: Es gibt zwei Optionen für Dienstanbieter hier – Azure AD v1 und Azure AD v2.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-229">Note-there are two options for Service Providers here-Azure AD V1 and Azure AD V2.</span></span>  <span data-ttu-id="d1bf5-230">Die Unterschiede zwischen den beiden Anbietern werden [hier](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison)zusammengefasst, im Allgemeinen bietet v2 jedoch mehr Flexibilität im Hinblick auf das Ändern von bot-Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-230">The differences between the two providers are summarized [here](https://docs.microsoft.com/azure/active-directory/azuread-dev/azure-ad-endpoint-comparison), but in general, V2 provides more flexibility with respect to changing bot permissions.</span></span>  <span data-ttu-id="d1bf5-231">Graph-API-Berechtigungen werden im Feld Bereiche aufgelistet, und wenn neue hinzugefügt werden, können Benutzer den neuen Berechtigungen für die nächste Anmeldung zustimmen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-231">Graph API permissions are listed in the scopes field, and as new ones are added, bots will allow users to consent to the new permissions on the next sign in.</span></span>  <span data-ttu-id="d1bf5-232">Für v1 muss die bot-Zustimmung vom Benutzer gelöscht werden, damit im Dialogfeld OAuth neue Berechtigungen zur Eingabe aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-232">For V1, the bot consent must be deleted by the user for new permissions to be prompted in the OAuth dialog.</span></span> 

#### <a name="azure-ad-v1"></a><span data-ttu-id="d1bf5-233">Azure AD v1</span><span class="sxs-lookup"><span data-stu-id="d1bf5-233">Azure AD V1</span></span>

1. <span data-ttu-id="d1bf5-234">Wählen Sie im [**Azure-Portal**][azure-portal]ihre Ressourcengruppe aus dem Dashboard aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-234">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="d1bf5-235">Wählen Sie Ihren bot-Kanal Registrierungslink aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-235">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="d1bf5-236">Wählen Sie auf der Seite Ressource die Option **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-236">On the resource page, select **Settings**.</span></span>
1. <span data-ttu-id="d1bf5-237">Wählen Sie unter **OAuth-Verbindungseinstellungen** am unteren Rand der Seite die Option **Einstellung hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-237">Under **OAuth Connection Settings** near the bottom of the page, select **Add Setting**.</span></span>
1. <span data-ttu-id="d1bf5-238">Füllen Sie das Formular wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-238">Complete the form as follows:</span></span>

    1. <span data-ttu-id="d1bf5-239">**Name**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-239">**Name**.</span></span> <span data-ttu-id="d1bf5-240">Geben Sie einen Namen für die Verbindung ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-240">Enter a name for the connection.</span></span> <span data-ttu-id="d1bf5-241">Sie verwenden diesen Namen in Ihrem bot in der `appsettings.json` Datei.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-241">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="d1bf5-242">Beispiel *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-242">For example *BotTeamsAuthADv1*.</span></span>
    1. <span data-ttu-id="d1bf5-243">**Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-243">**Service Provider**.</span></span> <span data-ttu-id="d1bf5-244">Wählen Sie **Azure Active Directory** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-244">Select **Azure Active Directory**.</span></span> <span data-ttu-id="d1bf5-245">Nachdem Sie diese Option ausgewählt haben, werden die Azure AD spezifischen Felder angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-245">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="d1bf5-246">**Client-ID**. Geben Sie die Anwendungs-ID (Client) ein, die Sie in den obigen Schritten für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-246">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="d1bf5-247">**Geheimer Client Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-247">**Client secret**.</span></span> <span data-ttu-id="d1bf5-248">Geben Sie den geheimen Schlüssel ein, den Sie in den obigen Schritten für Ihre Azure Identity-Anbieter-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-248">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="d1bf5-249">**Grant-Typ**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-249">**Grant Type**.</span></span> <span data-ttu-id="d1bf5-250">Geben Sie ein `authorization_code` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-250">Enter `authorization_code`.</span></span>
    1. <span data-ttu-id="d1bf5-251">**Anmelde-URL**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-251">**Login URL**.</span></span> <span data-ttu-id="d1bf5-252">Geben Sie ein `https://login.microsoftonline.com` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-252">Enter `https://login.microsoftonline.com`.</span></span>
    1. <span data-ttu-id="d1bf5-253">**Mandanten-ID** : Geben Sie die **Verzeichnis (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure Identity-App aufgezeichnet haben, oder **verbreitet** , je nach dem unterstützten Kontotyp, der beim Erstellen der APP für den Identitätsanbieter ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-253">**Tenant ID** , enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="d1bf5-254">Um zu entscheiden, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-254">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="d1bf5-255">Wenn Sie entweder *Konten in diesem Organisations Verzeichnis (nur Microsoft – einzelner Mandant)* oder *Konten in einem Organisations Verzeichnis (Microsoft Aad Directory-Multi Mandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die Aad-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-255">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="d1bf5-256">Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-256">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="d1bf5-257">Wenn Sie *Konten in einem beliebigen Organisations Verzeichnis (AAD Directory-Multi Mandanten und persönliche Microsoft-Konten wie Skype, Xbox, Outlook)* ausgewählt haben, geben Sie das Wort " **Common** " anstelle einer Mandanten-ID ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-257">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="d1bf5-258">Andernfalls wird die Aad-App über den Mandanten überprüfen, dessen ID ausgewählt wurde, und persönliche Microsoft-Konten ausschließen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-258">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    <span data-ttu-id="d1bf5-259">h.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-259">h.</span></span> <span data-ttu-id="d1bf5-260">Geben Sie für **Ressourcen-URL** den Eintrag ein `https://graph.microsoft.com/` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-260">For **Resource URL** , enter `https://graph.microsoft.com/`.</span></span> <span data-ttu-id="d1bf5-261">Dies wird im aktuellen Codebeispiel nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-261">This is not used in the current code sample.</span></span>  
    <span data-ttu-id="d1bf5-262">i.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-262">i.</span></span> <span data-ttu-id="d1bf5-263">Lassen Sie **Bereiche** leer.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-263">Leave **Scopes** blank.</span></span> <span data-ttu-id="d1bf5-264">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-264">The following image is an example:</span></span>

    ![Teams Bots App auth Connection String ADV1 View](../../../assets/images/authentication/auth-bot-identity-connection-adv1.png)

1. <span data-ttu-id="d1bf5-266">Wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-266">Select **Save**.</span></span>

#### <a name="azure-ad-v2"></a><span data-ttu-id="d1bf5-267">Azure AD v2</span><span class="sxs-lookup"><span data-stu-id="d1bf5-267">Azure AD V2</span></span>

1. <span data-ttu-id="d1bf5-268">Wählen Sie im [**Azure-Portal**][azure-portal]ihre Ressourcengruppe aus dem Dashboard aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-268">In the [**Azure portal**][azure-portal], select your resource group from the dashboard.</span></span>
1. <span data-ttu-id="d1bf5-269">Wählen Sie Ihren bot-Kanal Registrierungslink aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-269">Select your bot channel registration link.</span></span>
1. <span data-ttu-id="d1bf5-270">Wählen Sie auf der Seite Ressource die Option **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-270">On the resource page, select **Settings**.</span></span>
1. <span data-ttu-id="d1bf5-271">Wählen Sie unter **OAuth-Verbindungseinstellungen** am unteren Rand der Seite die Option **Einstellung hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-271">Under **OAuth Connection Settings** near the bottom of the page, select **Add Setting**.</span></span>
1. <span data-ttu-id="d1bf5-272">Füllen Sie das Formular wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-272">Complete the form as follows:</span></span>

    1. <span data-ttu-id="d1bf5-273">**Name**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-273">**Name**.</span></span> <span data-ttu-id="d1bf5-274">Geben Sie einen Namen für die Verbindung ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-274">Enter a name for the connection.</span></span> <span data-ttu-id="d1bf5-275">Sie verwenden diesen Namen in Ihrem bot in der `appsettings.json` Datei.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-275">You'll use this name in your bot in the `appsettings.json` file.</span></span> <span data-ttu-id="d1bf5-276">Beispiel *BotTeamsAuthADv2*.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-276">For example *BotTeamsAuthADv2*.</span></span>
    1. <span data-ttu-id="d1bf5-277">**Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-277">**Service Provider**.</span></span> <span data-ttu-id="d1bf5-278">Wählen Sie **Azure Active Directory v2** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-278">Select **Azure Active Directory v2**.</span></span> <span data-ttu-id="d1bf5-279">Nachdem Sie diese Option ausgewählt haben, werden die Azure AD spezifischen Felder angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-279">Once you select this, the Azure AD-specific fields will be displayed.</span></span>
    1. <span data-ttu-id="d1bf5-280">**Client-ID**. Geben Sie die Anwendungs-ID (Client) ein, die Sie in den obigen Schritten für Ihre Azure Identity Provider-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-280">**Client id**. Enter the Application (client) ID that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="d1bf5-281">**Geheimer Client Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-281">**Client secret**.</span></span> <span data-ttu-id="d1bf5-282">Geben Sie den geheimen Schlüssel ein, den Sie in den obigen Schritten für Ihre Azure Identity-Anbieter-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-282">Enter the secret that you recorded for your Azure identity provider app in the steps above.</span></span>
    1. <span data-ttu-id="d1bf5-283">**Token Exchange-URL**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-283">**Token Exchange URL**.</span></span> <span data-ttu-id="d1bf5-284">Lassen Sie das Feld leer.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-284">Leave this blank.</span></span>
    1. <span data-ttu-id="d1bf5-285">**Mandanten-ID** : Geben Sie die **Verzeichnis (Mandanten-ID)** ein, die Sie zuvor für Ihre Azure Identity-App aufgezeichnet haben, oder **verbreitet** , je nach dem unterstützten Kontotyp, der beim Erstellen der APP für den Identitätsanbieter ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-285">**Tenant ID** , enter the **Directory (tenant) ID** that you recorded earlier for your Azure identity app or **common** depending on the supported account type selected when you created the identity provider app.</span></span> <span data-ttu-id="d1bf5-286">Um zu entscheiden, welcher Wert zugewiesen werden soll, befolgen Sie die folgenden Kriterien:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-286">To decide which value to assign follow these criteria:</span></span>

        - <span data-ttu-id="d1bf5-287">Wenn Sie entweder *Konten in diesem Organisations Verzeichnis (nur Microsoft – einzelner Mandant)* oder *Konten in einem Organisations Verzeichnis (Microsoft Aad Directory-Multi Mandant)* ausgewählt haben, geben Sie die **Mandanten-ID** ein, die Sie zuvor für die Aad-App aufgezeichnet haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-287">If you selected either *Accounts in this organizational directory only (Microsoft only - Single tenant)* or *Accounts in any organizational directory(Microsoft AAD directory - Multi tenant)* enter the **tenant ID** you recorded earlier for the AAD app.</span></span> <span data-ttu-id="d1bf5-288">Dies ist der Mandant, der den Benutzern zugeordnet ist, die authentifiziert werden können.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-288">This will be the tenant associated with the users who can be authenticated.</span></span>

        - <span data-ttu-id="d1bf5-289">Wenn Sie *Konten in einem beliebigen Organisations Verzeichnis (AAD Directory-Multi Mandanten und persönliche Microsoft-Konten wie Skype, Xbox, Outlook)* ausgewählt haben, geben Sie das Wort " **Common** " anstelle einer Mandanten-ID ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-289">If you selected *Accounts in any organizational directory (Any AAD directory - Multi tenant and personal Microsoft accounts e.g. Skype, Xbox, Outlook)* enter the word **common** instead of a tenant ID.</span></span> <span data-ttu-id="d1bf5-290">Andernfalls wird die Aad-App über den Mandanten überprüfen, dessen ID ausgewählt wurde, und persönliche Microsoft-Konten ausschließen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-290">Otherwise, the AAD app will verify through the tenant whose ID was selected and exclude personal Microsoft accounts.</span></span>

    1. <span data-ttu-id="d1bf5-291">Geben Sie für **Bereiche** eine durch Leerzeichen getrennte Liste von Graph-Berechtigungen ein, die diese Anwendung benötigt, beispielsweise: User. Read User. ReadBasic. all Mail. Read</span><span class="sxs-lookup"><span data-stu-id="d1bf5-291">For **Scopes** , enter a space-delimited list of graph permissions this application requires e.g.: User.Read User.ReadBasic.All Mail.Read</span></span> 

1. <span data-ttu-id="d1bf5-292">Wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-292">Select **Save**.</span></span>

### <a name="test-the-connection"></a><span data-ttu-id="d1bf5-293">Testen der Verbindung</span><span class="sxs-lookup"><span data-stu-id="d1bf5-293">Test the connection</span></span>

1. <span data-ttu-id="d1bf5-294">Wählen Sie den Eintrag Connection aus, um die soeben erstellte Verbindung zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-294">Select the connection entry to open the connection you just created.</span></span>
1. <span data-ttu-id="d1bf5-295">Wählen Sie oben im Bereich **Service Provider Connection Setting** die Option **Test connection** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-295">Select **Test Connection** at the top of the **Service Provider Connection Setting** panel.</span></span>
1. <span data-ttu-id="d1bf5-296">Wenn Sie das erste Mal durchführen, wird ein neues Browserfenster geöffnet, in dem Sie aufgefordert werden, ein Konto auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-296">The first time you do this will open a new browser window asking you to select an account.</span></span> <span data-ttu-id="d1bf5-297">Wählen Sie diejenige aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-297">Select the one you want to use.</span></span>
1. <span data-ttu-id="d1bf5-298">Als nächstes werden Sie aufgefordert, dem Identitätsanbieter die Verwendung Ihrer Daten (Anmeldeinformationen) zu gestatten.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-298">Next, you'll be asked to allow to the identity provider to use your data (credentials).</span></span> <span data-ttu-id="d1bf5-299">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-299">The following image is an example:</span></span>

    ![Teams-bot-auth-Verbindungszeichenfolge ADV1](../../../assets/images/authentication/auth-bot-connection-test-accept.PNG)

1. <span data-ttu-id="d1bf5-301">Wählen Sie **Annehmen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-301">Select **Accept**.</span></span>
1. <span data-ttu-id="d1bf5-302">Anschließend sollten Sie zu einer **Test Verbindung zu einer \<your-connection-name> erfolgreichen** Seite umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-302">This should then redirect you to a **Test Connection to \<your-connection-name> Succeeded** page.</span></span> <span data-ttu-id="d1bf5-303">Aktualisieren Sie die Seite, wenn Sie eine Fehlermeldung erhalten.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-303">Refresh the page if you get an error.</span></span> <span data-ttu-id="d1bf5-304">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-304">The following image is an example:</span></span>

  ![Teams Bots App auth Connection Str ADV1](../../../assets/images/authentication/auth-bot-connection-test-token.PNG)

<span data-ttu-id="d1bf5-306">Der Verbindungsname wird vom bot-Code zum Abrufen von Benutzerauthentifizierungstoken verwendet.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-306">The connection name is used by the bot code to retrieve user authentication tokens.</span></span>

## <a name="prepare-the-bot-sample-code"></a><span data-ttu-id="d1bf5-307">Vorbereiten des bot-Beispielcodes</span><span class="sxs-lookup"><span data-stu-id="d1bf5-307">Prepare the bot sample code</span></span>

<span data-ttu-id="d1bf5-308">Nachdem die vorläufigen Einstellungen vorgenommen wurden, konzentrieren wir uns auf die Erstellung des bot, der in diesem Artikel verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-308">With the preliminary settings done, let's focus on the creation of the bot to use in this article.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d1bf5-309">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d1bf5-309">C#/.NET</span></span>](#tab/dotnet)

1. <span data-ttu-id="d1bf5-310">Klon [CS-auth-Sample][teams-auth-bot-cs].</span><span class="sxs-lookup"><span data-stu-id="d1bf5-310">Clone [cs-auth-sample][teams-auth-bot-cs].</span></span>
1. <span data-ttu-id="d1bf5-311">Starten Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-311">Launch Visual Studio.</span></span>
1. <span data-ttu-id="d1bf5-312">Wählen Sie in der Symbolleiste **Datei-> Open-> Projekt/Lösung** aus, und öffnen Sie das bot-Projekt.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-312">From the toolbar select **File -> Open -> Project/Solution** and open the bot project.</span></span>
1. <span data-ttu-id="d1bf5-313">In C# Update **appsettings.js** wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-313">In C# Update **appsettings.json** as follows:</span></span>

    - <span data-ttu-id="d1bf5-314">Legen `ConnectionName` Sie den Namen der Identitätsanbieter Verbindung fest, die Sie der bot-Kanal Registrierung hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-314">Set `ConnectionName` to the name of the identity provider connection you added to the bot channel registration.</span></span> <span data-ttu-id="d1bf5-315">Der Name, den wir in diesem Beispiel verwendet haben, ist *BotTeamsAuthADv1*.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-315">The name we used in this example is *BotTeamsAuthADv1*.</span></span>
    - <span data-ttu-id="d1bf5-316">Legen `MicrosoftAppId` Sie die **bot-APP-ID** fest, die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-316">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="d1bf5-317">Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-317">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="d1bf5-318">Legen `ConnectionName` Sie den auf den Namen der Identitätsanbieter Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-318">Set the `ConnectionName` to the name of the identity provider connection.</span></span>

    <span data-ttu-id="d1bf5-319">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-319">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="d1bf5-320">Beispielsweise müssen alle kaufmännischen und-Zeichen (&) als codiert werden `&amp;` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-320">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-json[appsettings](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/appsettings.json?range=1-5)]

1. <span data-ttu-id="d1bf5-321">Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner öffnen `manifest.json` und festlegen `id` sowie `botId` zur **bot-APP-ID** , die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-321">In the Solution Explorer, navigate to the `TeamsAppManifest` folder, open `manifest.json` and set `id` and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="javascript"></a>[<span data-ttu-id="d1bf5-322">JavaScript</span><span class="sxs-lookup"><span data-stu-id="d1bf5-322">JavaScript</span></span>](#tab/node-js)

1. <span data-ttu-id="d1bf5-323">Clone [Node-auth-Sample][teams-auth-bot-js].</span><span class="sxs-lookup"><span data-stu-id="d1bf5-323">Clone [node-auth-sample][teams-auth-bot-js].</span></span>
1. <span data-ttu-id="d1bf5-324">Navigieren Sie in einer Konsole zum Projekt:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-324">In a console, navigate to the project:</span></span> </br></br>
`cd samples/javascript_nodejs/46.teams`  
1. <span data-ttu-id="d1bf5-325">Installieren von Modulen</span><span class="sxs-lookup"><span data-stu-id="d1bf5-325">Install modules</span></span></br></br>
`npm install`
1. <span data-ttu-id="d1bf5-326">Aktualisieren Sie die **. env-** Konfiguration wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-326">Update the **.env** configuration as follows:</span></span>

    - <span data-ttu-id="d1bf5-327">Legen `MicrosoftAppId` Sie die **bot-APP-ID** fest, die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-327">Set `MicrosoftAppId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="d1bf5-328">Legen `MicrosoftAppPassword` Sie den **geheimen Kundenschlüssel** fest, den Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-328">Set `MicrosoftAppPassword` to the **customer secret** you saved at the time of the bot channel registration.</span></span>
    - <span data-ttu-id="d1bf5-329">Legen `connectionName` Sie den auf den Namen der Identitätsanbieter Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-329">Set the `connectionName` to the name of the identity provider connection.</span></span>

    <span data-ttu-id="d1bf5-330">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-330">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="d1bf5-331">Beispielsweise müssen alle kaufmännischen und-Zeichen (&) als codiert werden `&amp;` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-331">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

     [!code-javascript[settings](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/.env)]

1. <span data-ttu-id="d1bf5-332">`teamsAppManifest`Öffnen Sie in dem Ordner `manifest.json` `id` Ihre **Microsoft-App-ID** und `botId` die **bot-APP-ID** , die Sie zum Zeitpunkt der bot-Kanal Registrierung gespeichert haben, und legen Sie diese fest.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-332">In the `teamsAppManifest` folder, open `manifest.json` and set `id`  to your **Microsoft App ID** and `botId` to the **bot App ID** you saved at the time of the bot channel registration.</span></span>

# <a name="python"></a>[<span data-ttu-id="d1bf5-333">Python</span><span class="sxs-lookup"><span data-stu-id="d1bf5-333">Python</span></span>](#tab/python)

1. <span data-ttu-id="d1bf5-334">Clone [py-auth-Sample][teams-auth-bot-py] aus dem GitHub-Repository.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-334">Clone [py-auth-sample][teams-auth-bot-py] from the github repository.</span></span>
1. <span data-ttu-id="d1bf5-335">**Config.py** aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-335">Update **config.py** :</span></span>

    - <span data-ttu-id="d1bf5-336">Legen `ConnectionName` Sie den Namen der OAuth-Verbindungseinstellung fest, die Sie Ihrem bot hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-336">Set `ConnectionName` to the name of the OAuth connection setting you added to your bot.</span></span>
    - <span data-ttu-id="d1bf5-337">Legen `MicrosoftAppId` `MicrosoftAppPassword` Sie die APP-ID und den App-Schlüssel Ihres bot fest.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-337">Set `MicrosoftAppId` and `MicrosoftAppPassword` to your bot's app ID and app secret.</span></span>

      <span data-ttu-id="d1bf5-338">Je nach den Zeichen in Ihrem bot-Schlüssel müssen Sie möglicherweise XML-Escapezeichen für das Kennwort eingeben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-338">Depending on the characters in your bot secret, you may need to XML escape the password.</span></span> <span data-ttu-id="d1bf5-339">Beispielsweise müssen alle kaufmännischen und-Zeichen (&) als codiert werden `&amp;` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-339">For example, any ampersands (&) will need to be encoded as `&amp;`.</span></span>

      [!code-python[config](~/../botbuilder-samples/samples/python/46.teams-auth/config.py?range=14-16)]

---

### <a name="deploy-the-bot-to-azure"></a><span data-ttu-id="d1bf5-340">Bereitstellen des bot in Azure</span><span class="sxs-lookup"><span data-stu-id="d1bf5-340">Deploy the bot to Azure</span></span>

<span data-ttu-id="d1bf5-341">Um den bot bereitzustellen, befolgen Sie die Schritte unter How to [deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-341">To deploy the bot, follow the steps in the how to [Deploy your bot to Azure](https://aka.ms/azure-bot-deployment-cli).</span></span>

<span data-ttu-id="d1bf5-342">Alternativ können Sie in Visual Studio die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-342">Alternatively, while in Visual Studio, you can follow these steps:</span></span>

1. <span data-ttu-id="d1bf5-343">Wählen Sie im Visual Studio Projekt *Mappen-Explorer* den Projektnamen aus, und halten Sie ihn (oder klicken Sie mit der rechten Maustaste).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-343">In Visual Studio *Solution Explorer* select and hold (or right-click) the project name.</span></span>
1. <span data-ttu-id="d1bf5-344">Wählen Sie im Dropdownmenü die Option **veröffentlichen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-344">In the drop-down menu, select **Publish**.</span></span>
1. <span data-ttu-id="d1bf5-345">Wählen Sie im angezeigten Fenster den **neuen** Link aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-345">In the displayed window, select the **New** link.</span></span>
1. <span data-ttu-id="d1bf5-346">Wählen Sie im Dialogfeld **App-Dienst** auf der linken Seite aus, und **Erstellen Sie neu** auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-346">In the dialog window, select **App Service** on the left and **Create New** on the right.</span></span>
1. <span data-ttu-id="d1bf5-347">Klicken Sie auf die Schaltfläche **veröffentlichen** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-347">Select the **Publish** button.</span></span>
1. <span data-ttu-id="d1bf5-348">Geben Sie im nächsten Dialogfenster die erforderlichen Informationen ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-348">In the next dialog window, enter the required information.</span></span> <span data-ttu-id="d1bf5-349">Es folgt ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-349">The following is an example:</span></span>

   ![auth-App-Service](../../../assets/images/authentication/auth-bot-app-service.png)

1. <span data-ttu-id="d1bf5-351">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-351">Select **Create**.</span></span>
1. <span data-ttu-id="d1bf5-352">Wenn die Bereitstellung erfolgreich abgeschlossen wurde, sollte Sie in Visual Studio angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-352">If the deployment completes successfully, you should see it reflected in Visual Studio.</span></span> <span data-ttu-id="d1bf5-353">Darüber hinaus wird in Ihrem Standardbrowser eine Seite angezeigt, die besagt, dass *Ihr bot Ready!*.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-353">Moreover, a page is displayed in your default browser saying *Your bot is ready!*.</span></span> <span data-ttu-id="d1bf5-354">Die URL wird wie folgt aussehen: `https://botteamsauth.azurewebsites.net/` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-354">The URL will be similar to this: `https://botteamsauth.azurewebsites.net/`.</span></span> <span data-ttu-id="d1bf5-355">Speichern Sie Sie in einer Datei.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-355">Save it to a file.</span></span>
1. <span data-ttu-id="d1bf5-356">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="d1bf5-356">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="d1bf5-357">Überprüfen Sie Ihre Ressourcengruppe, der bot sollte zusammen mit den anderen Ressourcen aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-357">Check your resource group, the bot should be listed along with the other resources.</span></span> <span data-ttu-id="d1bf5-358">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-358">The following image is an example:</span></span>

    ![Teams-bot-auth-App-Service-Gruppe](../../../assets/images/authentication/auth-bot-app-service-in-group.png)

1. <span data-ttu-id="d1bf5-360">Wählen Sie in der Gruppe Ressourcen den Namen des bot-Kanal Registrierungs namens (Link) aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-360">In the resource group, select the bot channel registration name (link).</span></span>
1. <span data-ttu-id="d1bf5-361">Wählen Sie im linken Bereich **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-361">In the left panel, select **Settings**.</span></span>
1. <span data-ttu-id="d1bf5-362">Geben Sie im Feld **Messaging-Endpunkt** die oben abgerufene URL ein, gefolgt von `api/messages` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-362">In the **Messaging endpoint** box, enter the URL obtained above followed by `api/messages`.</span></span> <span data-ttu-id="d1bf5-363">Dies ist ein Beispiel: `https://botteamsauth.azurewebsites.net/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-363">This is an example: `https://botteamsauth.azurewebsites.net/api/messages`.</span></span>
1. <span data-ttu-id="d1bf5-364">Klicken Sie oben links auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-364">Select the **Save** button in the upper left.</span></span>

## <a name="test-the-bot-using-the-emulator"></a><span data-ttu-id="d1bf5-365">Testen des bot mit dem Emulator</span><span class="sxs-lookup"><span data-stu-id="d1bf5-365">Test the bot using the Emulator</span></span>

<span data-ttu-id="d1bf5-366">Wenn Sie es nicht bereits getan haben, installieren Sie den [Microsoft bot Framework-Emulator](https://aka.ms/bot-framework-emulator-readme).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-366">If you haven't done it already, install the [Microsoft Bot Framework Emulator](https://aka.ms/bot-framework-emulator-readme).</span></span> <span data-ttu-id="d1bf5-367">Siehe auch [Debuggen mit dem Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-367">See also [Debug with the Emulator](https://aka.ms/bot-framework-emulator-debug-with-emulator).</span></span>

<span data-ttu-id="d1bf5-368">Damit die bot-Beispiel Anmeldung funktioniert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-368">In order for the bot sample login to work you must configure the Emulator as shown below.</span></span>

### <a name="configure-the-emulator-for-authentication"></a><span data-ttu-id="d1bf5-369">Konfigurieren des Emulators für die Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="d1bf5-369">Configure the Emulator for authentication</span></span>

<span data-ttu-id="d1bf5-370">Wenn ein bot eine Authentifizierung erfordert, müssen Sie den Emulator wie unten gezeigt konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-370">If a bot requires authentication, you must configure the Emulator as shown below.</span></span>

1. <span data-ttu-id="d1bf5-371">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-371">Start the Emulator.</span></span>
1. <span data-ttu-id="d1bf5-372">Wählen Sie im Emulator das Zahnradsymbol &#9881; unten links oder die Registerkarte **Emulatoreinstellungen** in der oberen rechten Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-372">In the Emulator, select the gear icon &#9881; in the bottom left, or the **Emulator Settings** tab in the upper right.</span></span>
1. <span data-ttu-id="d1bf5-373">Aktivieren Sie das Kontrollkästchen mit der **Version 1,0-Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-373">Check the box by **Use version 1.0 authentication tokens**.</span></span>
1. <span data-ttu-id="d1bf5-374">Geben Sie den lokalen Pfad zum **ngrok** -Tool ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-374">Enter the local path to the **ngrok** tool.</span></span> <span data-ttu-id="d1bf5-375">*Siehe* bot Framework Emulator/ngrok Tunneling Integration [wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-375">*See* the Bot Framework Emulator / ngrok tunneling integration [Wiki](https://github.com/Microsoft/BotFramework-Emulator/wiki/Tunneling-(ngrok)).</span></span> <span data-ttu-id="d1bf5-376">Weitere Informationen zum Tool finden Sie unter [ngrok](https://ngrok.com/).</span><span class="sxs-lookup"><span data-stu-id="d1bf5-376">For more tool information, see [ngrok](https://ngrok.com/).</span></span>
1. <span data-ttu-id="d1bf5-377">Aktivieren Sie das Kontrollkästchen **ngrok ausführen, wenn der Emulator gestartet wird**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-377">Check the box by **Run ngrok when the Emulator starts up**.</span></span>
1. <span data-ttu-id="d1bf5-378">Klicken Sie auf die Schaltfläche **Speichern** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-378">Select the **Save** button.</span></span>

<span data-ttu-id="d1bf5-379">Wenn der bot eine Anmeldekarte anzeigt und der Benutzer die Anmeldeschaltfläche auswählt, öffnet der Emulator eine Seite, die der Benutzer zum Anmelden mit dem Authentifizierungsanbieter verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-379">When the bot displays a sign-in card and the user selects the sign-in button, the Emulator opens a page that the user can use to sign in with the authentication provider.</span></span>
<span data-ttu-id="d1bf5-380">Sobald der Benutzer dies tut, generiert der Anbieter ein Benutzertoken und sendet es an den bot.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-380">Once the user does so, the provider generates a user token and sends it to the bot.</span></span> <span data-ttu-id="d1bf5-381">Danach kann der bot im Namen des Benutzers handeln.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-381">After that, the bot can act on behalf of the user.</span></span>

### <a name="test-the-bot-locally"></a><span data-ttu-id="d1bf5-382">Testen des bot lokal</span><span class="sxs-lookup"><span data-stu-id="d1bf5-382">Test the bot locally</span></span>

<span data-ttu-id="d1bf5-383">Nachdem Sie den Authentifizierungsmechanismus konfiguriert haben, können Sie die eigentlichen bot-Tests durchführen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-383">After you have configured the authentication mechanism, you can perform the actual bot testing.</span></span>  

1. <span data-ttu-id="d1bf5-384">Führen Sie das bot-Beispiel lokal auf Ihrem Computer aus, beispielsweise über Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-384">Run the bot sample locally on your machine, via Visual Studio for example.</span></span>
1. <span data-ttu-id="d1bf5-385">Starten Sie den Emulator.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-385">Start the Emulator.</span></span>
1. <span data-ttu-id="d1bf5-386">Klicken Sie auf die Schaltfläche **bot öffnen** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-386">Select the **Open bot** button.</span></span>
1. <span data-ttu-id="d1bf5-387">Geben Sie in der **bot-URL** die lokale URL des bot ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-387">In the **Bot URL** , enter the bot's local URL.</span></span> <span data-ttu-id="d1bf5-388">Normalerweise `http://localhost:3978/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-388">Usually, `http://localhost:3978/api/messages`.</span></span>
1. <span data-ttu-id="d1bf5-389">Geben Sie in der **Microsoft App-ID** die APP-ID des bot von ein `appsettings.json` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-389">In the **Microsoft App ID** enter the bot's app ID from `appsettings.json`.</span></span>
1. <span data-ttu-id="d1bf5-390">Geben Sie im **Microsoft App-Kennwort** das App-Kennwort des bot aus dem ein `appsettings.json` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-390">In the **Microsoft App password** enter the bot's app password from the `appsettings.json`.</span></span>
1. <span data-ttu-id="d1bf5-391">Wählen Sie **verbinden** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-391">Select **Connect**.</span></span>
1. <span data-ttu-id="d1bf5-392">Geben Sie nach dem Starten des bot einen beliebigen Text ein, um die Anmeldekarte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-392">After the bot is up and running, enter any text to display the sign-in card.</span></span>
1. <span data-ttu-id="d1bf5-393">Wählen Sie die Schaltfläche **Anmelden** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-393">Select the **Sign in** button.</span></span>
1. <span data-ttu-id="d1bf5-394">Ein Popupdialogfeld wird angezeigt, um die **geöffnete URL zu bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-394">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="d1bf5-395">Dadurch kann der Benutzer des bot (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-395">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="d1bf5-396">Wählen Sie **Bestätigen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-396">Select **Confirm**.</span></span>
1. <span data-ttu-id="d1bf5-397">Wenn Sie dazu aufgefordert werden, wählen Sie das entsprechende Benutzerkonto aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-397">If asked, select the applicable user's account.</span></span>
1. <span data-ttu-id="d1bf5-398">Je nachdem, welche Konfiguration Sie für den Emulator verwendet haben, erhalten Sie eine der folgenden Optionen:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-398">Depending which configuration you used for the Emulator, you get one of the following:</span></span>
    1. <span data-ttu-id="d1bf5-399">**Verwenden des Anmelde Bestätigungscodes**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-399">**Using sign-in verification code**</span></span>  
      <span data-ttu-id="d1bf5-400">&#x2713; ein Fenster wird geöffnet, in dem der Validierungscode angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-400">&#x2713; A window is opened displaying the validation code.</span></span>  
      <span data-ttu-id="d1bf5-401">&#x2713; kopieren Sie den Validierungscode, und geben Sie ihn in das Feld Chat ein, um die Anmeldung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-401">&#x2713; Copy and enter the validation code into the chat box to complete the sign-in.</span></span>
    1. <span data-ttu-id="d1bf5-402">**Verwenden von Authentifizierungstoken**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-402">**Using authentication tokens**.</span></span>  
      <span data-ttu-id="d1bf5-403">&#x2713; Sie auf der Grundlage ihrer Anmeldeinformationen angemeldet sind.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-403">&#x2713; You're logged in based on your credentials.</span></span>

    <span data-ttu-id="d1bf5-404">Die folgende Abbildung ist ein Beispiel für die bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-404">The following image is an example of the bot UI after you've logged in:</span></span>

    ![Authentifizierungs-bot-Anmelde Emulator](../../../assets/images/authentication/auth-bot-login-emulator.PNG)

1. <span data-ttu-id="d1bf5-406">Wenn Sie " **Ja** " auswählen, wenn der bot *möchte, dass Ihr Token angezeigt* wird, erhalten Sie eine ähnliche Antwort wie die folgende:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-406">If you select **Yes** when the bot asks *Would you like to view your token?* , you'll get a response similar to the following:</span></span>

    ![Authentifizierungs-bot-Anmelde Emulator-Token](../../../assets/images/authentication/auth-bot-login-emulator-token.png)

1. <span data-ttu-id="d1bf5-408">Geben Sie **Logout** in das Feld Eingabe Chat ein, um sich abzumelden. Dadurch wird das Benutzertoken freigegeben, und der Bot kann nicht in Ihrem Namen handeln, bis Sie sich erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-408">Enter **logout** in the input chat box to sign out. This releases the user token, and the bot won't be able to act on your behalf until you sign in again.</span></span>

> [!NOTE]
> <span data-ttu-id="d1bf5-409">Für die bot-Authentifizierung ist die Verwendung des **bot Connector-Diensts** erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-409">Bot authentication requires use of the **Bot Connector Service**.</span></span> <span data-ttu-id="d1bf5-410">Der Dienst greift auf die Registrierungsinformationen für bot-Kanäle für Ihren bot zu.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-410">The service accesses the bot channels registration information for your bot.</span></span>

## <a name="test-the-deployed-bot"></a><span data-ttu-id="d1bf5-411">Testen des bereitgestellten bot</span><span class="sxs-lookup"><span data-stu-id="d1bf5-411">Test the deployed bot</span></span>

<!--There are several testing scenarios here. Ideally, we'd have a separate article on the what, why, 
and when for these, and just reference that from here, along with the set of steps that exercises the bot code.-->

1. <span data-ttu-id="d1bf5-412">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="d1bf5-412">In your browser, navigate to the [**Azure portal**][azure-portal].</span></span>
1. <span data-ttu-id="d1bf5-413">Suchen Sie Ihre Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-413">Find your resource group.</span></span>
1. <span data-ttu-id="d1bf5-414">Wählen Sie den Link Ressource aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-414">Select the resource link.</span></span> <span data-ttu-id="d1bf5-415">Die Seite Ressource wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-415">The resource page is displayed.</span></span>
1. <span data-ttu-id="d1bf5-416">Wählen Sie auf der Seite Ressource die Option **Test im Webchat** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-416">In the resource page, select **Test in Web Chat**.</span></span> <span data-ttu-id="d1bf5-417">Der bot startet und zeigt die vordefinierten Begrüßungen an.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-417">The bot starts and displays the predefined greetings.</span></span>
1. <span data-ttu-id="d1bf5-418">Geben Sie im Feld Chat eine beliebige Eingabe ein.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-418">Type anything in the chat box.</span></span>
1. <span data-ttu-id="d1bf5-419">Aktivieren Sie das Kontrollkästchen **Anmelden** .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-419">Select the **Sign in** box.</span></span>
1. <span data-ttu-id="d1bf5-420">Ein Popupdialogfeld wird angezeigt, um die **geöffnete URL zu bestätigen**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-420">A pop-up dialog is displayed to **Confirm Open URL**.</span></span> <span data-ttu-id="d1bf5-421">Dadurch kann der Benutzer des bot (Sie) authentifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-421">This is to allow the bot's user (you) to be authenticated.</span></span>  
1. <span data-ttu-id="d1bf5-422">Wählen Sie **Bestätigen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-422">Select **Confirm**.</span></span>
1. <span data-ttu-id="d1bf5-423">Wenn Sie dazu aufgefordert werden, wählen Sie das entsprechende Benutzerkonto aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-423">If asked, select the applicable user's account.</span></span>
    <span data-ttu-id="d1bf5-424">Die folgende Abbildung ist ein Beispiel für die bot-Benutzeroberfläche, nachdem Sie sich angemeldet haben:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-424">The following image is an example of the bot UI after you have logged in:</span></span>

    ![bereitgestellte Authentifizierungs-bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed.PNG)<span data-ttu-id="d1bf5-426">.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-426">.</span></span>

1. <span data-ttu-id="d1bf5-427">Wählen Sie die Schaltfläche **Ja** aus, um das Authentifizierungstoken anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-427">Select the **Yes** button to display your authentication token.</span></span> <span data-ttu-id="d1bf5-428">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-428">The following image is an example:</span></span>

    ![bereitgestelltes Token für auth-bot-Anmeldung](../../../assets/images/authentication/auth-bot-login-deployed-token.PNG)<span data-ttu-id="d1bf5-430">.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-430">.</span></span>

1. <span data-ttu-id="d1bf5-431">Geben Sie Logout ein, um sich abzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-431">Enter logout to sign out.</span></span>

    ![Authentifizierungs-bot bereitgestellt Logout](../../../assets/images/authentication/auth-bot-deployed-logout.PNG)

> [!NOTE]
> <span data-ttu-id="d1bf5-433">Wenn Sie bei der Anmeldung Probleme haben, versuchen Sie, die Verbindung erneut zu testen, wie in den vorherigen Schritten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-433">If you're having problems signing in, try to test the connection again as described in the previous steps.</span></span> <span data-ttu-id="d1bf5-434">Dadurch könnte das Authentifizierungstoken neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-434">This could recreate the authentication token.</span></span>
> <span data-ttu-id="d1bf5-435">Mit dem bot-Framework-Webchat Client in Azure müssen Sie sich möglicherweise mehrere Male anmelden, bevor die Authentifizierung ordnungsgemäß eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-435">With the Bot Framework Web Chat client in Azure, you may need to sign in several times before the authentication is established correctly.</span></span>

## <a name="install-and-test-the-bot-in-teams"></a><span data-ttu-id="d1bf5-436">Installieren und Testen des bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d1bf5-436">Install and test the bot in Teams</span></span>

1. <span data-ttu-id="d1bf5-437">Stellen Sie in Ihrem bot-Projekt sicher, dass der `TeamsAppManifest` Ordner den `manifest.json` zusammen mit einem `outline.png` und `color.png` Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-437">In your bot project, ensure that the `TeamsAppManifest` folder contains the `manifest.json` along with an `outline.png` and `color.png` files.</span></span>
1. <span data-ttu-id="d1bf5-438">Navigieren Sie im Projektmappen-Explorer zum `TeamsAppManifest` Ordner.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-438">In Solution Explorer, navigate to the `TeamsAppManifest` folder.</span></span> <span data-ttu-id="d1bf5-439">Bearbeiten `manifest.json` , indem Sie die folgenden Werte zuweisen:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-439">Edit `manifest.json` by assigning the following values:</span></span>
    1. <span data-ttu-id="d1bf5-440">Stellen Sie sicher, dass die **bot-APP-ID** , die Sie zum Zeitpunkt der bot-Kanal Registrierung erhalten haben, und zugewiesen ist `id` `botId` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-440">Ensure that the **bot App ID** you received at the time of the bot channel registration is assigned to `id` and `botId`.</span></span>
    1. <span data-ttu-id="d1bf5-441">Weisen Sie diesen Wert zu: `validDomains: [ "token.botframework.com" ]` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-441">Assign this value: `validDomains: [ "token.botframework.com" ]`.</span></span>
1. <span data-ttu-id="d1bf5-442">Wählen Sie die Dateien aus, und **zippen** Sie Sie `manifest.json` `outline.png` `color.png` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-442">Select and **zip** the `manifest.json`, `outline.png`, and `color.png` files.</span></span>
1. <span data-ttu-id="d1bf5-443">Öffnen Sie **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-443">Open **Microsoft Teams**.</span></span>
1. <span data-ttu-id="d1bf5-444">Wählen Sie im linken Bereich unten das **Symbol apps** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-444">In the left panel, at the bottom, select the **Apps icon**.</span></span>
1. <span data-ttu-id="d1bf5-445">Wählen Sie im rechten Bereich unten die Option **benutzerdefinierte App hochladen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-445">In the right panel, at the bottom, select **Upload a custom app**.</span></span>
1. <span data-ttu-id="d1bf5-446">Navigieren Sie zum `TeamsAppManifest` Ordner, und laden Sie das gezippte Manifest hoch.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-446">Navigate to the `TeamsAppManifest` folder and upload the zipped manifest.</span></span>
<span data-ttu-id="d1bf5-447">Der folgende Assistent wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-447">The following wizard is displayed:</span></span>

    ![Upload von auth-bot-Teams](../../../assets/images/authentication/auth-bot-teams-upload.png)

1. <span data-ttu-id="d1bf5-449">Klicken Sie auf die Schaltfläche **Zum Team hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-449">Select the **Add to a team** button.</span></span>
1. <span data-ttu-id="d1bf5-450">Wählen Sie im nächsten Fenster das Team aus, in dem Sie den bot verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-450">In the next window, select the team where you want to use the bot.</span></span>
1. <span data-ttu-id="d1bf5-451">Wählen Sie die Schaltfläche **Einrichten eines bot** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-451">Select the **Set up a bot** button.</span></span>
1. <span data-ttu-id="d1bf5-452">Wählen Sie im linken Bereich die drei Punkte (&#x25cf;&#x25cf;&#x25cf;) aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-452">Select the three dots (&#x25cf;&#x25cf;&#x25cf;) in the left panel.</span></span> <span data-ttu-id="d1bf5-453">Wählen Sie dann das **App Studio** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-453">Then select the **App Studio** icon.</span></span>
1. <span data-ttu-id="d1bf5-454">Wählen Sie die Registerkarte **Manifest-Editor** aus. Das Symbol für den von Ihnen hochgeladenen bot sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-454">Select the **Manifest editor** tab. You should see the icon for the bot you uploaded.</span></span>
1. <span data-ttu-id="d1bf5-455">Außerdem sollten Sie in der Lage sein, den bot als Kontakt in der Chat Liste zu sehen, den Sie zum Austauschen von Nachrichten mit dem bot verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-455">Also, you should be able to see the bot listed as a contact in the chat list that you can use to exchange messages with the bot.</span></span>

### <a name="testing-the-bot-locally-in-teams"></a><span data-ttu-id="d1bf5-456">Testen des bot lokal in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d1bf5-456">Testing the bot locally in Teams</span></span>

<span data-ttu-id="d1bf5-457">Microsoft Teams ist ein vollständig Cloud-basiertes Produkt, für das alle Dienste, auf die es zugreift, über die Cloud über HTTPS-Endpunkte verfügbar sein müssen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-457">Microsoft Teams is an entirely cloud-based product, it requires all services it accesses to be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="d1bf5-458">Um den bot (unser Beispiel) für die Arbeit in Microsoft Teams zu aktivieren, müssen Sie daher entweder den Code in der Cloud Ihrer Wahl veröffentlichen oder eine lokal ausgeführten Instanz über ein **Tunneling** -Tool Extern zugänglich machen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-458">Therefore, to enable the bot (our sample) to work in Teams, you need to either publish the code to the cloud of your choice, or make a locally running instance externally accessible via a **tunneling** tool.</span></span> <span data-ttu-id="d1bf5-459">Wir empfehlen  [ngrok](https://ngrok.com/download), mit dem eine extern adressierbare URL für einen Port erstellt wird, den Sie lokal auf Ihrem Computer öffnen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-459">We recommend  [ngrok](https://ngrok.com/download), which creates an externally addressable URL for a port you open locally on your machine.</span></span>
<span data-ttu-id="d1bf5-460">Führen Sie die folgenden Schritte aus, um ngrok als Vorbereitung für die lokale Ausführung Ihrer Microsoft Teams-App einzurichten:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-460">To set up ngrok in preparation for running your Microsoft Teams app locally, follow these steps:</span></span>

1. <span data-ttu-id="d1bf5-461">Wechseln Sie in einem Terminalfenster zu dem Verzeichnis, in dem Sie `ngrok.exe` installiert haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-461">In a terminal window, go the directory where you have `ngrok.exe` installed.</span></span> <span data-ttu-id="d1bf5-462">Es wird empfohlen, den Pfad der *Umgebungsvariable* so festzulegen, dass darauf verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-462">We suggest setting the *environment variable* path to point to it.</span></span>
1. <span data-ttu-id="d1bf5-463">Ausführen, beispielsweise `ngrok http 3978 --host-header=localhost:3978` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-463">Run, for example, `ngrok http 3978 --host-header=localhost:3978`.</span></span> <span data-ttu-id="d1bf5-464">Ersetzen Sie die Portnummer bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-464">Replace the port number as needed.</span></span>
<span data-ttu-id="d1bf5-465">Dadurch wird ngrok gestartet, um den angegebenen Port abzuhören.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-465">This launches ngrok to listen on the port you specify.</span></span> <span data-ttu-id="d1bf5-466">Im Gegenzug erhalten Sie eine extern adressierbare URL, die gültig ist, solange ngrok ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-466">In return, it gives you an externally addressable URL, valid for as long as ngrok is running.</span></span> <span data-ttu-id="d1bf5-467">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-467">The following image is an example:</span></span>

    ![Teams-bot-App-Authentifizierungs-Verbindungszeichenfolge ADV1](../../../assets/images/authentication/auth-bot-ngrok-start.PNG)<span data-ttu-id="d1bf5-469">.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-469">.</span></span>

1. <span data-ttu-id="d1bf5-470">Kopieren Sie die Weiterleitungs-HTTPS-Adresse.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-470">Copy the forwarding HTTPS address.</span></span> <span data-ttu-id="d1bf5-471">Es sollte wie folgt aussehen: `https://dea822bf.ngrok.io/` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-471">It should be similar to the following: `https://dea822bf.ngrok.io/`.</span></span>
1. <span data-ttu-id="d1bf5-472">Append `/api/messages` zu erhalten `https://dea822bf.ngrok.io/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-472">Append `/api/messages` to obtain `https://dea822bf.ngrok.io/api/messages`.</span></span> <span data-ttu-id="d1bf5-473">Dies ist der **Nachrichten Endpunkt** für den bot, der lokal auf Ihrem Computer läuft und über das Internet in einem Chat in Microsoft Teams erreichbar ist.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-473">This is the **messages endpoint** for the bot running locally on your machine and reachable over the web in a chat in Microsoft Teams.</span></span>
1. <span data-ttu-id="d1bf5-474">Ein letzter Schritt besteht darin, den Nachrichten Endpunkt des bereitgestellten bot zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-474">One final step to perform is to update the messages endpoint of the deployed bot.</span></span> <span data-ttu-id="d1bf5-475">In dem Beispiel haben wir den bot in Azure bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-475">In the example, we deployed the bot in Azure.</span></span> <span data-ttu-id="d1bf5-476">So \* \* lassen Sie uns diese Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-476">So \*\*let's perform these steps:</span></span>
    1. <span data-ttu-id="d1bf5-477">Navigieren Sie in Ihrem Browser zum [**Azure-Portal**][azure-portal].</span><span class="sxs-lookup"><span data-stu-id="d1bf5-477">In your browser navigate to the [**Azure portal**][azure-portal].</span></span>
    1. <span data-ttu-id="d1bf5-478">Wählen Sie Ihre **bot-Kanal Registrierung** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-478">Select your **Bot Channel Registration**.</span></span>
    1. <span data-ttu-id="d1bf5-479">Wählen Sie im linken Bereich **Einstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-479">In the left panel, select **Settings**.</span></span>
    1. <span data-ttu-id="d1bf5-480">Geben Sie im rechten Bereich im Feld **Messaging-Endpunkt** die ngrok-URL in unserem Beispiel ein `https://dea822bf.ngrok.io/api/messages` .</span><span class="sxs-lookup"><span data-stu-id="d1bf5-480">In the right panel, in the **Messaging endpoint** box, enter the ngrok URL, in our example, `https://dea822bf.ngrok.io/api/messages`.</span></span>
1. <span data-ttu-id="d1bf5-481">Starten Sie Ihren bot lokal, beispielsweise in Visual Studio Debugmodus.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-481">Start your bot locally, for example in Visual Studio debug mode.</span></span>
1. <span data-ttu-id="d1bf5-482">Testen Sie den bot, während er lokal mit dem **Test-Webchat** des bot-Framework-Portals läuft.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-482">Test the bot while running locally using the Bot Framework portal's **Test Web chat**.</span></span> <span data-ttu-id="d1bf5-483">Wie der Emulator erlaubt Ihnen dieser Test nicht den Zugriff auf Teams-spezifische Funktionen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-483">Like the Emulator, this test doesn't allow you to access Teams-specific functionality.</span></span>
1. <span data-ttu-id="d1bf5-484">Im Terminal-Fenster, in dem `ngrok` Sie sich befinden, können Sie den HTTP-Datenverkehr zwischen dem bot und dem Chat Client sehen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-484">In the terminal window where `ngrok` is running you can see HTTP traffic between the bot and the web chat client.</span></span> <span data-ttu-id="d1bf5-485">Wenn Sie eine detailliertere Ansicht wünschen, geben Sie in einem Browserfenster die Daten ein, `http://127.0.0.1:4040` die Sie aus dem vorherigen Terminalfenster erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-485">If you want a more detailed view, in a browser window enter `http://127.0.0.1:4040` you obtained from the previous terminal window.</span></span> <span data-ttu-id="d1bf5-486">Die folgende Abbildung ist ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-486">The following image is an example:</span></span>

    ![Authentifizierungs-bot-Teams ngrok Tests](../../../assets/images/authentication/auth-bot-teams-ngrok-testing.png)<span data-ttu-id="d1bf5-488">.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-488">.</span></span>

> [!NOTE]
> <span data-ttu-id="d1bf5-489">Wenn Sie ngrok beenden und neu starten, ändert sich die URL.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-489">If you stop and restart ngrok, the URL changes.</span></span> <span data-ttu-id="d1bf5-490">Um ngrok in Ihrem Projekt zu verwenden, müssen Sie in Abhängigkeit von den von Ihnen verwendeten Funktionen alle URL-Verweise aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-490">To use ngrok in your project, and depending on the capabilities you're using, you must update all URL references.</span></span>
 

## <a name="additional-information"></a><span data-ttu-id="d1bf5-491">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d1bf5-491">Additional information</span></span>

### <a name="teamsappmanifestmanifestjson"></a><span data-ttu-id="d1bf5-492">TeamsAppManifest/manifest.jsein</span><span class="sxs-lookup"><span data-stu-id="d1bf5-492">TeamsAppManifest/manifest.json</span></span>

<span data-ttu-id="d1bf5-493">Dieses Manifest enthält Informationen, die Microsoft Teams benötigt, um eine Verbindung mit dem bot herzustellen.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-493">This manifest contains information needed by Microsoft Teams to connect with the bot.</span></span>  

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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

<span data-ttu-id="d1bf5-494">Bei der Authentifizierung verhält sich Microsoft Teams geringfügig anders als andere Kanäle, wie unten erläutert.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-494">With authentication, Teams behaves slightly differently than other channels, as explained below.</span></span>

### <a name="handling-invoke-activity"></a><span data-ttu-id="d1bf5-495">Behandeln von Invoke-Aktivität</span><span class="sxs-lookup"><span data-stu-id="d1bf5-495">Handling Invoke Activity</span></span>

<span data-ttu-id="d1bf5-496">Eine **Invoke-Aktivität** wird an den bot statt an die Ereignisaktivität gesendet, die von anderen Kanälen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-496">An **Invoke Activity** is sent to the bot rather than the Event Activity used by other channels.</span></span>
<span data-ttu-id="d1bf5-497">Dies wird durch Unterklassen für das **ActivityHandler** getan.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-497">This is done by sub-classing the **ActivityHandler**.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="d1bf5-498">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="d1bf5-498">C#/.NET</span></span>](#tab/dotnet-sample)

<span data-ttu-id="d1bf5-499">**Bots/DialogBot. cs**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-499">**Bots/DialogBot.cs**</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/DialogBot.cs?range=19-51)]

<span data-ttu-id="d1bf5-500">**Bots/TeamsBot. cs**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-500">**Bots/TeamsBot.cs**</span></span>

<span data-ttu-id="d1bf5-501">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-501">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-csharp[ActivityHandler](~/../botbuilder-samples/samples/csharp_dotnetcore/46.teams-auth/Bots/TeamsBot.cs?range=34-42)]

#### <a name="teamsactivityhandlercs"></a><span data-ttu-id="d1bf5-502">TeamsActivityHandler.cs</span><span class="sxs-lookup"><span data-stu-id="d1bf5-502">TeamsActivityHandler.cs</span></span>

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

# <a name="javascript"></a>[<span data-ttu-id="d1bf5-503">JavaScript</span><span class="sxs-lookup"><span data-stu-id="d1bf5-503">JavaScript</span></span>](#tab/node-js-dialog-sample)

<span data-ttu-id="d1bf5-504">**Bots/dialogBot.js**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-504">**bots/dialogBot.js**</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/dialogBot.js?range=4-46)]

<span data-ttu-id="d1bf5-505">**Bots/teamsBot.js**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-505">**bots/teamsBot.js**</span></span>

<span data-ttu-id="d1bf5-506">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-506">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-javascript[ActivityHandler](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/bots/teamsBot.js?range=4-33)]

<span data-ttu-id="d1bf5-507">**Dialogfelder/mainDialog.js**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-507">**dialogs/mainDialog.js**</span></span>

<span data-ttu-id="d1bf5-508">Verwenden Sie in einem Dialogschritt `beginDialog` zum Starten der OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-508">Within a dialog step, use `beginDialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="d1bf5-509">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Token-Antwortereignis, ohne dass der Benutzer aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-509">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="d1bf5-510">Andernfalls wird der Benutzer aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-510">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="d1bf5-511">Der Azure bot-Dienst sendet das Token-Antwortereignis, nachdem der Benutzer versucht, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-511">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-52)]

<span data-ttu-id="d1bf5-512">Überprüfen Sie im folgenden Dialogschritt auf das vorhanden sein eines Tokens im Ergebnis des vorherigen Schritts.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-512">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="d1bf5-513">Wenn es sich nicht um NULL handelt, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-513">If it is not null, the user successfully signed in.</span></span>

[!code-javascript[AddOAuthPrompt](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/mainDialog.js?range=50-64)]

<span data-ttu-id="d1bf5-514">**Bots/logoutDialog.js**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-514">**bots/logoutDialog.js**</span></span>

[!code-javascript[allow-logout](~/../botbuilder-samples/samples/javascript_nodejs/46.teams-auth/dialogs/logoutDialog.js?range=31-42&highlight=7)]

# <a name="python"></a>[<span data-ttu-id="d1bf5-515">Python</span><span class="sxs-lookup"><span data-stu-id="d1bf5-515">Python</span></span>](#tab/python-sample)

<span data-ttu-id="d1bf5-516">**Bots/dialog_bot. py**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-516">**bots/dialog_bot.py**</span></span>

[!code-python[ActivityHandler](~/../botbuilder-samples/samples/python/46.teams-auth/bots/dialog_bot.py?range=10-42)]

<span data-ttu-id="d1bf5-517">**Bots/teams_bot. py**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-517">**bots/teams_bot.py**</span></span>

<span data-ttu-id="d1bf5-518">Die *Invoke-Aktivität* muss an das Dialogfeld weitergeleitet werden, wenn die **OAuthPrompt** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-518">The *Invoke Activity* must be forwarded to the dialog if the **OAuthPrompt** is used.</span></span>

[!code-python[on_token_response_event](~/../botbuilder-samples/samples/python/46.teams-auth/bots/teams_bot.py?range=38-45)]

<span data-ttu-id="d1bf5-519">**Dialoge/main_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-519">**dialogs/main_dialog.py**</span></span>

<span data-ttu-id="d1bf5-520">Verwenden Sie in einem Dialogschritt `begin_dialog` zum Starten der OAuth-Eingabeaufforderung, in der der Benutzer aufgefordert wird, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-520">Within a dialog step, use `begin_dialog` to start the OAuth prompt, which asks the user to sign in.</span></span>

- <span data-ttu-id="d1bf5-521">Wenn der Benutzer bereits angemeldet ist, generiert dies ein Token-Antwortereignis, ohne dass der Benutzer aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-521">If the user is already signed in, this will generate a token response event, without prompting the user.</span></span>
- <span data-ttu-id="d1bf5-522">Andernfalls wird der Benutzer aufgefordert, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-522">Otherwise, this will prompt the user to sign in.</span></span> <span data-ttu-id="d1bf5-523">Der Azure bot-Dienst sendet das Token-Antwortereignis, nachdem der Benutzer versucht, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-523">The Azure Bot Service sends the token response event after the user attempts to sign in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=48-49)]

<span data-ttu-id="d1bf5-524">Überprüfen Sie im folgenden Dialogschritt auf das vorhanden sein eines Tokens im Ergebnis des vorherigen Schritts.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-524">Within the following dialog step, check for the presence of a token in the result from the previous step.</span></span> <span data-ttu-id="d1bf5-525">Wenn es sich nicht um NULL handelt, hat sich der Benutzer erfolgreich angemeldet.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-525">If it is not null, the user successfully signed in.</span></span>

[!code-python[Add OAuthPrompt](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/main_dialog.py?range=51-61)]

<span data-ttu-id="d1bf5-526">**Dialoge/logout_dialog. py**</span><span class="sxs-lookup"><span data-stu-id="d1bf5-526">**dialogs/logout_dialog.py**</span></span>

[!code-python[allow logout](~/../botbuilder-samples/samples/python/46.teams-auth/dialogs/logout_dialog.py?range=29-36&highlight=6)]

---

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1bf5-527">Informationen zum Hinzufügen von Authentifizierung über Azure bot-Dienst</span><span class="sxs-lookup"><span data-stu-id="d1bf5-527">Learn about adding authentication via Azure Bot Service</span></span>](https://aka.ms/azure-bot-add-authentication)

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
