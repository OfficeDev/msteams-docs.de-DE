---
title: Erweitern Sie Teams-Apps auf Microsoft 365 (Vorschau)
description: Erfahren Sie, wie Sie Teams-Apps auf Microsoft 365 (ausgeführt in Teams, Outlook und Office als Anwendungshosts) erweitern.
ms.date: 10/10/2022
ms.topic: Conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 91586eefe21836118ed2f0a0071070ac2034bf76
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789877"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Erweitern von Teams-Apps auf Microsoft 365

Mit den neuesten Versionen des [Microsoft Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) (Version 2.0.0 und höher), [des Teams App-Manifests](../resources/schema/manifest-schema.md) (Version 1.13 und höher) und des [Teams Toolkits](../toolkit/visual-studio-code-overview.md) können Sie Teams-Apps erstellen und aktualisieren, um sie in anderen microsoft 365-Produkten mit hoher Nutzung auszuführen, und sie im kommerziellen Microsoft-Marketplace ([Microsoft AppSource](https://appsource.microsoft.com/)) oder im privaten App Store Ihrer Organisation veröffentlichen.

Die Erweiterung Ihrer Teams-App auf Microsoft 365 bietet eine optimierte Möglichkeit, plattformübergreifende Apps für eine erweiterte Benutzergruppe bereitzustellen: Aus einer einzigen Codebasis können Sie App-Umgebungen erstellen, die auf Teams-, Outlook- und Office-Umgebungen zugeschnitten sind. Endbenutzer müssen den Kontext ihrer Arbeit nicht verlassen, um Ihre App zu verwenden, und Administratoren profitieren von einem konsolidierten Verwaltungs- und Bereitstellungsworkflow.

Die Teams-App-Plattform entwickelt sich weiter und erweitert sich ganzheitlich in das Microsoft 365-Ökosystem. Hier sehen Sie die aktuelle Unterstützung von Teams-App-Plattformelementen in Microsoft 365 (Teams, Outlook und Office als Anwendungshosts):

| Features der Teams-App| App-Manifestelement | Teams-Support |Outlook*-Unterstützung | Office*-Support | Notizen |
|--|--|--|--|--|--|
| [**Persönlicher Bereich für Registerkarten**](../tabs/what-are-tabs.md)    |`staticTabs`  | Web, Desktop, Mobil | Web (Gezieltes Release), Desktop (Betakanal) | Web (Gezieltes Release), Desktop (Betakanal), Mobil (Android)| Kanal- und Gruppenbereich wird für Microsoft 365 noch nicht unterstützt. Siehe [Hinweise](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Suche nach Nachrichtenerweiterungen**](../messaging-extensions/what-are-messaging-extensions.md)| `composeExtensions` | Web, Desktop, Mobil| Web (Gezieltes Release), Desktop (Betakanal)| - |Aktionsbasiert wird für Microsoft 365 noch nicht unterstützt. Siehe [Hinweise](extend-m365-teams-message-extension.md#troubleshooting). |
| Verbreiten von Links | `composeExtensions.messageHandlers` | Web, Desktop | Web (Gezieltes Release), Desktop (Betakanal) | - | [Hinweise](extend-m365-teams-message-extension.md#link-unfurling) anzeigen |
| [**Office-Add-Ins**](/office/dev/add-ins/develop/json-manifest-overview) (Vorschau) | `extensions` | - | Web, Desktop | - | Nur in [der devPreview-Manifestversion](../resources/schema/manifest-schema-dev-preview.md) verfügbar. Siehe [Hinweise](#office-add-ins-preview).|

\*Die Microsoft [365 Targeted Release-Option](/microsoft-365/admin/manage/release-options-in-office-365) und [Microsoft 365 Apps Registrierung des Updatekanals](/deployoffice/change-update-channels) erfordern die Administratoranmeldung für die gesamte Organisation oder ausgewählte Benutzer. Updatekanäle sind gerätespezifisch und gelten nur für Installationen von Office unter Windows.

Anleitungen zum Teams-App-Manifest und zum SDK-Versionsverwaltungsleitfaden sowie weitere Details zur unterstützung der aktuellen Teams-Plattformfunktionen in Microsoft 365 finden Sie in der [Übersicht über das Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Wir freuen uns über Ihr Feedback und Ihre Problemberichterstattung, während Sie Teams-Apps so erweitern, dass sie im gesamten Microsoft 365-Ökosystem ausgeführt werden! Verwenden Sie die [regulären Microsoft Teams-Entwicklercommunity-Kanäle](/microsoftteams/platform/feedback) , um Feedback zu senden.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Persönliche Registerkarten und Messaging-Erweiterungen in Outlook und Office

Erreichen Sie Ihre Benutzer dort, wo sie gerade im Kontext ihrer Arbeit sind, indem Sie Ihre Web-App als [persönliche Teams-Registerkartenanwendung](extend-m365-teams-personal-tab.md) erweitern, die auch in Outlook und Office ausgeführt wird.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Der Screenshot ist ein Beispiel, das die Registerkarte &quot;Persönlich&quot; zeigt, die in Outlook, Office und Teams ausgeführt wird.":::

Auf Mobilgeräten können Sie Ihre persönliche Teams-Registerkarte testen und debuggen, die in der [Office-App für Android](extend-m365-teams-personal-tab.md#office-app-for-android) ausgeführt wird.

:::image type="content" source="images/office-mobile-personal-tab.png" alt-text="Der Screenshot ist ein Beispiel, das die persönliche Registerkarte zeigt, die in Office ausgeführt wird.":::

Sie können Ihre [suchbasierten Teams-Nachrichtenerweiterungen](extend-m365-teams-message-extension.md) auch auf Outlook im Web und Windows-Desktop erweitern, sodass Ihre Kunden neben Microsoft Teams-Clients auch über den Nachrichtenerstellungsbereich von Outlook suchen und Ergebnisse freigeben können.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Der Screenshot ist ein Beispiel, das die Nachrichtenerweiterung zeigt, die in Outlook und Teams ausgeführt wird.":::

[Das Entpacken von Links](extend-m365-teams-message-extension.md#link-unfurling)  funktioniert in Outlook-Web- und Windows-Umgebungen genauso wie in Microsoft Teams ohne weitere Arbeit als die Verwendung von Teams-App-Manifestversion 1.13 oder höher.

:::image type="content" source="images/outlook-teams-link-unfurling.png" alt-text="Der Screenshot ist ein Beispiel, das zeigt, wie link unfurling in Outlook und Teams ausgeführt wird.":::

Erstellen Sie Ihre App mit dem neuesten [Teams-App-Manifest](../resources/schema/manifest-schema.md) und [dem Teams JavaScript-Client-SDK](../tabs/how-to/using-teams-client-sdk.md) , um den neuesten konsolidierten Microsoft 365-App-Entwicklungsprozess zu nutzen. Stellen Sie dann eine optimierte Bereitstellung, Installation und Administratorerfahrung für Ihre Kunden bereit, die die Reichweite und Nutzung Ihrer App erweitert.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Verwenden des Teams-App-Manifests in Microsoft 365

Mit dem Ziel, das Microsoft 365-Entwicklerökosystem zu vereinfachen und zu optimieren, erweitern wir das Teams-App-Manifest mit folgenden Schritten weiter auf andere Bereiche von Microsoft 365.

### <a name="office-add-ins-preview"></a>Office-Add-Ins (Vorschau)

Sie können office-Add-Ins jetzt in der [Entwicklervorschauversion](../resources/schema/manifest-schema-dev-preview.md) des Microsoft Teams-App-Manifests definieren und bereitstellen. Derzeit ist diese Vorschau auf Outlook-Add-Ins beschränkt, die im Abonnement Office für Windows ausgeführt werden.

Weitere Informationen finden Sie unter [Teams-Manifest für Office-Add-Ins (Vorschau)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-commercial-marketplace-submission"></a>Übermittlung im kommerziellen Microsoft-Marketplace

Treten Sie der wachsenden Anzahl von Produktions-Teams-Apps im [Microsoft Commercial Marketplace](https://appsource.microsoft.com/) (Microsoft AppSource) store mit erweiterter Unterstützung für Outlook- und Office-Vorschaugruppen (Targeted Release) bei. Der [App-Übermittlungsprozess für Teams-Apps, die für Outlook und Office aktiviert](../concepts/deploy-and-publish/appsource/publish.md) sind, ist derselbe wie bei herkömmlichen Teams-Apps. Der einzige Unterschied besteht darin, dass Sie version [1.13](../tabs/how-to/using-teams-client-sdk.md) des Teams-App-Manifests in Ihrem App-Paket verwenden, wodurch Unterstützung für Teams-Apps eingeführt wird, die in Microsoft 365 ausgeführt werden.

Nachdem Ihre App als Microsoft 365-fähige Teams-App veröffentlicht wurde, ist Ihre App zusätzlich zum Teams Store als installierbare App in den Outlook- und Office-App-Stores erkennbar. Bei der Ausführung in Outlook und Office verwendet Ihre App die gleichen Berechtigungen, die in Teams gewährt wurden. Teams-Administratoren können [den Zugriff auf Teams-Apps in Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) für Benutzer in ihrer Organisation verwalten.

Weitere Informationen finden Sie unter [Veröffentlichen von Teams-Apps für Microsoft 365](publish.md).

## <a name="next-step"></a>Nächster Schritt

Richten Sie Ihre Entwicklungsumgebung ein, um Teams-Apps für Microsoft 365 zu erstellen:

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)
