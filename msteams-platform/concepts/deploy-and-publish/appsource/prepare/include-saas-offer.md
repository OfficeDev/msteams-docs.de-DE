---
title: Einschließen eines SaaS-Angebots mit Ihrer App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App monetarisieren, indem Sie Abonnementpläne direkt aus Ihrem Teams Store-Eintrag verkaufen. Grundlegendes zum Veröffentlichen von Apps, Endbenutzern und Administratoren.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 23327ea2765eb5496f8cfb157cdd194fcc13aaf7
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243255"
---
# <a name="include-a-saas-offer-with-your-teams-app"></a>Binden Sie ein SaaS-Angebot in Ihre Teams-App ein

:::row:::
   :::column span="3":::

Mit einem transaktionsfähigen SaaS-Angebot (Software-as-a-Service) können Sie Ihre Teams-App monetarisieren, indem Sie Abonnementpläne direkt aus Ihrem Teams Store-Eintrag verkaufen. Angenommen, Sie haben eine kostenlose App, die jeder im Store erhalten kann. Jetzt können Sie Premium- und Enterprise-Pläne für Benutzer anbieten, die mehr Features benötigen.

Hier ist eine allgemeine Vorstellung davon, wie Sie Ihre App monetarisieren können:

1. [Planen Ihres SaaS-Angebots](#plan-your-saas-offer).

1. [Integration in die SaaS-Erfüllungs-APIs](#integrate-with-the-saas-fulfillment-apis).

1. [Erstellen einer Angebotsseite für die Abonnementverwaltung](#build-a-landing-page-for-subscription-management).

1. [Erstellen Ihres SaaS-Angebots](#create-your-saas-offer).

1. [Konfigurieren Ihrer App für das SaaS-Angebot](#configure-your-app-for-the-saas-offer).

1. [Veröffentlichen Ihrer App im Teams-Store](#publish-your-app).

   :::column-end:::
   :::column span="1":::

:::image type="content" source="~/assets/images/saas-offer/saas-offer-diagram.png" alt-text="Diagramm, das den Prozess zum Einschließen eines SaaS-Angebots in Ihre Teams-App darstellt.":::

   :::column-end:::
:::row-end:::

## <a name="plan-your-saas-offer"></a>Planen Ihres SaaS-Angebots

Eine umfassende Anleitung finden Sie unter [Planung eines SaaS-Angebots für den kommerziellen Microsoft-Marketplace](/azure/marketplace/plan-saas-offer).

Bei der Planung der Monetarisierung Ihrer Teams-App sollten Sie folgende Punkte berücksichtigen:

* Entscheiden Sie sich für Ihr Abonnementmodell. Ein transaktionsfähiges SaaS-Angebot kann mehrere Abonnementpläne enthalten. Öffentliche Abonnementpläne, die für jeden verfügbar sind, sind am häufigsten, aber Sie möchten möglicherweise auch bestimmte Kunden mit Angeboten nur für sie ansprechen. Weitere Informationen finden Sie unter [private Pläne im kommerziellen Microsoft Marketplace](/azure/marketplace/private-plans).
* Informieren Sie sich über die Option zum [*Verkaufen über Microsoft-Angebote*](/azure/marketplace/plan-saas-offer#listing-options) für Ihr SaaS-Angebot, die erforderlich ist, wenn Benutzer Abonnementpläne für Ihre App direkt über den Teams Store erwerben möchten.
* Erfahren Sie, wie [Azure Active Directory Single Sign-On (SSO)](/azure/marketplace/azure-ad-saas) Ihren Kunden hilft, Abonnements zu erwerben und zu verwalten. (Microsoft Azure Active Directory (Azure AD) SSO ist für Teams Apps mit SaaS-Angeboten erforderlich.)
* Sie werden darüber informiert, dass Sie für das Verwalten und Bezahlen der Infrastruktur verantwortlich sind, die erforderlich ist, um die Nutzung Ihres SaaS-Angebots durch Ihre Kunden zu unterstützen.
* Planen für Mobilgeräte. Um zu verhindern, dass die App Store-Richtlinien von Drittanbietern verletzt werden, kann Ihre App keine Links enthalten, mit denen Benutzer Abonnementpläne auf Mobilgeräten erwerben können. Sie können jedoch weiterhin angeben, ob Ihre App über Features verfügt, die einen Abonnementplan erfordern. Weitere Informationen finden Sie in den [Zertifizierungsrichtlinien für den Commercial Marketplace](/legal/marketplace/certification-policies#114048-mobile-experience).

## <a name="integrate-with-the-saas-fulfillment-apis"></a>Integration in die SaaS-Erfüllungs-APIs

Die Integration in die SaaS-Erfüllungs-APIs ist für die Monetarisierung Ihrer Teams-App erforderlich. Diese APIs helfen Ihnen bei der Verwaltung des Lebenszyklus eines Abonnementplans, sobald er von einem Benutzer erworben wurde.

Vollständige Anweisungen und API-Referenz finden Sie in der [Dokumentation zu SaaS-Erfüllungs-APIs](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-apis). Im Allgemeinen implementieren Sie die folgenden Schritte mithilfe der APIs, sobald ein Abonnement erworben wurde:

1. Erhalten Sie ein [*Kaufidentifikationstoken*](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-life-cycle#purchased-but-not-yet-activated-pendingfulfillmentstart) über die URL zu Ihrer Angebotsseite.

1. Verwenden Sie das Token, um Abonnementdetails abzurufen.

1. Benachrichtigen Sie den Commercial Marketplace, dass das Abonnement aktiviert ist.

### <a name="best-practices-for-implementing-subscription-management"></a>Bewährte Methoden für die Implementierung der Abonnementverwaltung

* Bei transaktionensfähigen SaaS-Angeboten für Teams Apps sollten Abonnementpläne (Lizenzen) einzelnen Benutzern und nicht Gruppen oder einer ganzen Organisation zugewiesen werden.
* Wenn Benutzern ein Abonnementplan zugewiesen ist, benachrichtigen Sie sie über einen Teams Bot oder eine E-Mail. Fügen Sie Informationen zum Hinzufügen der App zu Teams und zu den ersten Schritten in die Nachrichten ein.
* Unterstützen Sie die Idee mehrerer Administratoren. Mit anderen Worten, mehrere Benutzer in derselben Organisation können ihre eigenen Abonnements erwerben und verwalten.

## <a name="manage-license-for-third-party-apps-in-teams"></a>Verwalten der Lizenz für Drittanbieter-Apps in Teams

Teams ermöglicht unabhängigen Softwareanbietern (ISVs) Administratoren oder Benutzern das Verwalten von SaaS-Lizenzen für Apps von Drittanbietern, die über teams storefront erworben wurden. ISV-Administratoren oder Benutzer können SaaS-Lizenzen ganz einfach zuweisen, aufheben, verwenden und nachverfolgen.

Führen Sie die folgenden Schritte aus, um die Lizenzverwaltung für eine App in Teams zu aktivieren:

1. [Erstellen eines Angebots im Partner Center](#create-an-offer-in-partner-center)
1. [Aktualisieren Ihrer Teams-App](#update-your-teams-app)
1. [Nach dem Kauf](#post-purchase)
1. [Integration in die Graph Usage Right-API](#integrate-with-graph-usage-right-api)

### <a name="create-an-offer-in-partner-center"></a>Erstellen eines Angebots im Partner Center

1. Melden Sie sich beim [Partner Center](https://partner.microsoft.com/) an, und wählen Sie **"Partner Center" aus**.

   :::image type="content" source="~/assets/images/first-party-license-mgt/partner-center-home-page.png" alt-text="Die Screenshots zeigen, wie Sie sich beim Partner Center-Konto anmelden.":::

1. Wählen **Sie auf der** Startseite die Registerkarte **"Marketplace-Angebote** " aus, um kommerzielle Marketplace-Angebote zu definieren.

   :::image type="content" source="~/assets/images/first-party-license-mgt/home-page.png" alt-text="Die Screenshots zeigen die Startseite und die Registerkarte &quot;Marketplace-Angebot&quot; im Partner Center.":::

1. Wählen Sie im linken Bereich " **Übersicht** " aus.

1. Wählen Sie **"Neue Angebotssoftware****als Dienst**"  >  aus.

   :::image type="content" source="~/assets/images/first-party-license-mgt/commercial-marketplace.png" alt-text="Die Screenshots zeigen die Marketplace-Angebotsseite, auf der Sie ein neues Angebot auswählen können.":::

1. Geben Sie **Angebots-ID** und **Angebotsalias** ein, und wählen Sie **"Erstellen"** aus.

   > [!NOTE]
   > Wenn Sie ein Angebot zu Testzwecken erstellen, fügen Sie den Text **-ISVPILOT** am Ende Ihres Angebotsalias hinzu. Dies gibt dem Zertifizierungsteam an, dass das Angebot zu Testzwecken dient. Microsoft löscht Angebote mit **-ISVPILOT** regelmäßig. Verwenden Sie dieses Tag daher nicht aus anderen Gründen als dem Testen der Lizenzverwaltungsfunktion.

   :::image type="content" source="~/assets/images/first-party-license-mgt/saas.png" alt-text="Die Screenshots zeigen, wie Sie die Angebots-ID und den Angebotsalias im Partner Center eingeben.":::

1. Aktivieren Sie auf der Seite "Angebot einrichten" unter "Setupdetails" das Kontrollkästchen **"Ja". Ich möchte, dass Microsoft Kundenlizenzen in meinem Auftrag verwaltet**.

   :::image type="content" source="~/assets/images/first-party-license-mgt/saas-isvpilot.png" alt-text="Die Screenshots zeigen die Seite &quot;Angebot einrichten&quot;, um eine Lizenz einzurichten, die für Ihre App in Teams verwaltet werden soll.":::

   > [!NOTE]
   >
   > * Dies ist eine einmalige Einstellung, die Sie nach der Veröffentlichung Ihres Angebots nicht mehr ändern können. Auf diese Weise kann der Kunde Lizenzen für Ihre App in Teams verwalten.
   > * Das App-Manifest unterstützt nur ein Angebot für eine App. Wählen Sie eine geeignete Lizenzverwaltungslösung für alle in Ihrem Angebot verfügbaren Pläne aus, und Sie können diese Option nicht ändern, nachdem das Angebot live geschaltet wurde.

1. Wählen Sie **"Entwurf speichern" aus**.

1. Wählen Sie im linken Bereich " **Planübersicht** " und dann " **Neuen Plan erstellen**" aus.

   > [!NOTE]
   > Sie müssen mindestens einen Plan hinzufügen.

   :::image type="content" source="~/assets/images/first-party-license-mgt/plan-overview.png" alt-text="Die Screenshots zeigen eine Übersicht über den Plan zum Erstellen eines neuen Plans für Ihre Apps im Partner Center.":::

1. Geben Sie die Plan-ID und den Plannamen ein, und wählen Sie dann **"Erstellen"** aus.

1. Geben Sie den **Plannamen** und die **Planbeschreibung** ein.

   > [!NOTE]
   > Die Planinformationen werden im Teams Marketplace und [in Appsource](https://appsource.microsoft.com/) unter "Angebotseintrag" (Abschnitt "Pläne") angezeigt.

   :::image type="content" source="~/assets/images/first-party-license-mgt/plan-listing.png" alt-text="Die Screenshots zeigen die Planseite zum Hinzufügen des Plannamens und der Planbeschreibung für Ihre App.":::

1. Wählen Sie **"Entwurf speichern" aus**.

1. Wählen Sie im linken Bereich **Preise und Verfügbarkeit** aus.

1. Fügen Sie Preis- und Verfügbarkeitsdetails hinzu.

   :::image type="content" source="~/assets/images/first-party-license-mgt/pricing-availability.png" alt-text="Die Screenshots zeigen die Preis- und Verfügbarkeitsseite zum Hinzufügen eines SaaS-Angebots für Ihre App.":::

1. Wählen Sie **"Entwurf speichern" aus**.

1. Wählen Sie oben auf der Seite " **Planübersicht** " aus, um zur Eintragsseite zu wechseln, auf der alle Pläne angezeigt werden, die Sie für dieses Angebot erstellt haben.

   :::image type="content" source="~/assets/images/first-party-license-mgt/list-of-plans-created.png" alt-text="Die Screenshots zeigen die Seite &quot;Planeintrag&quot; mit Dienst-ID, Preismodell, Verfügbarkeit, Status und Aktion.":::

1. Kopieren Sie die Dienst-ID des Plans, den Sie für die Integration in die Microsoft Graph-Api für Nutzungsrechte erstellt haben.

### <a name="update-your-teams-app"></a>Aktualisieren Ihrer Teams-App

Aktualisieren Sie Ihre Teams-App so, dass sie der kostenpflichtigen Funktionalität zugeordnet wird, und [ordnen Sie Ihre Teams-App](https://aka.ms/TMTG) Ihrem Angebot und Ihrer Veröffentlichung zu.

### <a name="post-purchase"></a>Nach dem Kauf

1. Nach der Aktivierung wird der Kunde von der Zielseite zu Microsoft Teams License Management umgeleitet.

1. Nach erfolgreichem Abschluss des Abonnementkaufs wird der Kunde zur App-Startseite zur Abonnementaktivierung umgeleitet. Dies ist die vorhandene Erfahrung für den Kauf [monetarisierter Apps in Teams](https://aka.ms/TMTG).

1. Nachdem der Kunde den Abonnementkauf auf der Startseite aktiviert hat, wird der Kunde über einen [Umleitungs-URL-Link](https://teams.microsoft.com/_#/subscriptionManagement) oder eine Schaltfläche, die der Kunde auf der Publisher-Zielseite auswählt, auf die Seite "Abonnements" in Teams umgeleitet.

### <a name="integrate-with-graph-usage-right-api"></a>Integration in die Graph Usage Right-API

Integration in die Graph Usage Right-API zum Verwalten von Benutzerberechtigungen zum Zeitpunkt des App-Starts durch einen Kunden, der über eine Kauflizenz verfügt. Sie müssen die Berechtigungen des Benutzers für die App mit einem Graph-Aufruf der Api für Nutzungsrechte ermitteln.

Sie können Graph-APIs aufrufen, um festzustellen, ob der aktuell angemeldete Benutzer mit einem gültigen Abonnement des Plans Zugriff auf Ihre App hat. Führen Sie die folgenden Schritte aus, um die Graph UsageRight-API aufzurufen, um benutzerberechtigungen zu überprüfen:

1. Abrufen des Benutzer-OBO-Tokens: [Zugriff im Namen eines Benutzers erhalten – Microsoft Graph | Microsoft-Dokumentation](/graph/auth-v2-user).

1. Call Graph to get user's object ID: [Use the Microsoft Graph-API - Microsoft Graph | Microsoft-Dokumentation](/graph/use-the-api).

1. Rufen Sie die UsageRights-API auf, um zu ermitteln, ob der Benutzer über eine Lizenz für die [Planliste "User UsageRights" verfügt – Microsoft Graph Beta-| Microsoft-Dokumentation](/graph/api/user-list-usagerights?view=graph-rest-beta&tabs=http&preserve-view=true).

   > [!NOTE]
   > Sie müssen über Mindestberechtigungen `User.Read` zum Aufrufen von UsageRights verfügen.
   > Die UsageRights-API befindet sich derzeit in der Betaversion. Nachdem die Version auf V1 aktualisiert wurde, sollten ISV-Benutzer ein Upgrade von der Betaversion auf die V1-Version durchführen.

### <a name="check-license-usage-in-partner-center-analytics"></a>Überprüfen der Lizenznutzung in Partner Center-Analysen

1. Melden Sie sich beim [Partner Center](https://partner.microsoft.com/) an.
1. Wechseln Sie im linken Bereich zu **Commercial Marketplace > Analyze > Licensing**.
1. Wählen Sie im Berichterstellungs-Widget **"Plan und Mandant** " aus, um die monatliche Nutzung anzuzeigen.

## <a name="build-a-landing-page-for-subscription-management"></a>Erstellen einer Angebotsseite für die Abonnementverwaltung

Wenn jemand den Kauf eines Abonnementplans für Ihre App im Teams Store abgeschlossen hat, leitet der kommerzielle Marketplace sie zu Ihrer Startseite weiter, auf der er das Abonnement verwalten kann (z. B. das Zuweisen einer Lizenz zu einem bestimmten Benutzer in seiner Organisation).

Wählen Sie **"Nein" aus. In solchen Fällen würde ich es vorziehen, Kundenlizenzen selbst zu verwalten** .

Vollständige Anweisungen finden Sie unter [Erstellen der Angebotsseite für Ihr SaaS-Angebot](/azure/marketplace/azure-ad-transactable-saas-landing-page).

Wenn jemand den Kauf eines Abonnementplans für Ihre App abgeschlossen hat und in Teams bleiben möchte, ohne sie zu Ihrer Startseite zu leiten, wählen Sie **"Ja" aus, ich möchte, dass Microsoft Kundenlizenzen in meinem Auftrag verwaltet**.

Weitere Informationen finden Sie unter [Lizenzverwaltung von Erstanbietern](/platform/concepts/deploy-and-publish/appsource/prepare/first-party-license-management).

### <a name="best-practices-for-landing-pages"></a>Bewährte Methoden zum Speichern von Seiten

Berücksichtigen Sie die folgenden Ansätze beim Erstellen einer Startseite für die Teams App, die Sie monetarisieren. Sehen Sie sich eine Beispiel-Startseite unter [Endbenutzer-Einkaufserfahrung](#end-user-purchasing-experience) an.

* Benutzer müssen sich mit denselben Azure AD-Anmeldeinformationen, die sie zum Kauf des Abonnements verwendet haben, bei Ihrer Startseite anmelden können. Weitere Informationen finden Sie unter [Azure AD und transaktionensfähige SaaS-Angebote auf dem Commercial Marketplace](/azure/marketplace/azure-ad-saas).
* Gestatten Sie Benutzern die Ausführung der folgenden Aktionen auf Ihrer Startseite. Berücksichtigen Sie was für die Rolle und die Berechtigungen eines Benutzers angemessen ist. Sie können zum Beispiel nur Abonnementadministratoren die Suche nach Benutzern erlauben):
  * Suchen Sie mithilfe von E-Mails oder einer anderen Identitätsform nach Benutzern in ihrer Organisation.
  * Lassen Sie sich Benutzer in einer Liste anzeigen, denen sie Lizenzen zuweisen können.
  * Weisen Sie Lizenzen gleichzeitig einem oder mehreren Benutzern zu.
  * Weisen Sie verschiedener Arten von Lizenzen (sofern verfügbar) zu und verwalten Sie sie.
  * Überprüfen Sie, ob eine Lizenz bereits einem anderen Benutzer zugewiesen ist.
  * Kündigen Sie deren Abonnement.
* Stellen Sie eine Einführung in die Verwendung Ihrer App bereit.
* Fügen Sie Möglichkeiten hinzu, Support zu erhalten, z. B. häufig gestellte Fragen, eine Wissensdatenbank oder eine Kontakt-E-Mail.
* Stellen Sie einen Link bereit, der es dem Abonnenten erleichtert, zur Startseite zurückzukehren. Fügen Sie z. B. diesen Link in die Registerkarte **Info** Ihrer App ein.

## <a name="create-your-saas-offer"></a>Vorbereiten Ihres SaaS-Angebots

Nachdem Sie die SaaS-Erfüllungs-APIs integriert und Ihre Startseite erstellt haben, auf der Benutzer ihre Abonnements verwalten können, ist es an der Zeit, Ihr saaS-Angebot offiziell zu erstellen, zu testen und zu veröffentlichen.

### <a name="create-the-offer"></a>Erstellen des Angebots

Vollständige Anweisungen dazu finden Sie unter [Erstellen eines SaaS-Angebots](/azure/marketplace/create-new-saas-offer) im Partner Center. In den folgenden Schritten wird beschrieben, was auf den oberen Ebenen zu tun ist.

1. Erstellen Sie ein [Partner Center-Konto](https://partner.microsoft.com/), wenn Sie nicht über ein Konto verfügen.

1. Konfigurieren Sie die Abonnementpläne, Preisdetails und mehr für Ihr transaktionsfähiges SaaS-Angebot. Stellen Sie insbesondere sicher, dass Sie die folgenden Schritte ausführen:

    * Wählen Sie unter **Setupdetails** die Option **Ja** aus, um anzugeben, dass Sie das Angebot über Microsoft verkaufen.

    * Fügen Sie den AppSource-Link unter **Microsoft 365 Integration** zu Ihrem App-Eintrag hinzu. Mit diesem Schritt wird sichergestellt, dass Benutzer Ihre Abonnementpläne zusätzlich zu Teams in AppSource kaufen können.

1. Speichern Sie Ihren Herausgeber und Angebot-IDs. (Sie benötigen sie später, um das Angebot mit Ihrer App im Entwicklerportal zu verknüpfen.)

1. Veröffentlichen Sie Ihr Angebot auf dem Commercial Marketplace.

### <a name="test-the-offer"></a>Testen des Angebots

Wir empfehlen Ihnen, vor der Veröffentlichung Ihres SaaS-Angebots die End-to-End-Kauferfahrung zu überprüfen. Sie können dies überprüfen, indem Sie ein separates Angebot nur zu Testzwecken erstellen. Vollständige Informationen finden Sie unter [Testangebotsübersicht](/azure/marketplace/plan-saas-offer#test-offer), [Erstellen eines Testangebots](/azure/marketplace/create-saas-dev-test-offer) und [Anzeigen einer Vorschau Ihres Angebots](/azure/marketplace/test-publish-saas-offer).

> [!IMPORTANT]
> Sie können eine End-to-End-Transaktion in Teams mithilfe der [Testvorschau für monetarisierte Apps](Test-preview-for-monetized-apps.md) testen. Bei Live-Angeboten müssen Sie den Überprüfungsprozess des App Stores durchführen.

Aus Teams Sicht müssen diese Tests überprüfen, ob die Anzahl der Lizenzen und Zuweisungen mit den Angaben im Teams Admin Center übereinstimmt, wenn Benutzer Folgendes tun:

* Ihren Abonnementplan auf Ihrer Startseite aktivieren und konfigurieren.
* Lizenzen sich selbst oder anderen Benutzern zuweisen, sie entfernen oder erneut zuweisen.
* Ihr Abonnement kündigen oder erneuern.

### <a name="publish-the-offer"></a>Veröffentlichen des Angebots

Nachdem Sie die Tests abgeschlossen haben, [veröffentlichen Sie Ihr Angebot live](/azure/marketplace/test-publish-saas-offer#publish-your-offer-live).

## <a name="configure-your-app-for-the-saas-offer"></a>Konfigurieren Ihrer App für das SaaS-Angebot

Sie haben Ihr SaaS-Angebot veröffentlicht, müssen es jedoch noch mit Ihrer Teams-App verknüpfen, damit Benutzer Ihre Abonnementpläne im Teams Store anzeigen können.

1. Wechseln Sie zum [Entwicklerportal](https://dev.teams.microsoft.com/), und wählen Sie **Apps** aus.
1. Wählen Sie auf der Seite **Apps** die App aus, mit der Sie das SaaS-Angebot verknüpfen.
1. Wechseln Sie zur Seite **Pläne und Preise**, und geben Sie Ihre Herausgeber- und Angebots-IDs an. (Sie finden diese IDs im Partner Center, wenn sie nicht verfügbar sind.)
1. Wählen Sie **Anzeigen** aus, um die Abonnementpläne Ihres SaaS-Angebots in der Vorschau anzuzeigen.
1. Wenn alles gut aussieht, wählen Sie **Speichern** aus.

   Die `subscriptionOffer` Eigenschaft wird ihrem [App-Manifest](~/resources/schema/manifest-schema-dev-preview.md#subscriptionoffer) hinzugefügt.

   ```json
      "subscriptionOffer": {
        "offerId": "publisherId.offerId"  
        }
   ```

## <a name="publish-your-app"></a>Veröffentlichen eigener Apps

Sie haben Ihr SaaS-Angebot erstellt und mit Ihrer Teams-App verknüpft – jetzt ist es an der Zeit, Ihre App im Teams Store zu veröffentlichen. Vollständige Anweisungen finden Sie unter [Veröffentlichen Ihrer App im Teams Store](~/concepts/deploy-and-publish/appsource/publish.md).

> [!IMPORTANT]
>
> * Selbst wenn Ihre App bereits im Teams Store aufgeführt ist, müssen Sie den Überprüfungsprozess des Stores erneut durchlaufen, um Ihr SaaS-Angebot einzuschließen.
> * Pauschalangebote, die ohne die Angebots-ID und die Publisher-ID im App-Manifest erstellt wurden, sollten aktualisiert und erneut zur Validierung eingereicht werden.

Nach der Veröffentlichung wird Benutzern im Dialogfeld „App-Details“ eine Option **Abonnement kaufen** angezeigt, wenn sie versuchen, Ihre App zu Teams hinzuzufügen.

## <a name="end-user-purchasing-experience"></a>Endbenutzer-Einkaufserfahrung

Das folgende Beispiel zeigt, wie Benutzer Abonnementpläne für eine fiktive Teams-App namens *Recloud* erwerben können.

1. Suchen Sie im Teams Store die *Recloud-App*, und wählen Sie sie aus.

1. Wählen Sie im Dialogfeld „App-Details“ die Option **Abonnement kaufen** aus.

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplan.png" alt-text="Kaufen des Abonnements für die ausgewählte App.":::

1. Wählen Sie Ihr Land aus, um Abonnementpläne für Ihren Standort anzuzeigen.

1. Wählen Sie im Dialogfeld **Abonnementplan auswählen** den gewünschten Plan aus, und wählen Sie **Auschecken** aus. (Hinweis: Private Pläne sind nur für Benutzer in Organisationen sichtbar, für die Sie das Angebot bereitstellen. Diese Pläne sind mit einem **Sonderangebotssymbol** :::image type="icon" source="~/assets/icons/special-icon.png"::: gekennzeichnet.)

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplan.png" alt-text="Auswählen des entsprechenden Abonnementplans.":::

1. Geben Sie im Dialogfeld **Auschecken** alle erforderlichen Informationen an, und wählen Sie **Bestellung aufgeben** aus.

    :::image type="content" source="~/assets/images/saas-offer/placesubscriptionorder.png" alt-text="Aufgeben des Abonnementauftrags.":::

1. Wenn Sie dazu aufgefordert werden, wählen Sie **Jetzt einrichten** aus, um Ihr Abonnement einzurichten.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-set-up.png" alt-text="Einrichten des Abonnements.":::

1. Verwalten Sie Ihren Abonnementplan über die *Recloud-Website* (auch als [Angebotsseite](#build-a-landing-page-for-subscription-management) bezeichnet).

    :::image type="content" source="~/assets/images/saas-offer/subscriptionlicenses.png" alt-text="Konfigurieren von Benutzerlizenzen.":::

## <a name="admin-purchasing-experience"></a>Kauferfahrung für Administratoren

Administratoren können App-Abonnementpläne im [Teams Admin Center](/MicrosoftTeams/purchase-third-party-apps) erwerben.

## <a name="remove-a-saas-offer-from-your-app"></a>Entfernen eines SaaS-Angebots aus Ihrer App

Wenn Sie die Verknüpfung eines SaaS-Angebots aufheben, das in Ihrem Teams Store-Eintrag enthalten ist, müssen Sie Ihre App erneut veröffentlichen, um die Änderung im Store anzuzeigen.

1. Wechseln Sie zum [Entwicklerportal](https://dev.teams.microsoft.com/), und wählen Sie **Apps** aus.
1. Wählen Sie auf der Seite **Apps** die App aus, aus der Sie das Angebot entfernen.
1. Wechseln Sie zur Seite **Pläne und Preise**, und wählen Sie **Zurücksetzen** aus.
1. Sobald das Angebot nicht mehr verknüpft ist, führen Sie die folgenden Schritte aus, um Ihren Store-Eintrag zu aktualisieren:
   1. Wählen Sie **Verteilen > Im Teams Store veröffentlichen** aus.
   1. Wählen Sie **Partner Center öffnen** aus, um mit der erneuten Veröffentlichung Ihrer App ohne Angebot zu beginnen.

## <a name="see-also"></a>Siehe auch

* [Verwalten und Unterstützen Ihrer veröffentlichten App](../post-publish/overview.md)
* [Validierungsrichtlinien für Anwendungen im Zusammenhang mit SaaS-Angeboten](teams-store-validation-guidelines.md#apps-linked-to-saas-offer)
