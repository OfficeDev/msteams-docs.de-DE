---
title: Mit Universal-Aktionen für adaptive Karten arbeiten
description: Arbeiten Sie mit den universellen Aktionen für adaptive Karten.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4361f1c7774837b728c6382df4e62e00ea912e35
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649699"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a>Mit Universal-Aktionen für adaptive Karten arbeiten

Universelle Aktionen für adaptive Karten bieten eine Möglichkeit, adaptive Kartenszenarien sowohl für Teams als auch für Outlook. Dieses Dokument behandelt Folgendes:

* [Schema für universelle Aktionen für adaptive Karten](#schema-for-universal-actions-for-adaptive-cards)
* [Aktualisierungsmodell](#refresh-model)
* [`adaptiveCard/action` Aufrufen der Aktivität](#adaptivecardaction-invoke-activity)
* [Abwärtskompatibilität](#backward-compatibility)

## <a name="quick-start-guide-to-leverage-universal-actions-for-adaptive-cards-in-teams"></a>Schnellstartanleitung zur Nutzung universeller Aktionen für adaptive Karten in Teams

1. Ersetzen Sie alle Instanzen `Action.Submit` von `Action.Execute` durch, um ein vorhandenes Szenario auf Teams.
2. Fügen Sie Ihrer adaptiven Karte eine Klausel hinzu, wenn Sie das automatische Aktualisierungsmodell nutzen möchten oder wenn für Ihr Szenario `refresh` benutzerspezifische Ansichten erforderlich sind.

    >[!NOTE]
    > Geben Sie die `userIds` zu identifizierende Eigenschaft an, welche Benutzer automatische Updates erhalten.

3. Behandeln `adaptiveCard/action` sie Aufrufanforderungen in Ihrem Bot.
4. Verwenden Sie den Kontext der Aufrufanforderung, um mit Karten zurück zu antworten, die speziell für einen Benutzer erstellt wurden.

    > [!NOTE]
    > Wenn Ihr Bot eine neue Karte als Ergebnis der Verarbeitung einer zurückgibt, muss die Antwort `Action.Execute` dem Antwortformat entsprechen.

## <a name="schema-for-universal-actions-for-adaptive-cards"></a>Schema für universelle Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten werden im Schema adaptiver Karten, Version 1.4, eingeführt. Um adaptive Karte effektiv zu verwenden, muss die Eigenschaft Ihrer adaptiven Karte `version` auf 1,4 festgelegt sein.

> [!NOTE]
> Wenn Sie die Eigenschaft auf 1,4 festlegen, ist Ihre adaptive Karte mit älteren Clients der Plattformen oder Anwendungen wie Outlook und Teams nicht kompatibel, da sie die universellen Aktionen für adaptive Karten nicht `version` unterstützen.

Wenn Sie die Kartenversion auf kleiner als 1.4 festlegen und entweder oder beides, Eigenschaft und verwenden, geschieht `refresh` `Action.Execute` Folgendes:

| Client | Verhalten |
| :-- | :-- |
| Teams | Ihre Karte funktioniert nicht mehr. Die Karte wird nicht aktualisiert und wird in Abhängigkeit von der Version des Teams `Action.Execute` gerendert. Um maximale Kompatibilität in Teams zu gewährleisten, definieren `Action.Execute` Sie mit einer in der `Action.Submit` Fallback-Eigenschaft. |

Weitere Informationen zur Unterstützung älterer Clients finden Sie unter [Abwärtskompatibilität](#backward-compatibility).

### <a name="actionexecute"></a>Action.Execute

Ersetzen Sie beim Erstellen adaptiver Karten `Action.Submit` und `Action.Http` durch `Action.Execute` . Das Schema für `Action.Execute` ähnelt dem von `Action.Submit` .

Weitere Informationen finden Sie unter [Action.Exeschema and properties](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Jetzt können Sie das Aktualisierungsmodell verwenden, damit adaptive Karten automatisch aktualisiert werden können.

## <a name="refresh-model"></a>Aktualisierungsmodell

Um Ihre adaptive Karte automatisch zu aktualisieren, definieren Sie ihre Eigenschaft, die eine Aktion vom Typ und `refresh` `Action.Execute` ein Array `userIds` einbettet.

Weitere Informationen finden Sie unter [Aktualisierungsschema und Eigenschaften](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).

## <a name="user-ids-in-refresh"></a>Benutzer-IDs in der Aktualisierung

Im Folgenden sind die Features von UserIds in refresh zu finden:

* UserIds ist ein Array von MrI des Benutzers, das Teil der `refresh` Eigenschaft in Adaptive Karten ist.

* Wenn die List-Eigenschaft wie im Abschnitt "Aktualisieren" der Karte angegeben ist, wird die Karte `userIds` `userIds: []` nicht automatisch aktualisiert. Stattdessen wird  dem Benutzer eine Option Karte aktualisieren im Dreipunktmenü im Web oder Desktop und im kontextbezogenen Long-Press-Menü in Mobile angezeigt, d. h. Android oder iOS, um die Karte manuell zu aktualisieren.

* Die UserIds-Eigenschaft wird hinzugefügt, da Kanäle in Teams eine große Anzahl von Mitgliedern enthalten können. Wenn alle Mitglieder den Kanal gleichzeitig anzeigen, führt eine bedingungslose automatische Aktualisierung zu vielen gleichzeitigen Aufrufen des Bots. Um dies zu vermeiden, muss die Eigenschaft immer enthalten sein, um zu ermitteln, welche Benutzer eine automatische Aktualisierung mit maximal `userIds` *60 (60) Benutzer-MRIs erhalten müssen.*

* Weitere Informationen zum Abrufen Teams Benutzer-MRIs des Unterhaltungsmitglieds zum Hinzufügen in die UserIds-Liste im Abschnitt Aktualisierung von Adaptive Karte finden Sie unter [Fetch roster or user profile](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).

* Beispiel für Teams benutzer-MRI ist`29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`

> [!NOTE]
> Die `userIds` Eigenschaft wird in Outlook ignoriert, und die Eigenschaft wird immer automatisch `refresh` aktiviert. Es gibt kein Skalierungsproblem in Outlook, da Benutzer die Karte zu unterschiedlichen Zeiten anzeigen.

Im nächsten Schritt verwenden Sie die Aufrufaktivität, um zu verstehen, welche Anforderung nach der `adaptiveCard/action` Ausführung gestellt werden `Action.Execute` muss.

## <a name="adaptivecardaction-invoke-activity"></a>`adaptiveCard/action` Aufrufen der Aktivität

Wenn sie im Client ausgeführt wird, wird ihrem Bot eine neue `Action.Execute` Art von `adaptiveCard/action` Invoke-Aktivität vorgenommen.

Weitere Informationen finden Sie unter [Anforderungsformat und Eigenschaften für eine typische `adaptiveCard/action` Aufrufaktivität](/adaptive-cards/authoring-cards/universal-action-model#request-format).

Weitere Informationen finden Sie unter [Antwortformat und Eigenschaften für eine typische `adaptiveCard/action` Aufrufaktivität mit unterstützten Antworttypen](/adaptive-cards/authoring-cards/universal-action-model#response-format).

Als Nächstes können Sie die Abwärtskompatibilität auf ältere Clients über verschiedene Plattformen hinweg anwenden und Ihre adaptive Karte kompatibel machen.

## <a name="backward-compatibility"></a>Abwärtskompatibilität

Mit universellen Aktionen für adaptive Karten können Sie Eigenschaften festlegen, die die Abwärtskompatibilität mit älteren Versionen von Outlook und Teams.

### <a name="teams"></a>Teams

Um die Abwärtskompatibilität Ihrer adaptiven Karten mit älteren Versionen von Teams sicherzustellen, müssen Sie die Eigenschaft enthalten und `fallback` den Wert auf `Action.Submit` festlegen. Außerdem muss Ihr Botcode sowohl als auch `Action.Execute` `Action.Submit` verarbeiten.

Weitere Informationen finden Sie unter [Abwärtskompatibilität auf Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | . NETCore |
|----------------|-----------------|--------------|
| Teams-Catering-Bot | Erstellen Sie einen einfachen Bot, der die Essensbestellung mit adaptiven Karten akzeptiert. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a>Siehe auch

* [Adaptive Kartenaktionen in Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Wie Bots funktionieren](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
