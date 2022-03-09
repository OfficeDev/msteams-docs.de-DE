---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
author: surbhigupta
description: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen und verschiedene Besprechungsszenarien, Aktualisieren des App-Manifests, Konfigurieren von Features wie In-Meeting-Dialog, freigegebener Besprechungsphase, Besprechungs-SidePanel und mehr
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: 160518c147ac2bc1d1378a3f1bd31fde9de1723c
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355800"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen

Jedes Team hat eine andere Art, Aufgaben zu kommunizieren und zusammenzuarbeiten. Um diese unterschiedlichen Aufgaben zu erreichen, passen Sie Teams mit Apps für Besprechungen an. Aktivieren Sie Ihre Apps für Teams Besprechungen, und konfigurieren Sie die Apps so, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams Besprechungen

Um Ihre App für Teams Besprechungen zu aktivieren, aktualisieren Sie Ihr App-Manifest, und verwenden Sie die Kontexteigenschaften, um zu bestimmen, wo Ihre App angezeigt werden muss.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe von `configurableTabs`, `scopes`und `context` Arrays deklariert. Der Bereich definiert, auf wen zugegriffen werden kann, und der Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
> * Sie müssen Ihr App-Manifest mit dem [Manifestschema](../resources/schema/manifest-schema-dev-preview.md) aktualisieren.
> * Apps in Besprechungen erfordern den `groupchat` Bereich. Der `team` Bereich funktioniert nur für Registerkarten in Kanälen.

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

### <a name="context-property"></a>Context-Eigenschaft

Die `context` Eigenschaft bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo der Benutzer die App aufruft. Mit der Registerkarte `context` und `scopes` den Eigenschaften können Sie bestimmen, wo Ihre App angezeigt werden muss. Die Registerkarten im `team` Bereich können `groupchat` mehrere Kontexte aufweisen. Es folgen die Werte für die `context` Eigenschaft, aus der Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern für eine geplante Besprechung. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf mobilgeräten funktionieren. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetails-Ansicht des Kalenders. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf mobilgeräten funktionieren. |
| **meetingSidePanel** | Ein Besprechungsbereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App von der `meetingSidePanel` kann für die Besprechungsphase freigegeben werden. Sie können diese App weder auf mobilen noch auf Microsoft Teams-Raum-Clients verwenden. |

Nachdem Sie Ihre App für Teams Besprechungen aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

Teams Besprechungen bieten eine Zusammenarbeit für Ihre Organisation. Konfigurieren Sie Ihre App für verschiedene Besprechungsszenarien, und verbessern Sie die Besprechungserfahrung. Jetzt können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ausgeführt werden können:

