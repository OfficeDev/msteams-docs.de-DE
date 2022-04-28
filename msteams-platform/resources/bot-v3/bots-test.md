---
title: Testen und Debuggen Ihres Bots
description: Beschreibt das Testen von Bots in Microsoft Teams
keywords: Teams-Bots-Tests
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/20/2019
ms.openlocfilehash: df403343aab60ebd802b4da0e871649ded8b8a7e
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103432"
---
# <a name="test-and-debug-your-microsoft-teams-bot"></a>Testen und Debuggen Ihres Microsoft Teams Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Beim Testen Ihres Bots müssen Sie sowohl den Kontext(en) berücksichtigen, in dem Der Bot ausgeführt werden soll, als auch alle Funktionen, die Sie möglicherweise zu Ihrem Bot hinzugefügt haben, die datenspezifisch für Microsoft Teams erfordern. Stellen Sie sicher, dass die Methode, die Sie zum Testen Ihres Bots ausgewählt haben, mit ihrer Funktionalität übereinstimmt.

## <a name="test-by-uploading-to-teams"></a>Testen durch Hochladen in Teams

Die umfassendste Methode zum Testen Ihres Bots besteht darin, ein App-Paket zu erstellen und in Teams hochzuladen. Dies ist die einzige Methode zum Testen der vollständigen Funktionalität, die Für Ihren Bot in allen Bereichen verfügbar ist.

