---
title: Microsoft Teams Richtlinien für die Speicherüberprüfung
description: Beschreibt die Richtlinien, die jede an den Teams Store (AppSource) übermittelte App befolgen muss.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 79cdc032ee1e7479f7737e5dc71f8f01bb024da8
ms.sourcegitcommit: 25539046d408c4270b988fd826d7cf1275f4b9dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2021
ms.locfileid: "52763115"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Microsoft Teams Richtlinien für die Speicherüberprüfung

Die Einhaltung dieser Richtlinien erhöht die Wahrscheinlichkeit, dass Ihre App den Microsoft Teams Store-Übermittlungsprozess übergibt. Diese Teams-spezifischen Richtlinien ergänzen die Zertifizierungsrichtlinien für den [kommerziellen Microsoft-Marketplace](/legal/marketplace/certification-policies) und werden häufig aktualisiert, um neue Funktionen, Benutzerfeedback und Änderungen an Geschäftsregel zu berücksichtigen.

> [!NOTE]
> Einige Richtlinien gelten möglicherweise nicht für Ihre App. Wenn Ihre App beispielsweise keinen Bot enthält, können Sie botbezogene Richtlinien ignorieren.

## <a name="value-proposition"></a>Wertversprechen

### <a name="app-name"></a>App-Name

Der Name einer App spielt eine wichtige Rolle dabei, wie Benutzer ihn im Store entdecken. Denken Sie an Folgendes zu App-Namen:

* Der Name muss Ausdrücke enthalten, die für Ihre Benutzer relevant sind.
* Namen der wichtigsten Teams Features&#8212;wie **Chat,** **Kontakte,** **Kalender,** **Anrufe,** **Dateien,** **Aktivitäten,** **Teams,** **Apps** und **Hilfe**&#8212;sollten nicht im App-Namen enthalten sein.
* Häufig verwendete Substantivs müssen mit dem Namen des Entwicklers (z. B. **Contoso Tasks** statt **Tasks)** vorangestellt oder suffixed sein.
* Darf keine **Teams** oder andere Microsoft-Produktnamen verwenden, die fälschlicherweise auf Co-Branding oder Co-Verkauf hindeuten. (Weitere Informationen zum Verweisen auf Microsoft-Software, -Produkte und -Dienste finden Sie in den [Microsoft-Richtlinien für Marken und Marken](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)).
* Wenn Ihre App Teil einer offiziellen Partnerschaft mit Microsoft ist, muss der Name Ihrer App zuerst kommen (z. **B. Contoso Connector für Microsoft Teams).**
* Der Name einer im Store oder einem anderen Angebot auf dem kommerziellen Marketplace aufgeführten App darf nicht kopiert werden.
* Darf keine profanen oder abfälligen Ausdrücke enthalten. Der Name darf auch keine rassisch oder kulturunabhängige Sprache enthalten.
* Muss eindeutig sein. Beispielsweise können Sie nicht mehrere Apps für verschiedene Regionen mit demselben Namen und derselben Funktionalität auflisten.

### <a name="suitable-for-workplace-consumption"></a>Geeignet für den Arbeitsplatzverbrauch

