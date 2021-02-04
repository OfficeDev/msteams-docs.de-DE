---
title: Senden und Empfangen von Dateien über den Bot
description: Beschreibt, wie Dateien über den Bot gesendet und empfangen werden.
keywords: Teams bots files send receive
ms.date: 05/20/2019
ms.topic: how-to
ms.openlocfilehash: 07967ba4ce6d7e15e64c6f925fa588585f5a2c1d
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093276"
---
# <a name="send-and-receive-files-through-the-bot"></a><span data-ttu-id="1c734-104">Senden und Empfangen von Dateien über den Bot</span><span class="sxs-lookup"><span data-stu-id="1c734-104">Send and receive files through the bot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c734-105">Die Artikel in diesem Dokument basieren auf dem v4 Bot Framework SDK.</span><span class="sxs-lookup"><span data-stu-id="1c734-105">The articles in this document are based on the v4 Bot Framework SDK.</span></span>

<span data-ttu-id="1c734-106">Es gibt zwei Möglichkeiten, Dateien an einen Bot zu senden und von diesem zu empfangen:</span><span class="sxs-lookup"><span data-stu-id="1c734-106">There are two ways to send files to and receive files from a bot:</span></span>

* <span data-ttu-id="1c734-107">**Verwenden der Microsoft Graph-APIs:** Diese Methode funktioniert für Bots in allen Microsoft Teams-Bereich:</span><span class="sxs-lookup"><span data-stu-id="1c734-107">**Using the Microsoft Graph APIs:** This method works for bots in all Microsoft Teams scopes:</span></span>
  * `personal`
  * `channel`
  * `groupchat`

* <span data-ttu-id="1c734-108">**Verwenden der Teams-Bot-APIs:** Diese unterstützen nur Dateien im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="1c734-108">**Using the Teams bot APIs:** These only support files in `personal` context.</span></span>

## <a name="using-the-graph-apis"></a><span data-ttu-id="1c734-109">Verwenden der Graph-APIs</span><span class="sxs-lookup"><span data-stu-id="1c734-109">Using the Graph APIs</span></span>

<span data-ttu-id="1c734-110">Posten Sie Nachrichten mit Kartenanlagen, die auf vorhandene #A0 verweisen, mithilfe der #A1 für [OneDrive und SharePoint.](/onedrive/developer/rest-api/)</span><span class="sxs-lookup"><span data-stu-id="1c734-110">Post messages with card attachments that refer to existing SharePoint files, using the Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="1c734-111">Um die Graph-APIs zu verwenden, erhalten Sie Über den standardmäßigen OAuth 2.0-Autorisierungsfluss Zugriff auf eine der folgenden:</span><span class="sxs-lookup"><span data-stu-id="1c734-111">To use the Graph APIs, obtain access to either of the following through the standard OAuth 2.0 authorization flow:</span></span>
* <span data-ttu-id="1c734-112">Der #A0 eines Benutzers für `personal` und `groupchat` dateien.</span><span class="sxs-lookup"><span data-stu-id="1c734-112">A user's OneDrive folder for `personal` and `groupchat` files.</span></span>
* <span data-ttu-id="1c734-113">Die Dateien im Kanal eines Teams für `channel` Dateien.</span><span class="sxs-lookup"><span data-stu-id="1c734-113">The files in a team's channel for `channel` files.</span></span>

<span data-ttu-id="1c734-114">Graph-APIs funktionieren in allen Teams-Bereich.</span><span class="sxs-lookup"><span data-stu-id="1c734-114">Graph APIs work in all Teams scopes.</span></span>

## <a name="using-the-teams-bot-apis"></a><span data-ttu-id="1c734-115">Verwenden der Teams-Bot-APIs</span><span class="sxs-lookup"><span data-stu-id="1c734-115">Using the Teams bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="1c734-116">Teams-Bot-APIs funktionieren nur im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="1c734-116">Teams bot APIs work only in the `personal` context.</span></span> <span data-ttu-id="1c734-117">Sie funktionieren nicht im `channel` kontextbezogenen `groupchat` Kontext.</span><span class="sxs-lookup"><span data-stu-id="1c734-117">They do not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="1c734-118">Mithilfe von Teams-APIs kann der Bot Dateien direkt mit Benutzern im Kontext senden und empfangen, die auch als `personal` persönliche Chats bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="1c734-118">Using Teams APIs, the bot can directly send and receive files with users in the `personal` context, also known as personal chats.</span></span> <span data-ttu-id="1c734-119">Implementieren Sie Features wie Spesenabrechnung, Bilderkennung, Dateiarchivierung und E-Signaturen, die die Bearbeitung von Dateiinhalten beinhaltet.</span><span class="sxs-lookup"><span data-stu-id="1c734-119">Implement features, such as expense reporting, image recognition, file archival, and e-signatures involving the editing of file content.</span></span> <span data-ttu-id="1c734-120">In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.</span><span class="sxs-lookup"><span data-stu-id="1c734-120">Files shared in Teams typically appear as cards and allow rich in-app viewing.</span></span>

