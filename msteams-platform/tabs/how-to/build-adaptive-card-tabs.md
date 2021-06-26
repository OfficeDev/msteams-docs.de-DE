---
title: Erstellen adaptiver Kartenregisterkarten
author: KirtiPereira
description: Erstellen von Registerkarten mit adaptiven Karten
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: c551ae748805ddc380fb3213b67f704c73060a2f
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140285"
---
# <a name="build-tabs-with-adaptive-cards"></a><span data-ttu-id="ae88b-103">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="ae88b-103">Build tabs with Adaptive Cards</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="ae88b-104">Dieses Feature befindet sich in der [Öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) und wird auf Desktops und mobilen Geräten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-104">This feature is in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md) and is supported in desktop and mobile.</span></span> <span data-ttu-id="ae88b-105">Der Support im Webbrowser wird in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="ae88b-105">Support in the web browser is coming soon.</span></span>
> * <span data-ttu-id="ae88b-106">Registerkarten mit adaptiven Karten werden derzeit nur als persönliche Apps unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-106">Tabs with Adaptive Cards are currently only supported as personal apps.</span></span>

<span data-ttu-id="ae88b-107">Beim Entwickeln einer Registerkarte mithilfe der herkömmlichen Methode können diese Probleme auftreten, z. B. HTML- und CSS-Überlegungen, langsame Ladezeiten, iFrame-Einschränkungen sowie Serverwartung und -kosten.</span><span class="sxs-lookup"><span data-stu-id="ae88b-107">When developing a tab using the traditional method, you might run into these issues, such as HTML and CSS considerations, slow load times, iFrame constraints, and server maintenance and costs.</span></span> <span data-ttu-id="ae88b-108">Registerkarten für adaptive Karten sind eine neue Methode zum Erstellen von Registerkarten in Teams.</span><span class="sxs-lookup"><span data-stu-id="ae88b-108">Adaptive Card tabs is a new way to build tabs in Teams.</span></span> <span data-ttu-id="ae88b-109">Anstatt Webinhalte in einen IFrame einzubetten, können Sie adaptive Karten auf einer Registerkarte rendern. Während das Front-End mit adaptiven Karten gerendert wird, wird das Back-End von einem Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-109">Instead of embedding web content in an IFrame, you can render Adaptive Cards to a tab. While the front-end is rendered with Adaptive Cards, the backend is powered by a bot.</span></span> <span data-ttu-id="ae88b-110">Der Bot ist dafür verantwortlich, Anforderungen zu akzeptieren und entsprechend mit der gerenderten adaptiven Karte zu antworten.</span><span class="sxs-lookup"><span data-stu-id="ae88b-110">The bot is responsible for accepting requests and responding appropriately with the Adaptive Card that is rendered.</span></span>

<span data-ttu-id="ae88b-111">Sie können Ihre Registerkarten mit vorgefertigten Ui-Blocks (Ui) erstellen, die auf Desktops, im Web und auf mobilgeräten systemintern aussehen und sich nativ anfühlen.</span><span class="sxs-lookup"><span data-stu-id="ae88b-111">You can build your tabs with ready-made user interface (UI) Lego-blocks that look and feel native on desktop, web, and mobile.</span></span> <span data-ttu-id="ae88b-112">Dieser Artikel hilft Ihnen zu verstehen, welche Änderungen am App-Manifest vorgenommen werden müssen, wie das Aufrufen von Aktivitätsanforderungen und das Senden von Informationen auf der Registerkarte mit adaptiven Karten und die Auswirkungen auf den Aufgabenmodulworkflow erfolgt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-112">This article helps you understand the changes required to be made to the app manifest, how the invoke activity requests and sends information in tab with Adaptive Cards, and the impact on the task module workflow.</span></span>

<span data-ttu-id="ae88b-113">Die folgende Abbildung zeigt Buildregisterkarten mit adaptiven Karten auf Desktops und mobilgeräten:</span><span class="sxs-lookup"><span data-stu-id="ae88b-113">The following image depicts build tabs with Adaptive Cards in desktop and mobile:</span></span>

:::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="Beispiel für eine adaptive Karte, die auf Registerkarten gerendert wird." border="false":::

## <a name="prerequisites"></a><span data-ttu-id="ae88b-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ae88b-115">Prerequisites</span></span>

<span data-ttu-id="ae88b-116">Bevor Sie mit der Verwendung adaptiver Karten zum Erstellen von Registerkarten beginnen, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="ae88b-116">Before you start using Adaptive Cards to build tabs, you must:</span></span>

