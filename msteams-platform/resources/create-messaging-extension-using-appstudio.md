---
title: Eine Messaging-Erweiterung mit App Studio erstellen
author: surbhigupta
description: Erfahren Sie, wie Sie eine Microsoft Teams Messaging-Erweiterung mit App Studio erstellen.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 61bfed969b981bd5000bdb6eca0bbd77196e8086
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069223"
---
# <a name="create-a-messaging-extension-using-app-studio"></a><span data-ttu-id="11869-103">Eine Messaging-Erweiterung mit App Studio erstellen</span><span class="sxs-lookup"><span data-stu-id="11869-103">Create a messaging extension using App Studio</span></span>

> [!TIP]
> <span data-ttu-id="11869-104">Suchen Sie nach einer schnelleren Möglichkeit für die ersten Schritte?</span><span class="sxs-lookup"><span data-stu-id="11869-104">Looking for a faster way to get started?</span></span> <span data-ttu-id="11869-105">Erstellen Sie eine [Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md) mit dem Microsoft Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="11869-105">Create a [messaging extension](../build-your-first-app/build-messaging-extension.md) using the Microsoft Teams Toolkit.</span></span>

<span data-ttu-id="11869-106">Auf hoher Ebene müssen Sie die folgenden Schritte ausführen, um eine Messaging-Erweiterung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="11869-106">At a high level, you'll need to complete the following steps to create a messaging extension.</span></span>

1. <span data-ttu-id="11869-107">Vorbereiten Ihrer Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="11869-107">Prepare your development environment</span></span>
2. <span data-ttu-id="11869-108">Erstellen und Bereitstellen Des Webdiensts (während der Entwicklung verwenden Sie einen Tunneldienst wie ngrok, um ihn lokal auszuführen)</span><span class="sxs-lookup"><span data-stu-id="11869-108">Create and deploy your web service (while developing use a tunneling service like ngrok to run it locally)</span></span>
3. <span data-ttu-id="11869-109">Registrieren Ihres Webdiensts bei Bot Framework</span><span class="sxs-lookup"><span data-stu-id="11869-109">Register your web service with the Bot Framework</span></span>
4. <span data-ttu-id="11869-110">Erstellen Ihres App-Pakets</span><span class="sxs-lookup"><span data-stu-id="11869-110">Create your app package</span></span>
5. <span data-ttu-id="11869-111">Hochladen Ihres Pakets in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11869-111">Upload your package to Microsoft Teams</span></span>

<span data-ttu-id="11869-112">Das Erstellen Ihres Webdiensts, das Erstellen Ihres App-Pakets und das Registrieren Ihres Webdiensts beim Bot Framework können in beliebiger Reihenfolge erfolgen.</span><span class="sxs-lookup"><span data-stu-id="11869-112">Creating your web service, creating your app package, and registering your web service with the Bot Framework can be done in any order.</span></span> <span data-ttu-id="11869-113">Da diese drei Teile so miteinander verschachtelt sind, müssen Sie unabhängig davon, in welcher Reihenfolge Sie sie ausführen, zurückkehren, um die anderen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="11869-113">Because those three pieces are so intertwined, no matter which order you do them in you'll need return to update the others.</span></span> <span data-ttu-id="11869-114">Ihre Registrierung benötigt den Messaging-Endpunkt von Ihrem bereitgestellten Webdienst, und Ihr Webdienst benötigt die ID und das Kennwort, die aus Ihrer Registrierung erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="11869-114">Your registration needs the messaging endpoint from your deployed web service, and your web service needs the Id and password created from your registration.</span></span> <span data-ttu-id="11869-115">Ihr App-Manifest benötigt auch diese ID, um Teams mit Ihrem Webdienst zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="11869-115">Your app manifest also needs that Id to connect Teams to your web service.</span></span>

