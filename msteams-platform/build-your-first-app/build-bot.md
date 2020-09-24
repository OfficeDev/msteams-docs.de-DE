---
title: Erstellen eines Teams-bot
author: heath-hamilton
description: Hier erfahren Sie, wie Sie einen bot für Ihre erste Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: cc004bd0d86eca1e4e63c2a96a72f9c11d2269db
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237825"
---
# <a name="build-a-teams-bot"></a>Erstellen eines Teams-bot

In diesem Lernprogramm erstellen Sie eine einfache *bot* -app. Ein bot fungiert als Vermittler zwischen Microsoft Teams-Benutzern und Ihrem Webdienst. Personen können mit einem bot chatten, um schnell Informationen zu erhalten oder Workflows und Aufgaben zu initiieren, die von Ihrem Dienst ausgeführt werden.

## <a name="your-assignment"></a>Ihre Zuordnung

Ihr Arbeitsplatz verwendet [Registerkarten](../build-your-first-app/build-personal-tab.md) , um wichtige Kontaktinformationen in Microsoft Teams zu Surface. Kollegen haben beispielsweise schnellen Zugriff auf die Telefonnummer des Helpdesks. Aber statt aufzurufen, was wäre, wenn Personen mit einem Chatbot Kontakt zum Helpdesk aufnehmen könnten? Ihr Chef bittet Sie, sich anzusehen, wie schnell Sie einen einfachen Unterhaltungs bot in Microsoft Teams in Betrieb nehmen können.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und bot mithilfe des Microsoft Teams-Toolkits für Visual Studio Code
> * Identifizieren der Eigenschaften und Gerüste für App-Manifeste, die für Bots relevant sind
> * Lokal Hosten einer APP
> * Konfigurieren eines bot für Teams
> * Querladen und Testen eines bot in Microsoft Teams

## <a name="before-you-begin"></a>Bevor Sie beginnen

Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Das Microsoft Teams-Toolkit hilft Ihnen, die folgenden Komponenten für Ihre APP einzurichten:

* **App-Manifest und** für Bots relevante Gerüste
* **Bot** , der automatisch beim Microsoft Azure bot-Dienst registriert wird

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **bot** und dann **weiter**aus.
1. Wählen Sie **Create a New bot** and **Login** aus, um sich mit Ihrem Microsoft 365-entwicklungskonto anzumelden.<br/>
:::image type="content" source="../assets/images/build-your-first-app/vsc-create-bot.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot zu erstellen.":::
1. Speichern Sie Ihre bot-ID und Ihr Kennwort (Sie benötigen dies ein wenig später).
1. Optional Geben Sie einen benutzerdefinierten Namen für Ihren bot ein, und wählen Sie **Erstellen**aus. (Denken Sie daran, dies ist der Name für Ihren bot und nicht der Name der Microsoft Teams-APP, die Sie bereits angegeben haben.)
1. Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren der relevanten App-Projektkomponenten

Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen. Lassen Sie uns die Hauptkomponenten zum Erstellen eines bot betrachten.

### <a name="app-manifest"></a>App-Manifest

Im folgenden Codeausschnitt aus dem App-Manifest (die `manifest.json` Datei im Verzeichnis des Projekts `.publish` ) werden die Eigenschaften und Standardwerte für Bots angezeigt.

```JSON
"bots": [
    {
        "botId": "{botId0}",
        "scopes": [
            "personal",
            "groupchat",
            "team"
        ],
        "supportsFiles": false,
        "isNotificationOnly": false,
        "commandLists": [
            {
                "scopes": [
                    "personal",
                    "groupchat",
                    "team"
                ],
                "commands": [
                    {
                        "title": "Hello",
                        "description": "Sends a hello message and @mention the sender"
                    }
                ]
            }
        ]
    }
],
```

