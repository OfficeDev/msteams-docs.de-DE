---
title: Erste Schritte - Erstellen Eines Bots
author: girliemac
description: Erstellen Sie schnell einen Microsoft Teams-Bot mit dem Microsoft Teams Toolkit.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: 2cbd90b293e8ac8343febc7b3d23278d5bb5bf82
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565886"
---
# <a name="create-your-first-bot-for-teams"></a>Erstellen Sie Ihren ersten Bot für Teams

Dieses Tutorial lehrt Sie, eine grundlegende Bot-App zu erstellen. Ein Bot fungiert als Vermittler zwischen Teams Benutzern und Ihrer Web-App oder Ihrem Dienst mit einer Konversationsschnittstelle. Personen können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.

## <a name="what-youll-learn"></a>Was Sie lernen werden

* Erstellen Sie ein App-Projekt und einen Bot mit dem Microsoft Teams Toolkit für Visual Studio Code.
* Verstehen Sie die Teams App-Konfigurationen, die für Bots relevant sind.
* Hosten und führen Sie eine App lokal mit einer lokalen Host-Tunnellösung aus.
* Sideload und testen Sie einen Bot in Teams.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen. Weitere Informationen finden Sie [unter Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App](../build-your-first-app/build-and-run.md). 

## <a name="1-create-your-app-project"></a>1. Erstellen Sie Ihr App-Projekt

Mit dem Microsoft Teams Toolkit können Sie die folgenden Komponenten für Ihre App einrichten: 

* **App-Konfigurationen und Gerüste** relevant für Bots.
* **Bot,** der automatisch beim Microsoft Azure Bot Service registriert ist.

**So erstellen Sie Ihr App-Projekt**

1. Wählen Sie in Visual Studio Code **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus, und wählen Sie **eine neue Teams-App erstellen** aus.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Screenshot, der zeigt, wie sie eine App im Teams Toolkit erstellen.":::

1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an. 
1. Wählen Sie auf dem Bildschirm Projekt auswählen Unterhaltung-Bots aus: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Screenshot, der zeigt, wie Sie einen neuen Bot im Teams Toolkit erstellen.":::

1. Geben Sie auf dem **Bildschirm Projekt konfigurieren** einen Namen für Ihren Bot ein. Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.
1. Wählen Sie **Erstellen einer neuen**  >  **Bot-Registrierung erstellen** aus, wie in der folgenden Abbildung gezeigt:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Screenshot mit dem Benennen eines neuen Bots im Teams Toolkit.":::

    Wenn der Erfolg gelingt, hat Ihr neuer Bot einen **registrierten** Status. Jetzt wird Ihr Bot automatisch beim Microsoft Azure-Bot-Service registriert. 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Screenshot mit der Registrierung eines neuen Bots im Teams Toolkit.":::

1. Wählen Sie am unteren Bildschirmrand **fertig** und speichern Sie Das Projekt auf dem Computer.  

## <a name="2-understand-your-app-project-components"></a>2. Verstehen Ihrer App-Projektkomponenten

Ein Großteil der App-Konfigurationen und Gerüste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen. Sehen wir uns die Hauptkomponenten für den Aufbau eines Bots an:

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Screenshot mit einem Projektgerüst im Teams Toolkit.":::

