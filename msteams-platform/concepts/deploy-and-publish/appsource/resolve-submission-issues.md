---
title: Beheben von Problemen mit Ihrer Store-Übermittlung
description: Erfahren Sie, wie Sie Probleme mit Ihrer Microsoft Teams Store-Übermittlung behandeln und beheben.
ms.topic: how-to
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: none
ms.openlocfilehash: 39ab797bf87638e107f55e8b83d002372a4261f5
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156806"
---
# <a name="resolve-issues-if-your-microsoft-teams-store-submission-fails"></a>Beheben von Problemen, wenn die Übermittlung Microsoft Teams Store fehlschlägt

Apps, die im Microsoft Teams Store veröffentlicht werden, müssen den [Teams Store-Validierungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) und den Richtlinien für [den kommerziellen Marketplace](/legal/marketplace/certification-policies)entsprechen.

Wenn Ihre Store-Übermittlung fehlschlägt, bietet Microsoft einen Überprüfungsdienst an, mit dem Ihre App kompatibel und veröffentlicht werden kann.

## <a name="get-help-directly-from-microsoft"></a>Hilfe direkt von Microsoft erhalten

Der von Microsoft bereitgestellte Überprüfungsdienst hilft Entwicklern, ihre Apps im Teams Store zu veröffentlichen. Als Teil dieses Diensts überprüft Microsoft, ob Ihre App wie beschrieben funktioniert, enthält alle entsprechenden Metadaten und bietet Benutzern einen Wert.

Wenn Ihre App-Übermittlung fehlschlägt, sendet Microsoft Ihnen innerhalb von 24 Stunden nach der Übermittlung einen Prüfbericht mit Empfehlungen.

## <a name="resolve-issues-and-resubmit-your-app"></a>Beheben von Problemen und erneutes Übermitteln Ihrer App

Sie müssen alle probleme beheben, die vom Microsoft-Validierungsteam gemeldet wurden, bevor Sie Ihre App erneut im Partner Center übermitteln. Der Microsoft-Bericht enthält die folgenden Informationen:

* Eine entsprechende [Validierungsrichtlinie](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) für jedes Problem.
* Anweisungen zum Reproduzieren der einzelnen Probleme.
* Empfehlungen, um jedes Problem basierend auf der öffentlich verfügbaren Entwicklerdokumentation zu beheben.

Der Prozess zum Beheben von Problemen und zum erneuten Übermitteln einer App sieht in der Regel wie folgt aus:

1. Sie beheben alle Probleme im Bericht.
1. Sie senden Folgendes an das Microsoft-Validierungsteam bei <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com:</a>
   * Ein aktualisiertes App-Paket
   * Testnotizen für Ihre App, wenn Sie diese nicht in Ihre ursprüngliche Übermittlung aufgenommen haben:
      * Anmeldeinformationen für mindestens zwei Konten (ein Administrator und ein Nicht-Administrator).
      * Anweisungen zum Konfigurieren der App und Testen der Funktionalität.
      * Ein Video, das Ihre in Teams verwendete App zeigt.
1. Das Microsoft-Validierungsteam testet Ihre aktualisierte App vollständig.
1. Sie führen eine der folgenden Aktionen aus:
   * Wenn Ihre App frei von Problemen ist, übermitteln Sie Ihre App erneut im Partner Center.
   * Wenn Probleme nicht behoben werden oder Microsoft neue Probleme findet, erhalten Sie einen weiteren Bericht darüber, was behoben werden soll. Beheben Sie diese Probleme, und senden Sie eine aktualisierte Version der App an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

> [!CAUTION]
> Um mehrere Übermittlungsfehler zu vermeiden, übermitteln Sie Ihre App erst dann erneut im Partner Center, nachdem das Microsoft-Team für die Validierung Ihrer App ihre App genehmigt hat.

## <a name="faq"></a>Häufig gestellte Fragen

Erhalten Sie Antworten auf einige häufig gestellte Fragen bei der Lösung von Problemen bei der App-Übermittlung.

<br>

<details>

<summary><b>Wie lange dauert die Veröffentlichung meiner App?</b></summary>

Wenn Ihre Store-Übermittlung keine Probleme hat, wird Ihre App innerhalb von 1-2 Werktagen veröffentlicht. Wenn Ihre App fehlschlägt, bietet Ihnen ein Microsoft-Team Empfehlungen, um die Probleme zu beheben. Nachdem Sie diese Korrekturen vorgenommen und eine aktualisierte App an dieses Team erneut gesendet haben, werden Sie in 24 Stunden benachrichtigt, wenn Ihre App veröffentlichen kann oder noch mehr Arbeit benötigt.

<br>

</details>

<details>

<summary><b>Wie kann ich die Wahrscheinlichkeit erhöhen, dass meine App die Übermittlung übergibt?</b></summary>

Folgendes kann zu einer erfolgreichen Übermittlung führen:

1. Entwickeln Sie Ihre App basierend auf den [Teams Entwurfsrichtlinien.](~/concepts/design/design-teams-app-overview.md)
1. Stellen Sie sicher, dass Ihre App den Teams Richtlinien für [die Store-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) und den Zertifizierungsrichtlinien für [den kommerziellen Microsoft-Marketplace](/legal/marketplace/certification-policies)entspricht.
1. Testen Sie Ihr App-Paket mit dem [Microsoft Teams App-Überprüfungstool.](https://dev.teams.microsoft.com/appvalidation.html)
1. [Bereiten Sie ihre Teams Store-Übermittlung vor.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)

<br>

</details>

<details>

<summary><b>Meine App befindet sich im Betatest. Kann ich meine App trotzdem übermitteln, um Zeit beim Veröffentlichungsprozess zu sparen?</b></summary>

Nein. Microsoft überprüft nur produktionsbereite Apps.

<br>

</details>

<details>

<summary><b>Kann ich die teamsubm@microsoft.com E-Mail kontaktieren, bevor ich meine App zum ersten Mal im Partner Center absenden kann?</b></summary>

Nein. Microsoft beginnt erst mit der Überprüfung Ihrer App, wenn Sie Ihre App zum ersten Mal im Partner Center übermitteln.

<br>

</details>

<details>

<summary><b>Ich habe eine E-Mail vom Partner Center erhalten, dass meine App für die Veröffentlichung genehmigt wurde. Warum befindet sich meine App nicht im Teams Store?</b></summary>

Sobald Ihre App genehmigt wurde, dauert die Veröffentlichung in der Regel 1-2 Werktage, je nach den Funktionen der App.Wenn Ihre App nach zwei Werktagen nicht veröffentlicht wurde, wenden Sie sich an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

<br>

</details>
