---
title: Eine Messaging-Erweiterung mit App Studio erstellen
author: surbhigupta
description: Erfahren Sie, wie Sie eine Microsoft Teams Messaging-Erweiterung mit App Studio erstellen.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 9f222f52a4eea3b59e6caf15e77b006a58a426d2
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190024"
---
# <a name="create-a-messaging-extension-using-app-studio"></a>Eine Messaging-Erweiterung mit App Studio erstellen

> [!TIP]
> Suchen Sie nach einer schnelleren Möglichkeit für die ersten Schritte? Erstellen Sie eine [Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md) mit dem Microsoft Teams Toolkit.

Auf hoher Ebene müssen Sie die folgenden Schritte ausführen, um eine Messaging-Erweiterung zu erstellen.

1. Vorbereiten Ihrer Entwicklungsumgebung.
2. Erstellen und Bereitstellen Ihres Webdiensts (während der Entwicklung verwenden Sie einen Tunneldienst wie ngrok, um ihn lokal auszuführen).
3. Registrieren Sie Ihren Webdienst beim Bot Framework.
4. Erstellen Sie Ihr App-Paket.
5. Hochladen Das Paket Teams.

Das Erstellen Ihres Webdiensts, das Erstellen Ihres App-Pakets und das Registrieren Ihres Webdiensts beim Bot Framework kann in beliebiger Reihenfolge erfolgen. Da diese drei Teile so miteinander verflochten sind, müssen Sie unabhängig davon, in welcher Reihenfolge Sie sie ausführen, zurückkehren, um die anderen Zuschnitte zu aktualisieren. Ihre Registrierung benötigt den Messaging-Endpunkt von Ihrem bereitgestellten Webdienst, und Ihr Webdienst benötigt die ID und das Kennwort, die aus Ihrer Registrierung erstellt wurden. Ihr App-Manifest benötigt auch diese ID, um Teams mit Ihrem Webdienst zu verbinden.

Während Sie Ihre Messaging-Erweiterung erstellen, wechseln Sie regelmäßig zwischen dem Ändern Ihres App-Manifests und dem Bereitstellen von Code für Ihren Webdienst. Stellen Sie beim Arbeiten mit dem App-Manifest sicher, dass Sie die JSON-Datei entweder manuell ändern oder Änderungen über App Studio vornehmen können. In beiden Fällen müssen Sie Ihre App in Teams erneut bereitstellen (hochladen), wenn Sie eine Änderung am Manifest vornehmen. Dies ist jedoch nicht erforderlich, wenn Sie Änderungen an Ihrem Webdienst bereitstellen.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Erstellen Ihres Webdiensts

Das Herzstück Ihrer Messaging-Erweiterung ist Ihr Webdienst. Es wird eine einzelne Route definiert, in der Regel `/api/messages`, um alle Anforderungen zu empfangen. Wenn Sie von Grund auf neu beginnen, stehen Ihnen einige Optionen zur Auswahl.

