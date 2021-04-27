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
# <a name="send-and-receive-files-through-your-bot"></a><span data-ttu-id="10186-104">Senden und Empfangen von Dateien über Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="10186-104">Send and receive files through your bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="10186-105">Es gibt zwei Möglichkeiten zum Senden von Dateien an und von einem Bot:</span><span class="sxs-lookup"><span data-stu-id="10186-105">There are two ways to send files to and from a bot:</span></span>

* <span data-ttu-id="10186-106">Verwenden der Microsoft Graph-APIs.</span><span class="sxs-lookup"><span data-stu-id="10186-106">Using the Microsoft Graph APIs.</span></span> <span data-ttu-id="10186-107">Diese Methode funktioniert für Bots in allen Bereiche in Teams:</span><span class="sxs-lookup"><span data-stu-id="10186-107">This method works for bots in all scopes in Teams:</span></span>
  * `personal`
  * `channel`
  * `groupchat`
* <span data-ttu-id="10186-108">Verwenden der Teams-APIs.</span><span class="sxs-lookup"><span data-stu-id="10186-108">Using the Teams APIs.</span></span> <span data-ttu-id="10186-109">Diese unterstützen nur Dateien in einem Kontext:</span><span class="sxs-lookup"><span data-stu-id="10186-109">These only support files in one context:</span></span>
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="10186-110">Verwenden der Microsoft Graph-APIs</span><span class="sxs-lookup"><span data-stu-id="10186-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="10186-111">Sie können Nachrichten mit Kartenanlagen posten, die auf vorhandene #A0 verweisen, indem Sie die Microsoft Graph-APIs für [OneDrive und SharePoint verwenden.](/onedrive/developer/rest-api/)</span><span class="sxs-lookup"><span data-stu-id="10186-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="10186-112">Die Verwendung der Graph-APIs erfordert den Zugriff auf den #A0 eines Benutzers (für und Dateien) oder die Dateien in den Kanälen eines Teams (für Dateien) über den standardmäßigen `personal` `groupchat` `channel` OAuth 2.0-Autorisierungsfluss.</span><span class="sxs-lookup"><span data-stu-id="10186-112">Using the Graph APIs requires obtaining access to a user's OneDrive folder (for `personal` and `groupchat` files) or the files in a team's channels (for `channel` files) through the standard OAuth 2.0 authorization flow.</span></span> <span data-ttu-id="10186-113">Diese Methode funktioniert in allen Teams-Bereich.</span><span class="sxs-lookup"><span data-stu-id="10186-113">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="10186-114">Verwenden der Teams Bot-APIs</span><span class="sxs-lookup"><span data-stu-id="10186-114">Using the Teams Bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="10186-115">Diese Methode funktioniert nur im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="10186-115">This method works only in the `personal` context.</span></span> <span data-ttu-id="10186-116">Es funktioniert nicht im `channel` `groupchat` Oder-Kontext.</span><span class="sxs-lookup"><span data-stu-id="10186-116">It does not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="10186-117">Ihr Bot kann Dateien mit Benutzern im Kontext, auch als persönliche Chats bezeichnet, mithilfe von `personal` Teams-APIs direkt senden und empfangen.</span><span class="sxs-lookup"><span data-stu-id="10186-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="10186-118">Auf diese Weise können Sie Spesenabrechnung, Bilderkennung, Dateiarchivierung, E-Signaturen und andere Szenarien implementieren, in denen Dateiinhalte direkt manipuliert werden.</span><span class="sxs-lookup"><span data-stu-id="10186-118">This lets you implement expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="10186-119">In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.</span><span class="sxs-lookup"><span data-stu-id="10186-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>

<span data-ttu-id="10186-120">In den folgenden Abschnitten wird beschrieben, wie Sie dies tun, um Dateiinhalte als Ergebnis einer direkten Benutzerinteraktion, z. B. das Senden einer Nachricht, zu senden.</span><span class="sxs-lookup"><span data-stu-id="10186-120">The following sections describe how to do this to send file content as a result of direct user interaction, like sending a message.</span></span> <span data-ttu-id="10186-121">Diese API wird als Teil der Microsoft Teams Bot Platform bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="10186-121">This API is provided as part of the Microsoft Teams Bot Platform.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="10186-122">Konfigurieren des Bots für die Unterstützung von Dateien</span><span class="sxs-lookup"><span data-stu-id="10186-122">Configure your bot to support files</span></span>

