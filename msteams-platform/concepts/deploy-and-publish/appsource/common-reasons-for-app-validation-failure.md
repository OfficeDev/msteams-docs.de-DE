---
title: Häufige Gründe für App-Überprüfungsfehler
description: Erfahren Sie mehr über die häufigsten Gründe für Fehler bei der App-Überprüfung, z. B. fehlerhafte Links, unerwartete Fehler, Abstürze, Verstöße gegen gültige Domänenrichtlinien und Funktionsfehler.
ms.topic: overview
author: v-ypalikila
ms.author: v-ypalikila
ms.localizationpriority: high
ms.openlocfilehash: 006fe6d9e939d9578fa84c61daaa4c404a10d5f6
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791727"
---
# <a name="common-reasons-for-app-validation-failure"></a>Häufige Gründe für App-Überprüfungsfehler

Die meisten Apps bestehen den Store-Übermittlungsprozess aufgrund von Problemen während der App-Entwicklung nicht. Die am häufigsten auftretenden Probleme oder Gründe werden in diesem Artikel behandelt, damit Sie Ihre App besser vorbereiten können, bevor Sie sie [zur Überprüfung einreichen](/office/dev/store/add-in-submission-guide?toc=/microsoftteams/platform/toc.json&bc=/microsoftteams/platform/breadcrumb/toc.json). Vermeiden Sie diese gängigen Fehler, und befolgen Sie die [Microsoft Teams Richtlinien für die Store-Validierung](prepare/teams-store-validation-guidelines.md) und die [Zertifizierungsrichtlinien kommerzielle Marketplaces](/legal/marketplace/certification-policies), um die Wahrscheinlichkeit zu erhöhen, dass Ihre App den Microsoft Teams Store-Übermittlungsprozess besteht.

Nachfolgenden sind die häufigsten Gründe für die Ablehnung Ihrer App aufgeführt:

:::row:::
   :::column:::
      :::image type="icon" source="../../../assets/icons/broken-links-errors-icon-1.png" link="#broken-links-functional-bugs-app-crashes-and-unexpected-errors":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../assets/icons/app-description-icon.png" link="#app-description":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/trademark-icon.png" link="#violation-of-microsoft-trademark-and-brand-guidelines":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/testability-icon.png" link="#testability":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/compliance-icon.png" link="#microsoft-365-app-compliance-program":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column:::
      :::image type="icon" source="../../../assets/icons/app-guideline-icon.png" link="#violation-of-app-icon-guidelines":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../assets/icons/app-name-icon.png" link="#app-name":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/support-link-icon.png" link="#support-link":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/schema-icon.png" link="#manifest-schema":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/app-ui-icon.png" link="#app-ui":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column:::
      :::image type="icon" source="../../../assets/icons/domain-icon.png" link="#valid-domains":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/localization-icon.png" link="#localization-information":::
   :::column-end:::
   :::column span="":::
     :::image type="icon" source="../../../assets/icons/developer-name-icon.png" link="#provider-or-developer-name-mismatch":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/privacy-policy-icon.png" link="#privacy-policy":::
   :::column-end:::
   :::column span="":::
      :::image type="icon" source="../../../assets/icons/terms-of-use-icon.png" link="#terms-of-use":::
   :::column-end:::
:::row-end:::

## <a name="broken-links-functional-bugs-app-crashes-and-unexpected-errors"></a>Fehlerhafte Links, Funktionsfehler, App-Abstürze und unerwartete Fehler

Testen Sie Ihre App, um die Richtigkeit, Funktionalität und Nutzung Ihrer App zu überprüfen. Stellen Sie sicher, dass Sie Ihre App gründlich testen, alle von Der App unterstützten End-to-End-Workflows überprüfen, die App-Kompatibilität auf den Betriebssystemen und Browsern gemäß der [Zertifizierungsrichtlinie für den kommerziellen Marketplace](/legal/marketplace/certification-policies) testen und alle Fehler beheben. Sie müssen die folgenden Fehler in Ihrer App vermeiden, bevor Sie sie zur Überprüfung einreichen:

