---
title: Webhooks und Connectors
author: clearab
description: In diesem Modul erfahren Sie, wie Webhooks und Connectors Ihre Webdienste mit dem Teams-Client verbinden können.
ms.localizationpriority: high
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: bb453367eb0d8f4c2c1a54681d67dc38fb3e0358
ms.sourcegitcommit: ef545fac5c0dbe970d81f53b1631930e9196eba3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2022
ms.locfileid: "67991649"
---
# <a name="webhooks-and-connectors"></a>Webhooks und Connectors

Webhooks und Connectors helfen beim Verbinden der Webdienste mit Kanälen und Teams in Microsoft Teams. Webhooks sind benutzerdefinierte HTTP-Rückrufe, mit denen Benutzer über alle Aktionen benachrichtigt werden, die im Teams-Kanal ausgeführt wurden. Es ist eine Möglichkeit für eine App, Echtzeitdaten abzurufen. Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren. Sie stellen einen HTTPS-Endpunkt für Ihren Dienst bereit, um Nachrichten in Form von Karten zu posten.

> [!IMPORTANT]
> Sie können die Teams-App des Benachrichtigungs-Bots erstellen, die keine eingehenden Webhooks ist. Sie funktionieren ähnlich, aber der Benachrichtigungs-Bot hat mehr Funktionen. Weitere Informationen finden Sie im [Buildbenachrichtigungs-Bot mit JavaScript](../sbs-gs-notificationbot.yml) oder [im Beispiel für eingehende Webhook-Benachrichtigungen](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/incoming-webhook-notification). Um zu beginnen, laden Sie das [Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) jetzt herunter, und erkunden Sie es. Weitere Informationen finden Sie in den [Teams-Toolkit-Dokumenten](../toolkit/teams-toolkit-fundamentals.md).

## <a name="outgoing-webhooks"></a>Ausgehende Webhooks

Webhooks hilft Teams bei der Integration in externe Apps. Mit ausgehenden Webhooks können Sie Textnachrichten von einem Kanal an die Webdienste senden. Nach dem Konfigurieren der ausgehenden Webhooks können Benutzer Outgoing Webhook via @mention erwähnen und eine Nachricht an Webdienste senden. Der Dienst antwortet innerhalb von 10 Sekunden mit einem Text oder einer Karte auf die Nachricht.

> [!NOTE]
> Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden.

## <a name="connectors"></a>Connectors

Connectors ermöglichen Benutzern das Abonnieren von Benachrichtigungen und Nachrichten von den Webdiensten. Sie machen den HTTPS-Endpunkt für den Dienst verfügbar, um Nachrichten in Teams Kanälen zu posten, in der Regel in Form von Karten.

### <a name="incoming-webhooks"></a>Eingehende Webhooks

Eingehende Webhooks helfen beim Veröffentlichen von Nachrichten aus Apps in Teams. Wenn eingehende Webhooks für ein Team in einem beliebigen Kanal aktiviert sind, wird der HTTPS-Endpunkt verfügbar gemacht, der korrekt formatierte JSON akzeptiert und die Nachrichten in diesen Kanal einfügt. Sie können z. B. einen eingehenden Webhook in Ihrem DevOps-Kanal erstellen, Ihren Build konfigurieren und gleichzeitig Dienste bereitstellen und überwachen, um Warnungen zu senden.

#### <a name="notification-bot-or-incoming-webhook---choose-the-right-one"></a>Benachrichtigungs-Bot oder eingehender Webhook – wählen Sie den richtigen aus

Bevor Sie mit dem Erstellen eingehender Webhooks beginnen, sollten Sie auch wissen, dass Sie den Benachrichtigungs-Bot mithilfe des Teams-Toolkits erstellen können. Benachrichtigungs-Bots können eine anpassbare Benutzeroberfläche ermöglichen, um verschiedene Geschäftsszenarien zu erfüllen.

Erfahren Sie mehr über die Unterschiede zwischen dem Benachrichtigungs-Bot und dem eingehenden Webhook, damit Sie die richtigen Lösungen für Ihre Szenarien auswählen können:

