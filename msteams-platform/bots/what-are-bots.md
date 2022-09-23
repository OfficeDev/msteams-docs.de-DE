---
title: Bots in Microsoft Teams
author: surbhigupta
description: Verwenden Sie in diesem Artikel Unterhaltungsbots in Microsoft Teams, um Dateien freizugeben, proaktive Benachrichtigungen zu senden, interaktive Karten zu senden, Anrufe zu tätigen, Bot-Befehl aufzurufen, IVR.
ms.topic: overview
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: b9d0bda0d733a3b4a3204449ca9fd2ed6746ac98
ms.sourcegitcommit: b9ec2a17094cb8b24c3017815257431fb0a679d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2022
ms.locfileid: "67990910"
---
# <a name="build-bots-for-teams"></a>Erstellen von Bots für Teams

Ein Bot wird auch als Chatbot oder Unterhaltungsbot bezeichnet. Es handelt sich um eine App, die einfache und sich wiederholende Aufgaben von Benutzern ausführt, z. B. Kundendienst- oder Supportmitarbeiter. Die tägliche Verwendung von Bots umfasst Bots, die Informationen über das Wetter bereitstellen, Essensreservierungen durchführen oder Reiseinformationen bereitstellen. Interaktionen mit Bots können kurze Fragen und Antworten oder komplexe Unterhaltungen sein.

> [!NOTE]
> Es wird empfohlen, mit dem [Erstellen Ihrer ersten Bot-App mit JavaScript](../sbs-gs-bot.yml) oder [dem Buildbenachrichtigungs-Bot mit JavaScript](../sbs-gs-notificationbot.yml) mithilfe des Entwicklungstools der neuen Generation für Teams zu beginnen. Weitere Informationen finden Sie in der [Übersicht über das Teams-Toolkit](../toolkit/teams-toolkit-fundamentals.md).

> [!IMPORTANT]
>
> * Derzeit sind Bots in Government Community Cloud (GCC) und in GCC-High verfügbar, aber nicht in Department of Defense (DOD).
>
> * Bot-Anwendungen innerhalb von Microsoft Teams sind in GCC-High über [Azure Bot Service](/azure/bot-service/how-to-deploy-gov-cloud-high) verfügbar, und die Registrierung des Bot-Kanals muss im Azure Government-Portal erfolgen.
>
> * Anwendungen in GCCH unterstützen nur bis zur Manifestversion v1.10. Bild-URLs in adaptiven Karten werden in der GCCH-Umgebung nicht unterstützt. Sie können eine Bild-URL durch Base64-codierte DataUri ersetzen.

Unterhaltungs-Bots ermöglichen es Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren.

:::image type="content" source="../assets/images/invokebotwithtext.png" alt-text="Der Screenshot ist ein Beispiel, das einen Webdienst mit Text zeigt."lightbox="../assets/images/invokebotwithtext.png":::

:::image type="content" source="../assets/images/invokebotwithcard.png" alt-text="Der Screenshot ist ein Beispiel für einen Webdienst mit interaktiven Karten."lightbox="../assets/images/invokebotwithcard.png"border="true":::

:::image type="content" source="../assets/images/task-module-example.png" alt-text="Der Screenshot ist ein Beispiel für einen Webdienst mithilfe des Aufgabenmoduls." lightbox="../assets/images/task-module-example-expanded.png":::

Unterhaltungsbots sind unglaublich flexibel. Bots können einige Basisbefehle verarbeiten oder komplexe Aufgaben, die künstliche Intelligenz und die Verarbeitung natürlicher Sprache erfordern. Bots können Teil einer größeren Anwendung oder eigenständig sein.

Verwenden Sie die richtige Mischung aus Karten, Text und Aufgabenmodulen, um einen nützlichen Bot zu erstellen. Das folgende Bild zeigt einen Benutzer, der sich in einem 1:1-Chat mit einem Bot über Text und interaktive Karten unterhält.

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Der Screenshot ist ein Beispiel für einen FAQ-Beispiel-Bot.":::

