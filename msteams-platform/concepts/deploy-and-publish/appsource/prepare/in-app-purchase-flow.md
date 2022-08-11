---
title: In-App-Kauffluss für die Monetarisierung von Apps
description: Lernen Sie die grundlegenden Aufgaben und Konzepte kennen, die erforderlich sind, um In-App-Käufe und Testfunktionalitäten in Teams-Apps zu implementieren.
author: v-npaladugu
ms.author: surbhigupta
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 59511c62fbc03b2d730bbbcccf5f4d2eadc37885
ms.sourcegitcommit: f192d7685ee3ddf4a55dc9787d56744403c3f8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2022
ms.locfileid: "67302458"
---
# <a name="in-app-purchases"></a>In-App-Käufe

Microsoft Teams stellt APIs zur Verfügung, mit denen Sie die In-App-Käufe implementieren können, um ein Upgrade von kostenlosen auf kostenpflichtige Teams-Apps durchzuführen. Mit dem In-App-Kauf können Sie Benutzer direkt in Ihrer App von kostenlosen zu kostenpflichtigen Plänen konvertieren.

## <a name="implement-in-app-purchases"></a>Implementieren von In-App-Käufen

Um den Benutzern Ihrer App eine In-App-Kauferfahrung zu bieten, stellen Sie Folgendes sicher:

* Die App basiert auf der [Teams Client-SDK-Bibliothek](https://github.com/OfficeDev/microsoft-teams-library-js).

* Die App ist mit einem transaktionsfähigen [SaaS-Angebot](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md) aktiviert.

* Die App ist mit [RSC-Berechtigungen](#update-manifest) aktiviert.

* Die App wird mit der [`openPurchaseExperience`-API](#purchase-experience-api) aufgerufen.

Die In-App-Kauferfahrung kann entweder durch Aktualisieren der Datei `manifest.json` oder durch Aktivieren von **In-App-Kaufangebote anzeigen** im Abschnitt **Berechtigungen** Ihres **Entwicklerportals** aktiviert werden.

### <a name="update-manifest"></a>Aktualisieren des Manifests

Um die In-App-Kauferfahrung zu aktivieren, aktualisieren Sie Ihre Teams-App-Datei `manifest.json`, indem Sie die RSC-Berechtigungen hinzufügen. Dies ermöglicht Ihren App-Benutzern, ein Upgrade auf eine kostenpflichtige Version Ihrer App durchzuführen und neue Funktionalitäten zu verwenden. Das Update für das App-Manifest lautet wie folgt:

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

### <a name="purchase-experience-api"></a>Kauferfahrungs-API

Rufen Sie die `openPurchaseExperience`-API über Ihre Web-App auf, um In-App-Käufe für die App auszulösen.

Der folgende Codeausschnitt ist ein Beispiel für das Aufrufen der API aus der Teams-App, die mit dem JavaScript-Client-SDK für Teams erstellt wurde:

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/jsonV11)

```json
<div> 
<div class="sectionTitle">openPurchaseExperience</div>
<button onclick="openPurchaseExperience()">openPurchaseExperience</button>
</div>
</body>
<script>
   function openPurchaseExperience()
      microsoftTeams.initialize();
      let callbackcalled = false;
      microsoftTeams.monetization.openPurchaseExperience((e) => {
            console.log("callback is being called");
            console.log(e);
            if (!!e && typeof e !== "string") {
                  alert(JSON.stringify(e));
              }
              return;
            });
      console.log("after callback: ",callbackcalled);
    }
</script>
```

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/jsonV2)

```json
<div>
<div class="sectionTitle">openPurchaseExperience</div>
<button onclick="openPurchaseExperience()">openPurchaseExperience</button>
</div>
</body>
<script>
   function openPurchaseExperience() {
      app.initialize();
    var planInfo = {
        planId: "<Plan id>", // Plan Id of the published SAAS Offer
        term: "<Plan Term>" // Term of the plan.
    }
      monetization.openPurchaseExperience(planInfo);
    }
</script>
```

---

## <a name="end-user-in-app-purchasing-experience"></a>In-App-Kauferfahrung für Endbenutzer

Im folgenden Beispiel zeigt, wie Benutzer Abonnementpläne für eine fiktive Teams-App namens *Contoso Tasks for Teams* erwerben:

1. Suchen Sie im Teams **Store** die App, und wählen Sie sie aus.

1. Wählen Sie im Dialogfeld „App-Details“ die Option **Abonnement kaufen** oder **Für mich hinzufügen** aus.

    :::image type="content" source="~/assets/images/saas-offer/buysubscriptionplancontoso.png" alt-text="Kaufen des Abonnements für die ausgewählte App.":::

1. **Für mich hinzufügen** stellt eine kostenlose Testversion der App zur Verfügung und bietet später ein **Upgrade** auf eine kostenpflichtige Version an.

    :::image type="content" source="~/assets/images/saas-offer/upgradeapp.png" alt-text="Upgraden auf das Abonnement für die ausgewählte App." lightbox="../../../../assets/images/saas-offer/upgradeapp.png":::

1. Wählen Sie im Dialogfeld **Abonnementplan auswählen** den Plan und dann **Kasse** aus.

    :::image type="content" source="~/assets/images/saas-offer/choosingsubscriptionplancontoso.png" alt-text="Auswählen des entsprechenden Abonnementplans." lightbox="../../../../assets/images/saas-offer/choosingsubscriptionplancontoso.png":::

1. Schließen Sie die Transaktion ab, und wählen Sie **Jetzt konfigurieren** aus, um Ihr Abonnement einzurichten.

    :::image type="content" source="~/assets/images/saas-offer/saas-offer-configure-now.png" alt-text="Einrichten des Abonnements." lightbox="../../../../assets/images/saas-offer/saas-offer-configure-now.png":::

    :::image type="content" source="~/assets/images/saas-offer/getstarted.png" alt-text="Zielseite des Abonnements." lightbox="../../../../assets/images/saas-offer/getstarted.png":::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Testvorschau für monetarisierte Apps](~/concepts/deploy-and-publish/appsource/prepare/Test-preview-for-monetized-apps.md)

## <a name="see-also"></a>Siehe auch

* [Einschließen eines SaaS-Angebots in Ihre Microsoft Teams-App](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
* [Erstellen eines SaaS-Angebots (Software as a Service)](include-saas-offer.md#create-your-saas-offer)
