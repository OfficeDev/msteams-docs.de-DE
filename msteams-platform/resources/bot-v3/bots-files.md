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
# <a name="send-and-receive-files-through-your-bot"></a><span data-ttu-id="4ea55-104">Senden und empfangen von Dateien über Ihren bot</span><span class="sxs-lookup"><span data-stu-id="4ea55-104">Send and receive files through your bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="4ea55-105">Es gibt zwei Möglichkeiten, Dateien an einen bot zu senden:</span><span class="sxs-lookup"><span data-stu-id="4ea55-105">There are two ways to send files to and from a bot:</span></span>

* <span data-ttu-id="4ea55-106">Verwenden der Microsoft Graph-APIs.</span><span class="sxs-lookup"><span data-stu-id="4ea55-106">Using the Microsoft Graph APIs.</span></span> <span data-ttu-id="4ea55-107">Diese Methode funktioniert für Bots in allen Bereichen in Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="4ea55-107">This method works for bots in all scopes in Teams:</span></span>
  * `personal`
  * `channel`
  * `groupchat`
* <span data-ttu-id="4ea55-108">Verwenden der Teams-APIs.</span><span class="sxs-lookup"><span data-stu-id="4ea55-108">Using the Teams APIs.</span></span> <span data-ttu-id="4ea55-109">Dateien werden nur in einem Kontext unterstützt:</span><span class="sxs-lookup"><span data-stu-id="4ea55-109">These only support files in one context:</span></span>
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="4ea55-110">Verwenden der Microsoft Graph-APIs</span><span class="sxs-lookup"><span data-stu-id="4ea55-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="4ea55-111">Sie können Nachrichten mit Karten Anlagen nach verweisen auf vorhandene SharePoint-Dateien mithilfe der Microsoft Graph-APIs für [OneDrive und SharePoint](/onedrive/developer/rest-api/)bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="4ea55-112">Für die Verwendung der Graph-APIs muss der Zugriff auf den OneDrive-Ordner eines Benutzers (für `personal` und `groupchat` Dateien) oder die Dateien in den Kanälen eines Teams (für `channel` Dateien) über den standardmäßigen OAuth 2,0-Autorisierungs Fluss abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="4ea55-112">Using the Graph APIs requires obtaining access to a user's OneDrive folder (for `personal` and `groupchat` files) or the files in a team's channels (for `channel` files) through the standard OAuth 2.0 authorization flow.</span></span> <span data-ttu-id="4ea55-113">Diese Methode funktioniert in allen Microsoft Teams-Bereichen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-113">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="4ea55-114">Verwenden der Teams-bot-APIs</span><span class="sxs-lookup"><span data-stu-id="4ea55-114">Using the Teams Bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="4ea55-115">Diese Methode funktioniert nur im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="4ea55-115">This method works only in the `personal` context.</span></span> <span data-ttu-id="4ea55-116">Sie funktioniert nicht im `channel` oder `groupchat` -Kontext.</span><span class="sxs-lookup"><span data-stu-id="4ea55-116">It does not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="4ea55-117">Ihr Bot kann Dateien direkt mit Benutzern im `personal` Kontext, auch als persönliche Chats bezeichnet, mithilfe von Teams-APIs senden und empfangen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="4ea55-118">Auf diese Weise können Sie Spesenabrechnungen, Bild Erkennung, Dateiarchivierung, e-Signaturen und andere Szenarien mit direkter Manipulation von Dateiinhalten implementieren.</span><span class="sxs-lookup"><span data-stu-id="4ea55-118">This lets you implement expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="4ea55-119">In Microsoft Teams freigegebene Dateien werden normalerweise als Karten angezeigt und ermöglichen eine umfangreiche in-App-Anzeige.</span><span class="sxs-lookup"><span data-stu-id="4ea55-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>

<span data-ttu-id="4ea55-120">In den folgenden Abschnitten wird die Vorgehensweise zum Senden von Dateiinhalten als Ergebnis einer direkten Benutzerinteraktion wie das Senden einer Nachricht beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4ea55-120">The following sections describe how to do this to send file content as a result of direct user interaction, like sending a message.</span></span> <span data-ttu-id="4ea55-121">Diese API wird als Teil der Microsoft Teams-bot-Plattform bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="4ea55-121">This API is provided as part of the Microsoft Teams Bot Platform.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="4ea55-122">Konfigurieren Ihres bot zur Unterstützung von Dateien</span><span class="sxs-lookup"><span data-stu-id="4ea55-122">Configure your bot to support files</span></span>

<span data-ttu-id="4ea55-123">Um Dateien in Ihrem bot zu senden und zu empfangen, müssen Sie die `supportsFiles` -Eigenschaft im Manifest auf festlegen `true` .</span><span class="sxs-lookup"><span data-stu-id="4ea55-123">In order to send and receive files in your bot, you have to set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="4ea55-124">Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifest-Referenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4ea55-124">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="4ea55-125">Die Definition wird wie folgt aussehen: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="4ea55-125">The definition will look like this: `"supportsFiles": true`.</span></span> <span data-ttu-id="4ea55-126">Wenn Ihr bot nicht aktiviert wird `supportsFiles` , können die folgenden Funktionen nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4ea55-126">If your bot does not enable `supportsFiles`, the following features will not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="4ea55-127">Empfangen von Dateien im persönlichen Chat</span><span class="sxs-lookup"><span data-stu-id="4ea55-127">Receiving files in personal chat</span></span>

