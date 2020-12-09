---
title: Neuerungen
description: Beschreibt alle neuen Entwicklerfeatures in Microsoft Teams
keywords: Teams What es New Latest
ms.openlocfilehash: 29101e45a317268d1eacf00273a98bc30593d5bd
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604466"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Neuerungen für Entwickler in Microsoft Teams

>[!TIP]
> Schauen Sie sich unsere produktionsfähigen Vorlagen im   [**Katalog der Teams-App-Vorlagen**](samples/app-templates.md)an. Der Katalog ist alphabetisch sortiert, und die neuesten Ergänzungen werden mit einem Stern **&#9734;** versehen.

## <a name="change-log"></a>Änderungsprotokoll

Im Änderungsprotokoll werden Änderungen an der Microsoft Teams-Plattform und dieser Dokumentenmappe aufgelistet. Gelegentlich können Einträge verwendet werden, um die Aufmerksamkeit auf ein neues Feature zu lenken, das für Entwickler von Teams einfach interessant ist.

| **Date** | **Hinweise** | **Geänderte Themen** |
| -------- | --------- | ------------------ |
|11/30/2020|Neu: Identitäts Plattformintegration mit Teams Toolkit und Visual Studio Code für Registerkarten|[Authentifizierung mit einmaligem Anmelden mit Microsoft Teams Toolkit und Visual Studio Code für Registerkarten](toolkit/visual-studio-code-tab-sso.md)|
|11/16/2020|Teams-App-Manifest auf Version 1,8 aktualisiert|Referenz: Manifest-Schema für Microsoft Teams|[Referenz: Manifest-Schema für Microsoft Teams](resources/schema/manifest-schema.md)|
|11/11/2020| Manifest-Schema auf Version 1,8 aktualisiert| [Referenz: Manifest-Schema für Microsoft Teams](resources/schema/manifest-schema.md)|
|11/10/2020|Teams-bot-Entwurfsrichtlinien|[Richtlinien für bot-Designs](bots/design/bots.md)|
|9/30/2020|Das Senden und empfangen von Dateien an Bots auf mobilen Geräten wird nun unterstützt.|[Senden und empfangen von Dateien über Ihren bot](resources/bot-v3/bots-files.md)|
|09/22/2020|Leitfaden für neue "erste Schritte mit Teams"|[Erstellen Ihrer ersten Teams-App-Übersicht](build-your-first-app/build-first-app-overview.md)|
|9/18/2020|Unterstützung für in-Meeting Teams-Apps (Veröffentlichungs Vorschau)|[Erstellen von Apps für Microsoft Teams-Besprechungen](apps-in-teams-meetings/create-apps-for-teams-meetings.md) und- [apps in Microsoft Teams-Besprechungen](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|8/19/2020|Importieren von Teams-Nachrichten mit Microsoft Graph|[Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren](graph-api/import-messages/import-external-messages-to-teams.md)
| 08/12/2020 |Adaptive Kartenunterstützung im eingehenden webhook verschoben in GA.|[Senden von adaptiven Karten mithilfe eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|08/10/2020|Erste Schritte beim Erstellen von Microsoft Teams-apps mit dem Visual Studio Toolkit.|[Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code](toolkit/visual-studio-overview.md) |
|08/06/2020|Unterstützung für Registerkarten-SSO-Authentifizierung|[Entwickeln einer SSO-Microsoft Teams-Registerkarte](tabs/how-to/authentication/auth-aad-sso.md#develop-an-sso-microsoft-teams-tab) |
|07/27/2020 | Diagramm proaktive Bots und Nachrichten (öffentliche Vorschau)|[Aktivieren der proaktiven bot-Installation und proaktiver Nachrichten in Microsoft Graph-Teams](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
| 07/22/2020 |Updates für Mobile Gerätefunktionen.|[Anfordern von Geräte Berechtigungen für Ihre Microsoft Teams-Registerkarte](concepts/device-capabilities/native-device-permissions.md) |
|07/20/2020|Teams-App-Validierungs Tool für AppSource-Übermittlungen.|[Teams-App-Validierungs Tool](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)
|07/15/2020|Erstellen eines virtuellen Assistenten für Teams|[Virtueller Assistent für Microsoft Teams](samples/virtual-assistant.md)|
|07/14/2020|Dokumentation einer systemeigenen Lade Indikator Dokumentation|[Anzeigen eines systemeigenen Lade Indikators](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|07/01/2020|Erste Schritte beim Erstellen von Microsoft Teams-apps mit dem Visual Studio Code Toolkit.|[Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code](toolkit/visual-studio-code-overview.md) |
|07/01/2020|Einmaliges Anmelden für Tabs GA für Microsoft Teams-Webclients und-Desktop Clients|[Einzelne Sign-On (SSO)](tabs/how-to/authentication/auth-aad-sso.md)|
|06/05/2020| Manifest-Schema auf Version 1,7 aktualisiert| [Referenz: Manifest-Schema für Microsoft Teams](resources/schema/manifest-schema.md)|
| 05/20/2020 | Ressourcenspezifische Genehmigungsberechtigungen mit Microsoft Graph-APIs befinden sich in der Entwicklervorschau. |[Ressourcenspezifische Zustimmung (RSC) – Entwicklervorschau](graph-api/rsc/resource-specific-consent.md) |
|5/18/2020|Integrieren von Power Virtual Agents in Microsoft Teams|[Integrieren einer Power Virtual Agents Chatbot mit Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|04/01/2020|Integrieren von WFM-Systemen mit Shifts Connector für Teams|[Microsoft Teams verschiebt WFM-Konnektoren](samples/shifts-wfm-connectors.md)
| 03/24/2020 | Unterstützung für das Abrufen eines einzelnen Elements einer Unterhaltung und zusätzlicher Unterstützung für das Abrufen von ausgelagerten Elementen hinzugefügt. | [Teams-Kontext für Ihren Bot erhalten](~/bots/how-to/get-teams-context.md)
| 12/26/2019 | Der `replyToId` Parameter in Nutzlasten, die an einen bot gesendet werden, ist nicht mehr verschlüsselt, sodass Sie diesen Wert verwenden können, um Deeplinks für diese Nachrichten zu erstellen. Nachrichten Nutzlasten enthalten die verschlüsselten Werte im Parameter. `legacy.replyToId`.  |
| 11/5/2019 | Das einmalige Anmelden mit dem Microsoft Teams-JavaScript-SDK in einer Webinhalts Seite befindet sich in der Entwicklervorschau. | [Einmaliges Anmelden](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Unter Haltungs Bots und Messaging-Erweiterungs Dokumentation aktualisiert, um das 4,6 bot Framework SDK widerzuspiegeln. Die Dokumentation für das V3 SDK steht im Abschnitt Resources zur Verfügung. | Alle bot-und Messaging-Erweiterungs Dokumentation. |
| 10/31/2019 | Neue Dokumentationsstruktur und wichtige Artikel Umgestaltung. Melden Sie alle toten Links oder 404s, indem Sie ein GitHub-Problem erstellen. | Alle! |
| 9/13/2019 | Der Anforderungs-bot wird von der Aktions basierten Messaging Erweiterung installiert. | [Initiieren von Aktionen mit Messaging Erweiterungen](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 8/28/2019 | Unterstützung für private Kanäle in Registerkarten und Connectors. | [Kontext für die Registerkarte abrufen](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Geben Sie eine externe Website aus einer externen Website in einen Teams-Kanal frei. | [Freigeben für Teams](~/share-to-teams.md) |
| 05/25/2019 | Antwort mit der bot-Nachricht aus dem Aufgabenmodul. | [Antworten mit bot-Nachrichten aus dem Aufgabenmodul](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots in Gruppenchats. | [Interagieren mit einem bot im Gruppenchat oder-Kanal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | App-Manifest-Lokalisierung. | [App-Lokalisierung](~/publishing/apps-localization.md) |
| 05/20/2019 | Nachrichten Aktionen. | [Nachrichten Aktionen](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Verknüpfung wird entfaltet (benutzerdefinierte URL-Vorschau). | [Entfalten von Links](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Anwendungs Zertifizierungsprogramm für Store-Apps. | [Anwendungszertifizierung](~/publishing/application-certification.md) |
| 05/06/2019 | App-Vorlagen sind jetzt verfügbar. | [App-Vorlagen](~/samples/app-templates.md) |
| 04/23/2019 | Aktionsbasierte Messaging Erweiterungen sind jetzt verfügbar. | [Aktionsbasierte Nachrichten Erweiterungen](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | Das Erstellen von Deep Links zu privatem Chat erfolgt außerhalb der Entwicklervorschau und steht zur Verfügung. | [Deep Linking to a Chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Informationen zur Oberflächen-SKU und zu licencetype im Registerkartenkontext. | [Registerkartenkontext](~/concepts/tabs/tabs-context.md) |
| 12.11.2018 | Registerkarten im Gruppenchat sind jetzt in der veröffentlichten Version von Teams verfügbar und wurden aus der Entwicklervorschau verschoben. Im Rahmen dieser Arbeit wurde der Abschnitt Tabs aus Gründen der Übersichtlichkeit überarbeitet.| [Konfigurierbare Registerkarten](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | Erste Schritte für Node js und .NET/C# wurden für die Verwendung von App Studio in Microsoft Teams aktualisiert, und ein neuer Abschnitt wurde hinzugefügt, um Apps für Node-basierte Teams in Azure zu hosten. | Erste [Schritte mit der Microsoft Teams-Plattform mit C#/.net und App Studio](~/get-started/get-started-dotnet-app-studio.md), erste [Schritte mit der Microsoft Teams-Plattform mit Node js und App Studio](~/get-started/get-started-nodejs-app-studio.md), [Hosten der Node Teams-app in Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Sie können nun tiefe Links zu privaten Chats zwischen Benutzern erstellen. | [Deep Linking to a Chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 08.11.2018 | SharePoint Framework 1,7 hat und mit ihm ein neues Feature zur Verwendung von Microsoft Teams-Registerkarten als SharePoint-Framework-Webpart ausgeliefert. | [Registerkarten in SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | Das Feature "Aufgabenmodul" wurde veröffentlicht. Mithilfe eines Aufgabenmoduls können Sie modale Popup-Erlebnisse in Ihrer Teams-Anwendung von Bots und Registerkarten erstellen. Innerhalb des Popups können Sie Ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, ein `<iframe>` -basiertes Widget wie ein YouTube-oder Microsoft Stream-Video anzeigen oder eine [Adaptive Karte](https://docs.microsoft.com/adaptive-cards/)anzeigen. | [Aufgabenmodul Übersicht](~/concepts/task-modules/task-modules-overview.md), [Aufgabenmodul in Registerkarten](~/concepts/task-modules/task-modules-tabs.md),  [Aufgabenmodul in Bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | Formatierungsinformationen für Karten wurden aktualisiert und auf den Desktop-, IOS-und Android-Clients für Microsoft Teams getestet. | [Karten](~/concepts/cards/cards.md), Karten [Formatierung](~/concepts/cards/cards-format.md) |
| 09/24/2018 | Anrufe und Onlinebesprechungen-APIs für Microsoft Graph wurden für Beta veröffentlicht, und Microsoft Teams-Apps können jetzt mit Benutzern auf vielfältige Weise mit Sprache und Video interagieren. | [Bots für Anrufe und Onlinebesprechungen](~/concepts/calls-and-meetings/registering-calling-bot.md), [Echt Zeit Medienkonzepte](~/concepts/calls-and-meetings/real-time-media-concepts.md), [Registrieren eines aufrufenden bot](~/concepts/calls-and-meetings/registering-calling-bot.md), [Debuggen und lokale Tests](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md), von der [Anwendung gehostete Medien](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md), [Verarbeiten von Benachrichtigungen über eingehende Anrufe](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | Die Seiten der Registerkartenkonfiguration sind nun deutlich höher. | [Registerkarten Design](tabs/design/tabs.md) |
| 08/15/2018 | Adaptive Karten werden jetzt in Microsoft Teams unterstützt.|[Adaptive Karten Aktionen in Microsoft Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | Die Client Unterstützung für devtools wurde für die Entwicklervorschau dokumentiert.| [DevTools für den Microsoft Teams-Desktop Client](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | Messaging-Erweiterungen unterstützen jetzt mehrere Befehle. Dieses Feature wurde in der Entwicklervorschau und jetzt für alle Benutzer freigegeben.| [composeExtensions. Commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | Die Inline Konfiguration wird nun in Connectors unterstützt. Die Connectors-Dokumentation wurde auch zur besseren Übersichtlichkeit überarbeitet und erweitert.| [Connectors](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Ihr Bot kann nun Dateien senden und empfangen.| [Senden und empfangen von Dateien über Ihren bot](~/concepts/bots/bots-files.md)|
| 07/27/2018 | Die Entwicklervorschau unterstützt jetzt mehrere Befehle in Messaging Erweiterungen. | [Messaging Erweiterungen wurden erweitert](~/resources/dev-preview/developer-preview-features.md)|
| 07/23/2018 | Informationen zur APP-erneuten Zertifizierung wurden dem Abschnitt "Veröffentlichung" hinzugefügt. |[Manifest-Berechtigungen](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | In der Entwicklervorschau wurde mehr Speicherplatz der Registerkarten-Konfigurationsseite zugewiesen. | [Die Registerkarten-Konfigurationsseite ist deutlich größer](tabs/design/tabs.md)|
| 07/12/2018 | Informationen zum Gastzugriff. | [Gastzugriff in Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Vorab Veröffentlichungsinformationen für den Microsoft Teams-Mandanten-App-Katalog wurden hinzugefügt. | [Veröffentlichen Ihrer Microsoft Teams-App](~/publishing/apps-publish.md)|
| 05/31/2018 | Die Entwicklervorschau für Teams (Ring 3,6) wurde aktualisiert und enthält die Möglichkeit, Bots und Tabs zum Gruppenchat hinzuzufügen. | [Features in der Entwicklervorschau](~/resources/dev-preview/developer-preview-features.md), [Developer Preview-Schema](~/resources/schema/manifest-schema-dev-preview.md)|
| 05/29/2018 | Adaptive Karten werden jetzt in Microsoft Teams in den [Aktionen für Adaptive Karten in Microsoft Teams](task-modules-and-cards/cards/cards-reference.md)unterstützt. |
| 05/29/2018 | Wenn Sie die Vorschau des [Entwicklers](~/resources/dev-preview/developer-preview-intro.md)verwenden, kann Ihr bot nun Dateien senden und empfangen.| [Senden und empfangen von Dateien über Ihren bot](~/concepts/bots/bots-files.md), [Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md)|
| 04/17/2018 | replyToID wurde zur Nutzlast für die `Invoke` -und Karten Aktionen hinzugefügt `MessageBack` . Dies ist besonders nützlich, wenn Sie die Nachricht aktualisieren müssen, aus der die Karten Aktion stammt. | [Karten Aktionen](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Dieses Thema wurde hinzugefügt, um Änderungen an der Microsoft Teams-Programmierschnittstelle und diesen Dokumentations Sätzen nachzuverfolgen. | [Neuigkeiten](~/whats-new.md)|
| 04/10/2018 | Die Authentifizierungs-URLs wurden geändert, um die Mandanten-ID im Pfad konsistent zu verwenden. | [Authentifizierungsablauf für Registerkarten](~/concepts/authentication/auth-flow-tab.md), [Aad-Registerkarten Authentifizierung](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Entwurfsrichtlinien für die Verwendung des Befehlsfelds hinzugefügt. |[Befehlsfeld](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Verwenden von Bots zum Senden von Benachrichtigungen für Ihre APP. |[Reine Benachrichtigungsbots](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Erweiterte Dokumentation für proaktives Messaging. |[Beginn einer Unterhaltung](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Umgestaltungs Dokumentation für Karten. |[Karten](~/concepts/cards/cards.md), Karten [Aktionen](~/concepts/cards/cards-actions.md), [Kartenformatierung](~/concepts/cards/cards-format.md), [Karten Referenz](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Dokumentation für Teams App Studio hinzugefügt. |[Schnelles Entwickeln von apps mit Microsoft Teams App Studio](~/get-started/get-started-app-studio.md) [mithilfe der Steuerelementbibliothek in App Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Beispielcode zum Veranschaulichen der AsTeamsChannelAccounts ()-Methode hinzugefügt. |[Kontext für Ihren bot abrufen](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Themen für erste Schritte mit C# hinzugefügt. |[Erste Schritte mit der Microsoft Teams-Plattform mit C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

## <a name="submit-your-questions-bugs-feature-requests-and-contributions"></a>Übermitteln von Fragen, Bugs, Feature-Anfragen und Beiträgen

Wir hören der Entwicklercommunity über [mehrere Kanäle](feedback.md)hinweg zu.
