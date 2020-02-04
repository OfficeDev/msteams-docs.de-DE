---
title: Senden und empfangen von Dateien
author: clearab
description: Wie Sie Dateien mit Ihrem Microsoft Teams-bot senden und empfangen.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e7d703f30dffaf317f22529ab56b76d859ebd8b6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674480"
---
# <a name="send-and-receive-files-with-a-bot"></a><span data-ttu-id="8ef8a-103">Senden und empfangen von Dateien mit einem bot</span><span class="sxs-lookup"><span data-stu-id="8ef8a-103">Send and receive files with a bot</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="8ef8a-104">In diesem Artikel wird beschrieben, wie Sie Dateien mit einem Benutzer in einem eins-zu-eins-Chat mit Ihrem bot austauschen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-104">This article describe how to exchange files with a user in a one-to-one chat with your bot.</span></span> <span data-ttu-id="8ef8a-105">Sie können diese Funktion nicht verwenden, um Dateien in einem Team-oder Gruppenchat auszutauschen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-105">You cannot use this functionality to exchange files in a team or group chat.</span></span>

<span data-ttu-id="8ef8a-106">Es gibt zwei Ansätze zur Auswahl:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-106">There are two approaches to choose from:</span></span>

1. <span data-ttu-id="8ef8a-107">**Microsoft Graph-APIs**, die alle drei Bereiche unterstützt `personal`: `channel`, und`groupchat`</span><span class="sxs-lookup"><span data-stu-id="8ef8a-107">**Microsoft Graph APIs**, which supports all three scopes: `personal`, `channel`, and `groupchat`</span></span>
2. <span data-ttu-id="8ef8a-108">**Teams-bot-APIs**, die nur `personal` den Bereich unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-108">**Teams bot APIs**, which only support the `personal` scope.</span></span>

> [!NOTE] 
> <span data-ttu-id="8ef8a-109">Das Senden und empfangen von Dateien an Bots auf mobilen Geräten wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-109">Sending and receiving files to bots on mobile devices is not supported.</span></span>

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="8ef8a-110">Verwenden der Microsoft Graph-APIs</span><span class="sxs-lookup"><span data-stu-id="8ef8a-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="8ef8a-111">Sie können Nachrichten mit Karten Anlagen nach verweisen auf vorhandene SharePoint-Dateien mithilfe der Microsoft Graph-APIs für [OneDrive und SharePoint](https://docs.microsoft.com/onedrive/developer/rest-api/)bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](https://docs.microsoft.com/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="8ef8a-112">Für die Verwendung der Graph-APIs muss der authentifizierte Zugriff über den standardmäßigen OAuth 2,0-Fluss an Folgendes abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-112">Using the Graph APIs requires obtaining authenticated access, through the standard OAuth 2.0 flow, to:</span></span>

- <span data-ttu-id="8ef8a-113">Der OneDrive-Ordner eines Benutzers ( `personal` für `groupchat` und Dateien).</span><span class="sxs-lookup"><span data-stu-id="8ef8a-113">A user's OneDrive folder (for `personal` and `groupchat` files).</span></span>
- <span data-ttu-id="8ef8a-114">Oder an die Dateien in den Kanälen eines Teams (für `channel` Dateien).</span><span class="sxs-lookup"><span data-stu-id="8ef8a-114">Or to the files in a team's channels (for `channel` files).</span></span> <span data-ttu-id="8ef8a-115">Diese Methode funktioniert in allen Microsoft Teams-Bereichen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-115">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="8ef8a-116">Verwenden der Teams-bot-APIs</span><span class="sxs-lookup"><span data-stu-id="8ef8a-116">Using the Teams Bot APIs</span></span>

