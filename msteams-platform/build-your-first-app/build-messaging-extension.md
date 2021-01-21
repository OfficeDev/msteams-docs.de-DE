---
title: Erste Schritte – Erstellen einer Messagingerweiterung
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell eine Microsoft Teams-Messaging-Erweiterung.
ms.author: lajanuar
ms.date: 11/04/2020
ms.topic: tutorial
ms.openlocfilehash: 86d44740feaa2cd33aff0e1dde14d757420d90d6
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911919"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Erstellen einer Messagingerweiterung für Microsoft Teams

Es gibt zwei Arten von Messagingerweiterungen für *Teams-Apps:* [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle.](../messaging-extensions/how-to/action-commands/define-action-command.md)

In dieser Lektion erstellen Sie einen Suchbefehl *(auch* als suchbasierte *Messagingerweiterung* bezeichnet), der eine Verknüpfung zum Suchen externer Inhalte und zum Freigeben in Teams ist. Benutzer können über das Feld "Teams verfassen" oder ["Befehl" auf Suchbefehle zugreifen.](../messaging-extensions/what-are-messaging-extensions.md)

## <a name="your-assignment"></a>Ihre Zuordnung

Das Helpdesk Ihrer Organisation kommuniziert über Teams mit Benutzern, die Tickets befinden sich jedoch in einem separaten System. Das bedeutet, dass Supportmitarbeiter ständig zwischen Apps hin und her wechseln müssen. Sie untersuchen, wie Sie diesen Kontextwechsel reduzieren können, indem Sie eine einfache suchbasierte Messagingerweiterung für Teams erstellen.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und eines Messaging-Erweiterungs-Bots mithilfe des Microsoft Teams Toolkit for Visual Studio Code
> * Identifizieren der App-Konfigurationen und einiger der für Messagingerweiterungen relevanten Gerüste
> * Lokales Hosten einer App
> * Konfigurieren des Bots für Ihre Messagingerweiterung
> * Querladen und Testen einer Messagingerweiterung in Teams

## <a name="before-you-begin"></a>Vorabinformationen

Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die Entwicklung von Teams verstehen und [installieren.](build-first-app-overview.md#get-prerequisites)

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Mit dem Microsoft Teams Toolkit können Sie die folgenden Komponenten für Ihre Messagingerweiterung einrichten:

* **Für Messagingerweiterungen relevante App-Konfigurationen** und Gerüste
* **Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure Bot Service registriert wird

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diesen Anweisungen zu folgen, die Projekte ausführlicher erläutern.

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Create a new Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem Bildschirm "Funktionen** hinzufügen" die Option **"Messagingerweiterung" und** dann **"Weiter" aus.**
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.)
1. Gehen Sie **auf dem Bildschirm "Messagingerweiterung konfigurieren"** wie folgt vor:
    1. Wählen Sie nur **die suchbasierte Option** für den Typ der Messagingerweiterung aus.
    1. Wählen **Sie "Neuen Bot erstellen"** und dann **"Botregistrierung erstellen" aus.** Wenn dies erfolgreich ist, hat Ihr neuer Bot den **Status "Registriert".**
    1. Wählen Sie derzeit **"Nein"** für die Option zum Deaktivieren des Links aus.
1. Wählen **Sie "Fertig** stellen" am unteren Rand des Bildschirms aus, um das Projekt zu konfigurieren.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren relevanter Komponenten des App-Projekts

Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.

### <a name="app-configurations"></a>App-Konfigurationen

Wenn Sie die Konfigurationen Ihrer Messagingerweiterung anzeigen oder aktualisieren möchten, wählen **Sie App Studio** im Toolkit aus, und wechseln Sie zu **Messaging-Erweiterungen.**

### <a name="app-scaffolding"></a>App-Gerüst