App-Inhalte müssen für die allgemeine Nutzung am Arbeitsplatz geeignet sein und alle Einschränkungen einhalten, die in den Zertifizierungsrichtlinien für den kommerziellen Marketplace aufgeführt sind. Inhalte im Zusammenhang mit Musik, Politik, Theater und längerer Unterhaltung sind nicht zulässig. Weitere Informationen finden Sie in den Zertifizierungsrichtlinien für [den kommerziellen Marketplace.](/legal/marketplace/certification-policies#10010-inappropriate-content)

Ihre App muss die Zusammenarbeit in Gruppen erleichtern, die Produktivität einer Person verbessern oder beides. Apps, die für Teambindungen und Gruppierungen vorgesehen sind, müssen für die Zusammenarbeit und für mehrere Teilnehmer konzipiert sein. Diese Arten von Apps sollten auch keinen erheblichen Zeitaufwand erfordern oder die Produktivität in empfänglicher Weise beeinträchtigen.

### <a name="similar-platforms-and-services"></a>Ähnliche Plattformen und Dienste

Apps müssen sich auf die Teams Konzentrieren und dürfen keine Namen, Symbole oder Bilder anderer ähnlicher Chat-basierter Plattformen oder Dienste für die Zusammenarbeit enthalten, es sei denn, Ihre App bietet spezifische Interoperabilität.

### <a name="feature-names"></a>Featurenamen

App-Featurenamen in Schaltflächen und anderer Benutzeroberflächentext dürfen nicht mit der Terminologie in Konflikt geraten, die für Teams und andere Microsoft-Produkte reserviert ist. Beispiel: **Besprechung starten,** **Anruf tätigen** oder **Chat starten.** Fügen Sie Ihren App-Namen ein, wenn Sie dies nicht vollständig vermeiden können, z. **B. "Contoso-Besprechung starten"** anstelle von **"Besprechung starten".**

## <a name="security"></a>Sicherheit

### <a name="microsoft-365-app-compliance-program"></a>Microsoft 365 Compliance-Programm

Das [Microsoft 365 App Compliance-Programm](/microsoft-365-app-certification/overview) soll Organisationen dabei helfen, Risiken zu bewerten und zu verwalten, indem Sicherheits- und Complianceinformationen zu Ihrer App ausgewertet werden. Wenn Sie eine App im Teams Store veröffentlichen, müssen Sie die folgenden Stufen des Programms ausführen:

* [Publisher Überprüfung:](/azure/active-directory/develop/publisher-verification-overview)Hilft Administratoren und Endbenutzern, die Authentizität von App-Entwicklern zu verstehen, die sich in die Microsoft Identity Platform integrieren. Nach Abschluss des Vorgangs wird ein blaues Signal "bestätigt" im Zustimmungsdialogfeld Azure Active Directory (Azure AD) und auf anderen Bildschirmen angezeigt. Weitere Informationen finden Sie unter [häufig gestellte Fragen,](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions) [wie Sie Ihre App als herausgebergeprüft kennzeichnen](/azure/active-directory/develop/mark-app-as-publisher-verified)und problembehandlung bei der [Herausgeberüberprüfung](/azure/active-directory/develop/troubleshoot-publisher-verification)durchführen.
* [Publisher Nachweis:](/microsoft-365-app-certification/docs/attestation)Ein Prozess, bei dem Sie allgemeine, Datenverarbeitungs- und Sicherheits- und Complianceinformationen freigeben, um potenziellen Kunden zu helfen, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine App übermitteln, die zuvor nicht aufgeführt wurde, können Sie Publisher Nachweis erst offiziell abschließen, wenn sich Ihre App im Teams Store befindet. Wenn Sie eine aufgeführte App aktualisieren, führen Sie Publisher Attestation aus, bevor Sie die neueste Version der App übermitteln.

### <a name="bots"></a>Bots

Für Apps, die den Microsoft Azure Bot-Dienst verwenden (z. B. Bots und Messaging-Erweiterungen), müssen Sie alle anforderungen erfüllen, die in den [Microsoft Online Services-Nutzungsbedingungen](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)definiert sind.

Bots müssen immer die Berechtigung zum Hochladen einer Datei anfordern und nach dem Hochladen der Datei eine Bestätigungsmeldung anzeigen.

### <a name="external-domains"></a>Externe Domänen

In den meisten Fällen dürfen Sie keine Domänen außerhalb der Kontrolle Ihrer Organisation (einschließlich Platzhalter) und Tunneldienste in die Domänenkonfigurationen Ihrer App einschließen. Zu den folgenden Ausnahmen gehören:

* Wenn Ihre App die OAuthCard des Azure Bot Service verwendet, müssen Sie sie als gültige Domäne einschließen, `token.botframework.com` sonst funktioniert die **Anmeldeschaltfläche** nicht.
* Wenn Ihre App SharePoint verwendet, können Sie die zugeordnete Stamm SharePoint Website mithilfe der Kontexteigenschaft als gültige Domäne `{teamSiteDomain}` einschließen.

### <a name="authentication"></a>Authentifizierung

Informationen zum Implementieren der App-Authentifizierung finden Sie [unter "Authentifizierung" in Teams.](~/concepts/authentication/authentication.md)

#### <a name="authenticating-with-external-services"></a>Authentifizieren mit externen Diensten

Beachten Sie Folgendes, wenn Ihre App Benutzer mit einem externen Dienst authentifiziert.

* **Melden Sie sich an, melden Sie sich ab und registrieren Sie sich:**
  * Apps, die von externen Konten oder Diensten abhängen, müssen eine klare und einfache Anmelde-, Abmelde- und Registrierungserfahrung bereitstellen.
  * Wenn sich ein Benutzer abmeldet, muss er sich nur von der App abmelden und bei Teams angemeldet bleiben.
* Erfahrungen mit der **Inhaltsfreigabe:** Apps, die eine Authentifizierung mit einem externen Dienst erfordern, um Inhalte in Teams Kanälen freizugeben, müssen in der Hilfedokumentation (oder ähnlichen Ressourcen) deutlich angeben, wie Inhalte getrennt oder freigegeben werden können, wenn dieses Feature für den externen Dienst unterstützt wird. Dies bedeutet nicht, dass die Möglichkeit, die Freigabe von Inhalten aufzuheben, in Ihrer Teams App vorhanden sein muss.

#### <a name="government-community-cloud-listings"></a>Government Community Cloud-Einträge

Um Ihre App an Government Community Cloud (GCC)-Benutzer zu verteilen und doppelte Einträge im Teams Store zu vermeiden, muss der Authentifizierungsprozess Benutzer identifizieren und an eine GCC spezifische oder erwartete URL weiterleiten.

### <a name="sensitive-content"></a>Vertrauliche Inhalte

Ihre App darf keine vertraulichen Daten veröffentlichen, z. B. Kreditkarten- oder Finanzdaten. Die App darf einer Zielgruppe, die diese Inhalte nicht anzeigen möchte, keine Integrität, Kontaktablaufverfolgung oder andere personenbezogene Informationen (PII) anzeigen.

Warnen Sie Benutzer, bevor Ihre App Dateien oder ausführbare Dateien (.exe) auf den Computer oder die Umgebung des Benutzers herunterlädt.

### <a name="financial-information"></a>Finanzinformationen

Apps dürfen Benutzer nicht auffordern, Zahlungen innerhalb der Teams-Schnittstelle zu tätigen. Details zu Finanzinstituten dürfen nicht über eine Bot-Schnittstelle an Benutzer übertragen werden.

Sie dürfen nur dann zu sicheren externen Zahlungsdiensten verlinken, wenn Sie die entsprechende Offenlegung in Ihren Nutzungsbedingungen, Datenschutzrichtlinien oder profilseitigen Seiten oder Websites vorgenommen haben, bevor der Benutzer der Verwendung der App zugestimmt hat.

Apps, die unter der iOS- oder Android-Version von Teams ausgeführt werden, müssen die folgenden Richtlinien einhalten:

* Apps dürfen keine In-App-Käufe, Testangebote oder Benutzeroberflächen enthalten, die auf das Upselling kostenpflichtiger Versionen oder Links zu Onlinestores abzielen, in denen Benutzer andere Inhalte, Apps oder Add-Ins kaufen oder erwerben können.
* Wenn Ihre App ein Konto erfordert, müssen sich Benutzer kostenlos für ein Konto registrieren können. Die Verwendung des Begriffs **"kostenloses** oder **kostenloses Konto"** ist nicht zulässig.
* Sie können bestimmen, ob ein Konto unbegrenzt oder für einen begrenzten Zeitraum aktiv ist, aber wenn das Konto abläuft, werden möglicherweise keine Benutzeroberfläche, kein Text oder Links angezeigt, die die Notwendigkeit der Zahlung angeben.
* Die Datenschutzrichtlinien und Nutzungsbedingungen Ihrer App müssen frei von E-Commerce-bezogenen Benutzeroberflächen oder Links sein.

## <a name="general-functionality-and-performance"></a>Allgemeine Funktionalität und Leistung

### <a name="launching-external-functionality"></a>Starten externer Funktionen

Apps dürfen Benutzer nicht aus Teams für die wichtigsten Benutzerszenarien entfernen. App-Inhalte und -Interaktionen können innerhalb Teams Funktionen erfolgen, z. B. Bots, Karten und Aufgabenmodule.

Sie sollten Benutzer an Teams und nicht mit einer externen Website oder App verknüpfen. Für Szenarien, die externe Funktionen erfordern, muss Ihre App über eine explizite Benutzerberechtigung verfügen, um diese Funktionalität zu starten.

### <a name="compatibility"></a>Kompatibilität

Apps müssen unter den folgenden Betriebssystemen und Browsern voll funktionsfähig sein:

* Microsoft Windows 7 und höher
* macOS 10.10 und höher
* Microsoft Edge 12 und höher
* Mozilla Firefox 47.0 und höher
* Google Chrome 51.0 und höher
* iOS 9.0 und höher
* Android 4.4 und höher

### <a name="response-time"></a>Antwortzeit

Teams Apps müssen innerhalb eines angemessenen Zeitrahmens reagieren, der je nach Funktion unterschiedlich ist.

* Registerkarten müssen innerhalb von drei Sekunden reagieren oder eine Lademeldung oder Warnung anzeigen.
* Bots müssen innerhalb von zwei Sekunden auf Benutzerbefehle reagieren oder eine Eingabeanzeige anzeigen.
* Messaging-Erweiterungen müssen innerhalb von fünf Sekunden auf Benutzerbefehle reagieren.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

## <a name="app-package-and-store-listing"></a>App-Paket und Store-Eintrag

App-Pakete müssen korrekt formatiert sein und alle erforderlichen Informationen und Komponenten enthalten.

### <a name="app-manifest"></a>App-Manifest

Das Teams App-Manifest definiert die Konfigurationen Ihrer App.

* Ihr Manifest muss dem neuesten Manifestschema entsprechen. Weitere Informationen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md)
* Wenn Ihre App eine Bot- oder Messaging-Erweiterung enthält, muss Ihr Manifest mit Bot Framework-Metadaten konsistent sein, einschließlich Bot-Name, Logo, Link zur Datenschutzrichtlinie und Link zu Nutzungsbedingungen.
* Wenn Ihre App Azure Active Directory (Azure AD) für die Authentifizierung verwendet, fügen Sie die Azure AD-Anwendungs-ID (Client-ID) in das Manifest ein. Weitere Informationen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md#webapplicationinfo)

