---
title: Benutzerspezifische Ansichten
description: Beispiel für benutzerspezifische Ansichten mit universellen Aktionen
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: c24697b300d07ed53a172df162d0d3851361f579
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853515"
---
# <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Wenn adaptive Karten zuvor in einer Teams Unterhaltung gesendet wurden, sehen alle Benutzer genau den gleichen Karteninhalt. Mit der Einführung des Modells für universelle Aktionen und `refresh` für adaptive Karten können Botentwickler Benutzern jetzt benutzerspezifische Ansichten adaptiver Karten bereitstellen. Dieselbe adaptive Karte kann jetzt auf eine benutzerspezifische adaptive Karte aktualisiert werden. Maximal 60 verschiedene Benutzer können eine andere Version der Karte mit zusätzlichen Informationen oder Aktionen sehen. Dies bietet leistungsstarke Szenarien wie Genehmigungen, Steuerelemente für Umfrageersteller, Ticketing, Vorfallverwaltung und Projektverwaltungskarten.

Megan, ein Sicherheitsinspektor bei Contoso, möchte beispielsweise einen Vorfall erstellen und Alex zuweisen. Außerdem möchte sie, dass jeder im Team über den Vorfall informiert wird. Megan verwendet die Nachrichtenerweiterung "Contoso Incident Reporting", die von universellen Aktionen für adaptive Karten unterstützt wird.

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Benutzerspezifische Ansichten mobiler Benutzer":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

* * *

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

**Um adaptive Karten zu senden, aktualisieren Sie benutzerspezifische Ansichten, und rufen Sie Anforderungen an den Bot auf.**

1. Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die adaptive Karte oder allgemeine Karte mit Vorfalldetails in der Teams Unterhaltung.
2. Jetzt wird diese Karte automatisch auf die benutzerspezifische Ansicht für Megan und Alex aktualisiert. Alex und Megans Benutzer-MRIs werden als `userIds` Eigenschaft der Adaptive Card JSON `refresh` hinzugefügt. Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.
3. Bei Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Vorfallerstellerkarte mit `Edit` schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.
4. Auf ähnliche Weise löst die automatische Aktualisierung für Alex eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine `Resolve` Vorfallbesitzer-Kartenschaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Aufrufen einer Anforderung, die vom Teams-Client an den Bot gesendet wurde

Der folgende Code enthält ein Beispiel für eine Aufrufanforderung, die vom Teams-Client von Alex und Megan an den Bot gesendet wird:

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

## <a name="adaptivecardaction-invoke-response-card"></a>adaptiveCard/Aktionsaufrufantwortkarte

Der folgende Code enthält ein Beispiel für eine AdaptiveCard/Aktionsaufforderungsantwortkarte für Megan:

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a>adaptiveCard/Aktion ruft Antwortkarte für Alex auf

Der folgende Code enthält ein Beispiel für eine AdaptiveCard/Aktionsaufforderungsantwortkarte für Alex:

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

Der folgende Code enthält ein Beispiel für eine Aufrufantwort, um adaptive Karten zurückzugeben:

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

Richtlinien für den Kartenentwurf, die Sie beim Entwerfen benutzerspezifischer Ansichten beachten sollten:

* Sie können maximal **60 benutzerspezifische Ansichten** für eine bestimmte Karte erstellen, die an einen Chat oder Kanal gesendet wird, indem Sie diese `userIds` im Abschnitt `refresh` angeben.
* **Basiskarte:** Die Basisversion der Karte, die der Bot-Entwickler an den Chat sendet. Dies ist die Version der adaptiven Karte für alle Benutzer, die nicht im Abschnitt angegeben `userIds` sind.
* Eine Nachrichtenaktualisierung kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren. Beim Öffnen des Chats oder Kanals wird auch die Karte für Benutzer mit aktivierter Aktualisierung aktualisiert.
* Für Szenarien mit größeren Gruppen, in denen Benutzer zu einer Aktionsansicht wechseln, die dynamische Updates für Antwortende benötigt, können Sie bis zu 60 Benutzer zur `userIds` Liste hinzufügen. Sie können den Ersten Antwortenden aus der Liste entfernen, wenn der 61. Benutzer antwortet. Für die Benutzer, die aus der Liste entfernt `userIds` werden, können Sie eine manuelle Aktualisierungsschaltfläche bereitstellen oder die Schaltfläche "Aktualisieren" im Menü "Nachrichtenoptionen" verwenden, um das neueste Ergebnis zu erhalten.
* Geben Sie Benutzern eine Eingabeaufforderung, um eine benutzerspezifische Ansicht zu erhalten, in der nur eine bestimmte Ansicht der Karte oder einige Aktionen angezeigt werden.

## <a name="see-also"></a>Siehe auch

* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Aktuelle Ansichten](Up-To-Date-Views.md)
