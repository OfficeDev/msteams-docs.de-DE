---
title: Teams-Lösung zum Erstellen von Apps
author: heath-hamilton
description: Übersicht über die Teams-Lösung zum Erstellen von Apps
ms.topic: overview
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 11/02/2021
ms.openlocfilehash: bb05bc85c4b070870a88d8c71cb80e4d7ef4390c
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398722"
---
# <a name="the-teams-solution"></a>Die Teams-Lösung

Die Microsoft Teams-Plattform ist eine leistungsstarke und flexible Plattform zum Erstellen von Apps für Microsoft Teams. Sie bietet eine umfangreiche Sammlung von Entwicklungsumgebungen und Tools zur Unterstützung der App-Entwicklung.

## <a name="the-user-story"></a>Die User Story

Sie haben eine Ansicht der Teams-Angebote erhalten. Sie können sie nun den Benutzeranforderungen zuordnen. Sehen wir uns das Szenario noch einmal an.

Der Entwickler eines Reisebüros möchte eine App für seine Nutzer, die Reisenden, entwickeln. Die App muss:

- Überprüfung und Übermittlung der Vorhersage an die im Reisebüro registrierten Reisenden.
- Benachrichtigung der Nutzer einen Tag vor dem Abflugdatum, damit sie planen können.

Sortieren und Zuordnen von Anforderungen zu Teams-Features:

| Anforderungen der Nutzer-App | Prognose überprüfen | Benachrichtigung vor der Reise | Registrierter Nutzer |
| --- |:---:|:---:|:---:|
| **Funktionalität** | Bot | &nbsp; | &nbsp; |
| **Integration** | &nbsp; | &nbsp; | Microsoft Graph, Wetter-API |
| **Scope** | &nbsp; | Persönliche App | &nbsp; |
| **Integrationspunkt** | &nbsp; | Chat | &nbsp; |

**Teams-App-Lösung**: Eine *persönliche Chat-Bot*-App von Teams, die Prognosen prüft und *registrierten Nutzern* vor ihrem Reisedatum *eine Prognose-Benachrichtigung sendet*.

:::image type="content" source="../msteams-platform/assets/images/overview/developer-scenario-solution.png" alt-text="Ein Entwickler bei einem Reisebüro erstellt einen Bot für Microsoft Teams, der Wettervorhersagen an Kunden sendet, damit sie ihre Reisedaten im Voraus planen können " border="false":::.

Teams bietet diese und viele weitere Funktionen, um Ihren Benutzern eine funktionsreiche App-Lösung zu bieten. So entwickeln Sie diese App:

1. Erstellen Sie eine persönliche Chatbot-App.
1. Integrieren Sie eine externe Wettervorhersage-API, um eine Verbindung herzustellen und eine Vorhersage für ein bestimmtes Datum und einen bestimmten Standort abzufragen.
1. Integration in Microsoft Graph für registrierte Nutzer.
1. Überprüfen und senden Sie Prognosedetails basierend auf dem Reisedatum und dem Reisestandort des Nutzers.

## <a name="choose-what-suits-you"></a>Wählen Sie aus, was zu Ihnen passt

Sie können eine Teams-App gemäß den Anforderungen Ihrer App erstellen. Wählen Sie basierend auf Faktoren wie Geschäftsanforderungen, Entwicklungsumgebung, Domänenwissen die Umgebung und die Tools aus, die Sie erstellen möchten.

Eine Teams-App bietet Ihnen die Flexibilität, Ihre Buildumgebung auszuwählen. Sie enthält Tools, Framework und Sprachen für die App-Entwicklung.

:::image type="content" source="../msteams-platform/assets/images/overview/tools-of-your-choice.png" alt-text="Unternehmen benötigt App" border="false":::

Erstellen Sie Ihre Teams-App in der Umgebung, die ihren speziellen Anforderungen entspricht. Sie können sogar eine Kombination auswählen.

Beispielsweise können Sie das Teams-Toolkit verwenden, um eine App mit JavaScript zu erstellen und auf einer SharePoint-Website zu hosten.

