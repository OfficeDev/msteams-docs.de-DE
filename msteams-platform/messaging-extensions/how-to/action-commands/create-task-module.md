---
title: Erstellen und Senden des Aufgabenmoduls
author: clearab
description: Behandeln der anfänglichen Aufrufaktion und Reagieren mit einem Aufgabenmodul über einen Befehl zur Aktionserweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 12af2d788c0579414b544e7e2fd7f07a77d45919
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696276"
---
# <a name="create-and-send-the-task-module"></a><span data-ttu-id="8a128-103">Erstellen und Senden des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="8a128-103">Create and send the task module</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="8a128-104">Sie können das Aufgabenmodul mithilfe einer adaptiven Karte oder einer eingebetteten Webansicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a128-104">You can create the task module using an Adaptive Card or an embedded web view.</span></span> <span data-ttu-id="8a128-105">Zum Erstellen eines Aufgabenmoduls müssen Sie den Prozess ausführen, der als ursprüngliche Aufrufanforderung bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-105">To create a task module, you must perform the process called the initial invoke request.</span></span> <span data-ttu-id="8a128-106">Dieses Dokument behandelt die Eigenschaften der anfänglichen Aufrufanforderung, der Nutzlastaktivität, wenn ein Aufgabenmodul aus 1:1-Chat, Gruppenchat, Kanal (neuer Beitrag), Kanal (Antwort auf Thread) und Befehlsfeld aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-106">This document covers the initial invoke request, payload activity properties when a task module is invoked from 1:1 chat, group chat, channel (new post), channel (reply to thread), and command box.</span></span> 
> [!NOTE]
> <span data-ttu-id="8a128-107">Wenn Sie das Aufgabenmodul nicht mit Parametern füllen, die im App-Manifest definiert sind, müssen Sie das Aufgabenmodul für Benutzer mit einer adaptiven Karte oder einer eingebetteten Webansicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a128-107">If you are not populating the task module with parameters defined in the app manifest, you must create the task module for users with either an Adaptive Card or an embedded web view.</span></span>

## <a name="the-initial-invoke-request"></a><span data-ttu-id="8a128-108">Die anfängliche Aufrufanforderung</span><span class="sxs-lookup"><span data-stu-id="8a128-108">The initial invoke request</span></span>

<span data-ttu-id="8a128-109">Bei der ersten Aufrufanforderung empfängt Ihr Dienst ein Objekt vom Typ , und Sie müssen mit einem Objekt antworten, das entweder eine adaptive Karte oder eine URL für die eingebettete `Activity` `composeExtension/fetchTask` `task` Webansicht enthält.</span><span class="sxs-lookup"><span data-stu-id="8a128-109">In the process of the initial invoke request, your service receives an `Activity` object of type `composeExtension/fetchTask`, and you must respond with a `task` object containing either an Adaptive Card or a URL to the embedded web view.</span></span> <span data-ttu-id="8a128-110">Zusammen mit den standardmäßigen Botaktivitätseigenschaften enthält die ursprüngliche Aufrufnutzlast die folgenden Anforderungsmetadaten:</span><span class="sxs-lookup"><span data-stu-id="8a128-110">Along with the standard bot activity properties, the initial invoke payload contains the following request metadata:</span></span>

|<span data-ttu-id="8a128-111">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-111">Property name</span></span>|<span data-ttu-id="8a128-112">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-112">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-113">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="8a128-113">Type of request.</span></span> <span data-ttu-id="8a128-114">Es muss `invoke` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-114">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="8a128-115">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-115">Type of command that is issued to your service.</span></span> <span data-ttu-id="8a128-116">Es muss `composeExtension/fetchTask` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-116">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="8a128-117">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-117">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="8a128-118">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-118">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="8a128-119">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-119">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="8a128-120">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="8a128-120">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="8a128-121">Kanal-ID (wenn die Anforderung in einem Kanal vorgenommen wurde).</span><span class="sxs-lookup"><span data-stu-id="8a128-121">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="8a128-122">Team-ID (wenn die Anforderung in einem Kanal vorgenommen wurde).</span><span class="sxs-lookup"><span data-stu-id="8a128-122">Team ID (if the request was made in a channel).</span></span> |
|`value.commandId` | <span data-ttu-id="8a128-123">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8a128-123">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="8a128-124">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-124">The context that triggered the event.</span></span> <span data-ttu-id="8a128-125">Es muss `compose` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-125">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="8a128-126">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="8a128-126">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="8a128-127">Es muss `default` sein , oder `contrast` `dark` .</span><span class="sxs-lookup"><span data-stu-id="8a128-127">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="8a128-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-128">Example</span></span>

