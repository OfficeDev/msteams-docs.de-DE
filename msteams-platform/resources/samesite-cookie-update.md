---
title: Microsoft Teams und das SameSite-Cookie-Attribut (2020 Update)
author: laujan
description: ''
keywords: Cookie-Attribute SameSite
ms.topic: reference
ms.author: lomeybur
ms.openlocfilehash: 167266ba0b5af1c8233cffe1fef496dd94c27ae4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674106"
---
# <a name="microsoft-teams-and-the-samesite-cookie-attribute-2020-update"></a>Microsoft Teams und das SameSite-Cookie-Attribut (2020 Update)

## <a name="cookies-in-brief"></a>Cookies in Kürze

 Cookies sind Textzeichenfolgen, die von Websites gesendet und über den Webbrowser auf einem Computer gespeichert werden. Sie werden normalerweise für die Authentifizierung und Personalisierung verwendet, beispielsweise zum Aufrufen von statusbehafteten Informationen, zum Beibehalten von Benutzereinstellungen, zum Aufzeichnen von Browseraktivitäten und Anzeigen relevanter anzeigen. Cookies sind immer mit einer bestimmten Domäne verknüpft und können von verschiedenen Parteien installiert werden. Sie werden wie folgt kategorisiert:

 |Cookie|Bereich|
 | ------ | ------ |
 |**Erstanbieter-Cookie**|Ein First-Party-Cookie wird von Websites erstellt, die ein Benutzer besucht und zum Speichern von Daten wie Einkaufswagen Elementen, Anmeldeinformationen (beispielsweise Authentifizierungscookies) und anderen Analysen verwendet wird.|
 |**Zweit Anbieter Cookie**|Eine Drittanbieter-Cookies ist technisch identisch mit einem First-Party-Cookie. Der Unterschied besteht darin, dass Daten über eine Daten Partnerschaftsvereinbarung an einen zweiten Teilnehmer weitergegeben werden (beispielsweise [Microsoft Teams Analytics und Berichterstellung](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference)). |
 |**Drittanbieter-Cookie**|Ein Drittanbieter Cookie wird von einer Domäne installiert, die nicht der Benutzer ist, der explizit besucht wurde und hauptsächlich für die Nachverfolgung (beispielsweise "like"-Schaltflächen), für die Bereitstellung von anzeigen und für Live-Chats verwendet wird.|

### <a name="cookies-and-http-requests"></a>Cookies und HTTP-Anforderungen

