---
title: Power Virtual Agents Chatbot zu Teams hinzufügen
author: laujan
description: Integration eines Power Virtual Agents Chatbots in die Teams Plattform
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 2a8f9c23eaa1acf2555b91cc4caf8d0f3298c114
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566117"
---
# <a name="add-power-virtual-agents-chatbot"></a><span data-ttu-id="ca6e8-103">Hinzufügen eines Power Virtual Agent-Chatbots</span><span class="sxs-lookup"><span data-stu-id="ca6e8-103">Add Power Virtual Agents chatbot</span></span> 

<span data-ttu-id="ca6e8-104">Power Virtual Agents ist eine codefreie, geführte grafische Benutzeroberfläche, die es jedem Mitglied Ihres Teams ermöglicht, umfangreiche, konversationsfähige Chatbots zu erstellen, die sich problemlos in die Teams-Plattform integrieren lassen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-104">Power Virtual Agents is a no-code, guided graphical interface solution that empowers every member of your team to create rich, conversational chatbots that easily integrate with the Teams platform.</span></span> <span data-ttu-id="ca6e8-105">Alle inhalte, die in Power Virtual Agents erstellt werden, werden auf natürliche Weise in Teams gerendert.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-105">All content authored in Power Virtual Agents renders naturally in Teams.</span></span> <span data-ttu-id="ca6e8-106">Power Virtual Agents Bots interagieren mit Benutzern in der Teams nativen Chat-Canvas.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-106">Power Virtual Agents bots engage with users in the Teams native chat canvas.</span></span> <span data-ttu-id="ca6e8-107">IT-Administratoren, Business Analysten, Domänenspezialisten und erfahrene App-Entwickler können intelligente virtuelle Agenten für Teams entwerfen, entwickeln und veröffentlichen, ohne eine Entwicklungsumgebung einrichten zu müssen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-107">The IT administrators, business analysts, domain specialists, and skilled app developers can design, develop, and publish intelligent virtual agents for Teams without having to setup a development environment.</span></span> <span data-ttu-id="ca6e8-108">Sie können einen Webdienst erstellen oder sich direkt beim Bot Framework registrieren.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-108">They can create a web service, or directly register with the Bot Framework.</span></span> 

<span data-ttu-id="ca6e8-109">Dieses Dokument führt Sie darüber, wie Sie Ihren Chatbot in Teams über das Power Virtual Agents-Portal verfügbar machen und Ihren Bot mit App Studio zu Teams hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-109">This document guides you on how to make your chatbot available in Teams through the Power Virtual Agents portal, and add your bot to Teams using App Studio.</span></span> 

<span data-ttu-id="ca6e8-110">mit Power Virtual Agents können Sie leistungsstarke Chatbots erstellen, die Fragen beantworten können, die von Ihren Kunden, anderen Mitarbeitern oder Besuchern Ihrer Website oder Ihres Dienstes gestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-110">Power Virtual Agents lets you create powerful chatbots that can answer questions posed by your customers, other employees, or visitors to your website or service.</span></span>

<span data-ttu-id="ca6e8-111">Diese Bots können leicht erstellt werden, ohne dass Datenwissenschaftler oder Entwickler benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-111">These bots can be created easily without the need for data scientists or developers.</span></span>

> [!NOTE]
> <span data-ttu-id="ca6e8-112">Durch das Hinzufügen Ihres Chatbots zu Microsoft Teams werden einige der Daten, wie Bot-Inhalte und Benutzer-Chat-Inhalte, mit Microsoft Teams geteilt.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-112">By adding your chatbot to Microsoft Teams, some of the data, such as bot content and user chat content, is shared with Microsoft Teams.</span></span> <span data-ttu-id="ca6e8-113">Das bedeutet, dass Ihre Daten außerhalb der [Compliance- und geografischen oder regionalen Grenzen](/power-virtual-agents/data-location)Ihrer Organisation fließen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-113">It means that your data flows outside of your [organization’s compliance and geographic or regional boundaries](/power-virtual-agents/data-location).</span></span> <br/>

## <a name="make-your-chatbot-available-in-teams-through-the-power-virtual-agents-portal"></a><span data-ttu-id="ca6e8-114">Stellen Sie Ihren Chatbot in Teams über das Power Virtual Agents-Portal zur Verfügung</span><span class="sxs-lookup"><span data-stu-id="ca6e8-114">Make your chatbot available in Teams through the Power Virtual Agents portal</span></span>

