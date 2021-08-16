---
author: heath-hamilton
description: Bewährte Methoden für die Integration vorhandener Web-Apps in Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
localization_priority: Normal
ms.topic: conceptual
title: Web-Apps
ms.openlocfilehash: ba34241186484bb838ba3f61e5ca55914115a1f1
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345760"
---
# <a name="web-apps"></a>Web-Apps 

Sie können Web-Apps für soziale und zusammenarbeitende Features Teams eignen, indem Sie sie ordnungsgemäß in Teams integrieren.
  
Die verschiedenen Arten von Apps, die Sie in Teams integrieren können, sind wie folgt:
* **Eigenständige Apps:** Eine eigenständige App ist eine einzelseitige oder große und komplexe App. Der Benutzer kann einige Aspekte davon in Teams verwenden.
* Apps für die **Zusammenarbeit:** Eine App, die bereits für soziale und zusammenarbeitende Features erstellt wurde, die mit Teams verbunden sind.
* **SharePoint:** Eine SharePoint Seite, die in Teams angezeigt werden soll.

Sie können die entsprechende Richtlinie für Ihr Integrationsszenario zuordnen und befolgen.
Dieses Dokument bietet eine Übersicht über Teams Funktionen, Freigabepunktanforderungen für Datei- und Datenspeicherung, API-Anforderungen, Authentifizierung und Deep-Linking Ihrer App mit Teams.
 
## <a name="get-to-know-teams-platform-capabilities"></a>Kennenlernen Teams Plattformfunktionen

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Ihre Teams-App muss erforderliche und erwartete Features für die Zusammenarbeit enthalten. Um mit der App-Integration zu arbeiten, ist es wichtig, sich mit Teams Entwicklungsterminologie vertraut zu machen.

|Allgemeine App-Features   |Teams Plattformfunktionen   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder Webansicht  |[Tabs](../tabs/what-are-tabs.md)  |
|Freigeben von Verknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionsverknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Kanalbenachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Externe Nachrichtendienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modale  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Ermitteln einer Teilmenge von Funktionen

***Integrationsszenarien:** Eigenständige Apps*

Die Integration aller Features einer vorhandenen Anwendung in Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzererfahrung, insbesondere in größeren Apps. Beginnen Sie mit den wirkungsvollsten Features und den Features, die sich natürlicher in Teams integrieren. Sie können Benutzern erlauben, die Haupt-App zu starten und auf den gesamten Satz von Features zuzugreifen.

**Voraussetzungen für die Integration Ihrer App in Teams** Nachfolgend sind die Voraussetzungen für die Integration Ihrer App in Teams beschrieben. 

1. Ordnen Sie die [Anwendungsfälle Ihrer App Teams Plattformfunktionen zu.](../concepts/design/map-use-cases.md)
1. [Bestimmen Sie die Einstiegspunkte Ihrer App.](../concepts/extensibility-points.md) Ist es für den persönlichen Gebrauch, die Zusammenarbeit oder beides?

## <a name="understand-sharepoint-requirements-and-options"></a>Verstehen SharePoint Anforderungen und Optionen

***Integrationsszenarien:** SharePoint*

Um eine vorhandene [SharePoint Seite](/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) als Teams Registerkarte zu integrieren, müssen Sie Folgendes berücksichtigen:

* Dies muss eine *moderne* SharePoint Onlineseite sein.
* Es werden nur persönliche Registerkarten unterstützt. Sie können Ihre Seite nicht als Kanalregisterkarte integrieren.

Alternativ können Sie [mit dem](/sharepoint/dev/spfx/integrate-with-teams-introduction)SharePoint-Framework eine Teams Registerkarte erstellen.

## <a name="aim-towards-multi-tenancy"></a>Mehrinstanzenfähigkeit

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Wenn Ihre App von mehreren Organisationen verwendet wird, erwägen Sie mehrinstanzenfähiges Hosting, das Ihr Produkt skalierbar macht und die Verteilung erheblich vereinfacht.

## <a name="review-your-apis"></a>Überprüfen Ihrer APIs

***Integrationsszenarien:** eigenständige Apps, Apps für die Zusammenarbeit*

Sie müssen dafür sorgen, dass die vorhandenen APIs und Datenstrukturen Ihrer App die App bei der Integration mit Teams unterstützen. Um die Unterstützung zu erweitern, müssen Sie die APIs und Datenstrukturen mit kontextbezogenen Informationen zu Teams für [identitätszuordnung,](../concepts/authentication/configure-identity-provider.md) [Deep-Link-Unterstützung](../concepts/build-and-test/deep-links.md)und Integration von [Microsoft Graph](/graph/teams-concept-overview)erweitern.

