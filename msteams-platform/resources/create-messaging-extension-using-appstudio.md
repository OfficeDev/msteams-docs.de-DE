---
title: Eine Messaging-Erweiterung mit App Studio erstellen
author: clearab
description: Erfahren Sie, wie Sie eine Microsoft Teams-Messagingerweiterung mit App Studio erstellen.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 10de4c6f9e7b81e1edc47622cb5c0c814d2eb3a7
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019741"
---
# <a name="create-a-messaging-extension-using-app-studio"></a>Eine Messaging-Erweiterung mit App Studio erstellen

> [!TIP]
> Suchen Sie nach einer schnelleren Möglichkeit für die ersten Schritte? Erstellen Sie [eine Messagingerweiterung](../build-your-first-app/build-messaging-extension.md) mithilfe des Microsoft Teams Toolkits.

Auf einer hohen Ebene müssen Sie die folgenden Schritte ausführen, um eine Messagingerweiterung zu erstellen.

1. Vorbereiten Ihrer Entwicklungsumgebung
2. Erstellen und Bereitstellen Des Webdiensts (während der Entwicklung eines Tunneldiensts wie ngrok, um ihn lokal ausführen)
3. Registrieren Ihres Webdiensts bei Bot Framework
4. Erstellen Ihres App-Pakets
5. Hochladen Ihres Pakets in Microsoft Teams

Das Erstellen Ihres Webdiensts, das Erstellen Ihres App-Pakets und die Registrierung Ihres Webdiensts beim Bot Framework können in beliebiger Reihenfolge durchgeführt werden. Da diese drei Teile so miteinander verwoben sind, müssen Sie unabhängig von der Reihenfolge, in der Sie sie tun, zurückkehren, um die anderen zu aktualisieren. Ihre Registrierung benötigt den Messagingendpunkt von Ihrem bereitgestellten Webdienst, und Ihr Webdienst benötigt die ID und das Kennwort, die aus Ihrer Registrierung erstellt wurden. Ihr App-Manifest benötigt diese ID auch, um Teams mit Ihrem Webdienst zu verbinden.

Während Sie Ihre Messagingerweiterung erstellen, wechseln Sie regelmäßig zwischen dem Ändern des App-Manifests und der Bereitstellung von Code in Ihrem Webdienst. Beachten Sie bei der Arbeit mit dem App-Manifest, dass Sie die JSON-Datei manuell bearbeiten oder Änderungen über App Studio vornehmen können. So oder so müssen Sie Ihre App in Teams erneut bereitstellen (hochladen), wenn Sie eine Änderung am Manifest vornehmen. Dies ist jedoch nicht nötig, wenn Sie Änderungen an Ihrem Webdienst bereitstellen.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Erstellen Ihres Webdiensts

Das Herzstück Ihrer Messagingerweiterung ist Ihr Webdienst. Es wird eine einzelne Route definiert, in der Regel `/api/messages` , um alle Anforderungen zu empfangen. Wenn Sie von Grund auf beginnen, haben Sie einige Optionen zur Auswahl.

