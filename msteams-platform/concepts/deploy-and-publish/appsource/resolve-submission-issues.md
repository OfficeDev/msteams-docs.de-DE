---
title: Beheben von Problemen mit Ihrer Shop-Übermittlung
description: Erfahren Sie, wie Sie Probleme mit Ihrer Microsoft Teams-Shop-Übermittlung beheben und beheben.
ms.topic: how-to
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 23c751d7a9fec96de128521f660213a559534283
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565109"
---
# <a name="resolve-issues-if-your-microsoft-teams-store-submission-fails"></a>Beheben von Problemen, wenn die Übermittlung Ihres Microsoft Teams-Shops fehlschlägt

Apps, die im Microsoft Teams Store veröffentlicht werden, müssen die Richtlinien für die [Teams-Shop-Validierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) und [die Richtlinien für kommerzielle Marktplätze](/legal/marketplace/certification-policies)erfüllen.

Wenn Ihre Store-Übermittlung fehlschlägt, stellt Microsoft einen Concierge-Validierungsdienst bereit, mit dem Sie Ihre App konform und veröffentlicht erhalten können.

## <a name="get-help-directly-from-microsoft"></a>Hilfe direkt von Microsoft erhalten

Der von Microsoft bereitgestellte Concierge-Validierungsdienst hilft Entwicklern, ihre Apps im Teams Store zu veröffentlichen. Im Rahmen dieses Dienstes überprüft Microsoft, ob Ihre App wie beschrieben funktioniert, alle geeigneten Metadaten enthält und Benutzern einen Wert bietet.

Wenn Ihre App-Übermittlung fehlschlägt, sendet Ihnen Microsoft innerhalb von 24 Stunden nach der Übermittlung einen Bewertungsbericht mit Empfehlungen.

## <a name="resolve-issues-and-resubmit-your-app"></a>Beheben von Problemen und erneutes Senden Ihrer App

Sie müssen alle vom Microsoft-Concierge-Validierungsteam gemeldeten Probleme beheben, bevor Sie Ihre App erneut im Partner Center übermitteln. Der Microsoft-Bericht enthält die folgenden Informationen:

* Eine entsprechende [Validierungsrichtlinie](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) für jedes Problem.
* Anweisungen zum Reproduzieren der einzelnen Probleme.
* Empfehlungen, um jedes Problem basierend auf der öffentlich verfügbaren Entwicklerdokumentation zu beheben.

Der Prozess zum Beheben von Problemen und erneuten Übermitteln einer App verläuft in der Regel wie folgt:

1. Sie beheben alle Probleme im Bericht.
1. Sie senden Folgendes an das Microsoft Concierge-Validierungsteam unter <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com:</a>
   * Ein aktualisiertes App-Paket
   * Testen Sie Notizen für Ihre App, wenn Sie diese nicht in Ihre ursprüngliche Übermittlung aufgenommen haben:
      * Anmeldeinformationen für mindestens zwei Konten (ein Administrator und ein Nicht-Administrator).
      * Anweisungen zum Konfigurieren der App und Testen der Funktionalität.
      * Ein Video, das Ihre in Teams verwendete App zeigt.
1. Das Microsoft Concierge-Validierungsteam testet Ihre aktualisierte App vollständig.
1. Sie tun eine der folgenden Optionen:
   * Wenn Ihre App frei von Problemen ist, senden Sie Ihre App erneut im Partner Center.
   * Wenn Probleme nicht behoben werden oder Microsoft neue Probleme findet, erhalten Sie einen weiteren Bericht darüber, was behoben werden soll. Beheben Sie diese Probleme, und senden Sie eine aktualisierte Version der App an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

> [!CAUTION]
> Um mehrere Übermittlungsfehler zu vermeiden, senden Sie Ihre App erst im Partner Center erneut, wenn das Microsoft-Concierge-Validierungsteam Ihre App genehmigt.

## <a name="faq"></a>Häufig gestellte Fragen

Erhalten Sie Antworten auf einige häufig gestellte Fragen, wenn Sie Probleme mit der App-Übermittlung lösen.

<br>

<details>

<summary><b>Wie lange dauert es, meine App zu veröffentlichen?</b></summary>

Wenn Ihre Shop-Übermittlung keine Probleme hat, wird Ihre App innerhalb von 1-2 Werktagen veröffentlicht. Wenn Ihre App fehlschlägt, gibt Ihnen ein Team von Microsoft Empfehlungen, um die Probleme zu beheben. Sobald Sie diese Korrekturen vornehmen und eine aktualisierte App erneut an dieses Team senden, werden Sie in 24 Stunden benachrichtigt, wenn Ihre App zur Veröffentlichung bereit ist oder noch mehr Arbeit benötigt.

<br>

</details>

<details>

<summary><b>Wie erhebe ich die Wahrscheinlichkeit, dass meine App die Übermittlung übergibt?</b></summary>

Die folgenden Schritte können zu einer erfolgreichen Übermittlung führen:

1. Entwickeln Sie Ihre App basierend auf den [Teams Designrichtlinien](~/concepts/design/design-teams-app-overview.md).
1. Stellen Sie sicher, dass Ihre App die Richtlinien für die [Teams-Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) und die [Zertifizierungsrichtlinien](/legal/marketplace/certification-policies)für den kommerziellen Marktplatz von Microsoft einhält.
1. Testen Sie Ihr App-Paket mit dem [Microsoft Teams App-Validierungstool](https://dev.teams.microsoft.com/appvalidation.html).
1. [Bereiten Sie Ihre Teams Store-Übermittlung](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)vor.

<br>

</details>

<details>

<summary><b>Meine App befindet sich im Beta-Test. Kann ich meine App trotzdem einreichen, um Zeit beim Veröffentlichungsprozess zu sparen?</b></summary>

Nein. Microsoft überprüft nur produktionsfähige Apps.

<br>

</details>

<details>

<summary><b>Darf ich die teamsubm@microsoft.com E-Mail kontaktieren, bevor ich meine App zum ersten Mal im Partner Center absende?</b></summary>

Nein. Microsoft beginnt erst mit der Validierung Ihrer App, wenn Sie Ihre App zum ersten Mal im Partner Center übermitteln.

<br>

</details>

<details>

<summary><b>Ich habe eine E-Mail vom Partner Center erhalten, in der es heißt, dass meine App für die Veröffentlichung genehmigt wurde. Warum ist meine App nicht im Teams Store?</b></summary>

Sobald Ihre App genehmigt wurde, dauert die Veröffentlichung in der Regel 1-2 Werktage, abhängig von den Funktionen der App.Wenn Ihre App nach zwei Werktagen nicht veröffentlicht wurde, wenden Sie sich an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com</a>.

<br>

</details>
