---
title: Grundlegendes zu Ihren Anwendungsfällen
author: clearab
description: Grundlegendes zu Ihren Anwendungsfällen
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 270771ecc47bbfc03a33d1603f680bc3424989ad
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231617"
---
# <a name="understand-your-use-cases"></a>Grundlegendes zu Ihren Anwendungsfällen

Die Microsoft Teams-Plattform bietet eine Vielzahl von [Erweiterbarkeitspunkten](~/concepts/extensibility-points.md) und Benutzeroberflächenelementen, die Ihre App nutzen kann. Wenn Sie noch nicht genau wissen, was auf der Plattform Teams möglich ist, sollten Sie diesen Artikel zuerst lesen.

Jede Methode der Interaktion mit Ihren Benutzern hat ihre eigenen Stärken und Schwächen. Beim Erstellen einer großartigen Teams-App geht es darum, die richtige Kombination zu finden, um die Anforderungen Ihres Benutzers zu erfüllen. Wenn Sie diese Anforderungen erfüllen, müssen Sie diese zunächst verstehen.

## <a name="what-problem-are-you-trying-to-solve"></a>Welches Problem versuchen Sie zu lösen?

Jede gute App hat ein Kernproblem (oder eine Notwendigkeit), das sie zu lösen versucht – bevor Sie mit dem Erstellen beginnen, müssen Sie das Problem enignen. Im Kern ist Teams eine Plattform für die Zusammenarbeit, sodass Apps, die Probleme mit der Zusammenarbeit lösen wollen, gut geeignet sind. Es handelt sich auch um eine soziale Plattform, ist nativ plattformübergreifende, befindet sich im Zentrum von Office 365 und bietet eine persönliche Canvas, auf der Sie Apps erstellen können. Es gibt eine unglaublich vielzahl von Anforderungen, die mit einer Teams-App gelöst werden können. Stellen Sie einfach sicher, dass Sie wissen, welche Sie lösen möchten.

## <a name="who-are-you-solving-it-for"></a>Für wen lösen Sie es?

Manchmal kann dies offensichtlich sein: "Das Überwachungssystem meines Teams muss Benachrichtigungen an einen anderen Ort senden, wir müssen in der Lage sein, sie wirklich schnell zu besprechen, und keiner von uns möchte unsere E-Mails überprüfen." Manchmal kann Ihre Zielgruppe im Laufe der Zeit anwachsen– "Unser Team ist wirklich neidisch auf unser Benachrichtigungssystem, und jetzt möchten sie die Aktion ergreifen." Wenn Sie wissen, wer Ihre Benutzer sind, können Sie das richtige Verteilungsmodell identifizieren, aber noch wichtiger ist, wie *sie Teams verwenden.* Sind sie in erster Linie Front-Line-Mitarbeiter auf mobilen Clients? Erwarten Sie, dass viele Gastbenutzer Zugriff auf Ihre App benötigen? Verwenden sie Teams und Kanäle oder in erster Linie Gruppenchats? Wie technisch ausgefeilt sind sie? Benötigen Sie eine sorgfältige Einstiegserfahrung, oder werden einige Zeiger dies tun?

Manchmal lautet die Antwort "Wir möchten dieses Problem für alle Benutzer des Teams überall lösen". Wenn dies für Sie der Fall ist, sollten Sie einige Zeit damit verbringen, zu verstehen, was für die Veröffentlichung [in AppSource benötigt wird.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)

## <a name="do-you-need-authentication"></a>Benötigen Sie eine Authentifizierung?

Sie sollten frühzeitig erkennen, ob Sie die dienste, die Sie verfügbar machen, und auf welcher Ebene schützen müssen. Denken Sie daran, dass die Webdienste, die Sie in Ihrer Teams-App verfügbar machen werden, über das Internet öffentlich verfügbar sind. Wenn Sie also sichern müssen, denken Sie darüber nach, wie sie jetzt sind.

## <a name="should-the-entire-app-be-in-teams"></a>Sollte die gesamte App in Teams installiert sein?

Unabhängig davon, ob Sie etwas ganz Neues erstellen oder eine vorhandene Lösung in Teams bringen, ist es wichtig zu entscheiden, ob sich die gesamte App im Client von Teams befindet oder ob es sinnvoll ist, nur einen Teil der Erfahrung mit sich zu bringen. Mit einer Kombination aus Registerkarten, Messagingerweiterungen, Aufgabenmodulen, interaktiven Karten und Unterhaltungsbots können Sie komplexe Apps vollständig in Teams erstellen. Das ist jedoch nicht immer sinnvoll. Denken Sie daran, wer Ihre Benutzer sind, und das Problem, das Sie lösen möchten. Verfügen sie bereits über ein System zur Lösung des großteils des Problems, und Sie müssen nur einen Untersatz der Funktionalität in Teams erweitern? Wenn Sie nur einen Teil Ihrer Lösung integrieren möchten, sollten Sie sich in der Regel auf die Freigabe, Zusammenarbeit sowie das Initiieren und Überwachen von Workflows konzentrieren.

## <a name="what-will-the-onboarding-experience-be-like"></a>Wie sieht die Onboardingerfahrung aus?

Ihre Onboardingerfahrung kann der Unterschied zwischen Erfolg oder Misserfolg für Ihre App sein. Für jede Funktion Ihrer App und für jeden Kontext, in dem diese Funktion installiert werden kann, sollten Sie einen Plan für die Einführung haben. Wie Sie Ihren Unterhaltungsbot einführen, wenn er in einem Kanal mit tausend Personen installiert wird, ist wahrscheinlich anders als bei der Installation in einem 1:1-Chat. Was geschieht, wenn ein Benutzer ihre Registerkarte zum ersten Mal in einem Kanal konfiguriert? Wenn Sie Karten mit einer Messagingerweiterung teilen, ist es sinnvoll, einen kleinen Link zu einer Seite "Weitere Informationen" hinzuzufügen, um Benutzern die weiteren Funktionen Ihrer App zu ermöglichen?

Wenn Sie wissen, wer Ihre Benutzer sind, können Sie die richtige Erfahrung machen. Erwarten Sie, dass die meisten Personen bereits einen Kontext für Ihre App haben oder Ihre Dienste bereits in einem anderen Kontext genutzt haben? Oder kommen sie ohne Vorkenntnisse zu Ihrer App? Stellen Sie Ihre Onboardingerfahrung mit Den wichtigsten Benutzern zusammen.

Denken Sie auch daran, dass Benutzer Ihre App auf unterschiedliche Weise entdecken können – möglicherweise installieren sie sie, oder sie werden in Ihre App eingeführt, wenn sie von einem anderen Teammitglied zum Freigeben von Inhalten verwendet werden. Wenn Sie möchten, dass Ihre App verbreitet wird, sollten Sie nach Möglichkeiten suchen, sich für jeden zu öffnen.

Denken Sie vor allem daran, dass niemand Spam mag. Das Löschen von persönlichen Nachrichten und Kanalnachrichten ist eine gute Möglichkeit, um die Installation schnell zu entsenden!

## <a name="next-steps"></a>Nächste Schritte

* [Ordnen Sie Ihre Verwendungsfälle der Funktionalität zu.](~/concepts/design/map-use-cases.md)
* [Auswählen, wie Ihre App verbreitet werden soll](../deploy-and-publish/overview.md)

## <a name="learn-more"></a>Weitere Informationen

* [Entwerfen effektiver Registerkarten](~/tabs/design/tabs.md)
* [Erstellen beeindruckender Bots](~/bots/design/bots.md)