* Verwenden Sie eines unserer [Schnellstart-Lernprogramme,](#learn-more) die Sie durch die Erstellung Ihres Webdiensts führen.
* Wählen Sie eines der Messagingerweiterungsbeispiele aus, die im Bot Framework-Beispielrepository zum Starten verfügbar sind. [](https://github.com/Microsoft/BotBuilder-Samples)
* Wenn Sie JavaScript verwenden, verwenden Sie den [Yeoman-Generator für Microsoft Teams,](https://github.com/OfficeDev/generator-teams) um Ihre Teams-App einschließlich Ihres Webdiensts zu gerüsten.
* Erstellen Sie Ihren Webdienst von Grund auf neu. Sie können das Bot Framework-SDK für Ihre Sprache hinzufügen oder direkt mit den JSON-Nutzlasten arbeiten.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrieren Ihres Webdiensts bei Bot Framework

Messagingerweiterungen nutzen das Messagingschema und das sichere Kommunikationsprotokoll von Bot Framework. Wenn Sie noch nicht über einen verfügen, müssen Sie Ihren Webdienst im Bot Framework registrieren. Die Microsoft App-ID (wir bezeichnen dies als Ihre Bot-ID von innerhalb von Teams, um sie von anderen App-IDs zu identifizieren, mit der Sie möglicherweise arbeiten) und der Messagingendpunkt, mit dem Sie sich beim Bot Framework registrieren, werden in Ihrer Messagingerweiterung zum Empfangen und Beantworten von Anforderungen verwendet. Wenn Sie eine vorhandene Registrierung verwenden, stellen Sie sicher, dass Sie [den Microsoft Teams-Kanal aktivieren.](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true)

Wenn Sie einem der Schnellstarts folgen oder von einem der verfügbaren Beispiele starten, werden Sie durch die Registrierung Ihres Webdiensts geführt. Wenn Sie Ihren Dienst manuell registrieren möchten, haben Sie drei Möglichkeiten dazu. Wenn Sie sich ohne Verwendung eines Azure-Abonnements registrieren möchten, können Sie den vereinfachten OAuth-Authentifizierungsfluss, der vom Bot Framework bereitgestellt wird, nicht nutzen. Sie können Ihre Registrierung nach der Erstellung zu Azure migrieren.

* Wenn Sie über ein Azure-Abonnement verfügen (oder ein neues erstellen möchten), können Sie Ihren Webdienst manuell über das Azure-Portal registrieren. Erstellen Sie eine Ressource "Bot Channels Registration". Sie können die kostenlose Preisebene auswählen, da Nachrichten von Microsoft Teams nicht auf Ihre zulässigen Gesamtnachrichten pro Monat gezählt werden.
* Wenn Sie kein Azure-Abonnement verwenden möchten, können Sie das [Legacyregistrierungsportal verwenden.](https://dev.botframework.com/bots/new)
* App Studio kann Ihnen auch bei der Registrierung Ihres Webdiensts (Bot) helfen. Webdienste, die über App Studio registriert sind, sind nicht in Azure registriert. Mit dem [Legacyportal können](https://dev.botframework.com/bots) Sie Ihre Registrierungen anzeigen, verwalten und migrieren.

## <a name="create-your-app-manifest"></a>Erstellen Ihres App-Manifests

Sie können Ihr App-Manifest entweder in App Studio oder manuell erstellen.

### <a name="create-your-app-manifest-using-app-studio"></a>Erstellen Ihres App-Manifests mithilfe von App Studio

Sie können die App Studio-App aus dem Microsoft Teams-Client verwenden, um Ihr App-Manifest zu erstellen.

1. Öffnen Sie App Studio im Teams-Client aus dem **...**-Überlaufmenü auf der linken Navigationsleiste. Wenn es noch nicht installiert ist, können Sie dies tun, indem Sie danach suchen.
2. Wählen Sie **auf der Registerkarte Manifest-Editor** die Option **Neue** App erstellen aus (oder wenn Sie einer vorhandenen App eine Messagingerweiterung hinzufügen, können Sie Ihr App-Paket importieren)
3. Fügen Sie Ihre App-Details hinzu (in der [Manifestschemadefinition](~/resources/schema/manifest-schema.md) finden Sie die vollständigen Beschreibungen der einzelnen Felder).
4. Klicken Sie auf der Registerkarte **Messagingerweiterungen** auf die **Schaltfläche Setup.**
5. Sie können entweder einen neuen Webdienst (Bot) erstellen, damit Ihre Messagingerweiterung verwendet werden kann, oder wenn Sie bereits einen registriert haben, wählen/fügen Sie ihn hier hinzu.
6. Aktualisieren Sie Ihre Bot-Endpunktadresse bei Bedarf so, dass Sie auf Ihren Bot verweist. Dies sollte ungefähr so aussehen: `https://someplace.com/api/messages`.
7. Die **Schaltfläche** Hinzufügen im **Abschnitt Befehl** führt Sie durch das Hinzufügen von Befehlen zu Ihrer Messagingerweiterung. Im Abschnitt [Weitere Informationen finden](#learn-more) Sie Links zu weiteren Informationen zum Hinzufügen von Befehlen. Denken Sie daran, dass Sie bis zu 10 Befehle für Ihre Messagingerweiterung definieren können.
8. Im **Abschnitt Nachrichtenhandler können** Sie eine Domäne hinzufügen, für die Ihr Messaging ausgelöst wird. Weitere Informationen finden Sie unter Link [unfurling.](~/messaging-extensions/how-to/link-unfurling.md)

Auf der Registerkarte Finish => Test  and **distribute** können Sie Ihr App-Paket herunterladen (das ihr App-Manifest sowie Ihre App-Symbole enthält) oder **das** Paket installieren.

### <a name="create-your-app-manifest-manually"></a>Manuelles Erstellen des App-Manifests

Wie bei Bots und Registerkarten aktualisieren Sie das [App-Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer App so, dass die Nachrichtenerweiterungseigenschaften enthalten sind. Diese Eigenschaften steuern, wie Ihre Messagingerweiterung angezeigt wird und wie sie sich im Microsoft Teams-Client verhält. Messagingerweiterungen werden ab Version 1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren der Messagingerweiterung

Um eine Messagingerweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur auf oberster Ebene in Ihr App-Manifest mit der -Eigenschaft `composeExtensions` ein. Sie erstellen eine einzelne Messagingerweiterung für Ihre App mit bis zu 10 Befehlen.

> [!NOTE]
> Das Manifest bezieht sich auf Messagingerweiterungen als `composeExtensions` . Dadurch wird die Abwärtskompatibilität beibehalten.

Die Erweiterungsdefinition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel mit der ID ihrer gesamten Teams-App identisch sein. | Ja |
| `canUpdateConfiguration` | Aktiviert **das Menüelement** Einstellungen. | Nein |
| `commands` | Array von Befehlen, die von dieser Messagingerweiterung unterstützt werden. Sie sind auf 10 Befehle beschränkt. | Ja |

#### <a name="define-your-commands"></a>Definieren von Befehlen

Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren, die definieren, wo Ihre Benutzer Ihre Messagingerweiterung auslösen können, und den Typ der Interaktion. Weitere Informationen zu Messagingerweiterungsbefehlen finden Sie unter weitere Informationen. [](#learn-more)

#### <a name="simple-manifest-example"></a>Beispiel für ein einfaches Manifest

Das folgende Beispiel ist ein einfaches Messagingerweiterungsobjekt im App-Manifest mit einem Suchbefehl. Hierbei handelt es sich nicht um die komplette App-Manifestdatei, sondern nur um den Teil der Messagingerweiterungen. Ein vollständiges Beispiel finden Sie unter [App-Manifestschema.](~/resources/schema/manifest-schema.md)

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

#### <a name="complete-app-manifest-example"></a>Vollständiges Beispiel für das App-Manifest

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

## <a name="add-your-invoke-message-handlers"></a>Hinzufügen der aufruften Nachrichtenhandler

Wenn Ihre Benutzer Ihre Messagingerweiterung auslösen, müssen Sie die anfängliche Aufrufnachricht verarbeiten, einige Informationen vom Benutzer sammeln, diese Informationen verarbeiten und entsprechend reagieren. Zu diesem Schritt müssen Sie zunächst entscheiden, welche Art von BefehlEn Sie [](~/messaging-extensions/how-to/action-commands/define-action-command.md) Ihrer Messagingerweiterung hinzufügen möchten, und entweder einen Aktionsbefehl hinzufügen oder [suchbefehle hinzufügen.](~/messaging-extensions/how-to/search-commands/define-search-command.md)

## <a name="messaging-extensions-in-teams-meetings"></a>Messagingerweiterungen in Teams-Besprechungen

> [!NOTE]
> Wenn in einem Besprechungs- oder Gruppenchat Verbundbenutzer im Dienstplan stehen, unterdrückt Teams den Zugriff auf Messagingerweiterungen für alle Benutzer, einschließlich des Organisators.

Sobald eine Besprechung beginnt, können Teams-Teilnehmer während eines Liveanrufs direkt mit Ihrer Messagingerweiterung interagieren. Berücksichtigen Sie beim Erstellen Der Messagingerweiterung in Besprechungen Folgendes:

1. **Location**. Ihre Messagingerweiterung kann aus dem Bereich "Nachricht verfassen", dem Befehlsfeld oder @mentioned besprechungschat aufgerufen werden.

1. **Metadaten**. Wenn Ihre Messagingerweiterung aufgerufen wird, kann sie den Benutzer und Mandanten von `userId` und `tenantId` identifizieren. Die `meetingId`kann als Teil des Objekts `channelData` gefunden werden. Ihre App kann das `userId` und `meetingId`  für die `GetParticipant` API-Anforderung verwenden, um Benutzerrollen abzurufen.

1. **Befehlstyp**. Wenn Ihre Nachrichtenerweiterung [aktionsbasierte Befehle verwendet,](../messaging-extensions/what-are-messaging-extensions.md#action-commands)sollte sie den [Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md) für einmaliges Anmelden folgen.

1. **Benutzeroberfläche**. Die Messagingerweiterung sollte genauso aussehen und verhalten wie außerhalb einer Besprechung.

## <a name="next-steps"></a>Nächste Schritte

* [Erstellen von Aktionsbefehlen](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Erstellen von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Entfalten von Links](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a>Weitere Informationen

Testen Sie es in einem Schnellstart:

* Schnellstarts für C #
  * [Messagingerweiterung mit aktionsbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Messagingerweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* Schnellstarts für JavaScript
  * [Messagingerweiterung mit aktionsbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Messagingerweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

Weitere Informationen zu Teams-Entwicklungskonzepten:

* [Verstehen der Funktionen von Teams-Apps](../concepts/capabilities-overview.md)
* [Was sind Messaging-Erweiterungen?](../messaging-extensions/what-are-messaging-extensions.md)
