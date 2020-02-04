---
title: Testen und Debuggen des bot lokal
author: clearab
description: Testen und Debuggen Ihres bot lokal mit einer IDE
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 8494302b41e33910cb33f8c6889d82505b703577
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674215"
---
# <a name="test-and-debug-your-bot-locally"></a>Testen und Debuggen des bot lokal

Wenn Sie Ihren bot testen, müssen Sie sowohl den Kontext (die), den Sie für Ihren bot ausführen möchten, als auch alle Funktionen berücksichtigen, die Sie Ihrem bot möglicherweise hinzugefügt haben und für Microsoft Teams spezifische Daten benötigen. Stellen Sie sicher, dass die Methode, die Sie zum Testen Ihres bot ausgewählt haben, mit der Funktionalität übereinstimmt.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Microsoft Teams

Die umfassendste Möglichkeit zum Testen Ihres bot besteht darin, ein App-Paket zu erstellen und es in Microsoft Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die für Ihren bot zur Verfügung steht, über alle Bereiche hinweg.

Es gibt zwei Methoden zum Hochladen Ihrer APP. Sie können entweder [App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden, um Ihnen zu helfen, oder Sie können [ein App-Paket manuell erstellen](~/concepts/build-and-test/apps-package.md) und [Ihre APP hochladen](~/concepts/deploy-and-publish/apps-upload.md). Wenn Sie Ihr Manifest ändern und Ihre APP erneut hochladen müssen, sollten Sie [ihren bot](#deleting-a-bot-from-teams) vor dem Hochladen Ihres geänderten App-Pakets löschen.

## <a name="debug-your-bot-locally"></a>Debuggen des bot lokal

Wenn Sie Ihren bot während der Entwicklung lokal hosten, müssen Sie einen Tunnel Dienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunnel Dienst zu starten (möglicherweise müssen Sie ngrok zu Ihrem Pfad hinzufügen).

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten HTTPS-Endpunkt in Ihrem App-Manifest. Wenn Sie das Befehlsfenster schließen und neu starten, erhalten Sie eine neue URL, und Sie müssen ihre bot-Endpunktadresse so aktualisieren, dass diese ebenfalls verwendet wird.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testen Ihres bot ohne hochladen in Microsoft Teams

Gelegentlich kann es erforderlich sein, ihren bot zu testen, ohne ihn als app in Microsoft Teams zu installieren. Hierzu stehen zwei Methoden zur Verfügung. Das Testen Ihres bot ohne Installation als APP kann nützlich sein, um sicherzustellen, dass Ihr bot verfügbar ist und reagiert, aber Sie können nicht die gesamte Bandbreite der Microsoft Teams-Funktionen testen, die Sie Ihrem bot möglicherweise hinzugefügt haben. Wenn Sie Ihren bot vollständig testen müssen, befolgen Sie die Anweisungen zum [Testen durch Hochladen](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Verwenden des bot-Emulators

Der bot Framework-Emulator ist eine Desktopanwendung, die bot-Entwicklern das Testen und Debuggen Ihrer Bots entweder lokal oder Remote ermöglicht. Mit dem Emulator können Sie mit Ihrem bot chatten und die von Ihrem bot gesendeten und empfangenen Nachrichten überprüfen. Dies kann nützlich sein, um zu überprüfen, ob Ihr bot verfügbar ist und reagiert, aber der Emulator erlaubt Ihnen nicht, alle Teams-spezifischen Funktionen zu testen, die Sie Ihrem bot hinzugefügt haben, und auch Antworten von Ihrem bot werden keine präzise visuelle Darstellung dessen sein, was Sie tun werden. in Microsoft Teams gerendert werden. Wenn Sie eines dieser beiden Dinge testen müssen, ist es am besten, [ihren bot hochzuladen](#test-by-uploading-to-teams).

Ausführliche Anweisungen zum bot Framework-Emulator finden Sie [hier](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0).

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie mit Ihrem bot direkt über ID

>[!Important]
>Das Gespräch mit Ihrem bot durch ID ist nur für grundlegende Testzwecke gedacht. Alle Teams-spezifischen Funktionen, die Sie Ihrem bot hinzugefügt haben, können nicht verwendet werden.

Sie können auch eine Unterhaltung mit Ihrem bot initiieren, indem Sie dessen ID verwenden. Im folgenden sind zwei Methoden aufgeführt. Wenn ein bot durch eine dieser Methoden hinzugefügt wurde, kann er nicht in Kanal Unterhaltungen verwendet werden, und Sie können nicht von anderen Microsoft Teams-App-Funktionen wie Registerkarten oder Messaging Erweiterungen profitieren.

1. Wählen Sie auf der Seite [bot-Dashboard](https://dev.botframework.com/bots) für Ihren bot unter **Kanäle**die Option **zu Microsoft Teams hinzufügen**aus. Microsoft Teams wird mit einem persönlichen Chat mit Ihrem bot gestartet.
2. Verweisen Sie direkt in Microsoft Teams auf die APP-ID Ihres bot:
   * Kopieren Sie auf der Seite [bot-Dashboard](https://dev.botframework.com/bots) für Ihren bot unter **Details**die **Microsoft-App-ID** für Ihren bot.
  
     ![Aufrufen der-Anwendungskennung für den bot](~/assets/images/bots_appid_botframework.png)
  
   * Wählen Sie in Microsoft Teams im **Chat** Bereich das Symbol **Chat hinzufügen** aus. **Um:**, fügen Sie die Microsoft-App-ID Ihres bot ein.
  
     ![Aufrufen der-Anwendungskennung für den bot](~/assets/images/bots_uploading.png)

     Die APP-ID sollte in ihren bot-Namen aufgelöst werden.

   * Wählen Sie Ihren bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
   * Alternativ können Sie die APP-ID Ihres bot in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnisseite zur Registerkarte Personen, um Ihren bot anzuzeigen und damit zu beginnen, damit zu chatten.

Ihr bot erhält das `conversationUpdate` Ereignis genauso wie Bots, die einem Team hinzugefügt wurden, jedoch ohne die Team `channelData` Informationen im Objekt.

## <a name="blocking-a-bot-in-personal-chat"></a>Blockieren eines bot im persönlichen Chat

Beachten Sie, dass Benutzer entscheiden können, ihren bot am Senden persönlicher Chatnachrichten zu hindern. Sie können dies umschalten, indem Sie mit der rechten Maustaste auf Ihren bot im Chat Kanal klicken und die Option bot-unter **Haltung blockieren**wählen. Dies bedeutet, dass ihre Bots weiterhin Nachrichten senden, aber der Benutzer wird diese Nachrichten nicht erhalten.

![Blockieren eines bot](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Entfernen eines bot aus einem Team

Benutzer können den bot löschen, indem Sie das Papierkorbsymbol in der Liste "Bots" in der Ansicht "Teams" auswählen. Beachten Sie, dass dadurch nur der bot aus der Verwendung dieses Teams entfernt wird; einzelne Benutzer können weiterhin im persönlichen Kontext interagieren.

Bots im persönlichen Kontext können nicht deaktiviert oder von einem Benutzer entfernt werden, ohne dass der bot von Microsoft Teams vollständig entfernt wird.

## <a name="disabling-a-bot-in-teams"></a>Deaktivieren eines bot in Microsoft Teams

Um Ihren bot beim Empfang von Nachrichten zu beenden, wechseln Sie zu Ihrem bot-Dashboard, und bearbeiten Sie den Microsoft Teams-Kanal. Deaktivieren Sie die Option **auf Microsoft Teams aktivieren** . Dadurch wird verhindert, dass Benutzer mit dem bot interagieren, er kann jedoch weiterhin erkannt werden, und die Benutzer können ihn weiterhin zu Microsoft Teams hinzufügen.

## <a name="deleting-a-bot-from-teams"></a>Löschen eines bot aus Microsoft Teams

Wenn Sie Ihren bot vollständig aus Microsoft Teams entfernen möchten, wechseln Sie zu Ihrem bot-Dashboard, und bearbeiten Sie den Microsoft Teams-Kanal. Klicken Sie unten auf die Schaltfläche **Löschen** . Dadurch wird verhindert, dass Benutzer ihren bot entdecken, hinzufügen oder mit ihr interagieren. Beachten Sie, dass dadurch der bot nicht aus den Teams-Instanzen anderer Benutzer entfernt wird, obwohl er auch für Sie nicht mehr funktioniert.
