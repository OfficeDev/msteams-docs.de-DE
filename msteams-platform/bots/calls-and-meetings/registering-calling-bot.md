---
title: Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams
description: Erfahren Sie, wie Sie einen neuen Audio-/Videoanruf-Bot für Microsoft Teams registrieren, einen neuen Bot erstellen oder ihm Anruffunktionen hinzufügen und Graph-Berechtigungen hinzufügen.
ms.topic: conceptual
ms.localizationpriority: high
keywords: Anruf-Bot Audio-/Video Videomedien
ms.openlocfilehash: 53c12b3d65ad909088e18081ed4b38a77919844b
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111416"
---
# <a name="register-calls-and-meetings-bot-for-microsoft-teams"></a>Registrierung eines Anruf- und Besprechungsbots für Microsoft Teams

Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teilnimmt, ist ein regulärer Microsoft Teams-Bot mit den folgenden zusätzlichen Funktionen, die zum Registrieren des Bots verwendet werden:

* Es gibt eine neue Version des Microsoft Teams-App-Manifests mit zwei zusätzlichen Einstellungen: `supportsCalling` und `supportsVideo`. Diese Einstellungen sind im [Manifestschema für Microsoft Teams](../../resources/schema/manifest-schema.md) enthalten.
* [Microsoft Graph-Berechtigungen](./registering-calling-bot.md#add-graph-permissions) müssen für die Microsoft App-ID Ihres Bots konfiguriert werden.
* Für Microsoft Graph-APIs für Anrufe und Onlinebesprechungen ist die Zustimmung des Mandantenadministrators erforderlich.

## <a name="new-manifest-settings"></a>Neue Manifesteinstellungen

Für Aufruf- und Onlinebesprechungs-Bots gibt es die folgenden zwei zusätzlichen Einstellungen in der manifest.json-Datei, über die Audio oder Video für Ihren Bot in Microsoft Teams aktiviert werden.

* `bots[0].supportsCalling`. Wenn vorhanden und auf `true` festgelegt, erlaubt Microsoft Teams Ihrem Bot die Teilnahme an Anrufen und Onlinebesprechungen.
* `bots[0].supportsVideo`. Wenn vorhanden und auf `true` festgelegt, weiß Microsoft Teams, dass Ihr Bot Videofunktionen unterstützt.

Wenn Ihre IDE das manifest.json-Schema für Ihre Aufrufe und Besprechungs-Bots ordnungsgemäß auf diese Werte überprüfen soll, können Sie das `$schema`-Attribut wie folgt ändern:

```json
"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
```

Im nächsten Abschnitt können Sie einen neuen Bot erstellen oder Anruffunktionen zu Ihrem vorhandenen Bot hinzufügen.

## <a name="create-new-bot-or-add-calling-capabilities"></a>Erstellen eines neuen Bots oder Hinzufügen von Anruffunktionen

Informationen zum Erstellen von Bots finden Sie unter [Erstellen eines Bots für Microsoft Teams](../how-to/create-a-bot-for-teams.md).

So erstellen Sie einen neuen Bot für Microsoft Teams:

1. Verwenden Sie diesen Link, um einen neuen Bot zu erstellen: `https://dev.botframework.com/bots/new` Alternativ können Sie im Bot Framework-Portal die Schaltfläche "**Bot erstellen**" anklicken und Ihren Bot in Microsoft Azure erstellen. Hierfür müssen Sie über ein Azure-Konto verfügen.
1. Fügen Sie den Microsoft Teams-Kanal hinzu.
1. Wählen Sie die Registerkarte **Anrufe** auf der Microsoft Teams-Kanalseite aus. Klicken Sie auf **Anrufe aktivieren**, und aktualisieren Sie dann **Webhook (für Anrufe)** mit Ihrer HTTPS-URL, unter der Sie eingehende Benachrichtigungen erhalten, beispielsweise `https://contoso.com/teamsapp/api/calling`. Weitere Informationen finden Sie unter [Konfigurieren von Kanälen](/bot-framework/portal-configure-channels).

    ![Konfigurieren der Microsoft Teams-Kanalinformationen](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

Der nächste Abschnitt enthält eine Liste der Anwendungsberechtigungen, die für Anrufe und Onlinebesprechungen unterstützt werden.

## <a name="add-graph-permissions"></a>Hinzufügen von Microsoft Graph-Berechtigungen

Microsoft Graph bietet Berechtigungen, um den Zugriff von Apps auf Ressourcen präzise zu steuern. Sie entscheiden, welche Berechtigungen Ihre App für Microsoft Graph anfordert. Die Graph-aufrufenden APIs unterstützen Anwendungsberechtigungen, die von Apps verwendet werden, die ohne angemeldeten Benutzer ausgeführt werden. Anwendungsberechtigungen muss von einem Mandantenadministrator zugestimmt werden.

### <a name="application-permissions-for-calls"></a>Anwendungsberechtigungen für Anrufe

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Aufrufe:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| Calls.Initiate.All |Ausgehende 1:1-Anrufe aus der App initiieren (Vorschau) |Ermöglicht der App, ausgehende Anrufe an einen einzelnen Benutzer zu tätigen und Anrufe an Benutzer im Organisationsverzeichnis zu übertragen (ohne angemeldeten Benutzer).|Ja|
| Calls.InitiateGroupCall.All |Ausgehende Gruppenanrufe aus der App initiieren (Vorschau) |Ermöglicht der App, ausgehende Anrufe an mehrere Benutzer zu tätigen und Teilnehmer in Ihrer Organisation zu Besprechungen hinzufügen (ohne angemeldeten Benutzer).|Ja|
| Calls.JoinGroupCall.All |Gruppenanrufen und Besprechungen beitreten als App (Vorschau) |Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer zu verknüpfen. Die App tritt Besprechungen in Ihrem Mandanten mit den Berechtigungen eines Verzeichnisbenutzers bei.|Ja|
| Calls.JoinGroupCallasGuest.All |Gruppenanrufen und Besprechungen als Gast beitreten (Vorschau) |Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer anonym zu verknüpfen. Die App tritt Besprechungen in Ihrem Mandanten als Gast bei.|Ja|
| Calls.AccessMedia.All |Auf Medienstreams in einem Anruf als App zugreifen (Vorschau) |Ermöglicht der App, direkten Zugriff auf Medienstreams in einem Anruf ohne einen angemeldeten Benutzer zu erhalten.|Ja|

> [!IMPORTANT]
> Sie können die Media Access-API nicht verwenden, um Medieninhalte aus Anrufen oder Besprechungen, auf die Ihre Anwendung zugreift, oder aus diesen aufgezeichneten Medieninhalten abgeleitete Daten aufzuzeichnen oder auf andere Weise zu speichern. Sie müssen zuerst die [`updateRecordingStatus`-API](/graph/api/call-updaterecordingstatus) aufrufen, um anzugeben, dass die Aufzeichnung begonnen hat, und eine Erfolgsantwort von dieser API erhalten. Wenn Ihre Anwendung mit der Aufzeichnung einer Besprechung oder eines Anrufs beginnt, muss sie die Aufzeichnung beenden, bevor die `updateRecordingStatus`-API aufgerufen wird, um anzugeben, dass die Aufzeichnung beendet wurde.

### <a name="application-permissions-for-online-meetings"></a>Anwendungsberechtigungen für Onlinebesprechungen

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Onlinebesprechungen:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| OnlineMeetings.Read.All |Lesen von Onlinebesprechungsdetails aus der App (Vorschau)|Ermöglicht der App, Onlinebesprechungsdetails in Ihrer Organisation ohne einen angemeldeten Benutzer zu lesen.|Ja|
| OnlineMeetings.ReadWrite.All |Lesen und Erstellen von Onlinebesprechungen aus der App (Vorschau) im Namen eines Benutzers|Ermöglicht der App, Onlinebesprechungen in Ihrer Organisation im Namen eines Benutzers ohne einen angemeldeten Benutzer zu lesen.|Ja|

### <a name="assign-permissions"></a>Berechtigungen zuweisen

Wenn Sie den [Microsoft Azure Active Directory (Azure AD) V1-Endpunkt](/azure/active-directory/develop/azure-ad-endpoint-comparison) verwenden möchten, müssen Sie die Anwendungsberechtigungen für Ihren Bot vorab über das [Microsoft Azure-Portal](https://aka.ms/aadapplist) konfigurieren.

### <a name="get-tenant-administrator-consent"></a>Einholen der Administratorzustimmung

Bei Apps, die den Azure AD V1-Endpunkt verwenden, kann ein Administrator den Anwendungsberechtigungen im [Microsoft Azure-Portal](https://portal.azure.com) zustimmen, wenn die App in seiner Organisation installiert wird. Alternativ können Sie eine Registrierungsfunktion in der App bereitstellen, über die Administratoren den von Ihnen konfigurierten Berechtigungen zustimmen können. Sobald die Administratorzustimmung von Azure AD aufgezeichnet wurde, kann Ihre App Token anfordern, ohne dass eine erneute Zustimmung erforderlich ist.

Ein Administrator kann für Sie die Berechtigungen, die Ihre App benötigt, im [Microsoft Azure-Portal](https://portal.azure.com) gewähren. Eine bessere Option besteht darin, Administratoren eine Registrierungsfunktion über den Azure AD V2`/adminconsent`-Endpunkt zur Verfügung zu stellen. Weitere Informationen finden Sie unter [Anweisungen zum Erstellen einer Administratorzustimmungs-URL](/graph/auth-v2-service#3-get-administrator-consent).

> [!NOTE]
> Um die Zustimmungs-URL des Mandantenadministrators zu erstellen, ist eine konfigurierte Umleitungs-URI oder Antwort-URL im [App-Registrierungsportal](https://apps.dev.microsoft.com/) erforderlich. Um Antwort-URLs für Ihren Bot hinzuzufügen, wählen Sie in Ihrer Bot-Registrierung **Erweiterte Optionen** > **Anwendungsmanifest bearbeiten** aus. Fügen Sie die Umleitungs-URL zur `replyUrls`-Sammlung hinzu.

> [!IMPORTANT]
> Jedes Mal, wenn Sie Änderungen an den Berechtigungen Ihrer App vornehmen, müssen Sie auch den Prozess der Administratorzustimmung wiederholen. Im App-Registrierungsportal vorgenommene Änderungen werden erst wiedergegeben, wenn die Zustimmung des Mandantenadministrators erneut erteilt wurde.

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **Graph** |
|---------------|----------|--------|
| Anruf- und Besprechungs-Bots | Die Beispiel-App verdeutlicht, wie Bots Anrufe erstellen, an Besprechungen teilnehmen und Anrufe durchstellen können. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-calling-meeting/csharp) |

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../sbs-calling-and-meeting.yml) zum Einrichten von Anrufen und Besprechungen in einem Bot.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Eingehende Anrufbenachrichtigungen](~/bots/calls-and-meetings/call-notifications.md)

## <a name="see-also"></a>Siehe auch

* [Eingehende Anrufbenachrichtigungen](~/bots/calls-and-meetings/call-notifications.md)
* [Entwickeln von Anruf- und Onlinebesprechungs-Bots auf Ihrem lokalen PC](~/bots/calls-and-meetings/debugging-local-testing-calling-meeting-bots.md)
* [Anzeigen von App-Berechtigungen und Erteilen der Administratorzustimmung](/MicrosoftTeams/app-permissions-admin-center)
