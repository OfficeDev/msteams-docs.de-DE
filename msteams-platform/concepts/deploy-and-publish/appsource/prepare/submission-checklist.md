---
title: Übermittlungscheckliste
description: Die Prüfliste, die vor der Veröffentlichung Ihrer Microsoft Teams-app in AppSource verwendet werden soll
keywords: Microsoft Teams-Veröffentlichungs Speicher für Office-Veröffentlichung Checkliste Einreichung Teams apps appsource-Validierung
ms.openlocfilehash: 1b25a449901c303269334e5cea6de46fa3b6f6e5
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796302"
---
# <a name="prepare-for-appsource-submission"></a>Vorbereiten der AppSource-Übermittlung  

Um in AppSource aufgeführt zu werden, muss Ihre APP einen Genehmigungsprozess durchlaufen. Hierbei handelt es sich um einen kostenlosen Dienst, der von der Microsoft Teams-Gruppe bereitgestellt wird und überprüft, ob Ihre APP wie beschrieben funktioniert, alle geeigneten Metadaten enthält und Inhalte bereitstellt, die für einen Endbenutzer wertvoll wären. Damit Sie eine schnelle Genehmigung erhalten, müssen Sie sicherstellen, dass Ihre APP die folgenden Anforderungen und Richtlinien erfüllt:

* **Verteilungsmethode:** Stellen Sie sicher, dass Ihre APP für die Veröffentlichung auf einer Store-Plattform vorgesehen ist. Es gibt [andere Optionen](../../overview.md) zum Verteilen Ihrer APP ohne Veröffentlichung in AppSource.
* **Validierungsrichtlinien:** Ihre APP muss alle aktuellen [AppSource-Validierungsrichtlinien](https://docs.microsoft.com/legal/marketplace/certification-policies#1140-teams) vor der Übermittlung übergeben. Beachten Sie, dass diese Richtlinien Änderungen unterliegen. 
* * * Self-Test Ihrer APP mit dem [Manifest Validation-Tool](#teams-app-validation-tool) .
* **App-Detailseite:** Ihre APP muss mit der  [Prüfliste für die APP-Detailseite](detail-page-checklist.md)übereinstimmen.
* **Tipps und häufig fehlgeschlagene Fälle:** Achten Sie besonders auf die aufgelisteten [Tipps und häufig gescheiterten Fälle](frequently-failed-cases.md)  , um Ihre APP-Übermittlung und Genehmigungszeit zu verbessern.
* **App-Manifest:** Überprüfen des App-Manifests anhand der [Checkliste](app-manifest-checklist.md)für das App-Manifest.
* **Testen und Debuggen:** Stellen Sie sicher, dass Sie [Ihre APP vollständig getestet und gedebuggt](../../../build-and-test/debug.md)haben.
* **Testen von Notizen:** Einschließen der [Test Notizen zur Validierung](#test-notes-for-validation)
* **Datenschutzrichtlinien:** Stellen Sie sicher, dass Ihre [Datenschutzrichtlinien, Nutzungsbedingungen und Support-URLs](#privacy-policy-terms-of-use-and-support-urls) unseren Richtlinien entsprechen.

Wenn Sie alle oben genannten Anforderungen erfüllt haben, senden Sie Ihr Paket über das [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource)an AppSource.

## <a name="teams-app-validation-tool"></a>Teams-App-Validierungs Tool

Das App-Überprüfungstool besteht aus einer [App-Bestätigung](#teams-app-validator) und einer [vorläufigen Prüfliste](#preliminary-checklist). Das Tool repliziert dieselben Testfälle, die von [AppSource](/office/dev/store/submit-to-appsource-via-partner-center) verwendet werden, um Ihre APP-Übermittlung auszuwerten. Daher ist es wichtig, alle Testfälle vor dem Übermitteln Ihrer Lösung an AppSource zur Genehmigung zu übergeben. Das Tool kann in mehreren Bereichen innerhalb der Teams-Plattform gefunden werden:

> [!div class="checklist"]
>
> * [**Homepage der APP-Validator**](https://dev.teams.microsoft.com/appvalidation.html)
> * [**Teams Visual Studio Code Toolkit**](/toolkit/visual-studio-code-overview.md)
> * [**App Studio**](/concepts/build-and-test/app-studio-overview.md)

### <a name="teams-app-validator"></a>Teams-App-Validator

Auf der Seite über **prüfen** können Sie Ihr App-Paket vor der Übermittlung an AppSource überprüfen. Laden Sie einfach Ihr App-Paket hoch, und das Überprüfungstool überprüft Ihre APP mit allen Manifest-bezogenen Testfällen. Bei jedem fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, mit dem Sie den Fehler beheben können.

![Validierungstool](../../../../assets/images/validation-tool/validator.png)

### <a name="preliminary-checklist"></a>Vorläufige Prüfliste

Für Testszenarien, die schwierig zu automatisieren sind, werden in der vorläufigen Prüfliste sieben der am häufigsten fehlgeschlagenen Testfälle behandelt.

![Vorläufige Prüfliste](../../../../assets/images/validation-tool/preliminary-checklist.png)

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Datenschutzrichtlinien, Nutzungsbedingungen und Support-URLs

### <a name="privacy-policy"></a>Datenschutzrichtlinie

Richtlinien zur Datenschutzrichtlinie:

> [!div class="checklist"]
>
> * Die Datenschutzrichtlinie kann für Ihre APP und/oder eine allgemeine Richtlinie für alle Ihre Dienste spezifisch sein.
> * Wenn Sie eine generische Datenschutzrichtlinie verwenden, muss Sie auf "Dienste", "Anwendungen" und "Plattformen" verweisen, um Ihre Teams-APP und Ihre Website einzubeziehen.
> * Sie muss einschließen, wie Sie die Speicherung von Benutzerdaten, die Aufbewahrung von Benutzerdaten, Löschungen und Sicherheitskontrollen behandeln.
> * Sie muss Ihre Kontaktinformationen enthalten.
> * Es sollte keine fehlerhaften Links, Beta-URLs oder Staging-URLs enthalten.

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

* **Test Konten** . Ein Testkonto ist erforderlich, wenn Ihre APP lizenzierte Konten oder safelisting nur über das Back-End zulässt. Wenn in Ihrer APP ein Team/Gruppenchat Bereich zulässig ist, sind zwei Testkonten in demselben Mandanten erforderlich, um das Team Zusammenarbeitsszenario zu überprüfen.

* **Integrationsschritte** . Wenn die Vorkonfiguration durch einen mandantenadministrator erforderlich ist, um die APP zu verwenden, schließen Sie die Schritte ein, und/oder stellen Sie konfigurierte Administrator-und nicht-Administratorkonten zur Validierung bereit. Hinweis: Sie können sich für ein Abonnement für ein [Office 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden.

* **Hinweise zu den App-Features in Microsoft Teams** : detaillierte alle Funktionen, die die app in Microsoft Teams bietet, und Schritte zum Testen der einzelnen Funktionen.

* **Video mit der APP-Funktionalität (optional)** : Sie können eine Videoaufzeichnung des Produkts bereitstellen, damit wir die Funktionalität der APP vollständig verstehen.
