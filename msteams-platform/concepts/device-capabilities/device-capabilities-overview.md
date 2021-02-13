---
title: Übersicht über Gerätefunktionen
description: Übersicht über systemeigene Gerätefunktionen.
keywords: Kamerabild medienmikrofonfunktionen systemeigene Geräteberechtigungen
ms.topic: overview
ms.openlocfilehash: 8b2f92cb4586d646bde02742883122bb009847ea
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50232849"
---
# <a name="device-capabilities"></a>Gerätefunktionen 

Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf die integrierten Erfahrungen von Erstentwicklern ausgerichtet sind. Die erweiterte Teams-Plattform ermöglicht Partnern die Integration von Gerätefunktionen wie Kamera, Fotogalerie, Mikrofon und Standort in ihre Web-Apps. Diese Integration verringert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwickler-Community.

## <a name="native-device-capabilities"></a>Systemeigene Gerätefunktionen

Ein Mobiles oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die im [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)von Microsoft Teams verfügbar sind:
* Medienfunktionen, z. B.
    * Kamera
    * Mikrofon
    * Katalog
* Ort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in die Plattform "Teams" integrieren, um die Zusammenarbeit zu verbessern. 

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die Tools im [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) von Microsoft Teams, um die erforderlichen Berechtigungen für den Zugriff auf die systemeigenen Gerätefunktionen an fordern. [](native-device-permissions.md) Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf mobilen Teams- oder Desktopclients ausgeführt wird.
 
 ## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie die APIs für **die Medienfunktionen** von Teams, um die Funktionen in die Teams-Plattform zu integrieren, um die Benutzerfreundlichkeit zu verbessern. [](mobile-camera-image-permissions.md) Diese integrierten Funktionen ermöglichen Ihrer App:

* Erfassen und Freigeben von Bildern
* Aufzeichnen von Audio über mikrofon
* Freigeben der Standortinformationen


