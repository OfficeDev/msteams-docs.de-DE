---
title: Einschließen eines SaaS-Angebots mit Ihrer App
description: Erfahren Sie, wie Sie Ihre Microsoft Teams-App mit Abonnementplänen monetarisieren.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 597896d79408fa596e9949166fceda97ef440d07
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212005"
---
# <a name="include-a-saas-offer-with-your-microsoft-teams-app"></a>Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App

:::row:::
   :::column span="3":::

Mit einem transaktionsfähigen SaaS-Angebot (Software-as-a-Service) können Sie Ihre Teams-App monetarisieren, indem Sie Abonnementpläne direkt aus Ihrem Teams Store-Eintrag verkaufen. Angenommen, Sie haben eine kostenlose App, die jeder im Store erhalten kann. Jetzt können Sie Premium- und Enterprise-Pläne für Benutzer anbieten, die mehr Features benötigen.

Hier ist eine allgemeine Vorstellung davon, wie Sie Ihre App monetarisieren können:

1.  [Planen Sie Ihr SaaS-Angebot.](#plan-your-saas-offer)

1.  [Integration in die SaaS-Erfüllungs-APIs.](#integrate-with-the-saas-fulfillment-apis)

1.  [Erstellen Sie eine Angebotsseite für die Abonnementverwaltung.](#build-a-landing-page-for-subscription-management)

1.  [Erstellen Sie Ihr SaaS-Angebot.](#create-your-saas-offer)

1.  [Konfigurieren Sie Ihre App für das SaaS-Angebot.](#configure-your-app-for-the-saas-offer)

1.  [Veröffentlichen Sie Ihre App im Teams Store.](#publish-your-app)

   :::column-end:::
   :::column span="1":::
   
:::image type="content" source="~/assets/images/saas-offer/saas-offer-diagram.png" alt-text="Diagramm, das den Prozess zeigt, wie Sie ein SaaS-Angebot in Ihre Teams-App aufnehmen." border="false":::

   :::column-end:::
:::row-end:::

## <a name="plan-your-saas-offer"></a>Planen Ihres SaaS-Angebots

Eine umfassende Anleitung finden Sie unter ["Planen eines SaaS-Angebots für den kommerziellen Microsoft-Marketplace".](/azure/marketplace/plan-saas-offer)

Bei der Planung der Monetarisierung Ihrer Teams-App sollten Sie folgende Punkte berücksichtigen:

* Entscheiden Sie sich für Ihr Abonnementmodell. Ein transaktionsfähiges SaaS-Angebot kann mehrere Abonnementpläne enthalten. Öffentliche Abonnementpläne, die für jeden verfügbar sind, sind am häufigsten, aber Sie möchten möglicherweise auch bestimmte Kunden mit Angeboten nur für sie ansprechen. Weitere Informationen finden Sie unter [private Angebote auf dem kommerziellen Microsoft-Marketplace.](/azure/marketplace/private-offers)
* Informieren Sie sich über die Option [ *"Über Microsoft verkaufen"*](/azure/marketplace/plan-saas-offer#listing-options) für Ihr SaaS-Angebot, die erforderlich ist, wenn Benutzer Abonnementpläne für Ihre App direkt über den Teams Store erwerben möchten.
* Erfahren Sie, wie [Azure Active Directory einmaliges Anmelden (Single Sign-On, SSO)](/azure/marketplace/azure-ad-saas) Ihren Kunden hilft, Abonnements zu erwerben und zu verwalten. (Azure AD SSO ist für Teams Apps mit SaaS-Angeboten erforderlich.)
* Verstehen Sie, dass Sie für das Verwalten und Bezahlen der Infrastruktur verantwortlich sind, die erforderlich ist, um die Nutzung Ihres SaaS-Angebots durch Ihre Kunden zu unterstützen.
* Planen sie mobile Geräte. Um zu verhindern, dass Die App Store-Richtlinien von Drittanbietern verletzt werden, kann Ihre App keine Links enthalten, mit denen Benutzer Abonnementpläne auf Mobilgeräten erwerben können. Sie können jedoch weiterhin angeben, ob Ihre App über Features verfügt, die einen Abonnementplan erfordern. Weitere Informationen finden Sie in den zugehörigen Zertifizierungsrichtlinien für [den kommerziellen Marketplace.](/legal/marketplace/certification-policies#114048-mobile-experience)

## <a name="integrate-with-the-saas-fulfillment-apis"></a>Integration in die SaaS-Erfüllungs-APIs

Die Integration in die SaaS-Erfüllungs-APIs ist für die Monetarisierung Ihrer Teams-App erforderlich. Diese APIs helfen Ihnen bei der Verwaltung des Lebenszyklus eines Abonnementplans, sobald er von einem Benutzer erworben wurde.

Vollständige Anweisungen und API-Referenz finden Sie in der Dokumentation zu [SaaS-Erfüllungs-APIs.](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-apis) Im Allgemeinen implementieren Sie die folgenden Schritte mithilfe der APIs, sobald ein Abonnement erworben wurde:

1. Erhalten Sie ein [*Kaufidentifikationstoken*](/azure/marketplace/partner-center-portal/pc-saas-fulfillment-life-cycle#purchased-but-not-yet-activated-pendingfulfillmentstart) über die URL zu Ihrer Angebotsseite.

1. Verwenden Sie das Token, um Abonnementdetails abzurufen.

1. Benachrichtigen Sie den kommerziellen Marketplace, dass das Abonnement aktiviert ist.

### <a name="best-practices-for-implementing-subscription-management"></a>Bewährte Methoden für die Implementierung der Abonnementverwaltung

* Bei transaktionensfähigen SaaS-Angeboten für Teams Apps sollten Abonnementpläne (Lizenzen) einzelnen Benutzern und nicht Gruppen oder einer gesamten Organisation zugewiesen werden.
* Wenn Benutzern ein Abonnementplan zugewiesen ist, benachrichtigen Sie sie über einen Teams Bot oder eine E-Mail. Fügen Sie informationen zum Hinzufügen der App zu Teams und zu den ersten Schritten in das Messaging ein.
* Unterstützen Sie die Idee mehrerer Administratoren. Mit anderen Worten, mehrere Benutzer in derselben Organisation können ihre eigenen Abonnements erwerben und verwalten.

## <a name="build-a-landing-page-for-subscription-management"></a>Erstellen einer Angebotsseite für die Abonnementverwaltung 

Wenn jemand den Kauf eines Abonnementplans für Ihre App im Teams Store abgeschlossen hat, leitet der kommerzielle Marketplace sie zu Ihrer Zielseite weiter, auf der er das Abonnement verwalten kann (z. B. einem bestimmten Benutzer in seiner Organisation eine Lizenz zuweisen).

Vollständige Anweisungen finden Sie unter [Erstellen der Angebotsseite für Ihr SaaS-Angebot.](/azure/marketplace/azure-ad-transactable-saas-landing-page)

### <a name="best-practices-for-landing-pages"></a>Bewährte Methoden für Angebotsseiten

Berücksichtigen Sie die folgenden Ansätze beim Erstellen einer Zielseite für die Teams App, die Sie monetarisieren. Sehen Sie sich eine Beispiel-Angebotsseite in der [Endbenutzer-Einkaufsumgebung an.](#end-user-purchasing-experience)

* Benutzer müssen sich mit denselben Azure AD Anmeldeinformationen, die sie zum Kauf des Abonnements verwendet haben, bei Ihrer Zielseite anmelden können. Weitere Informationen finden Sie unter [Azure AD und transaktionensfähigen SaaS-Angeboten auf dem kommerziellen Marketplace.](/azure/marketplace/azure-ad-saas)
* Zulassen, dass Benutzer die folgenden Aktionen auf Ihrer Zielseite ausführen. Vergessen Sie nicht, zu überlegen, was für die Rolle und die Berechtigungen eines Benutzers geeignet ist (Sie können beispielsweise zulassen, dass nur Abonnementadministratoren nach Benutzern suchen):
  * Suchen Sie mithilfe von E-Mails oder einer anderen Identitätsform nach Benutzern in ihrer Organisation.
  * Anzeigen von Benutzern, denen sie Lizenzen zuweisen können, in einer Liste.
  * Gleichzeitiges Zuweisen von Lizenzen zu einem oder mehreren Benutzern.
  * Zuweisen und Verwalten verschiedener Arten von Lizenzen (sofern verfügbar).
  * Überprüfen Sie, ob eine Lizenz bereits einem anderen Benutzer zugewiesen ist.
  * Kündigen Sie ihr Abonnement.
* Stellen Sie eine Einführung in die Verwendung Ihrer App bereit.
* Fügen Sie Möglichkeiten hinzu, Support zu erhalten, z. B. häufig gestellte Fragen, eine Wissensdatenbank oder eine Kontakt-E-Mail.
* Stellen Sie einen Link bereit, der es dem Abonnenten erleichtert, zur Zielseite zurückzukehren. Fügen Sie z. B. diesen Link in die Registerkarte **"Info"** Ihrer App ein.

## <a name="create-your-saas-offer"></a>Erstellen Ihres SaaS-Angebots

Nachdem Sie die SaaS-Erfüllungs-APIs integriert und Ihre Zielseite erstellt haben, auf der Benutzer ihre Abonnements verwalten können, ist es an der Zeit, Ihr saaS-Angebot offiziell zu erstellen, zu testen und zu veröffentlichen.

> [!IMPORTANT]
> Teams unterstützt derzeit nur das Preismodell pro **Benutzer** (Benutzer/Monat und Benutzer/Jahr) für SaaS-Angebote. Weitere Informationen finden Sie unter [SaaS-Preismodelle.](/azure/marketplace/plan-saas-offer#saas-pricing-models)

### <a name="create-the-offer"></a>Erstellen des Angebots

Vollständige Anweisungen dazu finden Sie unter [Erstellen eines SaaS-Angebots](/azure/marketplace/create-new-saas-offer) im Partner Center. In den folgenden Schritten wird beschrieben, was auf hoher Ebene zu tun ist.

1.  Erstellen Sie ein [Partner Center-Konto,](https://partner.microsoft.com/) wenn Sie nicht über ein Konto verfügen.

1.  Konfigurieren Sie die Abonnementpläne, Preisdetails und mehr für Ihr transaktionsfähiges SaaS-Angebot. Stellen Sie insbesondere sicher, dass Sie die folgenden Schritte ausführen:

    * Wählen Sie unter **"Setupdetails"** die Option **"Ja"** aus, um anzugeben, dass Sie das Angebot über Microsoft verkaufen.
     
    * Fügen Sie unter **Microsoft 365 Integration** den AppSource-Link zu Ihrem App-Eintrag hinzu. Mit diesem Schritt wird sichergestellt, dass Benutzer Ihre Abonnementpläne zusätzlich zu Teams in AppSource kaufen können.

1. Store Ihres Herausgebers und anbieten von IDs. (Sie benötigen sie später, um das Angebot mit Ihrer App im Entwicklerportal zu verknüpfen.)

1. Veröffentlichen Sie Ihr Angebot auf dem kommerziellen Marketplace.

### <a name="test-the-offer"></a>Testen des Angebots

Es wird dringend empfohlen, die End-to-End-Einkaufserfahrung zu überprüfen, bevor Sie Ihr SaaS-Angebot veröffentlichen. Sie können dies tun, indem Sie ein separates Angebot nur zu Testzwecken erstellen. Vollständige Informationen finden Sie unter [Testangebotsübersicht,](/azure/marketplace/plan-saas-offer#test-offer) [Erstellen eines Testangebots](/azure/marketplace/create-saas-dev-test-offer)und Anzeigen einer [Vorschau Ihres Angebots.](/azure/marketplace/test-publish-saas-offer)

> [!IMPORTANT]
> Sie müssen Ihr transaktionsfähiges SaaS-Angebot in AppSource testen. Derzeit können Sie eine End-to-End-Transaktion in Teams erst testen, wenn Ihre App die Store-Überprüfung abgeschlossen hat.

Aus Teams Sicht müssen diese Tests überprüfen, ob die Anzahl der Lizenzen und Zuweisungen mit den Im Teams Admin Center übereinstimmt, wenn Benutzer:

* Aktivieren und konfigurieren Sie den Abonnementplan auf Ihrer Zielseite.
* Zuweisen, Entfernen oder erneutes Zuweisen von Lizenzen zu sich selbst oder anderen Benutzern.
* Kündigen oder verlängern Sie ihr Abonnement.

### <a name="publish-the-offer"></a>Veröffentlichen des Angebots

Nachdem Sie die Tests abgeschlossen haben, [veröffentlichen Sie Ihr Angebot live.](/azure/marketplace/test-publish-saas-offer#publish-your-offer-live)

## <a name="configure-your-app-for-the-saas-offer"></a>Konfigurieren Ihrer App für das SaaS-Angebot

Sie haben Ihr SaaS-Angebot veröffentlicht, müssen es jedoch weiterhin mit Ihrer Teams-App verknüpfen, damit Benutzer Ihre Abonnementpläne im Teams Store anzeigen können.

1. Wechseln Sie zum [Entwicklerportal,](https://dev.teams.microsoft.com/) und wählen Sie **"Apps"** aus.
1. Wählen Sie auf der Seite **"Apps"** die App aus, mit der Sie das SaaS-Angebot verknüpfen.
1. Wechseln Sie zur Seite **"Pläne und Preise",** und geben Sie Ihre Herausgeber- und Angebots-IDs an. (Sie finden diese IDs im Partner Center, wenn sie nicht verfügbar sind.)
1. Wählen Sie **"Anzeigen"** aus, um die Abonnementpläne Ihres SaaS-Angebots in der Vorschau anzuzeigen.
1. Wenn alles gut aussieht, wählen Sie **Speichern** aus.

   Die `subscriptionOffer` Eigenschaft wird ihrem [App-Manifest](~/resources/schema/manifest-schema-dev-preview.md#subscriptionoffer)hinzugefügt.

   ```json
      "subscriptionOffer": {
        "offerId": "publisherId.offerId"  
        }
   ```

## <a name="publish-your-app"></a>Veröffentlichen eigener Apps

Sie haben Ihr SaaS-Angebot erstellt und mit Ihrer Teams-App verknüpft – jetzt ist es an der Zeit, Ihre App im Teams Store zu veröffentlichen. Vollständige Anweisungen finden Sie unter [Veröffentlichen Ihrer App im Teams Store.](~/concepts/deploy-and-publish/appsource/publish.md)

> [!IMPORTANT]
> Auch wenn Ihre App bereits im Teams Store aufgeführt ist, müssen Sie den Überprüfungsprozess des Stores erneut durchlaufen, um Ihr SaaS-Angebot einzuschließen.

Nach der Veröffentlichung wird benutzern im Dialogfeld "App-Details" eine Option zum **Kaufen eines Abonnements** angezeigt, wenn sie versuchen, Ihre App Teams hinzuzufügen.

## <a name="end-user-purchasing-experience"></a>Endbenutzer-Einkaufserfahrung

Das folgende Beispiel zeigt, wie Benutzer Abonnementpläne für eine fiktive Teams-App namens *Recloud* erwerben können.

1. Suchen Sie im Teams Store die *Recloud-App,* und wählen Sie sie aus.

1. Wählen Sie im Dialogfeld "App-Details" die Option **"Abonnement kaufen"** aus.

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplan.png" alt-text="Kauf des Abonnements für die ausgewählte App.":::

1. Wählen Sie Ihr Land aus, um Abonnementpläne für Ihren Standort anzuzeigen.

1. Wählen Sie im Dialogfeld **Abonnementplan auswählen** den gewünschten Plan aus, und wählen Sie **"Auschecken"** aus. (Hinweis: Private Pläne sind nur für Benutzer in Organisationen sichtbar, für die Sie das Angebot bereitstellen. Diese Pläne werden  mit einem :::image type="icon" source="~/assets/icons/special-icon.png"::: Sonderangebotssymbol gekennzeichnet.)

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplan.png" alt-text="Auswählen des entsprechenden Abonnementplans.":::

1. Geben Sie im Dialogfeld **"Auschecken"** alle erforderlichen Informationen an, und wählen Sie **"Bestellung aufgeben"** aus.

    :::image type="content" source="~/assets/images/saas-offer/placesubscriptionorder.png" alt-text="Platzieren des Abonnementauftrags.":::

1. Wenn Sie dazu aufgefordert werden, wählen Sie **"Jetzt einrichten"** aus, um Ihr Abonnement einzurichten.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-set-up.png" alt-text="Einrichten des Abonnements.":::

1. Verwalten Sie Ihren Abonnementplan über die *Recloud-Website* (auch als [Angebotsseite](#build-a-landing-page-for-subscription-management)bezeichnet).

    :::image type="content" source="~/assets/images/saas-offer/subscriptionlicenses.png" alt-text="Konfigurieren von Benutzerlizenzen.":::

## <a name="admin-purchasing-experience"></a>Kauferfahrung für Administratoren

Administratoren können App-Abonnementpläne im [Teams Admin Center](/MicrosoftTeams/purchase-third-party-apps)erwerben.

## <a name="remove-a-saas-offer-from-your-app"></a>Entfernen eines SaaS-Angebots aus Ihrer App

Wenn Sie die Verknüpfung eines SaaS-Angebots aufheben, das in Ihrem Teams Store-Eintrag enthalten ist, müssen Sie Ihre App erneut veröffentlichen, um die Änderung im Store anzuzeigen.

1. Wechseln Sie zum [Entwicklerportal,](https://dev.teams.microsoft.com/) und wählen Sie **"Apps"** aus.
1. Wählen Sie auf der Seite **"Apps"** die App aus, aus der Sie das Angebot entfernen.
1. Wechseln Sie zur Seite **"Pläne und Preise",** und wählen Sie **"Zurücksetzen"** aus.
1. Sobald das Angebot nicht mehr verknüpft ist, führen Sie die folgenden Schritte aus, um Ihren Store-Eintrag zu aktualisieren:
   1. Wählen Sie **"Verteilen > Im Teams Store veröffentlichen"** aus.
   1. Wählen Sie **"Open Partner Center"** aus, um mit der erneuten Veröffentlichung Ihrer App ohne das Angebot zu beginnen.

## <a name="see-also"></a>Siehe auch

[Verwalten und Unterstützen Ihrer veröffentlichten App](../post-publish/overview.md)
