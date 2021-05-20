---
title: Senden und Empfangen von Dateien von einem Bot
description: Beschreibt das Senden und Empfangen von Dateien von einem Bot
keywords: Teams Bots-Dateien senden Empfang
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: f69a6ca9cfcdf3b1e559fbe8cf569accf3166f69
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566481"
---
# <a name="send-and-receive-files-through-your-bot"></a><span data-ttu-id="723ef-104">Senden und Empfangen von Dateien über Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="723ef-104">Send and receive files through your bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="723ef-105">Es gibt zwei Möglichkeiten, Dateien an und von einem Bot zu senden:</span><span class="sxs-lookup"><span data-stu-id="723ef-105">There are two ways to send files to and from a bot:</span></span>

* <span data-ttu-id="723ef-106">Verwenden der Microsoft Graph-APIs.</span><span class="sxs-lookup"><span data-stu-id="723ef-106">Using the Microsoft Graph APIs.</span></span> <span data-ttu-id="723ef-107">Diese Methode funktioniert für Bots in allen Bereichen in Teams:</span><span class="sxs-lookup"><span data-stu-id="723ef-107">This method works for bots in all scopes in Teams:</span></span>
  * `personal`
  * `channel`
  * `groupchat`
* <span data-ttu-id="723ef-108">Verwenden der Teams-APIs.</span><span class="sxs-lookup"><span data-stu-id="723ef-108">Using the Teams APIs.</span></span> <span data-ttu-id="723ef-109">Diese unterstützen nur Dateien in einem Kontext:</span><span class="sxs-lookup"><span data-stu-id="723ef-109">These only support files in one context:</span></span>
  * `personal`

## <a name="using-the-microsoft-graph-apis"></a><span data-ttu-id="723ef-110">Verwenden der Microsoft Graph-APIs</span><span class="sxs-lookup"><span data-stu-id="723ef-110">Using the Microsoft Graph APIs</span></span>

<span data-ttu-id="723ef-111">Sie können Nachrichten mit Kartenanlagen veröffentlichen, die auf vorhandene SharePoint Dateien verweisen, indem Sie die Microsoft Graph-APIs für [OneDrive und SharePoint](/onedrive/developer/rest-api/)verwenden.</span><span class="sxs-lookup"><span data-stu-id="723ef-111">You can post messages with card attachments referencing existing SharePoint files using the Microsoft Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="723ef-112">Die Verwendung der Graph-APIs erfordert den Zugriff auf den OneDrive Ordner eines Benutzers (für `personal` und `groupchat` Dateien) oder die Dateien in den Kanälen eines Teams (für `channel` Dateien) über den standardmäßigen OAuth 2.0-Autorisierungsfluss.</span><span class="sxs-lookup"><span data-stu-id="723ef-112">Using the Graph APIs requires obtaining access to a user's OneDrive folder (for `personal` and `groupchat` files) or the files in a team's channels (for `channel` files) through the standard OAuth 2.0 authorization flow.</span></span> <span data-ttu-id="723ef-113">Diese Methode funktioniert in allen Teams Bereichen.</span><span class="sxs-lookup"><span data-stu-id="723ef-113">This method works in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="723ef-114">Verwenden der Teams-Bot-APIs</span><span class="sxs-lookup"><span data-stu-id="723ef-114">Using the Teams Bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="723ef-115">Diese Methode funktioniert nur im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="723ef-115">This method works only in the `personal` context.</span></span> <span data-ttu-id="723ef-116">Es funktioniert nicht im `channel` `groupchat` Oder-Kontext.</span><span class="sxs-lookup"><span data-stu-id="723ef-116">It does not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="723ef-117">Ihr Bot kann Dateien direkt mit Benutzern im Kontext senden und `personal` empfangen, die auch als persönliche Chats bezeichnet werden, indem er Teams APIs verwendet.</span><span class="sxs-lookup"><span data-stu-id="723ef-117">Your bot can directly send and receive files with users in the `personal` context, also known as personal chats, using Teams APIs.</span></span> <span data-ttu-id="723ef-118">Auf diese Weise können Sie Spesenabrechnung, Bilderkennung, Dateiarchivierung, E-Signaturen und andere Szenarien implementieren, in denen Dateiinhalte direkt manipuliert werden.</span><span class="sxs-lookup"><span data-stu-id="723ef-118">This lets you implement expense reporting, image recognition, file archival, e-signatures, and other scenarios involving direct manipulation of file content.</span></span> <span data-ttu-id="723ef-119">In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.</span><span class="sxs-lookup"><span data-stu-id="723ef-119">Files shared in Teams typically appear as cards, and allow rich in-app viewing.</span></span>

