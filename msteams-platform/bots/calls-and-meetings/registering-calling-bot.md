---
title: Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams
description: Erfahren Sie, wie Sie einen neuen Audio-/Videoanrufbot für Microsoft Teams registrieren, einen neuen Bot erstellen oder Anruffunktionen hinzufügen und Graph-Berechtigungen hinzufügen.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Aufrufen von Bot-Audio-/Video-Audiovideomedien
ms.openlocfilehash: 1a90e430ba0c5bc4ae1ab246baa85a5d33507a43
ms.sourcegitcommit: 52af681132e496a57b18f468c5b73265a49a5f44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2022
ms.locfileid: "64590766"
---
# <a name="register-calls-and-meetings-bot-for-microsoft-teams"></a>Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams

Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt, ist ein regulärer Microsoft Teams Bot mit den folgenden zusätzlichen Features, die zum Registrieren des Bots verwendet werden:

* Es gibt eine neue Version des Teams-App-Manifests mit zwei zusätzlichen Einstellungen und `supportsCalling` `supportsVideo`. Diese Einstellungen sind im [Manifestschema für Microsoft Teams](../../resources/schema/manifest-schema.md) enthalten.
* [Microsoft Graph Berechtigungen](./registering-calling-bot.md#add-graph-permissions) müssen für die Microsoft App-ID Ihres Bots konfiguriert werden.
* Die APIs für Graph Anrufe und Onlinebesprechungen erfordern die Zustimmung des Mandantenadministrators.

## <a name="new-manifest-settings"></a>Neue Manifesteinstellungen

Bots für Anrufe und Onlinebesprechungen verfügen über die folgenden beiden zusätzlichen Einstellungen in "manifest.json", die Audio- oder Videodaten für Ihren Bot in Teams aktivieren.

* `bots[0].supportsCalling`. Wenn vorhanden und festgelegt`true`, ermöglicht Teams Ihrem Bot die Teilnahme an Anrufen und Onlinebesprechungen.
* `bots[0].supportsVideo`. Wenn vorhanden und festgelegt, `true`weiß Teams, dass Ihr Bot Video unterstützt.

Wenn Ihre IDE das Manifest.json-Schema für Ihre Aufrufe und Besprechungsbots ordnungsgemäß auf diese Werte überprüfen soll, können Sie das `$schema` Attribut wie folgt ändern:

```json
"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
```

Im nächsten Abschnitt können Sie einen neuen Bot erstellen oder Ihrem vorhandenen Bot Anruffunktionen hinzufügen.

## <a name="create-new-bot-or-add-calling-capabilities"></a>Erstellen eines neuen Bots oder Hinzufügen von Anruffunktionen

Informationen zum Erstellen von Bots finden Sie unter [Erstellen eines Bots für Teams](../how-to/create-a-bot-for-teams.md).

So erstellen Sie einen neuen Bot für Teams:

1. Verwenden Sie diesen Link, um einen neuen Bot zu erstellen. `https://dev.botframework.com/bots/new` Wenn Sie alternativ die Schaltfläche "**Bot** erstellen" im Bot Framework-Portal auswählen, erstellen Sie Ihren Bot in Microsoft Azure, für die Sie über ein Azure-Konto verfügen müssen.
1. Fügen Sie den Teams Kanal hinzu.
1. Wählen Sie die Registerkarte **"Anrufe**" auf der Teams Kanalseite aus. Wählen Sie **"Anruf aktivieren"** aus, und aktualisieren Sie dann **Webhook (für Anrufe)** mit Ihrer HTTPS-URL, unter der Sie eingehende Benachrichtigungen erhalten, z. B `https://contoso.com/teamsapp/api/calling`. . Weitere Informationen finden Sie unter ["Konfigurieren von Kanälen"](/bot-framework/portal-configure-channels).

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
> Sie können die Medienzugriffs-API nicht verwenden, um Medieninhalte aus Anrufen oder Besprechungen aufzuzeichnen oder anderweitig zu speichern, auf die Ihre Anwendung zugreift oder Daten aus diesem Medieninhaltseintrag oder dieser Aufzeichnung abgeleitet. Sie müssen zuerst die [`updateRecordingStatus` API](/graph/api/call-updaterecordingstatus) aufrufen, um anzugeben, dass die Aufzeichnung begonnen hat, und eine Erfolgsantwort von dieser API erhalten. Wenn Ihre Anwendung mit der Aufzeichnung einer Besprechung oder eines Anrufs beginnt, muss sie die Aufzeichnung beenden, bevor die `updateRecordingStatus` API aufgerufen wird, um anzugeben, dass die Aufzeichnung beendet wurde.

### <a name="application-permissions-for-online-meetings"></a>Anwendungsberechtigungen für Onlinebesprechungen

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Onlinebesprechungen:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| OnlineMeetings.Read.All |Lesen von Onlinebesprechungsdetails aus der App-Vorschau|Ermöglicht der App, Onlinebesprechungsdetails in Ihrer Organisation ohne einen angemeldeten Benutzer zu lesen.|Ja|
| OnlineMeetings.ReadWrite.All |Lesen und Erstellen von Onlinebesprechungen aus der App-Vorschau im Auftrag eines Benutzers|Ermöglicht der App, Onlinebesprechungen in Ihrer Organisation im Namen eines Benutzers ohne einen angemeldeten Benutzer zu erstellen.|Ja|

### <a name="assign-permissions"></a>Berechtigungen zuweisen

Sie müssen die Anwendungsberechtigungen für Ihren Bot im Voraus mithilfe des [Microsoft Azure-Portals](https://aka.ms/aadapplist) konfigurieren, wenn Sie den [Microsoft Azure Active Directory (Azure AD) V1-Endpunkt](/azure/active-directory/develop/azure-ad-endpoint-comparison) verwenden möchten.

### <a name="get-tenant-administrator-consent"></a>Einholen der Zustimmung des Mandantenadministrators

Bei Apps, die den Azure AD V1-Endpunkt verwenden, kann ein Mandantenadministrator den Anwendungsberechtigungen über das [Microsoft Azure-Portal](https://portal.azure.com) zustimmen, wenn Ihre App in ihrer Organisation installiert wird. Alternativ können Sie eine Anmeldeumgebung in Ihrer App bereitstellen, über die Administratoren den von Ihnen konfigurierten Berechtigungen zustimmen können. Nachdem die Administratorzustimmung von Azure AD aufgezeichnet wurde, kann Ihre App Token anfordern, ohne erneut die Zustimmung anfordern zu müssen.

Sie können sich darauf verlassen, dass ein Administrator die Berechtigungen erteilt, die Ihre App im [Microsoft Azure-Portal](https://portal.azure.com) benötigt. Eine bessere Option ist die Bereitstellung einer Anmeldeumgebung für Administratoren mithilfe des Azure AD V2-Endpunkts`/adminconsent`. Weitere Informationen finden Sie in [den Anweisungen zum Erstellen einer ADMINISTRATORzustimmungs-URL](/graph/auth-v2-service#3-get-administrator-consent).

> [!NOTE]
> Zum Erstellen der Mandanten-Administratorzustimmungs-URL ist ein konfigurierter Umleitungs-URI oder eine Antwort-URL im [App-Registrierungsportal](https://apps.dev.microsoft.com/) erforderlich. Um Antwort-URLs für Ihren Bot hinzuzufügen, greifen Sie auf Ihre Bot-Registrierung zu, und wählen Sie **"Erweiterte** **OptionenEdit-Anwendungsmanifest** > " aus. Fügen Sie die Umleitungs-URL zur `replyUrls` Sammlung hinzu.

> [!IMPORTANT]
> Jedes Mal, wenn Sie eine Änderung an den Berechtigungen Ihrer Anwendung vornehmen, müssen Sie auch den Administratorzustimmungsprozess wiederholen. Änderungen, die im App-Registrierungsportal vorgenommen wurden, werden erst widergespiegelt, wenn die Zustimmung vom Administrator des Mandanten erneut angewendet wurde.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Graph** |
|---------------|----------|--------|
| Anruf- und Besprechungsbot | Die Beispiel-App zeigt, wie Bot Anrufe erstellen, an Besprechungen teilnehmen und Anrufe übertragen kann. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-calling-meeting/csharp) |

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../sbs-calling-and-meeting.yml) zum Einrichten von Anrufen und Besprechungen in einem Bot.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Eingehende Anrufbenachrichtigungen](~/bots/calls-and-meetings/call-notifications.md)

## <a name="see-also"></a>Weitere Informationen

* [Eingehende Anrufbenachrichtigungen](~/bots/calls-and-meetings/call-notifications.md)
* [Entwickeln von Anruf- und Onlinebesprechungs-Bots auf Ihrem lokalen PC](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
* [Anzeigen der App-Berechtigung und Erteilen der Administratorzustimmung](/MicrosoftTeams/app-permissions-admin-center)
