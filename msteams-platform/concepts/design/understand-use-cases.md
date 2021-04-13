---
title: Grundlegendes zu Ihren Anwendungsfällen
author: clearab
description: Grundlegendes zu Ihren Anwendungsfällen
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: a873c3030ee4ed5f5fc98229c058583e64c38de5
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654279"
---
# <a name="understand-your-use-cases"></a>Grundlegendes zu Ihren Anwendungsfällen

Die Microsoft Teams-Plattform bietet eine Vielzahl von Einstiegspunkten und [Benutzeroberflächenelementen,](../../concepts/extensibility-points.md) die Ihre App nutzen kann.
> [!NOTE]
> Bevor Sie mit dem Erstellen Ihrer Verwendungsfälle beginnen, müssen Sie über ein gutes Verständnis der Funktionen von Teams und deren Verwendung auf der Teams-Plattform verfügen.

Jede Methode der Interaktion mit Ihren Benutzern hat ihre Stärken und Schwächen. Beim Erstellen einer großartigen Teams-App geht es darum, die richtige Kombination zu finden, um die Anforderungen Ihres Benutzers zu erfüllen. Wenn Sie diese Anforderungen erfüllen möchten, müssen Sie sie zuerst verstehen.

## <a name="understand-the-problem"></a>Verstehen des Problems

Jede gute App hat ein Kernproblem oder eine Notwendigkeit, die sie zu lösen versucht. Bevor Sie mit dem Erstellen einer App beginnen, müssen Sie artikulieren, was dieses Problem ist. Im Kern ist Teams eine Plattform für die Zusammenarbeit, sodass Apps, die Lücken beim Erreichen einer effektiven Zusammenarbeit überbrücken, gut geeignet sind. Sie ist auch eine plattformübergreifende Plattform für soziale Netzwerke, befindet sich im Herzen von Office 365 und bietet eine persönliche Canvas zum Erstellen von Apps. In dieser plattform für soziale Netzwerke gibt es eine Vielzahl von Anforderungen, die mit einer Teams-App gelöst werden können. Sie können eine Vielzahl von Problemen lösen, vorausgesetzt, Sie wissen, welches Problem Sie lösen möchten. Stellen Sie vor dem Erstellen einer App relevante Fragen, z. B.:

* Was sind die Vor- und Nachteile des aktuellen Zustandssystems, das von Ihren Benutzern verwendet wird?
* Welche Probleme haben Ihre Benutzer ab heute, die Sie ansprechen möchten?
* Welche Features oder Funktionen mögen und lieben Ihre Benutzer in ihrer aktuellen Art und Weise, diesen Prozess zu tun?

## <a name="understand-your-user"></a>Verstehen Ihres Benutzers

Verstehen Sie, wer Ihr Benutzer ist, und Sie können das richtige Verteilungsmodell identifizieren, aber vor allem hilft es Ihnen, zu identifizieren, wie Benutzer Teams verwenden. Stellen Sie relevante Fragen, z. B.:

* Sind die Benutzer in erster Linie Front-Line-Mitarbeiter auf mobilen Clients?
* Erwarten Sie, dass viele Gastbenutzer Zugriff auf Ihre App benötigen?
* Verwenden sie Teams und Kanäle oder in erster Linie Gruppenchats?
* Wie technisch ausgefeilt sind Ihre primären Benutzer?
* Benötigen Sie eine sorgfältige Onboarding-Erfahrung, oder können einige Zeiger verwendet werden?

Manchmal lautet die Antwort: Wir möchten dieses Problem für *alle Teams-Benutzer überall lösen.* Wenn dies für Sie der Fall ist, sollten Sie einige Zeit damit verbringen, zu verstehen, was für die Veröffentlichung [in AppSource benötigt wird.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)

## <a name="understand-the-limitations-of-the-app"></a>Verstehen der Einschränkungen der App

Wenn Sie die Einschränkungen der Apps im Hinblick auf die Datenbarrierefreiheit und die Datenresidenzanforderungen kennen, können Sie bessere Apps entwerfen. Dies ist wichtig, da informationen darüber, wem die Daten und die Verfügbarkeit von APIs gehört, auswirkungen auf die Lösungsarchitektur haben. Stellen Sie erneut relevante Fragen, z. B.:

* Was sind die Herausforderungen bei der Back-End-Integration der aktuellen App?
* Wem sind die Back-End-Daten zu eigen? In-house oder Drittanbieter.
* Gibt es Firewalls, die sich auf die Funktionsweise der App auswirken?
* Gibt es APIs für den Zugriff auf die Daten, die Sie für die Funktionsweise Ihrer App benötigen? 

## <a name="provide-authentication"></a>Bereitstellen der Authentifizierung

