---
title: Registrieren von Anrufen und Besprechungsbots für Microsoft Teams
description: Erfahren Sie, wie Sie einen neuen Audio-/Videoanrufbot für Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Aufrufen von Bot-Audio-/Video-Audiovideomedien
ms.openlocfilehash: 5013ebcbce0bc94199e846f20fc6ee52238d302f1dd1b05872245ef2c6e32d91
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57709569"
---
# <a name="register-calls-and-meetings-bot-for-microsoft-teams"></a>Registrieren von Anrufen und Besprechungsbots für Microsoft Teams

Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt, ist ein regulärer Microsoft Teams Bot mit den folgenden zusätzlichen Features, die zum Registrieren des Bots verwendet werden:

* Es gibt eine neue Version des Teams-App-Manifests mit zwei zusätzlichen Einstellungen `supportsCalling` und `supportsVideo` . Diese Einstellungen sind in der [Entwicklervorschauversion](../../resources/dev-preview/developer-preview-intro.md) des Teams-App-Manifests enthalten.
* [Microsoft Graph Berechtigungen](./registering-calling-bot.md#add-graph-permissions) müssen für die Microsoft App-ID Ihres Bots konfiguriert werden.
* Die APIs für Graph Anrufe und Onlinebesprechungen erfordern die Zustimmung des Mandantenadministrators.

## <a name="new-manifest-settings"></a>Neue Manifesteinstellungen

Bots für Anrufe und Onlinebesprechungen verfügen über die folgenden zwei zusätzlichen Einstellungen im manifest.js, die Audio- oder Videofunktionen für Ihren Bot in Teams aktivieren.

* `bots[0].supportsCalling`. Wenn vorhanden und `true` festgelegt, ermöglicht Teams Ihrem Bot die Teilnahme an Anrufen und Onlinebesprechungen.
* `bots[0].supportsVideo`. Wenn vorhanden und festgelegt `true` auf , weiß Teams, dass Ihr Bot Video unterstützt.

Wenn Ihre IDE die manifest.jsim Schema für Ihre Anrufe und Besprechungsbots ordnungsgemäß auf diese Werte überprüfen soll, können Sie das `$schema` Attribut wie folgt ändern:

```json
"$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
```

Im nächsten Abschnitt können Sie einen neuen Bot erstellen oder Ihrem vorhandenen Bot Anruffunktionen hinzufügen.

## <a name="create-new-bot-or-add-calling-capabilities"></a>Erstellen eines neuen Bots oder Hinzufügen von Anruffunktionen

Informationen zum Erstellen von Bots finden Sie unter [Erstellen eines Bots für Teams](../how-to/create-a-bot-for-teams.md).

**So erstellen Sie einen neuen Bot für Teams**

1. Verwenden Sie diesen Link, um einen neuen Bot zu `https://dev.botframework.com/bots/new` erstellen. Wenn Sie alternativ die Schaltfläche **"Bot** erstellen" im Bot Framework-Portal auswählen, erstellen Sie Ihren Bot in Microsoft Azure, für die Sie über ein Azure-Konto verfügen müssen.
1. Fügen Sie den Teams Kanal hinzu.
1. Wählen Sie die Registerkarte **"Anrufe"** auf der Teams Kanalseite aus. Wählen Sie **"Anruf aktivieren"** aus, und aktualisieren Sie dann **Webhook (für Anrufe)** mit Ihrer HTTPS-URL, unter der Sie eingehende Benachrichtigungen erhalten, z. `https://contoso.com/teamsapp/api/calling` B. . Weitere Informationen finden Sie unter [Konfigurieren von Kanälen.](/bot-framework/portal-configure-channels)

    ![Konfigurieren Teams Kanalinformationen](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

Der nächste Abschnitt enthält eine Liste der Anwendungsberechtigungen, die für Anrufe und Onlinebesprechungen unterstützt werden.

## <a name="add-graph-permissions"></a>Hinzufügen Graph Berechtigungen

Die Graph bietet präzise Berechtigungen, um den Zugriff zu steuern, den Apps auf Ressourcen haben. Sie entscheiden, welche Berechtigungen für Graph Ihre App-Anforderungen gelten. Die Graph aufrufenden APIs unterstützen Anwendungsberechtigungen, die von Apps verwendet werden, die ohne angemeldeten Benutzer ausgeführt werden. Ein Mandantenadministrator muss Anwendungsberechtigungen zustimmen.

### <a name="application-permissions-for-calls"></a>Anwendungsberechtigungen für Anrufe

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Aufrufe:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| Calls.Initiate.All |Ausgehende 1:1-Anrufe aus der App-Vorschau initiieren. |Ermöglicht der App, ausgehende Anrufe an einen einzelnen Benutzer zu tätigen und Anrufe an Benutzer im Organisationsverzeichnis zu übertragen (ohne angemeldeten Benutzer).|Ja|
| Calls.InitiateGroupCall.All |Ausgehende Gruppenanrufe aus der App-Vorschau initiieren. |Ermöglicht der App, ausgehende Anrufe an mehrere Benutzer zu tätigen und Teilnehmer in Ihrer Organisation zu Besprechungen hinzufügen (ohne angemeldeten Benutzer).|Ja|
| Calls.JoinGroupCall.All |Nehmen Sie an Gruppenanrufen und Besprechungen als App-Vorschau teil. |Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer zu verknüpfen. Die App ist mit den Berechtigungen eines Verzeichnisbenutzers für Besprechungen in Ihrem Mandanten verknüpft.|Ja|
| Calls.JoinGroupCallasGuest.All |Teilnehmen an Gruppenanrufen und Besprechungen als Gastvorschau. |Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer anonym zu verknüpfen. Die App ist als Gast zu Besprechungen in Ihrem Mandanten verbunden.|Ja|
| Calls.AccessMedia.All |Zugreifen auf Mediendatenströme in einem Anruf als App-Vorschau. |Ermöglicht der App, direkten Zugriff auf Medienstreams in einem Anruf ohne einen angemeldeten Benutzer zu erhalten.|Ja|

> [!IMPORTANT]
> Sie können die Medienzugriffs-API nicht verwenden, um Medieninhalte aus Anrufen oder Besprechungen aufzuzeichnen oder anderweitig zu speichern, auf die Ihre Anwendung zugreift oder Daten aus diesem Medieninhaltseintrag oder dieser Aufzeichnung abgeleitet. Sie müssen zuerst die [ `updateRecordingStatus` API](/graph/api/call-updaterecordingstatus) aufrufen, um anzugeben, dass die Aufzeichnung begonnen hat, und eine Erfolgsantwort von dieser API erhalten. Wenn Ihre Anwendung mit der Aufzeichnung einer Besprechung oder eines Anrufs beginnt, muss sie die Aufzeichnung beenden, bevor die API aufgerufen `updateRecordingStatus` wird, um anzugeben, dass die Aufzeichnung beendet wurde.

### <a name="application-permissions-for-online-meetings"></a>Anwendungsberechtigungen für Onlinebesprechungen

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Onlinebesprechungen:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| OnlineMeetings.Read.All |Lesen von Onlinebesprechungsdetails aus der App-Vorschau|Ermöglicht der App, Onlinebesprechungsdetails in Ihrer Organisation ohne einen angemeldeten Benutzer zu lesen.|Ja|
| OnlineMeetings.ReadWrite.All |Lesen und Erstellen von Onlinebesprechungen aus der App-Vorschau im Auftrag eines Benutzers|Ermöglicht der App, Onlinebesprechungen in Ihrer Organisation im Namen eines Benutzers ohne einen angemeldeten Benutzer zu erstellen.|Ja|

### <a name="assign-permissions"></a>Berechtigungen zuweisen

Sie müssen die Anwendungsberechtigungen für Ihren Bot im Voraus mithilfe des [Azure-Portals](https://aka.ms/aadapplist) konfigurieren, wenn Sie den [V1-Endpunkt Azure Active Directory (AAD)](/azure/active-directory/develop/azure-ad-endpoint-comparison)verwenden möchten.

### <a name="get-tenant-administrator-consent"></a>Einholen der Zustimmung des Mandantenadministrators

Bei Apps, die den AAD V1-Endpunkt verwenden, kann ein Mandantenadministrator den Anwendungsberechtigungen über das [Azure-Portal](https://portal.azure.com) zustimmen, wenn Ihre App in ihrer Organisation installiert wird. Alternativ können Sie eine Anmeldeumgebung in Ihrer App bereitstellen, über die Administratoren den von Ihnen konfigurierten Berechtigungen zustimmen können. Nachdem die Administratorzustimmung von AAD aufgezeichnet wurde, kann Ihre App Token anfordern, ohne erneut die Zustimmung anfordern zu müssen.

Sie können sich darauf verlassen, dass ein Administrator die Berechtigungen erteilt, die Ihre App im [Azure-Portal](https://portal.azure.com)benötigt. Eine bessere Option ist die Bereitstellung einer Anmeldeumgebung für Administratoren mithilfe des AAD `/adminconsent` V2-Endpunkts. Weitere Informationen finden Sie in den Anweisungen zum Erstellen einer URL für [die Administratorzustimmung.](https://developer.microsoft.com/graph/docs/concepts/auth_v2_service#3-get-administrator-consent)

> [!NOTE]
> Zum Erstellen der Mandanten-Administratorzustimmungs-URL ist ein konfigurierter Umleitungs-URI oder eine Antwort-URL im [App-Registrierungsportal](https://apps.dev.microsoft.com/) erforderlich. Um Antwort-URLs für Ihren Bot hinzuzufügen, greifen Sie auf Ihre Bot-Registrierung zu, und wählen Sie **"Erweiterte Optionen**  >  **Anwendungsmanifest bearbeiten"** aus. Fügen Sie die Umleitungs-URL zur `replyUrls` Sammlung hinzu.

> [!IMPORTANT]
> Jedes Mal, wenn Sie eine Änderung an den Berechtigungen Ihrer Anwendung vornehmen, müssen Sie auch den Administratorzustimmungsprozess wiederholen. Änderungen, die im App-Registrierungsportal vorgenommen wurden, werden erst widergespiegelt, wenn die Zustimmung vom Administrator des Mandanten erneut angewendet wurde.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Eingehende Anrufbenachrichtigungen](~/bots/calls-and-meetings/call-notifications.md)
