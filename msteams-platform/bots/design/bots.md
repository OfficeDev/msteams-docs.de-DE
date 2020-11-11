---
title: Entwurfsrichtlinien für Bots
description: Beschreibt die Richtlinien zum Erstellen von Bots
keywords: Teams-Entwurfsrichtlinien Referenz Framework-Bots im Gespräch
ms.openlocfilehash: 0691c483d12e537772b74abc015d71e1704f88c8
ms.sourcegitcommit: fdb53284a20285f7e8a7daf25e85cb5d06c52b95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "48992638"
---
# <a name="start-talking-with-bots"></a>Gespräch mit Bots beginnen

Bots sind Unterhaltungs-apps, die eine enge oder bestimmte Gruppe von Aufgaben ausführen. Sie bieten Ihnen die Möglichkeit, mit Benutzern zu kommunizieren, auf Ihre Fragen zu Antworten und Sie proaktiv über Änderungen zu informieren. Sie sind eine großartige Möglichkeit, um Sie zu erreichen.

---

## <a name="guidelines"></a>Anleitungen

### <a name="bot-design-guidelines"></a>Richtlinien für bot-Designs

* Bots sollten relevante Benachrichtigungen liefern, wenn Aktivität stattgefunden hat.
* Bots dürfen keine vertraulichen Daten in ein Team, einen Gruppenchat oder eine 1:1-Unterhaltung für eine Zielgruppe pushen, die diese Daten nicht anzeigen sollte.
* Bot-Benachrichtigungen sollten aussagekräftige Daten enthalten, um die Relevanz der Benachrichtigung den Benutzern mitzuteilen.
* Der Ton des bot sollte die Voices für Teams reflektieren, wie in den Richtlinien definiert.
* Bots sollten eine Willkommensnachricht mit erster Ausführungs Erfahrung enthalten, die den Wert des bot und seine primären Funktionen hervorhebt, dies könnte in Form von "Take a Tour", einem interaktiven Tutorial mit Karussell Karten oder "try it"-Schaltflächen erfolgen.
* Der bottext darf keine Rechtschreibfehler oder Grammatikfehler aufweisen.
* Bots müssen eine Reihe von vordefinierten bot-Befehlen bereitstellen, die Aktionen unterstützen.
* Bot-Nachrichten sollten leicht verständlich und umsetzbare sein.
* Bots müssen Fallback-Hilfebefehle bereitstellen, wenn eine Nachricht nicht verstanden wird.
* In Karten eingebettete Formulare, die von einem bot gesendet werden, sollten deterministische Eingaben bereitstellen, die keine sequenzielle Aktualisierung erfordern.
* Bot-Benachrichtigungen sollten auf eine Team-, Gruppen-Chat-oder 1:1-Unterhaltung mit relevanten Inhalten für die Benutzergruppe beschränkt sein.

### <a name="avatars"></a>Avatars

Bot-Avatare in Teams sind wie Sechsecke geformt, sodass die Benutzer schnell erkennen können, dass Sie mit einem bot anstatt mit einer Person sprechen. Sie übermitteln Ihren Avatar als Quadrat, und wir beschneiden ihn für Sie. Wenn es um Avatare geht, empfehlen wir Ihnen, ihre Lesbarkeit von 2 m entfernt und einen höheren Kontrast zu verwenden.

[!include[Avatar image](~/includes/design/bot-avatar-image.html)]

### <a name="buttons"></a>Schaltflächen

Wir unterstützen bis zu sechs Schaltflächen pro Karte. Seien Sie beim Schreiben von Schaltflächentext prägnant, und denken Sie daran, dass die meisten Schaltflächen nur die Aufgabe behandeln sollten, die Ihnen zur Verfügung steht.

### <a name="graphics"></a>Grafik

Grafiken sind eine gute Möglichkeit, eine Geschichte zu erzählen, aber nicht alle bot-Unterhaltungen benötigen Grafiken, also verwenden Sie Sie für maximale Auswirkung.

### <a name="onboarding-users"></a>Onboarding-Benutzer

Es ist wichtig, dass sich Bots selbst vorstellen und übermitteln, was Sie für Benutzer tun können. Dieser *Wert Exchange* hilft Benutzern zu verstehen, was mit dem bot zu tun ist, wo die Einschränkungen liegen können, und, was am wichtigsten ist, hilft Benutzern, die Interaktion mit einem Computer zu tolerieren, der nicht so intuitiv wie eine reale Person sein wird. Darüber hinaus erteilt es die Berechtigung für Benutzerdaten in Exchange für den tatsächlichen Wert, den der Dienst bereitstellt.

