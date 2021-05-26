---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
author: laujan
description: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
ms.topic: conceptual
ms.openlocfilehash: 3484e82f3f51a9a92da6588234744c42a86b5730
ms.sourcegitcommit: 1cc1516e71441f6f3f82b35868e21ba9933333cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52651733"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen

Jedes Team hat eine andere Möglichkeit, Aufgaben zu kommunizieren und zusammen zu arbeiten. Sie können diese verschiedenen Aufgaben ausführen, indem Sie Teams Apps für Besprechungen anpassen. Um unterschiedliche Aufgaben anpassen und ausführen zu können, müssen Sie Ihre Apps für Teams-Besprechungen aktivieren und Ihre Apps so konfigurieren, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams Besprechungen

Um Ihre App für Teams zu aktivieren, müssen Sie Ihr App-Manifest aktualisieren und die Kontexteigenschaften verwenden, um zu bestimmen, wo Ihre App angezeigt werden muss.

### <a name="update-your-app-manifest"></a>Aktualisieren Des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mit `configurableTabs` den Arrays , und `scopes` `context` deklariert. Scope definiert, für wen und der Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
> * Versuchen Sie, Ihr App-Manifest mit dem [Manifestschema zu aktualisieren.](../resources/schema/manifest-schema-dev-preview.md)
> * Apps in Besprechungen erfordern Gruppenchatbereich. Der Teambereich funktioniert nur für Registerkarten in Kanälen.

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
> `meetingStage` ist derzeit nur in [der Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

### <a name="context-property"></a>Context-Eigenschaft

Die Eigenschaft bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo der Benutzer `context` die App aufruft. Mit der `context` Registerkarte und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss. Registerkarten im `team` Bereich oder können mehrere `groupchat` Kontexte haben. Es folgen die Werte für die Eigenschaft, aus der Sie `context` alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetailsansicht des Kalenders. |
| **meetingSidePanel** | Ein In-Meeting-Panel, das über die einheitliche Leiste (U-Leiste) geöffnet wurde. |
| **meetingStage** | Eine App aus dem meetingSidePanel kann für die Besprechungsphase freigegeben werden. |

> [!NOTE]
> `Context` wird derzeit auf mobilen Clients nicht unterstützt.

Nachdem Sie Ihre App für Teams aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

> [!NOTE]
> * Damit Ihre App im Registerkartenkatalog angezeigt wird, muss sie konfigurierbare Registerkarten und den Gruppenchatbereich unterstützen.
> * Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen.
> * Die Besprechungserfahrungen, die im Dialogfeld "Besprechung" und "Registerkarte" angezeigt werden, werden derzeit auf mobilen Clients nicht unterstützt. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf Mobilgeräten](../tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten für Mobilgeräte.

Teams Besprechungen bieten eine einzigartige Zusammenarbeit für Ihre Organisation. Es bietet die Möglichkeit, Ihre App für verschiedene Besprechungsszenarien zu konfigurieren. Sie können Ihre Apps konfigurieren, um die Besprechungserfahrung basierend auf der Teilnehmerrolle oder dem Benutzertyp zu verbessern. Jetzt können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ergriffen werden können:
* [Pre-Meeting](#pre-meeting)
* [In-Meeting](#in-meeting)
* [Nach der Besprechung](#post-meeting)

### <a name="pre-meeting"></a>Pre-Meeting

Vor einer Besprechung können Benutzer Registerkarten, Bots und Messagingerweiterungen hinzufügen. Benutzer mit Organisator- und Organisatorrollen können einer Besprechung Registerkarten hinzufügen.

**So fügen Sie einer Besprechung eine Registerkarte hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die **Registerkarte Details** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. Wählen Sie im angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

    > [!NOTE]
    > Derzeit wird das Abrufen von Besprechungsdetails und Teilnehmerinformationen auf der Registerkarte Besprechungen nicht unterstützt.

**So fügen Sie einer Besprechung eine Messagingerweiterung hinzu**

1. Wählen Sie die ellipsen &#x25CF;&#x25CF;&#x25CF; , die sich im Bereich Verfassen von Nachrichten im Chat befinden.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus. Die App wird als Messagingerweiterung installiert.

**So fügen Sie einer Besprechung einen Bot hinzu**

Geben Sie in einem Besprechungschat den Schlüssel **@** ein, und wählen Sie **Bots erhalten aus.**

> [!NOTE]
> * Die Benutzeridentität muss mithilfe von [Tabs SSO bestätigt werden.](../tabs/how-to/authentication/auth-aad-sso.md) Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen. Beispielsweise ermöglicht eine Abruf-App nur Organisatoren und Organisatoren, eine neue Umfrage zu erstellen.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie unter [Rollen in einer Teams Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="in-meeting"></a>In-Meeting

Während einer Besprechung können Sie das meetingSidePanel oder das Dialogfeld in der Besprechung verwenden, um einzigartige Erfahrungen für Ihre Apps zu erstellen.

#### <a name="meetingsidepanel"></a>meetingSidePanel

Mit dem meetingSidePanel können Sie die Erfahrungen in einer Besprechung anpassen, mit denen Organisatoren und Organisatoren verschiedene Ansichten und Aktionen ermöglichen. In Ihrem App-Manifest müssen Sie meetingSidePanel dem Kontextarray hinzufügen. In der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die 320 Pixel breit ist. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Informationen zur Verwendung der `userContext` API zum Entsprechend routen von Anforderungen finden Sie unter Teams [SDK](../tabs/how-to/access-teams-context.md#user-context). Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Registerkarten können also OAuth 2.0 direkt verwenden. Weitere Informationen finden Sie [unter Microsoft Identity Platform und OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

Die Messagingerweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet und der Benutzer Nachrichtenerweiterungskarten verfassen kann. AppName in-meeting ist eine QuickInfo, in der der App-Name in der Besprechungs-U-Leiste steht.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)da die Versionen zuvor die Seitenleiste nicht unterstützen.

#### <a name="in-meeting-dialog-box"></a>Dialogfeld "Besprechungsdialogfeld"

Das Dialogfeld in der Besprechung kann verwendet werden, um Teilnehmer während der Besprechung zu engagieren und Während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie die [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API, um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss. Geben Sie im Rahmen der Nutzlast der Benachrichtigungsanforderung die URL an, in der der anzuzeigende Inhalt gehostet wird.

Im Besprechungsdialogfeld darf kein Aufgabenmodul verwendet werden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Eine externe Ressourcen-URL wird zum Anzeigen von Inhaltsblasen in einer Besprechung verwendet. Sie können die Methode `submitTask` verwenden, um Daten in einem Besprechungschat zu übermitteln.

> [!NOTE]
> * Sie müssen die [submitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat. Dies ist eine Anforderung für die App-Übermittlung. Weitere Informationen finden Sie unter [Teams SDK Task Module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
> * Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Nutzlast der ursprünglichen Aufrufanforderung auf den Anforderungsmetadaten im Objekt und nicht auf den `from.id` `from` `from.aadObjectId` Anforderungsmetadaten beruhen. `from.id`ist die Benutzer-ID und `from.aadObjectId` Azure Active Directory (AAD)-ID des Benutzers. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

#### <a name="share-to-stage"></a>Freigeben in der Phase

> [!NOTE]
> * Diese Funktion ist derzeit nur in der [Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.
> * Um dieses Feature verwenden zu können, muss die App ein MeetingSidePanel in Besprechungen unterstützen.

Mit dieser Funktion können Entwickler eine App für die Besprechungsphase freigeben. Durch aktivieren der Freigabe für die Besprechungsphase können Besprechungsteilnehmer in Echtzeit zusammenarbeiten.

Der erforderliche Kontext befindet `meetingStage` sich im App-Manifest. Voraussetzung dafür ist der `meetingSidePanel` Kontext. Dadurch wird **Share** im meetingSidePanel aktiviert.

![Freigeben an die Stufe während der Besprechungserfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

Die manifeste Änderung, die zum Aktivieren dieser Funktion erforderlich ist, lautet wie folgt:

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

Die Konfigurationen nach der Besprechung und [vor](#pre-meeting) der Besprechung sind identisch.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | Beispiel |
|----------------|-----------------|--------------|----------------|-----------|
| Besprechungs-App | Veranschaulicht, wie sie die App "Besprechungstokengenerator" zum Anfordern eines Tokens verwendet, das sequenziell generiert wird, damit jeder Teilnehmer eine gerechte Möglichkeit zur Interaktion hat. Dies kann in Situationen wie Scrum-Besprechungen, Fragen&A-Sitzungen und so weiter hilfreich sein. | [View](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token) |

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialogdialog](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
