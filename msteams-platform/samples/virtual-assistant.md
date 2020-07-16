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
# <a name="virtual-assistant-for-microsoft-teams"></a>Virtueller Assistent für Microsoft Teams

Virtueller Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzerfreundlichkeit, das Branding der Organisation und die erforderlichen Daten erhalten können. Die [Virtual Assistant Core-Vorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) ist der grundlegende Baustein, der die zum Erstellen eines virtuellen Assistenten erforderlichen Microsoft-Technologien zusammenbringt, einschließlich des [bot-Framework-SDK](https://github.com/microsoft/botframework-sdk), des [Sprachverständnisses (Luis)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/)sowie der wesentlichen Funktionen, einschließlich der Fertigstellung von Qualifikationen, verknüpfter Konten, grundlegender Unterhaltungs Absicht, Endbenutzern eine Reihe nahtloser Interaktionen und Erlebnisse anzubieten Darüber hinaus umfassen die Vorlagen Funktionen umfangreiche Beispiele für wieder verwendbare Konversations [Fertigkeiten](https://microsoft.github.io/botframework-solutions/overview/skills).  Einzelne Fertigkeiten können in eine virtuelle Assistenten Lösung integriert werden, um mehrere Szenarien zu ermöglichen. Mithilfe des bot Framework-SDK werden Fertigkeiten in der Quell Code Form angezeigt, sodass Sie nach Bedarf anpassen und erweitern können. Siehe [Was ist ein bot-Framework-Fertigkeit](https://microsoft.github.io/botframework-solutions/overview/skills/).

![Virtueller Assistent – Übersichtsdiagramm](../assets/images/bots/virtual-assistant/overview.png)

Text Nachrichten Aktivitäten werden durch den virtuellen Assistenten Kern mithilfe eines [Dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) -Modells an die zugehörigen Fertigkeiten weitergeleitet. 

## <a name="implementation-considerations"></a>Überlegungen zur Implementierung

Die Entscheidung zum Hinzufügen eines virtuellen Assistenten kann viele Determinanten enthalten und für jede Organisation unterschiedlich sein. Hier sind die Faktoren, die die Implementierung eines virtuellen Assistenten für Ihre Organisation unterstützen:

- Ein zentrales Team verwaltet alle Mitarbeiter Erfahrungen und verfügt über die Möglichkeit, eine virtuelle Assistenten Erfahrung zu erstellen und Updates für die Kern Erfahrung einschließlich der Hinzufügung neuer Fertigkeiten zu verwalten.
- Mehrere Anwendungen sind in Geschäftsfunktionen vorhanden und/oder die Anzahl wird in Zukunft voraussichtlich zunehmen.
- Vorhandene Anwendungen sind anpassbar, im Besitz der Organisation und können in Fertigkeiten für einen virtuellen Assistenten umgewandelt werden.
- Das zentrale Team für Mitarbeiter-Erlebnisse kann Anpassungen an vorhandenen apps beeinflussen und erforderliche Anleitungen für die Integration vorhandener Anwendungen als Kompetenzen in der Erfahrung virtueller Assistenten bereitstellen.

![Das zentrale Team verwaltet den Assistenten, und die Business Function Teams tragen Fähigkeiten ein.](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines Teams-fokussierten virtuellen Assistenten

Microsoft hat eine [Visual Studio Vorlage](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) zum Erstellen virtueller Assistenten und Fertigkeiten veröffentlicht. Mit der Visual Studio Vorlage können Sie einen virtuellen Assistenten erstellen, der von einer textbasierten Oberfläche mit Unterstützung für beschränkte Rich-Karten mit Aktionen angetrieben wird. Wir haben die Visual Studio Basisvorlage erweitert, um Microsoft Teams-Plattformfunktionen und leistungsstarke Teams-App-Erlebnisse einzubeziehen. Einige der Funktionen umfassen Unterstützung für umfangreiche Adaptive Karten, Aufgaben Module, Teams/Gruppenchats und Messaging Erweiterungen. *Siehe auch*, [Lernprogramm: Erweitern des virtuellen Assistenten auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).

![High-Level-Diagramm einer Virtual Assistant-Lösung](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen von adaptiven Karten zu Ihrem virtuellen Assistenten

Um Anforderungen ordnungsgemäß zu versenden, muss Ihr virtueller Assistent das richtige Luis-Modell und die dazugehörige Fähigkeit identifizieren. Der Dispatching-Mechanismus kann jedoch nicht für Karten Aktionsaktivitäten verwendet werden, da das Luis-Modell, das einer Fertigkeit zugeordnet ist, möglicherweise nicht für Karten Aktions Texte ausgebildet wird, da es sich um feste, vordefinierte Schlüsselwörter und nicht um Äußerungen eines Benutzers handelt.

Wir haben dies durch das Einbetten von Fertigkeits Informationen in die Nutzlast der Karten Aktion gelöst. Jede Fertigkeit sollte `skillId` in das `value` Feld der Karten Aktionen einbetten. Dies ist die beste Möglichkeit, um sicherzustellen, dass jede Karten Aktions Aktivität die entsprechenden skillinformationen enthält und der virtuelle Assistent diese Informationen für die Versendung nutzen kann.

Unten sehen Sie ein Beispiel für eine Karten Aktionsdaten. Durch die Bereitstellung `skillId` im Konstruktor stellen wir sicher, dass Fertigkeits Informationen immer in Karten Aktionen vorhanden sind.

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

Als nächstes führen wir `SkillCardActionData` eine Klasse in der Vorlage virtuelles Assistenten ein, um `skillId` die Nutzlast der Karten Aktion zu extrahieren.

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

Unten finden Sie einen Codeausschnitt, der `skillId` aus Karten Aktionsdaten extrahiert werden kann. Wir haben Sie als Erweiterungsmethode in der [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) -Klasse implementiert.

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

### <a name="handle-interruptions-gracefully"></a>Ordnungsgemäße Behandlung von Unterbrechungen

Der virtuelle Assistent kann Unterbrechungen in Fällen behandeln, in denen ein Benutzer versucht, eine Fertigkeit aufzurufen, während eine andere Fertigkeit derzeit aktiv ist. Wir haben `TeamsSkillDialog` und `TeamsSwitchSkillDialog` basierend auf den [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von bot Frameworks eingeführt, um Benutzern die Möglichkeit zu geben, eine Fertigkeits Erfahrung aus Karten Aktionen zu wechseln. Zur Behandlung dieser Anforderung fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsmeldung auf, um die Fertigkeiten zu wechseln.

![Bestätigungsaufforderung beim Wechsel zu einer neuen Fertigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a>Verarbeiten von Aufgabenmodul Anforderungen

Um einem virtuellen Assistenten Aufgabenmodul Funktionen hinzuzufügen, werden zwei zusätzliche Methoden in den Aktivitäts Handler des virtuellen Assistenten aufgenommen: `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` . Diese Methoden hören Aufgabenmodul bezogene Aktivitäten vom virtuellen Assistenten, identifizieren die mit der Anforderung verknüpfte Fähigkeit und leiten die Anforderung an die erkannte Fertigkeit weiter. 

Die Anforderungs Weiterleitung erfolgt über [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable)die SkillHttpClient `PostActivityAsync` -Methode. Es gibt die Antwort zurück, die `InvokeResponse` analysiert und in konvertiert wird `TaskModuleResponse` .

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

Ein ähnlicher Ansatz wird für Karten Aktionen und Aufgabenmodul Antworten befolgt. Die Daten des Aufgabenmoduls "fetch" und "Submit Action" werden in include aktualisiert `skillId` . Die Aktivitäts Erweiterungsmethode `GetSkillId` extrahiert `skillId` die Nutzlast, die Details zu der Fertigkeit enthält, die aufgerufen werden muss.

Unten finden Sie einen Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und- `OnTeamsTaskModuleSubmitAsync` Methoden.

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

Darüber hinaus müssen alle Fertigkeits Domänen in dem `validDomains` Abschnitt in der Manifestdatei des virtuellen Assistenten enthalten sein, damit Aufgaben Module, die über eine Fertigkeit aufgerufen werden, ordnungsgemäß gerendert werden.

### <a name="handling-collaborative-app-scopes"></a>Behandeln kollaborativer App-Bereiche

Microsoft Teams-Apps können in mehreren Bereichen vorhanden sein, darunter 1:1 Chat, Gruppenchat und Kanäle. Die Vorlage Core Virtual Assistant wurde für 1:1-Chats entwickelt. Im Rahmen der Onboarding-Erfahrung wird der virtuelle Assistent aufgefordert, Benutzer nach Namen zu benennen und den Benutzerstatus zu verwalten. Da diese Onboarding-Erfahrung nicht für Gruppenchats/Kanalbereiche geeignet ist, wurde sie entfernt.

Skills sollten Aktivitäten in mehreren Bereichen behandeln (1:1 Chat, Gruppenchat und Kanal Unterhaltung). Wenn einer dieser Bereiche nicht unterstützt wird, sollten Fähigkeiten mit einer entsprechenden Nachricht reagieren.

Die folgenden Verarbeitungsfunktionen wurden dem virtuellen Assistenten Kern hinzugefügt:

- Virtueller Assistent kann ohne Textnachricht aus einem Gruppenchat oder-Kanal aufgerufen werden.
- Artikulationen werden bereinigt (d. h., entfernen Sie die erforderlichen @mention des bot), bevor Sie die Nachricht an das Dispatch-Modul senden.

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

### <a name="handling-messaging-extensions"></a>Behandeln von Messaging Erweiterungen

Die Befehle für eine Messaging Erweiterung werden in Ihrer APP-Manifestdatei deklariert. Die Benutzeroberfläche der Messaging Erweiterung wird von diesen Befehlen angetrieben. Damit ein virtueller Assistent einen Messaging Erweiterungs Befehl (als angefügte Fertigkeit) macht, muss ein eigenes Manifest eines virtuellen Assistenten diese Befehle enthalten. Die Befehle aus dem Manifest eines einzelnen Skills sollten ebenfalls dem Manifest des virtuellen Assistenten hinzugefügt werden. Die Befehls-ID stellt Informationen zu einer zugeordneten Fertigkeit bereit, indem die APP-ID der Fertigkeit über ein Trennzeichen () angehängt wird `:` .

Unten sehen Sie einen Ausschnitt aus der Manifestdatei eines Skills.

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

Und, unten ist der entsprechende virtuelle Assistent Manifest Datei Codeausschnitt.

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

Sobald die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent eine zugeordnete Fertigkeit identifizieren, indem er die Befehls-ID analysiert, die Aktivität aktualisiert, indem das zusätzliche Suffix ( `:<skill_id>` ) aus der Befehls-ID entfernt und an die entsprechende Fertigkeit weitergeleitet wird. Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht verarbeiten, daher werden Konflikte zwischen Befehls-IDs zwischen den einzelnen Fertigkeiten vermieden. Bei diesem Ansatz können alle Such-und Aktionsbefehle einer Fertigkeit in allen Kontexten ("Verfassen", "commandbox" und "Message") von einem virtuellen Assistenten betrieben werden.

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

Einige Messaging Erweiterungsaktivitäten enthalten nicht die Befehls-ID. Enthält beispielsweise `composeExtension/selectItem` nur den Wert der Invoke-Tap-Aktion. Um die zugehörige Fertigkeit zu identifizieren, `skillId` wird an jede Element Karte angehängt, während eine Antwort für gebildet wird `OnTeamsMessagingExtensionQueryAsync` . (Dies ähnelt dem Ansatz für das [Hinzufügen von adaptiven Karten zu Ihrem virtuellen Assistenten](#add-adaptive-cards-to-your-virtual-assistant).

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a>Beispiel: Konvertieren der Vorlage "book-a-room app" in eine virtuelle Assistenten Fähigkeit

[Book-a-room](app-templates.md#book-a-room) ist ein [Microsoft Teams-bot](../bots/what-are-bots.md) , mit dem Benutzer einen Besprechungsraum für 30 (Standard), 60 oder 90 Minuten ab der aktuellen Uhrzeit schnell finden und reservieren können. Die book-a-room-bot-Bereiche für persönliche oder 1:1-Unterhaltungen.

![Virtueller Assistent mit einem "book a Room"-Skill](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Es folgen die Delta-Änderungen, die eingeführt wurden, um Sie in eine Fertigkeit umzuwandeln, die an einen virtuellen Assistenten angefügt werden kann. Ähnliche Richtlinien können befolgt werden, um einen vorhandenen V4-bot in eine Fertigkeit zu konvertieren.

### <a name="skill-manifest"></a>Fertigkeits Manifest

Ein Fertigkeits Manifest ist eine JSON-Datei, die den Messaging Endpunkt, die ID, den Namen und andere relevante Metadaten eines Skills verfügbar macht (dieses Manifest unterscheidet sich von dem Manifest, das für Sideloading einer APP in Microsoft Teams verwendet wird) ein virtueller Assistent benötigt einen Pfad zu dieser Datei als Eingabe zum Anfügen einer Fertigkeit. Wir haben dem WWWRoot-Ordner des bot das folgende Manifest hinzugefügt.

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

### <a name="luis-integration"></a>Luis-Integration

Das Dispatch-Modell des virtuellen Assistenten basiert auf den Luis-Modellen von Attached Skills. Das Dispatch-Modell identifiziert die Absicht für jede Text Aktivität und ermittelt die damit verbundene Fähigkeit.

Virtueller Assistent erfordert das Luis-Modell des Skills (im `.lu` Format) als Eingabe beim Anfügen einer Fertigkeit. Luis JSON kann `.lu` mit dem botframework-CLI-Tool in ein Format konvertiert werden.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

Der book-a-room-bot verfügt über zwei Hauptbefehle für Benutzer:

- `Book room`
- `Manage Favorites`

Wir haben ein Luis-Modell erstellt, das diese beiden Befehle versteht. Die entsprechenden Geheimnisse müssen in aufgefüllt werden `cognitivemodels.json` . Die entsprechende Luis JSON-Datei kann [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) gefunden werden und so sieht die entsprechende `.lu` Datei aus.

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

Bei dieser Vorgehensweise werden alle Befehls Probleme eines Benutzers an den virtuellen Assistenten im Zusammenhang mit `book room` oder `manage favorites` können als Befehl identifiziert werden, der dem book-a-room-bot zugeordnet ist und an diese Fertigkeit weitergeleitet werden.
Auf der anderen Seite muss book-a-room-bot das Luis-Modell verwenden, um diese Befehle zu verstehen, wenn Sie nicht wie folgt eingegeben werden (beispielsweise: `I want to manage my favorite rooms` ).

### <a name="multi-language-support"></a>Mehrsprachige Unterstützung

Für dieses Beispiel haben wir nur ein Luis-Modell mit englischer Kultur erstellt. Sie können Luis-Modelle erstellen, die anderen Sprachen entsprechen, und den Eintrag hinzufügen `cognitivemodels.json` .

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

Fügen Sie gleichzeitig die entsprechende `.lu` Datei in luisFolder Path hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Aktualisieren Sie den botskills-Befehl wie folgt, um den Parameter zu ändern `languages` :

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Virtueller Assistent verwendet `SetLocaleMiddleware` , um das aktuelle Gebietsschema zu identifizieren und das entsprechende Dispatch-Modell aufzurufen. (Bot-Framework-Aktivität hat Gebietsschema Feld, das von dieser Middleware verwendet wird.) Es wird empfohlen, das gleiche auch für ihre Fähigkeit zu verwenden. Der book-a-room-bot verwendet diese Middleware nicht und ruft stattdessen das Gebietsschema aus der [abgeschlossen werden ungültig-Entität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)der bot-Framework-Aktivität ab.

### <a name="claim-validation"></a>Anspruchsüberprüfung

Wir haben [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) hinzugefügt, um Anrufer auf die Fertigkeit einzuschränken. Um einem virtuellen Assistenten das Aufrufen dieser Fertigkeit zu gestatten, füllen Sie das `AllowedCallers` array `appsettings` mit der APP-ID dieses bestimmten virtuellen Assistenten auf.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das zulässige callers-Array kann einschränken, welche Fähigkeit Verbraucher auf die Fertigkeit zugreifen können. Fügen Sie diesem Array einen einzelnen Eintrag hinzu `*` , um Anrufe von beliebigen Skill-Consumern zu akzeptieren.

```
"AllowedCallers": [ "*" ],
```
Eine ausführliche Dokumentation zum Hinzufügen der Anspruchsüberprüfung zu einer Fertigkeit finden Sie [hier](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator).

### <a name="card-refresh-limitation"></a>Beschränkung der Kartenaktualisierung

Die Aktualisierungsaktivität (Kartenaktualisierung) wird noch nicht über den Virtual Assistant ([GitHub-Problem](https://github.com/microsoft/botbuilder-dotnet/issues/3686)) unterstützt. Daher haben wir alle Karten Aktualisierungsaufrufe ( `UpdateActivityAsync` ) durch das Veröffentlichen neuer Karten Anrufe ( `SendActivityAsync` ) ersetzt.

### <a name="card-actions-and-task-module-flows"></a>Karten Aktionen und Aufgabenmodul Flüsse

Um Karten Aktionen oder Aufgabenmodul Aktivitäten an eine zugeordnete Fertigkeit weiterzuleiten, muss die Fertigkeit darin eingebettet werden `skillId` .
Book-a-room-bot-Karten Aktion, Aufgabenmodul-FETCH-und-Submit-Aktions Nutzlasten werden geändert, sodass Sie `skillId` als Parameter enthalten sind. 

Weitere Informationen [finden Sie in diesem Abschnitt](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) in dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Behandeln von Aktivitäten im Gruppenchat oder Kanalbereich

Der book-a-room-bot ist nur für private Chats (persönlich/1:1 Bereich) konzipiert. Da wir den virtuellen Assistenten für die Unterstützung von Gruppenchats und Kanal Bereichen angepasst haben, kann der virtuelle Assistent aus diesen Bereichen aufgerufen werden, sodass der book-a-room-bot möglicherweise Aktivitäten für dasselbe erhält. Daher wird der book-a-room-bot angepasst, um diese Aktivitäten zu verarbeiten. Die Überprüfung wurde in `OnMessageActivityAsync` Methoden des Aktivitäts Handlers des book-a-room-bot eingeführt.

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

Sie können auch vorhandene Fertigkeiten aus dem [Repository von bot-Framework-Lösungen](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder ganz neu eine neue Fertigkeit erstellen. Lernprogramme für die spätere Version finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/). Weitere Informationen finden Sie in der [Dokumentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0) für Virtual Assistant and Skills Architecture.

## <a name="sample-code-to-get-started"></a>Beispielcode für erste Schritte

- [Aktualisierte Visual Studio-Vorlage](https://github.com/nebhagat/msteams-virtual-assistant-dotnet)
- [Qualifikationscode für Book-a-room-bot](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill)

## <a name="virtual-assistant-known-limitations"></a>Bekannte Einschränkungen für den virtuellen Assistenten

- **EndOfConversation**. Eine Fertigkeit sollte eine Aktivität senden, `endOfConversation` Wenn Sie eine Unterhaltung beendet. basierend auf dieser Aktivität beendet ein virtueller Assistent den Kontext mit dieser speziellen Fertigkeit und wird wieder in den (Stamm-) Kontext des virtuellen Assistenten eingefügt. Für einen book-a-room-bot gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet werden kann. Daher haben wir nicht `endOfConversation` von book-a-room-bot gesendet und wenn der Benutzer zum Stammkontext zurückkehren möchte, kann er dies einfach per `start over` Befehl tun.
- **Kartenaktualisierung**. Kartenaktualisierungen werden noch nicht über den virtuellen Assistenten unterstützt.
- **Messaging Erweiterungen**.:
  - Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messaging Erweiterungen unterstützen.
  - Die Konfiguration von Messaging Erweiterungen ist nicht auf einzelne Befehle, sondern auf die gesamte Erweiterung selbst beschränkt. Dadurch wird die Konfiguration für jede einzelne Fertigkeit mithilfe des virtuellen Assistenten eingeschränkt.
  - Befehls-IDs für Messaging Erweiterungen weisen eine maximale Länge von [64 Zeichen](../resources/schema/manifest-schema.md#composeextensions) auf, und 37 Zeichen werden für das Einbetten von Fertigkeits Informationen verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.
>
>
