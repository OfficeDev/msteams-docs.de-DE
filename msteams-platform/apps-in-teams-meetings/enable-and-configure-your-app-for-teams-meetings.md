---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
author: surbhigupta
description: Aktivieren und konfigurieren Sie Ihre Apps für Teams Besprechungen und verschiedene Besprechungsszenarien, aktualisieren Sie das App-Manifest, konfigurieren Sie Features, z. B. In-Besprechungsdialogfeld, freigegebene Besprechungsphase, Besprechungsseite und vieles mehr
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: 1f77d0924eec9c52dc2f3d10566010c2953bd66b
ms.sourcegitcommit: 5201e7f390fbb2a9190cae1781c2f09e1746c8f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2022
ms.locfileid: "64820195"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a>Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen

Jedes Team hat eine andere Art, Aufgaben zu kommunizieren und zusammenzuarbeiten. Um diese verschiedenen Aufgaben zu erledigen, passen Sie Teams mit Apps für Besprechungen an. Aktivieren Sie Ihre Apps für Teams Besprechungen, und konfigurieren Sie die Apps so, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="prerequisites"></a>Voraussetzungen

Mit Apps für Teams Besprechungen können Sie die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus erweitern. Bevor Sie mit Apps für Teams Besprechungen arbeiten, müssen Sie die folgenden Voraussetzungen erfüllen:

* Erfahren Sie, wie Sie Teams Apps entwickeln. Weitere Informationen zum Entwickeln Teams App finden Sie [unter Teams App-Entwicklung](../overview.md).

* Verwenden Sie Ihre App, die konfigurierbare Registerkarten im Gruppenchatbereich unterstützt. Weitere Informationen finden Sie [im Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) , und [erstellen Sie eine Gruppenregisterkarte](../build-your-first-app/build-channel-tab.md).

