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
# <a name="send-and-receive-files-through-the-bot"></a><span data-ttu-id="8287c-104">Senden und Empfangen von Dateien über den Bot</span><span class="sxs-lookup"><span data-stu-id="8287c-104">Send and receive files through the bot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8287c-105">Die Artikel in diesem Dokument basieren auf dem v4 Bot Framework SDK.</span><span class="sxs-lookup"><span data-stu-id="8287c-105">The articles in this document are based on the v4 Bot Framework SDK.</span></span>

<span data-ttu-id="8287c-106">Es gibt zwei Möglichkeiten zum Senden und Empfangen von Dateien von einem Bot:</span><span class="sxs-lookup"><span data-stu-id="8287c-106">There are two ways to send files to and receive files from a bot:</span></span>

* <span data-ttu-id="8287c-107">[**Verwenden Sie die Microsoft Graph-APIs:**](#use-the-graph-apis) Diese Methode funktioniert für Bots in allen Microsoft Teams-Bereiche:</span><span class="sxs-lookup"><span data-stu-id="8287c-107">[**Use the Microsoft Graph APIs:**](#use-the-graph-apis) This method works for bots in all Microsoft Teams scopes:</span></span>
  * `personal`
  * `channel`
  * `groupchat`

* <span data-ttu-id="8287c-108">[**Verwenden Sie die Teams-Bot-APIs:**](#use-the-teams-bot-apis) Diese unterstützen nur Dateien im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="8287c-108">[**Use the Teams bot APIs:**](#use-the-teams-bot-apis) These only support files in `personal` context.</span></span>

## <a name="use-the-graph-apis"></a><span data-ttu-id="8287c-109">Verwenden der Graph-APIs</span><span class="sxs-lookup"><span data-stu-id="8287c-109">Use the Graph APIs</span></span>

<span data-ttu-id="8287c-110">Posten von Nachrichten mit Kartenanlagen, die auf vorhandene #A0 verweisen, mithilfe der Graph-APIs für [OneDrive und SharePoint](/onedrive/developer/rest-api/).</span><span class="sxs-lookup"><span data-stu-id="8287c-110">Post messages with card attachments that refer to existing SharePoint files, using the Graph APIs for [OneDrive and SharePoint](/onedrive/developer/rest-api/).</span></span> <span data-ttu-id="8287c-111">Um die Graph-APIs zu verwenden, erhalten Sie über den standardmäßigen OAuth 2.0-Autorisierungsfluss Zugriff auf eine der folgenden:</span><span class="sxs-lookup"><span data-stu-id="8287c-111">To use the Graph APIs, obtain access to either of the following through the standard OAuth 2.0 authorization flow:</span></span>

* <span data-ttu-id="8287c-112">Der #A0 eines Benutzers für `personal` und `groupchat` Dateien.</span><span class="sxs-lookup"><span data-stu-id="8287c-112">A user's OneDrive folder for `personal` and `groupchat` files.</span></span>
* <span data-ttu-id="8287c-113">Die Dateien im Kanal eines Teams für `channel` Dateien.</span><span class="sxs-lookup"><span data-stu-id="8287c-113">The files in a team's channel for `channel` files.</span></span>

<span data-ttu-id="8287c-114">Graph-APIs funktionieren in allen Teams-Bereich.</span><span class="sxs-lookup"><span data-stu-id="8287c-114">Graph APIs work in all Teams scopes.</span></span> <span data-ttu-id="8287c-115">Weitere Informationen finden Sie unter [Senden von Chatnachrichtendateianlagen](/graph/api/chatmessage-post?view=graph-rest-beta&tabs=http#example-4-file-attachments&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="8287c-115">For more information, see [send chat message file attachments](/graph/api/chatmessage-post?view=graph-rest-beta&tabs=http#example-4-file-attachments&preserve-view=true).</span></span>

<span data-ttu-id="8287c-116">Alternativ können Sie Dateien mithilfe der Teams-Bot-APIs an einen Bot senden und von diesem empfangen.</span><span class="sxs-lookup"><span data-stu-id="8287c-116">Alternately, you can send files to and receive files from a bot using the Teams bot APIs.</span></span>

## <a name="use-the-teams-bot-apis"></a><span data-ttu-id="8287c-117">Verwenden der Teams-Bot-APIs</span><span class="sxs-lookup"><span data-stu-id="8287c-117">Use the Teams bot APIs</span></span>

> [!NOTE]
> <span data-ttu-id="8287c-118">Teams-Bot-APIs funktionieren nur im `personal` Kontext.</span><span class="sxs-lookup"><span data-stu-id="8287c-118">Teams bot APIs work only in the `personal` context.</span></span> <span data-ttu-id="8287c-119">Sie funktionieren nicht im `channel` `groupchat` Oder-Kontext.</span><span class="sxs-lookup"><span data-stu-id="8287c-119">They do not work in the `channel` or `groupchat` context.</span></span>

<span data-ttu-id="8287c-120">Mithilfe von Teams-APIs kann der Bot Dateien direkt mit Benutzern im Kontext senden und empfangen, auch als `personal` persönliche Chats bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8287c-120">Using Teams APIs, the bot can directly send and receive files with users in the `personal` context, also known as personal chats.</span></span> <span data-ttu-id="8287c-121">Implementieren Sie Features, z. B. Spesenabrechnung, Bilderkennung, Dateiarchivierung und E-Signaturen, die die Bearbeitung von Dateiinhalten enthalten.</span><span class="sxs-lookup"><span data-stu-id="8287c-121">Implement features, such as expense reporting, image recognition, file archival, and e-signatures involving the editing of file content.</span></span> <span data-ttu-id="8287c-122">In Teams freigegebene Dateien werden in der Regel als Karten angezeigt und ermöglichen eine umfassende Anzeige in der App.</span><span class="sxs-lookup"><span data-stu-id="8287c-122">Files shared in Teams typically appear as cards and allow rich in-app viewing.</span></span>

<span data-ttu-id="8287c-123">In den nächsten Abschnitten wird beschrieben, wie Dateiinhalte als direkte Benutzerinteraktion gesendet werden, z. B. das Senden einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="8287c-123">The next sections describe how to send file content as direct user interaction, like sending a message.</span></span> <span data-ttu-id="8287c-124">Diese API wird als Teil der Teams-Bot-Plattform bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8287c-124">This API is provided as part of the Teams bot platform.</span></span>

### <a name="configure-the-bot-to-support-files"></a><span data-ttu-id="8287c-125">Konfigurieren des Bots für die Unterstützung von Dateien</span><span class="sxs-lookup"><span data-stu-id="8287c-125">Configure the bot to support files</span></span>

<span data-ttu-id="8287c-126">Wenn Sie Dateien im Bot senden und empfangen möchten, legen Sie die `supportsFiles` Eigenschaft im Manifest auf . `true`</span><span class="sxs-lookup"><span data-stu-id="8287c-126">To send and receive files in the bot, set the `supportsFiles` property in the manifest to `true`.</span></span> <span data-ttu-id="8287c-127">Diese Eigenschaft wird im Abschnitt [Bots](~/resources/schema/manifest-schema.md#bots) der Manifestreferenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8287c-127">This property is described in the [bots](~/resources/schema/manifest-schema.md#bots) section of the Manifest reference.</span></span>

<span data-ttu-id="8287c-128">Die Definition sieht wie dies aus: `"supportsFiles": true` .</span><span class="sxs-lookup"><span data-stu-id="8287c-128">The definition looks like this, `"supportsFiles": true`.</span></span> <span data-ttu-id="8287c-129">Wenn der Bot nicht aktiviert ist, funktionieren die in diesem Abschnitt aufgeführten `supportsFiles` Features nicht.</span><span class="sxs-lookup"><span data-stu-id="8287c-129">If the bot does not enable `supportsFiles`, the features listed in this section do not work.</span></span>

### <a name="receive-files-in-personal-chat"></a><span data-ttu-id="8287c-130">Empfangen von Dateien in persönlichen Chats</span><span class="sxs-lookup"><span data-stu-id="8287c-130">Receive files in personal chat</span></span>

<span data-ttu-id="8287c-131">Wenn ein Benutzer eine Datei an den Bot sendet, wird die Datei zuerst in den OneDrive for Business-Speicher des Benutzers hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="8287c-131">When a user sends a file to the bot, the file is first uploaded to the user's OneDrive for business storage.</span></span> <span data-ttu-id="8287c-132">Der Bot empfängt dann eine Nachrichtenaktivität, die den Benutzer über den Benutzerupload informiert.</span><span class="sxs-lookup"><span data-stu-id="8287c-132">The bot then receives a message activity notifying the user about the user upload.</span></span> <span data-ttu-id="8287c-133">Die Aktivität enthält Dateimetadaten, z. B. den Namen und die Inhalts-URL.</span><span class="sxs-lookup"><span data-stu-id="8287c-133">The activity contains file metadata, such as its name and the content URL.</span></span> <span data-ttu-id="8287c-134">Der Benutzer kann direkt aus dieser URL lesen, um seinen binären Inhalt zu abrufen.</span><span class="sxs-lookup"><span data-stu-id="8287c-134">The user can directly read from this URL to fetch its binary content.</span></span>

#### <a name="message-activity-with-file-attachment-example"></a><span data-ttu-id="8287c-135">Beispiel für Nachrichtenaktivität mit Dateianlage</span><span class="sxs-lookup"><span data-stu-id="8287c-135">Message activity with file attachment example</span></span>

<span data-ttu-id="8287c-136">Der folgende Code zeigt ein Beispiel für nachrichtenaktivität mit Dateianlage:</span><span class="sxs-lookup"><span data-stu-id="8287c-136">The following code shows an example of message activity with file attachment:</span></span>

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

<span data-ttu-id="8287c-137">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8287c-137">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="8287c-138">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8287c-138">Property</span></span> | <span data-ttu-id="8287c-139">Zweck</span><span class="sxs-lookup"><span data-stu-id="8287c-139">Purpose</span></span> |
| --- | --- |
| `downloadUrl` | <span data-ttu-id="8287c-140">OneDrive-URL zum Abrufen des Inhalts der Datei.</span><span class="sxs-lookup"><span data-stu-id="8287c-140">OneDrive URL for fetching the content of the file.</span></span> <span data-ttu-id="8287c-141">Der Benutzer kann eine direkt `HTTP GET` von dieser URL aus aus.</span><span class="sxs-lookup"><span data-stu-id="8287c-141">The user can issue an `HTTP GET` directly from this URL.</span></span> |
| `uniqueId` | <span data-ttu-id="8287c-142">Eindeutige Datei-ID.</span><span class="sxs-lookup"><span data-stu-id="8287c-142">Unique file ID.</span></span> <span data-ttu-id="8287c-143">Dies ist die OneDrive-Laufwerkselement-ID, falls der Benutzer eine Datei an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="8287c-143">This is the OneDrive drive item ID, in case the user sends a file to the bot.</span></span> |
| `fileType` | <span data-ttu-id="8287c-144">Dateityp, z. B. PDF oder DOCX.</span><span class="sxs-lookup"><span data-stu-id="8287c-144">Type of file, such as .pdf or .docx.</span></span> |

<span data-ttu-id="8287c-145">Als bewährte Methode bestätigen Sie den Dateiupload, indem Sie eine Nachricht zurück an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="8287c-145">As a best practice, acknowledge the file upload by sending a message back to the user.</span></span>

### <a name="upload-files-to-personal-chat"></a><span data-ttu-id="8287c-146">Hochladen von Dateien in persönlichen Chat</span><span class="sxs-lookup"><span data-stu-id="8287c-146">Upload files to personal chat</span></span>

<span data-ttu-id="8287c-147">**So laden Sie eine Datei in einen Benutzer hoch**</span><span class="sxs-lookup"><span data-stu-id="8287c-147">**To upload a file to a user**</span></span>

1. <span data-ttu-id="8287c-148">Senden Sie eine Nachricht an den Benutzer, der die Berechtigung zum Schreiben der Datei anfordert.</span><span class="sxs-lookup"><span data-stu-id="8287c-148">Send a message to the user requesting permission to write the file.</span></span> <span data-ttu-id="8287c-149">Diese Nachricht muss eine Anlage `FileConsentCard` mit dem Namen der datei enthalten, die hochgeladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="8287c-149">This message must contain a `FileConsentCard` attachment with the name of the file to be uploaded.</span></span>
2. <span data-ttu-id="8287c-150">Wenn der Benutzer den Dateidownload akzeptiert, empfängt der Bot eine Aufrufaktivität mit einer Standort-URL.</span><span class="sxs-lookup"><span data-stu-id="8287c-150">If the user accepts the file download, the bot receives an invoke activity with a location URL.</span></span>
3. <span data-ttu-id="8287c-151">Um die Datei zu übertragen, führt der Bot `HTTP POST` eine direkt in die bereitgestellte Speicherort-URL aus.</span><span class="sxs-lookup"><span data-stu-id="8287c-151">To transfer the file, the bot performs an `HTTP POST` directly into the provided location URL.</span></span>
4. <span data-ttu-id="8287c-152">Entfernen Sie optional die ursprüngliche Zustimmungskarte, wenn Sie nicht möchten, dass der Benutzer weitere Uploads derselben Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="8287c-152">Optionally, remove the original consent card if you do not want the user to accept further uploads of the same file.</span></span>

#### <a name="message-requesting-permission-to-upload"></a><span data-ttu-id="8287c-153">Nachricht, die die Berechtigung zum Hochladen anfordert</span><span class="sxs-lookup"><span data-stu-id="8287c-153">Message requesting permission to upload</span></span>

<span data-ttu-id="8287c-154">Die folgende Desktopnachricht enthält ein einfaches Anlageobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="8287c-154">The following desktop message contains a simple attachment object requesting user permission to upload the file:</span></span>

![Zustimmungskarte, die die Benutzerberechtigung zum Hochladen der Datei anfordert](../../assets/images/bots/bot-file-consent-card.png)

<span data-ttu-id="8287c-156">Die folgende mobile Nachricht enthält ein Anlagenobjekt, das die Benutzerberechtigung zum Hochladen der Datei anfordert:</span><span class="sxs-lookup"><span data-stu-id="8287c-156">The following mobile message contains an attachment object requesting user permission to upload the file:</span></span>

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

<span data-ttu-id="8287c-157">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8287c-157">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="8287c-158">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8287c-158">Property</span></span> | <span data-ttu-id="8287c-159">Zweck</span><span class="sxs-lookup"><span data-stu-id="8287c-159">Purpose</span></span> |
| --- | --- |
| `description` | <span data-ttu-id="8287c-160">Beschreibt den Zweck der Datei oder fasst den Inhalt zusammen.</span><span class="sxs-lookup"><span data-stu-id="8287c-160">Describes the purpose of the file or summarizes its content.</span></span> |
| `sizeInBytes` | <span data-ttu-id="8287c-161">Stellt dem Benutzer eine Schätzung der Dateigröße und des Speicherplatzes in OneDrive zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8287c-161">Provides the user an estimate of the file size and the amount of space it takes in OneDrive.</span></span> |
| `acceptContext` | <span data-ttu-id="8287c-162">Zusätzlicher Kontext, der automatisch an den Bot übermittelt wird, wenn der Benutzer die Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="8287c-162">Additional context that is silently transmitted to the bot when the user accepts the file.</span></span> |
| `declineContext` | <span data-ttu-id="8287c-163">Zusätzlicher Kontext, der automatisch an den Bot übermittelt wird, wenn der Benutzer die Datei zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="8287c-163">Additional context that is silently transmitted to the bot when the user declines the file.</span></span> |

#### <a name="invoke-activity-when-the-user-accepts-the-file"></a><span data-ttu-id="8287c-164">Aufrufen von Aktivitäten, wenn der Benutzer die Datei akzeptiert</span><span class="sxs-lookup"><span data-stu-id="8287c-164">Invoke activity when the user accepts the file</span></span>

<span data-ttu-id="8287c-165">Eine Aufrufaktivität wird an den Bot gesendet, wenn und wann der Benutzer die Datei akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="8287c-165">An invoke activity is sent to the bot if and when the user accepts the file.</span></span> <span data-ttu-id="8287c-166">Sie enthält die OneDrive for Business-Platzhalter-URL, die der Bot dann ausgibt, `PUT` um den Dateiinhalt zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="8287c-166">It contains the OneDrive for Business placeholder URL that the bot can then issue a `PUT` to transfer the file contents.</span></span> <span data-ttu-id="8287c-167">Informationen zum Hochladen in die OneDrive-URL finden Sie unter [Upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span><span class="sxs-lookup"><span data-stu-id="8287c-167">For information on uploading to the OneDrive URL, see [upload bytes to the upload session](/onedrive/developer/rest-api/api/driveitem_createuploadsession#upload-bytes-to-the-upload-session).</span></span>

<span data-ttu-id="8287c-168">Der folgende Code zeigt ein Beispiel für eine prägnante Version der Aufrufaktivität, die der Bot empfängt:</span><span class="sxs-lookup"><span data-stu-id="8287c-168">The following code shows an example of a concise version of the invoke activity that the bot receives:</span></span>

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

<span data-ttu-id="8287c-169">Wenn der Benutzer die Datei zurückgibt, empfängt der Bot das folgende Ereignis mit demselben allgemeinen Aktivitätsnamen:</span><span class="sxs-lookup"><span data-stu-id="8287c-169">Similarly, if the user declines the file, the bot receives the following event with the same overall activity name:</span></span>

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

### <a name="notifying-the-user-about-an-uploaded-file"></a><span data-ttu-id="8287c-170">Benachrichtigen des Benutzers über eine hochgeladene Datei</span><span class="sxs-lookup"><span data-stu-id="8287c-170">Notifying the user about an uploaded file</span></span>

<span data-ttu-id="8287c-171">Nachdem Sie eine Datei auf das OneDrive des Benutzers hochgeladen haben, senden Sie eine Bestätigungsnachricht an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8287c-171">After uploading a file to the user's OneDrive, send a confirmation message to the user.</span></span> <span data-ttu-id="8287c-172">Die Nachricht muss die folgende Anlage enthalten, die der Benutzer auswählen kann, um eine Vorschau anzuzeigen oder sie in OneDrive zu öffnen `FileCard` oder lokal herunterzuladen:</span><span class="sxs-lookup"><span data-stu-id="8287c-172">The message must contain the following `FileCard` attachment that the user can select, either to preview or open it in OneDrive, or download locally:</span></span>

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

<span data-ttu-id="8287c-173">In der folgenden Tabelle werden die Inhaltseigenschaften der Anlage beschrieben:</span><span class="sxs-lookup"><span data-stu-id="8287c-173">The following table describes the content properties of the attachment:</span></span>

| <span data-ttu-id="8287c-174">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8287c-174">Property</span></span> | <span data-ttu-id="8287c-175">Zweck</span><span class="sxs-lookup"><span data-stu-id="8287c-175">Purpose</span></span> |
| --- | --- |
| `uniqueId` | <span data-ttu-id="8287c-176">OneDrive- oder SharePoint-Laufwerkelement-ID.</span><span class="sxs-lookup"><span data-stu-id="8287c-176">OneDrive or SharePoint drive item ID.</span></span> |
| `fileType` | <span data-ttu-id="8287c-177">Dateityp, z. B. PDF oder DOCX.</span><span class="sxs-lookup"><span data-stu-id="8287c-177">Type of file, such as .pdf or .docx.</span></span> |

### <a name="fetch-inline-images-from-message"></a><span data-ttu-id="8287c-178">Abrufen von Inlinebildern aus einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="8287c-178">Fetch inline images from message</span></span>

<span data-ttu-id="8287c-179">Abrufen von Inlinebildern, die Teil der Nachricht sind, mithilfe des Zugriffstokens des Bots.</span><span class="sxs-lookup"><span data-stu-id="8287c-179">Fetch inline images that are part of the message using the Bot's access token.</span></span>

![Inlinebild](../../assets/images/bots/inline-image.png)

<span data-ttu-id="8287c-181">Der folgende Code zeigt ein Beispiel für das Abrufen von Inlinebildern aus nachrichten:</span><span class="sxs-lookup"><span data-stu-id="8287c-181">The following code shows an example of fetching inline images from message:</span></span>

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

### <a name="basic-example-in-c"></a><span data-ttu-id="8287c-182">Grundlegendes Beispiel in C #</span><span class="sxs-lookup"><span data-stu-id="8287c-182">Basic example in C#</span></span>

<span data-ttu-id="8287c-183">Der folgende Code zeigt ein Beispiel für die Verarbeitung von Dateiuploads und das Senden von Datei-Zustimmungsanforderungen im Dialogfeld des Bots:</span><span class="sxs-lookup"><span data-stu-id="8287c-183">The following code shows an example of how to handle file uploads and send file consent requests in the bot's dialog:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="8287c-184">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8287c-184">Code sample</span></span>

<span data-ttu-id="8287c-185">Das folgende Codebeispiel veranschaulicht, wie Sie die Zustimmung der Datei erhalten und Dateien von einem Bot in Teams hochladen:</span><span class="sxs-lookup"><span data-stu-id="8287c-185">The following code sample demonstrates how to obtain file consent and upload files to Teams from a bot:</span></span>

|<span data-ttu-id="8287c-186">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="8287c-186">**Sample name**</span></span> | <span data-ttu-id="8287c-187">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="8287c-187">**Description**</span></span> | <span data-ttu-id="8287c-188">**.NET**</span><span class="sxs-lookup"><span data-stu-id="8287c-188">**.NET**</span></span> | <span data-ttu-id="8287c-189">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="8287c-189">**Javascript**</span></span> | <span data-ttu-id="8287c-190">**Python**</span><span class="sxs-lookup"><span data-stu-id="8287c-190">**Python**</span></span>|
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="8287c-191">File upload</span><span class="sxs-lookup"><span data-stu-id="8287c-191">File upload</span></span> | <span data-ttu-id="8287c-192">Zeigt, wie Sie die Zustimmung der Datei erhalten und Dateien von einem Bot in Teams hochladen.</span><span class="sxs-lookup"><span data-stu-id="8287c-192">Demonstrates how to obtain file consent and upload files to Teams from a bot.</span></span> <span data-ttu-id="8287c-193">Außerdem erfahren Sie, wie Sie eine an einen Bot gesendete Datei empfangen.</span><span class="sxs-lookup"><span data-stu-id="8287c-193">Also, how to receive a file sent to a bot.</span></span> | [<span data-ttu-id="8287c-194">View</span><span class="sxs-lookup"><span data-stu-id="8287c-194">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/csharp_dotnetcore/56.teams-file-upload) | [<span data-ttu-id="8287c-195">View</span><span class="sxs-lookup"><span data-stu-id="8287c-195">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/56.teams-file-upload) | [<span data-ttu-id="8287c-196">View</span><span class="sxs-lookup"><span data-stu-id="8287c-196">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/python/56.teams-file-upload) |

## <a name="next-step"></a><span data-ttu-id="8287c-197">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8287c-197">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8287c-198">Optimieren eines Bots mit Ratenbegrenzung in Teams</span><span class="sxs-lookup"><span data-stu-id="8287c-198">Optimize your bot with rate limiting in Teams</span></span>](~/bots/how-to/rate-limit.md)
