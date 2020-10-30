---
title: Eine Messaging-Erweiterung mit App Studio erstellen
author: clearab
description: In diesem Artikel erfahren Sie, wie Sie eine Microsoft Teams-Messaging Erweiterung mit App Studio erstellen.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: c3437457f7084d2d768af0f0db5208525c368682
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796183"
---
# <a name="create-a-messaging-extension-using-app-studio"></a>Eine Messaging-Erweiterung mit App Studio erstellen

> [!TIP]
> Suchen Sie nach einer schnelleren Möglichkeit für die ersten Schritte? Erstellen Sie mithilfe des Microsoft Teams-Toolkits eine [Messaging Erweiterung](../../build-your-first-app/build-messaging-extension.md) .

Auf einer hohen Ebene müssen Sie die folgenden Schritte ausführen, um eine Messaging Erweiterung zu erstellen.

1. Vorbereiten Ihrer Entwicklungsumgebung
2. Erstellen und Bereitstellen des Webdiensts (bei der Entwicklung verwenden Sie einen Tunnel Dienst wie ngrok, um den Webdienst lokal auszuführen)
3. Registrieren Ihres Webdiensts bei Bot Framework
4. Erstellen Ihres App-Paketes
5. Hochladen Ihres Pakets in Microsoft Teams

Das Erstellen Ihres Webdiensts, das Erstellen Ihres App-Pakets und das Registrieren des Webdiensts mit dem bot-Framework können in beliebiger Reihenfolge erfolgen. Da diese drei Teile so miteinander verflochten sind, müssen Sie zurückkehren, um die anderen zu aktualisieren, unabhängig davon, in welcher Reihenfolge Sie Sie durchführen. Ihre Registrierung benötigt den Messaging-Endpunkt aus dem bereitgestellten Webdienst, und Ihr Webdienst benötigt die ID und das Kennwort, die aus der Registrierung erstellt wurden. Ihr App-Manifest benötigt auch diese ID, um Teams mit Ihrem Webdienst zu verbinden.

Während Sie Ihre Messaging-Erweiterung erstellen, werden Sie regelmäßig zwischen dem Ändern des App-Manifests und dem Bereitstellen von Code in Ihrem Webdienst fortfahren. Beachten Sie beim Arbeiten mit dem App-Manifest, dass Sie entweder die JSON-Datei manuell bearbeiten oder über APP Studio Änderungen vornehmen können. In beiden Fällen müssen Sie Ihre APP in Microsoft Teams erneut bereitstellen, wenn Sie eine Änderung am Manifest vornehmen, dies ist jedoch nicht erforderlich, wenn Sie Änderungen an Ihrem Webdienst bereitstellen.

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Erstellen Ihres Webdiensts

Das Herzstück Ihrer Messaging Erweiterung ist Ihr Webdienst. In der Regel wird eine einzelne Route definiert, `/api/messages` um alle Anforderungen an zu empfangen. Wenn Sie von Grund auf neu gestartet werden, stehen Ihnen einige Optionen zur Auswahl.

