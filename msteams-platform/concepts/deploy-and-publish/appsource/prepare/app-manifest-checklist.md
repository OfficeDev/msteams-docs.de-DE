---
title: Checkliste für das App-Manifest
description: Die Prüfliste für Ihr App-Manifest für die Veröffentlichung Ihrer Microsoft Teams-App in AppSource
ms.topic: reference
keywords: Prüfliste für die Veröffentlichung im Store für Teams
ms.openlocfilehash: f07c0d2693d12d56d6717724e1ef402cf79d5fff
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014397"
---
# <a name="app-manifest-checklist"></a>Checkliste für das App-Manifest

>[!IMPORTANT]
>Aktuell wird die Verwaltung von Office-Lösungen vom Verkäufer-Dashboard zum Partner Center verschoben. Detailinformationen finden Sie unter [Verschieben vom Verkäufer-Dashboard zum Partner Center](https://developer.microsoft.com/office/blogs/moving-management-of-solutions-from-seller-dashboard-to-partner-center/) und unter [FAQ ‒ Häufig gestellte Fragen](https://docs.microsoft.com/office/dev/store/partner-center-faq).

Ihr App-Manifest muss den unten beschriebenen Richtlinien entsprechen.

>[!Tip]
> Verwenden Sie App Studio, um Ihr App-Manifest zu erstellen. Die meisten der unten aufgeführten Anforderungen werden überprüft, und auf der Registerkarte "Testen" und "Verteilen" werden Fehler oder **Warnungen** angezeigt.

## <a name="tips"></a>Tipps 

* Verwenden Sie in Ihrem App-Namen nicht "Teams", "Microsoft" oder "App".
* Der DeveloperName in Ihrem Manifest muss mit dem im Partner Center definierten Anbieternamen identisch sein.
* Stellen Sie sicher, dass die App-Beschreibung, Screenshots, Text und Werbebilder nur die App beschreiben und keine zusätzliche Werbung, Werbeaktionen oder urheberrechtlich geschützten Markennamen enthalten.
* Wenn Ihr Produkt ein Konto für Ihren Dienst oder einen anderen Dienst erfordert, listen Sie dieses in der Beschreibung auf, und stellen Sie sicher, dass Links zum Registrieren, Anmelden und Abmelden vorhanden sind.
* Wenn Ihr Produkt zusätzliche Käufe erfordert, um ordnungsgemäß zu funktionieren, listen Sie dies in der Beschreibung auf.
* Stellen Sie die erforderlichen Links zu Nutzungsbedingungen und Datenschutzrichtlinien im Manifest und im Partner Center oder Dashboard zur Verfügung. Stellen Sie sicher, dass die Links ordnungsgemäß in die richtige Dokumentation aufgelöst werden, idealerweise teamsspezifisch. Für Bots müssen Sie diese Informationen im Abschnitt "Übermittlung" der Registrierungsseite von Bot Framework bereitstellen.
* Stellen Sie sicher, dass metadaten im Manifest genau mit Metadaten im Partner Center (und, für Bots, in der Bot-Framework-Registrierung) übereinstimmungen. Beachten Sie, dass Ihr Partner Center-Eintrag möglicherweise eine detailliertere und formatierte Beschreibung für die Verwendung auf der AppSource-Produktseite enthält.
* Stellen Sie sicher, dass der  in Ihrem Manifest verwendete Titel genau mit dem in der Partner Center-Übermittlung eingegebenen Titel der App übereinstimmen muss. *Siehe* [Erstellen effektiver Einträge in Microsoft AppSource und in Office – Verwenden Sie einen konsistenten Add-In-Namen.](https://docs.microsoft.com/office/dev/store/create-effective-office-store-listings#use-a-consistent-add-in-name)

## <a name="metadata-requirement"></a>Metadatenanforderung

Die folgenden Metadaten sind für Ihre App erforderlich.

|Daten|Typ|Size|Manifest|Partner Center|Beschreibung|
|---|---|---|---|---|---|
|App-Paket|.ZIP|||✔|Das eigentliche App-Paket für das Hochladen oder die AppSource-Übermittlung.|
|Farblogo|.png|192 &times; 192 Pixel|`icon.color`||Das Symbol, das im Produktseiteneintrag im Teams-Katalog angezeigt werden soll. Dies ist Ihr vollfarbiges Produktlogo.|
|Logogliederung|.png|32 &times; 32 Pixel|`icon.outline`||Das Symbol, das in Teams, im Teams-Chatkanal und anderen Speicherorten angezeigt werden soll. Dies ist Ihr Logo, das als weiße Gliederung mit transparentem Hintergrund gerendert wird.|
|App-Logo|PNG, JPG, JPEG, GIF|300 &times; 300 Pixel||✔|Das Symbol, das in AppSource angezeigt werden soll. Dies ist das vollfarbige Produktlogo und eine andere Datei als die, die im Manifest für verwendet `icon.color` wird. Sie sollte kleiner als 512 KB sein.|
|Supportlink|URL|||✔|Ein Link zur Unterstützung von Material für Endbenutzer, die Ihre App möglicherweise nicht installiert haben. Öffentlich verfügbarer Link ohne Anmeldung (HTTPS).|
|Link "Datenschutz"|URL||`developer.privacyUrl`|✔|Ein Link zu Ihrer Datenschutzrichtlinie (HTTPS).|
|Videolink|URL|||Optional|Ein Link zu einem Video über Ihre App.|
|EULA|DOC, PDF usw.|||Optional|Für AppSource ist ein Endbenutzerlizenzvertrag erforderlich, den Sie als Anlage bereitstellen können. Wenn Sie eine EULA nicht übermitteln möchten, wird sie in Ihrem Auftrag bereitgestellt.|
|Nutzungsbedingungen|URL||`developer.termsOfServiceUrl`||Ein Link zu Ihren Nutzungsbedingungen (HTTPS).|
|Testhinweise|Inline oder Link zu einer öffentlichen URL ausfüllen|||Ausführliche Testhinweise zum schrittweisen Testen Ihrer Anwendung. Geben Sie zum Testen von Szenarien mit Administrator- und Nichtadministratoren zwei Anmeldeinformationen an.|

## <a name="localized-content"></a>Lokalisierter Inhalt

> [!NOTE]
> AppSource plant die Unterstützung lokalisierter Inhalte für die folgenden Metadaten. Derzeit wird Ihr App-Eintrag nur in Englisch in AppSource angezeigt, im Teams-Client jedoch ordnungsgemäß lokalisiert. Weitere [Informationen finden Sie unter "Lokalisieren](~/concepts/build-and-test/apps-localization.md) Ihrer App".

|Daten|Typ|Size|Manifest|Partner Center|Beschreibung|
|---|---|---|---|---|---|
|App-Name|Zeichenfolge|30|`name.short`|✔|Der Name ihrer Anwendung, wie er im Store und im Produkt angezeigt werden soll.|
|Langer App-Name|Zeichenfolge|30|`name.full`|✔|Der Name ihrer Anwendung, wie er im Store und im Produkt angezeigt werden soll.|
|Kurzbeschreibung|Zeichenfolge|80|`description.short`|✔|Kurze Beschreibung Ihrer App.|
|Lange Beschreibung|Zeichenfolge|4000|`description.full`|✔|Eine ausführlichere Beschreibung Ihrer App. In der Manifestdatei ist eine genaue Zusammenfassung ausreichend. In Partner Center können Sie eine detailliertere und formatierte Beschreibung für die AppSource-Produktseite verwenden.|
|Screenshot (1-5)|PNG, JPG oder GIF|1366w x 768h und kleiner als 1024 KB||✔|Mindestens ein Screenshot, der ihre App-Erfahrung zeigt. Wird auf der Seite mit den App-Details verwendet.|

## <a name="submission-extras-for-bots"></a>Übermittlungs-Extras für Bots

Bots in Microsoft Teams müssen mithilfe von Bot Framework erstellt werden. Anweisungen [finden Sie unter "Erstellen eines Bots".](~/bots/how-to/create-a-bot-for-teams.md) Verwenden Sie ein 96 x 96-Farbsymbol für das Symbol Ihres Bots in Bot Framework.