### <a name="app-icons"></a>App-Symbole

Symbole sind eines der Hauptelemente, die Benutzern beim Durchsuchen des Teams Store angezeigt werden. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig die folgenden Anforderungen erfüllen:

* Ihr App-Paket muss zwei PNG-Versionen des App-Symbols enthalten: ein Farbsymbol und ein Gliederungssymbol.
* Die Farbversion ihres Symbols wird in den meisten Teams Szenarien angezeigt und muss 192 x 192 Pixel groß sein. Das Symbolsymbol (96 x 96 Pixel) kann eine beliebige Farbe oder Farbe sein, muss sich jedoch auf einem durchgezogenen oder vollständig transparenten quadratischen Hintergrund befinden.
* Die Gliederungsversion Ihres Symbols wird angezeigt, wenn Ihre App verwendet und auf der App-Leiste auf der linken Seite von Teams "verschoben" wird und wenn ein Benutzer die Messaging-Erweiterung Ihrer App anheftet. Sie muss 32 x 32 Pixel groß sein und kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig). Das Symbol sollte keinen zusätzlichen Abstand um das Symbol aufweisen.
* Symbole mit korrekter Größe und Formatierung müssen in Ihrem App-Paket enthalten sein. Die Symbole müssen auch mit den Metadaten des Store-Eintrags übereinstimmen, die übermittelt werden.

