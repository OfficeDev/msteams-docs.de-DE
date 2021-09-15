---
title: Erste Schritte – Erstellen Sie Ihre erste Messaging-Erweiterung
author: adrianhall
description: Erstellen Sie mithilfe des Teams Toolkits eine Messaging-Erweiterung für Microsoft Teams.
ms.author: adhal
ms.date: 05/20/2021
ms.topic: quickstart
ms.localizationpriority: none
ms.openlocfilehash: 39659b6c58b61f8b8880bd277effba1c8f9d115e
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360685"
---
# <a name="build-and-run-your-first-messaging-extension-for-microsoft-teams"></a>Erstellen Sie Ihre erste Messaging-Erweiterung für Microsoft Teams, und führen Sie sie aus.

In diesem Lernprogramm erfahren Sie, wie Sie einen *Suchbefehl* erstellen, um nach externen Daten zu suchen und die Ergebnisse in eine Nachricht einzufügen. 

Es gibt zwei Arten von Teams-**Messaging-Erweiterungen**:

- Mit [Suchbefehlen](../messaging-extensions/how-to/search-commands/define-search-command.md) können Sie externe Systeme durchsuchen und die Ergebnisse dieser Suche in Form einer Karte in eine Nachricht einfügen.
- [Aktionsbefehle](../messaging-extensions/how-to/action-commands/define-action-command.md) ermöglichen Ihnen, Ihren Benutzern ein modales Popupfenster zum Sammeln oder Anzeigen von Informationen vorzuführen, ihre Interaktion zu verarbeiten und Informationen an Teams zurückzusenden.

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

1. Wählen Sie im Abschnitt **"Funktionen auswählen"** die Option **"Nachrichtenerweiterung"** aus, deaktivieren Sie **die Option "Registerkarte",** und wählen Sie **"OK"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. Wählen Sie im Abschnitt **"Bot-Registrierung"** die Option **"Neue Bot-Registrierung erstellen"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-bot-registration.png" alt-text="Wählen Sie „Eine neue Registrierung eines Bots erstellen“ aus":::

   > [!NOTE]
   > Messaging-Erweiterungen sind auf Bots angewiesen, um ein Dialogfeld zwischen Benutzer und Code zu gewährleisten.

1. Wählen Sie im Abschnitt **"Programmiersprache"** **JavaScript** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie einen Arbeitsbereichsordner aus.  Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

   Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.  Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.

``` bash
teamsfx new
```

Die CLI führt durch einige Fragen zum Erstellen des Projekts.  Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).  Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.
1. Wählen Sie die **Nachrichtenerweiterung aus,** und deaktivieren Sie **die Registerkarte**.
1. Wählen Sie **Eine neue Registrierung eines Bots erstellen** aus.
1. Wählen Sie **JavaScript** als Programmiersprache aus.
1. Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.
1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.

   Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.

---

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).

