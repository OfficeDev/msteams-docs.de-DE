---
title: Microsoft Teams und das SameSite-Cookieattribut (Update 2020)
author: surbhigupta
description: beschreibt die Attribute des SameSite-Cookies
keywords: Cookieattribute samesite
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 9e899cd7f4e8adcf55a39fc5cef434a7faa4b0ba
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068629"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams und das SameSite-Cookieattribut (Update 2020)

## <a name="cookies-in-brief"></a>Kurz zusammengefasste Cookies

 Cookies sind Textzeichenfolgen, die von Websites gesendet und vom Webbrowser auf einem Computer gespeichert werden. Sie werden in der Regel für die Authentifizierung und Personalisierung verwendet, z. B. das Abrufen zustandsbehafteten Informationen, das Beibehalten von Benutzereinstellungen, das Aufzeichnen von Browseraktivitäten und das Anzeigen relevanter Anzeigen. Cookies sind immer mit einer bestimmten Domäne verknüpft und können von verschiedenen Parteien installiert werden. Sie werden wie folgt kategorisiert:

 |Cookie|Bereich|
 | ------ | ------ |
 |**Erstanbietercookie**|Ein Erstanbieter-Cookie wird von Websites erstellt, die ein Benutzer besucht, und wird verwendet, um Daten wie Einkaufswagenelemente, Anmeldeinformationen zu speichern. Beispielsweise Authentifizierungscookies und andere Analysen.|
 |**Cookie von Drittanbietern**|Ein Cookies von Drittanbietern ist technisch identisch mit einem Erstanbietercookie. Der Unterschied besteht darin, dass Daten über einen Datenpartnerschaftsvertrag mit einer zweiten Partei geteilt werden. Beispielsweise [Microsoft Teams Analyse und Berichterstellung.](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference) |
 |**Drittanbietercookie**|Ein Drittanbietercookie wird von einer anderen Domäne als der Domäne installiert, die der Benutzer explizit besucht hat, und wird hauptsächlich für die Nachverfolgung verwendet. Beispielsweise "Gefällt mir"-Schaltflächen, Anzeigendienst und Livechats.|

### <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anforderungen

