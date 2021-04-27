---
title: Registrieren von Anrufen und Besprechungen für Microsoft Teams
description: Informationen zum Registrieren eines neuen Audio-/Videoanruf-Bots für Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Aufrufen von Audio-/Videovideomedien für Bots
ms.openlocfilehash: a11350a3c5bae0b2eb3a36b9e1233ed92e1705c8
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020148"
---
# <a name="register-calls-and-meetings-bot-for-microsoft-teams"></a>Registrieren von Anrufen und Besprechungen für Microsoft Teams

Ein Bot, der an Audio- oder Videoanrufen und Onlinebesprechungen teil nimmt, ist ein regulärer Microsoft Teams-Bot mit den folgenden zusätzlichen Funktionen, die zum Registrieren des Bots verwendet werden:

* Es gibt eine neue Version des Teams-App-Manifests mit zwei zusätzlichen Einstellungen `supportsCalling` und `supportsVideo` . Diese Einstellungen sind in der [Entwicklervorschauversion](../../resources/dev-preview/developer-preview-intro.md) des Teams-App-Manifests enthalten.
* [Microsoft Graph-Berechtigungen](./registering-calling-bot.md#add-graph-permissions) müssen für die Microsoft App-ID Ihres Bots konfiguriert werden.
* Die Zugriffsberechtigungen für Graph-Anrufe und Onlinebesprechungen erfordern die Zustimmung des Mandantenadministrators.

## <a name="new-manifest-settings"></a>Neue Manifesteinstellungen

Anrufe und Onlinebesprechungsbots verfügen über die folgenden zwei zusätzlichen Einstellungen manifest.js, die Audio oder Video für Ihren Bot in Teams aktivieren.

* `bots[0].supportsCalling`. Wenn vorhanden und auf festgelegt, ermöglicht Teams Ihrem Bot die Teilnahme an Anrufen `true` und Onlinebesprechungen.
* `bots[0].supportsVideo`. Wenn vorhanden und auf `true` festgelegt, weiß Teams, dass Ihr Bot Video unterstützt.

Wenn Sie möchten, dass ihre IDE die manifest.jsfür Ihre Anrufe und Besprechungsbots ordnungsgemäß auf diese Werte überprüft, können Sie das `$schema` Attribut wie folgt ändern:

```json
"$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
```

Im nächsten Abschnitt können Sie einen neuen Bot erstellen oder Ihrem vorhandenen Bot Anruffunktionen hinzufügen.

## <a name="create-new-bot-or-add-calling-capabilities"></a>Erstellen eines neuen Bots oder Hinzufügen von Anruffunktionen

Informationen zum Erstellen von Bots finden Sie unter [Create a bot for Teams](../how-to/create-a-bot-for-teams.md).

**So erstellen Sie einen neuen Bot für Teams**

1. Verwenden Sie diesen Link, um einen neuen Bot zu erstellen, `https://dev.botframework.com/bots/new` . Wenn Sie im Bot Framework-Portal alternativ die Schaltfläche Bot **erstellen** auswählen, erstellen Sie Ihren Bot in Microsoft Azure, für den Sie über ein Azure-Konto verfügen müssen.
1. Fügen Sie den Teams-Kanal hinzu.
1. Wählen Sie **auf der** Seite Teams-Kanal die Registerkarte Anruf aus. Wählen **Sie Anruf aktivieren** aus, und aktualisieren Sie dann **Webhook (für Anrufe)** mit Ihrer HTTPS-URL, in der Sie eingehende Benachrichtigungen erhalten, z. B. `https://contoso.com/teamsapp/api/calling` . Weitere Informationen finden Sie unter [Konfigurieren von Kanälen](/bot-framework/portal-configure-channels).

    ![Konfigurieren von Teams-Kanalinformationen](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

Der nächste Abschnitt enthält eine Liste der Anwendungsberechtigungen, die für Anrufe und Onlinebesprechungen unterstützt werden.

## <a name="add-graph-permissions"></a>Hinzufügen von Graph-Berechtigungen

Das Diagramm bietet detaillierte Berechtigungen zum Steuern des Zugriffs, den Apps auf Ressourcen haben. Sie entscheiden, welche Berechtigungen für Graph Ihre App-Anforderungen hat. Die graph-aufrufenden APIs unterstützen Anwendungsberechtigungen, die von Apps verwendet werden, die ohne angemeldeten Benutzer ausgeführt werden. Ein Mandantenadministrator muss anwendungsberechtigungen zustimmen.

### <a name="application-permissions-for-calls"></a>Anwendungsberechtigungen für Anrufe

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Aufrufe:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administrator-Zustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| Calls.Initiate.All |Initiieren sie ausgehende 1:1-Anrufe aus der App-Vorschau. |Ermöglicht der App, ausgehende Anrufe an einen einzelnen Benutzer zu tätigen und Anrufe an Benutzer im Organisationsverzeichnis zu übertragen (ohne angemeldeten Benutzer).|Ja|
| Calls.InitiateGroupCall.All |Initiieren von ausgehenden Gruppenanrufen aus der App-Vorschau. |Ermöglicht der App, ausgehende Anrufe an mehrere Benutzer zu tätigen und Teilnehmer in Ihrer Organisation zu Besprechungen hinzufügen (ohne angemeldeten Benutzer).|Ja|
| Calls.JoinGroupCall.All |Teilnehmen an Gruppenanrufen und Besprechungen als App-Vorschau. |Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer zu verknüpfen. Die App wird mit den Berechtigungen eines Verzeichnisbenutzers für Besprechungen in Ihrem Mandanten verbunden.|Ja|
| Calls.JoinGroupCallasGuest.All |Teilnehmen an Gruppenanrufen und Besprechungen als Gastvorschau. |Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer anonym zu verknüpfen. Die App wird als Gast an Besprechungen in Ihrem Mandanten teilnehmen.|Ja|
| Calls.AccessMedia.All |Zugreifen auf Medienstreams in einem Anruf als App-Vorschau. |Ermöglicht der App, direkten Zugriff auf Medienstreams in einem Anruf ohne einen angemeldeten Benutzer zu erhalten.|Ja|

> [!IMPORTANT]
> Sie können die Medienzugriffs-API nicht verwenden, um Medieninhalte aus Anrufen oder Besprechungen zu erfassen oder anderweitig zu speichern, auf die Ihre Anwendung zu diesem Medieninhaltsdatensatz oder dieser Aufzeichnung zu zugegriffen oder daraus Daten ableitung. Sie müssen zuerst die [ `updateRecordingStatus` API aufrufen,](/graph/api/call-updaterecordingstatus) um anzugeben, dass die Aufzeichnung begonnen hat, und eine Erfolgreiche Antwort von dieser API erhalten. Wenn Ihre Anwendung mit der Aufzeichnung einer Besprechung oder eines Anrufs beginnt, muss sie die Aufzeichnung beenden, bevor sie die API aufruft, um anzugeben, dass die Aufzeichnung `updateRecordingStatus` beendet wurde.

### <a name="application-permissions-for-online-meetings"></a>Anwendungsberechtigungen für Onlinebesprechungen

Die folgende Tabelle enthält eine Liste der Anwendungsberechtigungen für Onlinebesprechungen:

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administrator-Zustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
| OnlineMeetings.Read.All |Lesen von Onlinebetreffdetails aus der App-Vorschau|Ermöglicht der App das Lesen von Online-Besprechungsdetails in Ihrer Organisation, ohne dass ein Benutzer angemeldet ist.|Ja|
| OnlineMeetings.ReadWrite.All |Lesen und Erstellen von Onlinebesprechungen aus der App-Vorschau im Namen eines Benutzers|Ermöglicht der App das Erstellen von Onlinebesprechungen in Ihrer Organisation im Namen eines Benutzers, ohne dass ein Benutzer angemeldet ist.|Ja|

### <a name="assign-permissions"></a>Berechtigungen zuweisen

Sie müssen die Anwendungsberechtigungen für Ihren [](https://aka.ms/aadapplist) Bot vorab mithilfe des Azure-Portals konfigurieren, wenn Sie den [Azure Active Directory (AAD) V1-Endpunkt verwenden möchten.](/azure/active-directory/develop/azure-ad-endpoint-comparison)

### <a name="get-tenant-administrator-consent"></a>Zustimmung des Mandantenadministrators erhalten

Bei Apps, die den AAD V1-Endpunkt verwenden, kann [](https://portal.azure.com) ein Mandantenadministrator den Anwendungsberechtigungen mithilfe des Azure-Portals zustimmen, wenn Ihre App in ihrer Organisation installiert ist. Alternativ können Sie in Ihrer App eine Anmeldeerfahrung bereitstellen, über die Administratoren den von Ihnen konfigurierten Berechtigungen zustimmen können. Sobald die Zustimmung des Administrators vom AAD aufgezeichnet wurde, kann Ihre App Token anfordern, ohne erneut eine Zustimmung anfordern zu müssen.

Sie können sich darauf verlassen, dass ein Administrator die Berechtigungen erteilt, die Ihre App im [Azure-Portal benötigt.](https://portal.azure.com) Eine bessere Option ist die Bereitstellung einer Anmeldeerfahrung für Administratoren mithilfe des AAD `/adminconsent` V2-Endpunkts. Weitere Informationen finden Sie unter [Anweisungen zum Erstellen einer Administrator-Zustimmungs-URL](https://developer.microsoft.com/graph/docs/concepts/auth_v2_service#3-get-administrator-consent).

> [!NOTE]
> Zum Erstellen der Mandanten-Admin-Zustimmungs-URL ist ein konfigurierter Umleitungs-URI oder eine Antwort-URL im [App-Registrierungsportal](https://apps.dev.microsoft.com/) erforderlich. Um Antwort-URLs für Ihren Bot hinzuzufügen, greifen Sie auf Ihre Botregistrierung zu, wählen Sie **Erweiterte Optionen**  >  **Anwendungsmanifest bearbeiten aus.** Fügen Sie ihre Umleitungs-URL zur Auflistung `replyUrls` hinzu.

> [!IMPORTANT]
> Wenn Sie die Berechtigungen Ihrer Anwendung ändern, müssen Sie auch den Administrator-Zustimmungsprozess wiederholen. Änderungen, die im App-Registrierungsportal vorgenommen wurden, werden erst dann wider, wenn die Zustimmung vom Administrator des Mandanten erneut angewendet wurde.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Eingehende Anrufbenachrichtigungen](~/bots/calls-and-meetings/call-notifications.md)