Weitere Informationen, bewährte Methoden und Beispiele finden Sie in den Richtlinien für Teams [App-Symbole.](~/concepts/build-and-test/apps-package.md#app-icons)

### <a name="app-descriptions"></a>App-Beschreibungen

Sie benötigen eine kurze und lange Beschreibung Ihrer App. Die Beschreibungen in Ihren App-Konfigurationen und Partner Center müssen identisch sein.

Beschreibungen sollten nicht direkt oder durch Insinuation eine andere Marke unterscheiden (Im Besitz von Microsoft oder auf andere Weise). Stellen Sie sicher, dass Ihre Beschreibung keine Ansprüche enthält, die nicht verhindert werden können (z. B. "Garantierte Effizienzsteigerung von 200 Prozent").

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Beschreibung ist eine kurze Zusammenfassung Ihrer App, die deren Wertversprechen hervorhebt und an Ihre Zielgruppe gerichtet ist.

**Dos:**

* Behalten Sie die kurze Beschreibung auf einen Satz bei.
* Die wichtigsten Informationen kommen an erster Stelle.
* Schließen Sie Schlüsselwörter ein, nach denen Kunden wahrscheinlich suchen.

**Don’ts:**

* Wiederholen Sie den App-Namen.
* Verwenden Sie das Wort **"App"** in der Kurzbeschreibung.

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine ansprechende Darstellung liefern, die das Wertversprechen Ihrer App, die primäre Zielgruppe und die Zielbranche hervorhebt. Obwohl diese Beschreibung bis zu 4.000 Zeichen umfassen kann, lesen die meisten Benutzer nur zwischen 300 und 500 Wörter.

**Dos:**

* Verwenden Sie [Markdown,](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) um Ihre Beschreibung zu formatieren.
* Verwenden Sie aktive Sprache, und sprechen Sie direkt mit Benutzern. Sie können z. *B. ...*
* Auflisten von Features mit Aufzählungspunkten, sodass es einfacher ist, die Beschreibung zu überprüfen.
* Beschreiben Sie einschränkungen, Bedingungen oder Ausnahmen für die Funktionalität, Features und Lieferumfang, die im Eintrag und den zugehörigen Materialien beschrieben sind, bevor der Benutzer Ihre App installiert. Die Teams Funktionen, die Ihre App unterstützt, müssen sich auf die Kernfunktionen beziehen, die in Ihrem Eintrag beschrieben werden.
* Fügen Sie einen Hilfe- oder Supportlink hinzu.
* Verweisen Sie auf **Microsoft 365** anstelle **von Office 365.**
* Wenn Sie **auf Teams** verweisen müssen, schreiben Sie den ersten Verweis als **Microsoft Teams**. Nachfolgende Verweise können auf **Teams** gekürzt werden.
* Verwenden Sie die folgende Sprache, wenn Sie die Funktionsweise der App mit Teams (oder Microsoft 365) beschreiben:
  * "... funktioniert mit Microsoft Teams."
  * "... arbeiten mit Microsoft Teams."
  * "... in Microsoft Teams."
  * "... für Microsoft Teams."

**Don’ts:**

* Überschreitet 500 Wörter.
* Kürzen Sie **Microsoft** als **MS** oder **MSFT.**
* Geben Sie an, dass es sich bei der App um ein Angebot von Microsoft handelt, einschließlich der Verwendung von Microsoft-Parolen oder Taglines.
* Verwenden Sie geschützte Marken, die Sie nicht besitzen.
* Schließen Sie Tippfehler, Grammatikfehler und unnötige Groß-/Kleinschreibungen ein (z. **B. Benutzer** anstelle von **Benutzern).**
* Links zu AppSource einschließen.
* Verwenden Sie die folgende Sprache, es sei denn, Sie sind ein zertifizierter Microsoft-Partner:
  * "... in Microsoft Teams integriert"
  * "... integrations with ..."
  * "... erstellt für ..."
  * "... basierend auf ..."
  * "... wird auf ..." ausgeführt.
  * "... aktiviert durch ..."
  * "... zertifiziert für ..."
  * "... entwickelt für ..."
  * "... entwickelt für ..."

### <a name="screenshots"></a>Screenshots

Screenshots bieten eine ansprechende visuelle Vorschau Ihrer App, um den App-Namen, das Symbol und die Beschreibungen zu ergänzen. Denken Sie an Folgendes zu Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag haben.
* Unterstützte Dateitypen sind PNG, JPEG und GIF.
* Die Abmessungen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1.024 KB.

**Dos:**

* Konzentrieren Sie sich auf die Funktionen Ihrer App (z. B. wie Benutzer mit Ihrem Bot kommunizieren können).
* Fügen Sie Inhalte ein, die Ihre App genau darstellen.
* Verwenden Sie Text mit Bedacht.
* Rahmen-Screenshots mit einer Farbe, die Ihre Marke widerspiegelt und Marketinginhalte enthält, ähnlich wie im [Freshdesk-Eintragsbeispiel](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) (Dimensionsanforderungen gelten für das gesamte Bild und nicht nur für den Screenshot).

**Don’ts:**

* Zeigen Sie bestimmte Geräte an, z. B. Smartphones oder Laptops.
* Anzeigen von Chrom oder UI, das sich nicht in Ihrer App befindet.
* Erfassen Sie alle Teams oder Browser-UI in Ihren Screenshots.
* Schließen Sie Mockups ein, die die tatsächliche Benutzeroberfläche Ihrer App ungenau wiedergeben, z. B. anzeigen, dass Ihre App außerhalb von Teams verwendet wird.

> [!TIP]
> Ein Video kann die effektivste Methode sein, um zu kommunizieren, warum Benutzer Ihre App verwenden sollten. Ein Video ist auch das erste, was Benutzer in Ihrem Eintrag sehen (standardmäßig wird ein Video vor Screenshots angezeigt). Weitere Informationen finden Sie unter [Erstellen eines Videos für Ihren Store-Eintrag.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video)

### <a name="privacy-policy"></a>Datenschutz

Die Datenschutzrichtlinie kann spezifisch für Ihre Teams-App oder eine allgemeine Richtlinie für alle Ihre Dienste sein.

* Wenn Sie eine generische Datenschutzrichtlinienvorlage verwenden, müssen Sie auf **Dienste,** **Anwendungen** und **Plattformen** verweisen, um Ihre Teams-App und Ihren Dienst oder Ihre Website einzuschließen.
* Muss angeben, wie Sie mit der Speicherung, Aufbewahrung und Löschung von Benutzerdaten umgehen. Sie müssen auch die Sicherheitskontrollen beschreiben, die Sie für den Datenschutz verwenden.
* Muss Ihre Kontaktinformationen enthalten.
* Sollte keine URLs enthalten, die fehlerhaft sind oder für Beta- oder Stagingzwecke verwendet werden.
* Darf keine Links zu AppSource enthalten.

### <a name="terms-of-use"></a>Nutzungsbedingungen

Ihre Nutzungsbedingungen sollten spezifisch sein und für Ihr Angebot gelten.

### <a name="support-links"></a>Supportlinks

Für die Support-URLs Ihrer App sollte keine Authentifizierung erforderlich sein. Benutzer sollten sich beispielsweise nicht anmelden müssen, um Sie zu kontaktieren.

### <a name="localization"></a>Lokalisierung

Wenn Ihre App die Lokalisierung unterstützt, muss Ihr App-Paket eine Datei mit Sprachübersetzungen enthalten, die basierend auf der Teams Spracheinstellung angezeigt werden. Die Datei muss dem Teams Lokalisierungsschema entsprechen. Weitere Informationen finden Sie im [Teams Lokalisierungsschema.](~/concepts/build-and-test/apps-localization.md)

## <a name="tabs"></a>Registerkarten

Wenn Ihre App eine Registerkarte enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Designrichtlinien für Teams Registerkarten.](~/tabs/design/tabs.md)

