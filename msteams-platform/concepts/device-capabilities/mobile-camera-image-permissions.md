---
title: Integrieren von Medienfunktionen
author: Rajeshwari-v
description: Erfahren Sie anhand von Codebeispielen, wie Sie das Microsoft Teams JavaScript-Client-SDK verwenden, um Medienfunktionen zu aktivieren.
keywords: Medien-API Kamerabild Mikrofonfunktionen systemeigene Geräteberechtigungen
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: a65f39d3796bc0dacaa80f6badba7a011716edbf
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756758"
---
# <a name="integrate-media-capabilities"></a>Integrieren von Medienfunktionen

Sie können systemeigene Gerätefunktionen wie **Kamera** und **Mikrofon** in Ihre Microsoft Teams-App integrieren. Für die Integration können Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die Tools bereitstellt, die Ihre App für den Zugriff auf die [Geräteberechtigungen](native-device-permissions.md) eines Benutzers benötigt. Verwenden Sie geeignete Medienfunktions-APIs, um Gerätefunktionen wie **Kamera** und **Mikrofon** über die Microsoft Teams-Plattform in Ihre mobile Microsoft Teams-App zu integrieren und dadurch eine vielfältigere Benutzererfahrung zu schaffen.

## <a name="advantage-of-integrating-media-capabilities"></a>Vorteile der Integration von Medienfunktionen

Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Microsoft Teams-Apps besteht in der Nutzung systemeigener Microsoft Teams-Steuerelemente, um eine umfassende und immersive Benutzererfahrung zu schaffen.
Um Medienfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die Medienfunktions-APIs aufrufen.

Für eine effektive Integration benötigen Sie ein gutes Verständnis von [Codeausschnitten](#code-snippets) für den Aufruf der jeweiligen APIs, welche die Nutzung systemeigener Medienfunktionen ermöglichen.

Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

> [!NOTE]
>
> * Derzeit sind Microsoft Teams-Unterstützung für Medienfunktionen nur für mobile Clients verfügbar.
> * Derzeit werden in Microsoft Teams keine Geräteberechtigungen für Apps mit mehreren Fenstern, Registerkarten und den Besprechungsseitenbereich unterstützt.
> * Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter [Browsergeräteberechtigungen](browser-device-permissions.md).

## <a name="update-manifest"></a>Aktualisieren des Manifests

Aktualisieren Sie Ihre Microsoft Teams-App-Datei[manifest.json](../../resources/schema/manifest-schema.md#devicepermissions), indem Sie die `devicePermissions`-Eigenschaft hinzufügen und `media` angeben. Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der **Kamera** beginnt, um das Bild zu erfassen, den Katalog öffnet, um ein Bild auszuwählen, das als Anlage übermittelt werden soll, oder das **Mikrofon** zum Aufzeichnen der Unterhaltung verwendet. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die Eingabeaufforderung **Berechtigungen anfordern** wird automatisch angezeigt, wenn eine relevante Microsoft Teams-API initiiert wird. Weitere Informationen finden Sie unter [Geräteberechtigungen anfordern](native-device-permissions.md).

## <a name="media-capability-apis"></a>APIs für Medienfunktionen

Mit den [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true)-, [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)- und [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)-APIs können systemeigene Medienfunktionen wie folgt verwendet werden:

* Verwenden des systemeigenen **Mikrofons**, um Benutzern das **Aufzeichnen von Audio** (Aufzeichnen von 10 Gesprächsminuten) vom Gerät aus zu ermöglichen.
* Verwenden der systemeigenen **Kamerasteuerung**, um Benutzern das **Aufnehmen und Anfügen von Bildern** unterwegs zu ermöglichen.
* Verwenden der systemeigenen **Katalogunterstützung**, damit Benutzer **Gerätebilder** als Anlagen auswählen können.
* Verwenden des systemeigenen **Bildanzeigesteuerun**, um **mehrere Bilder gleichzeitig in der Vorschau anzuzeigen**.
* Unterstützung der **Übertragung großer Bilder** (von 1 MB bis 50 MB) über die SDK-Brücke.
* Die Unterstützung **erweiterter Bildfunktionen** ermöglicht es Benutzern, Bilder in der Vorschau anzuzeigen und zu bearbeiten:
  * Scannen Sie Dokumente, Whiteboards und Visitenkarten über die Kamera.
  
> [!IMPORTANT]
>
> * Die `selectMedia`-, `getMedia`- und `viewImages`-APIs können von mehreren Microsoft Teams-Oberflächen aus aufgerufen werden, z. B. Aufgabenmodulen, Registerkarten und persönlichen Apps. Weitere Informationen finden Sie unter [Einstiegspunkte für Teams Apps](../extensibility-points.md).
> * Die `selectMedia`-API wurde erweitert, um Mikrofon- und Audioeigenschaften zu unterstützen.

Sie müssen die folgenden APIs verwenden, um die Medienfunktionen Ihres Geräts zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Kamera)**| Mit dieser API können Benutzer **Medien über die Gerätekamera erfassen oder auswählen** und an die Web-App zurückgeben. Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder darauf zeichnen. Als Reaktion auf `selectMedia` empfängt die Web-App die Medien-IDs der ausgewählten Bilder und eine Miniaturansicht der ausgewählten Medien. Diese API kann über die [ImageProps-Konfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) weiter konfiguriert werden. |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Mikrofon**)| Legen Sie [mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true) auf `4` in der `selectMedia`-API fest, um auf die Mikrofonfunktion zuzugreifen. Diese API ermöglicht es Benutzern auch, Audio über das Gerätemikrofon aufzuzeichnen und aufgezeichnete Clips an die Web-App zurückzugeben. Die Benutzer können die Aufzeichnung vor der Übermittlung anhalten, erneut aufzeichnen und wiedergeben. Als Reaktion auf  **selectMedia** empfängt die Web-App die Medien-IDs der ausgewählten Audioaufzeichnungen. <br/> Verwenden Sie `maxDuration`, wenn Sie eine Dauer in Minuten für die Aufzeichnung von Unterhaltungen konfigurieren müssen. Die aktuelle Dauer der Aufzeichnung beträgt 10 Minuten, danach wird sie beendet.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| Diese API ruft die von der `selectMedia`-API erfassten Medien unabhängig von der Mediengröße in Blöcken ab. Diese Blöcke werden zusammengesetzt und als Datei oder Blob zurück an die Web-App gesendet. Das Aufteilen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.|