Jede Interaktion zwischen dem Benutzer und dem Bot wird als eine Aktivität dargestellt. Wenn ein Bot eine Aktivität empfängt, übergibt er diese an seine Aktivitätshandler. Weitere Informationen finden Sie unter [Bot-Aktivitätshandler](~/bots/bot-basics.md).

Bots sind Apps, die über eine Unterhaltungsschnittstelle verfügen. Sie können mithilfe von Text, interaktiven Karten und Sprache mit einem Bot interagieren. Ein Bot verhält sich in einer Kanal- oder Gruppenchatunterhaltung anders als in einer 1:1-Unterhaltung. Unterhaltungen werden über den Bot Framework-Connector verarbeitet. Weitere Informationen finden Sie unter [Grundlagen zu Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md).

Ihr Bot benötigt Kontextinformationen, z. B. Benutzerprofildetails, um auf relevante Inhalte zuzugreifen und die Boterfahrung zu verbessern. Weitere Informationen finden Sie unter [Teams-Kontext abrufen](~/bots/how-to/get-teams-context.md).

Sie können Dateien über den Bot mithilfe von Graph-APIs oder Teams-Bot-APIs senden und empfangen. Weitere Informationen finden Sie unter [Senden und Empfangen von Dateien über den Bot](~/bots/how-to/bots-filesv4.md).

Die Ratenbegrenzung wird verwendet, um Bots zu optimieren, die für Ihre Teams-Anwendung verwendet werden. Um Teams und seine Benutzer zu schützen, bieten die Bot-APIs eine Ratenbegrenzung für eingehende Anforderungen. Weitere Informationen finden Sie unter [Optimieren eines Bots mit Ratenbegrenzung in Teams](~/bots/how-to/rate-limit.md).

Mit Microsoft Graph-APIs für Anrufe und Onlinebesprechungen können Teams-Apps jetzt per Sprache und Video mit Benutzern interagieren. Weitere Informationen finden Sie unter [Anruf- und Besprechungsbots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).

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
| Hallo Welt Bot | Dies ist eine einfache Hello World-Anwendung mit Bot- und Nachrichtenerweiterungsfunktionen. |  | [Anzeigen](https://github.com/OfficeDev/TeamsFx-Samples/tree/v1.0.0/hello-world-bot) |
| Benachrichtigung über adaptive Karten | Dies ist ein Beispiel, das zeigt, wie Benachrichtigungen mit verschiedenen adaptiven Karten mithilfe von Bots gesendet werden. |  | [Anzeigen](https://github.com/OfficeDev/TeamsFx-Samples/tree/v1.0.0/adaptive-card-notification) |
| Eingehende Webhook-Benachrichtigung | Dies ist ein Beispiel, das zeigt, wie Sie Benachrichtigungen über eingehenden Webhook in Microsoft Teams-Kanälen senden. |  | [Anzeigen](https://github.com/OfficeDev/TeamsFx-Samples/tree/v1.0.0/incoming-webhook-notification) |

## <a name="see-also"></a>Siehe auch

* [Erstellen eines Bots für Teams](../resources/bot-v3/bots-create.md)
* [Funktionsweise von Microsoft Teams-Bots](/azure/bot-service/bot-builder-basics-teams)
* [Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams](~/bots/calls-and-meetings/registering-calling-bot.md)
* [Authentifizierung für Ihren Teams-Bot hinzufügen](~/bots/how-to/authentication/add-authentication.md)
* [Bot-Aktivitätenhandler](~/bots/bot-basics.md)
* [Unterhaltungsereignisse in Ihrem Teams-Bot](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* [Erstellen Ihrer ersten Bot-App mit JavaScript](../sbs-gs-bot.yml)
* [Erstellen eines Benachrichtigungsbots mit JavaScript](../sbs-gs-notificationbot.yml)
