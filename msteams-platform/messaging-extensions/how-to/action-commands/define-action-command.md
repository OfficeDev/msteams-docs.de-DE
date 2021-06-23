---
title: Definieren von Aktionsbefehlen für Messaging-Erweiterungen
author: surbhigupta
description: Eine Übersicht über Aktionsbefehle für Messaging-Erweiterungen
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: b4420247d3a0c1116bd1aed09fa2edccf18ae902
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068930"
---
# <a name="define-messaging-extension-action-commands"></a><span data-ttu-id="ef1be-103">Definieren von Aktionsbefehlen für Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="ef1be-103">Define messaging extension action commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="ef1be-104">Mit Aktionsbefehlen können Sie Ihren Benutzern ein modales Popup anzeigen, das als Aufgabenmodul in Teams bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ef1be-104">Action commands allow you to present your users with a modal popup called a task module in Teams.</span></span> <span data-ttu-id="ef1be-105">Das Aufgabenmodul sammelt oder zeigt Informationen an, verarbeitet die Interaktion und sendet die Informationen zurück an Teams.</span><span class="sxs-lookup"><span data-stu-id="ef1be-105">The task module collects or displays information, processes the interaction and sends the information back to Teams.</span></span> <span data-ttu-id="ef1be-106">Dieses Dokument führt Sie durch die Auswahl von Aktionsbefehlsaufforderungsspeicherorten, das Erstellen Ihres Aufgabenmoduls, das Senden einer endgültigen Nachricht oder Karte, das Erstellen eines Aktionsbefehls mit App Studio oder das manuelle Erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-106">This document guides you on how to select action command invoke locations, create your task module, send final message, or card, create action command using app studio, or create it manually.</span></span> 

<span data-ttu-id="ef1be-107">Bevor Sie den Aktionsbefehl erstellen, müssen Sie die folgenden Faktoren festlegen:</span><span class="sxs-lookup"><span data-stu-id="ef1be-107">Before creating the action command you must decide the following factors:</span></span>

