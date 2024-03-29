---
title: Aufgeklappte Registerkartenverknüpfung und Phasenansicht
author: Rajeshwari-v
description: Erfahren Sie mehr über die Phasenansicht, eine Vollbild-UI-Komponente, die aufgerufen wird, um Ihre Webinhalte anzuzeigen. Die Linkentflechtung wird verwendet, um URLs mithilfe von adaptiven Karten in eine Registerkarte umzuwandeln.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: 2563cfd266b967bd8c55c24491165c9979bad145
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820087"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Aufgeklappte Registerkartenverknüpfung und Phasenansicht

Die Phasenansicht ist eine neue Komponente der Benutzeroberfläche ( UI). Es ermöglicht Ihnen, den Inhalt zu rendern, der im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet wird.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

## <a name="stage-view"></a>Bühnenansicht

Die Bühnenansicht ist eine Vollbild-Benutzeroberflächenkomponente, die Sie aufrufen können, um Webinhalte anzuzeigen. Der vorhandene Link-Unfurling-Dienst wird aktualisiert, sodass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte umzuwandeln. Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird eine Vorschau der URL auf einer adaptiven Karte bereitgestellt. Der Benutzer kann auf **Ansicht** auf der Karte klicken und den Inhalt direkt aus der Bühnenansicht als Registerkarte anheften.

## <a name="advantage-of-stage-view"></a>Vorteile der Bühnenansicht

Stage View helps provide a more seamless experience of viewing content in Teams. Users can open and view the content provided by your app without leaving the context, and they can pin the content to the chat or channel for future quick access leading to a higher user engagement with your app.

## <a name="stage-view-vs-task-module"></a>Bühnenansicht im Vergleich zum Aufgabenmodul

