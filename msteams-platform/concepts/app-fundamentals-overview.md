---
title: Planen der App-Übersicht
author: heath-hamilton
description: Einführung in die Elemente der Planung einer App, des Verständnisses von Anwendungsfällen, App-Funktionen und anderer Teams-Funktionen.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.openlocfilehash: 7f1d12f1fe1e38ba674ca0ef4f21619ea0eb1b4a
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558716"
---
# <a name="plan-your-app-with-teams-features"></a>Planen Ihrer App mit Teams-Features

Beim Erstellen einer großartigen Teams-App geht es darum, die richtige Kombination von Features zu finden, um die Anforderungen Ihrer Benutzer zu erfüllen. Das Design, die Features und die Funktionen einer App ergeben sich aus diesem Zweck.

Im Kern ist Teams eine Plattform für die Zusammenarbeit. Es ist auch eine soziale Plattform, ist nativ plattformübergreifend, bildet das Herzstück von Office 365 und bietet Ihnen eine persönliche Leinwand für die Erstellung von Apps.

In diesem Abschnitt erfahren Sie, wie Sie:

* Identifizieren und Zuordnen von Anwendungsfällen zu Teams-Features.
* Planungscheckliste verwenden.
* Planen Sie über die App-Bereitstellung hinaus.

## <a name="plan-with-teams"></a>Planen mit Teams

Teams als Plattform bietet Ihnen Toolkits, Bibliotheken und Apps in jeder Phase der App-Entwicklung. Schauen wir uns den Lebenszyklus der App-Entwicklung an:

:::image type="content" source="../assets/images/app-fundamentals/plan-app.png" alt-text="Abbildung zeigt die Planung Ihrer App":::

