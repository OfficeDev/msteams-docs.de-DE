---
title: Erste Schritte - Erstellen einer Messagingerweiterung
author: girliemac
description: Erstellen Sie schnell eine Microsoft Teams Messaging-Erweiterung mit dem Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/25/2021
ms.topic: tutorial
ms.openlocfilehash: c120a5b5d878c549cde008c3e1ccc71743a4e24f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566061"
---
# <a name="build-your-first-messaging-extension-for-microsoft-teams"></a>Erstellen Sie Ihre erste Messagingerweiterung für Microsoft Teams

Es gibt zwei Arten von Teams *Messaging-Erweiterungen:* [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md).

In diesem Tutorial lernen Sie an, einen *Suchbefehl* (auch als *suchbasierte Messagingerweiterung* bezeichnet) zu erstellen, der eine Verknüpfung zum Suchen externer Inhalte und zum Freigeben von externen Inhalten und deren Freigabe in Teams darstellt. Benutzer können über das Teams verfassen oder Befehlsfeld auf Suchbefehle zugreifen.

## <a name="what-youll-learn"></a>Was Sie lernen werden

* Erstellen Sie einen App-Projekt- und Messagingerweiterungsbot mit dem Microsoft Teams Toolkit für Visual Studio Code.
* Verstehen Sie die App-Konfigurationen und das Gerüst, das für Messaging-Erweiterungen relevant ist.
* Hosten Sie eine App lokal.
* Konfigurieren Sie den Bot für Ihre Messaging-Erweiterung.
* Sideload und testen Sie eine Messagingerweiterung in Teams.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen. Weitere Informationen finden Sie [unter Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App](../build-your-first-app/build-and-run.md).

## <a name="1-create-your-app-project"></a>1. Erstellen Sie Ihr App-Projekt

Das Microsoft Teams Toolkit unterstützt Sie beim Einrichten der folgenden Komponenten für Ihre Messagingerweiterung:

* **App-Konfigurationen und Gerüste,** die für Messaging-Erweiterungen relevant sind.
* **Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure Bot Service registriert ist.

**So erstellen Sie Ihr App-Projekt**

1. Wählen Sie in Visual Studio Code **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus, und wählen Sie **eine neue Teams-App erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Klicken **Sie** auf dem Bildschirm Projekt auswählen auf **Messaging Extensions**  >  **Search** auf **JS (JavaScript)**. 
1. Geben Sie einen Namen für Ihre Teams App ein. Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.
1. Wählen Sie **Einen neuen Bot** erstellen und klicken Sie dann auf Die Schaltfläche **Bot-Registrierung erstellen.** Wenn der Erfolg gelingt, hat Ihr neuer Bot einen *registrierten* Status. Jetzt wird Ihr Bot automatisch beim Microsoft Azure-Bot-Service registriert. 
1. Wählen Sie am unteren Bildschirmrand **fertig** aus, um das Projekt zu konfigurieren und das Projekt auf dem lokalen Computer zu speichern.

## <a name="2-understand-your-app-project-components"></a>2. Verstehen Ihrer App-Projektkomponenten

Ein Großteil der App-Konfigurationen und Gerüste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.

