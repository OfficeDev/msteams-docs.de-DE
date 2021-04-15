---
title: Eine Messaging-Erweiterung mit App Studio erstellen
author: clearab
description: Erfahren Sie, wie Sie eine Microsoft Teams-Messagingerweiterung mit App Studio erstellen.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 25086d959004046e8227de46b31d840c0b3fd228
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697232"
---
# <a name="create-a-messaging-extension-using-app-studio"></a><span data-ttu-id="e5d52-103">Eine Messaging-Erweiterung mit App Studio erstellen</span><span class="sxs-lookup"><span data-stu-id="e5d52-103">Create a messaging extension using App Studio</span></span>

> [!TIP]
> <span data-ttu-id="e5d52-104">Suchen Sie nach einer schnelleren Möglichkeit für die ersten Schritte?</span><span class="sxs-lookup"><span data-stu-id="e5d52-104">Looking for a faster way to get started?</span></span> <span data-ttu-id="e5d52-105">Erstellen Sie [eine Messagingerweiterung](../build-your-first-app/build-messaging-extension.md) mithilfe des Microsoft Teams Toolkits.</span><span class="sxs-lookup"><span data-stu-id="e5d52-105">Create a [messaging extension](../build-your-first-app/build-messaging-extension.md) using the Microsoft Teams Toolkit.</span></span>

<span data-ttu-id="e5d52-106">Auf einer hohen Ebene müssen Sie die folgenden Schritte ausführen, um eine Messagingerweiterung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-106">At a high level, you'll need to complete the following steps to create a messaging extension.</span></span>

1. <span data-ttu-id="e5d52-107">Vorbereiten Ihrer Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="e5d52-107">Prepare your development environment</span></span>
2. <span data-ttu-id="e5d52-108">Erstellen und Bereitstellen Des Webdiensts (während der Entwicklung eines Tunneldiensts wie ngrok, um ihn lokal ausführen)</span><span class="sxs-lookup"><span data-stu-id="e5d52-108">Create and deploy your web service (while developing use a tunneling service like ngrok to run it locally)</span></span>
3. <span data-ttu-id="e5d52-109">Registrieren Ihres Webdiensts bei Bot Framework</span><span class="sxs-lookup"><span data-stu-id="e5d52-109">Register your web service with the Bot Framework</span></span>
4. <span data-ttu-id="e5d52-110">Erstellen Ihres App-Pakets</span><span class="sxs-lookup"><span data-stu-id="e5d52-110">Create your app package</span></span>
5. <span data-ttu-id="e5d52-111">Hochladen Ihres Pakets in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e5d52-111">Upload your package to Microsoft Teams</span></span>

<span data-ttu-id="e5d52-112">Das Erstellen Ihres Webdiensts, das Erstellen Ihres App-Pakets und die Registrierung Ihres Webdiensts beim Bot Framework können in beliebiger Reihenfolge durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-112">Creating your web service, creating your app package, and registering your web service with the Bot Framework can be done in any order.</span></span> <span data-ttu-id="e5d52-113">Da diese drei Teile so miteinander verwoben sind, müssen Sie unabhängig von der Reihenfolge, in der Sie sie tun, zurückkehren, um die anderen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-113">Because those three pieces are so intertwined, no matter which order you do them in you'll need return to update the others.</span></span> <span data-ttu-id="e5d52-114">Ihre Registrierung benötigt den Messagingendpunkt von Ihrem bereitgestellten Webdienst, und Ihr Webdienst benötigt die ID und das Kennwort, die aus Ihrer Registrierung erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-114">Your registration needs the messaging endpoint from your deployed web service, and your web service needs the Id and password created from your registration.</span></span> <span data-ttu-id="e5d52-115">Ihr App-Manifest benötigt diese ID auch, um Teams mit Ihrem Webdienst zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-115">Your app manifest also needs that Id to connect Teams to your web service.</span></span>

