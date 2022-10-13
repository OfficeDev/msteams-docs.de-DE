---
title: Richtlinien zur Validierung von Microsoft Teams-Speichern
description: Erfahren Sie, wie Sie die Wahrscheinlichkeit erhöhen, dass Ihre App den Microsoft Teams Store-Übermittlungsprozess besteht. Grundlegendes zu den obligatorischen und vorgeschlagenen Korrekturen. Erkunden Sie die Validierungsrichtlinien.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 0a0151c72820baf1b6bd39ee00539cacbd3fa38b
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560981"
---
# <a name="microsoft-teams-store-validation-guidelines"></a>Richtlinien zur Validierung von Microsoft Teams-Speichern

Wenn Sie diese Richtlinien befolgen, erhöht sich die Wahrscheinlichkeit, dass Ihre App den Einreichungsprozess im Microsoft Teams Store besteht. Die Teams-spezifischen Richtlinien ergänzen die Zertifizierungsrichtlinien für den [kommerziellen Microsoft-Marketplace](/legal/marketplace/certification-policies#1140-teams) und werden regelmäßig aktualisiert, um neue Funktionen, Benutzerfeedback und Änderungen der Geschäftsregeln zu berücksichtigen.

> [!NOTE]
>
> * Einige Richtlinien gelten möglicherweise nicht für Ihre App. Wenn Ihre App beispielsweise keinen Bot enthält, können Sie botbezogene Richtlinien ignorieren.
> * Wir haben diese Richtlinien mit Querverweisen auf die kommerziellen Zertifizierungsrichtlinien von Microsoft versehen und Do's und Don'ts mit Beispielen für erfolgreiche oder nicht erfolgreiche Szenarien in unserem Validierungsprozess hinzugefügt.
> * Bestimmte Richtlinien sind als *obligatorische Korrektur* gekennzeichnet. Wenn Ihre App-Einreichung diese obligatorischen Richtlinien nicht erfüllt, erhalten Sie von uns einen Fehlerbericht mit Maßnahmen zur Behebung des Problems. Ihre App-Einreichung wird die Microsoft Teams Store-Validierung erst bestehen, nachdem Sie die Probleme behoben haben.
> * Other guidelines are marked as *Suggested Fix*. For an ideal user experience, we suggest that you fix the issues, however, your app submission will not be blocked from publishing on the Teams store, if you choose not to fix the issues.

:::row:::
   :::column:::
      :::image type="icon" source="../../../../assets/icons/value-proposition.png" link="#value-proposition" border="false":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../../assets/icons/security.png" link="#security" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/function.png" link="#general-functionality-and-performance" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/package.png" link="#app-package-and-store-listing" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/saas-offer.PNG" link="#apps-linked-to-saas-offer" border="false":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/tab.png" link="#tabs" border="false":::
   :::column-end:::
   :::column:::
      :::image type="icon" source="../../../../assets/icons/bot.png" link="#bots-1" border="false":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../../assets/icons/messaging-extension.png" link="#message-extensions" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/task-module.png" link="#task-modules" border="false":::
   :::column-end:::
     :::column span="":::
      :::image type="icon" source="../../../../assets/icons/meeting.png" link="#meeting-extensions" border="false":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/notifications.png" link="#notifications" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/microsoft-365.png" link="#microsoft-365-app-compliance-program" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/advertising.png" link="#advertising" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/crypto-currency-based-apps-icon.png" link="#cryptocurrency-based-apps" border="false":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/app-functionality-icon.png" link="#app-functionality" border="false":::
   :::column-end:::
:::row-end:::
:::row:::
   :::column span="":::
      :::image type="icon" source="../../../../assets/icons/mobile-experience-icon.png" link="#mobile-experience" border="false":::
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
* Präfixe oder Suffixe von allgemeinen Substantiven mit dem Namen des Entwicklers. Beispielsweise **Contoso Tasks** anstelle von **Tasks**.
* Dürfen keine **Teams** - oder andere Microsoft-Produktnamen wie Excel, PowerPoint, Word, OneDrive, SharePoint, OneNote, Azure, Surface und Xbox verwenden, die fälschlicherweise auf co-Branding oder Co-Selling hinweisen könnten. Weitere Informationen zum Verweisen auf Microsoft-Softwareprodukte und -Dienste finden Sie unter [Microsoft-Warenzeichen- und Markenrichtlinien](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
* Der Name einer im Store aufgeführten App oder eines anderen Angebots auf dem kommerziellen Marktplatz darf nicht kopiert werden.
* Darf keine profanen oder abfälligen Begriffe enthalten. Der Name darf auch keine rassen- oder kulturell unsensible Sprache enthalten.
* Muss eindeutig sein. Wenn Ihre App (Contoso) im Microsoft Teams Store und in Microsoft AppSource aufgeführt ist und Sie eine andere app speziell für eine Geografische Region wie Contoso Mexico auflisten möchten, muss Ihre Übermittlung die folgenden Kriterien erfüllen:
  * Nennen Sie die regionsspezifischen Funktionen der App in den Abschnitten Titel, Metadaten, First-Response-App-Erfahrung und Hilfe. Der Titel muss z. B. „Contoso Mexiko“ sein. Der Titel der App muss eine bestehende App desselben Entwicklers deutlich unterscheiden, um Verwechslungen beim Endnutzer zu vermeiden.
  * Wählen Sie beim Hochladen des App-Pakets im Partner Center die richtigen **Märkte** aus, in denen die App im Abschnitt **„Verfügbarkeit“** verfügbar sein wird.

* Der App-Name darf nicht mit einem zentralen Teams-Feature wie Chat, Kontakte, Kalender, Anrufe, Dateien, Aktivität, Teams, Apps und Hilfe führen. Der App-Name kann auf Chat, Kontakte, Kalender, Anrufe, Dateien, Aktivität, Teams, Apps und Hilfe bei der Installation im linken Navigationsbereich gekürzt werden.

* If your app is part of an official partnership with Microsoft, the name of your app must come first. For example, **Contoso Connector for Microsoft Teams**.

* Der App-Name darf keinen Verweis auf Microsoft- oder Microsoft-Produkte enthalten. Verwenden Sie **Teams**, **Microsoft** oder **App** nicht im Namen der App, es sei denn, Ihre App steht in offizieller Partnerschaft mit Microsoft. In einem solchen Fall muss der App-Name vor einem Verweis auf Microsoft an erster Stelle sein. Beispiel: **Contoso-Connector für Microsoft Teams**.

* Verwenden Sie bei der Benennung keine Klammer, um Microsoft-Produkte einzuschließen.

* Der Name des Entwicklers muss im Manifest und in AppSource identisch sein.

* Übermittelte App-Manifeste müssen Produktionsmanifeste sein. Daher darf der App-Name nicht angeben, dass es sich bei der App um eine Vorproduktions-App handelt. Beispielsweise darf der App-Name keine Wörter wie Beta, Dev, Preview und UAT enthalten.

 > [!TIP]
 > Das Branding Ihrer App im Microsoft Teams Store und in AppSource, einschließlich Ihres App-Namens, Entwicklernamens, App-Symbols, AppSource-Screenshots, Videos, Kurzbeschreibungen und Websites, darf sich nicht als offizielles Microsoft-Angebot annehmen, es sei denn, Ihre App ist ein offizielles Microsoft 1P-Angebot.

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

App-Featurenamen in Schaltflächen und anderem Benutzeroberflächentext dürfen keine Terminologie verwenden, die für Teams und andere Microsoft-Produkte reserviert ist. Beispielsweise sind " **Besprechung starten**", **"Anrufen**" oder **"Chat starten** " Featurenamen, die von Microsoft in Microsoft Teams verwendet werden. Geben Sie bei Bedarf ihren App-Namen an, um den Unterschied deutlich zu machen, z. B. **"Contoso-Besprechung starten"**.

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

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png"::: Dieser Abschnitt ist inline mit der [kommerziellen Zertifizierungsrichtlinie 1140.3.1 von Microsoft](/legal/marketplace/certification-policies#114031-financial-transactions) und enthält Anleitungen zur Übermittlung von Finanzinformationen innerhalb der Teams-Benutzeroberfläche und benachrichtigt Entwickler über eingeschränkte Zahlungsszenarien auf der mobilen Version (Android und iOS) ihrer Teams-App.
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
* You can determine whether an account is active indefinitely or for a limited time. When the account expires the app must not show UI, text, or links indicating the need to pay.
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

Don't include domains outside of your organization's control (including wildcards) and tunneling services in your app's domain configurations. The following exceptions include:

* Wenn Ihre App die OAuthCard des Azure Bot Service verwendet, müssen Sie `token.botframework.com` als gültige Domäne angeben oder die Schaltfläche **Anmelden** funktioniert nicht.
* Wenn Ihre App auf SharePoint basiert, können Sie die zugehörige SharePoint-Stammsite mithilfe der Kontexteigenschaft `{teamSiteDomain}` als gültige Domäne einschließen.
* Verwenden Sie keine Domänen der obersten Ebene wie **.com**, **.in** und **.org** als gültige Domäne. [*Obligatorischer Fix*]

* Verwenden Sie " **.onmicrosoft.com" nicht oder** als gültige Domäne, für die **"onmicrosoft** " nicht unter Ihrer Kontrolle steht. Sie können **jedoch yoursite.com** als gültige Domäne verwenden, in der **Ihre Website** unter Ihrer Kontrolle steht, obwohl die Domäne einen Platzhalter enthält. [*Obligatorischer Fix*]

* Wenn Ihre App eine PowerApp ist, die auf der Microsoft Power Platform basiert, müssen Sie *apps.powerapps.com* als gültige Domäne einschließen, damit Ihre App in Teams barrierefrei und funktionsfähig ist.

</details>

### <a name="sensitive-content"></a>Vertraulicher Inhalt

[*Obligatorischer Fix*]

Ihre App darf keine sensiblen Daten wie Kreditkarten- oder Finanzdaten, Gesundheitsdaten, Kontaktinformationen oder andere persönlich identifizierbare Informationen (PII) an ein Publikum weitergeben, das den Inhalt nicht sehen soll.

Die App muss die Benutzer warnen, bevor sie Dateien oder ausführbare Dateien (.exe) auf den Computer oder in die Umgebung des Benutzers herunterlädt.

## <a name="general-functionality-and-performance"></a>Allgemeine Funktionalität und Leistung

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4](/legal/marketplace/certification-policies#11404-functionality).

* Anleitungen für die weitere Vorgehensweise sind sowohl für Administratoren als auch für vorhandene Benutzer obligatorisch. Sie können Wegweiser als Links hinzufügen, um sich zu registrieren, loszulegen, uns zu kontaktieren, Hilfelinks oder E-Mails zu senden.
* Das Aufrufen von Kontoabhängigkeiten oder Einschränkungen im Rahmen der App-Funktionalität ist nicht erforderlich, ist jedoch erforderlich, um es sowohl in der langen Manifestbeschreibung als auch in der AppSource-App-Auflistung hinzuzufügen.
* Sie müssen jede Abhängigkeit von Mandantenadministratoren für neue Benutzer herausrufen. Wenn keine Abhängigkeit besteht, ist es obligatorisch, eine Registrierung anzugeben, uns zu kontaktieren, einen Link zu den ersten Schritte oder eine E-Mail zu senden.

### <a name="launching-external-functionality"></a>Externe Funktionen starten

[*Obligatorischer Fix*]

Apps dürfen Benutzer für Kernbenutzerszenarien nicht aus Teams herausnehmen. App-Inhalte und -Interaktionen müssen im Rahmen von Teams-Funktionen wie Bots, adaptiven Karten, Registerkarten und Aufgabenmodulen erfolgen.
<br>
</br>

<details><summary>Erweitern, um mehr zu erfahren</summary>

* Verknüpfen Sie Benutzer innerhalb der Teams-App und nicht mit einer externen Website oder App. Für Szenarien, die externe Funktionen erfordern, muss Ihre Anwendung die ausdrückliche Erlaubnis des Benutzers einholen, um die Funktionen zu starten.

* Der UI-Text für Schaltflächen, die externe Funktionen starten, muss Inhalte enthalten, die anzeigen, dass der Benutzer die Teams-Instanz verlässt. Fügen Sie z. B. Text wie **„Hier geht es zu Contoso.com“** oder **„Ansicht in Contoso.com“** ein.

* Fügen Sie **das Popupsymbol** hinzu, um den Benutzern mitzuteilen, dass sie außerhalb von Teams navigiert werden. Sie können das Popupsymbol :::image type="icon" source="../../../../assets/icons/pop-out-icon.png" ::: rechts neben dem Link verwenden.

* Wenn Sie kein **Popupsymbol** hinzufügen können, können Sie eine der folgenden Optionen implementieren, um den Benutzer darüber zu informieren, dass er außerhalb von Teams navigiert wird:
  * Fügen Sie eine Notiz in der adaptiven Karte hinzu, die besagt, dass benutzer, wenn Sie **"Hilfe mit dieser App abrufen**" auswählen, den Benutzer außerhalb von Teams nehmen.
  * Hinzufügen von Interstitialdialogfeldern.

</details>

### <a name="compatibility"></a>Kompatibilität

[*Obligatorischer Fix*]

Die Apps müssen auf den neuesten Versionen der folgenden Betriebssysteme und Browser voll funktionsfähig sein:

* Microsoft Windows
* macOS
* Microsoft Edge
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
>
> * Sie müssen sicherstellen, dass die bereitgestellten Testkonten oder die Testumgebung dauerhaft gültig sind, d. h., bis die App auf dem kommerziellen Marketplace live ist.
> * Sie müssen die folgenden detaillierten Testanweisungen für die Überprüfung Ihrer App-Einreichung beifügen:
>
>   * **Schritte zum Konfigurieren der App-Testkonten** für den Fall, dass die App für die Authentifizierung auf externe Konten angewiesen ist.
>   * Zusammenfassung des **erwarteten App-Verhaltens** für die wichtigsten Workflows innerhalb Teams.
>   * **Beschreiben Sie Einschränkungen**, Bedingungen oder Ausnahmen der Funktionalität, Funktionen und Leistungen in der ausführlichen Beschreibung der App und den zugehörigen Materialien klar.
>   * **Hervorhebung aller Überlegungen** für Tester beim Überprüfen der App-Einreichung.
>   * Füllen Sie **die Testkonten vorab mit Dummy-Daten,** um die Tests zu unterstützen.
>   * Wenn Sie Ihre Testkonten bereitstellen, stellen Sie sicher, dass Sie die Integration von Drittanbietern aktivieren. Deaktivieren Sie außerdem die zweistufige oder mehrstufige Authentifizierung.

### <a name="app-manifest"></a>App-Manifest

[*Obligatorischer Fix*]

Das Manifest der Teams-App definiert die Konfiguration Ihrer App.

* Ihr Manifest muss einem öffentlich freigegebenen Manifest-Schema entsprechen. Weitere Informationen finden Sie in den[Manifest-Hinweisen.](~/resources/schema/manifest-schema.md) Reichen Sie Ihre App nicht mit einer Vorschauversion des Manifests ein.
* Wenn Ihre App eine Bot- oder Nachrichtenerweiterung enthält, müssen die Details im App-Manifest mit den Bot Framework-Metadaten übereinstimmen, einschließlich Bot-Name, Logo, Link zur Datenschutzerklärung und Link zu den Nutzungsbedingungen.
* Wenn Ihre App Azure Active Directory für die Authentifizierung verwendet, fügen Sie die Azure Active Directory (Azure AD)-Anwendungs-(Client-)ID in das Manifest ein. Weitere Informationen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md#webapplicationinfo)

### <a name="uses-of-latest-manifest-schema"></a>Verwendung des neuesten Manifestschemas

* Wenn Ihre App einmaliges Anmelden (Single Sign-On, SSO) verwendet, müssen Sie Microsoft Azure Active Directory (Azure AD)-ID im Manifest für die Benutzerauthentifizierung deklarieren. [*Obligatorischer Fix*]

* Sie müssen ein öffentlich veröffentlichtes Manifestschema verwenden. Sie können Ihr App-Paket aktualisieren, um eine öffentliche Version des Manifestschemas 1.10 oder höher zu verwenden. [*Obligatorischer Fix*]

* Wenn Sie ein App-Update übermitteln, erhöhen Sie nur die Versionsnummer der App. Die App-ID der aktualisierten App muss mit der App-ID der veröffentlichten App übereinstimmen. [*Obligatorischer Fix*]

* Das Vorhandensein zusätzlicher Dateien im App-Paket ist nicht akzeptabel. [*Obligatorischer Fix*]

* Die Versionsnummer muss im Manifestdateischema und im Manifestschema für zusätzliche Sprachen identisch sein. [*Obligatorischer Fix*]

* Sie müssen das Teams-Manifestschema version 1.5 oder höher verwenden, um Ihre App zu lokalisieren. Aktualisieren Sie das Attribut auf 1.5 oder höher, `$schema` um die App-Schemaversion 1.5 oder höher in Ihrer Datei manifest.json zu verwenden. Aktualisieren Sie die `manifestVersion` Eigenschaft auf `$schema` Version (in diesem Fall 1.5). [*Obligatorischer Fix*]

* Wenn Sie eine vorhandene Funktion hinzufügen, aktualisieren oder entfernen, Manifest- oder Partner Center-Metadaten hinzufügen, aktualisieren oder entfernen, müssen Sie die Versionsnummer der App erhöhen und das neue App-Manifest zur Überprüfung in Ihrem Partner Center-Konto übermitteln.

* Die Versionszeichenfolge muss dem SemVer-Standard (Semantic Versioning Specification, SemVer) (MAJOR) entsprechen. KLEINER. PATCH). [*Obligatorischer Fix*]

* Wenn Ihre App Administratoren dazu verpflichtet, Berechtigungen zu überprüfen und die Zustimmung im Teams Admin Center zu erteilen, müssen Sie dies im Manifest deklarieren `webapplicationinfo` . Wenn `webapplicationinfo` sie nicht im Manifest deklariert ist, wird die Seite **"Berechtigungen"** für Ihre App im Teams Admin Center als **...** [*Obligatorischer Fix*] angezeigt.

* Im Rahmen der Teams-App-Zertifizierung müssen Sie eine Produktionsversion des App-Manifests übermitteln. [*Obligatorischer Fix*]

* Es wird empfohlen, die Microsoft Partner Network (MPN)-ID im Manifest zu deklarieren. Die MPN-ID hilft dabei, die Partnerorganisation zu identifizieren, die die App erstellt. [*Vorgeschlagene Korrektur*]

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

Sie benötigen eine kurze und lange Beschreibung für Ihre App. Die Beschreibungen in Ihrer App-Konfiguration und im Partner Center müssen identisch sein.

:::image type="content" source="../../../../assets/images/submission/validation-app-description-adequete-information.png" alt-text="Die Grafik zeigt ein Beispiel für eine angemessene App-Beschreibung in der Teams-App.":::

:::image type="content" source="../../../../assets/images/submission/validation-app-description-inadequete.png" alt-text="Die Grafik zeigt ein fehlerhaftes Szenario für eine unzureichende App-Beschreibung.":::

<br></br>
<details><summary>Erweitern, um mehr zu erfahren</summary>

Beschreibungen dürfen nicht direkt oder durch Andeutungen eine andere Marke (von Microsoft oder anderen) verunglimpfen. Stellen Sie sicher, dass Ihre Beschreibung keine Ansprüche enthält, die nicht begründet werden können. Beispielsweise **garantierte Steigerung der Effizienz um 200 Prozent**.

* Die App-Beschreibung darf keine vergleichenden Marketinginformationen enthalten. Verwenden Sie z. B. keine Wettbewerbslogos oder Marken in der Angebotsliste, einschließlich Tags oder anderen Metadaten, die auf konkurrierende Angebote oder Marketplaces verweisen. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-comparitive-marketing-fail.png" alt-text="Die Grafik zeigt ein Beispiel für vergleichende Marketinginformationen in der App-Beschreibung.":::

* Linkkontaktdetails, erste Schritte, Hilfe oder Registrierung in der App-Beschreibung.

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-contact-deatils-hyperlinked.png" alt-text="Die Grafik zeigt ein Beispiel für Kontaktdetails, die in den App-Beschreibungen mit Links versehen sind.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-contact-deatils-not-hyperlinked.png" alt-text="Die Grafik zeigt ein Beispiel für Kontaktdetails, die in den App-Beschreibungen nicht mit Links versehen sind.":::

* Die App-Beschreibung muss die beabsichtigte Zielgruppe identifizieren, den eindeutigen und eindeutigen Wert kurz und deutlich erläutern, unterstützte Microsoft-Produkte und andere Software identifizieren und alle Voraussetzungen oder Anforderungen für die Verwendung enthalten. Bevor der Kunde Ihr Angebot erwirbt, müssen Sie alle Einschränkungen, Bedingungen oder Ausnahmen für die Funktionen, Features und Lieferungen klar beschreiben, wie in der Auflistung und den zugehörigen Materialien beschrieben. Die von Ihnen deklarierten Funktionen müssen sich auf die Kernfunktionen und die Beschreibung Ihres Angebots beziehen. [*Obligatorischer Fix*]

* Wenn Sie Ihren App-Namen aktualisieren, ersetzen Sie den alten App-Namen in den Angebotsmetadaten im Manifest, in AppSource und ggf. durch einen neuen App-Namen. [*Obligatorischer Fix*]

* Einschränkungen und Kontoabhängigkeiten müssen in der Manifest-App-Beschreibung, in AppSource und im Partner Center aufgerufen werden. Beispiel:
  * Unternehmenskonto
  * Kostenpflichtiges Abonnement
  * Eine andere Lizenz oder ein anderes Konto
  * Sprache
  * PSTN-Wählhilfe (Public Switched Telephone Network)
  * Regionale Abhängigkeit
  * Vorlaufzeit für die Buchung von Übersetzern oder Live-Agenten
  * Rollenbasierte Funktionalität
  * Abhängigkeit von nativer App

  :::image type="content" source="../../../../assets/images/submission/validation-app-description-limitations-calledout-pass.png" alt-text="Die Grafik zeigt ein Beispiel für Einschränkungen, die in der App-Beschreibung genannt werden.":::
  
  :::image type="content" source="../../../../assets/images/submission/validation-app-description-limitations-not-calledout-fail.png" alt-text="Die Grafik zeigt ein Beispiel für Einschränkungen, die in App-Beschreibungen nicht genannt werden.":::

* Wenn Ihre App für bestimmte Regionen oder geografische Standorte unterstützt wird, müssen Sie diese bestimmte Regionsabhängigkeit in der App-Beschreibung in Manifest, Partner Center und AppSource für dieses Angebot angeben.

* Wenn Sie auf Teams verweisen müssen, schreiben Sie den ersten Verweis im App-Eintrag als Microsoft Teams. Spätere Verweise können auf Teams-verkürzt werden.

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-teams-reference-pass.png" alt-text="Die Grafik zeigt ein Beispiel für einen korrekten Verweis auf Teams in der App-Beschreibung.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-teams-reference-fail.png" alt-text="Die Grafik zeigt ein Beispiel für einen falschen Verweis auf Teams in der App-Beschreibung.":::

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

* Stellen Sie sicher, dass die App-Beschreibung mit den in der Teams-App verfügbaren Funktionen übereinstimmt. Jeder Verweis auf Arbeitsabläufe außerhalb der Teams-App muss begrenzt sein und sich deutlich von den Funktionen der Teams-App abheben.

* Fügen Sie einen Hilfe- oder Support-Link hinzu.

* Verweisen Sie auf **Microsoft 365** anstelle von **Office 365**.

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

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-microsoft-abbreviated.png" alt-text="Die Grafik zeigt ein Beispiel für die erstmalige Abkürzung von Microsoft als MS oder MSFT in der App-Beschreibung.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-microsoft-not-abbreviated.png" alt-text="Die Grafik zeigt ein Beispiel dafür, dass Microsoft in der App-Beschreibung nicht zum ersten Mal als MS oder MSFT abgekürzt wird.":::

* Geben Sie an, dass es sich bei der App um ein Angebot von Microsoft handelt, einschließlich der Verwendung von Microsoft-Slogans oder Leitsätzen.

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-offering-from-microsoft.png" alt-text="Die Grafik zeigt ein Beispiel dafür, wie Microsoft-Angebote nicht in der App-Beschreibung angegeben werden.":::

   :::image type="content" source="../../../../assets/images/submission/validation-app-description-no-offering-indication-from-microsoft.png" alt-text="Grafik, die ein Beispiel für das Schreiben einer App-Beschreibung ohne Verwendung von Microsoft-Slogans und -Taglines zeigt.":::

* Die Verwendung folgender Sprache, es sei denn, Sie sind ein zertifizierter Microsoft-Partner:
  * **... zertifiziert für ...**
  * **... unterstützt von ...**
* Tippfehler, Grammatikfehler einschließen.
* Unnötigerweise wird das gesamte Manifest oder die lange Beschreibung oder der AppSource-Inhalt groß geschrieben.

   :::image type="content" source="../../../../assets/images/submission/validation-long-description-typos-pass.png" alt-text="Die Grafik zeigt ein Beispiel für eine lange App-Beschreibung ohne Fehler.":::

   :::image type="content" source="../../../../assets/images/submission/validation-long-description-typos-fail.png" alt-text="Die Grafik zeigt ein Beispiel für eine lange App-Beschreibung mit Tippfehlern und Fehlern.":::

* Links zu AppSource einschließen.

  :::image type="content" source="../../../../assets/images/submission/validation-app-description-link-to-appsource.png" alt-text="Die Grafik zeigt ein Beispiel für ein Fail-Szenario mit Links zu AppSource in einer langen App-Beschreibung.":::

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

* Focus on your app's capabilities. For example, how people can communicate with your bot.
* Fügen Sie Inhalte ein, die Ihre App genau darstellen.
* Verwenden Sie Text mit Bedacht.
* Rahmen Sie Screenshots mit einer Farbe, die Ihre Marke widerspiegelt und Marketinginhalte enthält.
* Verwenden Sie hochauflösende Screenshots, die scharf sind und lesbaren und klar lesbaren Text enthalten. [*Obligatorischer Fix*]
* Verwenden Sie Modelle, die die tatsächliche Benutzeroberfläche der App zum Nutzen der Endbenutzer genau darstellen. [*Obligatorischer Fix*]
* Stellen Sie mindestens drei Screenshots im Marketplace-Eintrag Ihrer App bereit.
* Wenn Ihre Teams-App auf andere Microsoft 365-Hubs erweiterbar ist, müssen die bereitgestellten Screenshots die App-Funktionalität in anderen Microsoft 365-Hubs darstellen.
* Mindestens ein Screenshot muss die Funktionalität Ihrer App auf mobilen Geräten darstellen.
* Es wird empfohlen, in Ihren Screenshots Beschriftungen bereitzustellen, damit der Benutzer die App-Funktion klar verstehen kann.

**Was Sie nicht tun sollten:**

* Schließen Sie Modelle ein, die die tatsächliche Benutzeroberfläche Ihrer App ungenau widerspiegeln, z. B. die Anzeige ihrer App, die außerhalb von Teams verwendet wird.

> [!TIP]
>
> * Ein Video kann die effektivste Methode sein, um zu kommunizieren, warum Benutzer Ihre App verwenden sollten. Ein Video ist auch das erste, was Benutzern in Ihrem Eintrag angezeigt wird.
> * Wenn Sie in Ihrem App-Eintrag ein Video bereitstellen möchten, müssen Sie die Anzeigen in den YouTube- oder Vimeo-Einstellungen deaktivieren, bevor Sie den Videolink im Partner Center übermitteln. Im App-Eintrag bereitgestellte Videos dürfen nicht länger als 90 Sekunden sein und dürfen nur die App-Funktionalität und -Integration in Microsoft Teams darstellen. Weitere Informationen finden Sie unter [Video für Ihren Store-Eintrag erstellen](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#create-a-video).

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

* Wenn Ihre App Lokalisierung unterstützt, muss Ihr App-Paket eine Datei mit Sprachübersetzungen enthalten, die basierend auf der Spracheinstellung von Teams angezeigt werden. Die Datei muss dem Lokalisierungsschema von Teams entsprechen. Weitere Informationen finden Sie unter [Teams-Lokalisierungsschema](~/concepts/build-and-test/apps-localization.md).

* App-Metadateninhalte müssen in und in `en-us` anderen Lokalisierungssprachen identisch sein. [*Obligatorischer Fix*]

* Unterstützte Sprachen müssen in der AppSource-App-Beschreibung angezeigt werden. Diese App ist beispielsweise in X (X= lokalisierte Sprache) verfügbar. [*Obligatorischer Fix*]

* Wenn die Clienteinstellungen des Benutzers keiner ihrer zusätzlichen Sprachen entsprechen, wird die Standardsprache als letzte Fallbacksprache verwendet. Aktualisieren Sie die `localizationInfo` Eigenschaft mit der richtigen Standardsprache, die ihre Anwendung unterstützt. [*Obligatorischer Fix*]

* Aktualisieren Sie die `localizationInfo` Eigenschaft mit der richtigen Standardsprache, die Ihre Anwendung unterstützt, oder fügen Sie lokalisierte Inhalte für manifest und Partner Center lange und kurze Beschreibung hinzu. [*Obligatorischer Fix*]

## <a name="apps-linked-to-saas-offer"></a>Apps, die mit dem SaaS-Angebot verknüpft sind

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für den kommerziellen Marktplatz Nr. 1140.5](/legal/marketplace/certification-policies?branch=pr-en-us-5673). Wenn Sie eine Teams-App erstellen, die mit einem SaaS-Angebot verknüpft ist, stellen Sie sicher, dass sie diesen Richtlinien entspricht.
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
* Stellen Sie verschiedene Möglichkeiten bereit, um sich mit Support für Probleme zu befassen, z. B. häufig gestellte Fragen (FAQ), Wissensdatenbank und E-Mail.
* Überprüfen Sie die Benutzer, um sicherzustellen, dass ihnen nicht bereits eine Lizenz durch einen anderen Benutzer zugewiesen wurde.
* Benutzer nach der Lizenzzuweisung benachrichtigen.
* Führen Sie Benutzer dazu, wie Sie die App zu Teams hinzufügen und mithilfe von Teams-Chat-Bots oder -E-Mails beginnen können.

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

Wenn die Einrichtung Ihrer App zu Testzwecken komplex ist, stellen Sie ein End-to-End-Funktionsdokument bereit, verknüpfte SaaS-Angebote bieten Konfigurationsschritte und Anweisungen für die Lizenz- und Benutzerverwaltung als Teil Ihrer *Hinweise zur Zertifizierung*.

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

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-new-user.png" alt-text="Die Grafik zeigt ein Beispiel für tab mit einer Sackgasse beim Setup.":::

* Der Benutzer darf die Registerkartenkonfigurationsoberfläche nicht in Teams verlassen, um Inhalte außerhalb von Teams zu erstellen und dann zu Teams zurückzukehren, um ihn anzuheften. Der Konfigurationsbildschirm der Registerkarte muss den Wert der Konfiguration erläutern und wie sie durchgeführt wird. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-profile-name.png" alt-text="validation-tabs-set-up-profile-name":::

* Tab configuration screen must not embed an entire website. Keep your configuration experience focused. For example, if you're building a project management app that lets users configure a project in a channel, keep the tab configuration screen focused on allowing the user to select a project from your app to configure in the channel. [*Mandatory Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-experience.png" alt-text="validation-tabs-setup-configuration-exp":::

    :::image type="content" source="../../../../assets/images/submission/validation-tabs-setup-configuration-screen.png" alt-text="validation-tabs-set-up-configuration-screen":::

* Apps, für die Benutzer beim Konfigurieren einer Registerkarte eine URL eingeben müssen, müssen:
  * Stellen Sie eine geeignete Anleitung für die Zukunft bereit, mit der der Benutzer die URL erwerben oder generieren kann. [*Obligatorischer Fix*]
  * Überprüfen Sie gemäß der App-Beschreibung, ob die URL relevant oder für die Funktionalität der App geeignet ist. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-tab-configuration-way-forward-url-pass.png" alt-text="Der Screenshot zeigt ein Beispiel für die Registerkartenkonfiguration mit einer Möglichkeit für Benutzer, eine URL zu generieren.":::
  
    :::image type="content" source="../../../../assets/images/submission/validation-tab-configuration-way-forward-url-fail.png" alt-text="Screenshot zeigt ein Beispiel für die Registerkartenkonfiguration, ohne dass der Benutzer eine URL generieren kann.":::

* Link zu den Kontaktinformationen auf dem Konfigurationsbildschirm anstelle von Nur-Text, um Benutzern zu helfen, sie für Supportanforderungen zu kontaktieren. [*Obligatorischer Fix*]

* Für eine nahtlose Benutzererfahrung beim ersten Ausführen empfehlen wir, dass Sie ihre Support-URL oder E-Mail-Adresse auf dem Konfigurationsbildschirm verlinken. [*Vorgeschlagene Korrektur*]

</details>
</br>

<details><summary>Ansichten</summary>

* The sign in screen area must not use large logos. [*Mandatory Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-applogin.png" alt-text="validation-views-app-login":::

* Inhalte können vereinfacht werden, indem sie auf mehrere Registerkarten verteilt werden.

    :::image type="content" source="../../../../assets/images/submission/validation-views-multiple-tabs.png" alt-text="val-views-multiple-tabs":::

* Registerkarten sollten keine doppelte Kopfzeile haben. Entfernen Sie doppelte Logos aus dem I-Frame, da das Registerkartenframework bereits das App-Symbol und den Namen anzeigt. [*Vorgeschlagene Korrektur*]

    :::image type="content" source="../../../../assets/images/submission/validation-views-no-duplicate-header-logo.png" alt-text="Die Grafik zeigt ein Beispiel für eine Registerkarte ohne doppelte Kopfzeilen und Logos.":::

    :::image type="content" source="../../../../assets/images/submission/validation-views-duplicate-header-logo.png" alt-text="Die Grafik zeigt ein Beispiel für eine Registerkarte mit doppelten Kopfzeilen und Logos.":::

</details>
</br>

<details><summary>Navigation</summary>

Im Folgenden sind die Navigationsrichtlinien aufgeführt:

* Registerkarten dürfen keine Navigation bereitstellen, die in Konflikt mit der primären Teams-Navigation steht. Wenn Sie eine linke Navigation auf der Registerkarte bereitstellen, darf sie nicht nur Symbole oder Symbole mit gestapeltem Text enthalten. Es darf sich nicht um eine zusammenklappbare Leiste mit der Möglichkeit handeln, Symbole mit gestapeltem Text zu sehen (wie bei der Teams-Navigationsleiste). Fügen Sie Icons mit Inline-Text oder nur Text ein oder verwenden Sie Hamburger-Menüs anstelle der linken Tabulatorleiste. [*Obligatorischer Fix*]

Entwerfen Sie Ihre App mit [einfachen](~/concepts/design/design-teams-app-basic-ui-components.md) und [erweiterten](~\concepts\design\design-teams-app-advanced-ui-components.md) Fluent UI-Komponenten.

:::image type="content" source="../../../../assets/images/submission/validation-navigation-static-tab.png" alt-text="Die Grafik zeigt ein Beispiel für die Navigation auf einer Registerkarte, die nicht mit der primären Teams-Navigation in Konflikt ist.":::

:::image type="content" source="../../../../assets/images/submission/validation-navigation-left-navigation.png" alt-text="Die Grafik zeigt ein Beispiel für die linke Navigationsleiste, die mit der primären Teams-Navigation in Konflikt steht.":::

* Registerkarten mit Symbolleiste in der linken Leiste müssen einen Abstand von 20 Pixeln von der linken Team-Navigation lassen. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-spacing-between-toolbar.png" alt-text="validation-nav-spacing-between-toolbar":::

* Die sekundären und tertiären Seiten in einer Registerkarte müssen in einer Ansicht der Ebene 2 (L2) und der dritten Ebene (L3) im Hauptregisterkartenbereich geöffnet werden, die über Breadcrumbs oder die linke Navigation navigiert wird. Sie können auch die folgenden Komponenten verwenden, um die Navigation auf einer Registerkarte zu unterstützen:
  * Zurück-Schaltflächen
  * Seitenüberschriften
  * Hamburger-Menüs

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-improper-navigation-leveles.png" alt-text="Screenshot, der ein Beispiel für ein Besprechungsdialogfeld mit mehreren Navigationsebenen zeigt.":::

* Deeplinks in Registerkarten dürfen nicht auf eine externe Webseite verweisen, sondern nur innerhalb von Teams. Zum Beispiel Aufgabenmodule oder andere Registerkarten. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-view-button-not-linked-static-tab.png" alt-text="validation-nav-view-button-not-linked-static-tab":::

* Registerkarten dürfen Benutzern nicht erlauben, außerhalb Teams zu navigieren, um die Hauptanwendung zu nutzen. Registerkarten können für nicht zum Kerngeschäft gehörende Arbeitsabläufe außerhalb von Teams umgeleitet werden. Zum Beispiel, um ein Supportticket zu erstellen. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-within-configuration.png" alt-text="validation-nav-core-workflow-within-configuration":::

    :::image type="content" source="../../../../assets/images/submission/validation-navigation-core-workflow-redirects-outside.png" alt-text="validation-nav-core-workflow-redirects-outside":::

* Der horizontale Bildlauf darf nicht auf einer Registerkarte in der Besprechung vorhanden sein. [*Obligatorische Korrektur*]

* In Besprechungsdialogfeldern, die in Ihrer App verwendet werden, darf kein horizontaler Bildlauf zulässig sein. Verwenden Sie In-Meeting-Dialoge sparsam und für Szenarien, die leicht und aufgabenorientiert sind. Sie können die Breite des I-Frames des Besprechungsdialogfelds innerhalb des unterstützten Größenbereichs angeben, um unterschiedliche Szenarien zu berücksichtigen. [*Obligatorischer Fix*]
* Aufgabenmodule, die in Ihrer App verwendet werden, dürfen kein horizontales Scrollen zulassen. Mit Aufgabenmodulen können Sie verschiedene Größen auswählen, um den Inhalt reaktionsfähig zu machen, ohne dass ein horizontaler Bildlauf erforderlich ist. Bei Bedarf können Sie eine Phasenansicht (eine Vollbild-UI-Komponente zum Anzeigen von Webinhalten) verwenden, um den Workflow ohne horizontalen Bildlauf abzuschließen. [*Obligatorischer Fix*]

* Ein horizontaler Bildlauf, der auf der Registerkarte in einem persönlichen Chat, Kanal und in einer Besprechungsdetails-Registerkarte in einem beliebigen Bereich vorhanden ist, ist nicht zulässig, wenn der gesamte Registerkartenbereich scrollbar ist, es sei denn, Ihre Registerkarte verwendet einen unendlichen Zeichenbereich mit festen UI-Elementen. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-allowed-scenarios.png" alt-text="Die Grafik zeigt Beispiele für alle Szenarien auf mobilgeräten, in denen ein horizontaler Bildlauf zulässig ist.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-allowed-kanban.png" alt-text="Die Grafik zeigt ein Beispiel für einen horizontalen Bildlauf im Kanban-Board.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-list-view-components.png" alt-text="Die Grafik zeigt ein Beispiel für die Listenansicht mit vielen Komponenten.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-fixed-board.png" alt-text="Die Grafik zeigt ein Beispiel für einen horizontalen Bildlauf auf einem Whiteboard mit unendlichem Zeichenbereich und festem Board.":::

   :::image type="content" source="../../../../assets/images/submission/validation-horizontal-scroll-in-list-view.png" alt-text="Die Grafik zeigt ein Beispiel für einen horizontalen Bildlauf in der Listenansicht.":::

* Der horizontale Bildlauf in adaptiven Karten darf in Teams nicht vorhanden sein. [*Obligatorischer Fix*]

* Die untere Schiene, die für die Navigation in Registerkarten verwendet wird, darf nicht mit der systemeigenen Mobilen App-Navigation von Teams in Konflikt kommen. [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-tab-bottom-rail-conflicts-with-teams-mobile.png" alt-text="Die Grafik zeigt ein Beispiel für eine Registerkarte, die in Konflikt mit der systemeigenen Mobilen App-Navigation von Teams steht.":::

</details>
</br>

<details><summary>Benutzerfreundlichkeit</summary>

* Registerkarten müssen einen Wert bereitstellen, der über das Hosten einer vorhandenen Website hinausgeht. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-provides-workflows.png" alt-text="Die Grafik zeigt ein Beispiel für eine App mit einem Workflow, der für Kanalmitglieder innerhalb eines Teams nützlich ist.":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-website-i-framed.png" alt-text="Die Grafik zeigt ein Beispiel für eine App mit der gesamten Website in einem I-Frame ohne Zurück-Option.":::

* Der Inhalt darf innerhalb der Registerkarte nicht abgeschnitten werden oder sich überschneiden.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-content-truncation.png" alt-text="validation-usability-content-truncations":::

* Benutzer müssen in der Lage sein, ihre letzte Aktion auf der Registerkarte rückgängig zu machen.

* Registerkarten in einem persönlichen Kontext können Inhalte von freigegebenen Instanzen der App aggregieren. So muss beispielsweise eine Projektmanagement-App mit einer konfigurierbaren Registerkarte, die es Kanalmitgliedern ermöglicht, das Projekt auf Kanban-Karten zu kommentieren, diese Inhalte zusammenfassen und in der persönlichen App anzeigen. [*Vorgeschlagene Korrektur*]

* Registerkarten müssen für Teams-Designs reaktionsfähig sein. Wenn ein Benutzer das Design ändert, muss das Design der App die Auswahl widerspiegeln.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-responsive-tabs.png" alt-text="Die Grafik zeigt ein Beispiel für eine Registerkarte, die auf ein Design in Teams reagiert.":::

    :::image type="content" source="../../../../assets/images/submission/validation-usability-unresponsive-tabs.png" alt-text="Die Grafik zeigt ein Beispiel für eine Registerkarte, die nicht auf designs in Teams reagiert.":::

* Registerkarten müssen teamsstilisierte Komponenten wie Teams-Schriftarten, Typhierarchien, Farbpaletten, Rastersystem, Bewegung, Tonfall, wann immer möglich verwenden. Weitere Informationen finden Sie in den [Richtlinien für das Registerkartendesign.](/microsoftteams/platform/tabs/design/tabs) [*Vorgeschlagene Korrektur*]

    :::image type="content" source="../../../../assets/images/submission/validation-usability-app-uses-diff-font.png" alt-text="Screenshot zeigt ein Beispiel für eine Registerkarte mit Calibri-Schriftart anstelle der nativen Teams-Schriftart.":::

* Wenn Ihre App-Funktionalität Änderungen an den Einstellungen erfordert, fügen Sie eine **Registerkarte „Einstellungen“** ein. [*Vorgeschlagene Korrektur*]
* Registerkarten müssen dem Teams-Interaktionsdesign folgen, z. B. Seitennavigation, Position und Verwendung von Dialogfeldern, Informationshierarchien. Weitere Informationen finden Sie im [Microsoft Teams Fluent UI Kit](~/concepts/design/design-teams-app-basic-ui-components.md).

* Registerkartenfunktionen müssen auf Mobilgeräten (Android und iOS) vollständig responsiv sein.

   > [!TIP]
   >
   > * Fügen Sie einen persönlichen Bot neben einer persönlichen Registerkarte ein.
   > * Erlauben Sie Benutzern, Inhalte von ihrer persönlichen Registerkarte zu teilen.

* Die Registerkarte darf keine Elemente enthalten, die Workflows innerhalb der Registerkarte vollständig behindern oder behindern. Beispiel: Bot innerhalb einer Registerkarte, die nicht minimiert werden kann.

   :::image type="content" source="../../../../assets/images/submission/validation-tab-elements-impede-workflow.png" alt-text="Die Grafik zeigt ein Beispiel für eine Registerkarte mit Elementen, die Workflows innerhalb der Registerkarte behindern.":::

* Die Registerkarte darf keine fehlerhafte Funktionalität aufweisen. Ihr Angebot muss eine verwendbare Softwarelösung sein und die Funktionen, Features und Lieferumfang bereitstellen, wie in Ihrem Eintrag und anderen verwandten Materialien beschrieben. [*Obligatorischer Fix*]

* Wenn Ihre Registerkarten eine Fußzeile enthalten, stellen Sie sicher, dass Sie alle Links, die nicht mit der App-Funktionalität zusammenhängen, aus der Fußzeile entfernen.

</details>
</br>

<details><summary>Bereichsauswahl</summary>

* Inhalte auf der Landing Page von konfigurierbaren Registerkarten dürfen nicht auf die individuelle Verwendung beschränkt sein und dürfen keine persönlichen Inhalte wie **Meine Aufgaben** oder **Mein Dashboard** enthalten.

   :::image type="content" source="../../../../assets/images/submission/validation-configurable-tab-content-personal-scope.png" alt-text="Die Grafik zeigt ein Beispiel für Inhalte auf einer konfigurierbaren Registerkarte mit persönlichem Bereich wie &quot;Meine Aufgaben&quot; oder &quot;Mein Dashboard&quot;.":::

* Nach der Konfiguration muss auf der Startseite eine Ansicht für die Zusammenarbeit für das gesamte Team angezeigt werden.

* Wenn Ihre App die Bereitstellung einer persönlichen Bereichsansicht für den Benutzer erfordert, um die Effizienz oder Produktivität am Arbeitsplatz zu steigern, verwenden Sie gefilterte Ansichten, Deep Links zu persönlichen Apps oder navigieren Sie auf der konfigurierbaren Registerkarte zu L2- oder L3-Ansichten, und halten Sie die Zielseite für alle Benutzer kontextbezogen gleich.

* Der Inhalt der Landing Page der konfigurierbaren Tabs muss für alle Mitglieder des Channels kontextuell gleich sein.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-tab-personal-info.png" alt-text="Die Grafik zeigt ein Beispiel für Inhalte auf der Startseite der konfigurierbaren Registerkarten, die für alle Mitglieder kontextabhängig unterschiedlich sind.":::

* Konfigurierbare Registerkarten müssen über eine gezielte Funktionalität verfügen.

    :::image type="content" source="../../../../assets/images/submission/validation-usability-configurable-nested-tabs.png" alt-text="validation-usability-configurable-nested-tab":::

</details>
<br/>

## <a name="bots"></a>Bots

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.3](/legal/marketplace/certification-policies#114043-bots).

Wenn Ihre App einen Bot enthält, stellen Sie sicher, dass diese Richtlinien eingehalten werden.

> [!TIP]
> Weitere Informationen zum Erstellen eines qualitativ hochwertigen App-Erlebnisses finden Sie unter [Entwurfsrichtlinien für Teams-Bots](~/bots/design/bots.md).

</br>
<details><summary>Bot-Entwurfsrichtlinien</summary>

* Ihre Teams-App muss den [Entwurfsrichtlinien für Teams-Bots](../../../../bots/design/bots.md) entsprechen.

* Sie müssen ein Aufgabenmodul implementieren, um eine Multi-Turn-Bot-Antwort zu vermeiden, wenn der Workflow den Benutzer dazu bringt, sich wiederholende Aufgaben auszuführen. Verwenden Sie z. B. ein Aufgabenmodul, um namen, dob, place und designation wiederholt zu erfassen, anstatt Unterhaltungen mit mehreren Drehungen zu verwenden. [*Obligatorischer Fix*]

* Fehlerhafte Links, Antworten oder Workflows in Ihrer App müssen behoben werden. [*Obligatorischer Fix*]

</details>

</br>
<details><summary>Bot-Befehle</summary>

Analyzing user input and predicting user intent is difficult. Bot commands provide users a set of words or phrases for your bot to understand.

* Sie müssen mindestens einen unterstützten Bot-Befehl im `{commandList}` Abschnitt Ihres App-Manifests auflisten. Diese Befehle werden im Feld zum Verfassen angezeigt, wenn ein Benutzer versucht, Ihrem Bot eine Nachricht zu senden.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-listed.png" alt-text="Die Grafik zeigt ein Beispiel für Bot-Befehle, die im App-Manifest aufgeführt sind.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-not-listed.png" alt-text="Die Grafik zeigt ein Beispiel für Bot-Befehle, die nicht im App-Manifest aufgeführt sind.":::

* Alle Befehle, die Ihr Bot unterstützt, müssen ordnungsgemäß funktionieren, einschließlich generischer Befehle wie **Hi**, **Hello** und **Help**.
  
  :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-generic-response-pass.png" alt-text="Die Grafik zeigt ein Beispiel für die Reaktion des Bots auf generische Befehle.":::

  :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-generic-no-response.png" alt-text="Die Grafik zeigt ein Beispiel für einen Bot ohne Antwort auf generische Befehle.":::

* Bot-Befehle dürfen einen Benutzer nicht in eine Sackgasse führen, die Befehle müssen immer einen Weg nach vorn weisen.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-deadend.png" alt-text="validation-bot-commands-dead-end":::

* Sie müssen mindestens einen gültigen Bot-Befehl im `items.commands.title` Abschnitt des Manifests auflisten und eine geeignete Beschreibung hinzufügen, die dem Benutzer Klarheit über den Botbefehl und dessen Verwendung gibt. Bot-Befehle, die `commandLists` im Abschnitt der Manifestoberfläche als vorgefüllte Befehle im Bot-Befehlsmenü aufgeführt sind, bieten dem neuen Benutzer eine Möglichkeit, mit dem Bot zu interagieren. [*Obligatorischer Fix*]

* Bot-Antworten dürfen keine offiziellen Microsoft-Produktbilder oder Avatare enthalten. Verwenden Sie Ihre eigenen Ressourcen in Ihrer App. Die Verwendung von Microsoft-Produktbildern in Ihrer App ist nicht zulässig. Sie dürfen urheberrechtlich geschützte Produktbilder von Microsoft nur kopieren, ändern, verteilen, anzeigen, lizenzieren oder verkaufen, wenn Ihnen innerhalb des End-User Lizenzvertrags( EULA), lizenzbedingungen, die den Inhalt begleiten, oder in den [Microsoft-Marken- und Markenrichtlinien](https://www.microsoft.com/legal/intellectualproperty/trademarks) ausdrückliche Erlaubnis erteilt wird. [*Obligatorischer Fix*]

* Bots müssen auf Benutzerbefehle reagieren, ohne einen Indikator für das kontinuierliche Laden anzuzeigen. [*Obligatorischer Fix*]

* Die Befehlsantwort der Bot-Hilfe darf den Benutzer nicht außerhalb von Teams umleiten. Die Antwort auf Bot-Hilfebefehle kann Benutzer zu einer Canvas in der Teams-App umleiten oder eine Möglichkeit bieten, auf eine adaptive Karte zu reagieren. [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-bot-redirects-user-outside-teams.png" alt-text="Die Grafik zeigt ein Beispiel für eine Botantwort, die Benutzer außerhalb von Teams umleitet.":::

* Bots müssen immer eine gültige Antwort auf eine Benutzereingabe bereitstellen, auch wenn die Eingabe irrelevant oder unsachgemäß ist. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-valid-improper-input.png" alt-text="Die Grafik zeigt ein Beispiel für eine gültige Antwort auf nicht ordnungsgemäßen Bot-Befehl.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-improper-response-invalid-command.png" alt-text="Die Grafik zeigt ein Beispiel für eine ungültige Antwort für nicht ordnungsgemäßen Bot-Befehl.":::

* Sonderzeichen wie Schrägstrich (**/**) dürfen bot-Befehlen nicht vorangestellt werden. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-commands-special-characters.png" alt-text="Die Grafik zeigt ein Beispiel für ein fehlerhaftes Szenario, in dem Sonderzeichen Bot-Befehlen vorangestellt werden.":::

* Bots müssen eine gültige Antwort auf ungültige Benutzerbefehle bereitstellen. Bots dürfen dem Benutzer kein Dead-End zuweisen oder einen Fehler anzeigen, wenn ein Benutzer einen ungültigen Bot-Befehl sendet. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-way-forward-for-invalid-command.png" alt-text="Die Grafik zeigt ein Beispiel dafür, wie ein Bot einen Weg nach vorne für einen ungültigen Befehl bereitstellt.":::

   :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-bot-dead-end-invalid-command.png" alt-text="Die Grafik zeigt ein Beispiel für ein fehlerhaftes Szenario, in dem ein Bot dieselbe Antwort für einen gültigen und ungültigen Befehl sendet.":::

* Die Bot-Funktionalität muss für den Bereich relevant sein, in dem der Bot installiert ist, und der Bot muss einen Wert im installierten Bereich bereitstellen. [*Obligatorischer Fix*]

* Bots dürfen keine doppelten Befehle enthalten. [*Obligatorischer Fix*]

* Bots dürfen keinen Eingabeindikator anzeigen, nachdem sie auf den Benutzerbefehl reagiert haben, sie können jedoch eine Eingabeanzeige anzeigen, während sie auf den Benutzerbefehl reagieren. [*Obligatorischer Fix*]

* Bots müssen eine gültige Antwort auf den in Klein- oder Großbuchstaben eingegebenen **Hilfebefehl** bereitstellen, der dem Benutzer eine Möglichkeit bietet, vorwärts zu gehen oder dem Benutzer den Zugriff auf die Hilfeinhalte im Zusammenhang mit der Bot-Nutzung zu ermöglichen. Bots müssen auch dann eine gültige Antwort bereitstellen, wenn sich der Benutzer nicht bei der App angemeldet hat. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-valid-response-lowercase.png" alt-text="Die Grafik zeigt ein Beispiel dafür, dass ein Bot keine gültige Antwort für einen Befehl in Klein- oder Großbuchstaben bereitstellt.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-valid-response-logged-app.png" alt-text="Die Grafik zeigt ein Beispiel für einen Bot ohne gültige Antwort, wenn sich der Benutzer nicht bei der App angemeldet hat.":::

* Bots müssen eine gültige Antwort auf den **Hilfebefehl** bereitstellen.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-help-command.png" alt-text="Die Grafik zeigt ein Beispiel für das Senden einer gültigen Antwort auf den Hilfebefehl durch den Bot.":::

* Bot-Antworten auf Mobilgeräten müssen reaktionsfähig sein, ohne dass Daten abgeschnitten werden, die die Bot-Nutzung des Endbenutzers behindern, um die gewünschten Workflows abzuschließen. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-no-truncate-mobile.png" alt-text="Die Grafik zeigt ein Beispiel für eine Bot-Nachricht, ohne auf mobilen Geräten abgeschnitten zu werden.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-response-truncate-mobile.png" alt-text="Die Grafik zeigt ein Beispiel für eine Bot-Nachricht, die auf mobilen Geräten abgeschnitten wird.":::

* Alle Links in einer adaptiven Botantwortkarte müssen reaktionsfähig sein. Jeder Link, der den Benutzer außerhalb der Teams-Plattform führt, muss über einen klaren Umleitungstext verfügen, z. B. **"Anzeigen in".** oder **"This way to.."**, ein Popupsymbol in der Interaktiven Schaltfläche "Bot-Antwort" oder einen geeigneten Umleitungstext im Textkörper der Bot-Antwortnachricht enthalten. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-action-button-redirect-warning.png" alt-text="Die Grafik zeigt ein Beispiel für die Interaktive Schaltfläche &quot;Bot-Antwort&quot; mit einer Umleitung.":::

* Wenn Ihr Bot standardmäßig keinen Benutzerbefehl antwortet oder unterstützt und ein Uni-Bot ist, der nur Benutzer benachrichtigen soll. Sie müssen im Manifest auf "true" festlegen `isNotificationOnly` . [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-bot-command-isnotification-only-true.png" alt-text="Die Grafik zeigt ein Beispiel für eine Benachrichtigungseigenschaft, die im App-Manifest auf &quot;true&quot; festgelegt ist.":::

  :::image type="content" source="../../../../assets/images/submission/validation-bot-command-isnotification-only-not-true.png" alt-text="Die Grafik zeigt ein Beispiel dafür, dass nur der Bot einer Benachrichtigung nicht auf die Nachricht eines Benutzers reagiert.":::

* Die Benutzererfahrung von Bots darf auf mobilen Plattformen nicht unterbrochen werden. Ihr Bot muss auf Mobilgeräten vollständig reaktionsfähig sein. [*Obligatorischer Fix*]

> [!TIP]
> Fügen Sie für persönliche Bots eine Registerkarte **Hilfe** hinzu, die genauer beschreibt, was Ihr Bot tun kann.

</details>
</br>

<details><summary>Bot-Begrüßungsnachrichten</summary>

* Wenn die App einen komplexen Konfigurationsablauf hat (erfordert eine Unternehmenslizenz oder hat keinen intuitiven Anmeldeablauf), dann müssen Bots in solchen Apps beim ersten Durchlauf immer eine Willkommensnachricht senden.

  Für eine optimale Benutzererfahrung muss die Willkommensnachricht den Wert enthalten, den der Bot Benutzern bietet, die den Bot im Kanal installiert haben, wie der Bot konfiguriert wird, und alle unterstützten Bot-Befehle kurz beschreiben. Sie können die Begrüßungsnachricht mithilfe einer adaptiven Karte mit Schaltflächen anzeigen, um die Benutzerfreundlichkeit zu verbessern. Weitere Informationen finden Sie unter [Auslösen einer Bot-Begrüßungsnachricht.](~/bots/how-to/conversations/send-proactive-messages.md) Für Apps ohne komplexen Konfigurationsablauf können Sie während der ersten Ausführung des Bots eine Willkommensnachricht auslösen. Wenn jedoch eine Begrüßungsnachricht ausgelöst wird, muss sie den Richtlinien für Begrüßungsnachrichten entsprechen.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message.png" alt-text="Die Grafik zeigt ein Beispiel für das Senden einer Willkommensnachricht durch den Bot, wenn der Bot über einen komplexen Konfigurationsworkflow verfügt.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-no-welcome-message.png" alt-text="Die Grafik zeigt ein Beispiel, wie ein Bot keine Willkommensnachricht sendet, wenn der Bot über einen komplexen Konfigurationsworkflow verfügt.":::

* Bot-Begrüßungsnachrichten in Kanälen und Chats sind bei der ersten Ausführung optional, insbesondere wenn der Bot für den persönlichen Gebrauch verfügbar ist und ähnliche Aktionen ausführt. Ihr Bot darf keine Begrüßungsnachrichten an einzelne Nutzer senden (das gilt als [Spamming](#botmessagespamming)). In der Nachricht muss auch die Person erwähnt werden, die den Bot hinzugefügt hat.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-not-triggered.png" alt-text="validation-bot-welcome-message-not-trigger":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-message-triggered.png" alt-text="validation-bot-wel-message-trigger":::

* Nur Bots mit Benachrichtigungen müssen eine Willkommensnachricht senden, die klarstellt, dass es sich bei dem Bot nur um einen Benachrichtigungsbot handelt und benutzer nicht mit dem Bot interagieren können. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-notification-only-welcome-message-pass.png" alt-text="Die Grafik zeigt ein Beispiel dafür, wie ein Bot eine Willkommensnachricht sendet, dass es sich um einen Benachrichtigungs-Bot handelt.":::

* Die Willkommensnachricht darf für den Benutzer nicht inaktiv sein. Die Willkommensnachricht muss den Wert enthalten, den der Bot den Benutzern bietet, die den Bot im Kanal installiert haben, wie der Bot konfiguriert wird, und alle unterstützten Bot-Befehle kurz beschreiben. Sie können die Begrüßungsnachricht mithilfe einer adaptiven Karte mit Schaltflächen anzeigen, um die Benutzerfreundlichkeit zu verbessern. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-no-way-forward.png" alt-text="Die Grafik zeigt ein Beispiel für ein fehlerhaftes Szenario, in dem der Bot für den Benutzer in einer Willkommensnachricht keinen Weg nach vorne hat.":::

   :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-clear-way-forward.png" alt-text="Die Grafik zeigt ein Beispiel für eine Bot-Willkommensnachricht mit einem klaren Weg für den Benutzer, die Aufgabe abzuschließen.":::

* Der in einem Kanal- oder Gruppenchatbereich installierte Bot darf keine proaktive Willkommensnachricht an alle Teammitglieder im 1:1-Chat senden. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-send-proactive-message-to-all-members.png" alt-text="Die Grafik zeigt ein Beispiel für das Senden einer proaktiven Willkommensnachricht an alle Teammitglieder durch den Bot.":::

* Nur ein Benachrichtigungs-Bot kann eine proaktive Willkommensnachricht in einem Kanal senden, wenn die Nachricht wichtige Informationen für jeden Benutzer enthält, um die Konfiguration für den Bot abzuschließen, oder die Szenarien erläutert, in denen Benachrichtigungen ausgelöst werden. [*Obligatorischer Fix*]

* Der in einem Kanal- oder Gruppenchatbereich installierte Bot darf keine proaktiven Nachrichten (nicht nur Willkommensnachricht) senden, die für alle Benutzer im Kanal- oder Gruppenchat irrelevant sind, sondern muss proaktive Nachrichten über 1:1-Chats an den Benutzer senden. [*Obligatorischer Fix*]

* Der in einem Kanal- oder Gruppenchatbereich installierte Bot darf benutzern nicht erlauben, einzelne Workflows zu starten. Bots müssen einzelne Workflows im 1:1-Chat mit dem Benutzer ausführen. [*Obligatorischer Fix*]

* Die Willkommensnachricht des Bots muss die Einschränkungen im Zusammenhang mit der Bot-Nutzung im installierten Bereich deutlich herausrufen. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-messahe-with-app-limitation.png" alt-text="Die Grafik zeigt ein Beispiel für die App-Einschränkung in der Willkommensnachricht des Bots.":::

   :::image type="content" source="../../../../assets/images/submission/validation-bot-welcome-messahe-without-app-limitation.png" alt-text="Die Grafik zeigt ein Beispiel für einen Bot ohne App-Einschränkung in einer Willkommensnachricht.":::

* Die Willkommensnachricht muss bei der App-Installation in einem persönlichen Bereich automatisch ausgelöst werden. Wenn der Bot keine Willkommensnachricht in einem persönlichen Bereich sendet, wird der Benutzer in eine Sackgasse geführt. Wenn die App keinen komplexen Konfigurationsworkflow enthält, kann der Entwickler optional eine Willkommensnachricht im Kanal- oder Gruppenchatbereich auslösen. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-bot-no-welcome-message-in-personal-scope.png" alt-text="Die Grafik zeigt ein Beispiel, wie ein Bot eine Willkommensnachricht nicht automatisch im persönlichen Bereich sendet.":::

* Willkommensnachrichten dürfen nur einmal bei der Bot-Installation ausgelöst werden. Begrüßungsnachrichten dürfen nicht jedes Mal ausgelöst werden, wenn der Benutzer den Hilfebefehl aufruft. Die Hilfebefehlsantwort muss sich darauf konzentrieren, eine Möglichkeit für den Benutzer einzuschließen, auf Hilfe im Zusammenhang mit dem Bot zuzugreifen. [*Obligatorischer Fix*]

* Willkommensnachrichten dürfen nicht mit jedem Botbefehl ausgelöst werden. Dies gilt als Spam. [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-welcome-message-trigger-for-any-command.png" alt-text="Die Grafik zeigt ein Beispiel für den Bot, der eine Willkommensnachricht für einen beliebigen Befehl auslöst.":::

* Der Inhalt der Willkommensnachricht muss sich auf den Bot-Workflow beziehen, der in der langen Beschreibung der App und im Installationsumfang erwähnt wird. Die Willkommensnachricht muss den Wert enthalten, den der Bot Benutzern bietet, die den Bot im Kanal installiert haben, wie der Bot konfiguriert wird, und alle unterstützten Bot-Befehle kurz beschreiben. [*Obligatorischer Fix*]

* Der Bot darf nicht mehrere Willkommensnachrichten senden, wenn er bei der App-Installation ausgelöst wird. [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-bot-multiple-message-trigger-install.png" alt-text="Die Grafik zeigt ein Beispiel für einen Bot, der bei der App-Installation mehrere Willkommensmeldungen auslöst.":::

* Der App-Name in der Willkommensnachricht muss mit dem App-Namen im Manifest übereinstimmen. [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-app-name-mismatch-manifeast-and-welcome-message.png" alt-text="Die Grafik zeigt ein Beispiel für den App-Namen in der Willkommensnachricht, der nicht mit dem App-Namen im App-Manifest übereinstimmt.":::

* Die Willkommensnachricht darf nur dann Chat-basierte Plattformnamen von Wettbewerbern anzeigen, es sei denn, die App bietet eine bestimmte Interoperabilität.

* Die Willkommensnachricht darf den Benutzer nicht zu einer anderen Teams-App umleiten. Stattdessen muss die Willkommensnachricht den Benutzer dazu angehalten haben, seine erste Aufgabe auszuführen und alle unterstützten Bot-Befehle in der App kurz zu beschreiben. [*Obligatorischer Fix*]

* Die Willkommensnachricht darf keine Links zu einem App-Marketplace einschließlich AppSource enthalten. [*Obligatorischer Fix*]

* Wenn Ihre App über einen komplexen Konfigurationsworkflow verfügt, der eine administratorgeführte Installation erfordert, keinen intuitiven und leicht verfügbaren Registrierungsablauf aufweist oder benutzer die Konfigurationsschritte außerhalb der Teams-Umgebung ausführen und zurückgeben müssen, muss der Bot nach der Installation eine proaktive Willkommensnachricht in einem Team- oder Gruppenchatbereich senden. [*Obligatorischer Fix*]

* Wenn Ihr Bot eine Willkommensnachricht im Kanal sendet, darf er sie nicht einzeln an Benutzer senden (es wird als Spamming betrachtet). In der Willkommensnachricht muss auch die Person erwähnt werden, die den Bot hinzugefügt hat. [*Vorgeschlagene Korrektur*]

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
  * Senden Sie nicht mehrere Nachrichten in schneller Folge.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-multiple-message-quick-succession.png" alt-text="Die Grafik zeigt ein Beispiel für einen Bot, der mehrere Nachrichten in schneller Folge sendet.":::

  * Senden Sie eine Nachricht mit vollständigen Informationen.
  * Vermeiden Sie mehrfache Unterhaltungen, um einen einzelnen sich wiederholenden Workflow abzuschließen.
  * Verwenden Sie ein Formular (oder Aufgabenmodul), um alle Eingaben eines Benutzers gleichzeitig zu erfassen.
  * NLP-basierte Chatbots können Multi-Turn-Konversationen nutzen, um die Diskussion ansprechender zu gestalten und einen Arbeitsablauf abzuschließen.

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-task-module.png" alt-text="validation-bot-message-using-task-module":::

    :::image type="content" source="../../../../assets/images/submission/validation-bot-messages-using-mutliple-conversation.png" alt-text="Die Grafik zeigt einen Beispiel-Bot, der Mehrfachdrehungsnachrichten verwendet, um eine einzelne Unterhaltung abzuschließen.":::

* **Willkommensnachrichten**: Wiederholen Sie nicht gleiche Willkommensnachricht in regelmäßigen Abständen. Wenn beispielsweise ein neues Mitglied zu einem Team hinzugefügt wird, sollten Sie die anderen Mitglieder nicht mit einer Begrüßungsnachricht spammen. Nachricht an das neue Mitglied persönlich senden.

   :::image type="icon" source="../../../../assets/images/submission/validation-bot-send-proactive-message-to-all-members.png" alt-text="Die Grafik zeigt einen Beispiel-Bot, der Benutzer mit derselben Willkommensnachricht spammt.":::

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

Apps, die nur Benachrichtigungen mit Inhalten bereitstellen, z. B. **Sie haben eine neue Benachrichtigung**, **klicken Sie, um sie anzuzeigen** , und fordern den Benutzer auf, für alles andere außerhalb von Teams zu navigieren, bieten in Teams keinen signifikanten Wert.

   :::image type="content" source="../../../../assets/images/submission/validation-bot-notification-only-inadequete-info.png" alt-text="Screenshot zeigt ein Beispiel für eine Benachrichtigung nur bit mit unzureichenden Informationen in der Vorschau.":::

> [!TIP]
> Zeigen Sie Informationen in der Vorschau an, und stellen Sie grundlegende Inline-Benutzeraktionen auf der bereitgestellten Karte bereit, damit der Benutzer nicht für alle Aktionen (unabhängig von der Komplexität) außerhalb von Teams navigieren muss.

</details>
<br/>

<details><summary>Bot-Metadateninformationen</summary>

* Bot-Informationen im App-Manifest (Bot-Name, Logo, Datenschutzlink und Link zu Nutzungsbedingungen) müssen mit den Bot Framework-Metadaten konsistent sein. [*Obligatorischer Fix*]

* Die Bot-ID muss im App-Manifest und in den Bot Framework-Metadaten übereinstimmen. [*Obligatorischer Fix*]

* Stellen Sie sicher, dass die Bot-ID im App-Manifest mit der Bot-ID in der zuletzt veröffentlichten Version Ihrer App übereinstimmt. Das Ändern von Bot-IDs in einem App-Update führt zu einem dauerhaften Verlust des gesamten Benutzerinteraktionsverlaufs mit dem Bot für vorhandene Benutzer Ihrer App und startet eine neue Unterhaltungskette mit der neuen Bot-ID. [*Obligatorischer Fix*]

* Jede Änderung des App-Namens, der Metadaten, der Bot-Willkommensnachricht oder der Botantworten muss mit einem neuen Namen aktualisiert werden. [*Obligatorischer Fix*]

* Der App-Name in der Bot-Willkommensnachricht oder den Botantworten muss mit dem App-Namen im Manifest übereinstimmen. [*Obligatorischer Fix*]

</details>
<br/>

<details><summary>Bot im Bereich der Zusammenarbeit</summary>

* Bot-Installation in einem Kanal- oder Gruppenchatbereich, um die Teamliste zum Senden proaktiver Benachrichtigungen für Benutzer abzurufen, da 1:1-Chats für teamspezifische Trigger nicht zulässig sind. Beispielsweise eine App, die Personen für ein Meetup paart. [*Obligatorischer Fix*]

* Bot im Kanal- oder Gruppenchat wird nur verwendet, um die Nachrichten oder Beiträge im Kanal- oder Gruppenchat abzurufen, um proaktive Benachrichtigungen für Benutzer zu senden, da 1:1-Chats nicht zulässig sind. [*Obligatorischer Fix*]

* Bots, die im Bereich der Zusammenarbeit installiert sind, müssen einen Benutzerwert im Bereich "Zusammenarbeit" bereitstellen. [*Obligatorischer Fix*]

</details>

## <a name="message-extensions"></a>Nachrichtenerweiterungen

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.4.4](/legal/marketplace/certification-policies#114044-messaging-extensions).

Wenn Ihre App eine Nachrichtenerweiterung enthält, stellen Sie sicher, dass sie diesen Richtlinien entspricht.

> [!TIP]
> Weitere Informationen zum Erstellen einer qualitativ hochwertigen App-Erfahrung finden Sie in den [Entwurfsrichtlinien für Microsoft Teams Nachrichtenerweiterungen](~/messaging-extensions/design/messaging-extension-design.md).

<br/>

<details><summary>Entwurfsrichtlinien für Messagingerweiterungen</summary>

* Wenn Ihre Teams-App die Messaging-Erweiterungsfunktion verwendet, muss Ihre App den [Entwurfsrichtlinien für Messaging-Erweiterungen](../../../../messaging-extensions/design/messaging-extension-design.md) entsprechen.

   :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-design-guidelines-fail.png" alt-text="Die Grafik zeigt ein Beispiel für eine App, die die Erweiterungsrichtlinien nicht erfüllt.":::

* Messagingerweiterungen sind Tastenkombinationen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne von der Konversation weg zu navigieren. Halten Sie Ihre Messaging-Erweiterung einfach, und zeigen Sie nur die Komponenten an, die erforderlich sind, um die Aktion effektiv abzuschließen. Die vollständige Website darf nicht in die Messaging-Erweiterung eingeschlossen werden [*Obligatorischer Fix*]

* Vorschaubilder in adaptiven Karten in Messaging-Erweiterungen müssen ordnungsgemäß geladen werden. [*Obligatorischer Fix*]

  :::image type="content" source="../../../../assets/images/submission/validation-preview-image-adaptive-card-loading.png" alt-text="Die Grafik zeigt ein Beispiel für das Laden von Vorschaubildern auf einer adaptiven Karte.":::

  :::image type="content" source="../../../../assets/images/submission/validation-preview-image-adaptive-card-not-loading.png" alt-text="Die Grafik zeigt ein Beispiel für ein Vorschaubild, das nicht in der adaptiven Karte geladen wird.":::

* Die Antwortkarte der Messaging-Erweiterung muss das App-Symbol enthalten, um Verwirrung bei Endbenutzern zu vermeiden. [*Obligatorischer Fix*]

* Ihre App darf keine fehlerhaften Funktionen aufweisen. Die App darf weder das Sackgassenende noch den Benutzer daran hindern, einen Workflow in einer Messaging-Erweiterung abzuschließen. [*Obligatorischer Fix*]

* Messaging-Erweiterungen müssen in Gruppenchat- und Kanalbereichen wie beabsichtigt reagieren oder funktionieren. [*Obligatorischer Fix*]

* Sie müssen eine Möglichkeit für den Benutzer angeben, sich bei der Messaging-Erweiterung anzumelden oder abzumelden. [*Obligatorischer Fix*]

</details>
</br>

<details><summary>Aktionsbefehle für aktionsbasierte Nachrichtenerweiterungen</summary>

Aktionsbasierte Nachrichtenerweiterungen müssen folgende Aktionen ausführen:

* Ermöglichen Sie es Benutzern, Aktionen für eine Nachricht auszulösen, ohne Zwischenschritte wie die Anmeldung auszuführen.

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-no-intermediate-step.png" alt-text="validation-messaging-extension-no-intermediate-steps":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-intermediate-step-available.png" alt-text="validation-messaging-extension-intermediate-steps-available":::

* Übergeben des Nachrichtenkontexts an den nächsten Arbeitsstatus. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-passes-message.png" alt-text="validation-messaging-extension-app-passes-messages":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-app-doesnot-pass-message.png" alt-text="validation-messaging-extension-app-doesnot-pass-messages":::

* Integrieren Sie den Namen der Host-App anstelle eines generischen Verbs für Aktionsbefehle, die von einer Chat-Nachricht, einem Channel-Post oder einem Aufruf zum Handeln innerhalb von Apps ausgelöst werden. Verwenden Sie z. B. "**Skype-Besprechung** starten" für "**Besprechung starten**", **"Datei zum Hochladen in DocuSign** **hochladen"**. [*Vorgeschlagene Korrektur*]

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-host-name.png" alt-text="Die Grafik zeigt ein Beispiel für den Namen der Host-App für einen Aktionsbefehl.":::

    :::image type="content" source="../../../../assets/images/submission/validation-messaging-extension-action-command-verb.png" alt-text="Die Grafik zeigt ein Beispiel für ein generisches Verb für einen Aktionsbefehl.":::

* Das Aufrufen einer Nachrichtenaktion muss es dem Benutzer ermöglichen, den Workflow abzuschließen. Fehler, leere Antworten oder Indikatoren für das kontinuierliche Laden, damit die Nachrichtenaktion wie beabsichtigt funktioniert, dürfen nicht vorhanden sein. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-continous-loading-indicator-action-command.png" alt-text="Die Grafik zeigt ein Beispiel für die Fortlaufende Ladeanzeige, wenn ein Bot einen Aktionsbefehl aufruft.":::

* Doppelte Aktionsbefehle dürfen nicht vorhanden sein. [*Obligatorischer Fix*]

* Nachrichtenaktionen müssen es dem Benutzer ermöglichen, den Workflow wie beabsichtigt auszuführen, ohne dass eine ungültige Antwort vorhanden ist. [*Obligatorischer Fix*]

* Apps mit nur aktionsbasierter Messaging-Erweiterung müssen den folgenden Endzustand aufweisen:

  * Posten Sie eine relevante Aktion als Benachrichtigung entweder in dem Kontext, in dem die Nachrichtenerweiterung aufgerufen wird, oder im 1:1-Bot-Chat basierend auf dem Benutzerszenario. [*Obligatorischer Fix*]

  * Benutzern das Freigeben von Karten für andere Benutzer basierend auf der ausgeführten Aktion erlauben. Dadurch wird sichergestellt, dass Apps keine automatischen Aktionen ausführen. Beispielsweise wird ein Ticket basierend auf einer Nachricht in einem Kanal erstellt, aber die App sendet keine Benachrichtigung oder bietet keine Möglichkeit, den Benutzer aufzufordern, Ticketdetails freizugeben, nachdem das Ticket erstellt wurde. [*Obligatorischer Fix*]

</details>
</br>

<details><summary>Vorschau-Links (Link-Unfurling)</summary>

[*Obligatorischer Fix*]

Nachrichtenerweiterungen müssen eine Vorschau der erkannten Links im Feld „Verfassen“ in Microsoft Teams anzeigen. Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden (entweder absolute URLs oder Platzhalter). Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig. Top-Level Domains sind ebenfalls nicht zulässig. Zum Beispiel `*.com` oder `*.org`. [*Obligatorischer Fix*]

</details>
</br>

<details><summary>Suchbefehle</summary>

* Such-basierte Nachrichtenerweiterungen müssen Text bereitstellen, der den Nutzern bei der effektiven Suche hilft. [*Obligatorischer Fix*]

    :::image type="content" source="../../../../assets/images/submission/validation-search-commands-text-available.png" alt-text="Die Grafik zeigt ein Beispiel für eine Nachrichtenerweiterung mit Hilfetext, damit Benutzer effektiv suchen können.":::

    :::image type="content" source="../../../../assets/images/submission/validation-search-commands-text-not-available.png" alt-text="Die Grafik zeigt ein Beispiel für eine Nachrichtenerweiterung ohne Hilfetext, damit Benutzer effektiv suchen können.":::

* @mention ausführbare Dateien müssen klar, leicht verständlich und lesbar sein.

    :::image type="content" source="../../../../assets/images/submission/validation-search-command-unclear-executable.png" alt-text="validation-search-commands-unclear-executable":::

</details>
</br>

<details><summary>Aktionsbefehle für die suchbasierte Nachrichtenerweiterung</summary>

[*Obligatorischer Fix*]

Apps, die aus einer suchbasierten Nachrichtenerweiterung bestehen, bieten Benutzern einen Mehrwert, indem sie Karten freigeben, die kontextbezogene Unterhaltungen ohne Kontextwechsel ermöglichen.

Um die Überprüfung nur für eine suchbasierte Nachrichtenerweiterungs-App zu bestehen, sind Folgendes als Basisplan erforderlich, um sicherzustellen, dass die Benutzererfahrung nicht unterbrochen wird. Eine über eine Nachrichtenerweiterung freigegebene Karte bietet einen Mehrwert in Microsoft Teams, wenn:

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
<details><summary>Entwurfsrichtlinien für Besprechungserweiterungen</summary>

* Ihre Teams-Apps müssen den [Entwurfsrichtlinien für Besprechungserweiterungen](../../../../apps-in-teams-meetings/design/designing-apps-in-meetings.md) entsprechen.

* Mit der In-Meeting-App können Sie Teilnehmer während der Besprechung mithilfe von Registerkarten in der Besprechung, dialogfeldern und der In-Meeting-Freigabe für die Phasenfunktion einbeziehen. Wenn Ihre App die Teams-Besprechungserweiterung unterstützt, müssen Sie eine reaktionsfähige Besprechungserfahrung bereitstellen, die an die Teams-Besprechungserfahrung angepasst ist. [*Obligatorischer Fix*]

* Mit der Pre-Meeting App-Erfahrung können Nutzer Meeting-Apps finden und hinzufügen. Benutzer können auch Aufgaben vor der Besprechung ausführen, z. B. das Entwickeln einer Umfrage, um die Besprechungsteilnehmer zu befragen. Eine App, die eine Erfahrung vor der Besprechung bereitstellt, muss für den Besprechungsworkflow relevant sein und dem Benutzer einen Mehrwert bieten. [*Obligatorischer Fix*]

* Mit der App-Erfahrung nach der Besprechung können Benutzer die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback und andere App-Inhalte. Eine App, die eine Erfahrung nach der Besprechung bereitstellt, muss für den Workflow der Besprechung relevant sein und dem Benutzer einen Mehrwert bieten. [*Obligatorischer Fix*]

* Mit der In-Meeting-App-Erfahrung können Sie Besprechungsteilnehmer während der Besprechung einbeziehen und die Besprechungserfahrung für alle Teilnehmer verbessern. Teilnehmer dürfen nicht außerhalb der Teams-Besprechung weitergeleitet werden, um die wichtigsten Benutzerworkflows der App abzuschließen. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-outside-teams-core-workflows.png" alt-text="Die Grafik zeigt ein Beispiel für eine Besprechungserfahrung, bei der Benutzer außerhalb von Teams umgeleitet werden, um die wichtigsten App-Funktionen abzuschließen.":::

* Ihre App muss einen Mehrwert bieten, der über die Bereitstellung nur benutzerdefinierter Szenen im Zusammen-Modus in Teams hinausgeht. [*Obligatorischer Fix*]

* Sie müssen als Bereich unter `configurableTabs` und `meetingChatTab``meetingDetailsTab`als Kontexteigenschaft im Manifest deklarieren`groupChat`, `meetingSidePanel` um Ihre App für Besprechungen auf Teams Mobile zu aktivieren. [*Obligatorischer Fix*]

* Besprechungsleinwände dürfen einen Besprechungsteilnehmer nicht im Sackgasse befinden. Besprechungszeichenbereiche müssen eine ordnungsgemäße Fehlermeldung für App-Einschränkungen wie z. B. regionsspezifische Abhängigkeiten anzeigen. [*Obligatorischer Fix*]

* In der Kopfzeile des Besprechungszeichenbereichs muss der richtige App-Name angezeigt werden, um den Besprechungsteilnehmer nicht zu verwirren. [*Obligatorischer Fix*]

* Sie müssen eine Option angeben, mit der sich der Benutzer bei der Besprechungserweiterung abmelden oder abmelden kann. [*Obligatorischer Fix*]

* Besprechungsregisterkarten auf mobilen Plattformen müssen relevante Workflows enthalten. Leere Seiten dürfen auf einer Besprechungsregisterkarte nicht vorhanden sein. [*Obligatorische Korrektur*]

* Die Besprechungsphase ist ein fokussierter, intuitiver und kollaborativer Teilnahmebereich. Die Besprechungsphase darf nicht die vollständige Websiteoberfläche einbetten. [*Obligatorischer Fix*]

* Die App darf keine fortlaufenden Ladebildschirme, Fehler oder fehlerhafte Funktionen anzeigen, die den Benutzer inaktiv stellen oder den Abschluss eines Workflows in einem Besprechungsszenario blockieren. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-app-shows-continous-loading-screen.png" alt-text="Die Grafik zeigt ein Beispiel für den fortlaufenden Ladebildschirm in einer App.":::

* Die App darf beim Starten einer Besprechung keine neue Teams-Instanz öffnen. Besprechungs canvases sind eine Erweiterung der Teams-Funktionen, die die Zusammenarbeit in Echtzeit fördern, und neue Besprechungen müssen immer innerhalb der derzeit aktiven Teams-Instanz geöffnet werden. [*Obligatorischer Fix*]

* Besprechungs-Apps müssen Workflows innerhalb der Microsoft Teams-Plattform ausführen, ohne zu chatbasierten Plattformen des Wettbewerbers umzuleiten. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-apps-redirecting-competitor-chat-platform.png" alt-text="Die Grafik zeigt ein Beispiel für eine App, die auf eine chatbasierte Plattform umleitet.":::

* Wenn Ihre App rollenbasierte Ansichten unterstützt und bestimmte Workflows für alle Teilnehmer nicht verfügbar sind, empfehlen wir, dass Sie geeignete Nachrichten für Teilnehmer in Registerkarten und Seitenpanel implementieren, die angeben, dass die App derzeit für die Ansicht des Organisators bestimmt ist, und Details dazu bereitstellen, wie die Teilnehmer die Besprechungsnotizen, Aktionselemente und Aktualisierungsagenda erhalten. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-way-forward-not-available-for-role-based-views.png" alt-text="Die Grafik zeigt ein Beispiel für eine App ohne Eine Möglichkeit für Teilnehmer in einer rollenbasierten Ansicht.":::

</details>
<br/>

<details><summary>Allgemein</summary>

Verwenden Sie die folgenden Richtlinien für die Erweiterung von Besprechungen:

* Besprechungserweiterungs-Apps müssen eine reaktionsfähige Besprechungserfahrung bieten, die an die Teams-Besprechungserfahrung angepasst ist. Die In-Meeting-Erfahrung ist für eine Teams-App obligatorisch, die die Erweiterbarkeit von Besprechungen unterstützt, aber Die Erfahrungen vor und nach der Besprechung sind nicht obligatorisch.

  * Mit der Pre-Meeting App-Erfahrung können Nutzer Meeting-Apps finden und hinzufügen. Benutzer können auch Aufgaben vor der Besprechung ausführen, z. B. das Entwickeln einer Umfrage zur Umfrage der Besprechungsteilnehmer. Wenn Ihre App eine Erfahrung vor der Besprechung bietet, muss sie für den Workflow der Besprechung relevant sein.

  * Mit der App-Erfahrung nach der Besprechung können Benutzer die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback und andere App-Inhalte. Wenn Ihre App eine Erfahrung nach der Besprechung bietet, muss sie für den Workflow der Besprechung relevant sein.

  * Mit der In-Meeting-App-Erfahrung können Sie Besprechungsteilnehmer während der Besprechung einbeziehen und die Besprechungserfahrung für alle Teilnehmer verbessern. Teilnehmer dürfen nicht außerhalb der Teams-Besprechung genommen werden, um die wichtigsten Benutzerworkflows Ihrer App abzuschließen.

* Ihre Anwendung muss einen Mehrwert bieten, der über die Bereitstellung benutzerdefinierter Szenen im Together-Modus in Teams hinausgeht.

* Das Feature „Gemeinsame Besprechungsphase“ kann nur über die Teams Desktop-App gestartet werden. Die Nutzung der gemeinsamen Besprechungsphase muss jedoch möglich sein und darf nicht unterbrochen werden, wenn sie auf mobilen Geräten angezeigt wird.

> [!TIP]
> Sie müssen als Bereich unter `configurableTabs` und `meetingChatTab``meetingDetailsTab`als Kontexteigenschaft im Manifest deklarieren`groupChat`, `meetingSidePanel` um Ihre App für Besprechungen auf Teams Mobile zu aktivieren.

</details>
</br>

<details><summary>Erfahrung vor und nach der Besprechung</summary>

* Bildschirmanzeigen vor und nach Besprechungen müssen den allgemeinen Richtlinien für den Entwurf von Registerkarten entsprechen. Weitere Informationen finden Sie unter [Teams-Entwurfsrichtlinien](~/tabs/design/tabs.md).
* Registerkarten müssen ein strukturiertes Layout aufweisen, wenn mehrere Elemente angezeigt werden. Beispielsweise finden Sie mehr als 10 Umfragen oder Erhebungen unter [Beispiellayout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Ihre App muss Benutzer benachrichtigen, wenn die Ergebnisse einer Umfrage oder Erhebung exportiert werden, indem sie angibt, dass **Ergebnisse erfolgreich heruntergeladen** wurden.

   :::image type="content" source="../../../../assets/images/submission/validation-meeting-experience-tab-design-guidelines-fail.png" alt-text="Die Grafik zeigt ein Beispiel für Registerkarten, die nicht den Entwurfsrichtlinien für Registerkarten entsprechen.":::

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

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button.png" alt-text="Die Grafik zeigt ein Beispiel für die Darstellung der Zurück-Schaltfläche.":::

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-exp-back-button-absent.png" alt-text="Die Grafik zeigt ein Beispiel, dass die Zurück-Schaltfläche nicht vorhanden ist.":::

* Darf nicht mehr als eine Schaltfläche zum Schließen enthalten. Dies könnte die Benutzer verwirren, da es bereits eine eingebaute Schaltfläche in der Kopfzeile gibt, um die Registerkarte zu schließen.
* Darf keinen horizontalen Bildlauf haben.

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-tab-vertical-scroll.png" alt-text="Die Grafik zeigt ein Beispiel für eine Besprechungsregisterkarte mit vertikalem Bildlauf.":::

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-tab-horizontal-scroll.png" alt-text="Die Grafik zeigt ein Beispiel für eine Besprechungsregisterkarte mit horizontalem Bildlauf.":::

</details>

</br>
<details><summary>Dialoge im Besprechungen</summary>

* Muss sparsam und für leichte und aufgabenorientierte Szenarien eingesetzt werden.
* Der Inhalt muss in einer einzigen Spalte angezeigt werden und darf nicht über mehrere Navigationsebenen verfügen.

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-single-column-layout.png" alt-text="Die Grafik zeigt ein Beispiel für ein Einspaltlayout für das Dialogfeld &quot;In-Meeting&quot;.":::

  :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-multiple-column-layout.png" alt-text="Die Grafik zeigt ein Beispiel für mehrere Spaltenlayouts für das Dialogfeld &quot;In-Meeting&quot;.":::

* Darf keine Aufgabenmodule verwenden.
* Muss mit der Mitte der Besprechungsbereich ausgerichtet sein.

    :::image type="content" source="../../../../assets/images/submission/validation-in-meeting-dialog-not-aligned.png" alt-text="Die Grafik zeigt ein Beispiel für ein Dialogfeld in einer Besprechung, das nicht mit der Mitte der Besprechungsphase übereinstimmt.":::

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

Wenn Ihre App die [von Microsoft Graph bereitgestellten Aktivitätsfeed-APIs](/graph/teams-send-activityfeednotifications) verwendet, stellen Sie sicher, dass sie den folgenden Richtlinien entspricht.

> [!TIP]
> Wenn Ihre Apps Benachrichtigungsszenarien unterstützen, in denen die Benachrichtigungen nach langen Intervallen ausgelöst werden, z. B. nach einem Tag oder einem Monat. Bevor Sie zur Überprüfung einreichen, stellen Sie sicher, dass Sie solche Benachrichtigungen im Hintergrund auslösen, damit wir die Benachrichtigungen testen können.

<br></br>

<details><summary>Entwurfsrichtlinien für Benachrichtigungen</summary>

* Ihre Teams-Apps müssen [den Entwurfsrichtlinien für Aktivitätsfeedbenachrichtigungen](/graph/teams-send-activityfeednotifications) entsprechen.

* Irrelevanter, unsachgemäßer, nicht reagierender oder fehlerhafter Workflow darf nicht vorhanden sein, nachdem der Benutzer eine Benachrichtigung im Teams-Aktivitätsfeed ausgewählt hat. Benutzer dürfen nicht daran gehindigt werden, einen Workflow abzuschließen, nachdem sie eine Aktivitätsfeedbenachrichtigung ausgewählt haben. [*Obligatorischer Fix*]

* Fügen Sie den Namen Ihrer App in die Aktivitätsfeedbenachrichtigung ein, damit Endbenutzer die Quelle oder den Auslöser für die Benachrichtigung ohne Verwirrung verstehen können. [*Obligatorischer Fix*]

* Die App muss Benachrichtigungen für alle Benachrichtigungsszenarien auslösen, die in der langen Beschreibung der App, bei der ersten Ausführung der App und in Szenarien, die im `activityTypes` Manifest deklariert sind, erwähnt werden. [*Obligatorischer Fix*]

* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden. [*Obligatorischer Fix*]

* Sie müssen Benachrichtigungseinschränkungen (falls vorhanden) in der langen Beschreibung Ihrer App oder in der Ersten Ausführung der App angeben. [*Obligatorischer Fix*]

</details>
<br/>

<details><summary>Allgemein</summary>

* Alle in der App-Konfiguration angegebenen Benachrichtigungs-Auslöser müssen funktionieren.
* Benachrichtigungen müssen gemäß den unterstützten Sprachen lokalisiert werden, die für Ihre App konfiguriert sind.
* Benachrichtigungen müssen innerhalb von fünf Sekunden nach der Benutzeraktion angezeigt werden.
* Benachrichtigungen müssen gemäß den unterstützten Sprachen für alle Plattformen lokalisiert werden, auf denen Ihre App kompatibel ist. [*Obligatorischer Fix*]

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

    :::image type="content" source="../../../../assets/images/submission/validation-365-compliance-publisher-verification.png" alt-text="Die Grafik zeigt ein Beispiel für ein blaues überprüftes Signal im Azure Active Directory-Zustimmungsdialogfeld.":::

* **Publisher-Bestätigung:** Ein Prozess, bei dem Sie allgemeine Informationen zur Datenverarbeitung sowie Sicherheits- und Compliance-Informationen weitergeben, um potenziellen Kunden zu helfen, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Wenn Sie eine App übermitteln, die zuvor noch nicht aufgeführt wurde, können Sie den Herausgebernachweis erst dann offiziell abschließen, wenn sich Ihre App im Teams Store befindet. Wenn Sie eine aufgeführte App aktualisieren, führen Sie die Publisher-Bestätigung durch, bevor Sie die neueste Version der App einreichen.

</details>

## <a name="advertising"></a>Werbung

:::image type="icon" source="../../../../assets/icons/certificate-icon-16.png":::Dieser Abschnitt steht im Einklang mit[ der Microsoft-Richtlinie für kommerzielle Marktplätze Nr. 1140.7](/legal/marketplace/certification-policies#11407-advertising).

Apps dürfen keine Werbung anzeigen, einschließlich dynamischer Anzeigen, Banneranzeigen und Anzeigen in Nachrichten.

:::image type="content" source="../../../../assets/images/submission/validation-advertising-banners.png" alt-text="Die Grafik zeigt ein Beispiel für ein fehlerhaftes Werbeszenario in Teams.":::

## <a name="cryptocurrency-based-apps"></a>Kryptowährungsbasierte Apps

Wenn Ihre App verteilt wird, müssen Sie die Einhaltung aller Gesetze nachweisen:

* Erleichtert Kryptowährungstransaktionen oder -übertragungen innerhalb der App.

* Fördert kryptowährungsbezogene Inhalte.

* Ermöglicht Benutzern, ihre gespeicherte Kryptowährung zu speichern oder darauf zuzugreifen.

* Ermutigt oder ermöglicht Benutzern, eine kryptowährungsbasierte Transaktion oder Übertragung außerhalb der Teams-Plattform abzuschließen.

* Fördert oder erleichtert das Mining von Kryptowährungstoken.

* Erleichtert die Teilnahme des Benutzers an Initial Coin Offerings.

* Rewards oder Incentivizes Benutzer mit Kryptowährungstoken für die Durchführung einer Aufgabe.

Nach einer internen Microsoft-Überprüfung kann Microsoft, wenn die Konformitätsdemonstration zufriedenstellend ist, mit der weiteren Zertifizierung Ihrer App fortfahren. Wenn die Compliancedemonstration nicht zufriedenstellend ist, informiert Microsoft Sie über die Entscheidung, die Zertifizierung Ihrer App nicht fortzusetzen.

## <a name="app-functionality"></a>App-Funktionalität

* Workflows oder Inhalte in der App müssen mit dem Bereich verknüpft sein. [*Obligatorischer Fix*]
* Alle App-Funktionen müssen funktionsfähig sein und ordnungsgemäß funktionieren, wie in der langen Beschreibung der AppSource oder des Manifests beschrieben. [*Obligatorischer Fix*]
* Apps müssen den Benutzer immer vertraut machen, bevor sie eine Datei oder ausführbare Datei in der Umgebung des Benutzers herunterladen. Jeder Handlungsaufruf (Call to Action, CTA), entweder textbasiert oder anderweitig, der dem Benutzer deutlich macht, dass eine Datei oder ausführbare Datei für die Benutzeraktion heruntergeladen wird, ist in der App zulässig. [*Obligatorischer Fix*]

## <a name="mobile-experience"></a>Mobile Erfahrung

* Mobile Add-Ins müssen kostenlos sein. Es darf keine In-App-Inhalte oder Links geben, die Upselling, Onlinestores oder andere Zahlungsaufforderungen fördern. Alle Konten, die für Apps erforderlich sind, dürfen keine Gebühren für die Nutzung haben und, wenn sie zeitlich begrenzt sind, keine Inhalte enthalten, die darauf hinweisen, dass sie bezahlt werden müssen.

   :::image type="content" source="../../../../assets/images/submission/validation-mobile-add-in-charges.png" alt-text="Die Grafik zeigt ein Beispiel für ein mobiles Add-In, das eine Zahlung anfordert.":::

* Die Verwendung des Worts **"KOSTENLOS**", **"KOSTENLOSE TESTVERSION"** oder " **TESTEN KOSTENLOS** " ist auf der Desktop- oder Web-App-Oberfläche ohne Einschränkung oder Gegenleistung zulässig.

* Die Verwendung des Worts **FREE** als Nur-Text im Kontext eines Test- oder App-Upgrades ist auf mobilen Geräten zulässig.

* Die Verwendung des Worts **"KOSTENLOS** " im Kontext eines Test- oder App-Upgrades mit einem Link, der zu einer Startseite führt, ohne dass Zahlungs- oder Preisinformationen auf mobilen Geräten zulässig sind. Nur-Text,um zu signalisieren, dass die App **kostenpflichtig** ist, ist auf mobilgeräten zulässig.

* Die Verwendung des Worts **"KOSTENLOS** " als Nur-Text im Kontext eines Test- oder App-Upgrades und im Zusammenhang mit Preisdetails ist auf Mobilgeräten nicht zulässig.

* Die Verwendung des Worts **"KOSTENLOS** " im Kontext eines Test- oder App-Upgrades, das einem Link zugeordnet ist, der zu einer Startseite mit Preisinformationen oder Zahlungsdetails auf mobilgeräten führt, ist nicht zulässig.

* Preisdetails auf Mobilgeräten in einem beliebigen Format, z. B. Bild, Text oder Link, sind nicht zulässig. CTA, z. B **. Ansichtspläne** auf mobilen Geräten, ist nicht zulässig. Informationen zu Plänen ohne Preisdetails, aber mit einem Kontaktlink oder einer E-Mail auf mobilen Geräten sind nicht zulässig. Text mit Kontaktdetails, der auf ein kostenpflichtiges Upgrade verlinkt oder anspielt, ist auf mobilen Geräten nicht zulässig. Zahlungen für physische Waren sind auf mobilgeräten erlaubt. Ihre App kann z. B. die Zahlung für die Buchung eines Taxis ermöglichen.

   :::image type="content" source="../../../../assets/images/submission/validation-mobile-exp-pricing-details-on-mobile-fail.png" alt-text="Die Grafik zeigt ein Beispiel für Preisdetails auf Mobilgeräten.":::

* Zahlungen für digitale Waren in der App sind auf mobilgeräten nicht zulässig. [*Obligatorischer Fix*]

   :::image type="content" source="../../../../assets/images/submission/validation-mobile-exp-payments-digital-goods.png" alt-text="Die Grafik zeigt ein Beispiel für Zahlungen für digitale Waren auf Mobilgeräten.":::

* Teams-Apps müssen eine entsprechende geräteübergreifende mobile Erfahrung bieten. [*Obligatorischer Fix*]

* Funktionen, die auf mobilgeräten nicht unterstützt werden, dürfen kein End-End für einen Benutzer sein und müssen ggf. eine ordnungsgemäße Fehlermeldung bereitstellen. [*Obligatorischer Fix*]

## <a name="next-step"></a>Nächster Schritt

> [!div class=*nextstepaction*]
> [Erstellen Sie ein Partner Center-Konto](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)

## <a name="see-also"></a>Weitere Informationen

* [Verteilen Ihrer App](~/concepts/deploy-and-publish/apps-publish-overview.md)
* [Vorbereiten der Übermittlung an den Store](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [Testen und Debuggen Ihrer App](~/concepts/build-and-test/debug.md)
* [Erstellen eines Partner Center-Entwicklerkontos](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md)
