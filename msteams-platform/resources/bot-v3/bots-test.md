---
title: Testen und debuggen Sie Ihren Bot
description: Beschreibt das Testen von Bots in Microsoft Teams
keywords: Teams Bots-Tests
ms.topic: how-to
localization_priority: Normal
ms.date: 03/20/2019
ms.openlocfilehash: 269b0680e45d764cf4cb0269c40d3d202145edb8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566460"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testen und debuggen Sie Ihren Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Beim Testen Ihres Bots müssen Sie sowohl den Kontext berücksichtigen, in dem Ihr Bot ausgeführt werden soll, als auch alle Funktionen, die Sie Ihrem Bot hinzugefügt haben, die datenspezifische Daten für Microsoft Teams erfordert. Stellen Sie sicher, dass die Methode, die Sie zum Testen des Bots gewählt haben, an seiner Funktionalität ausgerichtet ist.

## <a name="test-by-uploading-to-teams"></a>Testen, indem Sie in Teams hochladen

Die umfassendste Möglichkeit, Ihren Bot zu testen, besteht darin, ein App-Paket zu erstellen und es in Teams hochzuladen. Dies ist die einzige Methode, um die volle Funktionalität, die Ihrem Bot zur Verfügung steht, über alle Bereiche hinweg zu testen.

Es gibt zwei Methoden zum Hochladen Ihrer App. Sie können [entweder App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden, um Ihnen zu helfen, oder Sie können manuell [ein App-Paket erstellen](~/concepts/build-and-test/apps-package.md) und Ihre App [hochladen.](~/concepts/deploy-and-publish/apps-upload.md) Wenn Sie Ihr Manifest ändern und Ihre App erneut hochladen müssen, sollten Sie [Ihren Bot löschen,](#deleting-a-bot-from-teams) bevor Sie Ihr geändertes App-Paket hochladen.

## <a name="debug-your-bot-locally"></a>Debuggen Sie Ihren Bot lokal

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneling-Service wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten. Möglicherweise müssen Sie Ihrem Pfad ngrok hinzufügen.

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den https-Endpunkt, der von ngrok in Ihrem App-Manifest bereitgestellt wird. Wenn Sie das Befehlsfenster schließen und neu starten, erhalten Sie eine neue URL, und Sie müssen Ihre Bot-Endpunktadresse aktualisieren, um auch diese zu verwenden.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testen Ihres Bots ohne Upload auf Teams

Gelegentlich kann es notwendig sein, Ihren Bot zu testen, ohne ihn als App in Teams zu installieren. Wir bieten zwei Methoden, um dies unten zu tun. Testen Sie Ihren Bot, ohne ihn als App zu installieren, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert, aber es wird Ihnen nicht erlauben, die volle Breite der Microsoft Teams Funktionalität zu testen, die Sie Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, folgen Sie bitte den Anweisungen zum [Testen, indem Sie hochladen.](#test-by-uploading-to-teams)

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulators

Die Bot Framework Emulator ist eine Desktop-Anwendung, mit der Bot-Entwickler ihre Bots lokal oder remote testen und debuggen können. Mit dem Emulator können Sie mit Ihrem Bot chatten und die Nachrichten überprüfen, die Ihr Bot sendet und empfängt. Dies kann nützlich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und reagiert, aber der Emulator erlaubt es Ihnen nicht, Teams-spezifische Funktionalität zu testen, die Sie Ihrem Bot hinzugefügt haben, noch werden Antworten von Ihrem Bot eine genaue visuelle Darstellung davon sein, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, ist es am besten, [Ihren Bot hochzuladen.](#test-by-uploading-to-teams)

Vollständige Anweisungen zum Bot Framework Emulator finden Sie [hier](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie direkt mit Ihrem Bot durch Id

>[!Important]
>Das Gespräch mit Ihrem Bot von Id ist nur zu Testzwecken gedacht.

Sie können auch eine Unterhaltung mit Ihrem Bot initiieren, indem Sie seine ID verwenden. Im Folgenden werden zwei Methoden dafür aufgeführt. Wenn ein Bot durch eine dieser Methoden hinzugefügt wurde, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können andere Microsoft Teams App-Funktionen wie Registerkarten oder Messagingerweiterungen nicht nutzen.

1. Wählen Sie auf der [Seite Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Kanäle** die Option **Zu Microsoft Teams hinzufügen** aus. Microsoft Teams startet mit einem persönlichen Chat mit Ihrem Bot.
2. Direkt verweisen Sie auf die App-ID Ihres Bots innerhalb Microsoft Teams:
   * Kopieren Sie auf der [Seite Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Details** die **Microsoft App-ID** für Ihren Bot.
  
     ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   * Wählen Sie im **Chat-Bereich** innerhalb Microsoft Teams das Symbol **Chat hinzufügen** aus. Für **An:** fügen Sie die Microsoft App ID Ihres Bots ein.
  
     ![Hochladen der AppID für den Bot](~/assets/images/bots_uploading.png)

     Die App-ID sollte in Ihren Bot-Namen aufgelöst werden.

   * Wählen Sie Ihren Bot aus und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
   * Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Seite mit den Suchergebnissen zur Registerkarte Personen, um Ihren Bot zu sehen und mit ihm zu chatten.

Ihr Bot wird das Ereignis genauso empfangen `conversationUpdate` wie Bots, die einem Team hinzugefügt wurden, aber ohne die Teaminformationen im `channelData` Objekt.

## <a name="blocking-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Beachten Sie, dass Benutzer ihren Bot daran hindern können, persönliche Chat-Nachrichten zu senden. Sie können dies umschalten, indem Sie mit der rechten Maustaste auf Ihren Bot im Chat-Kanal klicken und **Block Bot-Unterhaltung** wählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, aber der Benutzer wird diese Nachrichten nicht empfangen.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Mülleimer-Symbol in der Bots-Liste in ihrer Teamansicht auswählen. Beachten Sie, dass dadurch nur der Bot aus der Verwendung dieses Teams entfernt wird. einzelne Benutzer werden weiterhin in der Lage sein, im persönlichen Kontext zu interagieren.

Bots im persönlichen Kontext können nicht von einem Benutzer deaktiviert oder entfernt werden, da der Bot nicht vollständig aus Teams entfernt wurde.

## <a name="disabling-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um den Empfang von Nachrichten durch Ihren Bot zu verhindern, gehen Sie zu Ihrem Bot-Dashboard und bearbeiten Sie den Microsoft Teams-Kanal. Deaktivieren Sie die Option **Aktivieren Microsoft Teams.** Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, aber es wird immer noch erkennbar sein und Benutzer werden immer noch in der Lage sein, es zu Teams hinzuzufügen.

## <a name="deleting-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams zu entfernen, gehen Sie zu Ihrem Bot-Dashboard und bearbeiten Sie den Microsoft Teams-Kanal. Wählen Sie unten die Schaltfläche **Löschen** aus. Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen oder mit ihm interagieren. Beachten Sie, dass dies den Bot nicht aus den Teams Instanzen anderer Benutzer entfernt, obwohl er auch für sie nicht mehr funktioniert.

## <a name="removing-your-bot-from-appsource"></a>Entfernen Ihres Bots aus AppSource

Wenn Sie Ihren Bot aus Ihrer Teams-App in AppSource entfernen möchten (zuvor Office Store), müssen Sie den Bot aus Ihrem App-Manifest entfernen und Ihre App zur Validierung erneut übermitteln. Weitere Informationen finden Sie unter [Veröffentlichen Ihrer Microsoft Teams-App in AppSource](~/concepts/deploy-and-publish/apps-publish.md).
