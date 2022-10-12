---
title: Erweitern Sie Teams-Apps auf Microsoft 365 (Vorschau)
description: Erfahren Sie, wie Sie Teams-Apps auf Microsoft 365 erweitern (die in Teams, Outlook und Office als Anwendungshosts ausgeführt werden).
ms.date: 10/10/2022
ms.topic: Conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 4c05fbe0c763d9b650573e33edfa5e332aaba90d
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537539"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Erweitern von Teams-Apps auf Microsoft 365

Mit den neuesten Versionen des [JavaScript-Client-SDK für Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) (Version 2.0.0 und höher), dem [Teams-App-Manifest](../resources/schema/manifest-schema.md) (Version 1.13 und höher) und dem [Teams-Toolkit](../toolkit/visual-studio-code-overview.md) können Sie Teams-Apps so erstellen und aktualisieren, dass sie in anderen microsoft 365-Produkten mit hoher Nutzung ausgeführt werden, und sie im kommerziellen Microsoft Marketplace ([Microsoft AppSource](https://appsource.microsoft.com/)) oder im privaten App Store Ihrer Organisation veröffentlichen.

Die Erweiterung Ihrer Teams-App auf Microsoft 365 bietet eine optimierte Möglichkeit, plattformübergreifende Apps für eine erweiterte Benutzergruppe bereitzustellen: Aus einer einzigen Codebasis können Sie App-Umgebungen erstellen, die auf Teams-, Outlook- und Office-Umgebungen zugeschnitten sind. Endbenutzer müssen den Kontext ihrer Arbeit nicht verlassen, um Ihre App verwenden zu können, und Administratoren profitieren von einem konsolidierten Verwaltungs- und Bereitstellungsworkflow.

Die Teams-App-Plattform entwickelt sich weiter und erweitert sich ganzheitlich in das Microsoft 365-Ökosystem. Hier ist die aktuelle Unterstützung von Teams-App-Plattformelementen in Microsoft 365 (Teams, Outlook und Office als Anwendungshosts):

| Features der Teams-App| App-Manifestelement | Teams-Support |Outlook*-Unterstützung | Office*-Support | Notizen |
|--|--|--|--|--|--|
| [**Persönlicher Bereich "Registerkarten**](../tabs/what-are-tabs.md) "    |`staticTabs`  | Web, Desktop, Mobile | Web (Targeted Release), Desktop (Betakanal) | Web (Targeted Release), Desktop (Betakanal), Mobile (Android)| Kanal- und Gruppenbereich werden für Microsoft 365 noch nicht unterstützt. Siehe [Notizen](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Nachrichtenerweiterungen**](../messaging-extensions/what-are-messaging-extensions.md) suchbasiert| `composeExtensions` | Web, Desktop, Mobile| Web (Targeted Release), Desktop (Betakanal)| - |Aktionsbasiert wird für Microsoft 365 noch nicht unterstützt. Siehe [Notizen](extend-m365-teams-message-extension.md#troubleshooting). |
| Verbreiten von Links | `composeExtensions.messageHandlers` | Web, Desktop | Web (Targeted Release), Desktop (Betakanal) | - | Notizen [anzeigen](extend-m365-teams-message-extension.md#link-unfurling) |
| [**Office-Add-Ins**](/office/dev/add-ins/develop/json-manifest-overview) (Vorschau) | `extensions` | - | Web, Desktop | - | Nur in [devPreview-Manifestversion](../resources/schema/manifest-schema-dev-preview.md) verfügbar. Siehe [Notizen](#office-add-ins-preview).|

\*Die [Microsoft 365 Targeted Release-Option](/microsoft-365/admin/manage/release-options-in-office-365) und [Microsoft 365 Apps Updatekanalregistrierung](/deployoffice/change-update-channels) erfordern die Administratoranmeldung für die gesamte Organisation oder ausgewählte Benutzer. Updatekanäle sind gerätespezifisch und gelten nur für Installationen von Office unter Windows.

Eine Anleitung zum Microsoft Teams-App-Manifest und zur SDK-Versionsverwaltung sowie weitere Details zur aktuellen Unterstützung von Teams-Plattformfunktionen in Microsoft 365 finden Sie in der [Übersicht über das JavaScript-Client-SDK für Teams](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> Wir freuen uns über Ihr Feedback und Ihre Problemberichterstattung, während Sie Teams-Apps erweitern, um über das Microsoft 365-Ökosystem hinweg ausgeführt zu werden! Verwenden Sie die regulären [Microsoft Teams-Entwicklercommunitykanäle](/microsoftteams/platform/feedback) , um Feedback zu senden.

## <a name="personal-tabs-and-messaging-extensions-in-outlook-and-office"></a>Persönliche Registerkarten und Messaging-Erweiterungen in Outlook und Office

Erreichen Sie Ihre Benutzer direkt im Kontext ihrer Arbeit, indem Sie Ihre Web-App als [persönliche Registerkartenanwendung für Teams](extend-m365-teams-personal-tab.md) erweitern, die auch in Outlook und Office ausgeführt wird.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Der Screenshot ist ein Beispiel für die Registerkarte &quot;Persönlich&quot;, die in Outlook, Office und Teams ausgeführt wird.":::

Auf mobilgeräten können Sie Ihre persönliche Teams-Registerkarte testen und debuggen, die in [der Office-App für Android](extend-m365-teams-personal-tab.md#office-app-for-android) ausgeführt wird.

:::image type="content" source="images/office-mobile-personal-tab.png" alt-text="Der Screenshot ist ein Beispiel für die persönliche Registerkarte, die in Office ausgeführt wird.":::

Sie können Ihre suchbasierten [Teams-Nachrichtenerweiterungen](extend-m365-teams-message-extension.md) auch auf Outlook im Web und Windows-Desktop erweitern, sodass Ihre Kunden neben Microsoft Teams-Clients auch Ergebnisse über den Nachrichtenbereich zum Verfassen von Outlook durchsuchen und freigeben können.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Der Screenshot ist ein Beispiel für die Nachrichtenerweiterung, die in Outlook und Teams ausgeführt wird.":::

[Die Verbreitung von Links](extend-m365-teams-message-extension.md#link-unfurling)  funktioniert in Outlook-Web- und Windows-Umgebungen genauso wie in Microsoft Teams, ohne dass weitere Arbeit erforderlich ist, als die Verwendung von Teams-App-Manifestversion 1.13 oder höher.

:::image type="content" source="images/outlook-teams-link-unfurling.png" alt-text="Der Screenshot ist ein Beispiel, in dem die Verbreitung von Links in Outlook und Teams angezeigt wird.":::

Erstellen Sie Ihre App mit dem neuesten [Teams-App-Manifest](../resources/schema/manifest-schema.md) und dem [JavaScript-Client-SDK für Teams](../tabs/how-to/using-teams-client-sdk.md) , um den neuesten konsolidierten Microsoft 365-App-Entwicklungsprozess zu nutzen. Stellen Sie dann eine optimierte Bereitstellungs-, Installations- und Administratorerfahrung für Ihre Kunden zur Erweiterung der Reichweite und Nutzung Ihrer App zur Folge.

## <a name="use-teams-app-manifest-across-microsoft-365"></a>Verwenden des Teams-App-Manifests in Microsoft 365

Mit dem Ziel, das Microsoft 365-Entwicklerökosystem zu vereinfachen und zu optimieren, erweitern wir das Teams-App-Manifest in weitere Bereiche von Microsoft 365 mit den folgenden Themen.

### <a name="office-add-ins-preview"></a>Office-Add-Ins (Vorschau)

Sie können jetzt Office-Add-Ins in der [Entwicklervorschauversion](../resources/schema/manifest-schema-dev-preview.md) des Microsoft Teams-App-Manifests definieren und bereitstellen. Derzeit ist diese Vorschau auf Outlook-Add-Ins beschränkt, die im Abonnement von Office für Windows ausgeführt werden.

Weitere Informationen finden Sie unter [Teams-Manifest für Office-Add-Ins (Vorschau)](/office/dev/add-ins/develop/json-manifest-overview).

## <a name="microsoft-commercial-marketplace-submission"></a>Übermittlung an den kommerziellen Microsoft Marketplace

Treten Sie der wachsenden Anzahl von Teams-Produktions-Apps im [Microsoft Commercial Marketplace](https://appsource.microsoft.com/) (Microsoft AppSource)-Store mit erweiterter Unterstützung für Outlook- und Office Preview -Zielgruppen (Targeted Release) bei. Der [App-Übermittlungsprozess für Teams-Apps, die für Outlook und Office aktiviert sind](../concepts/deploy-and-publish/appsource/publish.md) , ist der gleiche wie bei herkömmlichen Teams-Apps. Der einzige Unterschied besteht darin, dass Sie die Version [1.13](../tabs/how-to/using-teams-client-sdk.md) des Teams-App-Manifests in Ihrem App-Paket verwenden, wodurch Unterstützung für Teams-Apps eingeführt wird, die in Microsoft 365 ausgeführt werden.

Nach der Veröffentlichung als Microsoft 365-fähige Teams-App kann Ihre App zusätzlich zum Teams Store als installierbare App aus den Outlook- und Office-App-Stores ermittelt werden. Bei der Ausführung in Outlook und Office verwendet Ihre App die gleichen Berechtigungen, die in Teams erteilt wurden. Teams-Administratoren können [den Zugriff auf Teams-Apps in Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) für Benutzer in ihrer Organisation verwalten.

Weitere Informationen finden [Sie unter Veröffentlichen von Teams-Apps für Microsoft 365](publish.md).

## <a name="next-step"></a>Nächster Schritt

Richten Sie Ihre Entwicklungsumgebung ein, um Teams-Apps für Microsoft 365 zu erstellen:

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)