<span data-ttu-id="1c734-121">In den folgenden Abschnitten wird beschrieben, wie Dateiinhalte als direkte Benutzerinteraktion wie das Senden einer Nachricht gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="1c734-121">The following sections describe how to send file content as a direct user interaction, like sending a message.</span></span> <span data-ttu-id="1c734-122">Diese API wird als Teil der Teams-Bot-Plattform bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="1c734-122">This API is provided as part of the Teams bot platform.</span></span>

### <a name="configuring-the-bot-to-support-files"></a><span data-ttu-id="1c734-123">Konfigurieren des Bots zur Unterstützung von Dateien</span><span class="sxs-lookup"><span data-stu-id="1c734-123">Configuring the bot to support files</span></span>

<span data-ttu-id="1c734-124">Um Dateien im Bot zu senden und zu empfangen, legen Sie die Eigenschaft `supportsFiles` im Manifest auf `true` .</span><span class="sxs-lookup"><span data-stu-id="1c734-124">To send and receive files in the bot, set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="1c734-125">Diese Eigenschaft wird im Abschnitt ["Bots"](~/resources/schema/manifest-schema.md#bots) der Manifestreferenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1c734-125">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="1c734-126">Die Definition sieht wie hier aus: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="1c734-126">The definition looks like this, `"supportsFiles": true`.</span></span> <span data-ttu-id="1c734-127">Wenn der Bot nicht aktiviert wird, funktionieren die in diesem Abschnitt `supportsFiles` aufgeführten Features nicht.</span><span class="sxs-lookup"><span data-stu-id="1c734-127">If the bot does not enable `supportsFiles`, the features listed in this section do not work.</span></span>

### <a name="receiving-files-in-personal-chat"></a><span data-ttu-id="1c734-128">Empfangen von Dateien in persönlichen Chats</span><span class="sxs-lookup"><span data-stu-id="1c734-128">Receiving files in personal chat</span></span>

<span data-ttu-id="1c734-129">Wenn ein Benutzer eine Datei an den Bot sendet, wird die Datei zuerst in den OneDrive for #A0 des Benutzers hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="1c734-129">When a user sends a file to the bot, the file is first uploaded to the user's OneDrive for Business storage.</span></span> <span data-ttu-id="1c734-130">Der Bot empfängt dann eine Nachrichtenaktivität, die den Benutzer über den Benutzerupload informiert.</span><span class="sxs-lookup"><span data-stu-id="1c734-130">The bot then receives a message activity notifying the user about the user upload.</span></span> <span data-ttu-id="1c734-131">Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL.</span><span class="sxs-lookup"><span data-stu-id="1c734-131">The activity contains file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="1c734-132">Der Benutzer kann direkt von dieser URL lesen, um dessen binären Inhalt zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1c734-132">The user can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="1c734-133">Beispiel für Nachrichtenaktivität mit Dateianlage</span><span class="sxs-lookup"><span data-stu-id="1c734-133">Message activity with file attachment example</span></span>

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

<span data-ttu-id="1c734-134">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="1c734-134">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="1c734-135">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1c734-135">Property</span></span> | <span data-ttu-id="1c734-136">Zweck</span><span class="sxs-lookup"><span data-stu-id="1c734-136">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="1c734-137">OneDrive-URL zum Abrufen des Inhalts der Datei.</span><span class="sxs-lookup"><span data-stu-id="1c734-137">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="1c734-138">Der Benutzer kann eine direkt `HTTP GET` von dieser URL aus aussenen.</span><span class="sxs-lookup"><span data-stu-id="1c734-138">The user can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="1c734-139">Eindeutige Datei-ID.</span><span class="sxs-lookup"><span data-stu-id="1c734-139">Unique file ID.</span></span> <span data-ttu-id="1c734-140">Dies ist die OneDrive-Laufwerkelement-ID, falls der Benutzer eine Datei an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="1c734-140">This is the OneDrive drive item ID, in case the user sends a file to the bot.</span></span> |
| `fileType` | <span data-ttu-id="1c734-141">Dateityp, z. B. PDF oder DOCX.</span><span class="sxs-lookup"><span data-stu-id="1c734-141">Type of file, such as .pdf or .docx.</span></span> |

<span data-ttu-id="1c734-142">Als bewährte Methode sollten Sie den Dateiupload bestätigen, indem Sie eine Nachricht an den Benutzer zurücksenden.</span><span class="sxs-lookup"><span data-stu-id="1c734-142">As a best practice, acknowledge the file upload by sending a message back to the user.</span></span>

### <a name="uploading-files-to-personal-chat"></a><span data-ttu-id="1c734-143">Hochladen von Dateien in persönliche Chats</span><span class="sxs-lookup"><span data-stu-id="1c734-143">Uploading files to personal chat</span></span>

<span data-ttu-id="1c734-144">Die folgenden Schritte sind erforderlich, um eine Datei an einen Benutzer hochzuladen:</span><span class="sxs-lookup"><span data-stu-id="1c734-144">The following steps are required to upload a file to a user:</span></span>

1. <span data-ttu-id="1c734-145">Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert.</span><span class="sxs-lookup"><span data-stu-id="1c734-145">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="1c734-146">Diese Nachricht muss eine Anlage `FileConsentCard` mit dem Namen der hochladenen Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="1c734-146">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="1c734-147">Wenn der Benutzer den Dateidownload akzeptiert, empfängt der Bot eine Aufrufaktivität mit einer Orts-URL.</span><span class="sxs-lookup"><span data-stu-id="1c734-147">If the user accepts the file download, the bot receives an invoke activity with a location URL.</span></span>
3. <span data-ttu-id="1c734-148">Um die Datei zu übertragen, führt der Bot eine `HTTP POST` direkt in die bereitgestellte Speicherort-URL aus.</span><span class="sxs-lookup"><span data-stu-id="1c734-148">To transfer the file, the bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="1c734-149">Entfernen Sie optional die ursprüngliche Zustimmungskarte, wenn Sie nicht möchten, dass der Benutzer weitere Uploads derselben Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="1c734-149">Optionally, remove the original consent card if you do not want the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="1c734-150">Nachricht, die die Berechtigung zum Hochladen anfordert</span><span class="sxs-lookup"><span data-stu-id="1c734-150">Message requesting permission to upload</span></span>

<span data-ttu-id="1c734-151">Die folgende Desktopnachricht enthält ein einfaches Anlagenobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="1c734-151">The following desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei anfordert](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="1c734-153">Die folgende Mobiltelefonnachricht enthält ein Anlagenobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="1c734-153">The following mobile message contains an attachment object requesting user permission to upload the file:</span></span>

![Zustimmungskarte, die die Benutzerberechtigung zum Hochladen von Dateien auf mobilgeräte anfordert](../../assets/images/bots/mobile-bot-file-consent-card.png)

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

<span data-ttu-id="1c734-155">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="1c734-155">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="1c734-156">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1c734-156">Property</span></span> | <span data-ttu-id="1c734-157">Zweck</span><span class="sxs-lookup"><span data-stu-id="1c734-157">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="1c734-158">Beschreibt den Zweck der Datei oder fasst den Inhalt zusammen.</span><span class="sxs-lookup"><span data-stu-id="1c734-158">Describes the purpose of the file or summarizes its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="1c734-159">Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes in OneDrive zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1c734-159">Provides the user an estimate of the file size and the amount of space it takes in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="1c734-160">Zusätzlicher Kontext, der automatisch an den Bot übermittelt wird, wenn der Benutzer die Datei annimmt.</span><span class="sxs-lookup"><span data-stu-id="1c734-160">Additional context that is silently transmitted to the bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="1c734-161">Zusätzlicher Kontext, der automatisch an den Bot übermittelt wird, wenn der Benutzer die Datei abgibt.</span><span class="sxs-lookup"><span data-stu-id="1c734-161">Additional context that is silently transmitted to the bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="1c734-162">Aktivität aufrufen, wenn der Benutzer die Datei annimmt</span><span class="sxs-lookup"><span data-stu-id="1c734-162">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="1c734-163">Eine Aufrufaktivität wird an den Bot gesendet, wenn und wann der Benutzer die Datei annimmt.</span><span class="sxs-lookup"><span data-stu-id="1c734-163">An invoke activity is sent to the bot if and when the user accepts the file.</span></span> <span data-ttu-id="1c734-164">Sie enthält die OneDrive for Business-Platzhalter-URL, die der Bot dann ausgibt, `PUT` um den Dateiinhalt zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="1c734-164">It contains the OneDrive for Business placeholder URL that the bot can then issue a `PUT` to transfer the file contents.</span></span> <span data-ttu-id="1c734-165">Informationen zum Hochladen auf die OneDrive-URL finden Sie unter [Hochladen von Bytes in die Uploadsitzung.](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session)</span><span class="sxs-lookup"><span data-stu-id="1c734-165">For information on uploading to the OneDrive URL, see [upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="1c734-166">Das folgende Beispiel zeigt eine kurze Version der Aufrufaktivität, die der Bot empfängt:</span><span class="sxs-lookup"><span data-stu-id="1c734-166">The following example shows a concise version of the invoke activity that the bot receives:</span></span>

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

<span data-ttu-id="1c734-167">Ebenso empfängt der Bot das folgende Ereignis mit demselben Allgemeinen Aktivitätsnamen, wenn der Benutzer die Datei abgibt:</span><span class="sxs-lookup"><span data-stu-id="1c734-167">Similarly, if the user declines the file, the bot receives the following event with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="1c734-168">Benachrichtigen des Benutzers über eine hochgeladene Datei</span><span class="sxs-lookup"><span data-stu-id="1c734-168">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="1c734-169">Nachdem Sie eine Datei auf das OneDrive des Benutzers hochgeladen haben, senden Sie eine Bestätigungsnachricht an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="1c734-169">After uploading a file to the user's OneDrive, send a confirmation message to the user.</span></span> <span data-ttu-id="1c734-170">Die Nachricht muss die folgende Anlage enthalten, die der Benutzer auswählen kann, um eine Vorschau anzuzeigen oder sie in OneDrive zu öffnen oder lokal `FileCard` herunterzuladen:</span><span class="sxs-lookup"><span data-stu-id="1c734-170">The message must contain the following `FileCard` attachment that the user can select, either to preview or open it in OneDrive, or download locally:</span></span>

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

<span data-ttu-id="1c734-171">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="1c734-171">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="1c734-172">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1c734-172">Property</span></span> | <span data-ttu-id="1c734-173">Zweck</span><span class="sxs-lookup"><span data-stu-id="1c734-173">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="1c734-174">OneDrive- oder SharePoint-Laufwerkelement-ID.</span><span class="sxs-lookup"><span data-stu-id="1c734-174">OneDrive or SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="1c734-175">Dateityp, z. B. PDF oder DOCX.</span><span class="sxs-lookup"><span data-stu-id="1c734-175">Type of file, such as .pdf or .docx.</span></span> |

### <a name="fetching-inline-images-from-message"></a><span data-ttu-id="1c734-176">Abrufen von Inlinebildern aus einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="1c734-176">Fetching inline images from message</span></span>

<span data-ttu-id="1c734-177">Rufen Sie Inlinebilder ab, die Teil der Nachricht sind, indem Sie das Zugriffstoken des Bots verwenden.</span><span class="sxs-lookup"><span data-stu-id="1c734-177">Fetch inline images that are part of the message using the Bot's access token.</span></span>

![Inlinebild](../../assets/images/bots/inline-image.png)

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

### <a name="basic-example-in-c"></a><span data-ttu-id="1c734-179">Einfaches Beispiel in C #</span><span class="sxs-lookup"><span data-stu-id="1c734-179">Basic example in C#</span></span>

<span data-ttu-id="1c734-180">Das folgende Beispiel zeigt, wie Sie Dateiuploads verarbeiten und Zustimmungsanforderungen für Dateien im Dialogfeld des Bots senden:</span><span class="sxs-lookup"><span data-stu-id="1c734-180">The following sample shows how to handle file uploads and send file consent requests in the bot's dialog:</span></span>

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

### <a name="code-sample"></a><span data-ttu-id="1c734-181">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1c734-181">Code sample</span></span>

|<span data-ttu-id="1c734-182">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="1c734-182">**Sample name**</span></span> | <span data-ttu-id="1c734-183">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="1c734-183">**Description**</span></span> | <span data-ttu-id="1c734-184">**. NETCore**</span><span class="sxs-lookup"><span data-stu-id="1c734-184">**.NETCore**</span></span> | <span data-ttu-id="1c734-185">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="1c734-185">**Javascript**</span></span> | <span data-ttu-id="1c734-186">**Python**</span><span class="sxs-lookup"><span data-stu-id="1c734-186">**Python**</span></span>|
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="1c734-187">File upload</span><span class="sxs-lookup"><span data-stu-id="1c734-187">File upload</span></span> | <span data-ttu-id="1c734-188">Veranschaulicht, wie Sie von einem Bot die Dateizuwilligung erhalten und Dateien in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="1c734-188">Demonstrates how to obtain file consent and upload files to Teams from a bot.</span></span> <span data-ttu-id="1c734-189">Außerdem erfahren Sie, wie Sie eine an einen Bot gesendete Datei erhalten.</span><span class="sxs-lookup"><span data-stu-id="1c734-189">Also, how to receive a file sent to a bot.</span></span> | [<span data-ttu-id="1c734-190">View</span><span class="sxs-lookup"><span data-stu-id="1c734-190">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/56.teams-file-upload) | [<span data-ttu-id="1c734-191">View</span><span class="sxs-lookup"><span data-stu-id="1c734-191">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/56.teams-file-upload) | [<span data-ttu-id="1c734-192">View</span><span class="sxs-lookup"><span data-stu-id="1c734-192">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/56.teams-file-upload) |
