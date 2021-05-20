---
title: Microsoft Teams und das SameSite-Cookieattribut (Update 2020)
author: laujan
description: beschreibt die Attribute des SameSite-Cookies
keywords: Cookie-Attribute auf derselben Seite
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: cf28a28050d50b2b6b2601a3231cdad30211ab2c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566712"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams und das SameSite-Cookieattribut (Update 2020)

## <a name="cookies-in-brief"></a>Cookies in Kürze

 Cookies sind Textzeichenfolgen, die von Websites gesendet und vom Webbrowser auf einem Computer gespeichert werden. Sie werden in der Regel für die Authentifizierung und Personalisierung verwendet, z. B. das Abrufen zustandsbehafteter Informationen, das Beibehalten von Benutzereinstellungen, das Aufzeichnen von Browseraktivitäten und das Anzeigen relevanter Anzeigen. Cookies sind immer mit einer bestimmten Domain verknüpft und können von verschiedenen Parteien installiert werden. Sie sind wie folgt kategorisiert:

 |Cookie|Bereich|
 | ------ | ------ |
 |**First-Party-Cookie**|Ein First-Party-Cookie wird von Websites erstellt, die ein Benutzer besucht, und wird verwendet, um Daten wie Warenkorb-Elemente, Anmeldeinformationen zu speichern. Zum Beispiel Authentifizierungscookies und andere Analysen.|
 |**Zweitparteien-Cookie**|Ein Cookies für Drittanbieter ist technisch dasselbe wie ein First-Party-Cookie. Der Unterschied besteht darin, dass Daten über eine Datenpartnerschaftsvereinbarung mit einer zweiten Partei geteilt werden. Beispielsweise [Microsoft Teams Analysen und Berichte](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference). |
 |**Drittanbieter-Cookie**|Ein Drittanbieter-Cookie wird von einer anderen Domäne als der vom Benutzer explizit besuchten installiert und hauptsächlich für die Nachverfolgung verwendet. Beispiel: "Gefällt mir"-Schaltflächen, Anzeigenbereitstellung und Live-Chats.|

### <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anfragen

Vor der Einführung von SameSite-Einschränkungen, wenn Cookies im Browser gespeichert wurden, wurden sie an *jede* HTTP-Webanforderung angehängt und vom Set-Cookie HTTP-Antwortheader an den Server gesendet. Diese Leistung hatte das Potenzial, Sicherheitslücken wie CROSS-Site Request Forgery (CSRF)-Angriffe einzuführen. *Siehe* [HTTP-Cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies). Die SameSite-Komponente hat diese Risikoposition durch ihre Implementierung und Verwaltung im SetCookie-Header verringert.

### <a name="samesite-attribute-initial-release"></a>SameSite-Attribut: erste Version

Google Chrome Version 51 führte die SetCookie SameSite-Spezifikation als *optionales* Attribut ein. Ab Build 17672 Windows 10 SameSite-Cookie-Unterstützung für den [Microsoft Edge-Browser](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/)eingeführt.

Entwickler können das Hinzufügen des SameSite-Cookieattributs zum SetCookie-Header deaktivieren oder es mit einer von zwei Einstellungen, *Lax* und *Strict*, hinzufügen. Ein nicht implementiertes SameSite-Attribut wurde als Standardstatus betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookieattribut: 2020-Version

Chrome 80, das im Februar 2020 veröffentlicht werden soll, führt neue Cookie-Werte ein und schreibt standardmäßig Cookie-Richtlinien vor. Drei Werte können an das aktualisierte SameSite-Attribut übergeben werden: *Strict*, *Lax* oder *None*. Cookies, die das SameSite-Attribut nicht angeben, werden standardmäßig auf `SameSite=Lax` .

|Einstellung | Durchsetzung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur in einem Erstparteienkontext und mit HTTP *GET-Anforderungen* gesendet. SameSite-Cookies werden bei websiteübergreifenden Unteranforderungen zurückgehalten, z. B. bei Aufrufen zum Laden von Bildern oder iframes, werden jedoch gesendet, wenn ein Benutzer von einer externen Website zur URL navigiert, z. B. durch Das Nachfolgen eines Links.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Streng** |Der Browser sendet Cookies nur für Kontextanfragen von Erstparteien (Anfragen, die von der Website stammen, die das Cookie gesetzt hat). Wenn die Anforderung von einer anderen URL als der des aktuellen Speicherorts stammt, wird keines der mit dem Attribut markierten Cookies `Strict` gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl im Erstparteikontext als auch in ursprungsübergreifenden Anfragen gesendet; Der Wert muss jedoch explizit festgelegt werden, **`None`** und alle Browseranforderungen **müssen dem HTTPS-Protokoll folgen** und das Attribut enthalten, das eine **`Secure`** verschlüsselte Verbindung erfordert. Cookies, die dieser Anforderung nicht entsprechen, werden **abgelehnt.** <br/>**Beide Attribute sind zusammen erforderlich.** Wenn nur **`None`** ohne oder wenn das **`Secure`**  HTTPS-Protokoll nicht verwendet wird, wird das Drittanbieter-Cookie abgelehnt.| Optional, aber, wenn festgelegt, ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="teams-implications-and-adjustments"></a>Teams Implikationen und Anpassungen

