---
title: Mit Universal-Aktionen für adaptive Karten arbeiten
description: Informationen zum Arbeiten mit den universellen Aktionen für adaptive Karten, einschließlich Schema für UniversalActions für adaptive Karten, Aktualisierungsmodell und Abwärtskompatibilität
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 17dd7fd611c593c3f5de0237e0aa61885ac630c0
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143879"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a>Mit Universal-Aktionen für adaptive Karten arbeiten

Universal-Aktionen für adaptive Karten bieten eine Möglichkeit zum Implementieren adaptiver Kartenszenarien für Teams und Outlook. In diesem Dokument werden folgende Themen behandelt:

* [Schema, das für Universal-Aktionen für adaptive Karten verwendet wird](#schema-for-universal-actions-for-adaptive-cards)
* [Aktualisierungsmodell](#refresh-model)
* [`adaptiveCard/action` Aufrufaktivität](#adaptivecardaction-invoke-activity)
* [Abwärtskompatibilität](#backward-compatibility)

## <a name="quick-start-guide-to-use-universal-actions-for-adaptive-cards-in-teams"></a>Schnellstarthandbuch zur Nutzung von Universal-Aktionen für adaptive Karten in Teams

1. Ersetzen Sie alle Instanzen von `Action.Submit` durch `Action.Execute`, um ein vorhandenes Szenario in Teams zu aktualisieren.
2. Fügen Sie Ihrer adaptiven Karte eine `refresh`-Klausel hinzu, wenn Sie das Modell für die automatische Aktualisierung nutzen möchten oder wenn Ihr Szenario benutzerspezifische Ansichten erfordert.

    >[!NOTE]
    > Geben Sie die `userIds` Eigenschaft an, um zu identifizieren, welche Benutzer automatische Updates erhalten.

3. Verarbeiten Sie `adaptiveCard/action` Aufrufanforderungen in Ihrem Bot.
4. Verwenden Sie den Kontext der Aufrufanforderung, um mit Karten zu antworten, die für einen Benutzer erstellt wurden.

    > [!NOTE]
    > Wenn Ihr Bot als Ergebnis der Verarbeitung eines `Action.Execute` eine neue Karte zurückgibt, muss die Antwort dem Antwortformat entsprechen.

## <a name="schema-for-universal-actions-for-adaptive-cards"></a>Schema für Universal-Aktionen für adaptive Karten

Universal-Aktionen für adaptive Karten werden in der Adaptive Karten-Schemaversion 1.4 eingeführt. Um adaptive Karten effektiv verwenden zu können, muss die `version`-Eigenschaft Ihrer adaptiven Karte auf 1.4 festgelegt werden.

> [!NOTE]
> Wenn Sie die `version`-Eigenschaft auf 1.4 festlegen, ist Ihre adaptive Karte nicht mit älteren Clients der Plattformen oder Anwendungen wie Outlook und Teams kompatibel, da sie die Universal-Aktionen für adaptive Karten nicht unterstützen.

Wenn Sie die Kartenversion auf eine niedrigere Version als 1.4 festlegen und entweder die `refresh`-Eigenschaft oder `Action.Execute` verwenden, geschieht Folgendes:

| Client | Verhalten |
| :-- | :-- |
| Microsoft Teams | Ihre Karte funktioniert nicht mehr. Die Karte wird nicht aktualisiert, und `Action.Execute` wird nicht abhängig von der Version des Teams-Clients gerendert. Um maximale Kompatibilität in Teams sicherzustellen, definieren Sie `Action.Execute` mit einem `Action.Submit` in der Fallbackeigenschaft. |

Weitere Informationen zur Unterstützung älterer Clients finden Sie unter [Abwärtskompatibilität](#backward-compatibility).

### <a name="actionexecute"></a>Action.Execute

Ersetzen Sie beim Erstellen von adaptive Karten `Action.Submit` und `Action.Http` durch `Action.Execute`. Das Schema für `Action.Execute` ähnelt dem von `Action.Submit`.

Weitere Informationen finden Sie unter [Action.Execute-Schema und -Eigenschaften](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Jetzt können Sie das Aktualisierungsmodell verwenden, damit Adaptive Karten automatisch aktualisiert werden können.

## <a name="refresh-model"></a>Aktualisierungsmodell

Um Ihre adaptive Karte automatisch zu aktualisieren, definieren Sie ihre `refresh`-Eigenschaft, die eine Aktion vom Typ `Action.Execute` und ein `userIds`-Array einbettet.

Weitere Informationen finden Sie unter [Aktualisieren von Schemas und Eigenschaften](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).

## <a name="user-ids-in-refresh"></a>Benutzer-IDs, die aktualisiert werden

Im Folgenden sind die Features von UserIds aufgeführt, die aktualisiert werden:

* UserIds ist ein Array von Benutzer-MRIs, das Teil der `refresh`-Eigenschaft in „Adaptive Karten“ ist.

* Wenn die `userIds`-Listeneigenschaft als `userIds: []` im Aktualisierungsabschnitt der Karte angegeben ist, wird die Karte nicht automatisch aktualisiert. Stattdessen wird dem Benutzer im Dreifachpunktmenü in Teams Webclient oder Desktop eine Option "**Karte aktualisieren**" angezeigt, und im Kontextmenü für langes Drücken in Teams Mobilen, d. h. Android oder iOS, um die Karte manuell zu aktualisieren. Alternativ können Sie die Aktualisierungseigenschaft vollständig überspringen`userIds`, falls das Szenario <=60 Mitglieder in Teams Gruppenchats oder -kanälen umfasst. Der Teams-Client ruft automatisch Aktualisierungsaufrufe für alle Benutzer auf, wenn die Gruppe oder der Kanal über <=60 Benutzer verfügt.

* Die UserIds-Eigenschaft wird hinzugefügt, da Kanäle in Teams eine große Anzahl von Mitgliedern enthalten können. Wenn alle Mitglieder den Kanal gleichzeitig anzeigen, führt eine bedingungslose automatische Aktualisierung zu vielen gleichzeitigen Aufrufen des Bots. Die `userIds`-Eigenschaft muss immer eingeschlossen werden, um zu identifizieren, welche Benutzer eine automatische Aktualisierung erhalten müssen. Dabei gilt ein Limit von maximal *60 (sechzig) Benutzer-MRIs*.

* Sie können die Benutzer-MRIs eines Teams-Unterhaltungsmitglieds abrufen. Weitere Informationen dazu, wie Sie sie in der Liste "userIds" im Aktualisierungsabschnitt der adaptiven Karte hinzufügen, finden Sie unter [Abrufen der Liste oder des Benutzerprofils](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).

 Sie können die Benutzer-MRI für einen Kanal, Gruppenchat oder 1:1-Chat mithilfe des folgenden Beispiels abrufen:

 1. Verwenden von TurnContext  

     `userMRI= turnContext.Activity.From.Id`

 1. Verwenden der GetMemberAsync-Methode
  
     `var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);var userMRI = member.Id;`

* MRI des Teams-Beispielbenutzers ist `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`

> [!NOTE]
> Die `userIds`-Eigenschaft wird in Outlook ignoriert, und die `refresh`-Eigenschaft wird immer automatisch aktiviert. Es gibt kein Skalierungsproblem in Outlook, da Benutzer die Karte zu unterschiedlichen Zeiten anzeigen.

Der nächste Schritt besteht darin, die `adaptiveCard/action`-Aufrufaktivität zu verwenden, um zu verstehen, welche Anforderung ausgeführt werden muss, nachdem `Action.Execute` ausgeführt wurde.

## <a name="adaptivecardaction-invoke-activity"></a>`adaptiveCard/action` Aufrufaktivität

Wenn `Action.Execute` im Client ausgeführt wird, wird ein neuer Typ von Aufrufaktivität `adaptiveCard/action` für Ihren Bot erstellt.

Weitere Informationen finden Sie unter [Anforderungsformat und -eigenschaften für eine typische `adaptiveCard/action`-Aufrufaktivität](/adaptive-cards/authoring-cards/universal-action-model#request-format).

Weitere Informationen finden Sie unter [Antwortformat und -eigenschaften für eine typische `adaptiveCard/action`-Aufrufaktivität mit unterstützten Antworttypen](/adaptive-cards/authoring-cards/universal-action-model#response-format).

Als Nächstes können Sie Abwärtskompatibilität auf ältere Clients auf verschiedenen Plattformen anwenden und Ihre adaptive Karte kompatibel machen.

## <a name="backward-compatibility"></a>Abwärtskompatibilität

Mit Universal-Aktionen für adaptive Karten können Sie Eigenschaften festlegen, die Abwärtskompatibilität mit älteren Versionen von Outlook und Teams ermöglichen.

### <a name="teams"></a>Teams

Um die Abwärtskompatibilität Ihrer adaptiven Karten mit älteren Versionen von Teams sicherzustellen, müssen Sie die `fallback`-Eigenschaft einschließen und ihren Wert auf `Action.Submit` festlegen. Außerdem muss Ihr Botcode sowohl `Action.Execute` als auch `Action.Submit` verarbeiten.

Weitere Informationen finden Sie unter [Abwärtskompatibilität in Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).

## <a name="code-samples"></a>Codebeispiele

|Beispielname | Beschreibung | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Teams-Catering-Bot | Erstellen Sie einen Bot, der mit adaptiven Karten eine Bestellung annimmt. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| Noch nicht verfügbar |
| Adaptive Karten für sequenzielle Workflows | Veranschaulichen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Ansicht](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) .|

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Sequenzielle Workflows](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/sequential-workflows.md)
* [Aktuelle Karten](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/up-to-date-views.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
