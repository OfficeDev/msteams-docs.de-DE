---
title: Erstellen von Registerkarten für Besprechungen
author: surbhigupta
description: Erfahren Sie, wie Sie registerkarten für einen Besprechungschat, einen Besprechungsseitebereich und eine Besprechungsphase in Microsoft Teams-Besprechungen erstellen.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.date: 04/07/2022
ms.openlocfilehash: d86f0931cb6338ef331f2afe3a4a5fdb217bb316
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615431"
---
# <a name="build-tabs-for-meeting"></a>Erstellen von Registerkarten für Besprechungen

Jedes Team hat eine andere Art, zu kommunizieren und Aufgaben gemeinsam zu erledigen. Um diese verschiedenen Aufgaben zu erfüllen, passen Sie Teams mit Apps für Besprechungen an. Aktivieren Sie Ihre Apps für Teams-Besprechungen, und konfigurieren Sie die Apps so, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="tabs-in-teams-meetings"></a>Registerkarten in Teams-Besprechungen

Registerkarten ermöglichen es den Besprechungsteilnehmern, auf Dienste und Inhalte in einem bestimmten Bereich innerhalb einer Besprechung zuzugreifen. Wenn Sie mit der Entwicklung von Microsoft Teams-Registerkarten noch nicht fertig sind, lesen Sie [die Registerkarten "Erstellen" für Teams](/microsoftteams/platform/tabs/what-are-tabs).

Vor dem Erstellen einer Besprechungsregisterkarte ist es wichtig, sich über die Oberflächen zu informieren, die für die Besprechungschatansicht, die Besprechungsdetailsansicht, die Besprechungsseitenbereichsansicht und die Besprechungsphasenansicht verfügbar sind.

### <a name="meeting-details-view"></a>Ansicht "Besprechungsdetails"

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte " **Details** " und dann die Option :::image type="icon" source="../assets/icons/add-icon.png" Border = "false":::aus. Der App-Katalog wird angezeigt.

   :::image type="content" source="~/assets/images/apps-in-meetings/Pre-Meeting-002.png" alt-text="Dieser Screenshot zeigt die App-Erfahrung vor der Besprechung in Teams-Besprechungen.":::

1. Wählen Sie im App-Katalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die Registerkarte wird der Seite mit den Besprechungsdetails hinzugefügt.

# <a name="desktop"></a>[Desktop](#tab/desktop)

Die folgende Abbildung zeigt eine Registerkarte, die der Seite mit den Besprechungsdetails im Teams-Desktopclient hinzugefügt wurde:

   :::image type="content" source="~/assets/images/apps-in-meetings/PreMeetingTab.png" alt-text="Der Screenshot zeigt die Registerkarten &quot;Teams-Desktop&quot; in der Ansicht &quot;Besprechungsdetails&quot; in der Teams-Besprechung.":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Die folgende Abbildung zeigt eine Registerkarte, die der Besprechungsdetailseite im mobilen Microsoft Teams-Client hinzugefügt wurde:

   :::image type="content" source="../assets/images/mobile-tab.png" alt-text="Der Screenshot zeigt mobile Teams-Registerkarten in der Ansicht &quot;Besprechungsdetails&quot; in der Teams-Besprechung.":::

---

### <a name="meeting-chat-view"></a>Besprechungschatansicht

1. Wählen Sie im Teams-Chatbereich die Besprechungschatansicht aus.

1. Wählen Sie den App-Katalog aus :::image type="icon" source="../assets/icons/add-icon.png" Border = "false"::: , und der App-Katalog wird angezeigt.

1. Wählen Sie im App-Katalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die Registerkarte wird dem Besprechungschat hinzugefügt.

   :::image type="content" source="../assets/images/apps-in-meetings/meeting-chat-view.png" alt-text="Der Screenshot zeigt die Besprechungschatansicht in der Teams-Besprechung.":::

### <a name="meeting-side-panel-view"></a>Besprechungsseitige Bereichsansicht

1. Während einer Besprechung können Sie **Apps** aus dem Teams-Besprechungsfenster auswählen:::image type="icon" source="../assets/icons/add-icon.png" Border = "false":::, um der Besprechung Apps hinzuzufügen.

   :::image type="content" source="../assets/images/apps-in-meetings/add-app.png" alt-text="Dieser Screenshot zeigt, wie Sie eine App im Teams-Besprechungsfenster hinzufügen.":::

1. Wählen Sie im App-Katalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird dem Besprechungsseitenbereich hinzugefügt.

   :::image type="content" source="../assets/images/side-panel-view.png" alt-text="Dieser Screenshot zeigt die Seitenbereichsansicht mit der Liste der Apps.":::