| &nbsp; | Benachrichtigungs-Bot |  Eingehender Webhook |
| --- | --- | --- |
| Was ist das? | Eine Teams-App | Ein Teams-Feature |
| Installation erforderlich | Ja | Nein |
| Geeignete Szenarien | • Regelmäßige Benachrichtigungen und Nachrichten in regelmäßigen Abständen erhalten, z. B. tägliche Benachrichtigungen über Teamaufgaben. <br>  • Empfangen von Benachrichtigungen und Nachrichten basierend auf realen Ereignissen. Wenn Teamkollegen beispielsweise Dateien hochladen, erhalten Sie Benachrichtigungen. | Kommunikation mit externen Apps und Empfangen von Benachrichtigungen und Nachrichten von anderen Apps. |
| Bereichskonfiguration | • Teams-Kanal <br> • Gruppenchat <br> • Persönlicher Chat | Teams channel |
| Nachrichtenprozess | Ein Benachrichtigungs-Bot funktioniert als Teams-Anwendung. Sie können Ihre Geschäftslogik definieren, um Daten zu verarbeiten und Daten in einem angepassten Format anzuzeigen. | Webhook ist ein Microsoft Teams-Feature anstelle einer Teams-Anwendung, sodass nur Daten ohne Verarbeitung empfangen und angezeigt werden. |
| Abrufen des Teams-Kontexts | Der Benachrichtigungs-Bot kann Teams-Kontext wie den Kanal oder Benutzerinformationen, Nachrichten usw. abrufen. | Nein |
| Adaptive Karte senden | Ja | Ja |
| Senden einer Willkommensnachricht | Kann eine Willkommensnachricht senden | Keine Willkommensnachricht |
| Trigger unterstützt | Alle Trigger werden unterstützt. Wenn Sie das Teams-Toolkit verwenden, können Sie Vorlagenprojekte mit den folgenden Triggern schnell abrufen: <br> • Zeittrigger, der in Azure-Funktionen gehostet wird. <br> • Erneutes Bestätigen des HTTP-Triggers, der im Azure-App-Dienst gehostet wird <br> • HTTP-Trigger, der auf Azure Functions gehostet wird | Alle triggers supported |
| Erstellungstools | • [Übersicht über das Teams-Toolkit für Visual Studio Code](../toolkit/teams-toolkit-fundamentals.md) <br> • [Übersicht über das Teams-Toolkit für Visual Studio](../toolkit/teams-toolkit-fundamentals.md) <br> • [TeamsFx-Bibliothek](../toolkit/TeamsFx-CLI.md) <br> • [TeamsFx SDK](../toolkit/TeamsFx-SDK.md) | Keine Tools erforderlich |
| Cloudressource erforderlich | Azure Bot Framework | Keine Ressourcen erforderlich |
| Lernprogramm | [Erstellen eines Benachrichtigungsbots mit JavaScript](../sbs-gs-notificationbot.yml) | [Beispiel für eingehende Webhook-Benachrichtigungen](https://github.com/OfficeDev/TeamsFx-Samples/tree/dev/incoming-webhook-notification) |

### <a name="office-365-connectors"></a>Office 365-Connectors

Mit Office 365 Connectors können Sie eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und diese als Teil einer Teams-App zusammenfassen. Sie senden Nachrichten in erster Linie mit Office 365 Connectorkarten und haben die Möglichkeit, ihnen einen begrenzten Satz von Kartenaktionen hinzuzufügen. Beispielsweise ein Wetterconnector, mit dem Benutzer einen Ort und eine beliebige Tageszeit auswählen können, um Updates über das Wetter von morgen zu erhalten. Sie sind auf Kanalebene konfiguriert, aber auf Teamebene installiert.

> [!NOTE]
> Sie können die Office 365-Connector Teams-App an unseren AppStore leiten.

## <a name="create-and-send-messages"></a>Nachrichten erstellen und senden

Nachrichten mit Aktionen ermöglichen es Benutzern, Maßnahmen zu ergreifen, ohne ihren E-Mail-Client zu verlassen, was die Benutzereinbindung erhöht. Mit Office 365 und eingehenden Webhooks können Sie Nachrichten senden, indem Sie eine JSON-Nutzlast an die Webhook-URL senden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
* [Erstellen eines Benachrichtigungsbots mit JavaScript](../sbs-gs-notificationbot.yml)
* [Erstellen Ihrer ersten Bot-App mit JavaScript](../sbs-gs-bot.yml)
