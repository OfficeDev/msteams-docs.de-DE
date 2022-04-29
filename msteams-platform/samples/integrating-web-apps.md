---
author: heath-hamilton
description: Bewährte Methoden oder Überlegungen zum Integrieren vorhandener Web-Apps in Microsoft Teams
ms.author: surbhigupta
ms.date: 08/26/2020
ms.localizationpriority: high
ms.topic: conceptual
title: Überlegungen zur Microsoft Teams-Integration
ms.openlocfilehash: 2e1d749a34d0dec2a38e84e57aa6147c791264c1
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111661"
---
# <a name="considerations-for-teams-integration"></a>Überlegungen zur Microsoft Teams-Integration

Sie können Webanwendungen mit den sozialen und kollaborativen Funktionen von Microsoft Teams ausstatten, indem Sie sie richtig in Microsoft Teams integrieren.
  
Folgende Arten von Apps können Sie in Microsoft Teams integrieren:

* **Eigenständige Apps**: Eine eigenständige App ist eine einseitige oder große und komplexe App. Der Benutzer kann einige Aspekte davon in Teams verwenden.
* **Apps für die Zusammenarbeit**: Eine App, die bereits für die sozialen und kollaborativen Features von Microsoft Teams entwickelt wurde.
* **SharePoint**: Eine SharePoint-Seite, die in Microsoft Teams angezeigt werden soll.

Sie können die für Ihr Integrationsszenario geeignete Richtlinie zuordnen und befolgen.
Dieses Dokument bietet einen Überblick über Microsoft Teams-Funktionen, Share-Point-Anforderungen für die Datei- und Datenspeicherung, API-Anforderungen, Authentifizierung und Deep-Linking Ihrer App mit Microsoft Teams.

## <a name="get-to-know-teams-platform-capabilities"></a>Lernen Sie die Funktionen der Microsoft Teams-Plattform kennen

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Ihre Microsoft Teams-App muss erforderliche und erwartete Features für die Zusammenarbeit enthalten. Um mit der App-Integration zu arbeiten, ist es wichtig, sich mit Microsoft Teams-Entwicklungsterminologie vertraut zu machen.

