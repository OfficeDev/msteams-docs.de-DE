---
title: Checkliste für das App-Manifest
description: Die Prüfliste für Ihr App-Manifest für die Veröffentlichung Ihrer Microsoft Teams-App in AppSource
ms.topic: reference
localization_priority: Normal
keywords: Prüfliste für die Veröffentlichung von Office-Veröffentlichungen in Teams
ms.openlocfilehash: a8fd57d8050530856fa635f59c0a6ce4f8c2a5cf
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019902"
---
# <a name="app-manifest-checklist"></a>Checkliste für das App-Manifest

>[!IMPORTANT]
>Aktuell wird die Verwaltung von Office-Lösungen vom Verkäufer-Dashboard zum Partner Center verschoben. Detailinformationen finden Sie unter [Verschieben vom Verkäufer-Dashboard zum Partner Center](https://developer.microsoft.com/office/blogs/moving-management-of-solutions-from-seller-dashboard-to-partner-center/) und unter [FAQ ‒ Häufig gestellte Fragen](https://docs.microsoft.com/office/dev/store/partner-center-faq).

Ihr App-Manifest muss den unten beschriebenen Richtlinien entsprechen.

>[!Tip]
> Verwenden Sie App Studio, um Ihr App-Manifest zu erstellen. Es überprüft die meisten nachfolgenden Anforderungen für Sie und zeigt alle Fehler oder Warnungen auf der Registerkarte **Test und Verteilen** an.

## <a name="tips"></a>Tipps 

* Verwenden Sie "Teams", "Microsoft" oder "App" nicht in Ihrem App-Namen.
* Der developerName in Ihrem Manifest muss mit dem im Partner Center definierten Anbieternamen identisch sein.
* Stellen Sie sicher, dass die App-Beschreibung, Screenshots, Text- und Werbebilder nur die App beschreiben und keine zusätzliche Werbung, Werbeaktionen oder urheberrechtlich geschützte Markennamen enthalten.
* Wenn Für Ihr Produkt ein Konto für Ihren Dienst oder einen anderen Dienst erforderlich ist, listen Sie dies in der Beschreibung auf, und stellen Sie sicher, dass Links zum Registrieren, Anmelden und Abmelden vorhanden sind.
* Wenn für Ihr Produkt zusätzliche Einkäufe erforderlich sind, um ordnungsgemäß zu funktionieren, listen Sie dies in der Beschreibung auf.
* Stellen Sie die erforderlichen Links zu Nutzungsbedingungen und Datenschutzrichtlinien im Manifest und im Partner Center oder Dashboard zur Verfügung. Stellen Sie sicher, dass die Links ordnungsgemäß in die richtige Dokumentation aufgelöst werden, idealerweise teamsspezifisch. Für Bots müssen Sie diese Informationen im Abschnitt Übermittlung auf der Registrierungsseite für Bot Framework bereitstellen.
* Stellen Sie sicher, dass Metadaten im Manifest genau den Metadaten im Partner Center (und für Bots in der Bot Framework-Registrierung) entspricht. Beachten Sie, dass Ihr Partner Center-Eintrag eine ausführlichere und formatierte Beschreibung für die Verwendung auf der AppSource-Produktseite enthalten kann.
* Stellen Sie sicher, dass der  in Ihrem Manifest verwendete App-Titel genau mit dem in der Partner Center-Übermittlung eingegebenen App-Titel übereinstimmen soll. *Weitere* Informationen finden Sie unter Create [effective listings in Microsoft AppSource and within Office – Use a consistent add-in name](https://docs.microsoft.com/office/dev/store/create-effective-office-store-listings#use-a-consistent-add-in-name).

## <a name="metadata-requirement"></a>Metadatenanforderung

Die folgenden Metadaten sind für Ihre App erforderlich.

|Daten|Typ|Size|Manifest|Partner Center|Beschreibung|
|---|---|---|---|---|---|
|App-Paket|.ZIP|||✔|Das tatsächliche App-Paket für das Hochladen oder die AppSource-Übermittlung.|
|Farblogo|.png|192 &times; 192 Pixel|`icon.color`||Das Symbol, das im Produktseiteneintrag im Teams-Katalog angezeigt werden soll. Dies ist Ihr vollfarbiges Produktlogo.|
|Logogliederung|.png|32 &times; 32 Pixel|`icon.outline`||Das Symbol, das in Teams, im Teams-Chatkanal und an anderen Orten angezeigt werden soll. Dies ist Ihr Logo, das als weiße Gliederung mit transparentem Hintergrund gerendert wird.|
|App-Logo|.png, .jpg, .jpeg, .gif|300 &times; 300 Pixel||✔|Das Symbol, das in AppSource angezeigt werden soll. Dies ist das vollfarbige Produktlogo und eine andere Datei als die im Manifest für verwendete `icon.color` Datei. Sie sollte kleiner als 512 KB sein.|
|Supportlink|URL|||✔|Ein Link zum Unterstützen von Material für Endbenutzer, die Ihre App möglicherweise nicht installiert haben. Öffentlich zugänglicher Link ohne Anmeldung (HTTPS).|
|Link zum Datenschutz|URL||`developer.privacyUrl`|✔|Ein Link zu Ihrer Datenschutzrichtlinie (HTTPS).|
|Videolink|URL|||Optional|Ein Link zu einem Video zu Ihrer App.|
|EULA|.doc, .pdf usw.|||Optional|AppSource erfordert einen Endbenutzerlizenzvertrag (EULA), den Sie als Anlage bereitstellen können. Wenn Sie keine EULA übermitteln möchten, wird eine in Ihrem Namen bereitgestellt.|
|Nutzungsbedingungen|URL||`developer.termsOfServiceUrl`||Ein Link zu Ihren Nutzungsbedingungen (HTTPS).|
|Testhinweise|Ausfüllen von Inline oder Link zu einer öffentlichen URL|||Ausführliche Testhinweise zum schrittweisen Testen Ihrer Anwendung. Fügen Sie zwei Anmeldeinformationen zum Testen von Szenarien mit Administrator- und Nicht-Administrator-Szenarien ein.|

## <a name="localized-content"></a>Lokalisierter Inhalt

> [!NOTE]
> AppSource plant die Unterstützung lokalisierter Inhalte für die folgenden Metadaten. Derzeit wird Ihr App-Eintrag nur in Englisch in AppSource angezeigt, aber im Teams-Client ordnungsgemäß lokalisiert angezeigt. Weitere Informationen finden Sie unter [Localizing your app.](~/concepts/build-and-test/apps-localization.md)

|Daten|Typ|Size|Manifest|Partner Center|Beschreibung|
|---|---|---|---|---|---|
|App-Name|Zeichenfolge|30|`name.short`|✔|Der Name ihrer Anwendung, wie sie im Store und im Produkt angezeigt werden soll.|
|Langer App-Name|Zeichenfolge|30|`name.full`|✔|Der Name ihrer Anwendung, wie sie im Store und im Produkt angezeigt werden soll.|
|Kurzbeschreibung|Zeichenfolge|80|`description.short`|✔|Kurze Beschreibung Ihrer App.|
|Lange Beschreibung|Zeichenfolge|4000|`description.full`|✔|Eine ausführlichere Beschreibung Ihrer App. In der Manifestdatei ist eine genaue Zusammenfassung ausreichend. Im Partner Center können Sie eine detailliertere und formatierte Beschreibung für die AppSource-Produktseite verwenden.|
|Screenshot (1-5)|.png, .jpg oder GIF|1366w x 768h und kleiner als 1024 KB||✔|Mindestens ein Screenshot, der Ihre App-Erfahrung zeigt. Wird auf der Seite "App-Details" verwendet.|

## <a name="submission-extras-for-bots"></a>Übermittlungs-Extras für Bots

Bots in Microsoft Teams müssen mithilfe von Bot Framework erstellt werden. Anweisungen [finden Sie unter Erstellen eines Bots.](~/bots/how-to/create-a-bot-for-teams.md) Verwenden Sie ein 96 x 96-Farbsymbol für das Symbol Ihres Bots in Bot Framework.
