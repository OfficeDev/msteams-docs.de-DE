---
title: Installieren von Steuerelementen für die Zusammenarbeit
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Steuerelemente für die Zusammenarbeit mit Power-Apps und Microsoft 365 E3 installieren und Lösungen für Steuerelemente für die Zusammenarbeit installieren.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 5a253c9e7373a2df9e1161e6d3fc9d9b1c8ccdaa
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373031"
---
# <a name="install-collaboration-controls"></a>Installieren von Steuerelementen für die Zusammenarbeit

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

In diesem Artikel erfahren Sie, wie Sie Steuerelemente für die Zusammenarbeit installieren. Zum Erstellen und Bereitstellen Collaboration Manager Anwendungen mithilfe der Steuerelemente für die Zusammenarbeit sind Folgendes erforderlich:

* **Power-Apps**: So erstellen und führen Sie modellgesteuerte Anwendungen mithilfe der Steuerelemente für die Zusammenarbeit aus.
* **M365 E3 oder höher**: So stellen Sie benutzerdefinierte Anwendungen in Microsoft Teams bereit und speichern Aufgaben in Planner, Dateien in SharePoint und Besprechungen in Outlook.

Zum Installieren der Komponenten in einer Power Platform-Umgebung sind die folgenden Rollen erforderlich:

* System customizer
* Umgebungshersteller

