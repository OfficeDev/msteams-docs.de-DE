---
title: Erweitern Sie Teams-Apps auf Microsoft 365 (Vorschau)
description: Erweitern Sie Ihre Teams-App-Erfahrungen auf andere häufig genutzte Bereiche von Microsoft 365
ms.date: 05/24/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: ac7b82d4a0c984f1db94c770be28d0bcda71c8e6
ms.sourcegitcommit: 1e77573e47fad51a19545949fdac1241b13052e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2022
ms.locfileid: "65656093"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Erweitern von Teams-Apps auf Microsoft 365

Mit den neuesten Versionen von [Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) (Version 2.0.0), [Teams App-Manifest](../resources/schema/manifest-schema.md) (Version 1.13) und [Teams Toolkit](../toolkit/visual-studio-code-overview.md) können Sie Teams Apps erstellen und aktualisieren, um sie in anderen besonders auslastungsstark genutzten Microsoft 365 Produkten auszuführen und auf dem kommerziellen Microsoft Marketplace zu veröffentlichen ([ Microsoft AppSource](https://appsource.microsoft.com/)).

Die Erweiterung Ihrer Teams-App über Microsoft 365 hinweg bietet eine optimierte Möglichkeit, plattformübergreifende Apps für eine erweiterte Benutzergruppe bereitzustellen: Aus einer einzigen Codebasis können Sie App-Umgebungen erstellen, die auf Teams, Outlook und Office Umgebungen zugeschnitten sind. Endbenutzer müssen den Kontext ihrer Arbeit nicht verlassen, um Ihre App verwenden zu können, und Administratoren profitieren von einem konsolidierten Verwaltungs- und Bereitstellungsworkflow.

Die Teams App-Plattform entwickelt sich weiter und erweitert sich ganzheitlich in das Microsoft 365 Ökosystem. Hier ist die aktuelle Unterstützung von Teams App-Plattformelementen in Microsoft 365 (Teams, Outlook und Office als Anwendungshosts):

|          | App-Manifestelement | Teams-Unterstützung |Outlook* Support | Office* Support | Hinweise |
|--|--|--|--|--|--|
| [**Registerkarten**](../tabs/what-are-tabs.md) (persönlicher Bereich)    |`staticTabs`  | Web, Desktop, Mobile | Web (Targeted Release), Desktop (Betakanal) | Web (Targeted Release)| Kanal- und Gruppenbereich werden für Microsoft 365 noch nicht unterstützt. Siehe [Notizen](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Nachrichtenerweiterungen**](../messaging-extensions/what-are-messaging-extensions.md) (suchbasiert)| `composeExtensions` | Web, Desktop, Mobile| Web (Targeted Release), Desktop (Betakanal)| |Aktionsbasiert wird für Microsoft 365 noch nicht unterstützt. Siehe [Notizen](extend-m365-teams-message-extension.md#preview-your-message-extension-in-outlook). |
| [**Graph Connectors**](/microsoftsearch/connectors-overview)| `graphConnector` | Web, Desktop, Mobile| Web, Desktop | Netz| Notizen [anzeigen](#graph-connectors)
| [**Office-Add-Ins**](/office/dev/add-ins/develop/json-manifest-overview) (Vorschau) | `extensions` | | Web, Desktop  | | Nur in [devPreview-Manifestversion](../resources/schema/manifest-schema-dev-preview.md) verfügbar. Siehe [Notizen](#office-add-ins-preview).|

\*Die [Option Microsoft 365 Targeted Release](/microsoft-365/admin/manage/release-options-in-office-365) und [Microsoft 365 Apps Updatekanalregistrierung](/deployoffice/change-update-channels) erfordern die Administratoranmeldung für die gesamte Organisation oder ausgewählte Benutzer.

Eine Anleitung zur Teams App-Manifest- und SDK-Versionsverwaltung sowie weitere Details zur aktuellen unterstützung von Teams Plattformfunktionen in Microsoft 365 finden Sie in der [Teams JavaScript-Client-SDK-Übersicht](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Wir freuen uns über Ihr Feedback und Ihre Problemberichterstattung, während Sie Teams Apps erweitern, um über das Microsoft 365 Ökosystem hinweg ausgeführt zu werden! Bitte verwenden Sie die regulären [Microsoft Teams-Communitykanäle für Entwickler](/microsoftteams/platform/feedback), um Feedback zu senden.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Persönliche Registerkarten und Messaging-Erweiterungen in Outlook und Office

Erreichen Sie Ihre Benutzer direkt im Kontext ihrer Arbeit, indem Sie Ihre Web-App als Teams persönliche Registerkartenanwendung erweitern, die auch in Outlook und Office ausgeführt wird.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Persönliche Registerkarte, die in Outlook, Office und Teams ausgeführt wird":::

Sie können Ihre suchbasierten Teams-Nachrichtenerweiterungen auch auf Outlook im Web und Windows Desktop erweitern, sodass Ihre Kunden ergebnisse über den Nachrichtenbereich zum Verfassen von Outlook sowie über Microsoft Teams Clients durchsuchen und freigeben können.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Nachrichtenerweiterung, die in Outlook und Teams ausgeführt wird":::

Wenn Sie Ihre App mit dem neuesten [Teams App-Manifest](../resources/schema/manifest-schema.md) und [Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) erstellen, erhalten Sie einen konsolidierten Entwicklungsprozess. Durch die Bereitstellung einer optimierten Bereitstellungs-, Installations- und Administratorumgebung für Ihre Kunden können Sie die potenzielle Reichweite und Nutzung Ihrer App erweitern.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Verwenden Teams App-Manifests in Microsoft 365

Mit dem Ziel, das Microsoft 365 Entwicklerökosystem zu vereinfachen und zu optimieren, erweitern wir das Teams-App-Manifest in weitere Bereiche von Microsoft 365 mit den folgenden Themen.

### <a name="graph-connectors"></a>Graph Connectors

Mit Microsoft Graph Connectors kann Ihre Organisation Drittanbieterdaten indizieren, sodass sie als Microsoft Search Ergebnisse angezeigt werden, wodurch die Typen durchsuchbarer Inhaltsquellen in Ihren Teams-Apps erweitert werden.
Weitere Informationen finden Sie [in der Übersicht über Microsoft Graph Connectors für Microsoft Search](/microsoftsearch/connectors-overview).

Informationen zu den ersten Schritte mit Graph-Connectors in Teams Apps finden Sie im [Beispiel Teams Toolkit Graph Connectors](https://aka.ms/teamsfx-graph-connector-sample) und Microsoft Teams Schemareferenz für [das Entwicklervorschaumanifest](../resources/schema/manifest-schema-dev-preview.md).

### <a name="office-add-ins-preview"></a>Office-Add-Ins (Vorschau)

Sie können jetzt Office Add-Ins in der [Entwicklervorschauversion](../resources/schema/manifest-schema-dev-preview.md) des Microsoft Teams App-Manifests definieren und bereitstellen. Derzeit ist diese Vorschau auf Outlook Add-Ins beschränkt, die im Abonnement Office für Windows ausgeführt werden.

Weitere Informationen finden Sie [unter Teams Manifest für Office-Add-Ins (Vorschau).For more information, see Teams manifest for Office Add-ins (preview)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-appsource-submission"></a>Microsoft AppSource-Übermittlung

Nehmen Sie an der wachsenden Anzahl von Produktions-Teams-Apps im [Microsoft AppSource](https://appsource.microsoft.com/) Store teil, mit erweiterter Unterstützung für Outlook- und Office Preview(Targeted Release)-Zielgruppen. Der [App-Übermittlungsprozess für Teams apps enabled for Outlook and Office](../concepts/deploy-and-publish/appsource/publish.md) is the same as for traditional Teams apps; the only difference is you'll use Teams app manifest [version 1.13](../tabs/how-to/using-teams-client-sdk.md) in your app package, which introduces support for Teams apps that run across Microsoft 365.

Nach der Veröffentlichung als Microsoft 365-aktivierte Teams-App kann Ihre App zusätzlich zum Teams Store als installierbare App aus dem Outlook- und Office-App Store ermittelt werden. Bei der Ausführung in Outlook und Office verwendet Ihre App dieselben Berechtigungen, die in Teams erteilt wurden. Teams Administratoren können den [Zugriff auf Teams Apps Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) für Benutzer in ihrer Organisation verwalten.

Weitere Informationen finden Sie unter [Veröffentlichen Teams Apps für Microsoft 365](publish.md)

## <a name="next-step"></a>Nächster Schritt

Richten Sie Ihre Entwicklungsumgebung ein, um Teams Apps für Microsoft 365 zu erstellen:

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)