<span data-ttu-id="723ef-120">In den folgenden Abschnitten wird beschrieben, wie Sie Dateiinhalte als Ergebnis einer direkten Benutzerinteraktion senden können, z. B. beim Senden einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="723ef-120">The following sections describe how to do this to send file content as a result of direct user interaction, like sending a message.</span></span> <span data-ttu-id="723ef-121">Diese API wird als Teil der Microsoft Teams Bot Platform bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="723ef-121">This API is provided as part of the Microsoft Teams Bot Platform.</span></span>

### <a name="configure-your-bot-to-support-files"></a><span data-ttu-id="723ef-122">Konfigurieren Sie Ihren Bot für die Unterstützung von Dateien</span><span class="sxs-lookup"><span data-stu-id="723ef-122">Configure your bot to support files</span></span>

<span data-ttu-id="723ef-123">Um Dateien in Ihrem Bot zu senden und zu empfangen, müssen Sie die `supportsFiles` Eigenschaft im Manifest auf `true` festlegen.</span><span class="sxs-lookup"><span data-stu-id="723ef-123">In order to send and receive files in your bot, you have to set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="723ef-124">Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifest-Referenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="723ef-124">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="723ef-125">Die Definition sieht wie folgt aus: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="723ef-125">The definition will look like this: `"supportsFiles": true`.</span></span> <span data-ttu-id="723ef-126">Wenn Ihr Bot nicht aktiviert `supportsFiles` wird, funktionieren die folgenden Funktionen nicht.</span><span class="sxs-lookup"><span data-stu-id="723ef-126">If your bot does not enable `supportsFiles`, the following features will not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="723ef-127">Empfangen von Dateien im persönlichen Chat</span><span class="sxs-lookup"><span data-stu-id="723ef-127">Receiving files in personal chat</span></span>

<span data-ttu-id="723ef-128">Wenn ein Benutzer eine Datei an Ihren Bot sendet, wird die Datei zuerst in den OneDrive for Business Speicher des Benutzers hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="723ef-128">When a user sends a file to your bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="723ef-129">Ihr Bot erhält dann eine Nachrichtenaktivität, die Sie über den Upload des Benutzers informiert.</span><span class="sxs-lookup"><span data-stu-id="723ef-129">Your bot will then receive a message activity notifying you of the user upload.</span></span> <span data-ttu-id="723ef-130">Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL.</span><span class="sxs-lookup"><span data-stu-id="723ef-130">The activity will contain file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="723ef-131">Sie können direkt von dieser URL lesen, um den binären Inhalt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="723ef-131">You can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="723ef-132">Nachrichtenaktivität mit Dateianhangsbeispiel</span><span class="sxs-lookup"><span data-stu-id="723ef-132">Message activity with file attachment example</span></span>

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

<span data-ttu-id="723ef-133">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="723ef-133">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="723ef-134">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="723ef-134">Property</span></span> | <span data-ttu-id="723ef-135">Zweck</span><span class="sxs-lookup"><span data-stu-id="723ef-135">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="723ef-136">OneDrive URL zum Abrufen des Dateiinhalts.</span><span class="sxs-lookup"><span data-stu-id="723ef-136">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="723ef-137">Sie können eine `HTTP GET` direkt von dieser URL ausstellen.</span><span class="sxs-lookup"><span data-stu-id="723ef-137">You can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="723ef-138">Eindeutige Datei-ID.</span><span class="sxs-lookup"><span data-stu-id="723ef-138">Unique file ID.</span></span> <span data-ttu-id="723ef-139">Dies ist die OneDrive Laufwerkselement-ID, wenn der Benutzer eine Datei an Ihren Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="723ef-139">This will be the OneDrive drive item ID, in the case of the user sending a file to your bot.</span></span> |
| `fileType` | <span data-ttu-id="723ef-140">Dateierweiterungstyp, z. B. pdf oder docx.</span><span class="sxs-lookup"><span data-stu-id="723ef-140">File extension type, such as pdf or docx.</span></span> |

