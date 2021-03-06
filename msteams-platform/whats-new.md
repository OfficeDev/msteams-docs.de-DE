---
title: Neuerungen
description: Beschreibt alle neuen Entwicklerfeatures in Microsoft Teams
ms.topic: reference
keywords: Teams, was neu ist
ms.openlocfilehash: 62504b076fb8e4b0523a4a223301c9f031f03e7c
ms.sourcegitcommit: 9cfbc44912980a33d2d7c7c85739aeea6ccb41de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "50479854"
---
# <a name="whats-new-for-developers-in-microsoft-teams"></a>Neues für Entwickler in Microsoft Teams

>[!TIP]
> Sehen Sie sich unsere produktionsbereiten Vorlagen im [**Katalog der Teams-App-Vorlagen an.**](samples/app-templates.md) Der Katalog ist alphabetisch, und die neuesten Ergänzungen sind mit einem Stern **gekennzeichnet,**&#9734;.

## <a name="change-log"></a>Änderungsprotokoll

Im Änderungsprotokoll werden Änderungen an der Microsoft Teams-Plattform und diesem Dokumentsatz aufgeführt. Manchmal können Einträge verwendet werden, um auf ein neues Feature aufmerksam zu machen, das für Teams-Entwickler einfach von Interesse ist.

| **Date** | **Notizen** | **Geänderte Themen** |
| -------- | --------- | ------------------ |
|03/05/2021|Hinweis: Registerkarten haben keine Ränder mehr um ihre Erfahrungen. Registerkartenentwickler sollten ihre Apps überprüfen und aktualisieren. | [Entfernen von Registerkartenrändern](resources/removing-tab-margins.md) |
|03/05/2021 | Der Standardinstallationsbereich und die Gruppenfunktion werden in der Entwicklervorschau angezeigt.| [Standardinstallationsbereich und Gruppenfunktion](concepts/deploy-and-publish/apps-upload.md#add-a-default-install-scope-and-group-capability) |
|03/05/2021|Neu anordnen von registerkarten für persönliche Apps|[Neu anordnen der Registerkarte Chat in persönlichen Apps](tabs/how-to/create-tab-pages/content-page.md#reorder-static-personal-tabs)|
|03/04/2021|Informationsmasken in adaptiven Karten finden Sie in der Entwicklervorschau.| [Informationsmasken in adaptiven Karten](task-modules-and-cards/cards/cards-format.md#information-masking-in-adaptive-cards) |
|02/19/2021|Neu: Standortfunktionen hinzugefügt. <br/> Update: Informationen zu Standortfunktionen werden in der Übersicht über die Gerätefunktionen, systemeigene Geräteberechtigungen, Integrieren von Medienfunktionen und QR- oder Barcodescannerfunktionen hinzugefügt.|[Übersicht,](concepts/device-capabilities/device-capabilities-overview.md) [Geräteberechtigungen anfordern,](concepts/device-capabilities/native-device-permissions.md) [Medienfunktionen integrieren,](concepts/device-capabilities/mobile-camera-image-permissions.md) [QR- oder Strichcodescannerfunktion](concepts/device-capabilities/qr-barcode-scanner-capability.md)integrieren, [Standortfunktionen integrieren](concepts/device-capabilities/location-capability.md) |
|02/18/2021|Neu: Qr- oder Strichcodescannerfunktion hinzugefügt. <br/> Update: Informationen zu QR- oder Strichcodescannerfunktionen werden in der Übersicht über geräteeigene Gerätefunktionen, systemeigene Geräteberechtigungen und Integrieren von Medienfunktionen hinzugefügt.|[Übersicht](concepts/device-capabilities/device-capabilities-overview.md), [Geräteberechtigungen anfordern,](concepts/device-capabilities/native-device-permissions.md) [Medienfunktionen integrieren,](concepts/device-capabilities/mobile-camera-image-permissions.md) [QR- oder Strichcodescannerfunktion integrieren](concepts/device-capabilities/qr-barcode-scanner-capability.md) |
|02/09/2021|Neu: Übersicht über die Gerätefunktionen hinzugefügt. <br/> Update: Informationen zur Mikrofonfunktion werden in den systemeigenen Geräteberechtigungen hinzugefügt und integrieren Medienfunktionendateien.|[Übersicht](concepts/device-capabilities/device-capabilities-overview.md), [Geräteberechtigungen anfordern](concepts/device-capabilities/native-device-permissions.md), [Medienfunktionen integrieren](concepts/device-capabilities/mobile-camera-image-permissions.md)|
|11/30/2020|Neu: Integration der Identitätsplattform in Teams Toolkit und Visual Studio Code für Registerkarten|[Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten](toolkit/visual-studio-code-tab-sso.md)|
|11/16/2020|Auf Version 1.8 aktualisiertes Teams-App-Manifest|[Referenz: Manifestschema für Microsoft Teams](resources/schema/manifest-schema.md)|
|11/10/2020|Richtlinien zum Entwerfen von Teams-Bots|[Richtlinien für das Botdesign](bots/design/bots.md)|
|9/30/2020|Das Senden und Empfangen von Dateien an Bots auf mobilen Geräten wird jetzt unterstützt.|[Senden und Empfangen von Dateien über Ihren Bot](resources/bot-v3/bots-files.md)|
|09/22/2020|Neue Anleitung "Erste Schritte mit Teams"|[Erstellen Der ersten Teams-App -Übersicht](build-your-first-app/build-first-app-overview.md)|
|9/18/2020|Unterstützung für Teams-Apps in Besprechungen (Release Preview)|[Erstellen von Apps für Teams-Besprechungen](apps-in-teams-meetings/create-apps-for-teams-meetings.md) [und Apps in Teams-Besprechungen](apps-in-teams-meetings/teams-apps-in-meetings.md)|
|8/19/2020|Importieren von Teams-Nachrichten mit Microsoft Graph|[Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren](graph-api/import-messages/import-external-messages-to-teams.md)
| 08/12/2020 |Unterstützung für adaptive Karten im eingehenden Webhook, der zu GA verschoben wurde.|[Senden von adaptiven Karten mithilfe eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook) |
|08/10/2020|Erste Schritte beim Erstellen von Teams-Apps mit dem Visual Studio Toolkit.|[Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](toolkit/visual-studio-overview.md) |
|08/06/2020|Unterstützung der Tabs-SSO-Authentifizierung|[Entwickeln einer Microsoft Teams-Registerkarte für SSO](tabs/how-to/authentication/auth-aad-sso.md#develop-an-sso-microsoft-teams-tab) |
|07/27/2020 | Graph proactive bots and messages (Public Preview)|[Aktivieren einer proaktiven Botinstallation und proaktivem Messaging in Teams mit Microsoft Graph](graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)|
| 07/22/2020 |Updates für mobile Gerätefunktionen.|[Anfordern von Geräteberechtigungen für Ihre Microsoft Teams-Registerkarte](concepts/device-capabilities/native-device-permissions.md) |
|07/20/2020|Teams App Validation Tool für AppSource-Übermittlungen.|[Teams App Validation Tool](concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)
|07/15/2020|Erstellen eines virtuellen Assistenten für Teams|[Virtueller Assistent für Microsoft Teams](samples/virtual-assistant.md)|
|07/14/2020|Erstellen einer Dokumentation zu systemeigenen Ladeanzeigen|[Anzeigen eines systemeigenen Ladeindikators](tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)
|07/01/2020|Erste Schritte beim Erstellen von Teams-Apps mit Visual Studio Code Toolkit.|[Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code](toolkit/visual-studio-code-overview.md) |
|07/01/2020|Einmaliges Anmelden für Registerkarten GA für Teams Web- und Desktopclients|[Single Sign-On (SSO)](tabs/how-to/authentication/auth-aad-sso.md)|
|06/05/2020| Manifestschema auf Version 1.7 aktualisiert| [Referenz: Manifestschema für Microsoft Teams](resources/schema/manifest-schema.md)|
| 05/20/2020 | Ressourcenspezifische Zustimmungsberechtigungen mithilfe von Microsoft Graph-APIs werden in der Entwicklervorschau angezeigt. |[Ressourcenspezifische Zustimmung (RSC) – Developer Preview](graph-api/rsc/resource-specific-consent.md) |
|5/18/2020|Integrieren von virtuellen Power Agents in Teams|[Integrieren eines Power Virtual Agents-Chatbots in Microsoft Teams](bots/how-to/add-power-virtual-agents-bot-to-teams.md)|
|04/01/2020|Integrieren von WFM-Systemen in den Schichtconnector für Teams|[Microsoft Teams verschiebt WFM-Connectors](samples/shifts-wfm-connectors.md)
| 03/24/2020 | Unterstützung für das Abrufen eines einzelnen Mitglieds einer Unterhaltung und zusätzliche Unterstützung für das Abrufen von seitenseitigen Mitgliedern hinzugefügt. | [Teams-Kontext für Ihren Bot erhalten](~/bots/how-to/get-teams-context.md)
| 12/26/2019 | Der Parameter in Nutzlasten, die an einen Bot gesendet werden, ist nicht mehr verschlüsselt, sodass Sie diesen Wert verwenden können, um `replyToId` Deeplinks zu diesen Nachrichten zu erstellen. Nachrichtennutzlasten enthalten die verschlüsselten Werte im Parameter. `legacy.replyToId`.  |
| 11/5/2019 | Einmaliges Anmelden mit dem Teams JavaScript SDK auf einer Webinhaltsseite befindet sich in der Entwicklervorschau. | [Einmaliges Anmelden](tabs/how-to/authentication/auth-aad-sso.md) |
| 10/31/2019 | Dokumentation zu Unterhaltungsbots und Messagingerweiterungen, die aktualisiert wurden, um das 4.6 Bot Framework SDK zu widerspiegeln. Die Dokumentation für das v3 SDK finden Sie im Abschnitt Ressourcen. | Alle Bot- und Messagingerweiterungsdokumentation. |
| 10/31/2019 | Neue Dokumentationsstruktur und Hauptartikel-Umgestaltung. Melden Sie alle nicht verwendeten Links oder 404-Links, indem Sie ein GitHub-Problem erstellen. | Alle! |
| 9/13/2019 | Der Anforderungsbot wird über die aktionsbasierte Messagingerweiterung installiert. | [Initiieren von Aktionen mit Messagingerweiterungen](resources/messaging-extension-v3/create-extensions.md#request-to-install-your-conversational-bot)
| 8/28/2019 | Unterstützung für private Kanäle in Registerkarten und Connectors. | [Kontext für Ihre Registerkarte erhalten](tabs/how-to/access-teams-context.md#retrieving-context-in-private-channels) |
| 06/20/2019 | Freigeben einer externen Website von einer externen Website in einem Teams-Kanal. | [Freigeben für Teams](~/share-to-teams.md) |
| 05/25/2019 | Reagieren Sie mit Botnachricht aus dem Aufgabenmodul. | [Reagieren mit Botnachricht aus dem Aufgabenmodul](resources/messaging-extension-v3/create-extensions.md#respond-with-an-adaptive-card-message-sent-from-a-bot) |
| 05/25/2019 | Bots in Gruppenchats. | [Interagieren mit einem Bot im Gruppenchat oder -kanal](~/concepts/bots/bot-conversations/bots-conv-channel.md) |
| 05/20/2019 | Lokalisierung des App-Manifests. | [App-Lokalisierung](~/publishing/apps-localization.md) |
| 05/20/2019 | Nachrichtenaktionen. | [Nachrichtenaktionen](resources/messaging-extension-v3/create-extensions.md#action-type-message-extensions) |
| 05/20/2019 | Verknüpfungsentfurling (benutzerdefinierte URL-Vorschau). | [Entfalten von Links](messaging-extensions/how-to/link-unfurling.md)|
| 05/06/2019 | Anwendungszertifizierungsprogramm für Store-Apps. | [Anwendungszertifizierung](~/publishing/application-certification.md) |
| 05/06/2019 | App-Vorlagen sind jetzt verfügbar. | [App-Vorlagen](~/samples/app-templates.md) |
| 04/23/2019 | Aktionsbasierte Messagingerweiterungen sind jetzt verfügbar. | [Aktionsbasierte Nachrichtenerweiterungen](~/concepts/messaging-extensions/create-extensions.md) |
| 02/18/2019 | Das Erstellen von tiefen Links zu privaten Chats ist nicht in der Entwicklervorschau verfügbar. | [Tiefe Verknüpfung mit einem Chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 01/23/2019 | Anzeigen von SKU- und licenceType-Informationen im Registerkartenkontext. | [Registerkartenkontext](~/concepts/tabs/tabs-context.md) |
| 12.11.2018 | Registerkarten im Gruppenchat sind jetzt in der veröffentlichten Version von Teams verfügbar und wurden aus der Entwicklervorschau verschoben. Im Rahmen dieser Arbeit wurde der Abschnitt Registerkarten aus Gründen der Übersichtlichkeit überarbeitet.| [Konfigurierbare Registerkarten](~/concepts/tabs/tabs-configurable.md) |
| 11/11/2018 | Erste Schritte für Knoten JS und für .NET/C# wurde aktualisiert, um App Studio in Teams zu verwenden, und ein neuer Abschnitt wurde zum Hosten knotenbasierter Teams-Apps in Azure hinzugefügt. | Erste Schritte auf der [Microsoft Teams-Plattform mit C#/.NET und App Studio](~/get-started/get-started-dotnet-app-studio.md), Erste Schritte auf der Microsoft Teams-Plattform mit Node [JS und App Studio](~/get-started/get-started-nodejs-app-studio.md), [Hosten Ihrer Node Teams-App in Azure](~/get-started/get-started-nodejs-in-azure.md)|
| 11/09/2018 | Sie können jetzt tiefe Links zu privaten Chats zwischen Benutzern erstellen. | [Tiefe Verknüpfung mit einem Chat](concepts/build-and-test/deep-links.md#deep-linking-to-a-chat) |
| 08.11.2018 | SharePoint Framework 1.7 wurde ausgeliefert und damit ein neues Feature zur Verwendung der Registerkarte Microsoft Teams als SharePoint Framework-Web part. | [Registerkarten in SharePoint](~/concepts/tabs/tabs-in-sharepoint.md) |
| 11/05/2018 | Das Feature "Aufgabenmodul" wurde veröffentlicht. Mit einem Aufgabenmodul können Sie modale Popuperfahrungen in Ihrer Teams-Anwendung sowohl auf Bots als auch auf Registerkarten erstellen. Innerhalb des Popups können Sie ihren eigenen benutzerdefinierten HTML/JavaScript-Code ausführen, ein -basiertes Widget wie ein YouTube- oder Microsoft Stream-Video anzeigen oder eine `<iframe>` [adaptive Karte anzeigen.](https://docs.microsoft.com/adaptive-cards/) | [Aufgabenmodul Übersicht](~/concepts/task-modules/task-modules-overview.md), [Aufgabenmodul in Registerkarten](~/concepts/task-modules/task-modules-tabs.md),  [Aufgabenmodul in Bots](~/concepts/task-modules/task-modules-bots.md) |
| 10/05/2018 | Formatierungsinformationen für Karten wurden aktualisiert und auf desktop-, iOS- und Android-Clients für Teams getestet. | [Karten](~/concepts/cards/cards.md), [Kartenformatierung](~/concepts/cards/cards-format.md) |
| 09/24/2018 | Die APIs für Anrufe und Onlinebesprechungen für Microsoft Graph wurden in der Betaversion veröffentlicht, und Teams-Apps können nun mithilfe von Sprach- und Videonachrichten auf vielfältige Weise mit Benutzern interagieren. | [Bots für](~/concepts/calls-and-meetings/registering-calling-bot.md)Anrufe und Onlinebesprechungen, [Medienkonzepte](~/concepts/calls-and-meetings/real-time-media-concepts.md)in [Echtzeit,](~/concepts/calls-and-meetings/registering-calling-bot.md)Registrieren eines Anrufbots, [Debuggen](~/concepts/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)und lokale Tests, von Anwendungen gehostete [Medien,](~/concepts/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)Behandeln eingehender [Anrufbenachrichtigungen](~/concepts/calls-and-meetings/call-notifications.md) |
| 09/11/2018 | Registerkartenkonfigurationsseiten sind jetzt deutlich höher. | [Tabdesign](tabs/design/tabs.md) |
| 08/15/2018 | Adaptive Karten werden jetzt in Teams unterstützt.|[Adaptive Kartenaktionen in Teams](task-modules-and-cards/cards/cards-reference.md#adaptive-card) |
| 08/10/2018 | Die Clientunterstützung für DevTools wurde für die Developer Preview.| [DevTools für den Microsoft Teams-Desktopclient](~/resources/dev-preview/developer-preview-tools.md)|
| 08/08/2018 | Messagingerweiterungen unterstützen jetzt mehrere Befehle. Dieses Feature wurde in Developer Preview und ist jetzt für alle Benutzer freigegeben.| [composeExtensions.commands](~/resources/schema/manifest-schema.md#composeextensionscommands)|
| 08/07/2018 | Die Inlinekonfiguration wird jetzt in Connectors unterstützt. Die Connectors-Dokumentation wurde ebenfalls überarbeitet und aus Gründen der Übersichtlichkeit erweitert.| [Connectors](~/concepts/connectors/connectors.md)|
| 08/06/2018 | Ihr Bot kann jetzt Dateien senden und empfangen.| [Senden und Empfangen von Dateien über Ihren Bot](~/concepts/bots/bots-files.md)|
| 07/27/2018 | Die Entwicklervorschau unterstützt jetzt mehrere Befehle in Messagingerweiterungen. | [Messagingerweiterungen wurden erweitert](~/resources/dev-preview/developer-preview-features.md)|
| 07/23/2018 | Informationen zur Erneuten Zertifizierung von Apps wurden dem Abschnitt Veröffentlichung hinzugefügt. |[Manifestberechtigungen](resources/schema/manifest-schema.md#permissions)|
| 07/16/2018 | In der Entwicklervorschau wurde der Registerkartenkonfigurationsseite mehr Speicherplatz zugewiesen. | [Die Registerkartenkonfigurationsseite ist deutlich höher](tabs/design/tabs.md)|
| 07/12/2018 | Informationen zum Gastzugriff. | [Gastzugriff in Microsoft Teams](https://docs.microsoft.com/microsoftteams/guest-access#guest-access-overview)|
| 06/07/2018 | Vorabversionsinformationen für den Microsoft Teams-Mandanten-App-Katalog wurden hinzugefügt. | [Veröffentlichen Ihrer Microsoft Teams-App](~/publishing/apps-publish.md)|
| 05/31/2018 | Die Teams-Entwicklervorschau (Ring 3.6) wurde aktualisiert, um bots und registerkarten zum Gruppenchat hinzuzufügen. | [Features in der Entwicklervorschau](~/resources/dev-preview/developer-preview-features.md), [Entwicklervorschauschema](~/resources/schema/manifest-schema-dev-preview.md)|
| 05/29/2018 | Adaptive Karten werden jetzt in Teams in den [Aktionen für adaptive Karten in Teams unterstützt.](task-modules-and-cards/cards/cards-reference.md) |
| 05/29/2018 | Wenn Sie die Entwicklervorschau [verwenden,](~/resources/dev-preview/developer-preview-intro.md)kann Ihr Bot jetzt Dateien senden und empfangen.| [Senden und Empfangen von Dateien über Ihren Bot](~/concepts/bots/bots-files.md), Features im [öffentlichen Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md)|
| 04/17/2018 | replyToID wurde der Nutzlast für die `Invoke` `MessageBack` Und-Kartenaktionen hinzugefügt. Dies ist besonders hilfreich, wenn Sie die Nachricht aktualisieren müssen, aus der die Kartenaktion stammt. | [Kartenaktionen](~/concepts/cards/cards-actions.md)|
| 04/12/2018 | Dieses Thema wurde hinzugefügt, um Änderungen an der Programmierschnittstelle von Teams und diesem Dokumentationssatz nachverfolgt zu haben. | [Neuerungen](~/whats-new.md)|
| 04/10/2018 | Die Authentifizierungs-URLs wurden geändert, um die Mandanten-ID im Pfad konsistent zu verwenden. | [Authentifizierungsfluss für Registerkarten](~/concepts/authentication/auth-flow-tab.md), [AAD-Registerkartenauthentifizierung](~/concepts/authentication/auth-tab-AAD.md)|
| 04/06/2018 | Entwurfsrichtlinien für die Verwendung des Befehlsfelds hinzugefügt. |[Befehlsfeld](~/resources/design/framework/command-box.md)|
| 04/02/2018 | Verwenden von Bots zum Senden von Benachrichtigungen für Ihre App. |[Reine Benachrichtigungsbots](~/concepts/bots/bots-notification-only.md)|
| 03/27/2018 | Erweiterte Dokumentation für proaktives Messaging. |[Beginn einer Unterhaltung](./concepts/bots/bot-conversations/bots-conv-proactive.md)|
| 03/15/2018 | Umgestaltet dokumentation für Karten. |[Karten](~/concepts/cards/cards.md), [Kartenaktionen](~/concepts/cards/cards-actions.md), [Kartenformatierung](~/concepts/cards/cards-format.md), [Kartenreferenz](~/concepts/cards/cards-reference.md)|
| 03/03/2018 | Dokumentation für Teams App Studio hinzugefügt. |[Schnelles Entwickeln von Apps mit Teams App Studio](~/get-started/get-started-app-studio.md), Verwenden der [Steuerelementbibliothek in App Studio](~/get-started/app-studio-component-library.md)|
| 02/27/2018 | Beispielcode zum Veranschaulichen der AsTeamsChannelAccounts()-Methode hinzugefügt. |[Kontext für Ihren Bot erhalten](~/concepts/bots/bots-context.md)|
| 02/05/2018 | Themen zum Einstieg in die Verwendung von C#. |[Erste Schritte mit der Microsoft Teams-Plattform mit C#/.NET](./get-started/get-started-dotnet-app-studio.md)|

## <a name="submit-your-questions-bugs-feature-requests-and-contributions"></a>Übermitteln Von Fragen, Fehlern, Featureanforderungen und Beiträgen

Wir lauschen der Entwickler-Community über [mehrere Kanäle](feedback.md).
