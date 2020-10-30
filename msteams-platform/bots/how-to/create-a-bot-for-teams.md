---
title: Ein Bot mit App Studio erstellen
author: clearab
description: Erfahren Sie, wie Sie mit App Studio einen Microsoft Teams-Bot erstellen.
ms.topic: conceptual
localization_priority: Priority
ms.author: anclear
ms.openlocfilehash: 3d4f954afd56bf6ee442b57961c9d6b736ffa4d8
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796351"
---
# <a name="create-a-bot-using-app-studio"></a>Ein Bot mit App Studio erstellen

> [!TIP]
> Suchen Sie nach einer schnelleren Möglichkeit für die ersten Schritte? Erstellen Sie einen [Bot](../../build-your-first-app/build-bot.md) unter Verwendung des Microsoft Teams-Toolkits.

Zum Erstellen eines dialogorientierten Bots müssen die folgenden Schritte ausführen:

1. Vorbereiten Ihrer Entwicklungsumgebung.
1. Erstellen Ihres Webdiensts.
1. Registrieren Ihres Webdiensts als Bot bei Microsoft Bot Framework.
1. Erstellen Ihres App-Manifests -Pakets.
1. Hochladen Ihres Pakets in Microsoft Teams.

Die Erstellung Ihres Webdiensts, seine Registrierung und die Erstellung Ihres App-Pakets bei Bot Framework können in beliebiger Reihenfolge erfolgen. Da die drei Teile aber stark miteinander verwoben sind, müssen Sie stets die jeweils anderen Teile aktualisieren, ganz gleich, in welcher Reihenfolge Sie die Schritte ausführen. Für Ihre Registrierung ist der Messagingendpunkt aus Ihrem bereitgestellten Webdienst erforderlich, und Ihr Webdienst benötigt die ID und das Kennwort, die bei Ihrer Registrierung erstellt wurden. Für Ihr App-Manifest benötigen Sie zudem die Registrierungs-ID, um Teams mit Ihrem Webdienst zu verbinden.

Beim Erstellen des Bots wechseln Sie regelmäßig zwischen dem Ändern des App-Manifests und dem Bereitstellen von Code in Ihrem Webdienst hin und her. Wenn Sie mit dem App-Manifest arbeiten, denken Sie daran, dass Sie die JSON-Datei entweder manuell bearbeiten oder Änderungen über App Studio vornehmen können. So oder so müssen Sie Ihre App in Teams erneut bereitstellen (hochladen), wenn Sie eine Änderung am Manifest vornehmen. Bei der Bereitstellung von Änderungen an Ihrem Webdienst ist dies jedoch nicht erforderlich.

Weitere Informationen zu Bot Framework finden Sie in [Bot Framework-Dokumentation](/azure/bot-service/).

[!include[prepare environment](~/includes/prepare-environment.md)]

## <a name="create-your-web-service"></a>Erstellen Ihres Webdiensts

Das Herzstück Ihres Bots ist Ihr Webdienst. Er definiert eine einzelne Route (in der Regel `/api/messages`), auf der alle Anforderungen empfangen werden. Bei Beginn stehen Ihnen einige Optionen zur Auswahl:

