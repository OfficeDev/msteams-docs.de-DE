---
title: Steuerelemente für die Zusammenarbeit
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Mithilfe von Steuerelementen für die Zusammenarbeit Entscheidungsträger Apps erstellen können, die in Microsoft 365-Dienste wie Planner, Bookings und Outlook integriert sind.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: fa0cb45921820a61fbfd7112a50f28eb9230fb4b
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373024"
---
# <a name="collaboration-controls"></a>Steuerelemente für die Zusammenarbeit

Die Steuerelemente für die Zusammenarbeit ermöglichen die Anwendung von Microsoft 365 und Microsoft Teams für Genehmigungen, Dateien, Besprechungen, Notizen und Aufgaben, um die kontextbezogene Zusammenarbeit im Zusammenhang mit Geschäftsprozessen zu ermöglichen. Mit diesen Steuerelementen können Sie benutzerdefinierte Erfahrungen für die Zusammenarbeit erstellen, die direkt in Teams angezeigt werden können. Die Lösungen, die Steuerelemente für die Zusammenarbeit bilden, ermöglichen Es Entscheidungsträgern, Anwendungen zu erstellen, die in Microsoft 365-Dienste wie Planner, Bookings, Outlook und SharePoint in low-Code-Weise integriert werden.

Diese Steuerelemente bieten Ihnen die Möglichkeit, die Workflowzusammenarbeit für Ihre Benutzer zu vereinfachen, indem Sie Branchen-Apps erstellen und arbeiten, ohne den Kontext von App zu App umzuschalten:

* Genehmigungen
* Dateien
* Besprechungen
* Notizen
* Aufgaben

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

Im Folgenden sind einige der wichtigsten Funktionen von Steuerelementen für die Zusammenarbeit aufgeführt:

* **Microsoft Planner Aufgaben:** Erstellen Sie Aufgaben, und weisen Sie sie Mitgliedern eines Datensatzes zu, damit sie eine konsolidierte Liste von Aufgaben in der modellgesteuerten App und aufgaben-App in Microsoft Teams anzeigen können.

* **Dataverse-Aufgaben:** Erstellen Sie Aufgaben, die Benutzern zugewiesen werden können, die sich außerhalb Ihrer Organisation befinden.

* **Dataverse-Hinweise:** Erstellen Sie Notizen, die einem Datensatz in Ihrer App zugewiesen sind.

* **Outlook-Besprechungen:** Planen Sie Besprechungen mit Kunden und internen Mitarbeitern, und verbinden Sie sich mit Microsoft Teams nahtlos mit einer Auswahl einer Schaltfläche.

* **SharePoint-Dateien:** Geben Sie Dateien für Mitglieder eines Datensatzes frei, damit Sie relevante Artefakte an einem zentralen Speicherort suchen, referenzieren und bearbeiten können, der von SharePoint unterstützt wird.

* **Zulassungen:** Optimieren Sie Anforderungen innerhalb Ihres Teams.

> [!NOTE]
> Durch Konfigurieren und Verwenden der verschiedenen oben erwähnten Microsoft 365-Funktionen von Steuerelementen für die Zusammenarbeit erteilen Sie die Berechtigung für Benutzerdaten, die Graph-API zu durchlaufen, und akzeptieren [die Nutzungsbedingungen der Microsoft-API](/legal/microsoft-apis/terms-of-use?context=graph%2Fcontext). Weitere Informationen finden Sie unter [Microsoft Graph](/graph/overview).

## <a name="how-collaboration-controls-works"></a>Funktionsweise von Steuerelementen für die Zusammenarbeit

Die Steuerelemente werden in einer modellgesteuerten Power Apps-Anwendung (MDA) ausgeführt, die in Microsoft Teams bereitgestellt werden kann. MDA wird auf Microsoft Dataverse ausgeführt und kann in ein benutzerdefiniertes Datenmodell integriert werden. Die Steuerelemente werden in Microsoft Graph für Planner-Aufgaben, Outlook- und Teams-Kalender und SharePoint-Dateien integriert. Die Steuerelemente für die Zusammenarbeit können nicht direkt in externe Quellen integriert werden, z. B. in ein Datensatzsystem oder ein Portal.

* Daten können dataverse aus externen Quellen über OData-Standard-APIs hinzugefügt werden.

* Daten können von Dataverse über OData-Standard-APIs gelesen und an externe Quellen wie ein Datensatzsystem oder ein Portal übermittelt werden.

:::image type="content" source="~/assets/images/collaboration-control/consumption-mda.png" alt-text="Lebenszyklus der Zusammenarbeit":::
