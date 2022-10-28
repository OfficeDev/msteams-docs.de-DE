---
title: Bot-API-Änderungen für Team- und Chatmitglieder
author: ojasvichoudhary
description: In diesem Modul lernen Sie bevorstehende und laufende Änderungen an den Bot-APIs kennen, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden.
ms.localizationpriority: medium
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 8160f59f1bb08cf205d057fa6c1e5df7a4e61240
ms.sourcegitcommit: 0e4fcbc5efff4bfa1dbfba1e5467bbfaa6638705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2022
ms.locfileid: "68773485"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Änderungen an der Teams-Bot-API zum Abrufen von Team- oder Chatmitgliedern

>[!NOTE]
> Der Veraltetkeitsprozess für `TeamsInfo.getMembers` - und `TeamsInfo.GetMembersAsync` -APIs wurde gestartet. Anfangs werden sie stark auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Dies führt dazu, dass die vollständige Liste nicht zurückgegeben wird, wenn die Teamgröße zunimmt.
> Sie müssen auf Version 4.10 oder höher des Bot Framework SDK aktualisieren und zu den paginierten API-Endpunkten oder der `TeamsInfo.GetMemberAsync` Einzelbenutzer-API wechseln. Dies gilt auch für Ihren Bot, wenn Sie diese APIs nicht direkt verwenden, da ältere SDKs diese APIs während [memberAdded-Ereignissen](../bots/how-to/conversations/subscribe-to-conversation-events.md#members-added) aufrufen. Die Liste der bevorstehenden Änderungen finden Sie unter [API-Änderungen](team-chat-member-api-changes.md#api-changes).

Wenn Sie Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, können Sie derzeit die [Microsoft Teams-Bot-APIs](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` für C# oder `TeamsInfo.getMembers` für TypeScript oder Node.js-APIs verwenden. Weitere Informationen finden Sie unter [Abrufen einer Liste oder eines Benutzerprofils](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile).

Diese APIs weisen die folgenden Mängel auf:

* Bei großen Teams ist die Leistung schlecht, und Timeouts sind wahrscheinlicher: Die maximale Teamgröße ist seit der Veröffentlichung von Teams Anfang 2017 erheblich gewachsen. Da `GetMembersAsync` oder `getMembers` die gesamte Mitgliederliste zurückgibt, dauert es lange, bis der API-Aufruf für große Teams zurückgegeben wird, und es ist üblich, dass für den Aufruf ein Timeout auftritt, und Sie müssen es erneut versuchen.
* Das Abrufen von Profildetails für einen einzelnen Benutzer ist schwierig: Um die Profilinformationen für einen einzelnen Benutzer abzurufen, müssen Sie die gesamte Mitgliederliste abrufen und dann nach der gewünschten Liste suchen. Es gibt eine Hilfsfunktion im Bot Framework SDK, um es zu vereinfachen, aber sie ist nicht effizient.

Mit der Einführung organisationsweiter Teams besteht die Anforderung, diese APIs besser an Office 365 Datenschutzkontrollen auszurichten. Bots, die in großen Teams verwendet werden, können grundlegende Profilinformationen ähnlich der `User.ReadBasic.All` Microsoft Graph-Berechtigung abrufen. Mandantenadministratoren haben eine große Kontrolle darüber, welche Apps und Bots in ihrem Mandanten verwendet werden können, aber diese Einstellungen unterscheiden sich von Microsoft Graph.

Der folgende Code enthält eine JSON-Beispieldarstellung der von Teams-Bot-APIs zurückgegebenen Daten:

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

Im Folgenden sind die bevorstehenden API-Änderungen aufgeführt:

* Eine neue API wird zum Abrufen von Profilinformationen für Mitglieder eines Chats oder Teams erstellt [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) . Diese API ist jetzt mit dem Bot Framework Sdk Version 4.8 oder höher verfügbar. Verwenden Sie für die Entwicklung in allen anderen Versionen die [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) -Methode.

    > [!NOTE]
    > In v3 oder v4 besteht die beste Aktion darin, ein Upgrade auf die neueste Punktversion durchzuführen, die 3.30.2 oder 4.8 oder höher ist.

* Es wird eine neue API zum Abrufen der Profilinformationen für einen einzelnen Benutzer erstellt [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) . Sie verwendet die ID des Teams oder Chats und einen [UPN](/windows/win32/ad/naming-properties#userprincipalname)`userPrincipalName`, der , Microsoft Azure Active Directory (Azure AD)-Objekt-ID `objectId`oder die Teams-Benutzer-ID `id` ist, als Parameter und gibt die Profilinformationen für diesen Benutzer zurück.

    > [!NOTE]
    > `objectId` wird in `aadObjectId` geändert, um dem `Activity` Im -Objekt einer Bot Framework-Nachricht zu entsprechen. Die neue API ist mit Version 4.8 oder höher des Bot Framework SDK verfügbar. Es ist auch in der Teams SDK-Erweiterung Bot Framework 3.x verfügbar. In der Zwischenzeit können Sie den [REST-Endpunkt](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) verwenden.

* `TeamsInfo.GetMembersAsync` in C# und `TeamsInfo.getMembers` in TypeScript oder Node.js ist formal veraltet. Sobald die neue API verfügbar ist, müssen Sie Ihre Bots aktualisieren, um sie zu verwenden. Dies gilt auch für die [zugrunde liegende REST-API, die diese APIs verwenden](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json).
* Bis Ende 2022 können Bots die `userPrincipalName` Eigenschaften oder `email` für Mitglieder eines Chats oder Teams nicht proaktiv abrufen. Bots müssen die Graph-APIs verwenden, um die erforderlichen Informationen abzurufen. Die neue `GetConversationPagedMembers` API kann die `userPrincipalName` Eigenschaften und `email` ab Ende 2022 nicht zurückgeben.

    > [!NOTE]
    > Es wird empfohlen, die [Graph-API](/graph/api/user-get?view=graph-rest-1.0&tabs=http&preserve-view=true#examples) mit einem Zugriffstoken zum Abrufen von Informationen zu verwenden.
