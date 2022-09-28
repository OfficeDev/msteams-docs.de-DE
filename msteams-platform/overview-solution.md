---
title: Teams-Lösung zum Erstellen von Apps
author: heath-hamilton
description: Verstehen, wie Sie Ihre App planen, entwerfen, erstellen, auf Microsoft 365 erweitern, testen, verteilen, monetarisieren und in Teams integrieren.
ms.topic: overview
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 11/02/2021
ms.openlocfilehash: ac4f3a208484a093460a14777a351aa4abc10af7
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100784"
---
# <a name="the-teams-solution"></a>Die Teams-Lösung


Die Microsoft Teams-Plattform ist eine leistungsstarke und flexible Plattform zum Erstellen von Apps für Teams. Sie bietet eine umfangreiche Sammlung von Entwicklungsumgebungen und Tools zur Unterstützung der App-Entwicklung.

## <a name="the-user-story"></a>Die User Story

Sie haben eine Ansicht der Teams-Angebote erhalten. Sie können sie nun den Benutzeranforderungen zuordnen. Sehen wir uns das Szenario noch einmal an.

Der Entwickler der Tours and Travel Agency möchte eine App für seine Nutzer, die Reisenden, entwickeln. Die App muss:

- Überprüfung und Übermittlung der Vorhersage an die im Reisebüro registrierten Reisenden.
- Benachrichtigung der Nutzer einen Tag vor dem Abflugdatum, damit sie planen können.

Sortieren und Zuordnen von Anforderungen zu Teams-Features:

| Anforderungen der Nutzer-App | Prognose überprüfen | Benachrichtigung vor der Reise | Registrierter Nutzer |
| --- |:---:|:---:|:---:|
| **Funktionalität** | Bot | &nbsp; | &nbsp; |
| **Integration** | &nbsp; | &nbsp; | :::image type="icon" source="assets/icons/microsoft-icon.png"::: Microsoft Graph, Wetter-API |
| **Scope** | &nbsp; | Persönliche App | &nbsp; |
| **Integrationspunkt** | &nbsp; | Chat | &nbsp; |

**Teams-App-Lösung**: Eine *persönliche Chat-Bot*-App von Teams, die Prognosen prüft und *registrierten Nutzern* vor ihrem Reisedatum *eine Prognose-Benachrichtigung sendet*.

:::image type="content" source="../msteams-platform/assets/images/overview/developer-scenario-solution.png" alt-text="Ein Entwickler in einem Reisebüro erstellt einen Bot für Teams, der Wettervorhersagen an Kunden sendet, damit sie ihre Reisedaten im Voraus planen können":::

Teams offers these and many more capabilities to bring your users a feature-rich app solution. To develop this app:

1. Erstellen Sie eine persönliche Chatbot-App.
1. Integrieren Sie eine externe Wettervorhersage-API, um eine Verbindung herzustellen und eine Vorhersage für ein bestimmtes Datum und einen bestimmten Standort abzufragen.
1. Integration mit :::image type="icon" source="assets/icons/teams-icon.png"::: Microsoft Graph für registrierte Benutzer.
1. Überprüfen und senden Sie Prognosedetails basierend auf dem Reisedatum und dem Reisestandort des Nutzers.

## <a name="choose-what-suits-you"></a>Wählen Sie aus, was zu Ihnen passt

Sie können eine Teams-App gemäß den Anforderungen Ihrer App erstellen. Wählen Sie basierend auf Faktoren wie Geschäftsanforderungen, Entwicklungsumgebung, Domänenwissen die Umgebung und die Tools aus, die Sie erstellen möchten.

Eine Teams-App bietet Ihnen die Flexibilität, Ihre Buildumgebung auszuwählen. Sie enthält Tools, Framework und Sprachen für die App-Entwicklung.

:::image type="content" source="../msteams-platform/assets/images/overview/tools-of-your-choice.png" alt-text="Unternehmen benötigt App":::

Build your Teams app in the environment that works for your particular requirements. You can even select a combination.

Beispielsweise können Sie das Teams-Toolkit verwenden, um eine App mit JavaScript zu erstellen und auf einer SharePoint-Website zu hosten.

## <a name="teams-collaborative-platform"></a>Teams-Plattform für die Zusammenarbeit

Eine Teams-App bietet Ihren Nutzern die Vorteile eines Arbeitsbereichs für die Zusammenarbeit.

Als Plattform zum Erstellen von Apps bietet Teams die gesamte Palette von Apps und Toolkits. Die Teams-Plattform unterstützt Sie in jeder Phase von der Planung Ihrer App bis zur Vermarktung.

:::image type="content" source="../msteams-platform/assets/images/overview/teams-dev-life-cycle.png" alt-text="Beschreiben eines Lebenszyklus der Teams-App-Entwicklung. Planen, Entwerfen, Erstellen, Erweitern, Testen, Bereitstellen, Vermarkten. Details werden unten in einer Aufzählung angezeigt.":::