Vor der Einführung von SameSite-Einschränkungen, wenn Cookies im Browser gespeichert wurden, wurden sie *an jede* HTTP-Webanforderung angefügt und vom Set-Cookie HTTP-Antwortheader an den Server gesendet. Vorhersagbar, dass diese Leistung das Potenzial hatte, Sicherheitsrisiken wie siteübergreifende CSRF-Angriffe (Request Forgery) zu schaffen. *Siehe* [HTTP-Cookies.](https://developer.mozilla.org/docs/Web/HTTP/Cookies) Die SameSite-Komponente hat diese Gefährdung durch ihre Implementierung und Verwaltung im SetCookie-Header verringert.

### <a name="samesite-attribute-initial-release"></a>SameSite-Attribut: erste Version

In Google Chrome, Version 51, wurde die SetCookie SameSite-Spezifikation als *optionales* Attribut eingeführt. Ab Build 17672 Windows 10 die SameSite-Cookieunterstützung für den [Microsoft Edge Browser](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/)eingeführt.

Entwickler können das Hinzufügen des SameSite-Cookieattributs zum SetCookie-Header deaktivieren oder es mit einer der beiden Einstellungen *Lax* und *Strict* hinzufügen. Ein nicht implementiertes SameSite-Attribut wurde als Standardzustand betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookieattribut: Version 2020

Chrome 80, das im Februar 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und erlegt standardmäßig Cookierichtlinien auf. Drei Werte können an das aktualisierte SameSite-Attribut übergeben werden: *Strict*, *Lax* oder *None*. Cookies, die nicht das SameSite-Attribut angeben, werden standardmäßig auf `SameSite=Lax` .

|Setting | Durchsetzung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur in einem *Erstanbieterkontext* und mit HTTP GET-Anforderungen gesendet. SameSite-Cookies werden bei websiteübergreifenden Unteranforderungen, z. B. Aufrufen zum Laden von Bildern oder iFrames, beibehalten, aber gesendet, wenn ein Benutzer von einer externen Website zu der URL navigiert, z. B. durch Folgen eines Links.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Streng** |Der Browser sendet Cookies nur für Kontextanforderungen von Erstanbietern (Anforderungen, die von der Website stammen, die das Cookie festgelegt hat). Wenn die Anforderung von einer anderen URL als der des aktuellen Speicherorts stammt, wird keine der mit dem Attribut markierten Cookies `Strict` gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl im Erstanbieterkontext als auch in ursprungsübergreifenden Anforderungen gesendet. Der Wert muss jedoch explizit festgelegt werden, **`None`** und alle Browseranforderungen **müssen dem HTTPS-Protokoll folgen** und das Attribut **`Secure`** enthalten, das eine verschlüsselte Verbindung erfordert. Cookies, die diese Anforderung nicht erfüllen, werden **abgelehnt.** <br/>**Beide Attribute sind zusammen erforderlich.** Wenn nur **`None`** ohne oder wenn das **`Secure`**  HTTPS-Protokoll nicht verwendet wird, wird das Drittanbietercookie abgelehnt.| Optional, aber wenn festgelegt, ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams Auswirkungen und Anpassungen

1. Aktivieren Sie die relevante SameSite-Einstellung für Ihre Cookies, und überprüfen Sie, ob Ihre Apps und Erweiterungen weiterhin in Teams funktionieren.
1. Wenn Ihre Apps oder Erweiterungen fehlschlagen, nehmen Sie die erforderlichen Korrekturen vor der Chrome 80-Version vor.
1. Interne Microsoft-Partner können dem folgenden Team beitreten, wenn sie weitere Informationen oder Hilfe zu diesem Problem benötigen: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47> .

> [!NOTE]
> Aus Gründen der bewährten Vorgehensweise wird empfohlen, dass Sie immer SameSite-Attribute festlegen, um die beabsichtigte Verwendung für Ihre Cookies widerzuspiegeln. Verlassen Sie sich nicht auf das Standardverhalten des Browsers. Weitere Informationen finden Sie unter ["Entwickler: Vorbereiten auf die neue SameSite=None". Secure Cookie Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen

* Teams Registerkarten zum `<iframes>` Einbetten von Inhalten verwendet, die in einem Kontext der obersten Ebene oder im Erstanbieterkontext angezeigt werden.
* Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Erlebnissen in Ihrer Teams-Anwendung. Ähnlich wie bei einer Registerkarte wird ein modales Fenster auf der aktuellen Seite geöffnet.
* Mithilfe von Nachrichtenerweiterungen können Sie anreicherte Inhalte aus externen Ressourcen in Chatnachrichten einfügen.

Alle von eingebetteten Inhalten verwendeten Cookies werden als Drittanbieter betrachtet, wenn die Website in einer angezeigt `<iframe>` wird. Wenn Remoteressourcen auf einer Seite auf Cookies basieren, die mit einer Anforderung `<img>` und `<script>` Tags, externen Schriftarten und personalisierten Inhalten gesendet werden, müssen Sie außerdem sicherstellen, dass diese für die websiteübergreifende Nutzung gekennzeichnet sind, z. `SameSite=None; Secure` B. oder dass ein Fallback vorhanden ist.

### <a name="authentication"></a>Authentifizierung

* Wenn Sie eine Authentifizierung für eingebettete Inhaltsseiten in Registerkarten benötigen, müssen Sie den webbasierten Authentifizierungsfluss verwenden.
* Ein webbasierter Authentifizierungsfluss kann auch für eine Konfigurationsseite, ein Aufgabenmodul oder eine Messaging-Erweiterung verwendet werden.
* Sie können einen webbasierten Authentifizierungsfluss für einen Unterhaltungsbot verwenden, den Sie benötigen, um ein Aufgabenmodul zu verwenden.

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser kein Cookie zu einer bereits authentifizierten Website hinzu, wenn der Link von einer externen Website abgeleitet ist. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Nutzung gekennzeichnet sind `SameSite=None; Secure` – oder sicherstellen, dass ein Fallback vorhanden ist.

### <a name="android-system-webview"></a>Android System WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps Webinhalte anzeigen können. Die neuen Einschränkungen werden zwar zum Standard, beginnend mit Chrome 80, werden jedoch nicht sofort in WebViews erzwungen. Sie werden in Zukunft angewendet. Zur Vorbereitung ermöglicht Android nativen Apps das direkte Festlegen von Cookies über die [CookeManager-API:](https://developer.android.com/reference/android/webkit/CookieManager)

* Für Cookies, die nur in einem Erstanbieterkontext benötigt werden, sollten Sie sie entsprechend `SameSite=Lax` `SameSite=Strict` deklarieren.
* Bei Cookies, die in einem Drittanbieterkontext benötigt werden, sollten Sie sicherstellen, dass sie als deklariert `SameSite=None; Secure` werden.

## <a name="see-also"></a>Siehe auch

* [SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)
* [SameSite-Cookie-Rezept](https://web.dev/samesite-cookie-recipes/)
* [Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Entwickler: Bereiten Sie sich auf "New SameSite=None" vor; Secure Cookie Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**Auswirkungen auf openId Verbinden**<br>
[Bevorstehende Änderungen des SameSite-Cookies in ASP.NET und ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