|Allgemeine App-Features   |Funktionen der Microsoft Teams-Plattform   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder Webview  |[Registerkarten](../tabs/what-are-tabs.md)  |
|Freigabetastenkombinationen und -erweiterungen  |[Nachrichtenerweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionstastenkombinationen und -erweiterungen  |[Nachrichtenerweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots |[Bots](../bots/what-are-bots.md) |
|Kanalbenachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Externe Nachrichtendienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modale Elemente  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Bestimmen Sie eine Teilmenge von Funktionen

***Integrationsszenarien**: Eigenständige Apps*

Die Integration aller Features einer vorhandenen Anwendung in Microsoft Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzererfahrung, insbesondere in größeren Apps. Beginnen Sie mit den wirkungsvollsten Features und solchen, die sich natürlicher in Microsoft Teams integrieren. Sie können Benutzern erlauben, die Haupt-App zu starten und auf den vollständigen Featuresatz zuzugreifen.

Im Folgenden sind die Voraussetzungen für die Integration Ihrer App in Microsoft Teams aufgeführt.

1. [Ordnen Sie die Anwendungsfälle Ihrer App zu Funktionen der Microsoft Teams-Plattform zu](../concepts/design/map-use-cases.md).
1. [Bestimmen Sie die Einstiegspunkte Ihrer App](../concepts/extensibility-points.md). Ist sie für den persönlichen Gebrauch, für die Zusammenarbeit oder für beides bestimmt?

## <a name="understand-sharepoint-requirements-and-options"></a>Grundlegendes zu SharePoint-Anforderungen und -Optionen

***Integrationsszenarien**: SharePoint*

Um eine vorhandene [SharePoint-Seite](/sharepoint/dev/general-development/overview-of-the-sharepoint-page-model) als Microsoft Teams-Registerkarte zu integrieren, müssen Sie Folgendes berücksichtigen:

* Es muss eine *moderne* SharePoint-Onlineseite sein.
* Derzeit werden nur persönliche Registerkarten unterstützt. Sie können Ihre Seite nicht als Kanalregisterkarte integrieren.

Alternativ können Sie eine Microsoft Teams-Registerkarte [mit dem SharePoint-Framework](/sharepoint/dev/spfx/integrate-with-teams-introduction) erstellen.

## <a name="aim-towards-multitenancy"></a>Streben Sie Mehrinstanzenfähigkeit an.

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Wenn Ihre App von mehreren Organisationen verwendet wird, sollten Sie mehrinstanzenfähiges Hosting in Betracht ziehen. Es macht Ihr Produkt skalierbar und vereinfacht die Verteilung.

## <a name="review-your-apis"></a>Überprüfen Ihrer APIs

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit*

Die APIs und Datenstrukturen Ihrer App müssen die App bei der Integration in Microsoft Teams unterstützen. Um die Unterstützung zu erweitern, müssen Sie die APIs und Datenstrukturen mit Kontextinformationen zu Microsoft Teams für [Identitätszuordnung](../concepts/authentication/configure-identity-provider.md), [Deep-Link-Unterstützung](../concepts/build-and-test/deep-links.md) und [Integration von Microsoft Graph](/graph/teams-concept-overview) erweitern.

Erfahren Sie, wie Sie Kontext für Ihre Microsoft Teams-[Registerkarte](../tabs/how-to/access-teams-context.md) oder Ihren [Bot](../bots/how-to/get-teams-context.md) abrufen.

## <a name="understand-authentication-options"></a>Grundlegendes zu Authentifizierungsoptionen

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Azure Active Directory ist der Identitätsanbieter für Microsoft Teams. Wenn Ihre App einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitätszuordnungsübung durchführen oder mit Microsoft Azure Active Directory (Azure AD) kombinieren.

Microsoft Teams verfügt über Mechanismen für einmaliges Anmelden (Single Sign-On, SSO) mit Azure AD für Drittanbieter-Apps. Es bietet auch die Anleitung für Authentifizierungsflüsse an andere Identitätsanbieter unter Anwendung von Standards wie OAuth und Open ID Connect, auch bekannt als OIDC.

> [!IMPORTANT]
> Derzeit sind Drittanbieter-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und Department of Defense (DOD). Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Drittanbieter-Apps für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps](/microsoftteams/manage-apps).

Für SharePoint-Seiten können Sie nur SSO verwenden und keine weitere Azure AD-ID hinzufügen, wenn SSO für eine andere App verwendet werden soll, da die ID die SharePoint-App ist.

Erfahren Sie mehr über die [Authentifizierung in Microsoft Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Befolgen der Designrichtlinien für Microsoft Teams

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit*

Achten Sie darauf, die [Microsoft Teams-Designrichtlinien](../concepts/design/understand-use-cases.md) zu befolgen, um native Apps für Microsoft Teams zu erstellen. Sie können vorhandenen App-Inhalt nicht zu einer Microsoft Teams-Registerkarte migrieren. Weitere Informationen zum App-Design finden Sie unter [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximieren von Deep Linking

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Sie können Links zu Informationen und Features in Teams erstellen. Verwenden Sie [Deep-Links](../concepts/build-and-test/deep-links.md), um Ihre App mit Microsoft Teams zu verknüpfen, da so mehrere Teile einer App miteinander verknüpft werden, um eine nativere Microsoft Teams-Erfahrung zu ermöglichen.

## <a name="be-smart-when-messaging-users"></a>Gehen Sie beim Senden von Nachrichten an Benutzer intelligent vor.

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Verwenden Sie in Ihrer Microsoft Teams-App für Multithreadunterhaltungen einen [Bot](../bots/what-are-bots.md), da dieser mehr Flexibilität als ein [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md) bietet.

Bots ermöglichen Ihnen auch **, proaktive Nachrichten** an einzelne Benutzer oder Kanäle zu senden. Bei den proaktiven Nachrichten handelt es sich um nicht angeforderte Nachrichten, die durch ein externes Ereignis ausgelöst werden, und nicht um Nachrichten, die an einen Bot gesendet werden. Beispielsweise sendet Ihr Bot eine Willkommensnachricht, wenn er installiert wird oder ein neuer Benutzer einem Kanal beitritt.

Das Senden proaktiver Nachrichten erfordert Microsoft Teams-spezifische Bezeichner. Sie können die Informationen erfassen, indem Sie [Listen- oder Benutzerprofildaten abrufen](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile), [Unterhaltungsereignisse abonnieren](../bots/how-to/conversations/subscribe-to-conversation-events.md) oder [Microsoft Graph](/microsoftteams/platform/graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages?context=graph/context#proactive-messaging-in-teams) verwenden.

Spammen Sie die Benutzer nicht mit übermäßigen Nachrichten zu. Wenn die Microsoft Teams-Funktion dies unterstützt, können die Benutzer Benachrichtigungseinstellungen für Ihre App konfigurieren.
Es folgt ein Beispiel für eine Benachrichtigung: **Senden Sie mir keine nicht angeforderten Nachrichten**.

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden von SharePoint für Datei- und Datenspeicherung

***Integrationsszenarien**: Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint-Seiten*

Bei der Erstellung eines Teams wird auch eine [SharePoint-Websitesammlung](/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um die Speicherung von Dateien und Daten für dieses Team zu unterstützen. Ihre App muss dieses Feature nutzen, wenn mit Dateien interagiert wird. Verwenden Sie die Websitesammlung, um Rohdaten in SharePoint-Listen und Microsoft Excel zu speichern.

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Low-Code- und No-Code-Lösungen für Microsoft Teams](~/samples/teams-low-code-solutions.md)
* [Von Web-Apps für Teams freigeben](~/concepts/build-and-test/share-to-teams-from-web-apps.md)
* [SameSite-Cookieattribute](~/resources/samesite-cookie-update.md)
* [Integrieren des Power Virtual Agents-Chatbots](~/bots/how-to/add-power-virtual-agents-bot-to-teams.md)
