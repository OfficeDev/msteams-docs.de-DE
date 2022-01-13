---
title: Bots in Microsoft Teams
author: surbhigupta
description: Eine Übersicht über Bots in Microsoft Teams.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: a9f53654ba3240b973b77c05cd64a22c80237350
ms.sourcegitcommit: a6c39106ccc002d02a65e11627659e0c48981d8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2022
ms.locfileid: "62014563"
---
# <a name="bots-in-microsoft-teams"></a>Bots in Microsoft Teams

Ein Bot wird auch als Chatbot oder Unterhaltungs-Bot bezeichnet. Es handelt sich um eine App, die einfache und sich wiederholende Aufgaben von Benutzern wie Kundendienst oder Supportmitarbeitern ausführt. Die tägliche Verwendung von Bots umfasst Bots, die Informationen über das Wetter bereitstellen, Reservierungen vornehmen oder Reiseinformationen bereitstellen. Interaktionen mit Bots können schnell fragen und beantworten oder eine komplexe Unterhaltung sein.

> [!IMPORTANT]
> Derzeit sind Bots in Government Community Cloud (GCC) und nicht in GCC-High und Department of Defense (DOD) verfügbar.

Unterhaltungs-Bots ermöglichen Benutzern die Interaktion mit Ihrem Webdienst mithilfe von Text, interaktiven Karten und Aufgabenmodulen.

![Aufrufen eines Bots mithilfe von Text](~/assets/images/invokebotwithtext.png)

![Aufrufen eines Bots mithilfe einer Karte](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

Unterhaltungsbots sind unglaublich flexibel. Bots können einige grundlegende Befehle oder komplexe Aufgaben verarbeiten, die künstliche Intelligenz und verarbeitung natürlicher Sprache umfassen. Bots können Teil einer größeren Anwendung oder eigenständig sein.

Verwenden Sie die richtige Mischung aus Karten, Text und Aufgabenmodulen, um einen nützlichen Bot zu erstellen. Die folgende Abbildung zeigt einen Benutzer, der sich mit einem Bot in einem 1:1-Chat mit Text und interaktiven Karten unterhält.

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Beispiel für häufig gestellte Fragen (FAQ)-Bot" border="true":::

Jede Interaktion zwischen dem Benutzer und dem Bot wird als Aktivität dargestellt. Wenn ein Bot eine Aktivität empfängt, übergibt er sie an seine Aktivitätshandler. Siehe [Bot-Aktivitätshandler.](~/bots/bot-basics.md)

Bots sind Apps, die über eine Unterhaltungsoberfläche verfügen. Sie können mit einem Bot mit Text, interaktiven Karten und Sprache interagieren. Ein Bot verhält sich in einer Kanal- oder Gruppenchatunterhaltung und in einer 1:1-Unterhaltung anders. Unterhaltungen werden über den Bot Framework-Connector verarbeitet. Grundlegendes [zu Unterhaltungen.](~/bots/how-to/conversations/conversation-basics.md)

Ihr Bot erfordert Kontextinformationen, z. B. Benutzerprofildetails, um auf relevante Inhalte zuzugreifen und die Bot-Erfahrung zu verbessern. Weitere Informationen finden Sie [unter abrufen Teams Kontext.](~/bots/how-to/get-teams-context.md)

Sie können Dateien über den Bot senden und empfangen, indem Sie Graph-APIs oder Teams-Bot-APIs verwenden. Siehe ["Senden und Empfangen von Dateien über den Bot".](~/bots/how-to/bots-filesv4.md)

Die Begrenzung der Raten wird verwendet, um Bots zu optimieren, die für Ihre Teams-Anwendung verwendet werden. Um Microsoft Teams und ihre Benutzer zu schützen, bieten die Bot-APIs ein Preislimit für eingehende Anforderungen. Sehen Sie [sich die Optimierung Ihres Bots mit einer Begrenzung der Raten in Teams an.](~/bots/how-to/rate-limit.md)

Mit Microsoft Graph-APIs für Anrufe und Onlinebesprechungen können Microsoft Teams Apps jetzt mit Benutzern per Sprach- und Videofunktion interagieren. Siehe [Anrufe und Besprechungen Bots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

Sie können die Teams-Bot-APIs verwenden, um Informationen für Mitglieder eines Chats oder Teams abzurufen. Änderungen [an Teams Bot-APIs zum Abrufen von Team- oder Chatmitgliedern](~/resources/team-chat-member-api-changes.md)finden Sie unter .

<!--- TBD: For quick scanning, see if the above information can be itemized as a list.
--->

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Tools und SDKs](~/bots/bot-features.md)

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C # | Node.js |
|----------------|-----------------|--------------|--------------|
| Tägliche Bot-Aufgabenerinnerung| Vorführen, wie sie eine Terminserie planen und zu einem geplanten Zeitpunkt eine Erinnerung erhalten. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)
* [Registrieren von Anrufen und Besprechungsbots für Microsoft Teams](~/bots/calls-and-meetings/registering-calling-bot.md)
* [Hinzufügen der Authentifizierung zu Ihrem Teams-Bot](~/bots/how-to/authentication/add-authentication.md)
* [Bot-Aktivitätenhandler](~/bots/bot-basics.md)
* [Unterhaltungsereignisse in Ihrem Teams-Bot](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
