---
title: Gerätefunktionen – Übersicht
author: Rajeshwari-v
description: Erfahren Sie, wie Sie systemeigene Gerätefunktionen wie Standort und Medien (Kamera, Mikrofon, Katalog, QR- oder Strichcodescanner) in die Microsoft Teams-App integrieren.
ms.author: surbhigupta
ms.localizationpriority: medium
ms.topic: overview
ms.openlocfilehash: 04ae1a0b21c12ef7dda5d4bf8dfa799ac5726d15
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100567"
---
# <a name="device-capabilities"></a>Gerätefunktionen

Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an integrierten First-Party-Erfahrungen ausrichten. Die erweiterte Teams-Plattform ermöglicht es Partnern, Gerätefunktionen wie Kamera, QR- oder Barcode-Scanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps zu integrieren. Diese Integration reduziert die Barrieren für die App-Entwicklung, beschleunigt den Entwicklungszyklus und schafft neue Szenarien oder Anwendungsfälle für die Entwickler-Community.

Geräteberechtigungen sind im Browser unterschiedlich. Zuvor hat der Browser behandelt, wie Zugriffsberechtigungen erteilt werden, und jetzt werden diese Berechtigungen in Teams behandelt. Weitere Informationen finden Sie unter [Browsergeräteberechtigungen](browser-device-permissions.md).

## <a name="native-device-capabilities"></a>Systemeigene Gerätefunktionen

Ein Mobilgerät oder Desktop verfügt über integrierte Geräte wie Kamera und Mikrofon, die als Funktionen bezeichnet werden. Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) verfügbar sind:

* Medienfunktionen, z. B.
  * Kamera
  * Mikrofon
  * Katalog
  * QR- oder Barcode-Scanner
* Standort

Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in die Teams-Plattform integrieren, um die Zusammenarbeit zu verbessern.

## <a name="request-device-permissions"></a>Geräteberechtigungen anfordern

Verwenden Sie die im [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) enthaltenen Tools, um die erforderlichen [Berechtigungen](native-device-permissions.md) für den Zugriff auf die systemeigene Gerätefunktionen anzufordern. Während der Zugriff auf diese Funktionen in modernen Webbrowsern Standard ist, müssen Sie Teams über die von Ihnen verwendeten Funktionen informieren, indem Sie Ihr App-Manifest aktualisieren. Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf mobilen oder Desktop-Clients von Teams ausgeführt wird.

## <a name="integrate-device-capabilities"></a>Integrieren von Gerätefunktionen

Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie Teams-APIs für Medienfunktionen, um [Medienfunktionen](media-capabilities.md) in die Teams-Plattform zu integrieren und so die Benutzererfahrung zu verbessern. Diese integrierten Funktionen ermöglichen Ihrer App Folgendes:

* Bilder aufnehmen und teilen.
* Scannen von QR oder Barcode mit der [Scannersteuerung](qr-barcode-scanner-capability.md).
* Aufnehmen von Audio über das Mikrofon.
* Teilen von Standort mit der [Standortauswahl](location-capability.md).

Außerdem können Sie das systemeigene [Personenauswahl-Steuerelement](people-picker-capability.md) von Teams integrieren, mit dem Benutzer Personen in der Webanwendung suchen und auswählen können.

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | Node.js    |
|:---------------------|:--------------|:---------|
|Geräteberechtigungen | Beschreibt, wie die Beispiel-App der Teams-Registerkarte für Geräteberechtigungen veranschaulicht wird. |[View](<https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-device-permissions/nodejs>)|