<span data-ttu-id="ca6e8-115">Um Ihren Chatbot in Teams über das Power Virtual Agents-Portal verfügbar zu machen, müssen Sie die folgenden Prozessschritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="ca6e8-115">To make your chatbot available in Teams through the Power Virtual Agents portal, you must perform the following process steps:</span></span>

<span data-ttu-id="ca6e8-116">**So stellen Sie den Chatbot in Teams**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-116">**To make the chatbot available in Teams**</span></span>

1. <span data-ttu-id="ca6e8-117">**Veröffentlichen der neuesten Bot-Inhalte**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-117">**Publish the latest bot content**</span></span>  
<span data-ttu-id="ca6e8-118">Nachdem Sie einen Chatbot im Power Virtual Agents Portal erstellt haben, müssen Sie Ihren Bot veröffentlichen, bevor Teams Benutzer mit ihm interagieren können.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-118">After creating a chatbot in the Power Virtual Agents portal, you must publish your bot before Teams users can interact with it.</span></span> <span data-ttu-id="ca6e8-119">Weitere Informationen finden Sie unter [Veröffentlichen der neuesten Bot-Inhalte](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).</span><span class="sxs-lookup"><span data-stu-id="ca6e8-119">For more information, see [Publish the latest bot content](/power-virtual-agents/publication-fundamentals-publish-channels#publish-the-latest-bot-content).</span></span>

   ![Veröffentlichen im Power Virtual Agents Portal](../../assets/images/pva-publish.png)

1. <span data-ttu-id="ca6e8-121">**Konfigurieren des Teams Kanals**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-121">**Configure the Teams channel**</span></span>  
<span data-ttu-id="ca6e8-122">Nachdem Sie Ihren Bot veröffentlicht haben, fügen Sie den Teams-Kanal hinzu, um den Bot Teams Benutzern zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-122">After publishing your bot, add the Teams channel to make the bot available to Teams users.</span></span>

   ![Kanäle im Power Virtual Agents Portal](../../assets/images/pva-channels.png)

1. <span data-ttu-id="ca6e8-124">**Generieren einer App-ID für Ihren Chatbot**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-124">**Generate an App ID for your chatbot**</span></span>  
<span data-ttu-id="ca6e8-125">Nach dem Hinzufügen des Teams Kanals zu Ihrem Chatbot wird im Dialogfeld eine **App-ID** generiert.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-125">After adding the Teams channel to your chatbot, an **App ID** is generated in the dialog box.</span></span> <span data-ttu-id="ca6e8-126">Die App-ID ist ein eindeutiger von Microsoft generierter Bezeichner für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-126">The App ID is a unique Microsoft generated identifier for your bot.</span></span> <span data-ttu-id="ca6e8-127">Speichern Sie die App-ID, um ein App-Paket für Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-127">Save the App ID to create an app package for Teams.</span></span>

## <a name="add-your-bot-to-teams-using-app-studio"></a><span data-ttu-id="ca6e8-128">Fügen Sie Ihren Bot mit App Studio zu Teams hinzu</span><span class="sxs-lookup"><span data-stu-id="ca6e8-128">Add your bot to Teams using App Studio</span></span>

<span data-ttu-id="ca6e8-129">Wenn das [Hochladen benutzerdefinierter Apps](/microsoftteams/admin-settings) in Ihrer Teams-Instanz aktiviert ist, können Sie Teams App Studio verwenden, um Ihren Chatbot direkt hochzuladen und sofort zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-129">If [uploading custom apps is enabled](/microsoftteams/admin-settings) in your Teams instance, you can use Teams App Studio to directly upload your chatbot and start using it immediately.</span></span> <span data-ttu-id="ca6e8-130">Um Ihren Chatbot freizugeben, können Sie Ihren Administrator auffordern, Ihren Bot im Mandanten-App-Katalog verfügbar zu machen, oder Sie können Ihr App-Paket an andere senden und sie bitten, es unabhängig hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-130">To share your chatbot, you can request your admin to make your bot available in the tenant app catalog or you can send your app package to others and ask them to upload it independently.</span></span>