* [Vor dem Erstellen](#before-you-build)
* [Während der Erstellung](#during-build)
* [Nach der Erstellung](#post-build)
* [Planungscheckliste](../concepts/design/planning-checklist.md)

### <a name="before-you-build"></a>Vor dem Erstellen

Das Verstehen des Nutzers und seines Anliegens sind die ersten Indikatoren dafür, wie eine Teams-App helfen kann. Stellen Sie Ihren Anwendungsfall um das Problem herum auf, bestimmen Sie, wie eine App dieses Problem lösen kann, und entwerfen Sie eine Lösung.

* **Verstehen Ihres Anwendungsfalls und der Teams-App-Features**: Verstehen Sie die Anforderungen Ihres Benutzers, und Sie können die richtigen Features identifizieren.

* **Ihre Anwendungsfälle zuordnen**: Ordnen Sie gängige Anwendungsfälle Teams-Features basierend auf Anforderungen zu, z. B. Freigabe, Zusammenarbeit, Workflows, relevante soziale Plattformen und mehr.

* **Planen von reaktionsfähigen Registerkarten für Teams Mobile**: Es behandelt gängige Szenarien und hilft bei der Planung von Apps für Teams Mobile.

### <a name="during-build"></a>Während der Erstellung

* **Entwickeln und Erstellen eines App-Projekts**: Mit Teams können Sie die Build-Umgebung auswählen, die Ihren App-Anforderungen am besten entspricht. Verwenden Sie das Teams-Toolkit oder andere SDKs wie C#, Blazor, Node.js und vieles mehr, um loszulegen.

* **Entwerfen der App-Benutzeroberfläche**: Verwenden Sie Teams UI Toolkit und UI Library, um das Layout Ihrer App zu entwerfen.

* **Verwenden von Teams als Plattform**: Die Teams-Plattform unterstützt Sie beim Erstellen einer Einzel- oder Mehrfunktions-App. Ihre Teams-App wird von den integrierten Produkten und Diensten unterstützt, die die App-Erfahrung verbessern.

    :::image type="content" source="../assets/images/overview/teams-solution.png" alt-text="Konzeptionelle Darstellung der Teams-Lösung.":::

    Ihre Apps werden in Teams als Registerkarten, Bots, Nachrichtenerweiterungen, Connectors und Webhooks oder als App mit mehreren Funktionen angezeigt. Diese Funktionen werden im Hintergrund von Azure, Microsoft Graph, SharePoint und Power Apps unterstützt, mit denen Aufgaben und Prozesse automatisiert werden können.

    Zusammen erwecken diese Funktionen Ihre App-Lösung zum Leben.

* **Integrieren von Gerätefunktionen**: Sie können die nativen Gerätefunktionen in Ihre App integrieren, z. B. Kamera, QR- oder Barcodescanner, Fotogalerie, Mikrofon und Standort.

### <a name="post-build"></a>Nach der Erstellung

* Integrieren Sie Ihre App in Teams und andere Apps, z. B. Microsoft 365, Microsoft Graph und vieles mehr.
* Verwenden Sie das Developer Portal zur Konfiguration, Verwaltung und Bereitstellung Ihrer Anwendung.

#### <a name="government-community-cloud"></a>Government Community Cloud

Government Community Cloud (GCC) ist eine auf Behörden ausgerichtete Kopie der kommerziellen Umgebung. Das Verteidigungsministerium (Department of Defense, DOD) und Auftragnehmer des Bundes müssen die strengen Anforderungen an Cybersicherheit und Compliance erfüllen. Zu diesem Zweck wurde GCC-High erstellt, um die Anforderungen von DOD und Bundesauftragnehmern zu erfüllen. GCC-High ist eine Kopie der DOD-Cloud, existiert aber in einer eigenen souveränen Umgebung. Die DOD-Cloud wurde nur für das Verteidigungsministerium entwickelt.

Endpunkte für Government Cloud sind:

| Mandant | GCC | GCC – hoch | DOD |
|-------------|---------|---|---|
|Teams-Client|`https://teams.microsoft.com`|`https://gov.teams.microsoft.us/`|`https://dod.teams.microsoft.us/` |
|Microsoft Teams-Administrator |`https://admin.teams.microsoft.com/`|`https://admin.gov.teams.microsoft.us/`|`https://admin.dod.teams.microsoft.us`|
|Microsoft Graph |`https://graph.microsoft.com`|`https://graph.microsoft.us`|`https://dod-graph.microsoft.us`|

Die folgende Tabelle enthält Teams-Features und -Verfügbarkeit für GCC, GCC-High und DOD:

| Features   | GCC | GCC – hoch | DOD |
|-------------|---------|---|---|
| Apps im Besitz von Teams wie bei intern entwickelten Apps | ✔️ Die App ist aktiviert, wenn sie über GCC verfügt. | ✔️ Die App ist aktiviert, wenn sie über GCC-High verfügt. | ✔️ Die App ist aktiviert, wenn sie über DOD verfügt. |
| Microsoft-Apps | ✔️ Mit GCC kompatible Microsoft-Apps | ✔️ Mit GCC-High kompatible Microsoft-Apps | ✔️ Microsoft-Apps, die mit DOD kompatibel sind |
| 3P- oder Drittanbieter-Apps | ✔️ Apps von Drittanbietern sind verfügbar. Standardmäßig deaktiviert und der Mieter-Administrator kann sie nach eigenem Ermessen aktivieren. | ❌ | ❌ |
| Benutzerdefinierte oder Branchenregisterkarten-Apps |  ✔️ | ✔️ (****Compliancebenutzeroberfläche**_) | ✔️ (_ ***Compliancebenutzeroberfläche***) |
| Benutzerdefinierte oder branchenspezifische Bots | ✔️ | ✔️ (****Compliancebenutzeroberfläche***) | ❌ |
| Benutzerdefinierte Nachrichtenerweiterungen | ✔️ | ✔️ | ❌ |
| Sideloading von Apps | ✔️ | ❌ | ❌ |
| Benutzerdefinierte Connectors | ❌ | ❌ | ❌ |

****Compliancebenutzeroberfläche***: Durch die Aktivierung der Kommunikation mit Drittanbietern akzeptieren Kunden, dass diese Kommunikation vom Drittanbieter und nicht von Microsoft verarbeitet wird. Der Kunde ist allein für die Minderung von Risiken verantwortlich, die mit der Verbindung mit Bots von Drittanbietern in deren Diensten verbunden sind. Microsoft befürwortet und gibt keine ausdrücklichen oder stillschweigenden Gewährleistungen in Bezug auf die Sicherheit von Drittanbietern, denen der Kunde erlaubt, sich mit ihrem Dienst zu verbinden. Durch das Aktivieren von Bots wird Ihre Systemgrenze basierend auf dem Bot, den Sie nutzen möchten, über diesen Mandanten hinaus erweitert. Es liegt in Ihrer Verantwortung sicherzustellen, dass dadurch Ihre Complianceanforderungen erfüllt werden, einschließlich FedRAMP, DFARS, ITAR usw. Es liegt in Ihrer Verantwortung, das Risiko und die Compliance aller Endpunkte und URLs zu bewerten, mit denen Sie eine Verbindung herstellen.

Mithilfe der folgenden Liste können Sie die Verfügbarkeit von GCC, GCC-High und DOD für die Features ermitteln:

* Informationen zu Drittanbieter-Apps finden Sie unter [Web-Apps](../samples/integrating-web-apps.md) und [Erweiterbarkeit von Besprechungs-Apps](../apps-in-teams-meetings/meeting-app-extensibility.md).
* Informationen zu Bots finden Sie unter [Erstellen Ihres ersten Konversationsbots für Teams](../get-started/first-app-bot.md), [Entwerfen Ihres Teams-Bots](../bots/design/bots.md), [Hinzufügen von Bots zu Microsoft Teams-Apps](../resources/bot-v3/bots-overview.md)und [Bots in Teams](../bots/what-are-bots.md).
* Informationen zum Sideloading von Apps finden Sie unter [Ermöglichen der Anpassung Ihrer Teams-App](../concepts/design/enable-app-customization.md), [Vermarkten Ihrer Microsoft Teams-App](../concepts/deploy-and-publish/apps-publish-overview.md)und [Hochladen Ihrer App in Teams](../concepts/deploy-and-publish/apps-upload.md).
* Informationen zu benutzerdefinierten Connectors finden Sie unter [Erstellen von Office 365-Connectors für Teams](../webhooks-and-connectors/how-to/connectors-creating.md).

</details>

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Anwendungsfälle und Teams-Features](design/understand-use-cases.md)

## <a name="see-also"></a>Siehe auch

* [Planungscheckliste](../concepts/design/planning-checklist.md)
* [Überlegungen zur Microsoft Teams-Integration](../samples/integrating-web-apps.md)
* [Erstellen Ihrer ersten Microsoft Teams-App](../build-your-first-app/build-first-app-overview.md)