* [Vor einer Besprechung](#before-a-meeting)
* [Während einer Besprechung](#during-a-meeting)
* [Nach einer Besprechung](#after-a-meeting)

### <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung können Benutzer Registerkarten, Bots und Messaging-Erweiterungen hinzufügen. Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.

**So fügen Sie einer Besprechung eine Registerkarte hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **"Details** " aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Wählen Sie im daraufhin angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

**So fügen Sie einer Besprechung eine Messaging-Erweiterung hinzu**

1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; aus, die sich im Bereich zum Verfassen von Nachrichten im Chat befinden.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus. Die App wird als Messaging-Erweiterung installiert.

**So fügen Sie einer Besprechung einen Bot hinzu**

Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen **Sie "Bots abrufen" aus**.

> [!NOTE]
> * Die Inhaltsblase sendet eine adaptive Karte oder eine Karte gleichzeitig im Besprechungschat, auf den Benutzer zugreifen können. Dies hilft den Benutzern, wenn die Besprechung oder die Teams-App minimiert wird.
> * Die Benutzeridentität muss mit [tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md) bestätigt werden. Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen. Eine Abruf-App ermöglicht beispielsweise nur Organisatoren und Referenten das Erstellen einer neuen Umfrage.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie [unter Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Während einer Besprechung

Während einer Besprechung können Sie die Benachrichtigung oder Benachrichtigung innerhalb einer `meetingSidePanel` Besprechung verwenden, um einzigartige Erfahrungen für Ihre Apps zu erstellen.

#### <a name="meeting-sidepanel"></a>Meeting SidePanel

Dies `meetingSidePanel` ermöglicht ihnen das Anpassen von Erfahrungen in einer Besprechung, die Organisatoren und Referenten unterschiedliche Ansichten und Aktionen ermöglichen. Im App-Manifest müssen Sie dem Kontextarray hinzufügen `meetingSidePanel` . In der Besprechung und in allen Szenarien wird die App auf einer Besprechungsregisterkarte mit einer Breite von 320 Pixeln gerendert. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Informationen zur Verwendung der `userContext` API zum Weiterleiten von Anforderungen finden Sie [unter Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Registerkarten können daher OAuth 2.0 direkt verwenden. Weitere Informationen finden Sie unter [Microsoft Identity Platform und OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

Die Messaging-Erweiterung funktioniert erwartungsgemäß, wenn sich ein Benutzer in einer Besprechungsansicht befindet. Der Benutzer kann Erweiterungskarten zum Verfassen von Nachrichten posten. "AppName in-Meeting" ist eine QuickInfo, die den App-Namen in der Besprechungs-U-Leiste angibt.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), da die vorherigen Versionen den Seitenbereich nicht unterstützen.

#### <a name="in-meeting-notification"></a>In-Meeting-Benachrichtigung

Die In-Meeting-Benachrichtigung wird verwendet, um Teilnehmer während der Besprechung einzubeziehen und Informationen oder Feedback während der Besprechung zu sammeln. Verwenden Sie eine [In-Meeting-Benachrichtigungsnutzlast](API-references.md#send-an-in-meeting-notification) , um eine In-Meeting-Benachrichtigung auszulösen. Fügen Sie als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, unter der der anzuzeigende Inhalt gehostet wird.

In-Meeting-Benachrichtigungen dürfen kein Aufgabenmodul verwenden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Zum Anzeigen von In-Meeting-Benachrichtigungen wird eine externe Ressourcen-URL verwendet. Sie können die `submitTask` Methode verwenden, um Daten in einem Besprechungschat zu übermitteln.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld verwenden können." border="true":::

#### <a name="shared-meeting-stage"></a>Freigegebenes Besprechungsfreigabefenster

Die freigegebene Besprechungsphase ermöglicht es Besprechungsteilnehmern, in Echtzeit mit App-Inhalten zu interagieren und daran zusammenzuarbeiten. Sie können Ihre Apps auf folgende Weise für die Besprechungsphase für die Zusammenarbeit freigeben:

* [Teilen Sie die gesamte App in der Phase](#share-entire-app-to-stage) mithilfe der Schaltfläche "Freigabe für Phase" in Teams Client.
* [Teilen Sie bestimmte Teile der App, die](#share-specific-parts-of-the-app-to-stage) mithilfe von APIs im Teams-Client-SDK bereitgestellt werden sollen.

##### <a name="share-entire-app-to-stage"></a>Freigeben der gesamten App für die Phase

Teilnehmer können die gesamte App für die Besprechungsphase für die Zusammenarbeit freigeben, indem sie die Schaltfläche "Freigabe für Phase" aus dem App-Seitenbereich verwenden.

<img src="../assets/images/apps-in-meetings/share_to_stage_during_meeting.png" alt="Share full app" width = "900"/>

Um die gesamte App für die Phase freizugeben, müssen Sie im App-Manifest und `meetingSidePanel` als Framekontext konfigurieren`meetingStage`. Beispiel:

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

Weitere Informationen finden Sie unter [App-Manifest](../resources/schema/manifest-schema-dev-preview.md#configurabletabs). 

##### <a name="share-specific-parts-of-the-app-to-stage"></a>Freigeben bestimmter Teile der App für die Phasen

Teilnehmer können bestimmte Teile der App für die Gemeinsame Besprechungsphase freigeben, indem sie die APIs für die Freigabe in Phasen verwenden. Die APIs sind im Teams Client-SDK verfügbar und werden aus dem App-Seitenbereich aufgerufen.

<img src="../assets/images/apps-in-meetings/share-specific-content-to-stage.png" alt="Share specific parts of the app" width = "900"/>

Um bestimmte Teile der App für die Phasen freizugeben, müssen Sie die zugehörigen APIs in der Teams Client-SDK-Bibliothek aufrufen. Weitere Informationen finden Sie in der [API-Referenz](API-references.md).

Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Anforderungsnutzlast für den ersten Aufruf auf Anforderungsmetadaten im `from` Objekt basieren, nicht `from.aadObjectId` auf `from.id` Anforderungsmetadaten. `from.id`ist die Benutzer-ID und `from.aadObjectId` die Azure AD-ID des Benutzers. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen für Nach [- und Vorbesprechungen](#before-a-meeting) sind identisch.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Besprechungs-App | Veranschaulicht die Verwendung der Besprechungstoken-Generator-App zum Anfordern eines Tokens. Das Token wird sequenziell generiert, sodass jeder Teilnehmer eine angemessene Gelegenheit hat, an einer Besprechung mitzuwirken. Das Token ist nützlich in Situationen wie Meetings in DerBesprechung und Q&A-Sitzungen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
|Beispiel für Besprechungsphasen | Beispiel-App zum Anzeigen einer Registerkarte in der Besprechungsphase für die Zusammenarbeit | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
|Besprechungsseitiger Bereich | Beispiel-App zum Hinzufügen von Tagesordnungen in einem besprechungsseitigen Bereich | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [schrittweise Anleitung](../sbs-meeting-token-generator.yml), um Besprechungstoken in Ihrer Teams Besprechung zu generieren.
* Befolgen Sie die [schrittweise Anleitung zum Generieren von Besprechungs-Sidepanels](../sbs-meetings-sidepanel.yml) in Ihrer Teams Besprechung.
* Befolgen Sie die [schrittweise Anleitung](../sbs-meetings-stage-view.yml), um die Besprechungsphasenansicht in Ihrer Teams Besprechung zu generieren.
* Befolgen Sie die [schrittweise Anleitung](../sbs-meeting-content-bubble.yml), um eine Besprechungsinhaltsblase in Ihrer Teams Besprechung zu generieren.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [API-Referenzen für Besprechungs-Apps](API-references.md)

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialoge](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Entwurfsrichtlinien für gemeinsame Besprechungsphasen](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Hinzufügen von Apps zu Besprechungen über Microsoft Graph](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
