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
# <a name="device-capabilities"></a><span data-ttu-id="80799-104">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="80799-104">Device capabilities</span></span>

<span data-ttu-id="80799-105">Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf integrierte Erfahrungen von Erstentwicklern ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="80799-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="80799-106">Die erweiterte Teams ermöglicht Es Partnern, Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="80799-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location with their web apps.</span></span> <span data-ttu-id="80799-107">Diese Integration verringert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklergemeinschaft.</span><span class="sxs-lookup"><span data-stu-id="80799-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="80799-108">Systemeigene Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="80799-108">Native device capabilities</span></span>

<span data-ttu-id="80799-109">Ein Mobiles oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="80799-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="80799-110">Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in [Microsoft Teams JavaScript-Client-SDK verfügbar sind:](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="80799-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="80799-111">Medienfunktionen, z. B.</span><span class="sxs-lookup"><span data-stu-id="80799-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="80799-112">Camera</span><span class="sxs-lookup"><span data-stu-id="80799-112">Camera</span></span>
    * <span data-ttu-id="80799-113">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="80799-113">Microphone</span></span>
    * <span data-ttu-id="80799-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="80799-114">Gallery</span></span>
    * <span data-ttu-id="80799-115">QR- oder Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="80799-115">QR or barcode scanner</span></span>
* <span data-ttu-id="80799-116">Speicherort</span><span class="sxs-lookup"><span data-stu-id="80799-116">Location</span></span>

<span data-ttu-id="80799-117">Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in Teams integrieren, um die Zusammenarbeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="80799-117">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="80799-118">Geräteberechtigungen anfordern</span><span class="sxs-lookup"><span data-stu-id="80799-118">Request device permissions</span></span>

<span data-ttu-id="80799-119">Verwenden Sie die Tools in [Microsoft Teams JavaScript-Client-SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um die erforderlichen Berechtigungen für den Zugriff auf die systemeigenen Gerätefunktionen an fordern. [](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="80799-119">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to request the required  [permissions](native-device-permissions.md) for accessing the native device capabilities.</span></span> <span data-ttu-id="80799-120">Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie beim Aktualisieren Ihres App-Manifests verwenden.</span><span class="sxs-lookup"><span data-stu-id="80799-120">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="80799-121">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams oder Desktopclients ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80799-121">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="80799-122">Integrieren von Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="80799-122">Integrate device capabilities</span></span>

<span data-ttu-id="80799-123">Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden [](mobile-camera-image-permissions.md) Sie Teams-APIs, um Medienfunktionen in Teams zu integrieren, um die Benutzeroberfläche zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="80799-123">After getting access to device capabilities, use Teams media capability APIs to [integrate media capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="80799-124">Diese integrierten Funktionen ermöglichen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="80799-124">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="80799-125">Erfassen und Freigeben von Bildern.</span><span class="sxs-lookup"><span data-stu-id="80799-125">Capture and share images.</span></span>
* <span data-ttu-id="80799-126">Scannen Sie QR oder Strichcode mithilfe [des Scannersteuerelements.](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="80799-126">Scan QR or barcode using [scanner control](qr-barcode-scanner-capability.md).</span></span>
* <span data-ttu-id="80799-127">Aufzeichnen von Audio über mikrofon.</span><span class="sxs-lookup"><span data-stu-id="80799-127">Record audio through microphone.</span></span>
* <span data-ttu-id="80799-128">Freigeben des Speicherorts [mithilfe der Standortauswahl](location-capability.md).</span><span class="sxs-lookup"><span data-stu-id="80799-128">Share location using [location picker](location-capability.md).</span></span>
