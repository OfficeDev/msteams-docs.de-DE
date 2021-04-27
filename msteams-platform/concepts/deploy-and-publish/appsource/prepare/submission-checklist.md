---
title: Prüfliste für die Speicherübermittlung
description: Die Prüfliste vor der Veröffentlichung Ihrer Microsoft Teams-App in AppSource
ms.topic: reference
localization_priority: Normal
keywords: teams publish store office publishing checklist submission Teams apps appsource validation
ms.openlocfilehash: 1e7698e143d313ce46b834eada608571e3280b8a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020786"
---
# <a name="prepare-for-appsource-submission"></a>Vorbereiten der AppSource-Übermittlung  

Um in AppSource aufgeführt zu werden, muss Ihre App einen Genehmigungsprozess durchgehen. Dies ist ein kostenloser Dienst, der von der Microsoft Teams-Gruppe bereitgestellt wird und überprüft, ob Ihre App wie beschrieben funktioniert, alle entsprechenden Metadaten enthält und Inhalte zur Verfügung stellt, die für einen Endbenutzer von Nutzen wären. Stellen Sie sicher, dass Ihre App die folgenden Anforderungen und Richtlinien erfüllt, um eine schnelle Genehmigung zu erreichen:

* **Verteilungsmethode:** Stellen Sie sicher, dass Ihre App für die Veröffentlichung auf einer Storeplattform gedacht ist. Es gibt [weitere Optionen zum](../../overview.md) Verteilen Ihrer App ohne Veröffentlichung an AppSource.
* **Validierungsrichtlinien:** Ihre App muss alle aktuellen [AppSource-Validierungsrichtlinien vor der](https://docs.microsoft.com/legal/marketplace/certification-policies#1140-teams) Übermittlung übergeben. 
  > [!NOTE] 
  > Die Appsource-Validierungsrichtlinien können geändert werden.
* **Mobile Bereitschaft:** Ihre App muss mobil reagieren. Wenn Ihre App Registerkarten enthält, [](~/tabs/design/tabs-mobile.md) muss sie die Richtlinien für das mobile Design befolgen, und Ihre App muss keine [Upsellanforderungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#-mobile-responsiveness-no-direct-upsell-or-payment) für mobile Betriebssysteme (iOS und Android) erfüllen.
* **Testen Sie Ihre App selbst:** Testen Sie Ihre App mithilfe des [Manifestüberprüfungstools](#teams-app-validation-tool).
* **App-Detailseite:** Ihre App muss sich an der [Prüfliste für die App-Detailseite ausrichten.](detail-page-checklist.md)
* **Tipps und häufig fehlgeschlagene Fälle:** Achten Sie besonders auf die aufgeführten Tipps und häufig fehlgeschlagenen [Fälle,](frequently-failed-cases.md)  um Ihre App-Übermittlungs- und Genehmigungszeit zu verbessern.
* **App-Manifest:** Überprüfen Sie Ihr App-Manifest anhand der [Prüfliste für das App-Manifest.](app-manifest-checklist.md)
* **Testen und Debuggen:** Stellen Sie sicher, dass Sie Ihre App vollständig getestet [und debuggt haben.](../../../build-and-test/debug.md)
* **Testhinweise:** Fügen Sie Ihre [Testnotizen für die Überprüfung ein.](#test-notes-for-validation)
* **Datenschutzrichtlinien:** Stellen Sie [sicher, dass Ihre Datenschutzrichtlinien, Nutzungsbedingungen und Support-URLs](#privacy-policy-terms-of-use-and-support-urls) unseren Richtlinien entsprechen.

Nachdem Sie alle oben genannten Anforderungen erfüllt haben, übermitteln Sie Ihr Paket über Partner Center an [AppSource.](/office/dev/store/use-partner-center-to-submit-to-appsource)

## <a name="teams-app-validation-tool"></a>Teams App Validation Tool

Das App-Validierungstool besteht aus einem [App-Validator](#teams-app-validator) und einer [vorläufigen Prüfliste.](#preliminary-checklist) Das Tool repliziert dieselben Testfälle, die von [AppSource](/office/dev/store/submit-to-appsource-via-partner-center) verwendet werden, um Ihre App-Übermittlung auszuwerten. Daher ist es wichtig, alle Testfälle zu bestehen, bevor Ihre Lösung zur Genehmigung an AppSource übermittelt wird. Das Tool kann in mehreren Bereichen der Teams-Plattform gefunden werden:

> [!div class="checklist"]
>
> * [**App-Validator-Homepage**](https://dev.teams.microsoft.com/appvalidation.html)
> * [**Teams Visual Studio Code Toolkit**](/toolkit/visual-studio-code-overview.md)
> * [**App-Studio**](../../../build-and-test/app-studio-overview.md)

### <a name="teams-app-validator"></a>Teams-App-Validator

Auf **der Seite Überprüfen** können Sie Ihr App-Paket vor der Übermittlung an AppSource überprüfen. Laden Sie einfach Ihr App-Paket hoch, und das Überprüfungstool überprüft Ihre App mit allen manifestbezogenen Testfällen. Für jeden fehlgeschlagenen Test enthält die Beschreibung einen Dokumentationslink, mit dem Sie den Fehler beheben können.

![Überprüfungstool](../../../../assets/images/validation-tool/validator.png)

### <a name="preliminary-checklist"></a>Vorläufige Prüfliste

Bei schwierig zu automatisierenden Testszenarien werden in der vorläufigen Prüfliste sieben der am häufigsten fehlgeschlagenen Testfälle angezeigt.

![Vorläufige Prüfliste](../../../../assets/images/validation-tool/preliminary-checklist.png)

## <a name="privacy-policy-terms-of-use-and-support-urls"></a>Datenschutzrichtlinien, Nutzungsbedingungen und Support-URLs

### <a name="privacy-policy"></a>Datenschutzrichtlinien

Richtlinien für Datenschutzrichtlinien:

> [!div class="checklist"]
>
> * Die Datenschutzrichtlinie kann spezifisch für Ihre App und/oder eine allgemeine Richtlinie für alle Ihre Dienste sein.
> * Wenn Sie eine allgemeine Datenschutzrichtlinie verwenden, muss sie auf "Dienste", "Anwendungen" und "Plattformen" verweisen, um Ihre Teams-App sowie Ihre Website zu enthalten.
> * Sie muss die Verarbeitung von Benutzerdatenspeicherung, Benutzerdatenaufbewahrung, Löschung und Sicherheitskontrollen umfassen.
> * Sie muss Ihre Kontaktinformationen enthalten.
> * Es sollte keine beschädigten Links, Beta-URLs oder Staging-URLs enthalten.

### <a name="terms-of-use"></a>Nutzungsbedingungen

Ihre Nutzungsbedingungen-Anweisung sollte spezifisch sein und auf Ihr App- und/oder Add-In-Angebot anwendbar sein.

### <a name="support-urls"></a>Unterstützen von URLs

Ihre Support-URLs sollten keine Authentifizierungs- oder Anmeldeinformationen erfordern, um Sie bei Problemen mit Ihrer App zu kontaktieren.

## <a name="test-notes-for-validation"></a>Testhinweise zur Überprüfung

Geben Sie folgendes an:

* Sie müssen mindestens zwei Anmeldeinformationen angeben, einen Administrator und einen Nicht-Administrator.

* Zu Überprüfungszwecken sollten die von Ihnen zur Verfügung gestellten Konten über ausreichende vorab ausgefüllte Daten verfügen.

* Für Unternehmens-Apps, Apps, in denen ein Abonnement erforderlich ist, oder Apps, bei denen eine Office 365-Mandanten-/Domänenabhängigkeit besteht, müssen Sie ein drittes Konto in derselben Domäne bereitstellen, das nicht für Ihre App vorkonfiguriert ist, damit wir die Benutzererfahrung der ersten Ausführung überprüfen können.

* Wenn Ihre App über Premium-/Upgradefeatures verfügt, muss ein Konto mit dem erforderlichen Zugriff bereitgestellt werden, um diese Erfahrung zu testen.

* Sie können Ihre Testnotizen in SharePoint hochladen. Wenn ja, geben Sie einen öffentlichen Link zur Datei an.

* **Testkonten**. Ein Testkonto ist erforderlich, wenn Ihre App nur lizenzierte Konten oder listensichere Listen aus dem Back-End zulässt. Wenn in Ihrer App ein Team-/Gruppenchatbereich zulässig ist, sind außerdem zwei Testkonten im gleichen Mandanten erforderlich, um das Szenario für die Teamzusammenarbeit zu überprüfen.

* **Integrationsschritte**. Wenn für die Verwendung der App eine Vorkonfiguration durch einen Mandantenadministrator erforderlich ist, müssen Sie die Schritte ausführen und/oder konfigurierte Administrator- und Nicht-Admin-Konten zur Überprüfung bereitstellen. Hinweis: Sie können sich für ein [Office 365 Developer Program-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist *für* 90 Tage kostenlos und wird kontinuierlich verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.

* **Hinweise zu den App-Features in Teams:** Detaillierte Informationen zu allen Funktionen, die die App in Teams bietet, und Schritte zum Testen der einzelnen Features.

* **Video mit der App-Funktionalität (Optional):** Sie können eine Videoaufzeichnung des Produkts bereitstellen, damit wir die Funktionalität der App vollständig verstehen können.
