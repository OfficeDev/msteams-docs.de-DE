---
title: Ordnen Sie Ihre Anwendungsfälle Teams App-Funktionen zu
author: clearab
description: Identifizieren Sie, wie die Anwendungsfälle Ihrer App innerhalb der Teams-Erfahrung funktionieren können.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 179d0a37d72577c36f2cc44a11a8217cb9f016b2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566110"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Ordnen Sie Ihre Anwendungsfälle Teams App-Funktionen zu

Nachdem Sie festgestellt *haben, wer* der Benutzer ist und *welches* Problem Sie lösen werden, ist es an der Zeit zu entscheiden, *wie* das Problem zu lösen ist. Der *wer*, *was* und *wie* der Prozess des Verstehens und Zuordnens Ihrer Anwendungsfälle zu Teams App-Funktionen abgeschlossen. Sie müssen den Umfang der App basierend auf den Antworten definieren, die Sie vom Benutzer auf Ihre Abfragen erhalten haben, und dann entscheiden, welche Funktion zum Erstellen Ihrer App am besten geeignet ist.

> [!NOTE]
> Sie müssen über ein gutes Verständnis der [Einstiegspunkte und UI-Elemente](../../concepts/extensibility-points.md) verfügen, die für Ihre App verfügbar sind. Sie müssen auch sicherstellen, dass Sie [Ihre Anwendungsfälle](../../concepts/design/understand-use-cases.md) sorgfältig berücksichtigt haben.

## <a name="choose-the-correct-scope-for-your-app"></a>Wählen Sie den richtigen Bereich für Ihre App

Berücksichtigen Sie bei der Auswahl des App-Bereichs Folgendes:

* Eine App kann bereichsübergreifend vorhanden sein.
* App-Funktionen, z. B. Messagingerweiterungen, folgen Benutzern über alle Bereiche hinweg.
* Benutzer sind oft zögerlich, Apps zu Teams oder Kanälen hinzuzufügen.
* Gastbenutzer können auf Inhalte zugreifen, die in Teams oder Kanälen verfügbar gemacht werden.

Sie können je nach Denier zwischen persönlichem Bereich und Team- oder Kanalbereich für Ihre App wählen:

* Stellen Sie für den persönlichen Umfang die folgenden Fragen:
  * Gibt es Einzelinteraktionen mit der App, die aus Datenschutzgründen oder aus anderen Gründen erforderlich sind? Zum Beispiel die Überprüfung des Reststandes oder anderer privater Informationen.
  * Wird es eine Zusammenarbeit zwischen Benutzern geben, die möglicherweise keine gemeinsamen Teams haben? Suchen Sie z. B. anstehende organisationsweite Ereignisse in einem Unternehmen.
  * Gibt es personalisierte Benachrichtigungen oder Nachrichten, die während der gesamten Teams App an einen Benutzer gesendet werden müssen? Beispielsweise Erinnerungen für Genehmigungen oder Registrierungen.
* Stellen Sie für einen freigegebenen Bereich (Team, Kanal oder Chat) die folgenden Fragen:
  * Sind die von der App angezeigten Informationen entweder in der Registerkarte oder über einen Bot relevant und nützlich für die meisten Mitglieder in einem Team? Beispiel: Scrum-App.
  * Könnte sich der Kontext der App je nach team, dem sie hinzugefügt wird, ändern? Beispielsweise unterscheiden sich die Aufgaben von Planner in verschiedenen Teams. 
  * Ist es möglich, dass alle Mitglieder in einer Persona, die zusammenarbeiten müssen, Teil eines einzelnen Teams sind? Beispielsweise Agenten, die an einem Ticket arbeiten.

Die folgenden Szenarien führen Sie beim Verständnis der Auswahl von Einstiegspunkten und UI-Elementen, die mit Teams App-Funktionen gut funktionieren:

> [!NOTE]
> Es ist keine erschöpfende Liste, aber wird Ihnen helfen, einige der Möglichkeiten, die Ihnen zur Verfügung stehen, durchzudenken.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Erstellen, Freigeben und Zusammenarbeiten von Elementen in einem externen System

App for Microsoft Teams ist eine großartige Möglichkeit, mit Ihren Daten zu interagieren und es gibt eine Vielzahl von Integrationspunkten zur Auswahl.

* **Messaging-Erweiterungen mit Suchbefehlen**: Suchen Sie externe Systeme und teilen Sie die Ergebnisse als interaktive Karte.

* **Messagingerweiterungen mit Aktionsbefehlen:** Sammeln Sie Informationen, die in einen Datenspeicher eingefügt werden sollen, oder führen Sie erweiterte Suchvorgänge durch.

* **Registerkarten**: Erstellen Sie eingebettete Web-Erlebnisse zum Anzeigen, Arbeiten mit und Freigeben von Daten.

* **Connectors und Webhooks**: Eine einfache Möglichkeit, Daten zu übertragen und Daten aus dem Teams Client zu senden.

