---
title: Tipps und häufig fehlgeschlagene Fälle
description: Beschreibt Tipps für die Übermittlung und die meisten fehlgeschlagenen Richtlinien
author: laujan
ms.author: lajanuar
ms.topic: how to
keywords: Teams-apps-Validierung am häufigsten fehlgeschlagene Testfälle schnellgenehmigung appsource veröffentlichen
ms.openlocfilehash: 6e3f6e09de68cdb00743c6954b999c35ceefcdf7
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931806"
---
# <a name="tips-for-a-successful-app-submission"></a>Tipps für eine erfolgreiche App-Übermittlung

In diesem Artikel werden häufige Gründe für die Überprüfung von apps-Fehlern behandelt. Es ist zwar nicht beabsichtigt, eine erschöpfende Liste aller potenziellen Probleme mit Ihrer APP zu sein, aber im Anschluss an dieses Handbuch wird die Wahrscheinlichkeit erhöht, dass Ihre APP-Übermittlung das erste Mal übergeben wird. Eine umfassende Liste der Validierungsrichtlinien *finden Sie unter* [Commercial Marketplace Certification Policies](/legal/marketplace/certification-policies) .

>[!NOTE]
>**[Abschnitt 1140](/legal/marketplace/certification-policies#1140-teams)** ist spezifisch für Microsoft Teams und **[unter Abschnitt 1140,4](https://docs.microsoft.com/legal/marketplace/certification-policies#11404-functionality)** , in dem die Funktionalitätsanforderungen für Teams-apps behandelt werden.

## <a name="validation-guidelines--most-failed-test-cases"></a>Validierungsrichtlinien & am häufigsten fehlgeschlagenen Test Cases

### <a name="9989-general-considerations"></a>&#9989; allgemeine Überlegungen

*Siehe auch* [Abschnitt 100 – allgemein](/legal/marketplace/certification-policies#100-general)

* Stellen Sie sicher, dass Sie die Version 1.4.1 oder höher des [Microsoft Teams SDK](https://www.npmjs.com/package/@microsoft/teams-js)verwenden.
* Nehmen Sie keine Änderungen an Ihrer APP vor, während der Validierungsprozess ausgeführt wird. Auf diese Weise ist eine vollständige Revalidierung Ihrer APP erforderlich.
* Ihre APP darf nicht mehr reagieren, unerwartet beenden oder Programmierfehler enthalten. Wenn ein Problem auftritt, sollte Ihre APP ordnungsgemäß fehlschlagen und dem Benutzer eine gültige-Weg-weiter-Nachricht bereitstellen.
* Ihre APP darf keinen ausführbaren Code in der Benutzerumgebung automatisch herunterladen, installieren oder starten. Alle Downloads sollten eine explizite Berechtigung des Benutzers suchen.
* Jedes Material, das Sie Ihrer Erfahrung zuordnen, wie Beschreibungen und Support Dokumentationen, muss genau sein. Achten Sie in diesen Materialien auf Rechtschreibung, Zeichensetzung und Grammatik.
* Bereitstellen von Hilfe-und Supportinformationen Es wird dringend empfohlen, dass Ihre APP einen Link zu Hilfe/FAQ für die Benutzeroberfläche mit der ersten Ausführung enthält. Für alle persönlichen apps wird empfohlen, ihre Hilfeseite als persönliche Registerkarte bereitzustellen, um eine bessere Benutzerfreundlichkeit zu erreichen.
* Apps dürfen Benutzer nicht aus Teams für Hauptbenutzer Szenarien entfernen. Verwenden von Aufgaben Modulen AMD-Registerkarten werden empfohlen, um Informationen für den Benutzer in Microsoft Teams anzuzeigen.
* Erhöhen Sie Ihre APP-Versionsnummer im Manifest, wenn Sie an ihrer Übermittlung Manifeste Änderungen vornehmen.
* Die APP darf keine Benutzer aus Teams für Hauptbenutzer Szenarien entfernen. Verknüpfungsziele in apps dürfen nicht mit einem externen Browser verknüpft werden, sondern sollten mit div-Elementen in Microsoft Teams wie beispielsweise innerhalb von Aufgaben Modulen und Registerkarten verknüpft werden.
* Mit persönlichen Apps können Benutzer Inhalte aus einer persönlichen App-Umgebung für andere Teammitglieder freigeben.
* Kanal Registerkarten dürfen keine app-Leiste mit Symbolen in der linken Schiene zur Verfügung stellen, die mit der Navigation in den Haupt Teams in Konflikt stehen.
* Kanal Registerkarten mit komplexen Bearbeitungsfunktionen innerhalb der APP sollten die Editoransicht in mehreren Fenstern anstelle einer Registerkarte öffnen.

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
* Stellen Sie sicher, dass Sie einen neuen Benutzer mit klaren Anleitungen für die Anmeldung zur Verwendung Ihrer APP-Dienste versehen. Wenn keine Ready Sign up-Verknüpfung verfügbar ist, können Sie in der APP-Beschreibungsseite, in der Willkommensnachricht, in der Hilfenachricht und im Anmeldefenster, in dem Sie von einem Benutzer bei Ihren Diensten angemeldet werden, einen klaren Weg nach vorn finden. Apps, die nicht über einen einfachen Registrierungs Fluss verfügen, können auch eine Hilfe-Registerkarte oder einen Link zu einer Webseite enthalten, auf der ein neuer Benutzer detaillierte Anleitungen zum Konfigurieren Ihrer APP mit Microsoft Teams sehen kann.  Dadurch wird sichergestellt, dass für einen neuen Benutzer keine Straßensperre angezeigt wird, wenn die APP zum ersten Mal ausprobiert wird.
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

![SharePoint-Webansicht](~/assets/images/faq/web-sp.png)  
![SharePoint-Registerkartenansicht](~/assets/images/faq/tab-sp.png)

* Registerkarten sollten leicht in der Natur sein und keine komplexe Navigation umfassen.
* Registerkarten dürfen keine app-Leiste mit Symbolen in der linken Schiene darstellen, die mit der Navigation der Haupt Teams in Konflikt stehen.
* Registerkarten mit komplexen Bearbeitungsfunktionen innerhalb der APP sollten die Editoransicht in mehreren Fenstern anstatt auf der Registerkarte öffnen.
* Wenn mehrere Ansichtsoptionen vorhanden sind, sollten Sie ein Tab-Konfigurationsmenü für den Benutzer auswählen. Anstatt beispielsweise ein Menü in die Registerkarte einzubetten, legen Sie das Menü auf der Konfigurationsseite so fest, dass die tatsächliche Registerkartenansicht sauber und fokussiert ist.

![Seite "Wide idea-Konfiguration"](~/assets/images/faq/wideidea.png)

### <a name="9989-tab-configuration-must-happen-in-the-configuration-screen"></a>Auf dem Konfigurationsbildschirm muss &#9989;-Registerkarte konfiguriert sein.

* Auf dem Konfigurationsbildschirm sollte der Wert der Benutzeroberfläche eindeutig erläutert und die Registerkarte konfiguriert werden.
* Der Konfigurationsprozess sollte immer eine Möglichkeit für Benutzer bieten, die Benutzerfreundlichkeit weiterhin nicht zu beenden. Zeigen Sie beispielsweise nicht eine leere Platine an, nachdem der Benutzer die Registerkarte konfiguriert hat.
* Der Benutzeranmeldeprozess muss Teil des Konfigurationsprozesses sein und in der Registerkarten-Benutzeroberfläche abgeschlossen sein. Nachdem der Benutzer die Konfiguration abgeschlossen und die Registerkarte geladen hat, sollte keine weitere Aktion erforderlich sein.
* Zeigen Sie die gesamte Webseite nicht im Popupfenster der Anmeldekonfiguration an.
* Ein Benutzer sollte die Konfigurationsumgebung immer fertig stellen können, auch wenn er nicht sofort den gesuchten Inhalt finden kann.
* Die Konfigurationsumgebung sollte Optionen für den Benutzer bieten, um den Inhalt zu finden, eine URL zu fixieren oder neue Inhalte zu erstellen, falls diese nicht vorhanden sind.
* Die Konfigurations Erfahrung muss innerhalb des Teams-Kontexts verbleiben. Der Benutzer sollte die Konfigurationsoberfläche nicht verlassen müssen, um Inhalte zu erstellen und dann zu Microsoft Teams zurückzukehren, um es zu fixieren.
* Effizientes Verwenden des Bereichs "verfügbare Viewports" Verschwenden Sie es nicht bei der Verwendung von großen Logos innerhalb der Konfiguration Pop-up

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

* **Verwenden Sie Adaptive Karten und Aufgaben Module, um Ihre bot-Antwort übersichtlicher und Umsetz** 
 barer zu machen. [Adaptive Karten mit Schaltflächen, die Aufgaben Module aufrufen](/task-modules-and-cards/task-modules/task-modules-bots) , verbessern die bot-Benutzeroberfläche. Diese Karten und Schaltflächen sind im Gegensatz zu Ihrem Benutzer, der die Befehle eintippt, einfacher auf einem mobilen Gerät zu verwenden. Auch bot-Antworten sollten nicht Text mit langem Text sein. Bots müssen Adaptive Karten & Aufgaben Modulen anstelle von Konversations Chat-basierter Benutzeroberfläche und langwierigen Textantworten nutzen.

* **Überdenken Sie alle Bereiche**. Stellen Sie sicher, dass Ihr bot geeignete Antworten bereitstellt, wenn Sie `@*botname*` in einem Kanal und in persönlichen Unterhaltungen erwähnt werden. Wenn Ihr bot keinen sinnvollen Kontext innerhalb des Bereichs Personal oder Teams bereitstellt, deaktivieren Sie diesen Bereich über das Manifest. (Weitere Informationen finden Sie unter `bots` Block in der [Microsoft Teams Manifest-Schemareferenz](~/resources/schema/manifest-schema.md#bots).)

* **Vertrauliche Daten nicht pushen**. Bots dürfen keine vertraulichen Daten für ein Team, einen Gruppenchat oder eine 1:1-Unterhaltung pushen, bei denen die Benutzer nicht in der Lage sein sollten, diese Daten anzuzeigen.

* **Geben Sie eine Willkommensnachricht ein**. Bot muss eine Fre-Willkommensnachricht bereitstellen, die ein interaktives Lernprogramm mit Karussell Karten oder "try it"-Schaltflächen enthält, um das Engagement zu fördern.

### <a name="9989-personal-bots-must-always-send-a-welcome-message-on-first-launch"></a>&#9989; persönliche Bots müssen beim ersten Start immer eine Willkommensnachricht senden.

Eine Willkommensnachricht ist die beste Möglichkeit, um den Ton für Ihren persönlichen/Chat-bot festzulegen. Dies ist die erste Interaktion, die ein Benutzer mit dem Bot hat. Eine gute Willkommensnachricht kann den Benutzer ermutigen, die APP weiterhin zu erkunden. Wenn die Begrüßung oder einleitende Nachricht verwirrend oder unklar ist, sehen Benutzer den Wert der APP nicht sofort und verlieren ihre Interessen.
Im folgenden finden Sie Informationen zu den Anforderungen für willkommene Nachrichten.

> [!Note]
> Eine Willkommensnachricht ist optional für einen Kanal-bot.

### <a name="welcome-message-requirements"></a>Anforderungen für Willkommensnachrichten

* Fügen Sie einen Wert Vorschlag mit der Willkommens Tour ein.
* Bereitstellen von Anleitungen für die Verwendung der app.
* Anleitungen zum Registrieren und Konfigurieren Ihrer APP einschließen
* Präsentieren Sie einfach lesbaren Text und einfachen Dialog – vorzugsweise eine Karte mit einer Aktions baren Willkommens Tour-Schaltfläche, die einen Aufgabenmodul lädt.
* Halten Sie es einfach und nutzbar mit Schaltflächen und Karten-vermeiden Sie langen Text, gesprächig Dialog.
* Integrieren Sie Adaptive Karten und Schaltflächen, um die Begrüßungsnachricht nutzbar zu machen.
* Rufen Sie die Willkommensnachricht mit einem Ping-Befehl auf, nicht mit mindestens zwei gleichzeitigen Pings.
* Eine Willkommensnachricht darf nur dem Benutzer angezeigt werden, der die APP konfiguriert hat, vorzugsweise in einem 1:1 persönlichen Chat.
* Persönliche apps müssen einem Benutzer immer eine Willkommensnachricht bereitstellen.
* Senden Sie nie einen persönlichen Chat an alle Mitglieder des Teams-dies wird als Spam betrachtet.
* Senden Sie die Willkommensnachricht niemals mehrmals. Das Wiederholen derselben Willkommensnachricht über regelmäßige Intervalle ist nicht zulässig und wird als Spam betrachtet.

#### <a name="avoid-welcome-message-spamming"></a>Vermeiden von Begrüßungsnachrichten-Spam

* **Kanal Nachricht von bot**. Keine Spam-Benutzer durch Erstellen separater neuer Chat Beiträge. Erstellen Sie einen einzelnen Thread Beitrag mit Antworten im gleichen Thread.
* **Persönlicher Chat von bot**. Senden Sie keine mehrere Nachrichten. Senden Sie eine Nachricht mit vollständigen Informationen. Das Wiederholen derselben Willkommensnachricht über regelmäßige Intervalle ist nicht zulässig und wird als Spam betrachtet.

#### <a name="notification-only-bot-welcome-messages"></a>Willkommens Meldungen nur für Benachrichtigungen

Nur Benachrichtigungs Bots müssen eine Willkommensnachricht senden, die eine Nachricht mit dem Hinweis *"Ich bin ein nur-Benachrichtigungs-bot" ist und nicht auf Ihre Chats Antworten* kann.

#### <a name="welcome-messages-in-the-personal-scope"></a>Begrüßungsnachrichten im persönlichen Bereich

* **Machen Sie Ihre Nachricht prägnant und informativ**.  Höchstwahrscheinlich sind die Benutzerfreundlichkeit und das Wissen über Ihre APP unterschiedlich. Ein Benutzer hat Ihre APP möglicherweise auf einer anderen Plattform verwendet oder hat nichts über Ihre App erfahren. Sie möchten Ihre Nachricht an alle Zielgruppen anpassen und in einigen Sätzen erklären, was Ihr bot tut und wie er mit ihm interagieren kann. Sie sollten auch den Wert der APP erläutern und erfahren, wie die Benutzer davon profitieren.
![Cafe und ESS-bot](~/assets/images/faq/cafe-bot.png)

* **Machen Sie Ihre Nachricht Handlungs** bereit. Denken Sie an das erste, was Benutzer nach der Installation Ihrer APP tun sollen. Gibt es einen coolen Befehl, den Sie ausprobieren sollten? Gibt es eine weitere Onboarding-Erfahrung, die Sie kennen sollten? Müssen die Benutzer sich anmelden? Sie können Aktionen auf einer adaptiven Karte hinzufügen oder bestimmte Beispiele wie *"versuchen Sie Fragen...."* , *"Dies ist, was ich tun kann..."* bereitstellen.

#### <a name="welcome-messages-in-the-teamchannel--scope"></a>Begrüßungsnachrichten im Team/Kanal-Bereich

Die Dinge sind ein bisschen anders, wenn der bot zum ersten Mal einem Kanal hinzugefügt wird. Normalerweise sollten Sie keine 1:1-Nachricht an alle Benutzer im Team senden, aber der Bot kann eine Willkommensnachricht im Kanal senden.

### <a name="9989-mobile-responsiveness-no-direct-upsell-or-payment"></a>&#9989; Mobile Reaktionsfähigkeit, kein direktes Upselling oder Zahlung
* Ihre Registerkarten, Adaptive Karten, bot-Nachrichten und Inhalte in Aufgaben Modulen müssen für varios-Bildschirme mit mobilen Geräten reagieren.
* Apps, die IOS unterstützen, müssen auf dem neuesten iPad-Gerät mit der neuesten Version von IOS voll funktionsfähig sein.
* Dürfen keine direkten Bezüge zu in-App-Käufen, Test angeboten, Benutzeroberflächen, die auf kostenpflichtige Versionen upsellen sollen, oder Links zu Online Shops einschließen, in denen Benutzer andere Inhalte, Apps oder Add-Ins aus Ihrer Teams-app unter mobilen Betriebssystemen (Android, IOS) erwerben oder erwerben können.
* Die IOS-oder Android-Version des Add-Ins darf keine Benutzeroberfläche oder Sprache oder einen Link zu anderen apps, Add-Ins oder einer Website anzeigen, die den Benutzer zum bezahlen auffordern.
* Die zugehörigen Datenschutzrichtlinien und Nutzungsbedingungen-Seiten müssen ebenfalls frei von beliebigen Commerce-UI-oder Store-Links sein.

### <a name="9989-do-not-post-sensitive-data-to-an-audience-not-intended-to-view-the-data"></a>&#9989; keine vertraulichen Daten für eine Zielgruppe bereitstellen, die nicht zum Anzeigen der Daten vorgesehen ist
Ihre Teams-App darf keine vertraulichen Informationen wie Kreditkarten-/Finanzinstrumente, personenbezogene Informationen, Integrität oder Kontakt Ablaufverfolgungsinformationen an eine Zielgruppe senden, die diese Daten nicht anzeigen soll.

### <a name="9989-do-not-transmit-financial-payment-details-or-complete-financial-transactions-via-your-teams-app"></a>&#9989; keine finanziellen Zahlungsdetails oder vollständige Finanztransaktionen über ihre Teams-App übermitteln
* Ihre Teams-App darf Benutzer nicht bitten, direkt innerhalb der Teams-Schnittstelleeine Zahlung zu tätigen
* Apps übermitteln möglicherweise keine Finanzinstrumenten Details über den Benutzer auf der App-Schnittstelle. Apps senden möglicherweise nur Links zu sicheren Zahlungsdiensten an Benutzer, wenn diese in den Nutzungsbedingungen, der Datenschutzrichtlinie und auf jeder Profilseite oder Website für die APP offen gelegt werden, bevor ein Benutzer einverstanden ist, die APP zu verwenden.

### <a name="9989-clear-warning-before-downloading-any-files-or-exes-into-users-environment"></a>&#9989; deutliche Warnung vor dem Herunterladen von Dateien oder exe-Dateien in die Umgebung des Benutzers
Warnen Sie die Benutzer, bevor Ihre APP Dateien oder exe-Dateien in den Computer oder die Umgebung des Benutzers herunterlädt.


> [!div class="nextstepaction"]
> [Weitere Informationen zu Teams-App-Genehmigungsrichtlinien](/legal/marketplace/certification-policies#1140-teams) 