* Verwenden Sie eines unserer [Schnellstartanleitungen](#learn-more) , die Sie durch die Erstellung Ihres Webdiensts führen.
* Wählen Sie eines der Messaging-Erweiterungsbeispiele aus, die im [Bot Framework-Beispielrepository](https://github.com/Microsoft/BotBuilder-Samples) verfügbar sind.
* Wenn Sie JavaScript verwenden, verwenden Sie den [Yeoman-Generator für Microsoft Teams](https://github.com/OfficeDev/generator-teams), um ein Gerüst für Ihre Teams-App einschließlich Ihres Webdiensts zu erstellen.
* Erstellen Sie Ihren Webdienst von Grund auf neu. Sie können das Bot Framework-SDK für Ihre Sprache hinzufügen oder direkt mit den JSON-Nutzlasten arbeiten.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrieren Ihres Webdiensts bei Bot Framework

Messaging-Erweiterungen nutzen das Messagingschema und das sichere Kommunikationsprotokoll des Bot Framework. wenn Sie noch nicht über einen verfügen, müssen Sie Ihren Webdienst im Bot Framework registrieren. Die Microsoft-App-ID (wir bezeichnen diese ID als Ihre Bot-ID innerhalb von Teams, um sie aus anderen App-IDs zu identifizieren, mit denen Sie möglicherweise arbeiten) und der Messaging-Endpunkt, mit dem Sie sich beim Bot Framework registrieren, wird in Ihrer Messaging-Erweiterung verwendet, um Anfragen zu empfangen und zu beantworten. Wenn Sie eine vorhandene Registrierung verwenden, stellen Sie sicher, dass Sie [den Microsoft Teams Kanal aktivieren](/azure/bot-service/bot-service-manage-channels?preserve-view=true&view=azure-bot-service-4.0).

Wenn Sie einer der Schnellstarts folgen oder mit einem der verfügbaren Beispiele beginnen, werden Sie durch die Registrierung Ihres Webdiensts geführt. Wenn Sie Ihren Dienst manuell registrieren möchten, haben Sie drei Möglichkeiten, dies zu tun. Wenn Sie sich für die Registrierung entscheiden, ohne ein Azure-Abonnement zu verwenden, können Sie den vom Bot Framework bereitgestellten vereinfachten OAuth-Authentifizierungsfluss nicht nutzen. Sie können Ihre Registrierung nach der Erstellung zu Azure migrieren.

* Wenn Sie über ein Azure-Abonnement verfügen (oder ein neues erstellen möchten), können Sie Ihren Webdienst manuell über das Microsoft Azure-Portal registrieren. Erstellen Sie eine Ressource für die Registrierung von Bot-Kanälen. Sie können das kostenlose Preisniveau auswählen, da Nachrichten aus Microsoft Teams nicht zu Ihren insgesamt zulässigen Nachrichten pro Monat zählen.
* Wenn Sie kein Azure-Abonnement verwenden möchten, können Sie das [Legacyregistrierungsportal](https://dev.botframework.com/bots/new) verwenden.
* App Studio kann Ihnen auch helfen, Ihren Webdienst (Bot) zu registrieren. Webdienste, die über App Studio registriert sind, sind nicht in Azure registriert. Sie können das [Legacyportal](https://dev.botframework.com/bots) verwenden, um Ihre Registrierungen anzuzeigen, zu verwalten und zu migrieren.

## <a name="create-your-app-manifest"></a>Erstellen Des App-Manifests

Sie können Ihr App-Manifest entweder in App Studio oder manuell erstellen.

### <a name="create-your-app-manifest-using-app-studio"></a>Erstellen Ihres App-Manifests mit App Studio

Sie können die App Studio-App im Teams-Client verwenden, um Das App-Manifest zu erstellen.

1. Öffnen Sie App Studio im Teams-Client aus dem **...**-Überlaufmenü auf der linken Navigationsleiste. Wenn es noch nicht installiert ist, können Sie dies tun, indem Sie danach suchen.
2. Wählen Sie auf der Registerkarte " **Manifest-Editor** " die Option " **Neue App erstellen** " aus (oder wenn Sie einer vorhandenen App eine Messaging-Erweiterung hinzufügen, können Sie Ihr App-Paket importieren).
3. Fügen Sie Ihre App-Details hinzu (in der [Manifestschemadefinition](~/resources/schema/manifest-schema.md) finden Sie die vollständigen Beschreibungen der einzelnen Felder).
4. Wählen Sie auf der Registerkarte " **Messagingerweiterungen** " die Schaltfläche " **Einrichten** " aus.
5. Sie können entweder einen neuen Webdienst (Bot) erstellen, den Ihre Messaging-Erweiterung verwenden soll, oder wenn Sie bereits einen Select/Add-Eintrag registriert haben.
6. Aktualisieren Sie Ihre Bot-Endpunktadresse bei Bedarf so, dass Sie auf Ihren Bot verweist. Dies sollte ungefähr so aussehen: `https://someplace.com/api/messages`.
7. Die Schaltfläche **"Hinzufügen"** im Abschnitt **"Befehl** " führt Sie durch das Hinzufügen von Befehlen zu Ihrer Messaging-Erweiterung. Links zu weiteren Informationen zum Hinzufügen von Befehlen finden Sie im Abschnitt " [Weitere](#learn-more) Informationen". Denken Sie daran, dass Sie bis zu 10 Befehle für Ihre Messaging-Erweiterung definieren können.
8. Im Abschnitt **"Nachrichtenhandler** " können Sie eine Domäne hinzufügen, für die Ihre Nachrichten ausgelöst werden. Weitere Informationen finden Sie unter ["Verbreitung von Links](~/messaging-extensions/how-to/link-unfurling.md) ".

Auf der Registerkarte **"Fertig stellen => Testen und verteilen** " können Sie Ihr App-Paket (das Ihr App-Manifest sowie Ihre App-Symbole enthält) **herunterladen** oder das Paket **installieren** .

### <a name="create-your-app-manifest-manually"></a>Manuelles Erstellen des App-Manifests

Wie bei Bots und Registerkarten aktualisieren Sie das [App-Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App so, dass es die Eigenschaften der Messagingerweiterung enthält. Diese Eigenschaften steuern, wie Ihre Messaging-Erweiterung im Teams-Client angezeigt und verhalten wird. Messaging-Erweiterungen werden ab Version 1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren Ihrer Messaging-Erweiterung

Um eine Messaging-Erweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur der obersten Ebene in Ihr App-Manifest mit der `composeExtensions` Eigenschaft ein. Sie erstellen eine einzelne Messaging-Erweiterung für Ihre App mit bis zu 10 Befehlen.

> [!NOTE]
> Das Manifest bezieht sich auf Messaging-Erweiterungen als `composeExtensions`. Dies dient dazu, die Abwärtskompatibilität aufrechtzuerhalten.

Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App identisch sein. | Ja |
| `canUpdateConfiguration` | Aktiviert **Einstellungen** Menüelement. | Nein |
| `commands` | Array von Befehlen, die diese Messaging-Erweiterung unterstützt. Sie sind auf 10 Befehle beschränkt. | Ja |

#### <a name="define-your-commands"></a>Definieren von Befehlen

Ihre Messaging-Erweiterung sollte einen oder mehrere Befehle deklarieren, die definieren, wo Ihre Benutzer Ihre Messaging-Erweiterung auslösen können, und die Art der Interaktion. [Weitere Informationen](#learn-more) zu Messaging-Erweiterungsbefehlen finden Sie hier.

#### <a name="simple-manifest-example"></a>Beispiel für ein einfaches Manifest

Das folgende Beispiel ist ein einfaches Messaging-Erweiterungsobjekt im App-Manifest mit einem Suchbefehl. Hierbei handelt es sich nicht um die komplette App-Manifestdatei, sondern nur um den Teil der Messagingerweiterungen. Ein vollständiges Beispiel finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md) .

```json
...
"composeExtensions": [
  {
    "botId": "abcd1234-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "searchCmd",
        "description": "Search you ToDo's",
        "title": "Search",
        "initialRun": true,
        "parameters": [
          {
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }
        ]
      }
    ]
  }
]
...
```

#### <a name="complete-app-manifest-example"></a>Beispiel für ein vollständiges App-Manifest

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

## <a name="add-your-invoke-message-handlers"></a>Hinzufügen von Aufrufnachrichtenhandlern

Wenn Ihre Benutzer Ihre Messaging-Erweiterung auslösen, müssen Sie die ursprüngliche Aufrufnachricht behandeln, einige Informationen vom Benutzer sammeln und diese Informationen dann verarbeiten und entsprechend reagieren. Dazu müssen Sie zunächst entscheiden, welche Art von Befehlen Sie Ihrer Messaging-Erweiterung hinzufügen möchten, und entweder [einen Aktionsbefehl hinzufügen](~/messaging-extensions/how-to/action-commands/define-action-command.md) oder [einen Suchbefehl hinzufügen](~/messaging-extensions/how-to/search-commands/define-search-command.md).

## <a name="messaging-extensions-in-teams-meetings"></a>Messaging-Erweiterungen in Teams Besprechungen

> [!NOTE]
> Wenn in einer Besprechung oder einem Gruppenchat Verbundbenutzer in der Teilnehmerliste enthalten sind, unterdrückt Teams den Zugriff auf Messaging-Erweiterungen für alle Benutzer, einschließlich des Organisators.

Sobald eine Besprechung beginnt, können Teams Teilnehmer während eines Liveanrufs direkt mit Ihrer Messaging-Erweiterung interagieren. Berücksichtigen Sie beim Erstellen Ihrer Messaging-Erweiterung in Besprechungen Folgendes:

1. **Location**. Ihre Messaging-Erweiterung kann über den Nachrichtenbereich zum Verfassen, das Befehlsfeld oder @mentioned im Besprechungschat aufgerufen werden.

1. **Metadaten**. Wenn Ihre Messaging-Erweiterung aufgerufen wird, kann sie den Benutzer und Mandanten von `userId` und `tenantId`identifizieren. Die `meetingId`kann als Teil des Objekts `channelData` gefunden werden. Ihre App kann die `userId` und `meetingId`  für die `GetParticipant` API-Anforderung verwenden, um Benutzerrollen abzurufen.

1. **Befehlstyp**. Wenn Ihre Nachrichtenerweiterung [aktionsbasierte Befehle](../messaging-extensions/what-are-messaging-extensions.md#action-commands) verwendet, sollte sie der [Single Sign-On-Authentifizierung](../tabs/how-to/authentication/tab-sso-overview.md) der Registerkarten folgen.

1. **Benutzerfreundlichkeit**. Die Messaging-Erweiterung sollte genauso aussehen und sich wie außerhalb einer Besprechung verhalten.

## <a name="next-steps"></a>Nächste Schritte

* [Erstellen von Aktionsbefehlen](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Erstellen von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Verbreiten von Links](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a>Weitere Informationen

Probieren Sie es in einer Schnellstartanleitung aus:

* Schnellstarts für C #
  * [Messaging-Erweiterung mit aktionsbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Messaging-Erweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* Schnellstarts für JavaScript
  * [Messaging-Erweiterung mit aktionsbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Messaging-Erweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

Weitere Informationen zu Teams-Entwicklungskonzepten:

* [Grundlegendes zu Teams App-Funktionen](../concepts/capabilities-overview.md)
* [Was sind Messaging-Erweiterungen?](../messaging-extensions/what-are-messaging-extensions.md)
