---
title: Richtlinien zur Validierung von Microsoft Teams-Speichern
description: Beschreibt die Richtlinien, die jede an den Teams Store (AppSource) übermittelte App befolgen muss.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 19a14553d7fcf5ba4af316f9259c641751778932
ms.sourcegitcommit: 1431dfe08d5a19a63dbf1542a2e6c661e4dd7fc1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2021
ms.locfileid: "60949103"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Richtlinien zur Validierung von Microsoft Teams-Speichern

Das Befolgen dieser Richtlinien erhöht die Wahrscheinlichkeit, dass Ihre App den Einreichungsprozess für den Microsoft Teams Store besteht. Diese Teams-spezifischen Richtlinien ergänzen die [Microsoft-Zertifizierungsrichtlinien für kommerzielle Marktplätze](/legal/marketplace/certification-policies) und werden regelmäßig aktualisiert, um neue Funktionen, Benutzerfeedback und Änderungen an Geschäftsregeln zu berücksichtigen.

> [!NOTE]
> Einige Richtlinien gelten möglicherweise nicht für Ihre App. Wenn Ihre App beispielsweise keinen Bot enthält, können Sie botbezogene Richtlinien ignorieren.

## <a name="value-proposition"></a>Wertbeitrag 

### <a name="app-name"></a>App-Name

Der Name einer App spielt eine wichtige Rolle bei der Art und Weise, wie Benutzer sie im Store entdecken können. Beachten Sie Folgendes zu App-Namen:

* Der Name muss für Ihre Benutzer relevante Begriffe enthalten.
* Namen der Kernfunktionen von Teams &#8212;wie **Chat,** **Kontakte,** **Kalender,** **Anrufe,** **Dateien,** **Aktivitäten,** **Teams,** **Apps** und **Hilfe**&#8212;sollten nicht im App-Namen enthalten sein.
* Gebräuchlichen Nomen muss der Name des Entwicklers vorangestellt oder angehängt werden (z. B. **Contoso Tasks** statt **Tasks)**.
* Darf keine **Teams** oder andere Microsoft-Produktnamen verwenden, die fälschlicherweise auf Co-Branding oder Co-Selling hinweisen könnten. (Weitere Informationen zum Verweisen auf Microsoft-Software, -Produkte und -Dienste finden Sie in den [Microsoft-Marken- und Markenrichtlinien](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)).
* Wenn Ihre App Teil einer offiziellen Partnerschaft mit Microsoft ist, muss der Name Ihrer App an erster Stelle stehen (z. B. **Contoso Connector für Microsoft Teams**).
* Der Name einer im Store aufgeführten App oder eines anderen Angebots auf dem kommerziellen Marktplatz darf nicht kopiert werden.
* Darf keine profanen oder abfälligen Begriffe enthalten. Der Name darf auch keine rassen- oder kulturell unsensible Sprache enthalten.
* Er muss einzigartig sein. Sie können nicht mehrere Apps für verschiedene Regionen mit demselben Namen und Zweck verzeichnen.

### <a name="suitable-for-workplace-consumption"></a>Geeignet für den Gebrauch am Arbeitsplatz

