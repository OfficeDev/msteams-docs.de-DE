---
title: Senden und Empfangen von Dateien von einem Bot
description: Erfahren Sie, wie Sie Dateien über den Bot senden und empfangen, indem Sie Graph-APIs für persönliche, Kanal- und Gruppenchatbereiche verwenden. Verwenden Sie Teams-Bot-APIs unter Verwendung von Codebeispielen, die auf dem v3 Bot Framework SDK basieren.
keywords: Senden und Empfangen von Teams-Bots-Dateien
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 5d7b83890947a77a477c67197557c92aa6e7b103
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503585"
---
# <a name="send-and-receive-files-using-bots"></a>Senden und Empfangen von Dateien mithilfe von Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Es gibt zwei Möglichkeiten zum Senden von Dateien an und von einem Bot:

* Verwenden der Microsoft Graph-APIs Diese Methode funktioniert für Bots in allen Bereichen in Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Verwenden der Teams-APIs Diese unterstützen nur Dateien in einem Kontext:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Verwenden der Microsoft Graph-APIs

Sie können Nachrichten mit Kartenanlagen, die auf vorhandene SharePoint-Dateien verweisen, mithilfe der Microsoft Graph-APIs für [OneDrive und SharePoint](/onedrive/developer/rest-api/) posten. Die Verwendung der Graph-APIs erfordert den Zugriff auf den OneDrive-Ordner eines Benutzers (für `personal`- und `groupchat`-Dateien) oder die Dateien in den Kanälen eines Teams (für `channel`-Dateien) über den standardmäßigen OAuth 2.0-Autorisierungsfluss. Diese Methode funktioniert in allen Teams-Bereichen.

## <a name="using-the-teams-bot-apis"></a>Verwenden der Teams-Bot-APIs

> [!NOTE]
> Diese Methode funktioniert nur im `personal`-Kontext. Sie funktioniert weder im `channel`- noch im `groupchat`-Kontext.

Mit Teams-APIs kann der Bot Dateien an Benutzer im `personal`-Kontext, auch als persönliche Chats bezeichnet, direkt senden und von diesen empfangen. Auf diese Weise können Sie Spesenabrechnung, Bilderkennung, Dateiarchivierung, E-Signaturen und andere Szenarien implementieren, die eine direkte Bearbeitung von Dateiinhalten beinhalten. In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.

In den folgenden Abschnitten wird beschrieben, wie Sie dies tun, um Dateiinhalte als Ergebnis direkter Benutzerinteraktion, wie das Versenden einer Nachricht, zu versenden. Diese API wird als Teil der Microsoft Teams-Bot-Plattform bereitgestellt.

### <a name="configure-your-bot-to-support-files"></a>Konfigurieren Ihres Bots zur Unterstützung von Dateien

Um Dateien in Ihrem Bot zu senden und zu empfangen, müssen Sie die `supportsFiles`-Eigenschaft im Manifest auf `true`festlegen. Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifestreferenz beschrieben.

Die Definition sieht wie folgt aus: `"supportsFiles": true`. Wenn Ihr Bot nicht aktiviert `supportsFiles`ist, funktionieren die folgenden Features nicht.

### <a name="receiving-files-in-personal-chat"></a>Empfangen von Dateien im persönlichen Chat

Wenn ein Benutzer eine Datei an Ihren Bot sendet, wird die Datei zuerst in den OneDrive for Business-Speicher des Benutzers hochgeladen. Ihr Bot erhält dann eine Nachrichtenaktivität, die Sie über den Benutzerupload informiert. Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL. Sie können direkt aus dieser URL lesen, um den binären Inhalt abzurufen.

