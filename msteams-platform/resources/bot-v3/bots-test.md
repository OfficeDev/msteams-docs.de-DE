---
title: Testen und Debuggen Ihres Bots
description: In diesem Artikel erfahren Sie, wie Sie Ihre Bots in Microsoft Teams testen und debuggen und Ihren Bot testen, ohne auf Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/20/2019
ms.openlocfilehash: 3cfb76443566a0ca5c279547f7b3db490c6095d3
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143697"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testen und debuggen Ihres Microsoft Teams-Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Beim Testen Ihres Bots müssen Sie sowohl den bzw. die Kontext(e) berücksichtigen, in denen der Bot ausgeführt werden soll, als auch alle Funktionen, die Sie evtl. zu Ihrem Bot hinzugefügt haben, die für Microsoft Teams spezifische Daten erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen Ihres Bots ausgewählt haben, mit ihrer Funktionalität übereinstimmt.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Microsoft Teams

Die umfassendste Methode zum Testen Ihres Bots besteht darin, ein App-Paket zu erstellen und es in Microsoft Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität Ihres Bot in allen Bereichen.

Es gibt zwei Methoden zum Hochladen Ihrer App. Sie können entweder [App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden oder [manuell ein App-Paket erstellen](~/concepts/build-and-test/apps-package.md) und [Ihre App hochladen](~/concepts/deploy-and-publish/apps-upload.md). Wenn Sie Ihr Manifest ändern und Ihre App erneut hochladen müssen, sollten Sie [Ihren Bot löschen](#deleting-a-bot-from-teams), bevor Sie das geänderte App-Paket hochladen.

## <a name="debug-your-bot-locally"></a>Lokales Debuggen Ihres Bots

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten. Unter Umständen müssen Sie ngrok zu Ihrem Pfad hinzufügen.

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten HTTPS-Endpunkt in Ihrem App-Manifest. Wenn Sie das Befehlsfenster schließen und einen Neustart durchführen, erhalten Sie eine neue URL und müssen Ihre Bot-Endpunktadresse aktualisieren, um auch diese zu verwenden.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testen Ihres Bots ohne Hochladen in Microsoft Teams

Gelegentlich ist es erforderlich, Ihren Bot zu testen, ohne ihn als App in Microsoft Teams zu installieren. Wir stellen zwei Methoden zum Testen bereit. Das Testen Ihres Bots, ohne ihn als App zu installieren, kann nützlich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die vollständige Breite an Microsoft Teams-Funktionen testen, die Sie eventuell zu Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, folgen Sie den Anweisungen zum [Testen durch Hochladen](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulators

Der Bot Framework Emulator ist eine Desktopanwendung, mit der Bot-Entwickler ihre Bots entweder lokal oder remote testen und debuggen können. Mithilfe des Emulators können Sie mit Ihrem Bot chatten und die Nachrichten überprüfen, die Ihr Bot sendet und empfängt. Dies kann nützlich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und reagiert. Der Emulator ermöglicht es Ihnen jedoch nicht, Teams-spezifische Funktionalität zu testen, die Sie Ihrem Bot hinzugefügt haben, und antworten von Ihrem Bot nicht als genaue visuelle Darstellung, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, ist es nicht am besten, [Ihren Bot hochzuladen](#test-by-uploading-to-teams).

Vollständige Anweisungen zum Bot Framework Emulator finden Sie [hier](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Direkt per ID mit Ihrem Bot kommunizieren

>[!Important]
>Die Kommunikation mit Ihrem Bot per ID ist nur für Testzwecke vorgesehen.

Sie können auch eine Unterhaltung mit Ihrem Bot mithilfe seiner ID initiieren. Hierfür sind nachfolgend zwei Methoden angegeben. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können keine anderen Microsoft Teams App-Funktionen wie Registerkarten oder Nachrichtenerweiterungen nutzen.

1. Wählen Sie auf der seite [Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Kanäle** die Option **Zu Microsoft Teams hinzufügen** aus. Microsoft Teams wird mit einem persönlichen Chat mit Ihrem Bot gestartet.
2. Verweisen Sie direkt in Microsoft Teams auf die App-ID Ihres Bots:
   * Kopieren Sie auf der seite [Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Details** die **Microsoft-App-ID** für Ihren Bot.
  
      :::image type="content" source="../../assets/images/bots_appid_botframework.png" alt-text="Bot-Dashboard":::
  
   * Wählen Sie in Microsoft Teams im **Chatbereich** das Symbol **Chat hinzufügen** aus. Fügen Sie für **An** die Microsoft App-ID Ihres Bots ein.
  
      :::image type="content" source="../../assets/images/bots_uploading.png" alt-text="Hochladen der AppID für den Bot"border="true":::

     Die App-ID sollte in Ihren Botnamen aufgelöst werden.

   * Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu starten.
   * Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnisseite zur Registerkarte "Personen", um Ihren Bot anzuzeigen und damit zu chatten.

Ihr Bot empfängt das `conversationUpdate`-Ereignis genau wie Bots, die einem Team hinzugefügt wurden, jedoch ohne die Teaminformationen im `channelData`-Objekt.

## <a name="blocking-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Benutzer können ihren Bot am Senden persönlicher Chatnachrichten hindern. Sie können dies aktivieren, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und **Bot-Unterhaltungen blockieren** auswählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer diese Nachrichten jedoch nicht erhält.

  :::image type="content" source="../../assets/images/bots/botdisable.png" alt-text="Blockieren eines Bots"border="true":::

## <a name="removing-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in ihrer Teams-Ansicht auswählen. Beachten Sie, dass dadurch nur die Nutzung des Bots im Team blockiert wird, einzelne Benutzer können im persönlichen Kontext interagieren.

Bots im persönlichen Kontext können nicht von einem Benutzer deaktiviert oder entfernt werden, ohne den Bot vollständig aus Teams zu entfernen.

## <a name="disabling-a-bot-in-teams"></a>Deaktivieren eines Bots in Microsoft Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams-Kanal. Deaktivieren Sie die Option **In Microsoft Teams aktivieren**. Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, aber er ist weiterhin auffindbar, und Benutzer können ihn Teams hinzufügen.

## <a name="deleting-a-bot-from-teams"></a>Löschen eines Bots aus Microsoft Teams

Um Ihren Bot vollständig aus Microsoft Teams zu entfernen, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams-Kanal. Klicken Sie auf die Schaltfläche **Löschen** am unteren Rand der Seite. Dadurch wird verhindert, dass Benutzer Ihren Bot auffinden, hinzufügen oder mit ihm interagieren. Dadurch wird der Bot nicht aus den Teams Instanzen anderer Benutzer entfernt, obwohl er auch für sie nicht mehr funktioniert.

## <a name="removing-your-bot-from-appsource"></a>Entfernen Ihres Bots aus AppSource

Wenn Sie Ihren Bot aus Ihrer Microsoft Teams-App in AppSource (zuvor Office Store) entfernen möchten, müssen Sie ihn aus Ihrem App-Manifest entfernen und die App erneut zur Überprüfung übermitteln. Weitere Informationen finden Sie unter [Veröffentlichen Ihrer Microsoft Teams-App in AppSource](~/concepts/deploy-and-publish/apps-publish.md).
