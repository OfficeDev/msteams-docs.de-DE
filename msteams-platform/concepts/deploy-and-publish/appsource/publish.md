---
title: Grundlegendes zum Übermittlungsprozess des Teams Store
description: Beschreibt den Genehmigungsübermittlungsprozess für die Veröffentlichung Ihrer App im Microsoft Teams App Store
ms.topic: overview
keywords: Teams veröffentlichen store office publishing appsource partner center account verification apps account not publish eligible app submission
ms.openlocfilehash: d2dc624c6dd13896397041c5c69ce5c5eb471a5b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014411"
---
# <a name="submit-your-app-to-appsource"></a>Übermitteln Ihrer App an AppSource

## <a name="teams-app-submission"></a>Übermittlung von Teams-Apps

Stellen Sie Ihre App im Microsoft Teams-App-Katalog und im Web zur Verfügung, indem Sie sie in [AppSource veröffentlichen.](https://appsource.microsoft.com) Auf hoher Ebene erfolgt die Übermittlung Ihrer App an AppSource wie folgt:

1. Entwickeln Sie Ihre App, indem Sie die [Entwurfsrichtlinien befolgen.](~/concepts/design/understand-use-cases.md) Registerkarten müssen den Richtlinien für den Registerkartenentwurf für Desktop, [Web und](~/tabs/design/tabs.md) [Mobile entsprechen.](~/tabs/design/tabs-mobile.md) Bots müssen die Richtlinien für [das Botdesign befolgen.](~/bots/design/bots.md)
1. Stellen Sie sicher, dass Ihre App die [App-Validierungsrichtlinien](/legal/marketplace/certification-policies) für Microsoft Teams erfüllt. 
1. Testen Sie Ihre App mit dem [Manifestüberprüfungstool.](prepare/submission-checklist.md#teams-app-validation-tool)
1. Richten Sie ein [Entwicklerkonto im](/office/dev/store/open-a-developer-account) [Partner Center ein.](https://support.microsoft.com/help/4499930/partner-center-overview) *Weitere Informationen finden* [Sie unter "Erstellen eines Partner Center-Kontos"](#how-do-i-create-a-partner-center-account) im Abschnitt "Häufig gestellte Fragen".
1. Bereiten Sie Ihre App für die Übermittlung vor, indem Sie der [Prüfliste für die Übermittlung folgen.](prepare/submission-checklist.md)
1. Überprüfen Sie die [am häufigsten fehlgeschlagenen Testfälle, um eine schnellere Genehmigung der App-Qualität zu erhalten.](prepare/frequently-failed-cases.md)
1. Übermitteln Sie Ihr Paket [über Partner Center an AppSource.](/office/dev/store/use-partner-center-to-submit-to-appsource)
1. Verfolgen Sie den Genehmigungsprozess auf Ihrem Partner Center-Dashboard. *Weitere Informationen* [finden Sie im Partner Center ( Übersicht).](https://support.microsoft.com/help/4499930/partner-center-overview)
1. Lesen Sie nach der Übermittlung die Anleitungen für [die Wartung und Unterstützung Ihrer veröffentlichten App.](post-publish/overview.md)

>[!NOTE]
>
>- Ihre Teams-App muss mobil reagieren und keine [Upsellanforderungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) für mobile Betriebssysteme (iOS und Android) erfüllen. 
>- Wenn Ihre Teams-App einen Bot enthält, müssen Sie den Verhaltensregeln des Bot Developer Framework [einhalten.](https://aka.ms/bf-conduct)
>- Wenn Ihre App einen Office 365-Connector enthält, können zusätzliche Bedingungen gelten. Siehe [Entwicklerdashboard und](https://aka.ms/connectorsdashboard) [Vereinbarung für App-Entwickler für Connectors.](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm)
>- Um Ihre App für Benutzer der Government Community Cloud (GCC) verfügbar zu machen und doppelte App-Einträge im Store zu vermeiden, muss der Authentifizierungsprozess oder -fluss den Benutzer identifizieren und an die angegebene oder erwartete Inhalts-URL für die Benutzer des GCC weiterverfassen.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>HÄUFIG gestellte Fragen – Prozess der Überprüfung von Teams-Apps und -Partnerkontos im Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Wie erstelle ich ein Partner Center-Konto?

Es gibt zwei Möglichkeiten zum Erstellen eines Partner Center-Kontos:

- Wenn Sie noch nicht mit Partner Center verbunden sind und kein Konto im Microsoft Network haben, erstellen Sie ein Konto auf der [Partner Center-Registrierungsseite.](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment)
- Wenn Sie bereits im Partner Network registriert sind, erstellen Sie ein Konto direkt im Partner Center mithilfe einer [vorhandenen Registrierungsseite.](/office/dev/store/)

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>Was passiert, wenn ich mein Office Store-Konto im Partner Center nicht finden kann?

Öffnen Sie [ein Partner Center-Supportticket,](https://partner.microsoft.com/support/v2/?stage=1) und wählen Sie in den Dropdownmenüs Folgendes aus:

| Menü | Option |
| -------   | -------  |
|Kategorie| Commercial Marketplace|
| Thema | Allgemeine Hilfe und Fragen zur Funktionsweise von Marketplace |
| Untertopisch| Office-Add-In |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Wo kann ich Support für Probleme mit meinem Partner Center-Konto erhalten?

Besuchen Sie [die Supportseite der Herausgeber,](https://aka.ms/marketplacepublishersupport) um nach Ihrem Problemthema zu suchen und Anleitungen zu finden. Wenn die bereitgestellte Anleitung nicht hilfreich ist, lösen Sie ein [Partner Center-Supportticket aus.](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket)

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Wie verwalte ich mein Office Store-Konto im Partner Center?

Eine Anleitung [finden Sie im Partner Center zum](/office/dev/store/manage-account-settings-and-profile) Verwalten Ihres Office Store-Kontos.

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Wie füge ich meine Telefonnummer dem Kontaktabschnitt des Partnerprofils hinzu?

Die Telefonnummer hat drei Teile, Landes-, Orts- und Telefonnummer. Wenn Ihre Telefonnummer keine Vorwahl enthält, lassen Sie das zweite Feld leer, und füllen Sie das dritte Feld aus.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Wie verwalte ich meine Kontoeinstellungen und mein Partnerprofil im Partner Center?

Auf der [Seite "Kontoeinstellungen und Profilinformationen verwalten"](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) finden Sie Anleitungen zum Verwalten ihrer Partner Center-Kontoeinstellungen.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Warum erhalte ich die Meldung "Dieses Konto ist nicht veröffentlichungsberechtigt", wenn ich versuche, mein Add-in über Partner Center zu übermitteln?

Sie erhalten die oben aufgeführte Fehlermeldung, wenn [der Kontoüberprüfungsstatus](/partner-center/verification-responses) aussteht. Überprüfen Sie den Kontoüberprüfungsstatus im Partner [Center-Dashboard.](https://partner.microsoft.com/dashboard) Select **Settings**, the gear icon in the upper-right corner of the page header shell. Choose **Developer settings**  =>  **Account** Account   =>  **settings**.

![Seite "Partner Center-Kontoeinstellungen"](../../../assets/images/partner-center-accts-page.png)

![Überprüfungsstatus des Partner Centers](../../../assets/images/partner-center-verification-status.png)

Der Status jedes erforderlichen Schritts, z. B. E-Mail-Besitz, Anstellungsüberprüfung und Geschäftsüberprüfung, wird im Kontoüberprüfungsprozess angezeigt. Nach Abschluss des Überprüfungsprozesses ändert sich der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von *ausstehend* in *autorisiert.* Die Prozessschritte werden nicht mehr angezeigt.

![Überprüfungsfehler im Partner Center](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-the-partner-center-account-verification-process-and-how-to-respond"></a>Was wird im Partner Center-Konto-Überprüfungsprozess überprüft und wie kann ich darauf reagieren?
Es gibt drei Überprüfungsbereiche: **E-Mail-Besitz,** **Anstellung** und **Unternehmen.** Weitere Informationen zum Überprüfungsprozess finden Sie unter [Was überprüft wird und wie reagiert wird.](/partner-center/verification-responses#what-is-verified-and-how-to-respond)
Wenn Sie der primäre Kontakt, globaler Administrator oder Kontoadministrator sind, wechseln Sie zu Ihrem Partnerprofil, um den Überprüfungsstatus zu überwachen und den Fortschritt nachverfolgt.

Nach Abschluss des Überprüfungsprozesses ändert sich der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von *ausstehend in* *autorisiert.* Nach der Autorisierung sind die Prozessschritte und ihr Status nicht mehr auf der Seite verfügbar. Der primäre Kontakt erhält innerhalb weniger Werktage nach Abschluss der Überprüfung eine E-Mail von Microsoft.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-the-partner-center-how-should-i-proceed"></a>Der Überprüfungsstatus meines Kontos wurde nicht über den E-Mail-Besitz im Partner Center hinaus erweitert. Wie soll ich vorgehen?

Während der **Überprüfung des E-Mail-Besitzes** wird eine E-Mail-Überprüfung an die primäre Kontakt-E-Mail-Adresse gesendet. Check your primary contact inbox for an email from **maccount@<span>microsoft</span>.com** with the subject line *Action needed: Verify your email account with Microsoft*. Schließen Sie den E-Mail-Überprüfungsprozess ab. Die Überprüfungs-E-Mail wird an die E-Mail-Adresse gesendet, die auf der Seite mit den Kontoeinstellungen im Partner Center aufgeführt ist.

> [!NOTE]
> * Der E-Mail-Überprüfungslink ist nur für sieben Tage gültig. 
> * Sie können uns bitten, die E-Mail erneut zu senden, indem Sie Ihre Partnerprofilseite besuchen und den Link "Überprüfungs-E-Mail **erneut senden"** auswählen.
> * Um sicherzustellen, dass E-Mails empfangen werden, listen Sie die E-Mails von microsoft.com als sichere Domäne auf, und überprüfen Sie Ihre Junk-E-Mail-Ordner.

## <a name="how-do-i-get-further-support-for-my-account-related-issues"></a>Wie kann ich weitere Unterstützung für Probleme im Zusammenhang mit meinem Konto erhalten?

Auf der [Seite "Support für das Commercial Marketplace-Programm" im Partner Center](/azure/marketplace/partner-center-portal/support) finden Sie Anleitungen und Schritte zum Erstellen eines Supporttickets.

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what-must-i-do-next"></a>Ich habe meine E-Mail-Ordner überprüft und habe die Überprüfungs-E-Mail nicht erhalten. Was muss ich als Nächstes tun?

Versuchen Sie, das Problem durch folgende Maßnahme zu beheben:
* Überprüfen Sie Ihren Junk- oder Spamordner.
* Löschen Sie den Browsercache, wechseln Sie zu  Ihrem Partner Center-Konto-Dashboard, und wählen Sie den Link "Überprüfungs-E-Mail erneut senden" aus, damit die Überprüfungs-E-Mail erneut an Ihre E-Mail-Adresse gesendet wird.
* Versuchen Sie, von einem anderen Browser aus auf **den** Link "Überprüfungs-E-Mail erneut senden" zu zugreifen.
* Arbeiten Sie mit Ihrer IT-Abteilung zusammen, um sicherzustellen, dass die Überprüfungs-E-Mails nicht vom E-Mail-Server blockiert werden.
* Passen Sie den Spamfilter Ihres Servers an, um alle E-Mails von Ihrem Server zu erlauben **oder maccount@microsoft. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Wie lange dauert die Überprüfung der Beschäftigung in der Regel?

Wenn alle übermittelten Details korrekt sind, dauert die Überprüfung der Beschäftigung etwa zwei Stunden.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Wie lange dauert der Geschäftsüberprüfungsprozess in der Regel?

Wenn alle erforderlichen Dokumente übermittelt werden, dauert die Geschäftsüberprüfung ein bis zwei Werktage.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Wird mein Ticket beschleunigt, wenn ich mich an das Supportteam erfahre?

Supporttickets werden in einer Woche aufgelöst. Suchen Sie nach Updates, die an die E-Mail-ID gesendet werden, die beim Erhöhen des Supporttickets bereitgestellt wird.

## <a name="my-issue-is-not-listed-here-are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Mein Problem ist hier nicht aufgeführt. Gibt es weitere Seiten, auf die ich bei Problemen im Partner Center verweisen kann?

Weitere Hilfe [finden Sie in der Dokumentation zum](/azure/marketplace/) kommerziellen Marketplace.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Ich habe ein Supportticket erstellt, es hat 7 Werktage gezeit, und ich habe kein Update erhalten. Wo kann ich weitere Hilfe erhalten?

Senden Sie eine **<teamsubm@microsoft.com>** E-Mail mit den folgenden Details an:

* **Betreffzeile**: Partner Center Account Issue for <App_Name> (geben Sie den Namen Ihrer App an).
* **E-Mail-Text:**
    * Supportticketnummer
    * Ihre Verkäufer-ID
    * Screenshot des Problems (wenn möglich)
    
## <a name="app-category-mapping"></a>Zuordnung der App-Kategorie

| Kategorie "Teams"       | Kategorien für PCs  |
|:---------------------|:---------------|
| Analysen und BI | Analysen, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Education | Education |
| Personalwesen | Personalwesen und Einstellung |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Dienstprogramme |
| Projektmanagement | Kommunikation, Projektmanagement, Workflow und Geschäftsmanagement |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzmanagement, Vertrieb und Marketing |
| Soziales und Spaß | Bilder- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

>
> [!div class="nextstepaction"]
> [Weitere Informationen zu App-Validierungsrichtlinien für Microsoft Teams](/legal/marketplace/certification-policies)
