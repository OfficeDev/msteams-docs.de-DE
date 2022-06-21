---
title: Integrieren von Medienfunktionen
author: Rajeshwari-v
description: Erfahren Sie, wie Sie Teams JavaScript-Client-SDK verwenden, um Medienfunktionen mithilfe von Codebeispielen zu ermöglichen, und erfahren Sie außerdem, wie Sie die Vorteile der Integration von Medienfunktionen nutzen können.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 366c58ac283e687f8a297b8701b932f99550574e
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190237"
---
# <a name="integrate-media-capabilities"></a>Integrieren von Medienfunktionen

Sie können systemeigene Gerätefunktionen wie Kamera und Mikrofon in Ihre Teams-App integrieren. Für die Integration können Sie [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die erforderlichen Tools für den Zugriff auf [die Geräteberechtigungen](native-device-permissions.md) eines Benutzers für Ihre App bereitstellt. Verwenden Sie geeignete Medienfunktions-APIs, um die Gerätefunktionen wie Kamera und Mikrofon in die Teams Plattform in Ihrer Microsoft Teams-App zu integrieren und eine umfassendere Erfahrung zu schaffen. Die Medienfunktion ist für Teams Webclient, Desktop und Mobil verfügbar. Um Medienfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die Medienfunktions-APIs aufrufen.

Für eine effektive Integration benötigen Sie ein gutes Verständnis von [Codeausschnitten](#code-snippets) für den Aufruf der jeweiligen APIs, welche die Nutzung systemeigener Medienfunktionen ermöglichen. Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Microsoft Teams-App zu behandeln.

## <a name="advantages"></a>Vorteile

Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Microsoft Teams-Apps besteht in der Nutzung systemeigener Microsoft Teams-Steuerelemente, um eine umfassende und immersive Benutzererfahrung zu schaffen. Die folgenden Szenarien zeigen die Vorteile der Medienfunktionen:

* Ermöglichen Sie es dem Benutzer, die groben Modelle, die auf einem physischen Whiteboard gezeichnet werden, über das Mobiltelefon zu erfassen und die erfassten Bilder als Umfrageoptionen in Teams Gruppenchats zu verwenden.

* Zulassen, dass der Benutzer Eine Audionachricht aufzeichnet und an ein Vorfallticket anfügen kann.

* Ermöglichen Sie dem Benutzer, die physischen Dokumente vom Smartphone aus zu scannen, um einen Kfz-Versicherungsanspruch zu beantragen.

> [!NOTE]
>
> * Derzeit unterstützt Teams keine Geräteberechtigungen im Popup-Chatfenster, in Registerkarten und im Besprechungsbereich.</br>
> * Die Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter [Browsergeräteberechtigungen](browser-device-permissions.md).
> * Die Anforderungsberechtigungsaufforderung wird automatisch auf mobilgeräten angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen finden Sie unter [Geräteberechtigungen anfordern](native-device-permissions.md).

## <a name="update-manifest"></a>Aktualisieren des Manifests

Aktualisieren Sie Ihre Teams-App-Datei[manifest.json](../../resources/schema/manifest-schema.md#devicepermissions), indem Sie die `devicePermissions`-Eigenschaft hinzufügen und `media` angeben. Damit kann Ihre App die erforderlichen Berechtigungen von Benutzern anfordern, bevor sie mit der Verwendung der Kamera beginnt, um das Bild zu erfassen, den Katalog öffnet, um ein Bild auszuwählen, das als Anlage übermittelt werden soll, oder das Mikrofon zum Aufzeichnen der Unterhaltung verwendet. Das Update für das App-Manifest lautet wie folgt:

``` json
"devicePermissions": [
    "media",
],
```

## <a name="media-capability-apis"></a>APIs für Medienfunktionen

Mit den [selectMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true)-, [getMedia](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)- und [viewImages](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)-APIs können systemeigene Medienfunktionen wie folgt verwendet werden:

* Verwenden des systemeigenen **Mikrofons**, um Benutzern das **Aufzeichnen von Audio** (Aufzeichnen von 10 Gesprächsminuten) vom Gerät aus zu ermöglichen.
* Verwenden der systemeigenen **Kamerasteuerung**, um Benutzern das **Aufnehmen und Anfügen von Bildern** unterwegs zu ermöglichen.
* Verwenden der systemeigenen **Katalogunterstützung**, damit Benutzer **Gerätebilder** als Anlagen auswählen können.
* Verwenden des systemeigenen **Bildanzeigesteuerun**, um **mehrere Bilder gleichzeitig in der Vorschau anzuzeigen**.
* Unterstützung der **Übertragung großer Bilder** (von 1 MB bis 50 MB) über die SDK-Brücke.
* Unterstützen Sie **erweiterte Bildfunktionen** , indem Sie Benutzern die Vorschau und Bearbeitung von Bildern ermöglichen.
* Scannen Sie Dokumente, Whiteboards und Visitenkarten über die Kamera.
  
> [!IMPORTANT]
>
> * Die `selectMedia`-, `getMedia`- und `viewImages`-APIs können von mehreren Microsoft Teams-Oberflächen aus aufgerufen werden, z. B. Aufgabenmodulen, Registerkarten und persönlichen Apps. Weitere Informationen finden Sie unter [Einstiegspunkte für Microsoft Teams-Apps](../extensibility-points.md).</br>
> * `selectMedia` Die API unterstützt sowohl Kamera- als auch Mikrofonfunktionen durch unterschiedliche Eingabekonfigurationen.
> * Die `selectMedia` API für den Zugriff auf Mikrofonfunktionen unterstützt nur mobile Clients.

Die folgende Tabelle enthält eine Reihe von APIs zum Aktivieren der Medienfunktionen Ihres Geräts:

| API      | Beschreibung   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Kamera)**| Mit dieser API können Benutzer **Medien über die Gerätekamera erfassen oder auswählen** und an die Web-App zurückgeben. Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder darauf zeichnen. Als Reaktion auf `selectMedia` empfängt die Web-App die Medien-IDs der ausgewählten Bilder und eine Miniaturansicht der ausgewählten Medien. Diese API kann über die [ImageProps-Konfiguration](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageprops?view=msteams-client-js-latest&preserve-view=true) weiter konfiguriert werden. |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.media?view=msteams-client-js-latest&preserve-view=true) (**Mikrofon**)| Legen Sie "[mediaType](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediatype?view=msteams-client-js-latest&preserve-view=true)`4`" in `selectMedia` der API für den Zugriff auf die Mikrofonfunktion fest. Diese API ermöglicht es Benutzern auch, Audio über das Gerätemikrofon aufzuzeichnen und aufgezeichnete Clips an die Web-App zurückzugeben. Die Benutzer können die Aufzeichnung vor der Übermittlung anhalten, erneut aufzeichnen und wiedergeben. Als Reaktion auf  **selectMedia** empfängt die Web-App die Medien-IDs der ausgewählten Audioaufzeichnungen. <br/> Verwenden Sie `maxDuration`, wenn Sie eine Dauer in Minuten für die Aufzeichnung von Unterhaltungen konfigurieren müssen. Die aktuelle Dauer der Aufzeichnung beträgt 10 Minuten, danach wird sie beendet.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/microsoftteams.media.mediachunk?view=msteams-client-js-latest&preserve-view=true)| Diese API ruft die von der `selectMedia`-API erfassten Medien unabhängig von der Mediengröße in Blöcken ab. Diese Blöcke werden zusammengesetzt und als Datei oder Blob zurück an die Web-App gesendet. Das Aufteilen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/microsoftteams.media.imageuri?view=msteams-client-js-latest&preserve-view=true)| Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für die Bildfunktion:

