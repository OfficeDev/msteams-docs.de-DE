---
title: Erste Schritte – Erstellen Der ersten App-Übersicht und der voraussetzungen
author: heath-hamilton
description: Erfahren Sie, wie Sie mit der Entwicklung von Microsoft Teams-Apps beginnen und Ihre Umgebung einrichten.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: d975383022089579a04317de73595106e7920c56
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019993"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a>Erstellen Der ersten Microsoft Teams-App-Übersicht

In den **ersten Lektionen** erfahren Sie, wie Sie grundlegende Teams-Apps erstellen. In jedem Lernprogramm wird das Erstellen einer einfachen, realen Teams-App erläutert, während Sie allgemeine Tools, grundlegende Konzepte und erweiterte Features kennen lernen.

## <a name="what-youll-learn"></a>Was Sie lernen werden

Hier finden Sie eine Vorstellung davon, was Sie wissen werden, nachdem Sie die Lektionen durchgef?llt haben.

> [!div class="checklist"]
  >
  > * Starten Sie schnell mit dem **Teams Toolkit:** Das Microsoft Teams Toolkit für Visual Studio Code sorgt für die Erstellung Ihres App-Projekts und des Gerüsts, sodass Sie eine ausgeführte App in Minuten haben können.
  > * **Konfigurieren Sie Ihre App mit App Studio:** Geben Sie die Funktionen und Dienste an, die Ihre Teams-App verwendet.
  > * **Bereich der Zielgruppe Ihrer App:** Erstellen Sie eine Teams-App für den persönlichen Gebrauch, die Zusammenarbeit oder beides.
> * **Erhalten Sie Erfahrung mit Teams-Tools und SDKs:** Passen Sie Ihre App mithilfe des Teams JavaScript-Client-SDK an. Ändern Sie beispielsweise das Farbschema Ihrer App so, dass es mit dem Teams-Design übereinstimmen kann. Außerdem erfahren Sie mehr über gängige Tools zum Erstellen und Verwalten von Bots.
  > * **Erweitern Sie Ihre App:** Im Laufe der Lektionen finden Sie verwandte Themen, die Sie wahrscheinlich interessieren (z. B. Authentifizierungs- und Entwurfsrichtlinien).

## <a name="teams-app-fundamentals"></a>Grundlagen der Teams-App

Bevor Sie mit den Lernprogrammen beginnen, sollten Sie Folgendes über das Erstellen von Apps für Teams wissen.

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a>Apps können über mehrere Funktionen und Einstiegspunkte verfügen

Eine Teams-App besteht aus einer oder mehreren Plattformfunktionen [(wie](../concepts/capabilities-overview.md) Personen die App verwenden) und Einstiegspunkten [(wo](../concepts/extensibility-points.md) Personen die App verwenden).

### <a name="teams-doesnt-host-your-app"></a>Teams hosten Ihre App nicht

Eine Teams-App enthält die folgenden wichtigen Teile:

* Die Logik, datenspeicherung und API-Aufrufe, die Ihre App unterstützen. Diese Dienste werden nicht von Teams gehostet und müssen über HTTPS zugänglich sein.
* Der Teams-Client (Web, Desktop oder Mobile), auf dem Personen Ihre App verwenden.
* Ihre App-ID, mit der Sie Ihre App mit App Studio konfigurieren können.

## <a name="get-prerequisites"></a>Erforderliche Komponenten erhalten

Überprüfen Sie, ob Sie über das richtige Konto zum Erstellen von Teams-Apps verfügen und einige empfohlene Entwicklungstools installieren.

### <a name="set-up-your-development-account"></a>Einrichten Ihres Entwicklungskontos

Sie benötigen ein Teams-Konto, das das Querladen benutzerdefinierter Apps zulässt. (Ihr Konto kann dies bereits bereitstellen.)

1. Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:
    1. Wählen Sie im Teams-Client **Apps aus.**
    1. Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App.**

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, die zeigt, wo in Teams Sie eine benutzerdefinierte App hochladen können.":::
    
    Wenn die Schaltfläche nicht angezeigt wird, verfügen Sie nicht über die Berechtigung zum Hochladen benutzerdefinierter Apps in Ihrer Organisation. Sie können dieses Feature erhalten, indem Sie sich für ein kostenloses Microsoft 365-Entwicklerabonnement anmelden.

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Kostenloses Microsoft 365-Entwicklerabonnement</b></summary>

Sie können ein kostenloses Teams-Testkonto erhalten, das das Querladen von Apps ermöglicht, indem Sie am Microsoft 365-Entwicklerprogramm teilnehmen. (Der Registrierungsprozess dauert ca. zwei Minuten.)

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
1. Wählen **Sie Jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wenn Sie zum Willkommensbildschirm kommen, wählen Sie **E5-Abonnement einrichten aus.**
1. Richten Sie Ihr Administratorkonto ein. Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was Sie nach der Anmeldung für das Microsoft 365-Entwicklerprogramm sehen.":::
1. Melden Sie sich mit dem Administratorkonto, das Sie gerade eingerichtet haben, bei Teams an.
1. Überprüfen Sie, ob Sie jetzt über die **Option Benutzerdefinierte App hochladen** verfügen.

</details>

> [!Note]
> Wenn Sie Apps weiterhin nicht querladen können, lesen Sie Aktivieren von benutzerdefinierten [Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps.](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

### <a name="install-your-development-tools"></a>Installieren der Entwicklungstools

Sie können Teams-Apps mit Ihren bevorzugten Tools erstellen, aber diese Lektionen zeigen, wie Sie schnell mit dem Microsoft Teams Toolkit for Visual Studio Code beginnen können.

Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an. Um bestimmte Arten von Apps lokal zu debuggen, z. B. einen Bot, erfahren Sie, wie Sie [ngrok](../concepts/build-and-test/debug.md#locally-hosted) zum Einrichten eines sicheren Tunnels zwischen Teams und Ihrer App verwenden. (Produktionsteams-Apps werden in der Cloud gehostet.)

1. Installieren Sie [Node.js](https://nodejs.org/en/).
1. Installieren [Sie ngrok,](https://ngrok.com/download) wenn Sie eine Bot- oder Messagingerweiterung erstellen und einen [Tunnel mit ngrok erstellen.](https://docs.microsoft.com/microsoftteams/platform/tutorials/get-started-dotnet-app-studio#tunnel-using-ngrok)
1. Installieren Sie die neueste Version von [Visual Studio Code](https://code.visualstudio.com/download). (Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)
1. Wählen Visual Studio Code **auf** der linken :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: Aktivitätsleiste Erweiterungen aus, und installieren Sie **das Microsoft Teams Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Abbildung, in der Visual Studio Code die Microsoft Teams Toolkit-Erweiterung installieren können.":::

## <a name="about-the-tutorials"></a>Informationen zu den Lernprogrammen

Sie können mit einem der teams **get started-Lektionen** beginnen. Wenn Sie nicht sicher sind, wo Sie zuerst hingehen sollten, folgen Sie unserem anfängerfreundlichen Pfad und erstellen Sie ein "Hello, World!" app.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Skill tree showing learning paths for the Teams 'get started' lessons." border="false":::

## <a name="next-step"></a>Nächster Schritt

Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit der Einrichtung beginnen.

### <a name="beginner-friendly-tutorial"></a>Lernprogramm für Anfänger

> [!div class="nextstepaction"]
> [Erstellen einer "Hello, World!"-App](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a>Andere Lernprogramme

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
