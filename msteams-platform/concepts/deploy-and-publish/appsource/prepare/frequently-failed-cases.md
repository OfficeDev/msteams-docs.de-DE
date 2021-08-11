---
title: Tipps zur App-Übermittlung und häufig fehlgeschlagene Fälle
description: beschreibt Tipps für eine erfolgreiche Teams Store-Übermittlung und häufige Gründe, warum Übermittlungen fehlschlagen
ms.topic: reference
localization_priority: Normal
ms.author: lajanuar
keywords: Tipps zur App-Übermittlung häufig fehlgeschlagener Fälle – Validierungsrichtlinien
ms.openlocfilehash: 91ae68562d93e4ad8770d5251671c3fa756aa0b15482b4495fe016a01e068707
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57706533"
---
# <a name="tips-for-a-successful-microsoft-teams-app-submission"></a>Tipps für eine erfolgreiche Microsoft Teams App-Übermittlung

>[!NOTE]
>Diese Seite wird bis Mai 2021 veraltet sein. Weitere Informationen zum erfolgreichen Veröffentlichen Ihrer App finden Sie in den [Teams Store-Validierungsrichtlinien.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)

In diesem Artikel werden häufige Gründe beschrieben, warum die Validierung von übermittelten Apps fehlschlägt. Obwohl es sich nicht um eine vollständige Liste aller potenziellen Probleme mit Ihrer App handelt, erhöht das Befolgen dieses Leitfadens die Wahrscheinlichkeit, dass Ihre App-Übermittlung das erste Mal erfolgreich ist. Weitere Informationen finden Sie unter [Commercial Marketplace-Zertifizierungsrichtlinien](/legal/marketplace/certification-policies) für eine umfassende Liste von Validierungsrichtlinien.