Die folgende Abbildung zeigt die Web-App-Oberfläche der `selectMedia`-API für Bildfunktionen:

![Gerätekamera- und Bilderoberfläche in Microsoft Teams](../../assets/images/tabs/image-capability.png)

Die folgende Abbildung zeigt die Web-App-Oberfläche der `selectMedia`-API für Mikrofonfunktionen:

![Web-App-Oberfläche für Mikrofonfunktionen](../../assets/images/tabs/microphone-capability.png)

## <a name="error-handling"></a>Fehlerbehandlung

Sie müssen sicherstellen, dass diese Fehler in Ihrer Microsoft Teams-App angemessen behandelt werden. In der folgenden Tabelle sind die Fehlercodes und die Bedingungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Bedingung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | DIE API wird auf der aktuellen Plattform nicht unterstützt.|
| **404** | FILE_NOT_FOUND | Die angegebene Datei wird am angegebenen Speicherort nicht gefunden.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Die Berechtigung wird vom Benutzer verweigert.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000**| INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
|  **8000** | USER_ABORT |Der Benutzer bricht den Vorgang ab.|
| **9000**| OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|
| **10000**| SIZE_EXCEEDED |  Der Rückgabewert ist zu groß und hat die Größengrenzen der Plattform überschritten.|

## <a name="code-snippets"></a>Codeausschnitte

**Aufrufen der `selectMedia`-API** zum Aufnehmen von Bildern mithilfe der Kamera:

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

**Aufrufen der `getMedia`-API** zum Abrufen großer Medien in Blöcken:

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

**Aufrufen der `viewImages`-API nach ID, die von der `selectMedia`-API zurückgegeben wird**:

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

**Aufrufen der `viewImages`-API nach URL**:

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

**Aufrufen der `selectMedia`- und `getMedia`-APIs zum Aufzeichnen von Audio über das Mikrofon**:

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

* [Integrieren von QR-Code- oder Strichcodescanner-Funktionen in Microsoft Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Microsoft Teams](location-capability.md)
* [Integrieren der Personenauswahl in Microsoft Teams](people-picker-capability.md)
* [Anforderungen und Überlegungen für anwendungsgehostete Medienbots](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
