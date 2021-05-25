---
title: Erstellen eines virtuellen Assistenten
description: Erstellen von virtuellen Assistenten-Bots und -Fähigkeiten für die Verwendung in Microsoft Teams
localization_priority: Normal
ms.topic: how-to
keywords: teams Virtual Assistant Bots
ms.openlocfilehash: dea62a69a08c8d216a17dbd58558435f3cc623e8
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630733"
---
# <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten 

Der virtuelle Assistent ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die vollständige Kontrolle über die Benutzeroberfläche, das Unternehmensbranding und die erforderlichen Daten beibehalten können. Die [Kernvorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) des virtuellen Assistenten ist der grundlegende Baustein, der die zum Erstellen eines virtuellen Assistenten erforderlichen Microsoft-Technologien zusammen bringt, einschließlich [bot Framework SDK,](https://github.com/microsoft/botframework-sdk)Language Understanding [(LUS)](https://www.luis.ai/)und [QnA Maker](https://www.qnamaker.ai/). Außerdem werden die wesentlichen Funktionen wie die Registrierung von Fähigkeiten, verknüpfte Konten und grundlegende Unterhaltungsabsichten zusammengekoppelt, um Benutzern eine Reihe nahtloser Interaktionen und Erfahrungen zu bieten. Darüber hinaus enthalten die Vorlagenfunktionen umfassende Beispiele für wiederverwendbare [Unterhaltungskenntnisse.](https://microsoft.github.io/botframework-solutions/overview/skills)  Individuelle Fähigkeiten werden in eine Virtual Assistant-Lösung integriert, um mehrere Szenarien zu ermöglichen. Mithilfe des Bot Framework SDK werden Die Fähigkeiten im Quellcode dargestellt, sodass Sie die Funktionen nach Bedarf anpassen und erweitern können. Weitere Informationen zu den Fähigkeiten von Bot Framework finden Sie unter [What is a Bot Framework skill](https://microsoft.github.io/botframework-solutions/overview/skills/). Dieses Dokument führt Sie zu Überlegungen zur Implementierung des virtuellen Assistenten für Organisationen, zum Erstellen eines Teams-fokussierten virtuellen Assistenten, zugehörigen Beispielen, Codebeispielen und Einschränkungen des virtuellen Assistenten.
Die folgende Abbildung zeigt die Übersicht über den virtuellen Assistenten:

![Übersichtsdiagramm des virtuellen Assistenten](../assets/images/bots/virtual-assistant/overview.png)

Textnachrichtenaktivitäten werden vom Kern des virtuellen Assistenten mithilfe eines Versandmodells an [zugeordnete Fähigkeiten geroutet.](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) 

## <a name="implementation-considerations"></a>Überlegungen zur Implementierung

Die Entscheidung, einen virtuellen Assistenten hinzuzufügen, umfasst viele Determinanten und unterscheidet sich für jede Organisation. Die unterstützenden Faktoren einer Virtual Assistant-Implementierung für Ihre Organisation sind wie folgt:

* Ein zentrales Team verwaltet alle Mitarbeitererfahrungen. Es verfügt über die Möglichkeit, eine virtuelle Assistentenerfahrung zu erstellen und Updates für die Kernerfahrung zu verwalten, einschließlich der Hinzu ergänzung neuer Fähigkeiten.
* Mehrere Anwendungen sind in verschiedenen Geschäftsfunktionen vorhanden, und die Anzahl wird in Zukunft voraussichtlich zunehmen.
* Vorhandene Anwendungen sind anpassbar, gehören der Organisation und werden in Fertigkeiten für einen virtuellen Assistenten umgewandelt.
* Das team für zentrale Mitarbeitererfahrungen ist in der Lage, Anpassungen an vorhandenen Apps zu beeinflussen. Sie bietet außerdem die erforderlichen Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in der Virtuellen Assistenten-Erfahrung.

In der folgenden Abbildung werden die Geschäftsfunktionen des virtuellen Assistenten angezeigt: 

![Zentrales Team pflegt den Assistenten, und Geschäftsfunktionsteams tragen Fähigkeiten bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines Teams virtuellen Assistenten

Microsoft hat eine Visual Studio [zum](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) Erstellen virtueller Assistenten und Fähigkeiten veröffentlicht. Mit der Visual Studio können Sie einen virtuellen Assistenten erstellen, der von einer textbasierten Erfahrung mit Unterstützung für eingeschränkte Rich Cards mit Aktionen unterstützt wird. Wir haben die Basisvorlage Visual Studio erweitert, um Microsoft Teams Plattformfunktionen und die Teams zu erweitern. Einige der Funktionen umfassen unterstützung für umfangreiche adaptive Karten, Aufgabenmodule, Teams oder Gruppenchats und Messagingerweiterungen. Weitere Informationen zum Erweitern des virtuellen Assistenten auf Microsoft Teams finden Sie unter [Tutorial: Extend Your Virtual Assistant to Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).    
Die folgende Abbildung zeigt das Diagramm auf hoher Ebene einer Virtuellen Assistentenlösung:

![Diagramm einer virtuellen Assistentenlösung auf hoher Ebene](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen adaptiver Karten zu Ihrem virtuellen Assistenten

Damit Anforderungen ordnungsgemäß versendet werden können, muss Ihr virtueller Assistent das richtige MODELL FÜR DAS MODELL und die entsprechenden ihm zugeordneten Fähigkeiten identifizieren. Der Verteilmechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das einem Skill zugeordnete MODELL FÜR KARTENaktionen für Kartenaktionstexte geschult wird. Die Kartenaktionstexte sind feste, vordefinierte Schlüsselwörter und werden nicht von einem Benutzer kommentiert.

Dieser Nachteil wird durch Einbetten von Qualifikationsinformationen in die Kartenaktionsnutzlast behoben. Jede Fertigkeit sollte `skillId` in das Feld der  `value` Kartenaktionen eingebettet werden. Sie müssen sicherstellen, dass jede Kartenaktionsaktivität die relevanten Fertigkeiteninformationen enthält, und der virtuelle Assistent kann diese Informationen für die Versendung verwenden.

Sie müssen im Konstruktor bereitstellen, um sicherzustellen, dass die Fertigkeiteninformationen immer `skillId` in Kartenaktionen vorhanden sind.
Ein Beispielcode für Kartenaktionsdaten wird im folgenden Abschnitt angezeigt:
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

Als Nächstes wird die Klasse in der Vorlage Virtueller Assistent zum Extrahieren aus der Nutzlast der `SkillCardActionData` `skillId` Kartenaktion präsentiert.
Ein Codeausschnitt, der aus der Nutzlast der Kartenaktion extrahiert werden  `skillId` soll, wird im folgenden Abschnitt angezeigt:

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

Die Implementierung erfolgt über eine Erweiterungsmethode in der [Activity-Klasse.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)
Ein Codeausschnitt zum Extrahieren  `skillId` aus Kartenaktionsdaten wird im folgenden Abschnitt angezeigt:

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

### <a name="handle-interruptions"></a>Behandeln von Unterbrechungen

Der virtuelle Assistent kann Unterbrechungen in Fällen verarbeiten, in denen ein Benutzer versucht, eine Fähigkeit aufrief, während eine andere Fähigkeit derzeit aktiv ist. `TeamsSkillDialog`und `TeamsSwitchSkillDialog` werden basierend auf Den [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von Bot Framework eingeführt. Sie ermöglichen Benutzern das Wechseln einer Kompetenzerfahrung von Kartenaktionen. Um diese Anforderung zu verarbeiten, fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsnachricht auf, die Fähigkeiten zu wechseln:

![Bestätigungsaufforderung beim Wechseln zu einer neuen Fertigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Behandeln von Aufgabenmodulanforderungen

Zum Hinzufügen von Aufgabenmodulfunktionen zu einem virtuellen Assistenten sind zwei zusätzliche Methoden im Aktivitätshandler des virtuellen Assistenten `OnTeamsTaskModuleFetchAsync` enthalten: und `OnTeamsTaskModuleSubmitAsync` . Diese Methoden lauschen aufgabenmodulbezogenen Aktivitäten vom virtuellen Assistenten, identifizieren die der Anforderung zugeordneten Fähigkeiten und geben die Anforderung an die identifizierte Fähigkeit weiter. 

Die Anforderungs weiterleitung erfolgt über die [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true), `PostActivityAsync` -Methode. Es gibt die Antwort `InvokeResponse` zurück, die analysiert und in konvertiert `TaskModuleResponse` wird.


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

Ein ähnlicher Ansatz wird für kartenaktionsversand und Aufgabenmodulantworten verwendet. Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird so aktualisiert, dass sie enthalten `skillId` sind. Die Activity Extension-Methode extrahiert aus der Nutzlast, die Details zu den Fähigkeiten `GetSkillId` `skillId` enthält, die aufgerufen werden müssen.

Der Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und die Methoden finden Sie im folgenden `OnTeamsTaskModuleSubmitAsync` Abschnitt:

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

Darüber hinaus müssen Sie alle Kompetenzdomänen in den Abschnitt in die Manifestdatei des virtuellen Assistenten hinzufügen, damit Aufgabenmodule, die über eine Fähigkeit aufgerufen werden, ordnungsgemäß `validDomains` gerendert werden.

### <a name="handle-collaborative-app-scopes"></a>Behandeln kollaborativer App-Bereiche

Teams apps can exist in multiple scopes including 1:1 chat, group chat, and channels. Die zentrale Vorlage für den virtuellen Assistenten ist für 1:1-Chats konzipiert. Im Rahmen der Onboardingerfahrung fordert der virtuelle Assistent Benutzer zum Namen auf und behält den Benutzerstatus bei. Da diese Onboardingerfahrung nicht für Gruppenchat- oder Kanalbereiche geeignet ist, wurde sie entfernt.

Fähigkeiten sollten Aktivitäten in mehreren Bereich behandeln, z. B. 1:1-Chat, Gruppenchat und Kanalunterhaltung. Wenn einer dieser Bereiche nicht unterstützt wird, müssen Die Qualifikationen mit einer entsprechenden Nachricht antworten.

Die folgenden Verarbeitungsfunktionen wurden zu Virtual Assistant Core hinzugefügt:

* Der virtuelle Assistent kann ohne Textnachricht aus einem Gruppenchat oder -kanal aufgerufen werden.
* Artikulationen werden vor dem Senden der Nachricht an das Verteilermodul bereinigt. Entfernen Sie z. B. die @mention des Bots.

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

### <a name="handle-messaging-extensions"></a>Behandeln von Messagingerweiterungen

Die Befehle für eine Messagingerweiterung werden in Ihrer App-Manifestdatei deklariert. Die Benutzeroberfläche der Messagingerweiterung wird von diesen Befehlen unterstützt. Damit ein virtueller Assistent einen Befehl zur Nachrichtenerweiterung als angefügte Fähigkeit ausführen kann, muss das eigene Manifest eines virtuellen Assistenten diese Befehle enthalten. Sie müssen die Befehle aus dem Manifest einer einzelnen Fähigkeit zum Manifest des virtuellen Assistenten hinzufügen. Die Befehls-ID enthält Informationen zu einer zugeordneten Fähigkeit, indem die App-ID der Fähigkeit über ein Trennzeichen angefügt `:` wird.

Der Codeausschnitt aus der Manifestdatei einer Fähigkeit wird im folgenden Abschnitt angezeigt:

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

Der entsprechende Codeausschnitt der Manifestdatei des virtuellen Assistenten wird im folgenden Abschnitt angezeigt:

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

Sobald die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent eine zugeordnete Fähigkeit identifizieren, indem er die Befehls-ID durch Analyse der Befehls-ID identifiziert, die Aktivität aktualisiert, indem das zusätzliche Suffix aus der Befehls-ID entfernt wird, und es an die entsprechende Fähigkeit `:<skill_id>` weiterleiten. Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht verarbeiten. Auf diese Weise werden Konflikte zwischen Befehls-IDs über Die Fähigkeiten hinweg vermieden. Bei diesem Ansatz werden alle Such- und Aktionsbefehle einer Fähigkeit in allen Kontexten, z. B. **verfassen,** **commandBox** und **Nachricht,** von einem virtuellen Assistenten unterstützt.

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

Einige Messagingerweiterungsaktivitäten enthalten nicht die Befehls-ID. Enthält beispielsweise `composeExtension/selectItem` nur den Wert der Aufruftippaktion. Um die zugeordnete Fähigkeit zu identifizieren, wird jede Elementkarte `skillId`  angefügt, während sie eine Antwort für `OnTeamsMessagingExtensionQueryAsync` bildet. Dies ähnelt dem Ansatz zum Hinzufügen [adaptiver Karten zu Ihrem virtuellen Assistenten.](#add-adaptive-cards-to-your-virtual-assistant)

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

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie Sie die App-Vorlage "Book-a-room" in eine Virtuelle Assistent-Fähigkeit konvertieren: "Book-a-room" ist ein Microsoft Teams, mit dem Benutzer einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Zeit schnell finden und reservieren können. Die Standardzeit beträgt 30 Minuten. Der Book-a-room-Bot bietet Bereiche für persönliche oder 1:1-Unterhaltungen. In der folgenden Abbildung wird ein virtueller Assistent mit einem **Buch mit Raumfertigkeit** angezeigt:

![Virtueller Assistent mit einer "Raum reservieren"-Fähigkeit](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Nachfolgend finden Sie die delta-Änderungen, die eingeführt wurden, um sie in eine Fertigkeit zu konvertieren, die einem virtuellen Assistenten zugeordnet ist. Ähnliche Richtlinien werden befolgt, um vorhandene v4-Bots in eine Fertigkeit zu konvertieren.

### <a name="skill-manifest"></a>Kompetenzmanifest

Ein Kompetenzmanifest ist eine JSON-Datei, die den Messagingendpunkt, die ID, den Namen und andere relevante Metadaten einer Fähigkeit verfügbar macht. Dieses Manifest ist anders als das Manifest, das zum Querladen einer App in einem Microsoft Teams. Ein virtueller Assistent erfordert einen Pfad zu dieser Datei als Eingabe, um eine Fähigkeit anfügen zu können. Wir haben das folgende Manifest zum Wwwroot-Ordner des Bots hinzugefügt.

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

### <a name="luis-integration"></a>INTEGRATION VON LUS

Das Versandmodell des virtuellen Assistenten baut auf den ZUGEHÖRIGEN MODELL-Modellen der angefügten Fähigkeiten auf. Das Versandmodell identifiziert die Absicht für jede Textaktivität und ermittelt die damit verbundenen Fähigkeiten.

Für den virtuellen Assistenten ist das Fertigkeitsmodell "Fertigkeit" im Format als Eingabe `.lu` erforderlich, während eine Fähigkeit anfügen wird. MIT dem Botframework-cli-Tool wird DIEs in das Format `.lu` konvertiert.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

Der Book-a-Room-Bot verfügt über zwei Hauptbefehle für Benutzer:

- `Book room`
- `Manage Favorites`

Wir haben ein MODELL ERSTELLT, indem wir diese beiden Befehle verstehen. Entsprechende Geheim geheime Schlüssel müssen in aufgefüllt `cognitivemodels.json` werden. Die entsprechende LUSS-JSON-Datei finden Sie [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json).
Die entsprechende `.lu` Datei wird im folgenden Abschnitt angezeigt:

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

Bei diesem Ansatz wird jeder Befehl, der von einem Benutzer an den virtuellen Assistenten ausgegeben wird, im Zusammenhang mit oder als Befehl identifiziert, der dem Bot zugeordnet ist, und an `book room` `manage favorites` diese Fähigkeit `Book-a-room` weitergeleitet.
Auf der anderen Seite muss bot das MODELL "LUD" verwenden, um diese Befehle zu verstehen, `Book-a-room room` wenn sie nicht vollständig eingeben werden. Zum Beispiel: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Mehrsprachige Unterstützung

Als Beispiel wird ein MODELL MIT NUR englischer Kultur erstellt. Sie können DIESDING-Modelle erstellen, die anderen Sprachen entspricht, und eintragen zu `cognitivemodels.json` hinzufügen.

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

Fügen Sie parallel eine entsprechende `.lu` Datei im pfad von "luzfolder" hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Aktualisieren Sie `languages` zum Ändern des Parameters den Befehl botskills wie folgt:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Der virtuelle Assistent `SetLocaleMiddleware` verwendet, um das aktuelle Locale zu identifizieren und das entsprechende Versandmodell aufrief. Bot framework activity has locale field which is used by this middleware. Sie können dasselbe auch für Ihre Fähigkeiten verwenden. Book-a-room bot verwendet diese Middleware nicht und ruft stattdessen das Locale aus der [clientInfo-Entität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)der Bot-Framework-Aktivität ab.

### <a name="claim-validation"></a>Forderungsüberprüfung

Wir haben [claimsValidator hinzugefügt,](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) um Anrufer auf die Fähigkeit einzuschränken. Damit ein virtueller Assistent diese Fähigkeit aufrufen kann, füllen Sie das Array mit der App-ID dieses `AllowedCallers` `appsettings` bestimmten virtuellen Assistenten auf.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das Array der zugelassenen Anrufer kann einschränken, welche Benutzer auf die Fertigkeit zugreifen können. Fügen Sie diesem `*` Array einen einzelnen Eintrag hinzu, um Anrufe von jedem Kunden mit Qualifikationen zu akzeptieren.

```
"AllowedCallers": [ "*" ],
```

Weitere Informationen zum Hinzufügen der Anspruchsüberprüfung zu einer Fähigkeit finden Sie unter [Hinzufügen der Anspruchsüberprüfung zur Fähigkeit.](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true)

### <a name="limitation-of-card-refresh"></a>Einschränkung der Kartenaktualisierung 

Aktualisierungsaktivitäten, z. B. Kartenaktualisierung, werden noch nicht über den virtuellen Assistenten ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)) unterstützt. Daher haben wir alle Kartenaktualisierungsanrufe `UpdateActivityAsync` durch das Veröffentlichen neuer Kartenanrufe `SendActivityAsync` ersetzt.

### <a name="card-actions-and-task-module-flows"></a>Kartenaktionen und Aufgabenmodulflüsse

Um Kartenaktions- oder Aufgabenmodulaktivitäten an eine zugeordnete Fähigkeit weiter zu weiterleiten, muss die Fähigkeit darin `skillId` eingebettet werden.
`Book-a-room` bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter. 

Weitere Informationen finden Sie [in diesem](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) Abschnitt in dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Behandeln von Aktivitäten aus Gruppenchat- oder Kanalbereich

`Book-a-room bot` ist für private Chats konzipiert, z. B. nur für persönliche oder 1:1-Bereiche. Da wir den virtuellen Assistenten angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, muss der virtuelle Assistent über die Kanalbereiche aufgerufen werden, und daher muss bot Aktivitäten für denselben `Book-a-room` Bereich erhalten. Daher `Book-a-room` ist bot angepasst, um diese Aktivitäten zu verarbeiten. Sie finden die Check-In-Methoden `OnMessageActivityAsync` des `Book-a-room` Bot-Aktivitätshandlers.

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

Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework Solutions-Repository](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder eine neue Fähigkeit ganz neu erstellen. Informationen zum Erstellen einer neuen Fähigkeit finden Sie unter [Lernprogramme zum Erstellen einer neuen Fähigkeit.](https://microsoft.github.io/botframework-solutions/overview/skills/) Dokumentation zur Architektur des virtuellen Assistenten und der Fähigkeiten finden Sie unter[Virtual Assistant and skills architecture](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).  

## <a name="limitations-of-virtual-assistant"></a>Einschränkungen des virtuellen Assistenten 

* **EndOfConversation**: Eine Fähigkeit muss eine Aktivität `endOfConversation` senden, wenn sie eine Unterhaltung beendet. Basierend auf der Aktivität beendet ein virtueller Assistent den Kontext mit dieser bestimmten Fähigkeit und kommt wieder in den Stammkontext des virtuellen Assistenten zurück. Für Book-a-room-Bots gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet wird. Daher haben wir nicht vom Bot gesendet, und wenn der Benutzer wieder in den Stammkontext wechseln möchte, kann er `endOfConversation` `Book-a-room` dies einfach per Befehl `start over` tun.  
* **Kartenaktualisierung**: Die Kartenaktualisierung wird noch nicht über den virtuellen Assistenten unterstützt.  
* **Messagingerweiterungen**:
  * Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messagingerweiterungen unterstützen.
  * Die Konfiguration von Messagingerweiterungen ist nicht auf einzelne Befehle, sondern auf die gesamte Erweiterung selbst begrenzt. Dadurch wird die Konfiguration für jede einzelne Fähigkeit über den virtuellen Assistenten beschränkt.
  * Befehls-IDs für Messagingerweiterungen haben eine maximale Länge von [64](../resources/schema/manifest-schema.md#composeextensions) Zeichen, und 37 Zeichen werden zum Einbetten von Fertigkeiteninformationen verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.

Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework Solutions-Repository](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder eine neue Fähigkeit ganz neu erstellen. Lernprogramme für die spätere finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/). Weitere Informationen finden Sie [in der Dokumentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) zur Architektur des virtuellen Assistenten und der Fähigkeiten.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **C#** | **.NET** |
|----------|-----------------|----------|------------------|
| Visual Studio-Vorlage aktualisiert | Angepasste Vorlage zur Unterstützung von Teamfunktionen. | [View](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |
| Book-a-room bot skill code | Ermöglicht es Ihnen, unterwegs schnell einen Besprechungsraum zu finden und zu reservieren. |  | [View](https://github.com/nebhagat/msteams-virtual-assistant-dotnet) |


## <a name="see-also"></a>Sehen Sie ebenfalls

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Book-a-room](app-templates.md#book-a-room)
* [Microsoft Teams Bot](../bots/what-are-bots.md)
