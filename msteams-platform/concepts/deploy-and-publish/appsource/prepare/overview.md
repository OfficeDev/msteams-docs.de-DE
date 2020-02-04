---
title: Übermittlungscheckliste
description: Die Prüfliste, die vor der Veröffentlichung Ihrer Microsoft Teams-app in AppSource verwendet werden soll
keywords: Vorbereiten der Veröffentlichung von Microsoft Teams-Veröffentlichungs Speicher-Prüflisten Übermittlung
ms.openlocfilehash: b79e92b5cf8de01ec19c26c63814c6a6ae1e9a09
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674164"
---
# <a name="prepare-for-appsource-submission"></a>Vorbereiten der AppSource-Übermittlung  

Um in AppSource aufgeführt zu werden, muss Ihre APP einen Genehmigungsprozess durchlaufen. Hierbei handelt es sich um einen kostenlosen Dienst, der von der Microsoft Teams-Gruppe bereitgestellt wird und überprüft, ob Ihre APP wie beschrieben funktioniert, alle geeigneten Metadaten enthält und Inhalte bereitstellt, die für einen Endbenutzer wertvoll wären. Damit Sie eine schnelle Genehmigung erhalten, müssen Sie sicherstellen, dass Ihre APP die folgenden Anforderungen und Richtlinien erfüllt:

* **Verteilungsmethode:** Stellen Sie sicher, dass Ihre APP für einen Store bestimmt ist. Es gibt [andere Optionen](../../overview.md) zum Verteilen Ihrer APP ohne Veröffentlichung in AppSource.
* **App-Detailseite:** Ihre APP erfüllt die [Prüfliste für die APP-Detailseite](detail-page-checklist.md)
* **Tipps und häufig fehlgeschlagene Fälle:** Achten Sie besonders auf diese [Tipps und häufig fehlgeschlagene Fälle](frequently-failed-cases.md) , um Ihre APP-Übermittlung in die Genehmigungszeit zu verbessern.
* **App-Manifest:** Überprüfen des App-Manifests anhand der [Checkliste](app-manifest-checklist.md) für das App-Manifest und der manifestprüfung in App Studio
* **Testen und Debuggen:** Sie haben [Ihre APP vollständig getestet und gedebuggt](../../../build-and-test/debug.md).
* **Validierungsrichtlinien:** Sie muss alle aktuellen [AppSource-Validierungsrichtlinien](https://dev.office.com/officestore/docs/validation-policies) für Microsoft Teams-Registerkarten und Bots übergeben. Beachten Sie, dass diese Richtlinien Änderungen unterliegen.
* **Testen von Notizen:** Einschließen [von Test Notizen zur Validierung](#test-notes-for-validation)
* **Datenschutzrichtlinien:** Stellen Sie sicher, dass Ihre [Datenschutzrichtlinien, Nutzungsbedingungen und Support-URLs](#privacy-policy-terms-of-use-and-support-urls) unseren Richtlinien entsprechen.

Nachdem Sie alle oben genannten Anforderungen erfüllt haben, können Sie Ihr Paket über das [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource)an die APP-Quelle übermitteln.

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Datenschutzrichtlinien, Nutzungsbedingungen und Support-URLs

### <a name="privacy-policy"></a>Datenschutzrichtlinie

Richtlinien zur Datenschutzrichtlinie:
* Die Datenschutzrichtlinie kann entweder für Ihre APP und/oder für Ihr Add-in spezifisch sein oder für alle Ihre Dienste eine allgemeine Richtlinie. 
* Wenn Sie eine generische Datenschutzrichtlinie verwenden, muss Sie auf "Dienste/Anwendungen/Plattformen" verweisen, um Ihre Teams-APP und Ihre Website abzudecken. 
* Es muss einschließen, wie Sie Benutzerdaten Speicherung, Speicherung von Benutzerdaten, Löschungen und Sicherheits Kontrollinformationen behandeln.
* Sie muss Ihre Kontaktinformationen enthalten.
* Es sollte keine fehlerhaften Links, Beta-URLs oder Staging-URLs enthalten. 


### <a name="terms-of-use"></a>Nutzungsbedingungen

Ihre Nutzungsbedingungen-Anweisung sollte spezifisch sein und auf Ihre APP und/oder Ihr Add-in-Angebot zutreffen.

### <a name="support-urls"></a>Support-URLs

Für Ihre Support-URLs sollten keine Authentifizierungs-oder Anmeldeinformationen erforderlich sein, um Sie bei Problemen mit Ihrer APP zu kontaktieren.

## <a name="test-notes-for-validation"></a>Testen von Notizen zur Überprüfung

Sie müssen mindestens zwei Anmeldeinformationen angeben, einen Administrator und einen nicht, damit Ihre APP überprüft werden kann.

* Für die von Ihnen bereitgestellten Konten sollten zu Überprüfungszwecken ausreichende Daten vorinstalliert sein.
* Für Enterprise-apps, apps, bei denen ein Abonnement erforderlich ist oder bei denen eine Office 365-Mandanten/Domänen Abhängigkeit für Tests vorhanden ist, müssen Sie ein drittes Konto in derselben Domäne bereitstellen, die noch nicht für die Verwendung Ihrer APP konfiguriert ist, damit wir die Benutzeroberfläche mit der ersten Ausführung überprüfen können.
* Wenn Ihre APP über Premium/Upgrade-Funktionen verfügt, muss ein Konto mit dem erforderlichen Zugriff bereitgestellt werden, um diese Erfahrung zu testen.
* Sie haben die Möglichkeit, Ihre Test Notizen in SharePoint hochzuladen. Geben Sie in diesen Fällen einen öffentlichen Link zur Datei an.
