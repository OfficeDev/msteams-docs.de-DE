---
title: Benutzerspezifische Ansichten
description: In diesem Modul erfahren Sie mehr über benutzerspezifische Ansichten mithilfe von universellen Aktionen mit Codebeispiel und adaptiveCard-/Aktionsaufruf-Antwortkarte
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: a3fdc937ba1528a2bf9aa304bf484bbcae68b5c6
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143921"
---
# <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Früher, wenn adaptive Karten in einer Teams Unterhaltung gesendet wurden, würden alle Benutzer genau den gleichen Karteninhalt sehen. Mit der Einführung des Modells für universelle Aktionen und `refresh` für adaptive Karten können Bot-Entwickler benutzern jetzt benutzerspezifische Ansichten adaptiver Karten bereitstellen. Dieselbe adaptive Karte kann jetzt auf eine benutzerspezifische adaptive Karte aktualisiert werden. Die adaptive Karte bietet leistungsstarke Szenarien wie Genehmigungen, Umfrageerstellungssteuerelemente, Ticketing, Vorfallverwaltung und Projektverwaltungskarten.

> [!NOTE]
>
> * Die benutzerspezifische Ansicht wird für adaptive Karten unterstützt, die von einem Bot gesendet werden, und hängt von universellen Aktionen ab.
> * Maximal 60 verschiedene Benutzer können eine andere Version der Karte mit zusätzlichen Informationen oder Aktionen sehen.

Megan, ein Sicherheitsinspektor bei Contoso, möchte beispielsweise einen Vorfall erstellen und alex zuweisen. Megan möchte auch, dass jeder im Team über den Vorfall informiert ist. Megan verwendet die Contoso-Erweiterung für Die Meldung von Vorfallberichten, die von universellen Aktionen für adaptive Karten unterstützt wird.

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Mobile benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/universal-bots-incident-management.png":::

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
      }
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

Aktualisieren Sie zum Senden adaptiver Karten benutzerspezifische Ansichten, und rufen Sie Anforderungen an den Bot auf:

1. Wenn Megan einen neuen Vorfall erstellt, sendet der Bot die adaptive Karte oder allgemeine Karte mit Vorfalldetails in der Teams Unterhaltung.
2. Jetzt wird diese Karte automatisch in die benutzerspezifische Ansicht für Megan und Alex aktualisiert. Alex und Megans Benutzer-MRIs werden in `userIds` der Eigenschaft der `refresh` Eigenschaft des JSON-Code für adaptive Karten hinzugefügt. Die Karte bleibt für andere Benutzer in der Unterhaltung gleich.
3. Bei Megan löst die automatische Aktualisierung eine `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Incident Creator-Karte mit `Edit` einer Schaltfläche als Antwort auf diese Aufrufanforderung zurückgeben.
4. Ähnlich wie bei Alex löst die automatische Aktualisierung eine weitere `adaptiveCard/action` Aufrufanforderung an den Bot aus. Der Bot kann eine Kartenschaltfläche des Vorfallbesitzers `Resolve` als Antwort auf diese Aufrufanforderung zurückgeben.

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a>Aufrufanforderung, die von Teams Client an den Bot gesendet wurde

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

## <a name="adaptivecardaction-invoke-response-card"></a>adaptiveCard-/Aktions-Aufruf-Antwortkarte

Der folgende Code enthält ein Beispiel für eine adaptiveCard-/Aktions-Aufruf-Antwortkarte für Megan:

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

Der folgende Code enthält ein Beispiel für eine adaptiveCard/Action Invoke-Antwortkarte für Alex:

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

Der folgende Code enthält ein Beispiel für eine Aufrufantwort zur Rückgabe adaptiver Karten:

### <a name="c"></a>[C#](#tab/C)

```csharp
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

### <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
var card = "<adaptive card json>";
 
const cardRes = {
        statusCode: 200,
        type: 'application/vnd.microsoft.card.adaptive',
        value: card
    };
    const res = {
        status: 200,
        body: cardRes
    };
    return res;

```

***

Die folgende Liste enthält Richtlinien für den Kartenentwurf für benutzerspezifische Ansichten:

* Aktualisierungsverhalten: Sie können maximal 60 benutzerspezifische Ansichten für eine bestimmte Karte erstellen, die an eine Unterhaltung gesendet wird, indem Sie deren `userIds` in der `Refresh` Eigenschaft angeben.

  * Wenn das `userIds` Feld in der `Refresh` Eigenschaft nicht angegeben ist, kann Teams Client automatisch eine Aktualisierung für alle Benutzer auslösen, wenn die Unterhaltung kleiner oder gleich 60 Mitgliedern ist.

  * Damit Benutzer die Kartenaktualisierung manuell auslösen können, können sie im Menü "Nachrichtenoptionen" die Option **"Aktualisieren"** auswählen. Dies geschieht für alle Benutzer, wenn weniger als 60 Mitglieder in einer Unterhaltung vorhanden sind, oder für die Gruppe von Benutzern, die nicht in der `userIds` Liste angegeben sind, wenn alle oder weniger als 60 Benutzer in einer Unterhaltung vorhanden sind.

* Basiskarte: Der Bot sendet die Nachricht, die in die Basisversion der Karte einbettet. Alle Mitglieder der Unterhaltung können dasselbe anzeigen. Der Bot ruft anschließend die benutzerspezifische Karte durch Aktualisierung für die im `userIds` Abschnitt angegebenen Benutzer ab.

* Aktualisierungstimeout: Teams Client löst eine Aktualisierung auf zwei Arten aus, entweder über **"Aktualisieren"** oder durch Auswählen von **"Ausführen**". Die Aktualisierung wird nur ausgelöst, wenn die Karte aus dem letzten Aufruf älter als eine Minute ist. Sie können das Aktualisierungsverhalten steuern, indem Sie dem Datenbehälter einen Zeitstempel hinzufügen und ihn überprüfen, bevor Sie die aktualisierte Karte senden.

* Eine Nachrichtenaktualisierung kann verwendet werden, um die Basiskarte zu aktualisieren und gleichzeitig die benutzerspezifische Karte zu aktualisieren. Beim Öffnen des Chats oder Kanals wird auch die Karte für Benutzer aktualisiert, für die **"Aktualisieren"** aktiviert ist.

* In Szenarien mit größeren Gruppen, in denen Benutzer zu einer Aktionsansicht wechseln, für die dynamische Updates für Die Antwortenden erforderlich sind, können Sie der Liste weiterhin bis zu 60 Benutzer `userIds` hinzufügen. Sie können den ersten Antwortenden aus der Liste entfernen, wenn der 61. Benutzer antwortet. Für die Benutzer, die aus der `userIds` Liste entfernt werden, können Sie eine manuelle **Aktualisierung** bereitstellen, um das neueste Ergebnis zu erhalten.

* Geben Sie den Benutzern die Aufforderung, eine benutzerspezifische Ansicht abzurufen, in der nur eine bestimmte Ansicht der Karte oder einige Aktionen angezeigt wird.

> [!NOTE]
> Die vom Bot zurückgegebene benutzerspezifische Karte wird nur an den spezifischen Client gesendet, der danach gefragt hat. Wenn ein Benutzer beispielsweise zu einem anderen Client wechselt, z. B. von Desktop zu Mobilgerät, wird ein weiteres Aufrufereignis ausgelöst, um die aktualisierte Karte abzurufen.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Adaptive Karten für sequenzielle Workflows | Veranschaulichen, wie sequenzielle Workflows, benutzerspezifische Ansichten und aktuelle adaptive Karten in Bots implementiert werden. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
* [Aktuelle Ansichten](Up-To-Date-Views.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
