---
title: Anleitung zum Übermittlungsprozess für die Genehmigung von Microsoft Teams-Apps
description: Beschreibt den Übermittlungsgenehmigungsprozess für die Veröffentlichung Ihrer App im Microsoft Teams-App-Store
keywords: Teams veröffentlichen store office publishing appsource partner center account verification apps account not publish eligible
ms.openlocfilehash: 6268d408cc4c44633b9b3629c902044815639176
ms.sourcegitcommit: db19fee033b41152267bb524d67aee5b7f64b04a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797482"
---
# <a name="submit-your-app-to-appsource"></a>Übermitteln Ihrer App an AppSource

## <a name="teams-app-submission"></a>Übermittlung von Teams-Apps

Wenn Sie Ihre App in [AppSource veröffentlichen,](https://appsource.microsoft.com) wird sie im Teams-App-Katalog und im Web verfügbar. Auf hoher Ebene ist der Prozess für die Übermittlung Ihrer App an AppSource:

1. Entwickeln Sie Ihre App, indem Sie die [Entwurfsrichtlinien befolgen.](~/concepts/design/understand-use-cases.md) Registerkarten müssen den Richtlinien für den Registerkartenentwurf für Desktop und [Web und](~/tabs/design/tabs.md) mobile [Geräte entsprechen.](~/tabs/design/tabs-mobile.md) Bots müssen die Richtlinien für [das Botdesign befolgen.](~/bots/design/bots.md)
1. Stellen Sie sicher, dass Ihre App die [App-Validierungsrichtlinien](/legal/marketplace/certification-policies) für Microsoft Teams erfüllt. 
1. Testen Sie Ihre App selbst mit dem [Manifestüberprüfungstool.](prepare/submission-checklist.md#teams-app-validation-tool)
1. [Richten Sie ein Entwicklerkonto](/office/dev/store/open-a-developer-account) im [Partner Center ein.](https://support.microsoft.com/help/4499930/partner-center-overview) *Weitere Informationen finden* [Sie unter "Erstellen eines Partner Center-Kontos"](#how-do-i-create-a-partner-center-account) im Abschnitt "Häufig gestellte Fragen" weiter unten.
1. Bereiten Sie Ihre App für die Übermittlung vor, indem Sie unserer [Prüfliste für die Übermittlung folgen.](prepare/submission-checklist.md)
1. Überprüfen Sie die [am häufigsten fehlgeschlagenen Testfälle, um eine schnellere Genehmigung der App-Qualität zu erhalten.](prepare/frequently-failed-cases.md)
1. Übermitteln Sie Ihr Paket [über Partner Center an AppSource.](/office/dev/store/use-partner-center-to-submit-to-appsource)
1. Verfolgen Sie den Genehmigungsprozess auf Ihrem Partner Center-Dashboard. *Weitere Informationen* [finden Sie im Partner Center ( Übersicht).](https://support.microsoft.com/help/4499930/partner-center-overview)
1. Nach der Übermittlung – lesen Sie unsere Anleitungen für [die Wartung und Unterstützung Ihrer veröffentlichten App.](post-publish/overview.md)

>[!NOTE]
>
>- Ihre Teams-App muss mobil reagieren und keine [Upsellanforderungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) für mobile Betriebssysteme (iOS und Android) erfüllen. 
>- Wenn Ihre Teams-App einen Bot enthält, müssen Sie den Verhaltensregeln des Bot Developer Framework [einhalten.](https://aka.ms/bf-conduct)
>- Wenn Ihre App einen Office 365-Connector enthält, können zusätzliche Bedingungen gelten. *Siehe* [Entwicklerdashboard und](https://aka.ms/connectorsdashboard) Vereinbarung für [App-Entwickler für Connectors.](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm)
>- Um Ihre App für GCC-Benutzer verfügbar zu machen und doppelte App-Einträge im Store zu vermeiden, sollte der Authentifizierungsprozess/-fluss den Benutzer identifizieren und an die angegebene/erwartete Inhalts-URL für die Benutzer des GCC weiterverfassen.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>HÄUFIG gestellte Fragen – Prozess der Überprüfung von Teams-Apps und -Partnerkontos im Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Wie erstelle ich ein Partner Center-Konto?

Es gibt zwei Möglichkeiten zum Erstellen eines Partner Center-Kontos:

- Wenn Sie noch nicht im Partner Center sind und kein Konto im Microsoft Network haben, erstellen Sie ein Konto auf der [Partner Center-Registrierungsseite.](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment)
- Wenn Sie bereits im Partner Network registriert sind, erstellen Sie ein Konto direkt im Partner Center mithilfe [einer vorhandenen Registrierung.](/office/dev/store/)

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>Was passiert, wenn ich mein Office Store-Konto im Partner Center nicht finden kann?

Öffnen Sie ein [Partner Center-Supportticket,](https://partner.microsoft.com/support/v2/?stage=1) und wählen Sie in den Dropdownmenüs Folgendes aus:

| Menü | Option |
| -------   | -------  |
|Kategorie| Commercial Marketplace|
| Thema | Allgemeine Hilfe und Fragen zu "How-to" in Marketplace |
| Untertopisch| Office-Add-In |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Wo kann ich Support für Probleme mit meinem Partner Center-Konto erhalten?

Besuchen Sie unsere [Supportseite für Herausgeber,](https://aka.ms/marketplacepublishersupport) um nach Ihrem Problemthema zu suchen und Anleitungen zu finden. Wenn die bereitgestellte Anleitung nicht hilfreich ist, [öffnen Sie ein Partner Center-Supportticket.](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket)

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Wie verwalte ich mein Office Store-Konto im Partner Center?

Besuchen Sie unser  [Office Store-Konto verwalten im Partner Center,](/office/dev/store/manage-account-settings-and-profile) um Anleitungen zum Verwalten Ihres Office Store-Kontos über Partner Center zu erhalten.

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Wie füge ich meine Telefonnummer dem Kontaktabschnitt des Partnerprofils hinzu?

Die Telefonnummer hat drei Teile: Landes-, Orts- und Telefonnummer. Wenn Ihre Telefonnummer keine Vorwahl enthält, lassen Sie das zweite Feld leer, und füllen Sie das dritte Feld aus.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Wie verwalte ich meine Kontoeinstellungen und mein Partnerprofil im Partner Center?

Besuchen Sie unsere Seite ["Kontoeinstellungen und Profilinformationen verwalten",](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) um Anleitungen zum Verwalten ihrer Partner Center-Kontoeinstellungen zu erhalten.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Warum erhalte ich die Meldung "Dieses Konto ist nicht veröffentlichungsberechtigt", wenn ich versuche, mein Add-in über Partner Center zu übermitteln?

Die oben aufgeführte Fehlermeldung wird angezeigt, wenn der [Kontoüberprüfungsstatus](/partner-center/verification-responses) aussteht. Sie können den Kontoüberprüfungsstatus im Partner   [Center-Dashboard](https://partner.microsoft.com/dashboard) überprüfen, indem Sie in der oberen rechten Ecke der Seitenkopfshell die Option "Einstellungen" (Zahnradsymbol) und die Kontoeinstellungen für Entwicklereinstellungen  =>     =>  **auswählen.**

![Seite "Partner Center-Kontoeinstellungen"](../../../assets/images/partner-center-accts-page.png)

![Überprüfungsstatus des Partner Centers](../../../assets/images/partner-center-verification-status.png)

Während des Kontoüberprüfungsprozesses wird der Status jedes erforderlichen Schritts – E-Mail-Besitz, Anstellungsüberprüfung und Unternehmensüberprüfung – angezeigt. Nachdem der Überprüfungsprozess erfolgreich abgeschlossen wurde, ändert sich der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von "Ausstehend" in "Autorisiert", und die Prozessschritte werden nicht mehr angezeigt.

![Fehler bei der Partner Center-Überprüfung](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-partner-center-account-verification-process-and-how-to-respond"></a>Was wird im Partner Center-Konto-Überprüfungsprozess überprüft und wie kann ich darauf reagieren?
Es gibt drei Überprüfungsbereiche: E-Mail-Besitz, Anstellung und Unternehmen. Bitte sehen Sie [](/partner-center/verification-responses#what-is-verified-and-how-to-respond) sich die Details der Überprüften an und erfahren, wie Sie antworten können, wenn Sie der primäre Kontakt (globaler Administrator oder Kontoadministrator) sind, sollten Sie zu Ihrem Partnerprofil wechseln, um den Überprüfungsstatus zu überwachen und den Fortschritt nachverfolgt.

Sobald der Überprüfungsprozess abgeschlossen ist, ändert sich der Überprüfungsstatus  Ihrer Registrierung auf der Profilseite von *"Ausstehend"* in "Autorisiert", und die Prozessschritte mit dem Status, die auf dieser Seite angezeigt werden, werden nicht mehr angezeigt. Der primäre Kontakt erhält innerhalb weniger Werktage nach Abschluss der Überprüfung eine E-Mail von Microsoft.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-partner-center-how-should-i-proceed"></a>Der Überprüfungsstatus meines Kontos wurde nicht über den E-Mail-Besitz im Partner Center hinaus erweitert. Wie soll ich vorgehen?

Während der **Überprüfung des E-Mail-Besitzes** wird eine E-Mail-Überprüfung an die primäre Kontakt-E-Mail-Adresse gesendet. Überprüfen Sie den Posteingang Ihres primären Kontakts auf eine E-Mail von **maccount@<span>microsoft</span>.com** mit der erforderlichen Betreffzeile Aktion: Überprüfen Sie Ihr E-Mail-Konto bei *Microsoft,* und fordern Sie an, den E-Mail-Überprüfungsprozess zu abschließen. Die Überprüfungs-E-Mail wird an die E-Mail-Adresse gesendet, die auf der Seite mit den Kontoeinstellungen im Partner Center aufgeführt ist.

> [!NOTE]
 >Der E-Mail-Überprüfungslink ist nur 7 Tage gültig. Sie können anfordern, dass wir die E-Mail erneut an Sie senden, indem Sie Ihre Partnerprofilseite besuchen und den Link "Bestätigungs-E-Mail **erneut senden"** auswählen. Um sicherzustellen, dass die E-Mail empfangen wird, listen Sie E-Mails von microsoft.com als sichere Domäne auf, und überprüfen Sie Ihre Junk-E-Mail-Ordner.

## <a name="how-i-do-get-further-support-for-my-account-related-issues"></a>Wie kann ich weitere Unterstützung für Probleme im Zusammenhang mit meinem Konto erhalten?

Besuchen Sie unseren [Support für das Commercial Marketplace-Programm im Partner Center,](/azure/marketplace/partner-center-portal/support) um Anleitungen und Schritte zum Erstellen eines Supporttickets zu erhalten.

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what--should-i-do-next"></a>Ich habe meine E-Mail-Ordner überprüft und habe die Überprüfungs-E-Mail nicht erhalten. Was soll ich als Nächstes tun?

Versuchen Sie Folgendes:

1. Überprüfen Sie Ihren Junk-/Spamordner.
1. Löschen Sie den Browsercache, wechseln Sie zu  Ihrem Partner Center-Konto-Dashboard, und wählen Sie den Link "Überprüfungs-E-Mail erneut senden" aus, damit die Überprüfungs-E-Mail erneut an Ihre E-Mail-Adresse gesendet wird.
1. Versuchen Sie, von einem anderen Browser aus auf  **den** Link "Überprüfungs-E-Mail erneut senden" zu zugreifen.
1. Arbeiten Sie mit Ihrer IT-Abteilung zusammen, um sicherzustellen, dass die Überprüfungs-E-Mails nicht vom E-Mail-Server blockiert werden.
1. Passen Sie den Spamfilter Ihres Servers so an, dass alle E-Mails von diesem Server **maccount@microsoft. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Wie lange dauert die Überprüfung der Beschäftigung in der Regel?

Wenn alle übermittelten Details korrekt sind, wird die Überprüfung der Beschäftigung in 1 bis 2 Stunden abgeschlossen.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Wie lange dauert der Prozess der Geschäftsüberprüfung in der Regel?

Die Geschäftsüberprüfung dauert 1 bis 2 Werktage, vorausgesetzt, alle erforderlichen Dokumente wurden übermittelt.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Wird mein Ticket beschleunigt, wenn ich mich an das Supportteam erfahre?

Supporttickets werden innerhalb einer Woche aufgelöst. Suchen Sie nach den Updates, die an die E-Mail gesendet werden, die beim Lösen des Supporttickets bereitgestellt wurde.

## <a name="my-issue-is-not-listed-here--are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Mein Problem ist hier nicht aufgeführt.  Gibt es weitere Seiten, auf die ich bei Problemen im Partner Center verweisen kann?

Weitere Hilfe finden Sie in der [Dokumentation zum](/azure/marketplace/) kommerziellen Marketplace.

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Ich habe ein Supportticket erstellt, es hat 7 Werktage gezeit, und ich habe kein Update erhalten. Wo kann ich weitere Hilfe erhalten?

Senden Sie eine E-Mail **<teamsubm@microsoft.com>** mit den folgenden Details an:

1. **Betreffzeile**. *Partner Center Account Issue for <App_Name>* (geben Sie den Namen Ihrer App an).
1. **E-Mail-Nachrichtentext:**
    * Supportticketnummer:
    * Ihre Verkäufer-ID:
    * Screenshot des Problems (wenn möglich):
    
## <a name="app-category-mapping"></a>Zuordnung der App-Kategorie

| Kategorie "Teams"       | Kategorien für PCs  |
|:---------------------|:---------------|
| Analysen und BI | Analysen, Datenvisualisierung und BI |
| Entwickler und IT | Entwicklertools, IT-Administrator |
| Schulung und Weiterbildung | Schulung und Weiterbildung |
| Personalwesen | Personalwesen und Einstellung |
| Produktivität | Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Dienstprogramme |
| Projektmanagement | Kommunikation, Projektmanagement, Workflow- und Geschäftsmanagement |
| Vertrieb und Support | Kunden- und Kontaktverwaltung, Kundensupport, Finanzmanagement, Vertrieb und Marketing |
| Soziales und Spaß | Bilder- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation |

>
> [!div class="nextstepaction"]
> [Weitere Informationen zu App-Validierungsrichtlinien für Microsoft Teams](/legal/marketplace/certification-policies)
