---
title: Grundlegendes zum Übermittlungsprozess des Teams-Speichers
description: Beschreibt den Genehmigungsübermittlungsprozess zum Veröffentlichen Ihrer App im Microsoft Teams App Store
ms.topic: overview
localization_priority: Normal
keywords: teams publish store office publishing publish AppSource partner center account verification apps account not publish eligible app submission
ms.openlocfilehash: 79584ae1eb0be24b4a66e2421f23dd694f8d610f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019895"
---
# <a name="submit-your-app-to-appsource"></a>Übermitteln Ihrer App an AppSource

## <a name="teams-app-submission"></a>Übermittlung von Teams-Apps

Stellen Sie Ihre App im Microsoft Teams-App-Katalog und im Web zur Verfügung, indem Sie sie in [AppSource veröffentlichen.](https://appsource.microsoft.com) Auf einer hohen Ebene lautet der Prozess zum Übermitteln Ihrer App an AppSource wie folgt:

1. Entwickeln Sie Ihre App, indem Sie die [Entwurfsrichtlinien befolgen.](~/concepts/design/understand-use-cases.md) Registerkarten müssen die Richtlinien für das Registerkartendesign sowohl für Desktop als [auch für Web](~/tabs/design/tabs.md) und Mobile [befolgen.](~/tabs/design/tabs-mobile.md) Bots müssen die Richtlinien für [das Botdesign befolgen.](~/bots/design/bots.md)
1. Stellen Sie sicher, dass Ihre App die [App-Validierungsrichtlinien](/legal/marketplace/certification-policies) für Microsoft Teams erfüllt. 
1. Testen Sie Ihre App mit dem [Manifestüberprüfungstool](prepare/submission-checklist.md#teams-app-validation-tool).
1. Richten Sie ein [Entwicklerkonto](/office/dev/store/open-a-developer-account) im [Partner Center ein.](https://support.microsoft.com/help/4499930/partner-center-overview) *Weitere Informationen finden* [Sie unter How do I create a Partner Center account](#how-do-i-create-a-partner-center-account) in the FAQ section.
1. Bereiten Sie Ihre App auf die Übermittlung vor, indem Sie die [Übermittlungscheckliste folgen.](prepare/submission-checklist.md)
1. Überprüfen Sie die [am häufigsten fehlgeschlagenen Testfälle, um eine schnellere App-Qualitätsgenehmigung zu erhalten.](prepare/frequently-failed-cases.md)
1. Senden Sie Ihr Paket [über Partner Center an AppSource.](/office/dev/store/use-partner-center-to-submit-to-appsource)
1. Verfolgen Sie den Genehmigungsprozess auf Ihrem Partner Center-Dashboard. *Weitere Informationen finden* [Sie unter Partner Center Overview](https://support.microsoft.com/help/4499930/partner-center-overview).
1. Lesen Sie nach der Übermittlung die Anleitungen zum Verwalten und Unterstützen [Ihrer veröffentlichten App.](post-publish/overview.md)

>[!NOTE]
>
>- Ihre Teams-App muss mobil reagieren und keine [Upsellanforderungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) für mobile Betriebssysteme (iOS und Android) erfüllen. 
>- Wenn Ihre Teams-App einen Bot enthält, müssen Sie den Bot Developer Framework [Code of Conduct einhalten.](https://aka.ms/bf-conduct)
>- Wenn Ihre App einen Office 365 Connector enthält, können zusätzliche Bedingungen gelten. Weitere [Informationen finden Sie unter Connectors Developer Dashboard](https://aka.ms/connectorsdashboard) and App Developer [Agreement](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm).
>- Um Ihre App für Benutzer der Government Community Cloud (GCC) verfügbar zu machen und doppelte App-Einträge im Store zu vermeiden, muss der Authentifizierungsprozess oder -fluss den Benutzer identifizieren und an die angegebene oder erwartete Inhalts-URL für GCC-Benutzer weiterverfassen.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>Häufig gestellte Fragen – Überprüfung von Teams-Apps und Partnerkonto im Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Wie erstelle ich ein Partner Center-Konto?

Es gibt zwei Möglichkeiten zum Erstellen eines Partner Center-Kontos:

- Wenn Sie neu im Partner Center sind und kein Konto im Microsoft-Netzwerk haben, erstellen Sie ein Konto auf der [Partner Center-Registrierungsseite](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment).
- Wenn Sie bereits im Partnernetzwerk registriert sind, erstellen Sie ein Konto direkt im Partner Center mithilfe einer vorhandenen [Registrierungsseite.](/office/dev/store/)

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>Was passiert, wenn ich mein Office Store-Konto im Partner Center nicht finden kann?

Öffnen Sie [ein Partner Center-Supportticket,](https://partner.microsoft.com/support/v2/?stage=1) und wählen Sie in den Dropdownmenüs Folgendes aus:

| Menü | Option |
| -------   | -------  |
|Kategorie| Kommerzieller Marketplace|
| Thema | Allgemeine Marketplace-Hilfe und How-to-Fragen |
| Untertopisch| Office-Add-In |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Wo kann ich Support für Probleme mit meinem Partner Center-Konto erhalten?

Besuchen Sie [die Supportseite für Herausgeber,](https://aka.ms/marketplacepublishersupport) um nach Ihrem Problemthema zu suchen und Anleitungen zu finden. Wenn die bereitgestellte Anleitung nicht hilfreich ist, lösen Sie ein [Partner Center-Supportticket aus.](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket)

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Wie verwalte ich mein Office Store-Konto im Partner Center?

Weitere Informationen [finden Sie unter Manage your Office Store account through Partner Center.](/office/dev/store/manage-account-settings-and-profile)

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Wie füge ich meine Telefonnummer dem Abschnitt Partnerprofilkontakt hinzu?

Die Telefonnummer hat drei Teile, Ländercode, Vorwahl und Telefonnummer. Wenn Ihre Telefonnummer keine Vorwahl enthält, lassen Sie das zweite Feld leer, und füllen Sie das dritte Feld aus.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Wie verwalte ich meine Kontoeinstellungen und mein Partnerprofil im Partner Center?

Informationen zum [Verwalten](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) Ihrer Partner Center-Kontoeinstellungen finden Sie auf der Seite Kontoeinstellungen und Profilinformationen verwalten.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Warum erhalte ich die Meldung "Dieses Konto ist nicht berechtigt zu veröffentlichen", wenn ich versuche, mein Add-In über das Partner Center zu übermitteln?

Sie erhalten die obige Fehlermeldung, wenn der [Kontoüberprüfungsstatus](/partner-center/verification-responses) aussteht. Überprüfen Sie den Kontoüberprüfungsstatus im Partner [Center-Dashboard.](https://partner.microsoft.com/dashboard) Wählen **Sie Einstellungen** aus, das Zahnradsymbol in der oberen rechten Ecke der Seitenkopfshell. Wählen **Sie Entwicklereinstellungen**  =>     =>  **Kontokontoeinstellungen aus.**

![Seite "Partner Center-Kontoeinstellungen"](../../../assets/images/partner-center-accts-page.png)

![Status der Partner Center-Überprüfung](../../../assets/images/partner-center-verification-status.png)

Der Status der einzelnen erforderlichen Schritte, z. B. **E-Mail-Besitz,** Beschäftigungsüberprüfung und **Unternehmensüberprüfung,** wird im Kontoüberprüfungsprozess angezeigt. Nach Abschluss des Überprüfungsprozesses ändert sich der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von *ausstehend* in *autorisiert.* Die Prozessschritte werden nicht mehr angezeigt.

![Fehler bei der Partner Center-Überprüfung](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-the-partner-center-account-verification-process-and-how-to-respond"></a>Was wird im Überprüfungsprozess des Partner Center-Kontos überprüft und wie wird reagiert?
Es gibt drei Überprüfungsbereiche: **E-Mail-Besitz,** **Beschäftigung** und **Unternehmen.** Weitere Informationen zum Überprüfungsprozess finden Sie unter [Was überprüft wird und wie sie reagieren.](/partner-center/verification-responses#what-is-verified-and-how-to-respond)
Wenn Sie der primäre Kontakt, globaler Administrator oder Kontoadministrator sind, wechseln Sie zu Ihrem Partnerprofil, um den Überprüfungsstatus zu überwachen und den Fortschritt nachverfolgt.

Nach Abschluss des Überprüfungsprozesses ändert sich der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von *ausstehend* in *autorisiert.* Nach der Autorisierung sind die Prozessschritte und deren Status auf der Seite nicht mehr verfügbar. Der primäre Kontakt empfängt eine E-Mail von Microsoft innerhalb weniger Werktage nach Abschluss der Überprüfung.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-the-partner-center-how-should-i-proceed"></a>Der Überprüfungsstatus meines Kontos wurde nicht über den E-Mail-Besitz im Partner Center hinaus erweitert. Wie soll ich vorgehen?

Während der **Überprüfung des** E-Mail-Besitzes wird eine Überprüfungs-E-Mail an die primäre E-Mail-Adresse des Kontakts gesendet. Überprüfen Sie ihren primären Kontakt posteingang auf eine E-Mail von **maccount@<span>microsoft</span>.com** mit der Betreffzeile Aktion erforderlich: Überprüfen Ihres E-Mail-Kontos *bei Microsoft*. Schließen Sie den E-Mail-Überprüfungsprozess ab. Die Überprüfungs-E-Mail wird an die E-Mail-Adresse gesendet, die auf der Seite mit den Kontoeinstellungen im Partner Center aufgeführt ist.

> [!NOTE]
> * Der Link zur E-Mail-Überprüfung ist nur für sieben Tage gültig. 
> * Sie können uns bitten, die E-Mail erneut zu senden, indem Sie Ihre Partnerprofilseite besuchen und den **Link Überprüfung** erneut senden auswählen.
> * Um sicherzustellen, dass E-Mails empfangen werden, listen Sie die E-Mails von microsoft.com als sichere Domäne auf, und überprüfen Sie Ihre Junk-E-Mail-Ordner.

## <a name="how-do-i-get-further-support-for-my-account-related-issues"></a>Wie kann ich weitere Unterstützung für probleme im Zusammenhang mit meinem Konto erhalten?

Auf der [Seite Support für das Kommerzielle Marketplace-Programm im Partner Center](/azure/marketplace/partner-center-portal/support) finden Sie Anleitungen und Schritte zum Erstellen eines Supporttickets.

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what-must-i-do-next"></a>Ich habe meine E-Mail-Ordner überprüft und die Überprüfungs-E-Mail nicht erhalten. Was muss ich als Nächstes tun?

Versuchen Sie, das Problem durch folgende Maßnahme zu beheben:
* Überprüfen Sie Ihren Junk- oder Spamordner.
* Löschen Sie den Browsercache, wechseln Sie zu Ihrem Partner Center-Kontodashboard, und wählen Sie den Link **E-Mail-Überprüfung** erneut senden aus, damit die Überprüfungs-E-Mail erneut an Ihre E-Mail-Adresse gesendet wird.
* Versuchen Sie, über einen anderen Browser auf den **E-Mail-Link** Zum Erneuten Senden der Überprüfung zu zugreifen.
* Arbeiten Sie mit Ihrer IT-Abteilung zusammen, um sicherzustellen, dass die Überprüfungs-E-Mails nicht vom E-Mail-Server blockiert werden.
* Passen Sie den Spamfilter Ihres Servers so an, dass alle E-Mails von ihrem Server **maccount@microsoft. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Wie lange dauert die Überprüfung der Beschäftigung in der Regel?

Wenn alle übermittelten Details korrekt sind, dauert die Überprüfung der Beschäftigung etwa zwei Stunden.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Wie lange dauert der Geschäftsüberprüfungsprozess in der Regel?

Wenn alle erforderlichen Dokumente übermittelt werden, dauert die Geschäftsüberprüfung ein bis zwei Werktage.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Wenn ich mich an das Supportteam stütze, wird mein Ticket beschleunigt?

Supporttickets werden in einer Woche aufgelöst. Suchen Sie nach Updates, die an die E-Mail-ID gesendet werden, die beim Erhöhen des Supporttickets bereitgestellt wird.

## <a name="my-issue-is-not-listed-here-are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Mein Problem ist hier nicht aufgeführt. Gibt es weitere Seiten, auf die ich für Partner Center-Probleme verweisen kann?

Weitere Hilfe finden Sie [in der Kommerziellen](/azure/marketplace/) Marketplace-Dokumentation.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Ich habe ein Supportticket erstellt, es waren 7 Werktage, und ich habe kein Update erhalten. Wo kann ich zusätzliche Hilfe erhalten?

Senden Sie eine **<teamsubm@microsoft.com>** E-Mail mit den folgenden Details:

* **Betreffzeile**: Partner Center Account Issue for <App_Name> (geben Sie den Namen Ihrer App an).
* **E-Mail-Text:**
    * Supportticketnummer
    * Ihre Verkäufer-ID
    * Screenshot des Problems (wenn möglich)
    
## <a name="app-category-mapping"></a>Zuordnung von App-Kategorie

| Kategorie "Teams"       | KATEGORIEN FÜR PCs  |
|:---------------------|:---------------|
| Analytics und BI | Analyse, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Bildung | Bildung |
| Personalwesen | Personalwesen und Personalwerbung |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Dienstprogramme |
| Projektmanagement | Kommunikation, Projektverwaltung, Workflow und Unternehmensverwaltung |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzverwaltung, Vertrieb und Marketing |
| Soziales und Spaß | Bilder- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

>
> [!div class="nextstepaction"]
> [Weitere Informationen zu App-Validierungsrichtlinien für Microsoft Teams](/legal/marketplace/certification-policies)
