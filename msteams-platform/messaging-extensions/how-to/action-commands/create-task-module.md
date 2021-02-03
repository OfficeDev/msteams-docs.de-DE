---
title: Erstellen und Senden des Aufgabenmoduls
author: clearab
description: Behandeln der anfänglichen Aufrufaktion und Reagieren mit einem Aufgabenmodul über einen Befehl für eine Aktions-Messaging-Erweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 58fb7e1ff5690b33c2e23f68529f05869afa9016
ms.sourcegitcommit: ce74f821660b1258c72b3c3f71c1cf177e7e92ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2021
ms.locfileid: "50072875"
---
# <a name="create-and-send-the-task-module"></a><span data-ttu-id="1619c-103">Erstellen und Senden des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="1619c-103">Create and send the task module</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="1619c-104">Wenn Sie das Aufgabenmodul nicht mit Parametern auffüllen, die im App-Manifest definiert sind, müssen Sie das Aufgabenmodul für Benutzer erstellen.</span><span class="sxs-lookup"><span data-stu-id="1619c-104">If you are not populating the task module with parameters defined in the app manifest, you must create the task module for users.</span></span> <span data-ttu-id="1619c-105">Verwenden Sie entweder eine adaptive Karte oder eine eingebettete Webansicht.</span><span class="sxs-lookup"><span data-stu-id="1619c-105">Use either an Adaptive Card or an embedded web view.</span></span>

## <a name="the-initial-invoke-request"></a><span data-ttu-id="1619c-106">Die ursprüngliche Aufrufanforderung</span><span class="sxs-lookup"><span data-stu-id="1619c-106">The initial invoke request</span></span>

<span data-ttu-id="1619c-107">Bei Verwendung dieser Methode erhält Ihr Dienst ein Objekt vom Typ, und Sie müssen mit einem Objekt antworten, das entweder die adaptive Karte oder eine URL zur eingebetteten `Activity` `composeExtension/fetchTask` `task` Webansicht enthält.</span><span class="sxs-lookup"><span data-stu-id="1619c-107">Using this method your service will receive an `Activity` object of type `composeExtension/fetchTask`, and you must respond with a `task` object containing either the adaptive card or a URL to the embedded web view.</span></span> <span data-ttu-id="1619c-108">Zusammen mit den standardmäßigen Botaktivitätseigenschaften enthält die ursprüngliche Aufrufnutzlast die folgenden Anforderungsmetadaten:</span><span class="sxs-lookup"><span data-stu-id="1619c-108">Along with the standard bot activity properties, the initial invoke payload contains the following request metadata:</span></span>

|<span data-ttu-id="1619c-109">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-109">Property name</span></span>|<span data-ttu-id="1619c-110">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-110">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-111">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="1619c-111">Type of request.</span></span> <span data-ttu-id="1619c-112">Es muss sein `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1619c-112">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="1619c-113">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-113">Type of command that is issued to your service.</span></span> <span data-ttu-id="1619c-114">Es muss sein `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="1619c-114">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="1619c-115">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-115">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="1619c-116">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-116">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="1619c-117">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-117">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="1619c-118">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="1619c-118">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="1619c-119">Kanal-ID (wenn die Anforderung in einem Kanal gestellt wurde).</span><span class="sxs-lookup"><span data-stu-id="1619c-119">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="1619c-120">Team-ID (wenn die Anforderung in einem Kanal gestellt wurde).</span><span class="sxs-lookup"><span data-stu-id="1619c-120">Team ID (if the request was made in a channel).</span></span> |
|`value.commandId` | <span data-ttu-id="1619c-121">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="1619c-121">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="1619c-122">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-122">The context that triggered the event.</span></span> <span data-ttu-id="1619c-123">Es muss sein `compose` .</span><span class="sxs-lookup"><span data-stu-id="1619c-123">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="1619c-124">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="1619c-124">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="1619c-125">Es muss sein `default` , `contrast` oder `dark` .</span><span class="sxs-lookup"><span data-stu-id="1619c-125">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-11-chat-are-listed-in-the-following-section"></a><span data-ttu-id="1619c-126">Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus dem 1:1-Chat werden im folgenden Abschnitt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="1619c-126">Payload activity properties when invoked a task module from 1:1 chat are listed in the following section:</span></span>

