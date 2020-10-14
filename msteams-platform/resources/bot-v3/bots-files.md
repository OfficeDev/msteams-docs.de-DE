---
title: Senden und empfangen von Dateien von einem bot
description: Beschreibt, wie Dateien von einem bot gesendet und empfangen werden
keywords: Teams-Bots-Dateien senden empfangen
ms.date: 05/20/2019
ms.openlocfilehash: b61e7f6934846b3abb1cfc16283cec1d264d7ecc
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452780"
---
# <a name="send-and-receive-files-through-your-bot"></a>Senden und empfangen von Dateien über Ihren bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Es gibt zwei Möglichkeiten, Dateien an einen bot zu senden:

* Verwenden der Microsoft Graph-APIs. Diese Methode funktioniert für Bots in allen Bereichen in Microsoft Teams:
  * `personal`
  * `channel`
  * `groupchat`
* Verwenden der Teams-APIs. Dateien werden nur in einem Kontext unterstützt:
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a>Verwenden der Microsoft Graph-APIs

Sie können Nachrichten mit Karten Anlagen nach verweisen auf vorhandene SharePoint-Dateien mithilfe der Microsoft Graph-APIs für [OneDrive und SharePoint](/onedrive/developer/rest-api/)bereitstellen. Für die Verwendung der Graph-APIs muss der Zugriff auf den OneDrive-Ordner eines Benutzers (für `personal` und `groupchat` Dateien) oder die Dateien in den Kanälen eines Teams (für `channel` Dateien) über den standardmäßigen OAuth 2,0-Autorisierungs Fluss abgerufen werden. Diese Methode funktioniert in allen Microsoft Teams-Bereichen.

## <a name="using-the-teams-bot-apis"></a>Verwenden der Teams-bot-APIs

> [!NOTE]
> Diese Methode funktioniert nur im `personal` Kontext. Sie funktioniert nicht im `channel` oder `groupchat` -Kontext.

Ihr Bot kann Dateien direkt mit Benutzern im `personal` Kontext, auch als persönliche Chats bezeichnet, mithilfe von Teams-APIs senden und empfangen. Auf diese Weise können Sie Spesenabrechnungen, Bild Erkennung, Dateiarchivierung, e-Signaturen und andere Szenarien mit direkter Manipulation von Dateiinhalten implementieren. In Microsoft Teams freigegebene Dateien werden normalerweise als Karten angezeigt und ermöglichen eine umfangreiche in-App-Anzeige.

In den folgenden Abschnitten wird die Vorgehensweise zum Senden von Dateiinhalten als Ergebnis einer direkten Benutzerinteraktion wie das Senden einer Nachricht beschrieben. Diese API wird als Teil der Microsoft Teams-bot-Plattform bereitgestellt.

### <a name="configure-your-bot-to-support-files"></a>Konfigurieren Ihres bot zur Unterstützung von Dateien

Um Dateien in Ihrem bot zu senden und zu empfangen, müssen Sie die `supportsFiles` -Eigenschaft im Manifest auf festlegen `true` . Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifest-Referenz beschrieben.

Die Definition wird wie folgt aussehen: `"supportsFiles": true` . Wenn Ihr bot nicht aktiviert wird `supportsFiles` , können die folgenden Funktionen nicht verwendet werden.

### <a name="receiving-files-in-personal-chat"></a>Empfangen von Dateien im persönlichen Chat

Wenn ein Benutzer eine Datei an Ihren bot sendet, wird die Datei zunächst in den OneDrive für Unternehmen Speicher des Benutzers hochgeladen. Ihr bot erhält dann eine Nachrichtenaktivität, in der Sie über den Benutzer Upload benachrichtigt werden. Die Aktivität enthält Datei Metadaten, beispielsweise den Namen und die Inhalts-URL. Sie können direkt aus dieser URL lesen, um den binären Inhalt abzurufen.

