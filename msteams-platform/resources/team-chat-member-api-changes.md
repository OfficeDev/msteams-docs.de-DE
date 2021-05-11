---
title: Bot-API-Änderungen für Team- und Chatmitglieder
author: ojasvichoudhary
description: Beschreibt bevorstehende und in Bearbeitung ausgeführte Änderungen an den Bot-APIs, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden.
keywords: Bot-Framework-Apis-Teammitgliederliste
localization_priority: Normal
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: ad03d14ca1c38eb810d43027e901e01199858992
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019678"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Teams Bot-API-Änderungen zum Abrufen von Team- oder Chatmitgliedern

>[!NOTE]
> Der Veraltetkeitsprozess für `TeamsInfo.getMembers` und `TeamsInfo.GetMembersAsync` APIs wurde gestartet. Anfangs werden sie auf fünf Anforderungen pro Minute stark gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Dies führt dazu, dass der vollständige Dienstplan nicht zurückgegeben wird, wenn die Teamgröße zunimmt.
> Sie müssen auf Version 4.10 oder höher des Bot Framework SDK aktualisieren und zu den paginierten API-Endpunkten oder der API mit einem `TeamsInfo.GetMemberAsync` einzelnen Benutzer wechseln. Dies gilt auch für Ihren Bot, auch wenn Sie diese APIs nicht direkt verwenden, da ältere SDKs diese APIs während [membersAdded-Ereignissen](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) aufrufen. Informationen zum Anzeigen der Liste anstehender Änderungen finden Sie unter [API-Änderungen](team-chat-member-api-changes.md#api-changes). 

Derzeit verwenden Botentwickler, die Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, die Microsoft Teams-Bot-APIs für C# oder `TeamsInfo.GetMembersAsync` `TeamsInfo.getMembers` für TypeScript- oder Node.js-APIs. Weitere Informationen finden Sie unter [Abrufliste oder Benutzerprofil](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile). Diese APIs haben mehrere Nachteile.

Derzeit können Sie, wenn Sie Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, die [Microsoft Teams-Bot-APIs](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) für C# oder `TeamsInfo.GetMembersAsync` für TypeScript- oder `TeamsInfo.getMembers` Node.js-APIs verwenden. Diese APIs haben die folgenden Nachteile:

* Bei großen Teams ist die Leistung schlecht, und Timeouts sind wahrscheinlicher: Die maximale Teamgröße ist seit Teams Anfang 2017 erheblich angezogen. Wenn die gesamte Mitgliederliste zurückgegeben oder zurückgegeben wird, dauert es sehr lange, bis der API-Aufruf für große Teams zurückgegeben wird, und es ist üblich, dass der Aufruf ein Zeit-Out eingibt, und Sie müssen es erneut `GetMembersAsync` `getMembers` versuchen.
* Das Abrufen von Profildetails für einen einzelnen Benutzer ist schwierig: Um die Profilinformationen für einen einzelnen Benutzer abzurufen, müssen Sie die gesamte Mitgliederliste abrufen und dann nach dem gesuchten suchen. Es gibt eine Hilfsfunktion im Bot Framework SDK, um es einfacher zu machen, aber es ist nicht effizient.

Mit der Einführung von organisationsweiten Teams ist es erforderlich, diese APIs besser an den Office 365 auszurichten. Bots, die in großen Teams verwendet werden, können grundlegende Profilinformationen wie die `User.ReadBasic.All` Microsoft-Graph abrufen. Mandantenadministratoren haben eine große Kontrolle darüber, welche Apps und Bots in ihrem Mandanten verwendet werden können, aber diese Einstellungen unterscheiden sich von microsoft Graph.

Der folgende Code enthält eine Beispiel-JSON-Darstellung der von den Teams zurückgegebenen ApIs:

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

Im Folgenden finden Sie die anstehenden API-Änderungen:

* Eine neue API wird zum [`TeamsInfo.GetPagedMembersAsync`](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) Abrufen von Profilinformationen für Mitglieder eines Chats oder Teams erstellt. Diese API ist jetzt mit dem Bot Framework 4.8 SDK verfügbar. Verwenden Sie für die Entwicklung in allen anderen Versionen die [`GetConversationPagedMembers`](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) Methode.

    > [!NOTE]
    > In v3 oder v4 besteht die beste Aktion im Upgrade auf die neueste Punktversion, die 3.30.2 bzw. 4.8 ist.

* Zum Abrufen der Profilinformationen für einen einzelnen Benutzer wird eine neue API [`TeamsInfo.GetMemberAsync`](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) erstellt. Es verwendet die ID des Teams oder Chats und einen [UPN,](https://docs.microsoft.com/windows/win32/ad/naming-properties#userprincipalname) der `userPrincipalName` Azure Active Directory Objekt-ID oder die Teams-Benutzer-ID als Parameter ist, und gibt die Profilinformationen für diesen Benutzer `objectId` `id` zurück.

    > [!NOTE]
    > `objectId` wird so geändert, dass es mit dem im `aadObjectId` Objekt einer Bot Framework-Nachricht `Activity` aufgerufenen Übereinstimmungen übereinstimmen soll. Die neue API ist mit Version 4.8 des Bot Framework SDK verfügbar. Sie ist auch in der Teams SDK-Erweiterung Bot Framework 3.x verfügbar. In der Zwischenzeit können Sie den [REST-Endpunkt](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) verwenden.

* `TeamsInfo.GetMembersAsync` in C# und `TeamsInfo.getMembers` in TypeScript oder Node.js ist formal veraltet. Sobald die neue API verfügbar ist, müssen Sie Ihre Bots so aktualisieren, dass sie verwendet werden. Dies gilt auch für die [zugrunde liegende REST-API, die diese APIs verwenden.](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json)
* Bis Ende 2021 können Bots die Eigenschaften oder für Mitglieder eines Chats oder Teams nicht proaktiv `userPrincipalName` `email` abrufen. Bots müssen Graph verwenden, um sie abzurufen. Die `userPrincipalName` `email` Und-Eigenschaften werden nicht von der neuen API ab `GetConversationPagedMembers` Ende 2021 zurückgegeben. Bots müssen Graph mit einem Zugriffstoken verwenden, um Informationen abzurufen. Es muss Bots erleichtert werden, ein Zugriffstoken zu erhalten und den Zustimmungsprozess für Endbenutzer zu optimieren und zu vereinfachen.