|<span data-ttu-id="1619c-127">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-127">Property name</span></span>|<span data-ttu-id="1619c-128">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-128">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-129">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="1619c-129">Type of request.</span></span> <span data-ttu-id="1619c-130">Es muss sein `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1619c-130">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="1619c-131">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-131">Type of command that is issued to your service.</span></span> <span data-ttu-id="1619c-132">Es muss sein `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="1619c-132">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="1619c-133">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-133">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="1619c-134">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-134">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="1619c-135">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-135">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="1619c-136">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="1619c-136">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="1619c-137">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-137">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="1619c-138">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="1619c-138">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="1619c-139">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="1619c-139">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="1619c-140">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-140">The context that triggered the event.</span></span> <span data-ttu-id="1619c-141">Es muss sein `compose` .</span><span class="sxs-lookup"><span data-stu-id="1619c-141">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="1619c-142">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="1619c-142">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="1619c-143">Es muss sein `default` , `contrast` oder `dark` .</span><span class="sxs-lookup"><span data-stu-id="1619c-143">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-group-chat-are-listed-in-the-following-section"></a><span data-ttu-id="1619c-144">Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem Gruppenchat werden im folgenden Abschnitt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="1619c-144">Payload activity properties when invoked a task module from a group chat are listed in the following section:</span></span>

|<span data-ttu-id="1619c-145">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-145">Property name</span></span>|<span data-ttu-id="1619c-146">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-146">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-147">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="1619c-147">Type of request.</span></span> <span data-ttu-id="1619c-148">Es muss sein `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1619c-148">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="1619c-149">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-149">Type of command that is issued to your service.</span></span> <span data-ttu-id="1619c-150">Es muss sein `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="1619c-150">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="1619c-151">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-151">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="1619c-152">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-152">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="1619c-153">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-153">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="1619c-154">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="1619c-154">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="1619c-155">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-155">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="1619c-156">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="1619c-156">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="1619c-157">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="1619c-157">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="1619c-158">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-158">The context that triggered the event.</span></span> <span data-ttu-id="1619c-159">Es muss sein `compose` .</span><span class="sxs-lookup"><span data-stu-id="1619c-159">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="1619c-160">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="1619c-160">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="1619c-161">Es muss sein `default` , `contrast` oder `dark` .</span><span class="sxs-lookup"><span data-stu-id="1619c-161">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-new-post-are-listed-in-the-following-section"></a><span data-ttu-id="1619c-162">Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem Kanal (neuer Beitrag) sind im folgenden Abschnitt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="1619c-162">Payload activity properties when invoked a task module from a channel (new post) are listed in the following section:</span></span>

|<span data-ttu-id="1619c-163">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-163">Property name</span></span>|<span data-ttu-id="1619c-164">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-164">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-165">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="1619c-165">Type of request.</span></span> <span data-ttu-id="1619c-166">Es muss sein `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1619c-166">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="1619c-167">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-167">Type of command that is issued to your service.</span></span> <span data-ttu-id="1619c-168">Es muss sein `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="1619c-168">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="1619c-169">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-169">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="1619c-170">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-170">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="1619c-171">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-171">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="1619c-172">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="1619c-172">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="1619c-173">Kanal-ID (wenn die Anforderung in einem Kanal gestellt wurde).</span><span class="sxs-lookup"><span data-stu-id="1619c-173">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="1619c-174">Team-ID (wenn die Anforderung in einem Kanal gestellt wurde).</span><span class="sxs-lookup"><span data-stu-id="1619c-174">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="1619c-175">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-175">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="1619c-176">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="1619c-176">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="1619c-177">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="1619c-177">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="1619c-178">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-178">The context that triggered the event.</span></span> <span data-ttu-id="1619c-179">Es muss sein `compose` .</span><span class="sxs-lookup"><span data-stu-id="1619c-179">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="1619c-180">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="1619c-180">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="1619c-181">Es muss sein `default` , `contrast` oder `dark` .</span><span class="sxs-lookup"><span data-stu-id="1619c-181">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-reply-to-thread-are-listed-in-the-following-section"></a><span data-ttu-id="1619c-182">Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem Kanal (Antwort an Thread) sind im folgenden Abschnitt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="1619c-182">Payload activity properties when invoked a task module from a channel (reply to thread) are listed in the following section:</span></span>