From designing to building and distributing a Teams app, you can use various tools and services. An example development flow can be:

1. Planen Sie Ihr Projekt und ermitteln Sie die Anforderung.
1. Design the app. Use Teams UI Kit and UI Library for designing tabs UI.
1. Erstellen Sie die App mit JavaScript mithilfe des Teams-Toolkits.
1. Erweitern Sie die Funktionalität, indem Sie weitere Teams-Funktionen und M365-Daten mit :::image type="icon" source="assets/icons/microsoft-icon.png"::: Microsoft Graph hinzufügen.
1. Testen Sie die App auf einem Entwicklermandanten mit Beispiel-Nutzerdaten.
1. Stellen Sie die App in Azure bereit.
1. Verwalten und Veröffentlichen der Apps im Store mit dem Developer Portal. Monetarisieren Sie Ihre App mit Optionen wie SaaS-Angeboten, In-App-Käufen uvm.

## <a name="next-step"></a>Nächster Schritt

:::row:::
    :::column span="1":::
        **Mit dem Erstellen beginnen**
    :::column-end:::
    :::column span="2":::
        Machen Sie sich schnell mit der Erstellung für Teams vertraut, indem Sie Ihre Umgebung einrichten und eine einfache App erstellen.

        > [!div class="nextstepaction"]
        > [Die erste App erstellen](get-started/get-started-overview.md)
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Siehe auch

:::row:::
    :::column span="1":::
        **Planen Ihrer App**
    :::column-end:::
    :::column span="2":::
        Verstehen und Zuordnen Ihrer App-Anwendungsfälle zu Teams-Features.

        > [!div class="nextstepaction"]
        > [Planen Ihrer App](~/concepts/app-fundamentals-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Entwerfen Ihrer App**
    :::column-end:::
    :::column span="2":::
        Entwerfen Sie Ihre App-Benutzeroberfläche mit dem Teams-Kit für Benutzeroberflächen.

        > [!div class="nextstepaction"]
        > [Entwerfen Ihrer Teams-App](~/concepts/design/design-teams-app-process.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Erstellen Sie Ihre Anwendung**
    :::column-end:::
    :::column span="2":::
        Looking for app development inspiration? Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways a Teams app can help your users.

        > [!div class="nextstepaction"]
        > [Anzeigen von App-Szenarien](https://adoption.microsoft.com/en-us/extensibility-look-book-gallery/)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Erstrecken Ihrer App über Microsoft 365**
    :::column-end:::
    :::column span="2":::
Mit dem Teams JavaScript-Client-SDK v2 Preview können Sie eine Vorschau Ihrer Teams Apps anzeigen, die in anderen stark genutzten Microsoft 365-Umgebungen ausgeführt werden.

        > [!div class="nextstepaction"]
        > [Erweitern Ihrer App](m365-apps/overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Testen eigener Apps**
    :::column-end:::
    :::column span="2":::
        Nachdem Sie Ihre App in Teams integriert haben, müssen Sie ihre App testen, bevor Sie diese veröffentlichen.

        > [!div class="nextstepaction"]
        > [Testen eigener Apps](concepts/build-and-test/test-app-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Verteilen Ihrer App**
    :::column-end:::
    :::column span="2":::
        Sie können Ihre Teams-App für eine Person, ein Team, eine Organisation oder jede Person zur Verfügung stellen, die sie nutzen möchte.

        > [!div class="nextstepaction"]
        > [Verteilen Ihrer App](~/concepts/deploy-and-publish/apps-publish-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Monetarisieren Ihrer App**
    :::column-end:::
    :::column span="2":::
        Teams Store bietet Optionen zur Monetarisierung von Apps, z. B. SaaS-Angebote und In-App-Käufe. Wählen Sie die beste Monetarisierungsoption aus, die für Ihre Teams-App geeignet ist.

        > [!div class="nextstepaction"]
        > [Monetarisieren Ihrer App](concepts/deploy-and-publish/appsource/prepare/monetize-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Integration in Microsoft Teams**
    :::column-end:::
    :::column span="2":::
        Kombinieren Sie die Features, die Benutzer an einer vorhandenen Web-App, einem Dienst oder System schätzen, mit den Features für die Zusammenarbeit von Teams.

        > [!div class="nextstepaction"]
        > [Integrieren einer vorhandenen App](samples/integrating-web-apps.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Selbst ein kleiner Code kann viel bewirken**
    :::column-end:::
    :::column span="2":::
        You don't need to be an expert programmer to build a great Teams app. Try one of several low-code solutions.

        > [!div class="nextstepaction"]
        > [Erstellen einer App mit wenig Code](samples/teams-low-code-solutions.md)
    :::column-end:::
:::row-end:::