### <a name="setup"></a>Setup

* Die Registerkarteneinrichtung darf für einen neuen Benutzer kein Sackgassen-Ende sein. Geben Sie eine Nachricht zum Abschließen der Aktion oder des Workflows an.
* Die Authentifizierung sollte während der Registerkarteneinrichtung und nicht danach erfolgen.

### <a name="views"></a>Ansichten

* Der Anmeldebildschirmbereich darf keine großen Logos verwenden oder eine ganze Webseite anzeigen.
* Inhalte können vereinfacht werden, indem sie auf mehrere Registerkarten verteilt werden.
* Registerkarten sollten keine doppelte Kopfzeile haben. Entfernen Sie das Logo aus dem iframe, da das Registerkartenframework bereits das App-Symbol und den App-Namen anzeigt.

### <a name="navigation"></a>Navigation

* Registerkarten dürfen nicht mehr als drei Navigationsebenen aufweisen.
* Registerkarten dürfen keine Navigation bereitstellen, die mit der primären Teams Navigation in Konflikt steht.
* Die sekundären und sekundären Seiten in einer Registerkarte müssen in einer Ansicht der Ebene 2 und ebene 3 im Hauptregisterkartenbereich geöffnet werden, der über Breadcrumbs oder die linke Navigation navigiert wird. Sie können auch die folgenden Komponenten einschließen, um die Registerkartennavigation zu unterstützen:
    * Zurück-Schaltflächen
    * Seitenüberschriften
    * Hamburger-Menüs
