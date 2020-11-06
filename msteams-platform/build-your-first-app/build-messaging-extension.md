---
title: Erste Schritte – Erstellen einer Messaging Erweiterung
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine Microsoft Teams-Messaging Erweiterung.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 160878d92969d57680e6fa25eb6fc13e82bf2a82
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931750"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Erstellen einer Messaging Erweiterung für Microsoft Teams

Es gibt zwei Typen von Teams-APP- *Messaging-Erweiterungen* : [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md).

In dieser Lektion erstellen Sie einen *Suchbefehl* (auch als *Suchbasierte Messaging Erweiterung* bezeichnet), bei dem es sich um eine Verknüpfung zum Suchen externer Inhalte und deren Freigabe in Microsoft Teams handelt. Benutzer können über das [Feld Verfassen oder Ausführen des Teams](../messaging-extensions/what-are-messaging-extensions.md)auf Suchbefehle zugreifen.

## <a name="your-assignment"></a>Ihre Zuordnung

Das Helpdesk Ihrer Organisation kommuniziert mit Benutzern über Teams, die Tickets befinden sich jedoch in einem separaten System. Dies bedeutet, dass Supportmitarbeiter ständig zwischen apps hin und her wechseln müssen. Sie werden untersuchen, wie Sie diese vielseitige Kontext Umstellung reduzieren können, indem Sie eine einfache suchbasierte Messaging Erweiterung für Teams erstellen.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und eines bot für die Messaging Erweiterung mithilfe des Microsoft Teams-Toolkits für Visual Studio Code
> * Identifizieren der APP-Konfigurationen und einiger der für Messaging-Erweiterungen relevanten Gerüste
> * Lokal Hosten einer APP
> * Konfigurieren des bot für Ihre Messaging Erweiterung
> * Querladen und Testen einer Messaging Erweiterung in Microsoft Teams

## <a name="before-you-begin"></a>Bevor Sie beginnen

Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Das Microsoft Teams-Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre Messaging-Erweiterung:

* Für Messaging-Erweiterungen relevantes **App-Konfigurationen und Gerüste**
* **Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure bot-Dienst registriert wird

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Messaging Erweiterung** und dann dann **weiter** aus.
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Führen Sie auf dem Bildschirm **Messaging-Erweiterung konfigurieren** die folgenden Aktionen aus:
    1. Wählen Sie nur die **Suchbasierte** Option für den Typ der Messaging Erweiterung aus.
    1. Wählen Sie **Create a New bot** aus, und erstellen Sie dann die **bot-Registrierung**. Wenn die Methode erfolgreich verläuft, wird Ihr neuer bot einen **registrierten** Status haben.
    1. Wählen Sie im Moment **Nein** für die Option zum Aufheben der Verknüpfung aus.
1. Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren der relevanten App-Projektkomponenten

Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.

### <a name="app-configurations"></a>App-Konfigurationen