|<span data-ttu-id="1619c-183">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-183">Property name</span></span>|<span data-ttu-id="1619c-184">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-184">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-185">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="1619c-185">Type of request.</span></span> <span data-ttu-id="1619c-186">Es muss sein `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1619c-186">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="1619c-187">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-187">Type of command that is issued to your service.</span></span> <span data-ttu-id="1619c-188">Es muss sein `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="1619c-188">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="1619c-189">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-189">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="1619c-190">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-190">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="1619c-191">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-191">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="1619c-192">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="1619c-192">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="1619c-193">Kanal-ID (wenn die Anforderung in einem Kanal gestellt wurde).</span><span class="sxs-lookup"><span data-stu-id="1619c-193">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="1619c-194">Team-ID (wenn die Anforderung in einem Kanal gestellt wurde).</span><span class="sxs-lookup"><span data-stu-id="1619c-194">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="1619c-195">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-195">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="1619c-196">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="1619c-196">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="1619c-197">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="1619c-197">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="1619c-198">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-198">The context that triggered the event.</span></span> <span data-ttu-id="1619c-199">Es muss sein `compose` .</span><span class="sxs-lookup"><span data-stu-id="1619c-199">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="1619c-200">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="1619c-200">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="1619c-201">Es muss sein `default` , `contrast` oder `dark` .</span><span class="sxs-lookup"><span data-stu-id="1619c-201">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-command-box-are-listed-in-the-following-section"></a><span data-ttu-id="1619c-202">Nutzlastaktivitätseigenschaften, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird, sind im folgenden Abschnitt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="1619c-202">Payload activity properties when invoked a task module from a command box are listed in the following section:</span></span>

|<span data-ttu-id="1619c-203">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-203">Property name</span></span>|<span data-ttu-id="1619c-204">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-204">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-205">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="1619c-205">Type of request.</span></span> <span data-ttu-id="1619c-206">Es muss sein `invoke` .</span><span class="sxs-lookup"><span data-stu-id="1619c-206">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="1619c-207">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-207">Type of command that is issued to your service.</span></span> <span data-ttu-id="1619c-208">Es muss sein `composeExtension/fetchTask` .</span><span class="sxs-lookup"><span data-stu-id="1619c-208">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="1619c-209">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-209">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="1619c-210">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-210">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="1619c-211">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-211">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="1619c-212">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="1619c-212">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="1619c-213">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-213">The source name from where task module is invoked.</span></span> |
|`value.commandId` | <span data-ttu-id="1619c-214">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="1619c-214">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="1619c-215">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="1619c-215">The context that triggered the event.</span></span> <span data-ttu-id="1619c-216">Es muss sein `compose` .</span><span class="sxs-lookup"><span data-stu-id="1619c-216">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="1619c-217">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="1619c-217">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="1619c-218">Es muss sein `default` , `contrast` oder `dark` .</span><span class="sxs-lookup"><span data-stu-id="1619c-218">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example-fetchtask-request"></a><span data-ttu-id="1619c-219">Beispiel für fetchTask-Anforderung</span><span class="sxs-lookup"><span data-stu-id="1619c-219">Example fetchTask request</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1619c-220">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1619c-220">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1619c-221">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1619c-221">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[<span data-ttu-id="1619c-222">Json</span><span class="sxs-lookup"><span data-stu-id="1619c-222">JSON</span></span>](#tab/json)

```json
{
  "name": "composeExtension/fetchTask",
  "type": "invoke",
  "timestamp": "2019-07-01T22:57:22.175Z",
  "localTimestamp": "2019-07-01T15:57:22.175-07:00",
  "id": "f:0123456878990178955",
  "channelId": "msteams",
  "serviceURL": "https://smba.trafficmanager.net/amer/",
  "from": {
    "id": "29:1test2GgHIa0DXzDT_OGwL5vSMZdAxDlGR7hYxZ6_JBVqHz2Zq9Nm44FUNWqHCdGBwHg8WrlFRsYrd0cCAS7dig",
    "name": "John Smith",
    "aadObjectId": "1234567d-1234-462a-8952-35b75f16f1e1"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "tenantId": "1234abcd-1234-12ab-12ab-35b75f16f1e1",
    "id": "19:83ed1d507cb5427c93495cf914326310@thread.skype"
  },
  "recipient": {
    "id": "28:049566e0-4401-4bcf-86a1-ce22082ce03a",
    "name": "mess"
  },
  "entities": [
    {
      "locale": "en-US",
      "country": "US",
      "platform": "Windows",
      "type": "clientInfo"
    }
  ],
  "channelData": {
    "channel": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "team": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "tenant": {
      "id": "1234abcd-1234-12ab-12ab-35b75f16f1e1"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "hello",
    "commandContext": "compose",
    "context": {
      "theme": "dark"
    }
  },
  "locale": "en-US"
}
```