<span data-ttu-id="8ef8a-117">Ihr Bot kann Dateien direkt mit Benutzern im `personal` Kontext, auch als persönliche Chats bezeichnet, mithilfe von Teams-APIs senden und empfangen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="8ef8a-118">Auf diese Weise können Sie Szenarien wie Spesenabrechnung, Bild Erkennung, Dateiarchivierung, e-Signaturen und andere Szenarien implementieren, in denen der Dateiinhalt direkt manipuliert wird.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-118">This lets you implement scenarios such expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="8ef8a-119">In Microsoft Teams freigegebene Dateien werden normalerweise als Karten angezeigt und ermöglichen eine umfangreiche in-App-Anzeige.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>  <span data-ttu-id="8ef8a-120">Die API wird als Teil der **Microsoft Teams-bot-Plattform**bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-120">The API is provided as part of the **Microsoft Teams Bot Platform**.</span></span>

> [!NOTE]
> <span data-ttu-id="8ef8a-121">Diese Methode funktioniert nur im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-121">This method works only in the `personal` context.</span></span> <span data-ttu-id="8ef8a-122">Sie funktioniert nicht im `channel` oder `groupchat` -Kontext.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-122">It does not work in the `channel` or `groupchat` context.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="8ef8a-123">Konfigurieren Ihres bot zur Unterstützung von Dateien</span><span class="sxs-lookup"><span data-stu-id="8ef8a-123">Configure your bot to support files</span></span>

<span data-ttu-id="8ef8a-124">Um Dateien in Ihrem bot zu senden und zu empfangen, müssen Sie `supportsFiles` die-Eigenschaft im Manifest `true`auf festlegen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-124">To send and receive files in your bot, you must set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="8ef8a-125">Diese Eigenschaft wird im Abschnitt [Bots](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema#bots
) der Manifest-Referenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-125">This property is described in the [bots](https://docs.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema#bots
) section of the Manifest reference.</span></span>

<span data-ttu-id="8ef8a-126">Die Einstellung sieht wie folgt aus `"supportsFiles": true`:.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-126">The setting looks like this: `"supportsFiles": true`.</span></span>

## <a name="invoke-activity-when-the-user-accepts-the-file-upload"></a><span data-ttu-id="8ef8a-127">Aktivität aufrufen, wenn der Benutzer den Dateiupload akzeptiert</span><span class="sxs-lookup"><span data-stu-id="8ef8a-127">Invoke activity when the user accepts the file upload</span></span>

<span data-ttu-id="8ef8a-128">Die Datei wird nach der Erteilung der Zustimmung zum Hochladen in den **OneDrive** -Speicher des Benutzers hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-128">The file is uploaded to the user's **OneDrive** storage after the consent to upload is issued.</span></span> <span data-ttu-id="8ef8a-129">Der bot erhält eine Nachrichtenaktivität, die Datei Metadaten wie den Namen und die Inhalts-URL enthält.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-129">The bot will receive a message activity which contains file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="8ef8a-130">Führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-130">Follow these steps:</span></span>

1. <span data-ttu-id="8ef8a-131">Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-131">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="8ef8a-132">Diese Nachricht muss eine `FileConsentCard` Anlage mit dem Namen der hochzuladenden Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-132">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>

    ![Berechtigungskarte zum Hochladen von bot-Dateien](../../../assets/images/bots/bot-file-upload-permission-card.png)

2. <span data-ttu-id="8ef8a-134">Wenn der Benutzer den Dateiupload akzeptiert, erhält der bot eine *Invoke* -Aktivität mit einer Standort-URL.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-134">If the user accepts the file upload, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="8ef8a-135">Um die Datei zu übertragen, führt Ihr `HTTP POST` bot einen direkt in die angegebene Standort-URL ein.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-135">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="8ef8a-136">Optional können Sie die ursprüngliche Zustimmungs Karte entfernen, wenn Sie nicht zulassen möchten, dass der Benutzer weitere Uploads derselben Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-136">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>
 
<span data-ttu-id="8ef8a-137">Das folgende Beispiel zeigt eine gekürzte Version der Invoke-Aktivität, die ihr bot empfangen wird:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-137">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