Weitere Informationen zu Rollenberechtigungen finden Sie unter [Konfigurieren der Benutzersicherheit in einer Umgebung](/power-platform/admin/database-security#predefined-security-roles).

## <a name="install-the-collaboration-controls-solutions"></a>Installieren der Lösungen für Steuerelemente für die Zusammenarbeit

Sie installieren die Steuerelemente für die Zusammenarbeit über [Microsoft AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscm.collaboration-toolkit-preview?flightCodes=collaborationcontrols&signInModalType=2&ctaType=1) in Ihrer Dataverse-Umgebung.

Sie können die Komponenten in Ihrer eigenen modellgesteuerten App erst konfigurieren und verwenden, nachdem Sie zu [Microsoft AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscm.collaboration-toolkit-preview?flightCodes=collaborationcontrols&signInModalType=2&ctaType=1)  gesurft und die Steuerelemente für die Zusammenarbeit in Ihrer dataverse-Umgebung installiert haben.

Zu den Steuerelementen für die Zusammenarbeit gehören die folgenden Lösungen:

|**Settings'-Lösungen** | **Zweck** |
|---|---|
| Einstellungen für Die Zusammenarbeitssteuerelemente | Speichern der Einstellungsinfrastruktur, die die Steuerelemente für die Zusammenarbeit unterstützt |
| Steuerelemente für die Zusammenarbeit – Einstellungsobjekte | Stellt vordefinierte Einstellungswerte bereit, die von den Steuerelementen für die Zusammenarbeit verwendet werden.|

|**Lösungen für die Zusammenarbeit** | **Zweck** |
|---|---|
| Zusammenarbeit steuert Aufgaben  | Enthält das Aufgaben-PCF-Steuerelement (Power Apps-Komponentenframework). |
| Zusammenarbeit steuert Ereignisse | Enthält das PCF-Steuerelement "Ereignisse" für Outlook- und Teams-Besprechungen und -Buchungen. |
| Notizen zu Steuerelementen für die Zusammenarbeit | Enthält das NOTIZEN-PCF-Steuerelement, das Notizen in Dataverse speichert. |
| Zusammenarbeit steuert Dateien | Enthält das PCF-Steuerelement "Dateien" für den Zugriff auf Dateien in SharePoint. |
| Steuerelemente für die Zusammenarbeit – Kern |Umfasst benutzerdefinierte Zusammenarbeits-APIs, das Datenmodell für die Zusammenarbeit und virtuelle Tabellen für Ereignisse, Dateien und Aufgabensteuerelemente. |
| Zusammenarbeit steuert Genehmigungen | Enthält das neue PCF-Steuerelement "Approvals". |
| Connector für Steuerelemente für die Zusammenarbeit | Enthält den neuen Power Automate-Connector für die Zusammenarbeit |

> [!NOTE]
> Wenn Sie eine vorhandene Version der Steuerelemente in Ihrer Umgebung installiert haben, müssen Sie möglicherweise eine neue Umgebung erstellen und eine neue Installation durchführen, um erfolgreich auf die neueste Version zu aktualisieren.

Vor der Installation müssen Sie sich in einer Power Platform-Umgebung oder einem Administratormandanten befinden. Sie benötigen eine Dataverse-Umgebung mit einer Datenbank. Wenn Sie keines haben, müssen Sie [ein neues erstellen](/power-platform/admin/create-environment) , um die Installation fortzusetzen.

Um die Lösungen zu installieren, navigieren Sie zu [Microsoft AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscm.collaboration-toolkit-preview?flightCodes=collaborationcontrols&signInModalType=2&ctaType=1) , und führen Sie die folgenden Schritte aus:

1. Wählen Sie die Schaltfläche " **Jetzt abrufen** " aus.

   :::image type="content" source="../assets/images/collaboration-control/preview-form.png" alt-text="Screenshot der Schaltfläche &quot;Jetzt abrufen&quot;, um die Zusammenarbeitssteuerung anzuzeigen."border="true":::

1. Melden Sie sich mit Ihrem Konto an, füllen Sie das Formular aus, und wählen Sie **"Weiter"** aus.

   :::image type="content" source="../assets/images/collaboration-control/overview.png" alt-text="Screenshot der Übersicht über das Steuerelement &quot;Zusammenarbeit&quot;." border="true":::

   :::image type="content" source="../assets/images/collaboration-control/collaboration-controls-preview.png" alt-text="Screenshot der Vorschau des Steuerelements &quot;Zusammenarbeit installieren&quot;." border="true":::

1. Sie werden zum Power Platform Admin Center weitergeleitet. Wählen Sie im Dropdownmenü eine Umgebung aus, und stimmen Sie den Bedingungen und Richtlinienanweisungen zu.

   > [!TIP]
   > Wenn beim Auswählen der Umgebung ein Berechtigungsfehler angezeigt wird, versuchen Sie, außerhalb des Dropdownmenüs der Umgebung auszuwählen, um festzustellen, ob das Problem dadurch behoben wird.

   :::image type="content" source="../assets/images/collaboration-control/install-environment.png" alt-text="Screenshot ist ein Beispiel für die Steuerungsumgebung für die Zusammenarbeit bei der Installation." border="true":::

1. Wählen Sie **"Installieren**" aus. Die Installation kann ca. 15 Minuten dauern.

1. Wechseln sie zu [https://make.powerapps.com/](https://make.powerapps.com/), [https://make.preview.powerapps.com/](https://make.preview.powerapps.com/) wird auch unterstützt, wenn Sie bei Power Apps Preview angemeldet sind.

1. Stellen Sie sicher, dass Sie sich in der Umgebung befinden, in der die Steuerelemente installiert sind, da Sie die Umgebung anzeigen und bei Bedarf oben rechts im Power Apps-Portal ändern können.

1. Wählen Sie die Registerkarte " **Lösungen** " aus, um alle Lösungen anzuzeigen, die Sie in der richtigen Umgebung installiert haben.

   :::image type="content" source="../assets/images/collaboration-control/solutions.png" alt-text="Screenshot der Registerkarte &quot;Lösungen&quot; zum Anzeigen aller Steuerelemente für die Zusammenarbeit an Lösungen." border= "true":::

> [!NOTE]
> Die Steuerelemente für die Zusammenarbeit sind Vorschau, und Elemente können sich im Laufe der Zeit ändern, was zu Änderungen führen kann. Die Steuerelemente für die Zusammenarbeit werden in Produktionsumgebungen nicht unterstützt.

Nach der erfolgreichen Installation aller Lösungen für die Zusammenarbeit in Ihrer Umgebung können Sie eine neue modellgesteuerte App erstellen, die die Steuerungsfunktionen für die Zusammenarbeit nutzen kann.
