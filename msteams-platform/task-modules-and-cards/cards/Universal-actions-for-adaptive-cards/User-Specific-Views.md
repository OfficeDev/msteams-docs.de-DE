---
title: Benutzerspezifische Ansichten
description: Beispiel für benutzerspezifische Ansichten mithilfe universeller Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 984b32511dda544942df11f7c5d8a25cca8e9a8a
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088837"
---
# <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Wenn adaptive Karten in einer Teams gesendet wurden, sehen alle Benutzer den exakt gleichen Karteninhalt. Mit der Einführung des Universellen Aktionsmodells und für adaptive Karten können Botentwickler benutzern nun benutzerspezifische Ansichten `refresh` adaptiver Karten bereitstellen. Dieselbe adaptive Karte kann jetzt auf eine benutzerspezifische adaptive Karte aktualisiert werden.

Beispielsweise möchte Megan, ein Sicherheitsinspektor bei Contoso, einen Vorfall erstellen und alex zuweisen. Außerdem möchte sie, dass jeder im Team über den Vorfall informiert ist. Megan verwendet die Nachrichtenerweiterung contoso incident reporting powered by Universal Actions for Adaptive Cards.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

## <a name="user-specific-views-for-adaptive-cards"></a>Benutzerspezifische Ansichten für adaptive Karten

Der folgende Code enthält ein Beispiel für adaptive Karten:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView",
      "data": {
              "refresh info": "<refresh info>"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ]
}
```

**Aktualisieren Sie benutzerspezifische Ansichten, und rufen Sie Anforderungen an den Bot auf, um adaptive Karten zu senden**

1. Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die adaptive Karte oder eine gemeinsame Karte mit Vorfalldetails in der Teams Unterhaltung.
2. Jetzt wird diese Karte automatisch auf benutzerspezifische Ansicht für Megan und Alex aktualisiert. Die Benutzer-MRIs von Alex und Megan werden in eigenschaft der Eigenschaft der `userIds` `refresh` adaptiven Karten-JSON hinzugefügt. Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.
3. Für Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Vorfallerstellerkarte mit `Edit` Schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.
4. Ähnlich wie bei Alex löst die automatische Aktualisierung eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Karte des Vorfallsbesitzers als `Resolve` Antwort auf diese Aufrufanforderung zurückgeben.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Aufrufen der Anforderung, die vom Teams an den Bot gesendet wird

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die von Alex' und Megans Teams an den Bot gesendet wird:

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "editOrResolveView",
      "data": { 
            "refresh info": "<refresh info>"
      } 
    },
    "trigger": "automatic" 
  }
}
```

## <a name="adaptivecardaction-invoke-response-card"></a>adaptiveCard/action invoke response card

Der folgende Code enthält ein Beispiel für eine adaptiveCard/Action-Aufrufantwortkarte für Megan:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Edit",
      "verb": "edit",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a>adaptiveCard/action invoke response card for Alex

Der folgende Code enthält ein Beispiel für eine adaptiveCard/Action-Aufrufantwortkarte für Alex:

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Resolve",
      "verb": "resolve",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="invoke-response-to-return-adaptive-cards"></a>Aufrufen der Antwort zum Zurückgeben adaptiver Karten

Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben adaptiver Karten:

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.card.adaptive",
    value = card
 });
```

Richtlinien für den Kartenentwurf, die beim Entwerfen benutzerspezifischer Ansichten zu berücksichtigen sind:

* Sie können maximal **60 benutzerspezifische** Ansichten für eine bestimmte Karte erstellen, die an einen Chat oder Kanal gesendet werden, indem Sie sie `userIds` im Abschnitt `refresh` angeben.
* **Basiskarte:** Die Basisversion der Karte, die der Botentwickler an den Chat sendet. Dies ist die Version der adaptiven Karte für alle Benutzer, die nicht im Abschnitt angegeben `userIds` sind.
* Ein Nachrichtenupdate oder -bearbeiten kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren.

## <a name="see-also"></a>Siehe auch

* [Arbeiten mit universellen Aktionen für adaptive Karten](Work-with-universal-actions-for-adaptive-cards.md)
* [Aktuelle Ansichten](Up-To-Date-Views.md)
