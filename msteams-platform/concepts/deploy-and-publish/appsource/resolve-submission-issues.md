---
title: Beheben von Problemen mit Der Store-Übermittlung
description: In diesem Artikel erfahren Sie, wie Sie Probleme mit Ihrer Microsoft Teams Store-Übermittlung behandeln und beheben.
ms.topic: how-to
author: heath-hamilton
ms.author: surbhigupta
ms.localizationpriority: medium
ms.openlocfilehash: 51427f2023ba566391a3d0b544d74e5658464a7c
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66123209"
---
# <a name="resolve-issues-if-your-microsoft-teams-store-submission-fails"></a>Beheben von Problemen, wenn ihre Microsoft Teams Store-Übermittlung fehlschlägt

Apps, die im Microsoft Teams Store veröffentlicht werden, müssen die [Teams Store-Validierungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) und [richtlinien für kommerzielle Marketplaces](/legal/marketplace/certification-policies) erfüllen.

Wenn ihre Store-Übermittlung fehlschlägt, stellt Microsoft einen Concierge-Überprüfungsdienst bereit, der Ihnen hilft, Ihre App kompatibel und veröffentlicht zu machen.

## <a name="get-help-directly-from-microsoft"></a>Hilfe direkt von Microsoft erhalten

Der von Microsoft bereitgestellte Concierge-Überprüfungsdienst hilft Entwicklern, ihre Apps im Teams Store zu veröffentlichen. Im Rahmen dieses Diensts überprüft Microsoft, ob Ihre App wie beschrieben funktioniert, enthält alle geeigneten Metadaten und bietet Benutzern einen Mehrwert.

Wenn ihre App-Übermittlung fehlschlägt, sendet Microsoft Ihnen innerhalb von 24 Stunden nach der Übermittlung einen Überprüfungsbericht mit Empfehlungen.

## <a name="resolve-issues-and-resubmit-your-app"></a>Beheben von Problemen und erneutes Übermitteln der App

Sie müssen alle vom Microsoft-Concierge-Validierungsteam gemeldeten Probleme beheben, bevor Sie Ihre App erneut im Partner Center übermitteln. Der Microsoft-Bericht enthält die folgenden Informationen:

* Eine entsprechende [Validierungsrichtlinie](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) für jedes Problem.
* Anweisungen zum Reproduzieren der einzelnen Probleme.
* Empfehlungen für die Behebung jedes Problems basierend auf der öffentlich verfügbaren Entwicklerdokumentation.

Der Prozess zum Beheben von Problemen und zum erneuten Übermitteln einer App läuft in der Regel wie folgt ab:

1. Sie beheben alle Probleme im Bericht.
1. Sie senden Folgendes an das Microsoft-Concierge-Validierungsteam unter <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>:
   * Ein aktualisiertes App-Paket
   * Testen Sie Notizen für Ihre App, wenn Sie diese nicht in die ursprüngliche Übermittlung aufgenommen haben:
      * Anmeldeinformationen für mindestens zwei Konten (ein Administrator und ein Nicht-Administrator).
      * Anweisungen zum Konfigurieren der App und Zum Testen ihrer Funktionalität.
      * Ein Video, das Ihre in Teams verwendete App zeigt.
1. Das Microsoft-Concierge-Validierungsteam testet Ihre aktualisierte App vollständig.
1. Sie führen eine der folgenden Aktionen aus:
   * Wenn Ihre App frei von Problemen ist, übermitteln Sie Ihre App erneut im Partner Center.
   * Wenn Probleme nicht behoben sind oder Microsoft neue Probleme findet, erhalten Sie einen weiteren Bericht über die zu behebenden Probleme. Beheben Sie diese Probleme, und senden Sie eine aktualisierte Version der App an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

> [!CAUTION]
> Um mehrere Übermittlungsfehler zu vermeiden, übermitteln Sie Ihre App nicht erneut im Partner Center, bis das Microsoft-Concierge-Validierungsteam Ihre App genehmigt hat.

## <a name="faq"></a>Häufig gestellte Fragen

Erhalten Sie Antworten auf einige häufig gestellte Fragen beim Beheben von Problemen bei der App-Übermittlung.

<br>

<details>

<summary><b>Wie lange dauert es, meine App zu veröffentlichen?</b></summary>

Wenn ihre Store-Übermittlung keine Probleme hat, wird Ihre App innerhalb von 1 bis 2 Werktagen veröffentlicht. Wenn Ihre App fehlschlägt, bietet Ihnen ein Microsoft-Team Empfehlungen zur Behebung der Probleme. Nachdem Sie diese Korrekturen vorgenommen und eine aktualisierte App erneut an dieses Team übermittelt haben, werden Sie innerhalb von 24 Stunden benachrichtigt, wenn Ihre App zur Veröffentlichung bereit ist oder noch mehr Arbeit benötigt.

<br>

</details>

<details>

<summary><b>Gewusst wie die Wahrscheinlichkeit erhöhen, dass meine App die Übermittlung besteht?</b></summary>

Wenn Sie Folgendes ausführen, kann dies zu einer erfolgreichen Übermittlung führen:

1. Entwickeln Sie Ihre App basierend auf den [Teams Designrichtlinien](~/concepts/design/design-teams-app-overview.md).
1. Stellen Sie sicher, dass Ihre App die [Validierungsrichtlinien für Teams Store](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) und [die Zertifizierungsrichtlinien für kommerzielle Microsoft Marketplaces](/legal/marketplace/certification-policies) einhält.
1. Testen Sie Ihr App-Paket mit dem [Microsoft Teams App-Überprüfungstool](https://dev.teams.microsoft.com/appvalidation.html).
1. [Bereiten Sie ihre übermittlung Teams Store](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md) vor.

<br>

</details>

<details>

<summary><b>Meine App befindet sich in Betatests. Kann ich meine App trotzdem übermitteln, um Zeit beim Veröffentlichungsprozess zu sparen?</b></summary>

Nein. Microsoft überprüft nur produktionsfähige Apps.

<br>

</details>

<details>

<summary><b>Darf ich die teamsubm@microsoft.com E-Mail kontaktieren, bevor ich meine App zum ersten Mal im Partner Center sende?</b></summary>

Nein. Microsoft beginnt erst dann mit der Überprüfung Ihrer App, wenn Sie Ihre App zum ersten Mal im Partner Center übermitteln.

<br>

</details>

<details>

<summary><b>Ich habe eine E-Mail vom Partner Center erhalten, die besagt, dass meine App für die Veröffentlichung genehmigt wurde. Warum befindet sich meine App nicht im Teams Store?</b></summary>

Nachdem Ihre App genehmigt wurde, dauert die Veröffentlichung je nach App-Funktionen in der Regel 1 bis 2 Werktage.Wenn Ihre App nach zwei Werktagen nicht veröffentlicht wurde, wenden Sie sich an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

<br>

</details>
