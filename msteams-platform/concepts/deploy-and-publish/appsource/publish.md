---
title: Prozessleitfaden für den Microsoft Teams-App-Genehmigungsantrag
description: Beschreibt den Prozess der Übermittlungs Genehmigung für die Veröffentlichung Ihrer APP im Microsoft Teams-App-Store.
keywords: Microsoft Teams Publish Store Office Publishing veröffentlichen AppSource Partner Center-Kontoüberprüfung Apps-Konto nicht veröffentlicht berechtigt
ms.openlocfilehash: 6cc38e29d02935cf023bb26d3a317554493b0fe2
ms.sourcegitcommit: 25afe104d10c9a6a2849decf5ec1d08969d827c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "48465929"
---
# <a name="submit-your-app-to-appsource"></a>Übermitteln Ihrer APP an AppSource

## <a name="teams-app-submission"></a>Teams-App-Übermittlung

Wenn Sie Ihre APP in [AppSource](https://appsource.microsoft.com) veröffentlichen, ist Sie im Microsoft Teams-App-Katalog und im Internet verfügbar. Auf hohem Niveau ist der Prozess für die Übermittlung Ihrer APP an AppSource:

1. Entwickeln Sie Ihre APP nach unseren [Entwurfsrichtlinien](~/concepts/design/understand-use-cases.md). Registerkarten sollten den [Entwurfsrichtlinien für die Registerkarte](~/tabs/design/tabs.md)entsprechen. Bots sollten den [bot-Entwurfsrichtlinien](~/bots/design/bots.md)folgen.
1. Stellen Sie sicher, dass Ihre APP die APP- [Validierungsrichtlinien](/legal/marketplace/certification-policies) für Microsoft Teams erfüllt.
1. [Richten Sie ein Entwicklerkonto](/office/dev/store/open-a-developer-account) im [Partner Center](https://support.microsoft.com/help/4499930/partner-center-overview)ein. *Siehe auch* [wie erstelle ich ein Partner Center-Konto](#how-do-i-create-a-partner-center-account) im Abschnitt häufig gestellte Fragen, unten.
1. Bereiten Sie Ihre APP für die Übermittlung vor, indem Sie unsere [Zulassungs Checkliste](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)befolgen.
1. Lesen Sie unsere [Tipps für eine erfolgreiche App-Übermittlung](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md).
1. Übermitteln Sie Ihr Paket [über das Partner Center an AppSource](/office/dev/store/use-partner-center-to-submit-to-appsource).
1. Verfolgen Sie den Genehmigungsprozess im Partner Center-Dashboard. *Siehe* [Partner Center (Übersicht](https://support.microsoft.com/help/4499930/partner-center-overview)).
1. Post Submitting – lesen Sie unsere Anleitung zum [warten und unterstützen Ihrer veröffentlichten App](~/concepts/deploy-and-publish/appsource/post-publish/overview.md).

>[!NOTE]
>
>- Wenn Ihre Teams-APP einen bot enthält, müssen Sie den [Code of Conduct für](https://aka.ms/bf-conduct)den bot Developer Framework einhalten.
>- Wenn Ihre APP einen Office 365 Connector enthält, gelten möglicherweise zusätzliche Bedingungen. *Weitere Informationen finden Sie unter* [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard) und [App Developer Agreement](https://sellerdashboard.microsoft.com/Assets/Content/Agreements/Office_Store_Seller_Agreement_20120927.htm).
>- Um Ihre APP für gcc-Benutzer verfügbar zu machen und doppelte App-Auflistungen im Store zu vermeiden, sollte der Authentifizierungsprozess/-Ablauf den Benutzer identifizieren und an die angegebene/erwartete Inhalts-URL für gcc-Benutzer weiterleiten.

## <a name="faqs--teams-apps-and-partner-account-verification-process-in-partner-center"></a>FAQs – Microsoft Teams-apps und Partnerkonto Verifizierungsprozess im Partner Center

## <a name="how-do-i-create-a-partner-center-account"></a>Wie erstelle ich ein Partner Center-Konto?

Es gibt zwei Möglichkeiten, ein Partner Center-Konto zu erstellen:

- Wenn Sie noch nicht im Partner Center sind und kein Konto im Microsoft-Netzwerk haben, [Erstellen Sie ein Konto über die Seite Partner Center-Registrierung](/office/dev/store/open-a-developer-account#create-an-account-using-an-existing-partner-center-enrollment).
- Wenn Sie bereits im Partnernetzwerk registriert sind, [Erstellen Sie ein Konto direkt im Partner Center unter Verwendung einer vorhandenen Registrierung](/office/dev/store/).

## <a name="what-if-i-cannot-find-my-office-store-account-in-partner-center"></a>Was kann ich tun, wenn ich mein Office Store-Konto im Partner Center nicht finde?

Öffnen Sie ein [Partner Center Support Ticket](https://partner.microsoft.com/support/v2/?stage=1) , und wählen Sie in den Dropdownmenüs Folgendes aus:

| Menü | Option |
| -------   | -------  |
|Kategorie| Kommerzieller Marktplatz|
| Thema | Allgemeine Marketplace-Hilfe und Vorgehens Fragen |
| Subtopic| Office-Add-In |

## <a name="where-can-i-get-support-for-my-partner-center-account-issues"></a>Wo erhalte ich Unterstützung für meine Partner Center-Konto Probleme?

Besuchen Sie die [Seite Publisher-Support](https://aka.ms/marketplacepublishersupport) , um nach Ihrem Problemthema zu suchen und Anleitungen zu finden. Wenn die bereitgestellten Anleitungen nicht hilfreich sind, [Öffnen Sie ein Partner Center-Support Ticket](/azure/marketplace/partner-center-portal/support#how-to-open-a-support-ticket).

## <a name="how-do-i-manage-my-office-store-account-in-partner-center"></a>Wie verwalte ich mein Office Store-Konto im Partner Center?

Weitere Informationen zum Verwalten Ihres Office Store-Kontos über das Partner Center finden Sie  [in unserem Office Store-Konto verwalten im Partner Center](/office/dev/store/manage-account-settings-and-profile) .

## <a name="how-do-i-add-my-phone-number-to-the-partner-profile-contact-section"></a>Wie füge ich meine Telefonnummer zum Kontaktbereich des Partnerprofils hinzu?

Die Telefonnummer besteht aus drei Teilen: Ländervorwahl, Ortsvorwahl und Telefonnummer. Wenn Ihre Telefonnummer keine Ortskennzahl enthält, lassen Sie das zweite Feld leer, und füllen Sie das dritte Feld aus.

## <a name="how-do-i-manage-my-account-settings-and-partner-profile-in-partner-center"></a>Wie verwalte ich meine Kontoeinstellungen und das Partnerprofil im Partner Center?

Auf unserer Seite [Kontoeinstellungen und Profilinformationen verwalten](/windows/uwp/publish/manage-account-settings-and-profile#additional-settings-and-info) finden Sie Anleitungen zum Verwalten der Einstellungen Ihres Partner Center-Kontos.

## <a name="why-do-i-receive-the-message-this-account-is-not-publish-eligible-when-i-try-to-submit-my-add-in-through-partner-center"></a>Warum erhalte ich die Meldung "dieses Konto ist nicht veröffentlicht?", wenn ich versuche, mein Add-in über das Partner Center zu übermitteln?

Die obige Fehlermeldung wird angezeigt, wenn der [Status Ihrer Kontoüberprüfung](/partner-center/verification-responses) aussteht. Sie können den Status der Kontoüberprüfung im Partner Center- [Dashboard](https://partner.microsoft.com/dashboard) überprüfen, indem Sie die Option **Einstellungen** (Zahnradsymbol) in der oberen rechten Ecke der Seitenkopf Schale auswählen und die Einstellungen für das Konto Konto für **Entwicklereinstellungen**auswählen  =>  **Account**   =>  **Account settings** .

![Seite "Partner Center-Kontoeinstellungen"](../../../assets/images/partner-center-accts-page.png)

![Partner Center-Überprüfungsstatus](../../../assets/images/partner-center-verification-status.png)

Während des Konto Überprüfungsprozesses wird der Status jedes erforderlichen Schritts (e-Mail-Besitz, Überprüfung der Arbeitsplätze und Unternehmens Verifizierung) angezeigt. Nachdem der Überprüfungsvorgang erfolgreich abgeschlossen wurde, ändert sich der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von "Ausstehend" in "autorisiert", und die Prozessschritte werden nicht mehr angezeigt.

![Partner Center-Überprüfungsfehler](../../../assets/images/partner-center-acct-verification-error.png)

## <a name="what-is-verified-in-partner-center-account-verification-process-and-how-to-respond"></a>Was wird im Verifizierungsprozess des Partner Center-Kontos überprüft und wie Sie darauf reagieren?
Es gibt drei Überprüfungs Bereiche – e-Mail-Besitz, Beschäftigung und Unternehmen. Informationen dazu, [Was überprüft wird und wie Sie Antworten](/partner-center/verification-responses#what-is-verified-and-how-to-respond) können, wenn Sie der primäre Kontakt (globaler Administrator oder Konto Administrator) sind, wird empfohlen, dass Sie zu Ihrem Partner Profil wechseln, um den Überprüfungsstatus zu überwachen und den Fortschritt nachzuverfolgen.

Sobald der Überprüfungsvorgang abgeschlossen ist, wird der Überprüfungsstatus Ihrer Registrierung auf der Profilseite von *Ausstehend* zu *autorisiert* geändert, und die Prozessschritte mit dem Status, die auf dieser Seite angezeigt werden, werden ausgeblendet. Der primäre Kontakt erhält innerhalb weniger Werktage nach Abschluss der Überprüfung eine e-Mail von Microsoft.

## <a name="my-account-verification-status-has-not-advanced-beyond-email-ownership-in-partner-center-how-should-i-proceed"></a>Der Status "meine Kontoüberprüfung" wurde nicht über den e-Mail-Besitz im Partner Center hinaus erweitert. Wie sollte ich vorgehen?

Während der Überprüfung des **e-Mail-Eigentums** wird eine Bestätigungs-e-Mail an die primäre Kontakt-e-Mail-Adresse gesendet. Überprüfen Sie Ihren primären Kontakt Posteingang auf eine e-Mail von **Maccount@<span>Microsoft</span>. com** mit der *erforderlichen Betreffzeile: Überprüfen Sie Ihr e-Mail-Konto bei Microsoft*, indem Sie den e-Mail-Verifizierungsvorgang abschließen. Die Bestätigungs-e-Mail wird an die e-Mail-Adresse gesendet, die auf der Seite Kontoeinstellungen im Partner Center aufgeführt ist.

> [!NOTE]
 >Der Link zur e-Mail-Überprüfung ist nur 7 Tage gültig. Sie können anfordern, dass wir die e-Mail erneut an Sie senden, indem Sie Ihre Partnerprofil Seite besuchen und den Link zur über **Prüfung der Bestätigung erneut senden** auswählen. Um sicherzustellen, dass die e-Mail empfangen wird, werden e-Mails von Microsoft.com als sichere Domäne von der e-Mail-Adresse geschützt und Ihre Junk-e-Mail-Ordner überprüft.

## <a name="how-i-do-get-further-support-for-my-account-related-issues"></a>Wie erhalte ich weitere Unterstützung für meine Konto bezogenen Probleme?

Anleitungen und Schritte zum Erstellen eines Support Tickets finden Sie [unter Support für das Programm "Commercial Marketplace" auf der Seite "Partner Center](/azure/marketplace/partner-center-portal/support) ".

## <a name="ive-checked-my-mail-folders-and-havent-received-the-verification-email-what--should-i-do-next"></a>Ich habe meine e-Mail-Ordner überprüft und die Bestätigungs-e-Mail nicht erhalten. Was muss ich als nächstes tun?

Versuchen Sie Folgendes:

1. Überprüfen Sie Ihren Junk-Spam-Ordner.
1. Löschen Sie den Browsercache, wechseln Sie zu Ihrem Partner Center-Konto Dashboard, und wählen Sie den Link Überprüfung der über **Prüfung erneut senden** aus, damit die Bestätigungs-e-Mail an Ihre e-Mail-Adresse gesendet wird
1. Versuchen Sie, über einen anderen Browser auf den Link zum  **erneuten Senden der Überprüfungs e-Mail** zuzugreifen.
1. Arbeiten Sie mit Ihrer IT-Abteilung zusammen, um sicherzustellen, dass die Überprüfungs e-Mails nicht vom e-Mail-Server blockiert werden.
1. Passen Sie den Spamfilter Ihres Servers so an, dass alle e-Mails von Maccount@Microsoft zugelassen/geschützt werden **. <span></span> com**.

## <a name="how-long-does-the-employment-verification-process-usually-take"></a>Wie lange dauert der Prozess der Überprüfung der Arbeit?

Wenn alle übermittelten Details korrekt sind, wird die Überprüfung der Arbeit in 1 bis 2 Stunden abgeschlossen.

## <a name="how-long-does-the-business-verification-process-usually-take"></a>Wie lange dauert der Prozess der "Geschäfts Verifizierung" normalerweise?

Die Unternehmens Überprüfung dauert 1 bis 2 Werktage, vorausgesetzt, alle erforderlichen Dokumente wurden übermittelt.

## <a name="if-i-reach-out-to-the-support-team-will-my-ticket-be-expedited"></a>Wenn ich das Support Team erreiche, wird mein Ticket beschleunigt?

Support Tickets werden innerhalb einer Woche aufgelöst. Suchen Sie nach den Updates, die an die e-Mail gesendet werden, die bei der Erhöhung des Support Tickets angegeben wurde.

## <a name="my-issue-is-not-listed-here--are-there-other-pages-i-can-reference-for-partner-center-issues"></a>Mein Problem wird hier nicht aufgeführt.  Gibt es weitere Seiten, auf die ich für Partner Center-Probleme verweisen kann?

Weitere Informationen finden Sie in der [Dokumentation zum kommerziellen Marktplatz](/azure/marketplace/) .

## <a name="ive-created-a-support-ticket-it-has-been-7-business-days-and-i-havent-received-an-update-where-can-i-get-additional-help"></a>Ich habe ein Support Ticket erstellt, es war 7 Werktage, und ich habe kein Update erhalten. Wo erhalte ich weitere Hilfe?

Senden Sie eine e-Mail **<teamsubm@microsoft.com>** mit den folgenden Details:

1. **Betreffzeile**. *Problem beim Partner Center Konto für <App_Name>* (geben Sie den Namen Ihrer APP an).
1. **E-Mail-Text:**
    * Support Ticketnummer:
    * Ihre Verkäufer-ID:
    * Ein Screenshot des Problems (falls möglich):

>
> [!div class="nextstepaction"]
> [Weitere Informationen zu app-Validierungsrichtlinien für Microsoft Teams](/legal/marketplace/certification-policies)