* Registerkarte sollte keinen horizontalen Bildlauf aufweisen.
* Deep-Links in Registerkarten dürfen nicht mit einer externen Webseite, sondern an einer Stelle innerhalb Teams verknüpft werden. Beispielsweise Aufgabenmodule oder andere Registerkarten.
* Registerkarten sollten es Benutzern nicht ermöglichen, außerhalb Teams für die Kern-App-Erfahrung zu navigieren.

### <a name="usability"></a>Usability

* Registerkarten müssen über das Hosten einer vorhandenen Website hinausgehen.
* Benutzer müssen in der Lage sein, ihre letzte Aktion auf der Registerkarte rückgängig zu machen.
* Registerkarten in einem persönlichen Kontext können Inhalte aus freigegebenen Instanzen der App aggregieren.
* Registerkarten müssen auf Teams Designs reagieren. Wenn ein Benutzer das Design ändert, muss das Design der App die Auswahl widerspiegeln.
* Registerkarten müssen nach Möglichkeit Teams Komponenten verwenden, z. B. Teams Schriftarten, Typhierarchien, Farbpaletten, Rastersystem, Bewegung, Tonfall der Stimme usw.
* Sie müssen eine **Einstellungen** Registerkarte einschließen.
* Registerkarten müssen Teams Interaktionsdesign folgen, z. B. Seitennavigation, Position und Verwendung von Dialogfeldern, Informationshierarchien usw., wann immer möglich.
* Registerkarteninhalte im iframe dürfen keine Features enthalten, die Teams Kernfunktionen imitieren. Beispielsweise Bots, Messaging-Erweiterungen, Anrufe, Besprechungen usw.

> [!TIP]
>
> * Fügen Sie einen persönlichen Bot zusammen mit einer persönlichen Registerkarte hinzu.
> * Zulassen, dass Benutzer Inhalte über ihre persönliche Registerkarte freigeben können.

## <a name="bots"></a>Bots

Wenn Ihre App einen Bot enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Teams Bot-Entwurfsrichtlinien.](~/bots/design/bots.md)

### <a name="bot-commands"></a>Bot-Befehle

Die Analyse der Benutzereingabe und die Vorhersage der Benutzerabsicht ist schwierig. Bot-Befehle stellen Benutzern eine Reihe von Wörtern oder Ausdrücken bereit, die Ihr Bot versteht, damit sie (und Ihr Bot) nicht erraten müssen.

* Es wird dringend empfohlen, unterstützte Bot-Befehle in Ihren App-Konfigurationen aufzulisten. Diese Befehle werden im Feld zum Verfassen angezeigt, wenn ein Benutzer versucht, ihren Bot zu melden.
* Alle Befehle, die Ihr Bot unterstützt, müssen ordnungsgemäß funktionieren, einschließlich des Befehls **"Hallo",** **"Hello"** und **"Hilfe".**

> [!TIP]
> Fügen Sie für persönliche Bots eine **Registerkarte "Hilfe"** hinzu, die weiter beschreibt, was Ihr Bot tun kann.

### <a name="bot-welcome-messages"></a>Bot-Willkommensnachrichten

