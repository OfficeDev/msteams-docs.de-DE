---
title: Gerätefunktionen - Übersicht
author: Rajeshwari-v
description: Überblick über die Funktionen nativer Geräte.
ms.author: surbhigupta
keywords: Kamera Bild Medien Mikrofon mikrofon qr code qrcode Barcode Scan Scanner Standortkarte Funktionen native Geräteberechtigungen
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 8df8341e8996e4bf380575ac59e05325da16bd0d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566194"
---
# <a name="device-capabilities"></a>Gerätefunktionen

Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an den integrierten First-Party-Erlebnissen orientieren. Die erweiterte Teams-Plattform ermöglicht es Partnern, Gerätefunktionen wie Kamera-, QR- oder Barcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps zu integrieren. Diese Integration reduziert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklercommunity.

## <a name="native-device-capabilities"></a>Native Gerätefunktionen

Ein mobiles oder Desktop-Gerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden. Sie können über dedizierte APIs, die im [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verfügbar sind, auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops zugreifen:
* Medienfunktionen, wie z. B.
    * Kamera
    * Mikrofon
    * Katalog
    * QR- oder Barcode-Scanner
* Speicherort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in Teams Plattform integrieren, um die kollaborative Erfahrung zu verbessern. 

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) vorhandenen Tools, um die erforderlichen [Berechtigungen](native-device-permissions.md) für den Zugriff auf die Funktionen des nativen Geräts anzufordern. Obwohl der Zugriff auf diese Funktionen in modernen Webbrowsern Standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams mobilen oder Desktopclients ausgeführt wird.
 
 ## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie Teams Medienfunktions-APIs, um Medienfunktionen in Teams Plattform zu [integrieren,](mobile-camera-image-permissions.md) um die Benutzerfreundlichkeit zu verbessern. Diese integrierten Funktionen ermöglichen Es Ihrer App:

* Erfassen und teilen Sie Bilder.
* QR oder Barcode mit [Scannersteuerung scannen.](qr-barcode-scanner-capability.md)
* Nehmen Sie Audio über mikrofon auf.
* Freigabespeicherort mithilfe [der Standortauswahl](location-capability.md).