<span data-ttu-id="10186-123">Zum Senden und Empfangen von Dateien in Ihrem Bot müssen Sie die `supportsFiles` Eigenschaft im Manifest auf `true` festlegen.</span><span class="sxs-lookup"><span data-stu-id="10186-123">In order to send and receive files in your bot, you have to set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="10186-124">Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifestreferenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="10186-124">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="10186-125">Die Definition sieht wie dies aus: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="10186-125">The definition will look like this: `"supportsFiles": true`.</span></span> <span data-ttu-id="10186-126">Wenn Ihr Bot nicht aktiviert `supportsFiles` ist, funktionieren die folgenden Features nicht.</span><span class="sxs-lookup"><span data-stu-id="10186-126">If your bot does not enable `supportsFiles`, the following features will not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="10186-127">Empfangen von Dateien in persönlichen Chats</span><span class="sxs-lookup"><span data-stu-id="10186-127">Receiving files in personal chat</span></span>

<span data-ttu-id="10186-128">Wenn ein Benutzer eine Datei an Ihren Bot sendet, wird die Datei zuerst in den OneDrive for #A0 des Benutzers hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="10186-128">When a user sends a file to your bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="10186-129">Ihr Bot erhält dann eine Nachrichtenaktivität, die Sie über den Benutzerupload informiert.</span><span class="sxs-lookup"><span data-stu-id="10186-129">Your bot will then receive a message activity notifying you of the user upload.</span></span> <span data-ttu-id="10186-130">Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL.</span><span class="sxs-lookup"><span data-stu-id="10186-130">The activity will contain file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="10186-131">Sie können direkt aus dieser URL lesen, um den binären Inhalt zu abrufen.</span><span class="sxs-lookup"><span data-stu-id="10186-131">You can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="10186-132">Beispiel für Nachrichtenaktivität mit Dateianlage</span><span class="sxs-lookup"><span data-stu-id="10186-132">Message activity with file attachment example</span></span>

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

<span data-ttu-id="10186-133">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="10186-133">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="10186-134">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="10186-134">Property</span></span> | <span data-ttu-id="10186-135">Zweck</span><span class="sxs-lookup"><span data-stu-id="10186-135">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="10186-136">OneDrive-URL zum Abrufen des Inhalts der Datei.</span><span class="sxs-lookup"><span data-stu-id="10186-136">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="10186-137">Sie können eine direkt `HTTP GET` von dieser URL aus aus.</span><span class="sxs-lookup"><span data-stu-id="10186-137">You can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="10186-138">Eindeutige Datei-ID.</span><span class="sxs-lookup"><span data-stu-id="10186-138">Unique file ID.</span></span> <span data-ttu-id="10186-139">Dies ist die OneDrive-Laufwerkelement-ID, wenn der Benutzer eine Datei an Ihren Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="10186-139">This will be the OneDrive drive item ID, in the case of the user sending a file to your bot.</span></span> |
| `fileType` | <span data-ttu-id="10186-140">Dateierweiterungstyp, z. B. pdf oder docx.</span><span class="sxs-lookup"><span data-stu-id="10186-140">File extension type, such as pdf or docx.</span></span> |

<span data-ttu-id="10186-141">Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="10186-141">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="10186-142">Hochladen von Dateien in persönliche Chats</span><span class="sxs-lookup"><span data-stu-id="10186-142">Uploading files to personal chat</span></span>

<span data-ttu-id="10186-143">Das Hochladen einer Datei in einen Benutzer umfasst die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="10186-143">Uploading a file to a user involves the following steps:</span></span>

1. <span data-ttu-id="10186-144">Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert.</span><span class="sxs-lookup"><span data-stu-id="10186-144">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="10186-145">Diese Nachricht muss eine Anlage `FileConsentCard` mit dem Namen der datei enthalten, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="10186-145">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="10186-146">Wenn der Benutzer den Dateidownload akzeptiert, erhält ihr Bot eine *Invoke-Aktivität* mit einer Speicherort-URL.</span><span class="sxs-lookup"><span data-stu-id="10186-146">If the user accepts the file download, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="10186-147">Um die Datei zu übertragen, führt Ihr Bot `HTTP POST` eine direkt in die bereitgestellte Speicherort-URL aus.</span><span class="sxs-lookup"><span data-stu-id="10186-147">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="10186-148">Optional können Sie die ursprüngliche Zustimmungskarte entfernen, wenn Sie dem Benutzer nicht erlauben möchten, weitere Uploads derselben Datei zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="10186-148">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="10186-149">Nachricht, die die Berechtigung zum Hochladen anfordert</span><span class="sxs-lookup"><span data-stu-id="10186-149">Message requesting permission to upload</span></span>

