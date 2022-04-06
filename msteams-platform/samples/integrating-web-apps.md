---
author: heath-hamilton
description: Bewährte Methoden oder Überlegungen zum Integrieren vorhandener Web-Apps in Microsoft Teams
ms.author: surbhigupta
ms.date: 08/26/2020
ms.localizationpriority: medium
ms.topic: conceptual
title: Überlegungen zur Microsoft Teams-Integration
ms.openlocfilehash: eb278d078c7b195ff5d2d2a2f980ffc9db74f748
ms.sourcegitcommit: f892125106adb6731a20127f15d6e92f279127c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2022
ms.locfileid: "64685597"
---
# <a name="considerations-for-teams-integration"></a>Überlegungen zur Microsoft Teams-Integration

Sie können Web-Apps mit den Features für soziale Netzwerke und Zusammenarbeit von Teams eignen, indem Sie sie ordnungsgemäß in Teams integrieren.
  
Die verschiedenen Arten von Apps, die Sie in Teams integrieren können, sind die folgenden:

* **Eigenständige Apps**: Eine eigenständige App ist eine einzelseitige oder große und komplexe App. Der Benutzer kann einige Aspekte davon in Teams verwenden.
* **Apps** für die Zusammenarbeit: Eine App, die bereits für die funktionen für soziale Netzwerke und zusammenarbeiten entwickelt wurde, die Teams.
* **SharePoint**: Eine SharePoint Seite, die in Teams angezeigt werden soll.

Sie können die für Ihr Integrationsszenario geeignete Richtlinie zuordnen und befolgen.
Dieses Dokument bietet einen Überblick über Teams Funktionen, Share-Point-Anforderungen für die Datei- und Datenspeicherung, API-Anforderungen, Authentifizierung und Deep-Linking Ihrer App mit Teams.

## <a name="get-to-know-teams-platform-capabilities"></a>Kennenlernen Teams Plattformfunktionen

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Ihre Teams-App muss erforderliche und erwartete Features für die Zusammenarbeit enthalten. Um mit der App-Integration zu arbeiten, ist es wichtig, sich mit Teams Entwicklungsterminologie vertraut zu machen.

|Allgemeine App-Features   |Teams Plattformfunktionen   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder Webview  |[Registerkarten](../tabs/what-are-tabs.md)  |
|Freigeben von Tastenkombinationen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionsverknüpfungen und -erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots |[Bots](../bots/what-are-bots.md) |
|Kanalbenachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Externe Nachrichtendienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modale Modalitäten  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Ermitteln einer Teilmenge der Funktionalität

***Integrationsszenarien**: Eigenständige Apps*

Die Integration aller Features einer vorhandenen Anwendung in Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzererfahrung, insbesondere in größeren Apps. Beginnen Sie mit den wirkungsvollsten Features und solchen, die sich natürlicher in Teams integrieren. Sie können Benutzern erlauben, die Haupt-App zu starten und auf die vollständigen Features zuzugreifen.

Im Folgenden sind die Voraussetzungen für die Integration Ihrer App in Teams.

1. [Ordnen Sie die Anwendungsfälle Ihrer App Teams Plattformfunktionen zu](../concepts/design/map-use-cases.md).
1. [Bestimmen Sie die Einstiegspunkte Ihrer App](../concepts/extensibility-points.md). Ist es für den persönlichen Gebrauch, für die Zusammenarbeit oder für beides?

## <a name="understand-sharepoint-requirements-and-options"></a>Grundlegendes zu SharePoint Anforderungen und Optionen

***Integrationsszenarien**: SharePoint*

Um eine vorhandene [SharePoint Seite](/sharepoint/dev/general-development/overview-of-the-sharepoint-page-model) als Teams Registerkarte zu integrieren, müssen Sie Folgendes berücksichtigen:

* Es muss eine *moderne* SharePoint Onlineseite sein.
* Es werden nur persönliche Registerkarten unterstützt. Sie können Ihre Seite nicht als Kanalregisterkarte integrieren.

Alternativ können Sie [mithilfe der](/sharepoint/dev/spfx/integrate-with-teams-introduction) SharePoint-Framework eine Teams Registerkarte erstellen.

## <a name="aim-towards-multitenancy"></a>Mehrinstanzenfähigkeit anstreben

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Wenn Ihre App von mehreren Organisationen verwendet wird, sollten Sie mehrinstanzenfähiges Hosting in Betracht ziehen. Es macht Ihr Produkt skalierbar und vereinfacht die Verteilung.

## <a name="review-your-apis"></a>Überprüfen Ihrer APIs

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit*

