---
title: Bot-API-Änderungen für Team- und Chatmitglieder
author: ojasvichoudhary
description: Beschreibt bevorstehende und laufende Änderungen an den Bot-APIs, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden
keywords: Liste der Bot-Framework-Apis-Teammitglieder
localization_priority: Normal
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 333a29664f0d60e89039f906fce77e71054d486f
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555437"
---
# <a name="teams-bot-api-changes-to-fetch-team-or-chat-members"></a>Teams-Bot-API-Änderungen, um Team- oder Chatmitglieder abzurufen

>[!NOTE]
> Der Veraltungsprozess für `TeamsInfo.getMembers` und `TeamsInfo.GetMembersAsync` APIs wurde gestartet. Zunächst werden sie stark auf fünf Anfragen pro Minute gedrosselt und geben maximal 10K-Mitglieder pro Team zurück. Dies führt dazu, dass der vollständige Dienstplan nicht zurückgegeben wird, wenn die Teamgröße zunimmt.
> Sie müssen auf Version 4.10 oder höher des Bot Framework SDK aktualisieren und zu den paginierten API-Endpunkten oder der `TeamsInfo.GetMemberAsync` Einzelbenutzer-API wechseln. Dies gilt auch für Ihren Bot, auch wenn Sie diese APIs nicht direkt verwenden, da ältere SDKs diese APIs während [membersAdded-Ereignissen](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) aufrufen. Informationen zur Liste der anstehenden Änderungen finden Sie unter [API-Änderungen](team-chat-member-api-changes.md#api-changes). 

Derzeit verwenden Bot-Entwickler, die Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, die Microsoft Teams-Bot-APIs `TeamsInfo.GetMembersAsync` für C- oder `TeamsInfo.getMembers` für TypeScript- oder Node.js-APIs. Weitere Informationen finden Sie unter Abrufen von [Dienstplänen oder Benutzerprofilen](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile). Diese APIs weisen mehrere Mängel auf.

Wenn Sie derzeit Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, können Sie die [Microsoft Teams-Bot-APIs](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) `TeamsInfo.GetMembersAsync` für C- oder `TeamsInfo.getMembers` typeScript- oder Node.js-APIs verwenden. Diese APIs weisen folgende Mängel auf:

* Für große Teams ist die Leistung schlecht und Timeouts sind wahrscheinlicher: Die maximale Teamgröße ist seit der Veröffentlichung Teams Anfang 2017 erheblich gestiegen. Wenn `GetMembersAsync` die gesamte Mitgliederliste zurückgegeben wird oder zurückgegeben `getMembers` wird, dauert es lange, bis der API-Aufruf für große Teams zurückgegeben wird, und es ist üblich, dass der Aufruf eine Zeitabfolge abläuft, und Sie müssen es erneut versuchen.
* Das Abrufen von Profildetails für einen einzelnen Benutzer ist schwierig: Um die Profilinformationen für einen einzelnen Benutzer abzurufen, müssen Sie die gesamte Mitgliederliste abrufen und dann nach der gewünschten Suchen suchen. Es gibt eine Hilfsfunktion im Bot Framework SDK, um sie einfacher zu machen, aber sie ist nicht effizient.

Mit der Einführung organisationsweiter Teams ist es erforderlich, diese APIs besser an Office 365 Datenschutzkontrollen auszurichten. Bots, die in großen Teams verwendet werden, können grundlegende Profilinformationen abrufen, die der `User.ReadBasic.All` Microsoft-Graph-Berechtigung ähneln. Mandantenadministratoren haben eine große Kontrolle darüber, welche Apps und Bots in ihrem Mandanten verwendet werden können, aber diese Einstellungen unterscheiden sich von Microsoft Graph.

Der folgende Code bietet eine JsON-Beispieldarstellung dessen, was von Teams-Bot-APIs zurückgegeben wird:

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

Im Folgenden sind die anstehenden API-Änderungen zu finden:

* Eine neue API wird [`TeamsInfo.GetPagedMembersAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile) zum Abrufen von Profilinformationen für Mitglieder eines Chats oder Teams erstellt. Diese API ist jetzt mit dem Bot Framework-SDK der Version 4.8 oder höher verfügbar. Für die Entwicklung in allen anderen Versionen verwenden Sie die [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) Methode.

    > [!NOTE]
    > In v3 oder v4 ist die beste Aktion, ein Upgrade auf die neueste Punktversion zu aktualisieren, die 3.30.2 bzw. 4.8 oder höher ist.

* Es wird eine neue API [`TeamsInfo.GetMemberAsync`](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) zum Abrufen der Profilinformationen für einen einzelnen Benutzer erstellt. Es nimmt die ID des Teams oder Chats und eines [UPNs,](/windows/win32/ad/naming-properties#userprincipalname) der `userPrincipalName` , Azure Active Directory Objekt-ID `objectId` oder die Teams Benutzer-ID `id` als Parameter und gibt die Profilinformationen für diesen Benutzer zurück.

    > [!NOTE]
    > `objectId` wird so geändert, dass es `aadObjectId` dem entspricht, was im Objekt einer Bot `Activity` Framework-Nachricht aufgerufen wird. Die neue API ist ab Version 4.8 des Bot Framework SDK verfügbar. Es ist auch in der Teams SDK-Erweiterung Bot Framework 3.x verfügbar. In der Zwischenzeit [](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) können Sie den REST-Endpunkt verwenden.

* `TeamsInfo.GetMembersAsync` in C- und `TeamsInfo.getMembers` typeScript oder Node.js ist formal veraltet. Sobald die neue API verfügbar ist, müssen Sie Ihre Bots aktualisieren, um sie zu verwenden. Dies gilt auch für die [zugrunde liegende REST-API, die von diesen APIs verwendet](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json)wird.
* Bis Ende 2021 können Bots die oder Eigenschaften für Mitglieder eines Chats oder Teams nicht proaktiv `userPrincipalName` `email` abrufen. Bots müssen Graph verwenden, um sie abzurufen. Die `userPrincipalName` und Eigenschaften werden ab Ende `email` 2021 nicht von der neuen `GetConversationPagedMembers` API zurückgegeben. Bots müssen Graph mit einem Zugriffstoken verwenden, um Informationen abzurufen. Es muss für Bots einfacher gemacht werden, ein Zugriffstoken zu erhalten und den Endbenutzer-Zustimmungsprozess zu rationalisieren und zu vereinfachen.