<span data-ttu-id="10186-150">Diese Desktopnachricht enthält ein einfaches Anlagenobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="10186-150">This desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Screenshot der Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei anfordert](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="10186-152">Diese mobile Nachricht enthält ein Attachment-Objekt, das benutzerberechtigungen zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="10186-152">This mobile message contains an attachment object requesting user permission to upload the file:</span></span>

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

<span data-ttu-id="10186-154">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="10186-154">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="10186-155">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="10186-155">Property</span></span> | <span data-ttu-id="10186-156">Zweck</span><span class="sxs-lookup"><span data-stu-id="10186-156">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="10186-157">Beschreibung der Datei.</span><span class="sxs-lookup"><span data-stu-id="10186-157">Description of the file.</span></span> <span data-ttu-id="10186-158">Kann dem Benutzer angezeigt werden, um seinen Zweck zu beschreiben oder seinen Inhalt zusammenzufassen.</span><span class="sxs-lookup"><span data-stu-id="10186-158">May be shown to the user to describe its purpose or to summarize its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="10186-159">Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes in OneDrive zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="10186-159">Provides the user an estimate of the file size and the amount of space it will take in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="10186-160">Zusätzlicher Kontext, der automatisch an Ihren Bot übermittelt wird, wenn der Benutzer die Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="10186-160">Additional context that will be silently transmitted to your bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="10186-161">Zusätzlicher Kontext, der automatisch an Ihren Bot übermittelt wird, wenn der Benutzer die Datei zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="10186-161">Additional context that will be silently transmitted to your bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="10186-162">Aufrufen von Aktivitäten, wenn der Benutzer die Datei akzeptiert</span><span class="sxs-lookup"><span data-stu-id="10186-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="10186-163">Eine Aufrufaktivität wird an Ihren Bot gesendet, wenn und wann der Benutzer die Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="10186-163">An invoke activity is sent to your bot if and when the user accepts the file.</span></span> <span data-ttu-id="10186-164">Sie enthält die OneDrive for Business-Platzhalter-URL, in die Ihr Bot dann eine ausgibt, um den `PUT` Dateiinhalt zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="10186-164">It contains the OneDrive for Business placeholder URL that your bot can then issue a `PUT` into to transfer the file contents.</span></span> <span data-ttu-id="10186-165">Informationen zum Hochladen in die OneDrive-URL finden Sie in diesem Artikel: [Hochladen von Bytes in die Uploadsitzung](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="10186-165">for information on uploading to the OneDrive URL read this article: [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="10186-166">Das folgende Beispiel zeigt eine gekürzte Version der Aufrufaktivität, die Ihr Bot erhält:</span><span class="sxs-lookup"><span data-stu-id="10186-166">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

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

<span data-ttu-id="10186-167">Wenn der Benutzer die Datei zurückgibt, erhält ihr Bot das folgende Ereignis mit demselben allgemeinen Aktivitätsnamen:</span><span class="sxs-lookup"><span data-stu-id="10186-167">Similarly, if the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="10186-168">Benachrichtigen des Benutzers über eine hochgeladene Datei</span><span class="sxs-lookup"><span data-stu-id="10186-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="10186-169">Nach dem Hochladen einer Datei in das OneDrive des Benutzers, unabhängig davon, ob Sie den oben beschriebenen Mechanismus oder delegierte #A0 verwenden, sollten Sie eine Bestätigungsnachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="10186-169">After uploading a file to the user's OneDrive, whether you use the mechanism described above or OneDrive user delegated APIs, you should send a confirmation message to the user.</span></span> <span data-ttu-id="10186-170">Diese Nachricht sollte eine Anlage enthalten, auf die der Benutzer klicken kann, um eine Vorschau anzuzeigen, sie in OneDrive zu öffnen `FileCard` oder lokal herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="10186-170">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span>

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

<span data-ttu-id="10186-171">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="10186-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="10186-172">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="10186-172">Property</span></span> | <span data-ttu-id="10186-173">Zweck</span><span class="sxs-lookup"><span data-stu-id="10186-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="10186-174">OneDrive/SharePoint-Laufwerkelement-ID.</span><span class="sxs-lookup"><span data-stu-id="10186-174">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="10186-175">Dateityp, z. B. pdf oder docx.</span><span class="sxs-lookup"><span data-stu-id="10186-175">File type, such as pdf or docx.</span></span> |

### <a name="basic-example-in-c"></a><span data-ttu-id="10186-176">Grundlegendes Beispiel in C #</span><span class="sxs-lookup"><span data-stu-id="10186-176">Basic example in C#</span></span>

<span data-ttu-id="10186-177">Das folgende Beispiel zeigt, wie Sie Dateiuploads verarbeiten und Datei-Zustimmungsanforderungen im Dialogfeld Ihres Bots senden können.</span><span class="sxs-lookup"><span data-stu-id="10186-177">The following sample shows how you can handle file uploads and send file consent requests in your bot's dialog.</span></span>

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
