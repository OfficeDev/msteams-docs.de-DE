---
title: Integrieren von Medienfunktionen
author: Rajeshwari-v
description: Erfahren Sie, wie Sie das JavaScript-Client-SDK von Teams verwenden, um Medienfunktionen anhand von Codebeispielen zu aktivieren, und erfahren Sie auch, wie Sie die Vorteile der Integration von Medienfunktionen nutzen können.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 25d8fb9c52e0dee02d8057f1fe4714f7f3f1f613
ms.sourcegitcommit: 3baca27a93e5a68eaaa52810700076f08f4c88a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2022
ms.locfileid: "67605789"
---
# <a name="integrate-media-capabilities"></a>Integrieren von Medienfunktionen

Sie können systemeigene Gerätefunktionen wie Kamera und Mikrofon in Ihre Teams-App integrieren. Für die Integration können Sie [das JavaScript-Client-SDK von Microsoft Teams](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verwenden, das die erforderlichen Tools für Ihre App für den Zugriff auf [die Geräteberechtigungen](native-device-permissions.md) eines Benutzers bereitstellt. Verwenden Sie geeignete Medienfunktions-APIs, um die Gerätefunktionen wie Kamera und Mikrofon in die Teams-Plattform in Ihrer Microsoft Teams-App zu integrieren und eine umfassendere Erfahrung zu schaffen. Die Medienfunktion ist für Teams-Webclient, -Desktop und mobile Geräte verfügbar. Um Medienfunktionen zu integrieren, müssen Sie die App-Manifestdatei aktualisieren und die Medienfunktions-APIs aufrufen.

Für eine effektive Integration benötigen Sie ein gutes Verständnis von [Codeausschnitten](#code-snippets) zum Aufrufen der jeweiligen APIs, mit denen Sie native Medienfunktionen verwenden können. Es ist wichtig, sich mit den [API-Antwortfehlern](#error-handling) vertraut zu machen, um die Fehler in Ihrer Teams-App zu behandeln.

## <a name="advantages"></a>Vorteile

Der Hauptvorteil der Integration von Gerätefunktionen in Ihre Teams-Apps ist die Verwendung nativer Teams-Steuerelemente, um Ihren Benutzern eine umfassende und immersive Erfahrung zu bieten. Die folgenden Szenarien zeigen die Vorteile der Medienfunktionen:

* Ermöglichen Sie es dem Benutzer, die groben Modelle, die auf einem physischen Whiteboard gezeichnet werden, über das Mobiltelefon zu erfassen und die erfassten Bilder als Umfrageoptionen im Teams-Gruppenchat zu verwenden.

* Zulassen, dass der Benutzer Eine Audionachricht aufzeichnet und an ein Vorfallticket anfügen kann.

* Ermöglichen Sie dem Benutzer, die physischen Dokumente vom Smartphone aus zu scannen, um einen Kfz-Versicherungsanspruch zu beantragen.

* Zulassen, dass der Benutzer ein Video auf einer Arbeitssite aufzeichnet und zur Teilnahme hochlädt.

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

Mit den [selectMedia](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-selectmedia)-, [getMedia](/javascript/api/@microsoft/teams-js/media.media#@microsoft-teams-js-media-media-getmedia)- und [viewImages](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-viewimages)-APIs können systemeigene Medienfunktionen wie folgt verwendet werden:

* Verwenden des systemeigenen **Mikrofons**, um Benutzern das **Aufzeichnen von Audio** (Aufzeichnen von 10 Gesprächsminuten) vom Gerät aus zu ermöglichen.
* Verwenden Sie die systemeigene **Kamerasteuerung** , um Benutzern das **Aufnehmen und Anfügen von Bildern** und **das Aufnehmen von Videos** (Aufzeichnen von bis zu 5 Minuten Video) unterwegs zu ermöglichen.
* Verwenden der systemeigenen **Katalogunterstützung**, damit Benutzer **Gerätebilder** als Anlagen auswählen können.
* Verwenden des systemeigenen **Bildanzeigesteuerun**, um **mehrere Bilder gleichzeitig in der Vorschau anzuzeigen**.
* Unterstützung der **Übertragung großer Bilder** (von 1 MB bis 50 MB) über die SDK-Brücke.
* Unterstützen Sie **erweiterte Bildfunktionen** , indem Sie Benutzern die Vorschau und Bearbeitung von Bildern ermöglichen.
* Scannen Sie Dokumente, Whiteboards und Visitenkarten über die Kamera.
  
> [!IMPORTANT]
>
> * Die `selectMedia`-, `getMedia`- und `viewImages`-APIs können von mehreren Microsoft Teams-Oberflächen aus aufgerufen werden, z. B. Aufgabenmodulen, Registerkarten und persönlichen Apps. Weitere Informationen finden Sie [unter Einstiegspunkte für Teams-Apps](../extensibility-points.md).</br>
> * `selectMedia` Die API unterstützt sowohl Kamera- als auch Mikrofonfunktionen durch unterschiedliche Eingabekonfigurationen.
> * Die `selectMedia` API für den Zugriff auf Mikrofonfunktionen unterstützt nur mobile Clients.

Die folgende Tabelle enthält eine Reihe von APIs zum Aktivieren der Medienfunktionen Ihres Geräts:

| API      | Beschreibung   |
| --- | --- |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-selectmedia) (**Kamera)**| Mit dieser API können Benutzer **Medien über die Gerätekamera erfassen oder auswählen** und an die Web-App zurückgeben. Die Benutzer können Bilder vor der Übermittlung bearbeiten, zuschneiden, drehen, kommentieren oder darauf zeichnen. Als Reaktion auf `selectMedia` empfängt die Web-App die Medien-IDs der ausgewählten Bilder und eine Miniaturansicht der ausgewählten Medien. Diese API kann über die [ImageProps-Konfiguration](/javascript/api/@microsoft/teams-js/media.imageprops) weiter konfiguriert werden. |
| [**selectMedia**](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-selectmedia) (**Mikrofon**)| Legen Sie "mediaType" in `selectMedia` der API für den Zugriff auf die Mikrofonfunktion auf `4` "[mediaType](/javascript/api/@microsoft/teams-js/media.mediatype)" (Audio) fest. Diese API ermöglicht es Benutzern auch, Audio vom Gerätemikrofon aufzuzeichnen und aufgezeichnete Clips an die Web-App zurückzugeben. Die Benutzer können die Aufzeichnung vor der Übermittlung anhalten, erneut aufzeichnen und wiedergeben. Als Reaktion auf  **selectMedia** empfängt die Web-App die Medien-IDs der ausgewählten Audioaufzeichnungen. <br/> Verwenden Sie `maxDuration`, wenn Sie eine Dauer in Minuten für die Aufzeichnung von Unterhaltungen konfigurieren müssen. Die aktuelle Dauer der Aufzeichnung beträgt 10 Minuten, danach wird sie beendet.  |
| [**getMedia**](/javascript/api/@microsoft/teams-js/media.media#@microsoft-teams-js-media-media-getmedia)| Diese API ruft die von der `selectMedia`-API erfassten Medien unabhängig von der Mediengröße in Blöcken ab. Diese Blöcke werden zusammengesetzt und als Datei oder Blob zurück an die Web-App gesendet. Das Aufteilen von Medien in kleinere Blöcke erleichtert die Übertragung großer Dateien. |
| [**viewImages**](/javascript/api/@microsoft/teams-js/media#@microsoft-teams-js-media-viewimages)| Diese API ermöglicht es dem Benutzer, Bilder im Vollbildmodus als bildlauffähige Liste anzuzeigen.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für die Bildfunktion:

:::image type="content" source="~/assets/images/tabs/media-capability-mobile2.png" alt-text="Die Abbildung zeigt die Bildfunktion für mobile Geräte.":::

> [!NOTE]
>
> Auf Geräten mit Android-Version unter 7 startet die `selectMedia` API die systemeigene Android-Kameraumgebung anstelle der nativen Teams-Kameraerfahrung.

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für die Mikrofonfunktion:

:::image type="content" source="~/assets/images/tabs/microphone-capability.png" alt-text="Die Abbildung zeigt die Mikrofonfunktion für mobile Geräte.":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

Die folgende Abbildung zeigt die Web-App-Erfahrung der `selectMedia` API für die Bildfunktion:

:::image type="content" source="~/assets/images/tabs/media-capability-desktop1.png" alt-text="Die Abbildung zeigt die Medienfunktion für den Desktop.":::

---

## <a name="error-handling"></a>Fehlerbehandlung

Stellen Sie sicher, dass diese Fehler in Ihrer Teams-App ordnungsgemäß behandelt werden. In der folgenden Tabelle sind die Fehlercodes und beschreibungen aufgeführt, unter denen die Fehler generiert werden:

|Fehlercode |  Fehlername     | Beschreibung|
| --------- | --------------- | -------- |
| **100** | NOT_SUPPORTED_ON_PLATFORM | Die API wird auf der aktuellen Plattform nicht unterstützt.|
| **404** | FILE_NOT_FOUND | Die angegebene Datei wird am angegebenen Speicherort nicht gefunden.|
| **500** | INTERNAL_ERROR | Interner Fehler beim Ausführen des erforderlichen Vorgangs.|
| **1000** | PERMISSION_DENIED |Die Berechtigung wird vom Benutzer verweigert.|
| **3000** | NO_HW_SUPPORT | Die Hardware unterstützt die Funktion nicht.|
| **4000**| INVALID_ARGUMENTS | Mindestens ein Argument ist ungültig.|
|  **8000** | USER_ABORT |Der Benutzer bricht den Vorgang ab.|
| **9000**| OLD_PLATFORM | Plattformcode ist veraltet und implementiert diese API nicht.|
| **10000**| SIZE_EXCEEDED |  Der Rückgabewert ist zu groß und hat die Grenzen der Plattformgröße überschritten.|

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

* Anruf-API `selectMedia` zum Aufnehmen von Videos mithilfe der Kamera:

  * Aufnehmen von Videos mit `fullscreen: true`:

       `fullscreen: true` öffnet die Kamera im Videoaufzeichnungsmodus. Es bietet eine Option für die Verwendung der Vorder- und Rückkamera sowie weitere Attribute, wie im folgenden Beispiel erwähnt:

       ```javascript
        
         const defaultLensVideoProps: microsoftTeams.media.VideoProps = {
             sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
             startMode: microsoftTeams.media.CameraStartMode.Video,
             cameraSwitcher: true,
             maxDuration: 30
        }
         const defaultLensVideoMediaInput: microsoftTeams.media.MediaInputs = {
             mediaType: microsoftTeams.media.MediaType.Video,
             maxMediaCount: 6,
             videoProps: defaultLensVideoProps
        }
       ```

  * Aufnehmen von Videos mit `fullscreen: false`:

       `fullscreen: false` öffnet die Kamera im Videoaufzeichnungsmodus und verwendet nur die Frontkamera. Wird in der Regel `fullscreen: false` verwendet, wenn Der Benutzer beim Lesen von Inhalten auf dem Gerätebildschirm Video aufzeichnen möchte.

       Dieser Modus unterstützt `isStopButtonVisible: true` auch das Hinzufügen einer Stoppschaltfläche auf dem Bildschirm, mit der der Benutzer die Aufzeichnung beenden kann. If `isStopButtonVisible: false`, recording can be stopped either by calling mediaController API or when the recording duration has reached `maxDuration` time specified.

       Es folgt ein Beispiel zum Beenden der Aufzeichnung mit `maxDuration` der angegebenen Zeit:

       ```javascript
          const defaultNativeVideoProps: microsoftTeams.media.VideoProps = {
             maxDuration: 30,
             isFullScreenMode: false,
             isStopButtonVisible: false,
             videoController: new microsoftTeams.media.VideoController(videoControllerCallback)
         }
          const defaultNativeVideoMediaInput: microsoftTeams.media.MediaInputs = {
             mediaType: microsoftTeams.media.MediaType.Video,
             maxMediaCount: 1,
             videoProps: defaultNativeVideoProps
         }
       ```

       Es folgt ein Beispiel zum Beenden der Aufzeichnung durch Aufrufen der mediaController-API:

       ```javascript
          const defaultNativeVideoProps: microsoftTeams.media.VideoProps = {
             videoController.stop(),
             isFullScreenMode: false,
             isStopButtonVisible: false,
             videoController: new microsoftTeams.media.VideoController(videoControllerCallback)
         }
          const defaultNativeVideoMediaInput: microsoftTeams.media.MediaInputs = {
             mediaType: microsoftTeams.media.MediaType.Video,
             maxMediaCount: 1,
             videoProps: defaultNativeVideoProps
         }
       ```

* Anruf-API `selectMedia` zum Aufzeichnen von Bildern und Videos mithilfe der Kamera:

  Auf diese Weise können Benutzer zwischen der Aufnahme eines Bilds oder Videos auswählen.

    ```javascript
    
      const defaultVideoAndImageProps: microsoftTeams.media.VideoAndImageProps = {
        sources: [microsoftTeams.media.Source.Camera, microsoftTeams.media.Source.Gallery],
        startMode: microsoftTeams.media.CameraStartMode.Photo,
        ink: true,
        cameraSwitcher: true,
        textSticker: true,
        enableFilter: true,
        maxDuration: 30
      }
    
      const defaultVideoAndImageMediaInput: microsoftTeams.media.MediaInputs = {
        mediaType: microsoftTeams.media.MediaType.VideoAndImage,
        maxMediaCount: 6,
        videoAndImageProps: defaultVideoAndImageProps
      }
    
      let videoControllerCallback: microsoftTeams.media.VideoControllerCallback = {
        onRecordingStarted() {
          console.log('onRecordingStarted Callback Invoked');
        },
      };
    
      microsoftTeams.media.selectMedia(defaultVideoAndImageMediaInput, (error: microsoftTeams.SdkError, attachments: microsoftTeams.media.Media[]) => {
        if (error) {
            if (error.message) {
                alert(" ErrorCode: " + error.errorCode + error.message);
            } else {
                alert(" ErrorCode: " + error.errorCode);
            }
        }
        
        var videoElement = document.createElement("video");
        attachments[0].getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
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
        videoElement.setAttribute("src", ("data:" + audioResult.mimeType + ";base64," + audioResult.preview));
        audioResult.getMedia((error: microsoftTeams.SdkError, blob: Blob) => {
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
    });
    ```

## <a name="see-also"></a>Siehe auch

* [Integrieren von QR-Code- oder Strichcodescanner-Funktionen in Microsoft Teams](qr-barcode-scanner-capability.md)
* [Integrieren von Standortfunktionen in Microsoft Teams](location-capability.md)
* [Integration der Personenauswahl](people-picker-capability.md)
* [Anforderungen und Überlegungen für anwendungsgehostete Medienbots](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
