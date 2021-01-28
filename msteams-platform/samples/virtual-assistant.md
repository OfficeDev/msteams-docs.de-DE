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
# <a name="virtual-assistant-for-microsoft-teams"></a>Virtueller Assistent für Microsoft Teams

Der virtuelle Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine robuste Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzeroberfläche, das Unternehmensbranding und die erforderlichen Daten beibehalten können. Die [](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) Kernvorlage des virtuellen Assistenten ist der grundlegende Baustein, der die zum Erstellen eines virtuellen Assistenten erforderlichen Technologien von Microsoft zusammen bringt, einschließlich [Bot Framework SDK,](https://github.com/microsoft/botframework-sdk) [Language Understanding (SDK)](https://www.luis.ai/), [QnA Maker](https://www.qnamaker.ai/)sowie grundlegende Funktionen wie z. B. Die Registrierung von Fertigkeiten, verknüpfte Konten, grundlegende Unterhaltungsabsichten, um Endbenutzern eine Reihe nahtloser Interaktionen und Erfahrungen zu bieten. Darüber hinaus enthalten die Vorlagenfunktionen umfangreiche Beispiele für wiederverwendbare [Unterhaltungskenntnisse.](https://microsoft.github.io/botframework-solutions/overview/skills)  Individuelle Fähigkeiten können in eine Virtual Assistant-Lösung integriert werden, um mehrere Szenarien zu ermöglichen. Mithilfe des Bot Framework SDK werden Fähigkeiten in Quellcodeform präsentiert, sodass Sie sie nach Bedarf anpassen und erweitern können. See [What is a Bot Framework Skill](https://microsoft.github.io/botframework-solutions/overview/skills/).

![Übersichtsdiagramm des virtuellen Assistenten](../assets/images/bots/virtual-assistant/overview.png)

Textnachrichtenaktivitäten werden vom Kern des virtuellen Assistenten mithilfe eines Verteilermodells an [zugeordnete Fähigkeiten geroutet.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs) 

## <a name="implementation-considerations"></a>Überlegungen zur Implementierung

Die Entscheidung, einen virtuellen Assistenten hinzuzufügen, kann viele Determinanten enthalten und für jede Organisation unterschiedlich sein. Dies sind die Faktoren, die die Implementierung eines virtuellen Assistenten für Ihre Organisation unterstützen:

- Ein zentrales Team verwaltet alle Mitarbeitererfahrungen und verfügt über die Möglichkeit, eine virtuelle Assistentenerfahrung zu erstellen und Updates für die Kernerfahrung zu verwalten, einschließlich der Ergänzung neuer Fähigkeiten.
- Es gibt mehrere Anwendungen in verschiedenen Geschäftsfunktionen, und/oder es wird erwartet, dass die Anzahl in Zukunft anwachsen wird.
- Vorhandene Anwendungen sind anpassbar, gehören der Organisation und können in Fähigkeiten für einen virtuellen Assistenten umgewandelt werden.
- Das zentrale Mitarbeiterteam kann Anpassungen an vorhandenen Apps beeinflussen und die erforderlichen Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in der Virtuellen Assistentenerfahrung bereitstellen.

![Das zentrale Team verwaltet den Assistenten, und Geschäftsfunktionsteams tragen Fähigkeiten bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines teamsorientierten virtuellen Assistenten

Microsoft hat eine vorlage [Visual Studio zum](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) Erstellen von virtuellen Assistenten und Fähigkeiten veröffentlicht. Mit der Visual Studio können Sie einen virtuellen Assistenten erstellen, der von einer textbasierten Umgebung mit Unterstützung für eingeschränkte umfangreiche Karten mit Aktionen unterstützt wird. Wir haben die Basisvorlage Visual Studio Microsoft Teams erweitert, um Microsoft Teams-Plattformfunktionen und power-great Teams-App-Erfahrungen zu enthalten. Einige der Funktionen umfassen Unterstützung für umfangreiche adaptive Karten, Aufgabenmodule, Teams/Gruppenchats und Messagingerweiterungen. *Siehe auch*, [Lernprogramm: Erweitern Des virtuellen Assistenten auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).

![Abbildung einer virtuellen Assistentenlösung auf hoher Ebene](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen adaptiver Karten zu Ihrem virtuellen Assistenten

Um Anforderungen ordnungsgemäß zu versenden, muss Ihr virtueller Assistent das richtige MODELL UND die zugehörigen Fähigkeiten identifizieren. Der Verteilermechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das mit einer Kompetenz verknüpfte MODELL ZU EINER Kompetenz möglicherweise nicht für Kartenaktionstexte geschult ist, da es sich dabei um feste, vordefinierte Schlüsselwörter und nicht um Diebnungen eines Benutzers handelt.

Wir haben dieses Problem gelöst, indem wir Fertigkeiteninformationen in die Kartenaktionsnutzlast einbetten. Jede Fähigkeit sollte `skillId` in das Feld der  `value` Kartenaktionen eingebettet werden. Dies ist die beste Möglichkeit, um sicherzustellen, dass jede Kartenaktionsaktivität die relevanten Fertigkeiteninformationen enthält und der virtuelle Assistent diese Informationen für die Versendung nutzen kann.

Im Folgenden finden Sie ein Beispiel für Kartenaktionsdaten. Durch Die `skillId` Angabe des Konstruktors stellen wir sicher, dass in Kartenaktionen immer Fertigkeiteninformationen vorhanden sind.

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

Als Nächstes stellen wir die `SkillCardActionData` Klasse in der Vorlage "Virtueller Assistent" vor, die aus der `skillId` Kartenaktionsnutzlast extrahiert werden soll.

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

Im Folgenden finden Sie einen Codeausschnitt zum Extrahieren  `skillId` aus Kartenaktionsdaten. Wir haben es als Erweiterungsmethode in der [Aktivitätsklasse](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) implementiert.

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

### <a name="handle-interruptions-gracefully"></a>Behandeln von Unterbrechungen ohne Kulanz

Der virtuelle Assistent kann Unterbrechungen behandeln, wenn ein Benutzer versucht, eine Fertigkeit zu aufrufen, während eine andere Fähigkeit derzeit aktiv ist. wir haben eingeführt und, basierend auf `TeamsSkillDialog` `TeamsSwitchSkillDialog` den [SkillDialog-](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog-Funktionen](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von Bot Framework, benutzern das Wechseln einer Fertigkeitenerfahrung von Kartenaktionen ermöglicht. Um diese Anforderung zu verarbeiten, fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsmeldung auf, die Fähigkeiten zu wechseln.

![Bestätigungsaufforderung beim Wechsel zu einer neuen Fähigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handling-task-module-requests"></a>Behandeln von Aufgabenmodulanforderungen

Zum Hinzufügen von Aufgabenmodulfunktionen zu einem virtuellen Assistenten sind zwei zusätzliche Methoden im Aktivitätshandler des virtuellen Assistenten `OnTeamsTaskModuleFetchAsync` enthalten: und `OnTeamsTaskModuleSubmitAsync` . Diese Methoden lauschen aufgabenmodulbezogene Aktivitäten vom virtuellen Assistenten ab, identifizieren die der Anforderung zugeordnete Kompetenz und geben die Anforderung an die identifizierte Kompetenz weiter. 

Die Anforderungs weiterleitung erfolgt über die  [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable), `PostActivityAsync` -Methode. Es wird die Antwort `InvokeResponse` zurückgegeben, die analysiert und in konvertiert `TaskModuleResponse` wird.

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

Ein ähnlicher Ansatz wird für Kartenaktionsversand und Aufgabenmodulantworten verfolgt. Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird so aktualisiert, dass sie enthalten `skillId` sind. Die Aktivitätserweiterungsmethode extrahiert aus der Nutzlast, die Details über die Fähigkeit `GetSkillId` `skillId` liefert, die aufgerufen werden muss.

Nachfolgend finden Sie einen Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` Methoden.

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

Darüber hinaus müssen alle Fertigkeitendomänen im Abschnitt in der Manifestdatei des virtuellen Assistenten enthalten sein, damit Aufgabenmodule, die über eine Fähigkeit aufgerufen werden, `validDomains` ordnungsgemäß gerendert werden.

### <a name="handling-collaborative-app-scopes"></a>Behandeln von Gemeinsamen App-Bereich

Teams Apps können in mehreren Bereiche vorhanden sein, einschließlich 1:1-Chat, Gruppenchat und Kanälen. Die Zentrale Vorlage für virtuelle Assistenten ist für 1:1-Chats konzipiert. Im Rahmen der Onboardingerfahrung fordert der virtuelle Assistent die Benutzer zur Eingabe des Namens auf und verwaltet den Benutzerstatus. Da diese Onboardingerfahrung nicht für Gruppenchat-/Kanalbereiche geeignet ist, wurde sie entfernt.

Fähigkeiten sollten Aktivitäten in mehreren Bereiche verarbeiten (1:1-Chat, Gruppenchat und Kanalunterhaltung). Wenn einer dieser Bereiche nicht unterstützt wird, sollten Fertigkeiten mit einer entsprechenden Nachricht antworten.

Die folgenden Verarbeitungsfunktionen wurden dem Kern des virtuellen Assistenten hinzugefügt:

- Der virtuelle Assistent kann ohne Textnachricht aus einem Gruppenchat oder Kanal aufgerufen werden.
- Articulationen werden bereinigt (d. h. die erforderlichen @mention des Bots entfernt), bevor die Nachricht an das Versandmodul gesendet wird.

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

### <a name="handling-messaging-extensions"></a>Behandeln von Messagingerweiterungen

Die Befehle für eine Messagingerweiterung werden in Ihrer App-Manifestdatei deklariert. Die Benutzeroberfläche der Messagingerweiterung wird von diesen Befehlen unterstützt. Damit ein virtueller Assistent einen Befehl zur Messagingerweiterung (als angefügte Fähigkeit) ausführen kann, muss das manifest eines virtuellen Assistenten diese Befehle enthalten. Die Befehle aus dem Manifest einer einzelnen Fertigkeit sollten auch dem Manifest des virtuellen Assistenten hinzugefügt werden. Die Befehls-ID enthält Informationen zu einer zugeordneten Fähigkeit, indem die App-ID der Fähigkeit über ein Trennzeichen ( ) angefügt `:` wird.

Unten sehen Sie einen Codeausschnitt aus der Manifestdatei einer Fähigkeit.

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

Und unten sehen Sie den entsprechenden Codeausschnitt der Manifestdatei des virtuellen Assistenten.

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

Nachdem die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent eine zugeordnete Fähigkeit identifizieren, indem er die Befehls-ID pariert, die Aktivität aktualisiert, indem er das zusätzliche Suffix ( ) aus der Befehls-ID entfernt und an die entsprechende Fähigkeit weitersentrat. `:<skill_id>` Der Code für eine Kompetenz muss das zusätzliche Suffix nicht behandeln, daher werden Konflikte zwischen Den Befehls-IDs zwischen Fähigkeiten vermieden. Bei diesem Ansatz können alle Such- und Aktionsbefehle einer Fähigkeit in allen Kontexten ("compose", "commandBox" und "message") von einem virtuellen Assistenten unterstützt werden.

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

Einige Messagingerweiterungsaktivitäten enthalten nicht die Befehls-ID. Enthält beispielsweise nur den Wert der Aktion zum Aufrufen `composeExtension/selectItem` des Tippens. Um die zugeordnete Fähigkeit zu identifizieren, wird an jede `skillId`  Elementkarte angefügt, während eine Antwort für `OnTeamsMessagingExtensionQueryAsync` bildet. (Dies ähnelt dem Ansatz zum Hinzufügen [adaptiver Karten zum virtuellen Assistenten.](#add-adaptive-cards-to-your-virtual-assistant)

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

## <a name="example-convert-the-book-a-room-app-template-to-a-virtual-assistant-skill"></a>Beispiel: Konvertieren der App-Vorlage "Buch-a-Raum" in einen virtuellen Assistenten

[Book-a-room](app-templates.md#book-a-room) ist ein [Microsoft Teams-Bot,](../bots/what-are-bots.md) mit dem Benutzer schnell einen Besprechungsraum für 30 (Standard), 60 oder 90 Minuten ab der aktuellen Uhrzeit finden und reservieren können. Der Bot "Buch-a-Raum" ist auf persönliche Unterhaltungen oder 1:1-Unterhaltungen begrenzt.

![Virtueller Assistent mit der Fähigkeit "Raum buchen"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Nachfolgend finden Sie die Deltaänderungen, die eingeführt wurden, um sie in eine Fähigkeit zu konvertieren, die an einen virtuellen Assistenten angefügt werden kann. Ähnliche Richtlinien können befolgt werden, um jeden vorhandenen v4-Bot in eine Fähigkeit zu konvertieren.

### <a name="skill-manifest"></a>Fertigkeitenmanifest

Ein Fertigkeitenmanifest ist eine JSON-Datei, die den Messagingendpunkt, die ID, den Namen und andere relevante Metadaten einer Fähigkeit verfügbar macht (dieses Manifest ist anders als das Manifest zum Querladen einer App in Microsoft Teams). Ein virtueller Assistent benötigt einen Pfad zu dieser Datei als Eingabe, um eine Fähigkeit anfügen zu können. Wir haben das folgende Manifest zum wwwroot-Ordner des Bots hinzugefügt.

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

### <a name="luis-integration"></a>INTEGRATION VON WIEDER

Das Verteilermodell des virtuellen Assistenten baut auf angefügten SKILLS-Modellen auf. Das Versandmodell identifiziert die Absicht für jede Textaktivität und ermittelt damit verbundene Fertigkeiten.

Für den virtuellen Assistenten ist das MODELL VON Fertigkeit (im Format) als Eingabe beim `.lu` Anfügen einer Fähigkeit erforderlich. MIT dem Botframework-cli-Tool kann DAS JSON in ein Format `.lu` konvertiert werden.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

Book-a-room bot has two main commands for users:

- `Book room`
- `Manage Favorites`

Wir haben ein MODELL VON HEUTE erstellt, das diese beiden Befehle verstehen kann. Entsprechende geheime Schlüssel müssen in aufgefüllt `cognitivemodels.json` werden. Die entsprechende NEUEINFN-Datei finden Sie [hier,](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json) und so sieht die entsprechende `.lu` Datei aus.

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

Bei diesem Ansatz werden alle Befehlsprobleme eines Benutzers an den virtuellen Assistenten im Zusammenhang mit oder können als Befehl identifiziert werden, der dem `book room` Bot "Book-a-room" zugeordnet ist, und an diese Fähigkeit `manage favorites` weitergeleitet.
Andererseits muss der Raumbot "Book-a-room" das MODELL EINES BUCHS verwenden, um diese Befehle zu verstehen, wenn sie nicht wie beschriftt sind (z. B.: `I want to manage my favorite rooms` ).

### <a name="multi-language-support"></a>Mehrsprachige Unterstützung

In diesem Beispiel haben wir nur ein MODELL MIT EINER ENGLISCHEN Kultur erstellt. Sie können EINES -Modell erstellen, das anderen Sprachen entspricht, und Eintrag hinzufügen zu `cognitivemodels.json` .

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

Fügen Sie parallel die entsprechende `.lu` Datei im pfadordnerischen Pfad hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Aktualisieren Sie den Befehl "botskills" wie folgt, um den Parameter `languages` zu ändern:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Der virtuelle Assistent identifiziert `SetLocaleMiddleware` das aktuelle Locale und ruft das entsprechende Verteilermodell auf. (Bot-Framework-Aktivität verfügt über ein Von-Ort-Feld, das von dieser Middleware verwendet wird.) Es wird empfohlen, dasselbe für Ihre Fähigkeiten zu verwenden. Book-a-room bot does not use this middleware and instead gets locale from Bot framework activity's [clientInfo entity.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)

### <a name="claim-validation"></a>Anspruchsüberprüfung

Wir haben [claimsValidator hinzugefügt,](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) um Anrufer auf die Fähigkeit einzuschränken. Damit ein virtueller Assistent diese Kompetenz aufrufen kann, füllen Sie das Array mit der App-ID dieses bestimmten virtuellen Assistenten `AllowedCallers` `appsettings` auf.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das Array der zulässigen Anrufer kann einschränken, welche Fertigkeiten Verbraucher auf die Fähigkeit zugreifen können. Fügen Sie diesem `*` Array einen einzelnen Eintrag hinzu, um Anrufe von einem beliebigen Fertigkeitsverbraucher zu akzeptieren.

```
"AllowedCallers": [ "*" ],
```
Eine ausführliche Dokumentation zum Hinzufügen der Anspruchsprüfung zu einer Kompetenz finden Sie [hier.](https://docs.microsoft.com/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator)

### <a name="card-refresh-limitation"></a>Einschränkung der Kartenaktualisierung

Aktualisierungsaktivitäten (Kartenaktualisierung) werden über den virtuellen Assistenten[(GitHub-Problem) noch nicht unterstützt.](https://github.com/microsoft/botbuilder-dotnet/issues/3686) Daher haben wir alle Kartenaktualisierungsaufrufe ( `UpdateActivityAsync` ) durch das Veröffentlichen neuer Kartenanrufe( ) ersetzt. `SendActivityAsync`

### <a name="card-actions-and-task-module-flows"></a>Kartenaktionen und Aufgabenmodulabläufe

Um Kartenaktions- oder Aufgabenmodulaktivitäten an eine zugeordnete Fähigkeit weiter zu weiterleiten, muss die Fähigkeit darin `skillId` eingebettet werden.
Botkartenaktion "Buch-a-Raum", Aufgabenmodul zum Abrufen und Übermitteln von Aktionsnutzlasten werden so geändert, dass sie `skillId` als Parameter enthalten sind. 

Weitere Informationen finden Sie [in diesem](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) Abschnitt aus dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Behandeln von Aktivitäten im Gruppenchat- oder Kanalbereich

Book-a-room bot ist nur für private Chats (persönlicher/1:1-Bereich) konzipiert. Da wir den virtuellen Assistenten angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, wird der virtuelle Assistent möglicherweise aus diesen Bereich aufgerufen, und daher kann der Bot "Buch-ein-Raum" Aktivitäten für denselben Bereich erhalten. Daher ist der Bot "Book-a-room" so angepasst, dass er diese Aktivitäten verarbeiten kann. Die Überprüfung wurde in Methoden des Aktivitätshandlers des `OnMessageActivityAsync` Bots "Book-a-room" verwendet.

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

Sie können auch vorhandene Fähigkeiten aus dem [Bot-Framework-Lösungsrepository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder ganz von Grund auf neue Fähigkeiten erstellen. Lernprogramme für den späteren Zeitpunkt finden Sie [hier.](https://microsoft.github.io/botframework-solutions/overview/skills/) Weitere Informationen finden Sie [in der Dokumentation](https://docs.microsoft.com/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0)   zur Architektur des virtuellen Assistenten und der Fähigkeiten.

## <a name="sample-code-to-get-started"></a>Beispielcode für die ersten Schritte

- [Aktualisierte Visual Studio-Vorlage](https://github.com/nebhagat/msteams-virtual-assistant-dotnet)
- [Book-a-room-Bot-Fertigkeitencode](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill)

## <a name="virtual-assistant-known-limitations"></a>Bekannte Einschränkungen des virtuellen Assistenten

- **EndOfConversation**. Eine Fähigkeit sollte eine Aktivität `endOfConversation` senden, wenn sie eine Unterhaltung beendet. Als Grundlage für diese Aktivität beendet ein virtueller Assistent den Kontext mit dieser bestimmten Fähigkeit und geht wieder in den Kontext des virtuellen Assistenten (Stammkontext) zurück. Für Book-a-Room-Bots gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet werden kann. Daher haben wir nicht vom `endOfConversation` Bot "Book-a-room" gesendet, und wenn der Benutzer zum Stammkontext zurück möchte, kann er dies einfach per Befehl `start over` tun.
- **Kartenaktualisierung**. Kartenaktualisierungen werden vom virtuellen Assistenten noch nicht unterstützt.
- **Messagingerweiterungen**.:
  - Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messagingerweiterungen unterstützen.
  - Die Konfiguration von Messagingerweiterungen ist nicht auf einzelne Befehle, sondern auf die gesamte Erweiterung selbst begrenzt. Dadurch wird die Konfiguration für jede einzelne Kompetenz über den virtuellen Assistenten beschränkt.
  - Befehls-IDs für Messagingerweiterungen haben eine maximale Länge von [64](../resources/schema/manifest-schema.md#composeextensions) Zeichen, und zum Einbetten von Fertigkeiteninformationen werden 37 Zeichen verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.
>
>