### <a name="meeting-stage-view"></a>Besprechungsphasenansicht

1. Nachdem dem Besprechungsbereich eine Registerkarte hinzugefügt wurde, können Sie sich jetzt für die globale App-Freigabe entscheiden.

1. Dies führt dazu, dass die Registerkarte "Rendern" auf der Bühne für jeden Teilnehmer der Besprechung angezeigt wird.

   :::image type="content" source="../assets/images/meeting-stage-view.png" alt-text="Dieser Screenshot zeigt die Ansicht der Besprechungsphase der App, die Sie für die Besprechung freigegeben haben.":::

### <a name="apps-in-channel-meeting"></a>Apps in Kanalbesprechungen

Eine öffentliche geplante Kanalbesprechung verfügt über die gleiche Liste von Apps wie das übergeordnete Team. Durch das Installieren einer App in einer Kanalbesprechung wird sie auch im übergeordneten Team zur Verfügung gestellt und umgekehrt.

Die Registerkarteninstanzen in einer Kanalbesprechung sind jedoch von den Registerkarten im Kanal selbst getrennt. Angenommen, ein *Entwicklungskanal* verfügt über eine Registerkarte *"Polly* ". Wenn Sie eine *Standup-Besprechung* in diesem Kanal erstellen, hätte diese Besprechung erst dann eine Registerkarte " *Polly* ", wenn Sie [die Registerkarte der Besprechung explizit hinzufügen](#meeting-details-view).

In öffentlichen geplanten Kanalbesprechungen können Sie nach dem Hinzufügen einer Besprechungsregisterkarte das Besprechungsobjekt auf der Seite mit den Besprechungsdetails auswählen, um auf die Registerkarte zuzugreifen.

:::image type="content" source="~/assets/images/apps-in-meetings/after-a-meeting1.png" alt-text="Nach einer Besprechung":::

> [!NOTE]
> Auf mobilen Geräten können anonyme Benutzer in geplanten Besprechungen im öffentlichen Kanal nicht auf Apps zugreifen.

### <a name="app-manifest-settings-for-tabs-in-meeting"></a>App-Manifesteinstellungen für Registerkarten in Besprechungen

Aktualisieren Sie Ihr [App-Manifest](/microsoftteams/platform/resources/schema/manifest-schema) mit relevanter Kontexteigenschaft, um die verschiedenen Registerkartenansichten zu konfigurieren. Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe der Bereiche und Kontextarrays im Abschnitt "KonfigurierbareTabs" deklariert.

#### <a name="scope"></a>Bereich

Der Bereich definiert, wer auf die Apps zugreifen kann.

* `groupchat` der Bereich macht Ihre App in einem Gruppenbereich verfügbar und ermöglicht das Hinzufügen der App zu einem Anruf oder einer Besprechung (geplante private Besprechungen oder Sofortbesprechungen).

* `team` bereich macht Ihre App in einem Teambereich verfügbar und ermöglicht das Hinzufügen Ihrer App in Team- oder Kanalbesprechungen oder geplanten Kanalbesprechungen.

#### <a name="context"></a>Kontext

Die `context` Eigenschaft bestimmt, ob die App nach der Installation und Konfiguration in einer bestimmten Ansicht verfügbar ist. Es folgen die Werte für die `context` Eigenschaft, aus der Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern für eine geplante Besprechung. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf Mobilgeräten funktionieren. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Ansicht der Besprechungsdetails des Kalenders. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf Mobilgeräten funktionieren. |
| **meetingSidePanel** | Ein besprechungsinterner Bereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App aus dem `meetingSidePanel` kann im Freigabefenster angezeigt werden. Sie können diese App weder auf mobilen noch auf Microsoft Teams-Raum-Clients verwenden. |

#### <a name="configure-tab-app-for-a-meeting"></a>Konfigurieren der Registerkarten-App für eine Besprechung

Apps in Besprechungen können die folgenden Kontexte verwenden: `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel` und `meetingStage`. Nachdem ein Besprechungsteilnehmer eine App installiert und die Registerkarte in der Besprechung konfiguriert hat, beginnt das Rendern der Registerkarte in allen anderen Kontexten der App für die jeweilige Besprechung.

Der folgende Codeausschnitt ist ein Beispiel für eine konfigurierbare Registerkarte, die in einer App für Teams Besprechungen verwendet wird:

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team",
        "groupchat"
      ],
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

---

#### <a name="other-examples"></a>Weitere Beispiele

Der Standardkontext für Registerkarten (falls nicht angegeben) lautet:  

