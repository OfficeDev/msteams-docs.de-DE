---
title: Registrieren eines Anruf-und Besprechungs-bot für Microsoft Teams
description: Informationen zum Registrieren eines neuen bot für Audio/Videoanrufe für Microsoft Teams
keywords: Aufrufen von bot-Audio/Video-Audio-Video Medien
ms.openlocfilehash: 5a832646d4fa622f746f88a3a969ae4ad3ce69a6
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552444"
---
# <a name="register-a-calling-bot-for-microsoft-teams"></a>Registrieren eines anrufenden bot für Microsoft Teams

Ein bot, der an Audio/Video-anrufen und Onlinebesprechungen teilnimmt, ist ein gewöhnlicher Microsoft Teams-bot mit einigen zusätzlichen Features:

* Es gibt eine neue Version des Teams-App-Manifests mit zwei zusätzlichen Einstellungen `supportsCalling` und `supportsVideo` . Diese Einstellungen sind in der [Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) -Version des Microsoft Teams-App-Manifests enthalten.
* [Microsoft Graph-Berechtigungen](./registering-calling-bot.md#add-microsoft-graph-permissions) müssen für die Microsoft-App-ID Ihres bot konfiguriert werden.
* Die Berechtigungen für Microsoft Graph-und Online Besprechungs-APIs erfordern mandantenadministrator Zustimmung.

Lassen Sie uns das oben beschriebene näher erläutern.

## <a name="new-manifest-settings"></a>Neue manifesteinstellungen

Bots für Anrufe und Onlinebesprechungen weisen zwei zusätzliche Einstellungen im manifest.jsauf, die Audio/Video für Ihren bot in Microsoft Teams aktivieren.

* `bots[0].supportsCalling`. Wenn diese Option vorhanden und auf festgelegt `true` ist, können Teams ihren bot an anrufen und Onlinebesprechungen teilnehmen.
* `bots[0].supportsVideo`. Wenn es vorhanden und auf festgelegt `true` ist, wissen Teams, dass Ihr bot Video unterstützt.

Wenn Sie möchten, dass die IDE die manifest.jsdes Schemas für Ihren anrufenden und Besprechungs-bot für diese Werte ordnungsgemäß überprüft, können Sie das `$schema` Attribut wie folgt ändern:

```json
"$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
```

## <a name="creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot"></a>Erstellen eines neuen bot oder Hinzufügen von Anruffunktionen zu einem vorhandenen bot

Das Erstellen eines neuen bot wird im Thema [Erstellen eines bot für Microsoft Teams](../how-to/create-a-bot-for-teams.md) ausführlicher behandelt, aber wir werden hier einiges wiederholen:

1. Verwenden Sie diesen Link, um einen neuen bot zu erstellen: `https://dev.botframework.com/bots/new` . Wenn Sie stattdessen die Schaltfläche " *bot erstellen* " im bot-Framework-Portal auswählen, erstellen Sie Ihren bot in Microsoft Azure, für die Sie ein Azure-Konto benötigen.
1. Fügen Sie den Microsoft Teams-Kanal hinzu. Klicken Sie auf der Microsoft Teams-Kanalseite auf die Registerkarte "anrufen", und wählen Sie **Anruf aktivieren** aus, und aktualisieren Sie dann **webhook (zum Aufrufen)** mit ihrer HTTPS-URL, über die Sie eingehende Benachrichtigungen erhalten, Beispiels `https://contoso.com/teamsapp/api/calling` Weise. Weitere Informationen zum Konfigurieren von Kanälen erhalten Sie unter [Configuring Channels](/bot-framework/portal-configure-channels) .
  ![Konfigurieren von Microsoft Teams-Kanalinformationen](~/assets/images/calls-and-meetings/configure-msteams-channel.png)

## <a name="add-microsoft-graph-permissions"></a>Hinzufügen von Microsoft Graph-Berechtigungen

Microsoft Graph macht granulare Berechtigungen verfügbar, die den Zugriff steuern, den apps auf Ressourcen haben. Als Entwickler entscheiden Sie, welche Berechtigungen für Microsoft Graph Ihre App anfordert.  Die Microsoft Graph-Aufruf-APIs unterstützen _Anwendungsberechtigungen_, die von apps verwendet werden, die ohne angemeldeten Benutzer ausgeführt werden.  Ein mandantenadministrator muss die Zustimmung zu den Anwendungsberechtigungen erteilen. Im folgenden finden Sie eine Liste dieser Berechtigungen:

### <a name="application-permissions-calls"></a>Anwendungsberechtigungen: Anrufe

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
|_Calls.Initiate.All_|Ausgehende 1:1-Anrufe aus der App initiieren (Vorschau)|Ermöglicht der App, ausgehende Anrufe an einen einzelnen Benutzer zu tätigen und Anrufe an Benutzer im Organisationsverzeichnis zu übertragen (ohne angemeldeten Benutzer).|Ja|
|_Calls.InitiateGroupCall.All_|Ausgehende Gruppenanrufe aus der App initiieren (Vorschau)|Ermöglicht der App, ausgehende Anrufe an mehrere Benutzer zu tätigen und Teilnehmer in Ihrer Organisation zu Besprechungen hinzufügen (ohne angemeldeten Benutzer).|Ja|
|_Calls.JoinGroupCall.All_|Gruppenanrufe und Besprechungen als App verknüpfen (Vorschau)|Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer zu verknüpfen. Die App wird mit den Berechtigungen eines Verzeichnisbenutzers und Besprechungen in Ihrem Mandanten verknüpft.|Ja|
|_Calls.JoinGroupCallasGuest.All_|Verknüpfen von Gruppenanrufen und Besprechungen als Gast (Vorschau)|Ermöglicht der App, Gruppenanrufe und geplante Besprechungen in Ihrer Organisation ohne einen angemeldeten Benutzer anonym zu verknüpfen. Die App wird als Gast mit Besprechungen in Ihrem Mandanten verknüpft.|Ja|
|_Calls. AccessMedia. all_ <sup> _siehe unten_</sup>|Auf Medienstreams in einem Anruf als App zugreifen (Vorschau)|Ermöglicht der App, direkten Zugriff auf Medienstreams in einem Anruf ohne einen angemeldeten Benutzer zu erhalten.|Ja|

> [!IMPORTANT]
> Sie **können** die Medien Zugriffs-API nicht verwenden, um Medieninhalte aus anrufen oder Besprechungen, auf die Ihre Anwendung zugreift, oder Daten, die von diesem Medieninhalt ("Record" oder "Recording") stammen, aufzuzeichnen oder anderweitig beizubehalten, ohne zuerst die [ `updateRecordingStatus` API](/graph/api/call-updaterecordingstatus) aufzurufen, um anzugeben, dass die Aufzeichnung begonnen hat, und eine Erfolgsantwort von dieser API erhalten. Wenn Ihre Anwendung mit der Aufzeichnung einer Besprechung/eines Anrufs beginnt, muss Sie die Aufzeichnung beenden, bevor Sie die API aufruft, `updateRecordingStatus` um anzugeben, dass die Aufzeichnung beendet wurde.

### <a name="application-permissions-online-meetings"></a>Anwendungsberechtigungen: Onlinebesprechungen

|Berechtigung    |Anzeigezeichenfolge   |Beschreibung |Administratorzustimmung erforderlich |
|:-----------------------------|:-----------------------------------------|:-----------------|:-----------------|
|_OnlineMeetings.Read.All_|Lesen von Onlinebesprechungsdetails aus der App (Vorschau)|Ermöglicht der App, Onlinebesprechungsdetails in Ihrer Organisation ohne einen angemeldeten Benutzer zu lesen.|Ja|
|_OnlineMeetings.ReadWrite.All_|Lesen und Erstellen von Onlinebesprechungen aus der App (Vorschau) im Namen eines Benutzers|Ermöglicht der App, Onlinebesprechungen in Ihrer Organisation im Namen eines Benutzers ohne einen angemeldeten Benutzer zu lesen.|Ja|

### <a name="assigning-permissions"></a>Zuweisen von Berechtigungen

Sie müssen die Anwendungsberechtigungen für Ihren bot im Voraus mithilfe des Azure- [Portals](https://aka.ms/aadapplist) konfigurieren, wenn Sie den [Azure AD v1-Endpunkt](/azure/active-directory/develop/azure-ad-endpoint-comparison)verwenden möchten.

### <a name="getting-tenant-administrator-consent"></a>Zustimmung zum mandantenadministrator wird abgerufen

Für apps, die den Azure AD v1-Endpunkt verwenden, kann ein mandantenadministrator die Berechtigungen der Anwendung mithilfe des [Azure-Portals](https://portal.azure.com) einwilligen, wenn Ihre APP in Ihrer Organisation installiert ist, oder Sie können eine Anmelde Erfahrung in Ihrer APP bereitstellen, über die Administratoren den von Ihnen konfigurierten Berechtigungen zustimmen können. Sobald die Zustimmung des Administrators von Azure AD aufgezeichnet wurde, kann Ihre APP Token anfordern, ohne erneut eine Zustimmung anfordern zu müssen.

Sie können sich darauf verlassen, dass ein Administrator die Berechtigungen, die Ihre APP benötigt, im [Azure-Portal](https://portal.azure.com)erteilt. häufig ist es jedoch besser, eine Anmelde Erfahrung für Administratoren mithilfe des Azure AD v2- `/adminconsent` Endpunkts bereitzustellen.  Weitere Informationen finden Sie in den [Anweisungen zum Erstellen einer URL für die Administrator Zustimmung](https://developer.microsoft.com/graph/docs/concepts/auth_v2_service#3-get-administrator-consent) .

> [!NOTE]
> Zum Erstellen der Zustimmungs-URL des Mandanten Administrators ist eine konfigurierte Umleitungs-URI/Antwort-URL im [App-Registrierungs Portal](https://apps.dev.microsoft.com/)erforderlich. Wenn Sie Antwort-URLs für Ihren bot hinzufügen möchten, greifen Sie auf Ihre bot-Registrierung zu, wählen Sie erweiterte Optionen – > Anwendungs Manifest bearbeiten.  Fügen Sie der Auflistung ihre Umleitungs-URL hinzu `replyUrls` .

> [!IMPORTANT]
> Wenn Sie eine Änderung an den Berechtigungen Ihrer Anwendung vornehmen, müssen Sie auch den Administrator Zustimmungsprozess wiederholen. Im App-Registrierungsportal vorgenommene Änderungen werden nicht wiedergegeben, bis die Zustimmung des Mandantenadministrators erneut erteilt wurde.
