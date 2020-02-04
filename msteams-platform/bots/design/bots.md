---
title: Entwurfsrichtlinien für Bots
description: Beschreibt die Richtlinien zum Erstellen von Bots
keywords: Teams-Entwurfsrichtlinien Referenz Framework-Bots im Gespräch
ms.openlocfilehash: f59a1e9c280f27567692b4d10341db79d05c3464
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674497"
---
# <a name="start-talking-with-bots"></a>Gespräch mit Bots beginnen

Bots sind Unterhaltungs-apps, die eine enge oder bestimmte Gruppe von Aufgaben ausführen. Sie bieten Ihnen die Möglichkeit, mit Benutzern zu kommunizieren, auf Ihre Fragen zu Antworten und Sie proaktiv über Änderungen zu informieren. Sie sind eine großartige Möglichkeit, um Sie zu erreichen.

---

## <a name="guidelines"></a>Anleitungen

### <a name="avatars"></a>Avatars

Bot-Avatare in Teams sind wie Sechsecke geformt, sodass die Benutzer schnell erkennen können, dass Sie mit einem bot anstatt mit einer Person sprechen. Sie übermitteln Ihren Avatar als Quadrat, und wir beschneiden ihn für Sie. Wenn es um Avatare geht, empfehlen wir Ihnen, ihre Lesbarkeit von 2 m entfernt und einen höheren Kontrast zu verwenden.

[!include[Avatar image](~/includes/design/bot-avatar-image.html)]

### <a name="buttons"></a>Schaltflächen

Wir unterstützen bis zu sechs Schaltflächen pro Karte. Seien Sie beim Schreiben von Schaltflächentext prägnant, und denken Sie daran, dass die meisten Schaltflächen nur die Aufgabe behandeln sollten, die Ihnen zur Verfügung steht.

### <a name="graphics"></a>Grafik

Grafiken sind eine gute Möglichkeit, eine Geschichte zu erzählen, aber nicht alle bot-Unterhaltungen benötigen Grafiken, also verwenden Sie Sie für maximale Auswirkung.

### <a name="responding-to-users-and-failing-gracefully"></a>Reagieren auf Benutzer und fehlgeschlagene ordnungsgemäße

Ihr bot sollte auch auf Dinge wie "Hi", "Help" und "Thanks" reagieren können, während häufige Rechtschreibfehler und Colloquialisms berücksichtigt werden. Zum Beispiel:

#### <a name="x2713-hello"></a>&#x2713; Hallo

`Hi` `how are you` `howdy`

#### <a name="x2713-help"></a>&#x2713; Hilfe

`What do you do?` `How does this work?` `What the heck?`

#### <a name="x2713-thanks"></a>&#x2713; Dank

`Thank you` `thankyou` `thx`

Ihr bot sollte in der Lage sein, die folgenden Arten von Abfragen und Eingaben zu verarbeiten:

* **Erkannte Fragen**: Dies sind die "Best Case"-Fragen, die Sie von Benutzern erwarten.
* **Erkannte nicht-Fragen**: Abfragen über nicht unterstützte Funktionen, zufällige Informationen oder wenn jemand bei Ihrem bot fluchen möchte.
* **Unbekannte Fragen**: unverständliche Eingaben (d. h., Kauderwelsch).

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

In persönlichen Gesprächen zwischen einem bot und einer einzelnen Person können benutzerspezifische Informationen und Listen in Registerkarten untergebracht werden. Sie sind auch ein guter Ort, um bot-Antworten auf häufig gestellte Fragen (FAQs) zu verwalten, sodass Benutzer nicht weiter gefragt werden müssen.

### <a name="x2713-a-place-to-finish-a-conversation"></a>&#x2713; eine Stelle zum Abschließen einer Unterhaltung

Sie können eine Verknüpfung mit einer Registerkarte von einer Karte herstellen. Wenn Ihr bot eine Antwort bereitstellt, die einige weitere Schritte erfordert, kann er eine Verknüpfung mit einer Registerkarte herstellen, um die Aufgabe oder den Ablauf abzuschließen.

### <a name="x2713-a-place-to-provide-some-help"></a>&#x2713; ein Ort, um Hilfe zu leisten

Fügen Sie eine Registerkarte hinzu, mit der Benutzer über die Kommunikation mit Ihrem bot informieren. Sie können einen Kontext für die Funktionen oder FAQs bereitstellen.

![Bereitstellen von Hilfe](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> Durch das Einbetten von Teilen Ihrer Website auf eine Registerkarte kann ein Benutzer den Kontext einer Unterhaltung beibehalten, während dieser den Dienst verwendet. Es entfällt die Notwendigkeit, ihren Dienst in einem Browser zu starten und zwischen apps hin und her zu wechseln.

---

## <a name="best-practices"></a>Bewährte Methoden

### <a name="x2713-bots-arent-assistants"></a>&#x2713; Bots sind keine Assistenten

Im Gegensatz zu Agents, beispielsweise Cortana, fungieren Bots als Spezialisten.

### <a name="x2713-discourage-chitchat"></a>&#x2713; abschrecken von Geplauder

Wenn Ihr bot nicht für Unterhaltungen entwickelt wurde, finden Sie Möglichkeiten, um das Geplauder in Richtung Aufgaben Abschluss umzuleiten.

### <a name="x2713-introduce-some-personality"></a>&#x2713; Einführung einer Persönlichkeit

Halten Sie Ihre bot-Persönlichkeit konsistent mit der Stimme Ihres Produkts. Denken Sie an Ihren bot als sprechen für Ihr Unternehmen.

### <a name="x2713-maintain-tone"></a>&#x2713; Ton beibehalten

Bestimmen Sie, ob Ihr Ton freundlich und leicht sein soll, "nur die Fakten" oder Super schrullig.

### <a name="x2713-encourage-easy-task-flow"></a>&#x2713; einfache Aufgaben Übermittlung fördern

Unterstützung von Multi-Turn-Interaktionen, während immer noch vollständig geformte Fragen zulässt Das antizipieren des nächsten Schritts erleichtert Benutzern das Durchlaufen von Aufgaben Abläufen erheblich.

Wenn ein Benutzer mehrere Schritte zum Ausführen einer Aufgabe ausführt, lassen Sie den bot diesen Schritt durchführen, aber beenden Sie ihn, indem Sie einen schnelleren Pfad vorschlagen. Wenn ein Benutzer beispielsweise mehrere Konversations Schritte durchgeführt hat, um eine Besprechung festzulegen (indem er zuerst eine Besprechung angibt, dann identifiziert, mit wem, dann die Uhrzeit angibt und dann den Tag angibt), beenden Sie die Unterhaltung mit dem folgenden Vorschlag: Fragen Sie das nächste Mal, ob Sie kann eine Besprechung mit Bob um 1:00 Morgen planen.