* Halten Sie sich an allgemeine [Teams Richtlinien für den Registerkartenentwurf](../tabs/design/tabs.md) für Szenarien vor und nach der Besprechung. Informationen zu Erfahrungen während Besprechungen finden Sie [in den Entwurfsrichtlinien für die Registerkarte "In Besprechung"](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) und den [Entwurfsrichtlinien für das Dialogfeld "In-Besprechung"](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie auf der Grundlage der Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich im Dialogfeld "Besprechung" und in anderen Phasen des Besprechungslebenszyklus befinden. Informationen zum Dialogfeld "In der Besprechung" finden Sie `completionBotId` unter "Parameter in der [Benachrichtigungsnutzlast](API-references.md#send-an-in-meeting-notification) in der Besprechung".

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams Besprechungen

Um Ihre App für Teams Besprechungen zu aktivieren, aktualisieren Sie Ihr App-Manifest, und verwenden Sie die Kontexteigenschaften, um zu bestimmen, wo die App angezeigt werden muss.

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe von `configurableTabs`Arrays `scopes`und `context` Arrays deklariert. Der Bereich definiert, auf wen zugegriffen werden kann, und der Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
>
> * Sie müssen Ihr App-Manifest mit dem [Manifestschema](../resources/schema/manifest-schema-dev-preview.md) aktualisieren.
> * Apps in Besprechungen erfordern `groupchat` Einen Bereich. Der `team` Bereich funktioniert nur für Registerkarten in Kanälen.

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

Die `context` Eigenschaft bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo der Benutzer die App aufruft. Mit der Registerkarte `context` und `scopes` den Eigenschaften können Sie bestimmen, wo Ihre App angezeigt werden muss. Die Registerkarten im `team` Oder `groupchat` Bereich können mehrere Kontexte aufweisen.

Unterstützen Sie den `groupchat` Bereich, um Ihre App in Chats vor und nach der Besprechung zu aktivieren. Mit der App vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und die Aufgaben vor der Besprechung ausführen. Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Gebühren.

 Es folgen die Werte für die `context` Eigenschaft, aus der Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern für eine geplante Besprechung. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf Mobilgeräten funktionieren. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetailsansicht des Kalenders. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf Mobilgeräten funktionieren. |
| **meetingSidePanel** | Ein Besprechungsbereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App von der `meetingSidePanel` kann in die Besprechungsphase freigegeben werden. Sie können diese App weder auf mobilen noch auf Microsoft Teams-Raum-Clients verwenden. |

Nachdem Sie Ihre App für Teams Besprechungen aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

Teams Besprechungen bieten eine Zusammenarbeitserfahrung für Ihre Organisation. Konfigurieren Sie Ihre App für verschiedene Besprechungsszenarien, und verbessern Sie die Besprechungserfahrung. Jetzt können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ausgeführt werden können:

* [Vor einer Besprechung](#before-a-meeting)
* [Während einer Besprechung](#during-a-meeting)
* [Nach einer Besprechung](#after-a-meeting)

### <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung können Benutzer Registerkarten, Bots und Messaging-Erweiterungen hinzufügen. Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.

So fügen Sie einer Besprechung eine Registerkarte hinzu:

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte " **Details** " und dann <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Wählen Sie im angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

So fügen Sie einer Besprechung eine Messaging-Erweiterung hinzu:

1. Wählen Sie die Auslassungszeichen aus, &#x25CF;&#x25CF;&#x25CF; sich im Bereich "Nachricht verfassen" im Chat befinden.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Messaging-Erweiterung installiert.

So fügen Sie einen Bot zu einer Besprechung hinzu:

Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen Sie **"Bots abrufen" aus**.

> [!NOTE]
>
> * Die Inhaltsblase sendet eine adaptive Karte oder eine Karte gleichzeitig im Besprechungschat, auf die Benutzer zugreifen können. Dies hilft den Benutzern, wenn die Besprechung oder die Teams-App minimiert wird.
> * Die Benutzeridentität muss mit [tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md) bestätigt werden. Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Erfahrungen bereitstellen. Eine Abfrage-App ermöglicht beispielsweise nur Organisatoren und Referenten das Erstellen einer neuen Umfrage.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Während einer Besprechung

Während einer Besprechung können Sie die Benachrichtigung oder die Benachrichtigung in der `meetingSidePanel` Besprechung verwenden, um einzigartige Erfahrungen für Ihre Apps zu erstellen.

#### <a name="meeting-sidepanel"></a>Besprechungs-SidePanel

Auf `meetingSidePanel` diese Weise können Sie die Benutzeroberflächen in einer Besprechung anpassen, sodass Organisatoren und Referenten unterschiedliche Ansichten und Aktionen haben können. In Ihrem App-Manifest müssen Sie dem Kontextarray hinzufügen `meetingSidePanel` . In der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die 320 Pixel breit ist. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Informationen zur Verwendung der `userContext` API zum Weiterleiten von Anforderungen finden Sie [unter Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Weitere Informationen finden Sie [unter Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Registerkarten können OAuth 2.0 also direkt verwenden. Weitere Informationen finden Sie [unter Microsoft Identity Platform- und OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

Die Messaging-Erweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet. Der Benutzer kann Erweiterungskarten zum Verfassen von Nachrichten posten. AppName in der Besprechung ist eine QuickInfo, die den App-Namen in der Besprechungs-U-Leiste angibt.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), da versionen davor das Seitenpanel nicht unterstützen.

#### <a name="in-meeting-notification"></a>Benachrichtigung in der Besprechung

Die Benachrichtigung in der Besprechung wird verwendet, um Teilnehmer während der Besprechung einzubeziehen und während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie eine [Benachrichtigungsnutzlast](API-references.md#send-an-in-meeting-notification) in der Besprechung, um eine Benachrichtigung in der Besprechung auszulösen. Fügen Sie als Teil der Benachrichtigungsanforderungsnutzlast die URL hinzu, unter der der anzuzeigende Inhalt gehostet wird.

In der Besprechungsbenachrichtigung darf kein Aufgabenmodul verwendet werden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Eine externe Ressourcen-URL wird zum Anzeigen von Benachrichtigungen in der Besprechung verwendet. Sie können die `submitTask` Methode verwenden, um Daten in einem Besprechungschat zu übermitteln.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="Das Beispiel zeigt, wie Sie ein Dialogfeld in der Besprechung verwenden können." border="true":::

#### <a name="shared-meeting-stage"></a>Freigegebenes Besprechungsfreigabefenster

Die freigegebene Besprechungsphase ermöglicht es Besprechungsteilnehmern, in Echtzeit mit App-Inhalten zu interagieren und daran zusammenzuarbeiten. Sie können Ihre Apps auf folgende Weise für die Besprechungsphase für die Zusammenarbeit freigeben:

* [Teilen Sie die gesamte App mithilfe](#share-entire-app-to-stage) der Schaltfläche "Teilen in Stufe" in Teams Client.
* [Teilen Sie bestimmte Teile der App](#share-specific-parts-of-the-app-to-stage) mithilfe von APIs im Teams-Client-SDK.

##### <a name="share-entire-app-to-stage"></a>Teilen der gesamten App für die Stufe

Teilnehmer können die gesamte App für die Besprechungsphase der Zusammenarbeit freigeben, indem sie die Schaltfläche "Freigeben zur Stufe" aus dem App-Seitenbereich verwenden.

<img src="../assets/images/apps-in-meetings/share_to_stage_during_meeting.png" alt="Share full app" width = "900"/>

Um die gesamte App für die Phase freizugeben, müssen Sie im App-Manifest den Framekontext konfigurieren`meetingStage`.`meetingSidePanel` Beispiel:

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

Weitere Informationen finden Sie im [App-Manifest](../resources/schema/manifest-schema-dev-preview.md#configurabletabs).

##### <a name="share-specific-parts-of-the-app-to-stage"></a>Teilen bestimmter Teile der App für die Stufe

Teilnehmer können bestimmte Teile der App für die Besprechungsphase für die Zusammenarbeit freigeben, indem sie die Freigabe zum Bereitstellen von APIs verwenden. Die APIs sind im Teams Client SDK verfügbar und werden über den App-Seitenbereich aufgerufen.

<img src="../assets/images/apps-in-meetings/share-specific-content-to-stage.png" alt="Share specific parts of the app" width = "900"/>

Um bestimmte Teile der App für die Phase freizugeben, müssen Sie die zugehörigen APIs in der Teams Client SDK-Bibliothek aufrufen. Weitere Informationen finden Sie in der [API-Referenz](API-references.md).

> [!NOTE]
> * Verwenden Sie Teams Manifestversion 1.12 oder höher, um bestimmte Teile der App für die Phase freizugeben.
> * Das Freigeben bestimmter Teile der App wird nur für Teams Desktopclients unterstützt.

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen nach und [vor Besprechungen](#before-a-meeting) sind identisch.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|----------------|
| Besprechungs-App | Veranschaulicht die Verwendung der Besprechungstoken-Generator-App zum Anfordern eines Tokens. Das Token wird sequenziell generiert, sodass jeder Teilnehmer eine faire Gelegenheit hat, an einer Besprechung mitzuwirken. Das Token ist in Situationen wie Scrum-Besprechungen und Q&A-Sitzungen nützlich. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
|Beispiel für Besprechungsphase | Beispiel-App zum Anzeigen einer Registerkarte in der Besprechungsphase für die Zusammenarbeit | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
|Besprechungsseite | Beispiel-App zum Hinzufügen einer Tagesordnung in einem Besprechungsbereich | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [schrittweise Anleitung](../sbs-meeting-token-generator.yml), um Besprechungstoken in Ihrer Teams Besprechung zu generieren.
* Befolgen Sie die [schrittweise Anleitung zum Generieren von Besprechungs-Sidepanels](../sbs-meetings-sidepanel.yml) in Ihrer Teams Besprechung.
* Befolgen Sie die [schrittweise Anleitung](../sbs-meetings-stage-view.yml), um die Ansicht der Besprechungsphase in Ihrer Teams Besprechung freizugeben.
* Befolgen Sie die [schrittweise Anleitung](../sbs-meeting-content-bubble.yml), um Besprechungsinhaltsblasen in Ihrer Teams Besprechung zu generieren.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [API-Referenzen für Besprechungs-Apps](API-references.md)

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Das Dialogfeld "In Besprechung"](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Entwurfsrichtlinien für gemeinsame Besprechungsphasen](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Hinzufügen von Apps zu Besprechungen über Microsoft Graph](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