<span data-ttu-id="4ea55-128">Wenn ein Benutzer eine Datei an Ihren bot sendet, wird die Datei zunächst in den OneDrive für Unternehmen Speicher des Benutzers hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-128">When a user sends a file to your bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="4ea55-129">Ihr bot erhält dann eine Nachrichtenaktivität, in der Sie über den Benutzer Upload benachrichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="4ea55-129">Your bot will then receive a message activity notifying you of the user upload.</span></span> <span data-ttu-id="4ea55-130">Die Aktivität enthält Datei Metadaten, beispielsweise den Namen und die Inhalts-URL.</span><span class="sxs-lookup"><span data-stu-id="4ea55-130">The activity will contain file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="4ea55-131">Sie können direkt aus dieser URL lesen, um den binären Inhalt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-131">You can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="4ea55-132">Nachrichtenaktivität mit Beispiel für eine Dateianlage</span><span class="sxs-lookup"><span data-stu-id="4ea55-132">Message activity with file attachment example</span></span>

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

<span data-ttu-id="4ea55-133">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="4ea55-133">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="4ea55-134">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4ea55-134">Property</span></span> | <span data-ttu-id="4ea55-135">Zweck</span><span class="sxs-lookup"><span data-stu-id="4ea55-135">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="4ea55-136">OneDrive-URL zum Abrufen des Inhalts der Datei.</span><span class="sxs-lookup"><span data-stu-id="4ea55-136">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="4ea55-137">Sie können eine `HTTP GET` direkt aus dieser URL heraus ausgeben.</span><span class="sxs-lookup"><span data-stu-id="4ea55-137">You can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="4ea55-138">Eindeutige Datei-ID.</span><span class="sxs-lookup"><span data-stu-id="4ea55-138">Unique file ID.</span></span> <span data-ttu-id="4ea55-139">Dies ist die OneDrive-Laufwerk Element-ID, wenn der Benutzer eine Datei an den bot sendet.</span><span class="sxs-lookup"><span data-stu-id="4ea55-139">This will be the OneDrive drive item ID, in the case of the user sending a file to your bot.</span></span> |
| `fileType` | <span data-ttu-id="4ea55-140">Dateityp der Dateierweiterung, wie PDF oder docx.</span><span class="sxs-lookup"><span data-stu-id="4ea55-140">File extension type, such as pdf or docx.</span></span> |

<span data-ttu-id="4ea55-141">Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer zurücksenden.</span><span class="sxs-lookup"><span data-stu-id="4ea55-141">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="4ea55-142">Hochladen von Dateien in persönlichen Chat</span><span class="sxs-lookup"><span data-stu-id="4ea55-142">Uploading files to personal chat</span></span>

<span data-ttu-id="4ea55-143">Das Hochladen einer Datei in einen Benutzer umfasst die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="4ea55-143">Uploading a file to a user involves the following steps:</span></span>

1. <span data-ttu-id="4ea55-144">Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert.</span><span class="sxs-lookup"><span data-stu-id="4ea55-144">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="4ea55-145">Diese Nachricht muss eine `FileConsentCard` Anlage mit dem Namen der hochzuladenden Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="4ea55-145">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="4ea55-146">Wenn der Benutzer den Dateidownload akzeptiert, erhält der bot eine *Invoke* -Aktivität mit einer Standort-URL.</span><span class="sxs-lookup"><span data-stu-id="4ea55-146">If the user accepts the file download, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="4ea55-147">Um die Datei zu übertragen, führt Ihr bot einen `HTTP POST` direkt in die angegebene Standort-URL ein.</span><span class="sxs-lookup"><span data-stu-id="4ea55-147">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="4ea55-148">Optional können Sie die ursprüngliche Zustimmungs Karte entfernen, wenn Sie nicht zulassen möchten, dass der Benutzer weitere Uploads derselben Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="4ea55-148">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="4ea55-149">Nachricht, die die Berechtigung zum Hochladen anfordert</span><span class="sxs-lookup"><span data-stu-id="4ea55-149">Message requesting permission to upload</span></span>

