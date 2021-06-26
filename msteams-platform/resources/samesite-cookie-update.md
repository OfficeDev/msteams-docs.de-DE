---
title: SameSite-Cookieattribut
author: laujan
description: beschreibt die Attribute des SameSite-Cookies
keywords: Cookieattribute samesite
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 34674ab58cc9808525d315cea3db464ddf11b4f9
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140565"
---
# <a name="samesite-cookie-attribute"></a>SameSite-Cookieattribut 

Cookies sind Textzeichenfolgen, die von Websites gesendet und vom Webbrowser auf einem Computer gespeichert werden. Sie werden für die Authentifizierung und Personalisierung verwendet. Cookies werden beispielsweise verwendet, um zustandsbehaftete Informationen zurückzurufen, Benutzereinstellungen beizubehalten, Browseraktivitäten zu aufzeichnen und relevante Anzeigen anzuzeigen. Cookies sind immer mit einer bestimmten Domäne verknüpft und werden von verschiedenen Parteien installiert. 

## <a name="types-of-cookies"></a>Arten von Cookies

Die Cookietypen und ihre entsprechenden Bereiche sind wie folgt:

|Cookie|Umfang|
| ------ | ------ |
|Cookies von Erstanbietern|Ein Erstanbieter-Cookie wird von Websites erstellt, die ein Benutzer besucht. Es wird verwendet, um Daten wie Einkaufswagenelemente und Anmeldeinformationen zu speichern. Beispielsweise Authentifizierungscookies und andere Analysen.|
|Cookies von Drittanbietern|Ein Drittanbietercookie ist technisch identisch mit einem Erstanbietercookie. Der Unterschied besteht darin, dass Daten mit einer zweiten Partei über einen Datenpartnerschaftsvertrag geteilt werden. Beispielsweise [Microsoft Teams Analyse und Berichterstellung.](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference) |
|Drittanbietercookie|Ein Drittanbietercookie wird von einer anderen Domäne als der Domäne installiert, die der Benutzer explizit besucht hat, und wird hauptsächlich für die Nachverfolgung verwendet. Beispielsweise **Wie** Schaltflächen, Anzeigendienst und Live-Chats.|

## <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anforderungen

Vor der Einführung von SameSite-Einschränkungen wurden die Cookies im Browser gespeichert. Sie wurden an jede HTTP-Webanforderung angefügt und vom `Set Cookie` HTTP-Antwortheader an den Server gesendet. Mit dieser Methode wurden Sicherheitsrisiken eingeführt, z. B. Cross Site Request Forgery, die als CSRF-Angriffe bezeichnet werden. Die SameSite-Komponente reduzierte die Gefährdung durch ihre Implementierung und Verwaltung im SetCookie-Header.

## <a name="samesite-cookie-attribute-initial-release"></a>SameSite-Cookieattribut: erste Version

In Google Chrome, Version 51, wurde die `SetCookie SameSite` Spezifikation als optionales Attribut eingeführt. Ab Build 17672 wurde Windows 10 die SameSite-Cookieunterstützung für den [Microsoft Edge Browser](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/)eingeführt.

Sie können das Hinzufügen des SameSite-Cookieattributs zum Header deaktivieren `SetCookie` oder es mit einer der beiden Einstellungen **Lax** und **Strict** hinzufügen. Ein nicht implementiertes SameSite-Attribut wurde als Standardzustand betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookieattribut: Version 2020

Chrome 80, veröffentlicht im Februar 2020, führt neue Cookiewerte ein und erlegt standardmäßig Cookierichtlinien auf. Drei Werte werden an das aktualisierte SameSite-Attribut übergeben: **Strict**, **Lax** oder **None**. Wenn nicht angegeben, verwendet das Cookies SameSite-Attribut standardmäßig den `SameSite=Lax` Wert.    
 
SameSite-Cookieattribute sind wie folgt:

