---
title: Registerkarten auf mobilen Geräten
description: Beschreibt Entwicklerüberlegungen für die Implementierung von Registerkarten auf Microsoft Teams Mobilgeräten.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 612084a1ff4258da16dc00f9b5a6844eead57f54
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140292"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Wenn Sie eine Microsoft Teams-App erstellen, die eine Registerkarte enthält, müssen Sie testen, wie Ihre Registerkarte auf android- und iOS-Microsoft Teams-Clients funktioniert. In diesem Artikel werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

Wenn Sie ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Clients anzeigen möchten, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` aufweisen. Um eine optimale Benutzererfahrung zu gewährleisten, müssen Sie die Anleitungen für Registerkarten auf mobilgeräten in diesem Artikel befolgen, wenn Sie Ihre Registerkarten erstellen.

Apps, [die über den Teams Store verteilt werden,](~/concepts/deploy-and-publish/appsource/publish.md) verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps lautet wie folgt:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wurde** | **Verhalten, wenn die App nicht genehmigt wurde** |
| --- | --- | --- |
| **Persönliche Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams Client geöffnet. | Die App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Kanal- und Gruppenregisterkarten** | Die Registerkarte wird im Teams Client mit `contentUrl` geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mit `websiteUrl` geöffnet. |

> [!NOTE]
> * Apps, die zur Veröffentlichung auf Teams an [AppSource](https://appsource.microsoft.com) übermittelt werden, werden automatisch auf die Reaktionsfähigkeit mobiler Geräte ausgewertet. Wenden Sie sich bei Abfragen an teamsubm@microsoft.com.
> * Für alle Apps, die nicht über AppSource verteilt werden, werden die Registerkarten standardmäßig in einer In-App-Webansicht innerhalb der Teams Clients geöffnet, und es ist kein separater Genehmigungsprozess erforderlich.
> * Das Standardverhalten von Apps gilt nur, wenn sie über den Teams Store verteilt werden. Standardmäßig werden alle Registerkarten im Teams Client geöffnet.
> * Wenden Sie sich an teamsubm@microsoft.com mit Ihren App-Details, um eine Bewertung Der Benutzerfreundlichkeit Ihrer App zu initiieren.

## <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

## <a name="low-bandwidth-and-intermittent-connections"></a>Geringe Bandbreite und zeitweilige Verbindungen

Mobile Clients funktionieren mit geringer Bandbreite und zeitweisen Verbindungen. Ihre App muss alle Timeouts entsprechend behandeln, indem dem Benutzer eine Kontextnachricht bereitgestellt wird. Außerdem müssen Sie Fortschrittsindikatoren verwenden, um Ihren Benutzern Feedback für lange dauernde Prozesse zu geben.

## <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert. Für Android-Geräte können Sie [DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte zu debuggen, während sie ausgeführt wird. Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf geräten mit niedriger Leistung, einschließlich tablet, zu testen.

## <a name="distribution"></a>Verteilung

Apps, die im Teams Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im Teams mobilen Client ordnungsgemäß funktionieren. Die Verfügbarkeit und das Verhalten von Registerkarten hängen davon ab, ob Ihre App genehmigt wurde.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Apps auf Teams Store für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams Store aufgeführt und für die mobile Verwendung genehmigt wurde:

|Funktion   |Mobile Verfügbarkeit?   |Mobiles Verhalten|
|----------|-----------|------------|
|Kanal <br /> und Gruppenregisterkarte|Ja|Die Registerkarte wird im Teams mobilen Client mithilfe der `contentUrl` App-Konfiguration geöffnet.|
|Persönliche App|Ja|Jede Registerkarte auf der persönlichen App-Registerkarte wird im Teams mobilen Client mit der entsprechenden `contentUrl` Konfiguration geöffnet.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Apps im Teams Store nicht für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams Store aufgeführt ist, jedoch nicht für die mobile Verwendung genehmigt wurde:

| Funktion | Mobile Verfügbarkeit? | Mobiles Verhalten |
|----------|-----------|------------|
|Kanal- und Gruppenregisterkarte|Ja|Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients mithilfe der `websiteUrl` App-Konfiguration geöffnet, die auch in der Quellcodefunktion enthalten sein `setSettings()` [](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true)muss. Benutzer können die Registerkarte jedoch im Teams mobilen Client anzeigen, indem sie neben der App **"Mehr"** auswählen und **"Öffnen"** auswählen, wodurch die `contentUrl` App-Konfiguration ausgelöst wird.|
|Persönliche App|Nein|–|

### <a name="apps-not-on-teams-store"></a>Apps, die nicht im Teams Store gespeichert sind

Wenn Sie Ihre App querladen oder im App-Katalog einer Organisation veröffentlichen, entspricht das Registerkartenverhalten Teams Store-Apps, die von Microsoft für Mobile genehmigt wurden.

## <a name="see-also"></a>Siehe auch

* [Richtlinien für den Registerkartenentwurf](~/tabs/design/tabs.md)
* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Voraussetzungen](~/tabs/how-to/tab-requirements.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Erstellen einer Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md)
* [Erstellen einer Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md)
* [Erstellen einer Seite zum Entfernen ihrer Registerkarte](~/tabs/how-to/create-tab-pages/removal-page.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Aufgeklappte Registerkartenverknüpfung und Phasenansicht](~/tabs/tabs-link-unfurling.md)
* [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)
* [Änderungen am Registerkartenrand](~/resources/removing-tab-margins.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kontext für Ihre Registerkarte erhalten](~/tabs/how-to/access-teams-context.md)