>[!NOTE]
>**[Abschnitt 1140](/legal/marketplace/certification-policies#1140-teams)** bezieht sich speziell auf Microsoft Teams und **[Unterabschnitt 1140.4](/legal/marketplace/certification-policies#11404-functionality)** befasst sich mit den Funktionalitätsanforderungen für Teams Apps.

## <a name="validation-guidelines--most-failed-test-cases"></a>Validierungsrichtlinien & meisten fehlgeschlagenen Testfällen

### <a name="9989-general-considerations"></a>allgemeine Überlegungen &#9989;

* Stellen Sie sicher, dass Sie Version 1.4.1 oder höher des [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js)verwenden.
* Nehmen Sie während des Überprüfungsprozesses keine Änderungen an Ihrer App vor. Dazu ist eine vollständige Erneute Überprüfung Ihrer App erforderlich.
* Ihre App darf sich nicht aufhängen, unerwartet beendet werden oder Programmierungsfehler enthalten. Wenn ein Problem auftritt, muss Ihre App fehlschlagen und gültige Informationen für die Weiterleitung an den Benutzer bereitstellen.
* Ihre App darf ausführbaren Code in der Benutzerumgebung nicht automatisch herunterladen, installieren oder starten. Alle Downloads müssen die explizite Berechtigung des Benutzers anfordern.
* Alle Materialien, die Sie Ihrer Erfahrung zuordnen, z. B. Beschreibungen und Supportdokumentation, müssen korrekt sein. Achten Sie in diesen Materialien auf Rechtschreibung, Zeichensetzung und Grammatik.
* Bereitstellen von Hilfe- und Supportinformationen. Es wird dringend empfohlen, dass Ihre App einen Hilfe- oder FAQ-Link für die Erste Ausführung enthält. Für alle persönlichen Apps empfehlen wir, Ihre Hilfeseite als persönliche Registerkarte für eine bessere Benutzererfahrung bereitzustellen.
* Alle Apps müssen über eine visuelle Tour verfügen, z. **B. "Take a Tour"** oder **"App Guide"** auf dem Konfigurationsbildschirm, auf dem über die App-Features und die erforderliche Integration an den folgenden Stellen gesprochen wird:
    * Die Seite für den Store-Eintrag (lange Beschreibung).
    * Registerkartenkonfigurationsbildschirm.
    * Willkommensnachricht für einen Bot.
    * App-Quellmetadaten.
    * Connector-Konfigurationsbildschirm.

* Die visuelle Tour kann ein Video, ein Screenshot und ein Link zu einer statischen Registerkarte mit App-Details sein. Alle diese Verweise müssen sich innerhalb der Teams Umgebung befinden.

    ![Beispiel-App 1 ](../../../../assets/images/faq/Sampleapp1.png) ![ Beispiel-App 2](../../../../assets/images/faq/Sampleapp2.png)

* Erhöhen Sie die Versionsnummer Ihrer App im Manifest, wenn Sie Manifeständerungen an Ihrer Übermittlung vornehmen.
* Die App darf benutzer nicht aus Teams für kernbenutzerszenarien entfernen. Linkziele in Apps dürfen nicht mit einem externen Browser verknüpft werden. Verknüpfungsziele müssen mit div-Elementen in Teams verknüpft werden, z. B. Aufgabenmodulen und Registerkarten. 
* Es wird empfohlen, Aufgabenmodule oder Registerkarten zu verwenden, um Benutzern Informationen innerhalb Teams anzuzeigen.
* Alle Kern- und Nicht-Kernszenarien müssen innerhalb der Teams Umgebung abgeschlossen werden, mit Ausnahme von:
  * Datenschutzrichtlinie
  * Nutzungsbedingungen
  * Websitelink
  * Registrierungsprozess

* Mit persönlichen Apps können Benutzer Inhalte aus einer persönlichen App-Erfahrung mit anderen Teammitgliedern teilen.

### <a name="9989-provide-a-clear-and-simple-sign-in-sign-out-and-sign-up-experience"></a>&#9989; Eine klare und einfache Anmelde-, Abmelde- und Registrierungserfahrung bereitstellen

* Wenn Ihre App oder Ihr Add-In von externen Konten oder Diensten abhängt, müssen die Anmelde-, Abmelde- und Registrierungserfahrung über alle Funktionen ihrer App hinweg offensichtlich und erreichbar sein.
* Wenn dem Benutzer eine explizite Anmeldeoption zur Verfügung steht, muss eine entsprechende Abmeldeoption vorhanden sein (auch wenn die App die [automatische Authentifizierung](../../../../tabs/how-to/authentication/auth-silent-aad.md)verwendet).
* Die Abmeldungsoption darf den Benutzer nur von der App-Funktion und nicht vom Teams Client abmelden.
* Die Abmeldungsoption muss den Benutzer mindestens von den gleichen Funktionen abmelden, auf die mit der Anmeldeoption zugegriffen wird. Wenn z. B. die Anmeldeoption messaging-Erweiterung und Registerkarte enthält, muss die Abmeldeoption sowohl Messaging-Erweiterung als auch Registerkarte enthalten.

* Stellen Sie sicher, dass es immer eine Möglichkeit gibt, das folgende (oder ähnliche) Verhalten umzukehren:
  * Anmeldung => Abmelden.
  * Verknüpfen eines Kontos/Diensts => Aufheben der Verknüpfung eines Kontos/Diensts.
  * Verbinden ein Konto/Dienst => Trennen eines Kontos/Diensts.
  * Autorisieren eines Kontos/Diensts => Aufheben der Autorisierung/Ablehnung eines Kontos/Diensts.
  * Registrieren eines Kontos/Diensts => die Registrierung eines Kontos/Diensts aufheben/kündigen.
* Wenn Ihre App ein Konto oder einen Dienst erfordert, müssen Sie dem Benutzer eine Möglichkeit bieten, sich zu registrieren oder eine Registrierungsanforderung zu erstellen. Eine Ausnahme kann gewährt werden, wenn Für Ihre App eine Lizenz erforderlich ist. Stellen Sie in solchen Szenarien klare Anweisungen für einen neuen Benutzer bereit, sich anzumelden.
* Stellen Sie klare Anleitungen für die Weiterleitung an einen neuen Benutzer bereit, wie Sie sich für die Verwendung Ihrer App-Dienste registrieren. Wenn kein bereiter Registrierungslink verfügbar ist, geben Sie in den folgenden Bereichen eine genaue Anleitung:

> [!div class="checklist"]
>
> * innerhalb des App-Beschreibungsabschnitts.
> * in der Willkommensnachricht Ihrer App.
> * in der Hilfenachricht Ihrer App.
> * in dem Fenster, in dem Sie einen Benutzer bitten, sich bei Ihren Diensten anzumelden.

* Apps ohne einfachen Registrierungsablauf müssen auch eine Hilferegisterkarte oder einen Link zu einer Webseite enthalten, auf der ein neuer Benutzer detaillierte Anleitungen zum Konfigurieren Ihrer Teams-App sehen kann. Stellen Sie detaillierte Informationen bereit, um sicherzustellen, dass ein neuer Benutzer beim ersten Versuch ihrer App nicht blockiert wird.
* Anmelde- und Abmeldefunktionen müssen auf mobilen Clients funktionieren. Stellen Sie sicher, dass Sie die [Microsoft Teams SDK-Version](https://www.npmjs.com/package/@microsoft/teams-js) 1.4.1 oder höher verwenden.

Weitere Informationen zur Authentifizierung finden Sie unter:

* [Authentifizierungsdokumentation](../../../authentication/authentication.md)
* [Bot-Authentifizierungsbeispiel in Node](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
* [Registerkartenauthentifizierungsbeispiel in Node](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)
* [Registerkarten-/Bot-Authentifizierung in C#/.NET](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp)

### <a name="9989-response-times-must-be-reasonable"></a>&#9989; Antwortzeiten müssen angemessen sein

* **Registerkarten**. Wenn eine Antwort auf eine Aktion mehr als drei Sekunden dauert, müssen Sie eine Lademeldung oder Warnung bereitstellen.
* **Bots**. Eine Antwort auf einen Benutzerbefehl muss innerhalb von zwei Sekunden erfolgen. Wenn eine längere Verarbeitung erforderlich ist, muss ihre App eine Eingabeanzeige anzeigen.
* **Verfassen-Erweiterungen**. Eine Antwort auf einen Benutzerbefehl muss innerhalb von fünf Sekunden erfolgen.

> [!TIP]
> Stellen Sie sicher, dass Ihre App eine Ladeanzeige oder eine Form von Warnung anzeigt, wenn ihre App länger als erwartet reagiert.

### <a name="9989-tab-content-must-not-have-excessive-chrome-or-layered-navigation"></a>&#9989; Registerkarteninhalte dürfen keine übermäßige Chrome- oder mehrstufige Navigation aufweisen

* Registerkarten müssen fokussierte Inhalte bereitstellen und unnötige UI-Elemente vermeiden. Dies bezieht sich in der Regel auf unnötige geschachtelte oder mehrschichtige Navigation, eine überflüssige oder irrelevante Benutzeroberfläche neben dem Inhalt oder links, die den Benutzer zu nicht verbundenen Inhalten führen. In der folgenden Registerkartenansicht werden beispielsweise Navigationsmenüs weggelassen und nur der Hauptinhalt angezeigt:

![SharePoint Webansicht](../../../../assets/images/faq/web-sp.png)  
![SharePoint Registerkartenansicht](../../../../assets/images/faq/tab-sp.png)

* Registerkarten müssen einfach sein und dürfen keine komplexe Navigation enthalten.
* Kanalregisterkarten mit komplexen Bearbeitungsfunktionen innerhalb der App müssen die Editoransicht in einem Mehrfenster statt in einer Registerkarte öffnen.
* Kanalregisterkarten dürfen keine App-Leiste mit Symbolen auf der linken Leiste bereitstellen, die mit der Hauptnavigation Teams in Konflikt steht.
* Registerkarten dürfen keine App-Leiste mit Symbolen auf der linken Leiste darstellen, die mit der Hauptnavigation Teams in Konflikt geraten.
* Registerkarten mit komplexen Bearbeitungsfunktionen innerhalb der App müssen die Editoransicht nicht in der Registerkarte, sondern in einem Fenster mit mehreren Fenstern öffnen.
* Wenn mehrere Ansichtsoptionen vorhanden sind, sollten Sie ein Registerkartenkonfigurationsmenü verwenden, aus dem der Benutzer auswählen kann. Anstatt z. B. ein Menü in die Registerkarte einzubetten, platzieren Sie das Menü auf der Konfigurationsseite, damit die tatsächliche Registerkartenansicht sauber und fokussiert ist.
* Fügen Sie eine *Registerkarte "Hilfe"* als statische Registerkarte ein, um Benutzern zu empfehlen, wie Sie Ihre App konfigurieren, registrieren und verwenden.
* Fügen Sie eine *Einstellungen* Registerkarte ein, die über den App-Header verfügbar ist.

![Konfigurationsseite für breite Ideen](../../../../assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>&#9989; Registerkartenkonfiguration muss auf dem Konfigurationsbildschirm erfolgen

* Der Konfigurationsbildschirm muss den Wert der Benutzeroberfläche und die Konfiguration der Registerkarte deutlich erläutern.
* Der Konfigurationsprozess muss den Benutzern immer eine Möglichkeit bieten, den Vorgang fortzusetzen und die Benutzererfahrung nicht zu beenden. Zeigen Sie beispielsweise kein leeres Board an, nachdem der Benutzer die Registerkarte konfiguriert hat.
* Der Benutzeranmeldungsprozess muss Teil des Konfigurationsprozesses sein. Stellen Sie sicher, dass Sie es auf der Registerkarten-Benutzeroberfläche vervollständigen. Nachdem der Benutzer die Konfiguration abgeschlossen und die Registerkarte geladen hat, ist keine weitere Aktion erforderlich.
* Zeigen Sie nicht die gesamte Webseite im Popupfenster der Anmeldekonfiguration an.
* Ein Benutzer muss immer in der Lage sein, die Konfiguration abzuschließen, auch wenn er den gesuchten Inhalt nicht sofort finden kann.
* Die Konfigurationsumgebung muss Optionen für den Benutzer bereitstellen, um seine Inhalte zu finden, eine URL anheften oder neue Inhalte erstellen zu können, wenn sie nicht vorhanden sind.
* Die Konfigurationsumgebung muss im Teams Kontext verbleiben. Der Benutzer sollte die Konfigurationsoberfläche nicht verlassen müssen, um Inhalte zu erstellen, und dann zu Teams zurückkehren, um ihn anheften zu können.
* Verwenden Sie den verfügbaren Viewportbereich effizient. Verwenden Sie keine großen Logos innerhalb des Konfigurationsfensters.

![OneNote ermöglicht Benutzern das Einfügen eines OneNote Links für den Fall, dass notizen nicht gefunden werden können](../../../../assets/images/faq/tab-onenote-config.png)

![Benutzer können in Planner immer einen neuen Plan erstellen, falls keine vorhanden sind.](../../../../assets/images/faq/tab-planner-config.png)

![SharePoint ermöglicht dem Benutzer auch das direkte Einfügen eines SharePoint Links](../../../../assets/images/faq/tab-sp-config.png)

### <a name="9989-tabs-in-channel---member-access"></a>&#9989; Registerkarten im Kanal – Mitgliederzugriff

* Auf eine Registerkarte, die von einem Mitglied in einem Kanalbereich konfiguriert wurde, muss für die anderen Mitglieder zugegriffen werden können, ohne berechtigungen von dem Mitglied anfordern zu müssen, das die Registerkarte konfiguriert hat.
* Die App muss die Berechtigungsverwaltungsoptionen vorab bereitstellen, wenn die Registerkarte für die private oder eingeschränkte Verwendung vorgesehen ist oder Berechtigungen des Mitglieds benötigt, das die Registerkarte konfiguriert hat.

### <a name="9989-bots-must-always-be-responsive-and-fail-gracefully"></a>&#9989; Bots müssen immer reaktionsfähig sein und ordnungsgemäß fehlschlagen.

Ihr Bot muss für jeden Befehl reagieren und nicht für den Benutzer inaktiv sein. Hier sind einige Tipps, um Ihrem Bot zu helfen, intelligent auf Benutzer zu reagieren:

* **Verwenden Sie Befehlslisten.** Die Analyse von Benutzereingaben oder die Vorhersage der Benutzerabsicht ist schwierig. Anstatt Benutzern zu ermöglichen, zu erraten, was Ihr Bot tun kann, stellen Sie eine Liste der Befehle bereit, die Ihr Bot versteht.

![Flow Befehlsliste](../../../../assets/images/faq/flow-bot.png)

* **Fügen Sie einen Hilfebefehl ein.** Benutzer geben wahrscheinlich "Hilfe" ein, wenn sie verloren gehen oder wenn Ihr Bot nicht wie erwartet reagiert. Fügen Sie einen Hilfebefehl ein, der beschreibt, wie der Wert Ihrer App zusammen mit allen gültigen Befehlen angezeigt wird.

![Flow Hilfebefehl](../../../../assets/images/faq/flow-help.png)

* **Fügen Sie Hilfeinhalte oder Anleitungen ein, wenn Ihr Bot verloren geht.** Wenn Ihr Bot die Benutzereingabe nicht verstehen kann, muss er eine alternative Aktion vorschlagen. Beispiel: *"Es tut mir leid, ich kann es nicht verstehen. Geben Sie "Hilfe" ein, um weitere Informationen zu erfahren."* Antworten Sie nicht mit einer Fehlermeldung oder einfach *"Ich kann nicht verstehen".*

### <a name="9989-help-command-response"></a>&#9989;-Hilfebefehlsantwort

* Der Hilfebefehl muss genau sein, und die App-Antworten müssen ein adaptives Kartenformat mit aktionen erfordernden Inhalten für mindestens sechs Befehle aufweisen.
* Wenn eine App weniger als sechs Befehle enthält, überprüfen Sie, ob alle Befehle auf der adaptiven Karte vorhanden sind.

  ![Hilfebefehlsbeispiel](../../../../assets/images/faq/helpcommand.png)

* **Verwenden von adaptiven Karten und Aufgabenmodulen, um Die Bot-Antwort klar und umsetzbar zu machen** Adaptive Karten mit Schaltflächen, die Aufgabenmodule aufrufen, verbessern die Bot-Benutzererfahrung. Diese Karten und Schaltflächen sind auf einem mobilen Gerät einfacher zu verwenden, anstatt dass Der Benutzer die Befehle eingibt. Auch Bot-Antworten dürfen nicht textbezogen mit langem Text sein. Bots müssen adaptive Karten und Aufgabenmodule anstelle von unterhaltungschatbasierter Benutzeroberfläche und langen Textantworten verwenden.

* **Denken Sie durch alle Bereiche.** Achten Sie darauf, dass Ihr Bot geeignete Antworten bereitstellt, wenn er `@*botname*` in einem Kanal und in persönlichen Unterhaltungen erwähnt wird ( ). Wenn Ihr Bot keinen sinnvollen Kontext im persönlichen oder Teams-Bereich bereitstellt, deaktivieren Sie diesen Bereich über das Manifest. (Siehe den `bots` Block in der Microsoft Teams [Manifestschemareferenz.)](../../../../resources/schema/manifest-schema.md#bots)

* **Team, Gruppenchat oder 1:1-Unterhaltung einschließen.** Bot-Benachrichtigungen müssen ein Team, einen Gruppenchat oder eine 1:1-Unterhaltung mit relevanten Inhalten für Ihre Zielgruppe enthalten.

* **Vertrauliche Daten dürfen nicht übertragen werden.** Bots dürfen vertrauliche Daten nicht an ein Team, einen Gruppenchat oder eine 1:1-Unterhaltung übertragen, bei der es eine Zielgruppe gibt, die diese Daten nicht anzeigen darf.

* **Senden Sie eine Willkommensnachricht.** Bot muss eine FRE-Willkommensnachricht bereitstellen, die ein interaktives Lernprogramm mit Karussellkarten oder Schaltflächen "Ausprobieren" enthält, um die Interaktion zu fördern.

### <a name="9989-personal-bots-must-always-send-a-welcome-message-on-first-launch"></a>&#9989; Persönliche Bots müssen beim ersten Start immer eine Willkommensnachricht senden

Eine Willkommensnachricht ist die beste Möglichkeit, den Ton für Ihren persönlichen Chat-Bot festzulegen. Dies ist die erste Interaktion, die ein Benutzer mit dem Bot hat. Eine gute Willkommensnachricht kann den Benutzer ermutigen, die App weiter zu erkunden. Wenn die Willkommens- oder Einführungsnachricht verwirrend oder unklar ist, werden die Benutzer den Wert der App nicht sofort sehen und ihr Interesse verlieren.
Anforderungen für Willkommensnachrichten finden Sie im folgenden Abschnitt:

> [!Note]
> Eine Willkommensnachricht ist für einen Kanal-Bot optional.

### <a name="welcome-message-requirements"></a>Anforderungen für Willkommensnachrichten

* Fügen Sie ein Wertversprechen in die Willkommenstour ein.
* Bereitstellen von Anleitungen für die Verwendung der App.
* Enthalten Sie Anleitungen zum Registrieren und Konfigurieren Ihrer App.
* Stellen Sie leicht lesbaren Text und einen einfachen Dialog bereit – vorzugsweise eine Karte mit einer Willkommens-Tour-Schaltfläche mit Aktionen, die ein Aufgabenmodul lädt.
* Halten Sie es einfach und mit Schaltflächen und Karten verwendbar – vermeiden Sie lange Text, chatty Dialoge.
* Fügen Sie adaptive Karten und Schaltflächen ein, um die Willkommensnachricht benutzerfreundlicher zu gestalten.
* Rufen Sie die Willkommensnachricht mit einem Ping auf, nicht mit zwei oder mehr gleichzeitigen Pings.
* Eine Willkommensnachricht darf nur dem Benutzer angezeigt werden, der die App konfiguriert hat, vorzugsweise in einem persönlichen 1:1-Chat.
* Persönliche Apps müssen immer eine Willkommensnachricht an einen Benutzer senden.
* Senden Sie niemals einen persönlichen Chat an jedes Mitglied des Teams; es wird als Spam betrachtet.
* Senden Sie die Willkommensnachricht niemals mehr als einmal. Das Wiederholen der gleichen Willkommensnachricht in regelmäßigen Intervallen ist nicht zulässig und wird als Spamming betrachtet.

#### <a name="avoid-welcome-message-spamming"></a>Vermeiden von Spamming von Willkommensnachrichten

* **Kanalnachricht nach Bot**. Spamen Sie Benutzer nicht, indem Sie separate neue Chatbeiträge erstellen. Erstellen Sie einen einzelnen Threadbeitrag mit Antworten im selben Thread.
* **Persönlicher Chat nach Bot**. Senden Sie nicht mehrere Nachrichten. Senden Sie eine Nachricht mit vollständigen Informationen. Das Wiederholen der gleichen Willkommensnachricht in regelmäßigen Intervallen ist nicht zulässig und wird als Spamming betrachtet.

#### <a name="notification-only-bot-welcome-messages"></a>Nur-Benachrichtigungen für Bot-Willkommensnachrichten

Nur-Benachrichtigung-Bots müssen eine Willkommensnachricht senden, die eine Nachricht mit der Meldung *"Ich bin ein Nur-Benachrichtigung-Bot und kann nicht auf Ihre Chats antworten" enthält.*

#### <a name="welcome-messages-in-the-personal-scope"></a>Willkommensnachrichten im persönlichen Bereich

   * **Formulieren Sie Ihre Nachricht prägnant und informativ.** Die Benutzererfahrung und das Wissen ihrer App variieren. Ein Benutzer hat Ihre App möglicherweise auf einer anderen Plattform verwendet oder weiß nichts über Ihre App. Sie möchten Ihre Nachricht an alle Zielgruppen anpassen und in einigen Sätzen erklären, was Ihr Bot macht und wie er damit interagieren kann. Außerdem müssen Sie den Wert der App erläutern und erläutern, wie die Benutzer von der Verwendung der App profitieren.
![Cafés und Dinning-Bot](../../../../assets/images/faq/cafe-bot.png)

* **Sorgen Sie dafür, dass Ihre Nachricht mit Aktionen ausgeführt werden kann.** Überlegen Sie, was Benutzer nach der Installation Ihrer App zuerst tun sollen. Gibt es einen coolen Befehl, den sie ausprobieren müssen? Gibt es eine weitere Onboarding-Erfahrung, die sie kennen müssen? Müssen sie sich anmelden? Sie können Aktionen auf einer adaptiven Karte hinzufügen oder bestimmte Beispiele wie *"Versuchen Sie zu fragen...",* *"Dies kann ich tun...".*

#### <a name="welcome-messages-in-the-team-or-channel--scope"></a>Willkommensnachrichten im Team- oder Kanalbereich

Die Dinge unterscheiden sich etwas, wenn der Bot zum ersten Mal zu einem Kanal hinzugefügt wird. Normalerweise sollten Sie keine 1:1-Nachricht an alle Personen im Team senden, aber der Bot kann eine Willkommensnachricht im Kanal senden.

### <a name="9989-mobile-responsiveness-no-direct-upsell-or-payment"></a>&#9989; Reaktionsfähigkeit mobiler Geräte, kein direkter Upselling oder zahlung

* Ihre Registerkarten, adaptiven Karten, Botnachrichten und Inhalte in Aufgabenmodulen müssen für eine Vielzahl von Bildschirmgrößen mobiler Geräte reaktionsfähig sein.
* Apps, die iOS unterstützen, müssen auf dem neuesten iPad Gerät mit der neuesten Version von iOS voll funktionsfähig sein.
* Sie dürfen keine direkten Verweise auf In-App-Käufe, Testangebote, Angebote für kostenpflichtige Versionen oder Links zu Onlinestores enthalten, in denen Benutzer andere Inhalte, Apps oder Add-Ins aus Ihrer Teams-App unter mobilem Betriebssystem (Android, iOS) erwerben oder erwerben können.
* Die iOS- oder Android-Version des Add-Ins darf keine Benutzeroberfläche oder Sprache oder keinen Link zu anderen Apps, Add-Ins oder Websites anzeigen, die den Benutzer zur Zahlung auffordern.
* Die zugehörigen Seiten für Datenschutzrichtlinien und Nutzungsbedingungen müssen ebenfalls frei von Commerce-UI- oder Store-Links sein.

### <a name="9989-do-not-post-sensitive-data-to-an-audience-not-intended-to-view-the-data"></a>&#9989; Keine vertraulichen Daten an eine Zielgruppe veröffentlichen, die die Daten nicht anzeigen soll

Ihre Teams-App darf keine vertraulichen Daten wie Kreditkarten- oder Zahlungen, personenbezogene Informationen (PIN), Integritäts- oder Kontaktablaufverfolgungsinformationen an eine Zielgruppe veröffentlichen, die diese Daten nicht anzeigen soll.

### <a name="9989-do-not-transmit-financial-payment-details-or-complete-financial-transactions-via-your-teams-app"></a>&#9989; Keine Finanziellen Zahlungsdetails übertragen oder Finanztransaktionen über Ihre Teams-App abschließen

* Ihre Teams-App darf Benutzer nicht auffordern, eine Zahlung direkt innerhalb Teams Schnittstelle vorzunehmen.
* Apps dürfen keine Details zu Finanzinstituten über den Benutzer auf der App-Benutzeroberfläche übertragen. Apps dürfen Links zu sicheren Zahlungsdiensten nur an Benutzer übertragen, wenn dies in den Nutzungsbedingungen, der Datenschutzrichtlinie und jeder Profilseite oder Website für die App offengelegt wird, bevor ein Benutzer der Verwendung der App zustimmt.

### <a name="9989-clear-warning-before-downloading-any-files-or-executable-exe-into-a-users-environment"></a>&#9989; Warnung vor dem Herunterladen von Dateien oder ausführbaren Dateien ( `.exe` ) in die Umgebung eines Benutzers löschen

Warnen Sie die Benutzer, bevor Ihre App Dateien oder ausführbare Dateien ( `.exe`  )auf den Computer oder die Umgebung des Benutzers herunterlädt.

### <a name="9989-messaging-extensions-must-provide-help-text-and-be-easy-to-read"></a>&#9989; Messaging-Erweiterungen müssen Hilfetext bereitstellen und leicht lesbar sein.

* Die suchbasierte Messaging-Erweiterung muss Hilfetext für die effektive Suche bereitstellen (z. B. Beispieleingabe anzeigen).
* Aufgabenmodule müssen ein Symbol und einen Kurznamen enthalten oder aus der App erstellt werden.
* Die ausführbaren Dateien der Nachrichtenerweiterung `@mention` müssen klar, leicht verständlich und leicht zu lesen sein.
![Nachrichtenerweiterung](../../../../assets/images/faq/message-extension.png)

## <a name="m365-publisher-attestation"></a>M365 Publisher Attestation

### <a name="9989-complete-the-publisher-attestation-in-partner-center"></a>&#9989; den Publisher Attestation im Partner Center abschließen

* Weitere Informationen finden Sie in der Dokumentation zum [Complete Publisher Attestation-Programm.](/microsoft-365-app-certification/docs/attestation)
* Führen Sie die Schritte im Abschnitt [Publisher Attestation Workflow](/microsoft-365-app-certification/docs/userguide#3publisher-attestation-workflow) aus, um den Nachweisprozess des Herausgebers abzuschließen. Schreiben Sie bei Fragen in appcert@microsoft.com.
* Weitere Informationen finden Sie im [Handbuch zur Problembehandlung.](/azure/active-directory/develop/troubleshoot-publisher-verification)
* Schließen Sie den Selbstnachweis über das Partner Center ab. Füllen Sie den Self-Assessment Fragebogen unter **App-Compliance** aus.

## <a name="see-also"></a>Weitere Informationen

* [Weitere Informationen zu Teams App-Genehmigungsrichtlinien](/legal/marketplace/certification-policies#1140-teams)
* [Abschnitt 100 – Allgemein](/legal/marketplace/certification-policies#100-general)
* [Abschnitt 1100.5 – Kundenkontrolle](/legal/marketplace/certification-policies#11005-customer-control)
