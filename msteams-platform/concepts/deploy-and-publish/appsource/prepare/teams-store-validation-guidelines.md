---
title: Richtlinien zur Validierung von Microsoft Teams-Speichern
description: In diesem Artikel finden Sie die Richtlinien, denen jede an den Teams Store (AppSource) übermittelte App folgen muss.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: c351214e019b0f794e4f279f69458da6adbf6dce
ms.sourcegitcommit: 06fdb41c124f82ea1b66181485339cb200ea7162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2022
ms.locfileid: "66962475"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Richtlinien zur Validierung von Microsoft Teams-Speichern

Wenn Sie diese Richtlinien befolgen, erhöht sich die Wahrscheinlichkeit, dass Ihre App den Einreichungsprozess im Microsoft Teams Store besteht. Die Teams-spezifischen Richtlinien ergänzen die Zertifizierungsrichtlinien für den [kommerziellen Microsoft-Marketplace](/legal/marketplace/certification-policies#1140-teams) und werden regelmäßig aktualisiert, um neue Funktionen, Benutzerfeedback und Änderungen der Geschäftsregeln zu berücksichtigen.

> [!NOTE]
>
> * Einige Richtlinien gelten möglicherweise nicht für Ihre App. Wenn Ihre App beispielsweise keinen Bot enthält, können Sie botbezogene Richtlinien ignorieren.
> * Wir haben diese Richtlinien mit Querverweisen auf die kommerziellen Zertifizierungsrichtlinien von Microsoft versehen und Do's und Don'ts mit Beispielen für erfolgreiche oder nicht erfolgreiche Szenarien in unserem Validierungsprozess hinzugefügt.
> * Bestimmte Richtlinien sind als *obligatorische Korrektur* gekennzeichnet. Wenn Ihre App-Einreichung diese obligatorischen Richtlinien nicht erfüllt, erhalten Sie von uns einen Fehlerbericht mit Maßnahmen zur Behebung des Problems. Ihre App-Einreichung wird die Microsoft Teams Store-Validierung erst bestehen, nachdem Sie die Probleme behoben haben.
> * Andere Richtlinien sind als *vorgeschlagene Korrektur* markiert. Für ein optimales Nutzererlebnis empfehlen wir Ihnen, die Probleme zu beheben. Ihre App wird jedoch nicht für die Veröffentlichung im Teams Store gesperrt, wenn Sie die Probleme nicht beheben.

:::row:::
   :::column:::
      :::image type="content" source="../../../../assets/icons/value-proposition.png" alt-text="value-proposition-teams" link="#value-proposition":::
   :::column-end:::
   :::column span="":::
     :::image type="content" source="../../../../assets/icons/security.png" alt-text="security-store" link="#security":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/function.png" alt-text="functionality" link="#general-functionality-and-performance":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/package.png" alt-text="app-package" link="#app-package-and-store-listing":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/saas-offer.PNG" alt-text="saas" link="#apps-linked-to-saas-offer":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/tab.png" alt-text="tab-teams" link="#tabs":::
   :::column-end:::
   :::column:::
      :::image type="content" source="../../../../assets/icons/bot.png" alt-text="bot-teams" link="#bots-1":::
   :::column-end:::
   :::column span="":::
     :::image type="content" source="../../../../assets/icons/messaging-extension.png" alt-text="messaging" link="#message-extensions":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/task-module.png" alt-text="task-module-teams" link="#task-modules":::
   :::column-end:::
     :::column span="":::
      :::image type="content" source="../../../../assets/icons/meeting.png" alt-text="meeting-extension" link="#meeting-extensions":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/empty.png" alt-text="empty-2":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/notifications.png" alt-text="teams-notification" link="#notifications":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/microsoft-365.png" alt-text="microsoft" link="#microsoft-365-app-compliance-program":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/advertising.png" alt-text="advertising-teams" link="#advertising":::
   :::column-end:::
   :::column span="":::
      :::image type="content" source="../../../../assets/icons/empty.png" alt-text="empty-1":::
   :::column-end:::
:::row-end:::

## <a name="value-proposition"></a>Wertbeitrag 

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der kommerziellen Zertifizierungsrichtlinie von Microsoft Nr. 1140.1](/legal/marketplace/certification-policies#11401-value-proposition-and-offer-requirements) und bietet Entwicklern von Microsoft Teams-Apps zusätzliche Anleitungen zum Wertversprechen ihres Angebots.

### <a name="app-name"></a>App-Name

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit der Microsoft[-Zertifizierungsrichtlinie Nr. 1140.1.1](/legal/marketplace/certification-policies#114011-app-name) und bietet Entwicklern zusätzliche Hinweise zur Benennung ihrer Anwendungen.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Der Name einer App spielt eine entscheidende Rolle dafür, wie Benutzer sie im Store entdecken. Verwenden Sie die folgenden Richtlinien, um eine App zu benennen:

* Der Name muss für Ihre Benutzer relevante Begriffe enthalten.
* Namen der wichtigsten Teams-Features dürfen nicht in Ihrem App-Namen enthalten sein, z. B.:  
  * **Chat**
  * **Kontakte**
  * **Calendar**
  * **Aufrufe**
  * **Files**
  * **Aktivität**
  * **Apps**
  * **Help**
* Präfixe oder Suffixe von allgemeinen Substantiven mit dem Namen des Entwicklers. Beispielsweise **Contoso Tasks** anstelle von **Tasks**.
* Darf **keine Teams** oder andere Microsoft-Produktnamen wie Excel, PowerPoint, Word, OneDrive, SharePoint, OneNote, Azure, Surface, Xbox usw. verwenden, was fälschlicherweise auf Co-Branding oder Co-Selling hinweisen könnte. Weitere Informationen zum Verweisen auf Microsoft-Softwareprodukte und -Dienste finden Sie unter [Microsoft-Warenzeichen- und Markenrichtlinien](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
* Wenn Ihre App Teil einer offiziellen Partnerschaft mit Microsoft ist, muss der Name Ihrer App an erster Stelle stehen. Beispiel: **Contoso Connector für Microsoft Teams**.
* Der Name einer im Store aufgeführten App oder eines anderen Angebots auf dem kommerziellen Marktplatz darf nicht kopiert werden.
* Darf keine profanen oder abfälligen Begriffe enthalten. Der Name darf auch keine rassen- oder kulturell unsensible Sprache enthalten.
* Muss eindeutig sein. Wenn Ihre App (Contoso) im Microsoft Teams Store und in Microsoft AppSource aufgeführt ist und Sie eine andere spezifische App für eine bestimmte Region wie Contoso Mexiko auflisten möchten, muss Ihre Einreichung die folgenden Kriterien erfüllen:
  * Nennen Sie die regionsspezifischen Funktionen der App in den Abschnitten Titel, Metadaten, First-Response-App-Erfahrung und Hilfe. Der Titel muss z. B. „Contoso Mexiko“ sein. Der Titel der App muss eine bestehende App desselben Entwicklers deutlich unterscheiden, um Verwechslungen beim Endnutzer zu vermeiden.
  * Wählen Sie beim Hochladen des App-Pakets im Partner Center die richtigen **Märkte** aus, in denen die App im Abschnitt **„Verfügbarkeit“** verfügbar sein wird.

 > [!TIP]  
 > Das Branding Ihrer App im Microsoft Teams Store und auf Microsoft AppSource, einschließlich Ihres App-Namens, Entwicklernamens, App-Symbols, der Microsoft AppSource-Screenshots, des Videos, der Kurzbeschreibung und der Website, darf weder einzeln noch zusammen ein offizielles Microsoft-Angebot vortäuschen, es sei denn, Ihre App ist ein offizielles Microsoft 1P-Angebot.

</details>

### <a name="suitable-for-workplace-consumption"></a>Geeignet für den Gebrauch am Arbeitsplatz

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit den kommerziellen Zertifizierungsrichtlinien von Microsoft Nr. [1140.1.2](/legal/marketplace/certification-policies#114012-workplace-appropriateness), [100.8](/legal/marketplace/certification-policies#1008-significant-value) und [100.10](/legal/marketplace/certification-policies#10010-inappropriate-content) und bietet Entwicklern zusätzliche Anleitungen für die Erstellung arbeitsplatzgerechter Anwendungen.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

App-Inhalte müssen für die allgemeine Nutzung am Arbeitsplatz geeignet sein und alle Einschränkungen einhalten, die in den Zertifizierungsrichtlinien für kommerzielle Marktplätze aufgeführt sind. Inhalte mit Bezug zu Religion, Politik, Glücksspielen und längerer Unterhaltung sind verboten.

Ihre Anwendung muss die Zusammenarbeit in der Gruppe ermöglichen, die Produktivität des Einzelnen verbessern oder beides. Apps, die für Teambindung und soziale Kontakte gedacht sind, müssen kollaborativ sein und für mehrere Teilnehmer konzipiert sein. Die Anwendungen dürfen weder einen erheblichen Zeitaufwand von mehr als 60 Minuten pro Sitzung erfordern noch die Produktivität beeinträchtigen.

</details>

### <a name="similar-platforms-and-services"></a>Ähnliche Plattformen und Dienste

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie zur kommerziellen Zertifizierung Nr. 1140.1.3](/legal/marketplace/certification-policies#114013-other-platforms-and-services).

Apps müssen sich auf die Teams-Erfahrung konzentrieren und dürfen keine Namen, Symbole oder Bilder anderer ähnlicher Chat-basierter Plattformen oder Dienste für die Zusammenarbeit im App-Inhalt oder in den App-Metadaten enthalten, es sei denn, die App bietet eine bestimmte Interoperabilität.

### <a name="feature-names"></a>Funktionsnamen

Die Namen von App-Funktionen in Schaltflächen und anderen UI-Texten dürfen sich nicht mit der Terminologie für Teams und andere Microsoft-Produkte überschneiden. Zum Beispiel, **Besprechung starten,** **Anruf tätigen** oder **Chat starten**. Fügen Sie bei Bedarf Ihren App-Namen ein, z. B. **Contoso-Besprechung starten**.

### <a name="authentication"></a>Authentifizierung

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der kommerziellen Microsoft-Zertifizierungsrichtlinie Nr. 1140.1.4](/legal/marketplace/certification-policies#114014-access-to-services) und bietet Entwicklern eine Anleitung für die Authentifizierung ihrer Anwendungen mit externen Diensten.

Weitere Informationen zum Implementieren der App-Authentifizierung finden Sie unter [Authentifizierung in Teams](~/concepts/authentication/authentication.md).
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

#### <a name="authenticating-with-external-services"></a>Authentifizieren mit externen Diensten

Wenn Ihre App Benutzer mit einem externen Dienst authentifiziert, befolgen Sie die folgenden Richtlinien:

* **Anmelde-, Abmelde- und Registrierungserfahrungen**:
  * Apps, die von externen Konten oder Diensten abhängen, müssen eine klare und einfache Anmeldung, Abmeldung und Registrierung ermöglichen.
  * Wenn sich Benutzer abmelden, müssen sie sich nur von der App abmelden und bei Teams angemeldet bleiben.
  * Apps, die von externen Konten oder Diensten abhängen, müssen eine Möglichkeit für neue Benutzer bieten, sich zu registrieren oder den App-Herausgeber zu kontaktieren, um mehr über die Dienste zu erfahren und Zugriff auf die Dienste zu erhalten.
  Der Weg dorthin muss in der Beschreibung der App, in der AppSource-Langbeschreibung und bei der ersten Ausführung der App (Bot-Begrüßungsnachricht, Registerkarteneinrichtung oder Konfigurationsseite) verfügbar sein.
  * Apps, die eine einmalige Einrichtung durch den Tenant-Administrator erfordern, müssen darauf hinweisen, dass der Tenant-Administrator die App konfigurieren muss (bevor ein anderer Tenant-Benutzer die App installieren und nutzen kann).  
  Die Abhängigkeit muss im App-Manifest, in der AppSource-Langbeschreibung, an allen Berührungspunkten beim ersten Start (Bot-Begrüßungsnachricht, Registerkarten-Einrichtung oder Konfigurationsseite), im Hilfetext, der als Teil der Bot-Antwort für notwendig erachtet wird, in der Compose-Erweiterung oder im statischen Registerkarteninhalt angegeben werden.
  
* **Erfahrungen beim Teilen von Inhalten**: Apps, die für die Freigabe von Inhalten in Teams-Kanälen eine Authentifizierung bei einem externen Dienst erfordern, müssen in der Hilfedokumentation (oder ähnlichen Ressourcen) klar angeben, wie die Verbindung zu Inhalten getrennt oder die Freigabe aufgehoben werden kann, wenn diese Funktion für den externen Dienst unterstützt wird. Dies bedeutet nicht, dass die Möglichkeit zum Aufheben der Freigabe von Inhalten in Ihrer Teams-App vorhanden sein muss.

</details>

## <a name="security"></a>Sicherheit

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie zur kommerziellen Zertifizierung Nr. 1140.3](/legal/marketplace/certification-policies#11403-security).

### <a name="financial-information"></a>Finanzinformationen

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der kommerziellen Zertifizierungsrichtlinie Nr. 1140.3.1](/legal/marketplace/certification-policies#114031-financial-transactions) von Microsoft und bietet eine Anleitung zur Übermittlung von Finanzinformationen innerhalb der Teams-Schnittstelle und informiert Entwickler über eingeschränkte Zahlungsszenarien in der mobilen Version (Android und iOS) ihrer Teams-App.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Apps dürfen Benutzer nicht auffordern, Zahlungen innerhalb der Teams-Benutzeroberfläche zu tätigen und Finanzinformationen über eine Bot-Schnittstelle an Benutzer zu übermitteln.

:::image type="content" source="../../../../assets/images/submission/validation-financial-information-1.png" alt-text="validation-financial-info":::

Sie können nur dann einen Link zu sicheren externen Zahlungsdiensten bereitstellen, wenn Sie dies in Ihren Nutzungsbedingungen, Datenschutzrichtlinien, auf Ihrer Profilseite oder auf Ihrer Website bekannt geben, bevor der Nutzer der Nutzung der App zustimmt.

Erleichtern Sie nicht Zahlungen über eine App für Waren oder Dienstleistungen, die gemäß [der allgemeinen Richtlinie Nr. 100.10 „Unzulässige Inhalte“](/legal/marketplace/certification-policies#10010-inappropriate-content)verboten sind.

Apps, die auf der iOS- oder Android-Version von Teams ausgeführt werden, müssen den folgenden Richtlinien entsprechen:

* Apps dürfen keine In-App-Käufe, Testangebote oder Benutzeroberflächen enthalten, die darauf abzielen, den Nutzern kostenpflichtige Versionen oder Online-Shops zum Kauf anderer Inhalte, Apps oder Add-Ins anzubieten.

    :::image type="content" source="../../../../assets/images/submission/validation-financial-information-in-app-purchase.png" alt-text="validation-financial-info-in-app-purchase":::

    :::image type="content" source="../../../../assets/images/submission/validation-financial-information-online-stores.png" alt-text="validation-online-store":::

* Wenn Ihre App ein Konto erfordert, können sich Benutzer kostenlos für ein Konto registrieren. Die Verwendung des Begriffs **kostenlos** oder **kostenloser Account** ist untersagt.
* Sie können bestimmen, ob ein Konto unbegrenzt oder für einen begrenzten Zeitraum aktiv ist. Wenn das Konto abläuft, darf die App keine Benutzeroberfläche, keinen Text oder keine Links anzeigen, die auf die Notwendigkeit der Zahlung hinweisen.
* Die Datenschutzrichtlinien und Nutzungsbedingungen Ihrer App müssen frei von kommerziellen UI oder Links sein.

</details>

### <a name="bots"></a>Bots

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für den kommerziellen Marktplatz Nr. 1140.3.2](/legal/marketplace/certification-policies#114032-bots-and-messaging-extension).
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Bei Apps, die den Microsoft Azure Bot Service nutzen (z. B. Bots und Nachrichtenerweiterungen), müssen Sie alle in den Microsoft-[Nutzungsbedingungen für Onlinedienste](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) definierten Anforderungen erfüllen.

Bots müssen immer die Berechtigung zum Hochladen einer Datei und zum Anzeigen einer Bestätigungsmeldung anfordern.

:::image type="content" source="../../../../assets/images/submission/validation-bot-confirmation-message.png" alt-text="validation-bot-confirmation":::

</details>

### <a name="external-domains"></a>Externe Domänen

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit der [Microsoft Richtlinie Nr. 1140.3.3 für kommerzielle Marktplätze](/legal/marketplace/certification-policies#114033-external-domains) und enthält eine Anleitung für Entwickler zur Verwendung eingeschränkter Domänen in der `validDomains` Manifest-Eigenschaft.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Sie dürfen keine Domänen außerhalb der Kontrolle Ihrer Organisation (einschließlich Wildcards) und Tunnelingdienste in die Domänenkonfigurationen Ihrer App einschließen. Zu den folgenden Ausnahmen gehören:

* Wenn Ihre App die OAuthCard des Azure Bot Service verwendet, müssen Sie `token.botframework.com` als gültige Domäne angeben oder die Schaltfläche **Anmelden** funktioniert nicht.
* Wenn Ihre App auf SharePoint basiert, können Sie die zugehörige SharePoint-Stammsite mithilfe der Kontexteigenschaft `{teamSiteDomain}` als gültige Domäne einschließen.

#### <a name="government-community-cloud-listings"></a>Community Cloud-Einträge für Behörden

Um Ihre App an Government Community Cloud (GCC)-Benutzer zu vertreiben, muss der Authentifizierungsprozess die Benutzer identifizieren und an eine GCC-spezifische oder erwartete URL weiterleiten, während doppelte Einträge im Teams Store vermieden werden.

</details>

### <a name="sensitive-content"></a>Vertraulicher Inhalt

[*Obligatorischer Fix*]

Ihre App darf keine sensiblen Daten wie Kreditkarten- oder Finanzdaten, Gesundheitsdaten, Kontaktinformationen oder andere persönlich identifizierbare Informationen (PII) an ein Publikum weitergeben, das den Inhalt nicht sehen soll.

Die App muss die Benutzer warnen, bevor sie Dateien oder ausführbare Dateien (.exe) auf den Computer oder in die Umgebung des Benutzers herunterlädt.

## <a name="general-functionality-and-performance"></a>Allgemeine Funktionalität und Leistung

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4](/legal/marketplace/certification-policies#11404-functionality).

### <a name="launching-external-functionality"></a>Externe Funktionen starten

[*Obligatorischer Fix*]

Apps dürfen Benutzer für Kernbenutzerszenarien nicht aus Teams herausnehmen. App-Inhalte und -Interaktionen müssen im Rahmen von Teams-Funktionen wie Bots, adaptiven Karten, Registerkarten und Aufgabenmodulen erfolgen.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Verknüpfen Sie Benutzer innerhalb der Teams-App und nicht mit einer externen Website oder App. Für Szenarien, die externe Funktionen erfordern, muss Ihre Anwendung die ausdrückliche Erlaubnis des Benutzers einholen, um die Funktionen zu starten.

Der UI-Text für Schaltflächen, die externe Funktionen starten, muss Inhalte enthalten, die anzeigen, dass der Benutzer die Teams-Instanz verlässt. Fügen Sie z. B. Text wie **„Hier geht es zu Contoso.com“** oder **„Ansicht in Contoso.com“** ein.

</details>

### <a name="compatibility"></a>Kompatibilität

[*Obligatorischer Fix*]

Die Apps müssen auf den neuesten Versionen der folgenden Betriebssysteme und Browser voll funktionsfähig sein:

* Microsoft Windows
* macOS
* Microsoft&nbsp;Edge
* Google Chrome
* iOS
* Android

Ihre Anwendung muss bei nicht unterstützten Browsern und Betriebssystemen eine entsprechende Fehlermeldung anzeigen.

### <a name="response-time"></a>Antwortzeit

[*Obligatorischer Fix*]

Team-Apps müssen innerhalb eines angemessenen Zeitrahmens reagieren oder eine Lade- oder Eingabeanzeige, Meldung oder Warnung anzeigen.

* Registerkarten müssen innerhalb von zwei Sekunden reagieren oder eine Lademeldung oder Warnung anzeigen.
* Bots müssen innerhalb von zwei Sekunden auf Benutzerbefehle reagieren oder eine Tippanzeige anzeigen.
* Nachrichtenerweiterungen müssen innerhalb von zwei Sekunden auf Benutzerbefehle reagieren.
* Benachrichtigungen müssen innerhalb von zwei Sekunden nach der Benutzeraktion angezeigt werden.

## <a name="app-package-and-store-listing"></a>App-Paket und Store-Eintrag

[*Obligatorischer Fix*]

App-Pakete müssen korrekt formatiert sein und alle erforderlichen Informationen und Komponenten enthalten.

> [!TIP]  
> Sie müssen die folgenden detaillierten Testanweisungen für die Überprüfung Ihrer App-Einreichung beifügen:
>
> * **Schritte zum Konfigurieren der App-Testkonten** für den Fall, dass die App für die Authentifizierung auf externe Konten angewiesen ist.
> * Zusammenfassung des **erwarteten App-Verhaltens** für die wichtigsten Workflows innerhalb Teams.
> * **Beschreiben Sie Einschränkungen**, Bedingungen oder Ausnahmen der Funktionalität, Funktionen und Leistungen in der ausführlichen Beschreibung der App und den zugehörigen Materialien klar.
> * **Hervorhebung aller Überlegungen** für Tester beim Überprüfen der App-Einreichung.  
> * Füllen Sie **die Testkonten vorab mit Dummy-Daten,** um die Tests zu unterstützen.

### <a name="app-manifest"></a>App-Manifest

[*Obligatorischer Fix*]

Das Manifest der Teams-App definiert die Konfiguration Ihrer App.

* Ihr Manifest muss einem öffentlich freigegebenen Manifest-Schema entsprechen. Weitere Informationen finden Sie in den[Manifest-Hinweisen.](~/resources/schema/manifest-schema.md) Reichen Sie Ihre App nicht mit einer Vorschauversion des Manifests ein.
* Wenn Ihre App eine Bot- oder Nachrichtenerweiterung enthält, müssen die Details im App-Manifest mit den Bot Framework-Metadaten übereinstimmen, einschließlich Bot-Name, Logo, Link zur Datenschutzerklärung und Link zu den Nutzungsbedingungen.
* Wenn Ihre App Azure Active Directory für die Authentifizierung verwendet, fügen Sie die Azure Active Directory (Azure AD)-Anwendungs-(Client-)ID in das Manifest ein. Weitere Informationen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md#webapplicationinfo)

### <a name="app-icons"></a>App-Symbole

[*Obligatorischer Fix*]

Symbole sind eines der Hauptelemente, die Benutzer beim Durchsuchen des Teams-Speichers sehen.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Ihre Symbole müssen die Marke und den Zweck Ihrer App unter Einhaltung der folgenden Anforderungen kommunizieren:

* Ihr App-Paket muss zwei .png-Versionen Ihres App-Symbols enthalten: Ein Farbsymbol und ein Umrisssymbol.
* Die Farbversion Ihres Symbols muss 192 x 192 Pixel betragen. Ihr Symbol kann eine beliebige Farbe oder mehrere Farben haben, muss aber auf einem einfarbigen oder vollständig transparenten quadratischen Hintergrund stehen.
* In den folgenden Szenarien wird die Kontur-Version Ihres Symbols angezeigt:
  * Wenn Ihre App in Gebrauch ist und auf der App-Leiste auf der linken Seite von Teams **gehostet** wird.
  * Wenn ein Benutzer die Nachrichtenerweiterung Ihrer App anheftet.

* Die Kontur muss 32 x 32 Pixel groß sein und kann weiß mit transparentem Hintergrund oder transparent mit weißem Hintergrund sein. Das Symbol darf keinen zusätzlichen Abstand um es herum aufweisen.

* Ihr App-Paket muss ordnungsgemäß dimensionierte und formatierte Symbole enthalten. Die Symbole müssen mit den Informationen in den Metadaten des Store-Eintrags übereinstimmen.

Weitere Informationen finden Sie in den [Richtlinien für Symbole.](~/concepts/build-and-test/apps-package.md#app-icons)

</details>

### <a name="app-descriptions"></a>App-Beschreibungen

Sie müssen eine kurze und lange Beschreibung Ihrer App haben. Die Beschreibungen in Ihren App-Konfigurationen und im Partner Center müssen identisch sein.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Beschreibungen dürfen nicht direkt oder durch Andeutungen eine andere Marke (von Microsoft oder anderen) verunglimpfen. Stellen Sie sicher, dass Ihre Beschreibung keine Behauptungen enthält, die nicht belegt werden können. Beispielsweise **garantierte Steigerung der Effizienz um 200 Prozent**.

#### <a name="short-description"></a>Kurzbeschreibung

Eine kurze Beschreibung ist eine prägnante Zusammenfassung Ihrer App, die ihr Wertversprechen hervorhebt und sich an Ihre Zielgruppe richtet.

**Was Sie tun sollten:**

* Halten Sie die kurze Beschreibung in einem Satz.
* Die wichtigsten Informationen kommen an erster Stelle.
* Fügen Sie Schlüsselwörter hinzu, nach denen Kunden wahrscheinlich suchen.
* Nutzen Sie das verfügbare Zeichenlimit effizient. Wiederholen Sie beispielsweise nicht Ihren App-Namen.

**Don’ts:**

[*Vorgeschlagene Korrektur*]

Verwenden Sie das Wort **App** in der Kurzbeschreibung.

#### <a name="long-description"></a>Lange Beschreibung

Die lange Beschreibung kann eine ansprechende Erzählung bieten, die das Wertversprechen Ihrer App, die primäre Zielgruppe und die Zielbranche hervorhebt. Obwohl diese Beschreibung bis zu 4 000 Zeichen lang sein kann, werden die meisten Benutzer nur zwischen 300 und 500 Wörter lesen.

**Was Sie tun sollten:**

* Verwenden Sie [Markdown,](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) um Ihre Beschreibung zu formatieren.
* Verwenden Sie aktive Stimme und sprechen Sie direkt mit Benutzern. Zum Beispiel **können Sie ...**.
* Listen Sie Features mit Aufzählungspunkten auf, damit die Beschreibung einfacher durchsucht werden kann.
* Beschreiben Sie die Einschränkungen, Features, Bedingungen oder Ausnahmen für die Funktionalität sowie die Lieferleistungen in der Auflistung und den zugehörigen Materialien eindeutig, bevor der Benutzer Ihre App installiert. Die Teams-Funktionen müssen sich auf die in der Auflistung beschriebenen Kernfunktionen beziehen.
* Stellen Sie sicher, dass die App-Beschreibung mit der in der Teams-App verfügbaren Funktionalität übereinstimmt. Jeder Verweis auf Arbeitsabläufe außerhalb der Teams-App muss begrenzt sein und sich deutlich von den Funktionen der Teams-App abheben.
* Fügen Sie einen Hilfe- oder Support-Link hinzu.
* Verweisen Sie auf **Microsoft 365** anstelle von **Office 365**.
* Wenn Sie auf **Teams** verweisen müssen, schreiben Sie den ersten Verweis als **Microsoft Teams**. Spätere Verweise können auf **Teams-** verkürzt werden.
* Verwenden Sie die folgende Sprache, wenn Sie beschreiben, wie die App mit Teams (oder Microsoft 365) funktioniert:
  * **... funktioniert mit Microsoft Teams.**
  * **... mit Microsoft Teams arbeiten.**
  * **... in Microsoft Teams.**
  * **... für Microsoft Teams.**
  * **... in Microsoft Teams integriert.**
  * **... erstellt für...**
  * **... entwickelt für...**
  * **.. entwickelt für...**

**Was Sie nicht tun sollten:**

[*Obligatorischer Fix*]

* Überschreitet 500 Wörter.
* Kürzen Sie **Microsoft** als **MS** oder **MSFT**.
* Geben Sie an, dass es sich bei der App um ein Angebot von Microsoft handelt, einschließlich der Verwendung von Microsoft-Slogans oder Leitsätzen.
* Die Verwendung urheberrechtlich geschützter Markennamen, deren Eigentümer Sie nicht sind.
* Die Verwendung folgender Sprache, es sei denn, Sie sind ein zertifizierter Microsoft-Partner:
  * **... zertifiziert für ...**
  * **... unterstützt von ...**
* Tippfehler, Grammatikfehler einschließen.
* Unnötigerweise wird das gesamte Manifest oder die lange Beschreibung oder der AppSource-Inhalt groß geschrieben.
* Links zu AppSource einschließen.
* Ungeprüfte Behauptungen aufstellen. Zum Beispiel „am besten“, „Top“ und „am besten bewertet“, es sei denn, dies wird mit der Quelle des Anspruchs angegeben.
* Vergleichen Sie Ihr Angebot mit anderen Marketplace-Angeboten.

</details>

### <a name="screenshots"></a>Screenshots

Screenshots bieten eine auffällige visuelle Vorschau Ihrer App, um Ihren App-Namen, das Symbol und die Beschreibungen zu ergänzen.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Beachten Sie Folgendes:

* Sie können bis zu fünf Screenshots pro Eintrag erstellen.
* Unterstützte Dateitypen sind PNG, JPEG und GIF.
* Die Abmessungen müssen 1366 x 768 Pixel betragen.
* Maximale Größe von 1 024 KB.

**Was Sie tun sollten:**

* Konzentrieren Sie sich auf die Funktionen Ihrer App. Beispielsweise, wie Personen mit Ihrem Bot kommunizieren können.
* Fügen Sie Inhalte ein, die Ihre App genau darstellen.
* Verwenden Sie Text mit Bedacht.
* Rahmen Sie Screenshots mit einer Farbe, die Ihre Marke widerspiegelt und Marketinginhalte enthält.

**Was Sie nicht tun sollten:**

[*Vorgeschlagene Korrektur*]

* Zeigen Sie bestimmte Geräte wie Telefone oder Laptops an.
* Zeigen Sie Chrome oder eine Benutzeroberfläche an, die nicht in Ihrer App enthalten ist.
* Erfassen Sie beliebige Teams oder Browser-UI in Ihren Screenshots.
* Fügen Sie Mockups hinzu, die die tatsächliche Benutzeroberfläche Ihrer App ungenau widerspiegeln, z. B. wenn Ihre App außerhalb von Teams verwendet wird.

> [!TIP]  
> Ein Video kann die effektivste Methode sein, um zu kommunizieren, warum Benutzer Ihre App verwenden sollten. Ein Video ist auch das erste, was Benutzern in Ihrem Eintrag angezeigt wird. Weitere Informationen finden Sie unter [Video für Ihren Store-Eintrag erstellen](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

</details>

### <a name="privacy-policy"></a>Datenschutzrichtlinie

[*Obligatorischer Fix*]

Die Datenschutzrichtlinie kann für Ihre Teams-App oder eine allgemeine Richtlinie für alle Ihre Dienste spezifisch sein.

* Wenn Sie eine generische Vorlage für Datenschutzrichtlinien verwenden, müssen Sie im Rahmen Ihrer Datenschutzerklärung einen Verweis auf **Dienste**, **Anwendungen** oder **Plattformen** hinzufügen. Sie müssen Ihre Teams-App nicht in dem Rahmen angeben, wenn Sie einen Verweis auf **Dienste**, **Anwendungen** und **Plattformen** hinzufügen. Der App-Überprüfungsprozess interpretiert diese Verweise so, dass Ihre Teams-App zusammen mit Ihren anderen Diensten oder Websites einbezogen wird.
* Muss beinhalten, wie Sie mit der Speicherung, Aufbewahrung und Löschung von Benutzerdaten umgehen. Sie müssen die Sicherheitskontrollen für den Datenschutz beschreiben.
* Muss Ihre Kontaktdaten enthalten.
* Darf keine URLs enthalten, die fehlerhaft sind oder für Beta- oder für Staging-Zwecke verwendet werden.
* Darf keine Links zu AppSource enthalten.
* Für den Zugriff auf die Datenschutzrichtlinie darf keine Authentifizierung erforderlich sein.
* Darf keine kommerziellen UI- oder Shop-Links enthalten.

### <a name="terms-of-use"></a>Nutzungsbedingungen

[*Obligatorischer Fix*]

Verwenden Sie die folgenden Richtlinien, um die Nutzungsbedingungen zu schreiben:

* Muss spezifisch und auf Ihr Angebot anwendbar sein.
* Muss in Ihrer eigenen Domäne gehostet werden.
* Muss über einen sicheren Link (HTTPS) verfügen.
* Der Zugriff auf Nutzungsbedingungen darf keine Authentifizierung erfordern.

### <a name="support-links"></a>Supportlinks

[*Obligatorischer Fix*]

Die Support-URLs Ihrer App dürfen keine Authentifizierung erfordern. Benutzer dürfen sich beispielsweise nicht anmelden müssen, um Sie zu kontaktieren.
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Support-URLs müssen Ihre Kontaktdetails oder eine Möglichkeit zur Weiterleitung enthalten, damit Benutzer ein Supportticket erstellen können. Wenn Ihre Support-URL beispielsweise auf GitHub gehostet wird, muss die GitHub-Seite in Ihrem Besitz sein und Ihre Kontaktdetails oder eine Möglichkeit zur Erstellung eines Supporttickets für Benutzer enthalten.

:::image type="content" source="../../../../assets/images/submission/validation-supportlinks-authentication.png" alt-text="validation-support-links-auth":::

</details>

### <a name="localization"></a>Lokalisierung

[*Obligatorischer Fix*]

Wenn Ihre App Lokalisierung unterstützt, muss Ihr App-Paket eine Datei mit Sprachübersetzungen enthalten, die basierend auf der Spracheinstellung von Teams angezeigt werden. Die Datei muss dem Lokalisierungsschema von Teams entsprechen. Weitere Informationen finden Sie unter [Teams-Lokalisierungsschema](~/concepts/build-and-test/apps-localization.md).

## <a name="apps-linked-to-saas-offer"></a>Apps, die mit dem SaaS-Angebot verknüpft sind

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für den kommerziellen Marktplatz Nr. 1140.5](/legal/marketplace/certification-policies?branch=pr-en-us-5673). Wenn Sie eine Teams-App erstellen, die mit einem SaaS-Angebot verknüpft ist, stellen Sie sicher, dass diese Richtlinien eingehalten werden.
<br></br>
<details><summary>Allgemein</summary>

* ISVs müssen die Möglichkeit unterstützen, dass mehrere Benutzer (Abonnenten) im selben Tenant ihr eigenes Abonnement verwalten und den Benutzern im Tenant Lizenzen zuweisen können.
* Das Angebot muss alle [technischen Anforderungen](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/include-saas-offer) für Teams-Apps erfüllen, die mit einem SaaS-Angebot verknüpft sind.
* Die mit dem SaaS-Angebot verbundenen Teams-Apps müssen alle in [1000 Software-As-A-Service (SaaS)](/legal/marketplace/certification-policies#1000-software-as-a-service-saas)definierten Anforderungen erfüllen.
* `subscriptionOffer` die in der Manifest-Datei erwähnten Details müssen korrekt sein. Fügen Sie in Ihrem App-Manifest den Knoten `subscriptionOffer` mit dem Wert `publisherId.offerId`hinzu oder aktualisieren Sie ihn. Wenn Ihre Herausgeber-ID beispielsweise `contoso1234` und Ihre Angebots-ID `offer01`ist, muss der Wert, den Sie in Ihrem App-Manifest angeben, `contoso1234.offer01`lauten.
* Das mit der Teams-App verknüpfte SaaS-Angebot muss in AppSource live sein, und Vorschau-Angebote werden nicht zur Genehmigung im Store akzeptiert.

</details>

</br>
<details><summary>Angebotsmetadaten</summary>

* Die Angebotsmetadaten müssen im Teams-Manifest, in der Auflistung der Teams-App in AppSource und im SaaS-Angebot in AppSource übereinstimmen.
* Teams-App und SaaS-Angebot müssen vom selben Herausgeber oder Entwickler stammen. Das SaaS-Angebot, auf das im App-Manifest verwiesen wird, muss demselben Herausgeber gehören wie die Teams-App, die auf dem kommerziellen Marktplatz eingereicht wird.
* Da es sich bei Ihrem eingereichten Angebot um eine Teams-App handelt, die mit einem SaaS-Angebot verknüpft ist, müssen Sie die Option **Zusätzliche Käufe** als **Ja, mein Produkt erfordert den Kauf eines Dienstes oder bietet zusätzliche In-App-Käufe** im Produkt-Setup-Abschnitt des Partner-Centers in Ihrer Angebotsauflistung auswählen.
* Plan-Beschreibungen und Preisdetails müssen genügend Informationen für Benutzer bereitstellen, um die Angebotsauflistungen klar zu verstehen.
* Alle Einschränkungen, Abhängigkeiten von Zusatzleistungen und Ausnahmen von den angebotenen Leistungen müssen in der Beschreibung des Plans genau angegeben werden.
* Die Teams-Apps, die mit dem SaaS-Angebot verknüpft sind, sind so konzipiert, dass sie Lizenzen unterstützen, die pro Benutzer zugewiesen werden. Manchmal ist das SaaS-Angebot mit anderen Methoden aufgebaut oder hat spezielle Kaufabläufe. Sie müssen in den Metadaten der App und in den Details des Abonnementplans deutlich auf die Methode und die Kaufabläufe hinweisen.
* Das SaaS-Angebot muss allen Nutzern in allen Phasen des Kaufprozesses Nachrichten und Anleitungen bereitstellen.

</details>
</br>

<details><summary>Startseite und Lizenzverwaltung für SaaS-Angebote</summary>

* Stellen Sie Abonnenten eine Einführung in die Verwendung des Produkts bereit.
* Zulassen, dass der Abonnent Lizenzen zuweist.
* Stellen Sie verschiedene Möglichkeiten bereit, sich bei Problemen an den Support zu wenden, z. B. FAQ, Wissensdatenbank und E-Mail-Adresse.
* Überprüfen Sie die Benutzer, um sicherzustellen, dass ihnen nicht bereits eine Lizenz durch einen anderen Benutzer zugewiesen wurde.
* Benutzer nach der Lizenzzuweisung benachrichtigen.
* Führen Sie die Benutzer über den Teams-Chatbot oder per E-Mail durch die Hinzufügung der App zu Teams und die ersten Schritte.

</details>
</br>

<details><summary>Benutzerfreundlichkeit und Funktionalität</summary>

* Nach dem erfolgreichen Kauf und der Zuweisung von Lizenzen müssen Sie Folgendes angeben:
* Zugang zu Nutzern für abonnierte Plan-Features.
* Zusätzlicher Nutzen und bedeutende Vorteile des Abonnements für die Nutzer.
* Stellen Sie in Ihrer Teams-App einen Link zur Startseite der SaaS-Anwendung bereit, auf der Abonnenten die Lizenzen in Zukunft verwalten können.

</details>
</br>

<details><summary>Konfigurieren und Testen der SaaS-Anwendung</summary>

Wenn die Einrichtung Ihrer Anwendung zu Testzwecken komplex ist, stellen Sie ein durchgängiges Funktionsdokument, verknüpfte Konfigurationsschritte für das SaaS-Angebot und Anweisungen für die Lizenz- und Benutzerverwaltung als Teil Ihrer „Hinweise zur Zertifizierung“ zur Verfügung.

> [!TIP]  
> Sie können ein Video zur Funktionsweise Ihrer App und Lizenzverwaltung hinzufügen, um das Team beim Testen zu unterstützen.

</details>

## <a name="tabs"></a>Registerkarten

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.2](/legal/marketplace/certification-policies#114042-tabs).
Wenn Ihre App eine Registerkarte enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.
> [!TIP]
> Weitere Informationen zum Erstellen einer qualitativ hochwertigen App finden Sie unter [Richtlinien zum Entwerfen von Teams-Registerkarten](~/tabs/design/tabs.md).

</br>
<details><summary>Setup</summary>

* Die Einrichtung der Registerkarte darf einen neuen Benutzer **nicht in eine Sackgasse führen**. Geben Sie eine Nachricht zum Abschließen der Aktion oder des Workflows an. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-create-new-account.png" alt-text="validation-tabs-setup-create-new-acc":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-missing-forward-guidance.png" alt-text="validation-tabs-missing-fwd-guidance":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-new-user.png" alt-text="validation-tabs-set-up-new-user":::

* Authentifizieren Sie Ihre Benutzer während der Registerkarteneinrichtung und nicht danach, um die beste Erfahrung beim ersten Start zu machen. Die Authentifizierung kann außerhalb des Konfigurationsfensters der Registerkarte erfolgen. [*Vorgeschlagene Korrektur*]

* Der Benutzer darf die Registerkartenkonfiguration in Teams nicht verlassen, um Inhalte außerhalb von Teams zu erstellen und dann zu Teams zurückzukehren, um sie anzuheften. Der Konfigurationsbildschirm der Registerkarte muss den Wert der Konfiguration erläutern und wie sie durchgeführt wird. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-profile-name.png" alt-text="validation-tabs-set-up-profile-name":::

* Der Registerkartenkonfigurationsbildschirm darf keine gesamte Website einbetten. Konzentrieren Sie sich auf Ihre Konfigurationserfahrung. Wenn Sie z. B. eine Projektmanagement-Anwendung entwickeln, mit der Benutzer ein Projekt in einem Kanal konfigurieren können, sollten Sie den Konfigurationsbildschirm für die Registerkarte so gestalten, dass der Benutzer ein Projekt aus Ihrer Anwendung auswählen kann, um es im Kanal zu konfigurieren. [*obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-experience.png" alt-text="validation-tabs-setup-configuration-exp":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-screen.png" alt-text="validation-tabs-set-up-configuration-screen":::

* Der Konfigurationsbildschirm der Registerkarte darf den Benutzer nicht auffordern, eine URL einzubetten. Die Aufforderung an den Benutzer, während der Einrichtung der Registerkarte eine URL zu konfigurieren, ist ein Fehler in der Benutzerführung. Der Benutzer verlässt den Konfigurationsbildschirm der Registerkarte, ruft die URL ab, kehrt zum Konfigurationsbildschirm zurück und gibt die URL ein. Ein bereits vorhandenes Teams-Feature ermöglicht Benutzern bereits das Anheften eines Websitelinks im Kanal. Wenn Ihre App den Benutzer auffordert, bei der Konfiguration der Registerkarte eine Website-URL einzubetten, und die App darauf beschränkt ist, den gesamten Website-Inhalt auf der Registerkarte des Kanals anzuzeigen, bietet Ihre App dem Benutzer keinen nennenswerten Mehrwert. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configured-url.png" alt-text="validation-tabs-set-up-configured-url":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configured-url-two.png" alt-text="validation-tabs-set-up-configured-url-two":::

</details>
</br>

<details><summary>Ansichten</summary>

* Im Bereich des Anmeldebildschirms dürfen keine großen Logos verwendet werden. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-applogin.png" alt-text="validation-views-app-login":::

* Inhalte können vereinfacht werden, indem sie auf mehrere Registerkarten verteilt werden. [*Vorgeschlagene Korrektur*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-multiple-tabs.png" alt-text="val-views-multiple-tabs":::

* Registerkarten dürfen keinen doppelten Header aufweisen. Entfernen Sie das doppelte Logo aus dem iframe, da das Registerkartenframework bereits das App-Symbol und den Namen anzeigt. [*Vorgeschlagener Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-duplicate-header-logo.png" alt-text="validation-views-duplicate-head-logo":::

</details>
</br>

<details><summary>Navigation</summary>

Im Folgenden sind die Navigationsrichtlinien aufgeführt:

* Registerkarten dürfen keine Navigation bereitstellen, die in Konflikt mit der primären Teams-Navigation steht. Wenn Sie eine linke Navigation auf der Registerkarte bereitstellen, darf sie nicht nur Symbole oder Symbole mit gestapeltem Text enthalten. Es darf sich nicht um eine zusammenklappbare Leiste mit der Möglichkeit handeln, Symbole mit gestapeltem Text zu sehen (wie bei der Teams-Navigationsleiste). Fügen Sie Icons mit Inline-Text oder nur Text ein oder verwenden Sie Hamburger-Menüs anstelle der linken Tabulatorleiste. [*Obligatorischer Fix*]

Entwerfen Sie Ihre App mit [einfachen](~/concepts/design/design-teams-app-basic-ui-components.md) und [erweiterten](~\concepts\design\design-teams-app-advanced-ui-components.md) Fluent UI-Komponenten.

:::image type="content" source="../../../../assets/images/submission/validation-navigation-static-tab.png" alt-text="validation-nav-static-tab":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-horizontal-rail.png" alt-text="validation-nav-horizontal-rail":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-left-navigation.png" alt-text="validation-navigation-left-nav":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-icon-text.png" alt-text="validation-nav-icon-text":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-collapsable-left-rail.png" alt-text="validation-nav-collapsable-left-rail":::

* Registerkarten mit Symbolleiste in der linken Leiste müssen einen Abstand von 20 Pixeln von der linken Team-Navigation lassen. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-spacing-between-toolbar.png" alt-text="validation-nav-spacing-between-toolbar":::

* Die Zweit- und Drittseiten eines Tabs müssen in einer Ebene Zwei (L2)- und Ebene Drei (L3)-Ansicht im Hauptregisterkartenbereich geöffnet werden, der über Breadcrumb Navigation oder die linke Navigationsleiste geleitet wird. Sie können auch die folgenden Komponenten einschließen, um die Registerkartennavigation zu unterstützen: [*Obligatorischer Fix*]
  * Zurück-Schaltflächen
  * Seitenüberschriften
  * Hamburger-Menüs
* Die Registerkarte darf keinen horizontalen Bildlauf aufweisen. Whiteboarding-Apps und andere Apps, die eine größere Arbeitsfläche benötigen, damit die Benutzer zusammenarbeiten können, ohne dass das Gefühl entsteht, dass die App nicht funktioniert, können je nach geschäftlichem Bedarf einen horizontalen Bildlauf verwenden. [*Vorgeschlagene Korrektur*]

* Deep-Links in Registerkarten dürfen nicht mit einer externen Webseite, sondern an einer Stelle in Teams verknüpft werden. Beispielsweise Aufgabenmodule oder andere Registerkarten. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-view-button-not-linked-static-tab.png" alt-text="validation-nav-view-button-not-linked-static-tab":::

* Registerkarten dürfen Benutzern nicht erlauben, außerhalb Teams zu navigieren, um die Hauptanwendung zu nutzen. Registerkarten können für nicht zum Kerngeschäft gehörende Arbeitsabläufe außerhalb von Teams umgeleitet werden. Zum Beispiel, um ein Supportticket zu erstellen. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-within-configuration.png" alt-text="validation-nav-core-workflow-within-configuration":::

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-redirects-outside.png" alt-text="validation-nav-core-workflow-redirects-outside":::

</details>
</br>

<details><summary>Benutzerfreundlichkeit</summary>

* Registerkarten müssen einen Wert bereitstellen, der über das Hosten einer vorhandenen Website hinausgeht. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-provides-workflows.png" alt-text="validation-usability-app-provides-work-flows":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-website-i-framed.png" alt-text="validation-usability-website-i-frame":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-teams-app-identical-website.png" alt-text="validation-usability-teams-app-identical-websites":::

* Der Inhalt darf innerhalb der Registerkarte nicht abgeschnitten werden oder sich überschneiden.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-content-truncation.png" alt-text="validation-usability-content-truncations":::

* Benutzer müssen in der Lage sein, ihre letzte Aktion auf der Registerkarte rückgängig zu machen.

* Registerkarten in einem persönlichen Kontext können Inhalte von freigegebenen Instanzen der App aggregieren. So muss beispielsweise eine Projektmanagement-App mit einer konfigurierbaren Registerkarte, die es Kanalmitgliedern ermöglicht, das Projekt auf Kanban-Karten zu kommentieren, diese Inhalte zusammenfassen und in der persönlichen App anzeigen. [*Vorgeschlagene Korrektur*]

* Registerkarten müssen für Teams-Designs reaktionsfähig sein. Wenn ein Benutzer das Design ändert, muss das Design der App die Auswahl widerspiegeln.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-responsive-tabs.png" alt-text="validation-usability-responsive-tab":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-unresponsive-tabs.png" alt-text="validation-usability-unresponsive-tab":::

* Registerkarten müssen nach Möglichkeit Komponenten im Teams-Stil verwenden, z. B. Teams-Schriftarten, Typraster, Farbpaletten, Rastersystem, Bewegung, Ton der Stimme usw. Weitere Informationen finden Sie unter [Richtlinien für den Registerkartenentwurf](/microsoftteams/platform/tabs/design/tabs). [*vorgeschlagene Korrektur*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-uses-diff-font.png" alt-text="validation-usability-app-uses-font":::

* Wenn Ihre App-Funktionalität Änderungen an den Einstellungen erfordert, fügen Sie eine **Registerkarte „Einstellungen“** ein. [*Vorgeschlagene Korrektur*]
* Registerkarten müssen dem Teams-Interaktionsentwurf folgen, z. B. seiteninterne Navigation, Position und Verwendung von Dialogfeldern, Informationshierarchien usw. Weitere Informationen finden Sie unter [Microsoft Teams Fluent UI Kit](~/concepts/design/design-teams-app-basic-ui-components.md)

* Registerkarteninhalte im iframe dürfen keine Funktionen enthalten, die die Kernfunktionen von Teams nachahmen. Zum Beispiel Bots, Nachrichtenerweiterungen, Anrufe, Besprechungen usw.

* Der Inhalt der Landing Page der konfigurierbaren Tabs muss für alle Mitglieder des Channels kontextuell gleich sein.

* Inhalte auf der Landing Page von konfigurierbaren Registerkarten dürfen nicht auf die individuelle Verwendung beschränkt sein und dürfen keine persönlichen Inhalte wie **Meine Aufgaben** oder **Mein Dashboard** enthalten.

* Wenn Ihre App die Bereitstellung einer persönlichen Bereichsansicht für den Benutzer erfordert, um die Effizienz oder Produktivität am Arbeitsplatz zu steigern, verwenden Sie gefilterte Ansichten, Deep Links zu persönlichen Apps oder navigieren Sie auf der konfigurierbaren Registerkarte zu L2- oder L3-Ansichten, und halten Sie die Zielseite für alle Benutzer kontextbezogen gleich.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-tab-personal-info.png" alt-text="validation-usability-configurable-tab-pers-info":::

* Konfigurierbare Registerkarten müssen über eine gezielte Funktionalität verfügen.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-nested-tabs.png" alt-text="validation-usability-configurable-nested-tab":::

* Registerkartenfunktionen müssen auf Mobilgeräten (Android und iOS) vollständig responsiv sein.

> [!TIP]
>
> * Fügen Sie einen persönlichen Bot neben einer persönlichen Registerkarte ein.
> * Erlauben Sie Benutzern, Inhalte von ihrer persönlichen Registerkarte zu teilen.

</details>

## <a name="bots"></a>Bots

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.3](/legal/marketplace/certification-policies#114043-bots).

Wenn Ihre App einen Bot enthält, stellen Sie sicher, dass er diesen Richtlinien entspricht.

> [!TIP]
> Weitere Informationen zum Erstellen eines qualitativ hochwertigen App-Erlebnisses finden Sie unter [Entwurfsrichtlinien für Teams-Bots](~/bots/design/bots.md).

</br>
<details><summary>Bot-Befehle</summary>

Das Analysieren von Benutzereingaben und das Vorhersagen der Benutzerabsicht ist schwierig. Botbefehle stellen Benutzern eine Reihe von Wörtern oder Ausdrücken bereit, die Ihr Bot versteht.

* Es wird dringend empfohlen, unterstützte Bot-Befehle in Ihren App-Konfigurationen aufzulisten. Diese Befehle werden im Feld zum Verfassen angezeigt, wenn ein Benutzer versucht, Ihrem Bot eine Nachricht zu senden.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-listed.png" alt-text="validation-bot-commands-list":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-not-listed.png" alt-text="validation-bot-commands-not-list":::

* Alle Befehle, die Ihr Bot unterstützt, müssen ordnungsgemäß funktionieren, einschließlich generischer Befehle wie **Hi**, **Hello** und **Help**.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-help-command.png" alt-text="validation-bots-help-command":::

* Bot-Befehle dürfen einen Benutzer nicht in eine Sackgasse führen, die Befehle müssen immer einen Weg nach vorn weisen.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-deadend.png" alt-text="validation-bot-commands-dead-end":::

> [!TIP]
> Fügen Sie für persönliche Bots eine Registerkarte **Hilfe** hinzu, die genauer beschreibt, was Ihr Bot tun kann.

</details>
</br>

<details><summary>Bot-Begrüßungsnachrichten</summary>

* Wenn die App einen komplexen Konfigurationsablauf hat (erfordert eine Unternehmenslizenz oder hat keinen intuitiven Anmeldeablauf), dann müssen Bots in solchen Apps beim ersten Durchlauf immer eine Willkommensnachricht senden.

Für ein optimales Erlebnis muss die Willkommensnachricht den Wert enthalten, den der Bot den Benutzern bietet, wer den Bot im Kanal installiert hat, wie der Bot konfiguriert wird und alle unterstützten Bot-Befehle kurz beschrieben werden. Sie können die Begrüßungsnachricht mithilfe einer adaptiven Karte mit Schaltflächen anzeigen, um die Benutzerfreundlichkeit zu verbessern. Weitere Informationen finden Sie unter [Auslösen einer Bot-Begrüßungsnachricht.](~/bots/how-to/conversations/send-proactive-messages.md) Für Apps ohne komplexen Konfigurationsablauf können Sie während der ersten Ausführung des Bots eine Willkommensnachricht auslösen. Wenn jedoch eine Begrüßungsnachricht ausgelöst wird, muss sie den Richtlinien für Begrüßungsnachrichten entsprechen.

:::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message.png" alt-text="validation-bot-welcom-message":::

:::image type="content" source="../../../../assets/images/submission/validation-bot-no-welcome-message.png" alt-text="validation-bot-no-wel-come-message":::

* Bot-Begrüßungsnachrichten in Kanälen und Chats sind bei der ersten Ausführung optional, insbesondere wenn der Bot für den persönlichen Gebrauch verfügbar ist und ähnliche Aktionen ausführt. Ihr Bot darf keine Begrüßungsnachrichten an einzelne Nutzer senden (das gilt als [Spamming](#botmessagespamming)). In der Nachricht muss auch die Person erwähnt werden, die den Bot hinzugefügt hat.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-not-triggered.png" alt-text="validation-bot-welcome-message-not-trigger":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-triggered.png" alt-text="validation-bot-wel-message-trigger":::

> [!TIP]
> In Begrüßungsnachrichten an einzelne Nutzer kann eine Karussell-Tour einen effektiven Überblick über Ihren Bot und alle anderen App-Funktionen bieten, um Nutzer zu ermutigen, Bot-Befehle auszuprobieren. Erstellen Sie z. B. **eine Aufgabe**.

</details>
</br>

<details><summary><a id="botmessagespamming">Spam mit Bot-Nachrichten</a></summary>

Bots dürfen Nutzer nicht durch das Versenden mehrerer Nachrichten in kurzer Zeit spammen.

* **Bot-Nachrichten in Kanälen und Chats**: Spamen Sie Benutzer nicht, indem Sie separate Beiträge erstellen. Erstellen Sie einen einzelnen Beitrag mit Antworten im selben Thread.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-message-spamming-one-message.png" alt-text="validation-bot-message-spam-one-message":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-message-spamming-multiple-messages.png" alt-text="validation-bot-message-spam-multiple-message":::

* **Bot-Nachrichten in persönlichen Apps**:
  * Senden Sie nicht mehrere Nachrichten in kurzer Zeit.
  * Senden Sie eine Nachricht mit vollständigen Informationen.
  * Vermeiden Sie mehrfache Unterhaltungen, um einen einzelnen sich wiederholenden Workflow abzuschließen.
  * Verwenden Sie ein Formular (oder Aufgabenmodul), um alle Eingaben eines Benutzers gleichzeitig zu erfassen.
  * NLP-basierte Chatbots können Multi-Turn-Konversationen nutzen, um die Diskussion ansprechender zu gestalten und einen Arbeitsablauf abzuschließen.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-task-module.png" alt-text="validation-bot-message-using-task-module":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-mutliple-conversation.png" alt-text="validation-bot-messages-using-mutliple-conversations":::

* **Willkommensnachrichten**: Wiederholen Sie nicht gleiche Willkommensnachricht in regelmäßigen Abständen. Wenn beispielsweise ein neues Mitglied zu einem Team hinzugefügt wird, sollten Sie die anderen Mitglieder nicht mit einer Begrüßungsnachricht spammen. Nachricht an das neue Mitglied persönlich senden.

</details>
</br>

<details><summary>Bot-Benachrichtigungen</summary>

Bot-Benachrichtigungen müssen Inhalte enthalten, die für den Bereich relevant sind, den Sie für den Bot definieren (Team, Chat oder persönlich).

:::image type="content" source="../../../../assets/images/submission/validation-bot-notifications-relevant.png" alt-text="validation-bot-notification-relevant":::

:::image type="content" source="../../../../assets/images/submission/validation-bot-notifications-not-relevant.png" alt-text="validation-bot-notification-not-relevant":::

</details>
</br>
<details><summary>Bots und adaptive Karten</summary>

Adaptive Karten sind eine dringend empfohlene Möglichkeit, Bot-Nachrichten anzuzeigen. Die Karten müssen einfach sein und nur bis zu sechs Aktionen enthalten. Um weitere Inhalte anzuzeigen, sollten Sie ein Aufgabenmodul oder eine Registerkarte verwenden.

Weitere Informationen zu Karten finden Sie unter:

* [Entwerfen Adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

Die Bot-Erfahrung muss auf Mobilgeräten vollständig responsiv sein. Die Bot-Antworten müssen gegebenenfalls einen Weg nach vorn aufzeigen. Bots müssen reaktionsschnell sein und bei Fehlern eine ansprechende Fehlermeldung anzeigen. Bot-Nachrichten, die im persönlichen Bereich an die Basis des Benutzers auf Triggern in einem gemeinsamen Bereich gesendet werden, müssen kontextbezogene Informationen (einschließlich des Nachrichtenursprungs) bereitstellen.

</details>
</br>

<details><summary>Nur Benachrichtigungsbots</summary>

Apps, die aus reinen Benachrichtigungs-Bots bestehen, bieten dem Nutzer einen Mehrwert, indem sie auf der Grundlage bestimmter Auslöser oder Ereignisse in der Hauptanwendung oder im Backend Benachrichtigungen für den Nutzer auslösen. Beispielsweise wird ein neuer Vertriebsleiter oder Einsteiger hinzugefügt, den das Vertriebsteam weiter verfolgen kann. Ein sehr guter Benachrichtigungsbot benachrichtigt die Benutzer regelmäßig über bestimmte Ereignisvervollständigungen, z. B. Workflowvervollständigungen oder Warnungen.

Eine Meldung ist für Teams von Nutzen, wenn:

1. Die bereitgestellte Karte oder der bereitgestellte Text enthält angemessene Details, die keine weiteren Benutzeraktionen erfordern.
1. Die bereitgestellte Karte oder der bereitgestellte Text enthält angemessene Vorschauinformationen, damit ein Benutzer Maßnahmen ergreifen oder weitere Details in einem Link anzeigen kann, der außerhalb Teams geöffnet wird.

Apps, die nur Benachrichtigungen mit Inhalten bereitstellen wie **“Sie haben eine neue Benachrichtigung. Klicken Sie, um sie anzuzeigen“** bereitstellen und von den Nutzern verlangen, für alles andere außerhalb von Teams zu navigieren, bieten keinen nennenswerten Mehrwert innerhalb von Teams.

:::image type="content" source="../../../../assets/images/submission/validation-navigation-static-tab.png" alt-text="validation-nav-static-tab":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-horizontal-rail.png" alt-text="validation-nav-horizontal-rail":::

:::image type="content" source="../../../../assets/images/submission/validation-bot-notification-only-inadequete-info.png" alt-text="validation-bot-notifications-only-inadequete-info":::

> [!TIP]
> Zeigen Sie Informationen in der Vorschau an, und stellen Sie grundlegende Inline-Benutzeraktionen auf der bereitgestellten Karte bereit, so dass der Benutzer nicht für alle Aktionen (unabhängig von der Komplexität) außerhalb von Teams navigieren muss.

</details>

## <a name="message-extensions"></a>Nachrichtenerweiterungen

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.4](/legal/marketplace/certification-policies#114044-messaging-extensions).

Wenn Ihre App eine Nachrichtenerweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Weitere Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Microsoft Teams Nachrichtenerweiterungen](~/messaging-extensions/design/messaging-extension-design.md).

</br>
<details><summary>Aktionsbefehle</summary>

Aktionsbasierte Nachrichtenerweiterungen müssen folgende Aktionen ausführen:

* Ermöglichen Sie es Benutzern, Aktionen für eine Nachricht auszulösen, ohne Zwischenschritte wie die Anmeldung auszuführen.

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-no-intermediate-step.png" alt-text="validation-messaging-extension-no-intermediate-steps":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-intermediate-step-available.png" alt-text="validation-messaging-extension-intermediate-steps-available":::

* Übergeben des Nachrichtenkontexts an den nächsten Arbeitsstatus. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-passes-message.png" alt-text="validation-messaging-extension-app-passes-messages":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-doesnot-pass-message.png" alt-text="validation-messaging-extension-app-doesnot-pass-messages":::

* Integrieren Sie den Namen der Host-App anstelle eines generischen Verbs für Aktionsbefehle, die von einer Chat-Nachricht, einem Channel-Post oder einem Aufruf zum Handeln innerhalb von Apps ausgelöst werden. Verwenden Sie z. B. **Starten einer Skype-Besprechung** für **Besprechung starten**, **Datei in DocuSign hochladen** für **Datei hochladen** usw. [*Vorgeschlagene Korrektur*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-host-name.png" alt-text="validation-messaging-extension-action-command-host-names":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-verb.png" alt-text="validation-messaging-extension-action-commands-verb":::

</details>
</br>

<details><summary>Vorschau-Links (Link-Unfurling)</summary>

[*Obligatorischer Fix*]

Nachrichtenerweiterungen müssen eine Vorschau der erkannten Links im Feld „Verfassen“ in Microsoft Teams anzeigen. Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden (entweder absolute URLs oder Platzhalter). Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig. Top-Level Domains sind ebenfalls nicht zulässig. Zum Beispiel `*.com` oder `*.org`. [*Obligatorischer Fix*]

</details>
</br>

<details><summary>Suchbefehle</summary>

* Such-basierte Nachrichtenerweiterungen müssen Text bereitstellen, der den Nutzern bei der effektiven Suche hilft. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-search-commands-text-available.png" alt-text="validation-search-command-text-available":::

* @mention ausführbare Dateien müssen klar, leicht verständlich und lesbar sein.

    :::image type="content" source="../../../../assets/images/submission/validation-search-command-unclear-executable.png" alt-text="validation-search-commands-unclear-executable":::

</details>
</br>

<details><summary>Aktionsbefehle</summary>Nur Apps mit suchbasierten Nachrichtenerweiterungen

[*Obligatorischer Fix*]

Apps, die aus einer suchbasierten Nachrichtenerweiterung bestehen, bieten Benutzern einen Mehrwert, indem sie Karten freigeben, die kontextbezogene Unterhaltungen ohne Kontextwechsel ermöglichen.

Um die Validierung für eine reine suchbasierte Nachrichtenerweiterung zu bestehen, ist Folgendes als Basis erforderlich, um sicherzustellen, dass die Benutzerfreundlichkeit nicht beeinträchtigt wird. Eine über eine Nachrichtenerweiterung freigegebene Karte bietet einen Mehrwert in Microsoft Teams, wenn:

1. Die bereitgestellte Karte enthält angemessene Details, die keine weitere Benutzeraktion erfordern.
1. Die bereitgestellte Karte enthält angemessene Vorschauinformationen, damit ein Benutzer Maßnahmen ergreifen oder weitere Details in einem Link anzeigen kann, der außerhalb von Teams geöffnet wird.

    :::image type="content" source="../../../../assets/images/submission/validation-search-based-messaging-ext-adequete-info.png" alt-text="validation-search-base-messaging-ext-adequete-info":::

    :::image type="content" source="../../../../assets/images/submission/validation-search-based-messaging-ext-inadequete-info.png" alt-text="validation-search-base-messaging-ext-inadequete-info":::

Apps, die nur zur Verbreitung von Links dienen, bieten in Teams keinen nennenswerten Mehrwert. Erwägen Sie die Erstellung zusätzlicher Workflows in Ihrer App, wenn Ihre App nur die Verbreitung von Links unterstützt und keine andere Funktionalität aufweist.

</details>

## <a name="task-modules"></a>Aufgabenmodule

[*Obligatorischer Fix*]

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.5](/legal/marketplace/certification-policies#114045-task-modules).
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Ein Aufgabenmodul muss ein Symbol und den Kurznamen der App enthalten, mit der es verknüpft ist. Aufgabenmodule dürfen nicht eine ganze App einbetten, sondern nur die Komponenten anzeigen, die für die Durchführung einer bestimmten Aktion erforderlich sind.

Weitere Informationen finden Sie unter [Entwurfsrichtlinien für Teams-Aufgabenmodule](~\task-modules-and-cards\task-modules\design-teams-task-modules.md).

:::image type="content" source="../../../../assets/images/submission/validation-task-module-displays-components.png" alt-text="validation-task-module-displays-component":::

:::image type="content" source="../../../../assets/images/submission/validation-task-module-embeds-app.png" alt-text="validation-task-module-embed-app":::

> [!TIP]
> Weitere Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den[ Entwurfsrichtlinien für Teams Aufgabenmodule](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

</details>

## <a name="meeting-extensions"></a>Besprechungserweiterungen

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.6](/legal/marketplace/certification-policies#114046-meeting-extensions).
> [!TIP]
> Weitere Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Designrichtlinien für die Erweiterung von Teams-Meetings](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

</br>
<details><summary>Allgemein</summary>

Verwenden Sie die folgenden Richtlinien für die Erweiterung von Besprechungen:

* Apps zur Erweiterbarkeit von Besprechungen müssen ein reaktionsschnelles In-Meeting-Erlebnis bieten und auf die Team Meeting-Erfahrung abgestimmt sein. Die In-Meeting-Erfahrung ist obligatorisch, Pre-Meeting-Erfahrungen und Post-Meeting-Erfahrungen sind nicht obligatorisch.

  * Mit der Pre-Meeting App-Erfahrung können Nutzer Meeting-Apps finden und hinzufügen. Benutzer können auch Aufgaben vor der Besprechung ausführen, z. B. die Entwicklung einer Umfrage, um die Besprechungsteilnehmer zu befragen. Wenn Ihre App eine Erfahrung vor der Besprechung bietet, muss sie für den Workflow der Besprechung relevant sein.

  * Mit der App-Erfahrung nach der Besprechung können Benutzer die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback sowie andere App-Inhalte. Wenn Ihre App eine Erfahrung nach der Besprechung bietet, muss sie für den Workflow der Besprechung relevant sein.

  * Mit der In-Meeting-App-Erfahrung können Sie Besprechungsteilnehmer während der Besprechung einbeziehen und die Besprechungserfahrung für alle Teilnehmer verbessern. Teilnehmer dürfen nicht nach außerhalb der Teams-Besprechung geleitet werden, um wichtige Benutzer-Workflows Ihrer App abzuschließen.

* Ihre Anwendung muss einen Mehrwert bieten, der über die Bereitstellung benutzerdefinierter Szenen im Together-Modus in Teams hinausgeht.

* Das Feature „Gemeinsame Besprechungsphase“ kann nur über die Teams Desktop-App gestartet werden. Die Nutzung der gemeinsamen Besprechungsphase muss jedoch möglich sein und darf nicht unterbrochen werden, wenn sie auf mobilen Geräten angezeigt wird.

> [!TIP]
> Sie müssen `groupchat` als Bereich unter `configurableTabs` und `meetingDetailsTab` oder `meetingChatTab` und `meetingSidePanel` als Kontexteigenschaft im Manifest deklarieren, um Ihre App für Besprechungen auf Teams Mobile zu aktivieren.

</details>

</br>
<details><summary>Erfahrung vor und nach der Besprechung</summary>

* Bildschirmanzeigen vor und nach Besprechungen müssen den allgemeinen Richtlinien für den Entwurf von Registerkarten entsprechen. Weitere Informationen finden Sie unter [Teams-Entwurfsrichtlinien](~/tabs/design/tabs.md).
* Registerkarten dürfen kein horizontales Scrollen haben.
* Registerkarten müssen ein strukturiertes Layout aufweisen, wenn mehrere Elemente angezeigt werden. Beispielsweise finden Sie mehr als 10 Umfragen oder Erhebungen unter [Beispiellayout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Ihre App muss Benutzer benachrichtigen, wenn die Ergebnisse einer Umfrage oder Erhebung exportiert werden, indem sie angibt, dass **Ergebnisse erfolgreich heruntergeladen** wurden.

</details>

</br>
<details><summary>Besprechungserfahrung</summary>

* Apps dürfen nur während Besprechungen ein dunkles Design verwenden. Weitere Informationen finden Sie unter [Teams-Entwurfsrichtlinien](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming).
* Eine QuickInfo muss den Namen der App anzeigen, wenn der Mauszeiger während einer Besprechung über das App-Symbol bewegt wird.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-display-app-name.png" alt-text="validation-in-meeting-exp-display-app-names":::

* Nachrichtenerweiterungen müssen während Besprechungen genauso funktionieren wie außerhalb von Besprechungen.

</details>

</br>
<details><summary>Registerkarten in Besprechungen</summary>

* Muss reaktionsfähig sein.
* Die Abstands- und Komponentengrößen müssen beibehalten werden.
* Muss über eine Schaltfläche „Zurück“ verfügen, wenn mehrere Navigationsebenen vorhanden sind.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button.png" alt-text="validation-in-meeting-exp-back-buttons":::

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button-absent.png" alt-text="validation-in-meeting-exp-back-buttons-absent":::

* Darf nicht mehr als eine Schaltfläche zum Schließen enthalten. Dies könnte die Benutzer verwirren, da es bereits eine eingebaute Schaltfläche in der Kopfzeile gibt, um die Registerkarte zu schließen.
* Darf kein horizontales Scrollen haben.

</details>

</br>
<details><summary>Dialoge im Besprechungen</summary>

* Muss sparsam und für leichte und aufgabenorientierte Szenarien eingesetzt werden.
* Der Inhalt muss in einer einzigen Spalte angezeigt werden und darf nicht über mehrere Navigationsebenen verfügen.
* Darf keine Aufgabenmodule verwenden.
* Muss mit der Mitte der Besprechungsbereich ausgerichtet sein.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-dialog-not-aligned.png" alt-text="validation-in-meeting-dialog-not-align":::

* Muss geschlossen werden, nachdem ein Benutzer eine Schaltfläche ausgewählt oder eine Aktion ausgeführt hat.

* **Zusammen-Modus**: Stellen Sie sicher, dass Sie die folgenden Best Practices für den Aufbau einer Szene beachten:
  * Alle Bilder haben das .png-Format.
  * Das endgültige Paket mit allen zusammengestellten Bildern darf die Auflösung von 1920 x 1080 nicht überschreiten. Die Auflösung ist eine gerade Zahl. Diese Auflösung ist eine Voraussetzung dafür, dass Szenen erfolgreich angezeigt werden.
  * Die maximale Größe einer Szene beträgt 10 MB.
  * Die maximale Größe jedes Bilds beträgt 5 MB. Eine Szene ist eine Sammlung mehrerer Bilder. Der Grenzwert gilt für jedes einzelne Bild.
  * Wählen Sie nach Bedarf **Transparent** aus. Dieses Kontrollkästchen ist im rechten Bereich verfügbar, wenn ein Bild ausgewählt ist. Die überlappenden Bilder müssen als „transparent“ gekennzeichnet werden, um anzugeben, dass sie Bilder in der Szene überlappen.

</details>

## <a name="notifications"></a>Benachrichtigungen

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.7](/legal/marketplace/certification-policies#114047-notification-apis).

Wenn Ihre App die von [Microsoft Graph bereitgestellten Aktivitätsfeed-APIs](/graph/teams-send-activityfeednotifications) verwendet, stellen Sie sicher, dass sie die folgenden Richtlinien einhält.
<br></br>
<details><summary>Allgemein</summary>

* Alle in der App-Konfiguration angegebenen Benachrichtigungs-Auslöser müssen funktionieren.
* Benachrichtigungen müssen gemäß den unterstützten Sprachen lokalisiert werden, die für Ihre App konfiguriert sind.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.

</details>
</br>
<details><summary>Avatare</summary>

* Der Benachrichtigungs-Avatar muss mit dem Farbsymbol Ihrer App übereinstimmen.
* Von einem Benutzer ausgelöste Benachrichtigungen müssen den Avatar des Benutzers enthalten.

</details>
</br>
<details><summary>Spamming</summary>

* Apps dürfen nicht mehr als 10 Benachrichtigungen pro Minute an einen Benutzer senden.
* Bots und der Aktivitätsfeed dürfen keine doppelten Benachrichtigungen auslösen.
* Benachrichtigungen müssen den Benutzern einen gewissen Wert bieten und dürfen nicht für triviale oder irrelevante Ereignisse verwendet werden.

</details>
</br>
<details><summary>Navigation und Layout</summary>

* Benachrichtigungen müssen dem Layout und der Erfahrung des Teams-Aktivitätsfeeds entsprechen.
* Bei Auswahl einer Benachrichtigung muss der Benutzer zu relevanten Inhalten innerhalb Teams weitergeleitet werden.

</details>

## <a name="microsoft-365-app-compliance-program"></a>Microsoft 365-App-Compliance Program

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.6](/legal/marketplace/certification-policies#11406-publisher-attestation).
<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Das Microsoft 365 App Compliance-Programm soll Organisationen dabei helfen, Risiken zu bewerten und zu verwalten, indem Sicherheits- und Compliance-Informationen zu Ihrer App ausgewertet werden. Wenn Sie eine App im Teams Store veröffentlichen, müssen Sie die folgenden Stufen des Programms abschließen:

* **Publisher Überprüfung:** Hilft Administratoren und Endbenutzern, die Authentizität von App-Entwicklern zu verstehen, die sich in die Microsoft Identity Platform integrieren. Nach Abschluss des Vorgangs wird im Zustimmungsdialog von Azure Active Directory und auf anderen Bildschirmen ein blaues **verifiziert** Zeichen angezeigt. Weitere Informationen finden Sie unter [Markieren Ihrer App als vom Herausgeber überprüft](/azure/active-directory/develop/mark-app-as-publisher-verified).

    :::image type="content" source="../../../../assets/images/submission/validation-365-compliance-publisher-verification.png" alt-text="validation-365-compliance-publisher-verifications":::

* **Publisher-Bestätigung:** Ein Prozess, bei dem Sie allgemeine Informationen zur Datenverarbeitung sowie Sicherheits- und Compliance-Informationen weitergeben, um potenziellen Kunden zu helfen, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Wenn Sie eine App übermitteln, die zuvor noch nicht aufgeführt wurde, können Sie den Herausgebernachweis erst dann offiziell abschließen, wenn sich Ihre App im Teams Store befindet. Wenn Sie eine aufgeführte App aktualisieren, führen Sie die Publisher-Bestätigung durch, bevor Sie die neueste Version der App einreichen.

</details>

## <a name="advertising"></a>Werbung

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.7](/legal/marketplace/certification-policies#11407-advertising).

Apps dürfen keine Werbung anzeigen, einschließlich dynamischer Anzeigen, Banneranzeigen und Anzeigen in Nachrichten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Sie ein Partner Center-Konto](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)

## <a name="see-also"></a>Weitere Informationen

* [Verteilen Ihrer App](~/concepts/deploy-and-publish/apps-publish-overview.md)
* [Vorbereiten der Übermittlung an den Store](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Testen und Debuggen Ihrer App](~/concepts/build-and-test/debug.md)
* [Erstellen eines Partner Center-Entwicklerkontos](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
