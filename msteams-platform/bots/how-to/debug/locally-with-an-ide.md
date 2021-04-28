---
title: Testen und Debuggen des Bots lokal
author: clearab
description: Testen und Debuggen des Bots lokal mit einer IDE
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 52676d35599560704e5bb72d85e09860174fdaf1
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058376"
---
# <a name="test-and-debug-your-bot-locally"></a>Testen und Debuggen des Bots lokal

Beim Testen Ihres Bots müssen Sie sowohl die Kontexte berücksichtigen, in denen Ihr Bot ausgeführt werden soll, als auch alle Funktionen, die Sie ihrem Bot hinzugefügt haben, die für Microsoft Teams spezifische Daten erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen des Bots auswählen, mit der Funktionalität des Bots in Einklang ist.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Teams

Die umfassendste Methode zum Testen Ihres Bots ist das Erstellen eines App-Pakets und das Hochladen in Teams. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die Ihrem Bot für alle Bereiche zur Verfügung steht.

Es gibt zwei Methoden zum Hochladen Ihrer App:
* Verwenden [von App Studio](~/concepts/build-and-test/app-studio-overview.md).
* [Erstellen Sie ein App-Paket](~/concepts/build-and-test/apps-package.md) manuell, und laden Sie [dann Ihre App hoch.](~/concepts/deploy-and-publish/apps-upload.md)

> [!NOTE]
> Wenn Sie Ihr Manifest ändern und Ihre App [](#delete-a-bot-from-teams) erneut hochladen müssen, müssen Sie den Bot löschen, bevor Sie Ihr geändertes App-Paket hochladen.

## <a name="debug-your-bot-locally"></a>Lokal debuggen des Bots

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, fügen Sie dem Pfad hinzu, und führen Sie den folgenden Befehl aus, um den `ngrok` Tunneldienst zu starten:

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten https-Endpunkt in Ihrem App-Manifest. 

> [!NOTE]
> Wenn Sie das Befehlsfenster schließen und neu starten, wird eine neue URL generiert, und Sie müssen Ihre Botendpunktadresse aktualisieren, damit sie verwendet wird.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testen Des Bots ohne Hochladen in Teams

Gelegentlich kann es erforderlich sein, Ihren Bot zu testen, ohne ihn als App in Teams zu installieren. Wir bieten zwei Methoden zum Testen des Bots. Das Testen Ihres Bots ohne die Installation als App kann hilfreich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die gesamte Bandbreite der Microsoft Teams-Funktionen testen, die Sie Ihrem Bot möglicherweise hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, lesen Sie [Tests durch Hochladen](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulators

Der Bot-Framework-Emulator ist eine Desktopanwendung, mit der Botentwickler ihre Bots lokal oder remote testen und debuggen können. Der Emulator hilft Ihnen, mit Ihrem Bot zu chatten und die Nachrichten zu überprüfen, die Ihr Bot sendet und empfängt. Dies kann hilfreich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und reagiert. Der Emulator ermöglicht es Ihnen jedoch nicht, teamsspezifische Funktionen zu testen, die Sie dem Bot hinzugefügt haben, und die Antworten ihres Bots sind keine genaue visuelle Darstellung, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, laden Sie ihren [Bot am besten hoch.](#test-by-uploading-to-teams)

Weitere Informationen finden Sie [unter vollständige Anweisungen im Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie direkt per ID mit Ihrem Bot.

> [!Important]
> Das Sprechen mit Ihrem Bot nach ID ist nur für grundlegende Testzwecke vorgesehen. Alle Teams-spezifischen Funktionen, die Sie Ihrem Bot hinzugefügt haben, funktionieren nicht.

Sie können auch eine Unterhaltung mit Ihrem Bot mithilfe der ID initiieren. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, kann er in Kanalunterhaltungen nicht adressiert werden, und Sie können andere Microsoft Teams-App-Funktionen wie Registerkarten oder Messagingerweiterungen nicht nutzen. Sie können eine Unterhaltung auf eine der folgenden Arten initiieren:

* Wählen Sie [auf der Seite Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Kanäle** die Option Zu Microsoft Teams **hinzufügen aus.** Microsoft Teams startet einen persönlichen Chat mit Ihrem Bot.

* Verweisen Sie direkt auf die App-ID Ihres Bots in Microsoft Teams:
   1. Kopieren Sie [auf der Seite Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Details** die **Microsoft App-ID** für Ihren Bot.
  
      ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   2. Öffnen Sie Microsoft Teams, wählen Sie im **Chatbereich** das Symbol **Chat hinzufügen** aus. Fügen **Sie in An:** die Microsoft App-ID Ihres Bots ein.
  
      ![Hochladen von Bots](~/assets/images/bots_uploading.png)

      Die App-ID muss in Ihren Botnamen aufgelöst werden.

   3. Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
      Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnissetseite zur Registerkarte **Personen,** um Ihren Bot zu sehen und mit dem Chat zu beginnen.

Ihr Bot empfängt das Ereignis, wenn Sie die Bots zu einem Team hinzufügen, ohne dass die `conversationUpdate` Teaminformationen im Objekt `channelData` enthalten sind.

## <a name="block-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Benutzer können ihren Bot am Senden persönlicher Chatnachrichten blockieren. Sie können dies umschalten, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und **Bot-Unterhaltung blockieren auswählen.** Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer die Nachrichten jedoch nicht erhält.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in der Ansicht ihres Teams auswählen. Dadurch wird nur der Bot aus der Verwendung dieses Teams entfernt, einzelne Benutzer können weiterhin im persönlichen Kontext interagieren. Bots im persönlichen Kontext können nicht von Benutzern deaktiviert oder entfernt werden.

## <a name="disable-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem **Bot-Dashboard,** und bearbeiten Sie den Microsoft Teams-Kanal. Deaktivieren Sie **die Option Aktivieren in Microsoft Teams.** Auf diese Weise wird verhindert, dass Benutzer mit dem Bot interagieren, er kann jedoch weiterhin ermittelt werden, und Benutzer können ihn weiterhin zu Teams hinzufügen.

## <a name="delete-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams zu entfernen, wechseln Sie zu Ihrem **Bot-Dashboard,** und bearbeiten Sie den Microsoft Teams-Kanal. Klicken Sie **unten** auf die Schaltfläche Löschen. Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen und mit ihm interagieren. Dadurch wird der Bot nicht aus den Teams-Instanzen anderer Benutzer entfernt, er funktioniert jedoch auch nicht mehr für sie.

## <a name="see-also"></a>Siehe auch

- [Bot mit Inspektions-Middleware debuggen](/azure/bot-service/bot-service-debug-inspection-middleware)

- [Anruf- und Besprechungsbot lokal debuggen](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
