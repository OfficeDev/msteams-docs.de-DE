---
title: Get Teams specific context for your bot
author: laujan
description: Hier erfahren Sie, wie Sie den spezifischen Kontext von Microsoft Team für Ihren Bot, einschließlich Unterhaltungsliste, Details und Kanalliste, erhalten.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 9703a063ccccc8409239d5826a4935070b307edd
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696328"
---
# <a name="get-teams-specific-context-for-your-bot"></a>Get Teams specific context for your bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ein Bot kann auf zusätzliche Kontextdaten zu einem Team oder Chat zugreifen, in dem er installiert ist. Diese Informationen können verwendet werden, um die Funktionalität des Bots zu erweitern und eine personalisiertere Benutzererfahrung zu bieten.

## <a name="fetch-the-roster-or-user-profile"></a>Abrufen des Dienstplans oder Benutzerprofils

Ihr Bot kann die Liste der Mitglieder und deren grundlegende Benutzerprofile abfragen, einschließlich Teams-Benutzer-IDs und Azure Active Directory (AAD)-Informationen, z. B. Name und objectId. Sie können diese Informationen verwenden, um Benutzeridentitäten zu korrelieren. Um beispielsweise zu überprüfen, ob sich ein Benutzer über AAD-Anmeldeinformationen bei einer Registerkarte angemeldet hat, ist er Mitglied des Teams. Zum Erhalten von Unterhaltungsmitgliedern hängt die minimale oder maximale Seitengröße von der Implementierung ab. Seitengröße kleiner als 50, werden als 50 behandelt, und größer als 500 werden auf 500 begrenzt. Auch wenn Sie die nicht ausseitige Version verwenden, ist sie in großen Teams unzuverlässig und darf nicht verwendet werden. Weitere Informationen finden Sie [unter Änderungen an Teams Bot-APIs zum Abrufen von Team- oder Chatmitgliedern.](~/resources/team-chat-member-api-changes.md)

Im folgenden Beispielcode wird der seitenseitige Endpunkt zum Abrufen der Liste verwendet:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var members = new List<TeamsChannelAccount>();
        string continuationToken = null;

        do
        {
            var currentPage = await TeamsInfo.GetPagedMembersAsync(turnContext, 100, continuationToken, cancellationToken);
            continuationToken = currentPage.ContinuationToken;
            members.AddRange(currentPage.Members);
         }
         while (continuationToken != null);
     }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            var continuationToken;
            var members = [];

            do {
                var pagedMembers = await TeamsInfo.getPagedMembers(context, 100, continuationToken);
                continuationToken = pagedMembers.continuationToken;
                members.push(...pagedMembers.members);
            }
            while(continuationToken !== undefined)

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

# <a name="json"></a>[Json](#tab/json)

Sie können eine GET-Anforderung direkt auf `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden. Der Wert von `serviceUrl` ist stabil, kann sich jedoch ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen. Die Antwortnutzlast gibt außerdem an, ob der Benutzer ein regulärer oder anonymer Benutzer ist.

```http
GET /v3/conversations/19:meeting_N2QzYTA3YmItYmMwOC00OTJmLThkYzMtZWMzZGU0NGIyZGI0@thread.v2/pagedmembers?pageSize=100&continuationToken=asdfasdfalkdsjfalksjdf

Response body
{
   "continuationToken":"asdfqwerueiqpiewr",
   "members":[
      {
         "id":"29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
         "name":"Anon1 (Guest)",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"anonymous"
      },
      {
         "id":"29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
         "objectId":"76b0b09f-d410-48fd-993e-84da521a597b",
         "givenName":"John",
         "surname":"Patterson",
         "email":"johnp@fabrikam.com",
         "userPrincipalName":"johnp@fabrikam.com",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"user"
      },
      {
         "id":"29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
         "objectId":"6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
         "givenName":"Rick",
         "surname":"Stevens",
         "email":"Rick.Stevens@fabrikam.com",
         "userPrincipalName":"rstevens@fabrikam.com",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"user"
      }
   ]
}
```

* * *

Nachdem Sie den Dienstplan oder das Benutzerprofil abgerufen haben, können Sie Details zu einem einzelnen Mitglied abrufen. Um Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abzurufen, verwenden Sie derzeit die Microsoft Teams-Bot-APIs für C# oder `TeamsInfo.GetMembersAsync` `TeamsInfo.getMembers` für TypeScript-APIs.

## <a name="get-single-member-details"></a>Details zu einzelnen Membern erhalten

Sie können auch die Details eines bestimmten Benutzers mithilfe der Teams-Benutzer-ID, des UPN oder der AAD-Objekt-ID abrufen.

Der folgende Beispielcode wird verwendet, um Details zu einzelnen Membern zu erhalten:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        const member = await TeamsInfo.getMember(context, encodeURI('someone@somecompany.com'));

        // By calling next() you ensure that the next BotHandler is run.
        await next();
        });
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    member = TeamsInfo.get_member(turn_context, turn_context.activity.from_property.id)
```

# <a name="json"></a>[Json](#tab/json)

