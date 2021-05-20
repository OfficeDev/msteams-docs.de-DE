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
# <a name="device-capabilities"></a><span data-ttu-id="e6351-104">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="e6351-104">Device capabilities</span></span>

<span data-ttu-id="e6351-105">Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an den integrierten First-Party-Erlebnissen orientieren.</span><span class="sxs-lookup"><span data-stu-id="e6351-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="e6351-106">Die erweiterte Teams-Plattform ermöglicht es Partnern, Gerätefunktionen wie Kamera-, QR- oder Barcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="e6351-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location with their web apps.</span></span> <span data-ttu-id="e6351-107">Diese Integration reduziert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklercommunity.</span><span class="sxs-lookup"><span data-stu-id="e6351-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="e6351-108">Native Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="e6351-108">Native device capabilities</span></span>

<span data-ttu-id="e6351-109">Ein mobiles oder Desktop-Gerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="e6351-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="e6351-110">Sie können über dedizierte APIs, die im [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verfügbar sind, auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops zugreifen:</span><span class="sxs-lookup"><span data-stu-id="e6351-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="e6351-111">Medienfunktionen, wie z. B.</span><span class="sxs-lookup"><span data-stu-id="e6351-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="e6351-112">Kamera</span><span class="sxs-lookup"><span data-stu-id="e6351-112">Camera</span></span>
    * <span data-ttu-id="e6351-113">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="e6351-113">Microphone</span></span>
    * <span data-ttu-id="e6351-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="e6351-114">Gallery</span></span>
    * <span data-ttu-id="e6351-115">QR- oder Barcode-Scanner</span><span class="sxs-lookup"><span data-stu-id="e6351-115">QR or barcode scanner</span></span>
* <span data-ttu-id="e6351-116">Speicherort</span><span class="sxs-lookup"><span data-stu-id="e6351-116">Location</span></span>

<span data-ttu-id="e6351-117">Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in Teams Plattform integrieren, um die kollaborative Erfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="e6351-117">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="e6351-118">Geräteberechtigungen anfordern</span><span class="sxs-lookup"><span data-stu-id="e6351-118">Request device permissions</span></span>

<span data-ttu-id="e6351-119">Verwenden Sie die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) vorhandenen Tools, um die erforderlichen [Berechtigungen](native-device-permissions.md) für den Zugriff auf die Funktionen des nativen Geräts anzufordern.</span><span class="sxs-lookup"><span data-stu-id="e6351-119">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to request the required  [permissions](native-device-permissions.md) for accessing the native device capabilities.</span></span> <span data-ttu-id="e6351-120">Obwohl der Zugriff auf diese Funktionen in modernen Webbrowsern Standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="e6351-120">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="e6351-121">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams mobilen oder Desktopclients ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e6351-121">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="e6351-122">Integrieren von Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="e6351-122">Integrate device capabilities</span></span>

<span data-ttu-id="e6351-123">Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie Teams Medienfunktions-APIs, um Medienfunktionen in Teams Plattform zu [integrieren,](mobile-camera-image-permissions.md) um die Benutzerfreundlichkeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="e6351-123">After getting access to device capabilities, use Teams media capability APIs to [integrate media capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="e6351-124">Diese integrierten Funktionen ermöglichen Es Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="e6351-124">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="e6351-125">Erfassen und teilen Sie Bilder.</span><span class="sxs-lookup"><span data-stu-id="e6351-125">Capture and share images.</span></span>
* <span data-ttu-id="e6351-126">QR oder Barcode mit [Scannersteuerung scannen.](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="e6351-126">Scan QR or barcode using [scanner control](qr-barcode-scanner-capability.md).</span></span>
* <span data-ttu-id="e6351-127">Nehmen Sie Audio über mikrofon auf.</span><span class="sxs-lookup"><span data-stu-id="e6351-127">Record audio through microphone.</span></span>
* <span data-ttu-id="e6351-128">Freigabespeicherort mithilfe [der Standortauswahl](location-capability.md).</span><span class="sxs-lookup"><span data-stu-id="e6351-128">Share location using [location picker](location-capability.md).</span></span>