<span data-ttu-id="723ef-141">Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer zurücksenden.</span><span class="sxs-lookup"><span data-stu-id="723ef-141">As a best practice, you should acknowledge the file upload by sending back a message to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="723ef-142">Hochladen von Dateien in den persönlichen Chat</span><span class="sxs-lookup"><span data-stu-id="723ef-142">Uploading files to personal chat</span></span>

<span data-ttu-id="723ef-143">Das Hochladen einer Datei in einen Benutzer umfasst die folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="723ef-143">Uploading a file to a user involves the following steps:</span></span>

1. <span data-ttu-id="723ef-144">Senden Sie eine Nachricht an den Benutzer, in der die Berechtigung zum Schreiben der Datei angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="723ef-144">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="723ef-145">Diese Nachricht muss eine `FileConsentCard` Anlage mit dem Namen der datei enthalten, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="723ef-145">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="723ef-146">Wenn der Benutzer den Dateidownload akzeptiert, erhält Ihr Bot eine *Invoke-Aktivität* mit einer Standort-URL.</span><span class="sxs-lookup"><span data-stu-id="723ef-146">If the user accepts the file download, your bot will receive an *Invoke* activity with a location URL.</span></span>
3. <span data-ttu-id="723ef-147">Um die Datei zu übertragen, führt Ihr Bot eine `HTTP POST` direkt in die angegebene Standort-URL aus.</span><span class="sxs-lookup"><span data-stu-id="723ef-147">To transfer the file, your bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="723ef-148">Optional können Sie die ursprüngliche Zustimmungskarte entfernen, wenn Sie dem Benutzer nicht erlauben möchten, weitere Uploads derselben Datei zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="723ef-148">Optionally, you can remove the original consent card if you do not want to allow the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="723ef-149">Nachricht, die die Berechtigung zum Hochladen anfordert</span><span class="sxs-lookup"><span data-stu-id="723ef-149">Message requesting permission to upload</span></span>

