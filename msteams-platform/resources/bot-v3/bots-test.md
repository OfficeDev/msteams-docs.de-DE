---
title: Testen und Debuggen des Bots
description: Beschreibt das Testen von Bots in Microsoft Teams
keywords: Teams-Bots-Tests
ms.topic: how-to
localization_priority: Normal
ms.date: 03/20/2019
ms.openlocfilehash: 0f44a88bcf054f4e0f4112ddc8bd3fbfdc18117d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020632"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testen und Debuggen des Microsoft Teams Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Beim Testen Ihres Bots müssen Sie sowohl den Kontext(n) berücksichtigen, in dem Der Bot ausgeführt werden soll, als auch alle Funktionen, die Sie ihrem Bot hinzugefügt haben, die spezifische Daten für die Microsoft Teams. Stellen Sie sicher, dass die Methode, die Sie zum Testen des Bots ausgewählt haben, mit der Funktionalität des Bots in Einklang ist.

## <a name="test-by-uploading-to-teams"></a>Testen Durch Hochladen in Teams

Die umfassendste Methode zum Testen Ihres Bots ist das Erstellen eines App-Pakets und das Hochladen in Teams. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die Ihrem Bot für alle Bereiche zur Verfügung steht.

Es gibt zwei Methoden zum Hochladen Ihrer App. Sie können Entweder [App Studio verwenden,](~/concepts/build-and-test/app-studio-overview.md) um Ihnen zu helfen, oder Sie können manuell ein App-Paket [erstellen](~/concepts/build-and-test/apps-package.md) und Ihre [App hochladen.](~/concepts/deploy-and-publish/apps-upload.md) Wenn Sie Ihr Manifest ändern und Ihre App [](#deleting-a-bot-from-teams) erneut hochladen müssen, sollten Sie den Bot löschen, bevor Sie Ihr geändertes App-Paket hochladen.

## <a name="debug-your-bot-locally"></a>Lokal debuggen des Bots

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten (Möglicherweise müssen Sie ngrok zu Ihrem Pfad hinzufügen).

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten https-Endpunkt in Ihrem App-Manifest. Wenn Sie das Befehlsfenster schließen und neu starten, erhalten Sie eine neue URL, und Sie müssen Ihre Botendpunktadresse aktualisieren, um auch diese zu verwenden.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testen Des Bots ohne Hochladen in Teams

Gelegentlich kann es erforderlich sein, Ihren Bot zu testen, ohne ihn als App in einem Teams. Hier finden Sie zwei Methoden. Das Testen Ihres Bots ohne Die Installation als App kann hilfreich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die gesamte Bandbreite der Microsoft Teams-Funktionen testen, die Sie Ihrem Bot möglicherweise hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, befolgen Sie bitte die Anweisungen zum [Testen, indem Sie hochladen.](#test-by-uploading-to-teams)

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulators

Die Bot Framework Emulator ist eine Desktopanwendung, mit der Botentwickler ihre Bots lokal oder remote testen und debuggen können. Mithilfe des Emulators können Sie mit Ihrem Bot chatten und die Nachrichten überprüfen, die Ihr Bot sendet und empfängt. Dies kann nützlich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und reagiert. Der Emulator ermöglicht es Ihnen jedoch nicht, eine Teams-spezifische Funktionalität zu testen, die Sie Ihrem Bot hinzugefügt haben, und auch Antworten von Ihrem Bot sind keine genaue visuelle Darstellung, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, laden Sie ihren [Bot am besten hoch.](#test-by-uploading-to-teams)

Vollständige Anweisungen zum Bot Framework Emulator finden Sie [hier](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie direkt per ID mit Ihrem Bot.

>[!Important]
>Das Sprechen mit Ihrem Bot per ID ist nur zu Testzwecken vorgesehen.

Sie können auch eine Unterhaltung mit Ihrem Bot mit seiner ID initiieren. Im Folgenden finden Sie zwei Methoden dazu. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können keine anderen Microsoft Teams-App-Funktionen wie Registerkarten oder Messagingerweiterungen nutzen.

1. Wählen Sie [auf der Seite Botdashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Kanäle** die Option Hinzufügen **zu Microsoft Teams**. Microsoft Teams wird mit einem persönlichen Chat mit Ihrem Bot gestartet.
2. Verweisen Sie direkt auf die App-ID Ihres Bots innerhalb Microsoft Teams:
   * Kopieren Sie [auf der Seite Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Details** die **Microsoft App-ID** für Ihren Bot.
  
     ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   * Wählen Sie Microsoft Teams im **Chatbereich** das Symbol Chat **hinzufügen** aus. Fügen **Sie für An:** die Microsoft App-ID Ihres Bots ein.
  
     ![Hochladen der AppID für den Bot](~/assets/images/bots_uploading.png)

     Die App-ID sollte in Ihren Botnamen aufgelöst werden.

   * Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
   * Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in der Microsoft Teams. Navigieren Sie auf der Suchergebnissetseite zur Registerkarte Personen, um Ihren Bot zu sehen und mit dem Chat zu beginnen.

Ihr Bot erhält das Ereignis genauso wie Bots, die einem Team hinzugefügt wurden, jedoch ohne `conversationUpdate` die Teaminformationen im `channelData` Objekt.

## <a name="blocking-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Beachten Sie, dass Benutzer ihren Bot am Senden persönlicher Chatnachrichten blockieren können. Sie können dies umschalten, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und **Bot-Unterhaltung blockieren auswählen.** Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer diese Nachrichten jedoch nicht erhält.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in ihrer Teams-Ansicht auswählen. Beachten Sie, dass dadurch nur der Bot aus der Verwendung dieses Teams entfernt wird. Einzelne Benutzer können weiterhin im persönlichen Kontext interagieren.

Bots im persönlichen Kontext können nicht von einem Benutzer deaktiviert oder entfernt werden, es ist nicht möglich, den Bot vollständig aus Teams.

## <a name="disabling-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams Kanal. Deaktivieren Sie **die Option Microsoft Teams** aktivieren. Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, aber er kann weiterhin ermittelt werden, und Benutzer können ihn weiterhin zu Teams hinzufügen.

## <a name="deleting-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams entfernen, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams Kanal. Klicken Sie **unten** auf die Schaltfläche Löschen. Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen oder mit ihm interagieren. Beachten Sie, dass dadurch der Bot nicht aus den Teams anderen Benutzern entfernt wird, obwohl er auch für sie nicht mehr funktioniert.

## <a name="removing-your-bot-from-appsource"></a>Entfernen des Bots aus AppSource

Wenn Sie Ihren Bot aus Ihrer Teams-App in AppSource (ehemals Office Store) entfernen möchten, müssen Sie den Bot aus Ihrem App-Manifest entfernen und Ihre App zur Überprüfung erneut übermitteln. Weitere Informationen finden Sie unter Publish [your Microsoft Teams app to AppSource.](~/concepts/deploy-and-publish/apps-publish.md)
