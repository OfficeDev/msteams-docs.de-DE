---
title: Erste Schritte – Erstellen einer Messaging Erweiterung
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine Microsoft Teams-Messaging Erweiterung.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: b19856eacee866ebbc89f21ac12575f1392918b3
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452834"
---
# <a name="build-a-messaging-extension-for-microsoft-teams"></a>Erstellen einer Messaging Erweiterung für Microsoft Teams

Es gibt zwei Typen von Microsoft Teams- *Messaging Erweiterungen*: [Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) und [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md).

In dieser Lektion erstellen Sie einen *Suchbefehl* (auch als *Suchbasierte Messaging Erweiterung*bezeichnet), bei dem es sich um eine Verknüpfung zum Suchen externer Inhalte und deren Freigabe in Microsoft Teams handelt. Benutzer können über das [Feld Verfassen oder Ausführen des Teams](../messaging-extensions/what-are-messaging-extensions.md)auf Suchbefehle zugreifen.

## <a name="your-assignment"></a>Ihre Zuordnung

Das Helpdesk Ihrer Organisation kommuniziert mit Benutzern über Teams, die Tickets befinden sich jedoch in einem separaten System. Dies bedeutet, dass Supportmitarbeiter ständig zwischen apps hin und her wechseln müssen. Sie werden untersuchen, wie Sie diese vielseitige Kontext Umstellung reduzieren können, indem Sie eine einfache suchbasierte Messaging Erweiterung für Teams erstellen.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Erstellen eines App-Projekts und eines bot für die Messaging Erweiterung mithilfe des Microsoft Teams-Toolkits für Visual Studio Code
> * Identifizieren der Eigenschaften des App-Manifests und einiger für Messaging-Erweiterungen relevanter Gerüste
> * Lokal Hosten einer APP
> * Konfigurieren des bot für Ihre Messaging Erweiterung
> * Querladen und Testen einer Messaging Erweiterung in Microsoft Teams

## <a name="before-you-begin"></a>Vorabinformationen

Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Das Microsoft Teams-Toolkit hilft Ihnen beim Einrichten der folgenden Komponenten für Ihre Messaging-Erweiterung:

* Für Messaging-Erweiterungen relevantes **App-Manifest und Gerüste**
* **Bot** für Ihre Messaging-Erweiterung, die automatisch beim Microsoft Azure bot-Dienst registriert wird

> [!TIP]
> Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Messaging Erweiterung** und dann dann **weiter**aus.
1. Führen Sie auf dem Bildschirm **Messaging-Erweiterung konfigurieren** die folgenden Aktionen aus:
    1. Wählen Sie nur die **Suchbasierte** Option für den Typ der Messaging Erweiterung aus.
    1. Wählen Sie **Create a New bot** and **Login** aus, um sich mit Ihrem Microsoft 365-entwicklungskonto anzumelden.
    1. Speichern Sie Ihre bot-ID und Ihr Kennwort (Sie benötigen dies ein wenig später).
    1. Optional Geben Sie einen benutzerdefinierten Namen für Ihren bot ein, und wählen Sie **Erstellen**aus. (Dies ist nicht der Name der Microsoft Teams-APP, die Sie bereits angegeben haben.)
    1. Wählen Sie im Moment **Nein** für die Option zum Aufheben der Verknüpfung aus.</br>
:::image type="content" source="../assets/images/build-your-first-app/choose-me-search.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot für Ihre Messaging Erweiterung zu erstellen.":::
1. Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.

## <a name="2-identify-relevant-app-project-components"></a>2. Identifizieren der relevanten App-Projektkomponenten

Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.

### <a name="app-manifest"></a>App-Manifest

Im folgenden Codeausschnitt aus dem App-Manifest (die `manifest.json` Datei im Verzeichnis des Projekts `.publish` ) werden die Eigenschaften und Standardwerte für Messaging Erweiterungen angezeigt.

```JSON
"composeExtensions": [
    {
        "botId": "{botId0}",
        "canUpdateConfiguration": true,
        "commands": [
            {
                "id": "searchQuery",
                "context": [
                    "compose",
                    "commandBox"
                ],
                "description": "Test command to run query",
                "title": "Search",
                "type": "query",
                "parameters": [
                    {
                        "name": "searchQuery",
                        "title": "Search Query",
                        "description": "Your search query",
                        "inputType": "text"
                    }
                ]
            }
        ]
    }
],
```

Lassen Sie uns einige der Eigenschaften verstehen, die das Toolkit für Sie erstellt hat. (Weitere Informationen finden Sie in der vollständigen Liste unterstützter [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) Eigenschaften.)

