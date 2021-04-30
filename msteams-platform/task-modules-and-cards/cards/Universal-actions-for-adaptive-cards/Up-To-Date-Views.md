---
title: Aktuelle Ansichten
description: Beispiel für aktuelle Ansichten mithilfe von Universal Bot
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 2027d07961929fb40e7afc3ee268e1267b235a02
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088888"
---
# <a name="up-to-date-cards"></a>Aktuelle Karten

Sie können Ihren Benutzern jetzt aktuelle Informationen zu adaptiven Karten mit einer Kombination aus Aktualisierungs- und Nachrichtenbearbeitungen in Teams. Dadurch können Sie die benutzerspezifischen Ansichten dynamisch auf den neuesten Status aktualisieren, wenn eine Änderung an Ihrem Dienst vor sich geht. Bei Projektverwaltungs- oder Ticketkarten können Sie beispielsweise Kommentare und den Status der Aufgabe aktualisieren. Bei Genehmigungen wird der neueste Zustand widersspiegelt und gleichzeitig differenzierte Informationen und Aktionen zur Verfügung stellt.

Beispielsweise kann ein Benutzer eine Anforderung zur Anlagengenehmigung in einer Teams erstellen. Alex erstellt eine Genehmigungsanforderung und weist sie Megan und Nestor zu. Es folgen die beiden Teile zum Erstellen der Genehmigungsanforderung:

* Benutzerspezifische Ansichten können mithilfe der Eigenschaft der `refresh` adaptiven Karten genutzt werden.
Mithilfe benutzerspezifischer Ansichten kann  eine  Karte mit Den Schaltflächen Genehmigen oder Ablehnen für eine Gruppe von Benutzern und eine Karte ohne diese Schaltflächen für andere Benutzer angezeigt werden.

* Um den Kartenstatus immer auf dem neuesten Stand zu halten, Teams Nachrichtenbearbeitungsmechanismus genutzt werden. Jedes Mal, wenn eine Genehmigung vor liegt, kann der Bot beispielsweise eine Nachrichtenbearbeitung für alle Benutzer auslösen. Diese Botnachrichtenbearbeitung löst eine Aufrufanforderung für alle Benutzer der automatischen Aktualisierung aus, auf die der Bot mit der aktualisierten `adaptiveCard/action` benutzerspezifischen Karte antworten kann.

Weitere Informationen finden Sie unter [How to do a bot message edit](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).

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

## <a name="approval-card-with-approve-and-reject-buttons"></a>Genehmigungskarte mit Schaltflächen Genehmigen und Ablehnen

Der folgende Code enthält ein Beispiel für eine Genehmigungskarte mit den Schaltflächen **Genehmigen** **und Ablehnen:**

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

Es folgen die beiden Rollen, die Benutzern in Abhängigkeit von ihrer Beteiligung an der Genehmigungsanforderung angezeigt werden:

* Genehmigungsbasiskarte: Wird Benutzern angezeigt, die nicht Teil der Liste genehmiger Personen sind und die Anforderung noch nicht genehmigt oder abgelehnt haben und nicht Teil der Liste in der Eigenschaft der `userIds` `refresh` adaptiven Karten-JSON sind.
* Genehmigungskarte mit  **Den** Schaltflächen Genehmigen oder Ablehnen: Wird den Benutzern angezeigt, die Teil der Liste genehmiger Personen sind, und der Liste in der Eigenschaft des `userIds` `refresh` JSON für adaptive Karten.

**So senden Sie die Anforderung zur Anlagengenehmigung**

1. Alex löst eine Anforderung zur Anlagengenehmigung in einer Teams aus und weist sie Megan und Nestor zu.
2. Bot sendet die Genehmigungsbasiskarte in der Unterhaltung.
3. Alle anderen Benutzer in der Unterhaltung sehen die vom Bot gesendete Karte. Die automatische Aktualisierung wird für Megan und Nestor ausgelöst,  denen nun die benutzerspezifische Karte mit den Schaltflächen **Genehmigen** oder Ablehnen angezeigt wird, da ihre Benutzer-MRIs der Liste in der Eigenschaft der adaptiven Karte hinzugefügt `userIds` `refresh` werden.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Benutzerspezifische Ansichten":::

4. Nestor wählt die Schaltfläche **Genehmigen** aus, die mit betrieben `Action.Execute` wird. Der Bot ruft eine `adaptiveCard/action` Aufrufanforderung ab, an die er als Antwort eine adaptive Karte zurückgeben kann.
5. Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, auf der nestor die Anforderung genehmigt hat, während Megans Genehmigung aussteht.
6. Die Bot-Nachrichtenbearbeitung löst eine automatische Aktualisierung für Megan aus, und ihr wird die aktualisierte  benutzerspezifische Karte angezeigt, auf der nestor die Anforderung genehmigt hat, aber auch die Schaltflächen Genehmigen oder Ablehnen **angezeigt** wird. Die Benutzer-MRT von Nestor wird in den Schritten 4 und 5 aus der Liste in der Eigenschaft dieses JSON für adaptive Karten `userIds` `refresh` entfernt. Jetzt wird die automatische Aktualisierung nur für Megan ausgelöst.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

7. Megan wählt nun die Schaltfläche **Genehmigen** aus, die mit betrieben `Action.Execute` wird. Der Bot ruft eine `adaptiveCard/action` Aufrufanforderung ab, an die er als Antwort eine adaptive Karte zurückgeben kann.
8. Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, die nestor und Megan die Anforderung genehmigt haben.
9. Die Botnachrichtenbearbeitung löst keine automatische Aktualisierung aus. Megans Benutzer-MRI wird auch in der Eigenschaft dieser adaptiven Karten-JSON in den Schritten `userIds` `refresh` 7 und 8 aus der Liste entfernt.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Aktuelle Ansichten":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a>Adaptive Karte, die als Antwort von und gesendet `adaptiveCard/action` wird `message edit`

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort auf und für die `adaptiveCard/action` `message edit` Schritte 4 und 5 gesendet werden:

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

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Reaktion auf den Aufruf durch `adaptiveCard/action` automatische Aktualisierung für Schritt 6 gesendet werden:

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

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort auf und für die Schritte `adaptiveCard/action` `message edit` 7 und 8 gesendet werden:

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

## <a name="see-also"></a>Siehe auch

* [Arbeiten mit universellen Aktionen für adaptive Karten](Work-with-universal-actions-for-adaptive-cards.md)
* [Benutzerspezifische Ansichten](User-Specific-Views.md)
