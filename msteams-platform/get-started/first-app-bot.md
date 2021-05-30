---
title: Erste Schritte – Erstellen Sie Ihren ersten Unterhaltungs-Bot
author: adrianhall
description: Erstellen Sie mithilfe des Teams-Toolkits einen Unterhaltungs-Bot für Microsoft Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.openlocfilehash: 3084020000cf53fbb33ffc25d141b41ffff83160
ms.sourcegitcommit: 2c8b35899dd845acd66f1f927e40d99523c29a91
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "52697977"
---
# <a name="build-your-first-conversational-bot-for-microsoft-teams"></a>Erstellen Sie Ihren ersten Unterhaltungs-Bot für Microsoft Teams

Ein Bot agiert als Vermittler zwischen einem Teams-Benutzer und einem Webdienst.  Benutzer können mit einem Bot chatten, um schnell Informationen zu erhalten, Workflows zu initiieren, oder für alles andere, was Ihr Webservice tun kann.  In diesem Lernprogramm erfahren Sie, wie Sie eine Teams-Bot-App erstellen, ausführen und bereitstellen.

## <a name="before-you-begin"></a>Bevor Sie beginnen

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten](prerequisites.md) installieren.

> [!div class="nextstepaction"]
> [Installieren erforderlicher Komponenten](prerequisites.md)

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie das Teams-Toolkit zum Erstellen Ihres ersten Projekts:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Öffnen Sie das Teams-Toolkit, indem Sie das Teams-Symbol in der Randleiste auswählen:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Wählen Sie **Erstellen eines neuen Projekts** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Teams-Toolkits.":::

1. Wählen Sie **Eine neue Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Start des Assistenten für „Neues Projekt erstellen“":::

1. Wählen Sie im Schritt **Funktionen auswählen** die Option **Bot** aus, und heben Sie die Auswahl **Registerkarte** auf. Drücken Sie **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities-bot.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden.":::

1. Wählen Sie im Schritt **Bot -Registrierung** die Option **Eine neue Bot-Registrierung erstellen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Bot-Registrierung erstellen“ aus":::

1. Wählen Sie im Schritt **Programmiersprache** die Option **JavaScript** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie einen Arbeitsbereichsordner aus.  Innerhalb Ihres Arbeitsbereichsordners wird für das Projekt, das Sie erstellen, ein Ordner erstellt.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

Ihre Teams-App wird innerhalb weniger Sekunden erstellt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie das `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.  Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.

``` bash
teamsfx new
```

Das CLI führt durch einige Fragen zum Erstellen des Projekts hindurch.  Bei jeder Frage wird angegeben, wie Sie diese beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).  Wenn Sie die Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.

1. Wählen Sie **Eine neue Teams-App erstellen** aus.
1. Wählen Sie die Funktion **Bot** aus, und heben Sie die Auswahl der Funktion **Registerkarte** auf.
1. Wählen Sie **Eine neue Bot-Registrierung erstellen** aus.
1. Wählen Sie **JavaScript** als Programmiersprache aus.
1. Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.
1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.

Sobald alle Fragen beantwortet sind, wird Ihr Projekt erstellt.

---

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).

Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.  Nach der Gerüsterstellung wird Ihr Projekt wie folgt aussehen:

:::image type="content" source="../assets/images/teams-toolkit-v2/bot-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

Der Bot-Code wird im `bot`-Verzeichnis gespeichert.  Das `bots/teamsBot.js` ist der Haupteinstiegspunkt für den Bot, und die Dialoge werden im `dialogs`-Verzeichnis gespeichert.

> [!Tip]
> Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.  Sie können weitere Informationen zu Bots in Lernprogrammen von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.

## <a name="run-your-app-locally"></a>Lokales Ausführen Ihrer App

Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.  Gehen Sie hierfür folgendermaßen vor:

- Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.
- Ein App-Manifest wird dem Entwickler-Center für Teams übermittelt.
- Eine API wird mittels der Azure Functions Core Tools lokal ausgeführt, um Ihre App zu unterstützen.
- [ngrok](https://ngrok.io) ist installiert und wird dazu verwendet, einen Tunnel zwischen Teams und Ihrem Bot-Code bereitzustellen.

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debug-Modus ausführen.

   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen, und die App wird erstellt.  Wenn das Erstellen abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.  Dies kann 3–5 Minuten in Anspruch nehmen.

1. Ihr Webbrowser wird gestartet, um die Anwendung auszuführen. Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben. Wenn Sie aufgefordert werden, wählen Sie **Stattdessen die Web-App verwenden** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot zeigt, wie die Web-Version von Teams beim Start ausgewählt wird":::

1. Möglicherweise werden Sie aufgefordert, sich anzumelden.  Wenn ja, melden Sie sich mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App in Teams zu installieren, drücken Sie **Hinzufügen**.

Sobald die App geladen ist, werden Sie direkt zu einer Chat-Sitzung mit dem Bot geführt.  Sie können `intro` eingeben, um einen Einführungskarte anzuzeigen, und `show`, um Ihre Details von Microsoft Graph anzuzeigen.  (Dies benötigt eine zusätzliche Berechtigungsgenehmigung).

Das Debuggen funktioniert so, wie Sie es normalerweise erwarten – probieren Sie es selbst aus! Öffnen Sie die Datei `bot/dialogs/rootDialog.js`, und suchen Sie die `triggerCommand(...)`-Methode.  Setzen Sie einen Haltepunkt auf dem Standardvorgang.  Geben Sie dann einigen Text ein.

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</summary>

Wenn Sie F5 gedrückt haben, hat das Teams Toolkit:

1. Ihre Anwendung bei Azure Active Directory registriert.
1. Ihre Anwendung bei Microsoft Teams für das „Querladen“ registriert.
1. Ihr Anwendungs-Back-End mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start) lokal gestartet.
1. Einen „ngrok“-Tunnel gestartet, sodass Teams mit Ihrer App kommunizieren kann.
1. Microsoft Teams mit einem Befehl gestartet, mit dem Teams angewiesen wird, die Anwendung querzuladen.

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</summary>

Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, welches das Querladen von Apps ermöglicht. Weitere Informationen zum Öffnen eines Kontos finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).

> [!TIP]
> Überprüfen Sie vor dem Querladen Ihrer App mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt. Beheben Sie die Probleme, um die App erfolgreich querzuladen.
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</summary>

Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:

1. Das Back-End wird mithilfe von _Azure Functions Core Tools_ ausgeführt.
1. Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.

Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure. Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.

</details>

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen Methoden zum Erstellen von Teams-Apps:

- [Erstellen einer Teams-App mit React](first-app-react.md)
- [Erstellen einer Teams-App mit Blazor](first-app-blazor.md)
- [Erstellen einer Teams-App als ein SharePoint-Webpart](first-app-spfx.md) (Azure nicht erforderlich)
- [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
