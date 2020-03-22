---
title: Tipps und häufig fehlgeschlagene Fälle
description: Beschreibt Tipps für die Übermittlung und die meisten fehlgeschlagenen Richtlinien
author: laujan
ms.author: lajanuar
ms.topic: how to
ms.openlocfilehash: 12d0f39da24fc6850d74c9c78728b6a9b6de587a
ms.sourcegitcommit: 576a4768b835422545cb6b6b3f75dce8318ea02d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "42896520"
---
# <a name="tips-for-a-successful-app-submission"></a>Tipps für eine erfolgreiche App-Übermittlung

In diesem Artikel werden häufige Gründe für die Überprüfung von apps-Fehlern behandelt. Es ist zwar nicht beabsichtigt, eine erschöpfende Liste aller potenziellen Probleme mit Ihrer APP zu sein, aber im Anschluss an dieses Handbuch wird die Wahrscheinlichkeit erhöht, dass Ihre APP-Übermittlung das erste Mal übergeben wird. Eine umfassende Liste der Validierungsrichtlinien *finden Sie unter* [Commercial Marketplace Certification Policies](/legal/marketplace/certification-policies) .

>[!NOTE]
>**[Abschnitt 1140](/legal/marketplace/certification-policies#1140-teams)** ist spezifisch für Microsoft Teams und **[unter Abschnitt 1140,4](https://docs.microsoft.com/legal/marketplace/certification-policies#11404-functionality)** , in dem die Funktionalitätsanforderungen für Teams-apps behandelt werden.

## <a name="validation-guidelines"></a>Validierungsrichtlinien

### <a name="9989-general-considerations"></a>&#9989; allgemeine Überlegungen

*Siehe auch* [Abschnitt 100 – allgemein](/legal/marketplace/certification-policies#100-general)

* Stellen Sie sicher, dass Sie die Version 1.4.1 oder höher des [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js)verwenden.
* Nehmen Sie keine Änderungen an Ihrer APP vor, während der Validierungsprozess ausgeführt wird. Auf diese Weise ist eine vollständige Revalidierung Ihrer APP erforderlich.
* Ihre APP darf nicht mehr reagieren, unerwartet beenden oder Programmierfehler enthalten. Wenn ein Problem auftritt, sollte Ihre APP ordnungsgemäß fehlschlagen und dem Benutzer eine gültige-Weg-weiter-Nachricht bereitstellen.
* Ihre APP darf keinen ausführbaren Code in der Benutzerumgebung automatisch herunterladen, installieren oder starten. Alle Downloads sollten eine explizite Berechtigung des Benutzers suchen.
* Jedes Material, das Sie Ihrer Erfahrung zuordnen, wie Beschreibungen und Support Dokumentationen, muss genau sein. Achten Sie in diesen Materialien auf Rechtschreibung, Zeichensetzung und Grammatik.
* Bereitstellen von Hilfe-und Supportinformationen Es wird dringend empfohlen, dass Ihre APP einen Link zu Hilfe/FAQ für die Benutzeroberfläche mit der ersten Ausführung enthält. Für alle persönlichen apps wird empfohlen, ihre Hilfeseite als persönliche Registerkarte bereitzustellen, um eine bessere Benutzerfreundlichkeit zu erreichen.

### <a name="9989--provide-a-clear-and-simple-sign-insign-out-and-sign-up-experience"></a>&#9989; bieten eine klare und einfache Anmeldung/abmelden und Anmelde Erfahrung

*Siehe auch* [Abschnitt 1100,5 – Kunden Steuerung](/legal/marketplace/certification-policies#11005-customer-control)

* Wenn Ihre APP oder Ihr Add-in von externen Konten oder Diensten abhängt, muss die Anmelde-und Anmelde Erfahrung offensichtlich sein und über alle Funktionen in Ihrer APP erreichbar sein.
* Wenn dem Benutzer eine explizite Anmeldeoption zur Verfügung gestellt wird, muss eine entsprechende Abmeldeoption vorhanden sein (auch dann, wenn die APP die SSO/[Silent-Authentifizierung](~/tabs/how-to/authentication/auth-silent-aad.md)verwendet).
* Die Abmeldeoption darf den Benutzer nur aus der App-Funktion und nicht aus dem Microsoft Teams-Client signieren.
* Die Abmeldeoption muss den Benutzer mindestens aus denselben Funktionen signieren, auf die mit der Anmeldeoption zugegriffen wird. Wenn beispielsweise die Anmeldeoption sowohl eine Messaging Erweiterung als auch eine Registerkarte enthält, muss die Abmeldeoption sowohl die Messaging Erweiterung als auch die Registerkarte einschließen.

* Stellen Sie sicher, dass es immer eine Möglichkeit gibt, das folgende (oder ähnliche) Verhalten umzukehren:
  * Anmelden => abmelden.
  * Verknüpfen eines Kontos/Diensts => Aufheben der Verknüpfung mit einem Konto/Dienst.
  * Verbinden eines Kontos/Diensts => Trennen eines Kontos/Diensts.
  * Autorisieren eines Kontos/Diensts => deaktivieren/verweigern eines Kontos/Diensts.
  * Registrieren eines Kontos/Diensts => Aufheben der Registrierung/kündigen eines Kontos/Diensts.
* Wenn Ihre APP ein Konto oder einen Dienst benötigt, müssen Sie eine Möglichkeit für den Benutzer bereitstellen, sich anzumelden oder eine Anmeldeanforderung zu erstellen. Eine Ausnahme wird möglicherweise erteilt, wenn Ihre APP eine Unternehmensanwendung ist.
* Die Funktion "Anmelden/Abmelden" muss auf mobilen Clients funktionieren. Stellen Sie sicher, dass Sie das [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js) Version 1.4.1 oder höher verwenden.

Weitere Informationen zur Authentifizierung finden Sie unter:

* [Authentifizierungs Dokumentation](../../../authentication/authentication.md)
* [Beispiel für die bot-Authentifizierung im Knoten](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Beispiel für Tab-Authentifizierung im Knoten](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Tab/bot-Authentifizierung in C#/.net](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

### <a name="9989-response-times-must-be-reasonable"></a>&#9989; Antwortzeiten müssen angemessen sein

* **Registerkarten**. Wenn eine Antwort auf eine Aktion mehr als drei Sekunden dauert, müssen Sie eine Lade Nachricht oder eine Warnung angeben.
* **Bots**. Eine Antwort auf einen Benutzer Befehl muss innerhalb von zwei Sekunden auftreten. Wenn eine längere Verarbeitung erforderlich ist, muss Ihre APP einen Eingabe Indikator anzeigen.
* **Verfassen von Erweiterungen**. Eine Antwort auf einen Benutzer Befehl muss innerhalb von fünf Sekunden auftreten.

> [!TIP]
> Stellen Sie sicher, dass Ihre APP einen Lade Indikator oder eine Form von Warnung anzeigt, wenn Ihre APP länger als erwartet reagiert.

### <a name="9989-tab-content-should-not-have-excessive-chrome-or-layered-navigation"></a>&#9989; Registerkarteninhalt sollte keine übermäßige Chrom-oder mehrstufige Navigation aufweisen

* Registerkarten sollten fokussierten Inhalt bereitstellen und unnötige Benutzeroberflächenelemente vermeiden. Im Allgemeinen bezieht sich dies in der Regel auf unnötige geschachtelte/schichtige Navigation, auf eine externe oder irrelevante Benutzeroberfläche neben dem Inhalt oder auf Links, die den Benutzer zu nicht verwandten Inhalten führen. Unten sehen Sie beispielsweise eine Registerkartenansicht, in der Navigationsmenüs ausgelassen werden und nur der Hauptinhalt präsentiert wird:

![SharePoint-](~/assets/images/faq/web-sp.png)
![Webansicht SharePoint-Registerkartenansicht](~/assets/images/faq/tab-sp.png)

* Wenn mehrere Ansichtsoptionen vorhanden sind, sollten Sie ein Tab-Konfigurationsmenü für den Benutzer auswählen. Anstatt beispielsweise ein Menü in die Registerkarte einzubetten, legen Sie das Menü auf der Konfigurationsseite so fest, dass die tatsächliche Registerkartenansicht sauber und fokussiert ist.

![Seite "Wide idea-Konfiguration"](~/assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>Auf dem Konfigurationsbildschirm muss &#9989;-Registerkarte konfiguriert sein.

* Auf dem Konfigurationsbildschirm sollte der Wert der Benutzeroberfläche eindeutig erläutert und die Registerkarte konfiguriert werden.
* Der Konfigurationsprozess sollte nicht die Benutzeroberfläche beenden und immer eine Möglichkeit für Benutzer bieten, den Vorgang fortzusetzen.
* Ein Benutzer sollte die Konfigurationsumgebung immer fertig stellen können, auch wenn er nicht sofort den gesuchten Inhalt finden kann.
* Die Konfigurationsumgebung sollte Optionen für den Benutzer bieten, um den Inhalt zu finden, eine URL zu fixieren oder neue Inhalte zu erstellen, falls diese nicht vorhanden sind.
* Der Benutzer sollte die Konfigurationsoberfläche nicht verlassen müssen, um Inhalte zu erstellen, und dann zu Microsoft Teams zurückkehren, um ihn zu fixieren.

![OneNote ermöglicht Benutzern das Einfügen eines OneNote-Links, falls Notizen nicht gefunden werden können.](~/assets/images/faq/tab-onenote-config.png)

![Benutzer können immer einen neuen Plan für den Planer erstellen, falls keines vorhanden sind](~/assets/images/faq/tab-planner-config.png)

![SharePoint ermöglicht es dem Benutzer auch, eine SharePoint-Verknüpfung direkt einzufügen.](~/assets/images/faq/tab-sp-config.png)

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>&#9989;-Bots müssen immer reaktionsfähig sein und ordnungsgemäß fehlschlagen

Ihr bot sollte auf alle Befehle reagieren und nicht auf den Endbenutzer. Hier sind einige Tipps, die Ihrem bot helfen, intelligent auf Benutzer zu reagieren:

* **Verwenden Sie Befehlslisten**. Das Analysieren von Benutzereingaben oder das Vorhersagen der Benutzerabsicht ist schwierig. Anstatt Benutzer erraten zu lassen, was Ihr bot tun kann, geben Sie eine Liste von Befehlen an, die ihr bot versteht.

![Fluss Befehlsliste](~/assets/images/faq/flow-bot.png)

* **Einschließen eines Hilfebefehls**. Benutzer werden wahrscheinlich "Hilfe" eingeben, wenn Sie verloren gehen oder wenn Ihr bot nicht wie erwartet reagiert. Fügen Sie einen Hilfebefehl ein, der beschreibt, wie der Wert Ihrer APP zusammen mit allen gültigen Befehlen erfahren wird.

![Befehl "Flow Help"](~/assets/images/faq/flow-help.png)

* **Fügen Sie Hilfeinhalte oder Anleitungen hinzu, wenn Ihr bot verloren geht**. Wenn Ihr bot die Benutzereingabe nicht verstehen kann, sollte er eine alternative Aktion vorschlagen. Zum Beispiel: "es tut mir *leid, ich verstehe nicht. Geben Sie "Hilfe" ein, um weitere Informationen zu erhalten. "* Reagieren Sie nicht mit einer Fehlermeldung oder einfach: *"Ich verstehe nicht"*. Nutzen Sie diese Möglichkeit, um Ihre Benutzer zu unterrichten.

* **Überdenken Sie alle Bereiche**. Stellen Sie sicher, dass Ihr bot geeignete Antworten bereitstellt`@*botname*`, wenn Sie in einem Kanal und in persönlichen Unterhaltungen erwähnt werden. Wenn Ihr bot keinen sinnvollen Kontext innerhalb des Bereichs Personal oder Teams bereitstellt, deaktivieren Sie diesen Bereich über das Manifest. (Weitere Informationen `bots` finden Sie unter Block in der [Microsoft Teams Manifest-Schemareferenz](~/resources/schema/manifest-schema.md#bots).)

### <a name="9989-bots-must-send-a-welcome-message-on-first-launch"></a>&#9989; Bots müssen beim ersten Start eine Willkommensnachricht senden

Begrüßungsnachrichten sind die beste Möglichkeit, den Klingelton Ihres bot festzulegen. Dies ist die erste Interaktion, die ein Benutzer mit dem Bot hat. Eine gute Willkommensnachricht kann den Benutzer ermutigen, die APP weiterhin zu erkunden. Wenn die Begrüßung oder einleitende Nachricht verwirrend oder unklar ist, sehen Benutzer den Wert der APP nicht sofort und verlieren ihre Interessen. Die Willkommensnachricht muss Folgendes enthalten:

* Ein Hilfebefehl.
* Der Wert Vorschlag
* Alle gültigen Befehle.

Im folgenden finden Sie einige Überlegungen zum Entwerfen Ihrer Willkommensnachricht:

#### <a name="personal-scope"></a>Persönlicher Bereich

* **Machen Sie Ihre Nachricht prägnant und informativ**. Höchstwahrscheinlich sind die Benutzererfahrung mit und das Wissen über Ihre APP unterschiedlich. Möglicherweise haben Sie Ihre APP auf einer anderen Plattform verwendet oder wissen nichts über Ihre APP. Sie möchten Ihre Nachricht an alle Zielgruppen anpassen und in einigen Sätzen erklären, was Ihr bot tut und wie er mit ihm interagieren kann. Sie sollten auch den Wert der APP erläutern und erfahren, wie die Benutzer davon profitieren.
![Cafe und ESS-bot](~/assets/images/faq/cafe-bot.png)

* **Machen Sie Ihre Nachricht Handlungs**bereit. Denken Sie an das erste, was Benutzer nach der Installation Ihrer APP tun sollen. Gibt es einen coolen Befehl, den Sie ausprobieren sollten? Gibt es eine weitere Onboarding-Erfahrung, die Sie kennen sollten? Müssen die Benutzer sich anmelden? Sie können Aktionen auf einer adaptiven Karte hinzufügen oder bestimmte Beispiele wie *"versuchen Sie Fragen...."*, *"Dies ist, was ich tun kann..."* bereitstellen.

#### <a name="team-scope"></a>Team Bereich

Die Dinge sind ein bisschen anders, wenn der bot zum ersten Mal einem Kanal hinzugefügt wird. Normalerweise sollten Sie keine 1:1-Nachricht an alle Benutzer im Team senden, aber der Bot kann eine Willkommensnachricht im Kanal senden.

> [!div class="nextstepaction"]
> [Weitere Informationen zu Teams-App-Genehmigungsrichtlinien](/legal/marketplace/certification-policies#1140-teams) 
