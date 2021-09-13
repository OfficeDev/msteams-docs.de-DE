---
title: Zuordnen von Anwendungsfällen zu Teams App-Funktionen
author: surbhigupta
description: Ermitteln Sie, wie die Anwendungsfälle Ihrer App innerhalb der Teams funktionieren können.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: d9c52acc1562cb2dcfdcd9b0c58e4d4001699c9c
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156297"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Zuordnen von Anwendungsfällen zu Teams App-Funktionen

Nachdem Sie ermittelt *haben, wer* der Benutzer ist und *welches* Problem Sie lösen werden, müssen Sie *entscheiden, wie* das Problem gelöst werden soll. *Wer,* *was* und *wie* den Prozess des Verständnisses und der Zuordnung Ihrer Anwendungsfälle zu Teams App-Funktionen abschließt. Sie müssen den Bereich der App basierend auf den Antworten definieren, die Sie vom Benutzer auf Ihre Abfragen erhalten haben, und dann entscheiden, welche Funktion für die App-Erstellung am besten geeignet ist.

> [!NOTE]
> Sie müssen über ein gutes Verständnis der [Einstiegspunkte und UI-Elemente verfügen,](../../concepts/extensibility-points.md) die für Ihre App verfügbar sind. Sie müssen auch sicherstellen, dass Sie [Ihre Anwendungsfälle](../../concepts/design/understand-use-cases.md) sorgfältig berücksichtigt haben.

## <a name="choose-the-correct-scope-for-your-app"></a>Auswählen des richtigen Bereichs für Ihre App

Berücksichtigen Sie bei der Auswahl des App-Bereichs Folgendes:

* Eine App kann bereichsübergreifend vorhanden sein.
* App-Funktionen, z. B. Messaging-Erweiterungen, folgen Benutzern in verschiedenen Bereichen.
* Benutzer zögern häufig, Apps zu Teams oder Kanälen hinzuzufügen.
* Gäste können auf Inhalte zugreifen, die in Teams oder Kanälen verfügbar gemacht werden.

Sie können zwischen dem persönlichen Bereich und dem Team- oder Kanalbereich für Ihre App abhängig von folgendem auswählen:

* Stellen Sie im persönlichen Bereich die folgenden Fragen:
  * Gibt es 1:1-Interaktionen mit der App, die aus Datenschutz- oder anderen Gründen erforderlich sind? Beispiel: Überprüfen des Kontostands oder anderer privater Informationen.
  * Wird es eine Zusammenarbeit zwischen Benutzern geben, die möglicherweise keine gemeinsamen Teams haben? Beispiel: Suchen nach bevorstehenden organisationsweiten Ereignissen in einem Unternehmen.
  * Gibt es personalisierte Benachrichtigungen oder Nachrichten, die während der Teams App an einen Benutzer gesendet werden müssen? Beispielsweise Erinnerungen für Genehmigungen oder Registrierungen.
* Stellen Sie für einen freigegebenen Bereich (Team, Kanal oder Chat) die folgenden Fragen:
  * Sind die Informationen, die von der App entweder auf der Registerkarte oder über einen Bot angezeigt werden, für die meisten Mitglieder in einem Team relevant und nützlich? Beispiel: Die App "Scrum".
  * Kann sich der Kontext der App je nach Dem Team ändern, in dem sie hinzugefügt wird? Beispielsweise unterscheiden sich die Aufgaben von Planner in verschiedenen Teams. 
  * Ist es möglich, dass alle Mitglieder in einer Persona, die zusammenarbeiten müssen, Teil eines einzelnen Teams sind? Beispielsweise Agenten, die an einem Ticket arbeiten.

Die folgenden Szenarien unterstützen Sie beim Verständnis der Auswahl von Einstiegspunkten und UI-Elementen, die gut mit Teams App-Funktionen funktionieren:

> [!NOTE]
> Es handelt sich nicht um eine vollständige Liste, sondern hilft Ihnen, einige der Möglichkeiten zu durchdenken, die Ihnen zur Verfügung stehen.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Erstellen, Freigeben und Zusammenarbeit an Elementen in einem externen System

App für Microsoft Teams ist eine hervorragende Möglichkeit, mit Ihren Daten zu interagieren, und es stehen eine Vielzahl von Integrationspunkten zur Auswahl.

* **Messaging-Erweiterungen mit Suchbefehlen:** Durchsuchen externer Systeme und Freigeben der Ergebnisse als interaktive Karte.

* **Messaging-Erweiterungen mit Aktionsbefehlen:** Sammeln sie Informationen, um sie in einen Datenspeicher einzufügen oder erweiterte Suchvorgänge auszuführen.

* **Registerkarten:** Erstellen eingebetteter Weboberflächen zum Anzeigen, Arbeiten mit und Freigeben von Daten.

* **Connectors und Webhooks:** Eine einfache Möglichkeit zum Übertragen von Daten und Senden von Daten aus dem Teams-Client.

* **Aufgabenmodule:** Interaktive modale Formulare von überall aus, wo sie zum Sammeln oder Anzeigen von Informationen benötigt werden.

