---
title: Aktuelle Ansichten
description: In diesem Modul erfahren Sie mehr über aktuelle Kartenansichten mithilfe von Universal Bot mit Codebeispielen in Microsoft Teams
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 5c6f7d13cd884baf9ffbc1fd30cafb7cfab33295
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143620"
---
# <a name="up-to-date-cards"></a>Aktuelle Karten

Sie können Ihren Benutzern jetzt neueste Informationen auf adaptiven Karten bereitstellen. Fügen Sie eine Kombination aus Aktualisierungs- und Nachrichtenbearbeitungen in Teams ein. Aktualisieren Sie die benutzerspezifischen Ansichten dynamisch auf den aktuellen Status, sobald eine Änderung in Ihrem Dienst vorliegt. Aktualisieren Sie beispielsweise für Projektmanagement- oder Ticketkarten Kommentare und den Vorgangsstatus. Für Genehmigungen wird der neueste Zustand widergespiegelt und gleichzeitig differenzierte Informationen und Aktionen bereitgestellt.

Beispielsweise kann ein Benutzer eine Genehmigungsanforderung für Ressourcen in einer Teams Unterhaltung erstellen. Alex erstellt eine Genehmigungsanforderung und weist sie Megan und Nestor zu. Im Folgenden sind die beiden Teile zum Erstellen der Genehmigungsanforderung aufgeführt:

* Benutzerspezifische Ansichten können mithilfe der `refresh` Eigenschaft der adaptiven Karten angewendet werden.
Mithilfe von benutzerspezifischen Ansichten kann eine Karte mit den Schaltflächen **"Genehmigen"** oder " **Ablehnen** " für eine Gruppe von Benutzern und eine Karte ohne diese Schaltflächen für andere Benutzer angezeigt werden.

* Damit der Kartenstatus immer aktualisiert wird, kann Teams Mechanismus zum Bearbeiten von Nachrichten verwendet werden. Für jede Genehmigung kann der Bot beispielsweise eine Nachrichtenbearbeitung für alle Benutzer auslösen. Diese Bot-Nachrichtenbearbeitung löst eine `adaptiveCard/action` Aufrufanforderung für alle Benutzer der automatischen Aktualisierung aus, auf die der Bot mit der aktualisierten benutzerspezifischen Karte antworten kann.

Weitere Informationen finden Sie unter [Bearbeiten einer Bot-Nachricht](/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).

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

## <a name="approval-card-with-approve-and-reject-buttons"></a>Genehmigungskarte mit den Schaltflächen "Genehmigen" und "Ablehnen"

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

Es folgen die beiden Rollen, die Benutzern je nach Genehmigungsanforderung angezeigt werden:

* Genehmigungsbasiskarte: Wird Benutzern angezeigt, die nicht Teil der Liste der genehmigenden Personen sind, und die Anforderung ist noch nicht genehmigt oder abgelehnt und nicht Teil der Liste in `refresh` der `userIds` Eigenschaft des JSON-Codes für adaptive Karten.
* Genehmigungskarte mit den Schaltflächen **"Genehmigen"** oder " **Ablehnen** ": Wird den Benutzern angezeigt, die Teil der Liste der genehmigenden Personen sind, und der `userIds` Liste in der `refresh` Eigenschaft des JSON-Codes für adaptive Karten.

So senden Sie die Objektgenehmigungsanforderung:

1. Alex löst eine Genehmigungsanforderung für Ressourcen in einer Teams Unterhaltung aus und weist sie Megan und Nestor zu.
2. Der Bot sendet die Genehmigungsbasiskarte in der Unterhaltung.
3. Allen anderen Benutzern in der Unterhaltung wird die vom Bot gesendete Karte angezeigt. Die automatische Aktualisierung wird für Megan und Nestor ausgelöst, die jetzt die benutzerspezifische Karte mit den Schaltflächen **"Genehmigen"** oder " **Ablehnen** " sehen, wenn deren Benutzer-MRIs der `userIds` Liste in der `refresh` Eigenschaft der adaptiven Karte hinzugefügt werden.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Benutzerspezifische Ansichten":::

4. Nestor wählt die Schaltfläche **"Genehmigen** " aus, die mit `Action.Execute`unterstützt wird. Der Bot erhält eine `adaptiveCard/action` Aufrufanforderung, an die er als Antwort eine adaptive Karte zurückgeben kann.
5. Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, die besagt, dass Nestor die Anforderung genehmigt hat, während Megans Genehmigung aussteht.
6. Die Bearbeitung von Bot-Nachrichten löst eine automatische Aktualisierung für Megan aus, und sie sieht die aktualisierte benutzerspezifische Karte, die besagt, dass Nestor die Anforderung genehmigt hat, aber auch die Schaltflächen **"Genehmigen"** oder **"Ablehnen** " sieht. Die Benutzer-MRT des Nestors wird in den Schritten 4 und 5 aus der `userIds` Liste in `refresh` der Eigenschaft dieses JSON-Codes für adaptive Karten entfernt. Jetzt wird die automatische Aktualisierung nur für Megan ausgelöst.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

7. Jetzt wählt Megan die Schaltfläche " **Genehmigen** " aus, die mit `Action.Execute`unterstützt wird. Der Bot erhält eine `adaptiveCard/action` Aufrufanforderung, an die er als Antwort eine adaptive Karte zurückgeben kann.
8. Der Bot löst eine Nachrichtenbearbeitung mit einer aktualisierten Karte aus, die besagt, dass Nestor und Megan die Anforderung genehmigt haben.
9. Die Bearbeitung von Botnachrichten löst keine automatische Aktualisierung aus. Megans Benutzer-MRT wird in Schritt 7 und 8 auch aus der `userIds` Liste in `refresh` der Eigenschaft dieses JSON-Codes für adaptive Karten entfernt.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Aktuelle Ansichten":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a>Adaptive Karte, gesendet als Antwort von `adaptiveCard/action` und `message edit`

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort von `adaptiveCard/action` und `message edit` für die Schritte 4 und 5 gesendet werden:

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

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort des Aufrufs `adaptiveCard/action` durch automatische Aktualisierung für Schritt 6 gesendet werden:

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

Der folgende Code enthält ein Beispiel für adaptive Karten, die als Antwort von `adaptiveCard/action` und `message edit` für die Schritte 7 und 8 gesendet werden:

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
| Adaptive Karten für sequenzielle Workflows | Veranschaulichen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Benutzerspezifische Ansichten](User-Specific-Views.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