* * *

## <a name="initial-invoke-request-from-a-message"></a><span data-ttu-id="1619c-223">Ursprüngliche Aufrufanforderung aus einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="1619c-223">Initial invoke request from a message</span></span>

<span data-ttu-id="1619c-224">Wenn Ihr Bot von einer Nachricht und nicht vom Bereich zum Verfassen oder von der Befehlsleiste aufgerufen wird, muss das Objekt in der ursprünglichen Anforderung die Details der Nachricht enthalten, aus der Ihre Messagingerweiterung `value` aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1619c-224">When your bot is invoked from a message rather than the compose area or the command bar, the `value` object in the initial request must contain the details of the message your messaging extension is invoked from.</span></span> <span data-ttu-id="1619c-225">Im folgenden Abschnitt finden Sie ein Beispiel für dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="1619c-225">See the following section  for the example of this object .</span></span> <span data-ttu-id="1619c-226">Die Arrays und Arrays sind optional und sind nicht vorhanden, wenn in der ursprünglichen Nachricht keine Reaktionen oder `reactions` `mentions` Erwähnungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="1619c-226">The `reactions` and `mentions` arrays are optional, and they are not present if there are no reactions or mentions in the original message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1619c-227">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1619c-227">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1619c-228">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1619c-228">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[<span data-ttu-id="1619c-229">Json</span><span class="sxs-lookup"><span data-stu-id="1619c-229">JSON</span></span>](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
...
  "value": {
    "commandId": "setReminder",
    "commandContext": "message",
    "messagePayload": {
      "id": "1111111111",
      "replyToId": null,
      "createdDateTime": "2019-02-25T21:29:36.065Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "subject": "Message subject",
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "This is the message the messaging extension was invoked from."
    },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "wxyz12ab8-ab12-cd34-ef56-098abc123876",
          "displayName": "Jamie Smythe"
        },
        "application": null
      },
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2019-02-25T22:40:40.806Z",
          "user": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "qrst12346-ab12-cd34-ef56-098abc123876",
              "displayName": "Jim Brown"
            },
            "application": null
          }
        }
      ],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Sarah",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "ab12345678-ab12-cd34-ef56-098abc123876",
              "displayName": "Sarah"
            },
            "application": null
          }
        }
      ]
    }
  ...
