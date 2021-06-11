---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
author: laujan
description: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
ms.topic: conceptual
ms.openlocfilehash: 6542a8d1b4b8055d09585da4cf8c1194b5f293d7
ms.sourcegitcommit: 4751ca40f36ed21ec743b14483b181adade6b904
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "52871839"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen

Jedes Team hat eine andere Art, Aufgaben zu kommunizieren und zusammenzuarbeiten. Sie können diese verschiedenen Aufgaben erreichen, indem Sie Teams mit Apps für Besprechungen anpassen. Um unterschiedliche Aufgaben anzupassen und zu erreichen, müssen Sie Ihre Apps für Teams Besprechungen aktivieren und Ihre Apps so konfigurieren, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams Besprechungen

Um Ihre App für Teams Besprechungen zu aktivieren, müssen Sie Ihr App-Manifest aktualisieren und anhand der Kontexteigenschaften bestimmen, wo Ihre App angezeigt werden muss.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe von `configurableTabs` `scopes` , und `context` Arrays deklariert. Der Bereich definiert, für wen und welcher Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
> * Versuchen Sie, Das App-Manifest mit dem [Manifestschema](../resources/schema/manifest-schema-dev-preview.md)zu aktualisieren.
> * Apps in Besprechungen erfordern den Gruppenchatbereich. Der Teambereich funktioniert nur für Registerkarten in Kanälen.

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

Die `context` Eigenschaft bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo der Benutzer die App aufruft. Mit der Registerkarte `context` und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss. Registerkarten im `team` Oder Bereich können mehrere `groupchat` Kontexte aufweisen. Es folgen die Werte für die `context` Eigenschaft, aus der Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetails-Ansicht des Kalenders. |
| **meetingSidePanel** | Ein Besprechungsbereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App aus dem meetingSidePanel kann für die Besprechungsphase freigegeben werden. |

> [!NOTE]
> `Context` auf mobilen Clients wird derzeit nicht unterstützt.

Nachdem Sie Ihre App für Teams Besprechungen aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

> [!NOTE]
> * Damit Ihre App im Registerkartenkatalog sichtbar ist, müssen konfigurierbare Registerkarten und der Gruppenchatbereich unterstützt werden.
> * Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen.
> * Die Besprechungsumgebungen, die sich im Dialogfeld "Besprechung" und "Registerkarte" befinden, werden derzeit auf mobilen Clients nicht unterstützt. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilgeräten,](../tabs/design/tabs-mobile.md) während Sie Ihre Registerkarten für mobilgeräte erstellen.

