---
title: Gerätefunktionen – Übersicht
author: Rajeshwari-v
description: Übersicht über systemeigene Gerätefunktionen.
ms.author: surbhigupta
keywords: Kamerabild Medienmikrofon Mikrofon QR Code Qrcode Barcode Barcode Scan Location Map Capabilities native Geräteberechtigungen
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 9c08b727808f33ad128709ce15ecab2ecc3602b3
ms.sourcegitcommit: 781e7b82240075e9d1f55e97f3f1dcbba82a5e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2021
ms.locfileid: "60566267"
---
# <a name="device-capabilities"></a>Gerätefunktionen

Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an den integrierten Oberflächen von Erstanbietern orientieren. Die erweiterte Teams-Plattform ermöglicht Partnern die Integration von Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps. Diese Integration reduziert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklercommunity.

Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter [Berechtigungen für Browsergeräte.](browser-device-permissions.md)

## <a name="native-device-capabilities"></a>Systemeigene Gerätefunktionen

Ein Mobilgerät oder Desktop verfügt über integrierte Geräte, z. B. Kamera und Mikrofon, die als Funktionen bezeichnet werden. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verfügbar sind:
* Medienfunktionen, z. B.
    * Kamera
    * Mikrofon
    * Katalog
    * QR- oder Strichcodescanner
* Speicherort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in die Teams-Plattform integrieren, um die Zusammenarbeit zu verbessern. 

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die tools in [Microsoft Teams JavaScript-Client-SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um die erforderlichen [Berechtigungen](native-device-permissions.md) für den Zugriff auf die systemeigenen Gerätefunktionen anzufordern. Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams mobilen oder Desktopclients ausgeführt wird.
 
 ## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Verwenden Sie nach dem Zugriff auf Gerätefunktionen Teams Medienfunktionen-APIs, um Medienfunktionen in die Teams-Plattform zu [integrieren,](mobile-camera-image-permissions.md) um die Benutzererfahrung zu verbessern. Diese integrierten Funktionen ermöglichen Ihrer App Folgendes:

* Erfassen und Freigeben von Bildern.
* Scannen Sie QR oder Barcode mithilfe des [Scannersteuerelements.](qr-barcode-scanner-capability.md)
* Aufzeichnen von Audiodaten über das Mikrofon.
* Freigeben des Standorts mithilfe der [Standortauswahl.](location-capability.md)

Darüber hinaus können Sie das steuerelement Teams systemeigenen [Personenauswahl](people-picker-capability.md) integrieren, mit dem Benutzer Personen in der Web-App-Oberfläche suchen und auswählen können.
