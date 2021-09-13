---
title: Erstellen eines virtuellen Assistenten
description: So erstellen Sie Virtual Assistant Bot und Fähigkeiten für die Verwendung in Microsoft Teams
ms.localizationpriority: medium
ms.topic: how-to
keywords: Bots für virtuelle Teams-Assistenten
ms.openlocfilehash: 47258b55cd00452b33c09da6a5d5403ba1f0aa2c
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156268"
---
# <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten 

Virtual Assistant ist eine Open Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die volle Kontrolle über die Benutzeroberfläche, das Branding der Organisation und die erforderlichen Daten behalten können. Die [Virtual Assistant Kernvorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) ist der grundlegende Baustein, der die Microsoft-Technologien zusammenführt, die zum Erstellen eines Virtual Assistant erforderlich sind, einschließlich bot [Framework SDK,](https://github.com/microsoft/botframework-sdk) [Language Understanding (CSV)](https://www.luis.ai/)und [QnA Maker.](https://www.qnamaker.ai/) Außerdem werden die wesentlichen Funktionen wie die Registrierung von Fähigkeiten, verknüpfte Konten und die grundlegende Unterhaltungsabsicht zusammengeführt, um Benutzern eine Reihe nahtloser Interaktionen und Erfahrungen zu bieten. Darüber hinaus enthalten die Vorlagenfunktionen umfassende Beispiele für wiederverwendbare [Unterhaltungsfähigkeiten.](https://microsoft.github.io/botframework-solutions/overview/skills)  Individuelle Fähigkeiten sind in eine Virtual Assistant Lösung integriert, um mehrere Szenarien zu ermöglichen. Mithilfe des Bot Framework SDK werden Fähigkeiten in Quellcodeform dargestellt, sodass Sie sie nach Bedarf anpassen und erweitern können. Weitere Informationen zu den Fähigkeiten von Bot Framework finden Sie unter ["Was ist eine Bot Framework-Fähigkeit."](https://microsoft.github.io/botframework-solutions/overview/skills/) Dieses Dokument führt Sie zu Virtual Assistant Implementierungsüberlegungen für Organisationen, zum Erstellen eines Teams fokussierten Virtual Assistant, verwandtem Beispiel, Codebeispiel und Einschränkungen von Virtual Assistant.
In der folgenden Abbildung wird die Übersicht über den virtuellen Assistenten angezeigt:

![Übersichtsdiagramm Virtual Assistant](../assets/images/bots/virtual-assistant/overview.png)

Textnachrichtenaktivitäten werden vom Virtual Assistant Kern mithilfe eines [Versandmodells](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) an zugeordnete Fähigkeiten weitergeleitet. 

## <a name="implementation-considerations"></a>Überlegungen zur Implementierung

Die Entscheidung, eine Virtual Assistant hinzuzufügen, umfasst viele Determinanten und unterscheidet sich für jede Organisation. Die unterstützenden Faktoren einer Virtual Assistant Implementierung für Ihre Organisation sind:

* Ein zentrales Team verwaltet alle Mitarbeitererfahrungen. Es bietet die Möglichkeit, eine Virtual Assistant Erfahrung zu erstellen und Updates für die Kernerfahrung zu verwalten, einschließlich des Hinzufügens neuer Fähigkeiten.
* Es gibt mehrere Anwendungen in allen Geschäftsfunktionen, und es wird erwartet, dass die Anzahl in Zukunft wächst.
* Vorhandene Anwendungen können angepasst werden, befinden sich im Besitz der Organisation und werden in Fähigkeiten für eine Virtual Assistant umgewandelt.
* Das zentrale Team für Mitarbeitererfahrungen kann Anpassungen an vorhandenen Apps beeinflussen. Es bietet auch die erforderlichen Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in Virtual Assistant Erfahrung.

Die folgende Abbildung zeigt die Geschäftsfunktionen von Virtual Assistant: 

![Das zentrale Team verwaltet den Assistenten, und Teams für Geschäftsfunktionen bringen Fähigkeiten ein.](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines Teams-fokussierten Virtual Assistant

Microsoft hat eine [Visual Studio Vorlage](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) zum Erstellen virtueller Assistenten und Fähigkeiten veröffentlicht. Mit der vorlage Visual Studio können Sie eine Virtual Assistant erstellen, die von einer textbasierten Oberfläche mit Unterstützung für begrenzte Rich-Cards mit Aktionen unterstützt wird. Wir haben die Visual Studio Basisvorlage erweitert, um Microsoft Teams Plattformfunktionen zu integrieren und großartige Teams App-Umgebungen zu bieten. Einige der Funktionen umfassen unterstützung für umfangreiche adaptive Karten, Aufgabenmodule, Teams oder Gruppenchats und Messaging-Erweiterungen. Weitere Informationen zum Erweitern von Virtual Assistant auf Microsoft Teams finden Sie im [Lernprogramm: Erweitern Ihrer Virtual Assistant auf Microsoft Teams.](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/)    
In der folgenden Abbildung wird das allgemeine Diagramm einer Virtual Assistant Lösung angezeigt:

![Allgemeines Diagramm einer Virtual Assistant Lösung](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen adaptiver Karten zu Ihrer Virtual Assistant

Um Anforderungen ordnungsgemäß zu verteilen, muss Ihre Virtual Assistant das richtige MODELL UND die zugehörigen Fähigkeiten identifizieren. Der Verteilungsmechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das einer Fähigkeit zugeordnete MODELL VON TALENT für Kartenaktionstexte trainiert wird. Die Kartenaktionstexte sind feste, vordefinierte Schlüsselwörter und werden nicht von einem Benutzer auskommentiert.

Dieser Nachteil wurde behoben, indem Qualifikationsinformationen in die Nutzlast der Kartenaktion eingebettet werden. Jede Fähigkeit sollte in das Feld der Kartenaktionen eingebettet `skillId`  `value` werden. Sie müssen sicherstellen, dass jede Kartenaktionsaktivität die relevanten Qualifikationsinformationen enthält, und Virtual Assistant diese Informationen für die Verteilung nutzen können.

Sie müssen `skillId` im Konstruktor angeben, um sicherzustellen, dass die Qualifikationsinformationen immer in Kartenaktionen vorhanden sind.
Ein Beispielcode für Kartenaktionsdaten wird im folgenden Abschnitt gezeigt:
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

Als `SkillCardActionData` Nächstes wird die Klasse in der Virtual Assistant Vorlage eingeführt, um aus der Nutzlast der Kartenaktion zu `skillId` extrahieren.
Ein Codeausschnitt, der aus der Nutzlast der Kartenaktion extrahiert  `skillId` werden soll, wird im folgenden Abschnitt gezeigt:

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

Die Implementierung erfolgt durch eine Erweiterungsmethode in der [Activity-Klasse.](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md)
Ein Codeausschnitt zum Extrahieren  `skillId` aus Kartenaktionsdaten wird im folgenden Abschnitt gezeigt:

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

Virtual Assistant können Unterbrechungen in Fällen behandeln, in denen ein Benutzer versucht, eine Fähigkeit aufzurufen, während eine andere Fähigkeit derzeit aktiv ist. `TeamsSkillDialog`und `TeamsSwitchSkillDialog` werden basierend auf Dem [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs)von Bot Framework eingeführt. Sie ermöglichen Es Benutzern, eine Fähigkeitenerfahrung von Kartenaktionen zu wechseln. Um diese Anforderung zu verarbeiten, fordert die Virtual Assistant den Benutzer mit einer Bestätigungsmeldung auf, die Fähigkeiten zu wechseln:

![Bestätigungsaufforderung beim Umstieg auf eine neue Fähigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Behandeln von Aufgabenmodulanforderungen

Um einem Virtual Assistant Aufgabenmodulfunktionen hinzuzufügen, sind zwei zusätzliche Methoden im Virtual Assistant-Aktivitätshandler enthalten: `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` . Diese Methoden hören aufgabenmodulbezogene Aktivitäten von Virtual Assistant ab, identifizieren die mit der Anforderung verknüpften Fähigkeiten und leiten die Anforderung an die identifizierte Fähigkeit weiter. 

Die Anforderungsweiterleitung erfolgt über die [SkillHttpClient](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true) `PostActivityAsync` -Methode. Es gibt die Antwort zurück, wie `InvokeResponse` sie analysiert und in konvertiert `TaskModuleResponse` wird.


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

Ein ähnlicher Ansatz wird für Die Verteilung von Kartenaktionen und Aufgabenmodulantworten befolgt. Das Abrufen und Übermitteln von Aktionsdaten des Aufgabenmoduls wird aktualisiert, um die Daten einzuschließen. `skillId` Activity Extension-Methode `GetSkillId` extrahiert `skillId` aus der Nutzlast, die Details zu den Fähigkeiten bereitstellt, die aufgerufen werden müssen.

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

Darüber hinaus müssen Sie alle Qualifikationsdomänen in den Abschnitt in die `validDomains` Manifestdatei Virtual Assistant einschließen, damit aufgabenmodule, die über eine Fähigkeit aufgerufen werden, ordnungsgemäß gerendert werden.

### <a name="handle-collaborative-app-scopes"></a>Behandeln von App-Bereichen für die Zusammenarbeit

Teams Apps können in mehreren Bereichen vorhanden sein, einschließlich 1:1-Chat, Gruppenchat und Kanälen. Die haupt Virtual Assistant Vorlage ist für 1:1-Chats konzipiert. Im Rahmen der Onboarding-Erfahrung werden Benutzer Virtual Assistant aufgefordert, den Namen einzufordern und den Benutzerstatus zu verwalten. Da diese Onboarding-Erfahrung nicht für Gruppenchat- oder Kanalbereiche geeignet ist, wurde sie entfernt.

Fähigkeiten sollten Aktivitäten in mehreren Bereichen verarbeiten, z. B. 1:1-Chat, Gruppenchat und Kanalunterhaltung. Wenn einer dieser Bereiche nicht unterstützt wird, müssen Die Fähigkeiten mit einer entsprechenden Nachricht antworten.

Die folgenden Verarbeitungsfunktionen wurden Virtual Assistant Core hinzugefügt:

* Virtual Assistant kann ohne Textnachricht aus einem Gruppenchat oder -kanal aufgerufen werden.
* Artikulationen werden vor dem Senden der Nachricht an das Verteilermodul bereinigt. Entfernen Sie beispielsweise die erforderlichen @mention des Bots.

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

### <a name="handle-messaging-extensions"></a>Behandeln von Messaging-Erweiterungen

Die Befehle für eine Messaging-Erweiterung werden in ihrer App-Manifestdatei deklariert. Die Benutzeroberfläche der Messaging-Erweiterung wird von diesen Befehlen unterstützt. Damit ein Virtual Assistant einen Messaging-Erweiterungsbefehl als angefügte Fähigkeit unterstützen kann, muss das manifest einer Virtual Assistant diese Befehle enthalten. Sie müssen die Befehle aus dem Manifest einer bestimmten Fähigkeit zum Manifest der Virtual Assistant hinzufügen. Die Befehls-ID stellt Informationen zu einer zugeordneten Fähigkeit bereit, indem die App-ID der Fähigkeit durch ein Trennzeichen angefügt `:` wird.

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

Der entsprechende Virtual Assistant Codeausschnitt der Manifestdatei wird im folgenden Abschnitt gezeigt:

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

Nachdem die Befehle von einem Benutzer aufgerufen wurden, kann der Virtual Assistant eine zugeordnete Fähigkeit identifizieren, indem er die Befehls-ID analysiert, die Aktivität aktualisiert, indem das zusätzliche Suffix `:<skill_id>` aus der Befehls-ID entfernt und an die entsprechende Fähigkeit weitergeleitet wird. Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht behandeln. Daher werden Konflikte zwischen Befehls-IDs über Fähigkeiten hinweg vermieden. Bei diesem Ansatz werden alle Such- und Aktionsbefehle einer Fähigkeit in allen Kontexten, **z. B. Verfassen,** **CommandBox** und **Nachricht,** von einem Virtual Assistant unterstützt.

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

Einige Messaging-Erweiterungsaktivitäten enthalten nicht die Befehls-ID. Enthält z. `composeExtension/selectItem` B. nur den Wert der Aktion "Tippen aufrufen". Um die zugeordnete Fähigkeit zu identifizieren, `skillId`  wird an jede Elementkarte angefügt, während eine Antwort für `OnTeamsMessagingExtensionQueryAsync` erstellt wird. Dies ähnelt dem Ansatz zum [Hinzufügen adaptiver Karten zu Ihrem Virtual Assistant.](#add-adaptive-cards-to-your-virtual-assistant)

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

Das folgende Beispiel zeigt, wie Sie die Vorlage "Book-a-room"-App in eine Virtual Assistant Fähigkeit konvertieren: "Book-a-room" ist ein Microsoft Teams, mit dem Benutzer schnell einen Besprechungsraum für 30, 60 oder 90 Minuten ab der aktuellen Zeit suchen und reservieren können. Die Standardzeit beträgt 30 Minuten. Der Book-a-Room-Bot umfasst persönliche oder 1:1-Unterhaltungen. In der folgenden Abbildung wird ein Virtual Assistant mit einem Buch mit **Raumkenntnissen** angezeigt:

![Virtual Assistant mit einer Fähigkeit zum "Reservieren eines Raumes"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Nachfolgend sind die Deltaänderungen aufgeführt, die eingeführt wurden, um sie in eine Fähigkeit umzuwandeln, die einem Virtual Assistant zugeordnet ist. Ähnliche Richtlinien werden befolgt, um einen vorhandenen v4-Bot in eine Fähigkeit zu konvertieren.

### <a name="skill-manifest"></a>Skill-Manifest

Ein Fähigkeitsmanifest ist eine JSON-Datei, die den Messaging-Endpunkt, die ID, den Namen und andere relevante Metadaten einer Fähigkeit verfügbar macht. Dieses Manifest unterscheidet sich von dem Manifest, das zum Querladen einer App in Microsoft Teams verwendet wird. Ein Virtual Assistant erfordert einen Pfad zu dieser Datei als Eingabe, um eine Fähigkeit anzufügen. Wir haben das folgende Manifest zum Wwwroot-Ordner des Bots hinzugefügt.

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

### <a name="luis-integration"></a>INTEGRAL-Integration

das Verteilermodell Virtual Assistant basiert auf den MODELS-Modellen der angefügten Fähigkeiten. Das Verteilermodell identifiziert die Absicht für jede Textaktivität und ermittelt die damit verbundenen Fähigkeiten.

Virtual Assistant erfordert das SKILL-Modell im `.lu` Format als Eingabe beim Anfügen einer Fähigkeit. JSON JSON wird `.lu` mithilfe des Botframework-Cli-Tools in das Format konvertiert.

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

Wir haben ein XAML-Modell erstellt, indem wir diese beiden Befehle verstanden haben. Entsprechende geheime Schlüssel müssen in aufgefüllt `cognitivemodels.json` werden. Die entsprechende CSV JSON-Datei finden Sie [hier.](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json)
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

Bei diesem Ansatz wird jeder Befehl, der von einem Benutzer ausgegeben wird, um zu Virtual Assistant, der `book room` mit einem Bot verknüpft ist, oder als `manage favorites` befehlsbezogen identifiziert `Book-a-room` und an diese Fähigkeit weitergeleitet.
Auf der anderen Seite `Book-a-room room` muss bot DAS MODELL VERWENDEN, um diese Befehle zu verstehen, wenn sie nicht vollständig eingegeben wurden. Beispiel: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Mehrsprachige Unterstützung

Als Beispiel wird ein MODELL MIT NUR englischer Kultur erstellt. You can create CSV models corresponding to other languages and add entry to `cognitivemodels.json` .

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

Fügen Sie parallel dazu die entsprechende `.lu` Datei im pfadgeschützten Ordner hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Aktualisieren Sie zum Ändern des `languages` Parameters den Befehl "botskills" wie folgt:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Virtual Assistant `SetLocaleMiddleware` verwendet, um das aktuelle Gebietsschema zu identifizieren und das entsprechende Verteilermodell aufzurufen. Bot-Framework-Aktivität verfügt über ein Gebietsschemafeld, das von dieser Middleware verwendet wird. Sie können dies auch für Ihre Fähigkeiten verwenden. Book-a-room-Bot verwendet diese Middleware nicht und ruft stattdessen das Gebietsschema aus der [ClientInfo-Entität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo)der Bot-Framework-Aktivität ab.

### <a name="claim-validation"></a>Anspruchsüberprüfung

Wir haben [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) hinzugefügt, um Aufrufer auf die Fähigkeit zu beschränken. Damit ein Virtual Assistant diese Fähigkeit aufrufen kann, füllen Sie das Array mit der `AllowedCallers` `appsettings` App-ID dieses bestimmten Virtual Assistant auf.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das Array der zulässigen Aufrufer kann einschränken, welche Fähigkeiten Verbraucher auf die Fähigkeit zugreifen können. Fügen Sie diesem Array einen einzelnen Eintrag `*` hinzu, um Anrufe von einem beliebigen Skill Consumer zu akzeptieren.

```
"AllowedCallers": [ "*" ],
```

Weitere Informationen zum Hinzufügen einer Anspruchsüberprüfung zu einer Fähigkeit finden Sie unter Hinzufügen der [Anspruchsüberprüfung zu den Fähigkeiten.](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true)

### <a name="limitation-of-card-refresh"></a>Einschränkung der Kartenaktualisierung 

Das Aktualisieren von Aktivitäten, z. B. die Kartenaktualisierung, wird noch nicht über Virtual Assistant ([GitHub-Problem)](https://github.com/microsoft/botbuilder-dotnet/issues/3686)unterstützt. Daher haben wir alle Kartenaktualisierungsanrufe `UpdateActivityAsync` durch die Veröffentlichung neuer Kartenanrufe `SendActivityAsync` ersetzt.

### <a name="card-actions-and-task-module-flows"></a>Kartenaktionen und Aufgabenmodulflüsse

Um Kartenaktions- oder Aufgabenmodulaktivitäten an eine zugeordnete Fähigkeit weiterzuleiten, muss die Fähigkeit darin eingebettet `skillId` werden.
`Book-a-room` bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter. 

Weitere Informationen finden Sie in [diesem](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) Abschnitt in dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Behandeln von Aktivitäten aus dem Gruppenchat- oder Kanalbereich

`Book-a-room bot` ist für private Chats vorgesehen, z. B. nur für persönliche Chats oder 1:1-Bereiche. Da wir Virtual Assistant angepasst haben, um Gruppenchats und Kanalbereiche zu unterstützen, muss die Virtual Assistant aus den Kanalbereichen aufgerufen werden. Daher `Book-a-room` muss der Bot Aktivitäten für denselben Bereich abrufen. Daher `Book-a-room` ist Bot so angepasst, dass er diese Aktivitäten verarbeitet. Sie finden die `OnMessageActivityAsync` Eincheckmethoden des `Book-a-room` Bot-Aktivitätshandlers.

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

Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework-Lösungs-Repository](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder eine neue Fertigkeit von Grund auf neu erstellen. Informationen zum Erstellen einer neuen Fähigkeit finden Sie in [Lernprogrammen zum Erstellen einer neuen Fähigkeit.](https://microsoft.github.io/botframework-solutions/overview/skills/) Virtual Assistant und Dokumentation zur Architektur von Fähigkeiten finden Sie unter[Virtual Assistant- und Kompetenzarchitektur.](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true)  

## <a name="limitations-of-virtual-assistant"></a>Einschränkungen von Virtual Assistant 

* **EndOfConversation:** Eine Fähigkeit muss eine `endOfConversation` Aktivität senden, wenn sie eine Unterhaltung beendet. Basierend auf der Aktivität beendet ein Virtual Assistant den Kontext mit dieser bestimmten Fähigkeit und geht zurück in den Stammkontext Virtual Assistant. Für Book-a-Room-Bots gibt es keinen eindeutigen Zustand, in dem die Unterhaltung beendet wird. Daher haben wir nicht `endOfConversation` vom `Book-a-room` Bot gesendet, und wenn der Benutzer zum Stammkontext zurückkehren möchte, kann er dies einfach per `start over` Befehl tun.  
* **Kartenaktualisierung:** Die Kartenaktualisierung wird noch nicht über Virtual Assistant unterstützt.  
* **Messaging-Erweiterungen:**
  * Derzeit kann ein Virtual Assistant maximal zehn Befehle für Messaging-Erweiterungen unterstützen.
  * Die Konfiguration von Messaging-Erweiterungen ist nicht auf einzelne Befehle beschränkt, sondern auf die gesamte Erweiterung selbst. Dadurch wird die Konfiguration für jede einzelne Fähigkeit durch Virtual Assistant beschränkt.
  * Befehls-IDs für Messaging-Erweiterungen haben eine maximale Länge von [64 Zeichen](../resources/schema/manifest-schema.md#composeextensions) und 37 Zeichen werden zum Einbetten von Informationen zu Fähigkeiten verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.

Sie können auch vorhandene Fähigkeiten aus dem [Bot Framework-Lösungs-Repository](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder eine neue Fertigkeit von Grund auf neu erstellen. Lernprogramme für das spätere Finden Sie [hier.](https://microsoft.github.io/botframework-solutions/overview/skills/) Informationen zur Architektur von Virtual Assistant und Fähigkeiten finden Sie in der [Dokumentation.](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true)

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **C#**  **.NET** |
|----------|-----------------|---------------------------|
| Visual Studio-Vorlage aktualisiert | Angepasste Vorlage zur Unterstützung von Teams-Funktionen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-virtual-assistant/csharp) |
| Book-a-Room-Bot–Fähigkeitscode | Ermöglicht ihnen, einen Besprechungsraum unterwegs schnell zu finden und zu reservieren. | [Anzeigen](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |


## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Book-a-room](app-templates.md#book-a-room)
* [Microsoft Teams Bot](../bots/what-are-bots.md)
