---
author: heath-hamilton
description: Bewährte Methoden für die Integration vorhandener Web-Apps in Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
localization_priority: Normal
ms.topic: conceptual
title: Web-Apps
ms.openlocfilehash: b7f530198a8e1c240e3cf4b227d786af94f6c89e
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630432"
---
# <a name="web-apps"></a>Web-Apps 

Sie können Web-Apps mit den features Teams sozialen und zusammenarbeiten von Apps geeignet machen, indem Sie sie ordnungsgemäß in die Teams.
  
Die verschiedenen Arten von Apps, die Sie in Teams integrieren können, sind wie folgt:
* **Eigenständige Apps:** Eine eigenständige App ist eine einzelne oder große und komplexe App. Der Benutzer kann einige Aspekte davon in der Teams.
* **Apps für die** Zusammenarbeit: Eine App, die bereits für die features für soziale netzwerke und zusammenarbeiten inhärent für Teams.
* **SharePoint**: Eine SharePoint, die sie in einem Teams.

Sie können die für Ihr Integrationsszenario geltenden Richtlinien zuordnungen und befolgen.
Dieses Dokument bietet eine Übersicht über Teams Funktionen, Freigabepunktanforderungen für Datei- und Datenspeicherung, API-Anforderungen, Authentifizierung und die tiefe Verknüpfung Ihrer App mit Teams.
 
## <a name="get-to-know-teams-platform-capabilities"></a>Kennenlernen Teams Plattformfunktionen

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Ihre Teams-App muss erforderliche und erwartete Features für die Zusammenarbeit enthalten. Um mit der App-Integration zu arbeiten, ist es wichtig, sich mit der Teams vertraut zu machen.

|Allgemeine App-Features   |Teams Plattformfunktionen   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder Webview  |[Registerkarten](../tabs/what-are-tabs.md)  |
|Freigeben von Verknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionsverknüpfungen und -erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Kanalbenachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Externe Nachrichtendienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modale  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Bestimmen einer Teilmenge der Funktionalität

***Integrationsszenarien:** Eigenständige Apps*

Die Integration aller Features einer vorhandenen Anwendung in Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzeroberfläche, insbesondere in größeren Apps. Beginnen Sie mit den auswirkungenreichsten Features und den Features, die sich besser in die Teams. Sie können Benutzern das Starten der Haupt-App und den Zugriff auf den vollständigen Satz von Features ermöglichen.

**Voraussetzungen für die Integration Ihrer App in Teams** Nachfolgend finden Sie die Voraussetzungen für die Integration Ihrer App in Teams. 

1. [Ordnen Sie die Anwendungsfälle Ihrer App Teams Plattformfunktionen zu.](../concepts/design/map-use-cases.md)
1. [Bestimmen Sie die Einstiegspunkte Ihrer App.](../concepts/extensibility-points.md) Ist dies für den persönlichen Gebrauch, die Zusammenarbeit oder beides?

## <a name="understand-sharepoint-requirements-and-options"></a>Verstehen SharePoint Anforderungen und Optionen

***Integrationsszenarien**: SharePoint*

Um eine vorhandene SharePoint [als](/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) Registerkarte Teams zu integrieren, müssen Sie Folgendes berücksichtigen:

* Es muss eine moderne *SharePoint* sein.
* Es werden nur persönliche Registerkarten unterstützt. Sie können Ihre Seite nicht als Kanalregisterkarte integrieren.

Alternativ können Sie mithilfe der Teams eine [Registerkarte SharePoint-Framework.](/sharepoint/dev/spfx/integrate-with-teams-introduction)

## <a name="aim-towards-multi-tenancy"></a>Ziel von Mehr-Mandanz

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Wenn Ihre App von mehreren Organisationen verwendet wird, sollten Sie das Mehr-Mandanten-Hosting in Betracht ziehen, das Ihr Produkt skalierbar macht und die Verteilung erheblich vereinfacht.

## <a name="review-your-apis"></a>Überprüfen Ihrer APIs

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit*

