---
title: Aufgeklappte Registerkartenverknüpfung und Phasenansicht
author: Rajeshwari-v
description: Erfahren Sie Näheres über die Vorschaugenerierung für Links, das Öffnen der Bühnenansicht und das Anheften einer Registerkarte mit der Microsoft Teams-App. Erfahren Sie mehr über die Bühnenansicht und deren Aufruf mithilfe einer adaptiven Karte anhand von Codebeispielen und Beispielen.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: medium
ms.openlocfilehash: 08df4cfccf6d9fabad1e07736796d6728d7c527c
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756737"
---
# <a name="tabs-link-unfurling-and-stage-view"></a>Aufgeklappte Registerkartenverknüpfung und Phasenansicht

Die Phasenansicht ist eine neue Benutzeroberflächenkomponente. Damit können Sie den Inhalt rendern, der im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet ist.

## <a name="stage-view"></a>Bühnenansicht

Die Bühnenansicht ist eine Vollbild-Benutzeroberflächenkomponente, die Sie aufrufen können, um Webinhalte anzuzeigen. Der vorhandene Link-Entknüpfungsdienst wird so aktualisiert, dass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte umzuwandeln. Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird eine Vorschau der URL auf einer adaptiven Karte bereitgestellt. Der Benutzer kann auf **Ansicht** auf der Karte klicken und den Inhalt direkt aus der Bühnenansicht als Registerkarte anheften.

## <a name="advantage-of-stage-view"></a>Vorteile der Bühnenansicht

Stage View sorgt für ein nahtloses Erlebnis beim Betrachten von Inhalten in Teams. Die Benutzer können die von Ihrer App bereitgestellten Inhalte öffnen und ansehen, ohne den Kontext zu verlassen, und sie können die Inhalte an den Chat oder den Kanal anheften, um später schnell darauf zugreifen zu können, was zu einem höheren Engagement der Benutzer mit Ihrer App führt.

## <a name="stage-view-vs-task-module"></a>Bühnenansicht im Vergleich zum Aufgabenmodul

