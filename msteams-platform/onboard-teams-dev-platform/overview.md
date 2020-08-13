---
title: Entwicklerplattform für Teams
author: clearab
description: Übersicht darüber, wie Entwickler Microsoft Teams-Funktionen mithilfe der Teams-Plattform erweitern und anpassen können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: d127acb33212f23dff9cf0dd83a1936044c10d5e
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651997"
---
# <a name="building-for-microsoft-teams"></a>Erstellen für Microsoft Teams

Microsoft Teams-apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dazu, wo Personen zunehmend sammeln, lernen und arbeiten.

Mit apps erweitern Sie Teams entsprechend Ihren Anforderungen. Sie können etwas ganz neues für Teams erstellen oder einfach Features in Ihren bevorzugten apps und Diensten integrieren.

## <a name="what-can-teams-apps-do"></a>Was können Teams-apps tun?

Personen ermitteln und verwenden Teams-Apps über eine Reihe von Platt Form [Funktionen](capabilities-overview.md).

Einige apps sind einfach (Benachrichtigungen senden), andere sind komplex (Patientendatensätze anzeigen). Beachten Sie bei der Planung Ihrer APP, dass Teams ein Hub für die Zusammenarbeit sind. Die besten Teams-Apps helfen Benutzern, sich selbst auszudrücken und besser zusammenzuarbeiten.

### <a name="get-information-more-conveniently"></a>Bequemeres Abrufen von Informationen

Manchmal müssen Sie die Dinge einfacher finden. Zeigt eine wichtige Webseite auf einer [Registerkarte](doc-links/what-are-tabs.md)an, die eine Vollbildansicht für statischen und dynamischen Inhalt in Microsoft Teams bietet.

![Konzeptionelle Darstellung dessen, was Registerkarten im Microsoft Teams-Client aussehen.](doc-links/images/overview-tabs.png)

### <a name="share-links-without-switching-context"></a>Freigeben von Links ohne Kontextwechsel

Informationen in eine Unterhaltung ziehen und Teams niemals verlassen. Mit [Messaging-Erweiterungen](doc-links/what-are-messaging-extensions.md) können Sie beispielsweise umfangreiche, leicht verdauliche Inhalte aus einem externen System mithilfe des Felds zum Verfassen von Nachrichten freigeben.

![Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen](doc-links\images\overview-messaging.png)

### <a name="turn-words-into-actions"></a>Umwandeln von Wörtern in Aktionen

Unterhaltungen führen häufig dazu, dass Sie etwas tun müssen (eine Bestellung erstellen, meinen Code überprüfen usw.). Ein [bot](doc-links/what-are-bots.md) kann diese Art von Workflows direkt innerhalb von Teams abstoßen.

![Konzeptionelle Darstellung dessen, was Bots im Microsoft Teams-Client aussieht](doc-links/images/overview-bots.png)

### <a name="communicate-with-external-apps-and-services"></a>Kommunikation mit externen apps und Diensten

Bei [eingehenden webhooks](doc-links/what-are-webhooks-and-connectors.md#incoming-webhooks) handelt es sich um eine einfache Möglichkeit, Benachrichtigungen automatisch von einer anderen APP an einen Microsoft Teams-Kanal oder Chat zu senden. Mit [ausgehenden webhooks](doc-links/what-are-webhooks-and-connectors.md#outgoing-webhooks)können Sie eine Nachricht an den Webdienst mit einem @mention senden.

![Konzeptionelle Darstellung dessen, was Konnektoren im Teams-Client aussieht.](doc-links/images/overview-connectors.png)

### <a name="utilize-teams-data"></a>Verwenden von Microsoft Teams-Daten

Die [Microsoft Graph-Rest-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Sie beim Erstellen oder Erweitern von Features für Ihre APP unterstützen können.

!["Konzeptionelle Darstellung der Microsoft Graph-Rest-API für Teams](doc-links/images/overview-graph.png)
  
## <a name="start-building"></a>Erstellen beginnen

   Machen Sie sich schnell mit der Erstellung für Microsoft Teams vertraut, indem Sie eine einfache APP erstellen und ein paar häufig verwendete Funktionen hinzufügen.

   > [!div class="nextstepaction"]
   > [Erstellen Sie jetzt Ihre erste app.](build-your-first-app/build-real-world-app.md)

### <a name="bring-it-all-together"></a>Zusammenführen

   Vereinfachen Sie Prozesse und Workflows für Benutzer, indem Sie die bevorzugten Webanwendungen, Dienste und Systeme Ihrer Organisation mit kollaborativen Teams-Features kombinieren.

   > [!div class="nextstepaction"]
   > [Integrieren einer vorhandenen APP](doc-links/integrating-web-apps.md)

### <a name="trust-the-process"></a>Dem Prozess Vertrauen

   Verstehen Sie den gesamten Entwicklungsprozess für Teams-Plattformen, um eine APP für Ihre Organisation oder andere Personen effektiv zu planen, zu entwerfen, zu erstellen und zu veröffentlichen.

   > [!div class="nextstepaction"]
   > [Starten der Planung Ihrer APP](doc-links/extensibility-points.md)

### <a name="no-code-no-worries"></a>Kein Code, keine Sorge

   Sie müssen kein Programmierer sein, um eine großartige APP zu erstellen. Erstellen Sie eine Teams-App mit wenig bis gar keinen Code mithilfe der Microsoft Power-Plattform.

   > [!div class="nextstepaction"]
   > [Importieren einer Power Platform-App](doc-links/importing-custom-microsoft-apps.md)

## <a name="resources"></a>Ressourcen

* [Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website](doc-links/share-to-teams.md)
* [Entwerfen Ihrer App mithilfe empfohlener Richtlinien](doc-links/designing-overview.md)
* [Fluent-Benutzeroberflächen-Entwurfs System](https://fluentsite.z22.web.core.windows.net/)
* [Microsoft Teams JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest)
* [Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [bot Framework SDK für .net](https://github.com/Microsoft/botbuilder-dotnet/)