Erfahren Sie mehr über das Abrufen des Kontexts für Ihre Teams [Registerkarte](../tabs/how-to/access-teams-context.md) oder [Ihren Bot.](../bots/how-to/get-teams-context.md)

## <a name="understand-authentication-options"></a>Grundlegendes zu Authentifizierungsoptionen

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Azure Active Directory (AD) ist der Identitätsanbieter für Teams. Wenn Ihre App einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitätszuordnungsübung durchführen oder mit Azure AD kombinieren.

Teams verfügt über SSO-Mechanismen (Single Sign-On) mit Azure AD für Apps von Drittanbietern. Es enthält auch die Anleitung für Authentifizierungsflüsse an andere Identitätsanbieter mit Standards wie OAuth und Open ID Verbinden, die als OIDC bezeichnet werden.

> [!IMPORTANT]
> Derzeit sind Apps von Drittanbietern in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und das Verteidigungsministerium (Department of Defense, DOD). Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Drittanbieter-Apps für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps.](/microsoftteams/manage-apps)

Für SharePoint Seiten können Sie nur SSO verwenden und keine weitere Azure AD-ID hinzufügen, wenn SSO für eine andere App verwendet werden soll, da die ID die SharePoint-App ist.

Weitere Informationen zur [Authentifizierung in Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Befolgen Teams Entwurfsrichtlinien

***Integrationsszenarien:** eigenständige Apps, Apps für die Zusammenarbeit*

Stellen Sie sicher, [dass Sie Teams Entwurfsrichtlinien](../concepts/design/understand-use-cases.md) befolgen, damit Ihre App für Teams systemeigen ist. Sie können einen vorhandenen App-Inhalt nicht zu einer Teams Registerkarte migrieren. Weitere Informationen zum App-Design finden Sie unter [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximieren der Deep-Verknüpfung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Sie können Links zu Informationen und Features in Teams erstellen. Verwenden Sie [Deep-Links,](../concepts/build-and-test/deep-links.md) um Ihre App mit Teams zu verknüpfen, da sie mehrere Teile einer App miteinander verknüpfen, um eine native Teams Zu bieten.

## <a name="be-smart-when-messaging-users"></a>Seien Sie intelligent, wenn Messaging-Benutzer

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Verwenden Sie einen [Bot](../bots/what-are-bots.md) in Ihrer Teams-App für Multithread-Unterhaltungen, da er mehr Flexibilität bietet als ein [Webhook.](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Bots ermöglichen es Ihnen auch, **proaktive Nachrichten** an einzelne Benutzer oder Kanäle zu senden. Bei den proaktiven Nachrichten handelt es sich um nicht empfangene Nachrichten, die durch ein externes Ereignis ausgelöst werden, und nicht um eine an einen Bot gesendete Nachricht. Beispielsweise sendet Ihr Bot eine Willkommensnachricht, wenn er installiert ist oder ein neuer Benutzer einem Kanal beitritt. 

Das Senden proaktiver Nachrichten erfordert Teams-spezifische Bezeichner. Sie können die Informationen erfassen, indem Sie [Listen- oder Benutzerprofildaten abrufen,](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile) [Unterhaltungsereignisse abonnieren](../bots/how-to/conversations/subscribe-to-conversation-events.md)oder [Microsoft Graph](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams)verwenden.

Spamen Sie Benutzer nicht mit übermäßigen Nachrichten. Wenn die Teams-Funktion dies unterstützt, können die Benutzer Benachrichtigungseinstellungen für Ihre App konfigurieren.   
Nachfolgend sehen Sie ein Beispiel für eine Benachrichtigung: **Senden Sie mir keine nicht empfangenen Nachrichten.**

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden von SharePoint für die Datei- und Datenspeicherung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint Seiten*

Wenn ein Team erstellt wird, wird auch eine [SharePoint Websitesammlung](/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um die Datei- und Datenspeicherung für dieses Team zu unterstützen. Ihre App muss dieses Feature nutzen, wenn sie mit Dateien interagiert. Verwenden Sie die Websitesammlung, um Rohdaten in SharePoint Listen und Excel zu speichern.

## <a name="see-also"></a>Siehe auch

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
