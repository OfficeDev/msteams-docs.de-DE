---
title: Registerkarten auf mobilen Geräten
description: In diesem Modul erfahren Sie mehr über die Implementierung von Registerkarten auf Microsoft Teams Mobilgeräten, deren Authentifizierung, Verbindung mit geringer Bandbreite, Testen auf mobilen Clients, Verteilung und vieles mehr.
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: da9757ee0153b3f2fe80e576e156f45bc90a15cd
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144265"
---
# <a name="tabs-on-mobile"></a>Registerkarten auf mobilen Geräten

Wenn Sie eine Microsoft Teams-App erstellen, die eine Registerkarte enthält, müssen Sie testen, wie Ihre Registerkarte sowohl auf dem Android als auch auf iOS Microsoft Teams Clients funktioniert. In diesem Artikel werden einige der wichtigsten Szenarien beschrieben, die Sie berücksichtigen müssen.

Wenn Ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Clients angezeigt werden soll, muss die [`setSettings()`](/javascript/api/@microsoft/teams-js/microsoftteams.settings?view=msteams-client-js-latest#@microsoft-teams-js-microsoftteams-settings-setsettings&preserve-view=true) Konfiguration einen Wert für die `websiteUrl` Eigenschaft aufweisen. Um eine optimale Benutzererfahrung zu gewährleisten, müssen Sie die Anleitungen für Registerkarten auf mobilen Geräten in diesem Artikel befolgen, wenn Sie Ihre Registerkarten erstellen.

Apps[, die über den Teams Store verteilt](~/concepts/deploy-and-publish/appsource/publish.md) werden, verfügen über einen separaten Genehmigungsprozess für mobile Clients. Das Standardverhalten solcher Apps lautet wie folgt:

| **App-Funktion** | **Verhalten, wenn die App genehmigt wurde** | **Verhalten, wenn die App nicht genehmigt wurde** |
| --- | --- | --- |
| **Persönliche Registerkarten** | Die App wird in der unteren Leiste der mobilen Clients angezeigt. Registerkarten werden im Teams-Client geöffnet. | Die App wird nicht in der unteren Leiste der mobilen Clients angezeigt. |
| **Kanal- und Gruppenregisterkarten** | Die Registerkarte wird im Teams-Client mithilfe von `contentUrl`geöffnet. | Die Registerkarte wird in einem Browser außerhalb des Teams-Clients mit geöffnet`websiteUrl`. |

> [!NOTE]
>
> * Apps, die zur Veröffentlichung auf Teams an [AppSource](https://appsource.microsoft.com) übermittelt werden, werden automatisch für die Reaktionsfähigkeit mobiler Geräte ausgewertet. Wenden Sie sich bei allen Abfragen an teamsubm@microsoft.com.
> * Für alle Apps, die nicht über AppSource verteilt werden, werden die Registerkarten standardmäßig in einer In-App-Webview innerhalb der Teams Clients geöffnet, und es ist kein separater Genehmigungsprozess erforderlich.
> * Das Standardverhalten von Apps gilt nur, wenn es über den Teams Store verteilt wird. Standardmäßig werden alle Registerkarten im Teams-Client geöffnet.
> * Wenn Sie eine Bewertung Ihrer App für mobile Freundlichkeit initiieren möchten, wenden Sie sich mit Ihren App-Details an teamsubm@microsoft.com.

## <a name="authentication"></a>Authentifizierung

Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.

## <a name="low-bandwidth-and-intermittent-connections"></a>Geringe Bandbreite und zeitweilige Verbindungen

Mobile Clients funktionieren mit geringer Bandbreite und zeitweiligen Verbindungen. Ihre App muss alle Timeouts entsprechend behandeln, indem dem Benutzer eine Kontextnachricht bereitgestellt wird. Sie müssen auch Statusanzeigen verwenden, um Ihren Benutzern Feedback für lang andauernde Prozesse zu geben.

## <a name="testing-on-mobile-clients"></a>Testen auf mobilen Clients

Sie müssen überprüfen, ob Ihre Registerkarte auf mobilen Geräten unterschiedlicher Größe und Qualität ordnungsgemäß funktioniert. Für Android Geräte können Sie [DevTools](~/tabs/how-to/developer-tools.md) verwenden, um Ihre Registerkarte zu debuggen, während sie ausgeführt wird. Es wird empfohlen, sowohl auf Geräten mit hoher als auch auf leistungsschwachen Geräten zu testen, einschließlich eines Tablets.

## <a name="distribution"></a>Verteilung

Apps, die im Teams Store aufgeführt sind, müssen für die mobile Verwendung genehmigt werden, damit sie im Teams mobilen Client ordnungsgemäß funktionieren. Die Verfügbarkeit und das Verhalten von Registerkarten hängen davon ab, ob Ihre App genehmigt wurde.

### <a name="apps-on-teams-store-approved-for-mobile"></a>Apps in Teams Store, die für Mobilgeräte genehmigt wurden

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams Store aufgeführt und für die mobile Verwendung genehmigt wurde:

|Funktion   |Mobile Verfügbarkeit?   |Mobiles Verhalten|
|----------|-----------|------------|
|Kanal <br /> und Gruppenregisterkarte|Ja|Die Registerkarte wird im Teams mobilen Clients mithilfe der `contentUrl` App-Konfiguration geöffnet.|
|Persönliche App|Ja|Jede Registerkarte auf der Registerkarte "Persönliche App" wird im Teams mobilen Clients mithilfe der entsprechenden `contentUrl` Konfiguration geöffnet.|

### <a name="apps-on-teams-store-not-approved-for-mobile"></a>Apps in Teams Store nicht für Mobilgeräte genehmigt

In der folgenden Tabelle werden die Verfügbarkeit und das Verhalten von Registerkarten beschrieben, wenn die App im Teams Store aufgeführt, aber nicht für die mobile Verwendung genehmigt wurde:

| Funktion | Mobile Verfügbarkeit? | Mobiles Verhalten |
|----------|-----------|------------|
|Kanal- und Gruppenregisterkarte|Ja|Die Registerkarte wird im Standardbrowser des Geräts anstelle des Teams mobilen Clients mithilfe der `websiteUrl` App-Konfiguration geöffnet, die ebenfalls in der [Funktion](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk#settings-namespace) des Quellcodes `setSettings()` enthalten sein muss. Benutzer können die Registerkarte jedoch im Teams mobilen Clients anzeigen, indem sie neben der App **"Weitere**" auswählen und "**Öffnen**" auswählen, wodurch die Konfiguration Ihrer App `contentUrl` ausgelöst wird.|
|Persönliche App|Nein|Nicht zutreffend|

### <a name="apps-not-on-teams-store"></a>Apps, die nicht in Teams Store gespeichert sind

Wenn Sie Ihre App querladen oder in den App-Katalog einer Organisation veröffentlichen, entspricht das Registerkartenverhalten Teams von Microsoft für Mobile genehmigten Store-Apps.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kontext für Ihre Registerkarte erhalten](~/tabs/how-to/access-teams-context.md)

## <a name="see-also"></a>Siehe auch

* [Richtlinien für den Registerkartenentwurf](~/tabs/design/tabs.md)
* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Planen Teams mobiler Geräte – Teams](~/concepts/design/plan-responsive-tabs-for-teams-mobile.md)
