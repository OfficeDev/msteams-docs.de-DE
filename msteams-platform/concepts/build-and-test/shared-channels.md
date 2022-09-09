---
title: Teams Connect freigegebener Kanäle
author: Rajeshwari-v
description: Erfahren Sie mehr über Teams Connect freigegebenen Kanäle für die sichere Zusammenarbeit mit internen und externen Benutzern in einem freigegebenen Raum, ohne mandantenwechseln zu müssen.
ms.author: surbhigupta
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: f063be5bce83484a259e67e94f4caa73ef8afa76
ms.sourcegitcommit: bd30d33af59dd870a309ae72b4c4496c9c1f920d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2022
ms.locfileid: "67635315"
---
# <a name="microsoft-teams-connect-shared-channels"></a>Microsoft Teams Connect freigegebener Kanäle

Microsoft Teams Connect freigegebenen Kanälen ermöglichen Mitgliedern eines Kanals die Zusammenarbeit mit Benutzern in anderen Teams und Organisationen. Sie können einen freigegebenen Kanal erstellen und freigeben mit:

* Mitglieder eines anderen Teams innerhalb derselben Organisation.
* Personen innerhalb derselben Organisation.
* Einzelpersonen und andere Teams anderer Organisationen.

Teams Connect freigegebenen Kanäle ermöglichen eine nahtlose sichere Zusammenarbeit. Ermöglichen Sie externen Benutzern außerhalb Ihrer Organisation die Zusammenarbeit mit internen Benutzern in Teams, ohne ihren Benutzerkontext zu ändern. Verbessern Sie die Benutzerfreundlichkeit im Gegensatz zur Verwendung von Gastkonten, z. B. müssen sich die Mitglieder von Teams abmelden und sich erneut mit einem Gastkonto anmelden. Teams-Anwendungen erweitern den leistungsstarken Platz für die Zusammenarbeit.

:::image type="content" source="~/assets/images/app-fundamentals/shared-channels-teams.png" alt-text="Diagramm, das Team B aus Organisation A und Team C aus Organisation B zeigt, das in einem freigegebenen Kanal als Team A zusammenarbeitet." border="true" :::

## <a name="enable-your-app-for-shared-channels"></a>Aktivieren Ihrer App für freigegebene Kanäle

SupportedChannelTypes ist eine optionale Eigenschaft, die Ihre App in nicht standardmäßigen Kanälen ermöglicht. Wenn Ihre App den Teambereich unterstützt und die Eigenschaft definiert ist, aktiviert Teams Ihre App in jedem Kanaltyp entsprechend. Private und freigegebene Kanäle werden derzeit unterstützt. Weitere Informationen finden Sie unter [supportedChannelTypes](../../resources/schema/manifest-schema.md#supportedchanneltypes).

```JSON
"supportedChannelTypes": {
      "type": "array",
      "description": "List of ‘non-standard’ channel types that the app supports. Note: Channels of standard type are supported by default if the app supports team scope. ",
      "maxItems": 2,
      "items": { 
        "enum": [
          "sharedChannels",
          "privateChannels"
        ]
      }
    }
```

> [!NOTE]
>
> * Wenn Ihre App den Teambereich unterstützt, funktioniert sie in Standardkanälen, unabhängig davon, welche Werte in dieser Eigenschaft definiert sind.
> * Ihre App muss möglicherweise die eindeutigen Eigenschaften der einzelnen Kanaltypen berücksichtigen, um ordnungsgemäß funktionieren zu können.

## <a name="get-context-for-shared-channels"></a>Abrufen des Kontexts für freigegebene Kanäle

Wenn die Inhalts-UX in einen freigegebenen Kanal geladen wird, verwenden Sie die vom `getContext` Aufruf empfangenen Daten für Änderungen des freigegebenen Kanals. `getContext` aufruf veröffentlicht zwei neue Eigenschaften und `hostTeamGroupID` `hostTenantID`, die zum Abrufen der Kanalmitgliedschaft mithilfe von Microsoft Graph-APIs verwendet werden. `hostTeam` ist das Team, das den freigegebenen Kanal erstellt.

Weitere Informationen zum Aktivieren Ihrer Registerkarte finden Sie unter:

* [Abrufen des Kontexts für Ihre Registerkarte für private Kanäle](../../tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels)
* [Abrufen von Kontext in freigegebenen Kanälen](../../tabs/how-to/access-teams-context.md#get-context-in-shared-channels)

## <a name="apps-and-permissions-in-shared-channels"></a>Apps und Berechtigungen in freigegebenen Kanälen

Sie können mit externen Mitgliedern außerhalb Ihrer Organisation über freigegebene Kanäle zusammenarbeiten. App-Berechtigungen in freigegebenen Kanälen folgen der App-Liste des Hostteams und der App-Richtlinie des Hostmandanten.

> [!NOTE]
> Die [Aktivitätsfeedbenachrichtigungs-API](/graph/teams-send-activityfeednotifications) unterstützt keine mandantenübergreifenden Benachrichtigungen für Apps in einem freigegebenen Kanal.

## <a name="get-shared-channel-membership"></a>Abrufen der Mitgliedschaft im freigegebenen Kanal

Sie können eine direkte Mitgliedschaft im freigegebenen Kanal erhalten, indem Sie die `hostTeamGroupID` `getContext` folgenden Schritte ausführen:

1. Rufen Sie direkte Mitglieder mit der [API für GET-Kanalmitglieder ab](/graph/api/channel-list-members?view=graph-rest-beta&tabs=http&preserve-view=true) .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/members
    ```

2. Rufen Sie jedes freigegebene Team mit der GET-API ab `sharedWithTeams` .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/sharedWithTeams
    ```

3. Verwenden Sie GET-Mitglieder jedes freigegebenen Teams (Team X) mit der GET-API `sharedWithTeams` .

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/sharedWithTeams/{teamX}/members
    ```

## <a name="classify-members-in-the-shared-channel-as-in-tenant-or-out-tenant"></a>Klassifizieren von Mitgliedern im freigegebenen Kanal als In-Tenant oder Out-Tenant

Sie können Mitglieder als In-Tenant oder Out-Tenant klassifizieren, indem Sie das Mitglied oder Team wie `hostTeamTenantID` folgt vergleichen`tenantID`:

1. Rufen Sie das Mitglied ab, das Sie vergleichen möchten.

    ```http
    GET /teams/{host-team-group-id}/channels/{channel-id}/members
    ```

2. Verwenden Sie `getContext`, vergleichen Sie das `tenantID` Element mit der `hostTenantID` Eigenschaft.

## <a name="azure-ad-native-identity"></a>Native Azure AD-Identität

Apps müssen mandantenübergreifend in Installation und Nutzung funktionieren. In der folgenden Tabelle sind die Kanaltypen und die entsprechenden Gruppen-IDs aufgeführt:

|Kanaltyp| groupId | hostTeamGroupId |
|----------|---------|-----------------|
|Regular | Azure AD-Teamgruppen-ID | Azure AD-Teamgruppen-ID |
|Shared | Empty | Azure AD-Gruppen-ID des Hostteams |

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](../../tabs/what-are-tabs.md)
* [App-Manifestschema für Teams](../../resources/schema/manifest-schema.md)
* [Freigegebene Kanäle in Microsoft Teams](/MicrosoftTeams/shared-channels)
* [Aufbewahrungsrichtlinie für Teams-Speicherorte](/microsoft-365/compliance/create-retention-policies)
