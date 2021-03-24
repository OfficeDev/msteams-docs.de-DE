---
title: Bot-API-Änderungen für Team- und Chatmitglieder
author: ojasvichoudhary
description: Beschreibt bevorstehende und in Bearbeitung ausgeführte Änderungen an den Bot-APIs, die zum Abrufen von Mitgliedern von Teams und Chats verwendet werden.
keywords: Bot-Framework-Apis-Teammitgliederliste
ms.topic: reference
ms.author: ojchoudh
ms.openlocfilehash: d55cbcdfea5e374c151c3eec82c52ac7f434c153
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034691"
---
# <a name="changes-to-teams-bot-apis-for-fetching-team-and-chat-members"></a>Änderungen an Teams-Bot-APIs zum Abrufen von Team- und Chatmitgliedern

>[!NOTE]
> Wir haben mit dem Veraltetkeitsprozess für und `TeamsInfo.getMembers` `TeamsInfo.GetMembersAsync` APIs begonnen. Anfangs werden sie auf 5 Anforderungen pro Minute stark gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Dies führt dazu, dass der vollständige Dienstplan nicht zurückgegeben wird, wenn die Teamgröße zunimmt. 
> 
> **Sie müssen auf Version 4.10** oder höher des Bot Framework SDK aktualisieren und zu den paginierten API-Endpunkten oder der API mit einem `TeamsInfo.GetMemberAsync` einzelnen Benutzer wechseln. Dies gilt auch für Ihren Bot, auch wenn Sie diese APIs nicht direkt verwenden, da ältere SDKs diese APIs während [membersAdded-Ereignissen](../bots/how-to/conversations/subscribe-to-conversation-events.md#team-members-added) aufrufen. Informationen zum Anzeigen der Liste anstehender Änderungen finden Sie unter [API-Änderungen](team-chat-member-api-changes.md#api-changes). 

Derzeit verwenden Botentwickler, die Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abrufen möchten, die Microsoft Teams-Bot-APIs `TeamsInfo.GetMembersAsync` (für C#) oder `TeamsInfo.getMembers` (für TypeScript/Node.js)-APIs [(hier dokumentiert).](../bots/how-to/get-teams-context.md#fetching-the-roster-or-user-profile) Diese APIs haben heute mehrere Nachteile:

* **Bei großen Teams ist die Leistung schlecht, und Timeouts sind wahrscheinlicher.** Die maximale Teamgröße ist seit der Released von Microsoft Teams Anfang 2017 erheblich angezogen. Da die gesamte Mitgliederliste zurückgegeben wird, dauert es lange, bis der API-Aufruf für große Teams zurückgegeben wird, und es ist nicht ungewöhnlich, dass für den Aufruf ein Zeit-Out durchgeführt wird, und Sie müssen es erneut `GetMembersAsync` / `getMembers` versuchen.
* **Das Abrufen von Profildetails für einen einzelnen Benutzer ist umständlich.** Um die Profilinformationen für einen einzelnen Benutzer abzurufen, müssen Sie die gesamte Mitgliederliste abrufen und dann nach der gesuchten suchen. True, es gibt eine Hilfsfunktion im Bot Framework SDK, um es einfacher zu machen, aber unter den Abdeckungen ist es nicht effizient.

Mit der Einführung organisationsweiter Teams wurde uns klar, dass es an der Zeit war, diese APIs besser an Office 365-Datenschutzsteuerelementen auszurichten: Bots, die in großen Teams verwendet werden, können grundlegende Profilinformationen abrufen, die der `User.ReadBasic.All` Microsoft Graph-Berechtigung ähneln. Mandantenadministratoren haben eine große Kontrolle darüber, welche Apps und Bots in ihrem Mandanten verwendet werden können, aber diese Einstellungen unterscheiden sich von denen für Microsoft Graph.

Hier sehen Sie eine Beispiel-JSON-Darstellung der heute von diesen APIs zurückgegebenen. Ich verweise auf einige der folgenden Felder.

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
Hier sind die anstehenden API-Änderungen:

* Wir haben eine neue API zum [`TeamsInfo.GetPagedMembersAsync`](../bots/how-to/get-teams-context.md#fetching-the-roster-or-user-profile) Abrufen von Profilinformationen für Mitglieder eines Chats/Teams erstellt. Diese API ist jetzt mit dem Bot Framework 4.10 SDK verfügbar. Für die Entwicklung in allen anderen Versionen verwenden Sie die [`GetConversationPagedMembers`](/dotnet/api/microsoft.bot.connector.conversationsextensions.getconversationpagedmembersasync?view=botbuilder-dotnet-stable&preserve-view=true) Methode. 
  > [!NOTE]
  > In v3 oder v4 besteht die beste Aktion im Upgrade auf die neueste Punktversion. 
* Wir haben eine neue API zum Abrufen der [`TeamsInfo.GetMemberAsync`](../bots/how-to/get-teams-context.md#get-single-member-details) Profilinformationen für einen einzelnen Benutzer erstellt. Es verwendet die ID des Teams/Chats und einen [UPN](https://docs.microsoft.com/windows/win32/ad/naming-properties#userprincipalname) ( , siehe `userPrincipalName` *oben*), Azure Active Directory-Objekt-ID ( , siehe oben ) oder die `objectId` Teams-Benutzer-ID ( , siehe oben ) als Parameter und gibt die Profilinformationen für diesen Benutzer `id` zurück.  
  > [!NOTE]
  > Wir ändern uns so, dass sie dem entsprechen, was im Objekt einer `objectId` `aadObjectId` Bot `Activity` Framework-Nachricht aufgerufen wird. Die neue API ist mit Version 4.10 des Bot Framework SDK verfügbar. Es wird bald auch in der Teams SDK-Erweiterung Bot Framework 3.x verfügbar sein. Mittlerweile können Sie den [REST-Endpunkt](../bots/how-to/get-teams-context.md?get-single-member-details) verwenden.
* `TeamsInfo.GetMembersAsync` (C#) und (TypeScript/Node.js) sind formal veraltet und funktionieren Ende `TeamsInfo.getMembers` 2021 nicht mehr. Aktualisieren Sie Ihre Bots so, dass sie die seitenseitigen APIs verwenden. (Dies gilt auch für die [zugrunde liegende REST-API, die diese APIs verwenden.)](../bots/how-to/get-teams-context.md)
* Bis Ende 2021 können Bots die Eigenschaften oder für Mitglieder eines Chats/Teams nicht proaktiv abrufen und müssen Microsoft Graph zum Abrufen `userPrincipalName` `email` verwenden. Insbesondere werden eigenschaften nicht von der neuen API zurückgegeben, die `userPrincipalName` `email` Ende `GetConversationPagedMembers` 2021 beginnt. Bots müssen Microsoft Graph mit einem Zugriffstoken verwenden, um diese Informationen abzurufen. Dies ist natürlich eine wesentliche Änderung: Wir müssen es Bots erleichtern, ein Zugriffstoken zu erhalten, und wir müssen den Zustimmungsprozess für Endbenutzer optimieren und vereinfachen.

## <a name="feedback-and-more-information"></a>Feedback und weitere Informationen
Wir verwenden diese Seite, um aktuelle Informationen zu diesen Änderungen zur Verfügung zu haben. Wenn Sie Fragen haben, verwenden Sie den Abschnitt "Feedback senden > auf dieser Seite" im **Abschnitt Feedback** unten. 