<span data-ttu-id="4ea55-150">Diese Desktop Nachricht enthält ein einfaches Attachment-Objekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="4ea55-150">This desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Screenshot der Zustimmungs Karte, die die Benutzerberechtigung zum Hochladen von Dateien anfordert](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="4ea55-152">Diese Mobile Nachricht enthält ein Attachment-Objekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="4ea55-152">This mobile message contains an attachment object requesting user permission to upload the file:</span></span>

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

<span data-ttu-id="4ea55-154">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="4ea55-154">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="4ea55-155">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4ea55-155">Property</span></span> | <span data-ttu-id="4ea55-156">Zweck</span><span class="sxs-lookup"><span data-stu-id="4ea55-156">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="4ea55-157">Beschreibung der Datei.</span><span class="sxs-lookup"><span data-stu-id="4ea55-157">Description of the file.</span></span> <span data-ttu-id="4ea55-158">Kann dem Benutzer angezeigt werden, um seinen Zweck zu beschreiben oder seinen Inhalt zusammenzufassen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-158">May be shown to the user to describe its purpose or to summarize its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="4ea55-159">Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes zur Verfügung, der in OneDrive ausgeführt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="4ea55-159">Provides the user an estimate of the file size and the amount of space it will take in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="4ea55-160">Zusätzlicher Kontext, der automatisch an Ihren bot weitergeleitet wird, wenn der Benutzer die Datei annimmt.</span><span class="sxs-lookup"><span data-stu-id="4ea55-160">Additional context that will be silently transmitted to your bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="4ea55-161">Zusätzlicher Kontext, der automatisch an Ihren bot weitergeleitet wird, wenn der Benutzer die Datei ablehnt.</span><span class="sxs-lookup"><span data-stu-id="4ea55-161">Additional context that will be silently transmitted to your bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="4ea55-162">Aktivität aufrufen, wenn der Benutzer die Datei akzeptiert</span><span class="sxs-lookup"><span data-stu-id="4ea55-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="4ea55-163">Eine Invoke-Aktivität wird an Ihren bot gesendet, wenn der Benutzer die Datei annimmt.</span><span class="sxs-lookup"><span data-stu-id="4ea55-163">An invoke activity is sent to your bot if and when the user accepts the file.</span></span> <span data-ttu-id="4ea55-164">Sie enthält die OneDrive für Unternehmen Platzhalter-URL, über die der bot dann eine `PUT` zum Übertragen der Dateiinhalte ausgeben kann.</span><span class="sxs-lookup"><span data-stu-id="4ea55-164">It contains the OneDrive for Business placeholder URL that your bot can then issue a `PUT` into to transfer the file contents.</span></span> <span data-ttu-id="4ea55-165">Informationen zum Hochladen der OneDrive-URL finden Sie in diesem Artikel: [Upload Bytes to the Upload Session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="4ea55-165">for information on uploading to the OneDrive URL read this article: [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="4ea55-166">Das folgende Beispiel zeigt eine gekürzte Version der Invoke-Aktivität, die ihr bot empfangen wird:</span><span class="sxs-lookup"><span data-stu-id="4ea55-166">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

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

<span data-ttu-id="4ea55-167">Wenn der Benutzer die Datei ablehnt, erhält der bot das folgende Ereignis mit dem gleichen Gesamt Aktivitätsnamen:</span><span class="sxs-lookup"><span data-stu-id="4ea55-167">Similarly, if the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="4ea55-168">Benachrichtigen des Benutzers über eine hochgeladene Datei</span><span class="sxs-lookup"><span data-stu-id="4ea55-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="4ea55-169">Nachdem Sie eine Datei in das OneDrive des Benutzers hochgeladen haben, sollten Sie, unabhängig davon, ob Sie den oben beschriebenen Mechanismus oder OneDrive-Benutzer delegierte APIs verwenden, eine Bestätigungsnachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="4ea55-169">After uploading a file to the user's OneDrive, whether you use the mechanism described above or OneDrive user delegated APIs, you should send a confirmation message to the user.</span></span> <span data-ttu-id="4ea55-170">Diese Nachricht sollte eine Anlage enthalten, auf `FileCard` die der Benutzer klicken kann, entweder um eine Vorschau anzuzeigen, Sie in OneDrive zu öffnen oder lokal herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="4ea55-170">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span>

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

<span data-ttu-id="4ea55-171">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="4ea55-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="4ea55-172">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4ea55-172">Property</span></span> | <span data-ttu-id="4ea55-173">Zweck</span><span class="sxs-lookup"><span data-stu-id="4ea55-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="4ea55-174">OneDrive/SharePoint-Laufwerk Element-ID.</span><span class="sxs-lookup"><span data-stu-id="4ea55-174">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="4ea55-175">Dateityp, wie PDF oder docx.</span><span class="sxs-lookup"><span data-stu-id="4ea55-175">File type, such as pdf or docx.</span></span> |

### <a name="basic-example-in-c"></a><span data-ttu-id="4ea55-176">Grundlegendes Beispiel in C #</span><span class="sxs-lookup"><span data-stu-id="4ea55-176">Basic example in C#</span></span>

<span data-ttu-id="4ea55-177">Im folgenden Beispiel wird gezeigt, wie Sie Dateiuploads verarbeiten und Datei Genehmigungsanforderungen im Dialogfeld Ihres bot senden können.</span><span class="sxs-lookup"><span data-stu-id="4ea55-177">The following sample shows how you can handle file uploads and send file consent requests in your bot's dialog.</span></span>

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
