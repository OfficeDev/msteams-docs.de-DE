---
title: Erste Schritte – Erstellen eines Bots
author: girliemac
description: Erstellen Sie schnell Microsoft Teams bot mithilfe des Microsoft Teams Toolkits.
ms.author: timura
ms.date: 04/14/2020
ms.topic: tutorial
ms.openlocfilehash: d54766d739ceaf585ab4a1e026f4a6e1150e3a2e
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630978"
---
# <a name="create-your-first-bot-for-teams"></a>Erstellen Des ersten Bots für Teams

In diesem Lernprogramm lernen Sie, eine einfache Bot-App zu erstellen. Ein Bot fungiert als Vermittler zwischen Teams und Ihrer Web-App oder Ihrem Dienst mit einer Unterhaltungsschnittstelle. Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.

## <a name="what-youll-learn"></a>Was Sie lernen werden

* Erstellen Sie ein App-Projekt und einen Bot mit dem Microsoft Teams Toolkit für Visual Studio Code.
* Verstehen der Teams für Bots relevanten App-Konfigurationen.
* Hosten und ausführen Sie eine App lokal mit einer localhost-Tunnellösung.
* Querladen und Testen eines Bots in Teams.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache App Teams erstellen. Weitere Informationen finden Sie unter [Create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md). 

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre App: 

* **App-Konfigurationen und Gerüste, die** für Bots relevant sind.
* **Bot,** der automatisch beim Microsoft Azure registriert wird.

**So erstellen Sie Ihr App-Projekt**

1. Wählen Visual Studio Code sie **Microsoft Teams** auf der linken Aktivitätsleiste aus, und wählen Sie Erstellen einer :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: neuen Teams App **aus.**

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-01.png" alt-text="Screenshot des Erstellens einer App im Teams Toolkit.":::

1. Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365 an. 
1. Wählen Sie auf dem Bildschirm Projekt auswählen die Option Unterhaltungsbots aus: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-02.png" alt-text="Screenshot, der zeigt, wie Sie einen neuen Bot im Teams erstellen.":::

1. Geben Sie **auf dem Bildschirm** Projekt konfigurieren einen Namen für Ihren Bot ein. Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.
1. Wählen **Sie Create a new Bot** Create Bot  >  **Registration** aus, wie in der folgenden Abbildung dargestellt:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-03.png" alt-text="Screenshot mit der Benennung eines neuen Bots im Teams Toolkit.":::

    Wenn der neue Bot erfolgreich ist, hat er den **Status "Registriert".** Jetzt wird Ihr Bot automatisch beim Microsoft Azure registriert. 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-04.png" alt-text="Screenshot mit der Registrierung eines neuen Bots im Teams Toolkit.":::

1. Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, und speichern Sie Ihr Projekt auf Ihrem Computer.  

## <a name="2-understand-your-app-project-components"></a>2. Verstehen Ihrer App-Projektkomponenten

Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen eines Bots an:

:::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-05.png" alt-text="Screenshot eines Projektgerüsts im Teams Toolkit.":::

