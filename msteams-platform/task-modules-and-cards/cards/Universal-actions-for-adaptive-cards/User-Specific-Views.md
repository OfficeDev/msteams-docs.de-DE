---
title: Benutzerspezifische Ansichten
description: Beispiel für benutzerspezifische Ansichten mithilfe universeller Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 696fc5ce25c79d749b301309bfe0c737e39ad294
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555444"
---
# <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Früher, wenn Adaptive Cards in einer Teams Unterhaltung gesendet wurden, sehen alle Benutzer genau den gleichen Karteninhalt. Mit der Einführung des Universal Actions-Modells und `refresh` für Adaptive Cards können Bot-Entwickler Benutzern nun benutzerspezifische Ansichten von Adaptive Cards zur Verfügung stellen. Dieselbe Adaptive Karte kann jetzt auf einer benutzerspezifischen adaptiven Karte aktualisiert werden.

Beispielsweise möchte Megan, ein Sicherheitsinspektor bei Contoso, einen Vorfall erstellen und Alex zuweisen. Sie möchte auch, dass alle im Team über den Vorfall informiert werden. Megan verwendet Contoso Incident Reporting Message Extension powered by Universal Actions for Adaptive Cards.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

## <a name="user-specific-views-for-adaptive-cards"></a>Benutzerspezifische Ansichten für adaptive Karten

Der folgende Code enthält ein Beispiel für Adaptive Cards:

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

**Um Adaptive Cards zu senden, benutzerspezifische Ansichten zu aktualisieren und Anforderungen an den Bot aufzurufen**

1. Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die Adaptive Card oder die gemeinsame Karte mit Ereignisdetails im Teams Gespräch.
2. Diese Karte wird jetzt automatisch in der benutzerspezifischen Ansicht für Megan und Alex aktualisiert. Die Benutzer-MRTs von Alex und Megan werden in `userIds` der Eigenschaft der Adaptive Card `refresh` JSON hinzugefügt. Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.
3. Für Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Vorfall-Ersteller-Karte mit `Edit` Schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.
4. Ebenso löst die automatische Aktualisierung für Alex eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Schaltfläche für den Vorfallbesitzer als `Resolve` Antwort auf diese Aufrufanforderung zurückgeben.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Aufrufen von Anforderung, die von Teams Client an den Bot gesendet wurde

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die von Alex und Megans Teams-Client an den Bot gesendet wurde:

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

## <a name="adaptivecardaction-invoke-response-card"></a>adaptiveCard/Action-Aufrufantwortkarte

Der folgende Code enthält ein Beispiel für eine adaptiveCard/Aktionsaufrufantwortkarte für Megan:

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a>adaptiveCard/Action-Aufrufantwortkarte für Alex

Der folgende Code enthält ein Beispiel für eine adaptiveCard/Aktionsaufrufantwortkarte für Alex:

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

## <a name="invoke-response-to-return-adaptive-cards"></a>Aufrufen der Antwort auf die Rückgabe von Adaptive Cards

Der folgende Code enthält ein Beispiel für eine Aufrufantwort zum Zurückgeben von Adaptive Cards:

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

Richtlinien für das Kartendesign, die Beim Entwerfen von benutzerspezifischen Ansichten zu beachten sind:

* Sie können maximal **60 benutzerspezifische Ansichten** für eine bestimmte Karte erstellen, die an einen Chat oder Kanal gesendet wird, indem Sie deren `userIds` im Abschnitt `refresh` angeben.
* **Basiskarte:** Die Basisversion der Karte, die der Bot-Entwickler an den Chat sendet. Dies ist die Version der Adaptive Card für alle Benutzer, die nicht im Abschnitt angegeben `userIds` sind.
* Eine Nachrichtenaktualisierung oder -bearbeitung kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren.

## <a name="see-also"></a>Siehe auch

* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Aktuelle Ansichten](Up-To-Date-Views.md)
