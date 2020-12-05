---
title: Kamera-und Bildfunktionen in Microsoft Teams
description: Verwenden von Microsoft Teams-JavaScript-Client-SDK zur Aktivierung systemeigener Kamera-und Bildfunktionen
keywords: Kamerabild Funktionen systemeigene Geräte Berechtigungen
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d0ca4dc9c289ec525aa99ea0e156a9f91f5b5d4a
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576885"
---
# <a name="camera-and-image-capabilities-in-teams"></a>Kamera-und Bildfunktionen in Microsoft Teams

>[!IMPORTANT]
>
> * Derzeit ist die Microsoft Teams-Unterstützung für Kamera-und Bildfunktionen nur für mobile Clients verfügbar.
>* Die `selectMedia` `getMedia` `viewImages` APIs können von mehreren Teams-Oberflächen wie Aufgaben Module, Registerkarten und persönliche apps aufgerufen werden. Weitere Informationen _finden Sie unter_ [Einstiegspunkte für Microsoft Teams-apps](../extensibility-points.md)

Sie können das  [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verwenden, um die Kamera-und Bildfunktionen in Ihren Microsoft Teams-Mobile App problemlos zu integrieren. Das SDK stellt die Tools bereit, die für Ihre APP erforderlich sind, um auf die [Geräte Berechtigungen](native-device-permissions.md?tabs=desktop#device-permissions) eines Benutzers zuzugreifen und eine umfassendere Benutzeroberfläche zu erstellen.

Die [selectMedia](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)-, [getmedia](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)-und [viewImages](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true) -APIs ermöglichen die Verwendung systemeigener Kamera/Bild-Funktionen wie folgt:

* Verwenden Sie systemeigene **Kamerasteuerung** , damit Benutzer **Bilder unterwegs erfassen und Anfügen** können.
* Verwenden Sie Native **Gallery-Unterstützung** , um Benutzern das **Auswählen von Geräte Abbildern** als Anlagen zu ermöglichen.
* Verwenden Sie das systemeigene **Image Viewer-Steuerelement** , um mehrere Bilder gleichzeitig in einer **Vorschau anzuzeigen** .
* Unterstützung der **großen Bildübertragung** (bis zu 50 MB) über die SDK-Brücke
* Unterstützung **Erweiterter Bildfunktionen** , mit denen Benutzer Bilder in der Vorschau anzeigen und bearbeiten können:
  * Überprüfen Sie Dokument, Whiteboard, Visitenkarten usw. über die Kamera.
  * Zuschneiden und Drehen der Bilder.
  * Fügen Sie dem Bild Text, Freihand oder Freihand-Anmerkungen hinzu.

## <a name="get-started"></a>Erste Schritte

Aktualisieren Sie Ihre Teams-APP- [manifest.jsauf](../../resources/schema/manifest-schema.md#devicepermissions) Datei, indem Sie die `devicePermissions`  -Eigenschaft hinzufügen und angeben `media` . Dadurch kann Ihre APP die erforderlichen Berechtigungen von Endbenutzern anfordern, bevor Sie die Kamera zum Erfassen des Bilds verwenden oder den Katalog öffnen, um ein Bild auszuwählen, das als Anlage gesendet werden soll.

``` json
"devicePermissions": [
    "media",
],
```

> [!NOTE]
> Die _Anforderungs Berechtigungs_ Eingabeaufforderung wird automatisch angezeigt, wenn eine relevante Teams-API initiiert wird. Weitere Informationen *finden Sie unter* [anfordern von Geräte Berechtigungen](native-device-permissions.md).

## <a name="using-camera-and-image-capability-apis"></a>Verwenden von Kamera-und Bild Funktions-APIs

Sie können die folgenden APIs verwenden, um die Kamera-und Bildgeräte Funktionen zu aktivieren:

| API      | Beschreibung   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest&branch=master#selectMedia_MediaInputs___error__SdkError__attachments__Media_______void_&preserve-view=true)| Mit dieser API können Benutzer **Medien von einem systemeigenen Gerät erfassen oder auswählen** und zur Webanwendung zurückkehren. Benutzer können vor der Übermittlung auswählen, ob Sie Bilder bearbeiten, Zuschneiden, drehen, kommentieren oder darüber zeichnen möchten. Als Reaktion auf **selectMedia** empfängt die Webanwendung Medien-IDs ausgewählter Bilder und erhält möglicherweise eine Miniaturansicht des ausgewählten Mediums. |
| [**getmedia**](/javascript/api/@microsoft/teams-js/_media?view=msteams-client-js-latest&branch=master#getMedia__error__SdkError__blob__Blob_____void_&preserve-view=true)| Diese API ruft die Medien unabhängig von ihrer Größe in Chunks ab. Diese Chunks werden zusammengestellt und als Datei/BLOB an die Webanwendung zurückgesendet. Mit dieser API wird ein Bild in kleinere Abschnitte unterteilt, um eine große Bildübertragung zu ermöglichen. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/media?view=msteams-client-js-latest#viewImages_ImageUri_____error___SdkError_____void_&preserve-view=true)| Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.|

**Webanwendungs Oberfläche für die selectMedia-API** 
 ![ Gerätekamera-und Bilderfahrung in Microsoft Teams](../../assets/images/tabs/image-capability-screenshot.jpg)

## <a name="error-handling"></a>Fehlerbehandlung

Sie sollten die API-Antwortfehler Codes verstehen und Sie entsprechend behandeln. Nachfolgend finden Sie eine Liste der Fehlercodes, die von der Plattform zurückgegeben werden können:

|Fehlercode |  Fehler Name     | Bedingung|
| --- | --- | --- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | API wird in der aktuellen Plattform nicht unterstützt.|
| **404** | FILE_NOT_FOUND | Die angegebene Datei wurde an der angegebenen Position nicht gefunden.|
| **500** | INTERNAL_ERROR | Interner Fehler, der beim Ausführen des erforderlichen Vorgangs aufgetreten ist.|
| **1000** | PERMISSION_DENIED |Vom Benutzer verweigerte Berechtigungen.|
| **2000** |NETWORK_ERROR | Netzwerkproblem.|
| **3000** | NO_HW_SUPPORT | Die zugrunde liegende Hardware unterstützt die Funktion nicht.|
| **4000**| INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
| **5000** | UNAUTHORIZED_USER_OPERATION | Der Benutzer ist nicht berechtigt, diesen Vorgang abzuschließen.|
| **6000** |INSUFFICIENT_RESOURCES | Der Vorgang konnte aufgrund unzureichender Ressourcen nicht abgeschlossen werden.|
|**7000** | THROTTLE | Die Plattform hat die Anforderung gedrosselt, da die API zu häufig aufgerufen wurde.|
|  **8000** | USER_ABORT |Der Benutzer hat den Vorgang abgebrochen.|
| **9000**| OLD_PLATFORM | Der Plattformcode ist veraltet und implementiert diese API nicht.|
| **10000**| SIZE_EXCEEDED |  Der Rückgabewert ist zu groß und hat die Begrenzungen der Plattformgröße überschritten.|

## <a name="sample-code-snippets"></a>Beispielcodeausschnitte

**Aufrufende `selectMedia` API**

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

**Aufrufende `getMedia` API**

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

**Aufrufen `viewImages`  der API nach ID**

```javascript
view images by id:
    assumption: attachmentArray = select Media API Outputlet uriList = [];
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

**Aufrufen der viewImages-API nach URL**

```javascript
View Images by URL:
    // Assumption 2 urls, url1 and url2let uriList = [];
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
}
```
