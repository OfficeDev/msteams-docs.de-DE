---
title: Erste Schritte – Erstellen Ihrer ersten App-Übersicht und Voraussetzungen
author: heath-hamilton
description: Erfahren Sie, wie Sie mit der Microsoft Teams-App-Entwicklung beginnen und Ihre Umgebung einrichten.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 7fc3f7e9fd9d3c2a028999be53ba6bdcd5b3ba72
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931792"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a>Erstellen Ihrer ersten Microsoft Teams-App-Übersicht

In den **ersten App** -Lektionen erstellen Sie grundlegende Teams-apps. In jedem Lernprogramm wird erläutert, wie Sie eine einfache Real-World-Teams-app erstellen, während Sie allgemeine Tools, grundlegende Konzepte und erweiterte Funktionen einführen.

## <a name="what-youll-learn"></a>Was Sie lernen

Hier ist eine Vorstellung davon, was Sie wissen, nachdem Sie die Lektionen durchlaufen haben.

> [!div class="checklist"]
  >
  > * Mit dem Microsoft Teams Toolkit für Visual Studio Code können Sie **schnell mit dem Team-Toolkit in Kontakt** treten, um ein App-Projekt und ein Gerüst zu erstellen, damit Sie in wenigen Minuten eine laufende APP haben.
  > * **Konfigurieren Ihrer APP mit App Studio** : Geben Sie die Funktionen und Dienste an, die ihre Teams-App verwendet.
  > * **Bereich der Benutzergruppe Ihrer APP** : Erstellen einer Teams-App für den persönlichen Gebrauch, die Zusammenarbeit oder beides.
  > * **Erfahren Sie mehr über Microsoft Teams-Tools und SDKs** : passen Sie Ihre APP an (ändern Sie beispielsweise Ihr Farbschema so, dass Sie mit dem Microsoft Teams-Design übereinstimmt), und helfen Sie dem Microsoft Teams-JavaScript-SDK. Außerdem finden Sie Informationen zu allgemeinen Tools zum Erstellen und Verwalten von Bots.
  > * **Erweitern Sie Ihre APP** : in den Lektionen finden Sie Verwandte Themen, die Sie wahrscheinlich interessieren (beispielsweise Authentifizierungs-und Entwurfsrichtlinien).

## <a name="teams-app-fundamentals"></a>Grundlagen der Microsoft Teams-App

Bevor Sie mit den Lernprogrammen beginnen, sollten Sie die folgenden Informationen zum Erstellen von Apps für Microsoft Teams kennen.

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a>Apps können über mehrere Funktionen und Einstiegspunkte verfügen.

Eine Teams-App besteht aus einer oder mehreren [Plattformfunktionen](../concepts/capabilities-overview.md) (wie die Benutzer die APP verwenden) und [Einstiegspunkten](../concepts/extensibility-points.md) (bei denen Personen die APP entdecken).

### <a name="teams-doesnt-host-your-app"></a>Ihre APP wird von Microsoft Teams nicht gehostet.

Eine Teams-App umfasst die folgenden wichtigen Teile:

* Die Logik, Datenspeicherung und API-Aufrufe, mit denen Ihre APP versorgt wird. Diese Dienste werden nicht von Microsoft Teams gehostet und müssen über HTTPS zugänglich sein.
* Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer Ihre APP verwenden.
* Ihre APP-ID, mit der Sie Ihre APP mit App Studio konfigurieren können.

## <a name="get-prerequisites"></a>Abrufen von Voraussetzungen

Stellen Sie sicher, dass Sie das richtige Konto für die Erstellung von Teams-apps haben, und installieren Sie einige empfohlene Entwicklungstools.

### <a name="set-up-your-development-account"></a>Einrichten Ihres entwicklungskontos

Sie benötigen ein Teams-Konto, das benutzerdefinierte App-Sideloading zulässt. (Dies wird möglicherweise bereits von Ihrem Konto bereitgestellt.)

1. Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie apps in Microsoft Teams querladen können:
    1. Wählen Sie im Microsoft Teams-Client **apps** aus.
    1. Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung zeigt, wo in Microsoft Teams eine benutzerdefinierte App hochgeladen werden kann.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Wählen Sie hier aus</b> , wenn die querladen-Option nicht angezeigt wird oder kein Teams-Konto vorhanden ist.</summary>

Sie können ein kostenloses Test Konto für Teams erhalten, das App-Sideloading ermöglicht, indem Sie dem Microsoft 365-Entwicklerprogramm beitreten. (Der Registrierungsvorgang dauert ungefähr zwei Minuten.)

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
1. Wählen Sie **jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wenn Sie zum Begrüßungsbildschirm gelangen, wählen Sie **E5-Abonnement einrichten** aus.
1. Richten Sie Ihr Administratorkonto ein. Wenn Sie fertig sind, sollten Sie einen Bildschirm wie den folgenden sehen.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel dessen, was nach der Anmeldung für das Microsoft 365-Entwicklerprogramm angezeigt wird.":::
1. Melden Sie sich mit dem soeben eingerichteten Administratorkonto bei Microsoft Teams an.
1. Überprüfen Sie, ob Sie nun die Option **benutzerdefinierte App hochladen** haben.

</details>

### <a name="install-your-development-tools"></a>Installieren der Entwicklungstools

Sie können Teams-apps mit Ihren bevorzugten Tools erstellen, doch in diesen Lektionen wird gezeigt, wie Sie mit dem Microsoft Teams-Toolkit für Visual Studio-Code schnell loslegen können.

Microsoft Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an. Um bestimmte Arten von apps lokal zu debuggen, beispielsweise einen bot, erfahren Sie, wie Sie [ngrok verwenden, um einen sicheren Tunnel](../concepts/build-and-test/debug.md#locally-hosted) zwischen Teams und ihrer App einzurichten. (Produktions Teams-apps werden in der Cloud gehostet.)

1. Installieren Sie [Node.js](https://nodejs.org/en/).
1. Installieren Sie [ngrok](https://ngrok.com/download) , wenn Sie eine bot-oder Messaging-Erweiterung erstellen möchten.
1. Installieren Sie die neueste Version von [Visual Studio-Code](https://code.visualstudio.com/download). (Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)
1. Wählen Sie in Visual Studio Code in der linken Aktivitäts Leiste die Option **Extensions** aus, :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: und installieren Sie das **Microsoft Teams-Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Abbildung zeigt, wo in Visual Studio Code Sie die Microsoft Teams Toolkit-Erweiterung installieren können.":::

## <a name="about-the-tutorials"></a>Informationen zu den Lernprogrammen

Sie können mit einem der Teams beginnen, **Ihre ersten App** -Lektionen zu erstellen. Wenn Sie sich nicht sicher sind, wo Sie zuerst suchen, begeben Sie sich auf unseren anfängerfreundlichen Pfad und erstellen Sie ein "Hello, World!". App.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Skill Tree mit Lernpfaden für die Lernprogramme zum Erstellen Ihrer ersten app." border="false":::

## <a name="next-step"></a>Nächster Schritt

Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit dem Erstellen beginnen.

### <a name="beginner-friendly-tutorial"></a>Anfänger freundliches Tutorial

> [!div class="nextstepaction"]
> [Erstellen einer "Hello, World!"-App](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a>Andere Lernprogramme

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
