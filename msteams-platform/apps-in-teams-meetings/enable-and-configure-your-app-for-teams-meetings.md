---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
author: surbhigupta
description: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: 1695b3e63a08935abd2db264ff171ebdf1d49fc3
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156400"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen

Jedes Team hat eine andere Art, Aufgaben zu kommunizieren und zusammenzuarbeiten. Um diese unterschiedlichen Aufgaben zu erreichen, passen Sie Teams mit Apps für Besprechungen an. Aktivieren Sie Ihre Apps für Teams Besprechungen, und konfigurieren Sie die Apps so, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams Besprechungen

Um Ihre App für Teams Besprechungen zu aktivieren, aktualisieren Sie Ihr App-Manifest, und verwenden Sie die Kontexteigenschaften, um zu bestimmen, wo Ihre App angezeigt werden muss.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe von `configurableTabs` `scopes` , und `context` Arrays deklariert. Der Bereich definiert, auf wen zugegriffen werden kann, und der Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
> * Sie müssen Ihr App-Manifest mit dem [Manifestschema](../resources/schema/manifest-schema-dev-preview.md)aktualisieren.
> * Apps in Besprechungen erfordern `groupchat` den Bereich. Der `team` Bereich funktioniert nur für Registerkarten in Kanälen.

Das App-Manifest muss den folgenden Codeausschnitt enthalten:

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

