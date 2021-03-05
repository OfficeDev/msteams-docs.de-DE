---
title: Übersicht über Gerätefunktionen
description: Übersicht über systemeigene Gerätefunktionen.
keywords: Kamerabild medienmikromi qr code qrcode strichcode barcode scan scanner location map funktionen systemeigene Geräteberechtigungen
ms.topic: overview
ms.openlocfilehash: 4c826d1705dfeea1feea21b02e7be51789817e48
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449591"
---
# <a name="device-capabilities"></a>Gerätefunktionen 

Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf integrierte Erfahrungen von Erstentwicklern ausgerichtet sind. Mit der erweiterten Teams-Plattform können Partner Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps integrieren. Diese Integration verringert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklergemeinschaft.

## <a name="native-device-capabilities"></a>Systemeigene Gerätefunktionen

Ein Mobiles oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die im [Microsoft Teams JavaScript-Client-SDK verfügbar sind:](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)
* Medienfunktionen, z. B.
    * Camera
    * Mikrofon
    * Katalog
    * QR- oder Strichcodescanner
* Standort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in die Teams-Plattform integrieren, um die Zusammenarbeit zu verbessern. 

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die Tools im [Microsoft Teams JavaScript-Client-SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um die erforderlichen Berechtigungen für den Zugriff auf die systemeigenen Gerätefunktionen an fordern. [](native-device-permissions.md) Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie beim Aktualisieren Ihres App-Manifests verwenden. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf mobilen Teams- oder Desktopclients ausgeführt wird.
 
 ## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie Die Medienfunktionen-APIs von Teams, um [Medienfunktionen](mobile-camera-image-permissions.md) in die Teams-Plattform zu integrieren, um die Benutzerfreundlichkeit zu verbessern. Diese integrierten Funktionen ermöglichen Ihrer App:

* Erfassen und Freigeben von Bildern
* Scannen von QR oder Strichcode mithilfe eines [Scannersteuerelements](qr-barcode-scanner-capability.md)
* Aufzeichnen von Audio über Mikrofon
* Freigeben des Speicherorts [mithilfe der Standortauswahl](location-capability.md).
