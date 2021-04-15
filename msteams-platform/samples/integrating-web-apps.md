---
author: heath-hamilton
description: Bewährte Methoden für die Integration vorhandener Web-Apps in Microsoft Teams
ms.author: v-heha
ms.date: 08/26/2020
ms.topic: conceptual
title: Integrieren einer Web-App in Microsoft Teams
ms.openlocfilehash: 4671d2277d5eb7c035421c51b1714eccaac06a31
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696486"
---
# <a name="integrate-web-apps-with-teams"></a>Integrieren von Web-Apps in Teams

Verfügen Sie über eine Web-App, die ihrer Meinung nach natürlich in die Features für soziale netzwerke und zusammenarbeiten von Teams passen würde? Diese Richtlinien helfen Ihnen zu verstehen, wie Sie die folgenden Arten von Apps integrieren:

* **Eigenständige Apps:** Dies kann eine einseitige App oder eine große, komplexe App sein, von der Personen einige Aspekte in Teams verwenden sollen.
* **Apps für die** Zusammenarbeit: Eine App, die bereits für die features für soziale Netzwerke und Zusammenarbeit in Teams erstellt wurde.
* **SharePoint**: Eine SharePoint-Seite, die Sie in Teams anzeigen möchten.

Für jede Richtlinie können Sie sehen, ob sie auf Ihr Integrationsszenario anwendbar ist.

## <a name="get-to-know-teams-platform-capabilities"></a>Kennenlernen der Funktionen der Teams-Plattform

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Ihre Teams-App kann Features enthalten, die Benutzer bei der Zusammenarbeit wünschen und erwarten können, aber Sie sind möglicherweise nicht mit der Teams-Entwicklungsterminologie vertraut.