```json
"context":[ 
  "channelTab", 
  "privateChatTab", 
  "meetingChatTab", 
  "meetingDetailsTab" 
     ] 
```

Um zu verhindern, dass eine App in Gruppenchats ohne Besprechung angezeigt wird, müssen Sie den folgenden Kontext festlegen:

```json
"context":[ 
  "meetingSidePanel", 
  "meetingChatTab", 
  "meetingDetailsTab" 
     ] 
```

Nur für Besprechungsseite:For in-meeting side panel experience only:  

```json
"context":[ 
  "meetingSidePanel" 
     ] 
```

### <a name="advanced-tab-sdk-apis"></a>Erweiterte Registerkarten-SDK-APIs

Das Microsoft Teams JavaScript-Client-SDK ist ein umfangreiches SDK zum Erstellen von Registerkarten mit JavaScript. Verwenden Sie die neuesten TeamsJS (V.2.0 oder höher), um in Teams, Office und Outlook zu arbeiten. Weitere Informationen finden Sie unter [JavaScript-Client-SDK für Teams](/microsoftteams/platform/tabs/how-to/using-teams-client-sdk?tabs=javascript%2Cmanifest-teams-toolkit).

### <a name="frame-context"></a>Framekontext

Die JavaScript-Bibliothek von Microsoft Teams macht den frameContext verfügbar, in dem die URL Ihrer Besprechungsregisterkarte in der getContext-API geladen wird. Die möglichen Werte von frameContext sind Inhalt, Aufgabe, Einstellung, Entfernen, SidePanel und MeetingStage. Auf diese Weise können Sie angepasste Oberflächen basierend auf dem Renderort der App erstellen. Beispiel: Anzeigen einer bestimmten Benutzeroberfläche mit Relevanz für die Zusammenarbeit in der Benutzeroberfläche für die `meetingStage` Besprechungsvorbereitung auf der Registerkarte "Chat" (`content`). Weitere Informationen finden Sie unter [getContext API](/microsoftteams/platform/tabs/how-to/access-teams-context?tabs=teamsjs-v2).

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Besprechungs-App | Veranschaulicht, wie die Generator-App für Besprechungstoken verwendet wird, um ein Token anzufordern. Das Token wird sequenziell generiert, sodass jeder Teilnehmer eine angemessene Gelegenheit hat, in einer Besprechung mitzuwirken. Das Token ist in Situationen wie Scrum-Besprechungen und Q&A-Sitzungen nützlich. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Beispiel für Freigabefenster | Beispiel-App zum Anzeigen einer Registerkarte im Freigabefenster für die Zusammenarbeit | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
| Besprechungsseitenbereich | Beispiel-App zum zeigen, wie eine Agenda in einem Besprechungsseitenbereich hinzugefügt wird | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|
| Besprechungsinterne Benachrichtigung | Veranschaulicht die Implementierung von Benachrichtigungen in Besprechungen mithilfe eines Bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs) |
| Dokumentsignierung in der Besprechung | Veranschaulicht die Implementierung einer Teams-App zum Signieren von Dokumenten. Umfasst die Freigabe bestimmter App-Inhalte für die Stufe, teams-SSO und benutzerspezifische Phasenansicht. | [View](https://github.com/officedev/microsoft-teams-samples/tree/main/samples/meetings-share-to-stage-signing/csharp) | – |

> [!NOTE]
>
> * Besprechungs-Apps (Randbereich und Besprechungsphase) werden im Teams-Desktopclient unterstützt.
> * Besprechungs-Apps (Randbereich und Besprechungsphase) im Teams-Webclient werden nur unterstützt, wenn die [Entwicklervorschau aktiviert ist](/microsoftteams/platform/resources/dev-preview/developer-preview-intro#enable-developer-preview).

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../sbs-meeting-token-generator.yml), um in Ihrer Teams-Besprechung Besprechungstoken zu generieren.
* Befolgen Sie die schrittweise Anleitung zum Generieren des Besprechungsseitenbereichs in Ihrer [Teams-Besprechung](../sbs-meetings-sidepanel.yml) .
* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../sbs-meetings-stage-view.yml), um in Ihrer Teams-Besprechung die Freigabefensteransicht freizugeben.
* Befolgen Sie die schrittweise Anleitung zum Generieren von Benachrichtigungen in der Besprechung in Ihrer [Teams-Besprechung](../sbs-meeting-content-bubble.yml) .

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Benachrichtigungen in Besprechungen](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams-Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Entwurfsrichtlinien für die Erfahrung geteilter Freigabefenster](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Apps über Microsoft Graph zu Besprechungen hinzufügen](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
