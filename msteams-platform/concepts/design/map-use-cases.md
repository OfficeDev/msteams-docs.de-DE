---
title: Zuordnen von Anwendungsfällen zu App-Funktionen
author: clearab
description: Entscheiden, wie Ihre APP verteilt werden soll
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 5ebfa73df9b4f2c83533a33fbc6366c2c0ccffb4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674408"
---
# <a name="map-your-use-cases-to-teams-app-capabilities"></a>Zuordnen von Anwendungsfällen zu Teams-App-Funktionen

Wenn Sie dies noch nicht getan haben, stellen Sie sicher, dass Sie [Ihre Anwendungsfälle sorgfältig berücksichtigt](~/concepts/design/map-use-cases.md) haben. Sie sollten auch die [Erweiterungspunkte und Benutzeroberflächenelemente verstehen,](~/concepts/extensibility-points.md) die für Ihre app verfügbar sind. Nachdem Sie herausgefunden haben, *was* Sie zu lösen versuchen und für *wen* Sie es lösen, ist es an der Zeit, sich Gedanken darüber *zu machen.*

Im folgenden finden Sie einige gängige Szenarien und eine Auswahl von Erweiterbarkeitspunkten und Benutzeroberflächenelementen, die gut mit Ihnen zusammenarbeiten. Es ist nicht beabsichtigt, eine erschöpfende Liste zu sein, nur um Ihnen dabei zu helfen, einige der Möglichkeiten zu überdenken, die Ihnen und der Teams-Plattform zur Verfügung stehen.

## <a name="create-share-and-collaborate-on-items-in-an-external-system"></a>Erstellen, freigeben und zusammenarbeiten von Elementen in einem externen System

App für Microsoft Teams sind eine großartige Möglichkeit, um mit Ihren Daten zu interagieren, und es gibt eine Vielzahl von Integrationspunkten zur Auswahl.

* Messaging Extensions with Search Commands-externe Systeme durchsuchen und die Ergebnisse als interaktive Karte freigeben.

* Messaging Extensions with Action Commands – sammeln Sie Informationen, die in einen Datenspeicher eingefügt werden sollen, oder führen Sie erweiterte Suchvorgänge durch.

* Tabs – erstellen Sie eingebettete Weberfahrungen zum Anzeigen, arbeiten mit und Freigeben von Daten.

* Connectors und webhooks – eine einfache Möglichkeit zum Pushen von Daten in und zum Senden von Daten aus dem Microsoft Teams-Client.

* Aufgaben Module-interaktive modale Formulare von wo immer Sie Sie zum Sammeln oder Anzeigen von Informationen benötigen.

## <a name="initiate-workflows-and-processes"></a>Initiieren von Workflows und Prozessen

Manchmal benötigen Sie nur eine schnelle Möglichkeit, einen Prozess oder Workflow in einem externen System zu starten.

* Aktionsbefehle für Messaging Erweiterungen – Auslöser aus Nachrichten, sodass Benutzer den Inhalt einer Nachricht schnell an Ihre Webdienste senden können.

* Aufgaben Module – öffnen Sie Sie über eine Registerkarte, einen bot oder eine Messaging Erweiterung, um Informationen vor dem Initiieren eines Workflows zu sammeln.

* Conversational Bots – interagieren Sie mit ihren Benutzern über Text und umfangreiche Karten.

* Ausgehende webhooks – eine gute Wahl für eine einfache hin-und her-Interaktion, wenn Sie keinen ganzen Unterhaltungs-bot erstellen müssen.

## <a name="send-notifications-and-alerts"></a>Senden von Benachrichtigungen und Benachrichtigungen

Senden Sie asynchrone Benachrichtigungen und Warnungen an Ihre Benutzer in Microsoft Teams. Verwenden Sie interaktive Karten, um schnellen Zugriff auf häufig verwendete Aktionen und Links zu zusätzlichen Informationen bereitzustellen.

* Conversational Bots – senden Sie proaktive Nachrichten an Gruppen, Kanäle oder einzelne Benutzer.

* Connectors #a0 eingehenden webhooks – einem Kanal das Abonnieren von Nachrichten erlauben. Mit einem Connector können Benutzer das Abonnement mit einer Konfigurationsseite anpassen.

## <a name="ask-questions-and-get-answers"></a>Fragen stellen und Antworten erhalten

Personen haben Fragen. Sie haben wahrscheinlich viele der Antworten irgendwo gespeichert. Leider ist es oft ziemlich schwierig, die beiden miteinander zu verbinden.

* Conversational Bots – natürliche Sprachverarbeitung, Ai, Maschinelles Lernen, alle Schlagworte. Verwenden Sie einen bot, der von der intelligenten Cloud betrieben wird, um Ihre Benutzer mit den Antworten zu verbinden, die Sie benötigen.

* Tabs: Betten Sie Ihr vorhandenes Webportal in Microsoft Teams ein, oder erstellen Sie eine Teams-spezifische Version für zusätzliche Funktionen.

## <a name="get-social"></a>Get Social

Eine Plattform für die Zusammenarbeit ist inhärent eine soziale Plattform. Lassen Sie Ihre kreative Seite frei sein, und fügen Sie Ihrem Arbeitsplatz Spaß hinzu.

* Alle von Ihnen-Witze senden, Lob geben, einige Meme, werfen Sie einige Emojis oder was sonst noch Streiks Ihre Phantasie.

## <a name="anything-you-can-do-in-a-single-page-app-spa"></a>Alles, was Sie in einer einzelnen Seite-app (Spa) tun können

Registerkarten sind eingebettete Webseiten. So ziemlich alles, was Sie in einem Whirlpool tun können, können Sie auf einer Registerkarte in Microsoft Teams tun. Achten Sie darauf, dass Sie auf Bereichsgruppen-und Kanal Registerkarten für gemeinsame Benutzeroberflächen, persönliche Registerkarten für... persönliche Erlebnisse. Die Liste der Inhalte des Teams geht auf die Registerkarte Kanal, die Liste Ihrer Bestellung wird auf der Registerkarte persönlich angezeigt.

## <a name="start-small"></a>Klein starten

Sie wissen nicht, wo Sie beginnen sollen? Fühlen Sie sich ein wenig überwältigt von der fantastischen Vielfalt an Optionen, die Ihnen zur Verfügung stehen? Ärgern Sie sich nicht, wählen Sie ein Hauptfeature Ihrer APP aus, und beginnen Sie dort. Sobald Sie ein Gefühl für den Informationsfluss durch die verschiedenen Kontexte in Microsoft Teams erhalten haben, ist es wesentlich einfacher, eine komplexere Interaktion zu sehen.

## <a name="putting-it-all-together"></a>Zusammenfassung

Allerdings kombinieren die besten Apps in der Regel mehrere Features und erstellen eine APP, die die Benutzer im richtigen Kontext mit der richtigen Funktionalität zur richtigen Zeit einbindet. Versuchen Sie nicht, die Funktionalität an einen Ort zu zwingen, der ihr nicht gehört – nur weil Sie einen guten eins-zu-eins-bot haben, bedeutet das nicht, dass Sie es einfach einem Team hinzufügen sollten. Unterschiedliche Erweiterbarkeitspunkte sind für verschiedene Dinge geeignet; Spielen Sie mit ihren Stärken und Ihre APP wird glänzen.
