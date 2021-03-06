---
title: Bot-API-Änderungen für Team- und Chatmitglieder
author: ojasvichoudhary
description: Beschreibt bevorstehende und laufende Änderungen an den Bot-APIs, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden.
keywords: Listenliste für Bot-Framework-APIs-Teammitglieder
localization_priority: Normal
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 9c6444967d330d27a415ac596a3858c05c49236e
ms.sourcegitcommit: b1f9162a0bbcd276064ae9e4f1e8bccc06cb7035
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2021
ms.locfileid: "53328065"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Teams Bot-API-Änderungen zum Abrufen von Team- oder Chatmitgliedern

>[!NOTE]
> Der Veraltete Prozess für `TeamsInfo.getMembers` und `TeamsInfo.GetMembersAsync` APIs wurde gestartet. Anfangs werden sie stark auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Dies führt dazu, dass die vollständige Liste nicht zurückgegeben wird, wenn die Teamgröße zunimmt.
> Sie müssen auf Version 4.10 oder höher des Bot Framework SDK aktualisieren und zu den paginierten API-Endpunkten oder der `TeamsInfo.GetMemberAsync` API für einzelne Benutzer wechseln. Dies gilt auch für Ihren Bot, auch wenn Sie diese APIs nicht direkt verwenden, da ältere SDKs diese APIs während [MembersAdded-Ereignissen](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) aufrufen. Informationen zum Anzeigen der Liste bevorstehender Änderungen finden Sie unter [API-Änderungen.](team-chat-member-api-changes.md#api-changes)

Wenn Sie informationen zu einem oder mehreren Mitgliedern eines Chats oder Teams abrufen möchten, können Sie derzeit die [Microsoft Teams-Bot-APIs](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` für C# oder für `TeamsInfo.getMembers` TypeScript- oder Node.js-APIs verwenden. Weitere Informationen finden Sie unter [Abrufen von Dienstplänen oder Benutzerprofilen.](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile)

Diese APIs weisen die folgenden Nachteile auf:

* Bei großen Teams ist die Leistung schlecht, und Timeouts sind wahrscheinlicher: Die maximale Teamgröße ist seit der Veröffentlichung Teams Anfang 2017 erheblich gestiegen. As `GetMembersAsync` or returns the entire member `getMembers` list, it takes a long time for the API call to return for large teams, and it is common for the call to time out and you have to try again.
* Das Abrufen von Profildetails für einen einzelnen Benutzer ist schwierig: Um die Profilinformationen für einen einzelnen Benutzer abzurufen, müssen Sie die gesamte Mitgliederliste abrufen und dann nach der gewünschten Liste suchen. Es gibt eine Hilfsfunktion im Bot Framework SDK, um sie zu vereinfachen, ist aber nicht effizient.

Mit der Einführung organisationsweiter Teams ist es erforderlich, diese APIs besser an Office 365 Datenschutzkontrollen auszurichten. Bots, die in großen Teams verwendet werden, können grundlegende Profilinformationen wie die `User.ReadBasic.All` Microsoft Graph-Berechtigung abrufen. Mandantenadministratoren haben eine große Kontrolle darüber, welche Apps und Bots in ihrem Mandanten verwendet werden können, aber diese Einstellungen unterscheiden sich von Microsoft Graph.

Der folgende Code stellt eine JSON-Beispieldarstellung der von Teams Bot-APIs zurückgegebenen Elemente bereit:

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

Nachfolgend sind die bevorstehenden API-Änderungen aufgeführt:

* Es wird eine neue API [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) zum Abrufen von Profilinformationen für Mitglieder eines Chats oder Teams erstellt. Diese API ist jetzt mit bot Framework Version 4.8 oder höher SDK verfügbar. Verwenden Sie für die Entwicklung in allen anderen Versionen die [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) Methode.

    > [!NOTE]
    > In v3 oder v4 besteht die beste Aktion darin, auf die neueste Punktversion zu aktualisieren, die 3.30.2 oder 4.8 oder höher ist.

* Es wird eine neue API [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) zum Abrufen der Profilinformationen für einen einzelnen Benutzer erstellt. Sie verwendet die ID des Teams oder Chats und einen [UPN](/windows/win32/ad/naming-properties#userprincipalname) `userPrincipalName` , Azure Active Directory Objekt-ID, `objectId` oder die Teams Benutzer-ID `id` als Parameter und gibt die Profilinformationen für diesen Benutzer zurück.

    > [!NOTE]
    > `objectId` wird so geändert, dass es `aadObjectId` mit dem übereinstimmt, was im Objekt einer `Activity` Bot Framework-Nachricht aufgerufen wird. Die neue API ist mit Version 4.8 oder höher des Bot Framework SDK verfügbar. Es ist auch in der Teams SDK-Erweiterung Bot Framework 3.x verfügbar. In der Zwischenzeit können Sie den [REST-Endpunkt](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) verwenden.

* `TeamsInfo.GetMembersAsync` in C# und `TeamsInfo.getMembers` in TypeScript oder Node.js ist formell veraltet. Sobald die neue API verfügbar ist, müssen Sie Ihre Bots aktualisieren, um sie zu verwenden. Dies gilt auch für die [zugrunde liegende REST-API, die diese APIs verwenden.](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json)
* Ende 2022 können Bots die Oder Eigenschaften für Mitglieder eines Chats oder Teams nicht proaktiv `userPrincipalName` `email` abrufen. Bots müssen Graph verwenden, um sie abzurufen. Die `userPrincipalName` eigenschaften werden ab Ende `email` 2022 nicht von der neuen `GetConversationPagedMembers` API zurückgegeben. Bots müssen Graph mit einem Zugriffstoken verwenden, um Informationen abzurufen. Bots müssen das Abrufen eines Zugriffstokens vereinfachen und den Zustimmungsprozess für Endbenutzer optimieren und vereinfachen.