```

* * *

## <a name="respond-to-the-fetchtask"></a><span data-ttu-id="1619c-230">Antworten auf "fetchTask"</span><span class="sxs-lookup"><span data-stu-id="1619c-230">Respond to the fetchTask</span></span>

<span data-ttu-id="1619c-231">Reagieren Sie auf die Aufrufanforderung mit einem Objekt, das entweder ein Objekt mit der adaptiven Karte oder Web-URL oder eine einfache `task` `taskInfo` Zeichenfolgennachricht enthält.</span><span class="sxs-lookup"><span data-stu-id="1619c-231">Respond to the invoke request with a `task` object that contains either a `taskInfo` object with the adaptive card or web URL, or a simple string message.</span></span>

|<span data-ttu-id="1619c-232">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-232">Property name</span></span>|<span data-ttu-id="1619c-233">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-233">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="1619c-234">Dies kann entweder `continue` sein, um ein Formular oder ein `message` einfaches Popup zu präsentieren.</span><span class="sxs-lookup"><span data-stu-id="1619c-234">Can be either `continue` to present a form, or `message` for a simple popup.</span></span> |
|`value`| <span data-ttu-id="1619c-235">Entweder ein `taskInfo` Objekt für ein Formular oder ein Objekt für eine `string` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="1619c-235">Either a `taskInfo` object for a form, or a `string` for a message.</span></span> |

<span data-ttu-id="1619c-236">Das Schema für das taskInfo -Objekt ist:</span><span class="sxs-lookup"><span data-stu-id="1619c-236">The schema for the taskInfo object is:</span></span>

|<span data-ttu-id="1619c-237">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="1619c-237">Property name</span></span>|<span data-ttu-id="1619c-238">Zweck</span><span class="sxs-lookup"><span data-stu-id="1619c-238">Purpose</span></span>|
|---|---|
|`title`| <span data-ttu-id="1619c-239">Der Titel des Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="1619c-239">The title of the task module.</span></span>|
|`height`| <span data-ttu-id="1619c-240">Es muss entweder eine ganze Zahl (in Pixel) oder `small` , `medium` `large` sein.</span><span class="sxs-lookup"><span data-stu-id="1619c-240">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`width`| <span data-ttu-id="1619c-241">Es muss entweder eine ganze Zahl (in Pixel) oder `small` , `medium` `large` sein.</span><span class="sxs-lookup"><span data-stu-id="1619c-241">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`card`| <span data-ttu-id="1619c-242">Die adaptive Karte, die das Formular definiert (bei Verwendung eines Formulars).</span><span class="sxs-lookup"><span data-stu-id="1619c-242">The adaptive card defining the form (if using one).</span></span>
|`url`| <span data-ttu-id="1619c-243">Die URL, die innerhalb des Aufgabenmoduls als eingebettete Webansicht geöffnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="1619c-243">The URL to be opened inside of the task module as an embedded web view.</span></span>|
|`fallbackUrl`| <span data-ttu-id="1619c-244">Wenn ein Client das Aufgabenmodulfeature nicht unterstützt, wird diese URL auf einer Browserregisterkarte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="1619c-244">If a client does not support the task module feature, this URL is opened in a browser tab.</span></span> |

### <a name="with-an-adaptive-card"></a><span data-ttu-id="1619c-245">Mit einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="1619c-245">With an adaptive card</span></span>

<span data-ttu-id="1619c-246">Wenn Sie eine adaptive Karte verwenden, müssen Sie mit einem Objekt mit dem Objekt `task` `value` antworten, das eine adaptive Karte enthält.</span><span class="sxs-lookup"><span data-stu-id="1619c-246">When using an adaptive card, you must respond with a `task` object with the `value` object containing an adaptive card.</span></span>

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a><span data-ttu-id="1619c-247">Beispiel für fetchTask-Antwort mit einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="1619c-247">Example fetchTask response with an adaptive card</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1619c-248">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1619c-248">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="1619c-249">In diesem Beispiel wird das [AdaptiveCards-NuGet-Paket](https://www.nuget.org/packages/AdaptiveCards) zusätzlich zum Bot Framework SDK verwendet.</span><span class="sxs-lookup"><span data-stu-id="1619c-249">This sample uses the [AdaptiveCards NuGet package](https://www.nuget.org/packages/AdaptiveCards) in addition to the Bot Framework SDK.</span></span>

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Card = new Attachment()
        {
          ContentType = AdaptiveCard.ContentType,
          Content = new AdaptiveCard("1.0")
          {
            Body = new List<AdaptiveElement>()
            {
              new AdaptiveTextInput() { Id = "FormField1", Placeholder = placeholder},
              new AdaptiveTextInput() { Id = "FormField2", Placeholder = "FormField2"},
              new AdaptiveTextInput() { Id = "FormField3", Placeholder = "FormField3"},
            },
            Actions = new List<AdaptiveAction>()
            {
              new AdaptiveSubmitAction()
              {
                Type = AdaptiveSubmitAction.TypeName,
                Title = "Submit",
              },
            },
          },
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1619c-250">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1619c-250">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    handleTeamsMessagingExtensionFetchTask(context, action) {
      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [{
          data: { submitLocation: 'messagingExtensionFetchTask'},
          title: 'Submit',
          type: 'Action.Submit'
        }],
        body: [
          { text: 'Task Module', type: 'TextBlock', weight: 'bolder'},
          { type: 'TextBlock', text: 'Enter text for Question:' },
          { id: 'Question', placeholder: 'Question text here', type: 'Input.Text', value: userText },
          { type: 'TextBlock', text: 'Options for Question:' },
          { type: 'TextBlock', text: 'Is Multi-Select:' },
          {
            choices: [{ title: 'True', value: 'true' }, { title: 'False', value: 'false' }],
            id: 'MultiSelect',
            isMultiSelect: false,
            style: 'expanded',
            type: 'Input.ChoiceSet',
            value: isMultiSelect ? 'true' : 'false'
          },
          { id: 'Option1', placeholder: 'Option 1 here', type: 'Input.Text', value: option1 },
          { id: 'Option2', placeholder: 'Option 2 here', type: 'Input.Text', value: option2 }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });

      return {
        task: {
          type: 'continue',
          value: {
            card: adaptiveCard,
            height: 450,
            title: 'Task Module Fetch Example',
            url: null,
            width: 500
          }
        }
      };
    }
}
```

