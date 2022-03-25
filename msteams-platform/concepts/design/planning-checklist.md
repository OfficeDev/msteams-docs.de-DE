---
title: Fragen zur Planung der Entwicklung von Teams-Apps
author: heath-hamilton
description: 'Fragen, die Sie bei der Planung Ihrer App berücksichtigen sollten: Ihre Nutzer und deren Bedürfnisse verstehen, Probleme der Nutzer verstehen, die Ihre App lösen würde, die Nutzerauthentifizierung und deren Onboarding-Erfahrung planen'
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: 6a2440ea05c1a89f4e1306b6fb54635287fb2d6d
ms.sourcegitcommit: 65cea59cc0602269395a2f87e023a4057d9cc55e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2022
ms.locfileid: "63765932"
---
# <a name="teams-app-planning-checklist"></a>Prüfliste für die Teams App-Planung

Der Lebenszyklus einer App reicht von der Planung Ihrer App bis hin zur Bereitstellung und darüber hinaus. Die Planung Ihrer App erfordert mehr als nur das Wissen über Ihren Nutzer und dessen Anforderungen. Je nach Ihren App-Anforderungen können Sie auch die Planung zukünftiger Updates in Betracht ziehen.

Sehen wir uns die Planung für den Lebenszyklus einer App in der Praxis an.

## <a name="relevant-questions"></a>Relevante Fragen

Hier ist eine Checkliste mit Fragen, die Sie bei der Planung Ihrer App berücksichtigen sollten. Verwenden Sie sie als Richtlinie, um sicherzustellen, dass Ihr Plan die wichtigen Details der App-Entwicklung abdeckt.

<br>
<br>
<details>
<summary>Grundlegendes zu Ihrem Nutzer</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Handelt es sich bei den Nutzern hauptsächlich um Frontline-Mitarbeiter auf mobilen Clients? |
| 2 | Erwarten Sie, dass viele Gastnutzer Zugriff auf Ihre App benötigen? |
| 3 | Verwenden sie Teams und Kanäle oder hauptsächlich Gruppenchats? |
| 4 | Wie technisch versiert sind Ihre Hauptnutzer? |
| 5 | Benötigen Sie ein umfassendes Onboarding-Erlebnis oder reichen ein paar Hinweise aus? |

</details>
<br>
<details>
<summary>Grundlegendes zum Problem</summary>

| # | Erwägen Sie... |
|--- | --- |
| 1 | Welche Vor- und Nachteile hat das derzeitige System, das von Ihren Nutzern verwendet wird? |
| 2 | Welche Probleme haben Ihre Nutzer, die Sie beheben möchten? |
| 3 | Welche Funktionen oder Möglichkeiten schätzen Ihre Nutzer bei ihrer derzeitigen Arbeitsweise? |

</details>
<br>
<details>
<summary>Grundlegendes zu den Einschränkungen der App</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Was sind die Herausforderungen bei der Back-End-Integration der aktuellen App? |
| 2 | Wer ist Eigentümer der Backend-Daten – intern oder Drittanbieter? |
| 3 | Gibt es Firewalls, die sich auf die Funktionsweise der App auswirken? |
| 4 | Gibt es APIs für den Zugriff auf die Daten, die Sie für die Funktion Ihrer App benötigen? |

</details>
<br>
<details>
<summary>Bereitstellen der Authentifizierung</summary>

| # | Erwägen Sie...|
|--- | --- |
| 1 | Greifen die Nutzer basierend je nach ihrer Rolle auf unterschiedliche Datenansichten zu? |
| 2 | Sind personenbezogene Informationen betroffen? |
| 3 | Basieren die Interaktionen auch auf den Nutzerrollen? |
| 4 | Greifen externe Nutzer auf die App zu? |

