---
title: Erstellen adaptiver Kartenregisterkarten
author: KirtiPereira
description: Erstellen von Registerkarten mit adaptiven Karten
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: d65fc537b5282c050d891a6a73ff114c630e2c1c
ms.sourcegitcommit: c59d90ae03eae32996db49f162855965b55c52fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2021
ms.locfileid: "52668848"
---
# <a name="build-tabs-with-adaptive-cards"></a><span data-ttu-id="5baaf-103">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="5baaf-103">Build tabs with Adaptive Cards</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="5baaf-104">Dieses Feature befindet sich im [öffentlichen Developer Preview](~/resources/dev-preview/developer-preview-intro.md) und wird auf Desktop- und Mobilgeräten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5baaf-104">This feature is in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) and is supported in desktop and mobile.</span></span> <span data-ttu-id="5baaf-105">Unterstützung im Webbrowser wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="5baaf-105">Support in the web browser is coming soon.</span></span>
> * <span data-ttu-id="5baaf-106">Registerkarten mit adaptiven Karten werden derzeit nur als persönliche Apps unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5baaf-106">Tabs with Adaptive Cards are currently only supported as personal apps.</span></span>

<span data-ttu-id="5baaf-107">Verwenden Sie adaptive Karten, um Registerkarten mühelos zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5baaf-107">Use Adaptive Cards to build tabs with ease.</span></span> <span data-ttu-id="5baaf-108">Sie können Ihre Registerkarten mit fertigen Benutzeroberflächen-Lego-Blöcken erstellen, die auf Desktop, Web und Mobil nativ aussehen und sich als nativ anfühlen.</span><span class="sxs-lookup"><span data-stu-id="5baaf-108">You can build your tabs with ready-made UI Lego-blocks that look and feel native on desktop, web, and mobile.</span></span> <span data-ttu-id="5baaf-109">Das Erstellen von Registerkarten mit adaptiven Karten zentralisiert alle Teams-App-Funktionen um ein Bot-Back-End und das Frontend adaptiver Karten, sodass kein anderes Back-End für Ihren Bot und Ihre Registerkarten benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="5baaf-109">Building tabs with Adaptive Cards centralizes all Teams app capabilities around a bot backend and Adaptive Card frontend, thus, eliminating the need for a different backend for your bot and tabs.</span></span> <span data-ttu-id="5baaf-110">Dadurch werden die Server- und Wartungskosten Ihrer Teams erheblich reduziert.</span><span class="sxs-lookup"><span data-stu-id="5baaf-110">This greatly reduces server and maintenance costs of your Teams app.</span></span> <span data-ttu-id="5baaf-111">Dieser Artikel hilft Ihnen, die änderungen zu verstehen, die am App-Manifest vorgenommen werden müssen, wie die Aktivität aufgerufen wird und wie Informationen auf der Registerkarte mit adaptiven Karten aufgerufen werden, sowie die Auswirkungen auf den Workflow des Aufgabenmoduls.</span><span class="sxs-lookup"><span data-stu-id="5baaf-111">This article helps you understand the changes required to be made to the app manifest, how the invoke activity requests and sends information in tab with Adaptive Cards, and the impact on the task module workflow.</span></span> 

Die folgende Abbildung zeigt Buildregisterkarten mit adaptiven Karten auf Desktop- und Mobilgeräten: Beispiel für adaptive Karten, die :::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="in Registerkarten gerendert werden." border="false":::

## <a name="prerequisites"></a><span data-ttu-id="5baaf-113">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5baaf-113">Prerequisites</span></span>

<span data-ttu-id="5baaf-114">Bevor Sie mit der Verwendung adaptiver Karten zum Erstellen von Registerkarten beginnen, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="5baaf-114">Before you start using Adaptive Cards to build tabs, you must:</span></span>

