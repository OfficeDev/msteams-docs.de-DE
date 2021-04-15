---
title: Erste Schritte – Erstellen einer Messagingerweiterung
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-Messagingerweiterung mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 09e851820314efd3dc114b926a0111603cac18a4
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696878"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Erstellen einer Messagingerweiterung für Microsoft Teams

Es gibt zwei Arten von *Teams-Messagingerweiterungen:* [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle.](../messaging-extensions/how-to/action-commands/define-action-command.md)

In dieser Lektion erstellen Sie einen Suchbefehl *(auch* als suchbasierte Messagingerweiterung *bezeichnet),* der eine Verknüpfung zum Suchen externer Inhalte und deren Freigabe in Teams ist. Benutzer können über das Verfassen- oder [Befehlsfeld Teams auf Suchbefehle zugreifen.](../messaging-extensions/what-are-messaging-extensions.md)

## <a name="your-assignment"></a>Ihre Zuordnung

Der Helpdesk Ihrer Organisation kommuniziert mit Benutzern über Teams, die Tickets befinden sich jedoch in einem separaten System. Dies bedeutet, dass Supportmitarbeiter ständig zwischen Apps hin- und hergehen müssen. Sie untersuchen, wie Sie diesen Kontextwechsel reduzieren können, indem Sie eine einfache suchbasierte Messagingerweiterung für Teams erstellen.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und eines Messagingerweiterungsbots mithilfe des Microsoft Teams Toolkits für Visual Studio Code
> * Identifizieren der App-Konfigurationen und einiger Gerüste, die für Messagingerweiterungen relevant sind
> * Lokal hosten einer App
> * Konfigurieren des Bots für Ihre Messagingerweiterung
> * Querladen und Testen einer Messagingerweiterung in Teams

## <a name="before-you-begin"></a>Bevor Sie beginnen

Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die [Teams-Entwicklung verstehen und installieren.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Das Microsoft Teams Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre Messagingerweiterung:

* **Für Messagingerweiterungen** relevante App-Konfigurationen und Gerüste
* **Bot** für Ihre Messagingerweiterung, die automatisch beim Microsoft Azure Bot Service registriert ist

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, die Projekte ausführlicher erläutern.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem Bildschirm** Funktionen hinzufügen die Option **Messagingerweiterung** und dann **Weiter aus.**
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Gehen Sie auf dem Bildschirm **Messagingerweiterung** konfigurieren wie folgt vor:
    1. Wählen Sie nur **die suchbasierte** Option für den Typ der Messagingerweiterung aus.
    1. Wählen **Sie Erstellen eines neuen Bots** und dann **Botregistrierung erstellen aus.** Wenn der neue Bot erfolgreich ist, hat er den **Status "Registriert".**
    1. Wählen Sie im Ersten **Nein** für die Option zum Entf?nden des Links aus.
1. Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, um Ihr Projekt zu konfigurieren.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren relevanter App-Projektkomponenten

Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.

### <a name="app-configurations"></a>App-Konfigurationen

Wenn Sie die Konfigurationen Ihrer Messagingerweiterung anzeigen oder aktualisieren möchten, wählen Sie im Toolkit **App Studio aus,** und wechseln Sie zu **Messagingerweiterungen**.

### <a name="app-scaffolding"></a>App-Gerüst

Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verfügung, um zu behandeln, wie Ihre Messagingerweiterung (oder technisch der Bot der Messagingerweiterung) auf Suchabfragen `botActivityHandler.js` in Teams reagiert. [](#4-configure-the-bot-for-your-messaging-extension)

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre App

Zu Testzwecken hosten wir Ihre Messagingerweiterung auf einem lokalen Webserver (Port 3978).

1. Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` aus.
1. Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams HTTPS-Verbindungen erfordert.

Mit dieser URL kann Teams (für die HTTPS-Verbindungen erforderlich sind) zu dem Ort tunneln, an dem Sie Ihre App hosten ( `localhost` an Port 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Konfigurieren des Bots für Ihre Messagingerweiterung

Messagingerweiterungen verwenden Bots, um Benutzeranforderungen von Teams an Ihren gehosteten Dienst zu senden und zu verarbeiten. Der Bot muss beim Azure Bot Service registriert sein, was beim Einrichten Ihrer App mithilfe des Teams Toolkits erfolgt ist.

Sie müssen weiterhin eine Botendpunkt-URL angeben, um Suchabfragen in Ihrer Messagingerweiterung zu empfangen und zu verarbeiten. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies schnell im Toolkit konfigurieren.

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Microsoft Teams Toolkit **öffnen aus.**
1. Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL (z. B. ) ein, in der Sie den Bot hosten, und `https://468b9ab725e9.ngrok.io` fügen Sie ihn `/api/messages` an.

Ihr Bot kann Abfragen in Ihrer Messagingerweiterung verarbeiten.

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihrer Messagingerweiterung eingerichtet und für die Verarbeitung von Suchen konfiguriert. Es ist an der Zeit, Ihre App in Betrieb zu halten.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass Ihr Messagingerweiterungsdienst aktivitäten bei Ihrer `localhost` abhört:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Querladen Ihrer Messagingerweiterung in Teams

Wenn Ihre Messagingerweiterung ausgeführt wird, können Sie sie in Teams installieren.

> [!TIP]
> Wenn Sie eine Teams-App noch nicht nebeneinander geladen haben und Probleme auftreten, führen Sie diese [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)

1. Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen aus.**

## <a name="7-test-your-messaging-extension"></a>7. Testen Der Messagingerweiterung

Erfahren Sie, wie Messagingerweiterungen in einem Teams-Chat funktionieren.

1. Starten Sie einen neuen Chat. Wählen Sie im Feld Verfassen die Option **Mehr** :::image type="icon" source="../assets/icons/teams-client-more.png"::: aus, und wählen Sie die Messagingerweiterungs-App aus, die Sie gerade seitengeladen haben.
1. Versuchen Sie, nach etwas zu suchen (z. B. **Tickets**). Wenn Ihre App funktioniert, werden Beispielsuchergebnisse angezeigt (Sie können ihre eigenen später hinzufügen).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messagingerweiterung im Feld Teams verfassen verwendet wird.":::

## <a name="well-done"></a>Gut gemacht

Glückwunsch! Sie verfügen über eine grundlegende Teams-Messagingerweiterung, die für die Suche nach externen Inhalten im Verfassen- oder Befehlsfeld eingerichtet ist.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Erstellen einer voll funktionsfähigen Messagingerweiterung finden Sie auf den folgenden Seiten:

1. [Definieren Sie Suchbefehle,](../messaging-extensions/how-to/search-commands/define-search-command.md) die für Ihren Dienst relevant sind.
1. Konfigurieren Sie Ihren Dienst [so, dass er auf benutzersuchen reagiert.](../messaging-extensions/how-to/search-commands/respond-to-search.md)

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn Beim Abschließen dieses Lernprogramms Probleme auftreten.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Teams verbunden

Wenn Sie Ihre App installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der Bot der Messagingerweiterung mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist. In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Weitere Informationen

* [Schließen Sie ein Feature zum Entfingen eines Links ein.](../messaging-extensions/how-to/link-unfurling.md)
* Befolgen Sie [unsere Entwurfsrichtlinien,](../messaging-extensions/design/messaging-extension-design.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.
* [Authentifizierung hinzufügen](../messaging-extensions/how-to/add-authentication.md)
* [Erstellen einer aktionsbasierten Messagingerweiterung](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)

