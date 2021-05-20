---
title: Tipps zur App-Übermittlung und häufig fehlgeschlagene Fälle
description: Beschreibt Tipps für eine erfolgreiche Teams-Shop-Einreichung und häufige Gründe für fehlererfolgreiche Einreichungen
ms.topic: reference
localization_priority: Normal
ms.author: lajanuar
keywords: App-Übermittlungstipps häufig fehlgeschlagene Richtlinien zur Validierung von Fällen
ms.openlocfilehash: 50bbd2af3b4c834e2ac4776e1fc7db1d8bf45173
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565245"
---
# <a name="tips-for-a-successful-microsoft-teams-app-submission"></a>Tipps für eine erfolgreiche Microsoft Teams App-Übermittlung

>[!NOTE]
>Diese Seite wird bis Mai 2021 veraltet sein. Weitere Informationen zum erfolgreichen Veröffentlichen Ihrer App finden Sie in den Richtlinien für die [Teams-Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

In diesem Artikel werden häufige Gründe behandelt, warum übermittelte Apps die Validierung fehlschlagen. Obwohl es sich nicht um eine erschöpfende Liste aller potenziellen Probleme mit Ihrer App handelt, erhöht das Befolgen dieses Handbuchs die Wahrscheinlichkeit, dass Ihre App-Übermittlung das erste Mal vergeht. Weitere Informationen finden Sie unter [Zertifizierungsrichtlinien für den kommerziellen Marktplatz](/legal/marketplace/certification-policies) für eine umfassende Liste von Validierungsrichtlinien.

>[!NOTE]
>**[Abschnitt 1140](/legal/marketplace/certification-policies#1140-teams)** ist spezifisch für Microsoft Teams und **[Unterabschnitt 1140.4](/legal/marketplace/certification-policies#11404-functionality)** behandelt Die Funktionsanforderungen für Teams Apps.

## <a name="validation-guidelines--most-failed-test-cases"></a>Validierungsrichtlinien & den meisten fehlgeschlagenen Testfällen

### <a name="9989-general-considerations"></a>&#9989; Allgemeine Erwägungen

* Stellen Sie sicher, dass Sie Version 1.4.1 oder höher des [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js)verwenden.
* Nehmen Sie während des Validierungsprozesses keine Änderungen an Ihrer App vor. Dazu ist eine vollständige Erneutvalidierung Ihrer App erforderlich.
* Ihre App darf sich nicht aufhängen, unerwartet beendet werden oder Programmierungsfehler enthalten. Wenn ein Problem auftritt, muss Ihre App fehlschlagen und dem Benutzer gültige Informationen für den Weg zum Vortritt bereitstellen.
* Ihre App darf nicht automatisch ausführbaren Code in der Benutzerumgebung herunterladen, installieren oder starten. Alle Downloads müssen die ausdrückliche Erlaubnis des Benutzers einholen.
* Alle Materialien, die Sie Ihrer Erfahrung zuordnen, z. B. Beschreibungen und Supportdokumentation, müssen genau sein. Achten Sie in diesen Materialien auf Rechtschreibung, Zeichensetzung und Grammatik.
* Geben Sie Hilfe- und Supportinformationen an. Es wird dringend empfohlen, dass Ihre App einen Hilfe- oder FAQ-Link für die erste Ausführung der Benutzererfahrung enthält. Für alle persönlichen Apps empfehlen wir, Ihre Hilfeseite als persönliche Registerkarte für eine bessere Benutzererfahrung bereitzustellen.
* Alle Apps müssen eine visuelle Tour haben, z. B. **Take a Tour** oder ein App **Guide** im Konfigurationsbildschirm, der über die App-Funktionen und die notwendige Integration an den folgenden Stellen spricht:
    * Die Shop-Eintragsseite (Lange Beschreibung).
    * Registerkartenkonfigurationsbildschirm.
    * Willkommensnachricht für einen Bot.
    * App-Quellmetadaten.
    * Connector-Konfigurationsbildschirm.

* Die visuelle Tour kann ein Video, Screenshot, ein Link zu einer statischen Registerkarte mit App-Details sein. Alle diese Verweise müssen sich innerhalb der Teams Umgebung befinden.

    ![Beispiel App 1 ](../../../../assets/images/faq/Sampleapp1.png) ![ Sample App 2](../../../../assets/images/faq/Sampleapp2.png)

* Erhöhen Sie Ihre App-Versionsnummer im Manifest, wenn Sie Manifeständerungen an Ihrer Übermittlung vornehmen.
* Die App darf Benutzer nicht aus Teams für Kernbenutzerszenarien herausnehmen. Verknüpfungsziele in Apps dürfen nicht mit einem externen Browser verknüpft werden. Verknüpfungsziele müssen mit div-Elementen verknüpft werden, die in Teams z. B. Taskmodulen und Registerkarten enthalten sind. 
* Die Verwendung von Aufgabenmodulen oder Registerkarten wird empfohlen, um Informationen für Benutzer innerhalb Teams anzuzeigen.
* Alle Kern- und Nicht-Kernszenarien müssen in der Teams Umgebung abgeschlossen werden, mit Ausnahme von:
  * Datenschutzrichtlinie
  * Nutzungsbedingungen (TOU)
  * Website-Link
  * Anmeldeprozess

* Persönliche Apps ermöglichen es Benutzern, Inhalte aus einer persönlichen App-Erfahrung mit anderen Teammitgliedern zu teilen.

### <a name="9989-provide-a-clear-and-simple-sign-in-sign-out-and-sign-up-experience"></a>&#9989; Bereitstellung einer klaren und einfachen Anmeldung, Anmeldung und Anmeldung

* Wenn Ihre App oder Ihr Add-In von externen Konten oder Diensten abhängt, muss die Anmelde-, Abmelde- und Anmeldeerfahrung für alle Funktionen in Ihrer App sichtbar und erreichbar sein.
* Wenn dem Benutzer eine explizite Anmeldeoption zur Verfügung gestellt wird, muss eine entsprechende Abmeldeoption vorhanden sein (auch wenn die App [eine automatische Authentifizierung](../../../../tabs/how-to/authentication/auth-silent-aad.md)verwendet).
* Die Abmeldeoption darf den Benutzer nur aus der Funktion Ihrer App und nicht aus dem Teams Client abmelden.
* Die Abmeldeoption muss den Benutzer mindestens von denselben Funktionen abmelden, auf die mit der Anmeldeoption zugegriffen wird. Wenn die Anmeldeoption z. B. sowohl die Messagingerweiterung als auch die Registerkarte enthält, muss die Abmeldeoption sowohl die Messagingerweiterung als auch die Registerkarte enthalten.

* Stellen Sie sicher, dass es immer eine Möglichkeit gibt, die folgenden (oder ähnlichen) Verhaltensweisen umzukehren:
  * Anmelden => Abmelden.
  * Verknüpfen eines Kontos/Dienstes => die Verknüpfung eines Kontos/Dienstes aufzulinken.
  * Verbinden ein Konto/Dienst => trennen Sie ein Konto/dienst.
  * Autorisieren eines Kontos/Dienstes => deautorisieren/verweigern eines Kontos/Dienstes.
  * Registrieren eines Kontos/Dienstes => abmelden/abmelden ein Konto/Dienst.
* Wenn Ihre App ein Konto oder einen Dienst erfordert, müssen Sie dem Benutzer eine Möglichkeit bieten, sich anzumelden oder eine Anmeldeanforderung zu erstellen. Eine Ausnahme kann gewährt werden, wenn Ihre App eine Lizenz für die Verwendung benötigt. Geben Sie in solchen Szenarien klare Anweisungen für die Anmeldung eines neuen Benutzers an.
* Geben Sie einem neuen Benutzer eine klare Anleitung zum Wegvorweg, wie Sie sich anmelden, um Ihre App-Dienste zu verwenden. Wenn kein bereiter Anmeldelink verfügbar ist, geben Sie präzise Anleitungen in den folgenden Bereichen:

> [!div class="checklist"]
>
> * im Beschreibungsbereich Ihrer App.
> * in der Begrüßungsnachricht Ihrer App.
> * in der Hilfenachricht Ihrer App.
> * in dem Fenster, in dem Sie einen Benutzer bitten, sich bei Ihren Diensten anzumelden.

* Apps ohne einfachen Anmeldeablauf müssen auch eine Hilferegisterkarte oder einen Link zu einer Webseite enthalten, auf der ein neuer Benutzer detaillierte Anleitungen zum Konfigurieren Ihrer Teams-App sehen kann. Geben Sie detaillierte Informationen an, um sicherzustellen, dass ein neuer Benutzer nicht blockiert wird, wenn Sie Ihre App zum ersten Mal ausprobieren.
* Die Anmelde- und Abmeldefunktion muss auf mobilen Clients funktionieren. Stellen Sie sicher, dass Sie die [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js) Version 1.4.1 oder höher verwenden.

Weitere Informationen zur Authentifizierung finden Sie unter:

* [Authentifizierungsdokumentation](../../../authentication/authentication.md)
* [Bot-Authentifizierungsbeispiel in Node](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Tabauthentifizierungsbeispiel in Knoten](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Tab/Bot-Authentifizierung in C-/.NET](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

### <a name="9989-response-times-must-be-reasonable"></a>&#9989; Reaktionszeiten müssen angemessen sein

* **Tabs**. Wenn eine Antwort auf eine Aktion mehr als drei Sekunden dauert, müssen Sie eine Lademeldung oder Warnung bereitstellen.
* **Bots**. Eine Antwort auf einen Benutzerbefehl muss innerhalb von zwei Sekunden erfolgen. Wenn eine längere Verarbeitung erforderlich ist, muss Ihre App eine Eingabeanzeige anzeigen.
* **Erweiterungen erstellen**. Eine Antwort auf einen Benutzerbefehl muss innerhalb von fünf Sekunden erfolgen.

> [!TIP]
> Stellen Sie sicher, dass Ihre App eine Ladeanzeige oder eine Art Warnung anzeigt, wenn die Antwort Ihrer App länger dauert als erwartet.

### <a name="9989-tab-content-must-not-have-excessive-chrome-or-layered-navigation"></a>&#9989; Tab-Inhalt darf keine übermäßige Chrom- oder mehrschichtige Navigation aufweisen

* Registerkarten müssen fokussierten Inhalt bereitstellen und unnötige UI-Elemente vermeiden. Dies bezieht sich in der Regel auf unnötige verschachtelte oder mehrschichtige Navigation, eine fremde oder irrelevante Benutzeroberfläche neben dem Inhalt oder links, die den Benutzer zu nicht verwandten Inhalten führen. In der folgenden Registerkartenansicht werden beispielsweise Navigationsmenüs ausgelassen und nur der Hauptinhalt angezeigt:

![SharePoint Webansicht](../../../../assets/images/faq/web-sp.png)  
![SharePoint Registerkartenansicht](../../../../assets/images/faq/tab-sp.png)

* Tabs müssen in der Natur leicht sein und dürfen keine komplexe Navigation enthalten.
* Kanalregisterkarten mit komplexen Bearbeitungsfunktionen innerhalb der App müssen die Editoransicht in einem Multifenster anstelle einer Registerkarte öffnen.
* Kanalregisterkarten dürfen keine App-Leiste mit Symbolen in der linken Schiene bereitstellen, die mit der Hauptnavigation Teams.
* Tabs dürfen keine App-Leiste mit Symbolen in der linken Schiene darstellen, die mit dem Haupt Teams Navigation in Konflikt stehen.
* Registerkarten mit komplexen Bearbeitungsfunktionen innerhalb der App müssen die Editoransicht in einem Multifenster und nicht auf der Registerkarte öffnen.
* Wenn mehrere Ansichtsoptionen vorhanden sind, sollten Sie ein Registerkartenkonfigurationsmenü verwenden, aus dem der Benutzer auswählen kann. Anstatt beispielsweise ein Menü in die Registerkarte einzubetten, legen Sie das Menü auf der Konfigurationsseite ein, damit die tatsächliche Registerkartenansicht sauber und fokussiert ist.
* Fügen Sie eine *Hilferegisterkarte* als statische Registerkarte ein, um Benutzern zu beraten, wie Sie Ihre App konfigurieren, registrieren und verwenden können.
* Fügen Sie eine *Einstellungen* Registerkarte ein, die über den App-Header verfügbar ist.

![Breite Ideenkonfigurationsseite](../../../../assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>&#9989; Tab-Konfiguration muss im Konfigurationsbildschirm erfolgen

* Der Konfigurationsbildschirm muss den Wert der Erfahrung und die Konfiguration der Registerkarte klar erläutern.
* Der Konfigurationsprozess muss den Benutzern immer eine Möglichkeit bieten, fortzufahren, und darf die Benutzererfahrung nicht beenden. Zeigen Sie z. B. kein leeres Board an, nachdem der Benutzer die Registerkarte konfiguriert hat.
* Der Benutzeranmeldevorgang muss Teil des Konfigurationsprozesses sein. Stellen Sie sicher, dass sie in der Registerkartenbenutzeroberfläche abgeschlossen wird. Nachdem der Benutzer die Konfiguration abgeschlossen und die Registerkarte geladen hat, ist keine weitere Aktion erforderlich.
* Zeigen Sie nicht Die gesamte Webseite im Popupfenster für die Anmeldekonfiguration an.
* Ein Benutzer muss immer in der Lage sein, die Konfigurationsumgebung zu beenden, auch wenn er den gesuchten Inhalt nicht sofort finden kann.
* Die Konfigurationsumgebung muss Optionen für den Benutzer bieten, um seinen Inhalt zu finden, eine URL anzuheften oder neue Inhalte zu erstellen, wenn er nicht vorhanden ist.
* Die Konfigurationserfahrung muss im Teams Kontext bleiben. Der Benutzer sollte die Konfigurationsumgebung nicht verlassen müssen, um Inhalte zu erstellen, und dann zu Teams zurückkehren, um sie anzuheften.
* Verwenden Sie den verfügbaren Ansichtsfensterbereich effizient. Verschwenden Sie es nicht mit riesigen Logos innerhalb der Konfiguration Pop-up.

![OneNote ermöglicht es Benutzern, einen OneNote Link einzufügen, falls Notizen nicht gefunden werden können](../../../../assets/images/faq/tab-onenote-config.png)

![Benutzer können immer einen neuen Plan auf Planer erstellen, falls es keine vorhandenen gibt](../../../../assets/images/faq/tab-planner-config.png)

![SharePoint ermöglicht es dem Benutzer auch, einen SharePoint Link direkt einzufügen](../../../../assets/images/faq/tab-sp-config.png)

### <a name="9989-tabs-in-channel---member-access"></a>&#9989; Tabs im Kanal - Member-Zugriff

* Eine Registerkarte, die von einem Mitglied in einem Kanalbereich konfiguriert wurde, muss für die anderen Mitglieder zugänglich sein, ohne dass das Mitglied, das die Registerkarte konfiguriert hat, Berechtigungen einholen muss.
* Die App muss die Berechtigungsverwaltungsoptionen im Voraus bereitstellen, wenn die Registerkarte für die private oder eingeschränkte Verwendung bestimmt ist oder Berechtigungen des Mitglieds benötigt, das die Registerkarte konfiguriert hat.

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>&#9989; Bots müssen immer ansprechbar sein und anmutig scheitern

Ihr Bot muss auf jeden Befehl reagieren und darf den Benutzer nicht in die Sackgasse geraten. Hier sind einige Tipps, die Ihrem Bot helfen, intelligent auf Benutzer zu reagieren:

* **Verwenden Sie Befehlslisten**. Die Analyse von Benutzereingaben oder die Vorhersage der Benutzerabsicht ist schwierig. Anstatt Benutzer erraten zu lassen, was Ihr Bot tun kann, stellen Sie eine Liste von Befehlen bereit, die Ihr Bot versteht.

![Flow Befehlsliste](../../../../assets/images/faq/flow-bot.png)

* **Fügen Sie einen Hilfebefehl ein.** Benutzer geben wahrscheinlich "Hilfe" ein, wenn sie verloren gehen oder wenn Ihr Bot nicht wie erwartet reagiert. Fügen Sie einen Hilfebefehl ein, der beschreibt, wie der Wert Ihrer App zusammen mit allen gültigen Befehlen angezeigt wird.

![Flow Hilfebefehl](../../../../assets/images/faq/flow-help.png)

* **Fügen Sie Hilfeinhalte oder Anleitungen ein, wenn Ihr Bot verloren geht.** Wenn Ihr Bot die Benutzereingabe nicht verstehen kann, muss er eine alternative Aktion vorschlagen. Zum Beispiel: *"Es tut mir leid, ich verstehe es nicht. Geben Sie "Hilfe" ein, um weitere Informationen zu erhalten."* Reagieren Sie nicht mit einer Fehlermeldung oder einfach mit *"Ich verstehe nicht"*.

### <a name="9989-help-command-response"></a>&#9989; Hilfebefehlsantwort

* Der Hilfebefehl muss präzise sein, und die App-Antworten müssen in einem adaptiven Kartenformat mit einem umsetzbaren Inhalt für mindestens sechs Befehle vorliegen.
* Wenn eine App über weniger als sechs Befehle verfügt, überprüfen Sie, ob alle Befehle auf der adaptiven Karte vorhanden sind.

  ![Hilfebefehlsbeispiel](../../../../assets/images/faq/helpcommand.png)

* **Verwenden Sie adaptive Karten und Aufgabenmodule, um Ihre Bot-Antwort klar und umsetzbar** 
 zu machen [Adaptive Karten mit Schaltflächen, die Task-Module aufrufen,](/task-modules-and-cards/task-modules/task-modules-bots.md) verbessern die Bot-Benutzererfahrung. Diese Karten und Schaltflächen sind einfacher in einem mobilen Gerät zu verwenden, im Gegensatz zu Ihrem Benutzer, der die Befehle eingibt. Auch Bot-Antworten dürfen nicht textlich mit langem Text sein. Bots müssen adaptive Karten und Aufgabenmodule anstelle von Konversationschat-basierten Benutzeroberfläche und langen Textantworten verwenden.

* **Denken Sie alle Bereiche durch**. Stellen Sie sicher, dass Ihr Bot angemessene Antworten bietet, wenn erwähnt ( `@*botname*` ) in einem Kanal und in persönlichen Gesprächen. Wenn Ihr Bot keinen aussagekräftigen Kontext innerhalb des persönlichen bereichs oder des Teams bietet, deaktivieren Sie diesen Bereich über das Manifest. (Siehe den `bots` Block im [Microsoft Teams Manifestschemaverweis](../../../../resources/schema/manifest-schema.md#bots).)

* **Schließen Sie Team, Gruppenchat oder 1:1-Unterhaltung ein.** Bot-Benachrichtigungen müssen ein Team, einen Gruppenchat oder eine Einzelunterhaltung mit relevanten Inhalten für Ihre Zielgruppe enthalten.

* **Drücken Sie keine sensiblen Daten**. Bots dürfen keine vertraulichen Daten an ein Team, einen Gruppenchat oder eine 1:1-Unterhaltung übertragen, bei der eine Zielgruppe diese Daten nicht anzeigen darf.

* **Geben Sie eine Willkommensnachricht**. Bot muss eine FRE-Willkommensnachricht bereitstellen, die ein interaktives Tutorial mit Karussellkarten oder "Try it"-Tasten enthält, um das Engagement zu fördern.

### <a name="9989-personal-bots-must-always-send-a-welcome-message-on-first-launch"></a>&#9989; Persönliche Bots müssen beim ersten Start immer eine Willkommensnachricht senden

Eine Willkommensnachricht ist der beste Weg, um den Ton für Ihren persönlichen Chat-Bot zu setzen. Dies ist die erste Interaktion, die ein Benutzer mit dem Bot hat. Eine gute Willkommensnachricht kann den Benutzer dazu ermutigen, die App weiter zu erkunden. Wenn die Begrüßungs- oder Einführungsnachricht verwirrend oder unklar ist, sehen Benutzer den Wert der App nicht sofort und verlieren das Interesse.
Im folgenden Abschnitt finden Sie Anforderungen an Begrüßungsnachrichten:

> [!Note]
> Eine Willkommensnachricht ist optional für einen Channel-Bot.

### <a name="welcome-message-requirements"></a>Anforderungen an die Begrüßungsnachricht

* Fügen Sie ein Wertversprechen in die Begrüßungstour ein.
* Stellen Sie Anleitungen für die Verwendung der App bereit.
* Geben Sie Anleitungen zum Anmelden und Konfigurieren Ihrer App an.
* Präsentieren Sie leicht lesbaren Text und einen einfachen Dialog – vorzugsweise eine Karte mit einer umsetzbaren Willkommens-Tour-Taste, die ein Aufgabenmodul lädt.
* Halten Sie es einfach und nutzbar mit Tasten und Karten - vermeiden Sie langen Text, chatty Dialog.
* Fügen Sie adaptive Karten und Schaltflächen ein, um die Willkommensnachricht nutzbarer zu machen.
* Rufen Sie die Begrüßungsnachricht mit einem Ping auf, nicht mit zwei oder mehr gleichzeitigen Pings.
* Eine Willkommensnachricht darf nur dem Benutzer angezeigt werden, der die App konfiguriert hat, vorzugsweise in einem persönlichen 1:1-Chat.
* Persönliche Apps müssen einem Benutzer immer eine Willkommensnachricht bieten.
* Senden Sie niemals einen persönlichen Chat an jedes Teammitglied; es gilt als Spam.
* Senden Sie die Begrüßungsnachricht niemals mehr als einmal. Das Wiederholen derselben Begrüßungsnachricht in regelmäßigen Abständen ist nicht zulässig und gilt als Spamming.

#### <a name="avoid-welcome-message-spamming"></a>Vermeiden Sie Begrüßungsnachrichten-Spamming

* **Kanalnachricht per Bot**. Spam-Benutzer nicht, indem Sie separate neue Chat-Beiträge erstellen. Erstellen Sie einen einzelnen Threadbeitrag mit Antworten im gleichen Thread.
* **Persönlicher Chat von bot**. Senden Sie nicht mehrere Nachrichten. Senden Sie eine Nachricht mit vollständigen Informationen. Das Wiederholen derselben Begrüßungsnachricht in regelmäßigen Abständen ist nicht zulässig und gilt als Spamming.

#### <a name="notification-only-bot-welcome-messages"></a>Nur Benachrichtigungsbot-Willkommensnachrichten

Nur Benachrichtigungsbots müssen eine Willkommensnachricht senden, die eine Nachricht enthält, die übermittelt wird: *"Ich bin ein reines Benachrichtigungsbot und kann nicht auf Ihre Chats antworten"*.

#### <a name="welcome-messages-in-the-personal-scope"></a>Willkommensbotschaften im persönlichen Bereich

   * **Machen Sie Ihre Botschaft prägnant und informativ**. Die Benutzerfreundlichkeit und das Wissen Ihrer App variieren. Ein Benutzer hat Ihre App möglicherweise auf einer anderen Plattform verwendet oder weiß nichts über Ihre App. Sie möchten Ihre Botschaft an alle Zielgruppen anpassen und in ein paar Sätzen erklären, was Ihr Bot tut und wie Sie mit ihm interagieren können. Sie müssen auch den Wert der App erklären und erklären, wie die Benutzer von der Verwendung profitieren.
![Cafe und Dinning Bot](../../../../assets/images/faq/cafe-bot.png)

* **Machen Sie Ihre Nachricht umsetzbar**. Denken Sie über das erste, was Benutzer nach der Installation Ihrer App tun sollen. Gibt es einen coolen Befehl, den sie ausprobieren müssen? Gibt es eine weitere Onboarding-Erfahrung, die sie kennen müssen? Müssen sie sich anmelden? Sie können Aktionen auf einer adaptiven Karte hinzufügen oder spezifische Beispiele wie *"Versuchen Sie fragen..."*, *"Dies ist, was ich tun kann..."*.

#### <a name="welcome-messages-in-the-team-or-channel--scope"></a>Willkommensmeldungen im Team- oder Kanalbereich

Die Dinge sind ein wenig anders, wenn der Bot zum ersten Mal zu einem Kanal hinzugefügt wird. Normalerweise sollten Sie nicht eine 1:1-Nachricht an alle im Team senden, aber der Bot kann eine Willkommensnachricht im Kanal senden.

### <a name="9989-mobile-responsiveness-no-direct-upsell-or-payment"></a>&#9989; Mobile Reaktionsfähigkeit, kein direkter Upsell oder Zahlung

* Ihre Registerkarten, adaptiven Karten, Bot-Nachrichten und Inhalte in Aufgabenmodulen müssen für eine Vielzahl von Bildschirmgrößen für mobile Geräte reagieren.
* Apps, die iOS unterstützen, müssen auf den neuesten iPad Gerät mit der neuesten Version von iOS voll funktionsfähig sein.
* Sie dürfen keine direkten Verweise auf In-App-Käufe, Testangebote, Angebote für kostenpflichtige Versionen oder Links zu Onlineshops enthalten, in denen Benutzer andere Inhalte, Apps oder Add-Ins von Ihrer Teams-App auf mobilem Betriebssystem (Android, iOS) erwerben oder erwerben können.
* Die iOS- oder Android-Version des Add-Ins darf keine Benutzeroberfläche, Sprache oder Verknüpfung zu anderen Apps, Add-Ins oder Websites anzeigen, die den Benutzer zur Zahlung auffordern.
* Die zugehörigen Seiten für die Datenschutzrichtlinie und die Nutzungsbedingungen müssen auch frei von Commerce-UI oder Store-Links sein.

### <a name="9989-do-not-post-sensitive-data-to-an-audience-not-intended-to-view-the-data"></a>&#9989; Stellen Sie keine vertraulichen Daten an eine Zielgruppe weiter, die nicht zum Anzeigen der Daten bestimmt ist.

Ihre Teams App darf keine vertraulichen Daten wie Kreditkarten- oder Finanzzahlungsinstrument, PERSÖNLICHE Identifizierbare Informationen (PIN), Integrität oder Kontaktverfolgungsinformationen an eine Zielgruppe veröffentlichen, die nicht dazu bestimmt ist, diese Daten anzuzeigen.

### <a name="9989-do-not-transmit-financial-payment-details-or-complete-financial-transactions-via-your-teams-app"></a>&#9989; Übermitteln Sie keine finanziellen Zahlungsdetails oder vollständige Finanztransaktionen über Ihre Teams App

* Ihre Teams App darf Benutzer nicht auffordern, eine Zahlung direkt über Teams Schnittstelle zu tätigen.
* Apps dürfen keine Finanzinstrumentdetails über den Benutzer auf der App-Oberfläche übertragen. Apps dürfen Links zu sicheren Zahlungsdiensten nur dann an Benutzer übertragen, wenn dies in den Nutzungsbedingungen der App, der Datenschutzrichtlinie und einer Profilseite oder Website für die App angegeben ist, bevor ein Benutzer der Nutzung der App zustimmt.

### <a name="9989-clear-warning-before-downloading-any-files-or-executable-exe-into-a-users-environment"></a>&#9989; Warnung klar, bevor Sie Dateien oder ausführbare Dateien ( `.exe` ) in die Umgebung eines Benutzers herunterladen

Bitte warnen Sie Benutzer, bevor Ihre App Dateien oder ausführbare Dateien ( `.exe`  ) auf den Computer oder die Umgebung des Benutzers herunterlädt.

### <a name="9989-messaging-extensions-must-provide-help-text-and-be-easy-to-read"></a>&#9989; Messaging-Erweiterungen müssen Hilfetext bereitstellen und leicht lesbar sein

* Die suchbasierte Messaging-Erweiterung muss Hilfetext zur effektiven Suche bereitstellen (z. B. Beispieleingabe anzeigen).
* Aufgabenmodule müssen ein Symbol und einen kurzen Namen enthalten, die in der App enthalten sind oder aus der App erstellt werden.
* Die `@mention` ausführbaren Nachrichtenerweiterungen müssen klar, leicht verständlich und leicht lesbar sein.
![Nachrichtenerweiterung](../../../../assets/images/faq/message-extension.png)

## <a name="m365-publisher-attestation"></a>M365 Publisher Attestation

### <a name="9989-complete-the-publisher-attestation-in-partner-center"></a>&#9989; die Publisher Attestation im Partner Center abschließen

* Weitere Informationen finden Sie in der Dokumentation zum [Programm "Complete Publisher Attestation".](/microsoft-365-app-certification/docs/attestation)
* Führen Sie die Schritte im Abschnitt [Publisher Attestation Workflow](/microsoft-365-app-certification/docs/userguide#3publisher-attestation-workflow) aus, um den Herausgeberbehzerbehzulagevorgang abzuschließen. Schreiben Sie an appcert@microsoft.com für Fragen.
* Weitere Informationen finden Sie im [Leitfaden zur Fehlerbehebung.](/azure/active-directory/develop/troubleshoot-publisher-verification)
* Vervollständigen Sie die Selbstbescheinigung durch das Partnercenter. Füllen Sie den Self-Assessment Fragebogen unter **App Compliance** aus.

## <a name="see-also"></a>Siehe auch

* [Weitere Informationen zu Teams App-Genehmigungsrichtlinien](/legal/marketplace/certification-policies#1140-teams)
* [Abschnitt 100 — Allgemeines](/legal/marketplace/certification-policies#100-general)
* [Abschnitt 1100.5 — Kundenkontrolle](/legal/marketplace/certification-policies#11005-customer-control)