Lassen Sie uns im Moment nur auf die folgenden erforderlichen Eigenschaften konzentrieren. (Weitere Informationen finden Sie in der vollständigen Liste unterstützter [`bots`](../resources/schema/manifest-schema.md#bots) Eigenschaften.)

* `botId`: Die ID des bot, den Sie zum Einrichten Ihres Projekts erstellt haben. (In gespeichert `{botId0}` , können Sie die tatsächliche ID in suchen `Development.env` .)
* `scopes`: Gibt an, ob Ihr bot in `personal` -, `groupchat` -oder- `team` (also Kanal-) Kontexten verfügbar ist.
* `commands`: Verfügbare Befehle, die Benutzer an Ihren bot senden können.
* `title`: Bot-Befehlsname, der im Teams-Client angezeigt wird.
* `description`: Eine kurze Beschreibung oder ein Beispiel für die Syntax und die Argumente, mit denen Benutzer verstehen, was ein bot-Befehl bewirkt.

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst enthält eine `botActivityHandler.js` Datei, die sich im Stammverzeichnis des Projekts befindet, um zu behandeln, wie Ihr Bot Aktivitäten in Microsoft Teams verarbeitet (beispielsweise, wie der bot auf bestimmte Nachrichten wie "Hello" reagiert).

Die `.env` Datei, auch im Stammverzeichnis, speichert Ihre bot-ID und Ihr Kennwort.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre APP

Zu Testzwecken hosten wir Ihren bot auf einem lokalen Webserver (Port 3978).

1. Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .
1. Kopieren Sie die HTTPS-URL in der Ausgabe, da für Teams HTTPS-Verbindungen erforderlich sind.
1. Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .
1. Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL. (Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

Ihr App-Manifest zeigt auf die Stelle, an der Sie den bot hosten.

## <a name="4-configure-your-bot"></a>4. Konfigurieren Ihres bot

Um einen bot in Microsoft Teams zu verwenden, müssen Sie ihn bei dem Azure bot-Dienst registrieren. Glücklicherweise wird dies automatisch durchgeführt, wenn Sie Ihre APP mit dem Teams-Toolkit einrichten.

### <a name="specify-your-bot-id-and-password"></a>Geben Sie Ihre bot-ID und Ihr Kennwort ein.

Wenn Ihr bot mit dem Azure bot-Dienst registriert ist, erhält er eine ID und ein Kennwort, über die ihre Teams-App Bescheid wissen muss.

1. Suchen Sie die bot-ID und das Kennwort, die Sie während des Toolkit-Setups gespeichert haben.
1. Öffnen Sie in Ihrem Stammverzeichnis die `.env` Datei.
1. Fügen Sie Ihre bot-ID und Ihr Kennwort zu `BotId` bzw `BotPassword` . hinzu.

### <a name="add-the-bot-endpoint-address"></a>Hinzufügen der bot-Endpunktadresse

Sie müssen eine Endpunkt-URL angeben, um Benutzer Nachrichten (d. h., Anforderungen) zu empfangen und zu verarbeiten, die an den bot gesendet werden. Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` . Sie können dies schnell im Teams-Toolkit konfigurieren.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**aus.
1. Wechseln Sie zu **bot Management > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie in das Feld **bot-Endpunktadresse** den lokalen Webserver ein, auf dem Sie den bot hosten ( `baseUrl10` Wert), und fügen Sie `/api/messages` ihn hinzu.

    :::image type="content" source="../assets/images/build-your-first-app/bot-config-endpoint-url.png" alt-text="Abbildung zeigt, wo Sie die bot-Endpunkt-URL im Teams-Toolkit konfigurieren können.":::

Ihr bot wird in der Lage sein, auf Nachrichten in Microsoft Teams zu antworten.

## <a name="5-run-your-app"></a>5. führen Sie Ihre APP aus.

Sie haben eine URL zum Hosten Ihres bot eingerichtet und für die Verarbeitung von Nachrichten konfiguriert. Es ist an der Zeit, dass Ihr bot in Betrieb geht.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Wenn die Meldung erfolgreich verläuft, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr bot ihre Aktivität überwacht `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-bot-in-teams"></a>6. querladen Ihres bot in Microsoft Teams

Wenn Ihr bot läuft, können Sie ihn in Microsoft Teams installieren.

> [!TIP]
> Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#5-sideload-your-app-in-teams)aus.

1. Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.
1. Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.
1. Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .
1. Wählen Sie im modalen Installationsmodus die Option **Hinzufügen** aus, um Ihre APP zu installieren.

## <a name="7-test-your-bot"></a>7. Testen Sie Ihren bot

Nun zum spaßigen Teil: sagen wir "Hallo" zu Ihrem bot in einem Einzelchat.

1. Wählen Sie in Microsoft **More** Teams :::image type="icon" source="../assets/icons/teams-client-more.png"::: auf der linken Seite Weitere aus.
1. Suchen und wählen Sie den bot, den Sie gerade quer geladene.<br/>
   :::image type="content" source="../assets/images/build-your-first-app/bot-teams-access.png" alt-text="Illustration, die zeigt, wo Sie in Microsoft Teams auf Ihren bot zugreifen.":::
1. Senden Sie im Feld Verfassen eine `Hello` Nachricht.

Ihr bot antwortet mit so etwas wie der folgenden Nachricht.

:::image type="content" source="../assets/images/build-your-first-app/contoso-chatbot.png" alt-text="Ein Screenshot mit einem Benutzer, der "Hello" zu einem Team-bot und einer Antwort ruft.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie haben einen einfachen Teams-bot, der mit Benutzern einzeln oder in Gruppeneinstellungen (Kanäle und Chats) kommunizieren kann.

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.

### <a name="toolkit-setup-fails"></a>Toolkit-Setup schlägt fehl

Beim Einrichten Ihres App-Projekts mit dem Teams-Toolkit erhalten Sie eine Fehlermeldung, nachdem Sie die Option **neue bot erstellen** ausgewählt und sich mit Ihrem Microsoft 365-entwicklungskonto angemeldet haben.

Hierbei kann es sich um ein Authentifizierungsproblem handeln. Führen Sie die folgenden Schritte aus, um das Einrichten Ihres Projekts abzuschließen.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Abmelden aus**.
1. Durchlaufen Sie den Setupvorgang erneut, indem Sie sich mit demselben Konto anmelden und einen neuen bot erstellen.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Microsoft Teams verbunden

Wenn Sie Ihre APP installiert haben, aber der bot nicht funktioniert, stellen Sie sicher, dass der bot [mit dem Microsoft Teams- *Kanal*des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.

Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist. In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.

## <a name="learn-more"></a>Weitere Informationen

* [Sehen Sie sich an, was andere Teams-Bots mit einem unserer Beispiele tun können](https://github.com/microsoft/BotBuilder-Samples#teams-samples)
* [Grundlegende Informationen zu Bot-Unterhaltungen](../bots/how-to/conversations/conversation-basics.md)
* [Bot-Authentifizierung in Microsoft Teams](../bots/how-to/authentication/auth-flow-bot.md)
* [Microsoft bot-Framework](https://dev.botframework.com/)
* [Erstellen eines bot ohne Toolkit](../bots/how-to/create-a-bot-for-teams.md)