* Starten Sie mit dem Beispiel eines dialogorientierten Bots für Teams entweder in [C#/dotnet](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot) oder [JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot).
* Wenn Sie JavaScript wählen, verwenden Sie den [Yeoman-Generator für Microsoft Teams](https://github.com/OfficeDev/generator-teams) zum Erstellen Ihrer Teams-App, einschließlich des Webdiensts. Dies ist besonders hilfreich, wenn Sie eine Teams-App erstellen, die mehr als nur einen dialogorientierten Bot enthält.
* Erstellen Sie Ihren Webdienst von Grund auf neu. Sie können das Bot Framework-SDK für Ihre Sprache hinzufügen oder direkt mit den JSON-Nutzlasten arbeiten.

## <a name="register-your-web-service-with-the-bot-framework"></a>Registrieren Ihres Webdiensts bei Bot Framework

> [!IMPORTANT]
> Achten Sie bei der Registrierung Ihres Webdiensts darauf, dass Sie den **Anzeigenamen** auf den gleichen Namen festlegen, den Sie in Ihrem App-Manifest als **Kurzname** verwendet haben. Wenn Ihre App entweder durch direktes Hochladen oder über den App-Katalog einer Organisation verteilt wird, verwenden Nachrichten, die von Ihrem Bot an eine Unterhaltung gesendet werden, den **Anzeigenamen** der Registrierung und nicht den **Kurznamen** der App.

Wenn Sie Ihren Webdienst bei Bot Framework registrieren, wird ein sicherer Kommunikationskanal zwischen dem Teams-Client und Ihrem Webdienst bereitgestellt. Der Team-Client und Ihr Webdienst kommunizieren niemals direkt. Stattdessen werden Nachrichten über Bot Framework Service geroutet (Microsoft Teams verwendet eine separate Instanz dieses Diensts, die mit Office 365-Standards kompatibel ist).

Sie haben zwei Optionen, wenn Sie Ihren Webdienst bei Bot Framework registrieren. Sie können entweder [App Studio](#using-app-studio) oder das [Legacy-Portal](#in-the-legacy-portal) verwenden, um ihren Bot ohne ein Azure-Abonnement zu registrieren. Oder, wenn Sie bereits über ein Azure-Abonnement verfügen (bzw. bereit sind, ein Abonnement zu erstellen), können Sie Ihren Webdienst über das [Azure-Portal](#with-an-azure-subscription) registrieren.

### <a name="without-an-azure-subscription"></a>Ohne Azure-Abonnement

Wenn Sie Ihre Bot-Registrierung nicht in Azure erstellen möchten, **müssen** Sie entweder diesen Link (https://dev.botframework.com/bots/new) oder App Studio verwenden. Wenn Sie im Bot Framework-Portal auf die Schaltfläche *Bot erstellen* klicken, erstellen Sie Ihre Bot-Registrierung in Microsoft Azure und müssen ein Azure-Abonnement bereitstellen. Um Ihre Registrierung nach der Erstellung zu verwalten oder zu einem Azure-Abonnement zu migrieren, wechseln Sie zu https://dev.botframework.com/bots.

Wenn Sie die Eigenschaften einer vorhandenen Bot Framework-Registrierung, die nicht in Azure registriert ist, bearbeiten, wird eine Spalte "Migrationsstatus" und eine blaue Schaltfläche "Migrieren" angezeigt, über die Sie zum Microsoft Azure-Portal gelangen. Wählen Sie die Schaltfläche "Migrieren" nicht aus, es sei denn, Sie möchten die Migration ausführen. Wählen Sie stattdessen den **Namen** des Bots aus. Sie können nun dessen Eigenschaften bearbeiten:

   ![Bearbeiten von Bot-Eigenschaften](~/assets/images/bots/bf-migrate-bot-to-azure.png)

Szenarien, in denen Ihre Bot-Registrierung in Azure erfolgen **muss** (entweder durch Erstellung im Azure-Portal oder durch Migration):

* Sie möchten [OAuthPrompt](./authentication/auth-flow-bot.md) von Bot Framework zur Authentifizierung verwenden.
* Sie möchten weitere Kanäle wie "Web Chat", "Direct Line" oder "Skype" aktivieren.

#### <a name="using-app-studio"></a>Verwenden von App Studio

*App Studio* ist eine Teams-Anwendung, die Sie bei der Erstellung von Teams-Apps unterstützt, beispielsweise beim Registrieren Ihres Webdiensts als Bot, beim Erstellen eines App-Manifests und App-Pakets und beim Aktualisieren von Einstellungen und Konfigurationen. App Studio enthält außerdem eine React-Steuerelementbibliothek sowie konfigurierbare Beispiele für Karten. Siehe [Erste Schritte mit Teams App Studio](../../concepts/build-and-test/app-studio-overview.md).

Denken Sie daran: Wenn Sie Ihren Webdienst mit App Studio registrieren, müssen Sie zu https://dev.botframework.com/bots wechseln, um Ihre Registrierung zu verwalten.

#### <a name="in-the-legacy-portal"></a>Im Legacy-Portal

Erstellen Sie Ihre Bot-Registrierung mit diesem Link: https://dev.botframework.com/bots/new. **Achten Sie darauf, dass Sie Microsoft Teams nach der Erstellung Ihres Bots aus der Liste der empfohlenen Kanäle als Kanal hinzufügen.** Sie können eine von Ihnen generierte Microsoft-App-ID wiederverwenden, wenn Sie Ihr App-Paket/-Manifest bereits erstellt haben.

   ![Bot Framework-Registrierungsseite](~/assets/images/bots/bfregister.png)

### <a name="with-an-azure-subscription"></a>Mit Azure-Abonnement

Sie können Ihren Webdienst auch registrieren, indem Sie im Azure-Portal eine Registrierungs Ressource für Bot-Kanäle erstellen.

[!INCLUDE [bot channels registration steps](~/includes/bots/azure-bot-channels-registration.md)]

Das [Bot Framework-Portal](https://dev.botframework.com) wurde für die Registrierung von Bots in Microsoft Azure optimiert. Hier sind einige weitere Punkte, die Sie wissen sollten:

* Der Microsoft Teams-Kanal für in Azure registrierte Bots ist **kostenlos** . Über den Teams-Kanal gesendete Nachrichten werden NICHT auf die verbrauchten Nachrichten für den Bot angerechnet.
* Wenn Sie Ihren Bot bei Microsoft Azure registrieren, muss Ihr Bot-Code nicht in Microsoft Azure *gehostet* werden.
* Wenn Sie einen Bot über das Microsoft Azure-Portal registrieren, müssen Sie über ein Microsoft Azure-Konto verfügen. Sie können [kostenlos ein Konto erstellen](https://azure.microsoft.com/free/). Zur Überprüfung Ihrer Identität beim Erstellen eines Azure-Kontos müssen Sie eine Kreditkarte angeben, die jedoch nicht belastet wird. In Microsoft Teams ist es stets kostenlos, Bots zu erstellen und zu verwenden.

## <a name="create-your-app-manifest-and-package"></a>Erstellen Ihres App-Manifests und App-Pakets

Ihr [App-Manifest](~/resources/schema/manifest-schema.md) definiert die Metadaten für Ihre App, die von der App verwendeten Erweiterungspunkte sowie Zeiger auf die Webdienste, mit denen diese Erweiterungspunkte verbunden sind. Sie können Ihr App-Manifest entweder in App Studio oder manuell erstellen.

### <a name="add-using-app-studio"></a>Mit App Studio hinzufügen

1. Öffnen Sie App Studio im Teams-Client aus dem **...** -Überlaufmenü auf der linken Navigationsleiste. Wenn App Studio noch nicht installiert ist, können Sie danach suchen und es installieren.
2. Wählen Sie auf der Registerkarte **Manifest-Editor** die Option **Neue App erstellen** aus. (Wenn Sie einen Bot zu einer vorhandenen App hinzufügen, können Sie Ihr App-Paket auch importieren.)
3. Fügen Sie Ihre App-Details hinzu (in der [Manifestschemadefinition](~/resources/schema/manifest-schema.md) finden Sie die vollständigen Beschreibungen der einzelnen Felder).
4. Wählen Sie auf der Registerkarte **Bots** die Schaltfläche **Setup** aus.
5. Sie können entweder eine neue Webdienstregistrierung ( **Neuer Bot** ) erstellen, oder wenn Sie sich bereits registriert haben, **Vorhandener Bot-** auswählen.
6. Wählen Sie die für den Bot benötigten Funktionen und Bereiche aus.
7. Aktualisieren Sie Ihre Bot-Endpunktadresse bei Bedarf so, dass Sie auf Ihren Bot verweist. Dies sollte ungefähr so aussehen: `https://someplace.com/api/messages`.
8. Optional können Sie [Bot-Befehle](~/bots/how-to/create-a-bot-commands-menu.md) hinzufügen.
9. Optional können Sie das fertige App-Paket über die Registerkarte **Testen und Verteilen** herunterladen.

### <a name="create-it-manually"></a>Manuell erstellen

Wie bei Messagingerweiterungen und Registerkarten aktualisieren Sie die [App-Manifest-](~/resources/schema/manifest-schema.md) zum Definieren Ihres Bots. Fügen Sie in Ihrem App-Manifest mit der `bots`-Eigenschaft eine neue JSON-Struktur der obersten Ebene hinzu.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|String|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Sie ist möglicherweise mit der Gesamt-App-ID identisch.|
|`needsChannelSelector`|Boolesch|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: `false`.|
|`isNotificationOnly`|Boolesch|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: `false`.|
|`supportsFiles`|Boolesch|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: `false`.|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|

Optional können Sie eine oder mehrere Listen von Befehlen definieren, die der Bot Benutzern empfehlen kann. Bei dem Objekt handelt es sich um ein Array (aus maximal 2 Elementen) wobei alle Elemente vom Typ `object` sind. Sie müssen für jeden von Ihrem Bot unterstützten Bereich eine separate Befehlsliste definieren. *Weitere Informationen finden Sie unter* [Bot-Menüs](./create-a-bot-commands-menu.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)|

#### <a name="simple-manifest-example"></a>Beispiel für ein einfaches Manifest

Das folgende Beispiel ist ein einfaches Bot-Objekt, in dem zwei Befehlslisten definiert sind. Hierbei handelt es sich nicht um die komplette App-Manifestdatei, sondern nur um den Teil der Messagingerweiterungen.

```json
...
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "scopes": [ "team", "personal", "groupchat" ],
      "supportsFiles": true,
      "commandLists": [
        {
          "scopes": [ "team", "groupchat" ],
          "commands": [
            {
              "title": "Command 1",
              "description": "Description of Command 1"
            },
            {
              "title": "Command N",
              "description": "Description of Command N"
            }
          ]
        },
        {
          "scopes": [ "personal", "groupchat" ],
          "commands": [
            {
              "title": "Personal command 1",
              "description": "Description of Personal command 1"
            },
            {
              "title": "Personal command N",
              "description": "Description of Personal command N"
            }
          ]
        }
      ]
    }
  ],
...
```

#### <a name="create-your-app-package-manually"></a>Manuelles Erstellen Ihres App-Pakets

Wenn Sie ein App-Paket erstellen möchten, müssen Sie Ihr App-Manifest und (optional) Ihre App-Symbole zu einer ZIP-Archivdatei hinzufügen. Die vollständigen Details finden Sie unter [Erstellen Ihres App-Pakets](~/concepts/build-and-test/apps-package.md). Vergewissern Sie sich, dass das ZIP-Archiv nur die erforderlichen Dateien enthält und keine zusätzliche Ordnerstruktur.

## <a name="upload-your-package-to-microsoft-teams"></a>Hochladen Ihres Pakets in Microsoft Teams

> [!NOTE]
> Um Ihren Bot erfolgreich hochzuladen, muss Ihr Mandantenadministrator zunächst [das Hochladen von Apps von Drittanbietern oder benutzerdefinierten Apps in Teams zulassen](/microsoftteams/manage-apps#manage-org-wide-app-settings).

Wenn Sie App Studio verwendet haben, können Sie die App über die Registerkarte **Testen und Verteilen** im **Manifest-Editor** installieren. Alternativ können Sie Ihr App-Paket installieren, indem Sie auf der linken Navigationsleiste auf das `...`-Überlaufmenü, dann auf **Weitere Apps** und schließlich auf den Link **Benutzerdefinierte App hochladen** klicken. Sie können ein App-Manifest oder App-Paket auch in App Studio importieren, um vor dem Hochladen weitere Aktualisierungen vorzunehmen.

## <a name="bots-in-teams-meetings"></a>Bots in Teams-Besprechungen

Teams unterstützt die Bot-Aufrufe während Besprechungen. Wenn Ihr Bot die Aufforderungsnachricht erhält, kann er Benutzer und Mandanten anhand von `userId` und `tenantId` identifizieren. Die `meetingId`kann als Teil des Objekts `channelData` gefunden werden. Ihr Bot kann die `userId` und `meetingId` für die API-Anforderung `GetParticipant` verwenden, um Benutzerrollen abzurufen.

## <a name="next-steps"></a>Nächste Schritte

* [Grundlegende Informationen zu Bot-Unterhaltungen](./conversations/conversation-basics.md)
* [Abonnieren von Unterhaltungsereignissen](./conversations/subscribe-to-conversation-events.md)
