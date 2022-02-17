---
title: Übersicht – Teams App Store-Veröffentlichungsprozess
description: Beschreibt das Verfahren zum Übermitteln Ihrer App an Partner Center und zum Veröffentlichen der App im Microsoft Teams Store (und AppSource).
ms.topic: overview
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: eaebde76a3d1f387ba16c9fdc77670144d22fa61
ms.sourcegitcommit: 40aade608ee21f5d7d813bd145bef5736dc647f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2022
ms.locfileid: "62881651"
---
# <a name="publish-your-app-to-the-microsoft-teams-store"></a>Veröffentlichen Ihrer App im Microsoft Teams Store

Sie können Ihre App direkt an den Store innerhalb Microsoft Teams verteilen und Millionen von Benutzern auf der ganzen Welt erreichen. Wenn Ihre App auch im Store enthalten ist, können Sie potenzielle Kunden sofort erreichen.

Im Teams Store veröffentlichte Apps werden auch automatisch auf [Microsoft AppSource](https://appsource.microsoft.com) aufgeführt, dem offiziellen Marketplace für Microsoft 365 Apps und Lösungen.

## <a name="understand-the-publishing-process"></a>Grundlegendes zum Veröffentlichungsprozess

Wenn Sie den Eindruck haben, dass Ihre App bereit für die Produktion ist, können Sie damit beginnen, sie im Teams Store zu veröffentlichen.

> [!TIP]
> Wenn Sie die Schritte vor der Übermittlung genau befolgen, kann dies die Möglichkeit erhöhen, dass Microsoft Ihre App für die Veröffentlichung genehmigt.

:::row:::
   :::column span="":::
      
   :::column-end:::
   :::column span="3":::
      :::image type="content" source="../../../assets/images/submission/teams-app-store-publish-process.png" alt-text="Teams App Store-Veröffentlichungsprozess" lightbox="../../../assets/images/submission/teams-app-store-publish-process.png":::
   :::column-end:::
   :::column span="":::
      
   :::column-end:::
:::row-end:::

1. [Überprüfen Sie die Teams Store-Validierungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md), um sicherzustellen, dass Ihre App Teams App- und Store-Standards erfüllt.

1. [Erstellen Sie ein Partner Center-Entwicklerkonto](~/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md).

1. [Bereiten Sie Ihre Store-Übermittlung vor](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md). Dazu gehören das Ausführen automatisierter Tests, das Kompilieren von Testnotizen, das Erstellen eines Store-Eintrags sowie andere wichtige Aufgaben, um den Überprüfungsprozess zu beschleunigen.

1. [Übermitteln Sie Ihre App](/office/dev/store/add-in-submission-guide) über Partner Center.

1. Wenn Ihre Übermittlung fehlschlägt, wenden Sie sich direkt an Microsoft, um [die Probleme zu beheben, und übermitteln Sie Ihre App erneut](~/concepts/deploy-and-publish/appsource/resolve-submission-issues.md).

## <a name="what-to-expect-after-you-submit-your-app"></a>Was ist nach dem Übermitteln ihrer App zu erwarten?

* **Umfassende Funktions- und Erfahrungstests**

  Ihre App wird von einem Validator sorgfältig überprüft, um die Einhaltung der [Zertifizierungsrichtlinien für den Microsoft Commercial Marketplace](/legal/marketplace/certification-policies) sicherzustellen, wobei der Schwerpunkt auf umfassenden Funktions- und Benutzerfreundlichkeitstests, Benutzerfreundlichkeitsprüfungen und Metadatenüberprüfungen liegt. Die App-Überprüfung wird auf Desktop-, Web- und mobilen Clients durchgeführt.

* **Veröffentlichung der geführten App über den Service**

  Wenn keine Probleme mit Ihrer App auftreten, wird Ihre App genehmigt und im Teams Store veröffentlicht. Wenn Probleme auftreten, erhalten Sie einen automatisierten Überprüfungsbericht vom Partner Center mit den Fehlerdetails. Um Ihnen zu helfen, Ihre App erfolgreich im Teams Store zu veröffentlichen und Sie durch diesen Prozess zu führen, sendet Ihnen das Validierungsteam eine personalisierte E-Mail von unserem [Service teamsubm@microsoft.com](mailto:teamsubm@microsoft.com), die die folgenden Informationen enthält:

   * Zusammenfassung aller Probleme

   * Details zu Fehlern oder Problemen mit Richtlinienlinks und Kategorisierung: 

     * Obligatorische Korrektur: Diese Probleme müssen vor der App-Genehmigung behoben werden.

     * Empfohlene Lösung: Diese Probleme können nach der App-Genehmigung behoben werden, da dies Empfehlungen zur Verbesserung der App-Erfahrung sind.

     * Blocker: Diese Probleme verhindern, dass das Validierungsteam Ihre App-Funktionen weiter testet, und müssen behoben werden, damit die Überprüfung fortgesetzt werden kann.

     * Abfrage: Diese Abfragen können freigegeben werden, um Antworten auf bestimmte Fragen im Zusammenhang mit Ihrer App zu erhalten.

   * Schritte zum Neuerstellen von Problemen durch schriftliche Anweisungen oder das Videoformat.

   * Empfehlungen, um die gemeldeten Probleme mit Links zu Anleitungsdokumenten zu beheben.
 
  Nachdem Sie die Liste der Probleme überprüft haben, beheben Sie alle gemeldeten Probleme, und geben Sie das aktualisierte App-Paket per E-Mail frei, damit das Validierungsteam Ihre App gründlich erneut überprüft. Wenn Sie Abfragen im Zusammenhang mit den gemeldeten Problemen haben, wenden Sie sich unter [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com) an das Validierungsteam.

  Wenn in Ihrer App Probleme verbleiben oder Regressionsprobleme auftreten, gibt das Validierungsteam einen aktualisierten Validierungsbericht für Sie frei. Wenn Ihre App Blocker hatte, werden möglicherweise neue Probleme gemeldet, wenn Ihre App überprüft wird, nachdem die Blocker behoben wurden. Manchmal hat das Überprüfungsteam auch Regressionsprobleme in Apps nach der Bereitstellung von Fixes bemerkt. Es dauert einige erneute Übermittlungen, um alle Probleme für eine App zu schließen, die aus Fehlern besteht, und die Genehmigung für die Veröffentlichung im Teams Store zu erhalten.

  Nachdem alle gemeldeten Probleme geschlossen wurden und die endgültige Übermittlung im Partner Center erfolgt ist, genehmigt und veröffentlicht das Validierungsteam Ihre App. Lassen Sie zu, dass die App mindestens einen Arbeitstag im Teams Store verfügbar ist.

## <a name="tips-for-rapid-approval-to-publish-your-app"></a>Tipps zur schnellen Genehmigung der Veröffentlichung Ihrer App

* **Während der Entwurfsphase**

  Überprüfen Sie die [Richtlinien für die Store-Validierung](prepare/teams-store-validation-guidelines.md) frühzeitig im Lebenszyklus Ihrer App (Entwurfsphase), um sicherzustellen, dass Sie Ihre App entsprechend den Store-Anforderungen erstellen. Wenn Sie Ihre App gemäß diesen Richtlinien erstellen, werden dadurch aufgrund der Nichteinhaltung von Store-Richtlinien keine Überarbeitungen ausgeführt.

* **Vor der App-Übermittlung**

  1. [Erstellen Sie Ihr Partner Center-Konto](prepare/create-partner-center-dev-account.md) bereits im Voraus. Wenn Sie probleme mit Ihrem [Partner Center-Konto](prepare/create-partner-center-dev-account.md) haben, erstellen Sie ein [Supportticket](/azure/marketplace/partner-center-portal/support).

  1. Überprüfen Sie erneut die Richtlinien für die [Store-Validierung](prepare/teams-store-validation-guidelines.md) , um sicherzustellen, dass Ihre App den Store-Anforderungen entspricht. Dies trägt dazu bei, die Anzahl der in Ihrer App festgestellten Probleme zu verringern und folglich die Zeit für die Genehmigung Ihrer App zu reduzieren.

  1. Testen und erneutes Testen Ihrer App:

     1. Überprüfen Sie Ihr App-Paket mithilfe des Teams [Entwicklerportals](https://dev.teams.microsoft.com/home), um Paketfehler zu identifizieren und zu beheben.

        :::image type="content" source="../../../assets/images/submission/teams-validation-developer-portal.png" alt-text="Speicherüberprüfung":::
 
     1. Testen Sie Ihre App sorgfältig vor der App-Übermittlung, um sicherzustellen, dass sie den Store-Richtlinien entspricht. Laden Sie die App in Teams quer, und testen Sie die End-to-End-Benutzerabläufe für Ihre App. Stellen Sie sicher, dass die Funktionalität wie erwartet funktioniert, Links nicht beschädigt sind, die Benutzeroberfläche nicht blockiert wird und alle Einschränkungen deutlich hervorgehoben sind.

     1. Testen Sie Ihre App auf Desktop-, Web- und mobilen Clients. Stellen Sie sicher, dass die App über verschiedene Formfaktoren hinweg reaktionsfähig ist.

  1. Führen Sie die [Herausgeberüberprüfung](/azure/active-directory/develop/publisher-verification-overview) aus, bevor Sie Ihre App übermitteln. Wenn Probleme auftreten, können Sie ein [Supportticket](/azure/marketplace/partner-center-portal/support) für die Lösung erstellen.

  1. Befolgen Sie bei der Vorbereitung der App-Übermittlung [die Checkliste](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/submission-checklist) , und fügen Sie die folgenden Details als Teil Ihres Übermittlungspakets ein:

      1. Sorgfältig überprüftes App-Paket.

      1. Benutzeranmeldeinformationen für Arbeitsadministratoren und Benutzer, die keine Administratoren sind, um Ihre App-Funktionalität zu testen (wenn Ihre App ein Premiumabonnementmodell bietet).

      1. Testanweisungen, die die App-Funktionalität und die unterstützten Szenarien detailliert beschreiben.

      1. Einrichtungsanweisungen, wenn ihre App eine zusätzliche Konfiguration für den Zugriff auf app-Funktionen erfordert. Wenn Ihre App eine komplexe Konfiguration erfordert, können Sie alternativ auch einen [bereitgestellten Demomandanten](/office/developer-program/microsoft-365-developer-program-get-started) mit Administratorzugriff bereitstellen, damit unsere Validierer die Konfigurationsschritte überspringen können.

      1. Link zu einem Demo-Video-Aufzeichnungsschlüssel-Benutzerablauf für Ihre App. Dies wird dringend empfohlen.

* **Posten der App-Übermittlung**

  * Nachdem Sie den Überprüfungsbericht überprüft haben, antworten Sie mit allen Abfragen im Zusammenhang mit dem Überprüfungsbericht auf den E-Mail-Thread, oder wenn Sie zusätzliche Unterstützung benötigen, um die gemeldeten Probleme zu beheben.

  * Stellen Sie sicher, dass Sie über eine ausreichende Entwicklerbandbreite verfügen, um alle gemeldeten Probleme zu beheben, bis die App genehmigt wurde.

  * Stellen Sie sicher, dass Sie [alle Probleme behoben](/microsoftteams/platform/concepts/deploy-and-publish/appsource/resolve-submission-issues) haben, die ihnen vom Service [teamsubm@microsoft.com](mailto:teamsubm@microsoft.com) gemeldet wurden, bevor Sie Ihr App-Paket für weitere Tests freigeben. Dies reduziert die Anzahl der Iterationen, die zum Überprüfen Ihrer App erforderlich sind, und folglich die Zeit für die Genehmigung Ihrer App.
  
  * Vermeiden Sie es, die App-Funktionalität während des Überprüfungsprozesses zu ändern. Dies kann zur Ermittlung neuer Probleme führen und die Zeit für die Genehmigung Ihrer App erhöhen.

## <a name="see-also"></a>Siehe auch

* [Veröffentlichen in Microsoft 365 App Stores](/office/dev/store/)
* [Hochladen Ihrer Teams-App](~/concepts/deploy-and-publish/apps-upload.md)
* [Veröffentlichen Ihrer Teams-App in Ihrer Organisation](/MicrosoftTeams/tenant-apps-catalog-teams?toc=/microsoftteams/platform/toc.json&bc=/MicrosoftTeams/breadcrumb/toc.json)
* [Planen der Onboarding-Erfahrung für Benutzer](../../design/understand-use-cases.md#plan-the-onboarding-experience)
* [Verteilen von Registerkarten-Apps auf mobilgeräten](../../../tabs/design/tabs-mobile.md#distribution)
* [Testvorschau für monetarisierte Apps](prepare/Test-preview-for-monetized-apps.md)
