---
title: Erstellen eines virtuellen Assistenten
description: Erstellen von virtuellen Assistenten-Bots und -Fähigkeiten für die Verwendung in Microsoft Teams
localization_priority: Normal
ms.topic: how-to
keywords: teams Virtual Assistant Bots
ms.openlocfilehash: 072d9cb5742cd39101587cad32e3048bd36cc1d8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566873"
---
# <a name="create-virtual-assistant"></a><span data-ttu-id="f10b7-104">Erstellen eines virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="f10b7-104">Create Virtual Assistant</span></span> 

<span data-ttu-id="f10b7-105">Der virtuelle Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzeroberfläche, das Unternehmensbranding und die erforderlichen Daten beibehalten können.</span><span class="sxs-lookup"><span data-stu-id="f10b7-105">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> <span data-ttu-id="f10b7-106">Die [Kernvorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) des virtuellen Assistenten ist der grundlegende Baustein, der die zum Erstellen eines virtuellen Assistenten erforderlichen Microsoft-Technologien zusammen bringt, einschließlich [bot Framework SDK,](https://github.com/microsoft/botframework-sdk)Language Understanding [(LUS)](https://www.luis.ai/)und [QnA Maker](https://www.qnamaker.ai/).</span><span class="sxs-lookup"><span data-stu-id="f10b7-106">The [Virtual Assistant core template](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) is the basic building block that brings together the Microsoft technologies required to build a Virtual Assistant, including the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/), and [QnA Maker](https://www.qnamaker.ai/).</span></span> <span data-ttu-id="f10b7-107">Außerdem werden die wesentlichen Funktionen wie die Registrierung von Fähigkeiten, verknüpfte Konten und grundlegende Unterhaltungsabsichten zusammengekoppelt, um Benutzern eine Reihe nahtloser Interaktionen und Erfahrungen zu bieten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-107">It also brings together the essential capabilities including  skills registration, linked accounts, basic conversational intent to offer a range of seamless interactions and experiences to users.</span></span> <span data-ttu-id="f10b7-108">Darüber hinaus enthalten die Vorlagenfunktionen umfassende Beispiele für wiederverwendbare [Unterhaltungskenntnisse.](https://microsoft.github.io/botframework-solutions/overview/skills)</span><span class="sxs-lookup"><span data-stu-id="f10b7-108">In addition, the template capabilities include rich examples of reusable conversational [skills](https://microsoft.github.io/botframework-solutions/overview/skills).</span></span>  <span data-ttu-id="f10b7-109">Individuelle Fähigkeiten werden in eine Virtual Assistant-Lösung integriert, um mehrere Szenarien zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-109">Individual skills are integrated in a Virtual Assistant solution to enable multiple scenarios.</span></span> <span data-ttu-id="f10b7-110">Mithilfe des Bot Framework SDK werden Die Fähigkeiten im Quellcode dargestellt, sodass Sie die Funktionen nach Bedarf anpassen und erweitern können.</span><span class="sxs-lookup"><span data-stu-id="f10b7-110">Using the Bot Framework SDK, skills are presented in source code form, enabling you to customize and extend as required.</span></span> <span data-ttu-id="f10b7-111">Weitere Informationen zu den Fähigkeiten von Bot Framework finden Sie unter [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="f10b7-111">For more information on skills of Bot Framework, see [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="f10b7-112">Dieses Dokument führt Sie zu Überlegungen zur Implementierung des virtuellen Assistenten für Organisationen, zum Erstellen eines Teams-fokussierten virtuellen Assistenten, zugehörigen Beispielen, Codebeispielen und Einschränkungen des virtuellen Assistenten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-112">This document guides you on Virtual Assistant implementation considerations for organizations, how to create a Teams focused Virtual Assistant, related example, code sample, and limitations of Virtual Assistant.</span></span>
<span data-ttu-id="f10b7-113">Die folgende Abbildung zeigt die Übersicht über den virtuellen Assistenten:</span><span class="sxs-lookup"><span data-stu-id="f10b7-113">The following image displays the overview of virtual assistant:</span></span>

![Übersichtsdiagramm des virtuellen Assistenten](../assets/images/bots/virtual-assistant/overview.png)

<span data-ttu-id="f10b7-115">Textnachrichtenaktivitäten werden vom Kern des virtuellen Assistenten mithilfe eines Versandmodells an [zugeordnete Fähigkeiten geroutet.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="f10b7-115">Text message activities are routed to associated skills by the Virtual Assistant core using a [dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) model.</span></span> 

## <a name="implementation-considerations"></a><span data-ttu-id="f10b7-116">Überlegungen zur Implementierung</span><span class="sxs-lookup"><span data-stu-id="f10b7-116">Implementation considerations</span></span>

<span data-ttu-id="f10b7-117">Die Entscheidung, einen virtuellen Assistenten hinzuzufügen, umfasst viele Determinanten und unterscheidet sich für jede Organisation.</span><span class="sxs-lookup"><span data-stu-id="f10b7-117">The decision to add a Virtual Assistant includes many determinants and differs for each organization.</span></span> <span data-ttu-id="f10b7-118">Die unterstützenden Faktoren einer Virtual Assistant-Implementierung für Ihre Organisation sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-118">The supporting factors of a Virtual Assistant implementation for your organization are as follows:</span></span>

* <span data-ttu-id="f10b7-119">Ein zentrales Team verwaltet alle Mitarbeitererfahrungen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-119">A central team manages all employee experiences.</span></span> <span data-ttu-id="f10b7-120">Es verfügt über die Möglichkeit, eine virtuelle Assistentenerfahrung zu erstellen und Updates für die Kernerfahrung zu verwalten, einschließlich der Hinzu ergänzung neuer Fähigkeiten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-120">It has the capability to build a Virtual Assistant experience and manage updates to the core experience including the addition of new skills.</span></span>
* <span data-ttu-id="f10b7-121">Mehrere Anwendungen sind in verschiedenen Geschäftsfunktionen vorhanden, und die Anzahl wird in Zukunft voraussichtlich zunehmen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-121">Multiple applications exist across business functions and the number is expected to grow in the future.</span></span>
* <span data-ttu-id="f10b7-122">Vorhandene Anwendungen sind anpassbar, gehören der Organisation und werden in Fertigkeiten für einen virtuellen Assistenten umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-122">Existing applications are customizable, owned by the organization, and are converted into skills for a Virtual Assistant.</span></span>
* <span data-ttu-id="f10b7-123">Das team für zentrale Mitarbeitererfahrungen ist in der Lage, Anpassungen an vorhandenen Apps zu beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-123">The central employee experiences team is able to influence customizations to existing apps.</span></span> <span data-ttu-id="f10b7-124">Sie bietet außerdem die erforderlichen Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in der Virtuellen Assistenten-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="f10b7-124">It also provides necessary guidance for integrating existing applications as skills in Virtual Assistant experience.</span></span>

<span data-ttu-id="f10b7-125">In der folgenden Abbildung werden die Geschäftsfunktionen des virtuellen Assistenten angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-125">The following image displays the business functions of Virtual Assistant:</span></span> 

![Zentrales Team pflegt den Assistenten, und Geschäftsfunktionsteams tragen Fähigkeiten bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a><span data-ttu-id="f10b7-127">Erstellen eines Teams virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="f10b7-127">Create a Teams-focused Virtual Assistant</span></span>

<span data-ttu-id="f10b7-128">Microsoft hat eine Visual Studio [zum](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) Erstellen virtueller Assistenten und Fähigkeiten veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="f10b7-128">Microsoft has published a [Visual Studio template](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) for building Virtual Assistants and skills.</span></span> <span data-ttu-id="f10b7-129">Mit der Visual Studio können Sie einen virtuellen Assistenten erstellen, der von einer textbasierten Erfahrung mit Unterstützung für eingeschränkte Rich Cards mit Aktionen unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="f10b7-129">With the Visual Studio template, you can create a Virtual Assistant, powered by a text based experience with support for limited rich cards with actions.</span></span> <span data-ttu-id="f10b7-130">Wir haben die Basisvorlage Visual Studio erweitert, um Microsoft Teams Plattformfunktionen und die Teams zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="f10b7-130">We have enhanced the Visual Studio base template to include Microsoft Teams platform capabilities and power great Teams app experiences.</span></span> <span data-ttu-id="f10b7-131">Einige der Funktionen umfassen unterstützung für umfangreiche adaptive Karten, Aufgabenmodule, Teams oder Gruppenchats und Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-131">A few of the capabilities include support for rich Adaptive Cards, task modules, teams or group chats, and messaging extensions.</span></span> <span data-ttu-id="f10b7-132">Weitere Informationen zum Erweitern des virtuellen Assistenten auf Microsoft Teams finden Sie unter [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span><span class="sxs-lookup"><span data-stu-id="f10b7-132">For more information on extending Virtual Assistant to Microsoft Teams, see [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span></span>    
<span data-ttu-id="f10b7-133">Die folgende Abbildung zeigt das Diagramm auf hoher Ebene einer Virtuellen Assistentenlösung:</span><span class="sxs-lookup"><span data-stu-id="f10b7-133">The following image displays the high level diagram of a Virtual Assistant solution:</span></span>

![Diagramm einer virtuellen Assistentenlösung auf hoher Ebene](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a><span data-ttu-id="f10b7-135">Hinzufügen adaptiver Karten zu Ihrem virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="f10b7-135">Add Adaptive Cards to your Virtual Assistant</span></span>

<span data-ttu-id="f10b7-136">Damit Anforderungen ordnungsgemäß versendet werden können, muss Ihr virtueller Assistent das richtige MODELL FÜR DAS MODELL und die entsprechenden ihm zugeordneten Fähigkeiten identifizieren.</span><span class="sxs-lookup"><span data-stu-id="f10b7-136">To dispatch requests properly, your Virtual Assistant must identify the correct LUIS model and corresponding skill associated with it.</span></span> <span data-ttu-id="f10b7-137">Der Verteilmechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das einem Skill zugeordnete MODELL FÜR KARTENaktionen für Kartenaktionstexte geschult wird.</span><span class="sxs-lookup"><span data-stu-id="f10b7-137">However, the dispatching mechanism cannot be used for card action activities as the LUIS model associated with a skill, is trained for card action texts.</span></span> <span data-ttu-id="f10b7-138">Die Kartenaktionstexte sind feste, vordefinierte Schlüsselwörter und werden nicht von einem Benutzer kommentiert.</span><span class="sxs-lookup"><span data-stu-id="f10b7-138">The card action texts are fixed, pre-defined keywords, and not commented from a user.</span></span>

<span data-ttu-id="f10b7-139">Dieser Nachteil wird durch Einbetten von Qualifikationsinformationen in die Kartenaktionsnutzlast behoben.</span><span class="sxs-lookup"><span data-stu-id="f10b7-139">This drawback is resolved this by embedding skill information in the card action payload.</span></span> <span data-ttu-id="f10b7-140">Jede Fertigkeit sollte `skillId` in das Feld der  `value` Kartenaktionen eingebettet werden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-140">Every skill should embed `skillId` in the  `value` field of card actions.</span></span> <span data-ttu-id="f10b7-141">Sie müssen sicherstellen, dass jede Kartenaktionsaktivität die relevanten Fertigkeiteninformationen enthält, und der virtuelle Assistent kann diese Informationen für die Versendung verwenden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-141">You must ensure that each card action activity carries the relevant skill information, and Virtual Assistant can utilize this information for dispatching.</span></span>

<span data-ttu-id="f10b7-142">Sie müssen im Konstruktor bereitstellen, um sicherzustellen, dass die Fertigkeiteninformationen immer `skillId` in Kartenaktionen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="f10b7-142">You must provide `skillId` in the constructor to ensure that the skill information is always present in card actions.</span></span>
<span data-ttu-id="f10b7-143">Ein Beispielcode für Kartenaktionsdaten wird im folgenden Abschnitt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-143">A card action data sample code is shown in the following section:</span></span>
```csharp
    public class CardActionData
    {
        public CardActionData(string skillId)
        {
            this.SkillId = skillId;
        }

        [JsonProperty("skillId")]
        public string SkillId { get; set; }
    }

    ...
    var button = new CardAction
    {
        Type = ActionTypes.MessageBack,
        Title = "Card action button",
        Text = "card action button text",
        Value = new CardActionData(<SkillId>),
    };
```

<span data-ttu-id="f10b7-144">Als Nächstes wird die Klasse in der Vorlage Virtueller Assistent zum Extrahieren aus der Nutzlast der `SkillCardActionData` `skillId` Kartenaktion präsentiert.</span><span class="sxs-lookup"><span data-stu-id="f10b7-144">Next, `SkillCardActionData` class in the Virtual Assistant template is introduces to extract `skillId` from the card action payload.</span></span>
<span data-ttu-id="f10b7-145">Ein Codeausschnitt, der aus der Nutzlast der Kartenaktion extrahiert werden  `skillId` soll, wird im folgenden Abschnitt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-145">A code snippet to extract  `skillId` from card action payload is shown in the following section:</span></span>

```csharp
    // Skill Card action data should contain skillId parameter
    // This class is used to deserialize it and get skillId 
    public class SkillCardActionData
    {
        /// <summary>
        /// Gets the ID of the skil that should handle this card
        /// </summary>
        [JsonProperty("skillId")]
        public string SkillId { get; set; }
    }
```

<span data-ttu-id="f10b7-146">Die Implementierung erfolgt über eine Erweiterungsmethode in der [Activity-Klasse.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)</span><span class="sxs-lookup"><span data-stu-id="f10b7-146">The implementation is done by an extension method in the [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) class.</span></span>
<span data-ttu-id="f10b7-147">Ein Codeausschnitt zum Extrahieren  `skillId` aus Kartenaktionsdaten wird im folgenden Abschnitt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-147">A code snippet to extract  `skillId` from card action data is shown in the following section:</span></span>

```csharp
    public static class ActivityExtensions
    {
        // Fetches skillId from CardAction data if present
        public static string GetSkillId(this Activity activity)
        {
            string skillId = string.Empty;

            try
            {
                if (activity.Type.Equals(ActivityTypes.Message) && activity.Value != null)
                {
                    var data = JsonConvert.DeserializeObject<SkillCardActionData>(activity.Value.ToString());
                    skillId = data.SkillId;
                }
                else if (activity.Type.Equals(ActivityTypes.Invoke) && activity.Value != null)
                {
                    var data = JsonConvert.DeserializeObject<SkillCardActionData>(JObject.Parse(activity.Value.ToString()).SelectToken("data").ToString());
                    skillId = data.SkillId;
                }
            }
            catch
            {
                // If not able to retrive skillId, empty skillId should be returned
            }

            return skillId;
        }
    }
```

### <a name="handle-interruptions"></a><span data-ttu-id="f10b7-148">Behandeln von Unterbrechungen</span><span class="sxs-lookup"><span data-stu-id="f10b7-148">Handle interruptions</span></span>

<span data-ttu-id="f10b7-149">Der virtuelle Assistent kann Unterbrechungen in Fällen verarbeiten, in denen ein Benutzer versucht, eine Fähigkeit aufrief, während eine andere Fähigkeit derzeit aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="f10b7-149">Virtual Assistant can handle interruptions in cases where a user tries to invoke a skill while another skill is currently active.</span></span> <span data-ttu-id="f10b7-150">`TeamsSkillDialog`und `TeamsSwitchSkillDialog` werden basierend auf Den [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von Bot Framework eingeführt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-150">`TeamsSkillDialog`, and `TeamsSwitchSkillDialog`are introduced based on Bot Framework's [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) and [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs).</span></span> <span data-ttu-id="f10b7-151">Sie ermöglichen Benutzern das Wechseln einer Kompetenzerfahrung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-151">They enable users to switch a skill experience from card actions.</span></span> <span data-ttu-id="f10b7-152">Um diese Anforderung zu verarbeiten, fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsnachricht auf, die Fähigkeiten zu wechseln:</span><span class="sxs-lookup"><span data-stu-id="f10b7-152">To handle this request, the Virtual Assistant prompts the user with a confirmation message to switch skills:</span></span>

![Bestätigungsaufforderung beim Wechseln zu einer neuen Fertigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a><span data-ttu-id="f10b7-154">Behandeln von Aufgabenmodulanforderungen</span><span class="sxs-lookup"><span data-stu-id="f10b7-154">Handle task module requests</span></span>

<span data-ttu-id="f10b7-155">Zum Hinzufügen von Aufgabenmodulfunktionen zu einem virtuellen Assistenten sind zwei zusätzliche Methoden im Aktivitätshandler des virtuellen Assistenten `OnTeamsTaskModuleFetchAsync` enthalten: und `OnTeamsTaskModuleSubmitAsync` .</span><span class="sxs-lookup"><span data-stu-id="f10b7-155">To add task module capabilities to a Virtual Assistant, two additional methods are included in the Virtual Assistant activity handler: `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync`.</span></span> <span data-ttu-id="f10b7-156">Diese Methoden lauschen aufgabenmodulbezogenen Aktivitäten vom virtuellen Assistenten, identifizieren die der Anforderung zugeordneten Fähigkeiten und geben die Anforderung an die identifizierte Fähigkeit weiter.</span><span class="sxs-lookup"><span data-stu-id="f10b7-156">These methods listen to task module-related activities from Virtual Assistant, identify the skill associated with the request, and forward the request to the identified skill.</span></span> 

<span data-ttu-id="f10b7-157">Die Anforderungs weiterleitung erfolgt über die [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true), `PostActivityAsync` -Methode.</span><span class="sxs-lookup"><span data-stu-id="f10b7-157">Request forwarding is done through the [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true), `PostActivityAsync` method.</span></span> <span data-ttu-id="f10b7-158">Es gibt die Antwort `InvokeResponse` zurück, die analysiert und in konvertiert `TaskModuleResponse` wird.</span><span class="sxs-lookup"><span data-stu-id="f10b7-158">It returns the response as `InvokeResponse` which is parsed and converted to `TaskModuleResponse` .</span></span>


```csharp
    public static TaskModuleResponse GetTaskModuleRespose(this InvokeResponse invokeResponse)
    {
        if (invokeResponse.Body != null)
        {
            return new TaskModuleResponse()
            {
                Task = GetTask(invokeResponse.Body),
            };
        }

        return null;
    }

    private static TaskModuleResponseBase GetTask(object invokeResponseBody)
        {
            JObject resposeBody = (JObject)JToken.FromObject(invokeResponseBody);
            var task = resposeBody.GetValue("task");
            var taskType = task.SelectToken("type").ToString();

            return taskType switch
            {
                "continue" => new TaskModuleContinueResponse()
                {
                    Type = taskType,
                    Value = task.SelectToken("value").ToObject<TaskModuleTaskInfo>(),
                },
                "message" => new TaskModuleMessageResponse()
                {
                    Type = taskType,
                    Value = task.SelectToken("value").ToString(),
                },
                _ => null,
            };
        }
```

<span data-ttu-id="f10b7-159">Ein ähnlicher Ansatz wird für kartenaktionsversand und Aufgabenmodulantworten verwendet.</span><span class="sxs-lookup"><span data-stu-id="f10b7-159">A similar approach is followed for card action dispatching and task module responses.</span></span> <span data-ttu-id="f10b7-160">Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird so aktualisiert, dass sie enthalten `skillId` sind.</span><span class="sxs-lookup"><span data-stu-id="f10b7-160">Task module fetch and submit action data is updated to include `skillId`.</span></span> <span data-ttu-id="f10b7-161">Die Activity Extension-Methode extrahiert aus der Nutzlast, die Details zu den Fähigkeiten `GetSkillId` `skillId` enthält, die aufgerufen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-161">Activity Extension method `GetSkillId` extracts `skillId` from the payload which provides details about the skill that needs to be invoked.</span></span>

<span data-ttu-id="f10b7-162">Der Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und die Methoden finden Sie im folgenden `OnTeamsTaskModuleSubmitAsync` Abschnitt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-162">The code snippet for `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync` methods are given in the following section:</span></span>

```csharp
    // Invoked when a "task/fetch" event is received to invoke task module.
    protected override async Task<TaskModuleResponse> OnTeamsTaskModuleFetchAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
    {
        try
        {
            string skillId = (turnContext.Activity as Activity).GetSkillId();
            var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == skillId).First().Value;

            // Forward request to correct skill
            var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken);

            return invokeResponse.GetTaskModuleRespose();
        }
        catch (Exception exception)
        {
            await turnContext.SendActivityAsync(_templateEngine.GenerateActivityForLocale("ErrorMessage"));
            _telemetryClient.TrackException(exception);

            return null;
        }
    }

    // Invoked when a 'task/submit' invoke activity is received for task module submit actions.
    protected override async Task<TaskModuleResponse> OnTeamsTaskModuleSubmitAsync(ITurnContext<IInvokeActivity> turnContext, TaskModuleRequest taskModuleRequest, CancellationToken cancellationToken)
    {
        try
        {
            string skillId = (turnContext.Activity as Activity).GetSkillId();
            var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == skillId).First().Value;

            // Forward request to correct skill
            var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken).ConfigureAwait(false);

            return invokeResponse.GetTaskModuleRespose();
        }
        catch (Exception exception)
        {
            await turnContext.SendActivityAsync(_templateEngine.GenerateActivityForLocale("ErrorMessage"));
            _telemetryClient.TrackException(exception);

            return null;
        }
    }
```

<span data-ttu-id="f10b7-163">Darüber hinaus müssen Sie alle Kompetenzdomänen in den Abschnitt in die Manifestdatei des virtuellen Assistenten hinzufügen, damit Aufgabenmodule, die über eine Fähigkeit aufgerufen werden, ordnungsgemäß `validDomains` gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-163">Additionally, you must include all skill domains in the `validDomains` section in Virtual Assistant's manifest file so that task modules invoked through a skill render properly.</span></span>

### <a name="handle-collaborative-app-scopes"></a><span data-ttu-id="f10b7-164">Behandeln kollaborativer App-Bereiche</span><span class="sxs-lookup"><span data-stu-id="f10b7-164">Handle collaborative app scopes</span></span>

<span data-ttu-id="f10b7-165">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span><span class="sxs-lookup"><span data-stu-id="f10b7-165">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span></span> <span data-ttu-id="f10b7-166">Die zentrale Vorlage für den virtuellen Assistenten ist für 1:1-Chats konzipiert.</span><span class="sxs-lookup"><span data-stu-id="f10b7-166">The core Virtual Assistant template is designed for 1:1 chats.</span></span> <span data-ttu-id="f10b7-167">Im Rahmen der Onboardingerfahrung fordert der virtuelle Assistent Benutzer zum Namen auf und behält den Benutzerstatus bei.</span><span class="sxs-lookup"><span data-stu-id="f10b7-167">As part of the onboarding experience Virtual Assistant prompts users for name and maintains user state.</span></span> <span data-ttu-id="f10b7-168">Da diese Onboardingerfahrung nicht für Gruppenchat- oder Kanalbereiche geeignet ist, wurde sie entfernt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-168">Since that onboarding experience is not suited for group chat or channel scopes it has been removed.</span></span>

<span data-ttu-id="f10b7-169">Fähigkeiten sollten Aktivitäten in mehreren Bereich behandeln, z. B. 1:1-Chat, Gruppenchat und Kanalunterhaltung.</span><span class="sxs-lookup"><span data-stu-id="f10b7-169">Skills should handle activities in multiple scopes, such as 1:1 chat, group chat, and channel conversation.</span></span> <span data-ttu-id="f10b7-170">Wenn einer dieser Bereiche nicht unterstützt wird, müssen Die Qualifikationen mit einer entsprechenden Nachricht antworten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-170">If any of these scopes are not supported, skills must respond with an appropriate message.</span></span>

<span data-ttu-id="f10b7-171">Die folgenden Verarbeitungsfunktionen wurden zu Virtual Assistant Core hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-171">The following  processing functions have been added to Virtual Assistant core:</span></span>

* <span data-ttu-id="f10b7-172">Der virtuelle Assistent kann ohne Textnachricht aus einem Gruppenchat oder -kanal aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-172">Virtual Assistant can be invoked without any text message from a group chat or channel.</span></span>
* <span data-ttu-id="f10b7-173">Artikulationen werden vor dem Senden der Nachricht an das Verteilermodul bereinigt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-173">Articulations are cleaned before sending the message to the dispatch module.</span></span> <span data-ttu-id="f10b7-174">Entfernen Sie z. B. die @mention des Bots.</span><span class="sxs-lookup"><span data-stu-id="f10b7-174">For example, remove the necessary @mention of the bot.</span></span>

```csharp
    if (innerDc.Context.Activity.Conversation?.IsGroup == true)
    {
        // Remove bot atmentions for teams/groupchat scope
        innerDc.Context.Activity.RemoveRecipientMention();

        // If bot is invoked without any text, reply with FirstPromptMessage
        if (string.IsNullOrWhiteSpace(innerDc.Context.Activity.Text))
        {
            await innerDc.Context.SendActivityAsync(_templateEngine.GenerateActivityForLocale("FirstPromptMessage"));
            return EndOfTurn;
        }
    }
```

### <a name="handle-messaging-extensions"></a><span data-ttu-id="f10b7-175">Behandeln von Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="f10b7-175">Handle messaging extensions</span></span>

<span data-ttu-id="f10b7-176">Die Befehle für eine Messagingerweiterung werden in Ihrer App-Manifestdatei deklariert.</span><span class="sxs-lookup"><span data-stu-id="f10b7-176">The commands for a messaging extension are declared in your app manifest file.</span></span> <span data-ttu-id="f10b7-177">Die Benutzeroberfläche der Messagingerweiterung wird von diesen Befehlen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-177">The messaging extension user interface is powered by those commands.</span></span> <span data-ttu-id="f10b7-178">Damit ein virtueller Assistent einen Befehl zur Nachrichtenerweiterung als angefügte Fähigkeit ausführen kann, muss das eigene Manifest eines virtuellen Assistenten diese Befehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-178">For a Virtual Assistant to power a messaging extension command as an attached skill, a Virtual Assistant's own manifest must contain those commands.</span></span> <span data-ttu-id="f10b7-179">Sie müssen die Befehle aus dem Manifest einer einzelnen Fähigkeit zum Manifest des virtuellen Assistenten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-179">You must add the commands from an individual skill's manifest to the Virtual Assistant's manifest.</span></span> <span data-ttu-id="f10b7-180">Die Befehls-ID enthält Informationen zu einer zugeordneten Fähigkeit, indem die App-ID der Fähigkeit über ein Trennzeichen angefügt `:` wird.</span><span class="sxs-lookup"><span data-stu-id="f10b7-180">The command ID provides information about an associated skill by appending the skill's app ID through a separator `:`.</span></span>

<span data-ttu-id="f10b7-181">Der Codeausschnitt aus der Manifestdatei einer Fähigkeit wird im folgenden Abschnitt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-181">The snippet from a skill's manifest file is shown in the following section:</span></span>

```json
 "composeExtensions": [
    {
        "botId": "<Skil_App_Id>",
        "commands": [
            {
                "id": "searchQuery",
                "context": [ "compose", "commandBox" ],
                "description": "Test command to run query",
    ....
```

<span data-ttu-id="f10b7-182">Der entsprechende Codeausschnitt der Manifestdatei des virtuellen Assistenten wird im folgenden Abschnitt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-182">The corresponding Virtual Assistant manifest file code snippet is shown in the following section:</span></span>

```json
 "composeExtensions": [
    {
        "botId": "<VA_App_Id>",
        "commands": [
            {
                "id": "searchQuery:<skill_id>",
                "context": [ "compose", "commandBox" ],
                "description": "Test command to run query",
    ....
```

<span data-ttu-id="f10b7-183">Sobald die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent eine zugeordnete Fähigkeit identifizieren, indem er die Befehls-ID durch Analyse der Befehls-ID identifiziert, die Aktivität aktualisiert, indem das zusätzliche Suffix aus der Befehls-ID entfernt wird, und es an die entsprechende Fähigkeit `:<skill_id>` weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-183">Once the commands are invoked by a user, the Virtual Assistant can identify an associated skill by parsing the command ID, update the activity by removing the extra suffix `:<skill_id>` from the command ID,  and forward it to the corresponding skill.</span></span> <span data-ttu-id="f10b7-184">Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-184">The code for a skill doesnot need to handle the extra suffix.</span></span> <span data-ttu-id="f10b7-185">Auf diese Weise werden Konflikte zwischen Befehls-IDs über Die Fähigkeiten hinweg vermieden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-185">Thus, conflicts between command IDs across skills are avoided.</span></span> <span data-ttu-id="f10b7-186">Bei diesem Ansatz werden alle Such- und Aktionsbefehle einer Fähigkeit in allen Kontexten, z. B. **verfassen,** **commandBox** und **Nachricht,** von einem virtuellen Assistenten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-186">With this approach, all the search and action commands of a skill within all contexts, such as **compose**, **commandBox**, and **message** are powered by a Virtual Assistant.</span></span>

```csharp
    const string MessagingExtensionCommandIdSeparator = ":";

    // Invoked when a 'composeExtension/submitAction' invoke activity is received for a messaging extension action command
    protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
    {
        return await ForwardMessagingExtensionActionCommandActivityToSkill(turnContext, action, cancellationToken);
    }

    // Forwards invoke activity to right skill for messaging extension action commands.
    private async Task<MessagingExtensionActionResponse> ForwardMessagingExtensionActionCommandActivityToSkill(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
    {
        var skillId = ExtractSkillIdFromMessagingExtensionActionCommand(turnContext, action);
        var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == skillId).First().Value;
        var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken).ConfigureAwait(false);

        return invokeResponse.GetMessagingExtensionActionResponse();
    }

    // Extracts skill Id from messaging extension command and updates activity value
    private string ExtractSkillIdFromMessagingExtensionActionCommand(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action)
    {
        var commandArray = action.CommandId.Split(MessagingExtensionCommandIdSeparator);
        var skillId = commandArray.Last();

        // Update activity value by removing skill id before forwarding to the skill.
        var activityValue = JsonConvert.DeserializeObject<MessagingExtensionAction>(turnContext.Activity.Value.ToString());
        activityValue.CommandId = string.Join(MessagingExtensionCommandIdSeparator, commandArray, 0 commandArray.Length - 1);
        turnContext.Activity.Value = activityValue;

        return skillId;
    }
```

<span data-ttu-id="f10b7-187">Einige Messagingerweiterungsaktivitäten enthalten nicht die Befehls-ID.</span><span class="sxs-lookup"><span data-stu-id="f10b7-187">Some messaging extension activities do not include the command ID.</span></span> <span data-ttu-id="f10b7-188">Enthält beispielsweise `composeExtension/selectItem` nur den Wert der Aufruftippaktion.</span><span class="sxs-lookup"><span data-stu-id="f10b7-188">For example, `composeExtension/selectItem` contains only the value of the invoke tap action.</span></span> <span data-ttu-id="f10b7-189">Um die zugeordnete Fähigkeit zu identifizieren, wird jede Elementkarte `skillId`  angefügt, während sie eine Antwort für `OnTeamsMessagingExtensionQueryAsync` bildet.</span><span class="sxs-lookup"><span data-stu-id="f10b7-189">To identify the associated skill, `skillId`  is attached to each item card while forming a response for `OnTeamsMessagingExtensionQueryAsync`.</span></span> <span data-ttu-id="f10b7-190">Dies ähnelt dem Ansatz zum Hinzufügen [adaptiver Karten zu Ihrem virtuellen Assistenten.](#add-adaptive-cards-to-your-virtual-assistant)</span><span class="sxs-lookup"><span data-stu-id="f10b7-190">This is similar to the approach for [adding adaptive  cards to your Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).</span></span>

```csharp
    // Invoked when a 'composeExtension/selectItem' invoke activity is received for compose extension query command.
    protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionSelectItemAsync(ITurnContext<IInvokeActivity> turnContext, JObject query, CancellationToken cancellationToken)
    {
        var data = JsonConvert.DeserializeObject<SkillCardActionData>(query.ToString());
        var skill = _skillsConfig.Skills.Where(s => s.Value.AppId == data.SkillId).First().Value;
        var invokeResponse = await _skillHttpClient.PostActivityAsync(this._appId, skill, _skillsConfig.SkillHostEndpoint, turnContext.Activity as Activity, cancellationToken).ConfigureAwait(false);

        return invokeResponse.GetMessagingExtensionResponse();
    }
```

---

## <a name="example"></a><span data-ttu-id="f10b7-191">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f10b7-191">Example</span></span>

<span data-ttu-id="f10b7-192">Im folgenden Beispiel wird gezeigt, wie Sie die App-Vorlage "Book-a-room" in eine Virtuelle Assistent-Fähigkeit konvertieren: "Book-a-room" ist ein Microsoft Teams, mit dem Benutzer einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Zeit schnell finden und reservieren können.</span><span class="sxs-lookup"><span data-stu-id="f10b7-192">The following example shows how to convert the Book-a-room app template to a Virtual Assistant skill: Book-a-room is a Microsoft Teams that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="f10b7-193">Die Standardzeit beträgt 30 Minuten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-193">The default time is 30 minutes.</span></span> <span data-ttu-id="f10b7-194">Der Book-a-room-Bot bietet Bereiche für persönliche oder 1:1-Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-194">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="f10b7-195">In der folgenden Abbildung wird ein virtueller Assistent mit einem **Buch mit Raumfertigkeit** angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-195">The following image displays a Virtual Assistant with a **book a room** skill:</span></span>

![Virtueller Assistent mit einer "Raum reservieren"-Fähigkeit](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

<span data-ttu-id="f10b7-197">Nachfolgend finden Sie die delta-Änderungen, die eingeführt wurden, um sie in eine Fertigkeit zu konvertieren, die einem virtuellen Assistenten zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="f10b7-197">Followings are the delta changes introduced to convert it to a skill which is attached to a Virtual Assistant.</span></span> <span data-ttu-id="f10b7-198">Ähnliche Richtlinien werden befolgt, um vorhandene v4-Bots in eine Fertigkeit zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="f10b7-198">Similar guidelines are followed to convert any existing v4 bot to a skill.</span></span>

### <a name="skill-manifest"></a><span data-ttu-id="f10b7-199">Kompetenzmanifest</span><span class="sxs-lookup"><span data-stu-id="f10b7-199">Skill manifest</span></span>

<span data-ttu-id="f10b7-200">Ein Kompetenzmanifest ist eine JSON-Datei, die den Messagingendpunkt, die ID, den Namen und andere relevante Metadaten einer Fähigkeit verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="f10b7-200">A skill manifest is a JSON file that exposes a skill's messaging endpoint, ID, name, and other relevant metadata.</span></span> <span data-ttu-id="f10b7-201">Dieses Manifest ist anders als das Manifest, das zum Querladen einer App in einem Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f10b7-201">This manifest is different than the manifest used for sideloading an app in Microsoft Teams.</span></span> <span data-ttu-id="f10b7-202">Ein virtueller Assistent erfordert einen Pfad zu dieser Datei als Eingabe, um eine Fähigkeit anfügen zu können.</span><span class="sxs-lookup"><span data-stu-id="f10b7-202">A Virtual Assistant requires a path to this file as an input to attach a skill.</span></span> <span data-ttu-id="f10b7-203">Wir haben das folgende Manifest zum Wwwroot-Ordner des Bots hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-203">We have added the following manifest to the bot's wwwroot folder.</span></span>

```bash
botskills connect --remoteManifest "<url to skill's manifest>" ..
```

```json
{
  "$schema": "https://schemas.botframework.com/schemas/skills/skill-manifest-2.1.preview-0.json",
  "$id": "microsoft_teams_apps_bookaroom",
  "name": "microsoft-teams-apps-bookaroom",
  "description": "microsoft-teams-apps-bookaroom description",
  "publisherName": "Your Company",
  "version": "1.1",
  "iconUrl": "<icon url>",
  "copyright": "Copyright (c) Microsoft Corporation. All rights reserved.",
  "license": "",
  "privacyUrl": "<privacy url>",
  "endpoints": [
    {
      "name": "production",
      "protocol": "BotFrameworkV3",
      "description": "Production endpoint for the skill",
      "endpointUrl": "<endpoint url>",
      "msAppId": "skill app id"
    }
  ],
  "dispatchModels": {
    "languages": {
      "en-us": [
        {
          "id": "microsoft-teams-apps-bookaroom-en",
          "name": "microsoft-teams-apps-bookaroom LU (English)",
          "contentType": "application/lu",
          "url": "file://book-a-meeting.lu",
          "description": "English language model for the skill"
        }
      ]
    }
  },
  "activities": {
    "message": {
      "type": "message",
      "description": "Receives the users utterance and attempts to resolve it using the skill's LU models"
    }
  }
}
```

### <a name="luis-integration"></a><span data-ttu-id="f10b7-204">INTEGRATION VON LUS</span><span class="sxs-lookup"><span data-stu-id="f10b7-204">LUIS Integration</span></span>

<span data-ttu-id="f10b7-205">Das Versandmodell des virtuellen Assistenten baut auf den ZUGEHÖRIGEN MODELL-Modellen der angefügten Fähigkeiten auf.</span><span class="sxs-lookup"><span data-stu-id="f10b7-205">Virtual Assistant's dispatch model is built on top of attached skills' LUIS models.</span></span> <span data-ttu-id="f10b7-206">Das Versandmodell identifiziert die Absicht für jede Textaktivität und ermittelt die damit verbundenen Fähigkeiten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-206">The dispatch model identifies the intent for every text activity and finds out skill associated with it.</span></span>

<span data-ttu-id="f10b7-207">Für den virtuellen Assistenten ist das Fertigkeitsmodell "Fertigkeit" im Format als Eingabe `.lu` erforderlich, während eine Fähigkeit anfügen wird.</span><span class="sxs-lookup"><span data-stu-id="f10b7-207">Virtual Assistant requires skill's LUIS model in `.lu` format as an input while attaching a skill.</span></span> <span data-ttu-id="f10b7-208">MIT dem Botframework-cli-Tool wird DIEs in das Format `.lu` konvertiert.</span><span class="sxs-lookup"><span data-stu-id="f10b7-208">LUIS json is converted to `.lu` format using botframework-cli  tool.</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

<span data-ttu-id="f10b7-209">Der Book-a-Room-Bot verfügt über zwei Hauptbefehle für Benutzer:</span><span class="sxs-lookup"><span data-stu-id="f10b7-209">Book-a-room bot has two main commands for users:</span></span>

- `Book room`
- `Manage Favorites`

<span data-ttu-id="f10b7-210">Wir haben ein MODELL ERSTELLT, indem wir diese beiden Befehle verstehen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-210">We have built a LUIS model by understanding these two commands.</span></span> <span data-ttu-id="f10b7-211">Entsprechende Geheim geheime Schlüssel müssen in aufgefüllt `cognitivemodels.json` werden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-211">Corresponding secrets must be populated in `cognitivemodels.json`.</span></span> <span data-ttu-id="f10b7-212">Die entsprechende LUSS-JSON-Datei finden Sie [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json).</span><span class="sxs-lookup"><span data-stu-id="f10b7-212">The corresponding LUIS JSON file is found [here](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json).</span></span>
<span data-ttu-id="f10b7-213">Die entsprechende `.lu` Datei wird im folgenden Abschnitt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-213">The corresponding `.lu` file is shown in the following section:</span></span>

```
> ! Automatically generated by [LUDown CLI](https://github.com/Microsoft/botbuilder-tools/tree/master/Ludown), Tue Mar 31 2020 17:30:32 GMT+0530 (India Standard Time)

> ! Source LUIS JSON file: book-a-meeting.json

> ! Source QnA TSV file: Not Specified

> ! Source QnA Alterations file: Not Specified


> # Intent definitions

## BOOK ROOM
- book a room
- book room
- please book a room
- reserve a room
- i want to book a room
- i want to book a room please
- get me a room please
- get me a room


## MANAGE FAVORITES
- manage favorites
- manage favorite
- please manage my favorite rooms
- manage my favorite rooms please
- manage my favorite rooms
- i want to manage my favorite rooms

## None


> # Entity definitions


> # PREBUILT Entity definitions


> # Phrase list definitions


> # List entities

> # RegEx entities
```

<span data-ttu-id="f10b7-214">Bei diesem Ansatz wird jeder Befehl, der von einem Benutzer an den virtuellen Assistenten ausgegeben wird, im Zusammenhang mit oder als Befehl identifiziert, der dem Bot zugeordnet ist, und an `book room` `manage favorites` diese Fähigkeit `Book-a-room` weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="f10b7-214">With this approach, any command issued by a user to Virtual Assistant related to `book room` or `manage favorites` are identified as a command associated with `Book-a-room` bot and is forwarded to this skill.</span></span>
<span data-ttu-id="f10b7-215">Auf der anderen Seite muss bot das MODELL "LUD" verwenden, um diese Befehle zu verstehen, `Book-a-room room` wenn sie nicht vollständig eingeben werden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-215">On the other hand, `Book-a-room room` bot needs to use LUIS model to understand these commands if they are not typed full.</span></span> <span data-ttu-id="f10b7-216">Zum Beispiel: `I want to manage my favorite rooms`.</span><span class="sxs-lookup"><span data-stu-id="f10b7-216">For example: `I want to manage my favorite rooms`.</span></span>

### <a name="multi-language-support"></a><span data-ttu-id="f10b7-217">Mehrsprachige Unterstützung</span><span class="sxs-lookup"><span data-stu-id="f10b7-217">Multi-Language support</span></span>

<span data-ttu-id="f10b7-218">Als Beispiel wird ein MODELL MIT NUR englischer Kultur erstellt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-218">As an example, a LUIS model with only English culture is created.</span></span> <span data-ttu-id="f10b7-219">Sie können DIESDING-Modelle erstellen, die anderen Sprachen entspricht, und eintragen zu `cognitivemodels.json` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-219">You can create LUIS models corresponding to other languages and add entry to `cognitivemodels.json`.</span></span>

```json
{
  "defaultLocale": "en-us",
  "languageModels": {
    "en-us": {
      "luisAppId": "",
      "luisApiKey": "",
      "luisApiHost": ""
    },
    "<your_language_culture>": {
      "luisAppId": "",
      "luisApiKey": "",
      "luisApiHost": ""
    }
  }
}
```

<span data-ttu-id="f10b7-220">Fügen Sie parallel eine entsprechende `.lu` Datei im pfad von "luzfolder" hinzu.</span><span class="sxs-lookup"><span data-stu-id="f10b7-220">In parallel, add corresponding `.lu` file in luisFolder path.</span></span> <span data-ttu-id="f10b7-221">Die Ordnerstruktur sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f10b7-221">Folder structure should be as follows:</span></span>

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

<span data-ttu-id="f10b7-222">Aktualisieren Sie `languages` zum Ändern des Parameters den Befehl botskills wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f10b7-222">To modify `languages` parameter, update botskills command as follows:</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

<span data-ttu-id="f10b7-223">Der virtuelle Assistent `SetLocaleMiddleware` verwendet, um das aktuelle Locale zu identifizieren und das entsprechende Versandmodell aufrief.</span><span class="sxs-lookup"><span data-stu-id="f10b7-223">Virtual Assistant uses `SetLocaleMiddleware` to identify current locale and invoke corresponding dispatch model.</span></span> <span data-ttu-id="f10b7-224">Bot framework activity has locale field which is used by this middleware.</span><span class="sxs-lookup"><span data-stu-id="f10b7-224">Bot framework activity has locale field which is used by this middleware.</span></span> <span data-ttu-id="f10b7-225">Sie können dasselbe auch für Ihre Fähigkeiten verwenden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-225">You can use the same for your skill as well.</span></span> <span data-ttu-id="f10b7-226">Book-a-room bot verwendet diese Middleware nicht und ruft stattdessen das Locale aus der [clientInfo-Entität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)der Bot-Framework-Aktivität ab.</span><span class="sxs-lookup"><span data-stu-id="f10b7-226">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>

### <a name="claim-validation"></a><span data-ttu-id="f10b7-227">Forderungsüberprüfung</span><span class="sxs-lookup"><span data-stu-id="f10b7-227">Claim validation</span></span>

<span data-ttu-id="f10b7-228">Wir haben [claimsValidator hinzugefügt,](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) um Anrufer auf die Fähigkeit einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="f10b7-228">We have added [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) to restrict callers to the skill.</span></span> <span data-ttu-id="f10b7-229">Damit ein virtueller Assistent diese Fähigkeit aufrufen kann, füllen Sie das Array mit der App-ID dieses `AllowedCallers` `appsettings` bestimmten virtuellen Assistenten auf.</span><span class="sxs-lookup"><span data-stu-id="f10b7-229">To allow a Virtual Assistant to call this skill, populate `AllowedCallers` array from `appsettings` with that particular Virtual Assistant's app ID.</span></span>

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

<span data-ttu-id="f10b7-230">Das Array der zugelassenen Anrufer kann einschränken, welche Benutzer auf die Fertigkeit zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="f10b7-230">The allowed callers array can restrict which skill consumers can access the skill.</span></span> <span data-ttu-id="f10b7-231">Fügen Sie diesem `*` Array einen einzelnen Eintrag hinzu, um Anrufe von jedem Kunden mit Qualifikationen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="f10b7-231">Add single entry `*` to this array, to accept calls from any skill consumer.</span></span>

```
"AllowedCallers": [ "*" ],
```

<span data-ttu-id="f10b7-232">Weitere Informationen zum Hinzufügen der Anspruchsüberprüfung zu einer Fähigkeit finden Sie unter [Hinzufügen der Anspruchsüberprüfung zur Fähigkeit.](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="f10b7-232">For more information on adding claims validation to a skill, see [add claims validation to skill](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).</span></span>

### <a name="limitation-of-card-refresh"></a><span data-ttu-id="f10b7-233">Einschränkung der Kartenaktualisierung</span><span class="sxs-lookup"><span data-stu-id="f10b7-233">Limitation of card refresh</span></span> 

<span data-ttu-id="f10b7-234">Aktualisierungsaktivitäten, z. B. Kartenaktualisierung, werden noch nicht über den virtuellen Assistenten ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-234">Updating activity, such as card refresh is not supported yet through Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span></span> <span data-ttu-id="f10b7-235">Daher haben wir alle Kartenaktualisierungsanrufe `UpdateActivityAsync` durch das Veröffentlichen neuer Kartenanrufe `SendActivityAsync` ersetzt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-235">Hence, we have replaced all card refresh calls `UpdateActivityAsync` with posting new card calls `SendActivityAsync`.</span></span>

### <a name="card-actions-and-task-module-flows"></a><span data-ttu-id="f10b7-236">Kartenaktionen und Aufgabenmodulflüsse</span><span class="sxs-lookup"><span data-stu-id="f10b7-236">Card actions and task module flows</span></span>

<span data-ttu-id="f10b7-237">Um Kartenaktions- oder Aufgabenmodulaktivitäten an eine zugeordnete Fähigkeit weiter zu weiterleiten, muss die Fähigkeit darin `skillId` eingebettet werden.</span><span class="sxs-lookup"><span data-stu-id="f10b7-237">To forward card action or task module activities to an associated skill, the skill must embed `skillId` to it.</span></span>
<span data-ttu-id="f10b7-238">`Book-a-room` bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span><span class="sxs-lookup"><span data-stu-id="f10b7-238">`Book-a-room` bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span></span> 

<span data-ttu-id="f10b7-239">Weitere Informationen finden Sie [in diesem](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) Abschnitt in dieser Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="f10b7-239">For more information refer [this](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) section from this documentation.</span></span>

### <a name="handle-activities-from-group-chat-or-channel-scope"></a><span data-ttu-id="f10b7-240">Behandeln von Aktivitäten aus Gruppenchat- oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="f10b7-240">Handle activities from group chat or channel scope</span></span>

<span data-ttu-id="f10b7-241">`Book-a-room bot` ist für private Chats konzipiert, z. B. nur für persönliche oder 1:1-Bereiche.</span><span class="sxs-lookup"><span data-stu-id="f10b7-241">`Book-a-room bot` is designed for private chats, such as personal or 1:1 scope only.</span></span> <span data-ttu-id="f10b7-242">Da wir den virtuellen Assistenten angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, muss der virtuelle Assistent über die Kanalbereiche aufgerufen werden, und daher muss bot Aktivitäten für denselben `Book-a-room` Bereich erhalten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-242">Since we have customized Virtual Assistant to support group chat and channel scopes, the Virtual Assistant must be invoked from the channel scopes and thus, `Book-a-room` bot must get activities for the same scope.</span></span> <span data-ttu-id="f10b7-243">Daher `Book-a-room` ist bot angepasst, um diese Aktivitäten zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-243">Hence `Book-a-room`bot is customized to handle those activities.</span></span> <span data-ttu-id="f10b7-244">Sie finden die Check-In-Methoden `OnMessageActivityAsync` des `Book-a-room` Bot-Aktivitätshandlers.</span><span class="sxs-lookup"><span data-stu-id="f10b7-244">You can find the check in `OnMessageActivityAsync` methods of `Book-a-room` bot's activity handler.</span></span>

```csharp
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        // Check if activities are from groupchat/ teams scope. This might happen when the bot is consumed by Virtual Assistant.
        if (turnContext.Activity.Conversation.IsGroup == true)
        {
            await ShowNotSupportedInGroupChatCardAsync(turnContext).ConfigureAwait(false);
        }
        else
        {
            ...
        }
    }
```

<span data-ttu-id="f10b7-245">Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework Solutions-Repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder eine neue Fähigkeit ganz neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-245">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="f10b7-246">Informationen zum Erstellen einer neuen Fähigkeit finden Sie unter [Lernprogramme zum Erstellen einer neuen Fähigkeit.](https://microsoft.github.io/botframework-solutions/overview/skills/)</span><span class="sxs-lookup"><span data-stu-id="f10b7-246">For creating a new skill, see [tutorials to create a new skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="f10b7-247">Dokumentation zur Architektur des virtuellen Assistenten und der Fähigkeiten finden Sie unter[Virtual Assistant and skills architecture](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="f10b7-247">For Virtual Assistant and skills architecture documentation, see[Virtual Assistant and skills architecture](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).</span></span>  

## <a name="limitations-of-virtual-assistant"></a><span data-ttu-id="f10b7-248">Einschränkungen des virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="f10b7-248">Limitations of Virtual Assistant</span></span> 

* <span data-ttu-id="f10b7-249">**EndOfConversation**: Eine Fähigkeit muss eine Aktivität `endOfConversation` senden, wenn sie eine Unterhaltung beendet.</span><span class="sxs-lookup"><span data-stu-id="f10b7-249">**EndOfConversation**: A skill must send an `endOfConversation` activity when it finishes a conversation.</span></span> <span data-ttu-id="f10b7-250">Basierend auf der Aktivität beendet ein virtueller Assistent den Kontext mit dieser bestimmten Fähigkeit und kommt wieder in den Stammkontext des virtuellen Assistenten zurück.</span><span class="sxs-lookup"><span data-stu-id="f10b7-250">Based on the activity, a Virtual Assistant ends context with that particular skill and gets back into Virtual Assistant's root context.</span></span> <span data-ttu-id="f10b7-251">Für Book-a-room-Bots gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet wird.</span><span class="sxs-lookup"><span data-stu-id="f10b7-251">For Book-a-room bot, there is no clear state where conversation is ended.</span></span> <span data-ttu-id="f10b7-252">Daher haben wir nicht vom Bot gesendet, und wenn der Benutzer wieder in den Stammkontext wechseln möchte, kann er `endOfConversation` `Book-a-room` dies einfach per Befehl `start over` tun.</span><span class="sxs-lookup"><span data-stu-id="f10b7-252">Hence we have not sent `endOfConversation` from `Book-a-room` bot and when user wants to go back to root context they can simply do that by `start over` command.</span></span>  
* <span data-ttu-id="f10b7-253">**Kartenaktualisierung**: Die Kartenaktualisierung wird noch nicht über den virtuellen Assistenten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-253">**Card refresh**: Card refresh is not yet supported through Virtual Assistant.</span></span>  
* <span data-ttu-id="f10b7-254">**Messagingerweiterungen**:</span><span class="sxs-lookup"><span data-stu-id="f10b7-254">**Messaging extensions**:</span></span>
  * <span data-ttu-id="f10b7-255">Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messagingerweiterungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-255">Currently, a Virtual Assistant can support a maximum of ten commands for messaging extensions.</span></span>
  * <span data-ttu-id="f10b7-256">Die Konfiguration von Messagingerweiterungen ist nicht auf einzelne Befehle, sondern auf die gesamte Erweiterung selbst begrenzt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-256">Configuration of messaging extensions is not scoped to individual commands but for the entire extension itself.</span></span> <span data-ttu-id="f10b7-257">Dadurch wird die Konfiguration für jede einzelne Fähigkeit über den virtuellen Assistenten beschränkt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-257">This limits configuration for each individual skill through Virtual Assistant.</span></span>
  * <span data-ttu-id="f10b7-258">Befehls-IDs für Messagingerweiterungen haben eine maximale Länge von [64](../resources/schema/manifest-schema.md#composeextensions) Zeichen, und 37 Zeichen werden zum Einbetten von Fertigkeiteninformationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="f10b7-258">Messaging extensions command IDs have a maximum length of [64 characters](../resources/schema/manifest-schema.md#composeextensions) and 37 characters are used for embedding skill information.</span></span> <span data-ttu-id="f10b7-259">Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="f10b7-259">Thus, updated constraints for command ID are limited to 27 characters.</span></span>

<span data-ttu-id="f10b7-260">Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework Solutions-Repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder eine neue Fähigkeit ganz neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-260">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="f10b7-261">Lernprogramme für die spätere finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="f10b7-261">Tutorials for the later can be found [here](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="f10b7-262">Weitere Informationen finden Sie [in der Dokumentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) zur Architektur des virtuellen Assistenten und der Fähigkeiten.</span><span class="sxs-lookup"><span data-stu-id="f10b7-262">Please refer to [documentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) for Virtual Assistant and skills architecture.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f10b7-263">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="f10b7-263">Code sample</span></span>

| <span data-ttu-id="f10b7-264">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="f10b7-264">**Sample name**</span></span> | <span data-ttu-id="f10b7-265">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="f10b7-265">**Description**</span></span> | <span data-ttu-id="f10b7-266">**C#**</span><span class="sxs-lookup"><span data-stu-id="f10b7-266">**C#**</span></span> | <span data-ttu-id="f10b7-267">**.NET**</span><span class="sxs-lookup"><span data-stu-id="f10b7-267">**.NET**</span></span> |
|----------|-----------------|----------|------------------|
| <span data-ttu-id="f10b7-268">Visual Studio-Vorlage aktualisiert</span><span class="sxs-lookup"><span data-stu-id="f10b7-268">Updated visual studio template</span></span> | <span data-ttu-id="f10b7-269">Angepasste Vorlage zur Unterstützung von Teamfunktionen.</span><span class="sxs-lookup"><span data-stu-id="f10b7-269">Customized template to support teams capabilities.</span></span> | [<span data-ttu-id="f10b7-270">View</span><span class="sxs-lookup"><span data-stu-id="f10b7-270">View</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |
| <span data-ttu-id="f10b7-271">Book-a-room bot skill code</span><span class="sxs-lookup"><span data-stu-id="f10b7-271">Book-a-room bot skill code</span></span> | <span data-ttu-id="f10b7-272">Ermöglicht es Ihnen, unterwegs schnell einen Besprechungsraum zu finden und zu reservieren.</span><span class="sxs-lookup"><span data-stu-id="f10b7-272">Lets you quickly find and book a meeting room on the go.</span></span> |  | [<span data-ttu-id="f10b7-273">View</span><span class="sxs-lookup"><span data-stu-id="f10b7-273">View</span></span>](https://github.com/nebhagat/msteams-virtual-assistant-dotnet) |


## <a name="see-also"></a><span data-ttu-id="f10b7-274">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f10b7-274">See also</span></span>

- [<span data-ttu-id="f10b7-275">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="f10b7-275">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)

- [<span data-ttu-id="f10b7-276">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="f10b7-276">Book-a-room</span></span>](app-templates.md#book-a-room)

- [<span data-ttu-id="f10b7-277">Microsoft Teams Bot</span><span class="sxs-lookup"><span data-stu-id="f10b7-277">Microsoft Teams bot</span></span>](../bots/what-are-bots.md)