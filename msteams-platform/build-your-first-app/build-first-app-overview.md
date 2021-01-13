---
title: Erste Schritte – Erstellen der ersten App-Übersicht und voraussetzungen
author: heath-hamilton
description: Erfahren Sie, wie Sie mit der Entwicklung von Microsoft Teams-Apps beginnen und Ihre Umgebung einrichten.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 4288efdbfada5f1a51fa1d4aeccdd6cdf9c64382
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797897"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a>Erstellen Einer Übersicht über Ihre erste Microsoft Teams-App

In den **ersten Lektionen** erfahren Sie, wie Sie grundlegende Teams-Apps erstellen. Jedes Lernprogramm führt Sie durch das Erstellen einer einfachen, realen Teams-App und führt Sie gleichzeitig mit gängigen Tools, grundlegenden Konzepten und erweiterten Features ein.

## <a name="what-youll-learn"></a>Was Sie lernen werden

Hier sehen Sie eine Vorstellung davon, was Sie wissen werden, nachdem Sie die Lektionen durchgef llt.

> [!div class="checklist"]
  >
  > * Starten Sie schnell mit dem **Teams Toolkit:** Das Microsoft Teams Toolkit für Visual Studio Code übernimmt die Erstellung Ihres App-Projekts und -Gerüsts, damit Sie eine ausgeführte App in Minuten haben können.
  > * **Konfigurieren Sie Ihre App mit App Studio:** Geben Sie die Funktionen und Dienste an, die Ihre Teams-App verwendet.
  > * **Umfang der Zielgruppe Ihrer App:** Erstellen Sie eine Teams-App für die persönliche Verwendung, Zusammenarbeit oder beides.
> * **Erfahren Sie mehr über Teams-Tools und SDKs:** Passen Sie Ihre App mithilfe des JavaScript-Client-SDK für Teams an. Ändern Sie z. B. das Farbschema Ihrer App so, dass es dem Design "Teams" zu entsprechen. Erfahren Sie außerdem mehr über allgemeine Tools zum Erstellen und Verwalten von Bots.
  > * **Erweitern Sie Ihre App:** Im Laufe der Lektionen finden Sie verwandte Themen, an denen Sie wahrscheinlich interessiert sind (z. B. Authentifizierungs- und Entwurfsrichtlinien).

## <a name="teams-app-fundamentals"></a>Grundlagen der Teams-App

Bevor Sie mit den Lernprogrammen beginnen, sollten Sie Folgendes zum Erstellen von Apps für Teams wissen.

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a>Apps können über mehrere Funktionen und Einstiegspunkte verfügen

Eine Teams-App besteht aus einer oder mehreren Plattformfunktionen [(wie](../concepts/capabilities-overview.md) Personen die App verwenden) und Einstiegspunkten [(wo](../concepts/extensibility-points.md) Personen die App verwenden).

### <a name="teams-doesnt-host-your-app"></a>Teams hosten Ihre App nicht

Eine Teams-App enthält die folgenden wichtigen Teile:

* Die Logik, Datenspeicherung und API-Aufrufe, die Ihre App unterstützen. Diese Dienste werden nicht von Teams gehostet und müssen über HTTPS zugänglich sein.
* Der Teams-Client (Web, Desktop oder Mobil), auf dem Personen Ihre App verwenden.
* Ihre App-ID, mit der Sie Ihre App mit App Studio konfigurieren können.

## <a name="get-prerequisites"></a>Voraussetzungen erhalten

Stellen Sie sicher, dass Sie über das richtige Konto zum Erstellen von Teams-Apps verfügen, und installieren Sie einige empfohlene Entwicklungstools.

### <a name="set-up-your-development-account"></a>Einrichten Ihres Entwicklungskontos

Sie benötigen ein Teams-Konto, das das Querladen benutzerdefinierter Apps ermöglicht. (Ihr Konto stellt dies möglicherweise bereits zur Verfügung.)

1. Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:
    1. Wählen Sie im Teams-Client **Apps aus.**
    1. Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App.**

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, die zeigt, wo Sie in Teams eine benutzerdefinierte App hochladen können.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Wählen Sie hier</b> aus, wenn die Option zum Querladen nicht angezeigt wird oder sie kein Konto für Teams hat.</summary>

Sie können ein kostenloses Teams-Testkonto erhalten, das das Querladen von Apps ermöglicht, indem Sie am Microsoft 365-Entwicklerprogramm teilnehmen. (Der Registrierungsprozess dauert ca. zwei Minuten.)

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm.](https://developer.microsoft.com/microsoft-365/dev-program)
1. Wählen Sie **"Jetzt beitreten"** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wenn Sie zum Willkommensbildschirm kommen, wählen **Sie "E5-Abonnement einrichten" aus.**
1. Richten Sie Ihr Administratorkonto ein. Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was nach der Anmeldung für das Microsoft 365-Entwicklerprogramm zu sehen ist.":::
1. Melden Sie sich mit dem Administratorkonto, das Sie gerade eingerichtet haben, bei Teams an.
1. Überprüfen Sie, ob Sie jetzt über die **Option zum Hochladen einer benutzerdefinierten App** verfügen.

</details>

> [!Note]
> Wenn Sie Apps weiterhin nicht querladen können, lesen Sie die Informationen zum Aktivieren von benutzerdefinierten Teams-Apps, und aktivieren Sie das Hochladen [benutzerdefinierter Apps.](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

### <a name="install-your-development-tools"></a>Installieren der Entwicklungstools

Sie können Teams-Apps mit Ihren bevorzugten Tools erstellen, aber diese Lektionen zeigen, wie Sie schnell mit dem Microsoft Teams Toolkit for Visual Studio Code beginnen können.

Teams zeigt den Inhalt von Apps nur über HTTPS-Verbindungen an. Um bestimmte Arten von Apps lokal zu debuggen, z. B. einen Bot, erfahren Sie, wie Sie [ngrok](../concepts/build-and-test/debug.md#locally-hosted) zum Einrichten eines sicheren Tunnels zwischen Teams und Ihrer App verwenden. (Produktions-Teams-Apps werden in der Cloud gehostet.)

1. Installieren Sie [Node.js](https://nodejs.org/en/).
1. Installieren [Sie ngrok,](https://ngrok.com/download) wenn Sie planen, einen Bot oder eine Messagingerweiterung zu erstellen.
1. Installieren Sie die neueste Version von [Visual Studio Code](https://code.visualstudio.com/download). (Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)
1. Wählen Visual Studio Code auf  der linken Aktivitätsleiste Erweiterungen :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: aus, und installieren Sie **das Microsoft Teams Toolkit.**

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Illustration showing where in Visual Studio Code you can install the Microsoft Teams Toolkit extension.":::

## <a name="about-the-tutorials"></a>Informationen zu den Lernprogrammen

Sie können mit jeder der Ersten **Schritte** in Teams beginnen. Wenn Sie nicht sicher sind, wo Sie zuerst hingehen sollten, folgen Sie unserem anfängerfreundlichen Pfad, und erstellen Sie ein "Hello, World!" app.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Fertigkeitenstruktur, die Lernpfade für die Teams &quot;Erste Schritte&quot; zeigt." border="false":::

## <a name="next-step"></a>Nächster Schritt

Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit der Einrichtung beginnen.

### <a name="beginner-friendly-tutorial"></a>Lernprogramm für Anfänger

> [!div class="nextstepaction"]
> [Erstellen einer "Hello, World!"-App](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a>Weitere Lernprogramme

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
