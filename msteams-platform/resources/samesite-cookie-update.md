---
title: Microsoft Teams und das SameSite-Cookieattribut (Update 2020)
author: laujan
description: beschreibt die Attribute des SameSite-Cookies
keywords: Cookieattribute samesite
ms.topic: reference
localization_priority: Normal
ms.author: lomeybur
ms.openlocfilehash: 5713c7aae0461e577627ae7296f0a58a25ba062f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020436"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams und das SameSite-Cookieattribut (Update 2020)

## <a name="cookies-in-brief"></a>Cookies in Kürze

 Cookies sind Textzeichenfolgen, die von Websites gesendet und vom Webbrowser auf einem Computer gespeichert werden. Sie werden in der Regel für die Authentifizierung und Personalisierung verwendet, z. B. zum Abrufen zustandsrelevanter Informationen, zum Beibehalten von Benutzereinstellungen, zum Aufzeichnen von Browseraktivitäten und zum Anzeigen relevanter Anzeigen. Cookies sind immer mit einer bestimmten Domäne verknüpft und können von verschiedenen Parteien installiert werden. Sie sind wie folgt kategorisiert:

 |Cookie|Bereich|
 | ------ | ------ |
 |**First-Party-Cookie**|Ein First-Party-Cookie wird von Websites erstellt, die ein Benutzer besucht und zum Speichern von Daten wie Einkaufswagenelementen, Anmeldeinformationen (z. B. Authentifizierungscookies) und anderen Analysen verwendet wird.|
 |**Drittanbietercookie**|Ein Drittanbietercookie ist technisch identisch mit einem Cookie eines ersten Drittanbieters. Der Unterschied besteht in der Freigabe von Daten an einen Zweiten über einen Datenpartnerschaftsvertrag (z. B. [Microsoft Teams-Analysen und -Berichte).](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference) |
 |**Drittanbietercookie**|Ein Drittanbietercookie wird von einer anderen Domäne als der Domäne installiert, die der Benutzer explizit besucht hat, und wird hauptsächlich für die Nachverfolgung (z. B. "Gefällt mir"-Schaltflächen), anzeigende Dienste und Livechats verwendet.|

### <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anforderungen

Vor der Einführung von SameSite-Einschränkungen, als Cookies im  Browser gespeichert wurden, wurden sie an jede HTTP-Webanforderung angefügt und vom Set-Cookie HTTP-Antwortheader an den Server gesendet. Vorhersehbar war, dass diese Leistung das Potenzial hatte, Sicherheitsrisiken wie csrF-Angriffe (Cross-Site Request Forgery) einzuführen. *Siehe* [HTTP-Cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies). Die SameSite-Komponente hat diese Gefährdung durch ihre Implementierung und Verwaltung im SetCookie-Header verringert.

### <a name="samesite-attribute-initial-release"></a>SameSite-Attribut: erstveröffentlichung

In Google Chrome, Version 51, wurde die SetCookie SameSite-Spezifikation als *optionales Attribut* eingeführt. Ab Build 17672 hat Windows 10 die Unterstützung von SameSite-Cookies für den [Microsoft Edge-Browser eingeführt.](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/)

Entwickler könnten das Hinzufügen des SameSite-Cookieattributs zum SetCookie-Header deaktivieren oder es mit einer der beiden Einstellungen *Lax* und *Strict hinzufügen.* Ein nicht implementiertes SameSite-Attribut wurde als Standardzustand betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookieattribut: 2020-Version

Chrome 80, das im Februar 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und setzt standardmäßig Cookierichtlinien auf. Drei Werte können an das aktualisierte SameSite-Attribut übergeben werden: *Strict*, *Lax* oder *None*. Cookies, die das SameSite-Attribut nicht angeben, werden standardmäßig auf `SameSite=Lax` festgelegt.

|Einstellung | Erzwingung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur in einem Kontext von Erstpartei und mit HTTP *GET-Anforderungen* gesendet. SameSite-Cookies werden für websiteübergreifende Unteranforderungen, z. B. Aufrufe zum Laden von Bildern oder iframes, einbehalten, aber gesendet, wenn ein Benutzer von einer externen Website zur URL navigiert, z. B. über einen Link.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Strict** |Der Browser sendet nur Cookies für Kontextanforderungen von Drittanbietern (Anforderungen, die von der Website stammen, von der das Cookie festgelegt wurde). Wenn die Anforderung von einer anderen URL als der des aktuellen Speicherorts stammt, wird keines der mit dem Attribut markierten Cookies `Strict` gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl in kontextbezogenen als auch in originübergreifenden Anforderungen gesendet. Der Wert muss jedoch explizit auf festgelegt werden, und alle Browseranforderungen müssen dem HTTPS-Protokoll folgen und das Attribut enthalten, das **`None`** eine  **`Secure`** verschlüsselte Verbindung erfordert. Cookies, die dieser Anforderung nicht gerecht werden, **werden abgelehnt.** <br/>**Beide Attribute sind zusammen erforderlich.** Wenn nur ohne oder wenn das HTTPS-Protokoll nicht verwendet wird, wird das **`None`** **`Secure`**  Drittanbietercookie abgelehnt.| Optional, aber wenn festgelegt, ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="handling-incompatible-clients"></a>Behandeln inkompatibler Clients