<span data-ttu-id="723ef-150">Diese Desktopnachricht enthält ein einfaches Anlageobjekt, das die Berechtigung des Benutzers zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="723ef-150">This desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Screenshot der Zustimmungskarte, auf der Benutzer die Berechtigung zum Hochladen der Datei anfordert](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="723ef-152">Diese mobile Nachricht enthält ein Anlageobjekt, das benutzerberechtigt zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="723ef-152">This mobile message contains an attachment object requesting user permission to upload the file:</span></span>

![Screenshot der Zustimmungskarte, auf der benutzerberechtigt die Berechtigung zum Hochladen von Dateien auf Mobilgeräten angefordert wird](../../assets/images/bots/mobile-bot-file-consent-card.png)

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

<span data-ttu-id="723ef-154">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="723ef-154">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="723ef-155">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="723ef-155">Property</span></span> | <span data-ttu-id="723ef-156">Zweck</span><span class="sxs-lookup"><span data-stu-id="723ef-156">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="723ef-157">Beschreibung der Datei.</span><span class="sxs-lookup"><span data-stu-id="723ef-157">Description of the file.</span></span> <span data-ttu-id="723ef-158">Kann dem Benutzer angezeigt werden, um seinen Zweck zu beschreiben oder seinen Inhalt zusammenzufassen.</span><span class="sxs-lookup"><span data-stu-id="723ef-158">May be shown to the user to describe its purpose or to summarize its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="723ef-159">Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes bereit, der in OneDrive belegt wird.</span><span class="sxs-lookup"><span data-stu-id="723ef-159">Provides the user an estimate of the file size and the amount of space it will take in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="723ef-160">Zusätzlicher Kontext, der im Hintergrund an Ihren Bot übertragen wird, wenn der Benutzer die Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="723ef-160">Additional context that will be silently transmitted to your bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="723ef-161">Zusätzlicher Kontext, der im Hintergrund an Ihren Bot übertragen wird, wenn der Benutzer die Datei ablehnt.</span><span class="sxs-lookup"><span data-stu-id="723ef-161">Additional context that will be silently transmitted to your bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="723ef-162">Aufrufen der Aktivität, wenn der Benutzer die Datei akzeptiert</span><span class="sxs-lookup"><span data-stu-id="723ef-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="723ef-163">Eine Aufrufaktivität wird an Ihren Bot gesendet, wenn der Benutzer die Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="723ef-163">An invoke activity is sent to your bot if and when the user accepts the file.</span></span> <span data-ttu-id="723ef-164">Es enthält die OneDrive for Business Platzhalter-URL, die Ihr Bot dann ausstellen `PUT` kann, um den Dateiinhalt zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="723ef-164">It contains the OneDrive for Business placeholder URL that your bot can then issue a `PUT` into to transfer the file contents.</span></span> <span data-ttu-id="723ef-165">Informationen zum Hochladen in die OneDrive-URL finden Sie in diesem Artikel: [Hochladen Bytes zur Upload-Sitzung](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="723ef-165">for information on uploading to the OneDrive URL read this article: [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="723ef-166">Das folgende Beispiel zeigt eine gekürzte Version der Aufrufaktivität, die Ihr Bot erhält:</span><span class="sxs-lookup"><span data-stu-id="723ef-166">The following example shows an abridged version of the invoke activity that your bot will receive:</span></span>

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

<span data-ttu-id="723ef-167">Wenn der Benutzer die Datei ablehnt, erhält Ihr Bot das folgende Ereignis mit demselben allgemeinen Aktivitätsnamen:</span><span class="sxs-lookup"><span data-stu-id="723ef-167">Similarly, if the user declines the file, your bot will receive the following event, with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="723ef-168">Benachrichtigung des Benutzers über eine hochgeladene Datei</span><span class="sxs-lookup"><span data-stu-id="723ef-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="723ef-169">Nach dem Hochladen einer Datei in die OneDrive des Benutzers, unabhängig davon, ob Sie den oben beschriebenen Mechanismus verwenden oder OneDrive vom Benutzer delegierte APIs verwenden, sollten Sie eine Bestätigungsnachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="723ef-169">After uploading a file to the user's OneDrive, whether you use the mechanism described above or OneDrive user delegated APIs, you should send a confirmation message to the user.</span></span> <span data-ttu-id="723ef-170">Diese Meldung sollte eine Anlage enthalten, `FileCard` auf die der Benutzer klicken kann, entweder um eine Vorschau anzuzeigen, sie in OneDrive zu öffnen oder lokal herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="723ef-170">This message should contain  a `FileCard` attachment that the user can click on, either to preview it, open it in OneDrive, or download locally.</span></span>

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

<span data-ttu-id="723ef-171">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="723ef-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="723ef-172">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="723ef-172">Property</span></span> | <span data-ttu-id="723ef-173">Zweck</span><span class="sxs-lookup"><span data-stu-id="723ef-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="723ef-174">OneDrive/SharePoint Laufwerkelement-ID.</span><span class="sxs-lookup"><span data-stu-id="723ef-174">OneDrive/SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="723ef-175">Dateityp, z. B. pdf oder docx.</span><span class="sxs-lookup"><span data-stu-id="723ef-175">File type, such as pdf or docx.</span></span> |

### <a name="basic-example-in-c"></a><span data-ttu-id="723ef-176">Grundlegendes Beispiel in C #</span><span class="sxs-lookup"><span data-stu-id="723ef-176">Basic example in C#</span></span>

<span data-ttu-id="723ef-177">Das folgende Beispiel zeigt, wie Sie Datei-Uploads verarbeiten und Dateizustimmungsanfragen im Dialogfeld Ihres Bots senden können:</span><span class="sxs-lookup"><span data-stu-id="723ef-177">The following sample shows how you can handle file uploads and send file consent requests in your bot's dialog:</span></span>

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
