---
title: Testen und Debuggen des bot lokal
author: clearab
description: Testen und Debuggen Ihres bot lokal mit einer IDE
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 8494302b41e33910cb33f8c6889d82505b703577
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674215"
---
# <a name="test-and-debug-your-bot-locally"></a><span data-ttu-id="34808-103">Testen und Debuggen des bot lokal</span><span class="sxs-lookup"><span data-stu-id="34808-103">Test and debug your bot locally</span></span>

<span data-ttu-id="34808-104">Wenn Sie Ihren bot testen, müssen Sie sowohl den Kontext (die), den Sie für Ihren bot ausführen möchten, als auch alle Funktionen berücksichtigen, die Sie Ihrem bot möglicherweise hinzugefügt haben und für Microsoft Teams spezifische Daten benötigen.</span><span class="sxs-lookup"><span data-stu-id="34808-104">When testing your bot you need to take into consideration both the context(s) you want your bot to run in, as well as any functionality you may have added to your bot that requires data specific to Microsoft Teams.</span></span> <span data-ttu-id="34808-105">Stellen Sie sicher, dass die Methode, die Sie zum Testen Ihres bot ausgewählt haben, mit der Funktionalität übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="34808-105">Make sure that the method you chose to test your bot aligns with its functionality.</span></span>

## <a name="test-by-uploading-to-teams"></a><span data-ttu-id="34808-106">Testen durch Hochladen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="34808-106">Test by uploading to Teams</span></span>

<span data-ttu-id="34808-107">Die umfassendste Möglichkeit zum Testen Ihres bot besteht darin, ein App-Paket zu erstellen und es in Microsoft Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="34808-107">The most comprehensive way to test your bot is by creating an app package and uploading it to Teams.</span></span> <span data-ttu-id="34808-108">Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die für Ihren bot zur Verfügung steht, über alle Bereiche hinweg.</span><span class="sxs-lookup"><span data-stu-id="34808-108">This is the only method to test the full functionality available to your bot, across all scopes.</span></span>

