---
title: Empfangen aller Kanalnachrichten mit RSC
author: surbhigupta12
description: Empfangen aller Kanalnachrichten mit RSC-Berechtigungen
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: ea247d7718b76f1e48bbb2c9839606dcb5cbab51
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156051"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Empfangen aller Kanalnachrichten mit RSC

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Das ressourcenspezifische Zustimmungsmodell (RSC), das ursprünglich für Teams Graph-APIs entwickelt wurde, wurde jetzt auf Bot-Szenarien erweitert.

Derzeit können Bots nur Benutzerkanalnachrichten empfangen, wenn sie @mentioned sind. Mithilfe von RSC können Sie jetzt Teambesitzer bitten, zuzustimmen, dass ein Bot Benutzernachrichten über Standardkanäle in einem Team empfängt, ohne @mentioned zu werden. Diese Funktion wird aktiviert, indem die `ChannelMessage.Read.Group` Berechtigung im Manifest einer RSC-aktivierten Teams-App angegeben wird. Nach der Konfiguration können Teambesitzer während des App-Installationsvorgangs ihre Zustimmung erteilen.

Weitere Informationen zum Aktivieren von RSC für Ihre App finden Sie unter [ressourcenspezifischer Zustimmung in Teams.](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest)

## <a name="enable-bots-to-receive-all-channel-messages"></a>Bots den Empfang aller Kanalnachrichten ermöglichen

Die `ChannelMessage.Read.Group` RSC-Berechtigung wird auf Bots erweitert. Mit der Zustimmung des Benutzers ermöglicht diese Berechtigung Graph-Anwendungen, alle Nachrichten in einer Unterhaltung abzurufen und Bots alle Kanalnachrichten zu empfangen, ohne @mentioned zu werden.

## <a name="update-app-manifest"></a>Aktualisieren des App-Manifests

Damit Ihr Bot alle Kanalnachrichten empfangen kann, muss RSC im Teams App-Manifest mit der in der Eigenschaft angegebenen Berechtigung konfiguriert `ChannelMessage.Read.Group` `webApplicationInfo` werden.

![Aktualisieren des App-Manifests](~/bots/how-to/conversations/Media/appmanifest.png)

Es folgt ein Beispiel für das `webApplicationInfo` Objekt:

* **id:** Ihre Azure Active Directory -App-ID (AAD). Dies kann mit Ihrer Bot-ID identisch sein.
* **ressource:** Eine beliebige Zeichenfolge. Dieses Feld verfügt über keinen Vorgang in RSC, muss jedoch hinzugefügt werden und einen Wert aufweisen, um eine Fehlerantwort zu vermeiden.
* **applicationPermissions:** RSC-Berechtigungen für Ihre App mit `ChannelMessage.Read.Group` müssen angegeben werden. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen.](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions)

Der folgende Code enthält ein Beispiel für das App-Manifest:

```json
"webApplicationInfo": {
"id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
"resource": "https://AnyString",
"applicationPermissions": [
"ChannelMessage.Read.Group"
    ]
  }
```

## <a name="sideload-in-a-team-to-test"></a>Querladen in einem Team zum Testen

Wenn Sie in einem Team querladen möchten, um zu testen, ob alle Kanalnachrichten in einem Team mit RSC empfangen werden, ohne @mentioned:

1. Wählen Sie ein Team aus, oder erstellen Sie es.
1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; im linken Bereich aus. Das Dropdownmenü wird angezeigt.
1. Wählen Sie im Dropdownmenü die Option **"Team verwalten"** aus. Die Details werden angezeigt.

   ![Verwalten von Apps im Team](~/bots/how-to/conversations/Media/managingteam.png)

1. Wählen Sie **Apps** aus. Es werden mehrere Apps angezeigt.
1. Wählen Sie in der unteren rechten Ecke **Hochladen einer benutzerdefinierten App** aus.

    ![Hochladen einer benutzerdefinierten App](~/bots/how-to/conversations/Media/uploadingcustomapp.png)

1. Wählen Sie im Dialogfeld **"Öffnen"** das App-Paket aus.
1. Klicken Sie auf **Öffnen**.

    ![Auswählen des App-Pakets](~/bots/how-to/conversations/Media/selectapppackage.png)

1. Wählen Sie im Popup "App-Details" die Option **"Hinzufügen"** aus, um den Bot ihrem ausgewählten Team hinzuzufügen.

    ![Hinzufügen des Bots](~/bots/how-to/conversations/Media/addingbot.png)

1. Wählen Sie einen Kanal aus, und geben Sie eine Nachricht im Kanal für Ihren Bot ein.

    Der Bot empfängt die Nachricht, ohne @mentioned zu werden.

    ![Bot empfängt Nachricht](~/bots/how-to/conversations/Media/botreceivingmessage.png)

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C # |Node.js|
|-------------|-------------|------|----|
|Kanalnachrichten mit RSC-Berechtigungen| Microsoft Teams Beispiel-App veranschaulicht, wie ein Bot alle Kanalnachrichten mit RSC empfangen kann, ohne @mentioned zu werden.|  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/csharp) |    [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-receive-channel-messages-withRSC/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Bot-Unterhaltungen](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Ressourcenspezifische Zustimmung](/microsoftteams/resource-specific-consent)
* [Testen der ressourcenspezifischen Zustimmung](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Hochladen benutzerdefinierte App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
