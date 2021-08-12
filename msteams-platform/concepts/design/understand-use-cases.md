---
title: Grundlegendes zu den Anwendungsfällen Ihrer App
author: heath-hamilton
description: Bei der Planung Ihrer Microsoft Teams-App sollten Sie zunächst verstehen, welche Probleme Ihre App zu lösen versucht.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 5171ce800c09c31486cfddcffcca7069ed81f0bf8d913876acaaaef4144d7bf7
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57703173"
---
# <a name="understand-your-use-cases"></a>Grundlegendes zu Ihren Anwendungsfällen

Die Microsoft Teams-Plattform bietet eine Vielzahl von [Einstiegspunkten und UI-Elementen, die](../../concepts/extensibility-points.md) Ihre App nutzen kann.
> [!NOTE]
> Bevor Sie mit der Erstellung Ihrer Anwendungsfälle beginnen, müssen Sie über ein gutes Verständnis der Teams Funktionen und der Möglichkeiten auf der Teams Plattform verfügen, die sie verwendet.

Jede Interaktionsmethode mit Ihren Benutzern hat ihre Stärken und Schwachstellen. Beim Erstellen einer großartigen Teams App geht es darum, die richtige Kombination zu finden, um die Anforderungen Ihrer Benutzer zu erfüllen. Wenn Sie diese Anforderungen erfüllen, müssen Sie sie zuerst verstehen.

## <a name="understand-the-problem"></a>Verstehen des Problems

Jede gute App hat ein Kernproblem oder eine Notwendigkeit, die sie zu lösen versucht. Bevor Sie mit dem Erstellen einer App beginnen, müssen Sie das Problem erläutern. Im Kern ist Teams eine Plattform für die Zusammenarbeit, sodass Apps, die Lücken bei der Erzielung einer effektiven Zusammenarbeit schließen, gut geeignet sind. Es ist auch eine Plattform für soziale Netzwerke, nativ plattformübergreifend, befindet sich im Mittelpunkt Office 365 und bietet eine persönliche Canvas für Sie zum Erstellen von Apps. In dieser sozialen Plattform gibt es eine Vielzahl von Anforderungen, die mit einer Teams App gelöst werden können. Sie können eine Vielzahl von Problemen lösen, vorausgesetzt, Sie wissen, welches Sie lösen möchten. Stellen Sie vor dem Erstellen einer App relevante Fragen, z. B.:

* Welche Vor- und Nachteile des aktuellen Zustandssystems werden von Ihren Benutzern verwendet?
* Welche Probleme haben Ihre Benutzer ab heute, die Sie behandeln möchten?
* Welche Features oder Funktionen gefällt und schätzen Ihre Benutzer in ihrer aktuellen Vorgehensweise?

## <a name="understand-your-user"></a>Grundlegendes zu Ihrem Benutzer

Verstehen Sie, wer Ihr Benutzer ist, und Sie können das richtige Verteilungsmodell identifizieren, aber noch wichtiger ist, dass es Ihnen hilft, zu identifizieren, wie Benutzer Teams verwenden. Stellen Sie relevante Fragen, z. B.:

* Sind die Benutzer in erster Linie Mitarbeiter im Front-Line-Dienst auf mobilen Clients?
* Erwarten Sie, dass viele Gastbenutzer Zugriff auf Ihre App benötigen?
* Verwenden sie Teams und Kanäle oder hauptsächlich Gruppenchats?
* Wie technisch ausgereift sind Ihre primären Benutzer?
* Benötigen Sie eine sorgfältige Onboarding-Erfahrung oder einige Zeiger?

Manchmal lautet die Antwort: *Wir möchten dieses Problem für alle Teams Benutzer überall lösen.* Wenn dies für Sie der Fall ist, müssen Sie etwas Zeit damit verbringen, [zu verstehen, was erforderlich ist, um in AppSource veröffentlicht zu werden.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)

## <a name="understand-the-limitations-of-the-app"></a>Verstehen der Einschränkungen der App

Wenn Sie die Einschränkungen der Apps hinsichtlich der Datenbarrierefreiheit und der Datenaufbewahrung kennen, können Sie bessere Apps entwerfen. Dies ist wichtig, da sich Informationen darüber, wem die Daten und die Verfügbarkeit von APIs gehören, auf die Lösungsarchitektur auswirken. Stellen Sie auch hier relevante Fragen, z. B.:

* Was sind die Herausforderungen bei der Back-End-Integration der aktuellen App?
* Wer besitzt die Back-End-Daten? In-House oder Drittanbieter.
* Gibt es Firewalls, die sich auf die Funktionsweise der App auswirken?
* Gibt es APIs für den Zugriff auf die Daten, die Sie für die Funktion Ihrer App benötigen? 

## <a name="provide-authentication"></a>Bereitstellen der Authentifizierung