|Allgemeine App-Features   |Funktionen der Teams-Plattform   |
|----------|-----------|
|Eingebettete Webseite, Homepage oder Webview  |[Tabs](../tabs/what-are-tabs.md)  |
|Freigeben von Verknüpfungen und Erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Aktionsverknüpfungen und -erweiterungen  |[Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)  |
|Chatbots  |[Bots](../bots/what-are-bots.md) |
|Kanalbenachrichtigungen  |[Bots](../bots/what-are-bots.md)<br/>[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)<br/>[Office 365-Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Externe Nachrichtendienste  |[Bots](../bots/what-are-bots.md)<br/>[Ausgehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)  |
|Modale  |[Aufgabenmodule](../task-modules-and-cards/what-are-task-modules.md)  |
|Inhaltsreiche Karten  |[Adaptive Karten](../task-modules-and-cards/what-are-cards.md)  |

## <a name="determine-a-subset-of-functionality"></a>Bestimmen einer Teilmenge der Funktionalität

***Integrationsszenarien:** Eigenständige Apps*

Die Integration aller Features einer vorhandenen Anwendung in Teams führt häufig zu einer erzwungenen oder unnatürlichen Benutzererfahrung, insbesondere in größeren Apps. Erwägen Sie, mit den auswirkungenreichsten Features und denen zu beginnen, die sich besser in Teams integrieren lassen. Denken Sie daran, dass Sie Benutzern immer erlauben können, die Haupt-App zu starten und auf den vollständigen Satz von Features zu zugreifen.

Bevor Sie mit den technischen Arbeiten beginnen, planen Sie ihre Teams-App:

1. [Ordnen Sie die Anwendungsfälle Ihrer App den Funktionen der Teams-Plattform zu.](../concepts/design/map-use-cases.md)
1. [Bestimmen Sie die Einstiegspunkte Ihrer App.](../concepts/extensibility-points.md) Ist dies für den persönlichen Gebrauch, die Zusammenarbeit oder beides?

## <a name="understand-sharepoint-requirements-and-options"></a>Verstehen von SharePoint-Anforderungen und -Optionen

***Integrationsszenarien**: SharePoint*

Sie können eine vorhandene [SharePoint-Seite als](https://docs.microsoft.com/MicrosoftTeams/teams-standalone-static-tabs-using-spo-sites) Registerkarte Teams integrieren. Beachten Sie Folgendes:

* Es muss eine *moderne* SharePoint Online-Seite sein.
* Es werden nur persönliche Registerkarten unterstützt (Sie können Ihre Seite nicht als Kanalregisterkarte integrieren)

Alternativ können Sie eine Registerkarte Teams mit [dem SharePoint Framework erstellen.](https://docs.microsoft.com/sharepoint/dev/spfx/integrate-with-teams-introduction)

## <a name="aim-towards-multi-tenancy"></a>Ziel von Mehr-Mandanz

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Wenn Ihre App von mehreren Organisationen verwendet wird, sollten Sie das Mehr-Mandanten-Hosting in Betracht ziehen, das Ihr Produkt skalierbar und die Verteilung erheblich vereinfachen würde.

## <a name="review-your-apis"></a>Überprüfen Ihrer APIs

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit*

Gehen Sie nicht davon aus, dass die vorhandenen APIs und Datenstrukturen Ihrer App die App bei der Integration in Teams vollständig unterstützen. Möglicherweise müssen Sie diese mit kontextbezogenen [](../concepts/authentication/configure-identity-provider.md)Informationen zu Teams für die Identitätszuordnung, die Unterstützung von [DeepLinks](../concepts/build-and-test/deep-links.md)und die Integration [von Microsoft Graph erweitern.](https://docs.microsoft.com/graph/teams-concept-overview)

Erfahren Sie mehr über das Abrufen des Kontexts für Ihre Registerkarte [oder](../tabs/how-to/access-teams-context.md) Ihren Bot für [Teams.](../bots/how-to/get-teams-context.md)

## <a name="understand-authentication-options"></a>Verstehen von Authentifizierungsoptionen

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Azure Active Directory (AD) ist der Identitätsanbieter für Teams. Wenn Ihre App einen anderen Identitätsanbieter verwendet, müssen Sie entweder eine Identitätszuordnungsübung oder einen Verbund mit Azure AD erstellen.

Teams verfügt über Mechanismen für einmaliges Anmelden (Single Sign-On, SSO) mit Azure AD für Drittanbieter-Apps und Anleitungen für Authentifizierungsflüsse an andere Identitätsanbieter mithilfe von Standards wie OAuth und Open ID Connect (OIDC).

Für SharePoint-Seiten können Sie nur SSO verwenden und keine weitere Azure AD-ID hinzufügen, wenn SSO für eine andere App verwendet werden soll (da die ID die SharePoint-App ist).

Erfahren Sie mehr über [die Authentifizierung in Teams](../concepts/authentication/authentication.md).

## <a name="follow-teams-design-guidelines"></a>Befolgen von Teams-Entwurfsrichtlinien

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit*

Im Allgemeinen sollte sich Ihre App in Teams natürlich anfühlen. Möglicherweise halten Sie die Migration vorhandener App-Inhalte zu einer Registerkarte Teams für ausreichend, es wird jedoch dringend empfohlen, dass Ihre App [den Teams-Entwurfsrichtlinien folgt.](../concepts/design/understand-use-cases.md) Siehe auch: [Fluent Design System](https://fluentsite.z22.web.core.windows.net/).

## <a name="maximize-deep-linking"></a>Maximieren der tiefen Verknüpfung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Fast alles in Teams kann direkt mit einem tiefen [Link verknüpft werden.](../concepts/build-and-test/deep-links.md) Ihre App sollte diese maximieren, einschließlich der Verknüpfung mit und von bestimmten Nachrichten und Registerkarteninhalten. Tiefe Links können wirklich mehrere Teile einer App verbinden, um eine nativere Teams-Erfahrung zu ermöglichen.

## <a name="be-smart-when-messaging-users"></a>Smart sein, wenn Messagingbenutzer

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint*

Berücksichtigen Sie die Arten von Nachrichten, die Ihre Teams-App jetzt und langfristig senden kann. Wenn Sie glauben, dass Ihre App jemals über eine Unterhaltung mit mehreren Threads verfügen wird, bietet ein [Bot](../bots/what-are-bots.md) möglicherweise mehr Flexibilität als ein [Webhook](../webhooks-and-connectors/what-are-webhooks-and-connectors.md).

Mit Bots können Sie auch proaktive Nachrichten *an* einzelne Benutzer oder Kanäle senden. Dabei handelt es sich um nicht gesendete Nachrichten, die durch ein externes Ereignis ausgelöst werden, und nicht um eine Nachricht, die an einen Bot gesendet wird. (Ihr Bot kann z. B. eine Willkommensnachricht senden, wenn er installiert ist oder ein neuer Benutzer einem Kanal beitritt.)

Für das Senden proaktiver Nachrichten sind teamsspezifische Bezeichner erforderlich– Sie können [](../bots/how-to/conversations/subscribe-to-conversation-events.md)diese Informationen erfassen, indem Sie Dienstplan- oder Benutzerprofildaten [abrufen,](../bots/how-to/get-teams-context.md#fetch-the-roster-or-user-profile)Unterhaltungsereignisse abonnieren oder Microsoft [Graph verwenden.](https://docs.microsoft.com/graph/teams-proactive-messaging)

Achten Sie darauf, Benutzer nicht mit übermäßigen Nachrichten zu spamen. Wenn sie von der Teams-Funktion unterstützt wird, sollten Sie es Benutzern ermöglichen, Benachrichtigungseinstellungen für Ihre App zu konfigurieren (z. B. "Senden Sie mir keine unprompten Nachrichten.").

## <a name="use-sharepoint-for-file-and-data-storage"></a>Verwenden von SharePoint für Datei- und Datenspeicherung

***Integrationsszenarien:** Eigenständige Apps, Apps für die Zusammenarbeit, SharePoint-Seiten*

Wenn ein Team erstellt wird, wird auch eine [SharePoint-Websitesammlung](https://docs.microsoft.com/microsoftteams/sharepoint-onedrive-interact) bereitgestellt, um Datei- und Datenspeicherung für dieses Team zu unterstützen. Ihre App kann und sollte dieses Feature nutzen, wenn sie mit Dateien interagiert. Sie können die Websitesammlung auch verwenden, um Rohdaten in SharePoint-Listen und Excel zu speichern.
