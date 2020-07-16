---
title: Virtueller Assistent für Microsoft Teams
description: Erstellen virtueller Assistenten-bot-und-Fertigkeiten für die Verwendung in Microsoft Teams
keywords: virtuelle Teams-Assistent-Bots
ms.openlocfilehash: 0bb1ad832fd33675e607874fcc50f20ffbb96943
ms.sourcegitcommit: 26b7404142706290810064f8216abaa1c262d1e5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "45146009"
---
# <a name="virtual-assistant-for-microsoft-teams"></a><span data-ttu-id="67d3b-104">Virtueller Assistent für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="67d3b-104">Virtual Assistant for Microsoft Teams</span></span>

<span data-ttu-id="67d3b-105">Virtueller Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzerfreundlichkeit, das Branding der Organisation und die erforderlichen Daten erhalten können.</span><span class="sxs-lookup"><span data-stu-id="67d3b-105">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> <span data-ttu-id="67d3b-106">Die [Virtual Assistant Core-Vorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) ist der grundlegende Baustein, der die zum Erstellen eines virtuellen Assistenten erforderlichen Microsoft-Technologien zusammenbringt, einschließlich des [bot-Framework-SDK](https://github.com/microsoft/botframework-sdk), des [Sprachverständnisses (Luis)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/)sowie der wesentlichen Funktionen, einschließlich der Fertigstellung von Qualifikationen, verknüpfter Konten, grundlegender Unterhaltungs Absicht, Endbenutzern eine Reihe nahtloser Interaktionen und Erlebnisse anzubieten</span><span class="sxs-lookup"><span data-stu-id="67d3b-106">The [Virtual Assistant core template](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) is the basic building block that brings together the Microsoft technologies required to build a Virtual Assistant, including the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/), as well as essential capabilities including  skills registration, linked accounts, basic conversational intent to offer end users a range of seamless interactions and experiences.</span></span> <span data-ttu-id="67d3b-107">Darüber hinaus umfassen die Vorlagen Funktionen umfangreiche Beispiele für wieder verwendbare Konversations [Fertigkeiten](https://microsoft.github.io/botframework-solutions/overview/skills).</span><span class="sxs-lookup"><span data-stu-id="67d3b-107">In addition, the template capabilities include rich examples of reusable conversational [skills](https://microsoft.github.io/botframework-solutions/overview/skills).</span></span>  <span data-ttu-id="67d3b-108">Einzelne Fertigkeiten können in eine virtuelle Assistenten Lösung integriert werden, um mehrere Szenarien zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-108">Individual skills can be integrated in a Virtual Assistant solution to enable multiple scenarios.</span></span> <span data-ttu-id="67d3b-109">Mithilfe des bot Framework-SDK werden Fertigkeiten in der Quell Code Form angezeigt, sodass Sie nach Bedarf anpassen und erweitern können.</span><span class="sxs-lookup"><span data-stu-id="67d3b-109">Using the Bot Framework SDK, Skills are presented in source code form enabling you to customize and extend as required.</span></span> <span data-ttu-id="67d3b-110">Siehe [Was ist ein bot-Framework-Fertigkeit](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="67d3b-110">See [What is a Bot Framework Skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span>

![Virtueller Assistent – Übersichtsdiagramm](../assets/images/bots/virtual-assistant/overview.png)

<span data-ttu-id="67d3b-112">Text Nachrichten Aktivitäten werden durch den virtuellen Assistenten Kern mithilfe eines [Dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) -Modells an die zugehörigen Fertigkeiten weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="67d3b-112">Text message activities are routed to associated skills by the Virtual Assistant core using a [dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) model.</span></span> 

## <a name="implementation-considerations"></a><span data-ttu-id="67d3b-113">Überlegungen zur Implementierung</span><span class="sxs-lookup"><span data-stu-id="67d3b-113">Implementation considerations</span></span>

<span data-ttu-id="67d3b-114">Die Entscheidung zum Hinzufügen eines virtuellen Assistenten kann viele Determinanten enthalten und für jede Organisation unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="67d3b-114">The decision to add a Virtual Assistant can include many determinants and differ for each organization.</span></span> <span data-ttu-id="67d3b-115">Hier sind die Faktoren, die die Implementierung eines virtuellen Assistenten für Ihre Organisation unterstützen:</span><span class="sxs-lookup"><span data-stu-id="67d3b-115">Here are the factors that support implementing a Virtual Assistant for your organization:</span></span>

- <span data-ttu-id="67d3b-116">Ein zentrales Team verwaltet alle Mitarbeiter Erfahrungen und verfügt über die Möglichkeit, eine virtuelle Assistenten Erfahrung zu erstellen und Updates für die Kern Erfahrung einschließlich der Hinzufügung neuer Fertigkeiten zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="67d3b-116">A central team manages all employee experiences and has the capability to build a Virtual Assistant experience and manage updates to the core experience including the addition of new skills.</span></span>
- <span data-ttu-id="67d3b-117">Mehrere Anwendungen sind in Geschäftsfunktionen vorhanden und/oder die Anzahl wird in Zukunft voraussichtlich zunehmen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-117">Multiple applications exist across business functions and/or the number is expected to grow in the future.</span></span>
- <span data-ttu-id="67d3b-118">Vorhandene Anwendungen sind anpassbar, im Besitz der Organisation und können in Fertigkeiten für einen virtuellen Assistenten umgewandelt werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-118">Existing applications are customizable, owned by the organization, and can be converted into skills for a Virtual Assistant.</span></span>
- <span data-ttu-id="67d3b-119">Das zentrale Team für Mitarbeiter-Erlebnisse kann Anpassungen an vorhandenen apps beeinflussen und erforderliche Anleitungen für die Integration vorhandener Anwendungen als Kompetenzen in der Erfahrung virtueller Assistenten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-119">The central employee-experiences team is able to influence customizations to existing apps and provide necessary guidance for integrating existing applications as skills in Virtual Assistant experience</span></span>

![Das zentrale Team verwaltet den Assistenten, und die Business Function Teams tragen Fähigkeiten ein.](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a><span data-ttu-id="67d3b-121">Erstellen eines Teams-fokussierten virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="67d3b-121">Create a Teams-focused Virtual Assistant</span></span>

<span data-ttu-id="67d3b-122">Microsoft hat eine [Visual Studio Vorlage](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) zum Erstellen virtueller Assistenten und Fertigkeiten veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="67d3b-122">Microsoft has published a [Visual Studio template](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) for building Virtual Assistants and skills.</span></span> <span data-ttu-id="67d3b-123">Mit der Visual Studio Vorlage können Sie einen virtuellen Assistenten erstellen, der von einer textbasierten Oberfläche mit Unterstützung für beschränkte Rich-Karten mit Aktionen angetrieben wird.</span><span class="sxs-lookup"><span data-stu-id="67d3b-123">With the Visual Studio template, you can create a Virtual Assistant, powered by a text-based experience with support for limited rich cards with actions.</span></span> <span data-ttu-id="67d3b-124">Wir haben die Visual Studio Basisvorlage erweitert, um Microsoft Teams-Plattformfunktionen und leistungsstarke Teams-App-Erlebnisse einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-124">We have enhanced the Visual Studio base template to include Microsoft Teams platform capabilities and power great Teams app experiences.</span></span> <span data-ttu-id="67d3b-125">Einige der Funktionen umfassen Unterstützung für umfangreiche Adaptive Karten, Aufgaben Module, Teams/Gruppenchats und Messaging Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-125">A few of the capabilities include support for rich adaptive cards, task modules, teams/group chats and messaging extensions.</span></span> <span data-ttu-id="67d3b-126">*Siehe auch*, [Lernprogramm: Erweitern des virtuellen Assistenten auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span><span class="sxs-lookup"><span data-stu-id="67d3b-126">*See also*, [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span></span>

![High-Level-Diagramm einer Virtual Assistant-Lösung](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a><span data-ttu-id="67d3b-128">Hinzufügen von adaptiven Karten zu Ihrem virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="67d3b-128">Add adaptive cards to your Virtual Assistant</span></span>

<span data-ttu-id="67d3b-129">Um Anforderungen ordnungsgemäß zu versenden, muss Ihr virtueller Assistent das richtige Luis-Modell und die dazugehörige Fähigkeit identifizieren.</span><span class="sxs-lookup"><span data-stu-id="67d3b-129">To dispatch requests properly, your Virtual Assistant needs to identify the correct LUIS model and corresponding skill associated with it.</span></span> <span data-ttu-id="67d3b-130">Der Dispatching-Mechanismus kann jedoch nicht für Karten Aktionsaktivitäten verwendet werden, da das Luis-Modell, das einer Fertigkeit zugeordnet ist, möglicherweise nicht für Karten Aktions Texte ausgebildet wird, da es sich um feste, vordefinierte Schlüsselwörter und nicht um Äußerungen eines Benutzers handelt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-130">However, the dispatching mechanism cannot be used for card action activities since the LUIS model associated with a skill may not be trained for card action texts since these are fixed, pre-defined keywords, not utterances from a user.</span></span>

<span data-ttu-id="67d3b-131">Wir haben dies durch das Einbetten von Fertigkeits Informationen in die Nutzlast der Karten Aktion gelöst.</span><span class="sxs-lookup"><span data-stu-id="67d3b-131">We have resolved this by embedding skill information in the card action payload.</span></span> <span data-ttu-id="67d3b-132">Jede Fertigkeit sollte `skillId` in das `value` Feld der Karten Aktionen einbetten.</span><span class="sxs-lookup"><span data-stu-id="67d3b-132">Every skill should embed `skillId` in the  `value` field of card actions.</span></span> <span data-ttu-id="67d3b-133">Dies ist die beste Möglichkeit, um sicherzustellen, dass jede Karten Aktions Aktivität die entsprechenden skillinformationen enthält und der virtuelle Assistent diese Informationen für die Versendung nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="67d3b-133">This is the best way to ensure that each card action activity carries the relevant skill information and Virtual Assistant can utilize this information for dispatching.</span></span>

<span data-ttu-id="67d3b-134">Unten sehen Sie ein Beispiel für eine Karten Aktionsdaten.</span><span class="sxs-lookup"><span data-stu-id="67d3b-134">Below is a card action data sample.</span></span> <span data-ttu-id="67d3b-135">Durch die Bereitstellung `skillId` im Konstruktor stellen wir sicher, dass Fertigkeits Informationen immer in Karten Aktionen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="67d3b-135">By providing `skillId` in the constructor we ensure that skill information is always present in card actions.</span></span>

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

<span data-ttu-id="67d3b-136">Als nächstes führen wir `SkillCardActionData` eine Klasse in der Vorlage virtuelles Assistenten ein, um `skillId` die Nutzlast der Karten Aktion zu extrahieren.</span><span class="sxs-lookup"><span data-stu-id="67d3b-136">Next, we introduce `SkillCardActionData` class in the Virtual Assistant template to extract `skillId` from the card action payload.</span></span>

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

<span data-ttu-id="67d3b-137">Unten finden Sie einen Codeausschnitt, der `skillId` aus Karten Aktionsdaten extrahiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="67d3b-137">Below is a code snippet to extract  `skillId` from card action data.</span></span> <span data-ttu-id="67d3b-138">Wir haben Sie als Erweiterungsmethode in der [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) -Klasse implementiert.</span><span class="sxs-lookup"><span data-stu-id="67d3b-138">We implemented it as an  extension method in the [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) class.</span></span>

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

### <a name="handle-interruptions-gracefully"></a><span data-ttu-id="67d3b-139">Ordnungsgemäße Behandlung von Unterbrechungen</span><span class="sxs-lookup"><span data-stu-id="67d3b-139">Handle interruptions gracefully</span></span>

<span data-ttu-id="67d3b-140">Der virtuelle Assistent kann Unterbrechungen in Fällen behandeln, in denen ein Benutzer versucht, eine Fertigkeit aufzurufen, während eine andere Fertigkeit derzeit aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="67d3b-140">Virtual Assistant can handle interruptions in cases where a user tries to invoke a skill while another skill is currently active.</span></span> <span data-ttu-id="67d3b-141">Wir haben `TeamsSkillDialog` und `TeamsSwitchSkillDialog` basierend auf den [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von bot Frameworks eingeführt, um Benutzern die Möglichkeit zu geben, eine Fertigkeits Erfahrung aus Karten Aktionen zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="67d3b-141">we have introduced `TeamsSkillDialog` and `TeamsSwitchSkillDialog`, based on Bot Framework's [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) and [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs), to enable users to switch a skill experience from card actions.</span></span> <span data-ttu-id="67d3b-142">Zur Behandlung dieser Anforderung fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsmeldung auf, um die Fertigkeiten zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="67d3b-142">To handle this request the Virtual Assistant prompts the user with a confirmation message to switch skills.</span></span>

![Bestätigungsaufforderung beim Wechsel zu einer neuen Fertigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a><span data-ttu-id="67d3b-144">Verarbeiten von Aufgabenmodul Anforderungen</span><span class="sxs-lookup"><span data-stu-id="67d3b-144">Handling task module requests</span></span>

<span data-ttu-id="67d3b-145">Um einem virtuellen Assistenten Aufgabenmodul Funktionen hinzuzufügen, werden zwei zusätzliche Methoden in den Aktivitäts Handler des virtuellen Assistenten aufgenommen: `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-145">To add task module capabilities to a Virtual Assistant, two additional methods are included in the Virtual Assistant activity handler: `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync`.</span></span> <span data-ttu-id="67d3b-146">Diese Methoden hören Aufgabenmodul bezogene Aktivitäten vom virtuellen Assistenten, identifizieren die mit der Anforderung verknüpfte Fähigkeit und leiten die Anforderung an die erkannte Fertigkeit weiter.</span><span class="sxs-lookup"><span data-stu-id="67d3b-146">These methods listen to task module-related activities from Virtual Assistant, identify the skill associated with the request, and forward the request to the identified skill.</span></span> 

<span data-ttu-id="67d3b-147">Die Anforderungs Weiterleitung erfolgt über [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable)die SkillHttpClient `PostActivityAsync` -Methode.</span><span class="sxs-lookup"><span data-stu-id="67d3b-147">Request forwarding is done via the  [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable), `PostActivityAsync` method.</span></span> <span data-ttu-id="67d3b-148">Es gibt die Antwort zurück, die `InvokeResponse` analysiert und in konvertiert wird `TaskModuleResponse` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-148">It returns the response as `InvokeResponse` which is parsed and converted to `TaskModuleResponse` .</span></span>

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

<span data-ttu-id="67d3b-149">Ein ähnlicher Ansatz wird für Karten Aktionen und Aufgabenmodul Antworten befolgt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-149">A similar approach is followed for card action dispatching and task module responses.</span></span> <span data-ttu-id="67d3b-150">Die Daten des Aufgabenmoduls "fetch" und "Submit Action" werden in include aktualisiert `skillId` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-150">Task module fetch and submit action data is updated to include `skillId`.</span></span> <span data-ttu-id="67d3b-151">Die Aktivitäts Erweiterungsmethode `GetSkillId` extrahiert `skillId` die Nutzlast, die Details zu der Fertigkeit enthält, die aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="67d3b-151">Activity Extension method `GetSkillId` extracts `skillId` from the payload which provides details about the skill that needs to be invoked.</span></span>

<span data-ttu-id="67d3b-152">Unten finden Sie einen Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und- `OnTeamsTaskModuleSubmitAsync` Methoden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-152">Below is a code snippet for `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync` methods.</span></span>

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

<span data-ttu-id="67d3b-153">Darüber hinaus müssen alle Fertigkeits Domänen in dem `validDomains` Abschnitt in der Manifestdatei des virtuellen Assistenten enthalten sein, damit Aufgaben Module, die über eine Fertigkeit aufgerufen werden, ordnungsgemäß gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-153">Additionally, all skill domains must be included in the `validDomains` section in Virtual Assistant's manifest file so that task modules invoked via a skill render properly.</span></span>

### <a name="handling-collaborative-app-scopes"></a><span data-ttu-id="67d3b-154">Behandeln kollaborativer App-Bereiche</span><span class="sxs-lookup"><span data-stu-id="67d3b-154">Handling collaborative app scopes</span></span>

<span data-ttu-id="67d3b-155">Microsoft Teams-Apps können in mehreren Bereichen vorhanden sein, darunter 1:1 Chat, Gruppenchat und Kanäle.</span><span class="sxs-lookup"><span data-stu-id="67d3b-155">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span></span> <span data-ttu-id="67d3b-156">Die Vorlage Core Virtual Assistant wurde für 1:1-Chats entwickelt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-156">The core Virtual Assistant template is designed for 1:1 chats.</span></span> <span data-ttu-id="67d3b-157">Im Rahmen der Onboarding-Erfahrung wird der virtuelle Assistent aufgefordert, Benutzer nach Namen zu benennen und den Benutzerstatus zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="67d3b-157">As part of the onboarding experience Virtual Assistant  prompts users for name and maintains user state.</span></span> <span data-ttu-id="67d3b-158">Da diese Onboarding-Erfahrung nicht für Gruppenchats/Kanalbereiche geeignet ist, wurde sie entfernt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-158">Since that onboarding experience is not suited for group chat/channel scopes it has been removed.</span></span>

<span data-ttu-id="67d3b-159">Skills sollten Aktivitäten in mehreren Bereichen behandeln (1:1 Chat, Gruppenchat und Kanal Unterhaltung).</span><span class="sxs-lookup"><span data-stu-id="67d3b-159">Skills should handle activities in multiple scopes (1:1 chat, group chat, and channel conversation).</span></span> <span data-ttu-id="67d3b-160">Wenn einer dieser Bereiche nicht unterstützt wird, sollten Fähigkeiten mit einer entsprechenden Nachricht reagieren.</span><span class="sxs-lookup"><span data-stu-id="67d3b-160">If any of these scopes are not supported, skills should respond with an appropriate message.</span></span>

<span data-ttu-id="67d3b-161">Die folgenden Verarbeitungsfunktionen wurden dem virtuellen Assistenten Kern hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="67d3b-161">The following  processing functions have been added to Virtual Assistant core:</span></span>

- <span data-ttu-id="67d3b-162">Virtueller Assistent kann ohne Textnachricht aus einem Gruppenchat oder-Kanal aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-162">Virtual Assistant can be invoked without any text message from a group chat or channel.</span></span>
- <span data-ttu-id="67d3b-163">Artikulationen werden bereinigt (d. h., entfernen Sie die erforderlichen @mention des bot), bevor Sie die Nachricht an das Dispatch-Modul senden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-163">Articulations are cleaned (i.e.,  remove the necessary @mention of the bot) before sending the message to the dispatch module.</span></span>

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

### <a name="handling-messaging-extensions"></a><span data-ttu-id="67d3b-164">Behandeln von Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="67d3b-164">Handling messaging extensions</span></span>

<span data-ttu-id="67d3b-165">Die Befehle für eine Messaging Erweiterung werden in Ihrer APP-Manifestdatei deklariert.</span><span class="sxs-lookup"><span data-stu-id="67d3b-165">The commands for a messaging extension are declared in your app manifest file.</span></span> <span data-ttu-id="67d3b-166">Die Benutzeroberfläche der Messaging Erweiterung wird von diesen Befehlen angetrieben.</span><span class="sxs-lookup"><span data-stu-id="67d3b-166">The messaging extension user interface is powered by those commands.</span></span> <span data-ttu-id="67d3b-167">Damit ein virtueller Assistent einen Messaging Erweiterungs Befehl (als angefügte Fertigkeit) macht, muss ein eigenes Manifest eines virtuellen Assistenten diese Befehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="67d3b-167">For a Virtual Assistant to power a messaging extension command (as an attached skill), a Virtual Assistant's own manifest must contain those commands.</span></span> <span data-ttu-id="67d3b-168">Die Befehle aus dem Manifest eines einzelnen Skills sollten ebenfalls dem Manifest des virtuellen Assistenten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-168">The commands from an individual skill's manifest should be added to the Virtual Assistant's manifest as well.</span></span> <span data-ttu-id="67d3b-169">Die Befehls-ID stellt Informationen zu einer zugeordneten Fertigkeit bereit, indem die APP-ID der Fertigkeit über ein Trennzeichen () angehängt wird `:` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-169">The command ID provides information about an associated skill by appending the skill's app ID via a separator (`:`).</span></span>

<span data-ttu-id="67d3b-170">Unten sehen Sie einen Ausschnitt aus der Manifestdatei eines Skills.</span><span class="sxs-lookup"><span data-stu-id="67d3b-170">Below is a snippet from a skill's manifest file.</span></span>

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

<span data-ttu-id="67d3b-171">Und, unten ist der entsprechende virtuelle Assistent Manifest Datei Codeausschnitt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-171">And, below is the corresponding Virtual Assistant manifest file code snippet.</span></span>

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

<span data-ttu-id="67d3b-172">Sobald die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent eine zugeordnete Fertigkeit identifizieren, indem er die Befehls-ID analysiert, die Aktivität aktualisiert, indem das zusätzliche Suffix ( `:<skill_id>` ) aus der Befehls-ID entfernt und an die entsprechende Fertigkeit weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="67d3b-172">Once the commands are invoked by a user, the Virtual Assistant can identify an associated skill by parsing the command ID, update the activity by removing the extra suffix (`:<skill_id>`) from the command ID,  and forward it to the corresponding skill.</span></span> <span data-ttu-id="67d3b-173">Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht verarbeiten, daher werden Konflikte zwischen Befehls-IDs zwischen den einzelnen Fertigkeiten vermieden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-173">The code for a skill doesn't need to handle the extra suffix, thus, conflicts between command IDs across skills are avoided.</span></span> <span data-ttu-id="67d3b-174">Bei diesem Ansatz können alle Such-und Aktionsbefehle einer Fertigkeit in allen Kontexten ("Verfassen", "commandbox" und "Message") von einem virtuellen Assistenten betrieben werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-174">With this approach, all the search and action commands of a skill within all contexts ("compose", "commandBox" and "message") can be powered by a Virtual Assistant.</span></span>

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

<span data-ttu-id="67d3b-175">Einige Messaging Erweiterungsaktivitäten enthalten nicht die Befehls-ID.</span><span class="sxs-lookup"><span data-stu-id="67d3b-175">Some messaging extension activities do not include the command ID.</span></span> <span data-ttu-id="67d3b-176">Enthält beispielsweise `composeExtension/selectItem` nur den Wert der Invoke-Tap-Aktion.</span><span class="sxs-lookup"><span data-stu-id="67d3b-176">For example, `composeExtension/selectItem` contains only the value of the invoke tap action.</span></span> <span data-ttu-id="67d3b-177">Um die zugehörige Fertigkeit zu identifizieren, `skillId` wird an jede Element Karte angehängt, während eine Antwort für gebildet wird `OnTeamsMessagingExtensionQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-177">To identify the associated skill, `skillId`  is attached to each item card while forming a response for `OnTeamsMessagingExtensionQueryAsync`.</span></span> <span data-ttu-id="67d3b-178">(Dies ähnelt dem Ansatz für das [Hinzufügen von adaptiven Karten zu Ihrem virtuellen Assistenten](#add-adaptive-cards-to-your-virtual-assistant).</span><span class="sxs-lookup"><span data-stu-id="67d3b-178">(This is similar to the approach for [adding adaptive  cards to your Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).</span></span>

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a><span data-ttu-id="67d3b-179">Beispiel: Konvertieren der Vorlage "book-a-room app" in eine virtuelle Assistenten Fähigkeit</span><span class="sxs-lookup"><span data-stu-id="67d3b-179">Example: Convert the Book-a-room app template to a Virtual Assistant skill</span></span>

<span data-ttu-id="67d3b-180">[Book-a-room](app-templates.md#book-a-room) ist ein [Microsoft Teams-bot](../bots/what-are-bots.md) , mit dem Benutzer einen Besprechungsraum für 30 (Standard), 60 oder 90 Minuten ab der aktuellen Uhrzeit schnell finden und reservieren können.</span><span class="sxs-lookup"><span data-stu-id="67d3b-180">[Book-a-room](app-templates.md#book-a-room) is a [Microsoft Teams bot](../bots/what-are-bots.md) that lets users quickly find and reserve a meeting room for 30 (default), 60, or 90 minutes starting from the current  time.</span></span> <span data-ttu-id="67d3b-181">Die book-a-room-bot-Bereiche für persönliche oder 1:1-Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-181">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span>

![Virtueller Assistent mit einem "book a Room"-Skill](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

<span data-ttu-id="67d3b-183">Es folgen die Delta-Änderungen, die eingeführt wurden, um Sie in eine Fertigkeit umzuwandeln, die an einen virtuellen Assistenten angefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="67d3b-183">Followings are the delta changes introduced to convert it to a skill which can be attached to a Virtual Assistant.</span></span> <span data-ttu-id="67d3b-184">Ähnliche Richtlinien können befolgt werden, um einen vorhandenen V4-bot in eine Fertigkeit zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="67d3b-184">Similar guidelines can be followed to convert any existing v4 bot to a skill.</span></span>

### <a name="skill-manifest"></a><span data-ttu-id="67d3b-185">Fertigkeits Manifest</span><span class="sxs-lookup"><span data-stu-id="67d3b-185">Skill manifest</span></span>

<span data-ttu-id="67d3b-186">Ein Fertigkeits Manifest ist eine JSON-Datei, die den Messaging Endpunkt, die ID, den Namen und andere relevante Metadaten eines Skills verfügbar macht (dieses Manifest unterscheidet sich von dem Manifest, das für Sideloading einer APP in Microsoft Teams verwendet wird) ein virtueller Assistent benötigt einen Pfad zu dieser Datei als Eingabe zum Anfügen einer Fertigkeit.</span><span class="sxs-lookup"><span data-stu-id="67d3b-186">A skill manifest is a JSON file that exposes a skill's messaging endpoint, id, name, and other relevant metadata (this manifest is different than the manifest used for sideloading an app in Microsoft Teams) A Virtual Assistant requires a path to this file as an input to attach a skill.</span></span> <span data-ttu-id="67d3b-187">Wir haben dem WWWRoot-Ordner des bot das folgende Manifest hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-187">We have added the following manifest to the bot's wwwroot folder.</span></span>

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

### <a name="luis-integration"></a><span data-ttu-id="67d3b-188">Luis-Integration</span><span class="sxs-lookup"><span data-stu-id="67d3b-188">LUIS Integration</span></span>

<span data-ttu-id="67d3b-189">Das Dispatch-Modell des virtuellen Assistenten basiert auf den Luis-Modellen von Attached Skills.</span><span class="sxs-lookup"><span data-stu-id="67d3b-189">Virtual Assistant's dispatch model is built on top of attached skills' LUIS models.</span></span> <span data-ttu-id="67d3b-190">Das Dispatch-Modell identifiziert die Absicht für jede Text Aktivität und ermittelt die damit verbundene Fähigkeit.</span><span class="sxs-lookup"><span data-stu-id="67d3b-190">The dispatch model identifies the intent for every text activity and finds out skill associated with it.</span></span>

<span data-ttu-id="67d3b-191">Virtueller Assistent erfordert das Luis-Modell des Skills (im `.lu` Format) als Eingabe beim Anfügen einer Fertigkeit.</span><span class="sxs-lookup"><span data-stu-id="67d3b-191">Virtual Assistant requires skill's LUIS model (in `.lu` format) as an input while attaching a skill.</span></span> <span data-ttu-id="67d3b-192">Luis JSON kann `.lu` mit dem botframework-CLI-Tool in ein Format konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-192">LUIS json can be converted to `.lu` format using botframework-cli  tool.</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

<span data-ttu-id="67d3b-193">Der book-a-room-bot verfügt über zwei Hauptbefehle für Benutzer:</span><span class="sxs-lookup"><span data-stu-id="67d3b-193">Book-a-room bot has two main commands for users:</span></span>

- `Book room`
- `Manage Favorites`

<span data-ttu-id="67d3b-194">Wir haben ein Luis-Modell erstellt, das diese beiden Befehle versteht.</span><span class="sxs-lookup"><span data-stu-id="67d3b-194">We have built a LUIS model understanding these two commands.</span></span> <span data-ttu-id="67d3b-195">Die entsprechenden Geheimnisse müssen in aufgefüllt werden `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-195">Corresponding secrets need to be populated in `cognitivemodels.json`.</span></span> <span data-ttu-id="67d3b-196">Die entsprechende Luis JSON-Datei kann [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) gefunden werden und so sieht die entsprechende `.lu` Datei aus.</span><span class="sxs-lookup"><span data-stu-id="67d3b-196">The corresponding LUIS JSON file can be found [here](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) and this is how the corresponding `.lu` file looks like.</span></span>

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

<span data-ttu-id="67d3b-197">Bei dieser Vorgehensweise werden alle Befehls Probleme eines Benutzers an den virtuellen Assistenten im Zusammenhang mit `book room` oder `manage favorites` können als Befehl identifiziert werden, der dem book-a-room-bot zugeordnet ist und an diese Fertigkeit weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-197">With this approach, any command issues by a user to Virtual Assistant related to `book room` or `manage favorites` can be identified as a command associated with Book-a-room bot and is forwarded to this skill.</span></span>
<span data-ttu-id="67d3b-198">Auf der anderen Seite muss book-a-room-bot das Luis-Modell verwenden, um diese Befehle zu verstehen, wenn Sie nicht wie folgt eingegeben werden (beispielsweise: `I want to manage my favorite rooms` ).</span><span class="sxs-lookup"><span data-stu-id="67d3b-198">On the other hand, Book-a-room room bot needs to use LUIS model to understand these commands if they are not typed as is (for example: `I want to manage my favorite rooms`).</span></span>

### <a name="multi-language-support"></a><span data-ttu-id="67d3b-199">Mehrsprachige Unterstützung</span><span class="sxs-lookup"><span data-stu-id="67d3b-199">Multi-Language support</span></span>

<span data-ttu-id="67d3b-200">Für dieses Beispiel haben wir nur ein Luis-Modell mit englischer Kultur erstellt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-200">For this example, we have only created a LUIS model with English culture.</span></span> <span data-ttu-id="67d3b-201">Sie können Luis-Modelle erstellen, die anderen Sprachen entsprechen, und den Eintrag hinzufügen `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-201">You can create LUIS models corresponding to other languages and add entry to `cognitivemodels.json`.</span></span>

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

<span data-ttu-id="67d3b-202">Fügen Sie gleichzeitig die entsprechende `.lu` Datei in luisFolder Path hinzu.</span><span class="sxs-lookup"><span data-stu-id="67d3b-202">In parallel, add corresponding `.lu` file in luisFolder path.</span></span> <span data-ttu-id="67d3b-203">Die Ordnerstruktur sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="67d3b-203">Folder structure should be as follows:</span></span>

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

<span data-ttu-id="67d3b-204">Aktualisieren Sie den botskills-Befehl wie folgt, um den Parameter zu ändern `languages` :</span><span class="sxs-lookup"><span data-stu-id="67d3b-204">Update botskills command as follows to modify `languages` parameter:</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

<span data-ttu-id="67d3b-205">Virtueller Assistent verwendet `SetLocaleMiddleware` , um das aktuelle Gebietsschema zu identifizieren und das entsprechende Dispatch-Modell aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-205">Virtual Assistant uses `SetLocaleMiddleware` to identify current locale and invoke corresponding dispatch model.</span></span> <span data-ttu-id="67d3b-206">(Bot-Framework-Aktivität hat Gebietsschema Feld, das von dieser Middleware verwendet wird.) Es wird empfohlen, das gleiche auch für ihre Fähigkeit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="67d3b-206">(Bot framework activity has locale field which is used by this middleware.) We recommend to use the same for your skill as well.</span></span> <span data-ttu-id="67d3b-207">Der book-a-room-bot verwendet diese Middleware nicht und ruft stattdessen das Gebietsschema aus der [abgeschlossen werden ungültig-Entität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)der bot-Framework-Aktivität ab.</span><span class="sxs-lookup"><span data-stu-id="67d3b-207">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>

### <a name="claim-validation"></a><span data-ttu-id="67d3b-208">Anspruchsüberprüfung</span><span class="sxs-lookup"><span data-stu-id="67d3b-208">Claim validation</span></span>

<span data-ttu-id="67d3b-209">Wir haben [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) hinzugefügt, um Anrufer auf die Fertigkeit einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="67d3b-209">We have added [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) to restrict callers to the skill.</span></span> <span data-ttu-id="67d3b-210">Um einem virtuellen Assistenten das Aufrufen dieser Fertigkeit zu gestatten, füllen Sie das `AllowedCallers` array `appsettings` mit der APP-ID dieses bestimmten virtuellen Assistenten auf.</span><span class="sxs-lookup"><span data-stu-id="67d3b-210">To allow a Virtual Assistant to call this skill, populate `AllowedCallers` array from `appsettings` with that particular Virtual Assistant's app ID.</span></span>

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

<span data-ttu-id="67d3b-211">Das zulässige callers-Array kann einschränken, welche Fähigkeit Verbraucher auf die Fertigkeit zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="67d3b-211">The allowed callers array can restrict which skill consumers can access the skill.</span></span> <span data-ttu-id="67d3b-212">Fügen Sie diesem Array einen einzelnen Eintrag hinzu `*` , um Anrufe von beliebigen Skill-Consumern zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="67d3b-212">Add single entry `*` to this array, to accept calls from any skill consumer.</span></span>

```
"AllowedCallers": [ "*" ],
```
<span data-ttu-id="67d3b-213">Eine ausführliche Dokumentation zum Hinzufügen der Anspruchsüberprüfung zu einer Fertigkeit finden Sie [hier](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator).</span><span class="sxs-lookup"><span data-stu-id="67d3b-213">Detailed documentation for adding claims validation to a skill can be found [here](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator).</span></span>

### <a name="card-refresh-limitation"></a><span data-ttu-id="67d3b-214">Beschränkung der Kartenaktualisierung</span><span class="sxs-lookup"><span data-stu-id="67d3b-214">Card refresh limitation</span></span>

<span data-ttu-id="67d3b-215">Die Aktualisierungsaktivität (Kartenaktualisierung) wird noch nicht über den Virtual Assistant ([GitHub-Problem](https://github.com/microsoft/botbuilder-dotnet/issues/3686)) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-215">Updating activity (card refresh) is not supported yet via Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span></span> <span data-ttu-id="67d3b-216">Daher haben wir alle Karten Aktualisierungsaufrufe ( `UpdateActivityAsync` ) durch das Veröffentlichen neuer Karten Anrufe ( `SendActivityAsync` ) ersetzt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-216">Hence, we have replaced all card refresh calls (`UpdateActivityAsync`) with posting new card calls(`SendActivityAsync`).</span></span>

### <a name="card-actions-and-task-module-flows"></a><span data-ttu-id="67d3b-217">Karten Aktionen und Aufgabenmodul Flüsse</span><span class="sxs-lookup"><span data-stu-id="67d3b-217">Card actions and task module flows</span></span>

<span data-ttu-id="67d3b-218">Um Karten Aktionen oder Aufgabenmodul Aktivitäten an eine zugeordnete Fertigkeit weiterzuleiten, muss die Fertigkeit darin eingebettet werden `skillId` .</span><span class="sxs-lookup"><span data-stu-id="67d3b-218">To forward card action or task module activities to an associated skill, the skill needs to embed `skillId` to it.</span></span>
<span data-ttu-id="67d3b-219">Book-a-room-bot-Karten Aktion, Aufgabenmodul-FETCH-und-Submit-Aktions Nutzlasten werden geändert, sodass Sie `skillId` als Parameter enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="67d3b-219">Book-a-room bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span></span> 

<span data-ttu-id="67d3b-220">Weitere Informationen [finden Sie in diesem Abschnitt](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) in dieser Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="67d3b-220">For more information refer [this](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) section from this documentation.</span></span>

### <a name="handle-activities-from-group-chat-or-channel-scope"></a><span data-ttu-id="67d3b-221">Behandeln von Aktivitäten im Gruppenchat oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="67d3b-221">Handle activities from group chat or channel scope</span></span>

<span data-ttu-id="67d3b-222">Der book-a-room-bot ist nur für private Chats (persönlich/1:1 Bereich) konzipiert.</span><span class="sxs-lookup"><span data-stu-id="67d3b-222">Book-a-room bot is designed for private chats (personal/1:1 scope) only.</span></span> <span data-ttu-id="67d3b-223">Da wir den virtuellen Assistenten für die Unterstützung von Gruppenchats und Kanal Bereichen angepasst haben, kann der virtuelle Assistent aus diesen Bereichen aufgerufen werden, sodass der book-a-room-bot möglicherweise Aktivitäten für dasselbe erhält.</span><span class="sxs-lookup"><span data-stu-id="67d3b-223">Since we have customized Virtual Assistant to support group chat and channel scopes, the Virtual Assistant might be invoked from these scopes and thus, Book-a-room bot might get activities for the same.</span></span> <span data-ttu-id="67d3b-224">Daher wird der book-a-room-bot angepasst, um diese Aktivitäten zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="67d3b-224">Hence Book-a-room bot is customized to handle those activities.</span></span> <span data-ttu-id="67d3b-225">Die Überprüfung wurde in `OnMessageActivityAsync` Methoden des Aktivitäts Handlers des book-a-room-bot eingeführt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-225">The check has been put in `OnMessageActivityAsync` methods of Book-a-room bot's activity handler.</span></span>

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

<span data-ttu-id="67d3b-226">Sie können auch vorhandene Fertigkeiten aus dem [Repository von bot-Framework-Lösungen](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder ganz neu eine neue Fertigkeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-226">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="67d3b-227">Lernprogramme für die spätere Version finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="67d3b-227">Tutorials for the later can be found [here](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="67d3b-228">Weitere Informationen finden Sie in der [Dokumentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0) für Virtual Assistant and Skills Architecture.</span><span class="sxs-lookup"><span data-stu-id="67d3b-228">Please refer to [documentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0)   for Virtual Assistant and skills architecture.</span></span>

## <a name="sample-code-to-get-started"></a><span data-ttu-id="67d3b-229">Beispielcode für erste Schritte</span><span class="sxs-lookup"><span data-stu-id="67d3b-229">Sample code to get started</span></span>

- [<span data-ttu-id="67d3b-230">Aktualisierte Visual Studio-Vorlage</span><span class="sxs-lookup"><span data-stu-id="67d3b-230">Updated visual studio template</span></span>](https://github.com/nebhagat/msteams-virtual-assistant-dotnet)
- [<span data-ttu-id="67d3b-231">Qualifikationscode für Book-a-room-bot</span><span class="sxs-lookup"><span data-stu-id="67d3b-231">Book-a-room bot skill code</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill)

## <a name="virtual-assistant-known-limitations"></a><span data-ttu-id="67d3b-232">Bekannte Einschränkungen für den virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="67d3b-232">Virtual Assistant known limitations</span></span>

- <span data-ttu-id="67d3b-233">**EndOfConversation**.</span><span class="sxs-lookup"><span data-stu-id="67d3b-233">**EndOfConversation**.</span></span> <span data-ttu-id="67d3b-234">Eine Fertigkeit sollte eine Aktivität senden, `endOfConversation` Wenn Sie eine Unterhaltung beendet.</span><span class="sxs-lookup"><span data-stu-id="67d3b-234">A skill should send an `endOfConversation` activity when it finishes a conversation.</span></span> <span data-ttu-id="67d3b-235">basierend auf dieser Aktivität beendet ein virtueller Assistent den Kontext mit dieser speziellen Fertigkeit und wird wieder in den (Stamm-) Kontext des virtuellen Assistenten eingefügt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-235">basis this activity, a Virtual Assistant ends context with that particular skill and gets back into Virtual Assistant's (root) context.</span></span> <span data-ttu-id="67d3b-236">Für einen book-a-room-bot gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="67d3b-236">For Book-a-room bot, there is no clear state where conversation can be ended.</span></span> <span data-ttu-id="67d3b-237">Daher haben wir nicht `endOfConversation` von book-a-room-bot gesendet und wenn der Benutzer zum Stammkontext zurückkehren möchte, kann er dies einfach per `start over` Befehl tun.</span><span class="sxs-lookup"><span data-stu-id="67d3b-237">Hence we have not sent `endOfConversation` from Book-a-room bot and when user wants to go back to root context they can simply do that by `start over` command.</span></span>
- <span data-ttu-id="67d3b-238">**Kartenaktualisierung**.</span><span class="sxs-lookup"><span data-stu-id="67d3b-238">**Card refresh**.</span></span> <span data-ttu-id="67d3b-239">Kartenaktualisierungen werden noch nicht über den virtuellen Assistenten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-239">Card refreshes is not yet supported through Virtual Assistant.</span></span>
- <span data-ttu-id="67d3b-240">**Messaging Erweiterungen**.:</span><span class="sxs-lookup"><span data-stu-id="67d3b-240">**Messaging extensions**.:</span></span>
  - <span data-ttu-id="67d3b-241">Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messaging Erweiterungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="67d3b-241">Currently, a Virtual Assistant can support a maximum of ten commands for messaging extensions.</span></span>
  - <span data-ttu-id="67d3b-242">Die Konfiguration von Messaging Erweiterungen ist nicht auf einzelne Befehle, sondern auf die gesamte Erweiterung selbst beschränkt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-242">Configuration of messaging extensions is not scoped to individual commands but for the entire extension itself.</span></span> <span data-ttu-id="67d3b-243">Dadurch wird die Konfiguration für jede einzelne Fertigkeit mithilfe des virtuellen Assistenten eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-243">This limits configuration for each individual skill through Virtual Assistant.</span></span>
  - <span data-ttu-id="67d3b-244">Befehls-IDs für Messaging Erweiterungen weisen eine maximale Länge von [64 Zeichen](../resources/schema/manifest-schema.md#composeextensions) auf, und 37 Zeichen werden für das Einbetten von Fertigkeits Informationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="67d3b-244">Messaging extensions command IDs have a maximum length of [64 characters](../resources/schema/manifest-schema.md#composeextensions) and 37 characters will be used for embedding skill information.</span></span> <span data-ttu-id="67d3b-245">Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="67d3b-245">Thus, updated constraints for command ID are limited to 27 characters.</span></span>
>
>
