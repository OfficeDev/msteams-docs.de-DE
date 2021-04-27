---
title: Senden und Empfangen von Dateien von einem Bot
description: Beschreibt das Senden und Empfangen von Dateien von einem Bot
keywords: teams bots files send receive
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: c5ee32d10e5a6adc5a08d1a0556a18be8367460a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020653"
---
# <a name="send-and-receive-files-through-your-bot"></a>Senden und Empfangen von Dateien über Ihren Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Es gibt zwei Möglichkeiten zum Senden von Dateien an und von einem Bot:

* Verwenden der Microsoft Graph-APIs. Diese Methode funktioniert für Bots in allen Bereiche in Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Verwenden der Teams-APIs. Diese unterstützen nur Dateien in einem Kontext:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Verwenden der Microsoft Graph-APIs

Sie können Nachrichten mit Kartenanlagen posten, die auf vorhandene #A0 verweisen, indem Sie die Microsoft Graph-APIs für [OneDrive und SharePoint verwenden.](/onedrive/developer/rest-api/) Die Verwendung der Graph-APIs erfordert den Zugriff auf den #A0 eines Benutzers (für und Dateien) oder die Dateien in den Kanälen eines Teams (für Dateien) über den standardmäßigen `personal` `groupchat` `channel` OAuth 2.0-Autorisierungsfluss. Diese Methode funktioniert in allen Teams-Bereich.

## <a name="using-the-teams-bot-apis"></a>Verwenden der Teams Bot-APIs

> [!NOTE]
> Diese Methode funktioniert nur im `personal` Kontext. Es funktioniert nicht im `channel` `groupchat` Oder-Kontext.

Ihr Bot kann Dateien mit Benutzern im Kontext, auch als persönliche Chats bezeichnet, mithilfe von `personal` Teams-APIs direkt senden und empfangen. Auf diese Weise können Sie Spesenabrechnung, Bilderkennung, Dateiarchivierung, E-Signaturen und andere Szenarien implementieren, in denen Dateiinhalte direkt manipuliert werden. In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.

In den folgenden Abschnitten wird beschrieben, wie Sie dies tun, um Dateiinhalte als Ergebnis einer direkten Benutzerinteraktion, z. B. das Senden einer Nachricht, zu senden. Diese API wird als Teil der Microsoft Teams Bot Platform bereitgestellt.

### <a name="configure-your-bot-to-support-files"></a>Konfigurieren des Bots für die Unterstützung von Dateien

Zum Senden und Empfangen von Dateien in Ihrem Bot müssen Sie die `supportsFiles` Eigenschaft im Manifest auf `true` festlegen. Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifestreferenz beschrieben.

Die Definition sieht wie dies aus: `"supportsFiles": true` . Wenn Ihr Bot nicht aktiviert `supportsFiles` ist, funktionieren die folgenden Features nicht.

### <a name="receiving-files-in-personal-chat"></a>Empfangen von Dateien in persönlichen Chats

Wenn ein Benutzer eine Datei an Ihren Bot sendet, wird die Datei zuerst in den OneDrive for #A0 des Benutzers hochgeladen. Ihr Bot erhält dann eine Nachrichtenaktivität, die Sie über den Benutzerupload informiert. Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL. Sie können direkt aus dieser URL lesen, um den binären Inhalt zu abrufen.

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
| `downloadUrl` | OneDrive-URL zum Abrufen des Inhalts der Datei. Sie können eine direkt `HTTP GET` von dieser URL aus aus. |
| `uniqueId` | Eindeutige Datei-ID. Dies ist die OneDrive-Laufwerkelement-ID, wenn der Benutzer eine Datei an Ihren Bot sendet. |
| `fileType` | Dateierweiterungstyp, z. B. pdf oder docx. |

Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer senden.

### <a name="uploading-files-to-personal-chat"></a>Hochladen von Dateien in persönliche Chats

Das Hochladen einer Datei in einen Benutzer umfasst die folgenden Schritte:

1. Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert. Diese Nachricht muss eine Anlage `FileConsentCard` mit dem Namen der datei enthalten, die hochgeladen werden soll.
2. Wenn der Benutzer den Dateidownload akzeptiert, erhält ihr Bot eine *Invoke-Aktivität* mit einer Speicherort-URL.
3. Um die Datei zu übertragen, führt Ihr Bot `HTTP POST` eine direkt in die bereitgestellte Speicherort-URL aus.
4. Optional können Sie die ursprüngliche Zustimmungskarte entfernen, wenn Sie dem Benutzer nicht erlauben möchten, weitere Uploads derselben Datei zu akzeptieren.

#### <a name="message-requesting-permission-to-upload"></a>Nachricht, die die Berechtigung zum Hochladen anfordert

Diese Desktopnachricht enthält ein einfaches Anlagenobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:

![Screenshot der Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei anfordert](../../assets/images/bots/bot-file-consent-card.png)

Diese mobile Nachricht enthält ein Attachment-Objekt, das benutzerberechtigungen zum Hochladen der Datei anfordert:

![Screenshot der Zustimmungskarte, die die Benutzerberechtigung zum Hochladen von Dateien auf Mobilgeräten anfordert](../../assets/images/bots/mobile-bot-file-consent-card.png)

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
| `description` | Beschreibung der Datei. Kann dem Benutzer angezeigt werden, um seinen Zweck zu beschreiben oder seinen Inhalt zusammenzufassen. |
| `sizeInBytes` | Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes in OneDrive zur Verfügung. |
| `acceptContext` | Zusätzlicher Kontext, der automatisch an Ihren Bot übermittelt wird, wenn der Benutzer die Datei akzeptiert. |
| `declineContext` | Zusätzlicher Kontext, der automatisch an Ihren Bot übermittelt wird, wenn der Benutzer die Datei zurückgibt. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Aufrufen von Aktivitäten, wenn der Benutzer die Datei akzeptiert

Eine Aufrufaktivität wird an Ihren Bot gesendet, wenn und wann der Benutzer die Datei akzeptiert. Sie enthält die OneDrive for Business-Platzhalter-URL, in die Ihr Bot dann eine ausgibt, um den `PUT` Dateiinhalt zu übertragen. Informationen zum Hochladen in die OneDrive-URL finden Sie in diesem Artikel: [Hochladen von Bytes in die Uploadsitzung](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

Das folgende Beispiel zeigt eine gekürzte Version der Aufrufaktivität, die Ihr Bot erhält:

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

Wenn der Benutzer die Datei zurückgibt, erhält ihr Bot das folgende Ereignis mit demselben allgemeinen Aktivitätsnamen:

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

Nach dem Hochladen einer Datei in das OneDrive des Benutzers, unabhängig davon, ob Sie den oben beschriebenen Mechanismus oder delegierte #A0 verwenden, sollten Sie eine Bestätigungsnachricht an den Benutzer senden. Diese Nachricht sollte eine Anlage enthalten, auf die der Benutzer klicken kann, um eine Vorschau anzuzeigen, sie in OneDrive zu öffnen `FileCard` oder lokal herunterzuladen.

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
| `uniqueId` | OneDrive/SharePoint-Laufwerkelement-ID. |
| `fileType` | Dateityp, z. B. pdf oder docx. |

### <a name="basic-example-in-c"></a>Grundlegendes Beispiel in C #

Das folgende Beispiel zeigt, wie Sie Dateiuploads verarbeiten und Datei-Zustimmungsanforderungen im Dialogfeld Ihres Bots senden können.

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
