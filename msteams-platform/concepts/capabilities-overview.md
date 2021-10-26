---
title: Grundlegendes zu App-Funktionen
author: heath-hamilton
description: Teams erläuterte App-Funktionen
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: eae30ddfd735730208c4f1ac47cfd5ec2a8c2c88
ms.sourcegitcommit: 781e7b82240075e9d1f55e97f3f1dcbba82a5e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2021
ms.locfileid: "60566295"
---
# <a name="understand-microsoft-teams-app-capabilities"></a>Grundlegendes zu Microsoft Teams App-Funktionen

Erweiterbarkeit oder Einstiegspunkte sind unterschiedliche Möglichkeiten, wie sich eine App für einen Benutzer manifestieren kann. Beispielsweise kann ein Benutzer mit einer App auf einer Canvas-Registerkarte interagieren, um eine Aktivität zu machen, oder er kann sich dafür entscheiden, dies mithilfe eines Unterhaltungs-Bots zu tun. Die verschiedenen Funktionen, die zum Erstellen Ihrer Teams App verwendet werden, ermöglichen es Ihnen, den Nutzungsbereich zu erhöhen.

Es gibt mehrere Möglichkeiten, Teams zu erweitern, sodass jede App einzigartig ist. Einige verfügen nur über eine Funktion, z. B. einen Webhook, während andere über mehrere Funktionen verfügen, um Benutzern verschiedene Optionen zu bieten. Ihre App kann z. B. Daten an einem zentralen Ort anzeigen, d. h. auf der **Registerkarte** und diese Informationen über eine Unterhaltungsschnittstelle, d. h. den **Bot,** darstellen.

## <a name="app-capabilities"></a>App-Funktionen

Ihre Teams-Apps verfügen über eine oder alle der folgenden Kernfunktionen:

* [Registerkarten](../tabs/what-are-tabs.md)
* [Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks und Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Ihre App kann auch erweiterte Funktionen nutzen, z. B. die [Microsoft Graph-API für Teams.](/graph/teams-concept-overview)

In der folgenden Abbildung erhalten Sie eine Vorstellung davon, welche Funktionen die gewünschten Features in Ihrer App bereitstellen:

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mind map illustrating what Teams app capabilities are.":::

## <a name="always-consider-your-user"></a>Berücksichtigen Sie immer Ihren Benutzer

Wenn Sie sich mit Teams App-Entwicklung vertraut machen, verstehen Sie die grundlegenden Grundlagen. Sie wissen, dass es mehrere Möglichkeiten gibt, bestimmte Features zu erstellen. Überlegen Sie in solchen Szenarien, wie Sie Ihren Benutzern eine nativeere Benutzeroberfläche bieten können.
Sie können beispielsweise Benutzereingaben in einem Formular sammeln, das als Registerkarte in der App erstellt wurde. Sie können dies auch mithilfe eines Aufgabenmoduls tun, ohne die Ansichten zu wechseln und den Workflow des Benutzers zu unterbrechen. Es ist wichtig, Erweiterungspunkte auszuwählen, die die geringste Abweichung vom regulären Workflow eines Benutzers bereitstellen.

## <a name="government-community-cloud-gcc"></a>Government Community Cloud (GCC)

Government Community Cloud ist eine Auf Regierung ausgerichtete Kopie der kommerziellen Umgebung. Das Verteidigungsministerium (Department of Defense, DOD) und Die Auftragnehmer des Bundes müssen die strengen Anforderungen an Cybersicherheit und Compliance erfüllen. Zu diesem Zweck wurde GCC-High erstellt, um die Anforderungen von DOD und Bundesauftragnehmern zu erfüllen. GCC-High ist eine Kopie der DOD-Cloud, aber in einer eigenen unabhängigen Umgebung vorhanden. Die DOD-Cloud wurde nur für das Verteidigungsministerium erstellt.

Die folgende Tabelle enthält Teams Features und Verfügbarkeit für GCC, GCC-Hoch und DOD:

| Features   | GCC | GCC – hoch | DOD |
|-------------|---------|
| Teams eigenen Apps wie in intern entwickelten Apps | ✔️ App ist aktiviert, wenn sie über GCC verfügt. | ✔️ App ist aktiviert, wenn sie über GCC-Hoch verfügt. | ✔️ App ist aktiviert, wenn sie ÜBER DOD verfügt. |
| Microsoft-Apps | ✔️ Microsoft-Apps, die mit GCC kompatibel sind | ✔️ Microsoft-Apps, die mit GCC-High kompatibel sind | ✔️ Microsoft-Apps, die DOD-konform sind |
| 3p- oder Drittanbieter-Apps | ✔️ Drittanbieter-Apps sind verfügbar. Standardmäßig deaktiviert, und mandantenadministratoren verwenden ihren eigenen Ermessen, um es zu aktivieren. | ❌ | ❌ |
| Bots | ✔️ | ❌ | ❌ |
| Benutzerdefinierte oder Branchenregisterkarten-Apps |  ✔️ | ✔️ | ✔️ |
| Querladen von Apps | ✔️ | ❌ | ❌ |
| Benutzerdefinierte oder Lob-Bots | ✔️ | ❌ | ❌ |
| Benutzerdefinierte Messaging-Erweiterungen | ❌ | ❌ | ❌ |
| Benutzerdefinierte Connectors | ❌ | ❌ | ❌ |

Die folgende Liste hilft, die Verfügbarkeit von GCC, GCC-Hoch und DOD für die Features zu ermitteln:

* Informationen zu Drittanbieter-Apps finden Sie unter [Web-Apps](../samples/integrating-web-apps.md) und [Besprechungs-App-Erweiterbarkeit.](../apps-in-teams-meetings/meeting-app-extensibility.md)
* Informationen zu Bots finden Sie unter [Erstellen Ihres ersten Unterhaltungs-Bots für Teams,](../get-started/first-app-bot.md)Entwerfen Ihres Teams [Bots, Hinzufügen von Bots zu Microsoft Teams Apps](../resources/bot-v3/bots-overview.md)und [Bots in Teams](../bots/what-are-bots.md). [](../bots/design/bots.md)
* Informationen zum Querladen von Apps finden Sie unter [Aktivieren der anpassungsfähigen Teams-App,](../concepts/design/enable-app-customization.md) [Verteilen Ihrer Microsoft Teams-App](../concepts/deploy-and-publish/apps-publish-overview.md)und [Hochladen Ihrer App in Teams.](../concepts/deploy-and-publish/apps-upload.md)
* Benutzerdefinierte Connectors finden Sie unter [Erstellen Office 365 Connectors für Teams.](../webhooks-and-connectors/how-to/connectors-creating.md)

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Apps für Teams](../overview.md) 
 [Erstellen Ihrer ersten Microsoft Teams-App](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Microsoft Teams-App-Einstiegspunkte](../concepts/extensibility-points.md)