> [!NOTE]
> `meetingStage` ist derzeit nur in der [Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

### <a name="context-property"></a>Context-Eigenschaft

Die `context` Eigenschaft bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo der Benutzer die App aufruft. Mit der Registerkarte `context` und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss. Die Registerkarten im `team` Bereich `groupchat` können mehrere Kontexte aufweisen. Es folgen die Werte für die `context` Eigenschaft, aus der Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern für eine geplante Besprechung. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf mobilgeräten funktionieren. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetails-Ansicht des Kalenders. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf mobilgeräten funktionieren. |
| **meetingSidePanel** | Ein Besprechungsbereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App von der `meetingSidePanel` kann für die Besprechungsphase freigegeben werden. Sie können diese App nicht auf mobilgeräten verwenden. |

Nachdem Sie Ihre App für Teams Besprechungen aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

Teams Besprechungen bieten eine Zusammenarbeitserfahrung für Ihre Organisation. Konfigurieren Sie Ihre App für verschiedene Besprechungsszenarien, und verbessern Sie die Besprechungserfahrung. Jetzt können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ausgeführt werden können:

* [Vor einer Besprechung](#before-a-meeting)
* [Während einer Besprechung](#during-a-meeting)
* [Nach einer Besprechung](#after-a-meeting)

### <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung können Benutzer Registerkarten, Bots und Messaging-Erweiterungen hinzufügen. Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.

**So fügen Sie einer Besprechung eine Registerkarte hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **"Details"** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Wählen Sie im daraufhin angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

**So fügen Sie einer Besprechung eine Messaging-Erweiterung hinzu**

1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; aus, die sich im Bereich zum Verfassen von Nachrichten im Chat befinden.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus. Die App wird als Messaging-Erweiterung installiert.

**So fügen Sie einer Besprechung einen Bot hinzu**

Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen **Sie "Bots abrufen" aus.**

> [!NOTE]
> * Die Benutzeridentität muss mit [tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden. Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen. Eine Abruf-App ermöglicht beispielsweise nur Organisatoren und Referenten das Erstellen einer neuen Umfrage.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

### <a name="during-a-meeting"></a>Während einer Besprechung

Während einer Besprechung können Sie das `meetingSidePanel` Dialogfeld oder das In-Meeting-Dialogfeld verwenden, um einzigartige Erfahrungen für Ihre Apps zu erstellen.

#### <a name="meeting-sidepanel"></a>Sidepanel für Besprechungen

Dies ermöglicht ihnen das Anpassen von `meetingSidePanel` Erfahrungen in einer Besprechung, die Organisatoren und Referenten unterschiedliche Ansichten und Aktionen ermöglichen. Im App-Manifest müssen Sie `meetingSidePanel` dem Kontextarray hinzufügen. In der Besprechung und in allen Szenarien wird die App auf einer Besprechungsregisterkarte mit einer Breite von 320 Pixeln gerendert. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle.](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)

Informationen zur Verwendung der API zum Weiterleiten von `userContext` Anforderungen finden Sie unter Teams [SDK.](../tabs/how-to/access-teams-context.md#user-context) Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Registerkarten.](../tabs/how-to/authentication/auth-flow-tab.md) Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Registerkarten können daher OAuth 2.0 direkt verwenden. Weitere Informationen finden Sie unter [Microsoft Identity Platform und OAuth 2.0-Autorisierungscodefluss.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

Die Messaging-Erweiterung funktioniert erwartungsgemäß, wenn sich ein Benutzer in einer Besprechungsansicht befindet. Der Benutzer kann Erweiterungskarten zum Verfassen von Nachrichten posten. "AppName in-Meeting" ist eine QuickInfo, die den App-Namen in der Besprechungs-U-Leiste angibt.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)da die vorherigen Versionen den Seitenbereich nicht unterstützen.

#### <a name="in-meeting-dialog-box"></a>Dialogfeld "Besprechungsinterne Besprechung"

Das Dialogfeld in der Besprechung wird verwendet, um Teilnehmer während der Besprechung einzubeziehen und Während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie die [`NotificationSignal`](API-references.md#notificationsignal-api) API, um eine Blasenbenachrichtigung auszulösen. Fügen Sie als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, unter der der anzuzeigende Inhalt gehostet wird.

Das Besprechungsdialogfeld darf kein Aufgabenmodul verwenden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Eine externe Ressourcen-URL wird verwendet, um die Inhaltsblase in einer Besprechung anzuzeigen. Sie können die `submitTask` Methode verwenden, um Daten in einem Besprechungschat zu übermitteln.

> [!NOTE]
> * Sie müssen die [SubmitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submit-the-result-of-a-task-module) aufrufen, um sie automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat. Dies ist eine Anforderung für die App-Übermittlung. Weitere Informationen finden Sie unter [Teams SDK-Aufgabenmodul.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)
> * Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Anforderungsnutzlast für den ersten Aufruf auf `from.id` Anforderungsmetadaten im `from` Objekt basieren, nicht `from.aadObjectId` auf Anforderungsmetadaten. `from.id`ist die Benutzer-ID und `from.aadObjectId` die Azure Active Directory (AAD)-ID des Benutzers. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

#### <a name="shared-meeting-stage"></a>Freigegebene Besprechungsphase

> [!NOTE]
> Diese Funktion ist derzeit nur in der [Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die freigegebene Besprechungsphase ermöglicht es Besprechungsteilnehmern, in Echtzeit mit App-Inhalten zu interagieren und daran zusammenzuarbeiten.

Der erforderliche Kontext befindet `meetingStage` sich im App-Manifest. Voraussetzung ist, dass der Kontext vorhanden ist `meetingSidePanel` und die **Freigabe** in der `meetingSidePanel` .

![Freigeben für die Bereitstellung während der Besprechungserfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

Konfigurieren Sie ihr App-Manifest wie folgt, um die freigegebene Besprechungsphase zu aktivieren:

```json
"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "groupchat"
      ],
      "context":[
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

Erfahren Sie, wie Sie [eine gemeinsame Besprechungsphase entwerfen.](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen für Nach- und [Vorbesprechungen](#before-a-meeting) sind identisch.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | Beispiel |
|----------------|-----------------|--------------|----------------|-----------|
| Besprechungs-App | Veranschaulicht die Verwendung der Besprechungstoken-Generator-App zum Anfordern eines Tokens. Das Token wird sequenziell generiert, sodass jeder Teilnehmer eine angemessene Gelegenheit hat, an einer Besprechung mitzuwirken. Das Token ist nützlich in Situationen wie Meetings mit DerBesprechung und Q&A-Sitzungen. | [Anzeigen](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token) |

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialoge](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