#### <a name="welcome-messages"></a>Willkommensnachrichten

Willkommensnachrichten sind die beste Möglichkeit, um den Ton Ihres bot festzulegen und sollten in persönlichen und Team-oder Gruppen Szenarien verwendet werden. In der Nachricht werden die Funktionen des bot und einige gängige Methoden für deren Interaktion erklärt. Verwenden Sie spezifische Funktionsbeispiele wie " *versuchen Sie, Fragen.*..." in einer Aufzählungsliste. Wenn möglich, sollten diese Vorschläge gespeicherte Antworten zurückgeben. Es ist wichtig, dass die Funktionsbeispiele funktionieren, ohne dass sich Benutzer anmelden müssen.
Weitere Anleitungen *finden Sie unter* [Welcome Message Requirements](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-personal-bots-must-always-send-a-welcome-message-on-first-launch) .

#### <a name="tours"></a>Touren

Include a *Take a Tour* -Attribut mit Begrüßungsnachrichten und Antworten auf Benutzereingabe Äquivalent zu " *Hilfe* ". Dies ist die effektivste Möglichkeit, Benutzern zu ermöglichen, zu erfahren, was ein bot tun kann. Karussells in eins-zu-eins-Erlebnissen sind eine hervorragende Möglichkeit, diese Geschichte zu erzählen, einschließlich der Schaltflächen zum *Verknüpfen mit Beispielen* möglicher Antworten wird empfohlen. Tours sind auch großartige Orte, um über die anderen Funktionen einer APP zu sprechen. Sie können beispielsweise Screenshots von Messaging Erweiterungen und Microsoft Teams-Registerkarten hinzufügen.  Benutzer sollten sich nicht für den Zugriff auf und die Verwendung einer Tour anmelden.

Wenn Touren in Team-oder Gruppen Szenarien verwendet werden, sollten Sie in einem Aufgabenmodul geöffnet werden, um den laufenden Unterhaltungen zwischen Benutzern nicht mehr Karten Rauschen hinzuzufügen.

### <a name="responding-to-users-and-failing-gracefully"></a>Reagieren auf Benutzer und fehlgeschlagene ordnungsgemäße

Ihr bot sollte auch auf Dinge wie " *Hallo* ", " *Hilfe* " und " *Danke* " reagieren können, während häufige Rechtschreibfehler und Colloquialisms berücksichtigt werden. Beispiel:

#### <a name="x2713-hello"></a>&#x2713; Hallo

`"Hi"`  `"How are you"`  `"Howdy"`

#### <a name="x2713-help"></a>&#x2713; Hilfe

`"What do you do?"`  `"How does this work?"`  `"What the heck?"`

#### <a name="x2713-thanks"></a>&#x2713; Dank

`"Thank you"`  `"Thankyou"`  `"Thx"`

Ihr bot sollte in der Lage sein, die folgenden Arten von Abfragen und Eingaben zu verarbeiten:

> [!div class="checklist"]
>
> * **Erkannte Fragen**. Dies sind die Fragen, die Sie von Benutzern im Fall eines "besten Szenarios" erwarten.
> * **Erkannte nicht-Fragen**. Abfragen über nicht unterstützte Funktionen und/oder zufällige, nicht verwandte oder profane Einträge.
> * **Unbekannte Fragen** : Eingabe oder Einträge, die unverständlich, bedeutungslos oder Unsinn sind.

Beispiele für bot-Persönlichkeits-und-Antworttypen:

[!include[Bot responses](~/includes/design/bot-responses-table.html)]

> [!TIP]
> Wenn Sie Ihr bot-Skript schreiben, Fragen Sie sich selbst: "wird mein Unternehmen beschämt, wenn eine Antwort auf dem Bildschirm aufgezeichnet und freigegeben wird?"

### <a name="understanding-what-users-are-trying-to-say"></a>Verstehen, was Benutzer zu sagen versuchen

#### <a name="use-a-thesaurus-for-synonyms"></a>Verwenden eines Thesaurus für Synonyme

Verwenden Sie bei Brainstorming-Varianten einen Thesaurus, und rufen Sie Personen aus so vielen verschiedenen Hintergründen ab, die Sie bei der Generierung unterschiedlicher Interpretationen der einzelnen Abfragen unterstützen.

#### <a name="make-use-of-telemetry-and-interviews"></a>Nutzen von Telemetrie und Interviews