<span data-ttu-id="e5d52-116">Während Sie Ihre Messagingerweiterung erstellen, wechseln Sie regelmäßig zwischen dem Ändern des App-Manifests und der Bereitstellung von Code in Ihrem Webdienst.</span><span class="sxs-lookup"><span data-stu-id="e5d52-116">As you're building your messaging extension, you'll regularly be moving between changing your app manifest, and deploying code to your web service.</span></span> <span data-ttu-id="e5d52-117">Beachten Sie bei der Arbeit mit dem App-Manifest, dass Sie die JSON-Datei manuell bearbeiten oder Änderungen über App Studio vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="e5d52-117">When working with the app manifest, keep in mind that you can either manually manipulate the JSON file, or make changes through App Studio.</span></span> <span data-ttu-id="e5d52-118">So oder so müssen Sie Ihre App in Teams erneut bereitstellen (hochladen), wenn Sie eine Änderung am Manifest vornehmen. Dies ist jedoch nicht nötig, wenn Sie Änderungen an Ihrem Webdienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-118">Either way, you'll need to re-deploy (upload) your app in Teams when you make a change to the manifest, but there's no need to do so when you deploy changes to your web service.</span></span>

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a><span data-ttu-id="e5d52-119">Erstellen Ihres Webdiensts</span><span class="sxs-lookup"><span data-stu-id="e5d52-119">Create your web service</span></span>

<span data-ttu-id="e5d52-120">Das Herzstück Ihrer Messagingerweiterung ist Ihr Webdienst.</span><span class="sxs-lookup"><span data-stu-id="e5d52-120">The heart of your messaging extension is your web service.</span></span> <span data-ttu-id="e5d52-121">Es wird eine einzelne Route definiert, in der Regel `/api/messages` , um alle Anforderungen zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-121">It will define a single route, typically `/api/messages`, to receive all requests on.</span></span> <span data-ttu-id="e5d52-122">Wenn Sie von Grund auf beginnen, haben Sie einige Optionen zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="e5d52-122">If you're getting started from scratch, you have a few options to choose from.</span></span>