1. Aktivieren Sie die entsprechende SameSite-Einstellung für Ihre Cookies und überprüfen Sie, ob Ihre Apps und Erweiterungen weiterhin in Teams funktionieren.
1. Wenn Ihre Apps oder Erweiterungen fehlschlagen, treffen Sie die erforderlichen Korrekturen vor der Chrome 80-Version.
1. Interne Microsoft-Partner können dem folgenden Team beitreten, wenn sie weitere Informationen benötigen oder Hilfe zu diesem Problem benötigen: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47> .

> [!NOTE]
> Für bewährte Verfahren wird empfohlen, dass Sie immer SameSite-Attribute festlegen, um die beabsichtigte Verwendung für Ihre Cookies widerzuspiegeln. Verlassen Sie sich nicht auf das Standardmäßige Browserverhalten. Weitere Informationen finden Sie unter [Entwickler: Bereit für New SameSite=None; Secure Cookie Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen

* Teams Registerkarten zum Einbetten von Inhalten verwenden, die in einem Kontext der `<iframes>` obersten Ebene oder der ersten Instanz angezeigt werden.
* Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Ähnlich wie auf einer Registerkarte wird ein modales Fenster innerhalb der aktuellen Seite geöffnet.
* Mit Nachrichtenerweiterungen können Sie angereicherte Inhalte aus externen Ressourcen in Chatnachrichten einfügen.

Alle Cookies, die von eingebetteten Inhalten verwendet werden, werden als Drittanbieter betrachtet, wenn die Website in einem angezeigt `<iframe>` wird. Wenn Remoteressourcen auf einer Seite darauf angewiesen sind, dass Cookies mit einer Anforderung `<img>` und `<script>` Tags, externen Schriftarten und personalisierten Inhalten gesendet werden, müssen Sie außerdem sicherstellen, dass diese für die websiteübergreifende Nutzung markiert sind, z. `SameSite=None; Secure` B. oder stellen Sie sicher, dass ein Fallback vorhanden ist.

### <a name="authentication"></a>Authentifizierung

* Wenn Sie eine Authentifizierung für eingebettete Inhaltsseiten in Registerkarten benötigen, müssen Sie den webbasierten Authentifizierungsfluss verwenden.
* Ein webbasierter Authentifizierungsfluss kann auch für eine Konfigurationsseite, ein Taskmodul oder eine Messagingerweiterung verwendet werden.
* Sie können einen webbasierten Authentifizierungsfluss für einen Konversationsbot verwenden, den Sie benötigen, um ein Aufgabenmodul zu verwenden.

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser einer bereits authentifizierten Website kein Cookie hinzu, wenn der Link von einer externen Website stammt. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Nutzung markiert sind `SameSite=None; Secure` – oder sicherstellen, dass ein Fallback vorhanden ist.

### <a name="android-system-webview"></a>Android System WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps Webinhalte anzeigen können. Obwohl die neuen Einschränkungen standardmäßig gelten, beginnend mit Chrome 80, werden sie in WebViews nicht sofort erzwungen. Sie werden in Zukunft angewendet. Zur Vorbereitung ermöglicht Android nativen Apps das direkte Setzen von Cookies über die [CookeManager-API:](https://developer.android.com/reference/android/webkit/CookieManager)

* Für Cookies, die nur in einem Erstparteienkontext benötigt werden, sollten Sie sie `SameSite=Lax` als oder als , entsprechend deklarieren. `SameSite=Strict`
* Bei Cookies, die in einem Drittanbieterkontext benötigt werden, sollten Sie sicherstellen, dass sie als deklariert `SameSite=None; Secure` werden.

## <a name="see-also"></a>Siehe auch

* [SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)

* [SameSite-Cookie-Rezepte](https://web.dev/samesite-cookie-recipes/)

* [Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)

* [Entwickler: Machen Sie sich bereit für New SameSite=None; Sichere Cookie-Einstellungen](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**OpenId Verbinden Auswirkungen**<br>
[Kommende Änderungen von SameSite-Cookies in ASP.NET und ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
