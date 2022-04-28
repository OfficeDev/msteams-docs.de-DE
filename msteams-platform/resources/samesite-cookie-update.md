---
title: SameSite-Cookieattribut
author: laujan
description: Erfahren Sie mehr über Arten von Cookies, einschließlich SameSite-Cookies, deren Attribute, ihre Auswirkungen auf Teams Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen sowie deren Authentifizierung in Teams
keywords: Cookieattribute samesite
ms.topic: reference
ms.localizationpriority: medium
ms.author: lomeybur
ms.openlocfilehash: 1fbaf46da93a0d7c253f1f5d2ad6c9ae1764565a
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104490"
---
# <a name="samesite-cookie-attribute"></a>SameSite-Cookieattribut

Cookies sind Textzeichenfolgen, die von Websites gesendet und vom Webbrowser auf einem Computer gespeichert werden. Sie werden für die Authentifizierung und Personalisierung verwendet. Cookies werden beispielsweise verwendet, um zustandsbehaftete Informationen zurückzurufen, Benutzereinstellungen beizubehalten, Browseraktivitäten aufzuzeichnen und relevante Anzeigen anzuzeigen. Cookies sind immer mit einer bestimmten Domäne verknüpft und werden von verschiedenen Parteien installiert.

## <a name="types-of-cookies"></a>Arten von Cookies

Die Cookietypen und ihre entsprechenden Bereiche lauten wie folgt:

