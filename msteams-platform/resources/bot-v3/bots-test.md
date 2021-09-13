---
title: Testen und Debuggen Ihres Bots
description: Beschreibt, wie Bots in Microsoft Teams getestet werden
keywords: Teams-Bots testen
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/20/2019
ms.openlocfilehash: 7d888d84434927cc22b4331ec51a01fb8905f555
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156442"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testen und Debuggen Ihres Microsoft Teams Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Beim Testen Ihres Bots müssen Sie sowohl die Kontext(en) berücksichtigen, in denen Ihr Bot ausgeführt werden soll, als auch alle Funktionen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben, die für Microsoft Teams spezifische Daten erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen Des Bots ausgewählt haben, mit der Funktionalität übereinstimmt.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen auf Teams

Die umfassendste Möglichkeit, Ihren Bot zu testen, besteht darin, ein App-Paket zu erstellen und in Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die Ihrem Bot in allen Bereichen zur Verfügung steht.

Es gibt zwei Methoden zum Hochladen Ihrer App. Sie können [Entweder App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden, um Ihnen zu helfen, oder Sie können manuell [ein App-Paket erstellen](~/concepts/build-and-test/apps-package.md) und Ihre App [hochladen.](~/concepts/deploy-and-publish/apps-upload.md) Wenn Sie Ihr Manifest ändern und Ihre App erneut hochladen müssen, sollten Sie [Ihren Bot löschen,](#deleting-a-bot-from-teams) bevor Sie das geänderte App-Paket hochladen.

## <a name="debug-your-bot-locally"></a>Lokal Debuggen des Bots

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten. Möglicherweise müssen Sie Ihrem Pfad ngrok hinzufügen.

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den https-Endpunkt, der von ngrok in Ihrem App-Manifest bereitgestellt wird. Wenn Sie Das Befehlsfenster schließen und neu starten, erhalten Sie eine neue URL, und Sie müssen Ihre Bot-Endpunktadresse aktualisieren, um diese auch zu verwenden.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testen Ihres Bots ohne Hochladen in Teams

Gelegentlich kann es erforderlich sein, Ihren Bot zu testen, ohne ihn als App in Teams zu installieren. Dazu stellen wir unten zwei Methoden bereit. Das Testen Ihres Bots, ohne ihn als App zu installieren, kann hilfreich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die gesamte Breite Microsoft Teams Funktionen testen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, befolgen Sie die Anweisungen zum Testen, indem Sie [sie hochladen.](#test-by-uploading-to-teams)

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulator

Die Bot Framework Emulator ist eine Desktopanwendung, mit der Botentwickler ihre Bots lokal oder remote testen und debuggen können. Mithilfe des Emulators können Sie mit Ihrem Bot chatten und die Nachrichten überprüfen, die Ihr Bot sendet und empfängt. Dies kann nützlich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und antwortet. Der Emulator ermöglicht es Ihnen jedoch nicht, Teams-spezifische Funktionalität zu testen, die Sie Ihrem Bot hinzugefügt haben, noch werden Antworten von Ihrem Bot eine genaue visuelle Darstellung ihrer Darstellung in Teams sein. Wenn Sie eines dieser Dinge testen müssen, ist es am [besten, Ihren Bot hochzuladen.](#test-by-uploading-to-teams)

Vollständige Anweisungen zu den Bot Framework Emulator finden Sie [hier.](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true)

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie mit Ihrem Bot direkt nach ID

>[!Important]
>Das Sprechen mit Ihrem Bot anhand der ID ist nur zu Testzwecken vorgesehen.

Sie können auch eine Unterhaltung mit Ihrem Bot mithilfe seiner ID initiieren. Im Folgenden finden Sie zwei Methoden dafür. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können keine anderen Microsoft Teams App-Funktionen wie Registerkarten oder Messaging-Erweiterungen nutzen.

1. Wählen Sie auf der [Seite "Bot-Dashboard"](https://dev.botframework.com/bots) für Ihren Bot unter **"Kanäle"** die Option **"Zu Microsoft Teams hinzufügen"** aus. Microsoft Teams wird mit einem persönlichen Chat mit Ihrem Bot gestartet.
2. Verweisen Sie direkt in Microsoft Teams auf die App-ID Ihres Bots:
   * Kopieren Sie auf der [Seite "Bot-Dashboard"](https://dev.botframework.com/bots) für Ihren Bot unter **"Details"** die **Microsoft-App-ID** für Ihren Bot.
  
     ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   * Wählen Sie in Microsoft Teams im **Chatbereich** das **Symbol "Chat hinzufügen"** aus. Fügen Sie für **"An:"** die Microsoft App-ID Ihres Bots ein.
  
     ![Hochladen der AppID für den Bot](~/assets/images/bots_uploading.png)

     Die App-ID sollte in Ihren Botnamen aufgelöst werden.

   * Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
   * Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnisseite zur Registerkarte "Kontakte", um Ihren Bot anzuzeigen und mit ihm zu chatten.

Ihr Bot empfängt das `conversationUpdate` Ereignis genau wie Bots, die einem Team hinzugefügt wurden, jedoch ohne die Teaminformationen im `channelData` Objekt.

## <a name="blocking-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Beachten Sie, dass Benutzer festlegen können, dass Ihr Bot keine persönlichen Chatnachrichten senden kann. Sie können dies umschalten, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und **bot-Unterhaltung blockieren** auswählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer diese Nachrichten jedoch nicht empfängt.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in der Teams-Ansicht auswählen. Beachten Sie, dass dadurch nur der Bot aus der Verwendung dieses Teams entfernt wird. Einzelne Benutzer können weiterhin im persönlichen Kontext interagieren.

Bots im persönlichen Kontext können nicht von einem Benutzer deaktiviert oder entfernt werden, kurz bevor der Bot vollständig aus Teams entfernt wird.

## <a name="disabling-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams Kanal. Deaktivieren Sie die Option **"Aktivieren bei Microsoft Teams".** Dies verhindert, dass Benutzer mit dem Bot interagieren, aber er ist weiterhin auffindbar, und Benutzer können ihn weiterhin zu Teams hinzufügen.

## <a name="deleting-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams zu entfernen, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams Kanal. Klicken Sie unten auf die Schaltfläche **"Löschen".** Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen oder mit diesem interagieren. Beachten Sie, dass dadurch der Bot nicht aus den Teams Instanzen anderer Benutzer entfernt wird, obwohl er auch für ihn nicht mehr funktioniert.

## <a name="removing-your-bot-from-appsource"></a>Entfernen Ihres Bots aus AppSource

Wenn Sie Ihren Bot aus Ihrer Teams-App in AppSource (zuvor Office Store) entfernen möchten, müssen Sie den Bot aus Ihrem App-Manifest entfernen und die App zur Überprüfung erneut übermitteln. Weitere Informationen finden Sie unter [Veröffentlichen Ihrer Microsoft Teams-App in AppSource.](~/concepts/deploy-and-publish/apps-publish.md)