* <span data-ttu-id="5baaf-115">Machen Sie sich mit [Bot-Entwicklung,](../../bots/what-are-bots.md) [adaptiven Karten](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)und [Aufgabenmodulen](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams.</span><span class="sxs-lookup"><span data-stu-id="5baaf-115">Be familiar with, [bot development](../../bots/what-are-bots.md), [Adaptive Cards](../../task-modules-and-cards/what-are-cards.md#adaptive-cards), and [Task Modules](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams.</span></span>
* <span data-ttu-id="5baaf-116">Sie können einen Bot in Teams Für Ihre Entwicklung ausführen.</span><span class="sxs-lookup"><span data-stu-id="5baaf-116">Have a bot running in Teams for your development.</span></span>
* <span data-ttu-id="5baaf-117">Be in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="5baaf-117">Be in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="changes-to-app-manifest"></a><span data-ttu-id="5baaf-118">Änderungen am App-Manifest</span><span class="sxs-lookup"><span data-stu-id="5baaf-118">Changes to app manifest</span></span>

<span data-ttu-id="5baaf-119">Persönliche Apps, die Registerkarten rendern, müssen ein `staticTabs` Array in ihr App-Manifest enthalten.</span><span class="sxs-lookup"><span data-stu-id="5baaf-119">Personal apps that render tabs must include a `staticTabs` array in their app manifest.</span></span> <span data-ttu-id="5baaf-120">Adaptive Kartenregisterkarten werden gerendert, wenn `contentBotId` die Eigenschaft in der Definition bereitgestellt `staticTab` wird.</span><span class="sxs-lookup"><span data-stu-id="5baaf-120">Adaptive Card Tab are rendered when the `contentBotId` property is provided in the `staticTab` definition.</span></span> <span data-ttu-id="5baaf-121">Statische Registerkartendefinitionen müssen entweder eine enthalten, die eine Adaptive Kartenregisterkarte oder eine , die eine typische gehostete Webinhaltsregisterkartenerfahrung `contentBotId` `contentUrl` an gibt.</span><span class="sxs-lookup"><span data-stu-id="5baaf-121">Static tab definitions must contain either a `contentBotId`, specifying an Adaptive Card Tab or a `contentUrl`, specifying a typical hosted web content tab experience.</span></span>

> [!NOTE]
> <span data-ttu-id="5baaf-122">Die `contentBotId` Eigenschaft ist derzeit manifest version 1.9 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5baaf-122">The `contentBotId` property is currently available manifest version 1.9 or later.</span></span> 

<span data-ttu-id="5baaf-123">Geben Sie `contentBotId` der Eigenschaft die Eigenschaft `botId` an, mit der die Registerkarte Adaptive Karte kommunizieren muss.</span><span class="sxs-lookup"><span data-stu-id="5baaf-123">Provide the `contentBotId` property with the `botId` that the Adaptive Card Tab must communicate with.</span></span> <span data-ttu-id="5baaf-124">Die für die Registerkarte Adaptive Karte konfigurierte wird im Parameter jeder Aufrufanforderung gesendet und kann verwendet werden, um verschiedene adaptive Kartenregisterkarten zu unterscheiden, die vom gleichen Bot `entityId` `tabContext` unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="5baaf-124">The `entityId` configured for the Adaptive Card Tab is sent in the `tabContext` parameter of each invoke request, and can be used to differentiate different Adaptive Card Tabs that are powered by the same bot.</span></span> <span data-ttu-id="5baaf-125">Weitere Informationen zu anderen statischen Registerkartendefinitionsfeldern finden Sie unter [Manifestschema](../../resources/schema/manifest-schema.md#statictabs).</span><span class="sxs-lookup"><span data-stu-id="5baaf-125">For more information about other static tab definition fields, see [manifest schema](../../resources/schema/manifest-schema.md#statictabs).</span></span>

<span data-ttu-id="5baaf-126">Im Folgenden finden Sie ein Beispielmanifest für adaptive Kartenregisterkarten:</span><span class="sxs-lookup"><span data-stu-id="5baaf-126">Following is a sample Adaptive Card Tab manifest:</span></span>

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "1.9",
  "id": "00000000-0000-0000-0000-000000000000",
  "version": "0.0.1",
  "packageName": "acprototype",
  "developer": {
    "name": "Contoso",
    "websiteUrl": "https://contoso.yourwebsite.com",
    "privacyUrl": "https://contoso.yourwebsite.com/privacy.html",
    "termsOfUseUrl": "https://contoso.yourwebsite.com/terms.html"
  },
  "name": {
    "short": "Contoso",
    "full": "Contoso Home"
  },
  "description": {
    "short": "Add short description here",
    "full": "Add full description here"
  },
  "icons": {
    "outline": "icon-outline.png",
    "color": "icon-color.png"
  },
  "accentColor": "#D85028",
  "configurableTabs": [],
  "staticTabs": [
    {
      "entityId": "homeTab",
      "name": "Home",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    },
    {
      "entityId": "moreTab",
      "name": "More",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    }
  ],
  "connectors": [],
  "composeExtensions": [],
  "permissions": ["identity", "messageTeamMembers"],
  "validDomains": [
    "contoso.yourwebsite.com",
    "token.botframework.com"
  ]
}
```

## <a name="invoke-activities"></a><span data-ttu-id="5baaf-127">Aufrufen von Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="5baaf-127">Invoke activities</span></span>

<span data-ttu-id="5baaf-128">Die Kommunikation zwischen Ihrer Registerkarte für adaptive Karten und Ihrem Bot erfolgt über `invoke` Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="5baaf-128">Communication between your Adaptive Card Tab and your bot is done through `invoke` activities.</span></span> <span data-ttu-id="5baaf-129">Jede `invoke` Aktivität hat einen entsprechenden *Namen*.</span><span class="sxs-lookup"><span data-stu-id="5baaf-129">Each `invoke` activity has a corresponding *name*.</span></span> <span data-ttu-id="5baaf-130">Verwenden Sie den Namen jeder Aktivität, um jede Anforderung zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="5baaf-130">Use the name of each activity to differentiate each request.</span></span> <span data-ttu-id="5baaf-131">`tab/fetch` und `tab/submit` sind die aktivitäten, die in diesem Abschnitt behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="5baaf-131">`tab/fetch` and `tab/submit` are the activities covered in this section.</span></span>

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a><span data-ttu-id="5baaf-132">Abrufen der adaptiven Karte zum Rendern auf einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="5baaf-132">Fetch Adaptive Card to render to a tab</span></span>

<span data-ttu-id="5baaf-133">`tab/fetch` ist die erste Aufrufanforderung, die Ihr Bot empfängt, wenn ein Benutzer eine Registerkarte für adaptive Karten öffnet.</span><span class="sxs-lookup"><span data-stu-id="5baaf-133">`tab/fetch` is the first invoke request that your bot receives when a user opens an Adaptive Card Tabs.</span></span> <span data-ttu-id="5baaf-134">Wenn Ihr Bot die Anforderung empfängt, sendet er entweder eine Antwort **zur** Fortsetzung der Registerkarte oder eine Antwort der **Registerkartenauthentisierung.**</span><span class="sxs-lookup"><span data-stu-id="5baaf-134">When your bot receives the request, it will either send a tab **continue** response or a tab **auth** response.</span></span>
<span data-ttu-id="5baaf-135">Die **Fortsetzungsantwort** enthält ein Array für **Karten**, das vertikal auf die Registerkarte in der Reihenfolge des Arrays gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="5baaf-135">The **continue** response includes an array for **cards**, which is rendered vertically to the tab in the order of the array.</span></span>

> [!NOTE]
> <span data-ttu-id="5baaf-136">Die **Antwort auf** die Authentifizierung wird im Abschnitt Authentifizierung [ausführlich](#authentication) erläutert.</span><span class="sxs-lookup"><span data-stu-id="5baaf-136">The **auth** response is explained in detail in the [authentication](#authentication) section.</span></span>

<span data-ttu-id="5baaf-137">Die folgenden Codeausschnitte sind Beispiele für `tab/fetch` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="5baaf-137">The following code snippets are examples of `tab/fetch` request and response:</span></span>

<span data-ttu-id="5baaf-138">**`tab/fetch` request**</span><span class="sxs-lookup"><span data-stu-id="5baaf-138">**`tab/fetch` request**</span></span>

```json
// tab/fetch POST request: agents/{botId}/invoke
{
    "name": "tab/fetch",
    "value: {
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        },
        "context": {
            "theme": "default"
            }
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}"
}
```

<span data-ttu-id="5baaf-139">**`tab/fetch` response**</span><span class="sxs-lookup"><span data-stu-id="5baaf-139">**`tab/fetch` response**</span></span>

```json
// tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
                {
                    "card": adaptiveCard1,
                },
                {
                    "card": adaptiveCard2,
                }
                {
                    "card": adaptiveCard3
                }  
            ]
        },
    },
    "responseType": "tab"
}
```

### <a name="handle-submits-from-adaptive-card"></a><span data-ttu-id="5baaf-140">Behandeln von Übermittelten von adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="5baaf-140">Handle submits from Adaptive Card</span></span>

<span data-ttu-id="5baaf-141">Nachdem eine adaptive Karte auf der Registerkarte gerendert wurde, muss sie in der Lage sein, auf Benutzerinteraktionen zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="5baaf-141">After an Adaptive Card is rendered in the tab, it must be able to respond to user interactions.</span></span> <span data-ttu-id="5baaf-142">Diese Antwort wird von der `tab/submit` Aufrufanforderung verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="5baaf-142">This response is handled by the `tab/submit` invoke request.</span></span>

<span data-ttu-id="5baaf-143">Wenn ein Benutzer auf der Registerkarte Adaptive Karte eine Schaltfläche auswählt, wird die Anforderung an Ihren Bot mit den entsprechenden Daten über die `tab/submit` *Action.Submit-Funktion* der adaptiven Karte ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="5baaf-143">When a user selects a button on the Adaptive Card Tab, the `tab/submit` request is triggered to your bot with the corresponding data through the *Action.Submit* function of Adaptive Card.</span></span> <span data-ttu-id="5baaf-144">Die Adaptive Card-Daten sind über die Dateneigenschaft der Anforderung `tab/submit` verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5baaf-144">The Adaptive Card data is available through the data property of the `tab/submit` request.</span></span> <span data-ttu-id="5baaf-145">Sie erhalten eine der folgenden Antworten auf Ihre Anforderung:</span><span class="sxs-lookup"><span data-stu-id="5baaf-145">You will receive either of the following responses to your request:</span></span>

* <span data-ttu-id="5baaf-146">Eine Http-Statuscodeantwort `200` ohne Text.</span><span class="sxs-lookup"><span data-stu-id="5baaf-146">A http status code `200` response with no body.</span></span> <span data-ttu-id="5baaf-147">Eine leere 200-Antwort führt zu keiner Aktion des Clients.</span><span class="sxs-lookup"><span data-stu-id="5baaf-147">An empty 200 response will result in no action taken by the client.</span></span>
* <span data-ttu-id="5baaf-148">Auf der `200` **Standardregisterkarte wird die** Antwort fortgesetzt, wie im Abschnitt ["Adaptive Karte abrufen"](#fetch-adaptive-card-to-render-to-a-tab) erläutert.</span><span class="sxs-lookup"><span data-stu-id="5baaf-148">The standard `200` tab **continue** response, as explained in [Fetch Adaptive Card](#fetch-adaptive-card-to-render-to-a-tab) section.</span></span> <span data-ttu-id="5baaf-149">Eine Antwort **für die Fortsetzung** der Registerkarte löst den Client aus, um die gerenderte Adaptive Kartenregisterkarte mit den adaptiven Karten im Kartenarray der Fortsetzungsantwort **zu** aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5baaf-149">A tab **continue** response triggers the client to update the rendered Adaptive Card Tab with the Adaptive Cards provided in the cards array of the **continue** response.</span></span>

<span data-ttu-id="5baaf-150">Die folgenden Codeausschnitte sind Beispiele für `tab/submit` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="5baaf-150">The following code snippets are examples of `tab/submit` request and response:</span></span>

<span data-ttu-id="5baaf-151">**`tab/submit` request**</span><span class="sxs-lookup"><span data-stu-id="5baaf-151">**`tab/submit` request**</span></span>

```json
// tab/submit POST request: agents/{botId}/invoke:
{
    "name": "tab/submit",
    "value": {
        "data": {
            "type": "tab/submit",
            //...<data properties>
            },
        "context": {
            "theme": "default"
            },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
            },
        },
    "conversation": {
           "id": "{generated_conversation_id}" 
        },
    "imdisplayname": "{user_display_name}"
}
```

<span data-ttu-id="5baaf-152">**`tab/submit` response**</span><span class="sxs-lookup"><span data-stu-id="5baaf-152">**`tab/submit` response**</span></span>

```json
//tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
              {
                "card": adaptiveCard1,
                },
              {
                "card": adaptiveCard2,
                } 
            ]
        },
    },
    "responseType": "tab"
}
```

## <a name="understand-task-module-workflow"></a><span data-ttu-id="5baaf-153">Verstehen des Aufgabenmodulworkflows</span><span class="sxs-lookup"><span data-stu-id="5baaf-153">Understand task module workflow</span></span>

<span data-ttu-id="5baaf-154">Das Aufgabenmodul verwendet auch adaptive Karte zum Aufrufen und `task/fetch` Zum Aufrufen von Anforderungen und `task/submit` Antworten.</span><span class="sxs-lookup"><span data-stu-id="5baaf-154">The task module also uses Adaptive Card to invoke `task/fetch` and `task/submit` requests and responses.</span></span> <span data-ttu-id="5baaf-155">Weitere Informationen finden Sie unter [Using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span><span class="sxs-lookup"><span data-stu-id="5baaf-155">For more information, see [Using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="5baaf-156">Mit der Einführung der Registerkarte Adaptive Karte ändert sich jedoch, wie der Bot auf eine Anforderung `task/submit` reagiert.</span><span class="sxs-lookup"><span data-stu-id="5baaf-156">However, with the introduction of Adaptive Card Tab there is a change in how the bot responds to a `task/submit` request.</span></span> <span data-ttu-id="5baaf-157">Wenn Sie eine Registerkarte für adaptive Karten verwenden, antwortet der Bot auf die Aufrufanforderung mit der Standard-Tab-Continue-Antwort und schließt `task/submit` das Aufgabenmodul. </span><span class="sxs-lookup"><span data-stu-id="5baaf-157">If you are using an Adaptive Card Tab, the bot responds to the `task/submit` invoke request with the standard tab **continue** response, and closes the task module.</span></span> <span data-ttu-id="5baaf-158">Die Registerkarte Adaptive Karte wird aktualisiert, indem die neue Liste der Im Antworttext der Registerkarte **"Fortsetzung"** bereitgestellten Karten gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="5baaf-158">The Adaptive Card Tab is updated by rendering the new list of cards provided in the tab **continue** response body.</span></span>

### <a name="invoke-taskfetch"></a><span data-ttu-id="5baaf-159">Invoke `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="5baaf-159">Invoke `task/fetch`</span></span>