Finden Sie heraus, was Benutzer sagen und was ihre Absicht war, als Sie Ihren bot Abfragen. Dies wird ein fortlaufender Prozess, wenn Sie Benutzer an unterschiedlichen Standorten und Unternehmenstypen erhalten. Sie können die Spracherkennung und die beabsichtigte Zuordnung mit dem Sprachverständnis Intelligent Service ([Luis](/azure/cognitive-services/luis/what-is-luis)) optimieren.

### <a name="how-often-should-you-use-your-bot-to-reach-out-to-a-user"></a>Wie oft sollten Sie Ihren bot verwenden, um einen Benutzer zu erreichen?

#### <a name="x2713-when-a-state-has-changed"></a>&#x2713;, wenn sich ein Status geändert hat

Beispiel: Wenn eine Zuordnung als abgeschlossen markiert ist, wenn sich ein Fehler ändert, wenn neue soziale Medien verfügbar sind oder wenn eine Umfrage abgeschlossen wurde.

#### <a name="x2713-when-the-timing-is-right"></a>&#x2713;, wenn das Timing stimmt

Ihr Bot kann wie eine tägliche Zusammenfassung handeln und eine Benachrichtigung an den Benutzer oder Kanal mit einer bestimmten Frequenz senden.

Lassen Sie den Benutzer im Steuerelement. Stellen Sie Benachrichtigungseinstellungen bereit, die Häufigkeit und Priorität umfassen.

[!include[Bot notification](~/includes/design/bot-notification-image.html)]

---

## <a name="using-tabs"></a>Verwenden von Registerkarten

Tabs machen Ihren bot viel funktionaler. Mit Registerkarten können Sie Folgendes erstellen:

### <a name="x2713-a-place-to-host-standing-queries"></a>&#x2713; einer Stelle zum Hosten von ständigen Abfragen

In persönlichen Unterhaltungen zwischen einem bot und einer einzelnen Person können Registerkarten benutzerspezifische Informationen und Listen enthalten. Sie sind auch ein guter Ort, um bot-Antworten auf häufig gestellte Fragen (FAQs) zu verwalten, sodass Benutzer nicht weiter gefragt werden müssen.

### <a name="x2713-a-place-to-finish-a-conversation"></a>&#x2713; eine Stelle zum Abschließen einer Unterhaltung

Sie können eine Verknüpfung mit einer Registerkarte von einer Karte herstellen. Wenn Ihr bot eine Antwort bereitstellt, die einige weitere Schritte erfordert, kann er eine Verknüpfung mit einer Registerkarte herstellen, um die Aufgabe oder den Ablauf abzuschließen. Beispielsweise kann als Antwort auf "wie kann ich mein iPhone formatieren?" eine gute Antwort eine Karte sein, die die ersten Schritte umreißt und eine Schaltfläche für *mehr anzeigen* enthält, die dann den Benutzer zur Registerkarte " *Hilfe* " des bot und zu tiefen Links zu den spezifischen Anweisungen führt.

### <a name="x2713-a-place-to-host-a-settings-page"></a>&#x2713; einen Ort zum Hosten einer Einstellungsseite

Bots sollten über einige Benutzersteuerelemente verfügen. Für viele Bots ist es über eine Chat Schnittstelle zulässig; Diese Einstellungen sind jedoch schwer zu merken. Auf der Registerkarte "Einstellungen" können Sie Benutzereinstellungen anzeigen, Benutzern erlauben, Sie alle gleichzeitig zu ändern, und ist möglicherweise auch ein guter Ausgangspunkte für komplexere bot-Benutzerverhalten.

### <a name="x2713-a-place-to-provide-some-help"></a>&#x2713; ein Ort, um Hilfe zu leisten

Fügen Sie eine Registerkarte hinzu, mit der Benutzer über die Kommunikation mit Ihrem bot informieren. Sie können einen Kontext für die Funktionen oder FAQs bereitstellen.