#### <a name="message-activity-with-file-attachment-example"></a>Beispiel für Nachrichtenaktivität mit Dateianlage

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.file.download.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "downloadUrl" : "https://download.link",
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C9D",
      "fileType": "txt",
      "etag": "123"
    }
  }]
}
```

In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:

| Eigenschaft | Zweck |
| --- | --- |
| `downloadUrl` | OneDrive-URL zum Abrufen des Dateiinhalts Sie können eine `HTTP GET` direkt über diese URL ausgeben. |
| `uniqueId` | Eindeutige Datei-ID Dies ist die OneDrive-Laufwerkelement-ID, wenn der Benutzer eine Datei an Ihren Bot sendet. |
| `fileType` | Dateierweiterungstyp, z. B. pdf oder docx. |

In der Regel sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer senden.

### <a name="uploading-files-to-personal-chat"></a>Hochladen von Dateien in einen persönlichen Chat

Das Hochladen einer Datei für einen Benutzer umfasst die folgenden Schritte:

1. Senden Sie eine Nachricht an den Benutzer, in der Sie um die Berechtigung zum Schreiben der Datei bitten. Diese Nachricht muss eine `FileConsentCard`-Anlage mit dem Namen der hochzuladenden Datei enthalten.
2. Wenn der Benutzer den Dateidownload akzeptiert, empfängt Ihr Bot eine *Aufrufaktivität* mit einer Standort-URL.
3. Um die Datei zu übertragen, führt Ihr Bot einen `HTTP POST` direkt in die angegebene Speicherort-URL aus.
4. Optional können Sie die ursprüngliche Zustimmungskarte entfernen, wenn Sie dem Benutzer nicht erlauben möchten, weitere Uploads derselben Datei zu akzeptieren.

#### <a name="message-requesting-permission-to-upload"></a>Nachricht für die Anforderung der Berechtigung zum Hochladen

Diese Desktopnachricht enthält ein einfaches Anlageobjekt, in dem der Benutzer um die Berechtigung zum Hochladen der Datei gebeten wird:

:::image type="content" source="../../assets/images/bots/bot-file-consent-card.png" alt-text="Screenshot der Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei anfordert" border="true":::

Die mobile Nachricht enthält ein Anlageobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:

![Screenshot der Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei auf einem Mobilgerät anfordert](../../assets/images/bots/mobile-bot-file-consent-card.png)

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.consent",
    "name": "file_example.txt",
    "content": {
      "description": "<Purpose of the file, such as: this is your monthly expense report>",
      "sizeInBytes": 1029393,
      "acceptContext": {
      },
      "declineContext": {
      }
    }
  }]
}
```

In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:

| Eigenschaft | Zweck |
| --- | --- |
| `description` | Beschreibung der Datei Kann dem Benutzer angezeigt werden, um den Zweck zu beschreiben oder den Inhalt zusammenzufassen. |
| `sizeInBytes` | Bietet dem Benutzer eine Schätzung der Dateigröße und des in OneDrive benötigten Platzes. |
| `acceptContext` | Zusätzlicher Kontext, der automatisch an Ihren Bot übertragen wird, wenn der Benutzer die Datei akzeptiert. |
| `declineContext` | Zusätzlicher Kontext, der automatisch an Ihren Bot übertragen wird, wenn der Benutzer die Datei ablehnt. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Aufrufaktivität, wenn der Benutzer die Datei akzeptiert