Sie müssen sicherstellen, dass die vorhandenen APIs und Datenstrukturen Ihrer App die App bei der Integration in Teams. Um die Unterstützung zu erweitern, müssen Sie die APIs und Datenstrukturen um kontextbezogene Informationen zu Teams für die [Identitätszuordnung,](../concepts/authentication/configure-identity-provider.md)die Unterstützung von [DeepLinks](../concepts/build-and-test/deep-links.md)und die Integration von Microsoft [Graph](/graph/teams-concept-overview).

Erfahren Sie mehr über das Abrufen des Kontexts für Teams [Oder](../tabs/how-to/access-teams-context.md) [Bot](../bots/how-to/get-teams-context.md).

## <a name="understand-authentication-options"></a>Verstehen von Authentifizierungsoptionen

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Azure Active Directory (AD) ist der Identitätsanbieter für Teams. Wenn Ihre App einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitätszuordnungsübung oder azure AD kombinieren.

Teams verfügt über Mechanismen für einmaliges Anmelden (Single Sign-On, SSO) mit Azure AD für Drittanbieter-Apps. Darüber hinaus enthält sie Anleitungen für Authentifizierungsflüsse zu anderen Identitätsanbietern mithilfe von Standards wie OAuth und Open ID Verbinden, bekannt als OIDC.

Für SharePoint Seiten können Sie nur SSO verwenden und keine weitere Azure AD-ID hinzufügen, wenn SSO für eine andere App verwendet werden soll, da die ID die SharePoint ist.

Erfahren Sie mehr über [die Authentifizierung in Teams.](../concepts/authentication/authentication.md)

## <a name="follow-teams-design-guidelines"></a>Befolgen Teams Entwurfsrichtlinien

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit*

Befolgen Sie die [Teams,](../concepts/design/understand-use-cases.md) damit Ihre App für die Anwendung nativ Teams. Sie können einen vorhandenen App-Inhalt nicht auf eine registerkarte Teams migrieren. Weitere Informationen zum App-Design finden Sie unter [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximieren der tiefen Verknüpfung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Sie können Links zu Informationen und Features innerhalb von Teams. Verwenden [Sie tiefe Links,](../concepts/build-and-test/deep-links.md) um Ihre App mit Teams zu verknüpfen, wenn sie mehrere Teile einer App verbinden, um eine nativere Teams zu ermöglichen.

## <a name="be-smart-when-messaging-users"></a>Smart sein, wenn Messagingbenutzer

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Verwenden Sie einen [Bot](../bots/what-are-bots.md) in Teams App für Unterhaltungen mit mehreren Threads, da er mehr Flexibilität bietet als ein [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Mit Bots können Sie auch proaktive Nachrichten **an** einzelne Benutzer oder Kanäle senden. Bei den proaktiven Nachrichten handelt es sich um nicht gesendete Nachrichten, die durch ein externes Ereignis ausgelöst werden, und nicht um eine Nachricht, die an einen Bot gesendet wird. Beispielsweise sendet Ihr Bot eine Willkommensnachricht, wenn er installiert ist oder ein neuer Benutzer einem Kanal beitritt. 

Das Senden proaktiver Nachrichten erfordert Teams-spezifischen Bezeichner. Sie können die Informationen erfassen, indem [Sie](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile)Dienstplan- oder Benutzerprofildaten [abrufen,](../bots/how-to/conversations/subscribe-to-conversation-events.md)Unterhaltungsereignisse abonnieren oder [Microsoft Graph.](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams)

Spamen Sie Benutzer nicht mit übermäßigen Nachrichten. Wenn die Teams unterstützt, können die Benutzer Benachrichtigungseinstellungen für Ihre App konfigurieren.   
Es folgt ein Beispiel für eine Benachrichtigung: Senden Sie mir keine **nicht gesendeten Nachrichten.**

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden SharePoint für Datei- und Datenspeicherung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint Seiten*

Wenn ein Team erstellt wird, wird [SharePoint websitesammlung](/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um Datei- und Datenspeicherung für dieses Team zu unterstützen. Ihre App muss dieses Feature nutzen, wenn sie mit Dateien interagiert. Verwenden Sie die Websitesammlung zum Speichern von Rohdaten in SharePoint Listen und Excel.

## <a name="see-also"></a>Sehen Sie ebenfalls

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
