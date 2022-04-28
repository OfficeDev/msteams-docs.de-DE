---
title: Planen von Teams Mobilgeräten
author: surbhigupta
description: Leitfaden zum Planen des Erstellens einer App auf Teams Mobile
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: v-abirade
ms.openlocfilehash: e260d3d4a1afcc625d588e6918eb9a01acfdea77
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103930"
---
# <a name="plan-responsive-tabs-for-teams-mobile"></a>Planen reaktionsfähiger Registerkarten für Teams Mobile

 Teams Plattform bietet die Möglichkeit, Apps auf Mobilgeräten und Desktops zu erstellen. Ihre App-Benutzer können entweder Desktop oder Mobil oder beides bevorzugen. Die Benutzer können Daten auf dem Desktop vorbereiten, aber mehr Daten mit mobilen Geräten nutzen und teilen. Der Schlüssel zum Erstellen jeder App besteht darin, die Anforderungen der Benutzer zu verstehen und zu erfüllen. Es gibt Funktionen wie Bots, Nachrichtenerweiterungen und Connectors, die nahtlos auf desktop- und mobilen Geräten funktionieren. Das Erstellen von Registerkarten und Aufgabenmodulen erfordert jedoch eine Planung für das Hosten Ihrer Weboberfläche auf Teams Mobilgeräten. Der Artikel enthält Anleitungen zum Planen Ihrer reaktionsfähigen Webseiten auf Teams Mobilgeräten.

## <a name="identify-apps-scope"></a>Identifizieren des App-Bereichs

Die folgende Liste enthält die wichtigsten Informationen zum Planen des Erstellens von Apps für Teams Mobile:

* Berücksichtigen Sie die geräteübergreifende Funktionalität Teams App. Wenn Sie beispielsweise über eine gut funktionierende App auf dem Desktop verfügen, können Sie eine ähnliche App auf mobilgeräten erstellen. Anfangs kann es schwierig sein, die gesamte Desktoperfahrung auf Mobilgeräten zu verschieben. Sie können mit einfachen, aber gängigen Szenarien beginnen. Fügen Sie Funktionen und Funktionen hinzu, nachdem Sie mehr Einblicke und Benutzerfeedback gesammelt haben.

* Stellen Sie sicher, dass sie auf mobilgeräte geeignete Benutzerpersona ausgerichtet sind. Wenn Sie z. B. eine App erstellen, die Diensten für Endbenutzer und außerdem Datenzugriff für Entwickler und leitende Manager bereitstellt, können die Endbenutzer die App mehr nutzen, während Sie mit dem Erstellen von Apps auf Teams Mobilgerät beginnen. Sie können auf alle Personen in Ihrer Desktop-App eingehen, es wird jedoch empfohlen, mit Persona mit einer größeren Basis und möglichen Early Adopters für eine kleinere Bildschirmerfahrung zu beginnen. Gemäß dem Beispiel sind die Endbenutzer die entsprechenden Benutzerpersonas. Sie können schrittweise Funktionen hinzufügen, um andere Benutzerpersonas auf Ihrem Teams Mobile zu unterstützen.

## <a name="understand-different-stages-to-build-apps"></a>Grundlegendes zu verschiedenen Phasen zum Erstellen von Apps

Nachdem Sie den App-Bereich identifiziert haben, ist es an der Zeit, die folgenden drei Phasen zu verstehen, um jede App auf Teams Mobilgeräten zu planen und die Benutzerfreundlichkeit zu verbessern:

1. **Verbrauch**

   Apps auf Mobilgeräten anzeigen. Um eine App auf mobilgeräten zu erstellen, können Sie mit der Nutzung beginnen. Da die mobile Welt das Scrollen nach Inhalten zu einer gängigen Praxis gemacht hat, können Sie relevante Informationen anzeigen. Verwenden Sie Einsatzmechanismen, z. B. Benachrichtigungen, um Updates zu informieren.

2. **Schnelle Aktionen**

   Verwenden Sie die App auf mobilgeräten. Nachdem Ihre Benutzer mit der Nutzung der Inhalte auf mobilgeräten begonnen haben, können Sie Ihre App auf die nächste Ebene skalieren, indem Sie einige Aktionen von der Desktop-App migrieren. Sie können neue Aktionen für mobile Geräte optimieren und erstellen.