## <a name="teams-collaborative-platform"></a>Teams-Plattform für die Zusammenarbeit

Eine Teams-App bietet Ihren Nutzern die Vorteile eines Arbeitsbereichs für die Zusammenarbeit.

Als Plattform zum Erstellen von Apps bietet Teams die gesamte Palette von Apps und Toolkits. Die Teams-Plattform unterstützt Sie in jeder Phase von der Planung Ihrer App bis zur Vermarktung.

:::image type="content" source="../msteams-platform/assets/images/overview/teams-dev-life-cycle.png" alt-text="Beschreiben eines Lebenszyklus der Teams-App-Entwicklung. Planen, Entwerfen, Erstellen, Erweitern, Testen, Bereitstellen, Vermarkten. Details werden unten in einer Aufzählung angezeigt." border="false":::

Vom Entwurf bis zur Erstellung und Vermarktung einer Teams-App können Sie verschiedene Tools und Dienste nutzen. Ein Beispiel für einen Entwicklungsablauf kann sein:

1. Planen Sie Ihr Projekt und ermitteln Sie die Anforderung.
1. Entwerfen Sie die App. Verwenden Sie Teams UI Kit und UI Library für die Gestaltung der Benutzeroberfläche von Registerkarten.
1. Erstellen Sie die App mit JavaScript mithilfe des Teams-Toolkits.
1. Erweitern Sie die Funktionalität, indem Sie weitere Teams-Funktionen und M365-Daten mit Microsoft Graph hinzufügen.
1. Testen Sie die App auf einem Entwicklermandanten mit Beispiel-Nutzerdaten.
1. Stellen Sie die App in Azure bereit.
1. Verwalten und Veröffentlichen der Apps im Store mit dem Developer Portal.

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
        Entwerfen Sie Ihre App-Benutzeroberfläche mit dem Microsoft Teams UI Kit.

        > [!div class="nextstepaction"]
        > [Entwerfen Ihrer Teams-App](~/concepts/design/design-teams-app-process.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Erstellen Sie Ihre Anwendung**
    :::column-end:::
    :::column span="2":::
        Suchen Sie nach Inspiration für die App-Entwicklung? Stöbern Sie in unserer Liste mit realen Szenarien und Branchenlösungen mit High Fidelity-Konzeptmodellen, um die verschiedenen Möglichkeiten zu verstehen, wie eine Teams-App Ihren Benutzern helfen kann.

        > [!div class="nextstepaction"]
        > [Anzeigen von App-Szenarien](https://adoption.microsoft.com/extensibility-look-book/scenarios/)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Erstrecken Ihrer App über Microsoft 365**
    :::column-end:::
    :::column span="2":::
        Mit Microsoft Teams JavaScript-Client-SDK v2 Preview können Sie eine Vorschau Ihrer Teams Apps anzeigen, die in anderen stark frequentierten Microsoft 365-Umgebungen ausgeführt werden.

        > [!div class="nextstepaction"]
        > [Erweitern Ihrer App](m365-apps/overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Testen eigener Apps**
    :::column-end:::
    :::column span="2":::
        Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie ihre App testen, bevor Sie sie veröffentlichen.

        > [!div class="nextstepaction"]
        > [Testen eigener Apps](concepts/build-and-test/test-app-overview.md)
    :::column-end:::
:::row-end:::

:::row:::
    :::column span="1":::
        **Verteilen Ihrer App**
    :::column-end:::
    :::column span="2":::
        Sie können Ihre Microsoft Teams-App für eine Person, ein Team, eine Organisation oder jede Person bereitstellen, die sie verwenden möchte.

        > [!div class="nextstepaction"]
        > [Verteilen Ihrer App](~/concepts/deploy-and-publish/apps-publish-overview.md)
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
        Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu entwickeln. Probieren Sie eine der verschiedenen Low-Code-Lösungen aus.

        > [!div class="nextstepaction"]
        > [Erstellen einer App mit wenig Code](samples/teams-low-code-solutions.md)
    :::column-end:::
:::row-end:::