|Bühnenansicht|Aufgabenmodul|
|:-----------|:-----------|
|Die Bühnenansicht ist nützlich, wenn den Benutzern vielfältige Inhalte angezeigt werden sollen, z. B. eine Seite, ein Dashboard, eine Datei usw. Sie bietet umfangreiche Features zum Rendern Ihrer Inhalte im Vollbildbereich.|[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzuzeigen, welche die Aufmerksamkeit des Benutzers erfordern, oder um Informationen zu sammeln, die für den nächsten Schritt erforderlich sind.|
  
## <a name="invoke-stage-view"></a>Die Bühnenansicht aufrufen

Sie können die Bühnenansicht auf folgende Weise aufrufen:

* [Aufrufen der Bühnenansicht über eine adaptive Karte](#invoke-stage-view-from-adaptive-card)
* [Aufrufen der Bühnenansicht über einen Deep-Link](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a>Aufrufen der Bühnenansicht über eine adaptive Karte

Wenn der Benutzer eine URL auf dem Microsoft Teams-Desktopclient eingibt, wird der Bot aufgerufen, welcher eine [adaptive Karte](../task-modules-and-cards/cards/cards-actions.md) mit der Option zum Öffnen der URL in der Bühnenansicht zurückgibt. Sie können die Möglichkeit hinzufügen, die Bühnenansicht als Registerkarte anzuheften, nachdem sie gestartet und `tabInfo` bereitgestellt wurde.  

Die folgenden Bilder zeigen eine Bühnenansicht, die über eine adaptive Karte geöffnet wurde:

[![Öffnen einer Bühnenansicht über eine adaptive Karte](~/assets/images/tab-images/open-stage-from-adaptive-card1.png)](~/assets/images/tab-images/open-stage-from-adaptive-card1.png#lightbox)

[![Öffnen einer Bühnenansicht](~/assets/images/tab-images/open-stage-from-adaptive-card2.png)](~/assets/images/tab-images/open-stage-from-adaptive-card2.png#lightbox)

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

* Wenn der Benutzer **Ansicht** wählt, erhält der Bot eine `invoke`Anfrage. Der Anfragetyp ist`composeExtension/queryLink`.
* Die `invoke`-Antwort des Bots enthält eine adaptive Karte mit darin enthaltenem Typ `tab/tabInfoAction`.
* Der Bot antwortet mit einem `200`-Code.

> [!NOTE]
> Auf mobilen Clients von Teams wird beim Aufrufen von Stage View für Apps, die über den [Teams Store](/platform/concepts/deploy-and-publish/apps-publish-overview.md) vertrieben werden und nicht für Mobilgeräte optimiert sind, der Standard-Webbrowser des Geräts geöffnet. Der Browser öffnet die im `websiteUrl`Parameter des `TabInfo`Objekts angegebene URL.

## <a name="invoke-stage-view-through-deep-link"></a>Aufrufen der Bühnenansicht über einen Deep-Link

Um die Bühnenansicht über einen Deep-Link von Ihrer Registerkarte aufzurufen, müssen Sie die Deep-Link-URL in der `microsoftTeams.executeDeeplink(url)`-API umschließen. Der Deep-Link kann auch durch eine `OpenURL`-Aktion auf der Karte übergeben werden.

### <a name="syntax"></a>Syntax

Die Deep-Link-Syntax sieht wie folgt aus:

https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"contentUrl","websiteUrl":"websiteUrl","name":"Contoso"}
 
### <a name="examples"></a>Beispiele

Wenn ein Benutzer eine URL eingibt, wird sie in eine adaptive Karte eingeblendet.

Im Folgenden sind die Deep-Link-Beispiele zum Aufrufen der Bühnenansicht aufgeführt:

**Beispiel 1: URL mit threadId**

Nicht codierte URL:

https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context={"contentUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191","websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes: Miscellaneous","threadId":"19:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2"}

Codierte URL:

https://teams.microsoft.com/l/stage/be411542-2bd5-46fb-8deb-a3d5f85156f6/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%2C%22threadId%22%3A%2219:9UryYW9rjwnq-vwmBcexGjN1zQSNX0Y4oEAgtUC7WI81@thread.tacv2%22%7D

**Beispiel 2: URL ohne threadId**

Nicht codierte URL:

https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context={"contentUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191","websiteUrl":"https://teams-alb.wakelet.com/teams/collection/e4173826-5dae-4de0-b77d-bfabafd6f191?standalone=true","title":"Quotes: Miscellaneous"}

Codiert

https://teams.microsoft.com/l/stage/43f56af0-8615-49e6-9635-7bea3b5802c2/0?context=%7B%22contentUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%22%2C%22websiteUrl%22%3A%22https%3A%2F%2Fteams-alb.wakelet.com%2Fteams%2Fcollection%2Fe4173826-5dae-4de0-b77d-bfabafd6f191%3Fstandalone%3Dtrue%22%2C%22title%22%3A%22Quotes%3A%20Miscellaneous%22%7D

> [!NOTE]
> Alle Deep-Links müssen vor dem Einfügen der URL codiert werden. Nicht codierte URLs werden nicht unterstützt.
>
> * `name` ist in Deep-Links optional. Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt.
> * Der Deep-Link kann auch durch eine `OpenURL`-Aktion übergeben werden.
> * Wenn Sie eine Bühnenansicht aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert. Wenn die Bühnenansicht beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App über einen persönlichen Bereich verfügt.

## <a name="tab-information-property"></a>Eigenschaften für Registerkarteninformationen

| Eigenschaftenname | Typ | Anzahl Zeichen | Beschreibung |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | Zeichenfolge | 64 | Diese Eigenschaft ist ein eindeutiger Bezeichner für die von der Registerkarte angezeigte Entität. Dies ist ein Pflichtfeld.|
| `name` | Zeichenfolge | 128 | Diese Eigenschaft ist der Anzeigename der Registerkarte auf der Kanaloberfläche. Dieses Feld ist optional.|
| `contentUrl` | Zeichenfolge | 2048 | Bei dieser Eigenschaft handelt es sich um die URL https://, die auf die Entitäts-UI verweist, die im Teams Canvas angezeigt werden soll. Dies ist ein Pflichtfeld.|
| `websiteUrl?` | Zeichenfolge | 2048 | Bei dieser Eigenschaft handelt es sich um die URL https://, auf die Sie verweisen, wenn ein Benutzer die Ansicht in einem Browser auswählt. Dies ist ein Pflichtfeld.|
| `removeUrl?` | Zeichenfolge | 2048 | Diese Eigenschaft ist die https:// URL, die auf die Benutzeroberfläche verweist, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.|

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Registerkarte in der Bühnenansicht |Beispiel-App für Microsoft Teams-Registerkarten zum Demonstrieren einer Registerkarte in der Bühnenansicht.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-stage-view/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)

## <a name="see-also"></a>Siehe auch

* [Link-Vorschaugenerierung für Nachrichtenerweiterungen](~/messaging-extensions/how-to/link-unfurling.md)
* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
