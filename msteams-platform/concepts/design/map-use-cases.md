---
title: Ordnen Sie Ihre Anwendungsfälle Teams App-Funktionen zu.
author: clearab
description: Identifizieren Sie, wie die Anwendungsfälle Ihrer App innerhalb der Teams werden können.
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
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Ordnen Sie Ihre Anwendungsfälle Teams App-Funktionen zu.

Nachdem Sie identifiziert *haben,*  wer der Benutzer ist und welches Problem Sie lösen werden, ist es an der Zeit, zu entscheiden, *wie* das Problem gelöst werden soll. *Wer,* *was* und *wie* wird der Prozess des Verstehens und Zuordnens Ihrer Anwendungsfälle zu den Teams abgeschlossen. Sie müssen den Bereich der App basierend auf den Antworten definieren, die Sie vom Benutzer auf Ihre Abfragen erhalten haben, und dann entscheiden, welche Funktion am besten zum Erstellen Ihrer App geeignet ist.

> [!NOTE]
> Sie müssen über ein gutes Verständnis der Einstiegspunkte und [Benutzeroberflächenelemente](../../concepts/extensibility-points.md) verfügen, die für Ihre App verfügbar sind. Sie müssen auch sicherstellen, dass Sie [Ihre Verwendungsfälle sorgfältig geprüft](../../concepts/design/understand-use-cases.md) haben.

## <a name="choose-the-correct-scope-for-your-app"></a>Auswählen des richtigen Bereichs für Ihre App

Berücksichtigen Sie bei der Auswahl des App-Bereichs Folgendes:

* Eine App kann bereichsübergreifend vorhanden sein.
* App-Funktionen, z. B. Messagingerweiterungen, folgen Benutzern über bereiche hinweg.
* Benutzer sind häufig zögerlich, Apps zu Teams oder Kanälen hinzuzufügen.
* Gastbenutzer können auf Inhalte zugreifen, die in Teams oder Kanälen verfügbar gemacht werden.

Abhängig von den folgenden Kriterien können Sie zwischen persönlichem Bereich und Team- oder Kanalbereich für Ihre App wählen:

* Für persönlichen Bereich stellen Sie die folgenden Fragen:
  * Gibt es 1:1-Interaktionen mit der App, die aus Datenschutz- oder anderen Gründen erforderlich sind? Beispiel: Überprüfen des Restbetrags oder anderer privater Informationen.
  * Gibt es eine Zusammenarbeit zwischen Benutzern, die möglicherweise keine gemeinsamen Teams? Beispielsweise das Suchen anstehender organisationsweiter Ereignisse in einem Unternehmen.
  * Gibt es personalisierte Benachrichtigungen oder Nachrichten, die während der gesamten App-Teams an einen Benutzer gesendet werden müssen? Beispielsweise Erinnerungen für Genehmigungen oder Registrierungen.
* Stellen Sie für einen freigegebenen Bereich (Team, Kanal oder Chat) die folgenden Fragen:
  * Sind die informationen, die von der App entweder auf der Registerkarte oder über einen Bot angezeigt werden, für die meisten Mitglieder in einem Team relevant und nützlich? Beispiel: Scrum-App.
  * Kann sich der Kontext der App je nach Team ändern, dem sie hinzugefügt wird? Beispielsweise unterscheiden sich die Aufgaben von Planner in verschiedenen Teams. 
  * Ist es möglich, dass alle Mitglieder in einer Persona, die zusammenarbeiten müssen, Teil eines einzelnen Teams sind? Beispielsweise Agents, die an einem Ticket arbeiten.

Die folgenden Szenarien helfen Ihnen dabei, die Auswahl von Einstiegspunkten und Benutzeroberflächenelementen zu verstehen, die gut mit den funktionen Teams funktionieren:

> [!NOTE]
> Es handelt sich nicht um eine vollständige Liste, sie hilft Ihnen jedoch, einige der ihnen zur Verfügung en nen Möglichkeiten zu durchdenken.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Erstellen, Freigeben und Zusammenarbeit an Elementen in einem externen System

App für Microsoft Teams ist eine hervorragende Möglichkeit, mit Ihren Daten zu interagieren, und es stehen eine Vielzahl von Integrationspunkten zur Auswahl.

* **Messagingerweiterungen mit Suchbefehlen:** Durchsuchen Sie externe Systeme, und geben Sie die Ergebnisse als interaktive Karte weiter.

* **Messagingerweiterungen mit Aktionsbefehlen:** Sammeln von Informationen zum Einfügen in einen Datenspeicher oder ausführen erweiterter Suchen.

* **Registerkarten:** Erstellen eingebetteter Weberfahrungen zum Anzeigen, Arbeiten mit und Freigeben von Daten.

* **Connectors und Webhooks:** Eine einfache Möglichkeit zum Pushen von Daten und Senden von Daten aus dem Teams Client.