Vor der Einführung von SameSite-Einschränkungen wurden Cookies, die im Browser gespeichert wurden, an *jede* HTTP-Webanforderung angefügt und vom HTTP-Antwortheader "Satz-Cookie" an den Server gesendet. Vorhersehbar ist, dass die Leistung die Möglichkeit zur Einführung von Sicherheitsrisiken wie CSRF-Angriffe (Cross-Site Request Fälschung) hat. *Siehe* [http-Cookies](https://developer.mozilla.org/docs/Web/HTTP/Cookies). Die SameSite-Komponente hat diese Exposition durch die Implementierung und Verwaltung im SetCookie-Header abgeschwächt.

### <a name="samesite-attribute-initial-release"></a>SameSite-Attribut: erste Version

In Google Chrome, Version 51, wurde die setcookie SameSite-Spezifikation als *optionales* Attribut eingeführt. Beginnend mit Build 17672 wurde von Windows 10 die SameSite-Cookie-Unterstützung für den [Microsoft-Edge-Browser](https://blogs.windows.com/msedgedev/2018/05/17/samesite-cookies-microsoft-edge-internet-explorer/)eingeführt.

Entwickler konnten das Hinzufügen des SameSite-Cookie-Attributs zur setcookie-Kopfzeile ablehnen oder es mit einer von zwei Einstellungen, *Lax* und *Strict*, hinzufügen. Ein nicht implementiertes SameSite-Attribut wurde als Standardzustand betrachtet.

## <a name="samesite-cookie-attribute-2020-release"></a>SameSite-Cookie-Attribut: 2020 Release

In Chrome 80, das im Februar 2020 veröffentlicht werden soll, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt. Drei Werte können an das aktualisierte SameSite-Attribut übergeben werden: *Strict*, *Lax*oder *None*. Cookies, die das SameSite `SameSite=Lax`-Attribut nicht angeben, werden standardmäßig verwendet.

|Setting | Erzwingung | Wert |Attributspezifikation |
| -------- | ----------- | --------|--------|
| **Lax**  | Cookies werden automatisch nur im Kontext eines *ersten Anbieters* und mit HTTP GET-Anforderungen gesendet. SameSite-Cookies werden für websiteübergreifende unter Anforderungen wie Aufrufe zum Laden von Bildern oder iframes verweigert, Sie werden jedoch gesendet, wenn ein Benutzer von einer externen Website zur URL navigiert, beispielsweisedurch Folgen eines Links.| **Default** |`Set-Cookie: key=value; SameSite=Lax`|
| **Strict** |Der Browser sendet nur Cookies für Erstanbieter-Kontext Anforderungen (Anforderungen, die von der Website stammen, von der das Cookie festgelegt wird). Wenn die Anforderung von einer anderen URL als der des aktuellen Standorts stammt, wird keine der mit dem `Strict` Attribut gekennzeichneten Cookies gesendet.| Optional |`Set-Cookie: key=value; SameSite=Strict`|
| **Keine** | Cookies werden sowohl im Erstanbieter Kontext als auch bei Cross-Origin-Anforderungen gesendet. der Wert muss jedoch explizit auf **`None`** festgelegt werden, und alle Browseranforderungen **müssen dem HTTPS-Protokoll entsprechen** und **`Secure`** das Attribut einschließen, das eine verschlüsselte Verbindung erfordert. Cookies, die dieser Anforderung nicht entsprechen, werden **abgelehnt**. <br/>**Beide Attribute sind zusammen erforderlich**. Wenn nur **`None`** ohne **`Secure`** oder angegeben wird, wenn das HTTPS-Protokoll nicht verwendet wird, wird das Drittanbieter Cookie zurückgewiesen.| Optional, bei Festlegung jedoch ist das HTTPS-Protokoll erforderlich. |`Set-Cookie: key=value; SameSite=None; Secure` |

## <a name="handling-incompatible-clients"></a>Behandeln inkompatibler Clients

> [!IMPORTANT]
> `SameSite=None` Wird derzeit vom Microsoft [**Teams-Desktop Client**](/aspnet/core/security/samesite?view=aspnetcore-3.1#test-with-electron) oder älteren Versionen von Chrome oder Safari nicht unterstützt. *Siehe* [bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients).
>Es gibt jedoch zwei **Problem Umgehungslösungen**:
>
>1. Überprüfen Sie den Benutzer-Agent, um die richtige SameSite-Eigenschaft bereitzustellen. Sie können die User-Agent-Prüfung in [**C#**](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/) und [**node. js**](https://web.dev/samesite-cookie-recipes/)implementieren.
>2. Legen Sie die Cookie-Attribute mit den neuen und alten Modellen fest. *Siehe* [Handling inkompatibler Clients](https://web.dev/samesite-cookie-recipes/#handling-incompatible-clients)<br><br>
>**Wenn Ihre APP im Microsoft Teams-Desktop Client ausgeführt wird und Sie das SameSite-Attribut auf `SameSite=None` festlegen, wird Ihre APP nicht wie erwartet funktionieren.**

Durch die Verwendung einer der beiden Vorgehensweisen wird sichergestellt, dass Ihre Anwendung weiterhin ordnungsgemäß `SameSite=None` funktioniert, wenn der Desktop Client für Microsoft Teams auf eine kompatible Version von Chrom aktualisiert wird.

## <a name="teams-implications-and-adjustments"></a>Auswirkungen und Anpassungen von Teams

>[!WARNING]
>**Anwendungen, die im Microsoft Teams-Desktop Client ausgeführt werden, `SameSite=None` sind mit dem Attribut nicht kompatibel, und Sie funktionieren nicht wie erwartet.** Weitere Informationen finden Sie unter **Problem Umgehungslösungen**oben.

1. Aktivieren Sie die entsprechende SameSite-Einstellung für Ihre Cookies, und überprüfen Sie, ob Ihre apps und Erweiterungen weiterhin in Microsoft Teams funktionieren.
1. Wenn Ihre apps oder Erweiterungen ausfallen, nehmen Sie die erforderlichen Korrekturen vor der Chrome 80-Version vor.
1. Microsoft-interne Partner können dem folgenden Team beitreten, wenn Sie weitere Informationen benötigen oder Hilfe zu diesem <https://teams.microsoft.com/l/team/19%3A08b594cd465e4c0491fb751e823802e2%40thread.skype/conversations?groupId=4d6d04cd-dbf0-43c8-a2ff-f80dd38be034&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47>Problem erhalten:.

> [!NOTE]
> Für bewährte Methoden empfiehlt es sich, immer SameSite-Attribute entsprechend der beabsichtigten Verwendung für Ihre Cookies festzulegen – verlassen Sie sich nicht auf das Standardbrowser Verhalten. Weitere *Informationen finden Sie unter* [Developers: Get Ready for New SameSite = None; Einstellungen für sichere Cookies](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html).

### <a name="tabs-task-modules-and-message-extensions"></a>Registerkarten, Aufgaben Module und Nachrichten Erweiterungen

* Microsoft Teams- `<iframes>` Registerkarten verwenden, um Inhalte einzubetten, die im Kontext der obersten Ebene oder eines ersten Anbieters angezeigt werden.
* Aufgaben Module ermöglichen Ihnen das Erstellen modaler Popups in Ihrer Teams-Anwendung. Ähnlich wie bei einer Registerkarte wird in der aktuellen Seite ein modales Fenster geöffnet.
* Mithilfe von Nachrichten Erweiterungen können Sie bereicherte Inhalte aus externen Ressourcen in Chatnachrichten einfügen.

Alle von eingebetteten Inhalten verwendeten Cookies werden als Drittanbieter betrachtet, wenn die Website in einer `<iframe>`angezeigt wird. Darüber hinaus müssen Sie sicherstellen, dass diese für die websiteübergreifende Verwendung `<img>` `<script>` `SameSite=None; Secure` markiert sind, wenn Remoteressourcen auf einer Seite Cookies senden, die mit einer Anforderung gesendet werden (beispielsweise und Tags, externe Schriftarten und personalisierte Inhalte), oder sicherstellen, dass ein Fallback stattfindet.

### <a name="authentication"></a>Authentifizierung

* Wenn Sie die Authentifizierung für eingebettete Inhaltsseiten in Registerkarten benötigen, müssen Sie den webbasierten Authentifizierungs Fluss verwenden.
* Ein webbasierter Authentifizierungs Fluss kann auch für eine Konfigurationsseite, einen Aufgabenmodul oder eine Messaging Erweiterung verwendet werden.
* Sie können einen webbasierten Authentifizierungs Fluss für einen Unterhaltungs-bot verwenden, den Sie für die Verwendung eines Aufgabenmoduls benötigen.

Gemäß den aktualisierten SameSite-Einschränkungen fügt ein Browser kein Cookie zu einer bereits authentifizierten Website hinzu, wenn die Verknüpfung von einer externen Website abgeleitet wird. Sie müssen sicherstellen, dass Ihre Authentifizierungscookies für die websiteübergreifende Verwendung markiert `SameSite=None; Secure` sind – oder sicherstellen, dass ein Fallback stattfindet.

### <a name="android-system-webview"></a>Android-System-WebView

Android WebView ist eine Chrome-Systemkomponente, mit der Android-Apps Webinhalte anzeigen können. Während die neuen Einschränkungen standardmäßig werden, beginnend mit Chrome 80, werden Sie nicht sofort in Webviews erzwungen. Sie werden zukünftig angewendet. Zur Vorbereitung ermöglicht Android Native apps, Cookies direkt über die [cookemanager-API](https://developer.android.com/reference/android/webkit/CookieManager)festzulegen:

* Für Cookies, die nur im Kontext eines Erstanbieters erforderlich sind, sollten Sie Sie als `SameSite=Lax` oder `SameSite=Strict`, je nach Bedarf deklarieren.
* Für Cookies, die in einem Drittanbieter Kontext benötigt werden, sollten Sie sicherstellen, dass `SameSite=None; Secure`Sie als deklariert werden.

## <a name="learn-more"></a>Weitere Informationen

[SameSite-Beispiele](https://github.com/GoogleChromeLabs/samesite-examples)

[Rezepte für SameSite-Cookies](https://web.dev/samesite-cookie-recipes/)

[Bekannte inkompatible Clients]( https://www.chromium.org/updates/same-site/incompatible-clients)

[Entwickler: machen Sie sich auf neue SameSite = None gefasst; Einstellungen für sichere Cookies](https://blog.chromium.org/2019/10/developers-get-ready-for-new.html)

**OpenID Connect-Auswirkung**<br>
[Bevorstehende SameSite-Cookie-Änderungen in ASP.net und ASP.net-Kern](https://devblogs.microsoft.com/aspnet/upcoming-samesite-cookie-changes-in-asp-net-and-asp-net-core/)
