---
title: Bots in Microsoft Teams
author: surbhigupta
description: Eine Übersicht über Bots in Microsoft Teams.
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 655684ef4f2a93d3f9c3858e3bf5a84eab4bd43c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068969"
---
# <a name="bots-in-microsoft-teams"></a>Bots in Microsoft Teams

Ein Bot, der auch als Chatbot oder Unterhaltungsbot bezeichnet wird, ist eine App, die einfache und wiederholte automatisierte Aufgaben ausführt, die von den Benutzern ausgeführt werden, z. B. Kundendienst- oder Supportmitarbeiter. Beispiele für Bots im täglichen Gebrauch sind Bots, die Informationen über das Wetter bereitstellen, Reservierungen vornehmen oder Reiseinformationen bereitstellen. Eine Bot-Interaktion kann eine schnelle Frage und Antwort sein oder eine komplexe Unterhaltung, die Zugriff auf Dienste bietet.

> [!VIDEO https://www.youtube-nocookie.com/embed/zSIysk0yL0Q]

Unterhaltungsbots ermöglichen Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren.

![Aufrufen eines Bots mithilfe von Text](~/assets/images/invokebotwithtext.png)

![Aufrufen eines Bots mithilfe einer Karte](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

Unterhaltungs-Bots sind unglaublich flexibel und können so ausgelegt werden, dass sie einige einfache Befehle oder komplexe, von künstlicher Intelligenz unterstützte Und Verarbeitungsaufgaben in natürlicher Sprache verarbeiten. Sie können ein Aspekt einer größeren Anwendung oder vollständig eigenständig sein.

Die richtige Mischung aus Karten, Text und Aufgabenmodulen zu finden, ist der Schlüssel zum Erstellen eines nützlichen Bots. Die folgende Abbildung zeigt einen Benutzer, der sich mit einem Bot in einem 1:1-Chat mit textbasierten und interaktiven Karten unterhält:

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Beispiel für häufig gestellte Fragen (FAQ)-Bot" border="true":::

Jede Interaktion zwischen dem Benutzer und dem Bot wird als Aktivität dargestellt. Wenn ein Bot eine Aktivität empfängt, übergibt er sie an seine Aktivitätshandler. Weitere Informationen finden Sie unter [Bot-Aktivitätshandler.](~/bots/bot-basics.md) 

Darüber hinaus sind Bots Apps, die über eine Unterhaltungsoberfläche verfügen. Sie können mit einem Bot mit Text, interaktiven Karten und Sprache interagieren. Ein Bot verhält sich anders, je nachdem, ob es sich bei der Unterhaltung um eine Kanal- oder Gruppenchatunterhaltung oder um eine 1:1-Unterhaltung handelt. Unterhaltungen werden über den Bot Framework-Connector verarbeitet. Weitere Informationen finden Sie unter [Unterhaltungsgrundlagen.](~/bots/how-to/conversations/conversation-basics.md)

Ihr Bot erfordert Kontextinformationen, z. B. Benutzerprofildetails, um auf relevante Inhalte zuzugreifen und die Bot-Erfahrung zu verbessern. Weitere Informationen finden Sie unter [abrufen Teams Kontext.](~/bots/how-to/get-teams-context.md) 

Sie können Dateien auch über den Bot senden und empfangen, indem Sie Graph-APIs oder Teams-Bot-APIs verwenden. Weitere Informationen finden Sie unter [Senden und Empfangen von Dateien über den Bot.](~/bots/how-to/bots-filesv4.md)

Darüber hinaus wird die Ratenbegrenzung verwendet, um Bots zu optimieren, die für Ihre Teams-Anwendung verwendet werden. Um Microsoft Teams und seine Benutzer zu schützen, bieten die Bot-APIs ein Preislimit für eingehende Anforderungen. Weitere Informationen finden Sie unter [Optimieren Ihres Bots mit Einer Begrenzung der Rate in Teams.](~/bots/how-to/rate-limit.md)

Mit Microsoft Graph-APIs für Anrufe und Onlinebesprechungen können Microsoft Teams Apps jetzt per Sprach- und Videofunktion mit Benutzern interagieren. Weitere Informationen finden Sie unter ["Bots für Anrufe und Besprechungen".](~/bots/calls-and-meetings/calls-meetings-bots-overview.md) 

Sie können die Teams-Bot-APIs verwenden, um Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abzurufen. Weitere Informationen finden Sie unter [Änderungen an Teams Bot-APIs zum Abrufen von Team- oder Chatmitgliedern.](~/resources/team-chat-member-api-changes.md)

## <a name="see-also"></a>Siehe auch

[Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Tools und SDKs](~/bots/bot-features.md)