3. **Aktivierung**

   Stellen Sie vollständige App-Funktionen bereit, um sich auf mobilgeräten zu engagieren. Wenn Ihre Benutzer mit Ihrer App interagieren, bieten Sie die vollständige immersive Erfahrung auf mobilgeräten, entweder auf augenhöher oder besser als die Desktoperfahrung. Um ihren Benutzern eine gute Benutzererfahrung zu bieten, sorgen Sie dafür, dass alle Anwendungsfälle auf Mobilgeräten reaktionsfähig sind.

> [!TIP]
> Informationen zu den Entwurfsrichtlinien finden Sie im [Entwurfsprozess für Teams Apps](design-teams-app-process.md).

## <a name="use-cases"></a>Anwendungsfälle

Lassen Sie uns die folgenden Anwendungsfälle durchgehen, um zu verstehen, wie verschiedene Arten von Apps für Teams Mobile geplant werden:

<br>

<details>

<summary><b>Dashboarding- und Datenvisualisierungs-Apps</b></summary>

Sie können verstehen, wie Sie dynamische Registerkarten für Dashboarding- und Datenvisualisierungs-Apps auf Teams mobilen Plattform planen.

Verbrauch:

In der ersten Phase können Sie die grundlegendste Verbrauchserfahrung implementieren, um Daten anzuzeigen. Der Zweck jeder App in der Domäne besteht darin, Daten in Form von Visualisierungen anzuzeigen. In Ihrer App können Sie zuletzt angezeigte Visualisierungen auf dem Desktop oder eine Liste aller autorisierten Diagramme für die Benutzer anzeigen. Nach dem Erstellen von Dashboards auf dem Desktop können Benutzer auf die Informationen über mobile Geräte zugreifen. Sie können eine detaillierte Ansicht eines beliebigen Diagramms anzeigen, das vom Benutzer als erweiterte Ansicht auf Ihren Registerkarten oder mithilfe von Aufgabenmodulen ausgewählt wurde.

Sie können die folgenden Informationen anzeigen:

* Dashboards und Zusammenfassungen
* Visuelle Daten, Karten und Infografiken
* Diagramme, Diagramme und Tabellen

![Nutzung von Dashboarding- und Datenvisualisierungs-Apps](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-consumption.png)

Schnelle Aktionen:

In der zweiten Phase können die Benutzer über die Desktopoberfläche an den vorhandenen Diagrammen und visuellen Elementen arbeiten. Sie können die folgenden Aktionen einführen:

* Inhalt durchsuchen
* Filtern von Daten
* Erstellen von Lesezeichen

![Dashboarding- und Datenvisualisierungs-Apps – schnelle Aktionen](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-quick-actions.png)

Aktivierung:

In der dritten Phase können Benutzer Inhalte wie Diagramme und Grafiken von Grund auf neu erstellen. Stellen Sie sicher, dass Alle Funktionen in Ihrer App für mobile Geräte eingeführt werden. Sie können z. B. Aufgabenmodule verwenden, um auf bestimmte Datenelemente mit detaillierter Ansicht zuzugreifen.

Sie können Benutzern folgenden Zugriff gewähren:

* Titel und Beschreibung ändern
* Einfügen von Datenelementen zum Erstellen von Visualisierungen
* Freigeben von Visualisierungen in einem Kanal- oder Gruppenchat

![Aktivieren von Dashboarding- und Datenvisualisierungs-Apps](../../assets/images/app-fundamentals/dashboarding-and-data-visualization-apps-enablement.png)

<br>

</details>

<br>

<details>

<summary><b>Aufgaben-Boarding-Apps</b></summary>

Sie können verstehen, wie Sie reaktionsfähige Registerkarten für Aufgabenboarding-Apps auf Teams mobilen Plattform planen.

Verbrauch:

In der ersten Phase kann Ihre App dem Benutzer die Liste der Aufgaben in einem vertikalen Stapel anzeigen. Wenn mehrere Kategorien von Vorgängen vorhanden sind, z. B. **"Vorgeschlagen**", " **Aktiv"** und " **Geschlossen** ", stellen Sie Filter zum Anzeigen gruppierter Vorgänge oder als Kopfzeilen bereit, um die gruppierten Vorgänge anzuzeigen.

