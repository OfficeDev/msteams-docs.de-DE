---
title: Features in der Public Developer Preview
description: Beschreibt die Features in der öffentlichen Entwicklervorschau von Microsoft Teams
keywords: Entwicklerfeatures in Microsoft Teams Preview
ms.openlocfilehash: e607a6c65253a5fd94f8a805f1264a567bb8fd24
ms.sourcegitcommit: 9fd61042e8be513c2b2bd8a33ab5e9e6498d65c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "46819175"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="6271c-104">Features in der Public Preview für Entwickler von Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6271c-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="6271c-105">Die Entwicklervorschau umfasst die folgenden neuen Features:</span><span class="sxs-lookup"><span data-stu-id="6271c-105">The developer preview includes the following new features:</span></span>

## <a name="adaptive-cards-v12-support"></a><span data-ttu-id="6271c-106">Adaptive Cards v 1.2-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="6271c-106">Adaptive cards v1.2 support</span></span>

<span data-ttu-id="6271c-107">Die Unterstützung für [Adaptive Karten v 1.2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) in Microsoft Teams steht nun der allgemeinen Öffentlichkeit zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="6271c-107">Support for [Adaptive cards v1.2](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0) in Teams is now available to the general public.</span></span> <span data-ttu-id="6271c-108">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden jedoch derzeit in Adaptive Cards v 1.2 auf der Microsoft Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6271c-108">However, [Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="6271c-109">Registerkarten für einmaliges Anmelden (SSO)</span><span class="sxs-lookup"><span data-stu-id="6271c-109">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="6271c-110">Sie können jetzt [einmaliges Anmelden (Single Sign-on, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) für die Anmeldung und Authentifizierung eines Benutzers auf Desktop-und Mobilgeräten verwenden, indem Sie das Microsoft Teams-JavaScript-SDK über eine Webinhalts Seite verwenden.</span><span class="sxs-lookup"><span data-stu-id="6271c-110">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="6271c-111">Einer der Vorteile besteht darin, dass sich ein Benutzer niemals anmelden muss; und nachdem Sie der App mithilfe Ihres Profils zugestimmt haben: Sie werden automatisch auf Ihrer Registerkarte (einschließlich Mobiltelefon) angemeldet.</span><span class="sxs-lookup"><span data-stu-id="6271c-111">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="6271c-112">Unsere Entwicklervorschau steht in Manifest-Versionen 1,5 und höher zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="6271c-112">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="6271c-113">Unsere aktuelle Implementierung kann nur eine beschränkte Menge an Graph-APIs erhalten, aber wir bieten eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6271c-113">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="6271c-114">Bots für Anrufe und Onlinebesprechungen</span><span class="sxs-lookup"><span data-stu-id="6271c-114">Calls and online meeting bots</span></span>

<span data-ttu-id="6271c-115">Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta)können Microsoft Teams-apps nun mithilfe von Sprach-und Videofunktionen auf vielfältige Weise mit Benutzern interagieren.</span><span class="sxs-lookup"><span data-stu-id="6271c-115">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="6271c-116">Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Echtzeit-Audio-und/oder-Videodatenströme für Anrufe und Besprechungen einschließlich Desktop-und App-Freigaben hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6271c-116">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="6271c-117">Wir haben einen neuen Abschnitt zum Erstellen und entwickeln von Anrufen und Online-Besprechungs-Bots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6271c-117">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>