<span data-ttu-id="5baaf-160">Die folgenden Codeausschnitte sind Beispiele für `task/fetch` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="5baaf-160">The following code snippets are examples of `task/fetch` request and response:</span></span>

<span data-ttu-id="5baaf-161">**`task/fetch` request**</span><span class="sxs-lookup"><span data-stu-id="5baaf-161">**`task/fetch` request**</span></span>
```json
// task/fetch POST request: agents/{botId}/invoke
{
    "name": "task/fetch",
    "value": {
        "data": {
            "type": "task/fetch"
        },
        "context": {
            "theme": "default",
        },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        }
    },
    "imdisplayname": "{user_display_name}",
    "conversation": {
        "id": "{generated_conversation_id}"
    } 
}
```

<span data-ttu-id="5baaf-162">**`task/fetch` response**</span><span class="sxs-lookup"><span data-stu-id="5baaf-162">**`task/fetch` response**</span></span>

```json
// task/fetch POST response: agents/{botId}/invoke
{
    "task": {
        "value": {
            "title": "Ninja Cat",
            "height": "small",
            "width": "small",
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": adaptiveCard,
            }
        },
    "type": "continue"
    },
    "responseType": "task"
}
```

### <a name="invoke-tasksubmit"></a><span data-ttu-id="5baaf-163">Invoke `task/submit`</span><span class="sxs-lookup"><span data-stu-id="5baaf-163">Invoke `task/submit`</span></span>