* Fehlerhafte Links in einer App.

* Funktionsfehler, die die App-Nutzung blockieren.

* Die App stürzt ab.

* Kontinuierliches Laden von App-Oberflächen, die den Abschluss der von der App unterstützten Workflows verhindern.

* Unerwartete Fehlermeldungen während der App-Nutzung, -Anmeldung und -Registrierung sowie in Szenarien, in denen das App-Feature nicht wie erwartet funktioniert.

* Stellen Sie sicher, dass Ihre App vollständig und bereit für die Veröffentlichung ist, bevor Sie sie zur Überprüfung übermitteln.

## <a name="app-description"></a>App-Beschreibung

Eine großartige Beschreibung kann Ihre App im Microsoft Teams Store hervorheben und Kunden zum Herunterladen ermutigen. Sie müssen die folgenden Fehler in ihrer App-Beschreibung vermeiden:

* Weiterführende Informationen für neue Benutzer wie „Registrieren“- oder „Erste Schritte“- oder „Hilfe und Kontakt“-Links sind im Manifest und in der vollständigen Beschreibung von AppSource nicht enthalten.

* Der Name oder die Funktionalität einer regionspezifischen App ist in Manifest- und Partner Center-App-Beschreibungen nicht aufgeführt.

* Einschränkungen oder Kontoabhängigkeiten von externen Konten oder Diensten zum Abschließen der Anmelde-, Abmelde- und Registrierungserfahrung werden im App-Manifest und in der Langbeschreibung nicht genannt.

* Die kurze und vollständige Beschreibung im App-Manifest hebt das Wertversprechen der App nicht hervor.

* Unterstützte App-Features werden nicht aktualisiert.

* App-Vergleich mit einer anderen App.

* Verweise auf die Integrationen, die nicht Teil der App-Funktionalität sind.

* Grammatikfehler.

* Kurze und vollständige App-Beschreibung sind identisch.

## <a name="violation-of-microsoft-trademark-and-brand-guidelines"></a>Verletzung der Markenzeichen- und Markenrichtlinien von Microsoft

Die Markenressourcen von Microsoft, einschließlich Logos, Symbole, Designs, Handelskleidung, Schriftarten, Produktnamen, Dienste, Sounds, Emojis und alle anderen Markenfeatures und -elemente, unabhängig davon, ob registriert oder nicht registriert, sind proprietäre Vermögenswerte, die Eigentum von Microsoft und seiner Unternehmensgruppe sind.

