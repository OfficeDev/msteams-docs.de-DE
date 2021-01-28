---
title: Virtueller Assistent für Microsoft Teams
description: So erstellen Sie einen virtuellen Assistenten-Bot und Fähigkeiten für die Verwendung in Microsoft Teams
ms.topic: how-to
keywords: Teams Virtual Assistant Bots
ms.openlocfilehash: d72b1afbf975707d694d4aaef31263a3ce467629
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014614"
---
# <a name="virtual-assistant-for-microsoft-teams"></a><span data-ttu-id="1a6c1-104">Virtueller Assistent für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1a6c1-104">Virtual Assistant for Microsoft Teams</span></span>

<span data-ttu-id="1a6c1-105">Der virtuelle Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine robuste Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzeroberfläche, das Unternehmensbranding und die erforderlichen Daten beibehalten können.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-105">Virtual Assistant is a Microsoft open-source template that enables you to create a robust conversational solution while maintaining full control of user experience, organizational branding, and necessary data.</span></span> <span data-ttu-id="1a6c1-106">Die [](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) Kernvorlage des virtuellen Assistenten ist der grundlegende Baustein, der die zum Erstellen eines virtuellen Assistenten erforderlichen Technologien von Microsoft zusammen bringt, einschließlich [Bot Framework SDK,](https://github.com/microsoft/botframework-sdk) [Language Understanding (SDK)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/)sowie grundlegende Funktionen wie z. B. Die Registrierung von Fertigkeiten, verknüpfte Konten, grundlegende Unterhaltungsabsichten, um Endbenutzern eine Reihe nahtloser Interaktionen und Erfahrungen zu bieten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-106">The [Virtual Assistant core template](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) is the basic building block that brings together the Microsoft technologies required to build a Virtual Assistant, including the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/), as well as essential capabilities including  skills registration, linked accounts, basic conversational intent to offer end users a range of seamless interactions and experiences.</span></span> <span data-ttu-id="1a6c1-107">Darüber hinaus enthalten die Vorlagenfunktionen umfangreiche Beispiele für wiederverwendbare [Unterhaltungskenntnisse.](https://microsoft.github.io/botframework-solutions/overview/skills)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-107">In addition, the template capabilities include rich examples of reusable conversational [skills](https://microsoft.github.io/botframework-solutions/overview/skills).</span></span>  <span data-ttu-id="1a6c1-108">Individuelle Fähigkeiten können in eine Virtual Assistant-Lösung integriert werden, um mehrere Szenarien zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-108">Individual skills can be integrated in a Virtual Assistant solution to enable multiple scenarios.</span></span> <span data-ttu-id="1a6c1-109">Mithilfe des Bot Framework SDK werden Fähigkeiten in Quellcodeform präsentiert, sodass Sie sie nach Bedarf anpassen und erweitern können.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-109">Using the Bot Framework SDK, Skills are presented in source code form enabling you to customize and extend as required.</span></span> <span data-ttu-id="1a6c1-110">See [What is a Bot Framework Skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span><span class="sxs-lookup"><span data-stu-id="1a6c1-110">See [What is a Bot Framework Skill](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span>

![Übersichtsdiagramm des virtuellen Assistenten](../assets/images/bots/virtual-assistant/overview.png)

<span data-ttu-id="1a6c1-112">Textnachrichtenaktivitäten werden vom Kern des virtuellen Assistenten mithilfe eines Verteilermodells an [zugeordnete Fähigkeiten geroutet.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-112">Text message activities are routed to associated skills by the Virtual Assistant core using a [dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) model.</span></span> 

## <a name="implementation-considerations"></a><span data-ttu-id="1a6c1-113">Überlegungen zur Implementierung</span><span class="sxs-lookup"><span data-stu-id="1a6c1-113">Implementation considerations</span></span>

<span data-ttu-id="1a6c1-114">Die Entscheidung, einen virtuellen Assistenten hinzuzufügen, kann viele Determinanten enthalten und für jede Organisation unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-114">The decision to add a Virtual Assistant can include many determinants and differ for each organization.</span></span> <span data-ttu-id="1a6c1-115">Dies sind die Faktoren, die die Implementierung eines virtuellen Assistenten für Ihre Organisation unterstützen:</span><span class="sxs-lookup"><span data-stu-id="1a6c1-115">Here are the factors that support implementing a Virtual Assistant for your organization:</span></span>

- <span data-ttu-id="1a6c1-116">Ein zentrales Team verwaltet alle Mitarbeitererfahrungen und verfügt über die Möglichkeit, eine virtuelle Assistentenerfahrung zu erstellen und Updates für die Kernerfahrung zu verwalten, einschließlich der Ergänzung neuer Fähigkeiten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-116">A central team manages all employee experiences and has the capability to build a Virtual Assistant experience and manage updates to the core experience including the addition of new skills.</span></span>
- <span data-ttu-id="1a6c1-117">Es gibt mehrere Anwendungen in verschiedenen Geschäftsfunktionen, und/oder es wird erwartet, dass die Anzahl in Zukunft anwachsen wird.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-117">Multiple applications exist across business functions and/or the number is expected to grow in the future.</span></span>
- <span data-ttu-id="1a6c1-118">Vorhandene Anwendungen sind anpassbar, gehören der Organisation und können in Fähigkeiten für einen virtuellen Assistenten umgewandelt werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-118">Existing applications are customizable, owned by the organization, and can be converted into skills for a Virtual Assistant.</span></span>
- <span data-ttu-id="1a6c1-119">Das zentrale Mitarbeiterteam kann Anpassungen an vorhandenen Apps beeinflussen und die erforderlichen Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in der Virtuellen Assistentenerfahrung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-119">The central employee-experiences team is able to influence customizations to existing apps and provide necessary guidance for integrating existing applications as skills in Virtual Assistant experience</span></span>

![Das zentrale Team verwaltet den Assistenten, und Geschäftsfunktionsteams tragen Fähigkeiten bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a><span data-ttu-id="1a6c1-121">Erstellen eines teamsorientierten virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="1a6c1-121">Create a Teams-focused Virtual Assistant</span></span>

<span data-ttu-id="1a6c1-122">Microsoft hat eine vorlage [Visual Studio zum](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) Erstellen von virtuellen Assistenten und Fähigkeiten veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-122">Microsoft has published a [Visual Studio template](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) for building Virtual Assistants and skills.</span></span> <span data-ttu-id="1a6c1-123">Mit der Visual Studio können Sie einen virtuellen Assistenten erstellen, der von einer textbasierten Umgebung mit Unterstützung für eingeschränkte umfangreiche Karten mit Aktionen unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-123">With the Visual Studio template, you can create a Virtual Assistant, powered by a text-based experience with support for limited rich cards with actions.</span></span> <span data-ttu-id="1a6c1-124">Wir haben die Basisvorlage Visual Studio Microsoft Teams erweitert, um Microsoft Teams-Plattformfunktionen und power-great Teams-App-Erfahrungen zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-124">We have enhanced the Visual Studio base template to include Microsoft Teams platform capabilities and power great Teams app experiences.</span></span> <span data-ttu-id="1a6c1-125">Einige der Funktionen umfassen Unterstützung für umfangreiche adaptive Karten, Aufgabenmodule, Teams/Gruppenchats und Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-125">A few of the capabilities include support for rich adaptive cards, task modules, teams/group chats and messaging extensions.</span></span> <span data-ttu-id="1a6c1-126">*Siehe auch*, [Lernprogramm: Erweitern Des virtuellen Assistenten auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span><span class="sxs-lookup"><span data-stu-id="1a6c1-126">*See also*, [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).</span></span>

![Abbildung einer virtuellen Assistentenlösung auf hoher Ebene](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a><span data-ttu-id="1a6c1-128">Hinzufügen adaptiver Karten zu Ihrem virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="1a6c1-128">Add adaptive cards to your Virtual Assistant</span></span>

<span data-ttu-id="1a6c1-129">Um Anforderungen ordnungsgemäß zu versenden, muss Ihr virtueller Assistent das richtige MODELL UND die zugehörigen Fähigkeiten identifizieren.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-129">To dispatch requests properly, your Virtual Assistant needs to identify the correct LUIS model and corresponding skill associated with it.</span></span> <span data-ttu-id="1a6c1-130">Der Verteilermechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das mit einer Kompetenz verknüpfte MODELL ZU EINER Kompetenz möglicherweise nicht für Kartenaktionstexte geschult ist, da es sich dabei um feste, vordefinierte Schlüsselwörter und nicht um Diebnungen eines Benutzers handelt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-130">However, the dispatching mechanism cannot be used for card action activities since the LUIS model associated with a skill may not be trained for card action texts since these are fixed, pre-defined keywords, not utterances from a user.</span></span>

<span data-ttu-id="1a6c1-131">Wir haben dieses Problem gelöst, indem wir Fertigkeiteninformationen in die Kartenaktionsnutzlast einbetten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-131">We have resolved this by embedding skill information in the card action payload.</span></span> <span data-ttu-id="1a6c1-132">Jede Fähigkeit sollte `skillId` in das Feld der  `value` Kartenaktionen eingebettet werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-132">Every skill should embed `skillId` in the  `value` field of card actions.</span></span> <span data-ttu-id="1a6c1-133">Dies ist die beste Möglichkeit, um sicherzustellen, dass jede Kartenaktionsaktivität die relevanten Fertigkeiteninformationen enthält und der virtuelle Assistent diese Informationen für die Versendung nutzen kann.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-133">This is the best way to ensure that each card action activity carries the relevant skill information and Virtual Assistant can utilize this information for dispatching.</span></span>

<span data-ttu-id="1a6c1-134">Im Folgenden finden Sie ein Beispiel für Kartenaktionsdaten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-134">Below is a card action data sample.</span></span> <span data-ttu-id="1a6c1-135">Durch Die `skillId` Angabe des Konstruktors stellen wir sicher, dass in Kartenaktionen immer Fertigkeiteninformationen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-135">By providing `skillId` in the constructor we ensure that skill information is always present in card actions.</span></span>

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

<span data-ttu-id="1a6c1-136">Als Nächstes stellen wir die `SkillCardActionData` Klasse in der Vorlage "Virtueller Assistent" vor, die aus der `skillId` Kartenaktionsnutzlast extrahiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-136">Next, we introduce `SkillCardActionData` class in the Virtual Assistant template to extract `skillId` from the card action payload.</span></span>

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

<span data-ttu-id="1a6c1-137">Im Folgenden finden Sie einen Codeausschnitt zum Extrahieren  `skillId` aus Kartenaktionsdaten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-137">Below is a code snippet to extract  `skillId` from card action data.</span></span> <span data-ttu-id="1a6c1-138">Wir haben es als Erweiterungsmethode in der [Aktivitätsklasse](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) implementiert.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-138">We implemented it as an  extension method in the [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) class.</span></span>

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

### <a name="handle-interruptions-gracefully"></a><span data-ttu-id="1a6c1-139">Behandeln von Unterbrechungen ohne Kulanz</span><span class="sxs-lookup"><span data-stu-id="1a6c1-139">Handle interruptions gracefully</span></span>

<span data-ttu-id="1a6c1-140">Der virtuelle Assistent kann Unterbrechungen behandeln, wenn ein Benutzer versucht, eine Fertigkeit zu aufrufen, während eine andere Fähigkeit derzeit aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-140">Virtual Assistant can handle interruptions in cases where a user tries to invoke a skill while another skill is currently active.</span></span> <span data-ttu-id="1a6c1-141">wir haben eingeführt und, basierend auf `TeamsSkillDialog` `TeamsSwitchSkillDialog` den [SkillDialog-](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog-Funktionen](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von Bot Framework, benutzern das Wechseln einer Fertigkeitenerfahrung von Kartenaktionen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-141">we have introduced `TeamsSkillDialog` and `TeamsSwitchSkillDialog`, based on Bot Framework's [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) and [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs), to enable users to switch a skill experience from card actions.</span></span> <span data-ttu-id="1a6c1-142">Um diese Anforderung zu verarbeiten, fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsmeldung auf, die Fähigkeiten zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-142">To handle this request the Virtual Assistant prompts the user with a confirmation message to switch skills.</span></span>

![Bestätigungsaufforderung beim Wechsel zu einer neuen Fähigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a><span data-ttu-id="1a6c1-144">Behandeln von Aufgabenmodulanforderungen</span><span class="sxs-lookup"><span data-stu-id="1a6c1-144">Handling task module requests</span></span>

<span data-ttu-id="1a6c1-145">Zum Hinzufügen von Aufgabenmodulfunktionen zu einem virtuellen Assistenten sind zwei zusätzliche Methoden im Aktivitätshandler des virtuellen Assistenten `OnTeamsTaskModuleFetchAsync` enthalten: und `OnTeamsTaskModuleSubmitAsync` .</span><span class="sxs-lookup"><span data-stu-id="1a6c1-145">To add task module capabilities to a Virtual Assistant, two additional methods are included in the Virtual Assistant activity handler: `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync`.</span></span> <span data-ttu-id="1a6c1-146">Diese Methoden lauschen aufgabenmodulbezogene Aktivitäten vom virtuellen Assistenten ab, identifizieren die der Anforderung zugeordnete Kompetenz und geben die Anforderung an die identifizierte Kompetenz weiter.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-146">These methods listen to task module-related activities from Virtual Assistant, identify the skill associated with the request, and forward the request to the identified skill.</span></span> 

<span data-ttu-id="1a6c1-147">Die Anforderungs weiterleitung erfolgt über die  [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable), `PostActivityAsync` -Methode.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-147">Request forwarding is done via the  [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable), `PostActivityAsync` method.</span></span> <span data-ttu-id="1a6c1-148">Es wird die Antwort `InvokeResponse` zurückgegeben, die analysiert und in konvertiert `TaskModuleResponse` wird.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-148">It returns the response as `InvokeResponse` which is parsed and converted to `TaskModuleResponse` .</span></span>

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

<span data-ttu-id="1a6c1-149">Ein ähnlicher Ansatz wird für Kartenaktionsversand und Aufgabenmodulantworten verfolgt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-149">A similar approach is followed for card action dispatching and task module responses.</span></span> <span data-ttu-id="1a6c1-150">Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird so aktualisiert, dass sie enthalten `skillId` sind.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-150">Task module fetch and submit action data is updated to include `skillId`.</span></span> <span data-ttu-id="1a6c1-151">Die Aktivitätserweiterungsmethode extrahiert aus der Nutzlast, die Details über die Fähigkeit `GetSkillId` `skillId` liefert, die aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-151">Activity Extension method `GetSkillId` extracts `skillId` from the payload which provides details about the skill that needs to be invoked.</span></span>

<span data-ttu-id="1a6c1-152">Nachfolgend finden Sie einen Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` Methoden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-152">Below is a code snippet for `OnTeamsTaskModuleFetchAsync` and `OnTeamsTaskModuleSubmitAsync` methods.</span></span>

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

<span data-ttu-id="1a6c1-153">Darüber hinaus müssen alle Fertigkeitendomänen im Abschnitt in der Manifestdatei des virtuellen Assistenten enthalten sein, damit Aufgabenmodule, die über eine Fähigkeit aufgerufen werden, `validDomains` ordnungsgemäß gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-153">Additionally, all skill domains must be included in the `validDomains` section in Virtual Assistant's manifest file so that task modules invoked via a skill render properly.</span></span>

### <a name="handling-collaborative-app-scopes"></a><span data-ttu-id="1a6c1-154">Behandeln von Gemeinsamen App-Bereich</span><span class="sxs-lookup"><span data-stu-id="1a6c1-154">Handling collaborative app scopes</span></span>

<span data-ttu-id="1a6c1-155">Teams Apps können in mehreren Bereiche vorhanden sein, einschließlich 1:1-Chat, Gruppenchat und Kanälen.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-155">Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels.</span></span> <span data-ttu-id="1a6c1-156">Die Zentrale Vorlage für virtuelle Assistenten ist für 1:1-Chats konzipiert.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-156">The core Virtual Assistant template is designed for 1:1 chats.</span></span> <span data-ttu-id="1a6c1-157">Im Rahmen der Onboardingerfahrung fordert der virtuelle Assistent die Benutzer zur Eingabe des Namens auf und verwaltet den Benutzerstatus.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-157">As part of the onboarding experience Virtual Assistant  prompts users for name and maintains user state.</span></span> <span data-ttu-id="1a6c1-158">Da diese Onboardingerfahrung nicht für Gruppenchat-/Kanalbereiche geeignet ist, wurde sie entfernt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-158">Since that onboarding experience is not suited for group chat/channel scopes it has been removed.</span></span>

<span data-ttu-id="1a6c1-159">Fähigkeiten sollten Aktivitäten in mehreren Bereiche verarbeiten (1:1-Chat, Gruppenchat und Kanalunterhaltung).</span><span class="sxs-lookup"><span data-stu-id="1a6c1-159">Skills should handle activities in multiple scopes (1:1 chat, group chat, and channel conversation).</span></span> <span data-ttu-id="1a6c1-160">Wenn einer dieser Bereiche nicht unterstützt wird, sollten Fertigkeiten mit einer entsprechenden Nachricht antworten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-160">If any of these scopes are not supported, skills should respond with an appropriate message.</span></span>

<span data-ttu-id="1a6c1-161">Die folgenden Verarbeitungsfunktionen wurden dem Kern des virtuellen Assistenten hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="1a6c1-161">The following  processing functions have been added to Virtual Assistant core:</span></span>

- <span data-ttu-id="1a6c1-162">Der virtuelle Assistent kann ohne Textnachricht aus einem Gruppenchat oder Kanal aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-162">Virtual Assistant can be invoked without any text message from a group chat or channel.</span></span>
- <span data-ttu-id="1a6c1-163">Articulationen werden bereinigt (d. h. die erforderlichen @mention des Bots entfernt), bevor die Nachricht an das Versandmodul gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-163">Articulations are cleaned (i.e.,  remove the necessary @mention of the bot) before sending the message to the dispatch module.</span></span>

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

### <a name="handling-messaging-extensions"></a><span data-ttu-id="1a6c1-164">Behandeln von Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="1a6c1-164">Handling messaging extensions</span></span>

<span data-ttu-id="1a6c1-165">Die Befehle für eine Messagingerweiterung werden in Ihrer App-Manifestdatei deklariert.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-165">The commands for a messaging extension are declared in your app manifest file.</span></span> <span data-ttu-id="1a6c1-166">Die Benutzeroberfläche der Messagingerweiterung wird von diesen Befehlen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-166">The messaging extension user interface is powered by those commands.</span></span> <span data-ttu-id="1a6c1-167">Damit ein virtueller Assistent einen Befehl zur Messagingerweiterung (als angefügte Fähigkeit) ausführen kann, muss das manifest eines virtuellen Assistenten diese Befehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-167">For a Virtual Assistant to power a messaging extension command (as an attached skill), a Virtual Assistant's own manifest must contain those commands.</span></span> <span data-ttu-id="1a6c1-168">Die Befehle aus dem Manifest einer einzelnen Fertigkeit sollten auch dem Manifest des virtuellen Assistenten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-168">The commands from an individual skill's manifest should be added to the Virtual Assistant's manifest as well.</span></span> <span data-ttu-id="1a6c1-169">Die Befehls-ID enthält Informationen zu einer zugeordneten Fähigkeit, indem die App-ID der Fähigkeit über ein Trennzeichen ( ) angefügt `:` wird.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-169">The command ID provides information about an associated skill by appending the skill's app ID via a separator (`:`).</span></span>

<span data-ttu-id="1a6c1-170">Unten sehen Sie einen Codeausschnitt aus der Manifestdatei einer Fähigkeit.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-170">Below is a snippet from a skill's manifest file.</span></span>

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

<span data-ttu-id="1a6c1-171">Und unten sehen Sie den entsprechenden Codeausschnitt der Manifestdatei des virtuellen Assistenten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-171">And, below is the corresponding Virtual Assistant manifest file code snippet.</span></span>

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

<span data-ttu-id="1a6c1-172">Nachdem die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent eine zugeordnete Fähigkeit identifizieren, indem er die Befehls-ID pariert, die Aktivität aktualisiert, indem er das zusätzliche Suffix ( ) aus der Befehls-ID entfernt und an die entsprechende Fähigkeit weitersentrat. `:<skill_id>`</span><span class="sxs-lookup"><span data-stu-id="1a6c1-172">Once the commands are invoked by a user, the Virtual Assistant can identify an associated skill by parsing the command ID, update the activity by removing the extra suffix (`:<skill_id>`) from the command ID,  and forward it to the corresponding skill.</span></span> <span data-ttu-id="1a6c1-173">Der Code für eine Kompetenz muss das zusätzliche Suffix nicht behandeln, daher werden Konflikte zwischen Den Befehls-IDs zwischen Fähigkeiten vermieden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-173">The code for a skill doesn't need to handle the extra suffix, thus, conflicts between command IDs across skills are avoided.</span></span> <span data-ttu-id="1a6c1-174">Bei diesem Ansatz können alle Such- und Aktionsbefehle einer Fähigkeit in allen Kontexten ("compose", "commandBox" und "message") von einem virtuellen Assistenten unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-174">With this approach, all the search and action commands of a skill within all contexts ("compose", "commandBox" and "message") can be powered by a Virtual Assistant.</span></span>

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

<span data-ttu-id="1a6c1-175">Einige Messagingerweiterungsaktivitäten enthalten nicht die Befehls-ID.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-175">Some messaging extension activities do not include the command ID.</span></span> <span data-ttu-id="1a6c1-176">Enthält beispielsweise nur den Wert der Aktion zum Aufrufen `composeExtension/selectItem` des Tippens.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-176">For example, `composeExtension/selectItem` contains only the value of the invoke tap action.</span></span> <span data-ttu-id="1a6c1-177">Um die zugeordnete Fähigkeit zu identifizieren, wird an jede `skillId`  Elementkarte angefügt, während eine Antwort für `OnTeamsMessagingExtensionQueryAsync` bildet.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-177">To identify the associated skill, `skillId`  is attached to each item card while forming a response for `OnTeamsMessagingExtensionQueryAsync`.</span></span> <span data-ttu-id="1a6c1-178">(Dies ähnelt dem Ansatz zum Hinzufügen [adaptiver Karten zum virtuellen Assistenten.](#add-adaptive-cards-to-your-virtual-assistant)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-178">(This is similar to the approach for [adding adaptive  cards to your Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).</span></span>

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a><span data-ttu-id="1a6c1-179">Beispiel: Konvertieren der App-Vorlage "Buch-a-Raum" in einen virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="1a6c1-179">Example: Convert the Book-a-room app template to a Virtual Assistant skill</span></span>

<span data-ttu-id="1a6c1-180">[Book-a-room](app-templates.md#book-a-room) ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) mit dem Benutzer schnell einen Besprechungsraum für 30 (Standard), 60 oder 90 Minuten ab der aktuellen Uhrzeit finden und reservieren können.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-180">[Book-a-room](app-templates.md#book-a-room) is a [Microsoft Teams bot](../bots/what-are-bots.md) that lets users quickly find and reserve a meeting room for 30 (default), 60, or 90 minutes starting from the current  time.</span></span> <span data-ttu-id="1a6c1-181">Der Bot "Buch-a-Raum" ist auf persönliche Unterhaltungen oder 1:1-Unterhaltungen begrenzt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-181">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span>

![Virtueller Assistent mit der Fähigkeit "Raum buchen"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

<span data-ttu-id="1a6c1-183">Nachfolgend finden Sie die Deltaänderungen, die eingeführt wurden, um sie in eine Fähigkeit zu konvertieren, die an einen virtuellen Assistenten angefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-183">Followings are the delta changes introduced to convert it to a skill which can be attached to a Virtual Assistant.</span></span> <span data-ttu-id="1a6c1-184">Ähnliche Richtlinien können befolgt werden, um jeden vorhandenen v4-Bot in eine Fähigkeit zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-184">Similar guidelines can be followed to convert any existing v4 bot to a skill.</span></span>

### <a name="skill-manifest"></a><span data-ttu-id="1a6c1-185">Fertigkeitenmanifest</span><span class="sxs-lookup"><span data-stu-id="1a6c1-185">Skill manifest</span></span>

<span data-ttu-id="1a6c1-186">Ein Fertigkeitenmanifest ist eine JSON-Datei, die den Messagingendpunkt, die ID, den Namen und andere relevante Metadaten einer Fähigkeit verfügbar macht (dieses Manifest ist anders als das Manifest zum Querladen einer App in Microsoft Teams). Ein virtueller Assistent benötigt einen Pfad zu dieser Datei als Eingabe, um eine Fähigkeit anfügen zu können.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-186">A skill manifest is a JSON file that exposes a skill's messaging endpoint, id, name, and other relevant metadata (this manifest is different than the manifest used for sideloading an app in Microsoft Teams) A Virtual Assistant requires a path to this file as an input to attach a skill.</span></span> <span data-ttu-id="1a6c1-187">Wir haben das folgende Manifest zum wwwroot-Ordner des Bots hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-187">We have added the following manifest to the bot's wwwroot folder.</span></span>

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

### <a name="luis-integration"></a><span data-ttu-id="1a6c1-188">INTEGRATION VON WIEDER</span><span class="sxs-lookup"><span data-stu-id="1a6c1-188">LUIS Integration</span></span>

<span data-ttu-id="1a6c1-189">Das Verteilermodell des virtuellen Assistenten baut auf angefügten SKILLS-Modellen auf.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-189">Virtual Assistant's dispatch model is built on top of attached skills' LUIS models.</span></span> <span data-ttu-id="1a6c1-190">Das Versandmodell identifiziert die Absicht für jede Textaktivität und ermittelt damit verbundene Fertigkeiten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-190">The dispatch model identifies the intent for every text activity and finds out skill associated with it.</span></span>

<span data-ttu-id="1a6c1-191">Für den virtuellen Assistenten ist das MODELL VON Fertigkeit (im Format) als Eingabe beim `.lu` Anfügen einer Fähigkeit erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-191">Virtual Assistant requires skill's LUIS model (in `.lu` format) as an input while attaching a skill.</span></span> <span data-ttu-id="1a6c1-192">MIT dem Botframework-cli-Tool kann DAS JSON in ein Format `.lu` konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-192">LUIS json can be converted to `.lu` format using botframework-cli  tool.</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

<span data-ttu-id="1a6c1-193">Book-a-room bot has two main commands for users:</span><span class="sxs-lookup"><span data-stu-id="1a6c1-193">Book-a-room bot has two main commands for users:</span></span>

- `Book room`
- `Manage Favorites`

<span data-ttu-id="1a6c1-194">Wir haben ein MODELL VON HEUTE erstellt, das diese beiden Befehle verstehen kann.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-194">We have built a LUIS model understanding these two commands.</span></span> <span data-ttu-id="1a6c1-195">Entsprechende geheime Schlüssel müssen in aufgefüllt `cognitivemodels.json` werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-195">Corresponding secrets need to be populated in `cognitivemodels.json`.</span></span> <span data-ttu-id="1a6c1-196">Die entsprechende NEUEINFN-Datei finden Sie [hier,](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) und so sieht die entsprechende `.lu` Datei aus.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-196">The corresponding LUIS JSON file can be found [here](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) and this is how the corresponding `.lu` file looks like.</span></span>

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

<span data-ttu-id="1a6c1-197">Bei diesem Ansatz werden alle Befehlsprobleme eines Benutzers an den virtuellen Assistenten im Zusammenhang mit oder können als Befehl identifiziert werden, der dem `book room` Bot "Book-a-room" zugeordnet ist, und an diese Fähigkeit `manage favorites` weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-197">With this approach, any command issues by a user to Virtual Assistant related to `book room` or `manage favorites` can be identified as a command associated with Book-a-room bot and is forwarded to this skill.</span></span>
<span data-ttu-id="1a6c1-198">Andererseits muss der Raumbot "Book-a-room" das MODELL EINES BUCHS verwenden, um diese Befehle zu verstehen, wenn sie nicht wie beschriftt sind (z. B.: `I want to manage my favorite rooms` ).</span><span class="sxs-lookup"><span data-stu-id="1a6c1-198">On the other hand, Book-a-room room bot needs to use LUIS model to understand these commands if they are not typed as is (for example: `I want to manage my favorite rooms`).</span></span>

### <a name="multi-language-support"></a><span data-ttu-id="1a6c1-199">Mehrsprachige Unterstützung</span><span class="sxs-lookup"><span data-stu-id="1a6c1-199">Multi-Language support</span></span>

<span data-ttu-id="1a6c1-200">In diesem Beispiel haben wir nur ein MODELL MIT EINER ENGLISCHEN Kultur erstellt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-200">For this example, we have only created a LUIS model with English culture.</span></span> <span data-ttu-id="1a6c1-201">Sie können EINES -Modell erstellen, das anderen Sprachen entspricht, und Eintrag hinzufügen zu `cognitivemodels.json` .</span><span class="sxs-lookup"><span data-stu-id="1a6c1-201">You can create LUIS models corresponding to other languages and add entry to `cognitivemodels.json`.</span></span>

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

<span data-ttu-id="1a6c1-202">Fügen Sie parallel die entsprechende `.lu` Datei im pfadordnerischen Pfad hinzu.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-202">In parallel, add corresponding `.lu` file in luisFolder path.</span></span> <span data-ttu-id="1a6c1-203">Die Ordnerstruktur sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="1a6c1-203">Folder structure should be as follows:</span></span>

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

<span data-ttu-id="1a6c1-204">Aktualisieren Sie den Befehl "botskills" wie folgt, um den Parameter `languages` zu ändern:</span><span class="sxs-lookup"><span data-stu-id="1a6c1-204">Update botskills command as follows to modify `languages` parameter:</span></span>

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

<span data-ttu-id="1a6c1-205">Der virtuelle Assistent identifiziert `SetLocaleMiddleware` das aktuelle Locale und ruft das entsprechende Verteilermodell auf.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-205">Virtual Assistant uses `SetLocaleMiddleware` to identify current locale and invoke corresponding dispatch model.</span></span> <span data-ttu-id="1a6c1-206">(Bot-Framework-Aktivität verfügt über ein Von-Ort-Feld, das von dieser Middleware verwendet wird.) Es wird empfohlen, dasselbe für Ihre Fähigkeiten zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-206">(Bot framework activity has locale field which is used by this middleware.) We recommend to use the same for your skill as well.</span></span> <span data-ttu-id="1a6c1-207">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-207">Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).</span></span>

### <a name="claim-validation"></a><span data-ttu-id="1a6c1-208">Anspruchsüberprüfung</span><span class="sxs-lookup"><span data-stu-id="1a6c1-208">Claim validation</span></span>

<span data-ttu-id="1a6c1-209">Wir haben [claimsValidator hinzugefügt,](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) um Anrufer auf die Fähigkeit einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-209">We have added [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) to restrict callers to the skill.</span></span> <span data-ttu-id="1a6c1-210">Damit ein virtueller Assistent diese Kompetenz aufrufen kann, füllen Sie das Array mit der App-ID dieses bestimmten virtuellen Assistenten `AllowedCallers` `appsettings` auf.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-210">To allow a Virtual Assistant to call this skill, populate `AllowedCallers` array from `appsettings` with that particular Virtual Assistant's app ID.</span></span>

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

<span data-ttu-id="1a6c1-211">Das Array der zulässigen Anrufer kann einschränken, welche Fertigkeiten Verbraucher auf die Fähigkeit zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-211">The allowed callers array can restrict which skill consumers can access the skill.</span></span> <span data-ttu-id="1a6c1-212">Fügen Sie diesem `*` Array einen einzelnen Eintrag hinzu, um Anrufe von einem beliebigen Fertigkeitsverbraucher zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-212">Add single entry `*` to this array, to accept calls from any skill consumer.</span></span>

```
"AllowedCallers": [ "*" ],
```
<span data-ttu-id="1a6c1-213">Eine ausführliche Dokumentation zum Hinzufügen der Anspruchsprüfung zu einer Kompetenz finden Sie [hier.](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-213">Detailed documentation for adding claims validation to a skill can be found [here](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator).</span></span>

### <a name="card-refresh-limitation"></a><span data-ttu-id="1a6c1-214">Einschränkung der Kartenaktualisierung</span><span class="sxs-lookup"><span data-stu-id="1a6c1-214">Card refresh limitation</span></span>

<span data-ttu-id="1a6c1-215">Aktualisierungsaktivitäten (Kartenaktualisierung) werden über den virtuellen Assistenten[(GitHub-Problem) noch nicht unterstützt.](https://github.com/microsoft/botbuilder-dotnet/issues/3686)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-215">Updating activity (card refresh) is not supported yet via Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)).</span></span> <span data-ttu-id="1a6c1-216">Daher haben wir alle Kartenaktualisierungsaufrufe ( `UpdateActivityAsync` ) durch das Veröffentlichen neuer Kartenanrufe( ) ersetzt. `SendActivityAsync`</span><span class="sxs-lookup"><span data-stu-id="1a6c1-216">Hence, we have replaced all card refresh calls (`UpdateActivityAsync`) with posting new card calls(`SendActivityAsync`).</span></span>

### <a name="card-actions-and-task-module-flows"></a><span data-ttu-id="1a6c1-217">Kartenaktionen und Aufgabenmodulabläufe</span><span class="sxs-lookup"><span data-stu-id="1a6c1-217">Card actions and task module flows</span></span>

<span data-ttu-id="1a6c1-218">Um Kartenaktions- oder Aufgabenmodulaktivitäten an eine zugeordnete Fähigkeit weiter zu weiterleiten, muss die Fähigkeit darin `skillId` eingebettet werden.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-218">To forward card action or task module activities to an associated skill, the skill needs to embed `skillId` to it.</span></span>
<span data-ttu-id="1a6c1-219">Botkartenaktion "Buch-a-Raum", Aufgabenmodul zum Abrufen und Übermitteln von Aktionsnutzlasten werden so geändert, dass sie `skillId` als Parameter enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-219">Book-a-room bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.</span></span> 

<span data-ttu-id="1a6c1-220">Weitere Informationen finden Sie [in diesem](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) Abschnitt aus dieser Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-220">For more information refer [this](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) section from this documentation.</span></span>

### <a name="handle-activities-from-group-chat-or-channel-scope"></a><span data-ttu-id="1a6c1-221">Behandeln von Aktivitäten im Gruppenchat- oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="1a6c1-221">Handle activities from group chat or channel scope</span></span>

<span data-ttu-id="1a6c1-222">Book-a-room bot ist nur für private Chats (persönlicher/1:1-Bereich) konzipiert.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-222">Book-a-room bot is designed for private chats (personal/1:1 scope) only.</span></span> <span data-ttu-id="1a6c1-223">Da wir den virtuellen Assistenten angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, wird der virtuelle Assistent möglicherweise aus diesen Bereich aufgerufen, und daher kann der Bot "Buch-ein-Raum" Aktivitäten für denselben Bereich erhalten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-223">Since we have customized Virtual Assistant to support group chat and channel scopes, the Virtual Assistant might be invoked from these scopes and thus, Book-a-room bot might get activities for the same.</span></span> <span data-ttu-id="1a6c1-224">Daher ist der Bot "Book-a-room" so angepasst, dass er diese Aktivitäten verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-224">Hence Book-a-room bot is customized to handle those activities.</span></span> <span data-ttu-id="1a6c1-225">Die Überprüfung wurde in Methoden des Aktivitätshandlers des `OnMessageActivityAsync` Bots "Book-a-room" verwendet.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-225">The check has been put in `OnMessageActivityAsync` methods of Book-a-room bot's activity handler.</span></span>

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

<span data-ttu-id="1a6c1-226">Sie können auch vorhandene Fähigkeiten aus dem [Bot-Framework-Lösungsrepository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder ganz von Grund auf neue Fähigkeiten erstellen.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-226">You can also leverage existing skills from [Bot Framework Solutions repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) or create a new skill altogether from scratch.</span></span> <span data-ttu-id="1a6c1-227">Lernprogramme für den späteren Zeitpunkt finden Sie [hier.](https://microsoft.github.io/botframework-solutions/overview/skills/)</span><span class="sxs-lookup"><span data-stu-id="1a6c1-227">Tutorials for the later can be found [here](https://microsoft.github.io/botframework-solutions/overview/skills/).</span></span> <span data-ttu-id="1a6c1-228">Weitere Informationen finden Sie [in der Dokumentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0)   zur Architektur des virtuellen Assistenten und der Fähigkeiten.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-228">Please refer to [documentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0)   for Virtual Assistant and skills architecture.</span></span>

## <a name="sample-code-to-get-started"></a><span data-ttu-id="1a6c1-229">Beispielcode für die ersten Schritte</span><span class="sxs-lookup"><span data-stu-id="1a6c1-229">Sample code to get started</span></span>

- [<span data-ttu-id="1a6c1-230">Aktualisierte Visual Studio-Vorlage</span><span class="sxs-lookup"><span data-stu-id="1a6c1-230">Updated visual studio template</span></span>](https://github.com/nebhagat/msteams-virtual-assistant-dotnet)
- [<span data-ttu-id="1a6c1-231">Book-a-room-Bot-Fertigkeitencode</span><span class="sxs-lookup"><span data-stu-id="1a6c1-231">Book-a-room bot skill code</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill)

## <a name="virtual-assistant-known-limitations"></a><span data-ttu-id="1a6c1-232">Bekannte Einschränkungen des virtuellen Assistenten</span><span class="sxs-lookup"><span data-stu-id="1a6c1-232">Virtual Assistant known limitations</span></span>

- <span data-ttu-id="1a6c1-233">**EndOfConversation**.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-233">**EndOfConversation**.</span></span> <span data-ttu-id="1a6c1-234">Eine Fähigkeit sollte eine Aktivität `endOfConversation` senden, wenn sie eine Unterhaltung beendet.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-234">A skill should send an `endOfConversation` activity when it finishes a conversation.</span></span> <span data-ttu-id="1a6c1-235">Als Grundlage für diese Aktivität beendet ein virtueller Assistent den Kontext mit dieser bestimmten Fähigkeit und geht wieder in den Kontext des virtuellen Assistenten (Stammkontext) zurück.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-235">basis this activity, a Virtual Assistant ends context with that particular skill and gets back into Virtual Assistant's (root) context.</span></span> <span data-ttu-id="1a6c1-236">Für Book-a-Room-Bots gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-236">For Book-a-room bot, there is no clear state where conversation can be ended.</span></span> <span data-ttu-id="1a6c1-237">Daher haben wir nicht vom `endOfConversation` Bot "Book-a-room" gesendet, und wenn der Benutzer zum Stammkontext zurück möchte, kann er dies einfach per Befehl `start over` tun.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-237">Hence we have not sent `endOfConversation` from Book-a-room bot and when user wants to go back to root context they can simply do that by `start over` command.</span></span>
- <span data-ttu-id="1a6c1-238">**Kartenaktualisierung**.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-238">**Card refresh**.</span></span> <span data-ttu-id="1a6c1-239">Kartenaktualisierungen werden vom virtuellen Assistenten noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-239">Card refreshes is not yet supported through Virtual Assistant.</span></span>
- <span data-ttu-id="1a6c1-240">**Messagingerweiterungen**.:</span><span class="sxs-lookup"><span data-stu-id="1a6c1-240">**Messaging extensions**.:</span></span>
  - <span data-ttu-id="1a6c1-241">Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messagingerweiterungen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-241">Currently, a Virtual Assistant can support a maximum of ten commands for messaging extensions.</span></span>
  - <span data-ttu-id="1a6c1-242">Die Konfiguration von Messagingerweiterungen ist nicht auf einzelne Befehle, sondern auf die gesamte Erweiterung selbst begrenzt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-242">Configuration of messaging extensions is not scoped to individual commands but for the entire extension itself.</span></span> <span data-ttu-id="1a6c1-243">Dadurch wird die Konfiguration für jede einzelne Kompetenz über den virtuellen Assistenten beschränkt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-243">This limits configuration for each individual skill through Virtual Assistant.</span></span>
  - <span data-ttu-id="1a6c1-244">Befehls-IDs für Messagingerweiterungen haben eine maximale Länge von [64](../resources/schema/manifest-schema.md#composeextensions) Zeichen, und zum Einbetten von Fertigkeiteninformationen werden 37 Zeichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-244">Messaging extensions command IDs have a maximum length of [64 characters](../resources/schema/manifest-schema.md#composeextensions) and 37 characters will be used for embedding skill information.</span></span> <span data-ttu-id="1a6c1-245">Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.</span><span class="sxs-lookup"><span data-stu-id="1a6c1-245">Thus, updated constraints for command ID are limited to 27 characters.</span></span>
>
>