<span data-ttu-id="34808-109">Es gibt zwei Methoden zum Hochladen Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="34808-109">There are two methods for uploading your app.</span></span> <span data-ttu-id="34808-110">Sie können entweder [App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden, um Ihnen zu helfen, oder Sie können [ein App-Paket manuell erstellen](~/concepts/build-and-test/apps-package.md) und [Ihre APP hochladen](~/concepts/deploy-and-publish/apps-upload.md).</span><span class="sxs-lookup"><span data-stu-id="34808-110">You can either use [App Studio](~/concepts/build-and-test/app-studio-overview.md) to help you, or you can manually [create an app package](~/concepts/build-and-test/apps-package.md) and [upload your app](~/concepts/deploy-and-publish/apps-upload.md).</span></span> <span data-ttu-id="34808-111">Wenn Sie Ihr Manifest ändern und Ihre APP erneut hochladen müssen, sollten Sie [ihren bot](#deleting-a-bot-from-teams) vor dem Hochladen Ihres geänderten App-Pakets löschen.</span><span class="sxs-lookup"><span data-stu-id="34808-111">If you need to alter your manifest and re-upload your app, you should [delete your bot](#deleting-a-bot-from-teams) before uploading your altered app package.</span></span>

## <a name="debug-your-bot-locally"></a><span data-ttu-id="34808-112">Debuggen des bot lokal</span><span class="sxs-lookup"><span data-stu-id="34808-112">Debug your bot locally</span></span>

<span data-ttu-id="34808-113">Wenn Sie Ihren bot während der Entwicklung lokal hosten, müssen Sie einen Tunnel Dienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren bot zu testen.</span><span class="sxs-lookup"><span data-stu-id="34808-113">If you are hosting your bot locally during development you'll need to use a tunneling service like [ngrok](https://ngrok.com/) in order to test your bot.</span></span> <span data-ttu-id="34808-114">Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunnel Dienst zu starten (möglicherweise müssen Sie ngrok zu Ihrem Pfad hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="34808-114">Once you've downloaded and installed ngrok, run the below command to start the tunneling service (you may need to add ngrok to your path).</span></span>

```bash
ngrok http <port> -host-header=localhost:<port>
```

<span data-ttu-id="34808-115">Verwenden Sie den von ngrok bereitgestellten HTTPS-Endpunkt in Ihrem App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="34808-115">Use the https endpoint provided by ngrok in your app manifest.</span></span> <span data-ttu-id="34808-116">Wenn Sie das Befehlsfenster schließen und neu starten, erhalten Sie eine neue URL, und Sie müssen ihre bot-Endpunktadresse so aktualisieren, dass diese ebenfalls verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="34808-116">If you close your command window and restart you'll get a new URL, and you'll need to update your bot endpoint address to use that one as well.</span></span>

## <a name="testing-your-bot-without-uploading-to-teams"></a><span data-ttu-id="34808-117">Testen Ihres bot ohne hochladen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="34808-117">Testing your bot without uploading to Teams</span></span>

<span data-ttu-id="34808-118">Gelegentlich kann es erforderlich sein, ihren bot zu testen, ohne ihn als app in Microsoft Teams zu installieren.</span><span class="sxs-lookup"><span data-stu-id="34808-118">Occasionally it may be necessary to test your bot without installing it as an app in Teams.</span></span> <span data-ttu-id="34808-119">Hierzu stehen zwei Methoden zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="34808-119">We provide two methods for doing so below.</span></span> <span data-ttu-id="34808-120">Das Testen Ihres bot ohne Installation als APP kann nützlich sein, um sicherzustellen, dass Ihr bot verfügbar ist und reagiert, aber Sie können nicht die gesamte Bandbreite der Microsoft Teams-Funktionen testen, die Sie Ihrem bot möglicherweise hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="34808-120">Testing your bot without installing it as an app can be useful to ensure your bot is available and responding, however it will not allow you to test the full breadth of Microsoft Teams functionality you may have added to your bot.</span></span> <span data-ttu-id="34808-121">Wenn Sie Ihren bot vollständig testen müssen, befolgen Sie die Anweisungen zum [Testen durch Hochladen](#test-by-uploading-to-teams).</span><span class="sxs-lookup"><span data-stu-id="34808-121">If you need to fully test your bot, please follow the instructions for [testing by uploading](#test-by-uploading-to-teams).</span></span>

### <a name="use-the-bot-emulator"></a><span data-ttu-id="34808-122">Verwenden des bot-Emulators</span><span class="sxs-lookup"><span data-stu-id="34808-122">Use the Bot Emulator</span></span>

<span data-ttu-id="34808-123">Der bot Framework-Emulator ist eine Desktopanwendung, die bot-Entwicklern das Testen und Debuggen Ihrer Bots entweder lokal oder Remote ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="34808-123">The Bot Framework Emulator is a desktop application that allows bot developers to test and debug their bots, either locally or remotely.</span></span> <span data-ttu-id="34808-124">Mit dem Emulator können Sie mit Ihrem bot chatten und die von Ihrem bot gesendeten und empfangenen Nachrichten überprüfen.</span><span class="sxs-lookup"><span data-stu-id="34808-124">Using the emulator, you can chat with your bot and inspect the messages that your bot sends and receives.</span></span> <span data-ttu-id="34808-125">Dies kann nützlich sein, um zu überprüfen, ob Ihr bot verfügbar ist und reagiert, aber der Emulator erlaubt Ihnen nicht, alle Teams-spezifischen Funktionen zu testen, die Sie Ihrem bot hinzugefügt haben, und auch Antworten von Ihrem bot werden keine präzise visuelle Darstellung dessen sein, was Sie tun werden. in Microsoft Teams gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="34808-125">This can be useful for verifying that your bot is available and responding, however the emulator will not allow you to test any Teams-specific functionality you've added to your bot, nor will responses from your bot be an accurate visual representation of how they will be rendered in Teams.</span></span> <span data-ttu-id="34808-126">Wenn Sie eines dieser beiden Dinge testen müssen, ist es am besten, [ihren bot hochzuladen](#test-by-uploading-to-teams).</span><span class="sxs-lookup"><span data-stu-id="34808-126">If you need to test either of those things it is best to [upload your bot](#test-by-uploading-to-teams).</span></span>

<span data-ttu-id="34808-127">Ausführliche Anweisungen zum bot Framework-Emulator finden Sie [hier](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="34808-127">Complete instructions on the Bot Framework Emulator can be found [here](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0).</span></span>

### <a name="talk-to-your-bot-directly-by-id"></a><span data-ttu-id="34808-128">Sprechen Sie mit Ihrem bot direkt über ID</span><span class="sxs-lookup"><span data-stu-id="34808-128">Talk to your bot directly by Id</span></span>

>[!Important]
><span data-ttu-id="34808-129">Das Gespräch mit Ihrem bot durch ID ist nur für grundlegende Testzwecke gedacht.</span><span class="sxs-lookup"><span data-stu-id="34808-129">Talking to your bot by Id is intended for basic testing purposes only.</span></span> <span data-ttu-id="34808-130">Alle Teams-spezifischen Funktionen, die Sie Ihrem bot hinzugefügt haben, können nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="34808-130">Any Teams-specific functionality you've added to your bot will not work.</span></span>

<span data-ttu-id="34808-131">Sie können auch eine Unterhaltung mit Ihrem bot initiieren, indem Sie dessen ID verwenden. Im folgenden sind zwei Methoden aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="34808-131">You can also initiate a conversation with your bot by using its Id. Two methods for doing so are given below.</span></span> <span data-ttu-id="34808-132">Wenn ein bot durch eine dieser Methoden hinzugefügt wurde, kann er nicht in Kanal Unterhaltungen verwendet werden, und Sie können nicht von anderen Microsoft Teams-App-Funktionen wie Registerkarten oder Messaging Erweiterungen profitieren.</span><span class="sxs-lookup"><span data-stu-id="34808-132">When a bot has been added through one of these methods it will not be addressable in channel conversations, and you cannot take advantage of other Microsoft Teams app capabilities like tabs or messaging extensions.</span></span>

1. <span data-ttu-id="34808-133">Wählen Sie auf der Seite [bot-Dashboard](https://dev.botframework.com/bots) für Ihren bot unter **Kanäle**die Option **zu Microsoft Teams hinzufügen**aus.</span><span class="sxs-lookup"><span data-stu-id="34808-133">On the [Bot Dashboard](https://dev.botframework.com/bots) page for your bot, under **Channels**, select **Add to Microsoft Teams**.</span></span> <span data-ttu-id="34808-134">Microsoft Teams wird mit einem persönlichen Chat mit Ihrem bot gestartet.</span><span class="sxs-lookup"><span data-stu-id="34808-134">Microsoft Teams will launch with a personal chat with your bot.</span></span>
2. <span data-ttu-id="34808-135">Verweisen Sie direkt in Microsoft Teams auf die APP-ID Ihres bot:</span><span class="sxs-lookup"><span data-stu-id="34808-135">Directly reference your bot's app ID from within Microsoft Teams:</span></span>
   * <span data-ttu-id="34808-136">Kopieren Sie auf der Seite [bot-Dashboard](https://dev.botframework.com/bots) für Ihren bot unter **Details**die **Microsoft-App-ID** für Ihren bot.</span><span class="sxs-lookup"><span data-stu-id="34808-136">On the [Bot Dashboard](https://dev.botframework.com/bots) page for your bot, under **Details**, copy the **Microsoft App ID** for your bot.</span></span>
  
     ![Aufrufen der-Anwendungskennung für den bot](~/assets/images/bots_appid_botframework.png)
  
   * <span data-ttu-id="34808-138">Wählen Sie in Microsoft Teams im **Chat** Bereich das Symbol **Chat hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="34808-138">From within Microsoft Teams, on the **Chat** pane, select the **Add chat** icon.</span></span> <span data-ttu-id="34808-139">**Um:**, fügen Sie die Microsoft-App-ID Ihres bot ein.</span><span class="sxs-lookup"><span data-stu-id="34808-139">For **To:**, paste your bot's Microsoft App ID.</span></span>
  
     ![Aufrufen der-Anwendungskennung für den bot](~/assets/images/bots_uploading.png)

     <span data-ttu-id="34808-141">Die APP-ID sollte in ihren bot-Namen aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="34808-141">The app ID should resolve to your bot name.</span></span>

   * <span data-ttu-id="34808-142">Wählen Sie Ihren bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="34808-142">Select your bot and send a message to initiate a conversation.</span></span>
   * <span data-ttu-id="34808-143">Alternativ können Sie die APP-ID Ihres bot in das Suchfeld oben links in Microsoft Teams einfügen.</span><span class="sxs-lookup"><span data-stu-id="34808-143">Alternatively, you can paste your bot's app ID in the search box in the top left in Microsoft Teams.</span></span> <span data-ttu-id="34808-144">Navigieren Sie auf der Suchergebnisseite zur Registerkarte Personen, um Ihren bot anzuzeigen und damit zu beginnen, damit zu chatten.</span><span class="sxs-lookup"><span data-stu-id="34808-144">In the search results page, navigate to the People tab to see your bot and to start chatting with it.</span></span>

<span data-ttu-id="34808-145">Ihr bot erhält das `conversationUpdate` Ereignis genauso wie Bots, die einem Team hinzugefügt wurden, jedoch ohne die Team `channelData` Informationen im Objekt.</span><span class="sxs-lookup"><span data-stu-id="34808-145">Your bot will receive the `conversationUpdate` event just like bots added to a team, but without the team information in the `channelData` object.</span></span>

## <a name="blocking-a-bot-in-personal-chat"></a><span data-ttu-id="34808-146">Blockieren eines bot im persönlichen Chat</span><span class="sxs-lookup"><span data-stu-id="34808-146">Blocking a bot in personal chat</span></span>

<span data-ttu-id="34808-147">Beachten Sie, dass Benutzer entscheiden können, ihren bot am Senden persönlicher Chatnachrichten zu hindern.</span><span class="sxs-lookup"><span data-stu-id="34808-147">Note that users can choose to block your bot from sending personal chat messages.</span></span> <span data-ttu-id="34808-148">Sie können dies umschalten, indem Sie mit der rechten Maustaste auf Ihren bot im Chat Kanal klicken und die Option bot-unter **Haltung blockieren**wählen.</span><span class="sxs-lookup"><span data-stu-id="34808-148">They may toggle this by right-clicking your bot in the chat channel and choosing **Block bot conversation**.</span></span> <span data-ttu-id="34808-149">Dies bedeutet, dass ihre Bots weiterhin Nachrichten senden, aber der Benutzer wird diese Nachrichten nicht erhalten.</span><span class="sxs-lookup"><span data-stu-id="34808-149">This means your bots will continue to send messages but the user will not receive those messages.</span></span>

![Blockieren eines bot](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a><span data-ttu-id="34808-151">Entfernen eines bot aus einem Team</span><span class="sxs-lookup"><span data-stu-id="34808-151">Removing a bot from a team</span></span>

<span data-ttu-id="34808-152">Benutzer können den bot löschen, indem Sie das Papierkorbsymbol in der Liste "Bots" in der Ansicht "Teams" auswählen.</span><span class="sxs-lookup"><span data-stu-id="34808-152">Users can delete the bot by choosing the trash-can icon on the bots list in their teams view.</span></span> <span data-ttu-id="34808-153">Beachten Sie, dass dadurch nur der bot aus der Verwendung dieses Teams entfernt wird; einzelne Benutzer können weiterhin im persönlichen Kontext interagieren.</span><span class="sxs-lookup"><span data-stu-id="34808-153">Note that this only removes the bot from that team's use; individual users will still be able to interact in personal context.</span></span>

<span data-ttu-id="34808-154">Bots im persönlichen Kontext können nicht deaktiviert oder von einem Benutzer entfernt werden, ohne dass der bot von Microsoft Teams vollständig entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="34808-154">Bots in personal context cannot be disabled or removed by a user, short of completely removing the bot from Teams.</span></span>

## <a name="disabling-a-bot-in-teams"></a><span data-ttu-id="34808-155">Deaktivieren eines bot in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="34808-155">Disabling a bot in Teams</span></span>

<span data-ttu-id="34808-156">Um Ihren bot beim Empfang von Nachrichten zu beenden, wechseln Sie zu Ihrem bot-Dashboard, und bearbeiten Sie den Microsoft Teams-Kanal.</span><span class="sxs-lookup"><span data-stu-id="34808-156">To stop your bot receiving messages, go to your Bot Dashboard and edit the Microsoft Teams channel.</span></span> <span data-ttu-id="34808-157">Deaktivieren Sie die Option **auf Microsoft Teams aktivieren** .</span><span class="sxs-lookup"><span data-stu-id="34808-157">Clear the **Enable on Microsoft Teams** option.</span></span> <span data-ttu-id="34808-158">Dadurch wird verhindert, dass Benutzer mit dem bot interagieren, er kann jedoch weiterhin erkannt werden, und die Benutzer können ihn weiterhin zu Microsoft Teams hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="34808-158">This prevents users from interacting with the bot, but it will still be discoverable and users will still be able to add it to teams.</span></span>

## <a name="deleting-a-bot-from-teams"></a><span data-ttu-id="34808-159">Löschen eines bot aus Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="34808-159">Deleting a bot from Teams</span></span>

<span data-ttu-id="34808-160">Wenn Sie Ihren bot vollständig aus Microsoft Teams entfernen möchten, wechseln Sie zu Ihrem bot-Dashboard, und bearbeiten Sie den Microsoft Teams-Kanal.</span><span class="sxs-lookup"><span data-stu-id="34808-160">To remove your bot completely from Teams, go to your Bot Dashboard and edit the Microsoft Teams channel.</span></span> <span data-ttu-id="34808-161">Klicken Sie unten auf die Schaltfläche **Löschen** .</span><span class="sxs-lookup"><span data-stu-id="34808-161">Choose the **Delete** button at the bottom.</span></span> <span data-ttu-id="34808-162">Dadurch wird verhindert, dass Benutzer ihren bot entdecken, hinzufügen oder mit ihr interagieren.</span><span class="sxs-lookup"><span data-stu-id="34808-162">This prevents users from discovering, adding, or interacting with your bot.</span></span> <span data-ttu-id="34808-163">Beachten Sie, dass dadurch der bot nicht aus den Teams-Instanzen anderer Benutzer entfernt wird, obwohl er auch für Sie nicht mehr funktioniert.</span><span class="sxs-lookup"><span data-stu-id="34808-163">Note that this does not remove the bot from other users' Teams instances, although it will cease functioning for them as well.</span></span>