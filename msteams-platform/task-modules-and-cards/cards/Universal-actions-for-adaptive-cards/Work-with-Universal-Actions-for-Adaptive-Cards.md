---
title: Mit Universal-Aktionen für adaptive Karten arbeiten
description: Mit Universal-Aktionen für adaptive Karten arbeiten.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 426e1324f0ccc113d7fd0f16ef38ca8558148541
ms.sourcegitcommit: 6a41c529a423c81a184c7a79125dbaaed0179788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2021
ms.locfileid: "53586040"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a>Mit Universal-Aktionen für adaptive Karten arbeiten

Universelle Aktionen für adaptive Karten bieten eine Möglichkeit zum Implementieren adaptiver Kartenszenarien sowohl für Teams als auch für Outlook. Dieses Dokument behandelt die folgenden Themen:

* [Schema, das für Universal-Aktionen für adaptive Karten verwendet wird](#schema-for-universal-actions-for-adaptive-cards)
* [Aktualisierungsmodell](#refresh-model)
* [`adaptiveCard/action` Aufrufaktivität](#adaptivecardaction-invoke-activity)
* [Abwärtskompatibilität](#backward-compatibility)

## <a name="quick-start-guide-to-use-universal-actions-for-adaptive-cards-in-teams"></a>Schnellstartanleitung zur Verwendung von universellen Aktionen für adaptive Karten in Teams

1. Ersetzen Sie alle Instanzen von `Action.Submit` durch `Action.Execute`, um ein vorhandenes Szenario in Teams zu aktualisieren.
2. Fügen Sie ihrer adaptiven Karte eine `refresh` Klausel hinzu, wenn Sie das automatische Aktualisierungsmodell verwenden möchten oder wenn Ihr Szenario benutzerspezifische Ansichten erfordert.

    >[!NOTE]
    > Geben Sie die `userIds`-Eigenschaft an, die identifiziert werden soll, welche Benutzer automatische Updates erhalten.

3. Verarbeiten Sie `adaptiveCard/action` Aufrufanforderungen in Ihrem Bot.
4. Verwenden Sie den Kontext der Aufrufanforderung, um mit Karten zu antworten, die für einen Benutzer erstellt wurden.

    > [!NOTE]
    > Wenn Ihr Bot als Ergebnis der Verarbeitung eines `Action.Execute` eine neue Karte zurückgibt, muss die Antwort dem Antwortformat entsprechen.

## <a name="schema-for-universal-actions-for-adaptive-cards"></a>Schema für Universal-Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten werden in der Schemaversion 1.4 für adaptive Karten eingeführt. Um adaptive Karten effektiv verwenden zu können, muss die `version`-Eigenschaft Ihrer adaptiven Karte auf 1.4 festgelegt werden.

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

* UserIds ist ein Array von Benutzer-MRIs, das Teil der `refresh` Eigenschaft in adaptiven Karten ist.

* Wenn die `userIds`-Listeneigenschaft als `userIds: []` im Aktualisierungsabschnitt der Karte angegeben ist, wird die Karte nicht automatisch aktualisiert. Stattdessen wird dem Benutzer eine Option **Karte aktualisieren** im Dreifachpunktmenü im Web oder auf dem Desktop und im Kontextmenü mit langem Tastendruck auf Mobilgeräten, d. h. Android oder iOS, angezeigt, um die Karte manuell zu aktualisieren.

* Die UserIds-Eigenschaft wird hinzugefügt, da Kanäle in Teams eine große Anzahl von Mitgliedern enthalten können. Wenn alle Mitglieder den Kanal gleichzeitig anzeigen, führt eine bedingungslose automatische Aktualisierung zu vielen gleichzeitigen Aufrufen des Bots. Die `userIds` Eigenschaft muss immer eingeschlossen werden, um zu identifizieren, welche Benutzer eine automatische Aktualisierung mit maximal *60 (60) Benutzer-MRIs* erhalten müssen.

* Sie können Teams Benutzer-MRIs eines Unterhaltungsmitglieds abrufen. Weitere Informationen zum Hinzufügen der Liste "userIds" im Aktualisierungsbereich der adaptiven Karte finden Sie unter Abrufen der Teilnehmerliste oder des [Benutzerprofils.](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile)

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

Mit universellen Aktionen für adaptive Karten können Sie Eigenschaften festlegen, die die Abwärtskompatibilität mit älteren Versionen von Outlook und Teams ermöglichen.

### <a name="teams"></a>Microsoft Teams

Um die Abwärtskompatibilität Ihrer adaptiven Karten mit älteren Versionen von Teams sicherzustellen, müssen Sie die `fallback`-Eigenschaft einschließen und ihren Wert auf `Action.Submit`festlegen. Außerdem muss Ihr Botcode sowohl `Action.Execute` als auch `Action.Submit`verarbeiten.

Weitere Informationen finden Sie unter [Abwärtskompatibilität in Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).

## <a name="code-samples"></a>Codebeispiele

|Beispielname | Beschreibung | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Teams-Catering-Bot | Erstellen Sie einen Bot, der die Bestellung von Essen mithilfe adaptiver Karten akzeptiert. |[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| Noch nicht verfügbar |
| Sequenzielle Workflows adaptive Karten | Vorführen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