Sie müssen frühzeitig ermitteln, ob Sie die Dienste, die Sie verfügbar machen, und auf welcher Ebene schützen müssen. Denken Sie daran, dass die webdienste, die in Ihrer Teams App verfügbar gemacht werden, über das Internet öffentlich verfügbar sind. Wenn Sie also sicher sein müssen, dass sie jetzt darüber nachdenken. Wenn Sie eine Lösung benötigen, die erfordert, dass Sie Benutzern außerhalb des Mandanten Gastzugriff gewähren, müssen Zugriffseinschränkungen und -berechtigungen platziert werden, um vertrauliche Informationen zu schützen. Sie müssen Apps unter Berücksichtigung der Einschränkungen entwerfen, die mit dem Gastbenutzerzugriff verbunden sind. Stellen Sie daher Fragen, z. B.: 

* Greifen die Benutzer basierend auf ihren Rollen auf unterschiedliche Ansichten von Daten zu?
* Sind personenbezogene Informationen beteiligt?
* Basieren die Interaktionen auch auf den Benutzerrollen?
* Greifen externe Benutzer auf die App zu?

## <a name="decide-what-goes-in-teams"></a>Entscheiden, was in Teams

Unabhängig davon, ob Sie eine neue Lösung erstellen oder eine vorhandene Lösung in Teams bringen, ist es wichtig zu entscheiden, ob sich die gesamte App innerhalb des Teams-Clients befindet. Überprüfen Sie, ob es sinnvoll ist, nur einen Teil der Erfahrung einzubringen. Mit einer Kombination aus Registerkarten, Messaging-Erweiterungen, Aufgabenmodulen, adaptiven Karten und Unterhaltungsbots können Sie komplexe Apps vollständig in Teams erstellen.
Denken Sie daran, wer Ihre Benutzer sind und welche Probleme Sie lösen möchten. Verfügen sie bereits über ein System zur Lösung des großteils des Problems, oder müssen Sie lediglich einen Untersatz der Funktionalität in Teams erweitern? Wenn Sie einen Teil Ihrer Lösung bereitstellen möchten, müssen Sie sich in der Regel auf die Freigabe, Zusammenarbeit, Initiierung und Überwachung von Workflows konzentrieren.

## <a name="plan-the-onboarding-experience"></a>Planen der Onboarding-Erfahrung

Ihre Onboarding-Erfahrung kann der Unterschied zwischen Erfolg oder Fehler für Ihre App sein. Für jede Funktion Ihrer App und jeden Kontext, in dem die Funktion installiert werden kann, müssen Sie einen Plan haben, wie Sie sich selbst einführen. Wie Sie Ihren Unterhaltungs-Bot einführen, wenn er in einem Kanal mit 1.000 Personen installiert wird, ist anders, wenn er in einem 1:1-Chat installiert wird. Was geschieht, wenn ein Benutzer Ihre Registerkarte zum ersten Mal in einem Kanal konfiguriert? Wenn Sie Karten mit einer Messaging-Erweiterung teilen, ist es sinnvoll, einen kleinen Link zu einer Seite mit **weiteren Informationen** hinzuzufügen, um Benutzern die weiteren Möglichkeiten Ihrer App vorzustellen?

Wenn Sie wissen, wer Ihre Benutzer sind, können Sie die richtige Oberfläche erstellen. Erwarten Sie, dass die meisten Benutzer bereits einen Kontext ihrer App haben oder Ihre Dienste bereits in einem anderen Kontext verwendet haben? Kommen sie ohne Vorkenntnisse zu Ihrer App? Gestalten Sie Ihre Onboarding-Erfahrung mit Ihren wichtigsten Benutzern.

Denken Sie daran, dass Benutzer Ihre App auf verschiedene Arten entdecken können. Sie werden möglicherweise installiert, oder sie werden ihrer App eingeführt, wenn ein anderer Benutzer sie zum Freigeben von Inhalten verwendet. Wenn Sie möchten, dass mehr Benutzer Ihre App verwenden, müssen Sie nach Möglichkeiten suchen, sich allen vorzustellen.

Denken Sie vor allem daran, dass niemand Spam mag. Persönliche und Kanalnachrichten sind eine gute Möglichkeit, um schnell uninstalliert zu werden!

## <a name="plan-for-the-future"></a>Planen der Zukunft

Ermitteln Sie, welche neuen Features der Benutzer in der aktuellen Lösung bevorzugen wird. Wenn Sie über eine Roadmap für neue Features verfügen, die der App hinzugefügt werden sollen, sind das Design und die Architektur betroffen.

## <a name="see-also"></a>Weitere Informationen

* [Auswählen, wie Ihre App verbreitet werden soll](../deploy-and-publish/apps-publish-overview.md)
* [Designregisterkarten](../../tabs/design/tabs.md)
* [Entwerfen von Bots](../../bots/design/bots.md)
* [Erstellen Ihrer ersten Microsoft Teams-App](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Zuordnen von Anwendungsfällen](../../concepts/design/map-use-cases.md)
