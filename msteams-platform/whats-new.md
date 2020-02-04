---
title: Neuerungen
description: Beschreibt alle neuen Entwicklerfeatures in Microsoft Teams
keywords: Teams What es New Latest
ms.openlocfilehash: ad02795c7ab84e290b83e781ea413dd3ef797fdb
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674056"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Neuerungen für Entwickler in Microsoft Teams

## <a name="change-log"></a>Änderungsprotokoll

Im Änderungsprotokoll werden Änderungen an der Microsoft Teams-Plattform und dieser Dokumentenmappe aufgelistet. Gelegentlich können Einträge verwendet werden, um die Aufmerksamkeit auf ein neues Feature zu lenken, das für Entwickler von Teams einfach interessant ist.

| **Date** | **Hinweise** | **Geänderte Themen** |
| -------- | --------- | ------------------ |
| 12/26/2019 | Der `replyToId` Parameter in Nutzlasten, die an einen bot gesendet werden, ist nicht mehr verschlüsselt, sodass Sie diesen Wert verwenden können, um Deeplinks für diese Nachrichten zu erstellen. Nachrichten Nutzlasten enthalten die verschlüsselten Werte im `legacy.replyToId`Parameter.  |
| 11/5/2019 | Einmaliges Anmelden mit dem Microsoft Teams-JavaScript-SDK in einer Webinhalts Seite befindet sich in der Entwicklervorschau | [Einmaliges Anmelden](~/tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Unter Haltungs Bots und Messaging-Erweiterungs Dokumentation aktualisiert, um das 4,6 bot Framework SDK widerzuspiegeln. Die Dokumentation für das V3 SDK steht im Abschnitt Resources zur Verfügung. | Alle bot-und Messaging-Erweiterungs Dokumentation. |
| 10/31/2019 | Neue Dokumentationsstruktur und wichtige Artikel Umgestaltung. Melden Sie alle Dead Links oder 404s, indem Sie ein GitHub-Problem erstellen. | Alle! |
| 9/13/2019 | Anforderungs-bot wird von der Aktions basierten Messaging Erweiterung installiert | [Initiieren von Aktionen mit Messaging Erweiterungen](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 8/28/2019 | Unterstützung für private Kanäle in Registerkarten und Connectors | [Kontext für die Registerkarte abrufen](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Freigeben einer externen Website von einer externen Website in einen Teams-Kanal | [Freigeben für Teams](~/share-to-teams.md) |
| 05/25/2019 | Antworten mit bot-Nachrichten aus dem Aufgabenmodul | [Antworten mit bot-Nachrichten aus dem Aufgabenmodul](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots in Gruppenchats | [Interagieren mit einem bot im Gruppenchat oder-Kanal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | App-Manifest-Lokalisierung | [App-Lokalisierung](~/publishing/apps-localization.md) |
| 05/20/2019 | Nachrichten Aktionen | [Nachrichten Aktionen](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Verknüpfungs Entfaltung (benutzerdefinierte URL-Vorschau) | [Link-Entfaltung](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Anwendungs Zertifizierungsprogramm für Store-Apps | [Anwendungszertifizierung](~/publishing/application-certification.md) |
| 05/06/2019 | App-Vorlagen sind jetzt verfügbar. | [App-Vorlagen](~/samples/app-templates.md) |
| 04/23/2019 | Aktionsbasierte Messaging Erweiterungen sind jetzt verfügbar | [Aktionsbasierte Nachrichten Erweiterungen](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | Das Erstellen von Deep Links zu privatem Chat erfolgt außerhalb der Entwicklervorschau und verfügbar | [Deep Linking to a Chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Informationen zur Oberflächen-SKU und zu licencetype im Registerkartenkontext | [Registerkartenkontext](~/concepts/tabs/tabs-context.md) |
| 12.11.2018 | Registerkarten im Gruppenchat sind jetzt in der veröffentlichten Version von Teams verfügbar und wurden aus der Entwicklervorschau verschoben. Im Rahmen dieser Arbeit wurde der Abschnitt Tabs aus Gründen der Übersichtlichkeit überarbeitet.| [Konfigurierbare Registerkarten](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | Erste Schritte für Node js und .NET/C# wurden für die Verwendung von App Studio in Microsoft Teams aktualisiert, und ein neuer Abschnitt wurde hinzugefügt, um Apps für Node-basierte Teams in Azure zu hosten. | Erste [Schritte mit der Microsoft Teams-Plattform mit C#/.net und App Studio](~/get-started/get-started-dotnet-app-studio.md), erste [Schritte mit der Microsoft Teams-Plattform mit Node js und App Studio](~/get-started/get-started-nodejs-app-studio.md), [Hosten der Node Teams-app in Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Sie können nun tiefe Links zu privaten Chats zwischen Benutzern erstellen. | [Deep Linking to a Chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 08.11.2018 | SharePoint Framework 1,7 hat und mit ihm ein neues Feature zur Verwendung von Microsoft Teams-Registerkarten als SharePoint-Framework-Webpart ausgeliefert. | [Registerkarten in SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | Das Feature "Aufgabenmodul" wurde veröffentlicht. Mithilfe eines Aufgabenmoduls können Sie modale Popup-Erlebnisse in Ihrer Teams-Anwendung von Bots und Registerkarten erstellen. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, `<iframe>`ein-basiertes Widget wie ein YouTube-oder Microsoft Stream-Video anzeigen oder eine [Adaptive Karte](https://docs.microsoft.com/adaptive-cards/)anzeigen. | [Aufgabenmodul Übersicht](~/concepts/task-modules/task-modules-overview.md), [Aufgabenmodul in Registerkarten](~/concepts/task-modules/task-modules-tabs.md), [Aufgabenmodul in Bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | Formatierungsinformationen für Karten wurden aktualisiert und auf den Desktop-, IOS-und Android-Clients für Microsoft Teams getestet. | [Karten](~/concepts/cards/cards.md), Karten [Formatierung](~/concepts/cards/cards-format.md) |
| 09/24/2018 | Anrufe und Onlinebesprechungen-APIs für Microsoft Graph wurden für Beta veröffentlicht, und Microsoft Teams-Apps können jetzt mit Benutzern auf vielfältige Weise mit Sprache und Video interagieren. | [Bots für Anrufe und Onlinebesprechungen](~/concepts/calls-and-meetings/registering-calling-bot.md), [Echt Zeit Medienkonzepte](~/concepts/calls-and-meetings/real-time-media-concepts.md), [Registrieren eines aufrufenden bot](~/concepts/calls-and-meetings/registering-calling-bot.md), [Debuggen und lokale Tests](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md), von der [Anwendung gehostete Medien](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md), [Verarbeiten von Benachrichtigungen über eingehende Anrufe](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | Die Seiten der Registerkartenkonfiguration sind nun deutlich höher. | [Registerkarten Design](tabs/design/tabs.md) |
| 08/15/2018 | Adaptive Karten werden jetzt in Microsoft Teams unterstützt.|[Adaptive Karten Aktionen in Microsoft Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | Die Client Unterstützung für devtools wurde für die Entwicklervorschau dokumentiert.| [DevTools für den Microsoft Teams-Desktop Client](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | Messaging-Erweiterungen unterstützen jetzt mehrere Befehle. Dieses Feature wurde in der Entwicklervorschau und jetzt für alle Benutzer freigegeben.| [composeExtensions. Commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | Die Inline Konfiguration wird nun in Connectors unterstützt. Die Connectors-Dokumentation wurde ebenfalls überarbeitet und zur Verdeutlichung erweitert.| [Connectors](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Ihr Bot kann nun Dateien senden und empfangen.| [Senden und empfangen von Dateien über Ihren bot](~/concepts/bots/bots-files.md)|
| 07/27/2018 | Die Entwicklervorschau unterstützt jetzt mehrere Befehle in Messaging Erweiterungen. | [Messaging Erweiterungen wurden erweitert](~/resources/dev-preview/developer-preview-features.md)|
| 07/23/2018 | Informationen zur APP-erneuten Zertifizierung wurden dem Abschnitt "Veröffentlichung" hinzugefügt. |[Manifest-Berechtigungen](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | In der Entwicklervorschau wurde mehr Speicherplatz der Registerkarten-Konfigurationsseite zugewiesen. | [Die Registerkarten-Konfigurationsseite ist deutlich größer](tabs/design/tabs.md#configuration-page-height)|
| 07/12/2018 | Informationen zum Gastzugriff. | [Gastzugriff in Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Vorab Veröffentlichungsinformationen für den Microsoft Teams-Mandanten-App-Katalog wurden hinzugefügt. | [Veröffentlichen Ihrer Microsoft Teams-App](~/publishing/apps-publish.md)|
| 05/31/2018 | Die Entwicklervorschau für Teams (Ring 3,6) wurde aktualisiert und enthält die Möglichkeit, Bots und Tabs zum Gruppenchat hinzuzufügen. | [Features in der Entwicklervorschau](~/resources/dev-preview/developer-preview-features.md), [Developer Preview-Schema](~/resources/schema/manifest-schema-dev-preview.md)|
| 05/29/2018 | Adaptive Karten werden jetzt in Microsoft Teams in den [Aktionen für Adaptive Karten in Microsoft Teams](task-modules-and-cards/cards/cards-reference.md) unterstützt. |
| 05/29/2018 | Wenn Sie die Vorschau des [Entwicklers](~/resources/dev-preview/developer-preview-intro.md)verwenden, kann Ihr bot nun Dateien senden und empfangen.| [Senden und empfangen von Dateien über Ihren bot](~/concepts/bots/bots-files.md), [Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md)|
| 04/17/2018 | replyToID wurde zur Nutzlast für die `Invoke` -und `MessageBack` Karten Aktionen hinzugefügt. Dies ist besonders nützlich, wenn Sie die Nachricht aktualisieren müssen, aus der die Karten Aktion stammt. | [Karten Aktionen](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Dieses Thema wurde hinzugefügt, um Änderungen an der Microsoft Teams-Programmierschnittstelle und diesen Dokumentations Sätzen nachzuverfolgen. | [Neuigkeiten](~/whats-new.md)|
| 04/10/2018 | Die Authentifizierungs-URLs wurden geändert, um die Mandanten-ID im Pfad konsistent zu verwenden. | [Authentifizierungsablauf für Registerkarten](~/concepts/authentication/auth-flow-tab.md), [Aad-Registerkarten Authentifizierung](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Entwurfsrichtlinien für die Verwendung des Befehlsfelds hinzugefügt. |[Befehlsfeld](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Verwenden von Bots zum Senden von Benachrichtigungen für Ihre APP. |[Nur-Benachrichtigungs-Bots](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Erweiterte Dokumentation für proaktives Messaging. |[Starten einer Unterhaltung](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Umgestaltungs Dokumentation für Karten. |[Karten](~/concepts/cards/cards.md), Karten [Aktionen](~/concepts/cards/cards-actions.md), [Kartenformatierung](~/concepts/cards/cards-format.md), [Karten Referenz](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Dokumentation für Teams App Studio hinzugefügt. |[Schnelles Entwickeln von apps mit Microsoft Teams App Studio](~/get-started/get-started-app-studio.md) [mithilfe der Steuerelementbibliothek in App Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Beispielcode zum Veranschaulichen der AsTeamsChannelAccounts ()-Methode hinzugefügt. |[Kontext für Ihren bot abrufen](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Themen für erste Schritte mit C# hinzugefügt. |[Erste Schritte mit der Microsoft Teams-Plattform mit C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

## <a name="submit-your-questions-bugs-feature-requests-and-contributions"></a>Übermitteln von Fragen, Bugs, Feature-Anfragen und Beiträgen

Wir hören der Entwicklercommunity über [mehrere Kanäle](~/feedback.md)hinweg zu.
