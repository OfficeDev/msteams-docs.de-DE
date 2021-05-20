---
author: heath-hamilton
description: Bewährte Methoden für die Integration vorhandener Web-Apps in Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
localization_priority: Normal
ms.topic: conceptual
title: Web-Apps
ms.openlocfilehash: 6783a05079f876cf3c2475a0ad5ca0e1f6687fc4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566222"
---
# <a name="web-apps"></a>Web-Apps 

Sie können Web-Apps mit den sozialen und kollaborativen Funktionen von Teams für geeignet machen, indem Sie sie ordnungsgemäß in Teams integrieren.
  
Die verschiedenen Arten von Apps, die Sie in Teams integrieren können, sind wie folgt:
* **Eigenständige Apps:** Eine eigenständige App ist eine einseitige oder große und komplexe App. Der Benutzer kann einige Aspekte davon in Teams verwenden.
* **Collaboration-Apps**: Eine App, die bereits für die sozialen und kollaborativen Funktionen entwickelt wurde, die Teams innewohnen.
* **SharePoint**: Eine SharePoint Seite, die sie in Teams anzeigen möchten.

Sie können die entsprechende Richtlinie für Ihr Integrationsszenario zuordnen und befolgen.
Dieses Dokument gibt einen Überblick über Teams Funktionen, Anforderungen an Freigabepunkte für Datei- und Datenspeicherung, API-Anforderungen, Authentifizierung und Deep-Linking Ihrer App mit Teams.
 
## <a name="get-to-know-teams-platform-capabilities"></a>Lernen Sie Teams Plattformfunktionen kennen

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps, SharePoint*

Ihre Teams-App muss erforderliche und erwartete kollaborative Funktionen enthalten. Um mit der App-Integration zu arbeiten, ist es wichtig, sich mit Teams Entwicklungsterminologie vertraut zu machen.

|Gemeinsame App-Funktionen   |Teams Plattformfunktionen   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder Webview  |[Registerkarten](../tabs/what-are-tabs.md)  |
|Freigeben von Verknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionsverknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Kanalbenachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Nachricht externe Dienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modals  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Bestimmen einer Teilmenge der Funktionalität

***Integrationsszenarien**: Eigenständige Apps*

Die Integration aller Funktionen einer vorhandenen Anwendung in Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzererfahrung, insbesondere in größeren Apps. Beginnen Sie mit den wirkungsvollsten Funktionen und solchen, die sich natürlicher in Teams integrieren. Sie können Benutzern erlauben, die Haupt-App zu starten und auf den vollständigen Satz von Funktionen zuzugreifen.

**Voraussetzungen für die Integration Ihrer App in Teams** Im Folgenden finden Sie die Voraussetzungen für die Integration Ihrer App in Teams. 

1. Ordnen Sie die [Anwendungsfälle Ihrer App Teams Plattformfunktionen zu.](../concepts/design/map-use-cases.md)
1. [Bestimmen Sie die Einstiegspunkte Ihrer App](../concepts/extensibility-points.md). Ist es für den persönlichen Gebrauch, Zusammenarbeit oder beides?

## <a name="understand-sharepoint-requirements-and-options"></a>Verstehen SharePoint Anforderungen und Optionen

***Integrationsszenarien**: SharePoint*

Um eine vorhandene [SharePoint Seite](/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) als Teams Registerkarte zu integrieren, müssen Sie Folgendes berücksichtigen:

* Es muss eine *moderne* SharePoint Online-Seite sein.
* Es werden nur persönliche Registerkarten unterstützt. Sie können Ihre Seite nicht als Kanal-Registerkarte integrieren.

Alternativ können Sie eine Teams Registerkarte [mit dem SharePoint-Framework](/sharepoint/dev/spfx/integrate-with-teams-introduction)erstellen.

## <a name="aim-towards-multi-tenancy"></a>Ziel für Multi-Tenancy

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps, SharePoint*

Wenn Ihre App von mehreren Organisationen verwendet wird, sollten Sie ein mehrinstanzenfähiges Hosting in Betracht ziehen, das Ihr Produkt skalierbar macht und die Verteilung erheblich vereinfacht.

## <a name="review-your-apis"></a>Überprüfen Sie Ihre APIs

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps*