|Cookie|Bereich|
| ------ | ------ |
|First Party Cookie|Ein First Party Cookie wird von Websites erstellt, die ein Benutzer besucht. Es wird verwendet, um Daten, z. B. Einkaufswagenartikel, Anmeldeinformationen zu speichern. Beispielsweise Authentifizierungscookies und andere Analysen.|
|Second Party Cookie|Ein Second Party Cookie ist technisch identisch mit einem First Party Cookie. Der Unterschied besteht darin, dass Daten über eine Datenpartnerschaftsvereinbarung an eine zweite Partei weitergegeben werden. Beispielsweise [Microsoft Teams Analyse und Berichterstellung](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
|Cookie von Drittanbietern|Ein Drittanbieter-Cookie wird von einer anderen Domäne als der, die der Benutzer explizit besucht hat, installiert und hauptsächlich zum Nachverfolgen verwendet. Beispiel: **"Gefällt mir** "-Schaltflächen, Anzeigendienst und Live-Chats.|

## <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anforderungen

Vor der Einführung der SameSite-Einschränkungen wurden die Cookies im Browser gespeichert. Sie wurden an jede HTTP-Webanforderung angefügt und vom HTTP-Antwortheader an den `Set Cookie` Server gesendet. Mit dieser Methode wurden Sicherheitslücken eingeführt, z. B. siteübergreifende Anforderungsfälschung, die als CSRF-Angriffe bezeichnet werden. Die SameSite-Komponente verringerte die Belichtung durch ihre Implementierung und Verwaltung im SetCookie-Header.

## <a name="samesite-cookie-attribute-initial-release"></a>SameSite-Cookieattribut: erste Version

Google Chrome Version 51 hat die `SetCookie SameSite` Spezifikation als optionales Attribut eingeführt. Ab Build 17672 Windows 10 sameSite-Cookieunterstützung für den [MicrosoftEdge-Browser&nbsp;](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/) eingeführt.

Sie können das Hinzufügen des SameSite-Cookieattributs zur `SetCookie` Kopfzeile deaktivieren oder es mit einer der beiden Einstellungen **Lax** und **Strict** hinzufügen. Ein nicht implementiertes SameSite-Attribut wurde als Standardzustand betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookieattribut: Version 2020

Chrome 80, veröffentlicht im Februar 2020, führt neue Cookie-Werte ein und erzwingt standardmäßig Cookie-Richtlinien. Drei Werte werden an das aktualisierte SameSite-Attribut übergeben: **Strict**, **Lax** oder **None**. Wenn nicht angegeben, verwendet das SameSite-Attribut von Cookies standardmäßig den Wert `SameSite=Lax` .

SameSite-Cookieattribute lauten wie folgt:

|Setting | Durchsetzung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur in einem **Erstanbieterkontext** und mit HTTP GET-Anforderungen gesendet. SameSite-Cookies werden bei websiteübergreifenden Unteranforderungen, z. B. Aufrufen zum Laden von Bildern oder iFrames, einbehalten. Sie wurden gesendet, wenn ein Benutzer von einer externen Website aus zu der URL navigiert, z. B. durch Folgen eines Links.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Streng** |Der Browser sendet Cookies nur für Kontextanforderungen von Erstanbietern. Dies sind Anforderungen, die von der Website stammen, die das Cookie festgelegt hat. Wenn die Anforderung von einer anderen URL als der des aktuellen Speicherorts stammt, werden keine der mit dem `Strict` Attribut markierten Cookies gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl im Erstanbieterkontext als auch in Ursprungsübergreifenden Anfragen gesendet; Der Wert muss jedoch explizit festgelegt **`None`** werden, und alle Browseranforderungen **müssen dem HTTPS-Protokoll folgen** und das **`Secure`** Attribut enthalten, das eine verschlüsselte Verbindung erfordert. Cookies, die dieser Anforderung nicht entsprechen, werden **abgelehnt**. <br/>**Beide Attribute sind zusammen erforderlich**. Wenn  **`None`** die Angabe ohne **`Secure`**  oder wenn das HTTPS-Protokoll nicht verwendet wird, werden die Cookies von Drittanbietern abgelehnt.| Optional, wenn jedoch festgelegt, ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams Auswirkungen und Anpassungen

1. Aktivieren Sie die entsprechende SameSite-Einstellung für Ihre Cookies, und überprüfen Sie, ob Ihre Apps und Erweiterungen in Teams weiterhin funktionieren.
1. Wenn Ihre Apps oder Erweiterungen fehlschlagen, führen Sie die erforderlichen Korrekturen vor der Chrome 80-Version aus.
1. Interne Microsoft-Partner können dem folgenden Team beitreten, um weitere Informationen oder Hilfe zu diesem Problem zu erhalten: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>.

> [!NOTE]
> Sie müssen SameSite-Attribute festlegen, um die beabsichtigte Verwendung für Ihre Cookies widerzuspiegeln. Verlassen Sie sich nicht auf das Standardverhalten des Browsers. Weitere Informationen finden Sie unter [Developers: Get Ready for New SameSite=None; Secure Cookie Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen

* Teams Registerkarten verwenden`<iframes>`, um Inhalte einzubetten, die in einem Kontext der obersten Ebene oder des Erstanbieters angezeigt werden.
* Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Ähnlich wie bei einer Registerkarte wird innerhalb der aktuellen Seite ein modales Fenster geöffnet.
* Mithilfe von Nachrichtenerweiterungen können Sie angereicherte Inhalte aus externen Ressourcen in eine Chatnachricht einfügen.

Cookies, die von eingebetteten Inhalten verwendet werden, werden als Drittanbieter betrachtet, wenn die Website in einem `<iframe>`angezeigt wird. Wenn remote-Ressourcen auf einer Seite darauf angewiesen sind, dass Cookies mit einer Anforderung `<img>` und `<script>` Tags, externen Schriftarten und personalisierten Inhalten gesendet werden, müssen Sie sicherstellen, dass diese für die websiteübergreifende Nutzung gekennzeichnet sind, z `SameSite=None; Secure` . B. oder sicherstellen, dass ein Fallback vorhanden ist.

### <a name="authentication"></a>Authentifizierung

Sie müssen den webbasierten Authentifizierungsfluss für Folgendes verwenden:

* Eingebettete Inhaltsseiten in Registerkarten.
* Konfigurationsseite, Aufgabenmodul und Nachrichtenerweiterung.
* Unterhaltungs-Bot mit einem Aufgabenmodul.

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser kein Cookie zu einer bereits authentifizierten Website hinzu, wenn der Link von einer externen Website abgeleitet wird. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Nutzung `SameSite=None; Secure` gekennzeichnet sind, oder sicherstellen, dass ein Fallback vorhanden ist.

## <a name="android-system-webview"></a>Android System WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps den Webinhalt anzeigen können. Während die neuen Einschränkungen standardmäßig sind, werden sie ab Chrome 80 nicht sofort in WebViews erzwungen. Sie werden in Zukunft angewendet. Zur Vorbereitung ermöglicht Android nativen Apps, Cookies direkt über die [CookieManager-API](https://developer.android.com/reference/android/webkit/CookieManager) festzulegen.

> [!NOTE]
>
> * Sie müssen Cookies von Erstanbietern als `SameSite=Lax` oder `SameSite=Strict`gegebenenfalls deklarieren.
> * Sie müssen Cookies von Drittanbietern als `SameSite=None; Secure`deklarieren.

## <a name="see-also"></a>Siehe auch

* [SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)
* [SameSite Cookie Rezepte](https://web.dev/samesite-cookie-recipes/)
* [Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)
* [Entwickler: Machen Sie sich bereit für neue sichere Cookie-Einstellungen mit SameSite=None](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)
* [Bevorstehende Änderungen an SameSite-Cookies in ASP.NET und ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
* [HTTP-Cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies)