<span data-ttu-id="8a128-129">Der Code für die anfängliche Aufrufanforderung wird im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="8a128-129">The code for the initial invoke request is given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-11-chat"></a><span data-ttu-id="8a128-130">Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul aus dem 1:1-Chat aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="8a128-130">Payload activity properties when a task module is invoked from 1:1 chat</span></span> 

<span data-ttu-id="8a128-131">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul aus dem 1:1-Chat aufgerufen wird, sind wie folgt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8a128-131">The payload activity properties when a task module is invoked from 1:1 chat are listed as follows:</span></span>

|<span data-ttu-id="8a128-132">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-132">Property name</span></span>|<span data-ttu-id="8a128-133">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-133">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-134">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="8a128-134">Type of request.</span></span> <span data-ttu-id="8a128-135">Es muss `invoke` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-135">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="8a128-136">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-136">Type of command that is issued to your service.</span></span> <span data-ttu-id="8a128-137">Es muss `composeExtension/fetchTask` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-137">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="8a128-138">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-138">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="8a128-139">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-139">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="8a128-140">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-140">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="8a128-141">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="8a128-141">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="8a128-142">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-142">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="8a128-143">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="8a128-143">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="8a128-144">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8a128-144">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="8a128-145">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-145">The context that triggered the event.</span></span> <span data-ttu-id="8a128-146">Es muss `compose` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-146">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="8a128-147">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="8a128-147">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="8a128-148">Es muss `default` sein , oder `contrast` `dark` .</span><span class="sxs-lookup"><span data-stu-id="8a128-148">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="8a128-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-149">Example</span></span>