<span data-ttu-id="5baaf-164">Die folgenden Codeausschnitte sind Beispiele für `task/submit` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="5baaf-164">The following code snippets are examples of `task/submit` request and response:</span></span>

<span data-ttu-id="5baaf-165">**`task/submit` request**</span><span class="sxs-lookup"><span data-stu-id="5baaf-165">**`task/submit` request**</span></span>

```json
// task/submit POST request: agent/{botId}/invoke:
{
    "name": "task/submit",
    "value": {
        "data": {serialized_data_object},
        "context": {
            "theme": "default"
        },
    "tabContext": {
        "tabEntityId": "{tab_entity_id}"
        },
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}",
}
```

<span data-ttu-id="5baaf-166">**`task/submit` Antworttyp der Registerkarte**</span><span class="sxs-lookup"><span data-stu-id="5baaf-166">**`task/submit` tab response type**</span></span>

```json
// tab/fetch **continue** POST response: 
{
    "task":{
        "value": {
            "tab": {
                "type": "continue",
                "value": {
                    "cards": [
                        {
                            "card": adaptiveCard1
                        },
                        {
                            "card": adaptiveCard2
                        }
                    ]
                }
            }
        },
        "type": "continue"
    },
    "responseType": "task"
}
```

## <a name="authentication"></a><span data-ttu-id="5baaf-167">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="5baaf-167">Authentication</span></span>

