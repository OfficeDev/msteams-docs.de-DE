---
title: Tipps und häufig fehlgeschlagene Fälle
description: Beschreibt Tipps für die Übermittlung und die meisten fehlgeschlagenen Richtlinien
keywords: FAQ für Teams veröffentlichen häufig gescheitert häufige Tipps für Tipps
ms.openlocfilehash: ffb472c918a205bdcf921b967269a80fcaa93338
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674419"
---
# <a name="tips-and-frequently-failed-cases"></a>Tipps und häufig fehlgeschlagene Fälle 

In diesem Artikel werden einige der häufigsten Gründe für apps-Fehlerüberprüfung behandelt. Es sollte keine erschöpfende Liste aller potenziellen Probleme mit Ihrer APP sein. Wenn Sie diese Anleitung befolgten, wird die Wahrscheinlichkeit eines erstmaligen Verfalls jedoch erheblich erhöht. Die umfangreiche Liste der Richtlinien finden Sie hier: [AppSource Validation Policies](https://dev.office.com/officestore/docs/validation-policies). Die Richtlinien in Abschnitt 14 der allgemeinen AppSource-Validierungsrichtlinien gelten speziell für Microsoft Teams-apps.

## <a name="tips-for-successful-app-submission"></a>Tipps für die erfolgreiche App-Übermittlung

* Stellen Sie sicher, dass Sie die Version 1.4.1 oder höher des Microsoft Teams-JavaScript-SDK verwenden.
* Nehmen Sie keine Änderungen an Ihrer APP vor, während die Validierung ausgeführt wird. Für diese Vorgehensweise ist eine vollständige erneute Überprüfung Ihrer APP erforderlich.
* Ihre APP darf nicht mehr reagieren, unerwartet beenden oder Programmierfehler enthalten. Wenn ein Problem auftritt, sollte es ordnungsgemäß mit einem gültigen Weg Weiterleiten von Nachrichten an den Benutzer fehlschlagen.
* Ihre APP darf nicht automatisch ausführbaren Code in der Umgebung des Benutzers herunterladen, installieren oder starten. Jeder Download sollte eine explizite Berechtigung des Benutzers suchen.
* Jedes Material, das Sie Ihrer Erfahrung zuordnen, wie Beschreibungen und Support Dokumentationen, muss genau sein. Achten Sie in diesen Materialien auf Rechtschreibung, Zeichensetzung und Grammatik.
* Hilfe und Support: Es wird dringend empfohlen, Hilfe/FAQ-Link für Ihre Teams-APP zu haben und diesen Link in der ersten Ausführung der Benutzeroberfläche bereitzustellen. Für alle persönlichen apps empfehlen wir Ihnen, ihre Hilfeseite als persönliche Registerkarte zur besseren Benutzerfreundlichkeit bereitzustellen.

## <a name="policy-112-sign-up-sign-in-and-sign-out"></a>Richtlinie 11,2: registrieren, anmelden und Abmelden

Beschreibung: apps müssen eine eindeutige, einfache Anmeldung/Abmeldung und (falls erforderlich) Anmelde Erfahrung bereitstellen. Die Benutzeroberfläche muss für alle Funktionen in Ihrer APP erreichbar sein.

* Wenn dem Benutzer eine explizite Anmeldeoption zur Verfügung gestellt wird, muss auch eine Abmeldeoption vorhanden sein (auch dann, wenn die APP die SSO/Silent-Authentifizierung verwendet).
* Die Abmeldeoption muss den Benutzer nur aus der App-Funktion und nicht aus dem Microsoft Teams-Client signieren.
* Jeder Bereich, der über eine Anmeldung verfügt, muss auch über eine Abmeldung verfügen. Die Abmeldeoption sollte den Benutzer mindestens von denselben Funktionen abmelden, bei denen die Anmeldeoption Sie unterzeichnet hat. Wenn beispielsweise die Anmeldeoption den Benutzer sowohl in einer Messaging Erweiterung als auch in einer Registerkarte signiert, muss die Abmeldeoption den Benutzer von der Nachrichten Erweiterung und der Registerkarte abmelden.

* Stellen Sie sicher, dass es immer eine Möglichkeit gibt, das folgende (oder ähnliche) Verhalten umzukehren:
  * Anmeldung => Abmeldung
  * Verknüpfen eines Kontos/Diensts => ein Konto/eine Verbindung herstellen
  * Verbinden eines Kontos/Diensts => Trennen des Kontos/Diensts
  * Autorisieren eines Kontos/Diensts => de/un-Authorisierung des Kontos/Diensts
  * Registrieren eines Kontos/Diensts => Registrieren des Kontos/Diensts
* Wenn Ihre APP ein Konto oder einen Dienst benötigt, müssen Sie dem Benutzer die Möglichkeit geben, sich anzumelden oder die Anmeldung anzufordern. Eine Ausnahme kann für einen Anmeldeprozess angefordert werden, wenn Ihre APP in die Kategorie "Enterprise"-App passt.
* Die Funktion "Anmelden/Abmelden" muss auf mobilen Clients funktionieren. Stellen Sie sicher, dass Sie Ihr Microsoft Teams-JavaScript-SDK auf Version 1.4.1 oder höher aktualisiert haben.

Weitere Informationen zur Authentifizierung finden Sie unter:

* [Authentifizierungs Dokumentation](~/concepts/authentication/authentication.md)
* [Beispiel für die bot-Authentifizierung im Knoten](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Beispiel für Tab-Authentifizierung im Knoten](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Tab/bot-Authentifizierung in C#/.net](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

## <a name="policy-145-microsoft-teams-apps-must-respond-in-a-reasonable-timeframe"></a>Richtlinie 14,5: Microsoft Teams-apps müssen in einem angemessenen Zeitrahmen reagieren.

* 14.5.1: Wenn für Registerkarten eine Antwort auf eine Aktion mehr als drei Sekunden dauert, müssen Sie eine Lade Nachricht oder Warnung bereitstellen.
* 14.5.2: für Bots muss innerhalb von zwei Sekunden eine Antwort auf einen Benutzer Befehl auftreten. Wenn eine längere Verarbeitung erforderlich ist, müssen Sie einen Eingabe Indikator verwenden.
* 14.5.3: bei verfassen-Erweiterungen muss eine Antwort auf einen Benutzer Befehl innerhalb von fünf Sekunden auftreten.

> [!TIP]
> Stellen Sie sicher, dass Sie den Lade Indikator einschließen, wenn die APP zu lange dauert.

## <a name="policy-14153-content-in-a-tab-should-not-have-superfluousunnecessary-ui-aka-ui-chrome-or-layered-navigation"></a>Richtlinien 14.15.3: Inhalte auf einer Registerkarte sollten keine überflüssige/unnötige Benutzeroberfläche (aka: UI Chrome) oder mehrstufige Navigation aufweisen.

Registerkarten sollten fokussierten Inhalt bereitstellen und Benutzeroberflächenelemente vermeiden, die nicht mit diesem Inhalt in Zusammenhangstehen. Im Allgemeinen bezieht sich dies in der Regel auf unnötige geschachtelte/mehrschichtige Navigation, auf eine nicht zusammenhängende oder irrelevante Benutzeroberfläche neben dem Inhalt oder auf Links, die den Benutzer zu Inhalten führen, die nicht mit dem Inhalt der Registerkarte in Zusammenhangstehen. Beispielsweise hat SharePoint die Navigationsmenüs entfernt und nur den Hauptinhalt auf der Registerkarte angezeigt.

![SharePoint-](~/assets/images/faq/web-sp.png)
![Webansicht SharePoint-Registerkartenansicht](~/assets/images/faq/tab-sp.png)

Wenn mehrere Ansichtsoptionen vorhanden sind, sollten Sie ein Tab-Konfigurationsmenü für den Benutzer auswählen. Anstatt beispielsweise ein Menü in die Registerkarte einzubetten, wird das Menü in der Konfigurationsseite von Wide Ideas eingefügt, sodass die aktuelle Registerkartenansicht sauber und fokussiert ist.

![Seite "Wide idea-Konfiguration"](~/assets/images/faq/wideidea.png)

## <a name="policy-14157-bots-must-respond-to-any-command-and-must-not-dead-end-the-user"></a>Richtlinien 14.15.7: Bots müssen auf alle Befehle reagieren und dürfen den Benutzer nicht beenden.

Ihr bot sollte immer ansprechbar sein. Hier sind einige Tipps, die Ihrem bot helfen, intelligent auf Benutzer zu reagieren.

**Befehlsliste verwenden:** Analyse Benutzereingabe oder Absichten der Benutzer vorherzusagen ist hart. Anstatt Benutzer erraten zu lassen, was Ihr bot tun kann, stellen Sie Benutzern eine Liste von Befehlen zur Verfügung, die ihr bot verstehen kann.

![Fluss Befehlsliste](~/assets/images/faq/flow-bot.png)

Geben Sie **einen Help-Befehl ein:** Benutzer geben am ehesten "Hilfe" ein, wenn Sie verloren gehen oder Ihr bot nicht mit den erwarteten Antworten reagiert. Geben Sie einen Hilfebefehl ein, der ihren Wertbeitrag zusammen mit allen gültigen Befehlen bereitstellt.

![Befehl "Flow Help"](~/assets/images/faq/flow-help.png)

**Fügen Sie Hilfeinhalte oder Anleitungen hinzu, wenn Ihr bot verloren geht:** Wenn Sie die Benutzereingabe nicht verstehen, stellen Sie dem Benutzer stattdessen etwas zur Verfügung. Zum Beispiel "es tut mir leid, ich verstehe nicht. Geben Sie "Hilfe" ein, um weitere Informationen zu erhalten. " Reagieren Sie nicht mit einer Fehlermeldung oder einfach "Ich verstehe nicht". Nutzen Sie diese Möglichkeit, um Ihre Benutzer zu unterrichten.

**Überdenken beider Bereiche:** Stellen Sie sicher, dass Ihr bot bei Nennung (@*botname*) in einem Kanal und in persönlichen Unterhaltungen bei Bedarf entsprechende Antworten bereitstellt. Wenn Ihr bot keinen sinnvollen Kontext innerhalb des Bereichs Personal oder Teams bereitstellt, deaktivieren Sie diesen Bereich über das Manifest. (Weitere Informationen `bots` finden Sie unter Block in der [Microsoft Teams Manifest-Schemareferenz](~/resources/schema/manifest-schema.md#bots).)

## <a name="policy-14159-bot-must-send-welcome-messages-on-the-first-launch"></a>Richtlinien 14.15.9: bot muss Begrüßungsnachrichten beim ersten Start senden

Begrüßungsnachrichten stellen die beste Möglichkeit zum Festlegen des Tons dar. Dies ist der erste Interaktions Benutzer mit dem bot. Eine gute Willkommensnachricht kann den Benutzer ermutigen, die APP zu untersuchen, während eine schlechte Verwendung verwechselt wird und Benutzer möglicherweise Interessen verlieren, wenn der Wert der APP nicht sofort angezeigt wird.

### <a name="personal-scope"></a>Persönlicher Bereich

Beim ersten Start von bot sollte der Benutzer eine Willkommensnachricht von dem bot erhalten, sogar bevor er sich anmeldet. Paar Tipps, die Sie beim Entwerfen Ihrer Willkommensnachricht berücksichtigen sollten:

**Machen Sie die Nachricht prägnant und informativ:** Sie Benutzer haben möglicherweise sehr unterschiedliche Erfahrungen und Kenntnisse über Ihre APP. Möglicherweise haben Sie Ihre APP auf einer anderen Plattform verwendet oder wissen nichts über Ihre APP. Sie möchten Ihre Nachricht an alle Zielgruppen anpassen und in einigen Sätzen erklären, was Ihr bot tut und wie Sie mit ihm interagieren. Sie sollten auch den Wert der APP erläutern und erfahren, wie die Benutzer davon profitieren.
![Cafe und ESS-bot](~/assets/images/faq/cafe-bot.png)

**Machen Sie Ihre Nachricht handlungsbereit:** Überlegen Sie, was nach der Installation Ihrer APP das erste ist, was die Benutzer tun sollen. Gibt es einen coolen Befehl, den Sie ausprobieren sollten? Gibt es eine weitere Onboarding-Erfahrung, die Sie kennen sollten? Müssen die Benutzer sich anmelden? Sie können Aktionen auf einer adaptiven Karte hinzufügen oder bestimmte Beispiele wie "versuchen Sie Fragen....", "Dies ist, was ich tun kann..." bereitstellen.

### <a name="team-scope"></a>Team Bereich

Die Dinge sind ein bisschen anders, wenn der bot zum ersten Mal einem Kanal hinzugefügt wird. Normalerweise sollten Sie keine 1:1-Nachricht an alle Benutzer im Team senden, aber der bot sendet möglicherweise eine Willkommensnachricht im Kanal.

## <a name="policy-141510-tab-configuration-ui-should-not-dead-end-the-experience-and-always-provide-a-way-for-a-user-to-continue"></a>Richtlinie 14.15.10: die Benutzeroberfläche für die Registerkartenkonfiguration sollte die Umgebung nicht beenden und immer eine Möglichkeit für einen Benutzer bieten, den Vorgang fortzusetzen.

Ein Benutzer sollte die Konfigurationsumgebung immer fertig stellen können, auch wenn er nicht sofort den gesuchten Inhalt finden kann. Die Konfigurationsumgebung sollte dem Benutzeroptionen zur Verfügung stellen, um den Inhalt zu finden oder eine URL zu fixieren oder neue Inhalte zu erstellen, falls diese nicht vorhanden sind. Der Benutzer sollte die Konfigurationsoberfläche nicht verlassen müssen, um Inhalte zu erstellen, und dann zu Microsoft Teams zurückkehren, um ihn zu fixieren.

![OneNote ermöglicht Benutzern das Einfügen eines OneNote-Links, falls Notizen nicht gefunden werden können.](~/assets/images/faq/tab-onenote-config.png)

![Benutzer können immer einen neuen Plan für den Planer erstellen, falls keines vorhanden sind](~/assets/images/faq/tab-planner-config.png)

![SharePoint ermöglicht es dem Benutzer auch, eine SharePoint-Verknüpfung direkt einzufügen.](~/assets/images/faq/tab-sp-config.png)