* Bots sollten bei der ersten Ausführung fast immer eine Willkommensnachricht senden. Um eine optimale Erfahrung zu erzielen, sollte die Nachricht das Wertversprechen Ihres Bots, die Konfiguration des Bots und die kurz beschriebenen unterstützten Botbefehle enthalten. Sie können die Nachricht mit einer adaptiven Karte mit Schaltflächen anzeigen, um die Benutzerfreundlichkeit zu verbessern. Weitere Informationen finden Sie unter [Auslösen einer Bot-Willkommensnachricht.](~/bots/how-to/conversations/send-proactive-messages.md)
* Bot-Willkommensnachrichten in Kanälen und Chats sind bei der ersten Ausführung optional, insbesondere, wenn der Bot für den persönlichen Gebrauch verfügbar ist und ähnliche Aktionen ausführt. Wenn Ihr Bot Begrüßungsnachrichten sendet, darf er diese nicht einzeln an Benutzer senden (dies gilt als [Spamming).](#bot-message-spamming) In der Nachricht sollte auch die Person erwähnt werden, die den Bot hinzugefügt hat.
* Nur-Benachrichtigung-Bots müssen eine Willkommensnachricht senden, die vermittelt, dass sie nicht auf Benutzernachrichten antwortet.

> [!TIP]
> In Willkommensnachrichten an einzelne Benutzer kann eine Karussell-Tour einen effektiven Überblick über Ihren Bot und alle anderen App-Features bieten. Das Einschließen von Schaltflächen, mit derenHilfe Benutzer Bot-Befehle ausprobieren können, wird empfohlen. Erstellen Sie z. B. **eine Aufgabe.**

### <a name="bot-message-spamming"></a>Bot-Nachrichtenspaming

Bots dürfen Keine Spam-Benutzer senden, indem sie mehrere Nachrichten in kurzer Folge senden.

* **Bot-Nachrichten in Kanälen und Chats:** Spamen Sie Benutzer nicht, indem Sie separate Beiträge erstellen. Erstellen Sie einen einzelnen Beitrag mit Antworten im selben Thread.
* **Bot-Nachrichten in persönlichen Apps:** Senden Sie nicht mehrere Nachrichten in schneller Folge. Senden Sie eine Nachricht mit vollständigen Informationen. Vermeiden Sie mehrfache Unterhaltungen, um einen einzelnen Workflow abzuschließen. Erwägen Sie stattdessen die Verwendung eines Formulars (oder Aufgabenmoduls), um alle Eingaben eines Benutzers gleichzeitig zu erfassen.
* **Willkommensnachrichten:** Das Wiederholen derselben Willkommensnachricht in regelmäßigen Intervallen ist nicht zulässig und wird als Spamming betrachtet. Wenn z. B. ein neues Mitglied zu einem Team hinzugefügt wird, spammen Sie die anderen Mitglieder nicht mit einer Willkommensnachricht. Senden Sie dem neuen Mitglied stattdessen eine persönliche Nachricht.

### <a name="bot-notifications"></a>Bot-Benachrichtigungen

Bot-Benachrichtigungen müssen Inhalte enthalten, die für den Bereich relevant sind, den Sie für den Bot definieren (Team, Chat oder persönlich).

### <a name="bots-and-adaptive-cards"></a>Bots und adaptive Karten

Adaptive Karten sind eine dringend empfohlene Methode zum Anzeigen von Bot-Nachrichten. Ihre Karten müssen einfach sein und nur 1 bis 3 Aktionen enthalten. Wenn Sie mehr Inhalte anzeigen müssen, sollten Sie ein Aufgabenmodul oder eine Registerkarte verwenden.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Entwerfen Adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Karten-Referenz](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="messaging-extensions"></a>Messaging-Erweiterungen

Wenn Ihre App eine Messaging-Erweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Teams Messaging-Erweiterungen.](~/messaging-extensions/design/messaging-extension-design.md)

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbasierte Messaging-Erweiterungen sollten Folgendes tun:

* Zulassen, dass Benutzer Aktionen für eine Nachricht auslösen, ohne Zwischenschritte auszuführen, z. B. die Anmeldung.
* Übergeben Sie den Nachrichtenkontext an den nächsten Arbeitsstatus.

### <a name="preview-links-link-unfurling"></a>Vorschaulinks (Verbreitung von Links)

Messaging-Erweiterungen sollten eine Vorschau erkannter Links im Feld Teams Verfassen anzeigen. Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden (absolute URLs oder Platzhalter). Ist z. `yourapp.onmicrosoft.com` B. gültig, aber `*.onmicrosoft.com` nicht gültig. Domänen auf oberster Ebene sind ebenfalls nicht zulässig (z. B. `*.com` oder `*.org` ).

### <a name="search-commands"></a>Suchbefehle

* Suchbasierte Messaging-Erweiterungen müssen Text bereitstellen, mit dem Benutzer effektiv suchen können.
* @mention ausführbare Dateien müssen klar, leicht verständlich und lesbar sein.