Um die Konfigurationen Ihrer Messaging Erweiterung anzuzeigen oder zu aktualisieren, wählen Sie **App Studio** im Toolkit aus, und wechseln Sie zu **Messaging Erweiterungen**.

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst stellt eine `botActivityHandler.js` Datei bereit, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihre Messaging-Erweiterung (oder technisch gesehen, der [bot der Messaging Erweiterung](#4-configure-the-bot-for-your-messaging-extension)) auf Suchabfragen in Microsoft Teams reagiert.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre APP

Zu Testzwecken hosten wir Ihre Messaging-Erweiterung auf einem lokalen Webserver (Port 3978).

1. Wenn Sie noch nicht vorhanden sind, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .
1. Kopieren Sie die HTTPS-URL in der Ausgabe (beispielsweise `https://468b9ab725e9.ngrok.io` ), da für Teams HTTPS-Verbindungen erforderlich sind.

Mit dieser URL können Teams (für die HTTPS-Verbindungen erforderlich sind) in der Lage sein, zu dem Ort zu gelangen, an dem Sie Ihre APP hosten ( `localhost` auf Port 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Konfigurieren des bot für Ihre Messaging-Erweiterung

Messaging-Erweiterungen beruhen darauf, dass Bots Benutzeranforderungen von Teams an den gehosteten Dienst senden und verarbeiten. Der bot muss mit dem Azure bot-Dienst registriert werden, der beim Einrichten Ihrer APP mit dem Teams-Toolkit ausgeführt wurde.

Sie müssen immer noch eine bot-Endpunkt-URL angeben, um Suchabfragen in Ihrer Messaging-Erweiterung zu empfangen und zu verarbeiten. Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` . Sie können diese schnell im Toolkit konfigurieren.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen** aus.
1. Wechseln Sie zu **Bots > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie im Feld **bot-Endpunktadresse** die ngrok-URL (beispielsweise) ein, in der `https://468b9ab725e9.ngrok.io` Sie den bot hosten und `/api/messages` an ihn anfügen.

Ihr bot ist in der Lage, Abfragen in Ihrer Messaging-Erweiterung zu verarbeiten.

## <a name="5-build-and-run-your-app"></a>5. erstellen und Ausführen der APP

Sie haben eine URL eingerichtet, die Ihre Messaging-Erweiterung hostet und für die Verarbeitung von Suchvorgängen konfiguriert ist. Es ist an der Zeit, Ihre APP in Betrieb zu nehmen.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Wenn die Funktion erfolgreich verläuft, wird die folgende Meldung angezeigt, die besagt, dass Ihr Messaging-Erweiterungsdienst bei Ihrem `localhost` Folgendes überwacht:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. querladen Ihrer Messaging Erweiterung in Microsoft Teams

Wenn Ihre Messaging-Erweiterung aktiv ist, können Sie Sie in Microsoft Teams installieren.

> [!TIP]
> Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)aus.

1. Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **für mich hinzufügen** aus.

## <a name="7-test-your-messaging-extension"></a>7. Testen der Messaging Erweiterung

Erfahren Sie, wie Messaging-Erweiterungen in einem Microsoft Teams-Chat funktionieren.

1. Starten Sie einen neuen Chat. Wählen Sie im Feld Verfassen die Option **Weitere** aus, :::image type="icon" source="../assets/icons/teams-client-more.png"::: und wählen Sie die soeben quer geladene Messaging-Erweiterungs-App aus.
1. Suchen Sie nach etwas (beispielsweise **Tickets** ). Wenn Ihre APP funktioniert, werden Beispiel Suchergebnisse angezeigt (Sie können Sie später hinzufügen).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messaging Erweiterung im Feld &quot;Teams erstellen&quot; verwendet wird.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Standard-Microsoft Teams-Messaging Erweiterung, die für die Suche nach externem Inhalt im Feld Verfassen oder Befehl eingerichtet ist.

## <a name="next-steps"></a>Nächste Schritte

Auf den folgenden Seiten können Sie fortfahren und eine vollständig ausgestattete Messaging Erweiterung erstellen:

1. [Definieren Sie Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) , die für Ihren Dienst relevant sind.
1. Konfigurieren Sie den Dienst so, dass er [auf die Suchvorgänge von Benutzern reagiert](../messaging-extensions/how-to/search-commands/respond-to-search.md).

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Microsoft Teams verbunden

Wenn Sie Ihre APP installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der bot der Messaging Erweiterung [mit dem Microsoft Teams- *Kanal* des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.

Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist. In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.

## <a name="learn-more"></a>Mehr erfahren

* [Einschließen einer Link-Entfaltungs Funktion](../messaging-extensions/how-to/link-unfurling.md)
* [Authentifizierung hinzufügen](../messaging-extensions/how-to/add-authentication.md)
* [Erstellen einer Aktions basierten Messaging Erweiterung](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft bot-Framework](https://dev.botframework.com/)
