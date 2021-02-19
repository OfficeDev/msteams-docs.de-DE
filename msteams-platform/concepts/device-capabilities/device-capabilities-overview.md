---
title: Übersicht über Gerätefunktionen
description: Übersicht über systemeigene Gerätefunktionen.
keywords: Kamerabild medienmikromi qr code qrcode strichcode strichcode scan scanner funktionen systemeigene Geräteberechtigungen
ms.topic: overview
ms.openlocfilehash: 03ce0267f7160772e30ec88de2c29f81886b5280
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294726"
---
# <a name="device-capabilities"></a><span data-ttu-id="4d6b7-104">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="4d6b7-104">Device capabilities</span></span> 

<span data-ttu-id="4d6b7-105">Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf integrierte Erfahrungen von Erstentwicklern ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="4d6b7-106">Mit der erweiterten Teams-Plattform können Partner Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps integrieren.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location with their web apps.</span></span> <span data-ttu-id="4d6b7-107">Diese Integration verringert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklergemeinschaft.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="4d6b7-108">Systemeigene Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="4d6b7-108">Native device capabilities</span></span>

<span data-ttu-id="4d6b7-109">Ein Mobiles oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="4d6b7-110">Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die im [Microsoft Teams JavaScript-Client-SDK verfügbar sind:](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="4d6b7-111">Medienfunktionen, z. B.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="4d6b7-112">Camera</span><span class="sxs-lookup"><span data-stu-id="4d6b7-112">Camera</span></span>
    * <span data-ttu-id="4d6b7-113">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="4d6b7-113">Microphone</span></span>
    * <span data-ttu-id="4d6b7-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="4d6b7-114">Gallery</span></span>
    * <span data-ttu-id="4d6b7-115">QR- oder Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="4d6b7-115">QR or barcode scanner</span></span>
* <span data-ttu-id="4d6b7-116">Standort</span><span class="sxs-lookup"><span data-stu-id="4d6b7-116">Location</span></span>

<span data-ttu-id="4d6b7-117">Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in die Teams-Plattform integrieren, um die Zusammenarbeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-117">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="4d6b7-118">Geräteberechtigungen anfordern</span><span class="sxs-lookup"><span data-stu-id="4d6b7-118">Request device permissions</span></span>

<span data-ttu-id="4d6b7-119">Verwenden Sie die Tools im [Microsoft Teams JavaScript-Client-SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um die erforderlichen Berechtigungen für den Zugriff auf die systemeigenen Gerätefunktionen an fordern. [](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-119">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to request the required  [permissions](native-device-permissions.md) for accessing the native device capabilities.</span></span> <span data-ttu-id="4d6b7-120">Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-120">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="4d6b7-121">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf mobilen Teams- oder Desktopclients ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-121">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="4d6b7-122">Integrieren von Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="4d6b7-122">Integrate device capabilities</span></span>

<span data-ttu-id="4d6b7-123">Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie Die Medienfunktionen-APIs von Teams, um [Medienfunktionen](mobile-camera-image-permissions.md) in die Teams-Plattform zu integrieren, um die Benutzerfreundlichkeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="4d6b7-123">After getting access to device capabilities, use Teams media capability APIs to [integrate media capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="4d6b7-124">Diese integrierten Funktionen ermöglichen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="4d6b7-124">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="4d6b7-125">Erfassen und Freigeben von Bildern</span><span class="sxs-lookup"><span data-stu-id="4d6b7-125">Capture and share images</span></span>
* <span data-ttu-id="4d6b7-126">Scannen von QR- oder Barcodes mithilfe [eines Scannersteuerelements](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="4d6b7-126">Scan QR or barcode using [scanner control](qr-barcode-scanner-capability.md)</span></span>
* <span data-ttu-id="4d6b7-127">Aufzeichnen von Audio über Mikrofon</span><span class="sxs-lookup"><span data-stu-id="4d6b7-127">Record audio through microphone</span></span>
* <span data-ttu-id="4d6b7-128">Freigeben der Standortinformationen</span><span class="sxs-lookup"><span data-stu-id="4d6b7-128">Share the location information</span></span>
