---
title: Registerkarten auf mobilen Geräten
description: Beschreibt Überlegungen von Entwicklern zum Implementieren von Registerkarten auf Microsoft Teams Mobile.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 41ba96b64bd31f3b226aeba72969bc44c1ae8955
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630656"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Beim Erstellen einer Microsoft Teams-App, die eine Registerkarte enthält, müssen Sie berücksichtigen (und testen), wie Ihre Registerkarte sowohl auf den Android- als auch auf iOS-Microsoft Teams funktioniert. In den folgenden Abschnitten werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

## <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

## <a name="low-bandwidth-and-intermittent-connections"></a>Niedrige Bandbreite und zeitweilige Verbindungen

Mobile Clients müssen regelmäßig mit geringer Bandbreite und zeitweiligen Verbindungen funktionieren. Ihre App sollte timeouts entsprechend behandeln, indem sie dem Benutzer eine kontextbezogene Nachricht zur Verfügung stellt. Sie sollten auch Fortschrittsindikatoren der Benutzer verwenden, um Ihren Benutzern Feedback für alle lang laufenden Prozesse zu geben.

## <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert. Für Android-Geräte können Sie [devTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte während der Ausführung zu debuggen. Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf niedriger Leistung zu testen, einschließlich eines Tablets.

## <a name="distribution"></a>Verteilung

Apps, die im Teams-Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im mobilen Client Teams funktionieren. Verfügbarkeit und Verhalten von Registerkarten hängen davon ab, ob Ihre App genehmigt wurde.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Apps im Teams für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams und für die mobile Verwendung genehmigt ist:

|Funktion   |Mobile Verfügbarkeit?   |Mobiles Verhalten|
|----------|-----------|------------|
|Kanal <br /> Registerkarte "Gruppe" und "Gruppe"|Ja|Die Registerkarte wird im Teams mobilen Client mithilfe der Konfiguration Ihrer App `contentUrl` geöffnet.|
|Persönliche App|Ja|Jede Registerkarte auf der Registerkarte persönliche App wird im Teams mobilen Client mit der entsprechenden Konfiguration `contentUrl` geöffnet.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Apps im Teams store nicht für mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams,jedoch nicht für die mobile Verwendung genehmigt ist:

| Funktion | Mobile Verfügbarkeit? | Mobiles Verhalten |
|----------|-----------|------------|
|Registerkarte "Kanal" und "Gruppe"|Ja|Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients geöffnet, der die Konfiguration Ihrer App verwendet, die ebenfalls in der Quellcodefunktion `websiteUrl` enthalten `setSettings()` [sein muss.](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true) Benutzer können die Registerkarte jedoch weiterhin im mobilen Client  Teams anzeigen, indem Sie neben der App weitere auswählen und **Öffnen** auswählen, wodurch die Konfiguration Ihrer App ausgelöst `contentUrl` wird.|
|Persönliche App|Nein|Nicht zutreffend|

### <a name="apps-not-on-teams-store"></a>Apps, die nicht im Teams sind

Wenn Sie Ihre App oder Veröffentlichung querladen im App-Katalog einer Organisation, ist das Registerkartenverhalten identisch mit Teams von Microsoft für Mobile genehmigten Store-Apps.

## <a name="see-also"></a>Sehen Sie ebenfalls

* [Richtlinien für das Registerkartendesign](~/tabs/design/tabs.md)