Teams Besprechungen bietet eine einzigartige Umgebung für die Zusammenarbeit in Ihrer Organisation. Es bietet die Möglichkeit, Ihre App für verschiedene Besprechungsszenarien zu konfigurieren. Sie können Ihre Apps so konfigurieren, dass die Besprechungserfahrung basierend auf der Teilnehmerrolle oder dem Benutzertyp verbessert wird. Jetzt können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ausgeführt werden können:
* [Vor der Besprechung](#pre-meeting)
* [Besprechungsbesprechung](#in-meeting)
* [Nach der Besprechung](#post-meeting)

### <a name="pre-meeting"></a>Vor der Besprechung

Vor einer Besprechung können Benutzer Registerkarten, Bots und Messaging-Erweiterungen hinzufügen. Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.

**So fügen Sie einer Besprechung eine Registerkarte hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **"Details"** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. Wählen Sie im daraufhin angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

    > [!NOTE]
    > Derzeit wird das Abrufen von Besprechungsdetails und Teilnehmerinformationen auf der Registerkarte "Besprechungen" nicht unterstützt.

**So fügen Sie einer Besprechung eine Messaging-Erweiterung hinzu**

1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; aus, die sich im Bereich zum Verfassen von Nachrichten im Chat befinden.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus. Die App wird als Messaging-Erweiterung installiert.

**So fügen Sie einer Besprechung einen Bot hinzu**

Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen **Sie "Bots abrufen" aus.**

> [!NOTE]
> * Die Benutzeridentität muss mit [tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden. Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen. Eine Abruf-App ermöglicht beispielsweise nur Organisatoren und Referenten das Erstellen einer neuen Umfrage.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

### <a name="in-meeting"></a>Besprechungsbesprechung

Während einer Besprechung können Sie das meetingSidePanel oder das Dialogfeld in der Besprechung verwenden, um einzigartige Umgebungen für Ihre Apps zu erstellen.

#### <a name="meetingsidepanel"></a>meetingSidePanel

Mit dem meetingSidePanel können Sie Benutzeroberflächen in einer Besprechung anpassen, die Organisatoren und Referenten unterschiedliche Ansichten und Aktionen ermöglichen. In Ihrem App-Manifest müssen Sie meetingSidePanel dem Kontextarray hinzufügen. In der Besprechung und in allen Szenarien wird die App auf einer Besprechungsregisterkarte mit einer Breite von 320 Pixeln gerendert. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle.](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)

Informationen zur Verwendung der API zum weiterleiten von `userContext` Anforderungen finden Sie unter Teams [SDK.](../tabs/how-to/access-teams-context.md#user-context) Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Registerkarten.](../tabs/how-to/authentication/auth-flow-tab.md) Der Authentifizierungsfluss für Registerkarten ist dem Authentifizierungsfluss für Websites sehr ähnlich. Registerkarten können daher OAuth 2.0 direkt verwenden. Weitere Informationen finden Sie unter [Microsoft Identity Platform und OAuth 2.0-Autorisierungscodefluss.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

Die Messaging-Erweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet und der Benutzer Erweiterungskarten zum Verfassen von Nachrichten posten kann. "AppName in-Meeting" ist eine QuickInfo, die den App-Namen in der Besprechungs-U-Leiste angibt.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)da versionen zuvor den Seitenbereich nicht unterstützen.

#### <a name="in-meeting-dialog-box"></a>Dialogfeld "Besprechungsinterne Besprechung"

Das Dialogfeld in der Besprechung kann verwendet werden, um Teilnehmer während der Besprechung einzubeziehen und Während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie die [`NotificationSignal`](create-apps-for-teams-meetings.md#notificationsignal-api) API, um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss. Fügen Sie als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, unter der der anzuzeigende Inhalt gehostet wird.

Das Besprechungsdialogfeld darf kein Aufgabenmodul verwenden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Eine externe Ressourcen-URL wird verwendet, um Inhaltsblase in einer Besprechung anzuzeigen. Sie können die `submitTask` Methode verwenden, um Daten in einem Besprechungschat zu übermitteln.

> [!NOTE]
> * Sie müssen die [SubmitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um sie automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat. Dies ist eine Anforderung für die App-Übermittlung. Weitere Informationen finden Sie unter [Teams SDK-Aufgabenmodul.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)
> * Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss ihre anfängliche Aufrufanforderungsnutzlast auf den `from.id` Anforderungsmetadaten im `from` Objekt basieren, nicht auf den `from.aadObjectId` Anforderungsmetadaten. `from.id`ist die Benutzer-ID und `from.aadObjectId` die Azure Active Directory -ID (AAD) des Benutzers. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

#### <a name="share-to-stage"></a>Freigeben in der Phase

> [!NOTE]
> * Diese Funktion ist derzeit nur in der [Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.
> * Um dieses Feature zu verwenden, muss die App ein Besprechungs-MeetingSidePanel unterstützen.

Diese Funktion bietet Entwicklern die Möglichkeit, eine App für die Besprechungsphase freizugeben. Durch Aktivieren der Freigabe für die Besprechungsphase können Besprechungsteilnehmer in Echtzeit zusammenarbeiten.

Der erforderliche Kontext befindet `meetingStage` sich im App-Manifest. Voraussetzung hierfür ist, dass der Kontext vorhanden `meetingSidePanel` ist. Dadurch wird **"Freigeben** im meetingSidePanel" aktiviert.

![Freigeben für die Bereitstellung während der Besprechungserfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

Die Manifeständerung, die zum Aktivieren dieser Funktion erforderlich ist, lautet wie folgt:

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

### <a name="post-meeting"></a>Nach der Besprechung

Die Konfigurationen nach der Besprechung und vor der [Besprechung](#pre-meeting) sind identisch.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | Beispiel |
|----------------|-----------------|--------------|----------------|-----------|
| Besprechungs-App | Veranschaulicht, wie die Besprechungstoken-Generator-App verwendet wird, um ein Token anzufordern, das sequenziell generiert wird, sodass jeder Teilnehmer eine angemessene Möglichkeit zur Interaktion hat. Dies kann in Situationen wie Beibesprechungen, Q&A-Sitzungen usw. hilfreich sein. | [View](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token) |

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialoge](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