```json
{
    "name": "fileConsent/invoke",
    "type": "invoke",
    "timestamp": "2019-10-24T20:22:37.875Z",
    "localTimestamp": "2019-10-24T13:22:37.875-07:00",
    "id": "f:8805947989118514037",

    ...

    "value": {
        "type": "fileUpload",
        "action": "accept",
        "context": {
            "filename": "teams-logo.png"
        },
        "uploadInfo": {
            "contentUrl": "https://contoso.sharepoint.com//personal/<user alias>/Documents/Applications/TeamsFilesBot/teams-logo.png",
            "name": "teams-logo.png",
            "uploadUrl": "https://contoso.sharepoint.com//personal/<user alias>/_api/v2.0/drive/items/01FED6KHQXVVCUCI6XVJCZZMU2WMUSA6JS/uploadSession?guid=<GUID>",
            "uniqueId": "<Unique ID>",
            "fileType": "png"
        }
    },

    "locale": "en-US"
}

```

<span data-ttu-id="8ef8a-138">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-138">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="8ef8a-139">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8ef8a-139">Property</span></span> | <span data-ttu-id="8ef8a-140">Zweck</span><span class="sxs-lookup"><span data-stu-id="8ef8a-140">Purpose</span></span> |
| --- | --- |
| `uploadUrl` | <span data-ttu-id="8ef8a-141">OneDrive-URL zum Hochladen des Inhalts der Datei.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-141">OneDrive URL for uploading the content of the file.</span></span> |
| `uniqueId` | <span data-ttu-id="8ef8a-142">Eindeutige Datei-ID.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-142">Unique file ID.</span></span> <span data-ttu-id="8ef8a-143">Dies ist die OneDrive-Laufwerk Element-ID.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-143">This will be the OneDrive drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="8ef8a-144">Dateityp "Dateierweiterung", beispielsweise PDF oder \* PNG \* \*.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-144">File extension type, such as pdf or \*png\*\*.</span></span> |

<span data-ttu-id="8ef8a-145">Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer zurücksenden.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-145">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

<span data-ttu-id="8ef8a-146">Wenn der Benutzer die Datei ablehnt, erhält der bot das folgende Ereignis mit dem gleichen Gesamt Aktivitätsnamen:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-146">If the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

```json
{
  "name": "fileConsent/invoke",
  "value": {
    "type": "fileUpload",
    "action": "decline",
    "context": {
      ...
    }
  }
}
```

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="8ef8a-147">Benachrichtigen des Benutzers über eine hochgeladene Datei</span><span class="sxs-lookup"><span data-stu-id="8ef8a-147">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="8ef8a-148">Nachdem Sie eine Datei in das OneDrive des Benutzers hochgeladen haben, sollten Sie eine Bestätigungsnachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-148">After uploading a file to the user's OneDrive, you should send a confirmation message to the user.</span></span> <span data-ttu-id="8ef8a-149">Diese Nachricht sollte eine Anlage `FileCard` enthalten, auf die der Benutzer klicken kann, entweder um eine Vorschau anzuzeigen, Sie in OneDrive zu öffnen oder lokal herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-149">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span> <span data-ttu-id="8ef8a-150">Es folgt ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-150">The following is an example.</span></span> 

```json
{
  "attachments": [{
    "contentType": "application/vnd.microsoft.teams.card.file.info",
    "contentUrl": "https://contoso.sharepoint.com/personal/johnadams_contoso_com/Documents/Applications/file_example.txt",
    "name": "file_example.txt",
    "content": {
      "uniqueId": "<unique ID>",
      "fileType": "png",
    }
  }]
}

```

<span data-ttu-id="8ef8a-151">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8ef8a-151">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="8ef8a-152">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8ef8a-152">Property</span></span> | <span data-ttu-id="8ef8a-153">Zweck</span><span class="sxs-lookup"><span data-stu-id="8ef8a-153">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="8ef8a-154">OneDrive/SharePoint-Laufwerk Element-ID.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-154">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="8ef8a-155">Dateityp, wie PDF oder docx.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-155">File type, such as pdf or docx.</span></span> |

