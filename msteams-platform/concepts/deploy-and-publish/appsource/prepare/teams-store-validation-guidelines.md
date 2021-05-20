---
title: richtlinien für Microsoft Teams-Speichervalidierung
description: Beschreibt die Richtlinien, die jede App, die an den Teams Store (AppSource) gesendet wird, befolgen muss.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 4daa8b027d7525f0fb3223c2000eee301043398a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565137"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>richtlinien für Microsoft Teams-Speichervalidierung

Das Befolgen dieser Richtlinien erhöht die Wahrscheinlichkeit, dass Ihre App den Microsoft Teams Store-Übermittlungsprozess besteht. Diese Teams-spezifischen Richtlinien ergänzen die [Zertifizierungsrichtlinien](/legal/marketplace/certification-policies) für den kommerziellen Marktplatz von Microsoft und werden regelmäßig aktualisiert, um neue Funktionen, Benutzerfeedback und Änderungen an Geschäftsregeln widerzuspiegeln.

> [!NOTE]
> Einige Richtlinien gelten möglicherweise nicht für Ihre App. Wenn Ihre App beispielsweise keinen Bot enthält, können Sie botbezogene Richtlinien ignorieren.

## <a name="10-value-proposition"></a>1.0 Wertversprechen

### <a name="11-app-name"></a>1.1 App-Name

Der Name einer App spielt eine entscheidende Rolle, wenn Benutzer sie im Store entdecken. Beachten Sie folgendes über App-Namen:

