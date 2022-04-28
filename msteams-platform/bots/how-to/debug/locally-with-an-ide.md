---
title: Testen und Debuggen Ihres Bots lokal
author: surbhigupta
description: Erfahren Sie, wie Sie Ihren Bot lokal mit einer IDE innerhalb Teams Umgebung durch Querladen, außerhalb von Teams mithilfe des Bot-Emulators testen und debuggen können, indem Sie direkt mit Ihrem Bot sprechen.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: a673f1cd260c9b53de477cdd5084bd521c79bd41
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103986"
---
# <a name="test-and-debug-your-bot-locally"></a>Testen und Debuggen Ihres Bots lokal

Beim Testen Ihres Bots müssen Sie sowohl die Kontexte berücksichtigen, in denen Ihr Bot ausgeführt werden soll, als auch alle Funktionen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben, die datenspezifisch für Microsoft Teams erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen Ihres Bots auswählen, mit ihrer Funktionalität übereinstimmt.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Teams

Die umfassendste Methode zum Testen Ihres Bots besteht darin, ein App-Paket zu erstellen und in Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die Für Ihren Bot in allen Bereichen verfügbar ist.

Es gibt zwei Methoden zum Hochladen Ihrer App:

* Verwenden Sie [App Studio](~/concepts/build-and-test/app-studio-overview.md).
* [Erstellen Sie ein App-Paket](~/concepts/build-and-test/apps-package.md) manuell, und [laden Sie die App](~/concepts/deploy-and-publish/apps-upload.md) hoch.

> [!NOTE]
> Um das Manifest zu ändern und Ihre App erneut hochzuladen, [löschen Sie den Bot](#delete-a-bot-from-teams) , bevor Sie das geänderte App-Paket hochladen.
> Um den Bot zu testen, aktivieren Sie das Querladen in Teams. Siehe [Aktivieren des Querladens](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

## <a name="debug-your-bot-locally"></a>Debuggen Des Bots lokal

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, fügen Sie Ihrem Pfad hinzu `ngrok` , und führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten:

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten HTTPS-Endpunkt in Ihrem App-Manifest.

> [!NOTE]
> Wenn Sie Das Befehlsfenster schließen und neu starten, wird eine neue URL generiert, und Sie müssen Ihre Bot-Endpunktadresse aktualisieren, um sie zu verwenden.

## <a name="test-your-bot-without-uploading-to-teams"></a>Testen Sie Ihren Bot, ohne den Upload in Teams

Gelegentlich kann es erforderlich sein, Ihren Bot zu testen, ohne ihn als App in Teams zu installieren. Wir stellen zwei Methoden zum Testen des Bots bereit. Das Testen Ihres Bots, ohne ihn als App zu installieren, kann nützlich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die vollständige Breite Microsoft Teams Funktionen testen, die Sie Möglicherweise zu Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, sehen Sie sich [die Tests durch Hochladen an](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulator

Die Bot Framework Emulator ist eine Desktopanwendung, mit der Botentwickler ihre Bots lokal oder remote testen und debuggen können. Der Emulator hilft Ihnen, mit Ihrem Bot zu chatten und die Nachrichten zu prüfen, die Ihr Bot sendet und empfängt. Dies kann hilfreich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und darauf reagiert. Der Emulator erlaubt Es Ihnen jedoch nicht, Teams-spezifische Funktionalität zu testen, die Sie dem Bot hinzugefügt haben, oder die Antworten von Ihrem Bot stellen eine genaue visuelle Darstellung dar, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, ist es am besten, [Ihren Bot hochzuladen](#test-by-uploading-to-teams).

Weitere Informationen finden Sie [in den vollständigen Anweisungen auf der Bot Framework Emulator](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie mit Ihrem Bot direkt über die ID

> [!Important]
> Das Sprechen mit Ihrem Bot per ID ist nur für grundlegende Testzwecke vorgesehen. Alle Teams-spezifischen Funktionen, die Sie Ihrem Bot hinzugefügt haben, funktionieren nicht.

Sie können auch eine Unterhaltung mit Ihrem Bot mithilfe seiner ID initiieren. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, ist er in Kanalunterhaltungen nicht adressierbar, und Sie können keine anderen Microsoft Teams App-Funktionen wie Registerkarten oder Nachrichtenerweiterungen nutzen. Sie können eine Unterhaltung auf eine der folgenden Arten initiieren:

* Wählen Sie auf der Seite "[Bot-Dashboard](https://dev.botframework.com/bots)" für Ihren Bot unter **"Kanäle****" die Option "Zu Microsoft Teams hinzufügen"** aus. Microsoft Teams startet einen persönlichen Chat mit Ihrem Bot.

* Verweisen Sie direkt in Microsoft Teams auf die App-ID Ihres Bots:
   1. Kopieren Sie auf der Seite " [Bot-Dashboard](https://dev.botframework.com/bots) " für Ihren Bot unter **"Details**" die **Microsoft App-ID** für Ihren Bot.
  
      ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   2. Öffnen Sie Microsoft Teams, wählen Sie im **Chatbereich** das Symbol "**Chat hinzufügen**" aus. Fügen Sie in **"An:**" die Microsoft App-ID Ihres Bots ein.
  
      ![Hochladen von Bots](~/assets/images/bots_uploading.png)

      Die App-ID muss in Ihren Botnamen aufgelöst werden.

   3. Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
      Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnisseite zur Registerkarte " **Personen** ", um Ihren Bot anzuzeigen und damit zu chatten.

> [!Note]
> Damit Microsoft Teams auf die App-ID Ihres Bots verweisen können, aktivieren Sie [das Querladen von Apps](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

Ihr Bot empfängt das `conversationUpdate` Ereignis, wenn Sie die Bots zu einem Team hinzufügen, ohne die Teaminformationen im `channelData` Objekt.

## <a name="block-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Benutzer können ihren Bot daran hindern, persönliche Chatnachrichten zu senden. Sie können dies umschalten, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und " **Bot-Unterhaltung blockieren"** auswählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer empfängt die Nachrichten jedoch nicht.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="remove-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in der Ansicht ihres Teams auswählen. Dadurch wird nur der Bot aus der Nutzung dieses Teams entfernt, einzelne Benutzer können weiterhin im persönlichen Kontext interagieren. Bots im persönlichen Kontext können von Benutzern nicht deaktiviert oder entfernt werden.

## <a name="disable-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem **Bot-Dashboard**, und bearbeiten Sie den Microsoft Teams Kanal. Deaktivieren Sie die Option **"Bei Microsoft Teams aktivieren**". Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, er ist jedoch weiterhin auffindbar, und Benutzer können ihn weiterhin Teams hinzufügen.

## <a name="delete-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams zu entfernen, wechseln Sie zu Ihrem **Bot-Dashboard**, und bearbeiten Sie den Microsoft Teams Kanal. Wählen Sie unten die Schaltfläche " **Löschen** " aus. Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen und mit ihnen interagieren. Dadurch wird der Bot nicht aus den Teams Instanzen eines anderen Benutzers entfernt, es funktioniert jedoch auch nicht mehr für ihn.

## <a name="see-also"></a>Siehe auch

* [Bot mit Inspektions-Middleware debuggen](/azure/bot-service/bot-service-debug-inspection-middleware)
* [Anruf- und Besprechungsbot lokal debuggen](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
