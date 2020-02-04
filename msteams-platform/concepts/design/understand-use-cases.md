---
title: Grundlegendes zu den Anwendungsfällen
author: clearab
description: Entscheiden, wie Ihre APP verteilt werden soll
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: ef1007c21e79cd69155b64f02d2980bcf6a708b9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674406"
---
# <a name="understand-your-use-cases"></a>Grundlegendes zu den Anwendungsfällen

Die Microsoft Teams-Plattform bietet eine Vielzahl von [Erweiterbarkeitspunkten und Benutzeroberflächenelementen,](~/concepts/extensibility-points.md) die Ihre APP nutzen kann. Wenn Sie nicht bereits ein gutes Verständnis dafür haben, was auf der Microsoft Teams-Plattform möglich ist, sollten Sie diesen Artikel zuerst lesen.

Jede Methode der Interaktion mit ihren Benutzern hat ihre eigenen Stärken und Schwächen. Beim Erstellen einer awesome Teams-App geht es darum, die richtige Kombination zu finden, um die Anforderungen Ihrer Benutzer zu erfüllen. Wenn Sie diese Anforderungen erfüllen möchten, müssen Sie diese zunächst verstehen.

## <a name="what-problem-are-you-trying-to-solve"></a>Welches Problem versuchen Sie zu lösen?

Jede gute APP hat ein Kernproblem (oder müssen), das Sie lösen möchte – bevor Sie mit dem Erstellen beginnen, müssen Sie das Problem artikulieren. In seinem Herzen ist Microsoft Teams eine Plattform für die Zusammenarbeit, sodass apps, die sich mit der Lösung von Zusammenarbeits Problemen besprechen, eine große Größe haben. Es ist auch eine soziale Plattform, nativ plattformübergreifend, liegt im Herzen von Office 365 und bietet eine persönliche Leinwand, auf der Sie Apps erstellen können. Es gibt eine unglaubliche Vielzahl von Anforderungen, die mit einer Teams-App gelöst werden können, stellen Sie einfach sicher, dass Sie verstehen, welche Sie lösen möchten.

## <a name="who-are-you-solving-it-for"></a>Für wen lösen Sie die Lösung?

Dies kann manchmal offensichtlich sein: "das Überwachungssystem meines Teams muss Benachrichtigungen an einen beliebigen Ort senden, wir müssen in der Lage sein, diese wirklich schnell zu besprechen, und keiner von uns möchte unsere e-Mails überprüfen." Manchmal kann Ihre Zielgruppe im Laufe der Zeit wachsen-"unser Schwesterteam ist wirklich eifersüchtig auf unser Warnungssystem, und jetzt möchten Sie in der Aktion." Wenn Sie wissen, wer Ihre Benutzer sind, können Sie das richtige Verteilungsmodell ermitteln, aber noch wichtiger ist, dass Sie die Verwendung von Microsoft *Teams*leichter bestimmen können. Sind Sie in erster Linie Mitarbeiter von Front-Work auf mobilen Clients? Erwarten Sie, dass viele Gastbenutzer Zugriff auf Ihre APP benötigen? Verwenden Sie Teams und Kanäle oder hauptsächlich Gruppenchats? Wie technisch ausgereift sind Sie? Benötigen Sie eine gründliche on-Boarding-Erfahrung oder werden einige wenige Zeiger verwenden?

Manchmal lautet die Antwort: "Wir möchten dieses Problem für alle Benutzer des Teams überall lösen." Wenn dies der Fall ist, sollten Sie einige Zeit damit verbringen, zu verstehen, was für die [Veröffentlichung in AppSource benötigt](~/concepts/deploy-and-publish/appsource/prepare/overview.md)wird.

## <a name="do-you-need-authentication"></a>Benötigen Sie eine Authentifizierung?

Sie sollten frühzeitig erkennen, ob Sie die Dienste, die Sie verfügbar machen, und auf welcher Ebene schützen müssen. Denken Sie daran, dass die Webdienste, die Sie in Ihrer Teams-app verfügbar machen, öffentlich über das Internet zur Verfügung stehen, wenn Sie Sie also sichern müssen, denken Sie darüber nach, wie es jetzt weiter geht.