1. <span data-ttu-id="ca6e8-131">**Installieren von App Studio in Teams**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-131">**Install App Studio in Teams**</span></span>  
<span data-ttu-id="ca6e8-132">App Studio ist eine Teams App.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-132">App Studio is a Teams app.</span></span> <span data-ttu-id="ca6e8-133">Installieren Sie App Studio aus dem Teams Store, der den Prozess der Boterstellung und -registrierung in Teams vereinfacht:</span><span class="sxs-lookup"><span data-stu-id="ca6e8-133">Install App Studio from the Teams store that simplifies the process of bot creation and registration in Teams:</span></span> 

   1. <span data-ttu-id="ca6e8-134">Wählen Sie das App Store-Symbol aus Teams Instanz aus, und suchen Sie nach **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-134">Select the app store icon from Teams instance, and search for **App Studio**.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Finding App Studio in the Store" src="../../assets/images/get-started/app-studio-store.png"/>   

   1. <span data-ttu-id="ca6e8-135">Wählen Sie die **Kachel App Studio** aus, und wählen Sie im Popup-Dialogfeld installieren aus. </span><span class="sxs-lookup"><span data-stu-id="ca6e8-135">Select the **App Studio** tile and select **Install** in the pop-up dialog box.</span></span>

      &emsp;&emsp; <img  width="450px" alt="Installing App Studio" src="../../assets/images/get-started/app-studio-install.png"/>

1. <span data-ttu-id="ca6e8-136">**Erstellen des Teams-App-Manifests in App Studio**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-136">**Create the Teams app manifest in App Studio**</span></span>  
<span data-ttu-id="ca6e8-137">Bots in Teams werden durch eine App-Manifest-JSON-Datei definiert, die die grundlegenden Informationen über Ihren Bot und seine Funktionen bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-137">Bots in Teams are defined by an app manifest JSON file that provides the basic information about your bot and its capabilities.</span></span> <span data-ttu-id="ca6e8-138">Wählen Sie in **App Studio** **den Manifest-Editor** aus, und wählen Sie **eine neue App erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-138">In **App Studio**, select **Manifest editor**, and select **Create a new app**.</span></span>

    ![Erstellen einer neuen App](../../assets/images/get-started/create-new-app.png)

1. <span data-ttu-id="ca6e8-140">**Fügen Sie Ihre Bot-Details hinzu**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-140">**Add your bot details**</span></span>  
<span data-ttu-id="ca6e8-141">Füllen Sie alle erforderlichen Felder aus.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-141">Complete all the required fields.</span></span> <span data-ttu-id="ca6e8-142">Eine vollständige Beschreibung der einzelnen Felde finden Sie unter [Manifestschemadefinition](../../resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e8-142">For a full description of each field see [manifest schema definition](../../resources/schema/manifest-schema.md).</span></span>

    ![Hinzufügen von App-Details](../../assets/images/get-started/add-app-details.png)

1. <span data-ttu-id="ca6e8-144">**Einrichten Ihres Bots** Führen Sie die folgenden Schritte aus, um den Bot einzurichten:</span><span class="sxs-lookup"><span data-stu-id="ca6e8-144">**Set up your bot** To set-up the bot, perform the following steps:</span></span> 
     1. <span data-ttu-id="ca6e8-145">Öffnen Sie die Registerkarte **Bots.**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-145">Open the **Bots** tab.</span></span> 
     1. <span data-ttu-id="ca6e8-146">Wählen Sie **Vorhandene**  >  **Bots** einrichten aus und geben Sie den Namen Ihres Bots ein.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-146">Select **Setup** > **Existing bot** and enter the name of your bot.</span></span>

   ![Bot-Setup](../../assets/images/get-started/bot-set-up.png) 

   <span data-ttu-id="ca6e8-148">Die folgende Abbildung zeigt, wie Sie einen vorhandenen Bot einrichten:</span><span class="sxs-lookup"><span data-stu-id="ca6e8-148">The following image depicts how to set-up an existing bot:</span></span>      

   ![bestehende Bot-Einrichtung](../../assets/images/get-started/existing-bot-set-up.png)
       
1. <span data-ttu-id="ca6e8-150">**Hinzufügen Ihrer App-ID**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-150">**Add your App ID**</span></span>  
<span data-ttu-id="ca6e8-151">Führen Sie die folgenden Schritte aus, um Ihre App-ID hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="ca6e8-151">To add your App ID, perform the following steps:</span></span>  
    1. <span data-ttu-id="ca6e8-152">Wählen Sie **Verbinden einer anderen Bot-ID** aus und fügen Sie die **App-ID ein,** die Sie zuvor kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-152">Select **Connect to a different bot id** and paste the **App Id** you copied earlier.</span></span> 
    1. <span data-ttu-id="ca6e8-153">Wählen Sie **Bereich**  >    >  **Persönlichespeichern**.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-153">Select **Scope** > **Personal** > **Save**.</span></span>

    ![App-ID hinzufügen](../../assets/images/get-started/add-app-id.png)