:::image type="content" source="~/assets/images/tabs/media-capability-mobile2.png" alt-text="Die Abbildung zeigt die Bildfunktion für mobile Geräte." border="true":::

> [!NOTE]
>
> Auf Geräten mit Android Version unter 7 startet die `selectMedia` API die systemeigene Android Kameraerfahrung anstelle der systemeigenen Teams Kameraerfahrung.

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für die Mikrofonfunktion:

:::image type="content" source="~/assets/images/tabs/microphone-capability.png" alt-text="Die Abbildung zeigt die Mikrofonfunktion für mobile Geräte." border="true":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für die Bildfunktion:

:::image type="content" source="~/assets/images/tabs/media-capability-desktop1.png" alt-text="Die Abbildung zeigt die Medienfunktion für den Desktop." border="true":::

---

## <a name="error-handling"></a>Fehlerbehandlung

Stellen Sie sicher, dass diese Fehler in Ihrer Teams-App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und beschreibungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Beschreibung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **404** | FILE_NOT_FOUND | Die angegebene Datei wurde am angegebenen Speicherort nicht gefunden.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Die Berechtigung wird vom Benutzer verweigert.|
| **3000** | NO_HW_SUPPORT | Die Hardware unterstützt die Funktion nicht.|
| **4000**| INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
|  **8000** | USER_ABORT |Der Benutzer bricht den Vorgang ab.|
| **9000**| OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|
| **10000**| SIZE_EXCEEDED |  Der Rückgabewert ist zu groß und hat die Größengrenzen der Plattform überschritten.|

## <a name="code-snippets"></a>Codeausschnitte

* Anruf-API `selectMedia` zum Erfassen von Bildern mithilfe der Kamera:

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

* Aufrufen `getMedia` der API zum Abrufen großer Medien in Blöcken:

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

* Aufruf-API `viewImages` nach ID, die von `selectMedia` der API zurückgegeben wird:

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

* Aufruf-API `viewImages` nach URL:

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

* Anruf `selectMedia` und `getMedia` APIs zum Aufzeichnen von Audio über mikrofon:

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
* [Integration der Personenauswahl](people-picker-capability.md)
* [Anforderungen und Überlegungen für anwendungsgehostete Medienbots](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
