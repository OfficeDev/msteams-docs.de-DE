---
title: Senden und Empfangen von Dateien über den Bot
description: Beschreibt das Senden und Empfangen von Dateien über den Bot
keywords: teams bots files send receive
ms.date: 05/20/2019
ms.topic: how-to
ms.openlocfilehash: bc2cbaeedcc770f82e3fc1f6cfbbf1beda3948fd
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "51996044"
---
# <a name="send-and-receive-files-through-the-bot"></a>Senden und Empfangen von Dateien über den Bot

> [!IMPORTANT]
> Die Artikel in diesem Dokument basieren auf dem v4 Bot Framework SDK.

Es gibt zwei Möglichkeiten zum Senden und Empfangen von Dateien von einem Bot:

* [**Verwenden Sie die Microsoft Graph-APIs:**](#use-the-graph-apis) Diese Methode funktioniert für Bots in allen Microsoft Teams-Bereiche:
  * `personal`
  * `channel`
  * `groupchat`

* [**Verwenden Sie die Teams-Bot-APIs:**](#use-the-teams-bot-apis) Diese unterstützen nur Dateien im `personal` Kontext.

## <a name="use-the-graph-apis"></a>Verwenden der Graph-APIs

Posten von Nachrichten mit Kartenanlagen, die auf vorhandene #A0 verweisen, mithilfe der Graph-APIs für [OneDrive und SharePoint](/onedrive/developer/rest-api/). Um die Graph-APIs zu verwenden, erhalten Sie über den standardmäßigen OAuth 2.0-Autorisierungsfluss Zugriff auf eine der folgenden:

* Der #A0 eines Benutzers für `personal` und `groupchat` Dateien.
* Die Dateien im Kanal eines Teams für `channel` Dateien.

Graph-APIs funktionieren in allen Teams-Bereich. Weitere Informationen finden Sie unter [Senden von Chatnachrichtendateianlagen](/graph/api/chatmessage-post?view=graph-rest-beta&tabs=http#example-4-file-attachments&preserve-view=true).

Alternativ können Sie Dateien mithilfe der Teams-Bot-APIs an einen Bot senden und von diesem empfangen.

## <a name="use-the-teams-bot-apis"></a>Verwenden der Teams-Bot-APIs

> [!NOTE]
> Teams-Bot-APIs funktionieren nur im `personal` Kontext. Sie funktionieren nicht im `channel` `groupchat` Oder-Kontext.

Mithilfe von Teams-APIs kann der Bot Dateien direkt mit Benutzern im Kontext senden und empfangen, auch als `personal` persönliche Chats bezeichnet. Implementieren Sie Features, z. B. Spesenabrechnung, Bilderkennung, Dateiarchivierung und E-Signaturen, die die Bearbeitung von Dateiinhalten enthalten. In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.

In den nächsten Abschnitten wird beschrieben, wie Dateiinhalte als direkte Benutzerinteraktion gesendet werden, z. B. das Senden einer Nachricht. Diese API wird als Teil der Teams-Bot-Plattform bereitgestellt.

### <a name="configure-the-bot-to-support-files"></a>Konfigurieren des Bots für die Unterstützung von Dateien

Wenn Sie Dateien im Bot senden und empfangen möchten, legen Sie die `supportsFiles` Eigenschaft im Manifest auf . `true` Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifestreferenz beschrieben.

Die Definition sieht wie dies aus: `"supportsFiles": true` . Wenn der Bot nicht aktiviert ist, funktionieren die in diesem Abschnitt aufgeführten `supportsFiles` Features nicht.

### <a name="receive-files-in-personal-chat"></a>Empfangen von Dateien in persönlichen Chats

Wenn ein Benutzer eine Datei an den Bot sendet, wird die Datei zuerst in den OneDrive for Business-Speicher des Benutzers hochgeladen. Der Bot empfängt dann eine Nachrichtenaktivität, die den Benutzer über den Benutzerupload informiert. Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL. Der Benutzer kann direkt aus dieser URL lesen, um seinen binären Inhalt zu abrufen.

#### <a name="message-activity-with-file-attachment-example"></a>Beispiel für Nachrichtenaktivität mit Dateianlage

Der folgende Code zeigt ein Beispiel für nachrichtenaktivität mit Dateianlage:

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
| `downloadUrl` | OneDrive-URL zum Abrufen des Inhalts der Datei. Der Benutzer kann eine direkt `HTTP GET` von dieser URL aus aus. |
| `uniqueId` | Eindeutige Datei-ID. Dies ist die OneDrive-Laufwerkselement-ID, falls der Benutzer eine Datei an den Bot sendet. |
| `fileType` | Dateityp, z. B. PDF oder DOCX. |

Als bewährte Methode bestätigen Sie den Dateiupload, indem Sie eine Nachricht zurück an den Benutzer senden.

### <a name="upload-files-to-personal-chat"></a>Hochladen von Dateien in persönlichen Chat

**So laden Sie eine Datei in einen Benutzer hoch**

1. Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert. Diese Nachricht muss eine Anlage `FileConsentCard` mit dem Namen der datei enthalten, die hochgeladen werden soll.
2. Wenn der Benutzer den Dateidownload akzeptiert, empfängt der Bot eine Aufrufaktivität mit einer Standort-URL.
3. Um die Datei zu übertragen, führt der Bot `HTTP POST` eine direkt in die bereitgestellte Speicherort-URL aus.
4. Entfernen Sie optional die ursprüngliche Zustimmungskarte, wenn Sie nicht möchten, dass der Benutzer weitere Uploads derselben Datei akzeptiert.

#### <a name="message-requesting-permission-to-upload"></a>Nachricht, die die Berechtigung zum Hochladen anfordert

Die folgende Desktopnachricht enthält ein einfaches Anlageobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:

![Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei anfordert](../../assets/images/bots/bot-file-consent-card.png)

Die folgende mobile Nachricht enthält ein Anlagenobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:

<img src="../../assets/images/bots/mobile-bot-file-consent-card.png" alt="Consent card requesting user permission to upload file on mobile" width="350"/>

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
| `description` | Beschreibt den Zweck der Datei oder fasst den Inhalt zusammen. |
| `sizeInBytes` | Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes in OneDrive zur Verfügung. |
| `acceptContext` | Zusätzlicher Kontext, der automatisch an den Bot übermittelt wird, wenn der Benutzer die Datei akzeptiert. |
| `declineContext` | Zusätzlicher Kontext, der automatisch an den Bot übermittelt wird, wenn der Benutzer die Datei zurückgibt. |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a>Aufrufen von Aktivitäten, wenn der Benutzer die Datei akzeptiert

Eine Aufrufaktivität wird an den Bot gesendet, wenn und wann der Benutzer die Datei akzeptiert. Sie enthält die OneDrive for Business-Platzhalter-URL, die der Bot dann ausgibt, `PUT` um den Dateiinhalt zu übertragen. Informationen zum Hochladen in die OneDrive-URL finden Sie unter [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).

Der folgende Code zeigt ein Beispiel für eine prägnante Version der Aufrufaktivität, die der Bot empfängt:

```json
{
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

Wenn der Benutzer die Datei zurückgibt, empfängt der Bot das folgende Ereignis mit demselben allgemeinen Aktivitätsnamen:

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

Nachdem Sie eine Datei auf das OneDrive des Benutzers hochgeladen haben, senden Sie eine Bestätigungsnachricht an den Benutzer. Die Nachricht muss die folgende Anlage enthalten, die der Benutzer auswählen kann, um eine Vorschau anzuzeigen oder sie in OneDrive zu öffnen `FileCard` oder lokal herunterzuladen:

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
| `uniqueId` | OneDrive- oder SharePoint-Laufwerkelement-ID. |
| `fileType` | Dateityp, z. B. PDF oder DOCX. |

### <a name="fetch-inline-images-from-message"></a>Abrufen von Inlinebildern aus einer Nachricht

Abrufen von Inlinebildern, die Teil der Nachricht sind, mithilfe des Zugriffstokens des Bots.

![Inlinebild](../../assets/images/bots/inline-image.png)

Der folgende Code zeigt ein Beispiel für das Abrufen von Inlinebildern aus nachrichten:

```csharp
private async Task ProcessInlineImage(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var attachment = turnContext.Activity.Attachments[0];
    var client = _clientFactory.CreateClient();
    // Get Bot's access token to fetch inline image. 
    var token = await new MicrosoftAppCredentials(microsoftAppId, microsoftAppPassword).GetTokenAsync();
    client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
    var responseMessage = await client.GetAsync(attachment.ContentUrl);
    // Save the inline image to Files directory.
    var filePath = Path.Combine("Files", "ImageFromUser.png");
    using (var fileStream = new FileStream(filePath, FileMode.Create, FileAccess.Write, FileShare.None))
    {
        await responseMessage.Content.CopyToAsync(fileStream);
    }
    // Create reply with image.
    var reply = MessageFactory.Text($"Attachment of {attachment.ContentType} type and size of {responseMessage.Content.Headers.ContentLength} bytes received.");
    reply.Attachments = new List<Attachment>() { 
        GetInlineAttachment() 
    };
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
private static Attachment GetInlineAttachment()
{
    var imagePath = Path.Combine("Files", "ImageFromUser.png");
    var imageData = Convert.ToBase64String(File.ReadAllBytes(imagePath));
    return new Attachment
    {
        Name = @"ImageFromUser.png",
        ContentType = "image/png",
        ContentUrl = $"data:image/png;base64,{imageData}",
    };
}
```

### <a name="basic-example-in-c"></a>Grundlegendes Beispiel in C #

Der folgende Code zeigt ein Beispiel für die Verarbeitung von Dateiuploads und das Senden von Datei-Zustimmungsanforderungen im Dialogfeld des Bots:

```csharp

protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    if (turnContext.Activity.Attachments?[0].ContentType.Contains("image/*") == true)
    {
        // Inline image.
        await ProcessInlineImage(turnContext, cancellationToken);
    }
    else
    {
        string filename = "teams-logo.png";
        string filePath = Path.Combine("Files", filename);
        long fileSize = new FileInfo(filePath).Length;
        await SendFileCardAsync(turnContext, filename, fileSize, cancellationToken);
    }
}
private async Task ProcessInlineImage(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var attachment = turnContext.Activity.Attachments[0];
    var client = _clientFactory.CreateClient();
    // Get Bot's access token to fetch inline image. 
    var token = await new MicrosoftAppCredentials(microsoftAppId, microsoftAppPassword).GetTokenAsync();
    client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
    var responseMessage = await client.GetAsync(attachment.ContentUrl);
    // Save the inline image to Files directory.
    var filePath = Path.Combine("Files", "ImageFromUser.png");
    using (var fileStream = new FileStream(filePath, FileMode.Create, FileAccess.Write, FileShare.None))
    {
        await responseMessage.Content.CopyToAsync(fileStream);
    }
    // Create reply with image.
    var reply = MessageFactory.Text($"Attachment of {attachment.ContentType} type and size of {responseMessage.Content.Headers.ContentLength} bytes received.");
    reply.Attachments = new List<Attachment>() { GetInlineAttachment() };
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
private static Attachment GetInlineAttachment()
{
    var imagePath = Path.Combine("Files", "ImageFromUser.png");
    var imageData = Convert.ToBase64String(File.ReadAllBytes(imagePath));
    return new Attachment
    {
        Name = @"ImageFromUser.png",
        ContentType = "image/png",
        ContentUrl = $"data:image/png;base64,{imageData}",
    };
}
private async Task SendFileCardAsync(ITurnContext turnContext, string filename, long filesize, CancellationToken cancellationToken)
{
    var consentContext = new Dictionary<string, string>
    {
        { 
            "filename", filename 
        },
    };
    var fileCard = new FileConsentCard
    {
        Description = "This is the file I want to send you",
        SizeInBytes = filesize,
        AcceptContext = consentContext,
        DeclineContext = consentContext,
    };
    var asAttachment = new Attachment
    {
        Content = fileCard,
        ContentType = FileConsentCard.ContentType,
        Name = filename,
    };
    var replyActivity = turnContext.Activity.CreateReply();
    replyActivity.Attachments = new List<Attachment>() { asAttachment };
    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}
```

## <a name="code-sample"></a>Codebeispiel

Das folgende Codebeispiel veranschaulicht, wie Sie die Zustimmung der Datei erhalten und Dateien von einem Bot in Teams hochladen:

|**Beispielname** | **Beschreibung** | **.NET** | **Javascript** | **Python**|
|----------------|-----------------|--------------|----------------|-----------|
| File upload | Zeigt, wie Sie die Zustimmung der Datei erhalten und Dateien von einem Bot in Teams hochladen. Außerdem erfahren Sie, wie Sie eine an einen Bot gesendete Datei empfangen. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/56.teams-file-upload) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/56.teams-file-upload) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/56.teams-file-upload) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Optimieren eines Bots mit Ratenbegrenzung in Teams](~/bots/how-to/rate-limit.md)
