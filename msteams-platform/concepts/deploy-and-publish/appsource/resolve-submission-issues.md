---
title: Beheben von Problemen mit der Speicherübermittlung
description: Hier erfahren Sie, wie Sie Probleme mit ihrer Microsoft Teams beheben.
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
# <a name="resolve-issues-if-your-microsoft-teams-store-submission-fails"></a>Beheben von Problemen, wenn Microsoft Teams Speicherübermittlung fehlschlägt

Apps, die im Microsoft Teams veröffentlicht werden, müssen die Richtlinien für die Teams [und](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) kommerzielle [Marketplace-Richtlinien erfüllen.](/legal/marketplace/certification-policies)

Wenn Ihre Store-Übermittlung fehlschlägt, bietet Microsoft einen Dienst für die Überprüfung durch einen Mitarbeiter, der Ihnen dabei hilft, Ihre App kompatibel und veröffentlicht zu machen.

## <a name="get-help-directly-from-microsoft"></a>Hilfe direkt von Microsoft erhalten

Der von Microsoft bereitgestellte Dienst zur Überprüfung des Diensts für den Dienst zur Überprüfung des Diensts unterstützt Entwickler dabei, ihre Apps im Teams veröffentlichen. Als Teil dieses Diensts überprüft Microsoft, ob Ihre App wie beschrieben funktioniert, alle entsprechenden Metadaten enthält und Den Benutzern einen Wert bietet.

Wenn ihre App-Übermittlung fehlschlägt, sendet Microsoft Ihnen innerhalb von 24 Stunden nach übermittlung einen Überprüfungsbericht mit Empfehlungen.

## <a name="resolve-issues-and-resubmit-your-app"></a>Beheben von Problemen und erneutes Übermitteln Ihrer App

Sie müssen alle probleme beheben, die vom Microsoft-Team für die Überprüfung des Partnerservice gemeldet wurden, bevor Sie Ihre App im Partner Center erneut übermitteln. Der Microsoft-Bericht enthält die folgenden Informationen:

* Eine entsprechende [Validierungsrichtlinie](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) für jedes Problem.
* Anweisungen zum Reproduzieren der einzelnen Fehler.
* Empfehlungen, um jedes Problem basierend auf der öffentlich verfügbaren Entwicklerdokumentation zu beheben.

Der Prozess zum Beheben von Problemen und zum erneuten Übermitteln einer App läuft in der Regel wie dies ab:

1. Sie beheben alle Probleme im Bericht.
1. Sie senden folgendes an das Microsoft-Team für die Validierung von <a href="mailto:teamsubm@microsoft.com">Teamsubm@microsoft.com:</a>
   * Ein aktualisiertes App-Paket
   * Testnotizen für Ihre App, wenn Sie diese in Ihrer ursprünglichen Übermittlung nicht enthalten haben:
      * Anmeldeinformationen für mindestens zwei Konten (ein Administrator und ein Nicht-Administrator).
      * Anweisungen zum Konfigurieren der App und Testen der Funktionalität.
      * Ein Video, das Ihre app zeigt, die in Teams.
1. Das Microsoft-Team für die Überprüfung der 1.000-Mitarbeiter testet Ihre aktualisierte App vollständig.
1. Gehen Sie wie folgt vor:
   * Wenn Ihre App frei von Problemen ist, übermitteln Sie Ihre App erneut im Partner Center.
   * Wenn Probleme nicht behoben werden oder Microsoft neue Probleme findet, erhalten Sie einen weiteren Bericht darüber, was behoben werden soll. Beheben Sie diese Probleme, und senden Sie eine aktualisierte Version der App an <a href="mailto:teamsubm@microsoft.com">teamsubm@microsoft.com.</a>

> [!CAUTION]
> Um mehrere Übermittlungsfehler zu vermeiden, übermitteln Sie Ihre App erst dann erneut im Partner Center, wenn das Microsoft-Team für die Überprüfung ihrer App die App genehmigt hat.

## <a name="faq"></a>Häufig gestellte Fragen

Erhalten Sie Antworten auf einige häufig gestellte Fragen beim Beheben von Problemen mit der App-Übermittlung.

<br>

<details>

<summary><b>Wie lange dauert die Veröffentlichung meiner App?</b></summary>

Wenn Ihre Store-Übermittlung keine Probleme hat, wird Ihre App innerhalb von 1-2 Werktagen veröffentlicht. Wenn Ihre App ausfällt, gibt Ihnen ein Team von Microsoft Empfehlungen, um die Probleme zu beheben. Sobald Sie diese Korrekturen vorgenommen und eine aktualisierte App an dieses Team erneut senden, werden Sie in 24 Stunden benachrichtigt, ob Ihre App bereit ist, zu veröffentlichen oder noch mehr Arbeit benötigt.

<br>

</details>

<details>

<summary><b>Wie kann ich die Wahrscheinlichkeit erhöhen, dass meine App die Übermittlung besteht?</b></summary>

Wenn Sie folgendes tun, kann dies zu einer erfolgreichen Übermittlung führen:

1. Entwickeln Sie Ihre App basierend auf den [Teams Entwurfsrichtlinien](~/concepts/design/design-teams-app-overview.md).
1. Stellen Sie sicher, dass Ihre App die Teams [Und](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) Microsoft Commercial Marketplace Zertifizierungsrichtlinien [befolgt.](/legal/marketplace/certification-policies)
1. Testen Sie Ihr App-Paket mit [dem Microsoft Teams-App-Validierungstool](https://dev.teams.microsoft.com/appvalidation.html).
1. [Bereiten Sie Teams Store-Übermittlung vor.](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)

<br>

</details>

<details>

<summary><b>Meine App befindet sich im Betatest. Kann ich meine App trotzdem übermitteln, um Zeit beim Veröffentlichungsprozess zu sparen?</b></summary>

Nein. Microsoft überprüft nur produktionsbereite Apps.

<br>

</details>

<details>

<summary><b>Darf ich mich an teamsubm@microsoft.com E-Mail wenden, bevor ich meine App zum ersten Mal im Partner Center absende?</b></summary>

Nein. Microsoft beginnt erst mit der Validierung Ihrer App, wenn Sie Ihre App zum ersten Mal im Partner Center übermitteln.

<br>

</details>

<details>

<summary><b>Ich habe eine E-Mail vom Partner Center erhalten, dass meine App für die Veröffentlichung genehmigt wurde. Warum befindet sich meine App nicht im Teams Store?</b></summary>

Sobald Ihre App genehmigt wurde, dauert die Veröffentlichung in der Regel 1 bis 2 Werktage, je nach den Funktionen der App.Wenn Ihre App nach zwei Werktagen nicht veröffentlicht wurde, wenden Sie sich <a href="mailto:teamsubm@microsoft.com">an teamsubm@microsoft.com</a>.

<br>

</details>