* App-Konfigurationen: Um die Konfigurationen Ihrer Messagingerweiterung anzuzeigen oder zu aktualisieren, wählen Sie **App Studio** im Toolkit aus, und wechseln Sie zu **Messagingerweiterungen**.
* App-Gerüst: Das App-Gerüst stellt eine `botActivityHandler.js` Datei bereit, die sich im Stammverzeichnis Ihres Projekts befindet, um zu verarbeiten, wie Ihre Messaging-Erweiterung (oder technisch gesehen der Bot der [Messaging-Erweiterung)](#4-configure-the-bot-for-your-messaging-extension)auf Suchanfragen in Teams reagiert.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Richten Sie einen sicheren Tunnel zu Ihrer App ein

Zu Testzwecken hosten wir Ihre Messagingerweiterung auf einem lokalen Webserver (Port 3978). Sie werden [ngrok](https://ngrok.com/download) verwenden, um einen sicheren Tunnel zum localhost einzurichten. Weitere Informationen finden Sie in [Build your first bot for Microsoft Teams.](../build-your-first-app/build-bot.md#3-securely-expose-your-localhost-to-the-internet) 

1. Wenn Sie dies noch nicht getan haben, installieren Sie [ngrok](https://ngrok.com/download).
1. Führen Sie in einem Terminal `ngrok http -host-header=rewrite 3978` aus.
1. Kopieren Sie die HTTPS-URL in der Ausgabe (z. B. `https://468b9ab725e9.ngrok.io` ), da Teams HTTPS-Verbindungen erfordert.

   Mit dieser URL können Teams (die HTTPS-Verbindungen erfordert) tunneln, wo Sie Ihre App hosten `localhost` (auf Port 3978).

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Konfigurieren Sie den Bot für Ihre Messaging-Erweiterung

Messagingerweiterungen sind auf Bots angewiesen, um Benutzeranfragen von Teams an Ihren gehosteten Dienst zu senden und zu verarbeiten. Der Bot muss beim Azure Bot Service registriert sein, was beim Einrichten Ihrer App mit dem Teams Toolkit durchgeführt wurde.

Sie müssen weiterhin eine Bot-Endpunkt-URL angeben, um Suchabfragen in Ihrer Messagingerweiterung zu empfangen und zu verarbeiten. In der Regel sieht die URL wie `https://HOST_URL/api/messages` aus. Sie können dies schnell im Toolkit konfigurieren.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**.
1. Gehen Sie zu **Bots > Vorhandene Bot-Registrierungen** und wählen Sie den Bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie im Feld **Bot-Endpunktadresse** die ngrok-URL (z. B. ) ein, in der Sie den Bot hosten und an ihn `https://468b9ab725e9.ngrok.io` `/api/messages` anhängen.

   Ihr Bot wird in der Lage sein, Abfragen in Ihrer Messaging-Erweiterung zu behandeln.

## <a name="5-build-and-run-your-app"></a>5. Erstellen und Ausführen Ihrer App

Sie haben eine URL zum Hosten Ihrer Messagingerweiterung eingerichtet und für die Verarbeitung von Suchvorgängen konfiguriert. Es ist an der Zeit, Ihre App in Betrieb zu nehmen.

1. Öffnen Sie das Terminal, und wechseln Sie zum Stammverzeichnis Ihres App-Projekts.
1. Führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

   Wenn dies erfolgreich ist, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr Messagingerweiterungsdienst auf Aktivitäten in Ihrem folgenden Dienst `localhost` wartet:

   `Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. Sideload Ihre Messaging-Erweiterung in Teams

Wenn Ihre Messagingerweiterung ausgeführt wird, können Sie sie in Teams installieren.

> [!TIP]
> Wenn Sie noch keine Teams App geladen haben und Probleme auftreten, befolgen Sie diese [Anweisungen](../build-your-first-app/build-and-run.md#4-sideload-your-app-in-teams).

1. Wählen Sie Visual Studio Code die **Taste F5** aus, um einen Teams Webclient zu starten.
1. Wählen Sie im Dialogfeld App-Installation die Option **Für mich hinzufügen** aus.

## <a name="7-test-your-messaging-extension"></a>7. Testen Sie Ihre Messaging-Erweiterung

Erfahren Sie, wie Messagingerweiterungen in einem Teams Chat funktionieren.

1. Starten Sie einen neuen Chat. Wählen Sie im Feld Verfassen **Mehr** :::image type="icon" source="../assets/icons/teams-client-more.png"::: aus, und wählen Sie die Messagingerweiterungs-App aus, die Sie gerade seitlich geladen haben.
1. Versuchen Sie, nach etwas zu suchen (z. B. **Tickets**). Wenn Ihre App funktioniert, sehen Sie Beispielsuchergebnisse (Sie können später eigene hinzufügen).

   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Ein Screenshot, der zeigt, wie eine suchbasierte Messagingerweiterung im Teams Verfassen verwendet wird.":::

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn Sie Probleme beim Abschließen dieses Tutorials hatten.

**Bot ist nicht mit Teams verbunden**

Wenn Sie Ihre App installiert haben, diese jedoch nicht funktioniert, stellen Sie sicher, dass der Bot der Messagingerweiterung [mit dem Teams *Kanal*](/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)des Azure Bot Service verbunden ist.

Es ist wichtig zu verstehen, dass dies nicht dasselbe ist wie ein Kanal in Teams. In diesem Fall ist ein Kanal, wie der Azure Bot Service Ihren Bot mit Teams oder einer anderen [unterstützten Microsoft- oder Drittanbieter-Kommunikations-App](/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.

## <a name="see-also"></a>Siehe auch

* [Teams Verfassen oder Befehlsfeld](../messaging-extensions/what-are-messaging-extensions.md) 
* [Einschließen einer Link-Entfurlingsfunktion](../messaging-extensions/how-to/link-unfurling.md)
* [Richtlinien für den Entwurf](../messaging-extensions/design/messaging-extension-design.md) 
* [Produktionsfähige UI-Vorlagen](../concepts/design/design-teams-app-ui-templates.md) 
* [Authentifizierung hinzufügen](../messaging-extensions/how-to/add-authentication.md)
* [Erstellen einer aktionsbasierten Messagingerweiterung](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Definition von Suchbefehlen](../messaging-extensions/how-to/search-commands/define-search-command.md)

> [!div class="nextstepaction"]
> [Reagieren auf die Suchanfragen der Benutzer](../messaging-extensions/how-to/search-commands/respond-to-search.md)