Wenn Sie eine Registerkarte in einem anderen Tutorial erstellt haben, ist das App-Gerüst für den Bot anders. Im Gegensatz zu Registerkarten erfordert die Bot-Entwicklung keine Front-End-Webkomponenten oder die Verwendung des Teams JavaScript-Client-SDK.  Stattdessen verwendet das Gerüst die [Microsoft Bot Framework](https://dev.botframework.com/), die ein Open-Source-SDK für den Aufbau intelligenter Bots auf Enterprise-Qualität ist, die im Web, mobil und natürlich Teams funktionieren können! 

Die `botActivityHandler.js` Datei, die sich im Stammverzeichnis Ihres Projekts befindet, ist der Teams-spezifische Handler, der Bot-Aktivitäten verarbeitet, z. B. wie der Bot auf bestimmte Nachrichten reagiert. Das App-Gerüst stellt eine `botActivityHandler.js` Datei im Stammverzeichnis Ihres Projekts bereit, ist die Teams bestimmten Handlers, der Bot-Aktivitäten verarbeitet, z. B. wie der Bot auf bestimmte Nachrichten reagiert.

## <a name="3-securely-expose-your-localhost-to-the-internet"></a>3. Setzen Sie Ihren lokalen Host sicher dem Internet aus

Werfen Sie einen Blick auf die `index.js` Datei, die einen HTTP-Server erstellt und Routing verarbeitet, um eingehende Anforderungen an Ihren Bot zu hören. Die `/api/messages` ist die Endpunkt-URL Ihrer App, um auf Clientanforderungen zu reagieren: 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

Um die Anforderungen an die Logik Ihres Bots weiterzuleiten, müssen Sie eine öffentlich zugängliche URL einrichten, z. `https://example.com/api/messages` B. . `https://localhost` Da Ihre App derzeit von Ihrem lokalen Host aus ausgeführt wird, müssen Sie das Netzwerk *tunneln.*

Tunneling ist ein Protokoll, mit dem Sie Daten über ein Netzwerk transportieren können. Und localhost Tunneling bietet Ihnen eine Verbindung zwischen Ihrem lokalen Computer und einer Remote-Verbindung. Um Ihren lokalen Host sicher dem Internet auszusetzen, empfehlen wir Ihnen, das Drittanbieter-Tool **namens ngrok** zu verwenden. Dadurch erhalten Sie eine sichere URL. 

1. Rufen Sie die [ngrok.com-Website](https://ngrok.com/download) auf, und befolgen Sie die Anweisungen zum Installieren und Einrichten von ngrok in Ihrer Umgebung. 
    
    Fügen Sie den vollständigen Pfad zur ngrok.exe Datei hinzu, die Sie der Systemumgebungsvariablen PATH installiert haben. Die genauen Schritte sind spezifisch für die Shell, die Sie verwenden.

1.  Nachdem Sie die Einrichtung abgeschlossen haben, öffnen Sie ein Terminal, und führen Sie `ngrok http -host-header=rewrite 3978` aus. 

    Jetzt stellt ngrok Ihnen eine öffentliche, sichere URL bereit, die an Ihren lokalen Host an Port 3978 weitergeleitet wird, also kopieren Sie die HTTPS-URL, z. B., `https://287a4f4223bc.ngrok.io` wie im Screenshot unten gezeigt, da Teams HTTPS-Verbindungen erfordert: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Screenshot mit Tunnelbau von localhost mit ngrok.":::

1. Registrieren Sie die URL in Ihrem App-Manifest. 

## <a name="4-register-your-bot-endpoint"></a>4. Registrieren Sie Ihren Bot-Endpunkt

Um einen Bot in Teams verwenden zu können, müssen Sie ihn beim Azure Bot Service registrieren. Dies geschieht automatisch, wenn Sie Ihre App mit dem Teams Toolkit einrichten.

Sie müssen weiterhin eine Endpunktadresse angeben, um Benutzernachrichten oder an den Bot gesendete Anforderungen zu empfangen und zu verarbeiten. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies im Toolkit konfigurieren.

1. Öffnen Sie **Visual Studio Code Microsoft Teams Toolkit**.
1. Wählen Sie **Bots**  >  **Vorhandene Bot-Registrierungen** und wählen Sie den Bot, den Sie während des Setups erstellt haben. 
1. Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL ein, z. B. , in der Sie den Bot hosten und an ihn `https://287a4f4223bc.ngrok.io` `/api/messages` anhängen:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Screenshot, der zeigt, wie localhost mit ngrok getunnelt wird.":::

    Ihr Bot kann auf Nachrichten in Teams antworten, nachdem Sie den Endpunkt richtig eingerichtet haben. 

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert. Es ist an der Zeit, Ihre App in Betrieb zu nehmen.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

   Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr Bot auf Aktivitäten in Ihrem `localhost` feldt:

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Sideload Ihren Bot in Teams

Wenn Ihr Bot läuft, können Sie ihn in Teams installieren.

> [!TIP]
> Wenn Sie noch keine Teams App geladen haben und Probleme auftreten, befolgen Sie diese [Anweisungen](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Wählen Sie Visual Studio Code die **Taste F5** aus, um einen Teams Webclient zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen** aus. 

   > [!Note]
   > Standardmäßig wird die App zu Ihrer 1:1-Direktchatnachricht hinzugefügt, Sie können sie jedoch in einem Team installieren oder chatten, indem Sie auf den kleinen Pfeil neben **Add for me** klicken. In diesem Tutorial klicken wir einfach auf Hinzufügen.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Screenshot mit Tunneling localhost mit ngrok.":::

## <a name="7-test-your-bot"></a>7. Testen Sie Ihren Bot

Sagen wir "Hallo" zu Ihrem Bot.

* Senden Sie im Feld Verfassen eine `Hello` Nachricht.
    Ihr Bot antwortet mit der folgenden Nachricht:

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Ein Screenshot, der einen Benutzer zeigt, der einem Teams Bot &quot;Hallo&quot; sagt und eine Antwort erhält.":::

    Sie haben jetzt eine grundlegende Teams-Bots erstellt, die mit Benutzern eins zu eins oder in Gruppeneinstellungen (Kanäle und Chats) 🎉 kommunizieren können.

## <a name="troubleshoot-your-bot"></a>Beheben Sie Ihren Bot

Die folgenden Informationen können hilfreich sein, wenn Sie Probleme beim Abschließen dieses Tutorials hatten.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Teams verbunden


Wenn Sie Ihre App installiert haben, der Bot jedoch nicht funktioniert, stellen Sie sicher, dass der Bot [mit dem Teams *Kanal* des Azure Bot Service verbunden](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.

Es ist wichtig zu verstehen, dass dies nicht dasselbe ist wie ein Kanal in Teams. In diesem Fall ist ein Kanal, wie der Azure Bot Service Ihren Bot mit Teams oder einer anderen [unterstützten Microsoft- oder Drittanbieter-Kommunikations-App](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.

## <a name="see-also"></a>Siehe auch

* [Bot-Grundlagen](../bots/bot-basics.md)
* [Erstellen einer persönlichen Registerkarte für Microsoft Teams](../build-your-first-app/build-personal-tab.md)
* [Sehen Sie, was Teams Bots noch mit einem unserer Samples tun können](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Grundlegende Informationen zu Bot-Unterhaltungen](../bots/how-to/conversations/conversation-basics.md)
* [Richtlinien für den Entwurf](../bots/design/bots.md) 
* [Produktionsfähige UI-Vorlagen](../concepts/design/design-teams-app-ui-templates.md)
* [Bot-Authentifizierung in Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Erstellen eines Bots ohne Toolkit](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
