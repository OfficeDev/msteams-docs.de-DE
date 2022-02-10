---
title: In-App-Kaufablauf für die Monetarisierung von Apps
description: Lernen Sie die grundlegenden Aufgaben und Konzepte kennen, die erforderlich sind, um In-App-Käufe und Testfunktionen in Teams-Apps zu implementieren.
author: v-npaladugu
ms.author: surbhigupta
ms.topic: how-to
localization_priority: Normal
ms.openlocfilehash: 90b1bf713e898a0f61c540e76ee5dde77603e70b
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518240"
---
# <a name="in-app-purchases"></a>In-App-Käufe

Microsoft Teams APIs bereitstellen, mit denen Sie die In-App-Käufe implementieren können, um von kostenlos auf kostenpflichtige Teams Apps zu aktualisieren. Mit dem In-App-Kauf können Sie Benutzer von kostenlos in kostenpflichtige Pläne direkt aus Ihrer App heraus konvertieren.

> [!NOTE]
> In-App-Käufe für Teams-Apps sind derzeit nur in der [**Entwicklervorschau**](/microsoftteams/platform/resources/dev-preview/developer-preview-intro) verfügbar.

## <a name="implement-in-app-purchases"></a>Implementieren von In-App-Käufen

Um den Benutzern Ihrer App eine In-App-Kauferfahrung zu bieten, stellen Sie Folgendes sicher:

* Die App basiert auf [Teams Client-SDK-Bibliothek](https://github.com/OfficeDev/microsoft-teams-library-js).

* Die App ist mit einem transaktionsfähigen [SaaS-Angebot](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md) aktiviert.

* Die App ist mit [RSC-Berechtigungen](#update-manifest) aktiviert.

* Die App wird mit [`openPurchaseExperience` der API](#purchase-experience-api) aufgerufen.

Die In-App-Kauferfahrung kann entweder durch Aktualisieren der Datei **"manifest.json** " oder durch Aktivieren von **"In-App-Kaufangebote anzeigen" im** Abschnitt **"Berechtigungen** " Ihres **Entwicklerportals** aktiviert werden.

### <a name="update-manifest"></a>Updatemanifest

Um die In-App-Kauferfahrung zu aktivieren, aktualisieren Sie ihre Teams App **manifest.json-Datei**, indem Sie die RSC-Berechtigungen hinzufügen. Es ermöglicht Ihren App-Benutzern, ein Upgrade auf eine kostenpflichtige Version Ihrer App durchzuführen und neue Funktionen zu verwenden. Das Update für das App-Manifest lautet wie folgt:

```json

"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "InAppPurchase.Allow.User",
                "type": "Delegated"
            }
        ]
    }
}
```

### <a name="purchase-experience-api"></a>Einkaufserfahrungs-API

Rufen Sie die API aus Ihrer Web-App auf, um den In-App-Kauf für die `openPurchaseExperience` App auszulösen.

Es folgt ein Beispiel für den Aufruf der API aus der App:

```json
<body> 
<div> 
<div class="sectionTitle">openPurchaseExperience</div> 
<button onclick="openPurchaseExperience()">openPurchaseExperience</button> 
</div> 
</body> 
<script> 
   function openPurchaseExperience() {
      microsoftTeams.initialize();
      let callbackcalled = false;
      microsoftTeams.monetization.openPurchaseExperience((e) => {
      console.log("callback is being called");
      callbackcalled = true;  
      if (!!e && typeof e !== "string") {
            e = JSON.stringify(e);
            alert(e);
        }
        return;
      });
      console.log("after callback: ",callbackcalled);
    } 
</script> 
```

## <a name="end-user-in-app-purchasing-experience"></a>In-App-Kauferfahrung für Endbenutzer

Das folgende Beispiel zeigt die Benutzer zum Kauf von Abonnementplänen für eine fiktive Teams-App namens *Contoso Tasks for Teams*:

1. Suchen Sie im Teams **Store** die App, und wählen Sie sie aus.

1. Wählen Sie im Dialogfeld "App-Details" **die Option "Abonnement kaufen** " oder **"Für mich hinzufügen**" aus. 

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplancontoso.png" alt-text="Kauf des Abonnements für die ausgewählte App." border="true":::

    
1. **Add for me** offers a free trial version of the app and later **Upgrade** it to a paid version.

    :::image type="content" source="~/assets/images/saas-offer/upgradeapp.png" alt-text="Upgrade auf das Abonnement für die ausgewählte App." border="true":::

1. Wählen Sie im Dialogfeld **"Abonnementplan auswählen** " den Plan aus, und wählen Sie **"Auschecken"** aus.

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplancontoso.png" alt-text="Auswählen des entsprechenden Abonnementplans." border="true":::

1. Schließen Sie die Transaktion ab, und wählen Sie **"Jetzt konfigurieren** " aus, um Ihr Abonnement einzurichten.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-configure-now.png" alt-text="Einrichten des Abonnements." border="true":::

    :::image type="content" source="~/assets/images/saas-offer/getstarted.png" alt-text="Angebotsseite des Abonnements." border="true":::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Testvorschau für monetarisierte Apps](~/concepts/deploy-and-publish/appsource/prepare/Test-preview-for-monetized-apps.md)

## <a name="see-also"></a>Weitere Artikel

* [Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
* [Erstellen eines SaaS-Angebots (Software as a Service)](include-saas-offer.md#create-your-saas-offer)