Sie können eine GET-Anforderung direkt auf `/v3/conversations/{conversationId}/members/{userId}` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden. Der Wert von `serviceUrl` ist stabil, kann sich jedoch ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen. Dies kann für reguläre und anonyme Benutzer verwendet werden.

Nachfolgend finden Sie das Antwortbeispiel für reguläre Benutzer:

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members/29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "objectId": "9d3e08f9-a7ae-43aa-a4d3-de3f319a8a9c",
    "givenName": "Larry",
    "surname": "Brown",
    "email": "Larry.Brown@fabrikam.com",
    "userPrincipalName": "labrown@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47", 
    "userRole":"user"
}
```

Im Folgenden finden Sie das Antwortbeispiel für anonymen Benutzer:

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members/<anonymous user id>"

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "Anon1 (Guest)",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47", 
    "userRole":"anonymous"
}
```

* * *

Nachdem Sie Details zu einem einzelnen Mitglied erhalten haben, können Sie Details zum Team erhalten. Verwenden Sie derzeit zum Abrufen von Informationen für ein Team die Microsoft Teams-Bot-APIs `TeamsInfo.GetMemberDetailsAsync` für C# oder `TeamsInfo.getTeamDetails` typeScript.

## <a name="get-teams-details"></a>Details des Teams erhalten

Bei der Installation in einem Team kann ihr Bot Metadaten zu diesem Team abfragen, einschließlich der AAD-Gruppen-ID.

Der folgende Beispielcode wird verwendet, um die Details des Teams zu erhalten:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        TeamDetails teamDetails = await TeamsInfo.GetTeamDetailsAsync(turnContext, turnContext.Activity.TeamsGetTeamInfo().Id, cancellationToken);
        if (teamDetails != null) {
            await turnContext.SendActivityAsync($"The groupId is: {teamDetails.AadGroupId}");
        }
        else {
            await turnContext.SendActivityAsync($"Message did not come from a channel in a team.");
        }
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const teamDetails = await TeamsInfo.getTeamDetails(turnContext);
            if (teamDetails) {
                await turnContext.sendActivity(`The group ID is: ${teamDetails.aadGroupId}`);
            } else {
                await turnContext.sendActivity('This message did not come from a channel in a team.');
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[Json](#tab/json)

Sie können eine GET-Anforderung direkt auf `/v3/teams/{teamId}` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden. Der Wert von `serviceUrl` ist stabil, kann sich jedoch ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.

```http
GET /v3/teams/19:ja0cu120i1jod12j@skype.net

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "The Team Name",
    "aadGroupId": "02ce3874-dd86-41ba-bddc-013f34019978"
}
```

* * *

Nachdem Sie Details zum Team erhalten haben, können Sie die Liste der Kanäle in einem Team erhalten. Verwenden Sie derzeit zum Abrufen von Informationen für eine Liste von Kanälen in einem Team die Microsoft Teams-Bot-APIs für C# oder `TeamsInfo.GetTeamChannelsAsync` `TeamsInfo.getTeamChannels` für TypeScript-APIs.

## <a name="get-the-list-of-channels-in-a-team"></a>Liste der Kanäle in einem Team erhalten

Ihr Bot kann die Liste der Kanäle in einem Team abfragen.

> [!NOTE]
> * Der Name des standardmäßigen allgemeinen Kanals wird zurückgegeben, `null` um die Lokalisierung zu ermöglichen.
> * Die Kanal-ID für den allgemeinen Kanal entspricht immer der Team-ID.

Der folgende Beispielcode wird verwendet, um die Liste der Kanäle in einem Team zu erhalten:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        IEnumerable<ChannelInfo> channels = await TeamsInfo.GetTeamChannelsAsync(turnContext, turnContext.Activity.TeamsGetTeamInfo().Id, cancellationToken);

        await turnContext.SendActivityAsync($"The channel count is: {channels.Count()}");
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const channels = await TeamsInfo.getTeamChannels(turnContext);

            await turnContext.sendActivity(`The channel count is: ${channels.length}`);

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[Json](#tab/json)

Sie können eine GET-Anforderung direkt auf `/v3/teams/{teamId}/conversations` aus, indem Sie den Wert von `serviceUrl` als Endpunkt verwenden. Der Wert von `serviceUrl` ist stabil, kann sich jedoch ändern. Wenn eine neue Nachricht eintrifft, muss Ihr Bot seinen gespeicherten Wert für `serviceUrl` überprüfen.

```http
GET /v3/teams/19%3A033451497ea84fcc83d17ed7fb08a1b6%40thread.skype/conversations

Response body
{
    "conversations": [{
        "id": "19:033451497ea84fcc83d17ed7fb08a1b6@thread.skype",
        "name": null
    }, {
        "id": "19:cc25e4aae50746ecbb11473bba24c70a@thread.skype",
        "name": "Materials"
    }, {
        "id": "19:b7b84cba410c406ba671dbbf5e0a3519@thread.skype",
        "name": "Design"
    }, {
        "id": "19:fc5db2aed489454e8f8c06829ed6c986@thread.skype",
        "name": "Marketing"
    }]
}
```

* * *

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Senden und Empfangen von Dateien über den Bot](~/bots/how-to/bots-filesv4.md)
