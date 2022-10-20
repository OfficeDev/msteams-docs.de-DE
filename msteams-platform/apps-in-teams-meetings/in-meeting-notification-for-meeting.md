---
title: Erstellen einer Benachrichtigung in einer Besprechung für Teams-Besprechungen
author: v-sdhakshina
description: In diesem Artikel erfahren Sie, wie Sie Benachrichtigungen in Besprechungen für Microsoft Teams-Besprechungen und deren Codebeispiel erstellen.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.openlocfilehash: 2bdf63ab597c00627c14b909d51efa753e0cd1b0
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615454"
---
# <a name="build-in-meeting-notification-for-teams-meeting"></a>Erstellen einer Benachrichtigung in einer Besprechung für Teams-Besprechungen

Die Benachrichtigung in der Besprechung wird verwendet, um Teilnehmer einzubeziehen und während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie [besprechungsinterne Benachrichtigungsnutzdaten](meeting-apps-apis.md#send-an-in-meeting-notification), um eine besprechungsinterne Benachrichtigung auszulösen. Fügen Sie als Teil der Benachrichtigungsnutzlastanforderung die URL hinzu, unter der der anzuzeigende Inhalt gehostet wird.

Eine externe Ressourcen-URL wird verwendet, um besprechungsinterne Benachrichtigungen anzuzeigen. Sie können die Methode `submitTask` verwenden, um Daten in einem Besprechungschat zu übermitteln.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="Der Screenshot ist ein Beispiel, das zeigt, wie Sie ein Dialogfeld in der Besprechung verwenden können.":::

Sie können das Microsoft Teams-Anzeigebild und die Personenkarte des Benutzers auch zu Benachrichtigungen in Besprechungen hinzufügen, basierend auf einem `onBehalfOf`-Token mit Benutzer-MRI und dem in der Nutzlast übergebenen Anzeigenamen. Folgendes ist eine Beispielnutzlast:

```json
    {
       "type": "message",
       "text": "John Phillips assigned you a weekly todo",
       "summary": "Don't forget to meet with Marketing next week",
       "channelData": {
           onBehalfOf: [
             { 
               itemId: 0, 
               mentionType: 'person', 
               mri: context.activity.from.id, 
               displayname: context.activity.from.name 
             }
            ],
           "notification": {
           "alertInMeeting": true,
           "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
            }
        },
       "replyToId": "1493070356924"
    }
```

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-people-card.png" alt-text="Dieser Screenshot zeigt, wie Teams Bild- und Personenkarten in Besprechungsdialogfeldern anzeigt." border="true":::

## <a name="code-sample"></a>Codebeispiel

Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Besprechungsinterne Benachrichtigung | Veranschaulicht die Implementierung von Benachrichtigungen in Besprechungen mithilfe eines Bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs) |

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

Befolgen Sie die schrittweise Anleitung zum Generieren von Benachrichtigungen in der Besprechung in Ihrer [Teams-Besprechung](../sbs-meeting-content-bubble.yml) .

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Besprechungen](~/apps-in-teams-meetings/build-tabs-for-meeting.md)
* [Erstellen von Apps für teams-Besprechungsphase](build-apps-for-teams-meeting-stage.md)
* [Erstellen erweiterbarer Unterhaltungen für Besprechungschats](build-extensible-conversation-for-meeting-chat.md)
* [Erstellen von Apps für anonyme Benutzer](build-apps-for-anonymous-user.md)
* [Erweiterte Besprechungs-APIs](meeting-apps-apis.md)