Wenn Sie in einem anderen Lernprogramm eine Registerkarte erstellt haben, ist das App-Gerüst für den Bot anders. Im Gegensatz zu Registerkarten erfordert die Botentwicklung nicht, dass Sie Front-End-Webkomponenten erstellen oder das Teams JavaScript-Client-SDK verwenden.  Stattdessen verwendet das Gerüst das [Microsoft Bot Framework](https://dev.botframework.com/), das ein Open-Source-SDK zum Erstellen intelligenter Bots auf Enterprise-Qualität ist, die im Web, mobil und natürlich Teams! 

Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Teams-spezifischen Handler zur Behandlung von Botaktivitäten, z. B. wie der Bot auf bestimmte Nachrichten `botActivityHandler.js` reagiert.

## <a name="3-securely-expose-your-localhost-to-the-internet"></a>3. Stellen Sie Ihren localhost sicher für das Internet zur Verfügung

Werfen Sie einen Blick auf die Datei, die einen HTTP-Server erstellt und routing behandelt, um eingehende `index.js` Anforderungen an Ihren Bot zu lauschen. Die `/api/messages` ist die Endpunkt-URL Ihrer App, um auf Clientanforderungen zu reagieren: 

```JavaScript
server.post('/api/messages', (req, res) => { 
  adapter.processActivity(req, res, async (context) => { 
    await botActivityHandler.run(context); 
  }); 
}); 
```

Um die Anforderungen an die Logik Ihres Bots weiter zu weiterleiten, müssen Sie eine öffentlich zugängliche URL einrichten, z. B. `https://example.com/api/messages` , anstatt `https://localhost` . Da Ihre App derzeit von Ihrem localhost ausgeführt wird, müssen Sie *das* Netzwerk tunneln.

Tunneling ist ein Protokoll, mit dem Sie Daten über ein Netzwerk übertragen können. Und mit dem localhost-Tunneling können Sie eine Verbindung zwischen Ihrem lokalen Computer und einer Remoteverbindung herstellen. Um Ihren localhost sicher für das Internet verfügbar zu machen, empfehlen wir Die Verwendung des Drittanbietertools **ngrok**. Dadurch erhalten Sie eine sichere URL. 

1. Wechseln Sie zur [ngrok.com,](https://ngrok.com/download) und befolgen Sie die Anweisungen zum Installieren und Einrichten von ngrok in Ihrer Umgebung. 
    
    Fügen Sie den vollständigen Pfad zur ngrok.exe, die Sie zur Systempfadumgebungsvariablen installiert haben. Die genauen Schritte sind spezifisch für die shell, die Sie verwenden.

1.  Nachdem Sie die Einrichtung abgeschlossen haben, öffnen Sie ein Terminal, und führen Sie `ngrok http -host-header=rewrite 3978` aus. 

    Ngrok stellt Ihnen nun eine öffentliche, sichere URL zur Seite, die an Ihren localhost an Port 3978 weitergeleitet wird. Kopieren Sie daher beispielsweise die HTTPS-URL, wie im folgenden Screenshot gezeigt, da `https://287a4f4223bc.ngrok.io` Teams HTTPS-Verbindungen erfordert: 

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-ngrok-06.png" alt-text="Screenshot des Tunnelns von localhost mit ngrok.":::

1. Registrieren Sie die URL im App-Manifest. 

## <a name="4-register-your-bot-endpoint"></a>4. Registrieren Des Bot-Endpunkts

Um einen Bot in Teams verwenden zu können, müssen Sie ihn beim Azure Bot Service registrieren. Dies erfolgt automatisch, wenn Sie Ihre App mithilfe des Teams einrichten.

Sie müssen weiterhin eine Endpunktadresse angeben, um Benutzernachrichten oder An den Bot gesendete Anforderungen zu empfangen und zu verarbeiten. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies im Toolkit konfigurieren.

1. Öffnen Visual Studio Code in Microsoft Teams **Toolkit**.
1. Wählen **Sie Bots**  >  **Vorhandene Botregistrierungen aus,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben. 
1. Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL ein, z. B. , wo Sie den Bot hosten und `https://287a4f4223bc.ngrok.io` an ihn `/api/messages` anfügen:

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-bots-07.png" alt-text="Screenshot, der zeigt, wie Sie localhost mit ngrok tunneln.":::

    Ihr Bot kann auf Nachrichten in der Teams, nachdem Sie den Endpunkt ordnungsgemäß eingerichtet haben. 

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert. Es ist an der Zeit, Ihre App in Betrieb zu halten.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

   Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Bot aktivitäten bei Ihrer `localhost` abhört:

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Querladen Des Bots in Teams

Wenn Ihr Bot ausgeführt wird, können Sie ihn in einem Teams.

> [!TIP]
> Wenn Sie eine App noch nicht Teams geladen haben und probleme auftreten, führen Sie die folgenden [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)

1. Wählen Visual Studio Code die **F5-Taste** aus, um einen Teams zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen aus.** 

   > [!Note]
   > Standardmäßig wird die App Ihrer 1:1-Chatnachricht hinzugefügt, Sie können sie jedoch in einem Team oder Chat installieren, indem Sie auf den kleinen Pfeil neben Hinzufügen für mich **klicken.** In diesem Lernprogramm klicken wir einfach auf Hinzufügen.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install-08.png" alt-text="Screenshot, der das Tunneln von localhost mit ngrok zeigt.":::

## <a name="7-test-your-bot"></a>7. Testen Des Bots

Sagen wir "Hello" zu Ihrem Bot.

* Senden Sie im Feld Verfassen eine `Hello` Nachricht.
    Ihr Bot antwortet mit einer Nachricht wie der folgenden:

    :::image type="content" source="../assets/images/build-your-first-app/teams-client-bot.png" alt-text="Ein Screenshot, der zeigt, dass ein Benutzer &quot;Hello&quot; zu einem Teams und eine Antwort erhalten.":::

    Sie haben nun einen einfachen Teams erstellt, der mit Benutzern 1:1 oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren 🎉.

## <a name="troubleshoot-your-bot"></a>Problembehandlung für Ihren Bot

Die folgenden Informationen können hilfreich sein, wenn Beim Abschließen dieses Lernprogramms Probleme auftreten.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit der Teams


Wenn Sie Ihre App installiert haben, der Bot jedoch nicht funktioniert, stellen Sie sicher, dass der Bot mit dem Azure [Bot Service-Kanal Teams *ist.*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams. In diesem Fall stellt ein Kanal die Verbindung zwischen Dem Azure Bot Service und Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App bereit.](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="see-also"></a>Sehen Sie ebenfalls

* [Bot-Grundlagen](../bots/bot-basics.md)
* [Erstellen einer persönlichen Registerkarte für Microsoft Teams](../build-your-first-app/build-personal-tab.md)
* [Weitere Informationen zu Teams Bots mit einem unserer Beispiele](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Grundlegende Informationen zu Bot-Unterhaltungen](../bots/how-to/conversations/conversation-basics.md)
* [Richtlinien für den Entwurf](../bots/design/bots.md) 
* [Produktionsbereite Benutzeroberflächenvorlagen](../concepts/design/design-teams-app-ui-templates.md)
* [Botauthentifizierung in Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Erstellen eines Bots ohne Toolkit](../resources/bot-v3/bots-create.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