* Verwenden Sie eines unserer [Schnellstart](#learn-more) -Lernprogramme, das Sie durch die Erstellung Ihres Webdiensts führen wird.
* Wählen Sie eines der Beispiele für die Messaging-Erweiterung aus, die im Beispiel-Repository für das [bot-Framework](https://github.com/Microsoft/BotBuilder-Samples) zum Starten zur Verfügung stehen.
* Wenn Sie JavaScript verwenden, verwenden Sie den Autobauer- [Generator für Microsoft Teams](https://github.com/OfficeDev/generator-teams) , um Ihre Teams-APP zu Gerüsten, einschließlich des Webdiensts.
* Erstellen Sie Ihren Webdienst von Grund auf neu. Sie können das Bot Framework-SDK für Ihre Sprache hinzufügen oder direkt mit den JSON-Nutzlasten arbeiten.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrieren Ihres Webdiensts bei Bot Framework

Messaging-Erweiterungen nutzen das Messaging-Schema des bot-Frameworks und das Secure Communication-Protokoll; Wenn Sie noch nicht über einen verfügen, müssen Sie den Webdienst im bot-Framework registrieren. Die Microsoft-App-ID (wir bezeichnen dies als ihre bot-ID innerhalb von Teams, um Sie von anderen APP-IDs zu identifizieren, mit denen Sie möglicherweise arbeiten) und dem Messaging-Endpunkt Ihr Register mit dem bot-Framework wird in Ihrer Messaging-Erweiterung verwendet, um Anfragen zu empfangen und darauf zu reagieren. Wenn Sie eine vorhandene Registrierung verwenden, stellen Sie sicher, dass Sie [den Microsoft Teams-Kanal aktiviert](/azure/bot-service/bot-service-manage-channels.md?view=azure-bot-service-4.0&preserve-view=true)haben.

Wenn Sie eine der Schnellstarts ausführen oder von einem der verfügbaren Beispiele starten, werden Sie durch die Registrierung Ihres Webdiensts geführt. Wenn Sie Ihren Dienst manuell registrieren möchten, haben Sie drei Möglichkeiten. Wenn Sie sich für die Registrierung ohne Verwendung eines Azure-Abonnements entscheiden, können Sie den vereinfachten OAuth-Authentifizierungs Fluss, der vom bot-Framework bereitgestellt wird, nicht nutzen. Sie können Ihre Registrierung nach der Erstellung nach Azure migrieren.

* Wenn Sie über ein Azure-Abonnement verfügen (oder ein neues erstellen möchten), können Sie den Webdienst manuell mithilfe des Azure-Portals registrieren. Erstellen Sie eine "bot Channels Registration"-Ressource. Sie können die ﻿kostenlose Preisklasse auswählen, da Nachrichten von Microsoft Teams nicht auf ihre zulässigen Gesamt Nachrichten pro Monat zählen.
* Wenn Sie kein Azure-Abonnement verwenden möchten, können Sie das [Legacy-Registrierungs Portal](https://dev.botframework.com/bots/new)verwenden.
* App Studio kann Sie auch bei der Registrierung Ihres Webdiensts (bot) unterstützen. Über APP Studio registrierte Webdienste sind nicht in Azure registriert. Mithilfe des [Legacy Portals](https://dev.botframework.com/bots) können Sie Ihre Registrierungen anzeigen, verwalten und migrieren.

## <a name="create-your-app-manifest"></a>Erstellen des App-Manifests

Sie können Ihr App-Manifest entweder in App Studio oder manuell erstellen.

### <a name="create-your-app-manifest-using-app-studio"></a>Erstellen des App-Manifests mithilfe von App Studio

Sie können die APP Studio-app innerhalb des Microsoft Teams-Clients verwenden, um das App-Manifest zu erstellen.

1. Öffnen Sie App Studio im Teams-Client aus dem **...** -Überlaufmenü auf der linken Navigationsleiste. Wenn es nicht bereits installiert ist, können Sie dies durchsuchen.
2. Klicken Sie auf der Registerkarte **Manifest-Editor** auf **neue APP erstellen** (oder wenn Sie eine Messaging Erweiterung zu einer vorhandenen APP hinzufügen, können Sie Ihr App-Paket importieren)
3. Fügen Sie Ihre App-Details hinzu (in der [Manifestschemadefinition](~/resources/schema/manifest-schema.md) finden Sie die vollständigen Beschreibungen der einzelnen Felder).
4. Klicken Sie auf der Registerkarte **Messaging Erweiterungen** auf die Schaltfläche **Setup** .
5. Sie können entweder einen neuen Webdienst (bot) erstellen, der von Ihrer Messaging-Erweiterung verwendet werden soll, oder wenn Sie sich bereits registriert haben, wählen Sie ihn aus, und fügen Sie ihn hier ein.
6. Aktualisieren Sie Ihre Bot-Endpunktadresse bei Bedarf so, dass Sie auf Ihren Bot verweist. Dies sollte ungefähr so aussehen: `https://someplace.com/api/messages`.
7. Die Schaltfläche **Hinzufügen** im **Befehls** Abschnitt führt Sie durch das Hinzufügen von Befehlen zu Ihrer Messaging Erweiterung. Im Abschnitt [Weitere Informationen finden Sie Links](#learn-more) zu weiteren Informationen zum Hinzufügen von Befehlen. Denken Sie daran, dass Sie bis zu 10 Befehle für Ihre Messaging Erweiterung definieren können.
8. Im Abschnitt **Nachrichtenhandler** können Sie eine Domäne hinzufügen, die von Ihrem Messaging ausgelöst wird. Weitere Informationen finden Sie unter [disrolling Link](~/messaging-extensions/how-to/link-unfurling.md) .

Auf der Registerkarte **Finish => Test and Distribute** können Sie Ihr App-Paket **herunterladen** (das Ihr App-Manifest sowie Ihre APP-Symbole enthält) oder das Paket **Installieren** .

### <a name="create-your-app-manifest-manually"></a>Manuelles Erstellen des App-Manifests

Wie bei Bots und Tabs aktualisieren Sie das [App-Manifest](~/resources/schema/manifest-schema.md#composeextensions) Ihrer APP so, dass Sie die Eigenschaften der Messaging Erweiterung enthält. Diese Eigenschaften bestimmen, wie Ihre Messaging Erweiterung angezeigt wird und sich im Microsoft Teams-Client verhält. Messaging Erweiterungen werden beginnend mit v 1.0 des Manifests unterstützt.

#### <a name="declare-your-messaging-extension"></a>Deklarieren der Messaging Erweiterung

Um eine Messaging Erweiterung hinzuzufügen, fügen Sie eine neue JSON-Struktur der obersten Ebene in das App-Manifest mit der `composeExtensions` -Eigenschaft ein. Sie erstellen eine einzelne Messaging Erweiterung für Ihre APP mit bis zu 10 Befehlen.

> [!NOTE]
> Das Manifest bezieht sich auf Messaging Erweiterungen als `composeExtensions` . Dadurch wird die Abwärtskompatibilität gewährleistet.

Die Erweiterungs Definition ist ein Objekt mit der folgenden Struktur:

| Eigenschaftenname | Zweck | Pflichtfeld? |
|---|---|---|
| `botId` | Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies sollte in der Regel mit der ID für Ihre gesamte Teams-App übereinstimmen. | Ja |
| `canUpdateConfiguration` | Aktiviert das Menüelement **Einstellungen** . | Nein |
| `commands` | Array von Befehlen, die von dieser Messaging Erweiterung unterstützt werden. Sie sind auf 10 Befehle limitiert. | Ja |

#### <a name="define-your-commands"></a>Definieren der Befehle

Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren, mit denen definiert wird, wo Ihre Benutzer Ihre Messaging Erweiterung auslösen können, und welche Art von Interaktion Sie haben. Weitere Informationen zu Befehlen für die Messaging Erweiterung finden Sie unter [erfahren Sie mehr](#learn-more) .

#### <a name="simple-manifest-example"></a>Beispiel für ein einfaches Manifest

Das folgende Beispiel ist ein einfaches Messaging Erweiterungsobjekt im App-Manifest mit einem Suchbefehl. Hierbei handelt es sich nicht um die komplette App-Manifestdatei, sondern nur um den Teil der Messagingerweiterungen. Ein vollständiges Beispiel finden Sie unter [App-Manifest-Schema](~/resources/schema/manifest-schema.md) .

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

## <a name="add-your-invoke-message-handlers"></a>Hinzufügen von Nachrichten Handlern für die Aktivierung

Wenn Ihre Benutzer Ihre Messaging-Erweiterung auslösen, müssen Sie die anfängliche Invoke-Nachricht verarbeiten, einige Informationen vom Benutzer erfassen, diese Informationen verarbeiten und entsprechend reagieren. Zu diesem Zweck müssen Sie zunächst entscheiden, welche Art von Befehlen Sie Ihrer Messaging Erweiterung hinzufügen möchten, und entweder [eine Aktionsbefehle hinzu](~/messaging-extensions/how-to/action-commands/define-action-command.md) fügen oder [einen Suchbefehl hinzu](~/messaging-extensions/how-to/search-commands/define-search-command.md)fügen.

## <a name="messaging-extensions-in-teams-meetings"></a>Messaging Erweiterungen in Microsoft Teams-Besprechungen

Sobald eine Besprechung beginnt, können Teams-Teilnehmer während eines Live-Anrufs direkt mit Ihrer Messaging-Erweiterung interagieren. Berücksichtigen Sie beim Erstellen Ihrer in-Meeting-Messaging-Erweiterung Folgendes:

1. **Location** . Ihre Messaging Erweiterung kann über den Bereich zum Verfassen von Nachrichten, das Befehlsfeld oder @mentioned im Besprechungs Chat aufgerufen werden.

1. **Metadaten** . Wenn Ihre Messaging-Erweiterung aufgerufen wird, kann Sie den Benutzer und den Mandanten aus `userId` und identifizieren `tenantId` . Die `meetingId`kann als Teil des Objekts `channelData` gefunden werden. Ihre APP kann die `userId` und `meetingId`  für die `GetParticipant` API-Anforderung zum Abrufen von Benutzerrollen verwenden.

1. **Befehlstyp** . Wenn Ihre Nachrichten Erweiterung [Aktionsbasierte Befehle](../../messaging-extensions/what-are-messaging-extensions.md#action-commands)verwendet, sollte Sie den Registerkarten [für einmaliges Anmelden bei](../../tabs/how-to/authentication/auth-aad-sso.md) der Authentifizierung entsprechen.

1. **Benutzeroberfläche** . Ihre Messaging Erweiterung sollte genauso aussehen und sich Verhalten wie außerhalb einer Besprechung.

## <a name="next-steps"></a>Nächste Schritte

* [Aktionsbefehle erstellen](~/messaging-extensions/how-to/action-commands/define-action-command.md)
* [Erstellen von Suchbefehlen](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Entfalten von Links](~/messaging-extensions/how-to/link-unfurling.md)

## <a name="learn-more"></a>Mehr erfahren

Testen Sie es in einem Schnellstart:

* Schnellstarts für C #
  * [Messaging-Erweiterung mit Aktions basierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)
  * [Messaging-Erweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)
* Schnellstarts für JavaScript
  * [Messaging-Erweiterung mit Aktions basierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action)
  * [Messaging-Erweiterung mit suchbasierten Befehlen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)

Erfahren Sie mehr über Entwicklungskonzepte für Teams:

* [Grundlegendes zu Teams-App-Funktionen](../../concepts/capabilities-overview.md)
* [Was sind Messaging Erweiterungen?](~/messaging-extensions/what-are-messaging-extensions.md)