![Bereitstellen von Hilfe](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> Durch das Einbetten von Teilen Ihrer Website in eine Registerkarte können Benutzer den Kontext einer Unterhaltung bei der Verwendung Ihres Diensts beibehalten. Es entfällt die Notwendigkeit, ihren Dienst in einem Browser zu starten und zwischen apps hin und her zu wechseln.

---

## <a name="bots-in-channels"></a>Bots in Kanälen

Das Aufrufen eines bot in einem Kanal kann durch ausgeführt werden `@mention` . Das Dialogfeld "bot" sollte in Kanälen und Gruppen im Vergleich zu eins-zu-eins-Szenarien eindeutig sein, und es ist generell ratsam, separate Ansätze zu berücksichtigen. Dies gilt insbesondere in den folgenden Fällen:

### <a name="sensitive-data-sent-by-a-bot"></a>Von einem bot gesendete vertrauliche Daten

Während die Benutzer in einem Team dem Dienst bekannt sein können, können die tatsächlichen Benutzerrollen nicht. Dies bedeutet, dass beispielsweise in einem Bildungs Szenario mit Mobbing die Kontaktinformationen von übergeordneten und Kursteilnehmer nicht in einer Team Einstellung freigegeben werden. Stattdessen kann die Nachricht des bot lauten: "zwei Mobbing-Vorfälle sind heute aufgetreten" zusammen mit einer Schaltfläche zum Anzeigen von Details.

Durch das Starten von Details auf einer Webseite oder einem Aufgabenmodul können Benutzeranmeldeinformationen oder Abfragen für einen Index für Benutzerrollen, die mit Aad-Konten verbunden sind, angefordert werden. In diesen beiden Optionen befinden sich die Daten in einem privaten Ansichtsbereich, und es wird kein Datenverlust geben. Wenn dieselben Daten in einem 1:1-Chat zwischen einem Benutzer und dem bot gesendet werden, sind die Daten nur für den Benutzer in diesem Kontext sichtbar und daher sicher, in der bot-Nachricht vollständig angezeigt zu werden. Das Hinzufügen von Benutzern von einem Kanal zu einem 1:1-Chat sollte jedoch vermieden werden, da die erzwungene Navigation stark störend ist.

### <a name="sending-cards-as-a-response-to-interactions"></a>Senden von Karten als Reaktion auf Interaktionen

Beim Senden einer Karussell Karte als Reaktion auf eine *Tour* in einem 1:1-Chat ist es durchaus akzeptabel, das gleiche Muster kann Dutzende oder Hunderte von *Tour-Karussells* in einem aktiven Kanal mit vielen Benutzern ergeben. Um dies zu vermeiden, sollten sekundäre Karten in einem Aufgabenmodul gehostet werden. Dieses Muster hält Benutzer im Kontext mit dem Kanal, hält den Kanal von übermäßigen bot-Antworten sauber und kann optional unterschiedliche Benutzerrollen berücksichtigen, wenn die *Tour* angezeigt wird.

## <a name="useful-tips"></a>Nützliche Tipps

### <a name="x2713-remember-bots-arent-assistants"></a>&#x2713; denken Sie daran, Bots sind keine Assistenten

Im Gegensatz zu Agents, beispielsweise Cortana, fungieren Bots als Spezialisten.

### <a name="x2713-discourage-chitchat"></a>&#x2713; abschrecken von Geplauder

Wenn Ihr bot nicht für Unterhaltungen entwickelt wurde, finden Sie Möglichkeiten, um das Geplauder in Richtung Aufgaben Abschluss umzuleiten.

### <a name="x2713-introduce-some-personality"></a>&#x2713; Einführung einer Persönlichkeit

Halten Sie Ihre bot-Persönlichkeit konsistent mit der Stimme Ihres Produkts. Denken Sie an Ihren bot als sprechen für Ihr Unternehmen.

### <a name="x2713-maintain-tone"></a>&#x2713; Ton beibehalten

Bestimmen Sie, ob Ihr Ton freundlich und leicht sein soll, "nur die Fakten" oder Super schrullig.

### <a name="x2713-encourage-easy-task-flow"></a>&#x2713; einfache Aufgaben Übermittlung fördern

Unterstützung von Multi-Turn-Interaktionen, während immer noch vollständig geformte Fragen zulässt Das antizipieren des nächsten Schritts erleichtert Benutzern das Durchlaufen von Aufgaben Abläufen erheblich.

Wenn ein Benutzer mehrere Schritte zum Ausführen einer Aufgabe ausführt, lassen Sie den bot diesen Schritt durchführen, aber beenden Sie ihn, indem Sie einen schnelleren Pfad vorschlagen. Wenn ein Benutzer beispielsweise mehrere Gesprächsrunden zum Festlegen einer Besprechung genommen hat (indem er zuerst eine Besprechung angibt, dann identifiziert, mit wem, dann die Uhrzeit angibt und dann den Tag angibt), beenden Sie die Unterhaltung mit dem folgenden Vorschlag: Fragen Sie das nächste Mal, ob Sie eine Besprechung mit Bob um 1:00 Morgen planen können.