Die APIs und Datenstrukturen Ihrer App müssen die App bei der Integration in Teams unterstützen. Um die Unterstützung zu erweitern, müssen Sie die APIs und Datenstrukturen mit Kontextinformationen zu Teams für [Identitätszuordnung](../concepts/authentication/configure-identity-provider.md), [Deep-Link-Unterstützung](../concepts/build-and-test/deep-links.md) und [die Integration von Microsoft Graph](/graph/teams-concept-overview) erweitern.

Erfahren Sie, wie Sie Kontext für Ihre Teams [Registerkarte](../tabs/how-to/access-teams-context.md) oder Ihren [Bot](../bots/how-to/get-teams-context.md) abrufen.

## <a name="understand-authentication-options"></a>Grundlegendes zu Authentifizierungsoptionen

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Azure Active Directory ist der Identitätsanbieter für Teams. Wenn Ihre App einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitätszuordnungsübung durchführen oder mit Microsoft Azure Active Directory (Azure AD) kombinieren.

Teams verfügt über SSO-Mechanismen (Single Sign-On) mit Azure AD für Drittanbieter-Apps. Es bietet auch die Anleitung für Authentifizierungsflüsse an andere Identitätsanbieter mithilfe von Standards wie OAuth und Open ID Verbinden, bekannt als OIDC.

> [!IMPORTANT]
> Derzeit sind Drittanbieter-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und das Verteidigungsministerium (DEPARTMENT of Defense, DOD). Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Apps von Drittanbietern für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps](/microsoftteams/manage-apps).

Für SharePoint Seiten können Sie nur SSO verwenden und keine weitere Azure AD-ID hinzufügen, wenn SSO für eine andere App verwendet werden soll, da die ID die SharePoint App ist.

Weitere Informationen zur [Authentifizierung in Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Befolgen Teams Designrichtlinien

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit*

Achten Sie darauf, [Teams Designrichtlinien](../concepts/design/understand-use-cases.md) zu befolgen, damit Ihre App Teams nativ ist. Sie können einen vorhandenen App-Inhalt nicht zu einer Teams Registerkarte migrieren. Weitere Informationen zum App-Design finden Sie [unter Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximieren der Tiefenverknüpfung

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Sie können Links zu Informationen und Features in Teams erstellen. Verwenden Sie [Deep-Links](../concepts/build-and-test/deep-links.md), um Ihre App mit Teams zu verknüpfen, während sie mehrere Teile einer App miteinander verbinden, um eine systemeigenere Teams zu ermöglichen.

## <a name="be-smart-when-messaging-users"></a>Seien Sie beim Messaging von Benutzern intelligent

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Verwenden Sie einen [Bot](../bots/what-are-bots.md) in Ihrer Teams-App für Multithreadunterhaltungen, da er mehr Flexibilität als ein [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md) bietet.

Bots ermöglichen es Ihnen auch **, proaktive Nachrichten** an einzelne Benutzer oder Kanäle zu senden. Bei den proaktiven Nachrichten handelt es sich um nicht bereitgestellte Nachrichten, die durch ein externes Ereignis ausgelöst werden, und nicht um eine Nachricht, die an einen Bot gesendet wird. Beispielsweise sendet Ihr Bot eine Willkommensnachricht, wenn er installiert ist oder ein neuer Benutzer einem Kanal beitritt.

Das Senden proaktiver Nachrichten erfordert Teams-spezifische Bezeichner. Sie können die Informationen erfassen, indem Sie [Listen- oder Benutzerprofildaten abrufen](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile), [Unterhaltungsereignisse abonnieren](../bots/how-to/conversations/subscribe-to-conversation-events.md) oder [Microsoft Graph](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams) verwenden.

Spamen Sie Benutzer nicht mit übermäßigen Nachrichten. Wenn die Teams-Funktion dies unterstützt, können die Benutzer Benachrichtigungseinstellungen für Ihre App konfigurieren.
Es folgt ein Beispiel für eine Benachrichtigung: **Senden Sie mir keine nicht bereitgestellten Nachrichten**.

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden von SharePoint für Datei- und Datenspeicherung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint Seiten*

Wenn ein Team erstellt wird, wird auch eine [SharePoint Websitesammlung](/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um die Datei- und Datenspeicherung für dieses Team zu unterstützen. Ihre App muss dieses Feature nutzen, wenn sie mit Dateien interagiert. Verwenden Sie die Websitesammlung, um Rohdaten in SharePoint Listen und Microsoft Excel zu speichern.

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Low-Code- und No-Code-Lösungen für Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Freigeben für Teams aus Web-Apps](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [SameSite-Cookieattribute](~/resources/samesite-cookie-update.md)
* [Integrieren Power Virtual Agents Chatbots](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