Wenn Sie auf Microsoft-Marken, Produktnamen und -Dienste verweisen, müssen Sie die [Microsoft-Markenzeichen- und Markenrichtlinien](https://www.microsoft.com/legal/intellectualproperty/trademarks) einhalten. Sie müssen die folgenden häufigen Verstöße vermeiden, die zur Ablehnung der App führen:

* Kürzen von Microsoft als MS oder MSFT in der Angebotsliste und Verweisen auf die erste Instanz von Microsoft Teams im Angebotseintrag als **Teams** anstelle von **Microsoft Teams**.

* Verwenden von Microsoft-Markenressourcen in den Angebotsinhalten ohne eine ausdrückliche Lizenz von Microsoft.

* Erstellen eines Angebotseintrags (einschließlich Angebotsbeschreibung, Titel, Symbol, Screenshots und Videos), der vorgibt oder den Eindruck vermittelt, dass es sich um eine offizielle Microsoft-App für den Microsoft Teams Store handelt.

## <a name="testability"></a>Testbarkeit  

 [Detaillierte Testanweisungen](prepare/teams-store-validation-guidelines.md#app-package-and-store-listing) und Anmeldeinformationen helfen Ihnen bei einer erfolgreichen Überprüfung Ihrer App.

Stellen Sie sicher, dass Sie im Abschnitt „Hinweise für Zertifizierungsinformationen“ des Partner Centers alle erforderlichen Details zur Überprüfung Ihrer App angeben, gültige Demoanmeldeinformationen für Features, die eine Anmeldung erfordern, und Anweisungen zum Festlegen einer speziellen Konfiguration, eines Demovideos oder einer Hardware für Features, die eine schwer replizierte und vollständige Umgebung erfordern. Stellen Sie außerdem sicher, dass Sie die neuesten Kontaktinformationen angeben.

Sie müssen die folgenden Probleme vermeiden, die in 20 % der Apps auftreten, die während der App-Überprüfung abgelehnt werden:

* Keine Testanweisungen oder Anmeldeinformationen zum Testen der App.

* Nur ein Testkonto, das bereitgestellt wird, wenn eine Abhängigkeit mit zwei Testkonten besteht, um Szenarien für die Zusammenarbeit zu testen.

* Die bereitgestellten Testanweisungen und Anmeldeinformationen reichen nicht aus, um die App-Funktionstests abzuschließen.

## <a name="microsoft-365-app-compliance-program"></a>Microsoft 365-App-Compliance Program  

Das Microsoft 365 App Compliance-Programm soll Organisationen dabei helfen, Risiken zu bewerten und zu verwalten, indem Sicherheits- und Compliance-Informationen zu Ihrer App ausgewertet werden. Sie **müssen** die [Publisher Überprüfung](/azure/active-directory/develop/mark-app-as-publisher-verified) abschließen, bevor Sie Ihre App zur Veröffentlichung im Microsoft Teams Store übermitteln.

## <a name="violation-of-app-icon-guidelines"></a>Verstoß gegen die Richtlinien für App-Symbole

Symbole sind eines der Hauptelemente, die Benutzer beim Durchsuchen des Teams-Speichers sehen. Ihre Symbole müssen die Marke und den Zweck Ihrer App unter Einhaltung der folgenden [Richtlinien für App-Symbole](../../build-and-test/apps-package.md#app-icons) vermitteln. Sie müssen die folgenden Verstöße vermeiden, die zur Ablehnung der App führen:

* App-Einreichungen, die App-Pakete mit unterschiedlichen Farb- und Gliederungssymbolen oder nicht weißen und nicht transparenten Gliederungssymbolen enthalten.

* App-Einreichungen mit unterschiedlichen Logos im Partner Center und dem zur Überprüfung übermittelten App-Paket.

## <a name="app-name"></a>App-Name

Ihr App-Name spielt eine wichtige Rolle, damit Benutzer Ihre App im Microsoft Teams Store entdecken können. Stellen Sie sicher, dass Ihr App-Name den [Richtlinien für App-Namen](prepare/teams-store-validation-guidelines.md#app-name) entspricht und nicht gegen die [Microsoft-Markenzeichen und Markenrichtlinien](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks) verstößt. Sie müssen die folgenden Verstöße vermeiden, die zur Ablehnung der App führen:

* Uneinheitliche Verwendung des App-Namens während der gesamten App-Funktionalität.
* Diskrepanz zwischen dem im App-Manifest angegebenen App-Namen, der als Teil des App-Pakets übermittelt wurde, und dem App-Namen im Partner Center.
* App-Namen, die mit *Beta*, *Dev* und *Prod* angefügt werden, um anzugeben, dass die App nicht produktionsbereit ist.
* App-Übermittlungen, bei denen der Entwickler den App-Namen geändert hat, aber der alte App-Name weiterhin innerhalb der App verwendet wird.

## <a name="support-link"></a>Supportlink

 Supportlinks dürfen die Benutzer nicht zur Authentifizierung auffordern und müssen direkt zu den entsprechenden Supportinformationen führen. Sie müssen sicherstellen, dass Ihre App einen gültigen Supportlink enthält, unter dem Benutzer Kontakt mit dem Support aufnehmen können.

## <a name="manifest-schema"></a>Manifestschema

Das Teams App-Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird. Ihr Manifest muss einem öffentlich freigegebenen [Manifest-Schema](../../../resources/schema/manifest-schema.md) entsprechen. Wenn Ihre App die Lokalisierung unterstützt, stellen Sie sicher, dass Sie die Lokalisierungsmanifestschemaversion 1.5 oder höher verwenden. Bei App-Paketen, die Vorschauschemata (nicht öffentlich veröffentlicht) enthalten, schlagen die App-Überprüfung fehl.

Bei der Übermittlung eines App-Updates müssen Sie die im Manifest angegebene App-Version aktualisieren. Es wird empfohlen, beim Übermitteln einer neuen App oder eines App-Updates stets das neueste öffentlich veröffentlichte Manifestschema zu verwenden und sicherzustellen, dass die Manifestschemaversion in Microsoft Teams Store und Microsoft AppSource identisch ist.

Ihr App-Paket darf nur das Manifest, das Farbsymbol und das Gliederungssymbol Ihrer App enthalten. Bei App-Paketen, die andere zusätzliche Dateien oder Ordner enthalten, schlägt die App-Überprüfung fehl.

## <a name="app-ui"></a>App-Benutzeroberfläche

Die Benutzeroberfläche Ihrer App darf nicht unvollständig aussehen und sollte intuitiv sein. Stellen Sie sicher, dass Benutzern beim Ausführen einer Aktion auf der Benutzeroberfläche der App kein leerer Bildschirm angezeigt wird. Bei Apps mit abgeschnittenem oder überlappendem Inhalt und Apps, die fehlerhafte Bilder anzeigen, schlägt die App-Überprüfung fehl.

## <a name="valid-domains"></a>Gültige Domänen

Ihre App-Übermittlung muss den Richtlinien [für externe Domänen](/legal/marketplace/certification-policies) gemäß der Zertifizierungsrichtlinie für den kommerziellen Marketplace von Microsoft entsprechen. Damit Ihre App die Überprüfung besteht, stellen Sie sicher, dass die im App-Manifest angegebenen gültigen Domänen der direkten Kontrolle Ihrer Organisation unterliegen.

## <a name="localization-information"></a>Lokalisierungsinformationen

Sie müssen die lokalisierten Sprachdateien in Ihr App-Paket einschließen, wenn Ihre App die Lokalisierung unterstützt. Die Datei muss dem [Lokalisierungsschema von Teams](../../build-and-test/apps-localization.md) entsprechen. Bei Apps, die die Lokalisierung unterstützen, aber keine Lokalisierungsinformationen im App-Manifest enthalten, schlägt die App-Überprüfung fehl.

## <a name="provider-or-developer-name-mismatch"></a>Name des Anbieters oder Entwicklers stimmt nicht überein

Sie müssen sicherstellen, dass Sie in ihrem Angebotseintrag in beiden Storefronts denselben Entwicklernamen angeben, um Verwirrung beim Erwerb der App aus dem Microsoft Teams Store oder von Microsoft AppSource zu vermeiden. Bei Angeboten mit nicht übereinstimmendem Entwicklernamen schlägt die App-Überprüfung oft fehl.

## <a name="privacy-policy"></a>Datenschutzrichtlinie

Ihr Angebotseintrag muss einen gültigen Link zu Datenschutzrichtlinien enthalten. Bei Angeboten mit ungültigen, ungesicherten und fehlerhaften Links zu Datenschutzrichtlinien schlägt die App-Überprüfung fehl. Ihre Datenschutzrichtlinie muss den [Datenschutzrichtlinien](prepare/teams-store-validation-guidelines.md#privacy-policy) entsprechen.

## <a name="terms-of-use"></a>Nutzungsbedingungen

Ihr Angebotseintrag muss einen gültigen Link zu den Nutzungsbedingungen enthalten. Bei Angeboten mit ungültigen, ungesicherten und fehlerhaften Nutzungsbedingungen schlägt die App-Überprüfung fehl. Sie müssen die [Richtlinien für die Nutzungsbedingungen](prepare/teams-store-validation-guidelines.md#terms-of-use) einhalten.

## <a name="see-also"></a>Siehe auch

* [Richtlinien zur Validierung von Microsoft Teams-Speichern](prepare/teams-store-validation-guidelines.md)
* [Zertifizierungsrichtlinien für den kommerziellen Marketplace](/legal/marketplace/certification-policies)
* [Microsoft-Markenzeichen- und Markenrichtlinien](https://www.microsoft.com/legal/intellectualproperty/trademarks)