<span data-ttu-id="5baaf-168">In den vorherigen Abschnitten dieses Artikels haben Sie gesehen, dass die meisten Entwicklungsparadigmen aus den Aufgabenmodulanforderungen und -antworten in Registerkartenanforderungen und -antworten extrapoliert werden können.</span><span class="sxs-lookup"><span data-stu-id="5baaf-168">In the previous sections of this article, you have seen that most of the development paradigms could be extrapolated from the task module requests and responses into tab requests and responses.</span></span> <span data-ttu-id="5baaf-169">Beim Behandeln der Authentifizierung folgt der Workflow für adaptive Kartenregisterkarte jedoch dem Authentifizierungsmuster für Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="5baaf-169">However, when it comes to handling authentication, the workflow for Adaptive Card Tab follows the authentication pattern for messaging extensions.</span></span> <span data-ttu-id="5baaf-170">Weitere Informationen finden Sie unter [Hinzufügen der Authentifizierung](../../messaging-extensions/how-to/add-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5baaf-170">For more information, see [add authentication](../../messaging-extensions/how-to/add-authentication.md).</span></span> 

<span data-ttu-id="5baaf-171">Im Abschnitt [Aufrufaktivitäten](#invoke-activities) wurden Sie darüber informiert, dass Anforderungen entweder eine Fortsetzungs- oder eine `tab/fetch` **Authentifizierungsantwort haben** können. </span><span class="sxs-lookup"><span data-stu-id="5baaf-171">In the [invoke activities](#invoke-activities) section, you were informed that `tab/fetch` requests can have either a **continue** or an **auth** response.</span></span> <span data-ttu-id="5baaf-172">Wenn eine `tab/fetch` Anforderung ausgelöst wird und eine Antwort der **Registerkartenauthentisierung** empfängt, wird dem Benutzer die Anmeldeseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5baaf-172">When a `tab/fetch` request is triggered and receives a tab **auth** response, the sign-in page is shown to the user.</span></span> 

<span data-ttu-id="5baaf-173">**So rufen Sie einen Authentifizierungscode über `tab/fetch` das Aufrufen ab**</span><span class="sxs-lookup"><span data-stu-id="5baaf-173">**To get an authentication code through `tab/fetch` invoke**</span></span>

1. <span data-ttu-id="5baaf-174">Öffnen Sie Ihre App.</span><span class="sxs-lookup"><span data-stu-id="5baaf-174">Open your app.</span></span> <span data-ttu-id="5baaf-175">Die Anmeldeseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5baaf-175">The sign in page appears.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5baaf-176">Das App-Logo wird über die im App-Manifest definierte Eigenschaft bereitgestellt, und der Titel wird angezeigt, nachdem das Logo in der Eigenschaft definiert wurde, die im Antworttext der Registerkarte `icon` `title` **authentifizierung** zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5baaf-176">The app logo is provided through the `icon` property defined in the app manifest, and the title appearing after the logo is defined in the `title` property returned in the tab **auth** response body.</span></span>

1. <span data-ttu-id="5baaf-177">Wählen Sie **Anmelden** aus.</span><span class="sxs-lookup"><span data-stu-id="5baaf-177">Select **Sign in**.</span></span> <span data-ttu-id="5baaf-178">Sie werden zu der Authentifizierungs-URL umgeleitet, die in der `value` Eigenschaft des **Authentifizierungsantworttexts** angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="5baaf-178">You are redirected to the authentication URL provided in the `value` property of the **auth** response body.</span></span> 
1. <span data-ttu-id="5baaf-179">Ein Popupfenster wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="5baaf-179">A pop-up window appears.</span></span> <span data-ttu-id="5baaf-180">In diesem Popupfenster wird Ihre Webseite mithilfe der Authentifizierungs-URL hostet.</span><span class="sxs-lookup"><span data-stu-id="5baaf-180">This pop-up window hosts your web page using the authentication URL.</span></span>
1. <span data-ttu-id="5baaf-181">Schließen Sie nach der Anmeldung das Fenster.</span><span class="sxs-lookup"><span data-stu-id="5baaf-181">After you sign in, close the window.</span></span> <span data-ttu-id="5baaf-182">Ein *Authentifizierungscode* wird an den Teams gesendet.</span><span class="sxs-lookup"><span data-stu-id="5baaf-182">An *authentication code* is sent to the Teams client.</span></span>
1. <span data-ttu-id="5baaf-183">Der Teams-Client gibt die Anforderung dann erneut an Ihren Dienst weiter, der den von Ihrer gehosteten Webseite bereitgestellten Authentifizierungscode `tab/fetch` enthält.</span><span class="sxs-lookup"><span data-stu-id="5baaf-183">The Teams client then reissues the `tab/fetch` request to your service, which includes the authentication code provided by your hosted web page.</span></span> 

### <a name="tabfetch-authentication-data-flow"></a><span data-ttu-id="5baaf-184">`tab/fetch` Authentifizierungsdatenfluss</span><span class="sxs-lookup"><span data-stu-id="5baaf-184">`tab/fetch` authentication data flow</span></span>

<span data-ttu-id="5baaf-185">Die folgende Abbildung bietet eine Übersicht über die Funktionsweise des Authentifizierungsdatenflusses für einen `tab/fetch` Aufruf.</span><span class="sxs-lookup"><span data-stu-id="5baaf-185">The following image provides an overview of how the authentication data flow works for a `tab/fetch` invoke.</span></span>

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Beispiel für den Authentifizierungsfluss für adaptive Kartenregisterkarten." border="false":::

<span data-ttu-id="5baaf-187">**`tab/fetch` Antwort auf Authentifizierung**</span><span class="sxs-lookup"><span data-stu-id="5baaf-187">**`tab/fetch` auth response**</span></span>

<span data-ttu-id="5baaf-188">Der folgende Codeausschnitt ist ein Beispiel für `tab/fetch` die Authentifizierungsantwort:</span><span class="sxs-lookup"><span data-stu-id="5baaf-188">The following code snippet is an example of `tab/fetch` auth response:</span></span>

```json
// tab/auth POST response (openURL)
{
    "tab": {
        "type": "auth",
        "suggestedActions":{
            "actions":[
                {
                    "type": "openUrl",
                    "value": "https://example.com/auth",
                    "title": "Sign in to this app"
                }
            ]
        }
    }
}
```

### <a name="example"></a><span data-ttu-id="5baaf-189">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5baaf-189">Example</span></span>

<span data-ttu-id="5baaf-190">Das folgende Beispiel zeigt ein neu ausgestelltes Anforderungsbeispiel:</span><span class="sxs-lookup"><span data-stu-id="5baaf-190">The following shows a reissued request example:</span></span>

```json
{
    "name": "tab/fetch",
    "type": "invoke",
    "timestamp": "2021-01-15T00:10:12.253Z",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "{id}",
        "name": "John Smith",
        "aadObjectId": "00000000-0000-0000-0000-000000000000"
    },
    "conversation": {
        "tenantId": "{tenantId}",
        "id": "tab:{guid}"
    },
    "recipients": {
        "id": "28:00000000-0000-0000-0000-000000000000",
        "name": "ContosoApp"
    },
    "entities": [
        {
            "locale": "en-us",
            "country": "US",
            "platform": "Windows",
            "timezone": "America/Los_Angeles",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "tenant": { "id": "00000000-0000-0000-0000-000000000000" },
        "source": { "name": "message" }
    },
    "value": {
        "tabContext": { "tabEntityId": "homeTab" },
        "state": "0.43195668034524815"
    },
    "locale": "en-US",
    "localTimeZone": "America/Los_Angeles"
}
```

## <a name="see-also"></a><span data-ttu-id="5baaf-191">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5baaf-191">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5baaf-192">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="5baaf-192">Adaptive Card</span></span>](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)

