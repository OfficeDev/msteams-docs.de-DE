---
title: Fragen zur Planung der Entwicklung von Teams-Apps
author: heath-hamilton
description: 'Fragen, die Sie bei der Planung Ihrer App berücksichtigen sollten: Verstehen Sie Ihre Nutzer und ihre Bedürfnisse, die Probleme, die Ihre App lösen würde, die Nutzerauthentifizierung und die Erfahrung beim Onboarding?'
ms.topic: conceptual
ms.localizationpriority: high
ms.author: surbhigupta
ms.openlocfilehash: 78dd40e13c3bdac359cc5201bda92a5b1daccfb8
ms.sourcegitcommit: 42602e8ec917f5033c0b6a95cf65b428db3c5b0a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2022
ms.locfileid: "67286119"
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

Das Verstehen des Nutzers und seines Anliegens sind die ersten Indikatoren dafür, wie eine Teams-App helfen kann. Stellen Sie Ihren Anwendungsfall um das Problem herum auf, bestimmen Sie, wie eine App dieses Problem lösen kann, und entwerfen Sie eine Lösung. Weitere Informationen finden Sie unter [Grundlegendes zu Anwendungsfällen](understand-use-cases.md).

| # | Erwägen Sie... |
| --- | --- |
| 1 | Handelt es sich bei den Benutzern hauptsächlich um Mitarbeiter in Service und Produktion auf mobilen Clients? |
| 2 | Erwarten Sie, dass viele externe Benutzer Zugriff auf Ihre App benötigen? |
| 3 | Verwenden sie Teams und Kanäle oder hauptsächlich Gruppenchats? |
| 4  | Wie technisch versiert sind Ihre Hauptbenutzer? |
| 5  | Benötigen Sie ein umfassendes Onboarding-Erlebnis oder reichen ein paar Hinweise aus? |

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
| 4  | Gibt es APIs für den Zugriff auf die Daten, die Sie für die Funktion Ihrer App benötigen? |

</details>
<br>
<details>
<summary>Bereitstellen der Authentifizierung</summary>

Bei der Authentifizierung geht es darum, App-Benutzer zu überprüfen und die App- und App-Benutzer vor ungerechtfertigten Zugriffen zu schützen. Sie können eine Authentifizierungsmethode verwenden, die für Ihre App geeignet ist, um App-Benutzer zu überprüfen, die die Teams-App verwenden möchten. Weitere Informationen finden Sie unter [Authentifizieren von Benutzern in Microsoft Teams](../authentication/authentication.md).

| # | Erwägen Sie...|
|--- | --- |
| 1 | Greifen die Nutzer basierend je nach ihrer Rolle auf unterschiedliche Datenansichten zu? |
| 2 | Sind Kundeninhalte beteiligt? |
| 3 | Basieren die Interaktionen auch auf den Nutzerrollen? |
| 4  | Greifen externe Nutzer auf die App zu? |

</details>
<br>
<details>
<summary>Planen des Onboardings</summary>

Beim Erstellen einer großartigen Teams-App geht es darum, die richtige Kombination von Features zu finden, um die Anforderungen Ihrer Benutzer zu erfüllen. Um Ihren Benutzern ein nahtloses Onboarding zu ermöglichen, können Sie eine Schritt-für-Schritt-für-Schritt-Anleitung erstellen, in der erläutert wird, wie die App verwendet wird und was Sie damit tun können. Siehe z. B. [Erstellen eines Microsoft Teams-Unterhaltungs-Bots](../../sbs-teams-conversation-bot.yml).

| # | Erwägen Sie... |
| --- | --- |
| 1 | Was geschieht, wenn ein Nutzer Ihre Registerkarte zum ersten Mal in einem Kanal konfiguriert? |
| 2 | Wenn Sie Karten mit einer Nachrichtenerweiterung freigeben, ist es dann sinnvoll, einen kleinen Link zu einer Seite mit weiteren Informationen hinzuzufügen, um den Benutzern zu zeigen, was Ihre App sonst noch kann? |
| 3 | Erwarten Sie, dass die meisten Personen bereits einen gewissen Kontext haben, für den Ihre App gedacht ist, oder dass sie Ihre Dienste bereits in einem anderen Kontext genutzt haben? |
| 4  | Kommen sie ohne Vorkenntnisse zu Ihrer App? |

</details>
<br>
<details>
<summary>Apps im persönlichen Bereich</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Gibt es 1:1-Interaktionen mit der App, die aus Datenschutz- oder anderen Gründen erforderlich sind? Beispielsweise das Überprüfen des Restguthabens oder anderer privater Informationen. |
| 2 | Werden sie die Zusammenarbeit zwischen Benutzern fördern, die vielleicht keine gemeinsamen Teams haben? Beispiel: Suchen nach bevorstehenden organisationsweiten Ereignissen in einem Unternehmen. |
| 3 | Gibt es personalisierte Benachrichtigungen oder Nachrichten, die während der gesamten Teams-App an einen Benutzer gesendet werden müssen? |