1. [<span data-ttu-id="ef1be-108">Wo kann der Aktionsbefehl ausgelöst werden?</span><span class="sxs-lookup"><span data-stu-id="ef1be-108">Where can the action command be triggered from?</span></span>](#select-action-command-invoke-locations)
1. [<span data-ttu-id="ef1be-109">Wie wird das Aufgabenmodul erstellt?</span><span class="sxs-lookup"><span data-stu-id="ef1be-109">How will the task module be created?</span></span>](#select-how-to-create-your-task-module)
1. [<span data-ttu-id="ef1be-110">Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, die der Benutzer übermitteln kann?</span><span class="sxs-lookup"><span data-stu-id="ef1be-110">Will the final message or card be sent to the channel from a bot, or will the message or card be inserted into the compose message area for the user to submit?</span></span>](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a><span data-ttu-id="ef1be-111">Auswählen von Aktionsbefehlsaufforderungsspeicherorten</span><span class="sxs-lookup"><span data-stu-id="ef1be-111">Select action command invoke locations</span></span>

<span data-ttu-id="ef1be-112">Zunächst müssen Sie den Speicherort festlegen, an dem der Aktionsbefehl aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="ef1be-112">First, you must decide the location from where your action command must be invoked.</span></span> <span data-ttu-id="ef1be-113">Durch Angeben des `context` Befehls im App-Manifest kann der Befehl von einem oder mehreren der folgenden Speicherorte aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="ef1be-113">By specifying the `context` in your app manifest, your command can be invoked from one or more of the following locations:</span></span>

* <span data-ttu-id="ef1be-114">Bereich zum Verfassen von Nachrichten: Die Schaltflächen unten im Bereich zum Verfassen von Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="ef1be-114">Compose message area: The buttons at the bottom of the compose message area.</span></span>
* <span data-ttu-id="ef1be-115">Befehlsfeld: Durch @mentioning Ihre App im Befehlsfeld.</span><span class="sxs-lookup"><span data-stu-id="ef1be-115">Command box: By @mentioning your app in the command box.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="ef1be-116">Wenn die Messaging-Erweiterung über das Befehlsfeld aufgerufen wird, können Sie nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="ef1be-116">If messaging extension is invoked from the command box, you cannot respond with a bot message inserted directly into the conversation.</span></span>

* <span data-ttu-id="ef1be-117">Nachricht: Direkt aus einer vorhandenen Nachricht über das `...` Überlaufmenü einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="ef1be-117">Message: Directly from an existing message through the `...` overflow menu on a message.</span></span> 
    > [!NOTE] 
    > <span data-ttu-id="ef1be-118">Der anfängliche Aufruf für Ihren Bot enthält ein JSON-Objekt, das die Nachricht enthält, aus der er aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="ef1be-118">The initial invoke to your bot includes a JSON object containing the message from which it was invoked.</span></span> <span data-ttu-id="ef1be-119">Sie können die Nachricht verarbeiten, bevor Sie sie mit einem Aufgabenmodul präsentieren.</span><span class="sxs-lookup"><span data-stu-id="ef1be-119">You can process the message before presenting them with a task module.</span></span>

<span data-ttu-id="ef1be-120">In der folgenden Abbildung werden die Speicherorte angezeigt, an denen der Aktionsbefehl aufgerufen wird:</span><span class="sxs-lookup"><span data-stu-id="ef1be-120">The following image displays the locations from where action command is invoked:</span></span>

![Aufrufen von Speicherorten des Aktionsbefehls](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a><span data-ttu-id="ef1be-122">Auswählen, wie Das Aufgabenmodul erstellt werden soll</span><span class="sxs-lookup"><span data-stu-id="ef1be-122">Select how to create your task module</span></span>

<span data-ttu-id="ef1be-123">Sie müssen nicht nur auswählen, von wo aus Der Befehl aufgerufen werden kann, sie müssen auch auswählen, wie das Formular im Aufgabenmodul für Ihre Benutzer aufgefüllt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef1be-123">In addition to selecting where your command can be invoked from, you must also select how to populate the form in the task module for your users.</span></span> <span data-ttu-id="ef1be-124">Sie haben die folgenden drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:</span><span class="sxs-lookup"><span data-stu-id="ef1be-124">You have the following three options for creating the form that is rendered inside the task module:</span></span>   

* <span data-ttu-id="ef1be-125">**Statische Liste von Parametern:** Dies ist die einfachste Methode.</span><span class="sxs-lookup"><span data-stu-id="ef1be-125">**Static list of parameters**: This is the simplest method.</span></span> <span data-ttu-id="ef1be-126">Sie können eine Liste der Parameter in Ihrem App-Manifest definieren, die vom Teams Client gerendert wird, die Formatierung kann in diesem Fall jedoch nicht gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="ef1be-126">You can define a list of parameters in your app manifest the Teams client renders, but cannot control the formatting in this case.</span></span>
* <span data-ttu-id="ef1be-127">**Adaptive Karte:** Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie jedoch weiterhin auf die verfügbaren Steuerelemente und Formatierungsoptionen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="ef1be-127">**Adaptive Card**:  You can select to use an Adaptive Card, which provides greater control over the UI, but still limits you on the available controls and formatting options.</span></span>
* <span data-ttu-id="ef1be-128">**Eingebettete Webansicht:** Sie können eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten, um eine vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente zu haben.</span><span class="sxs-lookup"><span data-stu-id="ef1be-128">**Embedded web view**: You can select to embed a custom web view in the task module to have a complete control over the UI and controls.</span></span> 

<span data-ttu-id="ef1be-129">Wenn Sie das Aufgabenmodul mit einer statischen Liste von Parametern erstellen und wenn der Benutzer das Aufgabenmodul sendet, wird die Messaging-Erweiterung aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-129">If you select to create the task module with a static list of parameters and when the user submits the task module, the messaging extension is called.</span></span> <span data-ttu-id="ef1be-130">Bei Verwendung einer eingebetteten Webansicht oder einer adaptiven Karte muss Ihre Messaging-Erweiterung ein anfängliches Aufrufereignis des Benutzers verarbeiten, das Aufgabenmodul erstellen und an den Client zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="ef1be-130">When using an embedded web view or an Adaptive Card, your messaging extension must handle an initial invoke event from the user, create the task module, and return it back to the client.</span></span>

## <a name="select-how-the-final-message-is-sent"></a><span data-ttu-id="ef1be-131">Auswählen, wie die endgültige Nachricht gesendet wird</span><span class="sxs-lookup"><span data-stu-id="ef1be-131">Select how the final message is sent</span></span>

<span data-ttu-id="ef1be-132">In den meisten Fällen führt der Aktionsbefehl zu einer Karte, die in das Feld zum Verfassen von Nachrichten eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ef1be-132">In most cases, the action command results in a card inserted into the compose message box.</span></span> <span data-ttu-id="ef1be-133">Der Benutzer kann es in den Kanal oder Chat senden.</span><span class="sxs-lookup"><span data-stu-id="ef1be-133">The user can send it into the channel or chat.</span></span> <span data-ttu-id="ef1be-134">In diesem Fall stammt die Nachricht vom Benutzer, und der Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ef1be-134">In this case, the message comes from the user, and the bot cannot edit or update the card further.</span></span>

<span data-ttu-id="ef1be-135">Wenn die Messaging-Erweiterung aus dem Feld zum Verfassen oder direkt aus einer Nachricht aufgerufen wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-135">If the messaging extension is invoked from the compose box or directly from a message, your web service can insert the final response directly into the channel or chat.</span></span> <span data-ttu-id="ef1be-136">In diesem Fall stammt die adaptive Karte vom Bot, der Bot aktualisiert sie und antwortet bei Bedarf auf den Unterhaltungsthread.</span><span class="sxs-lookup"><span data-stu-id="ef1be-136">In this case, the Adaptive Card comes from the bot, the bot updates it, and replies to the conversation thread if needed.</span></span> <span data-ttu-id="ef1be-137">Sie müssen das `bot` Objekt dem App-Manifest mit derselben ID hinzufügen und die entsprechenden Bereiche definieren.</span><span class="sxs-lookup"><span data-stu-id="ef1be-137">You must add the `bot` object to the app manifest using  the same ID and defining the appropriate scopes.</span></span>

## <a name="add-the-action-command-to-your-app-manifest"></a><span data-ttu-id="ef1be-138">Hinzufügen des Aktionsbefehls zum App-Manifest</span><span class="sxs-lookup"><span data-stu-id="ef1be-138">Add the action command to your app manifest</span></span>

<span data-ttu-id="ef1be-139">Um den Aktionsbefehl zum App-Manifest hinzuzufügen, müssen Sie der `composeExtension` obersten Ebene des APP-Manifest-JSON ein neues Objekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-139">To add the action command to the app manifest, you must add a new `composeExtension` object to the top level of the app manifest JSON.</span></span> <span data-ttu-id="ef1be-140">Dazu können Sie eine der folgenden Methoden verwenden:</span><span class="sxs-lookup"><span data-stu-id="ef1be-140">You can use one of the following ways to do so:</span></span>

* [<span data-ttu-id="ef1be-141">Erstellen eines Aktionsbefehls mit App Studio</span><span class="sxs-lookup"><span data-stu-id="ef1be-141">Create an action command using App Studio</span></span>](#create-an-action-command-using-app-studio)
* [<span data-ttu-id="ef1be-142">Manuelles Erstellen eines Aktionsbefehls</span><span class="sxs-lookup"><span data-stu-id="ef1be-142">Create an action command manually</span></span>](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a><span data-ttu-id="ef1be-143">Erstellen eines Aktionsbefehls mit App Studio</span><span class="sxs-lookup"><span data-stu-id="ef1be-143">Create an action command using App Studio</span></span>

> [!NOTE]
> <span data-ttu-id="ef1be-144">Voraussetzung zum Erstellen eines Aktionsbefehls ist, dass Sie bereits eine Messaging-Erweiterung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ef1be-144">The prerequisite to create an action command is that you have already created a messaging extension.</span></span> <span data-ttu-id="ef1be-145">Informationen zum Erstellen einer Messaging-Erweiterung finden Sie unter [Erstellen einer Messaging-Erweiterung.](~/messaging-extensions/how-to/create-messaging-extension.md)</span><span class="sxs-lookup"><span data-stu-id="ef1be-145">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="ef1be-146">**So erstellen Sie einen Aktionsbefehl**</span><span class="sxs-lookup"><span data-stu-id="ef1be-146">**To create an action command**</span></span>

1. <span data-ttu-id="ef1be-147">Öffnen Sie **App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **"Manifest-Editor"** aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-147">Open **App Studio** from the Microsoft Teams client and select the **Manifest editor** tab.</span></span>
1. <span data-ttu-id="ef1be-148">Wenn Sie Ihr App-Paket bereits in **App Studio** erstellt haben, wählen Sie es aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-148">If you already created your app package in **App Studio**, select it from the list.</span></span> <span data-ttu-id="ef1be-149">Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes Paket.</span><span class="sxs-lookup"><span data-stu-id="ef1be-149">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="ef1be-150">Wählen Sie nach dem Importieren eines **App-Pakets Messaging-Erweiterungen** unter **"Funktionen"** aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-150">After importing an app package, select **Messaging extensions** under **Capabilities**.</span></span> <span data-ttu-id="ef1be-151">Sie erhalten ein Popupfenster zum Einrichten der Messaging-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="ef1be-151">You get a pop-up window to set up the messaging extension.</span></span>
1. <span data-ttu-id="ef1be-152">Wählen Sie im Fenster **"Einrichten"** aus, um die Messaging-Erweiterung in Ihre App-Oberfläche einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-152">Select **Set up** in the window to include the messaging extension in your app experience.</span></span> <span data-ttu-id="ef1be-153">In der folgenden Abbildung wird das Einrichtungsfenster der Messaging-Erweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ef1be-153">The following image displays the messaging extension set up window:</span></span>

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>
    
1. <span data-ttu-id="ef1be-154">Um eine Messaging-Erweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot.</span><span class="sxs-lookup"><span data-stu-id="ef1be-154">To create a messaging extension, you need a Microsoft registered bot.</span></span> <span data-ttu-id="ef1be-155">Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-155">You can either use an existing bot or create a new bot.</span></span> <span data-ttu-id="ef1be-156">Wählen Sie die Option **"Neuen Bot erstellen"** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie **"Erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-156">Select **Create new bot** option, give a name for the new bot, and select **Create**.</span></span> <span data-ttu-id="ef1be-157">Die folgende Abbildung zeigt die Bot-Erstellung für die Messaging-Erweiterung:</span><span class="sxs-lookup"><span data-stu-id="ef1be-157">The following image displays bot creation for messaging extension:</span></span>

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. <span data-ttu-id="ef1be-158">Wählen Sie im **Abschnitt "Befehl"** der Seite "Messaging-Erweiterungen" die Option **"Hinzufügen"** aus, um die Befehle einzuschließen, die das Verhalten der Messaging-Erweiterung bestimmen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-158">Select **Add** in the **Command section** of the messaging extensions page to include the commands which decides the behaviour of messaging extension.</span></span>   
<span data-ttu-id="ef1be-159">In der folgenden Abbildung wird die Befehlserweiterung für die Messaging-Erweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ef1be-159">The following image displays command addition for messaging extension:</span></span>

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. <span data-ttu-id="ef1be-160">Wählen Sie **"Benutzer dürfen Aktionen in externen Diensten auslösen, während sie sich innerhalb von Teams** befinden" aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-160">Select **Allow users to trigger actions in external services while inside of Teams**.</span></span> <span data-ttu-id="ef1be-161">In der folgenden Abbildung wird die Aktionsbefehlsauswahl angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ef1be-161">The following image displays the action command selection:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>
    
1. <span data-ttu-id="ef1be-162">Um einen statischen Satz von Parametern zum Erstellen des Aufgabenmoduls zu verwenden, wählen Sie **einen Satz statischer Parameter für den Befehl** definieren aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-162">To use a static set of parameters to create your task module, select **Define a set of static parameters for the command**.</span></span> 

    <span data-ttu-id="ef1be-163">In der folgenden Abbildung wird die Auswahl der statischen Parameter des Aktionsbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ef1be-163">The following image displays the action command static parameter selection:</span></span>

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/> 
   
    <span data-ttu-id="ef1be-164">Die folgende Abbildung zeigt ein Beispiel für die Einrichtung statischer Parameter:</span><span class="sxs-lookup"><span data-stu-id="ef1be-164">The following image displays an example static parameter set-up:</span></span> 

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    <span data-ttu-id="ef1be-165">Die folgende Abbildung zeigt ein Beispiel für statische Parametertests:</span><span class="sxs-lookup"><span data-stu-id="ef1be-165">The following image displays an example static parameter testing:</span></span>

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. <span data-ttu-id="ef1be-166">Um dynamische Parameter zu verwenden, wählen Sie aus, um **einen dynamischen Satz von Parametern von Ihrem Bot abzurufen.**</span><span class="sxs-lookup"><span data-stu-id="ef1be-166">To use dynamic parameters, select to **Fetch a dynamic set of parameters from your bot**.</span></span> <span data-ttu-id="ef1be-167">In der folgenden Abbildung wird die Auswahl des Aktionsbefehlsparameters angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ef1be-167">The following image displays the action command parameter selection:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>
    
1. <span data-ttu-id="ef1be-168">Fügen Sie eine **Befehls-ID** und einen **Titel** hinzu.</span><span class="sxs-lookup"><span data-stu-id="ef1be-168">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="ef1be-169">Wählen Sie den Speicherort aus, an dem Sie den Aktionsbefehl aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="ef1be-169">Select the location from where you want to invoke the action command.</span></span> <span data-ttu-id="ef1be-170">In der folgenden Abbildung wird der Aufrufspeicherort des Aktionsbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ef1be-170">The following image displays the action command invoke location:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. <span data-ttu-id="ef1be-171">Wählen Sie **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="ef1be-171">Select **Save**.</span></span>
1. <span data-ttu-id="ef1be-172">Um weitere Parameter hinzuzufügen, wählen Sie die Schaltfläche **"Hinzufügen"** im Abschnitt **"Parameter"** aus.</span><span class="sxs-lookup"><span data-stu-id="ef1be-172">To add more parameters, select the **Add** button in the **Parameters** section.</span></span>

### <a name="create-an-action-command-manually"></a><span data-ttu-id="ef1be-173">Manuelles Erstellen eines Aktionsbefehls</span><span class="sxs-lookup"><span data-stu-id="ef1be-173">Create an action command manually</span></span>

<span data-ttu-id="ef1be-174">Zum manuellen Hinzufügen des aktionsbasierten Messaging-Erweiterungsbefehls zum App-Manifest müssen Sie dem Array von Objekten die folgenden Parameter `composeExtension.commands` hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="ef1be-174">To manually add your action-based messaging extension command to your app manifest, you must add the following parameters to the `composeExtension.commands` array of objects:</span></span>

| <span data-ttu-id="ef1be-175">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="ef1be-175">Property name</span></span> | <span data-ttu-id="ef1be-176">Zweck</span><span class="sxs-lookup"><span data-stu-id="ef1be-176">Purpose</span></span> | <span data-ttu-id="ef1be-177">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="ef1be-177">Required?</span></span> | <span data-ttu-id="ef1be-178">Mindestversion des Manifests</span><span class="sxs-lookup"><span data-stu-id="ef1be-178">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="ef1be-179">Diese Eigenschaft ist eine eindeutige ID, die Sie diesem Befehl zuweisen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-179">This property is an unique ID that you assign to this command.</span></span> <span data-ttu-id="ef1be-180">Die Benutzeranforderung enthält diese ID.</span><span class="sxs-lookup"><span data-stu-id="ef1be-180">The user request includes this ID.</span></span> | <span data-ttu-id="ef1be-181">Ja</span><span class="sxs-lookup"><span data-stu-id="ef1be-181">Yes</span></span> | <span data-ttu-id="ef1be-182">1.0</span><span class="sxs-lookup"><span data-stu-id="ef1be-182">1.0</span></span> |
| `title` | <span data-ttu-id="ef1be-183">Diese Eigenschaft ist ein Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="ef1be-183">This property is a command name.</span></span> <span data-ttu-id="ef1be-184">Dieser Wert wird in der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ef1be-184">This value appears in the UI.</span></span> | <span data-ttu-id="ef1be-185">Ja</span><span class="sxs-lookup"><span data-stu-id="ef1be-185">Yes</span></span> | <span data-ttu-id="ef1be-186">1.0</span><span class="sxs-lookup"><span data-stu-id="ef1be-186">1.0</span></span> |
| `type` | <span data-ttu-id="ef1be-187">Diese Eigenschaft muss eine `action` .</span><span class="sxs-lookup"><span data-stu-id="ef1be-187">This property must be an `action`.</span></span> | <span data-ttu-id="ef1be-188">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-188">No</span></span> | <span data-ttu-id="ef1be-189">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-189">1.4</span></span> |
| `fetchTask` | <span data-ttu-id="ef1be-190">Diese Eigenschaft wird `true` für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul sowie für eine statische Liste von `false` Parametern oder beim Laden der Webansicht durch eine `taskInfo` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ef1be-190">This property is set to `true` for an adaptive card or embedded web view for your task module, and`false` for a static list of parameters or when loading the web view by a `taskInfo`.</span></span> | <span data-ttu-id="ef1be-191">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-191">No</span></span> | <span data-ttu-id="ef1be-192">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-192">1.4</span></span> |
| `context` | <span data-ttu-id="ef1be-193">Diese Eigenschaft ist ein optionales Array von Werten, das definiert, von wo aus die Messaging-Erweiterung aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ef1be-193">This property is an optional array of values that defines where the messaging extension is invoked from.</span></span> <span data-ttu-id="ef1be-194">Die möglichen Werte sind `message`, `compose` oder `commandBox`.</span><span class="sxs-lookup"><span data-stu-id="ef1be-194">The possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="ef1be-195">Der Standardwert ist `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="ef1be-195">The default value is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="ef1be-196">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-196">No</span></span> | <span data-ttu-id="ef1be-197">1,5</span><span class="sxs-lookup"><span data-stu-id="ef1be-197">1.5</span></span> |

<span data-ttu-id="ef1be-198">Wenn Sie eine statische Liste von Parametern verwenden, müssen Sie auch die folgenden Parameter hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="ef1be-198">If you are using a static list of parameters, you must also add the following parameters:</span></span>

| <span data-ttu-id="ef1be-199">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="ef1be-199">Property name</span></span> | <span data-ttu-id="ef1be-200">Zweck</span><span class="sxs-lookup"><span data-stu-id="ef1be-200">Purpose</span></span> | <span data-ttu-id="ef1be-201">Ist erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ef1be-201">Is required?</span></span> | <span data-ttu-id="ef1be-202">Mindestversion des Manifests</span><span class="sxs-lookup"><span data-stu-id="ef1be-202">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="ef1be-203">Diese Eigenschaft beschreibt die statische Liste der Parameter für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="ef1be-203">This property describes the static list of parameters for the command.</span></span> <span data-ttu-id="ef1be-204">Wird nur verwendet, wenn `fetchTask` `false` .</span><span class="sxs-lookup"><span data-stu-id="ef1be-204">Only use when `fetchTask` is `false`.</span></span> | <span data-ttu-id="ef1be-205">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-205">No</span></span> | <span data-ttu-id="ef1be-206">1.0</span><span class="sxs-lookup"><span data-stu-id="ef1be-206">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="ef1be-207">Diese Eigenschaft beschreibt den Namen des Parameters.</span><span class="sxs-lookup"><span data-stu-id="ef1be-207">This property describes the name of the parameter.</span></span> <span data-ttu-id="ef1be-208">Dies wird in der Benutzeranforderung an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="ef1be-208">This is sent to your service in the user request.</span></span> | <span data-ttu-id="ef1be-209">Ja</span><span class="sxs-lookup"><span data-stu-id="ef1be-209">Yes</span></span> | <span data-ttu-id="ef1be-210">1.0</span><span class="sxs-lookup"><span data-stu-id="ef1be-210">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="ef1be-211">Diese Eigenschaft beschreibt die Zwecke des Parameters oder ein Beispiel für den Wert, der angegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef1be-211">This property describes the parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="ef1be-212">Dieser Wert wird in der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ef1be-212">This value appears in the UI.</span></span> | <span data-ttu-id="ef1be-213">Ja</span><span class="sxs-lookup"><span data-stu-id="ef1be-213">Yes</span></span> | <span data-ttu-id="ef1be-214">1.0</span><span class="sxs-lookup"><span data-stu-id="ef1be-214">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="ef1be-215">Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine kurze Bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="ef1be-215">This property is a short user-friendly parameter title or label.</span></span> | <span data-ttu-id="ef1be-216">Ja</span><span class="sxs-lookup"><span data-stu-id="ef1be-216">Yes</span></span> | <span data-ttu-id="ef1be-217">1.0</span><span class="sxs-lookup"><span data-stu-id="ef1be-217">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="ef1be-218">Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ef1be-218">This property is set to the type of input required.</span></span> <span data-ttu-id="ef1be-219">Zu den möglichen Werten gehören `text` , , , , , `textarea` `number` `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="ef1be-219">The possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="ef1be-220">Der Standardwert ist `text` auf .</span><span class="sxs-lookup"><span data-stu-id="ef1be-220">The default value is set to `text`.</span></span> | <span data-ttu-id="ef1be-221">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-221">No</span></span> | <span data-ttu-id="ef1be-222">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-222">1.4</span></span> |

<span data-ttu-id="ef1be-223">Wenn Sie eine eingebettete Webansicht verwenden, können Sie optional das Objekt hinzufügen, `taskInfo` um Ihre Webansicht abzurufen, ohne Ihren Bot direkt aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ef1be-223">If you are using an embedded web view, you can optionally add the `taskInfo` object to fetch your web view without calling your bot directly.</span></span> <span data-ttu-id="ef1be-224">Wenn Sie diese Option auswählen, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern.</span><span class="sxs-lookup"><span data-stu-id="ef1be-224">If you select this option, the behavior is similar to that of using a static list of parameters.</span></span> <span data-ttu-id="ef1be-225">In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span><span class="sxs-lookup"><span data-stu-id="ef1be-225">In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span></span> <span data-ttu-id="ef1be-226">Wenn Sie ein `taskInfo` Objekt verwenden, müssen Sie den `fetchTask` Parameter auf `false` .</span><span class="sxs-lookup"><span data-stu-id="ef1be-226">If you are using a `taskInfo` object, you must set the `fetchTask` parameter to `false`.</span></span>

| <span data-ttu-id="ef1be-227">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="ef1be-227">Property name</span></span> | <span data-ttu-id="ef1be-228">Zweck</span><span class="sxs-lookup"><span data-stu-id="ef1be-228">Purpose</span></span> | <span data-ttu-id="ef1be-229">Ist erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ef1be-229">Is required?</span></span> | <span data-ttu-id="ef1be-230">Mindestversion des Manifests</span><span class="sxs-lookup"><span data-stu-id="ef1be-230">Minimum manifest version</span></span> |
|---|---|---|---|
|`taskInfo`|<span data-ttu-id="ef1be-231">Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="ef1be-231">Specify the task module to preload when using a messaging extension command.</span></span> | <span data-ttu-id="ef1be-232">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-232">No</span></span> | <span data-ttu-id="ef1be-233">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-233">1.4</span></span> |
|`taskInfo.title`|<span data-ttu-id="ef1be-234">Titel des anfänglichen Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="ef1be-234">Initial task module title.</span></span> |<span data-ttu-id="ef1be-235">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-235">No</span></span> | <span data-ttu-id="ef1be-236">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-236">1.4</span></span> |
|`taskInfo.width`|<span data-ttu-id="ef1be-237">Die Breite des Aufgabenmoduls, entweder eine Zahl in Pixeln oder ein Standardlayout wie `large` , `medium` oder `small` .</span><span class="sxs-lookup"><span data-stu-id="ef1be-237">Task module width, either a number in pixels or default layout such as `large`, `medium`, or `small`.</span></span> |<span data-ttu-id="ef1be-238">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-238">No</span></span> | <span data-ttu-id="ef1be-239">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-239">1.4</span></span> |
|`taskInfo.height`|<span data-ttu-id="ef1be-240">Die Höhe des Aufgabenmoduls, entweder eine Zahl in Pixeln oder ein Standardlayout wie `large` , `medium` oder `small` .</span><span class="sxs-lookup"><span data-stu-id="ef1be-240">Task module height, either a number in pixels or default layout such as `large`, `medium`, or `small`.</span></span>|<span data-ttu-id="ef1be-241">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-241">No</span></span> | <span data-ttu-id="ef1be-242">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-242">1.4</span></span> |
|`taskInfo.url`|<span data-ttu-id="ef1be-243">Ursprüngliche Webansichts-URL.</span><span class="sxs-lookup"><span data-stu-id="ef1be-243">Initial web view URL.</span></span>|<span data-ttu-id="ef1be-244">Nein</span><span class="sxs-lookup"><span data-stu-id="ef1be-244">No</span></span> | <span data-ttu-id="ef1be-245">1.4</span><span class="sxs-lookup"><span data-stu-id="ef1be-245">1.4</span></span> | 

#### <a name="app-manifest-example"></a><span data-ttu-id="ef1be-246">Beispiel für ein App-Manifest</span><span class="sxs-lookup"><span data-stu-id="ef1be-246">App manifest example</span></span>

<span data-ttu-id="ef1be-247">Der folgende Abschnitt ist ein Beispiel für ein `composeExtensions` Objekt, das zwei Aktionsbefehle definiert.</span><span class="sxs-lookup"><span data-stu-id="ef1be-247">The following section is an example of a `composeExtensions` object defining two action commands.</span></span> <span data-ttu-id="ef1be-248">Es ist kein Beispiel für das vollständige Manifest.</span><span class="sxs-lookup"><span data-stu-id="ef1be-248">It is not an example of the complete manifest.</span></span> <span data-ttu-id="ef1be-249">Das vollständige App-Manifestschema finden Sie unter [App-Manifestschema:](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="ef1be-249">For the complete app manifest schema, see [app manifest schema](~/resources/schema/manifest-schema.md):</span></span>

```json
...
"composeExtensions": [
  {
    "botId": "12a3c29f-1fc5-4d97-a142-12bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "addTodo",
        "description": "Create a To Do item",
        "title": "Create To Do",
        "type": "action",
        "context": ["commandBox", "message", "compose"],
        "fetchTask": true,
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
      }
    ]
  }
]
...
```

## <a name="code-sample"></a><span data-ttu-id="ef1be-250">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ef1be-250">Code sample</span></span>

| <span data-ttu-id="ef1be-251">Beispielname</span><span class="sxs-lookup"><span data-stu-id="ef1be-251">Sample Name</span></span>           | <span data-ttu-id="ef1be-252">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ef1be-252">Description</span></span> | <span data-ttu-id="ef1be-253">.NET</span><span class="sxs-lookup"><span data-stu-id="ef1be-253">.NET</span></span>    | <span data-ttu-id="ef1be-254">Node.js</span><span class="sxs-lookup"><span data-stu-id="ef1be-254">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="ef1be-255">Teams Messaging-Erweiterungsaktion</span><span class="sxs-lookup"><span data-stu-id="ef1be-255">Teams messaging extension action</span></span>| <span data-ttu-id="ef1be-256">Beschreibt, wie Aktionsbefehle definiert, Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktion reagiert wird.</span><span class="sxs-lookup"><span data-stu-id="ef1be-256">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="ef1be-257">View</span><span class="sxs-lookup"><span data-stu-id="ef1be-257">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="ef1be-258">View</span><span class="sxs-lookup"><span data-stu-id="ef1be-258">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="ef1be-259">Teams Messaging-Erweiterungssuche</span><span class="sxs-lookup"><span data-stu-id="ef1be-259">Teams messaging extension search</span></span>   |  <span data-ttu-id="ef1be-260">Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.</span><span class="sxs-lookup"><span data-stu-id="ef1be-260">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="ef1be-261">View</span><span class="sxs-lookup"><span data-stu-id="ef1be-261">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="ef1be-262">View</span><span class="sxs-lookup"><span data-stu-id="ef1be-262">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="ef1be-263">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ef1be-263">Next step</span></span>

<span data-ttu-id="ef1be-264">Wenn Sie eine adaptive Karte oder eine eingebettete Webansicht ohne `taskInfo` Objekt verwenden, besteht der nächste Schritt in folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="ef1be-264">If you are using either an Adaptive Card or an embedded web view without a `taskInfo` object, the next step is to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef1be-265">Erstellen und Antworten mit einem Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="ef1be-265">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/create-task-module.md)

<span data-ttu-id="ef1be-266">Wenn Sie die Parameter oder eine eingebettete Webansicht mit einem `taskInfo` Objekt verwenden, besteht der nächste Schritt in folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="ef1be-266">If you are using the parameters or an embedded web view with a `taskInfo` object, the next step is to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef1be-267">Antworten auf das Senden des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="ef1be-267">Respond to task module submit</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