Sie müssen die vorhandenen APIs und Datenstrukturen Ihrer App bei der Integration in Teams unterstützen. Um die Unterstützung zu erweitern, müssen Sie die APIs und Datenstrukturen um kontextbezogene Informationen über Teams für [Identitätszuordnung,](../concepts/authentication/configure-identity-provider.md) [Deeplink-Unterstützung](../concepts/build-and-test/deep-links.md)und [DieIntegration von Microsoft Graph](/graph/teams-concept-overview)erweitern.

Erfahren Sie mehr über das Abrufen von Kontext für Ihre Teams [Registerkarte](../tabs/how-to/access-teams-context.md) oder [Bot](../bots/how-to/get-teams-context.md).

## <a name="understand-authentication-options"></a>Verstehen von Authentifizierungsoptionen

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps, SharePoint*

Azure Active Directory (AD) ist der Identitätsanbieter für Teams. Wenn Ihre App einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitätszuordnungsübung durchführen oder mit Azure AD kombinieren.

Teams verfügt über Single Sign-On(SSO)-Mechanismen mit Azure AD für Drittanbieter-Apps. Es bietet auch die Anleitung für Authentifizierungsflüsse an andere Identitätsanbieter, die Standards wie OAuth und Open ID Verbinden verwenden, die als OIDC bezeichnet werden.

Für SharePoint Seiten können Sie SSO nur verwenden und keine weitere Azure AD-ID hinzufügen, wenn SSO für eine andere App funktionieren soll, da die ID die SharePoint-App ist.

Weitere Informationen [zur Authentifizierung finden Sie in Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Befolgen Sie Teams Designrichtlinien

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps*

Befolgen Sie [Teams Entwurfsrichtlinien,](../concepts/design/understand-use-cases.md) um Ihre App auf Teams zu sonnieren. Sie können einen vorhandenen App-Inhalt nicht auf eine Teams-Registerkarte migrieren. Weitere Informationen zum App-Design finden Sie unter [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximierung der tiefen Verknüpfung

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps, SharePoint*

Sie können Links zu Informationen und Features innerhalb Teams erstellen. Verwenden Sie [Deep Links,](../concepts/build-and-test/deep-links.md) um Ihre App mit Teams zu verknüpfen, da sie mehrere Teile einer App für eine nativere Teams-Erfahrung miteinander verknüpfen.

## <a name="be-smart-when-messaging-users"></a>Seien Sie intelligent, wenn Sie Messaging-Benutzer

***Integrationsszenarien**: Eigenständige Apps, Collaboration-Apps, SharePoint*

Verwenden Sie einen [Bot](../bots/what-are-bots.md) in Ihrer Teams-App für Multithread-Gespräche, da er mehr Flexibilität bietet als ein [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Bots ermöglichen es Ihnen auch, **proaktive Nachrichten** an einzelne Benutzer oder Kanäle zu senden. Die proaktiven Nachrichten sind nicht aufgeforderte Nachrichten, die durch ein externes Ereignis ausgelöst werden, und keine Nachricht, die an einen Bot gesendet wird. Beispielsweise sendet Ihr Bot eine Willkommensnachricht, wenn er installiert ist oder ein neuer Benutzer einem Kanal beitritt. 

Das Senden proaktiver Nachrichten erfordert Teams-spezifische Bezeichner. Sie können die Informationen erfassen, indem [Sie Dienstplan- oder Benutzerprofildaten abrufen,](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile) [Unterhaltungsereignisse abonnieren](../bots/how-to/conversations/subscribe-to-conversation-events.md)oder [Microsoft Graph](/graph/teams-proactive-messaging)verwenden.

Spam-Benutzer mit übermäßigen Nachrichten. Wenn die Teams-Funktion dies unterstützt, können die Benutzer Benachrichtigungseinstellungen für Ihre App konfigurieren.   
Im Folgenden finden Sie ein Beispiel für eine Benachrichtigung: **Senden Sie mir keine unaufgeforderten Nachrichten**.

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden SharePoint für die Datei- und Datenspeicherung

***Integrationsszenarien:** Eigenständige Apps, Collaboration-Apps SharePoint Seiten*

Wenn ein Team erstellt wird, wird auch eine [SharePoint Websitesammlung](/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um die Datei- und Datenspeicherung für dieses Team zu unterstützen. Ihre App muss diese Funktion nutzen, wenn sie mit Dateien interagiert. Verwenden Sie die Websitesammlung, um Rohdaten in SharePoint Listen und Excel zu speichern.

## <a name="see-also"></a>Siehe auch

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