#### <a name="message-activity-with-file-attachment-example"></a>Nachrichtenaktivität mit Beispiel für eine Dateianlage

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
| `downloadUrl` | OneDrive-URL zum Abrufen des Inhalts der Datei. Sie können eine `HTTP GET` direkt aus dieser URL heraus ausgeben. |
| `uniqueId` | Eindeutige Datei-ID. Dies ist die OneDrive-Laufwerk Element-ID, wenn der Benutzer eine Datei an den bot sendet. |
| `fileType` | Dateityp der Dateierweiterung, wie PDF oder docx. |

Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer zurücksenden.

### <a name="uploading-files-to-personal-chat"></a>Hochladen von Dateien in persönlichen Chat

Das Hochladen einer Datei in einen Benutzer umfasst die folgenden Schritte:

1. Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert. Diese Nachricht muss eine `FileConsentCard` Anlage mit dem Namen der hochzuladenden Datei enthalten.
2. Wenn der Benutzer den Dateidownload akzeptiert, erhält der bot eine *Invoke* -Aktivität mit einer Standort-URL.
3. Um die Datei zu übertragen, führt Ihr bot einen `HTTP POST` direkt in die angegebene Standort-URL ein.
4. Optional können Sie die ursprüngliche Zustimmungs Karte entfernen, wenn Sie nicht zulassen möchten, dass der Benutzer weitere Uploads derselben Datei akzeptiert.

#### <a name="message-requesting-permission-to-upload"></a>Nachricht, die die Berechtigung zum Hochladen anfordert

Diese Desktop Nachricht enthält ein einfaches Attachment-Objekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:

![Screenshot der Zustimmungs Karte, die die Benutzerberechtigung zum Hochladen von Dateien anfordert](../../assets/images/bots/bot-file-consent-card.png)

Diese Mobile Nachricht enthält ein Attachment-Objekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:

![Screenshot der Zustimmungs Karte anfordern der Benutzerberechtigung zum Hochladen von Dateien auf mobilen Geräten](../../assets/images/bots/mobile-bot-file-consent-card.png)

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
| `sizeInBytes` | Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes zur Verfügung, der in OneDrive ausgeführt werden sollte. |
| `acceptContext` | Zusätzlicher Kontext, der automatisch an Ihren bot weitergeleitet wird, wenn der Benutzer die Datei annimmt. |
| `declineContext` | Zusätzlicher Kontext, der automatisch an Ihren bot weitergeleitet wird, wenn der Benutzer die Datei ablehnt. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Aktivität aufrufen, wenn der Benutzer die Datei akzeptiert

Eine Invoke-Aktivität wird an Ihren bot gesendet, wenn der Benutzer die Datei annimmt. Sie enthält die OneDrive für Unternehmen Platzhalter-URL, über die der bot dann eine `PUT` zum Übertragen der Dateiinhalte ausgeben kann. Informationen zum Hochladen der OneDrive-URL finden Sie in diesem Artikel: [Upload Bytes to the Upload Session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

Das folgende Beispiel zeigt eine gekürzte Version der Invoke-Aktivität, die ihr bot empfangen wird:

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

Wenn der Benutzer die Datei ablehnt, erhält der bot das folgende Ereignis mit dem gleichen Gesamt Aktivitätsnamen:

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

Nachdem Sie eine Datei in das OneDrive des Benutzers hochgeladen haben, sollten Sie, unabhängig davon, ob Sie den oben beschriebenen Mechanismus oder OneDrive-Benutzer delegierte APIs verwenden, eine Bestätigungsnachricht an den Benutzer senden. Diese Nachricht sollte eine Anlage enthalten, auf `FileCard` die der Benutzer klicken kann, entweder um eine Vorschau anzuzeigen, Sie in OneDrive zu öffnen oder lokal herunterzuladen.

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
| `uniqueId` | OneDrive/SharePoint-Laufwerk Element-ID. |
| `fileType` | Dateityp, wie PDF oder docx. |

### <a name="basic-example-in-c"></a>Grundlegendes Beispiel in C #

Im folgenden Beispiel wird gezeigt, wie Sie Dateiuploads verarbeiten und Datei Genehmigungsanforderungen im Dialogfeld Ihres bot senden können.

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
