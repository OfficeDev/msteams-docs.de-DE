---
title: Registerkarten auf mobilen Geräten
description: Erfahren Sie, wie registerkartenfunktionen auf Android- und iOS Microsoft Teams-Clients (mobil), deren Authentifizierung, Verbindung mit geringer Bandbreite, Tests oder Verteilung funktionieren.
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 8dac56cd609466c116f39baf5dc9d9a7970645ec
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820080"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Wenn Sie eine Microsoft Teams-App erstellen, die eine Registerkarte enthält, müssen Sie testen, wie Ihre Registerkarte auf den Microsoft Teams-Clients für Android und iOS funktioniert. In diesem Artikel werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

Wenn Sie sich dafür entscheiden, dass Ihre Kanal- oder Gruppenregisterkarte auf mobilen Teams-Clients angezeigt wird, muss die [`setSettings()`](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-settings-setsettings&preserve-view=true) Konfiguration einen Wert für die `websiteUrl` Eigenschaft aufweisen. Um eine optimale Benutzererfahrung zu gewährleisten, müssen Sie beim Erstellen Ihrer Registerkarten die Anleitung für Registerkarten auf Mobilgeräten in diesem Artikel befolgen.

Apps, [die über den Teams Store verteilt](~/concepts/deploy-and-publish/appsource/publish.md) werden, verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps sieht wie folgt aus:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wird** | **Verhalten, wenn die App nicht genehmigt wurde** |
| --- | --- | --- |
| **Persönliche Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams-Client geöffnet. | Die App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Kanal- und Gruppenregisterkarten** | Die Registerkarte wird im Teams-Client mit `contentUrl`geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mit `websiteUrl`geöffnet. |

> [!NOTE]
>
> * Apps, die zur Veröffentlichung in Teams an [AppSource](https://appsource.microsoft.com) übermittelt werden, werden automatisch auf mobile Reaktionsfähigkeit ausgewertet. Wenden Sie sich für alle Abfragen an teamsubm@microsoft.com.
> * Für alle Apps, die nicht über AppSource verteilt werden, werden die Registerkarten standardmäßig in einer In-App-Webansicht innerhalb der Teams-Clients geöffnet, und es ist kein separater Genehmigungsprozess erforderlich.
> * Das Standardverhalten von Apps gilt nur, wenn sie über den Teams Store verteilt werden. Standardmäßig werden alle Registerkarten im Teams-Client geöffnet.
> * Wenden Sie sich an teamsubm@microsoft.com mit Ihren App-Details, um eine Bewertung Ihrer App für die Mobile-Freundlichkeit zu initiieren.

## <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie das Teams JavaScript SDK mindestens auf Version 1.4.1 aktualisieren.

## <a name="low-bandwidth-and-intermittent-connections"></a>Geringe Bandbreite und zeitweilige Verbindungen

Mobile Clients funktionieren mit geringer Bandbreite und zeitweiligen Verbindungen. Ihre App muss alle Timeouts angemessen behandeln, indem dem Benutzer eine kontextbezogene Nachricht bereitgestellt wird. Sie müssen auch Statusanzeigen verwenden, um Ihren Benutzern Feedback für prozesse mit langer Ausführungsdauer zu geben.

## <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten verschiedener Größen und Qualitäten ordnungsgemäß funktioniert. Für Android-Geräte können Sie [DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte zu debuggen, während sie ausgeführt wird. Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf niedriger Leistung zu testen, einschließlich eines Tablets.

## <a name="distribution"></a>Verteilung

Apps, die im Teams Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im mobilen Teams-Client ordnungsgemäß funktionieren. Die Verfügbarkeit und das Verhalten von Registerkarten hängen davon ab, ob Ihre App genehmigt wurde.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Apps im Teams Store für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams Store aufgeführt und für die mobile Verwendung genehmigt wird:

|Funktion   |Mobile Verfügbarkeit?   |Mobiles Verhalten|
|----------|-----------|------------|
|Kanal <br /> Und Registerkarte "Gruppe"|Ja|Die Registerkarte wird im mobilen Teams-Client mit der Konfiguration Ihrer App `contentUrl` geöffnet.|
|Persönliche App|Ja|Jede Registerkarte auf der Registerkarte "Persönliche App" wird im mobilen Teams-Client mit ihrer jeweiligen `contentUrl` Konfiguration geöffnet.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Apps im Teams Store nicht für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams Store aufgeführt, aber nicht für die mobile Verwendung genehmigt wird:

| Funktion | Mobile Verfügbarkeit? | Mobiles Verhalten |
|----------|-----------|------------|
|Registerkarte "Kanal" und "Gruppe"|Ja|Die Registerkarte wird im Standardbrowser des Geräts anstelle des mobilen Teams-Clients mit der Konfiguration Ihrer App `websiteUrl` geöffnet, die ebenfalls in der [Funktion](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk#settings-namespace) Ihres Quellcodes `setSettings()` enthalten sein muss. Benutzer können jedoch die Registerkarte im mobilen Teams-Client anzeigen, indem sie neben der App **Mehr** auswählen und **Dann Öffnen** auswählen, wodurch die `contentUrl` Konfiguration Ihrer App ausgelöst wird.|
|Persönliche App|Nein|Nicht zutreffend|

> [!NOTE]
> Die Botnachrichten werden im Chatabschnitt angezeigt, wenn eine mobile App sowohl über die Bot- als auch die Registerkartenfunktionen verfügt.
>
> Wenn Sie **Chat** der Bot-App auswählen und **Mehr (...)** auswählen, wird die Registerkartenfunktion dieser App in der Liste nicht angezeigt. Wenn Sie jedoch unten rechts **im Chatabschnitt** **Mehr (...)** auswählen, können Sie die Registerkarten-App mit einem Link zur Bot-App-Funktion dieser App anzeigen.

### <a name="apps-not-on-teams-store"></a>Apps, die sich nicht im Teams Store befinden

Wenn Sie Ihre App querladen oder im App-Katalog einer Organisation veröffentlichen, ist das Verhalten der Registerkarte dasselbe wie Teams Store-Apps, die von Microsoft für Mobilgeräte genehmigt wurden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kontext für Ihre Registerkarte erhalten](~/tabs/how-to/access-teams-context.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../what-are-tabs.md)
* [Erstellen von Registerkarten mit adaptiven Karten](../how-to/build-adaptive-card-tabs.md)
* [Erstellen einer persönlichen Registerkarte](../how-to/create-personal-tab.md)
* [Planen reaktionsfähiger Registerkarten für Teams Mobile](../../concepts/design/plan-responsive-tabs-for-teams-mobile.md)
* [Entwerfen Sie Ihre Registerkarte für Microsoft Teams](tabs.md)
* [Entwicklertools für Microsoft Teams-Registerkarten](../how-to/developer-tools.md)
* [Testen eigener Apps](../../concepts/build-and-test/test-app-overview.md)
* [Verteilen Ihrer Microsoft Teams-App](../../concepts/deploy-and-publish/apps-publish-overview.md)
* [Teams-App-Paket erstellen](../../concepts/build-and-test/apps-package.md)