# <a name="json"></a>[<span data-ttu-id="1619c-251">Json</span><span class="sxs-lookup"><span data-stu-id="1619c-251">JSON</span></span>](#tab/json)

```json
 {
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "card": {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Input.Text",
            "placeholder": "FormField1",
            "id": "FormField1"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField2",
            "id": "FormField2"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField3",
            "id": "FormField3"
          },
          {
            "type": "ActionSet",
            "actions": [
              {
                "type": "Action.Submit",
                "title": "Action.Submit",
                "id": "submitAction"
              }
            ]
          }
        ]
      }
    }
  }
}
```

* * *

### <a name="with-an-embedded-web-view"></a><span data-ttu-id="1619c-252">Mit einer eingebetteten Webansicht</span><span class="sxs-lookup"><span data-stu-id="1619c-252">With an embedded web view</span></span>

<span data-ttu-id="1619c-253">Wenn Sie eine eingebettete Webansicht verwenden, müssen Sie mit einem Objekt mit dem Objekt antworten, das die URL zu dem Webformular enthält, das `task` `value` Sie laden möchten.</span><span class="sxs-lookup"><span data-stu-id="1619c-253">When using an embedded web view, you must respond with a `task` object with the `value` object containing the URL to the web form you'd like to load.</span></span> <span data-ttu-id="1619c-254">Die Domänen aller URLs, die Sie laden möchten, müssen im Array im Manifest Ihrer `validDomains` App enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="1619c-254">The domains of any URL you want to load must be included in the `validDomains` array in your app's manifest.</span></span> <span data-ttu-id="1619c-255">Vollständige Informationen [zum](~/task-modules-and-cards/what-are-task-modules.md) Erstellen der eingebetteten Webansicht finden Sie in der Dokumentation zum Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="1619c-255">See the [task module documentation](~/task-modules-and-cards/what-are-task-modules.md) for complete information on building your embedded web view.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1619c-256">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1619c-256">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Url = "https://contoso.com/msteams/taskmodules/newcustomer",
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1619c-257">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1619c-257">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    return {
      task: {
        type: 'continue',
        value: {
          width: 500,
          height: 450,
          title: 'Task Module Fetch Example',
          url: 'https://contoso.com/msteams/taskmodules/newcustomer',
          fallbackUrl: 'https://contoso.com/msteams/taskmodules/newcustomer'
        }
      }
    };
  }
}
```

# <a name="json"></a>[<span data-ttu-id="1619c-258">Json</span><span class="sxs-lookup"><span data-stu-id="1619c-258">JSON</span></span>](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "url": "https://contoso.com/msteams/taskmodules/newcustomer",
      "fallbackUrl": "https://contoso.com/msteams/taskmodules/newcustomer"
    }
  }
}
```

* * *

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="1619c-259">Anfordern der Installation Ihres Unterhaltungsbots</span><span class="sxs-lookup"><span data-stu-id="1619c-259">Request to install your conversational bot</span></span>

<span data-ttu-id="1619c-260">Wenn die App einen Unterhaltungsbot enthält, installieren Sie den Bot in der Unterhaltung, bevor Sie das Aufgabenmodul laden.</span><span class="sxs-lookup"><span data-stu-id="1619c-260">If the app contains a conversational bot, install the bot in the conversation before loading the task module.</span></span> <span data-ttu-id="1619c-261">Es ist hilfreich, zusätzlichen Kontext für das Aufgabenmodul zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1619c-261">It is useful to get additional context for the task module.</span></span> <span data-ttu-id="1619c-262">Ein typisches Beispiel für dieses Szenario ist das Abrufen der Liste zum Auffüllen eines Personenauswahlsteuerelements oder der Liste der Kanäle in einem Team.</span><span class="sxs-lookup"><span data-stu-id="1619c-262">Typical example for this scenario is to fetch the roster to populate a people picker control or the list of channels in a team.</span></span>