Das App-Gerüst stellt eine Datei im Stammverzeichnis Ihres Projekts zur Verfügung, um zu behandeln, wie Ihre Messagingerweiterung (oder technisch der Bot der Messagingerweiterung) auf Suchabfragen `botActivityHandler.js` in Teams reagiert. [](#4-configure-the-bot-for-your-messaging-extension)

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre App

Zu Testzwecken hosten wir Ihre Messagingerweiterung auf einem lokalen Webserver (Port 3978).

1. Falls noch nicht, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` .
1. Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams https-Verbindungen benötigt.

Mit dieser URL kann Teams (für das HTTPS-Verbindungen erforderlich sind) an den Ort tunneln, an dem Sie Ihre App hosten (an `localhost` Port 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Konfigurieren des Bots für Ihre Messagingerweiterung

Messagingerweiterungen verlassen sich auf Bots, um Benutzeranforderungen von Teams an Ihren gehosteten Dienst zu senden und zu verarbeiten. Der Bot muss beim Azure Bot Service registriert sein, was beim Einrichten Ihrer App mithilfe des Teams Toolkits erfolgt ist.

Sie müssen dennoch eine Botendpunkt-URL angeben, um Suchabfragen in Ihrer Messagingerweiterung zu empfangen und zu verarbeiten. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies im Toolkit schnell konfigurieren.

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Open Microsoft Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Toolkit**.
1. Wechseln Sie **zu Bots > vorhandenen Botregistrierungen,** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie **im Adressfeld des** Bot-Endpunkts die ngrok-URL ein (z. B. ), in der Sie den Bot hosten, `https://468b9ab725e9.ngrok.io` und fügen Sie ihn `/api/messages` an.

Ihr Bot kann Abfragen in Ihrer Messagingerweiterung verarbeiten.

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihrer Messagingerweiterung eingerichtet und für die Verarbeitung von Suchen konfiguriert. Es ist an der Zeit, Ihre App zu starten und zu starten.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.
1. Führen Sie `npm start` .

Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die angibt, dass ihr Messagingerweiterungsdienst Aktivitäten an Ihrem Gerät `localhost` abhört:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Querladen Ihrer Messagingerweiterung in Teams

Wenn Ihre Messagingerweiterung ausgeführt wird, können Sie sie in Teams installieren.

> [!TIP]
> Wenn Sie zuvor noch keine Teams-App sideloaded haben und Probleme auftreten, führen Sie die folgenden [Anweisungen aus.](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams)

1. Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.
1. Wählen Sie im Dialogfeld "App-Installation" die Option **"Für mich hinzufügen" aus.**

## <a name="7-test-your-messaging-extension"></a>7. Testen der Messagingerweiterung

Erfahren Sie, wie Messagingerweiterungen in einem Teams-Chat funktionieren.

1. Starten Sie einen neuen Chat. Wählen Sie im Feld zum Verfassen **mehr** aus, und wählen Sie :::image type="icon" source="../assets/icons/teams-client-more.png"::: die Messaging-Erweiterungs-App aus, die Sie gerade geladen haben.
1. Suchen Sie nach etwas (z. B. **Tickets).** Wenn Ihre App funktioniert, werden Beispielsuchergebnisse angezeigt (Sie können später eigene hinzufügen).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messagingerweiterung im Feld zum Verfassen von Teams verwendet wird.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine grundlegende Teams-Messaging-Erweiterung, die für die Suche nach externen Inhalten im Feld zum Verfassen oder Befehl eingerichtet ist.

## <a name="next-steps"></a>Nächste Schritte

Auf den folgenden Seiten können Sie fortfahren und eine voll funktionsfähige Messagingerweiterung erstellen:

1. [Definieren Sie Suchbefehle,](../messaging-extensions/how-to/search-commands/define-search-command.md) die für Ihren Dienst relevant sind.
1. Konfigurieren Sie Ihren Dienst [so, dass er auf Benutzersuchen reagiert.](../messaging-extensions/how-to/search-commands/respond-to-search.md)

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn beim Abschließen dieses Lernprogramms Probleme auftreten.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Teams verbunden

Wenn Sie Ihre App installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der Bot der Messagingerweiterung mit dem Teams-Kanal des [Azure Bot Service verbunden *ist.*](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)

Es ist wichtig zu wissen, dass dies nicht mit einem Kanal in Teams identisch ist. In diesem Fall verbindet der Azure Bot Service Ihren Bot mit Teams oder einer anderen unterstützten Microsoft- oder [Drittanbieter-Kommunikations-App.](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)

## <a name="learn-more"></a>Weitere Informationen

* [Fügen Sie ein Feature zum Entfing von Links ein.](../messaging-extensions/how-to/link-unfurling.md)
* Folgen Sie [unseren Entwurfsrichtlinien,](../messaging-extensions/design/messaging-extension-design.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.
* [Authentifizierung hinzufügen](../messaging-extensions/how-to/add-authentication.md)
* [Erstellen einer aktionsbasierten Messagingerweiterung](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)