<span data-ttu-id="11869-116">Während Sie Ihre Messaging-Erweiterung erstellen, wechseln Sie regelmäßig zwischen dem Ändern Des App-Manifests und der Bereitstellung von Code für Ihren Webdienst.</span><span class="sxs-lookup"><span data-stu-id="11869-116">As you're building your messaging extension, you'll regularly be moving between changing your app manifest, and deploying code to your web service.</span></span> <span data-ttu-id="11869-117">Beachten Sie bei der Arbeit mit dem App-Manifest, dass Sie die JSON-Datei manuell bearbeiten oder Änderungen über App Studio vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="11869-117">When working with the app manifest, keep in mind that you can either manually manipulate the JSON file, or make changes through App Studio.</span></span> <span data-ttu-id="11869-118">In beiden Fällen müssen Sie Ihre App in Teams erneut bereitstellen (hochladen), wenn Sie eine Änderung am Manifest vornehmen. Dies ist jedoch nicht erforderlich, wenn Sie Änderungen an Ihrem Webdienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="11869-118">Either way, you'll need to re-deploy (upload) your app in Teams when you make a change to the manifest, but there's no need to do so when you deploy changes to your web service.</span></span>

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a><span data-ttu-id="11869-119">Erstellen Ihres Webdiensts</span><span class="sxs-lookup"><span data-stu-id="11869-119">Create your web service</span></span>

<span data-ttu-id="11869-120">Das Herzstück Ihrer Messaging-Erweiterung ist Ihr Webdienst.</span><span class="sxs-lookup"><span data-stu-id="11869-120">The heart of your messaging extension is your web service.</span></span> <span data-ttu-id="11869-121">Es wird eine einzelne Route definiert, in der `/api/messages` Regel, um alle Anforderungen zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="11869-121">It will define a single route, typically `/api/messages`, to receive all requests on.</span></span> <span data-ttu-id="11869-122">Wenn Sie von Grund auf neu beginnen, stehen Ihnen einige Optionen zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="11869-122">If you're getting started from scratch, you have a few options to choose from.</span></span>