## <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul muss ein Symbol und den Kurznamen der App enthalten, der es zugeordnet ist.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Teams Aufgabenmodul.](~/task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="meeting-extensions"></a>Besprechungserweiterungen

Wenn Ihre App eine Besprechungserweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Designrichtlinien für Teams Besprechungserweiterung.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)

### <a name="pre--and-post-meeting-experience"></a>Pre- und Post-Meeting-Erfahrung

* Bildschirme vor und nach besprechungen müssen den allgemeinen Richtlinien für das Registerkartendesign entsprechen. Weitere Informationen finden Sie in den [Teams Entwurfsrichtlinien.](~/tabs/design/tabs.md)
* Registerkarten dürfen keinen horizontalen Bildlauf aufweisen.
* Registerkarten sollten ein organisiertes Layout aufweisen, wenn mehrere Elemente angezeigt werden. Beispielsweise mehr als 10 Umfragen oder Umfragen. Sehen Sie sich ein [Beispiellayout an.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting)
* Ihre App muss Benutzer benachrichtigen, wenn die Ergebnisse einer Umfrage oder Umfrage exportiert werden, indem sie besagt: "Ergebnisse erfolgreich heruntergeladen".

### <a name="in-meeting-experience"></a>Besprechungserfahrung

* Apps dürfen nur während Besprechungen ein dunkles Design verwenden. Weitere Informationen finden Sie in den [Teams Entwurfsrichtlinien.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming)
* Eine QuickInfo sollte den App-Namen anzeigen, wenn Sie während Besprechungen auf das App-Symbol zeigen.
* Messaging-Erweiterungen müssen während Besprechungen genauso funktionieren wie außerhalb von Besprechungen.

### <a name="in-meeting-tabs"></a>Registerkarten in Besprechungen

* Muss reaktionsfähig sein. Achten Sie darauf, abstands- und komponentengrößen beizubehalten.
* Muss über eine Zurück-Schaltfläche verfügen, wenn mehr als eine Navigationsebene vorhanden ist.
* Darf nicht mehr als eine Schaltfläche zum Schließen oder Schließen enthalten. Dies kann Benutzer verwirren, da bereits eine integrierte Kopfzeilenschaltfläche vorhanden ist, um die Registerkarte zu schließen.
* Es darf kein horizontaler Bildlauf erfolgen.

### <a name="in-meeting-dialogs"></a>Dialogfelder in Besprechungen

* Sollte sparsam und für Szenarien verwendet werden, die einfach und aufgabenorientiert sind.
* Inhalt muss in einer einzelnen Spalte angezeigt werden und darf nicht über mehrere Navigationsebenen verfügen.
* Aufgabenmodule dürfen nicht verwendet werden.
* Muss am Mittelpunkt der Besprechungsphase ausgerichtet sein.
* Sollte geschlossen werden, sobald ein Benutzer eine Schaltfläche auswählt oder eine Aktion ausführt.

## <a name="notifications"></a>Benachrichtigungen

Wenn Ihre App die [von Microsoft Graph bereitgestellten Aktivitätsfeed-APIs](/graph/teams-send-activityfeednotifications)verwendet, stellen Sie sicher, dass sie die folgenden Richtlinien einhält.

### <a name="general"></a>Allgemein

* Alle in Ihren App-Konfigurationen angegebenen Benachrichtigungsauslöser sollten eine Benachrichtigung in der App erhalten.
* Benachrichtigungen müssen gemäß den unterstützten Sprachen lokalisiert werden, die für Ihre App konfiguriert sind.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

### <a name="avatars"></a>Avatare

* Der Benachrichtigungs-Avatar sollte mit dem Farbsymbol Ihrer App übereinstimmen.
* Von einem Benutzer ausgelöste Benachrichtigungen sollten den Avatar des Benutzers enthalten.

### <a name="spamming"></a>Spamming

* Apps dürfen nicht mehr als 10 Benachrichtigungen pro Minute an einen Benutzer senden.
* Bots und der Aktivitätsfeed sollten keine doppelten Benachrichtigungen auslösen.
* Benachrichtigungen müssen benutzern einen Gewissenswert bieten und dürfen nicht für triviale oder irrelevante Ereignisse verwendet werden.

### <a name="navigation-and-layout"></a>Navigation und Layout

* Benachrichtigungen müssen dem Layout und der Benutzeroberfläche des Teams Aktivitätsfeeds entsprechen.
* Wenn Sie eine Benachrichtigung auswählen, muss der Benutzer innerhalb Teams zu relevanten Inhalten geleitet und nicht aus der Teams Erfahrung herausgenommen werden.

## <a name="advertising"></a>Werbung

Apps dürfen keine Werbung anzeigen, einschließlich dynamischer Anzeigen, Banneranzeigen und Anzeigen in Nachrichten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines Partner Center-Kontos](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
