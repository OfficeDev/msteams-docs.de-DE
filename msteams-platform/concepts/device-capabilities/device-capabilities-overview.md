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
# <a name="device-capabilities"></a><span data-ttu-id="1e615-104">Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="1e615-104">Device capabilities</span></span> 

<span data-ttu-id="1e615-105">Die Microsoft Teams-Plattform verbessert kontinuierlich die Entwicklerfunktionen, die auf die integrierten Erfahrungen von Erstentwicklern ausgerichtet sind.</span><span class="sxs-lookup"><span data-stu-id="1e615-105">Microsoft Teams platform is continuously enhancing developer capabilities aligning with built-in first-party experiences.</span></span> <span data-ttu-id="1e615-106">Die erweiterte Teams-Plattform ermöglicht Partnern die Integration von Gerätefunktionen wie Kamera, Fotogalerie, Mikrofon und Standort in ihre Web-Apps.</span><span class="sxs-lookup"><span data-stu-id="1e615-106">The enhanced Teams platform allows partners to integrate device capabilities, such as camera, photo gallery, microphone, and location, with their web apps.</span></span> <span data-ttu-id="1e615-107">Diese Integration verringert die Barriere für die App-Entwicklung, beschleunigt den Entwicklungszyklus und erstellt neue Szenarien oder Anwendungsfälle für die Entwickler-Community.</span><span class="sxs-lookup"><span data-stu-id="1e615-107">This integration reduces the barrier to app development, speeds-up development-cycle, and creates new scenarios or use-cases for the developer community.</span></span>

## <a name="native-device-capabilities"></a><span data-ttu-id="1e615-108">Systemeigene Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="1e615-108">Native device capabilities</span></span>

<span data-ttu-id="1e615-109">Ein Mobiles oder Desktopgerät verfügt über integrierte Geräte, z. B. eine Kamera und ein Mikrofon, die als Funktionen bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="1e615-109">A mobile or desktop device has built-in devices, such as a camera and microphone, called capabilities.</span></span> <span data-ttu-id="1e615-110">Sie können auf die folgenden Gerätefunktionen auf Mobilgeräten oder Desktops über dedizierte APIs zugreifen, die im [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)von Microsoft Teams verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="1e615-110">You can access the following device capabilities on mobile or desktop through dedicated APIs available in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true):</span></span>
* <span data-ttu-id="1e615-111">Medienfunktionen, z. B.</span><span class="sxs-lookup"><span data-stu-id="1e615-111">Media capabilities, such as</span></span>
    * <span data-ttu-id="1e615-112">Kamera</span><span class="sxs-lookup"><span data-stu-id="1e615-112">Camera</span></span>
    * <span data-ttu-id="1e615-113">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="1e615-113">Microphone</span></span>
    * <span data-ttu-id="1e615-114">Katalog</span><span class="sxs-lookup"><span data-stu-id="1e615-114">Gallery</span></span>
* <span data-ttu-id="1e615-115">Ort</span><span class="sxs-lookup"><span data-stu-id="1e615-115">Location</span></span>

<span data-ttu-id="1e615-116">Nachdem Sie Zugriff auf die Gerätefunktionen erhalten haben, können Sie sie in die Plattform "Teams" integrieren, um die Zusammenarbeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="1e615-116">After getting access to the device capabilities, you can integrate them with Teams platform to enhance the collaborative experience.</span></span> 

## <a name="request-device-permissions"></a><span data-ttu-id="1e615-117">Geräteberechtigungen anfordern</span><span class="sxs-lookup"><span data-stu-id="1e615-117">Request device permissions</span></span>

<span data-ttu-id="1e615-118">Verwenden Sie die Tools im [JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) von Microsoft Teams, um die erforderlichen Berechtigungen für den Zugriff auf die systemeigenen Gerätefunktionen an fordern. [](native-device-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="1e615-118">Use the tools present in [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) to  request the required  [permissions](native-device-permissions.md) for  accessing the native device capabilities.</span></span> <span data-ttu-id="1e615-119">Während der Zugriff auf diese Funktionen in modernen Webbrowsern standard ist, müssen Sie Teams über die Funktionen informieren, die Sie verwenden, indem Sie Ihr App-Manifest aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1e615-119">While access to these capabilities is standard in modern web browsers, you must inform Teams about the capabilities that you are using by updating your app manifest.</span></span> <span data-ttu-id="1e615-120">Mit diesem Update können Sie Berechtigungen anfordern, während Ihre App auf mobilen Teams- oder Desktopclients ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1e615-120">This update allows you to request permissions while your app runs on Teams mobile or desktop clients.</span></span>
 
 ## <a name="integrate-device-capabilities"></a><span data-ttu-id="1e615-121">Integrieren von Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="1e615-121">Integrate device capabilities</span></span>

<span data-ttu-id="1e615-122">Nachdem Sie Zugriff auf Gerätefunktionen erhalten haben, verwenden Sie die APIs für **die Medienfunktionen** von Teams, um die Funktionen in die Teams-Plattform zu integrieren, um die Benutzerfreundlichkeit zu verbessern. [](mobile-camera-image-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="1e615-122">After getting access to device capabilities,use **Teams media capability APIs** to [integrate the capabilities](mobile-camera-image-permissions.md) with Teams platform to enhance the user experience.</span></span> <span data-ttu-id="1e615-123">Diese integrierten Funktionen ermöglichen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="1e615-123">These integrated capabilities allow your app to:</span></span>

* <span data-ttu-id="1e615-124">Erfassen und Freigeben von Bildern</span><span class="sxs-lookup"><span data-stu-id="1e615-124">Capture and share images</span></span>
* <span data-ttu-id="1e615-125">Aufzeichnen von Audio über mikrofon</span><span class="sxs-lookup"><span data-stu-id="1e615-125">Record audio through microphone</span></span>
* <span data-ttu-id="1e615-126">Freigeben der Standortinformationen</span><span class="sxs-lookup"><span data-stu-id="1e615-126">Share the location information</span></span>


