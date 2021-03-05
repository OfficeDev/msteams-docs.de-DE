---
title: Integrieren von Medienfunktionen
description: Verwenden des Teams JavaScript-Client-SDK zum Aktivieren von Medienfunktionen
keywords: Kamerabildmikrofonfunktionen Systemeigene Geräteberechtigungen Medien
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 375d68c7c712b7a8d2f7114b47aae61c889b4197
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449580"
---
# <a name="integrate-media-capabilities"></a>Integrieren von Medienfunktionen 

In diesem Dokument erfahren Sie, wie Sie Medienfunktionen integrieren. Diese Integration kombiniert die systemeigenen Gerätefunktionen, z. B. Kamera **und** **Mikrofon,** mit der Teams-Plattform.  

Sie können [das Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die tools zur Verfügung stellt, die für Ihre App für den Zugriff auf die [Geräteberechtigungen](native-device-permissions.md)eines Benutzers erforderlich sind. Verwenden Sie geeignete APIs für Medienfunktionen, um  die  systemeigenen Gerätefunktionen wie Kamera und Mikrofon in die Microsoft Teams-Plattform in Ihrer mobilen Microsoft Teams-App zu integrieren und eine reichhaltigere Erfahrung zu erstellen. 

## <a name="advantage-of-integrating-media-capabilities"></a>Vorteile der Integration von Medienfunktionen

Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Teams-Apps besteht in der Nutzung systemeigener Teams-Steuerelemente, um Ihren Benutzern eine umfassende und immersive Benutzererfahrung zu bieten.
Zum Integrieren von Medienfunktionen müssen Sie die App-Manifestdatei aktualisieren und die APIs für Medienfunktionen aufrufen. 

Für eine effektive Integration benötigen Sie [](#code-snippets) ein gutes Verständnis von Codeausschnitten zum Aufrufen der entsprechenden APIs, mit denen Sie systemeigene Medienfunktionen verwenden können.

Es ist wichtig, sich mit den API-Antwortfehlern vertraut zu [machen,](#error-handling) um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE] 
> Derzeit ist Die Unterstützung für Medienfunktionen von Microsoft Teams nur für mobile Clients verfügbar.

## <a name="update-manifest"></a>Updatemanifest

Aktualisieren Sie Ihre [ Teamsmanifest.js-App-Datei,](../../resources/schema/manifest-schema.md#devicepermissions) indem Sie die `devicePermissions` -Eigenschaft hinzufügen und `media` angeben. Sie ermöglicht es Ihrer App, die erforderlichen Berechtigungen  von Benutzern zu fordern, bevor sie mit der Kamera beginnen,  das Bild zu erfassen, den Katalog öffnen, um ein Bild auszuwählen, das als Anlage gesendet werden soll, oder das Mikrofon zum Aufzeichnen der Unterhaltung verwenden.

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die **Anforderungsberechtigungsaufforderung** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter [Anfordern von Geräteberechtigungen](native-device-permissions.md).

## <a name="media-capability-apis"></a>APIs für Medienfunktionen

Mit [den selectMedia-,](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) [getMedia-](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)und [viewImages-APIs](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) können Sie systemeigene Medienfunktionen wie folgt verwenden:

* Verwenden Sie **das** systemeigene Mikrofon, um Benutzern das Aufzeichnen von **Audiodaten** (10 Minuten Unterhaltung) vom Gerät zu ermöglichen.
* Verwenden Sie das **systemeigene Kamerasteuerelement,** um Benutzern das **Erfassen und Anfügen von** Bildern unterwegs zu ermöglichen.
* Verwenden Sie systemeigene **Katalogunterstützung,** um Benutzern die Auswahl von **Gerätebildern als** Anlagen zu ermöglichen.
* Verwenden Sie **systemeigenes Bildanzeigesteuerelement,** um **eine Vorschau mehrerer Bilder** gleichzeitig anzuzeigen.
* Unterstützt **eine große Bildübertragung** (von 1 MB auf 50 MB) über die SDK-Brücke.
* Unterstützung **erweiterter Bildfunktionen,** mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:
  * Scannen Sie Dokument-, Whiteboard- und Visitenkarten über die Kamera.
  
> [!IMPORTANT]
> * Die APIs , und können von mehreren Teams-Oberflächen aufgerufen werden, z. B. Aufgabenmodulen, `selectMedia` `getMedia` `viewImages` Registerkarten und persönlichen Apps. Weitere Informationen finden Sie unter [Einstiegspunkte für Teams-Apps](../extensibility-points.md).
> * `selectMedia` Die API wurde erweitert, um Mikrofon- und Audioeigenschaften zu unterstützen.

Sie müssen die folgenden APIs verwenden, um die Medienfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Camera)**| Mit dieser API können Benutzer **Medien** von der Gerätekamera erfassen oder auswählen und an die Web-App zurückgeben. Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder zeichnen. Als Antwort auf `selectMedia` empfängt die Web-App die Medien-IDs ausgewählter Bilder und eine Miniaturansicht der ausgewählten Medien. Diese API kann über die [ImageProps-Konfiguration weiter konfiguriert](/javascript/api/@microsoft/teams-js/imageprops?view=msteams-client-js-latest&preserve-view=true) werden. |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true) (**Microphone**)| Legen Sie [mediaType](/javascript/api/@microsoft/teams-js/mediatype?view=msteams-client-js-latest&preserve-view=true) `4` in der API auf für den Zugriff auf `selectMedia` mikrofonfunktion. Mit dieser API können Benutzer auch Audiodaten aus dem Gerätemikrofon aufzeichnen und aufgezeichnete Clips an die Web-App zurückgeben. Die Benutzer können die Aufzeichnungsvorschau vor der Übermittlung anhalten, erneut aufzeichnen und wiederverspielen. Als Antwort auf **selectMedia** empfängt die Web-App Medien-IDs der ausgewählten Audioaufzeichnung. <br/> Verwenden Sie , wenn Sie eine Dauer in Minuten für die `maxDuration` Aufzeichnung der Unterhaltung konfigurieren müssen. Die aktuelle Aufzeichnungsdauer beträgt 10 Minuten, nach der die Aufzeichnung beendet wird.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| Diese API ruft die von der API erfassten Medien unabhängig von der Mediengröße `selectMedia` in Blöcken ab. Diese Blöcke werden zusammengesetzt und als Datei oder Blob an die Web-App gesendet. Das Aufbrechen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| Mit dieser API kann der Benutzer Bilder im Vollbildmodus als bildlauffähige Liste anzeigen.|


**Web-App-Erfahrung für selectMedia-API für Bildfunktionen** 
 ![ Gerätekamera und Bilderfahrung in Teams](../../assets/images/tabs/image-capability.png)

**Web-App-Erfahrung für selectMedia-API für Mikrofonfunktion** 
 ![ Web-App-Erfahrung für Mikrofonfunktionen](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams-App angemessen umgangen werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden: 


|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | DIE API wird auf der aktuellen Plattform nicht unterstützt.|
| **404** | FILE_NOT_FOUND | Die angegebene Datei wird am angegebenen Speicherort nicht gefunden.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Die Berechtigung wird vom Benutzer verweigert.|
| **2000** |NETWORK_ERROR | Netzwerkproblem.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000**| INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
| **5000** | UNAUTHORIZED_USER_OPERATION | Der Benutzer ist nicht zum Abschließen dieses Vorgangs autorisiert.|
| **6000** |INSUFFICIENT_RESOURCES | Der Vorgang konnte aufgrund unzureichender Ressourcen nicht abgeschlossen werden.|
|**7000** | THROTTLE | Die Plattform hat die Anforderung gedrosselt, da die API häufig aufgerufen wurde.|
|  **8000** | USER_ABORT |Der Benutzer bricht den Vorgang ab.|
| **9000**| OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|
| **10000**| SIZE_EXCEEDED |  Der Rückgabewert ist zu groß und hat die Grenzen der Plattformgröße überschritten.|

## <a name="code-snippets"></a>Codeausschnitte

**Aufrufen `selectMedia` API** zum Aufzeichnen von Bildern mit der Kamera:

```javascript
let imageProp: microsoftTeams.media.ImageProps = {
    sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
    startMode: microsoftTeams.media.CameraStartMode.Photo,
    ink: false,
    cameraSwitcher: false,
    textSticker: false,
    enableFilter: true,
};
let mediaInput: microsoftTeams.media.MediaInputs = {
    mediaType: microsoftTeams.media.MediaType.Image,
    maxMediaCount: 10,
    imageProps: imageProp
};
microsoftTeams.media.selectMedia(mediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
    if (attachments) {
        let y = attachments[0];
        img.src = ("data:" + y.mimeType + ";base64," + y.preview);
    }
});
```

**Aufrufen `getMedia` API** zum Abrufen großer Medien in Blöcken:

```javascript
let media: microsoftTeams.media.Media = attachments[0]
media.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
    if (blob) {
        if (blob.type.includes("image")) {
            img.src = (URL.createObjectURL(blob));
        }
    }
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
});
```

**Aufrufen `viewImages` API nach ID, die von der `selectMedia` API zurückgegeben wird:**

```javascript
// View images by id:
// Assumption: attachmentArray = select Media API Output
let uriList = [];
if (attachmentArray && attachmentArray.length > 0) {
    for (let i = 0; i < attachmentArray.length; i++) {
        let file = attachmentArray[i];
        if (file.mimeType.includes("image")) {
            let imageUri = {
                value: file.content,
                type: 1,
            }
            uriList.push(imageUri);
        } else {
            alert("File type is not image");
        }
    }
}
if (uriList.length > 0) {
    microsoftTeams.media.viewImages(uriList, (error: microsoftTeams.SdkError) => {
        if (error) {
            if (error.message) {
                output(" ErrorCode: " + error.errorCode + error.message);
            } else {
                output(" ErrorCode: " + error.errorCode);
            }
        }
    });
} else {
    output("Url list is empty");
}
```

**Aufrufen `viewImages` API nach URL**:

```javascript
// View Images by URL:
// Assumption 2 urls, url1 and url2
let uriList = [];
if (URL1 != null && URL1.length > 0) {
    let imageUri = {
        value: URL1,
        type: 2,
    }
    uriList.push(imageUri);
}
if (URL2 != null && URL2.length > 0) {
    let imageUri = {
        value: URL2,
        type: 2,
    }
    uriList.push(imageUri);
}
if (uriList.length > 0) {
    microsoftTeams.media.viewImages(uriList, (error: microsoftTeams.SdkError) => {
        if (error) {
            if (error.message) {
                output(" ErrorCode: " + error.errorCode + error.message);
            } else {
                output(" ErrorCode: " + error.errorCode);
            }
        }
    });
} else {
    output("Url list is empty");
}
```

**Anrufe `selectMedia` und `getMedia` APIs zum Aufzeichnen von Audio über Mikrofon**:

```javascript
let mediaInput: microsoftTeams.media.MediaInputs = {
    mediaType: microsoftTeams.media.MediaType.Audio,
    maxMediaCount: 1,
};
microsoftTeams.media.selectMedia(mediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
    // If you want to directly use the audio file (for smaller file sizes (~4MB))    if (attachments) {
    let audioResult = attachments[0];
    var videoElement = document.createElement("video");
    videoElement.setAttribute("src", ("data:" + y.mimeType + ";base64," + y.preview));
    //To use the audio file via get Media API for bigger audio file sizes greater than 4MB        audioResult.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
    if (blob) {
        if (blob.type.includes("video")) {
            videoElement.setAttribute("src", URL.createObjectURL(blob));
        }
    }
    if (error) {
        if (error.message) {
            alert(" ErrorCode: " + error.errorCode + error.message);
        } else {
            alert(" ErrorCode: " + error.errorCode);
        }
    }
});
```

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Integrieren von QR- oder Barcodescannerfunktionen in Teams](qr-barcode-scanner-capability.md)

> [!div class="nextstepaction"]
> [Integrieren von Standortfunktionen in Teams](location-capability.md)