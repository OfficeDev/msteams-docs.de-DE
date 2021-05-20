---
title: Erstellen eines virtuellen Assistenten
description: So erstellen Sie Virtual Assistant-Bot und -Fähigkeiten für den Einsatz in Microsoft Teams
localization_priority: Normal
ms.topic: how-to
keywords: Teams virtuelle Assistenten Bots
ms.openlocfilehash: 072d9cb5742cd39101587cad32e3048bd36cc1d8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566873"
---
# <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten 

Virtual Assistant ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine robuste Unterhaltungslösung erstellen können, während Sie die volle Kontrolle über die Benutzerfreundlichkeit, das Organisationsbranding und die erforderlichen Daten behalten. Die [Core-Vorlage Virtual Assistant](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) ist der grundlegende Baustein, der die Microsoft-Technologien zusammenführt, die zum Erstellen eines virtuellen Assistenten erforderlich sind, einschließlich des Bot Framework [SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/)und [QnA Maker](https://www.qnamaker.ai/). Es vereint auch die wesentlichen Funktionen, einschließlich Kompetenzregistrierung, verknüpfte Konten, grundlegende Gesprächsabsicht, um eine Reihe von nahtlosen Interaktionen und Erfahrungen für Benutzer zu bieten. Darüber hinaus enthalten die Vorlagenfunktionen umfangreiche Beispiele für wiederverwendbare [Unterhaltungsfähigkeiten](https://microsoft.github.io/botframework-solutions/overview/skills).  Individuelle Fähigkeiten werden in eine Virtual Assistant-Lösung integriert, um mehrere Szenarien zu ermöglichen. Mithilfe des Bot Framework SDK werden Fähigkeiten in Quellcodeform dargestellt, sodass Sie sie bei Bedarf anpassen und erweitern können. Weitere Informationen zu den Fähigkeiten von Bot Framework finden Sie unter [Was ist ein Bot Framework.](https://microsoft.github.io/botframework-solutions/overview/skills/) In diesem Dokument finden Sie Anleitungen zur Implementierung des virtuellen Assistenten für Organisationen, zum Erstellen eines Teams fokussierten virtuellen Assistenten, zum zugehörigen Beispiel, zum Codebeispiel und zu Einschränkungen des virtuellen Assistenten.
Die folgende Abbildung zeigt die Übersicht des virtuellen Assistenten:

![Übersichtsdiagramm des virtuellen Assistenten](../assets/images/bots/virtual-assistant/overview.png)

Textnachrichtenaktivitäten werden vom Virtual Assistant-Kern mithilfe eines [Dispatchmodells](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) an zugeordnete Fertigkeiten weitergeleitet. 

## <a name="implementation-considerations"></a>Überlegungen zur Umsetzung

Die Entscheidung, einen virtuellen Assistenten hinzuzufügen, enthält viele Determinanten und unterscheidet sich für jede Organisation. Die unterstützenden Faktoren einer Virtual Assistant-Implementierung für Ihre Organisation sind:

* Ein zentrales Team verwaltet alle Mitarbeitererfahrungen. Es verfügt über die Fähigkeit, eine Virtual Assistant-Erfahrung zu erstellen und Updates für die Kernerfahrung zu verwalten, einschließlich des Hinzufügens neuer Fähigkeiten.
* Es gibt mehrere Anwendungen über Geschäftsfunktionen hinweg, und die Zahl wird in Zukunft voraussichtlich zunehmen.
* Vorhandene Anwendungen sind anpassbar, gehören der Organisation und werden in Fähigkeiten für einen virtuellen Assistenten umgewandelt.
* Das zentrale Mitarbeitererfahrungsteam ist in der Lage, Anpassungen an vorhandenen Apps zu beeinflussen. Darüber hinaus finden Sie notwendige Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in Virtual Assistant."

Die folgende Abbildung zeigt die Geschäftsfunktionen von Virtual Assistant: 

![Zentrales Team unterhält den Assistenten, und Business Function Teams tragen Fähigkeiten bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines Teams-orientierten virtuellen Assistenten

Microsoft hat eine [Visual Studio-Vorlage](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) zum Erstellen virtueller Assistenten und Fähigkeiten veröffentlicht. Mit der Visual Studio-Vorlage können Sie einen virtuellen Assistenten erstellen, der durch eine textbasierte Erfahrung mit Unterstützung für begrenzte Rich Cards mit Aktionen unterstützt wird. Wir haben die Visual Studio Basisvorlage erweitert, um Microsoft Teams Plattformfunktionen und großartige Teams App-Erlebnissen einzuschließen. Zu den Funktionen gehören Unterstützung für umfangreiche Adaptive Cards, Aufgabenmodule, Teams oder Gruppenchats und Messagingerweiterungen. Weitere Informationen zum Erweitern des virtuellen Assistenten auf Microsoft Teams finden Sie unter [Tutorial: Erweitern Des virtuellen Assistenten auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).    
In der folgenden Abbildung wird das übergeordnete Diagramm einer Virtual Assistant-Lösung angezeigt:

![High-Level-Diagramm einer Virtual Assistant-Lösung](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen von Adaptive Cards zu Ihrem virtuellen Assistenten

Um Anforderungen ordnungsgemäß zu versenden, muss Ihr virtueller Assistent das richtige LUIS-Modell und die damit verbundene Fähigkeit identifizieren. Der Dispatching-Mechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das LUIS-Modell, das einer Fertigkeit zugeordnet ist, für Kartenaktionstexte trainiert wird. Die Kartenaktionstexte sind feste, vordefinierte Schlüsselwörter und werden nicht von einem Benutzer kommentiert.

Dieser Nachteil wird dadurch behoben, dass Qualifikationsinformationen in die Nutzlast der Kartenaktion eingebettet werden. Jede Fertigkeit sollte `skillId` sich in den Bereich der Kartenaktionen einbetten. `value` Sie müssen sicherstellen, dass jede Kartenaktionsaktivität die relevanten Qualifikationsinformationen enthält, und Der virtuelle Assistent kann diese Informationen für den Versand verwenden.

Sie müssen `skillId` im Konstruktor angeben, dass die Fertigkeitsinformationen immer in Kartenaktionen vorhanden sind.
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

Als Nächstes `SkillCardActionData` wird die Klasse in der Vorlage "Virtueller Assistent" eingeführt, um aus der `skillId` Nutzlast der Kartenaktion zu extrahieren.
Ein Codeausschnitt zum Extrahieren  `skillId` aus der Kartenaktionsnutzlast wird im folgenden Abschnitt gezeigt:

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

Die Implementierung erfolgt über eine [](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) Erweiterungsmethode in der Activity-Klasse.
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

Der virtuelle Assistent kann Unterbrechungen in Fällen verarbeiten, in denen ein Benutzer versucht, eine Fertigkeit aufzurufen, während eine andere Fertigkeit derzeit aktiv ist. `TeamsSkillDialog`und `TeamsSwitchSkillDialog` werden basierend auf Bot Frameworks [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)eingeführt. Sie ermöglichen es Benutzern, eine Fertigkeitserfahrung von Kartenaktionen zu wechseln. Um diese Anforderung zu verarbeiten, fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsnachricht auf, die Fähigkeiten zu wechseln:

![Bestätigungsaufforderung beim Wechsel zu einer neuen Fertigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Behandeln von Aufgabenmodulanforderungen

Um einem virtuellen Assistenten Aufgabenmodulfunktionen hinzuzufügen, sind zwei zusätzliche Methoden im Aktivitätshandler des virtuellen Assistenten enthalten: `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` . Diese Methoden hören auf Aufgabenmodul-bezogene Aktivitäten von Virtual Assistant, identifizieren die der Anforderung zugeordnete Fertigkeit und leiten die Anforderung an die identifizierte Fertigkeit weiter. 

Die Anforderungsweiterleitung erfolgt über die [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true), `PostActivityAsync` Methode. Es gibt die Antwort als `InvokeResponse` zurück, die analysiert und in konvertiert `TaskModuleResponse` wird.


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

Ein ähnlicher Ansatz wird für Kartenaktionsdispatching und Aufgabenmodulantworten verfolgt. Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird aktualisiert, um `skillId` . Die Activity Extension-Methode `GetSkillId` extrahiert `skillId` aus der Nutzlast, die Details über die Fertigkeit enthält, die aufgerufen werden muss.

Der Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` die Methoden sind im folgenden Abschnitt angegeben:

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

Darüber hinaus müssen Sie alle Qualifikationsdomänen in den Abschnitt in die `validDomains` Manifestdatei des virtuellen Assistenten aufnehmen, damit Aufgabenmodule, die durch eine Fertigkeit aufgerufen werden, ordnungsgemäß gerendert werden.

### <a name="handle-collaborative-app-scopes"></a>Behandeln kollaborativer App-Bereiche

Teams-Apps können in mehreren Bereichen vorhanden sein, einschließlich 1:1-Chat, Gruppenchat und Kanälen. Die zentrale Vorlage für virtual Assistant ist für 1:1-Chats konzipiert. Im Rahmen der Onboarding-Erfahrung fordert Virtual Assistant Benutzer zur Eingabe des Namens auf und behält den Benutzerstatus bei. Da diese Onboarding-Erfahrung nicht für Gruppenchats oder Kanalbereiche geeignet ist, wurde sie entfernt.

Fähigkeiten sollten Aktivitäten in mehreren Bereichen behandeln, z. B. 1:1-Chat, Gruppenchat und Kanalunterhaltung. Wenn einer dieser Bereiche nicht unterstützt wird, müssen Fähigkeiten mit einer entsprechenden Nachricht antworten.

Die folgenden Verarbeitungsfunktionen wurden dem Virtual Assistant-Kern hinzugefügt:

* Virtueller Assistent kann ohne Textnachricht von einem Gruppenchat oder -kanal aufgerufen werden.
* Artikulationen werden vor dem Senden der Nachricht an das Dispatchmodul gesäubert. Entfernen Sie beispielsweise die erforderlichen @mention des Bots.

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

Die Befehle für eine Messagingerweiterung werden in der App-Manifestdatei deklariert. Die Benutzeroberfläche der Messagingerweiterung wird von diesen Befehlen unterstützt. Damit ein virtueller Assistent einen Messagingerweiterungsbefehl als angefügte Fertigkeit mitstrom, muss das manifest eines virtuellen Assistenten diese Befehle enthalten. Sie müssen die Befehle aus dem Manifest einer einzelnen Fertigkeit zum Manifest des virtuellen Assistenten hinzufügen. Die Befehls-ID stellt Informationen zu einer zugeordneten Fertigkeit bereit, indem die App-ID der Fertigkeit über ein Trennzeichen angehängt `:` wird.

Der Ausschnitt aus der Manifestdatei einer Fertigkeit wird im folgenden Abschnitt gezeigt:

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

Der entsprechende Virtual Assistant-Manifestdateicodeausschnitt wird im folgenden Abschnitt gezeigt:

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

Sobald die Befehle von einem Benutzer aufgerufen werden, kann der virtuelle Assistent eine zugeordnete Fertigkeit identifizieren, indem er die Befehls-ID analysiert, die Aktivität aktualisiert, indem das zusätzliche Suffix `:<skill_id>` aus der Befehls-ID entfernt wird, und es an die entsprechende Fertigkeit weiterleitet. Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht verarbeiten. Somit werden Konflikte zwischen Befehls-IDs über Fähigkeiten hinweg vermieden. Bei diesem Ansatz werden alle Such- und Aktionsbefehle einer Fertigkeit in allen Kontexten, z. B. **compose**, **commandBox** und **Message,** von einem virtuellen Assistenten unterstützt.

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

Einige Messagingerweiterungsaktivitäten enthalten nicht die Befehls-ID. Enthält z. `composeExtension/selectItem` B. nur den Wert der Aufrufaktion. Um die zugeordnete Fertigkeit zu identifizieren, `skillId`  wird jeder Artikelkarte angefügt, während eine Antwort für gebildet `OnTeamsMessagingExtensionQueryAsync` wird. Dies ähnelt dem Ansatz zum [Hinzufügen von adaptiven Karten zu Ihrem virtuellen Assistenten](#add-adaptive-cards-to-your-virtual-assistant).

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

Das folgende Beispiel zeigt, wie Sie die Book-a-Room-App-Vorlage in eine Virtual Assistant-Fähigkeit konvertieren: Book-a-room ist ein Microsoft Teams, mit dem Benutzer schnell einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Zeit finden und reservieren können. Die Standardzeit beträgt 30 Minuten. Der Book-a-room-Bot bietet persönliche oder 1:1-Gespräche. In der folgenden Abbildung wird ein virtueller Assistent mit einem **Buch und einer Raumfertigkeit** angezeigt:

![Virtueller Assistent mit einer "Zimmerbuch"-Fähigkeit](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Im Folgenden werden die Deltaänderungen eingeführt, um sie in eine Fertigkeit zu konvertieren, die an einen virtuellen Assistenten angefügt ist. Ähnliche Richtlinien werden befolgt, um einen vorhandenen v4-Bot in eine Fertigkeit umzuwandeln.

### <a name="skill-manifest"></a>Skill-Manifest

Ein Skill-Manifest ist eine JSON-Datei, die den Messagingendpunkt, die ID, den Namen und andere relevante Metadaten einer Fertigkeit verfügbar macht. Dieses Manifest unterscheidet sich von dem Manifest, das zum Sideloading einer App in Microsoft Teams verwendet wird. Ein virtueller Assistent benötigt einen Pfad zu dieser Datei als Eingabe, um eine Fertigkeit anzuhängen. Wir haben das folgende Manifest zum wwwroot-Ordner des Bots hinzugefügt.

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

### <a name="luis-integration"></a>LUIS Integration

Das Dispatch-Modell des virtuellen Assistenten basiert auf den LUIS-Modellen der angehängten Fähigkeiten. Das Dispatchmodell identifiziert die Absicht für jede Textaktivität und ermittelt die damit verbundene Fertigkeit.

Virtual Assistant erfordert das LUIS-Modell der Fertigkeit im `.lu` Format als Eingabe, während eine Fertigkeit angefügt wird. LUIS json wird `.lu` mit dem Tool botframework-cli in das Format konvertiert.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

Book-a-room Bot hat zwei Hauptbefehle für Benutzer:

- `Book room`
- `Manage Favorites`

Wir haben ein LUIS-Modell erstellt, indem wir diese beiden Befehle verstanden haben. Entsprechende Geheimnisse müssen in aufgefüllt `cognitivemodels.json` werden. Die entsprechende LUIS JSON-Datei finden Sie [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/book-a-meeting.json).
Die entsprechende `.lu` Datei wird im folgenden Abschnitt gezeigt:

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

Bei diesem Ansatz wird jeder Befehl, der von einem Benutzer an Virtual Assistant ausgegeben wird, mit dem Bot verknüpft `book room` oder `manage favorites` als Befehl identifiziert, der mit bot verknüpft `Book-a-room` ist, und an diese Fertigkeit weitergeleitet.
Auf der anderen Seite `Book-a-room room` muss Bot LUIS-Modell verwenden, um diese Befehle zu verstehen, wenn sie nicht voll eingegeben sind. Zum Beispiel: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Multi-Language-Unterstützung

Beispielsweise wird ein LUIS-Modell mit nur englischer Kultur erstellt. Sie können LUIS-Modelle erstellen, die anderen Sprachen entsprechen, und Eintrag zu `cognitivemodels.json` hinzufügen.

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

Fügen Sie parallel eine entsprechende `.lu` Datei im pfad luisFolder hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Um den Parameter zu `languages` ändern, aktualisieren Sie den Befehl botskills wie folgt:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Virtual Assistant `SetLocaleMiddleware` verwendet, um das aktuelle Gebietsschema zu identifizieren und das entsprechende Dispatchmodell aufzurufen. Bot-Framework-Aktivität hat Gebietsschema-Feld, das von dieser Middleware verwendet wird. Sie können das gleiche auch für Ihre Fähigkeiten verwenden. Book-a-room bot verwendet diese Middleware nicht und erhält stattdessen Gebietsschema von der [ClientInfo-Entität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)der Bot-Frameworkaktivität .

### <a name="claim-validation"></a>Anspruchsvalidierung

Wir haben [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) hinzugefügt, um Aufrufer auf die Fertigkeit zu beschränken. Damit ein virtueller Assistent diese Fertigkeit aufrufen kann, füllen Sie `AllowedCallers` das Array mit der `appsettings` App-ID dieses bestimmten virtuellen Assistenten aus.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das Array der zulässigen Aufrufer kann einschränken, auf welche Fähigkeiten Verbraucher auf die Fertigkeit zugreifen können. Fügen Sie diesem Array einen einzelnen Eintrag `*` hinzu, um Anrufe von jedem Skill-Consumer anzunehmen.

```
"AllowedCallers": [ "*" ],
```

Weitere Informationen zum Hinzufügen der Anspruchsvalidierung zu einer Fertigkeit finden Sie unter Hinzufügen von [Anspruchsvalidierung zu Skill](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).

### <a name="limitation-of-card-refresh"></a>Einschränkung der Kartenaktualisierung 

Aktualisierungsaktivität, z. B. Kartenaktualisierung, wird noch nicht über Virtual Assistant ([github issue](https://github.com/microsoft/botbuilder-dotnet/issues/3686)) unterstützt. Daher haben wir alle Kartenaktualisierungsanrufe durch das `UpdateActivityAsync` Posten neuer Kartenanrufe `SendActivityAsync` ersetzt.

### <a name="card-actions-and-task-module-flows"></a>Kartenaktionen und Aufgabenmodulflüsse

Um Kartenaktions- oder Aufgabenmodulaktivitäten an eine zugeordnete Fertigkeit weiterzuleiten, muss die Fertigkeit in sie eingebettet `skillId` werden.
`Book-a-room` Bot-Kartenaktion, Taskmodul abrufen und Aktionsnutzlasten werden so geändert, dass sie als Parameter enthalten `skillId` sind. 

Weitere Informationen finden Sie in [diesem](https://msteams-captain.visualstudio.com/xGrowth%20App%20Templates/_wiki/wikis/xGrowth.wiki/88/Virtual-Assistant-for-MS-Teams?anchor=rich-cards) Abschnitt in dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Behandeln von Aktivitäten aus Demons- oder Kanalbereich

`Book-a-room bot` ist nur für private Chats, wie z. B. persönlichen oder 1:1-Bereich, konzipiert. Da wir Virtual Assistant angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, muss der virtuelle Assistent aus den Kanalbereichen aufgerufen werden und daher `Book-a-room` muss Bot Aktivitäten für den gleichen Bereich abrufen. Daher `Book-a-room` ist Bot angepasst, um diese Aktivitäten zu behandeln. Sie finden die `OnMessageActivityAsync` Eincheckmethoden des `Book-a-room` Aktivitätshandlers des Bots.

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

Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework Solutions-Repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder eine neue Fertigkeit ganz von Grund auf neu erstellen. Informationen zum Erstellen einer neuen Fertigkeit finden Sie in [den Lernprogrammen zum Erstellen einer neuen Fertigkeit](https://microsoft.github.io/botframework-solutions/overview/skills/). Informationen zur Dokumentation zur Virtual Assistant- und Skills-Architektur finden Sie unter[Virtual Assistant und Skills Architecture](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).  

## <a name="limitations-of-virtual-assistant"></a>Einschränkungen des virtuellen Assistenten 

* **EndOfConversation**: Eine Fertigkeit muss eine `endOfConversation` Aktivität senden, wenn sie eine Unterhaltung beendet. Basierend auf der Aktivität beendet ein virtueller Assistent den Kontext mit dieser speziellen Fertigkeit und kehrt in den Stammkontext des virtuellen Assistenten zurück. Für Book-a-room Bot gibt es keinen eindeutigen Zustand, in dem das Gespräch beendet wird. Daher haben wir nicht von Bot gesendet `endOfConversation` und wenn Benutzer zurück zum `Book-a-room` Root-Kontext gehen will, können sie dies einfach per `start over` Befehl tun.  
* **Kartenaktualisierung**: Die Kartenaktualisierung wird noch nicht über Virtual Assistant unterstützt.  
* **Messaging-Erweiterungen**:
  * Derzeit kann ein virtueller Assistent maximal zehn Befehle für Messagingerweiterungen unterstützen.
  * Die Konfiguration von Messagingerweiterungen ist nicht auf einzelne Befehle beschränkt, sondern auf die gesamte Erweiterung selbst. Dadurch wird die Konfiguration für jede einzelne Fertigkeit über Virtual Assistant begrenzt.
  * Messaging-Erweiterungen Befehls-IDs haben eine maximale Länge von [64 Zeichen](../resources/schema/manifest-schema.md#composeextensions) und 37 Zeichen werden zum Einbetten von Fertigkeitsinformationen verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.

Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework Solutions-Repository](https://github.com/microsoft/botframework-solutions/tree/master/skills/csharp) nutzen oder eine neue Fertigkeit ganz von Grund auf neu erstellen. Tutorials für die spätere finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/). Weitere Informationen finden Sie in der [Dokumentation zu](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) Virtual Assistant und Skills Architecture.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **C#** | **.NET** |
|----------|-----------------|----------|------------------|
| Aktualisierte visuelle Studiovorlage | Angepasste Vorlage zur Unterstützung von Teams.de | [View](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |
| Book-a-Room-Bot-Fähigkeitscode | Ermöglicht ihnen, unterwegs schnell einen Tagungsraum zu finden und zu buchen. |  | [View](https://github.com/nebhagat/msteams-virtual-assistant-dotnet) |


## <a name="see-also"></a>Siehe auch

- [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)

- [Buch-a-Zimmer](app-templates.md#book-a-room)

- [Microsoft Teams-Bot](../bots/what-are-bots.md)