* <span data-ttu-id="11869-123">Verwenden Sie eines unserer [Schnellstartlernprogramme,](#learn-more) die Sie durch die Erstellung Ihres Webdiensts führen.</span><span class="sxs-lookup"><span data-stu-id="11869-123">Use one of our [quickstarts](#learn-more) tutorials that will guide you through the creation of your web service.</span></span>
* <span data-ttu-id="11869-124">Wählen Sie eines der Beispiele für Messaging-Erweiterungen aus, die im [Bot Framework-Beispiel-Repository](https://github.com/Microsoft/BotBuilder-Samples) verfügbar sind, um zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="11869-124">Choose one of the messaging extension samples available in the [Bot Framework sample repository](https://github.com/Microsoft/BotBuilder-Samples) to start from.</span></span>
* <span data-ttu-id="11869-125">Wenn Sie JavaScript verwenden, verwenden Sie den [Yeoman-Generator für Microsoft Teams](https://github.com/OfficeDev/generator-teams) zum Erstellen eines Gerüsts für Ihre Teams-App, einschließlich Ihres Webdiensts.</span><span class="sxs-lookup"><span data-stu-id="11869-125">If you're using JavaScript, use the [Yeoman generator for Microsoft Teams](https://github.com/OfficeDev/generator-teams) to scaffold your Teams app, including your web service.</span></span>
* <span data-ttu-id="11869-126">Erstellen Sie Ihren Webdienst von Grund auf neu.</span><span class="sxs-lookup"><span data-stu-id="11869-126">Create your web service from scratch.</span></span> <span data-ttu-id="11869-127">Sie können das Bot Framework-SDK für Ihre Sprache hinzufügen oder direkt mit den JSON-Nutzlasten arbeiten.</span><span class="sxs-lookup"><span data-stu-id="11869-127">You can choose to add the Bot Framework SDK for your language, or you can work directly with the JSON payloads.</span></span>

## <a name="register-your-web-service-with-the-bot-framework"></a><span data-ttu-id="11869-128">Registrieren Ihres Webdiensts bei Bot Framework</span><span class="sxs-lookup"><span data-stu-id="11869-128">Register your web service with the Bot Framework</span></span>

<span data-ttu-id="11869-129">Messaging-Erweiterungen nutzen das Messaging-Schema und das sichere Kommunikationsprotokoll des Bot-Frameworks. Wenn Sie noch nicht über einen verfügen, müssen Sie Ihren Webdienst im Bot Framework registrieren.</span><span class="sxs-lookup"><span data-stu-id="11869-129">Messaging extensions take advantage of the Bot Framework's messaging schema and secure communication protocol; if you don't already have one you'll need to register your web service on the Bot Framework.</span></span> <span data-ttu-id="11869-130">Die Microsoft App-ID (wir bezeichnen dies als Ihre Bot-ID innerhalb von Teams, um sie von anderen App-IDs zu identifizieren, mit denen Sie möglicherweise arbeiten), und der Messaging-Endpunkt, mit dem Sie sich beim Bot Framework registrieren, wird in Ihrer Messaging-Erweiterung verwendet, um Anforderungen zu empfangen und darauf zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="11869-130">The Microsoft App Id (we'll refer to this as your Bot Id from inside of Teams, to identify it from other App Id's you might be working with) and the messaging endpoint your register with the Bot Framework will be used in your messaging extension to receive and respond to requests.</span></span> <span data-ttu-id="11869-131">Wenn Sie eine vorhandene Registrierung verwenden, stellen Sie sicher, dass Sie [den Microsoft Teams Kanal aktivieren.](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="11869-131">If you're using an existing registration, make sure you [enable the Microsoft Teams channel](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<span data-ttu-id="11869-132">Wenn Sie eine der Schnellstarts befolgen oder mit einem der verfügbaren Beispiele beginnen, werden Sie durch die Registrierung Ihres Webdiensts geführt.</span><span class="sxs-lookup"><span data-stu-id="11869-132">If you follow one of the quickstarts or start from one of the available samples you'll be guided through registering your web service.</span></span> <span data-ttu-id="11869-133">Wenn Sie Ihren Dienst manuell registrieren möchten, haben Sie drei Möglichkeiten, dies zu tun.</span><span class="sxs-lookup"><span data-stu-id="11869-133">If you want to manually register your service you have three options to do so.</span></span> <span data-ttu-id="11869-134">Wenn Sie sich für die Registrierung entscheiden, ohne ein Azure-Abonnement zu verwenden, können Sie den vereinfachten OAuth-Authentifizierungsfluss des Bot Frameworks nicht nutzen.</span><span class="sxs-lookup"><span data-stu-id="11869-134">If you choose to register without using an Azure subscription you will not be able to take advantage of the simplified OAuth authentication flow provided by the Bot Framework.</span></span> <span data-ttu-id="11869-135">Sie können Ihre Registrierung nach der Erstellung zu Azure migrieren.</span><span class="sxs-lookup"><span data-stu-id="11869-135">You will be able to migrate your registration to Azure after creation.</span></span>

* <span data-ttu-id="11869-136">Wenn Sie über ein Azure-Abonnement verfügen (oder ein neues erstellen möchten), können Sie Ihren Webdienst manuell über das Azure-Portal registrieren.</span><span class="sxs-lookup"><span data-stu-id="11869-136">If you have an Azure subscription (or want to create a new one), you can register your web service manually using the Azure Portal.</span></span> <span data-ttu-id="11869-137">Erstellen Sie eine Ressource "Bot Channels Registration".</span><span class="sxs-lookup"><span data-stu-id="11869-137">Create a "Bot Channels Registration" resource.</span></span> <span data-ttu-id="11869-138">Sie können das preisfreie Preisniveau auswählen, da Nachrichten aus Microsoft Teams nicht auf Die Gesamtzahl der zulässigen Nachrichten pro Monat angerechnet werden.</span><span class="sxs-lookup"><span data-stu-id="11869-138">You can choose the free pricing tier, as messages from Microsoft Teams do not count towards your total allowable messages per month.</span></span>
* <span data-ttu-id="11869-139">Wenn Sie kein Azure-Abonnement verwenden möchten, können Sie das [Legacyregistrierungsportal](https://dev.botframework.com/bots/new)verwenden.</span><span class="sxs-lookup"><span data-stu-id="11869-139">If you do not wish to use an Azure subscription, you can use the [legacy registration portal](https://dev.botframework.com/bots/new).</span></span>
* <span data-ttu-id="11869-140">App Studio kann Ihnen auch dabei helfen, Ihren Webdienst (Bot) zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="11869-140">App Studio can also help you register your web service (bot).</span></span> <span data-ttu-id="11869-141">Über App Studio registrierte Webdienste sind in Azure nicht registriert.</span><span class="sxs-lookup"><span data-stu-id="11869-141">Web services registered through App Studio are not registered in Azure.</span></span> <span data-ttu-id="11869-142">Sie können das [Legacyportal](https://dev.botframework.com/bots) verwenden, um Ihre Registrierungen anzuzeigen, zu verwalten und zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="11869-142">You can use the [legacy portal](https://dev.botframework.com/bots) to view, manage, and migrate your registrations.</span></span>

## <a name="create-your-app-manifest"></a><span data-ttu-id="11869-143">Erstellen des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="11869-143">Create your app manifest</span></span>

<span data-ttu-id="11869-144">Sie können Ihr App-Manifest entweder in App Studio oder manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="11869-144">You can either use App Studio to help you create your app manifest, or create it manually.</span></span>

### <a name="create-your-app-manifest-using-app-studio"></a><span data-ttu-id="11869-145">Erstellen Ihres App-Manifests mit App Studio</span><span class="sxs-lookup"><span data-stu-id="11869-145">Create your app manifest using App Studio</span></span>

<span data-ttu-id="11869-146">Sie können die App Studio-App innerhalb des Microsoft Teams-Clients verwenden, um Ihr App-Manifest zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="11869-146">You can use the App Studio app from within the Microsoft Teams client to help create your app manifest.</span></span>

1. <span data-ttu-id="11869-147">Öffnen Sie App Studio im Teams-Client aus dem **...**-Überlaufmenü auf der linken Navigationsleiste.</span><span class="sxs-lookup"><span data-stu-id="11869-147">In the Teams client, open App Studio from the **...** overflow menu on the left navigation rail.</span></span> <span data-ttu-id="11869-148">Wenn es noch nicht installiert ist, können Sie dies tun, indem Sie danach suchen.</span><span class="sxs-lookup"><span data-stu-id="11869-148">If it isn't already installed, you can do so by searching for it.</span></span>
2. <span data-ttu-id="11869-149">Wählen Sie auf der Registerkarte **"Manifest-Editor"** die Option **"Neue App erstellen"** aus (oder wenn Sie einer vorhandenen App eine Messaging-Erweiterung hinzufügen, können Sie Ihr App-Paket importieren).</span><span class="sxs-lookup"><span data-stu-id="11869-149">On the **Manifest editor** tab select **Create a new app** (or if you're adding a messaging extension to an existing app, you can import your app package)</span></span>
3. <span data-ttu-id="11869-150">Fügen Sie Ihre App-Details hinzu (in der [Manifestschemadefinition](~/resources/schema/manifest-schema.md) finden Sie die vollständigen Beschreibungen der einzelnen Felder).</span><span class="sxs-lookup"><span data-stu-id="11869-150">Add your app details (see [manifest schema definition](~/resources/schema/manifest-schema.md) for full descriptions of each field).</span></span>
4. <span data-ttu-id="11869-151">Klicken Sie auf der Registerkarte **"Messaging-Erweiterungen"** auf die Schaltfläche **"Setup".**</span><span class="sxs-lookup"><span data-stu-id="11869-151">On the **Messaging extensions** tab click the **Setup** button.</span></span>
5. <span data-ttu-id="11869-152">Sie können entweder einen neuen Webdienst (Bot) für die Verwendung Ihrer Messaging-Erweiterung erstellen, oder wenn Sie hier bereits eine Auswahl registriert bzw. diesen hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="11869-152">You can either create a new web service (bot) for your messaging extension to use, or if you've already registered one select/add it here.</span></span>
6. <span data-ttu-id="11869-153">Aktualisieren Sie Ihre Bot-Endpunktadresse bei Bedarf so, dass Sie auf Ihren Bot verweist.</span><span class="sxs-lookup"><span data-stu-id="11869-153">If necessary, update your bot endpoint address to point to your bot.</span></span> <span data-ttu-id="11869-154">Dies sollte ungefähr so aussehen: `https://someplace.com/api/messages`.</span><span class="sxs-lookup"><span data-stu-id="11869-154">It should look something like `https://someplace.com/api/messages`.</span></span>
7. <span data-ttu-id="11869-155">Die Schaltfläche **"Hinzufügen"** im Abschnitt **"Befehl"** führt Sie durch das Hinzufügen von Befehlen zu Ihrer Messaging-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="11869-155">The **Add** button in the **Command** section will guide you through adding commands to your messaging extension.</span></span> <span data-ttu-id="11869-156">Links zu weiteren Informationen zum Hinzufügen von Befehlen finden Sie im Abschnitt ["Weitere Informationen".](#learn-more)</span><span class="sxs-lookup"><span data-stu-id="11869-156">See the [Learn more](#learn-more) section for links to more information on adding commands.</span></span> <span data-ttu-id="11869-157">Denken Sie daran, dass Sie bis zu 10 Befehle für Ihre Messaging-Erweiterung definieren können.</span><span class="sxs-lookup"><span data-stu-id="11869-157">Remember you can define up to 10 commands for your messaging extension.</span></span>
8. <span data-ttu-id="11869-158">Im Abschnitt **"Nachrichtenhandler"** können Sie eine Domäne hinzufügen, für die Ihr Messaging ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="11869-158">The **Message Handlers** section allows you to add a domain that your messaging will trigger on.</span></span> <span data-ttu-id="11869-159">Weitere Informationen finden Sie [unter "Verbreitung von Links".](~/messaging-extensions/how-to/link-unfurling.md)</span><span class="sxs-lookup"><span data-stu-id="11869-159">See [link unfurling](~/messaging-extensions/how-to/link-unfurling.md) for more information.</span></span>

<span data-ttu-id="11869-160">Über die Registerkarte **"Fertig stellen => Testen und Verteilen"** können Sie Ihr App-Paket (das Ihr App-Manifest sowie Ihre App-Symbole enthält) **herunterladen** oder das Paket **installieren.**</span><span class="sxs-lookup"><span data-stu-id="11869-160">From the **Finish => Test and distribute** tab you can **Download** your app package (which includes your app manifest as well as your app icons), or **Install** the package.</span></span>

### <a name="create-your-app-manifest-manually"></a><span data-ttu-id="11869-161">Manuelles Erstellen des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="11869-161">Create your app manifest manually</span></span>

<span data-ttu-id="11869-162">Wie bei Bots und Registerkarten aktualisieren Sie das [App-Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App, um die Eigenschaften der Messaging-Erweiterung einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="11869-162">As with bots and tabs, you update the [app manifest](~/resources/schema/manifest-schema.md#composeextensions) of your app to include the messaging extension properties.</span></span> <span data-ttu-id="11869-163">Diese Eigenschaften steuern, wie Ihre Messaging-Erweiterung im Microsoft Teams Client angezeigt wird und wie sie sich verhält.</span><span class="sxs-lookup"><span data-stu-id="11869-163">These properties govern how your messaging extension appears and behaves in the Microsoft Teams client.</span></span> <span data-ttu-id="11869-164">Messaging-Erweiterungen werden ab Version 1.0 des Manifests unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11869-164">Messaging extensions are supported beginning with v1.0 of the manifest.</span></span>

#### <a name="declare-your-messaging-extension"></a><span data-ttu-id="11869-165">Deklarieren Der Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="11869-165">Declare your messaging extension</span></span>

<span data-ttu-id="11869-166">Um eine Messaging-Erweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur auf oberster Ebene in Ihr App-Manifest mit der `composeExtensions` Eigenschaft ein.</span><span class="sxs-lookup"><span data-stu-id="11869-166">To add a messaging extension, include a new top-level JSON structure in your app manifest with the `composeExtensions` property.</span></span> <span data-ttu-id="11869-167">Sie erstellen eine einzelne Messaging-Erweiterung für Ihre App mit bis zu 10 Befehlen.</span><span class="sxs-lookup"><span data-stu-id="11869-167">You create a single messaging extension for your app, with up to 10 commands.</span></span>

> [!NOTE]
> <span data-ttu-id="11869-168">Das Manifest bezieht sich auf Messaging-Erweiterungen als `composeExtensions` .</span><span class="sxs-lookup"><span data-stu-id="11869-168">The manifest refers to messaging extensions as `composeExtensions`.</span></span> <span data-ttu-id="11869-169">Dies dient zur Aufrechterhaltung der Abwärtskompatibilität.</span><span class="sxs-lookup"><span data-stu-id="11869-169">This is to maintain backward compatibility.</span></span>

<span data-ttu-id="11869-170">Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="11869-170">The extension definition is an object that has the following structure:</span></span>

| <span data-ttu-id="11869-171">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="11869-171">Property name</span></span> | <span data-ttu-id="11869-172">Zweck</span><span class="sxs-lookup"><span data-stu-id="11869-172">Purpose</span></span> | <span data-ttu-id="11869-173">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="11869-173">Required?</span></span> |
|---|---|---|
| `botId` | <span data-ttu-id="11869-174">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="11869-174">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="11869-175">Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="11869-175">This should typically be the same as the ID for your overall Teams app.</span></span> | <span data-ttu-id="11869-176">Ja</span><span class="sxs-lookup"><span data-stu-id="11869-176">Yes</span></span> |
| `canUpdateConfiguration` | <span data-ttu-id="11869-177">Aktiviert **Einstellungen** Menüelement.</span><span class="sxs-lookup"><span data-stu-id="11869-177">Enables **Settings** menu item.</span></span> | <span data-ttu-id="11869-178">Nein</span><span class="sxs-lookup"><span data-stu-id="11869-178">No</span></span> |
| `commands` | <span data-ttu-id="11869-179">Array von Befehlen, die von dieser Messaging-Erweiterung unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="11869-179">Array of commands that this messaging extension supports.</span></span> <span data-ttu-id="11869-180">Sie sind auf 10 Befehle beschränkt.</span><span class="sxs-lookup"><span data-stu-id="11869-180">You are limited to 10 commands.</span></span> | <span data-ttu-id="11869-181">Ja</span><span class="sxs-lookup"><span data-stu-id="11869-181">Yes</span></span> |

#### <a name="define-your-commands"></a><span data-ttu-id="11869-182">Definieren von Befehlen</span><span class="sxs-lookup"><span data-stu-id="11869-182">Define your commands</span></span>

<span data-ttu-id="11869-183">Ihre Messaging-Erweiterung sollte einen oder mehrere Befehle deklarieren, die definieren, wo Ihre Benutzer Ihre Messaging-Erweiterung auslösen können, und die Art der Interaktion.</span><span class="sxs-lookup"><span data-stu-id="11869-183">Your messaging extension should declare one or more commands, which define where your users can trigger your messaging extension, and the type of interaction.</span></span> <span data-ttu-id="11869-184">Weitere Informationen zu Messaging-Erweiterungsbefehlen [finden Sie](#learn-more) hier.</span><span class="sxs-lookup"><span data-stu-id="11869-184">See [learn more](#learn-more) for more information on messaging extension commands.</span></span>

#### <a name="simple-manifest-example"></a><span data-ttu-id="11869-185">Beispiel für ein einfaches Manifest</span><span class="sxs-lookup"><span data-stu-id="11869-185">Simple manifest example</span></span>

<span data-ttu-id="11869-186">Das folgende Beispiel ist ein einfaches Messaging-Erweiterungsobjekt im App-Manifest mit einem Suchbefehl.</span><span class="sxs-lookup"><span data-stu-id="11869-186">The following example is a simple messaging extension object in the app manifest with a search command.</span></span> <span data-ttu-id="11869-187">Hierbei handelt es sich nicht um die komplette App-Manifestdatei, sondern nur um den Teil der Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="11869-187">This is not the entire app manifest file, just the part specific to messaging extensions.</span></span> <span data-ttu-id="11869-188">Ein vollständiges Beispiel finden Sie im [App-Manifestschema.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="11869-188">See [app manifest schema](~/resources/schema/manifest-schema.md) for a complete example.</span></span>

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

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="11869-189">Beispiel für ein vollständiges App-Manifest</span><span class="sxs-lookup"><span data-stu-id="11869-189">Complete app manifest example</span></span>

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

## <a name="add-your-invoke-message-handlers"></a><span data-ttu-id="11869-190">Hinzufügen der Aufrufnachrichtenhandler</span><span class="sxs-lookup"><span data-stu-id="11869-190">Add your invoke message handlers</span></span>

<span data-ttu-id="11869-191">Wenn Ihre Benutzer Ihre Messaging-Erweiterung auslösen, müssen Sie die anfängliche Aufrufnachricht verarbeiten, einige Informationen vom Benutzer sammeln und dann diese Informationen verarbeiten und entsprechend antworten.</span><span class="sxs-lookup"><span data-stu-id="11869-191">When your users trigger your messaging extension you'll need to handle the initial invoke message, collect some information from the user, then process that information and respond appropriately.</span></span> <span data-ttu-id="11869-192">Dazu müssen Sie zuerst entscheiden, welche Art von Befehlen Sie Ihrer Messaging-Erweiterung hinzufügen möchten, und entweder [Aktionsbefehle oder](~/messaging-extensions/how-to/action-commands/define-action-command.md) [Suchbefehle hinzufügen.](~/messaging-extensions/how-to/search-commands/define-search-command.md)</span><span class="sxs-lookup"><span data-stu-id="11869-192">To do that, you'll first need to decide what kind of commands you want to add to your messaging extension and either [add an action commands](~/messaging-extensions/how-to/action-commands/define-action-command.md) or [add a search commands](~/messaging-extensions/how-to/search-commands/define-search-command.md).</span></span>

## <a name="messaging-extensions-in-teams-meetings"></a><span data-ttu-id="11869-193">Messaging-Erweiterungen in Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="11869-193">Messaging extensions in Teams meetings</span></span>

> [!NOTE]
> <span data-ttu-id="11869-194">Wenn in einem Besprechungs- oder Gruppenchat Verbundbenutzer in der Liste enthalten sind, unterdrückt Teams den Zugriff auf Messaging-Erweiterungen für alle Benutzer, einschließlich des Organisators.</span><span class="sxs-lookup"><span data-stu-id="11869-194">If a meeting or group chat has federated users in the roster, Teams suppresses access to messaging extensions for all users, including the organizer.</span></span>

<span data-ttu-id="11869-195">Sobald eine Besprechung beginnt, können Teams Teilnehmer während eines Liveanrufs direkt mit Ihrer Messaging-Erweiterung interagieren.</span><span class="sxs-lookup"><span data-stu-id="11869-195">Once a meeting begins, Teams participants can interact directly with your messaging extension during a live call.</span></span> <span data-ttu-id="11869-196">Berücksichtigen Sie beim Erstellen Ihrer Messaging-Erweiterung in Besprechungen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="11869-196">Consider the following when building your in-meeting messaging extension:</span></span>

1. <span data-ttu-id="11869-197">**Location**.</span><span class="sxs-lookup"><span data-stu-id="11869-197">**Location**.</span></span> <span data-ttu-id="11869-198">Ihre Messaging-Erweiterung kann über den Bereich zum Verfassen von Nachrichten, das Befehlsfeld oder @mentioned im Besprechungschat aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="11869-198">Your messaging extension can be invoked from the compose message area, the command box, or @mentioned in the meeting chat.</span></span>

1. <span data-ttu-id="11869-199">**Metadaten**.</span><span class="sxs-lookup"><span data-stu-id="11869-199">**Metadata**.</span></span> <span data-ttu-id="11869-200">Wenn Ihre Messaging-Erweiterung aufgerufen wird, kann sie den Benutzer und Mandanten von `userId` und `tenantId` identifizieren.</span><span class="sxs-lookup"><span data-stu-id="11869-200">When your messaging extension is invoked it can identify the user and tenant from `userId` and `tenantId`.</span></span> <span data-ttu-id="11869-201">Die `meetingId`kann als Teil des Objekts `channelData` gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="11869-201">The `meetingId` can be found as part of the `channelData` object.</span></span> <span data-ttu-id="11869-202">Ihre App kann die `userId` `meetingId`  UND für die `GetParticipant` API-Anforderung verwenden, um Benutzerrollen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="11869-202">Your app can use the `userId` and `meetingId`  for the `GetParticipant` API request to retrieve user roles.</span></span>

1. <span data-ttu-id="11869-203">**Befehlstyp**.</span><span class="sxs-lookup"><span data-stu-id="11869-203">**Command type**.</span></span> <span data-ttu-id="11869-204">Wenn Ihre Nachrichtenerweiterung [aktionsbasierte Befehle](../messaging-extensions/what-are-messaging-extensions.md#action-commands)verwendet, sollte sie der Single [Sign-On-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md) der Registerkarten folgen.</span><span class="sxs-lookup"><span data-stu-id="11869-204">If your message extension uses [action-based commands](../messaging-extensions/what-are-messaging-extensions.md#action-commands), it should follow tabs [single sign-on](../tabs/how-to/authentication/auth-aad-sso.md) authentication.</span></span>

1. <span data-ttu-id="11869-205">**Benutzererfahrung**.</span><span class="sxs-lookup"><span data-stu-id="11869-205">**User experience**.</span></span> <span data-ttu-id="11869-206">Die Messaging-Erweiterung sollte genauso aussehen und sich verhalten wie außerhalb einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="11869-206">You messaging extension should look and behave the same as it would outside a meeting.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11869-207">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="11869-207">Next steps</span></span>

* [<span data-ttu-id="11869-208">Erstellen von Aktionsbefehlen</span><span class="sxs-lookup"><span data-stu-id="11869-208">Create action commands</span></span>](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [<span data-ttu-id="11869-209">Erstellen von Suchbefehlen</span><span class="sxs-lookup"><span data-stu-id="11869-209">Create search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [<span data-ttu-id="11869-210">Verbreiten von Links</span><span class="sxs-lookup"><span data-stu-id="11869-210">Link unfurling</span></span>](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a><span data-ttu-id="11869-211">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="11869-211">Learn more</span></span>

<span data-ttu-id="11869-212">Probieren Sie es in einer Schnellstartanleitung aus:</span><span class="sxs-lookup"><span data-stu-id="11869-212">Try it out in a quickstart:</span></span>

* <span data-ttu-id="11869-213">Schnellstarts für C #</span><span class="sxs-lookup"><span data-stu-id="11869-213">Quickstarts for C#</span></span>
  * [<span data-ttu-id="11869-214">Messaging-Erweiterung mit aktionsbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="11869-214">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [<span data-ttu-id="11869-215">Messaging-Erweiterung mit suchbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="11869-215">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* <span data-ttu-id="11869-216">Schnellstarts für JavaScript</span><span class="sxs-lookup"><span data-stu-id="11869-216">Quickstarts for JavaScript</span></span>
  * [<span data-ttu-id="11869-217">Messaging-Erweiterung mit aktionsbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="11869-217">Messaging extension with action-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [<span data-ttu-id="11869-218">Messaging-Erweiterung mit suchbasierten Befehlen</span><span class="sxs-lookup"><span data-stu-id="11869-218">Messaging extension with search-based commands</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

<span data-ttu-id="11869-219">Erfahren Sie mehr über Teams Entwicklungskonzepten:</span><span class="sxs-lookup"><span data-stu-id="11869-219">Learn more about Teams development concepts:</span></span>

* [<span data-ttu-id="11869-220">Grundlegendes zu Teams App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="11869-220">Understand Teams app capabilities</span></span>](../concepts/capabilities-overview.md)
* [<span data-ttu-id="11869-221">Was sind Messaging-Erweiterungen?</span><span class="sxs-lookup"><span data-stu-id="11869-221">What are messaging extensions?</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
