---
title: Erste Schritte – Erstellen und Ausführen Ihrer ersten App
author: girliemac
description: Erstellen Sie schnell Microsoft Teams App, die ein "Hello, World!" anzeigt. message using the Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2021
ms.topic: quickstart
ms.openlocfilehash: 6c3d215a3f2c1aa89a9a2bf28aad081d98c6dc33
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101723"
---
# <a name="create-your-first-microsoft-teams-app"></a>Erstellen Ihrer ersten Microsoft Teams App

Dieser Schnellstart vermittelt Ihnen das Erstellen und Ausführen Microsoft Teams App, die "Hello, World!" anzeigt.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie beginnen, müssen Sie Ihren mandanten [Teams einrichten](#set-up-your-teams-development-tenant) und ihre Teams [installieren.](#install-your-development-tools)

### <a name="set-up-your-teams-development-tenant"></a>Einrichten ihres Teams-Entwicklungs-Mandanten

Ein **Mandant** ist wie ein Container für eine Organisation. In Teams ist ein Mandant der Ort, an dem Personen aus dieser Organisation chatten, Dateien freigeben und Besprechungen ausführen. Als Entwickler benötigen Sie einen Mandanten zum Querladen und Testen der Teams, die Sie erstellen.  

# <a name="do-not-have-a-tenant"></a>[Kein Mandant](#tab/do-not-have-a-tenant)

Sie können ein kostenloses Teams, das einen Mandanten enthält, der das Querladen von Apps zulässt, indem Sie am Microsoft 365 teilnehmen. Der Registrierungsprozess dauert ca. zwei Minuten.

**So erhalten Sie einen Mandanten**

1. Wechseln Sie zum [Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
1. Wählen **Sie Jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wählen Sie auf dem Bildschirm Willkommen die Option **E5-Abonnement einrichten aus.**
1. Richten Sie Ihr Microsoft 365 Entwicklerkonto ein. 
   Nachdem Sie fertig sind, wird der folgende Bildschirm angezeigt:

   :::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was Sie nach der Anmeldung für das Microsoft 365 sehen.":::

1. Melden Sie sich bei Teams mit Ihrem neuen Konto an.
1. Wählen Sie im Teams Die Option **Apps aus.**
1. Stellen Sie sicher, dass die **Option Hochladen app angezeigt** wird. Wenn Sie dies tun, bedeutet dies, dass Sie Apps querladen können.

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, in der Teams sie eine benutzerdefinierte App hochladen können.":::

# <a name="have-a-tenant"></a>[Verfügen über einen Mandanten](#tab/have-a-tenant)

Wenn Sie bereits über einen Mandanten verfügen, überprüfen Sie, ob Sie Apps in einem Teams.

**Überprüfen, ob Sie Ihre Apps querladen können** 

1. Wählen Sie im Teams Client die Option **Apps aus.** 
1.  Stellen Sie sicher, dass die **Option Hochladen app angezeigt** wird. Wenn Sie dies tun, bedeutet dies, dass Sie Apps querladen können. 

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, in der Teams sie eine benutzerdefinierte App hochladen können.":::

---

### <a name="install-your-development-tools"></a>Installieren der Entwicklungstools

Zum Erstellen dieser App verwenden Sie das Teams Toolkit für Visual Studio Code, um schnell zu beginnen. Sie können auch Teams apps mit einem ihrer vordefinierten Tools erstellen. 

> [!NOTE]
> Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an. Um bestimmte Arten von Apps lokal zu debuggen, z. B. einen Bot, erfahren Sie, wie Sie ngrok zum Einrichten eines sicheren Tunnels zwischen Teams und Ihrer App verwenden.
> 
> Produktions Teams apps werden in der Cloud gehostet.

**So installieren Sie Microsoft Teams Tools**

1. Installieren Sie [Node.js](https://nodejs.org/en/).
1. Wenn Sie planen, einen Bot oder eine Messagingerweiterung zu erstellen, installieren Sie [ngrok](https://ngrok.com/download) und stellen Sie Ihren localhost mithilfe von [ngrok für](../tutorials/get-started-dotnet-app-studio.md#tunnel-using-ngrok)das Internet zur Verfügung.
1. Installieren Sie die neueste Version [von Visual Studio Code](https://code.visualstudio.com/download). 
   
   > [!NOTE]
   > Das Toolkit unterstützt frühere Versionen von Visual Studio Code.

1. Wählen Sie in der linken Aktivitätsleiste **Erweiterungen aus.** :::image type="icon" source="../assets/icons/vs-code-extensions.png":::
1. Wählen **Microsoft Teams Toolkit** installieren **aus.**

   :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Abbildung, die zeigt, Visual Studio Code Sie die Erweiterung Microsoft Teams Toolkit installieren können.":::

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

1. Öffnen Sie Visual Studio Code.
1. Wählen **Microsoft Teams Toolkit** Erstellen einer neuen Teams App :::image type="icon" source="../assets/icons/vsc-toolkit.png":::  >  **aus.**

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-02.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams erstellen.":::
   
1. Melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an. Entweder das konto, das Sie gerade erstellt haben, oder das Konto, das das Querladen von Apps ermöglicht.
1. Wechseln Sie **auf dem Bildschirm** Projekt auswählen zu Persönliche **App,** und wählen **Sie JS** (JavaScript) > **Weiter aus.**

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-03.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams konfigurieren.":::

1. Geben Sie einen Namen für Ihre Teams ein.

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-04.png" alt-text="Screenshot zum Hinzufügen eines Namens zu Ihrem App-Projekt mit dem Visual Studio Code Teams Toolkit.":::

1. Klicken Sie auf **Fertigstellen**. 
   Ihr Projekt ist jetzt konfiguriert. 

## <a name="2-understand-your-app-project-components"></a>2. Verstehen Ihrer App-Projektkomponenten

Nachdem das Toolkit Ihr App-Projekt konfiguriert hat, verfügen Sie über die Komponenten, um Ihre "Hello, World!" zu erstellen. Teams App. Die Verzeichnisse und Dateien des Projekts befinden sich im Visual Studio Code Explorer. 

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-05.png" alt-text="Screenshot des Gerüsts in Ihrem App-Projekt mit dem Visual Studio Code Teams Toolkit.":::

Das Toolkit erstellt automatisch ein App-Gerüst im Verzeichnis basierend auf den `src` Funktionen, die Sie während des Setups hinzugefügt haben. Da Sie während des Setups eine Registerkarte erstellt haben, übernimmt die Datei im Verzeichnis die `App.js` `src/components` Initialisierung und das Routing Ihrer App. Die Datei ruft außerdem das Microsoft Teams JavaScript-Client-SDK auf, um die Kommunikation zwischen Ihrer App und ihrem Teams. 

## <a name="3-build-and-run-your-app"></a>3. Erstellen und Ausführen Ihrer App

Erstellen und ausführen Sie Ihre App lokal, um Zeit zu sparen. 

**So erstellen und ausführen Sie Ihre App**

1. Wählen Visual Studio Code **Terminal**  >  **anzeigen aus.**
1. Führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.
  
  A **Compiled successfully!** wird im Terminal angezeigt. Ihre App wird jetzt auf Ihrem localhost unter `https://localhost:3000` ausgeführt. 

## <a name="4-sideload-your-app-in-teams"></a>4. Querladen Ihrer App in Teams

Querladen ist der Vorgang der Installation einer App in Teams, die nicht von Ihrem Administrator oder Von Microsoft genehmigt wurde. Das Querladen ist häufig beim Testen und Debuggen Teams Apps.

Standardmäßig ist Teams das Querladen von Apps nicht zulässig. Sie können diese Einstellung im Teams ändern.

**So aktivieren Sie das Querladen von Apps in Teams**

1. Melden Sie sich beim [Microsoft 365 Admin Center mit](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Ihren Administratoranmeldeinformationen an.  
1. Wählen **Sie Alle Teams**  >  aus. 

   ![Abbildung des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

   > [!Note] 
   > Es kann bis zu 24 Stunden dauern, bis **die Teams** angezeigt wird. 

1. Wechseln Sie **zu Teams**  >  **Setuprichtlinien**  >  **für Apps global** (Organisationsweite Standardeinstellung).

   ![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

1. Aktivieren Sie das **Umschalten benutzerdefinierter Apps** hochladen.

1. Wählen **Sie Speichern** aus, um die Änderungen zu speichern.

   Ihr Test-Mandant ermöglicht jetzt das Querladen benutzerdefinierter Apps.

   > [!Note]
   > Suchen Sie nach Problemen, bevor Sie Ihre App mit dem Validierungsfeature in App Studio querladen, das im Toolkit enthalten ist. Beheben Sie die Fehler, um die App erfolgreich querladen zu können.


### <a name="sideload-your-app"></a>Querladen Ihrer App

1. Öffnen Visual Studio Code sie das Teams Toolkit.
1. Wechseln Sie zu **App Studio**.  
1. Wählen **Sie Test and Distribute** Install  >  **aus.**

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-appstudio.png" alt-text="Screenshot, der zeigt, wie Sie Ihre App mit dem Teams Visual Studio Code Teams-Toolkit querladen.":::

**Alternativ**

1. Wählen Sie **die F5-Taste** aus, um das zu installierende Browserfenster zu öffnen. Dadurch wird der Installationsprozess im **App Studio** übersprungen und Teams Browser angezeigt.
1. Wählen Sie im Installationsdialogfeld **Hinzufügen** aus, um Ihre App zu installieren, Teams.

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install.png" alt-text="Screenshot, der zeigt, wie Sie Ihre App querladen, um Teams zu laden.":::

   > [!Note]
   > App Studio ist auch als eigenständige App für Teams verfügbar.

### <a name="troubleshoot-sideloading-issues"></a>Behandeln von Problemen beim Querladen

**Installation fehlgeschlagen**

Wenn die Fehlermeldung während der Installation Ihrer App angezeigt wird, stellen Sie sicher, dass `Manifest parsing has failed` die App-Informationen richtig eingegeben wurden.

**So überprüfen Sie die App-Informationen**

* Wechseln Sie Teams Toolkit zu **App Studio** App Details, und überprüfen Sie, ob alle erforderlichen  >   Informationen korrekt eingegeben wurden.
*  Wenn Sie die Datei manuell bearbeitet haben, stellen Sie sicher, dass das `manifest.json` JSON im **App-Manifest-Tool** in App Studio definiert ist.

**Tabulatorinhalt wird nicht angezeigt**

Vergewissern Sie sich, dass Ihre App ausgeführt wird. Wenn nicht, wechseln Sie zum Terminal, und führen Sie `npm start` aus.

## <a name="see-also"></a>Siehe auch

* [Vorbereiten Ihres Microsoft 365-Mandanten](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant)
* [Auswählen eines Setups zum Testen und Debuggen ihrer Microsoft Teams App](../concepts/build-and-test/debug.md)
* [Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md)
* [Vorbereiten der AppSource-Übermittlung](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Entwickeln Sie schnell Apps mit App Studio für Microsoft Teams](../concepts/build-and-test/app-studio-overview.md)
* [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte für Microsoft Teams](../build-your-first-app/build-personal-tab.md)
