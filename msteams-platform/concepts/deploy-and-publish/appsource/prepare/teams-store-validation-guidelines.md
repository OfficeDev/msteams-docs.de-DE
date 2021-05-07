---
title: Microsoft Teams richtlinien für die Speicherüberprüfung
description: Beschreibt die Richtlinien, die jede an den Teams (AppSource) übermittelte App befolgen muss.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: df60cf9e4a173186fbacacc90621c2efb23ba17f
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230925"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Microsoft Teams richtlinien für die Speicherüberprüfung

Wenn Sie diese Richtlinien befolgen, erhöht sich die Wahrscheinlichkeit, dass Ihre App den Microsoft Teams Store-Übermittlungsprozess übernimmt. Diese Teams-spezifischen Richtlinien ergänzen die Microsoft Commercial Marketplace-Zertifizierungsrichtlinien und werden häufig aktualisiert, um neue Funktionen, Benutzerfeedback und Änderungen an Geschäftsregeländerungen widerspiegeln zu können. [](https://docs.microsoft.com/legal/marketplace/certification-policies)

> [!NOTE]
> Einige Richtlinien gelten möglicherweise nicht für Ihre App. Wenn Ihre App beispielsweise keinen Bot enthält, können Sie botbezogene Richtlinien ignorieren.

## <a name="10-value-proposition"></a>1.0 Wertversprechen

### <a name="11-app-name"></a>1.1 App-Name

Der Name einer App spielt eine wichtige Rolle bei der Benutzerentkung im Store. Beachten Sie Folgendes zu App-Namen:

* Der Name muss Begriffe enthalten, die für Ihre Benutzer relevant sind.
* Die Namen der Teams features&#8212;wie **Chat**, **Contacts**, **Calendar**, **Calls**, **Files**, **Activity**, **Teams**, **Apps** und **Help**&#8212;sollten nicht in Ihrem App-Namen enthalten sein.
* Allgemeine Substantive müssen mit dem Namen des Entwicklers (z. B. **"Contoso Tasks"** statt "Tasks") vorangestellt oder mit **suffixiert werden.**
* Darf keine **Teams** oder andere Microsoft-Produktnamen verwenden, die fälschlicherweise auf co-branding oder Co-Selling hinweisen könnten. (Weitere Informationen zum Verweisen auf Microsoft-Software, -Produkte und -Dienste finden Sie unter [Microsoft Trademark and Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)).
* Wenn Ihre App Teil einer offiziellen Partnerschaft mit Microsoft ist, muss der Name Ihrer App zuerst kommen (z. B. **Contoso Connector für Microsoft Teams**).
* Darf nicht den Namen einer App kopieren, die im Store oder in einem anderen Angebot auf dem kommerziellen Marktplatz aufgeführt ist.
* Darf keine profanen oder abfälligen Begriffe enthalten. Der Name darf auch keine rassistisch oder kulturell unempfindliche Sprache enthalten.
* Muss eindeutig sein. Sie können beispielsweise nicht mehrere Apps für verschiedene Regionen mit demselben Namen und derselben Funktionalität auflisten.

Siehe auch: [4.0-App-Paket und Store-Eintrag](#40-app-package-and-store-listing)

### <a name="12-suitable-for-workplace-consumption"></a>1.2 Geeignet für den Arbeitsplatzverbrauch

App-Inhalte müssen für den allgemeinen Arbeitsplatzverbrauch geeignet sein und alle In den Kommerziellen Marketplace-Zertifizierungsrichtlinien aufgeführten Einschränkungen beachten. Inhalte im Zusammenhang mit Derreligion, der Politik, dem Spielen und der verlängerten Unterhaltung sind verboten. Weitere Informationen finden Sie unter [Commercial Marketplace Certification Policies](https://docs.microsoft.com/legal/marketplace/certification-policies#10010-inappropriate-content).

Ihre App muss die Gruppenzusammenarbeit erleichtern, die Produktivität einer Person verbessern oder beides. Apps, die für die Teambindung und Geselligkeit vorgesehen sind, müssen zusammenarbeiten und für mehrere Teilnehmer ausgelegt sein. Diese Arten von Apps sollten auch keine erheblichen Zeitinvestitionen erfordern oder sich spürbar auf die Produktivität auswirken.

### <a name="13-similar-platforms-and-services"></a>1.3 Ähnliche Plattformen und Dienste

Apps müssen sich auf die Teams konzentrieren und dürfen keine Namen, Symbole oder Bilder anderer ähnlicher chatbasierter Plattformen oder Dienste für die Zusammenarbeit enthalten, es sei denn, Ihre App bietet eine bestimmte Interoperabilität.

### <a name="14-feature-names"></a>1.4 Featurenamen

Namen von App-Features in Schaltflächen und anderen Benutzeroberflächentexten dürfen nicht mit der Terminologie in Konflikt stehen, die für Teams und andere Microsoft-Produkte reserviert ist (z. B. Besprechung **starten,** Anruf machen **oder** Chat **starten).** Schließen Sie Ihren App-Namen ein, wenn Sie dies nicht vollständig vermeiden können, z. **B. Contoso-Besprechung starten** statt **Besprechung starten.**

## <a name="20-security"></a>2.0 Sicherheit

### <a name="21-microsoft-365-app-compliance-program"></a>2.1 Microsoft 365 App Compliance Program

Das [Microsoft 365 App Compliance Program](https://docs.microsoft.com/microsoft-365-app-certification/overview) soll Organisationen dabei helfen, Risiken zu bewerten und zu verwalten, indem Sicherheits- und Complianceinformationen zu Ihrer App ausgewertet werden. Wenn Sie eine App im Teams veröffentlichen, müssen Sie die folgenden Stufen des Programms abschließen:

* [Publisher Überprüfung](/azure/active-directory/develop/publisher-verification-overview): Hilft Administratoren und Endbenutzern, die Authentizität von App-Entwicklern zu verstehen, die in das Microsoft Identity Platform. Nach Abschluss wird auf dem Zustimmungsdialogfeld Azure Active Directory (Azure AD) und anderen Bildschirmen ein blaues "überprüftes" Signal angezeigt. Weitere Informationen finden Sie unter [häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), wie Sie Ihre [App](/azure/active-directory/develop/mark-app-as-publisher-verified)als herausgeberverifiziert markieren und die Herausgeberüberprüfung [beheben.](/azure/active-directory/develop/troubleshoot-publisher-verification)
* [Publisher Attestation](/microsoft-365-app-certification/docs/attestation): Ein Prozess, bei dem Sie allgemeine Informationen zur Datenverarbeitung sowie Sicherheits- und Complianceinformationen freigeben, um potenziellen Kunden dabei zu helfen, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

> [!NOTE]
> Wenn Sie eine App übermitteln, die noch nicht aufgeführt wurde, können Sie die Publisher-Bestätigung erst dann offiziell abschließen, wenn sich Ihre App im Teams befindet. Wenn Sie eine aufgelistete App aktualisieren, schließen Sie Publisher, bevor Sie die neueste Version der App übermitteln.

### <a name="22-bots"></a>2.2 Bots

Für Apps, die den Microsoft Azure Bot Service verwenden (z. B. Bots und Messagingerweiterungen), müssen Sie alle Anforderungen erfüllen, die in den Microsoft [Online Services Terms definiert sind.](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)

Bots müssen immer die Berechtigung zum Hochladen einer Datei und zum Anzeigen einer Bestätigungsnachricht nach dem Hochladen der Datei bitten.

### <a name="23-external-domains"></a>2.3 Externe Domänen

In den meisten Fällen dürfen Sie domänen außerhalb der Kontrolle Ihrer Organisation (einschließlich Platzhalter) und Tunneldienste nicht in die Domänenkonfigurationen Ihrer App einschl. Die folgenden Ausnahmen sind:

* Wenn Ihre App die OAuthCard des Azure Bot-Diensts verwendet, müssen Sie eine gültige Domäne hinzufügen, oder die Schaltfläche Anmelden `token.botframework.com` funktioniert nicht. 
* Wenn Ihre App auf SharePoint basiert, können Sie die zugeordnete Stammwebsite SharePoint mithilfe der Context-Eigenschaft als gültige `{teamSiteDomain}` Domäne hinzufügen.

### <a name="24-authentication"></a>2.4 Authentifizierung

Informationen zum Implementieren der App-Authentifizierung finden Sie unter [Authentifizierung in Teams](~/concepts/authentication/authentication.md).

#### <a name="241-authenticating-with-external-services"></a>2.4.1 Authentifizierung bei externen Diensten

Beachten Sie Folgendes, wenn Ihre App Benutzer mit einem externen Dienst authentifiziert.

* **Anmelden, Abmelden und Registrieren von Erfahrungen**:
  * Apps, die von externen Konten oder Diensten abhängig sind, müssen klare und einfache Anmelde-, Abmelde- und Anmeldeerfahrungen bereitstellen.
  * Wenn sich ein Benutzer abmeldet, muss er sich nur von der App abmelden und bei der Teams.
* Erfahrungen mit der Inhaltsfreigabe: Apps, die eine Authentifizierung mit einem externen Dienst zum Freigeben von Inhalten in Teams-Kanälen erfordern, müssen in der Hilfedokumentation (oder ähnlichen Ressourcen) klar zum Trennen oder Freigeben von Inhalten beitragen, wenn dieses Feature vom externen Dienst unterstützt wird. Dies bedeutet nicht, dass die Möglichkeit der Freigabe von Inhalten in Ihrer App vorhanden Teams sein muss.

#### <a name="242-government-community-cloud-listings"></a>2.4.2 Government Community Cloud Einträge

Um Ihre App an Government Community Cloud (GCC)-Benutzer zu verteilen und doppelte Einträge im Teams-Speicher zu vermeiden, muss der Authentifizierungsprozess Benutzer identifizieren und an eine GCC-spezifische oder erwartete URL weiterverladen.

### <a name="25-sensitive-content"></a>2.5 Vertrauliche Inhalte

Ihre App darf keine vertraulichen Daten veröffentlichen, z. B. Kreditkarten- oder Zahlungsinstrumentdaten. Die App darf außerdem keine Integrität, Kontaktablaufverfolgung oder andere personenbezogene Informationen (PII) für eine Zielgruppe anzeigen, die diesen Inhalt nicht anzeigen möchte.

Warnen Sie Benutzer, bevor Ihre App Dateien oder ausführbare Dateien (.exe) auf den Computer oder die Umgebung des Benutzers herunterlädt.

### <a name="26-financial-information"></a>2.6 Finanzinformationen

Apps dürfen Benutzer nicht bitten, Zahlungen innerhalb der benutzeroberfläche Teams leisten. Finanzinstrumentdetails dürfen nicht über eine Botschnittstelle an Benutzer übermittelt werden.

Sie können nur dann zu sicheren externen Zahlungsdiensten verlinken, wenn Sie die entsprechende Offenlegung in Ihren Nutzungsbedingungen, Datenschutzrichtlinien oder einer Profilseite oder Website vorgenommen haben, bevor der Benutzer der Verwendung der App zugestimmt hat.

Apps, die auf der iOS- oder Android-Version von Teams ausgeführt werden, müssen die folgenden Richtlinien einhalten:

* Apps dürfen keine In-App-Käufe, Testangebote oder Benutzeroberflächen enthalten, mit denen kostenpflichtige Versionen oder Links zu Onlinespeichern angeboten werden sollen, in denen Benutzer andere Inhalte, Apps oder Add-Ins erwerben oder erwerben können.
* Wenn Ihre App ein Konto erfordert, müssen Sich Benutzer kostenlos für ein Konto registrieren können. Die Verwendung des **Begriffs kostenloses oder** **kostenloses Konto** ist untersagt.
* Sie können bestimmen, ob ein Konto auf unbestimmte Zeit oder für einen begrenzten Zeitraum aktiv ist, aber wenn das Konto abläuft, werden möglicherweise keine Benutzeroberfläche, kein Text oder Links angezeigt, die die Notwendigkeit einer Zahlung angeben.
* Die Datenschutzrichtlinien und Nutzungsbedingungen Ihrer App müssen frei von beliebigen handelsbezogenen Benutzeroberflächen oder Links sein.

## <a name="30-general-functionality-and-performance"></a>3.0 Allgemeine Funktionalität und Leistung

### <a name="31-launching-external-functionality"></a>3.1 Starten externer Funktionen

Apps dürfen Benutzer nicht aus der Teams für Kernbenutzerszenarien nehmen. App-Inhalte und -Interaktionen können innerhalb Teams, z. B. Bots, Karten und Aufgabenmodule, auftreten.

Sie sollten Benutzer an einer Teams und nicht mit einer externen Website oder App verknüpfen. Für Szenarien, die externe Funktionen erfordern, muss Ihre App über explizite Benutzerberechtigungen zum Starten dieser Funktionalität verfügen.

### <a name="32-compatibility"></a>3.2 Kompatibilität

Apps müssen unter den folgenden Betriebssystemen und Browsern voll funktionsfähig sein:

* Microsoft Windows 7 und höher
* macOS 10.10 und höher
* Microsoft Edge 12 und höher
* Mozilla Firefox 47.0 und höher
* Google Chrome 51.0 und höher
* iOS 9.0 und höher
* Android 4.4 und höher

### <a name="33-response-time"></a>3.3 Reaktionszeit

Teams apps must respond within a reasonable timeframe, which varies depending on the capability.

* Registerkarten müssen innerhalb von drei Sekunden reagieren oder eine Ladenachricht oder Warnung anzeigen.
* Bots müssen auf Benutzerbefehle innerhalb von zwei Sekunden reagieren oder eine Eingabeanzeige anzeigen.
* Messagingerweiterungen müssen auf Benutzerbefehle innerhalb von fünf Sekunden reagieren.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

## <a name="40-app-package-and-store-listing"></a>4.0 App-Paket- und Store-Eintrag

App-Pakete müssen ordnungsgemäß formatiert sein und alle erforderlichen Informationen und Komponenten enthalten.

### <a name="41-app-manifest"></a>4.1 App-Manifest

Das Teams-App-Manifest definiert die Konfigurationen Ihrer App.

* Ihr Manifest muss dem neuesten Manifestschema entsprechen. Weitere Informationen finden Sie im [Manifestverweis](~/resources/schema/manifest-schema.md).
* Wenn Ihre App einen Bot oder eine Messagingerweiterung enthält, muss Ihr Manifest mit Bot Framework-Metadaten, einschließlich Botname, Logo, Link zu Datenschutzrichtlinien und Nutzungsbedingungen, konsistent sein.
* Wenn Ihre App Azure Active Directory (Azure AD) für die Authentifizierung verwendet, schließen Sie die Azure AD Application (Client)-ID in das Manifest ein. Weitere Informationen finden Sie im [Manifestverweis](~/resources/schema/manifest-schema.md#webapplicationinfo).

### <a name="42-app-icons"></a>4.2 App-Symbole

Symbole sind eines der Wichtigsten Elemente, die personen beim Durchsuchen des Teams sehen. Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig die folgenden Anforderungen erfüllen:

* Ihr App-Paket muss zwei PNG-Versionen Ihres App-Symbols enthalten: ein Farbsymbol und ein Gliederungssymbol.
* Die Farbversion Des Symbols wird in den meisten Teams angezeigt und muss 192 x 192 Pixel groß sein. Ihr Symbol (96 x 96 Pixel) kann eine beliebige Farbe oder Farbe sein, muss jedoch auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund stehen.
* Die Gliederungsversion Ihres Symbols wird angezeigt, wenn Ihre App verwendet wird und auf der linken Seite von Teams auf der App-Leiste "gehisset" wird und wenn ein Benutzer die Messagingerweiterung Ihrer App anheftet. Er muss 32 x 32 Pixel groß sein und kann weiß mit einem transparenten Hintergrund oder transparent mit weißem Hintergrund sein (keine anderen Farben sind zulässig). Das Symbol sollte keinen zusätzlichen Abstand um das Symbol haben.
* Symbole mit ordnungsgemäßer Größe und formatierung müssen in Ihrem App-Paket enthalten sein. Die Symbole müssen auch mit den übermittelten Metadaten des Speichereintrags übereinstimmen.

Weitere Informationen, bewährte Methoden und Beispiele finden Sie in den Richtlinien Teams [App-Symbolen](~/concepts/build-and-test/apps-package.md#app-icons).

### <a name="43-app-descriptions"></a>4.3 App-Beschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben. Die Beschreibungen in Ihren App-Konfigurationen und im Partner Center müssen identisch sein.

Beschreibungen sollten keine andere Marke (im Besitz von Microsoft oder anderweitig) direkt oder durch Insinuation verfeinern. Stellen Sie sicher, dass Ihre Beschreibung keine Ansprüche enthält, die nicht konkretisiert werden können (z. B. "Garantierte Effizienzsteigerung von 200 Prozent").

#### <a name="431-short-description"></a>4.3.1 Kurze Beschreibung

Eine kurze Beschreibung ist eine kurze Zusammenfassung Ihrer App, die ihre Wertversprechen hervorhebt und sich an Ihre Zielgruppe richtet.

**Dos:**

* Behalten Sie die kurz beschriebene Beschreibung auf einen Satz bei.
* Die wichtigsten Informationen kommen an erster Stelle.
* Schließen Sie Schlüsselwörter ein, nach deren Suche Kunden wahrscheinlich suchen.

**Don’ts:**

* Wiederholen Sie Ihren App-Namen.
* Verwenden Sie die **Wort-App** in der kurzen Beschreibung.

#### <a name="432-long-description"></a>4.3.2 Lange Beschreibung

Die lange Beschreibung kann ein ansprechendes Narrativ bieten, das die Wertversprechen Ihrer App, die primäre Zielgruppe und die Zielbranche hervorhebt. Während diese Beschreibung bis zu 4.000 Zeichen umfassen kann, lesen die meisten Benutzer nur zwischen 300 und 500 Wörter.

**Dos:**

* Verwenden [Sie Markdown,](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) um Ihre Beschreibung zu formatieren.
* Verwenden Sie aktive Stimme, und sprechen Sie direkt mit Benutzern (z. B. *Sie können ...*).
* Auflisten von Features mit Aufzählungspunkten, damit die Beschreibung leichter gescannt werden kann.
* Beschreiben Sie die Einschränkungen, Bedingungen oder Ausnahmen der funktionalität, features und deliverables, die im Eintrag und den zugehörigen Materialien beschrieben sind, bevor der Benutzer Ihre App installiert. Die Teams, die Ihre App unterstützt, müssen sich auf die Kernfunktionen beziehen, die in Ihrem Eintrag beschrieben werden.
* Fügen Sie einen Hilfe- oder Supportlink ein.
* Verweisen Sie **auf Microsoft 365** anstatt **Office 365**.
* Wenn Sie auf Teams **verweisen** müssen, schreiben Sie den ersten Verweis als **Microsoft Teams**. Nachfolgende Verweise können auf **"Teams" verkürzt Teams.**
* Verwenden Sie die folgende Sprache, wenn Sie beschreiben, wie die App mit Teams (oder Microsoft 365):
  * "... funktioniert mit Microsoft Teams."
  * "... Arbeiten mit Microsoft Teams."
  * "... innerhalb Microsoft Teams."
  * "... für Microsoft Teams."

**Don’ts:**

* Mehr als 500 Wörter.
* Abkürzen von **Microsoft** als **MS** oder **MSFT**.
* Geben Sie an, dass die App ein Angebot von Microsoft ist, einschließlich der Verwendung von Microsoft-Parolen oder -Taglines.
* Verwenden Sie urheberrechtlich geschützte Markennamen, die Sie nicht besitzen.
* Schließen Sie Tippfehler, grammatikalische Fehler und unnötige Groß- und Großbuchstaben ein (z. B. **Benutzer** anstelle von **Benutzern**).
* Fügen Sie Links zu AppSource ein.
* Verwenden Sie die folgende Sprache, es sei denn, Sie sind ein zertifizierter Microsoft-Partner:
  * "... integriert in Microsoft Teams"
  * "... integriert sich in ..."
  * "... built for ..."
  * "... built on ..."
  * "... wird auf ..." ausgeführt.
  * "... aktiviert von ..."
  * "... zertifiziert für ..."
  * "... entwickelt für ..."
  * "... entwickelt für ..."

### <a name="44-screenshots"></a>4.4 Screenshots

Screenshots bieten eine prominente visuelle Vorschau Ihrer App, um Ihren App-Namen, Ihr Symbol und Ihre Beschreibungen zu ergänzen. Beachten Sie Folgendes zu Screenshots:

* Sie können bis zu fünf Screenshots pro Eintrag haben.
* Unterstützte Dateitypen sind PNG, JPEG und GIF.
* Die Abmessungen sollten 1366 x 768 Pixel betragen.
* Maximale Größe von 1.024 KB.

**Dos:**

* Konzentrieren Sie sich auf die Funktionen Ihrer App (z. B. wie Personen mit Ihrem Bot kommunizieren können).
* Fügen Sie Inhalte ein, die Ihre App genau darstellt.
* Verwenden Sie Text mit Bedacht.
* Frame screenshots with a color that reflects your brand and include marketing content, similar to the [Freshdesk listing](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) example (dimensions requirements apply to the whole image and not just the screenshot).

**Don’ts:**

* Zeigen Sie bestimmte Geräte an, z. B. Smartphones oder Laptops.
* Zeigt Chrom oder Benutzeroberfläche an, die sich nicht in Ihrer App befindet.
* Capture any Teams or browser UI in your screenshots.
* Fügen Sie Mockups ein, die die tatsächliche Benutzeroberfläche Ihrer App ungenau widerspiegeln, z. B. anzeigen, dass Ihre App außerhalb von Teams.

> [!TIP]
> Ein Video kann die effektivste Möglichkeit sein, um zu kommunizieren, warum Personen Ihre App verwenden sollten. Ein Video ist auch das erste, was Benutzern in Ihrem Eintrag angezeigt wird (standardmäßig wird ein Video vor Screenshots angezeigt). Weitere Informationen finden Sie unter [Erstellen eines Videos für Ihren Storeeintrag](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

### <a name="45-privacy-policy"></a>4.5 Datenschutzrichtlinien

Die Datenschutzrichtlinie kann spezifisch für Ihre Teams oder eine allgemeine Richtlinie für alle Ihre Dienste sein.

* Wenn Sie eine generische Datenschutzrichtlinienvorlage verwenden, müssen  Sie auf **Dienste,** Anwendungen und Plattformen verweisen, um Ihre Teams und Ihren Dienst oder Ihre Website zu verwenden.
* Muss die Art und Weise enthalten, wie Sie mit der Speicherung, Aufbewahrung und Löschung von Benutzerdaten umgehen. Sie müssen auch die Sicherheitssteuerelemente beschreiben, die Sie für den Datenschutz verwenden.
* Muss Ihre Kontaktinformationen enthalten.
* Sollte keine urLs enthalten, die beschädigt sind, oder für Beta- oder Stagingzwecke.
* Darf keine Links zu AppSource enthalten.

### <a name="46-terms-of-use"></a>4.6 Nutzungsbedingungen

Ihre Nutzungsbedingungen sollten spezifisch sein und auf Ihr Angebot anwendbar sein.

### <a name="47-support-links"></a>4.7 Supportlinks

Die Support-URLs Ihrer App sollten keine Authentifizierung erfordern. Benutzer sollten sich beispielsweise nicht anmelden müssen, um Sich mit Ihnen in Verbindung zu setzen.

### <a name="48-localization"></a>4.8 Lokalisierung

Wenn Ihre App die Lokalisierung unterstützt, muss Ihr App-Paket eine Datei mit Sprachübersetzungen enthalten, die basierend auf der Teams angezeigt werden. Die Datei muss dem Lokalisierungsschema Teams entsprechen. Weitere Informationen finden Sie im [Teams Lokalisierungsschema](~/concepts/build-and-test/apps-localization.md)

## <a name="50-tabs"></a>5.0 Registerkarten

Wenn Ihre App eine Registerkarte enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App finden Sie in den [Richtlinien Teams Registerkartenentwurf .](~/tabs/design/tabs.md)

### <a name="51-setup"></a>5.1 Setup

* Das Einrichten von Registerkarten darf für einen neuen Benutzer keine Sackgasse sein. Geben Sie eine Meldung zum Abschließen der Aktion oder des Workflows an.
* Die Authentifizierung sollte während der Registerkarteneinrichtung und nicht danach geschehen.

### <a name="52-views"></a>5.2 Ansichten

* Der Anmeldebildschirmbereich darf keine großen Logos verwenden oder eine ganze Webseite anzeigen.
* Inhalte können vereinfacht werden, indem sie auf mehrere Registerkarten verteilt werden.
* Registerkarten sollten keinen doppelten Header haben. Entfernen Sie das Logo aus dem iframe, da das Registerkartenframework bereits das App-Symbol und den Namen anzeigt.

### <a name="53-navigation"></a>5.3 Navigation

* Registerkarten dürfen nicht mehr als drei Navigationsebenen haben.
* Registerkarten dürfen keine Navigation bereitstellen, die im Konflikt mit der primären Teams steht.
* Die sekundären und tertiären Seiten in einer Registerkarte müssen in einer Ansicht der Ebene 2 und ebene 3 im Hauptregisterkartenbereich geöffnet werden, die über Breadcrumbs oder das linke Navigationsfenster navigiert wird. Sie können auch die folgenden Komponenten zur Unterstützung der Registerkartennavigation hinzufügen:
    * Schaltflächen zurück
    * Seitenkopfzeilen
    * Hamburger Menüs
* Tab sollte keinen horizontalen Bildlauf haben.
* Tiefe Links in Registerkarten dürfen nicht mit einer externen Webseite verknüpft werden, sondern Teams (z. B. Aufgabenmodule oder andere Registerkarten).
* Registerkarten sollten Benutzern nicht erlauben, außerhalb der Teams für die Haupt-App-Erfahrung zu navigieren.

### <a name="54-usability"></a>5.4 Verwendbarkeit

* Registerkarten müssen über das Hosten einer vorhandenen Website hinaus einen Mehrwert bieten.
* Benutzer müssen in der Lage sein, ihre letzte Aktion auf der Registerkarte rückgängig zu machen.
* Registerkarten in einem persönlichen Kontext können Inhalte aus freigegebenen Instanzen der App aggregieren.
* Registerkarten müssen auf die Teams reagieren. Wenn ein Benutzer das Design ändert, muss das Design der App die Auswahl widerspiegeln.
* Registerkarten müssen Teams-Stil-Komponenten (übernehmen Teams Schriftarten, Typ rampen, Farbpaletten, Rastersystem, Bewegung, Ton der Stimme usw.) verwenden, wann immer möglich.
* Sie müssen eine Registerkarte **Einstellungen** hinzufügen.
* Registerkarten müssen Teams Interaktionsentwurf (Seitennavigation, Position und Verwendung von Dialogen, Informationshierarchien usw.) nach Möglichkeit folgen.
* Registerkarteninhalte im iframe dürfen keine Features enthalten, die Teams funktionen imitieren (z. B. Bots, Messagingerweiterungen, Anrufe, Besprechungen usw.).

> [!TIP]
>
> * Fügen Sie neben einer persönlichen Registerkarte einen persönlichen Bot ein.
> * Zulassen, dass Benutzer Inhalte auf ihrer persönlichen Registerkarte freigeben.

## <a name="60-bots"></a>6.0 Bots

Wenn Ihre App einen Bot enthält, stellen Sie sicher, dass sie diese Richtlinien befolgt.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App finden Sie in den [Teams bot design guidelines](~/bots/design/bots.md).

### <a name="61-bot-commands"></a>6.1 Bot-Befehle

Das Analysieren von Benutzereingaben und die Vorhersage von Benutzerabsichten ist schwierig. Botbefehle bieten Benutzern eine Reihe von Wörtern oder Ausdrücken, die Ihr Bot versteht, damit sie (und Ihr Bot) nicht erraten müssen.

* Das Auflisten unterstützter Botbefehle in Ihren App-Konfigurationen wird dringend empfohlen. Diese Befehle werden im Verfassenfeld angezeigt, wenn ein Benutzer versucht, den Bot zu senden.
* Alle Befehle, die ihr Bot unterstützt, müssen ordnungsgemäß ausgeführt werden, einschließlich des Befehls **Hi,** **Hello** und **Hilfe.**

> [!TIP]
> Fügen Sie für persönliche Bots eine **Registerkarte Hilfe** ein, auf der weiter beschrieben wird, was Ihr Bot tun kann.

### <a name="62-bot-welcome-messages"></a>6.2 Bot-Willkommensnachrichten

* Bots sollten während der ersten Ausführung fast immer eine Willkommensnachricht senden. Für eine optimale Erfahrung sollte die Nachricht den Wertversprechen Ihres Bots enthalten, wie Sie den Bot konfigurieren und kurz alle unterstützten Botbefehle beschreiben. Sie können die Nachricht mithilfe einer adaptiven Karte mit Schaltflächen anzeigen, um eine bessere Benutzerfreundlichkeit zu gewährleisten. Weitere Informationen finden Sie unter [Auslösen einer Bot-Willkommensnachricht](~/bots/how-to/conversations/send-proactive-messages.md).
* Bot-Willkommensnachrichten in Kanälen und Chats sind während der ersten Ausführung optional, insbesondere wenn der Bot für den persönlichen Gebrauch verfügbar ist und ähnliche Aktionen ausführt. Wenn Ihr Bot Willkommensnachrichten sendet, darf er diese nicht einzeln an Benutzer senden (dies wird als [Spamming betrachtet).](#63-bot-message-spamming) In der Nachricht sollte auch die Person erwähnt werden, die den Bot hinzugefügt hat.
* Nur-Benachrichtigungsbots müssen eine Willkommensnachricht senden, die an die Nachrichten der Benutzer sendet.

> [!TIP]
> In Willkommensnachrichten an einzelne Benutzer kann eine Karusselltour einen effektiven Überblick über Ihren Bot und alle anderen App-Features bieten. Das Verwenden von Schaltflächen, mit denen Benutzer Bot-Befehle ausprobieren können, wird empfohlen (z. B. **Erstellen einer Aufgabe**).

### <a name="63-bot-message-spamming"></a>6.3 Spamming von Botnachrichten

Bots dürfen Benutzer nicht spamen, indem sie mehrere Nachrichten in kurzer Folge senden.

* **Botnachrichten in Kanälen und Chats:** Spamen Sie Benutzer nicht, indem Sie separate Beiträge erstellen. Erstellen Sie einen einzelnen Beitrag mit Antworten im gleichen Thread.
* **Botnachrichten in persönlichen Apps:** Senden Sie nicht mehrere Nachrichten in schneller Folge. Senden Sie eine Nachricht mit vollständigen Informationen. Vermeiden Sie Multi-Turn-Unterhaltungen, um einen einzelnen Workflow zu erstellen. Erwägen Sie stattdessen die Verwendung eines Formulars (oder Aufgabenmoduls), um alle Eingaben eines Benutzers gleichzeitig zu erfassen.
* **Willkommensnachrichten**: Das Wiederholen derselben Willkommensnachricht in regelmäßigen Abständen ist nicht zulässig und wird als Spamming betrachtet. Wenn beispielsweise einem Team ein neues Mitglied hinzugefügt wird, spamen Sie die anderen Mitglieder nicht mit einer Willkommensnachricht. Senden Sie stattdessen eine persönliche Nachricht an das neue Mitglied.

### <a name="64-bot-notifications"></a>6.4 Bot-Benachrichtigungen

Botbenachrichtigungen müssen Inhalte enthalten, die für den bereich relevant sind, den Sie für den Bot definieren (Team, Chat oder persönlich).

### <a name="65-bots-and-adaptive-cards"></a>6.5 Bots und adaptive Karten

Adaptive Karten sind eine dringend empfohlene Methode zum Anzeigen von Botnachrichten. Ihre Karten müssen leicht sein und nur 1 bis 3 Aktionen enthalten. Wenn Sie weitere Inhalte anzeigen müssen, erwägen Sie die Verwendung eines Aufgabenmoduls oder einer Registerkarte.

Weitere Informationen finden Sie in den folgenden Ressourcen:

* [Entwerfen Adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Karten-Referenz](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## <a name="70-messaging-extensions"></a>7.0 Messaging-Erweiterungen

Wenn Ihre App eine Messagingerweiterung enthält, stellen Sie sicher, dass sie diese Richtlinien befolgt.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App finden Sie in den Teams Richtlinien zum Entwerfen [von Messagingerweiterungen.](~/messaging-extensions/design/messaging-extension-design.md)

### <a name="71-action-commands"></a>7.1 Aktionsbefehle

Aktionsbasierte Messagingerweiterungen sollten folgendes tun:

* Zulassen, dass Benutzer Aktionen für eine Nachricht auslösen, ohne Zwischenschritte wie die Anmeldung ausführen zu müssen.
* Übergeben Sie den Nachrichtenkontext an den nächsten Arbeitsstatus.

### <a name="72-preview-links-link-unfurling"></a>7.2 Vorschaulinks (Link nicht mehr verfügbar)

Messagingerweiterungen sollten eine Vorschau der erkannten Links im Teams anzeigen. Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden (absolute URLs oder Platzhalter). Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` ungültig. Domänen auf oberster Ebene sind ebenfalls verboten (z. B. `*.com` oder `*.org` ).

### <a name="73-search-commands"></a>7.3 Suchbefehle

* Suchbasierte Messagingerweiterungen müssen Text bereitstellen, der Benutzern bei der effektiven Suche hilft.
* @mention ausführbare Dateien müssen klar, leicht verständlich und lesbar sein.

## <a name="80-task-modules"></a>8.0 Aufgabenmodule

Ein Aufgabenmodul muss ein Symbol und den kurzen Namen der App enthalten, der es zugeordnet ist.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App finden Sie in den [Entwurfsrichtlinien Teams Aufgabenmoduls.](~/task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="90-meeting-extensions"></a>9.0 Besprechungserweiterungen

Wenn Ihre App eine Besprechungserweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Informationen zum Erstellen einer qualitativ hochwertigen App finden Sie unter Teams Designrichtlinien für [Besprechungserweiterungen](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

### <a name="91-pre--and-post-meeting-experience"></a>9.1 Vor- und Nachbetreff

* Bildschirme vor und nach der Besprechung müssen den allgemeinen Richtlinien für den Registerkartenentwurf entsprechen. Weitere Informationen finden Sie unter [Teams Entwurfsrichtlinien](~/tabs/design/tabs.md).
* Registerkarten dürfen keinen horizontalen Bildlauf haben.
* Registerkarten sollten ein organisiertes Layout haben, wenn mehrere Elemente angezeigt werden (z. B. mehr als 10 Umfragen oder Umfragen). Sehen Sie sich ein [Beispiellayout an.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting)
* Ihre App muss Benutzer benachrichtigen, wenn die Ergebnisse einer Umfrage oder Umfrage exportiert werden, indem sie "Ergebnisse erfolgreich heruntergeladen" angeben.

### <a name="92-in-meeting-experience"></a>9.2 Besprechungserfahrung

* Apps dürfen nur in Besprechungen ein dunkles Design verwenden. Weitere Informationen finden Sie unter [Teams Entwurfsrichtlinien](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming).
* Eine QuickInfo sollte den App-Namen anzeigen, wenn sie während Besprechungen über das App-Symbol zeigt.
* Messagingerweiterungen müssen in Besprechungen genauso funktionieren wie außerhalb von Besprechungen.

### <a name="93-in-meeting-tabs"></a>9.3 Registerkarten in Besprechungen

* Muss reaktionsfähig sein. Achten Sie darauf, abstands- und komponentengrößen zu erhalten.
* Wenn mehr als eine Navigationsebene besteht, muss über eine Schaltfläche "Zurück" verfügen.
* Darf nicht mehr als eine Schaltfläche zum Schließen oder Schließen enthalten. Dies kann Benutzer verwirren, da bereits eine integrierte Kopfzeilenschaltfläche vorhanden ist, um die Registerkarte zu schließen.
* Darf keinen horizontalen Bildlauf haben.

### <a name="94-in-meeting-dialogs"></a>9.4 Dialoge in Besprechungen

* Sollte sparsam und für Szenarien verwendet werden, die leicht und aufgabenorientiert sind.
* Muss Inhalte in einer einzelnen Spalte anzeigen und nicht über mehrere Navigationsebenen verfügen.
* Aufgabenmodule dürfen nicht verwendet werden.
* Muss sich am Mittelpunkt der Besprechungsphase ausrichten.
* Sollte verworfen werden, sobald ein Benutzer eine Schaltfläche auswählt oder eine Aktion ausführt.

## <a name="100-notifications"></a>10.0 Benachrichtigungen

Wenn Ihre App die von Microsoft Graph bereitgestellten [Aktivitätsfeed-APIs](https://docs.microsoft.com/graph/teams-send-activityfeednotifications)verwendet, achten Sie darauf, dass die folgenden Richtlinien eingehalten werden.

### <a name="101-general"></a>10.1 Allgemein

* Alle in Ihren App-Konfigurationen angegebenen Benachrichtigungsauslöser sollten eine Benachrichtigung in der App erhalten.
* Benachrichtigungen müssen in den unterstützten Sprachen lokalisiert werden, die für Ihre App konfiguriert sind.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

### <a name="102-avatars"></a>10.2 Avatare

* Der Benachrichtigungs-Avatar sollte mit dem Farbsymbol Ihrer App übereinstimmen.
* Von einem Benutzer ausgelöste Benachrichtigungen sollten den Avatar des Benutzers enthalten.

### <a name="103-spamming"></a>10.3 Spamming

* Apps dürfen nicht mehr als 10 Benachrichtigungen pro Minute an einen Benutzer senden.
* Bots und der Aktivitätsfeed sollten keine doppelten Benachrichtigungen auslösen.
* Benachrichtigungen müssen benutzern einen bestimmten Wert bieten und nicht für triviale oder irrelevante Ereignisse verwendet werden.

### <a name="104-navigation-and-layout"></a>10.4 Navigation und Layout

* Benachrichtigungen müssen sich an das Teams-Feedlayout und -erfahrung halten.
* Beim Auswählen einer Benachrichtigung muss der Benutzer innerhalb eines Teams zu relevanten Inhalten geleitet und nicht aus der Teams werden.

## <a name="110-advertising"></a>11.0 Werbung

Apps dürfen keine Werbung anzeigen, einschließlich dynamischer Anzeigen, Banneranzeigen und Anzeigen in Nachrichten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines Partner Center-Kontos](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
