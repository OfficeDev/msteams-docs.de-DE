---
title: Testvorschau für monetarisierte Apps
author: v-ypalikila
description: Erstellen und testen Sie SaaS Preview-Angebote für Teams App, bevor Sie das Angebot live übertragen.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: medium
keywords: Teams-Apps SaaS bieten Vorschau an, Testvorschau monetarisierte Saas
ms.openlocfilehash: 849dd2ecd79a4b43d6feb6ceaca599f371df1de1
ms.sourcegitcommit: 54f6690b559beedc330b971618e574d33d69e8a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2022
ms.locfileid: "62363444"
---
# <a name="test-preview-for-monetized-apps"></a>Testvorschau für monetarisierte Apps

> [!NOTE]
> Die Testvorschau für monetarisierte Apps ist derzeit nur in der [**Entwicklervorschau**](/microsoftteams/platform/resources/dev-preview/developer-preview-intro) verfügbar.

Sie können ein SaaS-Angebot (Software as a Service) erstellen und die End-to-End-Kauferfahrung für Ihre monetarisierten Apps in Teams testen. Benutzer, die als Vorschaugruppe für die Teams-App hinzugefügt werden, können Ihr SaaS-Angebot vor der Veröffentlichung überprüfen.

## <a name="create-a-preview-offer-id"></a>Erstellen einer Vorschau-Angebots-ID

Sie können die Vorschau-Angebots-ID über den **AppSource-Vorschaulink** im Partner Center generieren. Stellen Sie sicher, dass sich das SaaS-Angebot in der Vorschau-Erstellungsphase befindet. So generieren Sie die Vorschau-Angebots-ID:

1. Wechseln Sie zum [Partner Center](https://go.microsoft.com/fwlink/?linkid=2166002) , und melden Sie sich mit Ihren Entwickleranmeldeinformationen an.
1. Wählen Sie **Marketplace-Angebote** aus.
1. Wählen Sie das SaaS-Angebot aus, das Sie in der Vorschau anzeigen möchten.
1. Fügen Sie eine [Vorschaugruppe](/azure/marketplace/create-new-saas-offer-preview) für Ihr SaaS-Angebot hinzu.
1. Wählen Sie den **AppSource-Vorschaulink** unter **"Go Live"** aus, um die Vorschau-Angebots-ID in der Adressleiste des Browsers mit dem Format *"publisherId.offerId-preview* " zu finden.

    :::image type="content" source="../../../../assets/images/apps-in-meetings/publish-status-publisher-signoff.png" alt-text="Vorschau-Angebots-ID" border="true" :::

1. Kopieren Sie die Vorschau-Angebots-ID aus der Browseradressleiste.

      :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-monetized-apps-preview-offer-id.png" alt-text="Vorschau-Angebots-ID" border="true" :::

    > [!NOTE]
    > Im Gegensatz zu einer öffentlichen Angebots-ID kann die Vorschau-Angebots-ID mit dem Suffix *-preview* erkannt werden. Beispiel: **publisherId.offerId-preview**.

## <a name="configure-your-app-with-the-preview-offer-id"></a>Konfigurieren Ihrer App mit der Vorschau-Angebots-ID

Bevor Sie beginnen, melden Sie sich beim **Entwicklerportal** mit einem Entwicklerkonto mit **Vorschauziel an**, damit Benutzer Ihre Abonnementpläne im Teams Store anzeigen können.

Nachdem Sie Ihre Vorschau-Angebots-ID generiert haben, verknüpfen Sie die Angebots-ID mit Ihrer Teams-App. So verknüpfen Sie die Angebots-ID:

1. Wechseln Sie zum [Entwicklerportal](https://dev.teams.microsoft.com/) , und melden Sie sich mit Ihren Entwickleranmeldeinformationen an.
1. Wählen Sie im linken Bereich **Apps** aus.
1. Wählen Sie die App aus, mit der das SaaS-Angebot verknüpft werden soll.
1. Wählen Sie **Pläne und Preise** aus, und geben Sie die **Publisher-ID** und **die Angebots-ID ein**.  
  Stellen Sie sicher, dass die Angebots-ID *das Suffix -preview* enthält.
1. Wählen Sie **"Anzeigen** " aus, um eine Vorschau Ihrer Abonnementpläne anzuzeigen.
1. Überprüfen Sie die unter **"Apps-Abonnement** " aufgeführten Pläne, und wählen Sie " **Speichern**" aus.

    :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-add-offer-id.png" alt-text="Angebots-ID hinzufügen" :::

Die subscriptionOffer-Eigenschaft wird Ihrem App-Manifest hinzugefügt.

```json
"subscriptionOffer": {
     "offerId": "publisherId.offerId-preview"  
     }
```

>[!NOTE]
> Suchen Sie nach dem *Bezeichnungsvorschau-Angebot* neben dem **App-Abonnement** , um zu überprüfen, ob es sich bei dem Angebot um ein Vorschauangebot handelt.

## <a name="sideload-the-app-to-teams"></a>Querladen der App an Teams

Nachdem Sie Ihre App mit der Vorschau-Angebots-ID konfiguriert haben, erstellen Sie ein aktualisiertes App-Paket, und laden Sie es in Teams hoch, um die End-to-End-Kauferfahrung zu testen. Weitere Informationen finden Sie unter [Hochladen Ihrer App in Microsoft Teams](../../apps-upload.md). Sie können im Entwicklerportal auch "**Vorschau" in Teams** für Teams auswählen, um Ihre App schnell im Teams-Client zu starten.

Wenn das Vorschauangebot im App-Manifest angegeben ist und die Vorschaugruppe im Partner Center für das Angebot definiert ist, wird dem Benutzer die Schaltfläche " **Abonnement kaufen** " angezeigt.

:::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-buy-subscription.png" alt-text="Erwerben eines Abonnements" border="true":::

### <a name="error-scenarios"></a>Fehlerszenarien

* Wenn die Angebots-ID angegeben ist, der Benutzer aber nicht Teil der im Partner Center definierten **Vorschaugruppe** ist, ist die Schaltfläche " **Abonnement kaufen** " nicht aktiviert, und die App zeigt dem Benutzer die folgende Warnmeldung an:

  Es wurden keine Pläne mit **-preview** gefunden. Stellen Sie sicher, dass Sie sich in der Vorschaugruppe befinden.

  :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-no-preview-audience.png" alt-text="Keine Zielgruppe vor dem Ziel" border="true" :::

* Wenn es sich bei der im App-Manifest angegebenen Angebots-ID nicht um ein Vorschauangebot handelt, zeigt die App dem Benutzer die folgende Warnmeldung an, und das Querladen ist deaktiviert:
  
  Dies ist kein Vorschauangebot. Achten Sie darauf, die **-preview** an die Angebots-ID anzufügen.

  :::image type="content" source="../../../../assets/images/apps-in-meetings/test-preview-no-preview-offer-id.png" alt-text="no -preview" border="true" :::

## <a name="see-also"></a>Siehe auch

* [Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App](include-saas-offer.md)
* [Erstellen eines SaaS-Angebots (Software as a Service)](include-saas-offer.md#create-your-saas-offer)
* [Hinzufügen einer Vorschaugruppe für ein SaaS-Angebot](/azure/marketplace/create-new-saas-offer-preview)
* [Vorschauerstellungsphase](/azure/marketplace/review-publish-offer)
* [Überprüfen und Veröffentlichen eines Angebots auf dem kommerziellen Marketplace](/azure/marketplace/review-publish-offer#validation-and-publishing-steps)