* `botId`: Die ID des bot, den Sie zum Einrichten Ihres Projekts erstellt haben. (In gespeichert `{botId0}` , können Sie die tatsächliche ID in suchen `Development.env` .)
* `commands`: Verfügbare Befehle für die Messaging Erweiterung. Das Toolkit bietet Ihnen ein Gerüst für einen Suchbefehl.
* `context`: Wo Benutzer die Messaging Erweiterung aufrufen können. In diesem Fall können Sie die Messaging Erweiterung im Verfassen-oder Befehlsfeld Teams starten.
* `description`: Hilfetext zur Benutzeroberfläche, der angibt, was der Befehl ausführt oder wie er verwendet wird.
* `parameters`: Enthält alle Parameter, die ein Befehl akzeptiert (Sie müssen mindestens einen haben und kann bis zu fünf).
* `parameters.description`: Hilfetext zur Benutzeroberfläche, der den Zweck oder die Beispiel Eingabe des Parameters beschreibt.

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst enthält eine `.env` Datei, die sich im Stammverzeichnis des Projekts befindet und die ID und das Kennwort für den bot Ihrer Messaging Erweiterung speichert.

Auch im Stammverzeichnis gibt es eine Datei, in der `botActivityHandler.js` Sie behandeln können, wie Ihre Messaging Erweiterung (oder der [bot der Messaging Erweiterung](#4-configure-the-bot-for-your-messaging-extension)) auf Suchabfragen in Microsoft Teams reagiert.

## <a name="3-set-up-a-secure-tunnel-to-your-app"></a>3. Einrichten eines sicheren Tunnels für Ihre APP

Zu Testzwecken hosten wir Ihre Messaging-Erweiterung auf einem lokalen Webserver (Port 3978).

1. Führen Sie in einem Terminal aus `ngrok http -host-header=rewrite 3978` .
1. Kopieren Sie die HTTPS-URL in der Ausgabe, da für Teams HTTPS-Verbindungen erforderlich sind.
1. Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .
1. Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL. (Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

Ihr App-Manifest zeigt auf die Stelle, an der Sie den von der Messaging Erweiterung verwendeten bot hosten.

## <a name="4-configure-the-bot-for-your-messaging-extension"></a>4. Konfigurieren des bot für Ihre Messaging-Erweiterung

Messaging-Erweiterungen beruhen darauf, dass Bots Benutzeranforderungen von Teams an den gehosteten Dienst senden und verarbeiten.

Der bot muss mit dem Azure bot-Dienst registriert werden, der beim Einrichten Ihrer APP mit dem Teams-Toolkit ausgeführt wurde.

### <a name="specify-your-bot-id-and-password"></a>Geben Sie Ihre bot-ID und Ihr Kennwort ein.

Wenn Ihr bot mit dem Azure bot-Dienst registriert ist, erhält er eine ID und ein Kennwort, über die ihre Teams-App Bescheid wissen muss.

1. Suchen Sie die bot-ID und das Kennwort, die Sie während des Toolkit-Setups gespeichert haben.
1. Öffnen Sie in Ihrem Stammverzeichnis die `.env` Datei.
1. Legen Sie Ihre bot-ID und Ihr Kennwort auf die `BotId` Eigenschaften und fest `BotPassword` .

### <a name="add-the-bot-endpoint-address"></a>Hinzufügen der bot-Endpunktadresse

Sie müssen eine bot-Endpunkt-URL angeben, um Suchabfragen in Ihrer Messaging-Erweiterung zu empfangen und zu verarbeiten. Normalerweise sieht die URL wie aus `https://HOST_URL/api/messages` . Sie können dies schnell im Teams-Toolkit konfigurieren.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Microsoft Teams Toolkit öffnen**aus.
1. Wechseln Sie zu **bot Management > vorhandene bot-Registrierungen** , und wählen Sie den bot aus, den Sie während des Setups erstellt haben.
1. Geben Sie in das Feld **bot-Endpunktadresse** den lokalen Webserver ein, auf dem Sie den bot hosten ( `baseUrl10` Wert), und fügen Sie `/api/messages` ihn hinzu.

Ihr bot ist in der Lage, Abfragen in Ihrer Messaging-Erweiterung zu verarbeiten.

## <a name="5-run-your-app"></a>5. führen Sie Ihre APP aus.

Sie haben eine URL eingerichtet, die Ihre Messaging-Erweiterung hostet und für die Verarbeitung von Suchvorgängen konfiguriert ist. Es ist an der Zeit, Ihre APP in Betrieb zu nehmen.

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Wenn die Meldung erfolgreich verläuft, wird die folgende Meldung angezeigt, die darauf hinweist, dass Ihr Messaging-Erweiterungsdienst bei Ihrem `localhost` Folgendes überwacht:

`Bot/ME service listening at http://localhost:3978`

## <a name="6-sideload-your-messaging-extension-in-teams"></a>6. querladen Ihrer Messaging Erweiterung in Microsoft Teams

Wenn Ihre Messaging-Erweiterung aktiv ist, können Sie Sie in Microsoft Teams installieren.

> [!TIP]
> Wenn Sie noch keine Teams-App quer geladene haben und Probleme haben, führen Sie die folgenden [Schritte](../build-your-first-app/build-and-run.md#5-sideload-your-app-in-teams)aus.

1. Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt.
1. Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.
1. Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` .
1. Wählen Sie im modalen Installationsmodus die Option **Hinzufügen** aus, um Ihre APP zu installieren.

## <a name="7-test-your-messaging-extension"></a>7. Testen der Messaging Erweiterung

Erfahren Sie, wie Messaging-Erweiterungen in einem Microsoft Teams-Chat funktionieren.

1. Starten Sie einen neuen Chat. Wählen Sie im Feld Verfassen die Option **Weitere** aus, :::image type="icon" source="../assets/icons/teams-client-more.png"::: und wählen Sie die soeben quer geladene Messaging-Erweiterungs-App aus.<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-access.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot für Ihre Messaging Erweiterung zu erstellen.":::
1. Versuchen Sie, nach etwas zu suchen (beispielsweise "Tickets"). Wenn Ihre APP funktioniert, werden Beispiel Suchergebnisse angezeigt (Sie können Sie später hinzufügen).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Abbildung, die zeigt, wie Sie sich im Teams-Toolkit bei Ihrem Microsoft 365-Konto anmelden können, um einen neuen bot für Ihre Messaging Erweiterung zu erstellen.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Standard-Microsoft Teams-Messaging Erweiterung, die für die Suche nach externem Inhalt im Feld Verfassen oder Befehl eingerichtet ist.

## <a name="next-steps"></a>Nächste Schritte

Auf den folgenden Seiten können Sie fortfahren und eine vollständig ausgestattete Messaging Erweiterung erstellen:

1. [Definieren Sie Suchbefehle](../messaging-extensions/how-to/search-commands/define-search-command.md) , die für Ihren Dienst relevant sind.
1. Konfigurieren Sie den Dienst so, dass er [auf die Suchvorgänge von Benutzern reagiert](../messaging-extensions/how-to/search-commands/respond-to-search.md).

## <a name="troubleshooting"></a>Problembehandlung

Die folgenden Informationen können hilfreich sein, wenn beim Abschluss dieses Lernprogramms Probleme aufgetreten sind.

### <a name="toolkit-setup-fails"></a>Toolkit-Setup schlägt fehl

Beim Einrichten Ihres App-Projekts mit dem Teams-Toolkit erhalten Sie eine Fehlermeldung, nachdem Sie die Option **neue bot erstellen** ausgewählt und sich mit Ihrem Microsoft 365-entwicklungskonto angemeldet haben.

Hierbei kann es sich um ein Authentifizierungsproblem handeln. Führen Sie die folgenden Schritte aus, um das Einrichten Ihres Projekts abzuschließen.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **Abmelden aus**.
1. Durchlaufen Sie den Setupvorgang erneut, indem Sie sich mit demselben Konto anmelden und einen neuen bot erstellen.

### <a name="bot-isnt-connected-to-teams"></a>Bot ist nicht mit Microsoft Teams verbunden

Wenn Sie Ihre APP installiert haben, aber nicht funktioniert, stellen Sie sicher, dass der bot der Messaging Erweiterung [mit dem Microsoft Teams- *Kanal*des Azure bot-Diensts verbunden](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true)ist.

Es ist wichtig zu verstehen, dass dies nicht mit einem Kanal in Microsoft Teams identisch ist. In diesem Fall stellt ein Kanal dar, wie der Azure bot-Dienst Ihren bot mit Teams oder einer anderen [unterstützten Microsoft-oder Drittanbieter-Kommunikations-App](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true)verbindet.

## <a name="learn-more"></a>Weitere Informationen

* [Einschließen einer Link-Entfaltungs Funktion](../messaging-extensions/how-to/link-unfurling.md)
* [Authentifizierung hinzufügen](../messaging-extensions/how-to/add-authentication.md)
* [Erstellen einer Aktions basierten Messaging Erweiterung](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft bot-Framework](https://dev.botframework.com/)