* <span data-ttu-id="e5d52-123">Verwenden Sie eines unserer [Schnellstart-Lernprogramme,](#learn-more) die Sie durch die Erstellung Ihres Webdiensts führen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-123">Use one of our [quickstarts](#learn-more) tutorials that will guide you through the creation of your web service.</span></span>
* <span data-ttu-id="e5d52-124">Wählen Sie eines der Messagingerweiterungsbeispiele aus, die im Bot Framework-Beispielrepository zum Starten verfügbar sind. [](https://github.com/Microsoft/BotBuilder-Samples)</span><span class="sxs-lookup"><span data-stu-id="e5d52-124">Choose one of the messaging extension samples available in the [Bot Framework sample repository](https://github.com/Microsoft/BotBuilder-Samples) to start from.</span></span>
* <span data-ttu-id="e5d52-125">Wenn Sie JavaScript verwenden, verwenden Sie den [Yeoman-Generator für Microsoft Teams,](https://github.com/OfficeDev/generator-teams) um Ihre Teams-App einschließlich Ihres Webdiensts zu gerüsten.</span><span class="sxs-lookup"><span data-stu-id="e5d52-125">If you're using JavaScript, use the [Yeoman generator for Microsoft Teams](https://github.com/OfficeDev/generator-teams) to scaffold your Teams app, including your web service.</span></span>
* <span data-ttu-id="e5d52-126">Erstellen Sie Ihren Webdienst von Grund auf neu.</span><span class="sxs-lookup"><span data-stu-id="e5d52-126">Create your web service from scratch.</span></span> <span data-ttu-id="e5d52-127">Sie können das Bot Framework-SDK für Ihre Sprache hinzufügen oder direkt mit den JSON-Nutzlasten arbeiten.</span><span class="sxs-lookup"><span data-stu-id="e5d52-127">You can choose to add the Bot Framework SDK for your language, or you can work directly with the JSON payloads.</span></span>

## <a name="register-your-web-service-with-the-bot-framework"></a><span data-ttu-id="e5d52-128">Registrieren Ihres Webdiensts bei Bot Framework</span><span class="sxs-lookup"><span data-stu-id="e5d52-128">Register your web service with the Bot Framework</span></span>

<span data-ttu-id="e5d52-129">Messagingerweiterungen nutzen das Messagingschema und das sichere Kommunikationsprotokoll von Bot Framework. Wenn Sie noch nicht über einen verfügen, müssen Sie Ihren Webdienst im Bot Framework registrieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-129">Messaging extensions take advantage of the Bot Framework's messaging schema and secure communication protocol; if you don't already have one you'll need to register your web service on the Bot Framework.</span></span> <span data-ttu-id="e5d52-130">Die Microsoft App-ID (wir bezeichnen dies als Ihre Bot-ID von innerhalb von Teams, um sie von anderen App-IDs zu identifizieren, mit der Sie möglicherweise arbeiten) und der Messagingendpunkt, mit dem Sie sich beim Bot Framework registrieren, werden in Ihrer Messagingerweiterung zum Empfangen und Beantworten von Anforderungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5d52-130">The Microsoft App Id (we'll refer to this as your Bot Id from inside of Teams, to identify it from other App Id's you might be working with) and the messaging endpoint your register with the Bot Framework will be used in your messaging extension to receive and respond to requests.</span></span> <span data-ttu-id="e5d52-131">Wenn Sie eine vorhandene Registrierung verwenden, stellen Sie sicher, dass Sie [den Microsoft Teams-Kanal aktivieren.](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="e5d52-131">If you're using an existing registration, make sure you [enable the Microsoft Teams channel](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="e5d52-132">Wenn Sie einem der Schnellstarts folgen oder von einem der verfügbaren Beispiele starten, werden Sie durch die Registrierung Ihres Webdiensts geführt.</span><span class="sxs-lookup"><span data-stu-id="e5d52-132">If you follow one of the quickstarts or start from one of the available samples you'll be guided through registering your web service.</span></span> <span data-ttu-id="e5d52-133">Wenn Sie Ihren Dienst manuell registrieren möchten, haben Sie drei Möglichkeiten dazu.</span><span class="sxs-lookup"><span data-stu-id="e5d52-133">If you want to manually register your service you have three options to do so.</span></span> <span data-ttu-id="e5d52-134">Wenn Sie sich ohne Verwendung eines Azure-Abonnements registrieren möchten, können Sie den vereinfachten OAuth-Authentifizierungsfluss, der vom Bot Framework bereitgestellt wird, nicht nutzen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-134">If you choose to register without using an Azure subscription you will not be able to take advantage of the simplified OAuth authentication flow provided by the Bot Framework.</span></span> <span data-ttu-id="e5d52-135">Sie können Ihre Registrierung nach der Erstellung zu Azure migrieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-135">You will be able to migrate your registration to Azure after creation.</span></span>

* <span data-ttu-id="e5d52-136">Wenn Sie über ein Azure-Abonnement verfügen (oder ein neues erstellen möchten), können Sie Ihren Webdienst manuell über das Azure-Portal registrieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-136">If you have an Azure subscription (or want to create a new one), you can register your web service manually using the Azure Portal.</span></span> <span data-ttu-id="e5d52-137">Erstellen Sie eine Ressource "Bot Channels Registration".</span><span class="sxs-lookup"><span data-stu-id="e5d52-137">Create a "Bot Channels Registration" resource.</span></span> <span data-ttu-id="e5d52-138">Sie können die kostenlose Preisebene auswählen, da Nachrichten von Microsoft Teams nicht auf Ihre zulässigen Gesamtnachrichten pro Monat gezählt werden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-138">You can choose the free pricing tier, as messages from Microsoft Teams do not count towards your total allowable messages per month.</span></span>
* <span data-ttu-id="e5d52-139">Wenn Sie kein Azure-Abonnement verwenden möchten, können Sie das [Legacyregistrierungsportal verwenden.](https://dev.botframework.com/bots/new)</span><span class="sxs-lookup"><span data-stu-id="e5d52-139">If you do not wish to use an Azure subscription, you can use the [legacy registration portal](https://dev.botframework.com/bots/new).</span></span>
* <span data-ttu-id="e5d52-140">App Studio kann Ihnen auch bei der Registrierung Ihres Webdiensts (Bot) helfen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-140">App Studio can also help you register your web service (bot).</span></span> <span data-ttu-id="e5d52-141">Webdienste, die über App Studio registriert sind, sind nicht in Azure registriert.</span><span class="sxs-lookup"><span data-stu-id="e5d52-141">Web services registered through App Studio are not registered in Azure.</span></span> <span data-ttu-id="e5d52-142">Mit dem [Legacyportal können](https://dev.botframework.com/bots) Sie Ihre Registrierungen anzeigen, verwalten und migrieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-142">You can use the [legacy portal](https://dev.botframework.com/bots) to view, manage, and migrate your registrations.</span></span>

## <a name="create-your-app-manifest"></a><span data-ttu-id="e5d52-143">Erstellen Ihres App-Manifests</span><span class="sxs-lookup"><span data-stu-id="e5d52-143">Create your app manifest</span></span>

<span data-ttu-id="e5d52-144">Sie können Ihr App-Manifest entweder in App Studio oder manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-144">You can either use App Studio to help you create your app manifest, or create it manually.</span></span>

### <a name="create-your-app-manifest-using-app-studio"></a><span data-ttu-id="e5d52-145">Erstellen Ihres App-Manifests mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="e5d52-145">Create your app manifest using App Studio</span></span>

<span data-ttu-id="e5d52-146">Sie können die App Studio-App aus dem Microsoft Teams-Client verwenden, um Ihr App-Manifest zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-146">You can use the App Studio app from within the Microsoft Teams client to help create your app manifest.</span></span>

1. <span data-ttu-id="e5d52-147">Öffnen Sie App Studio im Teams-Client aus dem **...**-Überlaufmenü auf der linken Navigationsleiste.</span><span class="sxs-lookup"><span data-stu-id="e5d52-147">In the Teams client, open App Studio from the **...** overflow menu on the left navigation rail.</span></span> <span data-ttu-id="e5d52-148">Wenn es noch nicht installiert ist, können Sie dies tun, indem Sie danach suchen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-148">If it isn't already installed, you can do so by searching for it.</span></span>
2. <span data-ttu-id="e5d52-149">Wählen Sie **auf der Registerkarte Manifest-Editor** die Option **Neue** App erstellen aus (oder wenn Sie einer vorhandenen App eine Messagingerweiterung hinzufügen, können Sie Ihr App-Paket importieren)</span><span class="sxs-lookup"><span data-stu-id="e5d52-149">On the **Manifest editor** tab select **Create a new app** (or if you're adding a messaging extension to an existing app, you can import your app package)</span></span>
3. <span data-ttu-id="e5d52-150">Fügen Sie Ihre App-Details hinzu (in der [Manifestschemadefinition](~/resources/schema/manifest-schema.md) finden Sie die vollständigen Beschreibungen der einzelnen Felder).</span><span class="sxs-lookup"><span data-stu-id="e5d52-150">Add your app details (see [manifest schema definition](~/resources/schema/manifest-schema.md) for full descriptions of each field).</span></span>
4. <span data-ttu-id="e5d52-151">Klicken Sie auf der Registerkarte **Messagingerweiterungen** auf die **Schaltfläche Setup.**</span><span class="sxs-lookup"><span data-stu-id="e5d52-151">On the **Messaging extensions** tab click the **Setup** button.</span></span>
5. <span data-ttu-id="e5d52-152">Sie können entweder einen neuen Webdienst (Bot) erstellen, damit Ihre Messagingerweiterung verwendet werden kann, oder wenn Sie bereits einen registriert haben, wählen/fügen Sie ihn hier hinzu.</span><span class="sxs-lookup"><span data-stu-id="e5d52-152">You can either create a new web service (bot) for your messaging extension to use, or if you've already registered one select/add it here.</span></span>
6. <span data-ttu-id="e5d52-153">Aktualisieren Sie Ihre Bot-Endpunktadresse bei Bedarf so, dass Sie auf Ihren Bot verweist.</span><span class="sxs-lookup"><span data-stu-id="e5d52-153">If necessary, update your bot endpoint address to point to your bot.</span></span> <span data-ttu-id="e5d52-154">Dies sollte ungefähr so aussehen: `https://someplace.com/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="e5d52-154">It should look something like `https://someplace.com/api/messages`.</span></span>
7. <span data-ttu-id="e5d52-155">Die **Schaltfläche** Hinzufügen im **Abschnitt Befehl** führt Sie durch das Hinzufügen von Befehlen zu Ihrer Messagingerweiterung.</span><span class="sxs-lookup"><span data-stu-id="e5d52-155">The **Add** button in the **Command** section will guide you through adding commands to your messaging extension.</span></span> <span data-ttu-id="e5d52-156">Im Abschnitt [Weitere Informationen finden](#learn-more) Sie Links zu weiteren Informationen zum Hinzufügen von Befehlen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-156">See the [Learn more](#learn-more) section for links to more information on adding commands.</span></span> <span data-ttu-id="e5d52-157">Denken Sie daran, dass Sie bis zu 10 Befehle für Ihre Messagingerweiterung definieren können.</span><span class="sxs-lookup"><span data-stu-id="e5d52-157">Remember you can define up to 10 commands for your messaging extension.</span></span>
8. <span data-ttu-id="e5d52-158">Im **Abschnitt Nachrichtenhandler können** Sie eine Domäne hinzufügen, für die Ihr Messaging ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="e5d52-158">The **Message Handlers** section allows you to add a domain that your messaging will trigger on.</span></span> <span data-ttu-id="e5d52-159">Weitere Informationen finden Sie unter Link [unfurling.](~/messaging-extensions/how-to/link-unfurling.md)</span><span class="sxs-lookup"><span data-stu-id="e5d52-159">See [link unfurling](~/messaging-extensions/how-to/link-unfurling.md) for more information.</span></span>

<span data-ttu-id="e5d52-160">Auf der Registerkarte Finish => Test  and **distribute** können Sie Ihr App-Paket herunterladen (das ihr App-Manifest sowie Ihre App-Symbole enthält) oder **das** Paket installieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-160">From the **Finish => Test and distribute** tab you can **Download** your app package (which includes your app manifest as well as your app icons), or **Install** the package.</span></span>

### <a name="create-your-app-manifest-manually"></a><span data-ttu-id="e5d52-161">Manuelles Erstellen des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="e5d52-161">Create your app manifest manually</span></span>

<span data-ttu-id="e5d52-162">Wie bei Bots und Registerkarten aktualisieren Sie das [App-Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App so, dass die Nachrichtenerweiterungseigenschaften enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e5d52-162">As with bots and tabs, you update the [app manifest](~/resources/schema/manifest-schema.md#composeextensions) of your app to include the messaging extension properties.</span></span> <span data-ttu-id="e5d52-163">Diese Eigenschaften steuern, wie Ihre Messagingerweiterung angezeigt wird und wie sie sich im Microsoft Teams-Client verhält.</span><span class="sxs-lookup"><span data-stu-id="e5d52-163">These properties govern how your messaging extension appears and behaves in the Microsoft Teams client.</span></span> <span data-ttu-id="e5d52-164">Messagingerweiterungen werden ab Version 1.0 des Manifests unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e5d52-164">Messaging extensions are supported beginning with v1.0 of the manifest.</span></span>

#### <a name="declare-your-messaging-extension"></a><span data-ttu-id="e5d52-165">Deklarieren der Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="e5d52-165">Declare your messaging extension</span></span>

<span data-ttu-id="e5d52-166">Um eine Messagingerweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur auf oberster Ebene in Ihr App-Manifest mit der -Eigenschaft `composeExtensions` ein.</span><span class="sxs-lookup"><span data-stu-id="e5d52-166">To add a messaging extension, include a new top-level JSON structure in your app manifest with the `composeExtensions` property.</span></span> <span data-ttu-id="e5d52-167">Sie erstellen eine einzelne Messagingerweiterung für Ihre App mit bis zu 10 Befehlen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-167">You create a single messaging extension for your app, with up to 10 commands.</span></span>

> [!NOTE]
> <span data-ttu-id="e5d52-168">Das Manifest bezieht sich auf Messagingerweiterungen als `composeExtensions` .</span><span class="sxs-lookup"><span data-stu-id="e5d52-168">The manifest refers to messaging extensions as `composeExtensions`.</span></span> <span data-ttu-id="e5d52-169">Dadurch wird die Abwärtskompatibilität beibehalten.</span><span class="sxs-lookup"><span data-stu-id="e5d52-169">This is to maintain backward compatibility.</span></span>

<span data-ttu-id="e5d52-170">Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="e5d52-170">The extension definition is an object that has the following structure:</span></span>

| <span data-ttu-id="e5d52-171">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="e5d52-171">Property name</span></span> | <span data-ttu-id="e5d52-172">Zweck</span><span class="sxs-lookup"><span data-stu-id="e5d52-172">Purpose</span></span> | <span data-ttu-id="e5d52-173">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="e5d52-173">Required?</span></span> |
|---|---|---|
| `botId` | <span data-ttu-id="e5d52-174">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="e5d52-174">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="e5d52-175">Dies sollte in der Regel mit der ID ihrer gesamten Teams-App identisch sein.</span><span class="sxs-lookup"><span data-stu-id="e5d52-175">This should typically be the same as the ID for your overall Teams app.</span></span> | <span data-ttu-id="e5d52-176">Ja</span><span class="sxs-lookup"><span data-stu-id="e5d52-176">Yes</span></span> |
| `canUpdateConfiguration` | <span data-ttu-id="e5d52-177">Aktiviert **das Menüelement** Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-177">Enables **Settings** menu item.</span></span> | <span data-ttu-id="e5d52-178">Nein</span><span class="sxs-lookup"><span data-stu-id="e5d52-178">No</span></span> |
| `commands` | <span data-ttu-id="e5d52-179">Array von Befehlen, die von dieser Messagingerweiterung unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-179">Array of commands that this messaging extension supports.</span></span> <span data-ttu-id="e5d52-180">Sie sind auf 10 Befehle beschränkt.</span><span class="sxs-lookup"><span data-stu-id="e5d52-180">You are limited to 10 commands.</span></span> | <span data-ttu-id="e5d52-181">Ja</span><span class="sxs-lookup"><span data-stu-id="e5d52-181">Yes</span></span> |

#### <a name="define-your-commands"></a><span data-ttu-id="e5d52-182">Definieren von Befehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-182">Define your commands</span></span>

<span data-ttu-id="e5d52-183">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren, die definieren, wo Ihre Benutzer Ihre Messagingerweiterung auslösen können, und den Typ der Interaktion.</span><span class="sxs-lookup"><span data-stu-id="e5d52-183">Your messaging extension should declare one or more commands, which define where your users can trigger your messaging extension, and the type of interaction.</span></span> <span data-ttu-id="e5d52-184">Weitere Informationen zu Messagingerweiterungsbefehlen finden Sie unter weitere Informationen. [](#learn-more)</span><span class="sxs-lookup"><span data-stu-id="e5d52-184">See [learn more](#learn-more) for more information on messaging extension commands.</span></span>

#### <a name="simple-manifest-example"></a><span data-ttu-id="e5d52-185">Beispiel für ein einfaches Manifest</span><span class="sxs-lookup"><span data-stu-id="e5d52-185">Simple manifest example</span></span>

<span data-ttu-id="e5d52-186">Das folgende Beispiel ist ein einfaches Messagingerweiterungsobjekt im App-Manifest mit einem Suchbefehl.</span><span class="sxs-lookup"><span data-stu-id="e5d52-186">The following example is a simple messaging extension object in the app manifest with a search command.</span></span> <span data-ttu-id="e5d52-187">Hierbei handelt es sich nicht um die komplette App-Manifestdatei, sondern nur um den Teil der Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-187">This is not the entire app manifest file, just the part specific to messaging extensions.</span></span> <span data-ttu-id="e5d52-188">Ein vollständiges Beispiel finden Sie unter [App-Manifestschema.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="e5d52-188">See [app manifest schema](~/resources/schema/manifest-schema.md) for a complete example.</span></span>

```json
...
"composeExtensions": [
  {
    "botId": "abcd1234-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "searchCmd",
        "description": "Search you ToDo's",
        "title": "Search",
        "initialRun": true,
        "parameters": [
          {
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }
        ]
      }
    ]
  }
]
...
```

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="e5d52-189">Vollständiges Beispiel für das App-Manifest</span><span class="sxs-lookup"><span data-stu-id="e5d52-189">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

## <a name="add-your-invoke-message-handlers"></a><span data-ttu-id="e5d52-190">Hinzufügen der aufruften Nachrichtenhandler</span><span class="sxs-lookup"><span data-stu-id="e5d52-190">Add your invoke message handlers</span></span>

<span data-ttu-id="e5d52-191">Wenn Ihre Benutzer Ihre Messagingerweiterung auslösen, müssen Sie die anfängliche Aufrufnachricht verarbeiten, einige Informationen vom Benutzer sammeln, diese Informationen verarbeiten und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-191">When your users trigger your messaging extension you'll need to handle the initial invoke message, collect some information from the user, then process that information and respond appropriately.</span></span> <span data-ttu-id="e5d52-192">Zu diesem Schritt müssen Sie zunächst entscheiden, welche Art von BefehlEn Sie [](~/messaging-extensions/how-to/action-commands/define-action-command.md) Ihrer Messagingerweiterung hinzufügen möchten, und entweder einen Aktionsbefehl hinzufügen oder [suchbefehle hinzufügen.](~/messaging-extensions/how-to/search-commands/define-search-command.md)</span><span class="sxs-lookup"><span data-stu-id="e5d52-192">To do that, you'll first need to decide what kind of commands you want to add to your messaging extension and either [add an action commands](~/messaging-extensions/how-to/action-commands/define-action-command.md) or [add a search commands](~/messaging-extensions/how-to/search-commands/define-search-command.md).</span></span>

## <a name="messaging-extensions-in-teams-meetings"></a><span data-ttu-id="e5d52-193">Messagingerweiterungen in Teams-Besprechungen</span><span class="sxs-lookup"><span data-stu-id="e5d52-193">Messaging extensions in Teams meetings</span></span>

> [!NOTE]
> <span data-ttu-id="e5d52-194">Wenn in einem Besprechungs- oder Gruppenchat Verbundbenutzer im Dienstplan stehen, unterdrückt Teams den Zugriff auf Messagingerweiterungen für alle Benutzer, einschließlich des Organisators.</span><span class="sxs-lookup"><span data-stu-id="e5d52-194">If a meeting or group chat has federated users in the roster, Teams suppresses access to messaging extensions for all users, including the organizer.</span></span>

<span data-ttu-id="e5d52-195">Sobald eine Besprechung beginnt, können Teams-Teilnehmer während eines Liveanrufs direkt mit Ihrer Messagingerweiterung interagieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-195">Once a meeting begins, Teams participants can interact directly with your messaging extension during a live call.</span></span> <span data-ttu-id="e5d52-196">Berücksichtigen Sie beim Erstellen Der Messagingerweiterung in Besprechungen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e5d52-196">Consider the following when building your in-meeting messaging extension:</span></span>

1. <span data-ttu-id="e5d52-197">**Location**.</span><span class="sxs-lookup"><span data-stu-id="e5d52-197">**Location**.</span></span> <span data-ttu-id="e5d52-198">Ihre Messagingerweiterung kann aus dem Bereich "Nachricht verfassen", dem Befehlsfeld oder @mentioned besprechungschat aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-198">Your messaging extension can be invoked from the compose message area, the command box, or @mentioned in the meeting chat.</span></span>

1. <span data-ttu-id="e5d52-199">**Metadaten**.</span><span class="sxs-lookup"><span data-stu-id="e5d52-199">**Metadata**.</span></span> <span data-ttu-id="e5d52-200">Wenn Ihre Messagingerweiterung aufgerufen wird, kann sie den Benutzer und Mandanten von `userId` und `tenantId` identifizieren.</span><span class="sxs-lookup"><span data-stu-id="e5d52-200">When your messaging extension is invoked it can identify the user and tenant from `userId` and `tenantId`.</span></span> <span data-ttu-id="e5d52-201">Die `meetingId`kann als Teil des Objekts `channelData` gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="e5d52-201">The `meetingId` can be found as part of the `channelData` object.</span></span> <span data-ttu-id="e5d52-202">Ihre App kann das `userId` und `meetingId`  für die `GetParticipant` API-Anforderung verwenden, um Benutzerrollen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-202">Your app can use the `userId` and `meetingId`  for the `GetParticipant` API request to retrieve user roles.</span></span>

1. <span data-ttu-id="e5d52-203">**Befehlstyp**.</span><span class="sxs-lookup"><span data-stu-id="e5d52-203">**Command type**.</span></span> <span data-ttu-id="e5d52-204">Wenn Ihre Nachrichtenerweiterung [aktionsbasierte Befehle verwendet,](../messaging-extensions/what-are-messaging-extensions.md#action-commands)sollte sie den [Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md) für einmaliges Anmelden folgen.</span><span class="sxs-lookup"><span data-stu-id="e5d52-204">If your message extension uses [action-based commands](../messaging-extensions/what-are-messaging-extensions.md#action-commands), it should follow tabs [single sign-on](../tabs/how-to/authentication/auth-aad-sso.md) authentication.</span></span>

1. <span data-ttu-id="e5d52-205">**Benutzeroberfläche**.</span><span class="sxs-lookup"><span data-stu-id="e5d52-205">**User experience**.</span></span> <span data-ttu-id="e5d52-206">Die Messagingerweiterung sollte genauso aussehen und verhalten wie außerhalb einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="e5d52-206">You messaging extension should look and behave the same as it would outside a meeting.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e5d52-207">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="e5d52-207">Next steps</span></span>

* [<span data-ttu-id="e5d52-208">Erstellen von Aktionsbefehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-208">Create action commands</span></span>](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="e5d52-209">Erstellen von Suchbefehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-209">Create search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [<span data-ttu-id="e5d52-210">Entfalten von Links</span><span class="sxs-lookup"><span data-stu-id="e5d52-210">Link unfurling</span></span>](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a><span data-ttu-id="e5d52-211">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5d52-211">Learn more</span></span>

<span data-ttu-id="e5d52-212">Testen Sie es in einem Schnellstart:</span><span class="sxs-lookup"><span data-stu-id="e5d52-212">Try it out in a quickstart:</span></span>

* <span data-ttu-id="e5d52-213">Schnellstarts für C #</span><span class="sxs-lookup"><span data-stu-id="e5d52-213">Quickstarts for C#</span></span>
  * [<span data-ttu-id="e5d52-214">Messagingerweiterung mit aktionsbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-214">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [<span data-ttu-id="e5d52-215">Messagingerweiterung mit suchbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-215">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* <span data-ttu-id="e5d52-216">Schnellstarts für JavaScript</span><span class="sxs-lookup"><span data-stu-id="e5d52-216">Quickstarts for JavaScript</span></span>
  * [<span data-ttu-id="e5d52-217">Messagingerweiterung mit aktionsbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-217">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [<span data-ttu-id="e5d52-218">Messagingerweiterung mit suchbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="e5d52-218">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

<span data-ttu-id="e5d52-219">Weitere Informationen zu Teams-Entwicklungskonzepten:</span><span class="sxs-lookup"><span data-stu-id="e5d52-219">Learn more about Teams development concepts:</span></span>

* [<span data-ttu-id="e5d52-220">Verstehen der Funktionen von Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="e5d52-220">Understand Teams app capabilities</span></span>](../concepts/capabilities-overview.md)
* [<span data-ttu-id="e5d52-221">Was sind Messaging-Erweiterungen?</span><span class="sxs-lookup"><span data-stu-id="e5d52-221">What are messaging extensions?</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
