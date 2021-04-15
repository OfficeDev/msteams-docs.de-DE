---
title: Definieren von Befehlen für Nachrichtenerweiterungsaktion
author: clearab
description: Übersicht über Messagingerweiterungsaktionsbefehle
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 51c2ce5ac3b8ab265d9bec0b1101ba18138a9365
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696951"
---
# <a name="define-messaging-extension-action-commands"></a><span data-ttu-id="f6f38-103">Definieren von Befehlen für Nachrichtenerweiterungsaktion</span><span class="sxs-lookup"><span data-stu-id="f6f38-103">Define messaging extension action commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="f6f38-104">Mit Aktionsbefehlen können Sie Ihren Benutzern ein modales Popup präsentieren, das als Aufgabenmodul in Teams bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="f6f38-104">Action commands allow you to present your users with a modal popup called a task module in Teams.</span></span> <span data-ttu-id="f6f38-105">Das Aufgabenmodul sammelt oder zeigt Informationen an, verarbeitet die Interaktion und sendet die Informationen zurück an Teams.</span><span class="sxs-lookup"><span data-stu-id="f6f38-105">The task module collects or displays information, processes the interaction and sends the information back to Teams.</span></span> <span data-ttu-id="f6f38-106">In diesem Dokument erfahren Sie, wie Sie Aktionsbefehlsaufrufe auswählen, Ihr Aufgabenmodul erstellen, endgültige Nachrichten oder Karten senden, Aktionsbefehle mithilfe von App Studio erstellen oder manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-106">This document guides you on how to select action command invoke locations, create your task module, send final message, or card, create action command using app studio, or create it manually.</span></span> 

<span data-ttu-id="f6f38-107">Bevor Sie den Aktionsbefehl erstellen, müssen Sie die folgenden Faktoren festlegen:</span><span class="sxs-lookup"><span data-stu-id="f6f38-107">Before creating the action command you must decide the following factors:</span></span>

