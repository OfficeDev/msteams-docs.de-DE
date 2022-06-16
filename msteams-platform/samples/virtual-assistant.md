---
title: Erstellen eines virtuellen Assistenten
description: Erfahren Sie, wie Sie Virtual Assistant Bot für Teams erstellen, indem Sie Codebeispiele und Codeausschnitte mit Features wie adaptive Karten, Behandlung von Unterbrechungen und mehr verwenden.
ms.localizationpriority: medium
ms.topic: how-to
ms.openlocfilehash: 4b1dc7168cc67cd455182dddd4dd2d14a0cf9c3d
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123062"
---
# <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten

Virtual Assistant ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die volle Kontrolle über die Benutzererfahrung, das Branding und die erforderlichen Daten behalten. Die [Virtual Assistant-Hauptvorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) ist der grundlegende Baustein, der die Microsoft-Technologien vereint, die zum Erstellen eines virtuellen Assistenten erforderlich sind, einschließlich [Bot Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/) und [QnA Maker](https://www.qnamaker.ai/). Sie umfasst auch wesentliche Funktionen wie die Skillregistrierung, verknüpfte Konten und grundlegende Unterhaltungsabsichten, um den Benutzern eine Reihe reibungsloser Interaktionen und Abläufe zu bieten. Darüber hinaus enthalten die Vorlagenfunktionen umfassende Beispiele für wiederverwendbare konversationsbasierte [Skills](https://microsoft.github.io/botframework-solutions/overview/skills).  In eine virtuelle Assistentenlösung sind individuelle Skills integriert, um mehrere Szenarien zu ermöglichen. Mithilfe des Bot Framework SDK werden die Skills in Quellcodeform dargestellt, sodass Sie sie nach Bedarf anpassen und erweitern können. Weitere Informationen zu den Skills des Bot Framework finden Sie unter [Was ist ein Bot-Framework-Skill?](https://microsoft.github.io/botframework-solutions/overview/skills/). Dieses Dokument führt Sie durch Implementierungsüberlegungen zu virtuellen Assistenten für Organisationen, das Erstellen eines virtuellen Microsoft Teams-fokussierten Assistenten, verwandte Beispiele, Codebeispiele und Einschränkungen virtueller Assistenten.
Die folgende Abbildung zeigt die Übersicht über einen virtuellen Assistenten:

![Übersichtliche Darstellung zu einem virtuellen Assistenten](../assets/images/bots/virtual-assistant/overview.png)

Textnachrichtenaktivitäten werden vom zentralen virtuellen Assistenten mithilfe eines [Versandmodells](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) an die zugehörigen Skills weitergeleitet.

## <a name="implementation-considerations"></a>Überlegungen zur Implementierung

Die Entscheidung zum Hinzufügen eines virtuellen Assistenten hängt von vielen Determinanten ab, und diese unterscheiden sich für jede Organisation. Die Faktoren, die für die Implementierung eines virtuellen Assistenten für Ihre Organisation sprechen, sind die folgenden:

* Ein zentrales Team verwaltet alle Mitarbeiterfunktionen. Es kann einen virtuellen Assistenten erstellen und Updates für die zentrale Funktion verwalten, einschließlich des Hinzufügens neuer Skills.
* Es gibt mehrere Anwendungen für mehrere Geschäftsfunktionen, und es werden in Zukunft voraussichtlich mehr werden.
* Bestehende Anwendungen können angepasst werden, gehören der Organisation und werden in Skills für eine virtuellen Assistenten umgewandelt.
* Das für die zentrale Mitarbeiterfunktion verantwortliche Team kann Anpassungen an vorhandenen Apps beeinflussen. Es bietet auch die erforderliche Hilfe für die Integration vorhandener Anwendungen als Skills in den virtuellen Assistenten.

In der folgenden Abbildung sind die Geschäftsfunktionen des virtuellen Assistenten dargestellt:

![Das zentrale Team verwaltet den Assistenten, und Geschäftsfunktionsteams tragen Skills bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines virtuellen Assistenten für Microsoft Teams

Microsoft hat eine [Microsoft Visual Studio-Vorlage](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) zum Erstellen von virtuellen Assistenten und Skills veröffentlicht. Mit der Visual Studio-Vorlage können Sie eine virtuellen Assistenten erstellen, der auf einer textbasierten Lösung basiert und eingeschränkte funktionsreiche Karten mit Aktionen unterstützt. Wir haben die Visual Studio-Basisvorlage um Microsoft Teams-Plattformfunktionen erweitert für eine hervorragende Microsoft Teams App-Benutzererfahrung. Einige der Funktionen umfassen Unterstützung für funktionsreiche adaptive Karten, Aufgabenmodule, Teams- oder Gruppenchats sowie Nachrichtenerweiterungen. Weitere Informationen zum Erweitern von virtuellen Assistenten auf Microsoft Teams finden Sie im [Lernprogramm: Erweitern Ihres virtuellen Assistenten auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).
Die folgende Abbildung zeigt das Übersichtsdiagramm einer virtuellen Assistentenlösung:

![Übersichtsdiagramm einer virtuellen Assistentenlösung](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen adaptiver Karten zu Ihrem virtuellen Assistenten

Um Anforderungen ordnungsgemäß zu versenden, muss Ihr virtueller Assistent das richtige LUIS-Modell und die zugehörigen Skills identifizieren. Der Versandmechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das einem Skill zugeordnete LUIS-Modell für Kartenaktionstexte trainiert wird. Die Aktionstexte der Karte sind fixe, vordefinierte Schlüsselwörter und werden nicht von einem Benutzer kommentiert.

Dieser Nachteil wird durch das Einbetten von Skillinformationen in die Nutzlast der Kartenaktion behoben. Jeder Skill sollte `skillId` in das `value`-Feld von Kartenaktionen einbetten. Sie müssen sicherstellen, dass jede Kartenaktionsaktivität die entsprechenden Skillinformationen enthält, und dass der virtuelle Assistent diese Informationen für die Versendung nutzen kann.

Sie müssen `skillId` im Konstruktor bereitstellen, um sicherzustellen, dass die Skillinformationen immer in Kartenaktionen vorhanden sind.
Ein Beispielcode für Kartenaktionsdaten ist im folgenden Abschnitt dargestellt:

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

Als Nächstes wird die `SkillCardActionData`-Klasse in die Virtual Assistant-Vorlage eingefügt, um `skillId` aus der Nutzlast der Kartenaktion zu extrahieren.
Im folgenden Abschnitt ist ein Codeausschnitt zum Extrahieren von `skillId` aus der Nutzlast der Kartenaktion dargestellt:

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

Die Implementierung erfolgt über eine Erweiterungsmethode in der [Activity](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)-Klasse.
Im folgenden Abschnitt ist ein Codeausschnitt zum Extrahieren von `skillId` aus Kartenaktionsdaten dargestellt:

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

### <a name="handle-interruptions"></a>Umgang mit Unterbrechungen

Virtuelle Assistenten können Unterbrechungen in Situationen behandeln, in denen ein Benutzer versucht, einen Skill aufzurufen, während gerade ein anderer Skill aktiv ist. `TeamsSkillDialog` und `TeamsSwitchSkillDialog` werden basierend auf [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs) von Bot Framework eingeführt. Sie ermöglichen es Benutzern, über Kartenaktionen zwischen Skills zu wechseln. Um diese Anforderung zu verarbeiten, fordert der virtuelle Assistent den Benutzer mit einer Bestätigungsmeldung auf, zu einem anderen Skill zu wechseln:

![Bestätigungsaufforderung beim Wechsel zu einem neuen Skill](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Behandeln von Aufgabenmodulanforderungen

Zum Hinzufügen von Aufgabenmodulfunktionen zu einem virtuellen Assistenten sind zwei zusätzliche Methoden im Aktivitätshandler für den virtuellen Assistenten enthalten: `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync`. Diese Methoden überwachen auf aufgabenmodulbezogene Aktivitäten des virtuellen Assistenten, identifizieren die mit der Anforderung verbundenen Skills und leiten die Anforderung an den identifizierten Skill weiter.

Die Anforderungsweiterleitung erfolgt über die [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true)-Methode `PostActivityAsync`. Die Antwort wird als `InvokeResponse` zurückgegeben, welches analysiert und in `TaskModuleResponse` konvertiert wird.

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

Ein ähnlicher Ansatz wird für die Weiterleitung von Kartenaktionen und Aufgabenmodulantworten verfolgt. Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird aktualisiert, um `skillId` einzuschließen.
Die Aktivitätserweiterungsmethode `GetSkillId` extrahiert `skillId` aus der Nutzlast, die Details zu dem Skill bereitstellt, der aufgerufen werden muss.

Im folgenden Abschnitt ist der Codeausschnitt für die `OnTeamsTaskModuleFetchAsync`- und `OnTeamsTaskModuleSubmitAsync`-Methoden dargestellt:

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

            return invokeResponse.GetTaskModuleResponse();
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

Darüber hinaus müssen Sie alle Skilldomänen in den `validDomains`-Abschnitt in der Manifestdatei des virtuellen Assistenten einschließen, damit Aufgabenmodule ordnungsgemäß gerendert werden.

### <a name="handle-collaborative-app-scopes"></a>Umgang mit App-Bereichen für die Zusammenarbeit

Microsoft Teams-Apps können in mehreren Bereichen genutzt werden, einschließlich 1:1-Chats, Gruppenchats und Kanälen. Die Kernvorlage des virtuellen Assistenten ist für 1:1-Chats konzipiert. Im Rahmen des Onboardings fordert der virtuelle Assistent die Benutzer zur Eingabe des Namens auf und behält den Benutzerstatus bei. Da die Onboarding nicht für Gruppenchat- oder Kanalbereiche geeignet ist, wurde es entfernt.

Skills sollten Aktivitäten in mehreren Bereichen verarbeiten, z. B. in 1:1-Chats, Gruppenchats und Kanalunterhaltungen. Wenn einer dieser Bereiche nicht unterstützt wird, müssen die Skills mit einer entsprechenden Nachricht antworten.

Die folgenden Verarbeitungsfunktionen wurden dem Kern des virtuellen Assistenten hinzugefügt:

* Der virtuelle Assistent kann ohne Textnachricht aus einem Gruppenchat oder Kanal aufgerufen werden.
* Artikulationen werden vor dem Senden der Nachricht an das Versandmodul bereinigt. Z. B. wird die erforderliche @Erwähnung des Bots entfernt.

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

### <a name="handle-message-extensions"></a>Umgang mit Nachrichtenerweiterungen

Die Befehle für eine Nachrichtenerweiterung werden in Ihrer App-Manifestdatei deklariert. Die Benutzeroberfläche der Nachrichtenerweiterung wird von diesen Befehlen unterstützt. Damit ein virtueller Assistent einen Nachrichtenerweiterungsbefehl als angefügten Skill ausführen kann, muss das Manifest des virtuellen Assistenten bereits diese Befehle enthalten. Sie müssen die Befehle aus dem Manifest eines einzelnen Skills dem Manifest des virtuellen Assistenten hinzufügen. Die Befehls-ID stellt Informationen zu einem zugeordneten Skill bereit, indem die App-ID des Skills über ein `:`-Trennzeichen angefügt wird.

Im folgenden Abschnitt ist der Codeausschnitt aus der Manifestdatei eines Skills dargestellt:

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

Im folgenden Abschnitt ist der entsprechende Codeausschnitt aus der Manifestdatei des virtuellen Assistenten dargestellt:

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

Nachdem die Befehle von einem Benutzer aufgerufen wurden, kann der virtuelle Assistent einen zugeordneten Skill durch die Analyse der Befehls-ID identifizieren, die Aktivität durch Entfernen des zusätzlichen Suffix `:<skill_id>` aus der Befehls-ID aktualisieren und an den entsprechenden Skill weiterleiten. Der Code für einen Skill muss das zusätzliche Suffix nicht verarbeiten. Somit werden Konflikte zwischen Befehls-IDs von Skills vermieden. Bei diesem Ansatz werden alle Such- und Aktionsbefehle eines Skills in allen Kontexten, z. B. **compose**, **CommandBox** und **message**, von einem virtuellen Assistenten unterstützt.

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

Einige Nachrichtenerweiterungsaktivitäten enthalten nicht die Befehls-ID. Beispielsweise enthält `composeExtension/selectItem` nur den Wert der Aktion zum Aufrufen von Tippen. Um den zugeordneten Skill zu identifizieren, wird `skillId` an jede Elementkarte angefügt, während eine Antwort für `OnTeamsMessagingExtensionQueryAsync` gebildet wird. Dies ähnelt dem Ansatz zum [Hinzufügen adaptiver Karten zu Ihrem virtuellen Assistenten](#add-adaptive-cards-to-your-virtual-assistant).

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

Das folgende Beispiel veranschaulicht, wie die App-Vorlage "Raum buchen" in einen Skill eines virtuellen Assistenten konvertiert werden kann: "Raum buchen" ist ein Microsoft Teams-Bot, mit dem Nutzer schnell einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Uhrzeit finden und reservieren können. Die Standarddauer beträgt 30 Minuten. Der "Raum buchen"-Bot ist auf persönliche bzw. 1:1-Unterhaltungen beschränkt.
Die folgende Abbildung zeigt einen virtuellen Assistenten mit einem "**Raum buchen**"-Skill:

![Virtueller Assistent mit einem "Raum buchen"-Skill](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Nachfolgend sind die Delta-Änderungen dargestellt, die eingeführt wurden, um sie in einen an einen virtuellen Assistenten angefügten Skill umzuwandeln. Ähnliche Ansätze werden befolgt, um vorhandene v4-Bots in Skills umzuwandeln.

### <a name="skill-manifest"></a>Skillmanifest

Ein Skillmanifest ist eine JSON-Datei, die den Messaging-Endpunkt, die ID, den Namen und andere relevante Metadaten eines Skills enthält. Dieses Manifest unterscheidet sich vom Manifest, das zum Querladen einer App in Microsoft Teams verwendet wird. Ein virtueller Assistent erfordert einen Pfad zu dieser Datei als Input zum Anfügen eines Skills. Wir haben das folgende Manifest zum Ordner "wwwroot" des Bots hinzugefügt.

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

### <a name="luis-integration"></a>LUIS-Integration

Das Versandmodell des virtuellen Assistenten basiert auf den LUIS-Modellen der angefügten Skills. Das Versandmodell identifiziert die Absicht für jede Textaktivität und ermittelt die damit verbundenen Skills.

Der virtuelle Assistent erfordert das LUIS-Modell eines Skills im `.lu`-Format als Input beim Anfügen eines Skills. LUIS-json wird mithilfe des Botframework-Cli-Tools in das `.lu`-Format konvertiert.

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

Der "Raum buchen"-Bot verfügt über zwei Hauptbefehle für Benutzer:

* `Book room`
* `Manage Favorites`

Wir haben ein LUIS-Modell mit Verständnis der beiden Befehle erstellt. Entsprechende geheime Schlüssel müssen in `cognitivemodels.json` aufgefüllt werden. Die entsprechende LUIS-JSON-Datei finden Sie [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json).
Die entsprechende `.lu`-Datei ist im folgenden Abschnitt dargestellt:

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

Bei diesem Ansatz wird jeder Befehl an den virtuellen Assistenten im Zusammenhang mit `book room` oder `manage favorites`, der von einem Benutzer ausgegeben wird, als ein dem `Book-a-room`-Bot zugeordneter Befehl identifiziert und an diesen Skill weitergeleitet.
Andererseits muss der `Book-a-room room`-Bot das LUIS-Modell verwenden, um diese Befehle zu verstehen, wenn sie nicht vollständig eingegeben werden. Zum Beispiel: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Unterstützung mehrerer Sprachen

Als Beispiel wird ein LUIS-Modell mit ausschließlicher Unterstützung der englischen Sprache erstellt. Sie können LUIS-Modelle für andere Sprachen erstellen und einen Eintrag zu `cognitivemodels.json` hinzufügen.

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

Fügen Sie parallel die entsprechende `.lu`-Datei im luisFolder-Pfad hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Um den `languages`-Parameter zu ändern, aktualisieren Sie den botskills-Befehl wie folgt:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Der virtuelle Assistent verwendet `SetLocaleMiddleware`, um das aktuelle Gebietsschema zu identifizieren und das entsprechende Versandmodell aufzurufen. Die Bot-Framework-Aktivitäten umfassen ein Gebietsschemafeld, das von dieser Middleware verwendet wird. Sie können dies auch für Ihre Skills verwenden. Der "Raum buchen"-Bot verwendet diese Middleware nicht und ruft das Gebietsschema stattdessen aus der [clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)-Entität der Bot-Framework-Aktivität ab.

### <a name="claim-validation"></a>Anspruchsüberprüfung

Wir haben [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) hinzugefügt, um Anrufende auf die Skills zu beschränken. Damit ein virtueller Assistent diese Skills aufrufen kann, füllen Sie das `AllowedCallers`-Array aus `appsettings` mit der App-ID dieses bestimmten virtuellen Assistenten auf.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das Array der zulässigen Aufrufer kann einschränken, welche Skills-Nutzer auf einen Skill zugreifen können. Fügen Sie diesem Array einen einzelnen Eintrag `*` hinzu, um Aufrufe von allen Skill-Nutzern anzunehmen.

```
"AllowedCallers": [ "*" ],
```

Weitere Informationen zum Hinzufügen der Anspruchsüberprüfung zu einem Skill finden Sie unter [Hinzufügen der Anspruchsüberprüfung zu Skills](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).

### <a name="limitation-of-card-refresh"></a>Einschränkung der Kartenaktualisierung

Das Aktualisieren von Aktivitäten, z. B. die Kartenaktualisierung, wird vom virtuellen Assistenten noch nicht unterstützt ([GitHub-Problem](https://github.com/microsoft/botbuilder-dotnet/issues/3686)). Daher haben wir alle `UpdateActivityAsync`-Kartenaktualisierungsaufrufe durch das Posten neuer `SendActivityAsync`-Kartenaufrufe ersetzt.

### <a name="card-actions-and-task-module-flows"></a>Kartenaktionen und Aufgabenmodulabläufe

Um Kartenaktionen oder Aufgabenmodulaktivitäten an einen zugeordneten Skill weiterzuleiten, muss der Skill in diese `skillId` einbetten.
`Book-a-room`-Botkartenaktionen, Nutzlasten für das Abrufen von Aufgabenmodulen und Übermitteln von Aktionen wurden so geändert, dass sie `skillId` als Parameter enthalten.

Weitere Informationen finden Sie in [diesem](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) Abschnitt in dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Verarbeiten von Aktivitäten aus dem Gruppenchat- oder Kanalbereich

`Book-a-room bot` ist nur für private Chats wie persönliche oder 1:1-Bereiche konzipiert. Da wir den virtuellen Assistenten angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, muss er aus den Kanalbereichen aufgerufen werden, und daher muss der `Book-a-room`-Bot Aktivitäten für denselben Bereich abrufen. Daher ist der `Book-a-room`-Bot angepasst, um diese Aktivitäten zu behandeln. Sie finden die Check-in-`OnMessageActivityAsync`-Methoden des Aktivitätshandlers des `Book-a-room`-Bots.

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

Sie können auch vorhandene Skills aus dem [Repository für Bot Framework-Lösungen](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder ganz von Grund auf einen neuen Skill erstellen. Informationen zum Erstellen eines neuen Skills finden Sie in den [Lernprogrammen zum Erstellen neuer Skills](https://microsoft.github.io/botframework-solutions/overview/skills/). Dokumentationen zur Architektur virtueller Assistenten und von Skills finden Sie unter [Architektur von virtuellen Assistenten und Skills](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).  

## <a name="limitations-of-virtual-assistant"></a>Einschränkungen von virtuellen Assistenten

* **EndOfConversation**: Ein Skill muss eine `endOfConversation`-Aktivität senden, wenn er eine Unterhaltung beendet. Basierend auf der Aktivität beendet ein virtueller Assistent den Kontext mit diesem bestimmten Skill und kehrt zum eigenen Stammkontext zurück. Für den "Raum buchen"-Bot gibt es keinen Beenden-Zustand, in dem die Unterhaltung beendet wird. Daher haben wir nicht `endOfConversation` vom `Book-a-room`-Bot gesendet, und wenn der Benutzer zum Stammkontext zurückkehren möchte, kann er dies einfach per `start over`-Befehl tun.  
* **Kartenaktualisierung**: Die Kartenaktualisierung wird vom virtuellen Assistenten noch nicht unterstützt.  
* **Nachrichtenerweiterungen**:
  * Derzeit kann ein virtueller Assistent maximal zehn Befehle für Nachrichtenerweiterungen unterstützen.
  * Die Konfiguration von Nachrichtenerweiterungen ist nicht auf einzelne Befehle beschränkt, sondern auf die gesamte Erweiterung selbst. Dadurch wird die Konfiguration für jeden einzelnen Skill durch den virtuellen Assistenten beschränkt.
  * Nachrichtenerweiterungen-Befehls-IDs haben eine maximale Länge von [64 Zeichen](../resources/schema/manifest-schema.md#composeextensions), und zum Einbetten von Skillinformationen werden 37 Zeichen verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.

Sie können auch vorhandene Skills aus dem [Repository für Bot Framework-Lösungen](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder ganz von Grund auf einen neuen Skill erstellen. Lernprogramme für später finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/). In der [Dokumentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) finden Sie Informationen zur Architektur von virtuellen Assistenten und Skills.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **C#**  **.NET** |
|----------|-----------------|---------------------------|
| Aktualisierte Visual Studio-Vorlage | Angepasste Vorlage zur Unterstützung von Microsoft Teams-Funktionen | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-virtual-assistant/csharp) |
| "Raum buchen"-Bot-Skillcode | Ermöglicht Ihnen, unterwegs schnell einen Besprechungsraum zu finden und zu buchen. | [Anzeigen](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* ["Raum buchen"](app-templates.md#app-template-code-samples)
* [Microsoft Teams-Bot](../bots/what-are-bots.md)