## <a name="initiate-workflows-and-processes"></a>Initiieren von Workflows und Prozessen

Manchmal benötigen Sie nur eine schnelle Möglichkeit, einen Prozess oder Workflow in einem externen System zu starten.

* **Aktionsbefehle für Messaging-Erweiterungen:** Auslösen von Nachrichten, sodass Ihre Benutzer den Inhalt einer Nachricht schnell an Ihre Webdienste senden können.

* **Aufgabenmodule:** Öffnen Sie sie über eine Registerkarte, einen Bot oder eine Messaging-Erweiterung, um Informationen zu sammeln, bevor Sie einen Workflow initiieren.

* **Unterhaltungs-Bots:** Interagieren Sie mit Ihren Benutzern über Text und Rich-Cards.

* **Ausgehende Webhooks:** Eine gute Wahl für eine einfache Hin- und Her-Interaktion, wenn Sie keinen gesamten Unterhaltungs-Bot erstellen müssen.

## <a name="send-notifications-and-alerts"></a>Senden von Benachrichtigungen und Warnungen

Senden asynchroner Benachrichtigungen und Warnungen an Ihre Benutzer in Teams. Verwenden Sie interaktive Karten, um schnell auf häufig verwendete Aktionen und Links zu zusätzlichen Informationen zuzugreifen.

* **Unterhaltungsbots:** Senden proaktiver Nachrichten an Gruppen, Kanäle oder einzelne Benutzer.

* **Connectors und eingehende Webhooks:** Zulassen, dass ein Kanal Nachrichten abonniert. Mit einem Connector können Benutzer das Abonnement mit einer Konfigurationsseite anpassen.

## <a name="ask-questions-and-get-answers"></a>Fragen stellen und Antworten erhalten

Die Menschen haben Fragen, und Sie haben wahrscheinlich viele der Antworten, die irgendwo gespeichert sind. Leider ist es oft ziemlich schwierig, die beiden zu verbinden.

* **Unterhaltungsbots:** Verarbeitung natürlicher Sprache, KI, maschinelles Lernen und alle Schlüsselwörter. Verwenden Sie einen Bot, der von der intelligenten Cloud unterstützt wird, um Ihre Benutzer mit den antworten zu verbinden, die sie benötigen.

* **Registerkarten:** Betten Sie Ihr vorhandenes Webportal in Teams ein, oder erstellen Sie eine Teams-spezifische Version für hinzugefügte Funktionen.

## <a name="get-social"></a>Soziale Netzwerke abrufen

Eine Plattform für die Zusammenarbeit ist inhärent eine soziale Plattform. Lassen Sie Ihre kreative Seite kostenlos sein und Ihrem Arbeitsplatz etwas Spaß machen. Alle Benutzer müssen in der Lage sein, Witze zu senden, Kudos zu geben, memes zu erhalten, emojis auszusenden oder alles andere, was Ihnen auffällt.

## <a name="think-in-terms-of-a-single-page-app"></a>Denken Sie an eine Einzelseiten-App

Registerkarten sind eingebettete Webseiten. So ziemlich alles, was Sie in einer SPA tun können, können Sie auf einer Registerkarte in Teams tun. Achten Sie darauf, den Bereich zu berücksichtigen. Gruppen- und Kanalregisterkarten sind für freigegebene Erfahrungen und persönliche Registerkarten für persönliche Erfahrungen. Die Liste der Füllungen des Teams wird auf der Kanalregisterkarte und die Liste Ihrer Füllungen auf der persönlichen Registerkarte angezeigt.

## <a name="start-small"></a>Klein starten

Sie sind sich nicht sicher, wo Sie beginnen sollen? Fühlen Sie sich etwas überfordert mit der großartigen Auswahl an Optionen, die Ihnen zur Verfügung stehen? Sie müssen ein Kernfeature Ihrer App auswählen und dort starten. Nachdem Sie ein Gefühl für den Informationsfluss durch die verschiedenen Kontexte in Teams erhalten haben, ist es viel einfacher, eine komplexere Interaktion zu erstellen.

## <a name="put-it-all-together"></a>Alles zusammenstellen

Abgesehen davon kombinieren die besten Apps in der Regel mehrere Features, wodurch eine App erstellt wird, die Benutzer im richtigen Kontext mit der richtigen Funktionalität zur richtigen Zeit einschaltet. Sie dürfen keine Funktionalität an einem Ort erzwingen, zu dem sie nicht gehört. Nur weil Sie über einen guten 1:1-Unterhaltungsbot verfügen, bedeutet dies nicht, dass Sie ihn zu einem Team hinzufügen. Unterschiedliche Erweiterbarkeitspunkte eignen sich für unterschiedliche Dinge und spielen ihre Stärken beim Erstellen einer erfolgreichen App aus.

## <a name="see-also"></a>Siehe auch

[Erstellen Ihrer ersten Microsoft Teams-App](~/get-started/code-samples.md#build-your-first-microsoft-teams-app-overview)
