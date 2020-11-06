---
title: Erste Schritte – Erstellen eines bot
author: heath-hamilton
description: Erstellen Sie schnell einen Microsoft Teams-bot mithilfe des Microsoft Teams-Toolkits.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 1229064ac6b7aab73c50048f0764c6a2353ab54a
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931739"
---
# <a name="build-a-bot-for-microsoft-teams"></a>Erstellen eines bot für Microsoft Teams

In diesem Lernprogramm erstellen Sie eine einfache *bot* -app. Ein bot fungiert als Vermittler zwischen Microsoft Teams-Benutzern und Ihrem Webdienst. Personen können mit einem bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.

## <a name="your-assignment"></a>Ihre Zuordnung

Ihr Arbeitsplatz hat eine Teams-App erstellt, die [Registerkarten](../build-your-first-app/build-personal-tab.md) verwendet, um wichtige Kontaktinformationen zu Surface. Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks. Aber statt aufzurufen, was wäre, wenn Personen mit einem Chatbot Kontakt zum Helpdesk aufnehmen könnten? Ihr Chef bittet Sie, sich anzusehen, wie schnell Sie einen einfachen Unterhaltungs bot in Microsoft Teams in Betrieb nehmen können.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und bot mithilfe des Microsoft Teams-Toolkits für Visual Studio Code
> * Identifizieren der für Bots relevanten App-Konfigurationen und Gerüste
> * Lokal Hosten einer APP
> * Konfigurieren eines bot für Teams
> * Querladen und Testen eines bot in Microsoft Teams

## <a name="before-you-begin"></a>Bevor Sie beginnen

Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Das Microsoft Teams-Toolkit hilft Ihnen, die folgenden Komponenten für Ihre APP einzurichten:

* **App-Konfigurationen und** für Bots relevante Gerüste
* **Bot** , der automatisch beim Microsoft Azure bot-Dienst registriert wird

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **bot** und dann **weiter** aus.
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Wechseln Sie zu **configure bot** , und wählen Sie **Create a New bot** und dann **Create bot Registration** aus. Wenn die Methode erfolgreich verläuft, wird Ihr neuer bot einen **registrierten** Status haben.
1. Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , und wählen Sie einen Speicherort aus, um das Projekt zu erstellen.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren der relevanten App-Projektkomponenten

Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen. Lassen Sie uns die Hauptkomponenten zum Erstellen eines bot betrachten.

### <a name="app-configurations"></a>App-Konfigurationen

Um Ihre bot-Konfigurationen anzuzeigen oder zu aktualisieren, wählen Sie **App Studio** im Toolkit aus, und wechseln Sie zu **Bots**.

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst enthält eine `botActivityHandler.js` Datei, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihr Bot Aktivitäten in Microsoft Teams verarbeitet (beispielsweise, wie der bot auf bestimmte Nachrichten wie "Hello" reagiert).

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre APP

Zu Testzwecken hosten wir Ihre APP auf einem lokalen Webserver (Port 3978).

1. Wenn Sie noch nicht vorhanden sind, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .
1. Kopieren Sie die HTTPS-URL in der Ausgabe (beispielsweise `https://468b9ab725e9.ngrok.io` ), da für Teams HTTPS-Verbindungen erforderlich sind.

Mit dieser URL können Teams (für die HTTPS-Verbindungen erforderlich sind) in der Lage sein, zu dem Ort zu gelangen, an dem Sie Ihre APP hosten ( `localhost` auf Port 3978).

## <a name="4-configure-your-bot"></a>4. Konfigurieren Ihres bot

Um einen bot in Microsoft Teams zu verwenden, müssen Sie ihn bei dem Azure bot-Dienst registrieren. Glücklicherweise wird dies automatisch durchgeführt, wenn Sie Ihre APP mit dem Teams-Toolkit einrichten.

Sie müssen immer noch eine Endpunktadresse angeben, um Benutzer Nachrichten (d. h., Anforderungen) zu empfangen und zu verarbeiten, die an den bot gesendet werden. Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` . Sie können diese schnell im Toolkit konfigurieren.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen** aus.
1. Wechseln Sie zu **Bots > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie im Feld **bot-Endpunktadresse** die ngrok-URL (beispielsweise) ein, in der `https://468b9ab725e9.ngrok.io` Sie den bot hosten und `/api/messages` an ihn anfügen.<br/>
    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Abbildung zeigt, wo Sie die bot-Endpunkt-URL im Teams-Toolkit konfigurieren können.":::

Ihr bot wird in der Lage sein, auf Nachrichten in Microsoft Teams zu antworten.

## <a name="5-build-and-run-your-app"></a>5. erstellen und Ausführen der APP

Sie haben eine URL zum Hosten Ihres bot eingerichtet und für die Verarbeitung von Nachrichten konfiguriert. Es ist an der Zeit, Ihre APP in Betrieb zu nehmen.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Wenn die Aktion erfolgreich verläuft, wird die folgende Meldung angezeigt, die besagt, dass Ihr bot ihre Aktivität überwacht `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. querladen Ihres bot in Microsoft Teams

Wenn Ihr bot läuft, können Sie ihn in Microsoft Teams installieren.

> [!TIP]
> Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)aus.

1. Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **für mich hinzufügen** aus. (Sie können den bot einem Kanal oder Chat hinzufügen, aber er ist für andere nicht störend, um einen bot in einem Einzelchat zu testen.)

## <a name="7-test-your-bot"></a>7. Testen Sie Ihren bot

Nun zum spaßigen Teil: sagen wir "Hallo" zu Ihrem bot.

1. Senden Sie im Feld Verfassen eine `Hello` Nachricht.

Ihr bot antwortet mit so etwas wie der folgenden Nachricht.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot mit einem Benutzer, der &quot;Hello&quot; zu einem Team-bot und einer Antwort ruft.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie haben einen einfachen Teams-bot, der mit Benutzern einzeln oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Microsoft Teams verbunden

Wenn Sie Ihre APP installiert haben, aber der bot nicht funktioniert, stellen Sie sicher, dass der bot [mit dem Microsoft Teams- *Kanal* des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.

Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist. In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.

## <a name="learn-more"></a>Mehr erfahren

* [Sehen Sie sich an, was andere Teams-Bots mit einem unserer Beispiele tun können](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Grundlegende Informationen zu Bot-Unterhaltungen](../bots/how-to/conversations/conversation-basics.md)
* [Bot-Authentifizierung in Microsoft Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft bot-Framework](https://dev.botframework.com/)
* [Erstellen eines bot ohne Toolkit](../bots/how-to/create-a-bot-for-teams.md)