## <a name="example-using-the-bot-framework-sdk"></a><span data-ttu-id="8ef8a-156">Beispiel für die Verwendung des bot Framework-SDK</span><span class="sxs-lookup"><span data-stu-id="8ef8a-156">Example using the Bot Framework SDK</span></span>

<span data-ttu-id="8ef8a-157">Im folgenden Beispiel wird gezeigt, wie Sie Dateiuploads verarbeiten und Datei Genehmigungsanforderungen an den Benutzer im Dialogfeld des bot senden können.</span><span class="sxs-lookup"><span data-stu-id="8ef8a-157">The following example shows how you can handle file uploads and send file consent requests to the user in the bot's dialog.</span></span> <span data-ttu-id="8ef8a-158">Die folgenden Codeausschnitte gehören zu einem vollständig ausführbaren Beispiel, das Sie an dieser Stelle herunterladen können: [FileUpload](https://github.com/microsoft/botbuilder-dotnet/tree/master/tests/Teams/FileUpload).</span><span class="sxs-lookup"><span data-stu-id="8ef8a-158">The code snippets shown next, belong to a complete runnable example you can download at this location: [FileUpload](https://github.com/microsoft/botbuilder-dotnet/tree/master/tests/Teams/FileUpload).</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="8ef8a-159">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="8ef8a-159">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    bool messageWithFileDownloadInfo = turnContext.Activity.Attachments?[0].ContentType == FileDownloadInfo.ContentType;
    if (messageWithFileDownloadInfo)
    {
        var file = turnContext.Activity.Attachments[0];
        var fileDownload = JObject.FromObject(file.Content).ToObject<FileDownloadInfo>();

        string filePath = Path.Combine("Files", file.Name);

        var client = _clientFactory.CreateClient();
        var response = await client.GetAsync(fileDownload.DownloadUrl);
        using (var fileStream = new FileStream(filePath, FileMode.Create, FileAccess.Write, FileShare.None))
        {
            await response.Content.CopyToAsync(fileStream);
        }

        var reply = ((Activity)turnContext.Activity).CreateReply();
        reply.TextFormat = "xml";
        reply.Text = $"Complete downloading <b>{file.Name}</b>";
        await turnContext.SendActivityAsync(reply, cancellationToken);
    }
    else
    {
        string filename = "teams-logo.png";
        string filePath = Path.Combine("Files", filename);
        long fileSize = new FileInfo(filePath).Length;
        await SendFileCardAsync(turnContext, filename, fileSize, cancellationToken);
    }
}

