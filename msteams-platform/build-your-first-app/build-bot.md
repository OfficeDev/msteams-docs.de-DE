---
title: Erste Schritte – Erstellen eines Bots
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Bot.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 3e07c148e1b03431dc419a4e3679abac0229ff72
ms.sourcegitcommit: e08f309f62db2cf0f505f2aadfe728e5b46c17a5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "50140468"
---
# <a name="build-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

In diesem Lernprogramm  erstellen Sie eine einfache Bot-App. Ein Bot fungiert als Vermittler zwischen Den Benutzern von Teams und Ihrem Webdienst. Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.

## <a name="your-assignment"></a>Ihre Zuordnung

Ihr Arbeitsplatz hat eine Teams-App erstellt, die [Registerkarten](../build-your-first-app/build-personal-tab.md) verwendet, um wichtige Kontaktinformationen verfügbar zu machen. Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks. Aber was passiert, wenn sich Personen über einen Chatbot an den Helpdesk wenden können, anstatt zu anrufen? Ihr Chef bittet Sie, zu sehen, wie schnell Sie einen einfachen Unterhaltungsbot in Teams einrichten können.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und -Bots mithilfe des Microsoft Teams Toolkit for Visual Studio Code
> * Identifizieren einiger der für Bots relevanten App-Konfigurationen und Gerüste
> * Lokales Hosten einer App
> * Konfigurieren eines Bots für Teams
> * Querladen und Testen eines Bots in Teams

## <a name="before-you-begin"></a>Bevor Sie beginnen

Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die Entwicklung von Teams verstehen und [installieren.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre App:

* **Für Bots relevante App-Konfigurationen** und Gerüste
* **Bot,** der automatisch beim Microsoft Azure Bot Service registriert wird

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diesen Anweisungen zu folgen, die Projekte ausführlicher erläutern.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** aus, und wählen :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: Sie **"Neue Teams-App erstellen" aus.**
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem Bildschirm** "Funktionen hinzufügen" **"Bot"** und dann **"Weiter" aus.**
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.)
1. Wechseln Sie zu **"Bot konfigurieren",** und wählen **Sie "Neuen Bot erstellen"** und dann **"Botregistrierung erstellen" aus.** Wenn dies erfolgreich ist, hat Ihr neuer Bot den **Status "Registriert".**
1. Wählen **Sie "Fertig** stellen" am unteren Rand des Bildschirms aus, und wählen Sie einen Speicherort zum Erstellen des Projekts aus.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren relevanter Komponenten des App-Projekts

Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen eines Bots an.

### <a name="app-configurations"></a>App-Konfigurationen

Wenn Sie die Konfigurationen Ihres Bots anzeigen oder aktualisieren möchten, wählen **Sie App Studio** im Toolkit aus, und wechseln Sie zu **Bots.**

### <a name="app-scaffolding"></a>App-Gerüst

Das Gerüst der App stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verarbeitung der Aktivitäten ihres Bots in Teams (z. B. wie der Bot auf bestimmte Nachrichten wie `botActivityHandler.js` "Hello") reagiert.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre App

Zu Testzwecken hosten wir Ihre App auf einem lokalen Webserver (Port 3978).

1. Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal die Ausführung `ngrok http -host-header=rewrite 3978` aus.
1. Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams https-Verbindungen benötigt.

Mit dieser URL kann Teams (für das HTTPS-Verbindungen erforderlich sind) an den Ort tunneln, an dem Sie Ihre App hosten (an `localhost` Port 3978).

## <a name="4-configure-your-bot"></a>4. Konfigurieren Des Bots

Um einen Bot in Teams zu verwenden, müssen Sie ihn beim Azure Bot Service registrieren. Dies erfolgt automatisch, wenn Sie Ihre App mit dem Teams Toolkit einrichten.

Sie müssen dennoch eine Endpunktadresse angeben, um Benutzernachrichten (d. h. Anforderungen) zu empfangen und zu verarbeiten, die an den Bot gesendet werden. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies im Toolkit schnell konfigurieren.

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Open Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie **im Feld für die** Adresse des Botendpunkts die ngrok-URL ein (z. B. ), in der Sie den Bot hosten, und fügen Sie ihn `https://468b9ab725e9.ngrok.io` `/api/messages` an.<br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Illustration showing where you can configure the bot endpoint URL in the Teams Toolkit.":::

Ihr Bot kann auf Nachrichten in Teams reagieren.

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert. Es ist an der Zeit, Ihre App zu starten und zu starten.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.
1. Führen Sie `npm start` .

Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Bot auf Aktivitäten bei Ihnen `localhost` lauscht:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Querladen Ihres Bots in Teams

Wenn Ihr Bot ausgeführt wird, können Sie ihn in Teams installieren.

> [!TIP]
> Wenn Sie zuvor noch keine Teams-App sideloaded haben und Probleme auftreten, führen Sie die folgenden [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)

1. Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.
1. Wählen Sie im Dialogfeld "App-Installation" die Option **"Für mich hinzufügen" aus.** (Sie können den Bot einem Kanal oder Chat hinzufügen, aber es ist weniger aufdringlich für andere, einen Bot in einem 1:1-Chat zu testen.)

## <a name="7-test-your-bot"></a>7. Testen Des Bots

Jetzt zum spaßig-Teil: Lassen Sie uns "Hello" zu Ihrem Bot sagen.

1. Senden Sie im Feld zum Verfassen eine `Hello` Nachricht.

Ihr Bot antwortet mit einer Nachricht wie der folgenden.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot, der zeigt, dass ein Benutzer &quot;Hello&quot; zu einem Teams-Bot sagt und eine Antwort erhalten.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über einen einfachen Teams-Bot, der mit Benutzern 1:1 oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn beim Abschließen dieses Lernprogramms Probleme auftreten.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Teams verbunden

Wenn Sie Ihre App installiert haben, der Bot aber nicht funktioniert, stellen Sie sicher, dass der Bot mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist. In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Weitere Informationen

* [Sehen Sie sich an, was Teams Bots sonst noch mit einem unserer Beispiele tun können.](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Grundlegende Informationen zu Bot-Unterhaltungen](../bots/how-to/conversations/conversation-basics.md)
* Folgen Sie [unseren Entwurfsrichtlinien,](../bots/design/bots.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.
* [Botauthentifizierung in Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Erstellen eines Bots ohne das Toolkit](../resources/bot-v3/bots-create.md)
