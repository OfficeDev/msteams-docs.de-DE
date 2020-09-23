---
author: heath-hamilton
description: Bewährte Methoden für die Integration vorhandener Webanwendungen mit Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
ms.topic: conceptual
title: Integrieren einer-Webanwendung in Microsoft Teams
ms.openlocfilehash: e7d4f74526f7a71fe33d5a70d9ed60be960adefc
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210274"
---
# <a name="integrate-web-apps-with-teams"></a>Integrieren von Webanwendungen in Microsoft Teams

Haben Sie eine Webanwendung, die ihrer Meinung nach auf natürliche Weise mit den sozialen und kollaborativen Features von Teams zusammen passt? Mithilfe dieser Richtlinien können Sie verstehen, wie die folgenden Arten von Apps integriert werden:

* **Eigenständige apps**: könnte eine einseitige APP oder eine große, komplexe APP sein, für die Benutzer einige Aspekte in Microsoft Teams verwenden möchten.
* **Collaboration apps**: eine APP, die bereits für die sozialen und kollaborativen Features von Teams entwickelt wurde.
* **SharePoint**: eine SharePoint-Seite, die Sie in Microsoft Teams Oberfläche anzeigen möchten.

Für jede Richtlinie können Sie sehen, ob Sie für Ihr Integrationsszenario geeignet ist.

## <a name="get-to-know-teams-platform-capabilities"></a>Erfahren Sie mehr über die Plattformfunktionen von Teams

***Integrationsszenarien**: eigenständige apps, Collaboration-apps, SharePoint *

Ihre Teams-App kann Features enthalten, die Benutzer wünschen und möglicherweise bei der Zusammenarbeit erwarten, aber Sie sind möglicherweise nicht mit der Entwicklungs Terminologie von Teams vertraut.

|Allgemeine App-Funktionen   |Plattformfunktionen für Teams   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder WebView  |[Tabs](../tabs/what-are-tabs.md)  |
|Freigeben von Verknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionsverknüpfungen und-Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Kanal Benachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Externe Nachrichtendienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modals  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Bestimmen einer Teilmenge der Funktionalität

***Integrationsszenarien**: eigenständige apps *

Die Integration aller Features einer vorhandenen Anwendung in Microsoft Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzererfahrung, insbesondere in größeren apps. Beginnen Sie mit den wirkungsvollsten Features und denen, die sich natürlicher in Microsoft Teams integrieren lassen. Denken Sie daran, dass Sie den Benutzern jederzeit das Starten der Haupt-APP und den Zugriff auf den vollständigen Funktionsumfang ermöglichen können.

Bevor Sie mit technischen Arbeiten beginnen, müssen Sie sich mit der Planung Ihrer Teams-App befassen:

1. [Ordnen Sie die Anwendungsfälle Ihrer APP den Plattformfunktionen von Teams zu](../concepts/design/map-use-cases.md).
1. [Bestimmen Sie die Einstiegspunkte Ihrer APP](../concepts/extensibility-points.md). Ist es für den persönlichen Gebrauch, die Zusammenarbeit oder beides?

## <a name="understand-sharepoint-requirements-and-options"></a>Grundlegendes zu SharePoint-Anforderungen und-Optionen

***Integrationsszenarien**: SharePoint *