Eine Aufrufaktivität wird an Ihren Bot gesendet, wenn der Benutzer die Datei akzeptiert. Sie enthält die OneDrive for Business-Platzhalter-URL, damit Ihr Bot dann eine `PUT` ausstellen kann, um den Dateiinhalt zu übertragen. Informationen zum Hochladen in die OneDrive-URL finden Sie im Artikel [Hochladen von Bytes in die Uploadsitzung](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

Das folgende Beispiel zeigt eine gekürzte Version der Aufrufaktivität, die Ihr Bot empfängt:

```json
{
  ...

  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "accept",
    "context": {
    },
    "uploadInfo": {
      "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
      "name": "file_example.txt",
      "uploadUrl": "https://upload.link",
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C8C",
      "fileType": "txt",
      "etag": "123"
    }
  }
}
```

Wenn der Benutzer die Datei ablehnt, erhält Ihr Bot entsprechend das folgende Ereignis mit demselben allgemeinen Aktivitätsnamen:

```json
{
  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "decline",
    "context": {
    }
  }
}
```

### <a name="notifying-the-user-about-an-uploaded-file"></a>Benachrichtigen des Benutzers über eine hochgeladene Datei

Nachdem Sie eine Datei in die OneDrive-Instanz des Benutzers hochgeladen haben, sollten Sie unabhängig davon, ob Sie den oben beschriebenen Mechanismus oder benutzerdelegierte OneDrive-APIs verwenden, eine Bestätigungsmeldung an den Benutzer senden. Diese Nachricht sollte eine `FileCard` Anlage enthalten, die der Benutzer auswählen kann, um entweder eine Vorschau anzuzeigen, sie in OneDrive zu öffnen oder lokal herunterzuladen.

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "uniqueId": "1150D938-8870-4044-9F2C-5BBDEBA70C8C",
      "fileType": "txt",
    }
  }]
}
```

In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:

| Eigenschaft | Zweck |
| --- | --- |
| `uniqueId` | OneDrive-/SharePoint-Laufwerkelement-ID |
| `fileType` | Dateityp, z. B. pdf oder docx. |

### <a name="basic-example-in-c"></a>Einfaches Beispiel in C #

Das folgende Beispiel zeigt, wie Sie Dateiuploads verarbeiten und Dateizustimmungsanforderungen im Dialogfeld Ihres Bots senden können:

```csharp

// This sample dialog shows two simple flows:
// 1) A silly example of receiving a file from the user, processing the key elements,
//    and then constructing the attachment and sending it back.
// 2) Creating a new file consent card requesting user permission to upload a file.
private async Task MessageReceivedAsync(IDialogContext context, IAwaitable<object> result)
{
    var replyMessage = context.MakeMessage();
    Attachment returnCard;

    var message = await result as Activity;

    // Check to see if the user is sending the bot a file.
    if (message.Attachments != null && message.Attachments.Any())
    {
        var attachment = message.Attachments.First();

        if (attachment.ContentType == FileDownloadInfo.ContentType)
        {
            FileDownloadInfo downloadInfo = (attachment.Content as JObject).ToObject<FileDownloadInfo>();
            if (downloadInfo != null)
            {
                returnCard = CreateFileInfoAttachment(downloadInfo, attachment.Name, attachment.ContentUrl);
                replyMessage.Attachments.Add(returnCard);
            }
        }
    }
    else
    {
        // Illustrates creating a file consent card.
        returnCard = CreateFileConsentAttachment();
        replyMessage.Attachments.Add(returnCard);
    }
    await context.PostAsync(replyMessage);
}


private static Attachment CreateFileInfoAttachment(FileDownloadInfo downloadInfo, string name, string contentUrl)
{
    FileInfoCard card = new FileInfoCard()
    {
        FileType = downloadInfo.FileType,
        UniqueId = downloadInfo.UniqueId
    };

    Attachment att = card.ToAttachment();
    att.ContentUrl = contentUrl;
    att.Name = name;

    return att;
}

private static Attachment CreateFileConsentAttachment()
{
    JObject acceptContext = new JObject();
    // Fill in any additional context to be sent back when the user accepts the file.

    JObject declineContext = new JObject();
    // Fill in any additional context to be sent back when the user declines the file.

    FileConsentCard card = new FileConsentCard()
    {
        AcceptContext = acceptContext,
        DeclineContext = declineContext,
        SizeInBytes = 102635,
        Description = "File description"
    };

    Attachment att = card.ToAttachment();
    att.Name = "Example file";

    return att;
}
```

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Dateien in Microsoft Graph](/graph/api/resources/onedrive)