* **Aufgabenmodule:** Interaktive modale Formulare von überall, wo Sie sie zum Sammeln oder Anzeigen von Informationen benötigen.

## <a name="initiate-workflows-and-processes"></a>Initiieren von Workflows und Prozessen

Manchmal benötigen Sie nur eine schnelle Möglichkeit, um einen Prozess oder Workflow in einem externen System zu starten.

* **Aktionsbefehle** für Messagingerweiterungen: Auslösen von Nachrichten, sodass Ihre Benutzer den Inhalt einer Nachricht schnell an Ihre Webdienste senden können.

* **Aufgabenmodule:** Öffnen Sie sie über eine Registerkarte, einen Bot oder eine Messagingerweiterung, um Informationen zu sammeln, bevor Sie einen Workflow initiieren.

* **Unterhaltungsbots:** Interagieren Sie mit Ihren Benutzern über Text und Rich Cards.

* **Ausgehende Webhooks:** Eine gute Wahl für eine einfache Hin-und-Her-Interaktion, wenn Sie keinen gesamten Unterhaltungsbot erstellen müssen.

## <a name="send-notifications-and-alerts"></a>Senden von Benachrichtigungen und Warnungen

Senden asynchroner Benachrichtigungen und Benachrichtigungen an Ihre Benutzer in Teams. Verwenden Sie interaktive Karten, um schnellen Zugriff auf häufig verwendete Aktionen und Links zu zusätzlichen Informationen zu ermöglichen.

* **Unterhaltungsbots:** Proaktive Nachrichten an Gruppen, Kanäle oder einzelne Benutzer senden.

* **Connectors und eingehende Webhooks:** Zulassen, dass ein Kanal Nachrichten abonniert. Mit einem Connector können Benutzer das Abonnement mit einer Konfigurationsseite anpassen.

## <a name="ask-questions-and-get-answers"></a>Fragen stellen und Antworten erhalten

Die Personen haben Fragen, und Sie haben wahrscheinlich eine Menge der Antworten erhalten, die an einem anderen Ort gespeichert sind. Leider ist es oft recht schwierig, die beiden zu verbinden.

* **Conversational bots**: Natural language processing, AI, machine learning, and all the buzzwords. Verwenden Sie einen Bot, der von der intelligenten Cloud unterstützt wird, um Ihre Benutzer mit den antworten zu verbinden, die sie benötigen.

* **Registerkarten**: Betten Sie Ihr vorhandenes Webportal in Teams ein, oder erstellen Teams-spezifische Version für zusätzliche Funktionen.

## <a name="get-social"></a>Soziale Netzwerke erhalten

Eine Plattform für die Zusammenarbeit ist inhärent eine soziale Plattform. Lassen Sie Ihre kreative Seite frei und fügen Sie Ihrem Arbeitsplatz etwas Spaß hinzu. Alle Benutzer müssen in der Lage sein, Witze zu senden, Kudos zu geben, memes zu erhalten, einige Emojis oder andere Emojis zu verstreichen.

## <a name="think-in-terms-of-a-single-page-app"></a>Denken Sie an eine einseitige App

Registerkarten sind eingebettete Webseiten. So ziemlich alles, was Sie in einem SPA tun können, können Sie auf einer Registerkarte in Teams. Achten Sie darauf, den Bereich zu beachten. Gruppen- und Kanalregisterkarten sind für freigegebene Erfahrungen und persönliche Registerkarten für persönliche Erfahrungen. Die Liste der Zeugs des Teams wird auf der Kanalregisterkarte angezeigt, und die Liste Ihrer Zeugs wird auf der persönlichen Registerkarte angezeigt.

## <a name="start-small"></a>Klein starten

Nicht sicher, wo sie beginnen soll? Fühlen Sie sich ein wenig überwältigt von der großartigen Auswahl an Optionen, die Ihnen zur Verfügung stehen? Sie müssen ein Kernfeature Ihrer App auswählen und dort beginnen. Nachdem Sie ein Gefühl für den Fluss von Informationen durch die verschiedenen Kontexte in Teams erhalten haben, ist es viel einfacher, eine komplexere Interaktion zu sehen.

## <a name="put-it-all-together"></a>Alles zusammen

Die besten Apps kombinieren in der Regel mehrere Features und erstellen eine App, die Benutzer im richtigen Kontext mit der richtigen Funktionalität zum richtigen Zeitpunkt ansprecht. Sie dürfen keine Funktionalität an einem Ort erzwingen, zu dem sie nicht gehört. Nur weil Sie über einen guten 1:1-Unterhaltungsbot verfügen, bedeutet dies nicht, dass Sie ihn einem Team hinzufügen. Verschiedene Erweiterbarkeitspunkte nen für verschiedene Dinge nen, ihre Stärken für die Erstellung einer erfolgreichen App nutzen.

## <a name="see-also"></a>Siehe auch

[Apps für Microsoft Teams erstellen](../../overview.md)
