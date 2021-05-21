---
title: Gerätefunktionen – Übersicht
author: Rajeshwari-v
description: Übersicht über systemeigene Gerätefunktionen.
ms.author: surbhigupta
keywords: Kamerabild medienmikromi qr code qrcode strichcode barcode scan scanner location map funktionen systemeigene Geräteberechtigungen
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

Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf integrierte Erfahrungen von Erstentwicklern ausgerichtet sind. Die erweiterte Teams ermöglicht Es Partnern, Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps zu integrieren. Diese Integration verringert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklergemeinschaft.

## <a name="native-device-capabilities"></a>Systemeigene Gerätefunktionen

Ein Mobiles oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in [Microsoft Teams JavaScript-Client-SDK verfügbar sind:](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)
* Medienfunktionen, z. B.
    * Camera
    * Mikrofon
    * Katalog
    * QR- oder Strichcodescanner
* Speicherort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in Teams integrieren, um die Zusammenarbeit zu verbessern. 

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die Tools in [Microsoft Teams JavaScript-Client-SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um die erforderlichen Berechtigungen für den Zugriff auf die systemeigenen Gerätefunktionen an fordern. [](native-device-permissions.md) Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie beim Aktualisieren Ihres App-Manifests verwenden. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams oder Desktopclients ausgeführt wird.
 
 ## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden [](mobile-camera-image-permissions.md) Sie Teams-APIs, um Medienfunktionen in Teams zu integrieren, um die Benutzeroberfläche zu verbessern. Diese integrierten Funktionen ermöglichen Ihrer App:

* Erfassen und Freigeben von Bildern.
* Scannen Sie QR oder Strichcode mithilfe [des Scannersteuerelements.](qr-barcode-scanner-capability.md)
* Aufzeichnen von Audio über mikrofon.
* Freigeben des Speicherorts [mithilfe der Standortauswahl](location-capability.md).