Sie können eine vorhandene [SharePoint-Seite](https://docs.microsoft.com/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) als Registerkarte Teams integrieren. Beachten Sie Folgendes:

* Es muss sich um eine *moderne* SharePoint Online Seite handeln.
* Nur persönliche Registerkarten werden unterstützt (Sie können Ihre Seite nicht als Kanal Registerkarte integrieren)

Alternativ können Sie eine Teams-Registerkarte [mithilfe des SharePoint-Frameworks](https://docs.microsoft.com/sharepoint/dev/spfx/integrate-with-teams-introduction)erstellen.

## <a name="aim-towards-multi-tenancy"></a>Ziel für Mehrmandantenfähigkeit

***Integrationsszenarien**: eigenständige apps, Collaboration-apps, SharePoint *

Wenn Ihre APP von mehreren Organisationen verwendet wird, sollten Sie ein Mehrmandantenfähiges Hosting in Frage stellen, das Ihr Produkt skalierbar macht und die Verteilung erheblich vereinfacht.

## <a name="review-your-apis"></a>Überprüfen der APIs

***Integrationsszenarien**: eigenständige apps, Collaboration-apps *

Gehen Sie nicht davon aus, dass die vorhandenen APIs und Datenstrukturen der App bei Integration in Microsoft Teams die APP vollständig unterstützen. Möglicherweise müssen Sie diese mit Kontextinformationen zu Teams für die [Identitätszuordnung](../concepts/authentication/configure-identity-provider.md), die [Deep-Link-Unterstützung](../concepts/build-and-test/deep-links.md)und die [Einbindung von Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview)erweitern.

Erfahren Sie mehr über das erhalten von Kontext für Ihre Teams- [Registerkarte](../tabs/how-to/access-teams-context.md) oder [bot](../bots/how-to/get-teams-context.md).

## <a name="understand-authentication-options"></a>Grundlegendes zu Authentifizierungsoptionen

***Integrationsszenarien**: eigenständige apps, Collaboration-apps, SharePoint *

Azure Active Directory (AD) ist der Identitätsanbieter für Teams. Wenn Ihre APP einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitäts Zuordnungsübung durchführen oder eine Föderation mit Azure AD.

Microsoft Teams verfügt über SSO-Mechanismen (Single Sign-on, einmaliges Anmelden) mit Azure AD für Drittanbieter-apps und Anleitungen für Authentifizierungs Flüsse an andere Identitätsanbieter mithilfe von Standards wie OAuth und Open ID Connect (OIDC).

Für SharePoint-Seiten können Sie nur SSO verwenden und keine weitere Azure Ad-ID hinzufügen, wenn SSO für eine andere App verwendet werden soll (da die ID die SharePoint-APP ist).

Erfahren Sie mehr über die [Authentifizierung in Microsoft Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Befolgen der Entwurfsrichtlinien für Teams

***Integrationsszenarien**: eigenständige apps, Collaboration-apps *

Im Allgemeinen sollte sich Ihre APP in Microsoft Teams als natürlich erweisen. Es kann sein, dass die Migration vorhandener App-Inhalte in eine Teams-Registerkarte ausreicht, es wird jedoch dringend empfohlen, dass Ihre APP die [Entwurfsrichtlinien für Teams](../concepts/design/understand-use-cases.md)befolgt. Siehe auch: [Fluent-Entwurfs System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximieren der tiefen Verknüpfung

***Integrationsszenarien**: eigenständige apps, Collaboration-apps, SharePoint *

Fast alles in Microsoft Teams kann direkt mit einer [tiefen Verknüpfung](../concepts/build-and-test/deep-links.md)verknüpft werden. Ihre APP sollte die Verwendung dieser Informationen maximieren, einschließlich der Verknüpfung zu und von bestimmten Nachrichten und Registerkarten Inhalten. Deep Links können tatsächlich mehrere Teile einer APP für eine nativere Teams-Erfahrung miteinander verknüpfen.

## <a name="be-smart-when-messaging-users"></a>Smart sein, wenn Messaging-Benutzer

***Integrationsszenarien**: eigenständige apps, Collaboration-apps, SharePoint *

Denken Sie an die Nachrichtentypen, die ihre Teams-APP jetzt und langfristig senden kann. Wenn Sie der Meinung sind, dass Ihre APP jemals eine Multithread-Unterhaltung hat, bietet ein [bot](../bots/what-are-bots.md) möglicherweise mehr Flexibilität als ein [webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)-Objekt.

Bots ermöglichen auch das Senden *proaktiver Nachrichten* an einzelne Benutzer oder Kanäle. Dabei handelt es sich um unaufgeforderte Nachrichten, die von einem externen Ereignis ausgelöst werden, und nicht aus einer an einen bot gesendeten Nachricht. (Beispielsweise kann Ihr bot eine Willkommensnachricht senden, wenn Sie installiert ist oder wenn ein neuer Benutzer einem Kanal Beitritt.) 

Das Senden proaktiver Nachrichten erfordert Teams-spezifische Bezeichner – Sie können diese Informationen erfassen, indem Sie [Dienstplan-oder Benutzerprofildaten abrufen](../bots/how-to/get-teams-context.md#fetching-the-roster-or-user-profile), [unterhaltungsereignisse abonnieren](../bots/how-to/conversations/subscribe-to-conversation-events.md)oder [Microsoft Graph](https://docs.microsoft.com/graph/teams-proactive-messaging)verwenden.

Achten Sie darauf, dass Sie Benutzer nicht mit übermäßigen Nachrichten spamisieren. Wenn die Teams-Funktion dies unterstützt, können Benutzer die Benachrichtigungseinstellungen für Ihre APP konfigurieren (beispielsweise "keine unaufgeforderten Nachrichten senden").

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden von SharePoint für Datei-und Datenspeicher

***Integrationsszenarien:** Eigenständige apps, Collaboration-apps, SharePoint-Seiten*

Wenn ein Team erstellt wird, wird auch eine [SharePoint-Websitesammlung](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um Datei-und Datenspeicher für dieses Team zu unterstützen. Ihre APP kann und sollte diese Funktion nutzen, wenn Sie mit Dateien interagiert. Sie können die Websitesammlung auch zum Speichern von Rohdaten in SharePoint-Listen und Excel verwenden.
