---
title: Bots in Microsoft Teams
author: clearab
description: Eine Übersicht über Bots in Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 08777e6d678bd75b56072412af46e3eb974c3678
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696894"
---
# <a name="bots-in-microsoft-teams"></a>Bots in Microsoft Teams

Ein Bot, der auch als Chatbot oder Unterhaltungsbot bezeichnet wird, ist eine App, in der einfache und sich wiederholende automatisierte Aufgaben ausgeführt werden, die von den Benutzern ausgeführt werden, z. B. vom Kundendienst oder vom Support. Beispiele für Bots im täglichen Gebrauch sind Bots, die Informationen über das Wetter bereitstellen, Reservierungen für Das Essen oder Reiseinformationen bereitstellen. Eine Botinteraktion kann eine schnelle Frage und Antwort oder eine komplexe Unterhaltung sein, die Zugriff auf Dienste bietet.

> [!VIDEO https://www.youtube-nocookie.com/embed/zSIysk0yL0Q]

Unterhaltungs-Bots ermöglichen Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren.

![Aufrufen des Bots mithilfe von Text](~/assets/images/invokebotwithtext.png)

![Aufrufen des Bots mithilfe der Karte](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

Unterhaltungsbots sind unglaublich flexibel und können für einige einfache Befehle oder komplexe Aufgaben mit künstlicher Intelligenz und natürlicher Sprache verwendet werden. Sie können ein Aspekt einer größeren Anwendung sein oder vollständig eigenständiger Sein.

Die Richtige Mischung aus Karten, Text und Aufgabenmodulen zu finden, ist der Schlüssel zum Erstellen eines nützlichen Bots. Die folgende Abbildung zeigt einen Benutzer, der mit einem Bot in einem 1:1-Chat mit Text- und interaktiven Karten konversiert:

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Beispiel-FAQ-Bot" border="true":::

Jede Interaktion zwischen dem Benutzer und dem Bot wird als Aktivität dargestellt. Wenn ein Bot eine Aktivität empfängt, wird sie an seine Aktivitätshandler übergeben. Weitere Informationen finden Sie unter [Bot-Aktivitätshandler .](~/bots/bot-basics.md) 

Darüber hinaus sind Bots Apps, die über eine Unterhaltungsschnittstelle verfügen. Sie können mit einem Bot mithilfe von Text, interaktiven Karten und Sprache interagieren. Ein Bot verhält sich anders, je nachdem, ob es sich bei der Unterhaltung um eine Kanal- oder Gruppenchat-Unterhaltung oder um eine 1:1-Unterhaltung handelt. Unterhaltungen werden über den Bot Framework-Connector behandelt. Weitere Informationen finden Sie unter [Conversation Basics](~/bots/how-to/conversations/conversation-basics.md).

Ihr Bot erfordert Kontextinformationen, z. B. Benutzerprofildetails, um auf relevante Inhalte zu zugreifen und die Boterfahrung zu verbessern. Weitere Informationen finden Sie unter [Get Teams context](~/bots/how-to/get-teams-context.md). 

Sie können Dateien auch über den Bot mithilfe von Graph-APIs oder Teams-Bot-APIs senden und empfangen. Weitere Informationen finden Sie unter [Senden und Empfangen von Dateien über den Bot](~/bots/how-to/bots-filesv4.md).

Darüber hinaus wird die Geschwindigkeitsbegrenzung verwendet, um Bots zu optimieren, die für Ihre Teams-Anwendung verwendet werden. Zum Schutz von Microsoft Teams und seinen Benutzern bieten die Bot-APIs eine Geschwindigkeitsbeschränkung für eingehende Anforderungen. Weitere Informationen finden Sie unter [Optimieren Ihres Bots mit Der Geschwindigkeitsbegrenzung in Teams](~/bots/how-to/rate-limit.md).

Mit Microsoft Graph-APIs für Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt mithilfe von Sprach- und Videonachrichten mit Benutzern interagieren. Weitere Informationen finden Sie unter [Anrufe und Besprechungsbots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md). 

Sie können die Teams-Bot-APIs verwenden, um Informationen für ein oder mehrere Mitglieder eines Chats oder Teams zu erhalten. Weitere Informationen finden Sie [unter Änderungen an Teams-Bot-APIs zum Abrufen von Team- oder Chatmitgliedern.](~/resources/team-chat-member-api-changes.md)

## <a name="see-also"></a>Weitere Informationen

> [!div class="nextstepaction"]
> [Erstellen eines Bots für Teams](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Tools und SDKs](~/bots/bot-features.md)