</details>
<br>
<details>
<summary>Freigegebene Bereichs-Apps</summary>

| # | Erwägen Sie... |
| --- | --- |
| 1 | Sind die informationen, die von der App auf der Registerkarte oder über einen Bot angezeigt werden, für die meisten Mitglieder eines Teams relevant und nützlich? Beispiel: Scrum-App. |
| 2 | Könnte sich der Kontext der App ändern, je nachdem, zu welchem Team sie hinzugefügt wird? Aufgaben der Planer unterscheiden sich beispielsweise in verschiedenen Teams. |
| 3 | Ist es möglich, dass alle Mitglieder einer Persona, die zusammenarbeiten müssen, Teil eines einzelnen Teams sind? Beispielsweise Mitarbeiter, die an einem Ticket arbeiten. |

</details>
<br>
<details>
<summary>Buildumgebung auswählen</summary>

Mit Microsoft Teams können Sie die Buildumgebung auswählen, die Ihren App-Anforderungen am besten entspricht. Verwenden Sie das Teams-Toolkit oder andere SDKs wie C#, Blazor, Node.js und vieles mehr, um loszulegen. Weitere Informationen finden Sie unter [Planen Ihrer App mit Microsoft Teams-Features](../app-fundamentals-overview.md).

Vorschlag: Optionen, mit denen Sie die richtige Umgebung basierend auf den App-Anforderungen auswählen können.
</details>
<br>
<details>
<summary>Testen der App planen</summary>

Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie ihre App testen, bevor Sie sie veröffentlichen. Das ultimative Ziel besteht darin, so viele Benutzer wie möglich für Ihre App zu erhalten. Stellen Sie daher sicher, dass Sie die App auf mehreren Geräten testen, die Benutzer verwenden können. Weitere Informationen finden Sie unter [Testen Ihrer App](../build-and-test/test-app-overview.md).

Vorschlag: Optionen, die dabei helfen, die beste Testumgebung für die App zu ermitteln.
</details>
<br>
<details>
<summary>Planen der App-Vermarktung</summary>

Sie können Ihre Microsoft Teams-App für eine Person, ein Team, eine Organisation oder jede Person bereitstellen, die sie verwenden möchte. Wie Sie verteilen, hängt von mehreren Faktoren ab, darunter die Bedürfnisse der Benutzer, geschäftliche und technische Anforderungen sowie Ihre Ziele für die App. Weitere Informationen finden Sie unter [Verteilen Ihrer Microsoft Teams-App](../deploy-and-publish/apps-publish-overview.md).

Vorschlag: Optionen, mit denen das beste Vermarktungsmodell ermittelt werden kann.

</details>

## <a name="plan-for-hosting-your-teams-app"></a>Planen des Hostings Ihrer Teams-App

Teams hostet Ihre App nicht. Wenn ein Benutzer Ihre App in Teams installiert, wird ein App-Paket installiert, das nur eine einzige Konfigurationsdatei (auch als App-Manifest bekannt) und die Symbole Ihrer App enthält. Die Logik und der Datenspeicher der App werden an anderer Stelle gehostet, z. B. während der Entwicklung auf „localhost“ und unter Azure Web Services. Teams greift über HTTPS auf diese Ressourcen zu.

:::image type="content" source="../../assets/images/teams-app-host.png" alt-text="Abbildung: App-Hosting der Microsoft Teams-App":::

## <a name="plan-beyond-app-building"></a>Über die App-Erstellung hinaus planen

- **Entscheiden Sie, was in Teams integriert werden soll**: Egal, ob es sich um eine neue oder eine bestehende App handelt, prüfen Sie, ob Sie die gesamte App im Teams-Client haben möchten. Wenn Sie nur einen Teil der App integrieren, konzentrieren Sie sich auf die Freigabe, Zusammenarbeit, Initiierung und Überwachung von Workflows.

- **Planen der Onboarding-Benutzeroberfläche**: Gestalten Sie Ihr Onboardingerlebnis mit Blick auf Ihre Nutzer. Die Einführung eines Chatbots, der in einem Kanal mit tausend Personen installiert ist, unterscheidet sich von der Einführung in einem Einzelchat.

- **Planen Sie für die Zukunft**: Identifizieren Sie neue Funktionen, die der Nutzer in der aktuellen Lösung bevorzugen wird. Alle neuen Features können sich auf das App-Design und die Architektur auswirken.