|Bühnenansicht|Aufgabenmodul|
|:-----------|:-----------|
|Die Bühnenansicht ist nützlich, wenn den Benutzern vielfältige Inhalte angezeigt werden sollen, z. B. eine Seite, ein Dashboard, eine Datei usw. Es bietet umfangreiche Features, mit denen Sie Ihre Inhalte im Vollbildbereich rendern können.|[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzuzeigen, welche die Aufmerksamkeit des Benutzers erfordern, oder um Informationen zu sammeln, die für den nächsten Schritt erforderlich sind.|
  
## <a name="invoke-stage-view"></a>Die Bühnenansicht aufrufen

Sie können die Bühnenansicht auf folgende Weise aufrufen:

* [Aufrufen der Bühnenansicht über eine adaptive Karte](#invoke-stage-view-from-adaptive-card)
* [Aufrufen der Bühnenansicht über einen Deep-Link](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Aufrufen der Bühnenansicht über eine adaptive Karte

Wenn der Benutzer eine URL auf dem Microsoft Teams-Desktopclient eingibt, wird der Bot aufgerufen, welcher eine [adaptive Karte](../task-modules-and-cards/cards/cards-actions.md) mit der Option zum Öffnen der URL in der Bühnenansicht zurückgibt. Sie können die Möglichkeit hinzufügen, die Bühnenansicht als Registerkarte anzuheften, nachdem sie gestartet und `tabInfo` bereitgestellt wurde.  

Die folgenden Bilder zeigen eine Bühnenansicht, die über eine adaptive Karte geöffnet wurde:

:::image type="content" source="../assets/images/tab-images/open-stage-from-adaptive-card1.png" alt-text="Screenshot: Geöffnete Phase von adaptiver Karte"lightbox="~/assets/images/tab-images/open-stage-from-adaptive-card1.png":::

:::image type="content" source="../assets/images/tab-images/open-stage-from-adaptive-card2.png" alt-text="Screenshot: Geöffnete Phase von der Karte aus"lightbox="~/assets/images/tab-images/open-stage-from-adaptive-card2.png":::

### <a name="example"></a>Beispiel

Im Folgenden sehen Sie den Code zum Öffnen einer Bühnenansicht über eine adaptive Karte:

```json
{
    type: "Action.Submit",
    name: "View",
    data: {
          msteams: {
            type: "invoke",
            value: {
                type: "tab/tabInfoAction",
                tabInfo: {
                    contentUrl: contentUrl,
                    websiteUrl: websiteUrl,
                    name: "Tasks",
                    entityId: "entityId"
                 }
                }
            }
        }
} 
```

Der `invoke`-Anforderungstyp muss `composeExtension/queryLink` sein.

> [!NOTE]
>
> * Der `invoke`-Workflow ähnelt dem aktuellen `appLinking`-Workflow.
> * Zur Gewährleistung der Einheitlichkeit wird empfohlen, `Action.Submit` als `View` zu benennen.
> * `websiteUrl` ist eine erforderliche Eigenschaft, die im `TabInfo`-Objekt übergeben werden muss.

Im Folgenden sehen Sie den Ablauf zum Aufrufen der Bühnenansicht:

* When the user selects **View**, the bot receives an `invoke` request. The request type is `composeExtension/queryLink`.
* Die `invoke`-Antwort des Bots enthält eine adaptive Karte mit darin enthaltenem Typ `tab/tabInfoAction`.
* Der Bot antwortet mit einem `200`-Code.

> [!NOTE]
>
> Wenn Sie auf mobilen Teams-Clients die Phasenansicht für Apps aufrufen, die über den [Teams Store](~/concepts/deploy-and-publish/apps-publish-overview.md) verteilt werden und nicht über eine für Mobilgeräte optimierte Oberfläche verfügen, wird der Standardwebbrowser des Geräts geöffnet. Der Browser öffnet die im `websiteUrl`-Parameter des `TabInfo`-Objekts angegebene URL.

## <a name="invoke-stage-view-through-deep-link"></a>Aufrufen der Bühnenansicht über einen Deep-Link

Um die Bühnenansicht über einen Deep-Link von Ihrer Registerkarte aufzurufen, müssen Sie die Deep-Link-URL in der `app.openLink(url)`-API umschließen. Der Deep-Link kann auch durch eine `OpenURL`-Aktion auf der Karte übergeben werden.

### <a name="syntax"></a>Syntax

Im Folgenden finden Sie die Deep Link-Syntax:

`<https://teams.microsoft.com/l/stage/{appId}/0?context>={"contentUrl":"contentUrl","websiteUrl":"websiteUrl","name":"Contoso"}`

### <a name="examples"></a>Beispiele

Wenn ein Benutzer eine URL eingibt, wird sie in einer adaptiven Karte entladen.

Im Folgenden sind die Deep-Link-Beispiele zum Aufrufen der Bühnenansicht aufgeführt:

**Beispiel 1: URL mit threadId**

Nicht codierte URL:

`<https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context>={"contentUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191","websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes: Miscellaneous","threadId":"19:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2"}`

Codierte URL:

`<https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%2C%22threadId%22%3A%2219:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2%22%7D>`

**Beispiel 2: URL ohne threadId**

Nicht codierte URL:

`<https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context>={"contentUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191","websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes: Miscellaneous"}`

Codiert

`<https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%7D>`

> [!NOTE]
> Alle DeepLinks müssen vor dem Einfügen der URL codiert werden. Nicht codierte URLs werden nicht unterstützt.
>
> * `name` ist in Deep-Links optional. Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt.
> * Der Deep-Link kann auch durch eine `OpenURL`-Aktion übergeben werden.
> * Wenn Sie eine Bühnenansicht aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert. Wenn die Bühnenansicht beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App über einen persönlichen Bereich verfügt.

## <a name="tab-information-property"></a>Eigenschaften für Registerkarteninformationen

| Eigenschaftenname | Typ | Anzahl Zeichen | Beschreibung |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | Zeichenfolge | 64 | Diese Eigenschaft ist ein eindeutiger Bezeichner für die von der Registerkarte angezeigte Entität. Dies ist ein Pflichtfeld.|
| `name` | Zeichenfolge | 128 | Diese Eigenschaft ist der Anzeigename der Registerkarte auf der Kanaloberfläche. Dieses Feld ist optional.|
| `contentUrl` | Zeichenfolge | 2048 | This property is the https:// URL that points to the entity UI to be displayed in the Teams canvas. This is a required field.|
| `websiteUrl?` | Zeichenfolge | 2048 | This property is the https:// URL to point at, if a user selects to view in a browser. This is a required field.|
| `removeUrl?` | Zeichenfolge | 2048 | Diese Eigenschaft ist die https:// URL, die auf die Benutzeroberfläche verweist, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.|

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Registerkarte in der Bühnenansicht |Beispiel-App für Microsoft Teams-Registerkarten zum Demonstrieren einer Registerkarte in der Bühnenansicht.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Erstellen von Registerkarten für Teams](what-are-tabs.md)
* [Linkausweitung hinzufügen](../messaging-extensions/how-to/link-unfurling.md)
* [composeExtensions](../resources/schema/manifest-schema.md#composeextensions)
* [Erstellen von Registerkarten mit adaptiven Karten](how-to/build-adaptive-card-tabs.md)
* [Erstellen von Deep-Links](../concepts/build-and-test/deep-links.md)
