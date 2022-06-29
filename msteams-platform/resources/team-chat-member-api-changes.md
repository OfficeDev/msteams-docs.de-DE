---
title: Bot-API-Änderungen für Team- und Chatmitglieder
author: ojasvichoudhary
description: In diesem Modul lernen Sie bevorstehende und laufende Änderungen an den Bot-APIs kennen, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden.
ms.localizationpriority: medium
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: e3096b3a2201d1bc36824fb5bf726150522f679b
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485363"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Änderungen der Teams-Bot-API zum Abrufen von Team- oder Chatmitgliedern

> [!NOTE]
> `TeamsInfo.getMembers` und `TeamsInfo.GetMembersAsync` APIs sind veraltet. Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10 Tausend Mitglieder pro Team zurück, und die vollständige Teilnehmerliste wird für große Teams nicht zurückgegeben. Sie müssen auf Version 4.10 oder höher des Bot Framework SDK aktualisieren und zu den paginierten API-Endpunkten wechseln, oder dies `TeamsInfo.GetMemberAsync` zum Abrufen einzelner Benutzer verwenden.
>
> Dies gilt auch für Ihren Bot, auch wenn Sie diese APIs nicht direkt verwenden, da ältere SDKs diese APIs während [membersAdded-Ereignissen](../bots/how-to/conversations/subscribe-to-conversation-events.md#members-added) aufrufen. Wenn Sie eine SDK-Version früher auf 4.10 verwenden, aktualisieren Sie sie auf die neueste Version.
>
> Informationen zum Anzeigen der Liste der anstehenden Änderungen finden Sie unter [API-Änderungen](team-chat-member-api-changes.md#api-changes).

Wenn Sie derzeit Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, können Sie die [Microsoft Teams-Bot-APIs](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` für C# oder `TeamsInfo.getMembers` für TypeScript oder Node.js-APIs verwenden. Weitere Informationen finden Sie unter [Abrufen der Teilnehmerliste oder des Benutzerprofils](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile).

Diese APIs weisen die folgenden Mängel auf:

* Bei großen Teams ist die Leistung schlecht, und Timeouts sind wahrscheinlicher: Die maximale Teamgröße ist seit der Veröffentlichung von Teams Anfang 2017 erheblich gewachsen. Da `GetMembersAsync` die gesamte Mitgliederliste zurückgegeben oder `getMembers` zurückgegeben wird, dauert es lange, bis der API-Aufruf für große Teams zurückgegeben wird, und es ist üblich, dass der Aufruf ein Timeout hat und Sie es erneut versuchen müssen.
* Das Abrufen von Profildetails für einen einzelnen Benutzer ist schwierig: Um die Profilinformationen für einen einzelnen Benutzer abzurufen, müssen Sie die gesamte Mitgliederliste abrufen und dann nach der gewünschten Liste suchen. Es gibt eine Hilfsfunktion im Bot Framework SDK, um es einfacher zu machen, aber es ist nicht effizient.

Mit der Einführung organisationsweiter Teams ist es erforderlich, diese APIs besser an Office 365 Datenschutzsteuerelemente auszurichten. Bots, die in großen Teams verwendet werden, können grundlegende Profilinformationen ähnlich wie die `User.ReadBasic.All` Microsoft Graph-Berechtigung abrufen. Mandantenadministratoren haben eine große Kontrolle darüber, welche Apps und Bots in ihrem Mandanten verwendet werden können, aber diese Einstellungen unterscheiden sich von Microsoft Graph.

Der folgende Code stellt eine JSON-Beispieldarstellung der von Teams-Bot-APIs zurückgegebenen Elemente bereit:

```json
[{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "Anon1 (Guest)",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
 "userRole": "anonymous"
}, {
    "id": "29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
    "objectId": "76b0b09f-d410-48fd-993e-84da521a597b",
    "givenName": "John",
    "surname": "Patterson",
    "email": "johnp@fabrikam.com",
    "userPrincipalName": "johnp@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
 "userRole": "user"
}, {
    "id": "29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
    "objectId": "6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
    "givenName": "Rick",
    "surname": "Stevens",
    "email": "Rick.Stevens@fabrikam.com",
    "userPrincipalName": "rstevens@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47",
 "userRole": "user"
}]
```

## <a name="api-changes"></a>API-Änderungen

Es folgen die anstehenden API-Änderungen:

* Es wird eine neue API zum Abrufen von Profilinformationen für Mitglieder eines Chats oder Teams erstellt [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) . Diese API ist jetzt mit dem Bot Framework Version 4.8 oder höher SDK verfügbar. Verwenden Sie die Methode für die [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) Entwicklung in allen anderen Versionen.

    > [!NOTE]
    > In v3 oder v4 besteht die beste Aktion darin, auf die neueste Point-Version zu aktualisieren, die 3.30.2 bzw. 4.8 oder höher ist.

* Es wird eine neue API zum Abrufen der Profilinformationen für einen einzelnen Benutzer erstellt [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) . Es verwendet die ID des Teams oder Chats und einen [UPN](/windows/win32/ad/naming-properties#userprincipalname)`userPrincipalName`, Microsoft Azure Active Directory (Azure AD) Object ID`objectId`, oder die Teams-Benutzer-ID `id` als Parameter und gibt die Profilinformationen für diesen Benutzer zurück.

    > [!NOTE]
    > `objectId` wird so geändert `aadObjectId` , dass es dem `Activity` entspricht, was im Objekt einer Bot Framework-Nachricht aufgerufen wird. Die neue API ist mit Version 4.8 oder höher des Bot Framework SDK verfügbar. Es ist auch in der Teams SDK-Erweiterung Bot Framework 3.x verfügbar. In der Zwischenzeit können Sie den [REST-Endpunkt](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) verwenden.

* `TeamsInfo.GetMembersAsync` in C# und `TeamsInfo.getMembers` in TypeScript oder Node.js ist formal veraltet. Sobald die neue API verfügbar ist, müssen Sie Ihre Bots aktualisieren, um sie zu verwenden. Dies gilt auch für die [zugrunde liegende REST-API, die diese APIs verwenden](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json). 