1. <span data-ttu-id="ca6e8-155">**Hinzufügen gültiger Domänen für Ihren Bot**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-155">**Add valid domains for your bot**</span></span>  
<span data-ttu-id="ca6e8-156">Dieser Schritt ist nur erforderlich, wenn Ihr Bot erfordert, dass sich der Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-156">This step is only required if your bot requires the user to sign in.</span></span> <span data-ttu-id="ca6e8-157">Wählen Sie **Domänen und Berechtigungen** aus, und geben Sie im Feld Gültige **Domänen** die folgenden Eingaben an:</span><span class="sxs-lookup"><span data-stu-id="ca6e8-157">Select **Domains and permissions** and in the **Valid Domains** field, provide the following input:</span></span>

    ```bash
       token.botframework.com
    ```

1. <span data-ttu-id="ca6e8-158">**Testen und verteilen Sie Ihren Bot**</span><span class="sxs-lookup"><span data-stu-id="ca6e8-158">**Test and distribute your bot**</span></span>  
<span data-ttu-id="ca6e8-159">Öffnen Sie die Registerkarte **Testen und verteilen,** und wählen Sie **Installieren** aus, um Ihren Bot direkt zu Ihrer Teams-Instanz hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-159">Open **Test and distribute** tab and select **Install** to add your bot directly to your Teams instance.</span></span> <span data-ttu-id="ca6e8-160">Alternativ können Sie das fertige App-Paket herunterladen, um es für Teams Benutzer freizugeben, oder es Ihrem Administrator zur Verfügung stellen, um Ihren Bot im Mandanten-App-Katalog verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-160">Alternately, you can download the completed app package to share with Teams users or provide it to your admin to make your bot available in the tenant app catalog.</span></span>

1. <span data-ttu-id="ca6e8-161">**Starten eines Chats** </span><span class="sxs-lookup"><span data-stu-id="ca6e8-161">**Start a chat** </span></span>  
<span data-ttu-id="ca6e8-162">Der Einrichtungsprozess zum Hinzufügen Ihres Power Virtual Agents Chat-Bots zu Teams ist abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-162">The set-up process for adding your Power Virtual Agents chat bot to Teams is complete.</span></span> <span data-ttu-id="ca6e8-163">Sie können jetzt ein Gespräch mit Ihrem Bot in einem persönlichen Chat beginnen.</span><span class="sxs-lookup"><span data-stu-id="ca6e8-163">You can now start a conversation with your bot in a personal chat.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca6e8-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ca6e8-164">See also</span></span>

- [<span data-ttu-id="ca6e8-165">Power Virtual Agents</span><span class="sxs-lookup"><span data-stu-id="ca6e8-165">Power Virtual Agents</span></span>](/power-virtual-agents/fundamentals-what-is-power-virtual-agents)  

- <span data-ttu-id="ca6e8-166">[Erstellen Sie einen Chatbot für Teams mit Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).</span><span class="sxs-lookup"><span data-stu-id="ca6e8-166">[Create a chatbot for Teams with Microsoft Power Virtual Agents](../bot-features.md#bots-and-the-microsoft-power-virtual-agents).</span></span>  

- [<span data-ttu-id="ca6e8-167">Power Virtual Agents Portal</span><span class="sxs-lookup"><span data-stu-id="ca6e8-167">Power Virtual Agents portal</span></span>](https://powervirtualagents.microsoft.com)

- [<span data-ttu-id="ca6e8-168">Veröffentlichen Sie Ihren Power Virtual Agents-Bot</span><span class="sxs-lookup"><span data-stu-id="ca6e8-168">Publish your Power Virtual Agents bot</span></span>](/power-virtual-agents/publication-fundamentals-publish-channels)

- <span data-ttu-id="ca6e8-169">[Sicherheit und Compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span><span class="sxs-lookup"><span data-stu-id="ca6e8-169">[Security and compliance in Microsoft Teams](/MicrosoftTeams/security-compliance-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="ca6e8-170">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ca6e8-170">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca6e8-171">Virtueller Assistent erstellen</span><span class="sxs-lookup"><span data-stu-id="ca6e8-171">Create virtual assistant</span></span>](~/samples/virtual-assistant.md)