App-Inhalte müssen für den allgemeinen Gebrauch am Arbeitsplatz geeignet sein und alle Einschränkungen einhalten, die in den Zertifizierungsrichtlinien für kommerzielle Marktplatz-Sites aufgeführt sind. Inhalte mit Bezug zu Religion, Politik, Glücksspielen und längerer Unterhaltung sind verboten. Weitere Informationen finden Sie in den [Zertifizierungsrichtlinien für kommerzielle Marktplätze](/legal/marketplace/certification-policies#10010-inappropriate-content).

Ihre App muss die Zusammenarbeit in Gruppen erleichtern, die Produktivität einer Person verbessern oder beides. Apps, die für Teambindung und soziale Kontakte gedacht sind, müssen kollaborativ sein und für mehrere Teilnehmer konzipiert sein. Diese Arten von Apps sollten auch keinen erheblichen Zeitaufwand erfordern oder die Produktivität spürbar beeinträchtigen.

### <a name="similar-platforms-and-services"></a>Ähnliche Plattformen und Dienste

Apps müssen sich auf die Teams-Erfahrung konzentrieren und dürfen keine Namen, Symbole oder Bilder anderer ähnlicher chatbasierter Plattformen oder Dienste für die Zusammenarbeit enthalten, es sei denn, Ihre App bietet eine bestimmte Interoperabilität.

### <a name="feature-names"></a>Funktionsnamen

App-Funktionsnamen in Schaltflächen und anderem UI-Text dürfen nicht mit der Terminologie in Konflikt stehen, die für Teams und andere Microsoft-Produkte reserviert ist. Zum Beispiel, **Besprechung starten,** **Anruf tätigen** oder **Chat starten**. Fügen Sie Ihren App-Namen ein, wenn Sie dies nicht vollständig vermeiden können, z. B. **Contoso-Besprechung starten** anstelle von **Besprechung starten**.

## <a name="security"></a>Sicherheit

### <a name="microsoft-365-app-compliance-program"></a>Microsoft 365-App-Compliance Program

Das [Microsoft 365 App Compliance-Programm](/microsoft-365-app-certification/overview) soll Organisationen dabei helfen, Risiken zu bewerten und zu verwalten, indem Sicherheits- und Compliance-Informationen zu Ihrer App ausgewertet werden. Wenn Sie eine App im Teams Store veröffentlichen, müssen Sie die folgenden Stufen des Programms abschließen:

* [Publisher Überprüfung:](/azure/active-directory/develop/publisher-verification-overview)Hilft Administratoren und Endbenutzern, die Authentizität von App-Entwicklern zu verstehen, die sich in die Microsoft Identity Platform integrieren. Nach Abschluss wird im Zustimmungsdialogfeld von Azure Active Directory (Azure AD) und auf anderen Bildschirmen ein blaues Badge „bestätigt“ angezeigt. Weitere Informationen finden Sie unter [Häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [wie Sie Ihre App als vom Publisher bestätigt markieren](/azure/active-directory/develop/mark-app-as-publisher-verified)und [Fehlerbehebung bei der Publisher-Verifizierung](/azure/active-directory/develop/troubleshoot-publisher-verification).
* [Publisher-Bestätigung:](/microsoft-365-app-certification/docs/attestation)Ein Prozess, bei dem Sie allgemeine Informationen zur Datenverarbeitung sowie Sicherheits- und Compliance-Informationen weitergeben, um potenziellen Kunden zu helfen, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine App einreichen, die zuvor nicht aufgeführt wurde, können Sie die Publisher-Bestätigung nicht offiziell abschließen, bis sich Ihre App im Teams Store befindet. Wenn Sie eine aufgeführte App aktualisieren, führen Sie die Publisher-Bestätigung durch, bevor Sie die neueste Version der App einreichen.

### <a name="bots"></a>Bots

Bei Apps, die den Microsoft Azure Bot Service verwenden (z. B. Bots und Messaging-Erweiterungen), müssen Sie alle in den Microsoft [Online Services-Bedingungen](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) definierten Anforderungen erfüllen.

Bots müssen immer um Erlaubnis zum Hochladen einer Datei bitten und nach dem Datei-Upload eine Bestätigungsnachricht anzeigen.

### <a name="external-domains"></a>Externe Domänen

In den meisten Fällen dürfen Sie keine Domänen außerhalb der Kontrolle Ihrer Organisation (einschließlich Wildcards) und Tunnelingdienste in die Domänenkonfigurationen Ihrer App einschließen. Zu den folgenden Ausnahmen gehören:

* Wenn Ihre App die OAuthCard des Azure Bot Service verwendet, müssen Sie `token.botframework.com` als gültige Domäne angeben oder die Schaltfläche **Anmelden** funktioniert nicht.
* Wenn Ihre App auf SharePoint basiert, können Sie die zugehörige SharePoint-Stammsite mithilfe der Kontexteigenschaft `{teamSiteDomain}` als gültige Domäne einschließen.

### <a name="authentication"></a>Authentifizierung

Informationen zum Implementieren der App-Authentifizierung finden Sie unter [Authentifizierung in Teams](~/concepts/authentication/authentication.md).

#### <a name="authenticating-with-external-services"></a>Authentifizieren mit externen Diensten

Beachten Sie Folgendes, wenn Ihre App Benutzer mit einem externen Dienst authentifiziert.

* **Anmelde-, Abmelde- und Registrierungserfahrungen**:
  * Apps, die von externen Konten oder Diensten abhängen, müssen klare und einfache Anmelde-, Abmelde- und Registrierungserfahrungen bieten.
  * Wenn sich ein Benutzer abmeldet, muss er sich nur von der App abmelden, er bleibt jedoch bei Teams angemeldet.
* **Erfahrungen beim Teilen von Inhalten**: Apps, die eine Authentifizierung bei einem externen Dienst erfordern, um Inhalte in Teams-Kanälen freizugeben, müssen in der Hilfedokumentation (oder ähnlichen Ressourcen) klar angeben, wie Inhalte getrennt oder freigegeben werden, wenn diese Funktion vom externen Dienst unterstützt wird. Dies bedeutet nicht, dass die Fähigkeit zur Aufhebung der Freigabe von Inhalten in Ihrer Teams-App vorhanden sein muss.

#### <a name="government-community-cloud-listings"></a>Community Cloud-Einträge für Behörden

Um Ihre App an Benutzer der Government Community Cloud (GCC) zu verteilen und gleichzeitig doppelte Einträge im Teams Store zu vermeiden, muss der Authentifizierungsprozess Benutzer identifizieren und an eine GCC-spezifische oder erwartete URL weiterleiten.

### <a name="sensitive-content"></a>Vertraulicher Inhalt

Ihre App darf keine sensiblen Daten wie Kreditkarten- oder Zahlungsinstrumentdaten veröffentlichen. Die App darf auch keine Informationen zum Gesundheitszustand, zur Kontaktverfolgung oder anderen persönlich identifizierbaren Informationen (PII) für ein Publikum anzeigen, das diese Inhalte nicht anzeigen soll.

Warnen Sie Benutzer, bevor Ihre App Dateien oder ausführbare Dateien (.exe) auf den Computer oder die Umgebung des Benutzers herunterlädt.

### <a name="financial-information"></a>Finanzinformationen

Apps dürfen Benutzer nicht auffordern, Zahlungen innerhalb der Teams-Benutzeroberfläche zu tätigen. Details zu Finanzinstrumenten dürfen nicht über eine Bot-Schnittstelle an Benutzer übermittelt werden.

Sie dürfen nur dann auf sichere, externe Zahlungsdienste verlinken, wenn Sie die entsprechende Offenlegung in Ihren Nutzungsbedingungen, Datenschutzrichtlinien oder einer Profilseite oder Website gemacht haben, bevor der Benutzer der Nutzung der App zugestimmt hat.

Apps, die auf der iOS- oder Android-Version von Teams ausgeführt werden, müssen den folgenden Richtlinien entsprechen:

* Apps dürfen keine In-App-Käufe, Testangebote oder Benutzeroberflächen enthalten, die darauf abzielen, auf kostenpflichtige Versionen oder Links zu Online-Shops zu verkaufen, in denen Benutzer andere Inhalte, Apps oder Add-Ins kaufen oder erwerben können.
* Wenn für Ihre App ein Konto erforderlich ist, müssen sich Benutzer kostenlos für ein Konto anmelden können. Die Verwendung des Begriffs **kostenlos** oder **kostenloser Account** ist untersagt.
* Sie können festlegen, ob ein Konto auf unbestimmte Zeit oder für eine begrenzte Zeit aktiv ist, aber wenn das Konto abläuft, werden möglicherweise keine Benutzeroberfläche, kein Text oder keine Links angezeigt, die auf eine Zahlungspflicht hinweisen.
* Die Seiten mit den Datenschutzrichtlinien und Nutzungsbedingungen Ihrer App müssen frei von handelsbezogenen Benutzeroberflächen oder Links sein.

> [!NOTE]
> Teams Store-Einträge können App-Abonnementpläne oder -lizenzen zum Kauf enthalten. Weitere Informationen finden Sie unter [Einschließen eines SaaS-Angebots mit Ihrer App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md).

## <a name="general-functionality-and-performance"></a>Allgemeine Funktionalität und Leistung

### <a name="launching-external-functionality"></a>Externe Funktionen starten

Apps dürfen Benutzer für Kernbenutzerszenarien nicht aus Teams herausnehmen. App-Inhalte und -Interaktionen können innerhalb von Teams-Funktionen wie Bots, Karten und Aufgabenmodulen auftreten.

Sie sollten Benutzer irgendwo in Teams verlinken und nicht mit einer externen Website oder App. Für Szenarien, die externe Funktionen erfordern, muss Ihre App über eine explizite Benutzerberechtigung verfügen, um diese Funktionen zu starten.

### <a name="compatibility"></a>Kompatibilität

Apps müssen auf den folgenden Betriebssystemen und Browsern voll funktionsfähig sein:

* Microsoft Windows 7 und höher
* macOS 10.10 und höher
* Microsoft Edge 12 und höher
* Mozilla Firefox 47.0 und höher
* Chrome 51.0 und höher
* iOS 9.0 und höher
* Android 4.4 oder höher

### <a name="response-time"></a>Antwortzeit

Teams-Apps müssen innerhalb eines angemessenen Zeitrahmens reagieren, der je nach Funktion unterschiedlich ist.

* Tabs müssen innerhalb von drei Sekunden reagieren oder eine Lademeldung oder Warnung anzeigen.
* Bots müssen innerhalb von zwei Sekunden auf Benutzerbefehle reagieren oder eine Tippanzeige anzeigen.
* Messaging-Erweiterungen müssen innerhalb von fünf Sekunden auf Benutzerbefehle reagieren.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

## <a name="app-package-and-store-listing"></a>App-Paket und Store-Eintrag

App-Pakete müssen korrekt formatiert sein und alle erforderlichen Informationen und Komponenten enthalten.

### <a name="app-manifest"></a>App-Manifest

Das Teams-App-Manifest definiert die Konfigurationen Ihrer App.

* Ihr Manifest muss dem neuesten Manifestschema entsprechen. Weitere Informationen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md)
* Wenn Ihre App einen Bot oder eine Messaging-Erweiterung enthält, muss Ihr Manifest mit Bot Framework-Metadaten übereinstimmen, einschließlich Bot-Name, Logo, Link zur Datenschutzrichtlinie und Link zu den Servicebedingungen.
* Wenn Ihre App Azure Active Directory (Azure AD) für die Authentifizierung verwendet, fügen Sie die Azure AD-Anwendungs-(Client-)ID in das Manifest ein. Weitere Informationen finden Sie in der [Manifest-Referenz](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="app-icons"></a>App-Symbole

Symbole sind eines der Hauptelemente, die Benutzer beim Durchsuchen des Teams-Speichers sehen. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig die folgenden Anforderungen erfüllen:

* Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: Ein Farbsymbol und ein Umrisssymbol.
* Die Farbversion Ihres Symbols wird in den meisten Teams-Szenarien angezeigt und muss 192x192 Pixel groß sein. Ihr Symbol (96x96 Pixel) kann eine beliebige Farbe oder Farben haben, es muss jedoch auf einem durchgehenden oder vollständig transparenten quadratischen Hintergrund stehen.
* Die Gliederungsversion Ihres Symbols wird angezeigt, wenn Ihre App verwendet und in der App-Leiste auf der linken Seite von Teams „herausgezogen“ wird und wenn ein Benutzer die Messaging-Erweiterung Ihrer App anheftet. Es muss 32x32 Pixel groß sein und kann weiß mit transparentem Hintergrund oder transparent mit weißem Hintergrund sein (andere Farben sind nicht erlaubt). Das Symbol sollte keine zusätzliche Auffüllung um das Symbol herum aufweisen.
* In Ihrem App-Paket müssen Symbole mit korrekter Größe und Format enthalten sein. Die Symbole müssen auch mit den übermittelten Metadaten des Store-Eintrags übereinstimmen.

Weitere Informationen, bewährte Methoden und Beispiele finden Sie in den [Richtlinien für Teams-App-Symbole](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="app-descriptions"></a>App-Beschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben. Die Beschreibungen in Ihren App-Konfigurationen und im Partner Center müssen identisch sein.

Beschreibungen sollten nicht direkt oder durch Andeutungen eine andere Marke (im Besitz von Microsoft oder nicht) herabwürdigen. Stellen Sie sicher, dass Ihre Beschreibung keine Behauptungen enthält, die nicht belegt werden können (z. B. "Garantierte Effizienzsteigerung von 200 %").

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Beschreibung ist eine prägnante Zusammenfassung Ihrer App, die ihr Wertversprechen hervorhebt und sich an Ihre Zielgruppe richtet.

**Dos:**

* Halten Sie die kurze Beschreibung in einem Satz.
* Die wichtigsten Informationen kommen an erster Stelle.
* Fügen Sie Schlüsselwörter hinzu, nach denen Kunden wahrscheinlich suchen.

**Don’ts:**

* Wiederholen Sie Ihren App-Namen.
* Verwenden Sie das Wort **App** in der Kurzbeschreibung.

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine ansprechende Erzählung bieten, die das Wertversprechen Ihrer App, die primäre Zielgruppe und die Zielbranche hervorhebt. Obwohl diese Beschreibung bis zu 4 000 Zeichen lang sein kann, werden die meisten Benutzer nur zwischen 300 und 500 Wörter lesen.

**Dos:**

* Verwenden Sie Markdown, um Ihre Beschreibung zu formatieren.
* Verwenden Sie aktive Stimme und sprechen Sie direkt mit Benutzern. Zum Beispiel *können Sie ...*.
* Listen Sie Features mit Aufzählungspunkten auf, damit die Beschreibung einfacher durchsucht werden kann.
* Beschreiben Sie Einschränkungen, Bedingungen oder Ausnahmen für die in der Auflistung und den zugehörigen Materialien beschriebenen Funktionsweisen, Funktionen und Leistungen klar und deutlich, bevor der Benutzer Ihre App installiert. Die von Ihrer App unterstützten Teams-Funktionen müssen sich auf die in Ihrem Eintrag beschriebenen Kernfunktionen beziehen.
* Stellen Sie sicher, dass die App-Beschreibung mit der in der Teams-App verfügbaren Funktionalität übereinstimmt. Jeder Verweis auf Workflows außerhalb der Teams-App muss begrenzt und von der Funktionsweise der Teams-App eindeutig hervorgehoben werden.
* Fügen Sie einen Hilfe- oder Support-Link hinzu.
* Verweisen Sie auf **Microsoft 365** anstelle von **Office 365**.
* Wenn Sie auf **Teams** verweisen müssen, schreiben Sie den ersten Verweis als **Microsoft Teams**. Nachfolgende Verweise können auf **Teams** gekürzt werden.
* Verwenden Sie die folgende Sprache, wenn Sie beschreiben, wie die App mit Teams (oder Microsoft 365) funktioniert:
  * "... funktioniert mit Microsoft Teams."
  * "... arbeitet mit Microsoft Teams."
  * "... in Microsoft Teams."
  * "... für Microsoft Teams."
  * "... in Microsoft Teams integriert."
  * "... erstellt für... "
  * "... entwickelt für... "
  * "... designed für..."


**Don’ts:**

* Überschreitet 500 Wörter.
* Kürzen Sie **Microsoft** als **MS** oder **MSFT**.
* Geben Sie an, dass es sich bei der App um ein Angebot von Microsoft handelt, einschließlich der Verwendung von Microsoft-Slogans oder Leitsätzen.
* Verwenden Sie urheberrechtlich geschützte Markennamen, die Ihnen nicht gehören.
 * Verwenden Sie die folgende Sprache, es sei denn, Sie sind ein zertifizierter Microsoft-Partner:
  * "... zertifiziert für ..."
  * "... unterstützt von ..."
* Tippfehler, Grammatikfehler und unnötige Groß-/Kleinschreibung einschließen, zum Beispiel **benutzer** anstelle von **Benutzer**.
* Links zu AppSource einschließen.
* Nicht überprüfte Ansprüche stellen (beispielsweise "bestbewertet"), es sei denn, die Quelle des Anspruchs steht dem gegenüber.
* Vergleichen Sie Ihr Angebot mit anderen Marketplace-Angeboten.



### <a name="screenshots"></a>Screenshots

Screenshots bieten eine markante visuelle Vorschau Ihrer App, um den Namen, das Symbol und die Beschreibungen Ihrer App zu ergänzen. Beachten Sie Folgendes zu Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag erstellen.
* Unterstützte Dateitypen sind PNG, JPEG und GIF.
* Die Dimensionen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1 024 KB.

**Dos:**

* Konzentrieren Sie sich auf die Funktionen Ihrer App (z. B. wie Personen mit Ihrem Bot kommunizieren können).
* Fügen Sie Inhalte ein, die Ihre App genau darstellen.
* Verwenden Sie Text mit Bedacht.
* Rahmen Sie Screenshots mit einer Farbe, die Ihre Marke widerspiegelt, und schließen Sie Marketinginhalte ein, ähnlich wie beim Beispiel für die [Freshdesk-Liste](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) (Anforderungen an die Dimensionen gelten für das gesamte Bild und nicht nur für den Screenshot).

**Don’ts:**

* Zeigen Sie bestimmte Geräte wie Telefone oder Laptops an.
* Zeigen Sie Chrome oder eine Benutzeroberfläche an, die nicht in Ihrer App enthalten ist.
* Erfassen Sie beliebige Teams oder Browser-UI in Ihren Screenshots.
* Fügen Sie Mockups hinzu, die die tatsächliche Benutzeroberfläche Ihrer App ungenau widerspiegeln, z. B. wenn Ihre App außerhalb von Teams verwendet wird.

> [!TIP]
> Ein Video kann der effektivste Weg sein, um zu kommunizieren, warum die Leute Ihre App verwenden sollten. Ein Video ist auch das erste, was Nutzer in Ihrem Eintrag sehen (standardmäßig wird ein Video vor Screenshots angezeigt). Weitere Informationen finden Sie unter [Video für Ihren Store-Eintrag erstellen](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

### <a name="privacy-policy"></a>Datenschutzrichtlinie

Die Datenschutzrichtlinie kann für Ihre Teams-App oder eine allgemeine Richtlinie für alle Ihre Dienste spezifisch sein.

* Wenn Sie eine generische Datenschutzrichtlinienvorlage verwenden, müssen Sie auf **Dienste,** **Anwendungen** und **Plattformen** verweisen, um Ihre Teams-App und Ihren Dienst oder Ihre Website einzuschließen.
* Muss beinhalten, wie Sie mit der Speicherung, Aufbewahrung und Löschung von Benutzerdaten umgehen. Sie müssen auch die Sicherheitskontrollen beschreiben, die Sie für den Datenschutz verwenden.
* Muss Ihre Kontaktdaten enthalten.
* Sollte keine URLs enthalten, die beschädigt sind oder für Beta- oder Staging-Zwecke verwendet werden.
* Darf keine Links zu AppSource enthalten.

### <a name="terms-of-use"></a>Nutzungsbedingungen

Ihre Nutzungsbedingungen sollten spezifisch und auf Ihr Angebot anwendbar sein.

### <a name="support-links"></a>Supportlinks

Die Support-URLs Ihrer App sollten keine Authentifizierung erfordern. Benutzer sollten sich beispielsweise nicht anmelden müssen, um Sie zu kontaktieren.

### <a name="localization"></a>Lokalisierung

Wenn Ihre App Lokalisierung unterstützt, muss Ihr App-Paket eine Datei mit Sprachübersetzungen enthalten, die basierend auf der Spracheinstellung von Teams angezeigt werden. Die Datei muss dem Lokalisierungsschema von Teams entsprechen. Weitere Informationen finden Sie im [Teams-Lokalisierungsschema](~/concepts/build-and-test/apps-localization.md).

## <a name="tabs"></a>Registerkarten

Wenn Ihre App eine Registerkarte enthält, stellen Sie sicher, dass diese diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Designrichtlinien für Teams Registerkarten](~/tabs/design/tabs.md).

### <a name="setup"></a>Setup

* Die Registerkarteneinrichtung darf einen neuen Benutzer nicht in eine Sackgasse führen. Geben Sie eine Nachricht zum Abschließen der Aktion oder des Workflows an.
* Die Authentifizierung sollte während der Registerkarteneinrichtung und nicht danach erfolgen.

### <a name="views"></a>Ansichten

* Der Bereich des Anmeldebildschirms darf keine großen Logos verwenden oder eine ganze Webseite anzeigen.
* Der Inhalt kann vereinfacht werden, indem er auf mehrere Registerkarten aufgeteilt wird.
* Registerkarten dürfen keinen doppelten Header aufweisen. Entfernen Sie das Logo aus dem iframe, da das Registerkartenframework bereits das App-Symbol und den Namen anzeigt.

### <a name="navigation"></a>Navigation

* Registerkarten dürfen nicht mehr als drei Navigationsebenen aufweisen.
* Registerkarten dürfen keine Navigation bereitstellen, die in Konflikt mit der primären Teams-Navigation steht.
* Die Sekundär- und Tertiärseiten eines Tabs müssen in einer Ebene 2- und Ebene 3 Ansicht im Hauptregisterkartenbereich geöffnet werden, der über Breadcrumb Navigation oder die linke Navigationsleiste geleitet wird. Sie können auch die folgenden Komponenten einschließen, um die Registerkartennavigation zu unterstützen:
    * Zurück-Schaltflächen
    * Seitenüberschriften
    * Hamburger-Menüs
* Die Registerkarte sollte kein horizontales Scrollen haben.
* Deep-Links in Registerkarten dürfen nicht mit einer externen Webseite, sondern an einer beliebigen Stelle in Teams verknüpft werden. Beispielsweise Aufgabenmodule oder andere Registerkarten.
* Registerkarten sollten es Benutzern nicht ermöglichen, außerhalb von Teams für die Kernanwendungserfahrung zu navigieren.

### <a name="usability"></a>Benutzerfreundlichkeit

* Registerkarten müssen einen Mehrwert bieten, der über das reine Hosten einer vorhandenen Website hinausgeht.
* Benutzer müssen in der Lage sein, ihre letzte Aktion auf der Registerkarte rückgängig zu machen.
* Registerkarten in einem persönlichen Kontext können Inhalte von freigegebenen Instanzen der App aggregieren.
* Registerkarten müssen für Teams-Designs reaktionsfähig sein. Wenn ein Benutzer das Design ändert, muss das Design der App die Auswahl widerspiegeln.
* Registerkarten müssen Komponenten im Stil von Teams verwenden, z-B. Teams-Schriftarten, Typrampen, Farbpaletten, Rastersystem, Bewegung, Tonfall und so weiter, wann immer möglich.
* Wenn Ihre App-Funktionalität Änderungen an den Einstellungen erfordert, fügen Sie eine **Einstellungen** Registerkarte hinzu.
* Registerkarten müssen nach Möglichkeit dem Interaktionsdesign von Teams folgen, z. B. seiteninterne Navigation, Position und Verwendung von Dialogfeldern, Informationshierarchien usw.
* Registerkarteninhalte im iframe dürfen keine Funktionen enthalten, die die Kernfunktionen von Teams nachahmen. Zum Beispiel Bots, Messaging-Erweiterungen, Anrufe, Besprechungen usw.

> [!TIP]
>
> * Fügen Sie einen persönlichen Bot neben einer persönlichen Registerkarte ein.
> * Erlauben Sie Benutzern, Inhalte von ihrer persönlichen Registerkarte zu teilen.

## <a name="bots"></a>Bots

Wenn Ihre App einen Bot enthält, stellen Sie sicher, dass er diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Teams-Bot-Entwurfsrichtlinien](~/bots/design/bots.md).

### <a name="bot-commands"></a>Bot-Befehle

Das Analysieren von Benutzereingaben und das Vorhersagen der Benutzerabsicht ist schwierig. Botbefehle stellen Benutzern eine Reihe von Wörtern oder Ausdrücken bereit, die Ihr Bot versteht, damit Sie (und Ihr Bot) diese nicht erraten müssen.

* Es wird dringend empfohlen, unterstützte Bot-Befehle in Ihren App-Konfigurationen aufzulisten. Diese Befehle werden im Feld zum Verfassen angezeigt, wenn ein Benutzer versucht, Ihrem Bot eine Nachricht zu senden.
* Alle Befehle, die Ihr Bot unterstützt, müssen ordnungsgemäß funktionieren, einschließlich des Befehls **"Hi",** **"Hallo"** und **"Hilfe".**

> [!TIP]
> Fügen Sie für persönliche Bots eine Registerkarte **Hilfe** hinzu, die genauer beschreibt, was Ihr Bot tun kann.

### <a name="bot-welcome-messages"></a>Bot-Begrüßungsnachrichten

* Bots sollten beim ersten Durchlauf fast immer eine Begrüßungsnachricht senden. Für eine optimale Erfahrung sollte die Nachricht das Wertversprechen Ihres Bots, die Konfiguration des Bots und eine kurze Beschreibung aller unterstützten Botbefehle enthalten. Sie können die Nachricht mit einer adaptiven Karte mit Schaltflächen für eine bessere Benutzerfreundlichkeit anzeigen. Weitere Informationen finden Sie unter [Auslösen einer Bot-Begrüßungsnachricht.](~/bots/how-to/conversations/send-proactive-messages.md)
* Bot-Begrüßungsnachrichten in Kanälen und Chats sind bei der ersten Ausführung optional, insbesondere wenn der Bot für den persönlichen Gebrauch verfügbar ist und ähnliche Aktionen ausführt. Wenn Ihr Bot Begrüßungsnachrichten sendet, darf er diese nicht einzeln an Benutzer senden (dies gilt als [Spamming).](#bot-message-spamming) Die Nachricht sollte auch die Person erwähnen, die den Bot hinzugefügt hat.
* Nur-Benachrichtigungs-Bots müssen eine Begrüßungsnachricht senden, die vermittelt, dass sie nicht auf die Nachrichten der Benutzer antworten.

> [!TIP]
> In Begrüßungsnachrichten an einzelne Benutzer kann eine Karusselltour einen effektiven Überblick über Ihren Bot und alle anderen App-Funktionen geben. Es wird das Einschließen von Schaltflächen empfohlen, mit denen Benutzer Bot-Befehle ausprobieren können. Erstellen Sie z. B. **eine Aufgabe**.

### <a name="bot-message-spamming"></a>Spam mit Bot-Nachrichten

Bots dürfen Benutzer nicht spammen, indem sie mehrere Nachrichten kurz hintereinander senden.

* **Bot-Nachrichten in Kanälen und Chats**: Spamen Sie Benutzer nicht, indem Sie separate Beiträge erstellen. Erstellen Sie einen einzelnen Beitrag mit Antworten im selben Thread.
* **Bot-Nachrichten in persönlichen Apps**: Senden Sie nicht mehrere Nachrichten kurz hintereinander. Senden Sie eine Nachricht mit vollständigen Informationen. Vermeiden Sie Gespräche mit mehreren Wendungen, um einen einzigen Workflow abzuschließen. Ziehen Sie stattdessen die Verwendung eines Formulars (oder Aufgabenmoduls) in Betracht, um alle Eingaben eines Benutzers gleichzeitig zu sammeln.
* **Begrüßungsnachrichten:** Das Wiederholen derselben Begrüßungsnachricht in regelmäßigen Abständen ist nicht erlaubt und wird als Spam angesehen. Wenn beispielsweise ein neues Mitglied zu einem Team hinzugefügt wird, sollten Sie die anderen Mitglieder nicht mit einer Begrüßungsnachricht spammen. Schreiben Sie dem neuen Mitglied stattdessen persönlich.

### <a name="bot-notifications"></a>Bot-Benachrichtigungen

Bot-Benachrichtigungen müssen Inhalte enthalten, die für den Bereich relevant sind, den Sie für den Bot definieren (Team, Chat oder persönlich).

### <a name="bots-and-adaptive-cards"></a>Bots und adaptive Karten

Adaptive Karten sind eine dringend empfohlene Möglichkeit, Bot-Nachrichten anzuzeigen. Ihre Karten müssen einfach sein und nur 1-3 Aktionen enthalten. Wenn Sie mehr Inhalte anzeigen müssen, ziehen Sie die Verwendung eines Aufgabenmoduls oder einer Registerkarte in Betracht.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Entwerfen Adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="messaging-extensions"></a>Messaging-Erweiterungen

Wenn Ihre App eine Messaging-Erweiterung enthält, stellen Sie sicher, dass diese diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Teams-.Messaging-Erweiterungen.](~/messaging-extensions/design/messaging-extension-design.md)

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbasierte Messaging-Erweiterungen sollten Folgendes tun:

* Benutzern erlauben, Aktionen für eine Nachricht auszulösen, ohne Zwischenschritte wie das Anmelden auszuführen.
* Übergeben des Nachrichtenkontexts an den nächsten Arbeitsstatus.

### <a name="preview-links-link-unfurling"></a>Vorschau-Links (Link-Unfurling)

Messaging-Erweiterungen sollten eine Vorschau erkannter Links im Feld zum Verfassen von Teams anzeigen. Fügen Sie keine Domänen hinzu, die außerhalb Ihrer Kontrolle liegen (entweder absolute URLs oder Wildcards). Beispiel: `yourapp.onmicrosoft.com` ist gültig, aber `*.onmicrosoft.com` ist nicht gültig. Domänen auf oberster Ebene sind ebenfalls nicht zulässig (z. B. `*.com` oder `*.org` ).

### <a name="search-commands"></a>Suchbefehle

* Suchbasierte Messaging-Erweiterungen müssen Text bereitstellen, der Benutzern bei der effektiven Suche hilft.
* @mention ausführbare Dateien müssen klar, leicht verständlich und lesbar sein.

## <a name="task-modules"></a>Aufgabenmodule

Ein Aufgabenmodul muss ein Symbol und den Kurznamen der App enthalten, mit der es verknüpft ist.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Teams-Aufgabenmodul](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="meeting-extensions"></a>Besprechungserweiterungen

Wenn Ihre App eine Besprechungserweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Teams-Besprechungserweiterungen](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

### <a name="pre--and-post-meeting-experience"></a>Erfahrung vor und nach der Besprechung

* Bildschirme vor und nach der Besprechung müssen den allgemeinen Richtlinien für das Design von Registerkarten entsprechen. Weitere Informationen finden Sie in den [Teams-Entwurfsrichtlinien.](~/tabs/design/tabs.md)
* Registerkarten dürfen kein horizontales Scrollen haben.
* Registerkarten sollten ein organisiertes Layout haben, wenn mehrere Elemente angezeigt werden. Zum Beispiel mehr als 10 Abstimmungen oder Umfragen. Sehen Sie sich ein [Beispiellayout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting) an.
* Ihre App muss Benutzer benachrichtigen, wenn die Ergebnisse einer Abstimmung oder Umfrage mit dem Hinweis "Ergebnisse erfolgreich heruntergeladen" exportiert werden.

### <a name="in-meeting-experience"></a>Besprechungserfahrung

* Apps dürfen nur während Besprechungen ein dunkles Design verwenden. Weitere Informationen finden Sie in den [Teams-Entwurfsrichtlinien.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming)
* Ein Tooltip sollte den App-Namen anzeigen, wenn Sie während Besprechungen mit der Maus über das App-Symbol fahren.
* Messaging-Erweiterungen müssen während Besprechungen genauso funktionieren wie außerhalb von Besprechungen.

### <a name="in-meeting-tabs"></a>Registerkarten in Besprechungen

* Muss erreichbar sein. Achten Sie darauf, die Auffüllung und Komponentengrößen beizubehalten.
* Muss eine Zurück-Schaltfläche haben, wenn mehr als eine Navigationsebene vorhanden ist.
* Darf nicht mehr als eine Schaltfläche zum Verwerfen oder Schließen enthalten. Dies kann Benutzer verwirren, da es bereits eine integrierte Kopfzeilenschaltfläche zum Schließen der Registerkarte gibt.
* Darf kein horizontales Scrollen haben.

### <a name="in-meeting-dialogs"></a>Dialoge im Besprechungen

* Sollte sparsam und für leichte und aufgabenorientierte Szenarien eingesetzt werden.
* Der Inhalt muss in einer einzigen Spalte angezeigt werden und darf nicht über mehrere Navigationsebenen verfügen.
* Darf keine Aufgabenmodule verwenden.
* Muss mit der Mitte der Besprechungsbereich ausgerichtet sein.
* Sollte verworfen werden, sobald ein Benutzer eine Schaltfläche auswählt oder eine Aktion ausführt.

## <a name="notifications"></a>Benachrichtigungen

Wenn Ihre App die von [Microsoft Graph bereitgestellten Aktivitätsfeed-APIs](/graph/teams-send-activityfeednotifications) verwendet, stellen Sie sicher, dass sie die folgenden Richtlinien einhält.

### <a name="general"></a>Allgemein

* Alle in Ihren App-Konfigurationen angegebenen Benachrichtigungsauslöser sollten eine Benachrichtigung in der App erhalten.
* Benachrichtigungen müssen gemäß den unterstützten Sprachen lokalisiert werden, die für Ihre App konfiguriert sind.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

### <a name="avatars"></a>Avatare

* Der Benachrichtigungsavatar sollte dem Farbsymbol Ihrer App entsprechen.
* Von einem Benutzer ausgelöste Benachrichtigungen sollten den Avatar des Benutzers enthalten.

### <a name="spamming"></a>Spamming

* Apps dürfen nicht mehr als 10 Benachrichtigungen pro Minute an einen Benutzer senden.
* Bots und der Aktivitätsfeed sollten keine doppelten Benachrichtigungen auslösen.
* Benachrichtigungen müssen den Benutzern einen gewissen Wert bieten und dürfen nicht für triviale oder irrelevante Ereignisse verwendet werden.

### <a name="navigation-and-layout"></a>Navigation und Layout

* Benachrichtigungen müssen dem Layout und der Erfahrung des Teams-Aktivitätsfeeds entsprechen.
* Bei der Auswahl einer Benachrichtigung muss der Benutzer zu relevanten Inhalten innerhalb von Teams geleitet werden und darf nicht aus der Teams-Erfahrung entfernt werden.

## <a name="advertising"></a>Werbung

Apps dürfen keine Werbung anzeigen, einschließlich dynamischer Anzeigen, Banneranzeigen und Anzeigen in Nachrichten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Sie ein Partner Center-Konto](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)

## <a name="see-also"></a>Siehe auch

* [Verteilen Ihrer App](~/concepts/deploy-and-publish/apps-publish-overview.md)
* [Vorbereiten der Übermittlung an den Store](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Testen und Debuggen Ihrer App](~/concepts/build-and-test/debug.md)
* [Erstellen eines Partner Center-Entwicklerkontos](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
