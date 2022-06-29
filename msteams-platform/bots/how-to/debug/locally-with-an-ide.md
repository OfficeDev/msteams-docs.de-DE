---
title: Testen und Debuggen Ihres Bots lokal
author: surbhigupta
description: Erfahren Sie mehr über das Testen und Debuggen Ihres Bots lokal mit einer IDE in der Teams-Umgebung durch Querladen und mehr
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 3e1225991ad240f74e045a6941002b9eb7b5e81d
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503718"
---
# <a name="test-and-debug-your-bot-locally-with-ide"></a>Testen und Debuggen Des Bots lokal mit IDE

Beim Testen Ihres Bots müssen Sie sowohl den Kontext berücksichtigen, in dem Ihr Bot ausgeführt werden soll, als auch alle Funktionen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben, die für Microsoft Teams spezifische Daten erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen Ihres Bots ausgewählt haben, seiner Funktionalität entspricht.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Microsoft Teams

Die umfassendste Methode zum Testen Ihres Bots besteht darin, ein App-Paket zu erstellen und es in Microsoft Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität Ihres Bot in allen Bereichen.

Es gibt zwei Methoden zum Hochladen Ihrer App:

* Verwenden Sie [App Studio](~/concepts/build-and-test/app-studio-overview.md).
* [Erstellen Sie ein App-Paket](~/concepts/build-and-test/apps-package.md) manuell, und [laden Sie die App](~/concepts/deploy-and-publish/apps-upload.md) hoch.

> [!NOTE]
> Um das Manifest zu ändern und Ihre App erneut hochzuladen, [löschen Sie den Bot](#delete-a-bot-from-teams), bevor Sie das geänderte App-Paket hochladen.
> Um den Bot zu testen, aktivieren Sie das Querladen in Teams. Siehe [Aktivieren des Querladens](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

## <a name="debug-your-bot-locally"></a>Lokales Debuggen Ihres Bots

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, fügen Sie Ihrem Pfad `ngrok` hinzu, und führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten:

```bash
ngrok http <port> --host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten HTTPS-Endpunkt in Ihrem App-Manifest.

> [!NOTE]
> Wenn Sie das Befehlsfenster schließen und einen Neustart durchführen, erhalten Sie eine neue URL und müssen Ihre Bot-Endpunktadresse aktualisieren, um auch diese zu verwenden.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testen Ihres Bots ohne Hochladen in Microsoft Teams

Gelegentlich ist es erforderlich, Ihren Bot zu testen, ohne ihn als App in Microsoft Teams zu installieren. Wir stellen zwei Methoden zum Testen des Bots bereit. Das Testen Ihres Bots, ohne ihn als App zu installieren, kann nützlich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Es ermöglicht Ihnen jedoch nicht, die gesamte Bandbreite der Microsoft Teams-Funktionen zu testen, die Sie Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen möchten, sehen Sie sich [Testen durch Hochladen](#test-by-uploading-to-teams) an.

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulators

Der Bot Framework Emulator ist eine Desktopanwendung, die es Bot-Entwicklern ermöglicht, ihre Bots entweder lokal oder remote zu testen und zu debuggen. Der Emulators hilft Ihnen mit Ihrem Bot zu chatten und die Nachrichten zu überprüfen, die Ihr Bot sendet und empfängt. Dies ist hilfreich, um zu überprüfen, ob Ihr Bot verfügbar ist und reagiert. Der Emulator ermöglicht es Ihnen jedoch nicht, Teams-spezifischen Funktionen zu testen, die Sie dem Bot hinzugefügt haben, und die Antworten von Ihrem Bot stellen keine genaue visuelle Darstellung dar, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, ist es am besten, [Ihren Bot hochzuladen](#test-by-uploading-to-teams).

Weitere Informationen finden Sie in den [vollständigen Anweisungen zum Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Direkt per ID mit Ihrem Bot kommunizieren

> [!Important]
> Die Kommunikation mit Ihrem Bot per ID ist nur für grundlegende Testzwecke vorgesehen. Alle Teams-spezifischen Funktionen, die Sie Ihrem Bot hinzugefügt haben, funktionieren nicht.

Initiieren Sie eine Unterhaltung mit Ihrem Bot mithilfe seiner ID. Wenn ein Bot über eine dieser Methoden hinzugefügt wird, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können keine anderen Teams-App-Funktionen wie Registerkarten oder Nachrichtenerweiterungen nutzen. Initiieren Sie eine Unterhaltung auf eine der folgenden Arten:

* Wählen Sie auf der seite [Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Kanäle** die Option **Zu Microsoft Teams hinzufügen** aus. Teams startet einen persönlichen Chat mit Ihrem Bot.

* Verweisen Sie direkt in Teams auf die App-ID Ihres Bots:
   1. Kopieren Sie auf der seite [Bot-Dashboard](https://dev.botframework.com/bots) für Ihren Bot unter **Details** die **Microsoft-App-ID** für Ihren Bot.
  
      ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   2. Wählen Sie in Microsoft Teams im **Chatbereich** das Symbol **Chat hinzufügen** aus. Fügen Sie im Feld **An:** die Microsoft App-ID Ihres Bots ein.
  
      ![Hochladen von Bots](~/assets/images/bots_uploading.png)

      Die App-ID muss in Ihrem Botnamen aufgelöst werden.

   3. Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu starten.
      Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Teams einfügen. Wechseln Sie auf der Suchergebnisseite zur Registerkarte **Personen**, um Ihren Bot anzuzeigen und damit zu chatten.

> [!Note]
> Damit Teams auf die App-ID Ihres Bots verweisen kann, aktivieren Sie [das Querladen von Apps](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

Ihr Bot empfängt das `conversationUpdate`-Ereignis, wenn Sie die Bots zu einem Team hinzufügen, jedoch ohne die Teaminformationen im `channelData`-Objekt.

## <a name="block-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Benutzer können ihren Bot am Senden persönlicher Chatnachrichten hindern. Sie können dies aktivieren, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und **Bot-Unterhaltungen blockieren** auswählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer empfängt die Nachrichten jedoch nicht.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie in ihrer Teams-Ansicht in der Bots-Liste das Papierkorbsymbol auswählen. Dadurch wird nur der Bot aus der Verwendung dieses Teams entfernt. Einzelne Benutzer können weiterhin im persönlichen Kontext interagieren. Bots im persönlichen Kontext können von Benutzern nicht deaktiviert oder entfernt werden.

## <a name="disable-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem **Bot-Dashboard**, und bearbeiten Sie den Teams-Kanal. Deaktivieren Sie die Option **In Microsoft Teams aktivieren**. Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, aber er ist weiterhin auffindbar, und Benutzer können ihn Teams hinzufügen.

## <a name="delete-a-bot-from-teams"></a>Löschen eines Bots aus Microsoft Teams

Um Ihren Bot vollständig aus Microsoft Teams zu entfernen, wechseln Sie zu Ihrem **Bot-Dashboard**, und bearbeiten Sie den Teams-Kanal. Klicken Sie auf die Schaltfläche **Löschen** am unteren Rand der Seite. Dadurch wird verhindert, dass Benutzer Ihren Bot auffinden, hinzufügen und mit ihm interagieren. Dadurch wird der Bot nicht aus den Teams-Instanzen eines anderen Benutzers entfernt, er funktioniert jedoch auch nicht mehr für ihn.

## <a name="see-also"></a>Siehe auch

* [Bot mit Inspektions-Middleware debuggen](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Anruf- und Besprechungsbot lokal debuggen](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