<span data-ttu-id="8a128-150">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul aus dem 1:1-Chat aufgerufen wird, werden im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="8a128-150">The payload activity properties when a task module is invoked from 1:1 chat are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```
## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-group-chat"></a><span data-ttu-id="8a128-151">Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul aus einem Gruppenchat aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="8a128-151">Payload activity properties when a task module is invoked from a group chat</span></span> 

<span data-ttu-id="8a128-152">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul aus einem Gruppenchat aufgerufen wird, werden wie folgt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8a128-152">The payload activity properties when a task module is invoked from a group chat are listed as follows:</span></span>

|<span data-ttu-id="8a128-153">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-153">Property name</span></span>|<span data-ttu-id="8a128-154">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-154">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-155">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="8a128-155">Type of request.</span></span> <span data-ttu-id="8a128-156">Es muss `invoke` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-156">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="8a128-157">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-157">Type of command that is issued to your service.</span></span> <span data-ttu-id="8a128-158">Es muss `composeExtension/fetchTask` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-158">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="8a128-159">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-159">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="8a128-160">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-160">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="8a128-161">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-161">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="8a128-162">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="8a128-162">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="8a128-163">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-163">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="8a128-164">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="8a128-164">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="8a128-165">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8a128-165">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="8a128-166">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-166">The context that triggered the event.</span></span> <span data-ttu-id="8a128-167">Es muss `compose` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-167">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="8a128-168">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="8a128-168">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="8a128-169">Es muss `default` sein , oder `contrast` `dark` .</span><span class="sxs-lookup"><span data-stu-id="8a128-169">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="8a128-170">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-170">Example</span></span>

<span data-ttu-id="8a128-171">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul aus einem Gruppenchat aufgerufen wird, werden im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="8a128-171">The payload activity properties when a task module is invoked from a group chat are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:bf72031f-a17e-f99c-48dc-5c0714950d87",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "groupChat",
    "id": "19:d77be72390a1416e9644261e9064fa00@thread.skype",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "213167a1e3b6428b93e186ea5407c759",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-new-post"></a><span data-ttu-id="8a128-172">Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (neuer Beitrag)</span><span class="sxs-lookup"><span data-stu-id="8a128-172">Payload activity properties when a task module is invoked from a channel (new post)</span></span> 

<span data-ttu-id="8a128-173">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul von einem Kanal (neuer Beitrag) aufgerufen wird, sind wie folgt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8a128-173">The payload activity properties when a task module is invoked from a channel (new post) are listed as follows:</span></span>

|<span data-ttu-id="8a128-174">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-174">Property name</span></span>|<span data-ttu-id="8a128-175">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-175">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-176">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="8a128-176">Type of request.</span></span> <span data-ttu-id="8a128-177">Es muss `invoke` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-177">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="8a128-178">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-178">Type of command that is issued to your service.</span></span> <span data-ttu-id="8a128-179">Es muss `composeExtension/fetchTask` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-179">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="8a128-180">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-180">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="8a128-181">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-181">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="8a128-182">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-182">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="8a128-183">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="8a128-183">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="8a128-184">Kanal-ID (wenn die Anforderung in einem Kanal vorgenommen wurde).</span><span class="sxs-lookup"><span data-stu-id="8a128-184">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="8a128-185">Team-ID (wenn die Anforderung in einem Kanal vorgenommen wurde).</span><span class="sxs-lookup"><span data-stu-id="8a128-185">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="8a128-186">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-186">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="8a128-187">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="8a128-187">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="8a128-188">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8a128-188">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="8a128-189">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-189">The context that triggered the event.</span></span> <span data-ttu-id="8a128-190">Es muss `compose` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-190">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="8a128-191">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="8a128-191">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="8a128-192">Es muss `default` sein , oder `contrast` `dark` .</span><span class="sxs-lookup"><span data-stu-id="8a128-192">It must be `default`, `contrast`, or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="8a128-193">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-193">Example</span></span>

<span data-ttu-id="8a128-194">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul von einem Kanal (neuer Beitrag) aufgerufen wird, werden im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="8a128-194">The payload activity properties when a task module is invoked from a channel (new post) are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:a5fbb109-c989-c449-ee83-71ac99919d4b",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "5336640edc7748b28ce2df43f5b45963",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-reply-to-thread"></a><span data-ttu-id="8a128-195">Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (An Thread antworten)</span><span class="sxs-lookup"><span data-stu-id="8a128-195">Payload activity properties when a task module is invoked from a channel (reply to thread)</span></span> 

<span data-ttu-id="8a128-196">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (An Thread antworten) sind wie folgt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8a128-196">The payload activity properties when a task module is invoked from a channel (reply to thread) are listed as follows:</span></span>

|<span data-ttu-id="8a128-197">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-197">Property name</span></span>|<span data-ttu-id="8a128-198">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-198">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-199">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="8a128-199">Type of request.</span></span> <span data-ttu-id="8a128-200">Es muss `invoke` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-200">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="8a128-201">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-201">Type of command that is issued to your service.</span></span> <span data-ttu-id="8a128-202">Es muss `composeExtension/fetchTask` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-202">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="8a128-203">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-203">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="8a128-204">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-204">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="8a128-205">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-205">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="8a128-206">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="8a128-206">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="8a128-207">Kanal-ID (wenn die Anforderung in einem Kanal vorgenommen wurde).</span><span class="sxs-lookup"><span data-stu-id="8a128-207">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="8a128-208">Team-ID (wenn die Anforderung in einem Kanal vorgenommen wurde).</span><span class="sxs-lookup"><span data-stu-id="8a128-208">Team ID (if the request was made in a channel).</span></span> |
|`channelData.source.name`| <span data-ttu-id="8a128-209">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-209">The source name from where task module is invoked.</span></span> |
|`ChannelData.legacy. replyToId`| <span data-ttu-id="8a128-210">Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest.</span><span class="sxs-lookup"><span data-stu-id="8a128-210">Gets or sets the ID of the message to which this message is a reply.</span></span> |
|`value.commandId` | <span data-ttu-id="8a128-211">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8a128-211">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="8a128-212">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-212">The context that triggered the event.</span></span> <span data-ttu-id="8a128-213">Es muss `compose` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-213">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="8a128-214">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="8a128-214">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="8a128-215">Es muss `default` sein , oder `contrast` `dark` .</span><span class="sxs-lookup"><span data-stu-id="8a128-215">It must be `default`, `contrast` or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="8a128-216">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-216">Example</span></span>

<span data-ttu-id="8a128-217">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (An Thread antworten) werden im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="8a128-217">The payload activity properties when a task module is invoked from a channel (reply to thread) are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:19ccc884-c792-35ef-2f40-d0ff43dcca71",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype;messageid=1611060744833",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "message",
    "requestId": "7f7d22efe5414818becebcec649a7912",
    "messagePayload": {
      "linkToMessage": "https://teams.microsoft.com/l/message/19:6decf54d86d945e4b3924b63a9161a78@thread.skype/1611060744833",
      "id": "1611060744833",
      "replyToId": null,
      "createdDateTime": "2021-01-19T12:52:24.833Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "<div><div><at id=\"0\">Testing outgoing Webhook-Nikitha</at> - Hi</div>\n</div>"
      },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc",
          "displayName": "Olo Brockhouse"
        },
        "application": null
      },
      "reactions": [],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Testing outgoing Webhook-Nikitha",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": null,
            "application": {
              "applicationIdentityType": "webhook",
              "id": "b8c1c68c-e290-4bdd-81c3-266f310751dc",
              "displayName": "Testing outgoing Webhook-Nikitha"
            }
          }
        }
      ],
      "attachments": []
    },
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-command-box"></a><span data-ttu-id="8a128-218">Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird</span><span class="sxs-lookup"><span data-stu-id="8a128-218">Payload activity properties when a task module is invoked from a command box</span></span> 

<span data-ttu-id="8a128-219">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird, sind wie folgt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8a128-219">The payload activity properties when a task module is invoked from a command box are listed as follows:</span></span>

|<span data-ttu-id="8a128-220">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-220">Property name</span></span>|<span data-ttu-id="8a128-221">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-221">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-222">Anforderungstyp.</span><span class="sxs-lookup"><span data-stu-id="8a128-222">Type of request.</span></span> <span data-ttu-id="8a128-223">Es muss `invoke` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-223">It must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="8a128-224">Typ des Befehls, der für Ihren Dienst ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-224">Type of command that is issued to your service.</span></span> <span data-ttu-id="8a128-225">Es muss `composeExtension/fetchTask` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-225">It must be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="8a128-226">ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-226">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="8a128-227">Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-227">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="8a128-228">Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-228">Azure Active Directory object ID of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="8a128-229">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="8a128-229">Azure Active Directory tenant ID.</span></span> |
|`channelData.source.name`| <span data-ttu-id="8a128-230">Der Quellname, von dem aus das Aufgabenmodul aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-230">The source name from where task module is invoked.</span></span> |
|`value.commandId` | <span data-ttu-id="8a128-231">Enthält die ID des Befehls, der aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="8a128-231">Contains the ID of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="8a128-232">Der Kontext, der das Ereignis ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="8a128-232">The context that triggered the event.</span></span> <span data-ttu-id="8a128-233">Es muss `compose` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-233">It must be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="8a128-234">Das Clientdesign des Benutzers, nützlich für die Formatierung eingebetteter Webansichten.</span><span class="sxs-lookup"><span data-stu-id="8a128-234">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="8a128-235">Es muss `default` sein , oder `contrast` `dark` .</span><span class="sxs-lookup"><span data-stu-id="8a128-235">It must be `default`, `contrast`, or `dark`.</span></span> |

### <a name="example"></a><span data-ttu-id="8a128-236">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-236">Example</span></span>

<span data-ttu-id="8a128-237">Die Eigenschaften der Nutzlastaktivität, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird, werden im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="8a128-237">The payload activity properties when a task module is invoked from a command box are given in the following example:</span></span>

```json
{
  "type": "invoke",
  "id": "f:172560f1-95f9-3189-edb2-b7612cd1a3cd",
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "compose",
    "requestId": "d2ce690cdc2b4920a538e75882610a30",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

### <a name="example"></a><span data-ttu-id="8a128-238">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-238">Example</span></span> 

<span data-ttu-id="8a128-239">Der folgende Codeabschnitt ist ein Beispiel für `fetchTask` eine Anforderung:</span><span class="sxs-lookup"><span data-stu-id="8a128-239">The following code section is an example of `fetchTask` request:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8a128-240">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8a128-240">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="8a128-241">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8a128-241">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[<span data-ttu-id="8a128-242">Json</span><span class="sxs-lookup"><span data-stu-id="8a128-242">JSON</span></span>](#tab/json)

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

## <a name="initial-invoke-request-from-a-message"></a><span data-ttu-id="8a128-243">Anfängliche Aufrufanforderung aus einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="8a128-243">Initial invoke request from a message</span></span>

<span data-ttu-id="8a128-244">Wenn Ihr Bot von einer Nachricht aufgerufen wird, muss das Objekt in der anfänglichen Aufrufanforderung die Details der Nachricht enthalten, aus der Ihre Messagingerweiterung `value` aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8a128-244">When your bot is invoked from a message,  the `value` object in the initial invoke request must contain the details of the message that your messaging extension is invoked from.</span></span> <span data-ttu-id="8a128-245">Die Arrays und sind optional und nicht vorhanden, wenn in der ursprünglichen Nachricht keine Reaktionen oder `reactions` `mentions` Erwähnungen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8a128-245">The `reactions` and `mentions` arrays are optional, and they are not present if there are no reactions or mentions in the original message.</span></span> <span data-ttu-id="8a128-246">Der folgende Abschnitt ist ein Beispiel für das `value` Objekt:</span><span class="sxs-lookup"><span data-stu-id="8a128-246">The following section is an example of the `value` object:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8a128-247">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8a128-247">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="8a128-248">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8a128-248">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[<span data-ttu-id="8a128-249">Json</span><span class="sxs-lookup"><span data-stu-id="8a128-249">JSON</span></span>](#tab/json)

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

## <a name="respond-to-the-fetchtask"></a><span data-ttu-id="8a128-250">Antworten auf fetchTask</span><span class="sxs-lookup"><span data-stu-id="8a128-250">Respond to the fetchTask</span></span>

<span data-ttu-id="8a128-251">Reagieren Sie auf die Aufrufanforderung mit einem Objekt, das entweder ein Objekt mit der adaptiven Karte oder `task` `taskInfo` Web-URL oder eine einfache Zeichenfolgennachricht enthält.</span><span class="sxs-lookup"><span data-stu-id="8a128-251">Respond to the invoke request with a `task` object that contains either a `taskInfo` object with the Adaptive Card or web URL, or a simple string message.</span></span>

|<span data-ttu-id="8a128-252">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-252">Property name</span></span>|<span data-ttu-id="8a128-253">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-253">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="8a128-254">Dies kann `continue` entweder sein, um ein Formular oder ein `message` einfaches Popup zu präsentieren.</span><span class="sxs-lookup"><span data-stu-id="8a128-254">Can be either `continue` to present a form, or `message` for a simple popup.</span></span> |
|`value`| <span data-ttu-id="8a128-255">Entweder ein `taskInfo` Objekt für ein Formular oder ein für eine `string` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="8a128-255">Either a `taskInfo` object for a form, or a `string` for a message.</span></span> |

<span data-ttu-id="8a128-256">Das Schema für das taskInfo-Objekt ist:</span><span class="sxs-lookup"><span data-stu-id="8a128-256">The schema for the taskInfo object is:</span></span>

|<span data-ttu-id="8a128-257">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8a128-257">Property name</span></span>|<span data-ttu-id="8a128-258">Zweck</span><span class="sxs-lookup"><span data-stu-id="8a128-258">Purpose</span></span>|
|---|---|
|`title`| <span data-ttu-id="8a128-259">Der Titel des Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="8a128-259">The title of the task module.</span></span>|
|`height`| <span data-ttu-id="8a128-260">Es muss entweder eine ganze Zahl (in Pixel) oder `small` , `medium` `large` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-260">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`width`| <span data-ttu-id="8a128-261">Es muss entweder eine ganze Zahl (in Pixel) oder `small` , `medium` `large` sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-261">It must be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`card`| <span data-ttu-id="8a128-262">Die adaptive Karte, die das Formular definiert (wenn sie eine verwendet).</span><span class="sxs-lookup"><span data-stu-id="8a128-262">The adaptive card defining the form (if using one).</span></span>
|`url`| <span data-ttu-id="8a128-263">Die URL, die innerhalb des Aufgabenmoduls als eingebettete Webansicht geöffnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a128-263">The URL to be opened inside of the task module as an embedded web view.</span></span>|
|`fallbackUrl`| <span data-ttu-id="8a128-264">Wenn ein Client das Aufgabenmodulfeature nicht unterstützt, wird diese URL auf einer Browserregisterkarte geöffnet.</span><span class="sxs-lookup"><span data-stu-id="8a128-264">If a client does not support the task module feature, this URL is opened in a browser tab.</span></span> |

### <a name="respond-to-the-fetchtask-with-an-adaptive-card"></a><span data-ttu-id="8a128-265">Antworten auf fetchTask mit einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="8a128-265">Respond to the fetchTask with an Adaptive Card</span></span>

<span data-ttu-id="8a128-266">Wenn Sie eine adaptive Karte verwenden, müssen Sie mit einem Objekt mit dem Objekt antworten, das `task` eine adaptive Karte `value` enthält.</span><span class="sxs-lookup"><span data-stu-id="8a128-266">When using an adaptive card, you must respond with a `task` object with the `value` object containing an Adaptive Card.</span></span>

#### <a name="example"></a><span data-ttu-id="8a128-267">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-267">Example</span></span>

<span data-ttu-id="8a128-268">Der folgende Codeabschnitt ist ein Beispiel für die `fetchTask` Antwort mit einer adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="8a128-268">The following code section is an example to `fetchTask` response with an adaptive card:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8a128-269">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8a128-269">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="8a128-270">In diesem Beispiel wird zusätzlich zum Bot Framework SDK das [AdaptiveCards-NuGet-Paket](https://www.nuget.org/packages/AdaptiveCards) verwendet.</span><span class="sxs-lookup"><span data-stu-id="8a128-270">This sample uses the [AdaptiveCards NuGet package](https://www.nuget.org/packages/AdaptiveCards) in addition to the Bot Framework SDK.</span></span>

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="8a128-271">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8a128-271">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="8a128-272">Json</span><span class="sxs-lookup"><span data-stu-id="8a128-272">JSON</span></span>](#tab/json)

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

### <a name="create-a-task-module-with-an-embedded-web-view"></a><span data-ttu-id="8a128-273">Erstellen eines Aufgabenmoduls mit einer eingebetteten Webansicht</span><span class="sxs-lookup"><span data-stu-id="8a128-273">Create a task module with an embedded web view</span></span>

<span data-ttu-id="8a128-274">Wenn Sie eine eingebettete Webansicht verwenden, müssen Sie mit einem Objekt mit dem Objekt antworten, das die URL zum Webformular enthält, das `task` `value` Sie laden möchten.</span><span class="sxs-lookup"><span data-stu-id="8a128-274">When using an embedded web view, you must respond with a `task` object with the `value` object containing the URL to the web form that you want to load.</span></span> <span data-ttu-id="8a128-275">Die Domänen einer beliebigen URL, die Sie laden möchten, müssen im Array im Manifest Ihrer `validDomains` App enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-275">The domains of any URL you want to load must be included in the `validDomains` array in your app's manifest.</span></span> <span data-ttu-id="8a128-276">Weitere Informationen zum Erstellen der eingebetteten Webansicht finden Sie in der [Dokumentation zum Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md).</span><span class="sxs-lookup"><span data-stu-id="8a128-276">For more information on building your embedded web view, see the [task module documentation](~/task-modules-and-cards/what-are-task-modules.md).</span></span> 

# <a name="cnet"></a>[<span data-ttu-id="8a128-277">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8a128-277">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="8a128-278">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8a128-278">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="8a128-279">Json</span><span class="sxs-lookup"><span data-stu-id="8a128-279">JSON</span></span>](#tab/json)

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

### <a name="request-to-install-your-conversational-bot"></a><span data-ttu-id="8a128-280">Anforderung zum Installieren des Unterhaltungsbots</span><span class="sxs-lookup"><span data-stu-id="8a128-280">Request to install your conversational bot</span></span>

<span data-ttu-id="8a128-281">Wenn die App einen Unterhaltungsbot enthält, installieren Sie den Bot in der Unterhaltung, und laden Sie dann das Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="8a128-281">If the app contains a conversational bot, install the bot in the conversation and then load the task module.</span></span> <span data-ttu-id="8a128-282">Der Bot ist hilfreich, um zusätzlichen Kontext für das Aufgabenmodul zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8a128-282">The bot is useful to get additional context for the task module.</span></span> <span data-ttu-id="8a128-283">Ein Beispiel für dieses Szenario ist das Abrufen der Liste zum Auffüllen eines Personenauswahlsteuerelements oder der Liste der Kanäle in einem Team.</span><span class="sxs-lookup"><span data-stu-id="8a128-283">An example for this scenario is to fetch the roster to populate a people picker control or the list of channels in a team.</span></span>

<span data-ttu-id="8a128-284">Wenn die Messagingerweiterung den Aufruf empfängt, überprüfen Sie, ob der Bot im aktuellen Kontext installiert `composeExtension/fetchTask` ist, um den Fluss zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="8a128-284">When the messaging extension receives the `composeExtension/fetchTask` invoke, check if the bot is installed in the current context to facilitate the flow.</span></span> <span data-ttu-id="8a128-285">Überprüfen Sie z. B. den Fluss mit einem Abruf von Dienstplanaufrufen.</span><span class="sxs-lookup"><span data-stu-id="8a128-285">For example, check the flow with a get roster call.</span></span> <span data-ttu-id="8a128-286">Wenn der Bot nicht installiert ist, geben Sie eine adaptive Karte mit einer Aktion zurück, die den Benutzer zum Installieren des Bots anfordert.</span><span class="sxs-lookup"><span data-stu-id="8a128-286">If the bot is not installed, return an Adaptive Card with an action that requests the user to install the bot.</span></span> <span data-ttu-id="8a128-287">Der Benutzer muss über die Berechtigung zum Installieren der Apps an diesem Speicherort für die Überprüfung verfügen.</span><span class="sxs-lookup"><span data-stu-id="8a128-287">The user must have the permission to install the apps in that location for checking.</span></span> <span data-ttu-id="8a128-288">Wenn die App-Installation nicht erfolgreich ist, erhält der Benutzer eine Nachricht, um sich an den Administrator zu wenden.</span><span class="sxs-lookup"><span data-stu-id="8a128-288">If the app installation is unsuccessful, the user receives a message to contact the administrator.</span></span>

#### <a name="example"></a><span data-ttu-id="8a128-289">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-289">Example</span></span> 

<span data-ttu-id="8a128-290">Der folgende Codeabschnitt ist ein Beispiel für die Antwort:</span><span class="sxs-lookup"><span data-stu-id="8a128-290">The following code section is an example of the response:</span></span>

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

<span data-ttu-id="8a128-291">Nach der Installation des Unterhaltungsbots empfängt er eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` , und `value.data.msteams.justInTimeInstall = true` .</span><span class="sxs-lookup"><span data-stu-id="8a128-291">After the installation of conversational bot, it receives another invoke message with `name = composeExtension/submitAction`, and `value.data.msteams.justInTimeInstall = true`.</span></span>

#### <a name="example"></a><span data-ttu-id="8a128-292">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-292">Example</span></span> 

<span data-ttu-id="8a128-293">Der folgende Codeabschnitt ist ein Beispiel für die Aufgabenantwort auf den Aufruf:</span><span class="sxs-lookup"><span data-stu-id="8a128-293">The following code section is an example of the task response to the invoke:</span></span>

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

<span data-ttu-id="8a128-294">Die Aufgabenantwort auf den Aufruf muss der des installierten Bots ähnlich sein.</span><span class="sxs-lookup"><span data-stu-id="8a128-294">The task response to the invoke must be similar to that of the installed bot.</span></span>

#### <a name="example"></a><span data-ttu-id="8a128-295">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-295">Example</span></span> 

<span data-ttu-id="8a128-296">Der folgende Codeabschnitt ist ein Beispiel für die Just-In-Time-Installation der App mit adaptiver Karte:</span><span class="sxs-lookup"><span data-stu-id="8a128-296">The following code section is an example of just-in time installation of app with Adaptive card:</span></span> 

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

## <a name="code-sample"></a><span data-ttu-id="8a128-297">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8a128-297">Code sample</span></span>

| <span data-ttu-id="8a128-298">Beispielname</span><span class="sxs-lookup"><span data-stu-id="8a128-298">Sample Name</span></span>           | <span data-ttu-id="8a128-299">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a128-299">Description</span></span> | <span data-ttu-id="8a128-300">.NET</span><span class="sxs-lookup"><span data-stu-id="8a128-300">.NET</span></span>    | <span data-ttu-id="8a128-301">Node.js</span><span class="sxs-lookup"><span data-stu-id="8a128-301">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="8a128-302">Messagingerweiterungsaktion für Teams</span><span class="sxs-lookup"><span data-stu-id="8a128-302">Teams messaging extension action</span></span>| <span data-ttu-id="8a128-303">Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren.</span><span class="sxs-lookup"><span data-stu-id="8a128-303">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="8a128-304">View</span><span class="sxs-lookup"><span data-stu-id="8a128-304">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="8a128-305">View</span><span class="sxs-lookup"><span data-stu-id="8a128-305">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="8a128-306">Suche nach Messagingerweiterungen in Teams</span><span class="sxs-lookup"><span data-stu-id="8a128-306">Teams messaging extension search</span></span>   |  <span data-ttu-id="8a128-307">Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.</span><span class="sxs-lookup"><span data-stu-id="8a128-307">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="8a128-308">View</span><span class="sxs-lookup"><span data-stu-id="8a128-308">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="8a128-309">View</span><span class="sxs-lookup"><span data-stu-id="8a128-309">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a><span data-ttu-id="8a128-310">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8a128-310">See also</span></span>

> [!div class="nextstepaction"] 
> [<span data-ttu-id="8a128-311">Definieren von Aktionsbefehlen</span><span class="sxs-lookup"><span data-stu-id="8a128-311">Define action commands</span></span>](~/messaging-extensions/how-to/action-commands/define-action-command.md)


## <a name="next-step"></a><span data-ttu-id="8a128-312">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8a128-312">Next step</span></span>

> [!div class="nextstepaction"] 
> [<span data-ttu-id="8a128-313">Reagieren auf Aktionsbefehl</span><span class="sxs-lookup"><span data-stu-id="8a128-313">Respond to action command</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