Es gibt zwei Methoden zum Hochladen Ihrer App. Sie können entweder [App Studio](~/concepts/build-and-test/app-studio-overview.md) verwenden oder [manuell ein App-Paket erstellen](~/concepts/build-and-test/apps-package.md) und [Ihre App hochladen](~/concepts/deploy-and-publish/apps-upload.md). Wenn Sie Ihr Manifest ändern und Ihre App erneut hochladen müssen, sollten Sie [Ihren Bot löschen](#deleting-a-bot-from-teams) , bevor Sie das geänderte App-Paket hochladen.

## <a name="debug-your-bot-locally"></a>Debuggen Des Bots lokal

Wenn Sie Ihren Bot während der Entwicklung lokal hosten, müssen Sie einen Tunneldienst wie [ngrok](https://ngrok.com/) verwenden, um Ihren Bot zu testen. Nachdem Sie ngrok heruntergeladen und installiert haben, führen Sie den folgenden Befehl aus, um den Tunneldienst zu starten. Möglicherweise müssen Sie ngrok zu Ihrem Pfad hinzufügen.

```bash
ngrok http <port> -host-header=localhost:<port>
```

Verwenden Sie den von ngrok bereitgestellten HTTPS-Endpunkt in Ihrem App-Manifest. Wenn Sie Ihr Befehlsfenster schließen und neu starten, erhalten Sie eine neue URL und müssen Ihre Bot-Endpunktadresse aktualisieren, um auch diese zu verwenden.

## <a name="testing-your-bot-without-uploading-to-teams"></a>Testen Ihres Bots ohne Hochladen in Teams

Gelegentlich ist es erforderlich, Ihren Bot zu testen, ohne ihn als App in Teams zu installieren. Wir stellen zwei Methoden zum Testen bereit. Das Testen Ihres Bots, ohne ihn als App zu installieren, kann nützlich sein, um sicherzustellen, dass Ihr Bot verfügbar ist und reagiert. Sie können jedoch nicht die vollständige Breite Microsoft Teams Funktionen testen, die Sie Möglicherweise zu Ihrem Bot hinzugefügt haben. Wenn Sie Ihren Bot vollständig testen müssen, folgen Sie den Anweisungen zum [Testen durch Hochladen](#test-by-uploading-to-teams).

### <a name="use-the-bot-emulator"></a>Verwenden des Bot-Emulator

Die Bot Framework Emulator ist eine Desktopanwendung, mit der Bot-Entwickler ihre Bots entweder lokal oder remote testen und debuggen können. Mithilfe des Emulators können Sie mit Ihrem Bot chatten und die Nachrichten überprüfen, die Ihr Bot sendet und empfängt. Dies kann nützlich sein, um zu überprüfen, ob Ihr Bot verfügbar ist und reagiert. Der Emulator ermöglicht es Ihnen jedoch nicht, Teams-spezifische Funktionalität zu testen, die Sie Ihrem Bot hinzugefügt haben, und Antworten von Ihrem Bot stellen auch keine genaue visuelle Darstellung dar, wie sie in Teams gerendert werden. Wenn Sie eines dieser Dinge testen müssen, ist es nicht am besten, [Ihren Bot hochzuladen](#test-by-uploading-to-teams).

Vollständige Anweisungen zum Bot Framework Emulator finden Sie [hier](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0&preserve-view=true).

### <a name="talk-to-your-bot-directly-by-id"></a>Sprechen Sie mit Ihrem Bot direkt über die ID

>[!Important]
>Das Sprechen mit Ihrem Bot per ID ist nur zu Testzwecken vorgesehen.

Sie können auch eine Unterhaltung mit Ihrem Bot mithilfe seiner ID initiieren. Hierfür sind im Folgenden zwei Methoden angegeben. Wenn ein Bot über eine dieser Methoden hinzugefügt wurde, kann er in Kanalunterhaltungen nicht adressierbar sein, und Sie können andere Microsoft Teams App-Funktionen wie Registerkarten oder Nachrichtenerweiterungen nicht nutzen.

1. Wählen Sie auf der Seite "[Bot-Dashboard](https://dev.botframework.com/bots)" für Ihren Bot unter **"Kanäle****" die Option "Zu Microsoft Teams hinzufügen"** aus. Microsoft Teams wird mit einem persönlichen Chat mit Ihrem Bot gestartet.
2. Verweisen Sie direkt in Microsoft Teams auf die App-ID Ihres Bots:
   * Kopieren Sie auf der Seite " [Bot-Dashboard](https://dev.botframework.com/bots) " für Ihren Bot unter **"Details**" die **Microsoft App-ID** für Ihren Bot.
  
     ![Abrufen der AppID für den Bot](~/assets/images/bots_appid_botframework.png)
  
   * Wählen Sie in Microsoft Teams im **Chatbereich** das Symbol "**Chat hinzufügen**" aus. Fügen Sie für **"An:**" die Microsoft App-ID Ihres Bots ein.
  
     ![Hochladen der AppID für den Bot](~/assets/images/bots_uploading.png)

     Die App-ID sollte in Ihren Botnamen aufgelöst werden.

   * Wählen Sie Ihren Bot aus, und senden Sie eine Nachricht, um eine Unterhaltung zu initiieren.
   * Alternativ können Sie die App-ID Ihres Bots in das Suchfeld oben links in Microsoft Teams einfügen. Navigieren Sie auf der Suchergebnisseite zur Registerkarte "Personen", um Ihren Bot anzuzeigen und damit zu chatten.

Ihr Bot empfängt das `conversationUpdate` Ereignis genau wie Bots, die einem Team hinzugefügt wurden, jedoch ohne die Teaminformationen im `channelData` Objekt.

## <a name="blocking-a-bot-in-personal-chat"></a>Blockieren eines Bots im persönlichen Chat

Beachten Sie, dass Benutzer ihren Bot am Senden persönlicher Chatnachrichten hindern können. Sie können dies umschalten, indem sie im Chatkanal mit der rechten Maustaste auf Ihren Bot klicken und " **Bot-Unterhaltung blockieren"** auswählen. Dies bedeutet, dass Ihre Bots weiterhin Nachrichten senden, der Benutzer diese Nachrichten jedoch nicht empfängt.

![Blockieren eines Bots](~/assets/images/bots/botdisable.png)

## <a name="removing-a-bot-from-a-team"></a>Entfernen eines Bots aus einem Team

Benutzer können den Bot löschen, indem sie das Papierkorbsymbol in der Bots-Liste in ihrer Teams-Ansicht auswählen. Beachten Sie, dass dadurch nur der Bot aus der Nutzung dieses Teams entfernt wird, einzelne Benutzer können im persönlichen Kontext interagieren.

Bots im persönlichen Kontext können nicht von einem Benutzer deaktiviert oder entfernt werden, ohne den Bot vollständig aus Teams zu entfernen.

## <a name="disabling-a-bot-in-teams"></a>Deaktivieren eines Bots in Teams

Um zu verhindern, dass Ihr Bot Nachrichten empfängt, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams Kanal. Deaktivieren Sie die Option **"Bei Microsoft Teams aktivieren**". Dadurch wird verhindert, dass Benutzer mit dem Bot interagieren, aber er ist weiterhin auffindbar, und Benutzer können ihn teams hinzufügen.

## <a name="deleting-a-bot-from-teams"></a>Löschen eines Bots aus Teams

Um Ihren Bot vollständig aus Teams zu entfernen, wechseln Sie zu Ihrem Bot-Dashboard, und bearbeiten Sie den Microsoft Teams Kanal. Wählen Sie unten die Schaltfläche " **Löschen** " aus. Dadurch wird verhindert, dass Benutzer Ihren Bot entdecken, hinzufügen oder mit ihnen interagieren. Beachten Sie, dass dadurch der Bot nicht aus den Teams Instanzen anderer Benutzer entfernt wird, obwohl er auch für sie nicht mehr funktioniert.

## <a name="removing-your-bot-from-appsource"></a>Entfernen Ihres Bots aus AppSource

Wenn Sie Ihren Bot aus Ihrer Teams-App in AppSource (zuvor Office Store) entfernen möchten, müssen Sie den Bot aus Ihrem App-Manifest entfernen und die App erneut zur Überprüfung übermitteln. Weitere Informationen finden Sie unter [Veröffentlichen Ihrer Microsoft Teams-App in AppSource](~/concepts/deploy-and-publish/apps-publish.md).
