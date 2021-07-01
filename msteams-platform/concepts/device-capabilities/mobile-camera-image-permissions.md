---
title: Integrieren von Medienfunktionen
author: Rajeshwari-v
description: So verwenden Sie Teams JavaScript-Client-SDK, um Medienfunktionen zu aktivieren
keywords: Systemeigene Geräteberechtigungsmedien für Kamerabildmikrofonfunktionen
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 22d4a791e83cf36f18b75a3846865835b0ee024f
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211625"
---
# <a name="integrate-media-capabilities"></a>Integrieren von Medienfunktionen 

Sie können systemeigene Gerätefunktionen wie **Kamera** und **Mikrofon** in Ihre Teams-App integrieren. Zur Integration können Sie [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, das die Tools bereitstellt, die Ihre App für den Zugriff auf [die Geräteberechtigungen](native-device-permissions.md)eines Benutzers benötigt. Verwenden Sie geeignete Medienfunktions-APIs, um die Gerätefunktionen wie **Kamera** und **Mikrofon** in die Teams-Plattform in Ihre Microsoft Teams mobile App zu integrieren und eine umfassendere Umgebung zu erstellen. 

## <a name="advantage-of-integrating-media-capabilities"></a>Vorteile der Integration von Medienfunktionen

Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Teams-Apps besteht darin, dass systemeigene Teams-Steuerelemente genutzt werden, um Ihren Benutzern eine umfassende und immersive Erfahrung zu bieten.
Um Medienfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die Medienfunktions-APIs aufrufen. 

Für eine effektive Integration müssen Sie über ein gutes Verständnis von [Codeausschnitten](#code-snippets) für den Aufruf der entsprechenden APIs verfügen, mit denen Sie systemeigene Medienfunktionen verwenden können.

Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE] 
> * Derzeit ist Microsoft Teams Unterstützung für Medienfunktionen nur für mobile Clients verfügbar.   
> * Derzeit unterstützt Teams keine Geräteberechtigungen für Apps mit mehreren Fenstern, Registerkarten und das Besprechungs-Sidepanel.    

## <a name="update-manifest"></a>Updatemanifest

Aktualisieren Sie die Teams [App-manifest.jsauf](../../resources/schema/manifest-schema.md#devicepermissions) der Datei, indem Sie die Eigenschaft hinzufügen `devicePermissions` und `media` angeben. Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Aufnahme des Bilds mit der **Kamera** beginnen, den Katalog öffnen, um ein Bild auszuwählen, das als Anlage übermittelt werden soll, oder das **Mikrofon** verwenden, um die Unterhaltung aufzuzeichnen. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die Eingabeaufforderung **"Berechtigungen anfordern"** wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter Anfordern von [Geräteberechtigungen.](native-device-permissions.md)

## <a name="media-capability-apis"></a>APIs für Medienfunktionen

Mit den [APIs selectMedia,](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)und [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true) können Sie systemeigene Medienfunktionen wie folgt verwenden:

* Verwenden Sie das systemeigene **Mikrofon,** um Benutzern das Aufzeichnen von **Audiodaten** (Aufzeichnung von 10 Minuten Unterhaltung) vom Gerät aus zu ermöglichen.
* Verwenden Sie das systemeigene **Kamerasteuerelement,** damit Benutzer **unterwegs Bilder erfassen und anfügen** können.
* Verwenden Sie die **native Katalogunterstützung,** damit Benutzer **Gerätebilder** als Anlagen auswählen können.
* Verwenden Sie das systemeigene **Bildanzeige-Steuerelement,** um **mehrere Bilder** gleichzeitig in der Vorschau anzuzeigen.
* Unterstützt **große Bildübertragung** (von 1 MB bis 50 MB) über die SDK-Brücke.
* Unterstützung **erweiterter Bildfunktionen,** mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:
  * Scannen Sie Dokumente, Whiteboards und Visitenkarten über die Kamera.
  
> [!IMPORTANT]
> * Die `selectMedia` , `getMedia` und `viewImages` APIs können von mehreren Teams Oberflächen aufgerufen werden, z. B. Aufgabenmodule, Registerkarten und persönliche Apps. Weitere Informationen finden Sie unter [Einstiegspunkte für Teams Apps.](../extensibility-points.md)
> * `selectMedia` Die API wurde erweitert, um Mikrofon- und Audioeigenschaften zu unterstützen.

Sie müssen die folgenden APIs verwenden, um die Medienfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Kamera)**| Mit dieser API können Benutzer **Medien aus der Gerätekamera erfassen oder auswählen** und an die Web-App zurückgeben. Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder zeichnen. Als Reaktion darauf `selectMedia` empfängt die Web-App die Medien-IDs ausgewählter Bilder und eine Miniaturansicht der ausgewählten Medien. Diese API kann über die [ImageProps-Konfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) weiter konfiguriert werden. |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Mikrofon**)| Legen Sie ["mediaType"](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) `4` auf "in `selectMedia` API" fest, um auf die Mikrofonfunktion zuzugreifen. Diese API ermöglicht es Benutzern auch, Audiodaten vom Gerätemikrofon aufzuzeichnen und aufgezeichnete Clips an die Web-App zurückzugeben. Die Benutzer können vor der Übermittlung anhalten, erneut aufzeichnen und die Aufzeichnungsvorschau wiedergeben. Als Reaktion auf **selectMedia** empfängt die Web-App Medien-IDs der ausgewählten Audioaufzeichnung. <br/> Verwenden Sie `maxDuration` dies, wenn Sie eine Dauer in Minuten für die Aufzeichnung der Unterhaltung konfigurieren müssen. Die aktuelle Aufzeichnungsdauer beträgt 10 Minuten, danach wird die Aufzeichnung beendet.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| Diese API ruft die von der API erfassten Medien `selectMedia` in Blöcken ab, unabhängig von der Mediengröße. Diese Blöcke werden zusammengestellt und als Datei oder Blob an die Web-App zurückgesendet. Das Unterteilen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.|

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für bildfunktion:

![Kamera- und Bilderfahrung des Geräts in Teams](../../assets/images/tabs/image-capability.png)

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für Mikrofonfunktion:

![Web-App-Erfahrung für Mikrofonfunktion](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Teams App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden: 

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **404** | FILE_NOT_FOUND | Die angegebene Datei wurde am angegebenen Speicherort nicht gefunden.|
| **500** | INTERNAL_ERROR | Beim Ausführen des erforderlichen Vorgangs ist ein interner Fehler aufgetreten.|
| **1000** | PERMISSION_DENIED |Der Benutzer verweigert die Berechtigung.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000**| INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
|  **8000** | USER_ABORT |Der Benutzer abgebrochen den Vorgang.|
| **9000**| OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|
| **10000**| SIZE_EXCEEDED |  Der Rückgabewert ist zu groß und hat die Grenzen der Plattformgröße überschritten.|

## <a name="code-snippets"></a>Codeausschnitte

**Anrufe `selectMedia` API** zum Aufnehmen von Bildern mithilfe der Kamera:

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

**Anrufe `getMedia` API** zum Abrufen großer Medien in Blöcken:

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

**Anrufe `viewImages` API nach ID, die von `selectMedia` der API zurückgegeben wird:**

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

**Anrufe `viewImages` API nach URL:**

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

**Anrufe `selectMedia` und `getMedia` APIs zum Aufzeichnen von Audio über das Mikrofon:**

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

* [Integrieren von QR- oder Strichcodescannern in Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Teams](location-capability.md)
* [Integrieren der Personenauswahlfunktion in Teams](people-picker-capability.md)