private async Task SendFileCardAsync(ITurnContext turnContext, string filename, long filesize, CancellationToken cancellationToken)
{
    var consentContext = new Dictionary<string, string>
    {
        { "filename", filename },
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

protected override async Task OnTeamsFileConsentAcceptAsync(ITurnContext<IInvokeActivity> turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    try
    {
        JToken context = JObject.FromObject(fileConsentCardResponse.Context);

        string filePath = Path.Combine("Files", context["filename"].ToString());
        long fileSize = new FileInfo(filePath).Length;
        var client = _clientFactory.CreateClient();
        using (var fileStream = File.OpenRead(filePath))
        {
            var fileContent = new StreamContent(fileStream);
            fileContent.Headers.ContentLength = fileSize;
            fileContent.Headers.ContentRange = new ContentRangeHeaderValue(0, fileSize - 1, fileSize);
            await client.PutAsync(fileConsentCardResponse.UploadInfo.UploadUrl, fileContent, cancellationToken);
        }

        await FileUploadCompletedAsync(turnContext, fileConsentCardResponse, cancellationToken);
    }
    catch (Exception e)
    {
        await FileUploadFailedAsync(turnContext, e.ToString(), cancellationToken);
    }
}

protected override async Task OnTeamsFileConsentDeclineAsync(ITurnContext<IInvokeActivity> turnContext, FileConsentCardResponse fileConsentCardResponse, CancellationToken cancellationToken)
{
    JToken context = JObject.FromObject(fileConsentCardResponse.Context);

    var reply = ((Activity)turnContext.Activity).CreateReply();
    reply.TextFormat = "xml";
    reply.Text = $"Declined. We won't upload file <b>{context["filename"]}</b>.";
    await turnContext.SendActivityAsync(reply, cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="8ef8a-160">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="8ef8a-160">TypeScript/Node.js</span></span>](#tab/typescript)

<!-- From sample: libraries\botbuilder\tests\teams\fileUpload\src\fileUploadBot.ts-->

```typescript

export class FileUploadBot extends TeamsActivityHandler {
    constructor() {
        super();

        this.onMessage(async (context, next) => {
            await this.sendFileCard(context);
            await next();
        });

        this.onMembersAdded(async (context, next) => {
            const membersAdded = context.activity.membersAdded;
            for (const member of membersAdded) {
                if (member.id !== context.activity.recipient.id) {
                    await context.sendActivity('Hello and welcome!');
                }
            }
            await next();
        });
    }

    private async sendFileCard(context: TurnContext): Promise<void> {
        let filename = "file name";
        let fs = require('fs'); 
        let path = require('path');
        let stats = fs.statSync(path.join('files', filename));
        let fileSizeInBytes = stats['size'];

        let fileContext = {
            filename: filename
        };

        let attachment = {
            content: <FileConsentCard>{
                description: 'This is the file I want to send you',
                fileSizeInBytes: fileSizeInBytes,
                acceptContext: fileContext,
                declineContext: fileContext
            },
            contentType: 'application/vnd.microsoft.teams.card.file.consent',
            name: filename
        } as Attachment;

        var replyActivity = this.createReply(context.activity);
        replyActivity.attachments = [ attachment ];
        await context.sendActivity(replyActivity);
    }

    protected async handleTeamsFileConsentAccept(context: TurnContext, fileConsentCardResponse: FileConsentCardResponse): Promise<void> {
        try {
            await this.sendFile(fileConsentCardResponse);
            await this.fileUploadCompleted(context, fileConsentCardResponse);
        }
        catch (err) {
            await this.fileUploadFailed(context, err.toString());
        }
    }

    protected async handleTeamsFileConsentDecline(context: TurnContext, fileConsentCardResponse: FileConsentCardResponse): Promise<void> {
        let reply = this.createReply(context.activity);
        reply.textFormat = "xml";
        reply.text = `Declined. We won't upload file <b>${fileConsentCardResponse.context["filename"]}</b>.`;
        await context.sendActivity(reply);
    }
...

}

```

<!-- Python samples verify -->

# <a name="pythontabpython"></a>[<span data-ttu-id="8ef8a-161">Python</span><span class="sxs-lookup"><span data-stu-id="8ef8a-161">Python</span></span>](#tab/python)

```python
class TeamsFileUploadBot(TeamsActivityHandler):
    async def on_message_activity(self, turn_context: TurnContext):
        message_with_file_download = (
            False
            if not turn_context.activity.attachments
            else turn_context.activity.attachments[0].content_type == ContentType.FILE_DOWNLOAD_INFO
        )

        if message_with_file_download:
            # Save an uploaded file locally
            file = turn_context.activity.attachments[0]
            file_download = FileDownloadInfo.deserialize(file.content)
            file_path = "files/" + file.name

            response = requests.get(file_download.download_url, allow_redirects=True)
            open(file_path, "wb").write(response.content)

            reply = self._create_reply(
                turn_context.activity, f"Complete downloading <b>{file.name}</b>", "xml"
            )
            await turn_context.send_activity(reply)
        else:
            # Attempt to upload a file to Teams.  This will display a confirmation to
            # the user (Accept/Decline card).  If they accept, on_teams_file_consent_accept
            # will be called, otherwise on_teams_file_consent_decline.
            filename = "teams-logo.png"
            file_path = "files/" + filename
            file_size = os.path.getsize(file_path)
            await self._send_file_card(turn_context, filename, file_size)

    async def _send_file_card(
            self, turn_context: TurnContext, filename: str, file_size: int
    ):
        """
        Send a FileConsentCard to get permission from the user to upload a file.
        """

        consent_context = {"filename": filename}

        file_card = FileConsentCard(
            description="This is the file I want to send you",
            size_in_bytes=file_size,
            accept_context=consent_context,
            decline_context=consent_context
        )

        as_attachment = Attachment(
            content=file_card.serialize(), content_type=ContentType.FILE_CONSENT_CARD, name=filename
        )

        reply_activity = self._create_reply(turn_context.activity)
        reply_activity.attachments = [as_attachment]
        await turn_context.send_activity(reply_activity)

    async def on_teams_file_consent_accept(
            self,
            turn_context: TurnContext,
            file_consent_card_response: FileConsentCardResponse
    ):
        """
        The user accepted the file upload request.  Do the actual upload now.
        """

        file_path = "files/" + file_consent_card_response.context["filename"]
        file_size = os.path.getsize(file_path)

        headers = {
            "Content-Length": f"\"{file_size}\"",
            "Content-Range": f"bytes 0-{file_size-1}/{file_size}"
        }
        response = requests.put(
            file_consent_card_response.upload_info.upload_url, open(file_path, "rb"), headers=headers
        )

        if response.status_code != 200:
            await self._file_upload_failed(turn_context, "Unable to upload file.")
        else:
            await self._file_upload_complete(turn_context, file_consent_card_response)

    async def on_teams_file_consent_decline(
            self,
            turn_context: TurnContext,
            file_consent_card_response: FileConsentCardResponse
    ):
        """
        The user declined the file upload.
        """

        context = file_consent_card_response.context

        reply = self._create_reply(
            turn_context.activity,
            f"Declined. We won't upload file <b>{context['filename']}</b>.",
            "xml"
        )
        await turn_context.send_activity(reply)

    async def _file_upload_complete(
            self,
            turn_context: TurnContext,
            file_consent_card_response: FileConsentCardResponse
    ):
        """
        The file was uploaded, so display a FileInfoCard so the user can view the
        file in Teams.
        """

        name = file_consent_card_response.upload_info.name

        download_card = FileInfoCard(
            unique_id=file_consent_card_response.upload_info.unique_id,
            file_type=file_consent_card_response.upload_info.file_type
        )

        as_attachment = Attachment(
            content=download_card.serialize(),
            content_type=ContentType.FILE_INFO_CARD,
            name=name,
            content_url=file_consent_card_response.upload_info.content_url
        )

        reply = self._create_reply(
            turn_context.activity,
            f"<b>File uploaded.</b> Your file <b>{name}</b> is ready to download",
            "xml"
        )
        reply.attachments = [as_attachment]

        await turn_context.send_activity(reply)

    async def _file_upload_failed(self, turn_context: TurnContext, error: str):
        reply = self._create_reply(
            turn_context.activity,
            f"<b>File upload failed.</b> Error: <pre>{error}</pre>",
            "xml"
        )
        await turn_context.send_activity(reply)

    def _create_reply(self, activity, text=None, text_format=None):
        return Activity(
            type=ActivityTypes.message,
            timestamp=datetime.utcnow(),
            from_property=ChannelAccount(
                id=activity.recipient.id, name=activity.recipient.name
            ),
            recipient=ChannelAccount(
                id=activity.from_property.id, name=activity.from_property.name
            ),
            reply_to_id=activity.id,
            service_url=activity.service_url,
            channel_id=activity.channel_id,
            conversation=ConversationAccount(
                is_group=activity.conversation.is_group,
                id=activity.conversation.id,
                name=activity.conversation.name,
            ),
            text=text or "",
            text_format=text_format or None,
            locale=activity.locale,
        )


```

---