</details>
<br>
<details>
<summary>Planen des Onboardings</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Was geschieht, wenn ein Nutzer Ihre Registerkarte zum ersten Mal in einem Kanal konfiguriert? |
| 2 | Wenn Sie Karten mit einer Messaging-Erweiterung austauschen, ist es dann sinnvoll, einen kleinen Link zu einer Seite mit weiteren Informationen hinzuzufügen, um den Nutzern zu zeigen, was Ihre App sonst noch kann? |
| 3 | Erwarten Sie, dass die meisten Personen bereits einen gewissen Kontext haben, für den Ihre App gedacht ist, oder dass sie Ihre Dienste bereits in einem anderen Kontext genutzt haben? |
| 4 | Kommen sie ohne Vorkenntnisse zu Ihrer App? |

</details>
<br>
<details>
<summary>Apps im persönlichen Bereich</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Gibt es 1:1-Interaktionen mit der App, die aus Datenschutz- oder anderen Gründen erforderlich sind? Beispielsweise das Überprüfen des Restguthabens oder anderer privater Informationen. |
| 2 | Gibt es eine Zusammenarbeit zwischen Nutzern, die möglicherweise keine gemeinsamen Teams haben? Beispiel: Suchen nach bevorstehenden organisationsweiten Ereignissen in einem Unternehmen. |
| 3 | Gibt es personalisierte Benachrichtigungen oder Nachrichten, die während der gesamten Teams-App an einen Benutzer gesendet werden müssen? |

</details>
<br>
<details>
<summary>Freigegebene Bereichs-Apps</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Sind die informationen, die von der App auf der Registerkarte oder über einen Bot angezeigt werden, für die meisten Mitglieder eines Teams relevant und nützlich? Beispiel: Scrum-App. |
| 2 | Kann sich der Appkontext ändern, je nachdem, in welchem Team diese hinzugefügt wird? Aufgaben der Planer unterscheiden sich beispielsweise in verschiedenen Teams. |
| 3 | Ist es möglich, dass alle Mitglieder einer Persona, die zusammenarbeiten müssen, Teil eines einzelnen Teams sind? Beispielsweise Mitarbeiter, die an einem Ticket arbeiten. |

</details>
<br>
<details>
<summary>Buildumgebung auswählen</summary>

Vorschlag: Optionen, mit denen Sie die richtige Umgebung basierend auf den App-Anforderungen auswählen können.
</details>
<br>
<details>
<summary>Testen der App planen</summary>

Vorschlag: Optionen, die dabei helfen, die beste Testumgebung für die App zu ermitteln.
</details>
<br>
<details>
<summary>Planen der App-Vermarktung</summary>

Vorschlag: Optionen, mit denen das beste Vermarktungsmodell ermittelt werden kann.

</details>

## <a name="plan-for-hosting-your-teams-app"></a>Planen des Hostings Ihrer Teams-App

Teams hostet Ihre App nicht. Wenn ein Benutzer Ihre App in Teams installiert, wird ein App-Paket installiert, das eine einzige Konfigurationsdatei (auch als App-Manifest bezeichnet) und die Symbole Ihrer App enthält. Die Logik und der Datenspeicher der App werden an anderer Stelle gehostet, z. B. während der Entwicklung auf „localhost“ und unter Azure Web Services. Teams greift über HTTPS auf diese Ressourcen zu.

:::image type="content" source="../../assets/images/teams-app-host.png" alt-text="Abbildung des App-Hostings der Teams-App" border="true":::

## <a name="plan-beyond-app-building"></a>Über die App-Erstellung hinaus planen

- **Entscheiden Sie, was in Teams integriert werden soll**: Egal, ob es sich um eine neue oder eine bestehende App handelt, prüfen Sie, ob Sie die gesamte App im Teams-Client haben möchten. Wenn Sie nur einen Teil der App integrieren, konzentrieren Sie sich auf die Freigabe, Zusammenarbeit, Initiierung und Überwachung von Workflows.

- **Planen der Onboarding-Benutzeroberfläche**: Gestalten Sie Ihr Onboardingerlebnis mit Blick auf Ihre Nutzer. Die Einführung eines Chatbots, der in einem Kanal mit tausend Personen installiert ist, unterscheidet sich von der Einführung in einem Einzelchat.

- **Planen Sie für die Zukunft**: Identifizieren Sie neue Funktionen, die der Nutzer in der aktuellen Lösung bevorzugen wird. Alle neuen Features können sich auf das App-Design und die Architektur auswirken.