## <a name="should-the-entire-app-be-in-teams"></a>Sollte die gesamte app in Microsoft Teams sein?

Unabhängig davon, ob Sie etwas ganz neues erstellen oder eine vorhandene Lösung in Microsoft Teams integrieren, ist es wichtig zu entscheiden, ob sich die gesamte APP innerhalb des Teams-Clients befindet oder ob es sinnvoll ist, nur einen Teil der Erfahrung einzubringen. Mit einer Kombination aus Registerkarten, Messaging Erweiterungen, Aufgaben Modulen, interaktiven Karten und Unterhaltungs Bots können Sie komplexe apps vollständig innerhalb von Teams erstellen. Das macht jedoch nicht immer Sinn. Denken Sie daran, wer Ihre Benutzer sind und welches Problem Sie lösen möchten. Verfügen Sie bereits über ein System zur Lösung der meisten Probleme, und Sie müssen lediglich eine Untergruppe der Funktionen in Microsoft Teams erweitern? Wenn Sie in der Regel nur einen Teil ihrer Lösung einbringen möchten, sollten Sie sich auf die Freigabe, Zusammenarbeit und das initiieren und Überwachen von Workflows konzentrieren.

## <a name="what-will-the-onboarding-experience-be-like"></a>Wie sieht die Onboarding-Umgebung aus?

Ihre Onboarding-Erfahrung kann der Unterschied zwischen Erfolg oder Misserfolg für Ihre APP sein. Für jede Funktion Ihrer APP und für jeden Kontext, in dem die Funktion installiert werden kann, sollten Sie einen Plan für die Vorgehensweise bereitstellen. Wie Sie Ihren Unterhaltungs-bot einführen, wenn er in einem Kanal mit tausend Personen installiert wird, ist wahrscheinlich anders als bei der Installation in einem 1:1-Chat. Was geschieht, wenn ein Benutzer die Registerkarte zunächst in einem Kanal konfiguriert? Wenn Sie Karten mit einer Messaging Erweiterung teilen, ist es sinnvoll, eine kleine Verknüpfung zu einer Seite "Weitere Informationen" hinzuzufügen, um Benutzern zu helfen, was Ihre APP sonst noch kann?

Wenn Sie wissen, wer Ihre Benutzer sind, können Sie die richtige Erfahrung machen. Erwarten Sie, dass die meisten Benutzer bereits einen Kontext für Ihre APP haben oder ihre Dienste bereits in einem anderen Kontext verwendet haben? Oder kommen Sie ohne vorheriges Wissen zu Ihrer APP? Machen Sie Ihre Onboarding-Erfahrung mit ihren Hauptbenutzern im Hinterkopf.

Denken Sie auch daran, dass Benutzer Ihre APP auf vielfältige Weise entdecken können-Sie sind es möglicherweise diejenigen, die Sie installieren, oder Sie werden möglicherweise zu ihrer app hinzugefügt, wenn ein anderes Teammitglied es verwendet, um Inhalte freizugeben. Wenn Sie Ihre APP verbreiten möchten, sollten Sie nach Möglichkeiten suchen, sich an alle Personen zu wenden.

Denken Sie vor allem daran, dass niemand Spam mag. Das Strahlen mit persönlichen und Kanal Nachrichten ist ein guter Weg, um schnell auf die schnelle Installation zu kommen!

## <a name="next-steps"></a>Weitere Schritte

* [Zuordnen von Anwendungsfällen zu Funktionen](~/concepts/design/map-use-cases.md)
* [Auswählen, wie Ihre APP verteilt werden soll](~/concepts/deploy-and-publish/apps-publish.md)

## <a name="learn-more"></a>Weitere Informationen

* [Entwerfen effektiver Registerkarten](~/tabs/design/tabs.md)
* [Erstellen erstaunlicher Bots](~/bots/design/bots.md)

