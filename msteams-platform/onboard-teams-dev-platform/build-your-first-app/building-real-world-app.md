---
title: Erste Schritte beim Erstellen Ihrer ersten Teams-App
author: heath-hamilton
ms.author: lajanuar
description: Übersicht und Voraussetzungen für die Erstellung Ihrer ersten Microsoft Teams-App
ms.openlocfilehash: 9392096a285a43d3a1f8bed5020e3464da0f7f18
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964703"
---
# <a name="get-started-building-your-first-teams-app"></a>Erste Schritte beim Erstellen Ihrer ersten Teams-App

In den **ersten App** -Lektionen erstellen Sie grundlegende Teams-apps. In jedem Lernprogramm wird erläutert, wie Sie eine einfache Real-World-Teams-app erstellen, während Sie allgemeine Tools, grundlegende Konzepte und einige erweiterte Funktionen einführen.

## <a name="what-youll-learn"></a>Was Sie lernen

Hier ist eine Vorstellung davon, was Sie wissen, nachdem Sie die Lektionen durchlaufen haben.

> [!div class="checklist"]
  >
  > * Mit dem Microsoft Teams Toolkit für Visual Studio Code können Sie **schnell mit dem Team-Toolkit in Kontakt**treten, um ein App-Projekt und ein Gerüst zu erstellen, damit Sie in wenigen Minuten eine laufende APP haben.
  > * **Definieren Sie Ihre APP mit dem Manifest**: im App-Manifest geben Sie die Funktionen und Dienste an, die ihre Teams-App verwendet.
  > * **Bereich der Benutzergruppe Ihrer APP**: Erstellen einer Teams-App für den persönlichen Gebrauch, die Zusammenarbeit oder beides.
  > * **Holen Sie sich Erfahrung mit Frameworks**: passen Sie Ihre APP an (ändern Sie beispielsweise Ihr Farbschema entsprechend dem Teams-Design) mit Hilfe des Teams-JavaScript-SDK. Außerdem finden Sie Informationen zu allgemeinen Tools zum Erstellen und Verwalten von Bots.
  > * **Erweitern Sie Ihre APP**: in den Lektionen finden Sie Verwandte Themen, die Sie wahrscheinlich interessieren (beispielsweise Authentifizierungs-und Entwurfsrichtlinien).

## <a name="teams-app-fundamentals"></a>Grundlagen der Microsoft Teams-App

Bevor Sie mit den Lernprogrammen beginnen, sollten Sie die folgenden Informationen zum Erstellen von Apps für Microsoft Teams kennen.

### <a name="apps-can-have-multiple-capabilities"></a>Apps können mehrere Funktionen haben

Microsoft Teams-apps bestehen aus einer oder mehreren [Plattformfunktionen](../capabilities-overview.md). Sie können diese Funktionen mithilfe einer Reihe von Teams-spezifischen [UI-Komponenten und Konventionen](../doc-links/teams-ui-conventions.md)anzeigen, beispielsweise Karten und Aufgaben Module.

### <a name="teams-doesnt-host-your-app"></a>Ihre APP wird von Microsoft Teams nicht gehostet.

Eine Teams-App umfasst drei wichtige Teile:

* Die Logik, Datenspeicherung und API-Aufrufe, mit denen Ihre APP versorgt wird. Diese Dienste werden nicht von Microsoft Teams gehostet und müssen über HTTPS zugänglich sein.
* Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer Ihre APP verwenden.
* Ihr App-Paket, mit dem Sie die app in Microsoft Teams installieren. Sie enthält App-Metadaten und Zeiger auf Ihre gehosteten Dienste.

## <a name="get-prerequisites"></a>Abrufen von Voraussetzungen

Stellen Sie sicher, dass Sie das richtige Konto für die Erstellung von Teams-apps haben, und installieren Sie einige empfohlene Entwicklungstools.

### <a name="set-up-your-development-account"></a>Einrichten Ihres entwicklungskontos

Sie benötigen ein Teams-Konto, das benutzerdefinierte App-Sideloading zulässt. (Dies wird möglicherweise bereits von Ihrem Konto bereitgestellt.)

1. Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie apps in Microsoft Teams querladen können:
    1. Wählen Sie im Microsoft Teams-Client **apps**aus.
    1. Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.

    :::image type="content" source="../doc-links/images/upload-custom-app-closeup.png" alt-text="querladen-Option (Ansicht)":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Wählen Sie hier aus</b> , wenn die querladen-Option nicht angezeigt wird oder kein Teams-Konto vorhanden ist.</summary>

Sie können ein kostenloses Test Konto für Teams erhalten, das App-Sideloading ermöglicht, indem Sie dem Microsoft 365-Entwicklerprogramm beitreten. (Der Registrierungsvorgang dauert ungefähr zwei Minuten.)

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
1. Wählen Sie **jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
1. Wenn Sie zum Begrüßungsbildschirm gelangen, wählen Sie **E5-Abonnement einrichten**aus.
1. Richten Sie Ihr Administratorkonto ein. Wenn Sie fertig sind, sollten Sie einen Bildschirm wie den folgenden sehen.
:::image type="content" source="../doc-links/images/dev-program-subscription.png" alt-text="Entwicklerprogramm-Abonnement Ansicht":::
1. Melden Sie sich mit dem soeben eingerichteten Administratorkonto bei Microsoft Teams an.
1. Überprüfen Sie, ob Sie nun die Option **benutzerdefinierte App hochladen** haben.

</details>

### <a name="install-your-development-tools"></a>Installieren der Entwicklungstools

Sie können Teams-apps mit Ihren bevorzugten Tools erstellen, doch in diesen Lektionen wird gezeigt, wie Sie mit dem Microsoft Teams-Toolkit für Visual Studio-Code schnell loslegen können.

Microsoft Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an. Da Sie die erste APP lokal hosten, erfahren Sie, wie Sie mithilfe von [ngrok einen sicheren Tunnel](../doc-links/debug.md#locally-hosted) zwischen Teams und ihrer App einrichten.

1. Installieren Sie [Node.js](https://nodejs.org/en/).
1. Installieren Sie die neueste Version von [Visual Studio-Code](https://code.visualstudio.com/download). (Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)
1. Wählen Sie in Visual Studio Code in der linken Aktivitäts Leiste die Option **Extensions** aus, :::image type="icon" source="../doc-links/images/vs-code-extensions.png"::: und installieren Sie das **Microsoft Teams-Toolkit**.
    :::image type="content" source="../doc-links/images/vsc-install-toolkit.png" alt-text="Installieren der Toolkit-Ansicht":::
1. Installieren Sie [ngrok](https://ngrok.com/download).

## <a name="next-step"></a>Nächster Schritt

Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit dem Erstellen beginnen.

> [!div class="nextstepaction"]
> [Erstellen und Ausführen ihrer ersten App](../build-your-first-app/build-and-run.md)