1. [<span data-ttu-id="f6f38-108">Wo kann der Aktionsbefehl ausgelöst werden?</span><span class="sxs-lookup"><span data-stu-id="f6f38-108">Where can the action command be triggered from?</span></span>](#select-action-command-invoke-locations)
1. [<span data-ttu-id="f6f38-109">Wie wird das Aufgabenmodul erstellt?</span><span class="sxs-lookup"><span data-stu-id="f6f38-109">How will the task module be created?</span></span>](#select-how-to-create-your-task-module)
1. [<span data-ttu-id="f6f38-110">Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, damit der Benutzer die Nachricht übermitteln kann?</span><span class="sxs-lookup"><span data-stu-id="f6f38-110">Will the final message or card be sent to the channel from a bot, or will the message or card be inserted into the compose message area for the user to submit?</span></span>](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a><span data-ttu-id="f6f38-111">Auswählen von Aktionsbefehlsaufrufen</span><span class="sxs-lookup"><span data-stu-id="f6f38-111">Select action command invoke locations</span></span>

<span data-ttu-id="f6f38-112">Zuerst müssen Sie den Speicherort festlegen, von dem aus der Aktionsbefehl aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="f6f38-112">First, you must decide the location from where your action command must be invoked.</span></span> <span data-ttu-id="f6f38-113">Durch Angeben des In-App-Manifests kann Ihr Befehl an einem oder mehreren der folgenden `context` Speicherorte aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="f6f38-113">By specifying the `context` in your app manifest, your command can be invoked from one or more of the following locations:</span></span>

* <span data-ttu-id="f6f38-114">Bereich "Nachricht verfassen": Die Schaltflächen am unteren Rand des Bereichs "Verfassen von Nachrichten".</span><span class="sxs-lookup"><span data-stu-id="f6f38-114">Compose message area: The buttons at the bottom of the compose message area.</span></span>
* <span data-ttu-id="f6f38-115">Befehlsfeld: Durch @mentioning App im Befehlsfeld.</span><span class="sxs-lookup"><span data-stu-id="f6f38-115">Command box: By @mentioning your app in the command box.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="f6f38-116">Wenn die Messagingerweiterung über das Befehlsfeld aufgerufen wird, können Sie nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="f6f38-116">If messaging extension is invoked from the command box, you cannot respond with a bot message inserted directly into the conversation.</span></span>

* <span data-ttu-id="f6f38-117">Nachricht: Direkt von einer vorhandenen Nachricht über das `...` Überlaufmenü einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="f6f38-117">Message: Directly from an existing message through the `...` overflow menu on a message.</span></span> 
    > [!NOTE] 
    > <span data-ttu-id="f6f38-118">Der anfängliche Aufruf ihres Bots enthält ein JSON-Objekt, das die Nachricht enthält, von der sie aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="f6f38-118">The initial invoke to your bot includes a JSON object containing the message from which it was invoked.</span></span> <span data-ttu-id="f6f38-119">Sie können die Nachricht verarbeiten, bevor Sie sie mit einem Aufgabenmodul präsentieren.</span><span class="sxs-lookup"><span data-stu-id="f6f38-119">You can process the message before presenting them with a task module.</span></span>

<span data-ttu-id="f6f38-120">In der folgenden Abbildung werden die Speicherorte angezeigt, an denen der Aktionsbefehl aufgerufen wird:</span><span class="sxs-lookup"><span data-stu-id="f6f38-120">The following image displays the locations from where action command is invoked:</span></span>

![Aktionsbefehl ruft Speicherorte auf](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a><span data-ttu-id="f6f38-122">Auswählen, wie Sie Ihr Aufgabenmodul erstellen</span><span class="sxs-lookup"><span data-stu-id="f6f38-122">Select how to create your task module</span></span>

<span data-ttu-id="f6f38-123">Sie müssen nicht nur auswählen, von wo aus Der Befehl aufgerufen werden kann, sondern auch auswählen, wie das Formular im Aufgabenmodul für Ihre Benutzer auffüllt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f6f38-123">In addition to selecting where your command can be invoked from, you must also select how to populate the form in the task module for your users.</span></span> <span data-ttu-id="f6f38-124">Sie haben die folgenden drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:</span><span class="sxs-lookup"><span data-stu-id="f6f38-124">You have the following three options for creating the form that is rendered inside the task module:</span></span>   

* <span data-ttu-id="f6f38-125">**Statische Liste der Parameter:** Dies ist die einfachste Methode.</span><span class="sxs-lookup"><span data-stu-id="f6f38-125">**Static list of parameters**: This is the simplest method.</span></span> <span data-ttu-id="f6f38-126">Sie können eine Liste der Parameter in Ihrem App-Manifest definieren, das der Teams-Client rendert, die Formatierung in diesem Fall jedoch nicht steuern.</span><span class="sxs-lookup"><span data-stu-id="f6f38-126">You can define a list of parameters in your app manifest the Teams client renders, but cannot control the formatting in this case.</span></span>
* <span data-ttu-id="f6f38-127">**Adaptive Karte**: Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie jedoch weiterhin die verfügbaren Steuerelemente und Formatierungsoptionen einschränkt.</span><span class="sxs-lookup"><span data-stu-id="f6f38-127">**Adaptive Card**:  You can select to use an Adaptive Card, which provides greater control over the UI, but still limits you on the available controls and formatting options.</span></span>
* <span data-ttu-id="f6f38-128">**Eingebettete Webansicht:** Sie können eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten, um eine vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f6f38-128">**Embedded web view**: You can select to embed a custom web view in the task module to have a complete control over the UI and controls.</span></span> 

<span data-ttu-id="f6f38-129">Wenn Sie das Aufgabenmodul mit einer statischen Liste von Parametern erstellen möchten und wenn der Benutzer das Aufgabenmodul übermittelt, wird die Messagingerweiterung aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-129">If you select to create the task module with a static list of parameters and when the user submits the task module, the messaging extension is called.</span></span> <span data-ttu-id="f6f38-130">Bei Verwendung einer eingebetteten Webansicht oder einer adaptiven Karte muss Ihre Messagingerweiterung ein anfängliches Aufrufereignis vom Benutzer behandeln, das Aufgabenmodul erstellen und an den Client zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="f6f38-130">When using an embedded web view or an Adaptive Card, your messaging extension must handle an initial invoke event from the user, create the task module, and return it back to the client.</span></span>

## <a name="select-how-the-final-message-is-sent"></a><span data-ttu-id="f6f38-131">Auswählen, wie die endgültige Nachricht gesendet wird</span><span class="sxs-lookup"><span data-stu-id="f6f38-131">Select how the final message is sent</span></span>

<span data-ttu-id="f6f38-132">In den meisten Fällen führt der Aktionsbefehl zu einer Karte, die in das Meldungsfeld Verfassen eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="f6f38-132">In most cases, the action command results in a card inserted into the compose message box.</span></span> <span data-ttu-id="f6f38-133">Der Benutzer kann es an den Kanal oder Chat senden.</span><span class="sxs-lookup"><span data-stu-id="f6f38-133">The user can send it into the channel or chat.</span></span> <span data-ttu-id="f6f38-134">In diesem Fall stammt die Nachricht vom Benutzer, und der Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f6f38-134">In this case, the message comes from the user, and the bot cannot edit or update the card further.</span></span>

<span data-ttu-id="f6f38-135">Wenn die Messagingerweiterung aus dem Verfassenfeld oder direkt aus einer Nachricht aufgerufen wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-135">If the messaging extension is invoked from the compose box or directly from a message, your web service can insert the final response directly into the channel or chat.</span></span> <span data-ttu-id="f6f38-136">In diesem Fall stammt die adaptive Karte vom Bot, der Bot aktualisiert sie und antwortet bei Bedarf auf den Unterhaltungsthread.</span><span class="sxs-lookup"><span data-stu-id="f6f38-136">In this case, the Adaptive Card comes from the bot, the bot updates it, and replies to the conversation thread if needed.</span></span> <span data-ttu-id="f6f38-137">Sie müssen das Objekt dem App-Manifest mit derselben ID hinzufügen `bot` und die entsprechenden Bereiche definieren.</span><span class="sxs-lookup"><span data-stu-id="f6f38-137">You must add the `bot` object to the app manifest using  the same ID and defining the appropriate scopes.</span></span>

## <a name="add-the-action-command-to-your-app-manifest"></a><span data-ttu-id="f6f38-138">Hinzufügen des Aktionsbefehls zum App-Manifest</span><span class="sxs-lookup"><span data-stu-id="f6f38-138">Add the action command to your app manifest</span></span>

<span data-ttu-id="f6f38-139">Zum Hinzufügen des Aktionsbefehls zum App-Manifest müssen Sie der obersten Ebene des App-Manifest-JSON ein neues `composeExtension` Objekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-139">To add the action command to the app manifest, you must add a new `composeExtension` object to the top level of the app manifest JSON.</span></span> <span data-ttu-id="f6f38-140">Dazu können Sie eine der folgenden Möglichkeiten verwenden:</span><span class="sxs-lookup"><span data-stu-id="f6f38-140">You can use one of the following ways to do so:</span></span>

* [<span data-ttu-id="f6f38-141">Erstellen eines Aktionsbefehls mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="f6f38-141">Create an action command using App Studio</span></span>](#create-an-action-command-using-app-studio)
* [<span data-ttu-id="f6f38-142">Manuelles Erstellen eines Aktionsbefehls</span><span class="sxs-lookup"><span data-stu-id="f6f38-142">Create an action command manually</span></span>](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a><span data-ttu-id="f6f38-143">Erstellen eines Aktionsbefehls mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="f6f38-143">Create an action command using App Studio</span></span>

> [!NOTE]
> <span data-ttu-id="f6f38-144">Voraussetzung für das Erstellen eines Aktionsbefehls ist, dass Sie bereits eine Messagingerweiterung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="f6f38-144">The prerequisite to create an action command is that you have already created a messaging extension.</span></span> <span data-ttu-id="f6f38-145">Informationen zum Erstellen einer Messagingerweiterung finden Sie unter [Create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="f6f38-145">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="f6f38-146">**So erstellen Sie einen Aktionsbefehl**</span><span class="sxs-lookup"><span data-stu-id="f6f38-146">**To create an action command**</span></span>

1. <span data-ttu-id="f6f38-147">Öffnen **Sie App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="f6f38-147">Open **App Studio** from the Microsoft Teams client and select the **Manifest editor** tab.</span></span>
1. <span data-ttu-id="f6f38-148">Wenn Sie Ihr App-Paket bereits in **App Studio erstellt haben,** wählen Sie es aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="f6f38-148">If you already created your app package in **App Studio**, select it from the list.</span></span> <span data-ttu-id="f6f38-149">Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.</span><span class="sxs-lookup"><span data-stu-id="f6f38-149">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="f6f38-150">Wählen Sie nach dem Importieren eines App-Pakets unter Funktionen die Option **Messagingerweiterungen** **aus.**</span><span class="sxs-lookup"><span data-stu-id="f6f38-150">After importing an app package, select **Messaging extensions** under **Capabilities**.</span></span> <span data-ttu-id="f6f38-151">Sie erhalten ein Popupfenster zum Einrichten der Messagingerweiterung.</span><span class="sxs-lookup"><span data-stu-id="f6f38-151">You get a pop-up window to set up the messaging extension.</span></span>
1. <span data-ttu-id="f6f38-152">Wählen **Sie Einrichten** im Fenster aus, um die Messagingerweiterung in Ihre App-Umgebung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f6f38-152">Select **Set up** in the window to include the messaging extension in your app experience.</span></span> <span data-ttu-id="f6f38-153">In der folgenden Abbildung wird das Einrichtungsfenster der Messagingerweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-153">The following image displays the messaging extension set up window:</span></span>

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>
    
1. <span data-ttu-id="f6f38-154">Zum Erstellen einer Messagingerweiterung benötigen Sie einen von Microsoft registrierten Bot.</span><span class="sxs-lookup"><span data-stu-id="f6f38-154">To create a messaging extension, you need a Microsoft registered bot.</span></span> <span data-ttu-id="f6f38-155">Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-155">You can either use an existing bot or create a new bot.</span></span> <span data-ttu-id="f6f38-156">Wählen **Sie Die Option Neuer Bot erstellen** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie Erstellen **aus.**</span><span class="sxs-lookup"><span data-stu-id="f6f38-156">Select **Create new bot** option, give a name for the new bot, and select **Create**.</span></span> <span data-ttu-id="f6f38-157">In der folgenden Abbildung wird die Boterstellung für die Messagingerweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-157">The following image displays bot creation for messaging extension:</span></span>

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. <span data-ttu-id="f6f38-158">Wählen **Sie Im** Abschnitt Befehl **der** Seite Messagingerweiterungen die Option Hinzufügen aus, um die Befehle hinzuzufügen, die das Verhalten der Messagingerweiterung bestimmen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-158">Select **Add** in the **Command section** of the messaging extensions page to include the commands which decides the behaviour of messaging extension.</span></span>   
<span data-ttu-id="f6f38-159">In der folgenden Abbildung wird die Befehlserweiterung für die Messagingerweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-159">The following image displays command addition for messaging extension:</span></span>

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. <span data-ttu-id="f6f38-160">Wählen **Sie Benutzer zulassen aus, um Aktionen in externen Diensten innerhalb von Teams auszulösen.**</span><span class="sxs-lookup"><span data-stu-id="f6f38-160">Select **Allow users to trigger actions in external services while inside of Teams**.</span></span> <span data-ttu-id="f6f38-161">In der folgenden Abbildung wird die Aktionsbefehlsauswahl angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-161">The following image displays the action command selection:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>
    
1. <span data-ttu-id="f6f38-162">Um einen statischen Parametersatz zum Erstellen des Aufgabenmoduls zu verwenden, wählen Sie Definieren einer Reihe statischer Parameter **für den Befehl aus.**</span><span class="sxs-lookup"><span data-stu-id="f6f38-162">To use a static set of parameters to create your task module, select **Define a set of static parameters for the command**.</span></span> 

    <span data-ttu-id="f6f38-163">In der folgenden Abbildung wird die Auswahl statischer Parameter des Aktionsbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-163">The following image displays the action command static parameter selection:</span></span>

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/> 
   
    <span data-ttu-id="f6f38-164">Die folgende Abbildung zeigt ein Beispiel für die Einrichtung statischer Parameter:</span><span class="sxs-lookup"><span data-stu-id="f6f38-164">The following image displays an example static parameter set-up:</span></span> 

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    <span data-ttu-id="f6f38-165">Die folgende Abbildung zeigt ein Beispiel für statische Parametertests:</span><span class="sxs-lookup"><span data-stu-id="f6f38-165">The following image displays an example static parameter testing:</span></span>

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. <span data-ttu-id="f6f38-166">Um dynamische Parameter zu verwenden, wählen Sie aus, um einen dynamischen Satz **von Parametern aus Ihrem Bot zu holen.**</span><span class="sxs-lookup"><span data-stu-id="f6f38-166">To use dynamic parameters, select to **Fetch a dynamic set of parameters from your bot**.</span></span> <span data-ttu-id="f6f38-167">In der folgenden Abbildung wird die Auswahl des Aktionsbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-167">The following image displays the action command parameter selection:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>
    
1. <span data-ttu-id="f6f38-168">Fügen Sie **eine Befehls-ID** und einen **Titel hinzu.**</span><span class="sxs-lookup"><span data-stu-id="f6f38-168">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="f6f38-169">Wählen Sie den Speicherort aus, an dem Sie den Aktionsbefehl aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="f6f38-169">Select the location from where you want to invoke the action command.</span></span> <span data-ttu-id="f6f38-170">In der folgenden Abbildung wird der Speicherort des Aktionsbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-170">The following image displays the action command invoke location:</span></span>

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. <span data-ttu-id="f6f38-171">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="f6f38-171">Select **Save**.</span></span>
1. <span data-ttu-id="f6f38-172">Um weitere Parameter hinzuzufügen, wählen Sie **im** Abschnitt Parameter **die** Schaltfläche Hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="f6f38-172">To add more parameters, select the **Add** button in the **Parameters** section.</span></span>

### <a name="create-an-action-command-manually"></a><span data-ttu-id="f6f38-173">Manuelles Erstellen eines Aktionsbefehls</span><span class="sxs-lookup"><span data-stu-id="f6f38-173">Create an action command manually</span></span>

<span data-ttu-id="f6f38-174">Zum manuellen Hinzufügen des aktionsbasierten Messagingerweiterungsbefehls zum App-Manifest müssen Sie dem Objektarray die folgenden `composeExtension.commands` Parameter hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="f6f38-174">To manually add your action-based messaging extension command to your app manifest, you must add the following parameters to the `composeExtension.commands` array of objects:</span></span>

| <span data-ttu-id="f6f38-175">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="f6f38-175">Property name</span></span> | <span data-ttu-id="f6f38-176">Zweck</span><span class="sxs-lookup"><span data-stu-id="f6f38-176">Purpose</span></span> | <span data-ttu-id="f6f38-177">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="f6f38-177">Required?</span></span> | <span data-ttu-id="f6f38-178">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="f6f38-178">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="f6f38-179">Diese Eigenschaft ist eine eindeutige ID, die Sie diesem Befehl zuweisen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-179">This property is an unique ID that you assign to this command.</span></span> <span data-ttu-id="f6f38-180">Die Benutzeranforderung enthält diese ID.</span><span class="sxs-lookup"><span data-stu-id="f6f38-180">The user request includes this ID.</span></span> | <span data-ttu-id="f6f38-181">Ja</span><span class="sxs-lookup"><span data-stu-id="f6f38-181">Yes</span></span> | <span data-ttu-id="f6f38-182">1.0</span><span class="sxs-lookup"><span data-stu-id="f6f38-182">1.0</span></span> |
| `title` | <span data-ttu-id="f6f38-183">Diese Eigenschaft ist ein Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="f6f38-183">This property is a command name.</span></span> <span data-ttu-id="f6f38-184">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6f38-184">This value appears in the UI.</span></span> | <span data-ttu-id="f6f38-185">Ja</span><span class="sxs-lookup"><span data-stu-id="f6f38-185">Yes</span></span> | <span data-ttu-id="f6f38-186">1.0</span><span class="sxs-lookup"><span data-stu-id="f6f38-186">1.0</span></span> |
| `type` | <span data-ttu-id="f6f38-187">Diese Eigenschaft muss eine `action` sein.</span><span class="sxs-lookup"><span data-stu-id="f6f38-187">This property must be an `action`.</span></span> | <span data-ttu-id="f6f38-188">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-188">No</span></span> | <span data-ttu-id="f6f38-189">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-189">1.4</span></span> |
| `fetchTask` | <span data-ttu-id="f6f38-190">Diese Eigenschaft ist für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul und für eine statische Liste von Parametern oder beim Laden der Webansicht durch `true` `false` eine `taskInfo` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f6f38-190">This property is set to `true` for an adaptive card or embedded web view for your task module, and`false` for a static list of parameters or when loading the web view by a `taskInfo`.</span></span> | <span data-ttu-id="f6f38-191">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-191">No</span></span> | <span data-ttu-id="f6f38-192">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-192">1.4</span></span> |
| `context` | <span data-ttu-id="f6f38-193">Diese Eigenschaft ist ein optionales Array von Werten, das definiert, von wo aus die Messagingerweiterung aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f6f38-193">This property is an optional array of values that defines where the messaging extension is invoked from.</span></span> <span data-ttu-id="f6f38-194">Die möglichen Werte sind `message`, `compose` oder `commandBox`.</span><span class="sxs-lookup"><span data-stu-id="f6f38-194">The possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="f6f38-195">Der Standardwert ist `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="f6f38-195">The default value is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="f6f38-196">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-196">No</span></span> | <span data-ttu-id="f6f38-197">1,5</span><span class="sxs-lookup"><span data-stu-id="f6f38-197">1.5</span></span> |

<span data-ttu-id="f6f38-198">Wenn Sie eine statische Liste von Parametern verwenden, müssen Sie auch die folgenden Parameter hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="f6f38-198">If you are using a static list of parameters, you must also add the following parameters:</span></span>

| <span data-ttu-id="f6f38-199">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="f6f38-199">Property name</span></span> | <span data-ttu-id="f6f38-200">Zweck</span><span class="sxs-lookup"><span data-stu-id="f6f38-200">Purpose</span></span> | <span data-ttu-id="f6f38-201">Ist erforderlich?</span><span class="sxs-lookup"><span data-stu-id="f6f38-201">Is required?</span></span> | <span data-ttu-id="f6f38-202">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="f6f38-202">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="f6f38-203">Diese Eigenschaft beschreibt die statische Liste der Parameter für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="f6f38-203">This property describes the static list of parameters for the command.</span></span> <span data-ttu-id="f6f38-204">Verwenden Sie nur, `fetchTask` wenn `false` .</span><span class="sxs-lookup"><span data-stu-id="f6f38-204">Only use when `fetchTask` is `false`.</span></span> | <span data-ttu-id="f6f38-205">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-205">No</span></span> | <span data-ttu-id="f6f38-206">1.0</span><span class="sxs-lookup"><span data-stu-id="f6f38-206">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="f6f38-207">Diese Eigenschaft beschreibt den Namen des Parameters.</span><span class="sxs-lookup"><span data-stu-id="f6f38-207">This property describes the name of the parameter.</span></span> <span data-ttu-id="f6f38-208">Dies wird in der Benutzeranforderung an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="f6f38-208">This is sent to your service in the user request.</span></span> | <span data-ttu-id="f6f38-209">Ja</span><span class="sxs-lookup"><span data-stu-id="f6f38-209">Yes</span></span> | <span data-ttu-id="f6f38-210">1.0</span><span class="sxs-lookup"><span data-stu-id="f6f38-210">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="f6f38-211">Diese Eigenschaft beschreibt die Zwecke oder das Beispiel des Parameters, der bereitgestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f6f38-211">This property describes the parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="f6f38-212">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6f38-212">This value appears in the UI.</span></span> | <span data-ttu-id="f6f38-213">Ja</span><span class="sxs-lookup"><span data-stu-id="f6f38-213">Yes</span></span> | <span data-ttu-id="f6f38-214">1.0</span><span class="sxs-lookup"><span data-stu-id="f6f38-214">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="f6f38-215">Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="f6f38-215">This property is a short user-friendly parameter title or label.</span></span> | <span data-ttu-id="f6f38-216">Ja</span><span class="sxs-lookup"><span data-stu-id="f6f38-216">Yes</span></span> | <span data-ttu-id="f6f38-217">1.0</span><span class="sxs-lookup"><span data-stu-id="f6f38-217">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="f6f38-218">Diese Eigenschaft ist auf den typ der erforderlichen Eingabe festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f6f38-218">This property is set to the type of input required.</span></span> <span data-ttu-id="f6f38-219">Die möglichen Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="f6f38-219">The possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="f6f38-220">Der Standardwert ist auf `text` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f6f38-220">The default value is set to `text`.</span></span> | <span data-ttu-id="f6f38-221">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-221">No</span></span> | <span data-ttu-id="f6f38-222">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-222">1.4</span></span> |

<span data-ttu-id="f6f38-223">Wenn Sie eine eingebettete Webansicht verwenden, können Sie optional das Objekt hinzufügen, um Ihre Webansicht ohne `taskInfo` direkten Aufruf des Bots zu abrufen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-223">If you are using an embedded web view, you can optionally add the `taskInfo` object to fetch your web view without calling your bot directly.</span></span> <span data-ttu-id="f6f38-224">Wenn Sie diese Option auswählen, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern.</span><span class="sxs-lookup"><span data-stu-id="f6f38-224">If you select this option, the behavior is similar to that of using a static list of parameters.</span></span> <span data-ttu-id="f6f38-225">In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span><span class="sxs-lookup"><span data-stu-id="f6f38-225">In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md).</span></span> <span data-ttu-id="f6f38-226">Wenn Sie ein Objekt `taskInfo` verwenden, müssen Sie den `fetchTask` Parameter auf `false` festlegen.</span><span class="sxs-lookup"><span data-stu-id="f6f38-226">If you are using a `taskInfo` object, you must set the `fetchTask` parameter to `false`.</span></span>

| <span data-ttu-id="f6f38-227">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="f6f38-227">Property name</span></span> | <span data-ttu-id="f6f38-228">Zweck</span><span class="sxs-lookup"><span data-stu-id="f6f38-228">Purpose</span></span> | <span data-ttu-id="f6f38-229">Ist erforderlich?</span><span class="sxs-lookup"><span data-stu-id="f6f38-229">Is required?</span></span> | <span data-ttu-id="f6f38-230">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="f6f38-230">Minimum manifest version</span></span> |
|---|---|---|---|
|`taskInfo`|<span data-ttu-id="f6f38-231">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vorab geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="f6f38-231">Specify the task module to preload when using a messaging extension command.</span></span> | <span data-ttu-id="f6f38-232">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-232">No</span></span> | <span data-ttu-id="f6f38-233">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-233">1.4</span></span> |
|`taskInfo.title`|<span data-ttu-id="f6f38-234">Titel des anfänglichen Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="f6f38-234">Initial task module title.</span></span> |<span data-ttu-id="f6f38-235">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-235">No</span></span> | <span data-ttu-id="f6f38-236">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-236">1.4</span></span> |
|`taskInfo.width`|<span data-ttu-id="f6f38-237">Breite des Aufgabenmoduls, entweder eine Zahl in Pixel oder ein Standardlayout wie `large` , `medium` oder `small` .</span><span class="sxs-lookup"><span data-stu-id="f6f38-237">Task module width, either a number in pixels or default layout such as `large`, `medium`, or `small`.</span></span> |<span data-ttu-id="f6f38-238">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-238">No</span></span> | <span data-ttu-id="f6f38-239">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-239">1.4</span></span> |
|`taskInfo.height`|<span data-ttu-id="f6f38-240">Höhe des Aufgabenmoduls, entweder eine Zahl in Pixel oder ein Standardlayout wie `large` , `medium` oder `small` .</span><span class="sxs-lookup"><span data-stu-id="f6f38-240">Task module height, either a number in pixels or default layout such as `large`, `medium`, or `small`.</span></span>|<span data-ttu-id="f6f38-241">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-241">No</span></span> | <span data-ttu-id="f6f38-242">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-242">1.4</span></span> |
|`taskInfo.url`|<span data-ttu-id="f6f38-243">Anfängliche Webansichts-URL.</span><span class="sxs-lookup"><span data-stu-id="f6f38-243">Initial web view URL.</span></span>|<span data-ttu-id="f6f38-244">Nein</span><span class="sxs-lookup"><span data-stu-id="f6f38-244">No</span></span> | <span data-ttu-id="f6f38-245">1.4</span><span class="sxs-lookup"><span data-stu-id="f6f38-245">1.4</span></span> | 

#### <a name="app-manifest-example"></a><span data-ttu-id="f6f38-246">Beispiel für ein App-Manifest</span><span class="sxs-lookup"><span data-stu-id="f6f38-246">App manifest example</span></span>

<span data-ttu-id="f6f38-247">Der folgende Abschnitt ist ein Beispiel für ein `composeExtensions` Objekt, das zwei Aktionsbefehle definiert.</span><span class="sxs-lookup"><span data-stu-id="f6f38-247">The following section is an example of a `composeExtensions` object defining two action commands.</span></span> <span data-ttu-id="f6f38-248">Es ist kein Beispiel für das vollständige Manifest.</span><span class="sxs-lookup"><span data-stu-id="f6f38-248">It is not an example of the complete manifest.</span></span> <span data-ttu-id="f6f38-249">Das vollständige App-Manifestschema finden Sie unter [App-Manifestschema](~/resources/schema/manifest-schema.md):</span><span class="sxs-lookup"><span data-stu-id="f6f38-249">For the complete app manifest schema, see [app manifest schema](~/resources/schema/manifest-schema.md):</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="f6f38-250">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f6f38-250">Code sample</span></span>

| <span data-ttu-id="f6f38-251">Beispielname</span><span class="sxs-lookup"><span data-stu-id="f6f38-251">Sample Name</span></span>           | <span data-ttu-id="f6f38-252">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f6f38-252">Description</span></span> | <span data-ttu-id="f6f38-253">.NET</span><span class="sxs-lookup"><span data-stu-id="f6f38-253">.NET</span></span>    | <span data-ttu-id="f6f38-254">Node.js</span><span class="sxs-lookup"><span data-stu-id="f6f38-254">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="f6f38-255">Messagingerweiterungsaktion für Teams</span><span class="sxs-lookup"><span data-stu-id="f6f38-255">Teams messaging extension action</span></span>| <span data-ttu-id="f6f38-256">Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren.</span><span class="sxs-lookup"><span data-stu-id="f6f38-256">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="f6f38-257">View</span><span class="sxs-lookup"><span data-stu-id="f6f38-257">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="f6f38-258">View</span><span class="sxs-lookup"><span data-stu-id="f6f38-258">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="f6f38-259">Suche nach Messagingerweiterungen in Teams</span><span class="sxs-lookup"><span data-stu-id="f6f38-259">Teams messaging extension search</span></span>   |  <span data-ttu-id="f6f38-260">Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.</span><span class="sxs-lookup"><span data-stu-id="f6f38-260">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="f6f38-261">View</span><span class="sxs-lookup"><span data-stu-id="f6f38-261">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="f6f38-262">View</span><span class="sxs-lookup"><span data-stu-id="f6f38-262">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="f6f38-263">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="f6f38-263">Next step</span></span>

<span data-ttu-id="f6f38-264">Wenn Sie entweder eine adaptive Karte oder eine eingebettete Webansicht ohne Objekt verwenden, ist `taskInfo` der nächste Schritt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-264">If you are using either an Adaptive Card or an embedded web view without a `taskInfo` object, the next step is to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f6f38-265">Erstellen und Reagieren mit einem Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="f6f38-265">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/create-task-module.md)

<span data-ttu-id="f6f38-266">Wenn Sie die Parameter oder eine eingebettete Webansicht mit einem Objekt `taskInfo` verwenden, ist der nächste Schritt:</span><span class="sxs-lookup"><span data-stu-id="f6f38-266">If you are using the parameters or an embedded web view with a `taskInfo` object, the next step is to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f6f38-267">Reagieren auf Absenden des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="f6f38-267">Respond to task module submit</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