* <span data-ttu-id="ae88b-117">Machen Sie sich mit [der Bot-Entwicklung,](../../bots/what-are-bots.md) [adaptiven Karten](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)und [Aufgabenmodulen](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams vertraut.</span><span class="sxs-lookup"><span data-stu-id="ae88b-117">Be familiar with, [bot development](../../bots/what-are-bots.md), [Adaptive Cards](../../task-modules-and-cards/what-are-cards.md#adaptive-cards), and [task modules](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams.</span></span>
* <span data-ttu-id="ae88b-118">Lassen Sie einen Bot in Teams für Ihre Entwicklung ausführen.</span><span class="sxs-lookup"><span data-stu-id="ae88b-118">Have a bot running in Teams for your development.</span></span>
* <span data-ttu-id="ae88b-119">Seien Sie in [der Öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="ae88b-119">Be in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="changes-to-app-manifest"></a><span data-ttu-id="ae88b-120">Änderungen am App-Manifest</span><span class="sxs-lookup"><span data-stu-id="ae88b-120">Changes to app manifest</span></span>

<span data-ttu-id="ae88b-121">Persönliche Apps, die Registerkarten rendern, müssen ein `staticTabs` Array in ihrem App-Manifest enthalten.</span><span class="sxs-lookup"><span data-stu-id="ae88b-121">Personal apps that render tabs must include a `staticTabs` array in their app manifest.</span></span> <span data-ttu-id="ae88b-122">Registerkarten für adaptive Karten werden gerendert, wenn die `contentBotId` Eigenschaft in der Definition bereitgestellt `staticTab` wird.</span><span class="sxs-lookup"><span data-stu-id="ae88b-122">Adaptive Card tabs are rendered when the `contentBotId` property is provided in the `staticTab` definition.</span></span> <span data-ttu-id="ae88b-123">Statische Registerkartendefinitionen müssen entweder eine , eine Registerkarte für `contentBotId` adaptive Karten oder eine , die eine typische `contentUrl` gehostete Webinhaltsregisterkarte angeben.</span><span class="sxs-lookup"><span data-stu-id="ae88b-123">Static tab definitions must contain either a `contentBotId`, specifying an Adaptive Card tab or a `contentUrl`, specifying a typical hosted web content tab experience.</span></span>

> [!NOTE]
> <span data-ttu-id="ae88b-124">Die `contentBotId` Eigenschaft ist derzeit in der Manifestversion 1.9 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ae88b-124">The `contentBotId` property is currently available in manifest version 1.9 or later.</span></span>

<span data-ttu-id="ae88b-125">Stellen Sie der `contentBotId` Eigenschaft die Eigenschaft `botId` bereit, mit der die Registerkarte "Adaptive Karte" kommunizieren muss.</span><span class="sxs-lookup"><span data-stu-id="ae88b-125">Provide the `contentBotId` property with the `botId` that the Adaptive Card tab must communicate with.</span></span> <span data-ttu-id="ae88b-126">Die `entityId` für die Registerkarte "Adaptive Karte" konfigurierte Karte wird im Parameter jeder Aufrufanforderung gesendet und kann verwendet `tabContext` werden, um adaptive Kartenregisterkarten zu unterscheiden, die vom gleichen Bot unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="ae88b-126">The `entityId` configured for the Adaptive Card tab is sent in the `tabContext` parameter of each invoke request, and can be used to differentiate Adaptive Card Tabs that are powered by the same bot.</span></span> <span data-ttu-id="ae88b-127">Weitere Informationen zu anderen statischen Registerkartendefinitionsfeldern finden Sie unter [Manifestschema.](../../resources/schema/manifest-schema.md#statictabs)</span><span class="sxs-lookup"><span data-stu-id="ae88b-127">For more information about other static tab definition fields, see [manifest schema](../../resources/schema/manifest-schema.md#statictabs).</span></span>

<span data-ttu-id="ae88b-128">Es folgt ein Beispiel für ein Registerkartenmanifest für adaptive Karten:</span><span class="sxs-lookup"><span data-stu-id="ae88b-128">Following is a sample Adaptive Card tab manifest:</span></span>

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

## <a name="invoke-activities"></a><span data-ttu-id="ae88b-129">Aufrufen von Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="ae88b-129">Invoke activities</span></span>

<span data-ttu-id="ae88b-130">Die Kommunikation zwischen Ihrer Registerkarte "Adaptive Karte" und Ihrem Bot erfolgt über `invoke` Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="ae88b-130">Communication between your Adaptive Card tab and your bot is done through `invoke` activities.</span></span> <span data-ttu-id="ae88b-131">Jede `invoke` Aktivität hat einen entsprechenden **Namen.**</span><span class="sxs-lookup"><span data-stu-id="ae88b-131">Each `invoke` activity has a corresponding **name**.</span></span> <span data-ttu-id="ae88b-132">Verwenden Sie den Namen jeder Aktivität, um jede Anforderung zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="ae88b-132">Use the name of each activity to differentiate each request.</span></span> <span data-ttu-id="ae88b-133">`tab/fetch` und `tab/submit` sind die in diesem Abschnitt behandelten Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="ae88b-133">`tab/fetch` and `tab/submit` are the activities covered in this section.</span></span>

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a><span data-ttu-id="ae88b-134">Abrufen einer adaptiven Karte zum Rendern auf einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ae88b-134">Fetch Adaptive Card to render to a tab</span></span>

<span data-ttu-id="ae88b-135">`tab/fetch`ist die erste Aufrufanforderung, die Ihr Bot empfängt, wenn ein Benutzer eine Registerkarte für adaptive Karten öffnet. Wenn Ihr Bot die Anforderung empfängt, sendet er entweder eine **Antwort** zur Fortsetzung der Registerkarte oder eine **Tab-Authentifizierungsantwort.**</span><span class="sxs-lookup"><span data-stu-id="ae88b-135">`tab/fetch` is the first invoke request that your bot receives when a user opens an Adaptive Card tab. When your bot receives the request, it either sends a tab **continue** response or a tab **auth** response.</span></span>
<span data-ttu-id="ae88b-136">Die **Fortsetzungsantwort** enthält ein Array für **Karten,** das vertikal auf der Registerkarte in der Reihenfolge des Arrays gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="ae88b-136">The **continue** response includes an array for **cards**, which is rendered vertically to the tab in the order of the array.</span></span>

> [!NOTE]
> <span data-ttu-id="ae88b-137">Weitere Informationen zur **Authentifizierungsantwort** finden Sie unter ["Authentifizierung".](#authentication)</span><span class="sxs-lookup"><span data-stu-id="ae88b-137">For more information on **auth** response, see [authentication](#authentication).</span></span>

<span data-ttu-id="ae88b-138">Der folgende Code enthält Beispiele für `tab/fetch` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="ae88b-138">The following code provides examples of `tab/fetch` request and response:</span></span>

<span data-ttu-id="ae88b-139">**`tab/fetch` Anfrage**</span><span class="sxs-lookup"><span data-stu-id="ae88b-139">**`tab/fetch` request**</span></span>

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

<span data-ttu-id="ae88b-140">**`tab/fetch` Antwort**</span><span class="sxs-lookup"><span data-stu-id="ae88b-140">**`tab/fetch` response**</span></span>

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

### <a name="handle-submits-from-adaptive-card"></a><span data-ttu-id="ae88b-141">Verarbeiten von Übermittlungen von einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="ae88b-141">Handle submits from Adaptive Card</span></span>

<span data-ttu-id="ae88b-142">Nachdem eine adaptive Karte auf der Registerkarte gerendert wurde, muss sie in der Lage sein, auf Benutzerinteraktionen zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="ae88b-142">After an Adaptive Card is rendered in the tab, it must be able to respond to user interactions.</span></span> <span data-ttu-id="ae88b-143">Diese Antwort wird von der `tab/submit` Aufrufanforderung verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="ae88b-143">This response is handled by the `tab/submit` invoke request.</span></span>

<span data-ttu-id="ae88b-144">Wenn ein Benutzer eine Schaltfläche auf der Registerkarte "Adaptive Karte" auswählt, wird die `tab/submit` Anforderung an Ihren Bot mit den entsprechenden Daten über die Funktion der `Action.Submit` adaptiven Karte ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ae88b-144">When a user selects a button on the Adaptive Card tab, the `tab/submit` request is triggered to your bot with the corresponding data through the `Action.Submit` function of Adaptive Card.</span></span> <span data-ttu-id="ae88b-145">Die Daten der adaptiven Karte sind über die Dateneigenschaft der `tab/submit` Anforderung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ae88b-145">The Adaptive Card data is available through the data property of the `tab/submit` request.</span></span> <span data-ttu-id="ae88b-146">Sie erhalten eine der folgenden Antworten auf Ihre Anforderung:</span><span class="sxs-lookup"><span data-stu-id="ae88b-146">You receive either of the following responses to your request:</span></span>

* <span data-ttu-id="ae88b-147">Eine HTTP-Statuscodeantwort `200` ohne Textkörper.</span><span class="sxs-lookup"><span data-stu-id="ae88b-147">An HTTP status code `200` response with no body.</span></span> <span data-ttu-id="ae88b-148">Eine leere 200-Antwort führt dazu, dass der Client keine Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-148">An empty 200 response results in no action taken by the client.</span></span>
* <span data-ttu-id="ae88b-149">Auf der `200` Standardregisterkarte wird die Antwort **fortgesetzt,** wie beim [Abrufen einer adaptiven Karte](#fetch-adaptive-card-to-render-to-a-tab)erläutert.</span><span class="sxs-lookup"><span data-stu-id="ae88b-149">The standard `200` tab **continue** response, as explained in [fetch Adaptive Card](#fetch-adaptive-card-to-render-to-a-tab).</span></span> <span data-ttu-id="ae88b-150">Eine **Fortsetzungsantwort** der Registerkarte löst aus, dass der Client die gerenderte Registerkarte "Adaptive Karte" mit den adaptiven Karten aktualisiert, die im Kartenarray der **Fortsetzungsantwort** bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="ae88b-150">A tab **continue** response triggers the client to update the rendered Adaptive Card tab with the Adaptive Cards provided in the cards array of the **continue** response.</span></span>

<span data-ttu-id="ae88b-151">Der folgende Code enthält Beispiele für `tab/submit` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="ae88b-151">The following code provides examples of `tab/submit` request and response:</span></span>

<span data-ttu-id="ae88b-152">**`tab/submit` Anfrage**</span><span class="sxs-lookup"><span data-stu-id="ae88b-152">**`tab/submit` request**</span></span>

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

<span data-ttu-id="ae88b-153">**`tab/submit` Antwort**</span><span class="sxs-lookup"><span data-stu-id="ae88b-153">**`tab/submit` response**</span></span>

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

## <a name="understand-task-module-workflow"></a><span data-ttu-id="ae88b-154">Grundlegendes zum Aufgabenmodulworkflow</span><span class="sxs-lookup"><span data-stu-id="ae88b-154">Understand task module workflow</span></span>

<span data-ttu-id="ae88b-155">Das Aufgabenmodul verwendet auch adaptive Karte zum Aufrufen `task/fetch` und `task/submit` Anfordern und Antworten.</span><span class="sxs-lookup"><span data-stu-id="ae88b-155">The task module also uses Adaptive Card to invoke `task/fetch` and `task/submit` requests and responses.</span></span> <span data-ttu-id="ae88b-156">Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Microsoft Teams Bots.](../../task-modules-and-cards/task-modules/task-modules-bots.md)</span><span class="sxs-lookup"><span data-stu-id="ae88b-156">For more information, see [using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).</span></span>

<span data-ttu-id="ae88b-157">Mit der Einführung der Registerkarte "Adaptive Karte" gibt es eine Änderung in der Art und Weise, wie der Bot auf eine `task/submit` Anforderung antwortet.</span><span class="sxs-lookup"><span data-stu-id="ae88b-157">With the introduction of Adaptive Card tab, there is a change in how the bot responds to a `task/submit` request.</span></span> <span data-ttu-id="ae88b-158">Wenn Sie eine Registerkarte für adaptive Karten verwenden, antwortet der Bot auf die `task/submit` Aufrufanforderung mit der Standardregisterkarte **"Continue"-Antwort** und schließt das Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="ae88b-158">If you are using an Adaptive Card tab, the bot responds to the `task/submit` invoke request with the standard tab **continue** response, and closes the task module.</span></span> <span data-ttu-id="ae88b-159">Die Registerkarte "Adaptive Karte" wird aktualisiert, indem die neue Liste der Im Antworttext der Registerkarte **"Fortsetzen"** bereitgestellten Karten gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="ae88b-159">The Adaptive Card tab is updated by rendering the new list of cards provided in the tab **continue** response body.</span></span>

### <a name="invoke-taskfetch"></a><span data-ttu-id="ae88b-160">Aufrufen `task/fetch`</span><span class="sxs-lookup"><span data-stu-id="ae88b-160">Invoke `task/fetch`</span></span>

<span data-ttu-id="ae88b-161">Der folgende Code enthält Beispiele für `task/fetch` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="ae88b-161">The following code provides examples of `task/fetch` request and response:</span></span>

<span data-ttu-id="ae88b-162">**`task/fetch` Anfrage**</span><span class="sxs-lookup"><span data-stu-id="ae88b-162">**`task/fetch` request**</span></span>
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

<span data-ttu-id="ae88b-163">**`task/fetch` Antwort**</span><span class="sxs-lookup"><span data-stu-id="ae88b-163">**`task/fetch` response**</span></span>

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

### <a name="invoke-tasksubmit"></a><span data-ttu-id="ae88b-164">Aufrufen `task/submit`</span><span class="sxs-lookup"><span data-stu-id="ae88b-164">Invoke `task/submit`</span></span>

<span data-ttu-id="ae88b-165">Der folgende Code enthält Beispiele für `task/submit` Anforderung und Antwort:</span><span class="sxs-lookup"><span data-stu-id="ae88b-165">The following code provides examples of `task/submit` request and response:</span></span>

<span data-ttu-id="ae88b-166">**`task/submit` Anfrage**</span><span class="sxs-lookup"><span data-stu-id="ae88b-166">**`task/submit` request**</span></span>

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

<span data-ttu-id="ae88b-167">**`task/submit` Registerkartenantworttyp**</span><span class="sxs-lookup"><span data-stu-id="ae88b-167">**`task/submit` tab response type**</span></span>

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

## <a name="authentication"></a><span data-ttu-id="ae88b-168">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="ae88b-168">Authentication</span></span>

<span data-ttu-id="ae88b-169">In den vorherigen Abschnitten dieses Artikels haben Sie gesehen, dass die meisten Entwicklungsparadigmen aus den Aufgabenmodulanforderungen und -antworten in Registerkartenanforderungen und -antworten erweitert werden können.</span><span class="sxs-lookup"><span data-stu-id="ae88b-169">In the previous sections of this article, you have seen that most of the development paradigms can be extended from the task module requests and responses into tab requests and responses.</span></span> <span data-ttu-id="ae88b-170">Wenn es um die Behandlung der Authentifizierung geht, folgt der Workflow für die Registerkarte "Adaptive Karte" dem Authentifizierungsmuster für Messaging-Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="ae88b-170">When it comes to handling authentication, the workflow for Adaptive Card tab follows the authentication pattern for messaging extensions.</span></span> <span data-ttu-id="ae88b-171">Weitere Informationen finden Sie unter Hinzufügen der [Authentifizierung.](../../messaging-extensions/how-to/add-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="ae88b-171">For more information, see [add authentication](../../messaging-extensions/how-to/add-authentication.md).</span></span>

<span data-ttu-id="ae88b-172">`tab/fetch` Anforderungen können entweder eine **Fortsetzungs-** oder eine **Authentifizierungsantwort** haben.</span><span class="sxs-lookup"><span data-stu-id="ae88b-172">`tab/fetch` requests can have either a **continue** or an **auth** response.</span></span> <span data-ttu-id="ae88b-173">Wenn eine `tab/fetch` Anforderung ausgelöst wird und eine Registerkartenauthentifizierungsantwort empfängt, wird dem Benutzer die Anmeldeseite angezeigt. </span><span class="sxs-lookup"><span data-stu-id="ae88b-173">When a `tab/fetch` request is triggered and receives a tab **auth** response, the sign-in page is shown to the user.</span></span>

<span data-ttu-id="ae88b-174">**So rufen Sie einen Authentifizierungscode durch Aufrufen ab `tab/fetch`**</span><span class="sxs-lookup"><span data-stu-id="ae88b-174">**To get an authentication code through `tab/fetch` invoke**</span></span>

1. <span data-ttu-id="ae88b-175">Öffnen Sie Ihre App.</span><span class="sxs-lookup"><span data-stu-id="ae88b-175">Open your app.</span></span> <span data-ttu-id="ae88b-176">Die Anmeldeseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-176">The sign in page appears.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ae88b-177">Das App-Logo wird über die `icon` im App-Manifest definierte Eigenschaft bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ae88b-177">The app logo is provided through the `icon` property defined in the app manifest.</span></span> <span data-ttu-id="ae88b-178">Der Titel, der angezeigt wird, nachdem das Logo in der Eigenschaft definiert wurde, `title` die im Antworttext der **Registerkartenauthentifizierung** zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="ae88b-178">The title appearing after the logo is defined in the `title` property returned in the tab **auth** response body.</span></span>

1. <span data-ttu-id="ae88b-179">Wählen Sie **Anmelden** aus.</span><span class="sxs-lookup"><span data-stu-id="ae88b-179">Select **Sign in**.</span></span> <span data-ttu-id="ae88b-180">Sie werden zu der Authentifizierungs-URL umgeleitet, die in der `value` Eigenschaft des **Authentifizierungsantworttexts** angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="ae88b-180">You are redirected to the authentication URL provided in the `value` property of the **auth** response body.</span></span>
1. <span data-ttu-id="ae88b-181">Ein Popupfenster wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="ae88b-181">A pop-up window appears.</span></span> <span data-ttu-id="ae88b-182">In diesem Popupfenster wird Ihre Webseite mithilfe der Authentifizierungs-URL gehostet.</span><span class="sxs-lookup"><span data-stu-id="ae88b-182">This pop-up window hosts your web page using the authentication URL.</span></span>
1. <span data-ttu-id="ae88b-183">Schließen Sie nach der Anmeldung das Fenster.</span><span class="sxs-lookup"><span data-stu-id="ae88b-183">After you sign in, close the window.</span></span> <span data-ttu-id="ae88b-184">Ein **Authentifizierungscode** wird an den Teams Client gesendet.</span><span class="sxs-lookup"><span data-stu-id="ae88b-184">An **authentication code** is sent to the Teams client.</span></span>
1. <span data-ttu-id="ae88b-185">Der Teams-Client sendet dann die `tab/fetch` Anforderung erneut an Ihren Dienst, der den von Ihrer gehosteten Webseite bereitgestellten Authentifizierungscode enthält.</span><span class="sxs-lookup"><span data-stu-id="ae88b-185">The Teams client then reissues the `tab/fetch` request to your service, which includes the authentication code provided by your hosted web page.</span></span>

### <a name="tabfetch-authentication-data-flow"></a><span data-ttu-id="ae88b-186">`tab/fetch` Authentifizierungsdatenfluss</span><span class="sxs-lookup"><span data-stu-id="ae88b-186">`tab/fetch` authentication data flow</span></span>

<span data-ttu-id="ae88b-187">Die folgende Abbildung enthält eine Übersicht über die Funktionsweise des Authentifizierungsdatenflusses für einen `tab/fetch` Aufruf.</span><span class="sxs-lookup"><span data-stu-id="ae88b-187">The following image provides an overview of how the authentication data flow works for a `tab/fetch` invoke.</span></span>

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Beispiel für den Authentifizierungsfluss für adaptive Kartenregisterkarten." border="false":::

<span data-ttu-id="ae88b-189">**`tab/fetch` Authentifizierungsantwort**</span><span class="sxs-lookup"><span data-stu-id="ae88b-189">**`tab/fetch` auth response**</span></span>

<span data-ttu-id="ae88b-190">Der folgende Code enthält ein Beispiel für die `tab/fetch` Authentifizierungsantwort:</span><span class="sxs-lookup"><span data-stu-id="ae88b-190">The following code provides an example of `tab/fetch` auth response:</span></span>

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

### <a name="example"></a><span data-ttu-id="ae88b-191">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ae88b-191">Example</span></span>

<span data-ttu-id="ae88b-192">Der folgende Code zeigt ein neu ausgestelltes Anforderungsbeispiel:</span><span class="sxs-lookup"><span data-stu-id="ae88b-192">The following code shows a reissued request example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ae88b-193">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ae88b-193">See also</span></span>

* [<span data-ttu-id="ae88b-194">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="ae88b-194">Adaptive Card</span></span>](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [<span data-ttu-id="ae88b-195">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="ae88b-195">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="ae88b-196">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ae88b-196">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="ae88b-197">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ae88b-197">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="ae88b-198">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="ae88b-198">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="ae88b-199">Erstellen einer Inhaltsseite</span><span class="sxs-lookup"><span data-stu-id="ae88b-199">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="ae88b-200">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="ae88b-200">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [<span data-ttu-id="ae88b-201">Erstellen einer Seite zum Entfernen ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="ae88b-201">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="ae88b-202">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="ae88b-202">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="ae88b-203">Kontext für Ihre Registerkarte erhalten</span><span class="sxs-lookup"><span data-stu-id="ae88b-203">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="ae88b-204">Registerkarten für Unterhaltungen erstellen</span><span class="sxs-lookup"><span data-stu-id="ae88b-204">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)
* [<span data-ttu-id="ae88b-205">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="ae88b-205">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)

## <a name="next-step"></a><span data-ttu-id="ae88b-206">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ae88b-206">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae88b-207">Aufgeklappte Registerkartenverknüpfung und Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="ae88b-207">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)