* Der Name muss Begriffe enthalten, die für Ihre Benutzer relevant sind.
* Namen von Kernfunktionen Teams Features&#8212;wie **Chat**, **Kontakte**, **Kalender**, **Anrufe**, **Dateien**, **Aktivität** **, Teams**, **Apps** und **Hilfe**&#8212;sollten nicht in Ihren App-Namen aufgenommen werden.
* Gemeinsamen Substantiven muss der Name des Entwicklers vorangestellt oder mit dem Namen des Entwicklers (z. B. **Contoso-Aufgaben** anstelle von **Aufgaben )** vorangestellt werden.
* Es dürfen **keine Teams** oder andere Microsoft-Produktnamen verwendet werden, die fälschlicherweise auf Co-Branding oder Co-Selling hinweisen könnten. (Weitere Informationen zum Verweisen auf Microsoft-Software, -Produkte und -Dienste finden Sie in den [Microsoft-Richtlinien für Marken- und Markenmarken](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
* Wenn Ihre App Teil einer offiziellen Partnerschaft mit Microsoft ist, muss der Name Ihrer App an erster Stelle stehen (z. B. **Contoso Connector für Microsoft Teams**).
* Der Name einer App, die im Store oder einem anderen Angebot auf dem kommerziellen Marktplatz aufgeführt ist, darf nicht kopiert werden.
* Darf keine profanen oder abfälligen Begriffe enthalten. Der Name darf auch keine rassisch oder kulturell unsensible Sprache enthalten.
* Muss einzigartig sein. Beispielsweise können Sie nicht mehrere Apps für verschiedene Regionen mit demselben Namen und denselben Funktionen auflisten.

### <a name="12-suitable-for-workplace-consumption"></a>1.2 Geeignet für den Verbrauch am Arbeitsplatz

App-Inhalte müssen für den allgemeinen Verbrauch am Arbeitsplatz geeignet sein und alle Einschränkungen einhalten, die in den Zertifizierungsrichtlinien für den kommerziellen Markt aufgeführt sind. Inhalte im Zusammenhang mit Religion, Politik, Glücksspiel und längerer Unterhaltung sind verboten. Weitere Informationen finden Sie in den [Zertifizierungsrichtlinien für den kommerziellen Marktplatz](/legal/marketplace/certification-policies#10010-inappropriate-content).

Ihre App muss die Gruppenzusammenarbeit erleichtern, die Produktivität einer Person verbessern oder beides. Apps, die für Team-Bindung und Geselligkeit gedacht sind, müssen kollaborativ sein und für mehrere Teilnehmer entwickelt werden. Diese Arten von Apps sollten auch keine erheblichen Zeitinvestitionen erfordern oder die Produktivität spürbar beeinträchtigen.

### <a name="13-similar-platforms-and-services"></a>1.3 Ähnliche Plattformen und Dienste

Apps müssen sich auf die Teams-Erfahrung konzentrieren und dürfen nicht die Namen, Symbole oder Bilder anderer ähnlicher Chat-basierter Plattformen oder Dienste für die Zusammenarbeit enthalten, es sei denn, Ihre App bietet eine bestimmte Interoperabilität.

### <a name="14-feature-names"></a>1.4 Feature-Namen

App-Feature-Namen in Schaltflächen und anderen UI-Text dürfen nicht mit der Terminologie in Konflikt stehen, die für Teams und andere Microsoft-Produkte reserviert ist. Beispiel: **Meeting starten**, **Anruf tätigen**, oder **Chat starten**. Fügen Sie Ihren App-Namen ein, wenn Sie dies nicht vollständig vermeiden können, z. B. **Contoso-Besprechung** anstelle von **Start Meeting** starten .

## <a name="20-security"></a>2.0 Sicherheit

### <a name="21-microsoft-365-app-compliance-program"></a>2.1 Microsoft 365 App Compliance-Programm

Das [Microsoft 365 App Compliance-Programm](/microsoft-365-app-certification/overview) soll Organisationen dabei helfen, Risiken zu bewerten und zu managen, indem Sicherheits- und Compliance-Informationen zu Ihrer App ausgewertet werden. Wenn Sie eine App im Teams Store veröffentlichen, müssen Sie die folgenden Programmstufen ausführen:

* [Publisher Verifizierung](/azure/active-directory/develop/publisher-verification-overview): Hilft Administratoren und Endbenutzern, die Authentizität von App-Entwicklern zu verstehen, die in die Microsoft Identity Platform integrieren. Nach Abschluss wird ein blaues "verifiziertes" Badge im Azure Active Directory (Azure AD)-Zustimmungsdialogfeld und auf anderen Bildschirmen angezeigt. Weitere Informationen finden Sie unter [Häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [wie Sie Ihre App als verifizierten Herausgeber markieren](/azure/active-directory/develop/mark-app-as-publisher-verified)und die [Herausgeberüberprüfung beheben](/azure/active-directory/develop/troubleshoot-publisher-verification).
* [Publisher Attestation](/microsoft-365-app-certification/docs/attestation): Ein Prozess, bei dem Sie allgemeine Datenverarbeitungs-, Sicherheits- und Compliance-Informationen gemeinsam nutzen, um potenziellen Kunden zu helfen, fundierte Entscheidungen über die Nutzung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine App übermitteln, die zuvor nicht aufgeführt wurde, können Sie Publisher Attestation erst dann offiziell abschließen, wenn sich Ihre App im Teams Store befindet. Wenn Sie eine aufgelistete App aktualisieren, schließen Sie Publisher Bescheinigung ab, bevor Sie die neueste Version der App übermitteln.

### <a name="22-bots"></a>2.2 Bots

Bei Apps, die den Microsoft Azure Bot Service verwenden (z. B. Bots und Messagingerweiterungen), müssen Sie alle Anforderungen erfüllen, die in den Microsoft [Online Services-Bedingungen](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)definiert sind.

Bots müssen immer um Erlaubnis bitten, eine Datei hochzuladen und eine Bestätigungsnachricht nach dem Hochladen der Datei anzuzeigen.

### <a name="23-external-domains"></a>2.3 Externe Domains

In den meisten Fällen dürfen Sie Domänen außerhalb der Kontrolle Ihrer Organisation (einschließlich Platzhalter) und Tunneldienste nicht in die Domänenkonfigurationen Ihrer App einbeziehen. Zu den folgenden Ausnahmen gehören:

* Wenn Ihre App die OAuthCard des Azure Bot Service verwendet, müssen Sie `token.botframework.com` eine gültige Domäne einschließen, oder die Schaltfläche **Anmelden** funktioniert nicht.
* Wenn Ihre App auf SharePoint basiert, können Sie die zugeordnete Stammwebsite SharePoint als gültige Domäne mithilfe der `{teamSiteDomain}` Kontexteigenschaft einschließen.

### <a name="24-authentication"></a>2.4 Authentifizierung

Informationen zum Implementieren der App-Authentifizierung finden Sie unter [Authentifizierung in Teams](~/concepts/authentication/authentication.md).

#### <a name="241-authenticating-with-external-services"></a>2.4.1 Authentifizierung mit externen Diensten

Beachten Sie Folgendes, wenn Ihre App Benutzer mit einem externen Dienst authentifiziert.

* **Melden Sie sich an, melden Sie sich an und melden Sie sich an:**
  * Apps, die von externen Konten oder Diensten abhängig sind, müssen eine klare und einfache Anmeldung, Abmelden und Anmeldeerfahrung bereitstellen.
  * Wenn sich ein Benutzer abmeldet, muss er sich nur über die App abmelden und bei Teams angemeldet bleiben.
* **Erfahrungmit der Inhaltsfreigabe:** Apps, die eine Authentifizierung mit einem externen Dienst benötigen, um Inhalte in Teams Kanälen freizugeben, müssen in der Hilfedokumentation (oder ähnlichen Ressourcen) eindeutig angeben, wie Inhalte getrennt oder aufgehört werden können, wenn diese Funktion auf dem externen Dienst unterstützt wird. Dies bedeutet nicht, dass die Möglichkeit, Inhalte zu teilen, in Ihrer Teams-App vorhanden sein muss.

#### <a name="242-government-community-cloud-listings"></a>2.4.2 Government Community Cloud Angebote

Um Ihre App an Government Community Cloud (GCC) Benutzer zu verteilen und gleichzeitig doppelte Auflistungen im Teams-Speicher zu vermeiden, muss der Authentifizierungsprozess Benutzer identifizieren und zu einer GCC-spezifischen oder erwarteten URL weiterleiten.

### <a name="25-sensitive-content"></a>2.5 Sensible Inhalte

Ihre App darf keine sensiblen Daten veröffentlichen, z. B. Kreditkarten- oder Finanzzahlungsinstrumentendaten. Die App darf auch keine Integrität, Kontaktverfolgung oder andere personenbezogene Daten (PII) für eine Zielgruppe anzeigen, die nicht dazu bestimmt ist, diesen Inhalt anzuzeigen.

Warnen Sie Benutzer, bevor Ihre App Dateien oder ausführbare Dateien (.exe) auf den Computer oder die Umgebung des Benutzers herunterlädt.

### <a name="26-financial-information"></a>2.6 Finanzinformationen

Apps dürfen Benutzer nicht auffordern, Zahlungen innerhalb der Teams-Schnittstelle zu tätigen. Finanzinstrumentdetails dürfen nicht über eine Bot-Schnittstelle an die Benutzer übermittelt werden.

Sie dürfen nur dann auf sichere, externe Zahlungsdienste verlinken, wenn Sie die entsprechende Offenlegung in Ihren Nutzungsbedingungen, Ihrer Datenschutzrichtlinie oder einer Profilseite oder Website vorgenommen haben, bevor der Nutzer der Nutzung der App zugestimmt hat.

Apps, die auf der iOS- oder Android-Version von Teams ausgeführt werden, müssen die folgenden Richtlinien einhalten:

* Apps dürfen keine In-App-Käufe, Testangebote oder Benutzeroberfläche enthalten, die darauf abzielt, kostenpflichtige Versionen oder Links zu Onlineshops zu verkaufen, in denen Benutzer andere Inhalte, Apps oder Add-Ins erwerben oder erwerben können.
* Wenn Ihre App ein Konto erfordert, müssen sich Benutzer kostenlos für ein Konto anmelden können. Die Nutzung des Begriffs **freies** oder **kostenloses Konto** ist verboten.
* Sie können bestimmen, ob ein Konto auf unbestimmte Zeit oder für eine begrenzte Zeit aktiv ist, aber wenn das Konto abläuft, kann keine Benutzeroberfläche, kein Text oder Links angezeigt werden, die auf die Notwendigkeit der Zahlung hinweisen.
* Die Datenschutzrichtlinien und Nutzungsbedingungen Ihrer App müssen frei von handelsbezogenen Benutzeroberflächen oder Links sein.

## <a name="30-general-functionality-and-performance"></a>3.0 Allgemeine Funktionalität und Leistung

### <a name="31-launching-external-functionality"></a>3.1 Starten externer Funktionen

Apps dürfen Benutzer nicht aus Teams für Kernbenutzerszenarien herausnehmen. App-Inhalte und Interaktionen können innerhalb Teams Funktionen wie Bots, Karten und Aufgabenmodule auftreten.

Sie sollten Benutzer irgendwo in Teams und nicht mit einer externen Website oder App verknüpfen. Für Szenarien, die externe Funktionen erfordern, muss Ihre App über explizite Benutzerberechtigungen zum Starten dieser Funktionalität verfügen.

### <a name="32-compatibility"></a>3.2 Kompatibilität

Apps müssen auf den folgenden Betriebssystemen und Browsern voll funktionsfähig sein:

* Microsoft Windows 7 und höher
* macOS 10.10 und höher
* Microsoft Edge 12 und höher
* Mozilla Firefox 47.0 und höher
* Google Chrome 51.0 und höher
* iOS 9.0 und höher
* Android 4.4 und höher

### <a name="33-response-time"></a>3.3 Reaktionszeit

Teams-Apps müssen innerhalb eines angemessenen Zeitrahmens reagieren, der je nach Funktion variiert.

* Registerkarten müssen innerhalb von drei Sekunden reagieren oder eine Lademeldung oder Warnung anzeigen.
* Bots müssen innerhalb von zwei Sekunden auf Benutzerbefehle reagieren oder eine Eingabeanzeige anzeigen.
* Messagingerweiterungen müssen innerhalb von fünf Sekunden auf Benutzerbefehle reagieren.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

## <a name="40-app-package-and-store-listing"></a>4.0 App-Paket und Store-Eintrag

App-Pakete müssen korrekt formatiert sein und alle erforderlichen Informationen und Komponenten enthalten.

### <a name="41-app-manifest"></a>4.1 App-Manifest

Das Teams App-Manifest definiert die Konfigurationen Ihrer App.

* Ihr Manifest muss dem neuesten Manifestschema entsprechen. Weitere Informationen finden Sie im [Manifestverweis](~/resources/schema/manifest-schema.md).
* Wenn Ihre App einen Bot oder eine Messaging-Erweiterung enthält, muss Ihr Manifest mit Bot Framework-Metadaten konsistent sein, einschließlich Bot-Name, Logo, Datenschutzrichtlinienlink und Dienstbedingungen-Link.
* Wenn Ihre App Azure Active Directory (Azure AD) für die Authentifizierung verwendet, fügen Sie die Azure AD-Anwendungs-ID (Client) in das Manifest ein. Weitere Informationen finden Sie im [Manifestverweis](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="42-app-icons"></a>4.2 App-Symbole

Symbole sind eines der Hauptelemente, die Menschen beim Durchsuchen des Teams-Shops sehen. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig die folgenden Anforderungen erfüllen:

* Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: ein Farbsymbol und ein Gliederungssymbol.
* Die Farbversion ihres Symbols wird in den meisten Teams Szenarien angezeigt und muss 192x192 Pixel betragen. Ihr Symbolsymbol (96x96 Pixel) kann eine beliebige Farbe oder Farbe sein, muss jedoch auf einem durchgezogenen oder vollständig transparenten quadratischen Hintergrund sitzen.
* Die Gliederungsversion Ihres Symbols wird angezeigt, wenn Ihre App verwendet wird und auf der App-Leiste auf der linken Seite Teams und wenn ein Benutzer die Messaging-Erweiterung Ihrer App anheftet. Es muss 32x32 Pixel groß sein und kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind erlaubt). Das Symbol sollte keine zusätzliche Auffüllung um das Symbol herum haben.
* Korrekte und formatierte Symbole müssen in Ihrem App-Paket enthalten sein. Die Symbole müssen auch mit den übermittelten Metadaten übereinstimmen.

Weitere Informationen, bewährte Methoden und Beispiele finden Sie in den Richtlinien für Teams [App-Symbol .](~/concepts/build-and-test/apps-package.md#app-icons)

### <a name="43-app-descriptions"></a>4.3 App-Beschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben. Die Beschreibungen in Ihren App-Konfigurationen und dem Partner Center müssen identisch sein.

Beschreibungen sollten nicht direkt oder durch Unterstellung eine andere Marke (microsoft-eigentümer oder anderweitig) verunglimpfen. Stellen Sie sicher, dass Ihre Beschreibung keine Ansprüche enthält, die nicht begründet werden können (z. B. "Garantierte 200-prozentige Effizienzsteigerung").

#### <a name="431-short-description"></a>4.3.1 Kurzbeschreibung

Eine kurze Beschreibung ist eine kurze Zusammenfassung Ihrer App, die ihr Wertversprechen hervorhebt und sich an Ihre Zielgruppe richtet.

**Dos:**

* Halten Sie die Kurzbeschreibung auf einen Satz.
* Die wichtigsten Informationen kommen an erster Stelle.
* Schließen Sie Schlüsselwörter ein, nach denen Kunden wahrscheinlich suchen.

**Don’ts:**

* Wiederholen Sie Ihren App-Namen.
* Verwenden Sie das Wort **App** in der Kurzbeschreibung.

#### <a name="432-long-description"></a>4.3.2 Lange Beschreibung

Die lange Beschreibung kann eine ansprechende Erzählung bieten, die das Wertversprechen, die primäre Zielgruppe und die Zielindustrie Ihrer App hervorhebt. Während diese Beschreibung bis zu 4.000 Zeichen lang sein kann, lesen die meisten Benutzer nur zwischen 300-500 Wörtern.

**Dos:**

* Verwenden Sie [Markdown,](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) um Ihre Beschreibung zu formatieren.
* Verwenden Sie aktive Stimme und sprechen Sie direkt mit Benutzern. Zum *Beispiel, Sie können ...*.
* Listen Sie Features mit Aufzählungszeichen auf, sodass die Beschreibung einfacher zu scannen ist.
* Beschreiben Sie eindeutig Einschränkungen, Bedingungen oder Ausnahmen von den Funktionen, Features und Lieferbestandteilen, die in der Auflistung und verwandten Materialien beschrieben sind, bevor der Benutzer Ihre App installiert. Die Teams Funktionen, die Ihre App unterstützt, müssen sich auf die Kernfunktionen beziehen, die In Ihrem Eintrag beschrieben werden.
* Fügen Sie einen Hilfe- oder Supportlink ein.
* Siehe **Microsoft 365** statt **Office 365**.
* Wenn Sie auf **Teams** verweisen müssen, schreiben Sie den ersten Verweis als **Microsoft Teams**. Nachfolgende Referenzen können auf **Teams** verkürzt werden.
* Verwenden Sie die folgende Sprache, wenn Sie beschreiben, wie die App mit Teams (oder Microsoft 365) funktioniert:
  * "... arbeitet mit Microsoft Teams."
  * "... Zusammenarbeit mit Microsoft Teams."
  * "... innerhalb Microsoft Teams."
  * "... für Microsoft Teams."

**Don’ts:**

* Überschreiten Sie 500 Wörter.
* Abkürzen Sie **Microsoft** als **MS** oder **MSFT**.
* Geben Sie an, dass es sich bei der App um ein Angebot von Microsoft handelt, einschließlich der Verwendung von Microsoft-Slogans oder -Slogans.
* Verwenden Sie urheberrechtlich geschützte Markennamen, die Sie nicht besitzen.
* Fügen Sie Tippfehler, grammatikalische Fehler und unnötige Großschreibungen ein (z. B. **Benutzer** statt **Benutzer**).
* Fügen Sie Links zu AppSource ein.
* Verwenden Sie die folgende Sprache, es sei denn, Sie sind zertifizierter Microsoft-Partner:
  * "... integriert mit Microsoft Teams"
  * "... integriert sich mit ..."
  * "... gebaut für ..."
  * "... gebaut auf ..."
  * "... läuft auf ..."
  * "... aktiviert durch ..."
  * "... zertifiziert für ..."
  * "... entwickelt für ..."
  * "... entwickelt für ..."

### <a name="44-screenshots"></a>4.4 Screenshots

Screenshots bieten eine prominente visuelle Vorschau Ihrer App, um Ihren App-Namen, Ihr Symbol und Ihre Beschreibungen zu ergänzen. Erinnern Sie sich an die folgenden Screenshots:

* Sie können bis zu fünf Screenshots pro Liste haben.
* Zu den unterstützten Dateitypen gehören PNG, JPEG und GIF.
* Die Abmessungen sollten 1366x768 Pixel betragen.
* Maximale Größe von 1.024 KB.

**Dos:**

* Konzentrieren Sie sich auf die Funktionen Ihrer App (z. B. wie Personen mit Ihrem Bot kommunizieren können).
* Fügen Sie Inhalte ein, die Ihre App korrekt darstellen.
* Verwenden Sie Text mit Bedacht.
* Frame-Screenshots mit einer Farbe, die Ihre Marke widerspiegelt und Marketinginhalte enthält, ähnlich wie das [Beispiel für Die Freshdesk-Auflistung](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) (Dimensionsanforderungen gelten für das gesamte Bild und nicht nur für den Screenshot).

**Don’ts:**

* Zeigen Sie bestimmte Geräte an, z. B. Telefone oder Laptops.
* Zeigen Sie Chrom oder Benutzeroberfläche an, die sich nicht in Ihrer App befindet.
* Erfassen Sie Teams oder Browser-Benutzeroberfläche in Ihren Screenshots.
* Fügen Sie Mockups ein, die die tatsächliche Benutzeroberfläche Ihrer App nicht genau widerspiegeln, z. B. die Anzeige der Verwendung der App außerhalb Teams.

> [!TIP]
> Ein Video kann die effektivste Möglichkeit sein, zu kommunizieren, warum Benutzer Ihre App verwenden sollten. Ein Video ist auch das erste, was Benutzer in Ihrem Eintrag sehen (standardmäßig wird ein Video vor Screenshots angezeigt). Weitere Informationen finden Sie unter [Erstellen eines Videos für Ihren Shop-Eintrag](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

### <a name="45-privacy-policy"></a>4.5 Datenschutzerklärung

Die Datenschutzrichtlinie kann spezifisch für Ihre Teams App oder eine allgemeine Richtlinie für alle Ihre Dienste sein.

* Wenn Sie eine generische Datenschutzrichtlinienvorlage verwenden, müssen Sie **auf Dienste**, **Anwendungen** und **Plattformen** verweisen, um Ihre Teams-App und Ihren Dienst oder Ihre Website einzuschließen.
* Sie müssen die Art und Weise umfassen, wie Sie mit der Speicherung, Aufbewahrung und Löschung von Benutzerdaten umgehen. Sie müssen auch die Sicherheitskontrollen beschreiben, die Sie für den Datenschutz verwenden.
* Sie müssen Ihre Kontaktinformationen enthalten.
* Sollte keine URLs enthalten, die defekt sind oder zu Beta- oder Stagingzwecken.
* Links zu AppSource dürfen nicht enthalten sein.

### <a name="46-terms-of-use"></a>4.6 Nutzungsbedingungen

Ihre Nutzungsbedingungen sollten spezifisch sein und auf Ihr Angebot anwendbar sein.

### <a name="47-support-links"></a>4.7 Support-Links

Die Support-URLs Ihrer App sollten keine Authentifizierung erfordern. Benutzer sollten sich beispielsweise nicht anmelden müssen, um Sie zu kontaktieren.

### <a name="48-localization"></a>4.8 Lokalisierung

Wenn Ihre App die Lokalisierung unterstützt, muss Ihr App-Paket eine Datei mit Sprachübersetzungen enthalten, die basierend auf der Teams Spracheinstellung angezeigt werden. Die Datei muss dem Teams-Lokalisierungsschema entsprechen. Weitere Informationen finden Sie im [Teams Lokalisierungsschema](~/concepts/build-and-test/apps-localization.md).

## <a name="50-tabs"></a>5.0 Tabs

Wenn Ihre App eine Registerkarte enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer hochwertigen App-Erfahrung finden Sie in den [Richtlinien für den Teams-Registerkartendesign](~/tabs/design/tabs.md).

### <a name="51-setup"></a>5.1 Einrichtung

* Tab-Setup darf einen neuen Benutzer nicht in die Sackgasse stellen. Geben Sie eine Meldung zum Abschließen der Aktion oder des Workflows an.
* Die Authentifizierung sollte während der Tab-Einrichtung und nicht danach erfolgen.

### <a name="52-views"></a>5.2 Ansichten

* Der Anmeldebildschirmbereich darf keine großen Logos verwenden oder eine ganze Webseite anzeigen.
* Inhalte können vereinfacht werden, indem sie auf mehrere Registerkarten aufklappen.
* Registerkarten sollten keinen doppelten Header haben. Entfernen Sie das Logo aus dem iframe, da das Registerkartenframework bereits das App-Symbol und den Namen anzeigt.

### <a name="53-navigation"></a>5.3 Navigation

* Registerkarten dürfen nicht mehr als drei Navigationsebenen haben.
* Registerkarten dürfen keine Navigation bereitstellen, die mit der primären Teams Navigation in Konflikt steht.
* Die sekundären und tertiären Seiten in einer Registerkarte müssen in einer Ansicht der Ebene 2 und der Ebene 3 im Hauptregisterbereich geöffnet werden, die über Breadcrumbs oder das linke Navi navigiert wird. Sie können auch die folgenden Komponenten einschließen, um die Tab-Navigation zu unterstützen:
    * Zurück-Tasten
    * Seitenüberschriften
    * Hamburger Menüs
* Die Registerkarte sollte nicht über einen horizontalen Bildlauf verfügen.
* Deep Links in Registerkarten dürfen nicht mit einer externen Webseite verknüpft werden, sondern irgendwo innerhalb Teams. Beispiel: Taskmodule oder andere Registerkarten.
* Registerkarten sollten es Benutzern nicht erlauben, außerhalb Teams für die Kern-App-Erfahrung zu navigieren.

### <a name="54-usability"></a>5.4 Benutzerfreundlichkeit

* Tabs müssen einen Wert bieten, der über das bloße Hosten einer vorhandenen Website hinausgeht.
* Benutzer müssen in der Lage sein, ihre letzte Aktion auf der Registerkarte rückgängig zu machen.
* Registerkarten in einem persönlichen Kontext können Inhalte aus freigegebenen Instanzen der App aggregieren.
* Registerkarten müssen auf Teams Themen reagieren. Wenn ein Benutzer das Design ändert, muss das Design der App die Auswahl widerspiegeln.
* Registerkarten müssen Teams Komponenten verwenden, z. B. Teams Schriftarten, Typrampen, Farbpaletten, Rastersystem, Bewegung, Ton der Stimme usw., wann immer dies möglich ist.
* Sie müssen eine **Einstellungen** Registerkarte einschließen.
* Registerkarten müssen Teams Interaktionsentwurfs folgen, z. B. in der Seitennavigation, Position und Verwendung von Dialogfeldern, Informationshierarchien usw., wann immer dies möglich ist.
* Tabinhalt im iframe darf keine Features enthalten, die Teams Kernfunktionen imitieren. Beispielsweise Bots, Messaging-Erweiterungen, Anrufe, Besprechungen usw.

> [!TIP]
>
> * Fügen Sie einen persönlichen Bot neben einem persönlichen Tab ein.
> * Erlauben Sie Benutzern, Inhalte über ihre persönliche Registerkarte freizugeben.

## <a name="60-bots"></a>6.0 Bots

Wenn Ihre App einen Bot enthält, stellen Sie sicher, dass er diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Richtlinien für Teams-Bot-Design](~/bots/design/bots.md).

### <a name="61-bot-commands"></a>6.1 Bot-Befehle

Die Analyse von Benutzereingaben und die Vorhersage der Benutzerabsicht ist schwierig. Bot-Befehle bieten Benutzern eine Reihe von Wörtern oder Phrasen, die Ihr Bot versteht, so dass sie (und Ihr Bot) nicht raten müssen.

* Es wird dringend empfohlen, unterstützte Bot-Befehle in Ihren App-Konfigurationen aufzulisten. Diese Befehle werden im Feld Verfassen angezeigt, wenn ein Benutzer versucht, einen Bot zu vermelden.
* Alle Befehle, die Ihr Bot unterstützt, müssen ordnungsgemäß funktionieren, einschließlich des Befehls **Hi**, **Hello** und **Help.**

> [!TIP]
> Für persönliche Bots,  fügen Sie eine Hilfe-Registerkarte, die weiter beschreibt, was Ihr Bot tun kann.

### <a name="62-bot-welcome-messages"></a>6.2 Bot-Willkommensbotschaften

* Bots sollten fast immer eine Willkommensnachricht während des ersten Laufs senden. Für die beste Erfahrung sollte die Nachricht das Wertversprechen Ihres Bots enthalten, wie Sie den Bot konfigurieren und kurz alle unterstützten Bot-Befehle beschreiben. Sie können die Nachricht mit einer adaptiven Karte mit Schaltflächen anzeigen, um die Benutzerfreundlichkeit zu verbessern. Weitere Informationen finden Sie unter [Auslösen einer Bot-Willkommensnachricht](~/bots/how-to/conversations/send-proactive-messages.md).
* Bot-Willkommensbotschaften in Kanälen und Chats sind während der ersten Ausführung optional, vor allem, wenn der Bot für den persönlichen Gebrauch verfügbar ist und ähnliche Aktionen ausführt. Wenn Ihr Bot Willkommensnachrichten sendet, darf er diese nicht einzeln an Benutzer senden (dies gilt als [Spamming).](#63-bot-message-spamming) Die Nachricht sollte auch die Person erwähnen, die den Bot hinzugefügt hat.
* Nur Benachrichtigungsbots müssen eine Willkommensnachricht senden, die vermittelt, dass sie nicht auf die Nachrichten der Benutzer antworten.

> [!TIP]
> In Willkommensbotschaften an einzelne Benutzer kann eine Karusselltour einen effektiven Überblick über Ihren Bot und alle anderen App-Funktionen bieten. Das Einschließen von Schaltflächen, die Benutzer bot-Befehle ausprobieren lassen, wird empfohlen. Erstellen Sie z. **B. eine Aufgabe**.

### <a name="63-bot-message-spamming"></a>6.3 Bot-Nachricht Spamming

Bots dürfen Benutzer nicht spamn, indem sie mehrere Nachrichten in kurzer Folge senden.

* **Bot-Nachrichten in Kanälen und Chats**: Spam-Benutzer nicht durch die Erstellung separater Beiträge. Erstellen Sie einen einzelnen Beitrag mit Antworten im gleichen Thread.
* **Bot-Nachrichten in persönlichen Apps**: Senden Sie nicht mehrere Nachrichten in schneller Folge. Senden Sie eine Nachricht mit vollständigen Informationen. Vermeiden Sie Mehrumdrehungen, um einen einzelnen Workflow abzuschließen. Erwägen Sie stattdessen, ein Formular (oder Einaufgabenmodul) zu verwenden, um alle Eingaben von einem Benutzer gleichzeitig zu erfassen.
* **Willkommensbotschaften**: Das Wiederholen der gleichen Begrüßungsnachricht über regelmäßige Intervalle ist nicht erlaubt und wird als Spamming betrachtet. Wenn beispielsweise ein neues Mitglied zu einem Team hinzugefügt wird, spamn Sie die anderen Mitglieder nicht mit einer Willkommensnachricht. Nachricht an das neue Mitglied persönlich.

### <a name="64-bot-notifications"></a>6.4 Bot-Benachrichtigungen

Bot-Benachrichtigungen müssen Inhalte enthalten, die für den Bereich relevant sind, den Sie für den Bot definieren (Team, Chat oder Persönlich).

### <a name="65-bots-and-adaptive-cards"></a>6.5 Bots und Adaptive Karten

Adaptive Karten sind eine sehr empfehlenswerte Möglichkeit, Bot-Nachrichten anzuzeigen. Ihre Karten müssen leicht sein und nur 1-3 Aktionen enthalten. Wenn Sie mehr Inhalt anzeigen müssen, sollten Sie ein Taskmodul oder eine Registerkarte verwenden.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Entwerfen Adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Karten-Referenz](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="70-messaging-extensions"></a>7.0 Messaging-Erweiterungen

Wenn Ihre App eine Messagingerweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Richtlinien für den Entwurf Teams Messagingerweiterung](~/messaging-extensions/design/messaging-extension-design.md).

### <a name="71-action-commands"></a>7.1 Aktionsbefehle

Aktionsbasierte Messagingerweiterungen sollten folgendes tun:

* Erlauben Sie Benutzern, Aktionen für eine Nachricht auszulösen, ohne Zwischenschritte auszuführen, z. B. anmelden.
* Übergeben Sie den Nachrichtenkontext an den nächsten Arbeitszustand.

### <a name="72-preview-links-link-unfurling"></a>7.2 Vorschau links (Link Entrollt)

Messagingerweiterungen sollten erkannte Links im Feld Teams verfassen in der Vorschau anzeigen. Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden (entweder absolute URLs oder Platzhalter). Beispielsweise `yourapp.onmicrosoft.com` ist gültig, aber `*.onmicrosoft.com` nicht gültig. Domains der obersten Ebene sind ebenfalls verboten (z. B. `*.com` oder `*.org` ).

### <a name="73-search-commands"></a>7.3 Suchbefehle

* Suchbasierte Messagingerweiterungen müssen Text bereitstellen, der Benutzern beim effektiven Suchen hilft.
* @mention ausführbare Dateien müssen klar, leicht verständlich und lesbar sein.

## <a name="80-task-modules"></a>8.0 Aufgabenmodule

Ein Aufgabenmodul muss ein Symbol und den Kurznamen der App enthalten, der es zugeordnet ist.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Teams-Task-Modul-Entwurfsrichtlinien](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

## <a name="90-meeting-extensions"></a>9.0 Besprechungserweiterungen

Wenn Ihre App eine Besprechungserweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Richtlinien für die Teams Besprechungserweiterungsdesign](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

### <a name="91-pre--and-post-meeting-experience"></a>9.1 Vor- und Nachbesprechungserfahrung

* Bildschirme vor und nach dem Meeting müssen den allgemeinen Richtlinien für das Tab-Design entsprechen. Weitere Informationen finden Sie in den [Teams Entwurfsrichtlinien](~/tabs/design/tabs.md).
* Registerkarten dürfen nicht horizontal gescrollt werden.
* Registerkarten sollten ein organisiertes Layout aufweisen, wenn mehrere Elemente angezeigt werden. Zum Beispiel mehr als 10 Umfragen oder Umfragen. Siehe [Beispiellayout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Ihre App muss Benutzer benachrichtigen, wenn die Ergebnisse einer Umfrage oder Umfrage exportiert werden, indem sie "Ergebnisse erfolgreich heruntergeladen" angibt.

### <a name="92-in-meeting-experience"></a>9.2 In-Meeting-Erfahrung

* Apps dürfen nur während Besprechungen ein dunkles Thema verwenden. Weitere Informationen finden Sie in den [Teams Entwurfsrichtlinien](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming).
* Eine QuickInfo sollte den App-Namen anzeigen, wenn Sie während Besprechungen mit dem Mauszeiger über das App-Symbol bewegen.
* Messagingerweiterungen müssen während Besprechungen genauso funktionieren wie außerhalb von Besprechungen.

### <a name="93-in-meeting-tabs"></a>9.3 Registerkarten in der Besprechung

* Muss ansprechbar sein. Achten Sie darauf, die Polsterung und die Komponentengrößen beizubehalten.
* Muss über eine Zurück-Schaltfläche verfügen, wenn mehr als eine Navigationsebene vorhanden ist.
* Es darf nicht mehr als eine Schaltfläche zum Schließen oder Schließen enthalten. Dies kann Benutzer verwirren, da es bereits eine integrierte Header-Schaltfläche gibt, um die Registerkarte zu schließen.
* Es darf kein horizontales Scrollen durchgeführt werden.

### <a name="94-in-meeting-dialogs"></a>9.4 In-Meeting-Dialoge

* Sollte sparsam und für Licht- und aufgabenorientierte Szenarien eingesetzt werden.
* Inhalte müssen in einer einzelnen Spalte angezeigt werden und dürfen nicht über mehrere Navigationsebenen verfügen.
* Vorgangsmodule dürfen nicht verwendet werden.
* Muss mit der Mitte der Besprechungsphase ausgerichtet werden.
* Sollte verworfen werden, sobald ein Benutzer eine Schaltfläche auswählt oder eine Aktion ausführt.

## <a name="100-notifications"></a>10.0 Benachrichtigungen

Wenn Ihre App die [von Microsoft Graph bereitgestellten Aktivitätsfeed-APIs](/graph/teams-send-activityfeednotifications)verwendet, stellen Sie sicher, dass sie die folgenden Richtlinien einhält.

### <a name="101-general"></a>10.1 Allgemein

* Alle benachrichtigungstrigger, die in Ihren App-Konfigurationen angegeben sind, sollten eine Benachrichtigung in der App erhalten.
* Benachrichtigungen müssen gemäß den unterstützten Sprachen lokalisiert werden, die für Ihre App konfiguriert sind.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

### <a name="102-avatars"></a>10.2 Avatare

* Der Benachrichtigungs-Avatar sollte mit dem Farbsymbol Ihrer App übereinstimmen.
* Benachrichtigungen, die von einem Benutzer ausgelöst werden, sollten den Avatar des Benutzers enthalten.

### <a name="103-spamming"></a>10.3 Spamming

* Apps dürfen nicht mehr als 10 Benachrichtigungen pro Minute an einen Benutzer senden.
* Bots und der Aktivitätsfeed sollten keine doppelten Benachrichtigungen auslösen.
* Benachrichtigungen müssen Benutzern einen bestimmten Wert bieten und dürfen nicht für triviale oder irrelevante Ereignisse verwendet werden.

### <a name="104-navigation-and-layout"></a>10.4 Navigation und Layout

* Benachrichtigungen müssen dem Teams-Aktivitätsfeed-Layout und der Erfahrung entsprechen.
* Bei der Auswahl einer Benachrichtigung muss der Benutzer zu relevanten Inhalten innerhalb Teams weitergeleitet und nicht aus dem Teams-Erlebnis herausgenommen werden.

## <a name="110-advertising"></a>11.0 Werbung

Apps dürfen keine Werbung anzeigen, einschließlich dynamischer Anzeigen, Banneranzeigen und Anzeigen in Nachrichten.

## <a name="see-also"></a>Siehe auch

[4.0 App-Paket und Store-Eintrag](#40-app-package-and-store-listing)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines Partner Center-Kontos](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
