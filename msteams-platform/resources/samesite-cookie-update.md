---
title: SameSite-Cookieattribut
author: laujan
description: Erfahren Sie mehr über verschiedene Arten von Cookies, einschließlich SameSite-Cookies, deren Attribute, ihre Auswirkungen auf Microsoft Teams-Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen sowie deren Authentifizierung in Microsoft Teams.
keywords: Cookieattribute samesite
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: f93ee29198400a0cabd4512d9abb4de80cebb9da
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756989"
---
# <a name="samesite-cookie-attribute"></a>SameSite-Cookieattribut

Cookies sind Textzeichenfolgen, die von Websites gesendet und vom Webbrowser auf einem Computer gespeichert werden. Sie werden für die Authentifizierung und Personalisierung verwendet. Cookies werden beispielsweise verwendet, um Statusinformationen abzurufen, Benutzereinstellungen beizubehalten, Browseraktivitäten aufzuzeichnen und relevante Werbeanzeigen einzublenden. Cookies sind immer mit einer bestimmten Domäne verknüpft und werden von verschiedenen Parteien installiert.

## <a name="types-of-cookies"></a>Arten von Cookies

Arten von Cookies und entsprechende Anwendungsbereiche:

|Cookie|Bereich|
| ------ | ------ |
|Cookies von Erstanbietern|Ein Erstanbieter-Cookie wird von Websites erstellt, die ein Benutzer besucht. Es wird verwendet, um Daten, z. B. Einkaufswagenartikel, Anmeldeinformationen zu speichern. Dazu gehören beispielsweise Authentifizierungscookies und andere Analyse-Cookies.|
|Zweitparteien-Cookies|Ein Zweitparteien-Cookie ist technisch gesehen dasselbe wie ein Erstanbieter-Cookie. Der Unterschied besteht darin, dass Daten auf der Grundlage einer Datenpartnerschaftsvereinbarung an eine zweite Partei übermittelt werden. Beispielsweise für [Microsoft Teams–Analysen und -Berichte](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
|Cookies von Drittanbietern|Ein Drittanbieter-Cookie wird von einer anderen Domäne als der, die der Benutzer explizit besucht hat, installiert und für die Nachverfolgung verwendet. Beispiele: **Gefällt mir**-Schaltflächen, Werbeanzeigen und Live-Chats.|

## <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anforderungen

Vor der Einführung der SameSite-Einschränkungen wurden die Cookies im Browser gespeichert. Sie wurden an jede HTTP-Webanforderung angefügt und über den `Set Cookie`-HTTP-Antwortheader an den Server gesendet. Dadurch wurden Sicherheitslücken eingeführt, z. B. siteübergreifende Anforderungsfälschungen, die als CSRF-Angriffe bezeichnet werden. Durch die SameSite-Komponente wurde dieses Risiko verringert dank deren Implementierung und Verwaltung im SetCookie-Header.

## <a name="samesite-cookie-attribute-initial-release"></a>SameSite-Cookieattribut: erste Veröffentlichung

Die `SetCookie SameSite`-Spezifikation wurde als optionales Attribut in Google Chrome Version 51 eingeführt. Ab Build 17672 bietet Windows 10 sameSite-Cookieunterstützung für den [Microsoft&nbsp;Edge-Browser](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/).

Sie können das Hinzufügen des SameSite-Cookieattributs zum `SetCookie`-Header deaktivieren oder es mit einer von zwei Einstellungen hinzufügen, **Lax** und **Strict**. Ein nicht implementiertes SameSite-Attribut wurde als Standardzustand betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookieattribut: Version 2020

In Chrome 80, veröffentlicht im Februar 2020, wurden neue Cookie-Werte eingeführt und es werden standardmäßig Cookie-Richtlinien erzwungen. Drei Werte werden im aktualisierten SameSite-Attribut übergeben: **Strict**, **Lax** oder **None**. Wenn nicht angegeben, verwendet das SameSite-Attribut von Cookies standardmäßig den Wert `SameSite=Lax`.

SameSite-Cookieattribute:

|Einstellung | Erzwingung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur in einem **Erstanbieterkontext** und mit HTTP GET-Anforderungen gesendet. SameSite-Cookies werden bei untergeordneten websiteübergreifenden Anforderungen, z. B. Aufrufen zum Laden von Bildern oder iFrames, einbehalten. Sie werden gesendet, wenn ein Benutzer von einer externen Website aus zu der URL navigiert, z. B. durch Folgen eines Links.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Streng** |Der Browser sendet Cookies nur für Erstanbieter-Kontextanforderungen. Dies sind Anforderungen, die von der Website stammen, von der das Cookie abgelegt wurde. Wenn die Anforderung von einer anderen URL als jener der aktuellen Site stammt, werden keine der mit dem `Strict`-Attribut getaggten Cookies gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl im Erstanbieterkontext als auch in Ursprungsübergreifenden Anfragen gesendet; Der Wert muss jedoch explizit festgelegt **`None`** werden, und alle Browseranforderungen **müssen dem HTTPS-Protokoll folgen** und das **`Secure`** Attribut enthalten, das eine verschlüsselte Verbindung erfordert. Cookies, die dieser Anforderung nicht entsprechen, werden **abgelehnt**. <br/>**Beide Attribute sind zusammen erforderlich**. Wenn  **`None`** die Angabe ohne **`Secure`**  oder wenn das HTTPS-Protokoll nicht verwendet wird, werden die Cookies von Drittanbietern abgelehnt.| Optional, aber falls festgelegt, ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Auswirkungen und Anpassungen in Microsoft Teams

1. Aktivieren Sie die entsprechende SameSite-Einstellung für Ihre Cookies, und überprüfen Sie dann, ob Ihre Apps und Erweiterungen in Microsoft Teams weiterhin funktionieren.
1. Wenn bei Ihren Apps oder Erweiterungen Fehler auftreten, nehmen Sie die erforderlichen Korrekturen vor der Chrome 80-Version vor.
1. Interne Microsoft-Partner können dem folgenden Team beitreten, um weitere Informationen oder Hilfe zu diesem Problem zu erhalten: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>.

> [!NOTE]
> Sie müssen SameSite-Attribute entsprechend der beabsichtigten Verwendung Ihrer Cookies festlegen. Verlassen Sie sich nicht auf das Standardverhalten von Browsern. Weitere Informationen finden Sie unter [Entwickler: Machen Sie sich bereit für neue sichere Cookie-Einstellungen mit SameSite=None](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen

* In Microsoft Teams-Registerkarten werden `<iframes>` verwendet, um Inhalte einzubetten, die in einem Kontext der obersten Ebene oder des Erstanbieters angezeigt werden.
* Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Ähnlich wie bei einer Registerkarte wird innerhalb der aktuellen Seite ein modales Fenster geöffnet.
* Mithilfe von Nachrichtenerweiterungen können Sie vielfältige Inhalte aus externen Ressourcen in eine Chatnachricht einfügen.

Cookies, die von eingebetteten Inhalten verwendet werden, werden als Drittanbieter-Cookies betrachtet, wenn die Website in einem `<iframe>` angezeigt wird. Wenn Remote-Ressourcen auf einer Seite darauf angewiesen sind, dass Cookies mit einer `<img>`-Anforderung und `<script>`-Tags, externen Schriftarten und personalisierten Inhalten gesendet werden, müssen Sie sicherstellen, dass diese für die websiteübergreifende Nutzung gekennzeichnet sind, z. B. `SameSite=None; Secure`, oder sicherstellen, dass ein Fallback vorhanden ist.

### <a name="authentication"></a>Authentifizierung

Sie müssen den webbasierten Authentifizierungsablauf für Folgendes verwenden:

* Eingebettete Inhaltsseiten in Registerkarten
* Konfigurationsseiten, Aufgabenmodule und Nachrichtenerweiterungen
* Unterhaltungs-Bots mit einem Aufgabenmodul

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser einer bereits authentifizierten Website kein Cookie hinzu, wenn der Link von einer externen Website abgeleitet wird. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Nutzung gekennzeichnet sind (`SameSite=None; Secure`) oder dass ein Fallback vorhanden ist.

## <a name="android-system-webview"></a>Android System WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps Webinhalte anzeigen können. Obwohl die neuen Einschränkungen standardmäßig sind, werden sie ab Chrome 80 nicht sofort in WebViews erzwungen. Sie werden in Zukunft angewendet. Zur Vorbereitung ermöglicht Android nativen Apps, Cookies direkt über die [CookieManager-API](https://developer.android.com/reference/android/webkit/CookieManager) festzulegen.

> [!NOTE]
>
> * Sie müssen Cookies von Erstanbietern als `SameSite=Lax` oder `SameSite=Strict` deklarieren.
> * Sie müssen Cookies von Drittanbietern als `SameSite=None; Secure`deklarieren.

## <a name="see-also"></a>Siehe auch

* [SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)
* [SameSite Cookie-Rezepte](https://web.dev/samesite-cookie-recipes/)
* [Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Entwickler: Machen Sie sich bereit für neue sichere Cookie-Einstellungen mit SameSite=None](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)
* [Bevorstehende Änderungen an SameSite-Cookies in ASP.NET und ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
* [HTTP-Cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies)