Sie müssen frühzeitig erkennen, ob Sie die dienste, die Sie verfügbar machen, und auf welcher Ebene schützen müssen. Denken Sie daran, dass die in Ihrer Teams-App verfügbar gemachten Webdienste über das Internet öffentlich verfügbar sind. Wenn Sie also sichern müssen, denken Sie jetzt darüber nach. Wenn Sie eine Lösung benötigen, für die Sie Gastzugriff für Benutzer außerhalb des Mandanten bereitstellen müssen, müssen Zugriffseinschränkungen und Berechtigungen zum Schutz vertraulicher Informationen erteilt werden. Sie müssen Apps unter Berücksichtigung der Einschränkungen entwerfen, die mit dem Gastbenutzerzugriff gelten. Stellen Sie daher Fragen, z. B.: 

* Greifen die Benutzer auf unterschiedliche Ansichten von Daten basierend auf ihren Rollen zu?
* Ist piI beteiligt?
* Basieren die Interaktionen auch auf den Benutzerrollen?
* Greifen externe Benutzer auf die App zu?

## <a name="decide-what-goes-in-teams"></a>Entscheiden, was in Teams passiert

Unabhängig davon, ob Sie etwas Neues erstellen oder eine vorhandene Lösung in Teams bringen, ist es wichtig zu entscheiden, ob sich die gesamte App im Teams-Client befindet. Überprüfen Sie, ob es sinnvoll ist, nur einen Teil der Erfahrung ein-/aus zu holen. Mit einer Kombination aus Registerkarten, Messagingerweiterungen, Aufgabenmodulen, adaptiven Karten und Unterhaltungsbots können Sie komplexe Apps vollständig in Teams erstellen.
Denken Sie daran, wer Ihre Benutzer sind und welche Probleme Sie zu lösen versuchen. Verfügen sie bereits über ein System zur Lösung des großteils des Problems, oder müssen Sie lediglich einen Untersatz der Funktionalität auf Teams erweitern? Wenn Sie einen Teil Ihrer Lösung einbinden möchten, müssen Sie sich in der Regel auf die Freigabe, Zusammenarbeit, Initiierung und Überwachung von Workflows konzentrieren.

## <a name="plan-the-onboarding-experience"></a>Planen der Onboardingerfahrung

Ihre Onboardingerfahrung kann der Unterschied zwischen Erfolg oder Misserfolg für Ihre App sein. Für jede Funktion Ihrer App und jeden Kontext, in dem diese Funktion installiert werden kann, müssen Sie einen Plan für ihre Einführung haben. Wie Sie Ihren Unterhaltungsbot einführen, wenn er in einem Kanal mit tausend Personen installiert wird, ist anders, wenn er in einem 1:1-Chat installiert wird. Was geschieht, wenn ein Benutzer ihre Registerkarte zum ersten Mal in einem Kanal konfiguriert? Ist es sinnvoll, wenn Sie Karten mit einer Messagingerweiterung teilen, ist es sinnvoll, einen kleinen Link zu einer Seite mit weiteren Informationen hinzuzufügen, um Benutzern zu helfen, zu erfahren, was Ihre App sonst noch tun kann? 

Wenn Sie wissen, wer Ihre Benutzer sind, können Sie die richtige Erfahrung machen. Erwarten Sie, dass die meisten Personen bereits über einen Kontext ihrer App verfügen oder Ihre Dienste bereits in einem anderen Kontext genutzt haben? Kommen sie ohne Vorkenntnisse zu Ihrer App? Stellen Sie Ihre Onboardingerfahrung mit Ihren wichtigsten Benutzern zusammen.

Denken Sie daran, dass Benutzer Ihre App auf unterschiedliche Weise entdecken können. Möglicherweise werden sie installiert oder in Ihre App eingeführt, wenn sie von einem anderen Benutzer zum Freigeben von Inhalten verwendet wird. Wenn Sie möchten, dass mehr Benutzer Ihre App verwenden, müssen Sie nach Möglichkeiten suchen, sich allen zu stellen.

Denken Sie vor allem daran, dass niemand Spam mag. Das Löschen von persönlichen Nachrichten und Kanalnachrichten ist eine gute Möglichkeit, um die Installation schnell zu entsenden.

## <a name="plan-for-the-future"></a>Planen der Zukunft

Ermitteln Sie, welche neuen Features der Benutzer in der aktuellen Lösung bevorzugt. Wenn Sie über eine Roadmap für neue Features verfügen, die der App hinzugefügt werden sollen, werden der Entwurf und die Architektur betroffen sein.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Auswählen, wie Ihre App verbreitet werden soll](../deploy-and-publish/overview.md)

> [!div class="nextstepaction"]
> [Entwerfen effektiver Registerkarten](../../tabs/design/tabs.md)

> [!div class="nextstepaction"]
> [Entwerfen von tollen Bots](../../bots/design/bots.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Zuordnung ihrer Verwendungsfälle](../../concepts/design/map-use-cases.md)
