---
title: Testen und debuggen Sie Ihren Bot lokal
author: surbhigupta
description: Erfahren Sie mehr über das lokale Testen und Debuggen Ihres Bots mit einer IDE innerhalb Teams Umgebung über Querladen, außerhalb Teams mithilfe des Bot-Emulators und durch direktes Gespräch mit Ihrem Bot.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: d9ddbb3aa4f93b8981fbba03d879a77f4175e81e
ms.sourcegitcommit: 4892d8d0fa38a472edab047754ef85b1a85be495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2021
ms.locfileid: "61608461"
---
# <a name="test-and-debug-your-bot-locally"></a>Testen und debuggen Sie Ihren Bot lokal

Beim Testen Ihres Bots müssen Sie sowohl die Kontexte berücksichtigen, in denen Ihr Bot ausgeführt werden soll, als auch alle Funktionen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben, die datenspezifische Microsoft Teams erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen Des Bots auswählen, mit seiner Funktionalität übereinstimmt.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Teams

Die umfassendste Möglichkeit, Ihren Bot zu testen, besteht darin, ein App-Paket zu erstellen und in Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die Ihrem Bot in allen Bereichen zur Verfügung steht.

Es gibt zwei Methoden zum Hochladen Ihrer App:

* Verwenden Sie [App Studio.](~/concepts/build-and-test/app-studio-overview.md)
* [Erstellen Sie manuell ein App-Paket,](~/concepts/build-and-test/apps-package.md) und [laden Sie ihre App](~/concepts/deploy-and-publish/apps-upload.md)hoch.

> [!NOTE]
> Um das Manifest zu ändern und Ihre App erneut hochzuladen, [löschen Sie den Bot,](#delete-a-bot-from-teams) bevor Sie das geänderte App-Paket hochladen.
> Um den Bot zu testen, aktivieren Sie das Querladen in Teams. Siehe [Aktivieren des Querladens.](/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

## <a name="debug-your-bot-locally"></a>Lokal Debuggen des Bots

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Fügen Sie nach dem Herunterladen und Installieren von ngrok `ngrok` Ihren Pfad hinzu, und führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten:

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den https-Endpunkt, der von ngrok in Ihrem App-Manifest bereitgestellt wird.

> [!NOTE]
> Wenn Sie das Befehlsfenster schließen und neu starten, wird eine neue URL generiert, und Sie müssen die Bot-Endpunktadresse aktualisieren, um sie zu verwenden.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testen Sie Ihren Bot, ohne es in Teams hochzuladen

Gelegentlich kann es erforderlich sein, Ihren Bot zu testen, ohne ihn als App in Teams zu installieren. Wir stellen zwei Methoden zum Testen des Bots bereit. Das Testen Ihres Bots, ohne ihn als App zu installieren, kann hilfreich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die gesamte Breite der Microsoft Teams Funktionen testen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, sehen Sie sich [die Tests durch Hochladen an.](#test-by-uploading-to-teams)

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulator

Die Bot Framework Emulator ist eine Desktopanwendung, mit der Botentwickler ihre Bots lokal oder remote testen und debuggen können. Der Emulator hilft Ihnen, mit Ihrem Bot zu chatten und die Nachrichten zu überprüfen, die Ihr Bot sendet und empfängt. Dies kann nützlich sein, um zu überprüfen, ob Ihr Bot verfügbar ist, und um zu antworten. Mit dem Emulator können Sie jedoch keine Teams-spezifischen Funktionen testen, die Sie dem Bot hinzugefügt haben, noch die Antworten Ihres Bots stellen eine genaue visuelle Darstellung ihrer Darstellung in Teams dar. Wenn Sie eines dieser Dinge testen müssen, ist es am [besten, Ihren Bot hochzuladen.](#test-by-uploading-to-teams)

Weitere Informationen finden Sie in [den vollständigen Anweisungen zum Bot Framework Emulator.](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true)

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie mit Ihrem Bot direkt nach ID

> [!Important]
> Das Gespräch mit Ihrem Bot nach ID ist nur für grundlegende Testzwecke vorgesehen. Alle Teams-spezifischen Funktionen, die Sie Ihrem Bot hinzugefügt haben, funktionieren nicht.

Sie können auch eine Unterhaltung mit Ihrem Bot mithilfe seiner ID initiieren. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können keine anderen Microsoft Teams App-Funktionen wie Registerkarten oder Messaging-Erweiterungen nutzen. Sie können eine Unterhaltung auf eine der folgenden Arten initiieren:

* Wählen Sie auf der [Seite "Bot-Dashboard"](https://dev.botframework.com/bots) für Ihren Bot unter **"Kanäle"** die Option **"Zu Microsoft Teams hinzufügen"** aus. Microsoft Teams startet einen persönlichen Chat mit Ihrem Bot.

* Verweisen Sie direkt in Microsoft Teams auf die App-ID Ihres Bots:
   1. Kopieren Sie auf der [Seite "Bot-Dashboard"](https://dev.botframework.com/bots) für Ihren Bot unter **"Details"** die **Microsoft-App-ID** für Ihren Bot.
  
      ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   2. Öffnen Sie Microsoft Teams, und wählen Sie im **Chatbereich** das **Symbol "Chat hinzufügen"** aus. Fügen Sie in **"An:"** die Microsoft App-ID Ihres Bots ein.
  
      ![Hochladen von Bots](~/assets/images/bots_uploading.png)

      Die App-ID muss in Ihren Botnamen aufgelöst werden.

   3. Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
      Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnisseite zur Registerkarte **"Kontakte",** um Ihren Bot anzuzeigen und mit ihm zu chatten.

> [!Note]
> Wenn Microsoft Teams auf die App-ID Ihres Bots verweisen möchten, aktivieren Sie [das Querladen von Apps.](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)      

Ihr Bot empfängt das `conversationUpdate` Ereignis, wenn Sie die Bots zu einem Team hinzufügen, ohne die Teaminformationen im `channelData` Objekt.

## <a name="block-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Benutzer können festlegen, dass Ihr Bot keine persönlichen Chatnachrichten senden kann. Sie können dies umschalten, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und **bot-Unterhaltung blockieren** auswählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer die Nachrichten jedoch nicht empfängt.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in der Ansicht ihres Teams auswählen. Dadurch wird der Bot nur aus der Verwendung dieses Teams entfernt, einzelne Benutzer können weiterhin im persönlichen Kontext interagieren. Bots im persönlichen Kontext können von Benutzern nicht deaktiviert oder entfernt werden.

## <a name="disable-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem **Bot-Dashboard,** und bearbeiten Sie den Microsoft Teams Kanal. Deaktivieren Sie die Option **"Bei Microsoft Teams aktivieren".** Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, er ist jedoch weiterhin auffindbar, und Benutzer können ihn weiterhin Teams hinzufügen.

## <a name="delete-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams zu entfernen, wechseln Sie zu Ihrem **Bot-Dashboard,** und bearbeiten Sie den Microsoft Teams Kanal. Klicken Sie unten auf die Schaltfläche **"Löschen".** Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen und mit diesem interagieren. Dadurch wird der Bot nicht aus den Teams Instanzen anderer Benutzer entfernt, er funktioniert jedoch auch für ihn nicht mehr.

## <a name="see-also"></a>Siehe auch

* [Bot mit Inspektions-Middleware debuggen](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Anruf- und Besprechungsbot lokal debuggen](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