> [!IMPORTANT]
> Wird `SameSite=None`  derzeit nicht vom [**Teams-Desktopclient oder**](/aspnet/core/security/samesite?view=aspnetcore-3.1#test-with-electron&preserve-view=true) älteren Versionen von Chrome oder Safari unterstützt. **Weitere Informationen finden** [Sie unter Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients).
>Es gibt jedoch zwei **Problemumgehungslösungen:**
>
>1. Überprüfen Sie den User-Agent, um die richtige SameSite-Eigenschaft zur Verfügung zu stellen. Sie können die Benutzer-Agent-Check-in-C# [**und**](https://web.dev/samesite-cookie-recipes/)Node.js. [](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
>2. Legen Sie Ihre Cookieattribute sowohl mithilfe der neuen als auch der alten Modelle. *Weitere Informationen finden Sie* [unter Behandeln inkompatibler Clients](https://web.dev/samesite-cookie-recipes/#handling-incompatible-clients)<br><br>
>**Wenn Ihre App im Teams-Desktopclient ausgeführt wird und Sie das SameSite-Attribut auf festlegen, funktioniert Ihre `SameSite=None` App nicht wie erwartet.**

Mit beiden Vorgehensweisen wird sichergestellt, dass Ihre Anwendung weiterhin ordnungsgemäß funktioniert, wenn der Teams-Desktopclient auf eine kompatible Version von `SameSite=None`   Chromium aktualisiert wird.

## <a name="teams-implications-and-adjustments"></a>Auswirkungen und Anpassungen von Teams

>[!WARNING]
>**Anwendungen, die im Teams-Desktopclient ausgeführt werden, sind mit dem Attribut nicht kompatibel und funktionieren `SameSite=None`  nicht wie erwartet.** Weitere Informationen finden Sie unter **Problemumgehungslösungen** oben.

1. Aktivieren Sie die entsprechende SameSite-Einstellung für Ihre Cookies, und überprüfen Sie, ob Ihre Apps und Erweiterungen weiterhin in Teams funktionieren.
1. Wenn Ihre Apps oder Erweiterungen fehlschlagen, führen Sie die erforderlichen Korrekturen vor der Chrome 80-Version aus.
1. Interne Microsoft-Partner können dem folgenden Team beitreten, wenn sie weitere Informationen oder Hilfe bei diesem Problem benötigen: <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47> .

> [!NOTE]
> Als bewährte Methode wird empfohlen, dass Sie sameSite-Attribute immer so festlegen, dass sie die beabsichtigte Verwendung für Ihre Cookies widerspiegeln – verlassen Sie sich nicht auf das Standardverhalten des Browsers. *Weitere* [Informationen finden Sie unter Developers: Get Ready for New SameSite=None; Einstellungen für sicheres Cookie](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Registerkarten, Aufgabenmodule und Nachrichtenerweiterungen

* Registerkarten von Teams werden zum Einbetten von Inhalten verwendet, die in einem Kontext der obersten Ebene oder der `<iframes>` ersten Ebene angezeigt werden.
* Aufgabenmodule ermöglichen Ihnen das Erstellen von modalen Popup-Oberflächen in Ihrer Teams-Anwendung. Ähnlich wie auf einer Registerkarte wird ein modales Fenster auf der aktuellen Seite geöffnet.
* Nachrichtenerweiterungen ermöglichen ihnen das Einfügen von bereicherten Inhalten in Chatnachrichten aus externen Ressourcen.

Alle von eingebetteten Inhalten verwendeten Cookies werden als Drittanbieter betrachtet, wenn die Website in einem angezeigt `<iframe>` wird. Wenn Remoteressourcen auf einer Seite darüber hinaus darauf vertrauen, dass Cookies mit einer Anforderung gesendet werden (z. B. Tags, externe Schriftarten und personalisierte Inhalte), müssen Sie sicherstellen, dass diese für die websiteübergreifende Verwendung gekennzeichnet sind – oder sicherstellen, dass ein Fallback vorhanden `<img>` `<script>` `SameSite=None; Secure` ist.

### <a name="authentication"></a>Authentifizierung

* Wenn Sie die Authentifizierung für eingebettete Inhaltsseiten in Registerkarten benötigen, müssen Sie den webbasierten Authentifizierungsfluss verwenden.
* Ein webbasierter Authentifizierungsfluss kann auch für eine Konfigurationsseite, ein Aufgabenmodul oder eine Messagingerweiterung verwendet werden.
* Sie können einen webbasierten Authentifizierungsfluss für einen Unterhaltungsbot verwenden, den Sie mit einem Aufgabenmodul verwenden müssen.

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser einer bereits authentifizierten Website kein Cookie hinzu, wenn der Link von einer externen Website stammt. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Verwendung gekennzeichnet sind – oder sicherstellen, dass ein `SameSite=None; Secure` Fallback vorhanden ist.

### <a name="android-system-webview"></a>Android System WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps Webinhalte anzeigen können. Die neuen Einschränkungen werden zwar standardmäßig, beginnend mit Chrome 80, aber nicht sofort in WebViews erzwungen. Sie werden in Zukunft angewendet. Zur Vorbereitung ermöglicht Android systemeigenen Apps das direkte Festlegen von Cookies über die [CookeManager-API:](https://developer.android.com/reference/android/webkit/CookieManager)

* Für Cookies, die nur in einem Kontext eines Erstverdingten benötigt werden, sollten Sie sie als `SameSite=Lax` oder `SameSite=Strict` deklarieren, falls erforderlich.
* Für Cookies, die in einem Drittanbieterkontext benötigt werden, sollten Sie sicherstellen, dass sie als deklariert `SameSite=None; Secure` werden.

## <a name="learn-more"></a>Weitere Informationen

[SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)

[SameSite-Cookierezepte](https://web.dev/samesite-cookie-recipes/)

[Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)

[Entwickler: Machen Sie sich bereit für neue SameSite=None; Einstellungen für sicheres Cookie](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**OpenId Connect-Auswirkung**<br>
[Bevorstehende Änderungen des SameSite-Cookies in ASP.NET und ASP.NET Core](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
