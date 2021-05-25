---
title: Empfangen aller Kanalnachrichten mit RSC
author: surbhigupta12
description: Empfangen aller Kanalnachrichten mit RSC-Berechtigungen
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 833bdbc015cf852fcd899ce4e75f742448b89978
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631326"
---
# <a name="receive-all-channel-messages-with-rsc"></a>Empfangen aller Kanalnachrichten mit RSC

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Das ressourcenspezifische Berechtigungsmodell (Resource-Specific Consent, RSC), das ursprünglich für Teams Graph-APIs entwickelt wurde, wurde nun auf Botszenarien erweitert.

Derzeit können Bots nur Benutzerkanalnachrichten empfangen, wenn sie @mentioned. Mithilfe von RSC können Sie teambesitzer nun bitten, einem Bot zu zustimmen, Benutzernachrichten über Standardkanäle in einem Team zu empfangen, ohne dass @mentioned. Diese Funktion wird durch Angeben der Berechtigung im Manifest einer `ChannelMessage.Read.Group` RSC-aktivierten Teams aktiviert. Nach der Konfiguration können Teambesitzer während des App-Installationsvorgangs ihre Zustimmung erteilen.

Weitere Informationen zum Aktivieren von RSC für Ihre App finden Sie unter [ressourcenspezifische](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest)Zustimmung in Teams .

## <a name="enable-bots-to-receive-all-channel-messages"></a>Aktivieren von Bots zum Empfangen aller Kanalnachrichten

Die `ChannelMessage.Read.Group` RSC-Berechtigung wird auf Bots erweitert. Mit dieser Berechtigung können Graph-Anwendungen mit Zustimmung des Benutzers alle Nachrichten in einer Unterhaltung und Bots alle Kanalnachrichten empfangen, ohne dass sie @mentioned.

## <a name="update-app-manifest"></a>Aktualisieren des App-Manifests

Damit Ihr Bot alle Kanalnachrichten empfangen kann, muss RSC im Teams-App-Manifest mit der in der `ChannelMessage.Read.Group` Eigenschaft angegebenen Berechtigung konfiguriert `webApplicationInfo` werden.

![Aktualisieren des App-Manifests](~/bots/how-to/conversations/Media/appmanifest.png)

Es folgt ein Beispiel für das `webApplicationInfo` Objekt:

* **id**: Ihre Azure Active Directory (AAD)-App-ID. Dies kann mit Ihrer Bot-ID identisch sein.
* **resource**: Any string. Dieses Feld hat keinen Vorgang in RSC, muss jedoch hinzugefügt werden und über einen Wert verfügen, um Fehlerantworten zu vermeiden.
* **applicationPermissions**: RSC-Berechtigungen für Ihre App `ChannelMessage.Read.Group` mit müssen angegeben werden. Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).

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

## <a name="sideload-in-a-team-to-test"></a>Querladen in einem zu testenden Team

So laden Sie in einem Team quer, um zu testen, ob alle Kanalnachrichten in einem Team mit RSC empfangen werden, ohne dass @mentioned:

1. Wählen Oder erstellen Sie ein Team.
1. Wählen Sie die ellipsen &#x25CF;&#x25CF;&#x25CF; linken Bereich aus. Das Dropdownmenü wird angezeigt.
1. Wählen **Sie team verwalten** im Dropdownmenü aus. Die Details werden angezeigt.

   ![Verwalten von Apps im Team](~/bots/how-to/conversations/Media/managingteam.png)

1. Wählen Sie **Apps** aus. Es werden mehrere Apps angezeigt.
1. Wählen **Hochladen eine benutzerdefinierte App aus** der unteren rechten Ecke aus.

    ![Hochladen benutzerdefinierter Apps](~/bots/how-to/conversations/Media/uploadingcustomapp.png)

1. Wählen Sie das App-Paket im Dialogfeld **Öffnen** aus.
1. Klicken Sie auf **Öffnen**.

    ![Auswählen des App-Pakets](~/bots/how-to/conversations/Media/selectapppackage.png)

1. Wählen **Sie Im** Popup app-Details hinzufügen aus, um den Bot zu Ihrem ausgewählten Team hinzuzufügen.

    ![Hinzufügen des Bots](~/bots/how-to/conversations/Media/addingbot.png)

1. Wählen Sie einen Kanal aus, und geben Sie eine Nachricht im Kanal für Ihren Bot ein.

    Der Bot empfängt die Nachricht, ohne dass @mentioned.

    ![Bot empfängt Nachricht](~/bots/how-to/conversations/Media/botreceivingmessage.png)

## <a name="see-also"></a>Sehen Sie ebenfalls

* [Bot-Unterhaltungen](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [Ressourcenspezifische Zustimmung](/microsoftteams/resource-specific-consent)
* [Testen der ressourcenspezifischen Zustimmung](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [Hochladen benutzerdefinierte App in Teams](~/concepts/deploy-and-publish/apps-upload.md)
