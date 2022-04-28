---
title: Erstellen eines virtuellen Assistenten
description: Erfahren Sie, wie Sie Virtual Assistant Bot für Microsoft Teams erstellen, indem Sie Codebeispiele und Codeausschnitte mit Features wie adaptive Karten verwenden, Unterbrechungen, Aufgabenmodulanforderungen, App-Bereiche für die Zusammenarbeit und Nachrichtenerweiterungen behandeln; mithilfe von Fähigkeitenmanifest; Unterstützung für mehrere Sprachen, Anspruchsüberprüfung, LUIS-Integration und Modus.
ms.localizationpriority: medium
ms.topic: how-to
keywords: Virtuelle Assistenten-Bots für Teams
ms.openlocfilehash: e473fd8166be6285ec90d78401b1df028d81b5b0
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104105"
---
# <a name="create-virtual-assistant"></a>Erstellen eines virtuellen Assistenten

Virtual Assistant ist eine Open-Source-Vorlage von Microsoft, mit der Sie eine stabile Unterhaltungslösung erstellen und gleichzeitig die volle Kontrolle über die Benutzererfahrung, das Branding der Organisation und die erforderlichen Daten behalten. Die [Virtual Assistant Kernvorlage](https://microsoft.github.io/botframework-solutions/overview/virtual-assistant-template) ist der grundlegende Baustein, der die Microsoft-Technologien vereint, die zum Erstellen eines Virtual Assistant erforderlich sind, einschließlich Bot [Framework SDK](https://github.com/microsoft/botframework-sdk), [Language Understanding (LUIS)](https://www.luis.ai/) und [QnA Maker](https://www.qnamaker.ai/). Es vereint auch die wesentlichen Funktionen wie die Registrierung von Fähigkeiten, verknüpfte Konten, grundlegende Unterhaltungsabsichten, um Benutzern eine Reihe nahtloser Interaktionen und Erfahrungen zu bieten. Darüber hinaus enthalten die Vorlagenfunktionen umfangreiche Beispiele für wiederverwendbare [Unterhaltungsfertigkeiten](https://microsoft.github.io/botframework-solutions/overview/skills).  Individuelle Fähigkeiten sind in eine Virtual Assistant Lösung integriert, um mehrere Szenarien zu ermöglichen. Mithilfe des Bot Framework SDK werden Die Fähigkeiten in Quellcodeform dargestellt, sodass Sie die Erforderlichen anpassen und erweitern können. Weitere Informationen zu den Fähigkeiten von Bot Framework finden Sie unter ["Was ist eine Bot-Framework-Fähigkeit](https://microsoft.github.io/botframework-solutions/overview/skills/)". Dieses Dokument enthält Anleitungen zu Virtual Assistant Implementierungsüberlegungen für Organisationen, zum Erstellen einer Teams fokussierten Virtual Assistant, zu verwandten Beispielen, Codebeispielen und Einschränkungen von Virtual Assistant.
Die folgende Abbildung zeigt die Übersicht über den virtuellen Assistenten:

![Virtual Assistant Übersichtsdiagramm](../assets/images/bots/virtual-assistant/overview.png)

Textnachrichtenaktivitäten werden vom Virtual Assistant Kern mithilfe eines [Versandmodells](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) an die zugehörigen Fähigkeiten weitergeleitet.

## <a name="implementation-considerations"></a>Überlegungen zur Implementierung

Die Entscheidung zum Hinzufügen eines Virtual Assistant umfasst viele Determinanten und unterscheidet sich für jede Organisation. Die unterstützenden Faktoren einer Virtual Assistant Implementierung für Ihre Organisation sind die folgenden:

* Ein zentrales Team verwaltet alle Mitarbeitererfahrungen. Es hat die Möglichkeit, eine Virtual Assistant Erfahrung zu erstellen und Updates für die Kernerfahrung einschließlich der Hinzufügung neuer Fähigkeiten zu verwalten.
* Es gibt mehrere Anwendungen in allen Geschäftsfunktionen, und die Anzahl wird in Zukunft voraussichtlich zunehmen.
* Vorhandene Anwendungen können angepasst werden, gehören der Organisation und werden in Fähigkeiten für eine Virtual Assistant konvertiert.
* Das zentrale Mitarbeitererfahrungsteam kann Anpassungen an vorhandenen Apps beeinflussen. Es bietet auch die erforderlichen Anleitungen für die Integration vorhandener Anwendungen als Fähigkeiten in Virtual Assistant Erfahrung.

In der folgenden Abbildung werden die Geschäftsfunktionen von Virtual Assistant angezeigt:

![Zentrales Team verwaltet den Assistenten, und Geschäftsfunktionsteams tragen Fähigkeiten bei](../assets/images/bots/virtual-assistant/business-functions.png)

## <a name="create-a-teams-focused-virtual-assistant"></a>Erstellen eines Teams-fokussierten Virtual Assistant

Microsoft hat eine [Microsoft Visual Studio Vorlage](https://marketplace.visualstudio.com/items?itemName=BotBuilder.VirtualAssistantTemplate) zum Erstellen von virtuellen Assistenten und Fähigkeiten veröffentlicht. Mit der Visual Studio Vorlage können Sie eine Virtual Assistant erstellen, die von einer textbasierten Erfahrung mit Unterstützung für eingeschränkte Rich-Karten mit Aktionen unterstützt wird. Wir haben die Visual Studio Basisvorlage um Microsoft Teams Plattformfunktionen erweitert und bieten eine hervorragende Teams App-Erfahrung. Einige der Funktionen umfassen Unterstützung für umfangreiche adaptive Karten, Aufgabenmodule, Teams oder Gruppenchats und Nachrichtenerweiterungen. Weitere Informationen zum Erweitern von Virtual Assistant auf Microsoft Teams finden Sie im [Lernprogramm: Erweitern Ihres Virtual Assistant auf Microsoft Teams](https://microsoft.github.io/botframework-solutions/clients-and-channels/tutorials/enable-teams/1-intro/).
Die folgende Abbildung zeigt das allgemeine Diagramm einer Virtual Assistant Lösung:

![Allgemeines Diagramm einer Virtual Assistant Lösung](../assets/images/bots/virtual-assistant/high-level-diagram.png)

### <a name="add-adaptive-cards-to-your-virtual-assistant"></a>Hinzufügen adaptiver Karten zu Ihrem Virtual Assistant

Um Anforderungen ordnungsgemäß zu versenden, muss Ihr Virtual Assistant das richtige LUIS-Modell und die zugehörigen Fähigkeiten identifizieren. Der Versandmechanismus kann jedoch nicht für Kartenaktionsaktivitäten verwendet werden, da das LUIS-Modell, das einer Fähigkeit zugeordnet ist, für Kartenaktionstexte trainiert wird. Die Aktionstexte der Karte sind feste, vordefinierte Schlüsselwörter und werden nicht von einem Benutzer kommentiert.

Dieser Nachteil wird behoben, indem Qualifikationsinformationen in die Nutzlast der Kartenaktion eingebettet werden. Jede Fähigkeit sollte in das Feld der `value` Kartenaktionen eingebettet `skillId` werden. Sie müssen sicherstellen, dass jede Aktionsaktivität der Karte die relevanten Qualifikationsinformationen enthält, und Virtual Assistant diese Informationen für die Versendung nutzen können.

Sie müssen im Konstruktor bereitstellen `skillId` , um sicherzustellen, dass die Qualifikationsinformationen immer in Kartenaktionen vorhanden sind.
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

Als Nächstes wird die Klasse in der vorlage Virtual Assistant eingeführt, `SkillCardActionData` um die Nutzlast der Kartenaktion zu extrahieren`skillId`.
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

Die Implementierung erfolgt über eine Erweiterungsmethode in der [Activity-Klasse](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md) .
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

Virtual Assistant können Unterbrechungen in Fällen behandeln, in denen ein Benutzer versucht, eine Fertigkeit aufzurufen, während eine andere Fähigkeit derzeit aktiv ist. `TeamsSkillDialog``TeamsSwitchSkillDialog`und werden basierend auf Dem [SkillDialog](https://github.com/microsoft/botframework-solutions/blob/5b46d73e220bbb4fba86c48be532e495535ca78a/sdk/csharp/libraries/microsoft.bot.solutions/Skills/SkillDialog.cs) und [SwitchSkillDialog](https://github.com/microsoft/botframework-solutions/blob/6d40fa8ae05f96b0c5e0464e01361a9e1deb696c/sdk/csharp/libraries/microsoft.bot.solutions/Skills/Dialogs/SwitchSkillDialog.cs) von Bot Framework eingeführt. Sie ermöglichen es Benutzern, eine Qualifikationserfahrung von Kartenaktionen zu wechseln. Um diese Anforderung zu verarbeiten, fordert die Virtual Assistant den Benutzer mit einer Bestätigungsmeldung auf, die Fähigkeiten zu wechseln:

![Bestätigungsaufforderung beim Wechseln zu einer neuen Fertigkeit](../assets/images/bots/virtual-assistant/switch-skills-prompt.png)

### <a name="handle-task-module-requests"></a>Behandeln von Aufgabenmodulanforderungen

Zum Hinzufügen von Aufgabenmodulfunktionen zu einem Virtual Assistant sind zwei zusätzliche Methoden im Virtual Assistant-Aktivitätshandler enthalten: `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync`. Diese Methoden lauschen auf aufgabenmodulbezogene Aktivitäten von Virtual Assistant, identifizieren die mit der Anforderung verbundenen Fähigkeiten und leiten die Anforderung an die identifizierte Qualifikation weiter.

Die Anforderungsweiterleitung erfolgt über die [SkillHttpClient-Methode](/dotnet/api/microsoft.bot.builder.integration.aspnet.core.skills.skillhttpclient?view=botbuilder-dotnet-stable&preserve-view=true)`PostActivityAsync`. Es gibt die Antwort zurück, wie `InvokeResponse` sie analysiert und in konvertiert `TaskModuleResponse` wird.

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

Ein ähnlicher Ansatz wird für die Verteilerung von Kartenaktionen und Aufgabenmodulantworten verfolgt. Aufgabenmodul Abrufen und Senden von Aktionsdaten wird aktualisiert, um einzuschließen `skillId`.
Die Aktivitätserweiterungsmethode `GetSkillId` `skillId` extrahiert aus der Nutzlast, die Details zu der Fähigkeit bereitstellt, die aufgerufen werden muss.

Der Codeausschnitt für `OnTeamsTaskModuleFetchAsync` und `OnTeamsTaskModuleSubmitAsync` die Methoden sind im folgenden Abschnitt aufgeführt:

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

Darüber hinaus müssen Sie alle Qualifikationsdomänen in den Abschnitt in der `validDomains` Manifestdatei von Virtual Assistant einschließen, damit Aufgabenmodule ordnungsgemäß gerendert werden.

### <a name="handle-collaborative-app-scopes"></a>Behandeln von App-Bereichen für die Zusammenarbeit

Teams Apps können in mehreren Bereichen vorhanden sein, einschließlich 1:1-Chat, Gruppenchat und Kanälen. Die Kernvorlage Virtual Assistant ist für 1:1-Chats konzipiert. Im Rahmen der Onboarding-Erfahrung fordert Virtual Assistant Benutzer zur Eingabe von Namen auf und behält den Benutzerstatus bei. Da die Onboarding-Erfahrung nicht für Gruppenchat- oder Kanalbereiche geeignet ist, wurde sie entfernt.

Fähigkeiten sollten Aktivitäten in mehreren Bereichen behandeln, z. B. 1:1-Chat, Gruppenchat und Kanalunterhaltung. Wenn einer dieser Bereiche nicht unterstützt wird, müssen Die Fähigkeiten mit einer entsprechenden Nachricht antworten.

Die folgenden Verarbeitungsfunktionen wurden Virtual Assistant Kern hinzugefügt:

* Virtual Assistant können ohne Textnachricht aus einem Gruppenchat oder Kanal aufgerufen werden.
* Artikulationen werden vor dem Senden der Nachricht an das Versandmodul bereinigt. Entfernen Sie z. B. die erforderlichen @mention des Bots.

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

### <a name="handle-message-extensions"></a>Behandeln von Nachrichtenerweiterungen

Die Befehle für eine Nachrichtenerweiterung werden in Ihrer App-Manifestdatei deklariert. Die Benutzeroberfläche der Nachrichtenerweiterung wird von diesen Befehlen unterstützt. Damit ein Virtual Assistant einen Befehl für die Nachrichtenerweiterung als angefügte Fähigkeit ausführen kann, muss das manifest eines Virtual Assistant diese Befehle enthalten. Sie müssen die Befehle aus dem Manifest einer einzelnen Fertigkeit dem Manifest des Virtual Assistant hinzufügen. Die Befehls-ID stellt Informationen zu einer zugeordneten Fertigkeit bereit, indem die App-ID der Fertigkeit über ein Trennzeichen angefügt wird `:`.

Der Codeausschnitt aus der Manifestdatei einer Fertigkeit wird im folgenden Abschnitt angezeigt:

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

Der entsprechende Codeausschnitt Virtual Assistant Manifestdatei wird im folgenden Abschnitt gezeigt:

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

Nachdem die Befehle von einem Benutzer aufgerufen wurden, kann der Virtual Assistant eine zugeordnete Fertigkeit identifizieren, indem er die Befehls-ID analysiert, die Aktivität aktualisiert, indem er das zusätzliche Suffix `:<skill_id>` aus der Befehls-ID entfernt und an die entsprechende Fähigkeit weiterleitet. Der Code für eine Fertigkeit muss das zusätzliche Suffix nicht verarbeiten. Somit werden Konflikte zwischen Befehls-IDs über Fähigkeiten hinweg vermieden. Bei diesem Ansatz werden alle Such- und Aktionsbefehle einer Fähigkeit in allen Kontexten, z. B. **Verfassen**, **CommandBox** und **Nachricht**, von einem Virtual Assistant unterstützt.

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

Einige Nachrichtenerweiterungsaktivitäten enthalten nicht die Befehls-ID. Enthält z. B `composeExtension/selectItem` . nur den Wert der Aufruf-Tippaktion. Um die zugeordnete Fähigkeit zu identifizieren, wird jeder Elementkarte angefügt, `skillId`  während eine Antwort für `OnTeamsMessagingExtensionQueryAsync`gebildet wird. Dies ähnelt dem Ansatz zum [Hinzufügen adaptiver Karten zu Ihrer Virtual Assistant](#add-adaptive-cards-to-your-virtual-assistant).

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

Das folgende Beispiel zeigt, wie Sie die App-Vorlage "Book-a-room" in eine Virtual Assistant Fähigkeit konvertieren: "Book-a-room" ist eine Microsoft Teams, mit der Benutzer einen Besprechungsraum ab der aktuellen Zeit schnell für 30, 60 oder 90 Minuten finden und reservieren können. Die Standardzeit beträgt 30 Minuten. Der Book-a-room-Bot begibt sich auf persönliche oder 1:1-Unterhaltungen.
Die folgende Abbildung zeigt eine Virtual Assistant mit einem **Buch mit einer Raumfertigkeit**:

![Virtual Assistant mit einer Fähigkeit zum "Buchen eines Raums"](../assets/images/bots/virtual-assistant/book-a-room-skill.png)

Nachfolgend sind die Delta-Änderungen dargestellt, die eingeführt wurden, um sie in eine Fertigkeit umzuwandeln, die an eine Virtual Assistant angefügt ist. Ähnliche Richtlinien werden befolgt, um vorhandene v4-Bots in eine Fertigkeit umzuwandeln.

### <a name="skill-manifest"></a>Qualifikationsmanifest

Ein Qualifikationsmanifest ist eine JSON-Datei, die den Messaging-Endpunkt, die ID, den Namen und andere relevante Metadaten einer Qualifikation verfügbar macht. Dieses Manifest unterscheidet sich vom Manifest, das zum Querladen einer App in Microsoft Teams verwendet wird. Ein Virtual Assistant erfordert einen Pfad zu dieser Datei als Eingabe, um eine Fertigkeit anzufügen. Wir haben das folgende Manifest zum Ordner "wwwroot" des Bots hinzugefügt.

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

das Versandmodell von Virtual Assistant basiert auf den LUIS-Modellen der angefügten Fähigkeiten. Das Versandmodell identifiziert die Absicht für jede Textaktivität und ermittelt die damit verbundenen Fähigkeiten.

Virtual Assistant erfordert das LUIS-Modell von Skill im `.lu` Format als Eingabe beim Anfügen einer Fähigkeit. LUIS json wird mithilfe des Botframework-Cli-Tools in ein Format konvertiert `.lu` .

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to the folder containing your Skill's .lu files>" --languages "en-us" --cs
```

```bash
npm i -g @microsoft/botframework-cli
bf luis:convert --in <pathToLUIS.json> --out <pathToLuFile>
```

Der Book-a-Room-Bot verfügt über zwei Hauptbefehle für Benutzer:

* `Book room`
* `Manage Favorites`

Wir haben ein LUIS-Modell erstellt, indem wir diese beiden Befehle verstehen. Entsprechende geheime Schlüssel müssen in `cognitivemodels.json`aufgefüllt werden. Die entsprechende LUIS JSON-Datei finden Sie [hier](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/blob/nebhagat/microsoft-teams-apps-bookaroom-skill/Deployment/Resources/LU/en-us/book-a-meeting.json).
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

Bei diesem Ansatz wird jeder Befehl, der von einem Benutzer ausgegeben wird, um Virtual Assistant im Zusammenhang mit `book room` bot zugeordneten Befehl zu Virtual Assistant, oder `manage favorites` als ein Befehl identifiziert, der dem `Book-a-room` Bot zugeordnet ist, und an diese Fähigkeit weitergeleitet.
Andererseits muss der Bot das LUIS-Modell verwenden, `Book-a-room room` um diese Befehle zu verstehen, wenn sie nicht vollständig eingegeben werden. Zum Beispiel: `I want to manage my favorite rooms`.

### <a name="multi-language-support"></a>Unterstützung für mehrere Sprachen

Als Beispiel wird ein LUIS-Modell mit nur englischer Kultur erstellt. Sie können LUIS-Modelle erstellen, die anderen Sprachen entsprechen, und Eintrag zu `cognitivemodels.json`hinzufügen.

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

Fügen Sie parallel die entsprechende `.lu` Datei im luisFolder-Pfad hinzu. Die Ordnerstruktur sollte wie folgt aussehen:

```bash
| - luisFolder

        | - en-us

                | - book-a-meeting.lu

        | - your_language_culture

                | - book-a-meeting.lu
```

Um den Parameter zu ändern `languages` , aktualisieren Sie den Botskills-Befehl wie folgt:

```json
botskills connect --remoteManifest "<url to skill's manifest>" --luisFolder "<path to luisFolder>" --languages "en-us, your_language_culture" --cs
```

Virtual Assistant verwendet`SetLocaleMiddleware`, um das aktuelle Gebietsschema zu identifizieren und das entsprechende Versandmodell aufzurufen. Die Bot-Framework-Aktivität verfügt über ein Gebietsschemafeld, das von dieser Middleware verwendet wird. Sie können das gleiche auch für Ihre Fähigkeiten verwenden. Der Book-a-Room-Bot verwendet diese Middleware nicht und erhält stattdessen gebietsschema aus der [ClientInfo-Entität der Bot-Framework-Aktivität](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).

### <a name="claim-validation"></a>Anspruchsüberprüfung

Wir haben [claimsValidator](https://github.com/nebhagat/msteams-virtual-assistant-dotnet/blob/master/msteams-virtual-assistant-dotnet/Authentication/AllowedCallersClaimsValidator.cs) hinzugefügt, um Anrufer auf die Fähigkeit zu beschränken. Damit ein Virtual Assistant diese Fähigkeit aufrufen kann, füllen Sie `AllowedCallers` das Array mit der App-ID dieses bestimmten Virtual Assistant auf`appsettings`.

```
"AllowedCallers": [ "<caller_VA1_appId>", "<caller_VA2_appId>" ],
```

Das Array der zulässigen Anrufer kann einschränken, welche Fähigkeitskunden auf die Fähigkeit zugreifen können. Fügen Sie diesem Array einen einzelnen Eintrag `*` hinzu, um Anrufe von jedem Skill-Consumer anzunehmen.

```
"AllowedCallers": [ "*" ],
```

Weitere Informationen zum Hinzufügen der Anspruchsüberprüfung zu einer Qualifikation finden [Sie unter Hinzufügen der Anspruchsüberprüfung zu Fähigkeiten](/azure/bot-service/skill-implement-skill?view=azure-bot-service-4.0&tabs=cs#claims-validator&preserve-view=true).

### <a name="limitation-of-card-refresh"></a>Einschränkung der Kartenaktualisierung

Das Aktualisieren von Aktivitäten, z. B. die Kartenaktualisierung, wird noch nicht durch Virtual Assistant ([GitHub-Problem](https://github.com/microsoft/botbuilder-dotnet/issues/3686)) unterstützt. Daher haben wir alle Kartenaktualisierungsaufrufe `UpdateActivityAsync` durch das Posten neuer Kartenanrufe `SendActivityAsync`ersetzt.

### <a name="card-actions-and-task-module-flows"></a>Kartenaktionen und Aufgabenmodulflüsse

Um Kartenaktionen oder Aufgabenmodulaktivitäten an eine zugeordnete Fähigkeit weiterzuleiten, muss die Fähigkeit in diese eingebettet werden `skillId` .
`Book-a-room` Bot card action, task module fetch and submit action payloads are modified to contain `skillId` as a parameter.

Weitere Informationen finden Sie in [diesem](/microsoftteams/platform/samples/virtual-assistant#add-adaptive-cards-to-your-virtual-assistant) Abschnitt aus dieser Dokumentation.

### <a name="handle-activities-from-group-chat-or-channel-scope"></a>Behandeln von Aktivitäten aus dem Gruppenchat- oder Kanalbereich

`Book-a-room bot` ist nur für private Chats wie persönliche Chats oder 1:1-Bereiche konzipiert. Da wir Virtual Assistant angepasst haben, um Gruppenchat- und Kanalbereiche zu unterstützen, muss die Virtual Assistant aus den Kanalbereichen aufgerufen werden, `Book-a-room` und daher muss der Bot Aktivitäten für denselben Bereich abrufen. Daher `Book-a-room`ist bot angepasst, um diese Aktivitäten zu behandeln. Sie finden die Check-in-Methoden `OnMessageActivityAsync` des Aktivitätshandlers des `Book-a-room` Bots.

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

Sie können auch vorhandene Fähigkeiten aus dem [Repository für Bot Framework-Lösungen](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder ganz von Grund auf eine neue Fertigkeit erstellen. Informationen zum Erstellen einer neuen Fertigkeit finden Sie in [den Lernprogrammen zum Erstellen einer neuen Fertigkeit](https://microsoft.github.io/botframework-solutions/overview/skills/). Dokumentation zur Virtual Assistant- und Kompetenzarchitektur [finden Sie unter Virtual Assistant und Kompetenzarchitektur](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true).  

## <a name="limitations-of-virtual-assistant"></a>Einschränkungen von Virtual Assistant

* **EndOfConversation: Eine Fertigkeit** muss eine `endOfConversation` Aktivität senden, wenn sie eine Unterhaltung beendet. Basierend auf der Aktivität beendet ein Virtual Assistant den Kontext mit dieser bestimmten Fähigkeit und gelangt wieder in den Stammkontext Virtual Assistant. Für den Bot "Book-a-room" gibt es keinen klaren Zustand, in dem die Unterhaltung beendet wird. Daher haben wir nicht vom Bot gesendet `endOfConversation` und wenn der Benutzer zum Stammkontext zurückkehren möchte, kann er dies einfach per `start over` Befehl `Book-a-room` tun.  
* **Kartenaktualisierung**: Die Kartenaktualisierung wird von Virtual Assistant noch nicht unterstützt.  
* **Nachrichtenerweiterungen**:
  * Derzeit kann ein Virtual Assistant maximal zehn Befehle für Nachrichtenerweiterungen unterstützen.
  * Die Konfiguration von Nachrichtenerweiterungen ist nicht auf einzelne Befehle beschränkt, sondern auf die gesamte Erweiterung selbst. Dadurch wird die Konfiguration für jede einzelne Fähigkeit durch Virtual Assistant beschränkt.
  * Nachrichtenerweiterungen-Befehls-IDs haben eine maximale Länge von [64 Zeichen](../resources/schema/manifest-schema.md#composeextensions) , und zum Einbetten von Qualifikationsinformationen werden 37 Zeichen verwendet. Daher sind aktualisierte Einschränkungen für die Befehls-ID auf 27 Zeichen beschränkt.

Sie können auch vorhandene Fähigkeiten aus dem [Repository für Bot Framework-Lösungen](https://github.com/microsoft/botframework-components/tree/main/skills/csharp) nutzen oder ganz von Grund auf eine neue Fertigkeit erstellen. Lernprogramme für die späteren finden Sie [hier](https://microsoft.github.io/botframework-solutions/overview/skills/). In der [Dokumentation](/azure/bot-service/skills-conceptual?view=azure-bot-service-4.0&preserve-view=true) finden Sie Virtual Assistant und Kompetenzarchitektur.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **C#**  **.NET** |
|----------|-----------------|---------------------------|
| Aktualisierte Visual Studio-Vorlage | Angepasste Vorlage zur Unterstützung von Teams-Funktionen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-virtual-assistant/csharp) |
| Book-a-Room-Bot-Qualifikationscode | Hier können Sie unterwegs schnell einen Besprechungsraum finden und buchen. | [Anzeigen](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom/tree/nebhagat/microsoft-teams-apps-bookaroom-skill) |

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Buch-a-Raum](app-templates.md#app-template-code-samples)
* [Microsoft Teams Bot](../bots/what-are-bots.md)