* **Aufgabenmodule**: Interaktive modale Formulare von überall aus, wo Sie sie zum Sammeln oder Anzeigen von Informationen benötigen.

## <a name="initiate-workflows-and-processes"></a>Initiieren von Workflows und Prozessen

Manchmal benötigen Sie nur eine schnelle Möglichkeit, einen Prozess oder Workflow in einem externen System zu starten.

* **Aktionsbefehle für Messagingerweiterungen:** Auslösen von Nachrichten, sodass Ihre Benutzer den Inhalt einer Nachricht schnell an Ihre Webdienste senden können.

* **Task-Module**: Öffnen Sie sie über eine Registerkarte, einen Bot oder eine Messaging-Erweiterung, um Informationen zu sammeln, bevor Sie einen Workflow einleiten.

* **Konversationsbots**: Interagieren Sie mit Ihren Benutzern durch Text und Rich Cards.

* **Outgoing Webhooks**: Eine gute Wahl für eine einfache Hin- und Her-Interaktion, wenn Sie nicht einen ganzen Konversationsbot erstellen müssen.

## <a name="send-notifications-and-alerts"></a>Senden von Benachrichtigungen und Benachrichtigungen

Senden Sie asynchrone Benachrichtigungen und Benachrichtigungen an Ihre Benutzer in Teams. Verwenden Sie interaktive Karten, um schnellen Zugriff auf häufig verwendete Aktionen und Links zu zusätzlichen Informationen zu ermöglichen.

* **Konversationsbots**: Senden Sie proaktive Nachrichten an Gruppen, Kanäle oder einzelne Benutzer.

* **Connectors und eingehende Webhooks**: Erlauben Sie einem Kanal, Nachrichten zu abonnieren. Mit einem Connector können Benutzer das Abonnement mit einer Konfigurationsseite anpassen.

## <a name="ask-questions-and-get-answers"></a>Stellen Sie Fragen und erhalten Sie Antworten

Die Leute haben Fragen und Sie haben wahrscheinlich eine Menge der Antworten irgendwo gespeichert. Leider ist es oft ziemlich schwierig, die beiden zu verbinden.

* **Konversationsbots**: Natürliche Sprachverarbeitung, KI, maschinelles Lernen und alle Schlagworte. Verwenden Sie einen Bot, der von der intelligenten Cloud angetrieben wird, um Ihre Benutzer mit den Antworten zu verbinden, die sie benötigen.

* **Registerkarten**: Betten Sie Ihr vorhandenes Webportal in Teams ein, oder erstellen Sie eine Teams-spezifische Version für zusätzliche Funktionen.

## <a name="get-social"></a>Holen Sie sich soziale

Eine Kollaborationsplattform ist von Natur aus eine soziale Plattform. Lassen Sie Ihre kreative Seite frei sein und fügen Sie etwas Spaß in Ihrem Arbeitsplatz. Alle Benutzer müssen in der Lage sein, Witze zu senden, Kudos zu geben, einige Meme zu bekommen, einige Emojis herauszuschmeisenden, oder irgendetwas anderes, das Ihre Phantasie trifft.

## <a name="think-in-terms-of-a-single-page-app"></a>Denken Sie an eine einseitige App

Registerkarten sind eingebettete Webseiten. So ziemlich alles, was Sie in einem SPA tun können, können Sie in einem Tab in Teams tun. Achten Sie nur auf den Umfang. Gruppen- und Kanalregisterkarten sind für gemeinsame Erlebnisse und persönliche Registerkarten für persönliche Erlebnisse. Die Liste der Dinge des Teams geht auf dem Kanal-Tab und die Liste Ihrer Sachen geht in der persönlichen Registerkarte.

## <a name="start-small"></a>Starten Sie klein

Sie sind sich nicht sicher, wo Sie anfangen sollen? Fühlen Sie sich ein wenig überwältigt von der tollen Vielfalt an Optionen, die Ihnen zur Verfügung stehen? Sie müssen eine Kernfunktion Ihrer App auswählen und dort starten. Nachdem Sie ein Gefühl für den Informationsfluss durch die verschiedenen Kontexte in Teams erhalten haben, ist es viel einfacher, sich eine komplexere Interaktion vorzustellen.

## <a name="put-it-all-together"></a>Setzen Sie alles zusammen

Davon abgesehen, die besten Apps kombinieren in der Regel mehrere Funktionen, eine App zu schaffen, die Benutzer im richtigen Kontext mit der richtigen Funktionalität zur richtigen Zeit einbindet. Sie dürfen keine Funktionalität an einen Ort erzwingen, zu dem sie nicht gehört. Nur weil Sie einen guten Eins-zu-Eins-Gesprächsbot haben, bedeutet das nicht, dass Sie ihn einem Team hinzufügen. Verschiedene Erweiterbarkeitspunkte sind gut für verschiedene Dinge, spielen ihre Stärken für die Schaffung einer erfolgreichen App.

## <a name="see-also"></a>Siehe auch

[Apps für Microsoft Teams erstellen](../../overview.md)
