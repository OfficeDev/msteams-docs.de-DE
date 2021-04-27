---
title: Erste Schritte – Erstellen eines Bots
author: heath-hamilton
description: Erstellen Sie schnell einen Microsoft Teams-Bot mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 5dfbfa05d2f1e36bbc14bd929cb2592303081522
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020000"
---
# <a name="build-a-bot-for-microsoft-teams"></a>Erstellen eines Bots für Microsoft Teams

In diesem Lernprogramm  erstellen Sie eine einfache Bot-App. Ein Bot fungiert als Vermittler zwischen Teams-Benutzern und Ihrem Webdienst. Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.

## <a name="your-assignment"></a>Ihre Zuordnung

Ihr Arbeitsplatz hat eine Teams-App erstellt, die [Registerkarten zum](../build-your-first-app/build-personal-tab.md) Anzeigen wichtiger Kontaktinformationen verwendet. Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks. Doch was wäre, wenn sich die Personen über einen Chatbot an den Helpdesk wenden könnten, anstatt zu anrufen? Ihr Vorgesetzter bittet Sie, zu sehen, wie schnell Sie einen einfachen Unterhaltungsbot in Teams einrichten und ausführen können.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und eines Bots mithilfe des Microsoft Teams Toolkits für Visual Studio Code
> * Identifizieren einiger der für Bots relevanten App-Konfigurationen und Gerüste
> * Lokal hosten einer App
> * Konfigurieren eines Bots für Teams
> * Querladen und Testen eines Bots in Teams

## <a name="before-you-begin"></a>Bevor Sie beginnen

Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die [Teams-Entwicklung verstehen und installieren.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre App:

* **Für Bots relevante** App-Konfigurationen und Gerüste
* **Bot,** der automatisch beim Microsoft Azure Bot Service registriert ist

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, die Projekte ausführlicher erläutern.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem** Bildschirm Funktionen hinzufügen die Option **Bot** und dann **Weiter aus.**
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Wechseln Sie **zu Bot konfigurieren,** und wählen **Sie Erstellen eines neuen Bots** und **dann Botregistrierung erstellen aus.** Wenn der neue Bot erfolgreich ist, hat er den **Status "Registriert".**
1. Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, und wählen Sie einen Speicherort aus, an dem Sie Ihr Projekt erstellen möchten.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren relevanter App-Projektkomponenten

Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen eines Bots an.

### <a name="app-configurations"></a>App-Konfigurationen

Wenn Sie die Konfigurationen Ihres Bots anzeigen oder aktualisieren möchten, wählen Sie im Toolkit **App Studio aus,** und wechseln Sie zu **Bots**.

### <a name="app-scaffolding"></a>App-Gerüst

Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verarbeitung der Aktivitäten ihres Bots in Teams (z. B. wie der Bot auf bestimmte Nachrichten wie `botActivityHandler.js` "Hello") reagiert.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre App

Zu Testzwecken hosten wir Ihre App auf einem lokalen Webserver (Port 3978).

1. Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` aus.
1. Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams HTTPS-Verbindungen erfordert.

Mit dieser URL kann Teams (für die HTTPS-Verbindungen erforderlich sind) zu dem Ort tunneln, an dem Sie Ihre App hosten ( `localhost` an Port 3978).

## <a name="4-configure-your-bot"></a>4. Konfigurieren des Bots

Um einen Bot in Teams zu verwenden, müssen Sie ihn beim Azure Bot Service registrieren. Zum Glück geschieht dies automatisch, wenn Sie Ihre App mithilfe des Teams Toolkits einrichten.

Sie müssen weiterhin eine Endpunktadresse angeben, um Benutzernachrichten (d. h. Anforderungen) zu empfangen und zu verarbeiten, die an den Bot gesendet werden. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies schnell im Toolkit konfigurieren.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Microsoft Teams Toolkit **öffnen aus.**
1. Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL (z. B. ) ein, in der Sie den Bot hosten, und `https://468b9ab725e9.ngrok.io` fügen Sie ihn `/api/messages` an.<br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Abbildung, in der Sie die URL des Botendpunkts im Teams Toolkit konfigurieren können.":::

Ihr Bot kann auf Nachrichten in Teams reagieren.

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihres Bots eingerichtet und für die Verarbeitung von Nachrichten konfiguriert. Es ist an der Zeit, Ihre App in Betrieb zu halten.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Bot aktivitäten bei Ihrer `localhost` abhört:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. Querladen Des Bots in Teams

Wenn Ihr Bot ausgeführt wird, können Sie ihn in Teams installieren.

> [!TIP]
> Wenn Sie eine Teams-App noch nicht nebeneinander geladen haben und Probleme auftreten, führen Sie diese [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)

1. Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen aus.** (Sie könnten den Bot zu einem Kanal oder Chat hinzufügen, aber es ist für andere weniger aufdringlich, einen Bot in einem 1:1-Chat zu testen.)

## <a name="7-test-your-bot"></a>7. Testen Des Bots

Jetzt für den lustigen Teil: Sagen wir "Hello" zu Ihrem Bot.

1. Senden Sie im Feld Verfassen eine `Hello` Nachricht.

Ihr Bot antwortet mit einer Nachricht wie der folgenden.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot, auf dem ein Benutzer &quot;Hello&quot; zu einem Teams-Bot sagt und eine Antwort erhalten.":::

## <a name="well-done"></a>Gut gemacht

Glückwunsch! Sie verfügen über einen einfachen Teams-Bot, der mit Benutzern 1:1 oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn Beim Abschließen dieses Lernprogramms Probleme auftreten.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Teams verbunden

Wenn Sie Ihre App installiert haben, der Bot jedoch nicht funktioniert, stellen Sie sicher, dass der Bot mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist. In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Weitere Informationen

* [Sehen Sie sich an, welche anderen Teams Bots mit einem unserer Beispiele arbeiten können](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Grundlegende Informationen zu Bot-Unterhaltungen](../bots/how-to/conversations/conversation-basics.md)
* Befolgen Sie [unsere Entwurfsrichtlinien,](../bots/design/bots.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.
* [Bot-Authentifizierung in Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
* [Erstellen eines Bots ohne Toolkit](../resources/bot-v3/bots-create.md)