<span data-ttu-id="1619c-263">Wenn die Messagingerweiterung den Aufruf empfängt, überprüfen Sie, ob der Bot im aktuellen Kontext installiert ist, `composeExtension/fetchTask` um den Fluss zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="1619c-263">When the messaging extension receives the `composeExtension/fetchTask` invoke, check if the bot is installed in the current context to facilitate the flow.</span></span> <span data-ttu-id="1619c-264">Überprüfen Sie z. B. den Ablauf mit einem Anruf zum Abruf der Dienstliste.</span><span class="sxs-lookup"><span data-stu-id="1619c-264">For example, check the flow with a get roster call.</span></span> <span data-ttu-id="1619c-265">Wenn der Bot nicht installiert ist, geben Sie eine adaptive Karte mit einer Aktion zurück, die den Benutzer zur Installation des Bots anfordert.</span><span class="sxs-lookup"><span data-stu-id="1619c-265">If the bot is not installed, return an Adaptive Card with an action that requests the user to install the bot.</span></span> <span data-ttu-id="1619c-266">Siehe die Aktion im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="1619c-266">See the action in the following example.</span></span> <span data-ttu-id="1619c-267">Der Benutzer muss zum Überprüfen über die Berechtigung zum Installieren der Apps an diesem Speicherort verfügen.</span><span class="sxs-lookup"><span data-stu-id="1619c-267">The user must have permission to install the apps in that location for checking.</span></span> <span data-ttu-id="1619c-268">Wenn die Installation der App nicht erfolgreich ist, erhält der Benutzer eine Meldung, um sich an den Administrator zu wenden.</span><span class="sxs-lookup"><span data-stu-id="1619c-268">If the app installation is unsuccessful, the user receives a message to contact the administrator.</span></span>

#### <a name="example-of-the-response"></a><span data-ttu-id="1619c-269">Beispiel für die Antwort:</span><span class="sxs-lookup"><span data-stu-id="1619c-269">Example of the response:</span></span>

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Looks like you haven't used Disco in this team/chat"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Continue",
      "data": {
        "msteams": {
          "justInTimeInstall": true
        }
      }
    }
  ],
  "version": "1.0"
}
```

<span data-ttu-id="1619c-270">Nach der Installation empfängt der Bot eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` und `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="1619c-270">After the installation, the bot receives another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

#### <a name="example-of-the-invoke"></a><span data-ttu-id="1619c-271">Beispiel für den Aufruf:</span><span class="sxs-lookup"><span data-stu-id="1619c-271">Example of the invoke:</span></span>

```json
{
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "msteams": {
        "justInTimeInstall": true
      }
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  },
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith"
}
```

<span data-ttu-id="1619c-272">Die Aufgabenantwort auf den Aufruf muss mit der des installierten Bots vergleichbar sein.</span><span class="sxs-lookup"><span data-stu-id="1619c-272">The task response to the invoke must be similar to that of the installed bot.</span></span>

#### <a name="example-of-just-in-time-installation-of-app-with-adaptive-card"></a><span data-ttu-id="1619c-273">Beispiel für die Just-In-Time-Installation der App mit adaptiver Karte:</span><span class="sxs-lookup"><span data-stu-id="1619c-273">Example of just-in time installation of app with Adaptive card:</span></span> 

```csharp
private static Attachment GetAdaptiveCardAttachmentFromFile(string fileName)
  {
      //Read the card json and create attachment.
         string[] paths = { ".", "Resources", fileName };
         var adaptiveCardJson = File.ReadAllText(Path.Combine(paths));
         var adaptiveCardAttachment = new Attachment()
            {
                ContentType = "application/vnd.microsoft.card.adaptive",
                Content = JsonConvert.DeserializeObject(adaptiveCardJson),
            };
            return adaptiveCardAttachment;
        }
```

* * *

## <a name="next-steps"></a><span data-ttu-id="1619c-274">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="1619c-274">Next steps</span></span>

<span data-ttu-id="1619c-275">Wenn Sie Ihren Benutzern erlauben, eine Antwort vom Aufgabenmodul zurück zu senden, müssen Sie die Sendeaktion verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="1619c-275">If you allow your users to send a response back from the task module, you must handle the submit action.</span></span>

* [<span data-ttu-id="1619c-276">Erstellen und Antworten mit einem Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="1619c-276">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