Eine Messaging-Erweiterung verwendet das [Bot-Framework](https://docs.botframework.com), um dem Benutzer die Interaktion mit Ihrem Dienst über eine Unterhaltung zu ermöglichen.  Nach der Gerüsterstellung wird Ihr Projekt folgend aussehen:

:::image type="content" source="../assets/images/teams-toolkit-v2/msgextn-file-layout.png" alt-text="Dateilayout eines Bot-Projekts.":::

Der Bot-Code wird im `bot` Verzeichnis gespeichert.  Das `bot/messageExtensionBot.js` ist der Haupteinsteigerpunkt der Messaging-Erweiterung.

> [!Tip]
> Machen Sie sich mit Bots außerhalb von Teams vertraut, bevor Sie Ihren ersten Bot in Teams integrieren.  Sie können weitere Informationen zu Bots im Lernprogramme von [Azure Bot Service](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true) finden.

## <a name="run-your-app-locally"></a>Lokales Ausführen Ihrer App

Das Teams-Toolkit ermöglicht es Ihnen, Ihre App lokal zu hosten.  Gehen Sie hierfür folgendermaßen vor:

- Eine Azure Active Directory-Anwendung ist im M365-Mandanten registriert.
- Ein App-Manifest wurde dem Entwicklerportal für Teams übermittelt.
- Eine API wird mittels des Azure Functions Core Tools ausgeführt, um Ihre App zu unterstützen.
- [ngrok](https://ngrok.io) ist installiert und dazu verwendet, eine Tunnel zwischen Teams und Ihrer Messaging-Erweiterung bereitzustellen.

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie Visual Studio Code die **F5-Taste,** um die Anwendung im Debugmodus auszuführen.

   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.  Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.  Diese Änderung kann 3-5 Minuten dauern.

1. Teams wird in einem Webbrowser geladen, und Sie werden dazu aufgefordert, sich anzumelden. Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben. Melden Sie sich mit Ihrem M365-Konto an.

1. Wählen Sie **"Hinzufügen"** aus, um die App Ihrem Konto hinzuzufügen.

   Nachdem die App geladen wurde, können Sie versuchen, die Beispielfunktion zu verwenden: Sie können die Nachrichtenerweiterung aus drei Punkten im Verfassenbereich starten und npm-Pakete über die Suchleiste durchsuchen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/search-message-extension.png" alt-text="Suchbasierte Messaging-Erweiterung in Aktion":::
   
   Sie können auch versuchen, Ihre Nachrichtenerweiterungsinstanz über die Suchleiste in der obersten Zeile von Teams zu @ @ senden und nach npm-Paket zu suchen.
    :::image type="content" source="../assets/images/teams-toolkit-v2/msgext-teams-search-bar.png" alt-text="Suchbasierte Messaging-Erweiterung in Aktion":::

   Geben Sie Text in das Suchfeld ein, und wählen Sie dann eine der Optionen aus. Sie können adaptive Karten der Suchergebnisse erstellen und senden.
    :::image type="content" source="../assets/images/teams-toolkit-v2/msgext-adptive-card.png" alt-text="Suchbasierte Messaging-Erweiterung in Aktion":::

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App lokal im Debugger ausführen.</summary>

Wenn Sie die **F5-Taste** drücken, wird das Teams Toolkit:

1. Registriert Ihre Anwendung bei Azure Active Directory.
1. Registriert Ihre Anwendung für das "Querladen" in Microsoft Teams.
1. Startet ihr Anwendungs-Back-End, das lokal mithilfe von [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start)ausgeführt wird.
1. Startet einen ngrok-Tunnel, damit Teams mit Ihrer App kommunizieren können.
1. Startet Microsoft Teams mit einem Befehl, um Teams anzuweisen, die Anwendung querzuladen.

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary>Erfahren Sie, wie Sie häufige Probleme bei dem lokalen Ausführen Ihrer App lösen können.</summary>

Um Ihre App in Teams erfolgreich auszuführen, müssen Sie ein Microsoft 365-Entwicklungskonto haben, das das Querladen von Apps ermöglicht. Weitere Informationen zum Öffnen von Apps finden Sie unter [Erforderliche Komponenten](prerequisites.md#enable-sideloading).

> [!TIP]
> Überprüfen Sie mithilfe des [Tools für die App-Überprüfung](https://dev.teams.microsoft.com/appvalidation.html), das im Toolkit enthalten ist, ob es Probleme gibt, bevor Sie ihre App querladen. Beheben Sie die Probleme, um die App erfolgreich querzuladen.
</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->

<details>
<summary>Erfahren Sie, was geschieht, wenn Sie Ihre App in Azure bereitstellen</summary>

Vor der Bereitstellung wurde die Anwendung lokal ausgeführt:

1. Das Back-End unter Verwendung von _Azure Functions Core Tools_ ausgeführt.
1. Der HTTP-Endpunkt der Anwendung, an dem Microsoft Teams die Anwendung lädt, wird lokal ausgeführt.

Die Bereitstellung umfasst das Bereitstellen von Ressourcen für ein aktives Azure-Abonnement und das Bereitstellen (Hochladen) des Back-End- und des Frontend-Codes für die Anwendung in Azure. Das Back-End verwendet eine Vielzahl von Azure-Diensten, einschließlich Azure App Service und Azure Bot Service.

</details>

## <a name="add-a-configuration-page-to-your-messaging-extension"></a>Hinzufügen einer Konfigurationsseite zu Ihrer Messaging-Erweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="code-sample"></a>Codebeispiel

Die Teams Search Auth Config for sample projects on GitHub, demonstrate how to create messaging extensions that include a configuration page and [Bot Service authentication.](https://github.com/microsoft/BotBuilder-Samples#teams-samples) Die Beispiele zeigen auch, wie Sie Nachrichtenerweiterungen erstellen, die Suchanforderungen akzeptieren und die Ergebnisse zurückgeben, nachdem sich der Benutzer angemeldet hat.

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|-----------------|-----------------|-------------|--------------|--------|
| Bot-Generator | So erstellen Sie Messaging-Erweiterungen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config) | [View]( https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |

## <a name="additional-code-sample"></a>Zusätzliches Codebeispiel

> [!div class="nextstepaction"]
> [Weitere Bot Framework-Beispiele auf GitHub anzeigen](https://github.com/OfficeDev/microsoft-teams-samples#messaging-extensions-samples-using-the-v4-sdk)

## <a name="see-also"></a>Siehe auch

* [Übersicht über Lernprogramme](code-samples.md) 
* [Erstellen einer App mit React](first-app-react.md)
* [Erstellen einer App mitHilfe von Blatter](first-app-blazor.md)
* [Erstellen einer App mit SPFx](first-app-spfx.md)
* [Erstellen einer App mithilfe von C# oder .NET](get-started-dotnet-app-studio.md)
* [Erstellen einer App mithilfe von Node.js](get-started-nodejs-app-studio.md)
* [Erstellen einer App mithilfe des Yeoman-Generators](get-started-yeoman.md)
* [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)
