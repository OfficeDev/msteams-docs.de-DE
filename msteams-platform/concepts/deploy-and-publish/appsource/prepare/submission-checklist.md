---
title: Übermittlungscheckliste
description: Die Prüfliste, die vor der Veröffentlichung Ihrer Microsoft Teams-app in AppSource verwendet werden soll
keywords: Vorbereiten der Veröffentlichung von Microsoft Teams-Veröffentlichungs Speicher-Prüflisten Übermittlung
ms.openlocfilehash: 3379fe670c9835c1f2223067592d9574fff83a69
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "44801300"
---
# <a name="prepare-for-appsource-submission"></a>Vorbereiten der AppSource-Übermittlung  

Um in AppSource aufgeführt zu werden, muss Ihre APP einen Genehmigungsprozess durchlaufen. Hierbei handelt es sich um einen kostenlosen Dienst, der von der Microsoft Teams-Gruppe bereitgestellt wird und überprüft, ob Ihre APP wie beschrieben funktioniert, alle geeigneten Metadaten enthält und Inhalte bereitstellt, die für einen Endbenutzer wertvoll wären. Damit Sie eine schnelle Genehmigung erhalten, müssen Sie sicherstellen, dass Ihre APP die folgenden Anforderungen und Richtlinien erfüllt:

* **Verteilungsmethode:** Stellen Sie sicher, dass Ihre APP für einen Store bestimmt ist. Es gibt [andere Optionen](../../overview.md) zum Verteilen Ihrer APP ohne Veröffentlichung in AppSource.
* **App-Detailseite:** Ihre APP erfüllt die [Prüfliste für die APP-Detailseite](detail-page-checklist.md)
* **Tipps und häufig fehlgeschlagene Fälle:** Achten Sie besonders auf diese [Tipps und häufig fehlgeschlagene Fälle](frequently-failed-cases.md) , um Ihre APP-Übermittlung in die Genehmigungszeit zu verbessern.
* **App-Manifest:** Überprüfen des App-Manifests anhand der [Checkliste](app-manifest-checklist.md) für das App-Manifest und der manifestprüfung in App Studio
* **Testen und Debuggen:** Sie haben [Ihre APP vollständig getestet und gedebuggt](../../../build-and-test/debug.md).
* **Validierungsrichtlinien:** Sie muss alle aktuellen [AppSource-Validierungsrichtlinien](https://docs.microsoft.com/legal/marketplace/certification-policies#1140-teams) für Microsoft Teams-Registerkarten und Bots übergeben. Beachten Sie, dass diese Richtlinien Änderungen unterliegen.
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

Fügen Sie Folgendes ein:

* Sie müssen mindestens zwei Anmeldeinformationen angeben: einen Administrator und einen nicht-Administrator.

* Zu Überprüfungszwecken sollten die von Ihnen bereitgestellten Konten über ausreichende vorab aufgefüllte Daten verfügen.

* Für Enterprise-apps, apps, bei denen ein Abonnement erforderlich ist, oder apps, bei denen es sich um eine Office 365 Mandanten/Domänen Abhängigkeit handelt, müssen Sie ein drittes Konto in derselben Domäne bereitstellen, die für Ihre APP nicht vorkonfiguriert ist, damit wir die Benutzeroberfläche mit der ersten Ausführung überprüfen können.

* Wenn Ihre APP über Premium/Upgrade-Funktionen verfügt, muss ein Konto mit dem erforderlichen Zugriff bereitgestellt werden, um diese Erfahrung zu testen.

* Sie haben die Möglichkeit, Ihre Test Notizen in SharePoint hochzuladen. Geben Sie in diesem Fall einen öffentlichen Link zur Datei an.

* **Test Konten**. Ein Testkonto ist erforderlich, wenn Ihre APP nur lizenzierte Konten oder Whitelists aus dem Back-End zulässt. Wenn in Ihrer APP ein Team/Gruppenchat Bereich zulässig ist, sind zwei Testkonten in demselben Mandanten erforderlich, um das Team Zusammenarbeitsszenario zu überprüfen.

* **Integrationsschritte**. Wenn die Vorkonfiguration durch einen mandantenadministrator erforderlich ist, um die APP zu verwenden, schließen Sie die Schritte ein, und/oder stellen Sie konfigurierte Administrator-und nicht-Administratorkonten zur Validierung bereit. Hinweis: Sie können sich für ein Abonnement für ein [Office 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden.

* **Hinweise zu den App-Features in Microsoft Teams**: detaillierte alle Funktionen, die die app in Microsoft Teams bietet, und Schritte zum Testen der einzelnen Funktionen.

* **Video mit der APP-Funktionalität (optional)**: Sie können eine Videoaufzeichnung des Produkts bereitstellen, damit wir die Funktionalität der APP vollständig verstehen.