|Setting | Durchsetzung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur in einem **Erstanbieterkontext** und mit HTTP GET-Anforderungen gesendet. SameSite-Cookies werden bei websiteübergreifenden Unteranforderungen, z. B. Aufrufen zum Laden von Bildern oder iframes, beibehalten. Sie werden gesendet, wenn ein Benutzer von einer externen Website zu der URL navigiert, z. B. durch Folgen eines Links.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Streng** |Der Browser sendet Cookies nur für Erstanbieterkontextanforderungen. Dies sind Anforderungen, die von der Website stammen, die das Cookie festgelegt hat. Wenn die Anforderung von einer anderen URL als der des aktuellen Speicherorts stammt, werden keine der mit dem Attribut markierten Cookies `Strict` gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl im Erstanbieterkontext als auch in ursprungsübergreifenden Anforderungen gesendet. Der Wert muss jedoch explizit festgelegt werden, **`None`** und alle Browseranforderungen **müssen dem HTTPS-Protokoll folgen** und das Attribut **`Secure`** enthalten, das eine verschlüsselte Verbindung erfordert. Cookies, die dieser Anforderung nicht entsprechen, werden **abgelehnt.** <br/>**Beide Attribute sind zusammen erforderlich.** Wenn  **`None`** ohne **`Secure`**  oder wenn das HTTPS-Protokoll nicht verwendet wird, werden die Cookies von Drittanbietern abgelehnt.| Optional, aber wenn festgelegt, ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams Auswirkungen und Anpassungen

1. Aktivieren Sie die relevante SameSite-Einstellung für Ihre Cookies, und überprüfen Sie, ob Ihre Apps und Erweiterungen weiterhin in Teams funktionieren.
1. Wenn Ihre Apps oder Erweiterungen fehlschlagen, nehmen Sie die erforderlichen Korrekturen vor der Chrome 80-Version vor.
1. Interne Microsoft-Partner können dem folgenden Team beitreten, um weitere Informationen oder Hilfe zu diesem Problem zu erhalten: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47> .

> [!NOTE]
> Sie müssen SameSite-Attribute festlegen, um die beabsichtigte Verwendung für Ihre Cookies widerzuspiegeln. Verlassen Sie sich nicht auf das Standardverhalten des Browsers. Weitere Informationen finden Sie unter ["Entwickler: Vorbereiten auf die neue SameSite=None". Secure Cookie Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-messaging-extensions"></a>Registerkarten, Aufgabenmodule und Messaging-Erweiterungen

* Teams Registerkarten werden `<iframes>` zum Einbetten von Inhalten verwendet, die in einem Kontext der obersten Ebene oder des Erstanbieters angezeigt werden.
* Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Erlebnissen in Ihrer Teams-Anwendung. Ähnlich wie bei einer Registerkarte wird ein modales Fenster auf der aktuellen Seite geöffnet.
* Messaging-Erweiterungen ermöglichen es Ihnen, anreicherte Inhalte aus externen Ressourcen in eine Chatnachricht einzufügen.

Alle von eingebetteten Inhalten verwendeten Cookies werden als Drittanbieter betrachtet, wenn die Website in einer angezeigt `<iframe>` wird. Wenn Remoteressourcen auf einer Seite auf Cookies basieren, die mit einer Anforderung `<img>` und `<script>` Tags, externen Schriftarten und personalisierten Inhalten gesendet werden, müssen Sie außerdem sicherstellen, dass diese für die websiteübergreifende Nutzung gekennzeichnet sind, z. `SameSite=None; Secure` B. oder dass ein Fallback vorhanden ist.

### <a name="authentication"></a>Authentifizierung

Sie müssen den webbasierten Authentifizierungsfluss für Folgendes verwenden:

* Eingebettete Inhaltsseiten in Registerkarten.
* Konfigurationsseite, Aufgabenmodul und Messaging-Erweiterung.
* Unterhaltungsbot mit einem Aufgabenmodul.

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser kein Cookie zu einer bereits authentifizierten Website hinzu, wenn der Link von einer externen Website abgeleitet ist. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Nutzung gekennzeichnet `SameSite=None; Secure` sind, oder dass ein Fallback vorhanden ist.

## <a name="android-system-webview"></a>Android System WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps den Webinhalt anzeigen können. Die neuen Einschränkungen sind zwar Standard, beginnend mit Chrome 80, werden jedoch nicht sofort in WebViews erzwungen. Sie werden in Zukunft angewendet. Zur Vorbereitung ermöglicht Android nativen Apps das direkte Festlegen von Cookies über die [CookieManager-API.](https://developer.android.com/reference/android/webkit/CookieManager)

> [!NOTE]     
> * Sie müssen Cookies von Erstanbietern entsprechend `SameSite=Lax` `SameSite=Strict` deklarieren.      
> * Sie müssen Cookies von Drittanbietern als `SameSite=None; Secure` deklarieren.   

## <a name="see-also"></a>Siehe auch

* [SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)
* [SameSite-Cookie-Rezept](https://web.dev/samesite-cookie-recipes/)
* [Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Entwickler: Bereiten Sie sich auf "New SameSite=None" vor; Secure Cookie Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)
* [Bevorstehende Änderungen des SameSite-Cookies in ASP.NET und ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
* [HTTP-Cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies)
