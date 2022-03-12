---
title: Aktuelle Ansichten
description: Erfahren Sie mehr über aktuelle Ansichten mit universellem Bot mit Codebeispielen
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Genehmigungsbasiskarte ablehnen adaptiv
ms.openlocfilehash: 3eea8e3c08927ab797525a10f59774410197d0e1
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453733"
---
# <a name="up-to-date-cards"></a>Aktuelle Karten

Jetzt können Sie Ihren Benutzern auf adaptiven Karten die neuesten Informationen zur Verfügung stellen. Fügen Sie eine Kombination aus Aktualisierungs- und Nachrichtenbearbeitungen in Teams ein. Aktualisieren Sie die benutzerspezifischen Ansichten dynamisch auf den neuesten Status, wenn eine Änderung für Ihren Dienst vorliegt. Aktualisieren Sie z. B. für Projektmanagement- oder Ticketkarten Kommentare und den Aufgabenstatus. Für Genehmigungen wird der neueste Status widergespiegelt, während auch differenzierte Informationen und Aktionen bereitgestellt werden.

Beispielsweise kann ein Benutzer in einer Teams Unterhaltung eine Objektgenehmigungsanforderung erstellen. Alex erstellt eine Genehmigungsanforderung und weist sie Megan und Nestor zu. Im Folgenden werden die beiden Teile zum Erstellen der Genehmigungsanforderung aufgeführt:

* Benutzerspezifische Ansichten können mithilfe der `refresh` Eigenschaft der adaptiven Karten angewendet werden.
Mit benutzerspezifischen Ansichten kann eine Karte mit den Schaltflächen **"Genehmigen"** oder " **Ablehnen** " für eine Gruppe von Benutzern und eine Karte ohne diese Schaltflächen für andere Benutzer angezeigt werden.

* Um den Kartenstatus immer auf dem neuesten Stand zu halten, kann Teams Mechanismus zum Bearbeiten von Nachrichten verwendet werden. Beispielsweise kann der Bot bei jeder Genehmigung eine Nachrichtenbearbeitung für alle Benutzer auslösen. Diese Bot-Nachrichtenbearbeitung löst eine `adaptiveCard/action` Aufrufanforderung für alle Benutzer der automatischen Aktualisierung aus, auf die der Bot mit der aktualisierten benutzerspezifischen Karte antworten kann.

Weitere Informationen finden Sie unter ["Bearbeiten einer Botnachricht"](/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).

## <a name="approval-base-card"></a>Genehmigungsbasiskarte

Der folgende Code enthält ein Beispiel für eine Genehmigungsbasiskarte:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>", "<Nestor's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan and Nestor**"
    }
  ]
}
```

## <a name="approval-card-with-approve-and-reject-buttons"></a>Genehmigungskarte mit Schaltflächen "Genehmigen" und "Ablehnen"

Der folgende Code enthält ein Beispiel für eine Genehmigungskarte mit den Schaltflächen **"Genehmigen"** und " **Ablehnen** ":

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Nestor's user MRI>", "<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Approval Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan and Nestor**"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Approve",
      "verb": "approve",
      "data": {
            "more info": "<more info>"
      }
    },
    {
      "type": "Action.Execute",
      "title": "Reject",
      "verb": "reject",
      "data": {
            "more info": "<more info>"
      }
    }
  ]
}
```

Im Folgenden sind die beiden Rollen aufgeführt, die Benutzern je nach Genehmigungsanforderung angezeigt werden:

* Genehmigungsbasiskarte: Wird Benutzern angezeigt, die nicht Teil der Liste der Genehmiger sind und die Anforderung noch nicht genehmigt oder abgelehnt wurde, und nicht Teil der `userIds` Liste in `refresh` eigenschaft des JSON-Codes für adaptive Karten.
* Genehmigungskarte mit Schaltflächen **"Genehmigen"** oder **"Ablehnen** ": Wird den Benutzern angezeigt, die Teil der Liste der genehmigeren Personen sind, und der `userIds` Liste in der `refresh` Eigenschaft des JSON-Codes für adaptive Karten.

So senden Sie die Anforderung zur Genehmigung des Objekts:

1. Alex löst in einer Teams Unterhaltung eine Anforderung zur Genehmigung von Ressourcen aus und weist sie Megan und Nestor zu.
2. Bot sendet die Genehmigungsbasiskarte in der Unterhaltung.
3. Alle anderen Benutzer in der Unterhaltung sehen die vom Bot gesendete Karte. Die automatische Aktualisierung wird für Megan und Nestor ausgelöst, die nun die benutzerspezifische Karte mit den Schaltflächen **"Genehmigen"** oder **"Ablehnen** " sehen, da ihre Benutzer-MRIs der `userIds` Liste in der `refresh` Eigenschaft der adaptiven Karte hinzugefügt werden.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Benutzerspezifische Ansichten":::

4. Nestor wählt die Schaltfläche **"Genehmigen"** aus, die mit `Action.Execute`. Der Bot erhält eine `adaptiveCard/action` Aufrufanforderung, auf die er als Antwort eine adaptive Karte zurückgeben kann.
5. Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, die besagt, dass Nestor die Anforderung genehmigt hat, während Megans Genehmigung aussteht.
6. Die Bearbeitung von Bot-Nachrichten löst eine automatische Aktualisierung für Megan aus, und sie sieht die aktualisierte benutzerspezifische Karte, die besagt, dass Nestor die Anforderung genehmigt hat, aber auch die Schaltflächen **"Genehmigen"** oder **"Ablehnen** " sieht. Die Benutzer-MRI von Nestor wird in den Schritten 4 und 5 aus der `userIds` Liste in `refresh` der Eigenschaft dieses JSON-Codes für adaptive Karten entfernt. Jetzt wird die automatische Aktualisierung nur für Megan ausgelöst.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

7. Jetzt wählt Megan die Schaltfläche **"Genehmigen"** aus, die mit `Action.Execute`eingeschaltet wird. Der Bot erhält eine `adaptiveCard/action` Aufrufanforderung, auf die er als Antwort eine adaptive Karte zurückgeben kann.
8. Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, die besagt, dass Nestor und Megan die Anforderung genehmigt haben.
9. Die Bearbeitung von Bot-Nachrichten löst keine automatische Aktualisierung aus. Megans Benutzer-MRI wird in den Schritten 7 und 8 ebenfalls aus der `userIds` Liste in `refresh` der Eigenschaft dieses JSON-Codes für adaptive Karten entfernt.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Aktuelle Ansichten":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a>Adaptive Karte, die als Antwort von `adaptiveCard/action` und `message edit`

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort auf `adaptiveCard/action` und `message edit` für die Schritte 4 und 5 gesendet werden:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor**"
    }
  ]
}
```

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Reaktion auf den `adaptiveCard/action` Aufruf über die automatische Aktualisierung für Schritt 6 gesendet werden:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Approval Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor**"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Approve",
      "verb": "approve",
      "data": {
            "more info": "<more info>"
      }
    },
    {
      "type": "Action.Execute",
      "title": "Reject",
      "verb": "reject",
      "data": {
            "more info": "<more info>"
      }
    }
  ]
}
```

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort auf `adaptiveCard/action` und `message edit` für die Schritte 7 und 8 gesendet werden:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": []
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor and Megan**"
    }
  ]
}
```

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Sequenzielle Workflows adaptive Karten | Vorführen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Benutzerspezifische Ansichten](User-Specific-Views.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
