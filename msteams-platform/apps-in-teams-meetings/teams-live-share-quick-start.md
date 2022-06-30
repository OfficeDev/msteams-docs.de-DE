---
title: Live Share Schnellstart
description: In diesem Modul erfahren Sie, wie Sie das Dice Roller-Beispiel schnell ausprobieren können.
ms.topic: concept
ms.localizationpriority: high
ms.author: stevenic
ms.openlocfilehash: 98150265f0c5876e726710cacc873db2ac23e9ee
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66484586"
---
---

# <a name="quick-start-guide"></a>Schnellstarthandbuch

Der Einstieg in das Live Share SDK mit dem Dice Roller-Beispiel ist eine Weiterentwicklung des [Fluid Framework Quick Start](https://fluidframework.com/docs/start/quick-start/) und wurde entwickelt, um schnell ein auf dem Live Share SDK basierendes [Dice Roller-Beispiel](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller) auf dem lokalen Host Ihres Computers auszuführen.

:::image type="content" source="../assets/images/teams-live-share/dice-roller.png" alt-text="DiceRoller-Beispiel":::

> [!NOTE]
> Dieser Leitfaden führt Sie durch die lokale Verwendung von Live Share in einem Browser. Weitere Informationen zur Verwendung des SDK in einer Teams-Besprechung finden Sie in unserem [Agile Poker-Tutorial](../sbs-teams-live-share.yml).

## <a name="set-up-your-development-environment"></a>Einrichten der Entwicklungsumgebung

Installieren Sie zunächst Folgendes:

* [Node.js](https://nodejs.org/en/download): Das Live Share SDK unterstützt Node.js LTS-Versionen 12.17 und höher.
* [Neueste Version von Visual Studio Code](https://code.visualstudio.com/).
* [Git](https://git-scm.com/downloads)

## <a name="build-and-run-the-dice-roller-app"></a>Erstellen und Ausführen der Dice Roller-App

1. Wechseln Sie zur Beispielanwendung [Dice Roller](https://github.com/microsoft/live-share-sdk/tree/main/samples/01.dice-roller).

1. Klonen Sie das [Live Share SDK-Repository](https://github.com/microsoft/live-share-sdk), um die Beispiel-App zu testen:

    ```bash
    $ git clone https://github.com/microsoft/live-share-sdk.git
    ```

1. Führen Sie den folgenden Befehl aus, um zum Ordner der Dice Roller-Beispielanwendung zu wechseln:

   ```bash
    $ cd live-share-sdk\samples\01.dice-roller
   ```

1. Führen Sie den folgenden Befehl aus, um das Abhängigkeitspaket zu installieren:

    ```bash
    $ npm install
    ```

1. Führen Sie den folgenden Befehl aus, um den Client und den lokalen Server zu starten:

   ```bash
   $ npm start
   ```
  
     Eine neue Browserregisterkarte öffnet eine `http://localhost:8080` URL, und das Dice Roller-Spiel wird angezeigt.

1. Kopieren Sie die vollständige URL im Browser, einschließlich der ID, und fügen Sie die URL in ein neues Fenster oder einen anderen Browser ein.

   Ein zweiter Client für Ihre Dice Roller-Anwendung wird geöffnet.

1. Öffnen Sie beide Fenster und wählen Sie in einem Fenster die Schaltfläche **Rollen** aus. Der Status der Würfel ändert sich auf beiden Clients.

    :::image type="content" source="../assets/images/teams-live-share/dice-roller.png" alt-text="Dice Roller mit mehreren Registerkarten":::
  
   **Herzlichen Glückwunsch**, Sie haben gelernt, wie Sie eine App mit dem Live Share SDK erstellen und ausführen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Dice Roller-Tutorial](teams-live-share-tutorial.md)

## <a name="see-also"></a>Siehe auch

* [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
* [Live Share-Funktionen](teams-live-share-capabilities.md)
* [Häufig gestellte Fragen zu Live Share](teams-live-share-faq.md)
* [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
