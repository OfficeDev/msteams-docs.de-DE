---
title: Erste Schritte – Erstellen Ihres ersten Bots
author: adrianhall
description: Erstellen Sie einen Bot für Microsoft Teams mit dem Teams Toolkit.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.localizationpriority: none
ms.openlocfilehash: 7e41de915e63b509da1db5b1cbe8e018be4d586d
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360604"
---
# <a name="build-your-first-bot-for-microsoft-teams"></a>Erstellen Ihres ersten Bots für Microsoft Teams

In diesem Lernprogramm erfahren Sie, wie Sie eine Teams-Bot-App erstellen, ausführen und bereitstellen. Ein Bot agiert als Vermittler zwischen einem Teams-Benutzer und einem Webdienst. Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten, Workflows zu initiieren, oder für alles andere, was Ihr Webservice tun kann. 

> [!IMPORTANT]
> Derzeit sind Bots in Government Community Cloud (GCC) verfügbar, aber nicht in GCC-High und department of Defense (DOD).

## <a name="before-you-begin"></a>Bevor Sie beginnen

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.

> [!div class="nextstepaction"]
> [Installieren erforderlicher Komponenten](prerequisites.md)

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie das symbol Teams in der Seitenleiste aus, um das Teams Toolkit zu öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Klicken Sie auf **Neues Projekt erstellen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. Wählen Sie im Abschnitt **"Funktionen auswählen"** die Option **"Bot"** aus, deaktivieren **Sie die Registerkarte,** und wählen Sie **"OK"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities-bot.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. Wählen Sie im Abschnitt **"Bot-Registrierung"** die Option **"Neue Bot-Registrierung erstellen"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Registrierung eines Bots erstellen“ aus":::

1. Wählen Sie im Abschnitt **"Programmiersprache"** **JavaScript** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie einen Arbeitsbereichsordner aus.  Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur alphanumerische Zeichen enthalten.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.  Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.

``` bash
teamsfx new
```

Die CLI führt durch einige Fragen zum Erstellen des Projekts.  Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).  Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.
1. Wählen Sie **Bot** aus, und heben Sie die **Auswahl auf der Registerkarte auf.**
1. Wählen Sie **Eine neue Registrierung eines Bots erstellen** aus.
1. Wählen Sie **JavaScript** als Programmiersprache aus.
1. Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.
1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.

Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.

---

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).

Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.  Nach der Gerüsterstellung wird Ihr Projekt folgend aussehen:

:::image type="content" source="../assets/images/teams-toolkit-v2/bot-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

Der Bot-Code wird im `bot` Verzeichnis gespeichert.  Dies `bot/teamsBot.js` ist der Haupteinstiegspunkt für den Bot.

> [!Tip]
> Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.  Sie können weitere Informationen zu Bots im Lernprogramme von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.

## <a name="run-your-app-locally"></a>Lokales Ausführen Ihrer App

Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.  Gehen Sie hierfür folgendermaßen vor:

- Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.
- Ein App-Manifest wird dem Entwickler-Center für Teams übermittelt.
- [ngrok](https://ngrok.io) ist installiert und wird dazu verwendet, einen Tunnel zwischen Teams und Ihrem Bot-Code bereitzustellen.

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie Visual Studio Code die **F5-Taste,** um die Anwendung im Debugmodus auszuführen.

   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.  Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.  Dies kann 3 bis 5 Minuten dauern.

1. Ihr Webbrowser beginnt mit der Ausführung der App. Wenn Sie aufgefordert werden, Teams Desktop zu öffnen, wählen Sie **"Abbrechen"** aus, um im Browser zu verbleiben. Möglicherweise werden Sie auch aufgefordert, zu anderen Zeiten zu Teams Desktop zu wechseln. wählen Sie in diesem Fall die Teams Web-App aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. Möglicherweise werden Sie aufgefordert, sich anzumelden.  Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App auf Teams zu installieren, wählen Sie **Hinzufügen** aus.

   Nachdem die App geladen wurde, werden Sie direkt zu einer Chatsitzung mit dem Bot weitergeleitet.  Sie können `welcome` eingeben, um eine Einführungskarte anzuzeigen und `learn` die Dokumentation für adaptive Karten und Bot-Befehle zu öffnen. 

   Das Debuggen funktioniert so, wie Sie es normalerweise erwarten – probieren Sie es selbst aus! Öffnen Sie die Datei `bot/teamsBot.js`, und suchen Sie die `onMessage()`-Methode.  Legen Sie für jeden Fall einen Haltepunkt fest.  Geben Sie dann einigen Text ein.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</summary>

Wenn Sie die **F5-Taste** drücken, wird das Teams Toolkit:

1. Registriert Ihre Anwendung bei Azure Active Directory.
1. Registriert Ihre Anwendung für das "Querladen" in Microsoft Teams.
1. Startet einen ngrok-Tunnel, damit Teams mit Ihrer App kommunizieren können.
1. Startet Microsoft Teams mit einem Befehl, um Teams anzuweisen, die Anwendung querzuladen.

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</summary>

Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, das das Querladen von Apps ermöglicht. Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).

> [!IMPORTANT]
> Sideloading-Apps sind derzeit in Government Community Cloud (GCC), GCC-Hoch und DOD verfügbar.

> [!TIP]
> Überprüfen Sie mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt, bevor Sie ihre App querladen. Beheben Sie die Probleme, um die App erfolgreich querzuladen.
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</summary>

Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:

1. Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.

   Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure. Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.

</details>

## <a name="see-also"></a>Siehe auch

* [Übersicht über Lernprogramme](code-samples.md) 
* [Erstellen einer App mit React](first-app-react.md)
* [Erstellen einer App mitHilfe von Blatter](first-app-blazor.md)
* [Erstellen einer App mit SPFx](first-app-spfx.md)
* [Erstellen einer App mithilfe von C# oder .NET](get-started-dotnet-app-studio.md)
* [Erstellen einer App mithilfe von Node.js](get-started-nodejs-app-studio.md)
* [Erstellen einer App mithilfe des Yeoman-Generators](get-started-yeoman.md)
* [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)