![Nutzung von Taskboarding-Apps](../../assets/images/app-fundamentals/taskboarding-apps-consumption.png)

Schnelle Aktionen:

In der zweiten Phase können Sie benutzern den folgenden App-Zugriff bereitstellen:

* Erstellen von Aufgaben oder Elementen mit den obligatorischen Feldern, um die kognitive Belastung der Benutzer zu verringern
* Ändern des Tafeltyps oder der Ansicht
* Überprüfen von Aufgaben durch Erweitern der Ansicht
* Verwenden von Aufgabenmodulen zum Anzeigen einer detaillierten Ansicht
* Verschieben der Aufgaben in verschiedene Kategorien
* Freigeben relevanter Aufgaben in Chats und Kanälen über E-Mails und Aktivitätsfeeds

![Schnelle Aktionen für Taskboarding-Apps](../../assets/images/app-fundamentals/taskboarding-apps-quick-actions.png)

Aktivierung:

In der dritten Phase können Sie die Benutzererfahrung mit den folgenden Aktivitäten aktivieren:

* Hinzufügen neuer Projekte und Boards
* Hinzufügen und Ändern verschiedener Kategorien, z. B. **"Vorgeschlagen"**, "**Aktiv"** und "**Geschlossen**"
* Konfigurieren der Aufgaben für Kommentare, Anlagen und andere komplexe Features

![Aktivierung von Taskboarding-Apps](../../assets/images/app-fundamentals/taskboarding-apps-enablement.png)
<br>

</details>

<br>

<details>

<summary><b>Gemeinsame Dokumenterstellung und Whiteboarding von Apps</b></summary>

Sie können verstehen, wie Sie dynamische Registerkarten für die gemeinsame Dokumenterstellung und das Whiteboarding von Apps auf Teams mobilen Plattform planen.

Verbrauch:

In der ersten Phase können Sie die Desktopoberfläche in Betracht ziehen, um die Inhalte und Ressourcen in Ihrer App anzuzeigen.  Sie können die folgenden Funktionen anzeigen:

* Kommentare oder Feedback
* Vergrößern oder Verkleinern
* Aktuelle Phase oder Fortschritt eines ausstehenden Dokuments

![Gemeinsame Dokumenterstellung und Nutzung von Whiteboarding-Apps](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-consumption.png)

Schnelle Aktionen:

In der zweiten Phase können Sie die folgenden Aktionen einführen:

* Erstellen einer neuen Tafel für die Zusammenarbeit oder neuer Dokumente zum Signieren
* Teilen von Boards intern und auch mit Gästen
* Konfigurieren von Administratorberechtigungen

> [!TIP]
> Sie machen Aktionen verfügbar, die auf den kleinen Bildschirmen einfach angezeigt werden können.

![Schnelle Aktionen für gemeinsame Dokumenterstellung und Whiteboarding von Apps](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-quick-actions.png)

Aktivierung:

Stellen Sie in der dritten Phase ihren Benutzern eine vollständige Erfahrung bereit. Sie können die Benutzererfahrung mit den folgenden Aktivitäten aktivieren:

* Hinzufügen von Text, Formen und schnellen Notizen
* Navigieren im Inhalt
* Hinzufügen von Ebenen und Filtern
* Löschen, Rückgängigmachen und Wiederholen von Vorgängen
* Zugreifen auf Kamera und Mikrofon mit JS SDK-APIs. Weitere Informationen zu Gerätefunktionen finden Sie in der [Übersicht über die Gerätefunktionen](../device-capabilities/device-capabilities-overview.md).

![Aktivieren von Apps für gemeinsame Dokumenterstellung und Whiteboarding](../../assets/images/app-fundamentals/coauthoring-and-whiteboarding-apps-enablement.png)

<br>

</details>

## <a name="see-also"></a>Siehe auch

Die folgenden Entwurfs- und Validierungsrichtlinien helfen je nach Umfang Ihrer App:

* [Entwerfen ihrer Registerkarte](../../tabs/design/tabs.md)
* [Entwerfen Ihres Bots](../../bots/design/bots.md)
* [Entwerfen von Aufgabenmodulen](../..//task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [Richtlinien für die Store-Validierung](../deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)
