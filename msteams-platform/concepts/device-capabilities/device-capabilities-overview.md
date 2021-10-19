---
title: Gerätefunktionen – Übersicht
author: Rajeshwari-v
description: Übersicht über systemeigene Gerätefunktionen.
ms.author: surbhigupta
keywords: Kamerabild Medienmikrofon Mikrofon QR Code Qrcode Barcode Barcode Scan Location Map Capabilities native Geräteberechtigungen
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 8e8c7d7920d3a00d3414226296d9baf3dc209be2
ms.sourcegitcommit: ce956267b620f807e15e6d2df7afa022ffacc22f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2021
ms.locfileid: "60496193"
---
# <a name="device-capabilities"></a>Gerätefunktionen

Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an den integrierten Erfahrungen von Erstanbietern orientieren. Die erweiterte Teams-Plattform ermöglicht Partnern die Integration von Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps. Diese Integration reduziert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklercommunity.

Geräteberechtigungen unterscheiden sich im Browser. Weitere Informationen finden Sie unter [Berechtigungen für Browsergeräte.](browser-device-permissions.md)

## <a name="native-device-capabilities"></a>Systemeigene Gerätefunktionen

Ein Mobile- oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verfügbar sind:
* Medienfunktionen, z. B.
    * Kamera
    * Mikrofon
    * Katalog
    * QR- oder Strichcodescanner
* Speicherort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in Teams Plattform integrieren, um die Zusammenarbeit zu verbessern. 

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die Tools, die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) vorhanden sind, um die erforderlichen [Berechtigungen](native-device-permissions.md) für den Zugriff auf die systemeigenen Gerätefunktionen anzufordern. Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams mobilen oder Desktopclients ausgeführt wird.
 
 ## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Verwenden Sie nach dem Zugriff auf Gerätefunktionen Teams Medienfunktionen-APIs, um Medienfunktionen in Teams Plattform zu [integrieren,](mobile-camera-image-permissions.md) um die Benutzererfahrung zu verbessern. Diese integrierten Funktionen ermöglichen Ihrer App Folgendes:

* Erfassen und Freigeben von Bildern.
* Scannen Sie QR oder Barcode mithilfe des [Scannersteuerelements.](qr-barcode-scanner-capability.md)
* Aufzeichnen von Audiodaten über das Mikrofon.
* Freigeben des Standorts mithilfe der [Standortauswahl.](location-capability.md)

Darüber hinaus können Sie das steuerelement Teams systemeigenen [Personenauswahl](people-picker-capability.md) integrieren, mit dem Benutzer Personen in der Web-App-Oberfläche suchen und auswählen können.
