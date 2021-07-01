---
title: Gerätefunktionen – Übersicht
author: Rajeshwari-v
description: Übersicht über systemeigene Gerätefunktionen.
ms.author: surbhigupta
keywords: Kamerabild Medienmikrofon Mikrofon QR Code Qrcode Barcode Barcode Scan Location Map Capabilities native Geräteberechtigungen
localization_priority: Normal
ms.topic: overview
ms.openlocfilehash: 069bd27057784076b3b701d013ead209ec6fa3a9
ms.sourcegitcommit: 059d22c436ee9b07a61561ff71e03e1c23ff40b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "53211583"
---
# <a name="device-capabilities"></a><span data-ttu-id="6cf30-104">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="6cf30-104">Device capabilities</span></span>

<span data-ttu-id="6cf30-105">Microsoft Teams Plattform verbessert kontinuierlich die Entwicklerfunktionen, die sich an den integrierten Oberflächen von Erstanbietern orientieren.</span><span class="sxs-lookup"><span data-stu-id="6cf30-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="6cf30-106">Die erweiterte Teams-Plattform ermöglicht Partnern die Integration von Gerätefunktionen wie Kamera, QR- oder Strichcodescanner, Fotogalerie, Mikrofon und Standort in ihre Web-Apps.</span><span class="sxs-lookup"><span data-stu-id="6cf30-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, QR or barcode scanner, photo gallery, microphone, and location with their web apps.</span></span> <span data-ttu-id="6cf30-107">Diese Integration reduziert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwicklercommunity.</span><span class="sxs-lookup"><span data-stu-id="6cf30-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="6cf30-108">Systemeigene Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="6cf30-108">Native device capabilities</span></span>

<span data-ttu-id="6cf30-109">Ein Mobile- oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="6cf30-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="6cf30-110">Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die in [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="6cf30-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="6cf30-111">Medienfunktionen, z. B.</span><span class="sxs-lookup"><span data-stu-id="6cf30-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="6cf30-112">Kamera</span><span class="sxs-lookup"><span data-stu-id="6cf30-112">Camera</span></span>
    * <span data-ttu-id="6cf30-113">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="6cf30-113">Microphone</span></span>
    * <span data-ttu-id="6cf30-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="6cf30-114">Gallery</span></span>
    * <span data-ttu-id="6cf30-115">QR- oder Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="6cf30-115">QR or barcode scanner</span></span>
* <span data-ttu-id="6cf30-116">Standort</span><span class="sxs-lookup"><span data-stu-id="6cf30-116">Location</span></span>

<span data-ttu-id="6cf30-117">Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in Teams Plattform integrieren, um die Zusammenarbeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="6cf30-117">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="6cf30-118">Geräteberechtigungen anfordern</span><span class="sxs-lookup"><span data-stu-id="6cf30-118">Request device permissions</span></span>

<span data-ttu-id="6cf30-119">Verwenden Sie die tools in [Microsoft Teams JavaScript-Client-SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) um die erforderlichen [Berechtigungen](native-device-permissions.md) für den Zugriff auf die systemeigenen Gerätefunktionen anzufordern.</span><span class="sxs-lookup"><span data-stu-id="6cf30-119">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to request the required  [permissions](native-device-permissions.md) for accessing the native device capabilities.</span></span> <span data-ttu-id="6cf30-120">Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="6cf30-120">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="6cf30-121">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf Teams mobilen oder Desktopclients ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="6cf30-121">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="6cf30-122">Integrieren von Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="6cf30-122">Integrate device capabilities</span></span>

<span data-ttu-id="6cf30-123">Verwenden Sie nach dem Zugriff auf Gerätefunktionen Teams Medienfunktionen-APIs, um Medienfunktionen in Teams Plattform zu [integrieren,](mobile-camera-image-permissions.md) um die Benutzererfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="6cf30-123">After getting access to device capabilities, use Teams media capability APIs to [integrate media capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="6cf30-124">Diese integrierten Funktionen ermöglichen Ihrer App Folgendes:</span><span class="sxs-lookup"><span data-stu-id="6cf30-124">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="6cf30-125">Erfassen und Freigeben von Bildern.</span><span class="sxs-lookup"><span data-stu-id="6cf30-125">Capture and share images.</span></span>
* <span data-ttu-id="6cf30-126">Scannen Sie QR oder Barcode mithilfe des [Scannersteuerelements.](qr-barcode-scanner-capability.md)</span><span class="sxs-lookup"><span data-stu-id="6cf30-126">Scan QR or barcode using [scanner control](qr-barcode-scanner-capability.md).</span></span>
* <span data-ttu-id="6cf30-127">Aufzeichnen von Audiodaten über das Mikrofon.</span><span class="sxs-lookup"><span data-stu-id="6cf30-127">Record audio through microphone.</span></span>
* <span data-ttu-id="6cf30-128">Freigeben des Standorts mithilfe der [Standortauswahl.](location-capability.md)</span><span class="sxs-lookup"><span data-stu-id="6cf30-128">Share location using [location picker](location-capability.md).</span></span>

<span data-ttu-id="6cf30-129">Darüber hinaus können Sie das Teams [Systemeigene Personenauswahl-Steuerelement](people-picker-capability.md) integrieren, mit dem Benutzer Personen in der Web-App-Oberfläche suchen und auswählen können.</span><span class="sxs-lookup"><span data-stu-id="6cf30-129">Also, you can integrate the Teams native [people picker control](people-picker-capability.md) that allows users to search and select people in the web app experience.</span></span>
