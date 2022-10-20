---
title: Erstellen erweiterbarer Unterhaltungen für Besprechungschats
author: v-sdhakshina
description: In diesem Artikel erfahren Sie, wie Sie erweiterbare Unterhaltungen für Microsoft Teams-Besprechungschats mit Bots, Karten und Nachrichtenerweiterungen erstellen.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.openlocfilehash: 65fc91d51cd4c740f28d5f33a2ad578f214c20a8
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615448"
---
# <a name="build-extensible-conversation-for-meeting-chat"></a>Erstellen erweiterbarer Unterhaltungen für Besprechungschats

Sie können Unterhaltungen in Microsoft Teams-Besprechungen erweiterbar machen. Bots, Nachrichtenerweiterungen, Karten und Aufgabenmodule können kombiniert werden, um eine intuitive Erfahrung zu bieten.

## <a name="bots"></a>Bots

Ein Bot wird auch als Chatbot oder Unterhaltungsbot bezeichnet. Es handelt sich um eine App, die einfache und sich wiederholende Aufgaben von Benutzern ausführt, z. B. Kundendienst- oder Supportmitarbeiter. Die tägliche Verwendung von Bots umfasst Bots, die Informationen über das Wetter bereitstellen, Essensreservierungen durchführen oder Reiseinformationen bereitstellen. Interaktionen mit Bots können kurze Fragen und Antworten oder komplexe Unterhaltungen sein. Ein Bot muss im `team` Bereich für eine Kanalbesprechung und im `groupchat` Bereich für alle anderen Besprechungstypen aktiviert werden. Um Bots zu implementieren, beginnen [Sie mit dem Erstellen eines Bots](/microsoftteams/platform//sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode).

### <a name="bot-apis"></a>Bot-APIs

[Microsoft Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zur Erstellung von Bots mit C#, Java, Python und JavaScript. Wenn Sie bereits über einen Bot verfügen, der auf Microsoft Bot Framework basiert, können Sie ihn mühelos zur Verwendung in Microsoft Teams ändern. Microsoft empfiehlt die Verwendung von C# oder Node.js, um unsere [SDKs](/microsoftteams/platform/) nutzen zu können.

### <a name="code-samples---bots"></a>Codebeispiele – Bots

|Beispielname | Beschreibung | .NETCore | Node.js | Python |
|----------------|-----------------|--------------|----------------|
| Teams-Unterhaltungsbot | Verarbeitung von Nachrichten- und Unterhaltungsereignissen | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |
|Bot-Beispiele | Gruppe von Bot-Beispielen  | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python) |

## <a name="message-extensions"></a>Nachrichtenerweiterungen

Nachrichtenerweiterungen ermöglichen es den Benutzern, mit Ihrem Webdienst über Schaltflächen und Formulare im Teams-Client zu interagieren. Benutzer können Aktionen in einem externen System über den Nachrichtenbereich zum Verfassen, das Befehlsfeld oder direkt aus einer Nachricht durchsuchen oder initiieren. Sie können die Ergebnisse dieser Interaktion in Form einer reich formatierten Karte an den Teams-Client zurücksenden. Die Implementierung von Nachrichtenerweiterungen für Besprechungschats unterscheidet sich nicht von normalen Chats. Um die Nachrichtenerweiterung zu implementieren, beginnen Sie mit [Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions?tabs=dotnet).

## <a name="cards-and-task-modules"></a>Karten und Aufgabenmodule

Karten bieten Benutzern verschiedene visuelle, audio- und auswählbare Nachrichten sowie Hilfe beim Unterhaltungsfluss. Mit Aufgabenmodulen können Sie modale Popuperfahrungen in Teams erstellen. Sie sind nützlich zum Starten und Abschließen der Aufgaben oder zum Anzeigen umfangreicher Informationen wie Videos oder Power Business Intelligence (BI)-Dashboards. Weitere Informationen finden Sie unter [Erstellen von Karten und Aufgabenmodulen](/microsoftteams/platform/task-modules-and-cards/cards-and-task-modules).

## <a name="feature-compatibility-by-user-types"></a>Featurekompatibilität nach Benutzertypen

Die folgende Tabelle enthält die Benutzertypen und listet die Features auf, auf die jeder Benutzer in Besprechungen zugreifen kann:

| Benutzertyp | Bots | Nachrichtenerweiterungen | Adaptive Karten | Aufgabenmodule |
| :-- | :-- | :-- | :-- | :-- |
| Mandantenspezifischer Benutzer | Verfügbar | Verfügbar | Verfügbar | Verfügbar |
| Gast, Teil des Mandanten Azure AD | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat über die adaptive Karte sind zulässig. |
| Verbundbenutzer finden weitere Informationen unter [nicht standardmäßigen Benutzern](/microsoftteams/non-standard-users). | Interaktion ist zulässig. Abrufen, Aktualisieren und Löschen sind nicht zulässig. | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat über die adaptive Karte sind zulässig. |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Nicht verfügbar |

## <a name="see-also"></a>Siehe auch

* [Entwerfen Ihrer Microsoft Teams-Nachrichtenerweiterung](../messaging-extensions/design/messaging-extension-design.md)
* [Entwerfen von Aufgabenmodulen für Ihre Microsoft Teams-App](../task-modules-and-cards/task-modules/design-teams-task-modules.md)
