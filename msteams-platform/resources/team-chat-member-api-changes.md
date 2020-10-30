---
title: Änderungen der bot-API für Team/Chat Mitglieder (2020 Update)
author: ojasvichoudhary
description: Beschreibt bevorstehende und in Bearbeitung befindliche Änderungen an den bot-APIs, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden.
keywords: Teammitglieder-Dienstplan für bot Framework-APIs
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: 243969796d9d1dc427ab7736cf5e0f0d320731c7
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796143"
---
# <a name="changes-to-teams-bot-apis-for-fetching-teamchat-members"></a>Änderungen an Teams-bot-APIs zum Abrufen von Team/Chat-Mitgliedern

Derzeit verwenden bot-Entwickler, die Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, die Microsoft Teams-bot-APIs `TeamsInfo.GetMembersAsync` (für C#) oder `TeamsInfo.getMembers` (für die Manuskript/Node.js)-APIs [(hier dokumentiert)](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetching-the-roster-or-user-profile). Diese APIs haben heute einige Mängel:

* **Bei großen Teams ist die Leistung schlecht, und Timeouts sind wahrscheinlicher.** Die maximale Team Größe ist erheblich gestiegen, seit Microsoft Teams Anfang 2017 veröffentlicht wurde. Da `GetMembersAsync` / `getMembers` die gesamte Mitgliederliste zurückgegeben wird, dauert es lange, bis der API-Aufruf für große Teams zurückgegeben wird, und es ist nicht ungewöhnlich, dass der Anruf mit einem Timeout erfolgt und Sie es erneut versuchen müssen.
* **Das Einholen von Profildetails für einen einzelnen Benutzer ist umständlich.** Wenn Sie die Profilinformationen für einen einzelnen Benutzer abrufen möchten, müssen Sie die gesamte Mitgliederliste abrufen und dann nach der gewünschten Person suchen. True, es gibt eine Hilfsfunktion im bot Framework SDK, um Sie einfacher zu machen, aber unter den Abdeckungen ist Sie nicht effizient.

Mit der Einführung von organisationsweiten Teams wurde klar, dass es an der Zeit war, diese APIs mit Office 365 Datenschutzkontrollen besser auszurichten: in großen Teams verwendete Bots können grundlegende Profilinformationen abrufen, was der `User.ReadBasic.All` Microsoft Graph-Berechtigung ähnelt. Mandantenadministratoren haben sehr viel Kontrolle darüber, welche apps und Bots in Ihrem Mandanten verwendet werden können, diese Einstellungen unterscheiden sich jedoch von denen, die Microsoft Graph steuern.

Hier ist eine Beispiel-JSON-Darstellung dessen, was heute von diesen APIs zurückgegeben wird. Ich beziehe mich auf einige der Felder unten.

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
Hier sind die bevorstehenden API-Änderungen:

* Wir haben eine neue API [`TeamsInfo.GetPagedMembersAsync`](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetching-the-roster-or-user-profile) zum Abrufen von Profilinformationen für Mitglieder eines Chats/Teams erstellt. Diese API steht jetzt mit dem bot Framework 4,8 SDK zur Verfügung. Für die Entwicklung in allen anderen Versionen verwenden Sie die [`GetConversationPagedMembers`](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable) -Methode. **Hinweis** : in V3 oder V4 besteht die beste Aktion darin, ein Upgrade auf die neueste Version des Points durchführen (3.30.2 oder 4,8). 
* Wir haben eine neue API [`TeamsInfo.GetMemberAsync`](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#get-single-member-details) zum Abrufen der Profilinformationen für einen einzelnen Benutzer erstellt. Er übernimmt die ID des Teams/Chats und einen [UPN](https://docs.microsoft.com/windows/win32/ad/naming-properties#userprincipalname) ( `userPrincipalName` , *siehe oben* ), Azure Active Directory Objekt-ID ( `objectId` , *siehe oben* ) oder die Benutzer-ID Teams ( `id` , *siehe oben* ) als Parameter und gibt die Profilinformationen für diesen Benutzer zurück. **Hinweis** : Wir ändern `objectId` zu `aadObjectId` , damit übereinstimmen, was es im `Activity` Objekt einer bot-Framework-Nachricht aufgerufen wird. Die neue API steht mit der Version 4,8 des bot Framework SDK zur Verfügung. Es wird in Kürze auch in der Microsoft Teams SDK-Erweiterung bot Framework 3. x verfügbar sein; in der Zwischenzeit können Sie den [Rest](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#get-single-member-details) -Endpunkt verwenden.
* `TeamsInfo.GetMembersAsync` (C#) und `TeamsInfo.getMembers` (Schreibweise/Node.js) ist offiziell veraltet und wird in späten 2021 nicht mehr funktionieren. Basierend auf dem Feedback von Entwicklern werden wir im Mai 2020 einen bestimmten Zeitplan bekanntgeben. Sobald die neue ausgelagerte API verfügbar ist, sollten Entwickler ihre Bots aktualisieren, um Sie zu verwenden. (Dies gilt auch für die [zugrunde liegende Rest-API, die diese APIs verwenden](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=json#tabpanel_CeZOj-G++Q_json).)
* Bis Ende 2021 können Bots die `userPrincipalName` oder- `email` Eigenschaften für Mitglieder eines Chats/Teams nicht proaktiv abrufen und müssen Microsoft Graph verwenden, um Sie abzurufen. Insbesondere `userPrincipalName` `email` werden Eigenschaften nicht von der neuen `GetConversationPagedMembers` API ab Ende 2021 zurückgegeben. Bots müssen Microsoft Graph mit einem Zugriffstoken verwenden, um diese Informationen abzurufen. Dies ist natürlich eine wesentliche Änderung: Wir müssen Bots einfacher machen, ein Zugriffstoken zu erhalten, und wir müssen den Endbenutzer-Zustimmungsprozess rationalisieren und vereinfachen.

## <a name="feedback-and-more-information"></a>Feedback und weitere Informationen
Wir verwenden diese Seite, um aktuelle Informationen zu diesen Änderungen bereitzustellen. Wenn Sie Fragen haben, verwenden Sie die "Feedback > auf dieser Seite senden" im Abschnitt **Feedback** unten. 
