---
title: Bots in Microsoft Teams
author: surbhigupta
description: Eine Übersicht über Bots in Microsoft Teams.
ms.topic: overview
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: fbf7f7b1f4e863ec7612a404b5576baf40035d21
ms.sourcegitcommit: 8ae93b7bfffff77a5b9cb7a5d287f202e73ea9be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952303"
---
# <a name="bots-in-microsoft-teams"></a>Bots in Microsoft Teams

Ein Bot wird auch als Chatbot oder Unterhaltungsbot bezeichnet. Es handelt sich um eine App, die einfache und sich wiederholende Aufgaben von Benutzern ausführt, z. B. Kundendienst- oder Supportmitarbeiter. Die tägliche Verwendung von Bots umfasst Bots, die Informationen über das Wetter bereitstellen, Essensreservierungen durchführen oder Reiseinformationen bereitstellen. Interaktionen mit Bots können kurze Fragen und Antworten oder komplexe Unterhaltungen sein.

> [!IMPORTANT]
> Derzeit sind Bots in Government Community Cloud (GCC) verfügbar, aber nicht in GCC-High und Department of Defense (DOD).

Unterhaltungs-Bots ermöglichen es Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren.

![Aufrufen eines Bots mithilfe von Text](~/assets/images/invokebotwithtext.png)

![Aufrufen eines Bots mithilfe einer Karte](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

Unterhaltungsbots sind unglaublich flexibel. Bots können einige Basisbefehle verarbeiten oder komplexe Aufgaben, die künstliche Intelligenz und die Verarbeitung natürlicher Sprache erfordern. Bots können Teil einer größeren Anwendung oder eigenständig sein.

Verwenden Sie die richtige Mischung aus Karten, Text und Aufgabenmodulen, um einen nützlichen Bot zu erstellen. Das folgende Bild zeigt einen Benutzer, der sich in einem 1:1-Chat mit einem Bot über Text und interaktive Karten unterhält.

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Beispiel eines FAQ-Bots" border="true":::

Jede Interaktion zwischen dem Benutzer und dem Bot wird als eine Aktivität dargestellt. Wenn ein Bot eine Aktivität empfängt, übergibt er diese an seine Aktivitätshandler. Weitere Informationen finden Sie unter [Bot-Aktivitätshandler](~/bots/bot-basics.md).

Bots sind Apps, die über eine Unterhaltungsschnittstelle verfügen. Sie können mithilfe von Text, interaktiven Karten und Sprache mit einem Bot interagieren. Ein Bot verhält sich in einer Kanal- oder Gruppenchatunterhaltung anders als in einer 1:1-Unterhaltung. Unterhaltungen werden über den Bot Framework-Connector verarbeitet. Weitere Informationen finden Sie unter [Grundlagen zu Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md).

Ihr Bot benötigt Kontextinformationen, z. B. Benutzerprofildetails, um auf relevante Inhalte zuzugreifen und das Boterlebnis zu verbessern. Weitere Informationen finden Sie unter [Abrufen des Teams-Kontexts](~/bots/how-to/get-teams-context.md).

Sie können Dateien über den Bot mithilfe von Graph-APIs oder Teams-Bot-APIs senden und empfangen. Weitere Informationen finden Sie unter [Senden und Empfangen von Dateien über den Bot](~/bots/how-to/bots-filesv4.md).

Die Ratenbegrenzung wird verwendet, um Bots zu optimieren, die für Ihre Teams-Anwendung verwendet werden. Um Microsoft Teams und seine Benutzer zu schützen, bieten die Bot-APIs eine Ratenbegrenzung für eingehende Anforderungen. Weitere Informationen finden Sie unter [Optimieren eines Bots mit Ratenbegrenzung in Teams](~/bots/how-to/rate-limit.md).

Mit Microsoft Graph APIs für Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt per Sprache und Video mit Benutzern interagieren. Siehe [Anrufe und Meeting-Bots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

Sie können die Teams-Bot-APIs verwenden, um Informationen für Mitglieder eines Chats oder Teams abzurufen. Weitere Informationen finden Sie unter [Änderungen an Teams-Bot-APIs zum Abrufen von Team- oder Chatmitgliedern](~/resources/team-chat-member-api-changes.md).

<!--- TBD: For quick scanning, see if the above information can be itemized as a list.
--->

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Tools und SDKs](~/bots/bot-features.md)

## <a name="code-samples"></a>Codebeispiele

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Tägliche Aufgabenerinnerung des Bots| Zeigen Sie, wie Sie eine wiederkehrende Aufgabe planen und eine Erinnerung zu einem bestimmten Zeitpunkt erhalten. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-daily-task-reminder/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)
* [Funktionsweise von Microsoft Teams-Bots](/azure/bot-service/bot-builder-basics-teams)
* [Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams](~/bots/calls-and-meetings/registering-calling-bot.md)
* [Authentifizierung für Ihren Teams-Bot hinzufügen](~/bots/how-to/authentication/add-authentication.md)
* [Bot-Aktivitätenhandler](~/bots/bot-basics.md)
* [Unterhaltungsereignisse in Ihrem Teams-Bot](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
