---
title: Prüfliste für App-Manifeste
description: Die Prüfliste für Ihr App-Manifest für die Veröffentlichung Ihrer Microsoft Teams-app in AppSource
keywords: Office-Veröffentlichungs Checkliste für Microsoft Teams Publishing Store
ms.openlocfilehash: e684bb4f578944c6f37eeb43541a491d42ec3479
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674420"
---
# <a name="app-manifest-checklist"></a>Prüfliste für App-Manifeste

Das App-Manifest muss mit den unten beschriebenen Richtlinien übereinstimmen.

>[!Tip]
> Mithilfe von App Studio können Sie Ihr App-Manifest erstellen. Die meisten der unten aufgeführten Anforderungen werden für Sie überprüft, und es werden alle Fehler oder Warnungen auf der Registerkarte **Testen und verteilen** angezeigt.

## <a name="tips"></a>Tipps 

* Verwenden Sie nicht "Teams", "Microsoft" oder "App" in Ihrem APP-Namen.
* Der Entwickler Name im App-Manifest muss mit dem im Partner Center oder Verkäuferdashboard definierten Anbieternamen übereinstimmen.
* Stellen Sie sicher, dass die APP-Beschreibung, Screenshots, Text und Werbebilder nur die APP beschreiben und keine zusätzlichen Werbungen, Promotionen oder urheberrechtlich geschützten Markennamen enthalten.
* Wenn für Ihr Produkt ein Konto in Ihrem Dienst oder ein anderer Dienst erforderlich ist, geben Sie das in der Beschreibung an, und stellen Sie sicher, dass Links zur Registrierung vorhanden sind, und melden Sie sich an und melden Sie sich ab.
* Wenn Ihr Produkt zusätzliche Käufe erfordert, um ordnungsgemäß zu funktionieren, müssen Sie dies in der Beschreibung auflisten.
* Geben Sie die erforderlichen Begriffe und Datenschutzrichtlinien Links im Manifest und im Partner Center oder Verkäuferdashboard an. Stellen Sie sicher, dass die Links ordnungsgemäß in die richtige Dokumentation aufgelöst werden, idealerweise Teams spezifisch. Für Bots müssen Sie dieselben Informationen im Abschnitt "Übermittlung" der Seite "bot Framework-Registrierung" angeben.
* Stellen Sie sicher, dass Metadaten im Manifest exakt mit den Metadaten im Partner Center oder Verkäuferdashboard (und, für Bots, in der bot-Framework-Registrierung) übereinstimmen. Beachten Sie, dass Ihr Verkäuferdashboard Eintrag eine ausführlichere und formatierte Beschreibung zur Verwendung auf der AppSource-Produktseite enthalten sollte.
* Stellen Sie sicher, dass der in ihrem Manifest verwendete APP-Titel exakt mit dem im Partner Center eingegebenen APP-Titel oder Verkäuferdashboard Übermittlung übereinstimmt.

## <a name="metadata-requirement"></a>Metadaten-Anforderung

Die folgenden Metadaten sind für Ihre APP erforderlich.

|Daten|Typ|Größe|Manifest|Partner Center|Beschreibung|
|---|---|---|---|---|---|
|App-Paket|.ZIP|||✔|Das tatsächliche APP-Paket zum Hochladen oder AppSource-Übermittlung.|
|Farb Logo|.png|192&times;192 Pixel|`icon.color`||Das Symbol, das in der Produktseiten Liste im Team Katalog angezeigt werden soll. Dies ist Ihr vollfarbiges Produktlogo.|
|Logo Umriss|.png|32&times;32 Pixel|`icon.outline`||Das Symbol, das in Microsoft Teams, im Chat Kanal für Teams und an anderen Standorten angezeigt werden soll. Dies ist Ihr Logo, das als weißer Umriss mit transparentem Hintergrund gerendert wird.|
|App-Logo|. png,. jpg,. JPEG,. gif|300&times;300 Pixel||✔|Das Symbol, das in AppSource angezeigt werden soll. Dies ist das vollfarbige Produktlogo und eine andere Datei als die, die im Manifest für `icon.color`verwendet wird. Er sollte kleiner als 512 KB sein.|
|Support Link|URL|||✔|Ein Link zum Supportmaterial für Endbenutzer, die Ihre APP möglicherweise nicht installiert haben. Öffentlich zugänglicher Link ohne Anmeldung (HTTPS).|
|DatenschutzLink|URL||`developer.privacyUrl`|✔|Ein Link zu ihrer Datenschutzrichtlinie (HTTPS).|
|Videolink|URL|||Optional|Ein Link zu einem Video über Ihre APP.|
|EULA|. doc,. PDF, etc.|||Optional|AppSource erfordert einen Endbenutzer-Lizenzvertrag (EULA), den Sie als Anlage bereitstellen können. Wenn Sie sich dafür entscheiden, keinen EULA zu übermitteln, wird einer in Ihrem Namen bereitgestellt.|
|Nutzungsbedingungen|URL||`developer.termsOfServiceUrl`||Ein Link zu ihren Nutzungsbedingungen (HTTPS).|
|Test Notizen|Inline-oder Link zu einer öffentlichen URL ausfüllen|||Ausführliche Test Hinweise zum Testen der Anwendung Schritt für Schritt. Geben Sie zwei Anmeldeinformationen zum Testen von Administrator-und nicht-Administrator-Szenarien an.|

## <a name="localized-content"></a>Lokalisierter Inhalt

> [!NOTE]
> AppSource plant die Unterstützung lokalisierter Inhalte für die folgenden Metadaten. Derzeit wird Ihre APP-Auflistung nur in englischer Sprache in AppSource angezeigt, wird jedoch im Microsoft Teams-Client ordnungsgemäß lokalisiert angezeigt. Weitere Informationen finden Sie unter [Lokalisieren Ihrer APP](~/concepts/build-and-test/apps-localization.md) .

|Daten|Typ|Größe|Manifest|Partner Center|Beschreibung|
|---|---|---|---|---|---|
|App-Name|Zeichenfolge|30|`name.short`|✔|Der Name Ihrer Anwendung, wie er im Storefront-und im-Produkt angezeigt werden soll.|
|Langer App-Name|Zeichenfolge|30|`name.full`|✔|Der Name Ihrer Anwendung, wie er im Storefront-und im-Produkt angezeigt werden soll.|
|Kurzbeschreibung|Zeichenfolge|80|`description.short`|✔|Kurze Beschreibung Ihrer APP.|
|Lange Beschreibung|Zeichenfolge|4000|`description.full`|✔|Eine ausführlichere Beschreibung Ihrer APP. In der Manifestdatei ist eine genaue Zusammenfassung ausreichend. Im Partner Center können Sie eine umfangreichere und formatierte Beschreibung für die AppSource-Produktseite verwenden.|
|Screenshots (1-5)|. png,. jpg oder. gif|1366w x 768h und kleiner als 1024 KB||✔|Mindestens ein Screenshot, der Ihre APP-Erfahrung zeigt. Wird auf der Seite mit den App-Details verwendet.|

## <a name="submission-extras-for-bots"></a>Eingabe-Extras für Bots

Bots in Microsoft Teams müssen mit bot Framework erstellt werden. Anweisungen finden Sie unter [Create a bot](~/bots/how-to/create-a-bot-for-teams.md) . Verwenden Sie ein 96x96-Farbsymbol für das Symbol Ihres bot im bot-Framework.
